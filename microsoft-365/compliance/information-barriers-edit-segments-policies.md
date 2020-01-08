---
title: Bearbeiten von Richtlinien für Informationsbarrieren
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/08/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: None
description: Hier erfahren Sie, wie Sie Richtlinien für Informationsbarrieren bearbeiten oder entfernen.
ms.openlocfilehash: 20a1dd62fa80469a7a31db9b5541064ae16b4e02
ms.sourcegitcommit: af7950d9674f0eab3aee03f9afccff9ca2f4709a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "40971339"
---
# <a name="edit-or-remove-information-barrier-policies"></a><span data-ttu-id="d5745-103">Bearbeiten (oder entfernen) von Richtlinien für Informationsbarrieren</span><span class="sxs-lookup"><span data-stu-id="d5745-103">Edit (or remove) information barrier policies</span></span>

<span data-ttu-id="d5745-104">Nachdem Sie [Richtlinien für Informationsbarrieren definiert](information-barriers-policies.md)haben, müssen Sie möglicherweise im Rahmen der [Problembehandlung](information-barriers-troubleshooting.md) oder als regelmäßige Wartung Änderungen an diesen Richtlinien oder an Ihren Benutzersegmenten vornehmen.</span><span class="sxs-lookup"><span data-stu-id="d5745-104">After you have [defined information barrier policies](information-barriers-policies.md), you might need to make changes to those policies or to your user segments, as part of [troubleshooting](information-barriers-troubleshooting.md) or as regular maintenance.</span></span> <span data-ttu-id="d5745-105">Verwenden Sie diesen Artikel als Leitfaden.</span><span class="sxs-lookup"><span data-stu-id="d5745-105">Use this article as a guide.</span></span>

## <a name="what-do-you-want-to-do"></a><span data-ttu-id="d5745-106">Was möchten Sie machen?</span><span class="sxs-lookup"><span data-stu-id="d5745-106">What do you want to do?</span></span>

|<span data-ttu-id="d5745-107">Aktion</span><span class="sxs-lookup"><span data-stu-id="d5745-107">Action</span></span>  |<span data-ttu-id="d5745-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d5745-108">Description</span></span> |
|---------|---------|
|[<span data-ttu-id="d5745-109">Bearbeiten von Benutzerkonto Attributen</span><span class="sxs-lookup"><span data-stu-id="d5745-109">Edit user account attributes</span></span>](#edit-user-account-attributes)     |<span data-ttu-id="d5745-110">Geben Sie Attribute in Azure Active Directory ein, die zum Definieren von Segmenten verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="d5745-110">Fill in attributes in Azure Active Directory that can be used to define segments.</span></span><br/><span data-ttu-id="d5745-111">Bearbeiten Sie benutzerkontoattribute, wenn Benutzer nicht in den Segmenten enthalten sind, die Sie sein sollten, um zu ändern, in welchen Segmenten Benutzer sich befinden, oder um Segmente mit unterschiedlichen Attributen zu definieren.</span><span class="sxs-lookup"><span data-stu-id="d5745-111">Edit user account attributes when users are not included in segments they should be, to change which segments users are in, or to define segments using different attributes.</span></span>         |
|[<span data-ttu-id="d5745-112">Bearbeiten eines Segments</span><span class="sxs-lookup"><span data-stu-id="d5745-112">Edit a segment</span></span>](#edit-a-segment)     |<span data-ttu-id="d5745-113">Bearbeiten Sie Segmente, wenn Sie ändern möchten, wie ein Segment definiert wird.</span><span class="sxs-lookup"><span data-stu-id="d5745-113">Edit segments when you want to change how a segment is defined.</span></span> <br/><span data-ttu-id="d5745-114">Sie haben beispielsweise ursprünglich Segmente mithilfe von *Department* definiert und möchten nun ein anderes Attribut verwenden *, wie Beispiels*Weise "" ".</span><span class="sxs-lookup"><span data-stu-id="d5745-114">For example, you might have originally defined segments using *Department* and now want to use another attribute, such as *MemberOf*.</span></span>         |
|[<span data-ttu-id="d5745-115">Bearbeiten einer Richtlinie</span><span class="sxs-lookup"><span data-stu-id="d5745-115">Edit a policy</span></span>](#edit-a-policy)     |<span data-ttu-id="d5745-116">Bearbeiten Sie eine Richtlinie für Informationsbarrieren, wenn Sie die Funktionsweise einer Richtlinie ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="d5745-116">Edit an information barrier policy when you want to change how a policy works.</span></span><br/><span data-ttu-id="d5745-117">Anstatt die Kommunikation zwischen zwei Segmenten zu blockieren, können Sie beispielsweise festlegen, dass die Kommunikation nur zwischen bestimmten Segmenten erfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="d5745-117">For example, instead of blocking communications between two segments, you might decide you want to allow communications to occur only between certain segments.</span></span>         |
|[<span data-ttu-id="d5745-118">Festlegen einer Richtlinie auf inaktiver Status</span><span class="sxs-lookup"><span data-stu-id="d5745-118">Set a policy to inactive status</span></span>](#set-a-policy-to-inactive-status)     |<span data-ttu-id="d5745-119">Legen Sie eine Richtlinie auf inaktiven Status fest, wenn Sie Änderungen an einer Richtlinie vornehmen möchten oder wenn Sie nicht möchten, dass eine Richtlinie wirksam ist.</span><span class="sxs-lookup"><span data-stu-id="d5745-119">Set a policy to inactive status when you want to make changes to a policy, or when you don't want a policy to be in effect.</span></span>         |
|[<span data-ttu-id="d5745-120">Entfernen einer Richtlinie</span><span class="sxs-lookup"><span data-stu-id="d5745-120">Remove a policy</span></span>](#remove-a-policy)     |<span data-ttu-id="d5745-121">Entfernen einer Richtlinie für Informationsbarrieren, wenn Sie eine bestimmte Richtlinie nicht mehr an Ort und Stelle benötigen.</span><span class="sxs-lookup"><span data-stu-id="d5745-121">Remove an information barrier policy when you no longer need a particular policy in place.</span></span>         |
|[<span data-ttu-id="d5745-122">Beenden einer Richtlinienanwendung</span><span class="sxs-lookup"><span data-stu-id="d5745-122">Stop a policy application</span></span>](#stop-a-policy-application)     |<span data-ttu-id="d5745-123">Tun Sie dies, wenn Sie den Prozess der Anwendung von Richtlinien für Informationsbarrieren beenden möchten.</span><span class="sxs-lookup"><span data-stu-id="d5745-123">Do this when you want to stop the process of applying information barrier policies.</span></span><br/><span data-ttu-id="d5745-124">Beachten Sie, dass das Beenden einer Richtlinienanwendung nicht sofort erfolgt und keine Richtlinien rückgängig gemacht wird, die bereits auf Benutzer angewendet wurden.</span><span class="sxs-lookup"><span data-stu-id="d5745-124">Note that stopping a policy application is not instant, and it does not undo policies that are already applied to users.</span></span>         |
|[<span data-ttu-id="d5745-125">Definieren von Richtlinien für Informationsbarrieren</span><span class="sxs-lookup"><span data-stu-id="d5745-125">Define policies for information barriers</span></span>](information-barriers-policies.md)     |<span data-ttu-id="d5745-126">Definieren Sie eine Richtlinie für Informationsbarrieren, wenn noch keine solchen Richtlinien vorhanden sind, und Sie müssen die Kommunikation zwischen bestimmten Benutzergruppen einschränken oder einschränken.</span><span class="sxs-lookup"><span data-stu-id="d5745-126">Define an information barrier policy when you do not already have such policies in place, and you must restrict or limit communications between specific groups of users.</span></span>         |
|[<span data-ttu-id="d5745-127">Problembehandlung bei Informationsbarrieren</span><span class="sxs-lookup"><span data-stu-id="d5745-127">Troubleshooting information barriers</span></span>](information-barriers-troubleshooting.md)     |<span data-ttu-id="d5745-128">Lesen Sie diesen Artikel, wenn Sie unerwartete Probleme mit Informationsbarrieren ausführen.</span><span class="sxs-lookup"><span data-stu-id="d5745-128">Refer to this article when you run into unexpected issues with information barriers.</span></span>         |

> [!IMPORTANT]
> <span data-ttu-id="d5745-129">Um die in diesem Artikel beschriebenen Aufgaben ausführen zu können, muss Ihnen eine entsprechende Rolle zugewiesen sein, beispielsweise eine der folgenden:</span><span class="sxs-lookup"><span data-stu-id="d5745-129">To perform the tasks described in this article, you must be assigned an appropriate role, such as one of the following:</span></span><br/><span data-ttu-id="d5745-130">-Microsoft 365 Enterprise-Global-Administrator</span><span class="sxs-lookup"><span data-stu-id="d5745-130">- Microsoft 365 Enterprise Global Administrator</span></span><br/><span data-ttu-id="d5745-131">-Office 365 globaler Administrator</span><span class="sxs-lookup"><span data-stu-id="d5745-131">- Office 365 Global Administrator</span></span><br/><span data-ttu-id="d5745-132">-Compliance-Administrator</span><span class="sxs-lookup"><span data-stu-id="d5745-132">- Compliance Administrator</span></span><br/><span data-ttu-id="d5745-133">-IB-Compliance-Management (Dies ist eine neue Rolle!)</span><span class="sxs-lookup"><span data-stu-id="d5745-133">- IB Compliance Management (this is a new role!)</span></span><p><span data-ttu-id="d5745-134">Weitere Informationen zu den Voraussetzungen für Informationsbarrieren finden Sie unter [Prerequisites (for Information Barrier Policies)](information-barriers-policies.md#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="d5745-134">To learn more about prerequisites for information barriers, see [Prerequisites (for information barrier policies)](information-barriers-policies.md#prerequisites).</span></span><p><span data-ttu-id="d5745-135">Stellen Sie sicher, dass Sie [eine Verbindung mit Office 365 Security #a0 Compliance Center PowerShell herstellen](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=exchange-ps).</span><span class="sxs-lookup"><span data-stu-id="d5745-135">Make sure to [connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=exchange-ps).</span></span>

## <a name="edit-user-account-attributes"></a><span data-ttu-id="d5745-136">Bearbeiten von Benutzerkonto Attributen</span><span class="sxs-lookup"><span data-stu-id="d5745-136">Edit user account attributes</span></span>

<span data-ttu-id="d5745-137">Verwenden Sie dieses Verfahren zum Bearbeiten von Attributen, die für die Segmentierung von Benutzern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d5745-137">Use this procedure to edit attributes that are used for segmenting users.</span></span> 

<span data-ttu-id="d5745-138">Wenn Sie beispielsweise ein Department-Attribut verwenden und für ein oder mehrere Benutzerkonten derzeit keine Werte für die Abteilung aufgeführt sind, müssen Sie diese Benutzerkonten bearbeiten, um Abteilungsinformationen einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="d5745-138">For example, if you are using a Department attribute, and one or more user accounts do not currently have any values listed for Department, you must edit those user accounts to include Department information.</span></span> 

<span data-ttu-id="d5745-139">Benutzerkontoattribute werden für die Definition von Segmenten verwendet, sodass Richtlinien für Informationsbarrieren zugewiesen werden können.</span><span class="sxs-lookup"><span data-stu-id="d5745-139">User account attributes are used for defining segments so that information barrier policies can be assigned.</span></span>

1. <span data-ttu-id="d5745-140">Verwenden Sie zum Anzeigen von Details für ein bestimmtes Benutzerkonto, wie Attributwerte und zugewiesene Segmente, das Cmdlet **Get-InformationBarrierRecipientStatus** mit Identitäts Parametern.</span><span class="sxs-lookup"><span data-stu-id="d5745-140">To view details for a specific user account, such as attribute values and assigned segment(s), use the **Get-InformationBarrierRecipientStatus** cmdlet with Identity parameters.</span></span> 

    |<span data-ttu-id="d5745-141">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5745-141">Syntax</span></span>  |<span data-ttu-id="d5745-142">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d5745-142">Example</span></span>  |
    |---------|---------|
    |`Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p>   <span data-ttu-id="d5745-143">Sie können einen beliebigen Wert verwenden, der jeden Benutzer eindeutig identifiziert, beispielsweise Name, Alias, Distinguished Name, kanonischer Domänenname, e-Mail-Adresse oder GUID.</span><span class="sxs-lookup"><span data-stu-id="d5745-143">You can use any value that uniquely identifies each user, such as name, alias, distinguished name, canonical domain name, email address, or GUID.</span></span> <p>   <span data-ttu-id="d5745-144">(Sie können dieses Cmdlet auch für einen einzelnen Benutzer verwenden: `Get-InformationBarrierRecipientStatus -Identity <value>`)</span><span class="sxs-lookup"><span data-stu-id="d5745-144">(You can also use this cmdlet for a single user: `Get-InformationBarrierRecipientStatus -Identity <value>`)</span></span>      |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw`  <p>   <span data-ttu-id="d5745-145">In diesem Beispiel wird auf zwei Benutzerkonten in Office 365 verwiesen: *meganb* für *Megan*und *alexw* für *Alex*.</span><span class="sxs-lookup"><span data-stu-id="d5745-145">In this example, we refer to two user accounts in Office 365: *meganb* for *Megan*, and *alexw* for *Alex*.</span></span>         |

2. <span data-ttu-id="d5745-146">Bestimmen Sie, welches Attribut Sie für Ihr Benutzerkontoprofil (en) bearbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="d5745-146">Determine which attribute you want to edit for your user account profile(s).</span></span> <span data-ttu-id="d5745-147">Weitere Informationen finden Sie unter [Attribute for Information Barrier Policies](information-barriers-attributes.md) .</span><span class="sxs-lookup"><span data-stu-id="d5745-147">Refer to [Attributes for information barrier policies](information-barriers-attributes.md) for more details.</span></span> 

3. <span data-ttu-id="d5745-148">Bearbeiten Sie ein oder mehrere Benutzerkonten, um Werte für das Attribut einzuschließen, das Sie im vorherigen Schritt ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="d5745-148">Edit one or more user accounts to include values for the attribute you selected in the previous step.</span></span> <span data-ttu-id="d5745-149">Verwenden Sie dazu eines der folgenden Verfahren:</span><span class="sxs-lookup"><span data-stu-id="d5745-149">To do this, use one of the following procedures:</span></span>

    - <span data-ttu-id="d5745-150">Informationen zum Bearbeiten eines einzelnen Kontos finden Sie unter [Hinzufügen oder Aktualisieren der Profilinformationen eines Benutzers mithilfe von Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="d5745-150">To edit a single account, see [Add or update a user's profile information using Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).</span></span>

    - <span data-ttu-id="d5745-151">Informationen zum Bearbeiten mehrerer Konten (oder zum Bearbeiten eines einzelnen Kontos mithilfe von PowerShell) finden Sie unter [Konfigurieren von Benutzerkontoeigenschaften mit Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/configure-user-account-properties-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="d5745-151">To edit multiple accounts (or use PowerShell to edit a single account), see [Configure user account properties with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/configure-user-account-properties-with-office-365-powershell).</span></span>

## <a name="edit-a-segment"></a><span data-ttu-id="d5745-152">Bearbeiten eines Segments</span><span class="sxs-lookup"><span data-stu-id="d5745-152">Edit a segment</span></span>

<span data-ttu-id="d5745-153">Verwenden Sie dieses Verfahren bearbeiten der Definition eines Benutzersegments.</span><span class="sxs-lookup"><span data-stu-id="d5745-153">Use this procedure edit the definition of a user segment.</span></span> <span data-ttu-id="d5745-154">Beispielsweise können Sie den Namen eines Segments oder den Filter ändern, der verwendet wird, um zu bestimmen, wer im Segment enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="d5745-154">For example, you might change the name of a segment, or the filter that is used to determine who's included in the segment.</span></span>

1. <span data-ttu-id="d5745-155">Verwenden Sie das Cmdlet **Get-OrganizationSegment** , um alle vorhandenen Segmente anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d5745-155">To view all existing segments, use the **Get-OrganizationSegment** cmdlet.</span></span>
    
    <span data-ttu-id="d5745-156">Syntax`Get-OrganizationSegment`</span><span class="sxs-lookup"><span data-stu-id="d5745-156">Syntax: `Get-OrganizationSegment`</span></span>

    <span data-ttu-id="d5745-157">Es wird eine Liste mit Segmenten und Details für jede, wie Segmenttyp, den UserGroupFilter-Wert, der erstellt oder zuletzt geändert, Guid, und so weiter angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d5745-157">You will see a list of segments and details for each, such as segment type, its UserGroupFilter value, who created or last modified it, GUID, and so on.</span></span>

    > [!TIP]
    > <span data-ttu-id="d5745-158">Drucken oder speichern Sie die Liste der Segmente als Referenz später.</span><span class="sxs-lookup"><span data-stu-id="d5745-158">Print or save your list of segments for reference later.</span></span> <span data-ttu-id="d5745-159">Wenn Sie beispielsweise ein Segment bearbeiten möchten, müssen Sie dessen Namen oder den Wert ermitteln (dieser wird mit dem Parameter Identity verwendet).</span><span class="sxs-lookup"><span data-stu-id="d5745-159">For example, if you want to edit a segment, you will need to know its name or identify value (this is used with the Identity parameter).</span></span>

2. <span data-ttu-id="d5745-160">Verwenden Sie zum Bearbeiten eines Segments das Cmdlet " **OrganizationSegment** " mit dem Parameter " **Identity** " und den relevanten Details.</span><span class="sxs-lookup"><span data-stu-id="d5745-160">To edit a segment, use the **Set-OrganizationSegment** cmdlet with the **Identity** parameter and relevant details.</span></span> 

    |<span data-ttu-id="d5745-161">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5745-161">Syntax</span></span>  |<span data-ttu-id="d5745-162">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d5745-162">Example</span></span>  |
    |---------|---------|
    |`Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"`     |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <p><span data-ttu-id="d5745-163">In diesem Beispiel haben wir für das Segment mit dem GUID- *c96e0837-C232-4a8a-841e-ef45787d8fcd*den Namen der Abteilung in "HRDept" geändert.</span><span class="sxs-lookup"><span data-stu-id="d5745-163">In this example, for the segment that has the GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*, we updated the department name to "HRDept".</span></span>         |

<span data-ttu-id="d5745-164">Wenn Sie die Bearbeitung von Segmenten für Ihre Organisation abgeschlossen haben, können Sie die Richtlinien für Informationsbarrieren entweder [definieren](information-barriers-policies.md#part-2-define-information-barrier-policies) oder [Bearbeiten](#edit-a-policy) .</span><span class="sxs-lookup"><span data-stu-id="d5745-164">When you have finished editing segments for your organization, you can either [define](information-barriers-policies.md#part-2-define-information-barrier-policies) or [edit](#edit-a-policy) information barrier policies.</span></span>

## <a name="edit-a-policy"></a><span data-ttu-id="d5745-165">Bearbeiten einer Richtlinie</span><span class="sxs-lookup"><span data-stu-id="d5745-165">Edit a policy</span></span>

1. <span data-ttu-id="d5745-166">Verwenden Sie das Cmdlet **Get-InformationBarrierPolicy** , um eine Liste der aktuellen Information Barrier-Richtlinien anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d5745-166">To view a list of current information barrier policies, use the **Get-InformationBarrierPolicy** cmdlet.</span></span>

    <span data-ttu-id="d5745-167">Syntax`Get-InformationBarrierPolicy`</span><span class="sxs-lookup"><span data-stu-id="d5745-167">Syntax: `Get-InformationBarrierPolicy`</span></span>

    <span data-ttu-id="d5745-168">Identifizieren Sie in der Ergebnisliste die Richtlinie, die Sie ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="d5745-168">In the list of results, identify the policy that you want to change.</span></span> <span data-ttu-id="d5745-169">Beachten Sie die GUID und den Namen der Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="d5745-169">Note the policy's GUID and name.</span></span>

2. <span data-ttu-id="d5745-170">Verwenden Sie das Cmdlet "InformationBarrierPolicy" mit einem **Identity** **-** Parameter, und geben Sie die Änderungen an, die Sie vornehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="d5745-170">Use the **Set-InformationBarrierPolicy** cmdlet with an **Identity** parameter, and specify the changes you want to make.</span></span>

    <span data-ttu-id="d5745-171">Beispiel: angenommen, eine Richtlinie wurde definiert, um zu verhindern, dass das *Forschungs* Segment mit den *Vertriebs* -und *Marketing* Segmenten kommuniziert.</span><span class="sxs-lookup"><span data-stu-id="d5745-171">Example: Suppose a policy was defined to block the *Research* segment from communicating with the *Sales* and *Marketing* segments.</span></span> <span data-ttu-id="d5745-172">Die Richtlinie wurde mithilfe dieses Cmdlets definiert:`New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`</span><span class="sxs-lookup"><span data-stu-id="d5745-172">The policy was defined by using this cmdlet: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`</span></span>
    
    <span data-ttu-id="d5745-173">Angenommen, wir möchten diese ändern, damit Personen im *Forschungs* Segment nur mit Personen im *HR* -Segment kommunizieren können.</span><span class="sxs-lookup"><span data-stu-id="d5745-173">Suppose we want to change it so that people in the *Research* segment can only communicate with people in the *HR* segment.</span></span> <span data-ttu-id="d5745-174">Um diese Änderung vorzunehmen, verwenden wir dieses Cmdlet:`Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`</span><span class="sxs-lookup"><span data-stu-id="d5745-174">To make this change, we use this cmdlet: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`</span></span>

    <span data-ttu-id="d5745-175">In diesem Beispiel haben wir "SegmentsBlocked" in "SegmentsAllowed" geändert und das *HR* -Segment angegeben.</span><span class="sxs-lookup"><span data-stu-id="d5745-175">In this example, we changed "SegmentsBlocked" to "SegmentsAllowed" and specified the *HR* segment.</span></span>

3. <span data-ttu-id="d5745-176">Wenn Sie die Bearbeitung einer Richtlinie abgeschlossen haben, sollten Sie Ihre Änderungen übernehmen.</span><span class="sxs-lookup"><span data-stu-id="d5745-176">When you are finished editing a policy, make sure to apply your changes.</span></span> <span data-ttu-id="d5745-177">(Weitere Informationen finden Sie unter [Apply Information Barrier Policies](information-barriers-policies.md#part-3-apply-information-barrier-policies).)</span><span class="sxs-lookup"><span data-stu-id="d5745-177">(See [Apply information barrier policies](information-barriers-policies.md#part-3-apply-information-barrier-policies).)</span></span>

## <a name="set-a-policy-to-inactive-status"></a><span data-ttu-id="d5745-178">Festlegen einer Richtlinie auf inaktiver Status</span><span class="sxs-lookup"><span data-stu-id="d5745-178">Set a policy to inactive status</span></span>

1. <span data-ttu-id="d5745-179">Verwenden Sie das Cmdlet **Get-InformationBarrierPolicy** , um eine Liste der aktuellen Information Barrier-Richtlinien anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d5745-179">To view a list of current information barrier policies, use the **Get-InformationBarrierPolicy** cmdlet.</span></span>

    <span data-ttu-id="d5745-180">Syntax`Get-InformationBarrierPolicy`</span><span class="sxs-lookup"><span data-stu-id="d5745-180">Syntax: `Get-InformationBarrierPolicy`</span></span>

    <span data-ttu-id="d5745-181">Identifizieren Sie in der Ergebnisliste die Richtlinie, die Sie ändern möchten (oder entfernen).</span><span class="sxs-lookup"><span data-stu-id="d5745-181">In the list of results, identify the policy that you want to change (or remove).</span></span> <span data-ttu-id="d5745-182">Beachten Sie die GUID und den Namen der Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="d5745-182">Note the policy's GUID and name.</span></span>

2. <span data-ttu-id="d5745-183">Um den Status der Richtlinie auf inaktiv festzulegen, verwenden Sie das Cmdlet "InformationBarrierPolicy" mit einem Identity-Parameter und dem State **-** Parameter auf "inaktiv" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d5745-183">To set the policy's status to inactive, use the **Set-InformationBarrierPolicy** cmdlet with an Identity parameter and the State parameter set to Inactive.</span></span>

    |<span data-ttu-id="d5745-184">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5745-184">Syntax</span></span>  |<span data-ttu-id="d5745-185">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d5745-185">Example</span></span>  |
    |---------|---------|
    |`Set-InformationBarrierPolicy -Identity GUID -State Inactive`     |`Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <p><span data-ttu-id="d5745-186">In diesem Beispiel wird eine Richtlinie für Informationsbarrieren festgelegt, die GUID *43c37853-EA10-4b90-a23d-ab8c9377247* in einen inaktiven Status hat.</span><span class="sxs-lookup"><span data-stu-id="d5745-186">In this example, we set an information barrier policy that has GUID *43c37853-ea10-4b90-a23d-ab8c9377247* to an inactive status.</span></span>         |

3. <span data-ttu-id="d5745-187">Verwenden Sie das Cmdlet **Start-InformationBarrierPoliciesApplication** , um die Änderungen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="d5745-187">To apply your changes, use the **Start-InformationBarrierPoliciesApplication** cmdlet.</span></span>

    <span data-ttu-id="d5745-188">Syntax`Start-InformationBarrierPoliciesApplication`</span><span class="sxs-lookup"><span data-stu-id="d5745-188">Syntax: `Start-InformationBarrierPoliciesApplication`</span></span>

    <span data-ttu-id="d5745-189">Änderungen werden angewendet, Benutzer nach Benutzer, für Ihre Organisation.</span><span class="sxs-lookup"><span data-stu-id="d5745-189">Changes are applied, user by user, for your organization.</span></span> <span data-ttu-id="d5745-190">Wenn Ihre Organisation groß ist, kann es 24 Stunden (oder mehr) dauern, bis dieser Prozess abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="d5745-190">If your organization is large, it can take 24 hours (or more) for this process to complete.</span></span> <span data-ttu-id="d5745-191">(Als allgemeine Richtlinie dauert es etwa eine Stunde, 5.000-Benutzerkonten zu verarbeiten.)</span><span class="sxs-lookup"><span data-stu-id="d5745-191">(As a general guideline, it takes about an hour to process 5,000 user accounts.)</span></span>

<span data-ttu-id="d5745-192">Zu diesem Zeitpunkt werden mindestens eine Richtlinie für Informationsbarrieren auf inaktiver Status festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d5745-192">At this point, one or more information barrier policies are set to inactive status.</span></span> <span data-ttu-id="d5745-193">Von hier aus können Sie einen der folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d5745-193">From here, you can do any of the following:</span></span>
- <span data-ttu-id="d5745-194">Beibehalten (eine auf inaktiven Status festgelegte Richtlinie hat keine Auswirkungen auf die Benutzer)</span><span class="sxs-lookup"><span data-stu-id="d5745-194">Keep it as is (a policy set to inactive status has no effect on users)</span></span>
- [<span data-ttu-id="d5745-195">Bearbeiten einer Richtlinie</span><span class="sxs-lookup"><span data-stu-id="d5745-195">Edit a policy</span></span>](#edit-a-policy) 
- [<span data-ttu-id="d5745-196">Entfernen einer Richtlinie</span><span class="sxs-lookup"><span data-stu-id="d5745-196">Remove a policy</span></span>](#remove-a-policy)

## <a name="remove-a-policy"></a><span data-ttu-id="d5745-197">Entfernen einer Richtlinie</span><span class="sxs-lookup"><span data-stu-id="d5745-197">Remove a policy</span></span>

1. <span data-ttu-id="d5745-198">Verwenden Sie das Cmdlet **Get-InformationBarrierPolicy** , um eine Liste der aktuellen Information Barrier-Richtlinien anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d5745-198">To view a list of current information barrier policies, use the **Get-InformationBarrierPolicy** cmdlet.</span></span>

    <span data-ttu-id="d5745-199">Syntax`Get-InformationBarrierPolicy`</span><span class="sxs-lookup"><span data-stu-id="d5745-199">Syntax: `Get-InformationBarrierPolicy`</span></span>

    <span data-ttu-id="d5745-200">Identifizieren Sie in der Ergebnisliste die Richtlinie, die Sie entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="d5745-200">In the list of results, identify the policy that you want to remove.</span></span> <span data-ttu-id="d5745-201">Beachten Sie die GUID und den Namen der Richtlinie.</span><span class="sxs-lookup"><span data-stu-id="d5745-201">Note the policy's GUID and name.</span></span> <span data-ttu-id="d5745-202">Stellen Sie sicher, dass die Richtlinie auf inaktiver Status festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="d5745-202">Make sure the policy is set to inactive status.</span></span>

2. <span data-ttu-id="d5745-203">Verwenden Sie das Cmdlet **Remove-InformationBarrierPolicy** mit einem Identity-Parameter.</span><span class="sxs-lookup"><span data-stu-id="d5745-203">Use the **Remove-InformationBarrierPolicy** cmdlet with an Identity parameter.</span></span>

    |<span data-ttu-id="d5745-204">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5745-204">Syntax</span></span>  |<span data-ttu-id="d5745-205">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d5745-205">Example</span></span>  |
    |---------|---------|
    |`Remove-InformationBarrierPolicy -Identity GUID`     |`Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <p><span data-ttu-id="d5745-206">In diesem Beispiel wird die Richtlinie mit GUID- *43c37853-EA10-4b90-a23d-ab8c93772471*entfernt.</span><span class="sxs-lookup"><span data-stu-id="d5745-206">In this example, we are removing the policy that has GUID *43c37853-ea10-4b90-a23d-ab8c93772471*.</span></span>          |

    <span data-ttu-id="d5745-207">Bestätigen Sie die Änderung, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="d5745-207">When prompted, confirm the change.</span></span>

3. <span data-ttu-id="d5745-208">Wiederholen Sie die Schritte 1-2 für jede Richtlinie, die Sie entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="d5745-208">Repeat steps 1-2 for each policy you want to remove.</span></span>

4. <span data-ttu-id="d5745-209">Wenn Sie das Entfernen von Richtlinien abgeschlossen haben, wenden Sie die Änderungen an.</span><span class="sxs-lookup"><span data-stu-id="d5745-209">When you are finished removing policies, apply your changes.</span></span> <span data-ttu-id="d5745-210">Verwenden Sie dazu das Cmdlet **Start-InformationBarrierPoliciesApplication** .</span><span class="sxs-lookup"><span data-stu-id="d5745-210">To do this, use the **Start-InformationBarrierPoliciesApplication** cmdlet.</span></span>

    <span data-ttu-id="d5745-211">Syntax`Start-InformationBarrierPoliciesApplication`</span><span class="sxs-lookup"><span data-stu-id="d5745-211">Syntax: `Start-InformationBarrierPoliciesApplication`</span></span>

    <span data-ttu-id="d5745-212">Änderungen werden angewendet, Benutzer nach Benutzer, für Ihre Organisation.</span><span class="sxs-lookup"><span data-stu-id="d5745-212">Changes are applied, user by user, for your organization.</span></span> <span data-ttu-id="d5745-213">Wenn Ihre Organisation groß ist, kann es 24 Stunden (oder mehr) dauern, bis dieser Prozess abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="d5745-213">If your organization is large, it can take 24 hours (or more) for this process to complete.</span></span>

## <a name="stop-a-policy-application"></a><span data-ttu-id="d5745-214">Beenden einer Richtlinienanwendung</span><span class="sxs-lookup"><span data-stu-id="d5745-214">Stop a policy application</span></span>

<span data-ttu-id="d5745-215">Wenn Sie die Anwendung von Richtlinien für Informationsbarrieren gestartet haben und diese Richtlinien nicht mehr angewendet werden sollen, verwenden Sie das folgende Verfahren.</span><span class="sxs-lookup"><span data-stu-id="d5745-215">If, after you have started applying information barrier policies, you want to stop those policies from being applied, use the following procedure.</span></span> <span data-ttu-id="d5745-216">Denken Sie daran, dass es ungefähr 30-35 Minuten dauern wird, bis der Prozess beginnt.</span><span class="sxs-lookup"><span data-stu-id="d5745-216">Keep in mind that it will take approximately 30-35 minutes for the process to begin.</span></span>

1. <span data-ttu-id="d5745-217">Verwenden Sie das Cmdlet **Get-InformationBarrierPoliciesApplicationStatus** , um den Status der neuesten Informations Barriere-Richtlinienanwendung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d5745-217">To view the status of the most recent information barrier policy application, use the **Get-InformationBarrierPoliciesApplicationStatus** cmdlet.</span></span>

    <span data-ttu-id="d5745-218">Syntax`Get-InformationBarrierPoliciesApplicationStatus`</span><span class="sxs-lookup"><span data-stu-id="d5745-218">Syntax: `Get-InformationBarrierPoliciesApplicationStatus`</span></span>

    <span data-ttu-id="d5745-219">Beachten Sie die GUID der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="d5745-219">Note the application's GUID.</span></span>

2. <span data-ttu-id="d5745-220">Verwenden Sie das Cmdlet **Stop-InformationBarrierPoliciesApplication** mit einem Identity-Parameter.</span><span class="sxs-lookup"><span data-stu-id="d5745-220">Use the **Stop-InformationBarrierPoliciesApplication** cmdlet with an Identity parameter.</span></span>

    |<span data-ttu-id="d5745-221">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5745-221">Syntax</span></span>  |<span data-ttu-id="d5745-222">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d5745-222">Example</span></span>  |
    |---------|---------|
    |`Stop-InformationBarrierPoliciesApplication -Identity GUID`     |`Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p><span data-ttu-id="d5745-223">In diesem Beispiel wird das Anwenden von Richtlinien für Informationsbarrieren angehalten.</span><span class="sxs-lookup"><span data-stu-id="d5745-223">In this example, we are stopping information barrier policies from being applied.</span></span>         |

## <a name="related-articles"></a><span data-ttu-id="d5745-224">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="d5745-224">Related articles</span></span>

[<span data-ttu-id="d5745-225">Hier erhalten Sie einen Überblick über Informationsbarrieren</span><span class="sxs-lookup"><span data-stu-id="d5745-225">Get an overview of information barriers</span></span>](information-barriers.md)

[<span data-ttu-id="d5745-226">Definieren von Richtlinien für Informationsbarrieren</span><span class="sxs-lookup"><span data-stu-id="d5745-226">Define policies for information barriers</span></span>](information-barriers-policies.md)

[<span data-ttu-id="d5745-227">Weitere Informationen zu Informationsbarrieren in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d5745-227">Learn more about information barriers in Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/information-barriers-in-teams)

[<span data-ttu-id="d5745-228">Attribute für Richtlinien für Informationsbarrieren</span><span class="sxs-lookup"><span data-stu-id="d5745-228">Attributes for information barrier policies</span></span>](information-barriers-attributes.md)

[<span data-ttu-id="d5745-229">Problembehandlung bei Informationsbarrieren</span><span class="sxs-lookup"><span data-stu-id="d5745-229">Troubleshooting information barriers</span></span>](information-barriers-troubleshooting.md)