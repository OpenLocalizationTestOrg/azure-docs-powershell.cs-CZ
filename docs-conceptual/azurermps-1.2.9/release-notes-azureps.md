---
title: "Protokol změn Azure PowerShellu | Dokumentace Microsoftu"
description: "Toto je historie změn provedených v nejnovější vydané verzi Azure PowerShellu."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.service: azure-powershell
ms.product: azure
ms.devlang: powershell
ms.topic: conceptual
ms.workload: 
ms.date: 05/18/2017
ms.openlocfilehash: 5fe7591855577e083aad5923aed37b18d0b2a40c
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <a name="release-notes"></a>Poznámky k verzi

Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.

## <a name="version-129"></a>Verze 1.2.9

Změny v této verzi

* Modul AzureRm.AzureStackAdmin
    + V rutině Add-AzureRmResourceProviderRegistration jsme provedli změny pro podporu oddělení Azure Resource Manageru pro správce a tenanta. Přidali jsme nový parametr -ResourceManagerType.
    + Odebrali jsme parametry -AdminUri, -ApiVersion, -SubscriptionId a -Token z jednotlivých rutin. Na zastarávání těchto parametrů jsme upozorňovali a teď jsme je odebrali.
* Modul AzureStackStorage
    + Přidání nových rutin pro podporu scénářů migrace kontejnerů
    + Odebrání rutin odkazujících na interní komponenty a odpovídající funkce
* AzureRM.BootStrapper
    + Vytvoření nového modulu pro správu verzí rutin Azure PowerShellu prostřednictvím profilů verzí