---
title: Implantar sites do SharePoint Online para três camadas de proteção
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
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: 'Resumo: Criar e configurar sites de equipe do SharePoint Online para diversos níveis de proteção de informações.'
ms.openlocfilehash: ddeb1885cbc74be6e7098660eb1d9906d43739fd
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="778f6-103">Implantar sites do SharePoint Online para três camadas de proteção</span><span class="sxs-lookup"><span data-stu-id="778f6-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="778f6-104">**Resumo:** Criar e configurar sites de equipe do SharePoint Online para diversos níveis de proteção de informações.</span><span class="sxs-lookup"><span data-stu-id="778f6-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="778f6-p101">Use as etapas neste artigo para projetar e implantar sites de equipe do SharePoint Online de linha de base, confidenciais e altamente confidenciais. Para obter mais informações sobre essas três camadas de proteção, consulte [Arquivos e sites do SharePoint Online seguros](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="778f6-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="778f6-107">Sites de equipe do SharePoint Online de linha de base</span><span class="sxs-lookup"><span data-stu-id="778f6-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="778f6-p102">A proteção de linha de base inclui os sites de equipe públicos e privados. Os sites de equipe públicos podem ser descobertos e acessados por qualquer pessoa na organização. Os sites privados podem ser descobertos e acessados somente por membros do grupo do Office 365 associado ao site de equipe. Esses dois tipos de sites de equipe permitem que os membros compartilhem o site com outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="778f6-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="778f6-112">Público</span><span class="sxs-lookup"><span data-stu-id="778f6-112">Public</span></span>

<span data-ttu-id="778f6-113">Para criar um site de equipe do SharePoint Online de linha de base com permissões e acesso público, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="778f6-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="778f6-p103">Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="778f6-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="778f6-116">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="778f6-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="778f6-117">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="778f6-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="778f6-118">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="778f6-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="778f6-119">Em **Nome do site**, digite um nome para o site de equipe público.</span><span class="sxs-lookup"><span data-stu-id="778f6-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="778f6-120">Em **Descrição do site de equipe**, digite uma descrição do objetivo do site.</span><span class="sxs-lookup"><span data-stu-id="778f6-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="778f6-121">Nas **configurações de privacidade**, selecione **pública - qualquer pessoa da organização pode acessar esse site**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="778f6-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="778f6-122">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="778f6-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="778f6-123">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="778f6-123">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online público.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="778f6-125">Private</span><span class="sxs-lookup"><span data-stu-id="778f6-125">Private</span></span>

<span data-ttu-id="778f6-126">Para criar um site de equipe do SharePoint Online de linha de base com permissões e acesso privado, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="778f6-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="778f6-p104">Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="778f6-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="778f6-129">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="778f6-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="778f6-130">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="778f6-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="778f6-131">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="778f6-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="778f6-132">Em **Nome do site**, digite um nome para o site de equipe privado.</span><span class="sxs-lookup"><span data-stu-id="778f6-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="778f6-133">Em **Descrição do site de equipe,** digite uma descrição do objetivo do site.</span><span class="sxs-lookup"><span data-stu-id="778f6-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="778f6-134">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="778f6-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="778f6-135">No painel **Quem você deseja adicionar?**, em **Adicionar membros**, digite os nomes das contas de usuário que têm acesso a esse site de equipe privado.</span><span class="sxs-lookup"><span data-stu-id="778f6-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="778f6-136">Quando você terminar adicionando o conjunto inicial de membros para o site, clique em **Concluir**</span><span class="sxs-lookup"><span data-stu-id="778f6-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="778f6-137">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="778f6-137">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online privado.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="778f6-139">Sites de equipe do SharePoint Online confidenciais</span><span class="sxs-lookup"><span data-stu-id="778f6-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="778f6-140">Um site de equipe do SharePoint Online confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio da associação em grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.</span><span class="sxs-lookup"><span data-stu-id="778f6-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="778f6-141">Para criar um site de equipe isolado, há duas etapas principais.</span><span class="sxs-lookup"><span data-stu-id="778f6-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="778f6-142">Etapa 1: Projetar o site isolado</span><span class="sxs-lookup"><span data-stu-id="778f6-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="778f6-143">Para projetar o site de equipe isolado, você precisa determinar:</span><span class="sxs-lookup"><span data-stu-id="778f6-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="778f6-144">Seus níveis de permissão e grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="778f6-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="778f6-145">O conjunto de grupos de acesso que serão membros de seus grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="778f6-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="778f6-146">O conjunto recomendado de grupos de acesso é um para membros do site, um para os visualizadores de site e outra para os administradores de sites.</span><span class="sxs-lookup"><span data-stu-id="778f6-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="778f6-147">Se você usará grupos aninhados dentro de seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="778f6-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="778f6-148">Por exemplo, os níveis de permissão e estrutura de grupo recomendados têm essa aparência:</span><span class="sxs-lookup"><span data-stu-id="778f6-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="778f6-149">**Grupo do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="778f6-149">**SharePoint group**</span></span>|<span data-ttu-id="778f6-150">**Nível de permissão**</span><span class="sxs-lookup"><span data-stu-id="778f6-150">**Permission level**</span></span>|<span data-ttu-id="778f6-151">**Grupo de acesso (exemplos)**</span><span class="sxs-lookup"><span data-stu-id="778f6-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="778f6-152">Membros do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="778f6-153">Editar</span><span class="sxs-lookup"><span data-stu-id="778f6-153">Edit</span></span>  <br/> |<span data-ttu-id="778f6-154">Membros do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="778f6-155">Visitantes do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="778f6-156">Ler</span><span class="sxs-lookup"><span data-stu-id="778f6-156">Read</span></span>  <br/> |<span data-ttu-id="778f6-157">Visualizadores do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="778f6-158">Proprietários do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="778f6-159">Controle total</span><span class="sxs-lookup"><span data-stu-id="778f6-159">Full control</span></span>  <br/> |<span data-ttu-id="778f6-160">Administradores do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="778f6-p105">Os níveis de permissão e grupos do SharePoint são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="778f6-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="778f6-163">Para obter os detalhes do processo de design, consulte [Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="778f6-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="778f6-164">Etapa 2: Implantar o site isolado</span><span class="sxs-lookup"><span data-stu-id="778f6-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="778f6-165">Para implantar seu site isolado, primeiro você precisa:</span><span class="sxs-lookup"><span data-stu-id="778f6-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="778f6-166">Determinar as contas de usuário e os grupos a serem adicionados a cada um dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="778f6-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="778f6-167">Criar os grupos de acesso e adicionar os membros de usuário e grupo.</span><span class="sxs-lookup"><span data-stu-id="778f6-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="778f6-168">Para obter as etapas detalhadas, consulte a **Fase 1** de [Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="778f6-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="778f6-169">Em seguida, você cria o site da equipe do SharePoint Online com estas etapas.</span><span class="sxs-lookup"><span data-stu-id="778f6-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="778f6-p106">Entrar no portal do Office 365 com uma conta que também será usada para administrar o site da equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="778f6-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="778f6-172">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="778f6-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="778f6-173">Na guia **SharePoint** novo do seu navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="778f6-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="778f6-174">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="778f6-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="778f6-175">Em **Nome do site**, digite um nome para o site de equipe privado.</span><span class="sxs-lookup"><span data-stu-id="778f6-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="778f6-176">Na **Descrição do site de equipe**, digite uma descrição opcional.</span><span class="sxs-lookup"><span data-stu-id="778f6-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="778f6-177">Nas **configurações de privacidade**, selecione **privada - somente membros podem acessar esse site**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="778f6-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="778f6-178">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="778f6-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="778f6-179">Em seguida, no novo site de equipe do SharePoint Online, configure as permissões com estas etapas.</span><span class="sxs-lookup"><span data-stu-id="778f6-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="778f6-p107">Determinar o nome Principal de usuário (UPN) do administrador de TI ou outra pessoa de quem será responsável para responder e lidando com as solicitações de acesso ao site (belindan@contoso.com é um exemplo de um UPN). Gravar esse UPN aqui: _.</span><span class="sxs-lookup"><span data-stu-id="778f6-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="778f6-182">Na barra de ferramentas, clique no ícone configurações e, em seguida, clique em **permissões do Site**.</span><span class="sxs-lookup"><span data-stu-id="778f6-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="778f6-183">No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="778f6-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="778f6-184">Na nova guia **Permissões** do navegador, clique em **Configurações de Solicitação de Acesso**.</span><span class="sxs-lookup"><span data-stu-id="778f6-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="778f6-185">Na caixa de diálogo **Configurações de Solicitações de Acesso**:</span><span class="sxs-lookup"><span data-stu-id="778f6-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="778f6-186">Desmarque as caixas de seleção **Permitir que os membros compartilhem o site e arquivos e pastas individuais** e **Permitir que os membros convidem outras pessoas para o grupo de membros do site**.</span><span class="sxs-lookup"><span data-stu-id="778f6-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="778f6-187">Digite o UPN do seu administrador de TI da etapa 1 em **Enviar todas as solicitações de acesso**.</span><span class="sxs-lookup"><span data-stu-id="778f6-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="778f6-188">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="778f6-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="778f6-189">Na guia **Permissões** do navegador, clique em **Membros do [nome do site]** na lista.</span><span class="sxs-lookup"><span data-stu-id="778f6-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="778f6-190">Em **pessoas e grupos**, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="778f6-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="778f6-191">Na caixa de diálogo **compartilhamento** , digite o nome do seu grupo de acesso de membros do site para este site, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="778f6-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="778f6-192">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="778f6-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="778f6-193">Na lista, clique em **[nome do site] proprietários** .</span><span class="sxs-lookup"><span data-stu-id="778f6-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="778f6-194">Em **pessoas e grupos**, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="778f6-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="778f6-195">Na caixa de diálogo **compartilhamento** , digite o nome do grupo de acesso de administradores de site para este site, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="778f6-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="778f6-196">Clique no botão voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="778f6-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="778f6-197">Clique em **visitantes do [nome do site]** na lista.</span><span class="sxs-lookup"><span data-stu-id="778f6-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="778f6-198">Em **pessoas e grupos**, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="778f6-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="778f6-199">Na caixa de diálogo **compartilhamento** , digite o nome do grupo de acesso ao site visualizadores para esse site, selecioná-la e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="778f6-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="778f6-200">Feche a guia **Permissões** do navegador.</span><span class="sxs-lookup"><span data-stu-id="778f6-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="778f6-201">Os resultados dessas configurações de permissão são:</span><span class="sxs-lookup"><span data-stu-id="778f6-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="778f6-202">O grupo do SharePoint **Proprietários do [nome do site]** contém o grupo de acesso de administradores de site, em que todos os membros têm o nível de permissão **Controle total**.</span><span class="sxs-lookup"><span data-stu-id="778f6-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="778f6-203">O grupo do SharePoint **Membros do [nome do site]** contém o grupo de acesso de membros de site, em que todos os membros têm o nível de permissão **Editar**.</span><span class="sxs-lookup"><span data-stu-id="778f6-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="778f6-204">O grupo do SharePoint **Visitantes do [nome do site]** contém o grupo de acesso de visualizadores de site, em que todos os membros têm o nível de permissão **Ler**.</span><span class="sxs-lookup"><span data-stu-id="778f6-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="778f6-205">A capacidade de os membros convidarem outros membros está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="778f6-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="778f6-206">A capacidade de não membros solicitarem o acesso está habilitada.</span><span class="sxs-lookup"><span data-stu-id="778f6-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="778f6-207">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="778f6-207">Here is your resulting configuration.</span></span>
  
![Proteção de nível confidencial para um site de equipe isolado do SharePoint Online.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="778f6-209">Os membros do site, por meio da associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança nos recursos do site.</span><span class="sxs-lookup"><span data-stu-id="778f6-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="778f6-210">Sites de equipe do SharePoint Online altamente confidenciais</span><span class="sxs-lookup"><span data-stu-id="778f6-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="778f6-211">Um site de equipe do SharePoint Online altamente confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio da associação em grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.</span><span class="sxs-lookup"><span data-stu-id="778f6-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="778f6-212">Para criar um site de equipe isolado para colaboração e informações altamente confidenciais, há duas etapas principais.</span><span class="sxs-lookup"><span data-stu-id="778f6-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="778f6-213">Etapa 1: Projetar o site isolado</span><span class="sxs-lookup"><span data-stu-id="778f6-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="778f6-214">Para projetar o site de equipe isolado, você precisa determinar:</span><span class="sxs-lookup"><span data-stu-id="778f6-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="778f6-215">Seus níveis de permissão e grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="778f6-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="778f6-216">O conjunto de grupos de acesso que serão membros de seus grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="778f6-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="778f6-217">O conjunto recomendado de grupos de acesso é um para membros do site, um para os visualizadores de site e outra para os administradores de sites.</span><span class="sxs-lookup"><span data-stu-id="778f6-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="778f6-218">Se você usará grupos aninhados dentro de seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="778f6-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="778f6-219">Por exemplo, os níveis de permissão e estrutura de grupo recomendados têm essa aparência:</span><span class="sxs-lookup"><span data-stu-id="778f6-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="778f6-220">**Grupo do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="778f6-220">**SharePoint group**</span></span>|<span data-ttu-id="778f6-221">**Nível de permissão**</span><span class="sxs-lookup"><span data-stu-id="778f6-221">**Permission level**</span></span>|<span data-ttu-id="778f6-222">**Grupo de acesso (exemplos)**</span><span class="sxs-lookup"><span data-stu-id="778f6-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="778f6-223">Membros do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="778f6-224">Editar</span><span class="sxs-lookup"><span data-stu-id="778f6-224">Edit</span></span>  <br/> |<span data-ttu-id="778f6-225">Membros do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="778f6-226">Visitantes do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="778f6-227">Ler</span><span class="sxs-lookup"><span data-stu-id="778f6-227">Read</span></span>  <br/> |<span data-ttu-id="778f6-228">Visualizadores do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="778f6-229">Proprietários do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="778f6-230">Controle total</span><span class="sxs-lookup"><span data-stu-id="778f6-230">Full control</span></span>  <br/> |<span data-ttu-id="778f6-231">Administradores do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="778f6-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="778f6-p108">Os níveis de permissão e grupos do SharePoint são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="778f6-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="778f6-234">Para obter os detalhes do processo de design, consulte [Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="778f6-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="778f6-235">Etapa 2: Implantar o site isolado</span><span class="sxs-lookup"><span data-stu-id="778f6-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="778f6-236">Para implantar seu site isolado, primeiro você precisa:</span><span class="sxs-lookup"><span data-stu-id="778f6-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="778f6-237">Determinar os membros de grupo e usuário de cada um dos seus grupos de acesso</span><span class="sxs-lookup"><span data-stu-id="778f6-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="778f6-238">Criar os grupos de acesso e adicionar os membros de grupo e usuário</span><span class="sxs-lookup"><span data-stu-id="778f6-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="778f6-239">Criar um site de equipe isolado que usa os grupos de acesso</span><span class="sxs-lookup"><span data-stu-id="778f6-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="778f6-240">Para obter as etapas detalhadas, consulte [Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="778f6-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="778f6-241">Os resultados das configurações de permissão são:</span><span class="sxs-lookup"><span data-stu-id="778f6-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="778f6-242">O grupo do SharePoint **Proprietários do [nome do site]** contém o grupo de acesso de administradores de site, em que todos os membros têm o nível de permissão **Controle total**.</span><span class="sxs-lookup"><span data-stu-id="778f6-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="778f6-243">O grupo do SharePoint **Membros do [nome do site]** contém o grupo de acesso de membros de site, em que todos os membros têm o nível de permissão **Editar**.</span><span class="sxs-lookup"><span data-stu-id="778f6-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="778f6-244">O grupo do SharePoint **Visitantes do [nome do site]** contém o grupo de acesso de visualizadores de site, em que todos os membros têm o nível de permissão **Ler**.</span><span class="sxs-lookup"><span data-stu-id="778f6-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="778f6-245">A capacidade de os membros convidarem outros membros está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="778f6-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="778f6-246">A capacidade de não membros solicitarem o acesso está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="778f6-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="778f6-247">Aqui está a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="778f6-247">Here is your resulting configuration.</span></span>
  
![Proteção com alto nível de confidencialidade para um site de equipe isolado do SharePoint Online.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="778f6-249">Os membros do site, por meio da associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança nos recursos do site.</span><span class="sxs-lookup"><span data-stu-id="778f6-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="778f6-250">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="778f6-250">Next step</span></span>

[<span data-ttu-id="778f6-251">Proteger os arquivos do SharePoint Online com o Office 365 rótulos e DLP</span><span class="sxs-lookup"><span data-stu-id="778f6-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="778f6-252">Confira também</span><span class="sxs-lookup"><span data-stu-id="778f6-252">See Also</span></span>

[<span data-ttu-id="778f6-253">Proteger sites e arquivos do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="778f6-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="778f6-254">Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="778f6-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="778f6-255">Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile</span><span class="sxs-lookup"><span data-stu-id="778f6-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="778f6-256">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="778f6-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




