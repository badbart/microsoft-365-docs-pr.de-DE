---
title: Microsoft Compliance Manager und die dsgvo
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Der Microsoft Compliance-Manager ist ein kostenloses Workflow basiertes Risiko Bewertungstool im Microsoft-Dienst Vertrauensstellungs Portal. Mit dem Compliance-Manager können Sie behördliche Compliance-Aktivitäten im Zusammenhang mit Microsoft Cloud Services nachverfolgen, zuweisen und überprüfen.
ms.openlocfilehash: 69e6551620fb654cb09d46554e6e3c98b6a2fc60
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "41595802"
---
# <a name="microsoft-compliance-manager-and-the-gdpr"></a>Microsoft Compliance Manager und die dsgvo

Die allgemeine Datenschutzverordnung (dsgvo), die von der Europäischen Union erlassen wird, kann sich auf Ihre Compliance-Strategie auswirken und spezifische Aktionen zum Verwalten von Benutzer-und Kundeninformationen im Compliance-Manager durchführen.

## <a name="user-privacy-settings"></a>Datenschutzeinstellungen

Für bestimmte Richtlinien ist es erforderlich, dass eine Organisation Benutzer Verlaufsdaten löschen kann. Compliance-Manager bietet Funktionen für **Benutzerdaten Schutzeinstellungen** , die Administratoren Folgendes ermöglichen:
  
- [Suchen eines Benutzers](#search-for-a-user)
- [Exportieren eines Berichts mit Kontoverlaufsdaten](#export-a-report-of-account-data-history)
- [Löschen der Verlaufsdaten von Benutzern](#delete-user-data-history)
  
## <a name="search-for-a-user"></a>Suchen eines Benutzers

So suchen Sie nach einem Benutzerkonto
  
1. Geben Sie den Benutzer-e-Mail-Alias (die Informationen links neben dem @-Symbol) ein, und wählen Sie den Domänennamen aus der Liste Domänensuffix auf der rechten Seite aus. Für Organisationen mit mehreren registrierten Domänen überprüfen Sie das Domänennamensuffix doppelt, um sicherzustellen, dass es richtig ist.

2. Wenn Sie den Benutzernamen richtig eingegeben haben, wählen Sie **Suchen**aus.

3. Für Benutzerkonten, die nicht zurückgegeben werden, wird die Seite **Benutzer nicht gefunden**angezeigt. Überprüfen Sie die e-Mail-Adressinformationen des Benutzers, und nehmen Sie bei Bedarf Korrekturen vor. Zum Wiederholen wählen Sie **Suchen**aus.

4. Für Benutzerkonten, die zurückgegeben werden, ändert sich der Text der Schaltfläche von **Suche** zu **Löschen**. Dies deutet darauf hin, dass das zurückgegebene Benutzerkonto der Betriebs Kontext für die zusätzlichen Funktionen ist und dass diese Funktionen für dieses Benutzerkonto gelten.

5. Um Suchergebnisse zu löschen und nach einem anderen Benutzer zu suchen, wählen Sie **Löschen**aus.

## <a name="export-a-report-of-account-data-history"></a>Exportieren eines Berichts mit Kontoverlaufsdaten

Sie können für jedes identifizierte Benutzerkonto einen Bericht über Abhängigkeiten generieren, die mit dem Konto verknüpft sind. Mit diesen Informationen können Sie offene Aktionselemente neu zuweisen oder den Zugriff auf zuvor hochgeladene Beweise sicherstellen.
  
 So generieren und exportieren Sie einen Bericht:
  
1. Wählen Sie **exportieren** aus, um einen Bericht der Compliance-Manager-Steuerelement Aktionselemente zu generieren und herunterzuladen, die dem zurückgegebenen Benutzerkonto derzeit zugewiesen sind, und die Liste der Dokumente, die von diesem Benutzer hochgeladen wurden. Wenn keine Aktionen oder hochgeladenen Dokumente zugeordnet sind, wird in einer Fehlermeldung "keine Daten für diesen Benutzer" angezeigt.

2. Der Bericht lädt im Hintergrund des aktiven Browserfensters herunter – wenn kein Popup zum Herunterladen angezeigt wird, in dem Sie den Downloadverlauf Ihres Browsers überprüfen möchten.

3. Öffnen Sie das Dokument, um die Daten des Berichts zu überprüfen.

> [!IMPORTANT]
> Bei den Berichtsdaten handelt es sich nicht um eine Verlaufsliste, in der Statusänderungen an Aktionselement-Zuordnungs Verlauf gespeichert und angezeigt werden. Der generierte Bericht ist eine Momentaufnahme der Steuerungs Aktionselemente, die zum Zeitpunkt der Ausführung des Berichts zugewiesen wurden (Datum und Zeitstempel in den Bericht). Beispielsweise ergeben alle nachfolgenden Neuzuweisungen von Aktionselementen unterschiedliche Snapshot-Berichtsdaten, wenn der Bericht für denselben Benutzer erneut generiert wird.
  
## <a name="delete-user-data-history"></a>Löschen der Verlaufsdaten von Benutzern

Legt alle dem zurückgegebenen Benutzer zugewiesenen Steuerungs Aktionselemente auf "nicht zugewiesen" fest. Legt den Wert für **hochgeladene** nach Werte für alle Dokumente fest, die vom zurückgegebenen Benutzer auf "Benutzer entfernt" hochgeladen wurden.
  
So löschen Sie das Benutzerkonto-Aktionselement und den Dokumentupload-Verlauf:
  
1. Wählen Sie **Löschen**aus.

    Es wird ein Bestätigungsdialogfeld angezeigt: "*Hierdurch werden alle Aktionselement Zuweisungen des Steuerelements und der Verlauf des dokumentuploads für den ausgewählten Benutzer entfernt. Diese Aktion ist dauerhaft. Möchten Sie wirklich fortfahren?*"

2. Um fortzufahren, wählen Sie **OK**, andernfalls **Abbrechen**aus.
