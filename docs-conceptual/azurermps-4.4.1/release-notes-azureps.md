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
ms.date: 07/26/2017
ms.openlocfilehash: d8a891673df343551cbd805016c2d25ee4e31c8c
ms.sourcegitcommit: e6b7e20bbd04eda51416c56b13f867102b602d1a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2017
---
# <a name="release-notes"></a>Poznámky k verzi

Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.

## <a name="20170925---version-440"></a>25. 9. 2017 – Verze 4.4.0
* AnalysisServices
  * Přidání nové rutiny roviny dat umožňující synchronizaci databází z instance pro čtení a zápis do instancí jen pro čtení
    - Zahrnutí souboru nápovědy pro tuto rutinu
    - Přidání testů v paměti a testu scénáře (pouze za provozu)
  * Oprava chyb v rutině Add-AzureAsAccount
* Automation
  * Oprava dokumentů nápovědy pro rutiny opravené v předchozí verzi
  * Přidání 4 nových rutin pro podporu fázovaného uvedení konfigurací uzlů DSC
    - Start-AzureRmAutomationDscNodeConfigurationDeployment
    - Stop-AzureRmAutomationDscNodeConfigurationDeployment
    - Get-AzureRmAutomationDscNodeConfigurationDeployment
    - Get-AzureRmAutomationDscNodeConfigurationDeploymentSchedule
* CognitiveServices
  * Integrace se sadou Cognitive Services Management SDK verze 2.0.0
  * Get-AzureRmCognitiveServicesAccount nyní správně podporuje stránkování
* Compute
  * Funkce příkazu Spustit:
    - Nová rutina Invoke-AzureRmVMRunCommand vyvolá příkaz Spustit na virtuálním počítači
    - Nová rutina Get-AzureRmVMRunCommandDocument zobrazuje dostupné dokumenty k příkazu Spustit
  * Přidání parametru StorageAccountType do Set-AzureRmDataDisk
  * Podpora zóny dostupnosti pro virtuální počítač, škálovací sadu virtuálních počítačů a disk
    - Přidání nového parametru Zone do New-AzureRmVM, New-AzureRmVMConfig, New-AzureRmVmssConfig a New-AzureRmDiskConfig
  * Funkce upgradu škálovací sady virtuálních počítačů se zajištěním provozu:
    - Nová rutina Start-AzureRmVmssRollingOSUpgrade vyvolá upgrade operačního systému škálovací sady virtuálních počítačů se zajištěním provozu
    - Nová rutina Set-AzureRmVmssRollingUpgradePolicy nastaví zásady upgradu pro upgrade škálovací sady virtuálních počítačů se zajištěním provozu
    - Nová rutina Stop-AzureRmVmssRollingUpgrade zruší upgrade škálovací sady virtuálních počítačů se zajištěním provozu
    - Nová rutina Get-AzureRmVmssRollingUpgrade zobrazuje stav upgradu škálovací sady virtuálních počítačů se zajištěním provozu
  * Zavedení přepínacího parametru AssignIdentity pro identitu přiřazenou systémem
    - Přidání nového parametru AssignIdentity do New-AzureRmVMConfig, New-AzureRmVmssConfig a Update-AzureRmVM
  * Funkce šifrování disku škálovací sady virtuálních počítačů:
    - Nová rutina Set-AzureRmVmssDiskEncryptionExtension povoluje šifrování disku ve škálovací sadě virtuálních počítačů
    - Nová rutina Disable-AzureRmVmssDiskEncryption zakazuje šifrování disku ve škálovací sadě virtuálních počítačů
    - Nová rutina Get-AzureRmVmssDiskEncryptionStatus zobrazuje stav šifrování disku škálovací sady virtuálních počítačů
    - Nová rutina Get-AzureRmVmssVMDiskEncryptionStatus zobrazuje stav šifrování disku virtuálního počítače ve škálovací sadě virtuálních počítačů
* ContainerInstance
  * Přidání rutin PowerShellu pro instance kontejneru Azure
    - New-AzureRmContainerGroup
    - Get-AzureRmContainerGroup
    - Remove-AzureRmContainerGroup
    - Get-AzureRmContainerInstanceLog
* Insights
  * Nová rutina Disable-AzureRmActivityLogAlert
    - Nová rutina pro zakázání existujícího upozornění protokolu aktivit
    - Volitelně je možné s touto rutinou také nastavit značky
  * Nová rutina Enable-AzureRmActivityLogAlert
    - Nová rutina pro povolení existujícího upozornění protokolu aktivit
    - Volitelně je možné s touto rutinou také nastavit značky
  * Nová rutina Get-AzureRmActivityLogAlert
    - Nová rutina pro načtení jednoho nebo více upozornění protokolu aktivit
    - Upozornění je možné načíst podle názvu, skupiny prostředků nebo předplatného
  * Nová rutina New-AzureRmActionGroup
    - Nová rutina pro vytvoření objektu ActionGroup v paměti (bez požadavků)
  * Nová rutina New-AzureRmActivityLogAlertCondition
    - Nová rutina pro vytvoření objektu podmínky typu list pro upozornění protokolu aktivit v paměti (bez požadavků)
  * Nová rutina Set-AzureRmActivityLogAlert
    - Nová rutina pro vytvoření nebo aktualizaci upozornění protokolu aktivit
  * Nová rutina Remove-AzureRmActivityLogAlert
    - Nová rutina pro odebrání jednoho upozornění protokolu aktivit
  * Nová rutina Set-AzureRmActionGroup
    - Nová rutina pro vytvoření nové skupiny akcí nebo aktualizaci existující
  * Nová rutina Get-AzureRmActionGroup
    - Nová rutina pro načtení jedné nebo více skupin akcí
    - Skupiny akcí je možné načíst podle názvu, skupiny prostředků nebo předplatného
  * Nová rutina Remove-AzureRmActionGroup
    - Nová rutina pro odebrání jedné skupiny akcí
  * Nová rutina New-AzureRmActionGroupReceiver
    - Nová rutina pro vytvoření nového příjemce skupiny akcí v paměti
* KeyVault
  * Nové nebo aktualizované rutiny pro podporu obnovitelného odstranění certifikátů ve službě Key Vault
    * Get-AzureKeyVaultCertificate
    * Remove-AzureKeyVaultCertificate
    * Undo-AzureKeyVaultCertificateRemoval
* Síť
  * Přidání podpory služeb koncových bodů do podsítí virtuálních sítí
    - Aktualizace Add-AzureRmVirtualSubnetConfig: Přidání volitelného parametru -ServiceEndpoint
    - Aktualizace New-AzureRmVirtualSubnetConfig: Přidání volitelného parametru -ServiceEndpoint
    - Aktualizace Set-AzureRmVirtualSubnetConfig: Přidání volitelného parametru -ServiceEndpoint
  * Přidání rutiny pro výpis dostupných služeb koncových bodů v daném umístění
    - Get-AzureRmVirtualNetworkAvailableEndpointService
  * Přidání možnosti konfigurovat externí ověřování P2S založené na protokolu RADIUS do následujících rutin
    - New-AzureVirtualNetworkGateway
    - Set-AzureVirtualNetworkGateway
    - Set-AzureRmVirtualNetworkGatewayVpnClientConfig
  * Přidání rutiny umožňující generování profilů VPN pro externí ověřování P2S založené na protokolu RADIUS
    - New-AzureRmVpnClientConfiguration
    - Get-AzureRmVpnClientConfiguration
  * Přidání podpory parametru SKU do veřejných IP adres a nástrojů pro vyrovnávání zatížení
    - Aktualizace New-AzureRMLoadBalancer: Přidání volitelného parametru -Sku
    - Aktualizace New-AzureRMPublicIpAddress: Přidání volitelného parametru -Sku
  * Přidání podpory DisableOutboundSNAT do pravidel nástroje pro vyrovnávání zatížení
    - Aktualizace New-AzureRMLoadBalancerRuleConfig: Přidání volitelného parametru DisableOutboundSNAT
    - Aktualizace Add-AzureRMLoadBalancerRuleConfig: Přidání volitelného parametru DisableOutboundSNAT
    - Aktualizace Set-AzureRMLoadBalancerRuleConfig: Přidání volitelného parametru DisableOutboundSNAT
  * Přidání podpory IkeV2 P2S
    - Aktualizace New-AzureRmVirtualNetworkGateway: Přidání volitelného parametru -VpnClientProtocol s výchozí hodnotou [ "SSTP", "IkeV2" ]
    - Aktualizace Set-AzureRmVirtualNetworkGateway: Přidání volitelného parametru -VpnClientProtocol
  * Přidání podpory vícehodnotových pravidel v pravidlech zabezpečení sítě a platných pravidlech zabezpečení sítě
    - Aktualizace Add-AzureRmNetworkSecurityRuleConfig: Aktualizace parametrů SourcePortRange, DestinationPortRange a SourceAddressPrefix pro příjem seznamu řetězců
    - Aktualizace New-AzureRmNetworkSecurityRuleConfig: Aktualizace parametrů SourcePortRange, DestinationPortRange a SourceAddressPrefix pro příjem seznamu řetězců
    - Aktualizace Set-AzureRmNetworkSecurityRuleConfig: Aktualizace parametrů SourcePortRange, DestinationPortRange a SourceAddressPrefix pro příjem seznamu řetězců
    - Aktualizace Add-AzureRmNetworkSecurityRuleConfig: Aktualizace parametrů SourcePortRange, DestinationPortRange a SourceAddressPrefix pro příjem seznamu řetězců
    - Aktualizace New-AzureRmNetworkSecurityGroup : Aktualizace parametru SecurityRules pro příjem parametrů SourcePortRange, DestinationPortRange a SourceAddressPrefix, což jsou seznamy řetězců v objektu PSSecurityRule
    - Aktualizace Get-AzureRmEffectiveNetworkSecurityGroup: Přidání parametru TagMap
    - Aktualizace Get-AzureRmEffectiveNetworkSecurityGroup: Aktualizace vráceného objektu PSEffectiveSecurityRule o parametry SourcePortRange, DestinationPortRange a SourceAddressPrefix, což jsou seznamy řetězců
  * Přidání podpory Ochrany před útoky DDoS pro virtuální sítě
    - Aktualizace New-AzureRmVirtualNetwork: Přidání přepínacích parametrů EnableDDoSProtection a EnableVmProtection
    - Přidání vlastností EnableDDoSProtection a EnableVmProtection v objektu PSVirtualNetwork
  * Přidání podpory vysoce dostupného interního nástroje pro vyrovnávání zatížení
    - Aktualizace Add-AzureRmLoadBalancerRuleConfig: Přidání přijatelné hodnoty All pro parametr Protocol
    - Aktualizace New-AzureRmLoadBalancerRuleConfig: Přidání přijatelné hodnoty All pro parametr Protocol
    - Aktualizace Set-AzureRmLoadBalancerRuleConfig: Přidání přijatelné hodnoty All pro parametr Protocol
  * Přidání podpory skupin zabezpečení aplikací
    - Přidání New-AzureRmApplicationSecurityGroup
    - Přidání Get-AzureRmApplicationSecurityGroup
    - Přidání Remove-AzureRmApplicationSecurityGroup
    - Aktualizace New-AzureRmNetworkInterface: Přidání volitelných parametrů ApplicationSecurityGroup a ApplicationSecurityGroupId
    - Aktualizace New-AzureRmNetworkInterfaceIpConfig: Přidání volitelných parametrů ApplicationSecurityGroup a ApplicationSecurityGroupId
    - Aktualizace Add-AzureRmNetworkInterfaceIpConfig: Přidání volitelných parametrů ApplicationSecurityGroup a ApplicationSecurityGroupId
    - Aktualizace Set-AzureRmNetworkInterfaceIpConfig: Přidání volitelných parametrů ApplicationSecurityGroup a ApplicationSecurityGroupId
    - Aktualizace New-AzureRmNetworkSecurityRuleConfig: Přidání volitelných parametrů SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup a DestinationApplicationSecurityGroupId
    - Aktualizace Add-AzureRmNetworkSecurityRuleConfig: Přidání volitelných parametrů SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup a DestinationApplicationSecurityGroupId
    - Aktualizace Set-AzureRmNetworkSecurityRuleConfig: Přidání volitelných parametrů SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup a DestinationApplicationSecurityGroupId
  * Přidání nových příkazů pro skripty konfigurace zařízení VPN
    - Get-AzureRmVirtualNetworkGatewaySupportedVpnDevices
    - Get-AzureRmVirtualNetworkGatewayConnectionVpnDeviceConfigScript
* Profil
  * Podpora Start-Job pro rutiny AzureRm
    * Všechny rutiny AzureRm přidávají parametr -AzureRmContext, který může přijímat kontext (výstup rutiny Context)
      - Běžný vzor pro úlohy se ZAKÁZANOU trvalostí kontextu: `Start-Job {param ($context) New-AzureRmVM -AzureRmContext $context [... other parameters]} -ArgumentList (Get-AzureRmContext)`
      - Běžný vzor pro úlohy s POVOLENOU trvalostí kontextu: `Start-Job {New-AzureRmVM [... other parameters]}`
  * Nové rutiny pro zachování přihlášení napříč relacemi:
    - Enable-AzureRmContextAutosave – Povolení trvalosti přihlášení napříč relacemi
    - Disable-AzureRmContextAutosave – Zakázání trvalosti přihlášení napříč relacemi
  * Nové rutiny pro správu informací o kontextu
    - Select-AzureRmContext – Výběr aktivního pojmenovaného kontextu
    - Rename-AzureRmContext – Přejmenování existujícího kontextu pro snadné odkazování
    - Remove-AzureRmContext – Odebrání existujícího kontextu
    - Remove-AzureRmAccount – Odebrání všech přihlašovacích údajů, předplatných a tenantů přidružených k účtu
  * Změny rutin pro správu informací o kontextu:
    - Přidání Scope = (Process | CurrentUser) (Rozsah = (Proces | Aktuální uživatel)) do všech rutin, které mění přihlašovací údaje
    - Get-AzureRmContext – Přidání parametru ListAvailable pro výpis všech uložených kontextů
* Zdroje
  * Přidání rutin Add PolicySetDefinition
    - Rutina New-AzureRmPolicySetDefinition pro vytvoření definice sady zásad
    - Rutina Get-AzureRmPolicySetDefinition pro výpis všech definic sad zásad nebo pro získání definice konkrétní sady zásad
    - Rutina Remove-AzureRmPolicySetDefinition pro odstranění definice sady zásad
    - Rutina Set-AzureRmPolicySetDefinition pro aktualizaci existující definice sady zásad
  * Přidání parametrů -PolicySetDefinition, -Sku a -NotScope do rutin New-AzureRmPolicyAssignment a Set-AzureRmPolicyAssignment
  * Přidání podpory předávání adresy URL zásad do rutin New-AzureRmPolicyDefinition a Set-AzureRmPolicyDefinition
  * Přidání parametru -Mode do rutiny New-AzureRmPolicyDefinition
  * Přidání podpory pro odebrání přiřazení role pomocí objektu PSRoleAssignment
    - Uživatelé nyní můžou pomocí vstupního objektu PSRoleassignmnet a rutiny Remove-AzureRMRoleAssignment odebrat přiřazení role
  * Přidání rutin ManagedApplication
    - Rutina New-AzureRmManagedApplication pro vytvoření spravované aplikace
    - Rutina Get-AzureRmManagedApplication pro výpis všech spravovaných aplikací v rámci předplatného nebo pro získání konkrétní spravované aplikace
    - Rutina Remove-AzureRmManagedApplication pro odstranění spravované aplikace
    - Rutina Set-AzureRmManagedApplication pro aktualizaci existující spravované aplikace
  * Přidání rutin ManagedApplicationDefinition
    - Rutina New-AzureRmManagedApplicationDefinition pro vytvoření definice spravované aplikace s použitím identifikátoru URI souboru ZIP nebo pomocí souborů JSON mainTemplate a createUiDefinition
    - Rutina Get-AzureRmManagedApplicationDefinition pro výpis definic všech spravovaných aplikací v rámci skupiny prostředků nebo pro získání definice konkrétní spravované aplikace
    - Rutina Remove-AzureRmManagedApplicationDefinition pro odstranění definice spravované aplikace
    - Rutina Set-AzureRmManagedApplicationDefinition pro aktualizaci existující definice spravované aplikace
* Sql
  * Přidání podpory pravidel virtuální sítě
    - Přidání rutiny Get-AzureRmSqlServerVirtualNetworkRule, která získá pravidla virtuální sítě podle konkrétního názvu pravidla nebo seznam pravidel virtuální sítě na serveru SQL Azure
    - Přidání rutiny Set-AzureRmSqlServerVirtualNetworkRule, která změní virtuální síť, na kterou dané pravidlo odkazuje
    - Přidání rutiny Remove-AzureRmSqlServerVirtualNetworkRule, která pro server SQL Azure odebere pravidlo virtuální sítě
    - Přidání rutiny New-AzureRmSqlServerVirtualNetworkRule, která pro server SQL Azure vytvoří nové pravidlo virtuální sítě
* Websites
  * Přidání úrovně PremiumV2 pro plány služby App Service
* Azure.Storage
  * Upgrade na Azure Storage Client Library 8.4.0 a Azure Storage DataMovement Library 0.6.1
  * Přidání podpory úrovně PremiumPageBlobTier v rozhraních API pro nahrání a kopírování objektů blob
    - Set-AzureStorageBlobContent
    - Start-AzureStorageBlobCopy
  * Upřesnění formátu výstupu konzoly pro AzureStorageContainer, AzureStorageBlob, AzureStorageQueue a AzureStorageTable
    - Get-AzureStorageContainer
    - Get-AzureStorageBlob
    - Get-AzureStorageQueue
    - Get-AzureStorageTable

## <a name="20170810---version-431"></a>10. srpna 2017 – verze 4.3.1
  * Aktualizace pro opravu potíží s podpisováním sestavení

## <a name="20170807---version-430"></a>7. srpna 2017 – verze 4.3.0
* AnalysisServices
  * Oprava chyby v Set-AzureRmAnalysisServciesServer
    - Když nebyl zadán správce, bude správce odebrán.
  * Přidání BackupBlobContainerUri v New-AzureRmAnalysisServicesServer a Set-AzureRmAnalysisServicesServer
    - Povolení nastavení/zákazu záložního kontejneru objektů blob pro zálohování/obnovení Azure Analysis Services Serveru
  * Aktualizace vyhledávání SKU v New-AzureRmAnalysisServicesServer a Set-AzureRmAnalysisServicesServer
    - Změna naprogramované jednotky SKU na dynamické vyhledávání
  * Add-AzureAnalysisServicesAccount pro podporu přihlašování s využitím instančního objektu
* Automation
  * Změny v rutinách AutomationDSC* pro vyžádání více než 100 záznamů
  * Vyřešení potíží, kdy streamy Verbose přestaly pracovat po volání některých rutin služby Automation (například Get-AzureRmAutomationVariable, Get-AzureRmAutomationJob)
  * Přidání podpory pro správu verzí sestavení NodeConfiguration do StartAzureAutomationDscCompilationJob a ImportAzureAutomationDscNodeConfiguration
  * Opravy chyb pro stávající potíže –oprava potíží s aliasem č. 3775 a alias runOn a podpora pro HybridWorkers
* Compute
  * Set-AzureRmVMAEMExtension: Přidání podpory pro nové velikosti disků typu Premium
  * Set-AzureRmVMAEMExtension: Přidání podpory pro M Series
  * Přidání parametru ForceUpdateTag do Add-AzureRmVmssExtension
  * Přidání parametru Primary do New-AzureRmVmssIpConfig
  * Přidání parametru EnableAcceleratedNetworking do Add-AzureRmVmssNetworkInterfaceConfig
  * Přidání InstanceId do Set-AzureRmVmss
  * Zveřejnění MaintenanceRedeployStatus pro výstup Get-AzureRmVM -Status
  * Zveřejnění Restriction a Capability d tabulkového formátu Get-AzureRmComputeResourceSku
* DataLakeStore
  * Oprava potíží: https://github.com/Azure/azure-powershell/issues/4323
* Centrum událostí
  * Přidání vlastnosti ResourceGroup do NamespaceAttributes
    - ResourceGroup získá název skupiny prostředků, ve které je obor názvů
  * Aktualizace rutin se sadami parametrů pro obor názvů a EventHub pro fungování autorizačního pravidla
    - New-AzureRmEventHubAuthorizationRule – Přidání nového autorizačního pravidla do existujícího oboru názvů nebo EventHubu
    - Get-AzureRmEventHubAuthorizationRule – Získání autorizačního pravidla / seznamu autorizačních pravidel pro existující obor názvů nebo EventHub
    - Set-AzureRmEventHubAuthorizationRule – Aktualizace vlastností existujícího autorizačního pravidla oboru názvů EventHubu
    - Remove-AzureRmEventHubAuthorizationRule – Odstranění existujícího autorizačního pravidla existujícího oboru názvů nebo EventHubu
    - New-AzureRmEventHubKey – Vygenerování nového primárního/sekundárního klíče pro autorizační pravidlo existujícího oboru názvů nebo EventHubu
    - Get-AzureRmEventHubKey – Získání primárního/sekundárního klíče pro autorizační pravidlo existujícího oboru názvů nebo EventHubu
* Síť
    * Přidání podpory pro IPv6 a nový volitelný parametr PeerAddressType
      * New-AzureRmExpressRouteCircuitPeeringConfig:
      * Set-AzureRmExpressRouteCircuitPeeringConfig: Přidání podpory pro IPv6 Přidání nového volitelného parametru
      * Remove-AzureRmExpressRouteCircuitPeeringConfig: Přidání podpory pro IPv6 Přidání nového volitelného parametru
    * Označení parametru -ProbeEnabled jako zastaralého
      - Add-AzureRmApplicationGatewayBackendHttpSettings
      - New-AzureRmApplicationGatewayBackendHttpSettings
      - Set-AzureRmApplicationGatewayBackendHttpSettings
* Profil
    * Ve výchozím nastavení je povoleno shromažďování dat. Microsoft shromažďuje data o využití za účelem zlepšení uživatelského prostředí. Data jsou anonymní a nezahrnují hodnoty argumentů příkazového řádku.
      - Vypnutí této funkce pomocí rutiny Disable-AzureRmDataCollection
      - Zapnutí této funkce pomocí rutiny Enable-AzureRmDataCollection
* Zdroje
    * Přidání podpory pro ověřování rozsahů pro následující rutiny roledefinition a roleassignment před odesláním požadavku do ARM
      - Get-AzureRMRoleAssignment
      - New-AzureRMRoleAssignment
      - Remove-AzureRMRoleAssignment
      - Get-AzureRMRoleDefinition
      - New-AzureRMRoleDefinition
      - Remove-AzureRMRoleDefinition
      - Set-AzureRMRoleDefinition
* ServiceBus
    * Přidání následujících nových rutin pro autorizační pravidla pro obor názvů, frontu a téma. Operace autorizačního pravidla se provádějí na základě nastaveného sady parametru.
     - New-AzureRmServiceBusAuthorizationRule – Přidání nového autorizačního pravidla do existujícího oboru názvů/fronty/tématu služby ServiceBus
     - Get-AzureRmServiceBusAuthorizationRule – Získání autorizačního pravidla / seznamu autorizačních pravidel pro existující obor názvů/frontu/téma služby ServiceBus
     - Set-AzureRmServiceBusAuthorizationRule – Aktualizace vlastností existujícího autorizačního pravidla oboru názvů/fronty/tématu služby ServiceBus
     - New-AzureRmServiceBusKey – Vygenerování nového primárního/sekundárního klíče pro autorizační pravidlo existujícího oboru názvů/fronty/tématu služby ServiceBus
     - Get-AzureRmServiceBusKey – Získání primárního/sekundárního klíče pro autorizační pravidlo existujícího oboru názvů/fronty/tématu služby ServiceBus
     - Remove-AzureRmServiceBusNamespaceAuthorizationRule – Odstranění existujícího autorizačního pravidla oboru názvů/fronty/tématu služby ServiceBus
    * Přidání vlastnosti skupiny prostředků do NamespceAttributes
* Sql
    * Aktualizace rutiny Set-AzureRmSqlServerTransparentDataEncryptionProtector pro zobrazení upozornění a vyžádání potvrzení, pokud je jako typ ochrany šifrování nastavena možnost AzureKeyVault
    * Přidání nových aktualizovaných rutin pro nastavení auditování
      - Rutina Get-AzureRmSqlDatabaseAuditing, která získá nastavení auditování databáze Azure SQL
      - Rutina Get-AzureRmSqlServerAuditing, která získá nastavení auditování serveru Azure SQL
      - Rutina Set-AzureRmSqlDatabaseAuditing, která změní nastavení auditování databáze Azure SQL
      - Rutina Set-AzureRmSqlServerAuditing, která změní nastavení auditování serveru Azure SQL
    * Ukončení podpory pro stávající rutiny zásad auditování
      - Get-AzureRmSqlDatabaseAuditingPolicy
      - Get-AzureRmSqlServerAuditingPolicy
      - Set-AzureRmSqlDatabaseAuditingPolicy
      - Set-AzureRmSqlServerAuditingPolicy
      - Use-AzureRmSqlServerAuditingPolicy
      - Remove-AzureRmSqlDatabaseAuditing
      - Remove-AzureRmSqlServerAuditing
    * Nerozlišování velkých a malých písmen při analýze souboru schémat pro Update-AzureRmSqlSyncGroup
* Úložiště
    * Přidání podpory NetworkRule pro rutiny účtu úložiště v režimu prostředků
      - New-AzureRmStorageAccount
      - Set-AzureRmStorageAccount
      - Get-AzureRmStorageAccountNetworkRuleSet
      - Update-AzureRmStorageAccountNetworkRuleSet
      - Add-AzureRmStorageAccountNetworkRule
      - Remove-AzureRmStorageAccountNetworkRule

## <a name="20170717---version-421"></a>27. července 2017 – verze 4.2.1
* Compute
    - Oprava potíží s rutinami pro vytvoření a aktualizaci snímků disků virtuálních počítačů (odkaz)[https://github.com/azure/azure-powershell/issues/4309]
      - New-AzureRmDisk
      - New-AzureRmSnapshot
      - Update-AzureRmDisk
      - Update-AzureRmSnapshot
* Profil
    - Oprava potíží s neinteraktivním ověřováním uživatelů v RDFE (odkaz) [https://github.com/Azure/azure-powershell/issues/4299]
* ServiceManagement
    - Oprava potíží s neinteraktivním ověřováním uživatelů (odkaz) [https://github.com/Azure/azure-powershell/issues/4299]

## <a name="2017711---version-420"></a>11. července 2017 – verze 4.2.0
* AnalysisServices
    * Přidání nového rozhraní API roviny dat
        - Zavedení rozhraní API pro získání protokolu serveru AS, Export-AzureAnalysisServicesInstanceLog
* Automation
    * Správné nastavení hodnoty TimeZone pro týdenní a měsíční plány pro New-AzureRmAutomationSchedule
        - Další informace najdete u popisu těchto potíží: https://github.com/Azure/azure-powershell/issues/3043
* AzureBatch
    - Přidání nové rutiny Get-AzureBatchJobPreparationAndReleaseTaskStatus
    - Přidání počátečního a koncového rozsahu bajtů pro parametry Get-AzureBatchNodeFileContent
* CognitiveServices
    * Integrace se sadou Cognitive Services Management SDK verze 1.0.0
    * Opravy chyby kontroly délky názvů účtů
* Compute
    * Podpora typu účtu úložiště pro disk Image:
        - Přidání parametru StorageAccountType pro Set-AzureRmImageOsDisk a Add-AzureRmImageDataDisk
    * Funkce PrivateIP a PublicIP v konfiguraci IP VMSS:
        - Přidání názvů PrivateIPAddressVersion, PublicIPAddressConfigurationName,PublicIPAddressConfigurationIdleTimeoutInMinutes, DnsSetting do New-AzureRmVmssIpConfig
        - Přidání parametru PrivateIPAddressVersion pro určení IPv4 nebo IPv6 do New-AzureRmVmssIpConfig
    * Funkce správy výkonu:
        - Přidání přepínacího parametru PerformMaintenance do Restart-AzureRmVM
        - Get-AzureRmVM -Status zobrazuje informace o správě výkonu daného virtuálního počítače
    * Funkce identity virtuálního počítače:
        - Přidání parametru IdentityType do New-AzureRmVMConfig a UpdateAzureRmVM
        - Get-AzureRmVM zobrazuje informace o identitě daného virtuálního počítače
    * Funkce identity VMSS:
        - Přidání parametru IdentityType do New-AzureRmVmssConfig
        - Get-AzureRmVmss zobrazuje informace o identitě daného VMSS
    * Funkce diagnostiky spouštění VMSS:
        - Nová rutina pro nastavení diagnostiky spouštění objektu Vmss: Set-AzureRmVmssBootDiagnostics
        - Přidání parametru BootDiagnostic do New-AzureRmVmssConfig
    * Funkce typu licence VMSS:
        - Přidání parametru LicenseType do New-AzureRmVmssConfig
    * Podpora pro RecoveryPolicyMode:
        - Přidání parametru RecoveryPolicyMode do New-AzureRmVmssConfig
    * Funkce pro SKU výpočetních prostředků:
        - Nová rutina Get-AzureRmComputeResourceSku zobrazuje SKU všech výpočetních prostředků
* DataFactory
    * Ukončení používání New-AzureRmDataFactoryGatewayKey
    * Zavedení funkce klíče ověření brány přidáním New-AzureRmDataFactoryGatewayAuthKey a Get-AzureRmDataFactoryGatewayAuthKey
* DataLakeAnalytics
    * Přidání podpory pro CRUD zásad Compute prostřednictvím následujících příkazů:
        - New-AzureRMDataLakeAnalyticsComputePolicy
        - Get-AzureRMDataLakeAnalyticsComputePolicy
        - Remove-AzureRMDataLakeAnalyticsComputePolicy
        - Update-AzureRMDataLakeAnalyticsComputePolicy
    * Přidání podpory pro metadata relací úloh pro usnadnění práce s opakujícími se úlohami a kanály úloh Následující příkazy byly aktualizovány nebo přidány:
        - Submit-AzureRMDataLakeAnalyticsJob
        - Get-AzureRMDataLakeAnalyticsJob
        - Get-AzureRMDataLakeAnalyticsJobRecurrence
        - Get-AzureRMDataLakeAnalyticsJobPipeline
    * Aktualizace cílové skupiny tokenů pro rozhraní API katalogů a úloh, aby se použila správná konkrétní cílová skupina Data Lake místo cílové skupiny prostředků Azure
* DataLakeStore
    * Přidání podpory pro rotace klíčů služby KeyVault spravovaných uživatelem v rutině Set-AzureRMDataLakeStoreAccount
    * Přidání zásadní aktualizace pro automatickou aktivaci volání `enableKeyVault` po přidání služby KeyVault spravované uživatelem nebo rotaci klíče
    * Aktualizace cílové skupiny tokenů pro rozhraní API katalogů a úloh, aby se použila správná konkrétní cílová skupina Data Lake místo cílové skupiny prostředků Azure
    * Opravy chyby omezující velikost souborů vytvořených nebo připojených pomocí následujících rutin:
        - New-AzureRmDataLakeStoreItem
        - Add-AzureRmDataLakeStoreItemContent
* Dns
    * Oprava chyby ve scénáři propojení pro Get-AzureRmDnsZone
        - Další informace najdete tady: https://github.com/Azure/azure-powershell/issues/4203
* HDInsight
    * Přidání podpory pro povolení/zákaz sady Operations Management Suite (OMS)
    * Nové rutiny
        - Enable-AzureRmHDInsightOperationsManagementSuite
        - Disable-AzureRmHDInsightOperationsManagementSuite
        - Get-AzureRmHDInsightOperationsManagementSuite
    * Přidání nových parametrů pro nastavení vlastních konfigurací Sparku do Add-AzureRmHDInsightConfigValues
        - Parametry SparkDefaults a SparkThriftConf pro Spark 1.6
        - Parametry Spark2Defaults a Spark2ThriftConf pro Spark 2.0
* Insights
    * Problém č. 4215 (žádost o změnu): Odebrání limitu 15 dnů v časovém intervalu pro rutinu Get-AzureRmLog Také menší změny v názvech testů jednotek
    * Problém č. 3957: Oprava pro Get-AzureRmLog
        - Problém č. 1: Back-end vrací záznamy na stránkách po 200 záznamech, které jsou propojené pomocí tokenu pokračování. Zákazníkům tato rutina vracela jenom 200 záznamů, přestože věděli, že je jich víc. K této situaci docházelo bez ohledu na hodnotu nastavenou MaxEvents (kromě případů, kdy tato hodnota byla menší než 200).
        - Problém č. 2: Dokumentace obsahovala nesprávné informace o této rutině, např. výchozí časový interval byla 1 hodina.
        - Oprava č. 1: Rutina teď následuje token pokračování vrácený back-endem, dokud nedosáhne hodnoty MaxEvents nebo konce sady.<br>Výchozí hodnota pro MaxEvents je 1000 a maximální hodnota je 100 000. Libovolná hodnota, která je menší než 1, se pro MaxEvents ignoruje a místo ní se použije výchozí hodnota. Tyto hodnoty a chování se nezměnily, ale nově jsou správně zdokumentované.<br>Byl přidán alias pro MaxEvents (MaxRecords), protože název rutiny už neodkazuje na události (event), ale jenom na protokoly (log).
        - Oprava č. 2: Dokumentace obsahuje správné informace, které jsou podrobnější: nový alias, správný časový interval a správnou výchozí, minimální a maximální hodnotu.
* KeyVault
    * Odebrání e-mailové adresy z dotazu na adresář, pokud je pro rutiny Set-AzureRMKeyVaultAccessPolicy a Remove-AzureRMKeyVaultAccessPolicy zadaný parametr -UserPrincipalName.
      - Obě tyto rutiny teď mají parametr -EmailAddress, který je možné použít místo parametru -UserPrincipalName, pokud je vhodné dotazování na e-mailovou adresu.  Pokud je v adresáři víc než jedna vyhovující e-mailová adresa, rutina selže.
* Síť
    * New-AzureRmIpsecPolicy: Parametry SALifeTimeSeconds a SADataSizeKilobytes už nejsou povinné
        - Výchozí nastavení pro SALifeTimeSeconds je 27 000 sekund
        - Výchozí nastavení pro SADataSizeKilobytes je 102 400 000 KB
    * Přidání podpory pro vlastní konfiguraci šifrovací sady s využitím zásad SSL a zobrazení rozhraní API se všemi možnostmi SSL ve službě Application Gateway
        - Přidání volitelného parametru -PolicyType, -PolicyName, -MinProtocolVersion, -Ciphersuite
            - Add-AzureRmApplicationGatewaySslPolicy
            - New-AzureRmApplicationGatewaySslPolicy
            - Set-AzureRmApplicationGatewaySslPolicy
        - Přidání Get-AzureRmApplicationGatewayAvailableSslOptions (alias: List-AzureRmApplicationGatewayAvailableSslOptions)
        - Přidání Get-AzureRmApplicationGatewaySslPredefinedPolicy (alias: List-AzureRmApplicationGatewaySslPredefinedPolicy)
    * Přidání podpory přesměrování ve službě Application Gateway
        - Přidání Add-AzureRmApplicationGatewayRedirectConfiguration
        - Přidání Get-AzureRmApplicationGatewayRedirectConfiguration
        - Přidání New-AzureRmApplicationGatewayRedirectConfiguration
        - Přidání Remove-AzureRmApplicationGatewayRedirectConfiguration
        - Přidání Set-AzureRmApplicationGatewayRedirectConfiguration
        - Přidání volitelného parametru -RedirectConfiguration
            - Add-AzureRmApplicationGatewayRequestRoutingRule
            - New-AzureRmApplicationGatewayRequestRoutingRule
            - Set-AzureRmApplicationGatewayRequestRoutingRule
        - Přidání volitelného parametru -DefaultRedirectConfiguration
            - Add-AzureRmApplicationGatewayUrlPathMapConfig
            - New-AzureRmApplicationGatewayUrlPathMapConfig
            - Set-AzureRmApplicationGatewayUrlPathMapConfig
        - Přidání volitelného parametru -RedirectConfiguration
            - Add-AzureRmApplicationGatewayPathRuleConfig
            - New-AzureRmApplicationGatewayPathRuleConfig
            - Set-AzureRmApplicationGatewayPathRuleConfig
        - Přidání volitelného parametru -RedirectConfigurations
            - New-AzureRmApplicationGateway
            - Set-AzureRmApplicationGateway
    * Přidání podpory pro weby Azure ve službě Application Gateway
        - Přidání New-AzureRmApplicationGatewayProbeHealthResponseMatch
        - Přidání volitelných parametrů -PickHostNameFromBackendHttpSettings, -MinServers, -Match
            - Add-AzureRmApplicationGatewayProbeConfig
            - New-AzureRmApplicationGatewayProbeConfig
            - Set-AzureRmApplicationGatewayProbeConfig
        - Přidání volitelných parametrů -PickHostNameFromBackendAddress, -AffinityCookieName, -ProbeEnabled, -Path
            - Add-AzureRmApplicationGatewayBackendHttpSettings
            - New-AzureRmApplicationGatewayBackendHttpSettings
            - Set-AzureRmApplicationGatewayBackendHttpSettings
    * Aktualizace Get-AzureRmPublicIPaddress pro načtení prostředků publicipaddress vytvořených pomocí škálovací sady virtuálního počítače
    * Přidání rutiny pro získání aktuálního využití virtuální sítě
        - Get-AzureRmVirtualNetworkUsageList
* Profil
    * Oprava chyby při použití Import-AzureRmContext nebo Save-AzureRmContext
        - Další informace najdete u popisu těchto potíží: https://github.com/Azure/azure-powershell/issues/3954
* RecoveryServices.SiteRecovery
    * Představení nového modulu pro operace Azure Site Recovery
        - Všechny rutiny začínají na AzureRmRecoveryServicesAsr*
* Sql
    * Přidání rutin PowerShellu pro synchronizaci dat do AzureRM.Sql
    * Aktualizace rutin AzureRmSqlServer pro použití nových verzí rozhraní REST API, které se vyhýbají časovým limitům při vytváření serveru
    * Zastaralé rutiny upgradu serveru, protože stará verze serveru (2.0) už neexistuje
    * Přidání nového volitelného přepínacího parametru AssignIdentity do rutin New-AzureRmSqlServer a Set-AzureRmSqlServer pro podporu zřizování identity pro prostředek serveru SQL
    * Parametr ResourceGroupName je teď pro Get-AzureRmSqlServer volitelný
        - Další informace najdete u popisu těchto potíží: https://github.com/Azure/azure-powershell/issues/635
* ServiceManagement pro ExpressRoute:
    * Aktualizace rutiny New-AzureBgpPeering pro přidání těchto nových možností:
        - PeerAddressType: Je možné zadat hodnoty IPv4 nebo IPv6 pro vytvoření partnerského vztahu protokolu BGP pro odpovídající typ adres
    * Aktualizace rutiny Set-AzureBgpPeering pro přidání těchto nových možností:
        - PeerAddressType: Je možné zadat hodnoty IPv4 nebo IPv6 pro aktualizaci partnerského vztahu protokolu BGP pro odpovídající typ adres
    * Aktualizace rutiny Remove-AzureBgpPeering pro přidání těchto nových možností:
        - PeerAddressType: Je možné zadat hodnoty IPv4, IPv6 nebo All pro odebrání partnerského vztahu protokolu BGP pro odpovídající typ adres nebo všech vztahů

## <a name="20170607---version-410"></a>7. června 2017 – verze 4.1.0
* AnalysisServices
    * Přidání nových SKU: B1, B2, S0
    * Přidání podpory pro vertikálně navýšení/snížení kapacity
* CognitiveServices
    * Aktualizace podrobného zobrazení licenčních smluv při vytváření prostředků služeb Cognitive Services
* Compute
    * Oprava Test-AzureRmVMAEMExtension pro virtuální počítače s několika spravovanými disky
    * Aktualizace Set-AzureRmVMAEMExtension: Přidání informací o ukládání do paměti pro spravované disky úrovně Premium
    * Add-AzureRmVhd: Zvýšení omezení velikosti pro VHD na 4 TB
    * Stop-AzureRmVM: Vyjasnění dokumentace pro parametr STayProvisioned
    * New-AzureRmDiskUpdateConfig
      * Zastaralé parametry CreateOption, StorageAccountId, ImageReference, SourceUri, SourceResourceId
    * Set-AzureRmDiskUpdateImageReference: Zastaralá rutina
    * New-AzureRmSnapshotUpdateConfig
      * Zastaralé parametry CreateOption, StorageAccountId, ImageReference, SourceUri, SourceResourceId
    * Set-AzureRmSnapshotUpdateImageReference: Zastaralá rutina
* DataLakeStore
    * Enable-AzureRmDataLakeStoreKeyVault (Enable-AdlStoreKeyVault)
      * Povolení spravovaného šifrování služby KeyVault pro DataLake Store
* DevTestLabs
    * Aktualizace rutin pro práci s aktuální a aktualizovanou verzí rozhraní API služby DevTest Labs
* IotHub
    * Přidání podpory směrování pro rutiny IoTHub
* KeyVault
  * Nové rutiny pro podporu spravovaných klíčů účtu úložiště služby KeyVault
    * Get-AzureKeyVaultManagedStorageAccount
    * Add-AzureKeyVaultManagedStorageAccount
    * Remove-AzureKeyVaultManagedStorageAccount
    * Update-AzureKeyVaultManagedStorageAccount
    * Update-AzureKeyVaultManagedStorageAccountKey
    * Get-AzureKeyVaultManagedStorageSasDefinition
    * Set-AzureKeyVaultManagedStorageSasDefinition
    * Remove-AzureKeyVaultManagedStorageSasDefinition
* Síť
    * Get-AzureRmNetworkUsage: Nová rutina pro zobrazení podrobných informací o kapacitě a využití sítě
    * Přidání nových možností GatewaySku pro VirtualNetworkGateways
        * VpnGw1, VpnGw2, VpnGw3 jsou nové SKU pro brány VPN Gateway
    * Set-AzureRmNetworkWatcherConfigFlowLog
      * Oprava příkladů nápovědy
* NotificationHubs
    * Transparentní aktualizace rutin NotificationHubs pro nové rozhraní API
* Profil
    * Resolve-AzureRmError
      * Nová rutina pro zobrazení podrobných informací o chybách a výjimkách vygenerovaných rutinami, včetně dat požadavku serveru / odpovědi
    * Send-Feedback
      * Povolení odeslání zpětné vazby bez přihlášení
    * Get-AzureRmSubscription
      * Oprava chyby při načítání předplatných CSP
* Zdroje
    * Oprava potíží s Get-AzureRMRoleAssignment, které způsobovaly chybnou žádost, pokud byl počet roleassignments větší než 1000
        * Uživatelé teď můžou použít Get-AzureRMRoleAssignment i v případě, že parametr roleassignments ke vrácení je větší než 1000
* Sql
    * Restore-AzureRmSqlDatabase: Aktualizace příkladu v dokumentaci
* Úložiště
    * Přidání podpory nastavení Add AssignIdentity pro rutiny účtu úložiště v režimu prostředků
        * New-AzureRmStorageAccount
        * Set-AzureRmStorageAccount
    * Přidání podpory zákaznických klíčů pro rutiny účtu úložiště v režimu prostředků
        * Set-AzureRmStorageAccount
        * New-AzureRmStorageAccountEncryptionKeySource
* TrafficManager

    * Nová nastavení monitorování: MonitorIntervalInSeconds, MonitorTimeoutInSeconds, MonitorToleratedNumberOfFailures
    * Nový monitorovací protokol TCP
* ServiceManagement
    * Add-AzureVhd: Zvýšení omezení velikosti pro VHD na 4 TB
    * New-AzureBGPPeering: Podpora režimu LegacyMode
* Azure.Storage
    * Aktualizace nápovědy pro parametry, které přijímají zástupné znaky, a aktualizace typu StorageContext

## <a name="20170523---version-402"></a>23. května 2017 – verze 4.0.2
* Profil
    * Add-AzureRmAccount
      * Přidání aliasu parametru `-EnvironmentName` pro zajištění zpětné kompatibility s AzureRM.profile verze 2.x

## <a name="20170512---version-401"></a>12. května 2017 – verze 4.0.1
 * Oprava potíží s New-AzureStorageContext v offline scénářích: https://github.com/Azure/azure-powershell/issues/3939

## <a name="20170510---version-400"></a>10. května 2017 – verze 4.0.0


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
