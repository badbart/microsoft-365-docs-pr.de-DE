---
title: Hinzufügen von Speicherplatz für Ihr Abonnement
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- commerce
- Adm_TOC
- SPO_Content
ms.custom:
- MAX_CampaignID
- okr_SMB
- AdminSurgePortfolio
search.appverid:
- MET150
description: Hier erfahren Sie, wie Sie den Dateispeicher in Ihrem Microsoft 365-Abonnement hinzufügen und reduzieren. Bei zusätzlichem Dateispeicher können Sie weitere Inhalte in SharePoint Online und OneDrive speichern.
ms.date: ''
ms.openlocfilehash: 7f9973054bfe97beae36e28b73a3eb2025a13e73
ms.sourcegitcommit: 25afc0c34edc7f8a5eb389d8c701175256c58ec8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "47324468"
---
# <a name="add-storage-space-for-your-subscription"></a>Hinzufügen von Speicherplatz für Ihr Abonnement

::: moniker range="o365-21vianet"

> [!NOTE]
> Das Admin Center wird geändert. Wenn Ihre Erfahrung nicht den hier aufgeführten Details entspricht, lesen Sie [über das neue Microsoft 365 Admin Center](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Wenn sich im Laufe der Zeit herausstellt, dass Sie nicht mehr über genügend Speicherplatz für Ihre SharePoint Online-Websitesammlungen verfügen, können Sie im Rahmen Ihres Abonnements zusätzlich weiteren Speicherplatz erwerben, wenn Sie gemäß Ihrem Plan dazu berechtigt sind.  Wenn in der Liste der verfügbaren Add-ons der **Office 365 zusätzliche Dateispeicherung** nicht angezeigt wird, bedeutet dies, dass Ihr Plan nicht berechtigt ist. Weitere Informationen finden Sie unter [ist mein Plan berechtigt?](#is-my-plan-eligible-for-office-365-extra-file-storage)

> [!NOTE]
> Wenn Sie Ihr Abonnement über Volumenlizenzierung oder einen CSP erworben haben, können Sie **Office 365 zusätzlichen Dateispeicher** für Ihre Organisation nicht direkt von Microsoft kaufen. Wenden Sie sich an Ihren Vertreter oder Partner, um Hilfe zu erhalten.

## <a name="before-you-begin"></a>Bevor Sie beginnen:

Sie müssen ein globaler oder SharePoint-Administrator sein, um die Aufgaben in diesem Artikel durchführen zu können. Weitere Informationen finden Sie unter [Informationen zu Administratorrollen](../admin/add-users/about-admin-roles.md).

## <a name="view-available-storage"></a>Anzeigen des verfügbaren Speichers

::: moniker range="o365-worldwide"

1. Wechseln Sie im SharePoint Admin Center zur Seite <a href="https://admin.microsoft.com/sharepoint?page=siteManagement&modern=true" target="_blank">aktive Websites</a> , und melden Sie sich mit einem Konto an, das über [Administratorberechtigungen](https://docs.microsoft.com/sharepoint/sharepoint-admin-role) für Ihre Organisation verfügt.

2. In der oberen rechten Ecke der Seite sehen Sie, wie viel Speicherplatz für alle Websites verwendet wird, und den Gesamtspeicher für Ihr Abonnement. Wenn in Ihrer Organisation Multi-Geo in Office 365 konfiguriert wurde, zeigt der Balken auch die Menge an Speicherplatz an, die für alle geografischen Standorte verwendet wird.

   ![Speicher Leiste auf der Seite "aktive Websites"](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > Der verwendete Speicher umfasst keine Änderungen, die innerhalb der letzten 24-48 Stunden vorgenommen wurden.

::: moniker-end

::: moniker range="o365-germany"

1. Melden Sie sich bei https://portal.office.de als globaler oder SharePoint-Administrator an, und wählen Sie dann die Kachel admin aus, um das Admin Center zu öffnen. Wenn eine Meldung angezeigt wird, dass Sie nicht über die Berechtigung zum Zugriff auf die Seite verfügen, bedeutet dies, dass Sie über keine Microsoft 365-Administratorberechtigungen in Ihrer Organisation verfügen.

2. Wählen Sie im linken Bereich unter **Admin Center**die Option **SharePoint**aus. Wenn das klassische SharePoint Admin Center angezeigt wird, wählen Sie **Jetzt öffnen** am oberen Rand der Seite aus, um das neue SharePoint Admin Center zu öffnen.

3. Wählen Sie im linken Bereich des neuen SharePoint Admin Center **Aktive Websites** aus.

4. In der oberen rechten Ecke der Seite sehen Sie, wie viel Speicherplatz für alle Websites verwendet wird, und den Gesamtspeicher für Ihr Abonnement.

   ![Speicher Leiste auf der Seite "aktive Websites"](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > Der verwendete Speicher umfasst keine Änderungen, die innerhalb der letzten 24-48 Stunden vorgenommen wurden.

::: moniker-end

::: moniker range="o365-21vianet"

1. Melden Sie sich bei https://login.partner.microsoftonline.cn/ als globaler oder SharePoint-Administrator an, und wählen Sie dann die Kachel admin aus, um das Admin Center zu öffnen. (Wenn eine Meldung angezeigt wird, dass Sie nicht über die Berechtigung zum Zugriff auf die Seite verfügen, bedeutet dies, dass Sie über keine Microsoft 365-Administratorberechtigungen in Ihrer Organisation verfügen.

2. Wählen Sie im linken Bereich unter **Admin Center**die Option **SharePoint**aus. Wenn das klassische SharePoint Admin Center angezeigt wird, wählen Sie **Jetzt öffnen** am oberen Rand der Seite aus, um das neue SharePoint Admin Center zu öffnen.

3. Wählen Sie im linken Bereich des neuen SharePoint Admin Center **Aktive Websites** aus.

4. In der oberen rechten Ecke der Seite sehen Sie, wie viel Speicherplatz für alle Websites verwendet wird, und den Gesamtspeicher für Ihr Abonnement.  

   ![Speicher Leiste auf der Seite "aktive Websites"](https://docs.microsoft.com/sharepoint/sharepointonline/media/active-sites-storage-bar.png)

   > [!NOTE]
   > Der verwendete Speicher umfasst keine Änderungen, die innerhalb der letzten 24-48 Stunden vorgenommen wurden.

::: moniker-end

Nachdem Sie festgestellt haben, wie viel Speicherplatz Sie verwenden, können Sie Speicherplatz für Ihr Abonnement hinzufügen oder entfernen. Um herauszufinden, wie viel Speicherplatz hinzugefügt werden kann, befolgen Sie die Schritte in diesem Artikel, und überprüfen Sie die Preisinformationen vor dem Kauf.
  
Informationen zum Festlegen von Speichergrenzwerten für Websitesammlungen finden Sie unter [Manage Site Collection Storage Limits](https://docs.microsoft.com/sharepoint/manage-site-collection-storage-limits).
  
## <a name="add-storage-to-your-subscription"></a>Hinzufügen von Speicher zu Ihrem Abonnement

Wenn Sie noch keinen zusätzlichen Speicherplatz für Ihr Abonnement erworben haben, können Sie dies tun.

::: moniker range="o365-worldwide"

1. Wechseln Sie im Admin Center zur Seite **Abrechnungs** - \> <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">Einkaufsdienste</a> .
2. Wählen Sie unten auf der Seite " **Einkaufsdienste** " **Add-ons**aus.
3. Wählen Sie **Office 365 zusätzlichen Dateispeicher**aus.
4. Wählen Sie auf der Seite **zusätzliche Dateispeicher Office 365** , falls angezeigt, das Basisabonnement aus, und geben Sie dann die Anzahl von Gigabyte Speicher ein, die Sie hinzufügen möchten.
5. Wählen Sie **jetzt Auschecken aus**.
6. Überprüfen Sie auf der Seite **wie sieht** das aus? die Anzahl von Gigabytes Speicher, die Sie ausgewählt haben, überprüfen Sie die Preisinformationen, und wählen Sie dann **weiter**aus.
7. Überprüfen Sie auf der Seite **vollständige Bestellung** die Summe. Wenn Sie Änderungen vornehmen müssen, wählen Sie **Bestellung bearbeiten**aus. Wenn für die Bestellung eine Bonitätsprüfung erforderlich ist, aktivieren Sie das Kontrollkästchen. Wenn Sie fertig sind, klicken Sie auf **Bestellung aufgeben** , \> **um zu admin Home zu wechseln**.

::: moniker-end

::: moniker range="o365-germany"

1. Wechseln Sie im Admin Center zur Seite **Abrechnungs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a> .  

2. Wählen Sie auf der Seite **Abonnements** das Abonnement aus, dem Sie Speicherplatz hinzufügen möchten, und wählen Sie dann **Add-ons**aus.

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Wenn **Add-ons**nicht angezeigt werden und Ihr Abonnement über einen Partner erworben wurde, wählen Sie **Volume Licensing Service Center (VLSC)** aus.
  
3. Wählen Sie **Add-ons kaufen**aus.

    ![Link "Add-ons kaufen" auf der Seite "Abonnements" des Admin Centers.](../media/f5cbc3fa-90f7-4299-976d-2482f2c69755.png)
  
4. Klicken Sie auf der Seite " **Dienste kaufen** " mit der Maus oder tippen Sie auf **Office 365 zusätzlichen Dateispeicher**, und wählen Sie dann **Jetzt kaufen**aus.
  
5. Geben Sie die Anzahl der benötigten Benutzerlizenzen ein, und wählen Sie, falls dies angezeigt wird, ein Basisabonnement aus. Wählen Sie **jetzt Auschecken aus**.
  
6. Überprüfen Sie auf der Seite **wie sieht** das aus? die Anzahl von Gigabytes Speicher, die Sie ausgewählt haben, überprüfen Sie die Preisinformationen, und wählen Sie dann **weiter**aus.

7. Wählen Sie auf der Seite **vollständige Bestellung** die Option **Bestellung platzieren**aus.

::: moniker-end

::: moniker range="o365-21vianet"

1. Navigieren Sie im Admin Center zur Seite **Abrechnung** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.

2. Wählen Sie auf der Seite **Abonnements** das Abonnement aus, dem Sie Speicherplatz hinzufügen möchten, und wählen Sie dann **Add-ons**aus.

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Wenn **Add-ons**nicht angezeigt werden und Ihr Abonnement über einen Partner erworben wurde, wählen Sie **Volume Licensing Service Center (VLSC)** aus.
  
3. Wählen Sie **Add-ons kaufen**aus.

    ![Link "Add-ons kaufen" auf der Seite "Abonnements" des Admin Centers.](../media/f5cbc3fa-90f7-4299-976d-2482f2c69755.png)
  
4. Klicken Sie auf der Seite " **Dienste kaufen** " mit der Maus oder tippen Sie auf **Office 365 zusätzlichen Dateispeicher**, und wählen Sie dann **Jetzt kaufen**aus.
  
5. Geben Sie die Anzahl der benötigten Benutzerlizenzen ein, und wählen Sie, falls dies angezeigt wird, ein Basisabonnement aus. Wählen Sie **jetzt Auschecken aus**.
  
6. Überprüfen Sie auf der Seite **wie sieht** das aus? die Anzahl von Gigabytes Speicher, die Sie ausgewählt haben, überprüfen Sie die Preisinformationen, und wählen Sie dann **weiter**aus.

7. Wählen Sie auf der Seite **vollständige Bestellung** die Option **Bestellung platzieren**aus.

::: moniker-end

## <a name="increase-or-decrease-storage"></a>Vergrößern oder Verkleinern des Speicherplatzes

Wenn Sie bereits über das **Office 365 extra File Storage** -Add-on zusätzlichen Dateispeicher erworben haben, können Sie diese Schritte verwenden, um den zusätzlichen Speicherplatz für Ihr Abonnement zu erweitern oder zu verringern. Sie können den Speicher auf so niedrig wie 1 Gigabyte reduzieren. Wenn Sie den gesamten zusätzlichen Speicherplatz entfernen möchten, [wenden Sie sich](../admin/contact-support-for-business-products.md)an den Support.

::: moniker range="o365-worldwide"

1. Navigieren Sie im Admin Center zur Seite **Abrechnung** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ihre Produkte</a>.
2. Wählen Sie auf der Registerkarte **Produkte** das Abonnement aus, das das Add-on für **Office 365 zusätzlichen Dateispeicher** enthält.
3. Wählen Sie auf der Seite Produkt Details im Abschnitt **Add-ons** die Option **Add-ons verwalten**aus.
4. Wählen Sie im Bereich **Add-ons verwalten** in der **Add-on-** Liste **Office 365 zusätzlichen Dateispeicher**aus.
5. Geben Sie im Textfeld **Menge** die Anzahl der GBs des Speicherplatzes ein, den Sie für das Abonnement benötigen.
6. Klicken Sie auf **Speichern**.

::: moniker-end

::: moniker range="o365-germany"

1. Navigieren Sie im Admin Center zur Seite **Abrechnung** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a>.

2. Wählen Sie auf der Seite **Abonnements** die Option **Add-ons**aus.

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Wenn **Add-ons**nicht angezeigt werden und Ihr Abonnement über einen Partner erworben wurde, wählen Sie **Volume Licensing Service Center (VLSC)** aus.
  
3. Wählen Sie unter **Office 365 zusätzlicher Dateispeicher**die Option **Menge ändern**aus.

    ![Link "Menge ändern"](../media/96473f2b-6ff6-45ec-b1a3-d7b204ac1f6e.png)
  
4. Geben Sie im rechten Bereich die Gesamtanzahl von Gigabytes ein, die Sie benötigen, und wählen Sie dann **Absenden**aus.

    Wenn Sie derzeit über 200 Gigabyte an zusätzlichen Dateispeicher verfügen, jedoch nur 100 Gigabyte benötigen, geben Sie **100** in das Feld ein.

5. Wählen Sie **Schließen** aus.

::: moniker-end

::: moniker range="o365-21vianet"

1. Navigieren Sie im Admin Center zur Seite **Abrechnung** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.

2. Wählen Sie auf der Seite **Abonnements** die Option **Add-ons**aus.

    ![Add-ons button used to purchase add-ons.](../media/b4d2beb4-4f6d-435a-b127-01ceebd6eebf.png)
  
    > [!NOTE]
    > Wenn **Add-ons**nicht angezeigt werden und Ihr Abonnement über einen Partner erworben wurde, wählen Sie **Volume Licensing Service Center (VLSC)** aus.
  
3. Wählen Sie unter **Office 365 zusätzlicher Dateispeicher**die Option **Menge ändern**aus.

    ![Link "Menge ändern"](../media/96473f2b-6ff6-45ec-b1a3-d7b204ac1f6e.png)
  
4. Geben Sie im rechten Bereich die Gesamtanzahl von Gigabytes ein, die Sie benötigen, und wählen Sie dann **Absenden**aus.

    Wenn Sie derzeit über 200 Gigabyte an zusätzlichen Dateispeicher verfügen, jedoch nur 100 Gigabyte benötigen, geben Sie **100** in das Feld ein.

5. Wählen Sie **Schließen** aus.

::: moniker-end

## <a name="is-my-plan-eligible-for-office-365-extra-file-storage"></a>Bin ich im Rahmen meines Plans für Office 365 Extra File Storage berechtigt?

Office 365 Extra File Storage steht im Rahmen der folgenden Abonnements zur Verfügung:
  
- Office 365 Enterprise E1

- Office 365 Enterprise E2

- Office 365 Enterprise E3

- Office 365 Enterprise E4

- Office 365 Enterprise E5

- Office für das Internet mit SharePoint-Plan 1

- Office für das Internet mit SharePoint-Plan 2

- SharePoint Online Plan 1

- SharePoint Online Plan 2

- Microsoft 365 Business Basic

- Microsoft 365 Business Standard

- Microsoft 365 Business Premium

- Microsoft 365 E3

- Microsoft 365 E5

- Microsoft 365 F1

> [!NOTE]
> Office 365 zusätzliche Dateispeicherung steht auch für gcc-, gcc-High-und DoD-Pläne zur Verfügung.

## <a name="related-content"></a>Verwandte Inhalte

[Verwalten von Websitespeicher Grenzwerten](ttps://docs.microsoft.com/sharepoint/manage-site-collection-storage-limits) (Artikel) \
[Festlegen des Standardspeicher Platzes für OneDrive-Benutzer](https://docs.microsoft.com/onedrive/set-default-storage-space)(Artikel)
