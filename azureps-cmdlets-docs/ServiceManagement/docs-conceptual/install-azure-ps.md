---
title: "<span data-ttu-id=\"80781-101\">Instalace a konfigurace modulu správy služeb prostředí Azure PowerShell | Dokumentace Microsoftu</span><span class=\"sxs-lookup\"><span data-stu-id=\"80781-101\">Install and configure the Azure PowerShell Service Management module | Microsoft Docs</span></span>"
description: <span data-ttu-id="80781-102">Jak nainstalovat a nakonfigurovat Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="80781-102">How to install and configure Azure PowerShell for first time use.</span></span>
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/06/2017
ms.openlocfilehash: c51c727c1cb022eca59f819c7f24d8e058c677da
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="80781-103">Instalace modulu správy služeb prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="80781-103">Installing the Azure PowerShell Service Management module</span></span>
<a id="installing-the-azure-powershell-service-management-module" class="xliff"></a>

<span data-ttu-id="80781-104">Preferovanou metodu instalace je instalace Azure PowerShellu z [Galerie prostředí PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="80781-104">Installing Azure PowerShell from the [PowerShell Gallery](https://www.powershellgallery.com/) is the preferred method of installation.</span></span>

## <span data-ttu-id="80781-105">Krok 1: Instalace modulu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="80781-105">Step 1: Install PowerShellGet</span></span>
<a id="step-1-install-powershellget" class="xliff"></a>

<span data-ttu-id="80781-106">Instalace položek z Galerie prostředí PowerShell vyžaduje modul PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="80781-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="80781-107">Ujistěte se, že máte vhodnou verzi modulu PowerShellGet a další požadavky na systém.</span><span class="sxs-lookup"><span data-stu-id="80781-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="80781-108">Spuštěním následujícího příkazu zjistěte, jestli máte PowerShellGet v systému nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="80781-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="80781-109">Zobrazený výstup by měl vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="80781-109">You should see something similar to the following output:</span></span>

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="80781-110">Pokud nemáte modul PowerShellGet nainstalovaný, přečtěte část [Jak získat modul PowerShellGet](install-azurerm-ps.md#how-to-get-powershellget).</span><span class="sxs-lookup"><span data-stu-id="80781-110">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](install-azurerm-ps.md#how-to-get-powershellget).</span></span>

## <span data-ttu-id="80781-111">Krok 2: Instalace Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="80781-111">Step 2: Install Azure PowerShell</span></span>
<a id="step-2-install-azure-powershell" class="xliff"></a>

<span data-ttu-id="80781-112">Z konzoly prostředí Windows PowerShell spusťte následující příkaz jako správce:</span><span class="sxs-lookup"><span data-stu-id="80781-112">Run the following command from the Windows PowerShell console running as Administrator:</span></span>

```powershell
Install-Module Azure
```

<span data-ttu-id="80781-113">Modul Azure je kumulativní modul pro rutiny Azure Resource Manageru.</span><span class="sxs-lookup"><span data-stu-id="80781-113">The Azure module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="80781-114">Při instalaci modulu AzureRM se z Galerie prostředí PowerShell stáhnou a nainstalují všechny ostatní moduly Azure, které nebyly nainstalované dřív.</span><span class="sxs-lookup"><span data-stu-id="80781-114">When you install the AzureRM module, any other Azure modules that have not previously been installed will be downloaded and installed from the PowerShell Gallery.</span></span>

<span data-ttu-id="80781-115">Modul správy služeb Azure sdílí závislosti s moduly Resource Manageru prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80781-115">The Azure Service Management module shares dependencies with the Azure PowerShell Resource Manager modules.</span></span> <span data-ttu-id="80781-116">Pokud jste nainstalovali moduly Resource Manageru prostředí Azure PowerShell, budete muset přidat do instalačního příkazu parametr `-AllowClobber`.</span><span class="sxs-lookup"><span data-stu-id="80781-116">If you have installed the Azure PowerShell Resource Manager modules, you will need to add the `-AllowClobber` parameter to the install command.</span></span> <span data-ttu-id="80781-117">Díky tomu lze aktualizovat existující sdílené závislosti.</span><span class="sxs-lookup"><span data-stu-id="80781-117">This allows this existing shared dependencies to be updated.</span></span> <span data-ttu-id="80781-118">Bez tohoto parametru se instalace modulu nezdaří.</span><span class="sxs-lookup"><span data-stu-id="80781-118">Without this parameter, installation of the module fails.</span></span>

```powershell
Install-Module Azure -AllowClobber
```

<span data-ttu-id="80781-119">Když nainstalujete tento modul, můžete importovat modul spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="80781-119">After you install this module, you can import the module by running the following command:</span></span>

```powershell
Import-Module Azure
```

## <span data-ttu-id="80781-120">Používání rutin</span><span class="sxs-lookup"><span data-stu-id="80781-120">To use the cmdlets</span></span>
<a id="to-use-the-cmdlets" class="xliff"></a>

<span data-ttu-id="80781-121">Pokud chcete začít pracovat s rutinami pro správu služeb Azure, nejprve se přihlaste k účtu Azure.</span><span class="sxs-lookup"><span data-stu-id="80781-121">To start working with the Azure Service Management cmdlets, first log on to your Azure account.</span></span> <span data-ttu-id="80781-122">Chcete-li se přihlásit k účtu, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="80781-122">To log on to your account, run the following command:</span></span>

```powershell
Add-AzureAccount
```

<span data-ttu-id="80781-123">Po přihlášení k Azure prostředí Azure PowerShell vytvoří kontext pro danou relaci.</span><span class="sxs-lookup"><span data-stu-id="80781-123">After logging into Azure, Azure PowerShell creates a context for the given session.</span></span> <span data-ttu-id="80781-124">Tento kontext obsahuje prostředí Azure PowerShell, účet, tenanta a předplatné, které se použije pro všechny rutiny v rámci této relace.</span><span class="sxs-lookup"><span data-stu-id="80781-124">That context contains the Azure PowerShell environment, account, tenant, and subscription that will be used for all cmdlets within that session.</span></span> <span data-ttu-id="80781-125">Nyní jste připraveni používat následující moduly.</span><span class="sxs-lookup"><span data-stu-id="80781-125">Now you are ready to use the modules below.</span></span>

## <span data-ttu-id="80781-126">Rutiny správy služeb Azure</span><span class="sxs-lookup"><span data-stu-id="80781-126">Azure Service Management cmdlets</span></span>
<a id="azure-service-management-cmdlets" class="xliff"></a>

<span data-ttu-id="80781-127">Moduly prostředí Azure PowerShell se často aktualizují.</span><span class="sxs-lookup"><span data-stu-id="80781-127">Azure PowerShell modules are updated frequently.</span></span> <span data-ttu-id="80781-128">Pokud si všimnete, že online nápověda k rutinám uvádí rutiny nebo parametry, které modul neobsahuje, stáhněte a nainstalujte nejnovější verzi modulu.</span><span class="sxs-lookup"><span data-stu-id="80781-128">If you notice that the online cmdlet help includes cmdlets or parameters that are not in your module, download and install the latest version of the module.</span></span> <span data-ttu-id="80781-129">Chcete-li zjistit verzi modulu, zadejte: `(Get-Module Azure).Version`.</span><span class="sxs-lookup"><span data-stu-id="80781-129">To find the version of your module, type: `(Get-Module Azure).Version`.</span></span>

<span data-ttu-id="80781-130">Ukázkové skripty, které vám pomůžou automatizovat některé běžné úlohy v Azure, najdete v [centru skriptů Windows Azure](http://www.windowsazure.com/documentation/scripts/).</span><span class="sxs-lookup"><span data-stu-id="80781-130">For sample scripts that can help you automate some of the common tasks in Azure, see the [Windows Azure Script Center](http://www.windowsazure.com/documentation/scripts/).</span></span>

<span data-ttu-id="80781-131">Obecné informace o instalaci prostředí Windows PowerShell, seznamování s ním, jeho používání a přizpůsobování najdete v článku [Skriptování v prostředí Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210).</span><span class="sxs-lookup"><span data-stu-id="80781-131">For general information about installing, learning, using, and customizing Windows PowerShell, see [Scripting with Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210).</span></span>
