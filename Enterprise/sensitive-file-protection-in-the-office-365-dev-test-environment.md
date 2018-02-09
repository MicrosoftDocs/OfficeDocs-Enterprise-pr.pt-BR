---
title: "Proteção de arquivos confidenciais no ambiente de desenvolvimento e teste Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "Resumo: Configurar e demonstrar como o Office 365 Information Rights Management protege arquivos confidenciais, mesmo quando eles são lançados ao conjunto de sites do SharePoint Online errado."
ms.openlocfilehash: 388eb2a6288fc72771b6a554d1c9de78febe8a4e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="7a74d-103">Proteção de arquivos confidenciais no ambiente de desenvolvimento e teste Office 365</span><span class="sxs-lookup"><span data-stu-id="7a74d-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="7a74d-104">**Resumo:** Configurar e demonstrar como o Office 365 Information Rights Management protege arquivos confidenciais, mesmo quando eles são lançados ao conjunto de sites do SharePoint Online errado.</span><span class="sxs-lookup"><span data-stu-id="7a74d-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="7a74d-p101">Gerenciamento de direitos de informação (IRM) no Office 365 é um conjunto de recursos para proteger os documentos que são baixados listas e bibliotecas do SharePoint Online. Arquivos baixados são criptografados e contenham cópia aberta, salvar e imprimir permissões que refletem a biblioteca do SharePoint Online na qual eles foram armazenados.</span><span class="sxs-lookup"><span data-stu-id="7a74d-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="7a74d-107">Com as instruções deste artigo, você pode habilitar e testar o IRM no Office 365 para arquivos que contenham informações confidenciais possíveis em sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a74d-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="7a74d-108">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="7a74d-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="7a74d-109">Fase 1: Criar o seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="7a74d-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="7a74d-110">Se você deseja testar a proteção de arquivo confidenciais de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="7a74d-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="7a74d-111">Se você deseja testar a proteção de arquivos confidenciais em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="7a74d-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="7a74d-p102">Testando a proteção de arquivos confidenciais não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa testar a proteção de arquivos confidenciais e experimentar em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="7a74d-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="7a74d-114">Fase 2: Demonstre como documentos de sites permissões protegido podem ser vazados</span><span class="sxs-lookup"><span data-stu-id="7a74d-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="7a74d-115">Nesta fase, você demonstrar que alguém pode fazer o download de um documento de um site protegido por permissões e carregá-la a um site que tenha permissões totalmente abertas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="7a74d-116">Primeiro, você adiciona três novas contas de usuário que representam executivos e atribuir-lhes licenças do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="7a74d-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="7a74d-117">Use as instruções em [conectar-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para instalar os módulos do PowerShell (se necessário) e se conectar à sua nova assinatura do Office 365 de:</span><span class="sxs-lookup"><span data-stu-id="7a74d-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="7a74d-118">Seu computador (para o ambiente leve de desenvolvimento/teste do Office 365).</span><span class="sxs-lookup"><span data-stu-id="7a74d-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="7a74d-119">A máquina virtual CLIENT1 (para o ambiente de desenvolvimento e teste de enterprise simulado Office 365).</span><span class="sxs-lookup"><span data-stu-id="7a74d-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="7a74d-120">Na caixa de diálogo **Solicitação de credencial do Windows PowerShell** , digite o nome de administrador global do Office 365 (exemplo: jdoe@contosotoycompany.onmicrosoft.com) e a senha da sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a74d-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="7a74d-121">Preencha o nome da sua organização (exemplo: contosotoycompany) e o país de dois caracteres de código para o seu local e, em seguida, execute os seguintes comandos no prompt Windows Azure Active Directory módulo para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7a74d-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="7a74d-122">Na exibição do comando **New-MsolUser** , observe a gerado senha da conta do CEO e registre-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="7a74d-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="7a74d-123">Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7a74d-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="7a74d-124">Na exibição do comando **New-MsolUser** , observe a gerado senha da conta do diretor financeiro e registre-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="7a74d-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="7a74d-125">Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7a74d-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="7a74d-126">Na exibição do comando **New-MsolUser** , observe a gerado senha da conta de COO e registre-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="7a74d-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="7a74d-127">Em seguida, você pode cria um grupo de executivos privado e adicione as novas contas de executivas a ela.</span><span class="sxs-lookup"><span data-stu-id="7a74d-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="7a74d-128">No seu navegador, vá para o portal do Office em [http://portal.office.com](http://portal.office.com) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="7a74d-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="7a74d-129">Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 lightweight, abra uma sessão particular do Internet Explorer ou seu navegador e acesse do computador local.</span><span class="sxs-lookup"><span data-stu-id="7a74d-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="7a74d-130">Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, use o portal Azure para conectar a máquina virtual CLIENT1 e entrar em CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="7a74d-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="7a74d-131">Na guia **Página inicial do Microsoft Office** , clique em **Admin > grupos > grupos**e, em seguida, clique em **Adicionar um grupo**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="7a74d-132">Em **Adicionar um grupo**, selecione o **grupo do Office 365** para o tipo de grupo, digite **executivos** em **nome** e **Id de grupo**, selecione **privada** para **privacidade**e, em seguida, clique em **Selecionar proprietário**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="7a74d-133">Na lista, clique em seu nome de conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="7a74d-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="7a74d-134">Clique em **Adicionar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="7a74d-135">Na lista de grupos, clique em **executivos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="7a74d-136">Clique em **Editar para membros**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="7a74d-p103">Clique em **Adicionar membros**. Na lista de membros, selecione as seguintes contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="7a74d-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="7a74d-139">Diretor executivo</span><span class="sxs-lookup"><span data-stu-id="7a74d-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="7a74d-140">Diretor financeiro</span><span class="sxs-lookup"><span data-stu-id="7a74d-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="7a74d-141">Diretor de operações</span><span class="sxs-lookup"><span data-stu-id="7a74d-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="7a74d-142">Clique em **Salvar**e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="7a74d-143">Feche a guia do **Centro de administração do Office** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="7a74d-144">Em seguida, você pode cria um conjunto de sites de executivos e permitir que apenas os membros do grupo executivos para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="7a74d-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="7a74d-145">Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="7a74d-146">Na guia do **Centro de administração do Office** , clique em **centrais de Admin > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="7a74d-147">Na guia do **Centro de administração do SharePoint** , clique em **Novo > conjunto de sites particulares**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="7a74d-148">No painel de novo conjunto de sites, digite **executivos** em **título**, executivos na caixa URL, especifique o nome da sua conta de administrador global no **administrador**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="7a74d-p104">Aguarde até que o novo conjunto de sites foi criado. Quando concluir, copie a URL do novo conjunto de sites executivos e colá-lo em uma nova guia do navegador.</span><span class="sxs-lookup"><span data-stu-id="7a74d-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="7a74d-151">No canto direito superior do conjunto de sites **executivos** , clique no ícone configurações e, em seguida, clique em **compartilhado com**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="7a74d-152">Em **compartilhamento 'Executivos'**, clique em **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="7a74d-153">Na lista de grupos do SharePoint, clique em **Membros de executivos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="7a74d-154">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="7a74d-155">Em **compartilhamento 'Executivos'**, digite **executivos**, clique no grupo **executivos** e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="7a74d-156">Feche a guia **pessoas e grupos** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="7a74d-157">Em seguida, você permitir que todos acessar o conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="7a74d-158">A partir da guia do **Centro de administração do SharePoint** , copie a URL do conjunto de sites de vendas e colá-lo em uma nova guia do navegador..</span><span class="sxs-lookup"><span data-stu-id="7a74d-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="7a74d-159">No canto superior direito, clique no ícone configurações e, em seguida, clique em **compartilhado com**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="7a74d-160">Em **compartilhamento 'Conjunto de sites de vendas'**, clique em **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="7a74d-161">Na lista de grupos do SharePoint, clique em **membros do conjunto de sites de vendas**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="7a74d-162">Na página **pessoas e grupos** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="7a74d-163">Em **compartilhamento 'Conjunto de sites de vendas'**, digite **todos**, clique em **todos exceto os usuários externos**e, em seguida, clique em **compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="7a74d-164">Feche as guias de **conjunto de sites de vendas** e **do SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="7a74d-165">Em seguida, você pode entrar com uma conta executiva e cria um documento no conjunto de sites executivos.</span><span class="sxs-lookup"><span data-stu-id="7a74d-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="7a74d-166">Na guia **Página inicial do Microsoft Office** , clique no ícone de usuário no canto superior direito e clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="7a74d-167">Vá para [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="7a74d-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="7a74d-168">Na página do **Office 365 entrar** , clique em **usar outra conta**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="7a74d-169">Digite o nome da conta **CEO** e sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="7a74d-170">Em uma nova guia do navegador, digite a URL para o conjunto de sites de executivos ( **https://**\<nome da organização >**.sharepoint.com/sites/executives**).</span><span class="sxs-lookup"><span data-stu-id="7a74d-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="7a74d-171">Clique em **documentos**, clique em **novo** e clique em **Documento do Word**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="7a74d-172">Clique na barra de título e digite **SensitiveData-BeforeIRM**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="7a74d-173">Clique no corpo do documento e digite **minutos da reunião placa mais recente**e clique em **executivos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="7a74d-174">Você deverá ver **SensitiveData-BeforeIRM.docx** na pasta **Documents** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="7a74d-175">Em seguida, você pode baixar uma cópia local do documento SensitiveData-BeforeIRM.docx e depois enviá-lo acidentalmente ao conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="7a74d-176">No computador local, crie uma nova pasta (por exemplo, c\\TLGs\\SensitiveDataTestFiles).</span><span class="sxs-lookup"><span data-stu-id="7a74d-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="7a74d-177">Na guia **documentos** do seu navegador, selecione o documento **SensitiveData-BeforeIRM.docx** , clique nas reticências e, em seguida, clique em **Baixar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="7a74d-178">Armazene um documento **SensitiveData-BeforeIRM.docx** na pasta criada na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="7a74d-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="7a74d-179">Em uma nova guia do navegador, digite a URL para o conjunto de sites de vendas ( **https://**\<nome da organização >**.sharepoint.com/sites/sales**).</span><span class="sxs-lookup"><span data-stu-id="7a74d-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="7a74d-180">Clique na pasta de **documentos** do que o **conjunto de sites de vendas**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="7a74d-181">Clique em **carregar**e, em seguida, especifique **SensitiveData-BeforeIRM.docx** documento na pasta criada na etapa 1 e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="7a74d-182">Verifique se o documento **SensitiveData-BeforeIRM.docx** na pasta **Documents** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="7a74d-183">Feche as guias de **vendas** e **do SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="7a74d-184">Em seguida, você pode entrar como User5 e tenta abrir o documento SensitiveData-BeforeIRM.docx no conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="7a74d-185">Na guia **Página inicial do Microsoft Office** , clique no ícone de usuário no canto superior direito e clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="7a74d-186">Vá para [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="7a74d-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="7a74d-187">Na página do **Office 365 entrar** , clique em **usar outra conta**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="7a74d-188">Digite o nome da conta User5 e sua senha e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="7a74d-189">Em uma nova guia do navegador, digite a URL para o conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="7a74d-190">Na pasta **documentos** do que o **conjunto de sites de vendas**, clique no documento de **SensitiveData-BeforeIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="7a74d-191">Você deve ver seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7a74d-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="7a74d-192">Feche as guias de **documentos** e o **conjunto de sites de vendas** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="7a74d-193">Ao postar acidentalmente o documento SensitiveData-BeforeIRM.docx no conjunto de sites de vendas, CEO ignorada a segurança de permissões do conjunto de sites executivos.</span><span class="sxs-lookup"><span data-stu-id="7a74d-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="7a74d-194">Para preparar o Office 365 para fases 3 e 4, habilite o IRM para o SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7a74d-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="7a74d-195">Na guia **Página inicial do Microsoft Office** , clique no ícone de usuário no canto superior direito e clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="7a74d-196">Vá para [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="7a74d-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="7a74d-197">Na página do **Office 365 entrar** , clique no nome da conta de administrador global, digite sua senha e, em seguida, clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="7a74d-198">Na guia **Página inicial do Microsoft Office** , clique em **Admin > centrais de Admin > SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="7a74d-199">Na guia do **Centro de administração do SharePoint** , clique em **configurações**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="7a74d-200">Na página **configurações** , na seção **Gerenciamento de direitos de informação (IRM)** , selecione **usar o serviço IRM especificado na sua configuração**e, em seguida, selecione **Atualizar configurações de IRM**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="7a74d-201">Feche a guia do **Centro de administração do SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="7a74d-202">Fase 3: Usar SharePoint Information Rights Management com um grupo particular do Office 365</span><span class="sxs-lookup"><span data-stu-id="7a74d-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="7a74d-203">Nesta fase, você usa SharePoint Information Rights Management com um grupo particular do Office 365 para proteger o acesso a um documento com informações confidenciais, mesmo quando ela é postada em um site com permissões open.</span><span class="sxs-lookup"><span data-stu-id="7a74d-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="7a74d-204">Primeiro, você pode habilitar e configurar o IRM para a biblioteca de documentos do conjunto de sites executivos.</span><span class="sxs-lookup"><span data-stu-id="7a74d-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="7a74d-205">Em uma nova guia do navegador, digite a URL para o conjunto de sites de executivos.</span><span class="sxs-lookup"><span data-stu-id="7a74d-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="7a74d-206">Clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="7a74d-207">No canto superior direito, clique no ícone configurações e clique em **definições da biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="7a74d-208">Na página **configurações** , em **permissões e gerenciamento**, clique em **Gerenciamento de direitos de informação**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="7a74d-209">Na página **Configurações de gerenciamento de direitos de informações** :</span><span class="sxs-lookup"><span data-stu-id="7a74d-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="7a74d-210">Selecione **Restringir permissão aos documentos essa biblioteca no download**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="7a74d-211">Para **criar um título de política de permissão**, digite **executivos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="7a74d-212">Para **Adicionar uma descrição da política de permissão**, digite o **IRM para executivos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="7a74d-213">Clique em **Mostrar opções**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="7a74d-214">Em **definir configurações adicionais do IRM biblioteca**, selecione **não permitir que os usuários carreguem documentos que não têm suporte para IRM**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="7a74d-215">Em **Configurar direitos de acesso de documento**, selecione **Permitir visualizadores para imprimir** e **visualizadores de permissões para gravar em uma cópia do documento baixado**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="7a74d-216">Em **definir proteção de grupo e o intervalo de credenciais**, selecione **Permitir proteção de grupo** e para o **grupo padrão**, digite **executivos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="7a74d-217">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-217">Click **OK**.</span></span>
    
<span data-ttu-id="7a74d-218">Em seguida, atuando como CEO, você carregar um novo documento na pasta de documentos de executivos, baixá-lo e acidentalmente carregá-la para a pasta de documentos de vendas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="7a74d-219">Abra a pasta local onde você armazenou o documento **SensitiveData-BeforeIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="7a74d-220">Clique com o botão **SensitiveData-BeforeIRM.docx**e clique em **Copiar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="7a74d-221">Com o botão direito na pasta e, em seguida, clique em **Colar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="7a74d-222">Renomeie o novo arquivo **SensitiveData-BeforeIRM - Copy.docx** para **SensitiveData-AfterIRM.docx**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="7a74d-223">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no ícone de usuário no canto superior direito e clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="7a74d-224">Vá para [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="7a74d-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="7a74d-225">Na página do **Office 365 entrar** , clique no nome de conta do CEO, digite sua senha e, em seguida, clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="7a74d-226">Em uma nova guia do navegador, digite a URL para o conjunto de sites de executivos.</span><span class="sxs-lookup"><span data-stu-id="7a74d-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="7a74d-227">Na página de **documentos** , clique em **carregar**, especifique o documento **SensitiveData-AfterIRM.docx** em sua pasta local e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="7a74d-228">Selecione o novo documento **SensitiveData-AfterIRM.docx** na página de **documentos** , clique nas reticências (…) na barra de menus e, em seguida, clique em **Baixar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="7a74d-229">Quando solicitado, salve o documento de **SensitiveData-AfterIRM.docx** na sua pasta local, substituindo a versão original.</span><span class="sxs-lookup"><span data-stu-id="7a74d-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="7a74d-230">Feche a guia para a página de **documentos** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="7a74d-231">Em uma nova guia do navegador, digite a URL para o conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="7a74d-232">Clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="7a74d-233">Na página de **documentos** , clique em **carregar**, especifique o documento **SensitiveData-AfterIRM.docx** em sua pasta local e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="7a74d-234">Feche as guias de **conjunto de sites de vendas** e **do SharePoint** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="7a74d-235">Em seguida, atuando como um usuário normal, você tenta acessar o documento **SensitiveData-AfterIRM.docx** da pasta de documentos de vendas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="7a74d-236">Na guia **Página inicial do Microsoft Office** no seu navegador, clique no ícone de usuário no canto superior direito e clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="7a74d-237">Vá para [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="7a74d-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="7a74d-238">Na página do **Office 365 entrar** , clique no nome da conta de User5, digite sua senha e, em seguida, clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="7a74d-239">Em uma nova guia do navegador, digite a URL para o conjunto de sites de vendas.</span><span class="sxs-lookup"><span data-stu-id="7a74d-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="7a74d-240">Clique em **documentos**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="7a74d-241">Na página de **documentos** , abra o documento de **SensitiveData-AfterIRM.docx** .</span><span class="sxs-lookup"><span data-stu-id="7a74d-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="7a74d-242">Você deverá ver uma mensagem que declara "Desculpe, Word Online não é possível abrir este documento porque ele está protegido por gerenciamento de direitos de informação (IRM)."</span><span class="sxs-lookup"><span data-stu-id="7a74d-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="7a74d-p105">Clique em **Editar no Word**. Você será solicitado a se desejar abrir o arquivo. Clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="7a74d-p106">Você será solicitado a sign-in. Digite o nome da conta da conta User5 e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="7a74d-p107">Você será solicitado a fornecer a senha. Digite a senha para a conta de User5 e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="7a74d-250">Você deverá ver a uma mensagem que declara: "Você não tem as credenciais que permitam abrir este documento".</span><span class="sxs-lookup"><span data-stu-id="7a74d-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="7a74d-251">Clique em **não**.</span><span class="sxs-lookup"><span data-stu-id="7a74d-251">Click **No**.</span></span>
    
<span data-ttu-id="7a74d-p108">Outra maneira para ver a proteção de IRM é examinar os arquivos em sua pasta local. O **SensitiveData-AfterIRM.docx** deve ser muito maior do que o arquivo **SensitiveData-BeforeIRM.docx** . O arquivo **SensitiveData-AfterIRM.docx** é criptografado e as informações de proteção de IRM adicionou a ele.</span><span class="sxs-lookup"><span data-stu-id="7a74d-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a74d-255">Veja também</span><span class="sxs-lookup"><span data-stu-id="7a74d-255">See Also</span></span>

[<span data-ttu-id="7a74d-256">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="7a74d-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="7a74d-257">Ambiente de desenvolvimento e teste de configuração de base</span><span class="sxs-lookup"><span data-stu-id="7a74d-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="7a74d-258">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="7a74d-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="7a74d-259">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="7a74d-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


