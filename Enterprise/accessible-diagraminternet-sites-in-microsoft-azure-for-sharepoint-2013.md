---
title: Diagrama acessível-sites da Internet no Microsoft Azure para SharePoint 2013
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
description: Este artigo é uma versão de texto acessível do diagrama chamado sites da Internet no Microsoft Azure para SharePoint 2013.
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487687"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="f59d0-103">Diagrama acessível-sites da Internet no Microsoft Azure para SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="f59d0-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="f59d0-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado sites da Internet no Microsoft Azure para SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="f59d0-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="f59d0-105">Este cartaz descreve e ilustra como os sites de Internet públicos se beneficiam da elasticidade de nuvem e do Azure AD para contas de cliente.</span><span class="sxs-lookup"><span data-stu-id="f59d0-105">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts.</span></span> <span data-ttu-id="f59d0-106">Há seis cenários diferentes que descrevem como os sites da Internet se beneficiam do Azure:</span><span class="sxs-lookup"><span data-stu-id="f59d0-106">There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="f59d0-107">Projetar e dimensionar a topologia do farm.</span><span class="sxs-lookup"><span data-stu-id="f59d0-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="f59d0-108">Ajuste para o Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="f59d0-109">Escolha o modelo do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f59d0-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="f59d0-110">Design para gerenciamento de identidades, zonas e autenticação.</span><span class="sxs-lookup"><span data-stu-id="f59d0-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="f59d0-111">Criar sites e URLs para publicação entre sites.</span><span class="sxs-lookup"><span data-stu-id="f59d0-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="f59d0-112">Projetar o ambiente do Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="f59d0-113">Projetar e dimensionar a topologia do farm</span><span class="sxs-lookup"><span data-stu-id="f59d0-113">Design and size the farm topology</span></span>

<span data-ttu-id="f59d0-114">Use as diretrizes de topologia, capacidade e desempenho do SharePoint 2013 no TechNet para projetar a topologia do farm.</span><span class="sxs-lookup"><span data-stu-id="f59d0-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="f59d0-115">Verifique se o farm que você design atende aos objetivos de capacidade e desempenho.</span><span class="sxs-lookup"><span data-stu-id="f59d0-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="f59d0-116">Exemplo: farm de sites médios da Internet (~ 85 visualizações de página por segundo)</span><span class="sxs-lookup"><span data-stu-id="f59d0-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="f59d0-117">Este farm fornece uma topologia de farm de pesquisa do SharePoint 2013 tolerante a falhas que é otimizada para um corpus que contém 3,4 milhões itens.</span><span class="sxs-lookup"><span data-stu-id="f59d0-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="f59d0-118">O farm de exemplo processa documentos 100-200 por segundo, dependendo do idioma e acomoda 85 visualizações de página por segundo e 100 consultas por segundo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="f59d0-119">O diagrama a seguir mostra um farm médio de sites da Internet com três tipos de servidores:</span><span class="sxs-lookup"><span data-stu-id="f59d0-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="f59d0-120">Servidores da Web</span><span class="sxs-lookup"><span data-stu-id="f59d0-120">Web servers</span></span> 
    
- <span data-ttu-id="f59d0-121">Servidores de aplicativos</span><span class="sxs-lookup"><span data-stu-id="f59d0-121">Application servers</span></span> 
    
- <span data-ttu-id="f59d0-122">Servidores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="f59d0-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="f59d0-123">Servidores da Web</span><span class="sxs-lookup"><span data-stu-id="f59d0-123">Web servers</span></span>

<span data-ttu-id="f59d0-124">Na seção servidores Web, há três servidores Web, host A, host B e host C. Cada servidor Web contém um cache distribuído, perfis de usuário, metadados gerenciados e recursos de processamento de consultas.</span><span class="sxs-lookup"><span data-stu-id="f59d0-124">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities.</span></span> <span data-ttu-id="f59d0-125">Eles também contêm uma réplica de partição de índice que está em cada servidor.</span><span class="sxs-lookup"><span data-stu-id="f59d0-125">They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="f59d0-126">Para expandir, adicione um servidor Web adicional com os mesmos recursos, que permite a exibição de 28 páginas adicionais por segundo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="f59d0-127">Servidores de aplicativos</span><span class="sxs-lookup"><span data-stu-id="f59d0-127">Application servers</span></span>

<span data-ttu-id="f59d0-128">Na seção servidores de aplicativos, há três servidores de aplicativos, host D, host e host F. o host D contém componentes de rastreamento, administração, análise e processamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-128">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components.</span></span> <span data-ttu-id="f59d0-129">O host E contém componentes de rastreamento, administração e processamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-129">Host E contains Crawl, Admin, and Content processing components.</span></span> <span data-ttu-id="f59d0-130">O host F contém componentes de rastreamento e processamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-130">Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="f59d0-131">Para expandir, adicione um servidor de aplicativos com um componente de rastreamento e um componente de processamento de conteúdo para processar um documento adicional de 40 por segundo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="f59d0-132">Servidores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="f59d0-132">Database servers</span></span>

<span data-ttu-id="f59d0-133">Na seção servidores de banco de dados, há dois servidores, host G e host H. Os servidores de banco de dados estão em hosts emparelhados para tolerância a falhas.</span><span class="sxs-lookup"><span data-stu-id="f59d0-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="f59d0-134">O host G contém todo o banco de dados do SharePoint, incluindo o banco de dados de administração de pesquisa, o banco de dados de link, dois bancos de dados de rastreamento</span><span class="sxs-lookup"><span data-stu-id="f59d0-134">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases.</span></span> <span data-ttu-id="f59d0-135">O host H contém todos os bancos de dados do SharePoint, incluindo cópias redundantes de todos os bancos de dados usando clusters SQL, espelhamento ou SQL Server 2012 AlwaysOn.</span><span class="sxs-lookup"><span data-stu-id="f59d0-135">Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="f59d0-136">Ajuste fino para o Azure</span><span class="sxs-lookup"><span data-stu-id="f59d0-136">Fine-tune for Azure</span></span>

<span data-ttu-id="f59d0-137">Talvez seja necessário ajustar o farm do SharePoint para os conjuntos de disponibilidade na plataforma do Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-137">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform.</span></span> <span data-ttu-id="f59d0-138">Para garantir a alta disponibilidade de todos os componentes, verifique se as funções de servidor estão definidas de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="f59d0-138">To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="f59d0-139">Na topologia de exemplo no diagrama:</span><span class="sxs-lookup"><span data-stu-id="f59d0-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="f59d0-140">Os servidores Web e os servidores de banco de dados são configurados de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="f59d0-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="f59d0-141">Os três servidores de aplicativos não são configurados de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="f59d0-141">The three application servers are not identically configured.</span></span> <span data-ttu-id="f59d0-142">Essas funções de servidor exigem ajuste fino para os conjuntos de disponibilidade no Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-142">These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="f59d0-143">Before</span><span class="sxs-lookup"><span data-stu-id="f59d0-143">Before</span></span>

<span data-ttu-id="f59d0-144">A parte superior do diagrama mostra o farm do SharePoint antes que ele tenha sido ajustado para conjuntos de disponibilidade no Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-144">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="f59d0-145">No diagrama, os três servidores de aplicativos host não são configurados de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="f59d0-145">In the diagram, the three host application servers are not identically configured.</span></span> <span data-ttu-id="f59d0-146">O número de componentes é determinado pelos objetivos de desempenho e capacidade do farm.</span><span class="sxs-lookup"><span data-stu-id="f59d0-146">The number of components is determined by the performance and capacity targets for the farm.</span></span> <span data-ttu-id="f59d0-147">Os três servidores são configurados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f59d0-147">The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="f59d0-148">O servidor de aplicativos do host D é configurado com funções de rastreamento, administração, análise e processamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="f59d0-149">O servidor de aplicativos host E é configurado com as funções de rastreamento, administração e processamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="f59d0-150">O servidor de aplicativos do host F é configurado com as funções de rastreamento e processamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="f59d0-151">After</span><span class="sxs-lookup"><span data-stu-id="f59d0-151">After</span></span>

<span data-ttu-id="f59d0-152">Esta parte do diagrama mostra o farm do SharePoint após ele ter sido ajustado para conjuntos de disponibilidade no Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-152">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure.</span></span> <span data-ttu-id="f59d0-153">Para adaptar essa arquitetura para o Azure, replicaremos os quatro componentes em todos os três servidores.</span><span class="sxs-lookup"><span data-stu-id="f59d0-153">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="f59d0-154">Isso aumenta o número de componentes além do que é necessário para desempenho e capacidade.</span><span class="sxs-lookup"><span data-stu-id="f59d0-154">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="f59d0-155">A compensação é que esse design garante alta disponibilidade de todos os quatro componentes da plataforma do Azure quando essas três máquinas virtuais são atribuídas a um conjunto de disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="f59d0-155">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="f59d0-156">Os três servidores são configurados para todas as funções de rastreamento, administração, análise e processamento de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="f59d0-157">Escolha o modelo do Active Directory</span><span class="sxs-lookup"><span data-stu-id="f59d0-157">Choose the Active Directory model</span></span>

<span data-ttu-id="f59d0-158">Todas as soluções do SharePoint exigem o AD DS (serviços de domínio Active Directory) do Windows.</span><span class="sxs-lookup"><span data-stu-id="f59d0-158">All SharePoint solutions require Windows Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="f59d0-159">No momento, há duas opções para soluções do SharePoint no Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-159">At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="f59d0-160">Opção 1: domínio dedicado — você pode implantar um domínio dedicado e isolado no Azure para dar suporte a um farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f59d0-160">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm.</span></span> <span data-ttu-id="f59d0-161">Essa é uma boa opção para sites de Internet voltados para o público.</span><span class="sxs-lookup"><span data-stu-id="f59d0-161">This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="f59d0-162">Opção 2: estender o domínio local por meio de uma conexão VPN site a site.</span><span class="sxs-lookup"><span data-stu-id="f59d0-162">Option 2: Extend the on-premises domain through a site-to-site VPN connection.</span></span> <span data-ttu-id="f59d0-163">Quando você estende o domínio local por meio de uma conexão VPN site a site, os usuários acessam o farm do SharePoint como se estivessem hospedados no local.</span><span class="sxs-lookup"><span data-stu-id="f59d0-163">When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises.</span></span> <span data-ttu-id="f59d0-164">Você pode aproveitar as implementações existentes do Active Directory e do DNS.</span><span class="sxs-lookup"><span data-stu-id="f59d0-164">You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="f59d0-165">Design para gerenciamento de identidades, zonas e autenticação</span><span class="sxs-lookup"><span data-stu-id="f59d0-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="f59d0-166">Design para contas e autenticação</span><span class="sxs-lookup"><span data-stu-id="f59d0-166">Design for accounts and authentication</span></span>

<span data-ttu-id="f59d0-167">Determine como as contas serão gerenciadas e qual tipo de autenticação será usado.</span><span class="sxs-lookup"><span data-stu-id="f59d0-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="f59d0-168">Contas para desenvolvedores e autores de sites</span><span class="sxs-lookup"><span data-stu-id="f59d0-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="f59d0-169">Adicionar contas ao domínio no Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="f59d0-170">Use o AD FS (serviços de Federação do Active Directory) no local para federar as contas internas para o domínio no Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="f59d0-171">Se o design incluir uma conexão VPN site a site, use as contas internas.</span><span class="sxs-lookup"><span data-stu-id="f59d0-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="f59d0-172">Contas para clientes</span><span class="sxs-lookup"><span data-stu-id="f59d0-172">Accounts for customers</span></span>

- <span data-ttu-id="f59d0-173">Usar o Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f59d0-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="f59d0-174">Use um provedor baseado em SAML diferente.</span><span class="sxs-lookup"><span data-stu-id="f59d0-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="f59d0-175">Design para zonas</span><span class="sxs-lookup"><span data-stu-id="f59d0-175">Design for zones</span></span>

<span data-ttu-id="f59d0-176">No SharePoint 2013, o gerenciamento de identidades é acrescentado à configuração de zonas e autenticação.</span><span class="sxs-lookup"><span data-stu-id="f59d0-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="f59d0-177">Esse design oferece uma clara separação das contas de clientes de todas as outras contas.</span><span class="sxs-lookup"><span data-stu-id="f59d0-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="f59d0-178">Use este design se quiser que as contas de clientes sejam tratadas de uma mesma diferença das contas internas de autores e desenvolvedores de sites.</span><span class="sxs-lookup"><span data-stu-id="f59d0-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="f59d0-179">Usando esse design, você pode usar políticas de zona para limitar as ações do cliente em um aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="f59d0-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="f59d0-180">Esse design resulta em diferentes URLs para contas de cliente e contas internas.</span><span class="sxs-lookup"><span data-stu-id="f59d0-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="f59d0-181">Neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="f59d0-181">In this example:</span></span> 
  
- <span data-ttu-id="f59d0-182">Configure a zona padrão para contas internas.</span><span class="sxs-lookup"><span data-stu-id="f59d0-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="f59d0-183">Configure a zona de extranet para acesso autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="f59d0-183">Configure the extranet zone for customer authenticated access.</span></span> <span data-ttu-id="f59d0-184">Usar o Azure Active Directory (AD) para contas de clientes ou usar um provedor baseado em SAML diferente.</span><span class="sxs-lookup"><span data-stu-id="f59d0-184">Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="f59d0-185">Configure a zona da Internet para acesso anônimo.</span><span class="sxs-lookup"><span data-stu-id="f59d0-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="f59d0-186">Não use um design de duas zonas no qual todos os usuários autenticados estão configurados para usar a zona padrão.</span><span class="sxs-lookup"><span data-stu-id="f59d0-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="f59d0-187">O diagrama a seguir mostra um design de três zonas com separação das contas internas e do cliente.</span><span class="sxs-lookup"><span data-stu-id="f59d0-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="f59d0-188">Os visitantes e clientes acessam o locatário do Azure AD no farm do SharePoint 2013 por meio de aplicativos Web em uma de duas zonas.</span><span class="sxs-lookup"><span data-stu-id="f59d0-188">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones.</span></span> <span data-ttu-id="f59d0-189">As duas zonas incluem:</span><span class="sxs-lookup"><span data-stu-id="f59d0-189">The two zones include:</span></span> 
  
- <span data-ttu-id="f59d0-190">Zona: Internet para usuários anônimos</span><span class="sxs-lookup"><span data-stu-id="f59d0-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="f59d0-191">Zona: Extranet para usuários autenticados</span><span class="sxs-lookup"><span data-stu-id="f59d0-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="f59d0-192">Os usuários com contas internas acessam o locatário do Azure Active Directory do AD DS e do AD FS no ambiente local por meio do túnel VPN para o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f59d0-192">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD.</span></span> <span data-ttu-id="f59d0-193">A zona padrão fornece autenticação do Windows (NTLM).</span><span class="sxs-lookup"><span data-stu-id="f59d0-193">The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="f59d0-194">Design para se conectar ao Azure AD</span><span class="sxs-lookup"><span data-stu-id="f59d0-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="f59d0-195">O Azure AD fornece recursos de gerenciamento de identidades e controle de acesso para serviços em nuvem.</span><span class="sxs-lookup"><span data-stu-id="f59d0-195">Azure AD provides identity management and access control capabilities for cloud services.</span></span> <span data-ttu-id="f59d0-196">Os recursos incluem um repositório baseado em nuvem para dados de diretório e um conjunto principal de serviços de identidade, incluindo processos de logon do usuário, serviços de autenticação e AD FS.</span><span class="sxs-lookup"><span data-stu-id="f59d0-196">Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS.</span></span> <span data-ttu-id="f59d0-197">Os serviços de identidade que estão incluídos no Azure AD se integram facilmente às implantações do AD DS local e dão suporte completo a provedores de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="f59d0-197">The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="f59d0-198">O diagrama de acompanhamento mostra o cenário a seguir:</span><span class="sxs-lookup"><span data-stu-id="f59d0-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="f59d0-199">Ao integrar o SharePoint 2013 com o Azure Active Directory, um serviço de controle de acesso (ACS) do Azure serve a duas finalidades:</span><span class="sxs-lookup"><span data-stu-id="f59d0-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="f59d0-200">O Azure AD usa SAML 2,0 e o SharePoint só funciona com o SAML 1,1.</span><span class="sxs-lookup"><span data-stu-id="f59d0-200">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1.</span></span> <span data-ttu-id="f59d0-201">O ACS compreende os formatos e serve como intermediário para transformar os formatos de token entre o SharePoint e o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f59d0-201">ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="f59d0-202">O ACS substitui a necessidade do serviço de token de segurança do provedor de identidade (IP-STS) para este cenário SAML.</span><span class="sxs-lookup"><span data-stu-id="f59d0-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="f59d0-203">Para obter mais informações, consulte Configurar o Azure AD com o SharePoint 2013 na biblioteca do TechNet.</span><span class="sxs-lookup"><span data-stu-id="f59d0-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="f59d0-204">Criar sites e URLs para publicação entre sites</span><span class="sxs-lookup"><span data-stu-id="f59d0-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="f59d0-205">Um design de aplicativo da Web é recomendado para cenários de publicação.</span><span class="sxs-lookup"><span data-stu-id="f59d0-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="f59d0-206">Os sites de criação e publicação estão no mesmo aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="f59d0-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="f59d0-207">A publicação entre sites é usada para publicar ativos.</span><span class="sxs-lookup"><span data-stu-id="f59d0-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="f59d0-208">Use conjuntos de sites baseados em caminho e nomeados por host.</span><span class="sxs-lookup"><span data-stu-id="f59d0-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="f59d0-209">Um conjunto de sites raiz é um requisito.</span><span class="sxs-lookup"><span data-stu-id="f59d0-209">A root site collection is a requirement.</span></span> <span data-ttu-id="f59d0-210">Crie este site como um site baseado em caminho.</span><span class="sxs-lookup"><span data-stu-id="f59d0-210">Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="f59d0-211">Crie todos os outros conjuntos de sites como conjuntos de sites nomeados por host.</span><span class="sxs-lookup"><span data-stu-id="f59d0-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="f59d0-212">URLs de aplicativo Web e site raiz</span><span class="sxs-lookup"><span data-stu-id="f59d0-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="f59d0-213">Use um nome interno para a URL do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="f59d0-213">Use an internal name for the web application URL.</span></span> <span data-ttu-id="f59d0-214">O SharePoint usa o nome da máquina local como o nome padrão, a menos que um nome diferente seja especificado.</span><span class="sxs-lookup"><span data-stu-id="f59d0-214">SharePoint uses the local machine name as the default name unless a different name is specified.</span></span> <span data-ttu-id="f59d0-215">Você pode usar um nome de domínio reservado para o ambiente de rede interna.</span><span class="sxs-lookup"><span data-stu-id="f59d0-215">You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="f59d0-216">O SharePoint atribui um número de porta não padrão quando o aplicativo Web é criado.</span><span class="sxs-lookup"><span data-stu-id="f59d0-216">SharePoint assigns a nonstandard port number when the web application is created.</span></span> <span data-ttu-id="f59d0-217">Use este número de porta em vez da porta 80 ou a porta 443.</span><span class="sxs-lookup"><span data-stu-id="f59d0-217">Use this port number instead of port 80 or port 443.</span></span> <span data-ttu-id="f59d0-218">Ou use um número de porta diferente, mas não padrão.</span><span class="sxs-lookup"><span data-stu-id="f59d0-218">Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="f59d0-219">Use o mesmo nome e número de porta para o conjunto de sites raiz, que é um conjunto de sites baseado em caminho.</span><span class="sxs-lookup"><span data-stu-id="f59d0-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="f59d0-220">O diagrama a seguir mostra os serviços do pool de aplicativos, como a pesquisa interagindo com conjuntos de sites usando aplicativos da Web.</span><span class="sxs-lookup"><span data-stu-id="f59d0-220">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications.</span></span> <span data-ttu-id="f59d0-221">Os conjuntos de sites mostrados incluem:</span><span class="sxs-lookup"><span data-stu-id="f59d0-221">The site collections shown include:</span></span> 
  
- <span data-ttu-id="f59d0-222">Conjunto de sites baseado em caminho localizado http://internal:8000 em (site raiz).</span><span class="sxs-lookup"><span data-stu-id="f59d0-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="f59d0-223">Rastreamento: conjuntos de sites nomeados por host, localizados em um https://authoring.contoso.com:8000endereço como.</span><span class="sxs-lookup"><span data-stu-id="f59d0-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="f59d0-224">Consultas: 2 conjuntos de sites nomeados por host diferentes localizados em endereços como:</span><span class="sxs-lookup"><span data-stu-id="f59d0-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - http://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="f59d0-225">Projetar o ambiente do Azure</span><span class="sxs-lookup"><span data-stu-id="f59d0-225">Design the Azure environment</span></span>

<span data-ttu-id="f59d0-226">Este exemplo de arquitetura inclui os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="f59d0-226">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="f59d0-227">Uma conexão VPN de site a site é opcional e estende o ambiente do Windows AD DS e DNS local para a rede virtual no Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-227">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="f59d0-228">Opcionalmente, use um domínio dedicado no Azure para dar suporte ao farm do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f59d0-228">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="f59d0-229">Os servidores são divididos nos serviços de nuvem do Azure com base na função.</span><span class="sxs-lookup"><span data-stu-id="f59d0-229">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="f59d0-230">Os conjuntos de disponibilidade garantem alta disponibilidade de funções de servidor configuradas de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="f59d0-230">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="f59d0-231">Para obter mais informações, consulte o seguinte artigo no TechNet: arquiteturas do Azure para soluções do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f59d0-231">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="f59d0-232">O diagrama a seguir mostra um exemplo de um ambiente local conectado a uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="f59d0-232">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="f59d0-233">Incluído no ambiente local, que é um elemento opcional do ambiente do Azure, os seguintes componentes são:</span><span class="sxs-lookup"><span data-stu-id="f59d0-233">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="f59d0-234">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="f59d0-234">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="f59d0-235">AD DS</span><span class="sxs-lookup"><span data-stu-id="f59d0-235">AD DS</span></span> 
    
- <span data-ttu-id="f59d0-236">Um gateway VPN do Windows Server e do AD DS para a sub-rede do gateway VPN ativa</span><span class="sxs-lookup"><span data-stu-id="f59d0-236">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="f59d0-237">O ambiente de rede virtual do Azure inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="f59d0-237">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="f59d0-238">A sub-rede ativa do gateway VPN (sobrepondo ao ambiente local, se aplicável)</span><span class="sxs-lookup"><span data-stu-id="f59d0-238">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="f59d0-239">Serviço de nuvem que inclui o AD DS e o conjunto de disponibilidade de DNS (dois servidores)</span><span class="sxs-lookup"><span data-stu-id="f59d0-239">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="f59d0-240">Serviço de nuvem que inclui o conjunto de disponibilidade do servidor front-end (três servidores do SharePoint) e o conjunto de disponibilidade do servidor de aplicativos (três servidores do SharePoint)</span><span class="sxs-lookup"><span data-stu-id="f59d0-240">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="f59d0-241">Serviço de nuvem que contém dois conjuntos de disponibilidade de banco de dados</span><span class="sxs-lookup"><span data-stu-id="f59d0-241">Cloud service that contains two database availability sets</span></span> 
    

