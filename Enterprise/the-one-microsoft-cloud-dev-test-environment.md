---
title: Ambiente de desenvolvimento/teste do One Microsoft Cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: 'Resumo: use este guia de laboratório de teste para criar um ambiente de desenvolvimento/teste que inclui todas as ofertas da nuvem da Microsoft.'
ms.openlocfilehash: b8ffd01c9d129d4537c82f0e1f74bd7c1be1388b
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037945"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>Ambiente de desenvolvimento/teste do One Microsoft Cloud

 **Resumo:** use este guia de laboratório de teste para criar um ambiente de desenvolvimento/teste que inclui todas as ofertas da nuvem da Microsoft.
  
Com as instruções neste artigo, crie uma intranet simulada nos serviços de infraestrutura do Microsoft Azure e, em seguida, adicione as assinaturas do Microsoft Office 365, do Microsoft Enterprise Mobility + Security (EMS) e do Microsoft Dynamics 365. O resultado é uma organização simplificada que usa todas as ofertas da nuvem da Microsoft ao mesmo tempo em um único ambiente de desenvolvimento/teste. 
  
![Fase 3 do ambiente de desenvolvimento/teste do One Microsoft Cloud com o Azure, Office 365, EMS e Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
Você pode usar a configuração resultante para:
  
- Experimentar a integração entre as ofertas da nuvem da Microsoft, como a infraestrutura de identidades comuns fornecida pelo Azure Active Directory (AD).
    
- Avaliar cenários de ponta a ponta que incluem várias ofertas do Microsoft Cloud.
    
- Criar uma demonstração, verificação de conceito ou configuração de desenvolvimento/teste que usa várias ofertas do Microsoft Cloud.
    
- Desenvolva suas habilidades no Microsoft Cloud para desenvolvimento profissional.
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>Fase 1: Criar uma intranet simulada e adicionar o Office 365

Siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
A Figura 1 mostra a configuração resultante, que inclui o Office 365 e uma intranet simulada em execução em serviços de infraestrutura do Azure e a sincronização de diretórios de uma floresta no local do AD DS (Active Directory Domain Services).
  
**Figura 1: A intranet simulada no Azure com o Office 365**

![O ambiente de desenvolvimento/teste do Office 365 com o DirSync](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> A avaliação do Azure é de 30 dias. A assinatura de avaliação do Office 365 Enterprise E5 é de 30 dias, que podem ser facilmente estendidos por mais 30 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga do Azure e uma nova assinatura paga do Office 365 Enterprise E5 com algumas licenças. 
  
## <a name="phase-2-add-ems"></a>Fase 2: Adicionar o EMS

Nesta fase, inscreva-se para a assinatura de avaliação do EMS e adicione-a à mesma organização de sua assinatura de avaliação do Office 365.
  
1. Com um navegador em seu computador desktop ou no CLIENT1, entre no portal do Office 365 em [https://www.office.com](https://www.office.com) com as credenciais de sua conta de administrador global.
    
2. Clique no bloco de **Administração**.
    
3. Na guia **Centro de Administração do Office** no navegador, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.
    
4. Na página **Comprar serviços**, encontre o item **Enterprise Mobility + Security E5**. Passe o ponteiro do mouse sobre ele e clique em **Iniciar avaliação gratuita**.
    
5. Na página **Confirmar seu pedido**, clique em **Experimentar agora**.
    
6. Na página **Recibo do pedido**, clique em **Continuar**.
    
> [!NOTE]
> A assinatura de avaliação do Enterprise Mobility + Security E5 dura 90 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com uma pequena quantidade de licenças. 
  
Em seguida, habilite a licença do Enterprise Mobility + Security E5 para todas as contas de usuários.
  
1. Na guia **Centro de administração do Office 365** do navegador, no painel de navegação esquerdo, clique em **Usuários > Usuários ativos**.
    
2. Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **Licenças de produto**.
    
3. No painel **Licenças de produto**, mude a licença de produto de **Enterprise Mobility + Security E5** para **Ativada**, clique em **Salvar** e clique em **Fechar** duas vezes.
    
4. Para todas as outras contas (Usuário1, Usuário 2, Usuário 3, Usuário 4 e Usuário 5), execute as etapas 2 e 3.
    
Seu ambiente de desenvolvimento/teste agora tem:
  
- A intranet simulada em execução nos serviços de infraestrutura do Azure.
    
- Assinaturas de avaliação do Office 365 Enterprise E5 e do EMS que compartilham a mesma organização e o mesmo locatário do Azure AD com sua lista de contas de usuário.
    
- Todas as suas contas de usuário habilitadas para usar o Office 365 E5 Enterprise e o EMS.
    
A Figura 2 mostra a configuração resultante, que adiciona o EMS.
  
**Figura 2: A intranet simulada no Azure com o Office 365 e o EMS**

![Fase 2 do ambiente de desenvolvimento/teste do One Microsoft Cloud com o Azure, Office 365 e EMS](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>Fase 3: Adicionar o Dynamics 365

Nesta fase, inscreva-se para receber a assinatura de avaliação do Dynamics 365 e adicione-a à mesma organização de suas assinaturas de avaliação do Office 365 e do EMS.
  
1. Usando um navegador em seu computador desktop ou no CLIENT1, entre no portal do Office 365 em [https://www.office.com](https://www.office.com) com as credenciais de sua conta de administrador global.
    
2. Clique no bloco de **Administração**.
    
3. Na guia **centro de administração do Microsoft 365**, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.
    
4. Na página **Comprar serviços**, encontre o item **Dynamics 365 Plan 1 Enterprise Edition**. Passe o ponteiro do mouse sobre ele e clique em **Iniciar avaliação gratuita**.
    
5. Na página **Confirmar seu pedido**, clique em **Experimentar agora**.
    
6. Na página **Recibo do pedido**, clique em **Continuar**.
    
> [!NOTE]
> A assinatura de avaliação do Dynamics 365 Plan 1 Enterprise Edition é de 30 dias, que podem ser facilmente estendidos por mais 30 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com algumas licenças. 
  
Use estas etapas para atribuir licenças do Dynamics 365 às contas do administrador global, do Usuário 2 e do Usuário 3 e para torná-los administradores do sistema.
  
1. Na guia **centro de administração do Microsoft 365**, clique em **Usuários > Usuários Ativos**.
    
2. Na lista de usuários ativos, clique em sua conta de administrador global e depois em **Editar** para **Licenças de produto**.
    
3. No painel **Licenças de produto**, mude a licença de produto de **Dynamics 365 Plan 1 Enterprise Edition** para **Ativada**, clique em **Salvar** e clique em **Fechar** duas vezes.
    
4. Siga as etapas 2 e 3 para as contas dos Usuários 2 e 3.
    
5. Feche a guia do **centro de administração do Microsoft 365**.
    
Use estas etapas para configurar as contas dos Usuários 2 e 3 como administradores de sistema do Dynamics 365.
  
1. Na guia **centro de administração do Office** no navegador, no painel de navegação esquerdo, clique em **Centros de administração** e depois em **Dynamics 365**.
    
    Talvez seja necessário aguardar que o Dynamics 365 conclua o provisionamento antes que seja exibido no menu.
    
2. Na guia Dynamics 365, clique em **Todos Esses**e depois em **Concluir Instalação.**
    
    Aguarde que a instalação seja concluída.
    
    Ao concluir a instalação, ele exibe o Painel de atividades de vendas com base nos dados de exemplo que fazem parte da assinatura de avaliação. Aproveite para ver o vídeo **Bem-vindo à sua avaliação**. Feche a janela do vídeo após a conclusão.
    
3. Na barra superior, clique na seta para baixo ao lado de **Vendas**, clique em **Configurações**e em **Segurança**.
    
4. Na página **Segurança**, clique em **Usuários**.
    
5. Na lista de usuários, clique em **Usuário 2**.
    
6. Na barra de ferramentas, clique em **Gerenciar Funções**.
    
7. Em **Gerenciar Funções**, clique em **Administrador do Sistema**e em **OK**.
    
8. Na barra de ferramentas superior clique em **Segurança**.
    
9. Repita as etapas de 5 a 8 para a conta do Usuário 3.
    
10. Feche a guia **Usuário: Usuário3**.
    
> [!NOTE]
> A função de administrador do sistema do Dynamics 365 foi atribuída automaticamente pela sua conta de administrador global do Office 365. 
  
Seu ambiente de desenvolvimento/teste agora tem:
  
- A intranet simulada em execução nos serviços de infraestrutura do Azure.
    
- As assinaturas de avaliação do Office 365 Enterprise E5, do EMS e do Dynamics 365 compartilham a mesma organização e o mesmo locatário do Azure AD com a sua lista de contas de usuários.
    
- Todas as suas contas de usuário habilitadas para usar o Office 365 E5 Enterprise e o EMS.
    
- As contas do administrador global da empresa, do Usuário 2 e do Usuário 3 estão habilitadas para usarem o Dynamics 365 e são os administradores do sistema do Dynamics 365.
    
A Figura 3 mostra a configuração resultante.
  
**Figura 3: A intranet simulada no Azure com o Office 365, o EMS e o Dynamics 365**

![Fase 3 do ambiente de desenvolvimento/teste do One Microsoft Cloud com o Azure, Office 365, EMS e Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>Próximas etapas

Agora você pode experimentar seu ambiente de desenvolvimento/teste do One Microsoft Cloud. Aqui estão algumas ideias para experiências guiadas:
  
- [Configurar políticas do gerenciamento de aplicativo móvel (MAM) no EMS para aplicativos do Office 365](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Demonstrar o Exchange Online em integração do Office 365 com contatos do Dynamics 365](https://technet.microsoft.com/library/mt798313.aspx)
    
- [Criar uma rede simulada entre locais nos serviços de infraestrutura Azure para hospedar cargas de trabalho baseadas em servidor](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>Confira também


[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Soluções híbridas](hybrid-solutions.md)
  
[Soluções de segurança](security-solutions.md)





