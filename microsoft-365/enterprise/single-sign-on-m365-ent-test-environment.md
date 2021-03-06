---
title: Nahtloses einmaliges Anmelden in Azure AD für Ihre Microsoft 365-Testumgebung
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Zusammenfassung: Konfigurieren und Testen des nahtlosen einmaliges Anmeldens in Azure AD für Ihre Microsoft 365-Testumgebung.'
ms.openlocfilehash: 3ba229a62f66cad715f604bab91cd12032da7be8
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46685772"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Nahtloses einmaliges Anmelden in Azure AD für Ihre Microsoft 365-Testumgebung

*Diese Test Umgebungs Anleitung kann sowohl für Microsoft 365 für Unternehmen als auch für Office 365 Enterprise Testumgebungen verwendet werden.*

Beim nahtlosen einmaligen Anmelden von Azure AD werden Benutzer automatisch angemeldet, wenn sie auf ihren Computern oder Geräten arbeiten, die mit ihrem Organisationsnetzwerk verbunden sind. Das nahtlose einmalige Anmelden in Azure AD bietet Benutzern einfachen Zugriff auf cloudbasierte Anwendungen, ohne dass dafür zusätzliche lokale Komponenten erforderlich sind.

Dieser Artikel beschreibt, wie Sie Ihre Microsoft 365-Testumgebung für das nahtlose einmalige Anmelden in Azure AD konfigurieren.

Die Einrichtung besteht aus zwei Phasen:

1.    Erstellen Sie die simulierte Microsoft 365-Testunternehmensumgebung mit Kennworthashsynchronisierung.
2.    Konfigurieren Sie Azure AD Connect auf APP1 für das nahtlose einmalige Anmelden in Azure AD.
    
![Testumgebungsanleitungen für die Microsoft-Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Klicken Sie [hier](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Microsoft 365 Enterprise zu erhalten.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Phase 1: Konfigurieren Sie Kennworthashsynchronisierung für Ihre Microsoft 365-Testumgebung

Befolgen Sie die Anweisungen unter [Kennworthashsynchronisierung für Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Hier ist die resultierende Konfiguration.
  
![Das simulierte Unternehmen mit Kennworthashsynchronisierung für die Testumgebung](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Diese Konfiguration besteht aus:  
  
- Eine Testversion oder ein kostenpflichtiges Abonnement für Microsoft 365 E5.
- Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks besteht. 
- Azure AD Connect wird auf APP1 ausgeführt, um die Active Directory Domain Services (AD DS)-Domäne TESTLAB mit dem Azure AD-Mandanten Ihrer Microsoft 365-Abonnements in regelmäßigen Abständen zu synchronisieren.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Phase 2: Konfigurieren Sie Azure AD Connect auf APP1 für das nahtlose einmalige Anmelden in Azure AD.

In dieser Phase konfigurieren Sie Azure AD Connect auf APP1 für das nahtlose einmalige Anmelden in Azure AD und vergewissern sich dann, dass es funktioniert.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurieren von Azure AD Connect auf APP1

1. Melden Sie sich über das [Azure-Portal](https://portal.azure.com) mit Ihrem globalen Administratorkonto an, und stellen Sie dann mit dem Konto „TESTLAB\User1“ eine Verbindung zu APP1 her.

2. Führen Sie Azure AD Connect über den Desktop von APP1 aus.

3. Klicken Sie auf der Seite **Willkommen** auf **Konfigurieren**.

4. Klicken Sie auf der Seite **Weitere Aufgaben** auf **Benutzeranmeldung ändern**, und klicken Sie dann auf **Weiter**.

5. Geben Sie auf der Seite **Mit Azure AD verbinden** die Anmeldeinformationen für das globale Administratorkonto ein, und klicken Sie dann auf **Weiter**.

6. Wählen Sie auf der Seite **Benutzeranmeldung** die Option **Einmaliges Anmelden aktivieren**, und klicken Sie dann auf **Weiter**.

7. Klicken Sie auf der Seite **Einmaliges Anmelden aktivieren** auf **Anmeldeinformationen eingeben**.

8. Geben Sie im Dialogfeld **Windows-Sicherheit** den Benutzer **Benutzer1** und das Kennwort für das Konto „Benutzer1“ ein, und klicken Sie dann auf **OK**. Klicken Sie auf **Weiter**.

9. Klicken Sie auf der Seite **Bereit zur Konfiguration** auf **Konfigurieren**.

10. Klicken Sie auf der Seite **Konfiguration abgeschlossen** auf **Beenden**.

11. Klicken Sie im Azure-Portal im linken Bereich auf **Azure Active Directory > Azure AD Connect**. Überprüfen Sie, ob die Funktion **Einmaliges Anmelden** als **Aktiviert** angezeigt wird.

Testen Sie als nächstes die Möglichkeit, sich mit dem user1@testlab bei Ihrem Abonnement anzumelden <strong>.</strong>\<your public domain> Benutzername des User1-Kontos.

1. Klicken Sie in Internet Explorer auf APP1 auf das Symbol „Einstellungen“, und klicken Sie dann auf **Internetoptionen**.
 
2. Klicken Sie unter **Internetoptionen** auf die Registerkarte **Sicherheit**.

3. Klicken Sie auf **Lokales Intranet** und dann auf **Sites**.

4. Klicken Sie unter **Lokales Intranet** auf **Erweitert**.

5. Geben Sie unter **Diese Website zur Zone hinzufügen** die Adresse **https<span>://</span>autologon.microsoftazuread-sso.com** ein, und klicken Sie auf **Hinzufügen > Schließen > OK > OK**.

6. Melden Sie sich ab, und melden Sie sich dann erneut an. Geben Sie dieses Mal ein anderes Konto an.

7. Wenn Sie zur Anmeldung aufgefordert werden, geben Sie <strong>User1@testlab an.</strong>\<your public domain> Namen ein, und klicken Sie dann auf **weiter**. Sie sollten sich erfolgreich als "User1" anmelden können, ohne zur Eingabe eines Kennworts aufgefordert zu werden. Dies beweist, dass das nahtlose einmalige Anmelden mit Azure AD funktioniert.

Beachten Sie, dass "User1" zwar über Administratorberechtigungen für die AD DS-Domäne TESTLAB verfügt, er aber kein globaler Administrator für Azure AD ist. Daher wird das Symbol **Admin** nicht als Option angezeigt.

Nachfolgend sehen Sie die daraus resultierende Konfiguration:

![Das simulierte Unternehmen mit einer Testumgebung mit Pass-Trought-Authentifizierung](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

 
Diese Konfiguration besteht aus: 

- Eine Microsoft 365 E5-Testversion oder kostenpflichtige Abonnements mit der DNS-Domäne testlab.\<your domain name> registriert.
- Einem vereinfachtem Unternehmensintranet mit Internetzugriff, das aus virtuellen DC1-, APP1- und CLIENT1-Computern in einem Subnetz eines virtuellen Azure-Netzwerks besteht. 
- Azure AD Connect wird auf APP1 ausgeführt, um die Liste von Konten und Gruppen des Azure AD-Mandanten Ihrer Microsoft 365-Abonnements mit der AD DS-Domäne „TESTLAB“ zu synchronisieren. 
- Das nahtlose einmalige Anmelden in Azure AD wird aktiviert, damit sich Computer im simulierten Intranet bei Microsoft 365-Cloudressourcen anmelden können, ohne ein Kennwort für ein Benutzerkonto anzugeben.

## <a name="next-step"></a>Nächster Schritt

Sehen Sie sich weitere [Identitäts](m365-enterprise-test-lab-guides.md#identity)features und- funktionen in Ihrer Testumgebung an.

## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen für Microsoft 365 Enterprise](m365-enterprise-test-lab-guides.md)

[Übersicht über Microsoft 365 Enterprise](microsoft-365-overview.md)

[Dokumentation zu Microsoft 365 für Unternehmen](https://docs.microsoft.com/microsoft-365-enterprise/)


