---
title: "Criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Resumo: Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em seu ambiente de desenvolvimento e teste de campanha política."
ms.openlocfilehash: 82e671af271508dfdecac6169a7892a8a12b7865
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="dbafe-103">Criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="dbafe-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="dbafe-104">**Resumo:** Crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em seu ambiente de desenvolvimento e teste de campanha política.</span><span class="sxs-lookup"><span data-stu-id="dbafe-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="dbafe-p101">Use as instruções deste artigo para criar um ambiente de desenvolvimento e teste que inclui os quatro tipos diferentes de sites de equipe do SharePoint Online para as [Diretrizes de segurança da Microsoft para campanhas político, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solução. Esses sites são descritos em detalhes no tópico 10, intitulado **SharePoint e o OneDrive for Business**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="dbafe-107">Fase 1: Crie seu ambiente de desenvolvimento e teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="dbafe-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="dbafe-108">Primeiro, siga as instruções em [Configure grupos e usuários para um ambiente de desenvolvimento e teste de campanha político](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) para criar suas assinaturas, usuários e grupos.</span><span class="sxs-lookup"><span data-stu-id="dbafe-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="dbafe-109">Fase 2: Criar rótulos do Office 365</span><span class="sxs-lookup"><span data-stu-id="dbafe-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="dbafe-110">Nesta fase, você deve criar os rótulos para os diferentes níveis de segurança para pastas de documentos do site de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="dbafe-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="dbafe-p102">Se necessário, entre no portal do Office 365 com as credenciais da conta de administrador global de sua assinatura de avaliação. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="dbafe-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dbafe-113">Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="dbafe-114">Na guia novo **Centro de administração do Office** do seu navegador, clique em **centrais de Admin > segurança &amp; conformidade**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="dbafe-115">Do novo **Home - segurança &amp; conformidade** guia do navegador, clique em **classificações > rótulos**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="dbafe-116">Da **Home > rótulos** painel, clique em **criar um rótulo**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="dbafe-117">No painel de **nome de seu rótulo** , digite **interno**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="dbafe-118">No painel de **configurações de rótulo** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="dbafe-119">No painel **Revise suas configurações** , clique em **criar este rótulo**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="dbafe-120">Repita as etapas 5 a 8 para esses rótulos adicionais:</span><span class="sxs-lookup"><span data-stu-id="dbafe-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="dbafe-121">Particular</span><span class="sxs-lookup"><span data-stu-id="dbafe-121">Private</span></span>
    
  - <span data-ttu-id="dbafe-122">Confidenciais</span><span class="sxs-lookup"><span data-stu-id="dbafe-122">Sensitive</span></span>
    
  - <span data-ttu-id="dbafe-123">Altamente confidenciais</span><span class="sxs-lookup"><span data-stu-id="dbafe-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="dbafe-124">Da **Home > rótulos** painel, clique em **Publicar rótulos**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="dbafe-125">No painel **Choose rótulos para publicar** , clique em **rótulos de escolher para publicar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="dbafe-126">No painel **Choose rótulos** , clique em **Adicionar** e selecione todas as quatro rótulos.</span><span class="sxs-lookup"><span data-stu-id="dbafe-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="dbafe-127">Clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="dbafe-128">No painel **Choose rótulos para publicar** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="dbafe-129">No painel **Choose locais** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="dbafe-130">No painel de **sua política de nome** , digite **campanha** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="dbafe-131">No painel **Revise suas configurações** , clique em **rótulos de publicar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="dbafe-132">Fase 3: Criar seus sites de equipe do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="dbafe-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="dbafe-133">Nesta fase, criar e configurar sites de equipe do SharePoint Online para a sua campanha política correspondente aos quatro tipos de sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="dbafe-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="dbafe-134">Site da equipe ampla campanha</span><span class="sxs-lookup"><span data-stu-id="dbafe-134">Campaign wide team site</span></span>

<span data-ttu-id="dbafe-135">Para criar um site de equipe ' baseline público do SharePoint Online, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbafe-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="dbafe-136">Se necessário, use um navegador no computador local e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="dbafe-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="dbafe-137">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dbafe-138">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dbafe-139">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dbafe-140">Em **nome do Site**, digite **campanha ampla**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="dbafe-141">Na **Descrição do site de equipe**, digite o **site do SharePoint para toda a campanha**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="dbafe-142">Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dbafe-143">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="dbafe-144">Em seguida, configure a pasta de documentos do site campanha ampla de equipe para o rótulo interno.</span><span class="sxs-lookup"><span data-stu-id="dbafe-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="dbafe-145">Na guia **wide-Home de campanhas** de seu navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="dbafe-146">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="dbafe-147">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="dbafe-148">Em **Configurações se aplicam rótulo**, selecione **interno**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="dbafe-149">Site da campanha 1 equipe de projeto</span><span class="sxs-lookup"><span data-stu-id="dbafe-149">Campaign project 1 team site</span></span>

<span data-ttu-id="dbafe-150">Para criar um site de equipe baseline privado SharePoint Online para um projeto dentro da campanha, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbafe-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="dbafe-151">Se necessário, use um navegador no computador local e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="dbafe-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="dbafe-152">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dbafe-153">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dbafe-154">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dbafe-155">Em **nome do Site**, digite **Projeto1 campanha**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="dbafe-156">Na **Descrição do site de equipe,** digite o **site do SharePoint para o projeto de campanha 1**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="dbafe-157">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dbafe-158">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="dbafe-159">Em seguida, configure a pasta de documentos do site campanha projeto 1 de equipe para o rótulo de privada.</span><span class="sxs-lookup"><span data-stu-id="dbafe-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="dbafe-160">Na guia **projeto 1-Home de campanhas** de seu navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="dbafe-161">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="dbafe-162">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="dbafe-163">Em **Configurações se aplicam rótulo**, selecione **privada**e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="dbafe-164">Site da campanha de marketing da equipe</span><span class="sxs-lookup"><span data-stu-id="dbafe-164">Campaign marketing team site</span></span>

<span data-ttu-id="dbafe-165">Para criar um nível confidenciais isolado SharePoint Online site de equipe para campanha de marketing recursos, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbafe-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="dbafe-166">Usando um navegador no computador local, entre no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="dbafe-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="dbafe-167">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dbafe-168">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dbafe-169">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dbafe-170">Em **nome do site de equipe**, digite **marketing campanha**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="dbafe-171">Na **Descrição do site de equipe**, digite o **site do SharePoint para campanha de marketing (confidenciais)**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="dbafe-172">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dbafe-173">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="dbafe-174">Na guia novo **marketing campanha** no seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="dbafe-175">No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="dbafe-176">Na guia **permissões** nova no seu navegador, clique em **Configurações de solicitação de acesso**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="dbafe-177">Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque as caixas de seleção **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** , digite **ITAdmin1 @** <your organization name> **. onmicrosoft.com** em **Enviar todas as solicitações de acesso**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="dbafe-178">Clique em **campanhas de marketing membros** na lista.</span><span class="sxs-lookup"><span data-stu-id="dbafe-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="dbafe-179">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="dbafe-180">Na caixa de diálogo **compartilhar** , digite **sênior e à equipe estratégico**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="dbafe-181">Repita as etapas 14 e 15 para o grupo de **equipe de análise** e a conta de usuário **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="dbafe-182">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="dbafe-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="dbafe-183">Na lista, clique em **campanhas de marketing proprietários** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="dbafe-184">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="dbafe-185">Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="dbafe-186">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="dbafe-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="dbafe-187">Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Home campanha de marketing** no seu navegador e, em seguida, feche o painel de **permissões do Site** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="dbafe-188">Estes são os resultados da configuração das permissões:</span><span class="sxs-lookup"><span data-stu-id="dbafe-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="dbafe-189">Grupo do SharePoint de **Campanhas de marketing-membros** contém somente o **sênior e à equipe estratégica** grupo (que contém as contas de usuário do candidato, ChiefOfStaff e Strategic1), grupo **campanhas marketing** (que contém o conta de usuário de administrador global), o grupo de **equipe de análise** (que contém a conta de usuário DataScientist1) e a conta de usuário **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="dbafe-190">O grupo do SharePoint de **Campanhas de marketing-proprietários** contém apenas o grupo de **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="dbafe-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="dbafe-191">Grupo de **Campanhas de marketing-visitantes** do SharePoint não contém grupos ou contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="dbafe-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="dbafe-192">Membros não podem modificar permissões de nível de site (isso só pode ser feito por membros do grupo de **Campanhas de marketing-proprietários** ).</span><span class="sxs-lookup"><span data-stu-id="dbafe-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="dbafe-193">Outras contas de usuário não podem acessar o site ou seus recursos, mas podem solicitar acesso ao site, qual enviará um email para a caixa de correio de conta de usuário ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="dbafe-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="dbafe-194">Em seguida, configure a pasta de documentos do site de equipe marketing a campanha para o rótulo de confidencial.</span><span class="sxs-lookup"><span data-stu-id="dbafe-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="dbafe-195">Na guia **Home campanha de marketing** do navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="dbafe-196">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="dbafe-197">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="dbafe-198">Em **Configurações se aplicam rótulo**, selecione **confidenciais**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="dbafe-p103">Em seguida, configure uma política de prevenção (DLP) de perda de dados que notifica os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo confidencial fora da organização. Essa política DLP serão aplicadas aos recursos em que o site da campanha de marketing.</span><span class="sxs-lookup"><span data-stu-id="dbafe-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="dbafe-201">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="dbafe-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="dbafe-202">No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="dbafe-203">No painel de **prevenção de perda de dados** , clique em **+ para criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="dbafe-204">No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="dbafe-205">No painel de **sua política de nome** , digite os **sites de equipe do SharePoint Online rótulo confidenciais** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="dbafe-206">No painel **Choose locais** , clique em **Deixe-me escolher locais específicos**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="dbafe-207">Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dbafe-208">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="dbafe-209">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="dbafe-210">No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="dbafe-211">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="dbafe-212">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="dbafe-213">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, clique em **Personalizar a dica e email**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="dbafe-214">No painel de **dicas de política personalizar e notificações por email** , clique em **Personalizar o texto da dica de política**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="dbafe-215">Na caixa de texto, digite ou cole o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="dbafe-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="dbafe-p104">Para compartilhar com um usuário fora da organização, baixe o arquivo e, em seguida, abri-lo. Clique em arquivo, em seguida, proteger documento e, em seguida, criptografar com senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="dbafe-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="dbafe-219">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="dbafe-220">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, desmarque a caixa de seleção **bloquear pessoas de compartilhamento e restringir o acesso ao conteúdo compartilhado** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="dbafe-221">No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="dbafe-222">No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="dbafe-223">Site de equipe da estratégia de campanha</span><span class="sxs-lookup"><span data-stu-id="dbafe-223">Campaign strategy team site</span></span>

<span data-ttu-id="dbafe-224">Para criar um site de equipe do SharePoint Online isolado no nível altamente confidencial para recursos de estratégia de campanha, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbafe-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="dbafe-225">Se necessário, use um navegador no computador local e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="dbafe-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="dbafe-226">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dbafe-227">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dbafe-228">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dbafe-229">Em **nome do site de equipe**, digite a **estratégia de campanha**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="dbafe-230">Na **Descrição do site de equipe**, digite o **site do SharePoint para a estratégia de campanha (altamente confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="dbafe-231">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dbafe-232">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="dbafe-233">Na guia **estratégia da campanha de** novo no seu navegador, na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="dbafe-234">No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="dbafe-235">Na guia **permissões** nova no seu navegador, clique em **Configurações de solicitação de acesso**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="dbafe-236">Na caixa de diálogo **Configurações de solicitação de acesso** , desmarque **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** (de forma que todas as três caixas de seleção estiver desmarcadas) e clique em ** Okey**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="dbafe-237">Clique em **estratégia da campanha de membros** na lista.</span><span class="sxs-lookup"><span data-stu-id="dbafe-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="dbafe-238">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="dbafe-239">Na caixa de diálogo **compartilhar** , digite **sênior e à equipe estratégico**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="dbafe-240">Na lista, clique em **estratégia da campanha de proprietários** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="dbafe-241">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="dbafe-242">Na caixa de diálogo **compartilhar** , digite a **equipe de TI**, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="dbafe-243">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="dbafe-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="dbafe-244">Fechar a guia **pessoas e grupos** no seu navegador, clique na guia **Home a estratégia de campanhas** no seu navegador e, em seguida, feche o painel de **permissões do Site** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="dbafe-245">Estes são os resultados da configuração das permissões:</span><span class="sxs-lookup"><span data-stu-id="dbafe-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="dbafe-246">Grupo do SharePoint **Campanha estratégia-membros** contém apenas o grupo de **sênior e à equipe estratégico** (que contém apenas as contas de usuário de candidato, ChiefOfStaff e Strategic1) e o grupo de **estratégia de campanha** (que contém somente a administrador global conta de usuário).</span><span class="sxs-lookup"><span data-stu-id="dbafe-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="dbafe-247">Grupo do SharePoint de **Proprietários de estratégia de campanha** contém apenas o grupo de **equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="dbafe-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="dbafe-248">Grupo do SharePoint **Campanha estratégia-visitantes** não contém grupos ou contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="dbafe-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="dbafe-249">Membros não podem modificar permissões de nível de site (isso só pode ser feito por membros do grupo **Proprietários de estratégia de campanha** ).</span><span class="sxs-lookup"><span data-stu-id="dbafe-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="dbafe-p105">Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar acesso ao site. Permissões adicionais para o site devem ser realizadas pelo administrador global ou por um membro do grupo **Proprietários campanha estratégia** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="dbafe-252">Em seguida, configure a pasta de documentos do site da equipe de estratégia campanha para o rótulo de altamente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="dbafe-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="dbafe-253">Na guia **Home a estratégia de campanhas** de seu navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="dbafe-254">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="dbafe-255">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="dbafe-256">Em **Configurações se aplicam rótulo**, selecione **Altamente confidenciais**e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="dbafe-p106">Em seguida, configure uma política de DLP que bloqueia usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo altamente confidenciais fora da organização. Essa política DLP serão aplicadas aos recursos no site da campanha de estratégia.</span><span class="sxs-lookup"><span data-stu-id="dbafe-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="dbafe-259">Se necessário, use um navegador no computador local e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) com uma conta que tenha a função de administrador de segurança ou administrador da empresa.</span><span class="sxs-lookup"><span data-stu-id="dbafe-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="dbafe-260">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="dbafe-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="dbafe-261">No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="dbafe-262">No painel de **prevenção de perda de dados** , clique em **+ para criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="dbafe-263">No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="dbafe-264">No painel de **sua política de nome** , digite **altamente confidenciais sites de equipe do SharePoint Online do rótulo** em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="dbafe-265">No painel **Choose locais** , clique em **Deixe-me escolher locais específicos**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dbafe-266">Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="dbafe-267">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="dbafe-268">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="dbafe-269">No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **Altamente confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="dbafe-270">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="dbafe-271">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="dbafe-272">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, clique em **Personalizar a dica e email**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="dbafe-273">No painel de **dicas de política personalizar e notificações por email** , clique em **Personalizar o texto da dica de política**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="dbafe-274">Na caixa de texto, digite ou cole o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="dbafe-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="dbafe-p107">Para compartilhar com um usuário fora da organização, baixe o arquivo e, em seguida, abri-lo. Clique em arquivo, em seguida, proteger documento e, em seguida, criptografar com senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="dbafe-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="dbafe-278">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="dbafe-279">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, selecione **exigir uma justificativa comercial para substituir**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="dbafe-280">No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="dbafe-281">No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="dbafe-282">Use as instruções em [Ativar o Azure RMS com o Centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="dbafe-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="dbafe-283">Em seguida, configure a proteção de informações do Windows Azure com uma nova política de escopo e sub-recurso rótulo para proteção e permissões com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="dbafe-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="dbafe-p108">Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="dbafe-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dbafe-286">Em uma guia separada do navegador, vá para o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="dbafe-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="dbafe-287">Se essa for a primeira vez que você está configurando a proteção de informações do Windows Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="dbafe-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="dbafe-288">No painel de lista, clique em **mais de serviços**, digite as **informações**e clique em **Proteção de informações do Windows Azure**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="dbafe-289">No blade **proteção das informações do Azure** , clique em **escopo políticas > + Adicionar uma nova diretiva**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="dbafe-290">Digite **CampaignStrategy** no **nome da diretiva** e **rótulo para documentos no site da equipe de estratégia campanha** em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="dbafe-291">Clique em **Selecione quais usuários ou grupos fazer essa política > grupos de usuários/**e selecione **sênior e equipe estratégica**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="dbafe-292">Clique em **Selecione > Okey**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="dbafe-293">Para o rótulo de **Altamente confidenciais** , clique nas reticências (…) e, em seguida, clique em **Adicionar um rótulo de subsites**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="dbafe-294">Digite um nome para o rótulo de subsites em **nome** e uma descrição do rótulo em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="dbafe-295">Em **definir permissões para documentos e emails contendo esse rótulo**, clique em **proteger**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="dbafe-296">Na seção **proteção** , clique em **Windows Azure (chave de nuvem)**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="dbafe-297">No blade **proteção** , em **configurações de proteção**, clique em **+ Adicionar permissões**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="dbafe-298">No blade **Adicionar permissões** , em **especificar usuários e grupos**, clique em **+ Procurar no diretório**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="dbafe-299">No painel **AAD usuários e grupos** , selecione **sênior e à equipe estratégico**e clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="dbafe-300">Em **Escolha as permissões a predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo**e **Encaminhar** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="dbafe-301">Clique duas vezes em **Okey** .</span><span class="sxs-lookup"><span data-stu-id="dbafe-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="dbafe-302">No **rótulo sub-recurso** blade, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="dbafe-303">Fechar o novo escopo blade de política.</span><span class="sxs-lookup"><span data-stu-id="dbafe-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="dbafe-304">No blade **proteção de informações do Windows Azure - políticas com escopo** , clique em **Publicar**e, em seguida, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="dbafe-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="dbafe-305">Agora você está pronto para começar a criar documentos em sites essas quatro e testar acessá-los com várias contas de usuário em sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="dbafe-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="dbafe-306">Para proteger um documento com esse novo rótulo e de proteção de informações do Windows Azure, você deve [instalar o cliente de proteção de informações do Windows Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em uma máquina de teste, instalar o Office do portal do Office 365 e entrar do Microsoft Word com uma conta no ** Sênior e à equipe estratégica** grupo de sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="dbafe-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dbafe-307">See Also</span><span class="sxs-lookup"><span data-stu-id="dbafe-307">See Also</span></span>

[<span data-ttu-id="dbafe-308">Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil</span><span class="sxs-lookup"><span data-stu-id="dbafe-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="dbafe-309">Configurar grupos e usuários para um ambiente de desenvolvimento e teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="dbafe-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="dbafe-310">Adoção de nuvem Test Lab Guides (TLGs)</span><span class="sxs-lookup"><span data-stu-id="dbafe-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="dbafe-311">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="dbafe-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




