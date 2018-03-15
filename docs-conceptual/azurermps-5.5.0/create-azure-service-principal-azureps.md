---
title: "Vytvoření instančního objektu Azure s použitím prostředí Azure PowerShell"
description: "Zjistěte, jak pro svou aplikaci nebo službu vytvořit instanční objekt s použitím prostředí Azure PowerShell."
keywords: Azure PowerShell, Azure Active Directory, Azure Active directory, AD, RBAC
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: 6eda2d2a729331b212938aa2681d0188a25b734a
ms.sourcegitcommit: 20af779cd523c758d40e23d60eb989a4ef982d5c
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="create-an-azure-service-principal-with-azure-powershell"></a><span data-ttu-id="d3055-104">Vytvoření instančního objektu Azure s použitím prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3055-104">Create an Azure service principal with Azure PowerShell</span></span>

<span data-ttu-id="d3055-105">Pokud plánujete spravovat svou aplikaci nebo službu s použitím prostředí Azure PowerShell, měli byste ji spouštět pod instančním objektem Azure Active Directory (AAD), a ne pod svými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="d3055-105">If you plan to manage your app or service with Azure PowerShell, you should run it under an Azure Active Directory (AAD) service principal, rather than your own credentials.</span></span> <span data-ttu-id="d3055-106">Toto téma vás provede vytvořením objektu zabezpečení s použitím prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3055-106">This topic steps you through creating a security principal with Azure PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="d3055-107">Instanční objekt můžete vytvořit také na webu Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="d3055-107">You can also create a service principal through the Azure portal.</span></span> <span data-ttu-id="d3055-108">Další podrobnosti najdete v tématu [Vytvoření aplikace služby Active Directory a instančního objektu s přístupem k prostředkům pomocí portálu](/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span><span class="sxs-lookup"><span data-stu-id="d3055-108">Read [Use portal to create Active Directory application and service principal that can access resources](/azure/azure-resource-manager/resource-group-create-service-principal-portal) for more details.</span></span>

## <a name="what-is-a-service-principal"></a><span data-ttu-id="d3055-109">Co je instanční objekt?</span><span class="sxs-lookup"><span data-stu-id="d3055-109">What is a 'service principal'?</span></span>

<span data-ttu-id="d3055-110">Instanční objekt Azure je identita zabezpečení, kterou používají aplikace, služby a nástroje pro automatizaci vytvořené uživatelem pro přístup ke konkrétním prostředkům Azure.</span><span class="sxs-lookup"><span data-stu-id="d3055-110">An Azure service principal is a security identity used by user-created apps, services, and automation tools to access specific Azure resources.</span></span> <span data-ttu-id="d3055-111">Můžete si ho představit jako identitu uživatele (uživatelské jméno a heslo nebo certifikát) s určitou rolí a přísně řízenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="d3055-111">Think of it as a 'user identity' (username and password or certificate) with a specific role, and tightly controlled permissions.</span></span> <span data-ttu-id="d3055-112">Na rozdíl od obecné identity uživatele potřebuje mít možnost provádět pouze určité akce.</span><span class="sxs-lookup"><span data-stu-id="d3055-112">It only needs to be able to do specific things, unlike a general user identity.</span></span> <span data-ttu-id="d3055-113">Zabezpečení můžete zvýšit tak, že mu přidělíte pouze minimální úroveň oprávnění k provádění úloh správy.</span><span class="sxs-lookup"><span data-stu-id="d3055-113">It improves security if you only grant it the minimum permissions level needed to perform its management tasks.</span></span>

## <a name="verify-your-own-permission-level"></a><span data-ttu-id="d3055-114">Ověření vlastní úrovně oprávnění</span><span class="sxs-lookup"><span data-stu-id="d3055-114">Verify your own permission level</span></span>

<span data-ttu-id="d3055-115">Nejprve musíte mít dostatečná oprávnění v Azure Active Directory i v předplatném Azure.</span><span class="sxs-lookup"><span data-stu-id="d3055-115">First, you must have sufficient permissions in both your Azure Active Directory and your Azure subscription.</span></span> <span data-ttu-id="d3055-116">Konkrétně musíte být schopni v Active Directory vytvořit aplikaci a přiřadit roli instančnímu objektu.</span><span class="sxs-lookup"><span data-stu-id="d3055-116">Specifically, you must be able to create an app in the Active Directory, and assign a role to the service principal.</span></span>

<span data-ttu-id="d3055-117">Nejjednodušším způsobem, jak zkontrolovat, jestli má váš účet dostatečná oprávnění, je použít k tomu portál.</span><span class="sxs-lookup"><span data-stu-id="d3055-117">The easiest way to check whether your account has adequate permissions is through the portal.</span></span> <span data-ttu-id="d3055-118">Informace najdete v článku [Kontrola požadovaných oprávnění na portálu](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions).</span><span class="sxs-lookup"><span data-stu-id="d3055-118">See [Check required permission in portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions).</span></span>

## <a name="create-a-service-principal-for-your-app"></a><span data-ttu-id="d3055-119">Vytvoření instančního objektu pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="d3055-119">Create a service principal for your app</span></span>

<span data-ttu-id="d3055-120">Po přihlášení k účtu Azure můžete vytvořit instanční objekt.</span><span class="sxs-lookup"><span data-stu-id="d3055-120">Once you are signed into your Azure account, you can create the service principal.</span></span> <span data-ttu-id="d3055-121">Musíte být schopni identifikovat nasazenou aplikaci jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="d3055-121">You must have one of the following ways to identify your deployed app:</span></span>

* <span data-ttu-id="d3055-122">Jedinečný název nasazené aplikace, například název MyDemoWebApp používaný v následujících příkladech, nebo:</span><span class="sxs-lookup"><span data-stu-id="d3055-122">The unique name of your deployed app, such as "MyDemoWebApp" in the following examples, or</span></span>
* <span data-ttu-id="d3055-123">ID aplikace, jedinečný identifikátor GUID přidružený k nasazené aplikaci, službě nebo objektu.</span><span class="sxs-lookup"><span data-stu-id="d3055-123">the Application ID, the unique GUID associated with your deployed app, service, or object</span></span>

### <a name="get-information-about-your-application"></a><span data-ttu-id="d3055-124">Získání informací o aplikaci</span><span class="sxs-lookup"><span data-stu-id="d3055-124">Get information about your application</span></span>

<span data-ttu-id="d3055-125">S použitím rutiny `Get-AzureRmADApplication` můžete získat informace o aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d3055-125">The `Get-AzureRmADApplication` cmdlet can be used to discover information about your application.</span></span>

```powershell
Get-AzureRmADApplication -DisplayNameStartWith MyDemoWebApp
```

```
DisplayName             : MyDemoWebApp
ObjectId                : 775f64cd-0ec8-4b9b-b69a-8b8946022d9f
IdentifierUris          : {http://MyDemoWebApp}
HomePage                : http://www.contoso.com
Type                    : Application
ApplicationId           : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
AvailableToOtherTenants : False
AppPermissions          :
ReplyUrls               : {}
```

### <a name="create-a-service-principal-for-your-application"></a><span data-ttu-id="d3055-126">Vytvoření instančního objektu pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="d3055-126">Create a service principal for your application</span></span>

<span data-ttu-id="d3055-127">Rutina `New-AzureRmADServicePrincipal` slouží k vytvoření instančního objektu.</span><span class="sxs-lookup"><span data-stu-id="d3055-127">The `New-AzureRmADServicePrincipal` cmdlet is used to create the service principal.</span></span>

```powershell
Add-Type -Assembly System.Web
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADServicePrincipal -ApplicationId 00c01aaa-1603-49fc-b6df-b78c4e5138b4 -Password $password
```

```
DisplayName                    Type                           ObjectId
-----------                    ----                           --------
MyDemoWebApp                   ServicePrincipal               698138e7-d7b6-4738-a866-b4e3081a69e4
```

### <a name="get-information-about-the-service-principal"></a><span data-ttu-id="d3055-128">Získání informací o instančním objektu</span><span class="sxs-lookup"><span data-stu-id="d3055-128">Get information about the service principal</span></span>

```powershell
$svcprincipal = Get-AzureRmADServicePrincipal -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4
$svcprincipal | Select-Object *
```

```
ServicePrincipalNames : {http://MyDemoWebApp, 00c01aaa-1603-49fc-b6df-b78c4e5138b4}
ApplicationId         : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
DisplayName           : MyDemoWebApp
Id                    : 698138e7-d7b6-4738-a866-b4e3081a69e4
Type                  : ServicePrincipal
```

### <a name="sign-in-using-the-service-principal"></a><span data-ttu-id="d3055-129">Přihlášení pomocí instančního objektu</span><span class="sxs-lookup"><span data-stu-id="d3055-129">Sign in using the service principal</span></span>

<span data-ttu-id="d3055-130">Nyní se můžete přihlásit jako nový instanční objekt pro vaši aplikaci s použitím hodnot *appId* a *password*, které jste zadali.</span><span class="sxs-lookup"><span data-stu-id="d3055-130">You can now sign in as the new service principal for your app using the *appId* and *password* you provided.</span></span> <span data-ttu-id="d3055-131">Je třeba zadat ID tenanta pro váš účet.</span><span class="sxs-lookup"><span data-stu-id="d3055-131">You need to supply the Tenant Id for your account.</span></span> <span data-ttu-id="d3055-132">Vaše ID tenanta se zobrazí, když se přihlásíte do Azure s použitím osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="d3055-132">Your Tenant Id is displayed when you sign into Azure with your personal credentials.</span></span>

```powershell
$cred = Get-Credential -UserName $svcprincipal.ApplicationId -Message "Enter Password"
Login-AzureRmAccount -Credential $cred -ServicePrincipal -TenantId XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="d3055-133">Spusťte tento příkaz z nové relace prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3055-133">Run this command from a new PowerShell session.</span></span> <span data-ttu-id="d3055-134">Po úspěšném přihlášení se zobrazí výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="d3055-134">After a successfully signing on you see output something like this:</span></span>

```
Environment           : AzureCloud
Account               : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
SubscriptionId        :
SubscriptionName      :
CurrentStorageAccount :
```

<span data-ttu-id="d3055-135">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="d3055-135">Congratulations!</span></span> <span data-ttu-id="d3055-136">Tyto přihlašovací údaje můžete použít ke spouštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d3055-136">You can use these credentials to run your app.</span></span> <span data-ttu-id="d3055-137">Dále je třeba upravit oprávnění instančního objektu.</span><span class="sxs-lookup"><span data-stu-id="d3055-137">Next, you need to adjust the permissions of the service principal.</span></span>

## <a name="managing-roles"></a><span data-ttu-id="d3055-138">Správa rolí</span><span class="sxs-lookup"><span data-stu-id="d3055-138">Managing roles</span></span>

> [!NOTE]
> <span data-ttu-id="d3055-139">Řízení přístupu na základě role (RBAC) Azure je model definování a správy rolí uživatele a instančních objektů.</span><span class="sxs-lookup"><span data-stu-id="d3055-139">Azure Role-Based Access Control (RBAC) is a model for defining and managing roles for user and service principals.</span></span> <span data-ttu-id="d3055-140">K rolím jsou přiřazeny sady oprávnění určující, ke kterým prostředkům má objekt zabezpečení přístup a které může číst, zapisovat a spravovat.</span><span class="sxs-lookup"><span data-stu-id="d3055-140">Roles have sets of permissions associated with them, which determine the resources a principal can read, access, write, or manage.</span></span> <span data-ttu-id="d3055-141">Další informace o RBAC a rolích najdete v tématu [RBAC: Předdefinované role](/azure/active-directory/role-based-access-built-in-roles).</span><span class="sxs-lookup"><span data-stu-id="d3055-141">For more information on RBAC and roles, see [RBAC: Built-in roles](/azure/active-directory/role-based-access-built-in-roles).</span></span>

<span data-ttu-id="d3055-142">Prostředí Azure PowerShell umožňuje spravovat přiřazování rolí pomocí následujících rutin:</span><span class="sxs-lookup"><span data-stu-id="d3055-142">Azure PowerShell provides the following cmdlets to manage role assignments:</span></span>

* [<span data-ttu-id="d3055-143">Get-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="d3055-143">Get-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/get-azurermroleassignment)
* [<span data-ttu-id="d3055-144">New-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="d3055-144">New-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/new-azurermroleassignment)
* [<span data-ttu-id="d3055-145">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="d3055-145">Remove-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/remove-azurermroleassignment)

<span data-ttu-id="d3055-146">Výchozí role pro instanční objekt je **Přispěvatel**.</span><span class="sxs-lookup"><span data-stu-id="d3055-146">The default role for a service principal is **Contributor**.</span></span> <span data-ttu-id="d3055-147">Tato role vzhledem k rozsáhlosti oprávnění nemusí být v závislosti na rozsahu interakce aplikace se službami Azure ideální.</span><span class="sxs-lookup"><span data-stu-id="d3055-147">It may not be the best choice depending on the scope of your app's interactions with Azure services, given its broad permissions.</span></span>
<span data-ttu-id="d3055-148">Role **Čtenář** je více omezující a může být dobrou volbou pro aplikace s přístupem jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d3055-148">The **Reader** role is more restrictive and can be a good choice for read-only apps.</span></span> <span data-ttu-id="d3055-149">Můžete zobrazit podrobnosti o oprávněních jednotlivých rolí nebo vytvořit vlastní role můžete na webu Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="d3055-149">You can view details on role-specific permissions or create custom ones through the Azure portal.</span></span>

<span data-ttu-id="d3055-150">V tomto příkladu přidáme do předchozího příkladu roli **Čtenář** a odstraníme roli **Přispěvatel**:</span><span class="sxs-lookup"><span data-stu-id="d3055-150">In this example, we add the **Reader** role to our prior example, and delete the **Contributor** one:</span></span>

```powershell
New-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4 -RoleDefinitionName Reader
```

```
RoleAssignmentId   : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG/providers/Microsoft.Authorization/roleAssignments/818892f2-d075-46a1-a3a2-3a4e1a12fcd5
Scope              : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG
DisplayName        : MyDemoWebApp
SignInName         :
RoleDefinitionName : Reader
RoleDefinitionId   : b24988ac-6180-42a0-ab88-20f7382dd24c
ObjectId           : 698138e7-d7b6-4738-a866-b4e3081a69e4
ObjectType         : ServicePrincipal
```

```powershell
Remove-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4 -RoleDefinitionName Contributor
```

<span data-ttu-id="d3055-151">Zobrazení aktuálních přiřazených rolí:</span><span class="sxs-lookup"><span data-stu-id="d3055-151">To view the current roles assigned:</span></span>

```powershell
Get-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4
```

```
RoleAssignmentId   : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG/providers/Microsoft.Authorization/roleAssignments/0906bbd8-9982-4c03-8dae-aeaae8b13f9e
Scope              : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG
DisplayName        : MyDemoWebApp
SignInName         :
RoleDefinitionName : Reader
RoleDefinitionId   : acdd72a7-3385-48ef-bd42-f606fba81ae7
ObjectId           : 698138e7-d7b6-4738-a866-b4e3081a69e4
ObjectType         : ServicePrincipal
```

<span data-ttu-id="d3055-152">Další rutiny prostředí Azure PowerShell pro správu rolí:</span><span class="sxs-lookup"><span data-stu-id="d3055-152">Other Azure PowerShell cmdlets for role management:</span></span>

* [<span data-ttu-id="d3055-153">Get-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="d3055-153">Get-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Get-AzureRmRoleDefinition)
* [<span data-ttu-id="d3055-154">New-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="d3055-154">New-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/New-AzureRmRoleDefinition)
* [<span data-ttu-id="d3055-155">Remove-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="d3055-155">Remove-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Remove-AzureRmRoleDefinition)
* [<span data-ttu-id="d3055-156">Set-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="d3055-156">Set-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Set-AzureRmRoleDefinition)

## <a name="change-the-credentials-of-the-security-principal"></a><span data-ttu-id="d3055-157">Změna přihlašovacích údajů objektu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d3055-157">Change the credentials of the security principal</span></span>

<span data-ttu-id="d3055-158">Z pohledu zabezpečení je dobrým zvykem pravidelně kontrolovat oprávnění a aktualizovat hesla.</span><span class="sxs-lookup"><span data-stu-id="d3055-158">It's a good security practice to review the permissions and update the password regularly.</span></span> <span data-ttu-id="d3055-159">Spravovat a upravovat přihlašovací údaje zabezpečení byste měli také se změnami aplikace.</span><span class="sxs-lookup"><span data-stu-id="d3055-159">You may also want to manage and modify the security credentials as your app changes.</span></span> <span data-ttu-id="d3055-160">Můžeme například změnit heslo instančního objektu vytvořením nového hesla a odebráním předchozího.</span><span class="sxs-lookup"><span data-stu-id="d3055-160">For example, we can change the password of the service principal by creating a new password and removing the old one.</span></span>

### <a name="add-a-new-password-for-the-service-principal"></a><span data-ttu-id="d3055-161">Přidání nového hesla pro instanční objekt</span><span class="sxs-lookup"><span data-stu-id="d3055-161">Add a new password for the service principal</span></span>

```powershell
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -Password $password
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```

### <a name="get-a-list-of-credentials-for-the-service-principal"></a><span data-ttu-id="d3055-162">Získání seznamu přihlašovacích údajů pro instanční objekt</span><span class="sxs-lookup"><span data-stu-id="d3055-162">Get a list of credentials for the service principal</span></span>

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
5/5/2016 4:55:27 PM 5/5/2017 4:55:27 PM ca9d4846-4972-4c70-b6f5-a4effa60b9bc Password
```

### <a name="remove-the-old-password-from-the-service-principal"></a><span data-ttu-id="d3055-163">Odebrání předchozího hesla z instančního objektu</span><span class="sxs-lookup"><span data-stu-id="d3055-163">Remove the old password from the service principal</span></span>

```powershell
Remove-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -KeyId ca9d4846-4972-4c70-b6f5-a4effa60b9bc
```

```
Confirm
Are you sure you want to remove credential with keyId '6f801c3e-6fcd-42b9-be8e-320b17ba1d36' for
service principal objectId '698138e7-d7b6-4738-a866-b4e3081a69e4'.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

### <a name="verify-the-list-of-credentials-for-the-service-principal"></a><span data-ttu-id="d3055-164">Ověření seznamu přihlašovacích údajů pro instanční objekt</span><span class="sxs-lookup"><span data-stu-id="d3055-164">Verify the list of credentials for the service principal</span></span>

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```
