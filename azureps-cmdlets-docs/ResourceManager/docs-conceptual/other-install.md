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
ms.openlocfilehash: 73c099375cecc8abdd5d6179109513946e7e793b
ms.sourcegitcommit: 202ec2df66c40a60f47ea06b30a6701ad444d229
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2017
---
# <a name="other-installation-methods"></a><span data-ttu-id="7d163-103">Jiné metody instalace</span><span class="sxs-lookup"><span data-stu-id="7d163-103">Other installation methods</span></span>

<span data-ttu-id="7d163-104">Prostředí Azure PowerShell podporuje několik metod instalace.</span><span class="sxs-lookup"><span data-stu-id="7d163-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="7d163-105">Upřednostňovaným způsobem je použití modulu PowerShellGet v Galerii prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d163-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="7d163-106">Prostředí Azure PowerShell můžete nainstalovat ve Windows s použitím instalačního programu webové platformy (WebPI) nebo s použitím souboru MSI, který je k dispozici na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="7d163-106">Azure PowerShell can be installed on Windows using the Web Platform Installer (WebPI) or by using the MSI file available from GitHub.</span></span> <span data-ttu-id="7d163-107">Azure PowerShell jde také nainstalovat v kontejneru s Dockerem.</span><span class="sxs-lookup"><span data-stu-id="7d163-107">Azure PowerShell can also be installed in a Docker container.</span></span>

## <a name="install-on-windows-using-the-web-platform-installer"></a><span data-ttu-id="7d163-108">Instalace ve Windows s použitím instalačního programu webové platformy</span><span class="sxs-lookup"><span data-stu-id="7d163-108">Install on Windows using the Web Platform Installer</span></span>

<span data-ttu-id="7d163-109">Instalace nejnovější verze prostředí Azure PowerShell z WebPI je stejná jako u předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="7d163-109">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="7d163-110">Stáhněte si [balíček Azure PowerShell WebPI](http://aka.ms/webpi-azps) a spusťte instalaci.</span><span class="sxs-lookup"><span data-stu-id="7d163-110">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="7d163-111">Pokud jste dříve nainstalovali moduly Azure z Galerie prostředí PowerShell, instalační program je automaticky odebere.</span><span class="sxs-lookup"><span data-stu-id="7d163-111">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="7d163-112">Tím se prostředí zjednoduší, protože se zajistí, že je nainstalována jen jedna verze prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d163-112">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="7d163-113">Existují však situace, v nichž můžete potřebovat mít současně nainstalovaných několik verzí.</span><span class="sxs-lookup"><span data-stu-id="7d163-113">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="7d163-114">Moduly Galerie prostředí PowerShell instalují moduly do umístění `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="7d163-114">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="7d163-115">Instalační program WebPI naproti tomu instaluje moduly Azure do umístění `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="7d163-115">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="7d163-116">Pokud během instalace dojde k chybě, můžete odebrat složky Azure* ve složce `$env:ProgramFiles\WindowsPowerShell\Modules` ručně a zkusit instalaci zopakovat.</span><span class="sxs-lookup"><span data-stu-id="7d163-116">If an error occurs during install, you can manually remove the Azure* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="7d163-117">Po dokončení instalace by součástí nastavení `$env:PSModulePath` měly být adresáře, které obsahují rutiny prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d163-117">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="7d163-118">Pomocí následujícího příkazu můžete ověřit, že je prostředí Azure PowerShell nainstalováno správně.</span><span class="sxs-lookup"><span data-stu-id="7d163-118">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="7d163-119">Při instalaci z WebPI se může vyskytnout známý problém.</span><span class="sxs-lookup"><span data-stu-id="7d163-119">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="7d163-120">Pokud počítač vyžaduje restartování z důvodu aktualizací systému nebo jiných instalací, může to vést k selhání aktualizací `$env:PSModulePath`, takže pak toto nastavení neobsahuje cestu k instalaci prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d163-120">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="7d163-121">Při pokusu o načítání nebo spouštění rutin po instalaci se zobrazí následující chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="7d163-121">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

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

<span data-ttu-id="7d163-122">Tuto chybu je možné odstranit restartováním počítače nebo naimportováním modulu s použitím plně kvalifikované cesty.</span><span class="sxs-lookup"><span data-stu-id="7d163-122">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="7d163-123">Například:</span><span class="sxs-lookup"><span data-stu-id="7d163-123">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-on-windows-using-the-msi-package"></a><span data-ttu-id="7d163-124">Instalaci ve Windows s použitím balíčku MSI</span><span class="sxs-lookup"><span data-stu-id="7d163-124">Install on Windows using the MSI Package</span></span>

<span data-ttu-id="7d163-125">Prostředí Azure PowerShell můžete nainstalovat s použitím souboru MSI, který je k dispozici na [GitHubu](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="7d163-125">Azure PowerShell can be installed using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span> <span data-ttu-id="7d163-126">Pokud jste nainstalovali dřívější verze modulů Azure, instalační program je automaticky odebere.</span><span class="sxs-lookup"><span data-stu-id="7d163-126">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="7d163-127">Balíček MSI instaluje moduly do umístění `$env:ProgramFiles\WindowsPowerShell\Modules`, ale nevytváří složky specifické pro konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="7d163-127">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>

## <a name="install-in-a-docker-container"></a><span data-ttu-id="7d163-128">Instalace v kontejneru s Dockerem</span><span class="sxs-lookup"><span data-stu-id="7d163-128">Install in a Docker container</span></span>

<span data-ttu-id="7d163-129">Udržujeme image Dockeru s předkonfigurovaným Azure PowerShellem.</span><span class="sxs-lookup"><span data-stu-id="7d163-129">We maintain a Docker image preconfigured with Azure PowerShell.</span></span>

<span data-ttu-id="7d163-130">Spusťte kontejner s `docker run`.</span><span class="sxs-lookup"><span data-stu-id="7d163-130">Run the container with `docker run`.</span></span>

```powershell
docker run azuresdk/azure-powershell
```

<span data-ttu-id="7d163-131">Kromě toho udržujeme podmnožinu rutin jako kontejner PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="7d163-131">In addition, we maintain a subset of cmdlets as a PowerShell Core container.</span></span>

<span data-ttu-id="7d163-132">Pro Mac/Linux použijte image `latest`.</span><span class="sxs-lookup"><span data-stu-id="7d163-132">For Mac/Linux, use the `latest` image.</span></span>

```bash
docker run azuresdk/azure-powershell-core:latest
```

<span data-ttu-id="7d163-133">Pro Windows použijte image `nanoserver`.</span><span class="sxs-lookup"><span data-stu-id="7d163-133">For Windows, use the `nanoserver` image.</span></span>

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

<span data-ttu-id="7d163-134">Prostředí Azure PowerShell je v imagi nainstalované prostřednictvím `Install-Module` z [Galerie prostředí PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="7d163-134">Azure PowerShell is installed on the image via `Install-Module` from the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>