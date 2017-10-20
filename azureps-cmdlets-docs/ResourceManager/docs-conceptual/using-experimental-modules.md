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
# <a name="using-experimental-azure-powershell-modules"></a>Používání experimentálních modulů Azure PowerShellu

Tým Azure PowerShellu s důrazem na vývojářské nástroje (zejména rozhraní příkazového řádku) v Azure experimentuje s řadou vylepšení prostředí Azure PowerShellu.

## <a name="experimentation-methodology"></a>Metodologie experimentování

Pro usnadnění experimentování vytváříme nové moduly Azure PowerShellu, které novým způsobem implementují existující funkce sady Azure SDK tak, aby se snáze používaly. Rutiny ve většině případů přesně odráží existující rutiny. Experimentální rutiny však poskytují zjednodušenou notaci a inteligentnější výchozí hodnoty, které usnadňují vytváření a správu prostředků Azure.

Tyto moduly je možné nainstalovat vedle stávajících modulů Azure PowerShellu. Názvy rutin se zkrátily, aby se zajistily kratší názvy a zamezilo se konfliktům názvů s existujícími rutinami, které nejsou experimentální.

Experimentální moduly se řídí následujícími zásadami vytváření názvů:

- AzureRM.Compute.Experiments
- AzureRM.Websites.Experiments

Tyto zásady vytváření názvů jsou podobné pojmenování modulů ve verzi Preview: `AzureRM.*.Preview`. Moduly ve verzi Preview se liší od experimentálních modulů. Moduly ve verzi Preview implementují nové funkce služeb Azure, které jsou dostupné pouze jako nabídka verze Preview. Moduly ve verzi Preview nahrazují existující moduly Azure PowerShellu a používají stejné názvy rutin a parametrů.

## <a name="how-to-install-an-experimental-module"></a>Instalace experimentálního modulu

Experimentální moduly se publikují v Galerii prostředí PowerShell stejně jako existující moduly Azure PowerShellu. Pokud chcete zobrazit seznam experimentálních modulů, spusťte následující příkaz:

```powershell
Find-Module AzureRM.*.Experiments
```

```Output
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      AzureRM.Websites.Experiments        PSGallery            Create and deploy web applications using Azure Ap...
1.0.25     AzureRM.Compute.Experiments         PSGallery            Azure Compute experiments for VM creation
```

Pokud chcete nainstalovat experimentální modul, použijte následující příkazy z relace PowerShellu se zvýšenými oprávněními:

```powershell
Install-Module AzureRM.Compute.Experiments
Install-Module AzureRM.Websites.Experiments
```

### <a name="documentation-and-support"></a>Dokumentace a podpora

Dokumentace je součástí instalačního balíčku a přístupná pomocí rutiny `Get-Help`. Pro experimentální moduly není publikována žádná oficiální dokumentace.

Doporučujeme vám tyto moduly vyzkoušet. Díky vašemu názoru můžeme vylepšovat použitelnost a reagovat na vaše potřeby. Protože jsou však tyto moduly experimentální, je pro ně omezená podpora. Dotazy nebo hlášení problému můžete odeslat vytvořením [problému](https://github.com/Azure/azure-powershell/issues) v úložišti GitHub.

## <a name="experiments-and-areas-of-improvement"></a>Experimenty a oblasti zlepšování

Tato vylepšení byla vybrána na základě klíčových předností konkurenčních produktů. Například Azure CLI 2.0 si klade za cíl zakládat příkazy na _scénářích_, a ne na _svrchní oblasti rozhraní API_.
Azure CLI 2.0 používá řadu inteligentních výchozích hodnot, které koncovým uživatelům usnadňují scénáře typu Začínáme.

### <a name="core-improvements"></a>Vylepšení jádra

Vylepšení jádra se považují za „zdravý rozum“ a při implementaci těchto aktualizací se nevyžaduje příliš experimentování.

- Rutiny založené na scénářích – Rutiny **All*- by se měly navrhovat s ohledem na scénáře, a ne na službu Azure REST.

- Kratší názvy – Zahrnuje to názvy rutin (například `New-AzureRmVM` => `New-AzVm`) i názvy parametrů (například `-ResourceGroupName` => `-Rg`). Pro zajištění kompatibility se „starými“ rutinami používejte aliasy. Zadávejte _zpětně kompatibilní_ sady parametrů.

- Inteligentní výchozí hodnoty – Vytvářejte inteligentní výchozí hodnoty, které vyplní požadované informace. Například:
  - Skupina prostředků
  - Umístění
  - Závislé prostředky

### <a name="experimental-improvements"></a>Experimentální vylepšení

Experimentální vylepšení představují významnou změnu, kterou by tým měl ověřit prostřednictvím experimentování.

- Jednoduché typy – Ve scénářích vytváření by se měly přestat používat komplexní typy a objekty konfigurace. Zjednodušte konfiguraci na jeden nebo dva parametry.

- Inteligentní vytvoření – Všechny scénáře vytvoření implementující inteligentní vytvoření nebudou mít _žádné_ požadované parametry. Všechny potřebné informace vybere Azure PowerShell dogmatickým způsobem.

- Šedé parametry – V řadě případů budou některé parametry šedé nebo částečně volitelné. Pokud parametr není zadaný, uživateli se zobrazí dotaz, jestli chce parametr nechat vygenerovat. Dává také smysl, aby se hodnota šedých parametrů vyvozovala na základě kontextu se souhlasem uživatele.
  Například může být vhodné, aby šedý parametr navrhoval poslední použitou hodnotu.

- Přepínač `-Auto` – Přepínač `-Auto` uživatelům nabízí volitelnou možnost _nastavit vše na výchozí hodnotu_ při zachování integrity požadovaných parametrů v hlavní cestě.

### <a name="feature-specific-switches"></a>Přepínače specifické pro funkce

Například scénář Vytvoření webové aplikace může zahrnovat přepínač `-Git` nebo `-AddRemote`, který do existujícího úložiště Git automaticky přidá vzdálené úložiště Azure.

- Nastavitelné výchozí hodnoty – Uživatelé by měli mít možnost nastavit výchozí hodnoty určitých všudypřítomných parametrů, jako je `-ResourceGroupName` nebo `-Location`.

- Výchozí velikost – Velikosti prostředků můžou být pro uživatele matoucí, protože řada poskytovatelů prostředků používá různé názvy (například Standard\_DS1\_v2 nebo S1). Většinu uživatelů však více zajímají náklady. Proto je vhodné definovat univerzální velikosti na základě cenového plánu. Uživatelé si můžou zvolit konkrétní velikost nebo nechat Azure PowerShell vybrat _nejlepší možnost_ podle rozpočtu na prostředky.

- Formát výstupu – Azure PowerShell v současné době vrací objekty `PSObject` s velmi omezeným výstupem konzoly. Azure PowerShell může potřebovat zobrazit uživateli určité informace související s použitými inteligentními výchozími hodnotami.

## <a name="try-using-the-experiments"></a>Vyzkoušejte vytváření experimentů

### <a name="install"></a>Instalace

```powershell
Install-Module AzureRM.Compute.Experiments
```

### <a name="create-a-vm"></a>Vytvoření virtuálního počítače

```powershell
$job = New-AzVm -Name MyVm -AsJob
Receive-Job $job
```

### <a name="send-us-feedback"></a>Odeslání vašeho názoru

```powershell
Send-Feedback
```

### <a name="uninstall-the-experimental-modules"></a>Odinstalace experimentálních modulů

```powershell
Uninstall-Module AzureRM.Compute.Experiments
```