---
title: Erstellen benutzerdefinierter vertraulicher Informationstypen mit genauer Datenübereinstimmung
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Erfahren Sie, wie Sie benutzerdefinierte vertrauliche Informationstypen mit genauer Datenübereinstimmungsklassifizierung erstellen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1c47d682d7b3c52fa5ca5b71386a764f3b3da693
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "47546957"
---
# <a name="create-custom-sensitive-information-types-with-exact-data-match-based-classification"></a>Erstellen von benutzerdefinierten vertraulichen Informationstypen mit genauer Datenübereinstimmungsklassifizierung

[Benutzerdefinierte Typen vertraulicher Informationen](custom-sensitive-info-types.md) werden verwendet, um vertrauliche Elemente zu identifizieren, sodass Sie verhindern können, dass Sie versehentlich oder in unangemessener Weise geteilt werden. Sie können einen benutzerdefinierten Typ vertraulicher Informationen folgendermaßen definieren:

- Durch Muster
- Durch den Nachweis von Schlüsselwörtern, z. B. *Mitarbeiter*, *Badge*oder *ID*
- Ähnliche Zeichen als Nachweis in einem bestimmten Muster
- Konfidenzniveaus

 Solche benutzerdefinierten vertraulichen Informationstypen erfüllen die geschäftlichen Anforderungen vieler Organisationen.

Was aber, wenn Sie einen benutzerdefinierten vertraulichen Informationstyp nutzen möchten, der genaue Datenwerte verwendet, anstatt eines Typs, der Übereinstimmungen basierend auf generischen Mustern findet? Mit einer EDM-basierten Klassifizierung (Exact Data Match, genaue Datenübereinstimmung) können Sie einen benutzerdefinierten Informationstyp mit den folgenden Merkmalen erstellen:

- dynamisch und aktualisierbar
- skalierbarer
- weniger falsch positive Ergebnisse
- arbeitet mit strukturierten vertraulichen Daten
- behandelt vertrauliche Informationen sicherer
- mit verschiedenen Microsoft Cloud Services verwendbar

![EDM-basierte Klassifikation](../media/EDMClassification.png)

Die EDM-basierte Klassifikation ermöglicht es Ihnen, benutzerdefinierte vertrauliche Informationstypen zu erstellen, die sich auf genaue Werte in einer Datenbank mit vertraulichen Informationen beziehen. Die Datenbank kann täglich aktualisiert werden und bis zu 100 Millionen Datenzeilen enthalten. Mitarbeiter, Patienten oder Kunden kommen und gehen und Datensätze ändern sich, aber Ihre benutzerdefinierten vertraulichen Informationstypen bleiben aktuell und anwendbar. Darüber hinaus können Sie EDM-basierte Klassifikation mit Richtlinien verwenden, z. B. [Richtlinien zur Verhinderung von Datenverlust](data-loss-prevention-policies.md) (Data Loss Prevention, DLP) oder [Microsoft Cloud App Security-Dateirichtlinien](https://docs.microsoft.com/cloud-app-security/data-protection-policies).

> [!NOTE]
> Microsoft 365 Information Protection unterstützt jetzt in der Vorschau Doppelbyte-Zeichensatz-Sprachen für:
> - Chinesisch (vereinfacht)
> - Chinesisch (traditionell)
> - Koreanisch
> - Japanisch
> 
>Diese Vorschau ist nur in der kommerziellen Cloud verfügbar, und die Einführung ist beschränkt auf:
> - Japan
> - Korea
> - China
> - Hongkong (SAR)
> - Macau (SAR)
> - Taiwan
>
>Diese Unterstützung ist für vertrauliche Informationstypen verfügbar. Mehr dazu finden Sie in den [Versionshinweisen (Vorschau) zur Unterstützung des Informationsschutzes für Doppelbyte-Zeichensätze](mip-dbcs-relnotes.md).

## <a name="required-licenses-and-permissions"></a>Erforderliche Lizenzen und Berechtigungen

Sie müssen ein globaler, Compliance- oder Exchange Online-Administrator sein, um die in diesem Artikel beschriebenen Aufgaben auszuführen. Weitere Informationen über DLP-Berechtigungen finden Sie unter [Berechtigungen](data-loss-prevention-policies.md#permissions).

Die EDM-basierte Klassifizierung ist in diesen Abonnements enthalten.

- Office 365 E5
- Microsoft 365 E5
- Microsoft 365 E5 Compliance
- Microsoft E5/ A5 Information Protection und Governance

## <a name="portal-links-for-your-subscription"></a>Portal Links für Ihr Abonnement


|Portal  |Weltweit/GCC  |GCC – hoch  |DOD  |
|---------|---------|---------|---------|
|Office SCC     |  protection.office.com       |scc.office365.us         |scc.protection.apps.mil |
|Microsoft 365 Security Center     |security.microsoft.com         |security.microsoft.us         |security.apps.mil|
|Microsoft 365 Compliance Center     |compliance.microsoft.com         |compliance.microsoft.us         |compliance.apps.mil|


## <a name="the-work-flow-at-a-glance"></a>Der Workflow auf einen Blick

|Phase  |Anforderungen  |
|---------|---------|
|[Teil 1: Einrichten der EDM-basierten Klassifizierung](#part-1-set-up-edm-based-classification)<br/><br/>(je nach Bedarf)<br/>- [Bearbeiten des Datenbankschemas](#editing-the-schema-for-edm-based-classification) <br/>- [Entfernen des Schemas](#removing-the-schema-for-edm-based-classification) |– Lesezugriff auf vertrauliche Daten<br/>– Datenbankschema im XML-Format (Beispiel)<br/>– Regelpaket im XML-Format (Beispiel)<br/>– Administratorberechtigungen für das Security & Compliance Center (mithilfe von PowerShell) |
|[Teil 2: Hashen und Hochladen vertraulicher Daten](#part-2-hash-and-upload-the-sensitive-data)<br/><br/>(je nach Bedarf)<br/>[Aktualisieren der Daten](#refreshing-your-sensitive-information-database) |– Benutzerdefinierte Sicherheitsgruppe und Benutzerkonto<br/>– Lokaler Administratorzugriff auf den Computer mit dem EDM-Upload-Agent<br/>– Lesezugriff auf vertrauliche Daten<br/>– Prozess und Zeitplan für die Datenaktualisierung|
|[Teil 3: Verwenden der EDM-basierten Klassifizierung mit Ihren Microsoft Cloud Services](#part-3-use-edm-based-classification-with-your-microsoft-cloud-services) |– Microsoft 365-Abonnement mit DLP<br/>– EDM-basiertes Klassifizierungsfeature aktiviert |

### <a name="part-1-set-up-edm-based-classification"></a>Teil 1: Einrichten der EDM-basierten Klassifizierung

Das Einrichten und Konfigurieren der EDM-basierten Klassifizierung umfasst:

1. [Speichern vertraulicher Daten im CSV-Format](#save-sensitive-data-in-csv-format)
2. [Definieren Ihres Datenbankschemas für vertrauliche Informationen](#define-the-schema-for-your-database-of-sensitive-information)
3. [Erstellen eines Regelpakets](#set-up-a-rule-package)


#### <a name="save-sensitive-data-in-csv-format"></a>Speichern vertraulicher Daten im CSV-Format

1. Identifizieren Sie die vertraulichen Informationen, die Sie verwenden möchten. Exportieren Sie die Daten in eine App, wie z. B. Microsoft Excel, und speichern Sie die Datei im CSV-Format. Die Datendatei kann maximal Folgendes umfassen:
      - bis zu 100 Millionen Zeilen vertraulicher Daten
      - bis zu 32 Spalten (Felder) pro Datenquelle
      - bis zu 5 als durchsuchbar markierte Spalten (Felder)

2. Strukturieren Sie die vertraulichen Daten in der CSV-Datei so, dass die erste Zeile die Namen der für die EDM-basierte Klassifizierung verwendeten Felder enthält. Möglicherweise gibt es in Ihrer CSV-Datei Feldnamen, wie z. B. "SSN", "Geburtsdatum", "Vorname" oder "Nachname". Die Namen der Spaltenüberschriften dürfen keine Leerzeichen oder Unterstriche enthalten. Die CSV-Datei, die wir in diesem Artikel verwenden, trägt beispielsweise den Namen  *PatientRecords.csv*, und hat u. a. die Spalten  *PatientID*, *MRN*, *LastName*, *FirstName* und  *SSN*.

#### <a name="define-the-schema-for-your-database-of-sensitive-information"></a>Definieren des Schemas für Ihre Datenbank mit vertraulichen Informationen

3. Definieren Sie das Schema für die Datenbank mit vertraulichen Informationen im XML-Format (ähnlich wie in unserem Beispiel unten). Nennen Sie diese Schemadatei **edm.xml**, und konfigurieren Sie sie so, dass es für jede Spalte in der Datenbank eine Zeile mit der folgenden Syntax gibt: 

      `\<Field name="" searchable=""/\>`.

      - Verwenden Sie Spaltennamen für *Field name*-Werte.
      - Verwenden Sie *searchable="true* für maximal 5 Felder, die durchsuchbar sein sollen. Mindestens ein Feld muss durchsuchbar sein.

      Im folgenden Beispiel definiert die XML-Datei das Schema für eine Datenbank mit Patientendatensätzen, wobei fünf Felder als durchsuchbar angegeben werden: *PatientID*, *MRN*, *SSN*, *Phone* und *DOB*.

      (Sie können das Beispiel kopieren, ändern und verwenden.)

      ```xml
      <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
            <DataStore name="PatientRecords" description="Schema for patient records" version="1">
                  <Field name="PatientID" searchable="true" />
                  <Field name="MRN" searchable="true" />
                  <Field name="FirstName" />
                  <Field name="LastName" />
                  <Field name="SSN" searchable="true" />
                  <Field name="Phone" searchable="true" />
                  <Field name="DOB" searchable="true" />
                  <Field name="Gender" />
                  <Field name="Address" />
            </DataStore>
      </EdmSchema>
      ```

4. Informationen zum Herstellen der Verbindung zu Security & Compliance Center PowerShell finden Sie unter [Verbinden mit Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).

5. Führen Sie die folgenden Cmdlets nacheinander aus, um das Datenbankschema hochzuladen:

      ```powershell
      $edmSchemaXml=Get-Content .\\edm.xml -Encoding Byte -ReadCount 0
      New-DlpEdmSchema -FileData $edmSchemaXml -Confirm:$true
      ```

      Sie werden zu folgenden Bestätigungen aufgefordert:

      > Bestätigen
      >
      > Möchten Sie diese Aktion wirklich ausführen?
      >
      > Das neue EDM-Schema für den Datenspeicher „patientrecords“ wird importiert.
      >
      > \[J\] Ja \[A\] Ja für alle \[N\] Nein \[L\] Nein für alle \[?\] Hilfe (Standard ist "J"):

> [!TIP]
> Wenn Sie möchten, dass Ihre Änderungen ohne Bestätigung durchgeführt werden, verwenden Sie in Schritt 5 stattdessen das folgende Cmdlet: New-DlpEdmSchema -FileData $edmSchemaXml

> [!NOTE]
> Es kann zwischen 10–60 Minuten dauern, bis das EDMSchema durch Ergänzungen aktualisiert wird. Das Update muss abgeschlossen sein, bevor Sie Schritte ausführen, die die Zusätze verwenden.

#### <a name="set-up-a-rule-package"></a>Einrichten eines Regelpakets

1. Erstellen Sie ein Regelpaket im XML-Format (mit Unicode-Codierung), ähnlich wie im folgenden Beispiel. (Sie können das Beispiel kopieren, ändern und verwenden.)

      Vergewissern Sie sich beim Einrichten des Regelpakets, dass Sie die CSV-Datei und die **edm.xml**-Datei korrekt referenzieren. Sie können das Beispiel kopieren, ändern und verwenden. In dieser XML-Beispieldatei müssen die folgenden Felder so angepasst werden, dass Sie Ihren vertraulichen EDM-Typ erstellen:

      - **RulePack id und ExactMatch id**: Verwenden Sie [New-GUID](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6), um eine GUID zu generieren.

      - **Datenspeicher**: Dieses Feld gibt den zu verwendenden EDM-Nachschlage-Datenspeicher an. Sie geben einen Datenquellennamen eines konfigurierten EDM-Schemas an.

      - **idMatch**: Dieses Feld verweist auf das primäre Element für EDM.
        - Stimmt überein mit: gibt das Feld an, das in der exakten Suche verwendet werden soll. Sie geben den Namen eines durchsuchbaren Felds im EDM-Schema für den Datenspeicher an.
        - Klassifizierung: Dieses Feld gibt die Übereinstimmung für den vertraulichen Typ an, der EDM-Nachschlagevorgänge auslöst. Sie können den Namen oder die GUID einer vorhandenen integrierten oder benutzerdefinierten Klassifizierung angeben.

      - **Übereinstimmung:** Dieses Feld verweist auf zusätzliche Nachweise, die sich in der Nähe von "idMatch" befinden.
        - Stimmt überein mit: Sie geben einen Feldnamen im EDM-Schema für den Datenspeicher an.
      - **Ressource:** In diesem Abschnitt werden der Name und die Beschreibung für den vertraulichen Typ in mehreren Sprachversionen angegeben.
        - idRef: Sie geben die GUID für die ExactMatch-ID an.
        - Name und Beschreibungen: nach Bedarf anpassen.

      ```xml
      <RulePackage xmlns="http://schemas.microsoft.com/office/2018/edm">
        <RulePack id="fd098e03-1796-41a5-8ab6-198c93c62b11">
          <Version build="0" major="2" minor="0" revision="0" />
          <Publisher id="eb553734-8306-44b4-9ad5-c388ad970528" />
          <Details defaultLangCode="en-us">
            <LocalizedDetails langcode="en-us">
              <PublisherName>IP DLP</PublisherName>
              <Name>Health Care EDM Rulepack</Name>
              <Description>This rule package contains the EDM sensitive type for health care sensitive types.</Description>
            </LocalizedDetails>
          </Details>
        </RulePack>
        <Rules>
          <ExactMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB371" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
            <Pattern confidenceLevel="65">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
            </Pattern>
            <Pattern confidenceLevel="75">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
              <Any minMatches ="3" maxMatches ="6">
                <match matches="PatientID" />
                <match matches="MRN"/>
                <match matches="FirstName"/>
                <match matches="LastName"/>
                <match matches="Phone"/>
                <match matches="DOB"/>
              </Any>
            </Pattern>
          </ExactMatch>
          <LocalizedStrings>
            <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB371">
              <Name default="true" langcode="en-us">Patient SSN Exact Match.</Name>
              <Description default="true" langcode="en-us">EDM Sensitive type for detecting Patient SSN.</Description>
            </Resource>
          </LocalizedStrings>
        </Rules>
      </RulePackage>
      ```

1. Laden Sie das Regelpaket hoch, indem Sie nacheinander die folgenden PowerShell-Cmdlets ausführen:

      ```powershell
      $rulepack=Get-Content .\\rulepack.xml -Encoding Byte -ReadCount 0
      New-DlpSensitiveInformationTypeRulePackage -FileData $rulepack
      ```

Sie haben die EDM-basierte Klassifizierung nun eingerichtet. Der nächste Schritt ist das Hashen vertraulicher Daten, gefolgt vom Hochladen der Hashes für die Indizierung.

Wie Sie im vorherigen Verfahren erfahren haben, wurden im PatientRecords-Schema fünf Felder als durchsuchbar definiert: *PatientID*, *MRN*, *SSN*, *Phone* und *DOB*. Unser Beispiel für ein Regelpaket enthält diese Felder und verweist auf die Datenbankschemadatei (**edm.xml**), mit einem  *ExactMatch* -Element pro durchsuchbarem Feld. Sehen Sie sich das folgende ExactMatch-Element an:

```xml
<ExactMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB371" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
      <Pattern confidenceLevel="65">
        <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
        <Any minMatches ="3" maxMatches ="100">
          <match matches="PatientID" />
          <match matches="MRN"/>
          <match matches="FirstName"/>
          <match matches="LastName"/>
          <match matches="Phone"/>
          <match matches="DOB"/>
        </Any>
      </Pattern>
    </ExactMatch>
```

Beachten Sie in diesem Beispiel Folgendes:

- Der dataStore-Name verweist auf die zuvor erstellte CSV-Datei: **dataStore = "PatientRecords"**.

- Der idMatch-Wert verweist auf ein durchsuchbares Feld, das in der Datenbankschema-Datei aufgelistet ist: **idMatch matches = "SSN"**.

- Der classification-Wert verweist auf einen vorhandenen oder benutzerdefinierten vertraulichen Informationstyp: **classification = "US-Sozialversicherungsnummer (SSN)"**. (In diesem Fall wird der vorhandene vertrauliche Informationstyp "US-Sozialversicherungsnummer" verwendet.)

> [!NOTE]
> Es kann zwischen 10–60 Minuten dauern, bis das EDMSchema durch Ergänzungen aktualisiert wird. Das Update muss abgeschlossen sein, bevor Sie Schritte ausführen, die die Zusätze verwenden.

#### <a name="editing-the-schema-for-edm-based-classification"></a>Bearbeiten des Schemas für die EDM-basierte Klassifikation

Wenn Sie Änderungen an Ihrer **edm.xml**-Datei vornehmen und z. B. ändern möchten, welche Felder für die EDM-basierte Klassifikation verwendet werden, führen Sie die folgenden Schritte aus:

1. Bearbeiten Sie Ihre **edm.xml**-Datei (die Datei, die im Abschnitt [Definieren des Schemas](#define-the-schema-for-your-database-of-sensitive-information) in diesem Artikel behandelt wird).

2. Informationen zum Herstellen der Verbindung zu Security & Compliance Center PowerShell finden Sie unter [Verbinden mit Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).

3. Führen Sie die folgenden Cmdlets nacheinander aus, um Ihr Datenbankschema zu aktualisieren:

      ```powershell
      $edmSchemaXml=Get-Content .\\edm.xml -Encoding Byte -ReadCount 0
      Set-DlpEdmSchema -FileData $edmSchemaXml -Confirm:$true
      ```

      Sie werden zu folgenden Bestätigungen aufgefordert:

      > Bestätigen
      >
      > Möchten Sie diese Aktion wirklich ausführen?
      >
      > Das EDM-Schema für den Datenspeicher „patientrecords“ wird aktualisiert.
      >
      > \[J\] Ja \[A\] Ja für alle \[N\] Nein \[L\] Nein für alle \[?\] Hilfe (Standard ist "J"):

      > [!TIP]
      > Wenn Sie möchten, dass Ihre Änderungen ohne Bestätigung durchgeführt werden, verwenden Sie in Schritt 3 stattdessen das folgende Cmdlet: Set-DlpEdmSchema -FileData $edmSchemaXml

      > [!NOTE]
      > Es kann zwischen 10–60 Minuten dauern, bis das EDMSchema durch Ergänzungen aktualisiert wird. Das Update muss abgeschlossen sein, bevor Sie Schritte ausführen, die die Zusätze verwenden.

#### <a name="removing-the-schema-for-edm-based-classification"></a>Entfernen des Schemas für die EDM-basierte Klassifikation

(Nach Bedarf) Wenn Sie das Schema entfernen möchten, das Sie für die EDM-basierte Klassifizierung verwenden, gehen Sie folgendermaßen vor:

1. Informationen zum Herstellen der Verbindung zu Security & Compliance Center PowerShell finden Sie unter [Verbinden mit Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).

2. Führen Sie die folgenden PowerShell-Cmdlets aus, und ersetzen Sie dabei den Datenspeichernamen "patient records" durch den Namen, den Sie entfernen möchten:

      ```powershell
      Remove-DlpEdmSchema -Identity patientrecords
      ```

      Sie werden zum Bestätigen aufgefordert:

      > Bestätigen
      >
      > Möchten Sie diese Aktion wirklich ausführen?
      >
      > Das EDM-Schema für den Datenspeicher „patientrecords“ wird entfernt.
      >
      > \[J\] Ja \[A\] Ja für alle \[N\] Nein \[L\] Nein für alle \[?\] Hilfe (Standard ist "J"):

      > [!TIP]
      >  Wenn Sie möchten, dass Ihre Änderungen ohne Bestätigung durchgeführt werden, verwenden Sie in Schritt 2 stattdessen das folgende Cmdlet: Remove-DlpEdmSchema -Identity patientrecords -Confirm:$false


<!-- salt notes
need two salting procedures, one for onestep from the externally facing and another for two step, on an internal machine then the upload from the external machine

- create A  folder put the edmupload agent and, csv and salt file there, run all processes there
- 
- stuff you need to have first: DataStoreName, /DataFile name (csv file)  /Hashlocation

- salt can be randomly generated by Microsoft or can be provided by the customer. If provided by the customer it must follow  format of 64 character, and can contain only letters or 0-9 characters.  Use a website to generate a valid salt value.
 
- can run EDMuploadagent.exe from PS or Windows cmd window . tested on Windows Server 2016 or Windows 10 and dot net version 4.6.2

when defiuning the schema file the searchable fields must be either an out of box SIT or custom SIT, only 5 fields )column headings) can be searchable

1. From outbound access device from the cmd prompt run EdmUploadAgent.exe /Authorize -  
2. data store schema must have already been uploaded
3.  create hash first then do upload
4. EdmUploadAgent.exe /CreateHash /DataFile (where the data file is ) E:\emd\test\data\schema32_1000000,csv /HashLocation  (where to store it) E:\edm\tat\hash this makes the salt file and the hash file as output
5. next is upload EdmUploadAgent.exe /UploadHash /DataStoreName (found in the Schema file DataSore name="FOO" /HashFile (path to hash file locaztion and file name /HashLocation path to hash)  for example
1.EdmUploadAgent/exe /UploadHash /DataStoreName schema321 /HashFile E:\edm\test\hash\schema32_10000000.EdmHash /HashLocation E:\edm\test\hash  -this one  uses MSFT generated salt, so no need to provide

Salt is an optional parameter so if yo uwant to use a custom salt add /salt and the salt value if salt file not copied to the outbound machine 

OR copy both files hash and salt to the same directory and the commmand will get both


OR do it in single step hash, salt ulopad

!! once they download the updated upload agent they will always have SALT, there is no going back.


all in one step: EdmUploadAgent.exe /UploadData /DataStoreName schema321 /DataFile E:\edm\test\data\schema32_10000.csv /HashLocation E:\edm\test\hash

tshooting/check status cmd



Once it gets to completed the admin can start using it in the custom SIT

they have to get their own custom SALT

just copy SALT over in a secure fashion










1.
6.
7.
1.  


 -->

### <a name="part-2-hash-and-upload-the-sensitive-data"></a>Teil 2: Hashvorgang durchführen und vertrauliche Daten hochladen

In dieser Phase richten Sie eine benutzerdefinierte Sicherheitsgruppe, ein Benutzerkonto und das Tool EDM-Upload-Agent ein. Dann verwenden Sie das Tool, um für die vertraulichen Daten mit Salt-Wert einen Hashvorgang durchzuführen und sie hochzuladen.

Der Hashvorgang und das Hochlande können mit einem einzigen Computer durchgeführt werden. Sie können aber auch den Hashvorgang vom Upload trennen, um größere Sicherheit zu gewährleisten.

Wenn Sie den Hashvorgang und das Hochladen von einem Computer aus durchführen möchten, muss dieser eine direkte Verbindung zu Ihrem Microsoft 365-Mandanten herstellen können. Dies setzt voraus, dass für den Hashvorgang die vertraulichen Datendateien im Klartext auf diesem Computer bereitstehen.

Wenn Sie Ihre vertrauliche Datendatei im Klartext nicht verfügbar machen möchten, können Sie den Hashvorgang auf einem Computer an einem sicheren Ort durchführen, und dann die Hashdatei und die Saltdatei auf einen Computer kopieren, der für das Hochladen eine direkte Verbindung mit Ihrem Microsoft 365-Mandanten herstellen kann. In diesem Szenario benötigen Sie das den EDM-Upload-Agenten auf beiden Computern. 

#### <a name="prerequisites"></a>Voraussetzungen

- Ein Microsoft 365-Geschäfts-, Schul- oder Unikonto, das der **EDM-\_DataUploaders**-Sicherheitsgruppe hinzugefügt wird
- Einen Computer mit Windows 10 oder Windows Server 2016 mit .NET Version 4.6.2, um den EDM-Upload-Agenten auszuführen
- Ein Verzeichnis auf dem für das Hochladen verwendeten Computer für den:
    -  EDM-Upload-Agenten
    - Ihre vertrauliche Elementdatei im CSV-Format (in unseren Beispielen **"PatientRecords.csv"**)
    -  sowie die Output-Hash- und-Saltdateien
    - Den Namen des Datenspeichers aus der Datei **EDM.xml** (in diesem Beispiel `PatientRecords`)

#### <a name="set-up-the-security-group-and-user-account"></a>Einrichten der Sicherheitsgruppe und des Benutzerkontos

1. Als globaler Administrator gehen Sie über den entsprechenden [Link für Ihr Abonnement](#portal-links-for-your-subscription) zum Verwaltungszentrum und  [erstellen Sie eine Sicherheitsgruppe](https://docs.microsoft.com/office365/admin/email/create-edit-or-delete-a-security-group?view=o365-worldwide) namens **EDM\_DataUploaders**.

2. Fügen Sie einen oder mehrere Benutzer zur **EDM\_DataUploaders**-Sicherheitsgruppe hinzu. (Diese Benutzer verwalten die Datenbank mit vertraulichen Informationen.)

#### <a name="hash-and-upload-from-one-computer"></a>Hash und Upload von einem Computer

Dieser Computer muss direkten Zugriff auf Ihren Microsoft 365-Mandanten haben.

>[!NOTE]
> Bevor Sie mit diesem Verfahren beginnen, stellen Sie sicher, dass Sie Mitglied der  **EDM\_DataUploaders** -Sicherheitsgruppe sind.

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>Links zum EDM-Upload-Agenten nach Abonnementtyp

- [Handel und GCC](https://go.microsoft.com/fwlink/?linkid=2088639)
- [GCC – hoch](https://go.microsoft.com/fwlink/?linkid=2137521)
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807)

1. Erstellen Sie ein Arbeitsverzeichnis für das den EDM-Upload-Agenten. Das kann beispielsweise das Verzeichnis **C:\EDM\Data** sein. Platzieren Sie dort die Datei **PatientRecords.csv"**.

2. Laden Sie den für Ihr Abonnement geeigneten [EDM-Upload-Agenten](#links-to-edm-upload-agent-by-subscription-type) herunter und installieren Sie ihn in das im ersten Schritt erstellte Verzeichnis.

> [!NOTE]
> Der EDM-Upload-Agent unter den oben aufgeführten Links wurde aktualisiert, um automatisch einen Saltwert zu den Hashdaten hinzuzufügen. Alternativ können Sie auch ihren eigenen Saltwert angeben. Sobald Sie diese Version verwendet haben, können Sie die vorherige Version des EDM-Upload-Agenten nicht mehr verwenden.
>
> Sie können Daten mit dem EDM-Upload-Agenten nur zwei Mal pro Tag in einen bestimmten Datenspeicherort hochladen.

> [!TIP]
> Um eine Liste der unterstützten Befehlsparameter zu erhalten, führen Sie den Agenten ohne Argumente aus. Zum Beispiel "EdmUploadAgent.exe".

2. Autorisieren Sie den EDM-Upload-Agenten Öffnen Sie dafür die Eingabeaufforderung (als Administrator), wechseln Sie ins Verzeichnis **C:\EDM\Data** und führen Sie dann den folgenden Befehl aus:

   `EdmUploadAgent.exe /Authorize`

3. Melden Sie sich mit Ihrem Microsoft 365-Geschäfts-, Schul- oder Unikonto an, das der Sicherheitsgruppe „EDM_DataUploaders“hinzugefügt wurde. Ihre Mandanteninformationen werden aus dem Benutzerkonto extrahiert, um die Verbindung herzustellen.

4. Um den Hashvorgang durchzuführen die vertraulichen Daten hochzuladen, führen Sie den folgenden Befehl in der Eingabeaufforderung aus:

`EdmUploadAgent.exe /UploadData /DataStoreName \<DataStoreName\> /DataFile \<DataFilePath\> /HashLocation \<HashedFileLocation\>`

Beispiel: **EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash**

Dadurch wird dem Hashwert automatisch ein zufällig generierter Saltwert hinzugefügt, um die Sicherheit zu vergrößern. Wenn Sie optional einen eigenen Saltwert verwenden möchten, fügen Sie dem Befehl **/Salt <saltvalue>** hinzu. Dieser Wert muss 64 Zeichen umfassen und darf nur die Zeichen a-z und die Ziffern 0-9 enthalten.

5. Überprüfen Sie den Uploadstatus, indem Sie den folgenden Befehl ausführen:

`EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>`

Beispiel: **EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords**

Suchen Sie nach dem Status in **ProcessingInProgress**. Überprüfen Sie den Status alle paar Minuten, bis er sich zu **Abgeschlossen** geändert hat. Sobald der Status „Abgeschlossen“ angezeigt wird, können Sie die EDM-Daten verwenden.

#### <a name="separate-hash-and-upload"></a>Trennen von Hash und Upload

Führen Sie den Hashvorgang auf einem Computer in einer sicheren Umgebung aus.

1. Führen Sie in den Eingabeaufforderungsfenstern den folgenden Befehl aus:

`EdmUploadAgent.exe /CreateHash /DataFile \<DataFilePath\> /HashLocation \<HashedFileLocation\>`

Beispiel:

> **EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash**

Dadurch wird eine Hashdatei und eine Saltdatei mit diesen Erweiterungen ausgegeben, wenn Sie die Option **/Salt <saltvalue>** nicht angegeben haben:
- .EdmHash
- .EdmSalt

2. Kopieren Sie diese Dateien auf sichere Weise auf den Computer, den Sie verwenden, um Ihre CSV-Datei mit den vertraulichen Elementen (PatientRecords) in ihren-Mandanten hochzuladen.

Führen Sie zum Hochladen gehashter Daten den folgenden Befehl in der Windows-Eingabeaufforderung aus:

`EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\>`

Zum Beispiel:

> **EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\PatientRecords.EdmHash**


Führen Sie zur Überprüfung, ob Ihre vertraulichen Daten hochgeladen wurden, den folgenden Befehl in der Windows-Eingabeaufforderung aus:


`EdmUploadAgent.exe /GetDataStore`

Sie sehen eine Liste der Datenspeicher und wann sie zuletzt aktualisiert wurden.

Wenn Sie alle Daten sehen möchten, die in einen bestimmten Store hochgeladen wurden, führen Sie den folgenden Befehl in einer Windows-Eingabeaufforderung aus:

`EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>`

Fahren Sie mit dem Einrichten des Prozesses und des Zeitplans für das [Aktualisieren der Datenbank für vertrauliche Informationen](#refreshing-your-sensitive-information-database) fort.

Sie können nun die EDM-basierte Klassifikation mit Ihren Microsoft Cloud Services verwenden. Sie können beispielsweise [eine DLP-Richtlinie mithilfe der EDM-basierten Klassifizierung einrichten](#to-create-a-dlp-policy-with-edm).

#### <a name="refreshing-your-sensitive-information-database"></a>Aktualisieren der Datenbank für vertrauliche Informationen

Sie können Ihre Datenbank für vertrauliche Informationen täglich aktualisieren, und das EDM-Upload-Tool kann die vertraulichen Daten neu indizieren und dann die indizierten Daten erneut hochladen.

1. Ermitteln Sie den Vorgang und die Häufigkeit (täglich oder wöchentlich) zum Aktualisieren der Datenbank mit vertraulichen Informationen.

2. Exportieren Sie die vertraulichen Daten erneut in eine App, wie z. B. Microsoft Excel, und speichern Sie die Datei im CSV-Format. Behalten Sie den Dateinamen und den Speicherort bei, den Sie beim Ausführen der unter  [Hashen und Hochladen vertraulicher Daten](#part-2-hash-and-upload-the-sensitive-data) beschriebenen Schritte verwendet haben.

      > [!NOTE]
      > Wenn es keine Änderungen an der Struktur (Feldnamen) der CSV-Datei gibt, müssen Sie auch keine an der Datenbankschemadatei vornehmen, wenn Sie die Daten aktualisieren. Wenn Sie jedoch Änderungen vornehmen müssen, stellen Sie sicher, dass Sie das Datenbankschema und Ihr Regelpaket entsprechend bearbeiten.

3. Mithilfe des  [Aufgabenplaners](https://docs.microsoft.com/windows/desktop/TaskSchd/task-scheduler-start-page)  können Sie die Schritte 2 und 3 im Verfahren [Hashen und Hochladen vertraulicher Daten](#part-2-hash-and-upload-the-sensitive-data)  automatisieren. Sie können Aufgaben mithilfe verschiedener Methoden planen:

      | Methode             | Vorgehensweise |
      | ---------------------- | ---------------- |
      | Windows PowerShell     | Siehe die Dokumentation [Aufgabenplanung](https://docs.microsoft.com/powershell/module/scheduledtasks/?view=win10-ps) und das [PowerShell-Beispielskript](#example-powershell-script-for-task-scheduler) in diesem Artikel |
      | Aufgabenplaner-API     | Lesen Sie die Dokumentation [Aufgabenplanung](https://docs.microsoft.com/windows/desktop/TaskSchd/using-the-task-scheduler)                                                                                                                                                                                                                                                                                |
      | Windows-Benutzeroberfläche | Klicken Sie in Windows auf **Start**, und geben Sie „Aufgabenplanung“ ein. Klicken Sie dann in der Ergebnisliste mit der rechten Maustaste auf **Aufgabenplanung** und wählen Sie **Als Administrator ausführen** aus.                                                                                                                                                                                                                                                                           |

#### <a name="example-powershell-script-for-task-scheduler"></a>„PowerShell-Beispielskript“ für „Aufgabenplanung“

Dieser Abschnitt enthält ein Beispiel für ein PowerShell-Skript, mit dem Sie Ihre Aufgaben zum Hashen von Daten und Hochladen gehashter Daten planen können:

##### <a name="to-schedule-hashing-and-upload-in-a-combined-step"></a>So planen Sie das Hashen und Hochladen in einem kombinierten Schritt

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
\# Assuming CSV file name is same as data store name
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

#### <a name="to-schedule-hashing-and-upload-as-separate-steps"></a>So planen Sie das Hashen und Hochladen als separate Schritte

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
\# Assuming CSV file name is same as data store name
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

### <a name="part-3-use-edm-based-classification-with-your-microsoft-cloud-services"></a>Teil 3: Verwenden der EDM-basierten Klassifizierung mit Ihren Microsoft Cloud Services

Diese Speicherorte sind unterstützte Typen vertraulicher EDM-Informationen:

- DLP für Exchange Online (E-Mail)
- OneDrive for Business (Dateien)
- Microsoft Teams (Unterhaltungen)
- DLP für SharePoint (Dateien)
- DLP-Richtlinien für Microsoft Cloud App-Sicherheit

Vertrauliche EDM-Informationstypen für die folgenden Szenarien sind derzeit in der Entwicklung, aber noch nicht verfügbar:

- automatische Klassifizierung von Vertraulichkeits- und Aufbewahrungsbezeichnungen

#### <a name="to-create-a-dlp-policy-with-edm"></a>Erstellen einer DLP-Richtlinie mit EDM

1. Gehen Sie zum Security & Compliance Center, indem Sie den entsprechenden [Link für Ihr Abonnement](#portal-links-for-your-subscription) verwenden.

2. Klicken Sie auf die **Richtlinie** \> **zur Verhinderung von Datenverlust**.

3. Wählen Sie **Richtlinie erstellen** \> **Benutzerdefiniert** \> **Weiter** aus.

4. Geben Sie auf der Registerkarte **Richtlinie benennen** einen Namen und eine Beschreibung ein, und wählen Sie dann **Weiter** aus.

5. Wählen Sie auf der Registerkarte **Speicherorte auswählen**  **Bestimmte Speicherorte auswählen** und dann **Weiter** aus.

6. Wählen Sie in der Spalte **Status**  **Exchange-E-Mail, OneDrive-Konten, Teams-Chat und Kanalnachricht** und dann **Weiter** aus.

7. Wählen Sie auf der Registerkarte **Richtlinieneinstellungen**  **Erweiterte Einstellungen verwenden** und dann **Weiter** aus.

8. Wählen Sie **+ Neue Regel** aus.

9. Geben Sie im Abschnitt **Name** einen Namen und eine Beschreibung für die Regel ein.

10. Wählen Sie im Abschnitt **Bedingungen** in der Liste **+ Bedingung hinzufügen**  **Inhalt enthält vertraulichen Typ** aus.

      ![Inhalt enthält sensible Informationstypen](../media/edm-dlp-newrule-conditions.png)

11. Suchen Sie den vertraulichen Informationstyp, den Sie beim Einrichten Ihres Regelpakets erstellt haben, und wählen Sie dann **+ Hinzufügen** aus.  
    Wählen Sie dann **Fertig** aus.

12. Wählen Sie Optionen für die Regel aus, wie z. B. **Benutzerbenachrichtigungen**, **Außerkraftsetzungen durch Benutzer**, **Schadensberichte** usw., und dann **Speichern** aus.

13. Überprüfen Sie auf der Registerkarte **Richtlinieneinstellungen** Ihre Regeln und wählen Sie dann **Weiter** aus.

14. Geben Sie an, ob Sie die Richtlinie sofort aktivieren, testen oder deaktivieren möchten. Wählen Sie dann **Weiter** aus.

15. Überprüfen Sie auf der Registerkarte **Überprüfen Sie Ihre Einstellungen** Ihre Richtlinie. Nehmen Sie alle nötigen Änderungen vor. Wenn Sie fertig sind, wählen Sie **Erstellen** aus.

> [!NOTE]
> Es kann ungefähr eine Stunde dauern, bis Ihre neue DLP-Richtlinie im Rechenzentrum erscheint.

## <a name="related-articles"></a>Verwandte Artikel

- [Entitätsdefinitionen für Typen vertraulicher Informationen](sensitive-information-type-entity-definitions.md)
- [Benutzerdefinierte vertrauliche Informationstypen](custom-sensitive-info-types.md)
- [Überblick über DLP-Richtlinien](data-loss-prevention-policies.md)
- [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)
- [New-DlpEdmSchema](https://docs.microsoft.com/powershell/module/exchange/new-dlpedmschema)

