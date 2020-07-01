---
title: Einrichten eines Connectors zum Archivieren von Bloomberg-Nachrichtendaten
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Administratoren können einen Data Connector zum Importieren und Archivieren von Daten aus dem Bloomberg-Nachrichten e-Mail-Tool in Microsoft 365 einrichten. Auf diese Weise können Sie Daten aus Drittanbieter-Datenquellen in Microsoft 365 archivieren, damit Sie Compliance-Features wie Legal Hold, Inhaltssuche und Aufbewahrungsrichtlinien zum Verwalten der drittanbieterdaten Ihrer Organisation verwenden können.
ms.openlocfilehash: 700a0619d2299fc7254628059787478cc0e168fa
ms.sourcegitcommit: c43ebb915fa0eb7eb720b21b62c0d1e58e7cde3d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "44937363"
---
# <a name="set-up-a-connector-to-archive-bloomberg-message-data-preview"></a><span data-ttu-id="caa75-104">Einrichten eines Connectors zum Archivieren von Bloomberg-Nachrichtendaten (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="caa75-104">Set up a connector to archive Bloomberg Message data (preview)</span></span>

<span data-ttu-id="caa75-105">Verwenden Sie einen Daten Konnektor im Microsoft 365 Compliance Center zum Importieren und Archivieren von Finanz Dienstleistungs-e-Mail-Daten aus dem [Bloomberg-Nachrichten](https://www.bloomberg.com/professional/product/collaboration/) Zusammenarbeits Tool.</span><span class="sxs-lookup"><span data-stu-id="caa75-105">Use a data connector in the Microsoft 365 compliance center to import and archive financial services email data from the [Bloomberg Message](https://www.bloomberg.com/professional/product/collaboration/) collaboration tool.</span></span> <span data-ttu-id="caa75-106">Nachdem Sie einen Connector eingerichtet und konfiguriert haben, stellt er eine Verbindung mit der Bloomberg Secure FTP (SFTP)-Website Ihrer Organisation täglich her und importiert e-Mail-Elemente in Postfächer in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="caa75-106">After you set up and configure a connector, it connects to your organization's Bloomberg secure FTP (SFTP) site once every day, and imports email items to mailboxes in Microsoft 365.</span></span>

<span data-ttu-id="caa75-107">Nachdem Bloomberg-Nachrichtendaten in Benutzerpostfächern gespeichert wurden, können Sie Microsoft 365-Compliance-Features wie Beweissicherungsverfahren, Inhaltssuche, in-situ-Archivierung, Überwachung, Kommunikations Konformität und Microsoft 365-Aufbewahrungsrichtlinien auf Bloomberg-Nachrichtendaten anwenden.</span><span class="sxs-lookup"><span data-stu-id="caa75-107">After Bloomberg Message data is stored in user mailboxes, you can apply Microsoft 365 compliance features such as Litigation hold, content search, In-place archiving, auditing, Communication compliance, and Microsoft 365 retention policies to Bloomberg Message data.</span></span> <span data-ttu-id="caa75-108">Beispielsweise können Sie Bloomberg-Nachrichten e-Mails mithilfe des Inhalts Such Tools durchsuchen oder das Postfach, das die Bloomberg-Nachrichtendaten enthält, einer Depotbank in einem erweiterten eDiscovery-Fall zuordnen.</span><span class="sxs-lookup"><span data-stu-id="caa75-108">For example, you can search Bloomberg Message emails using the content search tool or associate the mailbox that contains the Bloomberg Message data with a custodian in an Advanced eDiscovery case.</span></span> <span data-ttu-id="caa75-109">Die Verwendung eines Bloomberg-Nachrichten Connectors zum Importieren und Archivieren von Daten in Microsoft 365 kann dazu beitragen, dass Ihre Organisation mit behördlichen und behördlichen Richtlinien konform bleibt.</span><span class="sxs-lookup"><span data-stu-id="caa75-109">Using a Bloomberg Message connector to import and archive data in Microsoft 365 can help your organization stay compliant with government and regulatory policies.</span></span>

## <a name="overview-of-archiving-bloomberg-message-data"></a><span data-ttu-id="caa75-110">Übersicht über das Archivieren von Bloomberg-Nachrichtendaten</span><span class="sxs-lookup"><span data-stu-id="caa75-110">Overview of archiving Bloomberg Message data</span></span>

<span data-ttu-id="caa75-111">In der folgenden Übersicht wird erläutert, wie Sie einen Connector zum Archivieren von Bloomberg-Nachrichtendaten in Microsoft 365 verwenden.</span><span class="sxs-lookup"><span data-stu-id="caa75-111">The following overview explains the process of using a connector to archive Bloomberg Message data in Microsoft 365.</span></span>

![Bloomberg-Nachrichten Import-und-Archivierungsprozess](../media/BloombergMessageArchiving.png)

1. <span data-ttu-id="caa75-113">Ihre Organisation arbeitet mit Bloomberg zusammen, um eine Bloomberg SFTP-Website einzurichten.</span><span class="sxs-lookup"><span data-stu-id="caa75-113">Your organization works with Bloomberg to set up a Bloomberg SFTP site.</span></span> <span data-ttu-id="caa75-114">Sie werden auch mit Bloomberg zusammenarbeiten, um Bloomberg Message so zu konfigurieren, dass e-Mail-Nachrichten auf die Bloomberg SFTP-Website kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="caa75-114">You'll also work with Bloomberg to configure Bloomberg Message to copy email messages to the Bloomberg SFTP site.</span></span>

2. <span data-ttu-id="caa75-115">Einmal alle 24 Stunden werden e-Mail-Nachrichten von Bloomberg-Nachricht auf die Bloomberg SFTP-Website kopiert.</span><span class="sxs-lookup"><span data-stu-id="caa75-115">Once every 24 hours, email messages from Bloomberg Message are copied to the Bloomberg SFTP site.</span></span>

3. <span data-ttu-id="caa75-116">Der Bloomberg Message Connector, den Sie im Microsoft 365 Compliance Center erstellen, stellt jeden Tag eine Verbindung mit der Bloomberg SFTP-Website her und überträgt die e-Mail-Nachrichten aus den vorherigen 24 Stunden an einen sicheren Azure-Speicherbereich in der Microsoft-Cloud.</span><span class="sxs-lookup"><span data-stu-id="caa75-116">The Bloomberg Message connector that you create in the Microsoft 365 compliance center connects to the Bloomberg SFTP site every day and transfers the email messages from the previous 24 hours to a secure Azure Storage area in the Microsoft Cloud.</span></span>

4. <span data-ttu-id="caa75-117">Der Connector importiert die e-Mail-Nachrichtenelemente in das Postfach eines bestimmten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="caa75-117">The connector imports the email message items to the mailbox of a specific user.</span></span> <span data-ttu-id="caa75-118">Ein neuer Ordner mit dem Namen BloombergMessage wird im Postfach des jeweiligen Benutzers erstellt, und die Elemente werden darin importiert.</span><span class="sxs-lookup"><span data-stu-id="caa75-118">A new folder named BloombergMessage will be created in the specific user's mailbox and the items will be imported to it.</span></span> 

   <span data-ttu-id="caa75-119">Der Connector führt dies mithilfe des Werts der CorporateEmailAddress-Eigenschaft aus.</span><span class="sxs-lookup"><span data-stu-id="caa75-119">The connector does this by using the value of the CorporateEmailAddress property.</span></span> <span data-ttu-id="caa75-120">Jede e-Mail-Nachricht enthält diese Eigenschaft, die mit der e-Mail-Adresse jedes Teilnehmers der e-Mail-Nachricht aufgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="caa75-120">Every email message contains this property, which is populated with the email address of every participant of the email message.</span></span> <span data-ttu-id="caa75-121">Zusätzlich zur automatischen Benutzerzuordnung mit dem Wert der *CorporateEmailAddress* -Eigenschaft können Sie auch eine benutzerdefinierte Zuordnung definieren, indem Sie eine CSV-Zuordnungsdatei hochladen.</span><span class="sxs-lookup"><span data-stu-id="caa75-121">In addition to automatic user mapping using the value of the *CorporateEmailAddress* property, you can also define a custom mapping by uploading a CSV mapping file.</span></span> <span data-ttu-id="caa75-122">Diese Zuordnungsdatei enthält eine Bloomberg-UUID und die entsprechende Microsoft 365-Postfachadresse für jeden Benutzer in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="caa75-122">This mapping file contains a Bloomberg UUID and the corresponding Microsoft 365 mailbox address for each user in your organization.</span></span> <span data-ttu-id="caa75-123">Wenn Sie die automatische Benutzerzuordnung aktivieren und eine benutzerdefinierte Zuordnung bereitstellen, wird der Connector für jedes e-Mail-Element zuerst die benutzerdefinierte Zuordnungsdatei betrachten.</span><span class="sxs-lookup"><span data-stu-id="caa75-123">If you enable automatic user mapping and provide a custom mapping, for every email item the connector will first look at the custom-mapping file.</span></span> <span data-ttu-id="caa75-124">Wenn kein gültiger Microsoft 365-Benutzer gefunden wird, der der Bloomberg-UUID eines Benutzers entspricht, verwendet der Connector die *CorporateEmailAddress* -Eigenschaft des e-Mail-Elements.</span><span class="sxs-lookup"><span data-stu-id="caa75-124">If it doesn't find a valid Microsoft 365 user that corresponds to a user's Bloomberg UUID, the connector uses the *CorporateEmailAddress* property of the email item.</span></span> <span data-ttu-id="caa75-125">Wenn der Connector weder in der benutzerdefinierten Zuordnungsdatei noch in der *CorporateEmailAddress* -Eigenschaft des e-Mail-Elements einen gültigen Microsoft 365-Benutzer findet, wird das Element nicht importiert.</span><span class="sxs-lookup"><span data-stu-id="caa75-125">If the connector doesn't find a valid Microsoft 365 user in either the custom-mapping file or the *CorporateEmailAddress* property of the email item, the item won't be imported.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="caa75-126">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="caa75-126">Before you begin</span></span>

<span data-ttu-id="caa75-127">Viele der Implementierungsschritte, die zum Archivieren von Bloomberg-Nachrichtendaten erforderlich sind, sind extern bei Microsoft 365 und müssen abgeschlossen sein, bevor Sie den Connector im Compliance Center erstellen können.</span><span class="sxs-lookup"><span data-stu-id="caa75-127">Many of the implementation steps required to archive Bloomberg Message data are external to Microsoft 365 and must be completed before you can create the connector in the compliance center.</span></span>

- <span data-ttu-id="caa75-128">Ihre Organisation muss einwilligen, dass der Office 365 Import Dienst auf Postfachdaten in Ihrer Organisation zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="caa75-128">Your organization must consent to allow the Office 365 Import service to access mailbox data in your organization.</span></span> <span data-ttu-id="caa75-129">Um dieser Anforderung zuzustimmen, gehen Sie zu [dieser Seite](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), melden Sie sich mit den Anmeldeinformationen eines Office 365 globalen Administrators an, und nehmen Sie dann die Anforderung an.</span><span class="sxs-lookup"><span data-stu-id="caa75-129">To consent to this request, go to [this page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), sign in with the credentials of an Office 365 global admin, and then accept the request.</span></span> <span data-ttu-id="caa75-130">Sie müssen diesen Schritt ausführen, bevor Sie den Bloomberg Message Connector in Schritt 3 erfolgreich erstellen können.</span><span class="sxs-lookup"><span data-stu-id="caa75-130">You have to complete this step before you can successfully create the Bloomberg Message connector in Step 3.</span></span>

- <span data-ttu-id="caa75-131">Abonnieren Sie [Bloomberg Anywhere](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA).</span><span class="sxs-lookup"><span data-stu-id="caa75-131">Subscribe to [Bloomberg Anywhere](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA).</span></span> <span data-ttu-id="caa75-132">Dies ist erforderlich, damit Sie sich bei Bloomberg Anywhere anmelden können, um auf die Bloomberg SFTP-Website zuzugreifen, die Sie einrichten und konfigurieren müssen.</span><span class="sxs-lookup"><span data-stu-id="caa75-132">This is required so that you can log in to Bloomberg Anywhere to access the Bloomberg SFTP site that you have to set up and configure.</span></span>

- <span data-ttu-id="caa75-133">Richten Sie eine Bloomberg SFTP (Secure File Transfer Protocol)-Website ein.</span><span class="sxs-lookup"><span data-stu-id="caa75-133">Set up a Bloomberg SFTP (Secure file transfer protocol) site.</span></span> <span data-ttu-id="caa75-134">Nach der Arbeit mit Bloomberg, um die SFTP-Website einzurichten, werden die Daten aus Bloomberg-Nachricht jeden Tag auf die SFTP-Website hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="caa75-134">After working with Bloomberg to set up the SFTP site, data from Bloomberg Message is uploaded to the SFTP site every day.</span></span> <span data-ttu-id="caa75-135">Der in Schritt 2 erstellte Connector stellt eine Verbindung mit dieser SFTP-Website her und überträgt die e-Mail-Daten an Microsoft 365-Postfächer.</span><span class="sxs-lookup"><span data-stu-id="caa75-135">The connector you create in Step 2 connects to this SFTP site and transfers the email data to Microsoft 365 mailboxes.</span></span> <span data-ttu-id="caa75-136">SFTP verschlüsselt auch die Bloomberg-Nachrichtendaten, die während des Übertragungsprozesses an Postfächer gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="caa75-136">SFTP also encrypts the Bloomberg Message data that is sent to mailboxes during the transfer process.</span></span>

  <span data-ttu-id="caa75-137">Informationen zu Bloomberg SFTP (auch *BB-SFTP*genannt):</span><span class="sxs-lookup"><span data-stu-id="caa75-137">For information about Bloomberg SFTP (also called *BB-SFTP*):</span></span>

  - <span data-ttu-id="caa75-138">Siehe das Dokument "SFTP Connectivity Standards" unter [Bloomberg Support](https://www.bloomberg.com/professional/support/documentation/).</span><span class="sxs-lookup"><span data-stu-id="caa75-138">See the "SFTP Connectivity Standards" document at [Bloomberg Support](https://www.bloomberg.com/professional/support/documentation/).</span></span>

  - <span data-ttu-id="caa75-139">Wenden Sie sich an den [Bloomberg-Kundensupport](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).</span><span class="sxs-lookup"><span data-stu-id="caa75-139">Contact [Bloomberg customer support](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).</span></span>

   > [!NOTE]
   > <span data-ttu-id="caa75-140">Wenn Ihre Organisation bereits einen Connector zur Archivierung von Bloomberg-Daten bereitgestellt hat, müssen Sie keine andere SFTP-Website einrichten.</span><span class="sxs-lookup"><span data-stu-id="caa75-140">If your organization already deployed a connector to archive Instant Bloomberg data, you don't need to set up another SFTP site.</span></span> <span data-ttu-id="caa75-141">Sie können die gleiche SFTP-Website für den Bloomberg Message Connector verwenden.</span><span class="sxs-lookup"><span data-stu-id="caa75-141">You can use the same SFTP site for the Bloomberg Message connector.</span></span>

- <span data-ttu-id="caa75-142">Nachdem Sie mit Bloomberg zusammengearbeitet haben, um eine SFTP-Website einzurichten, stellt Bloomberg Ihnen einige Informationen zur Verfügung, nachdem Sie auf die e-Mail-Nachricht der Bloomberg-Implementierung reagiert haben.</span><span class="sxs-lookup"><span data-stu-id="caa75-142">After you work with Bloomberg to set up an SFTP site, Bloomberg will provide some information to you after you respond to the Bloomberg implementation email message.</span></span> <span data-ttu-id="caa75-143">Speichern Sie eine Kopie der folgenden Informationen.</span><span class="sxs-lookup"><span data-stu-id="caa75-143">Save a copy of the following information.</span></span> <span data-ttu-id="caa75-144">Sie verwenden Sie, um einen Connector in Schritt 3 einzurichten.</span><span class="sxs-lookup"><span data-stu-id="caa75-144">You use it to set up a connector in Step 3.</span></span>

  - <span data-ttu-id="caa75-145">Firm Code, der eine ID für Ihre Organisation ist und zur Anmeldung bei der Bloomberg SFTP-Website verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="caa75-145">Firm code, which is an ID for your organization and is used to log in to the Bloomberg SFTP site.</span></span>

  - <span data-ttu-id="caa75-146">Kennwort für Ihre Bloomberg SFTP-Website</span><span class="sxs-lookup"><span data-stu-id="caa75-146">Password for your Bloomberg SFTP site</span></span>

  - <span data-ttu-id="caa75-147">URL für Bloomberg SFTP-Website (beispielsweise SFTP.Bloomberg.com).</span><span class="sxs-lookup"><span data-stu-id="caa75-147">URL for Bloomberg SFTP site (for example, sftp.bloomberg.com).</span></span> <span data-ttu-id="caa75-148">Darüber hinaus kann Bloomberg auch eine entsprechende IP-Adresse für die Bloomberg SFTP-Website bereitstellen, die auch zum Einrichten des Connectors verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="caa75-148">In addition, Bloomberg may also provide a corresponding IP address for the Bloomberg SFTP site, which also can be used to set up the connector.</span></span>

  - <span data-ttu-id="caa75-149">Port Nummer für Bloomberg SFTP-Website</span><span class="sxs-lookup"><span data-stu-id="caa75-149">Port number for Bloomberg SFTP site</span></span>

- <span data-ttu-id="caa75-150">Der Benutzer, der in Schritt 3 einen Bloomberg-Nachrichten Konnektor erstellt (und der die öffentlichen Schlüssel und die IP-Adresse in Schritt 1 herunterlädt) muss die Rolle "Post Fach Import Export" in Exchange Online zugewiesen haben.</span><span class="sxs-lookup"><span data-stu-id="caa75-150">The user who creates a Bloomberg Message connector in Step 3 (and who downloads the public keys and IP address in Step 1) must be assigned the Mailbox Import Export role in Exchange Online.</span></span> <span data-ttu-id="caa75-151">Dies ist für das Hinzufügen von Connectors auf der Seite " **Daten Konnektoren** " im Microsoft 365 Compliance Center erforderlich.</span><span class="sxs-lookup"><span data-stu-id="caa75-151">This is required to add connectors in the **Data connectors** page in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="caa75-152">Standardmäßig ist diese Rolle keiner Rollengruppe in Exchange Online zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="caa75-152">By default, this role isn't assigned to any role group in Exchange Online.</span></span> <span data-ttu-id="caa75-153">Sie können die Rolle "Post Fach Import exportieren" der Rollengruppe "Organisationsverwaltung" in Exchange Online hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="caa75-153">You can add the Mailbox Import Export role to the Organization Management role group in Exchange Online.</span></span> <span data-ttu-id="caa75-154">Sie können auch eine Rollengruppe erstellen, die Rolle "Post Fach Import Export" zuweisen und dann die entsprechenden Benutzer als Mitglieder hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="caa75-154">Or you can create a role group, assign the Mailbox Import Export role, and then add the appropriate users as members.</span></span> <span data-ttu-id="caa75-155">Weitere Informationen finden Sie im Abschnitt [Erstellen](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) von Rollengruppen oder [Ändern von Rollengruppen](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) im Artikel "Verwalten von Rollengruppen in Exchange Online".</span><span class="sxs-lookup"><span data-stu-id="caa75-155">For more information, see the [Create role groups](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) or [Modify role groups](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) sections in the article "Manage role groups in Exchange Online".</span></span>


## <a name="step-1-obtain-ssh-and-pgp-public-keys"></a><span data-ttu-id="caa75-156">Schritt 1: Abrufen von öffentlichen SSH-und PGP-Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="caa75-156">Step 1: Obtain SSH and PGP public keys</span></span>

<span data-ttu-id="caa75-157">Der erste Schritt besteht darin, eine Kopie der öffentlichen Schlüssel für Secure Shell (SSH) und Pretty Good Privacy (PGP) zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="caa75-157">The first step is to obtain a copy of the public keys for Secure Shell (SSH) and Pretty Good Privacy (PGP).</span></span> <span data-ttu-id="caa75-158">Sie verwenden diese Schlüssel in Schritt 2, um die Bloomberg-SFTP-Website so zu konfigurieren, dass der in Schritt 3 erstellte Connector eine Verbindung mit der SFTP-Website herstellen und die Bloomberg-Nachrichten e-Mail-Daten an Microsoft 365-Postfächerüber tragen kann.</span><span class="sxs-lookup"><span data-stu-id="caa75-158">You use these keys in Step 2 to configure the Bloomberg SFTP site to allow the connector (that you create in Step 3) to connect to the SFTP site and transfer the Bloomberg Message email data to Microsoft 365 mailboxes.</span></span> <span data-ttu-id="caa75-159">Außerdem erhalten Sie in diesem Schritt eine IP-Adresse, die Sie beim Konfigurieren der Bloomberg SFTP-Website verwenden.</span><span class="sxs-lookup"><span data-stu-id="caa75-159">You also obtain an IP address in this step, which you use when configuring the Bloomberg SFTP site.</span></span>

1. <span data-ttu-id="caa75-160">Wechseln Sie zu [ https://compliance.microsoft.com\ ] ( https://compliance.microsoft.com) und klicken Sie im linken Navigationsbereich auf **Daten-Konnektoren** .</span><span class="sxs-lookup"><span data-stu-id="caa75-160">Go to [https://compliance.microsoft.com\](https://compliance.microsoft.com) and click **Data connectors** in the left nav.</span></span>

2. <span data-ttu-id="caa75-161">Klicken Sie auf der Seite **Daten Konnektoren** unter **Bloomberg-Nachricht**auf **Ansicht**.</span><span class="sxs-lookup"><span data-stu-id="caa75-161">On the **Data connectors** page under **Bloomberg Message**, click **View**.</span></span>

3. <span data-ttu-id="caa75-162">Klicken Sie auf der Seite **Bloomberg-Nachrichten** Produktbeschreibung auf **Connector hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="caa75-162">On the **Bloomberg Message** product description page, click **Add connector**</span></span>

4. <span data-ttu-id="caa75-163">Klicken Sie auf der Seite **Nutzungsbedingungen** auf **annehmen**.</span><span class="sxs-lookup"><span data-stu-id="caa75-163">On the **Terms of service** page, click **Accept**.</span></span>

5. <span data-ttu-id="caa75-164">Klicken Sie auf der **Website Anmeldeinformationen für Bloomberg SFTP** unter Schritt 1 auf den Link **SSH herunterladen**, **PGP-Schlüssel**herunterladen und **IP-Adress Links herunterladen** , um eine Kopie der einzelnen Dateien auf dem lokalen Computer zu speichern.</span><span class="sxs-lookup"><span data-stu-id="caa75-164">On the **Add credentials for Bloomberg SFTP site** under step 1, click the **Download SSH key**, **Download PGP key**, and **Download IP address** links to save a copy of each file to your local computer.</span></span> <span data-ttu-id="caa75-165">Diese Dateien enthalten die folgenden Elemente, die zum Konfigurieren der Bloomberg SFTP-Website in Schritt 2 verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="caa75-165">These files contain the following items that are used to configure the Bloomberg SFTP site in Step 2:</span></span>

   - <span data-ttu-id="caa75-166">Öffentlicher SSH-Schlüssel: dieser Schlüssel wird zum Konfigurieren von Secure Shell (SSH) verwendet, um eine sichere Remoteanmeldung zu ermöglichen, wenn der Connector eine Verbindung mit der Bloomberg SFTP-Website herstellt.</span><span class="sxs-lookup"><span data-stu-id="caa75-166">SSH public key: This key is used to configure Secure Shell (SSH) to enable a secure remote login when the connector connects to the Bloomberg SFTP site.</span></span>

   - <span data-ttu-id="caa75-167">Öffentlicher PGP-Schlüssel: dieser Schlüssel wird verwendet, um die Verschlüsselung von Daten zu konfigurieren, die von der Bloomberg SFTP-Website an Microsoft 365 übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="caa75-167">PGP public key: This key is used to configure the encryption of data that's transferred from the Bloomberg SFTP site to Microsoft 365.</span></span>

   - <span data-ttu-id="caa75-168">IP-Adresse: die Bloomberg SFTP-Website ist so konfiguriert, dass Sie eine Verbindungsanforderung nur von dieser IP-Adresse akzeptiert, die von dem Bloomberg-Nachrichten Connector verwendet wird, den Sie in Schritt 3 erstellen.</span><span class="sxs-lookup"><span data-stu-id="caa75-168">IP address: The Bloomberg SFTP site is configured to accept a connection request only from this IP address, which is used by the Bloomberg Message connector that you create in Step 3.</span></span>

6. <span data-ttu-id="caa75-169">Klicken Sie auf **Abbrechen** , um den Assistenten zu schließen.</span><span class="sxs-lookup"><span data-stu-id="caa75-169">Click **Cancel** to close the wizard.</span></span> <span data-ttu-id="caa75-170">Sie kehren zu diesem Assistenten in Schritt 3 zurück, um den Connector zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="caa75-170">You come back to this wizard in Step 3 to create the connector.</span></span>

## <a name="step-2-configure-the-bloomberg-sftp-site"></a><span data-ttu-id="caa75-171">Schritt 2: Konfigurieren der Bloomberg SFTP-Website</span><span class="sxs-lookup"><span data-stu-id="caa75-171">Step 2: Configure the Bloomberg SFTP site</span></span>

> [!NOTE]
> <span data-ttu-id="caa75-172">Wenn Sie, wie bereits erwähnt, zuvor eine Bloomberg-SFTP-Website eingerichtet haben, um Bloomberg-Daten zu archivieren, müssen Sie kein weiteres einrichten.</span><span class="sxs-lookup"><span data-stu-id="caa75-172">As previously stated, if you're organization has previously set up a Bloomberg SFTP site to archive Instant Bloomberg data, you don't have to set up another one.</span></span> <span data-ttu-id="caa75-173">Sie können dieselbe SFTP-Website angeben, wenn Sie den Connector in Schritt 3 erstellen.</span><span class="sxs-lookup"><span data-stu-id="caa75-173">You can specify the same SFTP site when you create the connector in Step 3.</span></span>

<span data-ttu-id="caa75-174">Der nächste Schritt besteht darin, die öffentlichen SSH-und PGP-Schlüssel sowie die IP-Adresse zu verwenden, die Sie in Schritt 1 zum Konfigurieren der SSH-Authentifizierung und der PGP-Verschlüsselung für die Bloomberg SFTP-Website erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="caa75-174">The next step is to use the SSH and PGP public keys and the IP address that you obtained in Step 1 to configure SSH authentication and PGP encryption for the Bloomberg SFTP site.</span></span> <span data-ttu-id="caa75-175">Dadurch kann der in Schritt 3 erstellte Bloomberg-Nachrichten Connector eine Verbindung mit der Bloomberg SFTP-Website herstellen und Bloomberg-Nachrichtendaten an Microsoft 365 übertragen.</span><span class="sxs-lookup"><span data-stu-id="caa75-175">This lets the Bloomberg Message connector that you create in Step 3 connect to the Bloomberg SFTP site and transfer Bloomberg Message data to Microsoft 365.</span></span> <span data-ttu-id="caa75-176">Sie müssen mit dem Bloomberg-Kundensupport zusammenarbeiten, um Ihre Bloomberg SFTP-Website einzurichten.</span><span class="sxs-lookup"><span data-stu-id="caa75-176">You need to work with Bloomberg customer support to set up your Bloomberg SFTP site.</span></span> <span data-ttu-id="caa75-177">Wenden Sie sich zur Unterstützung an den [Bloomberg-Kundensupport](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) .</span><span class="sxs-lookup"><span data-stu-id="caa75-177">Contact [Bloomberg customer support](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) for assistance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="caa75-178">Bloomberg empfiehlt, dass Sie die drei Dateien, die Sie in Schritt 1 heruntergeladen haben, an eine e-Mail-Nachricht anfügen und diese an Ihren Kundensupport senden, wenn Sie mit Ihnen zusammenarbeiten, um Ihre Bloomberg SFTP-Website einzurichten.</span><span class="sxs-lookup"><span data-stu-id="caa75-178">Bloomberg recommends that you attach the three files that you downloaded in Step 1 to an email message and send it to their customer support team when working with them to set up your Bloomberg SFTP site.</span></span>

## <a name="step-3-create-a-bloomberg-message-connector"></a><span data-ttu-id="caa75-179">Schritt 3: Erstellen eines Bloomberg-Nachrichten Connectors</span><span class="sxs-lookup"><span data-stu-id="caa75-179">Step 3: Create a Bloomberg Message connector</span></span>

<span data-ttu-id="caa75-180">Der letzte Schritt besteht darin, einen Bloomberg-Nachrichten Connector im Microsoft 365 Compliance Center zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="caa75-180">The last step is to create a Bloomberg Message connector in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="caa75-181">Der Connector verwendet die von Ihnen bereitgestellten Informationen, um eine Verbindung mit der Bloomberg SFTP-Website herzustellen und e-Mail-Nachrichten an die entsprechenden Benutzer Postfache in Microsoft 365 zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="caa75-181">The connector uses the information you provide to connect to the Bloomberg SFTP site and transfer email messages to the corresponding user mailbox boxes in Microsoft 365.</span></span>

1. <span data-ttu-id="caa75-182">Wechseln Sie zu, [https://compliance.microsoft.com](https://compliance.microsoft.com) und klicken Sie im linken Navigationsbereich auf **Daten-Konnektoren** .</span><span class="sxs-lookup"><span data-stu-id="caa75-182">Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.</span></span>

2. <span data-ttu-id="caa75-183">Klicken Sie auf der Seite **Daten Konnektoren** unter **Bloomberg-Nachricht**auf **Ansicht**.</span><span class="sxs-lookup"><span data-stu-id="caa75-183">On the **Data connectors** page under **Bloomberg Message**, click **View**.</span></span>

3. <span data-ttu-id="caa75-184">Klicken Sie auf der Seite **Bloomberg-Nachrichten** Produktbeschreibung auf **Connector hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="caa75-184">On the **Bloomberg Message** product description page, click **Add connector**</span></span>

4. <span data-ttu-id="caa75-185">Klicken Sie auf der Seite **Nutzungsbedingungen** auf **annehmen**.</span><span class="sxs-lookup"><span data-stu-id="caa75-185">On the **Terms of service** page, click **Accept**.</span></span>

5. <span data-ttu-id="caa75-186">Geben Sie auf der Seite **Anmeldeinformationen für Bloomberg SFTP-Website hinzufügen** unter Schritt 3 die erforderlichen Informationen in die folgenden Felder ein, und klicken Sie dann auf **weiter**.</span><span class="sxs-lookup"><span data-stu-id="caa75-186">On the **Add credentials for Bloomberg SFTP site** page, under Step 3, enter the required information in the following boxes and then click **Next**.</span></span>

      - <span data-ttu-id="caa75-187">**Firm Code:** Die ID für Ihre Organisation, die als Benutzername für die Bloomberg SFTP-Website verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="caa75-187">**Firm code:** The ID for your organization that is used as the username for the Bloomberg SFTP site.</span></span>

      - <span data-ttu-id="caa75-188">**Kennwort:** Das Kennwort für die Bloomberg SFTP-Website Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="caa75-188">**Password:** The password for your organization's Bloomberg SFTP site.</span></span>

      - <span data-ttu-id="caa75-189">**SFTP-URL:** Die URL für die Bloomberg-SFTP-Website (beispielsweise SFTP.Bloomberg.com).</span><span class="sxs-lookup"><span data-stu-id="caa75-189">**SFTP URL:** The URL for the Bloomberg SFTP site (for example, sftp.bloomberg.com).</span></span>

      - <span data-ttu-id="caa75-190">**SFTP-Port:** Die Portnummer für die Bloomberg SFTP-Website.</span><span class="sxs-lookup"><span data-stu-id="caa75-190">**SFTP port:** The port number for the Bloomberg SFTP site.</span></span> <span data-ttu-id="caa75-191">Der Connector verwendet diesen Port, um eine Verbindung mit der SFTP-Website herzustellen.</span><span class="sxs-lookup"><span data-stu-id="caa75-191">The connector uses this port to connect to the SFTP site.</span></span>

6. <span data-ttu-id="caa75-192">Aktivieren Sie auf der Seite **Benutzerzuordnung** die automatische Benutzerzuordnung, und geben Sie nach Bedarf Benutzerzuordnung an.</span><span class="sxs-lookup"><span data-stu-id="caa75-192">On the **User-mapping** page, enable automatic user mapping and provide custom user mapping as required</span></span>

7. <span data-ttu-id="caa75-193">Klicken Sie auf **weiter**, überprüfen Sie Ihre Einstellungen, und klicken Sie dann auf vorbereiten, um den Connector zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="caa75-193">Click **Next**, review your settings, and then click prepare to create the connector.</span></span>

8. <span data-ttu-id="caa75-194">Wechseln Sie zur Seite **Daten Konnektoren** , um den Fortschritt des Importvorgangs für den neuen Connector anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="caa75-194">Go to the **Data connectors** page to see the progress of the import process for the new connector.</span></span>

## <a name="known-issues"></a><span data-ttu-id="caa75-195">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="caa75-195">Known issues</span></span>

- <span data-ttu-id="caa75-196">Das Threading von Bloomberg-Nachrichten e-Mails, die in Microsoft 365 importiert werden, wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="caa75-196">Threading of Bloomberg Message email imported to Microsoft 365 isn't supported.</span></span> <span data-ttu-id="caa75-197">Einzelne Nachrichten, die an eine Person gesendet werden, werden importiert, aber nicht in einer Thread-Unterhaltung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="caa75-197">Individual messages sent to a person are imported, but they aren't presented in a threaded conversation.</span></span> <span data-ttu-id="caa75-198">Microsoft arbeitet an der Unterstützung des Threadings in späteren Versionen des Bloomberg-Nachrichtendaten-Konnektors.</span><span class="sxs-lookup"><span data-stu-id="caa75-198">Microsoft is working to support threading in later versions of the Bloomberg Message data connector.</span></span>