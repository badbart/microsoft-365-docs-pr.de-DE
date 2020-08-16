---
title: Verschieben einer SharePoint-Website an einen anderen geografischen Standort
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
f1.keywords:
- NOCSH
description: In diesem Artikel erfahren Sie, wie Sie eine SharePoint-Website an einen anderen geografischen Standort in ihrer Multi-Geo-Umgebung umstellen und die Erwartungen an die Änderungen an Ihre Benutzer weitergeben.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e96c422b1d2685c9fe3d4c8c45aa8437a6776621
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690267"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a><span data-ttu-id="b5ea3-103">Verschieben einer SharePoint-Website an einen anderen geografischen Standort</span><span class="sxs-lookup"><span data-stu-id="b5ea3-103">Move a SharePoint site to a different geo location</span></span>

<span data-ttu-id="b5ea3-104">Mit der geografischen Verschiebung von SharePoint-Websites können Sie SharePoint-Websites in einer Umgebung mit mehreren geografischen Standorten an andere geografische Standorte verschieben.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span>

<span data-ttu-id="b5ea3-105">Die folgenden Website-Typen können zwischen geografischen Standorten verschoben werden:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-105">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="b5ea3-106">Mit einer Microsoft 365-Gruppe verbundene Websites</span><span class="sxs-lookup"><span data-stu-id="b5ea3-106">Microsoft 365 Group-connected sites</span></span>
- <span data-ttu-id="b5ea3-107">Moderne Websites ohne eine Verbindung mit einer Microsoft 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="b5ea3-107">Modern sites without a Microsoft 365 Group association</span></span>
- <span data-ttu-id="b5ea3-108">Klassische SharePoint-Websites</span><span class="sxs-lookup"><span data-stu-id="b5ea3-108">Classic SharePoint sites</span></span>
- <span data-ttu-id="b5ea3-109">Kommunikationswebsites</span><span class="sxs-lookup"><span data-stu-id="b5ea3-109">Communication sites</span></span>

<span data-ttu-id="b5ea3-110">Sie müssen ein globaler Administrator oder SharePoint-Administrator sein, um eine Website zwischen geografischen Standorten zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-110">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="b5ea3-111">Bei der Verschiebung des geografischen Standorts einer SharePoint-Websites gibt es ein Zeitfenster von etwa 4 bis 6 Stunden, indem Schreibschutz besteht (abhängig vom Websiteinhalt).</span><span class="sxs-lookup"><span data-stu-id="b5ea3-111">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="b5ea3-112">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="b5ea3-112">Best practices</span></span>

- <span data-ttu-id="b5ea3-113">Probieren Sie das Verschieben einer SharePoint-Website mit einer Testwebsite aus, um sich mit dem Verfahren vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-113">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="b5ea3-114">Überprüfen Sie, ob die Website vor dem Planen oder Ausführen der Verschiebung verschoben werden kann.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-114">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="b5ea3-115">Planen Sie die geografische Verschiebung von Websites möglichst außerhalb der Arbeitszeiten, um die Auswirkungen auf die Benutzer möglichst gering zu halten.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-115">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="b5ea3-116">Teilen Sie den Benutzer, die von der Verschiebung betroffen sind, vorher mit, was passiert.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-116">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="b5ea3-117">Kommunikation mit Benutzern</span><span class="sxs-lookup"><span data-stu-id="b5ea3-117">Communicating to your users</span></span>

<span data-ttu-id="b5ea3-118">Wenn Sie SharePoint-Websites zwischen geografischen Standorten verschieben, ist es wichtig, dass Sie den Benutzern der Websites (in der Regel alle Benutzer, die die Website bearbeiten können) mitteilen, was sie erwartet.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-118">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="b5ea3-119">Dies kann verhindern, dass es bei den Benutzern zu Verwirrung kommt und unnötige Anrufe an den Helpdesk gerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-119">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="b5ea3-120">Senden Sie vor dem Verschieben eine E-Mail an die Benutzer der Websites, und teilen Sie ihnen die folgenden Informationen mit:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-120">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="b5ea3-121">Wann die Verschiebung voraussichtlich stattfinden soll und wie lange sie dauern wird.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-121">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="b5ea3-122">An welchen geografischen Standort die Website der Benutzer verschoben wird und welche URL zum Zugreifen auf den neuen Standort verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-122">What geo location their site is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="b5ea3-123">Die Benutzer sollten alle Dateien schließen und während der Verschiebung keine Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-123">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="b5ea3-124">Dateiberechtigungen und -freigabe ändern sich aufgrund der Verschiebung nicht.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-124">File permissions and sharing will not change because of the move.</span></span>
- <span data-ttu-id="b5ea3-125">Erwartungen im Hinblick auf die Benutzererfahrung in einer Multi-Geo-Umgebung</span><span class="sxs-lookup"><span data-stu-id="b5ea3-125">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="b5ea3-126">Vergessen Sie nicht, den Benutzern der Websites eine E-Mail zu schicken, wenn die Verschiebung erfolgreich abgeschlossen wurde, um sie darüber zu informieren, dass sie ihre Arbeit auf den Websites fortsetzen können.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-126">Be sure to send your sites' users an email when the move has successfully completed informing them that they can resume working on their sites.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="b5ea3-127">Planen der Verschiebung von SharePoint-Websites</span><span class="sxs-lookup"><span data-stu-id="b5ea3-127">Scheduling SharePoint site moves</span></span>

<span data-ttu-id="b5ea3-128">Sie können das Verschieben von SharePoint-Websites im voraus planen (wie weiter unten in diesem Artikel beschriebenen).</span><span class="sxs-lookup"><span data-stu-id="b5ea3-128">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="b5ea3-129">Sie können Verschiebungen wie folgt planen:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-129">You can schedule moves as follows:</span></span>

- <span data-ttu-id="b5ea3-130">Sie können bis zu 4.000 Verschiebungen zugleich planen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="b5ea3-131">Wenn mit dem Verschieben begonnen wird, können Sie weitere planen, bis zu maximal jeweils 4.000 ausstehenden Verschiebungen in der Warteschlange.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="b5ea3-132">Um das Verschieben einer SharePoint-Website für einen späteren Zeitpunkt zu planen, schließen Sie beim Beginn der Verschiebung einen der folgenden Parameter ein:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-132">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="b5ea3-133">`PreferredMoveBeginDate` – Die Verschiebung beginnt wahrscheinlich zu diesem Zeitpunkt.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-133">`PreferredMoveBeginDate` – The move will likely begin at this specified time.</span></span>
- <span data-ttu-id="b5ea3-134">`PreferredMoveEndDate` – Die Verschiebung wird wahrscheinlich bis zu diesem Zeitpunkt abgeschlossen sein.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-134">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis.</span></span> 

<span data-ttu-id="b5ea3-135">Die Uhrzeit muss für beide Parameter in koordinierter Weltzeit (UTC) angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-135">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="b5ea3-136">Verschieben einer Website</span><span class="sxs-lookup"><span data-stu-id="b5ea3-136">Moving the site</span></span>

<span data-ttu-id="b5ea3-137">Die geografische Verschiebung von SharePoint-Websites setzt voraus, dass Sie eine Verbindung mit der SharePoint-Admin-URL an dem Standort herstellen, an dem sich die Website befindet, und die Verschiebung von hier aus durchführen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-137">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="b5ea3-138">Wenn die URL der Website z. B. https://contosohealthcare.sharepoint.com/sites/Turbines lautet, stellen Sie eine Verbindung mit der SharePoint-Admin-URL unter https://contosohealthcare-admin.sharepoint.com: her.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-138">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`Connect-SPOService -url https://contosohealthcare-admin.sharepoint.com`

![](../media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="b5ea3-139">Überprüfen der Umgebung</span><span class="sxs-lookup"><span data-stu-id="b5ea3-139">Validating the environment</span></span>

<span data-ttu-id="b5ea3-140">Wir empfehlen, vor der Planung einer Websiteverschiebung eine Prüfung durchzuführen, um sicherzustellen, dass die Website verschoben werden kann.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-140">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="b5ea3-141">Das Verschieben von Websites wird nicht unterstützt mit:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-141">We do not support moving sites with:</span></span>
-    <span data-ttu-id="b5ea3-142">Business Connectivity Services</span><span class="sxs-lookup"><span data-stu-id="b5ea3-142">Business Connectivity Services</span></span>
-    <span data-ttu-id="b5ea3-143">InfoPath-Formularen</span><span class="sxs-lookup"><span data-stu-id="b5ea3-143">InfoPath forms</span></span> 
- <span data-ttu-id="b5ea3-144">Angewendete IRM-Vorlagen (Information Rights Management)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-144">Information Rights Management (IRM) templates applied</span></span>

<span data-ttu-id="b5ea3-145">Um sicherzustellen, dass alle geografischen Standorte kompatibel sind, führen Sie `Get-SPOGeoMoveCrossCompatibilityStatus` aus.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-145">To ensure all geo locations are compatible, run `Get-SPOGeoMoveCrossCompatibilityStatus`.</span></span> <span data-ttu-id="b5ea3-146">Hiermit werden alle geografischen Standorte aufgeführt, und es wird angezeigt, ob die Umgebung mit dem geografischen Zielstandort kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-146">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="b5ea3-147">Um für Ihre Website eine reine Überprüfung durchzuführen, verwenden Sie `Start-SPOSiteContentMove` mit dem `-ValidationOnly`-Parameter. So können Sie prüfen, ob die Website verschoben werden kann.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-147">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="b5ea3-148">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-148">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="b5ea3-149">Es wird *Erfolg* zurückgegeben, wenn die Website verschoben werden kann, oder *Fehler*, wenn Bedingungen vorhanden sind, die eine Verschiebung blockieren.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-149">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a><span data-ttu-id="b5ea3-150">Starten einer Verschiebung des geografischen Standorts einer SharePoint-Website ohne zugehöriger Microsoft 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="b5ea3-150">Start a SharePoint site geo move for a site with no associated Microsoft 365 Group</span></span>

<span data-ttu-id="b5ea3-151">Standardmäßig ändert sich die anfängliche URL für die Website in die URL des geografischen Zielstandorts.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-151">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="b5ea3-152">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-152">For example:</span></span>

<span data-ttu-id="b5ea3-153">https://Contoso.sharepoint.com/sites/projectx in https://ContosoEUR.sharepoint.com/sites/projectx</span><span class="sxs-lookup"><span data-stu-id="b5ea3-153">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projectx</span></span>

<span data-ttu-id="b5ea3-154">Bei Websites, denen keine Microsoft 365-Gruppe zugeordnet ist, können Sie die Website mit dem `-DestinationUrl`-Parameter umbenennen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-154">For sites with no Microsoft 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="b5ea3-155">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-155">For example:</span></span>

<span data-ttu-id="b5ea3-156">https://Contoso.sharepoint.com/sites/projectx in https://ContosoEUR.sharepoint.com/sites/projecty</span><span class="sxs-lookup"><span data-stu-id="b5ea3-156">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projecty</span></span>

<span data-ttu-id="b5ea3-157">Führe Sie Folgendes aus, um mit der Verschiebung der Website zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-157">To start the site move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Screenshot des PowerShell-Fensters mit dem Cmdlet „Start-SPOSiteContentMove“](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a><span data-ttu-id="b5ea3-159">Starten einer Verschiebung des geografischen Standorts einer SharePoint-Website mit zugehöriger Microsoft 365-Gruppe</span><span class="sxs-lookup"><span data-stu-id="b5ea3-159">Start a SharePoint site geo move for a Microsoft 365 Group-connected site</span></span>

<span data-ttu-id="b5ea3-160">Um eine Website zu verschieben, die mit einer Office 365-Gruppe verbundene ist, muss der globale Administrator oder SharePoint-Administrator zuerst das PDL-Attribut (Preferred Data Location, bevorzugter Datenspeicherort) der Office 365-Gruppe ändern.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-160">To move an Office 365 Group-connected site, the Global Administrator or SharePoint Administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="b5ea3-161">So Legen Sie den PDL einer Microsoft 365-Gruppe fest:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-161">To set the PDL for a Microsoft 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="b5ea3-162">Nachdem Sie den bevorzugten Datenspeicherort aktualisiert haben, können Sie mit der Websiteverschiebung beginnen:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-162">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="b5ea3-163">Abbrechen der Verschiebung des geografischen Standorts einer SharePoint-Website</span><span class="sxs-lookup"><span data-stu-id="b5ea3-163">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="b5ea3-164">Sie können die Verschiebung des geografischen Standorts einer SharePoint-Website stoppen, vorausgesetzt, dass die Verschiebung noch nicht läuft oder durch das Cmdlet `Stop-SPOSiteContentMove` abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-164">You can stop a SharePoint site geo move, provided the move is not in progress or completed by using the `Stop-SPOSiteContentMove` cmdlet.</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="b5ea3-165">Feststellen des Status SharePoint-Websiteverschiebung</span><span class="sxs-lookup"><span data-stu-id="b5ea3-165">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="b5ea3-166">Sie können den Status einer Websiteverschiebung an den geografischen Standort oder von dem geografischen Standort, mit dem Sie verbunden sind, mit den folgenden Cmdlets ermitteln:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-166">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="b5ea3-167">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (Websites, die nicht mit Gruppen verbunden sind)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-167">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="b5ea3-168">Get-SPOUnifiedGroupMoveState (Websites, die mit Gruppen verbunden sind)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-168">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="b5ea3-169">Verwenden Sie den `-SourceSiteUrl`-Parameter, um die Website anzugeben, für die Sie den Verschiebungsstatus anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-169">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="b5ea3-170">Die Statuswerte der Verschiebung werden in der folgenden Tabelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-170">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="b5ea3-171">Status</span><span class="sxs-lookup"><span data-stu-id="b5ea3-171">Status</span></span>|<span data-ttu-id="b5ea3-172">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b5ea3-172">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="b5ea3-173">Bereit zum Auslösen</span><span class="sxs-lookup"><span data-stu-id="b5ea3-173">Ready to Trigger</span></span>|<span data-ttu-id="b5ea3-174">Die Verschiebung wurde noch nicht begonnen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-174">The move has not started.</span></span>|
|<span data-ttu-id="b5ea3-175">Geplant</span><span class="sxs-lookup"><span data-stu-id="b5ea3-175">Scheduled</span></span>|<span data-ttu-id="b5ea3-176">Die Verschiebung befindet sich in der Warteschlange, wurde aber noch nicht begonnen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-176">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="b5ea3-177">In Bearbeitung (n/4)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-177">InProgress (n/4)</span></span>|<span data-ttu-id="b5ea3-178">Die Verschiebung wird ausgeführt, wenn einer der folgenden Statuswerte angezeigt wird: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span><span class="sxs-lookup"><span data-stu-id="b5ea3-178">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="b5ea3-179">Success</span><span class="sxs-lookup"><span data-stu-id="b5ea3-179">Success</span></span>|<span data-ttu-id="b5ea3-180">Die Verschiebung wurde erfolgreich ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-180">The move has completed successfully.</span></span>|
|<span data-ttu-id="b5ea3-181">Failed</span><span class="sxs-lookup"><span data-stu-id="b5ea3-181">Failed</span></span>|<span data-ttu-id="b5ea3-182">Beim Verschieben ist ein Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-182">The move failed.</span></span>|

<span data-ttu-id="b5ea3-183">Sie können auch die Option `-Verbose` anwenden, um weitere Informationen zur Verschiebung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-183">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="b5ea3-184">Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="b5ea3-184">User experience</span></span>

<span data-ttu-id="b5ea3-185">Benutzer sollten nur minimale Unterbrechungen bemerken, während ihre Website an einen anderen geografischen Standort verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-185">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="b5ea3-186">Während des Verschiebens kommt es nur zu einem kurzen, vorübergehenden schreibgeschützten Zustand, wobei vorhandene Links und Berechtigungen nach der Verschiebung weiterhin wie gewohnt funktionieren.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-186">Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="b5ea3-187">Website</span><span class="sxs-lookup"><span data-stu-id="b5ea3-187">Site</span></span>

<span data-ttu-id="b5ea3-188">Während die Verschiebung der Website durchgeführt wird, ist die Website kurzzeitig schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-188">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="b5ea3-189">Sobald die Verschiebung abgeschlossen ist, wird der Benutzer auf die neue Website am neuen geografischen Standort umgeleitet, wenn er auf Lesezeichen oder andere Links zur Website klickt.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-189">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="b5ea3-190">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="b5ea3-190">Permissions</span></span>

<span data-ttu-id="b5ea3-191">Benutzer, die über Berechtigungen für die Website verfügen, können auch während des Verschiebens und nach Abschluss des Vorgangs auf die Website zugreifen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-191">Users with permissions to site will continue to have access to the site during the move and after it's complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="b5ea3-192">Synchronisierungsclient</span><span class="sxs-lookup"><span data-stu-id="b5ea3-192">Sync Client</span></span>

<span data-ttu-id="b5ea3-193">Der Synchronisierungsclient erkennt den neuen Standort der Website nach Abschluss des Vorgangs automatisch und überträgt die Synchronisierung nahtlos auf diese Website.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-193">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="b5ea3-194">Der Benutzer muss sich nicht erneut anmelden oder eine andere Aktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-194">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="b5ea3-195">(Es ist Version 17.3.6943.0625 oder höher für den Synchronisierungsclient erforderlich.)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-195">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="b5ea3-196">Wenn ein Benutzer eine Datei aktualisiert, während die Verschiebung ausgeführt wird, benachrichtigt der Synchronisierungsclient den Benutzer, dass Dateiuploads ausstehen, während die Verschiebung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-196">If a user updates a file while the move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="b5ea3-197">Freigabelinks</span><span class="sxs-lookup"><span data-stu-id="b5ea3-197">Sharing links</span></span>

<span data-ttu-id="b5ea3-198">Nach Abschluss der geografischen Standortverschiebung in SharePoint werden vorhandene Freigabelinks für verschobene Dateien automatisch zu den Dateien an dem neuen geografischen Standort weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-198">When the SharePoint site geo move completes, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="b5ea3-199">Zuletzt verwendete Dateien in Office (MRU)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-199">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="b5ea3-200">Nach Abschluss der Verschiebung wird der MRU-Dienst mit der Website-URL und den Inhalts-URLs aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-200">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="b5ea3-201">Dies gilt für Word, Excel und PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-201">This applies to Word, Excel, and PowerPoint.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="b5ea3-202">OneNote-Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="b5ea3-202">OneNote experience</span></span>

<span data-ttu-id="b5ea3-203">Der OneNote-win32-Client und die UWP (Universal) App erkennen Notizbücher automatisch und synchronisieren sie mit dem neuen Websitestandort, nachdem die Verschiebung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-203">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="b5ea3-204">Der Benutzer muss sich nicht erneut anmelden oder eine andere Aktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-204">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="b5ea3-205">Der Benutzer bemerkt die Verschiebung gegebenenfalls nur dadurch, dass das Synchronisieren von Notizbüchern fehlschlägt, wenn die Verschiebung gerade läuft.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-205">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="b5ea3-206">Diese Benutzererfahrung ist für die folgenden Versionen des OneNote-Clients verfügbar:</span><span class="sxs-lookup"><span data-stu-id="b5ea3-206">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="b5ea3-207">OneNote-Win32 – Version 16.0.8326.2096 (und höher)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-207">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="b5ea3-208">OneNote UWP – Version 16.0.8431.1006 (und höher)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-208">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="b5ea3-209">Mobile OneNote-App – Version 16.0.8431.1011 (und höher)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-209">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a><span data-ttu-id="b5ea3-210">Teams (gilt für Websites, die mit Microsoft 365-Gruppen verbunden sind)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-210">Teams (applicable to Microsoft 365 Group connected sites)</span></span>

<span data-ttu-id="b5ea3-211">Wenn die Verschiebung des geografischen SharePoint-Websitestandorts abgeschlossen ist, haben Benutzer in der Teams-App Zugriff auf die Websitedateien ihrer Microsoft 365-Gruppe.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-211">When the SharePoint site geo move completes, users will have access to their Microsoft 365 Group site files on the Teams app.</span></span> <span data-ttu-id="b5ea3-212">Außerdem können Dateien, die vor dem Verschieben über den Teams-Chat geteilt wurden, nach Abschluss der Verschiebung weiterhin verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-212">Additionally, files shared via Teams chat from their site prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="b5ea3-213">Mobile SharePoint-App (iOS/Android)</span><span class="sxs-lookup"><span data-stu-id="b5ea3-213">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="b5ea3-214">Die mobile SharePoint-App ist über geografische Standorte hinweg kompatibel und erkennt den neuen geografischen Standort der Website.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-214">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="b5ea3-215">SharePoint-Workflows</span><span class="sxs-lookup"><span data-stu-id="b5ea3-215">SharePoint workflows</span></span>

<span data-ttu-id="b5ea3-216">SharePoint 2013-Workflows müssen erneut veröffentlicht werden, nachdem die Website verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-216">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="b5ea3-217">SharePoint 2010-Workflows sollten auch weiterhin normal funktionieren.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-217">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="b5ea3-218">Apps</span><span class="sxs-lookup"><span data-stu-id="b5ea3-218">Apps</span></span>

<span data-ttu-id="b5ea3-219">Wenn Sie eine Website mit Apps verschieben, müssen Sie die App am neuen geografischen Standort neu instanziieren, da die App und ihre Verbindungen am geografischen Zielstandort möglicherweise nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-219">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="b5ea3-220">Flow</span><span class="sxs-lookup"><span data-stu-id="b5ea3-220">Flow</span></span>

<span data-ttu-id="b5ea3-221">In den meisten Fällen funktioniert Flow nach dem Verschieben des geografischen Standorts der SharePoint-Website.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-221">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="b5ea3-222">Wir empfehlen, dies nach Abschluss der Verschiebung zu testen.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-222">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="b5ea3-223">PowerApps</span><span class="sxs-lookup"><span data-stu-id="b5ea3-223">PowerApps</span></span>

<span data-ttu-id="b5ea3-224">PowerApps müssen am Zielstandort neu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-224">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="b5ea3-225">Verschieben von Daten zwischen geografischen Standorten</span><span class="sxs-lookup"><span data-stu-id="b5ea3-225">Data movement between geo locations</span></span>

<span data-ttu-id="b5ea3-226">SharePoint verwendet Azure Blob-Speicher für Inhalte, während die mit den Websites verknüpften Metadaten und die zugehörigen Dateien in SharePoint gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-226">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="b5ea3-227">Nachdem die Website von ihrem Quellstandort an den Zielstandort verschoben wurde, verschiebt der Dienst auch den zugehörigen Blob-Speicher.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-227">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="b5ea3-228">Der Blob-Speicher wird in ungefähr 40 Tagen vollständig verschoben.</span><span class="sxs-lookup"><span data-stu-id="b5ea3-228">Blob Storage moves complete in approximately 40 days.</span></span> 