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
ms.date: 08/31/2017
ms.openlocfilehash: 0e560332c87fdcc8b7365f2271de24481003a4d6
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2017
---
# <a name="install-and-configure-azure-powershell"></a><span data-ttu-id="85e86-103">Instalace a konfigurace Azure Powershellu</span><span class="sxs-lookup"><span data-stu-id="85e86-103">Install and configure Azure PowerShell</span></span>

<span data-ttu-id="85e86-104">Tento článek vysvětluje kroky instalace modulů Azure PowerShell v prostředí Windows.</span><span class="sxs-lookup"><span data-stu-id="85e86-104">This article explains the steps to install the Azure PowerShell modules in a Windows environment.</span></span>
<span data-ttu-id="85e86-105">Pokud chcete používat Azure PowerShell v systému macOS nebo Linux, přečtěte si článek o [instalaci a konfiguraci Azure PowerShellu v systému macOS a Linux](install-azurermps-maclinux.md).</span><span class="sxs-lookup"><span data-stu-id="85e86-105">If you want to use Azure PowerShell on macOS or Linux, see the following article: [Install and configure Azure PowerShell on macOS and Linux](install-azurermps-maclinux.md).</span></span>

<span data-ttu-id="85e86-106">Preferovanou metodu instalace je instalace Azure PowerShellu z Galerie prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="85e86-106">Installing Azure PowerShell from the PowerShell Gallery is the preferred method of installation.</span></span>

## <a name="step-1-install-powershellget"></a><span data-ttu-id="85e86-107">Krok 1: Instalace modulu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="85e86-107">Step 1: Install PowerShellGet</span></span>

<span data-ttu-id="85e86-108">Instalace položek z Galerie prostředí PowerShell vyžaduje modul PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="85e86-108">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="85e86-109">Ujistěte se, že máte vhodnou verzi modulu PowerShellGet a další požadavky na systém.</span><span class="sxs-lookup"><span data-stu-id="85e86-109">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="85e86-110">Spuštěním následujícího příkazu zjistěte, jestli máte PowerShellGet v systému nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="85e86-110">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="85e86-111">Zobrazený výstup by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="85e86-111">You should see something similar to the following output:</span></span>

```Output
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="85e86-112">Pokud nemáte modul PowerShellGet nainstalovaný, přečtěte si v tomto článku část [Jak získat modul PowerShellGet](#how-to-get-powershellget).</span><span class="sxs-lookup"><span data-stu-id="85e86-112">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](#how-to-get-powershellget) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="85e86-113">Použití modulu PowerShellGet vyžaduje zásadu spouštění, která umožňuje spouštět skripty.</span><span class="sxs-lookup"><span data-stu-id="85e86-113">Using PowerShellGet requires an Execution Policy that allows you to run scripts.</span></span> <span data-ttu-id="85e86-114">Další informace o zásadě spouštění Powershellu najdete v tématu popisujícím [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="85e86-114">For more information about PowerShell's Execution Policy, see [About Execution Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="step-2-install-azure-powershell"></a><span data-ttu-id="85e86-115">Krok 2: Instalace Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="85e86-115">Step 2: Install Azure PowerShell</span></span>

<span data-ttu-id="85e86-116">Instalace Azure PowerShellu z Galerie prostředí PowerShell vyžaduje zvýšená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="85e86-116">Installing Azure PowerShell from the PowerShell Gallery requires elevated privileges.</span></span> <span data-ttu-id="85e86-117">Z relace PowerShellu se zvýšenými oprávněními spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="85e86-117">Run the following command from an elevated PowerShell session:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM -AllowClobber
```

<span data-ttu-id="85e86-118">Ve výchozím nastavení není galerie prostředí PowerShell nakonfigurovaná pro PowerShellGet jako důvěryhodné úložiště.</span><span class="sxs-lookup"><span data-stu-id="85e86-118">By default, the PowerShell gallery is not configured as a Trusted repository for PowerShellGet.</span></span> <span data-ttu-id="85e86-119">Při prvním použití PSGallery se zobrazí tato výzva:</span><span class="sxs-lookup"><span data-stu-id="85e86-119">The first time you use the PSGallery you see the following prompt:</span></span>

```Output
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

<span data-ttu-id="85e86-120">Pokračujte v instalaci výběrem možnosti Ano nebo Ano všem.</span><span class="sxs-lookup"><span data-stu-id="85e86-120">Answer 'Yes' or 'Yes to All' to continue with the installation.</span></span>

> [!NOTE]
> <span data-ttu-id="85e86-121">Pokud máte verzi NuGetu, která je starší než 2.8.5.201, zobrazí se výzva ke stažení a instalaci nejnovější verze NuGetu.</span><span class="sxs-lookup"><span data-stu-id="85e86-121">If you have a version older than 2.8.5.201 of NuGet, you are prompted to download and install the latest version of NuGet.</span></span>

<span data-ttu-id="85e86-122">Modul AzureRM je kumulativní modul pro rutiny Azure Resource Manageru.</span><span class="sxs-lookup"><span data-stu-id="85e86-122">The AzureRM module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="85e86-123">Při instalaci modulu AzureRM se z Galerie prostředí PowerShell stáhnou a nainstalují všechny ostatní moduly Azure, které nebyly nainstalované dřív.</span><span class="sxs-lookup"><span data-stu-id="85e86-123">When you install the AzureRM module, any Azure PowerShell module not previously installed is downloaded and from the PowerShell Gallery.</span></span>

<span data-ttu-id="85e86-124">Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, může se zobrazit chyba.</span><span class="sxs-lookup"><span data-stu-id="85e86-124">If you have a previous version of Azure PowerShell installed you may receive an error.</span></span> <span data-ttu-id="85e86-125">Postup řešení tohoto problému najdete v části [Aktualizace na novou verzi Azure PowerShellu](#update-azps) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="85e86-125">To resolve this issue, see the [Updating to a new version of Azure PowerShell](#update-azps) section of this article.</span></span>

## <a name="step-3-load-the-azurerm-module"></a><span data-ttu-id="85e86-126">Krok 3: Načtení modulu AzureRM</span><span class="sxs-lookup"><span data-stu-id="85e86-126">Step 3: Load the AzureRM module</span></span>
<span data-ttu-id="85e86-127">Jakmile je modul nainstalovaný, je potřeba modul načíst do relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="85e86-127">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="85e86-128">Toto byste měli udělat v normální relaci PowerShellu, a nikoli v relaci se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="85e86-128">You should do this in a normal (non-elevated) PowerShell session.</span></span> <span data-ttu-id="85e86-129">Moduly se načítají pomocí rutiny `Import-Module` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85e86-129">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM
```

## <a name="next-steps"></a><span data-ttu-id="85e86-130">Další kroky</span><span class="sxs-lookup"><span data-stu-id="85e86-130">Next Steps</span></span>

<span data-ttu-id="85e86-131">Další informace o použití Azure PowerShellu najdete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="85e86-131">For more information about using Azure PowerShell, see the following articles:</span></span>

* [<span data-ttu-id="85e86-132">Začínáme s Azure PowerShellem</span><span class="sxs-lookup"><span data-stu-id="85e86-132">Get started with Azure PowerShell</span></span>](get-started-azureps.md)

## <a name="reporting-issues-and-feedback"></a><span data-ttu-id="85e86-133">Hlášení chyb a poskytnutí zpětné vazby</span><span class="sxs-lookup"><span data-stu-id="85e86-133">Reporting issues and feedback</span></span>

<span data-ttu-id="85e86-134">Pokud v nástroji narazíte na jakékoli chyby, přidejte problém v části [Issues](https://github.com/Azure/azure-powershell/issues) (Problémy) našeho úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="85e86-134">If you encounter any bugs with the tool, file an issue in the [Issues](https://github.com/Azure/azure-powershell/issues) section of our GitHub repo.</span></span> <span data-ttu-id="85e86-135">Pokud chcete poskytnout zpětnou vazbu z příkazového řádku, použijte rutinu `Send-Feedback`.</span><span class="sxs-lookup"><span data-stu-id="85e86-135">To provide feedback from the command line, use the `Send-Feedback` cmdlet.</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="85e86-136">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="85e86-136">Frequently asked questions</span></span>

### <a name="how-to-get-powershellget"></a><span data-ttu-id="85e86-137">Jak získat modul PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="85e86-137">How to get PowerShellGet</span></span>

|<span data-ttu-id="85e86-138">Verze operačního systému</span><span class="sxs-lookup"><span data-stu-id="85e86-138">OS Version</span></span>|<span data-ttu-id="85e86-139">Pokyny pro instalaci</span><span class="sxs-lookup"><span data-stu-id="85e86-139">Install instructions</span></span>|
|---|---|
|<span data-ttu-id="85e86-140">Mám Windows 10 nebo Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="85e86-140">I have Windows 10 or Windows Server 2016</span></span>|<span data-ttu-id="85e86-141">Integrovaný do Windows Management Frameworku (WMF) 5.0 jako součást operačního systému</span><span class="sxs-lookup"><span data-stu-id="85e86-141">Built into Windows Management Framework (WMF) 5.0 included in the OS</span></span>|
|<span data-ttu-id="85e86-142">Chci upgradovat na PowerShell 5</span><span class="sxs-lookup"><span data-stu-id="85e86-142">I want to upgrade to PowerShell 5</span></span>|[<span data-ttu-id="85e86-143">Instalace nejnovější verze WMF</span><span class="sxs-lookup"><span data-stu-id="85e86-143">Install the latest version of WMF</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|<span data-ttu-id="85e86-144">Používám verzi Windows s PowerShellem 3 nebo 4</span><span class="sxs-lookup"><span data-stu-id="85e86-144">I am running on a version of Windows with PowerShell 3 or PowerShell 4</span></span>|[<span data-ttu-id="85e86-145">Získání modulů PackageManagement</span><span class="sxs-lookup"><span data-stu-id="85e86-145">Get the PackageManagement modules</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a><span data-ttu-id="85e86-146">Kontrola verze Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="85e86-146">Checking the version of Azure PowerShell</span></span>

<span data-ttu-id="85e86-147">I když vám doporučujeme upgradovat na nejnovější verzi co možná nejdříve, podporuje se několik verzí Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="85e86-147">Although we encourage you to upgrade to the latest version as early as possible, several versions of Azure PowerShell are supported.</span></span> <span data-ttu-id="85e86-148">Pokud chcete zjistit nainstalovanou verzi Azure PowerShellu, spusťte z příkazového řádku příkaz `Get-Module AzureRM`.</span><span class="sxs-lookup"><span data-stu-id="85e86-148">To determine the version of Azure PowerShell you have installed, run `Get-Module AzureRM` from your command line.</span></span>

```powershell
Get-Module AzureRM -list | Select-Object Name,Version,Path
```

### <a name="support-for-classic-deployment-methods"></a><span data-ttu-id="85e86-149">Podpora metod nasazení Classic</span><span class="sxs-lookup"><span data-stu-id="85e86-149">Support for classic deployment methods</span></span>

<span data-ttu-id="85e86-150">Pokud máte nasazení, která používají model nasazení Classic, můžete nainstalovat verzi správy služeb Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="85e86-150">If you have deployments that use the classic deployment model you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="85e86-151">Další informace najdete v tématu popisujícím [instalaci modulu správy služeb Azure PowerShellu](/powershell/azure/servicemanagement/install-azure-ps).</span><span class="sxs-lookup"><span data-stu-id="85e86-151">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span> <span data-ttu-id="85e86-152">Moduly Azure a AzureRM sdílejí společné závislosti.</span><span class="sxs-lookup"><span data-stu-id="85e86-152">The Azure and AzureRM modules share common dependencies.</span></span> <span data-ttu-id="85e86-153">Pokud používáte moduly Azure i AzureRM, měli byste nainstalovat stejnou verzi obou balíčků.</span><span class="sxs-lookup"><span data-stu-id="85e86-153">If you use both the Azure and AzureRM modules, you should install the same version of each package.</span></span>

### <a id="update-azps"></a><span data-ttu-id="85e86-154">Aktualizace na novou verzi Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="85e86-154">Updating to a new version of Azure PowerShell</span></span>

<span data-ttu-id="85e86-155">Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, která obsahuje modul správy služby, může se zobrazit následující chyba:</span><span class="sxs-lookup"><span data-stu-id="85e86-155">If you have a previous version of Azure PowerShell installed that includes the Service Management module, you may receive the following error:</span></span>

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

<span data-ttu-id="85e86-156">Jak uvádí chybová zpráva, musíte modul nainstalovat pomocí parametru -AllowClobber.</span><span class="sxs-lookup"><span data-stu-id="85e86-156">As the error message states, you need to use the -AllowClobber parameter to install the module.</span></span> <span data-ttu-id="85e86-157">Použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="85e86-157">Use the following command:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM -AllowClobber
```

<span data-ttu-id="85e86-158">Další informace najdete v tématu nápovědy k rutině [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span><span class="sxs-lookup"><span data-stu-id="85e86-158">For more information, see the help topic for [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span></span>

### <a name="installing-module-versions-side-by-side"></a><span data-ttu-id="85e86-159">Instalace verzí modulu vedle sebe</span><span class="sxs-lookup"><span data-stu-id="85e86-159">Installing module versions side by side</span></span>

<span data-ttu-id="85e86-160">Metoda instalace PowerShellGet je jedinou metodou, která podporuje instalaci více verzí.</span><span class="sxs-lookup"><span data-stu-id="85e86-160">The PowerShellGet method of installation is the only method that supports the installation of multiple versions.</span></span> <span data-ttu-id="85e86-161">Můžete mít například skripty, které jsou napsané v předchozí verzi Azure PowerShellu, a vy nemáte čas nebo prostředky je aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="85e86-161">For example, you may have scripts written using a previous version of Azure PowerShell that you don't have the time or resources to updated.</span></span> <span data-ttu-id="85e86-162">Následující příkazy ukazují, jak nainstalovat víc verzí Azure PowerShellu:</span><span class="sxs-lookup"><span data-stu-id="85e86-162">The following commands illustrate how to install multiple versions of Azure PowerShell:</span></span>

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

<span data-ttu-id="85e86-163">Do relace PowerShellu se dá načíst jenom jedna verze modulu.</span><span class="sxs-lookup"><span data-stu-id="85e86-163">Only one version of the module can be loaded in a PowerShell session.</span></span> <span data-ttu-id="85e86-164">Pokud chcete importovat konkrétní verzi rutin AzureRM, musíte otevřít nové okno PowerShellu a použít příkaz `Import-Module`:</span><span class="sxs-lookup"><span data-stu-id="85e86-164">You must open a new PowerShell window and use `Import-Module` to import a specific version of the AzureRM cmdlets:</span></span>

```powershell
Import-Module AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> <span data-ttu-id="85e86-165">Verze 2.1.0 a verze 1.2.6 jsou první verze modulu navržené tak, aby se daly instalovat vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="85e86-165">Version 2.1.0 and version 1.2.6 are the first module versions designed to be installed and used side by side.</span></span> <span data-ttu-id="85e86-166">Při načítání starší verze Azure PowerShellu se na načtou nekompatibilní verze modulu **AzureRM.Profile**.</span><span class="sxs-lookup"><span data-stu-id="85e86-166">When loading an earlier version of the Azure PowerShell, incompatible versions of the **AzureRM.Profile** module are loaded.</span></span> <span data-ttu-id="85e86-167">Výsledkem je to, že rutiny zobrazí výzvu k přihlášení při každém spuštění rutiny.</span><span class="sxs-lookup"><span data-stu-id="85e86-167">This results in the cmdlets prompting you to log in whenever you execute a cmdlet.</span></span>

### <a name="other-installation-methods"></a><span data-ttu-id="85e86-168">Jiné metody instalace</span><span class="sxs-lookup"><span data-stu-id="85e86-168">Other installation methods</span></span>

<span data-ttu-id="85e86-169">Informace o instalaci pomocí instalačního programu webové platformy nebo balíčku MSI najdete v popisu [jiných metod instalace](other-install.md).</span><span class="sxs-lookup"><span data-stu-id="85e86-169">For information about installing using the Web Platform Installer or the MSI Package, see [Other installation methods](other-install.md)</span></span>
