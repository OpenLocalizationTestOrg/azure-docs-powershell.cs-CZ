---
title: Paralelní spouštění rutin s využitím úloh PowerShellu
description: Jak paralelně spouštět rutiny s využitím parametru -AsJob
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 12/11/2017
ms.openlocfilehash: dfc1efa752c9c9fa42ad5904adacd83c2dc333b8
ms.sourcegitcommit: 5f0013981fcea1d689649b9a2b2ffe84ae842e56
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="running-cmdlets-in-parallel-using-powershell-jobs"></a><span data-ttu-id="07d88-103">Paralelní spouštění rutin s využitím úloh PowerShellu</span><span class="sxs-lookup"><span data-stu-id="07d88-103">Running cmdlets in parallel using PowerShell jobs</span></span>

<span data-ttu-id="07d88-104">PowerShell podporuje asynchronní akce s využitím [úloh PowerShellu](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="07d88-104">PowerShell supports asynchronous action with [PowerShell Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>
<span data-ttu-id="07d88-105">Prostředí Azure PowerShell je silně závislé na síťových voláních do Azure (a čeká na ně).</span><span class="sxs-lookup"><span data-stu-id="07d88-105">Azure PowerShell is heavily dependent on making, and waiting for, network calls to Azure.</span></span> <span data-ttu-id="07d88-106">Jako vývojář pravděpodobně často potřebujete provést několik neblokujících volání do Azure ve skriptu nebo vytvářet prostředky Azure v REPL bez blokování aktuální relace.</span><span class="sxs-lookup"><span data-stu-id="07d88-106">As a developer, you may often find yourself looking to make multiple non-blocking calls to Azure in a script, or you may find that you want to create Azure resources in the REPL without blocking the current session.</span></span> <span data-ttu-id="07d88-107">K zajištění těchto potřeb Azure PowerShell poskytuje prvotřídní podporu [úloh PS](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="07d88-107">To address these needs, Azure PowerShell provides first-class [PSJob](/powershell/module/microsoft.powershell.core/about/about_jobs) support.</span></span>

## <a name="context-persistence-and-psjobs"></a><span data-ttu-id="07d88-108">Trvalost kontextu a úlohy PS</span><span class="sxs-lookup"><span data-stu-id="07d88-108">Context Persistence and PSJobs</span></span>

<span data-ttu-id="07d88-109">Úlohy PS běží v samostatných procesech. To znamená, že s úlohami, které vytvoříte, je potřeba správně sdílet informace o připojeních Azure.</span><span class="sxs-lookup"><span data-stu-id="07d88-109">PSJobs are run in separate processes, which means that information about your Azure connection must be properly shared with the jobs you create.</span></span> <span data-ttu-id="07d88-110">Při připojení vašeho účtu Azure k relaci PowerShellu pomocí `Connect-AzureRmAccount` můžete předat úloze kontext.</span><span class="sxs-lookup"><span data-stu-id="07d88-110">Upon connecting your Azure account to your PowerShell session with `Connect-AzureRmAccount`, you can pass the context to a job.</span></span>

```powershell
$creds = Get-Credential
$job = Start-Job { param($context,$vmadmin) New-AzureRmVM -Name MyVm -AzureRmContext $context -Credential $vmadmin} -Arguments (Get-AzureRmContext),$creds
```

<span data-ttu-id="07d88-111">Pokud jste se ale rozhodli kontext automaticky ukládat pomocí `Enable-AzureRmContextAutosave`, bude se automaticky sdílet se všemi úlohami, které vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="07d88-111">However, if you have chosen to have your context automatically saved with `Enable-AzureRmContextAutosave`, the context is automatically shared with any jobs you create.</span></span>

```powershell
Enable-AzureRmContextAutosave
$creds = Get-Credential
$job = Start-Job { param($vmadmin) New-AzureRmVM -Name MyVm -Credential $vmadmin} -Arguments $creds
```

## <a name="automatic-jobs-with--asjob"></a><span data-ttu-id="07d88-112">Automatické úlohy s přepínačem `-AsJob`</span><span class="sxs-lookup"><span data-stu-id="07d88-112">Automatic Jobs with `-AsJob`</span></span>

<span data-ttu-id="07d88-113">Pro usnadnění Azure PowerShell poskytuje přepínač `-AsJob` také u některých dlouho běžících rutin.</span><span class="sxs-lookup"><span data-stu-id="07d88-113">As a convenience, Azure PowerShell also provides an `-AsJob` switch on some long-running cmdlets.</span></span>
<span data-ttu-id="07d88-114">Přepínač `-AsJob` dál usnadňuje vytváření úloh PS.</span><span class="sxs-lookup"><span data-stu-id="07d88-114">The `-AsJob` switch makes creating PSJobs even easier.</span></span>

```powershell
$creds = Get-Credential
$job = New-AzureRmVM -Name MyVm -Credential $creds -AsJob
```

<span data-ttu-id="07d88-115">Pomocí `Get-Job` a `Get-AzureRmVM` si kdykoli můžete prohlédnout úlohu a její průběh.</span><span class="sxs-lookup"><span data-stu-id="07d88-115">You can inspect the job and progress at any time with `Get-Job` and `Get-AzureRmVM`.</span></span>

```powershell
Get-Job $job
Get-AzureRmVM MyVm
```

```Output
Id Name                                       PSJobTypeName         State   HasMoreData Location  Command
-- ----                                       -------------         -----   ----------- --------  -------
1  Long Running Operation for 'New-AzureRmVM' AzureLongRunningJob`1 Running True        localhost New-AzureRmVM

ResourceGroupName    Name Location          VmSize  OsType     NIC ProvisioningState Zone
-----------------    ---- --------          ------  ------     --- ----------------- ----
MyVm                 MyVm   eastus Standard_DS1_v2 Windows    MyVm          Creating
```

<span data-ttu-id="07d88-116">Následně po dokončení můžete získat výsledek úlohy pomocí `Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="07d88-116">Subsequently, upon completion, you can obtain the result of the job with `Receive-Job`.</span></span>

> [!NOTE]
> <span data-ttu-id="07d88-117">`Receive-Job` vrací výsledek rutiny, jako kdyby příznak `-AsJob` nebyl použit.</span><span class="sxs-lookup"><span data-stu-id="07d88-117">`Receive-Job` returns the result from the cmdlet as if the `-AsJob` flag were not present.</span></span>
> <span data-ttu-id="07d88-118">Například výsledek `Receive-Job` pro `Do-Action -AsJob` je stejného typu jako výsledek `Do-Action`.</span><span class="sxs-lookup"><span data-stu-id="07d88-118">For example, the `Receive-Job` result of `Do-Action -AsJob` is of the same type as the result of `Do-Action`.</span></span>

```powershell
$vm = Receive-Job $job
$vm
```

```Output
ResourceGroupName        : MyVm
Id                       : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MyVm/providers/Microsoft.Compute/virtualMachines/MyVm
VmId                     : dff1f79e-a8f7-4664-ab72-0ec28b9fbb5b
Name                     : MyVm
Type                     : Microsoft.Compute/virtualMachines
Location                 : eastus
Tags                     : {}
HardwareProfile          : {VmSize}
NetworkProfile           : {NetworkInterfaces}
OSProfile                : {ComputerName, AdminUsername, WindowsConfiguration, Secrets}
ProvisioningState        : Succeeded
StorageProfile           : {ImageReference, OsDisk, DataDisks}
FullyQualifiedDomainName : myvmmyvm.eastus.cloudapp.azure.com
```

## <a name="example-scenarios"></a><span data-ttu-id="07d88-119">Ukázkové scénáře</span><span class="sxs-lookup"><span data-stu-id="07d88-119">Example Scenarios</span></span>

<span data-ttu-id="07d88-120">Vytvořte víc virtuálních počítačů najednou.</span><span class="sxs-lookup"><span data-stu-id="07d88-120">Create multiple VMs at once.</span></span>

```powershell
$creds = Get-Credential
# Create 10 jobs.
for($k = 0; $k -lt 10; $k++) {
    New-AzureRmVm -Name MyVm$k  -Credential $creds -AsJob
}

# Get all jobs and wait on them.
Get-Job | Wait-Job
"All jobs completed"
Get-AzureRmVM
```

<span data-ttu-id="07d88-121">V tomto příkladu rutina `Wait-Job` způsobí, že se skript při spuštění úloh pozastaví.</span><span class="sxs-lookup"><span data-stu-id="07d88-121">In this example, the `Wait-Job` cmdlet causes the script to pause while jobs run.</span></span> <span data-ttu-id="07d88-122">Skript pokračuje v provádění, jakmile se všechny úlohy dokončí.</span><span class="sxs-lookup"><span data-stu-id="07d88-122">The script continues executing once all of the jobs have completed.</span></span> <span data-ttu-id="07d88-123">To umožňuje vytvořit několik úloh běžících paralelně a počkat na jejich dokončení, než se bude pokračovat dál.</span><span class="sxs-lookup"><span data-stu-id="07d88-123">This allows you to create several jobs running in parallel then wait for completion before continuing.</span></span>

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
3      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
4      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
5      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
6      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
7      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
8      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
9      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
10     Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
11     Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
2      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
3      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
4      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
5      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
6      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
7      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
8      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
9      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
10     Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
11     Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
All Jobs completed.

ResourceGroupName        Name   Location          VmSize  OsType           NIC ProvisioningState Zone
-----------------        ----   --------          ------  ------           --- ----------------- ----
MYVM                     MyVm     eastus Standard_DS1_v2 Windows          MyVm         Succeeded
MYVM0                   MyVm0     eastus Standard_DS1_v2 Windows         MyVm0         Succeeded
MYVM1                   MyVm1     eastus Standard_DS1_v2 Windows         MyVm1         Succeeded
MYVM2                   MyVm2     eastus Standard_DS1_v2 Windows         MyVm2         Succeeded
MYVM3                   MyVm3     eastus Standard_DS1_v2 Windows         MyVm3         Succeeded
MYVM4                   MyVm4     eastus Standard_DS1_v2 Windows         MyVm4         Succeeded
MYVM5                   MyVm5     eastus Standard_DS1_v2 Windows         MyVm5         Succeeded
MYVM6                   MyVm6     eastus Standard_DS1_v2 Windows         MyVm6         Succeeded
MYVM7                   MyVm7     eastus Standard_DS1_v2 Windows         MyVm7         Succeeded
MYVM8                   MyVm8     eastus Standard_DS1_v2 Windows         MyVm8         Succeeded
MYVM9                   MyVm9     eastus Standard_DS1_v2 Windows         MyVm9         Succeeded
```
