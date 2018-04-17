---
title: Proteger os arquivos do SharePoint Online com proteção de informações do Windows Azure
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
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Resumo: Aplica proteção de informações do Windows Azure para proteger os arquivos em um site de equipe do SharePoint Online altamente confidencial.'
ms.openlocfilehash: 84bd1f48c7051f945e7b851f829421364de2a557
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="17b2e-103">Proteger os arquivos do SharePoint Online com proteção de informações do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="17b2e-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="17b2e-104">**Resumo:** Aplica proteção de informações do Windows Azure para proteger os arquivos em um site de equipe do SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="17b2e-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="17b2e-p101">Use as etapas neste artigo para configurar a proteção de informações do Windows Azure para fornecer criptografia e permissões para os arquivos em um site de equipe do SharePoint Online altamente confidencial. A proteção de criptografia e permissões viaja com um arquivo, mesmo quando ele é baixado do site. Para obter mais informações sobre altamente confidenciais sites de equipe do SharePoint Online, consulte [arquivos e sites seguro do SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="17b2e-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="17b2e-p102">Quando a criptografia da Proteção de Informações do Azure é aplicada aos arquivos armazenados no Office 365, o serviço não pode processar o conteúdo desses arquivos. Coautoria, descoberta eletrônica, pesquisa, Delve e outros recursos de colaboração não funcionam. Políticas DLP só funcionam com metadados (incluindo rótulos do Office 365), mas não com o conteúdo desses arquivos (como números de cartão de crédito em arquivos).</span><span class="sxs-lookup"><span data-stu-id="17b2e-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="17b2e-111">Primeiro, use as instruções em [Ativar o Azure RMS com o Centro de administração do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) para sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="17b2e-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="17b2e-112">Em seguida, configure a proteção de informações do Windows Azure com uma nova política de escopo e sub-recurso rótulo para proteção e permissões do seu site de equipe do SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="17b2e-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="17b2e-p103">Entrar no portal do Office 365 com uma conta que tenha a função de administrador de segurança ou administrador da empresa. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="17b2e-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="17b2e-115">Em uma guia separada do navegador, vá para o portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="17b2e-115">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="17b2e-116">Se essa for a primeira vez que você está configurando a proteção de informações do Windows Azure, consulte estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="17b2e-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="17b2e-117">No painel de lista, clique em **mais de serviços**, digite as **informações**e clique em **Proteção de informações do Windows Azure**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="17b2e-118">No blade **proteção das informações do Azure** , clique em **escopo políticas > + Adicionar uma nova diretiva**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="17b2e-119">Digite um nome para a nova política no **Nome da política** e uma descrição em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="17b2e-120">Clique em **Selecionar quais usuários ou grupos obtêm esta política > Usuário/ Grupos**, e selecione o grupo de acesso dos membros do site para o site da equipe do SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="17b2e-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="17b2e-121">Clique em **Selecionar > OK**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="17b2e-122">Para o rótulo **Altamente Confidencial**, clique nas reticências (...) e, em seguida, clique em **Adicionar um sub-rótulo**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="17b2e-123">Digite um nome para o subrótulo em **Nome** e uma descrição do rótulo em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="17b2e-124">Em **Definir permissões para documentos e emails que contenham este rótulo**, clique em **Proteger**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="17b2e-125">Na seção **Proteção**, clique em **Azure (chave de nuvem)**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="17b2e-126">Na folha **Proteção**, em **Configurações de proteção**, clique em **+ Adicionar permissões**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="17b2e-127">Na folha **Adicionar permissões**, em **Especificar usuários e grupos**, clique em **+ Procurar no diretório**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="17b2e-128">No painel **AAD usuários e grupos** , selecione o grupo de acesso de membros do site do seu site de equipe do SharePoint Online altamente confidencial e clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="17b2e-129">Em **Escolha as permissões a predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo**e **Encaminhar** .</span><span class="sxs-lookup"><span data-stu-id="17b2e-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="17b2e-130">Clique duas vezes em **Okey** .</span><span class="sxs-lookup"><span data-stu-id="17b2e-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="17b2e-131">Na folha **Rótulo**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="17b2e-132">Feche a nova folha de política em escopo.</span><span class="sxs-lookup"><span data-stu-id="17b2e-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="17b2e-133">No blade **proteção de informações do Windows Azure - políticas com escopo** , clique em **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="17b2e-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="17b2e-134">Isso é sua configuração resultante para seu site de equipe do SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="17b2e-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![Rótulo da Proteção de Informações do Azure de um site de equipe isolado do SharePoint Online.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="17b2e-136">Agora você está pronto para começar a criar documentos e protegê-los com a Proteção de Informações do Azure e seu novo rótulo.</span><span class="sxs-lookup"><span data-stu-id="17b2e-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="17b2e-p104">Você deve [instalar o cliente de proteção de informações do Windows Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) no seu dispositivo ou computador baseado no Windows. Você pode criar script e automatizar a instalação ou os usuários podem instalar manualmente o cliente. Consulte os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="17b2e-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="17b2e-140">O lado do cliente da Proteção de Informações do Azure</span><span class="sxs-lookup"><span data-stu-id="17b2e-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="17b2e-141">Instalando o cliente da Proteção de Informações do Azure</span><span class="sxs-lookup"><span data-stu-id="17b2e-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="17b2e-142">Página de download para a instalação manual</span><span class="sxs-lookup"><span data-stu-id="17b2e-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="17b2e-p105">Depois de instalado, seus usuários execute e, em seguida, login em um aplicativo do Office (por exemplo, o Microsoft Word) com sua conta do Office 365. Uma nova barra de **Proteção de informações** permite que os usuários selecionem o novo rótulo. Certifique-se de que os usuários saibam o site da equipe do SharePoint Online e que identificam os usar para proteger seus arquivos altamente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="17b2e-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="17b2e-146">Se houver vários sites de equipe do SharePoint Online altamente confidenciais, crie várias políticas de escopo de Proteção de Informações do Azure com sub-rótulos com as configurações acima, com as permissões para cada sub-rótulo definidas para o grupo de acesso de membros do site, de um site específico de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="17b2e-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="17b2e-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="17b2e-147">See Also</span></span>

[<span data-ttu-id="17b2e-148">Proteger sites e arquivos do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="17b2e-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="17b2e-149">Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="17b2e-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="17b2e-150">Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile</span><span class="sxs-lookup"><span data-stu-id="17b2e-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="17b2e-151">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="17b2e-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




