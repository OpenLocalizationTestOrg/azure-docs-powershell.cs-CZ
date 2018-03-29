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
ms.openlocfilehash: 0a445a7db84c8deb6518b826b4096983669c5961
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="running-cmdlets-in-parallel-using-powershell-jobs"></a>Paralelní spouštění rutin s využitím úloh PowerShellu

PowerShell podporuje asynchronní akce s využitím [úloh PowerShellu](/powershell/module/microsoft.powershell.core/about/about_jobs).
Prostředí Azure PowerShell je silně závislé na síťových voláních do Azure (a čeká na ně). Jako vývojář pravděpodobně často potřebujete provést několik neblokujících volání do Azure ve skriptu nebo vytvářet prostředky Azure v REPL bez blokování aktuální relace. K zajištění těchto potřeb Azure PowerShell poskytuje prvotřídní podporu [úloh PS](/powershell/module/microsoft.powershell.core/about/about_jobs).

## <a name="context-persistence-and-psjobs"></a>Trvalost kontextu a úlohy PS

Úlohy PS běží v samostatných procesech. To znamená, že s úlohami, které vytvoříte, je potřeba správně sdílet informace o připojeních Azure. Při připojení vašeho účtu Azure k relaci PowerShellu pomocí `Login-AzureRmAccount` můžete předat úloze kontext.

```powershell
$creds = Get-Credential
$job = Start-Job { param($context,$vmadmin) New-AzureRmVM -Name MyVm -AzureRmContext $context -Credential $vmadmin} -Arguments (Get-AzureRmContext),$creds
```

Pokud jste se ale rozhodli kontext automaticky ukládat pomocí `Enable-AzureRmContextAutosave`, bude se automaticky sdílet se všemi úlohami, které vytvoříte.

```powershell
Enable-AzureRmContextAutosave
$creds = Get-Credential
$job = Start-Job { param($vmadmin) New-AzureRmVM -Name MyVm -Credential $vmadmin} -Arguments $creds
```

## <a name="automatic-jobs-with--asjob"></a>Automatické úlohy s přepínačem `-AsJob`

Pro usnadnění Azure PowerShell poskytuje přepínač `-AsJob` také u některých dlouho běžících rutin.
Přepínač `-AsJob` dál usnadňuje vytváření úloh PS.

```powershell
$creds = Get-Credential
$job = New-AzureRmVM -Name MyVm -Credential $creds -AsJob
```

Pomocí `Get-Job` a `Get-AzureRmVM` si kdykoli můžete prohlédnout úlohu a její průběh.

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

Následně po dokončení můžete získat výsledek úlohy pomocí `Receive-Job`.

> [!NOTE]
> `Receive-Job` vrací výsledek rutiny, jako kdyby příznak `-AsJob` nebyl použit.
> Například výsledek `Receive-Job` pro `Do-Action -AsJob` je stejného typu jako výsledek `Do-Action`.

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

## <a name="example-scenarios"></a>Ukázkové scénáře

Vytvořte víc virtuálních počítačů najednou.

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

V tomto příkladu rutina `Wait-Job` způsobí, že se skript při spuštění úloh pozastaví. Skript pokračuje v provádění, jakmile se všechny úlohy dokončí. To umožňuje vytvořit několik úloh běžících paralelně a počkat na jejich dokončení, než se bude pokračovat dál.

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
