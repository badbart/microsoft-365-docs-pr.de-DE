---
title: Aktivieren oder Deaktivieren von integrierten Apps
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7e453a40-66df-44ab-92a1-96786cb7fb34
description: Erfahren Sie mehr über integrierte apps und wie Sie Sie aktivieren können, um Drittanbieter-apps den Zugriff auf die Office 365 Informationen von Benutzern zu ermöglichen.
ms.openlocfilehash: 932a99ec2c65b14e903ccffb86d291dac20ddfcf
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2020
ms.locfileid: "42244095"
---
# <a name="turning-integrated-apps-on-or-off"></a>Aktivieren oder Deaktivieren von integrierten Apps

[] Wenn integrierte Apps aktiviert sind, können Benutzer in Ihrer Organisation Apps von Drittanbietern den Zugriff auf ihre Office 365-Informationen gestatten. Wenn beispielsweise jemand eine App eines Drittanbieters verwendet, könnte diese App Berechtigungen für den Zugriff auf den Kalender des Benutzers anfordern sowie zum Bearbeiten von Dateien, die sich in einem OneDrive-Ordner befinden.

## <a name="turning-integrated-apps-on-or-off"></a>Aktivieren oder Deaktivieren von integrierten Apps
<a name="__toc379982114"> </a>

Wie folgt aktivieren oder deaktivieren Sie integrierte Apps.

1. Wechseln Sie im Admin Center zur Seite **Einstellungen** \> [-Dienst &amp; -Add-ins](https://go.microsoft.com/fwlink/p/?linkid=2053743) , und wählen Sie dann **integrierte apps**aus.

2. Wählen Sie auf der Seite **integrierte apps** die Option zum Aktivieren oder deaktivieren integrierter Apps aus.

## <a name="more-info-on-integrated-apps"></a>Weitere Informationen zu integrierten Apps
<a name="__toc379982114"> </a>

Eine integrierte App kann innerhalb Ihrer eigenen Organisation erstellt werden oder aus einer anderen Office 365-Organisation oder von einem Drittanbieter stammen.

Wenn integrierte Apps aktiviert sind und eine App verwendet wird, fordert die App die Berechtigung an, die Zugriffsebene so festlegen zu dürfen, wie sie beim Zugriff auf die Informationen des Benutzers erforderlich sind. Ein Benutzer kann nur Apps, deren Besitzer er ist, Zugriff auf seine Office 365-Informationen gewähren. Sie können einer App keinen Zugriff auf die Informationen anderer Benutzer gewähren.

Es gibt zwei Arten von Berechtigungen, die bei der Verwendung integrierter Apps in Office 365 verwendet werden: Benutzerberechtigungen und Administratorberechtigungen. Wenn Ihre Organisation beispielsweise für integrierte Apps aktiviert ist und ein Benutzer eine App eines Drittanbieters verwendet, könnte die App vom Benutzer die Berechtigung zum Lesen seiner Benutzerprofildetails, zum Bearbeiten oder Löschen seiner Dateien, zum Lesen von in Websitesammlungen enthaltenen Elementen und zum Senden von E-Mail im Namen dieses Benutzers fordern.

![Benutzerberechtigungen für integrierte Apps](../media/bb9a6cf8-da39-4ac0-9e40-cde03a81c121.gif)

Wenn ein Administrator eine APP für alle Benutzer in einer Organisation registriert, wird er aufgefordert, diese APP auf Informationen und Ressourcen in der Organisation zugreifen zu lassen. Danach werden andere Benutzer in der Organisation, wenn sie diese App benutzen, nicht mehr um Berechtigungen gebeten. Wenn ein Administrator eine App registriert, muss dieser Administrator sicherstellen, dass der Herausgeber dieser App vertrauenswürdig ist. Details zum Registrieren einer App finden Sie unter [Hinzufügen, Aktualisieren und Entfernen einer Anwendung](https://go.microsoft.com/fwlink/p/?LinkID=518600).

![Administratorberechtigungen für integrierte Apps](../media/e24aa504-bf10-446c-a9d5-45a6f2655187.gif)

Wenn integrierte Apps deaktiviert sind, werden Apps, die bereits installiert sind und Berechtigungen für den Zugriff auf Informationen nicht deinstalliert, und die Berechtigungen werden auch nicht entfernt. Selbst wenn integrierte Apps deaktiviert sind, können Administratoren immer noch Apps registrieren, um sie für ihre Benutzer verfügbar zu machen und diesen Apps zu gestatten, auf die Informationen der Benutzer zuzugreifen. Details zum Entfernen einer registrierten App mit ihren Berechtigungen finden Sie unter [Hinzufügen, Aktualisieren und Entfernen einer Anwendung](https://go.microsoft.com/fwlink/?LinkID=518600&amp;clcid=0x409).

