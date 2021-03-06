---
title: Bereitstellung von Windows 10 Enterprise für Contoso
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
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Informationen dazu, wie Contoso Microsoft Endpoint Configuration Manager zur Bereitstellung von direkten Upgrades für Windows 10 Enterprise verwendete.
ms.openlocfilehash: a100eb07408053fd270c26f388265696549fff9f
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686418"
---
# <a name="windows-10-enterprise-deployment-for-contoso"></a>Bereitstellung von Windows 10 Enterprise für Contoso

Vor dem breiten Rollout von Microsoft 365 for Enterprise hatte Contoso Windows-kompatible PCs und Geräte mit einer Kombination aus Windows 7 (10%), Windows 8.1 (65%) und Windows 10 (25%). Contoso wollte ein Upgrade seiner PCs für Windows 10 Enterprise nutzen Sie die erweiterte Sicherheit und senken Sie den IT-Overhead von automatisierten Bereitstellungen von Updates. 

Nach der Bewertung der Infrastruktur und der Geschäftsanforderungen identifizierte Contoso die folgenden Hauptanforderungen für die Bereitstellung:

- Windows 10 Enterprise soll auf so vielen Computern und Geräten wie möglich ausgeführt werden.
- Die Einführung von direkten Upgrades nutzt die vorhandene Configuration Manager-Infrastruktur.
- Die Steuerung, welche Versionen von Windows 10 Enterprise bereitgestellt und aktualisiert werden sollen, erfolgt über Ringe.
- Computer und Geräte sollen mit minimalen IT-Verwaltungskosten und minimalen Auswirkungen auf die Endbenutzer auf dem aktuellen Stand gehalten werden.

„Auf dem neuesten Stand“ wird definiert als die unterstützte Version von Windows 10 Enterprise, die den Geschäftsanforderungen von Contoso entspricht; dabei muss es nicht unbedingt darum gehen, dass auf allen Windows-kompatiblen Computern die neueste Version von Windows 10 Enterprise ausgeführt wird.

## <a name="deployment-tools"></a>Bereitstellungstools

Vor und während direkter Upgrades von Windows 10 Enterprise verwendete Contoso die folgenden Lösungen von Windows Analytics:

- Upgradebereitschaft  

  Es werden System-, Anwedungs- und Treiberdaten für die Analyse erfasst und dann Kompatibilitätsprobleme identifiziert, durch die ein Upgrade und vorgeschlagene Korrekturen blockiert werden können, die Microsoft bekannt sind.

- Update-Compliance  

  Zeigt den Status Ihrer Geräte in Bezug auf die Windows-Updates an, so dass Sie sicherstellen können, dass diese gegebenenfalls auf den aktuellsten Updates sind.

- Geräteintegrität  

  Identifiziert Geräte, die häufig abstürzen und daher möglicherweise neu aufgebaut oder ersetzt werden müssen, und Gerätetreiber, die Geräteabstürze verursachen, mit Vorschlägen für alternative Versionen dieser Treiber, welche die Anzahl der Abstürze reduzieren könnten. Bietet eine Benachrichtigung über Fehlkonfigurationen des Windows Information Protection, die Eingabeaufforderungen an Endbenutzer senden.
 
Contoso verfügt über eine vorhandene Infrastruktur von Configuration Manager (Current Branch). Configuration Manager kann an große Umgebungen angepasst werden und bietet eine umfassende Kontrolle über Installation, Updates und Einstellungen. Er verfügt außerdem über integrierte Features, um die Bereitstellung und Verwaltung von Windows 10 Enterprise zu vereinfachen und effizienter zu gestalten.

## <a name="planning-process"></a>Planungsprozess

Vor der Bereitstellung hat Contoso die folgenden Ringe definiert:

- Drei Ringe für die Überprüfung und das Staging der Bereitstellung 
  - Ein Ring für Vorschau-Builds 
  - Ein Ring für die Builds von neuen Versionen
  - Ein Ring für einen früheren Build 
- Ein Ring für die allgemeine Bereitstellung von Windows 10 Enterprise basierend auf Daten aus den Überprüfungsringen

Contoso hat auch die Lösung für die Upgradebereitschaft von Windows Analytics verwendet, um installierte Apps und deren Kompatibilität mit Windows 10 Enterprise zu bestimmen.

## <a name="deployment-process"></a>Bereitstellungsprozess

Um die Bereitstellung des direkten Upgrades von Windows 10 Enterprise abzuschließen, hat Contoso den folgenden Prozess implementiert, der Empfehlungen zu bewährten Vorgehensweisen von Microsoft umfasst:

1. Der Peercache für Configuration Manager wurde aktiviert.
2. Es wurden angepasste Windows-Pakete basierend auf Images aus dem Volume Licensing Service Center erstellt.
3. Configuration Manager wurde zur Bereitstellung der Windows-Pakete an Verteilungspunkten im Netzwerk verwendet, und es wurden Builds an den drei Ringen für Überprüfung und Staging der Bereitstellung bereitgestellt.
4. Mithilfe der Lösungen für Geräteintegrität und Updatebereitschaft von Windows Analytics wurden der Erfolg von Computern und Geräten in den drei Ringen für Überprüfung und Staging der Bereitstellung bewertet.
5. Contoso ermittelte (basierend auf den Windows Analytics-Informationen) die Version von Windows 10 Enterprise, die im Ring der Bereitstellung auf breiter Basis bereitgestellt werden soll.
6. Es wurden die Bereitstellungsaufgabenfolgen von Configuration Manager ausgeführt, um das ausgewählte Windows-Paket im Ring der Bereitstellung auf breiter Basis bereitzustellen.
7. Die Computer und Geräte im Ring der Bereitstellung auf breiter Basis wurden mithilfe der Lösungen für Geräteintegrität und Updatebereitschaft überwacht, die zur Behebung von Problemen bereitgestellt werden.

Hier ist Contosos Bereitstellungsarchitektur für das direkte Upgrade und fortlaufende Updates.

![Contosos Bereitstellungsinfrastruktur für Windows 10 Enterprise](../media/contoso-win10/contoso-win10-fig1.png)

Diese Infrastruktur besteht aus:

- Configuration Manager, der:
  - Images für Windows 10 Enterprise-Pakete aus dem Microsoft Volume Licensing Center im Microsoft Network abruft.
  - Als zentraler Verwaltungspunkt für Bereitstellungspakete fungiert.
- Regionale Verteilungspunkte befinden sich in der Regel in den regionalen Hub-Büros von Contoso.
- Windows-PCs und Geräte an verschiedenen Standorten, die die Bereitstellungspakete für das direkte Upgrade oder für laufende Updates basierend auf der Ringmitgliedschaft empfangen und installieren.

## <a name="next-step"></a>Nächster Schritt

[Erfahren Sie](contoso-o365pp.md), wie Contoso seine Configuration Manager-Infrastruktur verwendet, um das aktuelle Microsoft 365 Apps for Enterprise im gesamten Unternehmen bereitzustellen. 

## <a name="see-also"></a>Siehe auch

[Windows 10 Enterprise](https://docs.microsoft.com/windows/deployment/)

[Übersicht über Microsoft 365 Enterprise](microsoft-365-overview.md)

[Testumgebungsanleitungen](m365-enterprise-test-lab-guides.md)
