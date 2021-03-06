---
title: Deaktivieren von Berichten beim Exportieren von Inhaltssuchergebnissen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/30/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: c9b0ff0c-282b-4a44-b43f-cfc5b96557f9
ms.custom:
- seo-marvel-apr2020
description: Bearbeiten Sie die Windows-Registrierung auf dem lokalen Computer, um Berichte zu deaktivieren, wenn Sie die Ergebnisse einer Inhaltssuche aus dem Security & Compliance Center exportieren.
ms.openlocfilehash: 0eaf9c9d1f70e03481b00d38d2e487709329c4cd
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2020
ms.locfileid: "44817854"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>Deaktivieren von Berichten beim Exportieren von Inhaltssuchergebnissen

Wenn Sie das eDiscovery-Export Tool verwenden, um die Ergebnisse einer Inhaltssuche im Security & Compliance Center zu exportieren, erstellt und exportiert das Tool automatisch zwei Berichte, die zusätzliche Informationen zu den exportierten Inhalten enthalten. Bei diesen Berichten handelt es sich um die Results.csv Datei und die Manifest.xml Datei (ausführliche Beschreibungen dieser Berichte finden Sie im Abschnitt [häufig gestellte Fragen zum Deaktivieren von Export Berichten](#frequently-asked-questions-about-disabling-export-reports) in diesem Thema). Da diese Dateien sehr umfangreich sein können, können Sie die Downloadzeit beschleunigen und Speicherplatz sparen, indem Sie verhindern, dass diese Dateien exportiert werden. Sie können dies tun, indem Sie die Windows-Registrierung auf dem Computer ändern, den Sie zum Exportieren der Suchergebnisse verwenden. Wenn Sie die Berichte zu einem späteren Zeitpunkt einbeziehen möchten, können Sie die Registrierungseinstellung bearbeiten. 
  
## <a name="create-registry-settings-to-disable-the-export-reports"></a>Erstellen von Registrierungseinstellungen zum Deaktivieren der Export Berichte

Führen Sie das folgende Verfahren auf dem Computer aus, mit dem Sie die Ergebnisse mit einer Inhaltssuche exportieren.
  
1. Schließen Sie das eDiscovery-Export Tool, wenn es geöffnet ist.
    
2. Führen Sie einen oder beide der folgenden Schritte aus, je nachdem, welchen Exportbericht Sie deaktivieren möchten.
    
    - **Results.csv**
    
      Speichern Sie den folgenden Text in einer Windows-Registrierungsdatei unter Verwendung eines filename-Suffixes von. reg; Beispiel: DisableResultsCsv. reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**
    
      Speichern Sie den folgenden Text in einer Windows-Registrierungsdatei unter Verwendung eines filename-Suffixes von. reg; Beispiel: DisableManifestXml. reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. Klicken oder Doppelklicken Sie in Windows-Explorer auf die reg-Datei, die Sie in den vorherigen Schritten erstellt haben.
    
4. Klicken Sie im Fenster Benutzerzugriffssteuerung auf **Ja** , damit der Registrierungs-Editor die Änderung vornehmen kann. 
    
5. Wenn Sie aufgefordert werden, den Vorgang fortzusetzen, klicken Sie auf **Ja**.
    
    Der Registrierungs-Editor zeigt eine Meldung an, die besagt, dass die Einstellung der Registrierung erfolgreich hinzugefügt wurde.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Bearbeiten von Registrierungseinstellungen zum erneuten Aktivieren der Export Berichte

Wenn Sie die Results.csv-und Manifest.xml-Berichte deaktiviert haben, indem Sie die reg-Dateien im vorherigen Verfahren erstellt haben, können Sie diese Dateien bearbeiten, um einen Bericht erneut zu aktivieren, sodass er mit den Suchergebnissen exportiert wird. Führen Sie erneut das folgende Verfahren auf dem Computer aus, mit dem Sie die Ergebnisse mit einer Inhaltssuche exportieren.
  
1. Schließen Sie das eDiscovery-Export Tool, wenn es geöffnet ist.
    
2. Bearbeiten Sie eine oder beide der reg-Bearbeitungs Dateien, die Sie im vorherigen Verfahren erstellt haben.
    
    - **Results.csv**
    
        Öffnen Sie die Datei DisableResultsCsv. reg im Editor, ändern Sie den Wert in `False` `True` , und speichern Sie die Datei. Nachdem Sie die Datei beispielsweise bearbeitet haben, sieht Sie wie folgt aus:
    
        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**
    
        Öffnen Sie die Datei DisableManifestXml. reg im Editor, ändern Sie den Wert in `False` `True` , und speichern Sie die Datei. Nachdem Sie die Datei beispielsweise bearbeitet haben, sieht Sie wie folgt aus:
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. Klicken oder Doppelklicken Sie in Windows-Explorer auf eine REG-Datei, die Sie im vorherigen Schritt bearbeitet haben.
    
4. Klicken Sie im Fenster Benutzerzugriffssteuerung auf **Ja** , damit der Registrierungs-Editor die Änderung vornehmen kann. 
    
5. Wenn Sie aufgefordert werden, den Vorgang fortzusetzen, klicken Sie auf **Ja**.
    
    Der Registrierungs-Editor zeigt eine Meldung an, die besagt, dass die Einstellung der Registrierung erfolgreich hinzugefügt wurde.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Häufig gestellte Fragen zum Deaktivieren von Export Berichten

 **Was sind die Results.csv-und Manifest.xml Berichte?**
  
Die Results.csv-und Manifest.xml-Dateien enthalten zusätzliche Informationen zu dem exportierten Inhalt.
  
- **Results.csv** Ein Excel-Dokument, das Informationen zu jedem Element enthält, das als Suchergebnis heruntergeladen wird. Bei e-Mails enthält das Ergebnisprotokoll Informationen zu den einzelnen Nachrichten, einschließlich: 
    
  - Der Speicherort der Nachricht im Quellpostfach (einschließlich der Angabe, ob die Nachricht sich im primären oder im Archivpostfach befindet).
    
  - Das Datum, an dem die Nachricht gesendet oder empfangen wurde.
    
  - Die Betreffzeile der Nachricht.
    
  - Absender und Empfänger der Nachricht.
    
  - Gibt an, ob es sich bei der Nachricht um eine doppelte Nachricht handelt, wenn Sie beim Exportieren der Suchergebnisse die Deduplizierung aktiviert haben. Doppelte Nachrichten weisen einen Wert in der **übergeordneten Itemid** -Spalte auf, die die Nachricht als Duplikat identifiziert. Der Wert in der **übergeordneten Itemid** -Spalte ist identisch mit dem Wert in der Spalte **Element Dokument-Nr** der exportierten Nachricht. 
    
    Bei Dokumenten aus SharePoint-und OneDrive für Unternehmen-Websites enthält das Ergebnisprotokoll Informationen zu den einzelnen Dokumenten, einschließlich:
    
  - Die URL für das Dokument.
    
  - Die URL für die Websitesammlung, in der sich das Dokument befindet.
    
  - Das Datum, an dem das Dokument zuletzt geändert wurde.
    
  - Der Name des Dokuments (der sich in der Spalte Betreff im Ergebnisprotokoll befindet).
    
- **Manifest.xml** Eine Manifestdatei (im XML-Format), die Informationen zu jedem Element enthält, das in den Suchergebnissen enthalten ist. Die Informationen in diesem Bericht sind identisch mit dem Results.csv Bericht, jedoch in dem Format, das im Electronic Discovery Reference Model (EDRM) angegeben ist. Weitere Informationen zu EDRM finden Sie unter [https://www.edrm.net](https://www.edrm.net) .
    
 **Wann sollte ich den Export dieser Berichte deaktivieren?**
  
Dies hängt von ihren spezifischen Anforderungen ab. Viele Organisationen benötigen keine zusätzlichen Informationen zu Suchergebnissen und benötigen diese Berichte nicht.
  
 **Auf welchem Computer muss ich diese Funktion ausführen?**
  
 Sie müssen die Registrierungseinstellung auf einem lokalen Computer ändern, auf dem Sie das eDiscovery-Export Tool ausführen. 
  
 **Muss ich den Computer neu starten, nachdem ich diese Einstellung geändert habe?**
  
Nein, Sie müssen den Computer nicht neu starten. Wenn das eDiscovery-Export Tool jedoch aktiv ist, müssen Sie es schließen und neu starten, nachdem Sie die Registrierungseinstellung geändert haben.
  
 **Wird ein vorhandener Registrierungsschlüssel bearbeitet oder wird ein neuer Schlüssel erstellt?**
  
Ein neuer Registrierungsschlüssel wird erstellt, wenn Sie die reg-Datei zum ersten Mal ausführen, die Sie im Verfahren in diesem Thema erstellt haben. Anschließend wird die Einstellung jedes Mal bearbeitet, wenn Sie die reg-Bearbeitungs Datei ändern und erneut ausführen.
