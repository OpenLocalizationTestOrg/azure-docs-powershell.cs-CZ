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
ms.openlocfilehash: 9cee582f74b7f3260c6ae167a8ac358d360ad8ab
ms.sourcegitcommit: 45587b5091293288e16cfae8ac412e0d42f8f450
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2017
---
# <a name="other-installation-methods"></a><span data-ttu-id="b0cc2-103">Jiné metody instalace</span><span class="sxs-lookup"><span data-stu-id="b0cc2-103">Other installation methods</span></span>

<span data-ttu-id="b0cc2-104">Prostředí Azure PowerShell podporuje několik metod instalace.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="b0cc2-105">Upřednostňovaným způsobem je použití modulu PowerShellGet v Galerii prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="b0cc2-106">Prostředí Azure PowerShell můžete nainstalovat s použitím instalačního programu webové platformy (WebPI) nebo s použitím souboru MSI, který je k dispozici na [GitHubu](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-106">Azure PowerShell can be installed using the Web Platform Installer (WebPI) or by using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span>

## <a name="docker"></a><span data-ttu-id="b0cc2-107">Docker</span><span class="sxs-lookup"><span data-stu-id="b0cc2-107">Docker</span></span>

<span data-ttu-id="b0cc2-108">Udržujeme image Dockeru s předkonfigurovaným Azure PowerShellem.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-108">We maintain a Docker image preconfigured with Azure PowerShell.</span></span>

<span data-ttu-id="b0cc2-109">Spusťte kontejner s `docker run`.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-109">Run the container with `docker run`.</span></span>

```powershell
docker run azuresdk/azure-powershell
```

<span data-ttu-id="b0cc2-110">Kromě toho udržujeme podmnožinu rutin jako kontejner PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-110">In addition, we maintain a subset of cmdlets as a PowerShell Core container.</span></span>

<span data-ttu-id="b0cc2-111">Pro Mac/Linux použijte image `latest`.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-111">For Mac/Linux, use the `latest` image.</span></span>

```bash
docker run azuresdk/azure-powershell-core:latest
```

<span data-ttu-id="b0cc2-112">Pro Windows použijte image `nanoserver`.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-112">For Windows, use the `nanoserver` image.</span></span>

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

<span data-ttu-id="b0cc2-113">Prostředí Azure PowerShell je v imagi nainstalované prostřednictvím `Install-Module` z [Galerie prostředí PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-113">Azure PowerShell is installed on the image via `Install-Module` from the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

## <a name="install-using-the-web-platform-installer"></a><span data-ttu-id="b0cc2-114">Instalace s použitím instalačního programu webové platformy</span><span class="sxs-lookup"><span data-stu-id="b0cc2-114">Install using the Web Platform Installer</span></span>

<span data-ttu-id="b0cc2-115">Instalace nejnovější verze prostředí Azure PowerShell z WebPI je stejná jako u předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-115">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="b0cc2-116">Stáhněte si [balíček Azure PowerShell WebPI](http://aka.ms/webpi-azps) a spusťte instalaci.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-116">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="b0cc2-117">Pokud jste dříve nainstalovali moduly Azure z Galerie prostředí PowerShell, instalační program je automaticky odebere.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-117">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="b0cc2-118">Tím se prostředí zjednoduší, protože se zajistí, že je nainstalována jen jedna verze prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-118">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="b0cc2-119">Existují však situace, v nichž můžete potřebovat mít současně nainstalovaných několik verzí.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-119">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="b0cc2-120">Moduly Galerie prostředí PowerShell instalují moduly do umístění `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-120">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="b0cc2-121">Instalační program WebPI naproti tomu instaluje moduly Azure do umístění `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-121">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="b0cc2-122">Pokud během instalace dojde k chybě, můžete odebrat složky Azure* ve složce `$env:ProgramFiles\WindowsPowerShell\Modules` ručně a zkusit instalaci zopakovat.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-122">If an error occurs during install, you can manually remove the Azure* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="b0cc2-123">Po dokončení instalace by součástí nastavení `$env:PSModulePath` měly být adresáře, které obsahují rutiny prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-123">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="b0cc2-124">Pomocí následujícího příkazu můžete ověřit, že je prostředí Azure PowerShell nainstalováno správně.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-124">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="b0cc2-125">Při instalaci z WebPI se může vyskytnout známý problém.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-125">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="b0cc2-126">Pokud počítač vyžaduje restartování z důvodu aktualizací systému nebo jiných instalací, může to vést k selhání aktualizací `$env:PSModulePath`, takže pak toto nastavení neobsahuje cestu k instalaci prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-126">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="b0cc2-127">Při pokusu o načítání nebo spouštění rutin po instalaci se zobrazí následující chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="b0cc2-127">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

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

<span data-ttu-id="b0cc2-128">Tuto chybu je možné odstranit restartováním počítače nebo naimportováním modulu s použitím plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-128">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="b0cc2-129">Například:</span><span class="sxs-lookup"><span data-stu-id="b0cc2-129">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-using-the-msi-package"></a><span data-ttu-id="b0cc2-130">Instalaci s použitím balíčku MSI</span><span class="sxs-lookup"><span data-stu-id="b0cc2-130">Install using the MSI Package</span></span>

<span data-ttu-id="b0cc2-131">Prostředí Azure PowerShell můžete nainstalovat s použitím souboru MSI, který je k dispozici na [GitHubu](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="b0cc2-131">Azure PowerShell can be installed using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span> <span data-ttu-id="b0cc2-132">Pokud jste nainstalovali dřívější verze modulů Azure, instalační program je automaticky odebere.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-132">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="b0cc2-133">Balíček MSI instaluje moduly do umístění `$env:ProgramFiles\WindowsPowerShell\Modules`, ale nevytváří složky specifické pro konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="b0cc2-133">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>
