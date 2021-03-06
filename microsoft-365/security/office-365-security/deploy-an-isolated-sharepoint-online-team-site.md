---
title: Bereitstellen einer isolierten SharePoint Online-Teamwebsite
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/30/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: Verwenden Sie dieses Schritt-für-Schritt-Bereitstellungshandbuch, um eine isolierte SharePoint Online Teamwebsite in Microsoft Office 365 zu erstellen und zu konfigurieren.
ms.openlocfilehash: f2800e74149e79e5c3f0444799f454ab8b3caf69
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203131"
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>Bereitstellen einer isolierten SharePoint Online-Teamwebsite

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


 **Zusammenfassung:** Mithilfe dieser schrittweisen Anleitung können Sie eine neue isolierte SharePoint Online-Teamwebsite bereitstellen.
  
Dieser Artikel ist eine schrittweises Bereitstellungshandbuch für das Erstellen und Konfigurieren einer isolierten SharePoint Online-Teamwebsite in Microsoft Office 365. Bei diesen Schritten wird die Verwendung der drei SharePoint-Standardgruppen und der entsprechenden Berechtigungsstufen vorausgesetzt, wobei für jede Zugriffsebene eine einzige Azure Active Directory (AD)-basierte Zugriffsgruppe vorhanden ist.
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>Phase 1: Erstellen und Füllen der Zugriffsgruppen der Teamwebsite

In dieser Phase erstellen Sie die drei Azure AD-basierten Zugriffsgruppen für die drei SharePoint-Standardgruppen und füllen sie mit den entsprechenden Benutzerkonten.
  
> [!NOTE]
> In den folgenden Schritte wird davon ausgegangen, dass alle erforderlichen Benutzerkonten bereits vorhanden und ihnen die entsprechenden Lizenzen zugewiesen sind. Wenn dies nicht der Fall ist, fügen Sie sie hinzu, und weisen Sie Lizenzen zu, bevor Sie mit Schritt 1 fortfahren. 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>Schritt 1: Auflisten der SharePoint Online-Administratoren für die Website

Bestimmen Sie den Satz von Benutzerkonten, die den SharePoint Online-Administratoren für die isolierte Teamwebsite entsprechen.
  
Wenn Sie Benutzerkonten und Gruppen über Microsoft 365 verwalten und Windows PowerShell verwenden möchten, erstellen Sie eine Liste der Benutzerprinzipalnamen (UPNs) (Beispiel UPN: belindan@contoso.com).
  
### <a name="step-2-list-the-members-for-the-site"></a>Schritt 2: Auflisten der Mitglieder für die Website

Bestimmen Sie den Satz von Benutzerkonten, die den Mitgliedern der isolierten Teamwebsite entsprechen, diejenigen, die an den in der Website gespeicherten Ressourcen zusammenarbeiten.
  
Wenn Sie Benutzerkonten und Gruppen über Microsoft 365 verwalten und PowerShell verwenden möchten, erstellen Sie eine Liste Ihrer UPNs. Wenn die Website viele Mitglieder hat, können Sie die Liste der UPNs in einer Textdatei speichern und alle mit einem einzigen PowerShell-Befehl hinzufügen.
  
### <a name="step-3-list-the-viewers-for-the-site"></a>Schritt 3: Auflisten der Betrachter für die Website

Bestimmen Sie den Satz von Benutzerkonten, die den Betrachtern der isolierten Teamwebsite entsprechen, diejenigen, die die auf der Website gespeicherten Ressourcen anzeigen, aber nicht ändern oder direkt an ihren Inhalten zusammenarbeiten können.
  
Wenn Sie Benutzerkonten und Gruppen über Microsoft 365 verwalten und PowerShell verwenden möchten, erstellen Sie eine Liste Ihrer UPNs. Wenn die Website viele Mitglieder hat, können Sie die Liste der UPNs in einer Textdatei speichern und alle mit einem einzigen PowerShell-Befehl hinzufügen.
  
Zu den Betrachtern der Website können die Unternehmensführung, Rechtsberater oder Projektbeteiligte aus mehreren Abteilungen gehören.
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>Schritt 4: Erstellen der drei Zugriffsgruppen für die Website in Azure AD

Sie müssen die folgenden Zugriffsgruppen in Azure AD erstellen:
  
- Websiteadministratoren (umfassen die Liste aus Schritt 1)
    
- Websitemitglieder (umfassen die Liste aus Schritt 2)
    
- Websitebetrachter (umfassen die Liste aus Schritt 3)
    
1. Wechseln Sie in Ihrem Browser zum Azure-Portal unter [https://portal.azure.com](https://portal.azure.com), und melden Sie sich mit den Anmeldeinformationen eines Kontos an, dem die Rolle „Unternehmensadministrator" oder „Benutzerverwaltungsadministrator" zugewiesen wurde.
    
2. Klicken Sie im Azure-Portal auf **Azure Active Directory > Gruppen**.
    
3. Klicken Sie auf dem Blatt **Gruppen - Alle Gruppen** auf **+ Neue Gruppe**.
    
4. Auf dem **neuen Gruppen** Blatt:
    
    - Wählen Sie unter **Gruppentyp** die Option **Sicherheit** aus.

    - Geben Sie den Gruppennamen unter **Name** ein.

    - Geben Sie unter **Gruppenbeschreibung** eine Beschreibung der Gruppe ein.

    - Wählen Sie **Zugewiesen** unter **Mitgliedschaftstyp** aus.
    
5. Klicken Sie auf **Erstellen**, und schließen Sie dann das Blatt **Gruppe**.
    
6. Wiederholen Sie die Schritte 3 bis 5 für weitere Gruppen.
    
> [!NOTE]
> Sie müssen das Azure-Portal verwenden, um die Gruppen zu erstellen, damit die Office-Features für diese aktiviert sind. Wenn ein SharePoint Online isolierter Standort später als streng vertrauliche Website mit einer Azure Information Protection-Bezeichnung konfiguriert wird, um Dateien zu verschlüsseln und bestimmten Gruppen Berechtigungen zuzuweisen, müssen die zulässigen Gruppen mit aktivierten Office-Features erstellt worden sein. Sie können die Einstellung für Office-Features einer Azure Active Directory-Gruppe nicht mehr ändern, nachdem sie erstellt wurde. 
  
Hier ist die resultierende Konfiguration mit den drei Websitezugriffsgruppen.
  
![Die drei Zugriffsgruppen für die Bereitstellung einer isolierten SharePoint Online-Website.](../../media/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>Schritt 5: Hinzufügen der Benutzerkonten zu den Zugriffsgruppen

Führen Sie in diesem Schritt die folgenden Aufgaben aus:
  
1. Fügen Sie die Liste der Benutzer aus Schritt 1 zur Zugriffsgruppe der Websiteadministratoren hinzu.
    
2. Fügen Sie die Liste der Benutzer aus Schritt 2 zur Zugriffsgruppe der Websitemitglieder hinzu.
    
3. Fügen Sie die Liste der Benutzer aus Schritt 3 zur Zugriffsgruppe der Websitebetrachter hinzu.
    
Wenn Sie Benutzerkonten und Gruppen über Active Directory-Domänendienste (AD DS) verwalten, fügen Sie mithilfe der normalen AD DS Benutzer-und Gruppen Verwaltungsverfahren Benutzer zu den entsprechenden Zugriffsgruppen hinzu, und warten Sie mit Ihrem Microsoft 365-Abonnement auf die Synchronisierung.
  
Wenn Sie Benutzerkonten und Gruppen über Office 365 verwalten, können Sie das Microsoft 365 Admin Center oder PowerShell verwenden. Wenn Sie doppelte Gruppennamen für eine der Zugriffsgruppen haben, sollten Sie das Microsoft 365 Admin Center verwenden.
  
Melden Sie sich für das Microsoft 365 Admin Center mit einem Benutzerkonto an, dem die Rolle "Benutzerkonto Administrator" oder "Unternehmensadministrator" zugewiesen wurde, und verwenden Sie Gruppen zum Hinzufügen der entsprechenden Benutzerkonten und Gruppen zu den entsprechenden Zugriffsgruppen.
  
Stellen Sie für PowerShell zunächst [eine Verbindung mit dem Azure Active Directory PowerShell for Graph-Modul her](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell?view=o365-worldwide#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Verwenden Sie dann den folgenden Befehlsblock, um ein einzelnes Benutzerkonto zu einer Zugriffsgruppe hinzuzufügen:
  
```powershell
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```
Wenn Sie die UPNs von Benutzerkonten für eine der Zugriffsgruppen in einer Textdatei gespeichert haben, können Sie den folgenden PowerShell-Befehlsblock verwenden, um alle gleichzeitig hinzuzufügen:
  
```powershell
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

Verwenden Sie bei Verwendung von PowerShell den folgenden Befehlsblock, um eine einzelne Gruppe zu einer Zugriffsgruppe hinzuzufügen:
  
```powershell
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

Die Ergebnisse sollten folgendermaßen aussehen:
  
- Die Azure AD-Gruppe der Websiteadministratoren enthält die Benutzerkonten und -gruppen der Websiteadministratoren.
    
- Die Azure AD-Gruppe der Websitemitglieder enthält die Benutzerkonten und -gruppen der Websitemitglieder.
    
- Die Azure AD-Gruppe der Websitebetrachter enthält die Benutzerkonten oder -gruppen, die den Websiteinhalt lediglich anzeigen können.
    
Überprüfen Sie die Liste der Gruppenmitglieder für jede Zugriffsgruppe mit dem Microsoft 365 Admin Center oder mit dem folgenden PowerShell-Befehlsblock:
  
```powershell
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

Hier ist die resultierende Konfiguration mit den drei Websitezugriffsgruppen mit Benutzerkonten und -gruppen.
  
![Die drei Zugriffsgruppen, mit Benutzerkonten ausgefüllt.](../../media/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>Phase 2: Erstellen und Konfigurieren der isolierten Teamwebsite

In dieser Phase erstellen Sie die isolierte SharePoint Online-Website und konfigurieren die Berechtigungen für die SharePoint Online-Standardberechtigungsstufen zur Verwendung der neuen Azure AD-basierten Zugriffsgruppen. Standardmäßig umfassen neue Teamwebsites eine Microsoft 365-Gruppe und andere zugehörige Ressourcen, in diesem Fall erstellen wir jedoch eine Teamwebsite ohne Microsoft 365-Gruppe. Auf diese Weise können Berechtigungen vollständig über SharePoint verwaltet werden.
  
Erstellen Sie zuerst mit den folgenden Schritten die SharePoint Online-Teamwebsite.
  
1. Melden Sie sich beim Microsoft 365 Admin Center mit einem Konto an, das auch für die Verwaltung der SharePoint Online Teamwebsite (SharePoint Online Administrator) verwendet wird. Hilfe finden Sie unter [Where to sign in to Office 365 (Wo kann ich mich bei Office 365 anmelden?)](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4).

2. Klicken Sie im Microsoft 365 Admin Center unter **Admin**Centers auf **SharePoint**.

3. Erweitern Sie im SharePoint Admin Center den Knoten **Websites** , und klicken Sie dann auf **aktive Standorte**.

4. Klicken Sie auf **Erstellen**, und wählen Sie dann **andere Optionen**aus.

5. Wählen Sie in der Liste **Vorlage auswählen** die Option **Team Website**aus.
   
6. Geben Sie unter **Websitename** einen Namen für die Teamwebsite ein. 
    
7. Geben Sie in **Primärer Administrator**das Konto ein, mit dem Sie angemeldet sind.
 
8. Klicken Sie auf **Fertig stellen**.
    
Konfigurieren Sie als Nächstes auf der neuen SharePoint Online-Teamwebsite die gewünschten Berechtigungen.
  
1. Klicken Sie in der Symbolleiste auf das Symbol „Einstellungen“ und anschließend auf **Websiteberechtigungen**.

2. Klicken Sie unter **Website Freigabe**auf **ändern, wie Mitglieder freigegeben werden können**.

3. Wählen Sie die **einzigen Websitebesitzer können Dateien, Ordner und die Website freigeben**.

4. Festlegen von **Zugriffsanforderungen** auf **aus**zulassen.

5. Klicken Sie auf **Speichern**.
    
6. Klicken Sie im Bereich **Berechtigungen** auf **Erweiterte Berechtigungseinstellungen**.
    
7. Klicken Sie auf der Registerkarte **Berechtigungen** in Ihrem Browser auf ** \<site name> Mitglieder** in der Liste.
    
8. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
9. Geben Sie im Dialogfeld **Freigeben** den Namen der Zugriffsgruppe der Websitemitglieder ein, wählen Sie ihn aus, und klicken Sie dann auf **Freigeben**.
    
10. Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.
    
11. Klicken Sie in der Liste auf ** \<site name> Besitzer** .
    
12. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
13. Geben Sie im Dialogfeld **Freigeben** den Namen der Zugriffsgruppe der Websiteadministratoren ein, wählen Sie ihn aus, und klicken Sie dann auf **Freigeben**.
    
14. Klicken Sie auf die Schaltfläche „Zurück“ in Ihrem Browser.
    
15. Klicken Sie in der Liste auf ** \<site name> Besucher** .
    
16. Klicken Sie auf der Seite **Benutzer und Gruppen** auf **Neu**.
    
17. Geben Sie im Dialogfeld **Freigeben** den Namen der Zugriffsgruppe der Websitebetrachter ein, wählen Sie ihn aus, und klicken Sie dann auf **Freigeben**.
    
18. Schließen Sie die Registerkarte **Berechtigungen** Ihres Browsers.
    
Die Ergebnisse dieser Berechtigungseinstellungen sehen folgendermaßen aus:
  
- Die SharePoint-Gruppe ** \<site name> Besitzer** enthält die Zugriffsgruppe der Websiteadministratoren, in der alle Mitglieder über die Berechtigungsstufe **Vollzugriff** verfügen.
    
- Die SharePoint-Gruppe ** \<site name> Mitglieder** enthält die Zugriffsgruppe der Websitemitglieder, in der alle Mitglieder über die Berechtigungsstufe **Bearbeiten** verfügen.
    
- Die SharePoint-Gruppe ** \<site name> Besucher** enthält die Zugriffsgruppe der Website Betrachter, in der alle Mitglieder über die Berechtigungsstufe **Lesen** verfügen.
    
- Mitglieder können keine anderen Mitglieder einladen, und Nichtmitglieder können keinen Zugriff anfordern.
    
Hier ist die resultierende Konfiguration mit den drei SharePoint-Gruppen für die Website, die für die Verwendung der Zugriffsgruppen konfiguriert ist, die mit Benutzerkonten oder Azure AD-Gruppen ausgefüllt werden.
  
![Die endgültige Konfiguration der isolierten SharePoint Online-Website mit Zugriffsgruppen und Benutzerkonten.](../../media/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
Jetzt können Sie und die Mitglieder der Website über Gruppenmitgliedschaft in einer der Zugriffsgruppen zusammenarbeiten und die Ressourcen der Website nutzen.
  
## <a name="next-step"></a>Nächster Schritt

Wenn Sie die Website-Zugriffsgruppenmitgliedschaft ändern oder einen Dokumentordner mit benutzerdefinierten Berechtigungen erstellen müssen, finden Sie entsprechende Informationen unter [Verwalten einer isolierten SharePoint Online-Teamwebsite](manage-an-isolated-sharepoint-online-team-site.md).
  
## <a name="see-also"></a>Siehe auch

[Isolierte SharePoint Online-Teamwebsites](isolated-sharepoint-online-team-sites.md)
  
[Entwerfen einer isolierten SharePoint Online-Teamwebsite](design-an-isolated-sharepoint-online-team-site.md)
  
[Verwalten einer isolierten SharePoint Online-Teamwebsite](manage-an-isolated-sharepoint-online-team-site.md)
  



