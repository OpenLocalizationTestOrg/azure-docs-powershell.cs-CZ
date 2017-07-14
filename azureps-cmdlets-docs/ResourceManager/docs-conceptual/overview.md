---
title: "Přehled prostředí Azure PowerShell | Dokumentace Microsoftu"
description: "Přehled prostředí Azure PowerShell s odkazy na instalaci a konfiguraci."
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.manager: carmonm
ms.date: 05/15/2017
ms.openlocfilehash: dbcc818ecc06d3206b8ccd6f8743c670c86cead0
ms.sourcegitcommit: 5f2c794bfa44ec4ffacdd73f548288874210a498
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2017
---
# <span data-ttu-id="6cea1-103">Přehled prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="6cea1-103">Overview of Azure PowerShell</span></span>
<a id="overview-of-azure-powershell" class="xliff"></a>

<span data-ttu-id="6cea1-104">Prostředí Azure PowerShell poskytuje sadu rutin, které ke správě vašich prostředků Azure využívají model [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="6cea1-104">Azure PowerShell provides a set of cmdlets that use the [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) model for managing your Azure resources.</span></span>

<span data-ttu-id="6cea1-105">Po přečtení článku týkajícím se [instalace](install-azurerm-ps.md) budete moci prostředí Azure PowerShell zprovoznit ve svém systému.</span><span class="sxs-lookup"><span data-stu-id="6cea1-105">Review the [Install](install-azurerm-ps.md) article to get Azure PowerShell up and running on your system.</span></span> <span data-ttu-id="6cea1-106">Pak si přečtěte článek [Začínáme](get-started-azureps.md), abyste mohli začít s používáním.</span><span class="sxs-lookup"><span data-stu-id="6cea1-106">Then read the [Get Started](get-started-azureps.md) article to begin using it.</span></span> <span data-ttu-id="6cea1-107">Informace o nejnovější verzi najdete v tématu [Poznámky k verzi](release-notes-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-107">For information about the latest release, see the [release notes](release-notes-azureps.md).</span></span>

<span data-ttu-id="6cea1-108">Následující ukázky vám můžou pomoct při provádění běžných postupů s použitím prostředí Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6cea1-108">The following samples can help you learn how to perform common scenarios with Azure PowerShell:</span></span>

* [<span data-ttu-id="6cea1-109">Virtuální počítače s Linuxem</span><span class="sxs-lookup"><span data-stu-id="6cea1-109">Linux Virtual Machines</span></span>](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="6cea1-110">Virtuální počítače s Windows</span><span class="sxs-lookup"><span data-stu-id="6cea1-110">Windows Virtual Machines</span></span>](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="6cea1-111">Web Apps</span><span class="sxs-lookup"><span data-stu-id="6cea1-111">Web Apps</span></span>](/azure/app-service-web/app-service-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="6cea1-112">Databáze SQL</span><span class="sxs-lookup"><span data-stu-id="6cea1-112">SQL Databases</span></span>](/azure/sql-database/sql-database-powershell-samples?toc=/powershell/azure/toc.json)


> [!NOTE]<span data-ttu-id="6cea1-113"> > Pokud máte nasazení používající model nasazení Classic, který nejde převést, můžete nainstalovat verzi správy služeb Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="6cea1-113"> > If you have deployments that use the classic deployment model that cannot be converted, you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="6cea1-114">Další informace najdete v tématu popisujícím [instalaci modulu správy služeb Azure PowerShellu](/powershell/azure/servicemanagement/install-azure-ps).</span><span class="sxs-lookup"><span data-stu-id="6cea1-114">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span>


### <span data-ttu-id="6cea1-115">Potřebujete s prostředím PowerShell pomoct?</span><span class="sxs-lookup"><span data-stu-id="6cea1-115">Need help with PowerShell?</span></span>
<a id="need-help-with-powershell" class="xliff"></a>

<span data-ttu-id="6cea1-116">Pokud s prostředím PowerShell nejste seznámeni, může vám pomoct úvod do prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6cea1-116">If you are unfamiliar with PowerShell, you may find an introduction to PowerShell helpful.</span></span> <span data-ttu-id="6cea1-117">Pokud chcete s prostředím PowerShell začít, najdete informace v tématu [Skriptování v prostředí PowerShell](https://technet.microsoft.com/library/bb978526.aspx).</span><span class="sxs-lookup"><span data-stu-id="6cea1-117">To get started with PowerShell, see [Scripting with PowerShell](https://technet.microsoft.com/library/bb978526.aspx).</span></span>

<span data-ttu-id="6cea1-118">Můžete se podívat i na toto video: [Základy prostředí PowerShell, 1. část: Začínáme s prostředím PowerShell](https://channel9.msdn.com/Blogs/Taste-of-Premier/PowerShellBasicsPart1).</span><span class="sxs-lookup"><span data-stu-id="6cea1-118">You can also watch this video: [PowerShell Basics: (Part 1) Getting Started with PowerShell](https://channel9.msdn.com/Blogs/Taste-of-Premier/PowerShellBasicsPart1).</span></span>

## <span data-ttu-id="6cea1-119">Další moduly prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="6cea1-119">Other Azure PowerShell modules</span></span>
<a id="other-azure-powershell-modules" class="xliff"></a>

* [<span data-ttu-id="6cea1-120">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="6cea1-120">Azure Active Directory</span></span>](/powershell/azure/active-directory/)
* [<span data-ttu-id="6cea1-121">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="6cea1-121">Azure Information Protection</span></span>](/powershell/azure/aip/)
* [<span data-ttu-id="6cea1-122">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="6cea1-122">Azure Service Fabric</span></span>](/powershell/azure/oservice-fabric/)
* [<span data-ttu-id="6cea1-123">Azure ElasticDB</span><span class="sxs-lookup"><span data-stu-id="6cea1-123">Azure ElasticDB</span></span>](/powershell/azure/elasticdbjobs/)
