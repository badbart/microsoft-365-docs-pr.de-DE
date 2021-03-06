---
title: Definieren von Richtlinien für Informationsbarrieren
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: None
description: Hier erfahren Sie, wie Sie Richtlinien für Informationsbarrieren in Microsoft Teams definieren.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dcf7fd496098032bad075c1679f0081ddf29caef
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "47547443"
---
# <a name="define-information-barrier-policies"></a>Definieren von Richtlinien für Informationsbarrieren

Mit Informationsbarrieren können Sie Richtlinien definieren, mit denen verhindert werden soll, dass bestimmte Segmente von Benutzern miteinander kommunizieren, oder dass bestimmte Segmente nur mit bestimmten anderen Segmenten kommunizieren dürfen. Richtlinien für Informationsbarrieren können Ihrem Unternehmen dabei helfen, die Einhaltung relevanter Branchenstandards und-Vorschriften beizubehalten und potenzielle Interessenkonflikte zu vermeiden. Weitere Informationen finden Sie unter [Information Barriers](information-barriers.md). 

In diesem Artikel wird beschrieben, wie Sie Richtlinien für Informationsbarrieren planen, definieren, implementieren und verwalten. Es sind mehrere Schritte beteiligt, und der Arbeitsfluss ist in mehrere Teile unterteilt. Stellen Sie sicher, dass Sie die [Voraussetzungen](#prerequisites) und den gesamten Prozess gelesen haben, bevor Sie mit dem definieren (oder bearbeiten) von Informations Sperrrichtlinien beginnen.

> [!TIP]
> Dieser Artikel enthält ein [Beispielszenario](#example-contosos-departments-segments-and-policies) und eine [herunterladbare Excel-Arbeitsmappe](https://github.com/MicrosoftDocs/OfficeDocs-O365SecComp/raw/public/SecurityCompliance/media/InfoBarriers-PowerShellGenerator.xlsx) , die Sie bei der Planung und Definition Ihrer Richtlinien für Informationsbarrieren unterstützt.

## <a name="concepts-of-information-barrier-policies"></a>Ansätze hinter Richtlinien für Informationsbarrieren

Wenn Sie Richtlinien für Informationsbarrieren definieren, arbeiten Sie mit Benutzerkonto Attributen, Segmenten, "blockieren" und/oder "zulassen"-Richtlinien und Richtlinienanwendung.

- Benutzerkontoattribute sind in Azure Active Directory (oder Exchange Online) definiert. Diese Attribute können Abteilung, Position, Standort, Teamname und andere Auftragsprofildetails umfassen. 

- Segmente sind Benutzergruppen, die im Security & Compliance Center mithilfe eines ausgewählten **Benutzerkontoattributs**definiert sind. (Siehe auch die [Liste der unterstützten Attribute](information-barriers-attributes.md).) 

- Mit Richtlinien für Kommunikationsbarrieren werden bestimmte Kommunikationsbeschränkungen festgelegt. Beim Definieren von Richtlinien für Informationsbarrieren können Sie aus zwei Arten von Richtlinien auswählen:
    - "Blockieren"-Richtlinien verhindern, dass ein Segment mit einem anderen Segment kommuniziert.
    - Mit den Richtlinien "zulassen" kann ein Segment nur mit bestimmten anderen Segmenten kommunizieren.

- Die Richtlinienanwendung erfolgt, nachdem alle Richtlinien für Kommunikationsbarrieren definiert wurden und Sie bereit sind, sie in Ihrer Organisation anzuwenden.

## <a name="the-work-flow-at-a-glance"></a>Der Workflow auf einen Blick

|Phase    |Was beteiligt ist  |
|---------|---------|
|[Stellen Sie sicher, dass die Voraussetzungen erfüllt sind](#prerequisites)     |-Stellen Sie sicher, dass Sie über die [erforderlichen Lizenzen und Berechtigungen](information-barriers.md#required-licenses-and-permissions) verfügen<br/>-Sicherstellen, dass Ihr Verzeichnisdaten für die Segmentierung von Benutzern enthält<br/>-Aktivieren der bereichsbezogenen Verzeichnissuche für Microsoft Teams<br/>-Stellen Sie sicher, dass die Überwachungsprotokollierung aktiviert ist.<br/>-Sicherstellen, dass keine Exchange-adressbuchrichtlinien vorhanden sind<br/>-Verwenden von PowerShell (Beispiele werden bereitgestellt)<br/>-Bereitstellen der Zustimmung des Administrators für Microsoft Teams (Schritte sind enthalten)          |
|[Teil 1: Segmentieren von Benutzern in Ihrer Organisation](#part-1-segment-users)     |-Bestimmen der erforderlichen Richtlinien<br/>-Eine Liste der zu definierenden Segmente erstellen<br/>-Bestimmen der zu verwendenden Attribute<br/>-Definieren von Segmenten in Bezug auf Richtlinienfilter        |
|[Abschnitt 2: Definieren von Richtlinien für Informationsbarrieren](#part-2-define-information-barrier-policies)     |-Definieren Ihrer Richtlinien (noch nicht gültig)<br/>-Auswählen aus zwei Arten (blockieren oder zulassen) |
|[Abschnitt 3: Anwenden von Richtlinien für Informationsbarrieren](#part-3-apply-information-barrier-policies)     |-Festlegen von Richtlinien auf aktiven Status<br/>-Ausführen der Richtlinienanwendung<br/>-Anzeigen des Richtlinienstatus         |
|(Nach Bedarf) [Bearbeiten eines Segments oder einer Richtlinie](information-barriers-edit-segments-policies.md)    |-Bearbeiten eines Segments<br/>-Bearbeiten oder Entfernen einer Richtlinie<br/>-Die Richtlinienanwendung erneut ausführen<br/>-Anzeigen des Richtlinienstatus         |
|(Nach Bedarf) [Problembehandlung](information-barriers-troubleshooting.md)|-Maßnahmen ergreifen, wenn die Dinge nicht wie erwartet funktionieren|

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie zusätzlich zu den [erforderlichen Lizenzen und Berechtigungen](information-barriers.md#required-licenses-and-permissions)sicher, dass die folgenden Anforderungen erfüllt sind: 
     
- Verzeichnisdaten – stellen Sie sicher, dass die Struktur Ihrer Organisation in Verzeichnisdaten widergespiegelt wird. Stellen Sie dazu sicher, dass die Attribute des Benutzerkontos wie Gruppenmitgliedschaft, Abteilungsname usw. ordnungsgemäß in Azure Active Directory (oder Exchange Online) aufgefüllt werden. Weitere Informationen hierzu finden Sie in den folgenden Ressourcen:
  - [Attribute für Richtlinien für Informationsbarrieren](information-barriers-attributes.md)
  - [Hinzufügen oder Aktualisieren der Profilinformationen eines Benutzers mithilfe von Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Konfigurieren von Eigenschaften eines Benutzerkontos mit Office 365 PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/configure-user-account-properties-with-microsoft-365-powershell)

- Bereichsbezogene Verzeichnissuche – bevor Sie die erste Informations Sperrrichtlinie Ihrer Organisation definieren, müssen Sie die [bereichsbezogene Verzeichnissuche in Microsoft Teams aktivieren](https://docs.microsoft.com/MicrosoftTeams/teams-scoped-directory-search). Warten Sie mindestens 24 Stunden nach dem Aktivieren der bereichsbezogenen Verzeichnissuche, bevor Sie Richtlinien für Informationsbarrieren einrichten oder definieren.

- Überwachungsprotokollierung – um den Status einer Richtlinienanwendung nachzuschlagen, muss die Überwachungsprotokollierung aktiviert sein. Dies wird empfohlen, bevor Sie mit dem Definieren von Segmenten oder Richtlinien beginnen. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Überwachungsprotokoll Suche](turn-audit-log-search-on-or-off.md).

- Keine adressbuchrichtlinien – stellen Sie vor dem definieren und Anwenden von Richtlinien für Informationsbarrieren sicher, dass keine Exchange-adressbuchrichtlinien vorhanden sind. Informationsbarrieren basieren auf der Adressbuchrichtlinien, aber die beiden Arten von Richtlinien sind nicht kompatibel. Wenn Sie solche Richtlinien verwenden, müssen Sie zuerst [Ihre adressbuchrichtlinien entfernen](https://docs.microsoft.com/exchange/address-books/address-book-policies/remove-an-address-book-policy) . Sobald Richtlinien für Informationsbarrieren aktiviert sind und das hierarchische Adressbuch aktiviert ist, werden alle Benutzer, die nicht in einem Segment mit Informationsbarrieren ***enthalten sind*** , das [hierarchische Adressbuch](https://docs.microsoft.com/exchange/address-books/hierarchical-address-books/hierarchical-address-books) in Exchange Online sehen.

- PowerShell – derzeit werden Richtlinien für Informationsbarrieren im Office 365 Security & Compliance Center mithilfe von PowerShell-Cmdlets definiert und verwaltet. In diesem Artikel werden zwar einige Beispiele bereitgestellt, aber Sie müssen mit PowerShell-Cmdlets und-Parametern vertraut sein. Außerdem benötigen Sie das Azure PowerShell-Modul.
    - [Herstellen einer Verbindung mit Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell)
    - [Installieren des Azure PowerShell-Moduls](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-2.3.2)

- Zustimmung des Administrators für Informationsbarrieren in Microsoft Teams – Wenn Ihre Richtlinien vorhanden sind, können Informationsbarrieren Personen aus Chatsitzungen entfernen, in denen Sie sich nicht befinden sollen. Dadurch wird sichergestellt, dass Ihre Organisation mit den Richtlinien und Vorschriften konform bleibt. Verwenden Sie das folgende Verfahren, um Richtlinien für Informationsbarrieren zu aktivieren, die in Microsoft Teams erwartungsgemäß funktionieren. 

   1. Führen Sie die folgenden PowerShell-Cmdlets aus:

      ```powershell
      Connect-AzureAD 
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzADServicePrincipal -ServicePrincipalName $appId
      if ($sp -eq $null) { New-AzADServicePrincipal -ApplicationId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   2. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Arbeits-oder Schulkonto für Office 365 an.

   3. Überprüfen Sie im Dialogfeld **angeforderte Berechtigungen** die Informationen, und wählen Sie dann **akzeptieren**aus.

Wenn alle Voraussetzungen erfüllt sind, fahren Sie mit dem nächsten Abschnitt fort.

> [!TIP]
> Zur Unterstützung der Vorbereitung Ihres Plans ist ein Beispielszenario in diesem Artikel enthalten. [Informationen finden Sie unter Contosos Abteilungen, Segmente und Richtlinien](#example-contosos-departments-segments-and-policies).<p>Darüber hinaus steht eine herunterladbare Excel-Arbeitsmappe zur Verfügung, die Sie bei der Planung und Definition ihrer Segmente und Richtlinien (und Erstellen Ihrer PowerShell-Cmdlets) unterstützt. [Rufen Sie die Arbeitsmappe](https://github.com/MicrosoftDocs/OfficeDocs-O365SecComp/raw/public/SecurityCompliance/media/InfoBarriers-PowerShellGenerator.xlsx)ab. 

## <a name="part-1-segment-users"></a>Teil 1: Segment Benutzer

In dieser Phase bestimmen Sie, welche Richtlinien für Informationsbarrieren erforderlich sind, erstellen eine Liste der zu definierenden Segmente und definieren dann Ihre Segmente.

### <a name="determine-what-policies-are-needed"></a>Bestimmen der erforderlichen Richtlinien

Unter Berücksichtigung gesetzlicher und Branchen rechtlicher bestimmungensind die Gruppen in Ihrer Organisation, die Richtlinien für Informationsbarrieren benötigen? Erstellen Sie eine Liste. Gibt es Gruppen, die daran gehindert werden sollen, mit einer anderen Gruppe zu kommunizieren? Gibt es Gruppen, die nur mit einer oder zwei anderen Gruppen kommunizieren dürfen? Denken Sie an die Richtlinien, die Sie als Zugehörigkeit zu einer von zwei Gruppen benötigen:
- "Blockieren"-Richtlinien verhindern, dass eine Gruppe mit einer anderen Gruppe kommuniziert.
- Mit den Richtlinien "zulassen" kann eine Gruppe nur mit bestimmten anderen, bestimmten Gruppen kommunizieren.

Wenn Sie über eine anfängliche Liste von Gruppen und Richtlinien verfügen, fahren Sie mit dem Identifizieren der benötigten Segmente fort. 

### <a name="identify-segments"></a>Identifizieren von Segmenten

Erstellen Sie zusätzlich zu Ihrer anfänglichen Richtlinienliste eine Liste der Segmente für Ihre Organisation. Benutzer, die in Richtlinien für Informationsbarrieren eingeschlossen werden sollen, sollten zu einem Segment gehören. Planen Sie Ihre Segmente sorgfältig, da sich ein Benutzer nur in einem Segment befinden kann. Für jedes Segment kann nur eine Informations Sperrrichtlinie angewendet werden.

> [!IMPORTANT]
> Ein Benutzer darf sich nur in einem Segment befinden.

Bestimmen Sie, welche Attribute in den Verzeichnisdaten Ihrer Organisation verwendet werden, um Segmente zu definieren. Sie können *Department* *, Mitglied*oder eines der unterstützten Attribute verwenden. Stellen Sie sicher, dass Sie Werte in dem Attribut haben, das Sie für Benutzer auswählen. [Siehe Liste der unterstützten Attribute für Informationsbarrieren](information-barriers-attributes.md).

> [!IMPORTANT]
> **Bevor Sie mit dem nächsten Abschnitt fortfahren, stellen Sie sicher, dass Ihre Verzeichnisdaten Werte für Attribute aufweisen, die Sie zum Definieren von Segmenten verwenden können**. Wenn Ihre Verzeichnisdaten keine Werte für die Attribute enthalten, die Sie verwenden möchten, müssen die Benutzerkonten aktualisiert werden, um diese Informationen einzubeziehen, bevor Sie mit Informationsbarrieren fortfahren. Wenn Sie Hilfe dazu erhalten möchten, lesen Sie die folgenden Ressourcen:<br/>- [Konfigurieren von Eigenschaften von Benutzerkonten mit Office 365 PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/configure-user-account-properties-with-microsoft-365-powershell)<br/>- [Hinzufügen oder Aktualisieren der Profilinformationen eines Benutzers mithilfe von Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>Definieren von Segmenten mithilfe von PowerShell

Das Definieren von Segmenten wirkt sich nicht auf Benutzer aus. Es wird lediglich die Stufe für die Definition von Informationsschranken Richtlinien festgelegt und dann angewendet.

1. Verwenden Sie das **New-OrganizationSegment-** Cmdlet mit dem **UserGroupFilter** -Parameter, der dem [Attribut](information-barriers-attributes.md) entspricht, das Sie verwenden möchten.

    |Syntax   |Beispiel  |
    |---------|---------|
    |`New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"`     |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>In diesem Beispiel wird ein Segment namens *HR* mithilfe von *HR*definiert, einem Wert im *Department* -Attribut. Der **-EQ-** Teil des Cmdlets bezieht sich auf "Equals". (Alternativ können Sie **-ne** verwenden, um "nicht gleich" zu bedeuten. Siehe [Verwenden von "gleich" und "ungleich" in Segment Definitionen](#using-equals-and-not-equals-in-segment-definitions).)        |

    Nach dem Ausführen jedes Cmdlets sollte eine Liste mit Details zum neuen Segment angezeigt werden. Details umfassen den Typ des Segments, wer es erstellt oder zuletzt geändert hat usw. 

2. Wiederholen Sie diesen Vorgang für jedes Segment, das Sie definieren möchten.

    > [!IMPORTANT]
    > **Stellen Sie sicher, dass sich Ihre Segmente nicht überschneiden**. Jeder Benutzer, der von Informationsbarrieren betroffen ist, sollte einem (und nur einem) Segment angehören. Kein Benutzer sollte zu zwei oder mehr Segmenten gehören. (Siehe [Beispiel: Contosos definierte Segmente](#contosos-defined-segments) in diesem Artikel.)


Nachdem Sie Ihre Segmente definiert haben, fahren Sie mit [define Information Barrier Policies](#part-2-define-information-barrier-policies)fort.

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Verwenden von "gleich" und "nicht gleich" in Segment Definitionen

Im folgenden Beispiel definieren wir ein Segment so, dass "Department gleich HR" ist. 

|Beispiel  |
|---------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>Beachten Sie, dass in diesem Beispiel die Segmentdefinition den Parameter "Equals" enthält, der als **-EQ**bezeichnet wird. 
  |

Sie können Segmente auch mithilfe eines Parameters "ungleich" definieren, **wie in**der folgenden Tabelle dargestellt:

|Syntax  |Beispiel  |
|---------|---------|
|`New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"`   | <p>In diesem Beispiel haben wir ein Segment namens *NotSales* definiert, das alle Personen enthält, die nicht im *Vertrieb*sind. Der **-ne-** Teil des Cmdlets bezieht sich auf "ungleich".  |

Zusätzlich zum Definieren von Segmenten mit "gleich" oder "ungleich" können Sie ein Segment mit den Parametern "gleich" und "ungleich" definieren. Sie können auch komplexe Gruppenfilter mit logischen *and* -und *or* -Operatoren definieren.


|Syntax    |Beispiel  |
|---------|---------|
|`New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` |<p>In diesem Beispiel haben wir ein Segment namens *LocalFTE* definiert, das Personen enthält, die lokal gespeichert sind und deren Positionen nicht als *temporär*aufgeführt werden.    |
 |`New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`|  <p>In diesem Beispiel haben wir ein Segment namens *Segment1* definiert, das Personen enthält, die Mitglied von group1@contoso.com und nicht Mitglieder von Group3@contoso.com sind.
|`New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | In diesem Beispiel haben wir ein Segment namens *Segment2* definiert, das Personen enthält, die Mitglied von group2@contoso.com und nicht Mitglieder von Group3@contoso.com sind.
|`New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`|  In diesem Beispiel haben wir ein Segment namens *Segment1and2* definiert, das Personen Mitglieder von group1@contoso.com und group2@contoso.com und nicht Mitglieder von Group3@contoso.com enthält.


> [!TIP]
> Verwenden Sie nach Möglichkeit Segment Definitionen, die "-EQ" oder "-ne" enthalten. Versuchen Sie nicht, komplexe Segment Definitionen zu definieren.

## <a name="part-2-define-information-barrier-policies"></a>Abschnitt 2: Definieren von Richtlinien für Informationsbarrieren

Bestimmen Sie, ob Sie die Kommunikation zwischen bestimmten Segmenten verhindern oder die Kommunikation auf bestimmte Segmente beschränken müssen. Im Idealfall verwenden Sie die Mindestanzahl von Richtlinien, um sicherzustellen, dass Ihre Organisation den rechtlichen und branchenspezifischen Anforderungen entspricht.

Wählen Sie mit der Liste der Benutzersegmente und den Richtlinien für Informationsbarrieren, die Sie definieren möchten, ein Szenario aus, und führen Sie dann die Schritte aus. 

- [Szenario 1: Blockieren der Kommunikation zwischen Segmenten](#scenario-1-block-communications-between-segments)
- [Szenario 2: Zulassen, dass ein Segment nur mit einem anderen Segment kommuniziert](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Stellen Sie sicher, dass Sie bei der Definition von Richtlinien keinem Segment mehr als eine Richtlinie zuweisen**. Wenn Sie beispielsweise eine Richtlinie für ein Segment mit dem Namen " *Sales*" definieren, definieren Sie keine zusätzliche Richtlinie für den *Vertrieb*.<p>Achten Sie beim Definieren von Richtlinien für Informationsbarrieren darauf, diese Richtlinien auf inaktiven Status festzulegen, bis Sie bereit sind, Sie anzuwenden. Das definieren (oder bearbeiten) von Richtlinien wirkt sich erst dann auf Benutzer aus, wenn diese Richtlinien auf aktiver Status festgelegt und dann angewendet wurden.

(Weitere Informationen finden Sie in diesem Artikel unter [Beispiel: Contosos Information Barrier Policies](#contosos-information-barrier-policies) .)

### <a name="scenario-1-block-communications-between-segments"></a>Szenario 1: Blockieren der Kommunikation zwischen Segmenten

Wenn Sie verhindern möchten, dass Segmente miteinander kommunizieren, definieren Sie zwei Richtlinien: eine für jede Richtung. Jede Richtlinie blockiert die Kommunikation nur auf eine Weise.

Nehmen Sie beispielsweise an, dass Sie die Kommunikation zwischen Segment a und Segment B blockieren möchten. In diesem Fall definieren Sie eine Richtlinie, die verhindert, dass Segment a mit Segment b kommuniziert, und dann eine zweite Richtlinie definieren, um zu verhindern, dass Segment b mit Segment A kommuniziert.

1. Verwenden Sie zum Definieren Ihrer ersten Sperrrichtlinie das Cmdlet **New-InformationBarrierPolicy** mit dem Parameter **SegmentsBlocked** . 

    |Syntax  |Beispiel  |
    |---------|---------|
    |`New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"`     |`New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p>    In diesem Beispiel haben wir eine Richtlinie mit dem Namen " *Sales-Research* " für ein Segment namens " *Sales*" definiert. Wenn diese Richtlinie aktiv und angewendet wird, wird verhindert, dass Personen im *Vertrieb* mit Personen in einem Segment mit dem Namen *Research*kommunizieren.         |

2. Verwenden Sie zum Definieren des zweiten Sperr Segments das Cmdlet **New-InformationBarrierPolicy** mit dem Parameter **SegmentsBlocked** erneut, diesmal mit umgekehrten Segmenten.

    |Beispiel  |
    |---------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p>    In diesem Beispiel wurde eine Richtlinie mit dem Namen *Research-Sales* definiert, um zu verhindern, dass die *Forschung* mit dem *Vertrieb*kommuniziert.     |

2. Führen Sie einen der folgenden Schritte aus:

   - (Falls erforderlich) [Definieren einer Richtlinie, mit der ein Segment nur mit einem anderen Segment kommunizieren kann](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Nachdem alle Ihre Richtlinien definiert wurden) [Anwenden von Richtlinien für Informationsbarrieren](#part-3-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Szenario 2: Zulassen, dass ein Segment nur mit einem anderen Segment kommuniziert

1. Damit ein Segment nur mit einem anderen Segment kommunizieren kann, verwenden Sie das Cmdlet **New-InformationBarrierPolicy** mit dem Parameter **SegmentsAllowed** . 

    |Syntax  |Beispiel  |
    |---------|---------|
    |`New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"`     |`New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p>    In diesem Beispiel haben wir eine Richtlinie mit dem Namen *Manufacturing-HR* für ein Segment namens *Manufacturing*definiert. Wenn diese Richtlinie aktiv und angewendet wird, können Sie in der *Fertigung* nur Personen in einem Segment namens *HR*kommunizieren. (In diesem Fall kann die *Fertigung* nicht mit Benutzern kommunizieren, die nicht Teil von *HR*sind.)         |

    **Bei Bedarf können Sie mit diesem Cmdlet mehrere Segmente angeben, wie im folgenden Beispiel gezeigt.**

    |Syntax  |Beispiel  |
    |---------|---------|
    |`New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"`     |`New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p>In diesem Beispiel haben wir eine Richtlinie definiert, mit der das *Forschungs* Segment nur mit *HR* und *Manufacturing*kommunizieren kann.        |

    Wiederholen Sie diesen Schritt für jede Richtlinie, die Sie definieren möchten, damit bestimmte Segmente nur mit bestimmten anderen Segmenten kommunizieren können.

2. Führen Sie einen der folgenden Schritte aus:

   - (Falls erforderlich) [Definieren einer Richtlinie zum Blockieren der Kommunikation zwischen Segmenten](#scenario-1-block-communications-between-segments) 
   - (Nachdem alle Ihre Richtlinien definiert wurden) [Anwenden von Richtlinien für Informationsbarrieren](#part-3-apply-information-barrier-policies)

## <a name="part-3-apply-information-barrier-policies"></a>Abschnitt 3: Anwenden von Richtlinien für Informationsbarrieren

Richtlinien für Informationsbarrieren werden erst wirksam, wenn Sie Sie auf aktiver Status festlegen und dann die Richtlinien anwenden.

1. Verwenden Sie das Cmdlet **Get-InformationBarrierPolicy** , um eine Liste der definierten Richtlinien anzuzeigen. Notieren Sie den Status und die Identität (GUID) der einzelnen Richtlinien.

    Syntax `Get-InformationBarrierPolicy`

2. Um eine Richtlinie auf den aktiven Status festzulegen, verwenden Sie das Cmdlet "InformationBarrierPolicy" mit einem **Identity** -Parameter und den **State** **-** Parameter auf " **aktiv**" festgelegt. 

    |Syntax  |Beispiel  |
    |---------|---------|
    |`Set-InformationBarrierPolicy -Identity GUID -State Active`     |`Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p>    In diesem Beispiel wird eine Richtlinie für Informationsbarrieren festgelegt, bei der die GUID *43c37853-EA10-4b90-a23d-ab8c93772471* den Status aktiv besitzt.   |

    Wiederholen Sie diesen Schritt für jede Richtlinie entsprechend.

3. Wenn Sie die Richtlinien für Informationsbarrieren auf den aktiven Status festgesetzt haben, verwenden Sie das Cmdlet **Start-InformationBarrierPoliciesApplication** im Security & Compliance Center.

    Syntax `Start-InformationBarrierPoliciesApplication`

    Nachdem Sie `Start-InformationBarrierPoliciesApplication` 30 Minuten ausgeführt haben, damit das System die Richtlinien anwenden kann. Das System wendet Richtlinien Benutzer nach Benutzer an. Im allgemeinen verarbeitet das System etwa 5.000 Benutzerkonten pro Stunde.

## <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Anzeigen des Status von Benutzerkonten, Segmenten, Richtlinien oder Richtlinien Anwendungen

Mit PowerShell können Sie den Status von Benutzerkonten, Segmenten, Richtlinien und Richtlinien Anwendungen anzeigen, wie in der folgenden Tabelle aufgeführt.

|So zeigen Sie dies an  |Aktion  |
|---------|---------|
|Benutzerkonten     |Verwenden Sie das Cmdlet **Get-InformationBarrierRecipientStatus** mit Identitäts Parametern. <p>Syntax `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p>Sie können einen beliebigen Wert verwenden, der jeden Benutzer eindeutig identifiziert, beispielsweise Name, Alias, Distinguished Name, kanonischer Domänenname, e-Mail-Adresse oder GUID. <p>Beispiel: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p>In diesem Beispiel wird auf zwei Benutzerkonten in Office 365 verwiesen: *meganb* für *Megan*und *alexw* für *Alex*. <p>(Sie können dieses Cmdlet auch für einen einzelnen Benutzer verwenden: `Get-InformationBarrierRecipientStatus -Identity <value>` ) <p>Dieses Cmdlet gibt Informationen zu Benutzern zurück, beispielsweise Attributwerte und alle angewendeten Richtlinien für Informationsbarrieren.|
|Segmente     |Verwenden Sie das Cmdlet **Get-OrganizationSegment** .<p>Syntax `Get-OrganizationSegment` <p>Dadurch wird eine Liste aller Segmente angezeigt, die für Ihre Organisation definiert sind.         |
|Richtlinien für Informationsbarrieren     |Verwenden Sie das Cmdlet **Get-InformationBarrierPolicy** . <p> Syntax `Get-InformationBarrierPolicy` <p>Dadurch wird eine Liste der definierten Richtlinien für Informationsbarrieren angezeigt, die definiert wurden, und deren Status.       |
|Die neueste Informations Barriere-Richtlinienanwendung     | Verwenden Sie das Cmdlet **Get-InformationBarrierPoliciesApplicationStatus** . <p>Syntax `Get-InformationBarrierPoliciesApplicationStatus`<p>    Dadurch werden Informationen darüber angezeigt, ob die Richtlinienanwendung abgeschlossen, ein Fehler aufgetreten ist oder ausgeführt wird.       |
|Alle Informations Barrier Policy-Anwendungen|`Get-InformationBarrierPoliciesApplicationStatus -All $true` verwenden<p>Dadurch werden Informationen darüber angezeigt, ob die Richtlinienanwendung abgeschlossen, ein Fehler aufgetreten ist oder ausgeführt wird.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

## <a name="what-if-i-need-to-remove-or-change-policies"></a>Was kann ich tun, wenn ich Richtlinien entfernen oder ändern muss?

Ressourcen stehen zur Verfügung, um Sie bei der Verwaltung ihrer Informations Barriere-Richtlinien zu unterstützen.

- Wenn mit Informationsbarrieren etwas schief geht, finden Sie weitere Informationen unter [Troubleshooting Information Barriers](information-barriers-troubleshooting.md).

- Informationen zum Beenden der Anwendung von Richtlinien finden Sie unter [Beenden einer Richtlinienanwendung](information-barriers-edit-segments-policies.md#stop-a-policy-application).

- Informationen zum Entfernen einer Richtlinie zu Informationsbarrieren finden Sie unter [Remove a Policy](information-barriers-edit-segments-policies.md#remove-a-policy).

- Informationen zum vornehmen von Änderungen an Segmenten oder Richtlinien finden Sie unter [Bearbeiten (oder entfernen) von Richtlinien für Informationsbarrieren](information-barriers-edit-segments-policies.md).

## <a name="example-contosos-departments-segments-and-policies"></a>Beispiel: Abteilungen, Segmente und Richtlinien von Contoso

Wenn Sie sehen möchten, wie eine Organisation bei der Definition von Segmenten und Richtlinien vorgehen könnte, sehen Sie sich das folgende Beispiel an.

### <a name="contosos-departments-and-plan"></a>Die Abteilungen und der Plan von Contoso

Contoso verfügt über fünf Abteilungen: Personal, Vertrieb, Marketing, Forschung und Fertigung. Um mit den Branchenrichtlinien konform zu bleiben, sollten Personen in einigen Abteilungen nicht mit anderen Abteilungen kommunizieren, wie in der folgenden Tabelle aufgeführt:

|Segment  |Kann sprechen mit  |Kann nicht sprechen mit  |
|---------|---------|---------|
|Personal     |Alle         |(keine Beschränkungen)         |
|Vertrieb     |HR, Marketing, Produktion         |Forschung         |
|Marketing     |Alle         |(keine Beschränkungen)         |
|Forschung     |HR, Marketing, Produktion        |Vertrieb     |
|Fertigung |HR, Marketing |Andere Personen als HR oder Marketing |

Vor diesem Hintergrund umfasst der Plan von Contoso drei Richtlinien für Informationsbarrieren:

1. Eine Richtlinie, die verhindert, dass der Bereich Vertrieb Kommunikation an den Bereich Forschung richtet (und eine andere Richtlinie, die verhindert, dass der Bereich Forschung Kommunikation an den Bereich Vertrieb richtet)
2. Eine Richtlinie, anhand der die Fertigung nur mit Personal und Marketing kommunizieren kann 

Es ist nicht erforderlich, Richtlinien für HR oder Marketing zu definieren.

### <a name="contosos-defined-segments"></a>Die von Contoso definierten Segmente 

Contoso wird das Department-Attribut in Azure Active Directory verwenden, um Segmente wie folgt zu definieren:

|Abteilung  |Segment Definition  |
|---------|---------|
|Personal     | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"`        |
|Vertrieb     | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"`        |
|Marketing     | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"`        |
|Forschung     | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"`        |
|Fertigung     | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"`        |

Nachdem die Segmente definiert sind, fährt Contoso mit der Definition von Richtlinien fort. 

### <a name="contosos-information-barrier-policies"></a>Contosos Richtlinien für Informationsbarrieren

Contoso definiert drei Richtlinien, wie in der folgenden Tabelle beschrieben:

|Richtlinie  |Richtliniendefinition  |
|---------|---------|
|Richtlinie 1: Unterbindung der Kommunikation von der Abteilung Vertrieb zur Abteilung Forschung     | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> In diesem Beispiel heißt die Richtlinie zur Informationsbarriere *Vertrieb-Forschung*. Wenn diese Richtlinie aktiv und angewendet ist, verhindert sie, dass Benutzer im Segment Vertrieb Kommunikation an Benutzer im Segment Forschung richten können. Dies ist eine einseitige Richtlinie. Damit wird nicht verhindert, dass die Forschung Kommunikation an den Vertrieb richtet. Für diesen Fall ist Richtlinie 2 erforderlich.      |
|Richtlinie 2: Unterbindung der Kommunikation von der Abteilung Forschung zur Abteilung Vertrieb     | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> In diesem Beispiel heißt die Richtlinie zur Informationsbarriere *Forschung-Vertrieb*. Wenn diese Richtlinie aktiv und angewendet ist, verhindert sie, dass Benutzer im Segment Forschung Kommunikation an Benutzer im Segment Vertrieb richten können.       |
|Richtlinie 3: zulassen, dass die Fertigung nur mit HR und Marketing kommuniziert     | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p>In diesem Fall wird die Richtlinie zur Informationsbarriere als *Fertigung-PersonalMarketing* bezeichnet. Wenn diese Richtlinie aktiv und angewendet ist, kann die Fertigung nur mit Personal und Marketing kommunizieren. Beachten Sie, dass Personal und Marketing uneingeschränkt mit anderen Segmenten kommunizieren können. |

Wenn Segmente und Richtlinien definiert sind, wendet Contoso die Richtlinien durch Ausführen des Cmdlets **Start-InformationBarrierPoliciesApplication** an. 

Wenn dieser Vorgang abgeschlossen ist, entspricht Contoso den rechtlichen und branchenspezifischen Anforderungen.

## <a name="related-articles"></a>Verwandte Artikel

- [Hier erhalten Sie einen Überblick über Informationsbarrieren](information-barriers.md)

- [Informationsbarrieren in Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams)
