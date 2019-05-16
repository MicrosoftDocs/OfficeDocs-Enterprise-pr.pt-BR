---
title: Como verificar a integridade do serviço do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: 67595bddaed23222d09c0e7f6f5353b764722f83
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071217"
---
# <a name="how-to-check-office-365-service-health"></a>Como verificar a integridade do serviço do Office 365

Você pode exibir a integridade do Office 365, do Yammer, do Microsoft Dynamics CRM e dos serviços de nuvem do Microsoft Intune na página **integridade do serviço** do Office 365 no centro de [administração do Microsoft 365](https://admin.microsoft.com). Se tiver problemas com um serviço em nuvem, poderá verificar a integridade do serviço para determinar se é um problema conhecido com uma resolução em andamento, antes de chamar o suporte ou perder tempo na solução de problemas. 

Se você não conseguir entrar no portal de serviço, poderá usar a [página status do serviço](https://status.office365.com) para verificar se há problemas conhecidos, impedindo o login no locatário.
  
### <a name="how-to-check-service-health"></a>Como verificar a integridade do serviço

1. Acesse [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e entre com uma conta de administrador. 
    
    > [!NOTE]
    > As pessoas às quais a função de administrador global ou do serviço é atribuída podem visualizar a integridade do serviço. Para permitir que os administradores do Exchange, SharePoint e Skype for Business visualizem a integridade do serviço, eles também devem receber a função de administrador do serviço.
  
2. Para abrir a integridade do serviço, no centro de administração, vá para**integridade do serviço**de **integridade** > ou clique no **cartão de integridade do serviço** no **painel inicial**. O cartão do painel indica se existe um problema de serviço ativo e links para a página de integridade do serviço detalhada.
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. O estado de integridade de cada serviço da nuvem é mostrado em um formato de tabela com um ícone para indicar possíveis estados.
    
> [!TIP]
> Você também pode usar o [aplicativo de administração do Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) no seu dispositivo móvel para visualizar a integridade do serviço, o que é uma ótima maneira de se manter atualizado com as notificações por push. 
  
### <a name="view-details-of-posted-service-health"></a>Exibir detalhes da integridade do serviço postado

No modo de exibição padrão, todos os serviços e seu estado de integridade atual são exibidos. Para filtrar o modo de exibição para serviços que estão experimentando um incidente, selecione **incidentes** da barra sombreada à esquerda. A **** seleção de comunicados mostrará apenas os serviços que têm um comunicado publicado no momento. No modo de exibição **todos os serviços** , clicar no estado de serviço exibido abrirá um modo de exibição de resumo do comunicado ou incidente. 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
O resumo do aviso ou incidente fornece as seguintes informações: 
  
![Uma captura de tela rotulando os campos em um comunicado de serviço](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
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
|**Relatório de pós-incidente publicado** | Publicamos um relatório de incidente de postagem para um problema específico que inclui informações de causa raiz e próximas etapas para garantir que um problema semelhante não ocorra. |
   
## <a name="history"></a>Histórico

A integridade do serviço permite que você examine o status de integridade atual e visualize o histórico de qualquer comunicados de serviço e incidentes que impactaram o locatário nos últimos 30 dias. Para visualizar o estado de integridade anterior de todos os serviços, selecione **Exibir Histórico** na página **Integridade do Serviço**. 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
Uma lista de todas as mensagens de integridade de serviço postadas no cronograma selecionado é exibida, conforme mostrado abaixo:
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
Você pode visualizar o histórico de integridade dos últimos 7 dias ou dos últimos 30 dias. Selecione qualquer linha para exibir mais detalhes sobre esse problema.
  
Para obter mais informações sobre nosso compromisso com o tempo de atividade, consulte [operações transparentes do Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Deixar comentários

Nosso objetivo é garantir que as informações que fornecemos a você sobre um problema em andamento sejam oportunas, precisas e úteis. Para nos dizer como estamos trabalhando, selecione uma classificação por estrelas. Depois de nos dar uma pontuação de 1 a 5 estrelas, você pode fazer comentários sobre qualquer detalhe específico. Usaremos seus comentários para ajustar o nosso sistema de integridade do serviço.
  
## <a name="see-also"></a>Confira também

[Relatórios de atividades no centro de administração do Microsoft 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)