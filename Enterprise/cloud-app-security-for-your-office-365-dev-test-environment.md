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
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "Resumo: Configurar e demonstrar a segurança de aplicativo de nuvem do Office 365 em seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: 1fab5ebfd6e0670ba59fe34b2cca8a7282e75723
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="a773e-103">Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="a773e-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="a773e-104">**Resumo:** Configurar e demonstrar a segurança de aplicativo de nuvem do Office 365 em seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a773e-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="a773e-p101">Segurança de aplicativo do Office 365 nuvem, anteriormente conhecido como o Office 365 gerenciamento avançado de segurança, permite que você crie diretivas que monitoram e informam atividades suspeitas em sua assinatura do Office 365, para que você possa investigar e levar possíveis ação de remediação. Para obter mais informações, consulte [Visão geral da segurança nuvem de App no Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="a773e-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, allows you to create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="a773e-107">Com as instruções deste artigo, você pode habilitar e testar a segurança do aplicativo de nuvem em sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a773e-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="a773e-108">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="a773e-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="a773e-109">Fase 1: Desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="a773e-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="a773e-110">Se você deseja testar a segurança do aplicativo de nuvem de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a773e-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="a773e-111">Se você deseja testar a segurança do aplicativo de nuvem em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a773e-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="a773e-p102">Testando nuvem a segurança do aplicativo não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa testar a segurança do aplicativo de nuvem e experimentar em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="a773e-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="a773e-114">Fase 2: antes habilitando a segurança de aplicativo de nuvem e criando uma política</span><span class="sxs-lookup"><span data-stu-id="a773e-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="a773e-115">Neste procedimento, você demonstrar que antes de habilitar a segurança de aplicativo de nuvem, alterando a uma função do usuário não fornece nenhuma notificação por e-mail para o administrador global.</span><span class="sxs-lookup"><span data-stu-id="a773e-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="a773e-116">Testar o comportamento de notificação padrão do Office 365</span><span class="sxs-lookup"><span data-stu-id="a773e-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="a773e-117">Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a773e-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="a773e-118">Se você estiver usando o ambiente de desenvolvimento e teste leve do Office 365, entre usando o computador local.</span><span class="sxs-lookup"><span data-stu-id="a773e-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="a773e-119">Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, use o [portal Azure](https://portal.azure.com) para conectar a máquina virtual CLIENT1 e entrar em CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="a773e-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="a773e-120">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="a773e-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="a773e-121">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="a773e-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="a773e-122">Clique na conta de **usuário 4** .</span><span class="sxs-lookup"><span data-stu-id="a773e-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="a773e-123">Na página **4 de usuário** , clique em **Editar** para a linha de **funções** .</span><span class="sxs-lookup"><span data-stu-id="a773e-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="a773e-p103">Na página **Editar funções do usuário** , clique em **Administrador Global**, digite **user4@contoso.com** no **endereço de email alternativo**e, em seguida, clique em **Salvar**. Clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="a773e-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="a773e-126">Selecione o ícone do iniciador de app no canto superior esquerdo e escolha o **email**.</span><span class="sxs-lookup"><span data-stu-id="a773e-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="a773e-p104">Aguarde 30 minutos. Observe que não há nenhuma mensagem de email na caixa de entrada informando sobre a alteração na função do usuário 4 como um administrador global.</span><span class="sxs-lookup"><span data-stu-id="a773e-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="a773e-129">Fase 3: Habilite a segurança de aplicativo de nuvem e criar uma política</span><span class="sxs-lookup"><span data-stu-id="a773e-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="a773e-p105">Neste procedimento, habilite a segurança de aplicativo de nuvem e criar uma nova política para enviar notificações por email para sua conta de administrador global para que as alterações nas funções da conta de usuário. Esse procedimento requer:</span><span class="sxs-lookup"><span data-stu-id="a773e-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="a773e-132">O nome da conta de administrador global e a senha da sua assinatura de teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a773e-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="a773e-133">O nome e a senha da conta do Usuário 5 da sua assinatura de teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a773e-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="a773e-134">Habilitar e configurar a segurança de aplicativo de nuvem</span><span class="sxs-lookup"><span data-stu-id="a773e-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="a773e-135">Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a773e-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="a773e-136">Clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="a773e-136">Click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="a773e-137">No painel de navegação à esquerda, clique em **alertas > Gerenciar avançadas alertas**.</span><span class="sxs-lookup"><span data-stu-id="a773e-137">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="a773e-138">Na página **Gerenciar alertas de avançadas** , clique em **Ativar de segurança de aplicativo de nuvem do Office 365**e, em seguida, clique em **Ir para segurança de aplicativo de nuvem do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="a773e-138">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="a773e-139">Na guia nova **painel** , clique em **controle > políticas**.</span><span class="sxs-lookup"><span data-stu-id="a773e-139">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="a773e-140">Na página **política** , clique em **Criar política**e clique em **política de atividade**.</span><span class="sxs-lookup"><span data-stu-id="a773e-140">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="a773e-141">Em **nome da política**, digite **atividades administrativas**.</span><span class="sxs-lookup"><span data-stu-id="a773e-141">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="a773e-142">Na **gravidade da política**, clique em **alta**.</span><span class="sxs-lookup"><span data-stu-id="a773e-142">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="a773e-143">Em **categoria**, clique em **contas privilegiadas**.</span><span class="sxs-lookup"><span data-stu-id="a773e-143">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="a773e-144">Em **criar filtros para a política**, em **atividades correspondência das ações a seguir**, clique em **atividades administrativas**.</span><span class="sxs-lookup"><span data-stu-id="a773e-144">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="a773e-p106">Em **alertas**, clique em **Enviar alerta como email**. Na caixa **para**, digite o endereço de email da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a773e-p106">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="a773e-147">Na parte inferior da página, clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="a773e-147">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="a773e-148">Fase 4: Segurança de aplicativo de nuvem Mostrar em ação</span><span class="sxs-lookup"><span data-stu-id="a773e-148">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="a773e-149">Neste procedimento, você demonstrar como a segurança de aplicativo de nuvem cria alertas e envia notificações por email para a conta de administrador global, quando o usuário 4 torna 5 de usuário de um administrador de gerenciamento de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="a773e-149">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="a773e-150">Demonstrar a notificação por email para uma alteração em funções de conta de usuário</span><span class="sxs-lookup"><span data-stu-id="a773e-150">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="a773e-151">No canto superior direito, clique no ícone de usuário e, em seguida, clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="a773e-151">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="a773e-152">Vá para [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="a773e-152">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="a773e-153">Na página de entrada da Office 365, clique em **usar outra conta**.</span><span class="sxs-lookup"><span data-stu-id="a773e-153">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="a773e-154">Digite o nome da conta de usuário 4 e sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="a773e-154">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="a773e-155">Se necessário, altere a senha da conta de usuário 4 e clique em **Atualizar senha e entrar**.</span><span class="sxs-lookup"><span data-stu-id="a773e-155">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="a773e-156">Na página do portal do Office 365, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="a773e-156">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="a773e-157">Se necessário, clique em **Cancelar** quando solicitado a atualizar suas informações de contato do administrador.</span><span class="sxs-lookup"><span data-stu-id="a773e-157">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="a773e-158">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="a773e-158">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="a773e-159">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="a773e-159">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="a773e-160">Clique na conta de **usuário 5** .</span><span class="sxs-lookup"><span data-stu-id="a773e-160">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="a773e-161">Na página de **5 de usuário** , clique em **Editar** para a linha de **funções** .</span><span class="sxs-lookup"><span data-stu-id="a773e-161">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="a773e-p107">Na página **Editar funções do usuário** , clique em **administrador personalizado**, clique em **administrador de senha** e o **administrador de gerenciamento de usuário**, digite **user5@contoso.com** o **endereço de email alternativo**e, em seguida, clique em **Salvar**. Clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="a773e-p107">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="a773e-164">Clique no ícone de usuário no canto superior direito e clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="a773e-164">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="a773e-165">Vá para [https://portal.office.com](https://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="a773e-165">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="a773e-166">Na página do **Office 365 entrar** , clique em seu nome de conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a773e-166">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="a773e-167">Digite a senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="a773e-167">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="a773e-168">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="a773e-168">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="a773e-169">Clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="a773e-169">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="a773e-170">No painel de navegação à esquerda, clique em **alertas > Gerenciar avançadas alertas**.</span><span class="sxs-lookup"><span data-stu-id="a773e-170">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="a773e-171">Na página **Gerenciar alertas de avançadas** , clique em **Ir para segurança de aplicativo de nuvem do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="a773e-171">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="a773e-172">Na guia nova **painel** , observe os dois novos alertas para **atividades administrativas**.</span><span class="sxs-lookup"><span data-stu-id="a773e-172">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="a773e-p108">Na guia **Página inicial do Microsoft Office** , clique em **email**. Aguarde até 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="a773e-p108">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="a773e-p109">Você deverá ver duas novas mensagens de email na caixa de entrada com o **Serviço de notificação do Microsoft Azure AD**de título. Uma mensagem indica que a conta de usuário 5 foi adicionada à função de **Administrador de senha** e outra mensagem indica que a conta de usuário 5 foi adicionada à função de **Administrador do usuário** (igual a função de administrador de gerenciamento de usuário, no Centro de administração do Office 365).</span><span class="sxs-lookup"><span data-stu-id="a773e-p109">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="a773e-p110">Agora você pode usar esse ambiente para criar novas políticas e experimentar ainda mais a segurança de aplicativo de nuvem do Office 365. Para obter links para artigos de configuração adicionais, consulte [Prepare-se para a segurança de aplicativo de nuvem do Office 365](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) .</span><span class="sxs-lookup"><span data-stu-id="a773e-p110">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a773e-179">See Also</span><span class="sxs-lookup"><span data-stu-id="a773e-179">See Also</span></span>

[<span data-ttu-id="a773e-180">Adoção de nuvem Test Lab Guides (TLGs)</span><span class="sxs-lookup"><span data-stu-id="a773e-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a773e-181">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="a773e-181">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="a773e-182">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="a773e-182">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="a773e-183">Visão geral da segurança do aplicativo de nuvem no Office 365</span><span class="sxs-lookup"><span data-stu-id="a773e-183">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


