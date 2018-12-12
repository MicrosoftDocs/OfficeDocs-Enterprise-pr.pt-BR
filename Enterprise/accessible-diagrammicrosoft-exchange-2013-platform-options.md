---
title: Diagrama acessível - opções de plataforma do Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Exchange 2013, que está disponível em diagramas técnicos.
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503124"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="0d95a-103">Diagrama acessível - opções de plataforma do Microsoft Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d95a-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="0d95a-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Exchange 2013, que está disponível em [Diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="0d95a-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="0d95a-105">Este cartaz descreve o que arquitetos e business decision tomadores de precisam saber sobre implantações do Exchange Online e o Exchange Server e inclui:</span><span class="sxs-lookup"><span data-stu-id="0d95a-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="0d95a-106">Uma comparação de quatro opções de plataforma disponíveis para o Exchange 2013: Exchange Online (Office 365), Exchange híbrido, Exchange Server local e Provider-Hosted Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d95a-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="0d95a-107">Descrições de três recursos novos ou atualizados no Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="0d95a-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="0d95a-108">Comparação entre quatro diferentes implantações para a plataforma Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d95a-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="0d95a-109">Comparação fornece informações sobre cada opção de implantação nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="0d95a-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="0d95a-110">Uma visão geral dos recursos de implantação diferentes</span><span class="sxs-lookup"><span data-stu-id="0d95a-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="0d95a-111">Benefícios da implementação de cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="0d95a-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="0d95a-112">Requisitos de licenciamento</span><span class="sxs-lookup"><span data-stu-id="0d95a-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="0d95a-113">Tarefas necessárias de arquiteturais</span><span class="sxs-lookup"><span data-stu-id="0d95a-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="0d95a-114">Responsabilidades do IT Pro para implementar cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="0d95a-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="0d95a-115">Visão geral</span><span class="sxs-lookup"><span data-stu-id="0d95a-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="0d95a-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d95a-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="0d95a-117">Ganho de eficiência e reduzir os custos com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d95a-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="0d95a-p101">O diagrama acompanha mostra o Exchange Online com um locatário do Azure Active Directory que sincroniza os nomes de conta e senhas entre o ambiente de serviços de domínio Active Directory (AD DS) no local e o locatário do Azure Active Directory. Os serviços de Federação do Active Directory (AD FS) é necessário para o serviço single sign-on.</span><span class="sxs-lookup"><span data-stu-id="0d95a-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="0d95a-120">Descrição dos recursos e funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="0d95a-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0d95a-121">A operação de servidores e de software do servidor é manipulada pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0d95a-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="0d95a-122">Conjunto de recursos de rich do Exchange Server 2013 como um serviço baseado em nuvem.</span><span class="sxs-lookup"><span data-stu-id="0d95a-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="0d95a-123">Sempre atualizada com os recursos mais recentes.</span><span class="sxs-lookup"><span data-stu-id="0d95a-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="0d95a-124">Exchange Online Protection (EOP) é incluído para anti-spam/anti-malware protection.</span><span class="sxs-lookup"><span data-stu-id="0d95a-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="0d95a-125">Alta disponibilidade incorporada com um 99,9% contrato de nível de serviço (SLA).</span><span class="sxs-lookup"><span data-stu-id="0d95a-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="0d95a-p102">Sincronização de diretórios incluindo senhas entre o local serviços de domínio do Active Directory (AD DS) e o locatário do Azure Active Directory. Os serviços de Federação do Active Directory (AD FS) é necessário para o serviço single sign-on.</span><span class="sxs-lookup"><span data-stu-id="0d95a-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="0d95a-128">Exchange híbrido</span><span class="sxs-lookup"><span data-stu-id="0d95a-128">Exchange Hybrid</span></span>

<span data-ttu-id="0d95a-129">Você pode aproveitar os benefícios do Office 365, mantendo o Exchange Server local.</span><span class="sxs-lookup"><span data-stu-id="0d95a-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="0d95a-p103">O diagrama acompanha mostra o Office 365 com o Exchange Online em que alguns usuários estão hospedados no local e alguns usuários hospedados online. Ele também mostra um locatário do Azure Active Directory que sincroniza os nomes de conta e senhas entre o ambiente de serviços de domínio Active Directory (AD DS) no local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0d95a-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="0d95a-132">Descrição dos recursos e funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="0d95a-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0d95a-133">Alguns usuários estão hospedados no local e alguns usuários hospedados online e usuários compartilham o mesmo espaço de endereço de email.</span><span class="sxs-lookup"><span data-stu-id="0d95a-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="0d95a-134">Aproveita a infra-estrutura existente do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="0d95a-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="0d95a-135">Migre do Exchange local para o Exchange Online ao longo do tempo, no seu calendário.</span><span class="sxs-lookup"><span data-stu-id="0d95a-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="0d95a-136">Integre com outros aplicativos do Office 365, incluindo o Lync Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="0d95a-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="0d95a-137">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d95a-137">Exchange Server on-premises</span></span>

<span data-ttu-id="0d95a-138">Você pode criar e gerenciar sua própria infra-estrutura do Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="0d95a-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="0d95a-139">O diagrama acompanha mostra uma infraestrutura do Exchange Server com um ambiente de serviços de domínio Active Directory (AD DS) do local onde os usuários são hospedados no local.</span><span class="sxs-lookup"><span data-stu-id="0d95a-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="0d95a-140">Descrição dos recursos e funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="0d95a-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0d95a-141">Maior grau de personalização para sua configuração e controle.</span><span class="sxs-lookup"><span data-stu-id="0d95a-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="0d95a-142">Nenhuma dependência no mantendo a afinidade de sessão na camada de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="0d95a-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="0d95a-143">Simple alta disponibilidade e resiliência do site usando grupos de disponibilidade de banco de dados (DAGs).</span><span class="sxs-lookup"><span data-stu-id="0d95a-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="0d95a-144">Gerenciados disponibilidade que ajuda você a manter uma excelente experiência de usuário.</span><span class="sxs-lookup"><span data-stu-id="0d95a-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="0d95a-145">Aproveite a infra-estrutura de armazenamento e o hardware existente.</span><span class="sxs-lookup"><span data-stu-id="0d95a-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="0d95a-146">Exchange hospedado em provedor</span><span class="sxs-lookup"><span data-stu-id="0d95a-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="0d95a-147">Você pode terceirizar sua carga de trabalho do Exchange Server para um provedor de soluções do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="0d95a-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="0d95a-148">O diagrama acompanha mostra um ambiente do Exchange Server que é operado e mantido por um provedor.</span><span class="sxs-lookup"><span data-stu-id="0d95a-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="0d95a-149">Descrição dos recursos e funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="0d95a-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="0d95a-150">A operação de servidores e de software do servidor é manipulada pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="0d95a-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="0d95a-151">Planejamento, dimensionamento, dimensionamento e manutenção da infraestrutura do Exchange Server são delegadas ao provedor.</span><span class="sxs-lookup"><span data-stu-id="0d95a-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="0d95a-152">Manutenção de serviço é manipulada pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="0d95a-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="0d95a-153">O conjunto de recursos do Exchange é limitado a versão do software implantada pelo seu provedor.</span><span class="sxs-lookup"><span data-stu-id="0d95a-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="0d95a-154">Benefícios da implementação de cada opção de implantação</span><span class="sxs-lookup"><span data-stu-id="0d95a-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="0d95a-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d95a-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="0d95a-156">Essa opção de implantação é melhor para:</span><span class="sxs-lookup"><span data-stu-id="0d95a-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="0d95a-157">Organizações que buscam para reduzir os custos de operações para o local do Exchange implantações.</span><span class="sxs-lookup"><span data-stu-id="0d95a-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="0d95a-158">Organizações que planejam aproveitar outras ofertas do Office 365, como o SharePoint Online e o Lync Online.</span><span class="sxs-lookup"><span data-stu-id="0d95a-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="0d95a-159">Exchange híbrido</span><span class="sxs-lookup"><span data-stu-id="0d95a-159">Exchange Hybrid</span></span>

<span data-ttu-id="0d95a-160">Essa opção de implantação é melhor para:</span><span class="sxs-lookup"><span data-stu-id="0d95a-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="0d95a-161">Facilitando uma migração do Exchange local para o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0d95a-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="0d95a-162">Dando suporte a sites remotos sem investir em infraestrutura de escritório de filial.</span><span class="sxs-lookup"><span data-stu-id="0d95a-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="0d95a-163">Empresas multinacionais com subsidiárias que exigem dados devem residir no local.</span><span class="sxs-lookup"><span data-stu-id="0d95a-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="0d95a-164">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d95a-164">Exchange Server on-premises</span></span>

<span data-ttu-id="0d95a-165">Essa opção de implantação é melhor para:</span><span class="sxs-lookup"><span data-stu-id="0d95a-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="0d95a-166">Soluções altamente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0d95a-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="0d95a-167">Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados pelo Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0d95a-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="0d95a-168">As organizações está sujeito às normas de governança de dados que exigem dados devem residir no local.</span><span class="sxs-lookup"><span data-stu-id="0d95a-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="0d95a-169">Organizações que desejam retém o controle da plataforma inteira and solution.</span><span class="sxs-lookup"><span data-stu-id="0d95a-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="0d95a-170">Exchange hospedado em provedor</span><span class="sxs-lookup"><span data-stu-id="0d95a-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="0d95a-171">Essa opção de implantação é melhor para:</span><span class="sxs-lookup"><span data-stu-id="0d95a-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="0d95a-172">Organizações que precisam de funcionalidade do servidor do Exchange, mas deseja terceirizar sua implantação e manutenção.</span><span class="sxs-lookup"><span data-stu-id="0d95a-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="0d95a-173">Organizações que precisam de opções de suporte personalizado.</span><span class="sxs-lookup"><span data-stu-id="0d95a-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="0d95a-174">Soluções personalizadas e integração com aplicativos personalizados oferecidos pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="0d95a-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="0d95a-175">Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados pelo Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0d95a-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="0d95a-176">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="0d95a-176">License requirements</span></span>

<span data-ttu-id="0d95a-177">A tabela a seguir detalha os requisitos de licença de cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="0d95a-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="0d95a-178">**Opção de implantação**</span><span class="sxs-lookup"><span data-stu-id="0d95a-178">**Deployment option**</span></span>|<span data-ttu-id="0d95a-179">**Requisitos de licença**</span><span class="sxs-lookup"><span data-stu-id="0d95a-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0d95a-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d95a-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="0d95a-181">Modelo de assinatura</span><span class="sxs-lookup"><span data-stu-id="0d95a-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="0d95a-182">Exchange híbrido</span><span class="sxs-lookup"><span data-stu-id="0d95a-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="0d95a-183">Office 365 - modelo de assinatura</span><span class="sxs-lookup"><span data-stu-id="0d95a-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="0d95a-184">Local - todas as licenças de local se aplicam (licenças de revisão para trocas Server local)</span><span class="sxs-lookup"><span data-stu-id="0d95a-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="0d95a-185">Licença de servidor híbrido \*</span><span class="sxs-lookup"><span data-stu-id="0d95a-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="0d95a-186">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d95a-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="0d95a-187">Sistema operacional do servidor</span><span class="sxs-lookup"><span data-stu-id="0d95a-187">Server Operating System</span></span> <br/>  <span data-ttu-id="0d95a-188">Licença de servidor do Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d95a-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="0d95a-189">Licença de acesso para cliente Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d95a-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="0d95a-190">Exchange hospedado em provedor</span><span class="sxs-lookup"><span data-stu-id="0d95a-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="0d95a-191">Custos baseiam-se no contrato com o provedor</span><span class="sxs-lookup"><span data-stu-id="0d95a-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="0d95a-192">Tarefas de arquitetura</span><span class="sxs-lookup"><span data-stu-id="0d95a-192">Architecture tasks</span></span>

<span data-ttu-id="0d95a-193">Esta seção lista as tarefas de arquiteturais para cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="0d95a-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="0d95a-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d95a-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="0d95a-195">Planejar e projetar a sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="0d95a-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="0d95a-196">Certifique-se de capacidade de rede e conectividade através de firewalls, servidores proxy, gateways e em links de WAN.</span><span class="sxs-lookup"><span data-stu-id="0d95a-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="0d95a-197">Exchange híbrido</span><span class="sxs-lookup"><span data-stu-id="0d95a-197">Exchange Hybrid</span></span>

<span data-ttu-id="0d95a-198">Além das tarefas a arquitetura para o Office 365 e o local de ambientes:</span><span class="sxs-lookup"><span data-stu-id="0d95a-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="0d95a-199">Decida se deseja fornecer um logon único na experiência.</span><span class="sxs-lookup"><span data-stu-id="0d95a-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="0d95a-200">Decida se deseja rotear emails de entrada da Internet por meio de uma organização local ou Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="0d95a-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="0d95a-201">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d95a-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="0d95a-202">Projete a topologia do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d95a-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="0d95a-203">Planeje a capacidade para hardware de servidor.</span><span class="sxs-lookup"><span data-stu-id="0d95a-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="0d95a-204">Projete a topologia de roteamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0d95a-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="0d95a-205">Projetar o balanceamento de carga para servidores de acesso para cliente.</span><span class="sxs-lookup"><span data-stu-id="0d95a-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="0d95a-206">Plano para alta disponibilidade usando grupos de disponibilidade de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0d95a-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="0d95a-207">Exchange hospedado em provedor</span><span class="sxs-lookup"><span data-stu-id="0d95a-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="0d95a-208">Verifique se a capacidade da rede e a disponibilidade por meio de firewalls, servidores proxy, gateways e em links de WAN estão disponíveis para o seu provedor.</span><span class="sxs-lookup"><span data-stu-id="0d95a-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="0d95a-209">Responsabilidades do IT Pro</span><span class="sxs-lookup"><span data-stu-id="0d95a-209">IT Pro responsibilities</span></span>

<span data-ttu-id="0d95a-210">Esta seção lista as responsabilidades profissionais de TI para cada opção de implantação.</span><span class="sxs-lookup"><span data-stu-id="0d95a-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="0d95a-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="0d95a-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="0d95a-212">Implemente o plano de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="0d95a-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="0d95a-213">Planejar e implementar os registros DNS internos e externos e roteamento.</span><span class="sxs-lookup"><span data-stu-id="0d95a-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="0d95a-214">Configure o servidor proxy ou firewall para o endereço IP do Office 365 e requisitos de URL.</span><span class="sxs-lookup"><span data-stu-id="0d95a-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="0d95a-215">Administre as contas de usuário e as configurações do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0d95a-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="0d95a-216">Exchange híbrido</span><span class="sxs-lookup"><span data-stu-id="0d95a-216">Exchange Hybrid</span></span>

<span data-ttu-id="0d95a-217">Além das responsabilidades profissionais de TI para o Office 365 e o local de ambientes:</span><span class="sxs-lookup"><span data-stu-id="0d95a-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="0d95a-218">Configure serviços de Federação Active Directory (AD FS) para logon único em (se desejar).</span><span class="sxs-lookup"><span data-stu-id="0d95a-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="0d95a-219">Configure certificados do Exchange para comunicações seguras entre os servidores Exchange 2013 e o Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d95a-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="0d95a-220">Configure registros DNS para o caminho de email de Internet entrado desejado.</span><span class="sxs-lookup"><span data-stu-id="0d95a-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="0d95a-221">Exchange Server local</span><span class="sxs-lookup"><span data-stu-id="0d95a-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="0d95a-222">Configure os certificados necessários para os serviços do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d95a-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="0d95a-223">Provisione os servidores.</span><span class="sxs-lookup"><span data-stu-id="0d95a-223">Provision the servers.</span></span>
    
- <span data-ttu-id="0d95a-224">Implemente a topologia de roteamento de mensagem do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d95a-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="0d95a-225">Implemente grupos de disponibilidade de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="0d95a-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="0d95a-226">Atualizar e manter servidores do Exchange.</span><span class="sxs-lookup"><span data-stu-id="0d95a-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="0d95a-227">Dependendo da utilização, adicionar ou remover servidores conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="0d95a-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="0d95a-228">Exchange hospedado em provedor</span><span class="sxs-lookup"><span data-stu-id="0d95a-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="0d95a-229">Responsabilidades do provedor incluem:</span><span class="sxs-lookup"><span data-stu-id="0d95a-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="0d95a-230">Manutenção do sistema e de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d95a-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="0d95a-231">Recurso de distribuições.</span><span class="sxs-lookup"><span data-stu-id="0d95a-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="0d95a-232">Recuperação de desastres e proteção de dados.</span><span class="sxs-lookup"><span data-stu-id="0d95a-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="0d95a-233">Responsabilidades da equipe de TI em sua organização incluem criando e gerenciando contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="0d95a-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="0d95a-234">Mais informações</span><span class="sxs-lookup"><span data-stu-id="0d95a-234">More information</span></span>

<span data-ttu-id="0d95a-235">Para saber mais sobre o Exchange Online (Office 365), consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d95a-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="0d95a-236">Descrição do serviço do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0d95a-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="0d95a-237">Biblioteca on-line do Exchange no TechNet</span><span class="sxs-lookup"><span data-stu-id="0d95a-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="0d95a-238">Portal Online do Exchange</span><span class="sxs-lookup"><span data-stu-id="0d95a-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="0d95a-239">Para saber mais sobre o híbrido do Exchange, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d95a-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="0d95a-p104">[Implantações híbridas do Exchange 2013](https://aka.ms/ExchangeHybrid). Lembre-se de que a licença de servidor híbrido só é necessária para os seguintes cenários: organização do Exchange 2010 com o servidor híbrido do Exchange 2013 e a organização do Exchange 2007 com o servidor híbrido do Exchange 2013 ou Exchange 2010.</span><span class="sxs-lookup"><span data-stu-id="0d95a-p104">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="0d95a-242">O Office 365 entrar</span><span class="sxs-lookup"><span data-stu-id="0d95a-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="0d95a-243">Para saber mais sobre o Exchange Server local, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d95a-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="0d95a-244">Biblioteca do Exchange Server 2013 no TechNet</span><span class="sxs-lookup"><span data-stu-id="0d95a-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="0d95a-245">Portal do Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0d95a-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="0d95a-246">Arquitetura do Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0d95a-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="0d95a-247">Para saber mais sobre Provider-Hosted Exchange, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0d95a-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="0d95a-248">Orientação e soluções de hospedagem e de multilocação do Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="0d95a-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="0d95a-249">Descrições dos três recursos novos ou atualizados no Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="0d95a-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="0d95a-250">Proteção do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0d95a-250">Exchange Online Protection</span></span>

<span data-ttu-id="0d95a-p105">Exchange Online Protection (EOP) oferece proteção antispam e antimalware para qualquer implantação, fornecendo uma camada de recursos de proteção que são implantados em uma rede global de centros de dados. Isso ajuda a simplificar o gerenciamento de seus ambientes de mensagens. EOP está incluído no Exchange Online assinaturas, mas você também pode aproveitá-lo para implantações híbridas e no local.</span><span class="sxs-lookup"><span data-stu-id="0d95a-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="0d95a-254">Os diagramas acompanha mostram as implantações do Exchange Online, Exchange híbrido e Exchange local que incluem a camada EOP na rede global.</span><span class="sxs-lookup"><span data-stu-id="0d95a-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="0d95a-255">Assistente de implantação do Exchange Server</span><span class="sxs-lookup"><span data-stu-id="0d95a-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="0d95a-p106">O Assistente de implantação do Exchange Server é uma ferramenta baseada na web que faz algumas perguntas sobre seu ambiente atual e, em seguida, gera uma lista de verificação personalizada que tenha um passo a passo para ajudá-lo a implantar o Exchange Server para diferentes tipos de cenários. Se você estiver migrando de uma versão anterior do Exchange para o Exchange 2013, migrando para o Exchange Online ou planejando uma infraestrutura híbrida, o Assistente de implantação do Exchange Server cria uma lista de verificação de implantação personalizada para seu cenário.</span><span class="sxs-lookup"><span data-stu-id="0d95a-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="0d95a-258">Acompanha a captura de tela mostra uma lista de verificação de exemplo que foi criada usando o Assistente de implantação do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="0d95a-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="0d95a-259">Integração com o Lync e o SharePoint</span><span class="sxs-lookup"><span data-stu-id="0d95a-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="0d95a-p107">Exchange Server 2013 inclui vários recursos que integram com o Lync Server 2013 e SharePoint Server 2013. Juntos, esses produtos oferecem um conjunto rico de recursos e melhorar a colaboração em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="0d95a-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="0d95a-262">Um diagrama acompanha mostra o cartaz de autenticação de servidor-para-servidor e inclui um link para o pôster.</span><span class="sxs-lookup"><span data-stu-id="0d95a-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="0d95a-263">Arquivamento, retenção e descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="0d95a-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="0d95a-264">Caixas de correio locais</span><span class="sxs-lookup"><span data-stu-id="0d95a-264">Site mailboxes</span></span>
    
- <span data-ttu-id="0d95a-265">Repositório unificado de contatos</span><span class="sxs-lookup"><span data-stu-id="0d95a-265">Unified contact store</span></span>
    
- <span data-ttu-id="0d95a-266">Fotos de alta resolução do usuário</span><span class="sxs-lookup"><span data-stu-id="0d95a-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="0d95a-267">Presença do Lync no Outlook e Outlook Web App</span><span class="sxs-lookup"><span data-stu-id="0d95a-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="0d95a-268">Autenticação servidor-para-servidor</span><span class="sxs-lookup"><span data-stu-id="0d95a-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="0d95a-269">Caixa postal</span><span class="sxs-lookup"><span data-stu-id="0d95a-269">Voicemail</span></span>
    
- <span data-ttu-id="0d95a-270">Gravações de reuniões</span><span class="sxs-lookup"><span data-stu-id="0d95a-270">Meeting recordings</span></span>
    
- <span data-ttu-id="0d95a-271">Sincronização de tarefas do Exchange</span><span class="sxs-lookup"><span data-stu-id="0d95a-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="0d95a-272">Um diagrama acompanha mostra o cartaz da arquitetura do Exchange Server 2013 SP1 e inclui um link para o pôster.</span><span class="sxs-lookup"><span data-stu-id="0d95a-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

