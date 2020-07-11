---
title: DPIA-Datenverarbeitungsdienst für Windows für die DSGVO
description: Finden Sie Informationen, die dabei helfen, zu bestimmen, ob bei Verwendung des Microsoft-Datenverarbeitungsdienstes für Windows eine Datenschutz-Folgenabschätzung (Data Protection Impact Assessment, DPIA) erforderlich ist.
keywords: Datenschutz-Folgenabschätzung, DPIA, Microsoft 365, Microsoft 365 Education, Microsoft 365-Dokumentation, DSGVO
localization_priority: Priority
ROBOTS: NOINDEX, NOFOLLOW
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: daniha
author: DaniHalfin
manager: dansimp
audience: itpro
ms.collection:
- GDPR
- M365-security-compliance
ms.openlocfilehash: c594bbca6383874346719a477d3f86f3dac99409
ms.sourcegitcommit: 3ddcf08e8deec087df1fe524147313f1cb12a26d
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "45023602"
---
# <a name="data-protection-impact-assessments-guidance-for-data-controllers-using-microsoft-data-processor-service-for-windows"></a>Datenschutz-Folgenabschätzung: Leitfaden für Datenverantwortliche, die den Microsoft-Datenverarbeitungsdienst für Windows verwenden

>[!NOTE]
>Dieser Artikel richtet sich an Teilnehmer am Vorschauprogramm „Datenverarbeitungsdienst für Windows“ und setzt die Zustimmung zu bestimmten Nutzungsbedingungen voraus. Wenn Sie mehr über das Programm erfahren und den Nutzungsbedingungen zustimmen möchten, wechseln Sie zu [https://aka.ms/dpswpublicpreview](https://aka.ms/dpswpublicpreview).

Gemäß der EU-Datenschutzgrundverordnung (DSGVO) müssen Datenverantwortliche eine Datenschutz-Folgenabschätzung (Data Protection Impact Assessment, DPIA) für Verarbeitungsvorgänge durchführen, die „voraussichtlich ein hohes Risiko für die Rechte und Freiheiten natürlicher Personen zur Folge“ haben. Der Datenverarbeitungsdienst für Windows selbst weist nichts auf, das die Erstellung einer DPIA durch einen ihn nutzenden Datenverantwortlichen erfordern würde. Ob eine DPIA erforderlich ist, hängt vielmehr von den Details und dem Kontext der Bereitstellung, Konfiguration und Verwendung des Datenverarbeitungsdienstes für Windows durch den Datenverantwortlichen ab. 

Dieses Dokument soll den Datenverantwortlichen Informationen über den Datenverarbeitungsdienst für Windows bereitstellen, die ihnen helfen, zu bestimmen, ob eine Datenschutz-Folgenabschätzung erforderlich ist, und wenn ja, welche Informationen sie enthalten muss.

>[!Note]
>Microsoft stellt in diesem Dokument keine Rechtsberatungen bereit. Dieses Dokument dient ausschließlich zu Informationszwecken. Kunden sind dazu angehalten, mit Unterstützung ihrer Datenschutzbeauftragten und Rechtsberater die Notwendigkeit und Inhalte von DPIAs zu ermitteln, die mit der Verwendung des Datenverarbeitungsdienst für Windows oder einem anderen Microsoft-Onlinedienst verbunden sind.

## <a name="part-1--determining-whether-a-dpia-is-needed"></a>Teil 1: Bestimmen, ob eine DPIA erforderlich ist

Laut Artikel 35 der DSGVO muss ein Datenverantwortlicher eine Datenschutz-Folgenabschätzung (Data Protection Impact Assessment, DPIA) durchführen, "[wenn] eine Form der Verarbeitung, insbesondere bei Verwendung neuer Technologien, aufgrund der Art, des Umfangs, der Umstände und der Zwecke der Verarbeitung voraussichtlich ein hohes Risiko für die Rechte und Freiheiten natürlicher Personen zur Folge [hat]." Darüber hinaus werden darin bestimmte Faktoren angegeben, die auf ein solches hohes Risiko hindeuten. Diese werden in der folgenden Tabelle beschrieben. Beim Bestimmen der Notwendigkeit einer DPIA sollte ein Datenverantwortlicher diese Faktoren zusammen mit allen anderen relevanten Faktoren im Hinblick auf die spezifischen Implementierung(en) des Datenverantwortlichen und die Verwendung(en) des Datenverarbeitungsdienstes für Windows berücksichtigen.

## <a name="table-1--data-processor-service-for-windows-dpia-risk-factors"></a>Tabelle 1: Datenverarbeitungsdienst für Windows – DPIA- Risikofaktoren 

|||
|:----|:----|
|**Hoher Risikofaktor**|**Wichtige Informationen zum Datenverarbeitungsdienst für Windows**|
| Eine systematische und umfassende Bewertung der persönlichen Aspekte im Zusammenhang mit natürlichen Personen basierend auf der automatisierten Datenverarbeitung, einschließlich Profiling, und auf der Entscheidungen basieren, die hinsichtlich der natürlichen Person rechtliche Wirkung erzeugen oder sie auf ähnliche Weise betreffen. |Der Datenverarbeitungsdienst für Windows stellt keine Funktionen bereit, um bestimmte Vorgänge der Datenverarbeitung automatisiert durchzuführen.<br><br> Da jedoch andere Dienste den Datenverarbeitungsdienst für Windows als Datenquelle verwenden, könnte ein Datenverantwortlicher potenziell diese Dienste so konfigurieren, dass sie für die Verarbeitung verwendet werden können. Datenverantwortliche sollten dies anhand ihrer Nutzung der Dienste bestimmen, die mit dem Datenverarbeitungsdienst für Windows verbunden sind.|   
| Die umfassende Verarbeitung von Daten besonderer Kategorien (personenbezogene Daten, die die ethnische Herkunft, politische, religiöse oder philosophische Überzeugungen, die Mitgliedschaft in einer Gewerkschaft offenlegen sowie die Verarbeitung von genetischen bzw. biometrischen Daten für Zwecke der zweifelsfreien Identifikation einer natürlichen Person, Daten zu Gesundheit, Sexualleben oder sexueller Orientierung einer natürlichen Person) oder von personenbezogenen Daten bezüglich Begehung von Straftaten und strafrechtlicher Verurteilungen. | Der Datenverarbeitungsdienst für Windows ist nicht speziell dafür vorgesehen, besondere Kategorien personenbezogener Daten zu verarbeiten, und die Verwendung des Datenverarbeitungsdienstes für Windows erhöht nicht das inhärente Risiko der Verarbeitungstätigkeit eines Datenverantwortlichen.<br><br> Ein Datenverantwortlicher könnte jedoch Dienste verwenden, die mit dem Datenverarbeitungsdienst für Windows verbunden sind, um die aufgeführten besonderen Datenkategorien zu verarbeiten. Dienste, die den Datenverarbeitungsdienst für Windows als Datenquelle verwenden, könnten es dem Kunden ermöglichen, jeden beliebigen Datentyp nachzuverfolgen oder anderweitig zu verarbeiten, einschließlich besonderer Kategorien personenbezogener Daten. Als Datenverarbeiter hat Microsoft jedoch keine Kontrolle über diese Nutzung und wenig oder gar keinen Einblick in diese Nutzung. Die Bestimmung der angemessenen Verwendung der Daten des Datenverantwortlichen obliegt dem Datenverantwortlichen. |

## <a name="part-2--contents-of-a-dpia"></a>Teil 2 – Inhalte einer DPIA 

Article 35(7) mandates that a Data Protection Impact Assessment specify the purposes of processing and a systematic description of the envisioned processing. A systematic description of a comprehensive DPIA might include factors such as the types of data processed, how long data is retained, where the data is located and transferred, and what third parties may have access to the data. In addition, the DPIA must include: 

eine Bewertung der Notwendigkeit und Verhältnismäßigkeit in Bezug auf die Zwecke der Verarbeitung; 

eine Bewertung der Risiken für die Rechte und Grundfreiheiten natürlicher Personen 

die vorgesehenen Maßnahmen, um die Risiken, einschließlich Garantien, Sicherheitsmaßnahmen und Mechanismen zum Schutz personenbezogener Daten zu steuern und um die Einhaltung dieser Verordnung zu demonstrieren, wobei die Rechte und berechtigten Interessen der betroffenen Personen und anderer beteiligter Personen berücksichtigt werden. 

Die nachstehende Tabelle enthält Informationen zum Datenverarbeitungsdienst für Windows, die für jedes dieser Elemente relevant sind. Wie in Teil 1 müssen Datenverantwortliche die unten angegebenen Details zusammen mit anderen relevanten Faktoren im Kontext der spezifischen Implementierung(en) und Verwendung(en) des Datenverarbeitungsdienstes für Windows durch den Datenverantwortlichen berücksichtigen. 

## <a name="table-2--data-processor-service-for-windows-dpia-elements"></a>Tabelle 2: Datenverarbeitungsdienst für Windows – DPIA- Elemente 

||||
|:---|:---|:--|
|**Elemente einer DPIA**|**Wichtige Informationen zum Datenverarbeitungsdienst für Windows**| |
| Zweck(e) der Verarbeitung | Der/die Zweck/e der Verarbeitung von Diagnosedaten mithilfe des Datenverarbeitungsdienstes für Windows wird durch den Datenverantwortlichen bestimmt, der ihn implementiert, konfiguriert und verwendet. <br><br> Wie in den [Online Services-Nutzungsbedingungen](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) angegeben, verarbeitet Microsoft als Datenverarbeiter Kundendaten ausschließlich, um für unsere Kunden – die Datenverantwortlichen – die gewünschten Dienste bereitzustellen. Microsoft verwendet Kundendaten oder darauf abgeleitete Informationen nicht für Werbe- oder ähnliche kommerzielle Zwecke. |
| Kategorien verarbeiteter personenbezogener Daten | **Kundendaten**: Alle Daten, einschließlich aller Text-, Sound-, Video- oder Bilddateien, die Microsoft vom Kunden oder im Auftrag des Kunden durch Nutzung von Enterprise-Diensten bereitgestellt werden. Zu den Kundendaten gehören personenbezogene Informationen von Endbenutzern (z. B. Benutzernamen und Kontaktinformationen in Azure Active Directory oder Geräteinformationen über Windows-Diagnosedaten). <br><br> **Vom System generierte Daten**: Von Microsoft generierte Daten, die Microsoft bei der Bereitstellung von Enterprise-Diensten für Benutzer unterstützen. Vom System generierte Daten enthalten in erster Linie pseudonymisierte Daten, z. B. eindeutige, vom System generierte Bezeichner, die von sich aus eine Einzelperson nicht identifizierbar machen, aber dazu verwendet werden, die Enterprise-Dienste für Benutzer bereitzustellen. Vom System generierte Daten enthalten möglicherweise auch personenbezogene Informationen über Endbenutzer wie z. B. einen Benutzernamen. <br><br> **Unterstützungsdaten** – Diese Daten sind von oder im Namen der Kunden für Microsoft bereitgestellt (oder der Kunden autorisiert Microsoft, um diese von einem Onlinedienst zu erhalten) durch einen Kontakt mit Microsoft, um technischen Support für Onlinedienste zu erhalten. <br><br> Weitere Informationen zu den vom Datenverarbeitungsdienst für Windows verarbeiteten Daten finden Sie in den [Online Services-Nutzungsbedingungen](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) sowie im [Microsoft Trust Center](https://www.microsoft.com/trustcenter). |
| Datenaufbewahrung | Microsoft speichert und verarbeitet Kundendaten für die Dauer des Rechtes des Kunden zur Nutzung des Onlinedienstes und bis alle Kundendaten vom Kunden abgerufen oder gemäß den Bestimmungen des OST gelöscht werden. Der Kunde hat jederzeit während der Laufzeit seines Abonnements die Möglichkeit, Kundendaten zu exportieren, die im Datenverarbeitungsdienst für Windows gespeichert sind. Der Kunde kann personenbezogene Daten auf Antrag einer betroffenen Person unter Verwendung der Funktionen laut der [DSGVO-Dokumentation zu Anträgen betroffener Personen für den Datenverarbeitungsdienst für Windows](https://servicetrust.microsoft.com/ViewPage/GDPRDSR) löschen.
| Speicherort und Übertragung personenbezogener Daten | Die Kundendaten des Datenverarbeitungsdienstes für Windows befinden sich in Microsoft-Rechenzentren in den Vereinigten Staaten. |
| Teilen von Daten mit Dritten | Microsoft shares data with third parties acting as our subprocessors (i.e., subcontractors which process personal data) to support functions such as customer and technical support, service maintenance, and other operations. Any subcontractors to which Microsoft transfers Customer Data or Support Data will have entered into written agreements with Microsoft that are no less protective than the Data Protection Terms of the [Online Services Terms](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46). All third-party subcontractors with which Customer Data or Support Data is shared are included in the [Lists of subcontractors](https://www.microsoft.com/trustcenter/privacy/who-can-access-your-data-and-on-what-terms#subcontractors) (see “We limit access by subprocessors”). <br><br> Information regarding Microsoft’s response to law enforcement and third party requests for Customer Data and Support Data is located in the Online Services Terms. Unless Microsoft is legally prohibited from doing so, Microsoft will attempt to redirect the law enforcement agency or third party directly to the Customer. |
| Rechte betroffener Personen | Wenn Microsoft als Datenverarbeiter tätig ist, stellt das Unternehmen dem Kunden (dem Datenverantwortlichen) die personenbezogenen Daten der betroffenen Person sowie die Möglichkeit bereit, Anfragen von betroffenen Person zu erfüllen, wenn diese ihre Rechte unter der DSGVO ausüben. Microsoft tut dies in einer Weise, die der Funktionalität des Produkts und seiner Rolle als Datenverarbeiter entspricht.Erhält Microsoft eine Anfrage von betroffenen Personen des Kunden, eines oder mehrere ihrer Rechte unter der DSGVO auszuüben, wird die Anfrage an den Datenverantwortlichen weitergeleitet. <br><br> Die [DSGVO-Dokumentation zu Anfragen betroffener Personen für den Datenverarbeitungsdienst für Windows](https://servicetrust.microsoft.com/ViewPage/GDPRDSR) enthält eine Beschreibung, wie die Rechte betroffener Personen mithilfe der Funktionen des Datenverarbeitungsdienstes für Windows unterstützt werden können. |
| Eine Bewertung der Notwendigkeit und Verhältnismäßigkeit der Datenverarbeitung in Bezug auf ihren Zweck | Eine solche Bewertung hängt vom Bedarf und dem Zweck der Verarbeitung des Datenverantwortlichen ab. <br><br> With regard to the processing carried out by Microsoft, such processing is necessary and proportional for the purpose of providing the services to the data controller. Microsoft makes this commitment in the OST. |
| Eine Bewertung der Risiken für die Rechte und Freiheiten natürlicher Personen unterliegen | Die wichtigsten Risiken für die Rechte und Freiheiten der betroffenen Personen durch die Nutzung des Datenverarbeitungsdienstes für Windows hängen davon ab, wie und in welchem Kontext der Datenverantwortliche den Datenverarbeitungsdienst für Windows implementiert, konfiguriert und verwendet. <br><br> However, as with any service, personal data held in the service may be at risk of unauthorized access or inadvertent disclosure. Measures Microsoft takes to address such risks are discussed in the OST, as further detailed below. |
| Die vorgesehenen Maßnahmen, um die Risiken, einschließlich Garantien, Sicherheitsmaßnahmen und Mechanismen zum Schutz personenbezogener Daten zu steuern und um die Einhaltung der DSGVO zu demonstrieren, wobei die Rechte und berechtigten Interessen der betroffenen Personen und anderer beteiligter Personen berücksichtigt werden | Microsoft is committed to helping protect the security of Customer Data. The security measures Microsoft takes are described in detail in the OST. <br><br> Microsoft trifft angemessene und geeignete technische und organisatorische Maßnahmen, um die von Microsoft verarbeiteten personenbezogenen Daten zu schützen. Dazu gehören unter anderem interne Datenschutzrichtlinien und -praktiken, vertragliche Verpflichtungen sowie internationale und regionale Standardzertifikate. Weitere Informationen finden Sie auf der Seite zu den [Datenschutzstandards im Trust Center](https://www.microsoft.com/trustcenter/privacy/we-set-and-adhere-to-stringent-standards). <br><br> Microsoft provides significant, transparent customer facing security and privacy materials to help explain Microsoft’s use and processing of personal data. Customers are encouraged to contact Microsoft with questions. <br><br> Außerdem hält Microsoft alle sonstigen DSGVO-Vorschriften ein, die für Datenverarbeiter gelten, einschließlich unter anderem Datenschutz-Folgenabschätzungen und Buchführung.| 