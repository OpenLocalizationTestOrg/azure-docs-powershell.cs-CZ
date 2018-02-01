# <a name="breaking-changes-for-microsoft-azure-powershell-500"></a><span data-ttu-id="a12f7-101">Rozbíjející změny v prostředí Azure PowerShell 5.0.0.x</span><span class="sxs-lookup"><span data-stu-id="a12f7-101">Breaking changes for Microsoft Azure PowerShell 5.0.0</span></span>

<span data-ttu-id="a12f7-102">Tento dokument slouží jednak jako oznámení rozbíjejících změn, a jednak průvodce migrací pro všechny, kteří využívají rutiny prostředí Microsoft Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a12f7-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span> <span data-ttu-id="a12f7-103">Každá část popisuje jak důvody rozbíjející změny, tak i migrační cestu nejmenšího odporu.</span><span class="sxs-lookup"><span data-stu-id="a12f7-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span> <span data-ttu-id="a12f7-104">Podrobný kontext najdete v žádosti o přijetí změn související s každou změnou.</span><span class="sxs-lookup"><span data-stu-id="a12f7-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="a12f7-105">Obsah</span><span class="sxs-lookup"><span data-stu-id="a12f7-105">Table of Contents</span></span>

- [<span data-ttu-id="a12f7-106">Rozbíjející změny v rutinách ApiManagement</span><span class="sxs-lookup"><span data-stu-id="a12f7-106">Breaking changes to ApiManagement cmdlets</span></span>](#breaking-changes-to-apimanagement-cmdlets)
- [<span data-ttu-id="a12f7-107">Rozbíjející změny v rutinách Batch</span><span class="sxs-lookup"><span data-stu-id="a12f7-107">Breaking changes to Batch cmdlets</span></span>](#breaking-changes-to-batch-cmdlets)
- [<span data-ttu-id="a12f7-108">Rozbíjející změny v rutinách Compute</span><span class="sxs-lookup"><span data-stu-id="a12f7-108">Breaking changes to Compute cmdlets</span></span>](#breaking-changes-to-compute-cmdlets)
- [<span data-ttu-id="a12f7-109">Rozbíjející změny v rutinách EventHub</span><span class="sxs-lookup"><span data-stu-id="a12f7-109">Breaking changes to EventHub cmdlets</span></span>](#breaking-changes-to-eventhub-cmdlets)
- [<span data-ttu-id="a12f7-110">Rozbíjející změny v rutinách Insights</span><span class="sxs-lookup"><span data-stu-id="a12f7-110">Breaking changes to Insights cmdlets</span></span>](#breaking-changes-to-insights-cmdlets)
- [<span data-ttu-id="a12f7-111">Rozbíjející změny v rutinách Network</span><span class="sxs-lookup"><span data-stu-id="a12f7-111">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)
- [<span data-ttu-id="a12f7-112">Rozbíjející změny v rutinách Resources</span><span class="sxs-lookup"><span data-stu-id="a12f7-112">Breaking changes to Resources cmdlets</span></span>](#breaking-changes-to-resources-cmdlets)
- [<span data-ttu-id="a12f7-113">Rozbíjející změny v rutinách ServiceBus</span><span class="sxs-lookup"><span data-stu-id="a12f7-113">Breaking Changes to ServiceBus Cmdlets</span></span>](#breaking-changes-to-servicebus-cmdlets)

## <a name="breaking-changes-to-apimanagement-cmdlets"></a><span data-ttu-id="a12f7-114">Rozbíjející změny v rutinách ApiManagement</span><span class="sxs-lookup"><span data-stu-id="a12f7-114">Breaking changes to ApiManagement cmdlets</span></span>

### <a name="new-azurermapimanagementbackendproxy"></a><span data-ttu-id="a12f7-115">**New-AzureRmApiManagementBackendProxy**</span><span class="sxs-lookup"><span data-stu-id="a12f7-115">**New-AzureRmApiManagementBackendProxy**</span></span>
- <span data-ttu-id="a12f7-116">Parametry „UserName“ a „Password“ se nahrazují objektem PSCredential</span><span class="sxs-lookup"><span data-stu-id="a12f7-116">Parameters "UserName" and "Password" are being replaced in favor of a PSCredential</span></span>

```powershell
# Old
New-AzureRmApiManagementBackendProxy [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
New-AzureRmApiManagementBackendProxy [other required parameters] -Credential $PSCredentialVariable
```

### <a name="new-azurermapimanagementuser"></a><span data-ttu-id="a12f7-117">**New-AzureRmApiManagementUser**</span><span class="sxs-lookup"><span data-stu-id="a12f7-117">**New-AzureRmApiManagementUser**</span></span>
- <span data-ttu-id="a12f7-118">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-118">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapimanagementuser"></a><span data-ttu-id="a12f7-119">**Set-AzureRmApiManagementUser**</span><span class="sxs-lookup"><span data-stu-id="a12f7-119">**Set-AzureRmApiManagementUser**</span></span>
- <span data-ttu-id="a12f7-120">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-120">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-batch-cmdlets"></a><span data-ttu-id="a12f7-121">Rozbíjející změny v rutinách Batch</span><span class="sxs-lookup"><span data-stu-id="a12f7-121">Breaking changes to Batch cmdlets</span></span>

### <a name="new-azurebatchcertificate"></a><span data-ttu-id="a12f7-122">**New-AzureBatchCertificate**</span><span class="sxs-lookup"><span data-stu-id="a12f7-122">**New-AzureBatchCertificate**</span></span>
- <span data-ttu-id="a12f7-123">Parametr `Password` se nahrazuje řetězcem Secure</span><span class="sxs-lookup"><span data-stu-id="a12f7-123">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
New-AzureBatchCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureBatchCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchcomputenodeuser"></a><span data-ttu-id="a12f7-124">**New-AzureBatchComputeNodeUser**</span><span class="sxs-lookup"><span data-stu-id="a12f7-124">**New-AzureBatchComputeNodeUser**</span></span>
- <span data-ttu-id="a12f7-125">Parametr `Password` se nahrazuje řetězcem Secure</span><span class="sxs-lookup"><span data-stu-id="a12f7-125">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
New-AzureBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
New-AzureBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermbatchcomputenodeuser"></a><span data-ttu-id="a12f7-126">**Set-AzureRmBatchComputeNodeUser**</span><span class="sxs-lookup"><span data-stu-id="a12f7-126">**Set-AzureRmBatchComputeNodeUser**</span></span>
- <span data-ttu-id="a12f7-127">Parametr `Password` se nahrazuje řetězcem Secure</span><span class="sxs-lookup"><span data-stu-id="a12f7-127">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchtask"></a><span data-ttu-id="a12f7-128">**New-AzureBatchTask**</span><span class="sxs-lookup"><span data-stu-id="a12f7-128">**New-AzureBatchTask**</span></span>
 - <span data-ttu-id="a12f7-129">Odstranění přepínače `RunElevated` a jeho nahrazení přepínačem `UserIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-129">Removed the `RunElevated` switch and replaced it with `UserIdentity`.</span></span>

```powershell
# Old
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -RunElevated $TRUE

# New
$autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Task", "Admin")
$userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -UserIdentity $userIdentity
```

<span data-ttu-id="a12f7-130">To ovlivní navíc vlastnost `RunElevated` u rutin `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` a `PSJobReleaseTask`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-130">This additionally impacts the `RunElevated` property on `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask`, and `PSJobReleaseTask`.</span></span>

### <a name="psmultiinstancesettings"></a><span data-ttu-id="a12f7-131">**PSMultiInstanceSettings**</span><span class="sxs-lookup"><span data-stu-id="a12f7-131">**PSMultiInstanceSettings**</span></span>

- <span data-ttu-id="a12f7-132">Konstruktor `PSMultiInstanceSettings` už nepřijímá vyžadovaný parametr `numberOfInstances`, místo toho vyžaduje parametr `coordinationCommandLine`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-132">`PSMultiInstanceSettings` constructor no longer takes a required `numberOfInstances` parameter, instead it takes a required `coordinationCommandLine` parameter.</span></span>

```powershell
# Old
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @(2)
$settings.CoordinationCommandLine = "cmd /c echo hello"
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings

# New
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @("cmd /c echo hello", 2)
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings
```

### <a name="get-azurebatchtask"></a><span data-ttu-id="a12f7-133">**Get-AzureBatchTask**</span><span class="sxs-lookup"><span data-stu-id="a12f7-133">**Get-AzureBatchTask**</span></span>
 - <span data-ttu-id="a12f7-134">Byla odebrána vlastnost `RunElevated` u `PSCloudTask`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-134">Removed the `RunElevated` property on `PSCloudTask`.</span></span> <span data-ttu-id="a12f7-135">Byla přidána vlastnost `UserIdentity` nahrazující `RunElevated`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-135">The `UserIdentity` property has been added to replace `RunElevated`.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.RunElevated

# New
$task = Get-AzureBatchTask [parameters]
$task.UserIdentity.AutoUser.ElevationLevel
```

<span data-ttu-id="a12f7-136">To ovlivní navíc vlastnost `RunElevated` u rutin `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` a `PSJobReleaseTask`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-136">This additionally impacts the `RunElevated` property on `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask`, and `PSJobReleaseTask`.</span></span>

### <a name="multiple-types"></a><span data-ttu-id="a12f7-137">**Několik typů**</span><span class="sxs-lookup"><span data-stu-id="a12f7-137">**Multiple types**</span></span>

- <span data-ttu-id="a12f7-138">Byla přejmenována vlastnost `SchedulingError` u `PSExitConditions` na `PreProcessingError`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-138">Renamed the `SchedulingError` property on `PSExitConditions` to `PreProcessingError`.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.PreProcessingError
```

### <a name="multiple-types"></a><span data-ttu-id="a12f7-139">**Několik typů**</span><span class="sxs-lookup"><span data-stu-id="a12f7-139">**Multiple types**</span></span>

- <span data-ttu-id="a12f7-140">Byla přejmenována vlastnost `SchedulingError` u `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation` a `PSTaskExecutionInformation` na `FailureInformation`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-140">Renamed the `SchedulingError` property on `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation`, and `PSTaskExecutionInformation` to `FailureInformation`.</span></span>
  - <span data-ttu-id="a12f7-141">Vrací se `FailureInformation`, kdykoli dojde k selhání úlohy.</span><span class="sxs-lookup"><span data-stu-id="a12f7-141">`FailureInformation` is returned any time there is a task failure.</span></span> <span data-ttu-id="a12f7-142">To zahrnuje všechny předchozí případy chyb plánu, stejně jako nenulové ukončovací kódy úloh a selhání nahrávání souborů z nové funkce pro výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="a12f7-142">This includes all previous scheduling error cases, as well as nonzero task exit codes, and file upload failures from the new output files feature.</span></span>
  - <span data-ttu-id="a12f7-143">Struktura je stejná jako předtím, při použití tohoto typu tedy není nutná změna programu.</span><span class="sxs-lookup"><span data-stu-id="a12f7-143">This is structured the same as before, so no code change is needed when using this type.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.FailureInformation
```

<span data-ttu-id="a12f7-144">To ovlivňuje také: Get-AzureBatchPool, Get-AzureBatchSubtask a Get-AzureBatchJobPreparationAndReleaseTaskStatus</span><span class="sxs-lookup"><span data-stu-id="a12f7-144">This additionally impacts: Get-AzureBatchPool, Get-AzureBatchSubtask, and Get-AzureBatchJobPreparationAndReleaseTaskStatus</span></span>

### <a name="new-azurebatchpool"></a><span data-ttu-id="a12f7-145">**New-AzureBatchPool**</span><span class="sxs-lookup"><span data-stu-id="a12f7-145">**New-AzureBatchPool**</span></span>
 - <span data-ttu-id="a12f7-146">Odstranění přepínače `TargetDedicated` a jeho nahrazení přepínači `TargetDedicatedComputeNodes` a `TargetLowPriorityComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-146">Removed `TargetDedicated` and replaced it with `TargetDedicatedComputeNodes` and `TargetLowPriorityComputeNodes`.</span></span>
 - <span data-ttu-id="a12f7-147">`TargetDedicatedComputeNodes` má nový alias `TargetDedicated`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-147">`TargetDedicatedComputeNodes` has an alias `TargetDedicated`.</span></span>

```powershell
# Old
New-AzureBatchPool [other parameters] [-TargetDedicated <Int32>]

# New
New-AzureBatchPool [other parameters] [-TargetDedicatedComputeNodes <Int32>] [-TargetLowPriorityComputeNodes <Int32>]
```

<span data-ttu-id="a12f7-148">To ovlivňuje také: Start-AzureBatchPoolResize</span><span class="sxs-lookup"><span data-stu-id="a12f7-148">This also impacts: Start-AzureBatchPoolResize</span></span>

### <a name="get-azurebatchpool"></a><span data-ttu-id="a12f7-149">**Get-AzureBatchPool**</span><span class="sxs-lookup"><span data-stu-id="a12f7-149">**Get-AzureBatchPool**</span></span>
 - <span data-ttu-id="a12f7-150">Přejmenovány vlastnosti `TargetDedicated` a `CurrentDedicated` vlastnosti u `PSCloudPool` na `TargetDedicatedComputeNodes` a `CurrentDedicatedComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-150">Renamed the `TargetDedicated` and `CurrentDedicated` properties on `PSCloudPool` to `TargetDedicatedComputeNodes` and `CurrentDedicatedComputeNodes`.</span></span>

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

### <a name="type-pscloudpool"></a><span data-ttu-id="a12f7-151">**Typ PSCloudPool**</span><span class="sxs-lookup"><span data-stu-id="a12f7-151">**Type PSCloudPool**</span></span>

- <span data-ttu-id="a12f7-152">Přejmenováno `ResizeError` na `ResizeErrors` u `PSCloudPool`, nyní jde o kolekci.</span><span class="sxs-lookup"><span data-stu-id="a12f7-152">Renamed `ResizeError` to `ResizeErrors` on `PSCloudPool`, and it is now a collection.</span></span>

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeError

# New
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeErrors[0]
```

### <a name="new-azurebatchjob"></a><span data-ttu-id="a12f7-153">**New-AzureBatchJob**</span><span class="sxs-lookup"><span data-stu-id="a12f7-153">**New-AzureBatchJob**</span></span>
- <span data-ttu-id="a12f7-154">Byla přejmenována vlastnost `TargetDedicated` u `PSPoolSpecification` na `TargetDedicatedComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-154">Renamed the `TargetDedicated` property on `PSPoolSpecification` to `TargetDedicatedComputeNodes`.</span></span>

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

### <a name="get-azurebatchnodefile"></a><span data-ttu-id="a12f7-155">**Get-AzureBatchNodeFile**</span><span class="sxs-lookup"><span data-stu-id="a12f7-155">**Get-AzureBatchNodeFile**</span></span>
 - <span data-ttu-id="a12f7-156">Odstraněn přepínač `Name`, nahrazuje ho `Path`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-156">Removed `Name` and replaced it with `Path`.</span></span>
 - <span data-ttu-id="a12f7-157">`Path` má nový alias `Name`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-157">`Path` has an alias `Name`.</span></span>

```powershell
# Old
Get-AzureBatchNodeFile [other parameters] [[-Name] <String>]

# New
Get-AzureBatchNodeFile [other parameters] [[-Path] <String>]
```

<span data-ttu-id="a12f7-158">To ovlivňuje také: Get-AzureBatchNodeFileContent a Remove-AzureBatchNodeFile</span><span class="sxs-lookup"><span data-stu-id="a12f7-158">This also impacts: Get-AzureBatchNodeFileContent, Remove-AzureBatchNodeFile</span></span>

### <a name="type-psnodefile"></a><span data-ttu-id="a12f7-159">Typ **PSNodeFile**</span><span class="sxs-lookup"><span data-stu-id="a12f7-159">Type **PSNodeFile**</span></span>

 - <span data-ttu-id="a12f7-160">Byla přejmenována vlastnost `Name` u `PSNodeFile` na `Path`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-160">Renamed the `Name` property on `PSNodeFile` to `Path`.</span></span>

```powershell
# Old
$file = Get-AzureBatchNodeFile [parameters]
$file.Name

# New
$file = Get-AzureBatchNodeFile [parameters]
$file.Path
```

### <a name="get-azurebatchsubtask"></a><span data-ttu-id="a12f7-161">**Get-AzureBatchSubtask**</span><span class="sxs-lookup"><span data-stu-id="a12f7-161">**Get-AzureBatchSubtask**</span></span>
- <span data-ttu-id="a12f7-162">Vlastnosti `PreviousState` a `State` u `PSSubtaskInformation` již nejsou typu `TaskState`, místo toho jsou typu `SubtaskState`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-162">The `PreviousState` and `State` properties of `PSSubtaskInformation` are no longer of type `TaskState`, instead they are of type `SubtaskState`.</span></span>
  - <span data-ttu-id="a12f7-163">Na rozdíl od `TaskState`, `SubtaskState` nemá žádnou hodnotu `Active`, protože není možné, aby pro dílčí úkoly byly ve stavu `Active`.</span><span class="sxs-lookup"><span data-stu-id="a12f7-163">Unlike `TaskState`, `SubtaskState` has no `Active` value, since it is not possible for subtasks to be in an `Active` state.</span></span>

```powershell
# Old
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.TaskState.Running) { }

# New
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.SubtaskState.Running) { }
```

## <a name="breaking-changes-to-compute-cmdlets"></a><span data-ttu-id="a12f7-164">Rozbíjející změny v rutinách Compute</span><span class="sxs-lookup"><span data-stu-id="a12f7-164">Breaking changes to Compute cmdlets</span></span>

### <a name="set-azurermvmaccessextension"></a><span data-ttu-id="a12f7-165">**Set-AzureRmVMAccessExtension**</span><span class="sxs-lookup"><span data-stu-id="a12f7-165">**Set-AzureRmVMAccessExtension**</span></span>
- <span data-ttu-id="a12f7-166">Parametry „UserName“ a „Password“ se nahrazují objektem PSCredential</span><span class="sxs-lookup"><span data-stu-id="a12f7-166">Parameters "UserName" and "Password" are being replaced in favor of a PSCredential</span></span>

```powershell
# Old
Set-AzureRmVMAccessExtension [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
Set-AzureRmVMAccessExtension [other required parameters] -Credential $PSCredential
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a><span data-ttu-id="a12f7-167">Rozbíjející změny v rutinách EventHub</span><span class="sxs-lookup"><span data-stu-id="a12f7-167">Breaking changes to EventHub cmdlets</span></span>

### <a name="new-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="a12f7-168">**New-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-168">**New-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-169">Byla odstraněna rutina New-AzureRmEventHubNamespaceAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-169">The 'New-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-170">Použijte prosím rutinu New-AzureRmEventHubAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a12f7-170">Please use the 'New-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="get-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="a12f7-171">**Get-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-171">**Get-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-172">Byla odstraněna rutina Get-AzureRmEventHubNamespaceAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-172">The 'Get-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-173">Použijte prosím rutinu Get-AzureRmEventHubAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a12f7-173">Please use the 'Get-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="set-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="a12f7-174">**Set-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-174">**Set-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-175">Byla odstraněna rutina Set-AzureRmEventHubNamespaceAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-175">The 'Set-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-176">Použijte prosím rutinu Set-AzureRmEventHubAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a12f7-176">Please use the 'Set-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="remove-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="a12f7-177">**Remove-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-177">**Remove-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-178">Byla odstraněna rutina Remove-AzureRmEventHubNamespaceAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-178">The 'Remove-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-179">Použijte prosím rutinu Remove-AzureRmEventHubAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a12f7-179">Please use the 'Remove-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="new-azurermeventhubnamespacekey"></a><span data-ttu-id="a12f7-180">**New-AzureRmEventHubNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="a12f7-180">**New-AzureRmEventHubNamespaceKey**</span></span>
- <span data-ttu-id="a12f7-181">Byla odstraněna rutina New-AzureRmEventHubNamespaceKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-181">The 'New-AzureRmEventHubNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-182">Použijte prosím rutinu New-AzureRmEventHubKey</span><span class="sxs-lookup"><span data-stu-id="a12f7-182">Please use the 'New-AzureRmEventHubKey' cmdlet</span></span>
    
### <a name="get-azurermeventhubnamespacekey"></a><span data-ttu-id="a12f7-183">**Get-AzureRmEventHubNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="a12f7-183">**Get-AzureRmEventHubNamespaceKey**</span></span>
- <span data-ttu-id="a12f7-184">Byla odstraněna rutina Get-AzureRmEventHubNamespaceKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-184">The 'Get-AzureRmEventHubNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-185">Použijte prosím rutinu Get-AzureRmEventHubKey</span><span class="sxs-lookup"><span data-stu-id="a12f7-185">Please use the 'Get-AzureRmEventHubKey' cmdlet</span></span>
    
### <a name="new-azurermeventhubnamespace"></a><span data-ttu-id="a12f7-186">**New-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="a12f7-186">**New-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="a12f7-187">Budou odebrány vlastnosti Status a Enabled z NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="a12f7-187">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
    
### <a name="get-azurermeventhubnamespace"></a><span data-ttu-id="a12f7-188">**Get-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="a12f7-188">**Get-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="a12f7-189">Budou odebrány vlastnosti Status a Enabled z NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="a12f7-189">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
    
### <a name="set-azurermeventhubnamespace"></a><span data-ttu-id="a12f7-190">**Set-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="a12f7-190">**Set-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="a12f7-191">Budou odebrány vlastnosti Status a Enabled z NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="a12f7-191">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
  
### <a name="new-azurermeventhubconsumergroup"></a><span data-ttu-id="a12f7-192">**New-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="a12f7-192">**New-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="a12f7-193">Bude odebrána vlastnost EventHubPath z ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="a12f7-193">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="set-azurermeventhubconsumergroup"></a><span data-ttu-id="a12f7-194">**Set-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="a12f7-194">**Set-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="a12f7-195">Bude odebrána vlastnost EventHubPath z ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="a12f7-195">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="get-azurermeventhubconsumergroup"></a><span data-ttu-id="a12f7-196">**Get-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="a12f7-196">**Get-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="a12f7-197">Bude odebrána vlastnost EventHubPath z ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="a12f7-197">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
```

## <a name="breaking-changes-to-insights-cmdlets"></a><span data-ttu-id="a12f7-198">Rozbíjející změny v rutinách Insights</span><span class="sxs-lookup"><span data-stu-id="a12f7-198">Breaking changes to Insights cmdlets</span></span>

### <a name="add-azurermlogalertrule"></a><span data-ttu-id="a12f7-199">**Add-AzureRMLogAlertRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-199">**Add-AzureRMLogAlertRule**</span></span>
- <span data-ttu-id="a12f7-200">Rutina **Add-AzureRMLogAlertRule** je zastaralá</span><span class="sxs-lookup"><span data-stu-id="a12f7-200">The **Add-AzureRMLogAlertRule** cmdlet has been deprecated</span></span>
- <span data-ttu-id="a12f7-201">Po 1. říjnu už použití této rutiny nebude mít žádný účinek, protože se tato funkce převádí na Upozornění protokolu aktivit.</span><span class="sxs-lookup"><span data-stu-id="a12f7-201">After October 1st using this cmdlet will no longer have any effect as this functionality is being transitioned to Activity Log Alerts.</span></span> <span data-ttu-id="a12f7-202">Další informace najdete tady: https://aka.ms/migratemealerts.</span><span class="sxs-lookup"><span data-stu-id="a12f7-202">Please see https://aka.ms/migratemealerts for more information.</span></span>

### <a name="get-azurermusage"></a><span data-ttu-id="a12f7-203">**Get-AzureRMUsage**</span><span class="sxs-lookup"><span data-stu-id="a12f7-203">**Get-AzureRMUsage**</span></span>
- <span data-ttu-id="a12f7-204">Rutina **Get-AzureRMUsage** je zastaralá</span><span class="sxs-lookup"><span data-stu-id="a12f7-204">The **Get-AzureRMUsage** cmdlet has been deprecated</span></span>

### <a name="get-azurermalerthistory--get-azurermautoscalehistory--get-azurermlogs"></a><span data-ttu-id="a12f7-205">**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**</span><span class="sxs-lookup"><span data-stu-id="a12f7-205">**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**</span></span>
- <span data-ttu-id="a12f7-206">Změna výstupu: Pole EventChannels z objektu EventData (vraceno těmito rutinami) je nyní zastaralé a vrací konstantu (Admin,Operation).</span><span class="sxs-lookup"><span data-stu-id="a12f7-206">Output change: The field EventChannels from the EventData object (returned by these cmdlets) is being deprecated since it now returns a constant value (Admin,Operation.)</span></span>

### <a name="get-azurermalertrule"></a><span data-ttu-id="a12f7-207">**Get-AzureRmAlertRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-207">**Get-AzureRmAlertRule**</span></span>
- <span data-ttu-id="a12f7-208">Změna výstup: výstup této rutiny bude zjednodušen, tj. odstraní se pole vlastností, aby se zlepšil uživatelský komfort.</span><span class="sxs-lookup"><span data-stu-id="a12f7-208">Output change: The output of this cmdlet will be flattened, i.e. elimination of the properties field, to improve the user experience.</span></span>

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

### <a name="get-azurermautoscalesetting"></a><span data-ttu-id="a12f7-209">**Get-AzureRmAutoscaleSetting**</span><span class="sxs-lookup"><span data-stu-id="a12f7-209">**Get-AzureRmAutoscaleSetting**</span></span>
- <span data-ttu-id="a12f7-210">Změna výstupu: Pole AutoscaleSettingResourceName bude zastaralé, protože bude vždy rovné poli Název.</span><span class="sxs-lookup"><span data-stu-id="a12f7-210">Output change: The AutoscaleSettingResourceName field will be deprecated since it always equals the Name field.</span></span>

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

### <a name="remove-azurermalertrule--remove-azurermlogprofile"></a><span data-ttu-id="a12f7-211">**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**</span><span class="sxs-lookup"><span data-stu-id="a12f7-211">**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**</span></span>
- <span data-ttu-id="a12f7-212">Změna výstupu: Typ výstupu se změní na jeden objekt obsahující ID žádosti a stavový kód.</span><span class="sxs-lookup"><span data-stu-id="a12f7-212">Output change: The type of the output will change to return a single object containing the request Id and the status code.</span></span>

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

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="a12f7-213">Rozbíjející změny v rutinách Network</span><span class="sxs-lookup"><span data-stu-id="a12f7-213">Breaking changes to Network cmdlets</span></span>

### <a name="add-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="a12f7-214">**Add-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="a12f7-214">**Add-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="a12f7-215">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-215">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="a12f7-216">**New-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="a12f7-216">**New-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="a12f7-217">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-217">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="a12f7-218">**Set-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="a12f7-218">**Set-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="a12f7-219">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-219">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-resources-cmdlets"></a><span data-ttu-id="a12f7-220">Rozbíjející změny v rutinách Resources</span><span class="sxs-lookup"><span data-stu-id="a12f7-220">Breaking changes to Resources cmdlets</span></span>

### <a name="new-azurermadappcredential"></a><span data-ttu-id="a12f7-221">**New-AzureRmADAppCredential**</span><span class="sxs-lookup"><span data-stu-id="a12f7-221">**New-AzureRmADAppCredential**</span></span>
- <span data-ttu-id="a12f7-222">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-222">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADAppCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADAppCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadapplication"></a><span data-ttu-id="a12f7-223">**New-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="a12f7-223">**New-AzureRmADApplication**</span></span>
- <span data-ttu-id="a12f7-224">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-224">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADApplication [other required parameters] -Password "plain-text string"

# New
New-AzureRmADApplication [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadserviceprincipal"></a><span data-ttu-id="a12f7-225">**New-AzureRmADServicePrincipal**</span><span class="sxs-lookup"><span data-stu-id="a12f7-225">**New-AzureRmADServicePrincipal**</span></span>
- <span data-ttu-id="a12f7-226">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-226">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADServicePrincipal [other required parameters] -Password "plain-text string"

# New
New-AzureRmADServicePrincipal [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadspcredential"></a><span data-ttu-id="a12f7-227">**New-AzureRmADSpCredential**</span><span class="sxs-lookup"><span data-stu-id="a12f7-227">**New-AzureRmADSpCredential**</span></span>
- <span data-ttu-id="a12f7-228">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-228">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADSpCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADSpCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermaduser"></a><span data-ttu-id="a12f7-229">**New-AzureRmADUser**</span><span class="sxs-lookup"><span data-stu-id="a12f7-229">**New-AzureRmADUser**</span></span>
- <span data-ttu-id="a12f7-230">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-230">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermaduser"></a><span data-ttu-id="a12f7-231">**Set-AzureRmADUser**</span><span class="sxs-lookup"><span data-stu-id="a12f7-231">**Set-AzureRmADUser**</span></span>
- <span data-ttu-id="a12f7-232">Parametr „Password“ se nahrazuje objektem SecureString</span><span class="sxs-lookup"><span data-stu-id="a12f7-232">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a><span data-ttu-id="a12f7-233">Rozbíjející změny v rutinách ServiceBus</span><span class="sxs-lookup"><span data-stu-id="a12f7-233">Breaking changes to ServiceBus cmdlets</span></span>

### <a name="get-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="a12f7-234">**Get-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-234">**Get-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-235">Byla odstraněna rutina Get-AzureRmServiceBusTopicAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-235">The 'Get-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-236">Použijte prosím rutinu Get-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-236">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>    

### <a name="get-azurermservicebustopickey"></a><span data-ttu-id="a12f7-237">**Get-AzureRmServiceBusTopicKey**</span><span class="sxs-lookup"><span data-stu-id="a12f7-237">**Get-AzureRmServiceBusTopicKey**</span></span>
- <span data-ttu-id="a12f7-238">Byla odstraněna rutina Get-AzureRmServiceBusTopicKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-238">The 'Get-AzureRmServiceBusTopicKey' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-239">Použijte prosím rutinu Get-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-239">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="a12f7-240">**New-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-240">**New-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-241">Byla odstraněna rutina New-AzureRmServiceBusTopicAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-241">The 'New-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-242">Použijte prosím rutinu New-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-242">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="new-azurermservicebustopickey"></a><span data-ttu-id="a12f7-243">**New-AzureRmServiceBusTopicKey**</span><span class="sxs-lookup"><span data-stu-id="a12f7-243">**New-AzureRmServiceBusTopicKey**</span></span>
- <span data-ttu-id="a12f7-244">Byla odstraněna rutina New-AzureRmServiceBusTopicKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-244">The 'New-AzureRmServiceBusTopicKey' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-245">Použijte prosím rutinu New-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-245">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="remove-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="a12f7-246">**Remove-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-246">**Remove-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-247">Byla odstraněna rutina Remove-AzureRmServiceBusTopicAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-247">The 'Remove-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-248">Použijte prosím rutinu Remove-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-248">Please use the 'Remove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="a12f7-249">**Set-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-249">**Set-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-250">Byla odstraněna rutina Set-AzureRmServiceBusTopicAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-250">The 'Set-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-251">Použijte prosím rutinu Set-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-251">Please use the 'Set-AzureRmServiceBusAuthorizationRule'cmdlet.</span></span>

### <a name="new-azurermservicebusnamespacekey"></a><span data-ttu-id="a12f7-252">**New-AzureRmServiceBusNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="a12f7-252">**New-AzureRmServiceBusNamespaceKey**</span></span>
- <span data-ttu-id="a12f7-253">Byla odstraněna rutina New-AzureRmServiceBusNamespaceKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-253">The 'New-AzureRmServiceBusNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-254">Použijte prosím rutinu New-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-254">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="get-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="a12f7-255">**Get-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-255">**Get-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-256">Byla odstraněna rutina Get-AzureRmServiceBusQueueAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-256">The 'Get-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-257">Použijte prosím rutinu Get-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-257">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusqueuekey"></a><span data-ttu-id="a12f7-258">**Get-AzureRmServiceBusQueueKey**</span><span class="sxs-lookup"><span data-stu-id="a12f7-258">**Get-AzureRmServiceBusQueueKey**</span></span>
- <span data-ttu-id="a12f7-259">Byla odstraněna rutina Get-AzureRmServiceBusQueueKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-259">The 'Get-AzureRmServiceBusQueueKey' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-260">Použijte prosím rutinu Get-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-260">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="a12f7-261">**New-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-261">**New-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-262">Byla odstraněna rutina New-AzureRmServiceBusQueueAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-262">The 'New-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-263">Použijte prosím rutinu New-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-263">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="new-azurermservicebusqueuekey"></a><span data-ttu-id="a12f7-264">**New-AzureRmServiceBusQueueKey**</span><span class="sxs-lookup"><span data-stu-id="a12f7-264">**New-AzureRmServiceBusQueueKey**</span></span>
- <span data-ttu-id="a12f7-265">Byla odstraněna rutina New-AzureRmServiceBusQueueKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-265">The 'New-AzureRmServiceBusQueueKey' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-266">Použijte prosím rutinu New-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-266">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="remove-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="a12f7-267">**Remove-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-267">**Remove-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-268">Byla odstraněna rutina Remove-AzureRmServiceBusQueueAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-268">The 'Remove-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-269">Použijte prosím rutinu GRemove-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-269">Please use the 'GRemove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="a12f7-270">**Set-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-270">**Set-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-271">Byla odstraněna rutina Set-AzureRmServiceBusQueueAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-271">The 'Set-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-272">Použijte prosím rutinu Set-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-272">Please use the 'Set-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="a12f7-273">**Get-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-273">**Get-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-274">Byla odstraněna rutina Get-AzureRmServiceBusNamespaceAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-274">The 'Get-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-275">Použijte prosím rutinu Get-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-275">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusnamespacekey"></a><span data-ttu-id="a12f7-276">**Get-AzureRmServiceBusNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="a12f7-276">**Get-AzureRmServiceBusNamespaceKey**</span></span>
- <span data-ttu-id="a12f7-277">Byla odstraněna rutina Get-AzureRmServiceBusNamespaceKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-277">The 'Get-AzureRmServiceBusNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-278">Použijte prosím rutinu Get-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="a12f7-278">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="a12f7-279">**New-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-279">**New-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-280">Byla odstraněna rutina New-AzureRmServiceBusNamespaceAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-280">The 'New-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-281">Použijte prosím rutinu New-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-281">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="remove-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="a12f7-282">**Remove-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-282">**Remove-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-283">Byla odstraněna rutina Remove-AzureRmServiceBusNamespaceAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-283">The 'Remove-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-284">Použijte prosím rutinu Remove-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-284">Please use the 'Remove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="a12f7-285">**Set-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="a12f7-285">**Set-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="a12f7-286">Byla odstraněna rutina Set-AzureRmServiceBusNamespaceAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-286">The 'Set-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="a12f7-287">Použijte prosím rutinu Set-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="a12f7-287">Please use the 'Set-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="type-namespaceattributes"></a><span data-ttu-id="a12f7-288">**Typ NamespaceAttributes**</span><span class="sxs-lookup"><span data-stu-id="a12f7-288">**Type NamespaceAttributes**</span></span>
- <span data-ttu-id="a12f7-289">Byly odstraněny následující vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a12f7-289">The following properties have been removed</span></span>
    - <span data-ttu-id="a12f7-290">Povoleno</span><span class="sxs-lookup"><span data-stu-id="a12f7-290">Enabled</span></span>
    - <span data-ttu-id="a12f7-291">Status</span><span class="sxs-lookup"><span data-stu-id="a12f7-291">Status</span></span>
   
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

### <a name="type-queueattribute"></a><span data-ttu-id="a12f7-292">**Typ QueueAttribute**</span><span class="sxs-lookup"><span data-stu-id="a12f7-292">**Type QueueAttribute**</span></span>
- <span data-ttu-id="a12f7-293">Následující vlastnosti jsou označeny jako zastaralé:</span><span class="sxs-lookup"><span data-stu-id="a12f7-293">The following properties are marked as obsolete:</span></span>
    - <span data-ttu-id="a12f7-294">EnableBatchedOperations</span><span class="sxs-lookup"><span data-stu-id="a12f7-294">EnableBatchedOperations</span></span>
    - <span data-ttu-id="a12f7-295">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="a12f7-295">EntityAvailabilityStatus</span></span>
    - <span data-ttu-id="a12f7-296">IsAnonymousAccessible</span><span class="sxs-lookup"><span data-stu-id="a12f7-296">IsAnonymousAccessible</span></span>
    - <span data-ttu-id="a12f7-297">SupportOrdering</span><span class="sxs-lookup"><span data-stu-id="a12f7-297">SupportOrdering</span></span>

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
   
### <a name="type-topicattribute"></a><span data-ttu-id="a12f7-298">**Typ TopicAttribute**</span><span class="sxs-lookup"><span data-stu-id="a12f7-298">**Type TopicAttribute**</span></span>
- <span data-ttu-id="a12f7-299">Následující vlastnosti jsou označeny jako zastaralé:</span><span class="sxs-lookup"><span data-stu-id="a12f7-299">The following properties are marked as obsolete:</span></span>
    - <span data-ttu-id="a12f7-300">Umístění</span><span class="sxs-lookup"><span data-stu-id="a12f7-300">Location</span></span>
    - <span data-ttu-id="a12f7-301">IsExpress</span><span class="sxs-lookup"><span data-stu-id="a12f7-301">IsExpress</span></span>
    - <span data-ttu-id="a12f7-302">IsAnonymousAccessible</span><span class="sxs-lookup"><span data-stu-id="a12f7-302">IsAnonymousAccessible</span></span>
    - <span data-ttu-id="a12f7-303">FilteringMessagesBeforePublishing</span><span class="sxs-lookup"><span data-stu-id="a12f7-303">FilteringMessagesBeforePublishing</span></span>
    - <span data-ttu-id="a12f7-304">EnableSubscriptionPartitioning</span><span class="sxs-lookup"><span data-stu-id="a12f7-304">EnableSubscriptionPartitioning</span></span>
    - <span data-ttu-id="a12f7-305">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="a12f7-305">EntityAvailabilityStatus</span></span>

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
   
### <a name="type-subscriptionattribute"></a><span data-ttu-id="a12f7-306">**Typ SubscriptionAttribute**</span><span class="sxs-lookup"><span data-stu-id="a12f7-306">**Type SubscriptionAttribute**</span></span>
- <span data-ttu-id="a12f7-307">Následující vlastnosti jsou označeny jako zastaralé</span><span class="sxs-lookup"><span data-stu-id="a12f7-307">The following properties are marked as obsolete</span></span>
    - <span data-ttu-id="a12f7-308">DeadLetteringOnFilterEvaluationExceptions</span><span class="sxs-lookup"><span data-stu-id="a12f7-308">DeadLetteringOnFilterEvaluationExceptions</span></span>
    - <span data-ttu-id="a12f7-309">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="a12f7-309">EntityAvailabilityStatus</span></span>
    - <span data-ttu-id="a12f7-310">IsReadOnly</span><span class="sxs-lookup"><span data-stu-id="a12f7-310">IsReadOnly</span></span>
    - <span data-ttu-id="a12f7-311">Umístění</span><span class="sxs-lookup"><span data-stu-id="a12f7-311">Location</span></span>
   
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