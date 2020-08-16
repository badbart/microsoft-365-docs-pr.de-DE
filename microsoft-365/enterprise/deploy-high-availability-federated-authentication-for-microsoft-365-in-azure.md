---
title: Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Microsoft 365 in Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Zusammenfassung: Konfigurieren der Verbundauthentifizierung mit hoher Verfügbarkeit für Ihr Microsoft 365-Abonnement in Microsoft Azure.'
ms.openlocfilehash: abe01445b8963dcdc5693b45a680e273f5084446
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690651"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a><span data-ttu-id="644bb-103">Bereitstellen der Verbundauthentifizierung mit Hochverfügbarkeit für Microsoft 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="644bb-103">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>

<span data-ttu-id="644bb-104">Dieser Artikel enthält Links zu den schrittweisen Anleitungen für die Bereitstellung der Verbundauthentifizierung mit hoher Verfügbarkeit für Microsoft Microsoft 365 in Azure-Infrastrukturdiensten mit den folgenden virtuellen Computern:</span><span class="sxs-lookup"><span data-stu-id="644bb-104">This article has links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Microsoft 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="644bb-105">Zwei Webanwendungsproxy-Server</span><span class="sxs-lookup"><span data-stu-id="644bb-105">Two web application proxy servers</span></span>
    
- <span data-ttu-id="644bb-106">Zwei Active Directory-Verbunddienste (AD FS)</span><span class="sxs-lookup"><span data-stu-id="644bb-106">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="644bb-107">Zwei replizierte Domänencontroller</span><span class="sxs-lookup"><span data-stu-id="644bb-107">Two replica domain controllers</span></span>
    
- <span data-ttu-id="644bb-108">Ein Verzeichnissynchronisierungsserver, auf dem Azure AD Connect ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="644bb-108">One directory synchronization server running Azure AD Connect</span></span>
    
<span data-ttu-id="644bb-109">Nachfolgend sehen Sie die Konfiguration mit Platzhalternamen für jeden Server.</span><span class="sxs-lookup"><span data-stu-id="644bb-109">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="644bb-110">**Eine Verbundauthentifizierung mit hoher Verfügbarkeit für Microsoft 365-Infrastruktur in Azure**</span><span class="sxs-lookup"><span data-stu-id="644bb-110">**A high availability federated authentication for Microsoft 365 infrastructure in Azure**</span></span>

![Die endgültige Konfiguration der Microsoft 365-Verbund Authentifizierungsinfrastruktur mit hoher Verfügbarkeit in Azure](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="644bb-112">Alle virtuellen Computer befinden sich in einem einzigen standortübergreifenden virtuellen Azure-Netzwerk (VNet).</span><span class="sxs-lookup"><span data-stu-id="644bb-112">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="644bb-p101">Für die Verbundauthentifizierung einzelner Benutzer ist kein Rückgriff auf lokale Ressourcen erforderlich. Sollte die standortübergreifende Verbindung jedoch ausfallen, empfangen die Domänencontroller im VNet keine im lokalen AD DS (Active Directory Domain Services) vorgenommenen Updates an Benutzerkonten und Gruppen. Zur Vermeidung eines solchen Szenarios können Sie Hochverfügbarkeit für die standortübergreifende Verbindung konfigurieren. Weitere Informationen finden Sie unter [Standortübergreifende Verbindungen und VNet-zu-VNet-Verbindungen mit hoher Verfügbarkeit](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable).</span><span class="sxs-lookup"><span data-stu-id="644bb-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services (AD DS). To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="644bb-117">Jedes Paar virtuelle Computer für eine bestimmte Rolle befindet sich in einem eigenen Subnetz und einer eigenen Verfügbarkeitsgruppe.</span><span class="sxs-lookup"><span data-stu-id="644bb-117">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="644bb-p102">Da dieses VNet mit dem lokalen Netzwerk verbunden ist, umfasst diese Konfiguration keinen virtuellen Jumpbox- oder Überwachungscomputer in einem Verwaltungssubnetz. Weitere Informationen finden Sie unter [Ausführen von virtuellen Windows-Computern für eine Architektur mit N-Ebenen](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="644bb-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="644bb-120">Das Ergebnis dieser Konfiguration besteht darin, dass Sie eine Verbundauthentifizierung für alle Microsoft 365-Benutzer haben, in der Sie Ihre AD DS Anmeldeinformationen verwenden können, um sich anstelle Ihres Microsoft 365-Kontos anzumelden.</span><span class="sxs-lookup"><span data-stu-id="644bb-120">The result of this configuration is that you will have federated authentication for all of your Microsoft 365 users, in which they can use their AD DS credentials to sign in rather than their Microsoft 365 account.</span></span> <span data-ttu-id="644bb-121">Die Verbundauthentifizierungsinfrastruktur nutzt einen redundanten Satz von Servern, die in den Azure-Infrastrukturdiensten bereitgestellt sind, nicht in Ihrem lokalen Umkreisnetzwerk. Das ist eine deutlich einfacher zu implementierende Konstellation.</span><span class="sxs-lookup"><span data-stu-id="644bb-121">The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="644bb-122">Erforderliche Komponenten</span><span class="sxs-lookup"><span data-stu-id="644bb-122">Bill of materials</span></span>

<span data-ttu-id="644bb-123">Diese geplante Konfiguration erfordert den folgenden Satz von Azure-Diensten und Komponenten:</span><span class="sxs-lookup"><span data-stu-id="644bb-123">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="644bb-124">Sieben virtuelle Computer</span><span class="sxs-lookup"><span data-stu-id="644bb-124">Seven virtual machines</span></span>
    
- <span data-ttu-id="644bb-125">Ein standortübergreifendes virtuelles Netzwerk mit vier Subnetzen</span><span class="sxs-lookup"><span data-stu-id="644bb-125">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="644bb-126">Vier Ressourcengruppen</span><span class="sxs-lookup"><span data-stu-id="644bb-126">Four resource groups</span></span>
    
- <span data-ttu-id="644bb-127">Drei Verfügbarkeitsgruppen.</span><span class="sxs-lookup"><span data-stu-id="644bb-127">Three availability sets</span></span>
    
- <span data-ttu-id="644bb-128">Ein Azure-Abonnement</span><span class="sxs-lookup"><span data-stu-id="644bb-128">One Azure subscription</span></span>
    
<span data-ttu-id="644bb-129">Nachfolgend sehen Sie die virtuellen Computer und ihre Standardgrößen für diese Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="644bb-129">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="644bb-130">**Element**</span><span class="sxs-lookup"><span data-stu-id="644bb-130">**Item**</span></span>|<span data-ttu-id="644bb-131">**Beschreibung des virtuellen Computers**</span><span class="sxs-lookup"><span data-stu-id="644bb-131">**Virtual machine description**</span></span>|<span data-ttu-id="644bb-132">**Azure-Katalogbild**</span><span class="sxs-lookup"><span data-stu-id="644bb-132">**Azure gallery image**</span></span>|<span data-ttu-id="644bb-133">**Standardgröße**</span><span class="sxs-lookup"><span data-stu-id="644bb-133">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="644bb-134">1.</span><span class="sxs-lookup"><span data-stu-id="644bb-134">1.</span></span>  <br/> |<span data-ttu-id="644bb-135">Erster Domänencontroller</span><span class="sxs-lookup"><span data-stu-id="644bb-135">First domain controller</span></span>  <br/> |<span data-ttu-id="644bb-136">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="644bb-136">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="644bb-137">D2</span><span class="sxs-lookup"><span data-stu-id="644bb-137">D2</span></span>  <br/> |
|<span data-ttu-id="644bb-138">2.</span><span class="sxs-lookup"><span data-stu-id="644bb-138">2.</span></span>  <br/> |<span data-ttu-id="644bb-139">Zweiter Domänencontroller</span><span class="sxs-lookup"><span data-stu-id="644bb-139">Second domain controller</span></span>  <br/> |<span data-ttu-id="644bb-140">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="644bb-140">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="644bb-141">D2</span><span class="sxs-lookup"><span data-stu-id="644bb-141">D2</span></span>  <br/> |
|<span data-ttu-id="644bb-142">3.</span><span class="sxs-lookup"><span data-stu-id="644bb-142">3.</span></span>  <br/> |<span data-ttu-id="644bb-143">Azure AD Connect-Server</span><span class="sxs-lookup"><span data-stu-id="644bb-143">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="644bb-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="644bb-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="644bb-145">D2</span><span class="sxs-lookup"><span data-stu-id="644bb-145">D2</span></span>  <br/> |
|<span data-ttu-id="644bb-146">4.</span><span class="sxs-lookup"><span data-stu-id="644bb-146">4.</span></span>  <br/> |<span data-ttu-id="644bb-147">Erster AD FS-Server
</span><span class="sxs-lookup"><span data-stu-id="644bb-147">First AD FS server</span></span>  <br/> |<span data-ttu-id="644bb-148">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="644bb-148">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="644bb-149">D2</span><span class="sxs-lookup"><span data-stu-id="644bb-149">D2</span></span>  <br/> |
|<span data-ttu-id="644bb-150">5.</span><span class="sxs-lookup"><span data-stu-id="644bb-150">5.</span></span>  <br/> |<span data-ttu-id="644bb-151">Zweiter AD FS-Server
</span><span class="sxs-lookup"><span data-stu-id="644bb-151">Second AD FS server</span></span>  <br/> |<span data-ttu-id="644bb-152">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="644bb-152">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="644bb-153">D2</span><span class="sxs-lookup"><span data-stu-id="644bb-153">D2</span></span>  <br/> |
|<span data-ttu-id="644bb-154">6.</span><span class="sxs-lookup"><span data-stu-id="644bb-154">6.</span></span>  <br/> |<span data-ttu-id="644bb-155">Erster Webanwendungsproxy-Server
</span><span class="sxs-lookup"><span data-stu-id="644bb-155">First web application proxy server</span></span>  <br/> |<span data-ttu-id="644bb-156">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="644bb-156">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="644bb-157">D2</span><span class="sxs-lookup"><span data-stu-id="644bb-157">D2</span></span>  <br/> |
|<span data-ttu-id="644bb-158">7.</span><span class="sxs-lookup"><span data-stu-id="644bb-158">7.</span></span>  <br/> |<span data-ttu-id="644bb-159">Zweiter Webanwendungsproxy-Server
</span><span class="sxs-lookup"><span data-stu-id="644bb-159">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="644bb-160">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="644bb-160">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="644bb-161">D2</span><span class="sxs-lookup"><span data-stu-id="644bb-161">D2</span></span>  <br/> |
   
<span data-ttu-id="644bb-162">Um die geschätzten Kosten für diese Konfiguration zu berechnen, finden Sie unter [Azure-Preisrechner](https://azure.microsoft.com/pricing/calculator/) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="644bb-162">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="644bb-163">Phasen der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="644bb-163">Phases of deployment</span></span>

<span data-ttu-id="644bb-164">Sie stellen diese Arbeitslast in den folgenden Phasen bereit:</span><span class="sxs-lookup"><span data-stu-id="644bb-164">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="644bb-p104">[Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Erstellen von Ressourcengruppen, Speicherkonten, Verfügbarkeitsgruppen und einem standortübergreifenden virtuellen Netzwerk.</span><span class="sxs-lookup"><span data-stu-id="644bb-p104">[Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="644bb-167">[Phase 2: Konfigurieren von Domänencontrollern](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="644bb-167">[Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="644bb-168">Erstellen und Konfigurieren Sie AD DS-Replikatdomänencontroller und den Verzeichnissynchronisierungsserver.</span><span class="sxs-lookup"><span data-stu-id="644bb-168">Create and configure replica AD DS domain controllers and the directory synchronization server.</span></span>
    
- <span data-ttu-id="644bb-p106">[Phase 3: Konfigurieren von AD FS-Servern](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Erstellen und Konfigurieren der beiden AD FS-Server.</span><span class="sxs-lookup"><span data-stu-id="644bb-p106">[Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="644bb-p107">[Phase 4: Konfigurieren von Webanwendungsproxys](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Erstellen und Konfigurieren der beiden Webanwendungsproxy-Server.</span><span class="sxs-lookup"><span data-stu-id="644bb-p107">[Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="644bb-173">[Phase 5: Konfigurieren der Verbundauthentifizierung für Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span><span class="sxs-lookup"><span data-stu-id="644bb-173">[Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span></span> <span data-ttu-id="644bb-174">Konfigurieren Sie die Verbundauthentifizierung für Ihr Microsoft 365-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="644bb-174">Configure federated authentication for your Microsoft 365 subscription.</span></span>
    
<span data-ttu-id="644bb-175">In diesen Artikeln wird eine vordefinierte, phasenweise Anleitung für eine vordefinierte Architektur bereitgestellt, um eine funktionsfähige Verbundauthentifizierung mit hoher Verfügbarkeit für Microsoft 365 in Azure-Infrastrukturdiensten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="644bb-175">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Microsoft 365 in Azure infrastructure services.</span></span> <span data-ttu-id="644bb-176">Denken Sie dabei an Folgendes:</span><span class="sxs-lookup"><span data-stu-id="644bb-176">Keep the following in mind:</span></span>
  
- <span data-ttu-id="644bb-177">Wenn Sie ein erfahrener AD FS-Implementierer sind, können Sie die Anweisungen in den Phasen 3 und 4 entsprechend anpassen und eine Gruppe von Servern erstellen, die Ihren Anforderungen am besten entspricht. </span><span class="sxs-lookup"><span data-stu-id="644bb-177">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="644bb-178">Wenn Sie bereits über eine vorhandene Azure-Hybridcloudbereitstellung mit einem vorhandenen standortübergreifenden virtuellen Netzwerk verfügen, können Sie die Anweisungen in den Phasen 1 und 2 entsprechend anpassen oder überspringen und die AD FS-Server und die Webanwendungsproxy-Server in den entsprechenden Subnetzen platzieren.</span><span class="sxs-lookup"><span data-stu-id="644bb-178">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="644bb-179">Informationen zum Erstellen einer Entwicklungs-oder Testumgebung oder eines Machbarkeits Tests für diese Konfiguration finden Sie unter [Federated Identity for your Microsoft 365 dev/Test Environment](federated-identity-for-your-microsoft-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="644bb-179">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Microsoft 365 dev/test environment](federated-identity-for-your-microsoft-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="644bb-180">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="644bb-180">Next step</span></span>

<span data-ttu-id="644bb-181">Starten Sie die Konfiguration dieser Arbeitslast mit [Phase 1: Konfigurieren von Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="644bb-181">Start the configuration of this workload with [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  