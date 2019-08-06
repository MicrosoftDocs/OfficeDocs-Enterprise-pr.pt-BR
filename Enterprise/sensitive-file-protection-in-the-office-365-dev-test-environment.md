---
title: Proteção de arquivos confidenciais no ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: 'Resumo: Configure e demonstre como o gerenciamento de direitos de informação do Office 365 protege seus arquivos confidenciais, mesmo quando eles são publicados no conjunto de sites do SharePoint Online errado.'
ms.openlocfilehash: 9608bf68ced2f286f788dd94dfc27755f5ff23c0
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782491"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="e613e-103">Proteção de arquivos confidenciais no ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e613e-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="e613e-104">**Resumo:** Configure e demonstre como o gerenciamento de direitos de informação do Office 365 protege seus arquivos confidenciais, mesmo quando eles são publicados no conjunto de sites do SharePoint Online errado.</span><span class="sxs-lookup"><span data-stu-id="e613e-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="e613e-105">O gerenciamento de direitos de informação (IRM) no Office 365 é um conjunto de recursos para proteger documentos baixados de bibliotecas e listas do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e613e-105">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists.</span></span> <span data-ttu-id="e613e-106">Os arquivos baixados são criptografados e contêm as permissões abrir, copiar, salvar e imprimir que refletem a biblioteca do SharePoint Online na qual foram armazenadas.</span><span class="sxs-lookup"><span data-stu-id="e613e-106">Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="e613e-107">Com as instruções deste artigo, você habilita e testa o IRM no Office 365 para arquivos que contêm possíveis informações confidenciais em sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e613e-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="e613e-108">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual de todos os artigos da pilha da Guia do Laboratório de Teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e613e-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="e613e-109">Fase 1: criar seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e613e-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="e613e-110">Se você só quiser testar a proteção de arquivos confidenciais de forma leve com os requisitos mínimos, siga as instruções nas fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="e613e-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e613e-111">Se você quiser testar a proteção de arquivos confidenciais em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="e613e-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e613e-112">O teste de proteção de arquivos confidenciais não exige o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta dos serviços de domínio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="e613e-112">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="e613e-113">Ele é fornecido aqui como uma opção para que você possa testar a proteção de arquivos confidenciais e experimentá-lo em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="e613e-113">It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="e613e-114">Fase 2: demonstrar como os documentos de sites protegidos por permissões podem ser vazados</span><span class="sxs-lookup"><span data-stu-id="e613e-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="e613e-115">Nesta fase, você demonstra que alguém pode baixar um documento de um site protegido por permissões e carregá-lo em um site que tenha permissões de abertura ampla.</span><span class="sxs-lookup"><span data-stu-id="e613e-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="e613e-116">Primeiro, você adiciona três novas contas de usuário que representam executivos e atribui as licenças do Office 365 e5.</span><span class="sxs-lookup"><span data-stu-id="e613e-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="e613e-117">Use as instruções em [conectar-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar os módulos do PowerShell (se necessário) e se conectar à sua nova assinatura do Office 365 de:</span><span class="sxs-lookup"><span data-stu-id="e613e-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="e613e-118">Seu computador (para o ambiente leve de desenvolvimento/teste do Office 365).</span><span class="sxs-lookup"><span data-stu-id="e613e-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="e613e-119">A máquina virtual CLIENT1 (para o ambiente de desenvolvimento/teste corporativo simulado do Office 365).</span><span class="sxs-lookup"><span data-stu-id="e613e-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="e613e-120">Na caixa de diálogo solicitação de credencial do **Windows PowerShell** , digite o nome do administrador global do Office 365 (exemplo: jdoe@contosotoycompany.onmicrosoft.com) e a senha da sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e613e-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="e613e-121">Preencha o nome da sua organização (exemplo: contosotoycompany) e o código de país de dois caracteres para seu local e, em seguida, execute os seguintes comandos do prompt do módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e613e-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="e613e-122">Na exibição do comando **New-MsolUser** , anote a senha gerada para a conta do CEO e grave-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="e613e-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="e613e-123">Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e613e-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="e613e-124">Na exibição do comando **New-MsolUser** , anote a senha gerada para a conta CFO e grave-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="e613e-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="e613e-125">Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e613e-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="e613e-126">Na exibição do comando **New-MsolUser** , anote a senha gerada para a conta COO e grave-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="e613e-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="e613e-127">Em seguida, crie um grupo de executivos privados e adicione as novas contas executivas a ele.</span><span class="sxs-lookup"><span data-stu-id="e613e-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="e613e-128">No navegador, vá para o portal do Office em [http://admin.microsoft.com](http://admin.microsoft.com) e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="e613e-128">In your browser, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="e613e-129">Se você estiver usando o ambiente leve de desenvolvimento/teste do Office 365, abra uma sessão particular do Internet Explorer ou seu navegador e entre no computador local.</span><span class="sxs-lookup"><span data-stu-id="e613e-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="e613e-130">Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, use o portal do Azure para se conectar à máquina virtual do CLIENT1 e, em seguida, entre no CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e613e-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="e613e-131">Na guia **Microsoft Office Home** , clique em **administrador > grupos >** e, em seguida, clique em **Adicionar um grupo**.</span><span class="sxs-lookup"><span data-stu-id="e613e-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="e613e-132">Em **Adicionar um grupo**, selecione **grupo do Office 365** para o tipo de grupo, digite **executivos** em **nome** e **ID do grupo**, selecione **privado** para **privacidade**e clique em **selecionar proprietário**.</span><span class="sxs-lookup"><span data-stu-id="e613e-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="e613e-133">Na lista, clique no nome da conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="e613e-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="e613e-134">Clique em **Adicionar**e, em seguida, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="e613e-135">Na lista de grupos, clique em **executivos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="e613e-136">Clique em **Editar para membros**.</span><span class="sxs-lookup"><span data-stu-id="e613e-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="e613e-137">Clique em **Adicionar membros**.</span><span class="sxs-lookup"><span data-stu-id="e613e-137">Click **Add members**.</span></span> <span data-ttu-id="e613e-138">Na lista de membros, selecione as seguintes contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="e613e-138">In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="e613e-139">Diretor executivo</span><span class="sxs-lookup"><span data-stu-id="e613e-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="e613e-140">Diretor financeiro</span><span class="sxs-lookup"><span data-stu-id="e613e-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="e613e-141">Diretor de operações</span><span class="sxs-lookup"><span data-stu-id="e613e-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="e613e-142">Clique em **salvar**e, em seguida, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="e613e-143">Feche a guia **centro de administração do Office** .</span><span class="sxs-lookup"><span data-stu-id="e613e-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="e613e-144">Em seguida, você cria um conjunto de sites executivos e permite que apenas os membros do grupo executivos o acessem.</span><span class="sxs-lookup"><span data-stu-id="e613e-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="e613e-145">Na guia **Microsoft Office Home** , clique no bloco **administrador** .</span><span class="sxs-lookup"><span data-stu-id="e613e-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="e613e-146">Na guia **centro de administração do Office** , clique em **centros de administração > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e613e-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="e613e-147">Na guia **centro de administração do SharePoint** , clique em **novo > conjunto de sites particulares**.</span><span class="sxs-lookup"><span data-stu-id="e613e-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="e613e-148">No painel novo conjunto de sites, digite **executivos** em **título**, executivos na caixa URL, especifique o nome da conta de administrador global no **administrador**e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e613e-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e613e-149">Aguarde até que o novo conjunto de sites tenha sido criado.</span><span class="sxs-lookup"><span data-stu-id="e613e-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="e613e-150">Ao concluir, copie a URL do novo conjunto de sites executivos e cole-a em uma nova guia do navegador.</span><span class="sxs-lookup"><span data-stu-id="e613e-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="e613e-151">No canto superior direito do conjunto de sites **executivos** , clique no ícone configurações e, em seguida, clique em **compartilhado com**.</span><span class="sxs-lookup"><span data-stu-id="e613e-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="e613e-152">Em **compartilhar ' executivos '**, clique em **avançado**.</span><span class="sxs-lookup"><span data-stu-id="e613e-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="e613e-153">Na lista de grupos do SharePoint, clique em **membros de executivos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="e613e-154">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="e613e-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="e613e-155">Em **compartilhar ' executivos '**, digite **executivos**, clique no grupo **executivos** e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="e613e-156">Feche a guia **pessoas e grupos** .</span><span class="sxs-lookup"><span data-stu-id="e613e-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="e613e-157">Em seguida, permita que todos acessem o conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="e613e-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="e613e-158">Na guia **centro de administração do SharePoint** , copie a URL do conjunto de sites vendas e cole-a em uma nova guia do navegador.</span><span class="sxs-lookup"><span data-stu-id="e613e-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="e613e-159">No canto superior direito, clique no ícone configurações e, em seguida, clique em **compartilhado com**.</span><span class="sxs-lookup"><span data-stu-id="e613e-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="e613e-160">Em **compartilhar "conjunto de sites de vendas"**, clique em **avançado**.</span><span class="sxs-lookup"><span data-stu-id="e613e-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="e613e-161">Na lista de grupos do SharePoint, clique em **membros do conjunto de sites de vendas**.</span><span class="sxs-lookup"><span data-stu-id="e613e-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="e613e-162">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="e613e-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="e613e-163">Em **compartilhar ' conjunto de sites de vendas '**, digite **todos**, clique em **todos exceto usuários externos**e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="e613e-164">Feche as guias **conjunto de sites de vendas** e **do SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="e613e-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="e613e-165">Em seguida, você entra com uma conta executiva e cria um documento no conjunto de sites executivos.</span><span class="sxs-lookup"><span data-stu-id="e613e-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="e613e-166">Na guia **Microsoft Office Home** , clique no ícone de usuário no canto superior direito e, em seguida, \*\*\*\* clique em sair.</span><span class="sxs-lookup"><span data-stu-id="e613e-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="e613e-167">Acesse [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e613e-167">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="e613e-168">Na página de **entrada do Office 365** , clique em **usar outra conta**.</span><span class="sxs-lookup"><span data-stu-id="e613e-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="e613e-169">Digite o nome da conta do **CEO** e sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="e613e-170">Em uma nova guia do navegador, digite a URL para o conjunto de sites executivos (nome da organização do **https://**\<>**. SharePoint.com/sites/Executives**).</span><span class="sxs-lookup"><span data-stu-id="e613e-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="e613e-171">Clique em **documentos**, clique em **novo** e em **documento do Word**.</span><span class="sxs-lookup"><span data-stu-id="e613e-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="e613e-172">Clique na barra de título e digite **SensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="e613e-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="e613e-173">Clique no corpo do documento e digite **minutos na reunião mais recente da placa**e, em seguida, clique em **executivos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="e613e-174">Você verá **SensitiveData-BeforeIRM. docx** na pasta **documentos** .</span><span class="sxs-lookup"><span data-stu-id="e613e-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="e613e-175">Em seguida, Baixe uma cópia local do documento SensitiveData-BeforeIRM. docx e, em seguida, poste-a acidentalmente para o conjunto de sites Sales.</span><span class="sxs-lookup"><span data-stu-id="e613e-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="e613e-176">No computador local, crie uma nova pasta (por exemplo, C:\\TLGs\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="e613e-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="e613e-177">Na guia **documentos** do navegador, selecione o documento **SensitiveData-BeforeIRM. docx** , clique nas reticências e, em seguida, clique em **baixar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="e613e-178">Armazene o documento **SensitiveData-BeforeIRM. docx** na pasta criada na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="e613e-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="e613e-179">Em uma nova guia do navegador, digite a URL do conjunto de sites de vendas (nome da organização do **https://**\<>**. SharePoint.com/sites/Sales**).</span><span class="sxs-lookup"><span data-stu-id="e613e-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="e613e-180">Clique na pasta **documentos** do **conjunto de sites de vendas**.</span><span class="sxs-lookup"><span data-stu-id="e613e-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="e613e-181">Clique em **carregar**e especifique o documento **SensitiveData-BeforeIRM. docx** na pasta criada na etapa 1 e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e613e-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="e613e-182">Verifique se o documento **SensitiveData-BeforeIRM. docx** está na pasta **documentos** .</span><span class="sxs-lookup"><span data-stu-id="e613e-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="e613e-183">Feche as guias **vendas** e **do SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="e613e-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="e613e-184">Em seguida, você entra como User5 e tenta abrir o documento SensitiveData-BeforeIRM. docx no conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="e613e-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="e613e-185">Na guia **Microsoft Office Home** , clique no ícone de usuário no canto superior direito e, em seguida, \*\*\*\* clique em sair.</span><span class="sxs-lookup"><span data-stu-id="e613e-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="e613e-186">Acesse [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e613e-186">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="e613e-187">Na página de **entrada do Office 365** , clique em **usar outra conta**.</span><span class="sxs-lookup"><span data-stu-id="e613e-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="e613e-188">Digite o nome da conta do User5 e sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="e613e-189">Em uma nova guia do navegador, digite a URL do conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="e613e-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="e613e-190">Na pasta **documentos** do conjunto de **sites vendas**, clique no documento **SensitiveData-BeforeIRM. docx** .</span><span class="sxs-lookup"><span data-stu-id="e613e-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="e613e-191">Você deve ver seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e613e-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="e613e-192">Feche as guias **documentos** e **conjunto de sites de vendas** .</span><span class="sxs-lookup"><span data-stu-id="e613e-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="e613e-193">Ao postar o documento SensitiveData-BeforeIRM. docx acidentalmente no conjunto de sites de vendas, o CEO ignorou a segurança de permissões do conjunto de sites executivos.</span><span class="sxs-lookup"><span data-stu-id="e613e-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="e613e-194">Para preparar o Office 365 para as fases 3 e 4, habilite o IRM para o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e613e-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="e613e-195">Na guia **Microsoft Office Home** , clique no ícone de usuário no canto superior direito e, em seguida, \*\*\*\* clique em sair.</span><span class="sxs-lookup"><span data-stu-id="e613e-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="e613e-196">Acesse [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e613e-196">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="e613e-197">Na página de **entrada do Office 365** , clique no nome da conta de administrador global, digite sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="e613e-198">Na guia **Microsoft Office Home** , clique em **centro de administração de > de administração > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e613e-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="e613e-199">Na guia **centro de administração do SharePoint** , clique em **configurações**.</span><span class="sxs-lookup"><span data-stu-id="e613e-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="e613e-200">Na página, na seção **Gerenciamento de direitos de informação (IRM)** , selecione **usar o serviço IRM especificado em sua configuração**e, em seguida, selecione **Atualizar configurações de IRM**.</span><span class="sxs-lookup"><span data-stu-id="e613e-200">On the page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="e613e-201">Feche a guia **centro de administração do SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="e613e-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="e613e-202">Fase 3: usar o gerenciamento de direitos de informação do SharePoint com um grupo privado do Office 365</span><span class="sxs-lookup"><span data-stu-id="e613e-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="e613e-203">Nesta fase, você usa o gerenciamento de direitos de informação do SharePoint com um grupo privado do Office 365 para proteger o acesso a um documento com informações confidenciais, mesmo quando ele é publicado em um site com permissões abertas.</span><span class="sxs-lookup"><span data-stu-id="e613e-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="e613e-204">Primeiro, habilite e configure o IRM para a biblioteca de documentos do conjunto de sites executivos.</span><span class="sxs-lookup"><span data-stu-id="e613e-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="e613e-205">Em uma nova guia do navegador, digite a URL para o conjunto de sites executivos.</span><span class="sxs-lookup"><span data-stu-id="e613e-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="e613e-206">Clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="e613e-207">No canto superior direito, clique no ícone configurações e, em seguida, clique em **configurações da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="e613e-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="e613e-208">Na página **configurações** , em **permissões e gerenciamento**, clique em **Gerenciamento de direitos de informação**.</span><span class="sxs-lookup"><span data-stu-id="e613e-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="e613e-209">Na página **configurações de gerenciamento de direitos de informação** :</span><span class="sxs-lookup"><span data-stu-id="e613e-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="e613e-210">Selecione **restringir permissão para documentos nesta biblioteca durante o download**.</span><span class="sxs-lookup"><span data-stu-id="e613e-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="e613e-211">Para **criar um título de política de permissão**, digite **executivos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="e613e-212">Para **Adicionar uma descrição de política de permissão**, digite **IRM para executivos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="e613e-213">Clique em **Mostrar Opções**.</span><span class="sxs-lookup"><span data-stu-id="e613e-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="e613e-214">Em **definir configurações de biblioteca de IRM adicionais**, selecione não **permitir que os usuários carreguem documentos que não dão suporte ao IRM**.</span><span class="sxs-lookup"><span data-stu-id="e613e-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="e613e-215">Em **Configurar direitos de acesso ao documento**, selecione **permitir que** os visualizadores imprimam e **permitir que os visualizadores escrevam em uma cópia do documento baixado**.</span><span class="sxs-lookup"><span data-stu-id="e613e-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="e613e-216">Em **definir intervalo de credenciais e proteção de grupo**, selecione **permitir proteção de grupo. Grupo padrão**e, em seguida, digite **executivos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-216">Under **Set group protection and credentials interval**, select **Allow group protection. Default group**, and then type **Executives**.</span></span>
    
10. <span data-ttu-id="e613e-217">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e613e-217">Click **OK**.</span></span>
    
<span data-ttu-id="e613e-218">Em seguida, agindo como CEO, você carrega um novo documento na pasta de documentos executivos, baixa-o e, em seguida, o carrega acidentalmente para a pasta de documentos de vendas.</span><span class="sxs-lookup"><span data-stu-id="e613e-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="e613e-219">Abra a pasta local onde você armazenou o documento **SensitiveData-BeforeIRM. docx** .</span><span class="sxs-lookup"><span data-stu-id="e613e-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="e613e-220">Clique com o botão direito do mouse em **SensitiveData-BeforeIRM. docx**e clique em **copiar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="e613e-221">Clique com o botão direito do mouse na pasta e clique em **colar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="e613e-222">Renomeie o novo arquivo **SensitiveData-BeforeIRM-Copy. docx** para **SensitiveData-AfterIRM. docx**.</span><span class="sxs-lookup"><span data-stu-id="e613e-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="e613e-223">Na guia **Microsoft Office Home** no navegador, clique no ícone de usuário no canto superior direito e, em seguida, clique \*\*\*\* em sair.</span><span class="sxs-lookup"><span data-stu-id="e613e-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="e613e-224">Acesse [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e613e-224">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="e613e-225">Na página de **entrada do Office 365** , clique no nome da conta do CEO, digite sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="e613e-226">Em uma nova guia do navegador, digite a URL para o conjunto de sites executivos.</span><span class="sxs-lookup"><span data-stu-id="e613e-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="e613e-227">Na página **documentos** , clique em **carregar**, especifique o documento **SensitiveData-AfterIRM. docx** na pasta local e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="e613e-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="e613e-228">Selecione o novo documento **SensitiveData-AfterIRM. docx** na página **documentos** , clique nas reticências (...) na barra de menus e, em seguida, clique em **baixar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="e613e-229">Quando solicitado, salve o documento **SensitiveData-AfterIRM. docx** na pasta local, substituindo a versão original.</span><span class="sxs-lookup"><span data-stu-id="e613e-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="e613e-230">Feche a guia da página de **documentos** .</span><span class="sxs-lookup"><span data-stu-id="e613e-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="e613e-231">Em uma nova guia do navegador, digite a URL do conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="e613e-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="e613e-232">Clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="e613e-233">Na página **documentos** , clique em **carregar**, especifique o documento **SensitiveData-AfterIRM. docx** na pasta local e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="e613e-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="e613e-234">Feche as guias **conjunto de sites de vendas** e **do SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="e613e-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="e613e-235">Em seguida, agindo como um usuário normal, você tenta acessar o documento **SensitiveData-AfterIRM. docx** na pasta de documentos Sales.</span><span class="sxs-lookup"><span data-stu-id="e613e-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="e613e-236">Na guia **Microsoft Office Home** no navegador, clique no ícone de usuário no canto superior direito e, em seguida, clique \*\*\*\* em sair.</span><span class="sxs-lookup"><span data-stu-id="e613e-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="e613e-237">Acesse [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="e613e-237">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="e613e-238">Na página de **entrada do Office 365** , clique no nome da conta User5, digite sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="e613e-239">Em uma nova guia do navegador, digite a URL do conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="e613e-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="e613e-240">Clique em **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="e613e-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="e613e-241">Na página **documentos** , abra o documento **SensitiveData-AfterIRM. docx** .</span><span class="sxs-lookup"><span data-stu-id="e613e-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="e613e-242">Você deve ver uma mensagem afirmando que "o Word não pode abrir este documento porque ele está protegido pelo gerenciamento de direitos de informação (IRM)".</span><span class="sxs-lookup"><span data-stu-id="e613e-242">You should see a message that states, "Sorry, Word can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="e613e-243">Clique em **Editar no Word**.</span><span class="sxs-lookup"><span data-stu-id="e613e-243">Click **Edit in Word**.</span></span> <span data-ttu-id="e613e-244">Você será solicitado a confirmar se deseja abrir o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e613e-244">You are prompted if you want to open the file.</span></span> <span data-ttu-id="e613e-245">Clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="e613e-245">Click **Yes**.</span></span>
    
8. <span data-ttu-id="e613e-246">Você será solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="e613e-246">You are prompted to sign-in.</span></span> <span data-ttu-id="e613e-247">Digite o nome da conta do User5 e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-247">Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="e613e-248">Você será solicitado a fornecer a senha.</span><span class="sxs-lookup"><span data-stu-id="e613e-248">You are prompted to provide the password.</span></span> <span data-ttu-id="e613e-249">Digite a senha para a conta User5 e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="e613e-249">Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="e613e-250">Você deve ver a mensagem que diz: "você não tem as credenciais que permitem abrir este documento."</span><span class="sxs-lookup"><span data-stu-id="e613e-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="e613e-251">Clique em **não**.</span><span class="sxs-lookup"><span data-stu-id="e613e-251">Click **No**.</span></span>
    
<span data-ttu-id="e613e-252">Outra maneira de ver a proteção de IRM é examinar os arquivos na sua pasta local.</span><span class="sxs-lookup"><span data-stu-id="e613e-252">Another way to see the IRM protection is to look at the files in your local folder.</span></span> <span data-ttu-id="e613e-253">O **SensitiveData-AfterIRM. docx** deve ser muito maior do que o arquivo **SensitiveData-BeforeIRM. docx** .</span><span class="sxs-lookup"><span data-stu-id="e613e-253">The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file.</span></span> <span data-ttu-id="e613e-254">O arquivo **SensitiveData-AfterIRM. docx** é criptografado e tem as informações de proteção do IRM adicionadas a ele.</span><span class="sxs-lookup"><span data-stu-id="e613e-254">The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e613e-255">Confira também</span><span class="sxs-lookup"><span data-stu-id="e613e-255">See Also</span></span>

[<span data-ttu-id="e613e-256">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="e613e-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
<span data-ttu-id="e613e-257">[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="e613e-257">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="e613e-258">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e613e-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="e613e-259">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="e613e-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


