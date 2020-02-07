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
f1.keywords:
- CSH
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: 'Resumo: Configure e demonstre o Office 365 Cloud app Security no seu ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: a4f0f9e8912a5455ec5253e9992873136e71d694
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840798"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="644e3-103">Segurança de Aplicativo na Nuvem para o ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="644e3-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="644e3-104">**Resumo:** Configure e demonstre o Office 365 Cloud app Security no seu ambiente de desenvolvimento/teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="644e3-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="644e3-105">O Office 365 Cloud app Security, anteriormente conhecido como gerenciamento de segurança avançada do Office 365, permite que você crie políticas que monitoram e informam sobre atividades suspeitas em sua assinatura do Office 365, para que você possa investigar e realizar a possível correção ação.</span><span class="sxs-lookup"><span data-stu-id="644e3-105">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action.</span></span> <span data-ttu-id="644e3-106">Para obter mais informações, consulte [Overview of Cloud app Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span><span class="sxs-lookup"><span data-stu-id="644e3-106">For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="644e3-107">Com as instruções deste artigo, você habilita e testa o Cloud app Security na sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="644e3-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="644e3-108">Clique [aqui](https://aka.ms/catlgstack) para exibir um mapa visual de todos os artigos da pilha da Guia do Laboratório de Teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="644e3-108">Click [here](https://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="644e3-109">Fase 1: desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="644e3-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="644e3-110">Se você só quiser testar o Cloud app Security de uma maneira leve com os requisitos mínimos, siga as instruções nas fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="644e3-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="644e3-111">Se você quiser testar o Cloud app Security em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="644e3-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="644e3-112">O teste do Cloud app Security não exige o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta dos serviços de domínio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="644e3-112">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="644e3-113">Ele é fornecido aqui como uma opção para que você possa testar a segurança do Cloud app e experimentá-lo em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="644e3-113">It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="644e3-114">Fase 2: antes de habilitar o Cloud app Security e criar uma política</span><span class="sxs-lookup"><span data-stu-id="644e3-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="644e3-115">Neste procedimento, você demonstra que antes de habilitar o Cloud app Security, alterar a função de um usuário não fornece nenhuma notificação por email para o administrador global.</span><span class="sxs-lookup"><span data-stu-id="644e3-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="644e3-116">Testar o comportamento de notificação padrão do Office 365</span><span class="sxs-lookup"><span data-stu-id="644e3-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="644e3-117">Vá para o centro de administração do Microsoft[https://admin.microsoft.com](https://admin.microsoft.com)365 () e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="644e3-117">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="644e3-118">Se você estiver usando o ambiente leve de desenvolvimento/teste do Office 365, entre no computador local.</span><span class="sxs-lookup"><span data-stu-id="644e3-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="644e3-119">Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, use o [portal do Azure](https://portal.azure.com) para se conectar à máquina virtual do CLIENT1 e, em seguida, entre no CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="644e3-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="644e3-120">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="644e3-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="644e3-121">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="644e3-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="644e3-122">Clique na conta do **usuário 4** .</span><span class="sxs-lookup"><span data-stu-id="644e3-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="644e3-123">Na página **usuário 4** , clique em **Editar** para a linha **funções** .</span><span class="sxs-lookup"><span data-stu-id="644e3-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="644e3-124">Na página **Editar funções de usuário** , clique em **Administrador Global**, digite **User4@contoso.com** no **endereço de email alternativo**e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="644e3-124">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**.</span></span> <span data-ttu-id="644e3-125">Clique em **fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="644e3-125">Click **Close** twice.</span></span>
    
7. <span data-ttu-id="644e3-126">Selecione o ícone do inicializador de aplicativos no canto superior esquerdo e escolha **email**.</span><span class="sxs-lookup"><span data-stu-id="644e3-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="644e3-127">Aguarde 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="644e3-127">Wait 30 minutes.</span></span> <span data-ttu-id="644e3-128">Observe que não há mensagens de email na caixa de entrada, notificando-o sobre a alteração na função do usuário 4 como administrador global.</span><span class="sxs-lookup"><span data-stu-id="644e3-128">Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="644e3-129">Fase 3: habilitar o Cloud app Security e criar uma política</span><span class="sxs-lookup"><span data-stu-id="644e3-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="644e3-130">Neste procedimento, você habilitará o Cloud app Security e criará uma nova política para enviar notificações por email à sua conta de administrador global para alterações nas funções de conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="644e3-130">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles.</span></span> <span data-ttu-id="644e3-131">Este procedimento requer:</span><span class="sxs-lookup"><span data-stu-id="644e3-131">This procedure requires:</span></span>
  
- <span data-ttu-id="644e3-132">O nome da conta de administrador global e a senha da sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="644e3-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="644e3-133">O nome e a senha da conta do usuário 5 da sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="644e3-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="644e3-134">Habilitar e configurar o Cloud app Security</span><span class="sxs-lookup"><span data-stu-id="644e3-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="644e3-135">Vá para o centro de administração do Microsoft[https://admin.microsoft.com](https://admin.microsoft.com)365 () e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="644e3-135">Go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="644e3-136">Clique no bloco de **Administração**.</span><span class="sxs-lookup"><span data-stu-id="644e3-136">Click the **Admin** tile.</span></span> <span data-ttu-id="644e3-137">Na guia **centro de administração do Office** , clique em **centros de administração > segurança & conformidade**.</span><span class="sxs-lookup"><span data-stu-id="644e3-137">On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="644e3-138">No painel de navegação esquerdo, clique em **alertas > Gerenciar alertas avançados**.</span><span class="sxs-lookup"><span data-stu-id="644e3-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="644e3-139">Na página **Gerenciar alertas avançados** , clique em **ativar o Office 365 Cloud app Security**e clique em **ir para o Office 365 Cloud app Security**.</span><span class="sxs-lookup"><span data-stu-id="644e3-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="644e3-140">Na guia novo **painel** , clique em **controlar > políticas**.</span><span class="sxs-lookup"><span data-stu-id="644e3-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="644e3-141">Na página **política** , clique em **criar política**e em política de **atividade**.</span><span class="sxs-lookup"><span data-stu-id="644e3-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="644e3-142">Em **nome da política**, digite **atividade administrativa**.</span><span class="sxs-lookup"><span data-stu-id="644e3-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="644e3-143">Em **severidade da política**, clique em **alto**.</span><span class="sxs-lookup"><span data-stu-id="644e3-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="644e3-144">Em **categoria**, clique em **contas privilegiadas**.</span><span class="sxs-lookup"><span data-stu-id="644e3-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="644e3-145">Em **criar filtros para a política**, em **atividades que correspondem a todos os itens a seguir**, clique em **atividades administrativas**.</span><span class="sxs-lookup"><span data-stu-id="644e3-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="644e3-146">Em **alertas**, clique em **Enviar alerta como email**.</span><span class="sxs-lookup"><span data-stu-id="644e3-146">In **Alerts**, click **Send alert as email**.</span></span> <span data-ttu-id="644e3-147">Em **para**, digite o endereço de email da conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="644e3-147">In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="644e3-148">Na parte inferior da página, clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="644e3-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="644e3-149">Fase 4: mostrar a segurança do aplicativo na nuvem em ação</span><span class="sxs-lookup"><span data-stu-id="644e3-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="644e3-150">Neste procedimento, você demonstrará como o Cloud app Security cria alertas e envia notificações por email à conta de administrador global quando o usuário 4 torna o usuário 5 um administrador de senha e de gerenciamento de usuários.</span><span class="sxs-lookup"><span data-stu-id="644e3-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="644e3-151">Demonstrar a notificação por email para uma alteração nas funções da conta do usuário</span><span class="sxs-lookup"><span data-stu-id="644e3-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="644e3-152">No canto superior direito **, clique no**ícone usuário e, em seguida, clique em sair.</span><span class="sxs-lookup"><span data-stu-id="644e3-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="644e3-153">Acesse [https://www.office.com](https://www.office.com).</span><span class="sxs-lookup"><span data-stu-id="644e3-153">Go to [https://www.office.com](https://www.office.com).</span></span>
    
3. <span data-ttu-id="644e3-154">Na página de entrada do Office 365, clique em **usar outra conta**.</span><span class="sxs-lookup"><span data-stu-id="644e3-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="644e3-155">Digite o nome da conta do usuário 4 e sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="644e3-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="644e3-156">Se necessário, altere a senha da conta do usuário 4 e clique em **Atualizar senha e entrar**.</span><span class="sxs-lookup"><span data-stu-id="644e3-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="644e3-157">Na página do portal do Office 365, clique em **administrador**.</span><span class="sxs-lookup"><span data-stu-id="644e3-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="644e3-158">Se necessário, clique em **Cancelar** quando solicitado a atualizar suas informações de contato de administrador.</span><span class="sxs-lookup"><span data-stu-id="644e3-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="644e3-159">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="644e3-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="644e3-160">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="644e3-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="644e3-161">Clique na conta do **usuário 5** .</span><span class="sxs-lookup"><span data-stu-id="644e3-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="644e3-162">Na página **usuário 5** , clique em **Editar** para a linha **funções** .</span><span class="sxs-lookup"><span data-stu-id="644e3-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="644e3-163">Na página **Editar funções de usuário** , clique em **administrador personalizado**, clique em administrador de **Gerenciamento de usuário**e administrador de **senha** , digite **User5@contoso.com** no **endereço de email alternativo**e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="644e3-163">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**.</span></span> <span data-ttu-id="644e3-164">Clique em **fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="644e3-164">Click **Close** twice.</span></span>
    
13. <span data-ttu-id="644e3-165">Clique no ícone de usuário no canto superior direito e clique em sair **.**</span><span class="sxs-lookup"><span data-stu-id="644e3-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="644e3-166">Acesse [https://www.office.com](https://www.office.com).</span><span class="sxs-lookup"><span data-stu-id="644e3-166">Go to [https://www.office.com](https://www.office.com).</span></span>
    
15. <span data-ttu-id="644e3-167">Na página de **entrada do Office 365** , clique no nome da conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="644e3-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="644e3-168">Digite a senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="644e3-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="644e3-169">Na página do portal do Office 365, clique em **administrador**.</span><span class="sxs-lookup"><span data-stu-id="644e3-169">From the Office 365 portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="644e3-170">Clique no **bloco &amp; conformidade de segurança** .</span><span class="sxs-lookup"><span data-stu-id="644e3-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="644e3-171">No painel de navegação esquerdo, clique em **alertas > Gerenciar alertas avançados**.</span><span class="sxs-lookup"><span data-stu-id="644e3-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="644e3-172">Na página **Gerenciar alertas avançados** , clique em **ir para o Office 365 Cloud app Security**.</span><span class="sxs-lookup"><span data-stu-id="644e3-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="644e3-173">Na guia novo **painel** , observe os dois novos alertas de **atividades administrativas**.</span><span class="sxs-lookup"><span data-stu-id="644e3-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="644e3-174">Na guia **Microsoft Office Home** , clique em **email**.</span><span class="sxs-lookup"><span data-stu-id="644e3-174">From the **Microsoft Office Home** tab, click **Mail**.</span></span> <span data-ttu-id="644e3-175">Aguarde até 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="644e3-175">Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="644e3-176">Você deve ver duas novas mensagens de email na caixa de entrada com o título **Microsoft Azure ad Notification Service**.</span><span class="sxs-lookup"><span data-stu-id="644e3-176">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**.</span></span> <span data-ttu-id="644e3-177">Uma mensagem indica que a conta do usuário 5 foi adicionada à função de **administrador de senha** e outra mensagem indica que a conta do usuário 5 foi adicionada à função de **administrador de usuários** (igual à função Administrador de gerenciamento de usuários no centro de administração do Microsoft 365).</span><span class="sxs-lookup"><span data-stu-id="644e3-177">One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Microsoft 365 admin center).</span></span>
    
<span data-ttu-id="644e3-178">Agora você pode usar esse ambiente para criar novas políticas e experimentar mais com o Office 365 Cloud app Security.</span><span class="sxs-lookup"><span data-stu-id="644e3-178">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security.</span></span> <span data-ttu-id="644e3-179">Consulte preparar [para o Office 365 Cloud app Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) para obter links para artigos de configuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="644e3-179">See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="644e3-180">Confira também</span><span class="sxs-lookup"><span data-stu-id="644e3-180">See Also</span></span>

[<span data-ttu-id="644e3-181">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="644e3-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="644e3-182">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="644e3-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="644e3-183">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="644e3-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="644e3-184">Visão geral do Cloud app Security no Office 365</span><span class="sxs-lookup"><span data-stu-id="644e3-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


