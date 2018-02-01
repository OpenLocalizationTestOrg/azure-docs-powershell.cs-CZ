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
ms.sourcegitcommit: 72f56597f0329d35779a3ea4ccea6293f0fd2502
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="create-an-azure-service-principal-with-azure-powershell"></a>Vytvoření instančního objektu Azure s použitím prostředí Azure PowerShell

Pokud plánujete spravovat svou aplikaci nebo službu s použitím prostředí Azure PowerShell, měli byste ji spouštět pod instančním objektem Azure Active Directory (AAD), a ne pod svými přihlašovacími údaji. Toto téma vás provede vytvořením objektu zabezpečení s použitím prostředí Azure PowerShell.

> [!NOTE]
> Instanční objekt můžete vytvořit také na webu Azure Portal. Další podrobnosti najdete v tématu [Vytvoření aplikace služby Active Directory a instančního objektu s přístupem k prostředkům pomocí portálu](/azure/azure-resource-manager/resource-group-create-service-principal-portal).

## <a name="what-is-a-service-principal"></a>Co je instanční objekt?

Instanční objekt Azure je identita zabezpečení, kterou používají aplikace, služby a nástroje pro automatizaci vytvořené uživatelem pro přístup ke konkrétním prostředkům Azure. Můžete si ho představit jako identitu uživatele (uživatelské jméno a heslo nebo certifikát) s určitou rolí a přísně řízenými oprávněními. Na rozdíl od obecné identity uživatele potřebuje mít možnost provádět pouze určité akce. Zabezpečení můžete zvýšit tak, že mu přidělíte pouze minimální úroveň oprávnění k provádění úloh správy.

## <a name="verify-your-own-permission-level"></a>Ověření vlastní úrovně oprávnění

Nejprve musíte mít dostatečná oprávnění v Azure Active Directory i v předplatném Azure. Konkrétně musíte být schopni v Active Directory vytvořit aplikaci a přiřadit roli instančnímu objektu.

Nejjednodušším způsobem, jak zkontrolovat, jestli má váš účet dostatečná oprávnění, je použít k tomu portál. Informace najdete v článku [Kontrola požadovaných oprávnění na portálu](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions).

## <a name="create-a-service-principal-for-your-app"></a>Vytvoření instančního objektu pro aplikaci

Po přihlášení k účtu Azure můžete vytvořit instanční objekt. Musíte být schopni identifikovat nasazenou aplikaci jedním z následujících způsobů:

* Jedinečný název nasazené aplikace, například název MyDemoWebApp používaný v následujících příkladech, nebo:
* ID aplikace, jedinečný identifikátor GUID přidružený k nasazené aplikaci, službě nebo objektu.

### <a name="get-information-about-your-application"></a>Získání informací o aplikaci

S použitím rutiny `Get-AzureRmADApplication` můžete získat informace o aplikaci.

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

### <a name="create-a-service-principal-for-your-application"></a>Vytvoření instančního objektu pro aplikaci

Rutina `New-AzureRmADServicePrincipal` slouží k vytvoření instančního objektu.

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

### <a name="get-information-about-the-service-principal"></a>Získání informací o instančním objektu

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

### <a name="sign-in-using-the-service-principal"></a>Přihlášení pomocí instančního objektu

Nyní se můžete přihlásit jako nový instanční objekt pro vaši aplikaci s použitím hodnot *appId* a *password*, které jste zadali. Je třeba zadat ID tenanta pro váš účet. Vaše ID tenanta se zobrazí, když se přihlásíte do Azure s použitím osobních údajů.

```powershell
$cred = Get-Credential -UserName $svcprincipal.ApplicationId -Message "Enter Password"
Login-AzureRmAccount -Credential $cred -ServicePrincipal -TenantId XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

Spusťte tento příkaz z nové relace prostředí PowerShell. Po úspěšném přihlášení se zobrazí výstup podobný následujícímu:

```
Environment           : AzureCloud
Account               : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
SubscriptionId        :
SubscriptionName      :
CurrentStorageAccount :
```

Blahopřejeme! Tyto přihlašovací údaje můžete použít ke spouštění aplikace. Dále je třeba upravit oprávnění instančního objektu.

## <a name="managing-roles"></a>Správa rolí

> [!NOTE]
> Řízení přístupu na základě role (RBAC) Azure je model definování a správy rolí uživatele a instančních objektů. K rolím jsou přiřazeny sady oprávnění určující, ke kterým prostředkům má objekt zabezpečení přístup a které může číst, zapisovat a spravovat. Další informace o RBAC a rolích najdete v tématu [RBAC: Předdefinované role](/azure/active-directory/role-based-access-built-in-roles).

Prostředí Azure PowerShell umožňuje spravovat přiřazování rolí pomocí následujících rutin:

* [Get-AzureRmRoleAssignment](/powershell/module/azurerm.resources/get-azurermroleassignment)
* [New-AzureRmRoleAssignment](/powershell/module/azurerm.resources/new-azurermroleassignment)
* [Remove-AzureRmRoleAssignment](/powershell/module/azurerm.resources/remove-azurermroleassignment)

Výchozí role pro instanční objekt je **Přispěvatel**. Tato role vzhledem k rozsáhlosti oprávnění nemusí být v závislosti na rozsahu interakce aplikace se službami Azure ideální.
Role **Čtenář** je více omezující a může být dobrou volbou pro aplikace s přístupem jen pro čtení. Můžete zobrazit podrobnosti o oprávněních jednotlivých rolí nebo vytvořit vlastní role můžete na webu Azure Portal.

V tomto příkladu přidáme do předchozího příkladu roli **Čtenář** a odstraníme roli **Přispěvatel**:

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

Zobrazení aktuálních přiřazených rolí:

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

Další rutiny prostředí Azure PowerShell pro správu rolí:

* [Get-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Get-AzureRmRoleDefinition)
* [New-AzureRmRoleDefinition](/powershell/module/azurerm.resources/New-AzureRmRoleDefinition)
* [Remove-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Remove-AzureRmRoleDefinition)
* [Set-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Set-AzureRmRoleDefinition)

## <a name="change-the-credentials-of-the-security-principal"></a>Změna přihlašovacích údajů objektu zabezpečení

Z pohledu zabezpečení je dobrým zvykem pravidelně kontrolovat oprávnění a aktualizovat hesla. Spravovat a upravovat přihlašovací údaje zabezpečení byste měli také se změnami aplikace. Můžeme například změnit heslo instančního objektu vytvořením nového hesla a odebráním předchozího.

### <a name="add-a-new-password-for-the-service-principal"></a>Přidání nového hesla pro instanční objekt

```powershell
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -Password $password
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```

### <a name="get-a-list-of-credentials-for-the-service-principal"></a>Získání seznamu přihlašovacích údajů pro instanční objekt

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
5/5/2016 4:55:27 PM 5/5/2017 4:55:27 PM ca9d4846-4972-4c70-b6f5-a4effa60b9bc Password
```

### <a name="remove-the-old-password-from-the-service-principal"></a>Odebrání předchozího hesla z instančního objektu

```powershell
Remove-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -KeyId ca9d4846-4972-4c70-b6f5-a4effa60b9bc
```

```
Confirm
Are you sure you want to remove credential with keyId '6f801c3e-6fcd-42b9-be8e-320b17ba1d36' for
service principal objectId '698138e7-d7b6-4738-a866-b4e3081a69e4'.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

### <a name="verify-the-list-of-credentials-for-the-service-principal"></a>Ověření seznamu přihlašovacích údajů pro instanční objekt

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```
