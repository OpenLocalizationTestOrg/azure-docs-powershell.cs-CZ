---
title: "Protokol změn Azure PowerShellu | Dokumentace Microsoftu"
description: "Toto je historie změn provedených v nejnovější vydané verzi Azure PowerShellu."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.service: azure-powershell
ms.product: azure
ms.devlang: powershell
ms.topic: conceptual
ms.workload: 
ms.date: 05/18/2017
ms.openlocfilehash: 04f89e8d47d0825d46cb1b8817efbcc0cafa0acd
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="fd831-103">Poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="fd831-103">Release notes</span></span>
<a id="release-notes" class="xliff"></a>

<span data-ttu-id="fd831-104">Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="fd831-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <span data-ttu-id="fd831-105">Verze 3.8.0</span><span class="sxs-lookup"><span data-stu-id="fd831-105">Version 3.8.0</span></span>
<a id="version-380" class="xliff"></a>
* <span data-ttu-id="fd831-106">Compute</span><span class="sxs-lookup"><span data-stu-id="fd831-106">Compute</span></span>
  - <span data-ttu-id="fd831-107">Oprava chyby v rutinách Get-*, s cílem umožnit načítat více stránek (více než 120 položek).</span><span class="sxs-lookup"><span data-stu-id="fd831-107">Fix bug in Get-* cmdlets, to allow retrieving multiple pages of data (more than 120 items)</span></span>
* <span data-ttu-id="fd831-108">DataLakeAnalytics</span><span class="sxs-lookup"><span data-stu-id="fd831-108">DataLakeAnalytics</span></span>
  - <span data-ttu-id="fd831-109">Oprava nápovědy k některým příkazům, aby se používaly správné slovní popisy a příkazy.</span><span class="sxs-lookup"><span data-stu-id="fd831-109">Fix help for some commands to have the proper verbage and examples.</span></span>
* <span data-ttu-id="fd831-110">DataLakeStore</span><span class="sxs-lookup"><span data-stu-id="fd831-110">DataLakeStore</span></span>
  - <span data-ttu-id="fd831-111">Přidání podpory pro úvodní a koncovou část k rutině `Get-AzureRMDataLakeStoreItemContent`.</span><span class="sxs-lookup"><span data-stu-id="fd831-111">Add support for head and tail to the `Get-AzureRMDataLakeStoreItemContent` cmdlet.</span></span> <span data-ttu-id="fd831-112">To umožňuje vrátit prvních nebo posledních N nových řádků oddělených tabulátory k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="fd831-112">This enables returning the top N or last N new line delimited rows to be displayed.</span></span>
* <span data-ttu-id="fd831-113">HDInsight</span><span class="sxs-lookup"><span data-stu-id="fd831-113">HDInsight</span></span>
  - <span data-ttu-id="fd831-114">Přidaná podpora pro typ clusteru RServer.</span><span class="sxs-lookup"><span data-stu-id="fd831-114">Added support for RServer cluster type</span></span>
    + <span data-ttu-id="fd831-115">Velikost virtuálního počítače koncového uzlu je možné pro cluster RServer zadat pomocí New-AzureRmHDInsightCluster nebo New-AzureRmHDInsightClusterConfig.</span><span class="sxs-lookup"><span data-stu-id="fd831-115">Edgenode VM size can be specified for RServer cluster in New-AzureRmHDInsightCluster or New-AzureRmHDInsightClusterConfig</span></span>
    + <span data-ttu-id="fd831-116">RServer je nově konfigurační možnost v Add-AzureRmHDInsightConfigValues.</span><span class="sxs-lookup"><span data-stu-id="fd831-116">RServer is now a configuration option in Add-AzureRmHDInsightConfigValues.</span></span> <span data-ttu-id="fd831-117">Umožňuje nastavit příznak RStudio, který indikuje, že je potřeba provést instalaci R Studia.</span><span class="sxs-lookup"><span data-stu-id="fd831-117">It allows for RStudio flag to be set to indicate that R Studio installation should be done.</span></span>
* <span data-ttu-id="fd831-118">LogicApp</span><span class="sxs-lookup"><span data-stu-id="fd831-118">LogicApp</span></span>
  - <span data-ttu-id="fd831-119">Jsou opravené rutiny Set-AzureRmIntegrationAccountSchema a Set-AzureRmIntegrationAccountMap a vyřešily se potíže s vlastností contentlink (dřív byly nastavené vlastnosti content i contentlink a to mělo za následek selhání aktualizace).</span><span class="sxs-lookup"><span data-stu-id="fd831-119">Set-AzureRmIntegrationAccountSchema and Set-AzureRmIntegrationAccountMap cmdlets are fixed for the contentlink issue(Both content and contentlink were set resulting in update failure).</span></span>
* <span data-ttu-id="fd831-120">Síť</span><span class="sxs-lookup"><span data-stu-id="fd831-120">Network</span></span>
  - <span data-ttu-id="fd831-121">K branám Application Gateway byla přidaná podpora pro nové funkce brány webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="fd831-121">Added support for new web application firewall features to Application Gateways</span></span>
    + <span data-ttu-id="fd831-122">Přidání New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig</span><span class="sxs-lookup"><span data-stu-id="fd831-122">Added New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig</span></span>
    + <span data-ttu-id="fd831-123">Přidání Get-AzureRmApplicationGatewayAvailableWafRuleSets (alias: List-AzureRmApplicationGatewayAvailableWafRuleSets)</span><span class="sxs-lookup"><span data-stu-id="fd831-123">Added Get-AzureRmApplicationGatewayAvailableWafRuleSets (Alias: List-AzureRmApplicationGatewayAvailableWafRuleSets)</span></span>
    + <span data-ttu-id="fd831-124">Aktualizace New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Přidání parametrů -RuleSetType, -RuleSetVersion a -DisabledRuleGroups</span><span class="sxs-lookup"><span data-stu-id="fd831-124">Updated New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Added parameter -RuleSetType -RuleSetVersion and -DisabledRuleGroups</span></span>
    + <span data-ttu-id="fd831-125">Aktualizace Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Přidání parametrů -RuleSetType, -RuleSetVersion a -DisabledRuleGroups</span><span class="sxs-lookup"><span data-stu-id="fd831-125">Updated Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Added parameter -RuleSetType -RuleSetVersion and -DisabledRuleGroups</span></span>
  - <span data-ttu-id="fd831-126">Přidání podpory pro zásady IPSec k připojení bran virtuálních sítí</span><span class="sxs-lookup"><span data-stu-id="fd831-126">Added support for IPSec policies to Virtual Network Gateway Connections</span></span>
  - <span data-ttu-id="fd831-127">Přidání New-AzureRmIpsecPolicy</span><span class="sxs-lookup"><span data-stu-id="fd831-127">Added New-AzureRmIpsecPolicy</span></span>
  - <span data-ttu-id="fd831-128">Aktualizace New-AzureRmVirtualNetworkGatewayConnection: Přidání parametrů -IpsecPolicies a -UsePolicyBasedTrafficSelectors</span><span class="sxs-lookup"><span data-stu-id="fd831-128">Updated New-AzureRmVirtualNetworkGatewayConnection: Added parameter -IpsecPolicies and -UsePolicyBasedTrafficSelectors</span></span>
* <span data-ttu-id="fd831-129">Profil</span><span class="sxs-lookup"><span data-stu-id="fd831-129">Profile</span></span>
  - <span data-ttu-id="fd831-130">*Zastaralé:* Save-AzureRmProfile se přejmenovalo na Save-AzureRmContext. Používá se alias pro starý název rutiny, ale tento alias už v další verzi nebude.</span><span class="sxs-lookup"><span data-stu-id="fd831-130">*Obsolete*: Save-AzureRmProfile is renamed to Save-AzureRmContext, there is an alias to the old cmdlet name, the alias will be removed in the next release.</span></span>
  - <span data-ttu-id="fd831-131">*Zastaralé:* Select-AzureRmProfile se přejmenovalo na Import-AzureRmContext. Používá se alias pro starý název rutiny, ale tento alias už v další verzi nebude.</span><span class="sxs-lookup"><span data-stu-id="fd831-131">*Obsolete*: Select-AzureRmProfile is renamed to Import-AzureRmContext, there is an alias to the old cmdlet name, the alias will be removed in the next release.</span></span>
  - <span data-ttu-id="fd831-132">Výstupní typy PSAzureContext a PSAzureProfile rutin profilů se v příští verzi změní.</span><span class="sxs-lookup"><span data-stu-id="fd831-132">The PSAzureContext and PSAzureProfile output types of profile cmdlets will be changed in the next release.</span></span>
  - <span data-ttu-id="fd831-133">Rutina Save-AzureRmContext v příští verzi nebude mít žádný OutputType.</span><span class="sxs-lookup"><span data-stu-id="fd831-133">The Save-AzureRmContext cmdlet will have no OutputType in the next release.</span></span>
  - <span data-ttu-id="fd831-134">Oprava chyb ve společném kódu rutin, aby se pro hodnoty hash dat využíval algoritmus kompatibilní s FIPS: https://github.com/Azure/azure-powershell/issues/3651</span><span class="sxs-lookup"><span data-stu-id="fd831-134">Fix bug in cmdlet common code to use FIPS-compliant algorithm for data hashes: https://github.com/Azure/azure-powershell/issues/3651</span></span>
* <span data-ttu-id="fd831-135">Sql</span><span class="sxs-lookup"><span data-stu-id="fd831-135">Sql</span></span>
  - <span data-ttu-id="fd831-136">Opravy chyb v rutinách skupin převzetí služeb při selhání Azure</span><span class="sxs-lookup"><span data-stu-id="fd831-136">Bug fixes on Azure Failover Group Cmdlets</span></span>
  - <span data-ttu-id="fd831-137">Oprava pro cyklické dotazování operací</span><span class="sxs-lookup"><span data-stu-id="fd831-137">Fix for operation polling</span></span>
  - <span data-ttu-id="fd831-138">Oprava hodnoty GracePeriodWithDataLossHour při nastavení FailoverPolicy na Manual</span><span class="sxs-lookup"><span data-stu-id="fd831-138">Fix GracePeriodWithDataLossHour value when setting FailoverPolicy to Manual</span></span>
* <span data-ttu-id="fd831-139">TrafficManager</span><span class="sxs-lookup"><span data-stu-id="fd831-139">TrafficManager</span></span>
  - <span data-ttu-id="fd831-140">Podpora pro geografickou metodu směrování provozu</span><span class="sxs-lookup"><span data-stu-id="fd831-140">Support for the Geographic traffic routing method</span></span>
    + <span data-ttu-id="fd831-141">Nová hodnota Geographic pro parametr TrafficRoutingMethod funkce New-AzureRmTrafficManagerProfile</span><span class="sxs-lookup"><span data-stu-id="fd831-141">New value 'Geographic' for the TrafficRoutingMethod parameter of New-AzureRmTrafficManagerProfile</span></span>
    + <span data-ttu-id="fd831-142">Nový parametr GeoMapping pro New-AzureRmTrafficManagerEndpoint a Add-AzureRmTrafficManagerEndpointConfig</span><span class="sxs-lookup"><span data-stu-id="fd831-142">New parameter 'GeoMapping' for the New-AzureRmTrafficManagerEndpoint and Add-AzureRmTrafficManagerEndpointConfig</span></span>
    + <span data-ttu-id="fd831-143">Oprava vedení pro Get-AzureRmTrafficManagerProfile, když vrátí kolekci profilů</span><span class="sxs-lookup"><span data-stu-id="fd831-143">Fix piping for Get-AzureRmTrafficManagerProfile when it returns a collection of profiles</span></span>
* <span data-ttu-id="fd831-144">ServiceManagement</span><span class="sxs-lookup"><span data-stu-id="fd831-144">ServiceManagement</span></span>
  - <span data-ttu-id="fd831-145">Restart-AzureVM: Přidání parametru InitiateMaintenance pro provádění údržby během restartování virtuálního počítače</span><span class="sxs-lookup"><span data-stu-id="fd831-145">Restart-AzureVM: Added InitiateMaintenance parameter for performing maintenance during VM restart.</span></span>
  - <span data-ttu-id="fd831-146">Get-AzureVM: Přidání pole stavu údržby</span><span class="sxs-lookup"><span data-stu-id="fd831-146">Get-AzureVM: Added Maintenance Status field.</span></span>
  - <span data-ttu-id="fd831-147">Přidání nových rutin pro podporu upgradu trezoru služby Recovery Services</span><span class="sxs-lookup"><span data-stu-id="fd831-147">Added new cmdlets to support Recovery Services vault upgrade</span></span>
    + <span data-ttu-id="fd831-148">Test-AzureRecoveryServicesVaultUpgrade</span><span class="sxs-lookup"><span data-stu-id="fd831-148">Test-AzureRecoveryServicesVaultUpgrade</span></span>
    + <span data-ttu-id="fd831-149">Invoke-AzureRecoveryServicesVaultUpgrade</span><span class="sxs-lookup"><span data-stu-id="fd831-149">Invoke-AzureRecoveryServicesVaultUpgrade</span></span>
