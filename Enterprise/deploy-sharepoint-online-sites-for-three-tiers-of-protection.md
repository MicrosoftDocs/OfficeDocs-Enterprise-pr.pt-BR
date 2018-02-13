---
title: "Implantar sites do SharePoint Online para três camadas de proteção"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "Resumo: Criar e configurar sites de equipe do SharePoint Online para diversos níveis de proteção de informações."
ms.openlocfilehash: 4e6e70377f27bcd3cf367aefa1a640188abefc50
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="dec96-103">Implantar sites do SharePoint Online para três camadas de proteção</span><span class="sxs-lookup"><span data-stu-id="dec96-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="dec96-104">**Resumo:** Criar e configurar sites de equipe do SharePoint Online para diversos níveis de proteção de informações.</span><span class="sxs-lookup"><span data-stu-id="dec96-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="dec96-p101">Use as etapas neste artigo para projetar e implantar a linha de base, confidenciais e altamente confidenciais team sites do SharePoint Online. Para obter mais informações sobre esses três camadas de proteção, consulte [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="dec96-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="dec96-107">Sites de equipe do SharePoint Online da linha de base</span><span class="sxs-lookup"><span data-stu-id="dec96-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="dec96-p102">Proteção de linha de base inclui os dois sites de equipe públicos e particulares. Sites de equipe públicas podem ser descobertos e acessados por qualquer pessoa na organização. Sites privadas só podem ser descobertos e acessados pelos membros do grupo do Office 365 associadas ao site de equipe. Ambos os tipos de sites de equipe permitem que os membros compartilhe o site com outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="dec96-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="dec96-112">Público</span><span class="sxs-lookup"><span data-stu-id="dec96-112">Public</span></span>

<span data-ttu-id="dec96-113">Para criar um site de equipe do SharePoint Online da linha de base com e permissões de acesso público, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dec96-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="dec96-p103">Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="dec96-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dec96-116">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="dec96-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dec96-117">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="dec96-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dec96-118">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="dec96-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dec96-119">Em **nome do Site**, digite um nome para o site de equipe pública.</span><span class="sxs-lookup"><span data-stu-id="dec96-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="dec96-120">Em **Descrição do site de equipe**, digite uma descrição do objetivo do site.</span><span class="sxs-lookup"><span data-stu-id="dec96-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="dec96-121">Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dec96-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dec96-122">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="dec96-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="dec96-123">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="dec96-123">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online público.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="dec96-125">Particular</span><span class="sxs-lookup"><span data-stu-id="dec96-125">Private</span></span>

<span data-ttu-id="dec96-126">Para criar um site de equipe do SharePoint Online da linha de base com permissões e acesso privado, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dec96-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="dec96-p104">Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="dec96-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dec96-129">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="dec96-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dec96-130">Na guia **SharePoint** nova no seu navegador, clique em **Criar site +**.</span><span class="sxs-lookup"><span data-stu-id="dec96-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dec96-131">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="dec96-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dec96-132">Em **nome do Site**, digite um nome para o site de equipe particular.</span><span class="sxs-lookup"><span data-stu-id="dec96-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="dec96-133">Em **Descrição do site de equipe,** digite uma descrição do objetivo do site.</span><span class="sxs-lookup"><span data-stu-id="dec96-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="dec96-134">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dec96-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dec96-135">Sobre o **que você deseja adicionar?** painel, em **Adicionar membros**, digite os nomes das contas de usuário que têm acesso a este site de equipe particular.</span><span class="sxs-lookup"><span data-stu-id="dec96-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="dec96-136">Quando você terminar adicionando o conjunto inicial de membros para o site, clique em **Concluir**</span><span class="sxs-lookup"><span data-stu-id="dec96-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="dec96-137">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="dec96-137">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online privado.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="dec96-139">Sites de equipe do SharePoint Online confidenciais</span><span class="sxs-lookup"><span data-stu-id="dec96-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="dec96-140">Um site de equipe do SharePoint Online confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio de associação nos grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.</span><span class="sxs-lookup"><span data-stu-id="dec96-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="dec96-141">Para criar um site de equipe isolado, há duas etapas principais.</span><span class="sxs-lookup"><span data-stu-id="dec96-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="dec96-142">Etapa 1: Criar o seu site isolado</span><span class="sxs-lookup"><span data-stu-id="dec96-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="dec96-143">Para criar o seu site de equipe isolado, você precisa determinar:</span><span class="sxs-lookup"><span data-stu-id="dec96-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="dec96-144">Seus grupos do SharePoint e níveis de permissão.</span><span class="sxs-lookup"><span data-stu-id="dec96-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="dec96-145">O conjunto de grupos de acesso que serão membros de seus grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dec96-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="dec96-146">O conjunto recomendado de grupos de acesso é um para membros do site, um para os visualizadores de site e outra para os administradores de sites.</span><span class="sxs-lookup"><span data-stu-id="dec96-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="dec96-147">Se você usará grupos aninhados dentro dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="dec96-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="dec96-148">Por exemplo, os níveis de permissão e estrutura de grupo recomendada semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="dec96-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="dec96-149">**Grupo do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="dec96-149">**SharePoint group**</span></span>|<span data-ttu-id="dec96-150">**Nível de permissão**</span><span class="sxs-lookup"><span data-stu-id="dec96-150">**Permission level**</span></span>|<span data-ttu-id="dec96-151">**Grupo de acesso (exemplos)**</span><span class="sxs-lookup"><span data-stu-id="dec96-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="dec96-152">[nome do site] Membros</span><span class="sxs-lookup"><span data-stu-id="dec96-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="dec96-153">Editar</span><span class="sxs-lookup"><span data-stu-id="dec96-153">Edit</span></span>  <br/> |<span data-ttu-id="dec96-154">[nome do site] Membros</span><span class="sxs-lookup"><span data-stu-id="dec96-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="dec96-155">[nome do site] Visitantes</span><span class="sxs-lookup"><span data-stu-id="dec96-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="dec96-156">Leitura</span><span class="sxs-lookup"><span data-stu-id="dec96-156">Read</span></span>  <br/> |<span data-ttu-id="dec96-157">[nome do site] Visualizadores</span><span class="sxs-lookup"><span data-stu-id="dec96-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="dec96-158">[nome do site] Proprietários</span><span class="sxs-lookup"><span data-stu-id="dec96-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="dec96-159">Controle total</span><span class="sxs-lookup"><span data-stu-id="dec96-159">Full control</span></span>  <br/> |<span data-ttu-id="dec96-160">[nome do site] Administradores</span><span class="sxs-lookup"><span data-stu-id="dec96-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="dec96-p105">Os grupos do SharePoint e níveis de permissão são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="dec96-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="dec96-163">Para obter detalhes sobre o processo de design, consulte [Design um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="dec96-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="dec96-164">Etapa 2: Implantar seu site isolado</span><span class="sxs-lookup"><span data-stu-id="dec96-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="dec96-165">Para implantar seu site isolado, você precisa primeiro:</span><span class="sxs-lookup"><span data-stu-id="dec96-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="dec96-166">Determine as contas de usuário e grupos a serem adicionados a cada um dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="dec96-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="dec96-167">Criar os grupos de acesso e adicione os membros de grupo e usuário.</span><span class="sxs-lookup"><span data-stu-id="dec96-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="dec96-168">Para obter etapas detalhadas, consulte **Phase 1** de [implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="dec96-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="dec96-169">Em seguida, você cria o site da equipe do SharePoint Online com estas etapas.</span><span class="sxs-lookup"><span data-stu-id="dec96-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="dec96-p106">Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="dec96-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dec96-172">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="dec96-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dec96-173">Na guia **SharePoint** novo do seu navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="dec96-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dec96-174">Na página **criar um site** , clique em **sites de equipe**.</span><span class="sxs-lookup"><span data-stu-id="dec96-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dec96-175">Em **nome do Site**, digite um nome para o site de equipe particular.</span><span class="sxs-lookup"><span data-stu-id="dec96-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="dec96-176">Na **Descrição do site de equipe**, digite uma descrição opcional.</span><span class="sxs-lookup"><span data-stu-id="dec96-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="dec96-177">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="dec96-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dec96-178">Sobre o **que você deseja adicionar?** painel, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="dec96-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="dec96-179">Em seguida, do novo site de equipe do SharePoint Online, configure permissões com estas etapas.</span><span class="sxs-lookup"><span data-stu-id="dec96-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="dec96-p107">Determinar o nome Principal de usuário (UPN) do administrador de TI ou outra pessoa de quem será responsável para responder e lidando com as solicitações de acesso ao site (belindan@contoso.com é um exemplo de um UPN). Gravar esse UPN aqui: _.</span><span class="sxs-lookup"><span data-stu-id="dec96-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="dec96-182">Na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.</span><span class="sxs-lookup"><span data-stu-id="dec96-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="dec96-183">No painel de **permissões do Site** , clique em **configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="dec96-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="dec96-184">Na guia **permissões** novo do navegador, clique em **Configurações de solicitação de acesso**.</span><span class="sxs-lookup"><span data-stu-id="dec96-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="dec96-185">Na caixa de diálogo **Configurações de solicitações de acesso** :</span><span class="sxs-lookup"><span data-stu-id="dec96-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="dec96-186">Desmarque as caixas de seleção **Permitir que os membros para compartilhar o site e arquivos e pastas individuais** e **Permitir que os membros para convidar outras pessoas ao grupo de membros do site** .</span><span class="sxs-lookup"><span data-stu-id="dec96-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="dec96-187">Digite o UPN do seu administrador de TI da etapa 1 na **Enviar todas as solicitações de acesso**.</span><span class="sxs-lookup"><span data-stu-id="dec96-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="dec96-188">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="dec96-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="dec96-189">Na guia **permissões** do seu navegador, clique em **membros do [nome do site]** na lista.</span><span class="sxs-lookup"><span data-stu-id="dec96-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="dec96-190">Em **pessoas e grupos**, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="dec96-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="dec96-191">Na caixa de diálogo **compartilhamento** , digite o nome do seu grupo de acesso de membros do site para este site, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="dec96-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="dec96-192">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="dec96-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="dec96-193">Na lista, clique em **[nome do site] proprietários** .</span><span class="sxs-lookup"><span data-stu-id="dec96-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="dec96-194">Em **pessoas e grupos**, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="dec96-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="dec96-195">Na caixa de diálogo **compartilhamento** , digite o nome do grupo de acesso de administradores de site para este site, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="dec96-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="dec96-196">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="dec96-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="dec96-197">Clique em **visitantes do [nome do site]** na lista.</span><span class="sxs-lookup"><span data-stu-id="dec96-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="dec96-198">Em **pessoas e grupos**, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="dec96-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="dec96-199">Na caixa de diálogo **compartilhamento** , digite o nome do grupo de acesso ao site visualizadores para esse site, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="dec96-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="dec96-200">Feche a guia **permissões** do navegador.</span><span class="sxs-lookup"><span data-stu-id="dec96-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="dec96-201">Os resultados dessas configurações de permissão são:</span><span class="sxs-lookup"><span data-stu-id="dec96-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="dec96-202">Os **proprietários do [nome do site]** grupo do SharePoint contém o grupo de acesso de administradores de site, no quais todos os membros têm o nível de permissão **controle total** .</span><span class="sxs-lookup"><span data-stu-id="dec96-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="dec96-203">Os **membros do [nome do site]** grupo do SharePoint contém o grupo de acesso de membros do site, no quais todos os membros têm o nível de permissão **Editar** .</span><span class="sxs-lookup"><span data-stu-id="dec96-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="dec96-204">**Visitantes do [nome do site]** grupo do SharePoint contém site grupo visualizadores de acesso, no quais todos os membros têm o nível de permissão de **leitura** .</span><span class="sxs-lookup"><span data-stu-id="dec96-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="dec96-205">A capacidade de membros convidar outros membros está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="dec96-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="dec96-206">A capacidade de membros solicitar acesso está habilitada.</span><span class="sxs-lookup"><span data-stu-id="dec96-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="dec96-207">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="dec96-207">Here is your resulting configuration.</span></span>
  
![Proteção de nível confidencial para um site de equipe isolado do SharePoint Online.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="dec96-209">Os membros do site, por meio de associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança com os recursos do site.</span><span class="sxs-lookup"><span data-stu-id="dec96-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="dec96-210">Altamente confidenciais sites de equipe do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="dec96-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="dec96-211">Um site de equipe do SharePoint Online altamente confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio de associação nos grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.</span><span class="sxs-lookup"><span data-stu-id="dec96-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="dec96-212">Para criar um site de equipe isolado informações altamente confidenciais e colaboração, há duas etapas principais.</span><span class="sxs-lookup"><span data-stu-id="dec96-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="dec96-213">Etapa 1: Criar o seu site isolado</span><span class="sxs-lookup"><span data-stu-id="dec96-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="dec96-214">Para criar o seu site de equipe isolado, você precisa determinar:</span><span class="sxs-lookup"><span data-stu-id="dec96-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="dec96-215">Seus grupos do SharePoint e níveis de permissão.</span><span class="sxs-lookup"><span data-stu-id="dec96-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="dec96-216">O conjunto de grupos de acesso que serão membros de seus grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="dec96-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="dec96-217">O conjunto recomendado de grupos de acesso é um para membros do site, um para os visualizadores de site e outra para os administradores de sites.</span><span class="sxs-lookup"><span data-stu-id="dec96-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="dec96-218">Se você usará grupos aninhados dentro dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="dec96-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="dec96-219">Por exemplo, os níveis de permissão e estrutura de grupo recomendada semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="dec96-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="dec96-220">**Grupo do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="dec96-220">**SharePoint group**</span></span>|<span data-ttu-id="dec96-221">**Nível de permissão**</span><span class="sxs-lookup"><span data-stu-id="dec96-221">**Permission level**</span></span>|<span data-ttu-id="dec96-222">**Grupo de acesso (exemplos)**</span><span class="sxs-lookup"><span data-stu-id="dec96-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="dec96-223">[nome do site] Membros</span><span class="sxs-lookup"><span data-stu-id="dec96-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="dec96-224">Editar</span><span class="sxs-lookup"><span data-stu-id="dec96-224">Edit</span></span>  <br/> |<span data-ttu-id="dec96-225">[nome do site] Membros</span><span class="sxs-lookup"><span data-stu-id="dec96-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="dec96-226">[nome do site] Visitantes</span><span class="sxs-lookup"><span data-stu-id="dec96-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="dec96-227">Leitura</span><span class="sxs-lookup"><span data-stu-id="dec96-227">Read</span></span>  <br/> |<span data-ttu-id="dec96-228">[nome do site] Visualizadores</span><span class="sxs-lookup"><span data-stu-id="dec96-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="dec96-229">[nome do site] Proprietários</span><span class="sxs-lookup"><span data-stu-id="dec96-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="dec96-230">Controle total</span><span class="sxs-lookup"><span data-stu-id="dec96-230">Full control</span></span>  <br/> |<span data-ttu-id="dec96-231">[nome do site] Administradores</span><span class="sxs-lookup"><span data-stu-id="dec96-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="dec96-p108">Os grupos do SharePoint e níveis de permissão são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="dec96-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="dec96-234">Para obter detalhes sobre o processo de design, consulte [Design um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="dec96-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="dec96-235">Etapa 2: Implantar seu site isolado</span><span class="sxs-lookup"><span data-stu-id="dec96-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="dec96-236">Para implantar seu site isolado, você precisa primeiro:</span><span class="sxs-lookup"><span data-stu-id="dec96-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="dec96-237">Determinar os membros de grupo e usuário de cada um dos seus grupos de acesso</span><span class="sxs-lookup"><span data-stu-id="dec96-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="dec96-238">Criar os grupos de acesso e adicionar os membros de grupo e usuário</span><span class="sxs-lookup"><span data-stu-id="dec96-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="dec96-239">Criar um site de equipe isolado que usa os grupos de acesso</span><span class="sxs-lookup"><span data-stu-id="dec96-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="dec96-240">Para obter etapas detalhadas, consulte [Deploy um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="dec96-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="dec96-241">Os resultados das configurações de permissão são:</span><span class="sxs-lookup"><span data-stu-id="dec96-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="dec96-242">Os **proprietários do [nome do site]** grupo do SharePoint contém o grupo de acesso de administradores de site, no quais todos os membros têm o nível de permissão **controle total** .</span><span class="sxs-lookup"><span data-stu-id="dec96-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="dec96-243">Os **membros do [nome do site]** grupo do SharePoint contém o grupo de acesso de membros do site, no quais todos os membros têm o nível de permissão **Editar** .</span><span class="sxs-lookup"><span data-stu-id="dec96-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="dec96-244">**Visitantes do [nome do site]** grupo do SharePoint contém site grupo visualizadores de acesso, no quais todos os membros têm o nível de permissão de **leitura** .</span><span class="sxs-lookup"><span data-stu-id="dec96-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="dec96-245">A capacidade de membros convidar outros membros está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="dec96-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="dec96-246">A capacidade de membros solicitar acesso está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="dec96-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="dec96-247">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="dec96-247">Here is your resulting configuration.</span></span>
  
![Proteção com alto nível de confidencialidade para um site de equipe isolado do SharePoint Online.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="dec96-249">Os membros do site, por meio de associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança com os recursos do site.</span><span class="sxs-lookup"><span data-stu-id="dec96-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="dec96-250">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="dec96-250">Next step</span></span>

[<span data-ttu-id="dec96-251">Proteger os arquivos do SharePoint Online com o Office 365 rótulos e DLP</span><span class="sxs-lookup"><span data-stu-id="dec96-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="dec96-252">Veja também</span><span class="sxs-lookup"><span data-stu-id="dec96-252">See Also</span></span>

[<span data-ttu-id="dec96-253">Proteja arquivos e sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="dec96-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="dec96-254">Proteger sites do SharePoint Online em um ambiente de desenvolvimento e teste</span><span class="sxs-lookup"><span data-stu-id="dec96-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="dec96-255">Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil</span><span class="sxs-lookup"><span data-stu-id="dec96-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="dec96-256">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="dec96-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




