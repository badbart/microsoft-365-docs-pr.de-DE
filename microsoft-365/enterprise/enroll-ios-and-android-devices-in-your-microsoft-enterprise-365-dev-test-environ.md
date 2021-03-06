---
title: Registrieren von IOS-und Android-Geräten in Ihrer Microsoft 365 for Enterprise-Testumgebung
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Verwenden Sie diese Test Umgebungs Anleitung, um Geräte in Ihrer Microsoft 365-Testumgebung zu registrieren und Remote zu verwalten.
ms.openlocfilehash: b4a95b2c7e58239c0a8d0d3b5045e7337f43de6b
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686010"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Registrieren von IOS-und Android-Geräten in Ihrer Microsoft 365 for Enterprise-Testumgebung

*Diese Test Umgebungs Anleitung kann nur für Microsoft 365 für Enterprise-Testumgebungen verwendet werden.*

Wenn Sie die Anweisungen in diesem Artikel befolgen, können Sie grundlegende Funktionen zur Verwaltung mobiler Geräte für IOS-und Android-Geräte in Ihrer Microsoft 365 for Enterprise-Testumgebung registrieren und testen.

![Testumgebungsanleitungen für die Microsoft-Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Klicken Sie [hier](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf), um eine visuelle Darstellung aller Artikel im Stapel der Testumgebungsanleitungen in Microsoft 365 Enterprise zu erhalten.

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1: Erstellen der Testumgebung für Microsoft 365 für Unternehmen

Wenn Sie IOS-und Android-Geräte nur auf einfache Weise mit den Mindestanforderungen registrieren möchten, befolgen Sie die Anweisungen in [Lightweight Base Configuration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Wenn Sie IOS-und Android-Geräte in einem simulierten Unternehmen registrieren möchten, befolgen Sie die Anweisungen unter [Pass-Through-Authentifizierung](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Für das Testen der automatischen Lizenzierung und der Gruppenmitgliedschaft ist keine simulierte Enterprise-Testumgebung erforderlich, die ein simuliertes, mit dem Internet verbundenes Intranet und eine Verzeichnissynchronisierung für eine Active Directory-Domänendienste (AD DS) Gesamtstruktur umfasst. Sie wird hier als Option bereitgestellt, damit Sie die automatisierte Lizenzierung und Gruppenmitgliedschaft testen und in einer Umgebung experimentieren können, die eine typische Organisation darstellt. 
>  

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Phase 2: Registrieren von IOS-und Android-Geräten

Verwenden Sie zunächst die Anweisungen unter [Install, und melden Sie sich bei der Unternehmensportal-App](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) an, um die Microsoft InTune-Unternehmensportal-App für Ihre Testumgebung anzupassen.

Verwenden Sie als nächstes die Anweisungen unter [Einrichten des Zugriffs auf Ihre Unternehmensressourcen](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) , um ein IOS-Gerät zu registrieren.

Verwenden Sie als nächstes die Anweisungen unter [Registrieren Ihres Android-Geräts in InTune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) , um ein Android-Gerät zu registrieren.

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Phase 3: Remoteverwaltung von IOS-und Android-Geräten

Microsoft Intune bietet sowohl Funktionen für eine Remotesperre und das Zurücksetzen der Kennung. Wenn jemand sein Gerät verliert, können Sie das Gerät remote sperren. Wenn jemand Ihren Code vergisst, können Sie ihn Remote zurücksetzen.
  
So sperren Sie ein IOS-oder Android-Gerät Remote:

1. Melden Sie sich beim Azure-Portal unter [https://portal.azure.com](https://portal.azure.com) mit den Anmeldeinformationen Ihres globalen Administratorkontos an.
2. Geben Sie auf der Registerkarte Azure Portal in Ihrem Browser **InTune** in das Suchfeld ein, und klicken Sie dann auf **InTune**.
3. Klicken Sie auf **Geräte > alle Geräte**.
4. Klicken Sie in der Liste der Geräte auf ein IOS-oder Android-Gerät, und klicken Sie dann auf die Aktion **Remote Sperre** .

    
So setzen Sie den Zugangscode remote zurück

1. Melden Sie sich bei Bedarf im Azure-Portal unter [https://portal.azure.com](https://portal.azure.com) mit den Anmeldeinformationen Ihres globalen Administratorkontos an.
2. Geben Sie auf der Registerkarte Azure Portal in Ihrem Browser **InTune** in das Suchfeld ein, und klicken Sie dann auf **InTune**.
3. Klicken Sie auf **Geräte > alle Geräte**.
4. Klicken Sie in der Liste der Geräte, die Sie verwalten, auf ein IOS-oder Android-Gerät, und wählen Sie **... Mehr**. Klicken Sie dann auf die Remote Aktion Kennwort-Gerät **Entfernen** .

Weitere Experimente finden Sie unter [Verfügbare Geräteaktionen](https://docs.microsoft.com/intune/device-management#available-device-actions).

    
## <a name="next-step"></a>Nächster Schritt

Untersuchen Sie weitere Features und Funktionen zur [Verwaltung mobiler Geräte](m365-enterprise-test-lab-guides.md#mobile-device-management) in Ihrer Testumgebung.

## <a name="see-also"></a>Siehe auch

[Testumgebungsanleitungen für Microsoft 365 Enterprise](m365-enterprise-test-lab-guides.md)
  
[Geräte Konformitätsrichtlinien für Ihre Microsoft 365 für Enterprise-Testumgebung](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Übersicht über Microsoft 365 Enterprise](microsoft-365-overview.md)

