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
ms.openlocfilehash: 97a23180a1fc65d96fdc9dbdffcbe3501a4c4c2a
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="25f46-103">Poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="25f46-103">Release notes</span></span>
<a id="release-notes" class="xliff"></a>

<span data-ttu-id="25f46-104">Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="25f46-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <span data-ttu-id="25f46-105">Verze 4.0.0</span><span class="sxs-lookup"><span data-stu-id="25f46-105">Version 4.0.0</span></span>
<a id="version-400" class="xliff"></a>

* <span data-ttu-id="25f46-106">Toto vydání obsahuje nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="25f46-106">This release contains breaking changes.</span></span> <span data-ttu-id="25f46-107">Podrobnosti o změnách a informace o vlivu změn na stávající skripty najdete v [příručce k migraci](https://aka.ms/azps-migration-guide).</span><span class="sxs-lookup"><span data-stu-id="25f46-107">Please see [the migration guide](https://aka.ms/azps-migration-guide) for change details and the impact on existing scripts.</span></span>
* <span data-ttu-id="25f46-108">Správa rozhraní API</span><span class="sxs-lookup"><span data-stu-id="25f46-108">ApiManagement</span></span>
  - <span data-ttu-id="25f46-109">Přidání podpory konfigurace externích skupin ve skupině New-AzureRmApiManagementGroup</span><span class="sxs-lookup"><span data-stu-id="25f46-109">Added support for configuring external groups in New-AzureRmApiManagementGroup.</span></span>
* <span data-ttu-id="25f46-110">Fakturace</span><span class="sxs-lookup"><span data-stu-id="25f46-110">Billing</span></span>
  - <span data-ttu-id="25f46-111">Nová rutina Get-AzureRmBillingPeriod</span><span class="sxs-lookup"><span data-stu-id="25f46-111">New Cmdlet Get-AzureRmBillingPeriod</span></span>
    + <span data-ttu-id="25f46-112">Slouží k načtení fakturačních období Azure předplatného.</span><span class="sxs-lookup"><span data-stu-id="25f46-112">cmdlet to retrieve azure billing periods of the subscription.</span></span>
  - <span data-ttu-id="25f46-113">Aktualizace rutiny Get-AzureRmBillingInvoice</span><span class="sxs-lookup"><span data-stu-id="25f46-113">Update Cmdlet Get-AzureRmBillingInvoice</span></span>
  - <span data-ttu-id="25f46-114">Nová vlastnost BillingPeriodNames</span><span class="sxs-lookup"><span data-stu-id="25f46-114">new property BillingPeriodNames</span></span>
  - <span data-ttu-id="25f46-115">Výstup v zobrazení seznamu</span><span class="sxs-lookup"><span data-stu-id="25f46-115">output in list view</span></span>
* <span data-ttu-id="25f46-116">Compute</span><span class="sxs-lookup"><span data-stu-id="25f46-116">Compute</span></span>
  - <span data-ttu-id="25f46-117">Aktualizace rutin Set-AzureRmVMAEMExtension a Test-AzureRmVMAEMExtension pro podporu spravovaných disků úrovně Premium</span><span class="sxs-lookup"><span data-stu-id="25f46-117">Updated Set-AzureRmVMAEMExtension and Test-AzureRmVMAEMExtension cmdlets to support Premium managed disks</span></span>
  - <span data-ttu-id="25f46-118">Nastavení šifrování zálohování pro virtuální počítače IaaS a obnovení při selhání</span><span class="sxs-lookup"><span data-stu-id="25f46-118">Backup encryption settings for IaaS VMs and restore on failure</span></span>
  - <span data-ttu-id="25f46-119">Přejmenování ChefServiceInterval na ChefDaemonInterval</span><span class="sxs-lookup"><span data-stu-id="25f46-119">ChefServiceInterval option is renamed to ChefDaemonInterval now.</span></span> <span data-ttu-id="25f46-120">Stará rutina bude ale fungovat i nadále.</span><span class="sxs-lookup"><span data-stu-id="25f46-120">Old one will continue to work however.</span></span>
  - <span data-ttu-id="25f46-121">Odebrání duplikovaných vlastností DataDiskNames a NetworkInterfaceIDs z objektu virtuálního počítače PS</span><span class="sxs-lookup"><span data-stu-id="25f46-121">Remove duplicated DataDiskNames and NetworkInterfaceIDs properties from PS VM object.</span></span>
  - <span data-ttu-id="25f46-122">Nastavení parametrů DataDiskNames a NetworkInterfaceIDs jako volitelných v Remove-AzureRmVMDataDisk a Remove-AzureRmVMNetworkInterface</span><span class="sxs-lookup"><span data-stu-id="25f46-122">Make DataDiskNames and NetworkInterfaceIDs parameters optional in Remove-AzureRmVMDataDisk and Remove-AzureRmVMNetworkInterface, respectively.</span></span>
  - <span data-ttu-id="25f46-123">Oprava problému s propojením rutin Get, když tyto rutiny vrátí objekt seznamu</span><span class="sxs-lookup"><span data-stu-id="25f46-123">Fix the piping issue of Get cmdlets when the Get cmdlets return a list object.</span></span>
  - <span data-ttu-id="25f46-124">Přejmenování rutin, které byly v konfliktu s rutinami RDFE</span><span class="sxs-lookup"><span data-stu-id="25f46-124">Cmdlets that conflicted with RDFE cmdlets have been renamed.</span></span> <span data-ttu-id="25f46-125">Další podrobnosti o problému najdete v článku https://github.com/Azure/azure-powershell/issues/2917.</span><span class="sxs-lookup"><span data-stu-id="25f46-125">See issue https://github.com/Azure/azure-powershell/issues/2917 for more details</span></span>
    + <span data-ttu-id="25f46-126">Přejmenování `New-AzureVMSqlServerAutoBackupConfig` na `New-AzureRmVMSqlServerAutoBackupConfig`</span><span class="sxs-lookup"><span data-stu-id="25f46-126">`New-AzureVMSqlServerAutoBackupConfig` has been renamed to `New-AzureRmVMSqlServerAutoBackupConfig`</span></span>
    + <span data-ttu-id="25f46-127">Přejmenování `New-AzureVMSqlServerAutoPatchingConfig` na `New-AzureRmVMSqlServerAutoPatchingConfig`</span><span class="sxs-lookup"><span data-stu-id="25f46-127">`New-AzureVMSqlServerAutoPatchingConfig` has been renamed to `New-AzureRmVMSqlServerAutoPatchingConfig`</span></span>
    + <span data-ttu-id="25f46-128">Přejmenování `New-AzureVMSqlServerKeyVaultCredentialConfig` na `New-AzureRmVMSqlServerKeyVaultCredentialConfig`</span><span class="sxs-lookup"><span data-stu-id="25f46-128">`New-AzureVMSqlServerKeyVaultCredentialConfig` has been renamed to `New-AzureRmVMSqlServerKeyVaultCredentialConfig`</span></span>
* <span data-ttu-id="25f46-129">Využití</span><span class="sxs-lookup"><span data-stu-id="25f46-129">Consumption</span></span>
  - <span data-ttu-id="25f46-130">Nová rutina Get-AzureRmConsumptionUsageDetail</span><span class="sxs-lookup"><span data-stu-id="25f46-130">New Cmdlet Get-AzureRmConsumptionUsageDetail</span></span>
    + <span data-ttu-id="25f46-131">Rutina slouží k načtení podrobností o využití předplatného.</span><span class="sxs-lookup"><span data-stu-id="25f46-131">cmdlet to retrieve usage details of the subscription.</span></span>
* <span data-ttu-id="25f46-132">ContainerRegistry</span><span class="sxs-lookup"><span data-stu-id="25f46-132">ContainerRegistry</span></span>
  - <span data-ttu-id="25f46-133">Přidání powershellových rutin do Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="25f46-133">Add PowerShell cmdlets for Azure Container Registry</span></span>
    + <span data-ttu-id="25f46-134">New-AzureRmContainerRegistry</span><span class="sxs-lookup"><span data-stu-id="25f46-134">New-AzureRmContainerRegistry</span></span>
    + <span data-ttu-id="25f46-135">Get-AzureRmContainerRegistry</span><span class="sxs-lookup"><span data-stu-id="25f46-135">Get-AzureRmContainerRegistry</span></span>
    + <span data-ttu-id="25f46-136">Update-AzureRmContainerRegistry</span><span class="sxs-lookup"><span data-stu-id="25f46-136">Update-AzureRmContainerRegistry</span></span>
    + <span data-ttu-id="25f46-137">Remove-AzureRmContainerRegistry</span><span class="sxs-lookup"><span data-stu-id="25f46-137">Remove-AzureRmContainerRegistry</span></span>
    + <span data-ttu-id="25f46-138">Get-AzureRmContainerRegistryCredential</span><span class="sxs-lookup"><span data-stu-id="25f46-138">Get-AzureRmContainerRegistryCredential</span></span>
    + <span data-ttu-id="25f46-139">Update-AzureRmContainerRegistryCredential</span><span class="sxs-lookup"><span data-stu-id="25f46-139">Update-AzureRmContainerRegistryCredential</span></span>
    + <span data-ttu-id="25f46-140">Test-AzureRmContainerRegistryNameAvailability</span><span class="sxs-lookup"><span data-stu-id="25f46-140">Test-AzureRmContainerRegistryNameAvailability</span></span>
* <span data-ttu-id="25f46-141">DataLakeAnalytics</span><span class="sxs-lookup"><span data-stu-id="25f46-141">DataLakeAnalytics</span></span>
  - <span data-ttu-id="25f46-142">Přidání podpory pro získání a zobrazení seznamu balíčku katalogu</span><span class="sxs-lookup"><span data-stu-id="25f46-142">Add support for catalog package get and list</span></span>
  - <span data-ttu-id="25f46-143">Přidání podpory zobrazení seznamu následujících položek katalogu z hlubší úrovně nadřazených prvků:</span><span class="sxs-lookup"><span data-stu-id="25f46-143">Add support for listing the following catalog items from deeper ancestors:</span></span>
    + <span data-ttu-id="25f46-144">Table</span><span class="sxs-lookup"><span data-stu-id="25f46-144">Table</span></span>
    + <span data-ttu-id="25f46-145">TVF</span><span class="sxs-lookup"><span data-stu-id="25f46-145">TVF</span></span>
    + <span data-ttu-id="25f46-146">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="25f46-146">View</span></span>
    + <span data-ttu-id="25f46-147">Statistika</span><span class="sxs-lookup"><span data-stu-id="25f46-147">Statistics</span></span>
* <span data-ttu-id="25f46-148">DataLakeStore</span><span class="sxs-lookup"><span data-stu-id="25f46-148">DataLakeStore</span></span>
  - <span data-ttu-id="25f46-149">U `Import-AzureRMDataLakeStoreItem` a `Export-AzureRMDataLakeStoreItem` bylo ve výchozím nastavení vypnuto protokolování trasování z důvodu vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="25f46-149">For `Import-AzureRMDataLakeStoreItem` and `Export-AzureRMDataLakeStoreItem` trace logging has been disabled by default to improve performance.</span></span> <span data-ttu-id="25f46-150">Pokud protokolování trasování chcete používat, použijte parametry `-DiagnosticLogLevel` a `-DiagnosticLogPath`.</span><span class="sxs-lookup"><span data-stu-id="25f46-150">If trace logging is desired please use the `-DiagnosticLogLevel` and `-DiagnosticLogPath` parameters</span></span>
  - <span data-ttu-id="25f46-151">Oprava chyby, která někdy způsobovala selhání PowerShellu při načítání velkého množství malých souborů do ADLS</span><span class="sxs-lookup"><span data-stu-id="25f46-151">Fixed a bug that would sometimes cause PowerShell to crash when uploading lots of small file to ADLS.</span></span>
* <span data-ttu-id="25f46-152">Centrum událostí</span><span class="sxs-lookup"><span data-stu-id="25f46-152">EventHub</span></span>
  - <span data-ttu-id="25f46-153">Oprava chyby:</span><span class="sxs-lookup"><span data-stu-id="25f46-153">Bug fix :</span></span>
    + <span data-ttu-id="25f46-154">Oprava chyby u rutiny Set-AzureRmEventHubNamespace – Tier nemůže být null tam, kde by mělo být SkuName</span><span class="sxs-lookup"><span data-stu-id="25f46-154">Fix for Set-AzureRmEventHubNamespace cmdlet error  - 'Tier' cannot be null, where it should be 'SkuName'</span></span>
    + <span data-ttu-id="25f46-155">Set-AzureRmEventHub – oprava chyby, kdy při aktualizaci EventHub není odkaz objektu nastaven na instanci objektu</span><span class="sxs-lookup"><span data-stu-id="25f46-155">Set-AzureRmEventHub - Fix 'Object reference not set to an instance of an object' error while updating EventHub</span></span>
* <span data-ttu-id="25f46-156">Insights</span><span class="sxs-lookup"><span data-stu-id="25f46-156">Insights</span></span>
  - <span data-ttu-id="25f46-157">Add-AzureRm*AlertRule</span><span class="sxs-lookup"><span data-stu-id="25f46-157">Add-AzureRm*AlertRule</span></span>
    + <span data-ttu-id="25f46-158">Vrátí jeden objekt: newResource, statusCode, requestId.</span><span class="sxs-lookup"><span data-stu-id="25f46-158">Returns a single object: newResource, statusCode, requestId</span></span>
  - <span data-ttu-id="25f46-159">Get-AzureRmAlertRule</span><span class="sxs-lookup"><span data-stu-id="25f46-159">Get-AzureRmAlertRule</span></span>
    + <span data-ttu-id="25f46-160">Výstup teď představuje výčet a nepovažuje se za jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="25f46-160">The output is now enumerated instead of considered a single object.</span></span> <span data-ttu-id="25f46-161">Typ se nezměnil, stále se jedná o seznam.</span><span class="sxs-lookup"><span data-stu-id="25f46-161">Its type did not change, it is still a list.</span></span>
  - <span data-ttu-id="25f46-162">Remove-AzureRmAlertRule</span><span class="sxs-lookup"><span data-stu-id="25f46-162">Remove-AzureRmAlertRule</span></span>
    + <span data-ttu-id="25f46-163">statusCode se řídí stavovým kódem vráceným žádostí, dosud byl vždy OK.</span><span class="sxs-lookup"><span data-stu-id="25f46-163">The statusCode follows the status code returned by the request, before it was Ok always.</span></span>
  - <span data-ttu-id="25f46-164">Add-AzureRmAutoscaleSetting</span><span class="sxs-lookup"><span data-stu-id="25f46-164">Add-AzureRmAutoscaleSetting</span></span>
    + <span data-ttu-id="25f46-165">Vrátí jeden objekt (nikoli seznam jako dříve) obsahující statusCode, requestId a nově vytvořený nebo aktualizovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="25f46-165">Returns now a single object (not a list as before) containing statusCode, requestId, and the newly created/updated resource.</span></span>
    + <span data-ttu-id="25f46-166">Stavový kód se řídí stavem vráceným žádostí, dosud byl vždy OK.</span><span class="sxs-lookup"><span data-stu-id="25f46-166">The status code follows the status returned by the request, before it was always Ok.</span></span>
  - <span data-ttu-id="25f46-167">New-AzureRmAutoscaleRule</span><span class="sxs-lookup"><span data-stu-id="25f46-167">New-AzureRmAutoscaleRule</span></span>
    + <span data-ttu-id="25f46-168">Parametr ScaleActionType byl rozšířen, nyní přijímá tyto hodnoty: ChangeCount, PercentChangeCount, ExactCount.</span><span class="sxs-lookup"><span data-stu-id="25f46-168">The parameter ScaleActionType has been extended, it receives the following values now: ChangeCount, PercentChangeCount, ExactCount.</span></span>
  - <span data-ttu-id="25f46-169">Remove-AzureRmAutoscaleSetting</span><span class="sxs-lookup"><span data-stu-id="25f46-169">Remove-AzureRmAutoscaleSetting</span></span>
    + <span data-ttu-id="25f46-170">statusCode ve výstupu se řídí stavovým kódem vráceným žádostí.</span><span class="sxs-lookup"><span data-stu-id="25f46-170">The statusCode in the output follows the statusCode returned by the request.</span></span> <span data-ttu-id="25f46-171">Dosud byl vždy OK.</span><span class="sxs-lookup"><span data-stu-id="25f46-171">Before it was always Ok.</span></span>
  - <span data-ttu-id="25f46-172">Get-AzureRMLogProfile</span><span class="sxs-lookup"><span data-stu-id="25f46-172">Get-AzureRMLogProfile</span></span>
    + <span data-ttu-id="25f46-173">Výstup teď představuje výčet.</span><span class="sxs-lookup"><span data-stu-id="25f46-173">The output is now enumerated.</span></span> <span data-ttu-id="25f46-174">Dosud se považoval za jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="25f46-174">Before it was considered a single object.</span></span> <span data-ttu-id="25f46-175">Typ výstupu zůstává stejný – jedná se o seznam jako dříve.</span><span class="sxs-lookup"><span data-stu-id="25f46-175">The type of the output remains a list as before.</span></span>
  - <span data-ttu-id="25f46-176">Remove-AzureRmLogProfile</span><span class="sxs-lookup"><span data-stu-id="25f46-176">Remove-AzureRmLogProfile</span></span>
    + <span data-ttu-id="25f46-177">Byl implementován parametr PassThru.</span><span class="sxs-lookup"><span data-stu-id="25f46-177">The PassThru parameter has been implemented.</span></span>
  - <span data-ttu-id="25f46-178">Metrics API</span><span class="sxs-lookup"><span data-stu-id="25f46-178">Metrics API</span></span>
    + <span data-ttu-id="25f46-179">Sada SDK nyní načítá metriky z MDM.</span><span class="sxs-lookup"><span data-stu-id="25f46-179">The SDK now retrieves metrics from MDM.</span></span>
  - <span data-ttu-id="25f46-180">Get-AzureRmMetricDefinition</span><span class="sxs-lookup"><span data-stu-id="25f46-180">Get-AzureRmMetricDefinition</span></span>
    + <span data-ttu-id="25f46-181">Výstupem je stále seznam, ale jeho struktura se změnila.</span><span class="sxs-lookup"><span data-stu-id="25f46-181">The output is still a list, but the structure of the list changed.</span></span>
  - <span data-ttu-id="25f46-182">Get-AzureRmMetric</span><span class="sxs-lookup"><span data-stu-id="25f46-182">Get-AzureRmMetric</span></span>
    + <span data-ttu-id="25f46-183">Volání se změnilo.</span><span class="sxs-lookup"><span data-stu-id="25f46-183">The call has changed.</span></span> <span data-ttu-id="25f46-184">Nová syntaxe: Get-AzureRmMetric ResourceId [MetricNames [TimeGrain] [AggregationType] [StartTime] [EndTime]] [DetailedOutput]</span><span class="sxs-lookup"><span data-stu-id="25f46-184">This is the new syntax: Get-AzureRmMetric ResourceId [MetricNames [TimeGrain] [AggregationType] [StartTime] [EndTime]] [DetailedOutput]</span></span>
    + <span data-ttu-id="25f46-185">Výstupem je seznam a struktura jeho prvků se změnila.</span><span class="sxs-lookup"><span data-stu-id="25f46-185">The output is a list, and the structure of its elements has changed.</span></span>
* <span data-ttu-id="25f46-186">KeyVault</span><span class="sxs-lookup"><span data-stu-id="25f46-186">KeyVault</span></span>
  - <span data-ttu-id="25f46-187">Přidání podpory zálohování a obnovení pro tajné kódy KeyVault</span><span class="sxs-lookup"><span data-stu-id="25f46-187">Adding backup/restore support for KeyVault secrets</span></span>
    + <span data-ttu-id="25f46-188">Tajné kódy je možné zálohovat a obnovit, což odpovídá funkcím, které se momentálně podporují u klíčů.</span><span class="sxs-lookup"><span data-stu-id="25f46-188">Secrets can be backed up and restored, matching the functionality currently supported for Keys</span></span>

  - <span data-ttu-id="25f46-189">Rutiny zálohování pro klíče a tajné kódy nyní jako vstupní parametr přijímají odpovídající objekt.</span><span class="sxs-lookup"><span data-stu-id="25f46-189">Backup cmdlets for Keys and Secrets now accept a corresponding object as an input parameter</span></span>
    + <span data-ttu-id="25f46-190">Volající může zřetězit operace načtení a zálohování: Get-AzureKeyVaultKey -VaultName myVault -Name myKey | Backup-AzureKeyVaultKey</span><span class="sxs-lookup"><span data-stu-id="25f46-190">The caller may chain retrieval and backup operations: Get-AzureKeyVaultKey -VaultName myVault -Name myKey | Backup-AzureKeyVaultKey</span></span>

  - <span data-ttu-id="25f46-191">Rutiny zálohování nyní podporují přepínač -Force pro přepis existujícího souboru.</span><span class="sxs-lookup"><span data-stu-id="25f46-191">Backup cmdlets now support a -Force switch to overwrite an existing file</span></span>
    + <span data-ttu-id="25f46-192">Všimněte si, že při pokusu o přepis existujícího souboru se už přepis nespustí, ale místo se uživateli zobrazí výzva k výběru, jak chce postupovat.</span><span class="sxs-lookup"><span data-stu-id="25f46-192">Note that attempting to overwrite an existing file will no longer throw, and will instead prompt the user for a choice on how to proceed.</span></span>
* <span data-ttu-id="25f46-193">LogicApp</span><span class="sxs-lookup"><span data-stu-id="25f46-193">LogicApp</span></span>
  - <span data-ttu-id="25f46-194">Nové parametry pro rutiny zotavení po havárii kontrolních čísel výměny:</span><span class="sxs-lookup"><span data-stu-id="25f46-194">New parameters for Interchange Control Number disaster recovery cmdlets:</span></span>
    + <span data-ttu-id="25f46-195">Volitelný parametr -AgreementType (X12 nebo Edifact) pro zadání relevantních kontrolních čísel</span><span class="sxs-lookup"><span data-stu-id="25f46-195">Optional -AgreementType parameter ("X12", or "Edifact") to specify the relevant control numbers</span></span>
* <span data-ttu-id="25f46-196">MachineLearning</span><span class="sxs-lookup"><span data-stu-id="25f46-196">MachineLearning</span></span>
  - <span data-ttu-id="25f46-197">Využití nové verze sady Azure Machine Learning .Net SDK a přidání nové rutiny</span><span class="sxs-lookup"><span data-stu-id="25f46-197">Consume new version of Azure Machine Learning .Net SDK and add a new cmdlet</span></span>
    + <span data-ttu-id="25f46-198">Add-AzureRmMlWebServiceRegionalProperty</span><span class="sxs-lookup"><span data-stu-id="25f46-198">Add-AzureRmMlWebServiceRegionalProperty</span></span>
  - <span data-ttu-id="25f46-199">Menší opravy formulace v textu nápovědy</span><span class="sxs-lookup"><span data-stu-id="25f46-199">Minor wording fixes in help text.</span></span>
* <span data-ttu-id="25f46-200">Síť</span><span class="sxs-lookup"><span data-stu-id="25f46-200">Network</span></span>
  - <span data-ttu-id="25f46-201">Přidání rutiny Test-AzureRmNetworkWatcherConnectivity</span><span class="sxs-lookup"><span data-stu-id="25f46-201">Added Test-AzureRmNetworkWatcherConnectivity cmdlet</span></span>
    + <span data-ttu-id="25f46-202">Vrátí informace o konektivitě pro zadaný zdrojový virtuální počítač a cíl.</span><span class="sxs-lookup"><span data-stu-id="25f46-202">Returns connectivity information for a specified source VM and a destination</span></span>
    + <span data-ttu-id="25f46-203">Pokud není možné navázat připojení mezi zdrojem a cílem, rutina vrátí podrobnosti o problému.</span><span class="sxs-lookup"><span data-stu-id="25f46-203">If connectivity between the source and destination cannot be established, the cmdlet returns details about the issue</span></span>
* <span data-ttu-id="25f46-204">Profil</span><span class="sxs-lookup"><span data-stu-id="25f46-204">Profile</span></span>
  - <span data-ttu-id="25f46-205">Přidání rutiny Send-Feedback: umožňuje uživateli iniciovat sadu výzev, které posílají týmu Azure PowerShell zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="25f46-205">Added \`Send-Feedback' cmdlet: allows a user to initiate a set of prompts which sends feedback to the Azure PowerShell team.</span></span>
  - <span data-ttu-id="25f46-206">Následující aliasy byly odebrány, protože docházelo ke konfliktům s názvy existujících rutin v modulu Azure:</span><span class="sxs-lookup"><span data-stu-id="25f46-206">The following aliases have been removed as they conflicted with existing cmdlet names in the Azure module:</span></span>
    + <span data-ttu-id="25f46-207">`Enable-AzureDataCollection` (podporováno rutinou `Enable-AzureRmDataCollection`)</span><span class="sxs-lookup"><span data-stu-id="25f46-207">`Enable-AzureDataCollection` (supported by `Enable-AzureRmDataCollection`)</span></span>
    + <span data-ttu-id="25f46-208">`Disable-AzureDataCollection` (podporováno rutinou `Disable-AzureRmDataCollection`)</span><span class="sxs-lookup"><span data-stu-id="25f46-208">`Disable-AzureDataCollection` (supported by `Disable-AzureRmDataCollection`)</span></span>
* <span data-ttu-id="25f46-209">Relay</span><span class="sxs-lookup"><span data-stu-id="25f46-209">Relay</span></span>
  - <span data-ttu-id="25f46-210">Přidá rutiny pro Azure Relay, které umožňují uživatelům vytvářet a spravovat všechny prostředky Azure Relay.</span><span class="sxs-lookup"><span data-stu-id="25f46-210">Adds cmdlets for the Azure Relay which allows users to create and manage all Azure Relay resources.</span></span>
    + `New-AzureRmRelayNamespace`
    + `Get-AzureRmRelayNamespace`
    + `Set-AzureRmRelayNamespace`
    + `Remove-AzureRmRelayNamespace`
    + `New-AzureRmWcfRelay`
    + `Get-AzureRmWcfRelay`
    + `Set-AzureRmWcfRelay`
    + `Remove-AzureRmWcfRelay`
    + `New-AzureRmRelayHybridConnection`
    + `Get-AzureRmRelayHybridConnection`
    + `Set-AzureRmRelayHybridConnection`
    + `Remove-AzureRmRelayHybridConnection`
    + `Test-AzureRmRelayName`
    + `Get-AzureRmRelayOperation`
    + `New-AzureRmRelayKey`
    + `Get-AzureRmRelayKey`
    + `New-AzureRmRelayAuthorizationRule`
    + `Get-AzureRmRelayAuthorizationRule`
    + `Set-AzureRmRelayAuthorizationRule`
    + `Remove-AzureRmRelayAuthorizationRule`
* <span data-ttu-id="25f46-211">Zdroje a prostředky</span><span class="sxs-lookup"><span data-stu-id="25f46-211">Resources</span></span>
  - <span data-ttu-id="25f46-212">Podporuje nasazení v různých skupinách prostředků pro New-AzureRmResourceGroupDeployment.</span><span class="sxs-lookup"><span data-stu-id="25f46-212">Support cross-resource-group deployments for New-AzureRmResourceGroupDeployment</span></span>
    + <span data-ttu-id="25f46-213">Uživatelé teď můžou používat vnořená nasazení pro nasazení do různých skupin prostředků.</span><span class="sxs-lookup"><span data-stu-id="25f46-213">Users can now use nested deployments to deploy to different resource groups.</span></span>
* <span data-ttu-id="25f46-214">ServiceBus</span><span class="sxs-lookup"><span data-stu-id="25f46-214">ServiceBus</span></span>

  - <span data-ttu-id="25f46-215">Oprava chyby: Hodnoty vlastnosti objektu ServiceBus nebyly nastaveny na null, objekt slouží jako vstupní parametr v rutině Set-AzureRmServiceBusQueue pro aktualizaci fronty.</span><span class="sxs-lookup"><span data-stu-id="25f46-215">Bug Fix: ServiceBus Queue object property values were set to null, the object is used as input parameter in Set-AzureRmServiceBusQueue cmdlet to update Queue.</span></span>
   - <span data-ttu-id="25f46-216">Vlastnosti, kterých se to týká: LockDuration, EntityAvailabilityStatus, DuplicateDetectionHistoryTimeWindow, MaxDeliveryCount a MessageCount</span><span class="sxs-lookup"><span data-stu-id="25f46-216">Properties affected are LockDuration, EntityAvailabilityStatus, DuplicateDetectionHistoryTimeWindow, MaxDeliveryCount and MessageCount</span></span>
* <span data-ttu-id="25f46-217">ServiceFabric</span><span class="sxs-lookup"><span data-stu-id="25f46-217">ServiceFabric</span></span>

  - <span data-ttu-id="25f46-218">Přidání rutin pro prostředky infrastruktury služby</span><span class="sxs-lookup"><span data-stu-id="25f46-218">Added cmdlets for service fabric</span></span>
    + <span data-ttu-id="25f46-219">Add-AzureRmServiceFabricApplicationCertificate: Přidá certifikát, který se použije jako certifikát aplikace.</span><span class="sxs-lookup"><span data-stu-id="25f46-219">Add-AzureRmServiceFabricApplicationCertificate       Add a certificate which will be used as application certificate</span></span>
    + <span data-ttu-id="25f46-220">Add-AzureRmServiceFabricClientCertificate: Přidá běžný název nebo kryptografický otisk do nastavení clusteru pro ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="25f46-220">Add-AzureRmServiceFabricClientCertificate       Add a common name or thumbprint to the cluster settings for client authentication</span></span>
    + <span data-ttu-id="25f46-221">Add-AzureRmServiceFabricClusterCertificate: Do clusteru přidá sekundární certifikát clusteru pro předání existujícího certifikátu.</span><span class="sxs-lookup"><span data-stu-id="25f46-221">Add-AzureRmServiceFabricClusterCertificate       Add a secondary cluster certificate to the cluster for rolling over the existing certificate</span></span>
    + <span data-ttu-id="25f46-222">Add-AzureRmServiceFabricNodes: Do clusteru přidá uzly nebo virtuální počítače s konkrétním typem uzlu.</span><span class="sxs-lookup"><span data-stu-id="25f46-222">Add-AzureRmServiceFabricNodes       Add nodes/VMs of a specific node type to a cluster</span></span>
    + <span data-ttu-id="25f46-223">Add-AzureRmServiceFabricNodeType: Do existujícího clusteru přidá typ uzlu nebo virtuální počítače.</span><span class="sxs-lookup"><span data-stu-id="25f46-223">Add-AzureRmServiceFabricNodeType       Add a node type/VMs to an existing cluster</span></span>
    + <span data-ttu-id="25f46-224">Get-AzureRmServiceFabricCluster: Načte podrobnosti prostředku clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-224">Get-AzureRmServiceFabricCluster       Get the details of the cluster resource</span></span>
    + <span data-ttu-id="25f46-225">New-AzureRmServiceFabricCluster: Vytvoří nový cluster ServiceFabric.</span><span class="sxs-lookup"><span data-stu-id="25f46-225">New-AzureRmServiceFabricCluster Create a new ServiceFabric cluster.</span></span> <span data-ttu-id="25f46-226">Tento příkaz je možné využít v mnoha různých scénářích.</span><span class="sxs-lookup"><span data-stu-id="25f46-226">This command has many overloads to cover various scenarios</span></span>
    + <span data-ttu-id="25f46-227">Remove-AzureRmServiceFabricClientCertificate: Odebere klientskému certifikátu možnost přístupu ke clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-227">Remove-AzureRmServiceFabricClientCertificate       Remove a client certificate from being used to access a cluster</span></span>
    + <span data-ttu-id="25f46-228">Remove-AzureRmServiceFabricClusterCertificate: Odebere certifikátu clusteru možnost použití pro zabezpečení clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-228">Remove-AzureRmServiceFabricClusterCertificate       Remove a cluster certificate from being used for cluster security</span></span>
    + <span data-ttu-id="25f46-229">Remove-AzureRmServiceFabricNodes: Odebere uzly z konkrétního typu uzlu z clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-229">Remove-AzureRmServiceFabricNodes       Remove nodes from a specific node type from a cluster</span></span>
    + <span data-ttu-id="25f46-230">Remove-AzureRmServiceFabricNodeType: Odebere typ uzlu z clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-230">Remove-AzureRmServiceFabricNodeType       Remove a node type from a cluster</span></span>
    + <span data-ttu-id="25f46-231">Remove-AzureRmServiceFabricSettings: Odebere minimálně jedno nastavení ServiceFabric z clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-231">Remove-AzureRmServiceFabricSettings       Remove one or more ServiceFabric settings from a cluster</span></span>
    + <span data-ttu-id="25f46-232">Set-AzureRmServiceFabricSettings: Přidá nebo aktualizuje minimálně jedno nastavení clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-232">Set-AzureRmServiceFabricSettings       Add or update one or more ServiceFabric settings of a cluster</span></span>
    + <span data-ttu-id="25f46-233">Set-AzureRmServiceFabricUpgradeType: Změní typ upgradu ServiceFabric clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-233">Set-AzureRmServiceFabricUpgradeType       Change the ServiceFabric upgrade type of a cluster</span></span>
    + <span data-ttu-id="25f46-234">Update-AzureRmServiceFabricDurability: Změní úroveň odolnosti clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-234">Update-AzureRmServiceFabricDurability       Change the durability tier of a cluster</span></span>
    + <span data-ttu-id="25f46-235">Update-AzureRmServiceFabricReliability: Změní úroveň spolehlivosti clusteru.</span><span class="sxs-lookup"><span data-stu-id="25f46-235">Update-AzureRmServiceFabricReliability       Change the reliability tier of a cluster</span></span>
* <span data-ttu-id="25f46-236">Sql</span><span class="sxs-lookup"><span data-stu-id="25f46-236">Sql</span></span>
  - <span data-ttu-id="25f46-237">Přidání parametru -SampleName do New-AzureRmSqlDatabase</span><span class="sxs-lookup"><span data-stu-id="25f46-237">Added -SampleName parameter to New-AzureRmSqlDatabase</span></span>
  - <span data-ttu-id="25f46-238">Aktualizace rutin skupin převzetí služeb při selhání</span><span class="sxs-lookup"><span data-stu-id="25f46-238">Updates to Failover Group cmdlets</span></span>
  - <span data-ttu-id="25f46-239">Odebrání parametrů Tag</span><span class="sxs-lookup"><span data-stu-id="25f46-239">Remove 'Tag' parameters</span></span>
  - <span data-ttu-id="25f46-240">Odebrání parametrů PartnerResourceGroupName a PartnerServerName z rutiny Remove-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="25f46-240">Remove 'PartnerResourceGroupName' and 'PartnerServerName' parameters from Remove-AzureRmSqlDatabaseFailoverGroup cmdlet</span></span>
  - <span data-ttu-id="25f46-241">Přidání parametru GracePeriodWithDataLossHours do rutin New- a Set-, který nakonec nahradí parametr GracePeriodWithDataLossHour</span><span class="sxs-lookup"><span data-stu-id="25f46-241">Add 'GracePeriodWithDataLossHours' parameter to New- and Set- cmdlets, which shall eventually replace 'GracePeriodWithDataLossHour'</span></span>
  - <span data-ttu-id="25f46-242">Doplnění a aktualizace dokumentace</span><span class="sxs-lookup"><span data-stu-id="25f46-242">Documentation has been fleshed out and updated</span></span>
  - <span data-ttu-id="25f46-243">Změna formátování vrácených objektů a oprava některých chyb s občasným nenaplňováním polí</span><span class="sxs-lookup"><span data-stu-id="25f46-243">Change formatting of returned objects and fix some bugs where fields were not always populated</span></span>
  - <span data-ttu-id="25f46-244">Přidání vlastností DatabaseNames a PartnerLocation do objektu skupiny převzetí služeb při selhání</span><span class="sxs-lookup"><span data-stu-id="25f46-244">Add 'DatabaseNames' and 'PartnerLocation' properties to Failover Group object</span></span>
  - <span data-ttu-id="25f46-245">Oprava chyby, která způsobovala, že rutina Switch- vracela výsledky okamžitě, aniž by počkala na dokončení operace</span><span class="sxs-lookup"><span data-stu-id="25f46-245">Fix bug causing Switch- cmdlet to return immediately rather than waiting for operation to complete</span></span>
  - <span data-ttu-id="25f46-246">Oprava chyby s přetečením celého čísla při použití vysokých hodnot období odkladu</span><span class="sxs-lookup"><span data-stu-id="25f46-246">Fix integer overflow bug when high grace period values are used</span></span>
  - <span data-ttu-id="25f46-247">Možnost úpravy období odkladu na minimálně 1 hodinu, pokud je zadána nižší hodnota</span><span class="sxs-lookup"><span data-stu-id="25f46-247">Adjust grace period to a minimum of 1 hour if a lower one is provided</span></span>
  - <span data-ttu-id="25f46-248">Odebrání hodnoty Usage_Anomaly z akceptovaných hodnot parametru ExcludedDetectionType v rutině Set-AzureRmSqlDatabaseThreatDetectionPolicy a rutině Set-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="25f46-248">Remove "Usage_Anomaly" from the accepted values for "ExcludedDetectionType" parameter of Set-AzureRmSqlDatabaseThreatDetectionPolicy cmdlet and Set-AzureRmSqlServerThreatDetectionPolicy cmdlet.</span></span>
* <span data-ttu-id="25f46-249">Úložiště</span><span class="sxs-lookup"><span data-stu-id="25f46-249">Storage</span></span>
  - <span data-ttu-id="25f46-250">Upgrade sady SRP SDK na 6.3.0</span><span class="sxs-lookup"><span data-stu-id="25f46-250">Upgrade SRP SDK to 6.3.0</span></span>
  - <span data-ttu-id="25f46-251">New/Set-AzureRmStorageAccount: Přidá nový parametr pro podporu atributu EnableHttpsTrafficOnly.</span><span class="sxs-lookup"><span data-stu-id="25f46-251">New/Set-AzureRmStorageAccount:Add a new parameter to support EnableHttpsTrafficOnly</span></span>
  - <span data-ttu-id="25f46-252">New/Set/Get-AzureRmStorageAccount: Vrácený účet úložiště obsahuje nový atribut EnableHttpsTrafficOnly.</span><span class="sxs-lookup"><span data-stu-id="25f46-252">New/Set/Get-AzureRmStorageAccount: Returned Storage Account contains a new attribute EnableHttpsTrafficOnly</span></span>
* <span data-ttu-id="25f46-253">Azure.Storage</span><span class="sxs-lookup"><span data-stu-id="25f46-253">Azure.Storage</span></span>
  - <span data-ttu-id="25f46-254">Upgrade na Azure Storage Client Library 8.1.1 a Azure Storage DataMovement Library 0.5.1</span><span class="sxs-lookup"><span data-stu-id="25f46-254">Upgrade to Azure Storage Client Library 8.1.1 and Azure Storage DataMovement Library 0.5.1</span></span>
  - <span data-ttu-id="25f46-255">Přidání nové rutiny pro podporu funkce vytváření přírůstkových kopií objektu blob</span><span class="sxs-lookup"><span data-stu-id="25f46-255">Add a new cmdlet to support blob Incremental Copy feature</span></span>
