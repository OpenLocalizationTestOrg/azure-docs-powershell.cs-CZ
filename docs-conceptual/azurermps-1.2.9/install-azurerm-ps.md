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
ms.date: 03/27/2018
ms.openlocfilehash: 993c9570b7fe81e5be68b8d82943f2135aed2337
ms.sourcegitcommit: 8376e0bc5f862d382d7283ba72990e3707591e7b
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2018
---
# <a name="install-and-configure-azure-powershell"></a><span data-ttu-id="ecf1e-103">Instalace a konfigurace Azure Powershellu</span><span class="sxs-lookup"><span data-stu-id="ecf1e-103">Install and configure Azure PowerShell</span></span>

<span data-ttu-id="ecf1e-104">Preferovanou metodu instalace je instalace Azure PowerShellu z Galerie prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-104">Installing Azure PowerShell from the PowerShell Gallery is the preferred method of installation.</span></span>

## <a name="step-1-install-powershellget"></a><span data-ttu-id="ecf1e-105">Krok 1: Instalace modulu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="ecf1e-105">Step 1: Install PowerShellGet</span></span>

<span data-ttu-id="ecf1e-106">Instalace položek z Galerie prostředí PowerShell vyžaduje modul PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="ecf1e-107">Ujistěte se, že máte vhodnou verzi modulu PowerShellGet a další požadavky na systém.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="ecf1e-108">Spuštěním následujícího příkazu zjistěte, jestli máte PowerShellGet v systému nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module -Name PowerShellGet -ListAvailable | Select-Object -Property Name,Version,Path
```

<span data-ttu-id="ecf1e-109">Zobrazený výstup by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-109">You should see something similar to the following output:</span></span>

```Output
Name          Version Path
----          ------- ----
Name          Version Path
----          ------- ----
PowerShellGet 1.6.0   C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PowerShellGet.psd1
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="ecf1e-110">Potřebujete PowerShellGet verze 1.1.2.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-110">You need PowerShellGet version 1.1.2.0 or higher.</span></span> <span data-ttu-id="ecf1e-111">Pokud chcete PowerShellGet aktualizovat, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-111">To update PowerShellGet, use the following command:</span></span>

```powershell
Install-Module PowerShellGet -Force
```

<span data-ttu-id="ecf1e-112">Pokud nemáte modul PowerShellGet nainstalovaný, přečtěte si v tomto článku část [Jak získat modul PowerShellGet](#how-to-get-powershellget).</span><span class="sxs-lookup"><span data-stu-id="ecf1e-112">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](#how-to-get-powershellget) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="ecf1e-113">Použití modulu PowerShellGet vyžaduje zásadu spouštění, která umožňuje spouštět skripty.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-113">Using PowerShellGet requires an Execution Policy that allows you to run scripts.</span></span> <span data-ttu-id="ecf1e-114">Další informace o zásadě spouštění Powershellu najdete v tématu popisujícím [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="ecf1e-114">For more information about PowerShell's Execution Policy, see [About Execution Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="step-2-install-azure-powershell"></a><span data-ttu-id="ecf1e-115">Krok 2: Instalace Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="ecf1e-115">Step 2: Install Azure PowerShell</span></span>

<span data-ttu-id="ecf1e-116">Instalace Azure PowerShellu z Galerie prostředí PowerShell vyžaduje zvýšená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-116">Installing Azure PowerShell from the PowerShell Gallery requires elevated privileges.</span></span> <span data-ttu-id="ecf1e-117">Z relace PowerShellu se zvýšenými oprávněními spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-117">Run the following command from an elevated PowerShell session:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module -Name AzureRM -AllowClobber
```

<span data-ttu-id="ecf1e-118">Ve výchozím nastavení není galerie prostředí PowerShell nakonfigurovaná pro PowerShellGet jako důvěryhodné úložiště.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-118">By default, the PowerShell gallery is not configured as a Trusted repository for PowerShellGet.</span></span> <span data-ttu-id="ecf1e-119">Při prvním použití PSGallery se zobrazí tato výzva:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-119">The first time you use the PSGallery you see the following prompt:</span></span>

```Output
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

<span data-ttu-id="ecf1e-120">Pokračujte v instalaci výběrem možnosti Ano nebo Ano všem.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-120">Answer 'Yes' or 'Yes to All' to continue with the installation.</span></span>

> [!NOTE]
> <span data-ttu-id="ecf1e-121">Pokud máte verzi NuGetu, která je starší než 2.8.5.201, zobrazí se výzva ke stažení a instalaci nejnovější verze NuGetu.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-121">If you have a version older than 2.8.5.201 of NuGet, you are prompted to download and install the latest version of NuGet.</span></span>

<span data-ttu-id="ecf1e-122">Modul AzureRM je kumulativní modul pro rutiny Azure Resource Manageru.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-122">The AzureRM module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="ecf1e-123">Při instalaci modulu AzureRM se z Galerie prostředí PowerShell stáhnou a nainstalují všechny ostatní moduly Azure, které nebyly nainstalované dřív.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-123">When you install the AzureRM module, any Azure PowerShell module not previously installed is downloaded and from the PowerShell Gallery.</span></span>

<span data-ttu-id="ecf1e-124">Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, může se zobrazit chyba.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-124">If you have a previous version of Azure PowerShell installed you may receive an error.</span></span> <span data-ttu-id="ecf1e-125">Postup řešení tohoto problému najdete v části [Aktualizace na novou verzi Azure PowerShellu](#update-azps) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-125">To resolve this issue, see the [Updating to a new version of Azure PowerShell](#update-azps) section of this article.</span></span>

## <a name="step-3-load-the-azurerm-module"></a><span data-ttu-id="ecf1e-126">Krok 3: Načtení modulu AzureRM</span><span class="sxs-lookup"><span data-stu-id="ecf1e-126">Step 3: Load the AzureRM module</span></span>
<span data-ttu-id="ecf1e-127">Jakmile je modul nainstalovaný, je potřeba modul načíst do relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-127">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="ecf1e-128">Toto byste měli udělat v normální relaci PowerShellu, a nikoli v relaci se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-128">You should do this in a normal (non-elevated) PowerShell session.</span></span> <span data-ttu-id="ecf1e-129">Moduly se načítají pomocí rutiny `Import-Module` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-129">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module -Name AzureRM
```

## <a name="next-steps"></a><span data-ttu-id="ecf1e-130">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ecf1e-130">Next Steps</span></span>

<span data-ttu-id="ecf1e-131">Další informace o použití Azure PowerShellu najdete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-131">For more information about using Azure PowerShell, see the following articles:</span></span>

* [<span data-ttu-id="ecf1e-132">Začínáme s Azure PowerShellem</span><span class="sxs-lookup"><span data-stu-id="ecf1e-132">Get started with Azure PowerShell</span></span>](get-started-azureps.md)

## <a name="frequently-asked-questions"></a><span data-ttu-id="ecf1e-133">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="ecf1e-133">Frequently asked questions</span></span>

### <a name="how-to-get-powershellget"></a><span data-ttu-id="ecf1e-134">Jak získat modul PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="ecf1e-134">How to get PowerShellGet</span></span>

|<span data-ttu-id="ecf1e-135">Verze operačního systému</span><span class="sxs-lookup"><span data-stu-id="ecf1e-135">OS Version</span></span>|<span data-ttu-id="ecf1e-136">Pokyny pro instalaci</span><span class="sxs-lookup"><span data-stu-id="ecf1e-136">Install instructions</span></span>|
|---|---|
|<span data-ttu-id="ecf1e-137">Mám Windows 10 nebo Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ecf1e-137">I have Windows 10 or Windows Server 2016</span></span>|<span data-ttu-id="ecf1e-138">Integrovaný do Windows Management Frameworku (WMF) 5.0 jako součást operačního systému</span><span class="sxs-lookup"><span data-stu-id="ecf1e-138">Built into Windows Management Framework (WMF) 5.0 included in the OS</span></span>|
|<span data-ttu-id="ecf1e-139">Chci upgradovat na PowerShell 5</span><span class="sxs-lookup"><span data-stu-id="ecf1e-139">I want to upgrade to PowerShell 5</span></span>|[<span data-ttu-id="ecf1e-140">Instalace nejnovější verze WMF</span><span class="sxs-lookup"><span data-stu-id="ecf1e-140">Install the latest version of WMF</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|<span data-ttu-id="ecf1e-141">Používám verzi Windows s PowerShellem 3 nebo 4</span><span class="sxs-lookup"><span data-stu-id="ecf1e-141">I am running on a version of Windows with PowerShell 3 or PowerShell 4</span></span>|[<span data-ttu-id="ecf1e-142">Získání modulů PackageManagement</span><span class="sxs-lookup"><span data-stu-id="ecf1e-142">Get the PackageManagement modules</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a><span data-ttu-id="ecf1e-143">Kontrola verze Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="ecf1e-143">Checking the version of Azure PowerShell</span></span>

<span data-ttu-id="ecf1e-144">I když vám doporučujeme upgradovat na nejnovější verzi co možná nejdříve, podporuje se několik verzí Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-144">Although we encourage you to upgrade to the latest version as early as possible, several versions of Azure PowerShell are supported.</span></span> <span data-ttu-id="ecf1e-145">Pokud chcete zjistit nainstalovanou verzi Azure PowerShellu, spusťte z příkazového řádku příkaz `Get-Module AzureRM`.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-145">To determine the version of Azure PowerShell you have installed, run `Get-Module AzureRM` from your command line.</span></span>

```powershell
Get-Module AzureRM -ListAvailable | Select-Object -Property Name,Version,Path
```

### <a name="support-for-classic-deployment-methods"></a><span data-ttu-id="ecf1e-146">Podpora metod nasazení Classic</span><span class="sxs-lookup"><span data-stu-id="ecf1e-146">Support for classic deployment methods</span></span>

<span data-ttu-id="ecf1e-147">Pokud máte nasazení, která používají model nasazení Classic, můžete nainstalovat verzi správy služeb Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-147">If you have deployments that use the classic deployment model you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="ecf1e-148">Další informace najdete v tématu popisujícím [instalaci modulu správy služeb Azure PowerShellu](/powershell/azure/servicemanagement/install-azure-ps).</span><span class="sxs-lookup"><span data-stu-id="ecf1e-148">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span> <span data-ttu-id="ecf1e-149">Moduly Azure a AzureRM sdílejí společné závislosti.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-149">The Azure and AzureRM modules share common dependencies.</span></span> <span data-ttu-id="ecf1e-150">Pokud používáte moduly Azure i AzureRM, měli byste nainstalovat stejnou verzi obou balíčků.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-150">If you use both the Azure and AzureRM modules, you should install the same version of each package.</span></span>

### <a id="update-azps"></a><span data-ttu-id="ecf1e-151">Aktualizace na novou verzi Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="ecf1e-151">Updating to a new version of Azure PowerShell</span></span>

<span data-ttu-id="ecf1e-152">Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, která obsahuje modul správy služby, může se zobrazit následující chyba:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-152">If you have a previous version of Azure PowerShell installed that includes the Service Management module, you may receive the following error:</span></span>

```Output
PackageManagement\Install-Package : A command with name 'Get-AzureStorageContainerAcl' is already
available on this system. This module 'Azure.Storage' may override the existing commands. If you
still want to install this module 'Azure.Storage', use -AllowClobber parameter.

At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1772 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
    + FullyQualifiedErrorId : CommandAlreadyAvailable,Validate-ModuleCommandAlreadyAvailable,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

<span data-ttu-id="ecf1e-153">Jak uvádí chybová zpráva, musíte modul nainstalovat pomocí parametru -AllowClobber.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-153">As the error message states, you need to use the -AllowClobber parameter to install the module.</span></span> <span data-ttu-id="ecf1e-154">Použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-154">Use the following command:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module -Name AzureRM -AllowClobber
```

<span data-ttu-id="ecf1e-155">Další informace najdete v tématu nápovědy k rutině [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span><span class="sxs-lookup"><span data-stu-id="ecf1e-155">For more information, see the help topic for [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span></span>

### <a name="installing-module-versions-side-by-side"></a><span data-ttu-id="ecf1e-156">Instalace verzí modulu vedle sebe</span><span class="sxs-lookup"><span data-stu-id="ecf1e-156">Installing module versions side by side</span></span>

<span data-ttu-id="ecf1e-157">Metoda instalace PowerShellGet je jedinou metodou, která podporuje instalaci více verzí.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-157">The PowerShellGet method of installation is the only method that supports the installation of multiple versions.</span></span> <span data-ttu-id="ecf1e-158">Můžete mít například skripty, které jsou napsané v předchozí verzi Azure PowerShellu, a vy nemáte čas nebo prostředky je aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-158">For example, you may have scripts written using a previous version of Azure PowerShell that you don't have the time or resources to updated.</span></span> <span data-ttu-id="ecf1e-159">Následující příkazy ukazují, jak nainstalovat víc verzí Azure PowerShellu:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-159">The following commands illustrate how to install multiple versions of Azure PowerShell:</span></span>

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

<span data-ttu-id="ecf1e-160">Do relace PowerShellu se dá načíst jenom jedna verze modulu.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-160">Only one version of the module can be loaded in a PowerShell session.</span></span> <span data-ttu-id="ecf1e-161">Pokud chcete importovat konkrétní verzi rutin AzureRM, musíte otevřít nové okno PowerShellu a použít příkaz `Import-Module`:</span><span class="sxs-lookup"><span data-stu-id="ecf1e-161">You must open a new PowerShell window and use `Import-Module` to import a specific version of the AzureRM cmdlets:</span></span>

```powershell
Import-Module -Name AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> <span data-ttu-id="ecf1e-162">Verze 2.1.0 a verze 1.2.6 jsou první verze modulu navržené tak, aby se daly instalovat vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-162">Version 2.1.0 and version 1.2.6 are the first module versions designed to be installed and used side by side.</span></span> <span data-ttu-id="ecf1e-163">Při načítání starší verze Azure PowerShellu se na načtou nekompatibilní verze modulu **AzureRM.Profile**.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-163">When loading an earlier version of the Azure PowerShell, incompatible versions of the **AzureRM.Profile** module are loaded.</span></span> <span data-ttu-id="ecf1e-164">Výsledkem je to, že rutiny zobrazí výzvu k přihlášení při každém spuštění rutiny.</span><span class="sxs-lookup"><span data-stu-id="ecf1e-164">This results in the cmdlets prompting you to log in whenever you execute a cmdlet.</span></span>

### <a name="other-installation-methods"></a><span data-ttu-id="ecf1e-165">Jiné metody instalace</span><span class="sxs-lookup"><span data-stu-id="ecf1e-165">Other installation methods</span></span>

<span data-ttu-id="ecf1e-166">Informace o instalaci pomocí instalačního programu webové platformy nebo balíčku MSI najdete v popisu [jiných metod instalace](other-install.md).</span><span class="sxs-lookup"><span data-stu-id="ecf1e-166">For information about installing using the Web Platform Installer or the MSI Package, see [Other installation methods](other-install.md)</span></span>
