---
title: Kunden-Lockbox-Anforderungen
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
search.appverid:
- BCS160
- MET150
- MOE150
description: Erfahren Sie mehr über Kunden Lockbox-Anforderungen, mit denen Sie steuern können, wie ein Microsoft-Supporttechniker auf Ihre Daten zugreifen kann, wenn Sie auf ein Problem stoßen.
ms.openlocfilehash: d71fbaa42fba49bd0f06b26d34d2257f8a4a60ba
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "47546501"
---
# <a name="customer-lockbox-in-office-365"></a>Kunden-Lockbox in Office 365

Dieser Artikel enthält Anleitungen zur Bereitstellung und Konfiguration für Kunden-Lockbox. Kunden-Lockbox unterstützt Anforderungen für den Zugriff auf Daten in Exchange Online, SharePoint Online und OneDrive für Unternehmen. Um die Unterstützung für andere Dienste zu empfehlen, senden Sie eine Anfrage an [Office 365 UserVoice](https://office365.uservoice.com/).

Informationen zu den Optionen für die Lizenzierung von Benutzern, die von den Microsoft 365-Kompatibilitäts Angeboten profitieren, einschließlich dieses, ab dem 1. April 2020, finden Sie in der [Microsoft 365-Lizenzierungs Anleitung zur Sicherheit & Compliance](https://aka.ms/ComplianceSD).

Kunden-Lockbox stellt sicher, dass Microsoft nicht auf Ihre Inhalte zugreifen kann, um einen Dienstvorgang ohne Ihre ausdrückliche Genehmigung auszuführen. Kunden-Lockbox bringt Sie in den Genehmigungsworkflow für Anforderungen für den Zugriff auf Ihre Inhalte.

Gelegentlich helfen Microsoft-Ingenieure bei der Problembehandlung und beim Beheben von vom Kunden gemeldeten Problemen im Support Prozess. In der Regel werden Probleme durch umfangreiche Telemetrie-und Debugging-Tools behoben, die Microsoft für seine Dienste implementiert hat. In einigen Fällen ist es jedoch erforderlich, dass ein Microsoft-Techniker auf Kunden Inhalte zugreift, um die Ursache zu ermitteln und das Problem zu beheben. Kunden-Lockbox setzt voraus, dass der Techniker den Zugriff vom Kunden als letzten Schritt im Genehmigungsworkflow anfordert. Dadurch erhalten Organisationen die Möglichkeit, diese Anforderungen zu genehmigen oder abzulehnen und dem Kunden eine direkte Zugriffssteuerung bereitzustellen.

### <a name="customer-lockbox-overview-video"></a>Kunden-Lockbox – Übersichtsvideo

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>Kunden-Lockbox – Genehmigungsvorgang

Die folgenden Schritte beschreiben den typischen Workflow, wenn ein Microsoft-Techniker eine Kunden-Lockbox-Anforderung initiiert:

1. Ein Benutzer in einer Organisation hat ein Problem mit seinem Microsoft 365-Postfach.

2. Nachdem der Benutzer das Problem behoben, aber nicht beheben kann, öffnen Sie eine Supportanfrage mit dem Microsoft-Support.

3. Ein Microsoft-Supporttechniker überprüft die Dienstanforderung und legt fest, dass auf den Mandanten der Organisation zugegriffen werden muss, um das Problem in Exchange Online zu beheben.

4. Der Microsoft-Supporttechniker meldet sich beim Kunden Lockbox-Anforderungs Tool an und erstellt eine Datenzugriffsanforderung, die den Mandantennamen, die Dienstanforderungsnummer und die geschätzte Zeit, die der Techniker auf die Daten zugreifen muss, enthält.

5. Nachdem die Anforderung von einem Microsoft-Support-Mitarbeiter genehmigt wurde, sendet die Kunden-Lockbox der für die Genehmigung zuständigen Person in der Organisation eine E-Mail-Benachrichtigung über die ausstehende Zugriffsanforderung von Microsoft.

    ![Beispiel für eine Kunden-Lockbox-e-Mail-Benachrichtigung](../media/CustomerLockbox1.png)

   Jeder Benutzer, dem die Administratorrolle " [Customer Lockbox Access genehmigende](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles) Person" im Microsoft 365 Admin Center zugewiesen ist, kann Kunden-Lockbox-Anforderungen genehmigen.

6. Die genehmigende Person meldet sich beim Microsoft 365 Admin Center an und genehmigt die Anforderung. Mit diesem Schritt wird die Erstellung eines Überwachungseintrags ausgelöst, der über eine Suche innerhalb des Überwachungsprotokolls auffindbar ist. Weitere Informationen finden Sie unter [Auditing Customer Lockbox Requests](#auditing-customer-lockbox-requests).

   Wenn der Kunde die Anforderung ablehnt oder die Anforderung nicht innerhalb von 12 Stunden genehmigt, läuft die Anforderung ab, und dem Microsoft-Techniker wird kein Zugriff gewährt.

   > [!IMPORTANT]
   > Microsoft schließt keine Links in die Kunden-Lockbox-e-Mail-Benachrichtigungen ein, bei denen Sie sich bei Office 365 anmelden müssen.

7. Nachdem die genehmigende Person der Organisation die Anforderung genehmigt hat, erhält der Microsoft-Techniker die entsprechende Genehmigungsnachricht, meldet sich beim Mandanten in Exchange Online an und behebt das Problem des Kunden. Microsoft-Techniker haben die angeforderte Dauer, um das Problem zu beheben, nach dem der Zugriff automatisch aufgehoben wird.

> [!NOTE]
> Sämtliche von einem Microsoft-Techniker ausgeführten Aktionen werden im Überwachungsprotokoll protokolliert. Sie können nach diesen Überwachungseinträgen suchen und sie überprüfen.

## <a name="turn-customer-lockbox-requests-on-or-off"></a>Aktivieren oder Deaktivieren von Kunden-Lockbox-Anforderungen

Sie können die Steuerelemente für die Kunden-Lockbox im Microsoft 365 Admin Center aktivieren. Wenn Sie die Kunden-Lockbox aktivieren, muss Microsoft die Zustimmung Ihrer Organisation erhalten, bevor Sie auf den Inhalt Ihres Mandanten zugreifen können.

1. Wechseln Sie zu und melden Sie sich mit einem Arbeits-oder Schulkonto an, dem der globale Administrator oder die **Customer Lockbox Access-genehmigende** Rolle zugewiesen ist [https://admin.microsoft.com](https://admin.microsoft.com) .

2. Wählen Sie **Einstellungen > org-Einstellungen**aus.

3. Wählen Sie **Services**  >  **Customer Lockbox**  >  **Edit**aus, und bewegen Sie die Umschaltfläche in **ein** oder **aus** , um das Feature ein-oder auszuschalten.

    ![Require approval for Customer Lockbox](../media/CustomerLockbox4.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>Genehmigen oder Ablehnen einer Kunden-Lockbox-Anforderung

1. Wechseln Sie zu und melden Sie sich mit einem Arbeits-oder Schulkonto an, dem der globale Administrator oder die **Customer Lockbox Access-genehmigende** Rolle zugewiesen ist [https://admin.microsoft.com](https://admin.microsoft.com) .

2. Wählen Sie **Support > Kunden-Lockbox-Anforderungen**aus.

    ![Klicken Sie auf Support und dann auf Kunden-Lockbox-Anforderungen.](../media/CustomerLockbox5.png)

    Eine Liste der Kunden-Lockbox-Anforderungen wird angezeigt.

    ![Liste der Kunden-Lockbox-Anforderungen](../media/CustomerLockbox6.png)

3. Wählen Sie eine Kunden-Lockbox-Anforderung aus, und klicken Sie dann auf **genehmigen** oder **verweigern**.

    ![Genehmigen oder Verweigern von Kunden-Lockbox-Anforderungen](../media/CustomerLockbox7.png)

    Eine Bestätigungsmeldung zur Genehmigung der Kunden-Lockbox-Anforderung wird angezeigt.

    ![Genehmigen oder Verweigern von Kunden-Lockbox-Anforderungen](../media/CustomerLockbox8.png)

> [!NOTE]
> Verwenden Sie das Cmdlet "AccessToCustomerDataRequest", um Microsoft 365 Kunden-Lockbox-Anfragen zu genehmigen, zu verweigern oder zu kündigen, die den Zugriff auf Ihre Daten durch Microsoft-Supporttechniker steuern. Weitere Informationen finden Sie unter [Sets-AccessToCustomerDataRequest](https://docs.microsoft.com/powershell/module/exchange/set-accesstocustomerdatarequest).


## <a name="auditing-customer-lockbox-requests"></a>Überwachung von Kunden-Lockbox-Anforderungen

Überwachungsdatensätze, die den Kunden-Lockbox-Anforderungen entsprechen, werden im Überwachungsprotokoll protokolliert. Sie können auf diese Protokolle zugreifen, indem Sie das [Überwachungsprotokoll-Such Tool](search-the-audit-log-in-security-and-compliance.md) im Security & Compliance Center verwenden. Im Überwachungsprotokoll werden auch Aktionen im Zusammenhang mit der Annahme oder Ablehnung einer Kunden-Lockbox-Anforderung und von Microsoft-Ingenieuren durchgeführten Aktionen (wenn Zugriffsanforderungen genehmigt werden) im Überwachungsprotokoll protokolliert. Sie können nach diesen Überwachungseinträgen suchen und sie überprüfen.

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>Durchsuchen des Überwachungsprotokolls nach Aktivitäten im Zusammenhang mit Kunden-Lockbox-Anforderungen

Bevor Sie das Überwachungsprotokoll zum Nachverfolgen von Anforderungen für Kunden-Lockbox verwenden können, müssen Sie einige Schritte ausführen, um die Überwachungsprotokollierung einzurichten. Weitere Informationen finden Sie unter [Durchsuchen des Überwachungsprotokolls im Security & Compliance Center](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#before-you-begin). Nachdem Sie das Setup abgeschlossen haben, führen Sie die folgenden Schritte aus, um eine Überwachungsprotokoll-Suchabfrage zu erstellen, um Überwachungseinträge im Zusammenhang mit Customer Lockbox zurückzugeben:

1. Wechseln Sie zu [https://protection.office.com](https://protection.office.com).
  
2. Melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto an.

3. Klicken Sie im linken Bereich des Security & Compliance Centers auf **Suche & Ermittlungs**  >  **Überwachungsprotokoll-Suche**.

    Die Seite **Überwachungsprotokoll Suche** wird angezeigt.

    ![Seite "Überwachungsprotokoll Suche"](../media/auditlogsearch1.png)
  
4. Konfigurieren Sie die folgenden Suchkriterien: 

    a. **Aktivitäten** : lassen Sie dieses Feld leer, damit die Suche Überwachungsdatensätze für alle Aktivitäten zurückgibt. Dies ist erforderlich, um alle Überwachungseinträge im Zusammenhang mit Kunden-Lockbox-Anforderungen und der entsprechenden von Microsoft-Ingenieuren ausgeführten Aktivitäten zurückzugeben.

    b. **Start Datum** und **Enddatum** – wählen Sie einen Datums-und Zeitbereich aus, um die Ereignisse anzuzeigen, die innerhalb dieses Zeitraums aufgetreten sind.

    c. **Benutzer** – lassen Sie dieses Feld leer.

    d. **Datei, Ordner oder Website** – lassen Sie dieses Feld leer.

5. Klicken Sie auf **Suchen**, um die Suche anhand der Suchkriterien auszuführen. 

    Die Suchergebnisse werden geladen, und nach ein paar Momenten werden Sie unter **Ergebnisse** auf der Seite **Überwachungsprotokoll Suche** angezeigt.

6. Klicken Sie auf der Suchergebnisseite auf **Filter Ergebnisse** , und führen Sie eine der folgenden Aktionen aus:

   - So zeigen Sie Überwachungseinträge im Zusammenhang mit einer genehmigenden Person in Ihrer Organisation an, die eine Kunden-Lockbox-Anforderung genehmigt oder ablehnt: Geben Sie in das Feld unter der Spalte **Aktivität** den Text **Satz-AccessToCustomerDataRequest**ein.

   - So zeigen Sie Überwachungseinträge im Zusammenhang mit einem Microsoft Engineer an, der Aktionen als Reaktion auf eine zugelassene Kunden-Lockbox-Anforderung ausführt: Geben Sie in das Feld unter der Spalte **Benutzer** den Eintrag **Microsoft-Operator**ein. In der Spalte **Aktivität** wird die vom Techniker ausgeführte Aktion angezeigt.

      ![Auf "Microsoft-Operator" filtern, um Überwachungseinträge anzuzeigen](../media/CustomerLockbox10.png)

7. Klicken Sie in der Ergebnisliste auf einen Überwachungseintrag, um ihn anzuzeigen.

### <a name="audit-record-for-a-customer-lockbox-access-request"></a>Überwachungsdatensatz für eine Kunden-Lockbox-Zugriffsanforderung

Wenn eine Person in Ihrer Organisation eine Kunden-Lockbox-Anforderung genehmigt oder ablehnt, wird im Überwachungsprotokoll ein Überwachungseintrag protokolliert. Dieser Datensatz enthält folgende Informationen.

| Überwachungsdatensatz-Eigenschaft| Beschreibung|
|:---------- |:----------|
| Datum       | Das Datum und die Uhrzeit, zu der die Kunden-Lockbox-Anforderung genehmigt oder abgelehnt wurde.
| IP-Adresse | Die IP-Adresse des Computers, den die genehmigende Person zur Genehmigung oder Ablehnung einer Anforderung verwendet hat. |
| Benutzer       | Das Dienstkonto BOXServiceAccount@ \[ customerforest \] . Prod.Outlook.com.            |
| Aktivität   | Set-AccessToCustomerDataRequest; Hierbei handelt es sich um die Überwachungsaktivität, die protokolliert wird, wenn eine Kunden-Lockbox-Anforderung genehmigt oder abgelehnt wird.                                |
| Element       | Die GUID der Kunden-Lockbox-Anforderung                             |

Der folgende Screenshot zeigt ein Beispiel für einen Überwachungsprotokolleintrag, der einer genehmigten Kunden-Lockbox-Anforderung entspricht. Wenn eine Kunden-Lockbox-Anforderung verweigert wurde, lautet der Wert des **ApprovalDecision** -Parameters **Deny**.

![Überwachungseintrag für eine zugelassene Kunden-Lockbox-Anforderung](../media/CustomerLockbox9.png)

> [!TIP]
> Wenn Sie ausführlichere Informationen in einem Überwachungseintrag anzeigen möchten, klicken Sie auf **Weitere Informationen**.

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>Überwachungsdatensatz für eine Aktion, die von einem Microsoft-Techniker ausgeführt wird

Die Aktionen, die von einem Microsoft-Techniker nach der Genehmigung einer Kunden-Lockbox-Anforderung durchgeführt werden (und die zum Zugriff auf Kundeninhalte führen können), werden im Überwachungsprotokoll protokolliert. Diese Datensätze enthalten die folgenden Informationen.

| Überwachungsdatensatz-Eigenschaft| Beschreibung|
|:---------- |:----------|
| Datum       | Datum Uhrzeit, zu der die Aktion ausgeführt wurde. Beachten Sie, dass die Uhrzeit, zu der diese Aktion durchgeführt wurde, innerhalb von 4 Stunden nach der Genehmigung der Kunden-Lockbox-Anforderung liegt.              |
| IP-Adresse | Die IP-Adresse des Computers, den der Microsoft-Techniker verwendet hat. |
| Benutzer       | Microsoft-Operator; dieser Wert gibt an, dass dieser Datensatz mit einer Kunden-Lockbox-Anforderung verknüpft ist.                                  |
| Aktivität   | Name der vom Microsoft-Techniker ausgeführten Aktivität.|
| Element       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

#### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>Auf welche Microsoft 365-Dienste wird Kunden-Lockbox angewendet?

Kunden-Lockbox wird derzeit in Exchange Online, SharePoint Online und OneDrive für Unternehmen unterstützt.

#### <a name="is-customer-lockbox-available-to-all-customers"></a>Ist die Kunden-Lockbox für alle Kunden verfügbar?

Kunden-Lockbox ist in den Microsoft 365-oder Office 365 E5-Abonnements enthalten und kann mit einem Add-on für Informationsschutz und Compliance oder mit einem Advanced Compliance-Add-on-Abonnement zu anderen Plänen hinzugefügt werden. Weitere Informationen finden Sie unter [Pläne und Preise](https://products.office.com/business/office-365-enterprise-e5-business-software)   .

#### <a name="what-is-customer-content"></a>Was sind Kunden Inhalte?

Kunden Inhalte sind die Daten, die von Benutzern von Microsoft 365-Diensten und-Anwendungen erstellt wurden. Beispiele für Kundeninhalte:

- E-Mail-Nachrichtentext oder -Anlagen

- SharePoint-Websiteinhalte

- Informationen im Textkörper einer SharePoint-Datei

- Skype for Business-Präsentationsdatei Text

- Chatnachrichten oder VoIP-Unterhaltungen

- Kundengenerierte BLOB- oder strukturierte Speicherdaten (z. B. SQL-Container)

- Sicherheitsinformationen des Kunden (z. B. Zertifikate, Verschlüsselungsschlüssel und Kennwörter)

- Schlussfolgerungen und alle nachfolgenden Rückschlüsse, wenn der Inhalt des Kunden bleibt

Weitere Informationen zu Kundeninhalten in Office 365 finden Sie im [Office 365 Trust Center](https://products.office.com/business/office-365-trust-center-privacy/).

#### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>Wer wird benachrichtigt, wenn eine Anforderung für den Zugriff auf meine Inhalte vorliegt?

Globale Administratoren und alle Benutzer, denen die Administratorrolle "Customer Lockbox Access genehmigende Person" zugewiesen wurde, werden benachrichtigt. Dabei handelt es sich auch um dieselben Benutzer, die für Kunden-Lockbox-Anforderungen genehmigen können.

#### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>Wer kann diese Anforderungen in meiner Organisation genehmigen oder ablehnen?

Globale Administratoren und alle Benutzer, denen die Administratorrolle "Kunden Lockbox Access genehmigende Person" zugewiesen ist, können Kunden-Lockbox-Anforderungen genehmigen. Kunden steuern diese Rollenzuweisungen in ihren Organisationen.

#### <a name="how-do-i-opt-in-to-customer-lockbox"></a>Wie aktiviere ich die Kunden-Lockbox?

Ein globaler Administrator kann Kunden-Lockbox im Microsoft 365-oder Microsoft 365 Admin Center aktivieren und konfigurieren.

#### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>Was kann der Techniker tun, wenn ich eine Kunden-Lockbox-Anfrage genehmige, und woher weiß ich, was der Microsoft-Techniker getan hat?

Nachdem Sie eine Kunden-Lockbox-Anforderung genehmigt haben, hat der Microsoft-Techniker diese erforderlichen Berechtigungen für den Zugriff auf Kunden Inhalte mithilfe von vorab genehmigten Cmdlets erteilt. Von Microsoft-Ingenieuren als Reaktion auf Kunden-Lockbox-Anforderungen ausgeführte Aktionen werden im Überwachungsprotokoll im Security & Compliance Center protokolliert und zugänglich gemacht.

#### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>Woher weiß ich, dass Microsoft den Genehmigungsprozess befolgt?

Sie können die e-Mail-Genehmigungsbenachrichtigungen, die an Administratoren und genehmigende Personen in Ihrer Organisation gesendet werden, mit dem Kunden sperrbox-Anforderungsverlauf im Microsoft 365 Admin Center Querverweisen.

Kunden-Lockbox ist im neuesten [SOC 1 SSAE 16-Überwachungsbericht](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports)enthalten. Weitere Informationen finden Sie im [Microsoft-Dienst Vertrauensstellungs Portal](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports), um die neuesten Berichte zu erhalten.

#### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>Kann Microsoft die Liste der genehmigenden Personen für meinen Mandanten ändern? Wenn nicht, wie wird es verhindert?

Nur ein globaler Administrator in Ihrer Organisation kann angeben, wer Kunden-Lockbox-Anforderungen genehmigen kann. Das bedeutet, dass nur die Mitglieder der globalen Administratorgruppe in Azure Active Directory angeben können, wer die Anforderung genehmigen kann. Die Mitgliedschaft in der globalen Administratorgruppe in Azure Active Directory wird nur von Ihrer Organisation verwaltet.

#### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>Was ist, wenn ich weitere Informationen zu einer Inhalts Zugriffsanforderung benötige, um Sie zu genehmigen?

Jede Kunden-Lockbox-Anforderung enthält eine Microsoft 365-Dienstanforderungsnummer. Sie können sich an den Microsoft-Support wenden und auf diese Servicenummer verweisen, um weitere Informationen zur Anforderung zu erhalten.

#### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>Wie lange sind die Berechtigungen gültig, wenn eine Kunden-Lockbox-Anforderung genehmigt wird?

Zurzeit beträgt die maximale Zeitspanne der Zugriffsberechtigungen für den Microsoft-Techniker 4 Stunden. Der Microsoft-Techniker kann auch einen kürzeren Zeitraum anfordern.

#### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>Wie erhalte ich einen Verlauf aller Kunden-Lockbox-Anfragen?

Alle Kunden-Lockbox-Anforderungen werden im Microsoft 365 Admin Center angezeigt.

#### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>Wie kann ich die Inhalts Zugriffsanforderungen mit den zugehörigen Überwachungsprotokollen korrelieren?

Der Compliance Center-Aktivitäts Feed enthält Protokoll Aktivitäten von Customer Lockbox. Kunden können die Aktivitäten des Kunden-Lockbox-Protokolls aus dem Aktivitätsfeed auf die empfangene e-Mail-Anforderung Querverweisen.

#### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>Was geschieht, wenn ein Kunde nicht auf eine Kunden-Lockbox-Anforderung antwortet?

Kunden-Lockbox-Anfragen haben eine Standarddauer von 12 Stunden. Wenn Sie auf eine Anforderung nicht innerhalb von 12 Stunden antworten, läuft die Anforderung ab.

#### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>Was macht Microsoft, wenn ein Kunde eine Lockbox-Anfrage ablehnt?

Wenn ein Kunde eine Kunden-Lockbox-Anforderung ablehnt, erfolgt kein Zugriff auf Kunden Inhalte. Wenn ein Benutzer in Ihrer Organisation weiterhin ein Dienst Problem auftritt, das Microsoft benötigt, um auf Kunden Inhalte zuzugreifen, um das Problem zu beheben, kann das Dienst Problem weiterhin bestehen, und Microsoft informiert den Benutzer hierüber.

#### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>Schützt die Kunden-Lockbox vor Daten Anfragen von Strafverfolgungsbehörden oder anderen Drittanbietern?

Nein. Microsoft nimmt Anfragen von Drittanbietern für Kundendaten ernst. Als Cloud-Dienstanbieter plädiert Microsoft immer für den Schutz von Kundendaten. Für den Fall, dass eine Vorladung vorliegt, versucht Microsoft immer, den Drittanbieter an den Kunden umzuleiten, um die Informationen zu erhalten. (Lesen Sie den Blog von Brad Smith: [Schützen von Kundendaten vor Regierungs snoopings](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)). Wir veröffentlichen regelmäßig [detaillierte Informationen](https://www.microsoft.com/corporate-responsibility/lerr) zu den von Microsoft empfangenen Strafverfolgungs Anforderungen.

Weitere Informationen finden Sie im [Microsoft Trust Center](https://www.microsoft.com/trustcenter/default.aspx) in Bezug auf Datenanforderungen von Drittanbietern und im Abschnitt "Offenlegung von Kundendaten" in den [Online Dienstbedingungen](https://www.microsoft.com/Licensing/product-licensing/products.aspx) .

#### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>Wie gewährleistet Microsoft, dass ein Mitglied seiner Mitarbeiter in Office 365 Anwendungen keinen ständigen Zugriff auf Kunden Inhalte hat?

Microsoft implementiert umfassende vorbeugende Maßnahmen durch Zugriffs Kontrollsysteme und Detektiv Maßnahmen, um Versuche zur Umgehung dieser Zugriffs Steuerungssysteme zu identifizieren und zu beheben. Microsoft 365 arbeitet mit den Grundsätzen der geringsten Rechte und des Just-in-Time-Zugriffs. Daher verfügen keine Microsoft-Mitarbeiter über die Berechtigung für den regelmäßigen Zugriff auf Kunden Inhalte. Wenn die Berechtigung erteilt wird, ist Sie für eine beschränkte Dauer. 

Microsoft 365 verwendet ein Zugriffs Steuerungssystem namens *Lockbox* , um Anforderungen für Berechtigungen zu verarbeiten, die die Möglichkeit zum Ausführen von Betriebs-und Verwaltungsfunktionen innerhalb des Diensts gewähren. Ein Operator muss mithilfe von Lockbox Zugriff auf Kunden Inhalte anfordern, der dann eine zweite Person benötigt, um Maßnahmen für die Anforderung zu ergreifen (beispielsweise genehmigen), bevor der Zugriff erteilt wird. Diese zweite Person kann nicht der Anforderer sein und muss für die Genehmigung des Zugriffs auf Kunden Inhalte festgelegt werden. Nur wenn die Anforderung genehmigt wird, erwirbt der Operator temporären Zugriff auf Kunden Inhalte. Nach Ablauf des Höhen Zeitraums widerruft Lockbox den Zugriff.

Weitere Informationen zu allgemeinen Sicherheitsmethoden in Microsoft finden Sie in den [Online-Dienstbedingungen](https://www.microsoft.com/licensing/product-licensing/products) .

#### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>Unter welchen Umständen benötigen Microsoft-Techniker Zugriff auf meine Inhalte?

Das häufigste Szenario, in dem Microsoft-Ingenieure Zugriff auf Kunden Inhalte benötigen, besteht darin, dass der Kunde eine Supportanforderung für die Problembehandlung stellt. Ein grundlegendes Prinzip von Microsoft 365 ist, dass der Dienst ohne Microsoft-Zugriff auf Kunden Inhalte arbeitet. Fast alle von Microsoft ausgeführten Dienstvorgänge sind vollständig automatisiert, und die menschliche Beteiligung wird streng kontrolliert und von den Kundeninhalten abstrahiert. Das Ziel für Microsoft 365 ist, dass der Zugriff auf Kunden Inhalte zur Unterstützung des Diensts erst dann erforderlich ist, wenn der Kunde eine bestimmte Anforderung für Microsoft Access genehmigt.

#### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>Ich habe bereits gedacht, dass meine Daten mit der Microsoft-Cloud gesichert wurden, weshalb benötige ich die Kunden-Lockbox?

Kunden-Lockbox bietet eine zusätzliche Kontrollschicht, indem Kunden die Möglichkeit bieten, explizite Zugriffsautorisierung für Dienstvorgänge zu erteilen. Durch den Nachweis, dass Verfahren für die explizite Datenzugriffs Autorisierung vorhanden sind, hilft Kunden-Lockbox auch Kunden bei der Erfüllung bestimmter Compliance-Verpflichtungen wie HIPAA und FEDRAMP.
