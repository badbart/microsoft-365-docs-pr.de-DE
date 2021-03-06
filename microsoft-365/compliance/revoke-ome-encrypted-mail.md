---
title: Durch erweiterte Nachrichtenverschlüsselung verschlüsselte e-Mails widerrufen
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.date: 06/11/2020
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Als Administrator und als Absender der Nachricht können Sie bestimmte e-Mails widerrufen, die mit Office 365 erweiterten Nachrichtenverschlüsselung verschlüsselt wurden.
ms.openlocfilehash: 79ab3ef801d4d19317cbf1416d858de74d9f1393
ms.sourcegitcommit: 22dab0f7604cc057a062698005ff901d40771692
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "46868944"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Durch erweiterte Nachrichtenverschlüsselung verschlüsselte e-Mails widerrufen

Die e-Mail-Sperrung wird im Rahmen Office 365 erweiterten Nachrichtenverschlüsselung angeboten. Office 365 erweiterte Nachrichtenverschlüsselung ist in [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (Non-Profit-Mitarbeiter Preise), Office 365 Enterprise E5 (Nonprofit-Mitarbeiter Preise) und Office 365 Education A5 enthalten. Wenn Ihre Organisation über ein Abonnement verfügt, das Office 365 erweiterte Nachrichtenverschlüsselung nicht enthält, können Sie Sie mit dem Microsoft 365 E5 Compliance-SKU-Add-on für Microsoft 365 E3, Microsoft 365 E3 (Nonprofit Pricing) oder mit dem Office 365 Advanced Compliance SKU-Add-on für Microsoft 365 E3, Microsoft 365 E3 (Preise für gemeinnützige Mitarbeiter) oder Office 365-SKUs erwerben.

Dieser Artikel ist Teil einer größeren Reihe von Artikeln über [Office 365 Nachrichtenverschlüsselung](ome.md).

Wenn eine Nachricht mit Office 365 erweiterten Nachrichtenverschlüsselung verschlüsselt wurde und Sie ein Microsoft 365-Administrator sind oder Sie der Absender der Nachricht sind, können Sie die Nachricht unter bestimmten Bedingungen widerrufen. Administratoren widerrufen Nachrichten mithilfe von PowerShell. Als Absender widerrufen Sie eine Nachricht, die Sie direkt aus Outlook im Internet gesendet haben. In diesem Artikel werden die Umstände beschrieben, unter denen die Sperrung möglich ist, und wie dies geschieht.
  
## <a name="encrypted-emails-that-you-can-revoke"></a>Verschlüsselte e-Mails, die Sie widerrufen können

Administratoren und Nachrichtenabsender können verschlüsselte e-Mails widerrufen, wenn der Empfänger eine Linkbasierte, verschlüsselte e-Mail-Nachricht erhalten hat. Wenn der Empfänger eine systemeigene Inline Erfahrung in einem unterstützten Outlook-Client empfangen hat, können Sie die Nachricht nicht widerrufen.

Ob ein Empfänger eine Linkbasierte Erfahrung oder eine Inline-Erfahrung erhält, hängt vom Typ der Empfänger Identität ab: Office 365-und Microsoft-Konto Empfänger (beispielsweise Outlook.com-Benutzer) erhalten eine Inline-Erfahrung in unterstützten Outlook-Clients. Alle anderen Empfängertypen, wie etwa Gmail-und Yahoo-Empfänger, erhalten eine Linkbasierte Benutzeroberfläche.

Administratoren und Nachrichtenabsender können Nachrichten widerrufen, die mit der Verschlüsselung verschlüsselt werden, die direkt in Outlook im Internet angewendet wird. Beispielsweise werden Nachrichten mit der Option "nur verschlüsseln" verschlüsselt.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Screenshot mit der Option "nur verschlüsseln" in Outlook im Internet.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>Empfänger Erfahrung für gesperrte verschlüsselte e-Mails

Sobald eine e-Mail widerrufen wurde, erhält der Empfänger eine Fehlermeldung, wenn er über das Office 365 Nachrichten Verschlüsselungs Portal auf die verschlüsselte e-Mail zugreift: "die Nachricht wurde vom Absender widerrufen".

![Screenshot, der eine widerrufene verschlüsselte e-Mail zeigt.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Vorgehensweise widerrufen einer verschlüsselten Nachricht, die Sie gesendet haben

Zum Widerrufen einer verschlüsselten Nachricht, die Sie gesendet haben, führen Sie die folgenden Schritte aus:

1. Navigieren Sie in Outlook im Internet in Ihrem Ordner " **gesendet** " zu der Nachricht, die Sie widerrufen möchten.

   Wenn die e-Mail widerruflich ist, wird der Link "externen Zugriff entfernen" oben in der Nachricht angezeigt.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Screenshot mit verschlüsselten e-Mails, die Sie in Outlook im Internet widerrufen möchten.":::

2. Klicken Sie auf **externen Zugriff Entfernen** , um die Nachricht zu widerrufen.

   Die Meldung zeigt, dass der Status widerrufen wurde.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Screenshot mit Entsperrter verschlüsselter Nachricht in Outlook im Internet.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Vorgehensweise widerrufen einer verschlüsselten Nachricht als Administrator

Microsoft 365-Administratoren befolgen diese allgemeinen Schritte zum Widerrufen einer berechtigten verschlüsselten e-Mail:

- Rufen Sie die Nachrichten-ID der e-Mail ab.
- Stellen Sie sicher, dass Sie die Nachricht widerrufen können.
- Die e-Mail widerrufen.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Schritt 1: Abrufen der Nachrichten-ID der e-Mail

Bevor Sie eine verschlüsselte e-Mail widerrufen können, müssen Sie die Nachrichten-ID der e-Mail erfassen. Die MessageId weist normalerweise das folgende Format auf:

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

Es gibt mehrere Möglichkeiten, die Nachrichten-ID der e-Mail zu finden, die Sie widerrufen möchten. In diesem Abschnitt werden einige Optionen beschrieben, aber Sie können eine beliebige Methode verwenden, die die ID bereitstellt.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>So identifizieren Sie die Nachrichten-ID der e-Mail, die Sie mithilfe der Nachrichtenablaufverfolgung im Security &amp; Compliance Center widerrufen möchten

1. Suchen Sie nach der e-Mail nach Absender oder Empfänger mithilfe der [neuen Nachrichtenablaufverfolgung im Security & Compliance Center](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/).

2. Nachdem Sie die e-Mail-Adresse gefunden haben, wählen Sie Sie aus, um den Bereich **Nachrichtenablauf Verfolgungs Details** aufzurufen. Erweitern Sie **Weitere Informationen** , um nach der Nachrichten-ID zu suchen.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-office-message-encryption-reports-in-the-security-amp-compliance-center"></a>So identifizieren Sie die Nachrichten-ID der e-Mail, die Sie mithilfe von Office-Nachrichten Verschlüsselungs Berichten im Security Compliance Center widerrufen möchten &amp;

1. &amp;Navigieren Sie im Security Compliance Center zum **Nachrichten Verschlüsselungs Bericht**. Informationen zu diesem Bericht finden Sie unter [Anzeigen von e-Mail-Sicherheitsberichten im Security &amp; Compliance Center](../security/office-365-security/view-email-security-reports.md).

2. Wählen Sie die Tabelle **Details anzeigen** aus, und identifizieren Sie die Nachricht, die Sie widerrufen möchten.

3. Doppelklicken Sie auf die Nachricht, um Details anzuzeigen, die die Nachrichten-ID enthalten.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Schritt 2: Sicherstellen, dass die e-Mail widerruflich ist

Um zu überprüfen, ob Sie eine Nachricht widerrufen können, überprüfen Sie, ob das Feld Sperr Status im Verschlüsselungs Bericht in der Tabelle **Details** im Security &amp; Compliance Center angezeigt wird.

Führen Sie die folgenden Schritte aus, um zu überprüfen, ob Sie eine bestimmte e-Mail-Nachricht mithilfe von Windows PowerShell widerrufen können.

1. Verwenden Sie ein Arbeits-oder Schulkonto, das über globale Administratorberechtigungen in Ihrer Organisation verfügt, starten Sie eine Windows PowerShell Sitzung, und stellen Sie eine Verbindung mit Exchange Online her. Anleitungen finden Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://aka.ms/exopowershell).

2. Führen Sie das Cmdlet Get-OMEMessageStatus wie folgt aus:

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   Dieser Befehl gibt den Betreff der Nachricht zurück und gibt an, ob die Nachricht widerruflich ist. Beispiel:

     ```text
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Schritt 3: E-Mail widerrufen

Wenn Sie die Nachrichten-ID der zu widerrufenden e-Mail kennen und sichergestellt haben, dass die Nachricht widerruflich ist, können Sie die e-Mail mit dem Security &amp; Compliance Center oder Windows PowerShell widerrufen.

So widerrufen Sie die Nachricht mit dem Security &amp; Compliance Center

1. Stellen Sie mithilfe eines Arbeits-oder Schul Kontos, das über globale Administratorberechtigungen in Ihrer Organisation verfügt, eine Verbindung mit dem Security & Compliance Center her.

2. Wählen Sie im **Verschlüsselungs Bericht**in der Tabelle **Details** für die Nachricht die Option **Nachricht widerrufen**aus.

Verwenden Sie das Cmdlet "OMEMessageRevocation", um eine e-Mail mithilfe von Windows PowerShell zu widerrufen.

1. Wenn Sie ein Arbeits-oder Schulkonto mit globalen Administratorberechtigungen in Ihrer Organisation verwenden möchten, stellen Sie [eine Verbindung mit Exchange Online PowerShell her](https://aka.ms/exopowershell).

2. Führen Sie das Cmdlet "OMEMessageRevocation" wie folgt aus:

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. Um zu überprüfen, ob die e-Mail widerrufen wurde, führen Sie das Get-OMEMessageStatus-Cmdlet wie folgt aus:

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    Wenn die Sperrung erfolgreich war, gibt das Cmdlet das folgende Ergebnis zurück:  

     ```text
     Revoked: True
     ```

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Weitere Informationen zu Office 365 erweiterte Nachrichtenverschlüsselung

- [Erweiterte Office 365-Nachrichtenverschlüsselung](ome-advanced-message-encryption.md)

- [Office 365 erweiterte Nachrichtenverschlüsselung – e-Mail-Ablauf](ome-advanced-expiration.md)

- [Beschreibung des Nachrichtenrichtlinien-und Kompatibilitätsdiensts](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
