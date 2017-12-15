---
title: "Diagrama acessível - opções de plataforma do Microsoft SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft SharePoint 2013."
ms.openlocfilehash: 9cd282cc723376f85fe2cbc5a439ee24fd2ab883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="e3b3e-103">Diagrama acessível - opções de plataforma do Microsoft SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="e3b3e-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="e3b3e-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="e3b3e-105">O que arquitetos e business decision tomadores de precisam saber sobre o Office 365, Microsoft Azure e implantações em instalações.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="e3b3e-106">Este cartaz tem duas seções:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="e3b3e-107">Uma comparação dos quatro diferentes implantações do SharePoint 2013: SharePoint no Office 365, um híbrido do Office 365 com uma implantação local do SharePoint 2013, Windows Azure e uma implantação local do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="e3b3e-108">Uma descrição das três cargas de trabalho típicas para mover para o Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="e3b3e-109">Comparação entre quatro diferentes implantações para a plataforma SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="e3b3e-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="e3b3e-110">Comparação fornece informações sobre cada opção de implantação relacionada às seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="e3b3e-111">Uma visão geral dos recursos de implantação diferentes</span><span class="sxs-lookup"><span data-stu-id="e3b3e-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="e3b3e-112">O que é melhor para cada tipo de implantação</span><span class="sxs-lookup"><span data-stu-id="e3b3e-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="e3b3e-113">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="e3b3e-113">License requirements</span></span> 
    
- <span data-ttu-id="e3b3e-114">Tarefas de arquitetura necessárias para implementar</span><span class="sxs-lookup"><span data-stu-id="e3b3e-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="e3b3e-115">IT profissionais responsabilidades da implementação</span><span class="sxs-lookup"><span data-stu-id="e3b3e-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="e3b3e-116">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e3b3e-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="e3b3e-117">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="e3b3e-118">Ganho de eficiência e otimizar o custo com vários locatários planos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="e3b3e-119">O diagrama acompanha mostra o SharePoint Online com um locatário do Azure Active Directory, o que sincroniza os nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="e3b3e-120">Descrição de recursos:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-120">Description of features:</span></span> 
  
- <span data-ttu-id="e3b3e-121">Software como um serviço (SaaS).</span><span class="sxs-lookup"><span data-stu-id="e3b3e-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="e3b3e-122">Conjunto de recursos avançados sempre é atualizado.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="e3b3e-123">Inclui um locatário do Azure Active Directory (pode ser usado com outros aplicativos).</span><span class="sxs-lookup"><span data-stu-id="e3b3e-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="e3b3e-124">Integração de diretórios inclui sincronizando nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="e3b3e-125">Se o logon único (SSO) é um requisito, os serviços de Federação do Active Directory (AD FS) pode ser implementados.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="e3b3e-126">Comunicação do cliente pela Internet por meio de acesso criptografado e autenticado (porta 443).</span><span class="sxs-lookup"><span data-stu-id="e3b3e-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="e3b3e-127">Migração de dados está limitada a que pode ser carregado pela Internet.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="e3b3e-128">Personalizações: Aplicativos para Office, SharePoint e o SharePoint Designer 2013.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="e3b3e-129">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-129">Hybrid with Office 365</span></span>

<span data-ttu-id="e3b3e-130">Combine os benefícios do Office 365 com uma implantação local do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="e3b3e-131">O diagrama acompanha mostra o Office 365 com o SharePoint Online usando os serviços corporativos de conectividade (BCS) para conectar a um farm do SharePoint Server 2013 local.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="e3b3e-132">Escolha qual dos seguintes recursos para integrar:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="e3b3e-133">Pesquisa do SharePoint</span><span class="sxs-lookup"><span data-stu-id="e3b3e-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="e3b3e-134">Os usuários podem ver resultados de pesquisa de ambos os ambientes.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="e3b3e-135">Usuários da extranet podem fazer logon com uma conta do Active Directory local e usar toda a funcionalidade híbrida disponível remotamente.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="e3b3e-136">BCS</span><span class="sxs-lookup"><span data-stu-id="e3b3e-136">BCS</span></span>
  
<span data-ttu-id="e3b3e-p101">Do SharePoint Online: Os usuários podem realizar leitura e operações de gravação. O serviço BCS conecta-se a um farm do SharePoint Server 2013 local. O serviço BCS configurado nos agentes de farm local a conexão aos pontos de extremidade de serviço OData local.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p101">From SharePoint Online: Users can perform both read and write operations. The BCS service connects to an on-premises SharePoint Server 2013 farm. The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="e3b3e-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="e3b3e-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="e3b3e-141">Do SharePoint Online, os usuários podem executar leitura e gravação operações em relação a um sistema SAP no local.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="e3b3e-142">Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-142">Azure</span></span>

<span data-ttu-id="e3b3e-143">Tirar proveito da nuvem, mantendo o controle total da plataforma e recursos.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="e3b3e-144">O diagrama acompanha mostra Azure, que contém dois serviços de nuvem, um farm do SharePoint 2013 e Windows Server Active Directory com o DNS, conectando-se aos usuários através da Internet ou a conexão com o Active Directory no local por meio de túnel VPN.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="e3b3e-145">Os recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-145">Features include:</span></span> 
  
-  <span data-ttu-id="e3b3e-146">Windows Azure é uma plataforma que fornece os serviços de infraestrutura e aplicativos necessários para hospedar um farm do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="e3b3e-147">Serviços de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="e3b3e-148">Plataforma de nuvem nativo recomendada para SQL Server e SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="e3b3e-149">Recursos de computação estão disponíveis quase imediatamente com nenhum compromisso.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="e3b3e-150">Concentre-se nos aplicativos, em vez de data centers e infra-estrutura.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="e3b3e-151">Ambientes de desenvolvimento e teste e econômica.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="e3b3e-152">Soluções do SharePoint podem ser acessível pela Internet ou acessível somente a partir de um ambiente corporativo por meio de um túnel VPN-to-site.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="e3b3e-153">Personalizações não são limitadas.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="e3b3e-154">No local</span><span class="sxs-lookup"><span data-stu-id="e3b3e-154">On premises</span></span>

<span data-ttu-id="e3b3e-155">Você é proprietário tudo.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-155">You own everything.</span></span> 
  
<span data-ttu-id="e3b3e-156">O diagrama acompanha mostra um ambiente no local com servidores web, servidores de aplicativos e do Active Directory se comunicam com todos os bancos de dados e servidores de aplicativos dedicado para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="e3b3e-157">Os recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-157">Features include:</span></span> 
  
- <span data-ttu-id="e3b3e-158">Planejamento de capacidade e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="e3b3e-159">Aquisição de servidor e a instalação.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="e3b3e-160">Implantação.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-160">Deployment.</span></span> 
    
- <span data-ttu-id="e3b3e-161">Dimensionamento, aplicando o patch e operações.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="e3b3e-162">Fazendo backup de dados.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-162">Backing up data.</span></span> 
    
- <span data-ttu-id="e3b3e-163">Mantendo um ambiente de recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="e3b3e-164">Personalizações não são limitadas.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="e3b3e-p102">Tipo de implantação é melhor para...</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p102">Deployment type is best for . . .</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="e3b3e-168">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="e3b3e-p103">Proteja a colaboração e compartilhamento externo. (Recurso exclusivo!)</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p103">Secure external sharing and collaboration. (Unique feature!)</span></span> 
    
- <span data-ttu-id="e3b3e-171">Intranet — Colaboração interna, Meus Sites e sites de equipe.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="e3b3e-172">Armazenamento de documentos e controle de versão na nuvem.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="e3b3e-173">Site público de Basic.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="e3b3e-174">Recursos adicionais com planos de assinatura dedicados do Office 365:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="e3b3e-175">Equipamento de datacenter da Microsoft que é dedicado à sua organização e não é compartilhado com qualquer outra organização.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="e3b3e-176">Ambiente de cada cliente reside em uma rede fisicamente separada.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="e3b3e-p104">Comunicação do cliente em uma VPN protegido por IPSec ou conexão privada de propriedade do cliente. Autenticação de dois fatores é opcional.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p104">Client communication across an IPSec-secured VPN or customer-owned private connection. Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="e3b3e-179">Suporte de ITAR planos.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="e3b3e-180">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="e3b3e-181">Use o Office 365 para compartilhamento e colaboração em vez de configurar um ambiente de extranet externo.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="e3b3e-182">Mova Meus Sites (OneDrive for Business) para a nuvem facilitam para os usuários acessem seus arquivos remotamente.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="e3b3e-183">Inicie novos sites de equipe no Office 365.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="e3b3e-184">Integre um site do Office 365 com o ambiente do SharePoint de BCS no local.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="e3b3e-185">Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-185">Azure</span></span>

- <span data-ttu-id="e3b3e-p105">SharePoint para Sites da Internet — pública enfrentados pelos sites. Beneficie-se do Azure AD para contas de cliente e de autenticação.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p105">SharePoint for Internet Sites — Public facing sites. Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="e3b3e-188">Desenvolvedor, teste e preparo de ambientes — rapidamente provisionar e desprovisionamento ambientes inteiros.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="e3b3e-189">Aplicativos híbridos — aplicativos que abrangem o seu data center e a nuvem.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="e3b3e-p106">Ambiente de recuperação de desastre — rapidamente a recuperação de desastres. Preste apenas para uso.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p106">Disaster recovery environment — Quickly recover from a disaster. Pay only for use.</span></span> 
    
- <span data-ttu-id="e3b3e-192">Farms que exigem a profundidade de relatórios ou auditoria.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="e3b3e-193">Análise da Web.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-193">Web analytics.</span></span> 
    
- <span data-ttu-id="e3b3e-194">Criptografia de dados em repouso (dados criptografados nos bancos de dados SQL).</span><span class="sxs-lookup"><span data-stu-id="e3b3e-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="e3b3e-195">Criptografia de dados em repouso (dados criptografados nos bancos de dados SQL)</span><span class="sxs-lookup"><span data-stu-id="e3b3e-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="e3b3e-196">Farms de país (quando os dados é necessário para residem em uma jurisdição).</span><span class="sxs-lookup"><span data-stu-id="e3b3e-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="e3b3e-197">Soluções de BI complexas que devem residir fechar aos dados de BI.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="e3b3e-198">Soluções de nuvem privada.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="e3b3e-199">Soluções altamente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="e3b3e-200">Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados nos serviços de infraestrutura do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="e3b3e-201">Restrições de privacidade que evitam a sincronização de contas do Active Directory com o Windows Azure Active Directory (um requisito para o Office 365).</span><span class="sxs-lookup"><span data-stu-id="e3b3e-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="e3b3e-202">Organizações que preferem o controle da plataforma inteira and solution.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="e3b3e-203">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="e3b3e-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="e3b3e-204">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="e3b3e-p107">Modelo de assinatura. Não há licenças adicionais necessárias.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p107">Subscription model. No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="e3b3e-207">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="e3b3e-p108">Office 365 — Modelo de assinatura. Não há licenças adicionais necessárias.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p108">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="e3b3e-210">Local — Se aplicam todas as licenças de local.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="e3b3e-211">Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-211">Azure</span></span>

-  <span data-ttu-id="e3b3e-212">Assinatura do Windows Azure (inclui o sistema operacional do servidor)</span><span class="sxs-lookup"><span data-stu-id="e3b3e-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="e3b3e-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e3b3e-213">SQL Server</span></span> 
    
- <span data-ttu-id="e3b3e-214">Licença de servidor do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="e3b3e-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="e3b3e-215">Licença de acesso para cliente do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="e3b3e-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="e3b3e-216">No local</span><span class="sxs-lookup"><span data-stu-id="e3b3e-216">On premises</span></span>

- <span data-ttu-id="e3b3e-217">Sistema operacional do servidor</span><span class="sxs-lookup"><span data-stu-id="e3b3e-217">Server operating system</span></span> 
    
- <span data-ttu-id="e3b3e-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e3b3e-218">SQL Server</span></span> 
    
- <span data-ttu-id="e3b3e-219">Licença de servidor do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="e3b3e-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="e3b3e-220">Licença de acesso para cliente do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="e3b3e-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="e3b3e-221">Tarefas de arquitetura</span><span class="sxs-lookup"><span data-stu-id="e3b3e-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="e3b3e-222">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="e3b3e-p109">Design e plano de integração de diretório. Duas opções. Qualquer uma das opções podem ser implantados no local ou no Windows Azure: sincronização de senha (requer um servidor de 64 bits). SSO (requer o AD FS e vários servidores).</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p109">Plan and design directory integration. Two options. Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server). SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="e3b3e-227">Certifique-se de capacidade de rede e a disponibilidade por meio de firewalls, servidores proxy, gateways e em links de WAN.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="e3b3e-228">Adquira certificados SSL de terceiros para fornecer segurança da empresa para ofertas de serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="e3b3e-229">O nome do locatário de planejar e projetar a arquitetura do conjunto de sites e um governança.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="e3b3e-230">Planeje personalizações, soluções e aplicativos para o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="e3b3e-p110">Decida se deseja se conectar ao Office 365 usando o Internet Protocol 6 (IPv6). Isso não é comum.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p110">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6). This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="e3b3e-233">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-233">Hybrid with Office 365</span></span>

<span data-ttu-id="e3b3e-234">Além das tarefas para o Office 365 e o local de ambientes:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="e3b3e-p111">Determine quanto integração do recurso desejado e escolha a topologia híbrida. Consulte este cartaz de modelo: qual topologia híbrida devo usar?</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p111">Determine how much feature integration you want and choose the hybrid topology. See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="e3b3e-237">Se for necessário, determine qual dispositivo do servidor de proxy será usado.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="e3b3e-238">Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-238">Azure</span></span>

<span data-ttu-id="e3b3e-239">Projete o ambiente de rede Windows Azure:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="e3b3e-240">Rede virtual dentro do Azure, incluindo sub-redes.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="e3b3e-241">Ambiente de domínio e integração com servidores locais.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="e3b3e-242">Endereços IP e DNS.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="e3b3e-243">Afinidade de grupos e contas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="e3b3e-244">Projete o ambiente do SharePoint no Windows Azure:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="e3b3e-245">Topologia de farm do SharePoint e arquitetura lógica.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="e3b3e-246">Conjuntos de disponibilidade do Azure e domínios de atualização.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="e3b3e-247">Tamanhos de máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="e3b3e-248">Ponto de extremidade com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="e3b3e-249">Pontos de extremidade externos para acesso público, se o que é preferível.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="e3b3e-250">Ambiente de recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="e3b3e-251">No local</span><span class="sxs-lookup"><span data-stu-id="e3b3e-251">On premises</span></span>

<span data-ttu-id="e3b3e-252">Projete o ambiente do SharePoint em um ambiente local existente:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="e3b3e-253">Topologia de farm do SharePoint e arquitetura lógica.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="e3b3e-254">Hardware de servidor.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-254">Server hardware.</span></span> 
    
- <span data-ttu-id="e3b3e-255">Ambiente virtual, se usado.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="e3b3e-256">Balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-256">Load balancing.</span></span> 
    
- <span data-ttu-id="e3b3e-257">Integração com o AD DS e DNS.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="e3b3e-258">Ambiente de recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="e3b3e-259">IT profissionais responsabilidades</span><span class="sxs-lookup"><span data-stu-id="e3b3e-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="e3b3e-260">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="e3b3e-261">Certifique-se de estações de trabalho do usuário atender aos pré-requisitos de cliente do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="e3b3e-262">Implemente o plano de integração de diretório.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="e3b3e-263">Planejar e implementar os registros DNS internos e externos e roteamento.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="e3b3e-264">Configure o proxy ou firewall para o endereço IP do Office 365 e requisitos de URL.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="e3b3e-265">Criar e atribuir permissões aos conjuntos de sites.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="e3b3e-266">Implementar personalizações, soluções e aplicativos para o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="e3b3e-267">Monitorar a disponibilidade da rede e identificar afunilamentos possíveis.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="e3b3e-268">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="e3b3e-268">Hybrid with Office 365</span></span>

<span data-ttu-id="e3b3e-269">Além das tarefas para o Office 365 e o local de ambientes:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="e3b3e-270">Configure o dispositivo de servidor proxy, se necessário.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="e3b3e-271">Configurar a infraestrutura de gerenciamento de identidade híbrida: SSO e autenticação de servidor-para-servidor entre os dois ambientes.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="e3b3e-272">Configurar a integração dos recursos escolhidos: pesquisa, o BCS, Duet Enterprise Online.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="e3b3e-273">Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-273">Azure</span></span>

<span data-ttu-id="e3b3e-274">Implantar e gerenciar o ambiente do Windows Azure e o SharePoint:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="e3b3e-275">Implementar e gerenciar o ambiente de rede do Azure.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="e3b3e-276">Implante o ambiente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="e3b3e-277">Atualize servidores de farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="e3b3e-278">Adicionar ou desligar máquinas virtuais conforme necessário com base na utilização de farm.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="e3b3e-279">Aumentar ou diminuir os tamanhos de máquina virtual, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="e3b3e-280">Faça backup do ambiente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="e3b3e-281">Implemente o ambiente de recuperação de desastres e o protocolo.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="e3b3e-282">No local</span><span class="sxs-lookup"><span data-stu-id="e3b3e-282">On premises</span></span>

<span data-ttu-id="e3b3e-283">Implantar e gerenciar o SharePoint no ambiente local:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="e3b3e-284">Servidores de provisionamento.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-284">Provision servers.</span></span> 
    
- <span data-ttu-id="e3b3e-285">Implante o ambiente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="e3b3e-286">Atualize servidores de farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="e3b3e-287">Adicionar ou remover servidores do farm conforme necessário com base na utilização de farm.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="e3b3e-288">Faça backup do ambiente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="e3b3e-289">Implemente o ambiente de recuperação de desastres e o protocolo.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="e3b3e-290">Três cargas de trabalho típicas para mover para o Windows Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="e3b3e-291">O Office 365 mais componentes de diretório no Windows Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="e3b3e-292">Implantar o Office 365 componentes de integração de diretório no Windows Azure é mais rápido porque ele pode implantar máquinas virtuais sob demanda.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="e3b3e-293">Somente servidor de sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="e3b3e-293">Directory synchronization server only</span></span>

<span data-ttu-id="e3b3e-294">Em vez de implantar o servidor de sincronização de diretório de 64 bits em seu ambiente local, em vez disso provisionar uma máquina virtual no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="e3b3e-295">O diagrama acompanha mostra o SharePoint Online com um locatário do Azure Active Directory, o que sincroniza os nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="e3b3e-296">Sincronização de diretórios plus do AD FS</span><span class="sxs-lookup"><span data-stu-id="e3b3e-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="e3b3e-p112">Essa opção permite que você ofereça suporte a identidades do Office 365 federado (SSO) sem adicionar hardware à infraestrutura local. Ele também fornece resiliência se o ambiente do Active Directory local não está disponível.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p112">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="e3b3e-299">Componentes de integração de diretório residem no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="e3b3e-300">O AD FS é publicado na Internet por meio de proxies do AD FS no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="e3b3e-301">Tráfego de autenticação de cliente, para usuários que estão se conectando de qualquer local, é tratado por servidores AD FS e proxies que são implantados no Azure.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="e3b3e-302">Site de Internet público e o Azure AD para autenticação de cliente</span><span class="sxs-lookup"><span data-stu-id="e3b3e-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="e3b3e-p113">Aproveite a capacidade de expansão facilmente a demanda colocando em seu site da Internet no Windows Azure. Use o Azure AD para armazenar contas de cliente.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p113">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure. Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="e3b3e-305">Vantagens do Azure para sites da Internet</span><span class="sxs-lookup"><span data-stu-id="e3b3e-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="e3b3e-306">Preste apenas para os recursos que necessários dimensionando o número de máquinas virtuais com base na utilização de farm.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="e3b3e-307">Adicione profundidade a emissão de relatórios e do web analytics.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="e3b3e-308">Foco no desenvolvimento de um grande site, em vez da criação de infra-estrutura.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="e3b3e-309">AD do Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-309">Azure AD</span></span>

<span data-ttu-id="e3b3e-p114">Azure AD fornece recursos de controle acesso e o gerenciamento de identidade para serviços de nuvem. Os recursos incluem um repositório baseado em nuvem para dados de diretório e um conjunto básico de serviços de identidade, incluindo processos de logon do usuário, serviços de autenticação e AD FS. Os serviços de identidade que estão incluídos no Windows Azure AD integram facilmente suas implantações do Active Directory local e suportam totalmente os provedores de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p114">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="e3b3e-p115">O diagrama acompanha mostra a configuração de zonas e autenticação que é importante para sites na Internet. O diagrama mostra o Azure Active Directory inquilino, que contém um Farm do SharePoint no Azure com duas zonas:</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p115">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites. The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="e3b3e-315">Uma zona da Internet que interage com visitantes anônimos e autenticados e clientes fora da rede</span><span class="sxs-lookup"><span data-stu-id="e3b3e-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="e3b3e-316">Uma zona padrão que contém o NTLM para autenticação do Windows que interage com sua implantação do Active Directory local um túnel VPN e de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="e3b3e-317">Farm local além de recuperação de desastres no Azure</span><span class="sxs-lookup"><span data-stu-id="e3b3e-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="e3b3e-p116">Escolha uma opção de recuperação de desastres que atenda às suas necessidades de negócios. Azure fornece opções de nível básica para empresas de Introdução à recuperação de desastres e opções avançadas para empresas de grande porte com requisitos de alta resiliência.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p116">Choose a disaster recovery option that matches your business requirements. Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="e3b3e-320">Espera a frio</span><span class="sxs-lookup"><span data-stu-id="e3b3e-320">Cold standby</span></span>

- <span data-ttu-id="e3b3e-p117">O farm totalmente é criado, mas as máquinas virtuais são interrompidas. (Você está pagando somente quando eles estão executando!)</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p117">The farm is fully built, but the virtual machines are stopped. (You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="e3b3e-323">Manter o ambiente inclui começar as máquinas virtuais do tempo em tempos, patches, atualizando e verificando o ambiente.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="e3b3e-324">Inicie o ambiente completo em caso de desastre.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="e3b3e-325">Espera passiva</span><span class="sxs-lookup"><span data-stu-id="e3b3e-325">Warm standby</span></span>

- <span data-ttu-id="e3b3e-326">Isso inclui um pequeno farm é provisionado e em execução.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="e3b3e-327">O farm imediatamente pode atender a usuários em caso de um failover.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="e3b3e-328">Dimensionar o farm rapidamente para atender a base completos do usuário.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="e3b3e-329">Espera ativa</span><span class="sxs-lookup"><span data-stu-id="e3b3e-329">Hot standby</span></span>

<span data-ttu-id="e3b3e-330">Um farm de tamanho totalmente é provisionado e executado em espera.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="e3b3e-p118">O diagrama acompanha mostra um farm local interação com o ambiente de recuperação de desastres do SharePoint no Azure. Usam o os bancos de dados local envio de Log do SQL Server no túnel VPN para acessar o ambiente de recuperação de desastres do SharePoint, que inclui dois servidores de banco de dados SQL que contêm os bancos de dados do SharePoint, dois servidores Web Front-End e dois SharePoint Servidores de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e3b3e-p118">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure. The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

