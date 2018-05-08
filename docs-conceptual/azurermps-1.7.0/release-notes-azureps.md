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
ms.openlocfilehash: 0a3f152751fee569d3ac5fba6bcff8c1737f7b8c
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a><span data-ttu-id="4f0b8-103">Poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="4f0b8-103">Release notes</span></span>

<span data-ttu-id="4f0b8-104">Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <a name="version-170"></a><span data-ttu-id="4f0b8-105">Verze 1.7.0</span><span class="sxs-lookup"><span data-stu-id="4f0b8-105">Version 1.7.0</span></span>

* <span data-ttu-id="4f0b8-106">**Změnili jsme chování parametrů -Force, -Confirm a $ConfirmPreference pro všechny rutiny. Měníme tuto implementaci, aby byla v souladu s pokyny PowerShellu. U většiny rutin to znamená odebrání parametru Force a přeskočení řádku ShouldProcess. Uživatelé budou muset do skriptů PowerShellu zahrnout parametr -Confirm:$false.**</span><span class="sxs-lookup"><span data-stu-id="4f0b8-106">**Behavioral change for -Force, –Confirm and $ConfirmPreference parameters for all cmdlets. We are changing this implementation to be in line with PowerShell guidelines. For most cmdlets, this means removing the Force parameter and to skip the ShouldProcess prompt, users will need to include the parameter: ‘-Confirm:$false’ in their PowerShell scripts.**</span></span> <span data-ttu-id="4f0b8-107">Tato změna řeší následující problémy:</span><span class="sxs-lookup"><span data-stu-id="4f0b8-107">This changes are addressing following issues:</span></span>
  - <span data-ttu-id="4f0b8-108">Správná implementace funkce –WhatIf, která uživatelům umožňuje zjistit dopady rutiny nebo skriptu, aniž by bylo potřeba provádět vlastní změny.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-108">Correct implementation of –WhatIf functionality, allowing a user to determine the effects of a cmdlet or script without making any actual changes</span></span>
  - <span data-ttu-id="4f0b8-109">Kontrola nad zobrazením výzvy s využitím $ConfirmPreference na úrovni celé relace. Uživateli se zobrazí výzva v závislosti na dopadu případné změny (popsáno v příslušné rutině u nastavení ConfirmImpact).</span><span class="sxs-lookup"><span data-stu-id="4f0b8-109">Control over prompting using a session-wide $ConfirmPreference, so that the user is prompted based on the impact of a prospective change (as reported in the ConfirmImpact setting in the cmdlet)</span></span>
  - <span data-ttu-id="4f0b8-110">Kontrola nad výzvami k potvrzení pro konkrétní rutiny s využitím parametru –Confirm.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-110">Cmdlet-specific control over confirmation prompts using the –Confirm parameter</span></span>
  - <span data-ttu-id="4f0b8-111">Konzistentní použití parametrů ShouldContinue a -Force napříč rutinami jenom pro akce, které by vyžadovaly výzvy k potvrzení od uživatele vzhledem ke speciální povaze změn (například odstranění skrytých souborů).</span><span class="sxs-lookup"><span data-stu-id="4f0b8-111">Consistent use of ShouldContinue and the –Force parameter across cmdlets, for only those actions that would require prompting from the user due to the special nature of the changes (for example, deleting hidden files)</span></span>
  - <span data-ttu-id="4f0b8-112">Konzistence s ostatními rutinami prostředí PowerShell, aby se znalost skriptování PowerShellu z ostatních rutin dala okamžitě využít pro rutiny Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-112">Consistency with other PowerShell cmdlets, so that PowerShell scripting knowledge from other cmdlets is immediately applicable to the Azure PowerShell cmdlets.</span></span>

<span data-ttu-id="4f0b8-113">**Všimněte si, že pro *automatické přeskočení všech výzev za všech okolností* rutiny Azure PowerShellu teď vyžadují, aby uživatel zadal dva parametry:**</span><span class="sxs-lookup"><span data-stu-id="4f0b8-113">**Notice that now to *automatically skip all Prompts in all Circumstances* Azure PowerShell cmdlets require the user to supply two parameters:**</span></span>
```powershell
My-CmdletWithConfirmation –Confirm:$false -Force
```
* <span data-ttu-id="4f0b8-114">Azure Compute</span><span class="sxs-lookup"><span data-stu-id="4f0b8-114">Azure Compute</span></span>
  - <span data-ttu-id="4f0b8-115">Set-AzureRmVMADDomainExtension</span><span class="sxs-lookup"><span data-stu-id="4f0b8-115">Set-AzureRmVMADDomainExtension</span></span>
  - <span data-ttu-id="4f0b8-116">Get-AzureRmVMADDomainExtension</span><span class="sxs-lookup"><span data-stu-id="4f0b8-116">Get-AzureRmVMADDomainExtension</span></span>
  - <span data-ttu-id="4f0b8-117">Parametr -Redeploy pro Restart-AzureVM</span><span class="sxs-lookup"><span data-stu-id="4f0b8-117">-Redeploy parameter for Restart-AzureVM</span></span>
  - <span data-ttu-id="4f0b8-118">Parametr -Validate pro Move-AzureService, Move-AzureStorageAccount a Move-AzureVirtualNetwork</span><span class="sxs-lookup"><span data-stu-id="4f0b8-118">-Validate parameter for Move-AzureService, Move-AzureStorageAccount, and Move-AzureVirtualNetwork</span></span>
  - <span data-ttu-id="4f0b8-119">Parametry názvu a verze pro rutiny rozšíření jsou stejně jako dřív nepovinné.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-119">Name and version parameters for extension cmdlets are optional as before.</span></span>
  - <span data-ttu-id="4f0b8-120">New-AzureVM může získat typ licence z objektu virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-120">New-AzureVM can get a license type from VM object.</span></span>
* <span data-ttu-id="4f0b8-121">Azure Storage</span><span class="sxs-lookup"><span data-stu-id="4f0b8-121">Azure Storage</span></span>
  - <span data-ttu-id="4f0b8-122">Změna parametru Tags na Tag a přidání aliasu parametru Tags</span><span class="sxs-lookup"><span data-stu-id="4f0b8-122">Change Tags Parameter to Tag, and add parameter alias Tags</span></span>
    + <span data-ttu-id="4f0b8-123">New-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="4f0b8-123">New-AzureRmStorageAccount</span></span>
    + <span data-ttu-id="4f0b8-124">Set-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="4f0b8-124">Set-AzureRmStorageAccount</span></span>
* <span data-ttu-id="4f0b8-125">Síť Azure</span><span class="sxs-lookup"><span data-stu-id="4f0b8-125">Azure Network</span></span>
  - <span data-ttu-id="4f0b8-126">Přidání nové rutiny pro partnerské vztahy virtuálních sítí</span><span class="sxs-lookup"><span data-stu-id="4f0b8-126">New cmdlet added for Virtual Network Peering</span></span>
* <span data-ttu-id="4f0b8-127">Azure Redis Cache</span><span class="sxs-lookup"><span data-stu-id="4f0b8-127">Azure Redis Cache</span></span>
  - <span data-ttu-id="4f0b8-128">Přidání nové rutiny pro Reset-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="4f0b8-128">New cmdlet added for Reset-AzureRmRedisCache</span></span>
  - <span data-ttu-id="4f0b8-129">Přidání nové rutiny pro Export-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="4f0b8-129">New cmdlet added for Export-AzureRmRedisCache</span></span>
  - <span data-ttu-id="4f0b8-130">Přidání nové rutiny pro Import-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="4f0b8-130">New cmdlet added for Import-AzureRmRedisCache</span></span>
  - <span data-ttu-id="4f0b8-131">Úprava rutiny New-AzureRmRedisCache a zahrnutí změny parametru pro virtuální síť</span><span class="sxs-lookup"><span data-stu-id="4f0b8-131">Modified cmdlet New-AzureRmRedisCache to include parameter change for vNet</span></span>
* <span data-ttu-id="4f0b8-132">Zálohování a obnovení Azure SQL DB</span><span class="sxs-lookup"><span data-stu-id="4f0b8-132">Azure SQL DB Backup/Restore</span></span>
  - <span data-ttu-id="4f0b8-133">Rutiny pro zálohovací funkci LTR (dlouhodobé uchování)</span><span class="sxs-lookup"><span data-stu-id="4f0b8-133">Cmdlets for LTR (Long Term Retention) backup feature</span></span>
  - <span data-ttu-id="4f0b8-134">Get-AzureRmSqlServerBackupLongTermRetentionVault</span><span class="sxs-lookup"><span data-stu-id="4f0b8-134">Get-AzureRmSqlServerBackupLongTermRetentionVault</span></span>
  - <span data-ttu-id="4f0b8-135">Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span><span class="sxs-lookup"><span data-stu-id="4f0b8-135">Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span></span>
  - <span data-ttu-id="4f0b8-136">Set-AzureRmSqlServerBackupLongTermRetentionVault</span><span class="sxs-lookup"><span data-stu-id="4f0b8-136">Set-AzureRmSqlServerBackupLongTermRetentionVault</span></span>
  - <span data-ttu-id="4f0b8-137">Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span><span class="sxs-lookup"><span data-stu-id="4f0b8-137">Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span></span>
  - <span data-ttu-id="4f0b8-138">Nová podpora obnovení odstraněné databáze k určitému bodu v čase pro Restore-AzureRmSqlDatabase</span><span class="sxs-lookup"><span data-stu-id="4f0b8-138">Restore-AzureRmSqlDatabase now supports point-in-time restore of a deleted database</span></span>
  - <span data-ttu-id="4f0b8-139">Nová podpora obnovení ze zálohy s dlouhodobým uchováním pro Restore-AzureRmSqlDatabase</span><span class="sxs-lookup"><span data-stu-id="4f0b8-139">Restore-AzureRmSqlDatabase now supports restoring from a Long Term Retention backup</span></span>
* <span data-ttu-id="4f0b8-140">Azure LogicApp</span><span class="sxs-lookup"><span data-stu-id="4f0b8-140">Azure LogicApp</span></span>
  - <span data-ttu-id="4f0b8-141">Přidání rutin účtů integrace LogicApp</span><span class="sxs-lookup"><span data-stu-id="4f0b8-141">Added LogicApp Integration accounts cmdlets.</span></span>
  - <span data-ttu-id="4f0b8-142">Get-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="4f0b8-142">Get-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="4f0b8-143">Get-AzureRmIntegrationAccountCallbackUrl</span><span class="sxs-lookup"><span data-stu-id="4f0b8-143">Get-AzureRmIntegrationAccountCallbackUrl</span></span>
  - <span data-ttu-id="4f0b8-144">Get-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="4f0b8-144">Get-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="4f0b8-145">Get-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="4f0b8-145">Get-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="4f0b8-146">Get-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="4f0b8-146">Get-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="4f0b8-147">Get-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="4f0b8-147">Get-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="4f0b8-148">Get-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="4f0b8-148">Get-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="4f0b8-149">New-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="4f0b8-149">New-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="4f0b8-150">New-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="4f0b8-150">New-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="4f0b8-151">New-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="4f0b8-151">New-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="4f0b8-152">New-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="4f0b8-152">New-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="4f0b8-153">New-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="4f0b8-153">New-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="4f0b8-154">New-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="4f0b8-154">New-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="4f0b8-155">Remove-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="4f0b8-155">Remove-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="4f0b8-156">Remove-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="4f0b8-156">Remove-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="4f0b8-157">Remove-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="4f0b8-157">Remove-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="4f0b8-158">Remove-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="4f0b8-158">Remove-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="4f0b8-159">Remove-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="4f0b8-159">Remove-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="4f0b8-160">Remove-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="4f0b8-160">Remove-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="4f0b8-161">Set-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="4f0b8-161">Set-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="4f0b8-162">Set-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="4f0b8-162">Set-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="4f0b8-163">Set-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="4f0b8-163">Set-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="4f0b8-164">Set-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="4f0b8-164">Set-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="4f0b8-165">Set-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="4f0b8-165">Set-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="4f0b8-166">Set-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="4f0b8-166">Set-AzureRmIntegrationAccountSchema</span></span>
* <span data-ttu-id="4f0b8-167">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="4f0b8-167">Azure Data Lake Store</span></span>
  - <span data-ttu-id="4f0b8-168">Výrazně se vylepšil výkon nahrávání a stahování složek a souborů.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-168">Drastically improve performance of file and folder upload and download.</span></span>
  - <span data-ttu-id="4f0b8-169">To zahrnuje i drobnou změnu názvů parametrů pro stahování a dva nové parametry pro nahrávání:</span><span class="sxs-lookup"><span data-stu-id="4f0b8-169">This includes a slight change to the parameter names for download and inclusion of two new parameters for upload:</span></span>
    + <span data-ttu-id="4f0b8-170">NumThreads -> PerFileThreadCount. Slouží k určení počtu vláken pro použití v jednom souboru.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-170">NumThreads -> PerFileThreadCount, used to indicate the number of threads to use in a single file</span></span>
    + <span data-ttu-id="4f0b8-171">ConcurrentFileCount. Slouží k určení počtu souborů pro paralelní stahování a nahrávání při stahování a nahrávání složek.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-171">ConcurrentFileCount, used to indicate the number of files to upload/download in parallel for folder upload/download.</span></span>
  - <span data-ttu-id="4f0b8-172">Výchozí hodnoty pro použití vláken jsou teď navržené tak, aby poskytovaly lepší propustnost pro většinu velikostí souborů.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-172">Default threading values are now designed to give a better all around throughput for most file sizes.</span></span> <span data-ttu-id="4f0b8-173">Pokud výkon neodpovídá potřebám, je možné výše uvedené hodnoty upravit a zajistit splnění požadavků.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-173">If performance is not as desired, the values above can be modified to meet requirements.</span></span>
* <span data-ttu-id="4f0b8-174">Azure Data Lake Analytics</span><span class="sxs-lookup"><span data-stu-id="4f0b8-174">Azure Data Lake Analytics</span></span>
  - <span data-ttu-id="4f0b8-175">Get-AzureRMDataLakeAnalyticsDataSource teď při volání bez argumentů vrací všechny zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-175">Get-AzureRMDataLakeAnalyticsDataSource now returns all data sources when called with no arguments.</span></span>
  - <span data-ttu-id="4f0b8-176">Kvůli této změně se také z rutiny odebral parametr typu zdroje.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-176">This change also removes the data source type parameter from the cmdlet.</span></span>
  - <span data-ttu-id="4f0b8-177">Tato změna má za následek vrácení nového objektu pro operace seznamu s následujícími vlastnostmi:</span><span class="sxs-lookup"><span data-stu-id="4f0b8-177">This change results in a new object being returned for the list operation with the following properties:</span></span>
    + <span data-ttu-id="4f0b8-178">Type (typ zdroje dat)</span><span class="sxs-lookup"><span data-stu-id="4f0b8-178">Type, the type of data source</span></span>
    + <span data-ttu-id="4f0b8-179">Name (název zdroje dat)</span><span class="sxs-lookup"><span data-stu-id="4f0b8-179">Name, the name of the data source</span></span>
    + <span data-ttu-id="4f0b8-180">IsDefault (pro výchozí zdroj dat příslušného účtu nastavené na hodnotu true)</span><span class="sxs-lookup"><span data-stu-id="4f0b8-180">IsDefault, set to true if this is the default data source for the account</span></span>
  - <span data-ttu-id="4f0b8-181">Opravili jsme Get-AzureRMDataLakeAnalyticsJob, aby se při filtrování podle submittedBefore a submittedAfter vracel seznam konkrétních hodnot posunu data a času.</span><span class="sxs-lookup"><span data-stu-id="4f0b8-181">Get-AzureRMDataLakeAnalyticsJob fixed for list for certain date time offset values when filtering on submittedBefore and submittedAfter.</span></span>
* <span data-ttu-id="4f0b8-182">Web Apps</span><span class="sxs-lookup"><span data-stu-id="4f0b8-182">Web Apps</span></span>
  - <span data-ttu-id="4f0b8-183">Přidání rutiny Add Swap-AzureRmWebAppSlot pro běžné prohození a prohození s náhledem</span><span class="sxs-lookup"><span data-stu-id="4f0b8-183">Add Swap-AzureRmWebAppSlot cmdlet for regular swap and swap with preview</span></span>
  - <span data-ttu-id="4f0b8-184">Rozšíření rutiny Extend Set-AzureRmWebAppSlot o podporu pro automatické prohození</span><span class="sxs-lookup"><span data-stu-id="4f0b8-184">Extend Set-AzureRmWebAppSlot cmdlet to support auto swap</span></span>
* <span data-ttu-id="4f0b8-185">Azure API Management</span><span class="sxs-lookup"><span data-stu-id="4f0b8-185">Azure API Management</span></span>
  - <span data-ttu-id="4f0b8-186">Oprava rutin nasazení správy rozhraní Azure API pro AzureChinaCloud</span><span class="sxs-lookup"><span data-stu-id="4f0b8-186">Fixed Azure Api Management Deployment cmdlets for AzureChinaCloud.</span></span>
  - <span data-ttu-id="4f0b8-187">Odebrání rutiny Set-AzureRmApiManagementTenantGitAccess, protože přístup ke Gitu je ve výchozím nastavení povolený</span><span class="sxs-lookup"><span data-stu-id="4f0b8-187">Removed cmdlet Set-AzureRmApiManagementTenantGitAccess as Git Access is enabled by Default.</span></span>
* <span data-ttu-id="4f0b8-188">Zálohování pomocí služby Azure Recovery Services</span><span class="sxs-lookup"><span data-stu-id="4f0b8-188">Azure Recovery Services Backup</span></span>
  - <span data-ttu-id="4f0b8-189">Přidání podpory pro úlohy Azure SQL</span><span class="sxs-lookup"><span data-stu-id="4f0b8-189">Added support for the Azure SQL workload</span></span>
  - <span data-ttu-id="4f0b8-190">Přidání podpory pro zálohování a obnovení šifrovaných virtuálních počítačů Azure</span><span class="sxs-lookup"><span data-stu-id="4f0b8-190">Added support for backing up and restoring encrypted Azure VMs</span></span>
  - <span data-ttu-id="4f0b8-191">Backup-AzureRmRecoveryServicesBackupItem – přidání funkce volitelného času uchování pro body obnovení</span><span class="sxs-lookup"><span data-stu-id="4f0b8-191">Backup-AzureRmRecoveryServicesBackupItem - Added optional retention time feature for recovery points</span></span>
  - <span data-ttu-id="4f0b8-192">Opravy malých chyb souvisejících s filtrováním v rutinách Get-AzureRmRecoveryServicesBackupContainer a Get-AzureRmRecoveryServicesBackupItem</span><span class="sxs-lookup"><span data-stu-id="4f0b8-192">Minor filter-related bug fixes in Get-AzureRmRecoveryServicesBackupContainer and Get-AzureRmRecoveryServicesBackupItem cmdlets</span></span>
* <span data-ttu-id="4f0b8-193">Azure Automation</span><span class="sxs-lookup"><span data-stu-id="4f0b8-193">Azure Automation</span></span>
  - <span data-ttu-id="4f0b8-194">Přidání Get-AzureRmAutomationHybridWorkerGroup</span><span class="sxs-lookup"><span data-stu-id="4f0b8-194">Added Get-AzureRmAutomationHybridWorkerGroup</span></span>
