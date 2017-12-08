---
title: "Používání experimentálních modulů Azure PowerShellu"
description: "Seznamte se s filozofií a využitím experimentálních modulů Azure PowerShellu."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 09/05/2017
ms.openlocfilehash: 7a01957040be7c0498ef4f0e9b8f7297119221a5
ms.sourcegitcommit: 9d2d35944106bdb6758853b050089bc804e6b9d2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2017
---
# <a name="using-experimental-azure-powershell-modules"></a><span data-ttu-id="91e68-103">Používání experimentálních modulů Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="91e68-103">Using experimental Azure PowerShell modules</span></span>

<span data-ttu-id="91e68-104">Tým Azure PowerShellu s důrazem na vývojářské nástroje (zejména rozhraní příkazového řádku) v Azure experimentuje s řadou vylepšení prostředí Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="91e68-104">With the emphasis on developer tools (especially CLIs) in Azure, the Azure PowerShell team is experimenting with many improvements to the Azure PowerShell experience.</span></span>

## <a name="experimentation-methodology"></a><span data-ttu-id="91e68-105">Metodologie experimentování</span><span class="sxs-lookup"><span data-stu-id="91e68-105">Experimentation methodology</span></span>

<span data-ttu-id="91e68-106">Pro usnadnění experimentování vytváříme nové moduly Azure PowerShellu, které novým způsobem implementují existující funkce sady Azure SDK tak, aby se snáze používaly.</span><span class="sxs-lookup"><span data-stu-id="91e68-106">To facilitate experimentation, we are creating new Azure PowerShell modules that implement existing Azure SDK functionality in new, easier to use ways.</span></span> <span data-ttu-id="91e68-107">Rutiny ve většině případů přesně odráží existující rutiny.</span><span class="sxs-lookup"><span data-stu-id="91e68-107">In most cases, the cmdlets exactly mirror existing cmdlets.</span></span> <span data-ttu-id="91e68-108">Experimentální rutiny však poskytují zjednodušenou notaci a inteligentnější výchozí hodnoty, které usnadňují vytváření a správu prostředků Azure.</span><span class="sxs-lookup"><span data-stu-id="91e68-108">However, the experimental cmdlets provide a shorthand notation and smarter default values that make it easier to create and manage Azure resources.</span></span>

<span data-ttu-id="91e68-109">Tyto moduly je možné nainstalovat vedle stávajících modulů Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="91e68-109">These modules can be installed side-by-side with existing Azure PowerShell modules.</span></span> <span data-ttu-id="91e68-110">Názvy rutin se zkrátily, aby se zajistily kratší názvy a zamezilo se konfliktům názvů s existujícími rutinami, které nejsou experimentální.</span><span class="sxs-lookup"><span data-stu-id="91e68-110">The cmdlet names have been shortened to provide shorter names and avoid name conflicts with existing, non-experimental cmdlets.</span></span>

<span data-ttu-id="91e68-111">Experimentální moduly se řídí následujícími zásadami vytváření názvů:</span><span class="sxs-lookup"><span data-stu-id="91e68-111">The experimental modules use the following naming convention:</span></span>

- <span data-ttu-id="91e68-112">AzureRM.Compute.Experiments</span><span class="sxs-lookup"><span data-stu-id="91e68-112">AzureRM.Compute.Experiments</span></span>
- <span data-ttu-id="91e68-113">AzureRM.Websites.Experiments</span><span class="sxs-lookup"><span data-stu-id="91e68-113">AzureRM.Websites.Experiments</span></span>

<span data-ttu-id="91e68-114">Tyto zásady vytváření názvů jsou podobné pojmenování modulů ve verzi Preview: `AzureRM.*.Preview`.</span><span class="sxs-lookup"><span data-stu-id="91e68-114">This naming convention is similar to the naming of Preview modules: `AzureRM.*.Preview`.</span></span> <span data-ttu-id="91e68-115">Moduly ve verzi Preview se liší od experimentálních modulů.</span><span class="sxs-lookup"><span data-stu-id="91e68-115">Preview modules differ from experimental modules.</span></span> <span data-ttu-id="91e68-116">Moduly ve verzi Preview implementují nové funkce služeb Azure, které jsou dostupné pouze jako nabídka verze Preview.</span><span class="sxs-lookup"><span data-stu-id="91e68-116">Preview modules implement new functionality of Azure services that is only available as a Preview offering.</span></span> <span data-ttu-id="91e68-117">Moduly ve verzi Preview nahrazují existující moduly Azure PowerShellu a používají stejné názvy rutin a parametrů.</span><span class="sxs-lookup"><span data-stu-id="91e68-117">Preview modules replace existing Azure PowerShell modules and use the same cmdlet and parameter names.</span></span>

## <a name="how-to-install-an-experimental-module"></a><span data-ttu-id="91e68-118">Instalace experimentálního modulu</span><span class="sxs-lookup"><span data-stu-id="91e68-118">How to install an experimental module</span></span>

<span data-ttu-id="91e68-119">Experimentální moduly se publikují v Galerii prostředí PowerShell stejně jako existující moduly Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="91e68-119">Experimental modules are published to the PowerShell Gallery just like the existing Azure PowerShell modules.</span></span> <span data-ttu-id="91e68-120">Pokud chcete zobrazit seznam experimentálních modulů, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="91e68-120">To see a list of experimental modules, run the following command:</span></span>

```powershell
Find-Module AzureRM.*.Experiments
```

```Output
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      AzureRM.Websites.Experiments        PSGallery            Create and deploy web applications using Azure Ap...
1.0.25     AzureRM.Compute.Experiments         PSGallery            Azure Compute experiments for VM creation
```

<span data-ttu-id="91e68-121">Pokud chcete nainstalovat experimentální modul, použijte následující příkazy z relace PowerShellu se zvýšenými oprávněními:</span><span class="sxs-lookup"><span data-stu-id="91e68-121">To install the experimental module, use the following commands from an elevated PowerShell session:</span></span>

```powershell
Install-Module AzureRM.Compute.Experiments
Install-Module AzureRM.Websites.Experiments
```

### <a name="documentation-and-support"></a><span data-ttu-id="91e68-122">Dokumentace a podpora</span><span class="sxs-lookup"><span data-stu-id="91e68-122">Documentation and support</span></span>

<span data-ttu-id="91e68-123">Dokumentace je součástí instalačního balíčku a přístupná pomocí rutiny `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="91e68-123">Documentation is included in the install package and is accessed using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="91e68-124">Pro experimentální moduly není publikována žádná oficiální dokumentace.</span><span class="sxs-lookup"><span data-stu-id="91e68-124">No official documentation is published for experimental modules.</span></span>

<span data-ttu-id="91e68-125">Doporučujeme vám tyto moduly vyzkoušet.</span><span class="sxs-lookup"><span data-stu-id="91e68-125">We encourage you to test these modules.</span></span> <span data-ttu-id="91e68-126">Díky vašemu názoru můžeme vylepšovat použitelnost a reagovat na vaše potřeby.</span><span class="sxs-lookup"><span data-stu-id="91e68-126">Your feedback allows us to improve usability and respond to your needs.</span></span> <span data-ttu-id="91e68-127">Protože jsou však tyto moduly experimentální, je pro ně omezená podpora.</span><span class="sxs-lookup"><span data-stu-id="91e68-127">However, being experimental, support for these modules is limited.</span></span> <span data-ttu-id="91e68-128">Dotazy nebo hlášení problému můžete odeslat vytvořením [problému](https://github.com/Azure/azure-powershell/issues) v úložišti GitHub.</span><span class="sxs-lookup"><span data-stu-id="91e68-128">Questions or problem reports can be submitted by creating an [issue](https://github.com/Azure/azure-powershell/issues) in the GitHub repository.</span></span>

## <a name="experiments-and-areas-of-improvement"></a><span data-ttu-id="91e68-129">Experimenty a oblasti zlepšování</span><span class="sxs-lookup"><span data-stu-id="91e68-129">Experiments and areas of improvement</span></span>

<span data-ttu-id="91e68-130">Tato vylepšení byla vybrána na základě klíčových předností konkurenčních produktů.</span><span class="sxs-lookup"><span data-stu-id="91e68-130">These improvements were selected based on key differentiators in competing products.</span></span> <span data-ttu-id="91e68-131">Například Azure CLI 2.0 si klade za cíl zakládat příkazy na _scénářích_, a ne na _svrchní oblasti rozhraní API_.</span><span class="sxs-lookup"><span data-stu-id="91e68-131">For example, Azure CLI 2.0 has made a point of basing commands on _scenarios_ rather than _API surface area_.</span></span>
<span data-ttu-id="91e68-132">Azure CLI 2.0 používá řadu inteligentních výchozích hodnot, které koncovým uživatelům usnadňují scénáře typu Začínáme.</span><span class="sxs-lookup"><span data-stu-id="91e68-132">Azure CLI 2.0 use a number of smart defaults that make "getting started" scenarios easier for end users.</span></span>

### <a name="core-improvements"></a><span data-ttu-id="91e68-133">Vylepšení jádra</span><span class="sxs-lookup"><span data-stu-id="91e68-133">Core improvements</span></span>

<span data-ttu-id="91e68-134">Vylepšení jádra se považují za „zdravý rozum“ a při implementaci těchto aktualizací se nevyžaduje příliš experimentování.</span><span class="sxs-lookup"><span data-stu-id="91e68-134">The core improvements are regarded as "common sense", and little experimentation is needed to move forward in implementing these updates.</span></span>

- <span data-ttu-id="91e68-135">Rutiny založené na scénářích – Rutiny **All*- by se měly navrhovat s ohledem na scénáře, a ne na službu Azure REST.</span><span class="sxs-lookup"><span data-stu-id="91e68-135">Scenario-based Cmdlets - **All*- cmdlets should be designed around scenarios, not the Azure REST service.</span></span>

- <span data-ttu-id="91e68-136">Kratší názvy – Zahrnuje to názvy rutin (například `New-AzureRmVM` => `New-AzVm`) i názvy parametrů (například `-ResourceGroupName` => `-Rg`).</span><span class="sxs-lookup"><span data-stu-id="91e68-136">Shorter Names - Includes the names of cmdlets (for example, `New-AzureRmVM` => `New-AzVm`) and the names of parameters (for example, `-ResourceGroupName` => `-Rg`).</span></span> <span data-ttu-id="91e68-137">Pro zajištění kompatibility se „starými“ rutinami používejte aliasy.</span><span class="sxs-lookup"><span data-stu-id="91e68-137">Use aliases for compatibility with "old" cmdlets.</span></span> <span data-ttu-id="91e68-138">Zadávejte _zpětně kompatibilní_ sady parametrů.</span><span class="sxs-lookup"><span data-stu-id="91e68-138">Provide _backwards compatible_ parameter sets.</span></span>

- <span data-ttu-id="91e68-139">Inteligentní výchozí hodnoty – Vytvářejte inteligentní výchozí hodnoty, které vyplní požadované informace.</span><span class="sxs-lookup"><span data-stu-id="91e68-139">Smart Defaults - Create smart defaults to fill in "required" information.</span></span> <span data-ttu-id="91e68-140">Například:</span><span class="sxs-lookup"><span data-stu-id="91e68-140">For example:</span></span>
  - <span data-ttu-id="91e68-141">Skupina prostředků</span><span class="sxs-lookup"><span data-stu-id="91e68-141">Resource Group</span></span>
  - <span data-ttu-id="91e68-142">Umístění</span><span class="sxs-lookup"><span data-stu-id="91e68-142">Location</span></span>
  - <span data-ttu-id="91e68-143">Závislé prostředky</span><span class="sxs-lookup"><span data-stu-id="91e68-143">Dependent resources</span></span>

### <a name="experimental-improvements"></a><span data-ttu-id="91e68-144">Experimentální vylepšení</span><span class="sxs-lookup"><span data-stu-id="91e68-144">Experimental improvements</span></span>

<span data-ttu-id="91e68-145">Experimentální vylepšení představují významnou změnu, kterou by tým měl ověřit prostřednictvím experimentování.</span><span class="sxs-lookup"><span data-stu-id="91e68-145">The experimental improvements present a significant change that the team wants to validate via experimentation.</span></span>

- <span data-ttu-id="91e68-146">Jednoduché typy – Ve scénářích vytváření by se měly přestat používat komplexní typy a objekty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="91e68-146">Simple types - Create scenarios should move away from complex types and config objects.</span></span> <span data-ttu-id="91e68-147">Zjednodušte konfiguraci na jeden nebo dva parametry.</span><span class="sxs-lookup"><span data-stu-id="91e68-147">Simplify the configuration down to one or two parameters.</span></span>

- <span data-ttu-id="91e68-148">Inteligentní vytvoření – Všechny scénáře vytvoření implementující inteligentní vytvoření nebudou mít _žádné_ požadované parametry. Všechny potřebné informace vybere Azure PowerShell dogmatickým způsobem.</span><span class="sxs-lookup"><span data-stu-id="91e68-148">"Smart Create" - All create scenarios implementing "Smart Create" would have _no_ required parameters: all necessary information would be chosen by Azure PowerShell in an opinionated fashion.</span></span>

- <span data-ttu-id="91e68-149">Šedé parametry – V řadě případů budou některé parametry šedé nebo částečně volitelné.</span><span class="sxs-lookup"><span data-stu-id="91e68-149">Gray Parameters - In many cases, some parameters could be "gray" or semi-optional.</span></span> <span data-ttu-id="91e68-150">Pokud parametr není zadaný, uživateli se zobrazí dotaz, jestli chce parametr nechat vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="91e68-150">If the parameter is not specified, the user is asked if they want the parameter generated for them.</span></span> <span data-ttu-id="91e68-151">Dává také smysl, aby se hodnota šedých parametrů vyvozovala na základě kontextu se souhlasem uživatele.</span><span class="sxs-lookup"><span data-stu-id="91e68-151">It also makes sense for gray parameters to infer a value based on context with the user's consent.</span></span>
  <span data-ttu-id="91e68-152">Například může být vhodné, aby šedý parametr navrhoval poslední použitou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="91e68-152">For example, it may make sense to have the gray parameter suggest the most recently used value.</span></span>

- <span data-ttu-id="91e68-153">Přepínač `-Auto` – Přepínač `-Auto` uživatelům nabízí volitelnou možnost _nastavit vše na výchozí hodnotu_ při zachování integrity požadovaných parametrů v hlavní cestě.</span><span class="sxs-lookup"><span data-stu-id="91e68-153">`-Auto` Switch - The `-Auto` switch would provide an "opt-in" way for users to _default all the things_ while maintaining the integrity of required parameters in the mainline path.</span></span>

### <a name="feature-specific-switches"></a><span data-ttu-id="91e68-154">Přepínače specifické pro funkce</span><span class="sxs-lookup"><span data-stu-id="91e68-154">Feature-specific switches</span></span>

<span data-ttu-id="91e68-155">Například scénář Vytvoření webové aplikace může zahrnovat přepínač `-Git` nebo `-AddRemote`, který do existujícího úložiště Git automaticky přidá vzdálené úložiště Azure.</span><span class="sxs-lookup"><span data-stu-id="91e68-155">For example, the "Create web app" scenario might have a `-Git` or `-AddRemote` switch that would automatically add an "azure" remote to an existing git repository.</span></span>

- <span data-ttu-id="91e68-156">Nastavitelné výchozí hodnoty – Uživatelé by měli mít možnost nastavit výchozí hodnoty určitých všudypřítomných parametrů, jako je `-ResourceGroupName` nebo `-Location`.</span><span class="sxs-lookup"><span data-stu-id="91e68-156">Settable Defaults - Users should have the ability to default certain ubiquitous parameters like `-ResourceGroupName` and `-Location`.</span></span>

- <span data-ttu-id="91e68-157">Výchozí velikost – Velikosti prostředků můžou být pro uživatele matoucí, protože řada poskytovatelů prostředků používá různé názvy (například Standard\_DS1\_v2 nebo S1).</span><span class="sxs-lookup"><span data-stu-id="91e68-157">Size Defaults - Resource "sizes" can be confusing to users since many Resource Providers use different names (for example, "Standard\_DS1\_v2" or "S1").</span></span> <span data-ttu-id="91e68-158">Většinu uživatelů však více zajímají náklady.</span><span class="sxs-lookup"><span data-stu-id="91e68-158">However, most users care more about cost.</span></span> <span data-ttu-id="91e68-159">Proto je vhodné definovat univerzální velikosti na základě cenového plánu.</span><span class="sxs-lookup"><span data-stu-id="91e68-159">Therefore, it makes sense to define "universal" sizes based on a pricing schedule.</span></span> <span data-ttu-id="91e68-160">Uživatelé si můžou zvolit konkrétní velikost nebo nechat Azure PowerShell vybrat _nejlepší možnost_ podle rozpočtu na prostředky.</span><span class="sxs-lookup"><span data-stu-id="91e68-160">Users can choose a specific size or let Azure PowerShell choose the _best option_ based on the resource the budget.</span></span>

- <span data-ttu-id="91e68-161">Formát výstupu – Azure PowerShell v současné době vrací objekty `PSObject` s velmi omezeným výstupem konzoly.</span><span class="sxs-lookup"><span data-stu-id="91e68-161">Output Format - Azure PowerShell currently returns `PSObject`s and there is little console output.</span></span> <span data-ttu-id="91e68-162">Azure PowerShell může potřebovat zobrazit uživateli určité informace související s použitými inteligentními výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="91e68-162">Azure PowerShell may need to display some information to the user regarding the "smart defaults" used.</span></span>

## <a name="try-using-the-experiments"></a><span data-ttu-id="91e68-163">Vyzkoušejte vytváření experimentů</span><span class="sxs-lookup"><span data-stu-id="91e68-163">Try using the experiments</span></span>

### <a name="install"></a><span data-ttu-id="91e68-164">Instalace</span><span class="sxs-lookup"><span data-stu-id="91e68-164">Install</span></span>

```powershell
Install-Module AzureRM.Compute.Experiments
```

### <a name="create-a-vm"></a><span data-ttu-id="91e68-165">Vytvoření virtuálního počítače</span><span class="sxs-lookup"><span data-stu-id="91e68-165">Create a VM</span></span>

```powershell
$job = New-AzVm -Name MyVm -AsJob
Receive-Job $job
```

### <a name="send-us-feedback"></a><span data-ttu-id="91e68-166">Odeslání vašeho názoru</span><span class="sxs-lookup"><span data-stu-id="91e68-166">Send us feedback</span></span>

```powershell
Send-Feedback
```

### <a name="uninstall-the-experimental-modules"></a><span data-ttu-id="91e68-167">Odinstalace experimentálních modulů</span><span class="sxs-lookup"><span data-stu-id="91e68-167">Uninstall the experimental modules</span></span>

```powershell
Uninstall-Module AzureRM.Compute.Experiments
```