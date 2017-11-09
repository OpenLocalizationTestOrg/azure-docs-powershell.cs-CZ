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
# <a name="release-notes"></a>Poznámky k verzi

Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.

## <a name="version-170"></a>Verze 1.7.0

* **Změnili jsme chování parametrů -Force, -Confirm a $ConfirmPreference pro všechny rutiny. Měníme tuto implementaci, aby byla v souladu s pokyny PowerShellu. U většiny rutin to znamená odebrání parametru Force a přeskočení řádku ShouldProcess. Uživatelé budou muset do skriptů PowerShellu zahrnout parametr -Confirm:$false.** Tato změna řeší následující problémy:
  - Správná implementace funkce –WhatIf, která uživatelům umožňuje zjistit dopady rutiny nebo skriptu, aniž by bylo potřeba provádět vlastní změny.
  - Kontrola nad zobrazením výzvy s využitím $ConfirmPreference na úrovni celé relace. Uživateli se zobrazí výzva v závislosti na dopadu případné změny (popsáno v příslušné rutině u nastavení ConfirmImpact).
  - Kontrola nad výzvami k potvrzení pro konkrétní rutiny s využitím parametru –Confirm.
  - Konzistentní použití parametrů ShouldContinue a -Force napříč rutinami jenom pro akce, které by vyžadovaly výzvy k potvrzení od uživatele vzhledem ke speciální povaze změn (například odstranění skrytých souborů).
  - Konzistence s ostatními rutinami prostředí PowerShell, aby se znalost skriptování PowerShellu z ostatních rutin dala okamžitě využít pro rutiny Azure PowerShellu.

**Všimněte si, že pro *automatické přeskočení všech výzev za všech okolností* rutiny Azure PowerShellu teď vyžadují, aby uživatel zadal dva parametry:**
```powershell
My-CmdletWithConfirmation –Confirm:$false -Force
```
* Azure Compute
  - Set-AzureRmVMADDomainExtension
  - Get-AzureRmVMADDomainExtension
  - Parametr -Redeploy pro Restart-AzureVM
  - Parametr -Validate pro Move-AzureService, Move-AzureStorageAccount a Move-AzureVirtualNetwork
  - Parametry názvu a verze pro rutiny rozšíření jsou stejně jako dřív nepovinné.
  - New-AzureVM může získat typ licence z objektu virtuálního počítače.
* Azure Storage
  - Změna parametru Tags na Tag a přidání aliasu parametru Tags
    + New-AzureRmStorageAccount
    + Set-AzureRmStorageAccount
* Síť Azure
  - Přidání nové rutiny pro partnerské vztahy virtuálních sítí
* Azure Redis Cache
  - Přidání nové rutiny pro Reset-AzureRmRedisCache
  - Přidání nové rutiny pro Export-AzureRmRedisCache
  - Přidání nové rutiny pro Import-AzureRmRedisCache
  - Úprava rutiny New-AzureRmRedisCache a zahrnutí změny parametru pro virtuální síť
* Zálohování a obnovení Azure SQL DB
  - Rutiny pro zálohovací funkci LTR (dlouhodobé uchování)
  - Get-AzureRmSqlServerBackupLongTermRetentionVault
  - Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy
  - Set-AzureRmSqlServerBackupLongTermRetentionVault
  - Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy
  - Nová podpora obnovení odstraněné databáze k určitému bodu v čase pro Restore-AzureRmSqlDatabase
  - Nová podpora obnovení ze zálohy s dlouhodobým uchováním pro Restore-AzureRmSqlDatabase
* Azure LogicApp
  - Přidání rutin účtů integrace LogicApp
  - Get-AzureRmIntegrationAccountAgreement
  - Get-AzureRmIntegrationAccountCallbackUrl
  - Get-AzureRmIntegrationAccountCertificate
  - Get-AzureRmIntegrationAccount
  - Get-AzureRmIntegrationAccountMap
  - Get-AzureRmIntegrationAccountPartner
  - Get-AzureRmIntegrationAccountSchema
  - New-AzureRmIntegrationAccountAgreement
  - New-AzureRmIntegrationAccountCertificate
  - New-AzureRmIntegrationAccount
  - New-AzureRmIntegrationAccountMap
  - New-AzureRmIntegrationAccountPartner
  - New-AzureRmIntegrationAccountSchema
  - Remove-AzureRmIntegrationAccountAgreement
  - Remove-AzureRmIntegrationAccountCertificate
  - Remove-AzureRmIntegrationAccount
  - Remove-AzureRmIntegrationAccountMap
  - Remove-AzureRmIntegrationAccountPartner
  - Remove-AzureRmIntegrationAccountSchema
  - Set-AzureRmIntegrationAccountAgreement
  - Set-AzureRmIntegrationAccountCertificate
  - Set-AzureRmIntegrationAccount
  - Set-AzureRmIntegrationAccountMap
  - Set-AzureRmIntegrationAccountPartner
  - Set-AzureRmIntegrationAccountSchema
* Azure Data Lake Store
  - Výrazně se vylepšil výkon nahrávání a stahování složek a souborů.
  - To zahrnuje i drobnou změnu názvů parametrů pro stahování a dva nové parametry pro nahrávání:
    + NumThreads -> PerFileThreadCount. Slouží k určení počtu vláken pro použití v jednom souboru.
    + ConcurrentFileCount. Slouží k určení počtu souborů pro paralelní stahování a nahrávání při stahování a nahrávání složek.
  - Výchozí hodnoty pro použití vláken jsou teď navržené tak, aby poskytovaly lepší propustnost pro většinu velikostí souborů. Pokud výkon neodpovídá potřebám, je možné výše uvedené hodnoty upravit a zajistit splnění požadavků.
* Azure Data Lake Analytics
  - Get-AzureRMDataLakeAnalyticsDataSource teď při volání bez argumentů vrací všechny zdroje dat.
  - Kvůli této změně se také z rutiny odebral parametr typu zdroje.
  - Tato změna má za následek vrácení nového objektu pro operace seznamu s následujícími vlastnostmi:
    + Type (typ zdroje dat)
    + Name (název zdroje dat)
    + IsDefault (pro výchozí zdroj dat příslušného účtu nastavené na hodnotu true)
  - Opravili jsme Get-AzureRMDataLakeAnalyticsJob, aby se při filtrování podle submittedBefore a submittedAfter vracel seznam konkrétních hodnot posunu data a času.
* Web Apps
  - Přidání rutiny Add Swap-AzureRmWebAppSlot pro běžné prohození a prohození s náhledem
  - Rozšíření rutiny Extend Set-AzureRmWebAppSlot o podporu pro automatické prohození
* Azure API Management
  - Oprava rutin nasazení správy rozhraní Azure API pro AzureChinaCloud
  - Odebrání rutiny Set-AzureRmApiManagementTenantGitAccess, protože přístup ke Gitu je ve výchozím nastavení povolený
* Zálohování pomocí služby Azure Recovery Services
  - Přidání podpory pro úlohy Azure SQL
  - Přidání podpory pro zálohování a obnovení šifrovaných virtuálních počítačů Azure
  - Backup-AzureRmRecoveryServicesBackupItem – přidání funkce volitelného času uchování pro body obnovení
  - Opravy malých chyb souvisejících s filtrováním v rutinách Get-AzureRmRecoveryServicesBackupContainer a Get-AzureRmRecoveryServicesBackupItem
* Azure Automation
  - Přidání Get-AzureRmAutomationHybridWorkerGroup
