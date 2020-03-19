---
title: Zusammenarbeit mit Gästen in einer Website
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords: NOCSH
description: Hier erfahren Sie, wie Sie mit Gästen in einer SharePoint-Website zusammenarbeiten.
ms.openlocfilehash: 3a7c14cc4cd31961b0d4c1054f88b5ed276b3b1a
ms.sourcegitcommit: 21338a9287017a66298e0ff557e80051946ebf13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "42604754"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="126fa-103">Zusammenarbeit mit Gästen in einer Website</span><span class="sxs-lookup"><span data-stu-id="126fa-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="126fa-104">Wenn Sie mit Gästen in Dokumenten, Daten und Listen zusammenarbeiten müssen, können Sie eine SharePoint-Website verwenden.</span><span class="sxs-lookup"><span data-stu-id="126fa-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="126fa-105">Moderne SharePoint-Websites sind mit Office 365 Gruppen verbunden, die die Website Mitgliedschaft verwalten und zusätzliche Tools für die Zusammenarbeit wie ein freigegebenes Postfach und einen Kalender bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="126fa-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="126fa-106">In diesem Artikel werden die Microsoft 365-Konfigurationsschritte durchlaufen, die erforderlich sind, um eine SharePoint-Website für die Zusammenarbeit mit Gästen einzurichten.</span><span class="sxs-lookup"><span data-stu-id="126fa-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="126fa-107">Videodemonstration</span><span class="sxs-lookup"><span data-stu-id="126fa-107">Video demonstration</span></span>

<span data-ttu-id="126fa-108">Dieses Video zeigt die in diesem Dokument beschriebenen Konfigurationsschritte.</span><span class="sxs-lookup"><span data-stu-id="126fa-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="126fa-109">Azure Organizational Relationships-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="126fa-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="126fa-110">Die Freigabe in Microsoft 365 wird auf der höchsten Ebene durch die Einstellungen für organisatorische Beziehungen in Azure Active Directory gesteuert.</span><span class="sxs-lookup"><span data-stu-id="126fa-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="126fa-111">Wenn die Gast Freigabe in Azure AD deaktiviert oder eingeschränkt ist, werden alle Freigabeeinstellungen, die Sie in Microsoft 365 konfigurieren, außer Kraft gesetzt.</span><span class="sxs-lookup"><span data-stu-id="126fa-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="126fa-112">Überprüfen Sie die Einstellungen für Organisationsbeziehungen, um sicherzustellen, dass die Freigabe für Gäste nicht blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="126fa-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Screenshot der Seite mit den Einstellungen für die Azure Active Directory-Organisationsbeziehungen](../media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="126fa-114">So legen Sie Einstellungen für die Organisationsbeziehung fest</span><span class="sxs-lookup"><span data-stu-id="126fa-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="126fa-115">Melden Sie sich bei Microsoft Azure [https://portal.azure.com](https://portal.azure.com)an an.</span><span class="sxs-lookup"><span data-stu-id="126fa-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="126fa-116">Klicken Sie im linken Navigationsbereich auf **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="126fa-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="126fa-117">Klicken Sie im Bereich **Übersicht** auf **Organisationsbeziehungen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="126fa-118">Klicken Sie im Bereich **Organisationsbeziehungen** auf **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="126fa-119">Stellen Sie sicher, dass **Administratoren und Benutzer in der Rolle "Gast einladender" eingeladen** werden und **Mitglieder einladen können** , beide auf " **Ja**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="126fa-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="126fa-120">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="126fa-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="126fa-121">Beachten Sie die Einstellungen im Abschnitt Einschränkungen für die **Zusammenarbeit** .</span><span class="sxs-lookup"><span data-stu-id="126fa-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="126fa-122">Stellen Sie sicher, dass die Domänen der Gäste, mit denen Sie zusammenarbeiten möchten, nicht blockiert werden.</span><span class="sxs-lookup"><span data-stu-id="126fa-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="126fa-123">Gast Einstellungen für Office 365 Gruppen</span><span class="sxs-lookup"><span data-stu-id="126fa-123">Office 365 Groups guest settings</span></span>

<span data-ttu-id="126fa-124">Moderne SharePoint-Websites verwenden Office 365 Gruppen, um den Website Zugriff zu steuern.</span><span class="sxs-lookup"><span data-stu-id="126fa-124">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="126fa-125">Die Gast Einstellungen für Office 365 Gruppen müssen aktiviert sein, damit der Gastzugriff auf SharePoint-Websites funktioniert.</span><span class="sxs-lookup"><span data-stu-id="126fa-125">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Screenshot der Gasteinstellungen für Office 365-Gruppen im Microsoft 365 Admin Center](../media/office-365-groups-guest-settings.png)

<span data-ttu-id="126fa-127">So legen Sie die Gast Einstellungen für Office 365 Gruppen fest</span><span class="sxs-lookup"><span data-stu-id="126fa-127">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="126fa-128">Erweitern Sie im Microsoft 365 Admin Center in der linken Navigationsleiste **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-128">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="126fa-129">Klicken Sie auf **Dienste &-Add-ins**.</span><span class="sxs-lookup"><span data-stu-id="126fa-129">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="126fa-130">Klicken Sie in der Liste auf **Office 365 Gruppen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-130">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="126fa-131">Stellen Sie sicher, dass die Gruppen **Mitglieder außerhalb Ihrer Organisation Zugriff auf Gruppeninhalte** haben und Gruppen **Besitzer Personen außerhalb Ihrer Organisation hinzufügen zulassen** Kontrollkästchen aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="126fa-131">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="126fa-132">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Änderungen speichern**.</span><span class="sxs-lookup"><span data-stu-id="126fa-132">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="126fa-133">SharePoint-Freigabeeinstellungen auf Organisationsebene</span><span class="sxs-lookup"><span data-stu-id="126fa-133">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="126fa-134">Damit Gästezugriff auf SharePoint-Websites haben, müssen die SharePoint-Freigabeeinstellungen auf Organisationsebene für die Freigabe für Gäste zulässig sein.</span><span class="sxs-lookup"><span data-stu-id="126fa-134">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="126fa-135">Die Einstellungen auf Organisationsebene bestimmen, welche Einstellungen für einzelne Websites verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="126fa-135">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="126fa-136">Websiteeinstellungen dürfen nicht so restriktiv wie die Einstellungen auf Organisationsebene sein.</span><span class="sxs-lookup"><span data-stu-id="126fa-136">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="126fa-137">Wenn Sie die Freigabe nicht authentifizierter Dateien und Ordner zulassen möchten, wählen Sie **jeden**aus.</span><span class="sxs-lookup"><span data-stu-id="126fa-137">If you want to allow unauthenticated file and folder sharing, choose **Anyone**.</span></span> <span data-ttu-id="126fa-138">Wenn Sie sicherstellen möchten, dass sich alle Personen außerhalb Ihrer Organisation authentifizieren müssen, wählen Sie **neue und vorhandene Gäste**aus.</span><span class="sxs-lookup"><span data-stu-id="126fa-138">If you want to ensure that all people outside your organization have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="126fa-139">Wählen Sie die frei zügigste Einstellung aus, die von einer beliebigen Website in Ihrer Organisation benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="126fa-139">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Screenshot der SharePoint-Freigabeeinstellungen auf Organisationsebene](../media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="126fa-141">So legen Sie Freigabeeinstellungen für SharePoint-Organisationsebene fest</span><span class="sxs-lookup"><span data-stu-id="126fa-141">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="126fa-142">Klicken Sie im Microsoft 365 Admin Center in der linken Navigationsleiste unter **Admin Centers**auf **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="126fa-142">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="126fa-143">Klicken Sie im SharePoint Admin Center links in der Navigation auf **Freigabe**.</span><span class="sxs-lookup"><span data-stu-id="126fa-143">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="126fa-144">Stellen Sie sicher, dass die externe Freigabe für SharePoint auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="126fa-144">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="126fa-145">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="126fa-145">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="126fa-146">Erstellen einer Website</span><span class="sxs-lookup"><span data-stu-id="126fa-146">Create a site</span></span>

<span data-ttu-id="126fa-147">Im nächsten Schritt erstellen Sie die Website, die Sie für die Zusammenarbeit mit Gästen verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="126fa-147">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="126fa-148">So erstellen Sie eine Website</span><span class="sxs-lookup"><span data-stu-id="126fa-148">To create a site</span></span>
1. <span data-ttu-id="126fa-149">Klicken Sie im SharePoint Admin Center unter **Websites** auf **Aktive Websites**.</span><span class="sxs-lookup"><span data-stu-id="126fa-149">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="126fa-150">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-150">Click **Create**.</span></span>
3. <span data-ttu-id="126fa-151">Klicken Sie auf **Team Website**.</span><span class="sxs-lookup"><span data-stu-id="126fa-151">Click **Team site**.</span></span>
4. <span data-ttu-id="126fa-152">Geben Sie einen Websitenamen ein, und geben Sie einen Namen für den Gruppenbesitzer (Websitebesitzer) ein.</span><span class="sxs-lookup"><span data-stu-id="126fa-152">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="126fa-153">Wählen Sie unter **Erweiterte Einstellungen**aus, ob es sich um eine öffentliche oder private Website handeln soll.</span><span class="sxs-lookup"><span data-stu-id="126fa-153">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="126fa-154">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="126fa-154">Click **Next**.</span></span>
7. <span data-ttu-id="126fa-155">Klicken Sie auf **Fertig stellen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-155">Click **Finish**.</span></span>

<span data-ttu-id="126fa-156">Wir laden Benutzer später ein.</span><span class="sxs-lookup"><span data-stu-id="126fa-156">We'll invite users later.</span></span> <span data-ttu-id="126fa-157">Als nächstes ist es wichtig, die Freigabeeinstellungen auf Standortebene für diese Website zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="126fa-157">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="126fa-158">Freigabeeinstellungen für SharePoint-Websiteebene</span><span class="sxs-lookup"><span data-stu-id="126fa-158">SharePoint site level sharing settings</span></span>

<span data-ttu-id="126fa-159">Überprüfen Sie die Freigabeeinstellungen auf Standortebene, um sicherzustellen, dass die gewünschten Zugriffstypen für diese Website zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="126fa-159">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="126fa-160">Wenn Sie beispielsweise die Einstellungen auf Organisationsebene auf " **jeder**" festlegen, aber alle Gäste für diese Website authentifizieren möchten, stellen Sie sicher, dass die Freigabeeinstellungen auf Standortebene auf " **neu" und "vorhandene Gäste**" festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="126fa-160">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="126fa-161">Beachten Sie, dass die Website nicht für nicht authentifizierte Personen freigegeben werden kann (**jede** Einstellung), sondern einzelne Dateien und Ordner können.</span><span class="sxs-lookup"><span data-stu-id="126fa-161">Note that the site cannot be shared with unauthenticated people (**Anyone** setting), but individual files and folders can.</span></span>

![Screenshot der externen SharePoint-Freigabeeinstellungen](../media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="126fa-163">So legen Sie Freigabeeinstellungen auf Websiteebene fest</span><span class="sxs-lookup"><span data-stu-id="126fa-163">To set site-level sharing settings</span></span>
1. <span data-ttu-id="126fa-164">Erweitern Sie im SharePoint Admin Center links in der Navigation **Sites** und klicken Sie auf **Aktive Sites**.</span><span class="sxs-lookup"><span data-stu-id="126fa-164">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="126fa-165">Wählen Sie die Website aus, die Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="126fa-165">Select the site that you just created.</span></span>
3. <span data-ttu-id="126fa-166">Klicken Sie im Menüband auf **Freigabe**. </span><span class="sxs-lookup"><span data-stu-id="126fa-166">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="126fa-167">Stellen Sie sicher, dass die Freigabe auf " **jeder** " oder " **neue und vorhandene Gäste**" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="126fa-167">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="126fa-168">Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="126fa-168">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="126fa-169">Benutzer einladen</span><span class="sxs-lookup"><span data-stu-id="126fa-169">Invite users</span></span>

<span data-ttu-id="126fa-170">Die Einstellungen für die Gast Freigabe sind nun konfiguriert, sodass Sie mit dem Hinzufügen interner Benutzer und Gäste zu Ihrer Website beginnen können.</span><span class="sxs-lookup"><span data-stu-id="126fa-170">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="126fa-171">Der Website Zugriff wird über die zugehörige Office 365 Gruppe gesteuert, sodass Benutzer dort hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="126fa-171">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="126fa-172">So laden Sie interne Benutzer zu einer Gruppe ein</span><span class="sxs-lookup"><span data-stu-id="126fa-172">To invite internal users to a group</span></span>
1. <span data-ttu-id="126fa-173">Navigieren Sie zu der Website, auf der Sie Benutzer hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="126fa-173">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="126fa-174">Klicken Sie oben rechts auf **Mitglieder** .</span><span class="sxs-lookup"><span data-stu-id="126fa-174">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="126fa-175">Klicken Sie auf **Mitglieder hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-175">Click **Add members**.</span></span>
4. <span data-ttu-id="126fa-176">Geben Sie die Namen oder e-Mail-Adressen der Benutzer ein, die Sie zur Website einladen möchten, und klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="126fa-176">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="126fa-177">Gastbenutzer können nicht von der Website hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="126fa-177">Guest users can't be added from the site.</span></span> <span data-ttu-id="126fa-178">Sie müssen Sie mit Outlook im Internet hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="126fa-178">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="126fa-179">So laden Sie Gäste zu einer Gruppe ein</span><span class="sxs-lookup"><span data-stu-id="126fa-179">To invite guests to a group</span></span>
1. <span data-ttu-id="126fa-180">Klicken Sie in Outlook im Internet unter **Gruppen**auf die Gruppe, der Sie Mitglieder hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="126fa-180">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="126fa-181">Öffnen Sie die Gruppen Visitenkarte, und klicken Sie dann unter **Weitere Optionen** (...) auf **Mitglieder hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-181">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="126fa-182">Geben Sie die e-Mail-Adressen der Gäste ein, die Sie einladen möchten, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-182">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="126fa-183">Klicken Sie auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="126fa-183">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="126fa-184">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="126fa-184">See Also</span></span>

[<span data-ttu-id="126fa-185">Bewährte Methoden zum Freigeben von Dateien und Ordnern für nicht authentifizierte Benutzer</span><span class="sxs-lookup"><span data-stu-id="126fa-185">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="126fa-186">Einschränken des Risikos der versehentlichen Gefährdung von Dateien bei der Freigabe für Gäste</span><span class="sxs-lookup"><span data-stu-id="126fa-186">Limit accidental exposure to files when sharing with guests</span></span>](share-limit-accidental-exposure.md)

[<span data-ttu-id="126fa-187">Erstellen einer sicheren Gastfreigabeumgebung</span><span class="sxs-lookup"><span data-stu-id="126fa-187">Create a secure guest sharing environment</span></span>](create-secure-guest-sharing-environment.md)

[<span data-ttu-id="126fa-188">Erstellen eines B2B-Extranets mit verwalteten Gästen</span><span class="sxs-lookup"><span data-stu-id="126fa-188">Create a B2B extranet with managed guests</span></span>](b2b-extranet.md)
