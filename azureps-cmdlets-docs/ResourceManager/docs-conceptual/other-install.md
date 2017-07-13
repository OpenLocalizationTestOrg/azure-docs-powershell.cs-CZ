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
ms.date: 05/15/2017
ms.openlocfilehash: 368404bcb5218814b4965bb1bcda1e2876441d2a
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="f7b0a-103">Jiné metody instalace</span><span class="sxs-lookup"><span data-stu-id="f7b0a-103">Other installation methods</span></span>
<a id="other-installation-methods" class="xliff"></a>

<span data-ttu-id="f7b0a-104">Prostředí Azure PowerShell podporuje několik metod instalace.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="f7b0a-105">Upřednostňovaným způsobem je použití modulu PowerShellGet v Galerii prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="f7b0a-106">Prostředí Azure PowerShell můžete nainstalovat s použitím instalačního programu webové platformy (WebPI) nebo s použitím souboru MSI, který je k dispozici na [GitHubu](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="f7b0a-106">Azure PowerShell can be installed using the Web Platform Installer (WebPI) or by using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span>

## <span data-ttu-id="f7b0a-107">Instalace s použitím instalačního programu webové platformy</span><span class="sxs-lookup"><span data-stu-id="f7b0a-107">Install using the Web Platform Installer</span></span>
<a id="install-using-the-web-platform-installer" class="xliff"></a>

<span data-ttu-id="f7b0a-108">Instalace nejnovější verze prostředí Azure PowerShell z WebPI je stejná jako u předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-108">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="f7b0a-109">Stáhněte si [balíček Azure PowerShell WebPI](http://aka.ms/webpi-azps) a spusťte instalaci.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-109">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="f7b0a-110">Pokud jste dříve nainstalovali moduly Azure z Galerie prostředí PowerShell, instalační program je automaticky odebere.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-110">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="f7b0a-111">Tím se prostředí zjednoduší, protože se zajistí, že je nainstalována jen jedna verze prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-111">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="f7b0a-112">Existují však situace, v nichž můžete potřebovat mít současně nainstalovaných několik verzí.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-112">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="f7b0a-113">Moduly Galerie prostředí PowerShell instalují moduly do umístění `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-113">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="f7b0a-114">Instalační program WebPI naproti tomu instaluje moduly Azure do umístění `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-114">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="f7b0a-115">Pokud během instalace dojde k chybě, můžete odebrat složky Azure* ve složce `$env:ProgramFiles\WindowsPowerShell\Modules` ručně a zkusit instalaci zopakovat.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-115">If an error occurs during install, you can manually remove the Azure* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="f7b0a-116">Po dokončení instalace by součástí nastavení `$env:PSModulePath` měly být adresáře, které obsahují rutiny prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-116">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="f7b0a-117">Pomocí následujícího příkazu můžete ověřit, že je prostředí Azure PowerShell nainstalováno správně.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-117">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="f7b0a-118">Při instalaci z WebPI se může vyskytnout známý problém.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-118">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="f7b0a-119">Pokud počítač vyžaduje restartování z důvodu aktualizací systému nebo jiných instalací, může to vést k selhání aktualizací `$env:PSModulePath`, takže pak toto nastavení neobsahuje cestu k instalaci prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-119">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="f7b0a-120">Při pokusu o načítání nebo spouštění rutin po instalaci se zobrazí následující chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="f7b0a-120">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

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

<span data-ttu-id="f7b0a-121">Tuto chybu je možné odstranit restartováním počítače nebo naimportováním modulu s použitím plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-121">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="f7b0a-122">Například:</span><span class="sxs-lookup"><span data-stu-id="f7b0a-122">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <span data-ttu-id="f7b0a-123">Instalaci s použitím balíčku MSI</span><span class="sxs-lookup"><span data-stu-id="f7b0a-123">Install using the MSI Package</span></span>
<a id="install-using-the-msi-package" class="xliff"></a>

<span data-ttu-id="f7b0a-124">Prostředí Azure PowerShell můžete nainstalovat s použitím souboru MSI, který je k dispozici na [GitHubu](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="f7b0a-124">Azure PowerShell can be installed using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span> <span data-ttu-id="f7b0a-125">Pokud jste nainstalovali dřívější verze modulů Azure, instalační program je automaticky odebere.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-125">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="f7b0a-126">Balíček MSI instaluje moduly do umístění `$env:ProgramFiles\WindowsPowerShell\Modules`, ale nevytváří složky specifické pro konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="f7b0a-126">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>
