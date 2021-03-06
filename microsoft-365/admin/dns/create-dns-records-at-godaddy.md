---
title: Erstellen von DNS-Einträgen bei GoDaddy für Microsoft
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: Erfahren Sie, wie Sie Ihre Domäne überprüfen und DNS-Einträge für e-Mail, Skype for Business Online und andere Dienste bei GoDaddy für Microsoft einrichten.
ms.openlocfilehash: 95bc9e1ca522796111bbf5146c93686bbbac1a3d
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "44400461"
---
# <a name="create-dns-records-at-godaddy-for-microsoft"></a>Erstellen von DNS-Einträgen bei GoDaddy für Microsoft

 **[Überprüfen Sie die häufig gestellten Fragen (FAQ) zu Domänen](../setup/domains-faq.md)**, wenn Sie nicht finden, wonach Sie suchen.

Wenn GoDaddy Ihr DNS-Hostinganbieter ist, führen Sie die in diesem Artikel aufgeführten Schritte aus, um Ihre Domäne zu überprüfen und DNS-Einträge für E-Mail, Skype for Business Online und andere Dienste einzurichten.

Nachdem Sie diese Einträge bei GoDaddy hinzugefügt haben, ist Ihre Domäne für die Verwendung mit Microsoft-Diensten eingerichtet.

> [!NOTE]
> Normalerweise dauert es ungefähr 15 Minuten, bis DNS-Änderungen wirksam werden. Es kann jedoch gelegentlich länger dauern, bis eine von Ihnen vorgenommene Änderung im Internet im DNS-System aktualisiert wurde. Wenn nach dem Hinzufügen von DNS-Einträgen Probleme mit dem E-Mail-Fluss oder andere Probleme auftreten, lesen Sie [Behandeln von Problemen nach Änderung des Domänennamens oder von DNS-Einträgen](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Hinzufügen eines TXT-Eintrags zur Überprüfung
<a name="BKMK_verify"> </a>

Bevor Sie Ihre Domäne mit Microsoft verwenden können, müssen wir uns vergewissern, dass Sie deren Besitzer sind. Ihre Fähigkeit, sich bei Ihrem Konto bei Ihrer Domänenregistrierungsstelle anzumelden und den DNS-Eintrag zu erstellen, ist für Microsoft der Nachweis, dass Sie der Besitzer der Domäne sind.

> [!NOTE]
> Dieser Eintrag wird nur verwendet, um zu überprüfen, ob Sie der Besitzer Ihrer Domäne sind. Er hat keine weiteren Auswirkungen. Sie können ihn später ggf. löschen.

Führen Sie die folgenden Schritte aus.

1. Um zu beginnen, navigieren Sie über [diesen Link](https://account.godaddy.com/products/?go_redirect=disabled) zu Ihrer Domänenseite bei GoDaddy. Sie werden aufgefordert, sich anzumelden.

    ![GoDaddy-BP-configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Wählen Sie unter **Domänen**die Option DNS unter der Domäne aus, die Sie bearbeiten möchten.

    ![GoDaddy-BP-configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Klicken Sie auf **Hinzufügen**.

    ![GoDaddy-BP-configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. Wählen Sie in der Dropdownliste **TXT (Text)** aus. Geben Sie in den Feldern für den neuen Eintrag die Werte aus der folgenden Tabelle ein. Sie können die Werte auch kopieren und einfügen.

    |**Record type** |**Host**|**TXT VALUE**|**TTL** |
    |:-----|:-----|:-----|:-----|
    |TXT (Text)|@|MS=ms *XXXXXXXX*<br>**Hinweis:** Dies ist ein nur Beispiel. Verwenden Sie hier Ihre spezifischen **Ziel-oder Punkt-zu-Adresse** -Werte aus der Tabelle. [Wie finde ich diese Angabe?](../get-help-with-domains/information-for-dns-records.md)|1 hour  <br>(Wählen Sie in der Dropdownliste einen Wert aus.)|

      ![GoDaddy-BP-Verify-1-0](../../media/dns/56526870-d6465780-651a-11e9-9cf0-d6fff71e2f62.png)

5. Wählen Sie **Speichern**.

6. Warten Sie einige Minuten, bevor Sie fortfahren, damit der soeben erstellte Eintrag im Internet aktualisiert werden kann.

Nachdem Sie den Eintrag auf der Website Ihrer Domänenregistrierungsstelle hinzugefügt haben, kehren Sie zu Microsoft zurück und fordern Sie den Eintrag an.

Wenn Microsoft den richtigen TXT-Eintrag findet, ist die Domäne überprüft.
  
1. Wechseln Sie im Microsoft Admin Center zur Seite **Einstellungen** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domänen</a>.

    
2. Wählen Sie auf der Seite **Domänen** die zu überprüfende Domäne aus. 
    
    
  
3. Wählen Sie auf der Seite **Setup** die Option **Setup starten** aus.



4. Wählen Sie auf der Seite **Domäne überprüfen** die Option **Überprüfen** aus.



> [!NOTE]
>  Normalerweise dauert es ungefähr 15 Minuten, bis DNS-Änderungen wirksam werden. Es kann jedoch gelegentlich länger dauern, bis eine von Ihnen vorgenommene Änderung im Internet im DNS-System aktualisiert wurde. Wenn nach dem Hinzufügen von DNS-Einträgen Probleme mit dem E-Mail-Fluss oder andere Probleme auftreten, lesen Sie [Behandeln von Problemen nach Änderung des Domänennamens oder von DNS-Einträgen](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Fügen Sie einen MX-Eintrag hinzu, damit E-Mails für Ihre Domäne an Microsoft geleitet werden.
<a name="BKMK_add_MX"> </a>

Führen Sie die folgenden Schritte aus.

1. Um zu beginnen, navigieren Sie über [diesen Link](https://account.godaddy.com/products/?go_redirect=disabled) zu Ihrer Domänenseite bei GoDaddy. Sie werden aufgefordert, sich anzumelden.

    ![GoDaddy-BP-configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Wählen Sie unter **Domänen**die Option DNS unter der Domäne aus, die Sie bearbeiten möchten.

    ![GoDaddy-BP-configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Klicken Sie auf **Hinzufügen**.

    ![GoDaddy-BP-configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. Wählen Sie in der Dropdownliste **MX (Mail Exchanger)** aus.

    ![GoDaddy-BP-configure-2-0](../../media/dns/56528642-85842e00-651d-11e9-8dd8-217f468f9a18.png)

5. Geben Sie in den Feldern für den neuen Eintrag die Werte aus der folgenden Tabelle ein. Sie können die Werte auch kopieren und einfügen.

    (Wählen Sie in der Dropdownliste den Wert **TTL** aus.)

    |**Record type**|**Host**|**Points to**|**Priorität**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX (Mail Exchanger)  <br/> |@  <br/> | *\<domain-key\>*. Mail.Protection.Outlook.com  <br/> **Hinweis:** Holen Sie sich Ihr *\<domain-key\>* Microsoft-Konto.           [Wie finde ich diese Angabe?](../get-help-with-domains/information-for-dns-records.md)          |10    <br/> Weitere Informationen zur Priorität finden Sie unter [Was ist MX-Priorität?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) <br/> |1 Stunde  <br/> |

6. Wählen Sie **Speichern**.

## <a name="add-the-cname-records-that-are-required-for-microsoft"></a>Hinzufügen der für Microsoft erforderlichen CNAME-Einträge
<a name="BKMK_add_CNAME"> </a>

Führen Sie die folgenden Schritte aus.

1. Um zu beginnen, navigieren Sie über [diesen Link](https://account.godaddy.com/products/?go_redirect=disabled) zu Ihrer Domänenseite bei GoDaddy. Sie werden aufgefordert, sich anzumelden.

    ![GoDaddy-BP-configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Wählen Sie unter **Domänen**die Option DNS unter der Domäne aus, die Sie bearbeiten möchten.

    ![GoDaddy-BP-configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Klicken Sie auf **Hinzufügen**.

    ![GoDaddy-BP-configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)


4. Wählen Sie in der Dropdownliste **CNAME (Alias)** aus.

    ![GoDaddy-BP-configure-3-0](../../media/dns/56528891-e7449800-651d-11e9-8eac-112285b8e38c.png)

5. Erstellen Sie den ersten CNAME-Eintrag.

    Geben Sie in den Feldern für den neuen Eintrag die Werte aus der ersten Zeile der folgenden Tabelle ein. Sie können die Werte auch kopieren und einfügen.

    (Wählen Sie in der Dropdownliste den Wert **TTL** aus.)

    |**Record type**|**Host**|**Points to**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME (Alias)  <br/> |autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 Stunde  <br/> |
    |CNAME (Alias)  <br/> |sip  <br/> |sipdir.online.lync.com  <br/> |1 Stunde  <br/> |
    |CNAME (Alias)  <br/> |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |1 Stunde  <br/> |
    |CNAME (Alias)  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |1 hour  <br/> |
    |CNAME (Alias)  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment.manage.microsoft.com  <br/> |1 Stunde  <br/> |



6. Wiederholen Sie diese Schritte, um den nächsten CNAME-Eintrag hinzuzufügen, bis Sie alle sechs CNAME-Einträge erstellt haben.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Hinzufügen eines TXT-Eintrags für SPF, um E-Mail-Spam zu verhindern
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Es kann bei einer Domäne nur einen TXT-Eintrag für SPF geben. Wenn es bei Ihrer Domäne mehrere SPF-Einträge gibt, treten E-Mail-Fehler sowie Probleme bei der Übermittlung und Spamklassifizierung auf. Wenn es für Ihre Domäne bereits einen SPF-Eintrag gibt, erstellen Sie für Microsoft keinen neuen, Fügen Sie stattdessen die erforderlichen Microsoft-Werte zum aktuellen Datensatz hinzu, sodass Sie einen *einzelnen* SPF-Eintrag haben, der beide Wertegruppen enthält.

Führen Sie die folgenden Schritte aus.

1. Um zu beginnen, navigieren Sie über [diesen Link](https://account.godaddy.com/products/?go_redirect=disabled) zu Ihrer Domänenseite bei GoDaddy. Sie werden aufgefordert, sich anzumelden.

    ![GoDaddy-BP-configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Wählen Sie unter **Domänen**die Option DNS unter der Domäne aus, die Sie bearbeiten möchten.

    ![GoDaddy-BP-configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Klicken Sie auf **Hinzufügen**.

    ![GoDaddy-BP-configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. Wählen Sie in der Dropdownliste **TXT (Text)** aus.

    ![GoDaddy-BP-configure-4-0](../../media/dns/56529449-c0d32c80-651e-11e9-90e9-895aa1c4bbf1.png)

5. Geben Sie in den Feldern für den neuen Eintrag die folgenden Werte ein. Sie können die Werte auch kopieren und einfügen.

    (Wählen Sie in den Dropdownlisten den Wert **TTL** aus.)

    |**Record type**|**Host**|**TXT VALUE**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT (Text)  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Hinweis:** Es wird empfohlen, diesen Eintrag zu kopieren und einzufügen, damit alle Abstände korrekt übernommen werden.           |1 Stunde  <br/> |

    ![GoDaddy-BP-configure-4-1](../../media/7c724f02-c9b3-42ab-b9c0-78959fa6ffad.png)

6. Wählen Sie **Speichern**.


## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Hinzufügen der für Microsoft erforderlichen zwei SRV-Einträge
<a name="BKMK_add_SRV"> </a>

Führen Sie die folgenden Schritte aus.

1. Um zu beginnen, navigieren Sie über [diesen Link](https://account.godaddy.com/products/?go_redirect=disabled) zu Ihrer Domänenseite bei GoDaddy. Sie werden aufgefordert, sich anzumelden.

    ![GoDaddy-BP-configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. Wählen Sie unter **Domänen**die Option DNS unter der Domäne aus, die Sie bearbeiten möchten.

    ![GoDaddy-BP-configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. Klicken Sie auf **Hinzufügen**.

    ![GoDaddy-BP-configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. Wählen Sie in der Dropdownliste **SRV (Service)** aus.

    ![GoDaddy-BP-configure-5-0](../../media/dns/56529669-1dcee280-651f-11e9-8ba2-ecf4fc2f6dca.png)

5. Erstellen Sie den ersten SRV-Eintrag.

    Geben Sie in den Feldern für den neuen Eintrag die Werte aus der ersten Zeile der folgenden Tabelle ein. Sie können die Werte auch kopieren und einfügen.

    (Wählen Sie in den Dropdownlisten die Werte für **Record Type** und **TTL** aus.)

    |**Eintragstyp**|**Name**|**Target**|**Protocol**|**Service**|**Priority**|**Weight**|**Port**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV (Service)  <br/> |@  <br/> |sipdir.online.lync.com  <br/> |_tls  <br/> |_sip  <br/> |100  <br/> |1   <br/> |443  <br/> |1 hour  <br/> |
    |SRV (Dienst)  <br/> |@  <br/> |sipfed.online.lync.com  <br/> |_tcp  <br/> |_sipfederationtls  <br/> |100  <br/> |1   <br/> |5061  <br/> |1 Stunde  <br/> |

    ![GoDaddy-BP-configure-5-1](../../media/a1b15ab1-eb6a-4672-90d1-7ac3e0beb223.png)


6. Wiederholen Sie **Schritt 5** , um den anderen SRV-Eintrag zu erstellen.

7. Wählen Sie **Speichern**.

> [!NOTE]
> Normalerweise dauert es ungefähr 15 Minuten, bis DNS-Änderungen wirksam werden. Es kann jedoch gelegentlich länger dauern, bis eine von Ihnen vorgenommene Änderung im Internet im DNS-System aktualisiert wurde. Wenn nach dem Hinzufügen von DNS-Einträgen Probleme mit dem E-Mail-Fluss oder andere Probleme auftreten, lesen Sie [Behandeln von Problemen nach Änderung des Domänennamens oder von DNS-Einträgen](../get-help-with-domains/find-and-fix-issues.md).
