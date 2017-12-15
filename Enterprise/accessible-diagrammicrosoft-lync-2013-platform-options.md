---
title: "Diagrama acessível - opções de plataforma do Microsoft Lync 2013"
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: "Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Lync 2013, que está disponível em diagramas técnicos."
ms.openlocfilehash: 79342a30a0391980cf16304f3615f6a7e64d51ff
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="6667c-103">Diagrama acessível - opções de plataforma do Microsoft Lync 2013</span><span class="sxs-lookup"><span data-stu-id="6667c-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="6667c-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Lync 2013, que está disponível em [Diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="6667c-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="6667c-105">Este cartaz descreve o que arquitetos e business decision tomadores de precisam saber sobre o Lync Online (Office 365) e as implantações do Lync Server e inclui:</span><span class="sxs-lookup"><span data-stu-id="6667c-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="6667c-106">Uma comparação das quatro opções de implantação diferentes: Lync Online (Office 365), Lync Online/servidor híbrido, Lync Server e Provider-Hosted Lync Server.</span><span class="sxs-lookup"><span data-stu-id="6667c-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="6667c-107">Dois cenários de exemplo de implantação do Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="6667c-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="6667c-108">Comparação entre quatro diferentes implantações para a plataforma do Lync 2013</span><span class="sxs-lookup"><span data-stu-id="6667c-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="6667c-109">Comparação fornece informações sobre cada opção de implantação nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="6667c-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="6667c-110">Uma visão geral dos recursos de implantação diferentes</span><span class="sxs-lookup"><span data-stu-id="6667c-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="6667c-111">Benefícios da implementação de cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="6667c-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="6667c-112">Requisitos de licenciamento</span><span class="sxs-lookup"><span data-stu-id="6667c-112">Licensing requirements</span></span>
    
- <span data-ttu-id="6667c-113">Tarefas necessárias de arquiteturais</span><span class="sxs-lookup"><span data-stu-id="6667c-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="6667c-114">Responsabilidades do IT Pro para implementar cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="6667c-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="6667c-115">Visão geral</span><span class="sxs-lookup"><span data-stu-id="6667c-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="6667c-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6667c-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="6667c-117">Ganho de eficiência e otimizar o custo com vários locatários planos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="6667c-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="6667c-118">O diagrama acompanha mostra Lync Online com um locatário do Azure Active Directory, o que sincroniza os nomes de conta e senhas entre o ambiente de serviços de domínio Active Directory (AD DS) no local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6667c-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="6667c-119">Descrição dos recursos e funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="6667c-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="6667c-120">Software como um serviço (SaaS).</span><span class="sxs-lookup"><span data-stu-id="6667c-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="6667c-121">Avançado conjunto que sempre está atualizado de recursos.</span><span class="sxs-lookup"><span data-stu-id="6667c-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="6667c-122">Inclui um locatário do Azure Active Directory para contas online, que pode ser usado com outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6667c-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="6667c-123">Integração de diretórios inclui sincronizando nomes de conta e senhas entre o ambiente de serviços de domínio Active Directory (AD DS) no local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6667c-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="6667c-124">Se o logon único (SSO) é um requisito, os serviços de Federação do Active Directory (AD FS) devem ser implementados.</span><span class="sxs-lookup"><span data-stu-id="6667c-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="6667c-125">Comunicação do cliente pela Internet é criptografada e autenticada.</span><span class="sxs-lookup"><span data-stu-id="6667c-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="6667c-126">Equipamento de telefone herdado, pública comutada (PSTN) rede telefônica, conectividade está disponível por meio de provedores de terceiros.</span><span class="sxs-lookup"><span data-stu-id="6667c-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="6667c-127">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="6667c-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="6667c-128">Você pode combinar os benefícios do Office 365 com uma implantação local do Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="6667c-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="6667c-p101">O diagrama acompanha mostra o Office 365 com o Lync Online onde alguns usuários estão hospedados no local e alguns usuários hospedados online. Um servidor de borda é implantados no local também é mostrado.</span><span class="sxs-lookup"><span data-stu-id="6667c-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="6667c-131">Descrição dos recursos e funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="6667c-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="6667c-132">Alguns usuários hospedados no local e alguns usuários hospedados online, mas os usuários compartilhem o mesmo domínio SIP (por exemplo, contoso.com).</span><span class="sxs-lookup"><span data-stu-id="6667c-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="6667c-133">Aproveite sua infra-estrutura existente do Lync Server 2013, incluindo as conexões para o PSTN.</span><span class="sxs-lookup"><span data-stu-id="6667c-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="6667c-134">Adicione novos usuários do Lync Online facilmente quando eles não exigem PSTN.</span><span class="sxs-lookup"><span data-stu-id="6667c-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="6667c-135">Migre do Lync local para o Lync Online ao longo do tempo, no seu calendário.</span><span class="sxs-lookup"><span data-stu-id="6667c-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="6667c-136">Integre com outros aplicativos do Office 365, incluindo o Exchange Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6667c-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="6667c-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-137">Lync Server</span></span>

<span data-ttu-id="6667c-p102">Nesta implantação, você é proprietário tudo. O diagrama acompanha mostra uma infra-estrutura do Lync Server com um ambiente de serviços de domínio Active Directory (AD DS) do local onde os usuários são hospedados no local.</span><span class="sxs-lookup"><span data-stu-id="6667c-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="6667c-140">Descrição dos recursos e funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="6667c-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="6667c-141">Planejamento de capacidade e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="6667c-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="6667c-142">Aquisição de servidor e a instalação.</span><span class="sxs-lookup"><span data-stu-id="6667c-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="6667c-143">Implantação.</span><span class="sxs-lookup"><span data-stu-id="6667c-143">Deployment.</span></span>
    
- <span data-ttu-id="6667c-144">Dimensionamento, aplicando o patch e operações.</span><span class="sxs-lookup"><span data-stu-id="6667c-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="6667c-145">Fazendo backup de dados.</span><span class="sxs-lookup"><span data-stu-id="6667c-145">Backing up data.</span></span>
    
- <span data-ttu-id="6667c-146">Mantendo o failover e recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="6667c-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="6667c-147">Conectando-se a infraestrutura do Lync Server 2013 para a PSTN.</span><span class="sxs-lookup"><span data-stu-id="6667c-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="6667c-148">Integração com o equipamento de telefone existente, como privada de comutação telefônica (PBXs).</span><span class="sxs-lookup"><span data-stu-id="6667c-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="6667c-149">Hospedado em provedor do Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="6667c-p103">Nesta implantação, o seu provedor é proprietário tudo. O diagrama acompanha mostra uma rede provedor incluindo seus servidores e equipamentos com uma conexão para um ambiente local.</span><span class="sxs-lookup"><span data-stu-id="6667c-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="6667c-152">Descrição dos recursos e funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="6667c-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="6667c-153">Planejamento de capacidade e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="6667c-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="6667c-154">Aquisição de servidor e a instalação.</span><span class="sxs-lookup"><span data-stu-id="6667c-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="6667c-155">Implantação.</span><span class="sxs-lookup"><span data-stu-id="6667c-155">Deployment.</span></span>
    
- <span data-ttu-id="6667c-156">Dimensionamento, aplicando o patch e operações.</span><span class="sxs-lookup"><span data-stu-id="6667c-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="6667c-157">Fazendo backup de dados.</span><span class="sxs-lookup"><span data-stu-id="6667c-157">Backing up data.</span></span>
    
- <span data-ttu-id="6667c-158">Mantendo o failover e recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="6667c-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="6667c-159">Integração com o equipamento de telefone existente, como privada de comutação telefônica (PBXs).</span><span class="sxs-lookup"><span data-stu-id="6667c-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="6667c-160">Além disso, o provedor pode:</span><span class="sxs-lookup"><span data-stu-id="6667c-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="6667c-161">Instale os seus servidores e equipamentos em sua própria rede com uma conexão para o seu local (linha sólida).</span><span class="sxs-lookup"><span data-stu-id="6667c-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="6667c-162">Instale os seus servidores em seu local (linha pontilhada).</span><span class="sxs-lookup"><span data-stu-id="6667c-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="6667c-163">Benefícios da implementação de cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="6667c-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="6667c-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6667c-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="6667c-165">Nenhuma carga operacional dos servidores locais ou software de servidor.</span><span class="sxs-lookup"><span data-stu-id="6667c-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="6667c-166">Recursos de comunicação do Lync Server 2013, como um serviço baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="6667c-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="6667c-167">Lync presença, mensagens instantâneas, áudio e vídeo chamar, reuniões online ricas e recursos de webconferência extensiva.</span><span class="sxs-lookup"><span data-stu-id="6667c-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="6667c-168">Usada com organizações geograficamente dispersos ou com os funcionários móveis principalmente.</span><span class="sxs-lookup"><span data-stu-id="6667c-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="6667c-169">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="6667c-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="6667c-170">Use o Lync Online para usuários remotos e integração com parceiros comerciais.</span><span class="sxs-lookup"><span data-stu-id="6667c-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="6667c-171">Facilite uma migração do Lync local para o Lync Online.</span><span class="sxs-lookup"><span data-stu-id="6667c-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="6667c-172">Suporte a sites remotos sem usar um aparelho de escritório de filial.</span><span class="sxs-lookup"><span data-stu-id="6667c-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="6667c-173">Facilidade de adição de suporte do Lync para novas aquisições de negócios.</span><span class="sxs-lookup"><span data-stu-id="6667c-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="6667c-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-174">Lync Server</span></span>

- <span data-ttu-id="6667c-175">Soluções de nuvem privada.</span><span class="sxs-lookup"><span data-stu-id="6667c-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="6667c-176">Soluções altamente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="6667c-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="6667c-177">Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados pelo Lync Online.</span><span class="sxs-lookup"><span data-stu-id="6667c-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="6667c-178">Restrições de privacidade que evitam a sincronização de contas do AD DS com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="6667c-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="6667c-179">Organizações que desejam controlar a plataforma inteira e a solução.</span><span class="sxs-lookup"><span data-stu-id="6667c-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="6667c-180">Substituição de PBX com o Enterprise Voice do Lync.</span><span class="sxs-lookup"><span data-stu-id="6667c-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="6667c-181">Hospedado em provedor do Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="6667c-182">Organizações que deseja as funcionalidades do Lync Server, mas quer terceirizar sua implantação e manutenção.</span><span class="sxs-lookup"><span data-stu-id="6667c-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="6667c-183">Soluções baseadas no provedor.</span><span class="sxs-lookup"><span data-stu-id="6667c-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="6667c-184">Soluções altamente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="6667c-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="6667c-185">Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados pelo Lync Online.</span><span class="sxs-lookup"><span data-stu-id="6667c-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="6667c-186">Substituição de PBX com o Enterprise Voice do Lync.</span><span class="sxs-lookup"><span data-stu-id="6667c-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="6667c-187">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="6667c-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="6667c-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6667c-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="6667c-189">Modelo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="6667c-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="6667c-190">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="6667c-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="6667c-p104">Office 365 — Modelo de assinatura. Não há licenças adicionais necessárias.</span><span class="sxs-lookup"><span data-stu-id="6667c-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="6667c-193">Local — Se aplicam todas as licenças de local.</span><span class="sxs-lookup"><span data-stu-id="6667c-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="6667c-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-194">Lync Server</span></span>

- <span data-ttu-id="6667c-195">Sistema operacional do servidor</span><span class="sxs-lookup"><span data-stu-id="6667c-195">Server Operating System</span></span>
    
- <span data-ttu-id="6667c-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6667c-196">SQL Server</span></span>
    
- <span data-ttu-id="6667c-197">Licença de servidor do Lync 2013</span><span class="sxs-lookup"><span data-stu-id="6667c-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="6667c-198">Licença de acesso de cliente do Lync 2013</span><span class="sxs-lookup"><span data-stu-id="6667c-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="6667c-199">Hospedado em provedor do Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="6667c-200">Custos se baseiam no contrato com seu provedor de soluções do Lync.</span><span class="sxs-lookup"><span data-stu-id="6667c-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="6667c-201">Tarefas de arquitetura</span><span class="sxs-lookup"><span data-stu-id="6667c-201">Architecture tasks</span></span>

<span data-ttu-id="6667c-202">Esta seção lista as tarefas de arquiteturais para cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="6667c-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="6667c-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6667c-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="6667c-204">Design e plano de sincronização de diretórios.</span><span class="sxs-lookup"><span data-stu-id="6667c-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="6667c-205">Certifique-se de capacidade de rede e a disponibilidade por meio de firewalls, servidores proxy, gateways e em links de WAN.</span><span class="sxs-lookup"><span data-stu-id="6667c-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="6667c-206">Adquira certificados SSL de terceiros para fornecer segurança da empresa para ofertas de serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="6667c-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="6667c-207">Decida se deseja conectar ao Office 365 com protocolo IP versão 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="6667c-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="6667c-208">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="6667c-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="6667c-209">Além das tarefas para o Office 365 e o local de ambientes:</span><span class="sxs-lookup"><span data-stu-id="6667c-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="6667c-210">Determine quanto integração do recurso que você deseja usar com o local e as versões online do Exchange Server e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6667c-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="6667c-211">Se for necessário, determine qual dispositivo do servidor de proxy será usado para solicitações do Office 365.</span><span class="sxs-lookup"><span data-stu-id="6667c-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="6667c-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-212">Lync Server</span></span>

<span data-ttu-id="6667c-213">Projete o ambiente do Lync em um ambiente local existente:</span><span class="sxs-lookup"><span data-stu-id="6667c-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="6667c-214">Topologia do Lync para central e filiais.</span><span class="sxs-lookup"><span data-stu-id="6667c-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="6667c-215">Hardware de servidor, incluindo a virtualização.</span><span class="sxs-lookup"><span data-stu-id="6667c-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="6667c-216">Integração com serviços de domínio do Active Directory (AD DS) e DNS.</span><span class="sxs-lookup"><span data-stu-id="6667c-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="6667c-217">Balanceamento de carga para os pools do Lync server.</span><span class="sxs-lookup"><span data-stu-id="6667c-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="6667c-218">Failover e recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="6667c-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="6667c-219">Hospedado em provedor do Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="6667c-220">Para uma instalação baseada em nuvem, determine a conexão de rede do provedor de serviços.</span><span class="sxs-lookup"><span data-stu-id="6667c-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="6667c-221">Para uma instalação local, determine o posicionamento de servidores do Lync do provedor em sua rede.</span><span class="sxs-lookup"><span data-stu-id="6667c-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="6667c-222">Para os dois tipos, determine a integração com o AD DS e seu equipamento de PBX.</span><span class="sxs-lookup"><span data-stu-id="6667c-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="6667c-223">Responsabilidades do IT Pro</span><span class="sxs-lookup"><span data-stu-id="6667c-223">IT Pro responsibilities</span></span>

<span data-ttu-id="6667c-224">Esta seção lista as responsabilidades profissionais de TI para cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="6667c-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="6667c-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="6667c-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="6667c-226">Implantar e gerenciar o Lync Online (Office 365):</span><span class="sxs-lookup"><span data-stu-id="6667c-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="6667c-227">Implemente o plano de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="6667c-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="6667c-228">Planejar e implementar os registros DNS internos e externos e roteamento.</span><span class="sxs-lookup"><span data-stu-id="6667c-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="6667c-229">Configure seu proxy ou firewall para o endereço IP do Office 365 e requisitos de URL.</span><span class="sxs-lookup"><span data-stu-id="6667c-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="6667c-230">Administre contas de usuário e configurações do Lync Online.</span><span class="sxs-lookup"><span data-stu-id="6667c-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="6667c-231">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="6667c-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="6667c-232">Além das tarefas para o Office 365 e o local de ambientes:</span><span class="sxs-lookup"><span data-stu-id="6667c-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="6667c-233">Configure o dispositivo de servidor proxy, se necessário.</span><span class="sxs-lookup"><span data-stu-id="6667c-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="6667c-234">Configure a integração de recursos com o local e versões online do Exchange Server e do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6667c-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="6667c-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-235">Lync Server</span></span>

<span data-ttu-id="6667c-236">Implantar e gerenciar o Lync Server em um ambiente local:</span><span class="sxs-lookup"><span data-stu-id="6667c-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="6667c-237">Provisione os servidores.</span><span class="sxs-lookup"><span data-stu-id="6667c-237">Provision the servers.</span></span>
    
- <span data-ttu-id="6667c-238">Implante a topologia do Lync.</span><span class="sxs-lookup"><span data-stu-id="6667c-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="6667c-239">Atualize servidores do Lync.</span><span class="sxs-lookup"><span data-stu-id="6667c-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="6667c-240">Adicionar ou remover servidores de topologia conforme necessário com base na utilização.</span><span class="sxs-lookup"><span data-stu-id="6667c-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="6667c-241">Implemente o ambiente de recuperação de desastres e failover.</span><span class="sxs-lookup"><span data-stu-id="6667c-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="6667c-242">Hospedado em provedor do Lync Server</span><span class="sxs-lookup"><span data-stu-id="6667c-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="6667c-243">Trabalhar com o provedor para:</span><span class="sxs-lookup"><span data-stu-id="6667c-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="6667c-244">Integre o Lync Server em sua rede.</span><span class="sxs-lookup"><span data-stu-id="6667c-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="6667c-245">Integre o Lync Server com outros produtos da Microsoft ou soluções personalizadas.</span><span class="sxs-lookup"><span data-stu-id="6667c-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="6667c-246">Monitorar a adesão com um contrato de nível de serviço (SLA) do provedor.</span><span class="sxs-lookup"><span data-stu-id="6667c-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="6667c-247">Dois cenários de exemplo de implantação do Lync 2013</span><span class="sxs-lookup"><span data-stu-id="6667c-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="6667c-248">Componentes de sincronização de diretórios no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="6667c-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="6667c-249">Implantar o Office 365 componentes de sincronização de diretório no Windows Azure é mais rápido devido a capacidade de implantar máquinas virtuais sob demanda.</span><span class="sxs-lookup"><span data-stu-id="6667c-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="6667c-250">O diagrama acompanha mostra Lync Online com um locatário do Azure Active Directory, o que sincroniza os nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6667c-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="6667c-p105">**Somente servidor de sincronização de diretório**. Em vez de Implantando o servidor de sincronização de diretório de 64 bits em seu ambiente local, você pode provisionar uma máquina virtual no Azure pela Internet.</span><span class="sxs-lookup"><span data-stu-id="6667c-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="6667c-p106">**Sincronização de diretórios + AD FS**. Essa opção permite que você ofereça suporte a identidades do Office 365 federado (SSO) sem adicionar hardware à infraestrutura local. Ele também fornece resiliência se o ambiente do Active Directory local não está disponível. Os recursos desta opção incluem:</span><span class="sxs-lookup"><span data-stu-id="6667c-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="6667c-257">Componentes de integração de diretório são executados como máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="6667c-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="6667c-258">O AD FS é publicado na Internet por meio de proxies do AD FS executando como máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="6667c-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="6667c-259">Tráfego de autenticação de cliente, para usuários que estão se conectando de qualquer local, é tratado por servidores AD FS e proxies que são implantados como máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="6667c-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="6667c-260">Integração do Lync com o Exchange e SharePoint no Office 365</span><span class="sxs-lookup"><span data-stu-id="6667c-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="6667c-261">Lync Server com o Exchange Online e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6667c-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="6667c-262">O diagrama acompanha mostra o que Office 365 com o Exchange Online e SharePoint Online conectados a um farm do Lync Server 2013 local.</span><span class="sxs-lookup"><span data-stu-id="6667c-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="6667c-263">As vantagens dessa implantação permitem que você:</span><span class="sxs-lookup"><span data-stu-id="6667c-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="6667c-264">Use o conjunto completo de recursos do Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="6667c-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="6667c-265">Aproveite o equipamento de telefone local existente, como PBXs.</span><span class="sxs-lookup"><span data-stu-id="6667c-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="6667c-266">Use o Exchange Online para email, diminuir a carga de armazenamento e de servidores de email local.</span><span class="sxs-lookup"><span data-stu-id="6667c-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="6667c-267">Use o SharePoint Online para colaboração, a descarga a tarefa de manutenção de servidores locais do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6667c-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="6667c-268">Uso o Lync, Exchange e SharePoint integrado de recursos, incluindo Unified Messaging (UM) no Office 365.</span><span class="sxs-lookup"><span data-stu-id="6667c-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="6667c-269">Exchange Server com o Lync Online</span><span class="sxs-lookup"><span data-stu-id="6667c-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="6667c-270">O diagrama acompanha mostra o que Office 365 com o Lync Online conectados a um farm de servidor Exchange local.</span><span class="sxs-lookup"><span data-stu-id="6667c-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="6667c-271">As vantagens dessa implantação permitem que você:</span><span class="sxs-lookup"><span data-stu-id="6667c-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="6667c-272">Aproveite a infra-estrutura existente do Exchange.</span><span class="sxs-lookup"><span data-stu-id="6667c-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="6667c-273">Use o Lync Online para os recursos de conferência, mensagens instantâneas e presença.</span><span class="sxs-lookup"><span data-stu-id="6667c-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

