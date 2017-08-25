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
ms.openlocfilehash: 2a03697e0f3e80d63c48f2dc5615f6c99b9ef716
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <a name="azure-stack-powershell"></a><span data-ttu-id="9cca4-103">Azure Stack PowerShell</span><span class="sxs-lookup"><span data-stu-id="9cca4-103">Azure Stack PowerShell</span></span> 

<span data-ttu-id="9cca4-104">Azure Stack vyžaduje následující dva moduly PowerShellu:</span><span class="sxs-lookup"><span data-stu-id="9cca4-104">Azure Stack requires the following two PowerShell modules:</span></span>  

1. <span data-ttu-id="9cca4-105">Modul **AzureRM** kompatibilní s Azure Stackem, který je k dispozici nainstalováním profilu verze rozhraní API **2017-03-09-profile**.</span><span class="sxs-lookup"><span data-stu-id="9cca4-105">The Azure Stack compatible **AzureRM** module which is available by installing the **2017-03-09-profile** API Version Profile.</span></span> <span data-ttu-id="9cca4-106">Rutiny nainstalované pomocí tohoto profilu můžou použít tenanti a správci cloudu Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="9cca4-106">The cmdlets installed by using this profile can be used by the Azure Stack cloud administrators and the tenants.</span></span> <span data-ttu-id="9cca4-107">Další informace o rutinách PowerShellu, které jsou k dispozici v tomto profilu, najdete v obsahu referenční příručky PowerShellu pro [verzi 1.2.9 modulu AzureRM](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9).</span><span class="sxs-lookup"><span data-stu-id="9cca4-107">To learn about the PowerShell cmdlets that are available in this profile, see the PowerShell reference content for the [1.2.9 version of AzureRM](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9) module.</span></span>  

2. <span data-ttu-id="9cca4-108">Verze **1.2.9** modulu **AzureStack**.</span><span class="sxs-lookup"><span data-stu-id="9cca4-108">The **1.2.9** version of the **AzureStack** module.</span></span> <span data-ttu-id="9cca4-109">Rutiny nainstalované pomocí tohoto modulu můžou použít jenom správci cloudu Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="9cca4-109">The cmdlets installed by using this module can be used by Azure Stack cloud administrators only.</span></span> <span data-ttu-id="9cca4-110">Správce může prostřednictvím rutin PowerShellu poskytovaných tímto modulem provádět operace, jako je správa nabídek, plánů, služeb, kvót atd.</span><span class="sxs-lookup"><span data-stu-id="9cca4-110">Administrator can perform operations such as manage offers, plans, services, quotas, etc. by using the PowerShell cmdlets provided by this module.</span></span> <span data-ttu-id="9cca4-111">Informace o rutinách prostředí PowerShell dostupných v tomto modulu najdete v obsahu referenčních příruček pro [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) a [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage).</span><span class="sxs-lookup"><span data-stu-id="9cca4-111">To learn about the PowerShell cmdlets available in this module, see the [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) and [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage) Reference content.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9cca4-112">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9cca4-112">Next Steps</span></span>

* [<span data-ttu-id="9cca4-113">Instalace PowerShellu pro Azure Stack</span><span class="sxs-lookup"><span data-stu-id="9cca4-113">Install PowerShell for Azure Stack</span></span>](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [<span data-ttu-id="9cca4-114">Konfigurace PowerShellu pro použití s Azure Stackem</span><span class="sxs-lookup"><span data-stu-id="9cca4-114">Configure PowerShell for use with Azure Stack</span></span>](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)


