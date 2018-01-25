# <a name="breaking-changes-for-microsoft-azure-powershell-300"></a>Rozbíjející změny v prostředí Azure PowerShell 3.0.0.

Tento dokument slouží jednak jako oznámení rozbíjejících změn, a jednak průvodce migrací pro všechny, kteří využívají rutiny prostředí Microsoft Azure PowerShell.  Každá část popisuje jak důvody rozbíjející změny, tak i migrační cestu nejmenšího odporu.  Podrobný kontext najdete v žádosti o přijetí změn související s každou změnou.

## <a name="table-of-contents"></a>Obsah
1. [Rozbíjející změny v rutinách Data Lake Store](#breaking-changes-to-data-lake-store-cmdlets)
2. [Rozbíjející změny v rutinách ApiManagement](#breaking-changes-to-apimanagement-cmdlets)
3. [Rozbíjející změny v rutinách Network](#breaking-changes-to-network-cmdlets)

## <a name="breaking-changes-to-data-lake-store-cmdlets"></a>Rozbíjející změny v rutinách Data Lake Store

V této vydané verzi ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)) byly ovlivněny následující rutiny:

**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**
- Tato rutina byla odstraněna a nahrazuje ji ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.
- Původní rutina vracela složený objekt reprezentující seznam řízení přístupu (ACL). Nová rutina vrací jednoduchý seznam položek v seznamu ACL vybrané cesty.

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**
- Tato rutina nahrazuje původní rutinu ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.
- Tato nová rutina vrací jednoduchý seznam položek v seznamu ACL vybrané cesty, typ je ``DataLakeStoreItemAce[]``.
- Výstup této rutiny lze předat v parametru ``-Acl`` následujících rutin:
   - ``Remove-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAclEntry``

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**
- Tyto rutiny teď umožňují v parametru ``-Acl`` použít ``DataLakeStoreItemAce[]``.
- ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)`` vrací ``DataLakeStoreItemAce[]``.

```powershell
# Old
$acl = Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $acl

# New
$aclEntries = Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $aclEntries
```

## <a name="breaking-changes-to-apimanagement-cmdlets"></a>Rozbíjející změny v rutinách ApiManagement

V této vydané verzi ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)) byly ovlivněny následující rutiny:

**New-AzureRmApiManagementVirtualNetwork**
- Požadované parametry odkazující na virtuální síť se změnily a už nevyžadují SubnetName a VnetId pro SubnetResourceId ve formátu ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``

```powershell
# Old
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetName <String> -VnetId <Guid>

# New
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>

```

**Deprecating Cmdlet Set-AzureRmApiManagementVirtualNetworks**
- Rutina se stává zastaralou, protože existují další způsoby, jak nastavit virtuální síť přidruženou k nasazení ApiManagement.

```powershell
# Old
$networksList = @()
$networksList += New-AzureRmApiManagementVirtualNetwork -Location $vnetLocation -VnetId $vnetId -SubnetName $subnetName
Set-AzureRmApiManagementVirtualNetworks -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetworks $networksList

# New
$masterRegionVirtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>
Update-AzureRmApiManagementDeployment -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetwork $masterRegionVirtualNetwork
```

## <a name="breaking-changes-to-network-cmdlets"></a>Rozbíjející změny v rutinách Network

V této vydané verzi ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)) byly ovlivněny následující rutiny:

**New-AzureRmVirtualNetworkGateway**
- Popis co se změnilo: Odstranili jsme ``:- Bool parameter:-ActiveActive`` a přidali ``SwitchParameter:-EnableActiveActiveFeature``, což umožňuje zapnutí funkce Active-Active u nově vytvořené brány virtuální sítě.

```powershell
# Old 
# Sample of how the cmdlet was previously called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -ActiveActive $true

# New
# Sample of how the cmdlet should now be called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -EnableActiveActiveFeature
```

Set-AzureRmVirtualNetworkGateway
- Popis co se změnilo: Odstranili jsme ``:- Bool parameter:-ActiveActive`` a přidali 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature``, což umožňuje zapnutí a vypnutí funkce Active-Active u brány virtuální sítě.

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