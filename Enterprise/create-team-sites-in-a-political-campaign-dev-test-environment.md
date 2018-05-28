---
title: Criar sites de equipe em um ambiente de desenvolvimento/teste de campanha política
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 'Resumo: crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento/teste de campanha política.'
ms.openlocfilehash: 146632ede567be4bf412304960605e6d87de7657
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="c5438-103">Criar sites de equipe em um ambiente de desenvolvimento/teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="c5438-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="c5438-104">**Resumo:** crie sites de equipe do SharePoint Online públicos, privados, confidenciais e altamente confidenciais em um ambiente de desenvolvimento/teste de campanha política.</span><span class="sxs-lookup"><span data-stu-id="c5438-104">**Create SharePoint Online team sites**. Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="c5438-p101">Use as instruções deste artigo para criar um ambiente de desenvolvimento/teste com quatro diferentes tipos de sites de equipe do SharePoint Online para a solução de [Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md). Esses sites são descritos em detalhes no tópico 10, intitulado **SharePoint e OneDrive for Business**.</span><span class="sxs-lookup"><span data-stu-id="c5438-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="c5438-107">Fase 1: Criar seu ambiente de desenvolvimento/teste de campanha política</span><span class="sxs-lookup"><span data-stu-id="c5438-107">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="c5438-108">Primeiro, siga as instruções em [Configurar grupos e usuários para um ambiente de desenvolvimento/teste de campanha política](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) para criar assinaturas, usuários e grupos.</span><span class="sxs-lookup"><span data-stu-id="c5438-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="c5438-109">Fase 2: Criar rótulos do Office 365</span><span class="sxs-lookup"><span data-stu-id="c5438-109">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="c5438-110">Nesta fase, você deve criar os rótulos para os diferentes níveis de segurança para as pastas e documentos do site da equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c5438-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="c5438-p102">Se necessário, entre no Portal do Office 365 com as credenciais da conta de administrador global da sua assinatura de avaliação. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c5438-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c5438-113">Na guia **Microsoft Office Home**, clique no bloco **Administração**.</span><span class="sxs-lookup"><span data-stu-id="c5438-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c5438-114">Na nova guia **Centro de Administração do Office** do navegador, clique em **Centros de Administração > Segurança&amp; e Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="c5438-114">From the new Office Admin center tab of your browser, click Admin centers > Security & Compliance.</span></span>
    
4. <span data-ttu-id="c5438-115">Na nova guia **Início – Segurança &amp;e Conformidade** do navegador, clique em **Classificações > Rótulos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-115">From the new Home – Security & Compliance tab of your browser, click Classifications > Labels.</span></span>
    
5. <span data-ttu-id="c5438-116">No painel **Início > Rótulos**, clique em **Criar um rótulo**.</span><span class="sxs-lookup"><span data-stu-id="c5438-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="c5438-117">No painel **Atribuir nome ao seu rótulo**, digite **Interno** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-117">On the **Name your label** pane, type **Internal Public**, and click **Next**.</span></span>
    
7. <span data-ttu-id="c5438-118">No painel **Configurações do rótulo**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="c5438-119">No painel **Examine as configurações**, clique em **Criar este rótulo** e clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-119">On the **Review your settings** pane, click **Create this label**, and  click **Close**.</span></span>
    
9. <span data-ttu-id="c5438-120">Repita as etapas de 5 a 8 para os rótulos adicionais:</span><span class="sxs-lookup"><span data-stu-id="c5438-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="c5438-121">Private</span><span class="sxs-lookup"><span data-stu-id="c5438-121">Private</span></span>
    
  - <span data-ttu-id="c5438-122">Confidencial</span><span class="sxs-lookup"><span data-stu-id="c5438-122">Sensitive</span></span>
    
  - <span data-ttu-id="c5438-123">Altamente Confidencial</span><span class="sxs-lookup"><span data-stu-id="c5438-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="c5438-124">No painel **Início > Rótulos**, clique em **Publicar rótulos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="c5438-125">No painel **Escolher rótulos para publicar**, clique em **Escolher rótulos para publicar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="c5438-126">No painel **Escolher rótulos**, clique em **Adicionar** e selecione todos os quatro rótulos.</span><span class="sxs-lookup"><span data-stu-id="c5438-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="c5438-127">Clique em **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="c5438-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="c5438-128">No painel **Escolher rótulos para publicar**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="c5438-129">No painel **Escolher locais**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="c5438-130">No painel **Nomear sua política**, digite **Campanha** em **Nome** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-130">On the **Name your policy** pane, type **Example organization** in **Name**, and click **Next**.</span></span>
    
17. <span data-ttu-id="c5438-131">No painel **Examine as configurações**, clique em **Publicar rótulos** e clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-131">On the **Review your settings** pane, click **Publish labels**, and click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="c5438-132">Fase 3: Criar seus sites de equipe do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c5438-132">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="c5438-133">Nessa fase, você cria e configura sites de equipe do SharePoint Online para a campanha política correspondente aos quatro tipos de sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c5438-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="c5438-134">Site de equipe de toda a campanha</span><span class="sxs-lookup"><span data-stu-id="c5438-134">Organization wide team site</span></span>

<span data-ttu-id="c5438-135">Para criar um site de equipe do SharePoint Online público de linha de base, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c5438-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="c5438-136">Se necessário, use um navegador no computador local e entre no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c5438-136">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see Where to sign in to Office 365.</span></span>
    
2. <span data-ttu-id="c5438-137">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c5438-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c5438-138">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="c5438-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c5438-139">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="c5438-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c5438-140">Em **Nome do site**, digite **Toda a campanha**.</span><span class="sxs-lookup"><span data-stu-id="c5438-140">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="c5438-141">Na **Descrição do site de equipe**, digite **Site do SharePoint para toda a campanha**.</span><span class="sxs-lookup"><span data-stu-id="c5438-141">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="c5438-142">Em **Configurações de privacidade**, selecione **Público – qualquer pessoa na organização pode acessar esse site** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-142">In **Privacy settings**, select **Public – anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c5438-143">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="c5438-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="c5438-144">Em seguida, configure a pasta de documentos do site de equipe Toda a campanha com o rótulo Interno.</span><span class="sxs-lookup"><span data-stu-id="c5438-144">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="c5438-145">Na guia **Toda a campanha – Página inicial** do navegador, clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-145">In the **Organization wide–Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c5438-146">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c5438-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c5438-147">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c5438-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c5438-148">Em **Configurações – Aplicar Rótulo**, selecione **Interno** e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-148">In **Settings-Apply Label**, select **Internal Public**, and click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="c5438-149">Site de equipe 1 de projeto de campanha</span><span class="sxs-lookup"><span data-stu-id="c5438-149">Campaign project 1 team site</span></span>

<span data-ttu-id="c5438-150">Para criar um site de equipe do SharePoint Online privado de linha de base para um projeto dentro da campanha, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c5438-150">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="c5438-151">Se necessário, use um navegador no computador local e entre no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c5438-151">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="c5438-152">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c5438-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c5438-153">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="c5438-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c5438-154">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="c5438-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c5438-155">Em **Nome do site**, digite **Projeto 1 da campanha**.</span><span class="sxs-lookup"><span data-stu-id="c5438-155">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="c5438-156">Na **Descrição do site de equipe**, digite **Site do SharePoint para Projeto 1 de campanha**.</span><span class="sxs-lookup"><span data-stu-id="c5438-156">In **Team site description**, type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="c5438-157">Em **Configurações de privacidade**, selecione **Privado – somente membros podem acessar esse site** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-157">In **Privacy settings**, select **Private – only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c5438-158">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="c5438-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="c5438-159">Em seguida, configure a pasta de documentos do site de equipe Projeto 1 de campanha com o rótulo Privado.</span><span class="sxs-lookup"><span data-stu-id="c5438-159">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="c5438-160">Na guia **Projeto 1 de campanha – Página inicial** do navegador, clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-160">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c5438-161">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c5438-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c5438-162">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c5438-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c5438-163">Em **Configurações – Aplicar Rótulo**, selecione **Privado** e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-163">In **Settings-Apply Label**, select **Private**, and click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="c5438-164">Site de equipe de marketing de campanha</span><span class="sxs-lookup"><span data-stu-id="c5438-164">Campaign marketing team site</span></span>

<span data-ttu-id="c5438-165">Para criar um site de equipe do SharePoint Online isolado de nível confidencial para recursos de marketing de campanha, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c5438-165">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="c5438-166">Usando um navegador no computador local, entre no Portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c5438-166">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="c5438-167">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c5438-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c5438-168">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="c5438-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c5438-169">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="c5438-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c5438-170">Em **Nome do site de equipe**, digite **Marketing de campanha**.</span><span class="sxs-lookup"><span data-stu-id="c5438-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="c5438-171">Em **Descrição do site de equipe**, digite **Site do SharePoint para marketing de campanha (confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="c5438-171">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="c5438-172">Em **Configurações de privacidade**, selecione **Privado – somente membros podem acessar esse site** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-172">In **Privacy settings**, select **Private – only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c5438-173">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="c5438-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="c5438-174">Na nova guia **Marketing de campanha** no navegador, na barra de ferramentas, clique no ícone de configurações e depois clique em **Permissões do site**.</span><span class="sxs-lookup"><span data-stu-id="c5438-174">On the new ProjectX-Home tab in your browser, in the tool bar, click the settings icon, and then click Site permissions.</span></span>
    
10. <span data-ttu-id="c5438-175">No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="c5438-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="c5438-176">Na nova guia **Permissões** no navegador, clique em **Configurações de Solicitação de Acesso**.</span><span class="sxs-lookup"><span data-stu-id="c5438-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="c5438-177">Na caixa de diálogo **Configurações de Solicitação de Acesso**, desmarque as caixas de seleção **Permitir que membros compartilhem o site e arquivos e pastas individuais** e **Permitir que membros convidem outras pessoas para o grupo de membros do site**, digite **ITAdmin1 @**<your organization name> **.onmicrosoft.com** em **Enviar todas as solicitações para acesso** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5438-177">In the Access Request Settings dialog box, clear Allow members to share the site and individual files and folders and Allow members to invite others to the site members group (so that all three check boxes are cleared), and click OK.</span></span>
    
13. <span data-ttu-id="c5438-178">Clique em **Membros da campanha de marketing ** na lista.</span><span class="sxs-lookup"><span data-stu-id="c5438-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="c5438-179">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="c5438-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="c5438-180">Na caixa de diálogo **Compartilhar**, digite **Funcionários sênior e estratégicos**, selecione o item e clique em **Compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-180">In the **Share** dialog box, type **IT staff**, select it, and click **Share**.</span></span>
    
16. <span data-ttu-id="c5438-181">Repita as etapas 14 e 15 para o grupo **Equipe de análise** e a conta de usuário **Regular1**.</span><span class="sxs-lookup"><span data-stu-id="c5438-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="c5438-182">Clique no botão Voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="c5438-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="c5438-183">Clique em **Proprietários da campanha de marketing** na lista.</span><span class="sxs-lookup"><span data-stu-id="c5438-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="c5438-184">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="c5438-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="c5438-185">Na caixa de diálogo **Compartilhar**, digite **Equipe de TI**, selecione o item e clique em **Compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-185">In the **Share** dialog box, type **IT staff**, select it, and click **Share**.</span></span>
    
21. <span data-ttu-id="c5438-186">Clique no botão Voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="c5438-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="c5438-187">Feche a guia **Pessoas e Grupos** no navegador, clique na guia **Página inicial da campanha de marketing** no navegador e feche o painel **Permissões de site**.</span><span class="sxs-lookup"><span data-stu-id="c5438-187">Close the People and Groups tab in your browser, click the ProjectX-Home tab in your browser, and then close the Site permissions pane.
</span></span>
    
<span data-ttu-id="c5438-188">Aqui estão os resultados da configuração de permissões:</span><span class="sxs-lookup"><span data-stu-id="c5438-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="c5438-189">O grupo do SharePoint **Membros da campanha de marketing ** contém apenas o grupo **Funcionários sênior e estratégicos** (que contém as contas de usuário Candidato, ChiefOfStaff e Strategic1), o grupo **Marketing de campanha** (que contém a conta de administrador global), o grupo **Equipe de análise** (que contém a conta de usuário DataScientist1) e a conta de usuário **Regular1 **.</span><span class="sxs-lookup"><span data-stu-id="c5438-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="c5438-190">O grupo do SharePoint **Marketing de campanha – Proprietários** contém apenas o grupo **Equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="c5438-190">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="c5438-191">O grupo do SharePoint **Marketing de campanha – Visitantes** não contém grupos ou contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="c5438-191">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="c5438-192">Os membros não podem modificar permissões de nível de site (isso pode ser feito apenas por membros do grupo **Marketing de campanhas – Proprietários**).</span><span class="sxs-lookup"><span data-stu-id="c5438-192">Members cannot modify site-level permissions (this can only be done by members of the ProjectX-Admins group).</span></span>
    
- <span data-ttu-id="c5438-193">Outras contas de usuário não podem acessar o site ou seus recursos, mas podem solicitar o acesso ao site, que enviará um email para a caixa de correio da conta de usuário ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="c5438-193">Other user accounts cannot access the site or its resources, but can request access to the site, which sends an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="c5438-194">Em seguida, configure a pasta de documentos do site de equipe de marketing de campanha com o rótulo Confidencial.</span><span class="sxs-lookup"><span data-stu-id="c5438-194">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="c5438-195">Na guia **Marketing de campanha – Página inicial** do navegador, clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-195">In the **Organization wide–Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c5438-196">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c5438-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c5438-197">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c5438-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c5438-198">Em **Configurações – Aplicar Rótulo**, selecione **Confidencial** e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-198">In **Settings-Apply Label**, select **Sensitive**, and click **Save**.</span></span>
    
<span data-ttu-id="c5438-p103">Em seguida, configure uma política de DLP (prevenção de perda de dados) que notifica os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo Confidencial fora da organização. Essa política de DLP se aplicará a recursos no site de marketing da campanha.</span><span class="sxs-lookup"><span data-stu-id="c5438-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="c5438-201">Na guia **Microsoft Office Home** no navegador, clique no bloco **Segurança&amp; Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="c5438-201">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
2. <span data-ttu-id="c5438-202">Na nova guia **Segurança e&amp; Conformidade** no navegador, clique em **Prevenção de perda de dados > Política**.</span><span class="sxs-lookup"><span data-stu-id="c5438-202">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
3. <span data-ttu-id="c5438-203">No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="c5438-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="c5438-204">No painel **Iniciar com um modelo ou criar uma política personalizada**, clique em **Personalizado** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and click **Next**.</span></span>
    
5. <span data-ttu-id="c5438-205">No painel **Atribuir um nome à política**, digite **Sites de equipe do SharePoint Online de rótulo Confidencial** em **Nome** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and click **Next**.</span></span>
    
6. <span data-ttu-id="c5438-206">No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c5438-207">Na lista de locais, desabilite os locais **Email do Exchange** e **Contas do OneDrive** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and click **Next**.</span></span>
    
8. <span data-ttu-id="c5438-208">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="c5438-209">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Adicionar** na caixa suspensa e clique em **Rótulos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and click **Labels**.</span></span>
    
10. <span data-ttu-id="c5438-210">No painel **Rótulos**, clique em **+ Adicionar**, selecione o rótulo **Confidencial**, clique em **Adicionar** e clique em **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="c5438-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and click **Done**.</span></span>
    
11. <span data-ttu-id="c5438-211">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="c5438-212">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="c5438-213">No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.</span><span class="sxs-lookup"><span data-stu-id="c5438-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="c5438-214">No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.</span><span class="sxs-lookup"><span data-stu-id="c5438-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="c5438-215">Na caixa de texto, digite ou cole o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c5438-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="c5438-p104">Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="c5438-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="c5438-219">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5438-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="c5438-220">No painel **O que deseja fazer se detectarmos informações confidenciais?**, desmarque a caixa de seleção **Impedir que as pessoas compartilhem e restringir o acesso ao conteúdo compartilhado** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and click **Next**.</span></span>
    
18. <span data-ttu-id="c5438-221">No painel **Deseja ativar a política ou testar primeiro?**, clique em **Sim** para ativá-la imediatamente e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes**, turn it on right away, and click **Next**.</span></span>
    
19. <span data-ttu-id="c5438-222">No painel **Examine as configurações**, clique em **Criar** e em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-222">In the **Review your settings pane**, click **Create**, and click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="c5438-223">Site de equipe de estratégia de campanha</span><span class="sxs-lookup"><span data-stu-id="c5438-223">Company strategy team site</span></span>

<span data-ttu-id="c5438-224">Para criar um site de equipe do SharePoint Online isolado no nível altamente confidencial para recursos de estratégia de campanha, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c5438-224">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="c5438-225">Se necessário, use um navegador no computador local e entre no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) usando sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c5438-225">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="c5438-226">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c5438-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c5438-227">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="c5438-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c5438-228">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="c5438-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c5438-229">Em **Nome do site de equipe**, digite **Estratégia da campanha**.</span><span class="sxs-lookup"><span data-stu-id="c5438-229">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="c5438-230">Em **Descrição do site da equipe**, digite **Site do SharePoint para estratégia da campanha (altamente confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="c5438-230">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="c5438-231">Em **Configurações de privacidade**, selecione **Privado – somente membros podem acessar esse site** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-231">In **Privacy settings**, select **Private – only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c5438-232">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="c5438-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="c5438-233">Na nova guia **Estratégia da campanha** no navegador, na barra de ferramentas, clique no ícone de configurações e depois clique em **Permissões do site**.</span><span class="sxs-lookup"><span data-stu-id="c5438-233">On the new **Company strategy** tab in your browser, in the toolbar, click the settings icon, and click **Site permissions**.</span></span>
    
10. <span data-ttu-id="c5438-234">No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="c5438-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="c5438-235">Na nova guia **Permissões** no navegador, clique em **Configurações de Solicitação de Acesso**.</span><span class="sxs-lookup"><span data-stu-id="c5438-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="c5438-236">Na caixa de diálogo **Configurações de Solicitação de Acesso**, desmarque **Permitir que os membros compartilhem o site e arquivos e pastas individuais** e **Permitir que os membros convidem outros para o grupo de membros do site** (de forma que todas as três caixas de seleção estejam desmarcadas) e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5438-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and click **OK**.</span></span>
    
13. <span data-ttu-id="c5438-237">Clique em **Membros da estratégia da campanha** na lista.</span><span class="sxs-lookup"><span data-stu-id="c5438-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="c5438-238">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="c5438-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="c5438-239">Na caixa de diálogo **Compartilhar**, digite **Funcionários sênior e estratégicos**, selecione o item e clique em **Compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-239">In the **Share** dialog box, type **IT staff**, select it, and click **Share**.</span></span>
    
16. <span data-ttu-id="c5438-240">Clique em **Proprietários de Estratégia de Campanha** na lista.</span><span class="sxs-lookup"><span data-stu-id="c5438-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="c5438-241">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="c5438-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="c5438-242">Na caixa de diálogo **Compartilhar**, digite **Equipe de TI**, selecione o item e clique em **Compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-242">In the **Share** dialog box, type **IT staff**, select it, and click **Share**.</span></span>
    
19. <span data-ttu-id="c5438-243">Clique no botão Voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="c5438-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="c5438-244">Feche a guia **Pessoas e Grupos** no navegador, clique na guia **Estratégia de campanha – Página Inicial** no navegador e feche o painel **Permissões do site**.</span><span class="sxs-lookup"><span data-stu-id="c5438-244">Close the People and Groups tab in your browser, click the ProjectX-Home tab in your browser, and then close the Site permissions pane.
</span></span>
    
<span data-ttu-id="c5438-245">Aqui estão os resultados da configuração de permissões:</span><span class="sxs-lookup"><span data-stu-id="c5438-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="c5438-246">O grupo **Membros estratégicos da campanha** do SharePoint contém apenas o grupo **Funcionários sênior e estratégicos** (que contém apenas as contas de usuário Candidato, ChiefOfStaff e Strategic1) e o grupo ** Estratégia da campanha** (que contém a conta de usuário de administrador global).</span><span class="sxs-lookup"><span data-stu-id="c5438-246">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="c5438-247">O grupo do SharePoint **Estratégia da campanha – Proprietários** contém apenas o grupo **Equipe de TI** (que contém apenas as contas de usuário ITAdmin1 e ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="c5438-247">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="c5438-248">O grupo do SharePoint **Estratégia da campanha – Visitantes** não contém grupos ou contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="c5438-248">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="c5438-249">Os membros não podem modificar permissões de nível de site (isso pode ser feito apenas por membros do grupo **Estratégia da campanha – Proprietários**).</span><span class="sxs-lookup"><span data-stu-id="c5438-249">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="c5438-p105">Outras contas de usuário não podem acessar o site ou seus recursos ou solicitar o acesso ao site. As permissões adicionais para o site devem ser feias pelo administrador global ou por um membro do grupo **Estratégia da campanha – Proprietários**.</span><span class="sxs-lookup"><span data-stu-id="c5438-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="c5438-252">Em seguida, configure a pasta de documentos do site de equipe de estratégia da campanha com o rótulo Altamente Confidencial.</span><span class="sxs-lookup"><span data-stu-id="c5438-252">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="c5438-253">Na guia **Estratégia da campanha – Página inicial** do navegador, clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-253">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c5438-254">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c5438-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c5438-255">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c5438-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c5438-256">Em **Configurações – Aplicar Rótulo**, selecione **Altamente Confidencial** e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-256">In **Settings-Apply Label**, select **Highly Confidential**, and click **Save**.</span></span>
    
<span data-ttu-id="c5438-p106">Em seguida, configure uma política de DLP que bloqueia os usuários quando eles compartilham um documento em um site de equipe do SharePoint Online com o rótulo altamente confidencial fora da organização. Essa política de DLP se aplicará a recursos no site de estratégia da campanha.</span><span class="sxs-lookup"><span data-stu-id="c5438-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="c5438-259">Se necessário, use um navegador no computador local e entre no Portal do Office 365 ([https://portal.office.com](https://portal.office.com)) com uma conta que tenha a função de Administrador de Segurança ou Administrador da Empresa.</span><span class="sxs-lookup"><span data-stu-id="c5438-259">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="c5438-260">Na guia **Microsoft Office Home** no navegador, clique no bloco **Segurança&amp; Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="c5438-260">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
3. <span data-ttu-id="c5438-261">Na nova guia **Segurança e&amp; Conformidade** no navegador, clique em **Prevenção de perda de dados > Política**.</span><span class="sxs-lookup"><span data-stu-id="c5438-261">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
4. <span data-ttu-id="c5438-262">No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="c5438-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="c5438-263">No painel **Iniciar com um modelo ou criar uma política personalizada**, clique em **Personalizado** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and click **Next**.</span></span>
    
6. <span data-ttu-id="c5438-264">No painel **Atribuir um nome à política**, digite **Sites de equipe do SharePoint Online de rótulo Altamente Confidencial** em **Nome** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and click **Next**.</span></span>
    
7. <span data-ttu-id="c5438-265">No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c5438-266">Na lista de locais, desabilite os locais **Email do Exchange** e **Contas do OneDrive** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and click **Next**.</span></span>
    
9. <span data-ttu-id="c5438-267">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="c5438-268">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Adicionar** na caixa suspensa e clique em **Rótulos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and click **Labels**.</span></span>
    
11. <span data-ttu-id="c5438-269">No painel **Rótulos**, clique em **+ Adicionar**, selecione o **rótulo Altamente Confidencial**, clique em **Adicionar** e clique em **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="c5438-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential label**, click **Add**, and click **Done**.</span></span>
    
12. <span data-ttu-id="c5438-270">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="c5438-271">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="c5438-272">No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.</span><span class="sxs-lookup"><span data-stu-id="c5438-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="c5438-273">No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.</span><span class="sxs-lookup"><span data-stu-id="c5438-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="c5438-274">Na caixa de texto, digite ou cole o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c5438-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="c5438-p107">Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="c5438-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="c5438-278">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5438-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="c5438-279">No painel **O que deseja fazer se detectarmos informações confidenciais?**, selecione **Exigir uma justificativa de negócios para substituir** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and click **Next**.</span></span>
    
19. <span data-ttu-id="c5438-280">No painel **Deseja ativar a política ou testar primeiro?**, clique em **Sim** para ativá-la imediatamente e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes**, turn it on right away, and click **Next**.</span></span>
    
20. <span data-ttu-id="c5438-281">No painel **Examine as configurações**, clique em **Criar** e em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-281">In the **Review your settings pane**, click **Create**, and click **Close**.</span></span>
    
<span data-ttu-id="c5438-282">Use as instruções em [Ativar o Azure RMS com o centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="c5438-282">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="c5438-283">Depois, configure a Proteção de Informações do Azure com uma nova política e sub-rótulo em escopo para proteção e permissões com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c5438-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="c5438-p108">Entre no Portal do Office 365 com uma conta que tenha a função de Administrador de Segurança ou Administrador da Empresa. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c5438-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c5438-286">Em uma guia separada do navegador, vá para o portal do Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="c5438-286">In a separate tab of your browser, go to the Azure portal (https://portal.azure.com).</span></span>
    
3. <span data-ttu-id="c5438-287">Se esta é a primeira vez que configura a Proteção de Informações do Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="c5438-287">If this is the first time you are configuring Azure Information Protection, see [these instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="c5438-288">No painel de lista, clique em **Mais serviços**, digite **informações** e clique em **Proteção de Informações do Azure**.</span><span class="sxs-lookup"><span data-stu-id="c5438-288">In the list pane, click **More services**, type **information**, and click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="c5438-289">Na folha **Proteção de Informações do Azure**, clique em **Políticas no escopo > + Adicionar uma nova política**.</span><span class="sxs-lookup"><span data-stu-id="c5438-289">On the **Azure Information protection** blade, click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="c5438-290">Digite **CampaignStrategy** em **Nome da política** e **Rótulo para documentos no site da equipe de estratégia da campanha** em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="c5438-290">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="c5438-291">Clique em **Selecionar usuários ou grupos que obtêm essa política > Usuário/Grupos**e selecione **Funcionários sênior e estratégicos**.</span><span class="sxs-lookup"><span data-stu-id="c5438-291">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="c5438-292">Clique em **Selecionar > OK**.</span><span class="sxs-lookup"><span data-stu-id="c5438-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="c5438-293">Para o rótulo **Altamente Confidencial**, clique nas reticências (...) e, em seguida, clique em **Adicionar um sub-rótulo**.</span><span class="sxs-lookup"><span data-stu-id="c5438-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="c5438-294">Digite um nome para o subrótulo em **Nome** e uma descrição do rótulo em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="c5438-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="c5438-295">Em **Definir permissões para documentos e emails que contenham este rótulo**, clique em **Proteger**.</span><span class="sxs-lookup"><span data-stu-id="c5438-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="c5438-296">Na seção **Proteção**, clique em **Azure (chave de nuvem)**.</span><span class="sxs-lookup"><span data-stu-id="c5438-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="c5438-297">Na folha **Proteção**, em **Configurações de proteção**, clique em **+ Adicionar permissões**.</span><span class="sxs-lookup"><span data-stu-id="c5438-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="c5438-298">Na folha **Adicionar permissões**, em **Especificar usuários e grupos**, clique em **+ Procurar no diretório**.</span><span class="sxs-lookup"><span data-stu-id="c5438-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="c5438-299">No painel **Usuários e Grupos do AAD**, selecione **Funcionários sênior e estratégicos** e clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="c5438-300">Em **Escolher permissões da predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo** e **Encaminhar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-300">Under Choose permissions from the preset, clear the Print, Copy and extract content, and Forward check boxes.</span></span>
    
17. <span data-ttu-id="c5438-301">Clique em **OK** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="c5438-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="c5438-302">Na folha **Sub-rótulo**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="c5438-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="c5438-303">Feche a nova folha de política com escopo.</span><span class="sxs-lookup"><span data-stu-id="c5438-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="c5438-304">Na folha **Proteção de Informações do Azure – Políticas em escopo**, clique em **Publicar** e depois em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="c5438-304">On the **Azure Information Protection – Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="c5438-305">Agora você está pronto para começar a criar documentos nestes quatro sites e testar o acesso a eles com várias contas de usuário em sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="c5438-305">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="c5438-306">Para proteger um documento com a Proteção de Informações do Azure e esse novo rótulo, você deve [instalar o cliente de Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em um computador de teste, instalar o Office do portal do Office 365 e entrar no Microsoft Word com uma conta no grupo **Funcionários sênior e estratégicos** de sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="c5438-306">To protect a document with Azure Information Protection and the Highly Confidential label, you must install the Azure Information Protection client on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the C-Suite group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c5438-307">Veja também</span><span class="sxs-lookup"><span data-stu-id="c5438-307">See Also</span></span>

[<span data-ttu-id="c5438-308">Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile</span><span class="sxs-lookup"><span data-stu-id="c5438-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="c5438-309">Defina grupos e usuários para um ambiente de desenvolvimento/teste de uma campanha política</span><span class="sxs-lookup"><span data-stu-id="c5438-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="c5438-310">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="c5438-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c5438-311">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="c5438-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




