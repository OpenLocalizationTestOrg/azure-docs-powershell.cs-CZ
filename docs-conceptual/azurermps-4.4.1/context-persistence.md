---
title: Zachování přihlášení uživatele napříč relacemi PowerShellu
description: Tento článek popisuje nové funkce v Azure PowerShellu, které umožňují opětovné použití přihlašovacích údajů a dalších informací o uživateli napříč několika relacemi PowerShellu.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 08/31/2017
ms.openlocfilehash: 8ef20796b64b16c78a653e293a57d5e752d89710
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="persisting-user-logins-across-powershell-sessions"></a>Zachování přihlášení uživatele napříč relacemi PowerShellu

Ve verzi Azure PowerShellu vydané v září 2017 zavádějí rutiny Azure Resource Manageru novou funkci **automatického ukládání kontextu Azure**. Tato funkce umožňuje uživatelům několik nových scénářů, včetně:

- Uchování přihlašovacích údajů pro opětovné použití v nových relacích PowerShellu.
- Snadnější použití úloh na pozadí pro provádění dlouhotrvajících rutin.
- Přepínání mezi účty, předplatnými a prostředími bez samostatného přihlášení.
- Současné provádění úloh s použitím různých přihlašovacích údajů a předplatných ze stejné relace PowerShellu.

## <a name="azure-contexts-defined"></a>Definice kontextů Azure

*Kontext Azure* je soubor informací, který definuje cíl rutin Azure PowerShellu. Kontext se skládá z pěti částí:

- *Účet* – Uživatelské jméno nebo instanční objekt používané k ověřování komunikace s Azure.
- *Předplatné* – Předplatné Azure obsahující prostředky, se kterými se pracuje.
- *Tenant* – Tenant Azure Active Directory obsahující vaše předplatné. Tenanti jsou důležitější pro ověřování instančního objektu.
- *Prostředí* – Konkrétní cloud Azure, na který se cílí, obvykle globální cloud Azure.
  Nastavení prostředí však umožňuje cílit i na národní cloudy, cloudy pro státní správu a místní cloudy (Azure Stack).
- *Přihlašovací údaje* – Informace, které Azure používá k ověření vaší identity a zajištění vašeho oprávnění k přístupu k prostředkům v Azure.

V předchozích verzích se kontext Azure musel vytvořit při každém otevření nové relace PowerShellu. Od Azure PowerShellu verze 4.4.0 můžete povolit automatické ukládání a opětovné použití kontextů Azure, kdykoli otevřete novou relaci PowerShellu.

## <a name="automatically-saving-the-context-for-the-next-login"></a>Automatické ukládání kontextu pro další přihlášení

Azure PowerShell ve výchozím nastavení zahodí informace o kontextu při zavření relace PowerShellu.

Pokud chcete povolit, aby si Azure PowerShell pamatoval kontext po zavření relace PowerShellu, použijte `Enable-AzureRmContextAutosave`. Informace o kontextu a přihlašovacích údajích se automaticky uloží do speciální skryté složky v uživatelském adresáři (`%AppData%\Roaming\Windows Azure PowerShell`).
Následně bude každá nová relace PowerShellu cílit na kontext použitý v poslední relaci.

Pokud chcete PowerShell nastavit tak, aby kontext a přihlašovací údaje zapomínal, použijte `Disable-AzureRmContextAutoSave`. Při každém otevření relace PowerShellu se budete muset přihlásit k Azure.

Rutiny umožňující správu kontextů Azure umožňují také podrobné řízení. Pokud chcete, změny se můžou použít pouze pro aktuální relaci PowerShellu, (rozsah `Process`) nebo pro každou relaci PowerShellu (rozsah `CurrentUser`). Podrobnější popis těchto možností najdete v části [Používání rozsahů kontextu](#Using-Context-Scopes).

## <a name="running-azure-powershell-cmdlets-as-background-jobs"></a>Spouštění rutin Azure PowerShellu jako úloh na pozadí

Funkce **automatického ukládání kontextu Azure** umožňuje také sdílení kontextu s úlohami PowerShellu na pozadí. PowerShell umožňuje spouštět a monitorovat dlouhotrvající úlohy jako úlohy na pozadí bez nutnosti čekat na jejich dokončení. Přihlašovací údaje můžete s úlohami na pozadí sdílet dvěma různými způsoby:

- Předání kontextu jako argumentu

  Většina rutin AzureRM umožňuje předání kontextu do rutiny v podobě parametru. Kontext můžete do úlohy na pozadí předat způsobem znázorněným v následujícím příkladu:

  ```powershell
  PS C:\> $job = Start-Job { param ($ctx) New-AzureRmVm -AzureRmContext $ctx [... Additional parameters ...]} -ArgumentList (Get-AzureRmContext)
  ```

- Použití výchozího kontextu s povoleným automatickým ukládáním

  Pokud jste povolili **automatické ukládání kontextu**, úlohy na pozadí automaticky používají výchozí uložený kontext.

  ```powershell
  PS C:\> $job = Start-Job { New-AzureRmVm [... Additional parameters ...]}
  ```

Pokud potřebujete znát výsledek úlohy na pozadí, použijte `Get-Job` ke kontrole stavu úlohy a `Wait-Job` k čekání na dokončení úlohy. Pomocí `Receive-Job` můžete zachytit nebo zobrazit výstup úlohy na pozadí. Další informace najdete v tématu [Informace o úlohách](/powershell/module/microsoft.powershell.core/about/about_jobs).

## <a name="creating-selecting-renaming-and-removing-contexts"></a>Vytvoření, výběr, přejmenování a odebrání kontextů

Pokud chcete vytvořit kontext, musíte být přihlášeni k Azure. Rutina `Add-AzureRmAccount` (nebo její alias `Login-AzureRmAccount`) nastaví výchozí kontext používaný dalšími rutinami Azure PowerShellu a umožňuje přístup ke všem tenantům a předplatným, které povolují vaše přihlašovací údaje.

Pokud chcete po přihlášení přidat nový kontext, použijte rutinu `Set-AzureRmContext` (nebo její alias `Select-AzureRmSubscription`).

```powershell
PS C:\> Set-AzureRMContext -Subscription "Contoso Subscription 1" -Name "Contoso1"
```

Předchozí příklad přidá nový kontext s cílem Contoso Subscription 1 s použitím vašich aktuálních přihlašovacích údajů. Nový kontext se pojmenuje Contoso1. Pokud pro kontext nezadáte název, použije se výchozí název vycházející z ID účtu a ID předplatného.

Pokud chcete přejmenovat existující kontext, použijte rutinu `Rename-AzureRmContext`. Příklad:

```powershell
PS C:\> Rename-AzureRmContext '[user1@contoso.org; 123456-7890-1234-564321]` 'Contoso2'
```

Tento příklad přejmenuje kontext s automaticky nastaveným názvem `[user1@contoso.org; 123456-7890-1234-564321]` na jednodušší název Contoso2. Rutiny určené pro správu kontextů také používají dokončování pomocí tabulátoru umožňující rychlý výběr kontextu.

Pokud chcete nakonec odebrat kontext, použijte rutinu `Remove-AzureRmContext`.  Příklad:

```powershell
PS C:\> Remove-AzureRmContext Contoso2
```

Zapomene kontext s názvem Contoso2. Následně můžete tento kontext znovu vytvořit pomocí `Set-AzureRmContext`.

## <a name="removing-credentials"></a>Odebrání přihlašovacích údajů

Všechny přihlašovací údaje a kontexty přidružené k uživateli nebo instančnímu objektu můžete odebrat pomocí `Remove-AzureRmAccount` (označuje se také jako `Logout-AzureRmAccount`). Pokud se rutina `Remove-AzureRmAccount` provede bez parametrů, odebere všechny přihlašovací údaje a kontexty přidružené k uživateli nebo instančnímu objektu v aktuálním kontextu. Pokud chcete cílit na konkrétní instanční objekt, můžete předat uživatelské jméno, hlavní název služby (SPN) nebo kontext.

```powershell
Remove-AzureRmAccount user1@contoso.org
```

## <a name="using-context-scopes"></a>Používání rozsahů kontextu

Občas můžete chtít vybrat, změnit nebo odebrat kontext v relaci PowerShellu, aniž by to ovlivnilo ostatní relace. Pokud chcete změnit výchozí chování rutin pracujících s kontextem, použijte parametr `Scope`. Rozsah `Process` přepíše výchozí chování tak, že se bude vztahovat pouze na aktuální relaci. Naopak rozsah `CurrentUser` změní kontext ve všech relacích, a ne pouze v aktuální relaci.

Například pokud chcete změnit výchozí kontext v aktuální relaci PowerShellu, aniž by to ovlivnilo ostatní okna, nebo kontext, který se použije při dalším otevření relace, použijte:

```powershell
PS C:\> Select-AzureRmContext Contoso1 -Scope Process
```

## <a name="how-the-context-autosave-setting-is-remembered"></a>Způsob zapamatování nastavení automatického ukládání kontextu

Nastavení automatického ukládání kontextu se ukládá do uživatelského adresáře Azure PowerShellu (`%AppData%\Roaming\Windows Azure PowerShell`). Některé druhy účtů počítače k tomuto adresáři nemusejí mít přístup. Pro takové scénáře můžete použít proměnnou prostředí.

```powershell
$env:AzureRmContextAutoSave="true" | "false"
```

Pokud je nastavena na true, kontext se automaticky uloží. Pokud je nastavena na false, kontext se neuloží.

## <a name="changes-to-the-azurermprofile-module"></a>Změny modulu AzureRM.Profile

Nové rutiny pro správu kontextu

- [Enable-AzureRmContextAutosave][enable] – Povolení ukládání kontextu mezi relacemi PowerShellu.
  Všechny změny mění globální kontext.
- [Disable-AzureRmContextAutosave][disable] – Vypnutí automatického ukládání kontextu. V každé nové relaci PowerShellu se vyžaduje opětovné přihlášení.
- [Select-AzureRmContext][select] – Výběr kontextu jako výchozího. Všechny další rutiny k ověřování používají přihlašovací údaje v tomto kontextu.
- [Remove-AzureRmAccount][remove-cred] – Odebrání všech přihlašovacích údajů a kontextů přidružených k účtu.
- [Remove-AzureRmContext][remove-context] – Odebrání pojmenovaného kontextu.
- [Rename-AzureRmContext][rename] – Odebrání existujícího kontextu.

Změny existujících rutin pracujících s profilem

- [Add-AzureRmAccount][login] – Povolení nastavení rozsahu přihlášení na příslušný proces nebo aktuálního uživatele.
  Povolení pojmenování výchozího kontextu po přihlášení.
- [Import-AzureRmContext][import] – Povolení nastavení rozsahu přihlášení na příslušný proces nebo aktuálního uživatele.
- [Set-AzureRmContext][set-context] – Povolení výběru existujících pojmenovaných kontextů a změna rozsahu na příslušný proces nebo aktuálního uživatele.

<!-- Hyperlinks -->
[enable]: /powershell/module/azurerm.profile/Enable-AzureRmContextAutosave
[disable]: /powershell/module/azurerm.profile/Disable-AzureRmContextAutosave
[select]: /powershell/module/azurerm.profile/Select-AzureRmContext
[remove-cred]: /powershell/module/azurerm.profile/Remove-AzureRmAccount
[remove-context]: /powershell/module/azurerm.profile/Remove-AzureRmContext
[rename]: /powershell/module/azurerm.profile/Rename-AzureRmContext

<!-- Updated cmdlets -->
[login]: /powershell/module/azurerm.profile/Add-AzureRmAccount
[import]: /powershell/module/azurerm.profile/Import-AzureRmAccount
[set-context]: /powershell/module/azurerm.profile/Import-AzureRmContext
