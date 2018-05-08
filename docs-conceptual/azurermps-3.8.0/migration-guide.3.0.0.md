# <a name="breaking-changes-for-microsoft-azure-powershell-300"></a><span data-ttu-id="43b84-101">Rozbíjející změny v prostředí Azure PowerShell 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="43b84-101">Breaking changes for Microsoft Azure PowerShell 3.0.0.</span></span>

<span data-ttu-id="43b84-102">Tento dokument slouží jednak jako oznámení rozbíjejících změn, a jednak průvodce migrací pro všechny, kteří využívají rutiny prostředí Microsoft Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43b84-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span>  <span data-ttu-id="43b84-103">Každá část popisuje jak důvody rozbíjející změny, tak i migrační cestu nejmenšího odporu.</span><span class="sxs-lookup"><span data-stu-id="43b84-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span>  <span data-ttu-id="43b84-104">Podrobný kontext najdete v žádosti o přijetí změn související s každou změnou.</span><span class="sxs-lookup"><span data-stu-id="43b84-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="43b84-105">Obsah</span><span class="sxs-lookup"><span data-stu-id="43b84-105">Table of Contents</span></span>
1. [<span data-ttu-id="43b84-106">Rozbíjející změny v rutinách Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="43b84-106">Breaking changes to Data Lake Store cmdlets</span></span>](#breaking-changes-to-data-lake-store-cmdlets)
2. [<span data-ttu-id="43b84-107">Rozbíjející změny v rutinách ApiManagement</span><span class="sxs-lookup"><span data-stu-id="43b84-107">Breaking changes to ApiManagement cmdlets</span></span>](#breaking-changes-to-apimanagement-cmdlets)
3. [<span data-ttu-id="43b84-108">Rozbíjející změny v rutinách Network</span><span class="sxs-lookup"><span data-stu-id="43b84-108">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)

## <a name="breaking-changes-to-data-lake-store-cmdlets"></a><span data-ttu-id="43b84-109">Rozbíjející změny v rutinách Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="43b84-109">Breaking changes to Data Lake Store cmdlets</span></span>

<span data-ttu-id="43b84-110">V této vydané verzi ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)) byly ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="43b84-110">The following cmdlets were affected this release ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)):</span></span>

<span data-ttu-id="43b84-111">**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**</span><span class="sxs-lookup"><span data-stu-id="43b84-111">**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**</span></span>
- <span data-ttu-id="43b84-112">Tato rutina byla odstraněna a nahrazuje ji ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span><span class="sxs-lookup"><span data-stu-id="43b84-112">This cmdlet was removed and replaced with ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span></span>
- <span data-ttu-id="43b84-113">Původní rutina vracela složený objekt reprezentující seznam řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="43b84-113">The old cmdlet returned a complex object representing the access control list (ACL).</span></span> <span data-ttu-id="43b84-114">Nová rutina vrací jednoduchý seznam položek v seznamu ACL vybrané cesty.</span><span class="sxs-lookup"><span data-stu-id="43b84-114">The new cmdlet returns a simple list of entries in the chosen path's ACL.</span></span>

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

<span data-ttu-id="43b84-115">**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**</span><span class="sxs-lookup"><span data-stu-id="43b84-115">**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**</span></span>
- <span data-ttu-id="43b84-116">Tato rutina nahrazuje původní rutinu ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.</span><span class="sxs-lookup"><span data-stu-id="43b84-116">This cmdlet replaces the old cmdlet ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.</span></span>
- <span data-ttu-id="43b84-117">Tato nová rutina vrací jednoduchý seznam položek v seznamu ACL vybrané cesty, typ je ``DataLakeStoreItemAce[]``.</span><span class="sxs-lookup"><span data-stu-id="43b84-117">This new cmdlet returns a simple list of entries in the chosen path's ACL, with type ``DataLakeStoreItemAce[]``.</span></span>
- <span data-ttu-id="43b84-118">Výstup této rutiny lze předat v parametru ``-Acl`` následujících rutin:</span><span class="sxs-lookup"><span data-stu-id="43b84-118">The output of this cmdlet can be passed in to the ``-Acl`` parameter of the following cmdlets:</span></span>
   - ``Remove-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAclEntry``

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

<span data-ttu-id="43b84-119">**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**</span><span class="sxs-lookup"><span data-stu-id="43b84-119">**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**</span></span>
- <span data-ttu-id="43b84-120">Tyto rutiny teď umožňují v parametru ``-Acl`` použít ``DataLakeStoreItemAce[]``.</span><span class="sxs-lookup"><span data-stu-id="43b84-120">These cmdlets now accept ``DataLakeStoreItemAce[]`` for the ``-Acl`` parameter.</span></span>
- <span data-ttu-id="43b84-121">``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)`` vrací ``DataLakeStoreItemAce[]``.</span><span class="sxs-lookup"><span data-stu-id="43b84-121">``DataLakeStoreItemAce[]`` is returned by ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span></span>

```powershell
# Old
$acl = Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $acl

# New
$aclEntries = Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $aclEntries
```

## <a name="breaking-changes-to-apimanagement-cmdlets"></a><span data-ttu-id="43b84-122">Rozbíjející změny v rutinách ApiManagement</span><span class="sxs-lookup"><span data-stu-id="43b84-122">Breaking changes to ApiManagement cmdlets</span></span>

<span data-ttu-id="43b84-123">V této vydané verzi ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)) byly ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="43b84-123">The following cmdlets were affected this release ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)):</span></span>

<span data-ttu-id="43b84-124">**New-AzureRmApiManagementVirtualNetwork**</span><span class="sxs-lookup"><span data-stu-id="43b84-124">**New-AzureRmApiManagementVirtualNetwork**</span></span>
- <span data-ttu-id="43b84-125">Požadované parametry odkazující na virtuální síť se změnily a už nevyžadují SubnetName a VnetId pro SubnetResourceId ve formátu ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``</span><span class="sxs-lookup"><span data-stu-id="43b84-125">The required parameters to reference a virtual network changed from requiring SubnetName and VnetId to SubnetResourceId in format ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``</span></span>

```powershell
# Old
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetName <String> -VnetId <Guid>

# New
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>

```

<span data-ttu-id="43b84-126">**Deprecating Cmdlet Set-AzureRmApiManagementVirtualNetworks**</span><span class="sxs-lookup"><span data-stu-id="43b84-126">**Deprecating Cmdlet Set-AzureRmApiManagementVirtualNetworks**</span></span>
- <span data-ttu-id="43b84-127">Rutina se stává zastaralou, protože existují další způsoby, jak nastavit virtuální síť přidruženou k nasazení ApiManagement.</span><span class="sxs-lookup"><span data-stu-id="43b84-127">The Cmdlet is getting deprecated as there was more than one way to Set Virtual Network associated to ApiManagement deployment.</span></span>

```powershell
# Old
$networksList = @()
$networksList += New-AzureRmApiManagementVirtualNetwork -Location $vnetLocation -VnetId $vnetId -SubnetName $subnetName
Set-AzureRmApiManagementVirtualNetworks -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetworks $networksList

# New
$masterRegionVirtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>
Update-AzureRmApiManagementDeployment -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetwork $masterRegionVirtualNetwork
```

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="43b84-128">Rozbíjející změny v rutinách Network</span><span class="sxs-lookup"><span data-stu-id="43b84-128">Breaking changes to Network cmdlets</span></span>

<span data-ttu-id="43b84-129">V této vydané verzi ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)) byly ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="43b84-129">The following cmdlets were affected this release ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)):</span></span>

<span data-ttu-id="43b84-130">**New-AzureRmVirtualNetworkGateway**</span><span class="sxs-lookup"><span data-stu-id="43b84-130">**New-AzureRmVirtualNetworkGateway**</span></span>
- <span data-ttu-id="43b84-131">Popis co se změnilo: Odstranili jsme ``:- Bool parameter:-ActiveActive`` a přidali ``SwitchParameter:-EnableActiveActiveFeature``, což umožňuje zapnutí funkce Active-Active u nově vytvořené brány virtuální sítě.</span><span class="sxs-lookup"><span data-stu-id="43b84-131">Description of what has changed ``:- Bool parameter:-ActiveActive`` is removed and ``SwitchParameter:-EnableActiveActiveFeature`` is added for enabling Active-Active feature on newly creating virtual network gateway.</span></span>

```powershell
# Old 
# Sample of how the cmdlet was previously called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -ActiveActive $true

# New
# Sample of how the cmdlet should now be called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -EnableActiveActiveFeature
```

<span data-ttu-id="43b84-132">Set-AzureRmVirtualNetworkGateway</span><span class="sxs-lookup"><span data-stu-id="43b84-132">Set-AzureRmVirtualNetworkGateway</span></span>
- <span data-ttu-id="43b84-133">Popis co se změnilo: Odstranili jsme ``:- Bool parameter:-ActiveActive`` a přidali 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature``, což umožňuje zapnutí a vypnutí funkce Active-Active u brány virtuální sítě.</span><span class="sxs-lookup"><span data-stu-id="43b84-133">Description of what has changed ``:- Bool parameter:-ActiveActive`` is removed and 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature`` are added for enabling and disabling Active-Active feature on virtual network gateway.</span></span>

```powershell
# Old
# Sample of how the cmdlet was previously called
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -ActiveActive $true
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -ActiveActive $false  

# New
# Sample of how the cmdlet should now be called
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -EnableActiveActiveFeature
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -DisableActiveActiveFeature
```