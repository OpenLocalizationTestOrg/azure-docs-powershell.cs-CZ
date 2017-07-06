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
ms.openlocfilehash: 143d92384fd270711378f6741ba59e88c12833d1
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2017
---
# <a name="release-notes"></a>Poznámky k verzi

Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.

## <a name="version-220"></a>Verze 2.2.0
* Compute
  - Přidání podpory pro dotazování na stav šifrování z rozšíření AzureDiskEncryptionForLinux
* DataFactory
  - Přidání nové rutiny pro zobrazení seznamu oken aktivit
    + Get-AzureRmDataFactoryActivityWindow
* DataLake
  - Změna parametru `Host` na `DatabaseHost` a přidání aliasu pro `Host`
    + New-AzureRmDataLakeAnalyticsCatalogSecret
    + Set-AzureRmDataLakeAnalyticsCatalogSecret
  - Přidání podpory pro seznam ACL a odebrání výchozího seznamu ACL
  - Přidání podpory pro načtení a nastavení nepojmenovaných oprávnění u souborů a složek
* KeyVault
  - Přidání podpory pro certifikáty
    + Add-AzureKeyVaultCertificate
    + Add-AzureKeyVaultCertificateContact
    + Get-AzureKeyVaultCertificate
    + Get-AzureKeyVaultCertificateContact
    + Get-AzureKeyVaultCertificateIssuer
    + Get-AzureKeyVaultCertificateOperation
    + Get-AzureKeyVaultCertificatePolicy
    + Import-AzureKeyVaultCertificate
    + New-AzureKeyVaultCertificateAdministratorDetails
    + New-AzureKeyVaultCertificateOrganizationDetails
    + New-AzureKeyVaultCertificatePolicy
    + Remove-AzureKeyVaultCertificate
    + Remove-AzureKeyVaultCertificateContact
    + Remove-AzureKeyVaultCertificateIssuer
    + Remove-AzureKeyVaultCertificateOperation
    + Set-AzureKeyVaultCertificateAttribute
    + Set-AzureKeyVaultCertificateIssuer
    + Set-AzureKeyVaultCertificatePolicy
    + Stop-AzureKeyVaultCertificateOperation
* Síť

  - Přidání nového přepínacího parametru síťového rozhraní pro povolení nebo zákaz akcelerovaných síťových služeb -New-AzureRmNetworkInterface -EnableAcceleratedNetworking
  - Povolení rutin PowerShellu pro funkce brány typu aktivní-aktivní
    + Add-AzureRmVirtualNetworkGatewayIpConfig
    + Remove-AzureRmVirtualNetworkGatewayIpConfig
  - Přidání nové rutiny
    + Test-AzureRmPrivateIpAddressAvailability
* Zdroje a prostředky
  - Zóny podpory v rutinách zprostředkovatele a prostředků
    + Get-AzureRmProvider
    + New-AzureRmResource
    + Set-AzureRmResource
* Sql
  - Přidání nových rutin pro správu zásad detekce hrozeb Azure SQL na úrovni serveru
    + Get-AzureRmSqlServerThreatDetectionPolicy
    + Remove-AzureRmSqlServerThreatDetectionPolicy
    + Set-AzureRmSqlServerThreatDetectionPolicy
  - Přidání nových rutin pro podporu povolení/zákazu GeoBackupPolicy pro Sql Azure DataWarehouses
    + Get-AzureRmSqlDatabaseGeoBackupPolicy
    + Set-AzureRmSqlDatabaseGeoBackupPolicy
  - Přidání nových rutin pro Azure Sql Advisor a rozhraní API pro doporučené akce
    + Get-AzureRmSqlDatabaseAdvisor
    + Get-AzureRmSqlElasticPoolAdvisor
    + Get-AzureRmSqlServerAdvisor
    + Get-AzureRmSqlDatabaseRecommendedActions
    + Get-AzureRmSqlElasticPoolRecommendedActions
    + Get-AzureRmSqlServerRecommendedActions
    + Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus
    + Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus
    + Set-AzureRmSqlServerAdvisorAutoExecuteStatus
    + Set-AzureRmSqlDatabaseRecommendedActionState
    + Set-AzureRmSqlElasticPoolRecommendedActionState
    + Set-AzureRmSqlServerRecommendedActionState
