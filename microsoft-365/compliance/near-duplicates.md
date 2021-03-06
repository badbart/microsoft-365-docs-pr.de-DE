---
title: Nahe Duplicate Detection-Data Investigation
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
description: Verwenden Sie bei der Verwaltung von Daten Untersuchungen die nahezu doppelte Erkennung, um Text ähnliche Dokumente zu gruppieren, wenn Sie den Nachweis in Daten Untersuchungen (Preview) analysieren.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 37ce968016e674ec83da536c65361d2075cf9bbb
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285951"
---
# <a name="near-duplicate-detection"></a>Erkennen von Quasiduplikaten

Betrachten Sie eine Reihe von Dokumenten, die überprüft werden sollen, in denen eine Teilmenge auf derselben Vorlage basiert und meist die gleiche Standardsprache mit einigen Unterschieden. Wenn ein Prüfer diese Teilmenge identifizieren konnte, überprüfen Sie eine von Ihnen gründlich, und überprüfen Sie die Unterschiede für den Rest, würden Sie keine eindeutigen Informationen verpasst haben, wobei nur ein Bruchteil der Zeit, die Sie zum Lesen aller Dokument Deckung zur Deckung genommen hätte. Bei der Erkennung von Quasiduplikaten werden textuell ähnliche Dokumente gruppiert, um den Überprüfungsvorgang effizienter zu gestalten.

## <a name="how-does-it-work"></a>Wie funktioniert das?

Bei Ausführung der Erkennung von Quasiduplikaten analysiert das System jedes Dokument mit Text. Anschließend werden alle Dokumente miteinander verglichen, um zu bestimmen, ob ihre Ähnlichkeit über dem Schwellenwert liegt. Ist dies der Fall, werden die Dokumente gruppiert. Nachdem alle Dokumente verglichen und gruppiert wurden, wird ein Dokument aus jeder Gruppe als „Pivot“ markiert. Wenn Sie Ihre Dokumente überprüfen, können Sie zuerst das Pivot-Dokument und anschließend die restlichen Dokumente im gleichen Quasiduplikat-Satz überprüfen und sich dabei auf den Unterschied zwischen dem Pivot und dem Dokument konzentrieren, das sich in der Überprüfung befindet.
