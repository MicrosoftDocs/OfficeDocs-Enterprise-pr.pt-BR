---
title: O ambiente de desenvolvimento e teste de um Microsoft Cloud
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
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: "Resumo: Use este guia de laboratório de teste para criar um ambiente de desenvolvimento e teste que inclui todas as ofertas de nuvem da Microsoft."
ms.openlocfilehash: 90f93b1050ec0c2b82f4ed42c76413d68b314b7c
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="c6cfb-103">O ambiente de desenvolvimento e teste de um Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="c6cfb-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="c6cfb-104">**Resumo:** Use este guia de laboratório de teste para criar um ambiente de desenvolvimento e teste que inclui todas as ofertas de nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="c6cfb-p101">Com as instruções deste artigo, você cria uma intranet simulada nos serviços de infraestrutura do Microsoft Azure e em seguida, adicione o Microsoft Office 365, Microsoft Enterprise mobilidade + segurança (EMS) e inscrições do Microsoft Dynamics 365. O resultado é uma organização simplificada que usa ofertas de nuvem da Microsoft todos ao mesmo tempo em um ambiente de desenvolvimento e teste único.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Fase 3 do ambiente de desenvolvimento/teste do Microsoft Cloud com o Azure, Office 365, EMS e Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="c6cfb-108">Você pode usar a configuração resultante para:</span><span class="sxs-lookup"><span data-stu-id="c6cfb-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="c6cfb-109">Experiência a integração entre as ofertas de nuvem da Microsoft, como a infraestrutura de identidade comuns fornecidos pelo Windows Azure AD (Active Directory).</span><span class="sxs-lookup"><span data-stu-id="c6cfb-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="c6cfb-110">Avalie os cenários de ponta a ponta que incluem vários ofertas de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="c6cfb-111">Crie uma demonstração, prova de conceito ou configuração de desenvolvimento e teste que usa vários ofertas de Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="c6cfb-112">Construa suas habilidades Microsoft Cloud para desenvolvimento profissional.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="c6cfb-113">Fase 1: Criar uma intranet simulada e adicionar o Office 365</span><span class="sxs-lookup"><span data-stu-id="c6cfb-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="c6cfb-114">Siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c6cfb-114">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c6cfb-115">A Figura 1 mostra a configuração resultante, que inclui uma intranet simulada executando nos serviços de infraestrutura do Windows Azure e sincronização de diretório a partir de uma floresta do Windows Server AD (Active Directory) no local e o Office 365.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-115">Figure 1 shows your resulting configuration, which includes Office 365 and a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="c6cfb-116">**Figura 1: Simulado intranet no Windows Azure com o Office 365**</span><span class="sxs-lookup"><span data-stu-id="c6cfb-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![O ambiente de desenvolvimento e teste do Office 365 com o DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="c6cfb-p102">Versão de avaliação do Azure é 30 dias. A assinatura de avaliação do Office 365 Enterprise E5 é 30 dias, que pode ser facilmente estendidos para outro 30 dias. Para um ambiente de desenvolvimento e teste permanente, crie um novo pagos de assinatura do Windows Azure e uma nova assinatura paga do Office 365 Enterprise E5 com um pequeno número de licenças.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-p102">The Azure trial is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="c6cfb-121">Fase 2: Adicionar EMS</span><span class="sxs-lookup"><span data-stu-id="c6cfb-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="c6cfb-122">Nesta fase, inscreva-se para a assinatura de avaliação do EMS e adicione-a à mesma organização de sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="c6cfb-123">Com um navegador em um computador desktop ou do CLIENT1, entrar no portal do Office 365 em [https://portal.office.com](https://portal.office.com) com as credenciais da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-123">With a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="c6cfb-124">Clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="c6cfb-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c6cfb-125">Na guia do **Centro de administração do Office** em seu navegador, no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="c6cfb-p103">Na página **Serviços de compra** , localize o item de **mobilidade corporativos + E5 de segurança** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="c6cfb-128">Na página **confirmar seu pedido** , clique em **tente agora**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="c6cfb-129">Na página **confirmação de ordem** , clique em **continuar**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c6cfb-p104">A assinatura de avaliação do Enterprise Mobility + Security E5 dura 90 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com uma pequena quantidade de licenças.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="c6cfb-132">Em seguida, habilite a mobilidade corporativos + licença E5 de segurança para todas as contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="c6cfb-133">Na guia do **Centro de administração do Office 365** em seu navegador, no painel de navegação esquerdo, clique em **usuários > usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="c6cfb-134">Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="c6cfb-135">No painel de **licenças do produto** , ativar a licença do produto para **mobilidade corporativos + E5 de segurança** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="c6cfb-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="c6cfb-136">Para todas as suas contas (User1, usuário 2, 3 do usuário, usuário 4 e 5 do usuário), siga as etapas 2 e 3.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="c6cfb-137">Seu ambiente de desenvolvimento e teste agora tem:</span><span class="sxs-lookup"><span data-stu-id="c6cfb-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="c6cfb-138">Uma intranet simulada em execução nos serviços de infraestrutura do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="c6cfb-139">Assinaturas de avaliação do Office 365 Enterprise E5 e do EMS que compartilham a mesma organização e o mesmo locatário do Azure AD com sua lista de contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="c6cfb-140">Todas as suas contas de usuário habilitadas para usar o Office 365 E5 Enterprise e o EMS.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="c6cfb-141">A Figura 2 mostra a configuração resultante, que adiciona EMS.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="c6cfb-142">**Figura 2: Simulado intranet no Windows Azure com o Office 365 e EMS**</span><span class="sxs-lookup"><span data-stu-id="c6cfb-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Fase 2 do ambiente de desenvolvimento/teste do Microsoft Cloud com o Azure, Office 365 e EMS](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="c6cfb-144">Fase 3: Adicionar Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c6cfb-144">Phase 3: Add Dynamics 365</span></span>

<span data-ttu-id="c6cfb-145">Nesta fase, inscreva-se para a assinatura de avaliação do Dynamics 365 e adicioná-lo à mesma organização que suas assinaturas de avaliação do Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="c6cfb-146">Usando um navegador em um computador desktop ou do CLIENT1, entrar no portal do Office 365 em [https://portal.office.com](https://portal.office.com) com as credenciais da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-146">Using a browser on either your desktop computer or from CLIENT1, sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="c6cfb-147">Clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="c6cfb-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c6cfb-148">Na guia **Centro de administração do Office** , no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="c6cfb-p105">Na página **Serviços de compra** , encontre o item **Dynamics 365 planejar 1 Enterprise Edition** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="c6cfb-151">Na página **confirmar seu pedido** , clique em **tente agora**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="c6cfb-152">Na página **confirmação de ordem** , clique em **continuar**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c6cfb-p106">A assinatura de avaliação do Dynamics 365 planejar 1 Enterprise Edition é 30 dias. Você pode estender facilmente a assinatura de trilha para outro 30 dias. Para um ambiente de desenvolvimento e teste permanente, crie uma nova assinatura com um pequeno número de licenças paga.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="c6cfb-156">Use estas etapas para atribuir licenças do Dynamics 365 o administrador global, o usuário 2 e contas de usuário 3 e torná-los aos administradores de sistema.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="c6cfb-157">Na guia do **Centro de administração do Office** , clique em **usuários > usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="c6cfb-158">Na lista de usuários ativos, clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="c6cfb-159">No painel de **licenças do produto** , ativar a licença do produto para **Dynamics 365 planejar 1 Enterprise Edition** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="c6cfb-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="c6cfb-160">Execute as etapas 2 e 3 para as contas de usuário 2 e 3 do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="c6cfb-161">Feche a guia do **Centro de administração do Office** .</span><span class="sxs-lookup"><span data-stu-id="c6cfb-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="c6cfb-162">Use estas etapas para configurar as contas de usuário 2 e 3 do usuário como os administradores de sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="c6cfb-163">Na guia do **Centro de administração do Office** em seu navegador, no painel de navegação esquerdo, clique em **Admin centrais**e clique em **Dynamics 365**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="c6cfb-164">Você pode precisar aguardar Dynamics 365 concluir o provisionamento antes do Dynamics 365 aparece no menu.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="c6cfb-165">Na guia Dynamics 365, clique em **todos esses**e, em seguida, clique em **Concluir a instalação.**</span><span class="sxs-lookup"><span data-stu-id="c6cfb-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="c6cfb-166">Aguarde concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="c6cfb-p107">Quando terminar a instalação, ele exibe um painel de atividade de vendas com base nos dados de amostra que faz parte da assinatura trilha. Levar alguns momentos para exibir o **Bem-vindo à sua avaliação** vídeo. Feche a janela de vídeo quando tiver concluído.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="c6cfb-170">Na barra de ferramentas na parte superior, clique na seta ao lado de **vendas**, clique em **configurações**e, em seguida, clique em **segurança**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="c6cfb-171">Na página **segurança** , clique em **usuários**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="c6cfb-172">Na lista de usuários, clique em **usuário 2**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="c6cfb-173">Na barra de ferramentas, clique em **Gerenciar funções**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="c6cfb-174">Em **Gerenciar funções**, clique em **Administrador do sistema**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="c6cfb-175">Na barra de ferramentas na parte superior, clique em **segurança**.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="c6cfb-176">Repita as etapas 5 a 8 para a conta de usuário 3.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="c6cfb-177">Fechar o **usuário: User3** guia.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c6cfb-178">Sua conta de administrador global do Office 365 foi atribuída automaticamente a função de administrador de sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="c6cfb-179">Seu ambiente de desenvolvimento e teste agora tem:</span><span class="sxs-lookup"><span data-stu-id="c6cfb-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="c6cfb-180">Uma intranet simulada em execução nos serviços de infraestrutura do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="c6cfb-181">O Office 365 E5 Enterprise, EMS e Dynamics 365 assinaturas de avaliação da mesma organização e o mesmo inquilino do Azure AD de compartilhamento com sua lista de contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="c6cfb-182">Todas as suas contas de usuário habilitadas para usar o Office 365 E5 Enterprise e o EMS.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="c6cfb-183">Seu administrador corporativo global, o usuário 2 e contas de usuário 3 estão habilitadas para usar Dynamics 365 e são administradores de sistema do Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="c6cfb-184">A Figura 3 mostra a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="c6cfb-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="c6cfb-185">**Figura 3: Simulado intranet no Windows Azure com o Office 365, EMS e Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="c6cfb-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Fase 3 do ambiente de desenvolvimento/teste do Microsoft Cloud com o Azure, Office 365, EMS e Dynamics 365](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="c6cfb-187">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c6cfb-187">Next steps</span></span>

<span data-ttu-id="c6cfb-p108">Agora, você pode experimentar seu ambiente de desenvolvimento e teste de um Microsoft Cloud. Aqui estão algumas ideias para experiências guiadas:</span><span class="sxs-lookup"><span data-stu-id="c6cfb-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="c6cfb-190">Configurar políticas de gerenciamento (MAM) do aplicativo móvel no EMS para aplicativos do Office 365</span><span class="sxs-lookup"><span data-stu-id="c6cfb-190">Configure mobile application management (MAM) policies in EMS for Office 365 applications</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="c6cfb-191">Demonstrar o Exchange Online no Office 365 integração com contatos Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c6cfb-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contacts</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="c6cfb-192">Criar uma rede de locais cruzados simulado nos serviços de infraestrutura do Windows Azure para hospedar as cargas de trabalho baseado em servidor</span><span class="sxs-lookup"><span data-stu-id="c6cfb-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloads</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="c6cfb-193">Veja também</span><span class="sxs-lookup"><span data-stu-id="c6cfb-193">See Also</span></span>

[<span data-ttu-id="c6cfb-194">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="c6cfb-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c6cfb-195">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="c6cfb-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="c6cfb-196">Soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="c6cfb-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="c6cfb-197">Soluções de segurança</span><span class="sxs-lookup"><span data-stu-id="c6cfb-197">Security solutions</span></span>](security-solutions.md)





