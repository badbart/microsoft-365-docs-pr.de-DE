---
title: Tabelle „DeviceTvmSoftwareInventoryVulnerabilities“ im Schema „Erweiterte Suche“
description: Erfahren Sie mehr über den Softwarebestand auf Ihren Geräten und deren Sicherheitsrisiken in der DeviceTvmSoftwareInventoryVulnerabilities-Tabelle des Schemas „Erweiterte Suche“.
keywords: erweiterte Suche, Suche nach Bedrohungen, Suche nach Cyberbedrohungen, Suche, Abfrage, Telemetrie, Schema, Referenz, Kusto, Tabelle, Spalte, Datentyp, Beschreibung, Bedrohungs- und Sicherheitsrisikoverwaltung, TVM, Geräteverwaltung, Software, Inventar, Sicherheitsrisiken, CVE ID, OS, DeviceTvmSoftwareInventoryVulnerabilities
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: f7c7ab393a956aa894a0ca8704ea0e99a82addc9
ms.sourcegitcommit: 0c9c28a87201c7470716216d99175356fb3d1a47
ms.translationtype: MT + HT Review
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "39911094"
---
# <a name="devicetvmsoftwareinventoryvulnerabilities"></a>DeviceTvmSoftwareInventoryVulnerabilities

**Gilt für:**
- Microsoft Threat Protection

[!include[Prerelease information](prerelease.md)]

Die `DeviceTvmSoftwareInventoryVulnerabilities` Tabelle im Schema „Erweiterte Suche“ enthält den Softwarebestand für die [Bedrohungs- und Sicherheitsrisikoverwaltung](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) auf Ihren Geräten sowie alle bekannten Sicherheitsrisiken in diesen Softwareprodukten. Diese Tabelle enthält außerdem Betriebssysteminformationen, CVE-IDs und Informationen zum Schweregrad des Sicherheitsrisikos. Verwenden Sie diese Referenz, um Abfragen zu erstellen, die Informationen aus der Tabelle zurückgeben.

Informationen zu anderen Tabellen im Schema „Erweiterte Suche“ finden Sie unter [Referenz zur erweiterten Suche](advanced-hunting-schema-tables.md).

| Spaltenname | Datentyp | Beschreibung |
|-------------|-----------|-------------|
| `MachineId` | string | Eindeutiger Bezeichner für den Computer im Dienst |
| `ComputerName` | string | Vollqualifizierter Domänenname (FQDN) des Computers |
| `OSPlatform` | string | Die Plattform des Betriebssystem, das auf dem Computer ausgeführt wird. Gibt spezifische Betriebssysteme an, einschließlich Variationen innerhalb der gleichen Familie, wie z. B. Windows 10 und Windows 7. |
| `OSVersion` | string | Die Version des Betriebssystem, das auf dem Computer ausgeführt wird. |
| `OSArchitecture` | string | Die Architektur des Betriebssystem, das auf dem Computer ausgeführt wird. |
| `SoftwareVendor` | string | Schweregrad des Sicherheitsrisikos, basierend auf CVSS-Bewertung und dynamischen Faktoren, die von der Bedrohungslandschaft beeinflusst werden |
| `SoftwareName` | string | Name des Softwareprodukts |
| `SoftwareVersion` | string | Versionsnummer des Softwareprodukts |
| `CveId` | string | Eindeutiger Bezeichner des Sicherheitsrisikos nach CVE (Common Vulnerabilities and Exposures) |
| `VulnerabilitySeverityLevel` | string | Schweregrad des Sicherheitsrisikos, basierend auf CVSS-Bewertung und dynamischen Faktoren, die von der Bedrohungslandschaft beeinflusst werden |



## <a name="related-topics"></a>Verwandte Themen

- [Vorbeugende Suche nach Bedrohungen](advanced-hunting-overview.md)
- [Lernen der Abfragesprache](advanced-hunting-query-language.md)
- [Verwenden freigegebener Abfragen](advanced-hunting-shared-queries.md)
- [Suche nach Bedrohungen auf Geräten und in E-Mails](advanced-hunting-query-emails-devices.md)
- [Grundlegendes zum Schema](advanced-hunting-schema-tables.md)
- [Anwenden bewährter Methoden für Abfragen](advanced-hunting-best-practices.md)
- [Übersicht über die Bedrohungs- und Sicherheitsrisikoverwaltung](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)