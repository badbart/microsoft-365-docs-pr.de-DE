---
title: Grenzen im zentralen eDiscovery-Fall
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: In diesem Artikel werden die Grenzwerte im zentralen eDiscovery-Fall in Microsoft 365 beschrieben.
ms.openlocfilehash: 6224ce5ecb8fc0439e43ab5e1362f8a618194202
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358513"
---
# <a name="limits-in-core-ediscovery"></a>Grenzwerte in der zentralen eDiscovery

In der folgenden Tabelle sind die Grenzwerte für zentrale eDiscovery-Fälle und haltebereiche aufgelistet, die einem zentralen eDiscovery-Fall zugeordnet sind. Weitere Informationen zu Kern-eDiscovery finden Sie unter [Overview of Core eDiscovery](ediscovery-cases.md).
    
  |**Beschreibung der Beschränkung**|**Grenzwert**|
  |:-----|:-----|
  |Maximale Anzahl von Fällen für eine Organisation  <br/> |Keine Begrenzung  <br/> |
  |Maximale Anzahl von Fall Behältern für eine Organisation  <br/> |10.000  <br/> |
  |Maximale Anzahl von Postfächern in einem einzigen Aufbewahrungs Fall  <br/> |1,000  <br/> |
  |Maximale Anzahl von SharePoint-und OneDrive für Unternehmen-Websites in einem einzigen Aufbewahrungs Fall  <br/> |100  <br/> |
  |Die maximale Anzahl von Fällen, die auf der zentralen eDiscovery-Startseite angezeigt werden, und die maximale Anzahl von Elementen, die auf den Registerkarten Holds, suchen und Exportieren in einem Fall angezeigt werden. <sup>1</sup> |1,000|
  |||

   > [!NOTE]
   > <sup>1</sup> Wenn Sie eine Liste mit mehr als 1.000 Fällen, Aufbewahrungen, Suchvorgängen oder Exporten anzeigen möchten, können Sie das entsprechende PowerShell-Cmdlet Office 365 Security & Compliance verwenden:<br/> [Get-ComplianceCase](https://docs.microsoft.com/powershell/module/exchange/get-compliancecase) <br/> [Get-CaseHoldPolicy](https://docs.microsoft.com/powershell/module/exchange/get-caseholdpolicy)<br/> [Get-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearch)<br/> [Get-ComplianceSearchAction](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearchaction)
