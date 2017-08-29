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
# <a name="release-notes"></a><span data-ttu-id="d0c1a-103">Poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="d0c1a-103">Release notes</span></span>

<span data-ttu-id="d0c1a-104">Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="d0c1a-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <a name="version-129"></a><span data-ttu-id="d0c1a-105">Verze 1.2.9</span><span class="sxs-lookup"><span data-stu-id="d0c1a-105">Version 1.2.9</span></span>

<span data-ttu-id="d0c1a-106">Změny v této verzi</span><span class="sxs-lookup"><span data-stu-id="d0c1a-106">Changes This Release</span></span>

* <span data-ttu-id="d0c1a-107">Modul AzureRm.AzureStackAdmin</span><span class="sxs-lookup"><span data-stu-id="d0c1a-107">AzureRm.AzureStackAdmin Module</span></span>
    + <span data-ttu-id="d0c1a-108">V rutině Add-AzureRmResourceProviderRegistration jsme provedli změny pro podporu oddělení Azure Resource Manageru pro správce a tenanta.</span><span class="sxs-lookup"><span data-stu-id="d0c1a-108">Changes in the Add-AzureRmResourceProviderRegistration cmdlet for the support of Admin Azure resource manager and tenant azure resource manager split.</span></span> <span data-ttu-id="d0c1a-109">Přidali jsme nový parametr -ResourceManagerType.</span><span class="sxs-lookup"><span data-stu-id="d0c1a-109">A new parameter -ResourceManagerType has been added.</span></span>
    + <span data-ttu-id="d0c1a-110">Odebrali jsme parametry -AdminUri, -ApiVersion, -SubscriptionId a -Token z jednotlivých rutin.</span><span class="sxs-lookup"><span data-stu-id="d0c1a-110">Removal of the parameters -AdminUri, -ApiVersion, -SubscriptionId and -Token from each cmdlets.</span></span> <span data-ttu-id="d0c1a-111">Na zastarávání těchto parametrů jsme upozorňovali a teď jsme je odebrali.</span><span class="sxs-lookup"><span data-stu-id="d0c1a-111">We have been printing warnings that these parameters will be deprecated and now they got removed.</span></span>
* <span data-ttu-id="d0c1a-112">Modul AzureStackStorage</span><span class="sxs-lookup"><span data-stu-id="d0c1a-112">AzureStackStorage module</span></span>
    + <span data-ttu-id="d0c1a-113">Přidání nových rutin pro podporu scénářů migrace kontejnerů</span><span class="sxs-lookup"><span data-stu-id="d0c1a-113">Added new cmdlets to support container migration scenarios.</span></span>
    + <span data-ttu-id="d0c1a-114">Odebrání rutin odkazujících na interní komponenty a odpovídající funkce</span><span class="sxs-lookup"><span data-stu-id="d0c1a-114">Removed cmdlets referring to internal components and underlying features.</span></span>
* <span data-ttu-id="d0c1a-115">AzureRM.BootStrapper</span><span class="sxs-lookup"><span data-stu-id="d0c1a-115">AzureRM.BootStrapper</span></span>
    + <span data-ttu-id="d0c1a-116">Vytvoření nového modulu pro správu verzí rutin Azure PowerShellu prostřednictvím profilů verzí</span><span class="sxs-lookup"><span data-stu-id="d0c1a-116">Created new module to manage versions of Azure PowerShell cmdlets through the use of version profiles</span></span>