---
title: Proteger arquivos do SharePoint Online com a Proteção de Informações do Azure
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
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Resumo: aplique a Proteção de Informações do Azure para proteger arquivos em um site de equipe altamente confidencial do SharePoint Online.'
ms.openlocfilehash: 2c4776f5795a5a0b07be0f04b4872abadb4d31ca
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319282"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="483a9-103">Proteger arquivos do SharePoint Online com a Proteção de Informações do Azure</span><span class="sxs-lookup"><span data-stu-id="483a9-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="483a9-104">**Resumo:** aplique a Proteção de Informações do Azure para proteger arquivos em um site de equipe altamente confidencial do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="483a9-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="483a9-p101">Use as etapas neste artigo para configurar a Proteção de Informações do Azure para fornecer as permissões para arquivos e a criptografia. Esses arquivos podem ser adicionados a uma biblioteca do SharePoint configurada para proteção altamente confidencial. Em alternativa, você pode abrir um arquivo diretamente do site e usar o cliente da Proteção de Informações do Azure para adicionar criptografia. A proteção de criptografia e permissões acompanha um arquivo mesmo quando ele é baixado do site.</span><span class="sxs-lookup"><span data-stu-id="483a9-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files. These files can be added to a SharePoint library configured for highly confidential protection. Or, you can open a file directly from the site and use the Azure Information Protection client to add encryption. The encryption and permissions protection travels with a file even when it is downloaded from the site.</span></span> 

<span data-ttu-id="483a9-p102">Essas etapas são parte de uma solução maior de configuração da proteção altamente confidencial para sites do SharePoint e os arquivos dentro desses sites. Para saber mais, confira [Sites e arquivos seguros do SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="483a9-p102">These steps are part of a larger solution for configuring highly confidential protection for SharePoint sites and the files within these sites. For more information, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span> 

<span data-ttu-id="483a9-111">Usar a Proteção de Informações do Azure para arquivos no SharePoint Online não é recomendável para todos os clientes, mas é uma opção para os clientes que precisam deste nível de proteção para um subconjunto de arquivos.</span><span class="sxs-lookup"><span data-stu-id="483a9-111">Using Azure Information Protection for files in SharePoint Online is not recommended for all customers, but is an option for customers who need this level of protection for a subset of files.</span></span>

<span data-ttu-id="483a9-112">Algumas observações importantes sobre esta solução:</span><span class="sxs-lookup"><span data-stu-id="483a9-112">Some important notes about this solution:</span></span>
- <span data-ttu-id="483a9-p103">Quando a criptografia da Proteção de Informações do Azure é aplicada aos arquivos armazenados no Office 365, o serviço não pode processar o conteúdo desses arquivos. Coautoria, descoberta eletrônica, pesquisa, Delve e outros recursos de colaboração não funcionam. Políticas DLP só funcionam com metadados (incluindo rótulos do Office 365), mas não com o conteúdo desses arquivos (como números de cartão de crédito em arquivos).</span><span class="sxs-lookup"><span data-stu-id="483a9-p103">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
- <span data-ttu-id="483a9-p104">Esta solução exige que um usuário selecione um rótulo que se aplica à proteção da Proteção de Informações do Azure. Se precisar de criptografia automática e da capacidade do SharePoint de indexar e examinar os arquivos, considere usar o Gerenciamento de Direitos de Informação (IRM) no SharePoint Online. Quando você configura uma biblioteca do SharePoint para o IRM, os arquivos são criptografados automaticamente quando são baixados para edição. O IRM do SharePoint inclui limitações que podem influenciar a sua decisão. Para saber mais, confira [Configurar o Gerenciamento de Direitos de Informação (IRM) no Centro de administração do SharePoint](https://support.office.com/pt-BR/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span><span class="sxs-lookup"><span data-stu-id="483a9-p104">This solution requires a user to select a label that applies the protection from Azure Information Protection. If you require automatic encryption and the ability for SharePoint to index and inspect the files, consider using Information Rights Management (IRM) in SharePoint Online. When you configure a SharePoint library for IRM, files are automatically encrypted when they are downloaded for editing.  SharePoint IRM includes limitations that might influence your decision. For more information, see [Set up Information Rights Management (IRM) in SharePoint admin center](https://support.office.com/pt-BR/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span></span>

##<a name="admin-setup"></a><span data-ttu-id="483a9-121">Configuração de administrador</span><span class="sxs-lookup"><span data-stu-id="483a9-121">Admin setup</span></span>
<span data-ttu-id="483a9-122">Primeiro, use as instruções em [Ativar o Azure RMS com o centro de administração do Office 365 para sua assinatura do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="483a9-122">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="483a9-123">Em seguida, configure a Proteção de Informações do Azure com uma nova política com escopo e um sub-rótulo para proteção e permissões do seu site de equipe altamente confidencial do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="483a9-123">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="483a9-p105">Entre no Portal do Office 365 com uma conta que tenha a função de Administrador de Segurança ou Administrador da Empresa. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="483a9-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="483a9-126">Em uma guia separada do navegador, vá para o Portal do Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="483a9-126">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="483a9-127">Se esta é a primeira vez que você configura a Proteção de Informações do Azure, confira estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="483a9-127">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="483a9-128">No painel de lista, clique em **Todos os serviços**, digite **informações** e clique em **Proteção de Informações do Azure**.</span><span class="sxs-lookup"><span data-stu-id="483a9-128">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="483a9-129">Na folha **Proteção de Informações do Azure**, clique em **Políticas no escopo > + Adicionar uma nova política**.</span><span class="sxs-lookup"><span data-stu-id="483a9-129">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="483a9-130">Digite um nome para a nova política no **Nome da política** e uma descrição em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="483a9-130">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="483a9-131">Clique em **Selecionar quais usuários ou grupos obtêm esta política > Usuário/ Grupos**, e selecione o grupo de acesso dos membros do site para o site da equipe do SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="483a9-131">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="483a9-132">Clique em **Selecionar > OK**.</span><span class="sxs-lookup"><span data-stu-id="483a9-132">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="483a9-133">Para o rótulo **Altamente Confidencial**, clique nas reticências (...) e, em seguida, clique em **Adicionar um sub-rótulo**.</span><span class="sxs-lookup"><span data-stu-id="483a9-133">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="483a9-134">Digite um nome para o subrótulo em **Nome** e uma descrição do rótulo em **Descrição**.</span><span class="sxs-lookup"><span data-stu-id="483a9-134">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="483a9-135">Em **Definir permissões para documentos e emails que contenham este rótulo**, clique em **Proteger**.</span><span class="sxs-lookup"><span data-stu-id="483a9-135">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="483a9-136">Na seção **Proteção**, clique em **Azure (chave de nuvem)**.</span><span class="sxs-lookup"><span data-stu-id="483a9-136">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="483a9-137">Na folha **Proteção**, em **Configurações de proteção**, clique em **+ Adicionar permissões**.</span><span class="sxs-lookup"><span data-stu-id="483a9-137">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="483a9-138">Na folha **Adicionar permissões**, em **Especificar usuários e grupos**, clique em **+ Procurar no diretório**.</span><span class="sxs-lookup"><span data-stu-id="483a9-138">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="483a9-139">No painel **Usuários e Grupos do AAD**, selecione o grupo de acesso de membros do site para seu site de equipe altamente confidencial do SharePoint Online e clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="483a9-139">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="483a9-140">Em **Escolher permissões da predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo** e **Encaminhar**.</span><span class="sxs-lookup"><span data-stu-id="483a9-140">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="483a9-141">Clique em **OK** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="483a9-141">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="483a9-142">Na folha **Sub-rótulo**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="483a9-142">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="483a9-143">Feche a nova folha de política com escopo.</span><span class="sxs-lookup"><span data-stu-id="483a9-143">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="483a9-144">Na folha **Proteção de Informações do Azure – Políticas com escopo**, clique em **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="483a9-144">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
 
##<a name="client-setup"></a><span data-ttu-id="483a9-145">Configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="483a9-145">Client setup</span></span>
<span data-ttu-id="483a9-146">Agora você está pronto para começar a criar documentos e protegê-los com a Proteção de Informações do Azure e seu novo rótulo.</span><span class="sxs-lookup"><span data-stu-id="483a9-146">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="483a9-p106">Você deve [Instalar o cliente da Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em seu dispositivo ou computador baseado no Windows. Você pode criar scripts e automatizar a instalação, ou os usuários podem instalar o cliente manualmente. Confira os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="483a9-p106">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="483a9-150">O lado do cliente da Proteção de Informações do Azure</span><span class="sxs-lookup"><span data-stu-id="483a9-150">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="483a9-151">Instalando o cliente da Proteção de Informações do Azure</span><span class="sxs-lookup"><span data-stu-id="483a9-151">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="483a9-152">Página de download para a instalação manual</span><span class="sxs-lookup"><span data-stu-id="483a9-152">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="483a9-p107">Depois de instalado, os usuários executam e entram em um aplicativo do Office (como o Microsoft Word) com suas contas do Office 365. A nova barra **Proteção de Informações** permite aos usuários selecionar um novo rótulo. Certifique-se de que os usuários saibam o site da equipe do SharePoint Online e qual rótulo devem usar para proteger os arquivos altamente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="483a9-p107">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="483a9-156">Se houver vários sites de equipe do SharePoint Online altamente confidenciais, crie várias políticas de escopo de Proteção de Informações do Azure com sub-rótulos com as configurações acima, com as permissões para cada sub-rótulo definidas para o grupo de acesso de membros do site, de um site específico de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="483a9-156">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
##<a name="adding-permissions-for-external-users"></a><span data-ttu-id="483a9-157">Adicionar permissões para usuários externos</span><span class="sxs-lookup"><span data-stu-id="483a9-157">Adding permissions for external users</span></span>
<span data-ttu-id="483a9-p108">Há duas maneiras para conceder aos usuários externos o acesso aos arquivos protegidos com a Proteção de Informações do Azure. Em ambos os casos, os usuários externos devem ter uma conta do Azure AD. Se os usuários externos não forem membros de uma organização que usa o Azure AD, eles poderão obter uma conta do Azure AD como um indivíduo usando essa página de entrada: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span><span class="sxs-lookup"><span data-stu-id="483a9-p108">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>

 - <span data-ttu-id="483a9-p109">Adicione usuários externos a um grupo do Azure AD que seja usado para configurar proteção para um rótulo. Você precisará adicionar primeiro a conta como usuário B2B no diretório. Pode levar algumas horas para que seja realizado o [cache de associação de grupos pelo Azure Rights Management](https://docs.microsoft.com/pt-BR/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="483a9-p109">Add external users to an Azure AD group that is used to configure protection for a label. You’ll need to first add the account as a B2B user in your directory. It can take a couple of hours for group membership caching by Azure Rights Management. With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>  
 - <span data-ttu-id="483a9-p110">Adicione usuários externos diretamente à proteção de rótulo. Você pode adicionar todos os usuários de uma organização (por exemplo, Fabrikam.com), um grupo do Azure AD (como um grupo de finanças dentro de uma organização) ou um usuário. Por exemplo, você pode adicionar uma equipe externa de reguladores á proteção de um rótulo.</span><span class="sxs-lookup"><span data-stu-id="483a9-p110">Add external users directly to the label protection. You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>

## <a name="see-also"></a><span data-ttu-id="483a9-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="483a9-167">See Also</span></span>

[<span data-ttu-id="483a9-168">Proteger sites e arquivos do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="483a9-168">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="483a9-169">Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="483a9-169">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="483a9-170">Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile</span><span class="sxs-lookup"><span data-stu-id="483a9-170">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="483a9-171">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="483a9-171">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




