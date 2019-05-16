---
title: Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 'Resumo: Configure e demonstre a classificação de dados e rotular usando o cliente de proteção de informações do Azure (AIP) no seu ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: cf369894eb87381e3837a52946a0ba2b9705bf70
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067927"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="865ff-103">Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="865ff-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="865ff-104">**Resumo:** Configurar e demonstrar a classificação de dados e rotular usando o cliente de proteção de informações do Azure (AIP) em seu ambiente de desenvolvimento/teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="865ff-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="865ff-105">O cliente de proteção de informações do Azure permite que você classifique um documento antes de carregá-lo em uma pasta do SharePoint Online no Office 365.</span><span class="sxs-lookup"><span data-stu-id="865ff-105">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365.</span></span> <span data-ttu-id="865ff-106">Com as instruções deste artigo, você instala o cliente de proteção de informações do Azure e demonstra a classificação de dados.</span><span class="sxs-lookup"><span data-stu-id="865ff-106">With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification.</span></span> <span data-ttu-id="865ff-107">Confira mais informações em [proteção de informações do Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="865ff-107">For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="865ff-108">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual de todos os artigos da pilha da Guia do Laboratório de Teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="865ff-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="865ff-109">Fase 1: criar seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="865ff-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="865ff-110">Siga as instruções em [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="865ff-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="865ff-111">Fase 2: adicionar a assinatura de avaliação do Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="865ff-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="865ff-112">Nesta fase, adicione a proteção de informações do Azure ao seu ambiente de desenvolvimento/teste do Office 365 e habilite-a para suas contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="865ff-112">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts.</span></span> <span data-ttu-id="865ff-113">Se você tiver configurado o [ambiente de desenvolvimento/teste do Office 365 e EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), pule esta fase.</span><span class="sxs-lookup"><span data-stu-id="865ff-113">If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase.</span></span> <span data-ttu-id="865ff-114">A assinatura de avaliação do Enterprise Mobility Suite inclui licenças de proteção de informações do Azure.</span><span class="sxs-lookup"><span data-stu-id="865ff-114">The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="865ff-115">Primeiro, Inscreva-se em uma assinatura de avaliação do Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="865ff-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="865ff-116">Inscreva-se para obter uma assinatura de avaliação do Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="865ff-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="865ff-117">No Internet Explorer ou no navegador, acesse [http://admin.microsoft.com](http://admin.microsoft.com) e entre com sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="865ff-117">In Internet Explorer or your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="865ff-118">Na guia **Microsoft Office Home** , clique no bloco **administrador** .</span><span class="sxs-lookup"><span data-stu-id="865ff-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="865ff-119">Na guia Administração do Office 365, na navegação à esquerda, clique em **cobrança _GT_ comprar serviços**.</span><span class="sxs-lookup"><span data-stu-id="865ff-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="865ff-120">Na página **comprar serviços** , encontre o item do **Azure Information Protection Premium P2** .</span><span class="sxs-lookup"><span data-stu-id="865ff-120">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item.</span></span> <span data-ttu-id="865ff-121">Passe o mouse sobre ele e clique em **Iniciar avaliação gratuita**.</span><span class="sxs-lookup"><span data-stu-id="865ff-121">Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="865ff-122">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="865ff-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="865ff-123">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="865ff-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="865ff-124">Em seguida, habilite a licença de proteção de informações do Azure para todas as contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="865ff-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="865ff-125">Na guia centro de administração do Microsoft 365, clique em **usuários**.</span><span class="sxs-lookup"><span data-stu-id="865ff-125">On the Microsoft 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="865ff-126">Na lista de contas de usuário, selecione sua conta de administrador global e clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="865ff-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="865ff-127">Ative a licença de produto do **Azure Information Protection Premium P2** para **ativado**, clique em **salvar** e clique em **fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="865ff-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="865ff-128">Repita as etapas 2 e 3 para suas outras contas de usuário (usuário 1 até usuário 5).</span><span class="sxs-lookup"><span data-stu-id="865ff-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="865ff-129">Seu ambiente de desenvolvimento/teste do Office 365 agora tem:</span><span class="sxs-lookup"><span data-stu-id="865ff-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="865ff-130">Assinaturas de avaliação do Office 365 E5 Enterprise e Azure Information Protection.</span><span class="sxs-lookup"><span data-stu-id="865ff-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="865ff-131">Todas as suas contas de usuário habilitadas para usar a proteção de informações do Office 365 E5 Enterprise e do Azure.</span><span class="sxs-lookup"><span data-stu-id="865ff-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="865ff-132">Fase 3: demonstrar a classificação dos dados</span><span class="sxs-lookup"><span data-stu-id="865ff-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="865ff-133">Nesta fase, você demonstra a classificação de dados usando o cliente de proteção de informações do Azure e a política de proteção de informações padrão do Azure.</span><span class="sxs-lookup"><span data-stu-id="865ff-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="865ff-134">Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, primeiro deverá instalar o Office 2016 em CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="865ff-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="865ff-135">Use seu navegador e vá para o [portal do Azure](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="865ff-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="865ff-136">Clique em **grupos de recursos >** [seu nome de grupo de recursos] **_GT_ CLIENT1 > conectar**.</span><span class="sxs-lookup"><span data-stu-id="865ff-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="865ff-137">Em CLIENT1, execute o Internet Explorer, vá para o portal do [http://admin.microsoft.com](http://admin.microsoft.com)Office em e entre com o nome da conta e senha do User5.</span><span class="sxs-lookup"><span data-stu-id="865ff-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="865ff-138">Na guia **Microsoft Office Home**, clique em **Instalar o Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="865ff-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="865ff-139">Execute o download quando solicitado e clique em **Sim** quando solicitado pelo controle de conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="865ff-139">Run the download when prompted and click **Yes** when prompted by User Account Control.</span></span> <span data-ttu-id="865ff-140">Aguarde a instalação do Office.</span><span class="sxs-lookup"><span data-stu-id="865ff-140">Wait for Office to install.</span></span> <span data-ttu-id="865ff-141">Ao concluir, clique em **fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="865ff-141">When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="865ff-142">Em seguida, instale o cliente de proteção de informações do Azure.</span><span class="sxs-lookup"><span data-stu-id="865ff-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="865ff-143">No navegador ou no Internet Explorer, vá para a [página de download da proteção de informações do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="865ff-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="865ff-144">Se você estiver usando a versão leve do ambiente de desenvolvimento/teste do Office 365, use o navegador no computador local.</span><span class="sxs-lookup"><span data-stu-id="865ff-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="865ff-145">Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, execute o Internet Explorer a partir de CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="865ff-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="865ff-146">Na página Download da **proteção de informações do Microsoft Azure** , clique em **baixar**, clique em **AzInfoProtection. exe**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="865ff-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="865ff-147">Quando solicitado, execute AzInfoProtection. exe.</span><span class="sxs-lookup"><span data-stu-id="865ff-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="865ff-148">Na caixa **instalar o cliente de proteção de informações do Azure** , clique em **concordo**e, em seguida, clique em **Sim** quando solicitado pelo controle de conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="865ff-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="865ff-149">Na caixa **concluído com êxito** , clique em **fechar.**</span><span class="sxs-lookup"><span data-stu-id="865ff-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="865ff-150">Em seguida, demonstre a classificação de documentos.</span><span class="sxs-lookup"><span data-stu-id="865ff-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="865ff-151">Clique no ícone do **Word** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="865ff-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="865ff-152">Quando solicitado, entre com o nome da conta e senha do User5.</span><span class="sxs-lookup"><span data-stu-id="865ff-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="865ff-153">Se você acabou de instalar o Office 2016 em CLIENT1, na primeira caixa de **informações** , clique em **aceitar**.</span><span class="sxs-lookup"><span data-stu-id="865ff-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="865ff-154">Clique em **documento em branco**.</span><span class="sxs-lookup"><span data-stu-id="865ff-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="865ff-155">Observe a seção **proteção** da faixa de opções na guia **página inicial** e a linha de classificações de documento.</span><span class="sxs-lookup"><span data-stu-id="865ff-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="865ff-156">No documento em branco, digite algum texto.</span><span class="sxs-lookup"><span data-stu-id="865ff-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="865ff-157">Clique em **arquivo _GT_ salvar**, digite o nome **BeforeAIP**e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="865ff-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="865ff-158">Na linha de classes de documento, clique na seta para baixo para **segredo**e, em seguida, clique em **toda a empresa**.</span><span class="sxs-lookup"><span data-stu-id="865ff-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="865ff-159">Clique em **arquivo _GT_ salvar como**, digite o nome **AfterAIP**e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="865ff-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="865ff-160">Clique em **Explorador de arquivos** na barra de tarefas e, em seguida, abra a pasta **documentos** .</span><span class="sxs-lookup"><span data-stu-id="865ff-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="865ff-161">Observe os diferentes tamanhos de arquivo dos documentos **BeforeAIP** e **AfterAIP** .</span><span class="sxs-lookup"><span data-stu-id="865ff-161">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents.</span></span> <span data-ttu-id="865ff-162">O documento AfterAIP é maior porque tem as informações de classificação.</span><span class="sxs-lookup"><span data-stu-id="865ff-162">The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="865ff-163">Em seguida, permita que todos acessem o conjunto de sites de suporte.</span><span class="sxs-lookup"><span data-stu-id="865ff-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="865ff-164">Na guia **Microsoft Office Home** , clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="865ff-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="865ff-165">Na guia **SharePoint** , clique em **conjunto de sites de suporte**.</span><span class="sxs-lookup"><span data-stu-id="865ff-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="865ff-166">No canto superior direito, clique no ícone **configurações** e, em seguida, clique em **compartilhado com**.</span><span class="sxs-lookup"><span data-stu-id="865ff-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="865ff-167">Em **compartilhar ' conjunto de sites de suporte '**, clique em **avançado**.</span><span class="sxs-lookup"><span data-stu-id="865ff-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="865ff-168">Na lista de grupos do SharePoint, clique em **suporte para membros do conjunto de sites**.</span><span class="sxs-lookup"><span data-stu-id="865ff-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="865ff-169">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="865ff-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="865ff-170">Em **compartilhar ' conjunto de sites de suporte '**, digite **todos**, clique em **todos exceto usuários externos**e, em seguida, clique em **compartilhar.**</span><span class="sxs-lookup"><span data-stu-id="865ff-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="865ff-171">Feche a guia **pessoas e grupos** .</span><span class="sxs-lookup"><span data-stu-id="865ff-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="865ff-172">Em seguida, entre com sua conta do User5 e carregue o documento protegido por AIP na pasta documentos do conjunto de sites de suporte.</span><span class="sxs-lookup"><span data-stu-id="865ff-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="865ff-173">Na guia **página inicial do Microsoft Office** , no canto superior direito, clique no ícone usuário e, em \*\*\*\* seguida, clique em sair.</span><span class="sxs-lookup"><span data-stu-id="865ff-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="865ff-174">Acesse [http://admin.microsoft.com](http://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="865ff-174">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="865ff-175">Na página de **entrada do Office 365** , clique no nome da conta do User5 e entre.</span><span class="sxs-lookup"><span data-stu-id="865ff-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="865ff-176">Na guia **Microsoft Office Home** , clique em **conjunto de sites de suporte do SharePoint >**.</span><span class="sxs-lookup"><span data-stu-id="865ff-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="865ff-177">Clique em **documentos**, clique em **carregar**, clique no documento **AfterAIP** e, em seguida, clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="865ff-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="865ff-178">Você verá AfterAIP. docx na pasta documentos no conjunto de sites de suporte.</span><span class="sxs-lookup"><span data-stu-id="865ff-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="865ff-179">Confira também</span><span class="sxs-lookup"><span data-stu-id="865ff-179">See Also</span></span>

[<span data-ttu-id="865ff-180">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="865ff-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="865ff-181">Office 365 e o ambiente de desenvolvimento/teste do EMS</span><span class="sxs-lookup"><span data-stu-id="865ff-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="865ff-182">Proteção de Informações do Azure</span><span class="sxs-lookup"><span data-stu-id="865ff-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


