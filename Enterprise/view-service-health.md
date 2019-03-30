---
title: Como verificar a integridade do serviço do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Exibir o status de integridade dos serviços do Office 365 antes de ligar para o suporte para ver se há uma interrupção de serviço ativa
ms.openlocfilehash: 483ff0ff6507010c9a81f0774fc8c3e8820395cb
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001574"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="c136e-103">Como verificar a integridade do serviço do Office 365</span><span class="sxs-lookup"><span data-stu-id="c136e-103">How to check Office 365 service health</span></span>

<span data-ttu-id="c136e-104">Você pode exibir a integridade do Office 365, do Yammer, do Microsoft Dynamics CRM e dos serviços de nuvem do Microsoft Intune na página **integridade do serviço** do Office 365 no centro de [administração do Microsoft 365](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="c136e-104">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="c136e-105">Se tiver problemas com um serviço em nuvem, poderá verificar a integridade do serviço para determinar se é um problema conhecido com uma resolução em andamento, antes de chamar o suporte ou perder tempo na solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="c136e-105">If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="c136e-106">Se você não conseguir entrar no portal de serviço, poderá usar a [página status do serviço](https://status.office365.com) para verificar se há problemas conhecidos, impedindo o login no locatário.</span><span class="sxs-lookup"><span data-stu-id="c136e-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="c136e-107">Como verificar a integridade do serviço</span><span class="sxs-lookup"><span data-stu-id="c136e-107">How to check service health</span></span>

1. <span data-ttu-id="c136e-108">Acesse [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e entre com uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="c136e-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="c136e-p102">As pessoas às quais a função de administrador global ou do serviço é atribuída podem visualizar a integridade do serviço. Para permitir que os administradores do Exchange, SharePoint e Skype for Business visualizem a integridade do serviço, eles também devem receber a função de administrador do serviço.</span><span class="sxs-lookup"><span data-stu-id="c136e-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="c136e-111">Para abrir a integridade do serviço, no centro de administração, vá para**integridade do serviço**de **integridade** > ou clique no **cartão de integridade do serviço** no **painel inicial**.</span><span class="sxs-lookup"><span data-stu-id="c136e-111">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**.</span></span> <span data-ttu-id="c136e-112">O cartão do painel indica se existe um problema de serviço ativo e links para a página de integridade do serviço detalhada.</span><span class="sxs-lookup"><span data-stu-id="c136e-112">The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="c136e-114">O estado de integridade de cada serviço da nuvem é mostrado em um formato de tabela com um ícone para indicar possíveis estados.</span><span class="sxs-lookup"><span data-stu-id="c136e-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="c136e-115">Você também pode usar o [aplicativo de administração do Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) no seu dispositivo móvel para visualizar a integridade do serviço, o que é uma ótima maneira de se manter atualizado com as notificações por push.</span><span class="sxs-lookup"><span data-stu-id="c136e-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="c136e-116">Exibir detalhes da integridade do serviço postado</span><span class="sxs-lookup"><span data-stu-id="c136e-116">View details of posted service health</span></span>

<span data-ttu-id="c136e-117">No modo de exibição padrão, todos os serviços e seu estado de integridade atual são exibidos.</span><span class="sxs-lookup"><span data-stu-id="c136e-117">In the default view, all services and their current health state are displayed.</span></span> <span data-ttu-id="c136e-118">Para filtrar o modo de exibição para serviços que estão experimentando um incidente, selecione **incidentes** da barra sombreada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="c136e-118">To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left.</span></span> <span data-ttu-id="c136e-119">A \*\*\*\* seleção de comunicados mostrará apenas os serviços que têm um comunicado publicado no momento.</span><span class="sxs-lookup"><span data-stu-id="c136e-119">Selecting **Advisories** will show only services that currently have an advisory posted.</span></span> <span data-ttu-id="c136e-120">No modo de exibição **todos os serviços** , clicar no estado de serviço exibido abrirá um modo de exibição de resumo do comunicado ou incidente.</span><span class="sxs-lookup"><span data-stu-id="c136e-120">From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="c136e-122">O resumo do aviso ou incidente fornece as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="c136e-122">The advisory or incident summary provides the following information:</span></span> 
  
![Uma captura de tela rotulando os campos em um comunicado de serviço](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="c136e-124">Um identificador de problemas e uma declaração resumida do problema.</span><span class="sxs-lookup"><span data-stu-id="c136e-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="c136e-p105">O status atual. Veja as definições de status neste artigo para obter uma explicação de cada status potencial.</span><span class="sxs-lookup"><span data-stu-id="c136e-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="c136e-127">Uma descrição de como esse problema pode afetar os usuários.</span><span class="sxs-lookup"><span data-stu-id="c136e-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="c136e-p106">O horário em que o problema foi iniciado e a última vez que a mensagem de integridade do serviço foi atualizada. Durante um problema, publicamos mensagens frequentes para que você saiba o progresso que estamos fazendo na aplicação de uma solução.</span><span class="sxs-lookup"><span data-stu-id="c136e-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="c136e-130">Selecione o link **Mostrar detalhes** para ver mais detalhes sobre o problema, inclusive o histórico de todas as mensagens postadas enquanto trabalhamos em uma solução.</span><span class="sxs-lookup"><span data-stu-id="c136e-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="c136e-131">Traduzir dados da integridade do serviço</span><span class="sxs-lookup"><span data-stu-id="c136e-131">Translate service health details</span></span>

<span data-ttu-id="c136e-p107">Como as explicações de integridade do serviço são postadas em tempo real, elas não são traduzidas automaticamente para o seu idioma, e os detalhes de um evento de serviço estão apenas em inglês. Para traduzir a explicação, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="c136e-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="c136e-134">Acesse [Tradutor](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="c136e-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="c136e-p108">Na página **Integridade do Serviço**, selecione um incidente ou aviso. Em **Mostrar Detalhes**, copie o texto sobre o problema.</span><span class="sxs-lookup"><span data-stu-id="c136e-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="c136e-137">No Tradutor, cole o texto e escolha **Traduzir**.</span><span class="sxs-lookup"><span data-stu-id="c136e-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="c136e-138">Definições</span><span class="sxs-lookup"><span data-stu-id="c136e-138">Definitions</span></span>

<span data-ttu-id="c136e-p109">A maioria dos serviços de tempo aparecerá como íntegro sem mais informações. Quando um serviço está com um problema, ele é identificado como um aviso ou um incidente e mostra um status atual.</span><span class="sxs-lookup"><span data-stu-id="c136e-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="c136e-p110">Os eventos de manutenção planejados não são exibidos na integridade do serviço. Você pode acompanhar os eventos de manutenção planejados atualizando-se com o **Centro de Mensagens**. Filtre para mensagens categorizadas como Preparar-se para a mudança para descobrir quando a mudança acontecerá, seu efeito e como se preparar para isso. Confira mais detalhes no [Centro de Mensagens no Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093).</span><span class="sxs-lookup"><span data-stu-id="c136e-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="c136e-145">Incidentes e avisos</span><span class="sxs-lookup"><span data-stu-id="c136e-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="c136e-p111">Quando um serviço exibe um aviso, estamos cientes de um problema que está afetando alguns usuários, mas o serviço ainda está disponível. Em um aviso, muitas vezes há uma solução para o problema, e o problema pode ser intermitente ou ter alcance e impacto limitados no usuário.</span><span class="sxs-lookup"><span data-stu-id="c136e-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="c136e-p112">Quando um serviço exibe um incidente ativo, esse é um problema crítico, e o serviço ou uma função principal do serviço está indisponível. Por exemplo, os usuários podem não conseguir enviar e receber emails, ou não é possível entrar. Os incidentes terão um impacto perceptível nos usuários. Quando há um incidente em andamento, fornecemos atualizações sobre a investigação, os esforços de atenuação e a confirmação de resolução no painel de Integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="c136e-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="c136e-154">Definições de status</span><span class="sxs-lookup"><span data-stu-id="c136e-154">Status definitions</span></span>

|<span data-ttu-id="c136e-155">**Status**</span><span class="sxs-lookup"><span data-stu-id="c136e-155">**Status**</span></span>|<span data-ttu-id="c136e-156">**Definição**</span><span class="sxs-lookup"><span data-stu-id="c136e-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c136e-157">**Investigando**</span><span class="sxs-lookup"><span data-stu-id="c136e-157">**Investigating**</span></span> | <span data-ttu-id="c136e-158">Estamos cientes de um possível problema e reunindo mais informações sobre o que está acontecendo e o escopo de impacto.</span><span class="sxs-lookup"><span data-stu-id="c136e-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="c136e-159">**Degradação do serviço**</span><span class="sxs-lookup"><span data-stu-id="c136e-159">**Service degradation**</span></span> | <span data-ttu-id="c136e-p113">Confirmamos que existe um problema que pode afetar o uso de um serviço ou recurso. Talvez você veja esse status se um serviço apresentar um desempenho mais lento do que o normal, se houver interrupções intermitentes ou se um recurso não estiver funcionando, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="c136e-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="c136e-162">**Interrupção do serviço**</span><span class="sxs-lookup"><span data-stu-id="c136e-162">**Service interruption**</span></span> | <span data-ttu-id="c136e-p114">Você verá esse status se determinarmos que um problema afeta a capacidade dos usuários de acessar o serviço. Neste caso, a questão é significativa e pode ser reproduzida de forma consistente.</span><span class="sxs-lookup"><span data-stu-id="c136e-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="c136e-165">**Restaurando o serviço**</span><span class="sxs-lookup"><span data-stu-id="c136e-165">**Restoring service**</span></span> | <span data-ttu-id="c136e-166">A causa do problema foi identificada, sabemos quais ações corretivas devem ser tomadas e estamos no processo de retomar o estado de integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="c136e-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="c136e-167">**Recuperação estendida**</span><span class="sxs-lookup"><span data-stu-id="c136e-167">**Extended recovery**</span></span> | <span data-ttu-id="c136e-p115">Esse status indica que uma ação corretiva está em andamento para restaurar o serviço para a maioria dos usuários, mas levará algum tempo para alcançar todos os sistemas afetados. Você também poderá ver esse status se tivermos feito uma correção temporária para reduzir o impacto enquanto aguardamos para aplicar uma correção permanente.</span><span class="sxs-lookup"><span data-stu-id="c136e-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="c136e-170">**Investigação suspensa**</span><span class="sxs-lookup"><span data-stu-id="c136e-170">**Investigation suspended**</span></span> | <span data-ttu-id="c136e-p116">Se a nossa investigação detalhada de um problema potencial resultar em uma solicitação de informações adicionais de clientes para nos permitir investigar mais, você verá esse status. Se precisarmos de você para prosseguir, informaremos quais dados ou logs precisamos.</span><span class="sxs-lookup"><span data-stu-id="c136e-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="c136e-173">**Serviço restaurado**</span><span class="sxs-lookup"><span data-stu-id="c136e-173">**Service restored**</span></span> | <span data-ttu-id="c136e-p117">Confirmamos que a ação corretiva solucionou o problema subjacente, e o serviço foi restaurado para um estado íntegro. Para descobrir o que deu errado, confira os detalhes do problema.</span><span class="sxs-lookup"><span data-stu-id="c136e-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="c136e-176">**Relatório de pós-incidente publicado**</span><span class="sxs-lookup"><span data-stu-id="c136e-176">**Post-incident report published**</span></span> | <span data-ttu-id="c136e-177">Publicamos um relatório de incidente de postagem para um problema específico que inclui informações de causa raiz e próximas etapas para garantir que um problema semelhante não ocorra.</span><span class="sxs-lookup"><span data-stu-id="c136e-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="c136e-178">Histórico</span><span class="sxs-lookup"><span data-stu-id="c136e-178">History</span></span>

<span data-ttu-id="c136e-179">A integridade do serviço permite que você examine o status de integridade atual e visualize o histórico de qualquer comunicados de serviço e incidentes que impactaram o locatário nos últimos 30 dias.</span><span class="sxs-lookup"><span data-stu-id="c136e-179">Service health lets you look at current health status and view the history of any service advisories and incidents that have impacted your tenant in the past 30 days.</span></span> <span data-ttu-id="c136e-180">Para visualizar o estado de integridade anterior de todos os serviços, selecione **Exibir Histórico** na página **Integridade do Serviço**.</span><span class="sxs-lookup"><span data-stu-id="c136e-180">To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="c136e-182">Uma lista de todas as mensagens de integridade de serviço postadas no cronograma selecionado é exibida, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="c136e-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="c136e-184">Você pode visualizar o histórico de integridade dos últimos 7 dias ou dos últimos 30 dias.</span><span class="sxs-lookup"><span data-stu-id="c136e-184">You may view the health history for either the last 7 days or last 30 days.</span></span> <span data-ttu-id="c136e-185">Selecione qualquer linha para exibir mais detalhes sobre esse problema.</span><span class="sxs-lookup"><span data-stu-id="c136e-185">Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="c136e-186">Para obter mais informações sobre nosso compromisso com o tempo de atividade, consulte [operações transparentes do Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="c136e-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="c136e-187">Deixar comentários</span><span class="sxs-lookup"><span data-stu-id="c136e-187">Leave feedback</span></span>

<span data-ttu-id="c136e-p120">Nosso objetivo é garantir que as informações que fornecemos a você sobre um problema em andamento sejam oportunas, precisas e úteis. Para nos dizer como estamos trabalhando, selecione uma classificação por estrelas. Depois de nos dar uma pontuação de 1 a 5 estrelas, você pode fazer comentários sobre qualquer detalhe específico. Usaremos seus comentários para ajustar o nosso sistema de integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="c136e-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c136e-192">Confira também</span><span class="sxs-lookup"><span data-stu-id="c136e-192">See also</span></span>

[<span data-ttu-id="c136e-193">Relatórios de atividades no centro de administração do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c136e-193">Activity Reports in the Microsoft 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)