---
title: Anforderungen für die Lokalisierung russischer personenbezogener Daten
description: Erfahren Sie, wie das Sammeln personenbezogener Daten, die Erfassung, Systematisierung, Speicherung, Speicherung, Klärung und Extraktion von personenbezogenen Daten in Microsoft-Diensten und-Datenbanken in Russland ausgeführt wird.
keywords: Microsoft 365, Compliance, Angebote
localization_priority: None
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: M365-security-compliance
hideEdit: true
titleSuffix: Microsoft Compliance
ms.openlocfilehash: 29c56d525375162926d34bd298bbbd660964438d
ms.sourcegitcommit: e5ac81132cc5fd248350627a3cc7b3c640f53b6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48208157"
---
# <a name="russian-personal-data-localization-requirements"></a>Anforderungen für die Lokalisierung russischer personenbezogener Daten

Ab dem 1. September 2015 müssen Organisationen, die als personenbezogene Daten Betreiber betrachtet werden, sicherstellen, dass bei der Erfassung personenbezogener Daten, der Datenerfassung, Systematisierung, Akkumulation, Speicherung, Klärung (Aktualisierung, Änderung) und Extraktion durch die in Russland befindlichen Datenbanken ("Anforderungen an die persönliche Daten Lokalisierung") personenbezogene Daten erfasst werden. <sup>1</sup>

Microsoft Online Services, die Organisationen zur Verfügung stehen (einschließlich, aber nicht ausschließlich für Bildungseinrichtungen) (im folgenden "Kunde" genannt), einschließlich derer, die die Verarbeitung personenbezogener Daten wie Microsoft Azure, Microsoft 365, Dynamics 365 und Power Platform ermöglichen, werden von Rechenzentren außerhalb Russlands bereitgestellt (Weitere Informationen finden Sie im [Microsoft Trust Center](https://www.microsoft.com/trust-center)).

Basierend auf der Art und dem Inhalt der von den Kundeninformationssystemen verarbeiteten Informationen können solche Systeme, einschließlich derer, die Microsoft-cloudprodukte verwenden, als Daten Informationssystem ("PDIS", "ISPD") betrachtet werden. In Fällen, in denen der Kunde Microsoft Online Services in einem System verwenden möchte, das durch seine Architektur und die Art der Verarbeitung von Informationen als PDIS qualifiziert wird, lädt Microsoft seine Kunden ein, unter anderem die nachfolgend aufgeführten verfügbaren Lösungen zu prüfen. Alle bereitgestellten Szenarien stehen Kunden als zusätzliche Option für standardmäßige Unternehmensangebote zur Verfügung.

Es sei darauf hingewiesen, dass es der Kunde als personenbezogener Datenanbieter von PDIS ist, der für die Compliance verantwortlich ist, und die anwendbaren rechtlichen Anforderungen für die Lokalisierung personenbezogener Daten zu analysieren und zu bewerten und nach eigenem Ermessen unabhängige Maßnahmen zu treffen, um sicherzustellen, dass die Verarbeitung personenbezogener Daten in PDIS dem russischen personenbezogenen Daten Gesetz entspricht. <sup>2</sup>

## <a name="subscribing-to-microsoft-online-services"></a>Abonnieren von Microsoft Online Services

### <a name="microsoft-id-management"></a>Microsoft-ID-Verwaltung

Microsoft lädt Kunden ein, Microsoft Online Services – Microsoft Azure, Microsoft 365, Dynamics 365 und Power Platform – über einen Microsoft Cloud Solution Provider (CSP)-Partner zu abonnieren. Weitere Informationen finden Sie in dieser [Liste der CSP-Partner](https://pinpoint.microsoft.com/search?type=services&campaign=691) .

### <a name="managing-user-identity-and-access-for-microsoft-online-services"></a>Verwalten der Benutzeridentität und des Zugriffs für Microsoft Online Services

Für Microsoft Online Services wie Microsoft Azure, Microsoft 365, Dynamics 365 und Power Platform werden die Benutzerüberprüfung und die Zugriffsverwaltung über [Azure Active Directory (AAD)](https://azure.microsoft.com/services/active-directory/)ausgeführt. Beachten Sie, dass Fälle, in denen ein Microsoft-Kunde ein lokales Identifikations Verwaltungssystem für Microsoft-Cloud-Dienste verwendet (wie die Windows Server-Active Directory (AD) oder ein anderes ID-Verwaltungssystem), der Kunde die Möglichkeit hat, dieses System schnell über Azure AD Connect mit dem Azure-Active Directory (AAD) zu integrieren. Weitere Informationen finden Sie unter der [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/cloud-provisioning/) -Option. Microsoft-Kunden können außerdem Anwendungen und Lösungen von Drittanbietern verwenden, um Ihre Benutzer zu verwalten und Ihr lokales Identifikationssystem mit dem Azure AD zu integrieren.

## <a name="use-microsoft-compliance-manager-to-assess-your-risk"></a>Bewerten des Risikos mithilfe von Microsoft Compliance-Manager

[Microsoft Compliance Manager](compliance-manager.md) ist ein Feature im [Microsoft 365 Compliance Center](microsoft-365-compliance-center.md) , mit dem Sie die Compliance-Haltung ihrer Organisation besser verstehen und Maßnahmen zur Verringerung von Risiken unterstützen können. Compliance-Manager bietet eine Premium-Vorlage für die Erstellung einer Bewertung für diese Verordnung. Suchen Sie die Vorlage auf der Seite " **Bewertungs Vorlagen** " im Compliance-Manager. Hier erfahren Sie, wie Sie [Assessments im Compliance-Manager erstellen](compliance-manager-assessments.md).

## <a name="questions-and-support"></a>Fragen und Support

Technische und Abrechnungsfragen finden Sie in den folgenden Microsoft-Support Ressourcen: Wenden Sie sich für weitere Fragen oder Klärungen an das Microsoft- [Datenschutzteam](https://support.microsoft.com/gp/privacy-page).

### <a name="microsoft-azure"></a>Microsoft Azure

- **Website**: [Microsoft Azure-Unterstützung](https://aka.ms/GetAzureSupport)
- **Gebührenfreie Telefonkosten**: 8 800 200 8001
- **Ortsgespräch**: 495 916 7171
- **Online Support**: Senden von Abfragen über das [Azure-Portal](https://portal.azure.com)

### <a name="microsoft-365"></a>Microsoft 365

- **Gebührenfreie Telefonkosten**: 8 10 800 2548 1044
- **Ortsgespräch**: 499 922 8623
- **Online Support**: Senden von Abfragen über das [Admin Center](https://portal.office.com/)

### <a name="dynamics-365"></a>Dynamics 365

- **Gebührenfreie Telefonkosten**: 8 10 800 2548 1044
- **Ortsgespräch**: 499 922 8623
- **Online Support**: Senden von Abfragen über das [Dynamics-Support Portal](https://dynamics.microsoft.com/support/)

### <a name="power-platform"></a>Power-Plattform

- **Gebührenfreie Telefonkosten**: 8 10 800 2548 1044
- **Ortsgespräch**: 499 922 8623
- **Online Support**: Senden von Abfragen über die [Power Platform-Unterstützung](https://docs.microsoft.com/power-platform/admin/get-help-support)

> [!NOTE]
> <sup>1</sup> Bundesgesetz Nr. 242-FZ (Ausgabe vom 12.31.2014) "Änderungen in bestimmten Rechtsakten der Russischen Föderation zur Klärung des Verfahrens für die Verarbeitung personenbezogener Daten in Informations-und Telekommunikationsnetzen" vom 07.21.2014 <br>
> <sup>2</sup> Bundesgesetz Nr. 152-FZ für personenbezogene Daten vom 07,27. 2006<br>
