---
title: "Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "Resumo: Configurar e demonstrar a segurança de aplicativo de nuvem do Office 365 em seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: 8d398dcbf1ca5dea5ee790a64829eef55765025a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365

 **Resumo:** Configurar e demonstrar a segurança de aplicativo de nuvem do Office 365 em seu ambiente de desenvolvimento e teste do Office 365.
  
Segurança de aplicativo do Office 365 nuvem, anteriormente conhecido como o Office 365 gerenciamento avançado de segurança, permite que você crie diretivas que monitoram e informam atividades suspeitas em sua assinatura do Office 365, para que você possa investigar e levar possíveis ação de remediação. Para obter mais informações, consulte [Visão geral da segurança nuvem de App no Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
  
Com as instruções deste artigo, você pode habilitar e testar a segurança do aplicativo de nuvem em sua assinatura de avaliação do Office 365.
  
> [!TIP]
> Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>Fase 1: Desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada

Se você deseja testar a segurança do aplicativo de nuvem de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Se você deseja testar a segurança do aplicativo de nuvem em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).
  
> [!NOTE]
> Testando nuvem a segurança do aplicativo não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa testar a segurança do aplicativo de nuvem e experimentar em um ambiente que representa uma organização típica. 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>Fase 2: antes habilitando a segurança de aplicativo de nuvem e criando uma política

Neste procedimento, você demonstrar que antes de habilitar a segurança de aplicativo de nuvem, alterando a uma função do usuário não fornece nenhuma notificação por e-mail para o administrador global.
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Testar o comportamento de notificação padrão do Office 365

1. Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
  - Se você estiver usando o ambiente de desenvolvimento e teste leve do Office 365, entre usando o computador local.
    
  - Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, use o [portal Azure](https://portal.azure.com) para conectar a máquina virtual CLIENT1 e entrar em CLIENT1.
    
2. Na página principal do portal, clique em **Admin**.
    
3. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
4. Clique na conta de **usuário 4** .
    
5. Na página **4 de usuário** , clique em **Editar** para a linha de **funções** .
    
6. Na página **Editar funções do usuário** , clique em **Administrador Global**, digite **user4@contoso.com** no **endereço de email alternativo**e, em seguida, clique em **Salvar**. Clique duas vezes em **Fechar** .
    
7. Selecione o ícone do iniciador de app no canto superior esquerdo e escolha o **email**.
    
8. Aguarde 30 minutos. Observe que não há nenhuma mensagem de email na caixa de entrada informando sobre a alteração na função do usuário 4 como um administrador global.
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>Fase 3: Habilite a segurança de aplicativo de nuvem e criar uma política

Neste procedimento, habilite a segurança de aplicativo de nuvem e criar uma nova política para enviar notificações por email para sua conta de administrador global para que as alterações nas funções da conta de usuário. Esse procedimento requer:
  
- O nome da conta de administrador global e a senha da sua assinatura de teste do Office 365.
    
- O nome e a senha da conta do Usuário 5 da sua assinatura de teste do Office 365.
    
### <a name="enable-and-configure-cloud-app-security"></a>Habilitar e configurar a segurança de aplicativo de nuvem

1. Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.
    
2. Clique no **segurança &amp; conformidade** lado a lado.
    
3. No painel de navegação à esquerda, clique em **alertas > Gerenciar avançadas alertas**.
    
4. Na página **Gerenciar alertas de avançadas** , clique em **Ativar de segurança de aplicativo de nuvem do Office 365**e, em seguida, clique em **Ir para segurança de aplicativo de nuvem do Office 365**.
    
5. Na guia nova **painel** , clique em **controle > políticas**.
    
6. Na página **política** , clique em **Criar política**e clique em **política de atividade**.
    
7. Em **nome da política**, digite **atividades administrativas**.
    
8. Na **gravidade da política**, clique em **alta**.
    
9. Em **categoria**, clique em **contas privilegiadas**.
    
10. Em **criar filtros para a política**, em **atividades correspondência das ações a seguir**, clique em **atividades administrativas**.
    
11. Em **alertas**, clique em **Enviar alerta como email**. Na caixa **para**, digite o endereço de email da sua conta de administrador global.
    
12. Na parte inferior da página, clique em **criar**.
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>Fase 4: Segurança de aplicativo de nuvem Mostrar em ação

Neste procedimento, você demonstrar como a segurança de aplicativo de nuvem cria alertas e envia notificações por email para a conta de administrador global, quando o usuário 4 torna 5 de usuário de um administrador de gerenciamento de usuário e senha.
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>Demonstrar a notificação por email para uma alteração em funções de conta de usuário

1. No canto superior direito, clique no ícone de usuário e, em seguida, clique em **Sair**.
    
2. Vá para [https://portal.office.com](https://portal.office.com).
    
3. Na página de entrada da Office 365, clique em **usar outra conta**.
    
4. Digite o nome da conta de usuário 4 e sua senha e clique em **entrar**.
    
5. Se necessário, altere a senha da conta de usuário 4 e clique em **Atualizar senha e entrar**.
    
6. Na página do portal do Office 365, clique em **Admin**.
    
7. Se necessário, clique em **Cancelar** quando solicitado a atualizar suas informações de contato do administrador.
    
8. Na página principal do portal, clique em **Admin**.
    
9. Na navegação à esquerda, clique em **Usuários > Usuários ativos**.
    
10. Clique na conta de **usuário 5** .
    
11. Na página de **5 de usuário** , clique em **Editar** para a linha de **funções** .
    
12. Na página **Editar funções do usuário** , clique em **administrador personalizado**, clique em **administrador de senha** e o **administrador de gerenciamento de usuário**, digite **user5@contoso.com** o **endereço de email alternativo**e, em seguida, clique em **Salvar**. Clique duas vezes em **Fechar** .
    
13. Clique no ícone de usuário no canto superior direito e clique em **Sair**. 
    
14. Vá para [https://portal.office.com](https://portal.office.com).
    
15. Na página do **Office 365 entrar** , clique em seu nome de conta de administrador global.
    
16. Digite a senha e clique em **entrar**.
    
17. Na página principal do portal, clique em **Admin**.
    
18. Clique no **segurança &amp; conformidade** lado a lado.
    
19. No painel de navegação à esquerda, clique em **alertas > Gerenciar avançadas alertas**.
    
20. Na página **Gerenciar alertas de avançadas** , clique em **Ir para segurança de aplicativo de nuvem do Office 365**.
    
21. Na guia nova **painel** , observe os dois novos alertas para **atividades administrativas**.
    
22. Na guia **Página inicial do Microsoft Office** , clique em **email**. Aguarde até 30 minutos. 
    
    Você deverá ver duas novas mensagens de email na caixa de entrada com o **Serviço de notificação do Microsoft Azure AD**de título. Uma mensagem indica que a conta de usuário 5 foi adicionada à função de **Administrador de senha** e outra mensagem indica que a conta de usuário 5 foi adicionada à função de **Administrador do usuário** (igual a função de administrador de gerenciamento de usuário, no Centro de administração do Office 365).
    
Agora você pode usar esse ambiente para criar novas políticas e experimentar ainda mais a segurança de aplicativo de nuvem do Office 365. Para obter links para artigos de configuração adicionais, consulte [Prepare-se para a segurança de aplicativo de nuvem do Office 365](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .
  
## <a name="see-also"></a>Veja também

[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)

[Visão geral da segurança do aplicativo de nuvem no Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


