---
title: Como solicitar a migração dos dados
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
description: Os clientes existentes do Office 365 precisarão enviar uma solicitação antes do prazo final do seu país para que os dados do cliente de seus serviços do Office 365 participantes sejam movidos para a nova geografia.
ms.openlocfilehash: 97fc83db3ceac1a5c3aca65f8b780a3f7841528c
ms.sourcegitcommit: 77b8fd702d3a1010d3906d4024d272ad2097f54f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "39962458"
---
# <a name="how-to-request-your-data-move"></a>Como solicitar a migração dos dados

> [!NOTE]
> As informações nesta página só se aplicam aos clientes que tinham locatários do Office 365 antes dos novos datacenters em sua geografia. 
  
Os clientes existentes do Office 365 estão qualificados para solicitar a migração inicial de todos os dados do cliente principais da sua organização em repouso.  
  
## <a name="when-can-i-request-a-move"></a>Quando posso solicitar uma movimentação?

|**Clientes com país de inscrição no**|**Início do período da solicitação**|**Prazo da solicitação**|
|:-----|:-----|:-----|
|Japão  <br/> |1 de agosto de 2016  <br/> |31 de outubro de 2016  <br/> |
|Austrália, Nova Zelândia, Fiji  <br/> |1 de agosto de 2016  <br/> |31 de outubro de 2016  <br/> |
|Índia  <br/> |1 de agosto de 2016  <br/> |31 de outubro de 2016  <br/> |
|Canadá  <br/> |1 de agosto de 2016  <br/> |31 de outubro de 2016  <br/> |
|Reino Unido  <br/> |15 de março de 2017  <br/> |15 de setembro de 2017  <br/> |
|Coréia do Sul  <br/> |1 de maio de 2017  <br/> |31 de outubro de 2017  <br/> |
|França  <br/> |14 de março de 2018  <br/> |15 de setembro de 2018  <br/> |
|Emirados Árabes Unidos  <br/> |15 de julho de 2019  <br/> |31 de janeiro de 2020  <br/> |
|África do Sul  <br/> |25 de julho de 2019  <br/> |31 de janeiro de 2020  <br/> |
|Suíça, Liechtenstein  <br/> |10 de dezembro de 2019  <br/> |30 de junho de 2020  <br/> |
|Alemanha  <br/> |Liga  <br/> |Liga  <br/> |
   
## <a name="how-to-request-a-move"></a>Como solicitar uma movimentação

Os clientes qualificados verão uma página no [centro de administração do Microsoft 365](https://aka.ms/365admin), que lhes permitirá solicitar que seus principais dados do cliente sejam movidos para sua nova região de datacenter.  
  
Para acessar a página no centro de administração do Microsoft 365, no painel de navegação à esquerda, expanda **configurações**e clique em **perfil da organização**.
  
![Menu configurações com perfil organizacional realçado](media/22799fac-32b4-4f79-ae60-3f6ffb7cfbd7.png)
  
Na página **perfil da organização** , role para baixo até a seção **opção de residência de dados** . 
  
![Cartão de residência de dados](media/dataresidencyae.jpg)
  
**Talvez você não veja esta seção se uma das seguintes opções se aplicar**:
- Seu locatário não está qualificado para o programa Office 365 move.  A qualificação é determinada pelo país de inscrição do locatário.
- Todos os dados principais do cliente em repouso já estão localizados na nova Geografia (consulte a seção local dos dados da página). 
  
Se sua organização tiver requisitos de residência de dados e você precisar solicitar a migração inicial, clique em **aceitar** no canto superior direito da seção. Uma nova seção será exibida no lado direito da tela explicando os detalhes do programa Office 365 move. Selecione o botão de alternância ao lado do texto que diz que **desejo aos dados principais do cliente da minha organização em repouso para migrar**. Em seguida, clique em **Salvar**.
  
![Tela de aceitação de data center](media/dataresidencyflyoutae.jpg)
  
Você deve ver o texto na seção **residência de dados** alterar para indicar que **sua organização solicitou a movimentação de seus dados principais de cliente.** Você também terá uma mensagem de confirmação no centro de mensagens. Isso confirma que você solicitou uma movimentação com êxito. 


  
## <a name="what-happens-after-requesting-a-move"></a>O que acontece depois de solicitar uma movimentação?

Depois de solicitar uma movimentação, planejaremos movê-lo tão rapidamente quanto nossas restrições operacionais permitir. Devido à natureza imprevisível de muitas das restrições, não é possível compartilhar uma data ou um intervalo de tempo específico para as movimentações. Você verá uma notificação após a conclusão da movimentação.
  
As movimentações podem levar até 24 meses do prazo da solicitação para que o seu país seja concluído.
  
## <a name="microsoft-teams"></a>Microsoft Teams

Suporte à migração para o Microsoft Teams chat e os dados da mensagem do canal serão adicionados ao programa de migração local do Office 365.  Planejamos abrir o registro de programa em janeiro de 2020 para todos os clientes qualificados, incluindo clientes que anteriormente optaram por migrar para o Exchange Online e o SharePoint Online/OneDrive for Business.  Vamos expor o controle de consentimento no centro de administração do Microsoft 365 e enviar uma notificação no centro de mensagens para todos os clientes qualificados.   

## <a name="optional-actions-before-you-request-a-move"></a>Ações opcionais antes de solicitar uma movimentação

Execute as seguintes etapas, conforme apropriado.
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>Se você usar um firewall baseado em IP, adicione regras de permissão para os novos endereços IP

Recomendamos o uso da filtragem de DNS para firewalls em vez de endereços IP. Não há novas entradas DNS necessárias.
  
Se você usar um firewall baseado em IP para conectividade com a Internet, deverá adicionar regras de permissão para os novos endereços IP para a geografia do datacenter de destino. Os endereços IP para novos GEOS de datacenter, além de novos servidores, são adicionados de forma contínua às [URLs e intervalos de endereços IP do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=229631).
  
Consulte a documentação do firewall para obter informações sobre como adicionar regras de permissão (também conhecida como lista branca).
  
Após adicionar endereços IP, convém testar a conectividade com a nova Geografia do datacenter. Para fazer isso, recomendamos criar um [novo locatário gratuito de avaliação de 30 dias](https://go.microsoft.com/fwlink/?LinkId=522463) assim que a nova Geografia do datacenter estiver disponível. 
  
### <a name="test-using-a-new-tenant"></a>Testar usando um novo locatário

Se quiser testar a conectividade antes da movimentação, você pode configurar um [novo locatário gratuito de avaliação de 30 dias](https://go.microsoft.com/fwlink/?LinkId=522463) depois que a nova Geografia do datacenter estiver disponível e usá-la para experimentar o Office 365 hospedado na nova Geografia do datacenter. 
  
O locatário de avaliação não pode ser combinado com seu locatário existente:
  
- Os usuários devem usar uma conta de avaliação separada para o teste.
    
- Não é possível mover dados entre locatários.
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>Notificar os usuários para atualizar configurações do Exchange desatualizadas em dispositivos móveis

Se os usuários tiverem um dispositivo móvel com o Exchange Server definido como **m.Outlook.com** ou **podxxxxx.Outlook.com**, recomendamos que eles alternem para o **Outlook.office365.com**, seguindo as instruções em [configurar um dispositivo móvel para sincronizar com sua conta](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).

## <a name="related-topics"></a>Tópicos relacionados

[Movendo dados principais para o novo Office 365 datacenter GEOS](moving-data-to-new-datacenter-geos.md)

[Perguntas frequentes gerais sobre migração de dados](data-move-faq.md)

[Nova GEOS de datacenter do Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Serviços do Azure por região](https://azure.microsoft.com/regions/)
  

