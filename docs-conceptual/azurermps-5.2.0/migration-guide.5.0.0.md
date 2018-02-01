# <a name="breaking-changes-for-microsoft-azure-powershell-500"></a>Rozbíjející změny v prostředí Azure PowerShell 5.0.0.x

Tento dokument slouží jednak jako oznámení rozbíjejících změn, a jednak průvodce migrací pro všechny, kteří využívají rutiny prostředí Microsoft Azure PowerShell. Každá část popisuje jak důvody rozbíjející změny, tak i migrační cestu nejmenšího odporu. Podrobný kontext najdete v žádosti o přijetí změn související s každou změnou.

## <a name="table-of-contents"></a>Obsah

- [Rozbíjející změny v rutinách ApiManagement](#breaking-changes-to-apimanagement-cmdlets)
- [Rozbíjející změny v rutinách Batch](#breaking-changes-to-batch-cmdlets)
- [Rozbíjející změny v rutinách Compute](#breaking-changes-to-compute-cmdlets)
- [Rozbíjející změny v rutinách EventHub](#breaking-changes-to-eventhub-cmdlets)
- [Rozbíjející změny v rutinách Insights](#breaking-changes-to-insights-cmdlets)
- [Rozbíjející změny v rutinách Network](#breaking-changes-to-network-cmdlets)
- [Rozbíjející změny v rutinách Resources](#breaking-changes-to-resources-cmdlets)
- [Rozbíjející změny v rutinách ServiceBus](#breaking-changes-to-servicebus-cmdlets)

## <a name="breaking-changes-to-apimanagement-cmdlets"></a>Rozbíjející změny v rutinách ApiManagement

### <a name="new-azurermapimanagementbackendproxy"></a>**New-AzureRmApiManagementBackendProxy**
- Parametry „UserName“ a „Password“ se nahrazují objektem PSCredential

```powershell
# Old
New-AzureRmApiManagementBackendProxy [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
New-AzureRmApiManagementBackendProxy [other required parameters] -Credential $PSCredentialVariable
```

### <a name="new-azurermapimanagementuser"></a>**New-AzureRmApiManagementUser**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
New-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapimanagementuser"></a>**Set-AzureRmApiManagementUser**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
Set-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-batch-cmdlets"></a>Rozbíjející změny v rutinách Batch

### <a name="new-azurebatchcertificate"></a>**New-AzureBatchCertificate**
- Parametr `Password` se nahrazuje řetězcem Secure

```powershell
# Old
New-AzureBatchCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureBatchCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchcomputenodeuser"></a>**New-AzureBatchComputeNodeUser**
- Parametr `Password` se nahrazuje řetězcem Secure

```powershell
# Old
New-AzureBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
New-AzureBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermbatchcomputenodeuser"></a>**Set-AzureRmBatchComputeNodeUser**
- Parametr `Password` se nahrazuje řetězcem Secure

```powershell
# Old
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchtask"></a>**New-AzureBatchTask**
 - Odstranění přepínače `RunElevated` a jeho nahrazení přepínačem `UserIdentity`.

```powershell
# Old
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -RunElevated $TRUE

# New
$autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Task", "Admin")
$userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -UserIdentity $userIdentity
```

To ovlivní navíc vlastnost `RunElevated` u rutin `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` a `PSJobReleaseTask`.

### <a name="psmultiinstancesettings"></a>**PSMultiInstanceSettings**

- Konstruktor `PSMultiInstanceSettings` už nepřijímá vyžadovaný parametr `numberOfInstances`, místo toho vyžaduje parametr `coordinationCommandLine`.

```powershell
# Old
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @(2)
$settings.CoordinationCommandLine = "cmd /c echo hello"
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings

# New
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @("cmd /c echo hello", 2)
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings
```

### <a name="get-azurebatchtask"></a>**Get-AzureBatchTask**
 - Byla odebrána vlastnost `RunElevated` u `PSCloudTask`. Byla přidána vlastnost `UserIdentity` nahrazující `RunElevated`.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.RunElevated

# New
$task = Get-AzureBatchTask [parameters]
$task.UserIdentity.AutoUser.ElevationLevel
```

To ovlivní navíc vlastnost `RunElevated` u rutin `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` a `PSJobReleaseTask`.

### <a name="multiple-types"></a>**Několik typů**

- Byla přejmenována vlastnost `SchedulingError` u `PSExitConditions` na `PreProcessingError`.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.PreProcessingError
```

### <a name="multiple-types"></a>**Několik typů**

- Byla přejmenována vlastnost `SchedulingError` u `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation` a `PSTaskExecutionInformation` na `FailureInformation`.
  - Vrací se `FailureInformation`, kdykoli dojde k selhání úlohy. To zahrnuje všechny předchozí případy chyb plánu, stejně jako nenulové ukončovací kódy úloh a selhání nahrávání souborů z nové funkce pro výstupní soubory.
  - Struktura je stejná jako předtím, při použití tohoto typu tedy není nutná změna programu.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.FailureInformation
```

To ovlivňuje také: Get-AzureBatchPool, Get-AzureBatchSubtask a Get-AzureBatchJobPreparationAndReleaseTaskStatus

### <a name="new-azurebatchpool"></a>**New-AzureBatchPool**
 - Odstranění přepínače `TargetDedicated` a jeho nahrazení přepínači `TargetDedicatedComputeNodes` a `TargetLowPriorityComputeNodes`.
 - `TargetDedicatedComputeNodes` má nový alias `TargetDedicated`.

```powershell
# Old
New-AzureBatchPool [other parameters] [-TargetDedicated <Int32>]

# New
New-AzureBatchPool [other parameters] [-TargetDedicatedComputeNodes <Int32>] [-TargetLowPriorityComputeNodes <Int32>]
```

To ovlivňuje také: Start-AzureBatchPoolResize

### <a name="get-azurebatchpool"></a>**Get-AzureBatchPool**
 - Přejmenovány vlastnosti `TargetDedicated` a `CurrentDedicated` vlastnosti u `PSCloudPool` na `TargetDedicatedComputeNodes` a `CurrentDedicatedComputeNodes`.

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.TargetDedicated
$pool.CurrentDedicated

# New
$pool = Get-AzureBatchPool [parameters]
$pool.TargetDedicatedComputeNodes
$pool.CurrentDedicatedComputeNodes
```

### <a name="type-pscloudpool"></a>**Typ PSCloudPool**

- Přejmenováno `ResizeError` na `ResizeErrors` u `PSCloudPool`, nyní jde o kolekci.

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeError

# New
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeErrors[0]
```

### <a name="new-azurebatchjob"></a>**New-AzureBatchJob**
- Byla přejmenována vlastnost `TargetDedicated` u `PSPoolSpecification` na `TargetDedicatedComputeNodes`.

```powershell
# Old
$poolInfo = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
$poolInfo.AutoPoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification.TargetDedicated = 5
New-AzureBatchJob [other parameters] -PoolInformation $poolInfo

# New
$poolInfo = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
$poolInfo.AutoPoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification.TargetDedicatedComputeNodes = 5
New-AzureBatchJob [other parameters] -PoolInformation $poolInfo
```

### <a name="get-azurebatchnodefile"></a>**Get-AzureBatchNodeFile**
 - Odstraněn přepínač `Name`, nahrazuje ho `Path`.
 - `Path` má nový alias `Name`.

```powershell
# Old
Get-AzureBatchNodeFile [other parameters] [[-Name] <String>]

# New
Get-AzureBatchNodeFile [other parameters] [[-Path] <String>]
```

To ovlivňuje také: Get-AzureBatchNodeFileContent a Remove-AzureBatchNodeFile

### <a name="type-psnodefile"></a>Typ **PSNodeFile**

 - Byla přejmenována vlastnost `Name` u `PSNodeFile` na `Path`.

```powershell
# Old
$file = Get-AzureBatchNodeFile [parameters]
$file.Name

# New
$file = Get-AzureBatchNodeFile [parameters]
$file.Path
```

### <a name="get-azurebatchsubtask"></a>**Get-AzureBatchSubtask**
- Vlastnosti `PreviousState` a `State` u `PSSubtaskInformation` již nejsou typu `TaskState`, místo toho jsou typu `SubtaskState`.
  - Na rozdíl od `TaskState`, `SubtaskState` nemá žádnou hodnotu `Active`, protože není možné, aby pro dílčí úkoly byly ve stavu `Active`.

```powershell
# Old
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.TaskState.Running) { }

# New
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.SubtaskState.Running) { }
```

## <a name="breaking-changes-to-compute-cmdlets"></a>Rozbíjející změny v rutinách Compute

### <a name="set-azurermvmaccessextension"></a>**Set-AzureRmVMAccessExtension**
- Parametry „UserName“ a „Password“ se nahrazují objektem PSCredential

```powershell
# Old
Set-AzureRmVMAccessExtension [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
Set-AzureRmVMAccessExtension [other required parameters] -Credential $PSCredential
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a>Rozbíjející změny v rutinách EventHub

### <a name="new-azurermeventhubnamespaceauthorizationrule"></a>**New-AzureRmEventHubNamespaceAuthorizationRule**
- Byla odstraněna rutina New-AzureRmEventHubNamespaceAuthorizationRule. Použijte prosím rutinu New-AzureRmEventHubAuthorizationRule
    
### <a name="get-azurermeventhubnamespaceauthorizationrule"></a>**Get-AzureRmEventHubNamespaceAuthorizationRule**
- Byla odstraněna rutina Get-AzureRmEventHubNamespaceAuthorizationRule. Použijte prosím rutinu Get-AzureRmEventHubAuthorizationRule
    
### <a name="set-azurermeventhubnamespaceauthorizationrule"></a>**Set-AzureRmEventHubNamespaceAuthorizationRule**
- Byla odstraněna rutina Set-AzureRmEventHubNamespaceAuthorizationRule. Použijte prosím rutinu Set-AzureRmEventHubAuthorizationRule
    
### <a name="remove-azurermeventhubnamespaceauthorizationrule"></a>**Remove-AzureRmEventHubNamespaceAuthorizationRule**
- Byla odstraněna rutina Remove-AzureRmEventHubNamespaceAuthorizationRule. Použijte prosím rutinu Remove-AzureRmEventHubAuthorizationRule
    
### <a name="new-azurermeventhubnamespacekey"></a>**New-AzureRmEventHubNamespaceKey**
- Byla odstraněna rutina New-AzureRmEventHubNamespaceKey. Použijte prosím rutinu New-AzureRmEventHubKey
    
### <a name="get-azurermeventhubnamespacekey"></a>**Get-AzureRmEventHubNamespaceKey**
- Byla odstraněna rutina Get-AzureRmEventHubNamespaceKey. Použijte prosím rutinu Get-AzureRmEventHubKey
    
### <a name="new-azurermeventhubnamespace"></a>**New-AzureRmEventHubNamespace**
- Budou odebrány vlastnosti Status a Enabled z NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property  
$namespace = New-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Get-AzureRmEventHubNamespace <parameters>
```
    
### <a name="get-azurermeventhubnamespace"></a>**Get-AzureRmEventHubNamespace**
- Budou odebrány vlastnosti Status a Enabled z NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Get-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Get-AzureRmEventHubNamespace <parameters>
```
    
### <a name="set-azurermeventhubnamespace"></a>**Set-AzureRmEventHubNamespace**
- Budou odebrány vlastnosti Status a Enabled z NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Set-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Set-AzureRmEventHubNamespace <parameters>
``` 
  
### <a name="new-azurermeventhubconsumergroup"></a>**New-AzureRmEventHubConsumerGroup**
- Bude odebrána vlastnost EventHubPath z ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="set-azurermeventhubconsumergroup"></a>**Set-AzureRmEventHubConsumerGroup**
- Bude odebrána vlastnost EventHubPath z ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="get-azurermeventhubconsumergroup"></a>**Get-AzureRmEventHubConsumerGroup**
- Bude odebrána vlastnost EventHubPath z ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
```

## <a name="breaking-changes-to-insights-cmdlets"></a>Rozbíjející změny v rutinách Insights

### <a name="add-azurermlogalertrule"></a>**Add-AzureRMLogAlertRule**
- Rutina **Add-AzureRMLogAlertRule** je zastaralá
- Po 1. říjnu už použití této rutiny nebude mít žádný účinek, protože se tato funkce převádí na Upozornění protokolu aktivit. Další informace najdete tady: https://aka.ms/migratemealerts.

### <a name="get-azurermusage"></a>**Get-AzureRMUsage**
- Rutina **Get-AzureRMUsage** je zastaralá

### <a name="get-azurermalerthistory--get-azurermautoscalehistory--get-azurermlogs"></a>**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**
- Změna výstupu: Pole EventChannels z objektu EventData (vraceno těmito rutinami) je nyní zastaralé a vrací konstantu (Admin,Operation).

### <a name="get-azurermalertrule"></a>**Get-AzureRmAlertRule**
- Změna výstup: výstup této rutiny bude zjednodušen, tj. odstraní se pole vlastností, aby se zlepšil uživatelský komfort.

```powershell
# Old
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -Foreground Red "Error updating alert rule"
    Write-Host $rules[0].Id
    Write-Host $rules[0].Properties.IsEnabled
    Write-Host $rules[0].Properties.Condition
}

# New
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -Foreground red "Error updating alert rule"
    Write-Host $rules[0].Id

    # Properties will remain for a while
    Write-Host $rules[0].Properties.IsEnabled
      
    # But the properties will be at the top level too. Later Properties will be removed
    Write-Host $rules[0].IsEnabled
    Write-Host $rules[0].Condition
}
```

### <a name="get-azurermautoscalesetting"></a>**Get-AzureRmAutoscaleSetting**
- Změna výstupu: Pole AutoscaleSettingResourceName bude zastaralé, protože bude vždy rovné poli Název.

```powershell
# Old
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
if ($s1.AutoscaleSettingResourceName -ne $s1.Name)
{
    Write-Host "There is something wrong with the name"
}

# New
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
    
# there won't be a AutoscaleSettingResourceName
Write-Host $s1.Name    
```

### <a name="remove-azurermalertrule--remove-azurermlogprofile"></a>**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**
- Změna výstupu: Typ výstupu se změní na jeden objekt obsahující ID žádosti a stavový kód.

```powershell
# Old
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name $ruleName
if ($s1 -ne $null)
{
    $r = $s1[0].RequestId
    $s = $s1[0].StatusCode
}

# New
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name $ruleName
$r = $s1.RequestId
$s = $s1.StatusCode
```

## <a name="breaking-changes-to-network-cmdlets"></a>Rozbíjející změny v rutinách Network

### <a name="add-azurermapplicationgatewaysslcertificate"></a>**Add-AzureRmApplicationGatewaySslCertificate**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermapplicationgatewaysslcertificate"></a>**New-AzureRmApplicationGatewaySslCertificate**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapplicationgatewaysslcertificate"></a>**Set-AzureRmApplicationGatewaySslCertificate**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-resources-cmdlets"></a>Rozbíjející změny v rutinách Resources

### <a name="new-azurermadappcredential"></a>**New-AzureRmADAppCredential**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
New-AzureRmADAppCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADAppCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadapplication"></a>**New-AzureRmADApplication**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
New-AzureRmADApplication [other required parameters] -Password "plain-text string"

# New
New-AzureRmADApplication [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadserviceprincipal"></a>**New-AzureRmADServicePrincipal**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
New-AzureRmADServicePrincipal [other required parameters] -Password "plain-text string"

# New
New-AzureRmADServicePrincipal [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadspcredential"></a>**New-AzureRmADSpCredential**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
New-AzureRmADSpCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADSpCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermaduser"></a>**New-AzureRmADUser**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
New-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermaduser"></a>**Set-AzureRmADUser**
- Parametr „Password“ se nahrazuje objektem SecureString

```powershell
# Old
Set-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a>Rozbíjející změny v rutinách ServiceBus

### <a name="get-azurermservicebustopicauthorizationrule"></a>**Get-AzureRmServiceBusTopicAuthorizationRule**
- Byla odstraněna rutina Get-AzureRmServiceBusTopicAuthorizationRule. Použijte prosím rutinu Get-AzureRmServiceBusAuthorizationRule.    

### <a name="get-azurermservicebustopickey"></a>**Get-AzureRmServiceBusTopicKey**
- Byla odstraněna rutina Get-AzureRmServiceBusTopicKey. Použijte prosím rutinu Get-AzureRmServiceBusKey.

### <a name="new-azurermservicebustopicauthorizationrule"></a>**New-AzureRmServiceBusTopicAuthorizationRule**
- Byla odstraněna rutina New-AzureRmServiceBusTopicAuthorizationRule. Použijte prosím rutinu New-AzureRmServiceBusAuthorizationRule.

### <a name="new-azurermservicebustopickey"></a>**New-AzureRmServiceBusTopicKey**
- Byla odstraněna rutina New-AzureRmServiceBusTopicKey. Použijte prosím rutinu New-AzureRmServiceBusKey.

### <a name="remove-azurermservicebustopicauthorizationrule"></a>**Remove-AzureRmServiceBusTopicAuthorizationRule**
- Byla odstraněna rutina Remove-AzureRmServiceBusTopicAuthorizationRule. Použijte prosím rutinu Remove-AzureRmServiceBusAuthorizationRule.

### <a name="set-azurermservicebustopicauthorizationrule"></a>**Set-AzureRmServiceBusTopicAuthorizationRule**
- Byla odstraněna rutina Set-AzureRmServiceBusTopicAuthorizationRule. Použijte prosím rutinu Set-AzureRmServiceBusAuthorizationRule.

### <a name="new-azurermservicebusnamespacekey"></a>**New-AzureRmServiceBusNamespaceKey**
- Byla odstraněna rutina New-AzureRmServiceBusNamespaceKey. Použijte prosím rutinu New-AzureRmServiceBusKey.

### <a name="get-azurermservicebusqueueauthorizationrule"></a>**Get-AzureRmServiceBusQueueAuthorizationRule**
- Byla odstraněna rutina Get-AzureRmServiceBusQueueAuthorizationRule. Použijte prosím rutinu Get-AzureRmServiceBusAuthorizationRule.

### <a name="get-azurermservicebusqueuekey"></a>**Get-AzureRmServiceBusQueueKey**
- Byla odstraněna rutina Get-AzureRmServiceBusQueueKey. Použijte prosím rutinu Get-AzureRmServiceBusKey.

### <a name="new-azurermservicebusqueueauthorizationrule"></a>**New-AzureRmServiceBusQueueAuthorizationRule**
- Byla odstraněna rutina New-AzureRmServiceBusQueueAuthorizationRule. Použijte prosím rutinu New-AzureRmServiceBusAuthorizationRule.

### <a name="new-azurermservicebusqueuekey"></a>**New-AzureRmServiceBusQueueKey**
- Byla odstraněna rutina New-AzureRmServiceBusQueueKey. Použijte prosím rutinu New-AzureRmServiceBusKey.

### <a name="remove-azurermservicebusqueueauthorizationrule"></a>**Remove-AzureRmServiceBusQueueAuthorizationRule**
- Byla odstraněna rutina Remove-AzureRmServiceBusQueueAuthorizationRule. Použijte prosím rutinu GRemove-AzureRmServiceBusAuthorizationRule.

### <a name="set-azurermservicebusqueueauthorizationrule"></a>**Set-AzureRmServiceBusQueueAuthorizationRule**
- Byla odstraněna rutina Set-AzureRmServiceBusQueueAuthorizationRule. Použijte prosím rutinu Set-AzureRmServiceBusAuthorizationRule.

### <a name="get-azurermservicebusnamespaceauthorizationrule"></a>**Get-AzureRmServiceBusNamespaceAuthorizationRule**
- Byla odstraněna rutina Get-AzureRmServiceBusNamespaceAuthorizationRule. Použijte prosím rutinu Get-AzureRmServiceBusAuthorizationRule.

### <a name="get-azurermservicebusnamespacekey"></a>**Get-AzureRmServiceBusNamespaceKey**
- Byla odstraněna rutina Get-AzureRmServiceBusNamespaceKey. Použijte prosím rutinu Get-AzureRmServiceBusKey.

### <a name="new-azurermservicebusnamespaceauthorizationrule"></a>**New-AzureRmServiceBusNamespaceAuthorizationRule**
- Byla odstraněna rutina New-AzureRmServiceBusNamespaceAuthorizationRule. Použijte prosím rutinu New-AzureRmServiceBusAuthorizationRule.

### <a name="remove-azurermservicebusnamespaceauthorizationrule"></a>**Remove-AzureRmServiceBusNamespaceAuthorizationRule**
- Byla odstraněna rutina Remove-AzureRmServiceBusNamespaceAuthorizationRule. Použijte prosím rutinu Remove-AzureRmServiceBusAuthorizationRule.

### <a name="set-azurermservicebusnamespaceauthorizationrule"></a>**Set-AzureRmServiceBusNamespaceAuthorizationRule**
- Byla odstraněna rutina Set-AzureRmServiceBusNamespaceAuthorizationRule. Použijte prosím rutinu Set-AzureRmServiceBusAuthorizationRule.

### <a name="type-namespaceattributes"></a>**Typ NamespaceAttributes**
- Byly odstraněny následující vlastnosti
    - Enabled
    - Status
   
```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Get-AzureRmServiceBusNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Enabled and Status properties    
$namespace = Get-AzureRmServiceBusNamespace <parameters>
```

### <a name="type-queueattribute"></a>**Typ QueueAttribute**
- Následující vlastnosti jsou označeny jako zastaralé:
    - EnableBatchedOperations
    - EntityAvailabilityStatus
    - IsAnonymousAccessible
    - SupportOrdering

```powershell
# Old
# The $queue has EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties
$queue = Get-AzureRmServiceBusQueue <parameters>
$queue.EntityAvailabilityStatus
$queue.EnableBatchedOperations
$queue.IsAnonymousAccessible
$queue.SupportOrdering  

# New
# The call remains the same, but the returned values Queue object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$queue = Get-AzureRmServiceBusQueue <parameters>
```
   
### <a name="type-topicattribute"></a>**Typ TopicAttribute**
- Následující vlastnosti jsou označeny jako zastaralé:
    - Location
    - IsExpress
    - IsAnonymousAccessible
    - FilteringMessagesBeforePublishing
    - EnableSubscriptionPartitioning
    - EntityAvailabilityStatus

```powershell
# Old
# The $topic has EntityAvailabilityStatus, EnableSubscriptionPartitioning, IsAnonymousAccessible, IsExpress, Location and FilteringMessagesBeforePublishing properties
$topic = Get-AzureRmServiceBusTopic <parameters>
$topic.EntityAvailabilityStatus
$topic.EnableSubscriptionPartitioning
$topic.IsAnonymousAccessible
$topic.IsExpress
$topic.FilteringMessagesBeforePublishing
$topic.Location

# New
# The call remains the same, but the returned values Topic object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$topic = Get-AzureRmServiceBusTopic <parameters>
```
   
### <a name="type-subscriptionattribute"></a>**Typ SubscriptionAttribute**
- Následující vlastnosti jsou označeny jako zastaralé
    - DeadLetteringOnFilterEvaluationExceptions
    - EntityAvailabilityStatus
    - IsReadOnly
    - Umístění
   
```powershell
# Old
# The $subscription has EntityAvailabilityStatus, EnableSubscriptionPartitioning, IsAnonymousAccessible, IsExpress, Location and FilteringMessagesBeforePublishing properties
$subscription = Get-AzureRmServiceBussubscription <parameters>
$subscription.EntityAvailabilityStatus
$subscription.EnableSubscriptionPartitioning
$subscription.IsAnonymousAccessible
$subscription.IsExpress
$subscription.FilteringMessagesBeforePublishing
$subscription.Location

# New
# The call remains the same, but the returned values Topic object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$subscription = Get-AzureRmServiceBussubscription <parameters>
```