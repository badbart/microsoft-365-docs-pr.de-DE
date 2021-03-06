---
title: Testumgebungsanleitungen für Microsoft 365 Enterprise
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/20/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Verwenden Sie die folgenden Testumgebungsanleitungen, um Demos, Machbarkeitsstudien oder Entwicklungs-/Testumgebungen für Microsoft 365 Enterprise einzurichten.
ms.openlocfilehash: 685bf25db330b4bf43a3a7258aeb43517c239e81
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686766"
---
# <a name="microsoft-365-for-enterprise-test-lab-guides"></a>Testumgebungsanleitungen für Microsoft 365 Enterprise

*Dies gilt sowohl für Microsoft 365 Enterprise als auch Office 365 Enterprise.*

Mithilfe von Testumgebungsanleitungen können Sie schnell mehr zu Microsoft-Produkten erfahren. Sie enthalten Anweisungen zum Konfigurieren vereinfachter, aber repräsentativer Testumgebungen. Sie können diese Umgebungen für Demos, Anpassungen oder das Erstellen komplexer Machbarkeitsstudien für die Dauer eines Test- oder bezahlten Abonnements verwenden. 

Testumgebungsanleitungen sind modular aufgebaut. Sie bauen aufeinander auf, sodass mehrere Konfigurationen entstehen, die Ihren Lern- oder Testkonfigurationsanforderungen besser entsprechen. Diese praktische Erfahrung erweitert Ihre Kenntnisse der Bereitstellungsanforderungen neuer Produkte oder Szenarien, sodass Sie besser planen können, wie diese in der Produktionsumgebung gehostet werden sollen.

Testumgebungsanleitungen ermöglichen die Erstellung repräsentativer Umgebungen zum Entwickeln und Testen von Anwendungen, auch als Entwicklungs-/Testumgebungen bezeichnet.
  
![Testumgebungsanleitungen für die Microsoft-Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

Wechseln Sie zum [Test Labor Leitfaden](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) für eine visuelle Karte aller Artikel im Microsoft 365 for Enterprise Test Lab-Ratgeber Stapel.

[![Testumgebungsanleitungen für Microsoft 365 Enterprise](../media/m365-enterprise-test-lab-guides/microsoft-365-enterprise-tlg-stack.png)](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf)

## <a name="base-configuration"></a>Standardkonfiguration

Zunächst erstellen Sie eine Testumgebung für [Microsoft 365 für Unternehmen](https://docs.microsoft.com/microsoft-365-enterprise/). Sie können zwei verschiedene Typen von Basiskonfigurationen erstellen:

- Verwenden Sie die [einfache Standardkonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md), wenn Sie die Features und Funktionen von Microsoft 365 Enterprise in einer reinen Cloudumgebung konfigurieren und demonstrieren möchten, die keine lokalen Komponenten umfasst.

- Verwenden Sie die [simulierte Unternehmensstandardkonfiguration](simulated-ent-base-configuration-microsoft-365-enterprise.md), wenn Sie die Features und Funktionen von Microsoft 365 Enterprise in einer hybriden Cloudumgebung konfigurieren und demonstrieren möchten, die lokale Komponenten wie eine Active Directory Domain Services (AD DS)-Domäne verwendet.

Sie können auch Testumgebungen für Office 365 E5 erstellen, ohne die Microsoft 365 E5-Lizenz zu Ihrer Test- oder Produktionstestumgebung hinzuzufügen.
    
## <a name="identity"></a>Identität

Wie Sie identitätsbezogene Features und Funktionen demonstrieren können, erfahren Sie hier:

- [Kennworthashsynchronisierung](password-hash-sync-m365-ent-test-environment.md)
  
   Aktivieren und testen Sie die auf Kennworthash basierte Verzeichnissynchronisierung von einem AD DS-Domänencontroller aus.

- [Pass-Through-Authentifizierung](pass-through-auth-m365-ent-test-environment.md)
  
   Aktivieren und testen Sie die Pass-Through-Authentifizierung an einen AD DS-Domänencontroller.

- [Verbundauthentifizierung](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
   Aktivieren und testen Sie die Verbundauthentifizierung an einen AD DS-Domänencontroller.

- [Nahtloses einmaliges Anmelden in Azure AD](single-sign-on-m365-ent-test-environment.md)
  
   Aktivieren und testen Sie das nahtlose einmalige Anmelden in Azure AD mit einem AD DS-Domänencontroller.

- [Mehrstufige Authentifizierung](multi-factor-authentication-microsoft-365-test-environment.md)
  
   Aktivieren und testen Sie die Smartphone-basierte mehrstufige Authentifizierung für ein bestimmtes Benutzerkonto.

- [Schützen von globalen Administratorkonten](protect-global-administrator-accounts-microsoft-365-test-environment.md)
 
   Sperren Sie Ihre globalen Administratorkonten mit Richtlinien für bedingten Zugriff.

- [Rückschreiben des Kennworts](password-writeback-m365-ent-test-environment.md)

   Verwenden Sie das Rückschreiben des Kennworts, um das Kennwort in Ihrem AD DS-Benutzerkonto aus Azure AD zu ändern.

- [Kennwortzurücksetzung](password-reset-m365-ent-test-environment.md)

   Verwenden Sie die Self-Service-Kennwortzurücksetzung, um Ihr Kennwort zurückzusetzen.

- [Automatische Lizenzierung und Gruppenmitgliedschaft](automate-licenses-group-membership-microsoft-365-test-environment.md)

   Machen Sie die Verwaltung neuer Konten durch automatische Lizenzierung und dynamische Gruppenmitgliedschaft einfacher als je zuvor.

- [Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md)

   Überprüfen Sie Ihre aktuellen Benutzerkonten auf Sicherheitsrisiken.

- [Identitäts- und Gerätezugriff](identity-device-access-m365-test-environment.md)

   Erstellen Sie eine Umgebung, um empfohlene Konfigurationen für Identitäts- und Gerätezugriff sowie Richtlinien für bedingten Zugriff zu testen.


## <a name="mobile-device-management"></a>Verwaltung mobiler Geräte

Eine Veranschaulichung von Features und Funktionen im Zusammenhang mit der Verwaltung mobiler Geräte finden Sie unter:

- [Gerätekompatibilitätsrichtlinien](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   Erstellen Sie eine Benutzergruppe und eine Gerätekompatibilitätsrichtlinie für Windows 10-Geräte.
    
- [Registrieren von iOS- und Android-Geräten](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   Registrieren Sie iOS- oder Android-Geräte, und verwalten Sie sie remote.


## <a name="information-protection"></a>Schutz von Daten

Eine Veranschaulichung der schutzbezogenen Features und Funktionen finden Sie unter:

- [Erhöhte Sicherheit in Microsoft 365](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurieren der Einstellungen für höhere Sicherheit von Microsoft 365 und Prüfen der integrierten Sicherheitstools.
  
- [Datenklassifikation](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurieren und Anwenden von Bezeichnungen auf ein Dokument in einer SharePoint Online-Teamwebsite.
    
- [Privileged Access Management](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurieren von Privileged Access Management für Just-in-Time-Zugriff auf privilegierte Aufgaben mit erhöhten Rechten in Ihrer Organisation.


