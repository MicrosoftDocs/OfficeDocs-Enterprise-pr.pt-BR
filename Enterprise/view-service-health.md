---
title: Como verificar a integridade do serviço Office 365
ms.author: kfollis
author: kfollis
manager: scotv
ms.date: 6/15/2018
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
ms.openlocfilehash: d01fe8e269ace922ab92cca779d6f8fea8b6802e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539199"
---
# <a name="how-to-check-office-365-service-health"></a>Como verificar a integridade do serviço Office 365

Você pode exibir a integridade do Office 365, Yammer, o Microsoft Dynamics CRM e serviços de nuvem da Microsoft Intune sobre o Office 365 * * integridade de serviço * * página no Centro de administração. Se você estiver enfrentando problemas com um serviço em nuvem, você pode verificar a integridade do serviço para determinar se esse é um problema conhecido com uma resolução em andamento antes de chamar suporte ou gasto na solução de problemas de tempo. 
  
### <a name="how-to-check-service-health"></a>Como verificar a integridade do serviço

1. Vá para [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e assinar com uma conta de administrador. 
    
    > [!NOTE]
    > Pessoas que receberem o administrador global ou a função de administrador de serviço podem exibir a integridade do serviço. Para permitir que o Exchange, SharePoint e Skype para administradores corporativos exibir a integridade do serviço, eles devem também ter a função de administrador de serviço. 
  
2. Para abrir a integridade do serviço, no Centro de administração, vá para **integridade** \> **integridade do serviço**ou clique no painel de Home de cartão de integridade do serviço. O cartão de painel indica se há um problema de serviço ativas e links para a página de integridade do serviço detalhados.
    
    ![Cartão de Dashboard de integridade do serviço](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. O estado de integridade de cada serviço de nuvem é mostrado em um formato de tabela com um ícone para indicar estados possíveis.
    
> [!TIP]
> Você também pode usar o [aplicativo de administração do Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) no seu dispositivo móvel para exibir a integridade do serviço, que é uma ótima maneira de permanecer atualizado com as notificações por push. 
  
### <a name="view-details-of-posted-service-health"></a>Exibir detalhes de integridade do serviço postados

No modo de exibição padrão, todos os serviços e respectivos estados vigentes de integridade são exibidas. Para filtrar sua opinião aos serviços experimentando um incidente, selecione **incidentes** da barra de sombreado à esquerda. Selecionar **os comunicados** mostrará apenas os serviços que possuírem um comunicado lançado. Da exibição **todos os serviços** , clicando no estado do serviço exibido será aberto um modo de exibição de resumo do comunicado ou incidente. 
  
![Modo de exibição de problemas atuais na integridade do serviço](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
O comunicado ou um incidente resumo fornece as seguintes informações: 
  
![Uma captura de tela rotular os campos em um comunicado do serviço](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. Um problema resumo e do identificador de declaração do problema.
    
2. O status atual. Consulte as definições de status neste artigo para obter uma explicação de cada status possíveis.
    
3. Uma descrição de como esse problema pode afetar os usuários.
    
4. A hora em que o problema foi iniciado e a última vez em que a mensagem de integridade do serviço foi atualizada. Por toda a duração de uma questão postar mensagens frequentes para informar o progresso que estamos fazendo nos aplicando uma solução.
    
5. Selecione o link **Mostrar detalhes** para ver mais detalhes sobre o problema, incluindo o histórico de todas as mensagens postadas enquanto trabalhamos em uma solução. 
    
### <a name="translate-service-health-details"></a>Traduzir os detalhes de integridade do serviço

Porque explicações de integridade do serviço são lançadas em tempo real, eles não são automaticamente convertidos em seu idioma e os detalhes de um evento de serviço estão apenas em inglês. Para traduzir a explicação, siga estas etapas:
  
1. Vá para o [tradutor](https://www.bing.com/translator/).
    
2. Na página **integridade do serviço** , selecione um incidente ou o comunicado. Em **Mostrar detalhes**, copie o texto sobre o problema.
    
3. No tradutor, colar o texto e escolha **Traduzir**.
    
### <a name="definitions"></a>Definições

A maioria dos serviços do tempo aparecerá como saudável sem mais informações. Quando um serviço está tendo um problema, o problema é identificado como um comunicado ou de um incidente e exibe o status atual.
  
> [!TIP]
> Planos de manutenção de eventos não são exibidos na integridade do serviço. Você pode controlar os eventos de manutenção planejada por permanecer atualizado com o **Centro de mensagens**. Filtrar mensagens classificadas como planejar a mudança para descobrir quando a alteração vai acontecer, seu efeito e como se preparar para ele. Para obter mais detalhes, consulte o [Centro de mensagens no Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) . 
  
### <a name="incidents-and-advisories"></a>Incidentes e comunicados

|||
|:-----|:-----|
|![Ícone de informações do comunicado](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Se um serviço tem um comunicado mostrado, que estamos cientes de um problema que está afetando a alguns usuários, mas o serviço está disponível ainda. Um comunicado, geralmente é uma solução alternativa para o problema, e o problema pode ser intermitente ou de impacto de escopo e o usuário está limitado.  <br/> |
|![Ícone de ponto de exclamação de incidente](media/a636db57-6083-44dc-bbd5-556850804f17.png)|Se um serviço tem um incidente ativo mostrado, é uma questão crítica e o serviço ou uma função principal do serviço não está disponível. Por exemplo, os usuários podem ser capaz de enviar e receber emails ou impossível sign-in. incidentes terá impacto perceptível aos usuários. Quando houver um incidente em andamento, forneceremos atualizações relacionadas a investigação, os esforços de redução de risco e a confirmação da resolução no painel de integridade do serviço.  <br/> |
   
### <a name="status-definitions"></a>Definições de status

| |
|**Status**|**Definição**|
|:-----|:-----|
|Investigando  <br/> |Estamos cientes de um problema potencial e reunindo mais informações sobre o que está acontecendo e o escopo do impacto.  <br/> |
|Degradação do serviço  <br/> |Temos confirmado que há um problema que pode afetar o uso de um serviço ou recurso. Você pode ver esse status se um serviço está executando mais lenta do que o normal, há interrupções intermitentes, ou se um recurso não está funcionando, por exemplo.  <br/> |
|Interrupção do serviço  <br/> |Você verá esse status se determinamos que um problema afeta a capacidade dos usuários acessar o serviço. Nesse caso, o problema é significativo e pode ser reproduzido de forma consistente.  <br/> |
|Restaurar o serviço  <br/> |A causa do problema foi identificada, nós sabemos qual ação corretiva a ser executada e no processo trazendo o serviço de volta para um estado íntegro.  <br/> |
|Recuperação estendida  <br/> |Esse status indica que uma ação corretiva estiver em andamento para restaurar o serviço à maioria dos usuários mas levarão algum tempo para chegar a todos os sistemas afetados. Você também poderá ver esse status se fizemos temporária corrigir para reduzir o impacto enquanto podemos esperar para aplicar uma correção permanente.  <br/> |
|Investigação suspensa  <br/> |Se nossa investigação detalhada de um problema potencial resulta em uma solicitação para obter informações adicionais de clientes para permitir a investigar melhor, você verá esse status. Se precisarmos para agir, vamos deixá-lo saber quais dados ou os logs precisamos.  <br/> |
|Serviço restaurado  <br/> |Temos confirmado que a ação corretiva tenha resolvido o problema subjacente e o serviço foi restaurado para um estado íntegro. Para saber o que deu errado, exiba os detalhes do problema.  <br/> |
   
## <a name="history"></a>Histórico

Integridade do serviço permite examinar o status atual da integridade e exibir o histórico de todos os comunicados de serviço e incidentes nos últimos 30 dias. Para exibir a integridade últimos de todos os serviços, selecione **Exibir histórico** na página **integridade do serviço** . 
  
![Mostrar link para o histórico de integridade](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
É exibida uma lista de todas as mensagens de integridade do serviço postadas em que o período de tempo selecionado, conforme mostrado a seguir:
  
![Exibir histórico de integridade do serviço](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
Você pode exibir o histórico de integridade para o nos últimos 7 dias ou últimos 30 dias. Selecione qualquer linha para exibir mais detalhes sobre esse problema.
  
Para obter mais informações sobre nosso compromisso com o tempo de atividade, consulte [operations transparentes do Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Deixar comentários

Nosso objetivo é certificar-se de que as informações que podemos fornecer a você sobre um problema em andamento estão em tempo hábil, precisos e úteis. Para nos informar como estamos indo, selecione uma classificação de estrela. Depois que você envie seus uma pontuação de 1 a 5 estrelas, você pode fornecer comentários em qualquer detalhes específicos. Usaremos seus comentários para ajustar o nosso sistema de integridade do serviço.
  
![Formulário de comentários para problemas de integridade do serviço](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a>Confira também

[Relatórios de atividade no Centro de administração do Office 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

