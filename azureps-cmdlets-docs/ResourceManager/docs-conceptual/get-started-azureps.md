---
title: "<span data-ttu-id=\"7f265-101\">Začínáme s prostředím Azure PowerShell | Dokumentace Microsoftu</span><span class=\"sxs-lookup\"><span data-stu-id=\"7f265-101\">Get started with Azure PowerShell | Microsoft Docs</span></span>"
description: 
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: get-started-article
ms.date: 03/30/2017
ms.openlocfilehash: 4bfa14f4f139fa8c35d4bb51ae81baea819188ce
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="7f265-102">Začínáme s prostředím Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f265-102">Getting started with Azure PowerShell</span></span>
<a id="getting-started-with-azure-powershell" class="xliff"></a>

<span data-ttu-id="7f265-103">Prostředí Azure PowerShell je určeno pro správu prostředků Azure z příkazového řádku a pro vytváření skriptů pro automatizaci, které pracují s Azure Resource Managerem.</span><span class="sxs-lookup"><span data-stu-id="7f265-103">Azure PowerShell is designed for managing and administering Azure resources from the command line, and for building automation scripts that work against the Azure Resource Manager.</span></span> <span data-ttu-id="7f265-104">Tento článek vám pomůže začít ho používat a seznámí vás se základními koncepcemi jeho fungování.</span><span class="sxs-lookup"><span data-stu-id="7f265-104">This article helps get you started using it, and teaches you the core concepts behind it.</span></span>


## <span data-ttu-id="7f265-105">Instalace prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f265-105">Install Azure PowerShell</span></span>
<a id="install-azure-powershell" class="xliff"></a>
<span data-ttu-id="7f265-106">Prvním krokem je ověření, že máte nainstalovanou nejnovější verzí prostředí Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f265-106">The first step is to make sure you have the latest version of the Azure PowerShell installed.</span></span>  <span data-ttu-id="7f265-107">Nejnovější verze je 4.1.0.</span><span class="sxs-lookup"><span data-stu-id="7f265-107">The latest version is 4.1.0.</span></span>

1. <span data-ttu-id="7f265-108">[Nainstalujte prostředí Azure PowerShell](install-azurerm-ps.md).</span><span class="sxs-lookup"><span data-stu-id="7f265-108">[Install Azure PowerShell](install-azurerm-ps.md).</span></span>

2. <span data-ttu-id="7f265-109">Chcete-li ověřit, že instalace proběhla úspěšně, spusťte z příkazového řádku příkaz `Get-Module AzureRM`.</span><span class="sxs-lookup"><span data-stu-id="7f265-109">To verify the installation was successful, run `Get-Module AzureRM` from your command line.</span></span>


## <span data-ttu-id="7f265-110">Přihlaste se k Azure.</span><span class="sxs-lookup"><span data-stu-id="7f265-110">Log in to Azure</span></span>
<a id="log-in-to-azure" class="xliff"></a>

<span data-ttu-id="7f265-111">Interaktivní přihlášení:</span><span class="sxs-lookup"><span data-stu-id="7f265-111">Sign on interactively:</span></span>

1. <span data-ttu-id="7f265-112">Zadejte `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="7f265-112">Type `Login-AzureRmAccount`.</span></span>  <span data-ttu-id="7f265-113">Zobrazí se dialogové okno s výzvou k zadání přihlašovacích údajů Azure.</span><span class="sxs-lookup"><span data-stu-id="7f265-113">You will get dialog box asking for your Azure credentials.</span></span> <span data-ttu-id="7f265-114">Možnost '-EnvironmentName' umožňuje přihlásit se ke službě Azure China nebo Azure Germany.</span><span class="sxs-lookup"><span data-stu-id="7f265-114">Option '-EnvironmentName' can let you login in Azure China or Azure Germany.</span></span>
   <span data-ttu-id="7f265-115">Příklad: Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span><span class="sxs-lookup"><span data-stu-id="7f265-115">e.g. Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span></span>

2. <span data-ttu-id="7f265-116">Zadejte e-mailovou adresu a heslo, které jsou spojené s vaším účtem.</span><span class="sxs-lookup"><span data-stu-id="7f265-116">Type the email address and password associated with your account.</span></span> <span data-ttu-id="7f265-117">Azure přihlašovací údaje ověří, uloží je a pak zavře okno.</span><span class="sxs-lookup"><span data-stu-id="7f265-117">Azure authenticates and saves the credential information, and then closes the window.</span></span>

<span data-ttu-id="7f265-118">Po přihlášení k účtu Azure můžete s použitím rutin prostředí Azure PowerShell využívat přístup k prostředkům v rámci předplatného a spravovat je.</span><span class="sxs-lookup"><span data-stu-id="7f265-118">Once you have signed in to an Azure account, you can use the Azure PowerShell cmdlets to access and manager the resources in your subscription.</span></span>

## <span data-ttu-id="7f265-119">Vytvoření skupiny prostředků</span><span class="sxs-lookup"><span data-stu-id="7f265-119">Create a resource group</span></span>
<a id="create-a-resource-group" class="xliff"></a>

<span data-ttu-id="7f265-120">Po úspěšném nastavení můžete s použitím prostředí Azure PowerShell vytvářet prostředky v rámci Azure.</span><span class="sxs-lookup"><span data-stu-id="7f265-120">Now that we've got everything set up, let's use Azure PowerShell to create resources within Azure.</span></span>

<span data-ttu-id="7f265-121">Nejdříve vytvořte skupinu prostředků.</span><span class="sxs-lookup"><span data-stu-id="7f265-121">First, create a Resource Group.</span></span> <span data-ttu-id="7f265-122">Skupiny prostředků v Azure představují způsob, jak spravovat více prostředků, které chcete logicky seskupit.</span><span class="sxs-lookup"><span data-stu-id="7f265-122">Resource Groups in Azure provide a way to manage multiple resources that you want to logically group together.</span></span> <span data-ttu-id="7f265-123">Můžete například vytvořit skupinu prostředků pro aplikaci nebo projekt a přidat do ní virtuální počítač, databázi a službu CDN.</span><span class="sxs-lookup"><span data-stu-id="7f265-123">For example, you might create a Resource Group for an application or project and add a virtual machine, a database and a CDN service within it.</span></span>

<span data-ttu-id="7f265-124">Vytvořte skupinu prostředků s názvem „MyResourceGroup“ v oblasti westeurope v Azure.</span><span class="sxs-lookup"><span data-stu-id="7f265-124">Let's create a resource group named "MyResourceGroup" in the westeurope region of Azure.</span></span> <span data-ttu-id="7f265-125">Dosáhnete toho zadáním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="7f265-125">To do so type the following command:</span></span>

```powershell
New-AzureRmResourceGroup -Name 'myResourceGroup' -Location 'westeurope'
```

```
ResourceGroupName : myResourceGroup
Location          : westeurope
ProvisioningState : Succeeded
Tags              :
ResourceId        : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myResourceGroup
```

## <span data-ttu-id="7f265-126">Vytvoření virtuálního počítače s Windows</span><span class="sxs-lookup"><span data-stu-id="7f265-126">Create a Windows Virtual Machine</span></span>
<a id="create-a-windows-virtual-machine" class="xliff"></a>

<span data-ttu-id="7f265-127">Po vytvoření skupiny prostředků v ní vytvořte virtuální počítač s Windows.</span><span class="sxs-lookup"><span data-stu-id="7f265-127">Now that we have our resource group, let's create a Windows VM within it.</span></span> <span data-ttu-id="7f265-128">Chcete-li vytvořit nový virtuální počítač, je třeba nejdřív vytvořit ostatní požadované prostředky a přiřadit je ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7f265-128">To create a new VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="7f265-129">Pak můžeme vytvořit virtuální počítač s použitím této konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7f265-129">Then we can use that configuration to create the VM.</span></span>

### <span data-ttu-id="7f265-130">Vytvoření požadovaných síťových prostředků</span><span class="sxs-lookup"><span data-stu-id="7f265-130">Create the required network resources</span></span>
<a id="create-the-required-network-resources" class="xliff"></a>

<span data-ttu-id="7f265-131">Nejprve je třeba vytvořit konfiguraci podsítě, která se použije pro proces vytvoření virtuální sítě.</span><span class="sxs-lookup"><span data-stu-id="7f265-131">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="7f265-132">Vytvoříme také veřejnou IP adresu, abychom se mohli připojit k tomuto virtuálnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="7f265-132">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="7f265-133">Vytvoříme skupinu zabezpečení sítě pro zabezpečený přístup k veřejné adrese.</span><span class="sxs-lookup"><span data-stu-id="7f265-133">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="7f265-134">Nakonec vytvoříme virtuální síťovou kartu s použitím všech předchozích prostředků.</span><span class="sxs-lookup"><span data-stu-id="7f265-134">Finally we create the virtual NIC using all of the previous resources.</span></span>

```powershell
# Variables for common values
$resourceGroup = "myResourceGroup"
$location = "westeurope"
$vmName = "myWindowsVM"

# Create a subnet configuration
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet1 -AddressPrefix 192.168.1.0/24

# Create a virtual network
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName $resourceGroup -Location $location `
  -Name MYvNET1 -AddressPrefix 192.168.0.0/16 -Subnet $subnetConfig

# Create a public IP address and specify a DNS name
$publicIp = New-AzureRmPublicIpAddress -ResourceGroupName $resourceGroup -Location $location `
  -Name "mypublicdns$(Get-Random)" -AllocationMethod Static -IdleTimeoutInMinutes 4
$publicIp | Select-Object Name,IpAddress

# Create an inbound network security group rule for port 3389
$nsgRuleRDP = New-AzureRmNetworkSecurityRuleConfig -Name myNetworkSecurityGroupRuleRDP  -Protocol Tcp `
  -Direction Inbound -Priority 1000 -SourceAddressPrefix * -SourcePortRange * -DestinationAddressPrefix * `
  -DestinationPortRange 3389 -Access Allow

# Create a network security group
$nsg = New-AzureRmNetworkSecurityGroup -ResourceGroupName $resourceGroup -Location $location `
  -Name myNetworkSecurityGroup1 -SecurityRules $nsgRuleRDP

# Create a virtual network card and associate with public IP address and NSG
$nic = New-AzureRmNetworkInterface -Name myNic1 -ResourceGroupName $resourceGroup -Location $location `
  -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $publicIp.Id -NetworkSecurityGroupId $nsg.Id
```

### <span data-ttu-id="7f265-135">Vytvoření virtuálního počítače</span><span class="sxs-lookup"><span data-stu-id="7f265-135">Create the virtual machine</span></span>
<a id="create-the-virtual-machine" class="xliff"></a>

<span data-ttu-id="7f265-136">Nejdřív potřebujeme sadu přihlašovacích údajů pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="7f265-136">First we need a set of credentials for the OS.</span></span>

```powershell
# Create user object
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

<span data-ttu-id="7f265-137">Teď, když máme požadované prostředky, můžeme vytvořit virtuální počítač.</span><span class="sxs-lookup"><span data-stu-id="7f265-137">Now that we have the required resources we can create the VM.</span></span> <span data-ttu-id="7f265-138">Pro tento krok vytvoříme objekt konfigurace virtuálního počítače a potom konfiguraci použijeme k vytvoření virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="7f265-138">For this step, we create a VM configuration object, then we use the configuration to create the VM.</span></span>

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Windows -ComputerName $vmName -Credential $cred |
  Set-AzureRmVMSourceImage -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Create a virtual machine
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="7f265-139">Příkaz `New-AzureRmVM` zobrazí výsledky jako výstup, jakmile bude virtuální počítač zcela vytvořen a připraven k použití.</span><span class="sxs-lookup"><span data-stu-id="7f265-139">The `New-AzureRmVM` command outputs results once the VM has been fully created and is ready to be used.</span></span>

```
RequestId IsSuccessStatusCode StatusCode ReasonPhrase
--------- ------------------- ---------- ------------
                         True         OK OK
```

<span data-ttu-id="7f265-140">Teď se přihlaste k nově vytvořenému virtuálnímu počítači se systémem Windows Server prostřednictvím vzdálené plochy s použitím veřejné IP adresy virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="7f265-140">Now log on to your newly created Windows Server VM using Remote Desktop and the public IP address of the VM.</span></span> <span data-ttu-id="7f265-141">Následující příkaz zobrazí veřejnou IP adresu vytvořenou v předchozím skriptu.</span><span class="sxs-lookup"><span data-stu-id="7f265-141">The following command displays the public IP address created in the previous script.</span></span>

```powershell
$publicIp | Select-Object Name,IpAddress
```

```
Name                  IpAddress
----                  ---------
mypublicdns1400512543 xx.xx.xx.xx
```

<span data-ttu-id="7f265-142">Pokud pracujete v systému Windows, můžete tuto operaci provést z příkazového řádku pomocí příkazu mstsc:</span><span class="sxs-lookup"><span data-stu-id="7f265-142">If you are on a Windows-based system, you can do this from the command line using the mstsc command:</span></span>

```
mstsc /v:xx.xxx.xx.xxx
```

<span data-ttu-id="7f265-143">Pro přihlášení zadejte kombinaci uživatelského jména a hesla, kterou jste použili při vytváření virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="7f265-143">Supply the same username/password combination you used when creating the VM to log in.</span></span>


## <span data-ttu-id="7f265-144">Vytvoření virtuálního počítače s Linuxem</span><span class="sxs-lookup"><span data-stu-id="7f265-144">Create a Linux Virtual Machine</span></span>
<a id="create-a-linux-virtual-machine" class="xliff"></a>

<span data-ttu-id="7f265-145">Chcete-li vytvořit nový virtuální počítač s Linuxem, je třeba nejdřív vytvořit ostatní požadované prostředky a přiřadit je ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7f265-145">To create a new Linux VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="7f265-146">Pak můžeme vytvořit virtuální počítač s použitím této konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7f265-146">Then we can use that configuration to create the VM.</span></span> <span data-ttu-id="7f265-147">Předpokladem je, že jste již vytvořili skupinu prostředků podle předchozího popisu.</span><span class="sxs-lookup"><span data-stu-id="7f265-147">This assumes that you have already created the resource group as previously shown.</span></span> <span data-ttu-id="7f265-148">Budete také potřebovat veřejný klíč SSH s názvem `id_rsa.pub` v adresáři .ssh uživatelského profilu.</span><span class="sxs-lookup"><span data-stu-id="7f265-148">Also, you will need to have an SSH public key named `id_rsa.pub` in the .ssh directory of your user profile.</span></span>

### <span data-ttu-id="7f265-149">Vytvoření požadovaných síťových prostředků</span><span class="sxs-lookup"><span data-stu-id="7f265-149">Create the required network resources</span></span>
<a id="create-the-required-network-resources" class="xliff"></a>

<span data-ttu-id="7f265-150">Nejprve je třeba vytvořit konfiguraci podsítě, která se použije pro proces vytvoření virtuální sítě.</span><span class="sxs-lookup"><span data-stu-id="7f265-150">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="7f265-151">Vytvoříme také veřejnou IP adresu, abychom se mohli připojit k tomuto virtuálnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="7f265-151">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="7f265-152">Vytvoříme skupinu zabezpečení sítě pro zabezpečený přístup k veřejné adrese.</span><span class="sxs-lookup"><span data-stu-id="7f265-152">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="7f265-153">Nakonec vytvoříme virtuální síťovou kartu s použitím všech předchozích prostředků.</span><span class="sxs-lookup"><span data-stu-id="7f265-153">Finally we create the virtual NIC using all of the previous resources.</span></span>

```powershell
# Variables for common values
$resourceGroup = "myResourceGroup"
$location = "westeurope"
$vmName = "myLinuxVM"

# Definer user name and blank password
$securePassword = ConvertTo-SecureString ' ' -AsPlainText -Force
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

### <span data-ttu-id="7f265-154">Vytvoření virtuálního počítače</span><span class="sxs-lookup"><span data-stu-id="7f265-154">Create the virtual machine</span></span>
<a id="create-the-virtual-machine" class="xliff"></a>

<span data-ttu-id="7f265-155">Teď, když máme požadované prostředky, můžeme vytvořit virtuální počítač.</span><span class="sxs-lookup"><span data-stu-id="7f265-155">Now that we have the required resources we can create the VM.</span></span> <span data-ttu-id="7f265-156">Pro tento krok vytvoříme objekt konfigurace virtuálního počítače a potom konfiguraci použijeme k vytvoření virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="7f265-156">For this step, we create a VM configuration object, then we use the configuration to create the VM.</span></span>

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Linux -ComputerName $vmName -Credential $cred -DisablePasswordAuthentication |
  Set-AzureRmVMSourceImage -PublisherName Canonical -Offer UbuntuServer -Skus 14.04.2-LTS -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Configure SSH Keys
$sshPublicKey = Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"
Add-AzureRmVMSshPublicKey -VM $vmConfig -KeyData $sshPublicKey -Path "/home/azureuser/.ssh/authorized_keys"

# Create a virtual machine
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="7f265-157">Teď, když byl virtuální počítač vytvořen, se můžete k novému virtuálnímu počítači s Linuxem přihlásit pomocí protokolu SSH s použitím veřejné IP adresy virtuálního počítače:</span><span class="sxs-lookup"><span data-stu-id="7f265-157">Now that the VM has been created, you can log on to your new Linux VM using SSH with the public IP address of the VM you created:</span></span>

```bash
ssh xx.xxx.xxx.xxx
```

```
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

my-login@MyLinuxVM:~$
```

## <span data-ttu-id="7f265-158">Vytváření dalších prostředků v Azure</span><span class="sxs-lookup"><span data-stu-id="7f265-158">Creating other resources in Azure</span></span>
<a id="creating-other-resources-in-azure" class="xliff"></a>

<span data-ttu-id="7f265-159">Nyní jsme prošli postup při vytváření skupiny prostředků, virtuálního počítače s Linuxem a virtuálního počítače s Windows Serverem.</span><span class="sxs-lookup"><span data-stu-id="7f265-159">We've now walked through how to create a Resource Group, a Linux VM, and a Windows Server VM.</span></span> <span data-ttu-id="7f265-160">Můžete vytvářet i mnoho dalších typů prostředků Azure.</span><span class="sxs-lookup"><span data-stu-id="7f265-160">You can create many other types of Azure resources as well.</span></span>

<span data-ttu-id="7f265-161">Chceme-li například vytvořit Azure Network Load Balancer, který bychom pak přidružili k nově vytvořeným virtuálním počítačům, můžeme použít následující příkaz pro vytvoření:</span><span class="sxs-lookup"><span data-stu-id="7f265-161">For example, to create an Azure Network Load Balancer that we could then associate with our newly created VMs, we can use the following create command:</span></span>

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

<span data-ttu-id="7f265-162">Pro svou infrastrukturu můžeme také vytvořit novou privátní virtuální síť (v rámci Azure se obvykle označuje jako „virtuální síť“) pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="7f265-162">We could also create a new private Virtual Network (commonly referred to as a "VNet" within Azure) for our infrastructure using the following command:</span></span>

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

<span data-ttu-id="7f265-163">Azure a prostředí Azure PowerShell nabízejí vysokou výkonnost díky tomu, že je nemusíme používat jen k získání cloudové infrastruktury, ale také k vytváření služeb spravované platformy.</span><span class="sxs-lookup"><span data-stu-id="7f265-163">What makes Azure and the Azure PowerShell powerful is that we can use it not just to get cloud-based infrastructure but also to create managed platform services.</span></span> <span data-ttu-id="7f265-164">Služby spravované platformy je možné také spojovat s infrastrukturou a sestavovat ještě výkonnější řešení.</span><span class="sxs-lookup"><span data-stu-id="7f265-164">The managed platform services can also be combined with infrastructure to build even more powerful solutions.</span></span>

<span data-ttu-id="7f265-165">Můžete například použít prostředí Azure PowerShell k vytvoření služby Azure AppService.</span><span class="sxs-lookup"><span data-stu-id="7f265-165">For example, you can use the Azure PowerShell to create an Azure AppService.</span></span> <span data-ttu-id="7f265-166">Azure AppService je služba spravované platformy, která poskytuje skvělý způsob hostování webových aplikací bez nutnosti starat o infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="7f265-166">Azure AppService is a managed platform service that provides a great way to host web apps without having to worry about infrastructure.</span></span> <span data-ttu-id="7f265-167">Po vytvoření služby Azure AppService můžete v rámci služby AppService vytvořit dvě nové služby Azure Web Apps pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="7f265-167">After creating the Azure AppService, you can create two new Azure Web Apps within the AppService using the following commands:</span></span>

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <span data-ttu-id="7f265-168">Výpis nasazených prostředků</span><span class="sxs-lookup"><span data-stu-id="7f265-168">Listing deployed resources</span></span>
<a id="listing-deployed-resources" class="xliff"></a>

<span data-ttu-id="7f265-169">Pomocí rutiny `Get-AzureRmResource` můžete vypsat prostředky, které jsou v Azure spuštěné.</span><span class="sxs-lookup"><span data-stu-id="7f265-169">You can use the `Get-AzureRmResource` cmdlet to list the resources running in Azure.</span></span> <span data-ttu-id="7f265-170">V následujícím příkladu jsou uvedeny prostředky, které jsme právě vytvořili v nové skupině prostředků.</span><span class="sxs-lookup"><span data-stu-id="7f265-170">The following example shows the resources we just created in the new resource group.</span></span>

```powershell
Get-AzureRmResource |
  Where-Object ResourceGroupName -eq myResourceGroup |
    Select-Object Name,Location,ResourceType
```

```
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

## <span data-ttu-id="7f265-171">Odstraňování prostředků</span><span class="sxs-lookup"><span data-stu-id="7f265-171">Deleting resources</span></span>
<a id="deleting-resources" class="xliff"></a>

<span data-ttu-id="7f265-172">Chcete-li si vyčistit účtu Azure, může být vhodné odebrat prostředky, které jsme vytvořili v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="7f265-172">To clean up your Azure account, you want to remove the resources we created in this example.</span></span> <span data-ttu-id="7f265-173">Pomocí rutin `Remove-AzureRm*` můžete odstranit prostředky, které už nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="7f265-173">You can use the `Remove-AzureRm*` cmdlets to delete the resources you no longer need.</span></span> <span data-ttu-id="7f265-174">Vytvořené virtuální počítače s Windows je možné odebrat pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="7f265-174">To remove the Windows VM we created, using the following command:</span></span>

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

<span data-ttu-id="7f265-175">Zobrazí se výzva k potvrzení, že chcete příslušný prostředek odebrat.</span><span class="sxs-lookup"><span data-stu-id="7f265-175">You will be prompted to confirm that you want to remove the resource.</span></span>

```
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="7f265-176">Můžete také odstranit více prostředků najednou.</span><span class="sxs-lookup"><span data-stu-id="7f265-176">You can also use the delete many resources at one time.</span></span> <span data-ttu-id="7f265-177">Následující příkaz například odstraní všechny skupiny prostředků „MyResourceGroup“, které jsme používali pro všechny ukázky v tomto kurzu Začínáme.</span><span class="sxs-lookup"><span data-stu-id="7f265-177">For example, the following command deletes all the resource group "MyResourceGroup" that we've used for all the samples in this Get Started tutorial.</span></span> <span data-ttu-id="7f265-178">Tento příkaz odebere skupinu prostředků a všechny prostředky v ní.</span><span class="sxs-lookup"><span data-stu-id="7f265-178">This removes the resource group and all of the resources in it.</span></span>

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="7f265-179">Provedení může trvat i několik minut.</span><span class="sxs-lookup"><span data-stu-id="7f265-179">This can take several minutes to complete.</span></span>

## <span data-ttu-id="7f265-180">Získání ukázek</span><span class="sxs-lookup"><span data-stu-id="7f265-180">Get samples</span></span>
<a id="get-samples" class="xliff"></a>

<span data-ttu-id="7f265-181">Chcete-li se dozvědět víc o způsobech používání prostředí Azure PowerShell, podívejte se na naše nejběžnější skripty pro [virtuální počítače s Linuxem](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [virtuální počítače s Windows](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) a [databáze SQL](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span><span class="sxs-lookup"><span data-stu-id="7f265-181">To learn more about ways to use the Azure PowerShell, check out our most common scripts for [Linux VMs](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Windows VMs](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), and [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span></span>

## <span data-ttu-id="7f265-182">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7f265-182">Next steps</span></span>
<a id="next-steps" class="xliff"></a>

* [<span data-ttu-id="7f265-183">Přihlášení s využitím prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f265-183">Login with Azure PowerShell</span></span>](authenticate-azureps.md)
* [<span data-ttu-id="7f265-184">Správa předplatných Azure s využitím prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f265-184">Manage Azure subscriptions with Azure PowerShell</span></span>](manage-subscriptions-azureps.md)
* [<span data-ttu-id="7f265-185">Vytváření instančních objektů v Azure s využitím prostředí Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f265-185">Create service principals in Azure using Azure PowerShell</span></span>](create-azure-service-principal-azureps.md)
* <span data-ttu-id="7f265-186">Přečtěte si poznámky k verzi o migraci ze starší verze: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span><span class="sxs-lookup"><span data-stu-id="7f265-186">Read the Release notes about migrating from an older release: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span></span>
* <span data-ttu-id="7f265-187">Získejte pomoc od komunity:</span><span class="sxs-lookup"><span data-stu-id="7f265-187">Get help from the community:</span></span>
  + [<span data-ttu-id="7f265-188">Fórum Azure na webu MSDN</span><span class="sxs-lookup"><span data-stu-id="7f265-188">Azure forum on MSDN</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  + [<span data-ttu-id="7f265-189">stackoverflow</span><span class="sxs-lookup"><span data-stu-id="7f265-189">stackoverflow</span></span>](http://go.microsoft.com/fwlink/?LinkId=320213)
