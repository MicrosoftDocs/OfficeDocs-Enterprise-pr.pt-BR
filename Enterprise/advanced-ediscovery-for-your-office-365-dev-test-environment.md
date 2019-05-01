---
title: Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento e teste do Office 365
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
description: 'Resumo: Configure e demonstre a Descoberta Eletrônica Avançada do Office 365 com dados de amostra no seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: b1cf2714f79d38e5a3349b331cee0862cd6aac52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491217"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="76485-103">Descoberta Eletrônica Avançada para o ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="76485-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="76485-104">**Resumo:** Configure e demonstre a Descoberta Eletrônica Avançada do Office 365 com dados de amostra no seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="76485-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="76485-105">A descoberta eletrônica avançada do Office 365 permite que você encontre e analise rapidamente informações relevantes nos dados armazenados no Office 365, incluindo emails e documentos.</span><span class="sxs-lookup"><span data-stu-id="76485-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="76485-106">Isso pode poupar enormes quantidades de tempo e despesas, especialmente em situações de litígio.</span><span class="sxs-lookup"><span data-stu-id="76485-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="76485-107">Para saber mais, consulte [Descoberta Eletrônica Avançada do Office 365](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span><span class="sxs-lookup"><span data-stu-id="76485-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="76485-108">Com as instruções neste artigo, você cria um pequeno conjunto de dados para uma disputa de contrato fictícia e o analisa com a Descoberta Eletrônica Avançada.</span><span class="sxs-lookup"><span data-stu-id="76485-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="76485-109">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual de todos os artigos da pilha da Guia do Laboratório de Teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="76485-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="76485-110">Fase 1: Criar seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="76485-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="76485-111">Se você só quiser testar a descoberta eletrônica avançada de forma leve com os requisitos mínimos, siga as instruções na fase 2 e na fase 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="76485-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="76485-112">Se você quiser testar a descoberta eletrônica avançada em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="76485-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="76485-113">O teste de descoberta eletrônica avançada não requer o ambiente de empresa simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta dos serviços de domínio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="76485-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="76485-114">Ele é fornecido aqui como uma opção para que você possa executar testes e experimentos em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="76485-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="76485-115">Fase 2: Criar dados de exemplo para a Descoberta Eletrônica Avançada</span><span class="sxs-lookup"><span data-stu-id="76485-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="76485-116">Neste procedimento, você criará mensagens de email que, mais tarde, serão analisadas em um caso de Descoberta Eletrônica Avançada.</span><span class="sxs-lookup"><span data-stu-id="76485-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="76485-117">Abra o Internet Explorer e entre [https://outlook.com](https://outlook.com) na conta do Outlook que você criou na fase 2 do[ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="76485-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="76485-118">Se estiver usando o ambiente de desenvolvimento e teste leve, abra uma sessão particular do Internet Explorer e entre com o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="76485-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="76485-119">Se você estiver usando o ambiente de desenvolvimento/teste corporativo simulado, use o portal do[https://portal.azure.com](https://portal.azure.com)Azure () para se conectar à máquina virtual CLIENT1 e, em seguida, entre no CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="76485-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="76485-120">Na guia **Email do Outlook**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="76485-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="76485-121">Em **para**, digite o endereço de email da conta usuário6 da sua assinatura de avaliação ( **usuário6 @.**<organization name></span><span class="sxs-lookup"><span data-stu-id="76485-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name></span></span> <span data-ttu-id="76485-122">**. onmicrosoft.com**).</span><span class="sxs-lookup"><span data-stu-id="76485-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="76485-123">Para o assunto, digite **Email de teste 1**.</span><span class="sxs-lookup"><span data-stu-id="76485-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="76485-124">No corpo, digite **Rascunho do contrato com a Tailspin** e clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="76485-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="76485-125">Na guia **Email do Outlook**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="76485-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="76485-126">Em **Para**, digite o endereço de email da conta Usuário:6 da sua assinatura de teste.</span><span class="sxs-lookup"><span data-stu-id="76485-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="76485-127">Para o assunto, digite **Email de teste 2**.</span><span class="sxs-lookup"><span data-stu-id="76485-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="76485-128">No corpo, digite **Reunião de almoço com a Tailspin** e clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="76485-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="76485-129">Na guia **Email do Outlook**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="76485-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="76485-130">Em **Para**, digite o endereço de email da conta Usuário:6 da sua assinatura de teste.</span><span class="sxs-lookup"><span data-stu-id="76485-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="76485-131">Para o assunto, digite **Email de teste 3**.</span><span class="sxs-lookup"><span data-stu-id="76485-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="76485-132">No corpo, digite **Desacordo no contrato com a Tailspin** e clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="76485-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="76485-133">Clique no ícone de usuário no canto superior direito e depois clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="76485-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="76485-134">Abra uma nova guia e entre no portal do Office 365 ([https://www.office.com](https://www.office.com)) com o nome da conta e a senha da conta usuário6 da sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="76485-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="76485-135">Na guia do **portal do Office 365**, clique em **Email**.</span><span class="sxs-lookup"><span data-stu-id="76485-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="76485-136">Na guia **mail-usuário6-Outlook** , verifique se usuário6 recebeu todos os três emails da conta de email do Outlook.</span><span class="sxs-lookup"><span data-stu-id="76485-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="76485-137">Volte para a **guia do portal do Office 365** de Usuário6.</span><span class="sxs-lookup"><span data-stu-id="76485-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="76485-138">Clique no ícone de usuário no canto superior direito e depois clique em **Sair.**</span><span class="sxs-lookup"><span data-stu-id="76485-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="76485-139">Neste procedimento, você criará dois documentos do Word que, mais tarde, serão analisados em um caso de Descoberta Eletrônica Avançada.</span><span class="sxs-lookup"><span data-stu-id="76485-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="76485-140">Na página do **Office**, clique em **Entrar** e entre com as credenciais da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="76485-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="76485-141">em uma nova guia, acesse a URL do site de produção do SharePoint: **https://** <fictional organization name> **. sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="76485-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="76485-142">Na guia **Conjunto de sites de produção**, em **Documentos**, clique em **Novo > Documento do Word**.</span><span class="sxs-lookup"><span data-stu-id="76485-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="76485-143">Na página do **Word Online**, digite **Contrato de rascunho com a Tailspin**, aguarde até que **Salvo** apareça no título e feche a guia da página do **Word Online**.</span><span class="sxs-lookup"><span data-stu-id="76485-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="76485-144">Na guia **Conjunto de sites de produção**, em **Documentos**, clique em **Novo > Documento do Word**.</span><span class="sxs-lookup"><span data-stu-id="76485-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="76485-145">	Na guia do *\*Word Online*\*, digite *\*Notas da disputa contratual com a Tailspin*\*, aguarde até que *\*Salvo** apareça no título e feche a guia do *\*Word Online*\*.</span><span class="sxs-lookup"><span data-stu-id="76485-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="76485-146">Na guia **Conjunto de sites de produção**, você verá **Documento** e **Documento1** na lista de documentos.</span><span class="sxs-lookup"><span data-stu-id="76485-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="76485-147">Feche a guia **Coleção do site de produção**.</span><span class="sxs-lookup"><span data-stu-id="76485-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="76485-148">Fase 3: usar a descoberta eletrônica avançada para uma disputa legal</span><span class="sxs-lookup"><span data-stu-id="76485-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="76485-149">Infelizmente, uma disputa de contrato entre a organização e a Tailspin Toys chegou ao ponto de desencadear uma ação legal.</span><span class="sxs-lookup"><span data-stu-id="76485-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="76485-150">Neste procedimento, você criará e configurará uma ocorrência de descoberta eletrônica avançada para pesquisar e analisar emails e documentos que contenham o texto "Tailspin Contract".</span><span class="sxs-lookup"><span data-stu-id="76485-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="76485-151">O processo de uso da Descoberta Eletrônica Avançada é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="76485-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="76485-152">Criar uma pesquisa no centro de &amp; conformidade de segurança, analisar seus resultados e, em seguida, preparar os resultados para descoberta eletrônica avançada.</span><span class="sxs-lookup"><span data-stu-id="76485-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="76485-153">Criar e configurar um caso de Descoberta Eletrônica Avançada e analisar os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="76485-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="76485-154">Neste procedimento, você cria uma pesquisa no centro de conformidade &amp; de segurança para "contrato da Tailspin", examina os resultados e, em seguida, prepara os resultados para descoberta eletrônica avançada.</span><span class="sxs-lookup"><span data-stu-id="76485-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="76485-155">Na guia do **portal do Office 365**, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="76485-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="76485-156">Na navegação à esquerda da guia Centro de administração, clique em **Centros de administração > Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="76485-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="76485-157">Na guia **conformidade &amp; de segurança** , clique em **permissões**.</span><span class="sxs-lookup"><span data-stu-id="76485-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="76485-158">Na lista **Permissões**, clique duas vezes em **Gerenciamento da Organização**.</span><span class="sxs-lookup"><span data-stu-id="76485-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="76485-159">Na janela **Grupo de Função**, em **Membros**, clique no sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="76485-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="76485-160">Na janela **Selecionar Membros**, clique duas vezes o nome da sua conta de administrador e depois clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="76485-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="76485-161">Na janela **Grupo de Funções**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="76485-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="76485-162">Na lista **Permissões**, clique duas vezes em **Gerente de Descoberta Eletrônica**.</span><span class="sxs-lookup"><span data-stu-id="76485-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="76485-163">Na janela **Grupo de Função**, em **Administrador de Descoberta Eletrônica**, clique no ícone de adição.</span><span class="sxs-lookup"><span data-stu-id="76485-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="76485-164">Na janela **Selecionar Membros**, clique duas vezes o nome da sua conta de administrador e depois clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="76485-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="76485-165">Na janela **Grupo de Funções**, clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="76485-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="76485-166">No painel de navegação à esquerda, clique em **investigação de pesquisa &amp; > conteúdo pesquisa**.</span><span class="sxs-lookup"><span data-stu-id="76485-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="76485-167">Clique no ícone de adição para adicionar uma pesquisa.</span><span class="sxs-lookup"><span data-stu-id="76485-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="76485-168">Na janela **Nova pesquisa**, digite **Pesquisa de contrato com a Tailspin** em **Nome**.</span><span class="sxs-lookup"><span data-stu-id="76485-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="76485-169">Em **Onde deseja procurar?**, clique em **Pesquisar em todos os lugares**, selecione **Exchange**, **SharePoint** e **Pastas Públicas** e depois clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="76485-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="76485-170">Em **O que você deseja que procuremos?**, digite **Contrato com a Tailspin** e clique em **Pesquisar**.</span><span class="sxs-lookup"><span data-stu-id="76485-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="76485-171">Na lista de pesquisas, clique no nome **Pesquisa de contrato com a Tailspin**.</span><span class="sxs-lookup"><span data-stu-id="76485-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="76485-172">No painel **Pesquisa de contrato com a Tailspin**, clique em **Visualizar resultados de pesquisa** em **Resultados**.</span><span class="sxs-lookup"><span data-stu-id="76485-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="76485-173">Você verá uma janela listando os dois documentos no site de produção do SharePoint ( **Document** e **Documento1**) e os emails de **teste email 1** e **testar email 3** para o usuário6.</span><span class="sxs-lookup"><span data-stu-id="76485-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="76485-174">Feche a janela.</span><span class="sxs-lookup"><span data-stu-id="76485-174">Close the window.</span></span>
    
19. <span data-ttu-id="76485-175">No painel **Pesquisa de conteúdo**, em **Analisar os resultados com a Descoberta Eletrônica Avançada**, clique em **Visualizar resultados para análise**.</span><span class="sxs-lookup"><span data-stu-id="76485-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="76485-176">Na janela **Preparar os resultados da pesquisa para a pesquisa de contrato com a Tailspin**, clique em **Preparar** e aguarde a sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="76485-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="76485-177">Neste procedimento, você criará um novo caso de Descoberta Eletrônica Avançada e analisará os resultados da pesquisa de contrato com a Tailspin.</span><span class="sxs-lookup"><span data-stu-id="76485-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="76485-178">Na navegação à esquerda, clique em **descoberta eletrônica** em \*\*investigação de pesquisa &amp; \*\*.</span><span class="sxs-lookup"><span data-stu-id="76485-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="76485-179">No painel **Descoberta Eletrônica**, clique em **Ir para Descoberta Eletrônica Avançada**.</span><span class="sxs-lookup"><span data-stu-id="76485-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="76485-180">Na guia **Descoberta Eletrônica Avançada**, clique no ícone de adição para adicionar um novo caso.</span><span class="sxs-lookup"><span data-stu-id="76485-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="76485-p106">	No painel *\*Adicionar caso*\*, digite *\*Disputa contratual com a Tailspin** em *\*Nome** e depois clique em *\*OK*\*. Aguarde até que o caso seja criado.</span><span class="sxs-lookup"><span data-stu-id="76485-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="76485-183">Clique duas vezes no caso **Disputa contratual com a Tailspin** na lista. </span><span class="sxs-lookup"><span data-stu-id="76485-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="76485-184">Na lista **contêiner** , clique no contêiner de **pesquisa de contrato** com a Tailspin e, em seguida, clique em **processar**.</span><span class="sxs-lookup"><span data-stu-id="76485-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="76485-185">Aguarde até que o processamento seja concluído.</span><span class="sxs-lookup"><span data-stu-id="76485-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="76485-186">Quando a mensagem **Processo: concluído** aparecer na parte inferior da janela, clique em **Resumo do processo** na navegação à esquerda para ver um resumo.</span><span class="sxs-lookup"><span data-stu-id="76485-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="76485-187">Na navegação superior, clique em **Analisar**.</span><span class="sxs-lookup"><span data-stu-id="76485-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="76485-188">Na página **Configuração**, em **Temas**, digite **3** em **Número máximo de temas**.</span><span class="sxs-lookup"><span data-stu-id="76485-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="76485-189">Clique em **Analisar** e aguarde a conclusão da análise.</span><span class="sxs-lookup"><span data-stu-id="76485-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="76485-190">Você verá uma série de gráficos de pizza com a análise da população-alvo, documentos, emails e anexos.</span><span class="sxs-lookup"><span data-stu-id="76485-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="76485-191">Para obter mais informações, consulte [exibir resultados de análise](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span><span class="sxs-lookup"><span data-stu-id="76485-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="76485-192">Agora, você pode usar esse ambiente para criar novo conteúdo, novas pesquisas e casos e também para continuar os testes com a Descoberta Eletrônica Avançada no Office 365.</span><span class="sxs-lookup"><span data-stu-id="76485-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="76485-193">Confira também</span><span class="sxs-lookup"><span data-stu-id="76485-193">See Also</span></span>

[<span data-ttu-id="76485-194">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="76485-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
<span data-ttu-id="76485-195">[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="76485-195">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="76485-196">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="76485-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="76485-197">DirSync para o ambiente de desenvolvimento/ teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="76485-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="76485-198">Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="76485-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="76485-199">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="76485-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="76485-200">Descoberta Eletrônica Avançada do Office 365</span><span class="sxs-lookup"><span data-stu-id="76485-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


