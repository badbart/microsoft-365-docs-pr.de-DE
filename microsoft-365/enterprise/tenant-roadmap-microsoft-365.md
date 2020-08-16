---
title: Mandanten-Roadmap für Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-subscription-management
ms.custom: it-pro
description: Die Roadmap zum Einrichten Ihrer Mandanten für Microsoft 365.
ms.openlocfilehash: db7054d1f6afc7e4835507dc6415e0b240918c1f
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690839"
---
# <a name="tenant-roadmap-for-microsoft-365"></a><span data-ttu-id="742c2-103">Mandanten-Roadmap für Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="742c2-103">Tenant roadmap for Microsoft 365</span></span>

<span data-ttu-id="742c2-104">Ihr Microsoft 365-Mandant ist die Gruppe von Diensten, die Ihrer Organisation zugewiesen sind.</span><span class="sxs-lookup"><span data-stu-id="742c2-104">Your Microsoft 365 tenant is the set of services assigned to your organization.</span></span> <span data-ttu-id="742c2-105">Dieser Mandant ist normalerweise mit einem oder mehreren Ihrer DNS-Domänennamen verknüpft und fungiert als zentraler Container für unterschiedliche Abonnements und die Lizenzen, die Sie Benutzerkonten zuweisen.</span><span class="sxs-lookup"><span data-stu-id="742c2-105">This tenant is typically associated with one or more of your DNS domain names and acts as a central container for different subscriptions and the licenses within them that you assign to user accounts.</span></span> 

<span data-ttu-id="742c2-106">Wenn Sie einen Microsoft 365-Mandanten erstellen, weisen Sie ihn einem bestimmten geografischen Standort zu.</span><span class="sxs-lookup"><span data-stu-id="742c2-106">When you create a Microsoft 365 tenant, you assign it to a specific geographical location.</span></span> <span data-ttu-id="742c2-107">Sie können auch einen Mandanten mit mehreren geografischen Standorten haben und den Mandanten von einem Standort an einen anderen Speicherort verlagern.</span><span class="sxs-lookup"><span data-stu-id="742c2-107">You can also have a tenant with multiple geographical locations and move your tenant from one location to another.</span></span>

<span data-ttu-id="742c2-108">Eine gut geplante und ausgeführte Mandanten Konfiguration ist für die Vorbereitung auf die grundlegenden Dienste von Netzwerk und Identität entscheidend.</span><span class="sxs-lookup"><span data-stu-id="742c2-108">A well-planned and executed tenant configuration is critical to getting it ready for the foundational services of networking and identity.</span></span>

## <a name="plan"></a><span data-ttu-id="742c2-109">Plan</span><span class="sxs-lookup"><span data-stu-id="742c2-109">Plan</span></span>

<span data-ttu-id="742c2-110">In der Planungsphase Ihrer Mandanten Implementierung:</span><span class="sxs-lookup"><span data-stu-id="742c2-110">In the planning phase of your tenant implementation:</span></span>

- [<span data-ttu-id="742c2-111">Grundlegendes zu Abonnements, Lizenzen und Azure Active Directory (Azure AD)-Mandanten</span><span class="sxs-lookup"><span data-stu-id="742c2-111">Understand subscriptions, licenses, and Azure Active Directory (Azure AD) tenants</span></span>](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [<span data-ttu-id="742c2-112">Grundlegendes zur Verwendung von Drittanbieter-SSL-Zertifikaten</span><span class="sxs-lookup"><span data-stu-id="742c2-112">Understand how to use third-party SSL certificates</span></span>](plan-for-third-party-ssl-certificates.md)
- [<span data-ttu-id="742c2-113">Access-Setup Handbücher im Microsoft 365 Admin Center</span><span class="sxs-lookup"><span data-stu-id="742c2-113">Access setup guides in the Microsoft 365 admin center</span></span>](setup-guides-for-microsoft-365.md)
- [<span data-ttu-id="742c2-114">Grundlegendes zu den Möglichkeiten, mit denen ein Microsoft 365-Mandant in Azure AD Dienste integriert ist</span><span class="sxs-lookup"><span data-stu-id="742c2-114">Understand the ways a Microsoft 365 tenant is integrated with Azure AD services</span></span>](integrated-apps-and-azure-ads.md)
- [<span data-ttu-id="742c2-115">Planen der Client-App-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="742c2-115">Plan for client app support</span></span>](microsoft-365-client-support-certificate-based-authentication.md)
- [<span data-ttu-id="742c2-116">Bestimmen der Verwendung der modernen Hybrid Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="742c2-116">Determine how to use hybrid modern authentication</span></span>](hybrid-modern-auth-overview.md)
- [<span data-ttu-id="742c2-117">Planen von Office 2007-und Office 2010 Upgrades</span><span class="sxs-lookup"><span data-stu-id="742c2-117">Plan for Office 2007 and Office 2010 upgrades</span></span>](plan-upgrade-previous-versions-office.md)
- [<span data-ttu-id="742c2-118">Grundlegendes zur Mandanten Isolierung</span><span class="sxs-lookup"><span data-stu-id="742c2-118">Understand tenant isolation</span></span>](microsoft-365-tenant-isolation-overview.md)
- [<span data-ttu-id="742c2-119">Abrufen der Details zu Microsoft 365 Service Assurance</span><span class="sxs-lookup"><span data-stu-id="742c2-119">Get the details on Microsoft 365 service assurance</span></span>](https://docs.microsoft.com/microsoft-365/compliance/service-assurance)

## <a name="deploy"></a><span data-ttu-id="742c2-120">Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="742c2-120">Deploy</span></span>

<span data-ttu-id="742c2-121">Fügen Sie in der Bereitstellungsphase Ihrer Mandanten Implementierung [die DNS-Domänen](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain) für Ihre Organisation hinzu.</span><span class="sxs-lookup"><span data-stu-id="742c2-121">In the deployment phase of your tenant implementation, [add the DNS domains](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain) for your organization.</span></span>

## <a name="tenants-with-multiple-geographic-locations"></a><span data-ttu-id="742c2-122">Mandanten mit mehreren geografischen Standorten</span><span class="sxs-lookup"><span data-stu-id="742c2-122">Tenants with multiple geographic locations</span></span>

<span data-ttu-id="742c2-123">Mit Microsoft 365 Multi-Geo kann Ihr Unternehmen seine Microsoft 365-Präsenz auf mehrere geografische Regionen und/oder Länder innerhalb des vorhandenen Mandanten erweitern.</span><span class="sxs-lookup"><span data-stu-id="742c2-123">With Microsoft 365 Multi-Geo, your organization can expand its Microsoft 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span>

<span data-ttu-id="742c2-124">[Beginnen Sie](microsoft-365-multi-geo.md) mit dem Verständnis, der Planung, der Konfiguration und der Verwaltung von Microsoft 365 Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="742c2-124">[Get started](microsoft-365-multi-geo.md) in understanding, planning, configuring, and then administering with Microsoft 365 Multi-Geo.</span></span>

## <a name="moving-a-tenants-geographic-locations"></a><span data-ttu-id="742c2-125">Verschieben der geografischen Standorte eines Mandanten</span><span class="sxs-lookup"><span data-stu-id="742c2-125">Moving a tenant's geographic locations</span></span>

<span data-ttu-id="742c2-126">Microsoft öffnet weiterhin die neuen geografischen Standorte für das Rechenzentrum (GEOS) für Microsoft 365-Dienste.</span><span class="sxs-lookup"><span data-stu-id="742c2-126">Microsoft continues to open new datacenter geographic locations (geos) for Microsoft 365 services.</span></span> <span data-ttu-id="742c2-127">In diesem neuen Datencenter-GEOS wird Kapazität hinzugefügt und Ressourcen zur Unterstützung von Kundenanforderungen und Nutzungs Wachstum berechnet.</span><span class="sxs-lookup"><span data-stu-id="742c2-127">These new datacenter geos add capacity and compute resources to support customer demand and usage growth.</span></span> <span data-ttu-id="742c2-128">Darüber hinaus bieten die neuen Rechenzentrumsregionen die Aufbewahrung von Kundenkerndaten innerhalb der Geografie.</span><span class="sxs-lookup"><span data-stu-id="742c2-128">Additionally, the new datacenter geos offer in-geo data residency for core customer data.</span></span>

<span data-ttu-id="742c2-129">Beginnen Sie mit dem Verständnis und der Anforderung einer Geo-Datenverschiebung mit [Verschiebung der Kern Daten in das neue Microsoft 365 Datacenter Geo](moving-data-to-new-datacenter-geos.md).</span><span class="sxs-lookup"><span data-stu-id="742c2-129">Get started in understanding and requesting a geo data move with [Moving core data to new Microsoft 365 datacenter geo](moving-data-to-new-datacenter-geos.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="742c2-130">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="742c2-130">Next step</span></span>

<span data-ttu-id="742c2-131">Starten Sie Ihre Mandanten Planung mit [Abonnements, Lizenzen, Konten und Mandanten](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span><span class="sxs-lookup"><span data-stu-id="742c2-131">Start your tenant planning with [Subscriptions, licenses, accounts, and tenants](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
