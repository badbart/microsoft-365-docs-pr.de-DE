---
title: Schützen von Microsoft 365 Cloud-Diensten vor Denial-of-Service-Angriffen
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: In diesem Artikel erfahren Sie, wie Microsoft seine Cloud-Dienste vor Denial-of-Service-Angriffen (DOS) verteidigt.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 26c3df54811ffee06797c635bc565fcbe78b58fa
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690770"
---
# <a name="defending-microsoft-365-cloud-services-against-denial-of-service-attacks"></a><span data-ttu-id="ffd8f-103">Schützen von Microsoft 365 Cloud-Diensten vor Denial-of-Service-Angriffen</span><span class="sxs-lookup"><span data-stu-id="ffd8f-103">Defending Microsoft 365 cloud services against denial-of-service attacks</span></span>

<span data-ttu-id="ffd8f-104">Microsoft-Rechenzentren werden durch umfassende Sicherheitsvorkehrungen geschützt, einschließlich Umkreis Fechten, Videokameras, Sicherheitspersonal und sicheren Eingängen, die Biometrie, Smartcard und mehrstufige Authentifizierung verwenden.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-104">Microsoft datacenters are protected by defense-in-depth security that includes perimeter fencing, video cameras, security personnel, and secure entrances that use biometrics, smartcard, and multi-factor authentication.</span></span> <span data-ttu-id="ffd8f-105">Die tiefen Verteidigungs Sicherheit wird durch jeden Bereich der Einrichtung und für jede physische SERVEREINHEIT fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-105">The defense-in-depth security continues through every area of the facility and to each physical server unit.</span></span> <span data-ttu-id="ffd8f-106">Die [Microsoft Cloud Infrastructure and Operations Group](https://www.microsoft.com/cloud-platform/global-datacenters) bietet die Kerninfrastruktur und grundlegende Technologien für unsere Cloud-Dienste.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-106">The [Microsoft Cloud Infrastructure and Operations Group](https://www.microsoft.com/cloud-platform/global-datacenters) delivers the core infrastructure and foundational technologies for our cloud services.</span></span> <span data-ttu-id="ffd8f-107">Unsere Rechenzentren entsprechen Branchenstandards für physische Sicherheit und Zuverlässigkeit und werden von Microsoft Operationspersonal verwaltet, überwacht und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-107">Our datacenters comply with industry standards for physical security and reliability and are managed, monitored, and administered by Microsoft operations personnel.</span></span>

<span data-ttu-id="ffd8f-108">Um unsere Cloud-Dienste weiter zu schützen, bietet Microsoft ein DDoS-Abwehrsystem an, das Teil der Microsoft Azure kontinuierlichen Überwachungs-und Penetrationstest Prozesse ist.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-108">To further protect our cloud services, Microsoft provides a DDoS defense system that is part of the Microsoft Azure continuous monitoring and penetration-testing processes.</span></span> <span data-ttu-id="ffd8f-109">Das Azure DDoS-Abwehrsystem ist nicht nur für Angriffe von außen, sondern auch von anderen Azure-Mandanten ausgelegt.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-109">The Azure DDoS defense system is designed not only to withstand attacks from the outside, but also from other Azure tenants.</span></span> <span data-ttu-id="ffd8f-110">Azure verwendet standardmäßige Erkennungs-und Minderungs Methoden wie SYN-Cookies, raten Begrenzungen und Verbindungs Grenzwerte zum Schutz vor DDoS-Angriffen.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-110">Azure uses standard detection and mitigation techniques such as SYN cookies, rate limiting, and connection limits to protect against DDoS attacks.</span></span>

<span data-ttu-id="ffd8f-111">Die Cloud-Dienste von Microsoft unterliegen der Bedrohung durch Angriffe aus mehreren Quellen.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-111">Microsoft's cloud services are subject to the threat of attack from multiple sources.</span></span> <span data-ttu-id="ffd8f-112">Zur Minderung und zum Schutz vor den verschiedenen DOS-Bedrohungen wurde ein hoch skalierbares und dynamisches Azure-basiertes System zur Erkennung und Abwehr von Bedrohungen entwickelt und implementiert, mit dem Hauptziel, die zugrunde liegende Infrastruktur vor DoS-Angriffen zu schützen und Dienstunterbrechungen für Cloud Services-Kunden zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-112">To mitigate and protect against the various DoS threats, a highly-scalable and dynamic Azure-based threat detection and mitigation system have been developed and implemented with the primary objective of protecting the underlying infrastructure from DoS attacks and helping to prevent service interruptions for cloud services customers.</span></span> <span data-ttu-id="ffd8f-113">Das Azure DOS-Minderungs System schützt eingehende, ausgehende und Region-zu-Region-Datenverkehr.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-113">The Azure DoS mitigation system protects inbound, outbound, and region-to-region traffic.</span></span>

<span data-ttu-id="ffd8f-114">Die meisten DOS-Angriffe werden für Ziele auf den Netzwerk-(L3) und Transport Ebenen (L4) des OSI-Modells ( [Open Systems Interconnection](https://docs.microsoft.com/windows-hardware/drivers/network/windows-network-architecture-and-the-osi-model) ) gestartet.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-114">Most DoS attacks launched against targets at the Network (L3) and Transport (L4) layers of the [Open Systems Interconnection](https://docs.microsoft.com/windows-hardware/drivers/network/windows-network-architecture-and-the-osi-model) (OSI) model.</span></span> <span data-ttu-id="ffd8f-115">Angriffe auf die L3-und L4-Layer wurden entwickelt, um eine Netzwerkschnittstelle oder einen Dienst mit Angriffs Datenverkehr hoch zufluten, um Ressourcen zu überlasten und die Fähigkeit zu verweigern, auf legitimen Datenverkehr zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-115">Attacks directed at the L3 and L4 layers are designed to flood a network interface or service with attack traffic to overwhelm resources and deny the ability to respond to legitimate traffic.</span></span> <span data-ttu-id="ffd8f-116">Insbesondere L3-und L4-Angriffe versuchen, entweder die Kapazität von Netzwerkverbindungen, Geräten oder Diensten zu sättigen oder die CPUs von Servern oder virtuellen Computern zu überlasten, die eine Anwendung unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-116">Specifically, L3 and L4 attacks attempt to either saturate the capacity of network links, devices, or services or overwhelm the CPUs of servers or virtual machines supporting an application.</span></span>

<span data-ttu-id="ffd8f-117">Zum Schutz vor L3-und L4-Angriffen hat Microsoft eine Lösung entwickelt, entwickelt und bereitgestellt, die speziell darauf abzielt, die Infrastruktur und die Kunden Ziele zu schützen, die durch den Schutz dieser Schichten angegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-117">To guard against L3 and L4 attacks Microsoft has designed, developed, and deployed a solution aimed specifically at safeguarding the infrastructure and customer targets that come under attack by protecting these layers.</span></span> <span data-ttu-id="ffd8f-118">Durch den Schutz der Infrastruktur wird sichergestellt, dass der Angriffs Datenverkehr, der für einen Kunden bestimmt ist, keinen Kollateralschaden oder eine verringerte Netzwerkqualität für andere Kunden zur Folge hat.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-118">Protecting the infrastructure ensures that attack traffic intended for one customer does not result in collateral damage or diminished network quality of service for other customers.</span></span> <span data-ttu-id="ffd8f-119">Die Lösung verwendet Datenverkehrs Samplingdaten von Rechenzentrums Routern.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-119">The solution uses traffic sampling data from datacenter routers.</span></span> <span data-ttu-id="ffd8f-120">Diese Daten werden von einem Netzwerk Überwachungsdienst analysiert, um Angriffe zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-120">This data is analyzed by a network monitoring service to detect attacks.</span></span> <span data-ttu-id="ffd8f-121">Wenn ein Angriff erkannt wird, treten automatisierte Abwehrmechanismen ein.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-121">When an attack is detected, automated defense mechanisms kick in.</span></span>

## <a name="application-level-defenses"></a><span data-ttu-id="ffd8f-122">Verteidigung auf Anwendungsebene</span><span class="sxs-lookup"><span data-stu-id="ffd8f-122">Application-Level Defenses</span></span>
<span data-ttu-id="ffd8f-123">Microsoft Engineering Teams befolgten die strengen Standards, die von der [Microsoft Operational Security Assurance](https://www.microsoft.com/SDL/OperationalSecurityAssurance) zum Schutz von Kundendaten festgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-123">Microsoft engineering teams follow the rigorous standards set by [Microsoft Operational Security Assurance](https://www.microsoft.com/SDL/OperationalSecurityAssurance) to help protect customer data.</span></span> <span data-ttu-id="ffd8f-124">Die Cloud-Dienste von Microsoft wurden absichtlich zur Unterstützung einer sehr hohen Last sowie zum Schutz und zur Milderung von DOS-Angriffen auf Anwendungsebene entwickelt.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-124">Microsoft's cloud services are intentionally built to support a very high load as well as to protect and mitigate against application-level DoS attacks.</span></span> <span data-ttu-id="ffd8f-125">Wir haben eine skalierte Architektur implementiert, in der Dienste über mehrere globale Rechenzentren mit regionaler Isolierung und Einschränkungsfunktionen in einigen Arbeitslasten verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-125">We have implemented a scaled-out architecture where services are distributed across multiple global datacenters with regional isolation and throttling features in some of the workloads.</span></span>

<span data-ttu-id="ffd8f-126">Das Land oder die Region jedes Kunden, das der Administrator des Kunden während der Ersteinrichtung der Dienste identifiziert, bestimmt den primären Speicherort für die Daten dieses Kunden.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-126">Each customer's country or region, which the customer's administrator identifies during the initial setup of the services, determines the primary storage location for that customer's data.</span></span> <span data-ttu-id="ffd8f-127">Kundendaten werden gemäß einer primären/Sicherungsstrategie zwischen redundanten Rechenzentren repliziert.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-127">Customer data is replicated between redundant datacenters according to a primary/backup strategy.</span></span> <span data-ttu-id="ffd8f-128">Ein primäres Rechenzentrum hostet die Anwendungssoftware zusammen mit allen primären Kundendaten, die auf der Software installiert sind.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-128">A primary datacenter hosts the application software along with all the primary customer data running on the software.</span></span> <span data-ttu-id="ffd8f-129">Ein Sicherungsdatencenter bietet ein automatisches Failover.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-129">A backup datacenter provides automatic failover.</span></span> <span data-ttu-id="ffd8f-130">Wenn das primäre Rechenzentrum aus irgendeinem Grund nicht mehr funktionsfähig ist, werden Anforderungen an die Kopie der Software-und Kundendaten im Sicherungsdatencenter umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-130">If the primary datacenter ceases to function for any reason, requests are redirected to the copy of the software and customer data in the backup datacenter.</span></span> <span data-ttu-id="ffd8f-131">Kundendaten können zu einem bestimmten Zeitpunkt entweder im primären oder im Sicherungsdatencenter verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-131">At any given time, customer data may be processed in either the primary or the backup datacenter.</span></span> <span data-ttu-id="ffd8f-132">Durch die Verteilung von Daten in mehreren Rechenzentren wird die betroffene Oberfläche reduziert, wenn ein Rechenzentrum angegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-132">Distributing data across multiple datacenters reduces the affected surface area in case one datacenter is attacked.</span></span> <span data-ttu-id="ffd8f-133">Darüber hinaus können die Dienste im betroffenen Datencenter als einer der Wiederherstellungsmechanismen schnell zum sekundären Datencenter umgeleitet werden und umgekehrt (umgeleitet zurück zum primären Datencenter, sobald der Dienst wiederhergestellt wird).</span><span class="sxs-lookup"><span data-stu-id="ffd8f-133">Furthermore, the services in the affected datacenter can be quickly redirected to the secondary datacenter as one of the recovery mechanisms, and vice versa (redirected back to the primary datacenter once service is restored).</span></span>

<span data-ttu-id="ffd8f-134">Zu den einzelnen Arbeitslasten gehören integrierte Features zur Verwaltung der Ressourcennutzung.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-134">Individual workloads include built-in features that manage resource utilization.</span></span> <span data-ttu-id="ffd8f-135">Beispielsweise sind die Einschränkungs Mechanismen in Exchange Online und SharePoint Online Teil eines mehrschichtigen Ansatzes zur Verteidigung gegen DoS-Angriffe.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-135">For example, the throttling mechanisms in Exchange Online and SharePoint Online are part of a multi-layered approach to defending against DoS attacks.</span></span> <span data-ttu-id="ffd8f-136">Die Einschränkung für Exchange Online Benutzer beruht auf der vom Endbenutzer verbrauchten Ressourcenebene, unabhängig davon, ob sich die Ressourcen in Active Directory, im Exchange Online Informationsspeicher oder an einer anderen Position befinden.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-136">Throttling for Exchange Online users is based on the level of resources consumed by the end user, whether the resources are in Active Directory, the Exchange Online information store, or elsewhere.</span></span> <span data-ttu-id="ffd8f-137">Jedem Client wird ein Budget zugewiesen, um die von einem Benutzer konsumierten Ressourcen einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-137">A budget is allocated to each client to limit the resources consumed by a user.</span></span> <span data-ttu-id="ffd8f-138">Exchange Online Einschränkung für Benutzeraktivität und Systemkomponenten basiert auf der [Arbeitsauslastungsverwaltung](https://technet.microsoft.com/library/jj150503(v=exchg.150).aspx).</span><span class="sxs-lookup"><span data-stu-id="ffd8f-138">Exchange Online throttling for user activity and system components is based on [workload management](https://technet.microsoft.com/library/jj150503(v=exchg.150).aspx).</span></span> <span data-ttu-id="ffd8f-139">Bei einer Exchange Online Arbeitsauslastung handelt es sich um ein Exchange Online Feature, Protokoll oder Dienst, das explizit für die Exchange Online Systemressourcenverwaltung definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-139">An Exchange Online workload is an Exchange Online feature, protocol, or service that has been explicitly defined for the purposes of Exchange Online system resource management.</span></span> <span data-ttu-id="ffd8f-140">Für jede Exchange Online Arbeitsauslastung sind Systemressourcen wie CPU, Postfachdaten Bankvorgänge oder Active Directory Anforderungen zum Ausführen von Benutzeranforderungen oder Hintergrundarbeit erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-140">Each Exchange Online workload requires system resources such as CPU, mailbox database operations, or Active Directory requests to perform user requests or background work.</span></span> <span data-ttu-id="ffd8f-141">Beispiele für Exchange Online Arbeitslasten sind Outlook im Internet, Exchange ActiveSync, Postfachmigration und Postfach-Assistenten.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-141">Examples of Exchange Online workloads include Outlook on the web, Exchange ActiveSync, mailbox migration, and mailbox assistants.</span></span> <span data-ttu-id="ffd8f-142">Mandantenadministratoren können die Einstellungen für die Einschränkung der Exchange-Arbeitsauslastungsverwaltung für Benutzer mit dem Exchange-Verwaltungsshell verwalten.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-142">Tenant administrators can manage Exchange workload management throttling settings for users with the Exchange Management Shell.</span></span> <span data-ttu-id="ffd8f-143">Es gibt verschiedene Formen der Drosselung, die in Exchange Online implementiert wurden, einschließlich PowerShell, Exchange Webdienste und Pop und IMAP, Exchange ActiveSync, Verbindungen mit mobilen Geräten, Empfänger und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-143">There are various forms of throttling that have been implemented within Exchange Online, including PowerShell, Exchange Web Services, and POP and IMAP, Exchange ActiveSync, mobile device connections, recipients, and more.</span></span> <span data-ttu-id="ffd8f-144">Während Administratoren von lokalen Exchange-Bereitstellungen Einschränkungsrichtlinien konfigurieren können, können Administratoren keine Einschränkungsrichtlinien für Exchange Online konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-144">While administrators of on-premises Exchange deployments can configure throttling policies, Administrators cannot configure throttling policies for Exchange Online.</span></span>

<span data-ttu-id="ffd8f-145">Der häufigste Auslöser für die Drosselung in SharePoint Online ist der clientseitige Objektmodellcode (CSOM), der zu viele Aktionen mit zu hoher Frequenz ausführt.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-145">The most common trigger for throttling in SharePoint Online is client-side object model (CSOM) code that performs too many actions at too high a frequency.</span></span> <span data-ttu-id="ffd8f-146">Mit CSOM können zahlreiche Aktionen mit einer einzigen Anforderung durchgeführt werden, die die Verwendungsbeschränkungen überschreiten und die Einschränkung pro Benutzer verursachen kann.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-146">With CSOM, many actions can be performed with a single request, which can exceed usage limits and cause per-user throttling.</span></span>

<span data-ttu-id="ffd8f-147">Unabhängig von der Aktivität, die zu einer Drosselung führen kann, wenn ein Benutzer die Verwendungsbeschränkungen überschreitet, SharePoint Online alle weiteren Anforderungen dieses Benutzerkontos in der Regel für einen kurzen Zeitraum drosseln.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-147">Regardless of the activity that might result in throttling, when a user exceeds usage limits, SharePoint Online throttles any further requests from that user account, usually for a short period.</span></span> <span data-ttu-id="ffd8f-148">Während eine Benutzer Drosselung wirksam ist, werden alle Aktionen dieses Benutzers so lange gedrosselt, bis die Drosselung abläuft, gemäß den folgenden Kriterien:</span><span class="sxs-lookup"><span data-stu-id="ffd8f-148">While a user throttle is in effect, all actions by that user are throttled until the throttle expires, according to the following criteria:</span></span>
- <span data-ttu-id="ffd8f-149">Für Anforderungen, die vom Benutzer direkt in einem Browser ausgeführt werden, wird SharePoint Online an eine Einschränkungs Informationsseite umgeleitet, und die Anforderungen werden nicht erfüllt.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-149">For requests performed by the user directly in a browser, SharePoint Online redirects to a throttling information page, and the requests fail.</span></span>
- <span data-ttu-id="ffd8f-150">Für alle anderen Anforderungen, einschließlich CSOM-Aufrufe, gibt SharePoint Online den HTTP-Statuscode 429 ("zu viele Anforderungen") zurück, und die Anforderungen werden nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-150">For all other requests, including CSOM calls, SharePoint Online returns HTTP status code 429 ("too many requests"), and the requests fail.</span></span>

<span data-ttu-id="ffd8f-151">Wenn der problematische Prozess weiterhin die Verwendungsbeschränkungen überschreitet, kann SharePoint Online den Prozess vollständig blockieren und den HTTP-Statuscode 503 ("Dienst nicht verfügbar") zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-151">If the offending process continues to exceed usage limits, SharePoint Online may completely block the process and return HTTP status code 503 ("service unavailable").</span></span>

## <a name="vulnerability-and-penetration-testing"></a><span data-ttu-id="ffd8f-152">Sicherheitsrisiko und Penetrationstests</span><span class="sxs-lookup"><span data-stu-id="ffd8f-152">Vulnerability and Penetration Testing</span></span>
<span data-ttu-id="ffd8f-153">Microsoft verwendet viele [Sicherheitstechnologien und-Vorgehensweisen](https://www.microsoft.com/trustcenter/security/threatmanagement) , um [die Cloud-Infrastruktur](https://blogs.technet.microsoft.com/hybridcloud/2015/05/05/protecting-your-datacenter-and-cloud-from-emerging-threats/) und lokale Netzwerke vor modernen, ausgeklügelten Bedrohungen zu schützen, einschließlich der Verwendung von Antischadsoftware-Komponenten und-Diensten für Cloud-Dienste, virtuelle Computer (VMS) und andere Systeme.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-153">Microsoft uses many [security technologies and practices](https://www.microsoft.com/trustcenter/security/threatmanagement) to [protect its cloud infrastructure](https://blogs.technet.microsoft.com/hybridcloud/2015/05/05/protecting-your-datacenter-and-cloud-from-emerging-threats/) and on-premises networks against modern, sophisticated threats, including using antimalware components and services for cloud services, virtual machines (VMs), and other systems.</span></span> <span data-ttu-id="ffd8f-154">Advanced Threat Analytics, die normale Verwendungsmuster für Netzwerke, Systeme und Benutzer überwacht und das maschinelle Lernen verwendet, um jedes Verhalten zu kennzeichnen, das außergewöhnlich ist, und regelmäßige Penetrationstests.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-154">Advanced Threat Analytics, which monitors normal usage patterns for networks, systems, and users, and employs machine learning to flag any behavior that is out of the ordinary, and regular penetration testing.</span></span>

<span data-ttu-id="ffd8f-155">Neben der Durchführung eigener Penetrationstests und der Bereitstellung von [Microsoft Cloud Unified Penetration-Testprogramm](https://technet.microsoft.com/mt784683)für unsere Kunden beschäftigen wir uns auch mit Sicherheitsexperten von Drittanbietern, die regelmäßige Schwachstellen Bewertungen und Penetrationstests für unsere Cloud-Dienste durchführen.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-155">In addition to performing our own penetration tests and offering to our customers a [Microsoft Cloud Unified Penetration Testing program](https://technet.microsoft.com/mt784683), we also engage with third-party security professionals who perform regular vulnerability assessments of and penetration testing against our cloud services.</span></span> <span data-ttu-id="ffd8f-156">Wir stellen die Berichte aus diesen Drittanbieter Bewertungen zur Verfügung, die von der [Dienst Vertrauensstellung](https://aka.ms/STP) und den [Dienst Sicherungs](https://aka.ms/ServiceAssurance) Portalen heruntergeladen werden können.</span><span class="sxs-lookup"><span data-stu-id="ffd8f-156">We make the reports from these third-party vulnerability assessments available for download from the [Service Trust](https://aka.ms/STP) and the [Service Assurance](https://aka.ms/ServiceAssurance) portals.</span></span>