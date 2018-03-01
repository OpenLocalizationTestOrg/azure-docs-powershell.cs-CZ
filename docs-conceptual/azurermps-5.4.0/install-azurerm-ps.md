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
ms.openlocfilehash: 1a1a2e3d69252c8461284e6ec8e26fa838e773f7
ms.sourcegitcommit: 5fe9a579d2e0d1cb5a05aadaeba5db784f1b18fa
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="install-and-configure-azure-powershell"></a><span data-ttu-id="1e482-103">Instalace a konfigurace Azure Powershellu</span><span class="sxs-lookup"><span data-stu-id="1e482-103">Install and configure Azure PowerShell</span></span>

<span data-ttu-id="1e482-104">Tento článek vysvětluje kroky instalace modulů Azure PowerShell v prostředí Windows.</span><span class="sxs-lookup"><span data-stu-id="1e482-104">This article explains the steps to install the Azure PowerShell modules in a Windows environment.</span></span>  
<span data-ttu-id="1e482-105">Pokud chcete Azure PowerShell použít v systému macOS nebo Linux, přečtěte si tento článek:</span><span class="sxs-lookup"><span data-stu-id="1e482-105">If you want to use Azure PowerShell on macOS or Linux, see the following article:</span></span>  
<span data-ttu-id="1e482-106">[Instalace a konfigurace Azure PowerShellu v systémech macOS a Linux](install-azurermps-maclinux.md).</span><span class="sxs-lookup"><span data-stu-id="1e482-106">[Install and configure Azure PowerShell on macOS and Linux](install-azurermps-maclinux.md).</span></span>

<span data-ttu-id="1e482-107">Preferovanou metodu instalace je instalace Azure PowerShellu z Galerie prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e482-107">Installing Azure PowerShell from the PowerShell Gallery is the preferred method of installation.</span></span>

## <a name="step-1-install-powershellget"></a><span data-ttu-id="1e482-108">Krok 1: Instalace modulu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1e482-108">Step 1: Install PowerShellGet</span></span>

<span data-ttu-id="1e482-109">Instalace položek z Galerie prostředí PowerShell vyžaduje modul PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="1e482-109">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="1e482-110">Ujistěte se, že máte vhodnou verzi modulu PowerShellGet a další požadavky na systém.</span><span class="sxs-lookup"><span data-stu-id="1e482-110">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="1e482-111">Spuštěním následujícího příkazu zjistěte, jestli máte PowerShellGet v systému nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="1e482-111">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module -Name PowerShellGet -ListAvailable | Select-Object -Property Name,Version,Path
```

<span data-ttu-id="1e482-112">Zobrazený výstup by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="1e482-112">You should see something similar to the following output:</span></span>

```Output
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```
<span data-ttu-id="1e482-113">Kromě toho možná budete chtít aktualizovat PowerShellGet pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="1e482-113">In addition you may want to update PowerShellGet with the command below:</span></span>
```powershell
Install-Module PowerShellGet -Force
```

<span data-ttu-id="1e482-114">Pokud nemáte modul PowerShellGet nainstalovaný, přečtěte si v tomto článku část [Jak získat modul PowerShellGet](#how-to-get-powershellget).</span><span class="sxs-lookup"><span data-stu-id="1e482-114">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](#how-to-get-powershellget) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="1e482-115">Použití modulu PowerShellGet vyžaduje zásadu spouštění, která umožňuje spouštět skripty.</span><span class="sxs-lookup"><span data-stu-id="1e482-115">Using PowerShellGet requires an Execution Policy that allows you to run scripts.</span></span> <span data-ttu-id="1e482-116">Další informace o zásadě spouštění Powershellu najdete v tématu popisujícím [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="1e482-116">For more information about PowerShell's Execution Policy, see [About Execution Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="step-2-install-azure-powershell"></a><span data-ttu-id="1e482-117">Krok 2: Instalace Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="1e482-117">Step 2: Install Azure PowerShell</span></span>

<span data-ttu-id="1e482-118">Instalace Azure PowerShellu z Galerie prostředí PowerShell vyžaduje zvýšená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="1e482-118">Installing Azure PowerShell from the PowerShell Gallery requires elevated privileges.</span></span> <span data-ttu-id="1e482-119">Z relace PowerShellu se zvýšenými oprávněními spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1e482-119">Run the following command from an elevated PowerShell session:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module -Name AzureRM -AllowClobber
```

<span data-ttu-id="1e482-120">Ve výchozím nastavení není galerie prostředí PowerShell nakonfigurovaná pro PowerShellGet jako důvěryhodné úložiště.</span><span class="sxs-lookup"><span data-stu-id="1e482-120">By default, the PowerShell gallery is not configured as a Trusted repository for PowerShellGet.</span></span> <span data-ttu-id="1e482-121">Při prvním použití PSGallery se zobrazí tato výzva:</span><span class="sxs-lookup"><span data-stu-id="1e482-121">The first time you use the PSGallery you see the following prompt:</span></span>

```Output
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

<span data-ttu-id="1e482-122">Pokračujte v instalaci výběrem možnosti Ano nebo Ano všem.</span><span class="sxs-lookup"><span data-stu-id="1e482-122">Answer 'Yes' or 'Yes to All' to continue with the installation.</span></span>

> [!NOTE]
> <span data-ttu-id="1e482-123">Pokud máte verzi NuGetu, která je starší než 2.8.5.201, zobrazí se výzva ke stažení a instalaci nejnovější verze NuGetu.</span><span class="sxs-lookup"><span data-stu-id="1e482-123">If you have a version older than 2.8.5.201 of NuGet, you are prompted to download and install the latest version of NuGet.</span></span>

<span data-ttu-id="1e482-124">Modul AzureRM je kumulativní modul pro rutiny Azure Resource Manageru.</span><span class="sxs-lookup"><span data-stu-id="1e482-124">The AzureRM module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="1e482-125">Při instalaci modulu AzureRM se z Galerie prostředí PowerShell stáhnou a nainstalují všechny ostatní moduly Azure, které nebyly nainstalované dřív.</span><span class="sxs-lookup"><span data-stu-id="1e482-125">When you install the AzureRM module, any Azure PowerShell module not previously installed is downloaded and from the PowerShell Gallery.</span></span>

<span data-ttu-id="1e482-126">Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, může se zobrazit chyba.</span><span class="sxs-lookup"><span data-stu-id="1e482-126">If you have a previous version of Azure PowerShell installed you may receive an error.</span></span> <span data-ttu-id="1e482-127">Postup řešení tohoto problému najdete v části [Aktualizace na novou verzi Azure PowerShellu](#update-azps) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="1e482-127">To resolve this issue, see the [Updating to a new version of Azure PowerShell](#update-azps) section of this article.</span></span>

## <a name="step-3-load-the-azurerm-module"></a><span data-ttu-id="1e482-128">Krok 3: Načtení modulu AzureRM</span><span class="sxs-lookup"><span data-stu-id="1e482-128">Step 3: Load the AzureRM module</span></span>
<span data-ttu-id="1e482-129">Jakmile je modul nainstalovaný, je potřeba modul načíst do relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="1e482-129">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="1e482-130">Toto byste měli udělat v normální relaci PowerShellu, a nikoli v relaci se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="1e482-130">You should do this in a normal (non-elevated) PowerShell session.</span></span> <span data-ttu-id="1e482-131">Moduly se načítají pomocí rutiny `Import-Module` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1e482-131">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module -Name AzureRM
```

## <a name="next-steps"></a><span data-ttu-id="1e482-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1e482-132">Next Steps</span></span>

<span data-ttu-id="1e482-133">Další informace o použití Azure PowerShellu najdete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="1e482-133">For more information about using Azure PowerShell, see the following articles:</span></span>

* [<span data-ttu-id="1e482-134">Začínáme s Azure PowerShellem</span><span class="sxs-lookup"><span data-stu-id="1e482-134">Get started with Azure PowerShell</span></span>](get-started-azureps.md)

## <a name="reporting-issues-and-feedback"></a><span data-ttu-id="1e482-135">Hlášení chyb a poskytnutí zpětné vazby</span><span class="sxs-lookup"><span data-stu-id="1e482-135">Reporting issues and feedback</span></span>

<span data-ttu-id="1e482-136">Pokud v nástroji narazíte na jakékoli chyby, přidejte problém v části [Issues](https://github.com/Azure/azure-powershell/issues) (Problémy) našeho úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="1e482-136">If you encounter any bugs with the tool, file an issue in the [Issues](https://github.com/Azure/azure-powershell/issues) section of our GitHub repo.</span></span> <span data-ttu-id="1e482-137">Pokud chcete poskytnout zpětnou vazbu z příkazového řádku, použijte rutinu `Send-Feedback`.</span><span class="sxs-lookup"><span data-stu-id="1e482-137">To provide feedback from the command line, use the `Send-Feedback` cmdlet.</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="1e482-138">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="1e482-138">Frequently asked questions</span></span>

### <a name="how-to-get-powershellget"></a><span data-ttu-id="1e482-139">Jak získat modul PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1e482-139">How to get PowerShellGet</span></span>

|<span data-ttu-id="1e482-140">Scénář</span><span class="sxs-lookup"><span data-stu-id="1e482-140">Scenario</span></span>|<span data-ttu-id="1e482-141">Pokyny pro instalaci</span><span class="sxs-lookup"><span data-stu-id="1e482-141">Install instructions</span></span>|
|---|---|
|<span data-ttu-id="1e482-142">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1e482-142">Windows 10</span></span><br/><span data-ttu-id="1e482-143">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="1e482-143">Windows Server 2016</span></span>|<span data-ttu-id="1e482-144">Integrovaný do Windows Management Frameworku (WMF) 5.0 jako součást operačního systému</span><span class="sxs-lookup"><span data-stu-id="1e482-144">Built into Windows Management Framework (WMF) 5.0 included in the OS</span></span>|
|<span data-ttu-id="1e482-145">Chci upgradovat na PowerShell 5</span><span class="sxs-lookup"><span data-stu-id="1e482-145">I want to upgrade to PowerShell 5</span></span>|<ol><li>[<span data-ttu-id="1e482-146">Instalace nejnovější verze WMF</span><span class="sxs-lookup"><span data-stu-id="1e482-146">Install the latest version of WMF</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)</li><li><span data-ttu-id="1e482-147">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1e482-147">Run the following command:</span></span><br/>```Install-Module PowerShellGet -Force```</li></ol>|
|<span data-ttu-id="1e482-148">Používám verzi Windows s PowerShellem 3 nebo 4</span><span class="sxs-lookup"><span data-stu-id="1e482-148">I am running on a version of Windows with PowerShell 3 or PowerShell 4</span></span>|<ol><span data-ttu-id="1e482-149"><il>[Získání modulů PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217)</il></span><span class="sxs-lookup"><span data-stu-id="1e482-149"><il>[Get the PackageManagement modules](http://go.microsoft.com/fwlink/?LinkID=746217)</il></span></span><li><span data-ttu-id="1e482-150">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1e482-150">Run the following command:</span></span><br/>```Install-Module PowerShellGet -Force```</li></ol>|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a><span data-ttu-id="1e482-151">Kontrola verze Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="1e482-151">Checking the version of Azure PowerShell</span></span>

<span data-ttu-id="1e482-152">I když vám doporučujeme upgradovat na nejnovější verzi co možná nejdříve, podporuje se několik verzí Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="1e482-152">Although we encourage you to upgrade to the latest version as early as possible, several versions of Azure PowerShell are supported.</span></span> <span data-ttu-id="1e482-153">Pokud chcete zjistit nainstalovanou verzi Azure PowerShellu, spusťte z příkazového řádku příkaz `Get-Module AzureRM`.</span><span class="sxs-lookup"><span data-stu-id="1e482-153">To determine the version of Azure PowerShell you have installed, run `Get-Module AzureRM` from your command line.</span></span>

```powershell
Get-Module AzureRM -ListAvailable | Select-Object -Property Name,Version,Path
```

### <a name="support-for-classic-deployment-methods"></a><span data-ttu-id="1e482-154">Podpora metod nasazení Classic</span><span class="sxs-lookup"><span data-stu-id="1e482-154">Support for classic deployment methods</span></span>

<span data-ttu-id="1e482-155">Pokud máte nasazení, která používají model nasazení Classic, můžete nainstalovat verzi správy služeb Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="1e482-155">If you have deployments that use the classic deployment model you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="1e482-156">Další informace najdete v tématu popisujícím [instalaci modulu správy služeb Azure PowerShellu](/powershell/azure/servicemanagement/install-azure-ps).</span><span class="sxs-lookup"><span data-stu-id="1e482-156">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span> <span data-ttu-id="1e482-157">Moduly Azure a AzureRM sdílejí společné závislosti.</span><span class="sxs-lookup"><span data-stu-id="1e482-157">The Azure and AzureRM modules share common dependencies.</span></span> <span data-ttu-id="1e482-158">Pokud používáte moduly Azure i AzureRM, měli byste nainstalovat stejnou verzi obou balíčků.</span><span class="sxs-lookup"><span data-stu-id="1e482-158">If you use both the Azure and AzureRM modules, you should install the same version of each package.</span></span>

### <a id="update-azps"></a><span data-ttu-id="1e482-159">Aktualizace na novou verzi Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="1e482-159">Updating to a new version of Azure PowerShell</span></span>

<span data-ttu-id="1e482-160">Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, která obsahuje modul správy služby, může se zobrazit následující chyba:</span><span class="sxs-lookup"><span data-stu-id="1e482-160">If you have a previous version of Azure PowerShell installed that includes the Service Management module, you may receive the following error:</span></span>

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

<span data-ttu-id="1e482-161">Jak uvádí chybová zpráva, musíte modul nainstalovat pomocí parametru -AllowClobber.</span><span class="sxs-lookup"><span data-stu-id="1e482-161">As the error message states, you need to use the -AllowClobber parameter to install the module.</span></span> <span data-ttu-id="1e482-162">Použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1e482-162">Use the following command:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module -Name AzureRM -AllowClobber
```

<span data-ttu-id="1e482-163">Další informace najdete v tématu nápovědy k rutině [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span><span class="sxs-lookup"><span data-stu-id="1e482-163">For more information, see the help topic for [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span></span>

### <a name="installing-module-versions-side-by-side"></a><span data-ttu-id="1e482-164">Instalace verzí modulu vedle sebe</span><span class="sxs-lookup"><span data-stu-id="1e482-164">Installing module versions side by side</span></span>

<span data-ttu-id="1e482-165">Metoda instalace PowerShellGet je jedinou metodou, která podporuje instalaci více verzí.</span><span class="sxs-lookup"><span data-stu-id="1e482-165">The PowerShellGet method of installation is the only method that supports the installation of multiple versions.</span></span> <span data-ttu-id="1e482-166">Můžete mít například skripty, které jsou napsané v předchozí verzi Azure PowerShellu, a vy nemáte čas nebo prostředky je aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="1e482-166">For example, you may have scripts written using a previous version of Azure PowerShell that you don't have the time or resources to updated.</span></span> <span data-ttu-id="1e482-167">Následující příkazy ukazují, jak nainstalovat víc verzí Azure PowerShellu:</span><span class="sxs-lookup"><span data-stu-id="1e482-167">The following commands illustrate how to install multiple versions of Azure PowerShell:</span></span>

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

<span data-ttu-id="1e482-168">Do relace PowerShellu se dá načíst jenom jedna verze modulu.</span><span class="sxs-lookup"><span data-stu-id="1e482-168">Only one version of the module can be loaded in a PowerShell session.</span></span> <span data-ttu-id="1e482-169">Pokud chcete importovat konkrétní verzi rutin AzureRM, musíte otevřít nové okno PowerShellu a použít příkaz `Import-Module`:</span><span class="sxs-lookup"><span data-stu-id="1e482-169">You must open a new PowerShell window and use `Import-Module` to import a specific version of the AzureRM cmdlets:</span></span>

```powershell
Import-Module -Name AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> <span data-ttu-id="1e482-170">Verze 2.1.0 a verze 1.2.6 jsou první verze modulu navržené tak, aby se daly instalovat vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="1e482-170">Version 2.1.0 and version 1.2.6 are the first module versions designed to be installed and used side by side.</span></span> <span data-ttu-id="1e482-171">Při načítání starší verze Azure PowerShellu se na načtou nekompatibilní verze modulu **AzureRM.Profile**.</span><span class="sxs-lookup"><span data-stu-id="1e482-171">When loading an earlier version of the Azure PowerShell, incompatible versions of the **AzureRM.Profile** module are loaded.</span></span> <span data-ttu-id="1e482-172">Výsledkem je to, že rutiny zobrazí výzvu k přihlášení při každém spuštění rutiny.</span><span class="sxs-lookup"><span data-stu-id="1e482-172">This results in the cmdlets prompting you to log in whenever you execute a cmdlet.</span></span>

### <a name="other-installation-methods"></a><span data-ttu-id="1e482-173">Jiné metody instalace</span><span class="sxs-lookup"><span data-stu-id="1e482-173">Other installation methods</span></span>

<span data-ttu-id="1e482-174">Informace o instalaci pomocí instalačního programu webové platformy nebo balíčku MSI najdete v popisu [jiných metod instalace](other-install.md).</span><span class="sxs-lookup"><span data-stu-id="1e482-174">For information about installing using the Web Platform Installer or the MSI Package, see [Other installation methods](other-install.md)</span></span>
