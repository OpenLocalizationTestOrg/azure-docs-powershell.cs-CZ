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
ms.date: 11/14/2017
ms.openlocfilehash: cf58789ba69fd2fc157e37d0b052827b361246e5
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="release-notes"></a>Poznámky k verzi

Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.

## <a name="20171208-version-511"></a>8. prosince 2017 – verze 5.1.1
* AnalysisServices
    - Změna ověření sady umístění na dynamické vyhledávání, takže se podporují všechny cloudy
* Automation
    - Aktualizace pro Import-AzureRMAutomationRunbook
        - Podpora se nyní poskytuje pro runbooky Python2.
* Batch
    - Oprava chyby, kdy operace účtu bez skupiny prostředků selhaly při automatickém ověřování skupiny prostředků
* Compute
    - Get-AzureRmComputeResourceSku zobrazuje informace o zóně.
    - Aktualizovaná rutina Disable-AzureRmVmssDiskEncryption pro opravu potíží https://github.com/Azure/azure-powershell/issues/5038
    - Přidání podpory -AsJob pro dlouho běžící výpočetní rutiny. Umožňuje vybraným rutinám, aby běžely na pozadí, a vrací úlohu pro sledování a řízení průběhu.
        - Ovlivněné rutiny: Rutiny New-, Update-, Set-, Remove-, Start-, Restart-, Stop- pro virtuální počítače a škálovací sady virtuálních počítačů
    - Přidání zjednodušené sady parametrů do New-AzureRmVM, která vytvoří virtuální počítač a všechny požadované prostředky s využitím inteligentních výchozích hodnot
* ContainerInstance
    - Použití sady Azure Container Instance SDK z 1. října 2017
        - Podpora run-to-completion pro kontejnery
        - Podpora připojení svazku služby Soubory Azure
        - Podpora otevření více portů pro veřejnou IP adresu
* ContainerRegistry
    - Nové rutiny pro geografickou replikaci a webhooky
        - Get/New/Remove-AzureRmContainerRegistryReplication
        - Get/New/Remove/Test/Update-AzureRmContainerRegistryWebhook
* DataFactory
    - Funkce ověřování šifrování teď funguje, když je vzdálený přístup povolený (přes síť) i zakázaný (místní počítač).
* DataFactoryV2
    - Přidání dvou nových rutin: Update-AzureRmDataFactoryV2 a Stop-AzureRmDataFactoryV2PipelineRun
* DataLakeAnalytics
    - Přidání parametru nazvaného ScriptParameter do Submit-AzureRmDataLakeAnalyticsJob
        - Podrobné informace o ScriptParameter získáte pomocí Get-Help v Submit-AzureRmDataLakeAnalyticsJob.
    - Změna parametru pro New-AzureRmDataLakeAnalyticsAccount z MaxDegreeOfParallelism na MaxAnalyticsUnits
        - Přidání aliasu pro parametr MaxAnalyticsUnits: MaxDegreeOfParallelism
    - Změna parametru pro New-AzureRmDataLakeAnalyticsComputePolicy z MaxDegreeOfParallelismPerJob na MaxAnalyticsUnitsPerJob
        - Přidání aliasu pro parametr MaxAnalyticsUnitsPerJob: MaxDegreeOfParallelismPerJob
    - Změna parametru pro Set-AzureRmDataLakeAnalyticsAccount z MaxDegreeOfParallelism na MaxAnalyticsUnits
        - Přidání aliasu pro parametr MaxAnalyticsUnits: MaxDegreeOfParallelism
    - Změna parametru pro Submit-AzureRmDataLakeAnalyticsJob z DegreeOfParallelism na AnalyticsUnits
        - Přidání aliasu pro parametr AnalyticsUnits: DegreeOfParallelism
    - Změna parametru pro Update-AzureRmDataLakeAnalyticsComputePolicy z MaxDegreeOfParallelismPerJob na MaxAnalyticsUnitsPerJob
        - Přidání aliasu pro parametr MaxAnalyticsUnitsPerJob: MaxDegreeOfParallelismPerJob
* MachineLearningCompute
    - Přidání Set-AzureRmMlOpCluster
        - Aktualizace konfigurace SSL nebo počtu agentů clusteru
    - Vlastnosti orchestrátoru nepovinné
        - Pokud objekt služby není k dispozici, služba ho vytvoří, takže vlastnosti orchestrátoru jsou teď nepovinné.
* PowerBIEmbedded
    - Přidání podpory pro rutiny Power BI Embedded Capacity
    - Nová rutina Get-AzureRmPowerBIEmbeddedCapacity: Získá podrobnosti o službě PowerBI Embedded Capacity.
    - Nová rutina New-AzureRmPowerBIEmbeddedCapacity: Vytvoří novou službu PowerBI Embedded Capacity.
    - Nová rutina Remove-AzureRmPowerBIEmbeddedCapacity: Odebere instanci služby PowerBI Embedded Capacity.
    - Nová rutina Resume-AzureRmPowerBIEmbeddedCapacity: Obnoví instanci služby PowerBI Embedded Capacity.
    - Nová rutina Suspend-AzureRmPowerBIEmbeddedCapacity: Pozastaví instanci služby PowerBI Embedded Capacity.
    - Nová rutina Test-AzureRmPowerBIEmbeddedCapacity: Otestuje existenci instance služby PowerBI Embedded Capacity.
    - Nová rutina Update-AzureRmPowerBIEmbeddedCapacity: Upraví instanci služby PowerBI Embedded Capacity.
* Profil
    - Aktualizace USGovernmentActiveDirectoryEndpoint na https://login.microsoftonline.us/
        - Další informace o mapování koncových bodů služby Azure Government najdete v tématu https://docs.microsoft.com/en-us/azure/azure-government/documentation-government-developer-guide#endpoint-mapping.
    - Přidání podpory -AsJob pro rutiny, umožňuje vybraným rutinám, aby spouštěly na pozadí, a vrací úlohu pro sledování a řízení průběhu
    - Přidání parametru -AsJob do rutiny Get-AzureRmSubscription
* RecoveryServices.Backup
    - Oprava chyby: Rutina Get-AzureRmRecoveryServicesBackupItem by měla pro filtrování názvu kontejneru používat porovnání bez rozlišení velkých a malých písmen.
    - Oprava chyby: AzureVmItem teď má vlastnost, která ukazuje čas posledního provedení operace zálohování – LastBackupTime.
* Zdroje
    - Oprava potíží, kdy Get-AzureRMRoleAssignment má za výsledek přiřazení bez názvu roledefinition pro vlastní role
        - Uživatelé teď můžou použít Get-AzureRMRoleAssignment pro přiřazení s názvy roledefinition bez ohledu na typ role.
    - Oprava potíží, kdy Set-AzureRMRoleRoleDefinition vracela chybu typu Definice role se nenašla, pokud v assignablescopes byl nový obor
        - Uživatelé teď můžou použít Set-AzureRMRoleRoleDefinition s přiřaditelnými obory včetně nových oborů bez ohledu na pozici oboru.
    - Povolení oborů končících na "/"
        - Uživatelé teď můžou používat rutiny RoleDefinition a RoleAssignment s obory končícími na "/" (konzistentně s rozhraním API a rozhraním příkazového řádku).
    - Povolení vytvářet RoleAssignment s využitím příznaku delegování
        - Uživatelé teď můžou použít New-AzureRMRoleAssignment s možností přidat příznak delegování.
    - Oprava pro RoleAssignment, aby se respektoval parametr oboru
    - Přidání aliasu pro ServicePrincipalName v rutině New-AzureRmRoleAssignment Commandlet
        - Uživatelé teď můžou při použití rutiny New-AzureRmRoleAssignment používat ApplicationId místo ServicePrincipalName.
* SiteRecovery
    - Přidání upozornění na zastaralost pro všechny rutiny v tomto modulu (v rámci přípravy na další vydání se zásadními změnami)
        - Další informace o migraci rutin z AzureRM najdete v průvodci chystanými zásadními změnami.
* Sql
    - Přidání možnosti přejmenovat databázi pomocí Set-AzureRmSqlDatabase
    - Oprava potíží https://github.com/Azure/azure-powershell/issues/4974
        - Poskytnutí neplatné hodnoty AUDIT_CHANGED_GROUP pro rutiny auditování už nevyvolá chybu a v chystaném vydání se odebere.
    - Oprava potíží https://github.com/Azure/azure-powershell/issues/5046
        - Parametr AuditAction v rutinách auditování se už neignoruje.
    - Oprava potíží v rutinách auditování při poskytnutí hodnoty Secondary pro StorageKeyType
        - Při nastavení auditování objektů blob se při poskytnutí hodnoty Secondary pro parametr StorageKeyType používal primární klíč účtu úložiště místo sekundárního klíče.
    - Změna formulace pro potvrzovací zprávu z Set-AzureRmSqlServerTransparentDataEncryptionProtector
* Azure (RDFE)
    - Odebrání všech rutin RemoteApp
* Azure.Storage
    - Upgrade na Azure Storage Client Library 8.6.0 a Azure Storage DataMovement Library 0.6.5

Změny od poslední verze: https://github.com/azure/azure-powershell/compare/v5.0.1-November2017...v5.1.1-December2017

## <a name="20171110-version-501"></a>10. listopadu 2017 – verze 5.0.1
* Oprava potíží s načítáním sestavení, které způsobovaly selhání některých rutin při spuštění v následujících modulech:
    - AzureRM.ApiManagement
    - AzureRM.Backup
    - AzureRM.Batch
    - AzureRM.Compute
    - AzureRM.DataFactories
    - AzureRM.HDInsight
    - AzureRM.KeyVault
    - AzureRM.RecoveryServices
    - AzureRM.RecoveryServices.Backup
    - AzureRM.RecoveryServices.SiteRecovery
    - AzureRM.RedisCache
    - AzureRM.SiteRecovery
    - AzureRM.Sql
    - AzureRM.Storage
    - AzureRM.StreamAnalytics

## <a name="2017118---version-500"></a>8. listopadu 2017 – verze 5.0.0
* POZNÁMKA: Toto je vydání se zásadními změnami. Kompletní seznam uvedených zásadních změn najdete v průvodci migrací (https://aka.ms/azps-migration-guide).
* Všechny rutiny v AzureRM teď s podporou online nápovědy
    - Spuštění Get-Help s parametrem -Online pro otevření online nápovědy ve výchozím internetovém prohlížeči
* AnalysisServices
    * Oprava příkazu Synchronize-AzureAsInstance tak, aby fungoval s novým rozhraním AsAzure REST API pro synchronizaci
* Správa rozhraní API
    * Zásadní změny pro ApiManagement v této vydané verzi viz průvodce migrací
    * Aktualizovaná rutina Get-AzureRmApiManagementUser pro opravu potíží https://github.com/Azure/azure-powershell/issues/4510
    * Aktualizovaná rutina New-AzureRmApiManagementApi pro vytvoření rozhraní API s prázdnou cestou https://github.com/Azure/azure-powershell/issues/4069
* ApplicationInsights
    * Přidání příkazů pro získání/vytvoření/odebrání prostředku Application Insights
        - Get-AzureRmApplicationInsights
        - New-AzureRmApplicationInsights
        - Remove-AzureRmApplicationInsights
    * Přidání příkazů pro získání/aktualizaci cen / denního objemu dat prostředku Application Insights
        - Get-AzureRmApplicationInsights -IncludeDailyCap
        - Set-AzureRmApplicationInsightsPricingPlan
        - Set-AzureRmApplicationInsightsDailyCap
    * Přidání příkazů pro získání/vytvoření/aktualizaci/odebrání průběžného exportu prostředku Application Insights
        - Get-AzureRmApplicationInsightsContinuousExport
        - Set-AzureRmApplicationInsightsContinuousExport
        - New-AzureRmApplicationInsightsContinuousExport
        - Remove-AzureRmApplicationInsightsContinuousExport
    * Přidání příkazů pro získání/vytvoření/odebrání klíčů API prostředku Application Insights
        - Get-AzureRmApplicationInsightsApiKey
        - New-AzureRmApplicationInsightsApiKey
        - Remove-AzureRmApplicationInsightsApiKey
* AzureBatch
    * Přidání nových parametrů do `New-AzureRmBatchAccount`
        - `PoolAllocationMode`: Režim přidělení pro použití při vytváření fondů v účtu Batch. Pokud chcete vytvořit účet Batch, který přiděluje uzly fondů v předplatném uživatele, použijte nastavení `UserSubscription`.
        - `KeyVaultId`: ID prostředku trezoru klíčů Azure přidruženého k účtu Batch
        - `KeyVaultUrl`: Adresa URL trezoru klíčů Azure přidruženého k účtu Batch
    * Aktualizace parametrů pro `New-AzureBatchTask`
        - Odebrání přepínače `RunElevated`. Přidání parametru `UserIdentity` pro nahrazení `RunElevated`. Ekvivalentního chování je možné dosáhnout konstrukcí `PSUserIdentity` znázorněnou níže:
            - $autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Task", "Admin")
            - $userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
        - Přidání parametru `AuthenticationTokenSettings`. Tento parametr umožňuje vyžádat, aby služba Batch poskytla úloze při spuštění ověřovací token, takže není nutné úloze předávat klíče účtu Batch, aby mohla vydávat žádosti do služby Batch.
        - Přidání parametru `ContainerSettings`.
            - Tento parametr umožňuje vyžádat, aby služba Batch spustila úlohu uvnitř kontejneru.
        - Přidání parametru `OutputFiles`.
            - Tento parametr umožňuje nakonfigurovat úlohu, aby po dokončení nahrála soubory do služby Azure Storage.
    * Aktualizace parametrů pro `New-AzureBatchPool`
        - Přidání parametru `UserAccounts`.
            - Tento parametr definuje uživatelské účty vytvořené v jednotlivých uzlech ve fondu.
        - Přidání `TargetLowPriorityComputeNodes` a přejmenování `TargetDedicated` na `TargetDedicatedComputeNodes`
            - Vytvoření aliasu `TargetDedicated` pro parametr `TargetDedicatedComputeNodes`
        - Přidání parametru `NetworkConfiguration`.
            - Tento parametr umožňuje nakonfigurovat síťové nastavení fondů.
    * Aktualizace parametrů pro `New-AzureBatchCertificate`
        - Parametr `Password` je teď `SecureString`.
    * Aktualizace parametrů pro `New-AzureBatchComputeNodeUser`
        - Parametr `Password` je teď `SecureString`.
    * Aktualizace parametrů pro `Set-AzureBatchComputeNodeUser`
        - Parametr `Password` je teď `SecureString`.
    * Přejmenování parametru `Name` na `Path` v `Get-AzureBatchNodeFile`, `Get-AzureBatchNodeFileContent` a `Remove-AzureBatchNodeFile`
        - Vytvoření aliasu `Name` pro parametr `Path`
    * Změny objektů
        - Kompletní seznam viz protokol změn služby Batch
    * Přidání podpory pro ověřování na základě služby Azure Active Directory
        - Pokud chcete použít ověřování pomocí Azure Active Directory, načtěte objekt `BatchAccountContext` pomocí rutiny `Get-AzureRmBatchAccount` a předejte tento objekt `BatchAccountContext` parametru `-BatchContext` rutiny služby Batch. Ověřování pomocí Azure Active Directory je povinné pro účty s `PoolAllocationMode = UserSubscription`.
        - Pro stávající účty nebo nové účty vytvořené pomocí `PoolAllocationMode = BatchService` můžete i nadále používat ověřování pomocí sdíleného klíče načtením objektu `BatchAccountContext` pomocí rutiny `Get-AzureRmBatchAccoutKeys`.
* Compute
    * Rozšiřující příkazy pro Azure Disk Encryption
        - Nový parametr pro Set-AzureRmVmDiskEncryptionExtension: -EncryptFormatAll šifrovaně formátuje datové disky
        - Nové parametry pro Set-AzureRmVmDiskEncryptionExtension: -ExtensionPublisherName a -ExtensionType umožňují přepínání na další verze rozšíření
        - Nové parametry pro Disable-AzureRmVmDiskEncryption: -ExtensionPublisherName a -ExtensionType umožňují přepínání na další verze rozšíření
        - Nové parametry pro Get-AzureRmVmDiskEncryptionStatus: -ExtensionPublisherName a -ExtensionType umožňují přepínání na další verze rozšíření
* DataLakeAnalytics
    * Zásadní změny pro DataLakeAnalytics v této vydané verzi viz průvodce migrací
    * Změna jednoho ze dvou typů výstupu pro Get-AzureRmDataLakeAnalyticsAccount
        - Seznam \<DataLakeAnalyticsAccount> na seznam \<PSDataLakeAnalyticsAccountBasic>
        - Vlastnosti PSDataLakeAnalyticsAccountBasic jsou striktní podmnožinou vlastností DataLakeAnalyticsAccount.
        - Tato služba nevrací další parametry, které jsou v DataLakeAnalyticsAccount.  Účelem této změny proto je správně tuto skutečnost zachytit. Tyto další vlastnosti jsou nadále v PSDataLakeAnalyticsAccountBasic, ale jsou označené jako zastaralé.
    * Změna jednoho ze dvou typů výstupu pro Get-AzureRmDataLakeAnalyticsJob
        - Seznam \<JobInformation> na seznam \<PSJobInformationBasic>
        - Vlastnosti PSJobInformationBasic jsou striktní podmnožinou vlastností JobInformation.
        - Tato služba nevrací další parametry, které jsou v JobInformation.  Účelem této změny proto je správně tuto skutečnost zachytit. Tyto další vlastnosti jsou nadále v PSJobInformationBasic, ale jsou označené jako zastaralé.
* DataLakeStore
    * Zásadní změny pro DataLakeStore v této vydané verzi viz průvodce migrací
    * Změna jednoho ze dvou typů výstupu pro Get-AzureRmDataLakeStoreAccount
        - Seznam \<PSDataLakeStoreAccount> na seznam \<PSDataLakeStoreAccountBasic>
        - Vlastnosti PSDataLakeStoreAccountBasic jsou striktní podmnožinou vlastností PSDataLakeStoreAccount.
        - Tato služba nevrací další parametry, které jsou v PSDataLakeStoreAccount.  Účelem této změny proto je správně tuto skutečnost zachytit. Tyto další vlastnosti jsou nadále v PSDataLakeStoreAccountBasic, ale jsou označené jako zastaralé.
* Dns
    * Podpora typů záznamů CAA v Azure DNS
       - Podpora všech operací s typem záznamů CAA
* Centrum událostí
    * Zásadní změny pro EventHub v této vydané verzi viz průvodce migrací
* Insights
    * Zásadní změny pro Insights v této vydané verzi viz průvodce migrací
* Síť
    * Zásadní změny pro síť v této vydané verzi viz průvodce migrací
    * Přidání rutiny pro zobrazení seznamu dostupných poskytovatelů internetových služeb pro zadanou oblast Azure
        - Get-AzureRmNetworkWatcherReachabilityProvidersList
    * Přidání rutiny pro získání skóre relativní latence pro poskytovatele internetových služeb ze zadaného umístění do oblastí Azure
        - Get-AzureRmNetworkWatcherReachabilityReport
* Profil
    - Set-AzureRmDefault
        - Tuto rutinu použijte k nastavení výchozí skupiny prostředků.  Parametr -ResourceGroup potom bude pro některé rutiny nepovinný a pokud se nezadá skupina prostředků, použije se výchozí.
        - ```Set-AzureRmDefault -ResourceGroupName "ExampleResourceGroup"```
        - Pokud zadaná skupina prostředků v předplatném existuje, se tato skupina prostředků se nastaví na výchozí.  V opačném případě se skupina prostředků vytvoří a potom se nastaví na výchozí.
    - Get-AzureRmDefault
        - Tuto rutinu použijte k získání aktuální výchozí skupiny prostředků (a dalších výchozích skupin v budoucnu).
        - ```Get-AzureRmDefault -ResourceGroup```
    - Clear-AzureRmDefault
        - Tuto rutinu použijte k odebrání aktuální výchozí skupiny prostředků.
        - ```Clear-AzureRmDefault -ResourceGroup```
    - Add-AzureRmEnvironment a Set-AzureRmEnvironment
        - Přidání parametru BatchAudience, který umožňuje zadat cílovou skupinu Active Directory služby Azure Batch, která se má použít při získávání ověřovacích tokenů pro službu Batch
* RecoveryServices.Backup
    * Přidání rutin pro provedení okamžitého obnovení souborů
        - Get-AzureRmRecoveryServicesBackupRPMountScript
        - Disable-AzureRmRecoveryServicesBackupRPMountScript
    * Aktualizace verze RecoveryServices.Backup SDK na nejnovější
    * Aktualizace testů pro úlohy virtuálních počítačů Azure tak, aby veškeré nastavení nutné pro testy prováděly testy samotné
    * Opravy https://github.com/Azure/azure-powershell/issues/3164
* RecoveryServices.SiteRecovery
    * Změny pro ASR VMware do Azure Site Recovery (rutiny aktuálně podporují operace pro Enterprise do Enterprise, Enterprise do Azure, HyperV do Azure)
        - New-AzureRmRecoveryServicesAsrPolicy
        - New-AzureRmRecoveryServicesAsrProtectedItem
        - Update-AzureRmRecoveryServicesAsrPolicy
        - Update-AzureRmRecoveryServicesAsrProtectionDirection
    * Přidání podpory pro trezor založený na AAD
    * Přidání rutin pro správu prostředků VCenter
        - Get-AzureRmRecoveryServicesAsrVCenter
        - New-AzureRmRecoveryServicesAsrVCenter
        - Remove-AzureRmRecoveryServicesAsrVCenter
        - Update-AzureRmRecoveryServicesAsrVCenter
    * Přidání dalších rutin
        - Get-AzureRmRecoveryServicesAsrAlertSetting
        - Get-AzureRmRecoveryServicesAsrEvent
        - New-AzureRmRecoveryServicesAsrProtectableItem
        - Set-AzureRmRecoveryServicesAsrAlertSetting
        - Start-AzureRmRecoveryServicesAsrResynchronizeReplicationJob
        - Start-AzureRmRecoveryServicesAsrSwitchProcessServerJob
        - Start-AzureRmRecoveryServicesAsrTestFailoverCleanupJob
        - Update-AzureRmRecoveryServicesAsrMobilityService
* ServiceBus
    - Zásadní změny pro ServiceBus v této vydané verzi viz průvodce migrací
* Sql
    * Přidání podpory pro zobrazení výpisu a zrušení asynchronní operace updateslo s databází
        - Aktualizace stávající rutiny Get-AzureRmSqlDatabaseActivity, aby vracela stav databázové operace updateslo
        - Přidání nové rutiny Stop-AzureRmSqlDatabaseActivity pro zrušení asynchronní operace updateslo s databází
    * Přidání podpory pro redundanci zón pro databáze a elastické fondy
        - Přidání přepínacího parametru ZoneRedundant do New-AzureRmSqlDatabase
        - Přidání přepínacího parametru ZoneRedundant do Set-AzureRmSqlDatabase
        - Přidání přepínacího parametru ZoneRedundant do New-AzureRmSqlElasticPool
        - Přidání přepínacího parametru ZoneRedundant do Set-AzureRmSqlElasticPool
    * Přidání podpory pro aliasy DNS serveru
        - Přidání rutiny Get-AzureRmSqlServerDnsAlias, která získá aliasy DNS serveru podle názvu aliasu a serveru nebo seznam aliasů DNS serveru pro Azure SQL Server
        - Přidání rutiny New-AzureRmSqlServerDnsAlias, která vytvoří nový alias DNS serveru pro konkrétní Azure SQL Server
        - Přidání rutiny Set-AzurermSqlServerDnsAlias, která umožní aktualizaci Azure SQL Serveru, na který odkazuje alias DNS serveru
        - Přidání rutiny Remove-AzureRmSqlServerDnsAlias, která odebere alias DNS serveru pro Azure SQL Server
* Azure.Storage
    * Upgrade na Azure Storage Client Library 8.5.0 a Azure Storage DataMovement Library 0.6.3
    * Přidání funkce podpory snímku sdílené složky
        - Přidání parametru SnapshotTime do Get-AzureStorageShare
        - Přidání parametru IncludeAllSnapshot do Remove-AzureStorageShare
