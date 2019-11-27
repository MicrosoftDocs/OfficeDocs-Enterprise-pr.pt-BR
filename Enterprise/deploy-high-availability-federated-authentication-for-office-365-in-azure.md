---
title: Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Resumo: configurar a autenticação federada de alta disponibilidade para sua assinatura do Office 365 no Microsoft Azure.'
ms.openlocfilehash: 0b622c895bcd6b11ee7e096ac1e39f1b6bd2dae2
ms.sourcegitcommit: fbd2f3fb297c508212baed3ee9d1ce51765cc8bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39254510"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="d6292-103">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="d6292-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

<span data-ttu-id="d6292-104">Este artigo contém links para as instruções passo-a-passo para a implantação da autenticação federada de alta disponibilidade do Microsoft Office 365 nos serviços de infraestrutura do Azure com estas máquinas virtuais:</span><span class="sxs-lookup"><span data-stu-id="d6292-104">This article has links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="d6292-105">Dois servidores proxy de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="d6292-105">Two web application proxy servers</span></span>
    
- <span data-ttu-id="d6292-106">Dois servidores dos Serviços de Federação do Active Directory (AD FS)</span><span class="sxs-lookup"><span data-stu-id="d6292-106">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="d6292-107">Dois controladores de domínio de réplica</span><span class="sxs-lookup"><span data-stu-id="d6292-107">Two replica domain controllers</span></span>
    
- <span data-ttu-id="d6292-108">Um servidor de sincronização de diretório que executa o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="d6292-108">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="d6292-109">Aqui está a configuração, com nomes de espaço reservado para cada servidor.</span><span class="sxs-lookup"><span data-stu-id="d6292-109">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="d6292-110">**Uma autenticação federada de alta disponibilidade para a infraestrutura do Office 365 no Azure**</span><span class="sxs-lookup"><span data-stu-id="d6292-110">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![A configuração final da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="d6292-112">Todas as máquinas virtuais estão em uma única rede virtual do Azure entre instalações (VNet).</span><span class="sxs-lookup"><span data-stu-id="d6292-112">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="d6292-p101">A autenticação federada de usuários individuais não confia em nenhum recurso local. No entanto, se a conexão entre instalações ficar indisponível, os controladores de domínio na VNet não receberão as atualizações das contas de usuários e grupos feitas no AD do Serviços de Domínio do Active Directory(AD DS). Para garantir que isso não aconteça, você pode configurar a alta disponibilidade para sua conexão entre instalações. Veja mais informações em [Conectividade VNet para VNet e entre instalações altamente disponível](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="d6292-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services (AD DS). To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="d6292-117">Cada par de máquinas virtuais para uma função específica está em sua própria sub-rede e conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="d6292-117">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d6292-p102">Como esta VNet está conectada à rede local, essa configuração não inclui jumpbox ou monitoramento de máquinas virtuais em uma sub-rede de gerenciamento. Veja mais informações em [Executando VMs do Windows para uma arquitetura de N camadas](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="d6292-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="d6292-120">Como resultado dessa configuração, você terá a autenticação federada para todos os usuários do Office 365, em que eles podem usar as credenciais AD DS para fazer logon em vez de sua conta do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d6292-120">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account.</span></span> <span data-ttu-id="d6292-121">A infraestrutura de autenticação federada usa um conjunto redundante de servidores que são mais facilmente implantados em serviços de infraestrutura do Azure, em vez de em sua rede de borda local.</span><span class="sxs-lookup"><span data-stu-id="d6292-121">The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="d6292-122">Lista de materiais</span><span class="sxs-lookup"><span data-stu-id="d6292-122">Bill of materials</span></span>

<span data-ttu-id="d6292-123">Essa configuração da linha de base requer o conjunto de serviços do Azure e os componentes a seguir:</span><span class="sxs-lookup"><span data-stu-id="d6292-123">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="d6292-124">Sete máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="d6292-124">Seven virtual machines</span></span>
    
- <span data-ttu-id="d6292-125">Uma rede virtual entre locais com quatro sub-redes</span><span class="sxs-lookup"><span data-stu-id="d6292-125">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="d6292-126">Quatro grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="d6292-126">Four resource groups</span></span>
    
- <span data-ttu-id="d6292-127">Três conjuntos de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="d6292-127">Three availability sets</span></span>
    
- <span data-ttu-id="d6292-128">Uma assinatura do Azure</span><span class="sxs-lookup"><span data-stu-id="d6292-128">One Azure subscription</span></span>
    
<span data-ttu-id="d6292-129">Veja as máquinas virtuais e seus respectivos tamanhos padrão para essa configuração.</span><span class="sxs-lookup"><span data-stu-id="d6292-129">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="d6292-130">**Item**</span><span class="sxs-lookup"><span data-stu-id="d6292-130">**Item**</span></span>|<span data-ttu-id="d6292-131">**Descrição da máquina virtual**</span><span class="sxs-lookup"><span data-stu-id="d6292-131">**Virtual machine description**</span></span>|<span data-ttu-id="d6292-132">**Imagem da galeria do Azure**</span><span class="sxs-lookup"><span data-stu-id="d6292-132">**Azure gallery image**</span></span>|<span data-ttu-id="d6292-133">**Tamanho padrão**</span><span class="sxs-lookup"><span data-stu-id="d6292-133">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d6292-134">1.</span><span class="sxs-lookup"><span data-stu-id="d6292-134">1.</span></span>  <br/> |<span data-ttu-id="d6292-135">Primeiro controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="d6292-135">First domain controller</span></span>  <br/> |<span data-ttu-id="d6292-136">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="d6292-136">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="d6292-137">D2</span><span class="sxs-lookup"><span data-stu-id="d6292-137">D2</span></span>  <br/> |
|<span data-ttu-id="d6292-138">2.</span><span class="sxs-lookup"><span data-stu-id="d6292-138">2.</span></span>  <br/> |<span data-ttu-id="d6292-139">Segundo controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="d6292-139">Second domain controller</span></span>  <br/> |<span data-ttu-id="d6292-140">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="d6292-140">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="d6292-141">D2</span><span class="sxs-lookup"><span data-stu-id="d6292-141">D2</span></span>  <br/> |
|<span data-ttu-id="d6292-142">3.</span><span class="sxs-lookup"><span data-stu-id="d6292-142">3.</span></span>  <br/> |<span data-ttu-id="d6292-143">Servidor do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="d6292-143">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="d6292-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="d6292-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="d6292-145">D2</span><span class="sxs-lookup"><span data-stu-id="d6292-145">D2</span></span>  <br/> |
|<span data-ttu-id="d6292-146">4.</span><span class="sxs-lookup"><span data-stu-id="d6292-146">4.</span></span>  <br/> |<span data-ttu-id="d6292-147">Primeiro servidor do AD FS</span><span class="sxs-lookup"><span data-stu-id="d6292-147">First AD FS server</span></span>  <br/> |<span data-ttu-id="d6292-148">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="d6292-148">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="d6292-149">D2</span><span class="sxs-lookup"><span data-stu-id="d6292-149">D2</span></span>  <br/> |
|<span data-ttu-id="d6292-150">5.</span><span class="sxs-lookup"><span data-stu-id="d6292-150">5.</span></span>  <br/> |<span data-ttu-id="d6292-151">Segundo servidor do AD FS</span><span class="sxs-lookup"><span data-stu-id="d6292-151">Second AD FS server</span></span>  <br/> |<span data-ttu-id="d6292-152">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="d6292-152">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="d6292-153">D2</span><span class="sxs-lookup"><span data-stu-id="d6292-153">D2</span></span>  <br/> |
|<span data-ttu-id="d6292-154">6.</span><span class="sxs-lookup"><span data-stu-id="d6292-154">6.</span></span>  <br/> |<span data-ttu-id="d6292-155">Primeiro servidor proxy de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="d6292-155">First web application proxy server</span></span>  <br/> |<span data-ttu-id="d6292-156">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="d6292-156">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="d6292-157">D2</span><span class="sxs-lookup"><span data-stu-id="d6292-157">D2</span></span>  <br/> |
|<span data-ttu-id="d6292-158">7.</span><span class="sxs-lookup"><span data-stu-id="d6292-158">7.</span></span>  <br/> |<span data-ttu-id="d6292-159">Segundo servidor proxy de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="d6292-159">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="d6292-160">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="d6292-160">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="d6292-161">D2</span><span class="sxs-lookup"><span data-stu-id="d6292-161">D2</span></span>  <br/> |
   
<span data-ttu-id="d6292-162">Para calcular os custos estimados para essa configuração, veja a [Calculadora de preços do Azure](https://azure.microsoft.com/pricing/calculator/).</span><span class="sxs-lookup"><span data-stu-id="d6292-162">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="d6292-163">Fases da implantação</span><span class="sxs-lookup"><span data-stu-id="d6292-163">Phases of deployment</span></span>

<span data-ttu-id="d6292-164">Implante essa carga de trabalho nas seguintes fases:</span><span class="sxs-lookup"><span data-stu-id="d6292-164">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="d6292-p104">[Fase 1: Configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Crie grupos de recursos, contas de armazenamento, conjuntos de disponibilidade e uma rede virtual entre locais.</span><span class="sxs-lookup"><span data-stu-id="d6292-p104">[Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="d6292-167">[Fase 2: configurar os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="d6292-167">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)</span></span> <span data-ttu-id="d6292-168">Criar e configurar os controladores de domínio de réplica e o servidor de sincronização de diretório do AD DS.</span><span class="sxs-lookup"><span data-stu-id="d6292-168">Create and configure replica AD DS domain controllers and the directory synchronization server.</span></span>
    
- <span data-ttu-id="d6292-p106">[Fase 3: Configurar os servidores do AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Crie e configure os dois servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="d6292-p106">[Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="d6292-p107">[Fase 4: Configurar proxies de aplicativos Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Crie e configure os dois servidores proxy de aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="d6292-p107">[Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="d6292-p108">[Fase 5: Configurar a autenticação federada para o Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure a autenticação federada para sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d6292-p108">[Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="d6292-p109">Estes artigos fornecem um guia descritivo, fase por fase, de uma arquitetura predefinida para criar uma autenticação federada funcional e de alta disponibilidade para o Office 365 nos serviços de infraestrutura do Azure. Lembre-se do seguinte:</span><span class="sxs-lookup"><span data-stu-id="d6292-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="d6292-177">Se você for um implementador experiente do AD FS, fique à vontade para adaptar as instruções nas fases 3 e 4 e crie o conjunto de servidores que seja mais adequado às suas necessidades. </span><span class="sxs-lookup"><span data-stu-id="d6292-177">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="d6292-178">Se você já tiver uma implantação de nuvem híbrida do Azure com uma rede virtual entre instalações, fique à vontade para adaptar ou ignorar as instruções nas etapas 1 e 2 e coloque os servidores proxy de aplicativo Web e o AD FS nas sub-redes adequadas.</span><span class="sxs-lookup"><span data-stu-id="d6292-178">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="d6292-179">Para criar um ambiente de desenvolvimento e teste ou uma prova de conceito dessa configuração, veja [Identidade federada para seu ambiente de desenvolvimento e teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d6292-179">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="d6292-180">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="d6292-180">Next step</span></span>

<span data-ttu-id="d6292-181">Inicie a configuração dessa carga de trabalho com [Fase 1: Configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="d6292-181">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
