---
title: "Přehled Azure Stack PowerShellu | Dokumentace Microsoftu"
description: "Přehled instalace a konfigurace Azure Stack PowerShellu."
author: SnehaGunda
manager: Byronr
ms.product: azure-stack
ms.service: powershell
ms.devlang: powershell
ms.topic: reference
ms.author: sngun
ms.manager: byronr
ms.openlocfilehash: f895992b4200f260189b3dbc541452e73a377b00
ms.sourcegitcommit: 8446ae373ac6928871ec8f10d3a4918b4601d5b2
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="azure-stack-powershell"></a><span data-ttu-id="9bfc8-103">Azure Stack PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bfc8-103">Azure Stack PowerShell</span></span>

<span data-ttu-id="9bfc8-104">Azure Stack vyžaduje následující dva moduly PowerShellu:</span><span class="sxs-lookup"><span data-stu-id="9bfc8-104">Azure Stack requires the following two PowerShell modules:</span></span>  

1. <span data-ttu-id="9bfc8-105">Modul **AzureRM** kompatibilní s Azure Stackem, který je k dispozici nainstalováním profilu verze rozhraní API **2017-03-09-profile**.</span><span class="sxs-lookup"><span data-stu-id="9bfc8-105">The Azure Stack compatible **AzureRM** module which is available by installing the **2017-03-09-profile** API Version Profile.</span></span> <span data-ttu-id="9bfc8-106">Rutiny nainstalované pomocí tohoto modulu můžou použít jenom uživatelé a operátoři Azure Stacku.</span><span class="sxs-lookup"><span data-stu-id="9bfc8-106">The cmdlets installed by using this profile can be used by Azure Stack operators and users.</span></span>

2. <span data-ttu-id="9bfc8-107">Nejnovější verzí je instalace **1.2.11** modulu **AzureStack**.</span><span class="sxs-lookup"><span data-stu-id="9bfc8-107">The most current version is the **1.2.11** install of the **AzureStack** module.</span></span> <span data-ttu-id="9bfc8-108">Rutiny nainstalované pomocí tohoto modulu můžou použít jenom operátoři Azure Stacku.</span><span class="sxs-lookup"><span data-stu-id="9bfc8-108">The cmdlets installed by using this module can be used by Azure Stack operators only.</span></span> <span data-ttu-id="9bfc8-109">Operátor může prostřednictvím rutin PowerShellu poskytovaných tímto modulem provádět operace, jako je správa nabídek, plánů, služeb, kvót atd.</span><span class="sxs-lookup"><span data-stu-id="9bfc8-109">Operators can perform operations such as manage offers, plans, services, quotas, etc. by using the PowerShell cmdlets provided by this module.</span></span> <span data-ttu-id="9bfc8-110">Informace o rutinách prostředí PowerShell dostupných v tomto modulu najdete v obsahu referenčních příruček pro [AzureStackAdmin](https://docs.microsoft.com/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) a [AzureStackStorage](https://docs.microsoft.com/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage).</span><span class="sxs-lookup"><span data-stu-id="9bfc8-110">To learn about the PowerShell cmdlets available in this module, see the [AzureStackAdmin](https://docs.microsoft.com/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) and [AzureStackStorage](https://docs.microsoft.com/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage) Reference content.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9bfc8-111">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9bfc8-111">Next Steps</span></span>

* [<span data-ttu-id="9bfc8-112">Instalace PowerShellu pro Azure Stack</span><span class="sxs-lookup"><span data-stu-id="9bfc8-112">Install PowerShell for Azure Stack</span></span>](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [<span data-ttu-id="9bfc8-113">Konfigurace PowerShellu pro použití s Azure Stackem</span><span class="sxs-lookup"><span data-stu-id="9bfc8-113">Configure PowerShell for use with Azure Stack</span></span>](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
