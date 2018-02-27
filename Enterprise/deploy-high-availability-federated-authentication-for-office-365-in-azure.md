---
title: "Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "Resumo: configurar a autenticação federada de alta disponibilidade para sua assinatura do Office 365 no Microsoft Azure."
ms.openlocfilehash: 6bbc53eae616fca4c044b7b4c24314191d9be22a
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="5f0d4-103">Implantar a autenticação federada de alta disponibilidade para o Office 365 no Azure</span><span class="sxs-lookup"><span data-stu-id="5f0d4-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="5f0d4-104">**Resumo:** configurar a autenticação federada de alta disponibilidade para sua assinatura do Office 365 no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="5f0d4-105">Este artigo contém links para as instruções passo a passo de implantação da autenticação federada de alta disponibilidade do Microsoft Office 365 nos serviços de infraestrutura do Azure com estas máquinas virtuais:</span><span class="sxs-lookup"><span data-stu-id="5f0d4-105">This article contains links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="5f0d4-106">Dois servidores proxy de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="5f0d4-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="5f0d4-107">Dois servidores dos Serviços de Federação do Active Directory (AD FS)</span><span class="sxs-lookup"><span data-stu-id="5f0d4-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="5f0d4-108">Dois controladores de domínio de réplica</span><span class="sxs-lookup"><span data-stu-id="5f0d4-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="5f0d4-109">Um servidor de sincronização (DirSync) de diretório que executa o Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="5f0d4-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="5f0d4-110">Aqui está a configuração, com nomes de espaço reservado para cada servidor.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="5f0d4-111">**Uma autenticação federada de alta disponibilidade para a infraestrutura do Office 365 no Azure**</span><span class="sxs-lookup"><span data-stu-id="5f0d4-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![A configuração final da infraestrutura de autenticação federada de alta disponibilidade para o Office 365 no Azure](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="5f0d4-113">Todas as máquinas virtuais estão em uma única rede virtual do Azure entre instalações (VNet).</span><span class="sxs-lookup"><span data-stu-id="5f0d4-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5f0d4-p101">A autenticação federada de usuários individuais não confia em nenhum recurso local. No entanto, se a conexão entre instalações ficar indisponível, os controladores de domínio na VNet não receberão as atualizações das contas de usuários e grupos feitas no AD do Windows Server local. Para garantir que isso não aconteça, configure a alta disponibilidade para sua conexão entre instalações. Veja mais informações em [Conectividade VNet para VNet e entre instalações de alta disponibilidade](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="5f0d4-118">Cada par de máquinas virtuais para uma função específica está em sua própria sub-rede e conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5f0d4-p102">Como esta VNet está conectada à rede local, a configuração não incluirá jumpbox ou monitoramento de máquinas virtuais em uma sub-rede de gerenciamento. Veja mais informações em [Executando VMs do Windows para uma arquitetura de N camadas](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="5f0d4-p103">Como resultado dessa configuração, você terá a autenticação federada para todos os usuários do Office 365, em que eles podem usar as credenciais do Active Directory do Windows Server para fazer logon em vez da conta do Office 365 deles. A infraestrutura de autenticação federada usa um conjunto redundante de servidores que são mais facilmente implantados em serviços de infraestrutura do Azure, em vez de em sua rede de borda local.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="5f0d4-123">Lista de materiais</span><span class="sxs-lookup"><span data-stu-id="5f0d4-123">Bill of materials</span></span>

<span data-ttu-id="5f0d4-124">Essa configuração da linha de base requer o conjunto de serviços do Azure e os componentes a seguir:</span><span class="sxs-lookup"><span data-stu-id="5f0d4-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="5f0d4-125">Sete máquinas virtuais</span><span class="sxs-lookup"><span data-stu-id="5f0d4-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="5f0d4-126">Uma rede virtual entre locais com quatro sub-redes</span><span class="sxs-lookup"><span data-stu-id="5f0d4-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="5f0d4-127">Quatro grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="5f0d4-127">Four resource groups</span></span>
    
- <span data-ttu-id="5f0d4-128">Três conjuntos de disponibilidade</span><span class="sxs-lookup"><span data-stu-id="5f0d4-128">Three availability sets</span></span>
    
- <span data-ttu-id="5f0d4-129">Uma assinatura do Azure</span><span class="sxs-lookup"><span data-stu-id="5f0d4-129">One Azure subscription</span></span>
    
<span data-ttu-id="5f0d4-130">Veja as máquinas virtuais e seus respectivos tamanhos padrão para essa configuração.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="5f0d4-131">**Item**</span><span class="sxs-lookup"><span data-stu-id="5f0d4-131">**Item**</span></span>|<span data-ttu-id="5f0d4-132">**Descrição da máquina virtual**</span><span class="sxs-lookup"><span data-stu-id="5f0d4-132">**Virtual machine description**</span></span>|<span data-ttu-id="5f0d4-133">**Imagem da galeria do Azure**</span><span class="sxs-lookup"><span data-stu-id="5f0d4-133">**Azure gallery image**</span></span>|<span data-ttu-id="5f0d4-134">**Tamanho padrão**</span><span class="sxs-lookup"><span data-stu-id="5f0d4-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="5f0d4-135">1.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-135">1.</span></span>  <br/> |<span data-ttu-id="5f0d4-136">Primeiro controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="5f0d4-136">First domain controller</span></span>  <br/> |<span data-ttu-id="5f0d4-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5f0d4-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5f0d4-138">D2</span><span class="sxs-lookup"><span data-stu-id="5f0d4-138">D2</span></span>  <br/> |
|<span data-ttu-id="5f0d4-139">2.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-139">2.</span></span>  <br/> |<span data-ttu-id="5f0d4-140">Segundo controlador de domínio</span><span class="sxs-lookup"><span data-stu-id="5f0d4-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="5f0d4-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5f0d4-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5f0d4-142">D2</span><span class="sxs-lookup"><span data-stu-id="5f0d4-142">D2</span></span>  <br/> |
|<span data-ttu-id="5f0d4-143">3.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-143">3.</span></span>  <br/> |<span data-ttu-id="5f0d4-144">Servidor do Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="5f0d4-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="5f0d4-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5f0d4-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5f0d4-146">D2</span><span class="sxs-lookup"><span data-stu-id="5f0d4-146">D2</span></span>  <br/> |
|<span data-ttu-id="5f0d4-147">4.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-147">4.</span></span>  <br/> |<span data-ttu-id="5f0d4-148">Primeiro servidor do AD FS</span><span class="sxs-lookup"><span data-stu-id="5f0d4-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="5f0d4-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5f0d4-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5f0d4-150">D2</span><span class="sxs-lookup"><span data-stu-id="5f0d4-150">D2</span></span>  <br/> |
|<span data-ttu-id="5f0d4-151">5.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-151">5.</span></span>  <br/> |<span data-ttu-id="5f0d4-152">Segundo servidor do AD FS</span><span class="sxs-lookup"><span data-stu-id="5f0d4-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="5f0d4-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5f0d4-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5f0d4-154">D2</span><span class="sxs-lookup"><span data-stu-id="5f0d4-154">D2</span></span>  <br/> |
|<span data-ttu-id="5f0d4-155">6.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-155">6.</span></span>  <br/> |<span data-ttu-id="5f0d4-156">Primeiro servidor proxy de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="5f0d4-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="5f0d4-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5f0d4-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5f0d4-158">D2</span><span class="sxs-lookup"><span data-stu-id="5f0d4-158">D2</span></span>  <br/> |
|<span data-ttu-id="5f0d4-159">7.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-159">7.</span></span>  <br/> |<span data-ttu-id="5f0d4-160">Segundo servidor proxy de aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="5f0d4-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="5f0d4-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="5f0d4-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="5f0d4-162">D2</span><span class="sxs-lookup"><span data-stu-id="5f0d4-162">D2</span></span>  <br/> |
   
<span data-ttu-id="5f0d4-163">Para calcular os custos estimados para essa configuração, veja a [Calculadora de preços do Azure](https://azure.microsoft.com/pricing/calculator/).</span><span class="sxs-lookup"><span data-stu-id="5f0d4-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="5f0d4-164">Fases da implantação</span><span class="sxs-lookup"><span data-stu-id="5f0d4-164">Phases of deployment</span></span>

<span data-ttu-id="5f0d4-165">Implante essa carga de trabalho nas seguintes fases:</span><span class="sxs-lookup"><span data-stu-id="5f0d4-165">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="5f0d4-p104">[Autenticação federada de alta disponibilidade, Fase 1: configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Crie grupos de recursos, contas de armazenamento, conjuntos de disponibilidade e uma rede virtual entre locais.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p104">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="5f0d4-p105">[Autenticação federada de alta disponibilidade Fase 2: configurar os controladores de domínio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Crie e configure os controladores de domínio do Windows Server Active Directory (AD) e o DirSync server.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="5f0d4-p106">[Autenticação federada de alta disponibilidade Fase 3: configurar servidores do AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Crie e configure os dois servidores do AD FS.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p106">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="5f0d4-p107">[Autenticação federada de alta disponibilidade Fase 4: configurar proxies de aplicativos Web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Crie e configure os dois servidores proxy de aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p107">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="5f0d4-p108">[Autenticação federada de alta disponibilidade, Fase 5: configurar a autenticação federada para Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure a autenticação federada para sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p108">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="5f0d4-p109">Estes artigos fornecem um guia descritivo, fase por fase, de uma arquitetura predefinida para criar uma autenticação federada funcional e de alta disponibilidade para o Office 365 nos serviços de infraestrutura do Azure. Lembre-se do seguinte:</span><span class="sxs-lookup"><span data-stu-id="5f0d4-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="5f0d4-178">Se você for um implementador experiente do AD FS, fique à vontade para adaptar as instruções nas fases 3 e 4 e crie o conjunto de servidores que seja mais adequado às suas necessidades. </span><span class="sxs-lookup"><span data-stu-id="5f0d4-178">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="5f0d4-179">Se você já tiver uma implantação de nuvem híbrida do Azure com uma rede virtual entre instalações, fique à vontade para adaptar ou ignorar as instruções nas etapas 1 e 2 e coloque os servidores proxy de aplicativo Web e o AD FS nas sub-redes adequadas.</span><span class="sxs-lookup"><span data-stu-id="5f0d4-179">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="5f0d4-180">Para criar um ambiente de desenvolvimento e teste ou uma prova de conceito dessa configuração, veja [Identidade federada para seu ambiente de desenvolvimento e teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5f0d4-180">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="5f0d4-181">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="5f0d4-181">Next step</span></span>

<span data-ttu-id="5f0d4-182">Inicie a configuração dessa carga de trabalho com [Autenticação federada de alta disponibilidade Fase 1: Configurar o Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="5f0d4-182">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
> [!TIP]
> <span data-ttu-id="5f0d4-183">Para um conjunto de arquivos implantar mais rapidamente sua autenticação federada de alta disponibilidade para o Office 365 no Azure, confira [Autenticação federada do Office 365 no Kit de implantação do Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="5f0d4-183">For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
 

