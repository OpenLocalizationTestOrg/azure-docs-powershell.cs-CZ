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
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
---
# <a name="formatting-query-results"></a>Formátování výsledků dotazu

Ve výchozím nastavení má každá rutina prostředí PowerShell předdefinované formátování výstupu, což usnadňuje čtení jeho výstupu.  Prostředí PowerShell také poskytuje flexibilní možnosti úprav výstupu nebo převodu výstupu rutin do jiného formátu s použitím následujících rutin:

| Formátování      | Převod       |
|-----------------|------------------|
| `Format-Custom` | `ConvertTo-Csv`  |
| `Format-List`   | `ConvertTo-Html` |
| `Format-Table`  | `ConvertTo-Json` |
| `Format-Wide`   | `ConvertTo-Xml`  |

## <a name="formatting-examples"></a>Příklady formátování

V tomto příkladu zobrazíme seznam virtuálních počítačů Azure v našem výchozím předplatném.  Výchozí výstup příkazu Get-AzureRmVM je formátován jako tabulka.

```powershell
Get-AzureRmVM
```

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

Pokud chcete omezit vrácené sloupce, můžete použít rutinu `Format-Table`. V následujícím příkladu zobrazíme stejný seznam virtuálních počítačů, ale omezíme výstup jen na název virtuálního počítače, skupinu prostředků a umístění virtuálního počítače.  Parametr `-Autosize` nastavuje velikost sloupců podle velikosti dat.

```powershell
Get-AzureRmVM | Format-Table Name,ResourceGroupName,Location -AutoSize
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

Pokud chcete, můžete informace zobrazit ve formátu seznamu. To je uvedeno v následujícím příkladu s použitím rutiny `Format-List`.

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

## <a name="converting-to-other-data-types"></a>Převádění na jiné datové typy

Prostředí PowerShell také nabízí více formátů výstupu, které můžete použít pro splnění svých požadavků.  V následujícím příkladu zobrazíme s použitím rutiny `Select-Object` atributy virtuálních počítačů v našem předplatném a převedeme výstup do formátu CSV, který lze snadno importovat do databáze nebo tabulky.

```powershell
Get-AzureRmVM | Select-Object ResourceGroupName,Id,VmId,Name,Location,ProvisioningState | ConvertTo-Csv -NoTypeInformation
```

```
"ResourceGroupName","Id","VmId","Name","Location","ProvisioningState"
"MYWESTUERG","/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTUERG/providers/Microsoft.Compute/virtualMachines/MyUnbuntu1610","33422f9b-e339-4704-bad8-dbe094585496","MyUnbuntu1610","westeurope","Succeeded"
"MYWESTUERG","/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTUERG/providers/Microsoft.Compute/virtualMachines/MyWin2016VM","4650c755-fc2b-4fc7-a5bc-298d5c00808f","MyWin2016VM","westeurope","Succeeded"
```

Výstup je možné převést i do formátu JSON.  V následujícím příkladu vytvoříme stejný seznam virtuálních počítačů, ale změníme formát výstupu na JSON.

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
