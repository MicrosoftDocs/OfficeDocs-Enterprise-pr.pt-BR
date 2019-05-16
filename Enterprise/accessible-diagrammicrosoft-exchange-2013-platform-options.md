---
title: Diagrama acessível-opções de plataforma do Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Exchange 2013, disponível em diagramas técnicos.
ms.openlocfilehash: ddf215544b811257e6d43f212784a3a1e5aac7b0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068587"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="0d8a7-103">Diagrama acessível-opções de plataforma do Microsoft Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d8a7-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="0d8a7-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Exchange 2013, disponível em [diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="0d8a7-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="0d8a7-105">Este cartaz descreve quais responsáveis pelas decisões de negócios (BDMs) e arquitetos precisam saber sobre as implantações do Exchange Online e do Exchange Server e incluem:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="0d8a7-106">Uma comparação de quatro opções de plataforma disponíveis para o Exchange 2013: Exchange Online (Office 365), Exchange híbrido, Exchange Server local e Exchange hospedado pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="0d8a7-107">Descrições de três recursos novos ou atualizados no Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="0d8a7-108">Comparação de quatro implantações diferentes para a plataforma Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d8a7-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="0d8a7-109">A comparação fornece informações sobre cada opção de implantação nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="0d8a7-110">Uma visão geral dos diferentes recursos de implantação</span><span class="sxs-lookup"><span data-stu-id="0d8a7-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="0d8a7-111">Benefícios da implementação de cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="0d8a7-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="0d8a7-112">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="0d8a7-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="0d8a7-113">Tarefas de arquitetura necessárias</span><span class="sxs-lookup"><span data-stu-id="0d8a7-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="0d8a7-114">Responsabilidades de profissionais de ti para implementar cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="0d8a7-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="0d8a7-115">Visão geral</span><span class="sxs-lookup"><span data-stu-id="0d8a7-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="0d8a7-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d8a7-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="0d8a7-117">Você obtém eficiência e reduz custos com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="0d8a7-118">O diagrama a seguir mostra o Exchange Online com um locatário do Azure Active Directory que sincroniza nomes de conta e senhas entre o ambiente do AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-118">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> <span data-ttu-id="0d8a7-119">O AD FS (serviços de Federação do Active Directory) é necessário para o logon único.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-119">Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="0d8a7-120">Descrição dos recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0d8a7-121">A operação de servidores e software de servidor é manipulada pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="0d8a7-122">Conjunto de recursos avançados do Exchange Server 2013 como um serviço baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="0d8a7-123">Sempre atualizado com os recursos mais recentes.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="0d8a7-124">O proteção do Exchange Online (EOP) está incluído para proteção antispam/antimalware.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="0d8a7-125">Alta disponibilidade interna com um contrato de nível de serviço (SLA) de 99,9%.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="0d8a7-126">Sincronização de diretório, incluindo senhas entre o AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-126">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant.</span></span> <span data-ttu-id="0d8a7-127">O AD FS (serviços de Federação do Active Directory) é necessário para o logon único.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-127">Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="0d8a7-128">Exchange Híbrido</span><span class="sxs-lookup"><span data-stu-id="0d8a7-128">Exchange Hybrid</span></span>

<span data-ttu-id="0d8a7-129">Você pode aproveitar os benefícios do Office 365 enquanto mantém o Exchange Server no local.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="0d8a7-130">O diagrama a seguir mostra o Office 365 com o Exchange Online em que alguns usuários estão hospedados no local e alguns usuários estão hospedados online.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-130">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online.</span></span> <span data-ttu-id="0d8a7-131">Também mostra um locatário do Azure Active Directory que sincroniza nomes de conta e senhas entre o ambiente do AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-131">It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="0d8a7-132">Descrição dos recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0d8a7-133">Alguns usuários estão hospedados no local e alguns usuários estão hospedados online, e os usuários compartilham o mesmo espaço de endereço de email.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="0d8a7-134">Aproveita a infraestrutura existente do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="0d8a7-135">Migre do Exchange no local para o Exchange Online com o passar do tempo, no seu cronograma.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="0d8a7-136">Integre-se com outros aplicativos do Office 365, incluindo o Lync Online e o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="0d8a7-137">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d8a7-137">Exchange Server on-premises</span></span>

<span data-ttu-id="0d8a7-138">Você pode criar e gerenciar sua própria infraestrutura do Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="0d8a7-139">O diagrama a seguir mostra uma infraestrutura do Exchange Server com um ambiente do AD DS (serviços de domínio Active Directory) local onde os usuários estão hospedados no local.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="0d8a7-140">Descrição dos recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0d8a7-141">O maior grau de controle e personalização da sua configuração.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="0d8a7-142">Nenhuma dependência para manter a afinidade da sessão na camada de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="0d8a7-143">Alta disponibilidade simples e resiliência de site usando grupos de disponibilidade de banco de dados (DAGs).</span><span class="sxs-lookup"><span data-stu-id="0d8a7-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="0d8a7-144">Disponibilidade gerenciada que ajuda você a manter uma ótima experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="0d8a7-145">Aproveite o hardware existente e a infraestrutura de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="0d8a7-146">Exchange hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="0d8a7-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="0d8a7-147">Você pode terceirizar sua carga de trabalho do Exchange Server para um provedor de soluções do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="0d8a7-148">O diagrama a seguir mostra um ambiente do Exchange Server operado e mantido por um provedor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="0d8a7-149">Descrição dos recursos e funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0d8a7-150">A operação de servidores e software de servidor é manipulada pelo seu provedor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="0d8a7-151">O planejamento, o dimensionamento, a escalabilidade e a manutenção da infraestrutura do Exchange Server são delegados ao seu provedor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="0d8a7-152">A manutenção do serviço é manipulada pelo seu provedor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="0d8a7-153">O conjunto de recursos do Exchange é limitado à versão do software implantada pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="0d8a7-154">Benefícios da implementação de cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="0d8a7-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="0d8a7-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d8a7-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="0d8a7-156">Essa opção de implantação é melhor para:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="0d8a7-157">Organizações que procuram reduzir os custos de operações para implantações locais do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="0d8a7-158">Organizações que planejam aproveitar outras ofertas do Office 365, como o SharePoint Online e o Lync Online.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="0d8a7-159">Exchange Híbrido</span><span class="sxs-lookup"><span data-stu-id="0d8a7-159">Exchange Hybrid</span></span>

<span data-ttu-id="0d8a7-160">Essa opção de implantação é melhor para:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="0d8a7-161">Facilitar uma migração do Exchange no local para o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="0d8a7-162">Suporte a sites remotos sem investir na infraestrutura de filial do escritório.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="0d8a7-163">Empresas multinacionais com subsidiárias que exigem dados para residir no local.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="0d8a7-164">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d8a7-164">Exchange Server on-premises</span></span>

<span data-ttu-id="0d8a7-165">Essa opção de implantação é melhor para:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="0d8a7-166">Soluções altamente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="0d8a7-167">Soluções herdadas com componentes de terceiros que dependem de hardware e software que não são compatíveis com o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="0d8a7-168">As organizações estão sujeitas às regulamentações de governança de dados que exigem dados para residir no local.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="0d8a7-169">Organizações que desejam manter o controle de toda a plataforma e solução.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="0d8a7-170">Exchange hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="0d8a7-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="0d8a7-171">Essa opção de implantação é melhor para:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="0d8a7-172">Organizações que precisam de funcionalidade do Exchange Server, mas que desejam terceirizar sua implantação e manutenção.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="0d8a7-173">Organizações que precisam de opções de suporte personalizado.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="0d8a7-174">Soluções e integração personalizadas com aplicativos personalizados oferecidos pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="0d8a7-175">Soluções herdadas com componentes de terceiros que dependem de hardware e software que não são compatíveis com o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="0d8a7-176">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="0d8a7-176">License requirements</span></span>

<span data-ttu-id="0d8a7-177">A tabela a seguir detalha os requisitos de licença para cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="0d8a7-178">**Opção de implantação**</span><span class="sxs-lookup"><span data-stu-id="0d8a7-178">**Deployment option**</span></span>|<span data-ttu-id="0d8a7-179">**Requisitos de licença**</span><span class="sxs-lookup"><span data-stu-id="0d8a7-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0d8a7-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d8a7-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="0d8a7-181">Modelo de assinatura</span><span class="sxs-lookup"><span data-stu-id="0d8a7-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="0d8a7-182">Exchange Híbrido</span><span class="sxs-lookup"><span data-stu-id="0d8a7-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="0d8a7-183">Office 365-modelo de assinatura</span><span class="sxs-lookup"><span data-stu-id="0d8a7-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="0d8a7-184">Local-todas as licenças locais são aplicadas (revise as licenças do servidor de troca local)</span><span class="sxs-lookup"><span data-stu-id="0d8a7-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="0d8a7-185">Licença de servidor híbrido \*</span><span class="sxs-lookup"><span data-stu-id="0d8a7-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="0d8a7-186">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d8a7-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="0d8a7-187">Sistema operacional do servidor</span><span class="sxs-lookup"><span data-stu-id="0d8a7-187">Server Operating System</span></span> <br/>  <span data-ttu-id="0d8a7-188">Licença de servidor do Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d8a7-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="0d8a7-189">Licença de acesso para cliente do Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d8a7-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="0d8a7-190">Exchange hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="0d8a7-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="0d8a7-191">Os custos são baseados no contrato com o provedor</span><span class="sxs-lookup"><span data-stu-id="0d8a7-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="0d8a7-192">Tarefas de arquitetura</span><span class="sxs-lookup"><span data-stu-id="0d8a7-192">Architecture tasks</span></span>

<span data-ttu-id="0d8a7-193">Esta seção lista as tarefas arquitetônicas de cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="0d8a7-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d8a7-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="0d8a7-195">Planejar e projetar a sincronização de diretórios.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="0d8a7-196">Garantir a capacidade e a conectividade da rede por meio de firewalls, servidores de proxy, gateways e entre links de WAN.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="0d8a7-197">Exchange Híbrido</span><span class="sxs-lookup"><span data-stu-id="0d8a7-197">Exchange Hybrid</span></span>

<span data-ttu-id="0d8a7-198">Além das tarefas de arquitetura para os ambientes do Office 365 e local:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="0d8a7-199">Decida se deseja fornecer uma experiência de logon único.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="0d8a7-200">Decida se deseja encaminhar emails de entrada da Internet por meio de uma organização local ou através do Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="0d8a7-201">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d8a7-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="0d8a7-202">Projetar a topologia do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="0d8a7-203">Planejar a capacidade do hardware do servidor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="0d8a7-204">Criar a topologia de roteamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="0d8a7-205">Designar balanceamento de carga para servidores de acesso para cliente.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="0d8a7-206">Planejar a alta disponibilidade usando grupos de disponibilidade de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="0d8a7-207">Exchange hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="0d8a7-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="0d8a7-208">Certifique-se de que a capacidade e a disponibilidade da rede por meio de firewalls, servidores de proxy, gateways e links de WAN estão disponíveis para o provedor.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="0d8a7-209">Responsabilidades de profissionais de ti</span><span class="sxs-lookup"><span data-stu-id="0d8a7-209">IT Pro responsibilities</span></span>

<span data-ttu-id="0d8a7-210">Esta seção lista as responsabilidades de profissionais de ti para cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="0d8a7-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d8a7-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="0d8a7-212">Implementar o plano de sincronização de diretórios.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="0d8a7-213">Planejar e implementar registros DNS internos e externos e roteamento.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="0d8a7-214">Configure o servidor de proxy ou o firewall para os requisitos de URL e endereço IP do Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="0d8a7-215">Administre as contas de usuário e as configurações do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="0d8a7-216">Exchange Híbrido</span><span class="sxs-lookup"><span data-stu-id="0d8a7-216">Exchange Hybrid</span></span>

<span data-ttu-id="0d8a7-217">Além das responsabilidades do profissional de ti para os ambientes do Office 365 e locais:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="0d8a7-218">Configure o AD FS (serviços de Federação do Active Directory) para logon único (se desejado).</span><span class="sxs-lookup"><span data-stu-id="0d8a7-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="0d8a7-219">Configure certificados do Exchange para comunicações seguras entre os servidores do Exchange 2013 e o Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="0d8a7-220">Configurar registros DNS para o caminho de email da Internet de entrada desejado.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="0d8a7-221">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d8a7-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="0d8a7-222">Configure os certificados necessários para os serviços do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="0d8a7-223">Provisionar os servidores.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-223">Provision the servers.</span></span>
    
- <span data-ttu-id="0d8a7-224">Implementar a topologia de roteamento de mensagens do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="0d8a7-225">Implementar grupos de disponibilidade de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="0d8a7-226">Atualizar e manter servidores do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="0d8a7-227">Dependendo da utilização, adicione ou remova os servidores conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="0d8a7-228">Exchange hospedado pelo provedor</span><span class="sxs-lookup"><span data-stu-id="0d8a7-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="0d8a7-229">As responsabilidades do provedor incluem:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="0d8a7-230">Manutenção do sistema e do serviço.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="0d8a7-231">Distribuições de recursos.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="0d8a7-232">Proteção de dados e recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="0d8a7-233">As responsabilidades da equipe de ti em sua organização incluem a criação e o gerenciamento de contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="0d8a7-234">Mais informações</span><span class="sxs-lookup"><span data-stu-id="0d8a7-234">More information</span></span>

<span data-ttu-id="0d8a7-235">Para saber mais sobre o Exchange Online (Office 365), confira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="0d8a7-236">Descrição do serviço do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0d8a7-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="0d8a7-237">Biblioteca do Exchange Online no TechNet</span><span class="sxs-lookup"><span data-stu-id="0d8a7-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="0d8a7-238">Portal do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0d8a7-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="0d8a7-239">Para saber mais sobre o Exchange híbrido, confira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="0d8a7-240">Implantações híbridas do [Exchange 2013](https://aka.ms/ExchangeHybrid).</span><span class="sxs-lookup"><span data-stu-id="0d8a7-240">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid).</span></span> <span data-ttu-id="0d8a7-241">Você deve observar que a licença de servidor híbrido só é necessária para os seguintes cenários: organização do Exchange 2010 com o servidor do Exchange 2013 Hybrid Server e a organização do Exchange 2007 com o Exchange 2013 ou Exchange 2010 Hybrid Server.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-241">You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="0d8a7-242">Entrada do Office 365</span><span class="sxs-lookup"><span data-stu-id="0d8a7-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="0d8a7-243">Para saber mais sobre o Exchange Server local, confira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="0d8a7-244">Biblioteca do Exchange Server 2013 no TechNet</span><span class="sxs-lookup"><span data-stu-id="0d8a7-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="0d8a7-245">Portal do Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0d8a7-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="0d8a7-246">Arquitetura do Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0d8a7-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="0d8a7-247">Para saber mais sobre o Exchange hospedado pelo provedor, confira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d8a7-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="0d8a7-248">Orientações e soluções de hospedagem e multilocação do Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0d8a7-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="0d8a7-249">Descrições de três recursos novos ou atualizados no Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d8a7-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="0d8a7-250">Proteção do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0d8a7-250">Exchange Online Protection</span></span>

<span data-ttu-id="0d8a7-251">O Exchange Online Protection (EOP) fornece proteção antispam e antimalware para qualquer implantação fornecendo uma camada de recursos de proteção implantados em uma rede global de data centers.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-251">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers.</span></span> <span data-ttu-id="0d8a7-252">Isso ajuda a simplificar o gerenciamento de seus ambientes de mensagens.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-252">This helps you to simplify the management of your messaging environments.</span></span> <span data-ttu-id="0d8a7-253">O EOP está incluído nas assinaturas do Exchange Online, mas você também pode utilizá-lo para implantações híbridas e locais.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-253">EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="0d8a7-254">Os diagramas a seguir mostram implantações para o Exchange Online, o Exchange híbrido e o Exchange local que incluem a camada EOP na rede global.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="0d8a7-255">Assistente de Implantação do Exchange Server</span><span class="sxs-lookup"><span data-stu-id="0d8a7-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="0d8a7-256">O assistente de implantação do Exchange Server é uma ferramenta baseada na Web que faz algumas perguntas sobre seu ambiente atual e, em seguida, gera uma lista de verificação passo a passo personalizada para ajudá-lo a implantar o Exchange Server para diferentes tipos de cenários.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-256">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios.</span></span> <span data-ttu-id="0d8a7-257">Se você estiver migrando de uma versão anterior do Exchange para o Exchange 2013, migrar para o Exchange Online ou planejar uma infraestrutura híbrida, o assistente de implantação do Exchange Server cria uma lista de verificação de implantação personalizada para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-257">Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="0d8a7-258">A captura de tela a seguir mostra um exemplo de lista de verificação que foi criada usando o assistente de implantação do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="0d8a7-259">Integração com o Lync e o SharePoint</span><span class="sxs-lookup"><span data-stu-id="0d8a7-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="0d8a7-260">O Exchange Server 2013 inclui muitos recursos que se integram ao Lync Server 2013 e ao SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-260">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013.</span></span> <span data-ttu-id="0d8a7-261">Juntos, esses produtos oferecem um pacote avançado de recursos e aprimoram a colaboração em sua organização.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-261">Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="0d8a7-262">Um diagrama de acompanhamento mostra o pôster de autenticação de servidor para servidor e inclui um link para o pôster.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="0d8a7-263">Arquivamento, retenção e descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="0d8a7-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="0d8a7-264">Caixas de correio local</span><span class="sxs-lookup"><span data-stu-id="0d8a7-264">Site mailboxes</span></span>
    
- <span data-ttu-id="0d8a7-265">Repositório unificado de contatos</span><span class="sxs-lookup"><span data-stu-id="0d8a7-265">Unified contact store</span></span>
    
- <span data-ttu-id="0d8a7-266">Fotos do usuário de alta resolução</span><span class="sxs-lookup"><span data-stu-id="0d8a7-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="0d8a7-267">Presença do Lync no Outlook e no Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="0d8a7-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="0d8a7-268">Autenticação de servidor para servidor</span><span class="sxs-lookup"><span data-stu-id="0d8a7-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="0d8a7-269">Caixa postal</span><span class="sxs-lookup"><span data-stu-id="0d8a7-269">Voicemail</span></span>
    
- <span data-ttu-id="0d8a7-270">Gravações de reunião</span><span class="sxs-lookup"><span data-stu-id="0d8a7-270">Meeting recordings</span></span>
    
- <span data-ttu-id="0d8a7-271">Sincronização de tarefas do Exchange</span><span class="sxs-lookup"><span data-stu-id="0d8a7-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="0d8a7-272">Um diagrama de acompanhamento mostra o pôster da arquitetura do Exchange Server 2013 SP1 e inclui um link para o pôster.</span><span class="sxs-lookup"><span data-stu-id="0d8a7-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

