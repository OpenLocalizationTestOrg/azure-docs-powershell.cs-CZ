---
title: "Instalace a konfigurace modulu správy služeb prostředí Azure PowerShell | Dokumentace Microsoftu"
description: Jak nainstalovat a nakonfigurovat Azure PowerShell
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/06/2017
ms.openlocfilehash: 164af369d49e3044e5409c28d8b6145ebc067313
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2017
---
# <a name="installing-the-azure-powershell-service-management-module"></a>Instalace modulu správy služeb prostředí Azure PowerShell

Preferovanou metodu instalace je instalace Azure PowerShellu z [Galerie prostředí PowerShell](https://www.powershellgallery.com/).

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

Pokud nemáte modul PowerShellGet nainstalovaný, přečtěte část [Jak získat modul PowerShellGet](#how-to-get-powershellget).

## <a name="step-2-install-azure-powershell"></a>Krok 2: Instalace Azure PowerShellu

Z konzoly prostředí Windows PowerShell spusťte následující příkaz jako správce:

```powershell
Install-Module Azure
```

Modul Azure je kumulativní modul pro rutiny Azure Resource Manageru. Při instalaci modulu AzureRM se z Galerie prostředí PowerShell stáhnou a nainstalují všechny ostatní moduly Azure, které nebyly nainstalované dřív.

Modul správy služeb Azure sdílí závislosti s moduly Resource Manageru prostředí Azure PowerShell. Pokud jste nainstalovali moduly Resource Manageru prostředí Azure PowerShell, budete muset přidat do instalačního příkazu parametr `-AllowClobber`. Díky tomu lze aktualizovat existující sdílené závislosti. Bez tohoto parametru se instalace modulu nezdaří.

```powershell
Install-Module Azure -AllowClobber
```

Když nainstalujete tento modul, můžete importovat modul spuštěním následujícího příkazu:

```powershell
Import-Module Azure
```

## <a name="to-use-the-cmdlets"></a>Používání rutin

Pokud chcete začít pracovat s rutinami pro správu služeb Azure, nejprve se přihlaste k účtu Azure. Chcete-li se přihlásit k účtu, spusťte následující příkaz:

```powershell
Add-AzureAccount
```

Po přihlášení k Azure prostředí Azure PowerShell vytvoří kontext pro danou relaci. Tento kontext obsahuje prostředí Azure PowerShell, účet, tenanta a předplatné, které se použije pro všechny rutiny v rámci této relace. Nyní jste připraveni používat následující moduly.

## <a name="azure-service-management-cmdlets"></a>Rutiny správy služeb Azure

Moduly prostředí Azure PowerShell se často aktualizují. Pokud si všimnete, že online nápověda k rutinám uvádí rutiny nebo parametry, které modul neobsahuje, stáhněte a nainstalujte nejnovější verzi modulu. Chcete-li zjistit verzi modulu, zadejte: `(Get-Module Azure).Version`.

Ukázkové skripty, které vám pomůžou automatizovat některé běžné úlohy v Azure, najdete v [centru skriptů Windows Azure](http://www.windowsazure.com/documentation/scripts/).

Obecné informace o instalaci prostředí Windows PowerShell, seznamování s ním, jeho používání a přizpůsobování najdete v článku [Skriptování v prostředí Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210).

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
