---
title: Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: 'Resumo: Use este guia de laboratório de teste para adicionar Dynamics 365 ao seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: ccf0615befe2ba74f85177dc252516f685655ed6
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="b4cf6-103">Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b4cf6-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="b4cf6-104">**Resumo:** Use este guia de laboratório de teste para adicionar Dynamics 365 ao seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="b4cf6-105">Com as instruções deste artigo, você adiciona uma assinatura de avaliação do Dynamics 365 à mesma organização que seu ambiente de desenvolvimento e teste do Office 365, criação de um ambiente de desenvolvimento e teste do Office 365 e Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
<span data-ttu-id="b4cf6-p101">Você pode usar uma assinatura de avaliação do Dynamics 365 para demonstrar os recursos e capacidades do Dynamics 365. As seguintes soluções estão incluídas com uma Dynamics 365 plano 1, Enterprise Edition de avaliação:</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="b4cf6-p102">O [Microsoft Dynamics 365 de vendas](https://www.microsoft.com/dynamics365/sales). Aumente suas vendas com automação e digital intelligence ajudando seus vendedores manter o foco e trabalhar de forma mais inteligente.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="b4cf6-p103">O [Microsoft Dynamics 365 para atendimento ao cliente](https://www.microsoft.com/dynamics365/customer-service). Ganhe fidelidade, dando a seus agentes as informações completas e inteligência digital que precisam fornecer serviço contínuo.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="b4cf6-p104">O [Microsoft Dynamics 365 para o serviço de campo](https://www.microsoft.com/dynamics365/field-service). A chamada de serviço do mestre otimizando as agendas, equipando sua força de trabalho e usando ferramentas de previsão para aumentar o lucro.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="b4cf6-p105">O [Microsoft Dynamics 365 para automação de serviço do projeto](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Conclua a seus projetos com êxito e criar relacionamentos lucrativos com funcionários produtivos e ferramentas inteligentes.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="b4cf6-116">Você pode explorar uma ou mais das perguntas acima para sua assinatura de avaliação do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-116">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Guias do Laboratório de Teste da Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="b4cf6-118">Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="b4cf6-119">Fase 1: Desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="b4cf6-119">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="b4cf6-120">Se você quiser testar o Office 365 e Dynamics 365 de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf6-120">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="b4cf6-121">Se você quiser testar o Office 365 e Dynamics 365 para uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf6-121">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="b4cf6-p106">A configuração neste artigo não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você pode experimentar com o Office 365 e Dynamics 365 em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="b4cf6-124">Fase 2: Adicionar uma assinatura de avaliação do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b4cf6-124">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="b4cf6-125">Nesta fase, inscreva-se para a assinatura de avaliação do Dynamics 365 e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-125">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="b4cf6-126">Inscreva-se para uma assinatura de avaliação do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b4cf6-126">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="b4cf6-127">Usando um navegador em um computador desktop (lightweight) ou CLIENT1 (simulados enterprise), entrar no portal do Office 365 em [https://portal.office.com](https://portal.office.com) com as credenciais da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-127">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="b4cf6-128">Clique no bloco de **Administração**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-128">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="b4cf6-129">Na guia **Centro de administração do Office** , no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-129">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="b4cf6-p107">Na página **Serviços de compra** , encontre o item **Dynamics 365 planejar 1 Enterprise Edition** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="b4cf6-132">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-132">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="b4cf6-133">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-133">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="b4cf6-p108">A assinatura de avaliação do Dynamics 365 planejar 1 Enterprise Edition é 30 dias. Você pode estender facilmente a assinatura de trilha para outro 30 dias. Para um ambiente de desenvolvimento e teste permanente, crie uma nova assinatura com um pequeno número de licenças paga.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="b4cf6-137">Fase 3: Atribuir licenças do Dynamics 365 e administradores do sistema</span><span class="sxs-lookup"><span data-stu-id="b4cf6-137">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="b4cf6-138">Nesta fase, você pode atribuir licenças do Dynamics 365 o administrador global, o usuário 2 e contas de usuário 3 e torná-los aos administradores de sistema.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-138">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="b4cf6-139">Use estas etapas para atribuir licenças do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-139">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="b4cf6-140">Na guia do **Centro de administração do Office** , clique em **usuários > usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-140">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="b4cf6-141">Na lista de usuários ativos, clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-141">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="b4cf6-142">No painel de **licenças do produto** , ativar a licença do produto para **Dynamics 365 planejar 1 Enterprise Edition** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="b4cf6-142">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="b4cf6-143">Execute as etapas 2 e 3 para as contas de usuário 2 e 3 do usuário.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-143">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="b4cf6-144">Feche a guia do **Centro de administração do Office** .</span><span class="sxs-lookup"><span data-stu-id="b4cf6-144">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="b4cf6-145">Use estas etapas para configurar as contas de usuário 2 e 3 do usuário como os administradores de sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-145">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="b4cf6-146">Na guia **Página inicial do Microsoft Office** , clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-146">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="b4cf6-147">Na guia **Centro de administração do Office** , no painel de navegação esquerdo, clique em **Admin centrais**e clique em **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-147">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="b4cf6-148">Você pode precisar aguardar Dynamics 365 concluir o provisionamento antes do Dynamics 365 aparece no menu.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-148">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="b4cf6-149">Na guia Dynamics 365, clique em **todos esses**e, em seguida, clique em **Concluir a instalação.**</span><span class="sxs-lookup"><span data-stu-id="b4cf6-149">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="b4cf6-150">Aguarde concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-150">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="b4cf6-p109">Quando terminar a instalação, ele exibe um painel de atividade de vendas com base nos dados de amostra que faz parte da assinatura trilha. Levar alguns momentos para exibir o **Bem-vindo à sua avaliação** vídeo. Feche a janela de vídeo quando tiver concluído.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="b4cf6-154">Na barra de ferramentas na parte superior, clique na seta ao lado de **vendas**, clique em **configurações**e, em seguida, clique em **segurança**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-154">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="b4cf6-155">Na página **segurança** , clique em **usuários**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-155">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="b4cf6-156">Na lista de usuários, clique em **usuário 2**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-156">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="b4cf6-157">Na barra de ferramentas, clique em **Gerenciar funções**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-157">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="b4cf6-158">Em **Gerenciar funções**, clique em **Administrador do sistema**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-158">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="b4cf6-159">Na barra de ferramentas na parte superior, clique em **segurança**.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-159">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="b4cf6-160">Repita as etapas 5 a 8 para a conta de usuário 3.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-160">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="b4cf6-161">Fechar o **usuário: User3** guia.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-161">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="b4cf6-162">Sua conta de administrador global do Office 365 foi atribuída automaticamente a função de administrador de sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-162">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="b4cf6-163">Seu ambiente de desenvolvimento e teste do Office 365 e Dynamics 365 agora tem:</span><span class="sxs-lookup"><span data-stu-id="b4cf6-163">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="b4cf6-164">O Office 365 E5 Enterprise e Dynamics 365 assinaturas de avaliação da mesma organização e o mesmo inquilino do Azure AD de compartilhamento com sua lista de contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-164">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="b4cf6-165">Seu administrador corporativo global, o usuário 2 e contas de usuário 3 estão habilitadas para usar o Office 365 E5 Enterprise e Dynamics 365 e são administradores de sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="b4cf6-165">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="b4cf6-166">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="b4cf6-166">Next step</span></span>

<span data-ttu-id="b4cf6-167">Configurar e, em seguida, demonstre como Office 365 e Dynamics 365 trabalham juntos caixas de correio no Exchange Online com [integração com o Exchange Online para o seu ambiente de desenvolvimento e teste do Office 365 e Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf6-167">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b4cf6-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="b4cf6-168">See Also</span></span>

[<span data-ttu-id="b4cf6-169">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="b4cf6-169">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
<span data-ttu-id="b4cf6-170">[O ambiente de desenvolvimento e teste de configuração base](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="b4cf6-170">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="b4cf6-171">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="b4cf6-171">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="b4cf6-172">DirSync para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="b4cf6-172">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="b4cf6-173">Gerenciamento de assinatura do Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="b4cf6-173">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="b4cf6-174">Administrando o Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b4cf6-174">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


