---
title: Instalace a konfigurace Azure Powershellu | Dokumentace Microsoftu
description: Jak nainstalovat a nakonfigurovat Azure PowerShell
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/17/2017
ms.openlocfilehash: 86bf3ab84b706d44b46f420d07570069f65bde72
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <a name="install-and-configure-azure-powershell"></a>Instalace a konfigurace Azure Powershellu

Preferovanou metodu instalace je instalace Azure PowerShellu z Galerie prostředí PowerShell.

## <a name="step-1-install-powershellget"></a>Krok 1: Instalace modulu PowerShellGet

Instalace položek z Galerie prostředí PowerShell vyžaduje modul PowerShellGet. Ujistěte se, že máte vhodnou verzi modulu PowerShellGet a další požadavky na systém. Spuštěním následujícího příkazu zjistěte, jestli máte PowerShellGet v systému nainstalovaný.

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

Zobrazený výstup by měl vypadat přibližně takto:

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

Pokud nemáte modul PowerShellGet nainstalovaný, přečtěte si v tomto článku část [Jak získat modul PowerShellGet](#how-to-get-powershellget).

> [!NOTE]
> Použití modulu PowerShellGet vyžaduje zásadu spouštění, která umožňuje spouštět skripty. Další informace o zásadě spouštění Powershellu najdete v tématu popisujícím [zásady spouštění](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies).

## <a name="step-2-install-azure-powershell"></a>Krok 2: Instalace Azure PowerShellu

Instalace Azure PowerShellu z Galerie prostředí PowerShell vyžaduje zvýšená oprávnění. Z relace PowerShellu se zvýšenými oprávněními spusťte následující příkaz:

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM
```

Ve výchozím nastavení není galerie prostředí PowerShell nakonfigurovaná pro PowerShellGet jako důvěryhodné úložiště. Při prvním použití PSGallery se zobrazí tato výzva:

```
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

Pokračujte v instalaci výběrem možnosti Ano nebo Ano všem.

> [!NOTE]
> Pokud máte verzi NuGetu, která je starší než 2.8.5.201, zobrazí se výzva ke stažení a instalaci nejnovější verze NuGetu.

Modul AzureRM je kumulativní modul pro rutiny Azure Resource Manageru. Při instalaci modulu AzureRM se z Galerie prostředí PowerShell stáhnou a nainstalují všechny ostatní moduly Azure, které nebyly nainstalované dřív.

Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, může se zobrazit chyba. Postup řešení tohoto problému najdete v části [Aktualizace na novou verzi Azure PowerShellu](#update-azps) v tomto článku.

## <a name="step-3-load-the-azurerm-module"></a>Krok 3: Načtení modulu AzureRM
Jakmile je modul nainstalovaný, je potřeba modul načíst do relace PowerShellu. Toto byste měli udělat v normální relaci PowerShellu, a nikoli v relaci se zvýšenými oprávněními. Moduly se načítají pomocí rutiny `Import-Module` následujícím způsobem:

```powershell
Import-Module AzureRM
```

## <a name="next-steps"></a>Další kroky

Další informace o použití Azure PowerShellu najdete v následujících článcích:

* [Začínáme s Azure PowerShellem](get-started-azureps.md)

## <a name="reporting-issues-and-feedback"></a>Hlášení chyb a poskytnutí zpětné vazby

Pokud v nástroji narazíte na jakékoli chyby, přidejte problém v části [Issues](https://github.com/Azure/azure-powershell/issues) (Problémy) našeho úložiště GitHub. Pokud chcete poskytnout zpětnou vazbu z příkazového řádku, použijte rutinu `Send-Feedback`.

## <a name="frequently-asked-questions"></a>Nejčastější dotazy

### <a name="how-to-get-powershellget"></a>Jak získat modul PowerShellGet

|Verze operačního systému|Pokyny pro instalaci|
|---|---|
|Mám Windows 10 nebo Windows Server 2016|Integrovaný do Windows Management Frameworku (WMF) 5.0 jako součást operačního systému|
|Chci upgradovat na PowerShell 5|[Instalace nejnovější verze WMF](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|Používám verzi Windows s PowerShellem 3 nebo 4|[Získání modulů PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a>Kontrola verze Azure PowerShellu

I když vám doporučujeme upgradovat na nejnovější verzi co možná nejdříve, podporuje se několik verzí Azure PowerShellu. Pokud chcete zjistit nainstalovanou verzi Azure PowerShellu, spusťte z příkazového řádku příkaz `Get-Module AzureRM`.

```powershell
Get-Module AzureRM -list | Select-Object Name,Version,Path
```

### <a name="support-for-classic-deployment-methods"></a>Podpora metod nasazení Classic

Pokud máte nasazení, která používají model nasazení Classic, můžete nainstalovat verzi správy služeb Azure PowerShellu. Další informace najdete v tématu popisujícím [instalaci modulu správy služeb Azure PowerShellu](/powershell/azure/servicemanagement/install-azure-ps). Moduly Azure a AzureRM sdílejí společné závislosti. Pokud používáte moduly Azure i AzureRM, měli byste nainstalovat stejnou verzi obou balíčků.

### <a id="update-azps"></a>Aktualizace na novou verzi Azure PowerShellu

Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, která obsahuje modul správy služby, může se zobrazit následující chyba:

```
PackageManagement\Install-Package : A command with name 'Get-AzureStorageContainerAcl' is already
available on this system. This module 'Azure.Storage' may override the existing commands. If you
still want to install this module 'Azure.Storage', use -AllowClobber parameter.

At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1772 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
    + FullyQualifiedErrorId : CommandAlreadyAvailable,Validate-ModuleCommandAlreadyAvailable,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

Jak uvádí chybová zpráva, musíte modul nainstalovat pomocí parametru -AllowClobber. Použijte následující příkaz:

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM -AllowClobber
```

Další informace najdete v tématu nápovědy k rutině [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).

### <a name="installing-module-versions-side-by-side"></a>Instalace verzí modulu vedle sebe

Metoda instalace PowerShellGet je jedinou metodou, která podporuje instalaci více verzí. Můžete mít například skripty, které jsou napsané v předchozí verzi Azure PowerShellu, a vy nemáte čas nebo prostředky je aktualizovat. Následující příkazy ukazují, jak nainstalovat víc verzí Azure PowerShellu:

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

Do relace PowerShellu se dá načíst jenom jedna verze modulu. Pokud chcete importovat konkrétní verzi rutin AzureRM, musíte otevřít nové okno PowerShellu a použít příkaz `Import-Module`:

```powershell
Import-Module AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> Verze 2.1.0 a verze 1.2.6 jsou první verze modulu navržené tak, aby se daly instalovat vedle sebe. Při načítání starší verze Azure PowerShellu se na načtou nekompatibilní verze modulu **AzureRM.Profile**. Výsledkem je to, že rutiny zobrazí výzvu k přihlášení při každém spuštění rutiny.

### <a name="other-installation-methods"></a>Jiné metody instalace

Informace o instalaci pomocí instalačního programu webové platformy nebo balíčku MSI najdete v popisu [jiných metod instalace](other-install.md).
