---
title: Začínáme s prostředím Azure PowerShell | Dokumentace Microsoftu
description: ''
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: get-started-article
ms.date: 11/15/2017
ms.openlocfilehash: 24eb3cf1a58ac87d437d3471639cd9c8cec4070e
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="getting-started-with-azure-powershell"></a>Začínáme s prostředím Azure PowerShell

Prostředí Azure PowerShell je určeno pro správu prostředků Azure z příkazového řádku a pro vytváření skriptů pro automatizaci, které pracují s Azure Resource Managerem. Můžete ho používat v prohlížeči pomocí služby [Azure Cloud Shell](/azure/cloud-shell/overview) nebo nainstalovat na místním počítači a používat ho v jakékoli relaci PowerShellu. Tento článek vám pomůže začít ho používat a seznámí vás se základními koncepcemi jeho fungování.

## <a name="connect"></a>Připojení

Nejjednodušším způsobem, jak začít, je [spustit Cloud Shell](/azure/cloud-shell/quickstart).

1. Spusťte Cloud Shell z horního navigačního panelu na webu Azure Portal.

   ![Ikona prostředí](~/media/get-started-azureps/shell-icon.png)

2. Vyberte předplatné, které chcete použít, a vytvořte účet úložiště.

   ![vytvořit účet úložiště](~/media/get-started-azureps/storage-prompt.png)

Po vytvoření úložiště Cloud Shell v prohlížeči otevře relaci PowerShellu.

![Cloud Shell pro PowerShell](~/media/get-started-azureps/cloud-powershell.png)

Azure PowerShell můžete také nainstalovat a používat místně v relaci PowerShellu.

## <a name="install-azure-powershell"></a>Instalace prostředí Azure PowerShell

Prvním krokem je ověření, že máte nainstalovanou nejnovější verzí prostředí Azure PowerShell. Informace o nejnovější verzi najdete v tématu [Poznámky k verzi](./release-notes-azureps.md).

1. [Nainstalujte prostředí Azure PowerShell](install-azurerm-ps.md).

2. Chcete-li ověřit, že instalace proběhla úspěšně, spusťte z příkazového řádku příkaz `Get-Module AzureRM -ListAvailable`.

## <a name="log-in-to-azure"></a>Přihlášení k Azure

Interaktivní přihlášení:

1. Zadejte `Login-AzureRmAccount`. Zobrazí se dialogové okno s výzvou k zadání přihlašovacích údajů Azure. Možnost '-EnvironmentName' umožňuje přihlásit se ke službě Azure China nebo Azure Germany.

   Příklad: Login-AzureRmAccount -EnvironmentName AzureChinaCloud

2. Zadejte e-mailovou adresu a heslo, které jsou spojené s vaším účtem. Azure přihlašovací údaje ověří, uloží je a pak zavře okno.

Po přihlášení k účtu Azure můžete s použitím rutin prostředí Azure PowerShell využívat přístup k prostředkům v rámci předplatného a spravovat je.

## <a name="create-a-windows-virtual-machine-using-simple-defaults"></a>Vytvoření virtuálního počítače s Windows pomocí jednoduchých výchozích hodnot

Rutina `New-AzureRmVM` poskytuje zjednodušenou syntaxi, což usnadňuje vytvoření nového virtuálního počítače. Musíte zadat jenom dvě hodnoty parametrů: název virtuálního počítače a sadu přihlašovacích údajů pro účet místního správce ve virtuálním počítači.

Nejprve vytvořte objekt přihlašovacích údajů.

```powershell
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

```Output
Windows PowerShell credential request.
Enter a username and password for the virtual machine.
User: localAdmin
Password for user localAdmin: *********
```
Potom vytvořte virtuální počítač.

```powershell
New-AzureRmVM -Name SampleVM -Credential $cred
```

```Output
ResourceGroupName        : SampleVM
Id                       : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/SampleVM/providers/Microsoft.Compute/virtualMachines/SampleVM
VmId                     : 43f6275d-ce50-49c8-a831-5d5974006e63
Name                     : SampleVM
Type                     : Microsoft.Compute/virtualMachines
Location                 : eastus
Tags                     : {}
HardwareProfile          : {VmSize}
NetworkProfile           : {NetworkInterfaces}
OSProfile                : {ComputerName, AdminUsername, WindowsConfiguration, Secrets}
ProvisioningState        : Succeeded
StorageProfile           : {ImageReference, OsDisk, DataDisks}
FullyQualifiedDomainName : samplevm-2c0867.eastus.cloudapp.azure.com
```

To bylo snadné. Může vás ale zajímat, co se ještě vytvořilo a jak je virtuální počítač nakonfigurovaný. Nejdřív se podíváme na naše skupiny prostředků.

```powershell
Get-AzureRmResourceGroup | Select-Object ResourceGroupName,Location
```

```Output
ResourceGroupName          Location
-----------------          --------
cloud-shell-storage-westus westus
SampleVM                   eastus
```

Skupina prostředků **cloud-shell-storage-westus** se vytvoří při prvním použití Cloud Shell. Skupinu prostředků **SampleVM** vytvořila rutina `New-AzureRmVM`.

Jaké další prostředky se vytvořily v této nové skupině prostředků?

```powershell
Get-AzureRmResource |
  Where ResourceGroupName -eq SampleVM |
    Select-Object ResourceGroupName,Location,ResourceType,Name
```

```Output
ResourceGroupName          Location ResourceType                            Name
-----------------          -------- ------------                            ----
SAMPLEVM                   eastus   Microsoft.Compute/disks                 SampleVM_OsDisk_1_9b286c54b168457fa1f8c47...
SampleVM                   eastus   Microsoft.Compute/virtualMachines       SampleVM
SampleVM                   eastus   Microsoft.Network/networkInterfaces     SampleVM
SampleVM                   eastus   Microsoft.Network/networkSecurityGroups SampleVM
SampleVM                   eastus   Microsoft.Network/publicIPAddresses     SampleVM
SampleVM                   eastus   Microsoft.Network/virtualNetworks       SampleVM
```

Získáme o virtuálním počítači další podrobnosti. Tento příklad ukazuje, jak načíst informace o imagi operačního systému použité k vytvoření virtuálního počítače.

```powershell
Get-AzureRmVM -Name SampleVM -ResourceGroupName SampleVM |
  Select-Object -ExpandProperty StorageProfile |
    Select-Object -ExpandProperty ImageReference
```

```Output
Publisher : MicrosoftWindowsServer
Offer     : WindowsServer
Sku       : 2016-Datacenter
Version   : latest
Id        :
```

## <a name="create-a-fully-configured-linux-virtual-machine"></a>Vytvoření plně nakonfigurovaného virtuálního počítače s Linuxem

Předchozí příklad použil zjednodušenou syntaxi a výchozí hodnoty parametrů k vytvoření virtuálního počítače s Windows. V tomto příkladu zadáme hodnoty pro všechny možnosti virtuálního počítače.

### <a name="create-a-resource-group"></a>Vytvoření skupiny prostředků

V tomto příkladu chceme vytvořit skupinu prostředků. Skupiny prostředků v Azure představují způsob, jak spravovat více prostředků, které chcete logicky seskupit. Můžete například vytvořit skupinu prostředků pro aplikaci nebo projekt a přidat do ní virtuální počítač, databázi a službu CDN.

Vytvořte skupinu prostředků s názvem „MyResourceGroup“ v oblasti westeurope v Azure. Dosáhnete toho zadáním následujícího příkazu:

```powershell
New-AzureRmResourceGroup -Name 'myResourceGroup' -Location 'westeurope'
```

```Output
ResourceGroupName : myResourceGroup
Location          : westeurope
ProvisioningState : Succeeded
Tags              :
ResourceId        : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myResourceGroup
```

Tato nová skupina prostředků bude obsahovat všechny prostředky potřebné pro nově vytvářený virtuální počítač. Chcete-li vytvořit nový virtuální počítač s Linuxem, je třeba nejdřív vytvořit ostatní požadované prostředky a přiřadit je ke konfiguraci. Pak můžeme vytvořit virtuální počítač s použitím této konfigurace. Budete také potřebovat veřejný klíč SSH s názvem `id_rsa.pub` v adresáři .ssh uživatelského profilu.

#### <a name="create-the-required-network-resources"></a>Vytvoření požadovaných síťových prostředků

Nejprve je třeba vytvořit konfiguraci podsítě, která se použije pro proces vytvoření virtuální sítě. Vytvoříme také veřejnou IP adresu, abychom se mohli připojit k tomuto virtuálnímu počítači. Vytvoříme skupinu zabezpečení sítě pro zabezpečený přístup k veřejné adrese. Nakonec vytvoříme virtuální síťovou kartu s použitím všech předchozích prostředků.

```powershell
# Variables for common values
$resourceGroup = "myResourceGroup"
$location = "westeurope"
$vmName = "myLinuxVM"

# Definer user name and blank password
$securePassword = ConvertTo-SecureString 'azurepassword' -AsPlainText -Force
$cred = New-Object System.Management.Automation.PSCredential ("azureuser", $securePassword)

# Create a subnet configuration
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 192.168.2.0/24

# Create a virtual network
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName $resourceGroup -Location $location `
  -Name MYvNET2 -AddressPrefix 192.168.0.0/16 -Subnet $subnetConfig

# Create a public IP address and specify a DNS name
$publicIp = New-AzureRmPublicIpAddress -ResourceGroupName $resourceGroup -Location $location `
  -Name "mypublicdns$(Get-Random)" -AllocationMethod Static -IdleTimeoutInMinutes 4
$publicIp | Select-Object Name,IpAddress

# Create an inbound network security group rule for port 22
$nsgRuleSSH = New-AzureRmNetworkSecurityRuleConfig -Name myNetworkSecurityGroupRuleSSH  -Protocol Tcp `
  -Direction Inbound -Priority 1000 -SourceAddressPrefix * -SourcePortRange * -DestinationAddressPrefix * `
  -DestinationPortRange 22 -Access Allow

# Create a network security group
$nsg = New-AzureRmNetworkSecurityGroup -ResourceGroupName $resourceGroup -Location $location `
  -Name myNetworkSecurityGroup2 -SecurityRules $nsgRuleSSH

# Create a virtual network card and associate with public IP address and NSG
$nic = New-AzureRmNetworkInterface -Name myNic2 -ResourceGroupName $resourceGroup -Location $location `
  -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $publicIp.Id -NetworkSecurityGroupId $nsg.Id
```

### <a name="create-the-vm-configuration"></a>Vytvoření konfigurace virtuálního počítače

Teď, když máme požadované prostředky, můžeme vytvořit objekt konfigurace virtuálního počítače.

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Linux -ComputerName $vmName -Credential $cred -DisablePasswordAuthentication |
  Set-AzureRmVMSourceImage -PublisherName Canonical -Offer UbuntuServer -Skus 14.04.2-LTS -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Configure SSH Keys
$sshPublicKey = Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"
Add-AzureRmVMSshPublicKey -VM $vmConfig -KeyData $sshPublicKey -Path "/home/azureuser/.ssh/authorized_keys"
```

### <a name="create-the-virtual-machine"></a>Vytvoření virtuálního počítače

Nyní můžeme pomocí objektu konfigurace virtuálního počítače vytvořit virtuální počítač.

```powershell
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

Teď, když byl virtuální počítač vytvořen, se můžete k novému virtuálnímu počítači s Linuxem přihlásit pomocí protokolu SSH s použitím veřejné IP adresy virtuálního počítače:

```bash
ssh xx.xxx.xxx.xxx
```

```Output
Welcome to Ubuntu 14.04.4 LTS (GNU/Linux 3.19.0-65-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Feb 19 00:32:28 UTC 2017

  System load: 0.31              Memory usage: 3%   Processes:       89
  Usage of /:  39.6% of 1.94GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at:
    https://landscape.canonical.com/

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.



The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

my-login@MyLinuxVM:../../..$
```

## <a name="creating-other-resources-in-azure"></a>Vytváření dalších prostředků v Azure

Nyní jsme prošli postup při vytváření skupiny prostředků, virtuálního počítače s Linuxem a virtuálního počítače s Windows Serverem. Můžete vytvářet i mnoho dalších typů prostředků Azure.

Chceme-li například vytvořit Azure Network Load Balancer, který bychom pak přidružili k nově vytvořeným virtuálním počítačům, můžeme použít následující příkaz pro vytvoření:

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

Pro svou infrastrukturu můžeme také vytvořit novou privátní virtuální síť (v rámci Azure se obvykle označuje jako „virtuální síť“) pomocí následujícího příkazu:

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

Azure a prostředí Azure PowerShell nabízejí vysokou výkonnost díky tomu, že je nemusíme používat jen k získání cloudové infrastruktury, ale také k vytváření služeb spravované platformy. Služby spravované platformy je možné také spojovat s infrastrukturou a sestavovat ještě výkonnější řešení.

Můžete například použít prostředí Azure PowerShell k vytvoření služby Azure AppService. Azure AppService je služba spravované platformy, která poskytuje skvělý způsob hostování webových aplikací bez nutnosti starat o infrastrukturu. Po vytvoření služby Azure AppService můžete v rámci služby AppService vytvořit dvě nové služby Azure Web Apps pomocí následujících příkazů:

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a>Výpis nasazených prostředků

Pomocí rutiny `Get-AzureRmResource` můžete vypsat prostředky, které jsou v Azure spuštěné. V následujícím příkladu jsou uvedeny prostředky, které jsme právě vytvořili v nové skupině prostředků.

```powershell
Get-AzureRmResource |
  Where-Object ResourceGroupName -eq myResourceGroup |
    Select-Object Name,Location,ResourceType
```

```Output
Name                                                  Location   ResourceType
----                                                  --------   ------------
myLinuxVM_OsDisk_1_36ca038791f642ba91270879088c249a   westeurope Microsoft.Compute/disks
myWindowsVM_OsDisk_1_f627e6e2bb454c72897d72e9632adf9a westeurope Microsoft.Compute/disks
myLinuxVM                                             westeurope Microsoft.Compute/virtualMachines
myWindowsVM                                           westeurope Microsoft.Compute/virtualMachines
myWindowsVM/BGInfo                                    westeurope Microsoft.Compute/virtualMachines/extensions
myNic1                                                westeurope Microsoft.Network/networkInterfaces
myNic2                                                westeurope Microsoft.Network/networkInterfaces
myNetworkSecurityGroup1                               westeurope Microsoft.Network/networkSecurityGroups
myNetworkSecurityGroup2                               westeurope Microsoft.Network/networkSecurityGroups
mypublicdns245369171                                  westeurope Microsoft.Network/publicIPAddresses
mypublicdns779537141                                  westeurope Microsoft.Network/publicIPAddresses
MYvNET1                                               westeurope Microsoft.Network/virtualNetworks
MYvNET2                                               westeurope Microsoft.Network/virtualNetworks
micromyresomywi032907510                              westeurope Microsoft.Storage/storageAccounts
```

## <a name="deleting-resources"></a>Odstraňování prostředků

Chcete-li si vyčistit účtu Azure, může být vhodné odebrat prostředky, které jsme vytvořili v tomto příkladu. Pomocí rutin `Remove-AzureRm*` můžete odstranit prostředky, které už nepotřebujete. Vytvořené virtuální počítače s Windows je možné odebrat pomocí následujícího příkazu:

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

Zobrazí se výzva k potvrzení, že chcete příslušný prostředek odebrat.

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

Můžete také odstranit více prostředků najednou. Následující příkaz například odstraní všechny skupiny prostředků „MyResourceGroup“, které jsme používali pro všechny ukázky v tomto kurzu Začínáme. Tento příkaz odebere skupinu prostředků a všechny prostředky v ní.

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

Provedení může trvat i několik minut.

## <a name="get-samples"></a>Získání ukázek

Chcete-li se dozvědět víc o způsobech používání prostředí Azure PowerShell, podívejte se na naše nejběžnější skripty pro [virtuální počítače s Linuxem](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [virtuální počítače s Windows](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) a [databáze SQL](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).

## <a name="next-steps"></a>Další kroky

* [Přihlášení s využitím prostředí Azure PowerShell](authenticate-azureps.md)
* [Správa předplatných Azure s využitím prostředí Azure PowerShell](manage-subscriptions-azureps.md)
* [Vytváření instančních objektů v Azure s využitím prostředí Azure PowerShell](create-azure-service-principal-azureps.md)
* Přečtěte si poznámky k verzi věnované migraci ze starší verze: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).
* Získejte pomoc od komunity:
  * [Fórum Azure na webu MSDN](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  * [stackoverflow](http://go.microsoft.com/fwlink/?LinkId=320213)
