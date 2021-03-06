---
title: Entfernen eines ehemaligen Mitarbeiters
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 44d96212-4d90-4027-9aa9-a95eddb367d1
description: 'Führen Sie diese Prüfliste aus, um einen Mitarbeiter aus Microsoft 365 zu entfernen und Daten zu sichern. '
ms.openlocfilehash: 252442c36fd29b816626adb71b3ae38ae66f1f64
ms.sourcegitcommit: 25afc0c34edc7f8a5eb389d8c701175256c58ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "47324524"
---
# <a name="remove-or-delete-a-former-employee"></a>Entfernen oder Löschen eines ehemaligen Mitarbeiters

::: moniker range="o365-21vianet"

> [!NOTE]
> Das Admin Center wird geändert. Wenn Ihre Erfahrung nicht den hier aufgeführten Details entspricht, lesen Sie [über das neue Microsoft 365 Admin Center](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end
  
## <a name="sign-out-now"></a>Sofortiges Abmelden

::: moniker range="o365-worldwide"

Sehen Sie sich ein kurzes Video zum Entfernen eines Mitarbeiters an. <br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR] 

Wenn Sie dieses Video hilfreich fanden, sehen Sie sich bitte die [komplette Schulungsserie für kleine Unternehmen und diejenigen, für die Microsoft 365 neu ist](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816) an.

So verhindern Sie, dass ein Mitarbeiter sich anmeldet:

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive Benutzer</a>.
2. Aktivieren Sie das Kontrollkästchen neben dem Namen des Benutzers, und wählen Sie dann **Kennwort zurücksetzen**aus.
3. Geben Sie ein neues Kennwort ein, und wählen Sie dann **Zurücksetzen**aus. (Senden Sie es nicht an Sie.)
4. Wählen Sie den Namen des Benutzers aus, um den Eigenschaftenbereich zu öffnen, und wählen Sie auf der Registerkarte **Konto** die Option **Abmelden initiieren**aus.

::: moniker-end

::: moniker range="o365-germany"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Benutzer aus, und wählen Sie dann **Kennwort zurücksetzen**aus.

3. Geben Sie ein neues Kennwort ein, und wählen Sie dann **Zurücksetzen**aus. (Senden Sie es nicht an Sie.)

4. Wählen Sie den Namen des Benutzers aus, um den Eigenschaftenbereich zu öffnen, und wählen Sie auf der Registerkarte **Konto** die Option **Abmelden initiieren**aus.

::: moniker-end

::: moniker range="o365-21vianet"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Benutzer aus, und wählen Sie dann **Kennwort zurücksetzen**aus.

3. Geben Sie ein neues Kennwort ein, und wählen Sie dann **Zurücksetzen**aus. (Senden Sie es nicht an Sie.)

4. Wählen Sie den Namen des Benutzers aus, um den Eigenschaftenbereich zu öffnen, und wählen Sie auf der Registerkarte **Konto** die Option **Abmelden initiieren**aus.

::: moniker-end

> [!NOTE]
> Sie müssen ein globaler Administrator sein, um die Abmeldung zu initiieren.

Innerhalb einer Stunde-oder nachdem Sie die aktuelle Microsoft 365-Seite verlassen haben-werden Sie aufgefordert, sich erneut anzumelden. Ein Zugriffstoken ist für eine Stunde gut, sodass die Zeitachse davon abhängt, wie viel Zeit auf diesem Token bleibt und ob Sie aus Ihrer aktuellen Webseite navigieren.
  
> [!IMPORTANT]
> Wenn sich der Benutzer in Outlook im Internet befindet und nur in seinem Postfach klickt, wird er möglicherweise nicht sofort gestartet. Sobald Sie eine andere Kachel wie OneDrive auswählen oder Ihren Browser aktualisieren, wird die Abmeldung initiiert.
  
Wenn Sie PowerShell verwenden möchten, um einen Benutzer sofort abzumelden, lesen Sie den Artikel über das Cmdlet [Revoke-AzureADUserAllRefreshToken](https://go.microsoft.com/fwlink/?linkid=841345).
  
Weitere Informationen dazu, wie lange es dauert, für jemand die E-Mail-Nutzung zu beenden, finden Sie unter [Wichtige Informationen zum Beenden der E-Mail-Sitzung eines Mitarbeiters](#what-you-need-to-know-about-terminating-an-employees-email-session).
  
## <a name="overview-of-all-the-steps-to-remove-an-employee-and-secure-data"></a>Übersicht über alle Schritte zum Entfernen eines Mitarbeiters und Sichern der Daten

Eine Frage, die wir häufig erhalten, lautet: "Was muss ich tun, um Daten zu schützen, wenn ein Mitarbeiter die Organisation verlässt?" In diesem Artikel wird erläutert, wie Sie den Zugriff auf Microsoft 365 und die erforderlichen Schritte zum Sichern Ihrer Daten blockieren können.
  
> [!NOTE]
> Wenn Sie ein globaler Administrator sind, können Sie den Mitarbeiter löschen, seine e-Mail weiterleiten und auswählen, was mit dem OneDrive-Inhalt zu tun ist, indem Sie die neue geführte Benutzeroberfläche verwenden. Weitere Informationen finden Sie unter [globaler Administrator: Löschen eines Benutzers](remove-former-employee.md). Es wird jedoch empfohlen, alle hier aufgelisteten zusätzlichen Schritte abzuschließen, um sicherzustellen, dass der Mitarbeiter keinen Zugriff auf die Daten Ihres Unternehmens hat. 
  
Hier folgt eine kurze Übersicht. Die einzelnen Schritte werden in diesem Artikel ausführlich erläutert.
  
|||
|:-----|:-----|
|**Schritt** <br/> |**Zweck** <br/> |
|1. [Speichern der Inhalte des Postfachs eines ehemaligen Mitarbeiters](#save-the-contents-of-a-former-employees-mailbox) <br/> |Dies ist nützlich für die Person, die die Arbeit des Mitarbeiters übernimmt, oder wenn ein Rechtsstreit vorliegt.  <br/> |
|2. [Weiterleiten der E-Mails eines ehemaligen Mitarbeiters an einen anderen Mitarbeiter oder Konvertieren des Benutzerpostfachs in ein freigegebenes Postfach](#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox) <br/> |Damit sorgen Sie dafür, dass die E-Mail-Adresse des ehemaligen Mitarbeiters aktiv bleibt. Wenn Kunden oder Partner E-Mails weiterhin an diese Adresse senden, werden sie hierdurch an die Person geleitet, die dessen Arbeit übernimmt.  <br/> |
|3. [Zurücksetzen und Blockieren des mobilen Geräts eines ehemaligen Mitarbeiters](#wipe-and-block-a-former-employees-mobile-device) <br/> |Entfernt die Geschäftsdaten vom Smartphone oder Tablet.  <br/> |
|4. [Blockieren des Zugriffs eines ehemaligen Mitarbeiters auf Microsoft 365-Daten](#block-a-former-employees-access-to-microsoft-365-data)<br/> |Dadurch wird verhindert, dass die Person auf Ihr altes Microsoft 365-Postfach und Ihre Daten zugreift.  <br/><br/> **Tipp**: Wenn Sie den Zugriff eines Benutzers blockieren, bezahlen Sie weiterhin für Ihre Lizenz. Um das bezahlen zu beenden, löschen Sie die Lizenz aus Ihrem Abonnement (Schritt 5).  |
|5. [Verschieben des OneDrive-Inhalts eines Mitarbeiters](get-access-to-and-back-up-a-former-user-s-data.md) <br/> |Wenn Sie nur die Lizenz eines Benutzers entfernen, aber das Konto nicht löschen, können Sie auch nach mehr als 30 Tagen auf den OneDrive-Inhalt des Benutzers zugreifen.  <br/><br/> Bevor Sie das Konto löschen, sollten Sie den seinen OneDrive-Inhalt an einen anderen Speicherort verschieben, auf den Sie einfach zugreifen können. Nachdem Sie das Konto eines Mitarbeiters gelöscht haben, wird der Inhalt auf seinem OneDrive **30** Tage lang beibehalten. Während dieser Zeit können Sie das Konto des Benutzers jedoch wiederherstellen und auf den OneDrive-Inhalte zugreifen. Wenn Sie das Konto des Benutzers wiederherstellen, können Sie auch nach diesen 30 Tagen auf den OneDrive-Inhalt zugreifen.  <br/> |
|5a. Was passiert, wenn ein Benutzer mit seinem privaten PC auf OneDrive oder SharePoint zugegriffen hat?  <br/> |Wenn er anstelle eines vom Unternehmen bereitgestellten Computers seinen privaten PC zum Herunterladen von Dateien aus OneDrive und SharePoint verwendet hat, haben Sie keine Möglichkeit, die dort gespeicherten Dateien zu bereinigen.  <br/><br/> Sie haben weiterhin Zugriff auf alle Dateien, die mit Ihrem Computer synchronisiert wurden.  <br/> |
|6. [Entfernen und löschen Sie die Microsoft 365-Lizenz von einem ehemaligen Mitarbeiter](#remove-and-delete-the-microsoft-365-license-from-a-former-employee)<br/> |Wenn Sie eine Lizenz entfernen, können Sie sie einem anderen Benutzer zuweisen. Sie können die Lizenz auch löschen, damit Sie erst dann wieder dafür bezahlen, wenn Sie eine andere Person einstellen.  <br/><br/> Wenn Sie eine Lizenz entfernen oder löschen, werden die alten E-Mails, Kontakte und Kalender des Benutzers für **30 Tage** gespeichert und anschließend dauerhaft gelöscht. Wenn Sie eine Lizenz entfernen oder löschen, aber das Konto nicht löschen, können Sie auch nach mehr als 30 Tagen auf den OneDrive-Inhalt des Benutzers zugreifen.  <br/> |
|7. [Löschen des Benutzerkontos eines ehemaligen Mitarbeiters](#delete-a-former-employees-user-account)<br/> |Dadurch wird das Konto aus Ihrem Admin Center entfernt. So behalten Sie die Übersicht.  <br/> |

## <a name="save-the-contents-of-a-former-employees-mailbox"></a>Speichern der Inhalte des Postfachs eines ehemaligen Mitarbeiters

Es gibt zwei Möglichkeiten, wie Sie die Inhalte des Postfachs eines ehemaligen Mitarbeiters speichern können:
  
1. Sie fügen die E-Mail-Adresse des ehemaligen Mitarbeiters zu Ihrer Version von Outlook 2013 oder 2016 hinzu und exportieren dann die Daten in eine PST-Datei. Sie können die Daten bei Bedarf in ein anderes E-Mail-Konto importieren. Informationen dazu finden Sie unter [Zugreifen auf die und Sichern der Daten eines ehemaligen Mitarbeiters](get-access-to-and-back-up-a-former-user-s-data.md).

    ODER

2. Sie aktivieren vor dem Löschen des Benutzerkontos ein Beweissicherungsverfahren oder einen In-Situ-Speicher für das Postfach. Diese Option ist viel komplizierter als die erste, sie ist jedoch sinnvoll, wenn Ihr Enterprise-Plan die Archivierung und gesetzliche Aufbewahrungspflicht umfasst, die Möglichkeit besteht, in Rechtsstreitigkeiten zu geraten, und Sie über eine wirklich gute IT-Abteilung verfügen.

    Nachdem Sie das Postfach in ein inaktives Postfach konvertiert haben, können Administratoren, Compliance Officer oder Records Manager in-Place-eDiscovery-Tools in Exchange Online verwenden, um auf den Inhalt zuzugreifen und diese zu durchsuchen.

    Inaktive Postfächer können keine E-Mails empfangen und werden im freigegebenen Adressbuch Ihrer Organisation oder in anderen Listen nicht angezeigt.

    Informationen zum Aufbewahren eines Postfachs finden Sie unter [Manage inactive Mailboxes in Exchange Online](https://docs.microsoft.com/microsoft-365/compliance/create-and-manage-inactive-mailboxes).

## <a name="forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox"></a>Weiterleiten der E-Mails eines ehemaligen Mitarbeiters an einen anderen Mitarbeiter oder Konvertieren des Benutzerpostfachs in ein freigegebenes Postfach

In diesem Schritt weisen Sie die E-Mail-Adresse des ehemaligen Mitarbeiters einem anderen Mitarbeiter zu, oder Sie [konvertieren das Postfach des Benutzers in ein freigegebenes Postfach](../email/convert-user-mailbox-to-shared-mailbox.md), das Sie erstellt haben.
  
- Das Erstellen eines freigegebenen Postfachs ist die kostengünstigere Methode, weil Sie für keine Lizenz bezahlen müssen, **solange das Postfach kleiner als 50 GB ist**. Bei über 50 GB müssen Sie dem Postfach eine Lizenz zuweisen.
- Wenn Sie das Postfach in ein freigegebenes Postfach konvertieren, stehen auch alle alten E-Mails zur Verfügung. Dadurch kann eine Menge an Speicherplatz belegt werden.
- Wenn Sie die E-Mail-Weiterleitung eingerichtet haben, werden nur  *neue*  an den ehemaligen Mitarbeiter gesendeten E-Mails jetzt an den aktuellen Mitarbeiter gesendet.
- Bei der E-Mail-Weiterleitung muss das Konto des ehemaligen Mitarbeiters über eine Lizenz verfügen.

 > [!IMPORTANT]
 > Wenn Sie e-Mail-Weiterleitung oder ein freigegebenes Postfach einrichten, löschen Sie am Ende nicht das Konto des ehemaligen Mitarbeiters. Es muss nämlich vorhanden sein, damit die E-Mail-Weiterleitung oder das freigegebene Postfach funktionieren.

::: moniker range="o365-worldwide"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive Benutzer</a>.
2. Wählen Sie den Namen des Mitarbeiters aus, den Sie blockieren möchten, und wählen Sie dann die Registerkarte **e-Mail** aus.
3. Wählen Sie unter **e-Mail-weiter**Leitung die Option **e-Mail Weiterleitung verwalten**aus.
4. Aktivieren Sie **Alle an dieses Postfach gesendeten E-Mails weiterleiten**. Geben Sie im Feld **Weiterleitungsadresse** die E-Mail-Adresse des aktuellen Mitarbeiters (oder des freigegebenen Postfachs) ein, an den (oder das) die E-Mails weitergeleitet werden sollen.
5. Klicken Sie auf **Speichern**.
6. Denken Sie daran, dass das Konto des ehemaligen Mitarbeiters nicht gelöscht werden sollte.

::: moniker-end

::: moniker range="o365-germany"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Mitarbeiter aus, den Sie blockieren möchten, und erweitern Sie **e-Mail-Einstellungen**.

3. Wählen Sie neben **e-Mail-Weiterleitung**die Option **Bearbeiten**aus.

4. Aktivieren Sie **Alle an dieses Postfach gesendeten E-Mails weiterleiten**. Geben Sie im Feld **Weiterleitungsadresse** die E-Mail-Adresse des aktuellen Mitarbeiters (oder des freigegebenen Postfachs) ein, an den (oder das) die E-Mails weitergeleitet werden sollen.
  
5. Klicken Sie auf **Speichern**.

6. Denken Sie daran, dass das Konto des ehemaligen Mitarbeiters nicht gelöscht werden sollte.

::: moniker-end

::: moniker range="o365-21vianet"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Mitarbeiter aus, den Sie blockieren möchten, und erweitern Sie **e-Mail-Einstellungen**.

3. Wählen Sie neben **e-Mail-Weiterleitung**die Option **Bearbeiten**aus.

4. Aktivieren Sie **Alle an dieses Postfach gesendeten E-Mails weiterleiten**. Geben Sie im Feld **Weiterleitungsadresse** die E-Mail-Adresse des aktuellen Mitarbeiters (oder des freigegebenen Postfachs) ein, an den (oder das) die E-Mails weitergeleitet werden sollen.
  
5. Klicken Sie auf **Speichern**.

6. Denken Sie daran, dass das Konto des ehemaligen Mitarbeiters nicht gelöscht werden sollte.

::: moniker-end

## <a name="wipe-and-block-a-former-employees-mobile-device"></a>Zurücksetzen und Blockieren des mobilen Geräts eines ehemaligen Mitarbeiters

Wenn Ihr ehemaliger Mitarbeiter ein Organisations Telefon besaß, können Sie das Gerät mithilfe der Exchange-Verwaltungskonsole abwischen und blockieren, sodass alle Organisationsdaten aus dem Gerät entfernt werden und keine Verbindung mehr mit Office 365 hergestellt werden kann.

1. Wechseln Sie zum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Admin Center</a>.
2. Navigieren Sie im Exchange Admin Center zu **Empfänger** \> **Postfächer**.
3. Wählen Sie den Benutzer aus, und wählen Sie unter **Mobile Geräte**die Option **Details anzeigen**aus.
4. Wählen Sie auf der Seite **Details für mobile Geräte** unter **Mobile Geräte**das Mobile Gerät aus, wählen Sie Daten Zurücksetzungs Gerät **wischen**aus ![ ](../../media/1c113a36-53cb-4974-884f-3ecd9535506e.png) , und wählen Sie dann **blockieren**aus.
5. Klicken Sie auf **Speichern**.
   > [!TIP]
   > Stellen Sie sicher, dass Sie den Benutzer aus Ihrem lokalen BlackBerry Enterprise-Dienst entfernen oder deaktivieren. Sie sollten auch alle BlackBerry-Geräte für den Benutzer deaktivieren. Lesen Sie den Abschnitt BlackBerry Business Cloud Services Administration Guide, wenn Sie bestimmte Schritte zum Deaktivieren des Benutzers benötigen.

## <a name="block-a-former-employees-access-to-microsoft-365-data"></a>Blockieren des Zugriffs eines ehemaligen Mitarbeiters auf Microsoft 365-Daten

 > [!IMPORTANT]
 > Das Blockieren eines Kontos kann bis zu 24 Stunden dauern, bis es wirksam wird. Wenn Sie den Anmeldezugriff eines Benutzers sofort verhindern müssen, sollten Sie [Ihr Kennwort zurücksetzen](reset-passwords.md) und dann ein einmaliges Ereignis initiieren, das Sie von Microsoft 365-Sitzungen auf allen Geräten signieren wird. Weitere Informationen finden Sie unter [Sofortiges Abmelden](#sign-out-now).

::: moniker range="o365-worldwide"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive Benutzer</a>.
2. Wählen Sie den Namen des Mitarbeiters aus, den Sie blockieren möchten, und wählen Sie unter dem Namen des Benutzers das Symbol für **diesen Benutzer blockieren**aus.
3. Wählen Sie **blockieren Sie den Benutzer für die Anmeldung aus**, und wählen Sie dann **Speichern**aus.

::: moniker-end

::: moniker range="o365-germany"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Mitarbeiter aus, den Sie blockieren möchten, und wählen Sie dann **Anmeldung blockieren**aus.

3. Wählen Sie **blockieren Sie den Benutzer für die Anmeldung aus**, und wählen Sie dann **Speichern**aus.

::: moniker-end

::: moniker range="o365-21vianet"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Mitarbeiter aus, den Sie blockieren möchten, und wählen Sie dann **Anmeldung blockieren**aus.

3. Wählen Sie **blockieren Sie den Benutzer für die Anmeldung aus**, und wählen Sie dann **Speichern**aus.

::: moniker-end

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Blockieren des Zugriffs eines ehemaligen Mitarbeiters auf E-Mail (Exchange Online)

Wenn Sie über e-Mail als Teil Ihres Microsoft 365-Abonnements verfügen, müssen Sie sich beim Exchange Admin Center anmelden, um die folgenden Schritte durchführen, um zu verhindern, dass Ihr ehemaliger Mitarbeiter auf seine e-Mail zugreift.
  
1. Wechseln Sie zum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Admin Center</a>.
2. Navigieren Sie im Exchange Admin Center zu **Empfänger** \> **Postfächer**.
3. Doppelklicken Sie auf den Benutzer, und wechseln Sie zur Seite **Postfachfeatures** . Wählen Sie unter **Mobile Geräte**die Option **Exchange ActiveSync deaktivieren** aus **, und deaktivieren Sie OWA für mobile Geräte,** und beantworten Sie beide bei der entsprechenden Aufforderung mit **Ja** .
4. Wählen Sie unter **e-Mail-Konnektivität**die Option **Deaktivieren** und **Ja** beantworten, wenn Sie dazu aufgefordert werden.

## <a name="remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>Entfernen und Löschen der Microsoft 365-Lizenz von einem ehemaligen Mitarbeiter

Damit Sie nicht weiterhin für eine Lizenz bezahlen, nachdem jemand Ihre Organisation verlassen hat, müssen Sie Ihre Microsoft 365-Lizenz entfernen und dann aus Ihrem Abonnement löschen. Wenn Sie die Lizenz nicht aus Ihrem Abonnement löschen möchten, können Sie sie einem anderen Benutzer zuweisen.
  
Wenn Sie die Lizenz entfernen, werden alle Daten des Benutzers noch 30 Tage gespeichert. Sie können auf die Daten [zugreifen](get-access-to-and-back-up-a-former-user-s-data.md) oder das Konto [wiederherstellen](restore-user.md), wenn der Benutzer zurückkehrt. Nach 30 Tagen werden alle Daten des Benutzers (mit Ausnahme der in SharePoint Online gespeicherten Dokumente) dauerhaft aus Microsoft 365 gelöscht und können nicht wiederhergestellt werden.

::: moniker range="o365-worldwide"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive Benutzer</a>.
2. Wählen Sie den Namen des Mitarbeiters aus, den Sie blockieren möchten, und wählen Sie dann die Registerkarte **Lizenzen und apps** aus.
3. Deaktivieren Sie die Kontrollkästchen für die zu entfernenden Lizenzen, und wählen Sie dann **Änderungen speichern**aus.

::: moniker-end

::: moniker range="o365-germany"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Mitarbeiter aus, den Sie blockieren möchten, und wählen Sie dann neben **Produktlizenzen**die Option **Bearbeiten**aus.

3. Deaktivieren Sie auf der Seite **Produktlizenzen** die zu entfernenden Lizenzen, und wählen Sie dann **Speichern**aus.

::: moniker-end

::: moniker range="o365-21vianet"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Mitarbeiter aus, den Sie blockieren möchten, und wählen Sie dann neben **Produktlizenzen**die Option **Bearbeiten**aus.

3. Deaktivieren Sie auf der Seite **Produktlizenzen** die zu entfernenden Lizenzen, und wählen Sie dann **Speichern**aus.

::: moniker-end

Führen Sie die folgenden Schritte aus **, um die Anzahl der von Ihnen bezahlten Lizenzen zu reduzieren** , bis Sie eine andere Person einstellen:

::: moniker range="o365-worldwide"
1. Wechseln Sie im Admin Center zur Seite **Fakturierung** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">ihrer Produkte</a> , und wählen Sie die Registerkarte **Produkte** aus.
2. Wählen Sie das Abonnement aus, aus dem Sie Lizenzen entfernen möchten.
3. Wählen Sie auf der Seite Details die Option **Lizenzen entfernen**aus.
4. Geben Sie im Bereich **Lizenzen entfernen** unter neue Menge im Feld **Gesamt Lizenzen** die Gesamtzahl der Lizenzen ein, die Sie für dieses Abonnement benötigen. Wenn Sie beispielsweise 25 Lizenzen haben und eine davon entfernen möchten, geben Sie 24 ein.
5. Klicken Sie auf **Speichern**.
::: moniker-end

::: moniker range="o365-germany"
1. Navigieren Sie im Admin Center zur Seite **Abrechnung** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a>.
2. Wählen Sie **Lizenzen hinzufügen/entfernen** aus, um die Lizenz zu löschen, damit Sie Sie erst dann bezahlen, wenn Sie eine andere Person einstellen.
::: moniker-end

::: moniker range="o365-21vianet"
1. Navigieren Sie im Admin Center zur Seite **Abrechnung** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.
2. Wählen Sie **Lizenzen hinzufügen/entfernen** aus, um die Lizenz zu löschen, damit Sie Sie erst dann bezahlen, wenn Sie eine andere Person einstellen.
::: moniker-end

Wenn Sie [eine weitere Person](add-users.md) zu Ihrem Unternehmen hinzufügen, werden Sie aufgefordert, gleichzeitig eine Lizenz mit nur einem Schritt zu kaufen.

Weitere Informationen zum Verwalten von Benutzerlizenzen für Microsoft 365 for Business finden Sie unter [Zuweisen von Lizenzen zu Benutzern in Microsoft 365 for](../manage/assign-licenses-to-users.md)Business und Aufheben der [Zuweisung von Lizenzen von Benutzern in Microsoft 365 for Business](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Auswirkungen des gelöschten Mitarbeiterkontos auf Skype for Business

Wenn Sie die Lizenz eines Benutzers aus Office 365 entfernen, wird die dem Benutzer zugeordnete PSTN Calling-Nummer freigegeben. Sie können sie dann einem anderen Benutzer zuweisen.
  
Wenn der Benutzer einer Warteschlangengruppe angehört, ist er kein erreichbares Ziel der Anrufwarteschlangen-Agents mehr. Deshalb empfiehlt es sich, den Benutzer auch aus den Gruppen zu entfernen, die der Anrufwarteschlange zugeordnet sind.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Einrichten der Anrufweiterleitung für Personen in Ihrer Organisation

Wenn Sie die Anrufweiterleitung für die Telefonnummer des terminierten Mitarbeiters einrichten müssen, kann die Einstellung für die Anrufweiterleitung unter Anruf Richtlinien eine Weiterleitung einrichten, in der eingehende Anrufe an andere Benutzer weitergeleitet werden können, oder die eine andere Person gleichzeitig anrufen können. Weitere Informationen finden Sie unter [Calling Policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-calling-policy).
  
## <a name="delete-a-former-employees-user-account"></a>Löschen des Benutzerkontos eines ehemaligen Mitarbeiters

Nachdem Sie auf alle Benutzerdaten des ehemaligen Mitarbeiters zugegriffen und diese gespeichert haben, können Sie das Konto des ehemaligen Mitarbeiters löschen.
  
Löschen Sie das Konto nicht, wenn Sie eine E-Mail-Weiterleitung eingerichtet oder das Konto in ein freigegebenes Postfach konvertiert haben. Für beide Funktionen wird das Konto benötigt, damit die Weiterleitung oder Postfachfreigabe funktioniert.

::: moniker range="o365-worldwide"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive Benutzer</a>.
2. Wählen Sie den Namen des Mitarbeiters aus, den Sie löschen möchten.
3. Wählen Sie unter dem Namen des Benutzers das Symbol für **Delete User**aus. Wählen Sie die gewünschten Optionen für diesen Benutzer aus, und wählen Sie dann **Benutzer löschen**aus.

::: moniker-end

::: moniker range="o365-germany"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Namen des Mitarbeiters aus, den Sie löschen möchten.

3. Wählen Sie oben auf der Seite **Benutzer löschen**aus. Wählen Sie die gewünschten Optionen für diesen Benutzer aus, und wählen Sie dann **Benutzer löschen**aus.

::: moniker-end

::: moniker range="o365-21vianet"

1. Wechseln Sie im Admin Center zu der Seite **Benutzer** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive Benutzer</a>.

2. Wählen Sie den Namen des Mitarbeiters aus, den Sie löschen möchten.

3. Wählen Sie oben auf der Seite **Benutzer löschen**aus. Wählen Sie die gewünschten Optionen für diesen Benutzer aus, und wählen Sie dann **Benutzer löschen**aus.

::: moniker-end

Wenn Sie einen Benutzer löschen, wird das Konto ungefähr 30 Tage lang deaktiviert (inaktiv). Sie haben in dieser Zeit noch die Möglichkeit, das Konto wiederherzustellen, bevor es endgültig gelöscht wird.
  
### <a name="does-your-organization-use-active-directory"></a>Verwendet Ihre Organisation Active Directory?

Wenn Ihre Organisation Benutzerkonten mit Microsoft 365 aus einer lokalen Active Directory Umgebung synchronisiert, müssen Sie diese Benutzerkonten in Ihrem lokalen Active Directory Dienst löschen und wiederherstellen. Sie können sie nicht in Office 365 löschen und wiederherstellen.
  
Informationen zum Löschen und Wiederherstellen von Benutzerkonten in Active Directory finden Sie unter [Löschen eines Benutzerkontos](https://go.microsoft.com/fwlink/?linkid=841808).
  
Wenn Sie Azure Active Directory verwenden, lesen Sie das PowerShell [-Cmdlet Remove-MsolUser](https://go.microsoft.com/fwlink/?linkid=842230) .
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>Wichtige Informationen zum Beenden der E-Mail-Sitzung eines Mitarbeiters

Hier finden Sie Informationen dazu, wie Sie die E-Mail-Nutzung für einen Mitarbeiter beenden können (Exchange).
  
|||
|:-----|:-----|
|**Mögliche Aktionen** <br/> |**Wie geht das?** <br/> |
|Sitzung beenden (z. B. Outlook im Web, Outlook, Exchange Active Sync usw.) und Öffnen einer neuen Sitzung erzwingen  <br/> |Kennwort zurücksetzen  <br/> |
|Sitzung beenden und Zugriff auf zukünftige Sitzungen (für alle Protokolle) sperren  <br/> |Deaktivieren Sie das Konto. Beispielsweise (im Exchange Admin Center oder mithilfe von PowerShell):  <br/>  `Set-Mailbox user@contoso.com -AccountDisabled:$true` <br/> |
|Sitzung für ein bestimmtes Protokoll (z. B. ActiveSync) beenden  <br/> |Deaktivieren Sie das Protokoll. Beispielsweise (im Exchange Admin Center oder mithilfe von PowerShell):  <br/>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false` <br/> |

Die obigen Vorgänge können an drei Stellen ausgeführt werden:
  
|||
|:-----|:-----|
|**Ort zum Beenden der Sitzung** <br/> |**Dauer der Maßnahme** <br/> |
|Im Exchange Admin Center oder mithilfe von PowerShell  <br/> |Voraussichtliche Verzögerung = innerhalb von 30 Minuten  <br/> |
|Azure Active Directory Admin Center  <br/> |Voraussichtliche Verzögerung = 60 Minuten  <br/> |
|Lokale Umgebung  <br/> |Voraussichtliche Verzögerung = 3 Stunden oder mehr  <br/> |

### <a name="how-to-get-fastest-response-for-account-termination"></a>So erhalten Sie eine schnelle Reaktion auf die Kündigung eines Kontos

 **Schnellste Option**: Verwenden Sie das Exchange Admin Center (über PowerShell) oder das Azure Active Directory Admin Center. In einer lokalen Umgebung kann es mehrere Stunden dauern, bis die Änderung über das Azure Active Directory-Synchronisierungstool synchronisiert wurde.
  
 **Schnellste Option für einen Benutzer mit lokaler Präsenz und im Exchange-Rechenzentrum**: Beenden Sie die Sitzung über das Azure Active Directory Admin Center bzw. das Exchange Admin Center, UND führen Sie die Änderung auch in der lokalen Umgebung auch. Andernfalls wird die Änderung im Azure Active Directory Admin Center bzw. Exchange Admin Center durch DirSync überschrieben.
  
## <a name="related-articles"></a>Verwandte Artikel

[Wiederherstellen eines Benutzers](restore-user.md)