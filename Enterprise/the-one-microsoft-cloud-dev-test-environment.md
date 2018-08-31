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
ms.openlocfilehash: e5391b88a964261ad0698890bbb5c99866fbb57d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915626"
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="f284e-103">Ambiente de desenvolvimento/teste do One Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f284e-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="f284e-104">**Resumo:** use este guia de laboratório de teste para criar um ambiente de desenvolvimento/teste que inclui todas as ofertas da nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f284e-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="f284e-p101">Com as instruções neste artigo, crie uma intranet simulada nos serviços de infraestrutura do Microsoft Azure e, em seguida, adicione as assinaturas do Microsoft Office 365, do Microsoft Enterprise Mobility + Security (EMS) e do Microsoft Dynamics 365. O resultado é uma organização simplificada que usa todas as ofertas da nuvem da Microsoft ao mesmo tempo em um único ambiente de desenvolvimento/teste.</span><span class="sxs-lookup"><span data-stu-id="f284e-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Fase 3 do ambiente de desenvolvimento/teste do One Microsoft Cloud com o Azure, Office 365, EMS e Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="f284e-108">Você pode usar a configuração resultante para:</span><span class="sxs-lookup"><span data-stu-id="f284e-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="f284e-109">Experimentar a integração entre as ofertas da nuvem da Microsoft, como a infraestrutura de identidades comuns fornecida pelo Azure Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="f284e-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="f284e-110">Avaliar cenários de ponta a ponta que incluem várias ofertas do Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="f284e-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="f284e-111">Criar uma demonstração, verificação de conceito ou configuração de desenvolvimento/teste que usa várias ofertas do Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="f284e-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="f284e-112">Desenvolva suas habilidades no Microsoft Cloud para desenvolvimento profissional.</span><span class="sxs-lookup"><span data-stu-id="f284e-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="f284e-113">Fase 1: Criar uma intranet simulada e adicionar o Office 365</span><span class="sxs-lookup"><span data-stu-id="f284e-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="f284e-114">Siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="f284e-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="f284e-115">A Figura 1 mostra a configuração resultante, que inclui o Office 365 e uma intranet simulada em execução em serviços de infraestrutura do Azure e a sincronização de diretórios de uma floresta no local do Windows Server Active Directory (AD).</span><span class="sxs-lookup"><span data-stu-id="f284e-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="f284e-116">**Figura 1: A intranet simulada no Azure com o Office 365**</span><span class="sxs-lookup"><span data-stu-id="f284e-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![O ambiente de desenvolvimento/teste do Office 365 com o DirSync](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="f284e-p102">A avaliação do Azure é de 30 dias. A assinatura de avaliação do Office 365 Enterprise E5 é de 30 dias, que podem ser facilmente estendidos por mais 30 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga do Azure e uma nova assinatura paga do Office 365 Enterprise E5 com algumas licenças.</span><span class="sxs-lookup"><span data-stu-id="f284e-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="f284e-121">Fase 2: Adicionar o EMS</span><span class="sxs-lookup"><span data-stu-id="f284e-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="f284e-122">Nesta fase, inscreva-se para a assinatura de avaliação do EMS e adicione-a à mesma organização de sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="f284e-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="f284e-123">Com um navegador em seu computador desktop ou no CLIENT1, entre no portal do Office 365 em [https://portal.office.com](https://portal.office.com) com as credenciais de sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f284e-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="f284e-124">Clique no bloco de **Administração**.</span><span class="sxs-lookup"><span data-stu-id="f284e-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="f284e-125">Na guia **Centro de Administração do Office** no navegador, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.</span><span class="sxs-lookup"><span data-stu-id="f284e-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="f284e-p103">Na página **Comprar serviços**, encontre o item **Enterprise Mobility + Security E5**. Passe o ponteiro do mouse sobre ele e clique em **Iniciar avaliação gratuita**.</span><span class="sxs-lookup"><span data-stu-id="f284e-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="f284e-128">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="f284e-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="f284e-129">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="f284e-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f284e-p104">A assinatura de avaliação do Enterprise Mobility + Security E5 dura 90 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com uma pequena quantidade de licenças.</span><span class="sxs-lookup"><span data-stu-id="f284e-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="f284e-132">Em seguida, habilite a licença do Enterprise Mobility + Security E5 para todas as contas de usuários.</span><span class="sxs-lookup"><span data-stu-id="f284e-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="f284e-133">Na guia **Centro de administração do Office 365** do navegador, no painel de navegação esquerdo, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="f284e-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="f284e-134">Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **Licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="f284e-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="f284e-135">No painel **Licenças de produto**, mude a licença de produto de **Enterprise Mobility + Security E5** para **Ativada**, clique em **Salvar** e clique em **Fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="f284e-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="f284e-136">Para todas as outras contas (Usuário1, Usuário 2, Usuário 3, Usuário 4 e Usuário 5), execute as etapas 2 e 3.</span><span class="sxs-lookup"><span data-stu-id="f284e-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="f284e-137">Seu ambiente de desenvolvimento/teste agora tem:</span><span class="sxs-lookup"><span data-stu-id="f284e-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="f284e-138">A intranet simulada em execução nos serviços de infraestrutura do Azure.</span><span class="sxs-lookup"><span data-stu-id="f284e-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="f284e-139">Assinaturas de avaliação do Office 365 Enterprise E5 e do EMS que compartilham a mesma organização e o mesmo locatário do Azure AD com sua lista de contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="f284e-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="f284e-140">Todas as suas contas de usuário habilitadas para usar o Office 365 E5 Enterprise e o EMS.</span><span class="sxs-lookup"><span data-stu-id="f284e-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="f284e-141">A Figura 2 mostra a configuração resultante, que adiciona o EMS.</span><span class="sxs-lookup"><span data-stu-id="f284e-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="f284e-142">**Figura 2: A intranet simulada no Azure com o Office 365 e o EMS**</span><span class="sxs-lookup"><span data-stu-id="f284e-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Fase 2 do ambiente de desenvolvimento/teste do One Microsoft Cloud com o Azure, Office 365 e EMS](media/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="f284e-144">Fase 3: Adicionar o Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f284e-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="f284e-145">Nesta fase, inscreva-se para receber a assinatura de avaliação do Dynamics 365 e adicione-a à mesma organização de suas assinaturas de avaliação do Office 365 e do EMS.</span><span class="sxs-lookup"><span data-stu-id="f284e-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="f284e-146">Usando um navegador em seu computador desktop ou no CLIENT1, entre no portal do Office 365 em [https://portal.office.com](https://portal.office.com) com as credenciais de sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f284e-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="f284e-147">Clique no bloco de **Administração**.</span><span class="sxs-lookup"><span data-stu-id="f284e-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="f284e-148">Na guia **centro de administração do Office**, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.</span><span class="sxs-lookup"><span data-stu-id="f284e-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="f284e-p105">Na página **Comprar serviços**, encontre o item **Dynamics 365 Plan 1 Enterprise Edition**. Passe o ponteiro do mouse sobre ele e clique em **Iniciar avaliação gratuita**.</span><span class="sxs-lookup"><span data-stu-id="f284e-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="f284e-151">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="f284e-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="f284e-152">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="f284e-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f284e-p106">A assinatura de avaliação do Dynamics 365 Plan 1 Enterprise Edition é de 30 dias, que podem ser facilmente estendidos por mais 30 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com algumas licenças.</span><span class="sxs-lookup"><span data-stu-id="f284e-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="f284e-156">Use estas etapas para atribuir licenças do Dynamics 365 às contas do administrador global, do Usuário 2 e do Usuário 3 e para torná-los administradores do sistema.</span><span class="sxs-lookup"><span data-stu-id="f284e-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="f284e-157">Na guia **centro de administração do Office**, clique em **Usuários > Usuários Ativos**.</span><span class="sxs-lookup"><span data-stu-id="f284e-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="f284e-158">Na lista de usuários ativos, clique em sua conta de administrador global e depois em **Editar** para **Licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="f284e-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="f284e-159">No painel **Licenças de produto**, mude a licença de produto de **Dynamics 365 Plan 1 Enterprise Edition** para **Ativada**, clique em **Salvar** e clique em **Fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="f284e-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="f284e-160">Siga as etapas 2 e 3 para as contas dos Usuários 2 e 3.</span><span class="sxs-lookup"><span data-stu-id="f284e-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="f284e-161">Feche a guia **centro de administração do Office**.</span><span class="sxs-lookup"><span data-stu-id="f284e-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="f284e-162">Use estas etapas para configurar as contas dos Usuários 2 e 3 como administradores de sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="f284e-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="f284e-163">Na guia **centro de administração do Office** no navegador, no painel de navegação esquerdo, clique em **Centros de administração** e depois em **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="f284e-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="f284e-164">Talvez seja necessário aguardar que o Dynamics 365 conclua o provisionamento antes que seja exibido no menu.</span><span class="sxs-lookup"><span data-stu-id="f284e-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="f284e-165">Na guia Dynamics 365, clique em **Todos Esses**e depois em **Concluir Instalação.**</span><span class="sxs-lookup"><span data-stu-id="f284e-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="f284e-166">Aguarde que a instalação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="f284e-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="f284e-p107">Ao concluir a instalação, ele exibe o Painel de atividades de vendas com base nos dados de exemplo que fazem parte da assinatura de avaliação. Aproveite para ver o vídeo **Bem-vindo à sua avaliação** vídeo. Feche a janela do vídeo após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="f284e-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="f284e-170">Na barra superior, clique na seta para baixo ao lado de **Vendas**, clique em **Configurações**e em **Segurança**.</span><span class="sxs-lookup"><span data-stu-id="f284e-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="f284e-171">Na página **Segurança**, clique em **Usuários**.</span><span class="sxs-lookup"><span data-stu-id="f284e-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="f284e-172">Na lista de usuários, clique em **Usuário 2**.</span><span class="sxs-lookup"><span data-stu-id="f284e-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="f284e-173">Na barra de ferramentas, clique em **Gerenciar Funções**.</span><span class="sxs-lookup"><span data-stu-id="f284e-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="f284e-174">Em **Gerenciar Funções**, clique em **Administrador do Sistema**e em **OK**.</span><span class="sxs-lookup"><span data-stu-id="f284e-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="f284e-175">Na barra de ferramentas superior clique em **Segurança**.</span><span class="sxs-lookup"><span data-stu-id="f284e-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="f284e-176">Repita as etapas de 5 a 8 para a conta do Usuário 3.</span><span class="sxs-lookup"><span data-stu-id="f284e-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="f284e-177">Feche a guia **Usuário: Usuário3**.</span><span class="sxs-lookup"><span data-stu-id="f284e-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f284e-178">A função de administrador do sistema do Dynamics 365 foi atribuída automaticamente pela sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="f284e-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="f284e-179">Seu ambiente de desenvolvimento/teste agora tem:</span><span class="sxs-lookup"><span data-stu-id="f284e-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="f284e-180">A intranet simulada em execução nos serviços de infraestrutura do Azure.</span><span class="sxs-lookup"><span data-stu-id="f284e-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="f284e-181">As assinaturas de avaliação do Office 365 Enterprise E5, do EMS e do Dynamics 365 compartilham a mesma organização e o mesmo locatário do Azure AD com a sua lista de contas de usuários.</span><span class="sxs-lookup"><span data-stu-id="f284e-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="f284e-182">Todas as suas contas de usuário habilitadas para usar o Office 365 E5 Enterprise e o EMS.</span><span class="sxs-lookup"><span data-stu-id="f284e-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="f284e-183">As contas do administrador global da empresa, do Usuário 2 e do Usuário 3 estão habilitadas para usarem o Dynamics 365 e são os administradores do sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="f284e-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="f284e-184">A Figura 3 mostra a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="f284e-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="f284e-185">**Figura 3: A intranet simulada no Azure com o Office 365, o EMS e o Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="f284e-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Fase 3 do ambiente de desenvolvimento/teste do One Microsoft Cloud com o Azure, Office 365, EMS e Dynamics 365](media/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="f284e-187">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f284e-187">Next steps</span></span>

<span data-ttu-id="f284e-p108">Agora você pode experimentar seu ambiente de desenvolvimento/teste do One Microsoft Cloud. Aqui estão algumas ideias para experiências guiadas:</span><span class="sxs-lookup"><span data-stu-id="f284e-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="f284e-190">Configurar políticas do gerenciamento de aplicativo móvel (MAM) no EMS para aplicativos do Office 365</span><span class="sxs-lookup"><span data-stu-id="f284e-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="f284e-191">Demonstrar o Exchange Online em integração do Office 365 com contatos do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f284e-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="f284e-192">Criar uma rede simulada entre locais nos serviços de infraestrutura Azure para hospedar cargas de trabalho baseadas em servidor</span><span class="sxs-lookup"><span data-stu-id="f284e-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="f284e-193">Confira também
</span><span class="sxs-lookup"><span data-stu-id="f284e-193">See Also</span></span>

[<span data-ttu-id="f284e-194">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="f284e-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="f284e-195">Recursos de arquitetura de TI do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f284e-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="f284e-196">Soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="f284e-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="f284e-197">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="f284e-197">Security solutions</span></span>](security-solutions.md)





