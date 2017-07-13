---
title: "Protokol změn Azure PowerShellu | Dokumentace Microsoftu"
description: "Toto je historie změn provedených v nejnovější vydané verzi Azure PowerShellu."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.service: azure-resource-manager
ms.product: azure
ms.devlang: powershell
ms.topic: conceptual
ms.workload: 
ms.date: 05/18/2017
ms.openlocfilehash: 5c8fa2a5a8f94cd24b66f42c237749a7b89af3b3
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <a name="release-notes"></a>Poznámky k verzi

Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.

## <a name="version-400"></a>Verze 4.0.0

* Toto vydání obsahuje nejnovější změny. Podrobnosti o změnách a informace o vlivu změn na stávající skripty najdete v [příručce k migraci](https://aka.ms/azps-migration-guide).
* Správa rozhraní API
  - Přidání podpory konfigurace externích skupin ve skupině New-AzureRmApiManagementGroup
* Fakturace
  - Nová rutina Get-AzureRmBillingPeriod
    + Slouží k načtení fakturačních období Azure předplatného.
  - Aktualizace rutiny Get-AzureRmBillingInvoice
  - Nová vlastnost BillingPeriodNames
  - Výstup v zobrazení seznamu
* Compute
  - Aktualizace rutin Set-AzureRmVMAEMExtension a Test-AzureRmVMAEMExtension pro podporu spravovaných disků úrovně Premium
  - Nastavení šifrování zálohování pro virtuální počítače IaaS a obnovení při selhání
  - Přejmenování ChefServiceInterval na ChefDaemonInterval Stará rutina bude ale fungovat i nadále.
  - Odebrání duplikovaných vlastností DataDiskNames a NetworkInterfaceIDs z objektu virtuálního počítače PS
  - Nastavení parametrů DataDiskNames a NetworkInterfaceIDs jako volitelných v Remove-AzureRmVMDataDisk a Remove-AzureRmVMNetworkInterface
  - Oprava problému s propojením rutin Get, když tyto rutiny vrátí objekt seznamu
  - Přejmenování rutin, které byly v konfliktu s rutinami RDFE Další podrobnosti o problému najdete v článku https://github.com/Azure/azure-powershell/issues/2917.
    + Přejmenování `New-AzureVMSqlServerAutoBackupConfig` na `New-AzureRmVMSqlServerAutoBackupConfig`
    + Přejmenování `New-AzureVMSqlServerAutoPatchingConfig` na `New-AzureRmVMSqlServerAutoPatchingConfig`
    + Přejmenování `New-AzureVMSqlServerKeyVaultCredentialConfig` na `New-AzureRmVMSqlServerKeyVaultCredentialConfig`
* Využití
  - Nová rutina Get-AzureRmConsumptionUsageDetail
    + Rutina slouží k načtení podrobností o využití předplatného.
* ContainerRegistry
  - Přidání powershellových rutin do Azure Container Registry
    + New-AzureRmContainerRegistry
    + Get-AzureRmContainerRegistry
    + Update-AzureRmContainerRegistry
    + Remove-AzureRmContainerRegistry
    + Get-AzureRmContainerRegistryCredential
    + Update-AzureRmContainerRegistryCredential
    + Test-AzureRmContainerRegistryNameAvailability
* DataLakeAnalytics
  - Přidání podpory pro získání a zobrazení seznamu balíčku katalogu
  - Přidání podpory zobrazení seznamu následujících položek katalogu z hlubší úrovně nadřazených prvků:
    + Table
    + TVF
    + Zobrazení
    + Statistika
* DataLakeStore
  - U `Import-AzureRMDataLakeStoreItem` a `Export-AzureRMDataLakeStoreItem` bylo ve výchozím nastavení vypnuto protokolování trasování z důvodu vylepšení výkonu. Pokud protokolování trasování chcete používat, použijte parametry `-DiagnosticLogLevel` a `-DiagnosticLogPath`.
  - Oprava chyby, která někdy způsobovala selhání PowerShellu při načítání velkého množství malých souborů do ADLS
* Centrum událostí
  - Oprava chyby:
    + Oprava chyby u rutiny Set-AzureRmEventHubNamespace – Tier nemůže být null tam, kde by mělo být SkuName
    + Set-AzureRmEventHub – oprava chyby, kdy při aktualizaci EventHub není odkaz objektu nastaven na instanci objektu
* Insights
  - Add-AzureRm*AlertRule
    + Vrátí jeden objekt: newResource, statusCode, requestId.
  - Get-AzureRmAlertRule
    + Výstup teď představuje výčet a nepovažuje se za jeden objekt. Typ se nezměnil, stále se jedná o seznam.
  - Remove-AzureRmAlertRule
    + statusCode se řídí stavovým kódem vráceným žádostí, dosud byl vždy OK.
  - Add-AzureRmAutoscaleSetting
    + Vrátí jeden objekt (nikoli seznam jako dříve) obsahující statusCode, requestId a nově vytvořený nebo aktualizovaný prostředek.
    + Stavový kód se řídí stavem vráceným žádostí, dosud byl vždy OK.
  - New-AzureRmAutoscaleRule
    + Parametr ScaleActionType byl rozšířen, nyní přijímá tyto hodnoty: ChangeCount, PercentChangeCount, ExactCount.
  - Remove-AzureRmAutoscaleSetting
    + statusCode ve výstupu se řídí stavovým kódem vráceným žádostí. Dosud byl vždy OK.
  - Get-AzureRMLogProfile
    + Výstup teď představuje výčet. Dosud se považoval za jeden objekt. Typ výstupu zůstává stejný – jedná se o seznam jako dříve.
  - Remove-AzureRmLogProfile
    + Byl implementován parametr PassThru.
  - Metrics API
    + Sada SDK nyní načítá metriky z MDM.
  - Get-AzureRmMetricDefinition
    + Výstupem je stále seznam, ale jeho struktura se změnila.
  - Get-AzureRmMetric
    + Volání se změnilo. Nová syntaxe: Get-AzureRmMetric ResourceId [MetricNames [TimeGrain] [AggregationType] [StartTime] [EndTime]] [DetailedOutput]
    + Výstupem je seznam a struktura jeho prvků se změnila.
* KeyVault
  - Přidání podpory zálohování a obnovení pro tajné kódy KeyVault
    + Tajné kódy je možné zálohovat a obnovit, což odpovídá funkcím, které se momentálně podporují u klíčů.

  - Rutiny zálohování pro klíče a tajné kódy nyní jako vstupní parametr přijímají odpovídající objekt.
    + Volající může zřetězit operace načtení a zálohování: Get-AzureKeyVaultKey -VaultName myVault -Name myKey | Backup-AzureKeyVaultKey

  - Rutiny zálohování nyní podporují přepínač -Force pro přepis existujícího souboru.
    + Všimněte si, že při pokusu o přepis existujícího souboru se už přepis nespustí, ale místo se uživateli zobrazí výzva k výběru, jak chce postupovat.
* LogicApp
  - Nové parametry pro rutiny zotavení po havárii kontrolních čísel výměny:
    + Volitelný parametr -AgreementType (X12 nebo Edifact) pro zadání relevantních kontrolních čísel
* MachineLearning
  - Využití nové verze sady Azure Machine Learning .Net SDK a přidání nové rutiny
    + Add-AzureRmMlWebServiceRegionalProperty
  - Menší opravy formulace v textu nápovědy
* Síť
  - Přidání rutiny Test-AzureRmNetworkWatcherConnectivity
    + Vrátí informace o konektivitě pro zadaný zdrojový virtuální počítač a cíl.
    + Pokud není možné navázat připojení mezi zdrojem a cílem, rutina vrátí podrobnosti o problému.
* Profil
  - Přidání rutiny Send-Feedback: umožňuje uživateli iniciovat sadu výzev, které posílají týmu Azure PowerShell zpětnou vazbu.
  - Následující aliasy byly odebrány, protože docházelo ke konfliktům s názvy existujících rutin v modulu Azure:
    + `Enable-AzureDataCollection` (podporováno rutinou `Enable-AzureRmDataCollection`)
    + `Disable-AzureDataCollection` (podporováno rutinou `Disable-AzureRmDataCollection`)
* Relay
  - Přidá rutiny pro Azure Relay, které umožňují uživatelům vytvářet a spravovat všechny prostředky Azure Relay.
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
* Zdroje a prostředky
  - Podporuje nasazení v různých skupinách prostředků pro New-AzureRmResourceGroupDeployment.
    + Uživatelé teď můžou používat vnořená nasazení pro nasazení do různých skupin prostředků.
* ServiceBus

  - Oprava chyby: Hodnoty vlastnosti objektu ServiceBus nebyly nastaveny na null, objekt slouží jako vstupní parametr v rutině Set-AzureRmServiceBusQueue pro aktualizaci fronty.
   - Vlastnosti, kterých se to týká: LockDuration, EntityAvailabilityStatus, DuplicateDetectionHistoryTimeWindow, MaxDeliveryCount a MessageCount
* ServiceFabric

  - Přidání rutin pro prostředky infrastruktury služby
    + Add-AzureRmServiceFabricApplicationCertificate: Přidá certifikát, který se použije jako certifikát aplikace.
    + Add-AzureRmServiceFabricClientCertificate: Přidá běžný název nebo kryptografický otisk do nastavení clusteru pro ověření klienta.
    + Add-AzureRmServiceFabricClusterCertificate: Do clusteru přidá sekundární certifikát clusteru pro předání existujícího certifikátu.
    + Add-AzureRmServiceFabricNodes: Do clusteru přidá uzly nebo virtuální počítače s konkrétním typem uzlu.
    + Add-AzureRmServiceFabricNodeType: Do existujícího clusteru přidá typ uzlu nebo virtuální počítače.
    + Get-AzureRmServiceFabricCluster: Načte podrobnosti prostředku clusteru.
    + New-AzureRmServiceFabricCluster: Vytvoří nový cluster ServiceFabric. Tento příkaz je možné využít v mnoha různých scénářích.
    + Remove-AzureRmServiceFabricClientCertificate: Odebere klientskému certifikátu možnost přístupu ke clusteru.
    + Remove-AzureRmServiceFabricClusterCertificate: Odebere certifikátu clusteru možnost použití pro zabezpečení clusteru.
    + Remove-AzureRmServiceFabricNodes: Odebere uzly z konkrétního typu uzlu z clusteru.
    + Remove-AzureRmServiceFabricNodeType: Odebere typ uzlu z clusteru.
    + Remove-AzureRmServiceFabricSettings: Odebere minimálně jedno nastavení ServiceFabric z clusteru.
    + Set-AzureRmServiceFabricSettings: Přidá nebo aktualizuje minimálně jedno nastavení clusteru.
    + Set-AzureRmServiceFabricUpgradeType: Změní typ upgradu ServiceFabric clusteru.
    + Update-AzureRmServiceFabricDurability: Změní úroveň odolnosti clusteru.
    + Update-AzureRmServiceFabricReliability: Změní úroveň spolehlivosti clusteru.
* Sql
  - Přidání parametru -SampleName do New-AzureRmSqlDatabase
  - Aktualizace rutin skupin převzetí služeb při selhání
  - Odebrání parametrů Tag
  - Odebrání parametrů PartnerResourceGroupName a PartnerServerName z rutiny Remove-AzureRmSqlDatabaseFailoverGroup
  - Přidání parametru GracePeriodWithDataLossHours do rutin New- a Set-, který nakonec nahradí parametr GracePeriodWithDataLossHour
  - Doplnění a aktualizace dokumentace
  - Změna formátování vrácených objektů a oprava některých chyb s občasným nenaplňováním polí
  - Přidání vlastností DatabaseNames a PartnerLocation do objektu skupiny převzetí služeb při selhání
  - Oprava chyby, která způsobovala, že rutina Switch- vracela výsledky okamžitě, aniž by počkala na dokončení operace
  - Oprava chyby s přetečením celého čísla při použití vysokých hodnot období odkladu
  - Možnost úpravy období odkladu na minimálně 1 hodinu, pokud je zadána nižší hodnota
  - Odebrání hodnoty Usage_Anomaly z akceptovaných hodnot parametru ExcludedDetectionType v rutině Set-AzureRmSqlDatabaseThreatDetectionPolicy a rutině Set-AzureRmSqlServerThreatDetectionPolicy
* Úložiště
  - Upgrade sady SRP SDK na 6.3.0
  - New/Set-AzureRmStorageAccount: Přidá nový parametr pro podporu atributu EnableHttpsTrafficOnly.
  - New/Set/Get-AzureRmStorageAccount: Vrácený účet úložiště obsahuje nový atribut EnableHttpsTrafficOnly.
* Azure.Storage
  - Upgrade na Azure Storage Client Library 8.1.1 a Azure Storage DataMovement Library 0.5.1
  - Přidání nové rutiny pro podporu funkce vytváření přírůstkových kopií objektu blob
