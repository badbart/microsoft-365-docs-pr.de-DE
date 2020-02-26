---
title: Festlegen, dass das Kennwort eines einzelnen Benutzers nie abläuft
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: In diesem Artikel erfahren Sie, wie Sie mit Windows PowerShell einzelne Benutzerkennwörter so festlegen, dass Sie nie ablaufen.
ms.openlocfilehash: 1c44f5c4d5966d70b5fed0b1b99e69b2938c6ddd
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2020
ms.locfileid: "42241569"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>Festlegen, dass das Kennwort eines einzelnen Benutzers nie abläuft

## <a name="set-the-password-expiration-policy-for-your-organization"></a>Festlegen der Kennwortablaufrichtlinie für Ihre Organisation

1. Wechseln Sie im Admin Center zur Seite **Einstellungen** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">Sicherheit & Privatsphäre</a> .
2. Wählen Sie neben **Kennwortrichtlinie** die Option **Bearbeiten**aus. 
3. Wenn Kennwörter auf nie ablaufen festgelegt sind, legen Sie die Umschaltfläche auf **aus**. Sie erhalten die Option, die Anzahl der Tage anzugeben, bis Kennwörter ablaufen. 


## <a name="set-the-password-expiration-policy-for-individual-users"></a>Festlegen der Kennwortablaufrichtlinie für einzelne Benutzer 

Ein globaler Administrator für einen Microsoft-clouddienst kann das Microsoft Azure AD-Modul für Windows PowerShell verwenden, um Kennwörter festzulegen, die für bestimmte Benutzer nicht ablaufen. Sie können auch Windows PowerShell-Cmdlets verwenden, um die nie ablaufende Konfiguration zu entfernen oder um festzustellen, welche Benutzerkennwörter nie ablaufen. 

Dieses Handbuch gilt für andere Anbieter wie InTune und Office 365, die sich auch auf Azure AD für Identitäts-und Verzeichnisdienste stützen. Das Kennwortablaufdatum ist der einzige Teil der Richtlinie, der geändert werden kann.

> [!NOTE]
> Nur Kennwörter für Benutzerkonten, die nicht über die Verzeichnissynchronisierung synchronisiert werden, können so konfiguriert werden, dass Sie nicht ablaufen. Weitere Informationen zur Verzeichnissynchronisierung finden Sie unter [Connect AD with Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).


### <a name="how-to-check-the-expiration-policy-for-a-password"></a>Überprüfen der Ablaufrichtlinie auf ein Kennwort

* Führen Sie einen der folgenden Befehle aus:

   * Um festzustellen, ob das Kennwort eines einzelnen Benutzers auf nie abläuft, führen Sie das folgende Cmdlet mithilfe des UPN (beispielsweise *user@contoso.onmicrosoft.com*) oder der Benutzer-ID des Benutzers aus, den Sie überprüfen möchten:
```
Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
 }
```  
Beispiel:
```
Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
 }
```  

 * Führen Sie das folgende Cmdlet aus, um die Einstellung **Kennwort läuft nie ab** für alle Benutzer anzuzeigen: 
 
```
Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
 }
```  

* So rufen Sie einen Bericht aller Benutzer mit PasswordNeverExpires in HTML auf dem Desktop des aktuellen Benutzers mit dem Namen **ReportPasswordNeverExpires. html** ab


```
Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
} | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
```  

* So rufen Sie einen Bericht aller Benutzer mit PasswordNeverExpires in CSV auf dem Desktop des aktuellen Benutzers mit dem Namen **ReportPasswordNeverExpires. CSV** ab


```
Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
    N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
} | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv
```  


### <a name="set-a-password-to-expire"></a>Festlegen eines Kennworts zum ablaufen

Führen Sie einen der folgenden Befehle aus:

   * Um das Kennwort eines Benutzers so festzulegen, dass das Kennwort abläuft, führen Sie das folgende Cmdlet mithilfe des UPN oder der Benutzer-ID des Benutzers aus:

```
 Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None

```
   * Verwenden Sie das folgende Cmdlet, um die Kennwörter aller Benutzer in der Organisation so festzulegen, dass Sie ablaufen:

```
 Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None

```
### <a name="set-a-password-to-never-expire"></a>Festlegen eines Kennworts, das nie abläuft

Führen Sie einen der folgenden Befehle aus:

   * Um das Kennwort eines Benutzers so festzulegen, dass es nie abläuft, führen Sie das folgende Cmdlet mithilfe des UPN oder der Benutzer-ID des Benutzers aus: 

```
Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration

```
   * Führen Sie das folgende Cmdlet aus, um die Kennwörter aller Benutzer in einer Organisation so festzulegen, dass Sie nie ablaufen: 

```
Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration

```
   > [!WARNING]
   > Kennwörter, `-PasswordPolicies DisablePasswordExpiration` die auf dem Attribut basierend `pwdLastSet` auf "still Age" festgelegt sind. Wenn Sie festlegen, dass die Benutzerkennwörter nie ablaufen und dann 90 + Tage vergehen, laufen die Kennwörter ab. Wenn Sie den `pwdLastSet` Ablauf in `-PasswordPolicies None`ändern, müssen alle Kennwörter, die `pwdLastSet` älter als 90 Tage sind, basierend auf dem Attribut geändert werden, wenn Sie sich das nächste Mal anmelden. Diese Änderung kann sich auf eine große Anzahl von Benutzern auswirken. 