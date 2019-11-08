---
title: Migrieren von Microsoft 365 Business zu Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 5b4ba843-24b8-4526-8e1f-f9b9eab89d06
description: Erfahren Sie, wie Sie Ihr Unternehmen von Microsoft 365 Business auf Microsoft 365 Enterprise E3 migrieren.
ms.openlocfilehash: 1ef32960905f1336f9ac92231d463959e3bfd01c
ms.sourcegitcommit: 5c6c30ec5541d2fb77e53a1309db1fe7b75fc3e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2019
ms.locfileid: "37931853"
---
# <a name="migrate-from-microsoft-365-business-to-microsoft-365-enterprise-e3"></a>Migrieren von Microsoft 365 Business zu Microsoft 365 Enterprise E3

Microsoft 365 Business bietet alles, was Sie für Ihr kleines Unternehmen benötigen, und kombiniert die branchenbesten Cloud-basierten Produktivitäts-apps mit einfacher Geräteverwaltung und Sicherheit, mit denen Ihre Mitarbeiter ihre besten Aufgaben erledigen können. In einigen Fällen müssen Sie jedoch möglicherweise Ihr Microsoft 365 Business-Abonnement zu Microsoft 365 Enterprise migrieren. 

Beispielsweise ist Ihr Unternehmen gewachsen und benötigt mehr als 300 Lizenzen (Herzlichen Glückwunsch).

Oder Ihr Unternehmen benötigt Enterprise-Features wie Office 365 ProPlus, Windows 10 Enterprise E3 oder Enterprise-Client Zugriffs Lizenzen (CALs).

Das Upgrade ist ganz einfach: Sie können das Upgrade [über das Admin Center](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/upgrade-to-different-plan?view=o365-worldwide)initiieren. Alle Ihre Daten und Konfigurationen in Ihrem aktuellen Abonnement werden beibehalten. Es gibt nichts, was Sie tun müssen, um die Migration vorzubereiten und danach nichts zu tun, außer nutzen Sie die neuen Features. 

>[!Note]
>Sie können auch ein Microsoft 365 Business-Abonnement für bis zu 300-Sitze verwenden und ein Microsoft 365 Enterprise E3-Abonnement für mehr als 300 Sitze erhalten. Office 365 ATP ist jedoch nicht in Microsoft 365 Enterprise E3 enthalten. Für fortgesetzten Bedrohungsschutz sollten Sie zusätzliche Office 365 ATP-Lizenzen hinzufügen, damit alle Benutzer im Umfang Ihrer Office 365 ATP Policies lizenziert sind.
>

## <a name="differences-between-microsoft-365-business-and-microsoft-365-enterprise"></a>Unterschiede zwischen Microsoft 365 Business und Microsoft 365 Enterprise

In dieser Tabelle sind die Unterschiede zwischen Microsoft 365 Business und Microsoft 365 Enterprise E3 aufgeführt.

| Feature   | Unterstützung in Microsoft 365 Business | Unterstützung in Microsoft 365 Enterprise E3 | 
|:-------|:-----|:-----|
| **Lokal**       | | | 
| Windows 10    | Windows 10 Business  |    Windows 10 Enterprise E3| 
| Office-Apps *  | [Office 365 Business](#office-365-business)   | Office 365 ProPlus | 
| **Apps für die Cloud-Produktivität**       | | | 
| Exchange Online und Outlook   | 50 GB Speichergrenzwert pro Postfach und unbegrenzte Exchange Online Archivierung   | 100 GB Speichergrenzwert pro Postfach und unbegrenzte Exchange Online Archivierung | 
| Teams | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| OneDrive for Business | 1 TB Speichergrenzwert pro Benutzer   | Unbegrenzt | 
| Jammern, SharePoint Online, Planer, Stream    | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| StaffHub  | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Outlook-Kunden Manager, MileIQ  | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | | 
| **Bedrohungsschutz**     | | | 
| Funktionen zur Verringerung der Angriffsfläche | [Siehe diese Liste](#threat-protection) | Unternehmensverwaltung der hardwarebasierten Isolierung für Microsoft Edge | 
| Office 365 Advanced Threat Protection (ATP) Plan 1 | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)  | Nicht enthalten, kann aber hinzugefügt werden | 
| **Identitätsverwaltung**       | | | 
| Self-Service Password Reset für hybride Azure Active Directory (Azure AD)-Konten, Azure Multi-Factor Authentication (MFA), bedingter Zugriff, Kenn Wort Rückschreiben für lokale Identitäten|    ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png) | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Cloud-App-Ermittlung, Azure AD Connect-Integrität  |   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Einmaliges Anmelden für Azure AD Office 365 Apps (SSO): 10 apps pro Benutzer (Galerie Saas-apps wie Salesforce) * | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png) | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Azure AD Premium 1 SSO: No Limit (lokale Apps über Azure AD Anwendungs Proxy und nicht-Gallery-Apps mithilfe von Self-Service-APP-Integrations Vorlagen)  |   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| **Geräte-und App-Verwaltung**     | | | 
| Microsoft InTune, Windows Autopilot|  ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png) | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
|Virtueller Desktop Zugriff (VDA)   |  |    ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
|Virtueller Windows-Desktop (Oktober)  | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png) |     ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
|Freigegebene Computer Aktivierung (SCA)   | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png) |     ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Microsoft-Desktop Optimierungspaket    | |     ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| **Schutz von Daten**        | | | 
| Office 365 Verhinderung von Datenverlust, Azure Information Protection-Plan 1  | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Schutz von Fenster Informationen für Endpunkt-DLP    | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| **Client Zugriffslizenz (CAL-Rechte)**    | | |   
| Enterprise CAL Suite (Exchange, SharePoint, Skype, Windows, System Center Configuration Manager, Windows Rights Management)| |        ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| **Compliance**        | | | 
| Unbegrenzte e-Mail-Archivierung | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Compliance-Manager    | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| eDiscovery    | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Compliance-Aufbewahrungs-und Beweissicherungsverfahren | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
| Aufbewahrungstags und Aufbewahrungsrichtlinien für die Messaging-Datensatzverwaltung  | ![Im Lieferumfang von Microsoft 365 Business enthalten](./media/check-mark.png)   | ![Im Lieferumfang von Microsoft 365 Enterprise E3 enthalten](./media/check-mark.png) | 
||||

\*Benutzer, denen Zugriff auf Saas-apps zugewiesen wurde, können SSO-Zugriff auf bis zu 10 apps erhalten. Administratoren können SSO konfigurieren und den Benutzer Zugriff auf verschiedene Saas-apps ändern, aber SSO-Zugriff ist nur für 10 apps pro Benutzer gleichzeitig zulässig. Alle Office 365 apps werden als einzelne APP gezählt.

## <a name="migration"></a>Migration

Um zu migrieren, arbeiten Sie mit Ihrem Partner zusammen, um Ihr Microsoft 365 Business-Abonnement und ihre Lizenzen auf ein geeignetes Microsoft 365 Enterprise E3-Abonnement mit seinen Lizenzen zu verschieben.

In den folgenden Abschnitten wird beschrieben, welche Änderungen Sie vornehmen müssen, falls vorhanden, und was Sie nach der Migration tun können.

### <a name="microsoft-365-subscription-configuration-and-data"></a>Microsoft 365-Abonnementkonfiguration und-Daten

Sie müssen vor der Migration keine Änderungen am aktuellen Abonnement oder an den Daten vornehmen, einschließlich:

- Abonnementkonfiguration, wie DNS-Domänennamen.
- Benutzer-und Gruppenkonten und Authentifizierungseinstellungen, beispielsweise mehrstufige Authentifizierung oder Richtlinien für bedingten Zugriff.
- Produktivitäts Dienstkonfigurationen und deren Daten wie Teams, Exchange Online Postfächern, SharePoint Online Websites, OneDrive für Unternehmen Ordnern und OneNote-Notizbüchern.

Ihre Benutzer können jetzt unbegrenzten Speicherplatz in den Exchange Online Postfächern und OneDrive für Unternehmen Ordnern genießen.

Sie können mit der Verwendung der Cloud-App-Ermittlung, Azure AD Connect-Integrität und SSO für mehr als 10 apps beginnen.

>[!Note]
>Benutzer, die zu Microsoft 365 Enterprise E3 migriert wurden, können Outlook-Kunden Manager und MileIQ nicht mehr verwenden.
>

<a name="threat-protection"></a>
### <a name="threat-protection"></a>Bedrohungsschutz

Windows 10 Business umfasst diese Schutzfunktionen:

- Integritäts Erzwingung des Betriebssystem-Startvorgangs
- Integritäts Erzwingung von vertraulichen Betriebskomponenten
- Erweiterte Sicherheitsanfälligkeit und Zero-Day-Exploits zur Schadensminimierung
- Reputations basierter Netzwerkschutz für Microsoft Edge, Internet Explorer und Chrome
- Host basierte Firewall
- Ransomware-Abhilfemaßnahmen
- Hardware basierte Isolierung für Microsoft Edge
- Mit dem intelligenten Sicherheits Diagramm unterstützte Anwendungssteuerung
- Gerätesteuerung (USB)
- Netzwerkschutz für webbasierte Bedrohungen
- Host Intrusion Prevention-Regeln

Windows 10 Enterprise E3 umfasst auch die Unternehmensverwaltung der hardwarebasierten Isolierung für Microsoft Edge.

>[!Note]
>Für Benutzer, die zu Microsoft 365 Enterprise E3 migriert werden, benötigen Sie eine Office 365 ATP-Lizenz für fortgesetzten Bedrohungsschutz. Achten Sie darauf, zusätzliche Office 365 ATP-Lizenzen zu erwerben, damit alle Benutzer im Umfang Ihrer Office 365 ATP Policies lizenziert sind. 
>

### <a name="device-management-with-intune"></a>Geräteverwaltung mit InTune

Vor der Migration müssen Sie keine Änderungen an Ihrer aktuellen InTune-Konfiguration vornehmen, einschließlich der registrierten Geräte und Geräte-und App-Einstellungen.

### <a name="windows-10"></a>Windows 10

Microsoft 365 Business umfasst Windows 10 Business, das Sie mit Windows Autopilot installieren können. Wenn Sie zu Microsoft 365 Enterprise E3 migrieren, enthält jede Benutzerlizenz Windows 10 Enterprise E3, das Sie auch mit Windows Autopilot installieren können.

<a name="office-365-business"></a>
### <a name="office-365-business"></a>Office 365 Business

Der auf Ihren Geräten installierte Office 365 Business-Client beginnt automatisch mit der Verwendung der Features von Office 365 ProPlus. Nach der Migration können Sie nun Folgendes verwenden:

 - Volumenaktivierung über Gruppenrichtlinien
 - App-Telemetrie
 - Aktualisieren von Steuerelementen
 - Kalkulationstabelle vergleichen und Abfragen
 - Business intelligence
