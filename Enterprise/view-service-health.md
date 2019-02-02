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
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Exibir o status de integridade de serviços do Office 365, antes de chamar o suporte para ver se houver uma interrupção de serviço ativas
ms.openlocfilehash: 52a7b762b8e86c3e538579f7c1e1611515469389
ms.sourcegitcommit: c7ad181394a8a3ee261dc44e7a1e70f6ebe7cbcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2019
ms.locfileid: "29696348"
---
# <a name="how-to-check-office-365-service-health"></a>Como verificar a integridade do serviço do Office 365

Você pode exibir a integridade do Office 365, Yammer, o Microsoft Dynamics CRM e serviços de nuvem da Microsoft Intune na página no Centro de administração do Office 365 **integridade do serviço** . Se você estiver enfrentando problemas com um serviço em nuvem, você pode verificar a integridade do serviço para determinar se esse é um problema conhecido com uma resolução em andamento antes de chamar suporte ou gasto na solução de problemas de tempo. 

Se você não conseguir entrar no portal do serviço, você pode usar a [página de status do serviço](https://status.office365.com) para verificar se há problemas conhecidos impedindo de fazer logon no seu locatário.
  
### <a name="how-to-check-service-health"></a>Como verificar a integridade do serviço

1. Acesse [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e entre com uma conta de administrador. 
    
    > [!NOTE]
    > As pessoas às quais a função de administrador global ou do serviço é atribuída podem visualizar a integridade do serviço. Para permitir que os administradores do Exchange, SharePoint e Skype for Business visualizem a integridade do serviço, eles também devem receber a função de administrador do serviço.
  
2. Para abrir a integridade do serviço, no Centro de administração, vá para **integridade** > **integridade do serviço**, ou clique no **cartão de integridade do serviço** do **Painel de Home**. O cartão de painel indica se há um problema de serviço ativas e links para a página de integridade do serviço detalhados.
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. O estado de integridade de cada serviço da nuvem é mostrado em um formato de tabela com um ícone para indicar possíveis estados.
    
> [!TIP]
> Você também pode usar o [aplicativo de administração do Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) no seu dispositivo móvel para visualizar a integridade do serviço, o que é uma ótima maneira de se manter atualizado com as notificações por push. 
  
### <a name="view-details-of-posted-service-health"></a>Exibir detalhes da integridade do serviço postado

No modo de exibição padrão, todos os serviços e respectivos estados vigentes de integridade são exibidas. Para filtrar sua opinião aos serviços experimentando um incidente, selecione **incidentes** da barra de sombreado à esquerda. Selecionar **os comunicados** mostrará apenas os serviços que possuírem um comunicado lançado. Da exibição **todos os serviços** , clicando no estado do serviço exibido será aberto um modo de exibição de resumo do comunicado ou incidente. 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
O resumo do aviso ou incidente fornece as seguintes informações: 
  
![Uma captura de tela rotular os campos em um comunicado do serviço](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. Um identificador de problemas e uma declaração resumida do problema.
    
2. O status atual. Veja as definições de status neste artigo para obter uma explicação de cada status potencial.
    
3. Uma descrição de como esse problema pode afetar os usuários.
    
4. O horário em que o problema foi iniciado e a última vez que a mensagem de integridade do serviço foi atualizada. Durante um problema, publicamos mensagens frequentes para que você saiba o progresso que estamos fazendo na aplicação de uma solução.
    
5. Selecione o link **Mostrar detalhes** para ver mais detalhes sobre o problema, inclusive o histórico de todas as mensagens postadas enquanto trabalhamos em uma solução. 
    
### <a name="translate-service-health-details"></a>Traduzir dados da integridade do serviço

Como as explicações de integridade do serviço são postadas em tempo real, elas não são traduzidas automaticamente para o seu idioma, e os detalhes de um evento de serviço estão apenas em inglês. Para traduzir a explicação, siga estas etapas:
  
1. Acesse [Tradutor](https://www.bing.com/translator/).
    
2. Na página **Integridade do Serviço**, selecione um incidente ou aviso. Em **Mostrar Detalhes**, copie o texto sobre o problema.
    
3. No Tradutor, cole o texto e escolha **Traduzir**.
    
### <a name="definitions"></a>Definições

A maioria dos serviços de tempo aparecerá como íntegro sem mais informações. Quando um serviço está com um problema, ele é identificado como um aviso ou um incidente e mostra um status atual.
  
> [!TIP]
> Os eventos de manutenção planejados não são exibidos na integridade do serviço. Você pode acompanhar os eventos de manutenção planejados atualizando-se com o **Centro de Mensagens**. Filtre para mensagens categorizadas como Preparar-se para a mudança para descobrir quando a mudança acontecerá, seu efeito e como se preparar para isso. Confira mais detalhes no [Centro de Mensagens no Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093). 
  
### <a name="incidents-and-advisories"></a>Incidentes e avisos

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Quando um serviço exibe um aviso, estamos cientes de um problema que está afetando alguns usuários, mas o serviço ainda está disponível. Em um aviso, muitas vezes há uma solução para o problema, e o problema pode ser intermitente ou ter alcance e impacto limitados no usuário.  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|Quando um serviço exibe um incidente ativo, esse é um problema crítico, e o serviço ou uma função principal do serviço está indisponível. Por exemplo, os usuários podem não conseguir enviar e receber emails, ou não é possível entrar. Os incidentes terão um impacto perceptível nos usuários. Quando há um incidente em andamento, fornecemos atualizações sobre a investigação, os esforços de atenuação e a confirmação de resolução no painel de Integridade do serviço.  <br/> |
   
### <a name="status-definitions"></a>Definições de status

|**Status**|**Definição**|
|:-----|:-----|
|**Investigando** | Estamos cientes de um possível problema e reunindo mais informações sobre o que está acontecendo e o escopo de impacto. |
|**Degradação do serviço** | Confirmamos que existe um problema que pode afetar o uso de um serviço ou recurso. Talvez você veja esse status se um serviço apresentar um desempenho mais lento do que o normal, se houver interrupções intermitentes ou se um recurso não estiver funcionando, por exemplo. |
|**Interrupção do serviço** | Você verá esse status se determinarmos que um problema afeta a capacidade dos usuários de acessar o serviço. Neste caso, a questão é significativa e pode ser reproduzida de forma consistente. |
|**Restaurando o serviço** | A causa do problema foi identificada, sabemos quais ações corretivas devem ser tomadas e estamos no processo de retomar o estado de integridade do serviço. |
|**Recuperação estendida** | Esse status indica que uma ação corretiva está em andamento para restaurar o serviço para a maioria dos usuários, mas levará algum tempo para alcançar todos os sistemas afetados. Você também poderá ver esse status se tivermos feito uma correção temporária para reduzir o impacto enquanto aguardamos para aplicar uma correção permanente. |
|**Investigação suspensa** | Se a nossa investigação detalhada de um problema potencial resultar em uma solicitação de informações adicionais de clientes para nos permitir investigar mais, você verá esse status. Se precisarmos de você para prosseguir, informaremos quais dados ou logs precisamos. |
|**Serviço restaurado** | Confirmamos que a ação corretiva solucionou o problema subjacente, e o serviço foi restaurado para um estado íntegro. Para descobrir o que deu errado, confira os detalhes do problema. |
|**Relatório de POST-incidente publicado** | Publicamos um relatório de incidente de postagem para um problema específico que inclui informações de causa raiz e próximas etapas para garantir que um problema semelhante não ocorrer novamente. |
   
## <a name="history"></a>Histórico

Integridade do serviço permite examinar o status atual da integridade e exibir o histórico de qualquer comunicados de serviço e incidentes que têm afetado seu locatário nos últimos 30 dias. Para exibir a integridade últimos de todos os serviços, selecione **Exibir histórico** na página **integridade do serviço** . 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
Uma lista de todas as mensagens de integridade de serviço postadas no cronograma selecionado é exibida, conforme mostrado abaixo:
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
Você pode exibir o histórico de integridade para o nos últimos 7 dias ou últimos 30 dias. Selecione qualquer linha para exibir mais detalhes sobre esse problema.
  
Para obter mais informações sobre nosso compromisso com o tempo de atividade, consulte [operations transparentes do Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Deixar comentários

Nosso objetivo é garantir que as informações que fornecemos a você sobre um problema em andamento sejam oportunas, precisas e úteis. Para nos dizer como estamos trabalhando, selecione uma classificação por estrelas. Depois de nos dar uma pontuação de 1 a 5 estrelas, você pode fazer comentários sobre qualquer detalhe específico. Usaremos seus comentários para ajustar o nosso sistema de integridade do serviço.
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a>Confira também

[Relatórios de Atividade no Centro de administração do Office 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

