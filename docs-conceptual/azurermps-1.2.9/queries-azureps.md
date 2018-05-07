---
title: Zadávání dotazů na prostředky Azure a formátování výsledků | Dokumentace Microsoftu
description: Zde se dozvíte, jak zadávat dotazy na prostředky v Azure a jak formátovat výsledky.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 93a031ce90352286bb1a5e01dc65e6db7cbe5c7e
ms.sourcegitcommit: 5f0013981fcea1d689649b9a2b2ffe84ae842e56
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="querying-for-azure-resources"></a>Zadávání dotazů na prostředky Azure

Dotazování v prostředí PowerShell můžete dokončit s použitím integrovaných rutin. V prostředí PowerShell mají názvy rutin tvar  **_sloveso-podstatné jméno_**. Rutiny používající sloveso **_Get_** jsou rutiny pro dotazování. Rutiny s podstatnými jmény jsou typy prostředků Azure, se kterými se pracuje prostřednictvím rutin se slovesy.


## <a name="selecting-simple-properties"></a>Výběr jednoduchých vlastností

V prostředí Azure PowerShell je pro každou rutinu definováno výchozí formátování. Nejběžnější vlastnosti pro každý typ prostředku se automaticky zobrazují ve formátu tabulky nebo seznamu. Další informace o formátování výstupu najdete v tématu [Formátování výsledků dotazu](formatting-output.md).

Pomocí rutiny `Get-AzureRmVM` můžete zadat dotaz na seznam virtuálních počítačů ve vašem účtu.

```powershell
Get-AzureRmVM
```

Výchozí výstup je automaticky formátován jako tabulka.

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

Pomocí rutiny `Select-Object` můžete vybrat konkrétní vlastnosti, které vás zajímají.

```powershell
Get-AzureRmVM | Select Name,ResourceGroupName,Location
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

## <a name="selecting-complex-nested-properties"></a>Výběr komplexních vnořených vlastností

Pokud je vlastnost, kterou chcete vybrat, vnořená hluboko ve výstupu JSON, je třeba zadat úplnou cestu k této vnořené vlastnosti. Následující příklad ilustruje, jak vybrat název virtuálního počítače a typ operačního systému v rámci rutiny `Get-AzureRmVM`.

```powershell
Get-AzureRmVM | Select Name,@{Name='OSType'; Expression={$_.StorageProfile.OSDisk.OSType}}
```

```
Name           OSType
----           ------
MyUnbuntu1610   Linux
MyWin2016VM   Windows
```

## <a name="filter-result-using-the-where-object-cmdlet"></a>Filtrování výsledků s použitím rutiny Where-Object

Rutina `Where-Object` umožňuje filtrování výsledků na základě kterékoli hodnoty vlastnosti. V následujícím příkladu vybere filtr jenom virtuální počítače, které mají v názvu text „RGD“.

```powershell
Get-AzureRmVM | Where ResourceGroupName -like RGD* | Select ResourceGroupName,Name
```

```
ResourceGroupName  Name
-----------------  ----
RGDEMO001          KBDemo001VM
RGDEMO001          KBDemo020
```

V dalším příkladu jsou jako výsledky vráceny virtuální počítače s nastavením vmSize 'Standard_DS1_V2'.

```powershell
Get-AzureRmVM | Where vmSize -eq Standard_DS1_V2
```

```
ResourceGroupName          Name     Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----     --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610   westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM   westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```
