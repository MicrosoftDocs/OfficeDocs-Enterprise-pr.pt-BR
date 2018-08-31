---
title: Como solicitar a migração dos dados
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 3/22/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
description: Os clientes existentes do Office 365 precisará enviar uma solicitação antes do prazo para seu país para que os dados do cliente dos seus serviços do Office 365 participantes movidos para sua nova geo.
ms.openlocfilehash: 850a3a81b7e0405d47e36726e328ea078ae3f55c
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23222973"
---
# <a name="how-to-request-your-data-move"></a>Como solicitar a migração dos dados

> [!NOTE]
> As informações nesta página só se aplica aos clientes que tinham locatários existentes do Office 365, antes que os datacenters novos em seu geo iniciado. 
  
Os clientes existentes do Office 365 precisará enviar uma solicitação antes do prazo para seu país para que os dados do cliente dos seus serviços do Office 365 participantes movidos para sua nova geo. 
  
Estamos não consegue aceitar solicitações a serem movidos depois do prazo em cada geo. 
  
## <a name="when-can-i-request-a-move"></a>Quando solicitar uma movimentação?

|**Clientes com o endereço de cobrança**|**Solicitar o período começa**|**Prazo final de solicitação**|
|:-----|:-----|:-----|
|Japão  <br/> |1 de agosto de 2016  <br/> |31 de outubro de 2016  <br/> |
|Austrália, Nova Zelândia, Fiji  <br/> |1 de agosto de 2016  <br/> |31 de outubro de 2016  <br/> |
|Índia  <br/> |1 de agosto de 2016  <br/> |31 de outubro de 2016  <br/> |
|Canadá  <br/> |1 de agosto de 2016  <br/> |31 de outubro de 2016  <br/> |
|Reino Unido  <br/> |15 de março de 2017  <br/> |15 de setembro de 2017  <br/> |
|Coreia do Sul  <br/> |1 de maio de 2017  <br/> |31 de outubro de 2017  <br/> |
|França  <br/> |14 de março de 2018  <br/> |15 de setembro de 2018  <br/> |
   
## <a name="how-to-request-a-move"></a>Como solicitar uma movimentação

> [!NOTE]
> Essa opção só está disponível no Centro de administração do Office 365 Preview. Para obter instruções sobre como acessar esse, consulte [Office 365 para empresas - ajuda de Admin](https://aka.ms/365admin). Todas as solicitações para movimentações precisam ser feito por meio do Centro de administração do Office 365. Suporte não será capaz de fazer essa seleção para você ou substituir sua seleção. 
  
Os clientes qualificados verão uma página no seu [Centro de administração do Office 365](https://aka.ms/365admin), que lhes permitirão solicitar que os dados dos clientes de núcleo movidos para a sua nova região de datacenter.  
  
Para acessar a página no Centro de administração do Office 365, no painel de navegação à esquerda, expanda **configurações**e clique em **Perfil da organização**.
  
![Menu Configurações com Perfil Organizacional realçado](media/22799fac-32b4-4f79-ae60-3f6ffb7cfbd7.png)
  
Na página **Perfil da organização** , role até a seção **Opção de residência de dados** . 
  
![Cartão de residência de dados](media/fdb02cd0-825d-4d9e-bb35-6f806282884f.png)
  
**Você não pode ver nesta seção se aplicar por um dos seguintes**:
- Seu locatário não está qualificado para o programa de movimentação. 
- Todos os seus dados já estão localizados no novo geo (consulte a seção de dados local da página). 
  
> [!IMPORTANT]
> **Você vai fazer uma escolha importante para sua organização. Após confirmar a opção a seguir, você não pode desfazê-lo. Suporte é não é possível reverter essa decisão também.**
  
Se sua organização tem requisitos de residência de dados, e você precisa solicitar uma movimentação, clique em **Editar** na parte superior direita da seção. Uma nova seção aparecerá no lado direito da tela que explica os detalhes do programa de movimentação. Selecione o botão de alternância ao lado do texto que diz **Sim, minha organização tem requisitos de residência de dados**. Em seguida, clique em **Salvar**.
  
![Tela de aceitação de data center](media/f97ab8d2-b0e1-49bf-9d6b-bf75f3081233.png)
  
Você deve ver o texto sobre a alteração da seção de **Dados residência opção** para indicar **sua organização solicitou para mover dados de cliente seu core.** Você também terá uma mensagem de confirmação no Centro de sua mensagem. Isso confirma que você solicitou uma movimentação com êxito. 


  
## <a name="what-happens-after-requesting-a-move"></a>O que acontece após a solicitação de movimento?

Após a solicitação de movimento, podemos planeja mover você rapidamente nossas restrições operacionais permitem. Devido à natureza imprevisível de muitas das restrições, podemos não pode compartilhar uma data específica ou intervalo de tempo para as movimentações. Depois que a movimentação for concluída, você verá uma notificação.
  
Movimentações podem demorar até 24 meses a partir do prazo de solicitação para o seu país concluir.
  
Após a solicitação de uma movimentação, não é possível alterar sua seleção conforme começamos processar as movimentações, já que você fez a solicitação.
  
## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft Teams ainda não dá suporte para migração de conteúdo do cliente em repouso na região para centros de dados de país onde residência de dados for Microsoft Teams está disponível.  Portanto, somente os novos clientes terão todos os seus dados armazenados no país nas novas regiões onde Teams Microsoft suporta residência de dados.  Saiba mais sobre o Office 365 residência de dados para o seu local de empresa no [onde estão seus dados localizados?](https://office/com/datamaps)   

## <a name="optional-actions-before-you-request-a-move"></a>Ações opcionais antes de você solicitar uma movimentação

Execute as etapas a seguir conforme apropriado.
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>Se você usar um firewall com base em IP, adicionar regras para os novos endereços IP de permissão

É recomendável usar a filtragem para firewalls, em vez de endereços IP de DNS. Não há nenhuma novas entradas DNS necessárias.
  
Se você usar um firewall com base em IP para conectividade de Internet, você deve adicionar regras para os novos endereços IP para o destino datacenter geo de permissão. Endereços IP para o novo geos datacenter além dos novos servidores continuamente são adicionados ao [Office 365 URLs e intervalos de endereço IP](https://go.microsoft.com/fwlink/p/?LinkId=229631).
  
Consultar a documentação do firewall para obter informações sobre como adicionar permitir regras (também conhecidas como lista de exceções.)
  
Após adicionar endereços IP, você deseja testar a conectividade com o novo geo datacenter. Para fazer isso, recomendamos que você criar um locatário da [nova versão gratuita de avaliação de 30 dias](https://go.microsoft.com/fwlink/?LinkId=522463) , assim que o novo geo datacenter está disponível. 
  
### <a name="test-using-a-new-tenant"></a>Testar usando um novo inquilino

Se você quiser testar a conectividade antes da movimentação, você pode configurar um [novo inquilino de avaliação de 30 dias gratuito](https://go.microsoft.com/fwlink/?LinkId=522463) depois que o novo geo datacenter está disponível e usá-lo para experimentar o Office 365 hospedados no novo geo datacenter. 
  
O inquilino avaliação não pode ser combinado com seu locatário existente:
  
- Os usuários devem usar uma conta separada de avaliação para seus testes.
    
- Não há um meio para mover dados entre locatários.
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>Notificar os usuários a atualizarem desatualizadas configurações do Exchange em dispositivos móveis

Se os usuários têm um dispositivo móvel com o Exchange Server definida como **m.outlook.com** ou **podxxxxx.outlook.com**, recomendamos que elas alternam para **outlook.office365.com**, seguindo as instruções em [Set up um dispositivo móvel para sincronizar com a sua conta](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).
  

