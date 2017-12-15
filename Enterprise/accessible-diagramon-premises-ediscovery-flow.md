---
title: "Diagrama acessível - eDiscovery local fluxo"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "Este artigo é uma versão de texto acessível do diagrama denominado eDiscovery local fluxo."
ms.openlocfilehash: de94fc2af94df47a83f4a7847a84cd18131f637e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="4a2d5-103">Diagrama acessível - eDiscovery local fluxo</span><span class="sxs-lookup"><span data-stu-id="4a2d5-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="4a2d5-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama denominado eDiscovery local fluxo.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="4a2d5-105">Este cartaz fornece detalhes sobre a arquitetura e o fluxo de dados entre produtos de servidor.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="4a2d5-106">Entre o SharePoint, Exchange, Lync e compartilhamentos de arquivos</span><span class="sxs-lookup"><span data-stu-id="4a2d5-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="4a2d5-p101">O diagrama mostra um usuário que enviar uma consulta que acessa os dois farms de servidores, um Farm do SharePoint 2013 Enterprise App e um Farm de serviços do SharePoint 2013. O Farm de serviços do SharePoint 2013 se comunica com um Farm de conteúdo do SharePoint 2013, Exchange Server 2013 (que se comunica com o Lync 2013) e compartilhamentos de arquivos do Windows.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="4a2d5-109">A lista de fluxo de eDiscovery descreve o fluxo de dados e a ordem na qual eDisovery ações de consulta ocorrerem entre o SharePoint, Exchange, Lync em compartilhamentos de arquivos.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="4a2d5-110">A lista de fluxo de descoberta eletrônica é descrita em detalhes primeiro, seguido por uma descrição detalhada dos recursos descritos no diagrama.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="4a2d5-111">Lista de fluxo de descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="4a2d5-111">eDiscovery Flow List</span></span>

<span data-ttu-id="4a2d5-p102">Os números de cada uma das etapas descritas nesta lista pertencem a uma etapa ilustrada no diagrama. O diagrama é descrito em detalhes posteriormente neste documento.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="4a2d5-p103">casos de eDiscovery são criados, gerenciados e usados na Central de descoberta eletrônica (EDC). EDC é um conjunto de sites do SharePoint 2013. Isso é onde casos são definidos, fontes a serem rastreados são identificados, consultas são emitidas, resultados de consulta sejam revisados e isenções no conteúdo forem colocadas ou removidas.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="4a2d5-p104">A consulta de descoberta eletrônica ou a ação, por exemplo, colocar um bloqueio, ReleaseHold ou GetStatus, é retransmitida do EDC para o proxy de aplicativo de serviço de pesquisa (SSA) no Farm do aplicativo empresarial. Em seguida, o proxy de SSA retransmite o tráfego para o SSA do farm do aplicativo de serviços. Neste exemplo, a solicitação é colocar nada no Farm de conteúdo do SharePoint com "CONTOSO" no nome do arquivo em espera.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="4a2d5-p105">Se a solicitação é consultar um caso, o SSA a consulta o índice de pesquisa. Em seguida, o conjunto de resultados de consulta de descoberta eletrônica retorna para o usuário por meio de EDC.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="4a2d5-p106">Se a solicitação for uma ação, como colocar uma espera ou ReleaseHold, essa ação é gravada o Actions_Table no banco de dados SSA administrativas. Neste exemplo, uma solicitação de espera para qualquer coisa no Farm de conteúdo do SharePoint com "CONTOSO" é gravada o Actions_Table.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="4a2d5-124">Em intervalos regulares o Farm de conteúdo descoberta eletrônica in-loco espera o trabalho de timer ser acordado e gera uma solicitação por ações pendentes e envia as atualizações de status por meio do proxy do SSA para o SSA.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="4a2d5-p107">A consulta para ações pendentes é retransmitida para o SSA central, que consulta o Action_Table para pendentes ações para o Farm de conteúdo. O trabalho de timer de bloqueio in-loco do Farm de conteúdo também envia atualizações de status para objetos e ações recebeu, que são gravadas a ActionsTable.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="4a2d5-127">A solicitação de espera para qualquer conteúdo com "CONTOSO" no nome de usuário no Farm de conteúdo do SharePoint 2013 é enviada pelo SSA para o trabalho de timer de bloqueio in-loco de descoberta eletrônica no Farm de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="4a2d5-128">A descoberta eletrônica in-loco espera timer casas trabalho o "Site CONTOSO" e "Content da CONTOSO" em espera.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="4a2d5-129">O trabalho de timer de bloqueio in-loco de descoberta eletrônica periodicamente é executado no Farm do aplicativo empresarial para verificar o status das ações de descoberta e atualizar o status.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="4a2d5-130">A consulta de status é retransmitida por meio do proxy do SSA de Farm de aplicativo empresarial para o SSA de Farm do SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="4a2d5-131">O SSA recupera o status da tabela de ações e retorna para o trabalho de timer do farm de aplicativo empresarial, que envia as atualizações de status para EDC.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="4a2d5-p108">Quando o usuário de descoberta eletrônica é pesquisando (ou executando uma ação) para fontes do Exchange, como uma caixa de correio ou o conteúdo arquivado do Lync, o SSA central usa o proxy de serviços Web do Exchange (EWS) à consulta serviços Web do Exchange. Exchange tem sua própria infra-estrutura de pesquisa e descoberta eletrônica e gerencia todas as chamadas de eDiscovery internamente.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="4a2d5-134">Serviços Web do Exchange responde a SSA com resultados de pesquisa de descoberta eletrônica ou uma resposta a uma solicitação de status de uma isenção baseado em consulta, que, por sua vez, obtém retransmitida para EDC.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="4a2d5-135">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4a2d5-135">Prerequisites</span></span>

- <span data-ttu-id="4a2d5-136">Pesquisa corporativa do SharePoint deve ser configurada, rastreamentos de pesquisa em fontes de conteúdo (compartilhamentos de arquivos do SharePoint e do Windows) estão ocorrendo com êxito, e todas as fontes de conteúdo estão no índice.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="4a2d5-137">Autenticação e a relação de confiança de servidor-para-servidor devem ser configurados entre o Farm do SharePoint Services e o Exchange e também entre Exchange e Lync.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="4a2d5-138">Descrição dos componentes do diagrama</span><span class="sxs-lookup"><span data-stu-id="4a2d5-138">Description of components in the diagram</span></span>

<span data-ttu-id="4a2d5-p109">O diagrama mostra um usuário que enviar uma consulta, que acessa os dois farms de servidores, um Farm do SharePoint 2013 Enterprise App e um Farm de serviços do SharePoint 2013. Interfaces de Farm de serviços do SharePoint com um Farm de conteúdo do SharePoint 2013, Exchange Server 2013 (que interfaces com o Lync 2013) e compartilhamentos de arquivos do Windows.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="4a2d5-141">Farm de aplicativo empresarial do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="4a2d5-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="4a2d5-142">O Farm do SharePoint 2013 Enterprise App contém os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="4a2d5-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="4a2d5-143">EDC</span><span class="sxs-lookup"><span data-stu-id="4a2d5-143">EDC</span></span>
    
- <span data-ttu-id="4a2d5-144">Proxy SSA</span><span class="sxs-lookup"><span data-stu-id="4a2d5-144">SSA proxy</span></span> 
    
- <span data-ttu-id="4a2d5-145">Trabalho de timer</span><span class="sxs-lookup"><span data-stu-id="4a2d5-145">Timer job</span></span> 
    
<span data-ttu-id="4a2d5-p110">Uma consulta ou ação enviadas pelo usuário é enviada ao EDC do farm de aplicativo empresarial. Ocorrem as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="4a2d5-148">A consulta ou ação vai para o proxy do SSA.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="4a2d5-p111">O proxy do SSA envia uma consulta de status ou a resposta para o trabalho de Timer do farm de aplicativo empresarial, e ele também envia uma consulta de status ou a resposta ao serviço SSA no Farm de serviços do SharePoint. As ações que resultam de isso são descritas na seção sobre o Farm do SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="4a2d5-151">Quando ela recebe uma resposta, o trabalho de Timer envia a resposta para o proxy do SSA e EDC.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="4a2d5-152">Retorno de algum resultado da consulta ou ação é enviados para o usuário do EDC.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="4a2d5-153">Farm de serviços do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="4a2d5-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="4a2d5-154">O Farm de serviços do SharePoint 2013 contém os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="4a2d5-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="4a2d5-155">Serviço de SSA</span><span class="sxs-lookup"><span data-stu-id="4a2d5-155">SSA Service</span></span> 
    
- <span data-ttu-id="4a2d5-156">Banco de dados de índice de pesquisa</span><span class="sxs-lookup"><span data-stu-id="4a2d5-156">Search index database</span></span> 
    
- <span data-ttu-id="4a2d5-p112">Banco de dados de admin_db SSA. A tabela de ações neste banco de dados contém: mantenha GetStatus de espera de lançamento</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="4a2d5-159">Proxy EWS</span><span class="sxs-lookup"><span data-stu-id="4a2d5-159">EWS proxy</span></span> 
    
<span data-ttu-id="4a2d5-160">Quando o proxy do SSA no Farm de aplicativo empresarial do SharePoint envia uma consulta de status para o SSA no Farm de serviços do SharePoint, ocorrem as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="4a2d5-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="4a2d5-p113">Se a solicitação é uma consulta, o SSA a consulta o índice de pesquisa. A resposta de descoberta é retornada para o SSA e depois para o usuário por EDC.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="4a2d5-163">Se a solicitação é uma ação de gravação, o serviço SSA envia a ação de gravação para o admin_db SSA.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="4a2d5-164">Um rastreamento e respondendo resultados solicitação é enviada do SSA ao Farm de conteúdo do SharePoint 2013 e uma resposta é retornada para o SSA.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="4a2d5-165">Um rastreamento e respondendo resultados solicitação é enviada do SSA para os compartilhamentos de arquivos do Windows e uma resposta é retornada para o SSA.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="4a2d5-166">Uma consulta para as ações, respostas ou atualizações de status pendentes é enviada do SSA ao proxy SSA no Farm de conteúdo do SharePoint, e uma resposta é retornada para o SSA.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="4a2d5-167">Uma solicitação de status da ação/Exchange é enviada do SSA para o proxy do EWS, que envia uma solicitação de ação/status de consulta do Exchange para o serviço Web do Exchange no servidor Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="4a2d5-168">Uma resposta da consulta status é enviada do SSA para admin_db o SSA e é retornada para o SSA.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="4a2d5-169">Uma resposta da consulta ação pendente é enviada do SSA para admin_db o SSA e é retornada para o SSA.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="4a2d5-170">Farm de conteúdo do SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="4a2d5-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="4a2d5-171">O Farm de conteúdo do SharePoint 2013 contém os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="4a2d5-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="4a2d5-172">Proxy SSA</span><span class="sxs-lookup"><span data-stu-id="4a2d5-172">SSA proxy</span></span> 
    
- <span data-ttu-id="4a2d5-173">Trabalho de timer</span><span class="sxs-lookup"><span data-stu-id="4a2d5-173">Timer job</span></span> 
    
- <span data-ttu-id="4a2d5-174">Site do SharePoint da Contoso</span><span class="sxs-lookup"><span data-stu-id="4a2d5-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="4a2d5-175">Conteúdo do SharePoint da Contoso</span><span class="sxs-lookup"><span data-stu-id="4a2d5-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="4a2d5-176">Quando o SSA no Farm de serviços do SharePoint envia uma consulta de status ao Proxy SSA no Farm de conteúdo do SharePoint, ocorrem as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="4a2d5-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="4a2d5-177">O proxy do SSA no Farm de conteúdo do SharePoint envia uma consulta pendentes resposta ações/status do trabalho de Timer.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="4a2d5-178">O trabalho de Timer envia uma solicitação para o site do SharePoint de Contoso, que analisa o conteúdo do SharePoint da Contoso.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="4a2d5-179">A resposta à consulta ações/status pendente é enviada do trabalho de Timer para o proxy do SSA no Farm de conteúdo do SharePoint e, em seguida, ele é enviado ao serviço SSA no Farm de serviços do SharePoint</span><span class="sxs-lookup"><span data-stu-id="4a2d5-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="4a2d5-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="4a2d5-180">Exchange 2013</span></span>

<span data-ttu-id="4a2d5-181">O componente de servidor do Exchange 2013 contém o serviço Web do Exchange e oferece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="4a2d5-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="4a2d5-182">Relação de confiança de servidor-para-servidor/OAuth é manipulada entre o Farm de conteúdo do SharePoint 2013 e Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="4a2d5-183">Relação de confiança de servidor-para-servidor/OAuth é manipulada entre o Exchange 2013 e Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="4a2d5-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="4a2d5-184">Lync 2013</span></span>

<span data-ttu-id="4a2d5-185">O componente do Lync 2013 arquiva conteúdo do Lync no Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="4a2d5-186">Compartilhamentos de arquivos do Windows</span><span class="sxs-lookup"><span data-stu-id="4a2d5-186">Windows File Shares</span></span>

<span data-ttu-id="4a2d5-187">O componente de compartilhamentos de arquivos do Windows fornece resultados de rastreamento para o SSA no Farm de serviços do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="4a2d5-188">Legenda</span><span class="sxs-lookup"><span data-stu-id="4a2d5-188">Legend</span></span>

<span data-ttu-id="4a2d5-189">A legenda este diagrama mostra graficamente os diferentes tipos de tráfego citados entre os componentes nas linhas coloridos diferentes da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4a2d5-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="4a2d5-190">Claro de linha azul: consulta/ação - dados de consulta ou ação de descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="4a2d5-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="4a2d5-191">Linha laranja: eDisovery resposta - dados de resposta da consulta de descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="4a2d5-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="4a2d5-192">Verde linha: Status consulta/resposta - dados de consulta/resposta do status de descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="4a2d5-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="4a2d5-193">Roxo linha: solicitação de ação/status do Exchange - solicitação de descoberta eletrônica de status da ação para o tráfego do Exchange.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="4a2d5-194">Linha vermelha: Exchange resposta/status de dados - resposta de status ou de consulta de descoberta eletrônica do Exchange.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="4a2d5-195">Pontilhado linha preta: relação de confiança de servidor-para-servidor/Oauth</span><span class="sxs-lookup"><span data-stu-id="4a2d5-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="4a2d5-196">Linha preta sólida: / resultados de rastreamento</span><span class="sxs-lookup"><span data-stu-id="4a2d5-196">Solid black line: Crawl/results</span></span> 
    

