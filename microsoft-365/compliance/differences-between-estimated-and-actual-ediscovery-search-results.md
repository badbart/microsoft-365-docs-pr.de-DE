---
title: Unterschiede zwischen geschätzten und tatsächlichen eDiscovery-Suchergebnissen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 8f20ca4f-a908-46ec-99e6-9890d269ecf2
description: Verstehen Sie, warum geschätzte und tatsächliche Suchergebnisse bei Suchvorgängen mit eDiscovery-Tools in Office 365 variieren können.
ms.openlocfilehash: 2c127077552b831d5bd890e03772b137338e1674
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2020
ms.locfileid: "47357645"
---
# <a name="differences-between-estimated-and-actual-ediscovery-search-results"></a>Unterschiede zwischen geschätzten und tatsächlichen eDiscovery-Suchergebnissen

Dieses Thema bezieht sich auf Suchvorgänge, die Sie mit einem der folgenden Microsoft eDiscovery-Tools ausführen können: 

- Inhaltssuche im Security & Compliance Center  <br/>  
- In-Place-eDiscovery im Exchange Admin Center (EAC)  <br/>  
- Das eDiscovery Center in SharePoint Online  <br/> 
   
Wenn Sie eine eDiscovery-Suche ausführen, gibt das Tool, das Sie verwenden, eine Schätzung der Anzahl von Elementen (und deren Gesamtgröße) zurück, die den Suchkriterien entsprechen. Wenn Sie beispielsweise eine Suche im Security & Compliance Center ausführen, werden die geschätzten Suchergebnisse im Detailbereich für die ausgewählte Suche angezeigt.
  
![Schätzung der Ergebnisse, die im Detailbereich der ausgewählten Suche angezeigt werden](../media/74e4ce83-40be-41a9-b60f-5ad447e79fe4.png)
  
Dies ist die gleiche Schätzung der Gesamtgröße und der Anzahl von Elementen, die im eDiscovery-Export Tool angezeigt wird, wenn Sie Ergebnisse auf einen lokalen Computer und im Export Zusammenfassungsbericht exportieren, der mit den Suchergebnissen heruntergeladen wird.
  
**Geschätzte Ergebnisse im eDiscovery-Export Tool**

![Geschätzte Ergebnisse im eDiscovery-Export Tool](../media/d34312a5-0ee6-49aa-9460-7ea0015a6e66.png)
  
**Geschätzte Ergebnisse im Export Zusammenfassungsbericht**

![Geschätzte Suchergebnisse sind im Export Zusammenfassungsbericht enthalten.](../media/44b579da-86c2-4f33-81b5-84d604003eda.png)
  
Wie Sie jedoch im vorherigen Screenshot des Export Zusammenfassungsberichts bemerken, unterscheiden sich die Größe und Anzahl der tatsächlichen Suchergebnisse, die heruntergeladen werden, von der Größe und Anzahl der geschätzten Suchergebnisse.
  
![Unterschied zwischen geschätzten und heruntergeladenen Suchergebnissen](../media/84aef318-230f-430d-9d9e-02f21342d364.png)
  
Hier sind einige Gründe für diese Unterschiede:
  
- **Die Art und Weise, wie Ergebnisse geschätzt werden**. Eine Schätzung der Suchergebnisse ist lediglich eine Schätzung (und keine tatsächliche Anzahl) der Elemente, die den Suchabfrage Kriterien entsprechen. Um die Schätzung von Exchange-Elementen zu kompilieren, wird eine Liste der Nachrichten-IDs, die die Suchkriterien erfüllen, von der Exchange-Datenbank nach dem von Ihnen verwendeten eDiscovery-Tool angefordert. Wenn Sie die Suchergebnisse exportieren, wird die Suche jedoch erneut ausgeführt, und die tatsächlichen Nachrichten werden aus der Exchange-Datenbank abgerufen. Diese Unterschiede können daher dadurch entstehen, dass die geschätzte Anzahl von Elementen und die tatsächliche Anzahl von Elementen bestimmt werden.

- **Änderungen, die zwischen dem Zeitpunkt der Schätzung und dem Export von Suchergebnissen auftreten**. Wenn Sie Suchergebnisse exportieren, wird die Suche neu gestartet, um die letzten Elemente im Suchindex zu erfassen, die den Suchkriterien entsprechen. Es ist möglich, dass zusätzliche Elemente erstellt, gesendet oder empfangen wurden, die die Suchkriterien in dem Zeitraum erfüllen, in dem die geschätzten Suchergebnisse gesammelt wurden und die Suchergebnisse exportiert wurden. Es ist auch möglich, dass Elemente, die sich im Suchindex befanden, als die Suchergebnisse geschätzt wurden, nicht mehr vorhanden sind, da Sie vom Inhaltsspeicherort gelöscht wurden, bevor die Suchergebnisse exportiert wurden. Eine Möglichkeit zur Minderung dieses Problems besteht darin, einen Datumsbereich für eine eDiscovery-Suche anzugeben. Eine andere Möglichkeit besteht darin, inhaltsspeicherorte so einzuhalten, dass Elemente beibehalten werden und nicht gelöscht werden können. 

   Obwohl selten, selbst im Fall, wenn ein Haltebereich angewendet wird, kann die Wartung von integrierten Kalenderelementen (die nicht vom Benutzer bearbeitet werden, aber in vielen Suchergebnissen enthalten sind) möglicherweise von Zeit zu Zeit entfernt werden. Durch diese regelmäßige Entfernung von Kalenderelementen werden weniger Elemente exportiert.

- Nicht **indizierte Elemente**. Elemente, die für die Suche nicht indiziert sind, können Unterschiede zwischen geschätzten und tatsächlichen Suchergebnissen verursachen. Beispielsweise enthalten Compliance-eDiscovery in Exchange und das eDiscovery Center in SharePoint keine nicht indizierten Elemente (die die Suchkriterien nicht erfüllen), wenn Sie eine Suche ausführen, um die Suchergebnisse abzuschätzen. Sie können aber auch nicht indizierte Elemente einschließen, wenn Sie die Suchergebnisse exportieren. Wenn Sie nicht indizierte Elemente beim Exportieren von Suchergebnissen einbeziehen, werden möglicherweise weitere Elemente exportiert. Dies führt zu einem Unterschied zwischen den geschätzten und den exportierten Suchergebnissen.

    Wenn Sie das Tool für die Inhaltssuche im Security & Compliance Center verwenden, haben Sie die Möglichkeit, nicht indizierte Elemente in die Such Schätzung einzubeziehen. Die Anzahl der nicht indizierten Elemente, die von der Suche zurückgegeben werden, wird im Detailbereich zusammen mit den anderen geschätzten Suchergebnissen aufgeführt. Alle nicht indizierten Elemente wären auch in der Gesamtgröße der geschätzten Suchergebnisse enthalten. Wenn Sie Suchergebnisse exportieren, haben Sie die Möglichkeit, nicht indizierte Elemente einzubeziehen oder nicht einzubeziehen. Die Art und Weise, wie Sie diese Optionen konfigurieren, kann zu Unterschieden zwischen den geschätzten und den tatsächlichen Suchergebnissen führen, die heruntergeladen werden.

- **Exportieren der Ergebnisse einer Inhaltssuche, die alle inhaltsspeicherorte enthält**. Wenn es sich bei der Suche, aus der Sie Ergebnisse exportieren, um die Suche aller inhaltsspeicherorte in Ihrer Organisation handelt, werden nur die nicht indizierten Elemente aus Inhaltsspeicherorten exportiert, die Elemente enthalten, die mit den Suchkriterien übereinstimmen. In other words, if no search results are found in a mailbox or site, then any unindexed items in that mailbox or site won't be exported. Nicht indizierte Elemente aller inhaltsspeicherorte (auch solche, die keine Elemente enthalten, die mit der Suchabfrage übereinstimmen) werden in die geschätzten Suchergebnisse aufgenommen.

    Wenn die Suche, die Sie exportieren, aus bestimmten Inhaltsspeicherorten stammt, werden auch nicht indizierte Elemente (die nicht von den Suchkriterien ausgeschlossen werden) aus allen in der Suche angegebenen Inhaltsspeicherorten exportiert. In diesem Fall sollte die geschätzte Anzahl nicht indexierter Elemente und die Anzahl der exportierten nicht indizierten Elemente identisch sein.

    Der Grund für das nicht exportieren von nicht indizierten Elementen von allen Standorten in der Organisation liegt darin, dass es möglicherweise die Wahrscheinlichkeit von Exportfehlern erhöht und die Zeit für das Exportieren und Herunterladen der Suchergebnisse erhöht.

- **RAW-Dateiformate im Vergleich zu exportierten Dateiformaten**. Für Exchange-Elemente wird die geschätzte Größe der Suchergebnisse mithilfe der rohen Exchange-Nachrichtengrößen berechnet. E-Mail-Nachrichten werden jedoch in einer PST-Datei oder als einzelne Nachrichten (die als EML-Dateien formatiert sind) exportiert. Beide Exportoptionen verwenden ein anderes Dateiformat als rohe Exchange-Nachrichten, was dazu führt, dass die Gesamtgröße der exportierten Datei von der geschätzten Dateigröße abweicht.

- **Dokumentversionen**. Für SharePoint-Dokumente sind mehrere Versionen eines Dokuments nicht in den geschätzten Suchergebnissen enthalten. Sie haben jedoch die Möglichkeit, beim Exportieren der Suchergebnisse alle Dokumentversionen einzubeziehen, wodurch die tatsächliche Zahl (und Gesamtgröße) der exportierten Dokumente erhöht wird. 

- **Datendeduplizierung.** Bei Exchange-Elementen reduziert die Deduplizierung die Anzahl der exportierten Elemente. Sie haben die Möglichkeit, die Suchergebnisse beim Exportieren zu deduplizieren. Bei Exchange-Nachrichten bedeutet dies, dass nur eine einzige Instanz einer Nachricht exportiert wird, obwohl diese Nachricht in mehreren Postfächern gefunden werden kann. Die geschätzten Suchergebnisse enthalten jede Instanz einer Nachricht. Wenn Sie also die Option "Deduplizierung" beim Exportieren von Suchergebnissen auswählen, ist die tatsächliche Anzahl der exportierten Elemente möglicherweise erheblich kleiner als die geschätzte Anzahl von Elementen.

    Beachten Sie beim Auswählen der Option für die Deduplizierung, dass alle Exchange-Elemente in einer einzigen PST-Datei exportiert werden und die Ordnerstruktur aus den Quellpostfächern nicht beibehalten wird. Die exportierte PST-Datei enthält nur die e-Mail-Elemente. Ein Suchergebnisbericht enthält jedoch einen Eintrag für jede exportierte Nachricht, die das Quellpostfach identifiziert, in dem sich die Nachricht befindet. Auf diese Weise können Sie alle Postfächer identifizieren, die eine doppelte Nachricht enthalten. Wenn Sie Deduplizierung nicht aktivieren, wird für jedes durchsuchte Postfach eine separate PST-Datei exportiert. 

## <a name="exporting-unindexed-items-from-the-ediscovery-center-in-sharepoint-online"></a>Exportieren von nicht indizierten Elementen aus dem eDiscovery Center in SharePoint Online

Im eDiscovery Center in SharePoint Online haben Sie die Möglichkeit, nicht indizierte Inhalte (aus Exchange und SharePoint) einzubeziehen, wenn Sie die Ergebnisse einer eDiscovery-Suche exportieren. Hierzu müssen Sie die Option **Elemente einschließen, die verschlüsselt sind oder eine nicht erkannte Formatierung aufweisen** auswählen. Nicht indizierte Elemente (auch als nicht crawlbar in SharePoint bezeichnet) sind Elemente in Exchange und SharePoint, die aus irgendeinem Grund nicht für die Suche indiziert wurden. Nicht indizierte Exchange-Elemente werden im Exchange- **Indexfehler** Bericht aufgeführt, der beim Exportieren von Suchergebnissen enthalten ist. Ebenso werden nicht indexierte SharePoint-Elemente in **SharePoint-Indexfehler** Bericht aufgeführt. Wenn Sie nicht indizierte Elemente exportieren, werden Sie in einen Ordner mit dem Namen "nicht **gecrawlt**" heruntergeladen. Nicht indizierte Exchange-Elemente sind in einer PST-Datei enthalten; jedes nicht indizierte Dokument aus SharePoint wird ebenfalls heruntergeladen. Die Anzahl der nicht indizierten Elemente (sofern vorhanden) wird in jedem Indexfehler Bericht aufgeführt. Die Anzahl der nicht indizierten Elemente in den Berichten sollte mit der Anzahl der nicht indizierten Elemente übereinstimmen, die heruntergeladen werden.
  
 **Was sind einige Gründe, wenn die Anzahl der exportierten nicht indizierten Elemente nicht mit der Anzahl der Elemente im Indexfehler Bericht übereinstimmt?** Wie bereits erläutert, ist es möglich, dass Elemente zwischen dem Zeitpunkt, an dem die Such Schätzung ausgeführt wurde, und der Zeit, zu der die Suchergebnisse exportiert wurden, von Microsoft 365 gelöscht wurden. Bei nicht indizierten Elementen kann eine ähnliche Diskrepanz auftreten. Beispielsweise kann der Suchindex beim Exportieren des Suchergebnisses veraltet sein. Dies würde bedeuten, dass ein nicht indiziertes Element, das mit den Suchergebnissen exportiert wurde, möglicherweise nicht im Indexfehler Bericht aufgeführt wird, da das Element zum Zeitpunkt der Suchergebnisse nicht indiziert wurde. Dies würde dazu führen, dass mehr nicht indizierte Elemente exportiert werden, als im Indexfehler Bericht aufgeführt werden. Dementsprechend könnte ein nicht indiziertes Element, das im Indexfehler Bericht aufgeführt ist, aus Microsoft 365 gelöscht worden sein, bevor der Suchindex aktualisiert wurde. Dies führt dazu, dass weniger exportierte nicht indizierte Elemente als im Indexfehler Bericht aufgeführt werden.
  
> [!NOTE]
> Wenn Sie beim Exportieren von Suchergebnissen oder einfach nur zum Herunterladen der Berichte die Option **Elemente einschließen, die verschlüsselt sind oder nicht erkannt** sind, nicht auswählen, werden die Indexfehler Berichte heruntergeladen, aber keine Einträge. Dies bedeutet nicht, dass keine Indizierungsfehler vorliegen. Dies bedeutet nur, dass nicht indizierte Elemente nicht in den Export eingeschlossen wurden. 
