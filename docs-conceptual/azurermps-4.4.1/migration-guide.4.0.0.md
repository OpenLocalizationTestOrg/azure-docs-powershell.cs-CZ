# <a name="breaking-changes-for-microsoft-azure-powershell-400"></a><span data-ttu-id="0aa44-101">Rozbíjející změny v prostředí Microsoft Azure PowerShell 4.0.0</span><span class="sxs-lookup"><span data-stu-id="0aa44-101">Breaking changes for Microsoft Azure PowerShell 4.0.0</span></span>

<span data-ttu-id="0aa44-102">Tento dokument slouží jednak jako oznámení rozbíjejících změn, a jednak průvodce migrací pro všechny, kteří využívají rutiny prostředí Microsoft Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0aa44-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span> <span data-ttu-id="0aa44-103">Každá část popisuje jak důvody rozbíjející změny, tak i migrační cestu nejmenšího odporu.</span><span class="sxs-lookup"><span data-stu-id="0aa44-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span> <span data-ttu-id="0aa44-104">Podrobný kontext najdete v žádosti o přijetí změn související s každou změnou.</span><span class="sxs-lookup"><span data-stu-id="0aa44-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="0aa44-105">Obsah</span><span class="sxs-lookup"><span data-stu-id="0aa44-105">Table of Contents</span></span>

- [<span data-ttu-id="0aa44-106">Rozbíjející změny v rutinách Compute</span><span class="sxs-lookup"><span data-stu-id="0aa44-106">Breaking changes to Compute cmdlets</span></span>](#breaking-changes-to-compute-cmdlets)
- [<span data-ttu-id="0aa44-107">Rozbíjející změny v rutinách EventHub</span><span class="sxs-lookup"><span data-stu-id="0aa44-107">Breaking changes to EventHub cmdlets</span></span>](#breaking-changes-to-eventhub-cmdlets)
- [<span data-ttu-id="0aa44-108">Rozbíjející změny v rutinách Insights</span><span class="sxs-lookup"><span data-stu-id="0aa44-108">Breaking changes to Insights cmdlets</span></span>](#breaking-changes-to-insights-cmdlets)
- [<span data-ttu-id="0aa44-109">Rozbíjející změny v rutinách Network</span><span class="sxs-lookup"><span data-stu-id="0aa44-109">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)
- [<span data-ttu-id="0aa44-110">Rozbíjející změny v rutinách ServiceBus</span><span class="sxs-lookup"><span data-stu-id="0aa44-110">Breaking changes to ServiceBus cmdlets</span></span>](#breaking-changes-to-servicebus-cmdlets)
- [<span data-ttu-id="0aa44-111">Rozbíjející změny v rutinách Sql</span><span class="sxs-lookup"><span data-stu-id="0aa44-111">Breaking changes to Sql cmdlets</span></span>](#breaking-changes-to-sql-cmdlets)
- [<span data-ttu-id="0aa44-112">Rozbíjející změny v rutinách Storage</span><span class="sxs-lookup"><span data-stu-id="0aa44-112">Breaking changes to Storage cmdlets</span></span>](#breaking-changes-to-storage-cmdlets)
- [<span data-ttu-id="0aa44-113">Rozbíjející změny v rutinách Profile</span><span class="sxs-lookup"><span data-stu-id="0aa44-113">Breaking Changes to Profile Cmdlets</span></span>](#breaking-changes-to-profile-cmdlets)
## <a name="breaking-changes-to-compute-cmdlets"></a><span data-ttu-id="0aa44-114">Rozbíjející změny v rutinách Compute</span><span class="sxs-lookup"><span data-stu-id="0aa44-114">Breaking changes to Compute cmdlets</span></span>

<span data-ttu-id="0aa44-115">V této vydané verzi byly ovlivněny následující výstupní typy:</span><span class="sxs-lookup"><span data-stu-id="0aa44-115">The following output types were affected this release:</span></span>

### <a name="psvirtualmachine"></a><span data-ttu-id="0aa44-116">PSVirtualMachine</span><span class="sxs-lookup"><span data-stu-id="0aa44-116">PSVirtualMachine</span></span>
- <span data-ttu-id="0aa44-117">Vlastnosti nejvyšší úrovně `DataDiskNames` a `NetworkInterfaceIDs` objektu `PSVirtualMachine` objekt byly z výstupního typu odebrány.</span><span class="sxs-lookup"><span data-stu-id="0aa44-117">Top level properties `DataDiskNames` and `NetworkInterfaceIDs` of nthe `PSVirtualMachine` object have been removed from the output type.</span></span> <span data-ttu-id="0aa44-118">Tyto vlastnosti byly vždy k dispozici ve vlastnostech `StorageProfile` a `NetworkProfile` objektu `PSVirtualMachine` a to je také způsob, jakým bude v budoucnu třeba je získávat.</span><span class="sxs-lookup"><span data-stu-id="0aa44-118">These properties have always been available in the `StorageProfile` and `NetworkProfile` properties of the `PSVirtualMachine` object and will be the way they will need to be accessed going forward.</span></span>
- <span data-ttu-id="0aa44-119">Touto změnou jsou ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-119">This change affects the following cmdlets:</span></span>
    - `Add-AzureRmVMDataDisk`
    - `Add-AzureRmVMNetworkInterface`
    - `Get-AzureRmVM`
    - `Remove-AzureRmVMDataDisk`
    - `Remove-AzureRmVMNetworkInterface`
    - `Set-AzureRmVMDataDisk`

```powershell
# Old
$vm.DataDiskNames
$vm.NetworkInterfaceIDs

# New
$vm.StorageProfile.DataDisks | Select -Property Name
$vm.NetworkProfile.NetworkInterfaces | Select -Property Id
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a><span data-ttu-id="0aa44-120">Rozbíjející změny v rutinách EventHub</span><span class="sxs-lookup"><span data-stu-id="0aa44-120">Breaking changes to EventHub cmdlets</span></span>

<span data-ttu-id="0aa44-121">V této vydané verzi byly ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-121">The following cmdlets were affected this release:</span></span>

### <a name="get-azurermeventhubnamespace"></a><span data-ttu-id="0aa44-122">Get-AzureRmEventHubNamespace</span><span class="sxs-lookup"><span data-stu-id="0aa44-122">Get-AzureRmEventHubNamespace</span></span>
- <span data-ttu-id="0aa44-123">Vlastnost `ResourceGroupName` byla odebrána z výstupního typu `NamespaceAttributes`.</span><span class="sxs-lookup"><span data-stu-id="0aa44-123">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

### <a name="new-azurermeventhubnamespace"></a><span data-ttu-id="0aa44-124">New-AzureRmEventHubNamespace</span><span class="sxs-lookup"><span data-stu-id="0aa44-124">New-AzureRmEventHubNamespace</span></span>
- <span data-ttu-id="0aa44-125">Vlastnost `ResourceGroupName` byla odebrána z výstupního typu `NamespaceAttributes`.</span><span class="sxs-lookup"><span data-stu-id="0aa44-125">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

## <a name="breaking-changes-to-insights-cmdlets"></a><span data-ttu-id="0aa44-126">Rozbíjející změny v rutinách Insights</span><span class="sxs-lookup"><span data-stu-id="0aa44-126">Breaking changes to Insights cmdlets</span></span>

<span data-ttu-id="0aa44-127">V této vydané verzi byly ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-127">The following cmdlets were affected this release:</span></span>
    
### <a name="get-azurermusage"></a><span data-ttu-id="0aa44-128">Get-AzureRmUsage</span><span class="sxs-lookup"><span data-stu-id="0aa44-128">Get-AzureRmUsage</span></span>
- <span data-ttu-id="0aa44-129">Tato rutina je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0aa44-129">This cmdlet has been deprecated.</span></span>

### <a name="remove-azurermalertrule"></a><span data-ttu-id="0aa44-130">Remove-AzureRmAlertRule</span><span class="sxs-lookup"><span data-stu-id="0aa44-130">Remove-AzureRmAlertRule</span></span>
- <span data-ttu-id="0aa44-131">Výstup této rutiny se změnil ze seznamu s jedním objektem na jediný objekt; tento objekt obsahuje ID žádosti a stavový kód.</span><span class="sxs-lookup"><span data-stu-id="0aa44-131">The output of this cmdlet has changed from a list with a single object to a single object; this object includes the requestId, and status code.</span></span>
    
```powershell
# Old  
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name chiricutin
if ($s1 -ne $null)
{
    $r = $s1(0).RequestId
    $s = $s1(0).StatusCode
}

# New
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name chiricutin
$r = $s1.RequestId
$s = $s1.StatusCode
```
    
### <a name="add-azurermlogalertrule"></a><span data-ttu-id="0aa44-132">Add-AzureRmLogAlertRule</span><span class="sxs-lookup"><span data-stu-id="0aa44-132">Add-AzureRmLogAlertRule</span></span>
- <span data-ttu-id="0aa44-133">Tato rutina je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0aa44-133">This cmdlet has been deprecated.</span></span>
    
### <a name="get-azurermalertrule"></a><span data-ttu-id="0aa44-134">Get-AzureRmAlertRule</span><span class="sxs-lookup"><span data-stu-id="0aa44-134">Get-AzureRmAlertRule</span></span>
- <span data-ttu-id="0aa44-135">Každý prvek výstupu této rutiny (seznam objektů) bude zjednodušen, tj. místo vrácení objektů se strukturou `{ Id, Location, Name, Tags, Properties }` vrátí objekty se strukturou `{ Id, Location, Name, Tags, Type, Description, IsEnabled, Condition, Actions, LastUpdatedTime, ...}`, což jsou všechny atributy pro Azure Resource plus všechny atributy AlertRuleResource na nejvyšší úrovni.</span><span class="sxs-lookup"><span data-stu-id="0aa44-135">Each element of the the output (a list of objects) of this cmdlet is flattened, i.e. instead of returning objects with the structure `{ Id, Location, Name, Tags, Properties }` it will return objects with the structure `{ Id, Location, Name, Tags, Type, Description, IsEnabled, Condition, Actions, LastUpdatedTime, ...}`, which is all of the attributes of an Azure Resource plus all of the attributes of an AlertRuleResource at the top level.</span></span>
    
```powershell
# Old
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -fore red "Error updating alert rule"
      
    Write-Host $rules(0).Id
    Write-Host $rules(0).Properties.IsEnabled
    Write-Host $rules(0).Properties.Condition
}

# New
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -fore red "Error updating alert rule"
 
    Write-Host $rules(0).Id
      
    # Properties will remain for a while
    Write-Host $rules(0).Properties.IsEnabled
      
    # But the properties will be at the top level too. Later Properties will be removed
    Write-Host $rules(0).IsEnabled
    Write-Host $rules(0).Condition
}
```
    
### <a name="get-azurermautoscalesetting"></a><span data-ttu-id="0aa44-136">Get-AzureRmAutoscaleSetting</span><span class="sxs-lookup"><span data-stu-id="0aa44-136">Get-AzureRmAutoscaleSetting</span></span>
- <span data-ttu-id="0aa44-137">Pole `AutoscaleSettingResourceName` je zastaralé, protože má vždy stejnou hodnotu jako pole `Name`.</span><span class="sxs-lookup"><span data-stu-id="0aa44-137">The `AutoscaleSettingResourceName` field is deprecated since it always has the same value as the `Name` field.</span></span>

```powershell
# Old  
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
if ($s1.AutoscaleSettingResourceName -ne $s1.Name)
{
    Write-Host "There is something wrong with the name"
}

# New
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
    
# There won't be a AutoscaleSettingResourceName
Write-Host $s1.Name
```
    
### <a name="remove-azurermlogprofile"></a><span data-ttu-id="0aa44-138">Remove-AzureRmLogProfile</span><span class="sxs-lookup"><span data-stu-id="0aa44-138">Remove-AzureRmLogProfile</span></span>
- <span data-ttu-id="0aa44-139">Výstup této rutiny se změní z `Boolean` na objekt obsahující `RequestId` a `StatusCode`</span><span class="sxs-lookup"><span data-stu-id="0aa44-139">The output of this cmdlet will change from `Boolean` to and object containing `RequestId` and `StatusCode`</span></span>

```powershell
# Old  
$s1 = Remove-AzureRmLogProfile -Name myLogProfile
if ($s1 -eq $true)
{
    Write-Host "Removed"
}
else
{
    Write-Host "Failed"
}

# New
$s1 = Remove-AzureRmLogProfile -Name myLogProfile
$r = $s1.RequestId
$s = $s1.StatusCode
```
    
### <a name="add-azurermlogprofile"></a><span data-ttu-id="0aa44-140">Add-AzureRmLogProfile</span><span class="sxs-lookup"><span data-stu-id="0aa44-140">Add-AzureRmLogProfile</span></span>
- <span data-ttu-id="0aa44-141">Výstup této rutiny se změní z objektu obsahujícího Id žádosti, stavový kód a aktualizovaný nebo nově vytvořený prostředek</span><span class="sxs-lookup"><span data-stu-id="0aa44-141">The output of this cmdlet will change from an object that includes the requestId, status code, and the updated or newly created resource</span></span>
    
```powershell
# Old  
$s1 = Add-AzureRmLogProfile -Name default -StorageAccountId /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162 -Locations Global -categ Delete, Write, Action -retention 3
$r = $s1.ServiceBusRuleId

# New
$s1 = Add-AzureRmLogProfile -Name default -StorageAccountId /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162 -Locations Global -categ Delete, Write, Action -retention 3
$r = $s1.RequestId
$s = $s1.StatusCode
$a = $s1.NewResource.ServiceBusRuleId
    
```
    
### <a name="set-azurermdiagnosticsettings"></a><span data-ttu-id="0aa44-142">Set-AzureRmDiagnosticSettings</span><span class="sxs-lookup"><span data-stu-id="0aa44-142">Set-AzureRmDiagnosticSettings</span></span>
- <span data-ttu-id="0aa44-143">Příkaz bude přejmenován na `Update-AzureRmDiagnsoticSettings`</span><span class="sxs-lookup"><span data-stu-id="0aa44-143">The command is going to be renamed to `Update-AzureRmDiagnsoticSettings`</span></span>

```powershell
# Old
Set-AzureRmDiagnosticSettings

# New
Update-AzureRmDiagnosticSettings
```

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="0aa44-144">Rozbíjející změny v rutinách Network</span><span class="sxs-lookup"><span data-stu-id="0aa44-144">Breaking changes to Network cmdlets</span></span>

<span data-ttu-id="0aa44-145">V této vydané verzi byly ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-145">The following cmdlets were affected this release:</span></span>

### <a name="new-azurermvirtualnetworkgatewayconnection"></a><span data-ttu-id="0aa44-146">New-AzureRmVirtualNetworkGatewayConnection</span><span class="sxs-lookup"><span data-stu-id="0aa44-146">New-AzureRmVirtualNetworkGatewayConnection</span></span>
- <span data-ttu-id="0aa44-147">Parametr `EnableBgp` byl změněn tak, aby přijímal `boolean` místo `string`.</span><span class="sxs-lookup"><span data-stu-id="0aa44-147">`EnableBgp` parameter has been changed to take a `boolean` instead of a `string`</span></span>

```powershell
# Old
New-AzureRmVirtualNetworkGatewayConnection -ResourceGroupName "RG" -name "conn1" -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localnetGateway -ConnectionType IPsec -SharedKey "key" -EnableBgp "true"

# New
New-AzureRmVirtualNetworkGatewayConnection -ResourceGroupName "RG" -name "conn1" -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localnetGateway -ConnectionType IPsec -SharedKey "key" -EnableBgp $true
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a><span data-ttu-id="0aa44-148">Rozbíjející změny v rutinách ServiceBus</span><span class="sxs-lookup"><span data-stu-id="0aa44-148">Breaking changes to ServiceBus cmdlets</span></span>

<span data-ttu-id="0aa44-149">V této vydané verzi byly ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-149">The following cmdlets were affected this release:</span></span>

### <a name="get-azurermservicebusnamespace"></a><span data-ttu-id="0aa44-150">Get-AzureRmServiceBusNamespace</span><span class="sxs-lookup"><span data-stu-id="0aa44-150">Get-AzureRmServiceBusNamespace</span></span>
- <span data-ttu-id="0aa44-151">Vlastnost `ResourceGroupName` byla odebrána z výstupního typu `NamespaceAttributes`.</span><span class="sxs-lookup"><span data-stu-id="0aa44-151">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

### <a name="new-azurermservicebusnamespace"></a><span data-ttu-id="0aa44-152">New-AzureRmServiceBusNamespace</span><span class="sxs-lookup"><span data-stu-id="0aa44-152">New-AzureRmServiceBusNamespace</span></span>

- <span data-ttu-id="0aa44-153">Vlastnost `ResourceGroupName` byla odebrána z výstupního typu `NamespaceAttributes`.</span><span class="sxs-lookup"><span data-stu-id="0aa44-153">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

## <a name="breaking-changes-to-sql-cmdlets"></a><span data-ttu-id="0aa44-154">Rozbíjející změny v rutinách Sql</span><span class="sxs-lookup"><span data-stu-id="0aa44-154">Breaking changes to Sql cmdlets</span></span>

<span data-ttu-id="0aa44-155">V této vydané verzi byly ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-155">The following cmdlets were affected this release:</span></span>

### <a name="new-azurermsqldatabasefailovergroup"></a><span data-ttu-id="0aa44-156">New-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="0aa44-156">New-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="0aa44-157">Parametr `Tag` byl odebrán.</span><span class="sxs-lookup"><span data-stu-id="0aa44-157">`Tag` parameter has been removed</span></span>
- <span data-ttu-id="0aa44-158">Parametr `GracePeriodWithDataLossHour` byl přejmenován na `GracePeriodWithDataLossHours`.</span><span class="sxs-lookup"><span data-stu-id="0aa44-158">`GracePeriodWithDataLossHour` parameter has been renamed to `GracePeriodWithDataLossHours`</span></span>

```powershell
# Old
New-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -FailoverPolicy Automatic -GracePeriodWithDataLossHour 1 -Tag @{ Environment="Test" }

# New
New-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -FailoverPolicy Automatic -GracePeriodWithDataLossHours 1
```

### <a name="set-azurermsqldatabasefailovergroup"></a><span data-ttu-id="0aa44-159">Set-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="0aa44-159">Set-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="0aa44-160">Parametr `Tag` byl odebrán.</span><span class="sxs-lookup"><span data-stu-id="0aa44-160">`Tag` parameter has been removed</span></span>
- <span data-ttu-id="0aa44-161">Parametr `GracePeriodWithDataLossHour` byl přejmenován na `GracePeriodWithDataLossHours`.</span><span class="sxs-lookup"><span data-stu-id="0aa44-161">`GracePeriodWithDataLossHour` parameter has been renamed to `GracePeriodWithDataLossHours`</span></span>

```powershell
# Old
Set-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -FailoverPolicy Automatic -GracePeriodWithDataLossHour 1 -Tag @{ Environment="Test" }

# New
Set-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -FailoverPolicy Automatic -GracePeriodWithDataLossHours 1
```

### <a name="add-azurermsqldatabasetofailovergroup"></a><span data-ttu-id="0aa44-162">Add-AzureRmSqlDatabaseToFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="0aa44-162">Add-AzureRmSqlDatabaseToFailoverGroup</span></span>
- <span data-ttu-id="0aa44-163">Parametr `Tag` byl odebrán.</span><span class="sxs-lookup"><span data-stu-id="0aa44-163">`Tag` parameter has been removed</span></span>

```powershell
# Old
Add-AzureRmSqlDatabaseToFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1 -Tag @{ Environment="Test" }

# New
Add-AzureRmSqlDatabaseToFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1
```

###  <a name="remove-azurermsqldatabasefromfailovergroup"></a><span data-ttu-id="0aa44-164">Remove-AzureRmSqlDatabaseFromFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="0aa44-164">Remove-AzureRmSqlDatabaseFromFailoverGroup</span></span>
- <span data-ttu-id="0aa44-165">Parametr `Tag` byl odebrán.</span><span class="sxs-lookup"><span data-stu-id="0aa44-165">`Tag` parameter has been removed</span></span>

```powershell
# Old
Remove-AzureRmSqlDatabaseFromFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1 -Tag @{ Environment="Test" }

# New
Remove-AzureRmSqlDatabaseFromFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1
```

### <a name="remove-azurermsqldatabasefailovergroup"></a><span data-ttu-id="0aa44-166">Remove-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="0aa44-166">Remove-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="0aa44-167">Parametr `PartnerResourceGroupName` byl odebrán.</span><span class="sxs-lookup"><span data-stu-id="0aa44-167">`PartnerResourceGroupName` parameter has been removed</span></span>
- <span data-ttu-id="0aa44-168">Parametr `PartnerServerName` byl odebrán.</span><span class="sxs-lookup"><span data-stu-id="0aa44-168">`PartnerServerName` parameter has been removed</span></span>

```powershell
# Old
Remove-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -PartnerResourceGroupName rg

# New
Remove-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg
```

### <a name="set-azurermsqldatabasethreatdetectionpolicy"></a><span data-ttu-id="0aa44-169">Set-AzureRmSqlDatabaseThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="0aa44-169">Set-AzureRmSqlDatabaseThreatDetectionPolicy</span></span>
- <span data-ttu-id="0aa44-170">Pro parametr `ExcludedDetectionType` už není hodnota `Usage_Anomaly` platná.</span><span class="sxs-lookup"><span data-stu-id="0aa44-170">The value `Usage_Anomaly` is no longer valid for the parameter `ExcludedDetectionType`</span></span>

### <a name="set-azurermsqlserverthreatdetectionpolicy"></a><span data-ttu-id="0aa44-171">Set-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="0aa44-171">Set-AzureRmSqlServerThreatDetectionPolicy</span></span>
- <span data-ttu-id="0aa44-172">Pro parametr `ExcludedDetectionType` už není hodnota `Usage_Anomaly` platná.</span><span class="sxs-lookup"><span data-stu-id="0aa44-172">The value `Usage_Anomaly` is no longer valid for the parameter `ExcludedDetectionType`</span></span>

## <a name="breaking-changes-to-storage-cmdlets"></a><span data-ttu-id="0aa44-173">Rozbíjející změny v rutinách Storage</span><span class="sxs-lookup"><span data-stu-id="0aa44-173">Breaking changes to Storage cmdlets</span></span>

<span data-ttu-id="0aa44-174">V této vydané verzi byly ovlivněny následující vlastnosti výstupních typů:</span><span class="sxs-lookup"><span data-stu-id="0aa44-174">The following output type properties were affected this release:</span></span>

### <a name="azurestorageblobicloudblobserviceclient"></a><span data-ttu-id="0aa44-175">AzureStorageBlob.ICloudBlob.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="0aa44-175">AzureStorageBlob.ICloudBlob.ServiceClient</span></span>
- <span data-ttu-id="0aa44-176">Následující vlastnosti byly z tohoto typu odebrány (_Poznámka:_ jsou stále dostupné ve vlastnosti `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="0aa44-176">The following properties were removed from this type (_note_: they can still be found in `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `ServerTimeout`
    - `ParallelOperationThreadCount`
    - `SingleBlobUploadThresholdInBytes`
- <span data-ttu-id="0aa44-177">Touto změnou jsou ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-177">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageBlob`
    - `Get-AzureStorageBlobContent`
    - `Get-AzureStorageBlobCopyState`
    - `Set-AzureStorageBlobContent`
    - `Start-AzureStorageBlobCopy`
    - `Stop-AzureStorageBlobCopy`
    
### <a name="azurestoragecontainercloudblobcontainerserviceclient"></a><span data-ttu-id="0aa44-178">AzureStorageContainer.CloudBlobContainer.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="0aa44-178">AzureStorageContainer.CloudBlobContainer.ServiceClient</span></span>
- <span data-ttu-id="0aa44-179">Následující vlastnosti byly z tohoto typu odebrány (_Poznámka:_ jsou stále dostupné ve vlastnosti `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="0aa44-179">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `ServerTimeout`
    - `ParallelOperationThreadCount`
    - `SingleBlobUploadThresholdInBytes`
- <span data-ttu-id="0aa44-180">Touto změnou jsou ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-180">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageContainer`
    - `New-AzureStorageContainer`
    - `Set-AzureStorageContainerAcl`
    
### <a name="azurestoragequeuecloudqueueserviceclient"></a><span data-ttu-id="0aa44-181">AzureStorageQueue.CloudQueue.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="0aa44-181">AzureStorageQueue.CloudQueue.ServiceClient</span></span>
- <span data-ttu-id="0aa44-182">Následující vlastnosti byly z tohoto typu odebrány (_Poznámka:_ jsou stále dostupné ve vlastnosti `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="0aa44-182">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `RetryPolicy`
    - `ServerTimeout`
- <span data-ttu-id="0aa44-183">Touto změnou jsou ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-183">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageQueue`
    - `New-AzureStorageQueue`
    
### <a name="azurestoragetablecloudtableserviceclient"></a><span data-ttu-id="0aa44-184">AzureStorageTable.CloudTable.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="0aa44-184">AzureStorageTable.CloudTable.ServiceClient</span></span>
- <span data-ttu-id="0aa44-185">Následující vlastnosti byly z tohoto typu odebrány (_Poznámka:_ jsou stále dostupné ve vlastnosti `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="0aa44-185">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `PayloadFormat`
    - `RetryPolicy`
    - `ServerTimeout`
- <span data-ttu-id="0aa44-186">Touto změnou jsou ovlivněny následující rutiny:</span><span class="sxs-lookup"><span data-stu-id="0aa44-186">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageTable`
    - `New-AzureStorageTable`
    
```powershell
# Old
$LocationMode = (Get-AzureStorageBlob -Container $containername)[0].ICloudBlob.ServiceClient.LocationMode       
$ParallelOperationThreadCount = (Get-AzureStorageContainer -Container $containername).CloudBlobContainer.ServiceClient.ParallelOperationThreadCount
$PayloadFormat = (Get-AzureStorageTable -Name $tablename).CloudTable.ServiceClient.PayloadFormat
$RetryPolicy = (Get-AzureStorageQueue -Name $queuename).CloudQueue.ServiceClient.RetryPolicy

# New
$LocationMode = (Get-AzureStorageBlob -Container $containername)[0].ICloudBlob.ServiceClient.DefaultRequestOptions.LocationMode     
$ParallelOperationThreadCount = (Get-AzureStorageContainer -Container $containername).CloudBlobContainer.ServiceClient.DefaultRequestOptions.ParallelOperationThreadCount
$PayloadFormat = (Get-AzureStorageTable -Name $tablename).CloudTable.ServiceClient.DefaultRequestOptions.PayloadFormat
$RetryPolicy = (Get-AzureStorageQueue -Name $queuename).CloudQueue.ServiceClient.DefaultRequestOptions.RetryPolicy
```

## <a name="breaking-changes-to-profile-cmdlets"></a><span data-ttu-id="0aa44-187">Rozbíjející změny v rutinách Profile</span><span class="sxs-lookup"><span data-stu-id="0aa44-187">Breaking Changes to Profile Cmdlets</span></span>

<span data-ttu-id="0aa44-188">Následující rutiny a výstupní typy rutin se v této vydané verzi změnily.</span><span class="sxs-lookup"><span data-stu-id="0aa44-188">The following cmdlets and cmdlet output types were changed in this release.</span></span>

### <a name="add-azurermaccount-breaking-changes"></a><span data-ttu-id="0aa44-189">Rozbíjející změny v Add-AzureRmAccount</span><span class="sxs-lookup"><span data-stu-id="0aa44-189">Add-AzureRmAccount breaking changes</span></span>

- <span data-ttu-id="0aa44-190">Parametr ```EnvironmentName``` byl odebrán a nahrazen parametrem ```Environment```, ```Environment``` nyní přebírá řetězec, a nikoli objekt ```AzureEnvironment```.</span><span class="sxs-lookup"><span data-stu-id="0aa44-190">```EnvironmentName``` parameter has been removed and replaced with ```Environment```, the ```Environment``` now takes a string and not an ```AzureEnvironment``` object</span></span>

```powershell
# Old
Add-AzureRmAccount -EnvironmentName AzureChinaCloud

# New
Add-AzureRmAccount -Environment AzureChinaCloud
```

### <a name="select-azurermprofile-was-renamed-to-import-azurermcontext"></a><span data-ttu-id="0aa44-191">Rutina Select-AzureRmProfile byla přejmenována na Import-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="0aa44-191">Select-AzureRmProfile was renamed to Import-AzureRmContext</span></span>

<span data-ttu-id="0aa44-192">Přejmenování ```Select-AzureRmProfile``` na ```Import-AzureRmContext```</span><span class="sxs-lookup"><span data-stu-id="0aa44-192">```Select-AzureRmProfile``` was renamed to ```Import-AzureRmContext```</span></span>

```powershell
# Old
Select-AzureRmProfile -Path c:\mydir\myprofile.json

# New
Import-AzureRmContext -Path c:\mydir\myprofile.json
```

### <a name="save-azurermprofile-was-renamed-to-save-azurermcontext"></a><span data-ttu-id="0aa44-193">Rutina Save-AzureRmProfile byla přejmenována na Save-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="0aa44-193">Save-AzureRmProfile was renamed to Save-AzureRmContext</span></span>

<span data-ttu-id="0aa44-194">Přejmenování ```Save-AzureRmProfile``` na ```Save-AzureRmContext```</span><span class="sxs-lookup"><span data-stu-id="0aa44-194">```Save-AzureRmProfile``` was renamed to ```Save-AzureRmContext```</span></span>

```powershell
# Old
Save-AzureRmProfile -Path c:\mydir\myprofile.json

# New
Save-AzureRmContext -Path c:\mydir\myprofile.json
```
### <a name="breaking-changes-to-output-psazurecontext-type"></a><span data-ttu-id="0aa44-195">Rozbíjející změny výstupního typu PSAzureContext</span><span class="sxs-lookup"><span data-stu-id="0aa44-195">Breaking Changes to output PSAzureContext Type</span></span>

- <span data-ttu-id="0aa44-196">Vlastnost ```TokenCache``` byla změněna na typ, který implementuje ```IAzureTokenCache``` místo ```byte[]```</span><span class="sxs-lookup"><span data-stu-id="0aa44-196">The ```TokenCache``` property changed to a type that implements ```IAzureTokenCache``` instead of a ```byte[]```</span></span>

```powershell
# Old
$bytes = (Get-AzureRmContext).TokenCache
$bytes = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).TokenCache
$bytes = (Add-AzureRmAccount).Context.TokenCache

# New
$bytes = (Get-AzureRmContext).TokenCache.CacheData
$bytes = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).TokenCache.CacheData
$bytes = (Add-AzureRmAccount).Context.TokenCache.CacheData
```

### <a name="breaking-changes-to-the-output-psazureaccount-type"></a><span data-ttu-id="0aa44-197">Rozbíjející změny výstupního typu PSAzureAccount</span><span class="sxs-lookup"><span data-stu-id="0aa44-197">Breaking Changes to the output PSAzureAccount Type</span></span>

- <span data-ttu-id="0aa44-198">Vlastnost ```AccountType``` byla změněna na ```Type```</span><span class="sxs-lookup"><span data-stu-id="0aa44-198">The ```AccountType``` property was changed to ```Type```</span></span>

```powershell
# Old
$type = (Get-AzureRmContext).Account.AccountType
$type = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).Account.AccountType
$type = (Add-AzureRmAccount).Context.Account.AccountType

# New 
$type = (Get-AzureRmContext).Account.Type
$type = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).Account.Type
$type = (Add-AzureRmAccount).Context.Account.Type
```

### <a name="breaking-changes-to-the-output-psazuresubscription-type"></a><span data-ttu-id="0aa44-199">Rozbíjející změny výstupního typu PSAzureSubscription</span><span class="sxs-lookup"><span data-stu-id="0aa44-199">Breaking Changes to the output PSAzureSubscription Type</span></span>
- <span data-ttu-id="0aa44-200">Vlastnost ```SubscriptionId``` byla změněna na ```Id```</span><span class="sxs-lookup"><span data-stu-id="0aa44-200">The ```SubscriptionId``` property was changed to ```Id```</span></span>

```powershell
# Old
$id =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).SubscriptionId
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.SubscriptionId
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionId
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionId

# New
$id =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).Id
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.Id
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Id
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Id
```

- <span data-ttu-id="0aa44-201">Vlastnost ```SubscriptionName``` byla změněna na ```Name```</span><span class="sxs-lookup"><span data-stu-id="0aa44-201">The ```SubscriptionName``` property was changed to ```Name```</span></span>

```powershell
# Old
$name =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).SubscriptionName
$name =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.SubscriptionName
$name =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionName
$name =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionName

# New
$name =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).Name
$name =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.Name
$name =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Name
$name =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Name
```

### <a name="breaking-changes-to-the-output-psazuretenant-type"></a><span data-ttu-id="0aa44-202">Rozbíjející změny výstupního typu PSAzureTenant</span><span class="sxs-lookup"><span data-stu-id="0aa44-202">Breaking Changes to the output PSAzureTenant Type</span></span>

- <span data-ttu-id="0aa44-203">Vlastnost ```TenantId``` byla změněna na ```Id```</span><span class="sxs-lookup"><span data-stu-id="0aa44-203">The ```TenantId``` property was changed to ```Id```</span></span>

```powershell
# Old
$id =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).TenantId
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Tenant.TenantId
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.TenantId
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.TenantId

# New
$id =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Id
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Tenant.Id
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.Id
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.Id
```

- <span data-ttu-id="0aa44-204">Vlastnost ```Domain``` byla změněna na ```Directory```</span><span class="sxs-lookup"><span data-stu-id="0aa44-204">The ```Domain``` property was changed to ```Directory```</span></span>

```powershell
# Old
$tenantName =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Domain

# New
$tenantName =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Directory
```
