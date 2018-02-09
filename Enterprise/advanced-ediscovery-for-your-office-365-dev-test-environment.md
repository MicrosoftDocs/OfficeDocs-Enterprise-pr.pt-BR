---
title: "Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento e teste do Office 365"
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
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: "Resumo: Configurar e demonstrar o eDiscovery avançadas do Office 365 com dados de exemplo no seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: c55a466f05eba4e9f06ce2930dfc7c762d7fceae
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="4bdbd-103">Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="4bdbd-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="4bdbd-104">**Resumo:** Configurar e demonstrar o eDiscovery avançadas do Office 365 com dados de exemplo no seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="4bdbd-p101">Descoberta eletrônica avançada do Office 365 permite que você rapidamente encontrar e analisar informações relevantes entre os dados armazenados no Office 365, incluindo email e documentos. Isso pode salvar uma enorme quantidades de tempo e despesas, especialmente nas situações de litígio. Para obter mais informações, consulte [eDiscovery avançadas do Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="4bdbd-p101">Office 365 Advanced eDiscovery allows you to quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="4bdbd-108">Com as instruções neste artigo, você cria um pequeno conjunto de dados para uma disputa de contrato fictícia e o analisa com a Descoberta Eletrônica Avançada.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="4bdbd-109">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="4bdbd-110">Fase 1: Criar seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="4bdbd-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="4bdbd-111">Se você quiser testar eDiscovery avançado de forma leve com os requisitos mínimos, siga as instruções na fase 2 e a fase 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="4bdbd-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="4bdbd-112">Se você quiser testar eDiscovery avançada em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="4bdbd-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="4bdbd-p102">Testar eDiscovery avançada não exige o ambiente simulado enterprise, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa realizar testes e experimentação em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="4bdbd-115">Fase 2: Criar dados de exemplo para a Descoberta Eletrônica Avançada</span><span class="sxs-lookup"><span data-stu-id="4bdbd-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="4bdbd-116">Neste procedimento, você criará mensagens de email que, mais tarde, serão analisadas em um caso de Descoberta Eletrônica Avançada.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="4bdbd-117">Abra o Internet Explorer e entrar no [https://outlook.com](https://outlook.com) para a conta do Outlook que você criou na fase 2 do[ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="4bdbd-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="4bdbd-118">Se estiver usando o ambiente de desenvolvimento e teste leve, abra uma sessão particular do Internet Explorer e entre com o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="4bdbd-119">Se você estiver usando o ambiente de desenvolvimento e teste de enterprise simulado, use o portal Azure ([https://portal.azure.com](https://portal.azure.com)) para se conectar à máquina virtual CLIENT1 e entrar em CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="4bdbd-120">Na guia **Email do Outlook** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="4bdbd-p103">Em **para**, digite o endereço de email da conta User6 de sua assinatura de avaliação ( **user6 @.** <organization name> **. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="4bdbd-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="4bdbd-123">Para o assunto, digite **o email de teste 1**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="4bdbd-124">No corpo, digite **Tailspin rascunho de contrato**e clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="4bdbd-125">Na guia **Email do Outlook** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="4bdbd-126">Na caixa **para**, digite o endereço de email da conta User6 de sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="4bdbd-127">Para o assunto, digite **o email de teste 2**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="4bdbd-128">No corpo, digite **Tailspin almoço reunião**e, em seguida, clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="4bdbd-129">Na guia **Email do Outlook** , clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="4bdbd-130">Na caixa **para**, digite o endereço de email da conta User6 de sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="4bdbd-131">Para o assunto, digite **o email de teste 3**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="4bdbd-132">No corpo, digite **divergência de contrato Tailspin**e, em seguida, clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="4bdbd-133">Clique no ícone de usuário no canto superior direito e clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="4bdbd-134">Abra uma nova guia e entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) com o nome da conta e a senha da conta de User6 de sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="4bdbd-135">Na guia **portal do Office 365** , clique em **email**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="4bdbd-136">Na guia **email - User6 - Outlook** , verifique se que o User6 recebidas todos os três e-mails de conta de email do Outlook.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-136">On the **Mail - User6 - Outlook** tab, verify that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="4bdbd-137">Alterne para a **guia portal do Office 365** para User6.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="4bdbd-138">Clique no ícone de usuário no canto superior direito e, em seguida, clique em **desconectá-.**</span><span class="sxs-lookup"><span data-stu-id="4bdbd-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="4bdbd-139">Neste procedimento, você criará dois documentos do Word que, mais tarde, serão analisados em um caso de Descoberta Eletrônica Avançada.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="4bdbd-140">Na página do **Office** , clique em **entrar,** logon com as credenciais da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="4bdbd-141">Em uma nova guia, acessar a URL do seu site do SharePoint de produção: **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="4bdbd-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="4bdbd-142">Na guia **conjunto de sites de produção** , em **documentos**, clique em **New > documento do Word**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="4bdbd-143">Na página **Online do Word** , digite **contrato de rascunho Tailspin**, aguarde até que ele exibe **Saved** no título e feche a guia de página **Online do Word** .</span><span class="sxs-lookup"><span data-stu-id="4bdbd-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="4bdbd-144">Na guia **conjunto de sites de produção** , em **documentos**, clique em **New > documento do Word**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="4bdbd-145">Na guia **On-line do Word** , digite **Tailspin contrato contestação observações**, aguarde até que ele exibe **Saved** no título e feche a guia **Word Online** .</span><span class="sxs-lookup"><span data-stu-id="4bdbd-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="4bdbd-146">Na guia **conjunto de sites de produção** , você deverá ver o **documento** e **Document1** na lista de documentos.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="4bdbd-147">Feche a guia de **conjunto de sites de produção** .</span><span class="sxs-lookup"><span data-stu-id="4bdbd-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="4bdbd-148">Fase 3: Uso eDiscovery avançadas para uma disputa legal</span><span class="sxs-lookup"><span data-stu-id="4bdbd-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="4bdbd-p104">Infelizmente, uma contestação contrato entre sua organização e Tailspin Toys atingiu o ponto de ações legais. Neste procedimento, você cria e configurar um caso de eDiscovery avançadas para procurar e analisar o email e documentos que contêm o texto "Contrato Tailspin".</span><span class="sxs-lookup"><span data-stu-id="4bdbd-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="4bdbd-151">O processo de uso da Descoberta Eletrônica Avançada é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4bdbd-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="4bdbd-152">Criar uma pesquisa na segurança &amp; Centro de conformidade, analisar seus resultados e prepare os resultados para eDiscovery avançado.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="4bdbd-153">Criar e configurar um caso de Descoberta Eletrônica Avançada e analisar os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="4bdbd-154">Neste procedimento, você cria uma pesquisa na segurança &amp; conformidade center para o "Contrato Tailspin", procure os resultados e, em seguida, preparar os resultados eDiscovery avançado.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="4bdbd-155">Na guia **portal do Office 365** , clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="4bdbd-156">No painel de navegação à esquerda da guia Administração Central, clique em **centrais de Admin > conformidade**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="4bdbd-157">Sobre o **segurança &amp; conformidade** guia, clique em **permissões**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="4bdbd-158">Na lista de **permissões** , clique duas vezes em **Gerenciamento da organização**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="4bdbd-159">Na janela do **Grupo de função** , em **membros**, clique no sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="4bdbd-160">Na janela **Selecionar membros** , duas vezes no nome da sua conta de administrador e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="4bdbd-161">Na janela do **Grupo de função** , clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="4bdbd-162">Na lista de **permissões** , clique duas vezes em **Gerenciador de descoberta eletrônica**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="4bdbd-163">Na janela do **Grupo de função** , **eDiscovery administrador**, clique no ícone mais.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="4bdbd-164">Na janela **Selecionar membros** , duas vezes no nome da sua conta de administrador e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="4bdbd-165">Na janela do **Grupo de função** , clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="4bdbd-166">No painel de navegação esquerdo, clique em **pesquisa &amp; investigação > pesquisa de conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="4bdbd-167">Clique no ícone de adição para adicionar uma pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="4bdbd-168">Na janela **nova pesquisa** , digite a **pesquisa de contrato Tailspin** no **nome**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="4bdbd-169">No **onde você deseja com a aparência?**, clique em **Pesquisar em todos os lugares,** selecione **Exchange**, **SharePoint**e **As pastas públicas**e, em seguida, clique em **próxima.**</span><span class="sxs-lookup"><span data-stu-id="4bdbd-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="4bdbd-170">Em **que você deseja fazer conosco para procurar?**, digite **contrato Tailspin**e clique em **Pesquisar**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="4bdbd-171">Na lista de pesquisas, clique no nome de **pesquisa de contrato Tailspin** .</span><span class="sxs-lookup"><span data-stu-id="4bdbd-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="4bdbd-p105">No painel de **pesquisa de contrato Tailspin** , clique em **resultados da pesquisa de visualização** em **resultados**. Você deverá ver uma janela listando os dois documentos sobre o site do SharePoint de produção ( **documento** e **Document1**) e os emails de **e-mail de teste 1** e **3 de e-mail de teste** para User6. Feche a janela.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="4bdbd-175">No painel de **pesquisa de conteúdo** , **Analisar resultados com eDiscovery avançada**, clique em **resultados de visualização para análise**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="4bdbd-176">Na janela de **resultados para pesquisa de contrato Tailspin mais Prepare a pesquisa** , clique em **Preparar** e aguarde a conclusão.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="4bdbd-177">Neste procedimento, você criará um novo caso de Descoberta Eletrônica Avançada e analisará os resultados da pesquisa de contrato com a Tailspin.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="4bdbd-178">No painel de navegação esquerdo, clique em **Descoberta eletrônica** em **pesquisa &amp; investigação**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="4bdbd-179">No painel de **Descoberta eletrônica** , clique em **Ir para descoberta eletrônica avançada**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="4bdbd-180">Na guia **Avançado de descoberta eletrônica** , clique no ícone mais para adicionar um novo caso.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="4bdbd-p106">No painel de **caso de adicionar** , digite **disputa do contrato Tailspin** em **nome**e clique em **Okey**. Aguarde o caso a ser criado.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="4bdbd-183">Clique duas vezes o caso de **disputa do contrato Tailspin** na lista.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="4bdbd-p107">Na lista do **contêiner** , clique no contêiner de **pesquisa de contrato Tailspin** e, em seguida, clique em **processar**. Aguarde o processamento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="4bdbd-186">Quando **processo: concluído** aparece na parte inferior da janela, clique em **processo de resumo** no painel de navegação à esquerda para ver um resumo.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="4bdbd-187">No painel de navegação superior, clique em **Analisar**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="4bdbd-188">Na página **instalação** , em **temas**, digite **3** no **número máximo de temas**.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="4bdbd-p108">Clique em **Analisar** e aguarde concluir a análise. Você deverá ver uma série de gráficos de pizza com a análise da população de destino, documentos, emails e anexos. Para obter mais informações, consulte [Exibindo analisar resultados](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="4bdbd-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="4bdbd-192">Agora, você pode usar esse ambiente para criar novo conteúdo, novas pesquisas e casos e também para continuar os testes com a Descoberta Eletrônica Avançada no Office 365.</span><span class="sxs-lookup"><span data-stu-id="4bdbd-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4bdbd-193">Veja também</span><span class="sxs-lookup"><span data-stu-id="4bdbd-193">See Also</span></span>

[<span data-ttu-id="4bdbd-194">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="4bdbd-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="4bdbd-195">Ambiente de desenvolvimento e teste de configuração de base</span><span class="sxs-lookup"><span data-stu-id="4bdbd-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="4bdbd-196">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="4bdbd-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="4bdbd-197">DirSync para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="4bdbd-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4bdbd-198">Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="4bdbd-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="4bdbd-199">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="4bdbd-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="4bdbd-200">Descoberta eletrônica avançada do Office 365</span><span class="sxs-lookup"><span data-stu-id="4bdbd-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


