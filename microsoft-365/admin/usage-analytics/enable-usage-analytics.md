---
title: Aktivieren von Microsoft 365-Nutzungsanalysen
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
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Erfahren Sie, wie Sie mit der Microsoft 365 Usage Analytics-Vorlagen-app in Power BI mit dem Sammeln von Daten für Ihren Mandanten beginnen.
ms.openlocfilehash: 1e59811d6812c6a9d68878f6766181e85efb668b
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295329"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Aktivieren von Microsoft 365-Nutzungsanalysen

::: moniker range="o365-21vianet"

> [!NOTE]
> Das Admin Center wird geändert. Wenn Ihre Erfahrung nicht den hier aufgeführten Details entspricht, lesen Sie [über das neue Microsoft 365 Admin Center](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Microsoft 365-Verwendungsanalyse ist noch nicht für Microsoft 365 US Government Community verfügbar.
  
## <a name="steps-to-enable-microsoft-365-usage-analytics"></a>Schritte zum Aktivieren von Microsoft 365-Nutzungsanalysen

Für den Einstieg in die Microsoft 365-Verwendungsanalyse müssen Sie zunächst die Daten im Microsoft 365 Admin Center verfügbar machen und dann die Vorlagen-app in Power BI initiieren.
  
### <a name="get-power-bi"></a>So erhalten Sie Power BI

Wenn Sie noch nicht über Power BI verfügen, können Sie [sich für Power BI pro registrieren](https://go.microsoft.com/fwlink/p/?linkid=845347). Wählen Sie **kostenlos testen** aus, um sich für eine Testversion anzumelden, oder **kaufen Sie jetzt** , um Power BI pro zu erhalten.
  
  
Sie können auch **Produkte** erweitern, um eine Power BI-Version zu erwerben. 

> [!NOTE]
> Sie benötigen eine Power BI pro-Lizenz zum Installieren, anpassen und Verteilen einer Vorlagen-app. Weitere Informationen finden Sie unter [Voraussetzungen](https://docs.microsoft.com/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Sie benötigen eine Power BI pro-Lizenz, um Ihre Inhalte freizugeben, und die Personen, mit denen Sie Sie gemeinsam nutzen, oder die Inhalte müssen sich in einem Arbeitsbereich mit einer [Premium-Kapazität](https://docs.microsoft.com/power-bi/service-premium-what-is)befinden. 
  
### <a name="enable-the-template-app"></a>Aktivieren der Vorlagen-App

Um die Vorlagen-APP zu aktivieren, müssen Sie entweder **globaler Administrator**, **berichtsleser**, **Exchange-Administrator**, **Skype for Business Administrator**oder **SharePoint-Administrator**sein. 
  
Weitere Informationen finden Sie unter [Informationen zu Administratorrollen](../add-users/about-admin-roles.md). 
  
1. Wechseln Sie im Admin Center zur Seite **Berichte** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Verwendung</a>. 
    
2. Suchen Sie auf der Seite **Nutzung** die **Microsoft 365-Verwendungsanalyse** Karte, und wählen Sie **Erste Schritte**aus.
    
3. Legen Sie im Bereich Berichte, der geöffnet wird, für **Power BI den Eintrag Daten für Microsoft 365-Verwendungsanalyse verfügbar machen** **auf** \> **Speichern**fest. 
  
Dadurch wird der Datensammlungsprozess initiiert und in 2 bis 48 Stunden je nach Größe des Mandanten abgeschlossen. Die Schaltfläche **Gehe zu Power BI** wird aktiviert (nicht mehr grau), wenn die Datenerfassung abgeschlossen ist. 
    
### <a name="initiate-the-template-app"></a>Initiieren der Vorlagen-App

Um die Vorlagen-APP zu initiieren, müssen Sie entweder **globaler Administrator**, **berichtsleser**, **Exchange-Administrator**, **Skype for Business Administrator**oder **SharePoint-Administrator**sein. 
  
1. Kopieren Sie die Mandanten-ID, und wählen Sie **zu Power BI wechseln**aus.
    
2.  Wenn Power BI angezeigt wird, melden Sie sich an. Wählen Sie Apps aus dem Navigationsmenü aus, um apps >erhalten.    
  
3. Geben Sie auf der Registerkarte **apps** in das Suchfeld Microsoft 365 ein, und wählen Sie dann **Microsoft 365 Verwendungsanalyse** \> **Abrufen**aus.

    [![Wählen Sie Get it now aus.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)
    
4.  Sobald die APP installiert ist. Klicken Sie auf die Kachel, um Sie zu öffnen.

5.  Klicken Sie auf **App durchsuchen** , um die APP mit Beispieldaten anzuzeigen. Klicken Sie auf **verbinden** , um die APP mit den Daten Ihrer Organisation zu verbinden.

6.  Geben Sie nach dem Klicken auf **verbinden**im Bildschirm **Verbindung mit Microsoft 365-Verwendungsanalyse herstellen** die Mandanten-ID (ohne Bindestriche) ein, die Sie in Schritt (1) kopiert haben, und wählen Sie **weiter**aus.
    
7. Wählen Sie auf dem nächsten Bildschirm **OAuth2** als **Authentifizierungsmethode** \> **Anmelden**aus. Wenn Sie eine andere Authentifizierungsmethode auswählen, tritt bei der Verbindung zur Vorlagen-App ein Fehler auf.
    
    ![Auswählen von Microsoft-Konto als Authentifizierungsmethode](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)
  
8. Nachdem die Vorlagen-App instanziiert wurde, ist das Microsoft 365 Usage Analytics-Dashboard in Power BI im Internet verfügbar. Das erste Laden des Dashboards dauert zwischen 2 und 30 Minuten.
  
Aggregate auf Mandantenebene sind in allen Berichten verfügbar. **Details auf Benutzerebene werden erst nach dem 1. oder 15. Tag des Kalendermonats nach der Entscheidung verfügbar**. Dies wirkt sich auf alle Berichte unter Benutzeraktivität aus (Weitere Tipps zum Anzeigen und Verwenden dieser Berichte finden Sie unter [navigieren und Verwenden der Berichte in Microsoft 365-Verwendungsanalyse](navigate-and-utilize-reports.md) ).
    
## <a name="make-the-collected-data-anonymous"></a>Anonymisieren der gesammelten Daten

Sie müssen ein globaler Administrator sein, um die für alle Berichte gesammelten Daten anonymisieren zu können. Dadurch werden identifizierbare Informationen wie Benutzer-, Gruppen-und Websitenamen in Berichten und in der Vorlagen-App ausgeblendet.
  
1. Wechseln Sie im Admin Center zu den **Einstellungen** der \> **org**-Einstellungen, und wählen Sie unter **Dienste** die Registerkarte **Berichte**aus.
    
2. Wählen Sie **Berichte**aus, und wählen Sie dann **Anonyme Bezeichner anzeigen**aus. Diese Einstellung wird sowohl auf die Verwendungsberichte als auch auf die Vorlagen-App angewendet.
  
3. Wählen Sie **Änderungen speichern** aus.
