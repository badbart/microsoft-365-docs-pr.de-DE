---
title: Referenz zur Kommunikation Compliance-Feature
description: Funktionsreferenz für die Kommunikations Kompatibilität in Microsoft 365. Hier finden Sie Details und Spezifikationen für die einzelnen Feature-Komponenten.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: e1e1677c929ef0de5d47dbb98ef8987a8fba548d
ms.sourcegitcommit: 1522a6471e0c5254a6d0f592e1f4dfacd1dd473a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2020
ms.locfileid: "48245902"
---
# <a name="communication-compliance-feature-reference"></a>Referenz zur Kommunikation Compliance-Feature

## <a name="policies"></a>Richtlinien

>[!Important]
>Die Verwendung von PowerShell zum Erstellen und Verwalten von Richtlinien zur Kommunikationscompliance wird nicht unterstützt. Zum Erstellen und Verwalten dieser Richtlinien müssen Sie die Steuerelemente für die Richtlinienverwaltung in der [Microsoft 365 Communication Compliance-Lösung](https://compliance.microsoft.com/supervisoryreview)verwenden.

Im Microsoft 365 Compliance Center erstellen Sie Richtlinien zur Kommunikationscompliance für Microsoft 365-Organisationen. Compliance-Richtlinien für Kommunikation definieren, welche Kommunikation und welche Benutzer in Ihrer Organisation überprüft werden sollen, definieren, welche benutzerdefinierten Bedingungen die Kommunikation erfüllen muss, und angeben, wer Überprüfungen durchführen soll. Benutzer, denen die *Administratorrolle "Communications Compliance"* zugewiesen ist, können Richtlinien einrichten, und jeder, dem diese Rolle zugewiesen ist, kann auf die Seite " **Kommunikations Kompatibilität** " und globale Einstellungen im Microsoft 365 Compliance Center zugreifen. Bei Bedarf können Sie den Verlauf von Änderungen an einer Richtlinie in eine CSV-Datei exportieren, die auch den Status der ausstehenden Warnungen, eskalierter Elemente und aufgelöster Elemente enthält. Richtlinien können nicht umbenannt werden und können gelöscht werden, wenn Sie nicht mehr benötigt werden.

>[!NOTE]
>Aufsichtsrichtlinien, die im Security & Compliance Center für Office 365-Abonnements erstellt wurden, können nicht zu Microsoft 365 migriert werden. Wenn Sie von einem Office 365-Abonnement zu einem Microsoft 365-Abonnement migrieren, müssen Sie neue Richtlinien für die Kommunikationsrichtlinien Erstellung erstellen, um vorhandene Aufsichtsrichtlinien zu ersetzen.

## <a name="policy-templates"></a>Richtlinienvorlagen

Richtlinienvorlagen sind vordefinierte Richtlinieneinstellungen, mit denen Sie schnell Richtlinien erstellen können, um allgemeine Kompatibilitätsszenarien zu behandeln. Jede dieser Vorlagen weist Unterschiede bei Bedingungen und Umfang auf, und alle Vorlagen verwenden dieselben Arten von Scan Signalen. Sie können aus den folgenden Richtlinienvorlagen auswählen:

|**Bereich**|**Richtlinienvorlage**|**Details**|
|:-----|:-----|:-----|
| **Anstößige Sprache und Anti-Belästigung** | Überwachen der Kommunikation für anstößige Sprache | -Locations: Exchange Online, Microsoft Teams, jammern, Skype for Business <br> -Direction: eingehend, ausgehende, intern <br> -Review-Prozentsatz: 100% <br> -Bedingungen: anstößige sprach Klassifizierung |
| **Vertrauliche Informationen** | Überwachen der Kommunikation für vertrauliche Informationen | -Locations: Exchange Online, Microsoft Teams, jammern, Skype for Business <br> -Direction: eingehend, ausgehende, intern <br> -Review-Prozentsatz: 10% <br> -Bedingungen: vertrauliche Informationen, vordefinierte Inhalts Muster und Typen, Benutzerwörterbuch-Option, Anlagen größer als 1 MB |
| **Einhaltung gesetzlicher Bestimmungen** | Überwachen der Kommunikation für Informationen im Zusammenhang mit der finanzbehördlichen Compliance | -Locations: Exchange Online, Microsoft Teams, jammern, Skype for Business <br> -Direction: eingehend, Outbound <br> -Review-Prozentsatz: 10% <br> -Bedingungen: Benutzerwörterbuch-Option, Anlagen größer als 1 MB |

## <a name="permissions-preview"></a>Berechtigungen (Vorschau)

>[!Important]
>Standardmäßig haben globale Administratoren keinen Zugriff auf Features für die Kommunikations Kompatibilität. Die in diesem Schritt zugewiesenen Rollen sind erforderlich, bevor auf Kommunikations Kompatibilitätsfeatures zugegriffen werden kann.

Es gibt fünf Rollengruppen, die zum Konfigurieren von Berechtigungen zum Verwalten von Kommunikations Kompatibilitätsfeatures verwendet werden. Um die **Kommunikation Compliance** als Menüoption im Microsoft 365 Compliance Center zur Verfügung zu stellen und diese Konfigurationsschritte fortzusetzen, müssen Sie den Administratorrollengruppen " *Communication Compliance* " oder " *Communication Compliance"* zugewiesen sein. Für den Zugriff auf und die Verwaltung von Kommunikations Kompatibilitätsfeatures nach der anfänglichen Konfiguration müssen Benutzer Mitglied mindestens einer Rollengruppe für die Kommunikations Kompatibilität sein.

Je nachdem, wie Sie Kommunikationsrichtlinien und Warnungen verwalten möchten, müssen Sie Benutzer bestimmten Rollengruppen zuweisen. Sie haben die Möglichkeit, Benutzer mit unterschiedlichen Compliance-Verantwortlichkeiten bestimmten Rollengruppen zuzuweisen, um verschiedene Bereiche der Kommunikations Compliance-Features zu verwalten. Sie können auch festlegen, dass alle Benutzerkonten für designierte Administratoren, Analysten, Ermittler und Betrachter der Rollengruppe *Kommunikation Compliance* zugewiesen werden. Verwenden Sie eine einzelne Rollengruppe oder mehrere Rollengruppen, um Ihre Anforderungen an die Compliance-Verwaltung am besten anzupassen.

Wählen Sie unter diese Rollengruppen Optionen aus, wenn Sie die Kommunikations Kompatibilität konfigurieren:

|**Rolle**|**Rollenberechtigungen**|
|:-----|:-----|
| **Kommunikation Compliance** | Verwenden Sie diese Rollengruppe, um die Kommunikations Konformität für Ihre Organisation in einer einzigen Gruppe zu verwalten. Durch Hinzufügen aller Benutzerkonten für designierte Administratoren, Analysten, Ermittler und Betrachter können Sie die Berechtigungen für die Kommunikations Konformität in einer einzigen Gruppe konfigurieren. Diese Rollengruppe enthält alle Berechtigungsrollen für die Kommunikations Konformität. Diese Konfiguration ist die einfachste Möglichkeit, um schnell mit der Kommunikation zu beginnen, und Sie eignet sich gut für Organisationen, die keine separaten Berechtigungen benötigen, die für getrennte Benutzergruppen definiert sind. |
| **Communication Compliance-Administrator** | Verwenden Sie diese Rollengruppe, um die Kommunikationsrichtlinien Konfiguration zu konfigurieren und später Kommunikationsrichtlinien Administratoren in eine definierte Gruppe zu trennen. Benutzer, die dieser Rollengruppe zugewiesen sind, können Kommunikationsrichtlinien, globale Einstellungen und Rollengruppen Zuordnungen erstellen, lesen, aktualisieren und löschen. Benutzer, die dieser Rollengruppe zugewiesen sind, können keine Nachrichten Benachrichtigungen anzeigen. |
| **Communication Compliance Analyst** | Verwenden Sie diese Gruppe, um Benutzern Berechtigungen zuzuweisen, die als Kommunikations Compliance-Analysten fungieren sollen. Benutzer, die dieser Rollengruppe zugewiesen sind, können Richtlinien anzeigen, in denen Sie als Bearbeiter zugewiesen werden, Nachrichten Metadaten anzeigen (keine Nachrichteninhalte), an zusätzliche Bearbeiter eskalieren oder Benachrichtigungen an Benutzer senden. Ausstehende Warnungen können von Analysten nicht aufgelöst werden. |
| **Communication Compliance Investigator** | Verwenden Sie diese Gruppe, um Benutzern Berechtigungen zuzuweisen, die als Kommunikations Compliance-Ermittler fungieren sollen. Benutzer, die dieser Rollengruppe zugewiesen sind, können Nachrichten Metadaten und-Inhalte anzeigen, an zusätzliche Bearbeiter eskalieren, zu einem erweiterten eDiscovery-Fall eskalieren, Benachrichtigungen an Benutzer senden und die Warnung lösen. |
| **Communication Compliance Viewer** | Verwenden Sie diese Gruppe, um Benutzern Berechtigungen für die Verwaltung von Kommunikations Berichten zuzuweisen. Benutzer, die dieser Rollengruppe zugewiesen sind, können auf der Homepage der Communication Compliance auf alle Berichts-Widgets zugreifen und alle Kommunikations Konformitätsberichte anzeigen. |

### <a name="for-organizations-using-the-original-permissions-and-role-groups"></a>Für Organisationen, die die ursprünglichen Berechtigungen und Rollengruppen verwenden

Die neue Rollengruppen Struktur ersetzt die anfängliche Rollengruppen Struktur für die Kommunikations Kompatibilität. Für Organisationen, die die Kommunikations Konformität bereits verwenden, mussten Sie die Rolle Aufsichts Überprüfungs Administrator erhalten, um mit der Kommunikation im Microsoft 365 Compliance Center zu beginnen. Darüber hinaus mussten Sie eine neue Rollengruppe für Bearbeiter mit dem Aufsichts Überprüfungs Administrator, der Fallverwaltung, dem Kompatibilitäts Administrator und den Überprüfungs Rollen erstellen, um Nachrichten mit Richtlinien Übereinstimmungen zu untersuchen und zu beheben. Im Wesentlichen befanden sich alle Administratoren und Bearbeiter in einer einzelnen Rollengruppe, und alle hatten dieselben Zugriffs-und Verwaltungsberechtigungen. Mit den neuesten Updates für die Kommunikations Kompatibilität sollten Sie die Migration von der vorherigen Rollengruppen Struktur in die neue Rollengruppen Struktur planen. Die Unterstützung für die vorherige Rollengruppen Struktur wird ablaufen.

Zur Unterstützung der Migrationsplanung sollten Sie das folgende Beispiel verwenden. Sie verfügen derzeit über drei Typen von Benutzern in Ihrer Organisation, IT-Administratoren, Triage und Prüfer. Diese drei Benutzertypen befinden sich in der vorherigen Rollengruppen Struktur und sind alle Mitglieder einer einzelnen Rollengruppe, der die folgenden Rollen zugewiesen sind:

- Aufsichts Überprüfungs Administrator
- Fallverwaltung
- Complianceadministrator
- Überprüfung

Um die Rollen für diese Benutzer für die neue Rollengruppen Struktur zu aktualisieren und die Zugriffs-und Verwaltungsberechtigungen für die Benutzer zu trennen, können Sie drei neue Gruppen und die zugeordneten neuen Rollengruppen Zuweisungen in Frage stellen:

- **IT-Administratoren**: der neuen Administratorrollengruppe für die *Kommunikationsrichtlinien Verwaltung* zugewiesen.
- **Triage**: der Rollengruppe " *Communication Compliance Analyst* " zugewiesen.
- **Bearbeiter**: der neuen *Kommunikations Compliance-Ermittler* -Rollengruppe zugewiesen.

## <a name="supervised-users"></a>Beaufsichtigte Benutzer

Bevor Sie mit der Kommunikationscompliance beginnen, müssen Sie feststellen, wer die Überprüfung der Kommunikation benötigt. In der Richtlinie identifizieren die E-Mail-Adressen der Benutzer Einzelpersonen oder Personengruppen, die überwacht werden sollen. Einige Beispiele für diese Gruppen sind Microsoft 365-Gruppen, Exchange-basierte Verteilerlisten, Jammer Gemeinschaften und Microsoft Teams-Kanäle. Sie können auch bestimmte Benutzer oder Gruppen mit einer bestimmten Ausschlussgruppe oder einer Liste von Gruppen vom Überprüfen ausschließen.

>[!IMPORTANT]
>Für Benutzer, die von Kommunikationsrichtlinien Richtlinien abgedeckt werden, muss entweder eine Microsoft 365 E5-Konformitäts Lizenz, eine Office 365 Enterprise E3-Lizenz mit dem Add-on für die erweiterte Kompatibilität oder ein Office 365 Enterprise E5-Abonnement enthalten sein. Wenn Sie über keinen vorhandenen Enterprise E5-Plan verfügen und die Kommunikations Kompatibilität testen möchten, können Sie [sich für eine Testversion von Office 365 Enterprise E5 anmelden](https://go.microsoft.com/fwlink/p/?LinkID=698279).

## <a name="reviewers"></a>Prüfer

Wenn Sie eine Kommunikations Konformitätsrichtlinie erstellen, müssen Sie ermitteln, wer die Nachrichten der überwachten Benutzer überprüft. In der Richtlinie identifizieren die E-Mail-Adressen der Benutzer Einzelpersonen oder Personengruppen, welche die überwachte Kommunikation überprüfen sollen. Alle Bearbeiter müssen über Postfächer verfügen, die auf Exchange Online gehostet werden und entweder der *Kommunikations Konformitätsanalyse* oder der *Compliance-Ermittlungs* Rolle "Kommunikation" zugewiesen sein müssen. Bearbeiter (entweder Analysten oder Ermittler) müssen auch die *Verwaltungsrolle "Communication Compliance Case* " zugewiesen haben. Wenn Bearbeiter einer Richtlinie hinzugefügt werden, erhalten Sie automatisch eine e-Mail-Nachricht, die Sie über die Zuweisung zur Richtlinie benachrichtigt und Links zu Informationen über den Überprüfungsprozess enthält.

## <a name="groups-for-supervised-users-and-reviewers"></a>Gruppen für beaufsichtigte Benutzer und Bearbeiter

Um Ihr Setup zu vereinfachen, erstellen Sie Gruppen für Personen, die Ihre Kommunikation überprüfen müssen, sowie Gruppen für Personen, die diese Kommunikationen überprüfen. Wenn Sie Gruppen verwenden, benötigen Sie möglicherweise mehrere. Zum Beispiel, wenn Sie die Kommunikation zwischen zwei verschiedenen Personengruppen überprüfen möchten oder wenn Sie eine Gruppe angeben möchten, die nicht überwacht wird.

Wenn Sie eine Verteilergruppe in der Richtlinie zuweisen, überwacht die Richtlinie alle e-Mails von jedem Benutzer in der Verteilergruppe. Wenn Sie eine Microsoft 365-Gruppe in der Richtlinie zuweisen, überwacht die Richtlinie alle e-Mails, die an diese Gruppe gesendet werden, und nicht die einzelnen e-Mails, die von den einzelnen Gruppenmitgliedern empfangen werden.

Das Hinzufügen von Gruppen und Verteilerlisten zu Kommunikations Konformitätsrichtlinien ist Teil der allgemeinen Bedingungen und Regeln, sodass die maximale Anzahl von Gruppen und Verteilerlisten, die eine Richtlinie unterstützt, abhängig von der Anzahl der Bedingungen variiert, die auch der Richtlinie hinzugefügt werden. Jede Richtlinie sollte je nach der Anzahl der in der Richtlinie vorhandenen zusätzlichen Bedingungen ungefähr 20 Gruppen oder Verteilerlisten unterstützen.

## <a name="supported-communication-types"></a>Unterstützte Kommunikationstypen

Mit Richtlinien für die Kommunikations Konformität können Sie auswählen, ob Nachrichten in einer oder mehreren der folgenden Kommunikationsplattformen als Gruppe oder als eigenständige Quellen überprüft werden sollen. Auf diesen Plattformen erfasste Kommunikationen werden für jede Richtlinie standardmäßig sieben Jahre lang aufbewahrt, selbst wenn Benutzer Ihre Organisation verlassen und ihre Postfächer gelöscht werden.

- **Microsoft Teams**: Chatnachrichten im öffentlichen und privaten Microsoft Teams-Kanal und einzelne Chats können gescannt werden. Wenn Benutzer einer Kommunikations Konformitätsrichtlinie mit Microsoft Teams-Abdeckung ausgewählt sind, wird die Chat Kommunikation für die Benutzer automatisch in allen Microsoft Teams überwacht, in denen die Benutzer Mitglied sind. Microsoft Teams Coverage wird automatisch für vordefinierte Richtlinienvorlagen einbezogen und in der benutzerdefinierten Richtlinienvorlage standardmäßig ausgewählt. Microsoft Teams-Chats, die Richtlinienbedingungen für die Kommunikation erfüllen, können bis zu 24 Stunden verarbeiten. Verwenden Sie die folgenden Gruppen Verwaltungs Konfigurationen, um einzelne Benutzer Chats und Kanal Kommunikationen in Microsoft Teams zu überwachen:

    - **Für Chatnachrichten in Microsoft Teams:** Zuweisen einzelner Benutzer oder Zuweisen einer [Verteilergruppe](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) zur Kommunikations Konformitätsrichtlinie. Diese Einstellung gilt für Eins-zu-eins- oder Eins-zu-viele-Benutzer/Chat-Beziehungen.
    - **Für Teams-Kanal Kommunikation:** Weisen Sie jedem Microsoft Teams-Kanal oder einer Microsoft 365-Gruppe zu, die Sie überprüfen möchten, die einen bestimmten Benutzer für die Kommunikations Konformitätsrichtlinie enthält. Wenn Sie denselben Benutzer zu anderen Microsoft Teams-Kanälen oder Microsoft 365-Gruppen hinzufügen, stellen Sie sicher, dass Sie diese neuen Kanäle und Gruppen in die Richtlinie zur Kommunikationscompliance aufnehmen.
    - **Für Teams Chat Kommunikation mit Hybrid-e-Mail-Umgebungen**: Kommunikation Compliance kann Chatnachrichten für Benutzer für Organisationen mit einer lokalen Exchange-Bereitstellung oder einem externen e-Mail-Anbieter überwachen, die Microsoft Teams aktiviert haben. Sie müssen eine Verteilergruppe für die Benutzer mit lokalen oder externen Postfächern erstellen, die überwacht werden sollen. Wenn Sie eine Kommunikations Konformitätsrichtlinie erstellen, weisen Sie diese Verteilergruppe im Richtlinien-Assistenten als über **wachte Benutzer und Gruppen** Auswahl zu.

    >[!IMPORTANT]
    >Sie müssen eine Anforderung mit dem Microsoft-Support einreichen, damit Ihre Organisation die grafische Benutzeroberfläche im Security & Compliance Center verwenden kann, um nach teamchatdaten für lokale Benutzer zu suchen. Weitere Informationen finden Sie unter [searching Cloud-based Mailboxes for on-premises users](search-cloud-based-mailboxes-for-on-premises-users.md).

Sie müssen eine Anforderung beim Microsoft-Support stellen, damit Ihre Organisation die grafische Benutzeroberfläche im Security & Compliance Center verwenden kann, um in den cloudbasierten Postfächern für lokale Benutzer nach Teams-Chatdaten zu suchen.

- **Exchange-e-Mail**: Postfächer, die auf Exchange Online als Teil Ihres Microsoft 365-oder Office 365-Abonnements gehostet werden, sind alle für die Nachrichtenüberprüfung berechtigt. Exchange-e-Mail-Nachrichten und Anlagen, die Richtlinienbedingungen für die Kommunikation erfüllen, können bis zu 24 Stunden verarbeiten. Die für die Kommunikationscompliance unterstützten Anlagetypen sind die gleichen wie die [Dateitypen, die für die Inhaltsüberprüfung von Exchange-Mailflussregeln unterstützt werden](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

- **Jammern**: Private Nachrichten und öffentliche Unterhaltungen und zugehörige Anlagen in Jammer Gemeinschaften können gescannt werden. Wenn ein Benutzer zur Kommunikations Konformitätsrichtlinie hinzugefügt wird, die das Jammern als definierten Kanal umfasst, werden die Kommunikationen in allen Jammer Gemeinschaften, in denen der Benutzer Mitglied ist, in den Überprüfungsprozess einbezogen. Jammern von Chats und Anlagen, die Richtlinienbedingungen für die Kommunikation erfüllen, können bis zu 24 Stunden in Anspruch nehmen. Jammern muss im [einheitlichen Modus](https://docs.microsoft.com/yammer/configure-your-yammer-network/overview-native-mode) für Kommunikationsrichtlinien zur Überwachung von jammern von Kommunikation und Anlagen sein. Im nativen Modus befinden sich alle Yammer-Benutzer in Azure Active Directory (AAD), alle Gruppen sind Office 365-Gruppen, und alle Dateien werden in SharePoint Online gespeichert.

- **Skype for Business Online**: Chatnachrichten und zugehörige Anlagen in Skype for Business Online können überwacht werden. Die Bearbeitung von Skype for Business Online-Chats, in denen die Bedingungen für die Richtlinien zur Kommunikationscompliance erfüllt werden, kann bis zu 24 Stunden dauern. Überwachte Chat Unterhaltungen werden aus [früheren Unterhaltungen, die in Skype for Business Online gespeichert](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2)wurden, bezogen.  Verwenden Sie die folgende Gruppen Verwaltungskonfiguration, um die Benutzer Chat Kommunikation in Skype for Business Online zu überwachen:

    - **Für Skype for Business Online Chat Kommunikation**: zuweisen einzelner Benutzer oder Zuweisen einer [Verteilergruppe](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) zur Kommunikations Konformitätsrichtlinie. Diese Einstellung gilt für Eins-zu-eins- oder Eins-zu-viele-Benutzer/Chat-Beziehungen.

- **Drittanbieterquellen**: Sie können Kommunikationen aus Drittanbieterquellen nach Daten überprüfen, die in Postfächer in Ihrer Microsoft 365-Organisation importiert wurden. Connectors unterstützen die folgenden Drittanbieterressourcen:

    - [Instant Bloomberg](archive-instant-bloomberg-data.md)
    - [Bloomberg Message](archive-bloomberg-message-data.md)
    - [ICE Chat](archive-icechat-data.md)

Sie müssen einen Drittanbieter-Connector für Ihre Microsoft 365-Organisation konfigurieren, bevor Sie den Connector einer Kommunikations Konformitätsrichtlinie zuweisen können. Im Abschnitt " **Drittanbieterquellen** " des Assistenten für die Kommunikation mit Kompatibilitätsrichtlinien werden derzeit konfigurierte Connectors von Drittanbietern angezeigt.

## <a name="transitioning-from-supervision-in-office-365"></a>Übergang von der Aufsicht in Office 365

Organisationen, die Aufsichtsrichtlinien in Office 365 verwenden und den Übergang zu Kommunikationsrichtlinien in Microsoft 365 planen, müssen diese wichtigen Punkte verstehen:

- Beide Lösungen können in Ihrer Organisation nebeneinander verwendet werden, aber die in jeder Lösung verwendeten Richtlinien müssen eindeutige Richtliniennamen haben. aufweisen. Gruppen und benutzerdefinierte Schlüsselwortwörterbücher können während einer Übergangszeit von Lösungen gemeinsam genutzt werden.
- Nachrichten, die in Office 365 Richtlinien Übereinstimmungen gespeichert wurden, können nicht in der Kommunikations Kompatibilität in Microsoft 365 verschoben oder freigegeben werden.
- Die Überwachungslösung in Office 365 wird vollständig durch die Kommunikations kompatibilitätslösung in Microsoft 365 ersetzt. Es wird empfohlen, neue Richtlinien in der Kommunikations Kompatibilität zu erstellen, die die gleichen Einstellungen wie die vorhandenen Aufsichtsrichtlinien aufweisen, um die neuen Untersuchungen und Korrektur Verbesserungen zu verwenden. Beim Übergang zur Kommunikationscompliance in Microsoft 365 sollten Sie planen, Berichtsdaten aus der Aufsicht in Office 365 zu exportieren, wenn Sie interne Richtlinien zur Aufbewahrung von Compliance-Anforderungen haben.

Informationen zur Beaufsichtigung in Office 365 finden Sie im [Microsoft 365-Fahrplan](https://www.microsoft.com/microsoft-365/roadmap) für Vorsorge Informationen.

## <a name="policy-settings"></a>Richtlinieneinstellungen

### <a name="users"></a>Benutzer

Sie haben die Möglichkeit, **alle Benutzer** auszuwählen oder bestimmte Benutzer in einer Kommunikations Konformitätsrichtlinie zu definieren. Durch Auswahl von **Alle Benutzer** wird die Richtlinie auf alle Benutzer und alle Gruppen angewendet, in denen ein Benutzer als Mitglied enthalten ist. Das Festlegen bestimmter Benutzer wendet die Richtlinie auf die festgelegten Benutzer und alle Gruppen an, in denen die festgelegten Benutzer als Mitglied enthalten sind.

### <a name="direction"></a>Direction

Standardmäßig wird die Bedingung " **Direction** " angezeigt und kann nicht entfernt werden. Die Einstellungen für die Kommunikationsrichtung in einer Richtlinie werden einzeln oder gemeinsam ausgewählt:

- **Eingehend**: Sie können " **eingehend** " auswählen, um die Kommunikation zu überprüfen **, die an** die Personen gesendet wird, die Sie überwachen möchten.
- Ausgehend **: Sie**können ausgehend **wählen,** Wenn Sie die Kommunikationen überprüfen möchten, die **von** den Personen gesendet wurden, die Sie überwachen wollten.
- **Intern**: Sie können **interne** auswählen, um die Kommunikation zu überprüfen, die **zwischen** den Personen gesendet wird, die Sie in der Richtlinie angegeben haben.

### <a name="sensitive-information-types"></a>Typen vertraulicher Informationen

Sie haben die Möglichkeit, vertrauliche Informationstypen als Teil ihrer Kommunikations Konformitätsrichtlinie einzubinden. Vertrauliche Informationstypen sind entweder vordefinierte oder benutzerdefinierte Datentypen, die helfen, Kreditkartennummern, Bank Kontonummern, Passport-Nummern und vieles mehr zu identifizieren und zu schützen. Als Bestandteil von [Verhinderung von Datenverlust (Data Loss Prevention, DLP)](data-loss-prevention-policies.md), kann die Konfiguration vertraulicher Informationen Muster, Zeichennähe, Vertrauensniveaus und sogar benutzerdefinierte Datentypen verwenden, um möglicherweise vertrauliche Inhalte zu identifizieren und zu kennzeichnen. Die Standardtypen für vertrauliche Informationen sind:

- Finanzwesen
- Medizin und Gesundheit
- Datenschutz
- Benutzerdefinierter Informationstyp

Weitere Informationen zu vertraulichen Informationsdetails und den Mustern, die in den Standardtypen enthalten sind, finden Sie unter [sensitive Information Type Entity Definitions](sensitive-information-type-entity-definitions.md).

### <a name="custom-keyword-dictionaries"></a>Benutzerdefinierte Schlüsselwörter Wörterbücher

Konfigurieren Sie benutzerdefinierte Keyword-Wörterbücher (oder Lexika), um eine einfache Verwaltung von Schlüsselwörtern für Ihre Organisation oder Industrie bereitzustellen. Stichwort Wörterbücher unterstützen bis zu 100 KB von Begriffen (nach der Komprimierung) im Wörterbuch und unterstützen jede Sprache. Die Mandanten Grenze beträgt auch 100 KB nach der Komprimierung. Bei Bedarf können Sie mehrere benutzerdefinierte Schlüsselwörter Wörterbücher auf eine einzelne Richtlinie anwenden oder über ein einzelnes Schlüssel Wörterbuch pro Richtlinie verfügen. Diese Wörterbücher werden in einer Kommunikations Konformitätsrichtlinie zugewiesen und können aus einer Datei (wie einer CSV-oder txt-Liste) oder aus einer Liste stammen, [die Sie im Compliance Center importieren](create-a-keyword-dictionary.md)können. Verwenden Sie Benutzerwörterbücher, wenn Sie Ausdrücke oder Sprachen speziell für Ihre Organisation und ihre Richtlinien unterstützen müssen.

### <a name="classifiers"></a>Klassifizierungen

Integrierte Schulungs-und globale Klassifizierungen überprüfen gesendete oder empfangene Nachrichten über alle Kommunikationskanäle in Ihrer Organisation für unterschiedliche Arten von Kompatibilitätsproblemen. Klassifizierer verwenden eine Kombination aus künstlicher Intelligenz und Schlüsselwörtern, um Sprache in Botschaften zu identifizieren, die wahrscheinlich gegen die Antibelästigungsrichtlinien verstoßen. Integrierte Klassifizierungen unterstützen derzeit nur englische Stichwörter in Nachrichten.

Kommunikation Compliance integrierte Schulungs-und globale Klassifizierungen überprüfen die Kommunikation auf Begriffe, Bilder und Meinungen für die folgenden Sprach-und Inhaltstypen:

- **Bedrohung**: scannt nach Bedrohungen, um Gewalt oder körperlichen Schaden für eine Person oder Eigenschaft zu begehen.
- **Gezielte Belästigung**: Scans für anstößige Verhaltensweisen, die Menschen hinsichtlich Rasse, Farbe, Religion und nationalem Ursprung anvisieren.
- **Profanität**: scannt nach profanen Ausdrücken, die die meisten Menschen in Verlegenheit bringen.
- **Bilder für Erwachsene**: scannt nach Bildern, die in der Natur sexuell explizit sind.
- **Rassige Bilder**: scannt nach Bildern, die in der Natur sexuell suggestive sind, jedoch weniger expliziten Inhalt enthalten als für Erwachsene vorgesehene Bilder.
- **Blutige Bilder**: scannt nach Bildern, die Gewalt und Gore darstellen.

Die *adulten*, *rassigen*und *blutigen* Bild Klassifizierungen überprüfen Dateien in. JPEG,. PNG,. GIF und. BMP-Formate. Die Größe von Bilddateien muss kleiner als 4 MB sein, und die Abmessungen der Bilder müssen größer als 50x50 Pixel und größer als 50 Kilobyte (KB) sein, damit das Bild für die Auswertung qualifiziert wird. Die Bild Identifikation wird für Exchange Online e-Mail-Nachrichten und Microsoft Teams-Kanäle und-Chats unterstützt.

Die integrierten Schulungs-und globalen Klassifizierungen bieten keine erschöpfende Liste von Begriffen oder Bildern in diesen Bereichen. Außerdem ändern sich die Sprach-und Kulturstandards ständig, und in Anbetracht dieser Gegebenheiten behält sich Microsoft das Recht vor, die Klassifizierungen nach eigenem Ermessen zu aktualisieren. Während Klassifizierungen Ihre Organisation bei der Überwachung dieser Bereiche unterstützen können, sind Klassifizierungen nicht dazu gedacht, die einzige Möglichkeit zur Überwachung oder Adressierung solcher Sprachen oder Bilder in Ihrer Organisation bereitzustellen. Ihre Organisation, nicht Microsoft, bleibt für alle Entscheidungen im Zusammenhang mit dem Scannen und Blockieren von Sprache und Bildern in diesen Bereichen verantwortlich.

Informationen zu Schulungs Klassifizierern in Microsoft 365 finden Sie unter [Erste Schritte mit Schulungs Klassifizierern](classifier-get-started-with.md).

### <a name="conditional-settings"></a>Bedingte Einstellungen
<a name="ConditionalSettings"> </a>

Die Bedingungen, die Sie für die Richtlinie wählen, gelten für die Kommunikation sowohl von e-Mails als auch von Drittanbieterquellen in Ihrer Organisation (wie von Instant Bloomberg oder Dropbox).

In der folgenden Tabelle werden die einzelnen Bedingungen näher erläutert.
  
|**Bedingung**|**Verwendung**|
|:-----|:-----|
| **Inhalt entspricht einer dieser Klassifizierungen** | Auf die Richtlinie anwenden, wenn Klassifizierer in einer Nachricht eingeschlossen oder ausgeschlossen werden. Einige Klassifizierungen sind in Ihrem Mandanten vordefiniert, und benutzerdefinierte Klassifizierungen müssen separat konfiguriert werden, bevor Sie für diese Bedingung verfügbar sind. Nur eine Klassifizierung kann als Bedingung in einer Richtlinie definiert werden. Weitere Informationen zum Konfigurieren von Klassifizierungen finden Sie unter erfahren Sie mehr [über Lernende Klassifizierungen (Preview)](classifier-learn-about.md). |
| **Inhalt enthält alle diese vertraulichen Info Typen** | Auf die Richtlinie anwenden, wenn vertrauliche Informationstypen in einer Nachricht enthalten oder ausgeschlossen werden. Einige Klassifizierungen sind in Ihrem Mandanten vordefiniert, und benutzerdefinierte Klassifizierungen können separat oder als Teil des Bedingungs Zuordnungsprozesses konfiguriert werden. Jeder vertrauliche Informationstyp, den Sie auswählen, wird separat angewendet, und nur einer dieser Typen für vertrauliche Informationen muss für die Richtlinie gelten, die auf die Nachricht angewendet werden soll. Weitere Informationen zu benutzerdefinierten vertraulichen Informationstypen finden Sie unter [benutzerdefinierte vertrauliche Informationstypen](custom-sensitive-info-types.md). |
| **Nachricht wird von einer dieser Domänen empfangen**  <br><br> **Nachricht wird von keiner dieser Domänen empfangen** | Wenden Sie die Richtlinie an, um bestimmte Domänen oder e-Mail-Adressen in empfangene Nachrichten einzubeziehen oder auszuschließen. Geben Sie jede Domäne oder e-Mail-Adresse ein, und trennen Sie mehrere Domänen oder e-Mail-Adressen durch ein Komma. Jede eingegebene Domäne oder e-Mail-Adresse wird separat angewendet, nur eine Domäne oder e-Mail-Adresse muss für die Richtlinie gelten, die auf die Nachricht angewendet werden soll. <br><br> Wenn Sie alle e-Mails von einer bestimmten Domäne überprüfen möchten, aber Nachrichten ausschließen möchten, die keine Überprüfung (Newsletter, Ankündigungen usw.) benötigen, müssen Sie konfigurieren, dass eine **Nachricht nicht von einer dieser Domänen Bedingungen empfangen wird** , die die e-Mail-Adresse ausschließt (Beispiel "Newsletter@contoso.com"). |
| **Nachricht wird an eine dieser Domänen gesendet.**  <br><br> **Nachricht wird nicht an eine dieser Domänen gesendet** | Wenden Sie die Richtlinie an, um bestimmte Domänen oder e-Mail-Adressen in gesendete Nachrichten einzuschließen oder auszuschließen. Geben Sie jede Domäne oder e-Mail-Adresse ein, und trennen Sie mehrere Domänen oder e-Mail-Adressen durch ein Komma. Jede Domäne oder e-Mail-Adresse wird separat angewendet, nur eine Domäne oder e-Mail-Adresse muss für die Richtlinie gelten, die auf die Nachricht angewendet werden soll. <br><br> Wenn Sie alle an eine bestimmte Domäne gesendeten e-Mails überprüfen möchten, jedoch gesendete Nachrichten ausschließen möchten, die keine Überprüfung benötigen, müssen Sie zwei Bedingungen konfigurieren: <br> -Eine **Nachricht wird an eine dieser Domänen Bedingungen gesendet** , die die Domäne definiert ("contoso.com") und <br> -Eine **Nachricht wird nicht an eine dieser Domänen Bedingungen gesendet** , die die e-Mail-Adresse ("Subscriptions@contoso.com") ausschließen. |
| **Nachricht wird mit einer dieser Bezeichnungen klassifiziert.**  <br><br> **Nachricht ist nicht mit einer dieser Bezeichnungen klassifiziert** | So wenden Sie die Richtlinie an, wenn bestimmte Aufbewahrungs Bezeichnungen in einer Nachricht enthalten oder ausgeschlossen werden. Aufbewahrungs Bezeichnungen müssen separat konfiguriert werden, und die konfigurierten Beschriftungen werden als Teil dieser Bedingung ausgewählt. Jede ausgewählte Bezeichnung wird separat angewendet (nur eine dieser Bezeichnungen muss für die Richtlinie gelten, die auf die Nachricht angewendet wird). Weitere Informationen zu Aufbewahrungs Bezeichnungen finden Sie unter Informationen [zu Aufbewahrungsrichtlinien und Aufbewahrungs Bezeichnungen](retention.md).|
| **Nachricht enthält eines dieser Wörter**  <br><br> **Nachricht enthält keines dieser Wörter** | Wenn Sie die Richtlinie anwenden möchten, wenn bestimmte Wörter oder Ausdrücke in einer Nachricht enthalten oder ausgeschlossen werden, geben Sie jedes Wort ein, das durch ein Komma getrennt ist. Verwenden Sie für Ausdrücke mit zwei oder mehr Wörtern Anführungszeichen um den Ausdruck. Jedes Wort oder jede Phrase, die Sie eingeben, wird separat angewendet (es muss nur ein Wort für die Richtlinie gelten, die auf die Nachricht angewendet wird). Weitere Informationen zum Eingeben von Wörtern oder Ausdrücken finden Sie im nächsten Abschnitt [Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords).|
| **Attachment enthält eines dieser Wörter**  <br><br> **Attachment enthält keines dieser Wörter** | Wenn Sie die Richtlinie anwenden möchten, wenn bestimmte Wörter oder Ausdrücke in einer Nachrichtenanlage eingeschlossen oder ausgeschlossen werden (beispielsweise in einem Word-Dokument), geben Sie jedes Wort durch ein Komma getrennt ein. Verwenden Sie für Ausdrücke mit zwei oder mehr Wörtern Anführungszeichen um den Ausdruck. Jedes Wort oder jede Phrase, die Sie eingeben, wird separat angewendet (nur ein Wort muss gelten, damit die Richtlinie auf die Anlage angewendet wird). Weitere Informationen zum Eingeben von Wörtern oder Ausdrücken finden Sie im nächsten Abschnitt [Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords).|
| **Attachment ist einer der folgenden Dateitypen**  <br><br> **Attachment ist keiner dieser Dateitypen** | Geben Sie die Dateierweiterungen ein (beispielsweise. exe oder. pdf), um die Kommunikation zu überwachen, die bestimmte Anlagentypen einschließen oder ausschließen. Wenn Sie mehrere Dateierweiterungen einschließen oder ausschließen möchten, geben Sie diese in separaten Zeilen ein. Nur eine Anlagenerweiterung muss übereinstimmen, damit die Richtlinie angewendet wird.|
| **Nachricht ist größer als**  <br><br> **Die Nachrichtengröße ist nicht größer als** | Zum Überprüfen von Nachrichten, die auf einer bestimmten Größe basieren, verwenden Sie diese Bedingungen, um die maximale oder minimale Größe einer Nachricht anzugeben, bevor Sie überprüft werden kann. Wenn Sie beispielsweise angeben, dass die **Nachrichtengröße größer als** \> **1,0 MB**ist, werden alle Nachrichten mit einer Größe von 1,01 MB überprüft. Sie können Byte, Kilobyte, Megabyte oder Gigabyte für diese Bedingung auswählen.|
| **Anlage ist größer als**  <br><br> **Die Anlage ist nicht größer als** | Um Nachrichten anhand der Größe Ihrer Anlagen zu überprüfen, geben Sie die maximale oder minimale Größe an, die eine Anlage sein kann, bevor die Nachricht und ihre Anlagen überprüft werden können. Wenn Sie beispielsweise **Attachment größer als** \> **2,0 MB**angeben, werden alle Nachrichten mit Anlagen von 2,01 MB und mehr überprüft. Sie können Byte, Kilobyte, Megabyte oder Gigabyte für diese Bedingung auswählen.|
   
#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Übereinstimmende Wörter und Ausdrücke in E-Mails oder Anlagen
<a name="Matchwords"> </a>

Jedes Wort, das Sie eingeben und mit einem Komma trennen, wird separat angewendet (nur ein Wort muss gelten, damit die Richtlinienbedingung auf die e-Mail oder Anlage angewendet wird). Verwenden wir beispielsweise die Bedingung, **Nachricht enthält eines dieser Wörter**, wobei die Schlüsselwörter "Banker", "vertraulich" und "Insiderhandel" durch ein Komma getrennt sind (Banker, Confidential, "Insiderhandel"). Die Richtlinie gilt für alle Nachrichten, die das Wort "Banker", "vertraulich" oder den Ausdruck "Insiderhandel" enthalten. Nur eins der Wörter oder einer der Ausdrücke muss vorkommen, damit die Richtlinienbedingung zutrifft. Wörter in der Nachricht oder Anlage müssen genau übereinstimmen, die Sie eingeben.

>[!IMPORTANT]
>Wenn Sie eine benutzerdefinierte Wörterbuchdatei importieren, muss jedes Wort oder jeder Ausdruck mit einem Wagenrücklauf und in einer separaten Zeilen getrennt werden. <br> Beispiel: <br><br>
>*Banker* <br>
>*vertraulich* <br>
>*Insiderhandel*

Zum Überprüfen von e-Mail-Nachrichten und Anlagen für dieselben Stichwörter erstellen Sie eine [Richtlinie zur Verhinderung von Datenverlust](create-test-tune-dlp-policy.md) mit einem [benutzerdefinierten Stichwort Wörterbuch](create-a-keyword-dictionary.md) für die Begriffe, die Sie in Nachrichten überprüfen möchten. Diese Richtlinienkonfiguration identifiziert definierte Schlüsselwörter, die entweder in der e-Mail-Nachricht **oder** in der e-Mail-Anlage angezeigt werden. Verwenden der standardmäßigen bedingten Richtlinieneinstellungen (*Nachricht enthält* eines dieser Wörter, und *Attachment enthält*eines dieser Wörter) um Begriffe in Nachrichten und Anlagen zu identifizieren, müssen die Begriffe **sowohl** in der Nachricht als auch in der Anlage vorhanden sein.
  
#### <a name="enter-multiple-conditions"></a>Eingeben mehrerer Bedingungen

Wenn Sie mehrere Bedingungen eingeben, verwendet Microsoft 365 alle Bedingungen zusammen, um zu bestimmen, wann die Kommunikations Konformitätsrichtlinie auf Kommunikationselemente angewendet werden soll. Wenn Sie mehrere Bedingungen einrichten, müssen alle Bedingungen erfüllt sein, damit die Richtlinie angewendet werden kann, es sei denn, Sie geben eine Ausnahme ein. Sie benötigen beispielsweise eine Richtlinie, die gilt, wenn eine Nachricht das Wort "Trade" enthält und größer als 2 MB ist. Wenn die Nachricht jedoch auch die Wörter "von Contoso Financial genehmigt" enthält, sollte die Richtlinie nicht angewendet werden. In diesem Beispiel wären die drei Bedingungen wie folgt definiert:
  
- **Nachricht enthält eines dieser Wörter**mit dem Stichwort "Trade"
- Die **Nachrichtengröße ist größer als**, mit dem Wert 2 MB
- **Nachricht enthält keines dieser Wörter**, mit den Schlüsselwörtern "genehmigt von Contoso Financial Team"

### <a name="review-percentage"></a>Überprüfen des Prozentsatzes

Wenn Sie die zu überprüfende Menge an Inhalten reduzieren möchten, können Sie einen Prozentsatz der gesamten Kommunikation angeben, die durch eine Kommunikations Konformitätsrichtlinie geregelt wird. Eine zufällige Stichprobe von Inhalten wird in Echtzeit aus dem Gesamtprozentsatz der Inhalte ausgewählt, die den gewählten Richtlinienbedingungen entsprechen. Wenn Sie möchten, dass Prüfer alle Elemente prüfen, können Sie in einer Richtlinie zur Kommunikationscompliance **100 %** konfigurieren.

## <a name="privacy-preview"></a>Datenschutz (Vorschau)

Der Schutz der Privatsphäre von Benutzern mit Richtlinien Übereinstimmungen ist wichtig und kann zur Förderung der Objektivität bei Daten Ermittlungs-und Analyse Überprüfungen für Benachrichtigungen zur Kommunikations Konformität beitragen. Diese Einstellung gilt nur für Benutzernamen, die die Lösung für die Kommunikations Kompatibilität angezeigt haben. Es wirkt sich nicht auf die Anzeige von Namen in anderen Compliance-Lösungen oder Admin Center aus.

Für Benutzer mit einer Übereinstimmung mit Kommunikations Kompatibilität können Sie in den Einstellungen für die **Kommunikations Kompatibilität**eine der folgenden Einstellungen auswählen:

- **Anonyme Versionen von**Benutzernamen anzeigen: Benutzernamen werden anonymisiert, um zu verhindern, dass Administratoren, Analysten, Daten Ermittler und Bearbeiter sehen, wem die Richtlinienwarnungen zugeordnet sind. Beispielsweise würde ein Benutzer "Grace Taylor" mit einem randomisierten Pseudonym wie "AnonIS8-988" in allen Bereichen der Kommunikations Konformitäts Erfahrung angezeigt. Wenn Sie diese Einstellung wählen, werden alle Benutzer mit aktuellen und früheren Richtlinienübereinstimmungen anonymisiert und gelten für alle Richtlinien. Benutzerprofilinformationen in den Benachrichtigungsdetails zur Kommunikations Konformität sind nicht verfügbar, wenn diese Option ausgewählt wird. Benutzernamen werden jedoch beim Hinzufügen neuer Benutzer zu vorhandenen Richtlinien oder beim Zuweisen von Benutzern zu neuen Richtlinien angezeigt. Wenn Sie diese Einstellung deaktivieren, werden Benutzernamen für alle Benutzer angezeigt, die aktuelle oder vergangene Richtlinien Übereinstimmungen aufweisen.
- **Anonyme Versionen von Benutzernamen nicht anzeigen**: Benutzernamen werden für alle aktuellen und letzten Richtlinien Übereinstimmungen für Benachrichtigungen zur Kommunikations Konformität angezeigt. Benutzerprofilinformationen (Name, Titel, Alias und Organisation oder Abteilung) werden für den Benutzer für alle Benachrichtigungen zur Kommunikations Konformität angezeigt.

## <a name="notice-templates"></a>Benachrichtigungsvorlagen

Sie können Benachrichtigungsvorlagen erstellen, wenn Sie Benutzern eine e-Mail-Erinnerungs Benachrichtigung für Richtlinien Übereinstimmungen als Teil des Problem Lösungsprozesses senden möchten. Benachrichtigungen können nur an die e-Mail-Adresse des Benutzers gesendet werden, die der Richtlinienübereinstimmung zugeordnet ist, die die spezifische Warnung zur Behebung generiert hat. Wenn Sie eine Benachrichtigungsvorlage auswählen, die auf eine Richtlinienverletzung als Teil des Korrektur Workflows angewendet werden soll, können Sie die in der Vorlage definierten Feldwerte akzeptieren oder die Felder bei Bedarf überschreiben.

Notices-Vorlagen sind benutzerdefinierte e-Mail-Vorlagen, in denen Sie die folgenden Nachrichtenfelder im Bereich **Kommunikations Kompatibilitätseinstellungen** definieren können:

|**Feld**|**Required**| **Details** |
|:-----|:-----|:-----|
|**Vorlagenname** | Ja | Anzeigename für die Notizvorlage, die Sie im Benachrichtigungs Workflow während der Wiederherstellung auswählen, unterstützt Textzeichen. |
| **Absenderadresse** | Ja | Die Adresse von einem oder mehreren Benutzern oder Gruppen, die die Nachricht mit einer Richtlinienübereinstimmung an den Benutzer senden, ausgewählt aus dem Active Directory für Ihr Abonnement. |
| **CC-und Bcc-Adressen** | Nein | Optionale Benutzer oder Gruppen, die über die Richtlinienübereinstimmung benachrichtigt werden sollen, ausgewählt aus dem Active Directory für Ihr Abonnement. |
| **Betreff** | Ja | Informationen, die in der Betreffzeile der Nachricht angezeigt werden, unterstützen Textzeichen. |
| **Nachrichtentext** | Ja | Informationen, die im Nachrichtentext angezeigt werden, unterstützen Text-oder HTML-Werte. |

### <a name="html-for-notices"></a>HTML für Benachrichtigungen

Wenn Sie mehr als eine einfache textbasierte e-Mail-Nachricht für Benachrichtigungen erstellen möchten, können Sie eine ausführlichere Meldung mithilfe von HTML im Feld Nachrichtentext einer Notizvorlage erstellen. Im folgenden Beispiel wird das Nachrichtentextformat für eine grundlegende HTML-basierte e-Mail-Benachrichtigungsvorlage bereitgestellt:

```HTML
<!DOCTYPE html>
<html>
    <body>
        <h2>Action Required: Contoso Employee Code of Conduct Policy Training</h2>
        <p>A recent message you've sent has generated a policy alert for the Contoso Employee <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
        <p>You are required to attend the Contoso Employee Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
        <p>Thank you,</p>
        <p><em>Human Resources</em></p>
    </body>
</html>
```

>[!NOTE]
>Die HTML-href-Attribut Implementierung in den Benachrichtigungsvorlagen für die Kommunikations Konformität unterstützt derzeit nur einfache Anführungszeichen anstelle von doppelten Anführungszeichen für URL-Verweise.

## <a name="filters"></a>Filter

Mit den Kommunikations Kompatibilitäts filtern können Sie Warnmeldungen für schnellere Untersuchungen und Korrekturaktionen Filtern und sortieren. Die Filterung steht auf den Registerkarten **Ausstehend** und **aufgelöst** für jede Richtlinie zur Verfügung. Zum Speichern eines Filters oder Filtersatzes als gespeicherte Filterabfrage müssen mindestens ein Wert als Filterauswahl konfiguriert werden. In der folgenden Tabelle sind die Filterdetails aufgeführt:

|**Filter**|**Details**|
|:-----|:-----|
| **Date** | Das Datum, an dem die Nachricht von einem Benutzer in Ihrer Organisation gesendet oder empfangen wurde. Wenn Sie einen einzelnen Tag filtern möchten, wählen Sie einen Datumsbereich aus, der mit dem Tag beginnt, für den Sie Ergebnisse erhalten möchten, und beenden Sie den folgenden Tag. Wenn Sie beispielsweise Ergebnisse für 9/20/2020 Filtern wollten, wählen Sie einen Filter Datumsbereich von 9/20/2020-9/21/2020 aus.|
| **File-Klasse** | Die Klasse der Nachricht auf der Grundlage des Nachrichtentyps, entweder *Nachricht* oder *Anlage*. |
| **Weist eine Anlage auf** | Das Attachment-vorhanden sein in der Nachricht. |
| **Elementklasse** | Die Quelle der Nachricht basierend auf dem Nachrichtentyp, e-Mail, Microsoft Team Chat, Bloomberg usw. Weitere Informationen zu allgemeinen Elementtypen und Nachrichtenklassen finden Sie unter [Elementtypen und Nachrichtenklassen](https://docs.microsoft.com/office/vba/outlook/concepts/forms/item-types-and-message-classes). |
| **Empfängerdomänen** | Die Domäne, an die die Nachricht gesendet wurde. Diese Domäne ist normalerweise Ihre Microsoft 365-Abonnement Domäne standardmäßig. |
| **Empfänger** | Der Benutzer, an den die Nachricht gesendet wurde. |
| **Sender** | Die Person, die die Nachricht gesendet hat. |
| **Absenderdomäne** | Die Domäne, die die Nachricht gesendet hat. |
| **Size** | Die Größe der Nachricht in KB. |
| **Betreff/Titel** | Der Nachrichtenbetreff oder der Chat Titel. |
| **Tags** | Die einer Nachricht zugewiesenen Tags, entweder *fragwürdig*, *kompatibel*oder *nicht kompatibel*. |
| **Eskaliert an** | Der Benutzername der Person, die im Rahmen einer Nachrichten Eskalations Aktion enthalten ist. |
| **Klassifizierungen** | Der Name der integrierten und benutzerdefinierten Klassifizierungen, die auf die Nachricht angewendet werden. Einige Beispiele sind *beleidigende Sprache*, *gezielte Belästigung*, *Profanität*, *Bedrohung*und vieles mehr.

## <a name="alert-policies"></a>Warnungsrichtlinien

Nachdem Sie eine Richtlinie konfiguriert haben, wird automatisch eine entsprechende Warnungs Richtlinie erstellt, und Warnungen werden für Nachrichten generiert, die die in der Richtlinie definierten Bedingungen erfüllen. Standardmäßig wird für alle Richtlinien Übereinstimmungen Warnungsauslöser ein Schweregrad von Medium in der zugeordneten Warnungs Richtlinie zugewiesen. Warnungen werden für eine Kommunikations Konformitätsrichtlinie generiert, nachdem die Schwellenwertstufe Aggregations Auslöser in der zugeordneten Warnungs Richtlinie erfüllt ist.

Für Kommunikations Konformitätsrichtlinien sind die folgenden Warnungsrichtlinien Werte standardmäßig konfiguriert:

|**Warnungsrichtlinien Auslöser**|**Standardwert**|
|:-----|:-----|
| Aggregation | Einfache Aggregation |
| Schwellenwert | 4 Aktivitäten |
| Fenster | 60 Minuten |

>[!Note]
>Die Einstellungen für den Warnungsrichtlinien Schwellenwert für Aktivitäten unterstützen einen Mindestwert von 3 oder höher für Kommunikationsrichtlinien.

Sie können die Standardeinstellungen für Auslöser für die Anzahl der Aktivitäten, den Zeitraum für die Aktivitäten und für bestimmte Benutzer in Warnungsrichtlinien auf der Seite **Warnungsrichtlinien** im Security & Compliance Center ändern.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Ändern des Schweregrads für eine Warnungs Richtlinie

Wenn Sie den in einer Warnungs Richtlinie für eine bestimmte Kommunikations Konformitätsrichtlinie zugewiesenen Schweregrad ändern möchten, führen Sie die folgenden Schritte aus:

1. Melden [https://compliance.microsoft.com](https://compliance.microsoft.com) Sie sich mit Anmeldeinformationen für ein Administratorkonto in Ihrer Microsoft 365-Organisation an.

2. Wechseln Sie im Microsoft 365 Compliance Center zu **Richtlinien**.

3. Wählen Sie auf der Seite **Richtlinien** **Office 365 Benachrichtigung** aus, um die Seite **Warnungsrichtlinien** im **Office 365 Security & Compliance Center**zu öffnen.

4. Aktivieren Sie das Kontrollkästchen für die Kommunikations Konformitätsrichtlinie, die Sie aktualisieren möchten, und wählen Sie dann **Richtlinie bearbeiten**aus.

5. Wählen Sie auf der Registerkarte **Beschreibung** das Dropdownfeld **Schweregrad** aus, um die Richtlinien Warnstufe zu konfigurieren.

6. Wählen Sie **Speichern** aus, um den neuen Schweregrad auf die Richtlinie anzuwenden.

7. Wählen Sie **Schließen** aus, um die Seite Warnungsrichtlinien Details zu beenden.

## <a name="power-automate-flows-preview"></a>Power Automation Flows (Vorschau)

[Microsoft Power Automation](https://docs.microsoft.com/power-automate/getting-started) ist ein Workflowdienst, der Aktionen zwischen Anwendungen und Diensten automatisiert. Durch die Verwendung von Flows aus Vorlagen oder manuell erstellt, können Sie allgemeine Aufgaben automatisieren, die mit diesen Anwendungen und Diensten verbunden sind. Wenn Sie Power Automation Flows für die Kommunikations Konformität aktivieren, können Sie wichtige Aufgaben für Warnungen und Benutzer automatisieren. Sie können Power-Automatisierungs Flüsse so konfigurieren, dass Vorgesetzte benachrichtigt werden, wenn Benutzer über Kommunikations Konformitäts Benachrichtigungen und andere Anwendungen verfügen.

Kunden mit Microsoft 365-Abonnements, die die Kompatibilität mit der Kommunikation einbeziehen, benötigen keine zusätzlichen Power-Automatisierungs Lizenzen, um die empfohlene standardmäßige Kommunikations Kompatibilitäts Power-Automatisierungs Vorlage zu verwenden. Die Standardvorlage kann angepasst werden, um Ihre Organisation zu unterstützen und die wichtigsten Szenarien für die Kommunikations Konformität zu behandeln. Wenn Sie sich für die Verwendung von Premium Power Automation-Funktionen in diesen Vorlagen entscheiden, eine benutzerdefinierte Vorlage mit dem Microsoft 365-Konformitäts-Konnektor erstellen oder Power automatisieren-Vorlagen für andere Kompatibilitäts Bereiche in Microsoft 365 verwenden, benötigen Sie möglicherweise zusätzliche Power automatisieren-Lizenzen.

![Kommunikation Compliance Power automatisieren](../media/communication-compliance-power-automate.png)

Die folgende Power-Automatisierungs Vorlage wird Kunden zur Unterstützung der Prozessautomatisierung für Kommunikationsrichtlinien Warnungen bereitgestellt:

- Benachrichtigungs **-Manager, wenn ein Benutzer über eine Benachrichtigung über die Kommunikations Konformität verfügt**: einige Organisationen müssen möglicherweise eine sofortige Verwaltungs Benachrichtigung erhalten, wenn ein Benutzer über eine Benachrichtigung über die Kommunikations Konformität verfügt. Wenn dieser Ablauf konfiguriert und ausgewählt ist, wird dem Manager für den Fall Benutzer eine e-Mail-Nachricht mit den folgenden Informationen zu allen Warnungen gesendet:
    - Zutreffende Richtlinie für die Warnung
    - Datum/Uhrzeit der Warnung
    - Schweregrad der Warnung

### <a name="create-a-power-automate-flow"></a>Erstellen eines Power-Automatisierungs Flusses

Um einen Power-Automatisierungs Fluss aus einer empfohlenen Standardvorlage zu erstellen, verwenden Sie die Option **Power Automation** Flows verwalten aus dem **Automatisierungs** Steuerelement, wenn Sie direkt in einer Warnung arbeiten. Zum Erstellen eines Power-Automatisierungs Flusses mit **Power-Automatisierungs Fluss verwalten**müssen Sie Mitglied mindestens einer Rollengruppe für die Kommunikations Kompatibilität sein.

Führen Sie die folgenden Schritte aus, um einen Power-Automatisierungs Fluss aus einer Standardvorlage zu erstellen:

1. Wechseln Sie im Microsoft 365 Compliance Center zu **Compliance**  >  -**Richtlinien** für Kommunikation, und wählen Sie die Richtlinie mit der Warnung aus, die Sie überprüfen möchten.
2. Wählen Sie in der Richtlinie die Registerkarte **Ausstehend** aus, und wählen Sie eine ausstehende Warnung aus.
3. Wählen Sie im Menü Benachrichtigungsaktion die Option **Power Automation** aus.
4. Wählen Sie auf der Seite **Power automatisieren** eine Standardvorlage aus den Abschnitt **Kommunikations Kompatibilitäts Vorlagen** aus, die Sie auf der Seite mögen.
5. Der Flow listet die für den Fluss erforderlichen eingebetteten Verbindungen auf und wird angezeigt, wenn die Verbindungsstatus verfügbar sind. Aktualisieren Sie bei Bedarf alle Verbindungen, die nicht als verfügbar angezeigt werden. Wählen Sie **weiter**aus.
6. Standardmäßig sind die empfohlenen Flows mit den empfohlenen Kommunikationsrichtlinien und den Microsoft 365-Dienst Datenfeldern vorkonfiguriert, die zum Abschließen der zugewiesenen Aufgabe für den Fluss erforderlich sind. Passen Sie bei Bedarf die Fluss Komponenten mithilfe des Steuerelements " **Erweiterte Optionen anzeigen** " und Konfigurieren der verfügbaren Eigenschaften für die Fluss Komponente an.
7. Fügen Sie bei Bedarf zusätzliche Schritte zum Ablauf hinzu, indem Sie die Schaltfläche **neuer Schritt** auswählen. In den meisten Fällen sollte diese Änderung für die empfohlenen Standardvorlagen nicht erforderlich sein.
8. Wählen Sie **Entwurf speichern** aus, um den Fluss zur späteren Konfiguration zu speichern, oder wählen Sie **Speichern** aus, um die Konfiguration für den Fluss abzuschließen.
9. Wählen Sie **Schließen** aus, um zur Seite Power Automation Flow zurückzukehren. Die neue Vorlage wird auf der Registerkarte **meine Abläufe** als Fluss aufgeführt und ist automatisch über das Power Automation-Steuerelement für den Benutzer verfügbar, der den Fluss beim Arbeiten mit Kommunikations Konformitätswarnungen erstellt hat.

### <a name="share-a-power-automate-flow"></a>Freigeben eines Power-Automatisierungs Flusses

Standardmäßig sind Power Automation Flows, die von einem Benutzer erstellt werden, nur für diesen Benutzer verfügbar. Damit andere Benutzer der Kommunikations Konformität Zugriff haben und einen Fluss verwenden können, muss der Fluss vom Flow Creator gemeinsam verwendet werden. Um einen Fluss freizugeben, verwenden Sie das **Power Automation** -Steuerelement, wenn Sie direkt in einer Warnung arbeiten.

Zum Freigeben eines Power-Automatisierungs Flusses müssen Sie Mitglied mindestens einer Rollengruppe für die Kommunikations Kompatibilität sein.
Führen Sie die folgenden Schritte aus, um einen Power-Automatisierungs Fluss freizugeben:

1. Wechseln Sie im Microsoft 365 Compliance Center zu **Compliance**  >  -**Richtlinien** für Kommunikation, und wählen Sie die Richtlinie mit der Warnung aus, die Sie überprüfen möchten.
2. Wählen Sie in der Richtlinie die Registerkarte **Ausstehend** aus, und wählen Sie eine ausstehende Warnung aus.
3. Wählen Sie im Menü Benachrichtigungsaktion die Option **Power Automation** aus.
4. Wählen Sie auf der Seite **Power Automation Flows** die Registerkarte **meine Flows** oder **Team Flows** aus.
5. Wählen Sie den freizugebenden Fluss aus, und wählen Sie dann im Menü Fluss Optionen die Option **Freigeben** aus.
6. Geben Sie auf der Seite Fluss Freigabe den Namen des Benutzers oder der Gruppe ein, den Sie als Besitzer für den Datenfluss hinzufügen möchten.
7. Wählen Sie im Dialogfeld **Verbindung verwendet** die Option **OK** aus, um zu bestätigen, dass der hinzugefügte Benutzer oder die Gruppe Vollzugriff auf den Fluss haben wird.

### <a name="edit-a-power-automate-flow"></a>Bearbeiten eines Power-Automatisierungs Flusses

Wenn Sie einen Fluss bearbeiten müssen, verwenden Sie das **Power Automation** -Steuerelement, wenn Sie direkt in einer Warnung arbeiten. Zum Bearbeiten eines Power-Automatisierungs Flusses müssen Sie Mitglied mindestens einer Rollengruppe für die Kommunikations Kompatibilität sein.

Führen Sie die folgenden Schritte aus, um einen Power-Automatisierungs Fluss zu bearbeiten:

1. Wechseln Sie im Microsoft 365 Compliance Center zu **Compliance**  >  -**Richtlinien** für Kommunikation, und wählen Sie die Richtlinie mit der Warnung aus, die Sie überprüfen möchten.
2. Wählen Sie in der Richtlinie die Registerkarte **Ausstehend** aus, und wählen Sie eine ausstehende Warnung aus.
3. Wählen Sie im Menü Benachrichtigungsaktion die Option **Power Automation** aus.
4. Wählen Sie auf der Seite **Strom Automatisierungs Flüsse** auswählen den zu bearbeitenden Fluss aus. Wählen Sie im Menü Flusssteuerung die Option **Bearbeiten** aus.
5. Wählen Sie die **Auslassungs**  >  **Einstellungen** aus, um eine Fluss Komponenteneinstellung zu ändern, oder **Auslassungs**Punkte  >  **Löschen** , um eine Fluss Komponente zu löschen.
6. Klicken Sie auf **Speichern** und dann auf **Schließen** , um die Bearbeitung des Flusses abzuschließen.

### <a name="delete-a-power-automate-flow"></a>Löschen eines Power-Automatisierungs Flusses

Wenn Sie einen Fluss löschen müssen, verwenden Sie das **Power Automation** -Steuerelement, wenn Sie direkt in einer Warnung arbeiten. Zum Löschen eines Power-Automatisierungs Flusses müssen Sie Mitglied mindestens einer Rollengruppe für die Kommunikations Kompatibilität sein.

Führen Sie die folgenden Schritte aus, um einen Power-Automatisierungs Fluss zu löschen:

1. Wechseln Sie im Microsoft 365 Compliance Center zu **Compliance**  >  -**Richtlinien** für Kommunikation, und wählen Sie die Richtlinie mit der Warnung aus, die Sie überprüfen möchten.
2. Wählen Sie in der Richtlinie die Registerkarte **Ausstehend** aus, und wählen Sie eine ausstehende Warnung aus.
3. Wählen Sie im Menü Benachrichtigungsaktion die Option **Power Automation** aus.
4. Wählen Sie auf der Seite **Strom Automatisierungs Flüsse** auswählen den zu löschenden Fluss aus. Wählen Sie im Menü Flusssteuerung die Option **Löschen** aus.
5. Wählen Sie im Dialogfeld Löschbestätigung die Option **Löschen** aus, um den Fluss zu entfernen, oder wählen Sie **Abbrechen** aus, um die Löschaktion zu beenden.

## <a name="reports-preview"></a>Berichte (Vorschau)

Das Dashboard für neue **Berichte** ist der zentrale Ort zum Anzeigen aller Kompatibilitätsberichte für die Kommunikation. Berichts-Widgets bieten eine schnelle Übersicht über die am häufigsten benötigten Einblicke für eine Gesamtbewertung des Status von Kommunikations Compliance-Aktivitäten. In den Berichts-Widgets enthaltene Informationen sind nicht exportierbar. Detaillierte Berichte bieten ausführliche Informationen zu bestimmten Bereichen der Kommunikations Konformität und bieten die Möglichkeit zum Filtern, gruppieren, Sortieren und Exportieren von Informationen bei der Überprüfung.

Das **Dashboard Berichte** enthält die folgenden Berichts-Widgets und Links zu detaillierten Berichten:

- **Aktuelle Richtlinie entspricht** Widget: zeigt die Anzahl der Übereinstimmungen mit aktiver Richtlinie im Zeitverlauf an.
- **Auflösen von Elementen nach Richtlinie** Widget: zeigt die Anzahl von Richtlinien Übereinstimmungs Benachrichtigungen an, die über einen Zeitraum nach Richtlinien aufgelöst werden.
- **Benutzer mit dem meisten Richtlinien Übereinstimmungs** Widget: zeigt die Benutzer (oder anonymisierten Benutzernamen) und die Anzahl der Richtlinien Übereinstimmungen für einen bestimmten Zeitraum an.
- **Richtlinie mit den meisten Übereinstimmungen** Widget: zeigt die Richtlinien und die Anzahl der Übereinstimmungen für einen bestimmten Zeitraum an, der für Übereinstimmungen am höchsten und am niedrigsten ist.
- **Eskalationen nach Richtlinien** Widget: zeigt die Anzahl der Eskalationen pro Richtlinie in einem bestimmten Zeitraum an.
- **Richtlinieneinstellungen und Status** detaillierter Bericht: bietet einen detaillierten Überblick über die Richtlinienkonfiguration und-Einstellungen sowie den allgemeinen Status der einzelnen Richtlinien (Übereinstimmungen und Aktionen) für Nachrichten. Verwenden Sie die *Export* Option, um eine zu erstellen. CSV-Datei mit den Berichtsdetails.
- **Elemente und Aktionen pro Richtlinien** Detailbericht: überprüfen und Exportieren von übereinstimmenden Elementen und Korrekturaktionen pro Richtlinie. Verwenden Sie die *Export* Option, um eine zu erstellen. CSV-Datei mit den Berichtsdetails.
- **Element und Aktionen pro Standort** detaillierter Bericht: überprüfen und Exportieren von übereinstimmenden Elementen und Korrekturaktionen pro Microsoft 365-Standort. Verwenden Sie die *Export* Option, um eine zu erstellen. CSV-Datei mit den Berichtsdetails.

## <a name="audit"></a>Überwachung

In einigen Fällen müssen Sie Aufsichtsbehörden oder Compliance-Prüfern Informationen bereitstellen, um die Überwachung der Benutzeraktivitäten und der Kommunikation zu überprüfen. Bei diesen Informationen kann es sich um eine Zusammenfassung aller Aktivitäten handeln, die mit einer definierten Organisationsrichtlinie verknüpft sind, oder wenn sich eine Kommunikations Konformitätsrichtlinie ändert. Kommunikations Konformitätsrichtlinien verfügen über integrierte Überwachungspfade für die vollständige Bereitstellung interner oder externer Überprüfungen. Detaillierte Überwachungs Verläufe jeder Aktion zum Erstellen, bearbeiten und löschen werden von ihren Kommunikationsrichtlinien erfasst, um einen Nachweis der Aufsichtsverfahren zu ermöglichen.

>[!Important]
>Die Überwachung muss für Ihre Organisation aktiviert werden, bevor Kommunikations kompatibilitätsereignisse aufgezeichnet werden. Informationen zum Aktivieren der Überwachung finden Sie unter [Aktivieren des Überwachungsprotokolls](communication-compliance-configure.md#step-2-required-enable-the-audit-log).

Wählen Sie zum Anzeigen von Updateaktivitäten für die Kommunikationsrichtlinien Aktualisierung auf der Hauptseite für eine Richtlinie das Steuerelement **Export Richtlinienupdates** aus. Sie müssen den *globalen* Administrator-oder *Kommunikationsrichtlinien-Administrator* Rollen zugewiesen sein, um Aktualisierungsaktivitäten zu exportieren. Mit dieser Aktion wird eine Überwachungsdatei im CSV-Format generiert, die die folgenden Informationen enthält:

|**Feld**|**Details**|
|:-----|:-----|
| **CreationDate** | Das Datum, an dem die Update Aktivität in einer Richtlinie ausgeführt wurde. |
| **UserIds** | Der Benutzer, der die Aktualisierungsaktivität in einer Richtlinie ausgeführt hat. |
| **Operations** | Die für die Richtlinie ausgeführten Aktualisierungsvorgänge. |
| **Auditdata** | Dieses Feld ist die Hauptdatenquelle für alle Richtlinien Aktualisierungsaktivitäten. Alle Updateaktivitäten werden aufgezeichnet und durch Kommatrennzeichen getrennt. |

Zum **Anzeigen der Aktivitäten** zur Kommunikation-Konformitätsüberprüfung für eine Richtlinie wählen Sie auf der Übersichtsseite für eine bestimmte Richtlinie das Steuerelement zum **Überprüfen von Aktivitäten exportieren** aus. Sie müssen über die Administratorrollen für den *globalen Administrator* oder die *Kommunikations Konformität* verfügen, um Prüfungsaktivitäten zu exportieren. Mit dieser Aktion wird eine Überwachungsdatei im CSV-Format generiert, die die folgenden Informationen enthält:

|**Feld**|**Details**|
|:-----|:-----|
| **CreationDate** | Das Datum, an dem die Überprüfungsaktivität in einer Richtlinie ausgeführt wurde. |
| **UserIds** | Der Benutzer, der die Überprüfungsaktivität in einer Richtlinie ausgeführt hat. |
| **Operations** | Die für die Richtlinie ausgeführten Überprüfungsvorgänge. |
| **Auditdata** | Dieses Feld ist die Hauptdatenquelle für alle Aktivitäten zur Richtlinienüberprüfung. Alle Prüfaktivitäten werden aufgezeichnet und durch Kommatrennzeichen getrennt. |

Sie können auch Überwachungsaktivitäten im einheitlichen Überwachungsprotokoll oder mit dem PowerShell [-Cmdlet Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) anzeigen.

Im folgenden Beispiel werden die Aktivitäten für alle Aufsichts Überprüfungsaktivitäten (Richtlinien und Regeln) zurückgegeben:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

In diesem Beispiel werden die Updateaktivitäten für Ihre Richtlinien für die Kommunikations Konformität zurückgegeben:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

## <a name="ready-to-get-started"></a>Sind Sie bereit loszulegen?

Informationen zum Konfigurieren der Kommunikations Kompatibilität für Ihre Microsoft 365-Organisation finden Sie unter [configure Communication Compliance for your Microsoft 365 Organization](communication-compliance-configure.md).
