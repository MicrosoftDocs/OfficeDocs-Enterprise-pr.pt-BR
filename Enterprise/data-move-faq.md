---
title: Perguntas frequentes gerais sobre migração de dados
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Aqui estão as respostas para perguntas gerais sobre como mover dados principais para um novo geo de datacenter.
ms.openlocfilehash: fe2399afa81a189416c41e3acba67e53eb99c674
ms.sourcegitcommit: 75ad9af1fa8adc73611fc6140546222b001861d5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "23839589"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="9822f-103">Perguntas frequentes gerais sobre migração de dados</span><span class="sxs-lookup"><span data-stu-id="9822f-103">Data move general FAQ</span></span>

<span data-ttu-id="9822f-104">Aqui estão as respostas para perguntas gerais sobre como mover dados principais para um novo geo de datacenter.</span><span class="sxs-lookup"><span data-stu-id="9822f-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
 <span data-ttu-id="9822f-105">**P. como Certifique-se de que meus dados de cliente serão seguro durante a movimentação e o que eu não terão o tempo de inatividade?**</span><span class="sxs-lookup"><span data-stu-id="9822f-105">**Q. How do you make sure my customer data is safe during the move and that I won't experience downtime?**</span></span>
  
<span data-ttu-id="9822f-p101">Movimentações de dados r. são uma operação de serviço back-end com um impacto mínimo para os usuários finais. Recursos que podem ser afetados estão listados na [durante e após sua movimentação de dados](during-and-after-your-data-move.md). Podemos aderir ao [Microsoft Online Services nível contrato serviço (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) para disponibilidade, portanto, não há nada que os clientes precisam para preparar ou monitorar durante a movimentação.</span><span class="sxs-lookup"><span data-stu-id="9822f-p101">A. Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md). We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="9822f-p102">Todos os serviços do Office 365 executar as mesmas versões em datacenters, portanto, você pode ter certeza de funcionalidade consistente. O serviço é totalmente suportado ao longo do processo.</span><span class="sxs-lookup"><span data-stu-id="9822f-p102">All Office 365 services run the same versions in the datacenters, so you can be assured of consistent functionality. Your service is fully supported throughout the process.</span></span>
  
 <span data-ttu-id="9822f-112">**P. qual é o impacto de ter diferentes serviços localizados em geos diferentes?**</span><span class="sxs-lookup"><span data-stu-id="9822f-112">**Q. What is the impact of having different services located in different geos?**</span></span>
  
<span data-ttu-id="9822f-p103">R. para alguns clientes existentes e clientes no meio do processo de movimentação, alguns dos serviços do Office 365 podem estar localizado em geos diferentes. Nossos serviços execute independentemente uns dos outros e há nenhum impacto de usuário, se este for o caso.</span><span class="sxs-lookup"><span data-stu-id="9822f-p103">A. For some existing customers and customers in the middle of the move process, some of the Office 365 services may be located in different geos. Our services run independently of each other and there is no user impact if this is the case.</span></span>
  
 <span data-ttu-id="9822f-116">**P. serão novos clientes do Office 365 automaticamente provisionados no novo geos datacenter?**</span><span class="sxs-lookup"><span data-stu-id="9822f-116">**Q. Will new Office 365 customers be automatically provisioned in the new datacenter geos?**</span></span>
  
<span data-ttu-id="9822f-p104">R. Sim. Depois que um novo geo de datacenter estiver disponível, o novo Office 365 para clientes corporativos que selecionar um país elegível para a nova geo como seu país durante a inscrição terão seus dados principais hospedados no novo geo datacenter.</span><span class="sxs-lookup"><span data-stu-id="9822f-p104">A. Yes. Once a new datacenter geo is available, new Office 365 for business customers who select a country eligible for the new geo as their country during sign-up will have their core data hosted in the new datacenter geo.</span></span>
  
 <span data-ttu-id="9822f-120">**P. onde estão meus dados está localizado?**</span><span class="sxs-lookup"><span data-stu-id="9822f-120">**Q. Where is my data is located?**</span></span>
  
<span data-ttu-id="9822f-p105">Publicamos o local do datacenter geos, data centers e localização dos dados de cliente em que [mapeia datacenter interativo do Office 365 ](https://o365datacentermap.azurewebsites.net). A partir de 1 de agosto, você poderá verificar o local dos dados em repouso por meio da seção de dados local em seu perfil de organização no Centro de administração do Office 365 do cliente.</span><span class="sxs-lookup"><span data-stu-id="9822f-p105">We publish the location of datacenter geos, datacenters, and location of customer data on the [ Office 365 interactive datacenter maps ](https://o365datacentermap.azurewebsites.net). As of August 1, you will be able to verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Office 365 Admin Center.</span></span>
  
 <span data-ttu-id="9822f-123">**P. os clientes existentes do Office 365 serão movidos para o novo geos datacenter?**</span><span class="sxs-lookup"><span data-stu-id="9822f-123">**Q. Will existing Office 365 customers be moved to the new datacenter geos?**</span></span>
  
<span data-ttu-id="9822f-p106">Os clientes A. elegíveis Office 365 podem solicitar que seus dados principais movidos para o novo geos. Os clientes precisarão enviar uma solicitação antes do prazo para seu geo para participar.</span><span class="sxs-lookup"><span data-stu-id="9822f-p106">A. Eligible Office 365 customers can request to have their core data moved to the new geos. Customers will need to submit a request before the deadline for their geo in order to participate.</span></span> 
  
 <span data-ttu-id="9822f-127">**P. quais clientes estão qualificados para solicitar uma movimentação?**</span><span class="sxs-lookup"><span data-stu-id="9822f-127">**Q. What customers are eligible to request a move?**</span></span>
  
<span data-ttu-id="9822f-p107">Clientes comerciais A. existente Office 365, que selecionou um país elegível para a nova geo datacenter poderá solicitar uma movimentação.</span><span class="sxs-lookup"><span data-stu-id="9822f-p107">A. Existing Office 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span> 
  
 <span data-ttu-id="9822f-130">**P. quando eu poderão solicitar uma movimentação?**</span><span class="sxs-lookup"><span data-stu-id="9822f-130">**Q. When will I be able to request a move?**</span></span>
  
<span data-ttu-id="9822f-p108">R. o período de solicitação será anunciado na página [como solicitar sua movimentação de dados](request-your-data-move.md) .</span><span class="sxs-lookup"><span data-stu-id="9822f-p108">A. The request period will be announced on the [How to request your data move](request-your-data-move.md) page.</span></span> 
  
 <span data-ttu-id="9822f-133">**P. como pode solicitar a serem movidos?**</span><span class="sxs-lookup"><span data-stu-id="9822f-133">**Q. How can I request to be moved?**</span></span>
  
<span data-ttu-id="9822f-p109">R. os clientes qualificados serão exibida uma página no seu [Portal de administração do Office 365](https://portal.office.com/). Consulte [como solicitar sua movimentação de dados](request-your-data-move.md) para obter instruções sobre como solicitar uma movimentação.</span><span class="sxs-lookup"><span data-stu-id="9822f-p109">A. Eligible customers will see a page in their [Office 365 Admin Portal](https://portal.office.com/). Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
 <span data-ttu-id="9822f-137">**P. posso alterar meu seleção após a solicitação de movimento?**</span><span class="sxs-lookup"><span data-stu-id="9822f-137">**Q. Can I change my selection after requesting a move?**</span></span>
  
<span data-ttu-id="9822f-p110">R. It não é possível para que possamos removê-lo do processo após enviar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="9822f-p110">A. It is not possible for us to remove you from the process after you submit your request.</span></span>
  
 <span data-ttu-id="9822f-140">**P. o que acontece se eu não solicitam um movimento antes do prazo?**</span><span class="sxs-lookup"><span data-stu-id="9822f-140">**Q. What happens if I do not request a move before the deadline?**</span></span>
  
<span data-ttu-id="9822f-p111">R. estamos não consegue aceitar solicitações a serem movidos depois do prazo em cada geo.</span><span class="sxs-lookup"><span data-stu-id="9822f-p111">A. We are unable to accept requests to be moved after the deadline in each geo.</span></span>
  
 <span data-ttu-id="9822f-143">**P. o que ocorre se eu quiser mover meus dados para obter o melhor desempenho de rede?**</span><span class="sxs-lookup"><span data-stu-id="9822f-143">**Q. What if I want to move my data in order to get better network performance?**</span></span>
  
<span data-ttu-id="9822f-p112">Não é uma garantia para melhorar o desempenho de rede sendo perto de um datacenter do Office 365. Há muitos fatores e componentes que afetam o desempenho da rede entre o usuário final e o serviço do Office 365. Para obter mais informações sobre este e ajuste de desempenho, consulte [planejamento de rede e ajuste de desempenho para o Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="9822f-p112">Being close to an Office 365 datacenter is not a guarantee for a better networking performance. There are many factors and components that impact the network performance between the end user and the Office 365 service. For more information about this and performance tuning see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>
  
 <span data-ttu-id="9822f-147">**Todos os serviços p. mover seus dados no mesmo dia?**</span><span class="sxs-lookup"><span data-stu-id="9822f-147">**Q. Do all the services move their data on the same day?**</span></span>
  
<span data-ttu-id="9822f-p113">R. os serviços não mova seus dados ao mesmo tempo. Cada serviço serão transferidos de forma independente e provavelmente moverá seus dados em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="9822f-p113">A. The services do not move their data at the same time. Each service will move independently and will likely move their data at different times.</span></span>
  
 <span data-ttu-id="9822f-151">**P. eu devo escolher quando eu quero meus dados a serem movidos?**</span><span class="sxs-lookup"><span data-stu-id="9822f-151">**Q. Can I choose when I want my data to be moved?**</span></span>
  
<span data-ttu-id="9822f-p114">R. clientes não serão possível selecionar uma data específica, não é possível atrasar a sua migração e nós não é possível compartilhar uma data específica ou intervalo de tempo para as movimentações.</span><span class="sxs-lookup"><span data-stu-id="9822f-p114">A. Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 <span data-ttu-id="9822f-154">**P. você pode compartilhar quando meus dados serão ser movidos?**</span><span class="sxs-lookup"><span data-stu-id="9822f-154">**Q. Can you share when my data will be be moved?**</span></span>
  
<span data-ttu-id="9822f-p115">Movimentações de dados r. são uma operação de back-end com um impacto mínimo para os usuários finais. A complexidade, precisão e escala em que precisamos realizar movimentações de dados dentro de um ambiente automatizado e operado globalmente nos proíbem de compartilhamento quando uma movimentação de dados é esperada para ser concluída para seu locatário ou qualquer outro locatário único. Os clientes receberão uma confirmação no Centro de mensagens por serviço participante, de quando sua movimentação de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="9822f-p115">A. Data moves are a back-end operation with minimal impact to end-users. The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 <span data-ttu-id="9822f-159">**P. o que acontece se os usuários acessarem serviços enquanto está sendo movidos os dados?**</span><span class="sxs-lookup"><span data-stu-id="9822f-159">**Q. What happens if users access services while the data is being moved?**</span></span>
  
<span data-ttu-id="9822f-p116">R. consulte [durante e após sua movimentação de dados](during-and-after-your-data-move.md) para uma lista completa dos recursos que podem ser limitados durante as partes da movimentação de dados para cada serviço.</span><span class="sxs-lookup"><span data-stu-id="9822f-p116">A. See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 <span data-ttu-id="9822f-162">**P. como saber se que a movimentação está concluída?**</span><span class="sxs-lookup"><span data-stu-id="9822f-162">**Q. How do I know the move is complete?**</span></span>
  
<span data-ttu-id="9822f-p117">R. Assista Centro de mensagem do Office 365 confirmação de que a movimentação de dados de cada serviço foi concluída. Quando os dados de cada serviço são movidos, publicaremos um aviso de conclusão portanto você obterá três avisos de conclusão: um para o Exchange Online, SharePoint Online e Skype para negócios Online.</span><span class="sxs-lookup"><span data-stu-id="9822f-p117">A. Watch the Office 365 message center for confirmation that the move of each service's data is complete. When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>
  
<span data-ttu-id="9822f-166">Se você vir quaisquer problemas após a movimentação, contate o [Suporte do Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) para obter assistência.</span><span class="sxs-lookup"><span data-stu-id="9822f-166">If you see any issues after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  
 <span data-ttu-id="9822f-167">**P. quais dados para o Office 365 são armazenados no novo geos datacenter?**</span><span class="sxs-lookup"><span data-stu-id="9822f-167">**Q. What data for Office 365 is stored in the new datacenter geos?**</span></span>
  
<span data-ttu-id="9822f-p118">R. se provisiona um cliente seu locatário em um do novo geos datacenter, o Microsoft armazena os seguintes dados do cliente em repouso dentro do geo:</span><span class="sxs-lookup"><span data-stu-id="9822f-p118">A. If a customer provisions its tenant in one of the new datacenter geos, Microsoft stores the following customer data at rest within the geo:</span></span>
  
- <span data-ttu-id="9822f-170">Conteúdo de caixa de correio Exchange Online (corpo do email, entradas de calendário e o conteúdo de anexos de email)</span><span class="sxs-lookup"><span data-stu-id="9822f-170">Exchange Online mailbox content (e-mail body, calendar entries, and the content of email attachments)</span></span>
    
- <span data-ttu-id="9822f-171">O conteúdo do site do SharePoint Online e os arquivos armazenados dentro desse site, incluindo o conteúdo do Project Online e acesso Online.</span><span class="sxs-lookup"><span data-stu-id="9822f-171">SharePoint Online site content and the files stored within that site, including Project Online and Access Online content.</span></span>
    
<span data-ttu-id="9822f-172">Além disso, esses dados não são replicados fora o geo.</span><span class="sxs-lookup"><span data-stu-id="9822f-172">In addition, this data is not replicated outside of the geo.</span></span>
  
 <span data-ttu-id="9822f-173">**P. eu sou um cliente do Office 365 em um do novo geos datacenter, mas quando eu inscreveu, posso selecionado um país diferente. Como pode posso ser movido para a nova geo datacenter?**</span><span class="sxs-lookup"><span data-stu-id="9822f-173">**Q. I am an Office 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country. How can I be moved to the new datacenter geo?**</span></span>
  
<span data-ttu-id="9822f-p119">R. Infelizmente, não é possível alterar o país associado ao seu locatário. Em vez disso, você precisa criar um novo inquilino do Office 365 com uma nova assinatura e mova manualmente seus usuários e dados para o novo inquilino.</span><span class="sxs-lookup"><span data-stu-id="9822f-p119">A. Unfortunately, it is not possible to change the country associated with your tenant. Instead, you need to create a new Office 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
 <span data-ttu-id="9822f-177">**P. haverá quaisquer alterações na minha conta?**</span><span class="sxs-lookup"><span data-stu-id="9822f-177">**Q. Will there be any changes on my bill?**</span></span>
  
<span data-ttu-id="9822f-p120">R. na maioria dos casos, não há nenhuma alteração que os clientes no verão na sua declaração de faturamento.</span><span class="sxs-lookup"><span data-stu-id="9822f-p120">A. In most cases there are no changes that customers in will see on their billing statement.</span></span>
  
<span data-ttu-id="9822f-p121">A Microsoft irá cobra todos os clientes australiano do Office 365 quantidade adicional igual ao GST australiano para serviços do Office 365 e emitirá faturas de imposto. Essa alteração ocorrerá porque GST australiano é pago sobre tributável fornecimento de bens e serviços fornecidos e oferecidas em Austrália.</span><span class="sxs-lookup"><span data-stu-id="9822f-p121">Microsoft will charge all Australian customers of Office 365 an additional amount equal to the Australian GST for Office 365 services and will issue tax invoices. This change will occur because Australian GST is payable on taxable supplies of goods and services provided and offered in Australia.</span></span>
  
 <span data-ttu-id="9822f-182">**P. o que acontece se estamos estão em processo de migração de dados de email para o Office 365 durante a movimentação do Exchange Online?**</span><span class="sxs-lookup"><span data-stu-id="9822f-182">**Q. What happens if we are in process of email data migration to Office 365 during the Exchange Online move?**</span></span>
  
<span data-ttu-id="9822f-p122">R. Se as migrações de email estão em andamento, qualquer caixas de correio individuais que atualmente estão sendo migradas serão canceladas enquanto a movimentação de locatário finaliza e migração as caixas de correio será reiniciado automaticamente depois que o locatário estiver em centros de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="9822f-p122">A. If email migrations are in progress, any individual mailboxes that are currently being migrated will be canceled while the tenant move finalizes, and migration of those mailboxes will automatically restart once the tenant is in the target datacenters.</span></span>
  
 <span data-ttu-id="9822f-185">**P. após os dados são movidos sem o geo datacenter anterior, é ele removido dos data centers?**</span><span class="sxs-lookup"><span data-stu-id="9822f-185">**Q. After data is moved out of the previous datacenter geo, is it removed from those datacenters?**</span></span>
  
<span data-ttu-id="9822f-p123">R. Sim, os dados antigos serão removidos após um período de tempo.</span><span class="sxs-lookup"><span data-stu-id="9822f-p123">A. Yes, the old data will be purged after a period of time.</span></span>
  
 <span data-ttu-id="9822f-188">**P. posso testar alguns usuários?**</span><span class="sxs-lookup"><span data-stu-id="9822f-188">**Q. Can I pilot some users?**</span></span>
  
<span data-ttu-id="9822f-p124">R. quando seu locatário do Office 365 é movido para um novo geo de datacenter, todos os usuários são movidos ao mesmo tempo. Você pode criar um locatário separado de avaliação para testar a conectividade, mas o locatário avaliação não pode ser combinado de forma alguma com seu locatário existente.</span><span class="sxs-lookup"><span data-stu-id="9822f-p124">A. When your Office 365 tenant is moved to a new datacenter geo, all users are moved at once. You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>
  
 <span data-ttu-id="9822f-192">**P. como eu notificado sobre a movimentação e por quem em minha empresa será notificado?**</span><span class="sxs-lookup"><span data-stu-id="9822f-192">**Q. How will I be notified about the move and who at my company will be notified?**</span></span>
  
<span data-ttu-id="9822f-p125">R. usaremos o Centro de mensagem do Office 365, que é visível para qualquer pessoa com qualquer permissões de administrador no Office 365.</span><span class="sxs-lookup"><span data-stu-id="9822f-p125">A. We'll use the Office 365 message center, which is visible to anyone with any admin permissions in Office 365.</span></span>
  
 <span data-ttu-id="9822f-195">**P. eu não desejo esperar a Microsoft mover os meus dados. É possível apenas criar um novo inquilino e mover irei?**</span><span class="sxs-lookup"><span data-stu-id="9822f-195">**Q. I don't want to wait for Microsoft to move my data. Can I just create a new tenant and move myself?**</span></span>
  
<span data-ttu-id="9822f-p126">R. Sim, no entanto, o processo não será tão uniforme como se fosse do Microsoft executar a movimentação de dados.</span><span class="sxs-lookup"><span data-stu-id="9822f-p126">A. Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="9822f-p127">Se você criar um novo inquilino depois que o novo geo datacenter estiver disponível, o novo inquilino será hospedado em geo o novo. Este novo inquilino é completamente separado de seu locatário anterior e você seria responsável por movendo o conteúdo do site, todas as caixas de correio do usuário, nomes de domínio e quaisquer outros dados. Observe que você não pode mover o nome do locatário de um locatário para outro. Recomendamos que você aguarde o programa de movimentação fornecido pela Microsoft como vai cuidar de mover todas as configurações, dados e assinaturas para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="9822f-p127">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
 <span data-ttu-id="9822f-202">**P. eu não estiver pronta para ser movida, pode devo escolher uma data de movimentação específico?**</span><span class="sxs-lookup"><span data-stu-id="9822f-202">**Q. I'm not ready to be moved, can I pick a specific move date?**</span></span>
  
<span data-ttu-id="9822f-p128">R. It não é possível alterar quando os dados de cliente do cada serviço serão movidos. Movimentações de dados são uma operação de back-end com um impacto mínimo para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="9822f-p128">A. It is not possible for you to change when each service's customer data will be moved. Data moves are a back-end operation with minimal impact to end-users.</span></span>
  
 <span data-ttu-id="9822f-206">**P. meus dados do cliente já foi movidos para um novo geo de datacenter. Posso me mover novamente?**</span><span class="sxs-lookup"><span data-stu-id="9822f-206">**Q. My customer data has already been moved to a new datacenter geo. Can I move back?**</span></span>
  
<span data-ttu-id="9822f-p129">R. Isso não é possível. Os clientes que tiverem sido movidos para o novo data centers de geo não podem ser movidos novamente. Como um cliente na qualquer geo, fica a mesma qualidade de serviço, desempenho e controles de segurança como fez anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9822f-p129">A. This is not possible. Customers who have been moved to new geo datacenters cannot be moved back. As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>
  
 <span data-ttu-id="9822f-211">**Os novo geos datacenter p. usar as mesmas versões dos serviços do Office 365 como o geos datacenter atual?**</span><span class="sxs-lookup"><span data-stu-id="9822f-211">**Q. Do the new datacenter geos use the same versions of Office 365 services as the current datacenter geos?**</span></span>
  
<span data-ttu-id="9822f-p130">R. Sim.</span><span class="sxs-lookup"><span data-stu-id="9822f-p130">A. Yes.</span></span>
  
 <span data-ttu-id="9822f-214">**Inquilinos do p. será o Office 365 hospedados em datacenters a nova estará disponível para usuários externos do país?**</span><span class="sxs-lookup"><span data-stu-id="9822f-214">**Q. Will Office 365 tenants hosted in the new datacenters be available to users outside of the country?**</span></span>
  
<span data-ttu-id="9822f-p131">R. Sim. A Microsoft mantém uma rede global grande com conexões de Internet públicas nos locais mais de 50, 23 países em todo o mundo com contratos de correspondência com mais de 1.500 da Internet (provedores). Os usuários poderão acessar os datacenters onde quer que estejam na Internet.</span><span class="sxs-lookup"><span data-stu-id="9822f-p131">A. Yes. Microsoft maintains a large global network with public Internet connections in more than 50 locations in 23 countries around the world with peering agreements with more than 1,500 Internet Service Providers (ISPs). Users will be able to access the datacenters from wherever they are on the Internet.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="9822f-219">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="9822f-219">Related topics</span></span>

[<span data-ttu-id="9822f-220">Mover dados principais para o novo geos de datacenter do Office 365</span><span class="sxs-lookup"><span data-stu-id="9822f-220">Moving core data to new Office 365 datacenter geos</span></span>](moving-data-to-new-datacenter-geos.md)

[<span data-ttu-id="9822f-221">Como solicitar a migração dos dados</span><span class="sxs-lookup"><span data-stu-id="9822f-221">How to request your data move</span></span>](request-your-data-move.md)

[<span data-ttu-id="9822f-222">Novo geos datacenter para o Microsoft Dynamics CRM Online</span><span class="sxs-lookup"><span data-stu-id="9822f-222">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="9822f-223">Serviços do Azure por região</span><span class="sxs-lookup"><span data-stu-id="9822f-223">Azure services by region</span></span>](https://azure.microsoft.com/en-us/regions/)
