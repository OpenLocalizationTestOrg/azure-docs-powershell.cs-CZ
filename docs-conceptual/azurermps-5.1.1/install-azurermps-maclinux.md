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
ms.date: 09/06/2017
ms.openlocfilehash: 94b39c18acaca7a4b17b5207feed025442665acc
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a><span data-ttu-id="5a932-103">Instalace a konfigurace Azure PowerShellu v systémech macOS a Linux</span><span class="sxs-lookup"><span data-stu-id="5a932-103">Install and configure Azure PowerShell on macOS and Linux</span></span>

<span data-ttu-id="5a932-104">Nyní je možné nainstalovat PowerShell 6 (beta) a Azure PowerShell na jiných platformách než Windows.</span><span class="sxs-lookup"><span data-stu-id="5a932-104">It is now possible to install PowerShell 6 (beta) and Azure PowerShell on non-Windows platforms.</span></span>
<span data-ttu-id="5a932-105">Proces instalace Azure PowerShellu v systému macOS a Linux se neliší od Windows, ale je potřeba nejdřív nainstalovat PowerShell 6 (beta).</span><span class="sxs-lookup"><span data-stu-id="5a932-105">The process of installing Azure PowerShell on macOS and Linux is not that different from Windows, however, you must first install PowerShell 6 (beta).</span></span>

> [!NOTE]

> <span data-ttu-id="5a932-106">V tuto chvíli jsou PowerShell 6 (beta) i PowerShell Azure pro .NET Core stále ve verzi beta.</span><span class="sxs-lookup"><span data-stu-id="5a932-106">At this time, both PowerShell 6 (beta) and Azure PowerShell for .NET Core are still in beta.</span></span>
> <span data-ttu-id="5a932-107">Podpora pro tyto produkty je omezená.</span><span class="sxs-lookup"><span data-stu-id="5a932-107">Support for these products is limited.</span></span> <span data-ttu-id="5a932-108">Pokud máte problémy nebo zjistíte chyby, zaznamenejte prosím problémy v GitHubu.</span><span class="sxs-lookup"><span data-stu-id="5a932-108">If you have problems or discover bugs, please file Issues in GitHub.</span></span>
>
> * [<span data-ttu-id="5a932-109">Problémy PowerShellu 6 (beta)</span><span class="sxs-lookup"><span data-stu-id="5a932-109">Issues for PowerShell 6 (beta)</span></span>](https://github.com/PowerShell/PowerShell/issues)
> * [<span data-ttu-id="5a932-110">Problémy Azure PowerShellu</span><span class="sxs-lookup"><span data-stu-id="5a932-110">Issues for Azure PowerShell</span></span>](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-6-beta"></a><span data-ttu-id="5a932-111">Krok 1: Instalace PowerShellu 6 (beta)</span><span class="sxs-lookup"><span data-stu-id="5a932-111">Step 1: Install PowerShell 6 (beta)</span></span>

<span data-ttu-id="5a932-112">Proces instalace PowerShellu 6 (beta) se liší v závislosti na cílovém operačním systému.</span><span class="sxs-lookup"><span data-stu-id="5a932-112">The process of installing PowerShell 6 (beta) on varies depending on the target operating system.</span></span>
<span data-ttu-id="5a932-113">I když je možné nainstalovat PowerShell 6 (beta) ve Windows, tento článek se zaměřuje na systémy macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="5a932-113">While it is possible to install PowerShell 6 (beta) on Windows, this article focuses on macOS and Linux.</span></span> <span data-ttu-id="5a932-114">Pokud chcete používat Azure PowerShell ve Windows, přečtěte si téma o [instalaci](./install-azurerm-ps.md) ve Windows.</span><span class="sxs-lookup"><span data-stu-id="5a932-114">If you want to use Azure PowerShell on Windows, see the [install](./install-azurerm-ps.md) article for Windows.</span></span>

<span data-ttu-id="5a932-115">K instalaci **PowerShellu 6** (beta) v systému macOS nebo Linux potřebujete:</span><span class="sxs-lookup"><span data-stu-id="5a932-115">To install **PowerShell 6** (beta) on Linux or macOS, you need to:</span></span>

1. <span data-ttu-id="5a932-116">Získat PowerShell pro konkrétní operační systém a verzi z [GitHubu](https://github.com/powershell/powershell#get-powershell)</span><span class="sxs-lookup"><span data-stu-id="5a932-116">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
2. <span data-ttu-id="5a932-117">Postupovat podle pokynů k instalaci</span><span class="sxs-lookup"><span data-stu-id="5a932-117">Follow the installation instructions</span></span>
   - [<span data-ttu-id="5a932-118">Linux</span><span class="sxs-lookup"><span data-stu-id="5a932-118">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
   - [<span data-ttu-id="5a932-119">macOS</span><span class="sxs-lookup"><span data-stu-id="5a932-119">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)

## <a name="step-2-install-azure-powershell-for-net-core"></a><span data-ttu-id="5a932-120">Krok 2: Instalace Azure PowerShellu pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="5a932-120">Step 2: Install Azure PowerShell for .NET Core</span></span>

<span data-ttu-id="5a932-121">PowerShell 6 (beta) se dodává s již nainstalovaným modulem PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="5a932-121">PowerShell 6 (beta) comes with the PowerShellGet module already installed.</span></span> <span data-ttu-id="5a932-122">To usnadňuje instalaci libovolného modulu, který se publikuje v Galerii prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a932-122">This makes it easy to install any module that is published to the PowerShell Gallery.</span></span> <span data-ttu-id="5a932-123">Pokud chcete nainstalovat Azure PowerShell, otevřete novou relaci PowerShellu a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5a932-123">To install Azure PowerShell, open a new PowerShell session and run the following command:</span></span>

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a><span data-ttu-id="5a932-124">Krok 3: Načtení modulu AzureRM.Netcore</span><span class="sxs-lookup"><span data-stu-id="5a932-124">Step 3: Load the AzureRM.Netcore module</span></span>

<span data-ttu-id="5a932-125">Jakmile je modul nainstalovaný, je potřeba modul načíst do relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="5a932-125">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="5a932-126">Moduly se načítají pomocí rutiny `Import-Module` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5a932-126">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM.Netcore
```

<span data-ttu-id="5a932-127">Po dokončení importu můžete otestovat nově nainstalovaný modul pokusem o přihlášení do Azure pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="5a932-127">After the import completes, you can test your newly installed and module by attempting to sign into Azure using the following command:</span></span>

```powershell
Login-AzureRMAccount
```

<span data-ttu-id="5a932-128">Výše uvedený příkaz by měl zobrazit výzvu k přechodu na adresu `https://aka.ms/devicelogin` a zadání poskytnutého kódu.</span><span class="sxs-lookup"><span data-stu-id="5a932-128">The above command should prompt you to go to `https://aka.ms/devicelogin` and enter the provided code.</span></span>

## <a name="available-cmdlets"></a><span data-ttu-id="5a932-129">Dostupné rutiny</span><span class="sxs-lookup"><span data-stu-id="5a932-129">Available cmdlets</span></span>

<span data-ttu-id="5a932-130">Moduly Azure PowerShellu pro .NET Standard jsou stále ve vývoji.</span><span class="sxs-lookup"><span data-stu-id="5a932-130">The Azure PowerShell modules for .NET Standard are still in development.</span></span> <span data-ttu-id="5a932-131">Tyto moduly neposkytují úplnou sadu rutin, které jsou k dispozici pro verzi modulů pro Windows.</span><span class="sxs-lookup"><span data-stu-id="5a932-131">These modules do not provide the full set of cmdlets that are available for the Windows version of the modules.</span></span> <span data-ttu-id="5a932-132">Následující funkce jsou implementované v modulech AzureRM.Netcore:</span><span class="sxs-lookup"><span data-stu-id="5a932-132">The following functions are implemented in AzureRM.Netcore modules:</span></span>

* <span data-ttu-id="5a932-133">Správa účtů</span><span class="sxs-lookup"><span data-stu-id="5a932-133">Account management</span></span>
  - <span data-ttu-id="5a932-134">Přihlášení pomocí účtu Microsoft, účtu organizace nebo instančního objektu pomocí Microsoft Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="5a932-134">Login with Microsoft account, Organizational account, or Service Principal through Microsoft Azure Active Directory</span></span>
  - <span data-ttu-id="5a932-135">Uložení přihlašovacích údajů na disk pomocí Save-AzureRmContext a načtení uložených přihlašovacích údajů pomocí Import-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="5a932-135">Save Credentials to disk with Save-AzureRmContext and load saved credentials using Import-AzureRmContext</span></span>
* <span data-ttu-id="5a932-136">Prostředí</span><span class="sxs-lookup"><span data-stu-id="5a932-136">Environment</span></span>
  - <span data-ttu-id="5a932-137">Získání různých okamžitě dostupných prostředí Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="5a932-137">Get the different out-of-box Microsoft Azure environments</span></span>
  - <span data-ttu-id="5a932-138">Přidání, nastavení či odebrání přizpůsobených prostředí (například prostředí Azure Stack nebo Windows Azure Pack)</span><span class="sxs-lookup"><span data-stu-id="5a932-138">Add/Set/Remove customized environments (like your Azure Stack or Windows Azure Pack environments)</span></span>
* <span data-ttu-id="5a932-139">Rutiny na úrovni správy pro služby Azure s využitím rozhraní Resource Manageru a Správy služeb.</span><span class="sxs-lookup"><span data-stu-id="5a932-139">Management plane cmdlets for Azure services using Resource Manager and Service Management interfaces.</span></span>
  - <span data-ttu-id="5a932-140">Virtuální počítač</span><span class="sxs-lookup"><span data-stu-id="5a932-140">Virtual Machine</span></span>
  - <span data-ttu-id="5a932-141">App Service (Websites)</span><span class="sxs-lookup"><span data-stu-id="5a932-141">App Service (Websites)</span></span>
  - <span data-ttu-id="5a932-142">SQL Database</span><span class="sxs-lookup"><span data-stu-id="5a932-142">SQL Database</span></span>
  - <span data-ttu-id="5a932-143">Úložiště</span><span class="sxs-lookup"><span data-stu-id="5a932-143">Storage</span></span>
  - <span data-ttu-id="5a932-144">Síť</span><span class="sxs-lookup"><span data-stu-id="5a932-144">Network</span></span>

## <a name="next-steps"></a><span data-ttu-id="5a932-145">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5a932-145">Next Steps</span></span>

<span data-ttu-id="5a932-146">Další informace o použití Azure PowerShellu najdete v tématu [Začínáme s Azure PowerShellem](get-started-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="5a932-146">For more information about using Azure PowerShell, see the [Get started with Azure PowerShell](get-started-azureps.md) article.</span></span>
