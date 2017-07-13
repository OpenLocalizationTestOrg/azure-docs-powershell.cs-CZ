---
title: <span data-ttu-id="bd28f-101">Instalace a konfigurace Azure Powershellu | Dokumentace Microsoftu</span><span class="sxs-lookup"><span data-stu-id="bd28f-101">Install and configure Azure PowerShell | Microsoft Docs</span></span>
description: <span data-ttu-id="bd28f-102">Jak nainstalovat a nakonfigurovat Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd28f-102">How to install and configure Azure PowerShell for first time use.</span></span>
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
# <span data-ttu-id="bd28f-103">Instalace a konfigurace Azure Powershellu</span><span class="sxs-lookup"><span data-stu-id="bd28f-103">Install and configure Azure PowerShell</span></span>
<a id="install-and-configure-azure-powershell" class="xliff"></a>

<span data-ttu-id="bd28f-104">Preferovanou metodu instalace je instalace Azure PowerShellu z Galerie prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd28f-104">Installing Azure PowerShell from the PowerShell Gallery is the preferred method of installation.</span></span>

## <span data-ttu-id="bd28f-105">Krok 1: Instalace modulu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bd28f-105">Step 1: Install PowerShellGet</span></span>
<a id="step-1-install-powershellget" class="xliff"></a>

<span data-ttu-id="bd28f-106">Instalace položek z Galerie prostředí PowerShell vyžaduje modul PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="bd28f-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="bd28f-107">Ujistěte se, že máte vhodnou verzi modulu PowerShellGet a další požadavky na systém.</span><span class="sxs-lookup"><span data-stu-id="bd28f-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="bd28f-108">Spuštěním následujícího příkazu zjistěte, jestli máte PowerShellGet v systému nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="bd28f-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="bd28f-109">Zobrazený výstup by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="bd28f-109">You should see something similar to the following output:</span></span>

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="bd28f-110">Pokud nemáte modul PowerShellGet nainstalovaný, přečtěte si v tomto článku část [Jak získat modul PowerShellGet](#how-to-get-powershellget).</span><span class="sxs-lookup"><span data-stu-id="bd28f-110">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](#how-to-get-powershellget) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="bd28f-111">Použití modulu PowerShellGet vyžaduje zásadu spouštění, která umožňuje spouštět skripty.</span><span class="sxs-lookup"><span data-stu-id="bd28f-111">Using PowerShellGet requires an Execution Policy that allows you to run scripts.</span></span> <span data-ttu-id="bd28f-112">Další informace o zásadě spouštění Powershellu najdete v tématu popisujícím [zásady spouštění](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="bd28f-112">For more information about PowerShell's Execution Policy, see [About Execution Policies](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <span data-ttu-id="bd28f-113">Krok 2: Instalace Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="bd28f-113">Step 2: Install Azure PowerShell</span></span>
<a id="step-2-install-azure-powershell" class="xliff"></a>

<span data-ttu-id="bd28f-114">Instalace Azure PowerShellu z Galerie prostředí PowerShell vyžaduje zvýšená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="bd28f-114">Installing Azure PowerShell from the PowerShell Gallery requires elevated privileges.</span></span> <span data-ttu-id="bd28f-115">Z relace PowerShellu se zvýšenými oprávněními spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="bd28f-115">Run the following command from an elevated PowerShell session:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM
```

<span data-ttu-id="bd28f-116">Ve výchozím nastavení není galerie prostředí PowerShell nakonfigurovaná pro PowerShellGet jako důvěryhodné úložiště.</span><span class="sxs-lookup"><span data-stu-id="bd28f-116">By default, the PowerShell gallery is not configured as a Trusted repository for PowerShellGet.</span></span> <span data-ttu-id="bd28f-117">Při prvním použití PSGallery se zobrazí tato výzva:</span><span class="sxs-lookup"><span data-stu-id="bd28f-117">The first time you use the PSGallery you see the following prompt:</span></span>

```
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

<span data-ttu-id="bd28f-118">Pokračujte v instalaci výběrem možnosti Ano nebo Ano všem.</span><span class="sxs-lookup"><span data-stu-id="bd28f-118">Answer 'Yes' or 'Yes to All' to continue with the installation.</span></span>

> [!NOTE]
> <span data-ttu-id="bd28f-119">Pokud máte verzi NuGetu, která je starší než 2.8.5.201, zobrazí se výzva ke stažení a instalaci nejnovější verze NuGetu.</span><span class="sxs-lookup"><span data-stu-id="bd28f-119">If you have a version older than 2.8.5.201 of NuGet, you are prompted to download and install the latest version of NuGet.</span></span>

<span data-ttu-id="bd28f-120">Modul AzureRM je kumulativní modul pro rutiny Azure Resource Manageru.</span><span class="sxs-lookup"><span data-stu-id="bd28f-120">The AzureRM module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="bd28f-121">Při instalaci modulu AzureRM se z Galerie prostředí PowerShell stáhnou a nainstalují všechny ostatní moduly Azure, které nebyly nainstalované dřív.</span><span class="sxs-lookup"><span data-stu-id="bd28f-121">When you install the AzureRM module, any Azure PowerShell module not previously installed is downloaded and from the PowerShell Gallery.</span></span>

<span data-ttu-id="bd28f-122">Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, může se zobrazit chyba.</span><span class="sxs-lookup"><span data-stu-id="bd28f-122">If you have a previous version of Azure PowerShell installed you may receive an error.</span></span> <span data-ttu-id="bd28f-123">Postup řešení tohoto problému najdete v části [Aktualizace na novou verzi Azure PowerShellu](#update-azps) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="bd28f-123">To resolve this issue, see the [Updating to a new version of Azure PowerShell](#update-azps) section of this article.</span></span>

## <span data-ttu-id="bd28f-124">Krok 3: Načtení modulu AzureRM</span><span class="sxs-lookup"><span data-stu-id="bd28f-124">Step 3: Load the AzureRM module</span></span>
<a id="step-3-load-the-azurerm-module" class="xliff"></a>
<span data-ttu-id="bd28f-125">Jakmile je modul nainstalovaný, je potřeba modul načíst do relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="bd28f-125">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="bd28f-126">Toto byste měli udělat v normální relaci PowerShellu, a nikoli v relaci se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="bd28f-126">You should do this in a normal (non-elevated) PowerShell session.</span></span> <span data-ttu-id="bd28f-127">Moduly se načítají pomocí rutiny `Import-Module` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bd28f-127">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM
```

## <span data-ttu-id="bd28f-128">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bd28f-128">Next Steps</span></span>
<a id="next-steps" class="xliff"></a>

<span data-ttu-id="bd28f-129">Další informace o použití Azure PowerShellu najdete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="bd28f-129">For more information about using Azure PowerShell, see the following articles:</span></span>

* [<span data-ttu-id="bd28f-130">Začínáme s Azure PowerShellem</span><span class="sxs-lookup"><span data-stu-id="bd28f-130">Get started with Azure PowerShell</span></span>](get-started-azureps.md)

## <span data-ttu-id="bd28f-131">Hlášení chyb a poskytnutí zpětné vazby</span><span class="sxs-lookup"><span data-stu-id="bd28f-131">Reporting issues and feedback</span></span>
<a id="reporting-issues-and-feedback" class="xliff"></a>

<span data-ttu-id="bd28f-132">Pokud v nástroji narazíte na jakékoli chyby, přidejte problém v části [Issues](https://github.com/Azure/azure-powershell/issues) (Problémy) našeho úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="bd28f-132">If you encounter any bugs with the tool, file an issue in the [Issues](https://github.com/Azure/azure-powershell/issues) section of our GitHub repo.</span></span> <span data-ttu-id="bd28f-133">Pokud chcete poskytnout zpětnou vazbu z příkazového řádku, použijte rutinu `Send-Feedback`.</span><span class="sxs-lookup"><span data-stu-id="bd28f-133">To provide feedback from the command line, use the `Send-Feedback` cmdlet.</span></span>

## <span data-ttu-id="bd28f-134">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="bd28f-134">Frequently asked questions</span></span>
<a id="frequently-asked-questions" class="xliff"></a>

### <span data-ttu-id="bd28f-135">Jak získat modul PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bd28f-135">How to get PowerShellGet</span></span>
<a id="how-to-get-powershellget" class="xliff"></a>

|<span data-ttu-id="bd28f-136">Verze operačního systému</span><span class="sxs-lookup"><span data-stu-id="bd28f-136">OS Version</span></span>|<span data-ttu-id="bd28f-137">Pokyny pro instalaci</span><span class="sxs-lookup"><span data-stu-id="bd28f-137">Install instructions</span></span>|
|---|---|
|<span data-ttu-id="bd28f-138">Mám Windows 10 nebo Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="bd28f-138">I have Windows 10 or Windows Server 2016</span></span>|<span data-ttu-id="bd28f-139">Integrovaný do Windows Management Frameworku (WMF) 5.0 jako součást operačního systému</span><span class="sxs-lookup"><span data-stu-id="bd28f-139">Built into Windows Management Framework (WMF) 5.0 included in the OS</span></span>|
|<span data-ttu-id="bd28f-140">Chci upgradovat na PowerShell 5</span><span class="sxs-lookup"><span data-stu-id="bd28f-140">I want to upgrade to PowerShell 5</span></span>|[<span data-ttu-id="bd28f-141">Instalace nejnovější verze WMF</span><span class="sxs-lookup"><span data-stu-id="bd28f-141">Install the latest version of WMF</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|<span data-ttu-id="bd28f-142">Používám verzi Windows s PowerShellem 3 nebo 4</span><span class="sxs-lookup"><span data-stu-id="bd28f-142">I am running on a version of Windows with PowerShell 3 or PowerShell 4</span></span>|[<span data-ttu-id="bd28f-143">Získání modulů PackageManagement</span><span class="sxs-lookup"><span data-stu-id="bd28f-143">Get the PackageManagement modules</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <span data-ttu-id="bd28f-144">Kontrola verze Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="bd28f-144">Checking the version of Azure PowerShell</span></span>
<a id="checking-the-version-of-azure-powershell" class="xliff"></a>

<span data-ttu-id="bd28f-145">I když vám doporučujeme upgradovat na nejnovější verzi co možná nejdříve, podporuje se několik verzí Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="bd28f-145">Although we encourage you to upgrade to the latest version as early as possible, several versions of Azure PowerShell are support.</span></span> <span data-ttu-id="bd28f-146">Pokud chcete zjistit nainstalovanou verzi Azure PowerShellu, spusťte z příkazového řádku příkaz `Get-Module AzureRM`.</span><span class="sxs-lookup"><span data-stu-id="bd28f-146">To determine the version of Azure PowerShell you have installed, run `Get-Module AzureRM` from your command line.</span></span>

```powershell
Get-Module AzureRM -list | Select-Object Name,Version,Path
```

### <span data-ttu-id="bd28f-147">Podpora metod nasazení Classic</span><span class="sxs-lookup"><span data-stu-id="bd28f-147">Support for classic deployment methods</span></span>
<a id="support-for-classic-deployment-methods" class="xliff"></a>

<span data-ttu-id="bd28f-148">Pokud máte nasazení, která používají model nasazení Classic, můžete nainstalovat verzi správy služeb Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="bd28f-148">If you have deployments that use the classic deployment model you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="bd28f-149">Další informace najdete v tématu popisujícím [instalaci modulu správy služeb Azure PowerShellu](/powershell/azure/servicemanagement/install-azure-ps).</span><span class="sxs-lookup"><span data-stu-id="bd28f-149">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span> <span data-ttu-id="bd28f-150">Moduly Azure a AzureRM sdílejí společné závislosti.</span><span class="sxs-lookup"><span data-stu-id="bd28f-150">The Azure and AzureRM modules share common dependencies.</span></span> <span data-ttu-id="bd28f-151">Pokud používáte moduly Azure i AzureRM, měli byste nainstalovat stejnou verzi obou balíčků.</span><span class="sxs-lookup"><span data-stu-id="bd28f-151">If you use both the Azure and AzureRM modules, you should install the same version of each package.</span></span>

### <span data-ttu-id="bd28f-152"><a id="update-azps"></a>Aktualizace na novou verzi Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="bd28f-152"><a id="update-azps"></a>Updating to a new version of Azure PowerShell</span></span>

<span data-ttu-id="bd28f-153">Pokud máte nainstalovanou předchozí verzi Azure PowerShellu, která obsahuje modul správy služby, může se zobrazit následující chyba:</span><span class="sxs-lookup"><span data-stu-id="bd28f-153">If you have a previous version of Azure PowerShell installed that includes the Service Management module, you may receive the following error:</span></span>

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

<span data-ttu-id="bd28f-154">Jak uvádí chybová zpráva, musíte modul nainstalovat pomocí parametru -AllowClobber.</span><span class="sxs-lookup"><span data-stu-id="bd28f-154">As the error message states, you need to use the -AllowClobber parameter to install the module.</span></span> <span data-ttu-id="bd28f-155">Použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="bd28f-155">Use the following command:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM -AllowClobber
```

<span data-ttu-id="bd28f-156">Další informace najdete v tématu nápovědy k rutině [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span><span class="sxs-lookup"><span data-stu-id="bd28f-156">For more information, see the help topic for [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span></span>

### <span data-ttu-id="bd28f-157">Instalace verzí modulu vedle sebe</span><span class="sxs-lookup"><span data-stu-id="bd28f-157">Installing module versions side by side</span></span>
<a id="installing-module-versions-side-by-side" class="xliff"></a>

<span data-ttu-id="bd28f-158">Metoda instalace PowerShellGet je jedinou metodou, která podporuje instalaci více verzí.</span><span class="sxs-lookup"><span data-stu-id="bd28f-158">The PowerShellGet method of installation is the only method that supports the installation of multiple versions.</span></span> <span data-ttu-id="bd28f-159">Můžete mít například skripty, které jsou napsané v předchozí verzi Azure PowerShellu, a vy nemáte čas nebo prostředky je aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="bd28f-159">For example, you may have scripts written using a previous version of Azure PowerShell that you don't have the time or resources to updated.</span></span> <span data-ttu-id="bd28f-160">Následující příkazy ukazují, jak nainstalovat víc verzí Azure PowerShellu:</span><span class="sxs-lookup"><span data-stu-id="bd28f-160">The following commands illustrate how to install multiple versions of Azure PowerShell:</span></span>

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

<span data-ttu-id="bd28f-161">Do relace PowerShellu se dá načíst jenom jedna verze modulu.</span><span class="sxs-lookup"><span data-stu-id="bd28f-161">Only one version of the module can be loaded in a PowerShell session.</span></span> <span data-ttu-id="bd28f-162">Pokud chcete importovat konkrétní verzi rutin AzureRM, musíte otevřít nové okno PowerShellu a použít příkaz `Import-Module`:</span><span class="sxs-lookup"><span data-stu-id="bd28f-162">You must open a new PowerShell window and use `Import-Module` to import a specific version of the AzureRM cmdlets:</span></span>

```powershell
Import-Module AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> <span data-ttu-id="bd28f-163">Verze 2.1.0 a verze 1.2.6 jsou první verze modulu navržené tak, aby se daly instalovat vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="bd28f-163">Version 2.1.0 and version 1.2.6 are the first module versions designed to be installed and used side by side.</span></span> <span data-ttu-id="bd28f-164">Při načítání starší verze Azure PowerShellu se na načtou nekompatibilní verze modulu **AzureRM.Profile**.</span><span class="sxs-lookup"><span data-stu-id="bd28f-164">When loading an earlier version of the Azure PowerShell, incompatible versions of the **AzureRM.Profile** module are loaded.</span></span> <span data-ttu-id="bd28f-165">Výsledkem je to, že rutiny zobrazí výzvu k přihlášení při každém spuštění rutiny.</span><span class="sxs-lookup"><span data-stu-id="bd28f-165">This results in the cmdlets prompting you to log in whenever you execute a cmdlet.</span></span>

### <span data-ttu-id="bd28f-166">Jiné metody instalace</span><span class="sxs-lookup"><span data-stu-id="bd28f-166">Other installation methods</span></span>
<a id="other-installation-methods" class="xliff"></a>

<span data-ttu-id="bd28f-167">Informace o instalaci pomocí instalačního programu webové platformy nebo balíčku MSI najdete v popisu [jiných metod instalace](other-install.md).</span><span class="sxs-lookup"><span data-stu-id="bd28f-167">For information about installing using the Web Platform Installer or the MSI Package, see [Other installation methods](other-install.md)</span></span>
