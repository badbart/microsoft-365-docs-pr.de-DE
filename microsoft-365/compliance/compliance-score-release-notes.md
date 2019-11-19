---
title: Versionshinweise zu Microsoft Compliance Score
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Versionshinweise und bekannte Probleme für Microsoft Compliance Score (Preview), ein Feature im M365 Compliance Center, das das vereinfachen und Automatisieren von Risikobewertungen erleichtert.
ms.openlocfilehash: 192519e323f9d23420f82a603979b50f4581ac4f
ms.sourcegitcommit: e2ed110c4c3a8434f9fcc9d610069bc77bc39220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "38686196"
---
# <a name="microsoft-compliance-score-release-notes-preview"></a><span data-ttu-id="bf00b-103">Versionshinweise zu Microsoft Compliance Score (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="bf00b-103">Microsoft Compliance Score release notes (Preview)</span></span>

<span data-ttu-id="bf00b-104">Die Public Preview of Microsoft Compliance Score bietet Ihnen frühzeitigen Zugriff auf bevorstehende Funktionen und Updates.</span><span class="sxs-lookup"><span data-stu-id="bf00b-104">The public preview of Microsoft Compliance Score provides you with early access to upcoming functionality and updates.</span></span>

<span data-ttu-id="bf00b-105">Compliance Score ist ein neues Feature im [Microsoft 365 Compliance Center](microsoft-365-compliance-center.md) , das eine risikobasierte Bewertung berechnet und den Fortschritt bei der Durchführung von empfohlenen Aktionen misst, die zur Verringerung der Compliance-Risiken beitragen.</span><span class="sxs-lookup"><span data-stu-id="bf00b-105">Compliance Score is a new feature in the [Microsoft 365 compliance center](microsoft-365-compliance-center.md) that calculates a risk-based score, measuring your progress towards completing recommended actions that help reduce compliance risks.</span></span>

## <a name="compliance-score-and-compliance-manager-relationship"></a><span data-ttu-id="bf00b-106">Compliance-Score und Compliance-Manager-Beziehung</span><span class="sxs-lookup"><span data-stu-id="bf00b-106">Compliance Score and Compliance Manager relationship</span></span>

<span data-ttu-id="bf00b-107">Viele der Compliance-Funktionen, die im Compliance-Manager behandelt werden, können jetzt in der Kompatibilitätsbewertung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bf00b-107">Many of the compliance functions handled in Compliance Manager can now be done in Compliance Score.</span></span> <span data-ttu-id="bf00b-108">Einige Funktionen befinden sich jedoch weiterhin nur im Compliance-Manager, und einige frühere Funktionen im Compliance-Manager werden während des öffentlichen Vorschauzeitraums geändert.</span><span class="sxs-lookup"><span data-stu-id="bf00b-108">However some functionality still resides only in Compliance Manager, and some previous functionality in Compliance Manager is altered during the public preview period.</span></span> 

<span data-ttu-id="bf00b-109">Beachten Sie beim Arbeiten mit dem Kompatibilitäts Bewertungs-und Compliance-Manager während der öffentlichen Vorschau die folgenden Punkte:</span><span class="sxs-lookup"><span data-stu-id="bf00b-109">Keep these points in mind as you work with Compliance Score and Compliance Manager during public preview:</span></span>

- <span data-ttu-id="bf00b-110">**Verwalten von Bewertungen**: Benutzer können Bewertungen und deren Statusdetails in der Kompatibilitätsbewertung anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bf00b-110">**Managing assessments**: users can view assessments and their status details in Compliance Score.</span></span> <span data-ttu-id="bf00b-111">Benutzer können jedoch nur Assessment-Verwaltungsaufgaben im Compliance-Manager ([Anweisungen anzeigen](working-with-compliance-manager.md#assessments)) und Aufgaben ausführen und sind auf Folgendes beschränkt:</span><span class="sxs-lookup"><span data-stu-id="bf00b-111">However users can only perform assessment management tasks in Compliance Manager ([view instructions](working-with-compliance-manager.md#assessments)), and tasks and are limited to the following:</span></span>
    - <span data-ttu-id="bf00b-112">Neue Bewertungen hochladen, jedoch vorhandene Bewertungen nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="bf00b-112">Upload new assessments, but not modify existing assessments.</span></span> <span data-ttu-id="bf00b-113">Wenn Sie eine vorhandene Bewertung ändern müssen, müssen Sie eine neue Vorlage hochladen.</span><span class="sxs-lookup"><span data-stu-id="bf00b-113">If you need to modify an existing assessment, you will need to upload a new template.</span></span>
    - <span data-ttu-id="bf00b-114">Export Bewertungen</span><span class="sxs-lookup"><span data-stu-id="bf00b-114">Export assessments</span></span>
    - <span data-ttu-id="bf00b-115">Archiv Bewertungen</span><span class="sxs-lookup"><span data-stu-id="bf00b-115">Archive assessments</span></span>
    - <span data-ttu-id="bf00b-116">Anzeigen archivierter Bewertungen</span><span class="sxs-lookup"><span data-stu-id="bf00b-116">View archived assessments</span></span>
 - <span data-ttu-id="bf00b-117">**Erstellen von Vorlagen für Bewertungen**:</span><span class="sxs-lookup"><span data-stu-id="bf00b-117">**Creating templates for assessments**:</span></span> 
   - <span data-ttu-id="bf00b-118">Benutzer müssen zum Compliance-Manager wechseln, um neue Vorlagen zu erstellen und vorhandene Vorlagen zu exportieren.</span><span class="sxs-lookup"><span data-stu-id="bf00b-118">Users must go to Compliance Manager to create new templates and export existing templates.</span></span> 
   - <span data-ttu-id="bf00b-119">Vorhandene Vorlagen können nicht angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="bf00b-119">Existing templates cannot be customized.</span></span> <span data-ttu-id="bf00b-120">Lesen Sie Anweisungen zum [Verwalten von Vorlagen im Compliance-Manager](working-with-compliance-manager.md#templates).</span><span class="sxs-lookup"><span data-stu-id="bf00b-120">Read instructions for [managing templates in Compliance Manager](working-with-compliance-manager.md#templates).</span></span>
   - <span data-ttu-id="bf00b-121">Beim Erstellen einer Vorlage müssen Sie Dimensionen für **Produkt** und **Zertifizierung** einschließen, um sicherzustellen, dass Ihre Vorlage im Kompatibilitäts Bewertungsergebnis angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bf00b-121">When creating a template, you must include Dimensions for both **Product** and **Certification** to ensure your template displays in Compliance Score.</span></span>
 - <span data-ttu-id="bf00b-122">**Festlegen von Berechtigungen**: Konformitäts Bewertungs Benutzer, denen zuvor keine Berechtigungen im Compliance-Manager erteilt wurden, müssen Ihre Berechtigungen im Microsoft 365 Compliance Center festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="bf00b-122">**Setting permissions**: Compliance Score users who were not previously granted permissions in Compliance Manager must have their permissions set in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="bf00b-123">Benutzer, deren Rollen zuvor im Compliance-Manager festgelegt wurden, können dieselbe Zugriffsebene verwenden, wenn Sie in der Kompatibilitätsbewertung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="bf00b-123">Users whose roles were previously set in Compliance Manager can use that same level of access when working in Compliance Score.</span></span>
- <span data-ttu-id="bf00b-124">**Übertragung von Daten**: Organisationen mit Daten, die sich im Compliance-Manager befinden, sehen diese Daten in der Kompatibilitätsbewertung und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="bf00b-124">**Transfer of data**: organizations with data residing in Compliance Manger will see that data in Compliance Score, and vice-versa.</span></span>
- <span data-ttu-id="bf00b-125">**Anmelden beim Compliance-Manager aus Kompatibilitätsbewertung**: Wenn ein Benutzer bei der Kompatibilitätsbewertung angemeldet ist und einen Link auswählt, um zum Compliance-Manager zu wechseln, muss sich der Benutzer nicht erneut anmelden.</span><span class="sxs-lookup"><span data-stu-id="bf00b-125">**Signing in to Compliance Manager from Compliance Score**: if a user is signed in to Compliance Score and selects a link to go to Compliance Manager, the user will not have to sign in again.</span></span> <span data-ttu-id="bf00b-126">Nachdem Sie auf den Link geklickt haben, wird in Ihrem Browser eine neue Registerkarte mit einem Dialogfeld geöffnet.</span><span class="sxs-lookup"><span data-stu-id="bf00b-126">After clicking the link, a new tab opens in your browser featuring a dialogue box.</span></span> <span data-ttu-id="bf00b-127">Im oberen Abschnitt mit dem Header "bereits Microsoft Cloud Services-Kunde?</span><span class="sxs-lookup"><span data-stu-id="bf00b-127">In the top section with the header, “Already a Microsoft cloud services customer?</span></span> <span data-ttu-id="bf00b-128">Melden Sie sich bei Ihrem Konto an, "wählen Sie die Schaltfläche **Anmelden** aus, um sich automatisch beim Compliance-Manager anzumelden.</span><span class="sxs-lookup"><span data-stu-id="bf00b-128">Sign in to your account,” select the **Sign In** button to automatically sign in to Compliance Manager.</span></span>

## <a name="known-issues-in-compliance-score-preview"></a><span data-ttu-id="bf00b-129">Bekannte Probleme in Compliance Score (Preview)</span><span class="sxs-lookup"><span data-stu-id="bf00b-129">Known issues in Compliance Score (Preview)</span></span>

<span data-ttu-id="bf00b-130">In den folgenden Abschnitten werden bekannte Probleme behandelt, die in bevorstehenden Versionen von Compliance Score behoben werden sollten.</span><span class="sxs-lookup"><span data-stu-id="bf00b-130">The following sections cover known issues to be resolved in upcoming releases of Compliance Score.</span></span>

### <a name="launch-now-links-in-certain-improvement-actions"></a><span data-ttu-id="bf00b-131">Jetzt starten Links in bestimmten Verbesserungs Aktionen</span><span class="sxs-lookup"><span data-stu-id="bf00b-131">Launch Now links in certain improvement actions</span></span>

<span data-ttu-id="bf00b-132">Bei bestimmten Verbesserungs Aktionen wird beim Auswählen des Hyperlinks **jetzt starten** , der unterhalb der Implementierungsanweisungen angezeigt wird, ein Fehler ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="bf00b-132">In certain improvement actions, selecting the **Launch Now** link that appears underneath the implementation instructions gives an error.</span></span> <span data-ttu-id="bf00b-133">Führen Sie die folgenden Schritte aus, um auf das richtige Ziel, das SharePoint Admin Center, zuzugreifen:</span><span class="sxs-lookup"><span data-stu-id="bf00b-133">To access the proper destination, which is the the SharePoint admin center, follow these steps:</span></span>

1. <span data-ttu-id="bf00b-134">Wechseln Sie zum [Microsoft 365 Admin Center](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="bf00b-134">Go to the [Microsoft 365 Admin Center](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="bf00b-135">Wählen Sie im linken Navigationsmenü die Option **Alle anzeigen**aus.</span><span class="sxs-lookup"><span data-stu-id="bf00b-135">On the left navigation menu, select **Show all**.</span></span>
3. <span data-ttu-id="bf00b-136">Wählen Sie unter **Admin Center** die Option **SharePoint**aus.</span><span class="sxs-lookup"><span data-stu-id="bf00b-136">Under **Admin centers,** select **SharePoint**.</span></span>

<span data-ttu-id="bf00b-137">Im folgenden finden Sie die betroffenen Verbesserungs Aktionen, die sich alle in der Kategorie **Protect Information** befinden:</span><span class="sxs-lookup"><span data-stu-id="bf00b-137">Below are the affected improvement actions, which all reside in the **Protect information** category:</span></span>
  - <span data-ttu-id="bf00b-138">Anwenden der Verschlüsselung auf die SharePoint-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="bf00b-138">Apply encryption to SharePoint Library</span></span>
  - <span data-ttu-id="bf00b-139">Klassifizieren von Daten in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf00b-139">Classify Data in SharePoint Online</span></span>
  - <span data-ttu-id="bf00b-140">Konfigurieren externer Freigabe Links für Ablauf</span><span class="sxs-lookup"><span data-stu-id="bf00b-140">Configure External Sharing Links to Expire</span></span>
  - <span data-ttu-id="bf00b-141">Aktivieren der Versionsverwaltung für Dokumentbibliotheken</span><span class="sxs-lookup"><span data-stu-id="bf00b-141">Enable Versioning for Document Libraries</span></span>

### <a name="long-load-times-for-non-admin-users"></a><span data-ttu-id="bf00b-142">Lange Ladezeiten für Benutzer ohne Administratorrechte</span><span class="sxs-lookup"><span data-stu-id="bf00b-142">Long load times for non-admin users</span></span>
<span data-ttu-id="bf00b-143">Kompatibilitätsbewertung Benutzer, die andere Rollen als eine Administratorrolle innehaben, können lange Ladezeiten beim Versuch einer Anmeldung auftreten.</span><span class="sxs-lookup"><span data-stu-id="bf00b-143">Compliance Score users who hold roles other than an admin role may experience long load times when trying to a sign in.</span></span> <span data-ttu-id="bf00b-144">Wenn Sie den Browser aktualisieren, wird dieses Problem behoben.</span><span class="sxs-lookup"><span data-stu-id="bf00b-144">Refreshing your browser will resolve this issue.</span></span> <span data-ttu-id="bf00b-145">(Weitere Informationen finden Sie unter [Compliance Score Roles](compliance-score-setup.md#set-user-permissions-and-assign-roles).)</span><span class="sxs-lookup"><span data-stu-id="bf00b-145">(Learn more about [Compliance Score roles](compliance-score-setup.md#set-user-permissions-and-assign-roles).)</span></span>

### <a name="supported-browsers"></a><span data-ttu-id="bf00b-146">Unterstützte Browser</span><span class="sxs-lookup"><span data-stu-id="bf00b-146">Supported browsers</span></span>

- <span data-ttu-id="bf00b-147">Die neuesten Versionen von Microsoft Edge, Chrome und Safari werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bf00b-147">The latest versions of Microsoft Edge, Chrome, and Safari are supported.</span></span>
- <span data-ttu-id="bf00b-148">Es gibt möglicherweise Fälle, in denen aktualisierte Daten erst angezeigt werden, wenn Ihr Browser aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="bf00b-148">There may be instances where updated data does not appear until your browser is refreshed.</span></span>
- <span data-ttu-id="bf00b-149">Die Preview-Version von Microsoft Edge wird nicht unterstützt, aber es sind keine bekannten Probleme aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="bf00b-149">The preview version of Microsoft Edge is not supported but has no known issues.</span></span>
- <span data-ttu-id="bf00b-150">Internet Explorer wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bf00b-150">Internet Explorer is not supported.</span></span>
 
### <a name="language-support"></a><span data-ttu-id="bf00b-151">Sprachunterstützung</span><span class="sxs-lookup"><span data-stu-id="bf00b-151">Language support</span></span>

- <span data-ttu-id="bf00b-152">Das Kompatibilitäts Ergebnis steht nur in Englisch (USA) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="bf00b-152">Compliance Score is only available in U.S. English.</span></span>