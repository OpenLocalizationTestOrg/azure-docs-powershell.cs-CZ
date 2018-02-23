---
title: "Další způsoby instalace prostředí Azure PowerShell | Dokumentace Microsoftu"
description: "Postup při instalaci prostředí Azure PowerShell s použitím balíčku MSI nebo instalačního programu webové platformy."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 09/06/2017
ms.openlocfilehash: 8a88cce312b4cca002c342c04e1f97b966ae3d2f
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
---
# <a name="other-installation-methods"></a>Jiné metody instalace

Prostředí Azure PowerShell podporuje několik metod instalace. Upřednostňovaným způsobem je použití modulu PowerShellGet v Galerii prostředí PowerShell. Prostředí Azure PowerShell můžete nainstalovat ve Windows s použitím instalačního programu webové platformy (WebPI) nebo s použitím souboru MSI, který je k dispozici na GitHubu. Azure PowerShell jde také nainstalovat v kontejneru s Dockerem.

## <a name="install-on-windows-using-the-web-platform-installer"></a>Instalace ve Windows s použitím instalačního programu webové platformy

Instalace nejnovější verze prostředí Azure PowerShell z WebPI je stejná jako u předchozích verzí.
Stáhněte si [balíček Azure PowerShell WebPI](http://aka.ms/webpi-azps) a spusťte instalaci.

> [!NOTE]
> Pokud jste dříve nainstalovali moduly Azure z Galerie prostředí PowerShell, instalační program je automaticky odebere. Tím se prostředí zjednoduší, protože se zajistí, že je nainstalována jen jedna verze prostředí Azure PowerShell. Existují však situace, v nichž můžete potřebovat mít současně nainstalovaných několik verzí.
>
> Moduly Galerie prostředí PowerShell instalují moduly do umístění `$env:ProgramFiles\WindowsPowerShell\Modules`. Instalační program WebPI naproti tomu instaluje moduly Azure do umístění `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.
>
> Pokud během instalace dojde k chybě, můžete odebrat složky Azure* ve složce `$env:ProgramFiles\WindowsPowerShell\Modules` ručně a zkusit instalaci zopakovat.

Po dokončení instalace by součástí nastavení `$env:PSModulePath` měly být adresáře, které obsahují rutiny prostředí Azure PowerShell. Pomocí následujícího příkazu můžete ověřit, že je prostředí Azure PowerShell nainstalováno správně.

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> Při instalaci z WebPI se může vyskytnout známý problém. Pokud počítač vyžaduje restartování z důvodu aktualizací systému nebo jiných instalací, může to vést k selhání aktualizací `$env:PSModulePath`, takže pak toto nastavení neobsahuje cestu k instalaci prostředí Azure PowerShell.

Při pokusu o načítání nebo spouštění rutin po instalaci se zobrazí následující chybová zpráva:

```
PS C:\> Login-AzureRmAccount
Login-AzureRmAccount : The term 'Login-AzureRmAccount' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:1
+ Login-AzureRmAccount
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Login-AzureRmAccount:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Tuto chybu je možné odstranit restartováním počítače nebo naimportováním modulu s použitím plně kvalifikované cesty. Příklad:

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-on-windows-using-the-msi-package"></a>Instalaci ve Windows s použitím balíčku MSI

Prostředí Azure PowerShell můžete nainstalovat s použitím souboru MSI, který je k dispozici na [GitHubu](https://aka.ms/azps-release). Pokud jste nainstalovali dřívější verze modulů Azure, instalační program je automaticky odebere. Balíček MSI instaluje moduly do umístění `$env:ProgramFiles\WindowsPowerShell\Modules`, ale nevytváří složky specifické pro konkrétní verzi.

## <a name="install-in-a-docker-container"></a>Instalace v kontejneru s Dockerem

Udržujeme image Dockeru s předkonfigurovaným Azure PowerShellem.

Spusťte kontejner s `docker run`.

```powershell
docker run azuresdk/azure-powershell
```

Kromě toho udržujeme podmnožinu rutin jako kontejner PowerShell Core.

Pro Mac/Linux použijte image `latest`.

```bash
docker run azuresdk/azure-powershell-core:latest
```

Pro Windows použijte image `nanoserver`.

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

Prostředí Azure PowerShell je v imagi nainstalované prostřednictvím `Install-Module` z [Galerie prostředí PowerShell](https://www.powershellgallery.com/).
