---
title: Netzwerkfunktionen für die Contoso Corporation
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
description: Grundlegendes zur Contoso-Netzwerkinfrastruktur und zur Verwendung der SD-WAN-Technologie für eine optimale Netzwerkleistung für Microsoft 365 für Enterprise-Cloud-Dienste.
ms.openlocfilehash: bc2ae68917258b94ed46ef0c1257f56e0736105c
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46685818"
---
# <a name="networking-for-the-contoso-corporation"></a>Netzwerkfunktionen für die Contoso Corporation

Zur Einführung einer cloudeinschließenden Infrastruktur erkannten die Netzwerktechniker bei Contoso die grundlegende Änderung in der Art und Weise, wie Netzwerkdatenverkehr zu Clouddiensten fließt. Anstelle eines internen Hub-and-Spoke-Modells, das sich auf die Netzwerkkonnektivität und -datenverkehr für die nächste Ebene der Contoso-Bürohierarchie konzentriert, wurden Benutzerstandorte lokalen Internetausgängen und lokale Verbindungen den nächstgelegenen Microsoft 365-Netzwerkspeicherorten im Internet zugeordnet.

## <a name="contosos-networking-infrastructure"></a>Contosos Netzwerkinfrastruktur

Die Büros von Contoso werden über die folgenden Elemente des Contoso-Netzwerks miteinander verbunden:

- MPLS-WAN-Netzwerk (Multiprotocol Label Switching)

  Ein MPLS-WAN-Netzwerk verbindet die Zentrale in Paris mit regionalen Niederlassungen und regionale Niederlassungen mit Zweigstellen in einer Hub-and-Spoke-Konfiguration. Auf diese Weise können Benutzer auf lokale Server zugreifen, aus denen Branchen-Apps im Pariser Büro bestehen. Außerdem wird der allgemeine Internetdatenverkehr an das Pariser Büro weitergeleitet, wenn Netzwerksicherheitsgeräte die Anforderungen bereinigen. In jedem Büro senden Router Datenverkehr an kabelgebundene Hosts oder Funkzugriffspunkte in Subnetzen, für die der private IP-Adressraum verwendet wird.

- Lokaler direkter Internetzugriff für Microsoft 365-Datenverkehr

  Jede Niederlassung verfügt über ein Software-Defined-WAN (SD-WAN)-Gerät mit einem oder mehreren ISP-Netzwerkschaltern mit eigener Internetverbindung über einen Proxyserver. Dies wird in der Regel als eine WAN-Verbindung zu einem lokalen ISP implementiert, der auch öffentliche IP-Adressen und einen lokalen DNS-Server bereitstellt.

- Internetauftritt

  Contoso ist im Besitz des öffentlichen Domänennamens „contoso.com“. Die öffentliche Contoso-Website zum Bestellen von Produkten besteht aus einer Gruppe von Servern in einem mit dem Internet verbundenen Rechenzentrum auf dem Pariser Campus. Contoso verwendet einen öffentlichen /24-IP-Adressbereich im Internet.

Abbildung 1 zeigt die Contoso-Netzwerkinfrastruktur und die dazugehörigen Verbindungen mit dem Internet.

![Contoso-Netzwerk](../media/contoso-networking/contoso-networking-fig1.png)
 
**Abbildung 1: Contoso-Netzwerk**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Verwenden des SD-WAN für eine optimale Netzwerkkonnektivität mit Microsoft

Contoso folgte den folgenden [Prinzipien von Microsoft 365-Netzwerkverbindungen](microsoft-365-network-connectivity-principles.md) bei folgende Aufgaben:

1. Identifizieren und Unterscheiden von Microsoft 365-Netzwerkdatenverkehr
2. Lokaler Ausgang von Netzwerkverbindungen
3. Vermeiden von Spitzkehren für Netzwerke
4. Umgehen von doppelten Netzwerksicherheitsgeräten

Es gibt drei Kategorien von Netzwerkdatenverkehr für Microsoft 365: „Optimize“, „Allow“ und „Default“. Bei "Optimize" und "Allow" handelt es sich um vertrauenswürdigen Netzwerkdatenverkehr, der verschlüsselt und an den Endpunkten geschützt und an das Microsoft 365-Netzwerk gerichtet ist.

Contoso hat Folgendes beschlossen:

- Der direkte Internetausgang für Datenverkehr der Kategorie "Optimize" und "Allow" wird verwendet und der gesamte Datenverkehr der Kategorie "Default" wird an die zentrale Internetverbindung in Paris weitergeleitet.

- An jedem Standort wurden SD-WAN-Geräte bereitgestellt, damit diese Prinzipien problemlos umgesetzt werden konnten und eine optimale Netzwerkleistung für cloudbasierte Microsoft 365-Dienste erzielt werden kann.

  Die SD-WAN-Geräte weisen einen LAN-Port für das lokale Netzwerk und mehrere WAN-Ports auf. Ein WAN-Port stellt eine Verbindung mit dem MPLS-Netzwerk her, und ein weiterer WAN-Port stellt eine Verbindung mit einem lokalen ISP-Schaltkreis her. Die SD-WAN-Geräte leiten Netzwerkdatenverkehr der Kategorie "Optimize" und "Allow" über die ISP-Verbindung.

## <a name="contosos-line-of-business-app-infrastructure"></a>Contosos Infrastruktur für Branchen-Apps

Contoso hat seine Intranetinfrastruktur für Branchen-Apps und Server für Folgendes konzipiert:

- Zweigstellen verwenden lokale Cacheserver, um Dokumente und interne Websites zu speichern, auf die häufig zugegriffen wird.
- Regionalstellen verwenden regionale Anwendungsserver für die Regional- und Zweigstellenbüros. Diese Server werden mit den Servern in der Pariser Zentrale synchronisiert.
- Auf dem Pariser Campus befinden sich die Rechenzentren mit den zentralen-Anwendungsservern, die das gesamte Unternehmen bedienen.

Abbildung 2 zeigt den Prozentsatz des Netzwerkdatenverkehrs beim Zugriff auf Server im Intranet von Contoso.

![Contosos Infrastruktur für die interne Anwendung](../media/contoso-networking/contoso-networking-fig2.png)
 
**Abbildung 2: Contoso-Infrastruktur für die interne Anwendung**

Für Benutzer in Zweigstellen- oder Regionalbüros können 60 % der von ihnen benötigten Ressourcen von den Zweigstellen- oder Regionalbüroservern bereitgestellt werden.
 Die weiteren 40 % der Ressourcenanforderungen werden über die WAN-Verbindung mit dem Pariser Campus abgedeckt.

## <a name="contosos-network-analysis-and-preparation-of-their-network-for-microsoft-365-for-enterprise"></a>Contosos Netzwerkanalyse und Vorbereitung Ihres Netzwerks für Microsoft 365 for Enterprise

Die erfolgreiche Einführung von Microsoft 365 für Enterprise-Dienste durch die Benutzer von Contoso hängt von der hochgradig verfügbaren und leistungsfähigen Konnektivität mit dem Internet oder direkt mit Microsoft Cloud Services ab. Contoso hat die folgenden Schritte ausgeführt, um eine optimierte Konnektivität mit Microsoft 365 für Enterprise-Cloud-Dienste zu planen und zu implementieren:

1. Es wurde ein WAN-Netzwerkdiagramm für das Unternehmen zur Unterstützung der Planung erstellt.

   Contoso startete die Netzwerkplanung durch Erstellung eines Diagramms, in dem die Standorte, die vorhandene Netzwerkverbindung, die vorhandenen Netzwerkumkreisgeräte sowie die Dienstklassen dargestellt wurden, die im Netzwerk verwaltet werden. Dieses Diagramm wurde für alle nachfolgenden Schritte bei der Planung und Implementierung der Netzwerkkonnektivität verwendet.

2. Plan für Microsoft 365 für Enterprise-Netzwerkkonnektivität erstellt

   Contoso verwendete die [Prinzipien von Microsoft 365-Netzwerkverbindungen](microsoft-365-network-connectivity-principles.md) und stellte Referenznetzwerkarchitekturen bereit, um SD-WAN als bevorzugte Topologie für Microsoft 365-Konnektivität zu bestimmen.

3. In jeder Niederlassung wurde die Auslastung der Internetverbindung und die MPLS-WAN-Bandbreite analysiert und bei Bedarf erhöht.

   In jeder Niederlassung wurde die aktuelle Nutzung analysiert, und Schaltungen wurden so erhöht, dass der vorhergesagte cloudbasierte Microsoft 365-Datenverkehr mit durchschnittlich 20 % nicht genutzter Kapazität ausgeführt wurde.

4. Optimierte Leistung für Microsoft-Netzwerkdienste

   Contoso bestimmte die Gruppe von Office 365-, Intune- und Azure-Endpunkten, konfigurierte Firewalls, Sicherheitsgeräte und andere Systeme im Internetpfad für optimale Leistung. Endpunkte für Office 365-Datenverkehr der Kategorie "Optimize" und "Allow" wurden in den SD-WAN-Geräten für das Routing über den ISP-Schaltkreis konfiguriert.

5. Es wurde ein internes DNS konfiguriert.

   Das DNS muss betriebsbereit sein und für Microsoft 365-Datenverkehr lokal nachgeschlagen werden.

6. Netzwerkendpunkt und Portkonnektivität wurden überprüft.

   Contoso hat die von Microsoft bereitgestellten Tools zur Netzwerkkonnektivität getestet, um die Konnektivität für Microsoft 365 for Enterprise Cloud Services zu überprüfen.

7. Die Netzwerkverbindungen der Computer der Mitarbeiter wurden optimiert.

   Einzelne Computer wurden überprüft, um sicherzustellen, dass die neuesten Betriebssystemupdates installiert wurden und dass die Endpunkt-Sicherheitsüberwachung auf allen Clients aktiv ist.

## <a name="next-step"></a>Nächster Schritt

[Erfahren Sie](contoso-identity.md), wie Contoso seine lokalen Active Directory Domain Services (AD DS) in der Cloud für Mitarbeiter und Verbundauthentifizierung für Kunden und Geschäftspartner nutzt.

## <a name="see-also"></a>Siehe auch

[Roadmap für Netzwerke für Microsoft 365](networking-roadmap-microsoft-365.md)

[Übersicht über Microsoft 365 Enterprise](microsoft-365-overview.md)

[Testumgebungsanleitungen](m365-enterprise-test-lab-guides.md)
