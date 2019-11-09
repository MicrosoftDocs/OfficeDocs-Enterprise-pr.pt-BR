---
title: Diagrama acessível – opções de plataforma do Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- SPO_Content
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft SharePoint 2013.
ms.openlocfilehash: aeb17825efa26260422bd1407dfa71920838011d
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077544"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a><span data-ttu-id="8cdd1-103">Diagrama acessível – opções de plataforma do Microsoft SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8cdd1-103">Accessible diagram - Microsoft SharePoint 2013 Platform Options</span></span>

<span data-ttu-id="8cdd1-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-104">**Summary:** This article is an accessible text version of the diagram named Microsoft SharePoint 2013 Platform Options.</span></span>
  
<span data-ttu-id="8cdd1-105">Quais responsáveis pelas decisões de negócios (BDMs) e arquitetos precisam saber sobre o Office 365, o Microsoft Azure e implantações locais.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-105">What business decision makers (BDMs) and architects need to know about Office 365, Microsoft Azure, and on-premises deployments.</span></span> 
  
<span data-ttu-id="8cdd1-106">Este cartaz tem duas seções:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-106">This poster has two sections:</span></span> 
  
- <span data-ttu-id="8cdd1-107">Uma comparação de quatro implantações diferentes para o SharePoint 2013: SharePoint no Office 365, um híbrido do Office 365 com uma implantação local do SharePoint 2013, Azure e uma implantação local do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-107">A comparison of four different deployments for SharePoint 2013: SharePoint in Office 365, a hybrid of Office 365 with an on-premises deployment of SharePoint 2013, Azure, and an on-premises deployment of SharePoint 2013.</span></span> 
    
- <span data-ttu-id="8cdd1-108">Uma descrição de três cargas de trabalho típicas para mover para o Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-108">A description of three typical workloads to move to Azure.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a><span data-ttu-id="8cdd1-109">Comparação de quatro implantações diferentes para a plataforma do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8cdd1-109">Comparison of four different deployments for the SharePoint 2013 platform</span></span>

<span data-ttu-id="8cdd1-110">A comparação fornece informações sobre cada opção de implantação relacionada às seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-110">The comparison provides information about each deployment option related to the following areas:</span></span> 
  
- <span data-ttu-id="8cdd1-111">Uma visão geral dos diferentes recursos de implantação</span><span class="sxs-lookup"><span data-stu-id="8cdd1-111">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="8cdd1-112">O que cada tipo de implantação é ideal para</span><span class="sxs-lookup"><span data-stu-id="8cdd1-112">What each type of deployment is best for</span></span> 
    
- <span data-ttu-id="8cdd1-113">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="8cdd1-113">License requirements</span></span> 
    
- <span data-ttu-id="8cdd1-114">Tarefas de arquitetura necessárias para implementar</span><span class="sxs-lookup"><span data-stu-id="8cdd1-114">Architecture tasks required to implement</span></span> 
    
- <span data-ttu-id="8cdd1-115">Responsabilidades de profissionais de ti para implementação</span><span class="sxs-lookup"><span data-stu-id="8cdd1-115">IT pro responsibilities for implementation</span></span> 
    
### <a name="overview"></a><span data-ttu-id="8cdd1-116">Visão geral</span><span class="sxs-lookup"><span data-stu-id="8cdd1-116">Overview</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="8cdd1-117">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-117">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="8cdd1-118">Ganhe eficiência e otimize o custo com planos multilocatários do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-118">Gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span> 
  
<span data-ttu-id="8cdd1-119">O diagrama a seguir mostra o SharePoint Online com um locatário do Azure Active Directory, que sincroniza nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-119">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="8cdd1-120">Descrição dos recursos:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-120">Description of features:</span></span> 
  
- <span data-ttu-id="8cdd1-121">Software como serviço (SaaS).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-121">Software as a Service (SaaS).</span></span> 
    
- <span data-ttu-id="8cdd1-122">O conjunto de recursos avançados está sempre atualizado.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-122">Rich feature set is always up to date.</span></span> 
    
- <span data-ttu-id="8cdd1-123">Inclui um locatário do Azure Active Directory (pode ser usado com outros aplicativos).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-123">Includes an Azure Active Directory tenant (can be used with other applications).</span></span> 
    
- <span data-ttu-id="8cdd1-124">A integração de diretórios inclui a sincronização de nomes de contas e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-124">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
    
- <span data-ttu-id="8cdd1-125">Se o logon único (SSO) for um requisito, o AD FS (serviços de Federação do Active Directory) pode ser implementado.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-125">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) can be implemented.</span></span> 
    
- <span data-ttu-id="8cdd1-126">Comunicação de cliente pela Internet por meio de acesso criptografado e autenticado (porta 443).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-126">Client communication over the Internet through encrypted and authenticated access (port 443).</span></span> 
    
- <span data-ttu-id="8cdd1-127">A migração de dados é limitada ao que pode ser carregado pela Internet.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-127">Data migration is limited to what can be uploaded over the Internet.</span></span> 
    
- <span data-ttu-id="8cdd1-128">Personalizações: aplicativos para Office, SharePoint e SharePoint Designer 2013.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-128">Customizations: Apps for Office, SharePoint, and SharePoint Designer 2013.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="8cdd1-129">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-129">Hybrid with Office 365</span></span>

<span data-ttu-id="8cdd1-130">Combinar os benefícios do Office 365 com uma implantação local do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-130">Combine the benefits of Office 365 with an on-premises deployment of SharePoint 2013.</span></span> 
  
<span data-ttu-id="8cdd1-131">O diagrama a seguir mostra o Office 365 com o SharePoint online usando o serviços corporativos de conectividade (BCS) para se conectar a um farm local do SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-131">The accompanying diagram shows Office 365 with SharePoint Online using Business Connectivity Services (BCS) to connect to an on-premises SharePoint Server 2013 farm.</span></span> 
  
<span data-ttu-id="8cdd1-132">Escolha quais dos seguintes recursos serão integrados:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-132">Choose which of the following features to integrate:</span></span> 
  
<span data-ttu-id="8cdd1-133">Pesquisa do SharePoint</span><span class="sxs-lookup"><span data-stu-id="8cdd1-133">SharePoint Search</span></span> 
  
- <span data-ttu-id="8cdd1-134">Os usuários podem ver os resultados de pesquisa de ambos os ambientes.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-134">Users can see search results from both environments.</span></span> 
    
- <span data-ttu-id="8cdd1-135">Os usuários da extranet podem fazer logon remotamente com uma conta do Active Directory local e usar toda a funcionalidade híbrida disponível.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-135">Extranet users can remotely log on with an on-premises Active Directory account and use all available hybrid functionality.</span></span> 
    
<span data-ttu-id="8cdd1-136">BCS</span><span class="sxs-lookup"><span data-stu-id="8cdd1-136">BCS</span></span>
  
<span data-ttu-id="8cdd1-137">No SharePoint Online: os usuários podem executar operações de leitura e gravação.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-137">From SharePoint Online: Users can perform both read and write operations.</span></span> <span data-ttu-id="8cdd1-138">O serviço BCS se conecta a um farm local do SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-138">The BCS service connects to an on-premises SharePoint Server 2013 farm.</span></span> <span data-ttu-id="8cdd1-139">O serviço BCS configurado nos agentes do farm local a conexão com pontos de extremidade do serviço OData local.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-139">The BCS service configured on the on-premises farm brokers the connection to on-premises OData Service endpoints.</span></span> 
  
<span data-ttu-id="8cdd1-140">Duet Enterprise Online</span><span class="sxs-lookup"><span data-stu-id="8cdd1-140">Duet Enterprise Online</span></span> 
  
<span data-ttu-id="8cdd1-141">No SharePoint Online, os usuários podem realizar operações de leitura e gravação em um sistema SAP local.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-141">From SharePoint Online, users can perform read and write operations against an on-premises SAP system.</span></span> 
  
#### <a name="azure"></a><span data-ttu-id="8cdd1-142">Azure</span><span class="sxs-lookup"><span data-stu-id="8cdd1-142">Azure</span></span>

<span data-ttu-id="8cdd1-143">Aproveite a nuvem enquanto mantém o controle total da plataforma e dos recursos.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-143">Take advantage of the cloud while maintaining full control of the platform and features.</span></span> 
  
<span data-ttu-id="8cdd1-144">O diagrama a seguir mostra o Azure, que contém dois serviços de nuvem, um farm do SharePoint 2013 e o Windows Server Active Directory com o DNS conectado a usuários pela Internet ou conectando-se ao Active Directory local via túnel VPN.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-144">The accompanying diagram shows Azure, which contains two cloud services, a SharePoint 2013 farm, and Windows Server Active Directory with DNS connecting to users over the Internet or connecting to on-premises Active Directory via VPN tunnel.</span></span> 
  
<span data-ttu-id="8cdd1-145">Os recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-145">Features include:</span></span> 
  
-  <span data-ttu-id="8cdd1-146">O Azure é uma plataforma que fornece a infraestrutura e os serviços de aplicativo necessários para hospedar um farm do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-146">Azure is a platform that provides the infrastructure and app services needed to host a SharePoint 2013 farm.</span></span>
    
- <span data-ttu-id="8cdd1-147">Serviços de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-147">Infrastructure Services.</span></span> 
    
- <span data-ttu-id="8cdd1-148">Melhor plataforma de nuvem nativa para o SQL Server e o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-148">Best native cloud platform for SQL Server and SharePoint.</span></span> 
    
- <span data-ttu-id="8cdd1-149">Os recursos de computação estão disponíveis quase imediatamente sem nenhum compromisso.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-149">Computing resources are available almost immediately with no commitment.</span></span> 
    
- <span data-ttu-id="8cdd1-150">Concentre-se nos aplicativos, em vez de datacenters e infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-150">Focus on applications, instead of datacenters and infrastructure.</span></span> 
    
- <span data-ttu-id="8cdd1-151">Ambientes de desenvolvimento e teste de baixo custo.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-151">Inexpensive development and test environments.</span></span> 
    
- <span data-ttu-id="8cdd1-152">As soluções do SharePoint podem ser acessadas pela Internet ou acessíveis apenas de um ambiente corporativo por meio de um túnel VPN de site a site.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-152">SharePoint solutions can be accessible from the Internet or accessible only from a corporate environment through a site-to-site VPN tunnel.</span></span> 
    
- <span data-ttu-id="8cdd1-153">As personalizações não são limitadas.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-153">Customizations are not limited.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="8cdd1-154">Local</span><span class="sxs-lookup"><span data-stu-id="8cdd1-154">On premises</span></span>

<span data-ttu-id="8cdd1-155">Você tem tudo.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-155">You own everything.</span></span> 
  
<span data-ttu-id="8cdd1-156">O diagrama a seguir mostra um ambiente local com servidores Web, servidores de aplicativos e o Active Directory se comunicando com todos os bancos de dados e servidores de aplicativos dedicados para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-156">The accompanying diagram shows an on-premises environment with web servers, application servers, and Active Directory communicating with all databases and dedicated application servers for search.</span></span> 
  
<span data-ttu-id="8cdd1-157">Os recursos incluem:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-157">Features include:</span></span> 
  
- <span data-ttu-id="8cdd1-158">Planejamento de capacidade e dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-158">Capacity planning and sizing.</span></span> 
    
- <span data-ttu-id="8cdd1-159">Aquisição e configuração do servidor.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-159">Server acquisition and setup.</span></span> 
    
- <span data-ttu-id="8cdd1-160">Instalação.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-160">Deployment.</span></span> 
    
- <span data-ttu-id="8cdd1-161">Expansão, aplicação de patch e operações.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-161">Scaling out, patching, and operations.</span></span> 
    
- <span data-ttu-id="8cdd1-162">Backup de dados.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-162">Backing up data.</span></span> 
    
- <span data-ttu-id="8cdd1-163">Manutenção de um ambiente de recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-163">Maintaining a disaster recovery environment.</span></span> 
    
- <span data-ttu-id="8cdd1-164">As personalizações não são limitadas.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-164">Customizations are not limited.</span></span> 
    
### <a name="deployment-type-is-best-for---"></a><span data-ttu-id="8cdd1-165">O tipo de implantação é melhor para o.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-165">Deployment type is best for .</span></span> <span data-ttu-id="8cdd1-166">.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-166"></span></span> <span data-ttu-id="8cdd1-167">.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-167"></span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="8cdd1-168">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-168">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="8cdd1-169">Compartilhamento e colaboração externos seguros.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-169">Secure external sharing and collaboration.</span></span> <span data-ttu-id="8cdd1-170">(Recurso exclusivo!)</span><span class="sxs-lookup"><span data-stu-id="8cdd1-170">(Unique feature!)</span></span> 
    
- <span data-ttu-id="8cdd1-171">Intranet — sites de equipe, meus sites e colaboração interna.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-171">Intranet — Team sites, My Sites, and internal collaboration.</span></span> 
    
- <span data-ttu-id="8cdd1-172">Armazenamento de documentos e controle de versão na nuvem.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-172">Document storage and versioning in the cloud.</span></span> 
    
- <span data-ttu-id="8cdd1-173">Site básico voltado para o público.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-173">Basic public-facing website.</span></span> 
    
<span data-ttu-id="8cdd1-174">Recursos adicionais com planos de assinatura dedicados do Office 365:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-174">Additional features with Office 365 Dedicated subscription plans:</span></span> 
  
- <span data-ttu-id="8cdd1-175">Equipamento de datacenter da Microsoft dedicado à sua organização e não compartilhado com nenhuma outra organização.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-175">Microsoft datacenter equipment that is dedicated to your organization and not shared with any other organization.</span></span> 
    
- <span data-ttu-id="8cdd1-176">Cada ambiente do cliente reside em uma rede fisicamente separada.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-176">Each customer environment resides in a physically separate network.</span></span> 
    
- <span data-ttu-id="8cdd1-177">Comunicação de cliente através de uma VPN protegida por IPSec ou uma conexão privada de Propriedade do cliente.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-177">Client communication across an IPSec-secured VPN or customer-owned private connection.</span></span> <span data-ttu-id="8cdd1-178">A autenticação de dois fatores é opcional.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-178">Two-factor authentication is optional.</span></span> 
    
- <span data-ttu-id="8cdd1-179">ITAR-planos de suporte.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-179">ITAR-support plans.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="8cdd1-180">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-180">Hybrid with Office 365</span></span>

- <span data-ttu-id="8cdd1-181">Use o Office 365 para compartilhamento externo e colaboração em vez de configurar um ambiente de extranet.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-181">Use Office 365 for external sharing and collaboration instead of setting up an extranet environment.</span></span> 
    
- <span data-ttu-id="8cdd1-182">Mover meus sites (OneDrive for Business) para a nuvem para facilitar o acesso dos usuários aos seus arquivos remotamente.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-182">Move My Sites (OneDrive for Business) to the cloud to make it easier for users to access their files remotely.</span></span> 
    
- <span data-ttu-id="8cdd1-183">Inicie novos sites de equipe no Office 365.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-183">Start new team sites in Office 365.</span></span> 
    
- <span data-ttu-id="8cdd1-184">Integre um site do Office 365 com o ambiente do SharePoint de BCS local.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-184">Integrate an Office 365 site with on-premises BCS SharePoint environment.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="8cdd1-185">Azure</span><span class="sxs-lookup"><span data-stu-id="8cdd1-185">Azure</span></span>

- <span data-ttu-id="8cdd1-186">SharePoint para sites da Internet — sites voltados ao público.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-186">SharePoint for Internet Sites — Public facing sites.</span></span> <span data-ttu-id="8cdd1-187">Aproveite o Azure AD para contas de clientes e autenticação.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-187">Take advantage of Azure AD for customer accounts and authentication.</span></span> 
    
- <span data-ttu-id="8cdd1-188">Ambientes de desenvolvimento, teste e preparação — rapidamente provisionar e desprovisionar ambientes inteiros.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-188">Developer, test, and staging environments — Quickly provision and deprovision entire environments.</span></span> 
    
- <span data-ttu-id="8cdd1-189">Aplicativos híbridos — aplicativos que abrangem seu datacenter e a nuvem.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-189">Hybrid applications — Applications that span your datacenter and the cloud.</span></span> 
    
- <span data-ttu-id="8cdd1-190">Ambiente de recuperação de desastres — recupere rapidamente de um desastre.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-190">Disaster recovery environment — Quickly recover from a disaster.</span></span> <span data-ttu-id="8cdd1-191">Pagar somente para uso.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-191">Pay only for use.</span></span> 
    
- <span data-ttu-id="8cdd1-192">Farms que exigem relatórios ou auditoria profundas.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-192">Farms that require deep reporting or auditing.</span></span> 
    
- <span data-ttu-id="8cdd1-193">Web Analytics.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-193">Web analytics.</span></span> 
    
- <span data-ttu-id="8cdd1-194">Criptografia de dados em repouso (os dados são criptografados nos bancos de dados SQL).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-194">Data encryption at rest (data is encrypted in the SQL databases).</span></span> 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a><span data-ttu-id="8cdd1-195">Criptografia de dados em repouso (os dados são criptografados nos bancos de dados SQL)</span><span class="sxs-lookup"><span data-stu-id="8cdd1-195">Data encryption at rest (data is encrypted in the SQL databases)</span></span>

- <span data-ttu-id="8cdd1-196">Farms no país (quando os dados precisam residir em uma jurisdição).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-196">In-country farms (when data is required to reside within a jurisdiction).</span></span> 
    
- <span data-ttu-id="8cdd1-197">Soluções complexas de BI que devem residir perto de BI de dados.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-197">Complex BI solutions that must reside close to BI data.</span></span> 
    
- <span data-ttu-id="8cdd1-198">Soluções de nuvem privada.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-198">Private cloud solutions.</span></span> 
    
- <span data-ttu-id="8cdd1-199">Soluções altamente personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-199">Highly customized solutions.</span></span> 
    
- <span data-ttu-id="8cdd1-200">Soluções legadas com componentes de terceiros que dependem de hardware e software que não são suportados nos serviços de infraestrutura do Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-200">Legacy solutions with third-party components that depend on hardware and software that are not supported on Azure Infrastructure Services.</span></span> 
    
- <span data-ttu-id="8cdd1-201">Restrições de privacidade que impedem a sincronização de contas do Active Directory com o Azure Active Directory (um requisito para o Office 365).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-201">Privacy restrictions that prevent synchronization of Active Directory accounts with Azure Active Directory (a requirement for Office 365).</span></span> 
    
- <span data-ttu-id="8cdd1-202">Organizações que preferem o controle de toda a plataforma e solução.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-202">Organizations that prefer control of the entire platform and solution.</span></span> 
    
### <a name="license-requirements"></a><span data-ttu-id="8cdd1-203">Requisitos de licença</span><span class="sxs-lookup"><span data-stu-id="8cdd1-203">License requirements</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="8cdd1-204">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-204">SharePoint 2013 in Office 365</span></span>

<span data-ttu-id="8cdd1-205">Modelo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-205">Subscription model.</span></span> <span data-ttu-id="8cdd1-206">Nenhuma licença adicional necessária.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-206">No additional licenses needed.</span></span> 
  
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="8cdd1-207">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-207">Hybrid with Office 365</span></span>

- <span data-ttu-id="8cdd1-208">Office 365 – modelo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-208">Office 365 — Subscription model.</span></span> <span data-ttu-id="8cdd1-209">Nenhuma licença adicional necessária.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-209">No additional licenses needed.</span></span> 
    
- <span data-ttu-id="8cdd1-210">Local – todas as licenças locais são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-210">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="8cdd1-211">Azure</span><span class="sxs-lookup"><span data-stu-id="8cdd1-211">Azure</span></span>

-  <span data-ttu-id="8cdd1-212">Assinatura do Azure (inclui o sistema operacional do servidor)</span><span class="sxs-lookup"><span data-stu-id="8cdd1-212">Azure subscription (includes the server operating system)</span></span>
    
- <span data-ttu-id="8cdd1-213">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8cdd1-213">SQL Server</span></span> 
    
- <span data-ttu-id="8cdd1-214">Licença de servidor do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8cdd1-214">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="8cdd1-215">Licença de acesso para cliente do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8cdd1-215">SharePoint 2013 Client Access License</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="8cdd1-216">Local</span><span class="sxs-lookup"><span data-stu-id="8cdd1-216">On premises</span></span>

- <span data-ttu-id="8cdd1-217">Sistema operacional do servidor</span><span class="sxs-lookup"><span data-stu-id="8cdd1-217">Server operating system</span></span> 
    
- <span data-ttu-id="8cdd1-218">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8cdd1-218">SQL Server</span></span> 
    
- <span data-ttu-id="8cdd1-219">Licença de servidor do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8cdd1-219">SharePoint 2013 Server License</span></span> 
    
- <span data-ttu-id="8cdd1-220">Licença de acesso para cliente do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="8cdd1-220">SharePoint 2013 Client Access License</span></span> 
    
### <a name="architecture-tasks"></a><span data-ttu-id="8cdd1-221">Tarefas de arquitetura</span><span class="sxs-lookup"><span data-stu-id="8cdd1-221">Architecture tasks</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="8cdd1-222">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-222">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="8cdd1-223">Planejar e projetar a integração de diretórios.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-223">Plan and design directory integration.</span></span> <span data-ttu-id="8cdd1-224">Duas opções.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-224">Two options.</span></span> <span data-ttu-id="8cdd1-225">Qualquer uma das opções pode ser implantada no local ou no Azure: a sincronização de senha (requer o servidor de 1 64 bits).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-225">Either option can be deployed on premises or in Azure: Password sync (requires one 64-bit server).</span></span> <span data-ttu-id="8cdd1-226">SSO (requer o AD FS e vários servidores).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-226">SSO (requires AD FS and multiple servers).</span></span> 
    
- <span data-ttu-id="8cdd1-227">Garantir a capacidade e a disponibilidade da rede por meio de firewalls, servidores de proxy, gateways e entre links de WAN.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-227">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span> 
    
- <span data-ttu-id="8cdd1-228">Adquirir certificados SSL de terceiros para oferecer segurança corporativa para ofertas de serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-228">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span> 
    
- <span data-ttu-id="8cdd1-229">Planeje o nome do locatário e projete a arquitetura e a governança do conjunto de sites.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-229">Plan the tenant name, and design the site collection architecture and governance.</span></span> 
    
- <span data-ttu-id="8cdd1-230">Planejar personalizações, soluções e aplicativos para o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-230">Plan customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="8cdd1-231">Decida se você deseja se conectar ao Office 365 usando o protocolo de Internet 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="8cdd1-231">Decide if you want to connect to Office 365 by using the Internet Protocol 6 (IPv6).</span></span> <span data-ttu-id="8cdd1-232">Isso não é comum.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-232">This is not common.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="8cdd1-233">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-233">Hybrid with Office 365</span></span>

<span data-ttu-id="8cdd1-234">Além das tarefas para os ambientes do Office 365 e local:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-234">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="8cdd1-235">Determine quanta integração de recursos você deseja e escolha a topologia híbrida.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-235">Determine how much feature integration you want and choose the hybrid topology.</span></span> <span data-ttu-id="8cdd1-236">Consulte este pôster de modelo: qual topologia híbrida devo usar?</span><span class="sxs-lookup"><span data-stu-id="8cdd1-236">See this model poster: Which hybrid topology should I use?</span></span> 
    
- <span data-ttu-id="8cdd1-237">Se necessário, determine qual dispositivo de servidor proxy será usado.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-237">If required, determine which proxy server device will be used.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="8cdd1-238">Azure</span><span class="sxs-lookup"><span data-stu-id="8cdd1-238">Azure</span></span>

<span data-ttu-id="8cdd1-239">Projete o ambiente de rede do Azure:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-239">Design the Azure network environment:</span></span> 
  
- <span data-ttu-id="8cdd1-240">Rede virtual no Azure, incluindo sub-redes.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-240">Virtual network within Azure, including subnets.</span></span> 
    
- <span data-ttu-id="8cdd1-241">Ambiente de domínio e integração com servidores locais.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-241">Domain environment and integration with on-premises servers.</span></span> 
    
- <span data-ttu-id="8cdd1-242">Endereços IP e DNS.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-242">IP addresses and DNS.</span></span> 
    
- <span data-ttu-id="8cdd1-243">Grupos de afinidade e contas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-243">Affinity groups and storage accounts.</span></span> 
    
<span data-ttu-id="8cdd1-244">Projete o ambiente do SharePoint no Azure:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-244">Design the SharePoint environment in Azure:</span></span> 
  
- <span data-ttu-id="8cdd1-245">Topologia de farm do SharePoint e arquitetura lógica.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-245">SharePoint farm topology and logical architecture.</span></span> 
    
-  <span data-ttu-id="8cdd1-246">Conjuntos de disponibilidade do Azure e atualizar domínios.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-246">Azure availability sets and update domains.</span></span>
    
- <span data-ttu-id="8cdd1-247">Tamanhos de máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-247">Virtual machines sizes.</span></span> 
    
- <span data-ttu-id="8cdd1-248">Ponto de extremidade com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-248">Load balanced endpoint.</span></span> 
    
- <span data-ttu-id="8cdd1-249">Pontos de extremidade externos para acesso público, se for preferível.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-249">External endpoints for public access, if that is preferable.</span></span> 
    
- <span data-ttu-id="8cdd1-250">Ambiente de recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-250">Disaster recovery environment.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="8cdd1-251">Local</span><span class="sxs-lookup"><span data-stu-id="8cdd1-251">On premises</span></span>

<span data-ttu-id="8cdd1-252">Projetar o ambiente do SharePoint em um ambiente local existente:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-252">Design the SharePoint environment in an existing on-premises environment:</span></span> 
  
- <span data-ttu-id="8cdd1-253">Topologia de farm do SharePoint e arquitetura lógica.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-253">SharePoint farm topology and logical architecture.</span></span> 
    
- <span data-ttu-id="8cdd1-254">Hardware do servidor.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-254">Server hardware.</span></span> 
    
- <span data-ttu-id="8cdd1-255">Ambiente virtual, se usado.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-255">Virtual environment, if used.</span></span> 
    
- <span data-ttu-id="8cdd1-256">Balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-256">Load balancing.</span></span> 
    
- <span data-ttu-id="8cdd1-257">Integração com o AD DS e o DNS.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-257">Integration with AD DS and DNS.</span></span> 
    
- <span data-ttu-id="8cdd1-258">Ambiente de recuperação de desastres.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-258">Disaster recovery environment.</span></span> 
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="8cdd1-259">Responsabilidades de profissionais de ti</span><span class="sxs-lookup"><span data-stu-id="8cdd1-259">IT pro responsibilities</span></span>

#### <a name="sharepoint-2013-in-office-365"></a><span data-ttu-id="8cdd1-260">SharePoint 2013 no Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-260">SharePoint 2013 in Office 365</span></span>

- <span data-ttu-id="8cdd1-261">Verifique se as estações de trabalho de usuário atendem aos pré-requisitos de cliente do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-261">Ensure user workstations meet Office 365 client prerequisites.</span></span> 
    
- <span data-ttu-id="8cdd1-262">Implementar o plano de integração de diretórios.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-262">Implement the directory integration plan.</span></span> 
    
- <span data-ttu-id="8cdd1-263">Planejar e implementar registros DNS internos e externos e roteamento.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-263">Plan and implement internal and external DNS records and routing.</span></span> 
    
- <span data-ttu-id="8cdd1-264">Configure o proxy ou firewall para os requisitos de URL e endereço IP do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-264">Configure the proxy or firewall for Office 365 IP address and URL requirements.</span></span> 
    
- <span data-ttu-id="8cdd1-265">Criar e atribuir permissões a conjuntos de sites.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-265">Create and assign permissions to site collections.</span></span> 
    
- <span data-ttu-id="8cdd1-266">Implementar personalizações, soluções e aplicativos para o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-266">Implement customizations, solutions, and apps for SharePoint Online.</span></span> 
    
- <span data-ttu-id="8cdd1-267">Monitorar a disponibilidade da rede e identificar possíveis afunilamentos.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-267">Monitor network availability and identify possible bottlenecks.</span></span> 
    
#### <a name="hybrid-with-office-365"></a><span data-ttu-id="8cdd1-268">Híbrido com o Office 365</span><span class="sxs-lookup"><span data-stu-id="8cdd1-268">Hybrid with Office 365</span></span>

<span data-ttu-id="8cdd1-269">Além das tarefas para os ambientes do Office 365 e local:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-269">In addition to tasks for both the Office 365 and on-premises environments:</span></span> 
  
- <span data-ttu-id="8cdd1-270">Configure o dispositivo de servidor proxy, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-270">Configure the proxy server device, if required.</span></span> 
    
- <span data-ttu-id="8cdd1-271">Configure a infraestrutura de gerenciamento de identidade híbrida: autenticação de SSO e servidor para servidor entre os dois ambientes.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-271">Configure the hybrid identity management infrastructure: SSO and server-to-server authentication between the two environments.</span></span> 
    
- <span data-ttu-id="8cdd1-272">Configure a integração dos recursos escolhidos: Search, BCS, Duet Enterprise online.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-272">Configure the integration of chosen features: Search, BCS, Duet Enterprise Online.</span></span> 
    
#### <a name="azure"></a><span data-ttu-id="8cdd1-273">Azure</span><span class="sxs-lookup"><span data-stu-id="8cdd1-273">Azure</span></span>

<span data-ttu-id="8cdd1-274">Implantar e gerenciar o ambiente do Azure e do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-274">Deploy and manage the Azure and SharePoint environment:</span></span> 
  
- <span data-ttu-id="8cdd1-275">Implementar e gerenciar o ambiente de rede do Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-275">Implement and manage the Azure network environment.</span></span> 
    
- <span data-ttu-id="8cdd1-276">Implantar o ambiente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-276">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="8cdd1-277">Atualizar servidores de farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-277">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="8cdd1-278">Adicionar ou desligar máquinas virtuais conforme necessário com base na utilização do farm.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-278">Add or shut down virtual machines as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="8cdd1-279">Aumentar ou diminuir tamanhos de máquina virtual, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-279">Increase or decrease virtual machine sizes, as needed.</span></span> 
    
- <span data-ttu-id="8cdd1-280">Faça backup do ambiente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-280">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="8cdd1-281">Implementar o ambiente de recuperação de desastres e o protocolo.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-281">Implement the disaster recovery environment and protocol.</span></span> 
    
#### <a name="on-premises"></a><span data-ttu-id="8cdd1-282">Local</span><span class="sxs-lookup"><span data-stu-id="8cdd1-282">On premises</span></span>

<span data-ttu-id="8cdd1-283">Implantar e gerenciar o ambiente local do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-283">Deploy and manage the SharePoint on premises environment:</span></span> 
  
- <span data-ttu-id="8cdd1-284">Provisionar servidores.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-284">Provision servers.</span></span> 
    
- <span data-ttu-id="8cdd1-285">Implantar o ambiente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-285">Deploy the SharePoint environment.</span></span> 
    
- <span data-ttu-id="8cdd1-286">Atualizar servidores de farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-286">Update SharePoint farm servers.</span></span> 
    
- <span data-ttu-id="8cdd1-287">Adicione ou remova servidores de farm conforme necessário com base na utilização do farm.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-287">Add or remove farm servers as needed based on farm utilization.</span></span> 
    
- <span data-ttu-id="8cdd1-288">Faça backup do ambiente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-288">Back up the SharePoint environment.</span></span> 
    
- <span data-ttu-id="8cdd1-289">Implementar o ambiente de recuperação de desastres e o protocolo.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-289">Implement the disaster recovery environment and protocol.</span></span> 
    
## <a name="three-typical-workloads-to-move-to-azure"></a><span data-ttu-id="8cdd1-290">Três cargas de trabalho típicas para mover para o Azure</span><span class="sxs-lookup"><span data-stu-id="8cdd1-290">Three typical workloads to move to Azure</span></span>

### <a name="office-365-plus-directory-components-in-azure"></a><span data-ttu-id="8cdd1-291">Office 365 mais componentes de diretório no Azure</span><span class="sxs-lookup"><span data-stu-id="8cdd1-291">Office 365 plus Directory Components in Azure</span></span>

<span data-ttu-id="8cdd1-292">Implantar os componentes de integração de diretório do Office 365 no Azure é mais rápido porque pode implantar máquinas virtuais sob demanda.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-292">Deploying Office 365 directory integration components in Azure is faster because it can deploy virtual machines on-demand.</span></span> 
  
#### <a name="directory-synchronization-server-only"></a><span data-ttu-id="8cdd1-293">Somente servidor de sincronização de diretório</span><span class="sxs-lookup"><span data-stu-id="8cdd1-293">Directory synchronization server only</span></span>

<span data-ttu-id="8cdd1-294">Em vez de implantar o servidor de sincronização de diretório de 64 bits no seu ambiente local, Provisione uma máquina virtual no Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-294">Instead of deploying the 64-bit directory synchronization server in your on-premises environment, provision a virtual machine in Azure instead.</span></span> 
  
<span data-ttu-id="8cdd1-295">O diagrama a seguir mostra o SharePoint Online com um locatário do Azure Active Directory, que sincroniza nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-295">The accompanying diagram shows SharePoint Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span> 
  
#### <a name="directory-synchronization-plus-ad-fs"></a><span data-ttu-id="8cdd1-296">Sincronização de diretórios e AD FS</span><span class="sxs-lookup"><span data-stu-id="8cdd1-296">Directory synchronization plus AD FS</span></span>

<span data-ttu-id="8cdd1-297">Essa opção permite que você ofereça suporte a identidades federadas do Office 365 (SSO) sem adicionar hardware à sua infraestrutura local.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-297">This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure.</span></span> <span data-ttu-id="8cdd1-298">Também fornece resiliência se o ambiente do Active Directory local não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-298">It also provides resiliency if the on-premises Active Directory environment is unavailable.</span></span> 
  
- <span data-ttu-id="8cdd1-299">Os componentes de integração de diretórios residem no Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-299">Directory integration components reside in Azure.</span></span> 
    
- <span data-ttu-id="8cdd1-300">O AD FS é publicado na Internet por meio de proxies do AD FS no Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-300">AD FS is published to the Internet through AD FS proxies in Azure.</span></span> 
    
- <span data-ttu-id="8cdd1-301">O tráfego de autenticação do cliente, para usuários que estão se conectando de qualquer local, é tratado por servidores e proxies do AD FS implantados no Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-301">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed on Azure.</span></span> 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a><span data-ttu-id="8cdd1-302">Site voltado para o público e o Azure AD para autenticação de clientes</span><span class="sxs-lookup"><span data-stu-id="8cdd1-302">Public-facing Internet site and Azure AD for customer authentication</span></span>

<span data-ttu-id="8cdd1-303">Aproveite a capacidade de expansão fácil para a demanda, colocando seu site na Internet no Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-303">Take advantage of the ability to easily scale to demand by placing your Internet site in Azure.</span></span> <span data-ttu-id="8cdd1-304">Use o Azure AD para armazenar contas de cliente.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-304">Use Azure AD to store customer accounts.</span></span> 
  
#### <a name="azure-advantages-for-internet-sites"></a><span data-ttu-id="8cdd1-305">Vantagens do Azure para sites da Internet</span><span class="sxs-lookup"><span data-stu-id="8cdd1-305">Azure advantages for Internet sites</span></span>

- <span data-ttu-id="8cdd1-306">Pague apenas os recursos necessários, dimensionando o número de máquinas virtuais com base na utilização do farm.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-306">Pay only for the resources you need by scaling the number of virtual machines based on farm utilization.</span></span> 
    
- <span data-ttu-id="8cdd1-307">Adicione relatórios detalhados e análises da Web.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-307">Add deep reporting and web analytics.</span></span> 
    
- <span data-ttu-id="8cdd1-308">Concentre-se no desenvolvimento de um ótimo site, em vez de criar uma infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-308">Focus on developing a great site rather than building infrastructure.</span></span> 
    
#### <a name="azure-ad"></a><span data-ttu-id="8cdd1-309">Azure AD</span><span class="sxs-lookup"><span data-stu-id="8cdd1-309">Azure AD</span></span>

<span data-ttu-id="8cdd1-310">O Azure AD fornece recursos de gerenciamento de identidades e controle de acesso para serviços em nuvem.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-310">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="8cdd1-311">Os recursos incluem um repositório baseado em nuvem para dados de diretório e um conjunto principal de serviços de identidade, incluindo processos de logon do usuário, serviços de autenticação e AD FS.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-311">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="8cdd1-312">Os serviços de identidade que estão incluídos no Azure AD se integram facilmente às implantações do Active Directory local e dão suporte completo a provedores de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-312">The identity services that are included with Azure AD easily integrate with your on-premises Active Directory deployments and fully support third-party identity providers.</span></span> 
  
<span data-ttu-id="8cdd1-313">O diagrama a seguir mostra a configuração de zonas e autenticação importantes para sites voltados para a Internet.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-313">The accompanying diagram shows the configuration of zones and authentication that is important for Internet-facing sites.</span></span> <span data-ttu-id="8cdd1-314">O diagrama mostra o locatário do Azure Active Directory, que contém um farm do SharePoint no Azure com duas zonas:</span><span class="sxs-lookup"><span data-stu-id="8cdd1-314">The diagram shows the Azure Active Directory Tenant, which contains a SharePoint Farm on Azure with two zones:</span></span> 
  
- <span data-ttu-id="8cdd1-315">Uma zona da Internet que interage com visitantes anônimos e autenticados e clientes fora da rede</span><span class="sxs-lookup"><span data-stu-id="8cdd1-315">An Internet zone that interacts with Anonymous and Authenticated visitors and customers outside the network</span></span> 
    
- <span data-ttu-id="8cdd1-316">Uma zona padrão que contém NTLM para rastreamento e autenticação do Windows que interage com sua implantação local do Active Directory em um túnel VPN.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-316">A default zone that contains NTLM for Crawl and Windows Authentication that interacts with your on-premises Active Directory deployment over a VPN tunnel.</span></span> 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a><span data-ttu-id="8cdd1-317">Farm local mais recuperação de desastre no Azure</span><span class="sxs-lookup"><span data-stu-id="8cdd1-317">On-premises Farm plus Disaster Recovery in Azure</span></span>

<span data-ttu-id="8cdd1-318">Escolha uma opção de recuperação de desastres que corresponda aos seus requisitos de negócios.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-318">Choose a disaster recovery option that matches your business requirements.</span></span> <span data-ttu-id="8cdd1-319">O Azure fornece opções de nível de entrada para empresas que são introdução à recuperação de desastres e opções avançadas para empresas com requisitos de alta resiliência.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-319">Azure provides entry-level options for companies getting started with disaster recovery and advanced options for enterprises with high resiliency requirements.</span></span> 
  
#### <a name="cold-standby"></a><span data-ttu-id="8cdd1-320">Espera Cold</span><span class="sxs-lookup"><span data-stu-id="8cdd1-320">Cold standby</span></span>

- <span data-ttu-id="8cdd1-321">O farm está totalmente construído, mas as máquinas virtuais são interrompidas.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-321">The farm is fully built, but the virtual machines are stopped.</span></span> <span data-ttu-id="8cdd1-322">(Você está pagando apenas quando estão executando!)</span><span class="sxs-lookup"><span data-stu-id="8cdd1-322">(You're paying only when they're running!)</span></span> 
    
- <span data-ttu-id="8cdd1-323">A manutenção do ambiente inclui o início das máquinas virtuais de hora para hora, aplicação de patch, atualização e verificação do ambiente.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-323">Maintaining the environment includes starting the virtual machines from time-to-time, patching, updating, and verifying the environment.</span></span> 
    
- <span data-ttu-id="8cdd1-324">Inicie o ambiente completo em caso de desastre.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-324">Start the full environment in the event of a disaster.</span></span> 
    
#### <a name="warm-standby"></a><span data-ttu-id="8cdd1-325">Espera passiva</span><span class="sxs-lookup"><span data-stu-id="8cdd1-325">Warm standby</span></span>

- <span data-ttu-id="8cdd1-326">Isso inclui um pequeno farm que é provisionado e em execução.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-326">This includes a small farm that is provisioned and running.</span></span> 
    
- <span data-ttu-id="8cdd1-327">O farm pode servir imediatamente aos usuários em caso de failover.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-327">The farm can immediately serve users in the event of a failover.</span></span> 
    
- <span data-ttu-id="8cdd1-328">Expanda o farm rapidamente para atender à base completa do usuário.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-328">Scale out the farm quickly to serve the full user base.</span></span> 
    
#### <a name="hot-standby"></a><span data-ttu-id="8cdd1-329">Espera ativa</span><span class="sxs-lookup"><span data-stu-id="8cdd1-329">Hot standby</span></span>

<span data-ttu-id="8cdd1-330">Um farm de tamanho completo é provisionado e executado no modo de espera.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-330">A fully-sized farm is provisioned and running on standby.</span></span> 
  
<span data-ttu-id="8cdd1-331">O diagrama a seguir mostra um farm local interagindo com o ambiente de recuperação de desastres do SharePoint no Azure.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-331">The accompanying diagram shows an on-premises farm interacting with the SharePoint Disaster Recovery Environment on Azure.</span></span> <span data-ttu-id="8cdd1-332">Os bancos de dados locais usam o envio de logs do SQL Server sobre o túnel VPN para acessar o ambiente de recuperação de desastres do SharePoint, que inclui dois servidores de banco de dados SQL que contêm os bancos de dados do SharePoint, dois servidores Web front-end e dois SharePoint Servidores de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8cdd1-332">The on-premises databases use SQL Server Log Shipping over the VPN tunnel to access the SharePoint Disaster Recovery environment, which includes two SQL database servers that contain the SharePoint databases, two Web Front End servers, and two SharePoint Application servers.</span></span> 
  

