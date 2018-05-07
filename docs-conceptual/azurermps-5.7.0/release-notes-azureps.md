---
title: Protokol změn Azure PowerShellu | Dokumentace Microsoftu
description: Toto je historie změn provedených v nejnovější vydané verzi Azure PowerShellu.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.service: azure-powershell
ms.product: azure
ms.devlang: powershell
ms.topic: conceptual
ms.workload: ''
ms.date: 2/20/2018
ms.openlocfilehash: 2e80d314991539cb630a0f2a96048bb2e70a05b6
ms.sourcegitcommit: 5f0013981fcea1d689649b9a2b2ffe84ae842e56
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="release-notes"></a>Poznámky k verzi

Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.

---

# <a name="azure-powershell-570"></a>Azure PowerShell 5.7.0

Instalační program Azure PowerShellu 5.7.0: [odkaz](https://github.com/Azure/azure-powershell/releases/download/v5.7.0-April2018/azure-powershell.5.7.0.msi)

Modul galerie pro rutiny ARM: [odkaz](https://www.powershellgallery.com/packages/AzureRM/5.7.0)

Pokud chcete nainstalovat `AzureRM` z Galerie prostředí PowerShell, spusťte následující příkaz:

```powershell
Install-Module -Name AzureRM -Repository PSGallery -Force
```

Pokud chcete provést aktualizaci starší verze `AzureRM`, spusťte následující příkaz:

```powershell
Update-Module -Name AzureRM
```

## <a name="changes-since-last-release"></a>Změny od poslední vydané verze

#### <a name="general"></a>Obecné
* Aktualizace na nejnovější verzi Azure ClientRuntime

#### <a name="azurestorage"></a>Azure.Storage
* Oprava potíží, kdy rutiny pro nahrání objektu blob a souboru selhaly na počítačích s povolenými zásadami FIPS
    - Set-AzureStorageBlobContent
    - Set-AzureStorageFileContent

#### <a name="azurermbilling"></a>AzureRM.Billing
* Nová rutina Get-AzureRmEnrollmentAccount
  - Rutina pro načtení registračních účtů

#### <a name="azurermcognitiveservices"></a>AzureRM.CognitiveServices
* Integrace se sadou Cognitive Services Management SDK verze 4.0.0
* Přidání operace Get-AzureRmCognitiveServicesAccountUsage

#### <a name="azurermcompute"></a>AzureRM.Compute
* `Get-AzureRmVmssDiskEncryptionStatus` podporuje stav šifrování na úrovni datového disku
* `Get-AzureRmVmssVmDiskEncryptionStatus` podporuje stav šifrování na úrovni datového disku
* Aktualizace pro zajištění nezávislosti na zóně
* Rutiny New-AzureRmVm a New-AzureRmVmss (jednoduchá sada parametrů) podporují zóny dostupnosti

#### <a name="azurermcontainerregistry"></a>AzureRM.ContainerRegistry
* Oddělení závislosti na sadách SDK Commands.Resources.Rest a ARM/Storage

#### <a name="azurermdatalakestore"></a>AzureRM.DataLakeStore
* Přidání funkce ladění
* Aktualizace sady SDK roviny dat ADLS na verzi 1.1.2
* Export-AzureRmDataLakeStoreItem – Zastarání parametrů PerFileThreadCount a ConcurrentFileCount a zavedení parametru Concurrency
* Import-AzureRMDataLakeStoreItem – Zastarání parametrů PerFileThreadCount a ConcurrentFileCount a zavedení parametru Concurrency
* Get-AzureRMDataLakeStoreItemContent – Oprava chování koncové části obsahu většího než 4 MB
* Set-AzureRMDataLakeStoreItemExpiry – Zavedení nové sady parametrů SetRelativeExpiry umožňující nastavení relativního času vypršení platnosti
* Remove-AzureRmDataLakeStoreItem – Zastarání parametru Clean

#### <a name="azurermeventhub"></a>AzureRM.EventHub
* Oprava AlternameName v rutině New-AzureRmEventHubGeoDRConfiguration

#### <a name="azurermkeyvault"></a>AzureRM.KeyVault
* Aktualizace rutin, aby zahrnovaly scénáře propojení
* Přidání zpráv o zastarání pro nadcházející vydanou verzi se zásadními změnami

#### <a name="azurermnetwork"></a>AzureRM.Network
* Oprava chybové zprávy u rutin Network

#### <a name="azurermservicebus"></a>AzureRM.ServiceBus
* Přidání vlastnosti properties do filtru CorrelationFilter rutiny Rules pro zajištění podpory vlastních vlastností
* Aktualizace nápovědy k rutině New-AzureRmServiceBusGeoDRConfiguration a oprava výstupu rutiny Rules
* Oprava vlastností auto-forward v rutinách New-AzureRmServiceBusQueue a New-AzureRmServiceBusSubscription

#### <a name="azurermsql"></a>AzureRM.Sql
* Přidání nové rutiny Stop-AzureRmSqlElasticPoolActivity pro zajištění podpory rušení asynchronních operací v elastickém fondu
* Aktualizace odpovědí pro rutiny Get-AzureRmSqlDatabaseActivity a Get-AzureRmSqlElasticPoolActivity, aby zahrnovaly více informací

Změny od poslední vydané verze: https://github.com/Azure/azure-powershell/compare/v5.6.0-March2018...v5.7.0-April2018

## <a name="560---march-2018"></a>5.6.0 – březen 2018

#### <a name="general"></a>Obecné
* Oprava potíží s výchozí skupinou prostředků v CloudShellu
* Oprava potíží, kdy se během importu modulů spouštěly nesprávné spouštěcí skripty

#### <a name="azurermprofile"></a>AzureRM.Profile
* Povolení ověřování MSI v nepodporovaných scénářích
* Přidání podpory pro uživatelem definované identity spravované služby

#### <a name="azurermanalysisservices"></a>AzureRM.AnalysisServices
* Oprava potíží s čištěním skriptů v sestavení

#### <a name="azurermcdn"></a>AzureRM.Cdn
* Oprava potíží s čištěním skriptů v sestavení

#### <a name="azurermcompute"></a>AzureRM.Compute
* Podpora datových disků pro New-AzureRmVM a New-AzureRmVMSS
* Podpora vlastních imagí podle názvu nebo ID pro New-AzureRmVM a New-AzureRmVMSS
* Funkce analýzy protokolů
    - Přidání rutiny Export-AzureRmLogAnalyticRequestRateByInterval
    - Přidání rutiny Export-AzureRmLogAnalyticThrottledRequests

#### <a name="azurermcontainerinstance"></a>AzureRM.ContainerInstance
* Oprava potíží se sadami parametrů pro registr kontejnerů a připojení svazku služby Soubory Azure

#### <a name="azurermdatafactoryv2"></a>AzureRM.DataFactoryV2
* Aktualizace sady ADF .Net SDK na verzi 0.6.0 Preview obsahující následující změny:
    - Přidání nové propojené služby AzureDatabricks a aktivity DatabricksNotebook
    - Přidání vlastností headNodeSize a dataNodeSize v propojené službě HDInsightOnDemand
    - Přidání LinkedService, Dataset a CopySource pro SalesforceMarketingCloud
    - Přidání podpory pro SecureOutput u všech aktivit
    - Přidání nové vlastnosti BatchCount pro aktivitu ForEach, která řídí, kolik souběžných aktivit spustit
    - Přidána nové aktivity filtrování
    - Přidání podpory parametrů propojených služeb

#### <a name="azurermdns"></a>AzureRM.Dns
* Podpora pro privátní zóny DNS (verze Public Preview)
    - Přidání možnosti vytvářet zóny DNS, které jsou viditelné jenom pro přidružené virtuální sítě

#### <a name="azurermnetwork"></a>AzureRM.Network
* Aktualizace typů modelů pro zajištění kompatibility s rutinami DNS

#### <a name="azurermrecoveryservicessiterecovery"></a>AzureRM.RecoveryServices.SiteRecovery
* Změny pro obnovení do Azure s využitím Azure Site Recovery (rutiny aktuálně podporují operace pro Enterprise do Enterprise, Enterprise do Azure, HyperV do Azure, VMware to Azure)
    - New-AzureRmRecoveryServicesAsrProtectionContainer
    - New-AzureRmRecoveryServicesAsrAzureToAzureDiskReplicationConfig
    - Remove-AzureRmRecoveryServicesAsrProtectionContainer
    - Update-AzureRmRecoveryServicesAsrProtectionDirection

#### <a name="azurermstorage"></a>AzureRM.Storage
* Vyřazení následujících parametrů v rutinách New a Set pro účet úložiště: EnableEncryptionService a DisableEncryptionService, protože ve výchozím nastavení je povolené šifrování v klidovém stavu a nejde ho zakázat.
    - New-AzureRmStorageAccount
    - Set-AzureRmStorageAccount

#### <a name="azurermwebsites"></a>AzureRM.Websites
* Oprava nápovědy pro Remove-AzureRmWebAppSlot

## <a name="550---march-2018"></a>5.5.0 – březen 2018
#### <a name="azurermprofile"></a>AzureRM.Profile
* Oprava potíží s importem aliasů
* Načtení Newtonsoft.Json verze 10.0.3 souběžně s verzí 6.0.8

#### <a name="azurestorage"></a>Azure.Storage
* Podpora funkce obnovitelného odstranění
    - Enable-AzureStorageDeleteRetentionPolicy
    - Disable-AzureStorageDeleteRetentionPolicy
    - Get-AzureStorageBlob

#### <a name="azurermanalysisservices"></a>AzureRM.AnalysisServices
* Oprava potíží s importem aliasů
* Přidání podpory funkce horizontálního navýšení kapacity dotazů a brány firewall a také podpory verze API z 1. 8. 2017

#### <a name="azurermautomation"></a>AzureRM.Automation
* Oprava potíží s importem aliasů

#### <a name="azurermcdn"></a>AzureRM.Cdn
* Oprava potíží s importem aliasů

#### <a name="azurermcognitiveservices"></a>AzureRM.CognitiveServices
* Aktualizace notice.txt a zprávy s upozorněním

#### <a name="azurermcompute"></a>AzureRM.Compute
* Tisk připojovacích řetězců ve New-AzureRmVMSS v režimu s komentářem (verbose)
* Podpora New-AzureRmVmss pro veřejné IP adresy, pravidla vyrovnávání zatížení a pravidla příchozího překladu adres (NAT)
* Funkce WriteAccelerator
    - Přidání přepínacího parametru WriteAccelerator do následujících rutin: Set-AzureRmVMOSDisk Set-AzureRmVMDataDisk Add-AzureRmVMDataDisk Add-AzureRmVmssDataDisk
    - Přidání přepínacího parametru OsDiskWriteAccelerator do následující rutiny: Set-AzureRmVmssStorageProfile
    - Přidání logického parametru OsDiskWriteAccelerator do následujících rutin:     Update-AzureRmVM     Update-AzureRmVmss

#### <a name="azurermdatafactories"></a>AzureRM.DataFactories
* Oprava potíží se šifrováním přihlašovacích údajů, která způsobovala nesmyslné chyby pro některé operace šifrování
* Povolení sdílení modulu runtime integrace napříč datovou továrnou

#### <a name="azurermdatafactoryv2"></a>AzureRM.DataFactoryV2
* Přidání parametrů SetupScriptContainerSasUri a Edition pro příkaz Set-AzureRmDataFactoryV2IntegrationRuntime, aby se umožnilo vlastní nastavení a funkce výběru edice
* Oprava potíží se šifrováním přihlašovacích údajů, která způsobovala nesmyslné chyby pro některé operace šifrování
* Povolení sdílení modulu runtime integrace napříč datovou továrnou

#### <a name="azurermhdinsight"></a>AzureRM.HDInsight
* Oprava potíží s importem aliasů

#### <a name="azurermkeyvault"></a>AzureRM.KeyVault
* Oprava příkladu pro Set-AzureRmKeyVaultAccessPolicy

#### <a name="azurermnetwork"></a>AzureRM.Network
* Oprava potíží s importem aliasů

#### <a name="azurermoperationalinsights"></a>AzureRM.OperationalInsights
* Oprava potíží s importem aliasů

#### <a name="azurermrecoveryservices"></a>AzureRM.RecoveryServices
* Oprava potíží s importem aliasů

#### <a name="azurermrecoveryservicessiterecovery"></a>AzureRM.RecoveryServices.SiteRecovery
* Oprava potíží s importem aliasů

#### <a name="azurermresources"></a>AzureRM.Resources
* Oprava potíží s importem aliasů

#### <a name="azurermservicebus"></a>AzureRM.ServiceBus
* Přidání vlastnosti EnableBatchedOperations do fronty
* Přidání vlastnosti DeadLetteringOnFilterEvaluationExceptions do předplatných

#### <a name="azurermservicefabric"></a>AzureRM.ServiceFabric
* Aktualizace rutiny Service Fabric
  - Aktualizace šablon ARM
  - Neúspěšné operace se už nevracejí zpět
  - Add-AzureRmServiceFabricNodeType
    - Virtuální počítače ve výchozím nastavení použijí spravované disky
    - Použije se stávající podsíť VMSS
    - Všechny operace jsou idempotentní
  - Remove-AzureRmServiceFabricNodeType vymaže částečně vytvořené VMSS a/nebo typy uzlů clusteru
  - Oprava výstupu objektu PSCluster pro komplexní typy vlastností

#### <a name="azurermsql"></a>AzureRM.Sql
* Oprava potíží s importem aliasů
* Odpověď pro Get-AzureRmSqlServer, New-AzureRmSqlServer a Remove-AzureRmSqlServer teď zahrnuje vlastnost FullyQualifiedDomainName.

#### <a name="azurermwebsites"></a>AzureRM.Websites
* Oprava potíží s importem aliasů
* New-AzureRMWebApp – přidání sady parametrů pro zjednodušené vytváření webových aplikací, s podporou místního úložiště Git

## <a name="540---february-2018"></a>5.4.0 – únor 2018
#### <a name="azurermautomation"></a>AzureRM.Automation
* Přidání aliasu z New-AzureRmAutomationModule do Import-AzureRmAutomationModule

#### <a name="azurermcompute"></a>AzureRM.Compute
* Oprava potíží ErrorAction pro některé rutiny Get

#### <a name="azurermcontainerinstance"></a>AzureRM.ContainerInstance
* Použití sady Azure Container Instance SDK z 1. února 2018
    - Podpora pro popisky názvů DNS

#### <a name="azurermdevtestlabs"></a>AzureRM.DevTestLabs
* Oprava všech rutin GET, které dřív nefungovaly

#### <a name="azurermeventhub"></a>AzureRM.EventHub
* Oprava chyby v nápovědě k Get-AzureRmEventHubGeoDRConfiguration

#### <a name="azurermnetwork"></a>AzureRM.Network
* Přidání rutiny pro vytvoření nového monitorování připojení
    - New-AzureRmNetworkWatcherConnectionMonitor
* Přidání rutiny pro aktualizaci monitorování připojení
    - Set-AzureRmNetworkWatcherConnectionMonitor
* Přidání rutiny pro získání monitorování připojení nebo seznamu monitorování připojení
    - Get-AzureRmNetworkWatcherConnectionMonitor
* Přidání rutiny pro dotazování na monitorování připojení
    - Get-AzureRmNetworkWatcherConnectionMonitorReport
* Přidání rutiny pro zahájení monitorování připojení
    - Start-AzureRmNetworkWatcherConnectionMonitor
* Přidání rutiny pro ukončení monitorování připojení
    - Stop-AzureRmNetworkWatcherConnectionMonitor
* Přidání rutiny pro odebrání monitorování připojení
    - Remove-AzureRmNetworkWatcherConnectionMonitor
* Aktualizace dokumentace k Set-AzureRmApplicationGatewayBackendAddressPool pro odebrání zastaralých příkazů
* Přidání příznaku EnableHttp2 k Application Gateway
    - Aktualizace New-AzureRmApplicationGateway: Přidání volitelného parametru -EnableHttp2
* Přidání IpTagů pro PublicIpAddress
    - Aktualizace New-AzureRmPublicIpAddress: IpTagy
    - New-AzureRmPublicIpTag pro přidání IpTagu
* Přidání vlastnosti DisableBgpRoutePropagation do RouteTable a effectiveRoute

#### <a name="azurermresources"></a>AzureRM.Resources
* Register-AzureRmProviderFeature: Přidání chybějícího příkladu v dokumentaci
* Register-AzureRmResourceProvider: Přidání chybějícího příkladu v dokumentaci

#### <a name="azurermstorage"></a>AzureRM.Storage
* Vyřazení následujících parametrů v rutinách New a Set pro účet úložiště: EnableEncryptionService a DisableEncryptionService, protože ve výchozím nastavení je povolené šifrování v klidovém stavu a nejde ho zakázat.
    - New-AzureRmStorageAccount
    - Set-AzureRmStorageAccount


## <a name="530---february-2018"></a>5.3.0 – únor 2018
### <a name="azurermprofile"></a>AzureRM.Profile
* Přidání upozornění na vyřazení pro PowerShell 3 a 4
* Přejmenování `Add-AzureRmAccount` na `Connect-AzureRmAccount`; přidání aliasu pro starý název rutiny a přesměrování ostatních aliasů (`Login-AzAccount` a `Login-AzureRmAccount`) na nový název rutiny
* Přejmenování `Remove-AzureRmAccount` na `Disconnect-AzureRmAccount`; přidání aliasu pro starý název rutiny a přesměrování ostatních aliasů (`Logout-AzAccount` a `Logout-AzureRmAccount`) na nový název rutiny
* Oprava řetězců prostředků pro použití `Connect-AzureRmAccount` místo `Login-AzureRmAccount`
* `Add-AzureRmEnvironment` a `Set-AzureRmEnvironment`
  - Přidání `-AzureOperationalInsightsEndpoint` a `-AzureOperationalInsightsEndpointResourceId` jako parametrů pro použití s RP roviny dat OperationalInsights

### <a name="azurermanalysisservices"></a>AzureRM.AnalysisServices
* Oprava využití pro `Login-AzureRmAccount`, aby se použilo `Connect-AzureRmAccount`

### <a name="azurermcompute"></a>AzureRM.Compute
* Přidání parametru `-AvailabilitySetName` do zjednodušené sady parametrů `New-AzureRmVM`
* Oprava využití pro `Login-AzureRmAccount`, aby se použilo `Connect-AzureRmAccount`
* Podpora identit přiřazených uživateli pro virtuální počítače a škálovací sady virtuálních počítačů
    - Přidání parametrů `-IdentityType` a `-IdentityId` do `New-AzureRmVMConfig`, `New-AzureRmVmssConfig`, `Update-AzureRmVM` a `Update-AzureRmVmss`
* Přidání parametru `-EnableIPForwarding` do `Add-AzureRmVmssNetworkInterfaceConfig`
* Přidání parametru `-Priority` do `New-AzureRmVmssConfig`

### <a name="azurermdatalakeanalytics"></a>AzureRM.DataLakeAnalytics
* Oprava využití pro `Login-AzureRmAccount`, aby se použilo `Connect-AzureRmAccount`

### <a name="azurermdatalakestore"></a>AzureRM.DataLakeStore
* Oprava využití pro `Login-AzureRmAccount`, aby se použilo `Connect-AzureRmAccount`
* Oprava chybové zprávy `Test-AzureRmDataLakeStoreAccount` při spuštěné této rutiny bez přihlášení s využitím `Login-AzureRmAccount`

### <a name="azurermeventgrid"></a>AzureRM.EventGrid
* Aktualizace pro využití verze API z 1. ledna 2018

### <a name="azurermeventhub"></a>AzureRM.EventHub

* Přidání následujících nových příkazů pro operace geografického zotavení po havárii:
  - Vytvoření nového aliasu (konfigurace zotavení po havárii):
    - `New-AzureRmEventHubGeoDRConfiguration`
  - Načtení aliasu (konfigurace zotavení po havárii):
    - `Get-AzureRmEventHubGeoDRConfiguration`
  - Zákaz zotavení po havárii a zastavení replikace změn z primárních oborů názvů do sekundárních
    - `Set-AzureRmEventHubGeoDRConfigurationBreakPair`
  - Vyvolání převzetí služeb při selhání pro zotavení po havárii a změna konfigurace aliasu, aby odkazoval na sekundární obor názvů
    - `Set-AzureRmEventHubGeoDRConfigurationFailOver`
  - Odstranění aliasu (konfigurace zotavení po havárii)
    - `Remove-AzureRmEventHubGeoDRConfiguration`
* Přidání následujících příkazů pro kontrolu názvu oboru názvů a názvu konfigurace GeoDr – dostupnost aliasu.
  - Kontrola dostupnosti aliasu nebo názvu oboru názvů (konfigurace zotavení po havárii):
    - `Test-AzureRmEventHubName`

### <a name="azurerminsights"></a>AzureRM.Insights
* Oprava využití pro `Login-AzureRmAccount`, aby se použilo `Connect-AzureRmAccount`

### <a name="azurermkeyvault"></a>AzureRM.KeyVault
* Oprava využití pro `Login-AzureRmAccount`, aby se použilo `Connect-AzureRmAccount`

### <a name="azurermnetwork"></a>AzureRM.Network
* Oprava přepsání zprávy Opravdu chcete přepsat prostředek

#### <a name="azurermoperationalinsights"></a>AzureRM.OperationalInsights
* Přidání podpory pro dotazování V2 API prostřednictvím `Invoke-AzureRmOperationalInsightsQuery` Další informace o novém rozhraní API najdete tady: [https://dev.loganalytics.io/](https://dev.loganalytics.io/).

### <a name="azurermresources"></a>AzureRM.Resources
* `Get-AzureRmADServicePrincipal`: Odebrání `-ServicePrincipalName` z výchozí prázdné sady parametrů kvůli redundanci se sadou parametrů SPN

### <a name="azurermservicebus"></a>AzureRM.ServiceBus

* Přidání opravy funkcí pro `Remove-AzureRmServiceBusRule` a `Get-AzureRmServiceBusKey`
* Přidání následujících nových rutin pro operace geografického zotavení po havárii.
  - Vytvoření nového aliasu (konfigurace zotavení po havárii):
    - `New-AzureRmServiceBusDRConfigurations`
  - Načtení aliasu (konfigurace zotavení po havárii):
    - `Get-AzureRmServiceBusDRConfigurations`
  - Zákaz zotavení po havárii a zastavení replikace změn z primárních oborů názvů do sekundárních
    - `Set-AzureRmServiceBusDRConfigurationsBreakPairing`
  - Vyvolání převzetí služeb při selhání pro zotavení po havárii a změna konfigurace aliasu, aby odkazoval na sekundární obor názvů
    - `Set-AzureRmServiceBusDRConfigurationsFailOver`
  - Odstranění aliasu (konfigurace zotavení po havárii)
    - `Remove-AzureRmServiceBusDRConfigurations`
* Aktualizace rutin `Test-AzureRmServiceBusName` pro podporu operací kontroly dostupnosti názvu aliasu geografického zotavení po havárii
  - Kontrola dostupnosti aliasu nebo názvu oboru názvů (konfigurace zotavení po havárii):
    - `Test-AzureRmServiceBusName`

### <a name="azurermusageaggregates"></a>AzureRM.UsageAggregates
* Oprava využití pro `Login-AzureRmAccount`, aby se použilo `Connect-AzureRmAccount`

## <a name="520---january-2018"></a>5.2.0 – leden 2018
#### <a name="azurermprofile"></a>AzureRM.Profile
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Add-AzureRmAccount
  * Přidání přihlášení -MSI pro ověřování s využitím přihlašovacích údajů Managed Service Identity aktuálního virtuálního počítače nebo služby
  * Oprava ověřování služby KeyVault při přihlášení s využitím přístupových tokenů zadaných uživatelem

#### <a name="azurestorage"></a>Azure.Storage
* Přidání rutin pro získání a nastavení vlastností služby Storage
    - Get-AzureStorageServiceProperty
    - Update-AzureStorageServiceProperty

#### <a name="azurermanalysisservices"></a>AzureRM.AnalysisServices
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermapimanagement"></a>AzureRM.ApiManagement
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmApiManagementProperty, Set-AzureRmApiManagementProperty a New-AzureRmApiManagement

#### <a name="azurermapplicationinsights"></a>AzureRM.ApplicationInsights
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermautomation"></a>AzureRM.Automation
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro Set-AzureRmAutomationRunbook

#### <a name="azurermbackup"></a>AzureRM.Backup
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermbatch"></a>AzureRM.Batch
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermcdn"></a>AzureRM.Cdn
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmCdnEndpoint a New-AzureRmCdnProfile

#### <a name="azurermcognitiveservices"></a>AzureRM.CognitiveServices
* Integrace se sadou Cognitive Services Management SDK verze 3.0.0

#### <a name="azurermcompute"></a>AzureRM.Compute
* Přidání zjednodušené sady parametrů do New-AzureRmVmss, která vytvoří škálovací sadu virtuálních počítačů a všechny požadované prostředky s využitím inteligentních výchozích hodnot
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmVm a Update-AzureRmVm
* Oprava rutiny Get-AzureRmComputeResourceSku, když součástí omezení je zóna
* Aktualizace schématu konfigurace agenta diagnostiky pro podporu jímek Azure Monitoru

#### <a name="azurermcontainerinstance"></a>AzureRM.ContainerInstance
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermcontainerregistry"></a>AzureRM.ContainerRegistry
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermdatafactories"></a>AzureRM.DataFactories
* Povolení podpory Azure Key Vault pro všechny propojené služby úložiště dat
* Přidání vlastnosti typu licence pro Azure SSIS Integration Runtime
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmDataFactory

#### <a name="azurermdatafactoryv2"></a>AzureRM.DataFactoryV2
* Povolení podpory Azure Key Vault pro všechny propojené služby úložiště dat
* Přidání vlastnosti typu licence pro Azure SSIS Integration Runtime
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Přidání parametru LicenseType pro příkaz Set-AzureRmDataFactoryV2IntegrationRuntime s cílem povolit funkci AHUB

#### <a name="azurermdatalakeanalytics"></a>AzureRM.DataLakeAnalytics
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmDataLakeAnalyticsAccount a Set-AzureRmDataLakeAnalyticsAccount

#### <a name="azurermdatalakestore"></a>AzureRM.DataLakeStore
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmDataLakeStoreAccount a Set-AzureRmDataLakeStoreAccount

#### <a name="azurermdevtestlabs"></a>AzureRM.DevTestLabs
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermdns"></a>AzureRM.Dns
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermeventgrid"></a>AzureRM.EventGrid
* Přidání následující nové rutiny:
  - Update-AzureRmEventGridSubscription
    - Aktualizace vlastností předplatného událostí služby Event Grid
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermeventhub"></a>AzureRM.EventHub
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermhdinsight"></a>AzureRM.HDInsight
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurerminsights"></a>AzureRM.Insights
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermiothub"></a>AzureRM.IotHub
* Přidání podpory certifikátů pro rutiny IoTHub
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermkeyvault"></a>AzureRM.KeyVault
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Přidání podpory -AsJob pro dlouho běžící rutiny KeyVault. Umožňuje vybraným rutinám, aby běžely na pozadí, a vrací úlohu pro sledování a řízení průběhu.
  * Ovlivněná rutina: Remove-AzureRmKeyVault
* Oprava chyby v Set-AzureRmKeyVaultAccessPolicy, kde filtr AAD nastavoval hlavní název služby (SPN) na zadaný hlavní název uživatele (UPN) (místo nastavení hlavního názvu uživatele)
  - Další informace najdete tady: https://github.com/Azure/azure-powershell/issues/5201.

#### <a name="azurermlogicapp"></a>AzureRM.LogicApp
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermmachinelearning"></a>AzureRM.MachineLearning
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro Update-AzureRmMlCommitmentPlan

#### <a name="azurermmachinelearningcompute"></a>AzureRM.MachineLearningCompute
* Přidání parametru IncludeAllResources do rutiny Remove-AzureRmMlOpCluster
  - Použití tohoto přepínacího parametru odebere všechny prostředky původně vytvořené s clusterem
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermmedia"></a>AzureRM.Media
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro Set-AzureRmMediaService a New-AzureRmMediaService

#### <a name="azurermnetwork"></a>AzureRM.Network
* Přidání podpory -AsJob pro dlouho běžící rutiny Network. Umožňuje vybraným rutinám, aby běžely na pozadí, a vrací úlohu pro sledování a řízení průběhu.
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermnotificationhubs"></a>AzureRM.NotificationHubs
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmNotificationHubsNamespace a Set-AzureRmNotificationHubsNamespace

#### <a name="azurermoperationalinsights"></a>AzureRM.OperationalInsights
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmOperationalInsightsSavedSearch, Set-AzureRmOperationalInsightsSavedSearch, New-AzureRmOperationalInsightsWorkspace a Set-AzureRmOperationalInsightsWorkspace

#### <a name="azurermpowerbiembedded"></a>AzureRM.PowerBIEmbedded
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermrecoveryservices"></a>AzureRM.RecoveryServices
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermrecoveryservicesbackup"></a>AzureRM.RecoveryServices.Backup
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Přidání možnosti -UseOriginalStorageAccount do rutiny Restore-AzureRmRecoveryServicesBackupItem
  - Povolení tohoto příznaku má za následek obnovení disků do původních účtů úložiště, které uživatelům umožňují udržovat konfiguraci obnovených virtuálních počítačů co nejblíže původním virtuálním počítačům.
  - Pomáhá také zlepšit výkon operace obnovení.

#### <a name="azurermrediscache"></a>AzureRM.RedisCache
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Přidání 3 nových rutin pro pravidla brány firewall
* Přidání 3 nových rutin pro georeplikaci
* Přidání podpory pro zóny a značky
* Nastavení ResourceGroup volitelné všude, kde je to možné

#### <a name="azurermrelay"></a>AzureRM.Relay
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermresources"></a>AzureRM.Resources
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Přidání podpory -AsJob pro dlouho běžící rutiny Resources Umožňuje vybraným rutinám, aby běžely na pozadí, a vrací úlohu pro sledování a řízení průběhu.
* Přidání aliasu z Get-AzureRmProviderOperation do Get-AzureRmResourceProviderAction pro dodržení zásad vytváření názvů

#### <a name="azurermscheduler"></a>AzureRM.Scheduler
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermservermanagement"></a>AzureRM.ServerManagement
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Vyřazení -Tags a místo toho použití -Tag pro New-AzureRmServerManagementNode a New-AzureRmServerManagementGateway

#### <a name="azurermservicebus"></a>AzureRM.ServiceBus
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermservicefabric"></a>AzureRM.ServiceFabric
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermsiterecovery"></a>AzureRM.SiteRecovery
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermsql"></a>AzureRM.Sql
* Aktualizace popisu parametrů příkazů auditování
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Přidání parametru -AsJob pro dlouho běžící rutiny
* Vyřazení parametru -DatabaseName z Get-AzureRmSqlServiceObjective

#### <a name="azurermstorage"></a>AzureRM.Storage
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Oprava potíží s nulovým odkazem pro běhovou rutinu New-AzureRMStorageAccount s parametrem -EnableEncryptionService None
* Přidání podpory -AsJob pro dlouho běžící rutiny Storage Umožňuje vybraným rutinám, aby běžely na pozadí, a vrací úlohu pro sledování a řízení průběhu.
    - Ovlivněné rutiny: New-, Remove-, Add- a Update- pro Storage Account a Storage Account Network Rule

#### <a name="azurermstreamanalytics"></a>AzureRM.StreamAnalytics
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermtrafficmanager"></a>AzureRM.TrafficManager
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném

#### <a name="azurermwebsites"></a>AzureRM.Websites
* Přidání dokončovací rutiny Location pro parametry -Location, která umožňuje vyplnění karet s využitím platných umístění
* Přidání dokončovací rutiny ResourceGroup pro parametry -ResourceGroup, která umožňuje vyplnění karet s využitím skupin prostředků v aktuálním předplatném
* Přidání podpory -AsJob pro dlouho běžící rutiny Websites. Umožňuje vybraným rutinám, aby běžely na pozadí, a vrací úlohu pro sledování a řízení průběhu.
     - Ovlivněné rutiny: New-, Remove-, Add- a Set- pro WebApps, AppServicePlan a Slots

## <a name="2017128-version-511"></a>8. prosince 2017 – verze 5.1.1
* AnalysisServices
  - Změna ověření sady umístění na dynamické vyhledávání, takže se podporují všechny cloudy
* Automation
  - Aktualizace pro Import-AzureRMAutomationRunbook
    - Podpora se nyní poskytuje pro runbooky Python2.
* Batch
  - Oprava chyby, kdy operace účtu bez skupiny prostředků selhaly při automatickém ověřování skupiny prostředků
* Compute
  - Get-AzureRmComputeResourceSku zobrazuje informace o zóně.
  - Aktualizace Disable-AzureRmVmssDiskEncryption a vyřešení potíží https://github.com/Azure/azure-powershell/issues/5038
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
    - Další informace o mapování koncových bodů Azure Government najdete tady: https://docs.microsoft.com/en-us/azure/azure-government/documentation-government-developer-guide#endpoint-mapping.
    - Přidání podpory -AsJob pro rutiny, umožňuje vybraným rutinám, aby spouštěly na pozadí, a vrací úlohu pro sledování a řízení průběhu
    - Přidání parametru -AsJob do rutiny Get-AzureRmSubscription
* RecoveryServices.Backup
  - Oprava chyby: Rutina Get-AzureRmRecoveryServicesBackupItem by měla pro filtrování názvu kontejneru používat porovnání bez rozlišení velkých a malých písmen.
  - Oprava chyby: AzureVmItem teď má vlastnost, která ukazuje čas posledního provedení operace zálohování – LastBackupTime.
* Zdroje a prostředky
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
* POZNÁMKA: Toto je vydání se zásadními změnami. Kompletní seznam uvedených zásadních změn najdete v průvodci migrací (https://aka.ms/azps-migration-guide)).
* Všechny rutiny v AzureRM teď s podporou online nápovědy
  - Spuštění Get-Help s parametrem -Online pro otevření online nápovědy ve výchozím internetovém prohlížeči
* AnalysisServices
  * Oprava příkazu Synchronize-AzureAsInstance tak, aby fungoval s novým rozhraním AsAzure REST API pro synchronizaci
* Správa rozhraní API
  * Zásadní změny pro ApiManagement v této vydané verzi viz průvodce migrací
  * Aktualizovaná rutina Get-AzureRmApiManagementUser pro vyřešení potíží https://github.com/Azure/azure-powershell/issues/4510
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
