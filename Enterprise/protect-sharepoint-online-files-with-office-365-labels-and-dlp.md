---
title: "Proteger os arquivos do SharePoint Online com o Office 365 rótulos e DLP"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: "Resumo: Aplica Office 365 rótulos e dados perda prevention (DLP) políticas para sites de equipe do SharePoint Online com vários níveis de proteção das informações."
ms.openlocfilehash: 502a899c586114644bb59a2d55ca388c819f7777
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="5be04-103">Proteger os arquivos do SharePoint Online com o Office 365 rótulos e DLP</span><span class="sxs-lookup"><span data-stu-id="5be04-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="5be04-104">**Resumo:** Aplica Office 365 rótulos e dados perda prevention (DLP) políticas para sites de equipe do SharePoint Online com vários níveis de proteção das informações.</span><span class="sxs-lookup"><span data-stu-id="5be04-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="5be04-p101">Use as etapas neste artigo para projetar e implantar o Office 365 rótulos e políticas DLP da linha de base, confidenciais e altamente confidenciais SharePoint Online para sites de equipe. Para obter mais informações sobre esses três camadas de proteção, consulte [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="5be04-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="5be04-107">Rótulos do Office 365 para seus sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5be04-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="5be04-108">Existem três fases à criação e, em seguida, atribuir o Office 365 etiquetas aos sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5be04-108">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="5be04-109">Fase 1: Determinar os nomes de rótulo do Office 365</span><span class="sxs-lookup"><span data-stu-id="5be04-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="5be04-p102">Nesta fase, você deve determinar os nomes de seus rótulos do Office 365 para os quatro níveis de proteção de informações aplicado a sites de equipe do SharePoint Online. A tabela a seguir lista os nomes recomendados para cada nível.</span><span class="sxs-lookup"><span data-stu-id="5be04-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="5be04-112">**Nível de proteção de sites de equipe do SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="5be04-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="5be04-113">**Nome de rótulo**</span><span class="sxs-lookup"><span data-stu-id="5be04-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5be04-114">Linha de base-públicos</span><span class="sxs-lookup"><span data-stu-id="5be04-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="5be04-115">Público interno</span><span class="sxs-lookup"><span data-stu-id="5be04-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="5be04-116">Linha de base-privado</span><span class="sxs-lookup"><span data-stu-id="5be04-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="5be04-117">Particular</span><span class="sxs-lookup"><span data-stu-id="5be04-117">Private</span></span>  <br/> |
|<span data-ttu-id="5be04-118">Confidenciais</span><span class="sxs-lookup"><span data-stu-id="5be04-118">Sensitive</span></span>  <br/> |<span data-ttu-id="5be04-119">Confidenciais</span><span class="sxs-lookup"><span data-stu-id="5be04-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="5be04-120">Altamente confidenciais</span><span class="sxs-lookup"><span data-stu-id="5be04-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="5be04-121">Altamente confidenciais</span><span class="sxs-lookup"><span data-stu-id="5be04-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="5be04-122">Fase 2: Criar os rótulos do Office 365</span><span class="sxs-lookup"><span data-stu-id="5be04-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="5be04-123">Nesta fase, você pode cria e publica seus determinados rótulos para os diferentes níveis de proteção das informações.</span><span class="sxs-lookup"><span data-stu-id="5be04-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="5be04-124">Para criar os rótulos, você pode usar o Centro de administração do Office 365 ou o Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5be04-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="5be04-125">Crie rótulos do Office 365 com o Centro de administração do Office 365</span><span class="sxs-lookup"><span data-stu-id="5be04-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="5be04-p103">Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="5be04-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="5be04-128">Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="5be04-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="5be04-129">Na guia novo **Centro de administração do Office** do seu navegador, clique em **centrais de Admin > segurança &amp; conformidade**.</span><span class="sxs-lookup"><span data-stu-id="5be04-129">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="5be04-130">Do novo **Home - segurança &amp; conformidade** guia do navegador, clique em **classificações > rótulos**.</span><span class="sxs-lookup"><span data-stu-id="5be04-130">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="5be04-131">Da **Home > rótulos** painel, clique em **criar um rótulo**.</span><span class="sxs-lookup"><span data-stu-id="5be04-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="5be04-132">No painel de **nome de seu rótulo** , digite o nome do rótulo e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-132">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5be04-133">No painel de **configurações de rótulo** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="5be04-134">No painel **Revise suas configurações** , clique em **criar este rótulo**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-134">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="5be04-135">Repita as etapas 5 a 8 para seus rótulos adicionais.</span><span class="sxs-lookup"><span data-stu-id="5be04-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="5be04-136">Crie rótulos do Office 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="5be04-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="5be04-137">[Conectar para a segurança do Office 365 &amp; usando o PowerShell remoto do Centro de conformidade](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) e especifique as credenciais de uma conta que tenha a função de administrador de segurança ou administrador da empresa.</span><span class="sxs-lookup"><span data-stu-id="5be04-137">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="5be04-138">Preencher a lista de nomes de rótulo e, em seguida, execute estes comandos no prompt de comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5be04-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="5be04-139">Em seguida, execute estas etapas para publicar as novas etiquetas do Office 365.</span><span class="sxs-lookup"><span data-stu-id="5be04-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="5be04-140">Da **Home > rótulos** a segurança do painel &amp; Centro de conformidade, clique em **Publicar rótulos**.</span><span class="sxs-lookup"><span data-stu-id="5be04-140">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="5be04-141">No painel **Choose rótulos para publicar** , clique em **rótulos de escolher para publicar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="5be04-142">No painel **Choose rótulos** , clique em **Adicionar** e selecione todas as quatro rótulos.</span><span class="sxs-lookup"><span data-stu-id="5be04-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="5be04-143">Clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="5be04-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="5be04-144">No painel **Choose rótulos para publicar** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="5be04-145">No painel **Choose locais** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="5be04-146">No painel de **sua política de nome** , digite um nome para seu conjunto de etiquetas em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5be04-147">No painel **Revise suas configurações** , clique em **rótulos de publicar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-147">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="5be04-148">Fase 3: Aplicar os rótulos do Office 365 aos seus sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5be04-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="5be04-149">Use estas etapas para aplicar os rótulos do Office 365 para as pastas de documentos dos sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5be04-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="5be04-150">Na guia **Página inicial do Microsoft Office** do seu navegador, clique no lado do **SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="5be04-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="5be04-151">Na guia **SharePoint** nova no seu navegador, clique em um site que precisa de um rótulo do Office 365 atribuído.</span><span class="sxs-lookup"><span data-stu-id="5be04-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="5be04-152">Em uma nova guia de site do SharePoint do seu navegador, clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="5be04-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="5be04-153">Clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="5be04-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="5be04-154">Em **permissões e gerenciamento**, clique em **rótulo aplicar a itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="5be04-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="5be04-155">Em **Configurações se aplicam rótulo**, selecione o rótulo apropriado e, em seguida, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-155">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="5be04-156">Feche a guia para o site do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5be04-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="5be04-157">Repita as etapas 3 a 8 para atribuir o Office 365 rótulos aos seus sites do SharePoint Online adicionais.</span><span class="sxs-lookup"><span data-stu-id="5be04-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="5be04-158">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="5be04-158">Here is your resulting configuration.</span></span>
  
![Rótulos do Office 365 para os quatro tipos de sites de equipe do SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="5be04-160">Políticas de DLP para seus sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5be04-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="5be04-161">Use estas etapas para configurar uma política de DLP que notifica os usuários quando eles compartilham um documento em um site de equipe confidenciais SharePoint Online fora da organização.</span><span class="sxs-lookup"><span data-stu-id="5be04-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="5be04-162">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="5be04-162">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="5be04-163">No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.</span><span class="sxs-lookup"><span data-stu-id="5be04-163">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="5be04-164">No painel de **prevenção de perda de dados** , clique em **+ para criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="5be04-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="5be04-165">No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="5be04-166">No painel de **sua política de nome** , digite o nome para a política de DLP nível confidencial em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-166">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="5be04-167">No painel **Choose locais** , clique em **Deixe-me escolher locais específicos**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5be04-168">Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5be04-169">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="5be04-170">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="5be04-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="5be04-171">No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="5be04-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="5be04-172">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="5be04-173">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="5be04-174">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, clique em **Personalizar a dica e email**.</span><span class="sxs-lookup"><span data-stu-id="5be04-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="5be04-175">No painel de **dicas de política personalizar e notificações por email** , clique em **Personalizar o texto da dica de política**.</span><span class="sxs-lookup"><span data-stu-id="5be04-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="5be04-176">Na caixa de texto, digite ou cole o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="5be04-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="5be04-p104">Para compartilhar com um usuário fora da organização, baixe o arquivo e, em seguida, abri-lo. Clique em arquivo, em seguida, proteger documento e, em seguida, criptografar com senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="5be04-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="5be04-180">Como alternativa, digite ou cole em seu próprio dica de política que instrua os usuários sobre como compartilhar um arquivo de fora da sua organização.</span><span class="sxs-lookup"><span data-stu-id="5be04-180">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="5be04-181">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5be04-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="5be04-182">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, desmarque a caixa de seleção **bloquear pessoas de compartilhamento e restringir o acesso ao conteúdo compartilhado** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="5be04-183">No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="5be04-184">No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-184">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="5be04-185">Aqui está a sua configuração resultante para sites de equipe do SharePoint Online confidenciais.</span><span class="sxs-lookup"><span data-stu-id="5be04-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![A política DLP para um site de equipe isolado do SharePoint Online usando o rótulo Confidencial do Office 365.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="5be04-187">Em seguida, execute estas etapas para configurar uma política DLP que bloqueia usuários quando eles compartilham um documento em um site de equipe altamente confidenciais SharePoint Online fora da organização.</span><span class="sxs-lookup"><span data-stu-id="5be04-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="5be04-188">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no **segurança &amp; conformidade** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="5be04-188">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="5be04-189">No novo **segurança &amp; conformidade** no seu navegador, clique em **prevenção de perda de dados > política**.</span><span class="sxs-lookup"><span data-stu-id="5be04-189">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="5be04-190">No painel de **prevenção de perda de dados** , clique em **+ para criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="5be04-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="5be04-191">No **começar com um modelo ou criar uma política personalizada** painel, clique em **personalizado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="5be04-192">No painel de **sua política de nome** , digite o nome para a política de DLP nível altamente confidencial em **nome**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="5be04-193">No painel **Choose locais** , clique em **Deixe-me escolher locais específicos**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5be04-194">Na lista de locais, desabilitar os locais de **contas do OneDrive** e de **email do Exchange** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5be04-195">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="5be04-196">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Adicionar** na caixa suspensa e, em seguida, clique em **rótulos**.</span><span class="sxs-lookup"><span data-stu-id="5be04-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="5be04-197">No painel de **rótulos** , clique em **+ Adicionar**, selecione o rótulo **Altamente confidenciais** , clique em **Adicionar**e, em seguida, clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="5be04-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="5be04-198">No painel de **Escolher os tipos de conteúdo para proteger** , clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="5be04-199">No painel de **Personalizar os tipos de informações confidenciais que você queira proteger** , clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="5be04-200">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, clique em **Personalizar a dica e email**.</span><span class="sxs-lookup"><span data-stu-id="5be04-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="5be04-201">No painel de **dicas de política personalizar e notificações por email** , clique em **Personalizar o texto da dica de política**.</span><span class="sxs-lookup"><span data-stu-id="5be04-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="5be04-202">Na caixa de texto, digite ou cole o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="5be04-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="5be04-p105">Para compartilhar com um usuário fora da organização, baixe o arquivo e, em seguida, abri-lo. Clique em arquivo, em seguida, proteger documento e, em seguida, criptografar com senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="5be04-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="5be04-206">Como alternativa, digite ou cole em seu próprio dica de política que instrua os usuários sobre como compartilhar um arquivo de fora da sua organização.</span><span class="sxs-lookup"><span data-stu-id="5be04-206">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="5be04-207">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5be04-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="5be04-208">No **o que você deseja fazer se podemos detectar informações confidenciais?** painel, selecione **exigir uma justificativa comercial para substituir**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="5be04-209">No **você deseja ativar as coisas política ou teste out primeiro?** painel, clique em **Sim, ativá-lo imediatamente**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="5be04-210">No painel **Revise suas configurações** , clique em **criar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="5be04-210">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="5be04-211">Aqui está a sua configuração resultante para sites de equipe do SharePoint Online alta confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="5be04-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![A política DLP para um site de equipe isolado do SharePoint Online usando o rótulo Altamente Confidencial do Office 365.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="5be04-213">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="5be04-213">Next step</span></span>

[<span data-ttu-id="5be04-214">Proteger os arquivos do SharePoint Online com proteção de informações do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="5be04-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="5be04-215">See Also</span><span class="sxs-lookup"><span data-stu-id="5be04-215">See Also</span></span>

[<span data-ttu-id="5be04-216">Proteja arquivos e sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5be04-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="5be04-217">Proteger sites do SharePoint Online em um ambiente de desenvolvimento e teste</span><span class="sxs-lookup"><span data-stu-id="5be04-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="5be04-218">Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil</span><span class="sxs-lookup"><span data-stu-id="5be04-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="5be04-219">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="5be04-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


