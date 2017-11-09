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
ms.openlocfilehash: 49980b361c580a1a00f07c2002241e71f2c0b654
ms.sourcegitcommit: df44d5d9874b55455ec745f1846e06a4b3266d13
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2017
---
# <a name="azure-stack-powershell"></a><span data-ttu-id="ea195-103">Azure Stack PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea195-103">Azure Stack PowerShell</span></span>

<span data-ttu-id="ea195-104">Azure Stack vyžaduje následující dva moduly PowerShellu:</span><span class="sxs-lookup"><span data-stu-id="ea195-104">Azure Stack requires the following two PowerShell modules:</span></span>  

1. <span data-ttu-id="ea195-105">Modul **AzureRM** kompatibilní s Azure Stackem, který je k dispozici nainstalováním profilu verze rozhraní API **2017-03-09-profile**.</span><span class="sxs-lookup"><span data-stu-id="ea195-105">The Azure Stack compatible **AzureRM** module which is available by installing the **2017-03-09-profile** API Version Profile.</span></span> <span data-ttu-id="ea195-106">Rutiny nainstalované pomocí tohoto modulu můžou použít jenom uživatelé a operátoři Azure Stacku.</span><span class="sxs-lookup"><span data-stu-id="ea195-106">The cmdlets installed by using this profile can be used by Azure Stack operators and users.</span></span>

2. <span data-ttu-id="ea195-107">Nejnovější verzí je instalace **1.2.11** modulu **AzureStack**.</span><span class="sxs-lookup"><span data-stu-id="ea195-107">The most current version is the **1.2.11** install of the **AzureStack** module.</span></span> <span data-ttu-id="ea195-108">Rutiny nainstalované pomocí tohoto modulu můžou použít jenom operátoři Azure Stacku.</span><span class="sxs-lookup"><span data-stu-id="ea195-108">The cmdlets installed by using this module can be used by Azure Stack operators only.</span></span> <span data-ttu-id="ea195-109">Operátor může prostřednictvím rutin PowerShellu poskytovaných tímto modulem provádět operace, jako je správa nabídek, plánů, služeb, kvót atd.</span><span class="sxs-lookup"><span data-stu-id="ea195-109">Operators can perform operations such as manage offers, plans, services, quotas, etc. by using the PowerShell cmdlets provided by this module.</span></span> <span data-ttu-id="ea195-110">Informace o rutinách prostředí PowerShell dostupných v tomto modulu najdete v obsahu referenčních příruček pro [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) a [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage).</span><span class="sxs-lookup"><span data-stu-id="ea195-110">To learn about the PowerShell cmdlets available in this module, see the [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) and [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage) Reference content.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea195-111">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ea195-111">Next Steps</span></span>

* [<span data-ttu-id="ea195-112">Instalace PowerShellu pro Azure Stack</span><span class="sxs-lookup"><span data-stu-id="ea195-112">Install PowerShell for Azure Stack</span></span>](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [<span data-ttu-id="ea195-113">Konfigurace PowerShellu pro použití s Azure Stackem</span><span class="sxs-lookup"><span data-stu-id="ea195-113">Configure PowerShell for use with Azure Stack</span></span>](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
