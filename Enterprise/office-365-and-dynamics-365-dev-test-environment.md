---
title: Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: "Resumo: Use este guia de laboratório de teste para adicionar Dynamics 365 ao seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: f13cf81f989867e543439e1ccb6ecd7f8ba55cb6
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365

 **Resumo:** Use este guia de laboratório de teste para adicionar Dynamics 365 ao seu ambiente de desenvolvimento e teste do Office 365.
  
Com as instruções deste artigo, você adiciona uma assinatura de avaliação do Dynamics 365 à mesma organização que seu ambiente de desenvolvimento e teste do Office 365, criação de um ambiente de desenvolvimento e teste do Office 365 e Dynamics 365.
  
Você pode usar uma assinatura de avaliação do Dynamics 365 para demonstrar os recursos e capacidades do Dynamics 365. As seguintes soluções estão incluídas com uma Dynamics 365 plano 1, Enterprise Edition de avaliação:
  
- O [Microsoft Dynamics 365 de vendas](https://www.microsoft.com/dynamics365/sales). Aumente suas vendas com automação e digital intelligence ajudando seus vendedores manter o foco e trabalhar de forma mais inteligente.
    
- O [Microsoft Dynamics 365 para atendimento ao cliente](https://www.microsoft.com/dynamics365/customer-service). Ganhe fidelidade, dando a seus agentes as informações completas e inteligência digital que precisam fornecer serviço contínuo.
    
- O [Microsoft Dynamics 365 para o serviço de campo](https://www.microsoft.com/dynamics365/field-service). A chamada de serviço do mestre otimizando as agendas, equipando sua força de trabalho e usando ferramentas de previsão para aumentar o lucro.
    
- O [Microsoft Dynamics 365 para automação de serviço do projeto](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Conclua a seus projetos com êxito e criar relacionamentos lucrativos com funcionários produtivos e ferramentas inteligentes.
    
Você pode explorar uma ou mais das perguntas acima para sua assinatura de avaliação do Dynamics 365.
  
![Guias do Laboratório de Teste da Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada

Se você quiser testar o Office 365 e Dynamics 365 de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar o Office 365 e Dynamics 365 para uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> A configuração neste artigo não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você pode experimentar com o Office 365 e Dynamics 365 em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>Fase 2: Adicionar uma assinatura de avaliação do Dynamics 365

Nesta fase, inscreva-se para a assinatura de avaliação do Dynamics 365 e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365.
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>Inscreva-se para uma assinatura de avaliação do Dynamics 365

1. Usando um navegador em um computador desktop (lightweight) ou CLIENT1 (simulados enterprise), entre no portal do Office 365 em [https://portal.office.com](https://portal.office.com) com as credenciais da sua conta de administrador global.
    
2. Clique no lado do **Admin** .
    
3. Na guia **Centro de administração do Office** , no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.
    
4. Na página **Serviços de compra** , encontre o item **Dynamics 365 planejar 1 Enterprise Edition** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.
    
5. Na página **confirmar seu pedido** , clique em **tente agora**.
    
6. Na página **confirmação de ordem** , clique em **continuar**.
    
> [!NOTE]
> A assinatura de avaliação do Dynamics 365 planejar 1 Enterprise Edition é 30 dias. Você pode estender facilmente a assinatura de trilha para outro 30 dias. Para um ambiente de desenvolvimento e teste permanente, crie uma nova assinatura com um pequeno número de licenças paga. 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>Fase 3: Atribuir licenças do Dynamics 365 e administradores do sistema

Nesta fase, você pode atribuir licenças do Dynamics 365 o administrador global, o usuário 2 e contas de usuário 3 e torná-los aos administradores de sistema.
  
Use estas etapas para atribuir licenças do Dynamics 365.
  
1. Na guia do **Centro de administração do Office** , clique em **usuários > usuários ativos**.
    
2. Na lista de usuários ativos, clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.
    
3. No painel de **licenças do produto** , ativar a licença do produto para **Dynamics 365 planejar 1 Enterprise Edition** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .
    
4. Execute as etapas 2 e 3 para as contas de usuário 2 e 3 do usuário.
    
5. Feche a guia do **Centro de administração do Office** .
    
Use estas etapas para configurar as contas de usuário 2 e 3 do usuário como os administradores de sistema do Dynamics 365.
  
1. Na guia **Página inicial do Microsoft Office** , clique em **Admin**.
    
2. Na guia **Centro de administração do Office** , no painel de navegação esquerdo, clique em **Admin centrais**e clique em **Dynamics 365**.
    
    Você pode precisar aguardar Dynamics 365 concluir o provisionamento antes do Dynamics 365 aparece no menu.
    
3. Na guia Dynamics 365, clique em **todos esses**e, em seguida, clique em **Concluir a instalação.**
    
    Aguarde concluir a instalação.
    
    Quando terminar a instalação, ele exibe um painel de atividade de vendas com base nos dados de amostra que faz parte da assinatura trilha. Levar alguns momentos para exibir o **Bem-vindo à sua avaliação** vídeo. Feche a janela de vídeo quando tiver concluído.
    
4. Na barra de ferramentas na parte superior, clique na seta ao lado de **vendas**, clique em **configurações**e, em seguida, clique em **segurança**.
    
5. Na página **segurança** , clique em **usuários**.
    
6. Na lista de usuários, clique em **usuário 2**.
    
7. Na barra de ferramentas, clique em **Gerenciar funções**.
    
8. Em **Gerenciar funções**, clique em **Administrador do sistema**e, em seguida, clique em **Okey**.
    
9. Na barra de ferramentas na parte superior, clique em **segurança**.
    
10. Repita as etapas 5 a 8 para a conta de usuário 3.
    
11. Fechar o **usuário: User3** guia.
    
> [!NOTE]
> Sua conta de administrador global do Office 365 foi atribuída automaticamente a função de administrador de sistema do Dynamics 365. 
  
Seu ambiente de desenvolvimento e teste do Office 365 e Dynamics 365 agora tem:
  
- O Office 365 E5 Enterprise e Dynamics 365 assinaturas de avaliação da mesma organização e o mesmo inquilino do Azure AD de compartilhamento com sua lista de contas de usuário.
    
- Seu administrador corporativo global, o usuário 2 e contas de usuário 3 estão habilitadas para usar o Office 365 E5 Enterprise e Dynamics 365 e são administradores de sistema do Dynamics 365.
    
## <a name="next-step"></a>Próxima etapa

Configurar e, em seguida, demonstre como Office 365 e Dynamics 365 trabalham juntos caixas de correio no Exchange Online com [integração com o Exchange Online para o seu ambiente de desenvolvimento e teste do Office 365 e Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).
  
## <a name="see-also"></a>Veja também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento e teste de configuração de base](base-configuration-dev-test-environment.md)
  
[Ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)

[Gerenciamento de assinatura do Dynamics 365 (online)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Administrando o Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


