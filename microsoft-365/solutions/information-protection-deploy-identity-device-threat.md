---
title: Verwenden von Identitäts-, Geräte-und Bedrohungsschutz für die Datenschutzverordnung
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- M365solutions
ms.custom: ''
description: Verhindern von Verletzungen personenbezogener Daten mit Identitäts-, Geräte-und Bedrohungsschutz Diensten von Microsoft 365.
ms.openlocfilehash: 74894037ef2fe56aeb5bc44340cd8a946863baff
ms.sourcegitcommit: b03a7ad0a80f8b839f40b8d396ab3a049491a12f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2020
ms.locfileid: "44695079"
---
# <a name="use-identity-device-and-threat-protection-for-data-privacy-regulation"></a><span data-ttu-id="edd0c-103">Verwenden von Identitäts-, Geräte-und Bedrohungsschutz für die Datenschutzverordnung</span><span class="sxs-lookup"><span data-stu-id="edd0c-103">Use identity, device, and threat protection for data privacy regulation</span></span>

<span data-ttu-id="edd0c-104">Microsoft 365 bietet eine Reihe von Funktionen für Identitäts-, Geräte-und Bedrohungsschutz, die von Organisationen eingesetzt werden können, um die Einhaltung von Datenschutzbestimmungen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="edd0c-104">Microsoft 365 provides a number of identity, device, and threat protection capabilities that organizations can employ to help comply with data privacy-related compliance regulations.</span></span> <span data-ttu-id="edd0c-105">In diesem Artikel wird beschrieben, was die Datenschutzbestimmungen in diesen Bereichen erfordern und enthält eine Liste der zugehörigen Microsoft 365-Features und-Dienste mit Links zu weiteren Informationen, die Ihnen dabei helfen, die Implementierungsanforderungen zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="edd0c-105">This article describes what the data privacy regulations require in these areas and provides a listing of related Microsoft 365 features and services with links to more information to help you address implementation requirements.</span></span>

## <a name="how-identity-device-and-threat-protection-relate-to-data-privacy-regulation"></a><span data-ttu-id="edd0c-106">Wie Identitäts-, Geräte-und Bedrohungsschutz mit der Datenschutzverordnung in Zusammenhangstehen</span><span class="sxs-lookup"><span data-stu-id="edd0c-106">How identity, device, and threat protection relate to data privacy regulation</span></span>

<span data-ttu-id="edd0c-107">Während die Datenschutzbestimmungen sich in ihrer Besonderheit unterscheiden, ist die Essenz dessen, was Sie bezeichnen, im dsgvo-Artikel 5 (1) (f) aufgeführt, in dem Folgendes heißt:</span><span class="sxs-lookup"><span data-stu-id="edd0c-107">While the data privacy regulations vary in their specificity, the essence of what they call for is embodied in the GDPR’s Article 5(1)(f), which states that:</span></span> 

- <span data-ttu-id="edd0c-108">Personenbezogene Daten werden in einer Weise verarbeitet, die eine angemessene Sicherheit der personenbezogenen Daten einschließlich des Schutzes vor unbefugter oder unrechtmäßiger Verarbeitung sowie vor versehentlichem Verlust, Zerstörung oder Beschädigung durch geeignete technische oder organisatorische Maßnahmen ("Integrität und Vertraulichkeit") gewährleistet.</span><span class="sxs-lookup"><span data-stu-id="edd0c-108">Personal data shall be processed in a manner that ensures appropriate security of the personal data, including protection against unauthorized or unlawful processing and against accidental loss, destruction or damage, using appropriate technical or organizational measures ('integrity and confidentiality').</span></span>

<span data-ttu-id="edd0c-109">Da Verletzungen von personenbezogenen Daten häufig durch Administrator-oder Endbenutzerkonto Kompromisse und böswilligen Systemzugriff verursacht werden.</span><span class="sxs-lookup"><span data-stu-id="edd0c-109">Because personal data breaches are often caused by administrative or end-user account compromise and malicious system access.</span></span> <span data-ttu-id="edd0c-110">Beispielsweise kann ein Administratorkonto-hacken dazu führen, dass Kundenkreditkartennummern oder andere persönliche Informationen ausgefiltert werden.</span><span class="sxs-lookup"><span data-stu-id="edd0c-110">For example, an admin account hack can result in exfiltration of customer credit card numbers or other personal information.</span></span> <span data-ttu-id="edd0c-111">Es sollten alle allgemein anerkannten Identitäts-, Geräte-und Bedrohungsschutz Funktionen, die mit Microsoft 365 verfügbar sind, implementiert werden, was sich in der Konformitätsbewertung widerspiegelt.</span><span class="sxs-lookup"><span data-stu-id="edd0c-111">All the generally advisable identity, device, and threat protection available with Microsoft 365 potentially should be implemented, which will be reflected in your Compliance Score.</span></span>

## <a name="using-the-results-of-your-assessment-work-and-compliance-score"></a><span data-ttu-id="edd0c-112">Verwenden der Ergebnisse ihrer Beurteilungs Arbeit und der Konformitätsbewertung</span><span class="sxs-lookup"><span data-stu-id="edd0c-112">Using the results of your assessment work and Compliance Score</span></span>

<span data-ttu-id="edd0c-113">Die Konformitätsbewertung umfasst Identitäts-, Geräte-und Bedrohungsschutz mithilfe dieser Kategorien:</span><span class="sxs-lookup"><span data-stu-id="edd0c-113">Compliance Score includes identity, device, and threat protection using these categories:</span></span>

- <span data-ttu-id="edd0c-114">Identity entspricht der **Steuerelement Zugriffs** Kategorie</span><span class="sxs-lookup"><span data-stu-id="edd0c-114">Identity corresponds to the **Control Access** category</span></span>
- <span data-ttu-id="edd0c-115">Gerät entspricht der Kategorie " **Geräte verwalten** "</span><span class="sxs-lookup"><span data-stu-id="edd0c-115">Device corresponds to the **Manage Devices** category</span></span>
- <span data-ttu-id="edd0c-116">Bedrohungsschutz entspricht der Kategorie " **Schutz vor Bedrohungen** "</span><span class="sxs-lookup"><span data-stu-id="edd0c-116">Threat protection corresponds to the **Protect Against Threats** category</span></span>
 
<span data-ttu-id="edd0c-117">Wenn diese in unserem Beispielsatz mit vier wichtigen Datenschutzbestimmungen ausgewählt wurden, gibt das Kompatibilitäts Ergebnis 90 Verbesserungs Aktionen an, von denen die meisten eine "27" erzielt haben.</span><span class="sxs-lookup"><span data-stu-id="edd0c-117">If these are selected across our sample set of four major data privacy regulations, Compliance Score specifies 90 improvement actions, most of which are scored a "27".</span></span> <span data-ttu-id="edd0c-118">Da eine solche große Zahl durch die Konformitätsbewertung für diese Kategorien aufgerufen wird, werden einige der häufigsten hier aufgeführten als Referenz aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="edd0c-118">Since such a large number are called out by Compliance Score for these categories, some of the more common ones are listed here, for reference.</span></span>

<span data-ttu-id="edd0c-119">Verwenden Sie [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) für Identity und die Kategorie **Steuerelement Zugriff** , mit der Sie folgende Möglichkeiten haben:</span><span class="sxs-lookup"><span data-stu-id="edd0c-119">Use [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) for identity and the **Control Access** category, with which you can:</span></span>

- <span data-ttu-id="edd0c-120">Implementieren der Wiedergabe-resistenten Authentifizierung (um "Menschen in der Mitte"-Angriffe zu verhindern)</span><span class="sxs-lookup"><span data-stu-id="edd0c-120">Implement replay-resistant authentication (to prevent “Man in the middle” attacks)</span></span>
- <span data-ttu-id="edd0c-121">Legacy Authentifizierung blockieren.</span><span class="sxs-lookup"><span data-stu-id="edd0c-121">Block legacy authentication.</span></span>
- <span data-ttu-id="edd0c-122">Konfigurieren von Risikorichtlinien für Benutzer Risiken und Benutzeranmeldungen</span><span class="sxs-lookup"><span data-stu-id="edd0c-122">Configure user risk and user sign-in risk policies.</span></span>
- <span data-ttu-id="edd0c-123">Aktivieren Sie den bedingten Zugriff und die mehrstufige Authentifizierung (MFA) für Administratoren und nicht-Administratoren.</span><span class="sxs-lookup"><span data-stu-id="edd0c-123">Enable Conditional Access and multi-factor authentication (MFA) for admins and non-admins.</span></span>
- <span data-ttu-id="edd0c-124">Konfigurieren und Erzwingen von Kennwortrichtlinien</span><span class="sxs-lookup"><span data-stu-id="edd0c-124">Configure and enforce password policies.</span></span>
- <span data-ttu-id="edd0c-125">Einschränken des Zugriffs auf privilegierte Konten mit Azure AD privilegierten Identitätsverwaltung.</span><span class="sxs-lookup"><span data-stu-id="edd0c-125">Restrict access to privileged accounts with Azure AD Privileged Identity Management.</span></span>
- <span data-ttu-id="edd0c-126">Zugriff beim Beenden deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="edd0c-126">Disable access upon termination.</span></span>
- <span data-ttu-id="edd0c-127">Überwachen von Benutzerkonten und Statusänderungen.</span><span class="sxs-lookup"><span data-stu-id="edd0c-127">Audit user accounts and status changes.</span></span>
- <span data-ttu-id="edd0c-128">Überprüfen Sie die Rollengruppe und die administrativen Änderungen.</span><span class="sxs-lookup"><span data-stu-id="edd0c-128">Review role group and administrative changes.</span></span>

<span data-ttu-id="edd0c-129">Verwenden Sie [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) für Geräte und die Kategorie **Manage Devices** , mit der Sie folgende Möglichkeiten haben:</span><span class="sxs-lookup"><span data-stu-id="edd0c-129">Use [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) for devices and the **Manage Devices** category, with which you can:</span></span>

- <span data-ttu-id="edd0c-130">Gesperrte beschädigte und verwurzelte Mobile Geräte blockieren.</span><span class="sxs-lookup"><span data-stu-id="edd0c-130">Block jail broken and rooted mobile devices.</span></span>
- <span data-ttu-id="edd0c-131">Konfigurieren von InTune für die Verwaltung mobiler Geräte.</span><span class="sxs-lookup"><span data-stu-id="edd0c-131">Configure Intune for mobile device management.</span></span>
- <span data-ttu-id="edd0c-132">Erstellen Sie Konformitätsrichtlinien für Android-, Ios-, macOS-und Windows-Geräte.</span><span class="sxs-lookup"><span data-stu-id="edd0c-132">Create compliance policies for Android, iOS, macOS and Windows devices.</span></span>
- <span data-ttu-id="edd0c-133">Erstellen Sie ein Geräte Konfigurationsprofil für Android-, Ios-, macOS-und Windows-Geräte.</span><span class="sxs-lookup"><span data-stu-id="edd0c-133">Create a device configuration profile for Android, iOS, macOS and Windows devices.</span></span>
- <span data-ttu-id="edd0c-134">Erstellen von App-Schutzrichtlinien für IOS und Windows.</span><span class="sxs-lookup"><span data-stu-id="edd0c-134">Create app protection policies for iOS and Windows.</span></span>
- <span data-ttu-id="edd0c-135">Informationen mit Sperrbildschirm verbergen.</span><span class="sxs-lookup"><span data-stu-id="edd0c-135">Conceal information with lock screen.</span></span>
- <span data-ttu-id="edd0c-136">Implementieren von Kennwortrichtlinien für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="edd0c-136">Implement password policies for mobile devices.</span></span>
- <span data-ttu-id="edd0c-137">Erfordern, dass Mobile Geräte nach Inaktivität sperren.</span><span class="sxs-lookup"><span data-stu-id="edd0c-137">Require mobile devices to lock upon inactivity.</span></span>
- <span data-ttu-id="edd0c-138">Erfordern, dass Mobile Geräte bei mehreren Anmeldefehlern gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="edd0c-138">Require mobile devices to wipe on multiple sign-in failures.</span></span>

<span data-ttu-id="edd0c-139">Verwenden Sie [Exchange Online Schutz und Office 365 Advanced Threat Protection (ATP)](../security/office-365-security/office-365-atp.md) für die Kategorie **Protect Against Threats** , mit der Sie folgende Schritte durchführen können:</span><span class="sxs-lookup"><span data-stu-id="edd0c-139">Use [Exchange Online Protection and Office 365 Advanced Threat Protection (ATP)](../security/office-365-security/office-365-atp.md) for the **Protect Against Threats** category, with which you can:</span></span>

- <span data-ttu-id="edd0c-140">Aktivieren Sie die Sender Authentifizierung (SPF, DMARC und DKIM).</span><span class="sxs-lookup"><span data-stu-id="edd0c-140">Enable sender authentication (SPF, DMARC and DKIM).</span></span>
- <span data-ttu-id="edd0c-141">Richten Sie Office 365 Anti-Phishing-Richtlinien für Advanced Threat Protection (ATP) ein.</span><span class="sxs-lookup"><span data-stu-id="edd0c-141">Set up Office 365 Advanced Threat Protection (ATP) anti-phishing policies.</span></span>
- <span data-ttu-id="edd0c-142">Implementieren Sie ATP-sichere Anlagen.</span><span class="sxs-lookup"><span data-stu-id="edd0c-142">Implement ATP Safe Attachments.</span></span>
- <span data-ttu-id="edd0c-143">Implementieren Sie ATP-sichere Links.</span><span class="sxs-lookup"><span data-stu-id="edd0c-143">Implement ATP Safe Links.</span></span>
- <span data-ttu-id="edd0c-144">Implementieren von Malware Erkennungs-und-Antwort Richtlinien</span><span class="sxs-lookup"><span data-stu-id="edd0c-144">Implement malware detection and response policies.</span></span>
- <span data-ttu-id="edd0c-145">Implementieren Sie ausgehende und eingehende Spam Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="edd0c-145">Implement outbound and inbound spam policies.</span></span>

### <a name="references"></a><span data-ttu-id="edd0c-146">Referenzen</span><span class="sxs-lookup"><span data-stu-id="edd0c-146">References:</span></span>

- [<span data-ttu-id="edd0c-147">Allgemeine Identitäts- und Gerätezugriffsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="edd0c-147">Common identity and device access policies</span></span>](../enterprise/identity-access-policies.md)
- [<span data-ttu-id="edd0c-148">Schutz vor Bedrohungen in Office 365</span><span class="sxs-lookup"><span data-stu-id="edd0c-148">Protect against threats in Office 365</span></span>](https://support.office.com/article/protect-against-threats-in-office-365-b10023f6-f30f-45d3-b3ad-b71aa4aa0d58)
- [<span data-ttu-id="edd0c-149">Sichere Anlagen in ATP</span><span class="sxs-lookup"><span data-stu-id="edd0c-149">ATP Safe Attachments</span></span>](../security/office-365-security/atp-safe-attachments.md)
- [<span data-ttu-id="edd0c-150">ATP-sichere Links</span><span class="sxs-lookup"><span data-stu-id="edd0c-150">ATP Safe Links</span></span>](../security/office-365-security/atp-safe-links.md)
- [<span data-ttu-id="edd0c-151">Sichere Dokumente in ATP</span><span class="sxs-lookup"><span data-stu-id="edd0c-151">ATP Safe Documents</span></span>](../security/office-365-security/safe-docs.md)