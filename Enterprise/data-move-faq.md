---
title: Perguntas frequentes gerais sobre migração de dados
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 9/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Aqui estão as respostas para perguntas gerais sobre como mover dados principais para um novo geo de datacenter.
ms.openlocfilehash: 40f83ee94aaa7c919f08d91d888ff131da02df67
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539304"
---
# <a name="data-move-general-faq"></a>Perguntas frequentes gerais sobre migração de dados

Aqui estão as respostas para perguntas gerais sobre como mover dados principais para um novo geo de datacenter.
  
 **P. como Certifique-se de que meus dados de cliente serão seguro durante a movimentação e o que eu não terão o tempo de inatividade?**
  
Movimentações de dados r. são uma operação de serviço back-end com um impacto mínimo para os usuários finais. Recursos que podem ser afetados estão listados na [durante e após sua movimentação de dados](during-and-after-your-data-move.md). Podemos aderir ao [Microsoft Online Services nível contrato serviço (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) para disponibilidade, portanto, não há nada que os clientes precisam para preparar ou monitorar durante a movimentação. 
  
Todos os serviços do Office 365 executar as mesmas versões em datacenters, portanto, você pode ter certeza de funcionalidade consistente. O serviço é totalmente suportado ao longo do processo.
  
 **P. qual é o impacto de ter diferentes serviços localizados em geos diferentes?**
  
R. para alguns clientes existentes e clientes no meio do processo de movimentação, alguns dos serviços do Office 365 podem estar localizado em geos diferentes. Nossos serviços execute independentemente uns dos outros e há nenhum impacto de usuário, se este for o caso.
  
 **P. serão novos clientes do Office 365 automaticamente provisionados no novo geos datacenter?**
  
R. Sim. Depois que um novo geo de datacenter estiver disponível, o novo Office 365 para clientes corporativos que selecionar um país elegível para a nova geo como seu país durante a inscrição terão seus dados principais hospedados no novo geo datacenter.
  
 **P. onde estão meus dados está localizado?**
  
Publicamos o local do datacenter geos, data centers e localização dos dados de cliente em que [mapeia datacenter interativo do Office 365 ](https://o365datacentermap.azurewebsites.net). A partir de 1 de agosto, você poderá verificar o local dos dados em repouso por meio da seção de dados local em seu perfil de organização no Centro de administração do Office 365 do cliente.
  
 **P. os clientes existentes do Office 365 serão movidos para o novo geos datacenter?**
  
Os clientes A. elegíveis Office 365 podem solicitar que seus dados principais movidos para o novo geos. Os clientes precisarão enviar uma solicitação antes do prazo para seu geo para participar. 
  
 **P. quais clientes estão qualificados para solicitar uma movimentação?**
  
Clientes comerciais A. existente Office 365, que selecionou um país elegível para a nova geo datacenter poderá solicitar uma movimentação. 
  
 **P. quando eu poderão solicitar uma movimentação?**
  
R. o período de solicitação será anunciado na página [como solicitar sua movimentação de dados](request-your-data-move.md) . 
  
 **P. como pode solicitar a serem movidos?**
  
R. os clientes qualificados serão exibida uma página no seu [Portal de administração do Office 365](https://portal.office.com/). Consulte [como solicitar sua movimentação de dados](request-your-data-move.md) para obter instruções sobre como solicitar uma movimentação. 
  
 **P. posso alterar meu seleção após a solicitação de movimento?**
  
R. It não é possível para que possamos removê-lo do processo após enviar a solicitação.
  
 **P. o que acontece se eu não solicitam um movimento antes do prazo?**
  
R. estamos não consegue aceitar solicitações a serem movidos depois do prazo em cada geo.
  
 **P. o que ocorre se eu quiser mover meus dados para obter o melhor desempenho de rede?**
  
Não é uma garantia para melhorar o desempenho de rede sendo perto de um datacenter do Office 365. Há muitos fatores e componentes que afetam o desempenho da rede entre o usuário final e o serviço do Office 365. Para obter mais informações sobre este e ajuste de desempenho, consulte [planejamento de rede e ajuste de desempenho para o Office 365](network-planning-and-performance.md).
  
 **Todos os serviços p. mover seus dados no mesmo dia?**
  
R. os serviços não mova seus dados ao mesmo tempo. Cada serviço serão transferidos de forma independente e provavelmente moverá seus dados em momentos diferentes.
  
 **P. eu devo escolher quando eu quero meus dados a serem movidos?**
  
R. clientes não serão possível selecionar uma data específica, não é possível atrasar a sua migração e nós não é possível compartilhar uma data específica ou intervalo de tempo para as movimentações.
  
 **P. você pode compartilhar quando meus dados serão ser movidos?**
  
Movimentações de dados r. são uma operação de back-end com um impacto mínimo para os usuários finais. A complexidade, precisão e escala em que precisamos realizar movimentações de dados dentro de um ambiente automatizado e operado globalmente nos proíbem de compartilhamento quando uma movimentação de dados é esperada para ser concluída para seu locatário ou qualquer outro locatário único. Os clientes receberão uma confirmação no Centro de mensagens por serviço participante, de quando sua movimentação de dados foi concluída. 
  
 **P. o que acontece se os usuários acessarem serviços enquanto está sendo movidos os dados?**
  
R. consulte [durante e após sua movimentação de dados](during-and-after-your-data-move.md) para uma lista completa dos recursos que podem ser limitados durante as partes da movimentação de dados para cada serviço. 
  
 **P. como saber se que a movimentação está concluída?**
  
R. Assista Centro de mensagem do Office 365 confirmação de que a movimentação de dados de cada serviço foi concluída. Quando os dados de cada serviço são movidos, publicaremos um aviso de conclusão portanto você obterá três avisos de conclusão: um para o Exchange Online, SharePoint Online e Skype para negócios Online.
  
Se você vir quaisquer problemas após a movimentação, contate o [Suporte do Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) para obter assistência. 
  
 **P. quais dados para o Office 365 são armazenados no novo geos datacenter?**
  
R. se provisiona um cliente seu locatário em um do novo geos datacenter, o Microsoft armazena os seguintes dados do cliente em repouso dentro do geo:
  
- Conteúdo de caixa de correio Exchange Online (corpo do email, entradas de calendário e o conteúdo de anexos de email)
    
- O conteúdo do site do SharePoint Online e os arquivos armazenados dentro desse site, incluindo o conteúdo do Project Online e acesso Online.
    
Além disso, esses dados não são replicados fora o geo.
  
 **P. eu sou um cliente do Office 365 em um do novo geos datacenter, mas quando eu inscreveu, posso selecionado um país diferente. Como pode posso ser movido para a nova geo datacenter?**
  
R. Infelizmente, não é possível alterar o país associado ao seu locatário. Em vez disso, você precisa criar um novo inquilino do Office 365 com uma nova assinatura e mova manualmente seus usuários e dados para o novo inquilino.
  
 **P. haverá quaisquer alterações na minha conta?**
  
R. na maioria dos casos, não há nenhuma alteração que os clientes no verão na sua declaração de faturamento.
  
A Microsoft irá cobra todos os clientes australiano do Office 365 quantidade adicional igual ao GST australiano para serviços do Office 365 e emitirá faturas de imposto. Essa alteração ocorrerá porque GST australiano é pago sobre tributável fornecimento de bens e serviços fornecidos e oferecidas em Austrália.
  
 **P. o que acontece se estamos estão em processo de migração de dados de email para o Office 365 durante a movimentação do Exchange Online?**
  
R. Se as migrações de email estão em andamento, qualquer caixas de correio individuais que atualmente estão sendo migradas serão canceladas enquanto a movimentação de locatário finaliza e migração as caixas de correio será reiniciado automaticamente depois que o locatário estiver em centros de dados de destino.
  
 **P. após os dados são movidos sem o geo datacenter anterior, é ele removido dos data centers?**
  
R. Sim, os dados antigos serão removidos após um período de tempo.
  
 **P. posso testar alguns usuários?**
  
R. quando seu locatário do Office 365 é movido para um novo geo de datacenter, todos os usuários são movidos ao mesmo tempo. Você pode criar um locatário separado de avaliação para testar a conectividade, mas o locatário avaliação não pode ser combinado de forma alguma com seu locatário existente.
  
 **P. como eu notificado sobre a movimentação e por quem em minha empresa será notificado?**
  
R. usaremos o Centro de mensagem do Office 365, que é visível para qualquer pessoa com qualquer permissões de administrador no Office 365.
  
 **P. eu não desejo esperar a Microsoft mover os meus dados. É possível apenas criar um novo inquilino e mover irei?**
  
R. Sim, no entanto, o processo não será tão uniforme como se fosse do Microsoft executar a movimentação de dados.
  
Se você criar um novo inquilino depois que o novo geo datacenter estiver disponível, o novo inquilino será hospedado em geo o novo. Este novo inquilino é completamente separado de seu locatário anterior e você seria responsável por movendo o conteúdo do site, todas as caixas de correio do usuário, nomes de domínio e quaisquer outros dados. Observe que você não pode mover o nome do locatário de um locatário para outro. Recomendamos que você aguarde o programa de movimentação fornecido pela Microsoft como vai cuidar de mover todas as configurações, dados e assinaturas para seus usuários.
  
 **P. eu não estiver pronta para ser movida, pode devo escolher uma data de movimentação específico?**
  
R. It não é possível alterar quando os dados de cliente do cada serviço serão movidos. Movimentações de dados são uma operação de back-end com um impacto mínimo para os usuários finais.
  
 **P. meus dados do cliente já foi movidos para um novo geo de datacenter. Posso me mover novamente?**
  
R. Isso não é possível. Os clientes que tiverem sido movidos para o novo data centers de geo não podem ser movidos novamente. Como um cliente na qualquer geo, fica a mesma qualidade de serviço, desempenho e controles de segurança como fez anteriormente.
  
 **Os novo geos datacenter p. usar as mesmas versões dos serviços do Office 365 como o geos datacenter atual?**
  
R. Sim.
  
 **Inquilinos do p. será o Office 365 hospedados em datacenters a nova estará disponível para usuários externos do país?**
  
R. Sim. A Microsoft mantém uma rede global grande com conexões de Internet públicas nos locais mais de 50, 23 países em todo o mundo com contratos de correspondência com mais de 1.500 da Internet (provedores). Os usuários poderão acessar os datacenters onde quer que estejam na Internet.
  

