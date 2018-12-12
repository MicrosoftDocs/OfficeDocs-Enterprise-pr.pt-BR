---
title: Diagrama acessível - eDiscovery local fluxo
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
description: Este artigo é uma versão de texto acessível do diagrama denominado eDiscovery local fluxo.
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17503054"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Diagrama acessível - eDiscovery local fluxo

**Resumo:** Este artigo é uma versão de texto acessível do diagrama denominado eDiscovery local fluxo.
  
Este cartaz fornece detalhes sobre a arquitetura e o fluxo de dados entre produtos de servidor. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>Entre o SharePoint, Exchange, Lync e compartilhamentos de arquivos

O diagrama mostra um usuário que enviar uma consulta que acessa os dois farms de servidores, um Farm do SharePoint 2013 Enterprise App e um Farm de serviços do SharePoint 2013. O Farm de serviços do SharePoint 2013 se comunica com um Farm de conteúdo do SharePoint 2013, Exchange Server 2013 (que se comunica com o Lync 2013) e compartilhamentos de arquivos do Windows. 
  
A lista de fluxo de eDiscovery descreve o fluxo de dados e a ordem na qual eDisovery ações de consulta ocorrerem entre o SharePoint, Exchange, Lync em compartilhamentos de arquivos. 
  
A lista de fluxo de descoberta eletrônica é descrita em detalhes primeiro, seguido por uma descrição detalhada dos recursos descritos no diagrama. 
  
### <a name="ediscovery-flow-list"></a>Lista de fluxo de descoberta eletrônica

Os números de cada uma das etapas descritas nesta lista pertencem a uma etapa ilustrada no diagrama. O diagrama é descrito em detalhes posteriormente neste documento. 
  
1. casos de eDiscovery são criados, gerenciados e usados na Central de descoberta eletrônica (EDC). EDC é um conjunto de sites do SharePoint 2013. Isso é onde casos são definidos, fontes a serem rastreados são identificados, consultas são emitidas, resultados de consulta sejam revisados e isenções no conteúdo forem colocadas ou removidas. 
    
2. A consulta de descoberta eletrônica ou a ação, por exemplo, colocar um bloqueio, ReleaseHold ou GetStatus, é retransmitida do EDC para o proxy de aplicativo de serviço de pesquisa (SSA) no Farm do aplicativo empresarial. Em seguida, o proxy de SSA retransmite o tráfego para o SSA do farm do aplicativo de serviços. Neste exemplo, a solicitação é colocar nada no Farm de conteúdo do SharePoint com "CONTOSO" no nome do arquivo em espera. 
    
3. Se a solicitação é consultar um caso, o SSA a consulta o índice de pesquisa. Em seguida, o conjunto de resultados de consulta de descoberta eletrônica retorna para o usuário por meio de EDC. 
    
4. Se a solicitação for uma ação, como colocar uma espera ou ReleaseHold, essa ação é gravada o Actions_Table no banco de dados SSA administrativas. Neste exemplo, uma solicitação de espera para qualquer coisa no Farm de conteúdo do SharePoint com "CONTOSO" é gravada o Actions_Table. 
    
5. Em intervalos regulares o Farm de conteúdo descoberta eletrônica in-loco espera o trabalho de timer ser acordado e gera uma solicitação por ações pendentes e envia as atualizações de status por meio do proxy do SSA para o SSA. 
    
6. A consulta para ações pendentes é retransmitida para o SSA central, que consulta o Action_Table para pendentes ações para o Farm de conteúdo. O trabalho de timer de bloqueio in-loco do Farm de conteúdo também envia atualizações de status para objetos e ações recebeu, que são gravadas a ActionsTable. 
    
7. A solicitação de espera para qualquer conteúdo com "CONTOSO" no nome de usuário no Farm de conteúdo do SharePoint 2013 é enviada pelo SSA para o trabalho de timer de bloqueio in-loco de descoberta eletrônica no Farm de conteúdo. 
    
8. A descoberta eletrônica in-loco espera timer casas trabalho o "Site CONTOSO" e "Content da CONTOSO" em espera. 
    
9. O trabalho de timer de bloqueio in-loco de descoberta eletrônica periodicamente é executado no Farm do aplicativo empresarial para verificar o status das ações de descoberta e atualizar o status. 
    
10. A consulta de status é retransmitida por meio do proxy do SSA de Farm de aplicativo empresarial para o SSA de Farm do SharePoint Services. 
    
11. O SSA recupera o status da tabela de ações e retorna para o trabalho de timer do farm de aplicativo empresarial, que envia as atualizações de status para EDC. 
    
12. Quando o usuário de descoberta eletrônica é pesquisando (ou executando uma ação) para fontes do Exchange, como uma caixa de correio ou o conteúdo arquivado do Lync, o SSA central usa o proxy de serviços Web do Exchange (EWS) à consulta serviços Web do Exchange. Exchange tem sua própria infra-estrutura de pesquisa e descoberta eletrônica e gerencia todas as chamadas de eDiscovery internamente. 
    
13. Serviços Web do Exchange responde a SSA com resultados de pesquisa de descoberta eletrônica ou uma resposta a uma solicitação de status de uma isenção baseado em consulta, que, por sua vez, obtém retransmitida para EDC. 
    
#### <a name="prerequisites"></a>Pré-requisitos

- Pesquisa corporativa do SharePoint deve ser configurada, rastreamentos de pesquisa em fontes de conteúdo (compartilhamentos de arquivos do SharePoint e do Windows) estão ocorrendo com êxito, e todas as fontes de conteúdo estão no índice. 
    
- Autenticação e a relação de confiança de servidor-para-servidor devem ser configurados entre o Farm do SharePoint Services e o Exchange e também entre Exchange e Lync. 
    
### <a name="description-of-components-in-the-diagram"></a>Descrição dos componentes do diagrama

O diagrama mostra um usuário que enviar uma consulta, que acessa os dois farms de servidores, um Farm do SharePoint 2013 Enterprise App e um Farm de serviços do SharePoint 2013. Interfaces de Farm de serviços do SharePoint com um Farm de conteúdo do SharePoint 2013, Exchange Server 2013 (que interfaces com o Lync 2013) e compartilhamentos de arquivos do Windows. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>Farm de aplicativo empresarial do SharePoint 2013

O Farm do SharePoint 2013 Enterprise App contém os seguintes componentes: 
  
- EDC
    
- Proxy SSA 
    
- Trabalho de timer 
    
Uma consulta ou ação enviadas pelo usuário é enviada ao EDC do farm de aplicativo empresarial. Ocorrem as seguintes ações: 
  
- A consulta ou ação vai para o proxy do SSA. 
    
- O proxy do SSA envia uma consulta de status ou a resposta para o trabalho de Timer do farm de aplicativo empresarial, e ele também envia uma consulta de status ou a resposta ao serviço SSA no Farm de serviços do SharePoint. As ações que resultam de isso são descritas na seção sobre o Farm do SharePoint Services. 
    
- Quando ela recebe uma resposta, o trabalho de Timer envia a resposta para o proxy do SSA e EDC. 
    
- Retorno de algum resultado da consulta ou ação é enviados para o usuário do EDC. 
    
#### <a name="sharepoint-2013-services-farm"></a>Farm de serviços do SharePoint 2013

O Farm de serviços do SharePoint 2013 contém os seguintes componentes: 
  
- Serviço de SSA 
    
- Banco de dados de índice de pesquisa 
    
- Banco de dados de admin_db SSA. A tabela de ações neste banco de dados contém: mantenha GetStatus de espera de lançamento 
    
- Proxy EWS 
    
Quando o proxy do SSA no Farm de aplicativo empresarial do SharePoint envia uma consulta de status para o SSA no Farm de serviços do SharePoint, ocorrem as seguintes ações: 
  
- Se a solicitação é uma consulta, o SSA a consulta o índice de pesquisa. A resposta de descoberta é retornada para o SSA e depois para o usuário por EDC. 
    
- Se a solicitação é uma ação de gravação, o serviço SSA envia a ação de gravação para o admin_db SSA. 
    
- Um rastreamento e respondendo resultados solicitação é enviada do SSA ao Farm de conteúdo do SharePoint 2013 e uma resposta é retornada para o SSA. 
    
- Um rastreamento e respondendo resultados solicitação é enviada do SSA para os compartilhamentos de arquivos do Windows e uma resposta é retornada para o SSA. 
    
- Uma consulta para as ações, respostas ou atualizações de status pendentes é enviada do SSA ao proxy SSA no Farm de conteúdo do SharePoint, e uma resposta é retornada para o SSA. 
    
- Uma solicitação de status da ação/Exchange é enviada do SSA para o proxy do EWS, que envia uma solicitação de ação/status de consulta do Exchange para o serviço Web do Exchange no servidor Exchange 2013. 
    
- Uma resposta da consulta status é enviada do SSA para admin_db o SSA e é retornada para o SSA. 
    
- Uma resposta da consulta ação pendente é enviada do SSA para admin_db o SSA e é retornada para o SSA. 
    
#### <a name="sharepoint-2013-content-farm"></a>Farm de conteúdo do SharePoint 2013

O Farm de conteúdo do SharePoint 2013 contém os seguintes componentes: 
  
- Proxy SSA 
    
- Trabalho de timer 
    
- Site do SharePoint da Contoso 
    
- Conteúdo do SharePoint da Contoso 
    
Quando o SSA no Farm de serviços do SharePoint envia uma consulta de status ao Proxy SSA no Farm de conteúdo do SharePoint, ocorrem as seguintes ações: 
  
- O proxy do SSA no Farm de conteúdo do SharePoint envia uma consulta pendentes resposta ações/status do trabalho de Timer. 
    
- O trabalho de Timer envia uma solicitação para o site do SharePoint de Contoso, que analisa o conteúdo do SharePoint da Contoso. 
    
- A resposta à consulta ações/status pendente é enviada do trabalho de Timer para o proxy do SSA no Farm de conteúdo do SharePoint e, em seguida, ele é enviado ao serviço SSA no Farm de serviços do SharePoint 
    
#### <a name="exchange-2013"></a>Exchange 2013

O componente de servidor do Exchange 2013 contém o serviço Web do Exchange e oferece os seguintes recursos: 
  
- Relação de confiança de servidor-para-servidor/OAuth é manipulada entre o Farm de conteúdo do SharePoint 2013 e Exchange 2013. 
    
- Relação de confiança de servidor-para-servidor/OAuth é manipulada entre o Exchange 2013 e Lync 2013. 
    
#### <a name="lync-2013"></a>Lync 2013

O componente do Lync 2013 arquiva conteúdo do Lync no Exchange 2013. 
  
#### <a name="windows-file-shares"></a>Compartilhamentos de arquivos do Windows

O componente de compartilhamentos de arquivos do Windows fornece resultados de rastreamento para o SSA no Farm de serviços do SharePoint. 
  
### <a name="legend"></a>Legenda

A legenda este diagrama mostra graficamente os diferentes tipos de tráfego citados entre os componentes nas linhas coloridos diferentes da seguinte maneira: 
  
- Claro de linha azul: consulta/ação - dados de consulta ou ação de descoberta eletrônica 
    
- Linha laranja: eDisovery resposta - dados de resposta da consulta de descoberta eletrônica 
    
- Verde linha: Status consulta/resposta - dados de consulta/resposta do status de descoberta eletrônica 
    
- Roxo linha: solicitação de ação/status do Exchange - solicitação de descoberta eletrônica de status da ação para o tráfego do Exchange. 
    
- Linha vermelha: Exchange resposta/status de dados - resposta de status ou de consulta de descoberta eletrônica do Exchange. 
    
- Pontilhado linha preta: relação de confiança de servidor-para-servidor/Oauth 
    
- Linha preta sólida: / resultados de rastreamento 
    

