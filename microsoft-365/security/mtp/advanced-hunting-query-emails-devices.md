---
title: Jagd auf Bedrohungen über Geräte, e-Mails, Apps und Identitäten mit Advanced Hunting
description: Untersuchen Sie häufige Jagd Szenarien und Beispielabfragen, die Geräte, e-Mails, Apps und Identitäten abdecken.
keywords: Erweiterte Suche, Office365-Daten, Windows-Geräte, Office365-e-Mails, e-Mails, apps, Identitäten, Bedrohungs Suche, Cyber Threat Hunting, Suche, Abfrage, Telemetrie, Microsoft 365, Microsoft Threat Protection
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 5b2ef4881eabea7e546eb8cd3d164b372b0018ee
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48199830"
---
# <a name="hunt-for-threats-across-devices-emails-apps-and-identities"></a>Jagen nach Bedrohungen auf Geräten, e-Mails, Apps und Identitäten

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gilt für:**
- Microsoft Threat Protection

[Advanced Hunting](advanced-hunting-overview.md) in Microsoft Threat Protection ermöglicht Ihnen eine proaktive Suche nach Bedrohungen in folgenden Bereichen:
- Von Microsoft Defender ATP verwaltete Geräte
- Von Microsoft 365 verarbeitete e-Mails
- Cloud-App-Aktivitäten, Authentifizierungsereignisse und Domänencontroller Aktivitäten nachverfolgt von Microsoft Cloud App Security und Azure ATP

Mit dieser Sichtbarkeitsstufe können Sie schnell nach Bedrohungen suchen, die Abschnitte in Ihrem Netzwerk durchlaufen, einschließlich ausgeklügelter Intrusionen, die in e-Mails oder im Internet eingehen, lokale Berechtigungen erhöhen, privilegierte Domänenanmeldeinformationen erwerben und seitlich auf die Geräte übertragen werden. 

Hier finden Sie allgemeine Techniken und Beispielabfragen basierend auf verschiedenen Jagd Szenarien, mit denen Sie untersuchen können, wie Sie Abfragen bei der Suche nach derart anspruchsvollen Bedrohungen konstruieren könnten.

## <a name="get-entity-info"></a>Entitätsinformationen abrufen
Verwenden Sie diese Abfragen, um zu erfahren, wie Sie schnell Informationen zu Benutzerkonten, Geräten und Dateien abrufen können. 

### <a name="obtain-user-accounts-from-email-addresses"></a>Abrufen von Benutzerkonten aus E-Mail-Adressen
Beim Erstellen von Abfragen über [Tabellen, die Geräte und E-Mail-Nachrichten enthalten](advanced-hunting-schema-tables.md), müssen Sie wahrscheinlich Benutzerkontonamen aus E-Mail-Adressen von Absendern oder Empfängern abrufen. Sie können dies in der Regel entweder für die Empfänger-oder Absenderadresse verwenden, indem Sie den *lokalen Host* aus der e-Mail-Adresse verwenden.

Im Codeausschnitt unten verwenden wir die Kusto-Funktion [ToString ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/tostringfunction) , um den lokalen Host direkt vor den `@` e-Mail-Adressen von Empfängern in der Spalte zu extrahieren `RecipientEmailAddress` .

```kusto
//Query snippet showing how to extract the account name from an email address
AccountName = tostring(split(RecipientEmailAddress, "@")[0])
```
Die folgende Abfrage zeigt, wie dieser Codeausschnitt verwendet werden kann:

```kusto
EmailEvents
| where Timestamp > ago(7d)
| project RecipientEmailAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
```

### <a name="merge-the-identityinfo-table"></a>Zusammenführen der IdentityInfo-Tabelle

Sie können Kontonamen und andere Kontoinformationen abrufen, indem Sie die [IdentityInfo-Tabelle](advanced-hunting-identityinfo-table.md)zusammenführen oder beitreten. Die folgende Abfrage ruft die Liste der Phishing-und Schadsoftware-Erkennungen in der [EmailEvents-Tabelle](advanced-hunting-emailevents-table.md) ab und verknüpft diese Informationen dann mit der `IdentityInfo` Tabelle, um detaillierte Informationen zu den einzelnen Empfängern zu erhalten. 

```kusto
EmailEvents
| where Timestamp > ago(7d)
//Get email processing events where the messages were identified as either phishing or malware
| where MalwareFilterVerdict == 'Malware' or PhishFilterVerdict == 'Phish'
//Merge email events with identity info to get recipient details
| join (IdentityInfo | distinct AccountUpn, AccountDisplayName, JobTitle, 
Department, City, Country) on $left.RecipientEmailAddress == $right.AccountUpn 
//Show important message and recipient details
| project Timestamp, NetworkMessageId, Subject, PhishFilterVerdict, MalwareFilterVerdict,
SenderFromAddress, RecipientEmailAddress, AccountDisplayName, JobTitle, 
Department, City, Country
```

### <a name="get-device-information"></a>Abrufen von Geräteinformationen
Das [Advanced Hunting-Schema](advanced-hunting-schema-tables.md) stellt umfangreiche Geräteinformationen in verschiedenen Tabellen zur Verfügung. Beispielsweise bietet die [deviceInfo-Tabelle](advanced-hunting-deviceinfo-table.md) umfassende Geräteinformationen basierend auf Ereignisdaten, die regelmäßig aggregiert werden. Diese Abfrage verwendet die `DeviceInfo` Tabelle, um zu überprüfen, ob sich ein potenziell gefährdeter Benutzer ( `<account-name>` ) an einem Gerät angemeldet hat, und listet dann die Warnungen auf, die auf diesen Geräten ausgelöst wurden.

>[!Tip]
> Diese Abfrage verwendet, `kind=inner` um einen [Inner Join](https://docs.microsoft.com/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor)anzugeben, der die Deduplizierung von Werten für linke Seiten verhindert `DeviceId` .

```kusto
DeviceInfo
//Query for devices that the potentially compromised account has logged onto
| where LoggedOnUsers contains '<account-name>'
| distinct DeviceId
//Crosscheck devices against alert records in AlertEvidence and AlertInfo tables
| join kind=inner AlertEvidence on DeviceId
| project AlertId
//List all alerts on devices that user has logged on to
| join AlertInfo on AlertId
| project AlertId, Timestamp, Title, Severity, Category 
```

## <a name="hunting-scenarios"></a>Suchszenarien

### <a name="list-logon-activities-of-users-that-received-emails-that-were-not-zapped-successfully"></a>Auflisten von Anmeldeaktivitäten von Benutzern, die e-Mails empfangen haben, die nicht erfolgreich gezappt wurden
[Zero-Hour Auto Purge (zap)](../office-365-security/zero-hour-auto-purge.md) adressiert schädliche e-Mails, nachdem Sie empfangen wurden. Wenn zap fehlschlägt, wird möglicherweise böswilliger Code auf dem Gerät ausgeführt, und die Konten werden kompromittiert. Diese Abfrage sucht nach Anmeldeaktivitäten, die von den Empfängern von e-Mails vorgenommen wurden, die von Zap nicht erfolgreich behandelt wurden.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfully
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

### <a name="get-logon-attempts-by-domain-accounts-targeted-by-credential-theft"></a>Abrufen von Anmeldeversuchen durch Domänenkonten, die von Anmeldeinformationen Diebstahl betroffen sind
Diese Abfrage identifiziert zunächst alle Zugriffs Warnungen für Anmeldeinformationen in der `AlertInfo` Tabelle. Anschließend wird die Tabelle zusammengeführt oder verknüpft `AlertEvidence` , die Sie für die Namen der Zielkonten und Filter für Domänen verbundene Konten analysiert. Schließlich wird die Tabelle überprüft, `IdentityLogonEvents` um alle Anmeldeaktivitäten von den mit der Domäne verbundenen Zielkonten abzurufen.

```kusto
AlertInfo
| where Timestamp > ago(30d)
//Get all credential access alerts
| where Category == "CredentialAccess"
//Get more info from AlertEvidence table to get the SID of the target accounts
| join AlertEvidence on AlertId
| extend IsJoined=(parse_json(AdditionalFields).Account.IsDomainJoined)
| extend TargetAccountSid=tostring(parse_json(AdditionalFields).Account.Sid)
//Filter for domain-joined accounts only
| where IsJoined has "true"
//Merge with IdentityLogonEvents to get all logon attempts by the potentially compromised target accounts
| join kind=inner IdentityLogonEvents on $left.TargetAccountSid == $right.AccountSid
//Show only pertinent info, such as account name, the app or service, protocol, the accessed device, and type of logon
| project AccountDisplayName, TargetAccountSid, Application, Protocol, DeviceName, LogonType
```

### <a name="check-if-files-from-a-known-malicious-sender-are-on-your-devices"></a>Überprüfen, ob Dateien bekannter bösartiger Absender auf Ihren Geräten vorhanden sind
Wenn Sie wissen, dass eine e-Mail-Adresse schädliche Dateien sendet ( `MaliciousSender@example.com` ), können Sie diese Abfrage ausführen, um zu ermitteln, ob Dateien von diesem Absender auf Ihren Geräten vorhanden sind. Sie können diese Abfrage beispielsweise verwenden, um Geräte zu identifizieren, die von einer Malware Verteilungs Kampagne betroffen sind.

```kusto
EmailAttachmentInfo
| where SenderFromAddress =~ "MaliciousSender@example.com"
//Get emails with attachments identified by a SHA-256
| where isnotempty(SHA256)
| join (
//Check devices for any activity involving the attachments
DeviceFileEvents
| project FileName, SHA256
) on SHA256
| project Timestamp, FileName , SHA256, DeviceName, DeviceId,  NetworkMessageId, SenderFromAddress, RecipientEmailAddress
```

### <a name="review-logon-attempts-after-receipt-of-malicious-emails"></a>Überprüfen von Anmeldeversuchen nach dem Empfang von bösartigen E-Mails
Diese Abfrage ermittelt die 10 neuesten Anmeldungen, die von E-Mail-Empfängern innerhalb von 30 Minuten nach dem Empfang bekannter bösartiger E-Mails ausgeführt wurden. Sie können diese Abfrage verwenden, um zu überprüfen, ob die Konten der E-Mail-Empfänger kompromittiert wurden.

```kusto
//Define new table for malicious emails
let MaliciousEmails=EmailEvents
//List emails detected as malware, getting only pertinent columns
| where MalwareFilterVerdict == "Malware"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
MaliciousEmails
| join (
//Merge malicious emails with logon events to find logons by recipients
IdentityLogonEvents
| project LogonTime = Timestamp, AccountName, DeviceName
) on AccountName 
//Check only logons within 30 minutes of receipt of an email
| where (LogonTime - TimeEmail) between (0min.. 30min)
| take 10
```

### <a name="review-powershell-activities-after-receipt-of-emails-from-known-malicious-sender"></a>Überprüfen von PowerShell-Aktivitäten nach dem Empfang von E-Mails von bekannten bösartigen Absendern
Bösartige E-Mail-Nachrichten enthalten häufig Dokumente und andere speziell gestaltete Anlagen, die PowerShell-Befehle ausführen, um zusätzliche Nutzlasten zu übertragen. Wenn Sie wissen, dass e-Mails von einem bekannten böswilligen Absender ( `MaliciousSender@example.com` ) stammen, können Sie diese Abfrage verwenden, um PowerShell-Aktivitäten aufzulisten und zu überprüfen, die innerhalb von 30 Minuten nach dem Empfang einer e-Mail vom Absender aufgetreten sind.  

```kusto
//Define new table for emails from specific sender
let EmailsFromBadSender=EmailEvents
| where SenderFromAddress =~ "MaliciousSender@example.com"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
//Merge emails from sender with process-related events on devices
EmailsFromBadSender
| join (
DeviceProcessEvents
//Look for PowerShell activity
| where FileName =~ "powershell.exe"
//Add line below to check only events initiated by Outlook
//| where InitiatingProcessParentFileName =~ "outlook.exe"
| project TimeProc = Timestamp, AccountName, DeviceName, InitiatingProcessParentFileName, InitiatingProcessFileName, FileName, ProcessCommandLine
) on AccountName 
//Check only PowerShell activities within 30 minutes of receipt of an email
| where (TimeProc - TimeEmail) between (0min.. 30min)
```

## <a name="related-topics"></a>Verwandte Themen
- [Übersicht über die erweiterte Suche](advanced-hunting-overview.md)
- [Lernen der Abfragesprache](advanced-hunting-query-language.md)
- [Arbeiten mit Abfrageergebnissen](advanced-hunting-query-results.md)
- [Verwenden freigegebener Abfragen](advanced-hunting-shared-queries.md)
- [Grundlegendes zum Schema](advanced-hunting-schema-tables.md)
- [Anwenden bewährter Methoden für Abfragen](advanced-hunting-best-practices.md)
