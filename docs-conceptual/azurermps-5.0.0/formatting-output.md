---
title: "Formátování výsledků dotazu | Dokumentace Microsoftu"
description: "Zde se dozvíte, jak zadávat dotazy na prostředky v Azure a jak formátovat výsledky."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 916cf8590de89762bade4f01ce5a502383d51796
ms.sourcegitcommit: 95f216dfda4841358d4656fbdea1b7faaeecbdbd
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2017
---
# <a name="formatting-query-results"></a><span data-ttu-id="dd0dc-103">Formátování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="dd0dc-103">Formatting query results</span></span>

<span data-ttu-id="dd0dc-104">Ve výchozím nastavení má každá rutina prostředí PowerShell předdefinované formátování výstupu, což usnadňuje čtení jeho výstupu.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-104">By default each PowerShell cmdlet has predefined formatting of output making it easy to read.</span></span>  <span data-ttu-id="dd0dc-105">Prostředí PowerShell také poskytuje flexibilní možnosti úprav výstupu nebo převodu výstupu rutin do jiného formátu s použitím následujících rutin:</span><span class="sxs-lookup"><span data-stu-id="dd0dc-105">PowerShell also provides the flexibility to adjust the output or convert the cmdlet output to a different format with the following cmdlets:</span></span>

| <span data-ttu-id="dd0dc-106">Formátování</span><span class="sxs-lookup"><span data-stu-id="dd0dc-106">Formatting</span></span>      | <span data-ttu-id="dd0dc-107">Převod</span><span class="sxs-lookup"><span data-stu-id="dd0dc-107">Conversion</span></span>       |
|-----------------|------------------|
| `Format-Custom` | `ConvertTo-Csv`  |
| `Format-List`   | `ConvertTo-Html` |
| `Format-Table`  | `ConvertTo-Json` |
| `Format-Wide`   | `ConvertTo-Xml`  |

## <a name="formatting-examples"></a><span data-ttu-id="dd0dc-108">Příklady formátování</span><span class="sxs-lookup"><span data-stu-id="dd0dc-108">Formatting examples</span></span>

<span data-ttu-id="dd0dc-109">V tomto příkladu zobrazíme seznam virtuálních počítačů Azure v našem výchozím předplatném.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-109">In this example we get a list of Azure VMs in our default subscription.</span></span>  <span data-ttu-id="dd0dc-110">Výchozí výstup příkazu Get-AzureRmVM je formátován jako tabulka.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-110">The Get-AzureRmVM command defaults output into a table format.</span></span>

```powershell
Get-AzureRmVM
```

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

<span data-ttu-id="dd0dc-111">Pokud chcete omezit vrácené sloupce, můžete použít rutinu `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-111">If you would like to limit the columns returned you can use the `Format-Table` cmdlet.</span></span> <span data-ttu-id="dd0dc-112">V následujícím příkladu zobrazíme stejný seznam virtuálních počítačů, ale omezíme výstup jen na název virtuálního počítače, skupinu prostředků a umístění virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-112">In the following example we get the same list of virtual machines but restrict the output to just the name of the VM, the resource group, and the location of the VM.</span></span>  <span data-ttu-id="dd0dc-113">Parametr `-Autosize` nastavuje velikost sloupců podle velikosti dat.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-113">The `-Autosize` parameter sizes the columns according to the size of the data.</span></span>

```powershell
Get-AzureRmVM | Format-Table Name,ResourceGroupName,Location -AutoSize
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

<span data-ttu-id="dd0dc-114">Pokud chcete, můžete informace zobrazit ve formátu seznamu.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-114">If you would prefer you can view information in a list format.</span></span> <span data-ttu-id="dd0dc-115">To je uvedeno v následujícím příkladu s použitím rutiny `Format-List`.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-115">The following example shows this using the`Format-List` cmdlet.</span></span>

```powershell
Get-AzureRmVM | Format-List Name,VmId,Location,ResourceGroupName
```

```
Name              : MyUnbuntu1610
VmId              : 33422f9b-e339-4704-bad8-dbe094585496
Location          : westeurope
ResourceGroupName : MYWESTEURG

Name              : MyWin2016VM
VmId              : 4650c755-fc2b-4fc7-a5bc-298d5c00808f
Location          : westeurope
ResourceGroupName : MYWESTEURG
```

## <a name="converting-to-other-data-types"></a><span data-ttu-id="dd0dc-116">Převádění na jiné datové typy</span><span class="sxs-lookup"><span data-stu-id="dd0dc-116">Converting to other data types</span></span>

<span data-ttu-id="dd0dc-117">Prostředí PowerShell také nabízí více formátů výstupu, které můžete použít pro splnění svých požadavků.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-117">PowerShell also offers multiple output format you can use to meet your needs.</span></span>  <span data-ttu-id="dd0dc-118">V následujícím příkladu zobrazíme s použitím rutiny `Select-Object` atributy virtuálních počítačů v našem předplatném a převedeme výstup do formátu CSV, který lze snadno importovat do databáze nebo tabulky.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-118">In the following example we use the `Select-Object` cmdlet to get attributes of the virtual machines in our subscription and and convert the output to CSV format for easy import into a database or spreadsheet.</span></span>

```powershell
Get-AzureRmVM | Select-Object ResourceGroupName,Id,VmId,Name,Location,ProvisioningState | ConvertTo-Csv -NoTypeInformation
```

```
"ResourceGroupName","Id","VmId","Name","Location","ProvisioningState"
"MYWESTUERG","/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTUERG/providers/Microsoft.Compute/virtualMachines/MyUnbuntu1610","33422f9b-e339-4704-bad8-dbe094585496","MyUnbuntu1610","westeurope","Succeeded"
"MYWESTUERG","/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTUERG/providers/Microsoft.Compute/virtualMachines/MyWin2016VM","4650c755-fc2b-4fc7-a5bc-298d5c00808f","MyWin2016VM","westeurope","Succeeded"
```

<span data-ttu-id="dd0dc-119">Výstup je možné převést i do formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-119">You can also convert the output into JSON format.</span></span>  <span data-ttu-id="dd0dc-120">V následujícím příkladu vytvoříme stejný seznam virtuálních počítačů, ale změníme formát výstupu na JSON.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-120">The following example creates the same list of VMs but changes the output format to JSON.</span></span>

```powershell
Get-AzureRmVM | Select-Object ResourceGroupName,Id,VmId,Name,Location,ProvisioningState | ConvertTo-Json
```

```
[
    {
        "ResourceGroupName":  "MYWESTEURG",
        "Id":  "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTEURG/providers/Microsoft.Compute/virtualMachines/MyUnbuntu1610",
        "VmId":  "33422f9b-e339-4704-bad8-dbe094585496",
        "Name":  "MyUnbuntu1610",
        "Location":  "westeurope",
        "ProvisioningState":  "Succeeded"
    },
    {
        "ResourceGroupName":  "MYWESTEURG",
        "Id":  "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTEURG/providers/Microsoft.Compute/virtualMachines/MyWin2016VM",
        "VmId":  "4650c755-fc2b-4fc7-a5bc-298d5c00808f",
        "Name":  "MyWin2016VM",
        "Location":  "westeurope",
        "ProvisioningState":  "Succeeded"
    }
]
```
