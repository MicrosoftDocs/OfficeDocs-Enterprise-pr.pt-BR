---
title: Implantar sites do SharePoint Online para três camadas de proteção
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/05/2018
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
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: 'Resumo: Crie e configure sites de equipe do SharePoint Online para vários níveis de proteção de informações.'
ms.openlocfilehash: 6103675941802fcdee50c06ac3212d90f95c6d35
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915616"
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="6de23-103">Implantar sites do SharePoint Online para três camadas de proteção</span><span class="sxs-lookup"><span data-stu-id="6de23-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="6de23-104">**Resumo:** Crie e configure sites de equipe do SharePoint Online para vários níveis de proteção de informações.</span><span class="sxs-lookup"><span data-stu-id="6de23-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="6de23-p101">Use as etapas neste artigo para projetar e implantar sites de equipe do SharePoint Online de linha de base, confidenciais e altamente confidenciais. Para obter mais informações sobre essas três camadas de proteção, consulte [Arquivos e sites do SharePoint Online seguros](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="6de23-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="6de23-107">Sites de equipe do SharePoint Online de linha de base</span><span class="sxs-lookup"><span data-stu-id="6de23-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="6de23-p102">A proteção de linha de base inclui os sites de equipe públicos e privados. Os sites de equipe públicos podem ser descobertos e acessados por qualquer pessoa na organização. Os sites privados podem ser descobertos e acessados somente por membros do grupo do Office 365 associado ao site de equipe. Esses dois tipos de sites de equipe permitem que os membros compartilhem o site com outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="6de23-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="6de23-112">Público</span><span class="sxs-lookup"><span data-stu-id="6de23-112">Public</span></span>

<span data-ttu-id="6de23-113">Para criar um site de equipe do SharePoint Online de linha de base com permissões e acesso público, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6de23-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="6de23-p103">Entre no Portal do Office 365 com uma conta que também será usada para administrar o site de equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6de23-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6de23-116">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6de23-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6de23-117">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="6de23-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6de23-118">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="6de23-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6de23-119">Em **Nome do site**, digite um nome para o site de equipe público.</span><span class="sxs-lookup"><span data-stu-id="6de23-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="6de23-120">Em **Descrição do site de equipe**, digite uma descrição do objetivo do site.</span><span class="sxs-lookup"><span data-stu-id="6de23-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="6de23-121">Em **Configurações de privacidade**, selecione **Público – qualquer pessoa na organização pode acessar esse site** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="6de23-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6de23-122">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="6de23-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="6de23-123">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="6de23-123">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online público.](media/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="6de23-125">Privado</span><span class="sxs-lookup"><span data-stu-id="6de23-125">Private</span></span>

<span data-ttu-id="6de23-126">Para criar um site de equipe do SharePoint Online de linha de base com permissões e acesso privado, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6de23-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="6de23-p104">Entre no Portal do Office 365 com uma conta que também será usada para administrar o site de equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6de23-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6de23-129">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6de23-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6de23-130">Na nova guia **SharePoint** no navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="6de23-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6de23-131">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="6de23-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6de23-132">Em **Nome do site**, digite um nome para o site de equipe privado.</span><span class="sxs-lookup"><span data-stu-id="6de23-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="6de23-133">Em **Descrição do site de equipe,** digite uma descrição do objetivo do site.</span><span class="sxs-lookup"><span data-stu-id="6de23-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="6de23-134">Em **Configurações de privacidade**, selecione **Privado – somente membros podem acessar esse site** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="6de23-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6de23-135">No painel **Quem você deseja adicionar?**, em **Adicionar membros**, digite os nomes das contas de usuário que têm acesso a esse site de equipe privado.</span><span class="sxs-lookup"><span data-stu-id="6de23-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="6de23-136">Quando você terminar de adicionar o conjunto inicial de membros ao site, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="6de23-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="6de23-137">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="6de23-137">Here is your resulting configuration.</span></span>
  
![Proteção de nível de linha de base para um site de equipe do SharePoint Online privado.](media/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="6de23-139">Sites de equipe do SharePoint Online confidenciais</span><span class="sxs-lookup"><span data-stu-id="6de23-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="6de23-140">Um site de equipe do SharePoint Online confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio da associação em grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.</span><span class="sxs-lookup"><span data-stu-id="6de23-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="6de23-141">Para criar um site de equipe isolado, siga estas duas etapas principais.</span><span class="sxs-lookup"><span data-stu-id="6de23-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="6de23-142">Etapa 1: Projetar o site isolado</span><span class="sxs-lookup"><span data-stu-id="6de23-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="6de23-143">Para projetar o site de equipe isolado, você precisa determinar:</span><span class="sxs-lookup"><span data-stu-id="6de23-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="6de23-144">Seus níveis de permissão e grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6de23-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="6de23-145">O conjunto de grupos de acesso que serão membros dos grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6de23-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="6de23-146">O conjunto de grupos de acesso recomendado é um para os membros do site, um para os visualizadores do site e um para os administradores do site.</span><span class="sxs-lookup"><span data-stu-id="6de23-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="6de23-147">Se você usará grupos aninhados dentro de seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="6de23-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="6de23-148">Por exemplo, os níveis de permissão e estrutura de grupo recomendados têm essa aparência:</span><span class="sxs-lookup"><span data-stu-id="6de23-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="6de23-149">**Grupo do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="6de23-149">**SharePoint group**</span></span>|<span data-ttu-id="6de23-150">**Nível de permissão**</span><span class="sxs-lookup"><span data-stu-id="6de23-150">**Permission level**</span></span>|<span data-ttu-id="6de23-151">**Grupo de acesso (exemplos)**</span><span class="sxs-lookup"><span data-stu-id="6de23-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6de23-152">Membros do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="6de23-153">Editar</span><span class="sxs-lookup"><span data-stu-id="6de23-153">Edit</span></span>  <br/> |<span data-ttu-id="6de23-154">Membros do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="6de23-155">Visitantes do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="6de23-156">Ler</span><span class="sxs-lookup"><span data-stu-id="6de23-156">Read</span></span>  <br/> |<span data-ttu-id="6de23-157">Visualizadores do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="6de23-158">Proprietários do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="6de23-159">Controle total</span><span class="sxs-lookup"><span data-stu-id="6de23-159">Full control</span></span>  <br/> |<span data-ttu-id="6de23-160">Administradores do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="6de23-p105">Os níveis de permissão e grupos do SharePoint são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="6de23-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="6de23-163">Para obter os detalhes do processo de design, consulte [Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="6de23-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="6de23-164">Etapa 2: Implantar o site isolado</span><span class="sxs-lookup"><span data-stu-id="6de23-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="6de23-165">Para implantar seu site isolado, primeiro você precisa:</span><span class="sxs-lookup"><span data-stu-id="6de23-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="6de23-166">Determinar as contas de usuário e os grupos a serem adicionados a cada um dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="6de23-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="6de23-167">Criar os grupos de acesso e adicionar os membros de usuário e grupo.</span><span class="sxs-lookup"><span data-stu-id="6de23-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="6de23-168">Para obter as etapas detalhadas, consulte a **Fase 1** de [Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="6de23-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="6de23-169">Em seguida, crie o site de equipe do SharePoint Online com estas etapas.</span><span class="sxs-lookup"><span data-stu-id="6de23-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="6de23-p106">Entre no Portal do Office 365 com uma conta que também será usada para administrar o site de equipe do SharePoint Online (um administrador do SharePoint Online). Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="6de23-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="6de23-172">Na lista de blocos, clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6de23-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="6de23-173">Na nova guia **SharePoint** do navegador, clique em **+ Criar site**.</span><span class="sxs-lookup"><span data-stu-id="6de23-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="6de23-174">Na página **Criar um site**, clique em **Site de equipe**.</span><span class="sxs-lookup"><span data-stu-id="6de23-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="6de23-175">Em **Nome do site**, digite um nome para o site de equipe privado.</span><span class="sxs-lookup"><span data-stu-id="6de23-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="6de23-176">Na descrição de **Site de equipe**, digite uma descrição opcional.</span><span class="sxs-lookup"><span data-stu-id="6de23-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="6de23-177">Em **Configurações de privacidade**, selecione **Privado – somente membros podem acessar esse site** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="6de23-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="6de23-178">No painel **Quem você deseja adicionar?**, clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="6de23-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="6de23-179">Em seguida, no novo site de equipe do SharePoint Online, configure as permissões com estas etapas.</span><span class="sxs-lookup"><span data-stu-id="6de23-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="6de23-p107">Determine o nome UPN do administrador de TI ou outra pessoa que será responsável por responder e resolver as solicitações de acesso ao site (elzap@contoso.com é um exemplo de um UPN). Anote esse UPN aqui: ![](./media/Common-Images/TableLine.png).</span><span class="sxs-lookup"><span data-stu-id="6de23-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: ![](./media/Common-Images/TableLine.png).</span></span>
    
2. <span data-ttu-id="6de23-182">Na barra de ferramentas, clique no ícone Configurações e, em seguida, clique em **Permissões do site**.</span><span class="sxs-lookup"><span data-stu-id="6de23-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="6de23-183">No painel **Permissões do site**, clique em **Configurações de permissões avançadas**.</span><span class="sxs-lookup"><span data-stu-id="6de23-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="6de23-184">Na nova guia **Permissões** do navegador, clique em **Configurações de Solicitação de Acesso**.</span><span class="sxs-lookup"><span data-stu-id="6de23-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="6de23-185">Na caixa de diálogo **Configurações de Solicitações de Acesso**:</span><span class="sxs-lookup"><span data-stu-id="6de23-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="6de23-186">Desmarque as caixas de seleção **Permitir que os membros compartilhem o site e arquivos e pastas individuais** e **Permitir que os membros convidem outras pessoas para o grupo de membros do site**.</span><span class="sxs-lookup"><span data-stu-id="6de23-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="6de23-187">Digite o UPN do seu administrador de TI da etapa 1 em **Enviar todas as solicitações de acesso**.</span><span class="sxs-lookup"><span data-stu-id="6de23-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="6de23-188">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="6de23-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="6de23-189">Na guia **Permissões** do navegador, clique em **Membros do [nome do site]** na lista.</span><span class="sxs-lookup"><span data-stu-id="6de23-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="6de23-190">Em **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="6de23-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="6de23-191">Na caixa de diálogo **Compartilhar**, digite o nome do grupo de acesso dos membros do seu site para esse site, selecione-o e clique em **Compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="6de23-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="6de23-192">Clique no botão Voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="6de23-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="6de23-193">Clique em **Proprietários do [nome do site]** na lista.</span><span class="sxs-lookup"><span data-stu-id="6de23-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="6de23-194">Em **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="6de23-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="6de23-195">Na caixa de diálogo **Compartilhar**, digite o nome do grupo de acesso dos administradores do site para esse site, selecione-o e clique em **Compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="6de23-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="6de23-196">Clique no botão Voltar de seu navegador.</span><span class="sxs-lookup"><span data-stu-id="6de23-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="6de23-197">Clique em **Visitantes do [nome do site]** na lista.</span><span class="sxs-lookup"><span data-stu-id="6de23-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="6de23-198">Em **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="6de23-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="6de23-199">Na caixa de diálogo **Compartilhar**, digite o nome do grupo de acesso dos visualizadores do site para esse site, selecione-o e clique em **Compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="6de23-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="6de23-200">Feche a guia **Permissões** do navegador.</span><span class="sxs-lookup"><span data-stu-id="6de23-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="6de23-201">Os resultados dessas configurações de permissão são:</span><span class="sxs-lookup"><span data-stu-id="6de23-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="6de23-202">O grupo do SharePoint **Proprietários do [nome do site]** contém o grupo de acesso de administradores de site, em que todos os membros têm o nível de permissão **Controle total**.</span><span class="sxs-lookup"><span data-stu-id="6de23-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="6de23-203">O grupo do SharePoint **Membros do [nome do site]** contém o grupo de acesso de membros de site, em que todos os membros têm o nível de permissão **Editar**.</span><span class="sxs-lookup"><span data-stu-id="6de23-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="6de23-204">O grupo do SharePoint **Visitantes do [nome do site]** contém o grupo de acesso de visualizadores de site, em que todos os membros têm o nível de permissão **Ler**.</span><span class="sxs-lookup"><span data-stu-id="6de23-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="6de23-205">A capacidade de os membros convidarem outros membros está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6de23-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="6de23-206">A capacidade de não membros solicitarem o acesso está habilitada.</span><span class="sxs-lookup"><span data-stu-id="6de23-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="6de23-207">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="6de23-207">Here is your resulting configuration.</span></span>
  
![Proteção de nível confidencial para um site de equipe isolado do SharePoint Online.](media/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="6de23-209">Os membros do site, por meio da associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança nos recursos do site.</span><span class="sxs-lookup"><span data-stu-id="6de23-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="6de23-210">Sites de equipe do SharePoint Online altamente confidenciais</span><span class="sxs-lookup"><span data-stu-id="6de23-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="6de23-211">Um site de equipe do SharePoint Online altamente confidencial é um site de equipe isolado, o que significa que as permissões são controladas por meio da associação em grupos do SharePoint, em vez de ser membro do grupo do Office 365 associado ao site de equipe.</span><span class="sxs-lookup"><span data-stu-id="6de23-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="6de23-212">Para criar um site de equipe isolado para colaboração e informações altamente confidenciais, há duas etapas principais.</span><span class="sxs-lookup"><span data-stu-id="6de23-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="6de23-213">Etapa 1: Projetar o site isolado</span><span class="sxs-lookup"><span data-stu-id="6de23-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="6de23-214">Para projetar o site de equipe isolado, você precisa determinar:</span><span class="sxs-lookup"><span data-stu-id="6de23-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="6de23-215">Seus níveis de permissão e grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6de23-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="6de23-216">O conjunto de grupos de acesso que serão membros dos grupos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6de23-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="6de23-217">O conjunto de grupos de acesso recomendado é um para os membros do site, um para os visualizadores do site e um para os administradores do site.</span><span class="sxs-lookup"><span data-stu-id="6de23-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="6de23-218">Se você usará grupos aninhados dentro de seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="6de23-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="6de23-219">Por exemplo, os níveis de permissão e estrutura de grupo recomendados têm essa aparência:</span><span class="sxs-lookup"><span data-stu-id="6de23-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="6de23-220">**Grupo do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="6de23-220">**SharePoint group**</span></span>|<span data-ttu-id="6de23-221">**Nível de permissão**</span><span class="sxs-lookup"><span data-stu-id="6de23-221">**Permission level**</span></span>|<span data-ttu-id="6de23-222">**Grupo de acesso (exemplos)**</span><span class="sxs-lookup"><span data-stu-id="6de23-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="6de23-223">Membros do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="6de23-224">Editar</span><span class="sxs-lookup"><span data-stu-id="6de23-224">Edit</span></span>  <br/> |<span data-ttu-id="6de23-225">Membros do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="6de23-226">Visitantes do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="6de23-227">Ler</span><span class="sxs-lookup"><span data-stu-id="6de23-227">Read</span></span>  <br/> |<span data-ttu-id="6de23-228">Visualizadores do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="6de23-229">Proprietários do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="6de23-230">Controle total</span><span class="sxs-lookup"><span data-stu-id="6de23-230">Full control</span></span>  <br/> |<span data-ttu-id="6de23-231">Administradores do [nome do site]</span><span class="sxs-lookup"><span data-stu-id="6de23-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="6de23-p108">Os níveis de permissão e grupos do SharePoint são criados por padrão para um site de equipe. Você precisa determinar os nomes dos seus grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="6de23-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="6de23-234">Para obter os detalhes do processo de design, consulte [Projetar um site de equipe do SharePoint Online isolado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="6de23-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="6de23-235">Etapa 2: Implantar o site isolado</span><span class="sxs-lookup"><span data-stu-id="6de23-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="6de23-236">Para implantar seu site isolado, primeiro você precisa:</span><span class="sxs-lookup"><span data-stu-id="6de23-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="6de23-237">Determinar os membros do grupo e usuário de cada um dos grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="6de23-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="6de23-238">Criar os grupos de acesso e adicionar os membros de usuário e grupo.</span><span class="sxs-lookup"><span data-stu-id="6de23-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="6de23-239">Criar um site de equipe isolado que usa os grupos de acesso.</span><span class="sxs-lookup"><span data-stu-id="6de23-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="6de23-240">Para obter as etapas detalhadas, confira [Implantar um site de equipe do SharePoint Online isolado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="6de23-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="6de23-241">Os resultados das configurações de permissão são:</span><span class="sxs-lookup"><span data-stu-id="6de23-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="6de23-242">O grupo do SharePoint **Proprietários do [nome do site]** contém o grupo de acesso de administradores de site, em que todos os membros têm o nível de permissão **Controle total**.</span><span class="sxs-lookup"><span data-stu-id="6de23-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="6de23-243">O grupo do SharePoint **Membros do [nome do site]** contém o grupo de acesso de membros de site, em que todos os membros têm o nível de permissão **Editar**.</span><span class="sxs-lookup"><span data-stu-id="6de23-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="6de23-244">O grupo do SharePoint **Visitantes do [nome do site]** contém o grupo de acesso de visualizadores de site, em que todos os membros têm o nível de permissão **Ler**.</span><span class="sxs-lookup"><span data-stu-id="6de23-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="6de23-245">A capacidade de os membros convidarem outros membros está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6de23-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="6de23-246">A capacidade de não membros solicitarem o acesso está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6de23-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="6de23-247">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="6de23-247">Here is your resulting configuration.</span></span>
  
![Proteção com alto nível de confidencialidade para um site de equipe isolado do SharePoint Online.](media/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="6de23-249">Os membros do site, por meio da associação de grupo em um dos grupos de acesso, agora podem colaborar com segurança nos recursos do site.</span><span class="sxs-lookup"><span data-stu-id="6de23-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="6de23-250">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="6de23-250">Next step</span></span>

[<span data-ttu-id="6de23-251">Proteger arquivos do SharePoint Online com DLP e rótulos do Office 365</span><span class="sxs-lookup"><span data-stu-id="6de23-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="6de23-252">Confira também</span><span class="sxs-lookup"><span data-stu-id="6de23-252">See also</span></span>

[<span data-ttu-id="6de23-253">Proteger sites e arquivos do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6de23-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="6de23-254">Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="6de23-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="6de23-255">Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile</span><span class="sxs-lookup"><span data-stu-id="6de23-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="6de23-256">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="6de23-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




