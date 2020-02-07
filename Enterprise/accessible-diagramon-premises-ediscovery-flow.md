---
title: Diagrama de fluxo de descoberta eletrônica no local acessível
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
f1.keywords:
- NOCSH
description: Este artigo é uma versão de texto acessível do diagrama chamado fluxo de descoberta eletrônica local.
ms.openlocfilehash: ec9ecf7d3663503f2da412364d919a6c70032e23
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843852"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Diagrama de fluxo de descoberta eletrônica no local acessível

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado fluxo de descoberta eletrônica local.
  
Este cartaz fornece detalhes sobre a arquitetura e o fluxo de dados nos produtos de servidor. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>Entre o SharePoint, o Exchange, o Lync e os compartilhamentos de arquivos

O diagrama mostra um usuário enviando uma consulta que acessa dois farms de servidores, um farm de aplicativos corporativos do SharePoint 2013 e um farm de serviços do SharePoint 2013. O farm de serviços do SharePoint 2013 se comunica com um farm de conteúdo do SharePoint 2013, o Exchange Server 2013 (que se comunica com o Lync 2013) e compartilhamentos de arquivos do Windows. 
  
A lista de fluxo de descoberta eletrônica descreve o fluxo de dados e a ordem em que as ações de consulta do eDisovery ocorrem entre o SharePoint, o Exchange, o Lync e os compartilhamentos de arquivos. 
  
A lista de fluxo de descoberta eletrônica é descrita em detalhes primeiro, seguida de uma descrição detalhada dos recursos descritos no diagrama. 
  
### <a name="ediscovery-flow-list"></a>Lista de fluxo de descoberta eletrônica

Os números de cada uma das etapas descritas nesta lista pertencem a uma etapa representada no diagrama. O diagrama é descrito em detalhes mais adiante neste documento. 
  
1. as ocorrências de descoberta eletrônica são criadas, gerenciadas e usadas no centro de descoberta eletrônica (EDC). O EDC é um conjunto de sites do SharePoint 2013. É aí que os casos são definidos, as fontes a serem controladas são identificadas, as consultas são emitidas, os resultados da consulta são revisados e os bloqueios no conteúdo são colocados ou removidos. 
    
2. A consulta ou ação de descoberta eletrônica, como colocar um bloqueio, ReleaseHold ou GetStatus, é retransmitida do EDC para o proxy do aplicativo de serviço de pesquisa (SSA) no farm de aplicativos corporativos. O proxy SSA transmite o tráfego para o SSA no farm de aplicativos de serviços. Neste exemplo, a solicitação é colocar qualquer coisa no farm de conteúdo do SharePoint com "CONTOSO" no nome do arquivo em espera. 
    
3. Se a solicitação for consultar uma ocorrência, o SSA consulta o índice de pesquisa. Em seguida, o conjunto de resultados da consulta de descoberta eletrônica retorna ao usuário por meio do EDC. 
    
4. Se a solicitação for uma ação, como colocar uma isenção ou ReleaseHold, essa ação será gravada no Actions_Table no banco de dados administrativo do SSA. Neste exemplo, uma solicitação de bloqueio para qualquer coisa no farm de conteúdo do SharePoint com "CONTOSO" é gravada no Actions_Table. 
    
5. Em intervalos regulares, o trabalho de timer de bloqueio in-loco de descoberta eletrônica do farm de conteúdo é ativado e gera uma solicitação para ações pendentes e envia atualizações de status por meio do proxy SSA para o SSA. 
    
6. A consulta de ações pendentes é retransmitida para o SSA central, que consulta o Action_Table para qualquer ação pendente para o farm de conteúdo. O trabalho de timer de bloqueio in-loco do farm de conteúdo também envia atualizações de status para objetos e ações recebidas, que são gravadas no Actiontable. 
    
7. A solicitação de retenção para qualquer conteúdo com "CONTOSO" no nome no farm de conteúdo do SharePoint 2013 é enviada pelo adaptador SSA para o trabalho de timer de bloqueio in-loco de descoberta eletrônica no farm de conteúdo. 
    
8. O trabalho de timer de bloqueio in-loco de descoberta eletrônica coloca o "site CONTOSO" e o "conteúdo CONTOSO" em espera. 
    
9. O trabalho de timer de bloqueio in-loco de descoberta eletrônica é executado periodicamente no farm de aplicativos corporativos para verificar o status das ações de descoberta e para atualizar o status. 
    
10. A consulta de status é retransmitida por meio do proxy SSA do farm de aplicativos empresariais para o adaptador SSA do farm de serviços do SharePoint. 
    
11. O SSA recupera o status da tabela Actions e o retorna para o trabalho de timer no farm de aplicativos corporativos, que envia as atualizações de status para o EDC. 
    
12. Quando o usuário de descoberta eletrônica está pesquisando (ou executando uma ação) para fontes do Exchange, como uma caixa de correio ou conteúdo arquivado do Lync, o SSA central usa o proxy dos serviços Web do Exchange (EWS) para consultar os serviços Web do Exchange. O Exchange tem sua própria infraestrutura de pesquisa e descoberta eletrônica e gerencia todas as chamadas de descoberta eletrônica internamente. 
    
13. Os serviços Web do Exchange respondem a SSA com resultados de pesquisa de descoberta eletrônica ou uma resposta a uma solicitação de status de um bloqueio baseado em consulta, que, por sua vez, é retransmitido para o EDC. 
    
#### <a name="prerequisites"></a>Pré-requisitos

- A pesquisa do SharePoint Enterprise deve ser configurada, os rastreamentos de pesquisa em fontes de conteúdo (compartilhamentos de arquivos do SharePoint e do Windows) estão ocorrendo com êxito, e todas as fontes de conteúdo estão no índice. 
    
- A confiança de servidor para servidor e a autenticação devem ser configuradas entre o farm do SharePoint Services e o Exchange e também entre o Exchange e o Lync. 
    
### <a name="description-of-components-in-the-diagram"></a>Descrição dos componentes no diagrama

O diagrama mostra um usuário que envia uma consulta, que acessa dois farms de servidores, um farm de aplicativos corporativos do SharePoint 2013 e um farm de serviços do SharePoint 2013. O farm do SharePoint Services é interfaces com um farm de conteúdo do SharePoint 2013, o Exchange Server 2013 (que interface com o Lync 2013) e compartilhamentos de arquivos do Windows. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>Farm de aplicativos Enterprise do SharePoint 2013

O farm de aplicativos Enterprise do SharePoint 2013 contém os seguintes componentes: 
  
- EDC
    
- Proxy SSA 
    
- Trabalho de timer 
    
Uma consulta ou ação enviada pelo usuário é enviada para o EDC no farm de aplicativos corporativos. Ocorrem as seguintes ações: 
  
- A consulta ou a ação vai para o proxy SSA. 
    
- O proxy SSA envia uma consulta de status ou resposta para o trabalho de timer no farm de aplicativos corporativos e também envia uma consulta de status ou resposta para o serviço SSA no farm do SharePoint Services. As ações que fazem isso são descritas na seção sobre o farm de serviços do SharePoint. 
    
- Quando recebe uma resposta, o trabalho de timer envia a resposta para o proxy SSA e para o EDC. 
    
- Qualquer resultado da consulta ou ação é enviado para o usuário do EDC. 
    
#### <a name="sharepoint-2013-services-farm"></a>Farm de serviços do SharePoint 2013

O farm de serviços do SharePoint 2013 contém os seguintes componentes: 
  
- Serviço SSA 
    
- Banco de dados de índice de pesquisa 
    
- SSA admin_db banco de dados. A tabela Actions neste banco de dados contém: reter liberação GetStatus 
    
- Proxy do EWS 
    
Quando o proxy SSA no farm de aplicativos corporativos do SharePoint envia uma consulta de status para o SSA no farm do SharePoint Services, ocorrem as seguintes ações: 
  
- Se a solicitação for uma consulta, o SSA consulta o índice de pesquisa. A resposta de descoberta é retornada para o SSA e, em seguida, para o usuário por meio do EDC. 
    
- Se a solicitação for uma ação de gravação, o serviço SSA enviará a ação Write para o admin_db SSA. 
    
- Uma solicitação de resultados de rastreamento e resposta é enviada do adaptador SSA para o farm de conteúdo do SharePoint 2013 e uma resposta é retornada ao SSA. 
    
- Uma solicitação de resultados de rastreamento e resposta é enviada do adaptador SSA para os compartilhamentos de arquivos do Windows, e uma resposta é retornada ao SSA. 
    
- Uma consulta de ações pendentes, respostas ou atualizações de status é enviada do SSA para o proxy SSA no farm de conteúdo do SharePoint e uma resposta é retornada ao SSA. 
    
- Uma solicitação de ação/status do Exchange é enviada do adaptador SSA para o proxy EWS, que envia uma solicitação de ação/status de consulta do Exchange para o serviço Web do Exchange no servidor Exchange 2013. 
    
- Uma consulta/resposta de status é enviada do SSA para o SSA admin_db e é retornada ao SSA. 
    
- Uma ação/resposta pendente é enviada do SSA para o adaptador SSA admin_db e é retornada ao SSA. 
    
#### <a name="sharepoint-2013-content-farm"></a>Farm de conteúdo do SharePoint 2013

O farm de conteúdo do SharePoint 2013 contém os seguintes componentes: 
  
- Proxy SSA 
    
- Trabalho de timer 
    
- Site Contoso do SharePoint 
    
- Conteúdo do SharePoint da contoso 
    
Quando o SSA no farm de serviços do SharePoint envia uma consulta de status para o proxy SSA no farm de conteúdo do SharePoint, ocorrem as seguintes ações: 
  
- O proxy SSA no farm de conteúdo do SharePoint envia uma consulta para a resposta de ações/status pendentes para o trabalho de timer. 
    
- O trabalho de timer envia uma solicitação para o site do SharePoint da Contoso, que revisa o conteúdo do SharePoint da contoso. 
    
- A resposta para a consulta de ações/status pendentes é enviada do trabalho de timer para o proxy SSA no farm de conteúdo do SharePoint e, em seguida, é enviada para o serviço SSA no farm do SharePoint Services 
    
#### <a name="exchange-2013"></a>Exchange 2013

O componente de servidor do Exchange 2013 contém o serviço Web do Exchange e oferece o seguinte: 
  
- A confiança de servidor para servidor/OAuth é tratada entre o farm de conteúdo do SharePoint 2013 e o Exchange 2013. 
    
- A confiança de servidor para servidor/OAuth é tratada entre o Exchange 2013 e o Lync 2013. 
    
#### <a name="lync-2013"></a>Lync 2013

O componente do Lync 2013 arquiva o conteúdo do Lync no Exchange 2013. 
  
#### <a name="windows-file-shares"></a>Compartilhamentos de arquivos do Windows

O componente de compartilhamentos de arquivos do Windows fornece resultados de rastreamento para o SSA no farm do SharePoint Services. 
  
### <a name="legend"></a>Legenda

A legenda deste diagrama mostra graficamente os diferentes tipos de tráfego descritos entre os componentes em diferentes linhas coloridas da seguinte maneira: 
  
- Linha azul claro: consulta/ação-dados de consulta de descoberta eletrônica ou ação 
    
- Linha laranja: resposta eDisovery-dados de resposta da consulta de descoberta eletrônica 
    
- Linha verde: status de consulta/resposta-status de descoberta eletrônica/dados de resposta 
    
- Linha roxa: solicitação de status/ação do Exchange-solicitação de descoberta eletrônica para o tráfego de ação do Exchange. 
    
- Linha vermelha: resposta de dados/status do Exchange-resposta de status ou consulta de descoberta eletrônica do Exchange. 
    
- Linha preta pontilhada: confiança de servidor para servidor/OAuth 
    
- Linha preta sólida: rastreamento/resultados 
    

