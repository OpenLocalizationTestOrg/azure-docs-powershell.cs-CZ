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
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="manage-multiple-azure-subscriptions"></a>Správa několika předplatných Azure

Pokud jste úplně novým uživatelem Azure, máte nejspíš jen jedno předplatné. Pokud ale používáte Azure už delší dobu, pravděpodobně jste si vytvořili více předplatných Azure. Prostředí Azure PowerShell můžete nakonfigurovat tak, aby se příkazy spouštěly pro konkrétní předplatné.

1. Zobrazte seznam všech předplatných ve vašem účtu.

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

2. Nastavte výchozí položky.

    ```powershell
    Select-AzureRmSubscription -SubscriptionName "My Demos"
    ```

3. Ověřte změnu spuštěním rutiny `Get-AzureRmContext`.

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

Po nastavení výchozího předplatného se budou všechny následné příkazy prostředí Azure PowerShell spouštět pro toto předplatné.
