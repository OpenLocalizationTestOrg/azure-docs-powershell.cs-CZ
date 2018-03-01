---
title: "Instalace a konfigurace Azure PowerShellu v systémech macOS a Linux | Dokumentace Microsoftu"
description: "Postup instalace a konfigurace Azure PowerShellu pro první použití v systému macOS nebo Linux"
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 01/12/2018
ms.openlocfilehash: 64a86dfd4af7f3f0a91501e9a096ff190f7100cb
ms.sourcegitcommit: 5fe9a579d2e0d1cb5a05aadaeba5db784f1b18fa
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a><span data-ttu-id="2ca72-103">Instalace a konfigurace Azure PowerShellu v systémech macOS a Linux</span><span class="sxs-lookup"><span data-stu-id="2ca72-103">Install and configure Azure PowerShell on macOS and Linux</span></span>

<span data-ttu-id="2ca72-104">Nyní je možné nainstalovat PowerShell Core v6 a Azure PowerShell na jiných platformách než Windows.</span><span class="sxs-lookup"><span data-stu-id="2ca72-104">It is now possible to install PowerShell Core v6 and Azure PowerShell on non-Windows platforms.</span></span>
<span data-ttu-id="2ca72-105">Proces instalace Azure PowerShellu v systému macOS a Linux se neliší od Windows, ale je potřeba nejdřív nainstalovat PowerShell Core v6.</span><span class="sxs-lookup"><span data-stu-id="2ca72-105">The process of installing Azure PowerShell on macOS and Linux is not that different from Windows, however, you must first install PowerShell Core v6.</span></span>

> [!NOTE]

> <span data-ttu-id="2ca72-106">V tuto chvíli jsou PowerShell Core v6 i PowerShell Azure pro .NET Core stále ve verzi beta.</span><span class="sxs-lookup"><span data-stu-id="2ca72-106">At this time, both PowerShell Core v6 and Azure PowerShell for .NET Core are still in beta.</span></span>
> <span data-ttu-id="2ca72-107">Podpora pro tyto produkty je omezená.</span><span class="sxs-lookup"><span data-stu-id="2ca72-107">Support for these products is limited.</span></span> <span data-ttu-id="2ca72-108">Pokud máte problémy nebo zjistíte chyby, zaznamenejte prosím problémy v GitHubu.</span><span class="sxs-lookup"><span data-stu-id="2ca72-108">If you have problems or discover bugs, please file Issues in GitHub.</span></span>
>
> * [<span data-ttu-id="2ca72-109">Problémy PowerShellu Core v6</span><span class="sxs-lookup"><span data-stu-id="2ca72-109">Issues for PowerShell Core v6</span></span>](https://github.com/PowerShell/PowerShell/issues)
> * [<span data-ttu-id="2ca72-110">Problémy Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="2ca72-110">Issues for Azure PowerShell</span></span>](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-core-v6"></a><span data-ttu-id="2ca72-111">Krok 1: Instalace PowerShellu Core v6</span><span class="sxs-lookup"><span data-stu-id="2ca72-111">Step 1: Install PowerShell Core v6</span></span>

<span data-ttu-id="2ca72-112">Proces instalace PowerShellu Core v6 se liší v závislosti na cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="2ca72-112">The process of installing PowerShell Core v6 on varies depending on the target operating system.</span></span>
<span data-ttu-id="2ca72-113">I když je možné nainstalovat PowerShell Core v6 ve Windows, tento článek se zaměřuje na systémy macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="2ca72-113">While it is possible to install PowerShell Core v6 on Windows, this article focuses on macOS and Linux.</span></span> <span data-ttu-id="2ca72-114">Pokud chcete používat Azure PowerShell ve Windows, přečtěte si téma o [instalaci](./install-azurerm-ps.md) ve Windows.</span><span class="sxs-lookup"><span data-stu-id="2ca72-114">If you want to use Azure PowerShell on Windows, see the [install](./install-azurerm-ps.md) article for Windows.</span></span>

<span data-ttu-id="2ca72-115">Instalace **PowerShellu Core v6** v Linuxu nebo macOS se liší v závislosti na linuxové distribuci a verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2ca72-115">Installing **PowerShell Core v6** on Linux or macOS varies depending on the Linux distribution and OS version.</span></span>
<span data-ttu-id="2ca72-116">Podrobné pokyny najdete v následujícím článku:</span><span class="sxs-lookup"><span data-stu-id="2ca72-116">Detailed instructions can be found in the following article:</span></span>

- [<span data-ttu-id="2ca72-117">Instalace PowerShellu Core v macOS a Linuxu</span><span class="sxs-lookup"><span data-stu-id="2ca72-117">Installing PowerShell Core on macOS and Linux</span></span>](/powershell/scripting/setup/installing-powershell-core-on-macos-and-linux)

## <a name="step-2-install-azure-powershell-for-net-core"></a><span data-ttu-id="2ca72-118">Krok 2: Instalace Azure PowerShellu pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ca72-118">Step 2: Install Azure PowerShell for .NET Core</span></span>

<span data-ttu-id="2ca72-119">PowerShell Core v6 se dodává s už nainstalovaným modulem PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="2ca72-119">PowerShell Core v6 comes with the PowerShellGet module already installed.</span></span> <span data-ttu-id="2ca72-120">To usnadňuje instalaci libovolného modulu, který se publikuje v Galerii prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ca72-120">This makes it easy to install any module that is published to the PowerShell Gallery.</span></span> <span data-ttu-id="2ca72-121">Pokud chcete nainstalovat Azure PowerShell, otevřete novou relaci PowerShellu a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="2ca72-121">To install Azure PowerShell, open a new PowerShell session and run the following command:</span></span>

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a><span data-ttu-id="2ca72-122">Krok 3: Načtení modulu AzureRM.Netcore</span><span class="sxs-lookup"><span data-stu-id="2ca72-122">Step 3: Load the AzureRM.Netcore module</span></span>

<span data-ttu-id="2ca72-123">Jakmile je modul nainstalovaný, je potřeba modul načíst do relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="2ca72-123">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="2ca72-124">Moduly se načítají pomocí rutiny `Import-Module` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2ca72-124">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM.Netcore
Import-Module AzureRM.Profile.Netcore
```

<span data-ttu-id="2ca72-125">Po dokončení importu můžete otestovat nově nainstalovaný modul pokusem o přihlášení do Azure pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="2ca72-125">After the import completes, you can test your newly installed and module by attempting to sign into Azure using the following command:</span></span>

```powershell
Login-AzureRMAccount
```

<span data-ttu-id="2ca72-126">Výše uvedený příkaz by měl zobrazit výzvu k přechodu na adresu `https://aka.ms/devicelogin` a zadání poskytnutého kódu.</span><span class="sxs-lookup"><span data-stu-id="2ca72-126">The above command should prompt you to go to `https://aka.ms/devicelogin` and enter the provided code.</span></span>

## <a name="available-cmdlets"></a><span data-ttu-id="2ca72-127">Dostupné rutiny</span><span class="sxs-lookup"><span data-stu-id="2ca72-127">Available cmdlets</span></span>

<span data-ttu-id="2ca72-128">Moduly Azure PowerShellu pro .NET Standard jsou stále ve vývoji.</span><span class="sxs-lookup"><span data-stu-id="2ca72-128">The Azure PowerShell modules for .NET Standard are still in development.</span></span> <span data-ttu-id="2ca72-129">Tyto moduly neposkytují úplnou sadu rutin, které jsou k dispozici pro verzi modulů pro Windows.</span><span class="sxs-lookup"><span data-stu-id="2ca72-129">These modules do not provide the full set of cmdlets that are available for the Windows version of the modules.</span></span> <span data-ttu-id="2ca72-130">Následující funkce jsou implementované v modulech AzureRM.Netcore:</span><span class="sxs-lookup"><span data-stu-id="2ca72-130">The following functions are implemented in AzureRM.Netcore modules:</span></span>

* <span data-ttu-id="2ca72-131">Správa účtů</span><span class="sxs-lookup"><span data-stu-id="2ca72-131">Account management</span></span>
  - <span data-ttu-id="2ca72-132">Přihlášení pomocí účtu Microsoft, účtu organizace nebo instančního objektu pomocí Microsoft Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="2ca72-132">Login with Microsoft account, Organizational account, or Service Principal through Microsoft Azure Active Directory</span></span>
  - <span data-ttu-id="2ca72-133">Uložení přihlašovacích údajů na disk pomocí Save-AzureRmContext a načtení uložených přihlašovacích údajů pomocí Import-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="2ca72-133">Save Credentials to disk with Save-AzureRmContext and load saved credentials using Import-AzureRmContext</span></span>
* <span data-ttu-id="2ca72-134">Prostředí</span><span class="sxs-lookup"><span data-stu-id="2ca72-134">Environment</span></span>
  - <span data-ttu-id="2ca72-135">Získání různých okamžitě dostupných prostředí Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2ca72-135">Get the different out-of-box Microsoft Azure environments</span></span>
  - <span data-ttu-id="2ca72-136">Přidání, nastavení či odebrání přizpůsobených prostředí (například prostředí Azure Stack nebo Windows Azure Pack)</span><span class="sxs-lookup"><span data-stu-id="2ca72-136">Add/Set/Remove customized environments (like your Azure Stack or Windows Azure Pack environments)</span></span>
* <span data-ttu-id="2ca72-137">Rutiny na úrovni správy pro služby Azure s využitím rozhraní Resource Manageru a Správy služeb.</span><span class="sxs-lookup"><span data-stu-id="2ca72-137">Management plane cmdlets for Azure services using Resource Manager and Service Management interfaces.</span></span>
  - <span data-ttu-id="2ca72-138">Virtuální počítač</span><span class="sxs-lookup"><span data-stu-id="2ca72-138">Virtual Machine</span></span>
  - <span data-ttu-id="2ca72-139">App Service (Websites)</span><span class="sxs-lookup"><span data-stu-id="2ca72-139">App Service (Websites)</span></span>
  - <span data-ttu-id="2ca72-140">Databáze SQL</span><span class="sxs-lookup"><span data-stu-id="2ca72-140">SQL Database</span></span>
  - <span data-ttu-id="2ca72-141">Úložiště</span><span class="sxs-lookup"><span data-stu-id="2ca72-141">Storage</span></span>
  - <span data-ttu-id="2ca72-142">Síť</span><span class="sxs-lookup"><span data-stu-id="2ca72-142">Network</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ca72-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2ca72-143">Next Steps</span></span>

<span data-ttu-id="2ca72-144">Další informace o použití Azure PowerShellu najdete v tématu [Začínáme s Azure PowerShellem](get-started-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="2ca72-144">For more information about using Azure PowerShell, see the [Get started with Azure PowerShell](get-started-azureps.md) article.</span></span>
