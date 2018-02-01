---
title: "Instalace a konfigurace Azure PowerShellu v systémech macOS a Linux | Dokumentace Microsoftu"
description: "Postup instalace a konfigurace Azure PowerShellu pro první použití v systému macOS nebo Linux"
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 01/12/2018
ms.openlocfilehash: 64a86dfd4af7f3f0a91501e9a096ff190f7100cb
ms.sourcegitcommit: 72f56597f0329d35779a3ea4ccea6293f0fd2502
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a>Instalace a konfigurace Azure PowerShellu v systémech macOS a Linux

Nyní je možné nainstalovat PowerShell Core v6 a Azure PowerShell na jiných platformách než Windows.
Proces instalace Azure PowerShellu v systému macOS a Linux se neliší od Windows, ale je potřeba nejdřív nainstalovat PowerShell Core v6.

> [!NOTE]

> V tuto chvíli jsou PowerShell Core v6 i PowerShell Azure pro .NET Core stále ve verzi beta.
> Podpora pro tyto produkty je omezená. Pokud máte problémy nebo zjistíte chyby, zaznamenejte prosím problémy v GitHubu.
>
> * [Problémy PowerShellu Core v6](https://github.com/PowerShell/PowerShell/issues)
> * [Problémy Azure PowerShellu](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-core-v6"></a>Krok 1: Instalace PowerShellu Core v6

Proces instalace PowerShellu Core v6 se liší v závislosti na cílovém operačním systému.
I když je možné nainstalovat PowerShell Core v6 ve Windows, tento článek se zaměřuje na systémy macOS a Linux. Pokud chcete používat Azure PowerShell ve Windows, přečtěte si téma o [instalaci](./install-azurerm-ps.md) ve Windows.

Instalace **PowerShellu Core v6** v Linuxu nebo macOS se liší v závislosti na linuxové distribuci a verzi operačního systému.
Podrobné pokyny najdete v následujícím článku:

- [Instalace PowerShellu Core v macOS a Linuxu](/powershell/scripting/setup/installing-powershell-core-on-macos-and-linux)

## <a name="step-2-install-azure-powershell-for-net-core"></a>Krok 2: Instalace Azure PowerShellu pro .NET Core

PowerShell Core v6 se dodává s už nainstalovaným modulem PowerShellGet. To usnadňuje instalaci libovolného modulu, který se publikuje v Galerii prostředí PowerShell. Pokud chcete nainstalovat Azure PowerShell, otevřete novou relaci PowerShellu a spusťte následující příkaz:

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a>Krok 3: Načtení modulu AzureRM.Netcore

Jakmile je modul nainstalovaný, je potřeba modul načíst do relace PowerShellu. Moduly se načítají pomocí rutiny `Import-Module` následujícím způsobem:

```powershell
Import-Module AzureRM.Netcore
Import-Module AzureRM.Profile.Netcore
```

Po dokončení importu můžete otestovat nově nainstalovaný modul pokusem o přihlášení do Azure pomocí následujícího příkazu:

```powershell
Login-AzureRMAccount
```

Výše uvedený příkaz by měl zobrazit výzvu k přechodu na adresu `https://aka.ms/devicelogin` a zadání poskytnutého kódu.

## <a name="available-cmdlets"></a>Dostupné rutiny

Moduly Azure PowerShellu pro .NET Standard jsou stále ve vývoji. Tyto moduly neposkytují úplnou sadu rutin, které jsou k dispozici pro verzi modulů pro Windows. Následující funkce jsou implementované v modulech AzureRM.Netcore:

* Správa účtů
  - Přihlášení pomocí účtu Microsoft, účtu organizace nebo instančního objektu pomocí Microsoft Azure Active Directory
  - Uložení přihlašovacích údajů na disk pomocí Save-AzureRmContext a načtení uložených přihlašovacích údajů pomocí Import-AzureRmContext
* Prostředí
  - Získání různých okamžitě dostupných prostředí Microsoft Azure
  - Přidání, nastavení či odebrání přizpůsobených prostředí (například prostředí Azure Stack nebo Windows Azure Pack)
* Rutiny na úrovni správy pro služby Azure s využitím rozhraní Resource Manageru a Správy služeb.
  - Virtuální počítač
  - App Service (Websites)
  - Databáze SQL
  - Úložiště
  - Síť

## <a name="next-steps"></a>Další kroky

Další informace o použití Azure PowerShellu najdete v tématu [Začínáme s Azure PowerShellem](get-started-azureps.md).
