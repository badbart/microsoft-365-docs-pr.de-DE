---
title: Microsoft 365 Netzwerkbewertung (Vorschau)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 Netzwerkbewertung (Vorschau)
ms.openlocfilehash: aacbdf73da9552a12bde250e51544f1de533637c
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46695982"
---
# <a name="microsoft-365-network-assessment-preview"></a><span data-ttu-id="1552b-103">Microsoft 365 Netzwerkbewertung (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="1552b-103">Microsoft 365 network assessment (preview)</span></span>

<span data-ttu-id="1552b-104">In der Microsoft 365 Admin Center-Verbindung mit der Microsoft 365-Seite destillieren **Netzwerkbewertungen** ein Aggregat vieler Netzwerk Leistungs Metriken in einer Momentaufnahme ihres Unternehmensnetzwerk Status, dargestellt durch einen Points-Wert von 1-100.</span><span class="sxs-lookup"><span data-stu-id="1552b-104">In the Microsoft 365 Admin Center's Connectivity to Microsoft 365 page, **network assessments** distill an aggregate of many network performance metrics into a snapshot of your enterprise network health, represented by a points value from 1 - 100.</span></span> <span data-ttu-id="1552b-105">Netzwerkbewertungen sind sowohl für den gesamten Mandanten als auch für jeden geografischen Standort ausgelegt, von dem aus Benutzer eine Verbindung mit Ihrem Mandanten herstellen, sodass Microsoft 365-Administratoren eine einfache Möglichkeit haben, eine Gestalt der Netzwerkintegrität des Unternehmens sofort zu erfassen und schnell einen detaillierten Bericht für einen beliebigen globalen Office-Standort aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="1552b-105">Network assessments are scoped to both the entire tenant and for each geographic location from which users connect to your tenant, providing Microsoft 365 administrators with an easy way to instantly grasp a gestalt of the enterprise's network health and quickly drill down into a detailed report for any global office location.</span></span>

<span data-ttu-id="1552b-106">Der Wert Netzwerk Bewertungspunkte ist eine durchschnittliche Messung der Wartezeit, der Bandbreite, der Downloadgeschwindigkeit und der Verbindungs Qualitäts Metriken, die zum Zeitpunkt der Anzeige Live kompiliert wurden.</span><span class="sxs-lookup"><span data-stu-id="1552b-106">The network assessment points value is an average measurement of latency, bandwidth, download speed and connection quality metrics compiled live at the time they are viewed.</span></span> <span data-ttu-id="1552b-107">Leistungs Metriken für in Microsoft befindliche Netzwerke werden von diesen Messungen ausgeschlossen, um sicherzustellen, dass die Bewertungsergebnisse eindeutig und für das Unternehmensnetzwerk spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="1552b-107">Performance metrics for Microsoft-owned networks are excluded from these measurements to ensure that assessment results are unambiguous and specific to the corporate network.</span></span>

![Netzwerk Bewertungs Wert](../media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

<span data-ttu-id="1552b-109">Ein sehr niedriger Netzwerk Bewertungs Wert deutet darauf hin, dass Microsoft 365-Clients erhebliche Probleme beim Herstellen einer Verbindung mit dem Mandanten oder beim aufrecht erhalten einer reaktionsfähigen Benutzeroberfläche haben, während ein hoher Wert ein ordnungsgemäß konfiguriertes Netzwerk mit einigen fortlaufenden Leistungsproblemen angibt.</span><span class="sxs-lookup"><span data-stu-id="1552b-109">A very low network assessment value suggests that Microsoft 365 clients will have significant problems connecting to the tenant or maintaining a responsive user experience, while a high value indicates a properly configured network with few ongoing performance issues.</span></span> <span data-ttu-id="1552b-110">Ein Wert von 80% stellt eine gesunde Basislinie dar, bei der nicht erwartet werden soll, dass reguläre Benutzer Beschwerden über die Microsoft 365-Konnektivität oder die Reaktionsfähigkeit aufgrund der Netzwerkleistung empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="1552b-110">A value of 80% represents a healthy baseline where you should not expect to receive regular user complaints about Microsoft 365 connectivity or responsiveness due to network performance.</span></span> <span data-ttu-id="1552b-111">Wenn die Verbesserungen für eine iterative Netzwerkkonnektivität vorgenommen werden, steigt dieser Wert zusammen mit der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="1552b-111">As iterative network connectivity improvements are made, this value will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1552b-112">Netzwerk Einblicke, Leistungsempfehlungen und Bewertungen im Microsoft 365 Admin Center befinden sich derzeit im Vorschaustatus und stehen nur für Microsoft 365-Mandanten zur Verfügung, die im Feature Preview-Programm registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="1552b-112">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Microsoft 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="network-assessment-panel"></a><span data-ttu-id="1552b-113">Netzwerk Bewertungsbereich</span><span class="sxs-lookup"><span data-stu-id="1552b-113">Network assessment panel</span></span>

<span data-ttu-id="1552b-114">Bei jeder Netzwerkbewertung, unabhängig davon, ob Sie auf den Mandanten oder einen bestimmten Standort beschränkt ist, wird ein Bereich mit Details zur Bewertung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1552b-114">Each network assessment, whether scoped to the tenant or to a specific office location, shows a panel with details about the assessment.</span></span> <span data-ttu-id="1552b-115">Dieses Panel zeigt ein Balkendiagramm der Bewertung sowohl als Prozentsatz als auch als Gesamtpunktzahl für jede Arbeitsauslastung der Komponente einschließlich der Arbeitslasten, bei denen Messdaten empfangen wurden.</span><span class="sxs-lookup"><span data-stu-id="1552b-115">This panel shows a bar chart of the assessment both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="1552b-116">Für eine Bewertung des Office-Standortnetzwerks zeigen wir auch einen Benchmark an, bei dem es sich um den Median aller Microsoft 365-Clients handelt, von denen Daten in derselben Stadt wie Ihr Bürostandort gemeldet wurden.</span><span class="sxs-lookup"><span data-stu-id="1552b-116">For an office location network assessment, we also show a benchmark which is the median of all Microsoft 365 clients that reported data in the same city as your office location.</span></span>

![Beispiel für einen Netzwerk Bewertungs Wert](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

<span data-ttu-id="1552b-118">Der **Bewertungs Aufschlüsselung** im Bereich zeigt die Bewertung für jede der Komponenten Arbeitsauslastungen.</span><span class="sxs-lookup"><span data-stu-id="1552b-118">The **Assessment breakdown** in the panel shows the assessment for each of the component workloads.</span></span>

<span data-ttu-id="1552b-119">Der **Bewertungsverlauf** zeigt die letzten 30 Tage der Bewertung und die Benchmark an.</span><span class="sxs-lookup"><span data-stu-id="1552b-119">The **Assessment history** shows the past 30 days of the assessment and the benchmark.</span></span>

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a><span data-ttu-id="1552b-120">Assessments für Mandanten Netzwerke und Netzwerkbewertungen für Office-Standorte</span><span class="sxs-lookup"><span data-stu-id="1552b-120">Tenant network assessments and office location network assessments</span></span>

<span data-ttu-id="1552b-121">Eine Netzwerkbewertung misst den Entwurf des Netzwerkperimeters eines Office-Standorts für das Microsoft-Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="1552b-121">A network assessment measures the design of the network perimeter of an office location to Microsoft's network.</span></span> <span data-ttu-id="1552b-122">Verbesserungen am Netzwerkperimeter werden am besten an jedem Office-Standort vorgenommen, oder wenn die Netzwerkkonnektivität aggregiert ist, können Verbesserungen auftreten, die sich auf mehrere Standorte auswirken.</span><span class="sxs-lookup"><span data-stu-id="1552b-122">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>

<span data-ttu-id="1552b-123">Wir zeigen einen Wert für die Netzwerkbewertung für den gesamten Microsoft 365-Mandanten auf der Seite "Netzwerk Leistungsübersicht" und einen bestimmten Wert für jeden erkannten Office-Standort auf der Zusammenfassungsseite dieses Speicherorts an.</span><span class="sxs-lookup"><span data-stu-id="1552b-123">We show a network assessment value for the whole Microsoft 365 tenant on the network performance overview page and a specific value for each detected office location on that location's summary page.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="1552b-124">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1552b-124">Exchange Online</span></span>

<span data-ttu-id="1552b-125">Für Exchange Online wird die TCP-Wartezeit vom Clientcomputer auf den Exchange-Front-End-Server gemessen.</span><span class="sxs-lookup"><span data-stu-id="1552b-125">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="1552b-126">Dies kann durch die Entfernung beeinträchtigt werden, über die das Netzwerk über die Kunden LAN und WAN reist.</span><span class="sxs-lookup"><span data-stu-id="1552b-126">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="1552b-127">Es kann auch durch Netzwerk-zwischengeschaltete Geräte oder Dienste beeinträchtigt werden, die die Konnektivität verzögern oder dazu führen, dass Pakete erneut gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="1552b-127">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="1552b-128">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1552b-128">SharePoint Online</span></span>

<span data-ttu-id="1552b-129">Für SharePoint Online wird die Downloadgeschwindigkeit gemessen, die ein Benutzer für den Zugriff auf ein Dokument zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="1552b-129">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="1552b-130">Dies kann durch die verfügbare Bandbreite zwischen dem Clientcomputer und dem Netzwerk von Microsoft auf Netzwerk Schaltkreisen beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="1552b-130">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft's network.</span></span> <span data-ttu-id="1552b-131">Es wird auch häufig von Netzwerküberlastung beeinflusst, die in Engpässen bei komplexen Netzwerkgeräten oder in schlechten WLAN-Abdeckungsbereichen vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1552b-131">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="1552b-132">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1552b-132">Microsoft Teams</span></span>

<span data-ttu-id="1552b-133">Für Microsoft Teams wird die Netzwerkqualität als UDP-Wartezeit, UDP-Jitter und UDP-Paketverlust gemessen.</span><span class="sxs-lookup"><span data-stu-id="1552b-133">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="1552b-134">UDP wird für die Audio-und Video Medien Konnektivität für Anrufe und Konferenzen für Microsoft Teams verwendet.</span><span class="sxs-lookup"><span data-stu-id="1552b-134">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="1552b-135">Dies kann durch die gleichen Faktoren wie Wartezeit und Downloadgeschwindigkeit sowie Verbindungs Lücken in der UDP-Unterstützung eines Netzwerks beeinträchtigt werden, da UDP separat mit dem häufigeren TCP-Protokoll konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="1552b-135">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network's UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="related-topics"></a><span data-ttu-id="1552b-136">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1552b-136">Related topics</span></span>

[<span data-ttu-id="1552b-137">Empfehlungen zur Netzwerkleistung im Microsoft 365 Admin Center (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="1552b-137">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="1552b-138">Microsoft 365 Network Performance Insights (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="1552b-138">Microsoft 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="1552b-139">Microsoft 365 Connectivity Test im M365 Admin Center (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="1552b-139">Microsoft 365 connectivity test in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="1552b-140">Microsoft 365 Network Connectivity Location Services (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="1552b-140">Microsoft 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)