---
title: Proteger arquivos do SharePoint Online com DLP e rótulos do Office 365
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
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 'Resumo: Aplique rótulos do Office 365 e políticas de DLP (prevenção de perda de dados) aos sites de equipe do SharePoint Online com vários níveis de proteção de informações.'
ms.openlocfilehash: 52617e43f5c1bcb2ab958e751734a2f948ceba37
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="9c48b-103">Proteger arquivos do SharePoint Online com DLP e rótulos do Office 365</span><span class="sxs-lookup"><span data-stu-id="9c48b-103">Protect SharePoint Online files with Office 365 labels and Data Loss Prevention</span></span>

 <span data-ttu-id="9c48b-104">**Resumo:** Aplique rótulos do Office 365 e políticas de DLP (prevenção de perda de dados) aos sites de equipe do SharePoint Online com vários níveis de proteção de informações.</span><span class="sxs-lookup"><span data-stu-id="9c48b-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="9c48b-p101">Use as etapas neste artigo para projetar e implantar políticas de DLP e rótulos do Office 365 para sites de equipe do SharePoint Online de linha de base, confidenciais e altamente confidenciais. Para obter mais informações sobre essas três camadas de proteção, consulte [Arquivos e sites do SharePoint Online seguros](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="9c48b-p101">Use the steps in this article to design and deploy Office 365 labels and Data Loss Prevention (DLP) policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="9c48b-107">Rótulos do Office 365 para seus sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c48b-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="9c48b-108">Há três etapas para criar e atribuir rótulos do Office 365 a sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c48b-108">You must complete the following three phases when creating and assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="9c48b-109">Etapa 1: Determinar os nomes de rótulo do Office 365</span><span class="sxs-lookup"><span data-stu-id="9c48b-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="9c48b-p102">Nesta fase, você determina os nomes dos rótulos do Office 365 para os quatro níveis de proteção de informações aplicados a sites de equipe do SharePoint Online. A tabela a seguir lista os nomes recomendados para cada nível.</span><span class="sxs-lookup"><span data-stu-id="9c48b-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="9c48b-112">**Nível de proteção do site de equipe do SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="9c48b-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="9c48b-113">**Nome do rótulo**</span><span class="sxs-lookup"><span data-stu-id="9c48b-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9c48b-114">Linha de base público</span><span class="sxs-lookup"><span data-stu-id="9c48b-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="9c48b-115">Público interno</span><span class="sxs-lookup"><span data-stu-id="9c48b-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="9c48b-116">Linha de base privado</span><span class="sxs-lookup"><span data-stu-id="9c48b-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="9c48b-117">Private</span><span class="sxs-lookup"><span data-stu-id="9c48b-117">Private</span></span>  <br/> |
|<span data-ttu-id="9c48b-118">Confidencial</span><span class="sxs-lookup"><span data-stu-id="9c48b-118">Sensitive</span></span>  <br/> |<span data-ttu-id="9c48b-119">Confidencial</span><span class="sxs-lookup"><span data-stu-id="9c48b-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="9c48b-120">Altamente Confidencial</span><span class="sxs-lookup"><span data-stu-id="9c48b-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="9c48b-121">Altamente Confidencial</span><span class="sxs-lookup"><span data-stu-id="9c48b-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="9c48b-122">Fase 2: Criar os rótulos do Office 365</span><span class="sxs-lookup"><span data-stu-id="9c48b-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="9c48b-123">Nesta fase, você cria e publica seus determinados rótulos para os diferentes níveis de proteção de informações.</span><span class="sxs-lookup"><span data-stu-id="9c48b-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="9c48b-124">Para criar os rótulos, você pode usar o Centro de administração do Office 365 ou o Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c48b-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="9c48b-125">Criar rótulos do Office 365 com o Centro de administração do Office 365</span><span class="sxs-lookup"><span data-stu-id="9c48b-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="9c48b-p103">Entre no Portal do Office 365 com uma conta que tenha a função de Administrador de Segurança ou Administrador da Empresa. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="9c48b-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="9c48b-128">Na guia **Microsoft Office Home**, clique no bloco **Administração**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="9c48b-129">Na nova guia **Centro de Administração do Office** do navegador, clique em **Centros de Administração > Segurança&amp; e Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-129">From the new Office Admin center tab of your browser, click Admin centers > Security & Compliance.</span></span>
    
4. <span data-ttu-id="9c48b-130">Na nova guia **Início – Segurança &amp;e Conformidade** do navegador, clique em **Classificações > Rótulos**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-130">From the new Home – Security & Compliance tab of your browser, click Classifications > Labels.</span></span>
    
5. <span data-ttu-id="9c48b-131">No painel **Início > Rótulos**, clique em **Criar um rótulo**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="9c48b-132">No painel **Atribuir nome ao seu rótulo**, digite o nome do rótulo e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-132">On the **Name your label** pane, type the name of the label, and click **Next**.</span></span>
    
7. <span data-ttu-id="9c48b-133">No painel **Configurações do rótulo**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="9c48b-134">No painel **Examine as configurações**, clique em **Criar este rótulo** e clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-134">On the **Review your settings** pane, click **Create this label**, and click **Close**.</span></span>
    
9. <span data-ttu-id="9c48b-135">Repita as etapas de 5 a 8 para os rótulos adicionais.</span><span class="sxs-lookup"><span data-stu-id="9c48b-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="9c48b-136">Criar rótulos do Office 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c48b-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="9c48b-137">[Conecte-se ao Centro de Segurança e Conformidade do Office 365 &amp;usando o PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) remoto e especifique as credenciais da conta que têm a função de Administrador de Segurança ou Administrador da Empresa.</span><span class="sxs-lookup"><span data-stu-id="9c48b-137">Connect to the Office 365 Security & Compliance Center using remote PowerShell and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="9c48b-138">Preencha a lista de nomes de rótulo e execute esses comandos no prompt de comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9c48b-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="9c48b-139">Em seguida, use estas etapas para publicar os novos rótulos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9c48b-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="9c48b-140">No painel **Início > Rótulos** no Centro de Segurança&amp; e Conformidade, clique em** Publicar rótulos**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-140">From the Home > Labels pane in the Security & Compliance Center, click Publish labels.</span></span>
    
2. <span data-ttu-id="9c48b-141">No painel **Escolher rótulos para publicar**, clique em **Escolher rótulos para publicar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="9c48b-142">No painel **Escolher rótulos**, clique em **Adicionar** e selecione todos os quatro rótulos.</span><span class="sxs-lookup"><span data-stu-id="9c48b-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="9c48b-143">Clique em **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="9c48b-144">No painel **Escolher rótulos para publicar**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="9c48b-145">No painel **Escolher locais**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="9c48b-146">No painel **Atribuir um nome à política**, digite um nome para o conjunto de rótulos em **Nome** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and click **Next**.</span></span>
    
8. <span data-ttu-id="9c48b-147">No painel **Examine as configurações**, clique em **Publicar rótulos** e clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-147">On the **Review your settings** pane, click **Publish labels**, and click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="9c48b-148">Etapa 3: Aplicar os rótulos do Office 365 aos sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c48b-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="9c48b-149">Use estas etapas para aplicar os rótulos do Office 365 às pastas de documentos de seus sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c48b-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="9c48b-150">Na guia **Microsoft Office Home** do navegador, clique no bloco **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="9c48b-151">Na nova guia **SharePoint** no navegador, clique em um site que precisa de um rótulo do Office 365 atribuído.</span><span class="sxs-lookup"><span data-stu-id="9c48b-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="9c48b-152">Na nova guia de site do SharePoint do navegador, clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="9c48b-153">Clique no ícone de configurações e clique em **Configurações de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="9c48b-154">Em **Permissões e Gerenciamento**, clique em **Aplicar o rótulo aos itens nessa biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="9c48b-155">Em **Configurações – Aplicar Rótulo**, selecione o rótulo adequado e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-155">In **Settings-Apply Label**, select the appropriate label, and click **Save**.</span></span>
    
7. <span data-ttu-id="9c48b-156">Feche a guia para o site do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c48b-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="9c48b-157">Repita as etapas 3 a 8 acima para atribuir rótulos do Office 365 aos sites adicionais do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c48b-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="9c48b-158">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="9c48b-158">Here is your resulting configuration.</span></span>
  
![Rótulos do Office 365 para os quatro tipos de sites de equipe do SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="9c48b-160">Políticas DLP para seus sites do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c48b-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="9c48b-161">Use estas etapas para configurar uma política DLP que notifica os usuários quando eles compartilham um documento em um site de equipe confidencial do SharePoint Online fora da organização.</span><span class="sxs-lookup"><span data-stu-id="9c48b-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="9c48b-162">Na guia **Microsoft Office Home** no navegador, clique no bloco **Segurança&amp; Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-162">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
2. <span data-ttu-id="9c48b-163">Na nova guia **Segurança e&amp; Conformidade** no navegador, clique em **Prevenção de perda de dados > Política**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-163">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
3. <span data-ttu-id="9c48b-164">No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="9c48b-165">No painel **Iniciar com um modelo ou criar uma política personalizada**, clique em **Personalizado** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and click **Next**.</span></span>
    
5. <span data-ttu-id="9c48b-166">No painel **Atribuir um nome à política**, digite o nome da política DLP de nível confidencial em **Nome** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-166">In the Name your policy pane, type the name for the sensitive level DLP policy in Name, and click Next.</span></span>
    
6. <span data-ttu-id="9c48b-167">No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="9c48b-168">Na lista de locais, desabilite os locais **Email do Exchange** e **Contas do OneDrive** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and click **Next**.</span></span>
    
8. <span data-ttu-id="9c48b-169">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="9c48b-170">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Adicionar** na caixa suspensa e clique em **Rótulos**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and click **Labels**.</span></span>
    
10. <span data-ttu-id="9c48b-171">No painel **Rótulos**, clique em **+ Adicionar**, selecione o rótulo **Confidencial**, clique em **Adicionar** e clique em **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and click **Done**.</span></span>
    
11. <span data-ttu-id="9c48b-172">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="9c48b-173">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="9c48b-174">No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="9c48b-175">No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="9c48b-176">Na caixa de texto, digite ou cole o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9c48b-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="9c48b-p104">Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="9c48b-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="9c48b-180">Como alternativa, digite ou cole em sua própria dica de política que instrui os usuários sobre como compartilhar um arquivo fora da organização.</span><span class="sxs-lookup"><span data-stu-id="9c48b-180">Or type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="9c48b-181">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="9c48b-182">No painel **O que deseja fazer se detectarmos informações confidenciais?**, desmarque a caixa de seleção **Impedir que as pessoas compartilhem e restringir o acesso ao conteúdo compartilhado** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and click **Next**.</span></span>
    
18. <span data-ttu-id="9c48b-183">No painel **Deseja ativar a política ou testar primeiro?**, clique em **Sim** para ativá-la imediatamente e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes**, turn it on right away, and click **Next**.</span></span>
    
19. <span data-ttu-id="9c48b-184">No painel **Examine as configurações**, clique em **Criar** e em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-184">In the **Review your settings** pane, click **Create**, and click **Close**.</span></span>
    
<span data-ttu-id="9c48b-185">Aqui está a configuração resultante dos sites confidenciais da equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="9c48b-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![A política DLP para um site de equipe isolado do SharePoint Online usando o rótulo Confidencial do Office 365.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="9c48b-187">Em seguida, use estas etapas para configurar uma política DLP que bloqueia os usuários quando eles compartilham um documento em um site de equipe altamente confidencial do SharePoint Online fora da organização.</span><span class="sxs-lookup"><span data-stu-id="9c48b-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="9c48b-188">Na guia **Microsoft Office Home** no navegador, clique no bloco **Segurança&amp; Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-188">From the Microsoft Office Home tab in your browser, click the Security & Compliance tile.</span></span>
    
2. <span data-ttu-id="9c48b-189">Na nova guia **Segurança e&amp; Conformidade** no navegador, clique em **Prevenção de perda de dados > Política**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-189">On the new Security & Compliance tab in your browser, click Data loss prevention > Policy.</span></span>
    
3. <span data-ttu-id="9c48b-190">No painel **Prevenção de perda de dados**, clique em **+ Criar uma política**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="9c48b-191">No painel **Iniciar com um modelo ou criar uma política personalizada**, clique em **Personalizado** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and click **Next**.</span></span>
    
5. <span data-ttu-id="9c48b-192">No painel **Atribuir um nome à política**, digite o nome da política DLP de nível altamente confidencial em **Nome** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and click **Next**.</span></span>
    
6. <span data-ttu-id="9c48b-193">No painel **Escolher locais**, clique em **Deixe-me escolher locais específicos** e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="9c48b-194">Na lista de locais, desabilite os locais **Email do Exchange** e **Contas do OneDrive** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and click **Next**.</span></span>
    
8. <span data-ttu-id="9c48b-195">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="9c48b-196">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Adicionar** na caixa suspensa e clique em **Rótulos**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and click **Labels**.</span></span>
    
10. <span data-ttu-id="9c48b-197">No painel **Rótulos**, clique em **+ Adicionar**, selecione o **rótulo Altamente Confidencial**, clique em **Adicionar** e clique em **Concluído**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential label**, click **Add**, and click **Done**.</span></span>
    
11. <span data-ttu-id="9c48b-198">No painel **Escolher os tipos de conteúdo para proteger**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="9c48b-199">No painel **Personalizar os tipos de informações confidenciais que deseja proteger** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="9c48b-200">No painel **O que deseja fazer se detectarmos informações confidenciais?**, clique em **Personalizar a dica e o email**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="9c48b-201">No painel **Personalizar dicas de política e notificações de email**, clique em **Personalizar o texto da dica da política**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="9c48b-202">Na caixa de texto, digite ou cole o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9c48b-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="9c48b-p105">Para compartilhar com um usuário de fora da organização, baixe o arquivo e abra-o. Clique em Arquivo, em seguida, Proteger Documento e Criptografar com Senha e especifique uma senha forte. Envie a senha em um email separado ou outros meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="9c48b-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="9c48b-206">Como alternativa, digite ou cole em sua própria dica de política que instrui os usuários sobre como compartilhar um arquivo fora da organização.</span><span class="sxs-lookup"><span data-stu-id="9c48b-206">Or type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="9c48b-207">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="9c48b-208">No painel **O que deseja fazer se detectarmos informações confidenciais?**, selecione **Exigir uma justificativa de negócios para substituir** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and click **Next**.</span></span>
    
18. <span data-ttu-id="9c48b-209">No painel **Deseja ativar a política ou testar primeiro?**, clique em **Sim** para ativá-la imediatamente e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes**, turn it on right away, and click **Next**.</span></span>
    
19. <span data-ttu-id="9c48b-210">No painel **Examine as configurações**, clique em **Criar** e em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="9c48b-210">In the **Review your settings** pane, click **Create**, and click **Close**.</span></span>
    
<span data-ttu-id="9c48b-211">Aqui está a configuração resultante para sites de equipe do SharePoint Online de alta confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="9c48b-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![A política DLP para um site de equipe isolado do SharePoint Online usando o rótulo Altamente Confidencial do Office 365.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="9c48b-213">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="9c48b-213">Next step</span></span>

[<span data-ttu-id="9c48b-214">Proteger arquivos do SharePoint Online com a Proteção de Informações do Azure</span><span class="sxs-lookup"><span data-stu-id="9c48b-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="9c48b-215">Veja também</span><span class="sxs-lookup"><span data-stu-id="9c48b-215">See Also</span></span>

[<span data-ttu-id="9c48b-216">Proteger sites e arquivos do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9c48b-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="9c48b-217">Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="9c48b-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="9c48b-218">Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile</span><span class="sxs-lookup"><span data-stu-id="9c48b-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="9c48b-219">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="9c48b-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


