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
# <a name="azure-stack-powershell"></a>Azure Stack PowerShell 

Azure Stack vyžaduje následující dva moduly PowerShellu:  

1. Modul **AzureRM** kompatibilní s Azure Stackem, který je k dispozici nainstalováním profilu verze rozhraní API **2017-03-09-profile**. Rutiny nainstalované pomocí tohoto profilu můžou použít tenanti a správci cloudu Azure Stack. Další informace o rutinách PowerShellu, které jsou k dispozici v tomto profilu, najdete v obsahu referenční příručky PowerShellu pro [verzi 1.2.9 modulu AzureRM](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9).  

2. Verze **1.2.9** modulu **AzureStack**. Rutiny nainstalované pomocí tohoto modulu můžou použít jenom správci cloudu Azure Stack. Správce může prostřednictvím rutin PowerShellu poskytovaných tímto modulem provádět operace, jako je správa nabídek, plánů, služeb, kvót atd. Informace o rutinách prostředí PowerShell dostupných v tomto modulu najdete v obsahu referenčních příruček pro [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) a [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage).

## <a name="next-steps"></a>Další kroky

* [Instalace PowerShellu pro Azure Stack](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [Konfigurace PowerShellu pro použití s Azure Stackem](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)


