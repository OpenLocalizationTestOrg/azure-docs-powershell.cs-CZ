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
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a><span data-ttu-id="3d129-103">Poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="3d129-103">Release notes</span></span>

<span data-ttu-id="3d129-104">Toto je seznam změn provedených v této vydané verzi Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="3d129-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <a name="version-220"></a><span data-ttu-id="3d129-105">Verze 2.2.0</span><span class="sxs-lookup"><span data-stu-id="3d129-105">Version 2.2.0</span></span>
* <span data-ttu-id="3d129-106">Compute</span><span class="sxs-lookup"><span data-stu-id="3d129-106">Compute</span></span>
  - <span data-ttu-id="3d129-107">Přidání podpory pro dotazování na stav šifrování z rozšíření AzureDiskEncryptionForLinux</span><span class="sxs-lookup"><span data-stu-id="3d129-107">Add support for querying encryption status from the AzureDiskEncryptionForLinux extension</span></span>
* <span data-ttu-id="3d129-108">DataFactory</span><span class="sxs-lookup"><span data-stu-id="3d129-108">DataFactory</span></span>
  - <span data-ttu-id="3d129-109">Přidání nové rutiny pro zobrazení seznamu oken aktivit</span><span class="sxs-lookup"><span data-stu-id="3d129-109">Added new cmdlet for listing activity windows</span></span>
    + <span data-ttu-id="3d129-110">Get-AzureRmDataFactoryActivityWindow</span><span class="sxs-lookup"><span data-stu-id="3d129-110">Get-AzureRmDataFactoryActivityWindow</span></span>
* <span data-ttu-id="3d129-111">DataLake</span><span class="sxs-lookup"><span data-stu-id="3d129-111">DataLake</span></span>
  - <span data-ttu-id="3d129-112">Změna parametru `Host` na `DatabaseHost` a přidání aliasu pro `Host`</span><span class="sxs-lookup"><span data-stu-id="3d129-112">Changed parameter `Host` to `DatabaseHost` and added alias to `Host`</span></span>
    + <span data-ttu-id="3d129-113">New-AzureRmDataLakeAnalyticsCatalogSecret</span><span class="sxs-lookup"><span data-stu-id="3d129-113">New-AzureRmDataLakeAnalyticsCatalogSecret</span></span>
    + <span data-ttu-id="3d129-114">Set-AzureRmDataLakeAnalyticsCatalogSecret</span><span class="sxs-lookup"><span data-stu-id="3d129-114">Set-AzureRmDataLakeAnalyticsCatalogSecret</span></span>
  - <span data-ttu-id="3d129-115">Přidání podpory pro seznam ACL a odebrání výchozího seznamu ACL</span><span class="sxs-lookup"><span data-stu-id="3d129-115">Add support for ACL and Default ACL removal</span></span>
  - <span data-ttu-id="3d129-116">Přidání podpory pro načtení a nastavení nepojmenovaných oprávnění u souborů a složek</span><span class="sxs-lookup"><span data-stu-id="3d129-116">Add support for getting and setting unnamed permissions on files and folders</span></span>
* <span data-ttu-id="3d129-117">KeyVault</span><span class="sxs-lookup"><span data-stu-id="3d129-117">KeyVault</span></span>
  - <span data-ttu-id="3d129-118">Přidání podpory pro certifikáty</span><span class="sxs-lookup"><span data-stu-id="3d129-118">Add support for certificates</span></span>
    + <span data-ttu-id="3d129-119">Add-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="3d129-119">Add-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="3d129-120">Add-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="3d129-120">Add-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="3d129-121">Get-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="3d129-121">Get-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="3d129-122">Get-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="3d129-122">Get-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="3d129-123">Get-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="3d129-123">Get-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="3d129-124">Get-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="3d129-124">Get-AzureKeyVaultCertificateOperation</span></span>
    + <span data-ttu-id="3d129-125">Get-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="3d129-125">Get-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="3d129-126">Import-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="3d129-126">Import-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="3d129-127">New-AzureKeyVaultCertificateAdministratorDetails</span><span class="sxs-lookup"><span data-stu-id="3d129-127">New-AzureKeyVaultCertificateAdministratorDetails</span></span>
    + <span data-ttu-id="3d129-128">New-AzureKeyVaultCertificateOrganizationDetails</span><span class="sxs-lookup"><span data-stu-id="3d129-128">New-AzureKeyVaultCertificateOrganizationDetails</span></span>
    + <span data-ttu-id="3d129-129">New-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="3d129-129">New-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="3d129-130">Remove-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="3d129-130">Remove-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="3d129-131">Remove-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="3d129-131">Remove-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="3d129-132">Remove-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="3d129-132">Remove-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="3d129-133">Remove-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="3d129-133">Remove-AzureKeyVaultCertificateOperation</span></span>
    + <span data-ttu-id="3d129-134">Set-AzureKeyVaultCertificateAttribute</span><span class="sxs-lookup"><span data-stu-id="3d129-134">Set-AzureKeyVaultCertificateAttribute</span></span>
    + <span data-ttu-id="3d129-135">Set-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="3d129-135">Set-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="3d129-136">Set-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="3d129-136">Set-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="3d129-137">Stop-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="3d129-137">Stop-AzureKeyVaultCertificateOperation</span></span>
* <span data-ttu-id="3d129-138">Síť</span><span class="sxs-lookup"><span data-stu-id="3d129-138">Network</span></span>

  - <span data-ttu-id="3d129-139">Přidání nového přepínacího parametru síťového rozhraní pro povolení nebo zákaz akcelerovaných síťových služeb -New-AzureRmNetworkInterface -EnableAcceleratedNetworking</span><span class="sxs-lookup"><span data-stu-id="3d129-139">New switch parameter added for network interface to enable/disable accelerated networking +New-AzureRmNetworkInterface -EnableAcceleratedNetworking</span></span>
  - <span data-ttu-id="3d129-140">Povolení rutin PowerShellu pro funkce brány typu aktivní-aktivní</span><span class="sxs-lookup"><span data-stu-id="3d129-140">Enable Active-Active gateway feature PowerShell cmdlets</span></span>
    + <span data-ttu-id="3d129-141">Add-AzureRmVirtualNetworkGatewayIpConfig</span><span class="sxs-lookup"><span data-stu-id="3d129-141">Add-AzureRmVirtualNetworkGatewayIpConfig</span></span>
    + <span data-ttu-id="3d129-142">Remove-AzureRmVirtualNetworkGatewayIpConfig</span><span class="sxs-lookup"><span data-stu-id="3d129-142">Remove-AzureRmVirtualNetworkGatewayIpConfig</span></span>
  - <span data-ttu-id="3d129-143">Přidání nové rutiny</span><span class="sxs-lookup"><span data-stu-id="3d129-143">Added new cmdlet</span></span>
    + <span data-ttu-id="3d129-144">Test-AzureRmPrivateIpAddressAvailability</span><span class="sxs-lookup"><span data-stu-id="3d129-144">Test-AzureRmPrivateIpAddressAvailability</span></span>
* <span data-ttu-id="3d129-145">Zdroje a prostředky</span><span class="sxs-lookup"><span data-stu-id="3d129-145">Resources</span></span>
  - <span data-ttu-id="3d129-146">Zóny podpory v rutinách zprostředkovatele a prostředků</span><span class="sxs-lookup"><span data-stu-id="3d129-146">Support zones in provider and resource cmdlets</span></span>
    + <span data-ttu-id="3d129-147">Get-AzureRmProvider</span><span class="sxs-lookup"><span data-stu-id="3d129-147">Get-AzureRmProvider</span></span>
    + <span data-ttu-id="3d129-148">New-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="3d129-148">New-AzureRmResource</span></span>
    + <span data-ttu-id="3d129-149">Set-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="3d129-149">Set-AzureRmResource</span></span>
* <span data-ttu-id="3d129-150">Sql</span><span class="sxs-lookup"><span data-stu-id="3d129-150">Sql</span></span>
  - <span data-ttu-id="3d129-151">Přidání nových rutin pro správu zásad detekce hrozeb Azure SQL na úrovni serveru</span><span class="sxs-lookup"><span data-stu-id="3d129-151">Added new cmdlets for Azure SQL threat detection policy management at server level</span></span>
    + <span data-ttu-id="3d129-152">Get-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="3d129-152">Get-AzureRmSqlServerThreatDetectionPolicy</span></span>
    + <span data-ttu-id="3d129-153">Remove-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="3d129-153">Remove-AzureRmSqlServerThreatDetectionPolicy</span></span>
    + <span data-ttu-id="3d129-154">Set-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="3d129-154">Set-AzureRmSqlServerThreatDetectionPolicy</span></span>
  - <span data-ttu-id="3d129-155">Přidání nových rutin pro podporu povolení/zákazu GeoBackupPolicy pro Sql Azure DataWarehouses</span><span class="sxs-lookup"><span data-stu-id="3d129-155">Added new cmdlets to support enabling/disabling GeoBackupPolicy for Sql Azure DataWarehouses</span></span>
    + <span data-ttu-id="3d129-156">Get-AzureRmSqlDatabaseGeoBackupPolicy</span><span class="sxs-lookup"><span data-stu-id="3d129-156">Get-AzureRmSqlDatabaseGeoBackupPolicy</span></span>
    + <span data-ttu-id="3d129-157">Set-AzureRmSqlDatabaseGeoBackupPolicy</span><span class="sxs-lookup"><span data-stu-id="3d129-157">Set-AzureRmSqlDatabaseGeoBackupPolicy</span></span>
  - <span data-ttu-id="3d129-158">Přidání nových rutin pro Azure Sql Advisor a rozhraní API pro doporučené akce</span><span class="sxs-lookup"><span data-stu-id="3d129-158">Added new cmdlets for Azure Sql Advisors and Recommended Actions APIs</span></span>
    + <span data-ttu-id="3d129-159">Get-AzureRmSqlDatabaseAdvisor</span><span class="sxs-lookup"><span data-stu-id="3d129-159">Get-AzureRmSqlDatabaseAdvisor</span></span>
    + <span data-ttu-id="3d129-160">Get-AzureRmSqlElasticPoolAdvisor</span><span class="sxs-lookup"><span data-stu-id="3d129-160">Get-AzureRmSqlElasticPoolAdvisor</span></span>
    + <span data-ttu-id="3d129-161">Get-AzureRmSqlServerAdvisor</span><span class="sxs-lookup"><span data-stu-id="3d129-161">Get-AzureRmSqlServerAdvisor</span></span>
    + <span data-ttu-id="3d129-162">Get-AzureRmSqlDatabaseRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="3d129-162">Get-AzureRmSqlDatabaseRecommendedActions</span></span>
    + <span data-ttu-id="3d129-163">Get-AzureRmSqlElasticPoolRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="3d129-163">Get-AzureRmSqlElasticPoolRecommendedActions</span></span>
    + <span data-ttu-id="3d129-164">Get-AzureRmSqlServerRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="3d129-164">Get-AzureRmSqlServerRecommendedActions</span></span>
    + <span data-ttu-id="3d129-165">Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="3d129-165">Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="3d129-166">Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="3d129-166">Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="3d129-167">Set-AzureRmSqlServerAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="3d129-167">Set-AzureRmSqlServerAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="3d129-168">Set-AzureRmSqlDatabaseRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="3d129-168">Set-AzureRmSqlDatabaseRecommendedActionState</span></span>
    + <span data-ttu-id="3d129-169">Set-AzureRmSqlElasticPoolRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="3d129-169">Set-AzureRmSqlElasticPoolRecommendedActionState</span></span>
    + <span data-ttu-id="3d129-170">Set-AzureRmSqlServerRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="3d129-170">Set-AzureRmSqlServerRecommendedActionState</span></span>
