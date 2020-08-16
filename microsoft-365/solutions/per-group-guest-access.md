---
title: Blockieren von Gastbenutzern aus einer bestimmten Gruppe
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Blockieren von Gastbenutzern aus einer bestimmten Gruppe
ms.openlocfilehash: 923a9e5cd09d232f377f55fd6a9f499f8f536a84
ms.sourcegitcommit: 66f1f430b3dcae5f46cb362a32d6fb7da4cff5c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "46662643"
---
# <a name="block-guest-users-from-a-specific-group"></a><span data-ttu-id="fdea4-103">Blockieren von Gastbenutzern aus einer bestimmten Gruppe</span><span class="sxs-lookup"><span data-stu-id="fdea4-103">Block guest users from a specific group</span></span>

<span data-ttu-id="fdea4-104">Wenn Sie den Gastzugriff für die meisten Gruppen zulassen möchten, jedoch einige, in denen Sie Gastzugriff verhindern möchten, können Sie den Gastzugriff für einzelne Gruppen blockieren.</span><span class="sxs-lookup"><span data-stu-id="fdea4-104">If you want to allow guest access to most groups, but have some where you want to prevent guest access, you can block guest access for individual groups.</span></span>

<span data-ttu-id="fdea4-105">Wenn Sie Sensitivitäts Bezeichnungen in Ihrer Organisation verwenden, empfehlen wir die Verwendung zur Steuerung des Gastzugriffs pro Gruppe.</span><span class="sxs-lookup"><span data-stu-id="fdea4-105">If you use sensitivity labels in your organization, we recommend using them to control guest access on a per-group basis.</span></span> <span data-ttu-id="fdea4-106">Informationen zur Vorgehensweise finden [Sie unter Verwenden von Sensitivitäts Bezeichnungen zum Schutz von Inhalten in Microsoft Teams, Microsoft 365-Gruppen und SharePoint-Websites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span><span class="sxs-lookup"><span data-stu-id="fdea4-106">For information about how to do this, [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span></span> <span data-ttu-id="fdea4-107">Dies ist die empfohlene Vorgehensweise.</span><span class="sxs-lookup"><span data-stu-id="fdea4-107">This is the recommended approach.</span></span>

<span data-ttu-id="fdea4-108">Sie können auch Gastzugriff auf einzelne Gruppen mithilfe von Microsoft PowerShell blockieren.</span><span class="sxs-lookup"><span data-stu-id="fdea4-108">You can also block guest access to individual groups by using Microsoft PowerShell.</span></span>

<span data-ttu-id="fdea4-109">Sie müssen die Vorschauversion von [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) (Module Name **AzureADPreview**) verwenden, um die Einstellung Gastzugriff auf Gruppenebene zu ändern:</span><span class="sxs-lookup"><span data-stu-id="fdea4-109">You must use the preview version of [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) (module name **AzureADPreview**) to change the group-level guest access setting:</span></span>

- <span data-ttu-id="fdea4-110">Wenn Sie zuvor noch keine Version des Azure AD PowerShell-Moduls installiert haben, lesen Sie [Installieren des Azure AD-Moduls](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview#installing-the-azure-ad-module), und folgen Sie den Anweisungen zum Installieren der öffentlichen Vorschauversion.</span><span class="sxs-lookup"><span data-stu-id="fdea4-110">If you haven't installed any version of the Azure AD PowerShell module before, see [Installing the Azure AD Module](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview#installing-the-azure-ad-module) and follow the instructions to install the public preview release.</span></span>

- <span data-ttu-id="fdea4-111">Wenn Sie die allgemein verfügbare Version 2.0 des Azure AD PowerShell-Moduls (AzureAD) installiert haben, müssen Sie sie deinstallieren, indem Sie `Uninstall-Module AzureAD` in ihrer PowerShell-Sitzung ausführen, und dann mit `Install-Module AzureADPreview` die Vorschauversion installieren.</span><span class="sxs-lookup"><span data-stu-id="fdea4-111">If you have the 2.0 general availability version of the Azure AD PowerShell module (AzureAD) installed, you must uninstall it by running `Uninstall-Module AzureAD` in your PowerShell session, and then install the preview version by running `Install-Module AzureADPreview`.</span></span>

- <span data-ttu-id="fdea4-112">Wenn Sie die Vorschauversion bereits installiert haben, führen Sie `Install-Module AzureADPreview` aus, um sicherzustellen, dass es sich um die neueste Version dieses Moduls handelt.</span><span class="sxs-lookup"><span data-stu-id="fdea4-112">If you have already installed the preview version, run `Install-Module AzureADPreview` to make sure it's the latest version of this module.</span></span>

> [!NOTE]
> <span data-ttu-id="fdea4-113">Sie müssen über globale Administratorrechte verfügen, um diese Befehle ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="fdea4-113">You must have global admin rights to run these commands.</span></span> 

<span data-ttu-id="fdea4-114">Führen Sie das folgende Skript aus und ändern Sie */<GroupName/>* auf den Namen der Gruppe, für den Sie Gastzugriff sperren möchten.</span><span class="sxs-lookup"><span data-stu-id="fdea4-114">Run the following script, changing */<GroupName/>* to the name of the group where you want to block guest access.</span></span>

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

<span data-ttu-id="fdea4-115">Zum Überprüfen Ihrer Einstellungen führen Sie diesen Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="fdea4-115">To verify your settings, run this command:</span></span>

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

<span data-ttu-id="fdea4-116">Die Überprüfung sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="fdea4-116">The verification looks like this:</span></span>
    
![Screenshot des PowerShell-Fensters, das anzeigt, dass der Gastgruppenzugriff auf falsch festgelegt wurde.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)
  
## <a name="allow-or-block-guest-access-based-on-their-domain"></a><span data-ttu-id="fdea4-118">Zulassen oder Blockieren des Gastzugriffs basierend auf der Domäne</span><span class="sxs-lookup"><span data-stu-id="fdea4-118">Allow or block guest access based on their domain</span></span>

<span data-ttu-id="fdea4-119">Sie können Gastbenutzer zulassen oder blockieren, die eine bestimmte Domäne verwenden.</span><span class="sxs-lookup"><span data-stu-id="fdea4-119">You can allow or block guest users who are using a specific domain.</span></span> <span data-ttu-id="fdea4-120">Nehmen wir z. B. an, dass Ihr Unternehmen (Contoso) über eine Partnerschaft mit einem anderen Unternehmen (Fabrikam) verfügt. Sie können Fabrikam zu Ihrer Zulassungsliste hinzufügen, damit Ihre Benutzer diese Gäste zu ihren Gruppen hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="fdea4-120">For example, if your business (Contoso) has a partnership with another business (Fabrikam), you can add Fabrikam to your Allow list so your users can add those guests to their groups.</span></span>

<span data-ttu-id="fdea4-121">Weitere Informationen finden Sie unter [Zulassen oder Blockieren von Einladungen für B2B-Benutzer von bestimmten Organisationen](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list).</span><span class="sxs-lookup"><span data-stu-id="fdea4-121">For more information, see [Allow or block invitations to B2B users from specific organizations](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list).</span></span>

## <a name="add-guests-to-the-global-address-list"></a><span data-ttu-id="fdea4-122">Hinzufügen von Gästen zur globalen Adressliste</span><span class="sxs-lookup"><span data-stu-id="fdea4-122">Add guests to the global address list</span></span>

<span data-ttu-id="fdea4-123">Standardmäßig sind Gastbenutzer in der globalen Adressliste von Exchange nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="fdea4-123">By default, guests aren't visible in the Exchange Global Address List.</span></span> <span data-ttu-id="fdea4-124">Führen Sie die nachstehenden Schritte aus, um einen Gast in der globalen Adressliste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fdea4-124">Use the steps listed below to make a guest visible in the global address list.</span></span>

<span data-ttu-id="fdea4-125">Suchen Sie die ObjectID des Gastbenutzers:</span><span class="sxs-lookup"><span data-stu-id="fdea4-125">Find the guest user's ObjectID by running:</span></span>

```PowerShell
Get-AzureADUser -Filter "userType eq 'Guest'"
```

<span data-ttu-id="fdea4-126">Führen Sie dann die folgenden Aktionen mit den entsprechenden Werten für Objekt-ID, Vorname, Nachname, Anzeigename und Telefonnummer aus.</span><span class="sxs-lookup"><span data-stu-id="fdea4-126">Then run the following using the appropriate values for ObjectID, GivenName, Surname, DisplayName, and TelephoneNumber.</span></span>

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-articles"></a><span data-ttu-id="fdea4-127">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="fdea4-127">Related articles</span></span>

[<span data-ttu-id="fdea4-128">Verwalten von Gruppenmitgliedschaften im Microsoft 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="fdea4-128">Manage Group membership in the Microsoft 365 admin center</span></span>](https://docs.microsoft.com/microsoft-365/admin/create-groups/add-or-remove-members-from-groups)
  
[<span data-ttu-id="fdea4-129">Azure Active Directory Domain Services-Zugriffsüberprüfungen</span><span class="sxs-lookup"><span data-stu-id="fdea4-129">Azure Active Directory access reviews</span></span>](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[<span data-ttu-id="fdea4-130">Set-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="fdea4-130">Set-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser)