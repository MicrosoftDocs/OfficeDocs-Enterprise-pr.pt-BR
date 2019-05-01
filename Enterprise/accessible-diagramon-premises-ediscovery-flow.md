---
title: Diagrama de fluxo de descoberta eletrônica no local acessível
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: Este artigo é uma versão de texto acessível do diagrama chamado fluxo de descoberta eletrônica local.
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487692"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="27db4-103">Diagrama de fluxo de descoberta eletrônica no local acessível</span><span class="sxs-lookup"><span data-stu-id="27db4-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="27db4-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado fluxo de descoberta eletrônica local.</span><span class="sxs-lookup"><span data-stu-id="27db4-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="27db4-105">Este cartaz fornece detalhes sobre a arquitetura e o fluxo de dados nos produtos de servidor.</span><span class="sxs-lookup"><span data-stu-id="27db4-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="27db4-106">Entre o SharePoint, o Exchange, o Lync e os compartilhamentos de arquivos</span><span class="sxs-lookup"><span data-stu-id="27db4-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="27db4-107">O diagrama mostra um usuário enviando uma consulta que acessa dois farms de servidores, um farm de aplicativos corporativos do SharePoint 2013 e um farm de serviços do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="27db4-107">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="27db4-108">O farm de serviços do SharePoint 2013 se comunica com um farm de conteúdo do SharePoint 2013, o Exchange Server 2013 (que se comunica com o Lync 2013) e comPartilhamentos de arquivos do Windows.</span><span class="sxs-lookup"><span data-stu-id="27db4-108">The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="27db4-109">A lista de fluxo de descoberta eletrônica descreve o fluxo de dados e a ordem em que as ações de consulta do eDisovery ocorrem entre o SharePoint, o Exchange, o Lync e os compartilhamentos de arquivos.</span><span class="sxs-lookup"><span data-stu-id="27db4-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="27db4-110">A lista de fluxo de descoberta eletrônica é descrita em detalhes primeiro, seguida de uma descrição detalhada dos recursos descritos no diagrama.</span><span class="sxs-lookup"><span data-stu-id="27db4-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="27db4-111">Lista de fluxo de descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="27db4-111">eDiscovery Flow List</span></span>

<span data-ttu-id="27db4-112">Os números de cada uma das etapas descritas nesta lista pertencem a uma etapa representada no diagrama.</span><span class="sxs-lookup"><span data-stu-id="27db4-112">The numbers for each of the steps described in this list pertain to a step depicted in the diagram.</span></span> <span data-ttu-id="27db4-113">O diagrama é descrito em detalhes mais adiante neste documento.</span><span class="sxs-lookup"><span data-stu-id="27db4-113">The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="27db4-114">as ocorrências de descoberta eletrônica são criadas, gerenciadas e usadas no centro de descoberta eletrônica (EDC).</span><span class="sxs-lookup"><span data-stu-id="27db4-114">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC).</span></span> <span data-ttu-id="27db4-115">O EDC é um conjunto de sites do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="27db4-115">The EDC is a SharePoint 2013 site collection.</span></span> <span data-ttu-id="27db4-116">É aí que os casos são definidos, as fontes a serem controladas são identificadas, as consultas são emitidas, os resultados da consulta são revisados e os bloqueios no conteúdo são colocados ou removidos.</span><span class="sxs-lookup"><span data-stu-id="27db4-116">This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="27db4-117">A consulta ou ação de descoberta eletrônica, como colocar um bloqueio, ReleaseHold ou GetStatus, é retransmitida do EDC para o proxy do aplicativo de serviço de pesquisa (SSA) no farm de aplicativos corporativos.</span><span class="sxs-lookup"><span data-stu-id="27db4-117">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm.</span></span> <span data-ttu-id="27db4-118">O proxy SSA transmite o tráfego para o SSA no farm de aplicativos de serviços.</span><span class="sxs-lookup"><span data-stu-id="27db4-118">The SSA proxy then relays the traffic to the SSA in the Services App Farm.</span></span> <span data-ttu-id="27db4-119">Neste exemplo, a solicitação é colocar qualquer coisa no farm de conteúdo do SharePoint com "CONTOSO" no nome do arquivo em espera.</span><span class="sxs-lookup"><span data-stu-id="27db4-119">In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="27db4-120">Se a solicitação for consultar uma ocorrência, o SSA consulta o índice de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="27db4-120">If the request is to query a case, the SSA consults the search index.</span></span> <span data-ttu-id="27db4-121">Em seguida, o conjunto de resultados da consulta de descoberta eletrônica retorna ao usuário por meio do EDC.</span><span class="sxs-lookup"><span data-stu-id="27db4-121">Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="27db4-122">Se a solicitação for uma ação, como colocar uma isEnção ou ReleaseHold, essa ação será gravada no Actions_Table no banco de dados administrativo do SSA.</span><span class="sxs-lookup"><span data-stu-id="27db4-122">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database.</span></span> <span data-ttu-id="27db4-123">Neste exemplo, uma solicitação de bloqueio para qualquer coisa no farm de conteúdo do SharePoint com "CONTOSO" é gravada no Actions_Table.</span><span class="sxs-lookup"><span data-stu-id="27db4-123">In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="27db4-124">Em intervalos regulares, o trabalho de timer de bloqueio in-loco de descoberta eletrônica do farm de conteúdo é ativado e gera uma solicitação para ações pendentes e envia atualizações de status por meio do proxy SSA para o SSA.</span><span class="sxs-lookup"><span data-stu-id="27db4-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="27db4-125">A consulta de ações pendentes é retransmitida para o SSA central, que consulta o Action_Table para qualquer ação pendente para o farm de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="27db4-125">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm.</span></span> <span data-ttu-id="27db4-126">O trabalho de timer de bloqueio in-loco do farm de conteúdo também envia atualizações de status para objetos e ações recebidas, que são gravadas no Actiontable.</span><span class="sxs-lookup"><span data-stu-id="27db4-126">The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="27db4-127">A solicitação de retenção para qualquer conteúdo com "CONTOSO" no nome no farm de conteúdo do SharePoint 2013 é enviada pelo adaptador SSA para o trabalho de timer de bloqueio in-loco de descoberta eletrônica no farm de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="27db4-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="27db4-128">O trabalho de timer de bloqueio in-loco de descoberta eletrônica coloca o "site CONTOSO" e o "conteúdo CONTOSO" em espera.</span><span class="sxs-lookup"><span data-stu-id="27db4-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="27db4-129">O trabalho de timer de bloqueio in-loco de descoberta eletrônica é executado periodicamente no farm de aplicativos corporativos para verificar o status das ações de descoberta e para atualizar o status.</span><span class="sxs-lookup"><span data-stu-id="27db4-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="27db4-130">A consulta de status é retransmitida por meio do proxy SSA do farm de aplicativos empresariais para o adaptador SSA do farm de serviços do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="27db4-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="27db4-131">O SSA recupera o status da tabela Actions e o retorna para o trabalho de timer no farm de aplicativos corporativos, que envia as atualizações de status para o EDC.</span><span class="sxs-lookup"><span data-stu-id="27db4-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="27db4-132">Quando o usuário de descoberta eletrônica está pesquisando (ou executando uma ação) para fontes do Exchange, como uma caixa de correio ou conteúdo arquivado do Lync, o SSA central usa o proxy dos serviços Web do Exchange (EWS) para consultar os serviços Web do Exchange.</span><span class="sxs-lookup"><span data-stu-id="27db4-132">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services.</span></span> <span data-ttu-id="27db4-133">O Exchange tem sua própria infraestrutura de pesquisa e descoberta eletrônica e gerencia todas as chamadas de descoberta eletrônica internamente.</span><span class="sxs-lookup"><span data-stu-id="27db4-133">Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="27db4-134">Os serviços Web do Exchange respondem a SSA com resultados de pesquisa de descoberta eletrônica ou uma resposta a uma solicitação de status de um bloqueio baseado em consulta, que, por sua vez, é retransmitido para o EDC.</span><span class="sxs-lookup"><span data-stu-id="27db4-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="27db4-135">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="27db4-135">Prerequisites</span></span>

- <span data-ttu-id="27db4-136">A pesquisa do SharePoint Enterprise deve ser configurada, os rastreamentos de pesquisa em fontes de conteúdo (compartilhamentos de arquivos do SharePoint e do Windows) estão ocorrendo com êxito, e todas as fontes de conteúdo estão no índice.</span><span class="sxs-lookup"><span data-stu-id="27db4-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="27db4-137">A confiança de servidor para servidor e a autenticação devem ser configuradas entre o farm do SharePoint Services e o Exchange e também entre o Exchange e o Lync.</span><span class="sxs-lookup"><span data-stu-id="27db4-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="27db4-138">Descrição dos componentes no diagrama</span><span class="sxs-lookup"><span data-stu-id="27db4-138">Description of components in the diagram</span></span>

<span data-ttu-id="27db4-139">O diagrama mostra um usuário que envia uma consulta, que acessa dois farms de servidores, um farm de aplicativos corporativos do SharePoint 2013 e um farm de serviços do SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="27db4-139">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="27db4-140">O farm do SharePoint Services é interfaces com um farm de conteúdo do SharePoint 2013, o Exchange Server 2013 (que interface com o Lync 2013) e comPartilhamentos de arquivos do Windows.</span><span class="sxs-lookup"><span data-stu-id="27db4-140">The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="27db4-141">Farm de aplicativos Enterprise do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="27db4-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="27db4-142">O farm de aplicativos Enterprise do SharePoint 2013 contém os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="27db4-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="27db4-143">EDC</span><span class="sxs-lookup"><span data-stu-id="27db4-143">EDC</span></span>
    
- <span data-ttu-id="27db4-144">Proxy SSA</span><span class="sxs-lookup"><span data-stu-id="27db4-144">SSA proxy</span></span> 
    
- <span data-ttu-id="27db4-145">Trabalho de timer</span><span class="sxs-lookup"><span data-stu-id="27db4-145">Timer job</span></span> 
    
<span data-ttu-id="27db4-146">Uma consulta ou ação enviada pelo usuário é enviada para o EDC no farm de aplicativos corporativos.</span><span class="sxs-lookup"><span data-stu-id="27db4-146">A query or action sent by the user is sent to the EDC in the Enterprise App Farm.</span></span> <span data-ttu-id="27db4-147">Ocorrem as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="27db4-147">The following actions occur:</span></span> 
  
- <span data-ttu-id="27db4-148">A consulta ou a ação vai para o proxy SSA.</span><span class="sxs-lookup"><span data-stu-id="27db4-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="27db4-149">O proxy SSA envia uma consulta de status ou resposta para o trabalho de timer no farm de aplicativos corporativos e também envia uma consulta de status ou resposta para o serviço SSA no farm do SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="27db4-149">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm.</span></span> <span data-ttu-id="27db4-150">As ações que fazem isso são descritas na seção sobre o farm de serviços do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="27db4-150">The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="27db4-151">Quando recebe uma resposta, o trabalho de timer envia a resposta para o proxy SSA e para o EDC.</span><span class="sxs-lookup"><span data-stu-id="27db4-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="27db4-152">Qualquer resultado da consulta ou ação é enviado para o usuário do EDC.</span><span class="sxs-lookup"><span data-stu-id="27db4-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="27db4-153">Farm de serviços do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="27db4-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="27db4-154">O farm de serviços do SharePoint 2013 contém os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="27db4-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="27db4-155">Serviço SSA</span><span class="sxs-lookup"><span data-stu-id="27db4-155">SSA Service</span></span> 
    
- <span data-ttu-id="27db4-156">Banco de dados de índice de pesquisa</span><span class="sxs-lookup"><span data-stu-id="27db4-156">Search index database</span></span> 
    
- <span data-ttu-id="27db4-157">Banco de dados SSA admin_db.</span><span class="sxs-lookup"><span data-stu-id="27db4-157">SSA admin_db database.</span></span> <span data-ttu-id="27db4-158">A tabela Actions neste banco de dados contém: reter liberação GetStatus</span><span class="sxs-lookup"><span data-stu-id="27db4-158">The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="27db4-159">Proxy do EWS</span><span class="sxs-lookup"><span data-stu-id="27db4-159">EWS proxy</span></span> 
    
<span data-ttu-id="27db4-160">Quando o proxy SSA no farm de aplicativos corporativos do SharePoint envia uma consulta de status para o SSA no farm do SharePoint Services, ocorrem as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="27db4-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="27db4-161">Se a solicitação for uma consulta, o SSA consulta o índice de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="27db4-161">If the request is a query, the SSA consults the search index.</span></span> <span data-ttu-id="27db4-162">A resposta de descoberta é retornada para o SSA e, em seguida, para o usuário por meio do EDC.</span><span class="sxs-lookup"><span data-stu-id="27db4-162">The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="27db4-163">Se a solicitação for uma ação de gravação, o serviço SSA enviará a ação Write para o adaptador SSA admin_db.</span><span class="sxs-lookup"><span data-stu-id="27db4-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="27db4-164">Uma solicitação de resultados de rastreamento e resposta é enviada do adaptador SSA para o farm de conteúdo do SharePoint 2013 e uma resposta é retornada ao SSA.</span><span class="sxs-lookup"><span data-stu-id="27db4-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="27db4-165">Uma solicitação de resultados de rastreamento e resposta é enviada do adaptador SSA para os comPartilhamentos de arquivos do Windows, e uma resposta é retornada ao SSA.</span><span class="sxs-lookup"><span data-stu-id="27db4-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="27db4-166">Uma consulta de ações pendentes, respostas ou atualizações de status é enviada do SSA para o proxy SSA no farm de conteúdo do SharePoint e uma resposta é retornada ao SSA.</span><span class="sxs-lookup"><span data-stu-id="27db4-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="27db4-167">Uma solicitação de ação/status do Exchange é enviada do adaptador SSA para o proxy EWS, que envia uma solicitação de ação/status de consulta do Exchange para o serviço Web do Exchange no servidor Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="27db4-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="27db4-168">Uma consulta/resposta de status é enviada do SSA para o adaptador SSA admin_db e é retornada ao SSA.</span><span class="sxs-lookup"><span data-stu-id="27db4-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="27db4-169">Uma consulta/resposta de ação pendente é enviada do SSA para o adaptador SSA admin_db e é retornada ao SSA.</span><span class="sxs-lookup"><span data-stu-id="27db4-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="27db4-170">Farm de conteúdo do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="27db4-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="27db4-171">O farm de conteúdo do SharePoint 2013 contém os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="27db4-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="27db4-172">Proxy SSA</span><span class="sxs-lookup"><span data-stu-id="27db4-172">SSA proxy</span></span> 
    
- <span data-ttu-id="27db4-173">Trabalho de timer</span><span class="sxs-lookup"><span data-stu-id="27db4-173">Timer job</span></span> 
    
- <span data-ttu-id="27db4-174">Site Contoso do SharePoint</span><span class="sxs-lookup"><span data-stu-id="27db4-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="27db4-175">Conteúdo do SharePoint da contoso</span><span class="sxs-lookup"><span data-stu-id="27db4-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="27db4-176">Quando o SSA no farm de serviços do SharePoint envia uma consulta de status para o proxy SSA no farm de conteúdo do SharePoint, ocorrem as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="27db4-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="27db4-177">O proxy SSA no farm de conteúdo do SharePoint envia uma consulta para a resposta de ações/status pendentes para o trabalho de timer.</span><span class="sxs-lookup"><span data-stu-id="27db4-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="27db4-178">O trabalho de timer envia uma solicitação para o site do SharePoint da Contoso, que revisa o conteúdo do SharePoint da contoso.</span><span class="sxs-lookup"><span data-stu-id="27db4-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="27db4-179">A resposta para a consulta de ações/status pendentes é enviada do trabalho de timer para o proxy SSA no farm de conteúdo do SharePoint e, em seguida, é enviada para o serviço SSA no farm do SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="27db4-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="27db4-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="27db4-180">Exchange 2013</span></span>

<span data-ttu-id="27db4-181">O componente de servidor do Exchange 2013 contém o serviço Web do Exchange e oferece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="27db4-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="27db4-182">A confiança de servidor para servidor/OAuth é tratada entre o farm de conteúdo do SharePoint 2013 e o Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="27db4-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="27db4-183">A confiança de servidor para servidor/OAuth é tratada entre o Exchange 2013 e o Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="27db4-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="27db4-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="27db4-184">Lync 2013</span></span>

<span data-ttu-id="27db4-185">O componente do Lync 2013 arquiva o conteúdo do Lync no Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="27db4-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="27db4-186">ComPartilhamentos de arquivos do Windows</span><span class="sxs-lookup"><span data-stu-id="27db4-186">Windows File Shares</span></span>

<span data-ttu-id="27db4-187">O componente de comPartilhamentos de arquivos do Windows fornece resultados de rastreamento para o SSA no farm do SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="27db4-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="27db4-188">Legenda</span><span class="sxs-lookup"><span data-stu-id="27db4-188">Legend</span></span>

<span data-ttu-id="27db4-189">A legenda deste diagrama mostra graficamente os diferentes tipos de tráfego descritos entre os componentes em diferentes linhas coloridas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="27db4-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="27db4-190">Linha azul claro: consulta/ação-dados de consulta de descoberta eletrônica ou ação</span><span class="sxs-lookup"><span data-stu-id="27db4-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="27db4-191">Linha laranja: resposta eDisovery-dados de resposta da consulta de descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="27db4-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="27db4-192">Linha verde: status de consulta/resposta-status de descoberta eletrônica/dados de resposta</span><span class="sxs-lookup"><span data-stu-id="27db4-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="27db4-193">Linha roxa: solicitação de status/ação do Exchange-solicitação de descoberta eletrônica para o tráfego de ação do Exchange.</span><span class="sxs-lookup"><span data-stu-id="27db4-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="27db4-194">Linha vermelha: resposta de dados/status do Exchange-resposta de status ou consulta de descoberta eletrônica do Exchange.</span><span class="sxs-lookup"><span data-stu-id="27db4-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="27db4-195">Linha preta pontilhada: confiança de servidor para servidor/OAuth</span><span class="sxs-lookup"><span data-stu-id="27db4-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="27db4-196">Linha preta sólida: rastreamento/resultados</span><span class="sxs-lookup"><span data-stu-id="27db4-196">Solid black line: Crawl/results</span></span> 
    

