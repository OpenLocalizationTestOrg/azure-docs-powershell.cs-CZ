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
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a>Poznámky k verzi

Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.

## <a name="version-380"></a>Verze 3.8.0
* Compute
  - Oprava chyby v rutinách Get-*, s cílem umožnit načítat více stránek (více než 120 položek).
* DataLakeAnalytics
  - Oprava nápovědy k některým příkazům, aby se používaly správné slovní popisy a příkazy.
* DataLakeStore
  - Přidání podpory pro úvodní a koncovou část k rutině `Get-AzureRMDataLakeStoreItemContent`. To umožňuje vrátit prvních nebo posledních N nových řádků oddělených tabulátory k zobrazení.
* HDInsight
  - Přidaná podpora pro typ clusteru RServer.
    + Velikost virtuálního počítače koncového uzlu je možné pro cluster RServer zadat pomocí New-AzureRmHDInsightCluster nebo New-AzureRmHDInsightClusterConfig.
    + RServer je nově konfigurační možnost v Add-AzureRmHDInsightConfigValues. Umožňuje nastavit příznak RStudio, který indikuje, že je potřeba provést instalaci R Studia.
* LogicApp
  - Jsou opravené rutiny Set-AzureRmIntegrationAccountSchema a Set-AzureRmIntegrationAccountMap a vyřešily se potíže s vlastností contentlink (dřív byly nastavené vlastnosti content i contentlink a to mělo za následek selhání aktualizace).
* Síť
  - K branám Application Gateway byla přidaná podpora pro nové funkce brány webových aplikací.
    + Přidání New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig
    + Přidání Get-AzureRmApplicationGatewayAvailableWafRuleSets (alias: List-AzureRmApplicationGatewayAvailableWafRuleSets)
    + Aktualizace New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Přidání parametrů -RuleSetType, -RuleSetVersion a -DisabledRuleGroups
    + Aktualizace Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Přidání parametrů -RuleSetType, -RuleSetVersion a -DisabledRuleGroups
  - Přidání podpory pro zásady IPSec k připojení bran virtuálních sítí
  - Přidání New-AzureRmIpsecPolicy
  - Aktualizace New-AzureRmVirtualNetworkGatewayConnection: Přidání parametrů -IpsecPolicies a -UsePolicyBasedTrafficSelectors
* Profil
  - *Zastaralé:* Save-AzureRmProfile se přejmenovalo na Save-AzureRmContext. Používá se alias pro starý název rutiny, ale tento alias už v další verzi nebude.
  - *Zastaralé:* Select-AzureRmProfile se přejmenovalo na Import-AzureRmContext. Používá se alias pro starý název rutiny, ale tento alias už v další verzi nebude.
  - Výstupní typy PSAzureContext a PSAzureProfile rutin profilů se v příští verzi změní.
  - Rutina Save-AzureRmContext v příští verzi nebude mít žádný OutputType.
  - Oprava chyb ve společném kódu rutin, aby se pro hodnoty hash dat využíval algoritmus kompatibilní s FIPS: https://github.com/Azure/azure-powershell/issues/3651
* Sql
  - Opravy chyb v rutinách skupin převzetí služeb při selhání Azure
  - Oprava pro cyklické dotazování operací
  - Oprava hodnoty GracePeriodWithDataLossHour při nastavení FailoverPolicy na Manual
* TrafficManager
  - Podpora pro geografickou metodu směrování provozu
    + Nová hodnota Geographic pro parametr TrafficRoutingMethod funkce New-AzureRmTrafficManagerProfile
    + Nový parametr GeoMapping pro New-AzureRmTrafficManagerEndpoint a Add-AzureRmTrafficManagerEndpointConfig
    + Oprava vedení pro Get-AzureRmTrafficManagerProfile, když vrátí kolekci profilů
* ServiceManagement
  - Restart-AzureVM: Přidání parametru InitiateMaintenance pro provádění údržby během restartování virtuálního počítače
  - Get-AzureVM: Přidání pole stavu údržby
  - Přidání nových rutin pro podporu upgradu trezoru služby Recovery Services
    + Test-AzureRecoveryServicesVaultUpgrade
    + Invoke-AzureRecoveryServicesVaultUpgrade
