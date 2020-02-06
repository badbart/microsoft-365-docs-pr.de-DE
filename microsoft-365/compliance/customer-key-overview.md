---
title: Dienst Verschlüsselung mit Kundenschlüssel in Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 02/05/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Mit Customer Key können Sie die kryptografischen Schlüssel Ihrer Organisation steuern und dann Office 365 konfigurieren, um Ihre Daten im Ruhezustand in Microsoft-Rechenzentren mithilfe dieser Schlüssel zu verschlüsseln.
ms.openlocfilehash: ee62065542ea50091d73362dd8d05f2e4e7dc337
ms.sourcegitcommit: 5ff1dc62e8855be155cb2de45cf4ee5a02c321fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "41804799"
---
# <a name="service-encryption-with-customer-key-in-office-365"></a><span data-ttu-id="caf57-103">Dienst Verschlüsselung mit Kundenschlüssel in Office 365</span><span class="sxs-lookup"><span data-stu-id="caf57-103">Service encryption with Customer Key in Office 365</span></span>

<span data-ttu-id="caf57-104">Office 365 bietet eine Basis für die Verschlüsselung auf Volumen Ebene, die über BitLocker und den verteilten Schlüssel-Manager (DKM) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="caf57-104">Office 365 provides baseline, volume-level encryption enabled through BitLocker and Distributed Key Manager (DKM).</span></span> <span data-ttu-id="caf57-105">Office 365 bietet eine zusätzliche Verschlüsselungsebene auf Anwendungsebene für Ihre Inhalte.</span><span class="sxs-lookup"><span data-stu-id="caf57-105">Office 365 offers an added layer of encryption at the application level for your content.</span></span> <span data-ttu-id="caf57-106">Dieser Inhalt enthält Daten aus Exchange Online-, Skype for Business-, SharePoint Online-, OneDrive für Unternehmen-und Microsoft Teams-Dateien.</span><span class="sxs-lookup"><span data-stu-id="caf57-106">This content includes data from Exchange Online, Skype for Business, SharePoint Online, OneDrive for Business, and Teams files.</span></span> <span data-ttu-id="caf57-107">Diese hinzugefügte Verschlüsselungsebene wird als Dienst Verschlüsselung bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="caf57-107">This added layer of encryption is called service encryption.</span></span>

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a><span data-ttu-id="caf57-108">Zusammenarbeit von Dienst Verschlüsselung, BitLocker und Kunden Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="caf57-108">How service encryption, BitLocker, and Customer Key work together</span></span>

<span data-ttu-id="caf57-109">Durch die Dienst Verschlüsselung wird sichergestellt, dass Inhalte im Ruhezustand auf Anwendungsebene verschlüsselt werden.</span><span class="sxs-lookup"><span data-stu-id="caf57-109">Service encryption ensures that content at rest is encrypted at the application layer.</span></span> <span data-ttu-id="caf57-110">**Ihre Daten werden in Rest im Office 365 Dienst mit BitLocker und DKM immer verschlüsselt**.</span><span class="sxs-lookup"><span data-stu-id="caf57-110">**Your data is always encrypted at rest in the Office 365 service with BitLocker and DKM**.</span></span> <span data-ttu-id="caf57-111">Weitere Informationen finden Sie unter "Sicherheits-, Datenschutz-und Kompatibilitätsinformationen für Office 365" sowie dazu, [wie Exchange Online Ihre e-Mail-Geheimnisse sichert](exchange-online-secures-email-secrets.md).</span><span class="sxs-lookup"><span data-stu-id="caf57-111">For more information, see the "Security, Privacy, and Compliance Information for Office 365", and [How Exchange Online secures your email secrets](exchange-online-secures-email-secrets.md).</span></span> <span data-ttu-id="caf57-112">Der Kundenschlüssel bietet zusätzlichen Schutz vor dem Anzeigen von Daten durch nicht autorisierte Systeme oder Mitarbeiter und ergänzt die BitLocker-Datenträgerverschlüsselung in Microsoft-Rechenzentren.</span><span class="sxs-lookup"><span data-stu-id="caf57-112">Customer Key provides additional protection against viewing of data by unauthorized systems or personnel, and complements BitLocker disk encryption in Microsoft datacenters.</span></span> <span data-ttu-id="caf57-113">Die Dienst Verschlüsselung soll nicht verhindern, dass Microsoft-Mitarbeiter auf Kundendaten zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="caf57-113">Service encryption is not meant to prevent Microsoft personnel from accessing customer data.</span></span> <span data-ttu-id="caf57-114">Der Hauptzweck besteht darin, Kunden bei der Erfüllung behördlicher oder Compliance-rechtlicher Verpflichtungen zur Steuerung von Stamm Schlüsseln zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="caf57-114">The primary purpose is to assist customers in meeting regulatory or compliance obligations for controlling root keys.</span></span> <span data-ttu-id="caf57-115">Kunden autorisieren O365 Services ausdrücklich, ihre Verschlüsselungsschlüssel zur Bereitstellung von Mehrwert-Cloud-Diensten wie eDiscovery, Antischadsoftware, Spam Schutz, Suchindizierung usw. zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="caf57-115">Customers explicitly authorize O365 services to use their encryption keys to provide value added cloud services, such as eDiscovery, anti-malware, anti-spam, search indexing, etc.</span></span>

<span data-ttu-id="caf57-116">Der Kundenschlüssel basiert auf der Dienst Verschlüsselung und ermöglicht Ihnen das Bereitstellen und Steuern von Verschlüsselungsschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="caf57-116">Customer Key is built on service encryption and lets you provide and control encryption keys.</span></span> <span data-ttu-id="caf57-117">Office 365 verwendet diese Schlüssel dann zum Verschlüsseln von Daten im Ruhezustand, wie in den [Online Dienste-Bedingungen (Ost)](https://www.microsoft.com/licensing/product-licensing/products.aspx)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="caf57-117">Office 365 then uses these keys to encrypt your data at rest as described in the [Online Services Terms (OST)](https://www.microsoft.com/licensing/product-licensing/products.aspx).</span></span> <span data-ttu-id="caf57-118">Mit dem Kundenschlüssel können Sie Compliance-Verpflichtungen erfüllen, da Sie die Verschlüsselungsschlüssel steuern, die Office 365 zum Verschlüsseln und Entschlüsseln von Daten verwendet.</span><span class="sxs-lookup"><span data-stu-id="caf57-118">Customer Key helps you meet compliance obligations because you control the encryption keys that Office 365 uses to encrypt and decrypt data.</span></span>
  
<span data-ttu-id="caf57-119">Kundenschlüssel verbessert die Fähigkeit Ihrer Organisation, die Anforderungen der Compliance-Anforderungen zu erfüllen, die wichtige Vereinbarungen mit dem Cloud-Dienstanbieter festlegen.</span><span class="sxs-lookup"><span data-stu-id="caf57-119">Customer Key enhances the ability of your organization to meet the demands of compliance requirements that specify key arrangements with the cloud service provider.</span></span> <span data-ttu-id="caf57-120">Mit dem Kundenschlüssel stellen und Steuern Sie die Stamm Verschlüsselungsschlüssel für Ihre Office 365-Rest-Daten auf Anwendungsebene.</span><span class="sxs-lookup"><span data-stu-id="caf57-120">With Customer Key, you provide and control the root encryption keys for your Office 365 data at-rest at the application level.</span></span> <span data-ttu-id="caf57-121">Folglich üben Sie die Kontrolle über die Schlüssel Ihrer Organisation aus.</span><span class="sxs-lookup"><span data-stu-id="caf57-121">As a result, you exercise control over your organization's keys.</span></span> <span data-ttu-id="caf57-122">Wenn Sie sich entschließen, den Dienst zu beenden, widerrufen Sie den Zugriff auf die Stammschlüssel Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="caf57-122">If you decide to exit the service, you revoke access to your organization's root keys.</span></span> <span data-ttu-id="caf57-123">Bei allen Office 365 Diensten ist der Widerruf des Zugriffs auf die Schlüssel der erste Schritt auf dem Weg zum Löschen von Daten.</span><span class="sxs-lookup"><span data-stu-id="caf57-123">For all Office 365 services, revoking access to the keys is the first step on the path towards data deletion.</span></span> <span data-ttu-id="caf57-124">Durch das widerrufen des Zugriffs auf die Schlüssel sind die Daten für den Dienst nicht lesbar.</span><span class="sxs-lookup"><span data-stu-id="caf57-124">By revoking access to the keys, the data is unreadable to the service.</span></span>

## <a name="customer-key-encrypts-data-at-rest-in-office-365"></a><span data-ttu-id="caf57-125">Kundenschlüssel verschlüsselt Daten im Ruhezustand in Office 365</span><span class="sxs-lookup"><span data-stu-id="caf57-125">Customer Key encrypts data at rest in Office 365</span></span>

<span data-ttu-id="caf57-126">Mithilfe von von Ihnen bereitgestellten Schlüsseln verschlüsselt der Kundenschlüssel für Office 365:</span><span class="sxs-lookup"><span data-stu-id="caf57-126">Using keys you provide, Customer Key for Office 365 encrypts:</span></span>

- <span data-ttu-id="caf57-127">SharePoint Online-, OneDrive für Unternehmen-und Microsoft Teams-Dateien.</span><span class="sxs-lookup"><span data-stu-id="caf57-127">SharePoint Online, OneDrive for Business, and Teams files.</span></span>
- <span data-ttu-id="caf57-128">In OneDrive für Unternehmen hochgeladene Dateien.</span><span class="sxs-lookup"><span data-stu-id="caf57-128">Files uploaded to OneDrive for Business.</span></span>
- <span data-ttu-id="caf57-129">Exchange Online Postfachinhalte einschließlich Inhalt von e-Mail-Text, Kalendereinträgen und Inhalt in e-Mail-Anlagen.</span><span class="sxs-lookup"><span data-stu-id="caf57-129">Exchange Online mailbox content including e-mail body content, calendar entries, and the content within email attachments.</span></span>
- <span data-ttu-id="caf57-130">Text Unterhaltungen aus Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="caf57-130">Text conversations from Skype for Business.</span></span>

<span data-ttu-id="caf57-131">Wir bieten derzeit keine Kunden Kontrolle über die Verschlüsselungsschlüssel für Uploads von Skype-Live Konferenzen und Skype-Besprechungsinhalten.</span><span class="sxs-lookup"><span data-stu-id="caf57-131">We don't currently offer customer control of the encryption keys for Skype Meeting Broadcast and Skype Meeting content uploads.</span></span> <span data-ttu-id="caf57-132">Stattdessen werden diese Inhalte zusammen mit allen anderen Inhalten in Office 365 verschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="caf57-132">Instead, this content is encrypted along with all other content in Office 365.</span></span>

### <a name="customer-key-with-hybrid-deployments"></a><span data-ttu-id="caf57-133">Kundenschlüssel mit hybridbereitstellungen</span><span class="sxs-lookup"><span data-stu-id="caf57-133">Customer Key with hybrid deployments</span></span>

<span data-ttu-id="caf57-134">Der Kundenschlüssel verschlüsselt nur Daten im Rest in der Cloud.</span><span class="sxs-lookup"><span data-stu-id="caf57-134">Customer Key only encrypts data at rest in the cloud.</span></span> <span data-ttu-id="caf57-135">Der Kundenschlüssel kann nicht zum Schutz Ihrer lokalen Postfächer und Dateien verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="caf57-135">Customer Key does not work to protect your on-premises mailboxes and files.</span></span> <span data-ttu-id="caf57-136">Sie können Ihre lokalen Daten mithilfe einer anderen Methode wie BitLocker verschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="caf57-136">You can encrypt your on-premises data using another method, such as BitLocker.</span></span>

## <a name="about-the-data-encryption-policy-dep"></a><span data-ttu-id="caf57-137">Informationen zur Daten Verschlüsselungsrichtlinie (DEP)</span><span class="sxs-lookup"><span data-stu-id="caf57-137">About the data encryption policy (DEP)</span></span>

<span data-ttu-id="caf57-138">Eine Daten Verschlüsselungsrichtlinie definiert die Verschlüsselungshierarchie zum Verschlüsseln von Daten mit jedem der von Ihnen bereitgestellten Schlüssel sowie den von Microsoft geschützten Verfügbarkeits Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="caf57-138">A data encryption policy defines the encryption hierarchy to encrypt data using each of the keys you provide as well as the availability key protected by Microsoft.</span></span> <span data-ttu-id="caf57-139">Sie erstellen DEPs mithilfe von PowerShell-Cmdlets, die für jeden Dienst unterschiedlich sind, und weisen diese zum Verschlüsseln von Anwendungsdaten zu.</span><span class="sxs-lookup"><span data-stu-id="caf57-139">You create DEPs using PowerShell cmdlets, which are different for each service, and assign those to encrypt application data.</span></span> <span data-ttu-id="caf57-140">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="caf57-140">For example:</span></span>

<span data-ttu-id="caf57-141">**Exchange Online und Skype for Business** Sie können bis zu 50 DEPs pro Mandant erstellen.</span><span class="sxs-lookup"><span data-stu-id="caf57-141">**Exchange Online and Skype for Business** You can create up to 50 DEPs per tenant.</span></span> <span data-ttu-id="caf57-142">Sie ordnen DEPs ihren Kunden Schlüsseln in Azure Key Vault zu und weisen dann DEPs einzelnen Postfächern zu.</span><span class="sxs-lookup"><span data-stu-id="caf57-142">You associate DEPs to your Customer Keys in Azure Key Vault and then assign DEPs to individual mailboxes.</span></span> <span data-ttu-id="caf57-143">Wenn Sie einer Datenausführungsverhinderung einem Postfach zuweisen:</span><span class="sxs-lookup"><span data-stu-id="caf57-143">When you assign a DEP to a mailbox:</span></span>

- <span data-ttu-id="caf57-144">das Postfach ist für eine Post Fach Verlagerung markiert.</span><span class="sxs-lookup"><span data-stu-id="caf57-144">the mailbox is marked for a mailbox move.</span></span> <span data-ttu-id="caf57-145">Basierend auf den Prioritäten in Office 365 wie hier beschrieben, [verschiebt Anforderungen im Office 365 Dienst](https://docs.microsoft.com/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-office-365-service).</span><span class="sxs-lookup"><span data-stu-id="caf57-145">Based on priorities in Office 365 as described here [Move requests in the Office 365 service](https://docs.microsoft.com/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-office-365-service).</span></span>

- <span data-ttu-id="caf57-146">Die Verschlüsselung erfolgt, während das Postfach verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="caf57-146">The encryption takes place while the mailbox is moved.</span></span> <span data-ttu-id="caf57-147">Lassen Sie 72 Stunden zu, damit das Postfach mit der neuen DEP verschlüsselt wird.</span><span class="sxs-lookup"><span data-stu-id="caf57-147">Allow 72 hours for the mailbox to become encrypted with the new DEP.</span></span> <span data-ttu-id="caf57-148">Wenn die Postfächer nach dem warten auf 72 Stunden ab dem Zeitpunkt, an dem Sie die DEP erhalten haben, nicht verschlüsselt sind, wenden Sie sich an Microsoft.</span><span class="sxs-lookup"><span data-stu-id="caf57-148">If the mailboxes aren't encrypted after waiting 72 hours from the time you assigned the DEP, contact Microsoft.</span></span>

<span data-ttu-id="caf57-149">Später können Sie entweder die DEP aktualisieren oder eine andere DEP dem Postfach zuweisen, wie unter Verwalten des [Kunden Schlüssels für Office 365](customer-key-manage.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="caf57-149">Later, you can either refresh the DEP or assign a different DEP to the mailbox as described in [Manage Customer Key for Office 365](customer-key-manage.md).</span></span> <span data-ttu-id="caf57-150">Jedes Postfach muss über entsprechende Lizenzen verfügen, um eine Datenausführungsverhinderung zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="caf57-150">Each mailbox must have appropriate licenses in order to assign a DEP.</span></span> <span data-ttu-id="caf57-151">Weitere Informationen zur Lizenzierung finden Sie unter [vor dem Einrichten des Kunden Schlüssels](customer-key-set-up.md#before-you-set-up-customer-key).</span><span class="sxs-lookup"><span data-stu-id="caf57-151">For more information about licensing, see [Before you set up Customer Key](customer-key-set-up.md#before-you-set-up-customer-key).</span></span>

<span data-ttu-id="caf57-152">**SharePoint Online-, OneDrive für Unternehmen-und Microsoft Teams-Dateien** Wenn Sie das Multi-Geo-Feature verwenden, können Sie bis zu einer Datenausführungsverhinderung pro Geo für Ihre Organisation erstellen.</span><span class="sxs-lookup"><span data-stu-id="caf57-152">**SharePoint Online, OneDrive for Business, and Teams files** If you're using the multi-geo feature, you can create up to one DEP per geo for your organization.</span></span> <span data-ttu-id="caf57-153">Sie können für jedes Geo unterschiedliche Kundenschlüssel verwenden.</span><span class="sxs-lookup"><span data-stu-id="caf57-153">You can use different Customer Keys for each geo.</span></span> <span data-ttu-id="caf57-154">Wenn Sie das Multi-Geo-Feature nicht verwenden, können Sie nur eine DEP pro Mandanten erstellen.</span><span class="sxs-lookup"><span data-stu-id="caf57-154">If you're not using the multi-geo feature, you can only create one DEP per tenant.</span></span> <span data-ttu-id="caf57-155">Wenn Sie die Datenausführungsverhinderung zuweisen, beginnt die Verschlüsselung automatisch, kann jedoch einige Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="caf57-155">When you assign the DEP, encryption begins automatically but can take some time to complete.</span></span> <span data-ttu-id="caf57-156">Weitere Informationen finden Sie in den Details unter [Einrichten des Kunden Schlüssels für Office 365](customer-key-set-up.md).</span><span class="sxs-lookup"><span data-stu-id="caf57-156">Refer to the details in [Set up Customer Key for Office 365](customer-key-set-up.md).</span></span>

## <a name="leaving-the-service"></a><span data-ttu-id="caf57-157">Verlassen des Diensts</span><span class="sxs-lookup"><span data-stu-id="caf57-157">Leaving the service</span></span>

<span data-ttu-id="caf57-158">Kundenschlüssel unterstützt Sie bei der Erfüllung der Compliance-Verpflichtungen, indem Sie Ihnen die Möglichkeit geben, Ihre Schlüssel zu widerrufen, wenn Sie den Office 365 Dienst verlassen.</span><span class="sxs-lookup"><span data-stu-id="caf57-158">Customer Key assists you in meeting compliance obligations by allowing you to revoke your keys when you leave the Office 365 service.</span></span> <span data-ttu-id="caf57-159">Wenn Sie Ihre Schlüssel im Rahmen des Ausscheidens des Diensts widerrufen, wird der Verfügbarkeits Schlüssel gelöscht, was zu einer kryptografischen Löschung Ihrer Daten führt.</span><span class="sxs-lookup"><span data-stu-id="caf57-159">When you revoke your keys as part of leaving the service, the availability key is deleted resulting in cryptographic deletion of your data.</span></span> <span data-ttu-id="caf57-160">Durch kryptografische Löschung wird das Risiko von Daten Remanenz verringert, die für die Erfüllung von Sicherheits-und Compliance-Verpflichtungen wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="caf57-160">Cryptographic deletion mitigates the risk of data remanence which is important for meeting both security and compliance obligations.</span></span> <span data-ttu-id="caf57-161">Informationen zum Daten Löschprozess und zur Schlüssel Sperrung finden Sie unter [REVOKE your Keys und Start the Data Purge Path Process](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).</span><span class="sxs-lookup"><span data-stu-id="caf57-161">For information about the data purge process and key revocation, see [Revoke your keys and start the data purge path process](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).</span></span>

### <a name="encryption-ciphers-used-by-customer-key"></a><span data-ttu-id="caf57-162">Vom Kundenschlüssel verwendete Verschlüsselungs Chiffren</span><span class="sxs-lookup"><span data-stu-id="caf57-162">Encryption ciphers used by Customer Key</span></span>

<span data-ttu-id="caf57-163">Der Kundenschlüssel verwendet eine Vielzahl von Verschlüsselungs Chiffren zum Verschlüsseln von Schlüsseln, wie in den folgenden Abbildungen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="caf57-163">Customer Key uses a variety of encryption ciphers to encrypt keys as shown in the following figures.</span></span>

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a><span data-ttu-id="caf57-164">Verschlüsselungs Chiffren, die zum Verschlüsseln von Schlüsseln für Exchange Online und Skype for Business verwendet werden</span><span class="sxs-lookup"><span data-stu-id="caf57-164">Encryption ciphers used to encrypt keys for Exchange Online and Skype for Business</span></span>

![Verschlüsselungs Chiffren für Exchange Online Kundenschlüssel](media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a><span data-ttu-id="caf57-166">Verschlüsselungs Chiffren, die zum Verschlüsseln von Schlüsseln für SharePoint Online-, OneDrive für Unternehmen-und Team Dateien verwendet werden</span><span class="sxs-lookup"><span data-stu-id="caf57-166">Encryption ciphers used to encrypt keys for SharePoint Online, OneDrive for Business, and Teams files</span></span>

![Verschlüsselungs Chiffren für SharePoint Online Kundenschlüssel](media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a><span data-ttu-id="caf57-168">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="caf57-168">Related articles</span></span>

- [<span data-ttu-id="caf57-169">Einrichten des Kunden Schlüssels für Office 365</span><span class="sxs-lookup"><span data-stu-id="caf57-169">Set up Customer Key for Office 365</span></span>](customer-key-set-up.md)

- [<span data-ttu-id="caf57-170">Verwalten des Kunden Schlüssels für Office 365</span><span class="sxs-lookup"><span data-stu-id="caf57-170">Manage Customer Key for Office 365</span></span>](customer-key-manage.md)

- [<span data-ttu-id="caf57-171">Rollen oder Drehen eines Kunden Schlüssels oder eines Verfügbarkeits Schlüssels</span><span class="sxs-lookup"><span data-stu-id="caf57-171">Roll or rotate a Customer Key or an availability key</span></span>](customer-key-availability-key-roll.md)

- [<span data-ttu-id="caf57-172">Informationen zum Verfügbarkeits Schlüssel</span><span class="sxs-lookup"><span data-stu-id="caf57-172">Learn about the availability key</span></span>](customer-key-availability-key-understand.md)

- [<span data-ttu-id="caf57-173">Kunden-Lockbox in Office 365</span><span class="sxs-lookup"><span data-stu-id="caf57-173">Customer Lockbox in Office 365</span></span>](customer-lockbox-requests.md)

- [<span data-ttu-id="caf57-174">Office 365-Dienstverschlüsselung</span><span class="sxs-lookup"><span data-stu-id="caf57-174">Office 365 Service Encryption</span></span>](office-365-service-encryption.md)