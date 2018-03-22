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
ms.sourcegitcommit: 33738360a9bb22ff359dd854a29263e73e2b15d5
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2018
---
# <a name="getting-started-with-azure-powershell"></a><span data-ttu-id="8c581-102">Začínáme s prostředím Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c581-102">Getting started with Azure PowerShell</span></span>

<span data-ttu-id="8c581-103">Prostředí Azure PowerShell je určeno pro správu prostředků Azure z příkazového řádku a pro vytváření skriptů pro automatizaci, které pracují s Azure Resource Managerem.</span><span class="sxs-lookup"><span data-stu-id="8c581-103">Azure PowerShell is designed for managing and administering Azure resources from the command line, and for building automation scripts that work against the Azure Resource Manager.</span></span> <span data-ttu-id="8c581-104">Můžete ho používat v prohlížeči pomocí služby [Azure Cloud Shell](/azure/cloud-shell/overview) nebo nainstalovat na místním počítači a používat ho v jakékoli relaci PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="8c581-104">You can use it in your browser with [Azure Cloud Shell](/azure/cloud-shell/overview), or you can install it on your local machine and use it in any PowerShell session.</span></span> <span data-ttu-id="8c581-105">Tento článek vám pomůže začít ho používat a seznámí vás se základními koncepcemi jeho fungování.</span><span class="sxs-lookup"><span data-stu-id="8c581-105">This article helps get you started using it, and teaches you the core concepts behind it.</span></span>

## <a name="connect"></a><span data-ttu-id="8c581-106">Připojení</span><span class="sxs-lookup"><span data-stu-id="8c581-106">Connect</span></span>

<span data-ttu-id="8c581-107">Nejjednodušším způsobem, jak začít, je [spustit Cloud Shell](/azure/cloud-shell/quickstart).</span><span class="sxs-lookup"><span data-stu-id="8c581-107">The simplest way to get started is to [launch Cloud Shell](/azure/cloud-shell/quickstart).</span></span>

1. <span data-ttu-id="8c581-108">Spusťte Cloud Shell z horního navigačního panelu na webu Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="8c581-108">Launch Cloud Shell from the top navigation of the Azure portal.</span></span>

   ![Ikona prostředí](~/media/get-started-azureps/shell-icon.png)

2. <span data-ttu-id="8c581-110">Vyberte předplatné, které chcete použít, a vytvořte účet úložiště.</span><span class="sxs-lookup"><span data-stu-id="8c581-110">Choose the subscription you want to use and create a storage account.</span></span>

   ![vytvořit účet úložiště](~/media/get-started-azureps/storage-prompt.png)

<span data-ttu-id="8c581-112">Po vytvoření úložiště Cloud Shell v prohlížeči otevře relaci PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="8c581-112">Once your storage has been created, the Cloud Shell will open a PowerShell session in the browser.</span></span>

![Cloud Shell pro PowerShell](~/media/get-started-azureps/cloud-powershell.png)

<span data-ttu-id="8c581-114">Azure PowerShell můžete také nainstalovat a používat místně v relaci PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="8c581-114">You can also install Azure PowerShell and use it locally in a PowerShell session.</span></span>

## <a name="install-azure-powershell"></a><span data-ttu-id="8c581-115">Instalace prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c581-115">Install Azure PowerShell</span></span>

<span data-ttu-id="8c581-116">Prvním krokem je ověření, že máte nainstalovanou nejnovější verzí prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c581-116">The first step is to make sure you have the latest version of the Azure PowerShell installed.</span></span> <span data-ttu-id="8c581-117">Informace o nejnovější verzi najdete v tématu [Poznámky k verzi](./release-notes-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="8c581-117">For information about the latest release, see the [release notes](./release-notes-azureps.md).</span></span>

1. <span data-ttu-id="8c581-118">[Nainstalujte prostředí Azure PowerShell](install-azurerm-ps.md).</span><span class="sxs-lookup"><span data-stu-id="8c581-118">[Install Azure PowerShell](install-azurerm-ps.md).</span></span>

2. <span data-ttu-id="8c581-119">Chcete-li ověřit, že instalace proběhla úspěšně, spusťte z příkazového řádku příkaz `Get-Module AzureRM -ListAvailable`.</span><span class="sxs-lookup"><span data-stu-id="8c581-119">To verify the installation was successful, run `Get-Module AzureRM -ListAvailable` from your command line.</span></span>

## <a name="log-in-to-azure"></a><span data-ttu-id="8c581-120">Přihlášení k Azure</span><span class="sxs-lookup"><span data-stu-id="8c581-120">Log in to Azure</span></span>

<span data-ttu-id="8c581-121">Interaktivní přihlášení:</span><span class="sxs-lookup"><span data-stu-id="8c581-121">Sign on interactively:</span></span>

1. <span data-ttu-id="8c581-122">Zadejte `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="8c581-122">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="8c581-123">Zobrazí se dialogové okno s výzvou k zadání přihlašovacích údajů Azure.</span><span class="sxs-lookup"><span data-stu-id="8c581-123">You will get dialog box asking for your Azure credentials.</span></span> <span data-ttu-id="8c581-124">Možnost '-EnvironmentName' umožňuje přihlásit se ke službě Azure China nebo Azure Germany.</span><span class="sxs-lookup"><span data-stu-id="8c581-124">Option '-EnvironmentName' can let you login in Azure China or Azure Germany.</span></span>

   <span data-ttu-id="8c581-125">Příklad: Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span><span class="sxs-lookup"><span data-stu-id="8c581-125">e.g. Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span></span>

2. <span data-ttu-id="8c581-126">Zadejte e-mailovou adresu a heslo, které jsou spojené s vaším účtem.</span><span class="sxs-lookup"><span data-stu-id="8c581-126">Type the email address and password associated with your account.</span></span> <span data-ttu-id="8c581-127">Azure přihlašovací údaje ověří, uloží je a pak zavře okno.</span><span class="sxs-lookup"><span data-stu-id="8c581-127">Azure authenticates and saves the credential information, and then closes the window.</span></span>

<span data-ttu-id="8c581-128">Po přihlášení k účtu Azure můžete s použitím rutin prostředí Azure PowerShell využívat přístup k prostředkům v rámci předplatného a spravovat je.</span><span class="sxs-lookup"><span data-stu-id="8c581-128">Once you have signed in to an Azure account, you can use the Azure PowerShell cmdlets to access and manager the resources in your subscription.</span></span>

## <a name="create-a-windows-virtual-machine-using-simple-defaults"></a><span data-ttu-id="8c581-129">Vytvoření virtuálního počítače s Windows pomocí jednoduchých výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="8c581-129">Create a Windows virtual machine using simple defaults</span></span>

<span data-ttu-id="8c581-130">Rutina `New-AzureRmVM` poskytuje zjednodušenou syntaxi, což usnadňuje vytvoření nového virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="8c581-130">The `New-AzureRmVM` cmdlet provides a simplified syntax making it easy to create a new virtual machine.</span></span> <span data-ttu-id="8c581-131">Musíte zadat jenom dvě hodnoty parametrů: název virtuálního počítače a sadu přihlašovacích údajů pro účet místního správce ve virtuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="8c581-131">There are only two parameter values you must provide: the name of the VM and a set of credentials for the local administrator account on the VM.</span></span>

<span data-ttu-id="8c581-132">Nejprve vytvořte objekt přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="8c581-132">First, create the credential object.</span></span>

```powershell
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

```Output
Windows PowerShell credential request.
Enter a username and password for the virtual machine.
User: localAdmin
Password for user localAdmin: *********
```
<span data-ttu-id="8c581-133">Potom vytvořte virtuální počítač.</span><span class="sxs-lookup"><span data-stu-id="8c581-133">Next, create the VM.</span></span>

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

<span data-ttu-id="8c581-134">To bylo snadné.</span><span class="sxs-lookup"><span data-stu-id="8c581-134">That was easy.</span></span> <span data-ttu-id="8c581-135">Může vás ale zajímat, co se ještě vytvořilo a jak je virtuální počítač nakonfigurovaný.</span><span class="sxs-lookup"><span data-stu-id="8c581-135">But, you may wonder what else is created and how is the VM configured.</span></span> <span data-ttu-id="8c581-136">Nejdřív se podíváme na naše skupiny prostředků.</span><span class="sxs-lookup"><span data-stu-id="8c581-136">First, let's look at our resource groups.</span></span>

```powershell
Get-AzureRmResourceGroup | Select-Object ResourceGroupName,Location
```

```Output
ResourceGroupName          Location
-----------------          --------
cloud-shell-storage-westus westus
SampleVM                   eastus
```

<span data-ttu-id="8c581-137">Skupina prostředků **cloud-shell-storage-westus** se vytvoří při prvním použití Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="8c581-137">The **cloud-shell-storage-westus** resource group is created the first time you use the Cloud Shell.</span></span> <span data-ttu-id="8c581-138">Skupinu prostředků **SampleVM** vytvořila rutina `New-AzureRmVM`.</span><span class="sxs-lookup"><span data-stu-id="8c581-138">The **SampleVM** resource group was created by the `New-AzureRmVM` cmdlet.</span></span>

<span data-ttu-id="8c581-139">Jaké další prostředky se vytvořily v této nové skupině prostředků?</span><span class="sxs-lookup"><span data-stu-id="8c581-139">Now, what other resources were created in this new resource group?</span></span>

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

<span data-ttu-id="8c581-140">Získáme o virtuálním počítači další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="8c581-140">Let's get some more details about the VM.</span></span> <span data-ttu-id="8c581-141">Tento příklad ukazuje, jak načíst informace o imagi operačního systému použité k vytvoření virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="8c581-141">This examples shows how to retrieve information about the OS Image used to create the VM.</span></span>

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

## <a name="create-a-fully-configured-linux-virtual-machine"></a><span data-ttu-id="8c581-142">Vytvoření plně nakonfigurovaného virtuálního počítače s Linuxem</span><span class="sxs-lookup"><span data-stu-id="8c581-142">Create a fully configured Linux Virtual Machine</span></span>

<span data-ttu-id="8c581-143">Předchozí příklad použil zjednodušenou syntaxi a výchozí hodnoty parametrů k vytvoření virtuálního počítače s Windows.</span><span class="sxs-lookup"><span data-stu-id="8c581-143">The previous example used the simplified syntax and default parameter values to create a Windows virtual machine.</span></span> <span data-ttu-id="8c581-144">V tomto příkladu zadáme hodnoty pro všechny možnosti virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="8c581-144">In this example, we provide values for all options of the virtual machine.</span></span>

### <a name="create-a-resource-group"></a><span data-ttu-id="8c581-145">Vytvoření skupiny prostředků</span><span class="sxs-lookup"><span data-stu-id="8c581-145">Create a resource group</span></span>

<span data-ttu-id="8c581-146">V tomto příkladu chceme vytvořit skupinu prostředků.</span><span class="sxs-lookup"><span data-stu-id="8c581-146">For this example we want to create a Resource Group.</span></span> <span data-ttu-id="8c581-147">Skupiny prostředků v Azure představují způsob, jak spravovat více prostředků, které chcete logicky seskupit.</span><span class="sxs-lookup"><span data-stu-id="8c581-147">Resource Groups in Azure provide a way to manage multiple resources that you want to logically group together.</span></span> <span data-ttu-id="8c581-148">Můžete například vytvořit skupinu prostředků pro aplikaci nebo projekt a přidat do ní virtuální počítač, databázi a službu CDN.</span><span class="sxs-lookup"><span data-stu-id="8c581-148">For example, you might create a Resource Group for an application or project and add a virtual machine, a database and a CDN service within it.</span></span>

<span data-ttu-id="8c581-149">Vytvořte skupinu prostředků s názvem „MyResourceGroup“ v oblasti westeurope v Azure.</span><span class="sxs-lookup"><span data-stu-id="8c581-149">Let's create a resource group named "MyResourceGroup" in the westeurope region of Azure.</span></span> <span data-ttu-id="8c581-150">Dosáhnete toho zadáním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8c581-150">To do so type the following command:</span></span>

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

<span data-ttu-id="8c581-151">Tato nová skupina prostředků bude obsahovat všechny prostředky potřebné pro nově vytvářený virtuální počítač.</span><span class="sxs-lookup"><span data-stu-id="8c581-151">This new resource group will be used to contain all of the resources needed for the new VM we create.</span></span> <span data-ttu-id="8c581-152">Chcete-li vytvořit nový virtuální počítač s Linuxem, je třeba nejdřív vytvořit ostatní požadované prostředky a přiřadit je ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8c581-152">To create a new Linux VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="8c581-153">Pak můžeme vytvořit virtuální počítač s použitím této konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8c581-153">Then we can use that configuration to create the VM.</span></span> <span data-ttu-id="8c581-154">Budete také potřebovat veřejný klíč SSH s názvem `id_rsa.pub` v adresáři .ssh uživatelského profilu.</span><span class="sxs-lookup"><span data-stu-id="8c581-154">Also, you will need to have an SSH public key named `id_rsa.pub` in the .ssh directory of your user profile.</span></span>

#### <a name="create-the-required-network-resources"></a><span data-ttu-id="8c581-155">Vytvoření požadovaných síťových prostředků</span><span class="sxs-lookup"><span data-stu-id="8c581-155">Create the required network resources</span></span>

<span data-ttu-id="8c581-156">Nejprve je třeba vytvořit konfiguraci podsítě, která se použije pro proces vytvoření virtuální sítě.</span><span class="sxs-lookup"><span data-stu-id="8c581-156">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="8c581-157">Vytvoříme také veřejnou IP adresu, abychom se mohli připojit k tomuto virtuálnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="8c581-157">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="8c581-158">Vytvoříme skupinu zabezpečení sítě pro zabezpečený přístup k veřejné adrese.</span><span class="sxs-lookup"><span data-stu-id="8c581-158">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="8c581-159">Nakonec vytvoříme virtuální síťovou kartu s použitím všech předchozích prostředků.</span><span class="sxs-lookup"><span data-stu-id="8c581-159">Finally we create the virtual NIC using all of the previous resources.</span></span>

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

### <a name="create-the-vm-configuration"></a><span data-ttu-id="8c581-160">Vytvoření konfigurace virtuálního počítače</span><span class="sxs-lookup"><span data-stu-id="8c581-160">Create the VM configuration</span></span>

<span data-ttu-id="8c581-161">Teď, když máme požadované prostředky, můžeme vytvořit objekt konfigurace virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="8c581-161">Now that we have the required resources we can create the VM configuration oboject.</span></span>

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

### <a name="create-the-virtual-machine"></a><span data-ttu-id="8c581-162">Vytvoření virtuálního počítače</span><span class="sxs-lookup"><span data-stu-id="8c581-162">Create the virtual machine</span></span>

<span data-ttu-id="8c581-163">Nyní můžeme pomocí objektu konfigurace virtuálního počítače vytvořit virtuální počítač.</span><span class="sxs-lookup"><span data-stu-id="8c581-163">Now we can create the VM using the VM configuration object.</span></span>

```powershell
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="8c581-164">Teď, když byl virtuální počítač vytvořen, se můžete k novému virtuálnímu počítači s Linuxem přihlásit pomocí protokolu SSH s použitím veřejné IP adresy virtuálního počítače:</span><span class="sxs-lookup"><span data-stu-id="8c581-164">Now that the VM has been created, you can log on to your new Linux VM using SSH with the public IP address of the VM you created:</span></span>

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

## <a name="creating-other-resources-in-azure"></a><span data-ttu-id="8c581-165">Vytváření dalších prostředků v Azure</span><span class="sxs-lookup"><span data-stu-id="8c581-165">Creating other resources in Azure</span></span>

<span data-ttu-id="8c581-166">Nyní jsme prošli postup při vytváření skupiny prostředků, virtuálního počítače s Linuxem a virtuálního počítače s Windows Serverem.</span><span class="sxs-lookup"><span data-stu-id="8c581-166">We've now walked through how to create a Resource Group, a Linux VM, and a Windows Server VM.</span></span> <span data-ttu-id="8c581-167">Můžete vytvářet i mnoho dalších typů prostředků Azure.</span><span class="sxs-lookup"><span data-stu-id="8c581-167">You can create many other types of Azure resources as well.</span></span>

<span data-ttu-id="8c581-168">Chceme-li například vytvořit Azure Network Load Balancer, který bychom pak přidružili k nově vytvořeným virtuálním počítačům, můžeme použít následující příkaz pro vytvoření:</span><span class="sxs-lookup"><span data-stu-id="8c581-168">For example, to create an Azure Network Load Balancer that we could then associate with our newly created VMs, we can use the following create command:</span></span>

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

<span data-ttu-id="8c581-169">Pro svou infrastrukturu můžeme také vytvořit novou privátní virtuální síť (v rámci Azure se obvykle označuje jako „virtuální síť“) pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8c581-169">We could also create a new private Virtual Network (commonly referred to as a "VNet" within Azure) for our infrastructure using the following command:</span></span>

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

<span data-ttu-id="8c581-170">Azure a prostředí Azure PowerShell nabízejí vysokou výkonnost díky tomu, že je nemusíme používat jen k získání cloudové infrastruktury, ale také k vytváření služeb spravované platformy.</span><span class="sxs-lookup"><span data-stu-id="8c581-170">What makes Azure and the Azure PowerShell powerful is that we can use it not just to get cloud-based infrastructure but also to create managed platform services.</span></span> <span data-ttu-id="8c581-171">Služby spravované platformy je možné také spojovat s infrastrukturou a sestavovat ještě výkonnější řešení.</span><span class="sxs-lookup"><span data-stu-id="8c581-171">The managed platform services can also be combined with infrastructure to build even more powerful solutions.</span></span>

<span data-ttu-id="8c581-172">Můžete například použít prostředí Azure PowerShell k vytvoření služby Azure AppService.</span><span class="sxs-lookup"><span data-stu-id="8c581-172">For example, you can use the Azure PowerShell to create an Azure AppService.</span></span> <span data-ttu-id="8c581-173">Azure AppService je služba spravované platformy, která poskytuje skvělý způsob hostování webových aplikací bez nutnosti starat o infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="8c581-173">Azure AppService is a managed platform service that provides a great way to host web apps without having to worry about infrastructure.</span></span> <span data-ttu-id="8c581-174">Po vytvoření služby Azure AppService můžete v rámci služby AppService vytvořit dvě nové služby Azure Web Apps pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="8c581-174">After creating the Azure AppService, you can create two new Azure Web Apps within the AppService using the following commands:</span></span>

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a><span data-ttu-id="8c581-175">Výpis nasazených prostředků</span><span class="sxs-lookup"><span data-stu-id="8c581-175">Listing deployed resources</span></span>

<span data-ttu-id="8c581-176">Pomocí rutiny `Get-AzureRmResource` můžete vypsat prostředky, které jsou v Azure spuštěné.</span><span class="sxs-lookup"><span data-stu-id="8c581-176">You can use the `Get-AzureRmResource` cmdlet to list the resources running in Azure.</span></span> <span data-ttu-id="8c581-177">V následujícím příkladu jsou uvedeny prostředky, které jsme právě vytvořili v nové skupině prostředků.</span><span class="sxs-lookup"><span data-stu-id="8c581-177">The following example shows the resources we just created in the new resource group.</span></span>

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

## <a name="deleting-resources"></a><span data-ttu-id="8c581-178">Odstraňování prostředků</span><span class="sxs-lookup"><span data-stu-id="8c581-178">Deleting resources</span></span>

<span data-ttu-id="8c581-179">Chcete-li si vyčistit účtu Azure, může být vhodné odebrat prostředky, které jsme vytvořili v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="8c581-179">To clean up your Azure account, you want to remove the resources we created in this example.</span></span> <span data-ttu-id="8c581-180">Pomocí rutin `Remove-AzureRm*` můžete odstranit prostředky, které už nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="8c581-180">You can use the `Remove-AzureRm*` cmdlets to delete the resources you no longer need.</span></span> <span data-ttu-id="8c581-181">Vytvořené virtuální počítače s Windows je možné odebrat pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8c581-181">To remove the Windows VM we created, using the following command:</span></span>

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

<span data-ttu-id="8c581-182">Zobrazí se výzva k potvrzení, že chcete příslušný prostředek odebrat.</span><span class="sxs-lookup"><span data-stu-id="8c581-182">You will be prompted to confirm that you want to remove the resource.</span></span>

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="8c581-183">Můžete také odstranit více prostředků najednou.</span><span class="sxs-lookup"><span data-stu-id="8c581-183">You can also use the delete many resources at one time.</span></span> <span data-ttu-id="8c581-184">Následující příkaz například odstraní všechny skupiny prostředků „MyResourceGroup“, které jsme používali pro všechny ukázky v tomto kurzu Začínáme.</span><span class="sxs-lookup"><span data-stu-id="8c581-184">For example, the following command deletes all the resource group "MyResourceGroup" that we've used for all the samples in this Get Started tutorial.</span></span> <span data-ttu-id="8c581-185">Tento příkaz odebere skupinu prostředků a všechny prostředky v ní.</span><span class="sxs-lookup"><span data-stu-id="8c581-185">This removes the resource group and all of the resources in it.</span></span>

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="8c581-186">Provedení může trvat i několik minut.</span><span class="sxs-lookup"><span data-stu-id="8c581-186">This can take several minutes to complete.</span></span>

## <a name="get-samples"></a><span data-ttu-id="8c581-187">Získání ukázek</span><span class="sxs-lookup"><span data-stu-id="8c581-187">Get samples</span></span>

<span data-ttu-id="8c581-188">Chcete-li se dozvědět víc o způsobech používání prostředí Azure PowerShell, podívejte se na naše nejběžnější skripty pro [virtuální počítače s Linuxem](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [virtuální počítače s Windows](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) a [databáze SQL](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span><span class="sxs-lookup"><span data-stu-id="8c581-188">To learn more about ways to use the Azure PowerShell, check out our most common scripts for [Linux VMs](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Windows VMs](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), and [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8c581-189">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8c581-189">Next steps</span></span>

* [<span data-ttu-id="8c581-190">Přihlášení s využitím prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c581-190">Login with Azure PowerShell</span></span>](authenticate-azureps.md)
* [<span data-ttu-id="8c581-191">Správa předplatných Azure s využitím prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c581-191">Manage Azure subscriptions with Azure PowerShell</span></span>](manage-subscriptions-azureps.md)
* [<span data-ttu-id="8c581-192">Vytváření instančních objektů v Azure s využitím prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c581-192">Create service principals in Azure using Azure PowerShell</span></span>](create-azure-service-principal-azureps.md)
* <span data-ttu-id="8c581-193">Přečtěte si poznámky k verzi věnované migraci ze starší verze: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span><span class="sxs-lookup"><span data-stu-id="8c581-193">Read the Release notes about migrating from an older release: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span></span>
* <span data-ttu-id="8c581-194">Získejte pomoc od komunity:</span><span class="sxs-lookup"><span data-stu-id="8c581-194">Get help from the community:</span></span>
  * [<span data-ttu-id="8c581-195">Fórum Azure na webu MSDN</span><span class="sxs-lookup"><span data-stu-id="8c581-195">Azure forum on MSDN</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  * [<span data-ttu-id="8c581-196">stackoverflow</span><span class="sxs-lookup"><span data-stu-id="8c581-196">stackoverflow</span></span>](http://go.microsoft.com/fwlink/?LinkId=320213)
