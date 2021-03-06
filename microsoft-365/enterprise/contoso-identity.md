---
title: Identität für die Contoso Corporation
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
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Wie Contoso IDaaS (Identity as a Service) nutzt und eine cloudbasierte Authentifizierung für seine Mitarbeiter und eine Verbundauthentifizierung für Partner und Kunden bereitstellt.
ms.openlocfilehash: 795fb7dcb886c792c80d3bb251c9cb5774f1bf97
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686034"
---
# <a name="identity-for-the-contoso-corporation"></a>Identität für die Contoso Corporation

Microsoft bietet eine IDaaS (Identity as a Service, Identität als Dienst) in seinen Cloudangeboten mit Azure Active Directory (Azure AD). Um Microsoft 365 für Unternehmen zu verabschieden, musste die IDaaS-Lösung von Contoso Ihren lokalen Identitätsanbieter nutzen und weiterhin die Verbundauthentifizierung mit Ihren vorhandenen vertrauenswürdigen Drittanbieter-Identitätsanbietern einschließen.

## <a name="contosos-active-directory-domain-services-forest"></a>Active Directory Domain Services-Gesamtstruktur von Contoso

Contoso verwendet eine einzelne Active Directory Domain Services(AD DS)-Gesamtstruktur für „contoso.com“ mit sieben Unterdomänen, eine für jede Region der Welt. Die Zentrale, die Regionalstellen und die Zweigstellen enthalten Domänencontroller für die lokale Authentifizierung und Autorisierung.

Hier sehen Sie die Contoso-Gesamtstruktur mit regionalen Domänen für die unterschiedlichen Regionen, die regionale Hubs enthalten.

![Gesamtstruktur und Domänen von Contoso weltweit](../media/contoso-identity/contoso-identity-fig1.png)
 
Contoso wollte die Konten und Gruppen in der „contoso.com“-Gesamtstruktur zur Authentifizierung und Autorisierung seiner Microsoft 365-Arbeitslasten und -Dienste verwenden.

## <a name="contosos-federated-authentication-infrastructure"></a>Contosos Infrastruktur der Verbundauthentifizierung

Contoso lässt Folgendes zu:

- Kunden können ihre Microsoft-, Facebook- oder Google Mail-Konten verwenden, um sich bei ihren öffentlichen Websites anzumelden.
- Lieferanten und Partner können ihre LinkedIn-, Salesforce- oder Google Mail-Konten verwenden, um sich beim Partnerextranet anzumelden.

Hier sehen Sie die Contoso-DMZ mit einer öffentlichen Website, einem Partnerextranet und einer Reihe von Active Directory-Verbunddienste-Servern (AD FS). Die DMZ ist mit dem Internet verbunden, das Kunden, Partner und Internetdienste enthält.

![Unterstützung von Contoso für die Verbundauthentifizierung für Kunden und Partner](../media/contoso-identity/contoso-identity-fig2.png)
 
AD FS-Server in der DMZ erleichtern das Authentifizieren von Kundenanmeldeinformationen durch den Identitätsanbieter für Zugriff auf die öffentliche Website und Partneranmeldeinformationen für Zugriff auf das Partnerextranet.

Contoso hat sich entschlossen, seine Infrastruktur beizubehalten und diese für die Kunden- und Partnerauthentifizierung zu verwenden. Die Identitätsarchitekten bei Contoso befassen sich mit der Konvertierung dieser Infrastruktur in die Azure AD-Lösungen [B2B](https://docs.microsoft.com/azure/active-directory/b2b/hybrid-organizations) und [B2C](https://docs.microsoft.com/azure/active-directory-b2c/solution-articles).

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>Hybrididentität mit Kennwort-Hash-Synchronisierung für cloudbasierte Authentifizierung

Contoso wollte seine lokale AD DS-Gesamtstruktur für die Authentifizierung bei Microsoft 365-Cloudressourcen nutzen. Es entschied sich für Kennwort-Hash-Synchronisierung.

PHS synchronisiert die lokale AD DS Gesamtstruktur mit dem Azure AD Mandanten Ihres Microsoft 365 for Enterprise-Abonnements und kopiert Benutzer-und Gruppenkonten sowie eine gehashte Version der Kennwörter für Benutzerkonten. 

Um die laufende Verzeichnissynchronisierung durchzuführen, hat Contoso das Azure AD Connect-Tool auf einem Server im Rechenzentrum in Paris bereitgestellt. 

Hier sehen Sie den Server mit Azure AD Connect, das die AD DS-Gesamtstruktur von Contoso auf Änderungen abruft und diese Änderungen dann mit dem Azure AD-Mandanten synchronisiert.

![Infrastruktur für die PHS-Verzeichnissynchronisierung von Contoso](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-identity-and-device-access"></a>Richtlinien für bedingten Zugriff für Identitäts- und Gerätezugriff

Contoso hat eine Gruppe von Azure AD- und Intune-[Richtlinien für bedingten Zugriff](identity-access-policies.md) für drei Schutzebenen erstellt:

- **Baseline**-Schutz gilt für alle Benutzerkonten
- **Vertraulicher** Schutz gilt für die Geschäftsleitung und Führungskräfte
- **Hochgradig regulierter** Schutz gilt für bestimmte Benutzer der Finanz-, Rechts- und Forschungsabteilung, die Zugriff auf hochgradig regulierte Daten haben.

Hier sehen Sie die resultierenden identitäts- und gerätebasierten Richtlinien für bedingten Zugriff von Contoso.

![Identitäts- und gerätebasierte Richtlinien für bedingten Zugriff](../media/contoso-identity/contoso-identity-fig5.png)
 
## <a name="next-step"></a>Nächster Schritt

[Erfahren Sie](contoso-win10.md), wie Contoso seine Microsoft Endpoint Configuration Manager-Infrastruktur verwendet, um das aktuelle Windows 10 Enterprise im gesamten Unternehmen bereitzustellen.

## <a name="see-also"></a>Siehe auch

[Identity Roadmap für Microsoft 365](identity-roadmap-microsoft-365.md)

[Übersicht über Microsoft 365 Enterprise](microsoft-365-overview.md)

[Testumgebungsanleitungen](m365-enterprise-test-lab-guides.md)
