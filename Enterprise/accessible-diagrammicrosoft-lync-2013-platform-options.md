---
title: Diagrama acessível – opções da plataforma Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Lync 2013, disponível em diagramas técnicos.
ms.openlocfilehash: 4993ad90307973589da6dc5081d8c2875b44ce66
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068607"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="80a1e-103">Diagrama acessível – opções da plataforma Microsoft Lync 2013</span><span class="sxs-lookup"><span data-stu-id="80a1e-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="80a1e-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Lync 2013, disponível em [diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="80a1e-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="80a1e-105">Este cartaz descreve quais responsáveis pelas decisões de negócios (BDMs) e arquitetos precisam saber sobre as implantações do Lync Online (Office 365) e do Lync Server e incluem:</span><span class="sxs-lookup"><span data-stu-id="80a1e-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="80a1e-106">Uma comparação de quatro opções de implantação diferentes: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server e Lync Server hospedado pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="80a1e-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="80a1e-107">Dois cenários de exemplo para implantar o Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="80a1e-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="80a1e-108">Comparação de quatro implantações diferentes para a plataforma Lync 2013</span><span class="sxs-lookup"><span data-stu-id="80a1e-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="80a1e-109">A comparação fornece informações sobre cada opção de implantação nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="80a1e-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="80a1e-110">Uma visão geral dos diferentes recursos de implantação</span><span class="sxs-lookup"><span data-stu-id="80a1e-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="80a1e-111">Benefícios da implementação de cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="80a1e-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="80a1e-112">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="80a1e-112">Licensing requirements</span></span>
    
- <span data-ttu-id="80a1e-113">Tarefas de arquitetura necessárias</span><span class="sxs-lookup"><span data-stu-id="80a1e-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="80a1e-114">Responsabilidades de profissionais de ti para implementar cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="80a1e-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="80a1e-115">Visão geral</span><span class="sxs-lookup"><span data-stu-id="80a1e-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="80a1e-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="80a1e-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="80a1e-117">Você obtém eficiência e otimiza o custo com planos multilocatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="80a1e-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="80a1e-118">O diagrama a seguir mostra o Lync Online com um locatário do Azure Active Directory, que sincroniza nomes de conta e senhas entre o ambiente do AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="80a1e-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="80a1e-119">Descrição dos recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="80a1e-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="80a1e-120">Software como serviço (SaaS).</span><span class="sxs-lookup"><span data-stu-id="80a1e-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="80a1e-121">Conjunto de recursos avançado que está sempre atualizado.</span><span class="sxs-lookup"><span data-stu-id="80a1e-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="80a1e-122">O inclui um locatário do Azure Active Directory para contas online, que podem ser usadas com outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="80a1e-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="80a1e-123">A integração de diretórios inclui a sincronização de nomes de conta e senhas entre o ambiente do AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="80a1e-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="80a1e-124">Se o logon único (SSO) for um requisito, o AD FS (serviços de Federação do Active Directory) deverá ser implementado.</span><span class="sxs-lookup"><span data-stu-id="80a1e-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="80a1e-125">A comunicação do cliente pela Internet é criptografada e autenticada.</span><span class="sxs-lookup"><span data-stu-id="80a1e-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="80a1e-126">Equipamento de telefone herdado, rede telefônica pública comutada (PSTN), a conectividade está disponível por meio de provedores de terceiros.</span><span class="sxs-lookup"><span data-stu-id="80a1e-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="80a1e-127">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="80a1e-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="80a1e-128">Você pode combinar os benefícios do Office 365 com uma implantação local do Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="80a1e-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="80a1e-129">O diagrama a seguir mostra o Office 365 com o Lync Online em que alguns usuários estão hospedados no local e alguns usuários estão hospedados online.</span><span class="sxs-lookup"><span data-stu-id="80a1e-129">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online.</span></span> <span data-ttu-id="80a1e-130">Um servidor de borda implantado no local também é mostrado.</span><span class="sxs-lookup"><span data-stu-id="80a1e-130">An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="80a1e-131">Descrição dos recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="80a1e-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="80a1e-132">Alguns usuários estão hospedados no local e alguns usuários estão hospedados online, mas os usuários compartilham o mesmo domínio SIP (como contoso.com).</span><span class="sxs-lookup"><span data-stu-id="80a1e-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="80a1e-133">Aproveite a infraestrutura existente do Lync Server 2013, incluindo as conexões com o PSTN.</span><span class="sxs-lookup"><span data-stu-id="80a1e-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="80a1e-134">Adicione novos usuários do Lync Online facilmente quando eles não exigirem PSTN.</span><span class="sxs-lookup"><span data-stu-id="80a1e-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="80a1e-135">Migre do Lync local para o Lync Online com o passar do tempo, no seu cronograma.</span><span class="sxs-lookup"><span data-stu-id="80a1e-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="80a1e-136">Integre-se com outros aplicativos do Office 365, incluindo o Exchange Online e o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="80a1e-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="80a1e-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="80a1e-137">Lync Server</span></span>

<span data-ttu-id="80a1e-138">Nesta implantação, você tem todos os itens.</span><span class="sxs-lookup"><span data-stu-id="80a1e-138">In this deployment, you own everything.</span></span> <span data-ttu-id="80a1e-139">O diagrama a seguir mostra uma infraestrutura do Lync Server com um ambiente do AD DS (serviços de domínio Active Directory) local onde os usuários estão hospedados no local.</span><span class="sxs-lookup"><span data-stu-id="80a1e-139">The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="80a1e-140">Descrição dos recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="80a1e-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="80a1e-141">Planejamento de capacidade e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="80a1e-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="80a1e-142">Aquisição e configuração do servidor.</span><span class="sxs-lookup"><span data-stu-id="80a1e-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="80a1e-143">Instalação.</span><span class="sxs-lookup"><span data-stu-id="80a1e-143">Deployment.</span></span>
    
- <span data-ttu-id="80a1e-144">Expansão, aplicação de patch e operações.</span><span class="sxs-lookup"><span data-stu-id="80a1e-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="80a1e-145">Backup de dados.</span><span class="sxs-lookup"><span data-stu-id="80a1e-145">Backing up data.</span></span>
    
- <span data-ttu-id="80a1e-146">Manutenção de failover e recuperação de desastre.</span><span class="sxs-lookup"><span data-stu-id="80a1e-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="80a1e-147">Conexão da infraestrutura do Lync Server 2013 à PSTN.</span><span class="sxs-lookup"><span data-stu-id="80a1e-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="80a1e-148">Integração com equipamento de telefone existente, como PBXs (Private Branch eXchanges).</span><span class="sxs-lookup"><span data-stu-id="80a1e-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="80a1e-149">Lync Server hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="80a1e-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="80a1e-150">Nesta implantação, o provedor é proprietário de tudo.</span><span class="sxs-lookup"><span data-stu-id="80a1e-150">In this deployment, your provider owns everything.</span></span> <span data-ttu-id="80a1e-151">O diagrama a seguir mostra a rede de um provedor, incluindo seus servidores e equipamentos com uma conexão a um ambiente local.</span><span class="sxs-lookup"><span data-stu-id="80a1e-151">The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="80a1e-152">Descrição dos recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="80a1e-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="80a1e-153">Planejamento de capacidade e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="80a1e-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="80a1e-154">Aquisição e configuração do servidor.</span><span class="sxs-lookup"><span data-stu-id="80a1e-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="80a1e-155">Instalação.</span><span class="sxs-lookup"><span data-stu-id="80a1e-155">Deployment.</span></span>
    
- <span data-ttu-id="80a1e-156">Expansão, aplicação de patch e operações.</span><span class="sxs-lookup"><span data-stu-id="80a1e-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="80a1e-157">Backup de dados.</span><span class="sxs-lookup"><span data-stu-id="80a1e-157">Backing up data.</span></span>
    
- <span data-ttu-id="80a1e-158">Manutenção de failover e recuperação de desastre.</span><span class="sxs-lookup"><span data-stu-id="80a1e-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="80a1e-159">Integração com equipamento de telefone existente, como PBXs (Private Branch eXchanges).</span><span class="sxs-lookup"><span data-stu-id="80a1e-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="80a1e-160">Além disso, o provedor pode:</span><span class="sxs-lookup"><span data-stu-id="80a1e-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="80a1e-161">Instale seus servidores e equipamentos em sua própria rede com uma conexão com sua local (linha sólida).</span><span class="sxs-lookup"><span data-stu-id="80a1e-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="80a1e-162">Instale seus servidores no local (linha pontilhada).</span><span class="sxs-lookup"><span data-stu-id="80a1e-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="80a1e-163">Benefícios da implementação de cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="80a1e-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="80a1e-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="80a1e-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="80a1e-165">Sem carga operacional de servidores locais ou software de servidor.</span><span class="sxs-lookup"><span data-stu-id="80a1e-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="80a1e-166">Recursos de comunicação do Lync Server 2013 como um serviço baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="80a1e-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="80a1e-167">Presença do Lync, mensagens instantâneas, chamadas de áudio e vídeo, reuniões online avançadas e recursos de Webconferência abrangentes.</span><span class="sxs-lookup"><span data-stu-id="80a1e-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="80a1e-168">Usado com organizações geograficamente dispersas ou com funcionários móveis primariamente.</span><span class="sxs-lookup"><span data-stu-id="80a1e-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="80a1e-169">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="80a1e-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="80a1e-170">Use o Lync Online para usuários remotos e integração com parceiros de negócios.</span><span class="sxs-lookup"><span data-stu-id="80a1e-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="80a1e-171">Facilite uma migração do Lync local para o Lync Online.</span><span class="sxs-lookup"><span data-stu-id="80a1e-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="80a1e-172">Dar suporte a sites remotos sem usar um aparelho de filial do escritório.</span><span class="sxs-lookup"><span data-stu-id="80a1e-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="80a1e-173">Facilidade de adicionar o suporte do Lync para novas aquisições de negócios.</span><span class="sxs-lookup"><span data-stu-id="80a1e-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="80a1e-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="80a1e-174">Lync Server</span></span>

- <span data-ttu-id="80a1e-175">Soluções de nuvem privada.</span><span class="sxs-lookup"><span data-stu-id="80a1e-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="80a1e-176">Soluções altamente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="80a1e-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="80a1e-177">Soluções herdadas com componentes de terceiros que dependem de hardware e software que não são compatíveis com o Lync Online.</span><span class="sxs-lookup"><span data-stu-id="80a1e-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="80a1e-178">Restrições de privacidade que impedem a sincronização de contas do AD DS com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="80a1e-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="80a1e-179">Organizações que desejam controlar toda a plataforma e a solução.</span><span class="sxs-lookup"><span data-stu-id="80a1e-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="80a1e-180">Substituição de PBX pelo Lync Enterprise Voice.</span><span class="sxs-lookup"><span data-stu-id="80a1e-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="80a1e-181">Lync Server hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="80a1e-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="80a1e-182">Organizações que desejam a funcionalidade do Lync Server, mas que desejam terceirizar sua implantação e manutenção.</span><span class="sxs-lookup"><span data-stu-id="80a1e-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="80a1e-183">Soluções baseadas em provedor.</span><span class="sxs-lookup"><span data-stu-id="80a1e-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="80a1e-184">Soluções altamente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="80a1e-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="80a1e-185">Soluções herdadas com componentes de terceiros que dependem de hardware e software que não são compatíveis com o Lync Online.</span><span class="sxs-lookup"><span data-stu-id="80a1e-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="80a1e-186">Substituição de PBX pelo Lync Enterprise Voice.</span><span class="sxs-lookup"><span data-stu-id="80a1e-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="80a1e-187">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="80a1e-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="80a1e-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="80a1e-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="80a1e-189">Modelo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="80a1e-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="80a1e-190">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="80a1e-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="80a1e-191">Office 365 – modelo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="80a1e-191">Office 365 — Subscription model.</span></span> <span data-ttu-id="80a1e-192">Nenhuma licença adicional necessária.</span><span class="sxs-lookup"><span data-stu-id="80a1e-192">No additional licenses needed.</span></span> 
    
- <span data-ttu-id="80a1e-193">Local – todas as licenças locais são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="80a1e-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="80a1e-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="80a1e-194">Lync Server</span></span>

- <span data-ttu-id="80a1e-195">Sistema operacional do servidor</span><span class="sxs-lookup"><span data-stu-id="80a1e-195">Server Operating System</span></span>
    
- <span data-ttu-id="80a1e-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="80a1e-196">SQL Server</span></span>
    
- <span data-ttu-id="80a1e-197">Licença do Lync 2013 Server</span><span class="sxs-lookup"><span data-stu-id="80a1e-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="80a1e-198">Licença de acesso para cliente do Lync 2013</span><span class="sxs-lookup"><span data-stu-id="80a1e-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="80a1e-199">Lync Server hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="80a1e-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="80a1e-200">Os custos são baseados no acordo com o seu provedor de soluções do Lync.</span><span class="sxs-lookup"><span data-stu-id="80a1e-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="80a1e-201">Tarefas de arquitetura</span><span class="sxs-lookup"><span data-stu-id="80a1e-201">Architecture tasks</span></span>

<span data-ttu-id="80a1e-202">Esta seção lista as tarefas arquitetônicas de cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="80a1e-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="80a1e-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="80a1e-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="80a1e-204">Planejar e projetar a sincronização de diretórios.</span><span class="sxs-lookup"><span data-stu-id="80a1e-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="80a1e-205">Garantir a capacidade e a disponibilidade da rede por meio de firewalls, servidores de proxy, gateways e entre links de WAN.</span><span class="sxs-lookup"><span data-stu-id="80a1e-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="80a1e-206">Adquirir certificados SSL de terceiros para oferecer segurança corporativa para ofertas de serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="80a1e-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="80a1e-207">Decida se você deseja se conectar ao Office 365 com o protocolo IPv6 (Internet Protocol version 6).</span><span class="sxs-lookup"><span data-stu-id="80a1e-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="80a1e-208">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="80a1e-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="80a1e-209">Além das tarefas para os ambientes do Office 365 e local:</span><span class="sxs-lookup"><span data-stu-id="80a1e-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="80a1e-210">Determine quanta integração de recursos você deseja usar com as versões local e online do Exchange Server e do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="80a1e-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="80a1e-211">Se necessário, determine qual dispositivo de servidor proxy será usado para solicitações do Office 365.</span><span class="sxs-lookup"><span data-stu-id="80a1e-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="80a1e-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="80a1e-212">Lync Server</span></span>

<span data-ttu-id="80a1e-213">Projetar o ambiente do Lync em um ambiente local existente:</span><span class="sxs-lookup"><span data-stu-id="80a1e-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="80a1e-214">Topologia do Lync para escritórios centrais e filiais.</span><span class="sxs-lookup"><span data-stu-id="80a1e-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="80a1e-215">Hardware de servidor, incluindo virtualização.</span><span class="sxs-lookup"><span data-stu-id="80a1e-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="80a1e-216">Integração com os serviços de domínio do Active Directory (AD DS) e o DNS.</span><span class="sxs-lookup"><span data-stu-id="80a1e-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="80a1e-217">Balanceamento de carga para pools do Lync Server.</span><span class="sxs-lookup"><span data-stu-id="80a1e-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="80a1e-218">Failover e recuperação de desastre.</span><span class="sxs-lookup"><span data-stu-id="80a1e-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="80a1e-219">Lync Server hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="80a1e-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="80a1e-220">Para uma instalação baseada em nuvem, determine a conexão com a rede do provedor de serviços.</span><span class="sxs-lookup"><span data-stu-id="80a1e-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="80a1e-221">Para uma instalação local, determine o posicionamento dos servidores Lync do provedor em sua rede.</span><span class="sxs-lookup"><span data-stu-id="80a1e-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="80a1e-222">Para os dois tipos, determine a integração com o AD DS e o equipamento de PBX.</span><span class="sxs-lookup"><span data-stu-id="80a1e-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="80a1e-223">Responsabilidades de profissionais de ti</span><span class="sxs-lookup"><span data-stu-id="80a1e-223">IT Pro responsibilities</span></span>

<span data-ttu-id="80a1e-224">Esta seção lista as responsabilidades de profissionais de ti para cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="80a1e-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="80a1e-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="80a1e-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="80a1e-226">Implantar e gerenciar o Lync Online (Office 365):</span><span class="sxs-lookup"><span data-stu-id="80a1e-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="80a1e-227">Implementar o plano de sincronização de diretórios.</span><span class="sxs-lookup"><span data-stu-id="80a1e-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="80a1e-228">Planejar e implementar registros DNS internos e externos e roteamento.</span><span class="sxs-lookup"><span data-stu-id="80a1e-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="80a1e-229">Configure seu proxy ou firewall para os requisitos de URL e endereço IP do Office 365.</span><span class="sxs-lookup"><span data-stu-id="80a1e-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="80a1e-230">Administrar as contas de usuário e as configurações do Lync Online.</span><span class="sxs-lookup"><span data-stu-id="80a1e-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="80a1e-231">Lync Online/servidor híbrido (domínio dividido)</span><span class="sxs-lookup"><span data-stu-id="80a1e-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="80a1e-232">Além das tarefas para os ambientes do Office 365 e local:</span><span class="sxs-lookup"><span data-stu-id="80a1e-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="80a1e-233">Configure o dispositivo de servidor proxy, se necessário.</span><span class="sxs-lookup"><span data-stu-id="80a1e-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="80a1e-234">Configure a integração de recursos com as versões local e online do Exchange Server e do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="80a1e-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="80a1e-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="80a1e-235">Lync Server</span></span>

<span data-ttu-id="80a1e-236">Implantar e gerenciar o Lync Server em um ambiente local:</span><span class="sxs-lookup"><span data-stu-id="80a1e-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="80a1e-237">Provisionar os servidores.</span><span class="sxs-lookup"><span data-stu-id="80a1e-237">Provision the servers.</span></span>
    
- <span data-ttu-id="80a1e-238">Implantar a topologia do Lync.</span><span class="sxs-lookup"><span data-stu-id="80a1e-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="80a1e-239">Atualize os servidores do Lync.</span><span class="sxs-lookup"><span data-stu-id="80a1e-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="80a1e-240">Adicionar ou remover servidores de topologia conforme necessário com base na utilização.</span><span class="sxs-lookup"><span data-stu-id="80a1e-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="80a1e-241">Implementar o ambiente de failover e recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="80a1e-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="80a1e-242">Lync Server hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="80a1e-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="80a1e-243">Trabalhe com o provedor para:</span><span class="sxs-lookup"><span data-stu-id="80a1e-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="80a1e-244">Integre o Lync Server à sua rede.</span><span class="sxs-lookup"><span data-stu-id="80a1e-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="80a1e-245">Integre o Lync Server com outros produtos da Microsoft ou soluções personalizadas.</span><span class="sxs-lookup"><span data-stu-id="80a1e-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="80a1e-246">Monitorar a adesão ao contrato de nível de serviço (SLA) do provedor.</span><span class="sxs-lookup"><span data-stu-id="80a1e-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="80a1e-247">Dois cenários de exemplo para a implantação do Lync 2013</span><span class="sxs-lookup"><span data-stu-id="80a1e-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="80a1e-248">Componentes de sincronização de diretório no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="80a1e-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="80a1e-249">A implantação de componentes de sincronização de diretório do Office 365 no Azure é mais rápida devido à capacidade de implantar máquinas virtuais sob demanda.</span><span class="sxs-lookup"><span data-stu-id="80a1e-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="80a1e-250">O diagrama a seguir mostra o Lync Online com um locatário do Azure Active Directory, que sincroniza nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="80a1e-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="80a1e-251">**Somente servidor de sincronização de diretório**.</span><span class="sxs-lookup"><span data-stu-id="80a1e-251">**Directory synchronization server only**.</span></span> <span data-ttu-id="80a1e-252">Em vez de implantar o servidor de sincronização de diretório de 64 bits no seu ambiente local, você provisiona uma máquina virtual no Azure pela Internet.</span><span class="sxs-lookup"><span data-stu-id="80a1e-252">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="80a1e-253">**Sincronização de diretórios + AD FS**.</span><span class="sxs-lookup"><span data-stu-id="80a1e-253">**Directory synchronization + AD FS**.</span></span> <span data-ttu-id="80a1e-254">Essa opção permite que você ofereça suporte a identidades federadas do Office 365 (SSO) sem adicionar hardware à sua infraestrutura local.</span><span class="sxs-lookup"><span data-stu-id="80a1e-254">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="80a1e-255">Também fornece resiliência se o ambiente do Active Directory local não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="80a1e-255">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> <span data-ttu-id="80a1e-256">Os recursos dessa opção incluem:</span><span class="sxs-lookup"><span data-stu-id="80a1e-256">The features of this option include:</span></span>
  
- <span data-ttu-id="80a1e-257">Os componentes de integração de diretório são executados como máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="80a1e-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="80a1e-258">O AD FS é publicado na Internet através de proxies do AD FS executados como máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="80a1e-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="80a1e-259">O tráfego de autenticação de cliente, para usuários que estão se conectando de qualquer local, é tratado pelos servidores e proxies do AD FS implantados como máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="80a1e-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="80a1e-260">Integração do Lync com o Exchange e o SharePoint no Office 365</span><span class="sxs-lookup"><span data-stu-id="80a1e-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="80a1e-261">Lync Server com Exchange Online e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="80a1e-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="80a1e-262">O diagrama a seguir mostra o Office 365 com o Exchange Online e o SharePoint Online conectados a um farm local do Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="80a1e-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="80a1e-263">As vantagens dessa implantação permitem:</span><span class="sxs-lookup"><span data-stu-id="80a1e-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="80a1e-264">Use o conjunto de recursos completo do Lync Server 2013.</span><span class="sxs-lookup"><span data-stu-id="80a1e-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="80a1e-265">Aproveite o equipamento de telefone local existente, como PBXs.</span><span class="sxs-lookup"><span data-stu-id="80a1e-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="80a1e-266">Use o Exchange Online para email, descarregando o ônus de servidores de email locais e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="80a1e-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="80a1e-267">Use o SharePoint Online para colaboração, carregando o ônus de manter os servidores locais do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="80a1e-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="80a1e-268">Use o Lync, o Exchange e os recursos integrados do SharePoint, incluindo Unificação de mensagens (UM) no Office 365.</span><span class="sxs-lookup"><span data-stu-id="80a1e-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="80a1e-269">Servidor Exchange com Lync Online</span><span class="sxs-lookup"><span data-stu-id="80a1e-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="80a1e-270">O diagrama a seguir mostra o Office 365 com Lync Online conectado a um farm local do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="80a1e-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="80a1e-271">As vantagens dessa implantação permitem:</span><span class="sxs-lookup"><span data-stu-id="80a1e-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="80a1e-272">Aproveite a infraestrutura existente do Exchange.</span><span class="sxs-lookup"><span data-stu-id="80a1e-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="80a1e-273">Use o Lync Online para recursos de presença, mensagens instantâneas e conferência.</span><span class="sxs-lookup"><span data-stu-id="80a1e-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

