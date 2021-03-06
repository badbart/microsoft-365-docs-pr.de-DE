---
title: Grundlegendes zur Relevanz von Assessment in Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
titleSuffix: Office 365
ms.date: 09/14/2017
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 1d33d4fb-91ed-41c0-b72e-5a26eca3a2a7
description: Erhalten Sie einen Überblick über die Bewertungsphase und ihre Rolle bei der Bestimmung des Umfangs von Problemen bei der Relevanz-Schulung in Microsoft 365 Advanced eDiscovery.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: afd4f1f549d52652ac02cfa410efc507ece58910
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818414"
---
# <a name="understand-assessment-in-relevance-in-advanced-ediscovery-classic"></a>Understanding Assessment in Relevanz in Advanced eDiscovery (klassisch)

> [!NOTE]
> Für Advanced eDiscovery ist ein Office 365 E3-Abonnement mit dem Add-On für erweiterte Compliance oder ein E5-Abonnement für Ihre Organisation erforderlich. Wenn Sie nicht über diesen Plan verfügen und Advanced eDiscovery ausprobieren möchten, können Sie sich [für eine Testversion von Office 365 Enterprise E5 anmelden](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
Advanced eDiscovery ermöglicht eine frühzeitige Bewertung, beispielsweise für die definierten Probleme und die für einen Fall importierten Daten. Mit Advanced eDiscovery kann der Experte Entscheidungen über einen angenommenen Ansatz treffen und diese Entscheidungen auf das Dokument Überprüfungs Projekt anwenden.
  
## <a name="understanding-assessment"></a>Grundlegendes zur Bewertung

Bei der Bewertung prüft der Experte eine zufällige Reihe von mindestens 500 Dateien, die verwendet werden, um den Umfang der Probleme zu ermitteln und Statistiken zu erstellen, die die Schulungsergebnisse widerspiegeln. Die Bewertung ist erfolgreich, wenn genügend relevante Dateien gefunden werden, um eine statistische Ebene zu erreichen, die die erweiterte eDiscovery-Relevanz zur Bereitstellung genauer Statistiken und zur effektiven Ermittlung des Stabilisierungs Zeitpunktes im Schulungsprozess unterstützen wird. 
  
Je höher die Anzahl relevanter Dateien im assessmentsatz ist, desto genauer sind die Statistiken und die Effektivität des Stabilitäts Algorithmus. Die Anzahl der relevanten Dateien innerhalb der Bewertungsdateien hängt vom Umfang des Problems ab. "Reichtum" ist der geschätzte Prozentsatz relevanter Dateien im Satz, die für ein Problem relevant sind. Probleme mit höherer Reichweite erreichen eine höhere Anzahl relevanter Dateien schneller als Probleme mit geringerem Reichtum. Bei Problemen mit extrem geringer Reichweite (beispielsweise 2% oder weniger) ist ein sehr umfangreicher Bewertungssatz erforderlich, um eine bedeutende Anzahl relevanter Dateien zu erreichen.
  
Die Statistiken, die während des Trainings und nach der Batch Berechnung auf den Registerkarten Track und entscheiden angezeigt werden, umfassen Schätzungen des Rückrufs für verschiedene Überprüfungs Sätze. In der Statistik enthalten Schätzungen, die auf einem Stich Probenset (in diesem Fall die Bewertungsdateien) basieren, den Fehler Rand und die Zuverlässigkeitsstufe dieses Fehler Rands. Geschätzte Rückrufe von 80% können beispielsweise eine Fehlergrenze von Plus oder minus 5% mit einem Konfidenzniveau von 95% aufweisen. Dies bedeutet, dass der geschätzte Rückruf tatsächlich 75%-85% ist und diese Schätzung 95% Zuversicht hat. Je größer der Bewertungssatz ist, desto geringer ist die Fehlergrenze, und die Statistiken sind genauer. 
  
Nachdem der Experte einen anfänglichen assessmentsatz mit 500 Dateien überprüft hat, kann die Relevanz den aktuellen Fehler Rand der Rückruf Werte bestimmen. Relevanz wird auch empfohlen, einen standardmäßigen Fehlerbereich zu erreichen, um den Bewertungs Satzes zu optimieren. Im Folgenden finden Sie einige Beispiele:
  
- Wenn der Bewertungssatz bereits eine Fehlergrenze von Plus oder minus 10% ergab, wird die Relevanz für die Weiterbildung (keine zusätzliche Bewertungs Überprüfung erforderlich) empfohlen. 
    
- Wenn der Bewertungsgruppe eine Fehlermarge von Plus oder minus 13% ergab, kann die Relevanz die Überprüfung eines weiteren Satzes von Bewertungsdateien empfehlen, um einen kleineren Rand zu erreichen. 
    
- Wenn die Reichweite extrem niedrig ist, empfiehlt es sich möglicherweise, die Bewertung zu beenden, obwohl der Fehler Umfang groß ist (Statistik ist undurchführbar), da der für die Erreichung eines nützlichen Fehler Fehlers erforderliche Bewertungsumfang zu groß ist.
    
Jedes Problem hat seinen eigenen Reichtum, den aktuellen Fehlerbereich und als Ergebnis eine geschätzte Anzahl zusätzlicher Bewertungsdateien. Der nächste assessmentsatz wird entsprechend der maximalen Anzahl von Dateien (bis zu 1.000 in einer einzelnen Gruppe) erstellt.
  
Sie können die Relevanz-Empfehlungen akzeptieren oder den aktuellen Fehler Rand entsprechend Ihren Anforderungen anpassen. Der standardmäßige aktuelle Rand des Fehlers wird für den Rückruf auf gleich oder über 75% bestimmt.
  
> [!NOTE]
> Die Bewertungsphase kann auf der Registerkarte **Relevanz \> Track** in der erweiterten Ansicht für ein Problem umgangen werden, indem das Kontrollkästchen **Bewertung** pro Problem und dann für "alle Probleme" gelöscht wird. Daraus ergibt sich jedoch keine Statistik für dieses Problem. > das Deaktivieren des Kontrollkästchens **Bewertung** kann nur ausgeführt werden, bevor eine Bewertung durchgeführt wird. Wenn in einem Fall mehrere Probleme vorhanden sind, wird die Bewertung nur umgangen, wenn das Kontrollkästchen für jedes Problem deaktiviert ist. 
  
## <a name="related-topics"></a>Verwandte Themen

[Advanced eDiscovery (Classic)](office-365-advanced-ediscovery.md)
  
[Tagging und Bewertung](tagging-and-assessment-in-advanced-ediscovery.md)
  
[Tagging und Relevanz Training](tagging-and-relevance-training-in-advanced-ediscovery.md)
  
[Analyse der nach Verfolgungs Relevanz](track-relevance-analysis-in-advanced-ediscovery.md)
  
[Entscheidung basierend auf den Ergebnissen](decision-based-on-the-results-in-advanced-ediscovery.md)
  
[Testen der Relevanz-Analyse](test-relevance-analysis-in-advanced-ediscovery.md)

