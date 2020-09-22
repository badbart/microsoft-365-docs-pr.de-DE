---
title: Erweiterte Jagd Grenzwerte im Microsoft Threat Protection
description: Verstehen verschiedener Diensteinschränkungen, die den erweiterten Jagd Dienst reaktionsfähig halten
keywords: Erweiterte Suche, Bedrohungs Suche, Cyber-Bedrohungs Suche, Microsoft Threat Protection, Microsoft 365, MTP, m365, Suche, Abfrage, Telemetrie, Schema, Kusto, CPU-Grenze, Abfrage Grenzwert, Ressourcen, maximale Ergebnisse
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: e3fbe29076d541df68dc39754960386fe935c7bc
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950949"
---
# <a name="advanced-hunting-service-limits"></a><span data-ttu-id="f1d0b-104">Grenzwerte für erweiterte Jagd Dienste</span><span class="sxs-lookup"><span data-stu-id="f1d0b-104">Advanced hunting service limits</span></span>

<span data-ttu-id="f1d0b-105">**Gilt für:**</span><span class="sxs-lookup"><span data-stu-id="f1d0b-105">**Applies to:**</span></span>
- <span data-ttu-id="f1d0b-106">Microsoft Threat Protection</span><span class="sxs-lookup"><span data-stu-id="f1d0b-106">Microsoft Threat Protection</span></span>

<span data-ttu-id="f1d0b-107">Um den Dienst leistungsfähig und reaktionsfähig zu halten, setzt Advanced Hunting verschiedene Grenzwerte für Abfragen, die manuell und nach [benutzerdefinierten Erkennungsregeln](custom-detection-rules.md)ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-107">To keep the service performant and responsive, advanced hunting sets various limits for queries run manually and by [custom detection rules](custom-detection-rules.md).</span></span> <span data-ttu-id="f1d0b-108">Lesen Sie die folgende Tabelle, um diese Grenzwerte zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-108">Refer to the following table to understand these limits.</span></span>

| <span data-ttu-id="f1d0b-109">Grenze</span><span class="sxs-lookup"><span data-stu-id="f1d0b-109">Limit</span></span> | <span data-ttu-id="f1d0b-110">Größe</span><span class="sxs-lookup"><span data-stu-id="f1d0b-110">Size</span></span> | <span data-ttu-id="f1d0b-111">Aktualisierungszyklus</span><span class="sxs-lookup"><span data-stu-id="f1d0b-111">Refresh cycle</span></span> | <span data-ttu-id="f1d0b-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f1d0b-112">Description</span></span> |
|--|--|--|--|
| <span data-ttu-id="f1d0b-113">Datenbereich</span><span class="sxs-lookup"><span data-stu-id="f1d0b-113">Data range</span></span> | <span data-ttu-id="f1d0b-114">30 Tage</span><span class="sxs-lookup"><span data-stu-id="f1d0b-114">30 days</span></span> | <span data-ttu-id="f1d0b-115">Jede Abfrage</span><span class="sxs-lookup"><span data-stu-id="f1d0b-115">Every query</span></span> | <span data-ttu-id="f1d0b-116">Jede Abfrage kann Daten von bis zu den letzten 30 Tagen nachschlagen.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-116">Each query can look up data from up to the past 30 days.</span></span> |
| <span data-ttu-id="f1d0b-117">Ergebnismenge</span><span class="sxs-lookup"><span data-stu-id="f1d0b-117">Result set</span></span> | <span data-ttu-id="f1d0b-118">10.000 Zeilen</span><span class="sxs-lookup"><span data-stu-id="f1d0b-118">10,000 rows</span></span> | <span data-ttu-id="f1d0b-119">Jede Abfrage</span><span class="sxs-lookup"><span data-stu-id="f1d0b-119">Every query</span></span> | <span data-ttu-id="f1d0b-120">Jede Abfrage kann bis zu 10.000 Datensätze zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-120">Each query can return up to 10,000 records.</span></span> |
| <span data-ttu-id="f1d0b-121">Timeout</span><span class="sxs-lookup"><span data-stu-id="f1d0b-121">Timeout</span></span> | <span data-ttu-id="f1d0b-122">10 Minuten</span><span class="sxs-lookup"><span data-stu-id="f1d0b-122">10 minutes</span></span> | <span data-ttu-id="f1d0b-123">Jede Abfrage</span><span class="sxs-lookup"><span data-stu-id="f1d0b-123">Every query</span></span> | <span data-ttu-id="f1d0b-124">Jede Abfrage kann bis zu 10 Minuten lang ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-124">Each query can run for up to 10 minutes.</span></span> <span data-ttu-id="f1d0b-125">Wenn der Dienst nicht innerhalb von 10 Minuten abgeschlossen ist, wird ein Fehler angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-125">If it does not complete within 10 minutes, the service displays an error.</span></span>
| <span data-ttu-id="f1d0b-126">CPU-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f1d0b-126">CPU resources</span></span> | <span data-ttu-id="f1d0b-127">Basierend auf der Mandanten Größe</span><span class="sxs-lookup"><span data-stu-id="f1d0b-127">Based on tenant size</span></span> | <span data-ttu-id="f1d0b-128">-Auf die Stunde und dann alle 15 Minuten</span><span class="sxs-lookup"><span data-stu-id="f1d0b-128">- On the hour and then every 15 minutes</span></span><br><span data-ttu-id="f1d0b-129">-Täglich um 12 Uhr</span><span class="sxs-lookup"><span data-stu-id="f1d0b-129">- Daily at 12 midnight</span></span> | <span data-ttu-id="f1d0b-130">Der Dienst erzwingt den täglichen und den 15-minütigen Grenzwert separat.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-130">The service enforces the daily and the 15-minute limit separately.</span></span> <span data-ttu-id="f1d0b-131">Für jeden Grenzwert zeigt das [Portal einen Fehler](advanced-hunting-errors.md) an, wenn eine Abfrage ausgeführt wird und der Mandant mehr als 10% der zugeordneten Ressourcen verbraucht hat.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-131">For each limit, the [portal displays an error](advanced-hunting-errors.md) whenever a query runs and the tenant has consumed over 10% of allocated resources.</span></span> <span data-ttu-id="f1d0b-132">Abfragen werden blockiert, wenn der Mandant 100% bis nach dem nächsten täglichen oder 15-minütigen Zyklus erreicht hat.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-132">Queries are blocked if the tenant has reached 100% until after the next daily or 15-minute cycle.</span></span> |

>[!NOTE] 
><span data-ttu-id="f1d0b-133">Eine separate Reihe von Grenzwerten gilt für erweiterte Suchabfragen, die über die API ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-133">A separate set of limits apply to advanced hunting queries performed through the API.</span></span> [<span data-ttu-id="f1d0b-134">Lesen Sie mehr über erweiterte Jagd-APIs</span><span class="sxs-lookup"><span data-stu-id="f1d0b-134">Read about advanced hunting APIs</span></span>](https://docs.microsoft.com/microsoft-365/security/mtp/api-advanced-hunting)

<span data-ttu-id="f1d0b-135">Kunden, die mehrere Abfragen regelmäßig ausführen, sollten den Verbrauch nachverfolgen und [bewährte Methoden für die Optimierung anwenden](advanced-hunting-best-practices.md) , um Unterbrechungen aufgrund der Überschreitung dieser Grenzwerte zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="f1d0b-135">Customers who run multiple queries regularly should track consumption and [apply optimization best practices](advanced-hunting-best-practices.md) to minimize disruption resulting from exceeding these limits.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f1d0b-136">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f1d0b-136">Related topics</span></span>

- [<span data-ttu-id="f1d0b-137">Bewährte Methoden für die erweiterte Suche</span><span class="sxs-lookup"><span data-stu-id="f1d0b-137">Advanced hunting best practices</span></span>](advanced-hunting-best-practices.md)
- [<span data-ttu-id="f1d0b-138">Behandeln von erweiterten Jagd Fehlern</span><span class="sxs-lookup"><span data-stu-id="f1d0b-138">Handle advanced hunting errors</span></span>](advanced-hunting-errors.md)
- [<span data-ttu-id="f1d0b-139">Übersicht über die erweiterte Suche</span><span class="sxs-lookup"><span data-stu-id="f1d0b-139">Advanced hunting overview</span></span>](advanced-hunting-overview.md)
- [<span data-ttu-id="f1d0b-140">Benutzerdefinierte Erkennungen – Übersicht</span><span class="sxs-lookup"><span data-stu-id="f1d0b-140">Custom detections overview</span></span>](custom-detections-overview.md)