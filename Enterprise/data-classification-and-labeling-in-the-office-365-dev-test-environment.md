---
title: Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
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
description: 'Resumo: Configurar e demonstrar a classificação de dados e rótulos usando o cliente de proteção de informações do Windows Azure (AIP) em seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: 69526f8bf0ae0b6cc7509653cfaa72581e10dbfe
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897434"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="0b5b0-103">Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5b0-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="0b5b0-104">**Resumo:** Configurar e demonstrar a classificação de dados e rótulos usando o cliente de proteção de informações do Windows Azure (AIP) em seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="0b5b0-p101">O cliente de proteção de informações do Windows Azure lhe permite classificar um documento antes de carregá-la para uma pasta do SharePoint Online no Office 365. Com as instruções deste artigo, você pode instala o cliente de proteção de informações do Windows Azure e demonstrar a classificação de dados. Para obter mais informações, consulte [Proteção de informações do Windows Azure](https://www.microsoft.com/cloud-platform/azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="0b5b0-p101">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="0b5b0-108">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="0b5b0-109">Fase 1: Criar o seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0b5b0-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="0b5b0-110">Siga as instruções no [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0b5b0-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="0b5b0-111">Fase 2: Adicionar uma assinatura de avaliação de proteção de informações do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="0b5b0-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="0b5b0-p102">Nesta fase, você adiciona a proteção de informações do Windows Azure para seu ambiente de desenvolvimento e teste do Office 365 e habilitá-lo para suas contas de usuário. Se você tiver configurado o [Office 365 e o ambiente de desenvolvimento e teste do EMS](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), ignore esta fase. A assinatura de avaliação Enterprise mobilidade Suite inclui licenças da proteção de informações do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="0b5b0-115">Em primeiro lugar, inscreva-se para uma assinatura de avaliação de proteção de informações do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="0b5b0-116">Inscreva-se para uma assinatura de avaliação de proteção de informações do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="0b5b0-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="0b5b0-117">No Internet Explorer ou seu navegador, vá para [http://portal.office.com](http://portal.office.com) e entre com sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="0b5b0-118">Na guia **Página inicial do Microsoft Office** , clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="0b5b0-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="0b5b0-119">Na guia de administração do Office 365, no painel de navegação esquerdo, clique em **Serviços de compra gt _ de cobrança**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="0b5b0-p103">Na página **Serviços de compra** , localize o item de **P2 de Premium de proteção de informações do Azure** . Passe o mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="0b5b0-122">Na página **Confirmar seu pedido**, clique em **Experimentar agora**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="0b5b0-123">Na página **Recibo do pedido**, clique em **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="0b5b0-124">Em seguida, você pode habilitar a licença de proteção de informações do Windows Azure para todas as contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="0b5b0-125">Na guia Office 365 admin center, clique em **usuários**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="0b5b0-126">Na lista de contas de usuário, selecione sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="0b5b0-127">Ativar a licença do produto para o **Windows Azure informações proteção Premium P2** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .</span><span class="sxs-lookup"><span data-stu-id="0b5b0-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="0b5b0-128">Repita as etapas 2 e 3 para suas outras contas de usuário (usuário 1 a 5 do usuário).</span><span class="sxs-lookup"><span data-stu-id="0b5b0-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="0b5b0-129">Agora tem seu ambiente de desenvolvimento e teste do Office 365:</span><span class="sxs-lookup"><span data-stu-id="0b5b0-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="0b5b0-130">Assinaturas de avaliação do Office 365 E5 Enterprise e proteção de informações do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="0b5b0-131">Todas as suas contas de usuário habilitado para usar o Office 365 E5 Enterprise e proteção de informações do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="0b5b0-132">Fase 3: Demonstrar a classificação de dados</span><span class="sxs-lookup"><span data-stu-id="0b5b0-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="0b5b0-133">Nesta fase, você demonstrar a classificação de dados usando o cliente de proteção de informações do Windows Azure e a diretiva de proteção de informações do Azure padrão.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="0b5b0-134">Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, você deve instalar primeiro 2016 do Office no CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="0b5b0-135">Use o seu navegador e vá para o [portal do Azure](http://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="0b5b0-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="0b5b0-136">Clique em **gt _ de grupos de recursos** [seu nome de grupo de recursos] **gt _ CLIENT1 gt _ Connect**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="0b5b0-137">No CLIENT1, execute o Internet Explorer, vá para o portal do Office em [http://portal.office.com](http://portal.office.com)e, em seguida, entre com o nome da conta de User5 e a senha.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="0b5b0-138">Na guia **Microsoft Office Home**, clique em **Instalar o Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="0b5b0-p104">Execute o download quando solicitado e clique em **Sim** quando solicitado pelo controle de conta de usuário. Aguarde do Office instalar. Quando concluir, clique em **Fechar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="0b5b0-142">Em seguida, você pode instalar o cliente de proteção de informações do Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="0b5b0-143">No seu navegador ou o Internet Explorer, vá para a [página de download de proteção de informações do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=53018).</span><span class="sxs-lookup"><span data-stu-id="0b5b0-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="0b5b0-144">Se você estiver usando a versão leve do ambiente de desenvolvimento e teste do Office 365, use o navegador no computador local.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="0b5b0-145">Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, execute o Internet Explorer do CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="0b5b0-146">Na página de download de **Proteção de informações do Microsoft Azure** , clique em **Download**, clique em **AzInfoProtection.exe**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="0b5b0-147">Quando solicitado, execute AzInfoProtection.exe.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="0b5b0-148">Na caixa de cliente **instalar a proteção de informações do Windows Azure** , clique em **Concordo**e clique em **Sim** quando solicitado pelo controle de conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="0b5b0-149">Na caixa **concluída com êxito** , clique em **Close.**</span><span class="sxs-lookup"><span data-stu-id="0b5b0-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="0b5b0-150">Em seguida, você demonstrar a classificação de documento.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="0b5b0-151">Clique no ícone do **Word** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="0b5b0-152">Quando solicitado, inscreva-se com o nome da conta de User5 e a senha.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="0b5b0-153">Se você acabou de instalar Office 2016 no CLIENT1, no **primeiras coisas primeiro** , clique em **Aceitar**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="0b5b0-154">Clique em **documento em branco**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="0b5b0-155">Observe que a seção de **proteção** da faixa de opções, na guia **página inicial** e a linha de classificações de documento.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="0b5b0-156">No documento em branco, digite algum texto.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="0b5b0-157">Clique em **Salvar gt _ do arquivo**, digite o nome **BeforeAIP**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="0b5b0-158">Na linha de classes de documento, clique na seta para **segredo**e, em seguida, clique em **Tudo empresa**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="0b5b0-159">Clique em **arquivo gt _ Salvar como**, digite o nome **AfterAIP**e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="0b5b0-160">Clique em **Gerenciador de arquivos** , na barra de tarefas e, em seguida, abra a pasta de **documentos** .</span><span class="sxs-lookup"><span data-stu-id="0b5b0-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="0b5b0-p105">Observe os tamanhos de arquivo diferente dos documentos **BeforeAIP** e **AfterAIP** . O documento AfterAIP é maior porque ele tem as informações de classificação.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="0b5b0-163">Em seguida, você permitir que todos acessar a coleção de site de suporte.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="0b5b0-164">Na guia **Página inicial do Microsoft Office** , clique em **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="0b5b0-165">Na guia **SharePoint** , clique em **conjunto de sites de suporte**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="0b5b0-166">No canto superior direito, clique no ícone **configurações** e, em seguida, clique em **compartilhado com**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="0b5b0-167">Em **compartilhamento 'Conjunto de sites de suporte'**, clique em **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="0b5b0-168">Na lista de grupos do SharePoint, clique em **conjunto de sites de suporte membros**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="0b5b0-169">Na página **Pessoas e Grupos**, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="0b5b0-170">Em **compartilhamento 'Conjunto de sites de suporte'**, digite **todos**, clique em **todos exceto os usuários externos**e, em seguida, clique em **Share.**</span><span class="sxs-lookup"><span data-stu-id="0b5b0-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="0b5b0-171">Feche a guia **pessoas e grupos** .</span><span class="sxs-lookup"><span data-stu-id="0b5b0-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="0b5b0-172">Em seguida, você pode entrar com sua conta User5 e carregar um documento protegido por AIP para a pasta de documentos do conjunto de sites de suporte.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="0b5b0-173">Na guia **Página inicial do Microsoft Office** , no canto superior direito, clique no ícone de usuário e, em seguida, clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="0b5b0-174">Acesse [http://portal.office.com](http://portal.office.com).</span><span class="sxs-lookup"><span data-stu-id="0b5b0-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="0b5b0-175">Na página do **Office 365 entrar** , clique no nome da conta de User5 e entrar.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="0b5b0-176">Na guia **Página inicial do Microsoft Office** , clique em **SharePoint gt _ conjunto de sites de suporte**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="0b5b0-177">Clique em **documentos**, clique em **carregar**, clique no documento **AfterAIP** e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="0b5b0-178">Você deverá ver AfterAIP.docx na pasta documentos no conjunto de sites de suporte.</span><span class="sxs-lookup"><span data-stu-id="0b5b0-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="0b5b0-179">Confira também</span><span class="sxs-lookup"><span data-stu-id="0b5b0-179">See Also</span></span>

[<span data-ttu-id="0b5b0-180">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="0b5b0-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="0b5b0-181">Office 365 e o ambiente de desenvolvimento/teste do EMS</span><span class="sxs-lookup"><span data-stu-id="0b5b0-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="0b5b0-182">Proteção de Informações do Azure</span><span class="sxs-lookup"><span data-stu-id="0b5b0-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


