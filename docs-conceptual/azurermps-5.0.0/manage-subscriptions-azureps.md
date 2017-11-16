---
title: "Správa předplatných Azure s využitím prostředí Azure PowerShell | Dokumentace Microsoftu"
description: "Správa předplatných Azure s využitím prostředí Azure PowerShell"
keywords: "Azure PowerShell, předplatné"
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 68d03ec8d1a86fb3b270d02a4697bbf9af847f2d
ms.sourcegitcommit: 358d260a867c6ee2e8700b91f776ba4f1b0e24a5
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="manage-multiple-azure-subscriptions"></a><span data-ttu-id="f9958-104">Správa několika předplatných Azure</span><span class="sxs-lookup"><span data-stu-id="f9958-104">Manage multiple Azure subscriptions</span></span>

<span data-ttu-id="f9958-105">Pokud jste úplně novým uživatelem Azure, máte nejspíš jen jedno předplatné.</span><span class="sxs-lookup"><span data-stu-id="f9958-105">If you are brand new to Azure, you probably only have a single subscription.</span></span> <span data-ttu-id="f9958-106">Pokud ale používáte Azure už delší dobu, pravděpodobně jste si vytvořili více předplatných Azure.</span><span class="sxs-lookup"><span data-stu-id="f9958-106">But if you have been using Azure for a while, you may have created multiple Azure subscriptions.</span></span> <span data-ttu-id="f9958-107">Prostředí Azure PowerShell můžete nakonfigurovat tak, aby se příkazy spouštěly pro konkrétní předplatné.</span><span class="sxs-lookup"><span data-stu-id="f9958-107">You can configure Azure PowerShell to execute commands against a particular subscription.</span></span>

1. <span data-ttu-id="f9958-108">Zobrazte seznam všech předplatných ve vašem účtu.</span><span class="sxs-lookup"><span data-stu-id="f9958-108">Get a list of all subscriptions in your account.</span></span>

    ```powershell
    Get-AzureRmSubscription
    ```

    ```
    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Production Subscription
    CurrentStorageAccount :

    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My DevTest Subscription
    CurrentStorageAccount :

    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Demos
    CurrentStorageAccount :
    ```

2. <span data-ttu-id="f9958-109">Nastavte výchozí položky.</span><span class="sxs-lookup"><span data-stu-id="f9958-109">Set the default.</span></span>

    ```powershell
    Select-AzureRmSubscription -SubscriptionName "My Demos"
    ```

3. <span data-ttu-id="f9958-110">Ověřte změnu spuštěním rutiny `Get-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="f9958-110">Verify the change by running the `Get-AzureRmContext` cmdlet.</span></span>

    ```powershell
    Get-AzureRmContext
    ```

    ```
    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Demos
    CurrentStorageAccount :
    ```

<span data-ttu-id="f9958-111">Po nastavení výchozího předplatného se budou všechny následné příkazy prostředí Azure PowerShell spouštět pro toto předplatné.</span><span class="sxs-lookup"><span data-stu-id="f9958-111">Once you set your default subscription, all subsequent Azure PowerShell commands run against this subscription.</span></span>
