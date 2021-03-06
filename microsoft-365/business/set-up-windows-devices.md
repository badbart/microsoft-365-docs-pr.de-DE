---
title: Einrichten von Windows-Geräten für Microsoft 365 Business Premium-Benutzer
f1.keywords:
- CSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: In diesem Artikel erfahren Sie, wie Sie Windows-Geräte mit Windows 10 pro für Microsoft 365 Business Premium-Benutzer einrichten, sodass zentralisierte Verwaltungs-und Sicherheitssteuerelemente aktiviert werden können.
ms.openlocfilehash: 85ac3c964792a132d5699703e543289020e38f57
ms.sourcegitcommit: e5bc49f0a25954d008b6cc09c2b98bb7bfe1aa2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "44785850"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Einrichten von Windows-Geräten für Microsoft 365 Business Premium-Benutzer

## <a name="prerequisites-for-setting-up-windows-devices-for-microsoft-365-business-premium-users"></a>Voraussetzungen für das Einrichten von Windows-Geräten für Microsoft 365 Business Premium-Benutzer

Bevor Sie Windows-Geräte für Microsoft 365 Business Premium-Benutzer einrichten können, müssen Sie sicherstellen, dass auf allen Windows-Geräten Windows 10 pro, Version 1703 (Creators Update), installiert ist. Windows 10 pro ist eine Voraussetzung für die Bereitstellung von Windows 10 Business, einer Reihe von Cloud-Diensten und Geräteverwaltungsfunktionen, die Windows 10 pro ergänzen und die zentralisierte Verwaltung und Sicherheitskontrollen von Microsoft 365 Business Premium ermöglichen.
  
Wenn Sie über Windows-Geräte mit Windows 7 pro, Windows 8 pro oder Windows 8.1 pro verfügen, berechtigt Ihr Microsoft 365 Business Premium-Abonnement zu einem Windows 10-Upgrade.
  
Weitere Informationen zum Upgrade von Windows-Geräten auf Windows 10 Pro Creators Update erhalten Sie, indem Sie die Schritte in diesem Thema ausführen: [Aktualisieren von Windows-Geräten auf Windows Pro Creators Update](upgrade-to-windows-pro-creators-update.md).
  
Stellen Sie sicher, dass das [Gerät mit Azure AD verbunden ist](#verify-the-device-is-connected-to-azure-ad) , um zu überprüfen, ob das Upgrade ausgeführt wurde, oder ob das Upgrade erfolgreich war.

Sehen Sie sich ein kurzes Video über die Verbindung von Windows mit Microsoft 365 an.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3yXh3] 

Wenn Sie dieses Video hilfreich fanden, sehen Sie sich bitte die [komplette Schulungsserie für kleine Unternehmen und jene, die neu bei Microsoft 365 sind](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816), an.
  
## <a name="join-windows-10-devices-to-your-organizations-azure-ad"></a>Verbinden von Windows 10-Geräten in Ihrer Organisation mit Azure AD

Wenn alle Windows-Geräte in Ihrer Organisation entweder auf Windows 10 pro Creators-Update aktualisiert wurden oder bereits Windows 10 pro Creators Update ausgeführt wurden, können Sie diese Geräte mit der Azure-Active Directory Ihrer Organisation verbinden. Sobald die Geräte verbunden sind, werden Sie automatisch auf Windows 10 Business aktualisiert, das Teil Ihres Microsoft 365 Business Premium-Abonnements ist.
  
### <a name="for-a-brand-new-or-newly-upgraded-windows-10-pro-device"></a>Ganz neue oder neu aktualisierte Windows 10 Pro-Geräte

Führen Sie für ganze neue Geräte mit Windows 10 Pro Creators Update oder für Geräte, die auf Windows 10 Pro Creators Update aktualisiert wurden, für die die Windows 10-Geräteinstallation jedoch noch nicht ausgeführt wurde, die folgenden Schritte aus.
  
1. Führen Sie die Windows 10-Geräteinstallation aus, bis die Seite **Wie soll das Setup erfolgen** angezeigt wird. 
    
    ![On the How would you like to set up page, choose Set up for an organization](../media/1b0b2dba-00bb-4a99-a729-441479220cb7.png)
  
2. Wählen Sie hier **Einrichten für eine Organisation** aus, und geben Sie dann Ihren Benutzernamen und Ihr Kennwort für Microsoft 365 Business Premium ein. 
    
3. Beenden Sie die Windows 10-Geräteinstallation.
    
   Sobald Sie fertig sind, wird der Benutzer in Ihrer Organisation mit Azure AD verbunden. Ziehen Sie zur Sicherheit [Sicherstellen, dass das Gerät mit Azure AD verbunden ist](#verify-the-device-is-connected-to-azure-ad) zurate. 
  
### <a name="for-a-device-already-set-up-and-running-windows-10-pro"></a>Geräte, die bereits eingerichtet wurden und Windows 10 Pro ausführen

 **Herstellen der Verbindung der Benutzer zu Azure AD:**
  
1. Klicken Sie auf dem Windows-PC des Benutzers, auf dem Windows 10 Pro, Version 1703 (Creators Update) ausgeführt wird (siehe [Voraussetzungen](pre-requisites-for-data-protection.md)), auf das Windows-Logo und dann auf das Symbol "Einstellungen".
  
   ![In the Start menu, click Windows Settings icon](../media/74e1ce9a-1554-4761-beb9-330b176e9b9d.png)
  
2. Wechseln Sie unter **Einstellungen** zu **Konten**.
  
   ![In Windows Settings, go to Accounts](../media/472fd688-d111-4788-9fbb-56a00fbdc24d.png)
  
3. Klicken Sie auf der Seite **Ihre Informationen** auf **Auf Arbeits- oder Schulkonto zugreifen** \> **Verbinden**.
  
   ![Choose Connect under Access work or school](../media/af3a4e3f-f9b9-4969-b3e2-4ef99308090c.png)
  
4. Wählen Sie im Dialogfeld **Geschäfts-, Schul- oder Unikonto einrichten** unter **Alternative Aktionen** die Option **Dieses Gerät in Azure Active Directory einbinden**.
  
   ![Click Join this device to Azure Active Directory](../media/fb709a1b-05a9-4750-9cb9-e097f4412cba.png)
  
5. On the **Let's get you signed in** page, enter your work or school account \> **Next**.
  
   On the **Enter password** page, enter your password \> **Sign in**.
  
   ![Enter your work or school email on the Let's get you signed in page](../media/f70eb148-b1d2-4ba3-be38-7317eaf0321a.png)
  
6. Überprüfen Sie auf der Seite **Stellen Sie sicher, dass es sich um Ihre Organisation handelt** , dass die Informationen richtig sind, und klicken Sie auf **beitreten**.
  
   Klicken Sie auf der Seite **Sie sind fertig!** auf **Fertig**.
  
   ![On the Make sure this is your organization screen, click Join](../media/c749c0a2-5191-4347-a451-c062682aa1fb.png)
  
Wenn Sie Dateien nach OneDrive for Business hochgeladen haben, synchronisieren Sie diese wieder. Wenn Sie ein Drittanbietertool zum Migrieren von Profil und Dateien verwendet haben, synchronisieren Sie diese ebenfalls mit dem neuen Profil.
  
## <a name="verify-the-device-is-connected-to-azure-ad"></a>Stellen Sie sicher, dass das Gerät mit Azure AD verbunden ist

Um Ihren Synchronisierungsstatus zu überprüfen, klicken Sie auf der Seite **Zugriff auf Arbeit oder Schule** in **Einstellungen**auf den Bereich **verbunden mit** _ \<organization name\> _, um die Schaltflächen **Informationen** anzuzeigen und die **Verbindung zu trennen**. Klicken Sie auf **Info**, um Ihren Synchronisierungsstatus abzurufen. 
  
Klicken Sie auf der Seite "Synchronisierungsstatus" auf "Synchronisieren", um die neuesten Verwaltungsrichtlinien für Mobilgeräte auf den Computer abzurufen.
  
Um mit dem Microsoft 365 Business Premium-Konto zu beginnen, wechseln Sie zur Windows-Schaltfläche **Start** , klicken Sie mit der rechten Maustaste auf Ihr aktuelles Kontobild, und wechseln Sie dann zu **Konto**. Melden Sie sich mit der E-Mail-Adresse und dem Kennwort Ihrer Organisation an.
  
![Click Info button to view synchronization status](../media/818f7043-adbf-402a-844a-59d50034911d.png)
  
## <a name="verify-the-device-is-upgraded-to-windows-10-business"></a>Sicherstellen, dass das Gerät auf Windows 10 Business aktualisiert wurde

Stellen Sie sicher, dass Ihre Azure AD beige tretenen Windows 10-Geräte als Teil Ihres Microsoft 365 Business Premium-Abonnements auf Windows 10 Business aktualisiert wurden.
  
1. Wechseln Sie zu **Einstellungen** \> **System** \> **Info**.
    
2. Überprüfen Sie, ob unter **Edition** **Windows 10 Business** angezeigt wird.
    
    ![Verify that Windows edition is Windows 10 Business.](../media/ff660fc8-d3ba-431b-89a5-f5abded96c4d.png)
  
## <a name="next-steps"></a>Nächste Schritte

Informationen zum Einrichten von mobilen Geräten finden Sie unter [Einrichten von mobilen Geräten für Microsoft 365 Business Premium-Benutzer](set-up-mobile-devices.md)zum Festlegen des Geräteschutzes oder von Richtlinien für den App-Schutz unter [Verwalten von Microsoft 365 für Unternehmen](manage.md).
  
## <a name="for-more-on-setting-up-and-using-microsoft-365-business-premium"></a>Weitere Informationen zum Einrichten und Verwenden von Microsoft 365 Business Premium

[Microsoft 365 für Unternehmen-Schulungsvideos](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816)
