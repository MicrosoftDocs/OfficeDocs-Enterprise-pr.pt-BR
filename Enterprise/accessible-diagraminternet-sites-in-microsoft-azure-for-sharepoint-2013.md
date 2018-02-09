---
title: "Diagrama acessível - sites da Internet no Microsoft Azure para o SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: "Este artigo é uma versão de texto acessível do diagrama denominada sites da Internet no Microsoft Azure para SharePoint 2013."
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="3c443-103">Diagrama acessível - sites da Internet no Microsoft Azure para o SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="3c443-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="3c443-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama denominada sites da Internet no Microsoft Azure para SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="3c443-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="3c443-p101">Este pôster descreve e ilustra como público benefícios de sites de Internet do Azure AD para contas de cliente e de nuvem elasticidade. Há seis diferentes cenários que descrevem como sites da Internet se beneficiar do Azure:</span><span class="sxs-lookup"><span data-stu-id="3c443-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="3c443-107">Criar e dimensionar a topologia de farm.</span><span class="sxs-lookup"><span data-stu-id="3c443-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="3c443-108">Ajuste para Azure.</span><span class="sxs-lookup"><span data-stu-id="3c443-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="3c443-109">Escolha o modelo do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3c443-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="3c443-110">Design para gerenciamento de identidade, zonas e autenticação.</span><span class="sxs-lookup"><span data-stu-id="3c443-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="3c443-111">Design de sites e URLs para publicação intersite.</span><span class="sxs-lookup"><span data-stu-id="3c443-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="3c443-112">Projete o ambiente do Azure.</span><span class="sxs-lookup"><span data-stu-id="3c443-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="3c443-113">Criar e dimensionar a topologia de farm</span><span class="sxs-lookup"><span data-stu-id="3c443-113">Design and size the farm topology</span></span>

<span data-ttu-id="3c443-114">Use as diretrizes de topologia, a capacidade e desempenho para o SharePoint 2013 no TechNet para desenhar a topologia de farm.</span><span class="sxs-lookup"><span data-stu-id="3c443-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="3c443-115">Certifique-se de que o farm que você projetar cumpre os objetivos de desempenho e capacidade.</span><span class="sxs-lookup"><span data-stu-id="3c443-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="3c443-116">Exemplo: Farm médio Sites da Internet (~ 85 exibições de página por segundo)</span><span class="sxs-lookup"><span data-stu-id="3c443-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="3c443-117">Este farm fornece uma topologia de farm de pesquisa do SharePoint 2013 tolerante a falhas que é otimizada para um corpus que contém 3,400,000 itens.</span><span class="sxs-lookup"><span data-stu-id="3c443-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="3c443-118">O farm de exemplo processa os documentos de 100 a 200 por segundo, dependendo do idioma, e ele acomoda 85 visualizações de página por segunda e 100 consultas por segundo.</span><span class="sxs-lookup"><span data-stu-id="3c443-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="3c443-119">O diagrama acompanha mostra um farm médio de sites de internet com três tipos de servidores:</span><span class="sxs-lookup"><span data-stu-id="3c443-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="3c443-120">Servidores da Web</span><span class="sxs-lookup"><span data-stu-id="3c443-120">Web servers</span></span> 
    
- <span data-ttu-id="3c443-121">Servidores de aplicativos</span><span class="sxs-lookup"><span data-stu-id="3c443-121">Application servers</span></span> 
    
- <span data-ttu-id="3c443-122">Servidores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="3c443-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="3c443-123">Servidores Web</span><span class="sxs-lookup"><span data-stu-id="3c443-123">Web servers</span></span>

<span data-ttu-id="3c443-p102">Na seção de servidores web, há três servidores web, Host A, Host B e c de Host. Cada servidor web contém um cache distribuído, perfis de usuário, metadados gerenciados e recursos de processamento de consultas. Eles também contêm uma réplica da partição de índice que está em cada servidor.</span><span class="sxs-lookup"><span data-stu-id="3c443-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="3c443-126">Para dimensionar, adicionar um servidor de web adicionais com os mesmos recursos, o que permite uma 28 adicionais de exibições de página por segundo.</span><span class="sxs-lookup"><span data-stu-id="3c443-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="3c443-127">Servidores de aplicativos</span><span class="sxs-lookup"><span data-stu-id="3c443-127">Application servers</span></span>

<span data-ttu-id="3c443-p103">Na seção servidores de aplicativo, há três servidores de aplicativos, Host D, F de Host, e Host F. Host D contém os componentes de processamento de rastreamento, administração, análise e conteúdo. Host E contém os componentes de processamento de rastreamento, administração e de conteúdo. Host F contém os componentes de processamento de conteúdo e de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3c443-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="3c443-131">Para dimensionar, adicione um servidor de aplicativos com um componente de rastreamento e um componente para processar uma documentos adicionais de 40 por segundo de processamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3c443-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="3c443-132">Servidores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="3c443-132">Database servers</span></span>

<span data-ttu-id="3c443-133">Na seção servidores de banco de dados, existem dois servidores Host G e h de Host. Os servidores de banco de dados estão em hosts emparelhados para tolerância a falhas.</span><span class="sxs-lookup"><span data-stu-id="3c443-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="3c443-p104">Host G contém o banco de dados do SharePoint todos, incluindo o banco de dados vinculado, banco de dados de administração de pesquisa, dois bancos de dados de rastreamento, um banco de dados de análise e todos os outros bancos de dados do SharePoint. Host H contém os bancos de dados do SharePoint todos, inclusive cópias redundantes de todos os bancos de dados usando o SQL clustering, espelhamento ou SQL Server 2012 AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="3c443-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="3c443-136">Ajuste para o Windows Azure</span><span class="sxs-lookup"><span data-stu-id="3c443-136">Fine-tune for Azure</span></span>

<span data-ttu-id="3c443-p105">O farm do SharePoint talvez precisem ser ajustadas para conjuntos de disponibilidade na plataforma Windows Azure. Para garantir a alta disponibilidade de todos os componentes, certifique-se de que as funções de servidor tudo identicamente são configuradas.</span><span class="sxs-lookup"><span data-stu-id="3c443-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="3c443-139">Na topologia de exemplo no diagrama:</span><span class="sxs-lookup"><span data-stu-id="3c443-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="3c443-140">Os servidores web e os servidores de banco de dados são configurados de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="3c443-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="3c443-p106">Os servidores de três aplicativos não são configurados de forma idêntica. Essas funções de servidor requerem o ajuste fino para disponibilidade define no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="3c443-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="3c443-143">Antes</span><span class="sxs-lookup"><span data-stu-id="3c443-143">Before</span></span>

<span data-ttu-id="3c443-p107">A parte superior do diagrama mostra o farm do SharePoint antes que ele tenha sido ajustado para disponibilidade define no Windows Azure. No diagrama, os servidores de aplicativos de três do host não são identicamente configurados. O número de componentes é determinado pelas metas de desempenho e capacidade para o farm. Três servidores são configurados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3c443-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="3c443-148">Servidor de aplicativos host D é configurado com as funções de processamento de rastreamento, administração, análise e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3c443-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="3c443-149">Servidor de aplicativos host f é configurado com as funções de processamento de rastreamento, administração e de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3c443-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="3c443-150">Servidor de aplicativos host F é configurado com funções de processamento de conteúdo e de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3c443-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="3c443-151">After</span><span class="sxs-lookup"><span data-stu-id="3c443-151">After</span></span>

<span data-ttu-id="3c443-p108">Esta parte do diagrama mostra o farm do SharePoint depois que ele tenha sido ajustado para disponibilidade define no Windows Azure. Para adaptar-se essa arquitetura para o Windows Azure, podemos vai replicar quatro componentes em todos os três servidores. Isso aumenta o número de componentes além do que é necessário para desempenho e capacidade. A desvantagem é que esse design garante a alta disponibilidade de todos os quatro componentes na plataforma Windows Azure quando essas três máquinas virtuais são atribuídas a um conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="3c443-p108">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="3c443-156">Três servidores estiverem configurados para todos têm as funções de processamento de rastreamento, administração, análise e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3c443-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="3c443-157">Escolha o modelo do Active Directory</span><span class="sxs-lookup"><span data-stu-id="3c443-157">Choose the Active Directory model</span></span>

<span data-ttu-id="3c443-p109">Todas as soluções do SharePoint exigem o Windows Active Directory Domain Services (AD DS). Neste momento, há duas opções para soluções do SharePoint no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="3c443-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="3c443-p110">Opção 1: De domínio dedicado — você pode implantar um domínio dedicado e isolado no Azure para oferecer suporte a um farm do SharePoint. Esta é uma boa opção para sites da Internet público.</span><span class="sxs-lookup"><span data-stu-id="3c443-p110">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm. This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="3c443-p111">Opção 2: Estenda o domínio local por meio de uma conexão de VPN-to-site. Quando você estende o domínio local por meio de uma conexão VPN de site a site, os usuários acessar o farm do SharePoint como se estivesse hospedado no local. Você pode tirar proveito das suas implementações existentes do Active Directory e DNS.</span><span class="sxs-lookup"><span data-stu-id="3c443-p111">Option 2: Extend the on-premises domain through a site-to-site VPN connection. When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises. You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="3c443-165">Design para gerenciamento de identidade, zonas e autenticação</span><span class="sxs-lookup"><span data-stu-id="3c443-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="3c443-166">Design para contas e autenticação</span><span class="sxs-lookup"><span data-stu-id="3c443-166">Design for accounts and authentication</span></span>

<span data-ttu-id="3c443-167">Determine como contas serão gerenciadas e qual tipo de autenticação será usado.</span><span class="sxs-lookup"><span data-stu-id="3c443-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="3c443-168">Contas para autores e desenvolvedores de site</span><span class="sxs-lookup"><span data-stu-id="3c443-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="3c443-169">Adicione contas ao domínio no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="3c443-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="3c443-170">Use os serviços de Federação do Active Directory (AD FS) no local para estabelecer uma federação as contas internas no domínio no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="3c443-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="3c443-171">Se o design inclui uma conexão VPN de site a site, use as contas internas.</span><span class="sxs-lookup"><span data-stu-id="3c443-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="3c443-172">Contas para clientes</span><span class="sxs-lookup"><span data-stu-id="3c443-172">Accounts for customers</span></span>

- <span data-ttu-id="3c443-173">Use o Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3c443-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="3c443-174">Use um provedor de SAML-based diferente.</span><span class="sxs-lookup"><span data-stu-id="3c443-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="3c443-175">Design de zonas</span><span class="sxs-lookup"><span data-stu-id="3c443-175">Design for zones</span></span>

<span data-ttu-id="3c443-176">No SharePoint 2013, gerenciamento de identidade é acrescentado na configuração de zonas e autenticação.</span><span class="sxs-lookup"><span data-stu-id="3c443-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="3c443-177">Esse design fornece a separação clara de contas do cliente de todas as outras contas.</span><span class="sxs-lookup"><span data-stu-id="3c443-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="3c443-178">Use esse design, se você quiser contas de cliente a ser tratada completamente diferente do que as contas internas para autores e desenvolvedores de site.</span><span class="sxs-lookup"><span data-stu-id="3c443-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="3c443-179">Usando esse design, você pode usar políticas de zona para limitar as ações do cliente em um aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="3c443-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="3c443-180">Esse design resulta em diferentes URLs para contas de cliente e internos.</span><span class="sxs-lookup"><span data-stu-id="3c443-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="3c443-181">Neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="3c443-181">In this example:</span></span> 
  
- <span data-ttu-id="3c443-182">Configure a zona padrão para contas internas.</span><span class="sxs-lookup"><span data-stu-id="3c443-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="3c443-p112">Configure a zona extranet para acesso de cliente autenticado. Use o Azure AD (Active Directory) para contas de cliente, ou um provedor de SAML-based diferente.</span><span class="sxs-lookup"><span data-stu-id="3c443-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="3c443-185">Configure a zona da Internet para acesso anônimo.</span><span class="sxs-lookup"><span data-stu-id="3c443-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="3c443-186">Não use um design de dois-zona na qual todos os usuários autenticados são configurados para usar a zona padrão.</span><span class="sxs-lookup"><span data-stu-id="3c443-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="3c443-187">O diagrama acompanha mostra um design de três-zone com separação de internos e contas de cliente.</span><span class="sxs-lookup"><span data-stu-id="3c443-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="3c443-p113">Visitantes e clientes acessam o locatário do AD do Windows Azure no farm do SharePoint 2013 por meio de aplicativos da web em uma das duas zonas. As duas zonas incluem:</span><span class="sxs-lookup"><span data-stu-id="3c443-p113">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones. The two zones include:</span></span> 
  
- <span data-ttu-id="3c443-190">Zona: Internet para usuários anônimos</span><span class="sxs-lookup"><span data-stu-id="3c443-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="3c443-191">Zona: Extranet para usuários autenticados</span><span class="sxs-lookup"><span data-stu-id="3c443-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="3c443-p114">Usuários com contas internas acessem o locatário do Azure Active Directory do AD DS e AD FS no ambiente local através do túnel VPN para o Windows Azure AD. A zona padrão fornece autenticação do Windows (NTLM).</span><span class="sxs-lookup"><span data-stu-id="3c443-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="3c443-194">Design para conexão com o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3c443-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="3c443-p115">Azure AD fornece recursos de controle acesso e o gerenciamento de identidade para serviços de nuvem. Os recursos incluem um repositório baseado em nuvem para dados de diretório e um conjunto básico de serviços de identidade, incluindo processos de logon do usuário, serviços de autenticação e AD FS. Os serviços de identidade que estão incluídos no Windows Azure AD facilmente integram com o seu local implantações do AD DS e totalmente provedores de identidade de terceiros de suporte.</span><span class="sxs-lookup"><span data-stu-id="3c443-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="3c443-198">O diagrama acompanha mostra o cenário a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c443-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="3c443-199">Ao integrar o SharePoint 2013 com o Windows Azure Active Directory, um serviço de controle de acesso (ACS) do Azure tem duas finalidades:</span><span class="sxs-lookup"><span data-stu-id="3c443-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="3c443-p116">Azure AD usa SAML 2.0 e SharePoint só funciona com o SAML 1.1. ACS entende ambos os formatos e serve como intermediário para transformar os tokens formatos entre o SharePoint e o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3c443-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="3c443-202">ACS substitui a necessidade para o provedor security token serviço identidade (IP-STS) para este cenário SAML.</span><span class="sxs-lookup"><span data-stu-id="3c443-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="3c443-203">Para obter mais informações, consulte Configure Azure AD com o SharePoint 2013 na TechNet library.</span><span class="sxs-lookup"><span data-stu-id="3c443-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="3c443-204">Projetar sites e URLs para publicação intersite</span><span class="sxs-lookup"><span data-stu-id="3c443-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="3c443-205">Um um design de aplicativo da web é recomendado para cenários de publicação.</span><span class="sxs-lookup"><span data-stu-id="3c443-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="3c443-206">Tanto a criação e publicação de sites estão no mesmo aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="3c443-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="3c443-207">Publicação intersite é usada para publicar ativos.</span><span class="sxs-lookup"><span data-stu-id="3c443-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="3c443-208">Use conjuntos de sites baseados em caminho e nome de host.</span><span class="sxs-lookup"><span data-stu-id="3c443-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="3c443-p117">Um conjunto de sites raiz é um requisito. Crie este site como um site baseado em caminho.</span><span class="sxs-lookup"><span data-stu-id="3c443-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="3c443-211">Crie todos os outros conjuntos de sites como conjuntos de sites nomeados por host.</span><span class="sxs-lookup"><span data-stu-id="3c443-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="3c443-212">URLs de site raiz e aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="3c443-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="3c443-p118">Use um nome interno para a URL do aplicativo web. SharePoint usa o nome da máquina local como o nome padrão, a menos que um nome diferente for especificado. Você pode usar um nome de domínio que está reservado para o ambiente de rede interna.</span><span class="sxs-lookup"><span data-stu-id="3c443-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="3c443-p119">SharePoint atribui um número de porta não padrão quando o aplicativo web é criado. Use esse número de porta, em vez de porta 80 ou 443. Ou use um número de porta diferente, mas não-padrão.</span><span class="sxs-lookup"><span data-stu-id="3c443-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="3c443-219">Use o mesmo nome e o número da porta para o conjunto de sites raiz, que é um conjunto de sites baseados em caminho.</span><span class="sxs-lookup"><span data-stu-id="3c443-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="3c443-p120">O diagrama acompanha mostra serviços de pool de aplicativos, como pesquisa a interação com os conjuntos de sites usando os aplicativos web. Os conjuntos de sites mostrados incluem:</span><span class="sxs-lookup"><span data-stu-id="3c443-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="3c443-222">Conjunto de sites baseados em caminho localizado em http://internal:8000 (site raiz).</span><span class="sxs-lookup"><span data-stu-id="3c443-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="3c443-223">Rastreamento: Conjuntos de sites nomeados por Host localizados em um endereço como https://authoring.contoso.com:8000.</span><span class="sxs-lookup"><span data-stu-id="3c443-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="3c443-224">Consultas: 2 conjuntos de sites nomeados por Host separados localizada endereços como:</span><span class="sxs-lookup"><span data-stu-id="3c443-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - <span data-ttu-id="3c443-225">http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3c443-225">http://www.contoso.com</span></span> 
    
  - <span data-ttu-id="3c443-226">https://Secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3c443-226">https://secure.contoso.com</span></span> 
    
  - <span data-ttu-id="3c443-227">http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="3c443-227">http://www.contoso.com:8000</span></span> 
    
  - <span data-ttu-id="3c443-228">http://Assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3c443-228">http://assets.contoso.com</span></span> 
    
  - <span data-ttu-id="3c443-229">https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="3c443-229">https://secureassets.contoso.com</span></span> 
    
  - <span data-ttu-id="3c443-230">http://Assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="3c443-230">http://assets.contoso.com:8000</span></span> 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="3c443-231">Projetar o ambiente do Azure</span><span class="sxs-lookup"><span data-stu-id="3c443-231">Design the Azure environment</span></span>

<span data-ttu-id="3c443-232">Essa arquitetura de exemplo inclui os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="3c443-232">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="3c443-233">Uma conexão de VPN-to-site é opcional e estende o local Windows AD DS e o ambiente de DNS para a rede virtual no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="3c443-233">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="3c443-234">Opcionalmente, use um domínio dedicado no Windows Azure para suportar o farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3c443-234">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="3c443-235">Servidores estão divididos entre os serviços de nuvem Azure com base na função.</span><span class="sxs-lookup"><span data-stu-id="3c443-235">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="3c443-236">Conjuntos de disponibilidade garantir a alta disponibilidade das funções de servidor configurado de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="3c443-236">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="3c443-237">Para obter mais informações, consulte o artigo a seguir no TechNet: Azure Architectures for SharePoint Solutions.</span><span class="sxs-lookup"><span data-stu-id="3c443-237">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="3c443-238">O diagrama acompanha mostra um exemplo de um ambiente local se conectar com uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="3c443-238">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="3c443-239">Estão incluídos no ambiente local, que é um elemento opcional do ambiente do Azure, os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="3c443-239">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="3c443-240">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="3c443-240">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="3c443-241">AD DS</span><span class="sxs-lookup"><span data-stu-id="3c443-241">AD DS</span></span> 
    
- <span data-ttu-id="3c443-242">Um gateway VPN do Windows Server e o AD DS para a sub-rede do Gateway de VPN ativo</span><span class="sxs-lookup"><span data-stu-id="3c443-242">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="3c443-243">O ambiente de rede virtual do Azure inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="3c443-243">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="3c443-244">A sub-rede do Gateway de VPN ativo (sobrepostas com o ambiente local, se aplicável)</span><span class="sxs-lookup"><span data-stu-id="3c443-244">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="3c443-245">Serviço de nuvem que inclui a disponibilidade do AD DS e DNS definido (dois servidores)</span><span class="sxs-lookup"><span data-stu-id="3c443-245">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="3c443-246">Serviço de nuvem que incluem a disponibilidade do servidor front-end definido (três servidores do SharePoint) e a disponibilidade do servidor de aplicativo definido (três servidores do SharePoint)</span><span class="sxs-lookup"><span data-stu-id="3c443-246">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="3c443-247">Define um serviço em nuvem que contém dois disponibilidade de banco de dados</span><span class="sxs-lookup"><span data-stu-id="3c443-247">Cloud service that contains two database availability sets</span></span> 
    

