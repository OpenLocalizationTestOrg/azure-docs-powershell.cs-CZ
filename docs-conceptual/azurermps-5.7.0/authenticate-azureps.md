---
title: Přihlášení s využitím prostředí Azure PowerShell
description: Přihlášení s využitím prostředí Azure PowerShell
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: f07dee0eed106e39879d58ae06ff08b787faa531
ms.sourcegitcommit: 5f0013981fcea1d689649b9a2b2ffe84ae842e56
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="log-in-with-azure-powershell"></a><span data-ttu-id="0f6d2-103">Přihlášení s využitím prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f6d2-103">Log in with Azure PowerShell</span></span>

<span data-ttu-id="0f6d2-104">Prostředí Azure PowerShell podporuje několik způsobů přihlášení.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-104">Azure PowerShell supports multiple login methods.</span></span> <span data-ttu-id="0f6d2-105">Nejjednodušším způsobem, jak začít, je přihlásit se interaktivně na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-105">The simplest way to get started is to log in interactively at the command line.</span></span>

## <a name="interactive-log-in"></a><span data-ttu-id="0f6d2-106">Interaktivní přihlášení</span><span class="sxs-lookup"><span data-stu-id="0f6d2-106">Interactive log in</span></span>

1. <span data-ttu-id="0f6d2-107">Zadejte `Connect-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-107">Type `Connect-AzureRmAccount`.</span></span> <span data-ttu-id="0f6d2-108">Zobrazí se dialogové okno s výzvou k zadání přihlašovacích údajů Azure.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-108">You will get dialog box asking for your Azure credentials.</span></span>

2. <span data-ttu-id="0f6d2-109">Zadejte e-mailovou adresu a heslo, které jsou spojené s vaším účtem.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-109">Type the email address and password associated with your account.</span></span> <span data-ttu-id="0f6d2-110">Azure přihlašovací údaje ověří, uloží je a pak zavře okno.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-110">Azure authenticates and saves the credential information, and then closes the window.</span></span>

## <a name="log-in-with-a-service-principal"></a><span data-ttu-id="0f6d2-111">Přihlášení pomocí instančního objektu</span><span class="sxs-lookup"><span data-stu-id="0f6d2-111">Log in with a service principal</span></span>

<span data-ttu-id="0f6d2-112">Instanční objekty umožňují vytvořit neinteraktivní účty, pomocí kterých můžete manipulovat s prostředky.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-112">Service principals provide a way for you to create non-interactive accounts that you can use to manipulate resources.</span></span> <span data-ttu-id="0f6d2-113">Instanční objekty se podobají uživatelským účtům, na které můžete pomocí Azure Active Directory aplikovat pravidla.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-113">Service principals are like user accounts to which you can apply rules using Azure Active Directory.</span></span> <span data-ttu-id="0f6d2-114">Tím, že instančnímu objektu přidělíte minimální potřebná oprávnění, můžete zajistit ještě větší zabezpečení skriptů pro automatizaci.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-114">By granting the minimum permissions needed to a service principal, you can ensure your automation scripts are even more secure.</span></span>

1. <span data-ttu-id="0f6d2-115">Pokud ještě nemáte instanční objekt, [vytvořte si ho](create-azure-service-principal-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="0f6d2-115">If you don't already have a service principal, [create one](create-azure-service-principal-azureps.md).</span></span>

2. <span data-ttu-id="0f6d2-116">Přihlaste se pomocí instančního objektu.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-116">Log in with the service principal.</span></span>

    ```powershell
    Connect-AzureRmAccount -ServicePrincipal -ApplicationId  "http://my-app" -Credential $pscredential -TenantId $tenantid
    ```

    <span data-ttu-id="0f6d2-117">Pokud chcete zjistit svou hodnotu TenantId, interaktivně se přihlaste a pak z předplatného zjistěte hodnotu TenantId.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-117">To get your TenantId, log in interactively and then get the TenantId from your subscription.</span></span>

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
    ```

### <a name="log-in-using-an-azure-vm-managed-service-identity"></a><span data-ttu-id="0f6d2-118">Přihlášení pomocí identity spravované služby virtuálního počítače Azure</span><span class="sxs-lookup"><span data-stu-id="0f6d2-118">Log in using an Azure VM Managed Service Identity</span></span>

<span data-ttu-id="0f6d2-119">Identita spravované služby (MSI) je funkce Azure Active Directory ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-119">Managed Service Identity (MSI) is a preview feature of Azure Active Directory.</span></span> <span data-ttu-id="0f6d2-120">Pomocí instančního objektu MSI se můžete přihlásit a získat přístupový token jen pro aplikace pro přístup k dalším prostředkům.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-120">You can use an MSI service principal for sign-in, and acquire an app-only access token to access other resources.</span></span>

<span data-ttu-id="0f6d2-121">Další informace o MSI najdete v tématu [Použití identity spravované služby (MSI) virtuálního počítače Azure k přihlášení a získání tokenu](/azure/active-directory/msi-how-to-get-access-token-using-msi).</span><span class="sxs-lookup"><span data-stu-id="0f6d2-121">For more information about MSI, see [How to use an Azure VM Managed Service Identity (MSI) for sign-in and token acquisition](/azure/active-directory/msi-how-to-get-access-token-using-msi).</span></span>

## <a name="log-in-to-another-cloud"></a><span data-ttu-id="0f6d2-122">Přihlášení k jinému cloudu</span><span class="sxs-lookup"><span data-stu-id="0f6d2-122">Log in to another Cloud</span></span>

<span data-ttu-id="0f6d2-123">Azure Cloud Services poskytují různá prostředí, která dodržují vládní nařízení různých zemí týkající se manipulace s daty.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-123">Azure cloud services provide different environments that adhere to the data-handling regulations of various governments.</span></span> <span data-ttu-id="0f6d2-124">Pokud se váš účet Azure nachází v jednom z cloudů pro státní správu, musíte při přihlášení zadat prostředí.</span><span class="sxs-lookup"><span data-stu-id="0f6d2-124">If your Azure account is in one the government clouds, you need to specify the environment when you sign in.</span></span> <span data-ttu-id="0f6d2-125">Pokud máte účet Azure například v cloudu v Číně, přihlásíte pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="0f6d2-125">For example, if you account is in the China cloud you sign on using the following command:</span></span>

```powershell
Connect-AzureRmAccount -Environment AzureChinaCloud
```

<span data-ttu-id="0f6d2-126">Seznam dostupných prostředí zobrazíte spuštěním tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="0f6d2-126">Use the following command to get a list of available environments:</span></span>

```powershell
Get-AzureRmEnvironment | Select-Object Name
```

```
Name
----
AzureCloud
AzureChinaCloud
AzureUSGovernment
AzureGermanCloud
```

## <a name="learn-more-about-managing-azure-role-based-access"></a><span data-ttu-id="0f6d2-127">Další informace o správě přístupu na základě rolí Azure</span><span class="sxs-lookup"><span data-stu-id="0f6d2-127">Learn more about managing Azure role-based access</span></span>

<span data-ttu-id="0f6d2-128">Další informace o ověřování a správě předplatných v Azure najdete v článku [Správa účtů, předplatných a správních rolí](/azure/active-directory/role-based-access-control-configure).</span><span class="sxs-lookup"><span data-stu-id="0f6d2-128">For more information about authentication and subscription management in Azure, see [Manage Accounts, Subscriptions, and Administrative Roles](/azure/active-directory/role-based-access-control-configure).</span></span>

<span data-ttu-id="0f6d2-129">Rutiny prostředí Azure PowerShell pro správu rolí</span><span class="sxs-lookup"><span data-stu-id="0f6d2-129">Azure PowerShell cmdlets for role management</span></span>

* [<span data-ttu-id="0f6d2-130">Get-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="0f6d2-130">Get-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleAssignment)
* [<span data-ttu-id="0f6d2-131">Get-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="0f6d2-131">Get-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleDefinition)
* [<span data-ttu-id="0f6d2-132">New-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="0f6d2-132">New-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleAssignment)
* [<span data-ttu-id="0f6d2-133">New-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="0f6d2-133">New-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleDefinition)
* [<span data-ttu-id="0f6d2-134">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="0f6d2-134">Remove-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleAssignment)
* [<span data-ttu-id="0f6d2-135">Remove-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="0f6d2-135">Remove-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleDefinition)
* [<span data-ttu-id="0f6d2-136">Set-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="0f6d2-136">Set-AzureRmRoleDefinition</span></span>](/powershell/moduel/AzureRM.Resources/Set-AzureRmRoleDefinition)
