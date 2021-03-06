---
title: Anzeigen von Microsoft 365-Konto Lizenz-und-Dienstdetails mit PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Erläutert die Verwendung von PowerShell zum Bestimmen der Microsoft 365-Dienste, die Benutzern zugewiesen wurden.
ms.openlocfilehash: 163a92ec31f700aa6157e58b49e23a1cec587815
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690877"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>Anzeigen von Microsoft 365-Konto Lizenz-und-Dienstdetails mit PowerShell

*Dieser Artikel gilt sowohl für Microsoft 365 Enterprise als auch für Office 365 Enterprise.*

In Microsoft 365 ermöglichen Lizenzen aus Lizenzierungs Plänen (auch SKU-oder Microsoft 365-Pläne genannt) Benutzern den Zugriff auf die Microsoft 365-Dienste, die für diese Pläne definiert sind. Ein Benutzer hat möglicherweise aber keinen Zugriff auf alle Dienste, die in einer Lizenz verfügbar sind, die ihm derzeit zugewiesen ist. Sie können PowerShell für Microsoft 365 verwenden, um den Status von Diensten in Benutzerkonten anzuzeigen. 

Weitere Informationen zu Lizenzierungs Plänen, Lizenzen und Diensten finden Sie unter [Anzeigen von Lizenzen und Diensten mit PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Verwenden der Azure Active Directory PowerShell für Graph-Module

Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Als nächstes Listen Sie die Lizenz Pläne für Ihren Mandanten mit diesem Befehl auf.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Verwenden Sie diese Befehle, um die Dienste aufzulisten, die in den einzelnen Lizenzierungs Plänen zur Verfügung stehen.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

Verwenden Sie diese Befehle, um die Lizenzen aufzulisten, die einem Benutzerkonto zugewiesen sind.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Verwenden des Microsoft Azure Active Directory-Moduls für Windows PowerShell

Stellen Sie zunächst [eine Verbindung mit Ihrem Microsoft 365-Mandanten her](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Führen Sie als nächstes den folgenden Befehl aus, um die in Ihrer Organisation verfügbaren Lizenzierungs Pläne aufzulisten. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core unterstützt nicht das Microsoft Azure Active Directory-Modul für Windows PowerShell und Cmdlets mit **Msol** im Namen. Um diese Cmdlets weiterhin verwenden zu können, müssen Sie sie über Windows PowerShell ausführen.
>

Führen Sie als nächstes den folgenden Befehl aus, um die Dienste aufzulisten, die in den einzelnen Lizenzierungs Plänen verfügbar sind, und die Reihenfolge, in der Sie aufgeführt sind (die Indexnummer).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
Verwenden Sie diesen Befehl, um die Lizenzen aufzulisten, die einem Benutzer zugewiesen sind, und die Reihenfolge, in der Sie aufgeführt sind (die Indexnummer).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>So zeigen Sie Dienste für ein Benutzerkonto an

Verwenden Sie die folgende Syntax, um alle Microsoft 365-Dienste anzuzeigen, auf die ein Benutzer Zugriff hat:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

Dieses Beispiel zeigt die Dienste, auf die der Benutzer BelindaN@litwareinc.com Zugriff hat. Es zeigt die Dienste, die allen Lizenzen zugeordnet sind, die dem Konto zugewiesen sind.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

Dieses Beispiel zeigt die Dienste, auf die der Benutzer „BelindaN@litwareinc.com“ ab der ersten Lizenz, die dem Konto zugewiesen ist (die Indexnummer ist 0), zugreifen kann.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Verwenden Sie die folgende Syntax, um alle Dienste für einen Benutzer anzuzeigen, dem *mehrere Lizenzen*zugewiesen wurden:

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a>Siehe auch

[Verwalten von Microsoft 365-Benutzerkonten, -Lizenzen und -Gruppen mit PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Verwalten von Microsoft 365 mit PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Erste Schritte mit PowerShell für Microsoft 365](getting-started-with-microsoft-365-powershell.md)
