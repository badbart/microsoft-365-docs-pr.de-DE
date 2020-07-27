---
title: Doppelschlüssel Verschlüsselung (DKE)
description: Mit DKE können Sie hoch vertrauliche Daten schützen und gleichzeitig die vollständige Kontrolle über Ihren Schlüssel behalten.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 07/21/2020
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
localization_priority: Normal
ms.collection:
- M365-security-compliance
ms.openlocfilehash: d9ed155576d69889e53e4e4d1ce03e4233fd08ff
ms.sourcegitcommit: 4789b261eb029d7c965421a1260acc110e6385db
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387442"
---
# <a name="double-key-encryption-dke"></a>Doppelschlüssel Verschlüsselung (DKE)

> *Gilt für: Doppelschlüssel Verschlüsselung für Microsoft 365 Public Preview, [Microsoft 365-Compliance](https://www.microsoft.com/microsoft-365/business/compliance-management), [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection Unified Labeling-Client für Windows](https://docs.microsoft.com/azure/information-protection/faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*
>
> *Dienstbeschreibung für: [Microsoft 365 Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Bei der Doppelschlüssel Verschlüsselung (Double Key Encryption, DKE) werden zwei Schlüssel zusammen verwendet, um auf geschützte Inhalte zuzugreifen. Sie speichern einen Schlüssel in Microsoft Azure und halten die andere Taste. Der Azure Information Protection Unified Labeling-Client schützt hochsensible Inhalte, während Sie den Vollzugriff auf einen Ihrer Schlüssel beibehalten.

Die Doppelschlüssel Verschlüsselung unterstützt sowohl Cloud-als auch lokale Bereitstellungen. Mithilfe dieser Bereitstellungen kann sichergestellt werden, dass verschlüsselte Daten immer deckend bleiben, wenn Sie die geschützten Daten speichern.

Weitere Informationen zu den standardmäßigen cloudbasierten Mandantenstamm Schlüsseln finden Sie unter [Planning and Implementing your Azure Information Protection Mandant Key](https://docs.microsoft.com/azure/information-protection/plan-implement-tenant-key).

Im folgenden Video wird gezeigt, wie die doppelte Schlüssel Verschlüsselung funktioniert, um Ihre Inhalte zu schützen.

> [!VIDEO https://msit.microsoftstream.com/embed/video/f466a1ff-0400-a936-221c-f1eab45dc756]

Wenn Ihre Organisationen eine der folgenden Anforderungen haben, können Sie DKE verwenden, um Ihre Inhalte zu schützen:

- Sie möchten sicherstellen, dass *nur Sie* geschützte Inhalte immer entschlüsseln können, unter allen Umständen.
- Sie möchten nicht, dass Microsoft selbst Zugriff auf geschützte Daten hat.
- Sie haben regulatorische Anforderungen, um Schlüssel innerhalb einer geografischen Grenze zu halten. Alle Schlüssel, die Sie für die Datenverschlüsselung und-Entschlüsselung speichern, werden in Ihrem Rechenzentrum verwaltet.

## <a name="system-and-licensing-requirements-for-dke"></a>System-und Lizenzierungsanforderungen für DKE

Doppelschlüssel Verschlüsselung für Microsoft 365, Teil von Microsoft 365 E5 und Office 365 E5. Wenn Sie nicht über eine Microsoft 365 E5-Lizenz verfügen, können Sie sich für eine [Testversion](https://aka.ms/M365E5ComplianceTrial)registrieren. Weitere Informationen zu diesen Lizenzen finden Sie unter [Microsoft 365 Licensing Guidance for Security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Office-Insider** Um die öffentliche Vorschau verwenden zu können, müssen Sie Mitglied des Office-Insider Programms sein. Um an Office Insider teilzunehmen, wechseln Sie zu [https://insider.office.com](https://insider.office.com) . Nachdem Sie Mitglied sind, bereiten Sie Ihre Umgebung für die Bereitstellung von Office Insider-Builds vor, indem Sie die richtige Bereitstellungsmethode für Ihre Organisation auswählen. Anweisungen finden Sie unter [Erste Schritte bei der Bereitstellung von Office-Insider-Builds](https://insider.office.com/business/deploy).

**Azure Information Protection**. DKE arbeitet mit Sensitivitäts Bezeichnungen und benötigt Azure Information Protection.

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>Unterstützte Umgebungen zum Speichern und anzeigen DKE geschützter Inhalte

**Unterstützte Anwendungen**. [Microsoft 365-Apps für Enterprise](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) -Clients unter Windows, einschließlich Word, Excel und PowerPoint.

**Online-Inhalts Unterstützung**. Dokumente und Dateien, die Online in Microsoft SharePoint und OneDrive für Unternehmen gespeichert werden, werden unterstützt. Sie können verschlüsselte Inhalte per e-Mail freigeben, aber keine verschlüsselten Dokumente und Dateien online anzeigen. Stattdessen müssen Sie geschützte Inhalte mithilfe der Desktop-Apps auf dem lokalen Computer anzeigen.

## <a name="about-this-public-preview-article"></a>Informationen zu diesem öffentlichen Vorschau-Artikel

Sie können einige der Schritte zum Bereitstellen der doppelten Schlüssel Verschlüsselung auf verschiedene Weise ausführen. In diesem Artikel werden ausführliche Anweisungen bereitgestellt, damit erfahrene Administratoren den Dienst erfolgreich bereitstellen. Wenn Sie sich dafür entscheiden, können Sie Ihre eigenen Methoden verwenden.

Dieser Artikel enthält schrittweise Anweisungen zum Bereitstellen des doppelten Schlüssel Verschlüsselungs Diensts in Azure. Dieses Szenario ist nicht das, was Sie wahrscheinlich in der Produktion tun würden. Für die öffentliche Vorschau ist die Verwendung von Azure ein schneller Weg zur Bereitstellung von DKE. Durch die Bereitstellung in Azure können Sie sofort mit der doppelten Schlüssel Verschlüsselung beginnen.

Sie können den Dienst lokal in Ihrem Netzwerk oder mit einem anderen Anbieter bereitstellen. Sie müssen den Schlüsselspeicher mit Methoden veröffentlichen, die für diesen Speicherort geeignet sind.

## <a name="deploy-double-key-encryption"></a>Bereitstellen der doppelten Schlüssel Verschlüsselung

In diesem Artikel und dem Bereitstellungs Video wird Azure als Bereitstellungsziel für den DKE-Dienst verwendet. Wenn Sie an einem anderen Speicherort bereitstellen, müssen Sie Ihre eigenen Werte angeben.

Sehen Sie sich das [Video zur Bereitstellung der doppelten Schlüssel Verschlüsselung](https://msit.microsoftstream.com/video/cfdda3ff-0400-a521-1579-f1eacc37fc7e) an, um eine Schritt-für-Schritt-Übersicht der Konzepte im Artikel zu erhalten. Das Video dauert etwa 18 Minuten.

Sie führen die folgenden allgemeinen Schritte aus, um die doppelte Schlüssel Verschlüsselung für Ihre Organisation einzurichten.

1. [Installieren der erforderlichen Softwarekomponenten](#install-software-prerequisites)
1. [Klonen des GitHub-Repositorys mit doppelten Schlüssel Verschlüsselung](#clone-the-dke-github-repository)
1. [Ändern von Anwendungseinstellungen](#modify-application-settings)
1. [Generieren von Test Schlüsseln](#generate-test-keys)
1. [Erstellen des Projekts](#build-the-project)
1. [Veröffentlichen des Schlüsselspeichers](#publish-the-key-store)
1. [Überprüfen der Bereitstellung](#validate-your-deployment)
1. [Registrieren des Schlüsselspeichers](#register-your-key-store)
1. [Erstellen von Vertraulichkeitsbezeichnungen](#create-labels-using-dke)

Wenn Sie fertig sind, können Sie Dokumente und Dateien mit DKE verschlüsseln. Weitere Informationen finden Sie unter [Anwenden von Sensitivitäts Bezeichnungen auf Ihre Dateien und e-Mails in Office](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

### <a name="install-software-prerequisites"></a>Installieren der erforderlichen Softwarekomponenten

Es gibt zwei Arten von Softwarevoraussetzungen für die Doppelschlüssel Verschlüsselung.

- [Voraussetzungen für den doppelten Schlüssel Verschlüsselungsdienst](#double-key-encryption-service-prerequisites)
- [Zwei wichtige Verschlüsselungs Voraussetzungen für Clientcomputer](#double-key-encryption-prerequisites-for-client-computers)

#### <a name="double-key-encryption-service-prerequisites"></a>Voraussetzungen für den doppelten Schlüssel Verschlüsselungsdienst

Installieren Sie diese Voraussetzungen auf dem Computer, auf dem Sie den DKE-Dienst installieren möchten.

**.Net Core 3,1 SDK**. Laden Sie das SDK herunter, und installieren Sie es aus dem [Download .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio Code**. Laden Sie Visual Studio Code aus herunter [https://code.visualstudio.com/](https://code.visualstudio.com) . Nachdem Sie installiert haben, führen Sie Visual Studio Code aus, und wählen Sie **View** \> **Extensions**aus. Installieren Sie diese Erweiterungen.

- C# für Visual Studio Code

- NuGet-Paket-Manager

**Microsoft Office Insider**. Richten Sie mindestens eine [Bereitstellungsmethode](https://insider.office.com/business/deploy)ein.

**Git-Ressourcen**. Laden Sie eine der folgenden Optionen herunter, und installieren Sie Sie.

- [Git](https://git-scm.com/downloads)

- [GitHub-Desktop](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**OpenSSL** Sie müssen [OpenSSL](https://slproweb.com/products/Win32OpenSSL.html) installiert haben, um [Testschlüssel zu generieren](#generate-test-keys) , nachdem Sie DKE bereitgestellt haben. Stellen Sie sicher, dass Sie sie ordnungsgemäß aus dem Pfad der Umgebungsvariablen aufrufen. Weitere Informationen finden Sie beispielsweise unter "Add the Installation Directory to Path" unter https://www.osradar.com/install-openssl-windows/ .

#### <a name="double-key-encryption-prerequisites-for-client-computers"></a>Zwei wichtige Verschlüsselungs Voraussetzungen für Clientcomputer

Installieren Sie diese Voraussetzungen auf jedem Clientcomputer, auf dem geschützte Dokumente geschützt und verwendet werden sollen.

**Microsoft Office** Version *. 12711 oder höher.

**Azure Information Protection Unified Labelling-Client** Versionen 2.7.93.0 oder höher. Laden Sie den Unified Labeling-Client von [Microsoft](https://www.microsoft.com/download/details.aspx?id=53018)herunter, und installieren Sie ihn.

### <a name="clone-the-dke-github-repository"></a>Klonen des DKE GitHub-Repositorys

Microsoft stellt die DKE-Quelldateien in einem GitHub-Repository bereit. Sie klonen das Repository, um das Projekt für die Verwendung in Ihrer Organisation lokal zu erstellen. Das DKE GitHub-Repository befindet sich unter [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService) .

Die folgenden Anweisungen sind für Benutzer mit unerfahrenem git oder Visual Studio Code gedacht:

1. Wechseln Sie in Ihrem Browser zu:[https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService)

1. Klicken Sie auf der rechten Seite des Bildschirms auf **Code**. Ihre Version der Benutzeroberfläche zeigt möglicherweise eine Schaltfläche " **Klonen" oder "herunterladen** ". Wählen Sie dann in der Dropdownliste, die angezeigt wird, das Symbol Kopieren aus, um die URL in Ihre Zwischenablage zu kopieren.

    Beispiel:

    :::image type="content" source="../media/dke-clone.png" alt-text="Klonen des Double Key-Verschlüsselungsdienst-Repositorys von GitHub":::

3. Wählen Sie in Visual Studio Code **View** die Option \> **Befehls Palette** anzeigen aus, und wählen Sie **git: Clone**aus. Um zur Option in der Liste zu wechseln, beginnen Sie mit der Eingabe, `git: clone` um die Einträge zu filtern, und wählen Sie Sie dann im Dropdown aus. Beispiel:

    :::image type="content" source="../media/dke-vscode-clone.png" alt-text="Visual Studio Code git: Clone Option":::

4. Fügen Sie in das Textfeld die URL ein, die Sie aus git kopiert haben, und wählen Sie **aus GitHub Klonen aus**.

5. Navigieren Sie im angezeigten Dialogfeld **Ordner auswählen** zu einem Speicherort, und wählen Sie ihn aus, um das Repository zu speichern. Wählen Sie an der Eingabeaufforderung **Öffnen**aus.

    Das Repository wird in Visual Studio Code geöffnet und zeigt den aktuellen git-Zweig unten links an. Die Verzweigung sollte " **Master**" sein.

    Beispiel:

    :::image type="content" source="../media/dke-vscode-master.png" alt-text="Visual Studio Code Master Verzweigung":::

6. Wählen Sie das Wort **Master aus,** und wählen Sie dann in der Liste der Verzweigungen **public_preview** aus.

   > [!IMPORTANT]
   > Wenn Sie die public_preview Verzweigung auswählen, stellen Sie sicher, dass Sie über die richtigen Dateien zum Erstellen des Projekts verfügen. Wenn Sie nicht die richtige Verzweigung auswählen, wird die Bereitstellung nicht erfolgreich ausgeführt.

Sie haben Ihr DKE-Quell-Repository jetzt lokal eingerichtet. Ändern Sie als nächstes die [Anwendungseinstellungen](#modify-application-settings) für Ihre Organisation.

### <a name="modify-application-settings"></a>Ändern von Anwendungseinstellungen

Um den DKE-Dienst bereitzustellen, müssen Sie die folgenden Arten von Anwendungseinstellungen ändern:

- [Wichtige Zugriffseinstellungen](#key-access-settings)
- [Mandanten-und Schlüsseleinstellungen](#tenant-and-key-settings)

Sie ändern Anwendungseinstellungen in der Datei appsettings.js. Diese Datei befindet sich im DoubleKeyEncryptionService Repo, das Sie lokal unter DoubleKeyEncryptionService\src\customer-Key-Store. geklont haben. Beispielsweise können Sie in Visual Studio Code die Datei wie in der folgenden Abbildung gezeigt durchsuchen.

:::image type="content" source="../media/dke-appsettingsjson.png" alt-text="Suchen der appsettings.jsDatei für DKE.":::

#### <a name="key-access-settings"></a>Wichtige Zugriffseinstellungen

Wählen Sie aus, ob e-Mail-oder Rollenautorisierung verwendet werden soll. DKE unterstützt immer nur eine dieser Authentifizierungsmethoden.

- **E-Mail-Autorisierung**. Ermöglicht Ihrer Organisation die Autorisierung des Zugriffs auf Schlüssel nur basierend auf e-Mail-Adressen.

- **Rollenautorisierung**. Ermöglicht Ihrer Organisation das Autorisieren des Zugriffs auf Schlüssel basierend auf Active Directory Gruppen und erfordert, dass der Webdienst LDAP Abfragen kann.

**So legen Sie die wichtigsten Zugriffseinstellungen für DKE mithilfe der e-Mail-Autorisierung fest**

1. Öffnen Sie die Datei **appsettings.jsauf** , und suchen Sie die `AuthorizedEmailAddress` Einstellung.

2. Fügen Sie die e-Mail-Adressen hinzu, die Sie autorisieren möchten. Trennen Sie mehrere e-Mail-Adressen mit doppelten Anführungszeichen und Kommas. Beispiel:

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. Suchen `LDAPPath` Sie die Einstellung, und entfernen Sie den Text `If role authorization is used then this is the LDAP path` zwischen den doppelten Anführungszeichen. Lassen Sie die doppelten Anführungszeichen an der richtigen Stelle. Wenn Sie fertig sind, sollte die Einstellung wie folgt aussehen.

   ```json
   "LDAPPath": ""
   ```

4. Suchen Sie die `AuthorizedRoles` Einstellung, und löschen Sie die gesamte-Reihe.

Dieses Bild zeigt die **appsettings.jsauf** Datei, die für die e-Mail-Autorisierung ordnungsgemäß formatiert ist.

   :::image type="content" source="../media/dke-email-accesssetting.png" alt-text="Die appsettings.jsder Datei mit e-Mail-Autorisierungsmethode":::

**So legen Sie wichtige Zugriffseinstellungen für DKE mithilfe der Rollenautorisierung fest**

1. Öffnen Sie die Datei **appsettings.jsauf** , und suchen Sie die `AuthorizedRoles` Einstellung.

2. Fügen Sie die Active Directory Gruppennamen hinzu, die Sie autorisieren möchten. Trennen Sie mehrere Gruppennamen mit doppelten Anführungszeichen und Kommas. Beispiel:

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. Suchen `LDAPPath` Sie die Einstellung, und fügen Sie die Active Directory Domäne hinzu. Beispiel:

   ```json
   "LDAPPath": "contoso.com"
   ```

4. Suchen Sie die `AuthorizedEmailAddress` Einstellung, und löschen Sie die gesamte-Reihe.

Dieses Bild zeigt die **appsettings.jsauf** Datei, die für die Rollenautorisierung ordnungsgemäß formatiert ist.

   :::image type="content" source="../media/dke-role-accesssetting.png" alt-text="appsettings.jsfür die Datei mit der Rollen Autorisierungsmethode":::

#### <a name="tenant-and-key-settings"></a>Mandanten-und Schlüsseleinstellungen

DKE-Mandanten-und Key-Einstellungen befinden sich in der Datei **appsettings.js** .

**So konfigurieren Sie die Mandanten-und Schlüsseleinstellungen für DKE**

1. Öffnen Sie die Datei **appsettings.js** .

2. Suchen `ValidIssuers` Sie die Einstellung, und ersetzen `<tenantid>` Sie Sie durch ihre Mandanten-ID. Sie können die Mandanten-ID ermitteln, indem Sie zum Azure-Portal wechseln und die [Mandanten Eigenschaften](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties)anzeigen. Beispiel:

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

Suchen Sie nach der `JwtAudience` . Ersetzen Sie `<yourhostname>` durch den Hostnamen des Computers, auf dem der DKE-Dienst ausgeführt wird. Beispiel:



  > [!IMPORTANT]
  > Der Wert für `JwtAudience` muss mit dem Namen des Hosts *genau*übereinstimmen. Sie können **localhost: 5001** beim Debuggen verwenden. Wenn Sie das Debuggen abgeschlossen haben, sollten Sie diesen Wert jedoch auf den Hostnamen des Servers aktualisieren.

- `TestKeys:Name`. Geben Sie einen Namen für den Schlüssel ein. Beispiel: `TestKey1`
- `TestKeys:Id`. Erstellen Sie eine GUID, und geben Sie Sie als `TestKeys:ID` Wert ein. Beispiel: `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Sie können eine Website wie den [Online-GUID-Generator](https://guidgenerator.com/) verwenden, um eine GUID nach dem Zufallsprinzip zu generieren.

Dieses Bild zeigt das richtige Format für Mandanten-und Tasteneinstellungen in **appsettings.jsauf**. `LDAPPath`ist für die Rollenautorisierung konfiguriert.

:::image type="content" source="../media/dke-appsettingsjson-tenantkeysettings.png" alt-text="Zeigt die richtigen Mandanten-und Schlüsseleinstellungen für DKE in der Datei appsettings.js.":::

### <a name="generate-test-keys"></a>Generieren von Test Schlüsseln

Sobald Ihre Anwendungseinstellungen definiert sind, können Sie öffentliche und private Testschlüssel generieren.

So generieren Sie Schlüssel:

1. Führen Sie im Windows-Startmenü die OpenSSL-Eingabeaufforderung aus.

1. Wechseln Sie zu dem Ordner, in dem Sie die Testschlüssel speichern möchten. Die Dateien, die Sie erstellen, indem Sie die Schritte in dieser Aufgabe ausführen, werden im gleichen Ordner gespeichert.

1. Generieren Sie den neuen Testschlüssel.

   ```dos
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

2. Generiert den privaten Schlüssel.

   ```dos
   openssl rsa -in key.pem -out privkeynopass.pem
   ```

1. Generieren Sie den öffentlichen Schlüssel.

   ```dos
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

1. Öffnen Sie in einem Text-Editor **pubkeyonly. PEM**. Kopieren Sie den gesamten Inhalt der Datei **pubkeyonly. PEM** , mit Ausnahme der ersten und der letzten Zeile, in den `PublicPem` Abschnitt der Datei **appsettings.js** .

1. Öffnen Sie in einem Text-Editor **privkeynopass. PEM**. Kopieren Sie den gesamten Inhalt der Datei **privkeynopass. PEM** , mit Ausnahme der ersten und der letzten Zeile, in den `PrivatePem` Abschnitt der Datei **appsettings.js** .

1. Entfernen Sie alle Leerzeichen und Zeilen Umrisse in `PublicPem` den `PrivatePem` Abschnitten und.

    > [!IMPORTANT]
    > Wenn Sie diesen Inhalt kopieren, löschen Sie keine PEM-Daten.

1. Navigieren Sie in Visual Studio Code zur **Startup.cs** -Datei. Diese Datei befindet sich im DoubleKeyEncryptionService Repo, das Sie lokal unter DoubleKeyEncryptionService\src\customer-Key-store\. geklont haben.

2. Suchen Sie die folgenden Zeilen:

   ```c#
        #if USE_TEST_KEYS
        #error !!!!!!!!!!!!!!!!!!!!!! Use of test keys is only supported for testing,
        DO NOT USE  FOR PRODUCTION !!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
        #endif
   ```

3. Ersetzen Sie diese Zeilen durch den folgenden Text:

   ```csharp
   services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
   ```

   Die Endergebnisse sollten etwa wie folgt aussehen.

   :::image type="content" source="../media/dke-startupcs-usetestkeys.png" alt-text="Startup.cs-Datei für die öffentliche Vorschau":::

Jetzt sind Sie fertig, um [Ihr DKE-Projekt zu erstellen](#build-the-project).

### <a name="build-the-project"></a>Erstellen des Projekts

Verwenden Sie die folgenden Anweisungen, um das DKE-Projekt lokal zu erstellen:

1. Wählen Sie in Visual Studio Code im DKE-Dienst-Repository **View** die Option \> **Befehls Palette** anzeigen aus, und geben Sie dann an der Eingabeaufforderung **Erstellen** ein.

1. Wählen Sie in der Liste **Aufgaben: Build-Task ausführen**aus.

   Wenn keine Build-Tasks gefunden werden, wählen Sie Create **Task konfigurieren** aus, und erstellen Sie wie folgt einen für .net Core.

   :::image type="content" source="../media/dke-configurebuildtask.png" alt-text="Konfigurieren fehlender Build-Aufgabe für .net":::

   1. Wählen Sie **tasks.jsaus Vorlage erstellen aus**.

   :::image type="content" source="../media/dke-createtasksjsonfromtemplate.png" alt-text="Erstellen tasks.jsDatei aus der Vorlage für DKE":::

   2. Wählen Sie in der Liste der Vorlagentypen **.net Core**aus.

   :::image type="content" source="../media/dke-tasksjsontemplate.png" alt-text="Erstellen tasks.jsDatei aus der Vorlage für DKE":::

   3. Suchen Sie im Abschnitt erstellen nach dem Pfad zur Datei **customerkeystore. csproj** . Wenn er nicht vorhanden ist, fügen Sie die folgende Reihe hinzu:

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

  4. Führen Sie den Build erneut aus.

1. Stellen Sie sicher, dass im Ausgabefenster keine roten Fehler vorhanden sind.

   Wenn rote Fehler vorliegen, überprüfen Sie die Konsolenausgabe. Stellen Sie sicher, dass Sie alle vorherigen Schritte ordnungsgemäß abgeschlossen haben und die richtigen Build-Versionen vorhanden sind.

2. Wählen **Run** Sie \> **Start Debuggen** ausführen aus, um den Prozess zu debuggen. Wenn Sie zur Auswahl einer Umgebung aufgefordert werden, wählen Sie **.net Core**aus.

Der .net Core-Debugger wird normalerweise in "'" gestartet https://localhost:5001 `. To view your test key, go to ` https://localhost:5001 und ein Schrägstrich (/) und der Name des Schlüssels angefügt. Beispiel:

```https
https://localhost:5001/TestKey1
```

Der Schlüssel sollte im JSON-Format angezeigt werden.

Ihr Setup ist nun abgeschlossen. Stellen Sie vor dem Veröffentlichen des Keystores in appsettings.jsauf für die JwtAudience-Einstellung sicher, dass der Wert für Hostname genau mit dem Namen des App-Diensthosts übereinstimmt. Möglicherweise haben Sie es zu localhost geändert, um die Problembehandlung für den Build auszuführen.

### <a name="publish-the-key-store"></a>Veröffentlichen des Schlüsselspeichers

Zum Veröffentlichen des Schlüsselspeichers erstellen Sie eine Azure-App-Dienstinstanz, die ihre DKE-Bereitstellung hostet. Als Nächstes veröffentlichen Sie die generierten Schlüssel in Azure.

**So erstellen Sie eine Azure-Webanwendung-Instanz zum Hosten Ihrer DKE-Bereitstellung**

1. Melden Sie sich in Ihrem Browser beim [Microsoft Azure-Portal](https://ms.portal.azure.com)an, und wechseln Sie zu **App-Dienste**  >  **Hinzufügen**.

1. Wählen Sie Ihre Abonnement-und Ressourcengruppe aus, und definieren Sie die Details der Instanz.

    - Geben Sie den Hostnamen des Computers ein, auf dem Sie den DKE-Dienst installieren möchten. Stellen Sie sicher, dass der Name dem Namen entspricht, der für die JwtAudience-Einstellung in der Datei [**appsettings.js**](#tenant-and-key-settings) für festgelegt wurde. Der Wert, den Sie für den Namen angeben, ist auch der WebAppInstanceName.

    - Wählen Sie für **veröffentlichen**den **Code**aus, und wählen Sie für **Laufzeitstapel** **.net Core 3,1**aus.

    Beispiel:

    :::image type="content" source="../media/dke-azure-add-app-service.png" alt-text="Hinzufügen des App-Diensts":::

1. Wählen Sie unten auf der Seite **überprüfen + erstellen**aus, und wählen Sie dann **Hinzufügen**aus.

1. Führen Sie einen der folgenden Schritte aus, um die generierten Schlüssel in Azure zu veröffentlichen:

    - [Veröffentlichen über ZipDeployUI](#publish-via-zipdeployui)
    - [Veröffentlichen über FTP](#publish-via-ftp)
    - [Veröffentlichen über Visual Studio 2019 oder höher](https://docs.microsoft.com/aspnet/core/tutorials/)
    - [Veröffentlichen in einem lokalen System](https://docs.microsoft.com/aspnet/core/tutorials/publish-to-iis?view=aspnetcore-3.1&tabs=netcore-cli)

    > [!NOTE]
    > Möglicherweise bevorzugen Sie andere Methoden zum Bereitstellen der Schlüssel. Wählen Sie die Methode aus, die für Ihre Organisation am besten geeignet ist.

    > [!TIP]
    > Die [Veröffentlichung über Visual Studio](https://docs.microsoft.com/aspnet/core/tutorials/) und an ein [Lokales System](https://docs.microsoft.com/aspnet/core/tutorials/publish-to-iis?view=aspnetcore-3.1&tabs=netcore-cli) wird in der [ASP .NET-Dokumentation](https://docs.microsoft.com/aspnet/core/)beschrieben. Wenn Sie eine dieser Methoden verwenden, öffnen Sie die Anweisungen in einer separaten Registerkarte, damit Sie nach Abschluss des Verfahrens problemlos zurückkehren können.

#### <a name="publish-via-zipdeployui"></a>Veröffentlichen über ZipDeployUI

1. Navigieren Sie in das Verzeichnis `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`.

    Beispiel: https://customerkeystoreforpublicpreview.scm.azurewebsites.net/ZipDeployUI

1. Wechseln Sie in der CodeBase für den Schlüsselspeicher zum Ordner **Customer-Key-store\src\customer-Key-Store** , und vergewissern Sie sich, dass dieser Ordner die Datei **customerkeystore. csproj** enthält.

1. Ausführen: **dotnet veröffentlichen**

     Das Ausgabefenster zeigt das Verzeichnis an, in dem die Veröffentlichung bereitgestellt wurde.

    Beispiel: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

1. Senden Sie alle Dateien im Veröffentlichungsverzeichnis an eine ZIP-Datei. Stellen Sie beim Erstellen der ZIP-Datei sicher, dass sich alle Dateien im Verzeichnis auf der Stammebene der ZIP-Datei befinden.

1. Ziehen Sie die ZIP-Datei, die Sie erstellen, auf die ZipDeployUI-Website, die Sie oben geöffnet haben. Beispiel: https://customerkeystoreforpublicpreview.scm.azurewebsites.net/ZipDeployUI

DKE wird bereitgestellt, und Sie können zu den Test Schlüsseln navigieren, die Sie erstellt haben. Über [prüfen Sie Ihre Bereitstellung](#validate-your-deployment) weiter unten.

#### <a name="publish-via-ftp"></a>Veröffentlichen über FTP

1. Stellen Sie eine Verbindung mit dem [oben](#publish-the-key-store)erstellten App-Dienst her.

    Wechseln Sie in Ihrem Browser zu: **Azure Portal**  >  **App Service**  >  **Deployment Center**  >  **Manual Deployment**  >  **FTP**  >  **Dashboard**.

1. Kopieren Sie die angezeigten Verbindungszeichenfolgen in eine lokale Datei. Sie verwenden diese Zeichenfolgen, um eine Verbindung zum Webdienst des Webanwendungs herzustellen und Dateien über FTP hochzuladen.

    Beispiel:

    :::image type="content" source="../media/dke-ftp-dashboard.png" alt-text="Kopieren von Verbindungszeichenfolgen aus dem FTP-Dashboard":::

1. Wechseln Sie in der CodeBase für den Schlüsselspeicher zum **Verzeichnis Customer-Key-store\src\customer-Key-Store**.

1. Stellen Sie sicher, dass dieses Verzeichnis die Datei **customerkeystore. csproj** enthält.

1. Ausführen: **dotnet veröffentlichen**

    Die Ausgabe enthält das Verzeichnis, in dem die Veröffentlichung bereitgestellt wurde.

    Beispiel: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

1. Senden Sie alle Dateien im Veröffentlichungsverzeichnis in eine ZIP-Datei. Stellen Sie beim Erstellen der ZIP-Datei sicher, dass sich alle Dateien im Verzeichnis auf der Stammebene der ZIP-Datei befinden.

1. Verwenden Sie von Ihrem FTP-Client die Verbindungsinformationen, die Sie zum Herstellen einer Verbindung mit Ihrem App-Dienst kopiert haben. Laden Sie die ZIP-Datei, die Sie im vorherigen Schritt erstellt haben, in das Stammverzeichnis Ihrer Webanwendung hoch.

DKE wird bereitgestellt, und Sie können zu den Test Schlüsseln navigieren, die Sie erstellt haben. Als nächstes [validieren Sie Ihre Bereitstellung](#validate-your-deployment).

### <a name="validate-your-deployment"></a>Überprüfen der Bereitstellung

Nachdem Sie DKE mit einer der oben beschriebenen Methoden bereitgestellt haben, überprüfen Sie die Bereitstellung und die Schlüsselspeicher Einstellungen.

Ausführen

src\customer-key-store\scripts\key_store_tester.ps1 mykeystoreurl/MyKey

Beispiel:

key_store_tester.ps1https://mycustomerkeystore.com/mykey

Stellen Sie sicher, dass in der Ausgabe keine Fehler angezeigt werden. Wenn Sie fertig sind, [registrieren Sie Ihren Schlüsselspeicher](#register-your-key-store).

## <a name="register-your-key-store"></a>Registrieren des Schlüsselspeichers

Mit den folgenden Schritten können Sie den Schlüsselspeicher registrieren. Das Registrieren des Schlüsselspeichers ist der letzte Schritt bei der Bereitstellung von DKE, bevor Sie mit dem Erstellen von Beschriftungen beginnen können.

So registrieren Sie Ihren Schlüsselspeicher:

1. Öffnen Sie in Ihrem Browser das [Microsoft Azure-Portal](https://ms.portal.azure.com/), und wechseln Sie zu **alle Services** - \> **Identitäts** - \> **App-Registrierungen**.

2. Wählen Sie **neue Registrierung**aus, und geben Sie einen aussagekräftigen Namen ein.

3. Wählen Sie in den angezeigten Optionen einen Kontotyp aus.

    Wenn Sie Microsoft Azure mit einer nicht benutzerdefinierten Domäne wie **onmicrosoft.com**verwenden, wählen Sie **Konten nur in diesem Organisations Verzeichnis aus (nur Microsoft – einzelner Mandant).**

    Beispiel:

    :::image type="content" source="../media/dke-app-registration.png" alt-text="Neue APP-Registrierung":::

4. Wählen Sie unten auf der Seite **registrieren** aus, um die neue APP-Registrierung zu erstellen.

5. Wählen Sie in der neuen App-Registrierung im linken Bereich unter **Verwalten**die Option **Authentifizierung**aus.

6. Wählen Sie **Plattform hinzufügen**aus.
 
7. Wählen Sie im Popup **Konfigurieren von Plattformen** die Option **Internet**aus.
 
8. Geben Sie unter **Umleitungs-URIs**den URI des doppelten Schlüssel Verschlüsselungs Diensts ein. Geben Sie die APP-Dienst-URL ein, einschließlich des Hostnamens und der Domäne.

    Beispiel: https://mycustomerkeystoretest.com

    - Die eingegebene URL muss mit dem Hostnamen übereinstimmen, in dem der Schlüsselspeicher bereitgestellt wird.
    - Wenn Sie lokal mit Visual Studio testen, verwenden Sie **https://localhost:5001** .
    - In allen Fällen muss das Schema **https**sein.

    Stellen Sie sicher, dass der Hostname genau mit dem Hostnamen des App-Diensts übereinstimmt. Möglicherweise haben Sie es geändert, um `localhost` die Problembehandlung beim Build zu beheben. In **appsettings.json**ist dieser Wert der Hostname, für den Sie festgelegt haben `JwtAudience` .

6. Aktivieren Sie unter **implizite Gewährung**das Kontrollkästchen **ID-Token** .

1. Wählen Sie **Speichern** aus, um Ihre Änderungen zu speichern.

7. Wählen Sie im linken Bereich **eine API verfügbar machen**aus, und wählen Sie dann neben Anwendungs-ID-URI die Option **festlegen**aus.

9. Wählen Sie auf der Seite **eine API verfügbar machen** im Bereich **durch diese API definierte Bereiche** die Option **Bereich hinzufügen**aus. Im neuen Bereich:

    1. Definieren Sie den Bereichsnamen als **user_impersonation**.

    2. Wählen Sie die Administratoren und Benutzer, die zustimmen können.

    3. Definieren Sie alle verbleibenden erforderlichen Werte.

    4. Wählen Sie **Bereich hinzufügen aus.**

    Wählen Sie oben **Speichern** aus, um die Änderungen zu speichern.

10. Wählen Sie weiterhin auf der Seite **eine API verfügbar machen** im Bereich **autorisierte Clientanwendungen** die Option **Clientanwendung hinzufügen**aus.

    In der neuen Clientanwendung:

    1. Definieren Sie die Client-ID als **d3590ed6-52b3-4102-Aeff-aad2292ab01c**. Dieser Wert ist die Microsoft Office-Client-ID und ermöglicht Office das Abrufen eines Zugriffstokens für den Schlüsselspeicher.

    2. Wählen Sie unter **autorisierte Bereiche**den **user_impersonation** Bereich aus.

    3. Wählen Sie **Anwendung hinzufügen** aus.

    4. Wählen Sie oben **Speichern** aus, um die Änderungen zu speichern.

Ihr DKE-Schlüsselspeicher ist jetzt registriert. Fahren Sie mit dem [Erstellen von Beschriftungen mithilfe von DKE](#create-labels-using-dke)fort.

## <a name="create-labels-using-dke"></a>Erstellen von Beschriftungen mithilfe von DKE

Erstellen Sie im Microsoft 365 Compliance Center eine neue Sensitivitäts Bezeichnung, und wenden Sie die Verschlüsselung wie sonst an. Wählen Sie **Doppelschlüssel Verschlüsselung verwenden** aus, und geben Sie die Endpunkt-URL für Ihren Schlüssel ein.

Beispiel:

:::image type="content" source="../media/dke-use-dke.png" alt-text="Wählen Sie Doppelschlüssel Verschlüsselung im Microsoft 365 Compliance Center verwenden aus.":::

Alle DKE-Bezeichnungen, die Sie hinzufügen, werden für Benutzer in den neuesten Versionen von Microsoft 365 apps for Enterprise angezeigt.

> [!NOTE]
> Es kann bis zu 24 Stunden dauern, bis die Clients mit den neuen Bezeichnungen aktualisiert werden.

### <a name="enable-dke-in-your-client"></a>Aktivieren von DKE in Ihrem Client

Wenn Ihre DKE-Beschriftungen nicht unter dem Menüband für die Vertraulichkeit in Microsoft Office angezeigt werden, ist der Client möglicherweise nicht DKE aktiviert.

Aktivieren Sie DKE für Ihren Client, indem Sie die folgenden Registrierungsschlüssel hinzufügen:

```ini
    [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
    "DoubleKeyProtection"=dword:00000001

    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
    "DoubleKeyProtection"=dword:00000001
```