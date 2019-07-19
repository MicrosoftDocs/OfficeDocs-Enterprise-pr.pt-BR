---
title: Segurança de Aplicativo na Nuvem para o ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Resumo: Configure e demonstre o Office 365 Cloud app Security no seu ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: 1b20f4dc98c23c2063d77703f157a31889c69e6c
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782251"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Segurança de Aplicativo na Nuvem para o ambiente de desenvolvimento/teste do Office 365

 **Resumo:** Configure e demonstre o Office 365 Cloud app Security no seu ambiente de desenvolvimento/teste do Office 365.
  
O Office 365 Cloud app Security, anteriormente conhecido como gerenciamento de segurança avançada do Office 365, permite que você crie políticas que monitoram e informam sobre atividades suspeitas em sua assinatura do Office 365, para que você possa investigar e realizar a possível correção ação. Para obter mais informações, consulte [Overview of Cloud app Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
  
Com as instruções deste artigo, você habilita e testa o Cloud app Security na sua assinatura de avaliação do Office 365.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual de todos os artigos da pilha da Guia do Laboratório de Teste do Office 365.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada

Se você só quiser testar o Cloud app Security de uma maneira leve com os requisitos mínimos, siga as instruções nas fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).
  
Se você quiser testar o Cloud app Security em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> O teste do Cloud app Security não exige o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta dos serviços de domínio Active Directory (AD DS). Ele é fornecido aqui como uma opção para que você possa testar a segurança do Cloud app e experimentá-lo em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Fase 2: antes de habilitar o Cloud app Security e criar uma política

Neste procedimento, você demonstra que antes de habilitar o Cloud app Security, alterar a função de um usuário não fornece nenhuma notificação por email para o administrador global.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Testar o comportamento de notificação padrão do Office 365

1. Vá para o centro de administração do Microsoft[https://admin.microsoft.com](https://admin.microsoft.com)365 () e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
  - Se você estiver usando o ambiente leve de desenvolvimento/teste do Office 365, entre no computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, use o [portal do Azure](https://portal.azure.com) para se conectar à máquina virtual do CLIENT1 e, em seguida, entre no CLIENT1.
    
2. Na página principal do portal, clique em **Admin**.
    
3. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
4. Clique na conta do **usuário 4** .
    
5. Na página **usuário 4** , clique em **Editar** para a linha **funções** .
    
6. Na página **Editar funções de usuário** , clique em **Administrador Global**, digite **User4@contoso.com** no **endereço de email alternativo**e clique em **salvar**. Clique em **fechar** duas vezes.
    
7. Selecione o ícone do inicializador de aplicativos no canto superior esquerdo e escolha **email**.
    
8. Aguarde 30 minutos. Observe que não há mensagens de email na caixa de entrada, notificando-o sobre a alteração na função do usuário 4 como administrador global.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Fase 3: habilitar o Cloud app Security e criar uma política

Neste procedimento, você habilitará o Cloud app Security e criará uma nova política para enviar notificações por email à sua conta de administrador global para alterações nas funções de conta de usuário. Este procedimento requer:
  
- O nome da conta de administrador global e a senha da sua assinatura de avaliação do Office 365.
    
- O nome e a senha da conta do usuário 5 da sua assinatura de avaliação do Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Habilitar e configurar o Cloud app Security

1. Vá para o centro de administração do Microsoft[https://admin.microsoft.com](https://admin.microsoft.com)365 () e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
2. Clique no bloco de **Administração**. Na guia **centro de administração do Office** , clique em **centros de administração > segurança & conformidade**.
    
3. No painel de navegação esquerdo, clique em **alertas > Gerenciar alertas avançados**.
    
4. Na página **Gerenciar alertas avançados** , clique em **ativar o Office 365 Cloud app Security**e clique em **ir para o Office 365 Cloud app Security**.
    
5. Na guia novo **painel** , clique em **controlar > políticas**.
    
6. Na página **política** , clique em **criar política**e em política de **atividade**.
    
7. Em **nome da política**, digite **atividade administrativa**.
    
8. Em **severidade da política**, clique em **alto**.
    
9. Em **categoria**, clique em **contas privilegiadas**.
    
10. Em **criar filtros para a política**, em **atividades que correspondem a todos os itens a seguir**, clique em **atividades administrativas**.
    
11. Em **alertas**, clique em **Enviar alerta como email**. Em **para**, digite o endereço de email da conta de administrador global.
    
12. Na parte inferior da página, clique em **criar**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Fase 4: mostrar a segurança do aplicativo na nuvem em ação

Neste procedimento, você demonstrará como o Cloud app Security cria alertas e envia notificações por email à conta de administrador global quando o usuário 4 torna o usuário 5 um administrador de senha e de gerenciamento de usuários.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Demonstrar a notificação por email para uma alteração nas funções da conta do usuário

1. No canto superior direito, clique no ícone usuário e, em seguida, **** clique em sair.
    
2. Acesse [https://www.office.com](https://www.office.com).
    
3. Na página de entrada do Office 365, clique em **usar outra conta**.
    
4. Digite o nome da conta do usuário 4 e sua senha e clique em **entrar**.
    
5. Se necessário, altere a senha da conta do usuário 4 e clique em **Atualizar senha e entrar**.
    
6. Na página do portal do Office 365, clique em **administrador**.
    
7. Se necessário, clique em **Cancelar** quando solicitado a atualizar suas informações de contato de administrador.
    
8. Na página principal do portal, clique em **Admin**.
    
9. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
10. Clique na conta do **usuário 5** .
    
11. Na página **usuário 5** , clique em **Editar** para a linha **funções** .
    
12. Na página **Editar funções de usuário** , clique em **administrador personalizado**, clique em administrador de **Gerenciamento de usuário**e administrador de **senha** , digite **User5@contoso.com** no **endereço de email alternativo**e clique em **Salvar**. Clique em **fechar** duas vezes.
    
13. Clique no ícone de usuário no canto superior direito e clique em sair ****. 
    
14. Acesse [https://www.office.com](https://www.office.com).
    
15. Na página de **entrada do Office 365** , clique no nome da conta de administrador global.
    
16. Digite a senha e clique em **entrar**.
    
17. Na página do portal do Office 365, clique em **administrador**.
    
18. Clique no **bloco &amp; conformidade de segurança** .
    
19. No painel de navegação esquerdo, clique em **alertas > Gerenciar alertas avançados**.
    
20. Na página **Gerenciar alertas avançados** , clique em **ir para o Office 365 Cloud app Security**.
    
21. Na guia novo **painel** , observe os dois novos alertas de **atividades administrativas**.
    
22. Na guia **Microsoft Office Home** , clique em **email**. Aguarde até 30 minutos. 
    
    Você deve ver duas novas mensagens de email na caixa de entrada com o título **Microsoft Azure ad Notification Service**. Uma mensagem indica que a conta do usuário 5 foi adicionada à função de **administrador de senha** e outra mensagem indica que a conta do usuário 5 foi adicionada à função de **administrador de usuários** (igual à função Administrador de gerenciamento de usuários no Centro de administração do Microsoft 365).
    
Agora você pode usar esse ambiente para criar novas políticas e experimentar mais com o Office 365 Cloud app Security. Consulte preparar [para o Office 365 Cloud app Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) para obter links para artigos de configuração adicionais.
  
## <a name="see-also"></a>Confira também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Visão geral do Cloud app Security no Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


