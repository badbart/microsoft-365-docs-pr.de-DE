---
title: Überprüfen von Nachweisdaten
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Hier finden Sie Informationen zu Methoden zum Überprüfen der Daten in ihren beweisen, beispielsweise zum Anzeigen in systemeigenen, Text-oder near-nativen Formaten.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 9335b95cc57add69660b707577829caef1ad8183
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285381"
---
# <a name="review-the-data-in-evidence"></a>Überprüfen von Nachweisdaten

Die Daten in einem in einer Daten Untersuchung festgelegten Beweis sind eine Momentaufnahme der Suchergebnisse, die Sie gesammelt und dem Beweissatz hinzugefügt haben. Wenn Sie Suchergebnisse zu beweisen hinzufügen, wird ein Prozess ausgelöst, um Dateien, Metadaten und Text aus den Elementen zu extrahieren, die von der Suche zurückgegeben werden. Anschließend erstellt das Tool Daten Untersuchungen (Vorschau) einen neuen Index (durch einen Prozess mit dem Namen *Advanced Indexing*) aller Daten und fügt einen auf der Registerkarte **Beweise** festgelegten Beweis hinzu. 

Bei zeitkritischen Untersuchungen können Sie dadurch die Umgebung schnell enthalten, indem Sie die tatsächlichen verschütteten oder bösartigen Daten löschen, die sich in der at-ursprünglichen Datenquelle befinden, und gleichzeitig das erneute Erstellen von Beweisen in einer isolierten Umgebung, in diesem Fall die Daten, die in den Beweissatz kopiert werden, untersuchen. Nachdem die Beweise gesammelt und dem Beweissatz hinzugefügt wurden, können Sie einzelne Dokumente in ihrem systemeigenen Format, im Text Format oder in einem fast systemeigenen Format überprüfen, das Sie zum Beschriften und redact von Dokumenten verwenden können. Darüber hinaus können Sie Abfragen ausführen, um die festgelegten Daten nach Zeitbereich, Dateitypen, Datenbesitzern und vielen anderen Eigenschaften und Suchbedingungen einzuschränken. Beispielsweise können Sie mithilfe der Autoren-, Absender-oder Empfängerbedingungen schnell erkennen, welche Personen an dem Vorfall beteiligt sind und ob Daten aus Ihrer Organisation für externe Benutzer freigegeben wurden. Weitere Informationen zum Durchsuchen von Daten in einem Beweis Sätze finden Sie unter [Abfragen der Daten in Evidence](evidence-query.md).

Um Dokumente zu gruppieren und weitere Unterstützung für Ihre Überprüfung zu erhalten, wählen Sie auf der Registerkarte **Beweise** einen Beweissatz aus, und klicken Sie dann auf **Beweise verwalten**. Klicken Sie in der **Analyse** Kachel auf **Analyse für die gesamte Gruppe neu erstellen**. Dadurch werden erweiterte Analysen wie doppelte Erkennung, e-Mail-Threading und Design Analyse ausgeführt. Anschließend können Sie die allgemeinen Themen der Daten anzeigen und auch Dokumente per e-Mail-Threads, in der Nähe von Duplikaten und genaue Duplikate organisieren, um Ihre Untersuchung zu unterstützen. Weitere Informationen finden Sie unter [Ausführen von Analysen, um schneller zu untersuchen](run-analytics-to-investigate-faster.md).

## <a name="view-documents-in-evidence"></a>Anzeigen von Dokumenten in Evidence

Mit dem Tool zur Datenermittlung (Vorschau) können Sie Inhalte in mehreren unterschiedlichen Viewern anzeigen, wobei jeder Betrachter einen anderen Zweck hat. Diese Viewer sind:

- Dateimetadaten
- Systemeigene Ansicht
- Textansicht
- Kommentaransicht

Um auf einen dieser Viewer zuzugreifen, wählen Sie einfach ein Dokument in einem Beweissatzes aus.

## <a name="file-metadata"></a>Dateimetadaten

In dieser Ansicht werden verschiedene Metadaten-Eigenschaften angezeigt, die mit dem ausgewählten Dokument verknüpft sind. Sie können diese Ansicht aktivieren und deaktivieren, indem Sie auf **Datei Metadaten**klicken. Wenn Sie ein Dokument überprüfen, können Sie die Datei Metadaten anzeigen und sich immer noch zwischen den verschiedenen Viewern ändern.

Im folgenden finden Sie ein Beispiel für die Datei Metadaten für ein Dokument. Weitere Informationen zu den Metadaten-Feldern finden Sie unter [Document Metadata fields in Data Investigations (Preview)](document-metadata-fields.md).

![Datei Metadaten-Bereich](../media/Reviewimage2.png)

## <a name="native-view"></a>Systemeigene Ansicht

Der systemeigene Viewer zeigt die genaueste Ansicht eines Dokuments in seinem systemeigenen Format an. Native View wird für Hunderte von Dateitypen unterstützt und ist für die Anzeige von Dokumenten in der wahrsten nativen Umgebung möglich. Für Microsoft Office Dateien verwendet der systemeigene Viewer die Webversion von Office-Apps. Auf diese Weise können Sie Inhalte wie Kommentare in verschiedenen Office-Dokumenten, Formeln und ausgeblendeten Zeilen/Spalten in Excel und die Notizenansicht in PowerPoint anzeigen.

![Systemeigene Ansicht
](../media/Reviewimage3.png)

## <a name="text-view"></a>Textansicht

Der Text-Viewer bietet eine Ansicht des extrahierten Texts einer Datei. Eingebettete Bilder und Formatierungen werden ignoriert, diese Ansicht ist jedoch hilfreich, wenn Sie versuchen, den Inhalt eines Dokuments schnell zu überprüfen und zu verstehen. Die Textansicht bietet außerdem die folgenden Features:

  - Ein Leistungsindikator, der das verweisen auf bestimmte Teile eines Dokuments erleichtert.

  - Hervorheben von Suchtreffern, die Begriffe im Dokument sowie auf der Bildlaufleiste hervorheben

  - Eine diff-Ansicht bietet eine Vergleichsansicht, in der die Textunterschiede beim Anzeigen von Dokumenten mithilfe des Bereichs **nahe Duplikate** hervorgehoben werden.

**Beispiel für einen Leistungsindikator und eine Hervorhebung von Suchtreffern in Text und ScrollBar**

![Textansicht
](../media/Reviewimage4.png)

**Beispiel für die diff-Ansicht**

![Vergleichsansicht
](../media/Reviewimage5.png)

## <a name="annotate-view"></a>Kommentaransicht

Die Ansicht Anmerkungen enthält Features, mit denen Sie während des Überprüfungsprozesses Markup für ein Dokument anwenden können. Dazu gehören die folgenden Tools:

  - **Area-Aktionen** – Sie können ein deckendes Feld im Dokument zeichnen, in dem vertrauliche Inhalte ausgeblendet werden.

  - **Bleistift** – Sie können frei Handzeichen für ein Dokument freigeben, um die Aufmerksamkeit auf bestimmte Teile des Inhalts zu lenken.

  - **Anmerkungen auswählen** – Sie können Anmerkungen in einem Dokument auswählen und löschen.

  - **Anmerkungs Transparenz umschalten** – Sie können die Transparenz von Anmerkungen umschalten (zwischen opak und halbtransparent), damit Sie den Inhalt hinter der Anmerkung anzeigen können. Dies umfasst das Umschalten der Transparenz von Bleistift Anmerkungen und-Aktionen.

Die anmerkungsansicht bietet auch die folgende Navigationsfunktionalität:

  - **Vorherige Seite**, **Nächste Seite**, und **Navigieren Sie zu Seiten** Navigationssteuerelementen, die für mehrseitige Dokumente verwendet werden sollen.

  - **Zoom** – erhöht oder verkleinert die Größe von Dokumenten in der Ansicht Anmerkungen.

  - **Drehen** – Dokumente im Uhrzeigersinn drehen.

  - **Suche** – suchen Sie nach Stichwörtern in einem Dokument, und verwenden Sie dann die vorherigen und nächsten Steuerelemente, um die Treffer (die hervorgehoben werden) im Dokument anzuzeigen.

**Beispiel für die Ansicht "anmerken"**

![Kommentaransicht](../media/Reviewimage1.png)

> [!NOTE]
> Anmerkungen werden auf eine Kopie des Dokuments angewendet, die dem Beweissatz hinzugefügt wurde. Die ursprünglichen Dokumente im Live-Dienst werden nicht kommentiert.
