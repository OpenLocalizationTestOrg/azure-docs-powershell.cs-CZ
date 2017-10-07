Instalační program Azure PowerShellu 4.3.1: [odkaz](https://github.com/Azure/azure-powershell/releases/download/v4.3.1-August2017/azure-powershell.4.3.1.msi)

Modul galerie pro rutiny ARM: [odkaz](https://www.powershellgallery.com/packages/AzureRM/4.3.1)

Modul galerie pro rutiny starší verze pro Service Management (RDFE): [odkaz](https://www.powershellgallery.com/packages/Azure/4.3.1)

## <a name="changes-in-431"></a>Změny ve verzi 4.3.1

- Oprava potíží s tím, že výsledkem chybějícího podpisu u některých sestavení byla chyba `could not load file or assembly` při importu modulů

## <a name="changes-in-430"></a>Změny ve verzi 4.3.0

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
    * Aktualizace rutin s novým parametrem a aliasem parametru
        - Aktualizace následujících rutin se sadami parametrů pro obor názvů a EventHub pro fungování autorizačního pravidla
        - New-AzureRmEventHubAuthorizationRule
            + Přidání nového autorizačního pravidla do existujícího oboru názvů nebo EventHubu
        - Get-AzureRmEventHubAuthorizationRule
            + Získání autorizačního pravidla / seznamu autorizačních pravidel pro existující obor názvů nebo EventHub
        - Set-AzureRmEventHubAuthorizationRule
            + Aktualizace vlastností existujícího autorizačního pravidla oboru názvů EventHubu
        - Remove-AzureRmEventHubAuthorizationRule
            + Odstranění existujícího autorizačního pravidla existujícího oboru názvů nebo EventHubu
        - New-AzureRmEventHubKey
            + Vygenerování nového primárního/sekundárního klíče pro autorizační pravidlo existujícího oboru názvů nebo EventHubu
        - Get-AzureRmEventHubKey
            + Získání primárního/sekundárního klíče pro autorizační pravidlo existujícího oboru názvů nebo EventHubu
* Síť
    * New-AzureRmExpressRouteCircuitPeeringConfig: Přidání podpory pro IPv6 Přidání nového volitelného parametru
        - PeerAddressType
    * Set-AzureRmExpressRouteCircuitPeeringConfig: Přidání podpory pro IPv6 Přidání nového volitelného parametru
        - PeerAddressType
    * Remove-AzureRmExpressRouteCircuitPeeringConfig: Přidání podpory pro IPv6 Přidání nového volitelného parametru
        - PeerAddressType
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
     - New-AzureRmServiceBusAuthorizationRule
       - Přidání nového autorizačního pravidla do existujícího oboru názvů/fronty/tématu služby ServiceBus
     - Get-AzureRmServiceBusAuthorizationRule
       - Získání autorizačního pravidla / seznamu autorizačních pravidel pro existující obor názvů/frontu/téma služby ServiceBus
     - Set-AzureRmServiceBusAuthorizationRule
       - Aktualizace vlastností existujícího autorizačního pravidla oboru názvů/fronty/tématu služby ServiceBus
     - New-AzureRmServiceBusKey
       - Vygenerování nového primárního/sekundárního klíče pro autorizační pravidlo existujícího oboru názvů/fronty/tématu služby ServiceBus
     - Get-AzureRmServiceBusKey
       - Získání primárního/sekundárního klíče pro autorizační pravidlo existujícího oboru názvů/fronty/tématu služby ServiceBus
     - Remove-AzureRmServiceBusNamespaceAuthorizationRule
       - Odstranění existujícího autorizačního pravidla oboru názvů/fronty/tématu služby ServiceBus
    * Přidání vlastnosti skupiny prostředků do NamespceAttributes
* Sql
    * Aktualizace rutiny Set-AzureRmSqlServerTransparentDataEncryptionProtector pro zobrazení upozornění a vyžádání potvrzení, pokud je jako typ ochrany šifrování nastavena možnost AzureKeyVault
    * Přidání nových aktualizovaných rutin pro nastavení auditování
        - Přidání rutiny Get-AzureRmSqlDatabaseAuditing, která získá nastavení auditování databáze Azure SQL
        - Přidání rutiny Get-AzureRmSqlServerAuditing, která získá nastavení auditování serveru Azure SQL
        - Přidání rutiny Set-AzureRmSqlDatabaseAuditing, která změní nastavení auditování databáze Azure SQL
        - Přidání rutiny Set-AzureRmSqlServerAuditing, která změní nastavení auditování serveru Azure SQL
    * Ukončení podpory pro stávající rutiny zásad auditování
        - Ukončení podpory pro Get-AzureRmSqlDatabaseAuditingPolicy
        - Ukončení podpory pro Get-AzureRmSqlServerAuditingPolicy
        - Ukončení podpory pro Set-AzureRmSqlDatabaseAuditingPolicy
        - Ukončení podpory pro Set-AzureRmSqlServerAuditingPolicy
        - Ukončení podpory pro Use-AzureRmSqlServerAuditingPolicy
        - Ukončení podpory pro Remove-AzureRmSqlDatabaseAuditing
        - Ukončení podpory pro Remove-AzureRmSqlServerAuditing
    * Nerozlišování velkých a malých písmen při analýze souboru schémat pro Update-AzureRmSqlSyncGroup
* Úložiště
    * Přidání podpory NetworkRule pro rutiny účtu úložiště v režimu prostředků
        - New-AzureRmStorageAccount
        - Set-AzureRmStorageAccount
        - Get-AzureRmStorageAccountNetworkRuleSet
        - Update-AzureRmStorageAccountNetworkRuleSet
        - Add-AzureRmStorageAccountNetworkRule
        - Remove-AzureRmStorageAccountNetworkRule

Zobrazit [změny od poslední vydané verze](https://github.com/Azure/azure-powershell/compare/v4.2.1-July2017...v4.3.1-August2017)
