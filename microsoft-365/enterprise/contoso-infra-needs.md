---
title: IT-Infrastruktur und geschäftliche Anforderungen von Contoso
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 10/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Hier erfahren Sie, wie die grundlegende Struktur der lokalen IT-Infrastruktur von Contoso und wie die geschäftlichen Anforderungen von Microsoft 365 für Unternehmen erfüllt wurden.
ms.openlocfilehash: 3dd744a8d936307c61303bf8ba0f2f198af59d91
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46685830"
---
# <a name="contosos-it-infrastructure-and-business-needs"></a>IT-Infrastruktur und geschäftliche Anforderungen von Contoso

Contoso ist dabei, von der lokalen zentralen IT-Infrastruktur auf eine cloudeinschließende Infrastruktur umzustellen, die aus cloudbasierten persönlichen Produktivitätsarbeitslasten und Anwendungen besteht.

## <a name="contosos-existing-it-infrastructure"></a>Contosos vorhandene IT-Infrastruktur

Contoso nutzt eine weitestgehend zentrale lokale IT-Infrastruktur mit Anwendungsrechenzentren in der Pariser Zentrale.

Abbildung 1 zeigt eine Unternehmenszentrale mit Anwendungsrechenzentren, einer DMZ und Internet.

![Contosos vorhandene IT-Infrastruktur](../media/contoso-infra-needs/contoso-infra-needs-fig1.png)

**Abbildung 1: Contosos vorhandene IT-Infrastruktur**
 
In den lokalen Anwendungsrechenzentren wird Folgendes gehostet: 

- Benutzerdefinierte Branchenanwendungen, die SQL Server und andere Linux-Datenbanken verwenden.
- Eine Reihe von älteren SharePoint-Servern.
- Server auf Organisations- und Teamebene für das Speichern von Dateien.

Darüber hinaus unterstützt jedes regionales Hub-Büro eine Reihe von Servern mit einer ähnlichen Gruppe von Anwendungen. Diese Server werden von regionalen IT-Abteilungen gesteuert.

Die Durchsuchbarkeit über die Anwendungen und Daten dieser separaten Rechenzentren an mehreren geografischen Standorten hinweg bleibt eine Herausforderung.

In der DMZ am Hauptsitz von Contoso bieten verschiedene Servergruppen Folgendes:

- Hosting der öffentlichen Contoso-Website, über die Kunden Produkte, Teile, Zubehör oder Dienstleistungen bestellen können.
- Hosting für das Contoso-Partnerextranet für die Kommunikation und Zusammenarbeit mit Partnern.
- VPN-basierter Remotezugriff (virtuelles privates Netzwerk) auf das Contoso-Intranet und Webproxyfunktion für Mitarbeiter in der Pariser Zentrale.

## <a name="contosos-business-needs"></a>Contosos Geschäftsanforderungen

Die Geschäftsanforderungen von Contoso können in fünf Hauptkategorien unterteilt werden.

Produktivität:

- Vereinfachen der Zusammenarbeit

  Ersetzen Sie die auf E-Mails und Dateifreigaben basierte Zusammenarbeit durch ein Onlinemodell, das Echtzeitänderungen an Dokumenten, einfachere Onlinebesprechungen und erfasste Unterhaltungsthreads ermöglicht.
- Mehr Produktivität für Telearbeiter und Mobilmitarbeiter

  Viele Mitarbeiter arbeiten von zu Hause aus oder unterwegs – ersetzen Sie daher die zu Engpässen führende VPN-Lösung durch leistungsstarken Zugriff auf Contoso-Daten und -Ressourcen in der Cloud.
- Mehr Kreativität und Innovation

  Nutzen Sie die Vorteile der neuesten visuellen Lern- und Ideenfindungsmethoden, einschließlich Freihand und 3D-Visualisierung.

Sicherheit:

- Identitäts- und Zugriffsverwaltung

  Erzwingen Sie die mehrstufige Authentifizierung und andere Formen der Authentifizierung, und schützen Sie Anmeldeinformationen von Benutzer- und Administratorkonten.

- Bedrohungsschutz

  Schutz vor externen Sicherheitsrisiken, einschließlich Schadsoftware, die auf E-Mails oder dem Betriebssystem basiert.

- Schutz von Daten

  Sperren Sie den Zugriff auf wichtige digitale Ressourcen, und verschlüsseln Sie diese (z. B. Kundendaten, Entwurfs- und Fertigungsspezifikationen und Mitarbeiterinformationen).

- Sicherheitsverwaltung

  Überwachen des Sicherheitszustands und Ermitteln von sowie Reagieren auf Bedrohungen in Echtzeit.

Remote- und Mobilzugriff und Geschäftspartner:

- Mehr Sicherheit für Telearbeiter und Mobilmitarbeiter

  Führen Sie BYOD (Bring Your Own Device) und die Verwaltung von firmeneigenen Geräten ein, um einen sicheren Zugriff, ein korrektes Anwendungsverhalten sowie den Schutz von Unternehmensdaten zu gewährleisten.

- Verkleinern der Remotezugriffsinfrastruktur für Mitarbeiter

  Senken Sie die Wartungs- und Supportkosten, und verbessern Sie die Leistung für Remotezugriffslösungen, indem Sie Ressourcen, auf die häufig zugegriffen wird, in die Cloud verschieben.

- Bessere Konnektivität und weniger Aufwand für Business-to-Business-Transaktionen (B2B)

  Ersetzen Sie das in die Jahre gekommene Partnerextranet durch eine cloudbasierte Lösung, für die Verbundauthentifizierung verwendet wird.

Compliance:

- Einhalten von regionalen gesetzlichen Vorschriften

  Halten Sie branchenübliche und regionale Vorschriften für Datenspeicherung, Verschlüsselung und Datenschutz sowie Vorschriften für personenbezogene Daten ein, z. B. die DSGVO für die Europäische Union.

Verwaltung:

- Reduzieren des IT-Aufwands für die Verwaltung von Software, die auf Clientcomputern und -geräten ausgeführt wird

  Automatisieren Sie die Installation von Updates für das Windows-Betriebssystem und Microsoft 365 Apps for Enterprise in der gesamten Organisation.

## <a name="mapping-contosos-business-needs-to-microsoft-365-for-enterprise"></a>Zuordnen der geschäftlichen Anforderungen von Contoso zu Microsoft 365 für Unternehmen

Von der IT-Abteilung von Contoso wurde vor der Bereitstellung die folgende Zuordnung von Geschäftsanforderungen zu den Features von Microsoft 365 E5 vorgenommen:


| Kategorie | Geschäftsanforderung | Microsoft 365 für Enterprise-Produkte oder-Features |
|:-------|:-----|:-----|
| Produktivität |  |  |
|  | Vereinfachen der Zusammenarbeit | Microsoft Teams, SharePoint, OneDrive |
|  | Mehr Produktivität für Telearbeiter und Mobilmitarbeiter | Microsoft 365-Arbeitslasten und cloudbasierte Daten |
|  | Mehr Kreativität und Innovation | Windows Ink, Cortana at Work, PowerPoint |
| Sicherheit |  |  |
|  | Identitäts- und Zugriffsverwaltung | Dedizierte globale Administratorkonten mit Azure Multi-Factor Authentication (MFA) und Azure AD Privileged Identity Management (PIM) <BR> Mehrstufige Authentifizierung (MFA) für alle Benutzerkonten <BR> Bedingter Zugriff <BR> Windows Hello <BR> Windows Credential Guard |
|  | Bedrohungsschutz | Advanced Threat Analytics <BR> Windows Defender <BR> Advanced Threat Protection <BR> Office 365 Advanced Threat Protection <BR> Untersuchung und Antwort von Microsoft 365 Threat <BR> |
|  | Schutz von Daten | Azure Information Protection <BR> Verhinderung von Datenverlust (Data Loss Prevention, DLP) <BR> Windows Information Protection (WIP) <BR> Microsoft Cloud App Security <BR> Microsoft Intune |
|  | Sicherheitsverwaltung | Azure Security Center  <BR> Windows Defender Security Center |
| Remote- und Mobilzugriff und Geschäftspartner |  |  |
|  | Mehr Sicherheit für Telearbeiter und Mobilmitarbeiter | Microsoft Intune |
|  | Verkleinern der Remotezugriffsinfrastruktur für Mitarbeiter | Microsoft 365-Arbeitslasten und cloudbasierte Daten |
|  | Bessere Konnektivität und weniger Aufwand für B2B-Transaktionen | Verbundauthentifizierung und cloudbasierte Ressourcen |
| Compliance |  |  |
|  | Einhalten von regionalen gesetzlichen Vorschriften | Dsgvo-Features in Microsoft 365 |
| Verwaltung |  |  |
|  | Reduzieren des IT-Aufwands für die Installation von Clientupdates | Bereitstellungsringe <BR> Windows 10 Enterprise-Updates <BR> Microsoft 365 Apps for Enterprise-Updates |
||||

## <a name="next-step"></a>Nächster Schritt

[Erfahren Sie mehr](contoso-networking.md) über das lokale Netzwerk von Contoso und wie dieses im Hinblick auf Zugriff und Latenz für cloudbasierte Microsoft 365-Ressourcen optimiert wurde.

## <a name="see-also"></a>Siehe auch

[Übersicht über Microsoft 365 Enterprise](microsoft-365-overview.md)

[Testumgebungsanleitungen](m365-enterprise-test-lab-guides.md)
