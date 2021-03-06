---
title: Konfigurieren von Such-und Analyse Einstellungen-Daten Untersuchungen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: In diesem Artikel erfahren Sie, wie Sie Such-und Analyse Einstellungen wie etwa Duplikate, e-Mail-Threading und Designs beim Verwalten von Daten Untersuchungen konfigurieren.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: ebc04e68c4d8854c91ceae75b164cc061e77aad4
ms.sourcegitcommit: 1423e08a02d30f0a2b993fb99325c3f499c31787
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "48277073"
---
# <a name="configure-search-and-analytics-settings-in-data-investigations"></a>Konfigurieren von Such-und Analyse Einstellungen in Daten Untersuchungen

## <a name="near-duplicates-and-email-threading"></a>Erkennung von Quasiduplikaten und E-Mail-Threading

In diesem Abschnitt können Sie Parameter für die doppelte Erkennung, in der Nähe der doppelten Erkennung und beim e-Mail-Threading festlegen.

- Aktivieren/deaktivieren: doppelte Erkennung, nahezu doppelte Erkennung und e-Mail-Threading als Teil des Analyse Flusses einschließen, falls aktiviert. Da Sie sich übereinander aufbauen, müssen Sie alle aktivieren oder deaktivieren.

- Schwellenwert: Wenn sich die Ähnlichkeits Ebene von zwei Dokumenten über dem Schwellenwert befindet, werden Sie in derselben nahe doppelten Gruppe platziert.

- Duplikate standardmäßig ausblenden: Wenn diese Einstellung aktiviert ist, wird standardmäßig ein Filter zum Ausblenden von doppelten Dokumenten im Arbeitsmappen-Objekt angewendet. Der Filter kann bei Bedarf manuell im Arbeitsmappe entfernt werden.

- Minimale/maximale Anzahl von Wörtern: nahe Duplikate und e-Mail-Threading werden nur für Dokumente ausgeführt, die mindestens die minimale Anzahl von Wörtern und höchstens die maximale Anzahl von Wörtern aufweisen.

Weitere Informationen finden Sie [in der Nähe der doppelten Erkennung](near-duplicates.md) und des [e-Mail-Threadings](email-threading.md).

## <a name="themes"></a>Designs

In diesem Abschnitt können Sie Parameter für Designs festlegen.

- Aktivieren/deaktivieren: einbeziehen von Designs beim Clustering als Teil des Analyse Flusses, falls aktiviert.

- Anpassen der maximalen Anzahl von Designs dynamisch: in bestimmten Fällen gibt es nicht genügend Dokumente, um die gewünschte Anzahl von Designs zu erstellen. Wenn diese Einstellung aktiviert ist, wird nicht versucht, die gewünschte maximale Anzahl von Designs zu erzwingen, sondern das System passt die maximale Anzahl von Designs dynamisch an.

- Maximale Anzahl von Designs: gewünschte Anzahl von Designs.

- Zahlen in Designs einbeziehen: Wenn diese Option aktiviert ist, werden beim Generieren von Designs Zahlen in enthalten.  

## <a name="optical-character-recognition-ocr"></a>Optical Character Recognition (OCR; optische Zeichenerkennung)

Wenn diese Einstellung aktiviert ist, wird die OCR für Bilder ausgeführt, die in Arbeitsmappen aufgenommen werden, sodass Sie durchsuchbar sein können.

## <a name="ignore-text"></a>Ignorieren von Text

Es gibt Fälle, in denen bestimmte Texte die Qualität von Analysen vermindern, wie lange Haftungsausschlüsse, die zu bestimmten e-Mails hinzugefügt werden, unabhängig vom Inhalt der e-Mail. Wenn Sie solche Fälle kennen, können Sie diesen Text aus Analysen ausschließen, indem Sie den Text angeben (Regex wird unterstützt) und welche Module für den Text ausgeschlossen werden sollen.
