---
title: Ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Resumo: use este Guia do Laboratório de Teste para adicionar o Dynamics 365 a seu ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: 9e4c98129c68ab5d2f0d9fc486ab62740c625af5
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574055"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365

 **Resumo:** use este Guia do Laboratório de Teste para adicionar o Dynamics 365 a seu ambiente de desenvolvimento/teste do Office 365.
  
Usando as instruções deste artigo, adicione uma assinatura de avaliação do Dynamics 365 à mesma organização de seu ambiente de desenvolvimento/teste do Office 365, criando um ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365.

![Ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365](media/o365-dynamics365-dev-test.png)
  
  
Você pode usar uma assinatura de avaliação do Dynamics 365 para demonstrar recursos e funcionalidades do Dynamics 365. As seguintes soluções estão incluídas no Plano 1 do Dynamics 365, avaliação da Edição Empresarial:
  
- [Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Aumente suas vendas com automação e inteligência digital ajudar os vendedores a manter a concentração e trabalhar melhor.
    
- [Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Conquiste a fidelidade fornecendo a seus agentes as informações completas e a inteligência digital de que eles precisam para fornecer o serviço perfeito.
    
- [Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Domine a chamada de serviço otimizando seus cronogramas, equipando sua força de trabalho e usando ferramentas preventivas para aumentar o lucro.
    
- [Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/pt-BR/dynamics365/project-service-automation). Conclua seus projetos com êxito e crie relações lucrativas com funcionários produtivos e ferramentas inteligentes.
    
Você pode explorar uma ou mais das opções acima para sua assinatura de avaliação do Dynamics 365.
  
![Guias do Laboratório de Teste da Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada

Se você apenas deseja testar o Office 365 e o Dynamics 365 de modo leve, com requisitos mínimos, siga as instruções das fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).
  
Se deseja testar o Office 365 e o Dynamics 365 para uma empresa simulada, siga as instruções do [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).

![O ambiente de desenvolvimento/teste do Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> A configuração neste artigo não requer o ambiente de desenvolvimento/teste em uma empresa simulada, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do AD no Windows Server. Ela é fornecida aqui como uma opção para que você possa fazer testes com o Office 365 e o Dynamics 365 em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>Fase 2: adicionar uma assinatura de avaliação do Dynamics 365

Nesta fase, inscreva-se para receber a assinatura de avaliação do Dynamics 365 e a adicione à mesma organização de sua assinatura de avaliação do Office 365.
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>Adicionar uma assinatura de avaliação do Dynamics 365

1. Usando um navegador em seu computador desktop (leve) ou no CLIENT1 (empresa simulada), entre no centro de administração do Microsoft 365 em [https://admin.microsoft.com](https://admin.microsoft.com) com as credenciais da sua conta de administrador global.
    
2. Clique no bloco de **Administração**.
    
3. Na guia **centro de administração do Microsoft 365**, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.
    
4. Na página **Comprar serviços**, encontre o item **Dynamics 365 Plan 1 Enterprise Edition**. Passe o ponteiro do mouse sobre ele e clique em **Iniciar avaliação gratuita**.
    
5. Na página **Confirmar seu pedido**, clique em **Experimentar agora**.
    
6. Na página **Recibo do pedido**, clique em **Continuar**.

![Ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> A assinatura de avaliação do Dynamics 365 Plan 1 Enterprise Edition é de 30 dias, que podem ser facilmente estendidos por mais 30 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com algumas licenças. 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>Fase 3: atribuir licenças do Dynamics 365 e administradores do sistema

Nesta fase, você atribui licenças do Dynamics 365 às contas do administrador global, do Usuário 2 e do Usuário 3 e os torna administradores do sistema.
  
Use estas etapas para atribuir licenças do Dynamics 365.
  
1. Na guia **centro de administração do Microsoft 365**, clique em **Usuários > Usuários Ativos**.
    
2. Na lista de usuários ativos, clique em sua conta de administrador global e depois em **Editar** para **Licenças de produto**.
    
3. No painel **Licenças de produto**, mude a licença de produto de **Dynamics 365 Plan 1 Enterprise Edition** para **Ativada**, clique em **Salvar** e clique em **Fechar** duas vezes.
    
4. Siga as etapas 2 e 3 para as contas dos Usuários 2 e 3.
    
5. Feche a guia do **centro de administração do Microsoft 365**.
    
Use estas etapas para configurar as contas dos Usuários 2 e 3 como administradores de sistema do Dynamics 365.
  
1. Na guia **Microsoft Office Home**, clique em **Administração**.
    
2. Na guia **centro de administração do Office** no painel de navegação esquerdo, clique em **Centros de administração** e depois em **Dynamics 365**.
    
    Talvez seja necessário aguardar o Dynamics 365 concluir o provisionamento antes que o Dynamics 365 seja exibido no menu.
    
3. Na guia Dynamics 365, clique em **Todos Esses**e depois em **Concluir Instalação.**
    
    Aguarde que a instalação seja concluída.
    
    Ao concluir a instalação, ele exibe o Painel de atividades de vendas com base nos dados de exemplo que fazem parte da assinatura de avaliação. Aproveite para ver o vídeo **Bem-vindo à sua avaliação** vídeo. Feche a janela do vídeo após a conclusão.
    
4. Na barra superior, clique na seta para baixo ao lado de **Vendas**, clique em **Configurações**e em **Segurança**.
    
5. Na página **Segurança**, clique em **Usuários**.
    
6. Na lista de usuários, clique em **Usuário 2**.
    
7. Na barra de ferramentas, clique em **Gerenciar Funções**.
    
8. Em **Gerenciar Funções**, clique em **Administrador do Sistema**e em **OK**.
    
9. Na barra de ferramentas superior clique em **Segurança**.
    
10. Repita as etapas de 5 a 8 para a conta do Usuário 3.
    
11. Feche a guia **Usuário: Usuário3**.
    
> [!NOTE]
> A função de administrador do sistema do Dynamics 365 foi atribuída automaticamente pela sua conta de administrador global do Office 365. 
  
Seu o ambiente de desenvolvimento/teste do Office 365 e Dynamics 365 tem agora:
  
- As assinaturas de avaliação do Office 365 Enterprise E5 e do Dynamics 365 compartilhando a mesma organização e o mesmo locatário do Azure AD com a sua lista de contas de usuários.
    
- As contas do administrador global da empresa, do Usuário 2 e do Usuário 3 estão habilitadas para usarem tanto o Office 365 E5 Enterprise quanto o Dynamics 365, e são administradoras do sistema do Dynamics 365.
    
## <a name="next-step"></a>Próxima etapa

Configure e demonstre como o Office 365 e o Dynamics 365 trabalham em conjunto em caixas de correio do Exchange Online com [integração com o Exchange Online para seu ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).
  
## <a name="see-also"></a>Confira também


[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) 
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[DirSync para o ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)

[Gerenciamento de assinaturas do Dynamics 365 (online)](https://technet.microsoft.com/library/jj679903.aspx)
  
[Administração do Dynamics 365](https://technet.microsoft.com/library/dn531101.aspx)


