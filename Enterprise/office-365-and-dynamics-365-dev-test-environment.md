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
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="75625-103">Ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="75625-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="75625-104">**Resumo:** use este Guia do Laboratório de Teste para adicionar o Dynamics 365 a seu ambiente de desenvolvimento/teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="75625-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="75625-105">Usando as instruções deste artigo, adicione uma assinatura de avaliação do Dynamics 365 à mesma organização de seu ambiente de desenvolvimento/teste do Office 365, criando um ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="75625-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="75625-p101">Você pode usar uma assinatura de avaliação do Dynamics 365 para demonstrar recursos e funcionalidades do Dynamics 365. As seguintes soluções estão incluídas no Plano 1 do Dynamics 365, avaliação da Edição Empresarial:</span><span class="sxs-lookup"><span data-stu-id="75625-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="75625-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Aumente suas vendas com automação e inteligência digital ajudar os vendedores a manter a concentração e trabalhar melhor.</span><span class="sxs-lookup"><span data-stu-id="75625-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="75625-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Conquiste a fidelidade fornecendo a seus agentes as informações completas e a inteligência digital de que eles precisam para fornecer o serviço perfeito.</span><span class="sxs-lookup"><span data-stu-id="75625-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="75625-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Domine a chamada de serviço otimizando seus cronogramas, equipando sua força de trabalho e usando ferramentas preventivas para aumentar o lucro.</span><span class="sxs-lookup"><span data-stu-id="75625-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="75625-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/pt-BR/dynamics365/project-service-automation). Conclua seus projetos com êxito e crie relações lucrativas com funcionários produtivos e ferramentas inteligentes.</span><span class="sxs-lookup"><span data-stu-id="75625-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/pt-BR/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="75625-117">Você pode explorar uma ou mais das opções acima para sua assinatura de avaliação do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="75625-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Guias do Laboratório de Teste da Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="75625-119">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="75625-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="75625-120">Fase 1: desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="75625-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="75625-121">Se você apenas deseja testar o Office 365 e o Dynamics 365 de modo leve, com requisitos mínimos, siga as instruções das fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="75625-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="75625-122">Se deseja testar o Office 365 e o Dynamics 365 para uma empresa simulada, siga as instruções do [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="75625-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![O ambiente de desenvolvimento/teste do Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="75625-p106">A configuração neste artigo não requer o ambiente de desenvolvimento/teste em uma empresa simulada, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do AD no Windows Server. Ela é fornecida aqui como uma opção para que você possa fazer testes com o Office 365 e o Dynamics 365 em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="75625-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="75625-126">Fase 2: adicionar uma assinatura de avaliação do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="75625-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="75625-127">Nesta fase, inscreva-se para receber a assinatura de avaliação do Dynamics 365 e a adicione à mesma organização de sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="75625-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="75625-128">Adicionar uma assinatura de avaliação do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="75625-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="75625-129">Usando um navegador em seu computador desktop (leve) ou no CLIENT1 (empresa simulada), entre no centro de administração do Microsoft 365 em [https://admin.microsoft.com](https://admin.microsoft.com) com as credenciais da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="75625-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://admin.microsoft.com](https://admin.microsoft.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="75625-130">Clique no bloco de **Administração**.</span><span class="sxs-lookup"><span data-stu-id="75625-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="75625-131">Na guia **centro de administração do Microsoft 365**, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.</span><span class="sxs-lookup"><span data-stu-id="75625-131">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="75625-p107">Na página **Comprar serviços**, encontre o item **Dynamics 365 Plan 1 Enterprise Edition**. Passe o ponteiro do mouse sobre ele e clique em **Iniciar avaliação gratuita**.</span><span class="sxs-lookup"><span data-stu-id="75625-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="75625-134">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="75625-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="75625-135">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="75625-135">On the **Order receipt** page, click **Continue**.</span></span>

![Ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="75625-p108">A assinatura de avaliação do Dynamics 365 Plan 1 Enterprise Edition é de 30 dias, que podem ser facilmente estendidos por mais 30 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com algumas licenças.</span><span class="sxs-lookup"><span data-stu-id="75625-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="75625-140">Fase 3: atribuir licenças do Dynamics 365 e administradores do sistema</span><span class="sxs-lookup"><span data-stu-id="75625-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="75625-141">Nesta fase, você atribui licenças do Dynamics 365 às contas do administrador global, do Usuário 2 e do Usuário 3 e os torna administradores do sistema.</span><span class="sxs-lookup"><span data-stu-id="75625-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="75625-142">Use estas etapas para atribuir licenças do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="75625-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="75625-143">Na guia **centro de administração do Microsoft 365**, clique em **Usuários > Usuários Ativos**.</span><span class="sxs-lookup"><span data-stu-id="75625-143">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="75625-144">Na lista de usuários ativos, clique em sua conta de administrador global e depois em **Editar** para **Licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="75625-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="75625-145">No painel **Licenças de produto**, mude a licença de produto de **Dynamics 365 Plan 1 Enterprise Edition** para **Ativada**, clique em **Salvar** e clique em **Fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="75625-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="75625-146">Siga as etapas 2 e 3 para as contas dos Usuários 2 e 3.</span><span class="sxs-lookup"><span data-stu-id="75625-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="75625-147">Feche a guia do **centro de administração do Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="75625-147">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="75625-148">Use estas etapas para configurar as contas dos Usuários 2 e 3 como administradores de sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="75625-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="75625-149">Na guia **Microsoft Office Home**, clique em **Administração**.</span><span class="sxs-lookup"><span data-stu-id="75625-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="75625-150">Na guia **centro de administração do Office** no painel de navegação esquerdo, clique em **Centros de administração** e depois em **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="75625-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="75625-151">Talvez seja necessário aguardar o Dynamics 365 concluir o provisionamento antes que o Dynamics 365 seja exibido no menu.</span><span class="sxs-lookup"><span data-stu-id="75625-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="75625-152">Na guia Dynamics 365, clique em **Todos Esses**e depois em **Concluir Instalação.**</span><span class="sxs-lookup"><span data-stu-id="75625-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="75625-153">Aguarde que a instalação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="75625-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="75625-p109">Ao concluir a instalação, ele exibe o Painel de atividades de vendas com base nos dados de exemplo que fazem parte da assinatura de avaliação. Aproveite para ver o vídeo **Bem-vindo à sua avaliação** vídeo. Feche a janela do vídeo após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="75625-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="75625-157">Na barra superior, clique na seta para baixo ao lado de **Vendas**, clique em **Configurações**e em **Segurança**.</span><span class="sxs-lookup"><span data-stu-id="75625-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="75625-158">Na página **Segurança**, clique em **Usuários**.</span><span class="sxs-lookup"><span data-stu-id="75625-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="75625-159">Na lista de usuários, clique em **Usuário 2**.</span><span class="sxs-lookup"><span data-stu-id="75625-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="75625-160">Na barra de ferramentas, clique em **Gerenciar Funções**.</span><span class="sxs-lookup"><span data-stu-id="75625-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="75625-161">Em **Gerenciar Funções**, clique em **Administrador do Sistema**e em **OK**.</span><span class="sxs-lookup"><span data-stu-id="75625-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="75625-162">Na barra de ferramentas superior clique em **Segurança**.</span><span class="sxs-lookup"><span data-stu-id="75625-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="75625-163">Repita as etapas de 5 a 8 para a conta do Usuário 3.</span><span class="sxs-lookup"><span data-stu-id="75625-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="75625-164">Feche a guia **Usuário: Usuário3**.</span><span class="sxs-lookup"><span data-stu-id="75625-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="75625-165">A função de administrador do sistema do Dynamics 365 foi atribuída automaticamente pela sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="75625-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="75625-166">Seu o ambiente de desenvolvimento/teste do Office 365 e Dynamics 365 tem agora:</span><span class="sxs-lookup"><span data-stu-id="75625-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="75625-167">As assinaturas de avaliação do Office 365 Enterprise E5 e do Dynamics 365 compartilhando a mesma organização e o mesmo locatário do Azure AD com a sua lista de contas de usuários.</span><span class="sxs-lookup"><span data-stu-id="75625-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="75625-168">As contas do administrador global da empresa, do Usuário 2 e do Usuário 3 estão habilitadas para usarem tanto o Office 365 E5 Enterprise quanto o Dynamics 365, e são administradoras do sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="75625-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="75625-169">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="75625-169">Next step</span></span>

<span data-ttu-id="75625-170">Configure e demonstre como o Office 365 e o Dynamics 365 trabalham em conjunto em caixas de correio do Exchange Online com [integração com o Exchange Online para seu ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span><span class="sxs-lookup"><span data-stu-id="75625-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="75625-171">Confira também
</span><span class="sxs-lookup"><span data-stu-id="75625-171">See Also</span></span>

[<span data-ttu-id="75625-172">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="75625-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
<span data-ttu-id="75625-173">[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="75625-173">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="75625-174">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="75625-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="75625-175">DirSync para o ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="75625-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="75625-176">Gerenciamento de assinaturas do Dynamics 365 (online)</span><span class="sxs-lookup"><span data-stu-id="75625-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="75625-177">Administração do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="75625-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


