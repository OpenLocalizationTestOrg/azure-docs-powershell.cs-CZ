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
# <a name="azure-stack-powershell"></a>Azure Stack PowerShell

Azure Stack vyžaduje následující dva moduly PowerShellu:  

1. Modul **AzureRM** kompatibilní s Azure Stackem, který je k dispozici nainstalováním profilu verze rozhraní API **2017-03-09-profile**. Rutiny nainstalované pomocí tohoto modulu můžou použít jenom uživatelé a operátoři Azure Stacku.

2. Nejnovější verzí je instalace **1.2.11** modulu **AzureStack**. Rutiny nainstalované pomocí tohoto modulu můžou použít jenom operátoři Azure Stacku. Operátor může prostřednictvím rutin PowerShellu poskytovaných tímto modulem provádět operace, jako je správa nabídek, plánů, služeb, kvót atd. Informace o rutinách prostředí PowerShell dostupných v tomto modulu najdete v obsahu referenčních příruček pro [AzureStackAdmin](https://docs.microsoft.com/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) a [AzureStackStorage](https://docs.microsoft.com/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage).

## <a name="next-steps"></a>Další kroky

* [Instalace PowerShellu pro Azure Stack](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [Konfigurace PowerShellu pro použití s Azure Stackem](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
