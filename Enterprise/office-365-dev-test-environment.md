---
title: Ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Resumo: Use este guia de laboratório de teste para criar uma assinatura de avaliação do Office 365 para avaliação ou desenvolvimento/ teste.'
ms.openlocfilehash: 57fdf66f11d9c71faf81e2a88482093f8f17dfbd
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193541"
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="224cb-103">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="224cb-104">**Resumo:** Use este guia de laboratório de teste para criar uma assinatura de avaliação do Office 365 para avaliação ou desenvolvimento/ teste.</span><span class="sxs-lookup"><span data-stu-id="224cb-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="224cb-p101">Você pode usar uma assinatura de avaliação do Office 365 e criar um ambiente de desenvolvimento/teste do Office 365 para aplicativos ou para demonstrar recursos do Office 365. Há duas versões:</span><span class="sxs-lookup"><span data-stu-id="224cb-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="224cb-107">O leve ambiente de desenvolvimento/teste do Office 365 consiste em uma assinatura de avaliação do Office 365 que você acessa do seu computador principal.</span><span class="sxs-lookup"><span data-stu-id="224cb-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="224cb-p102">Use esse ambiente para demonstrar um recurso rapidamente. Para o ambiente de desenvolvimento/teste do Office 365 leve, conclua apenas as fases 2 e 3 deste artigo.</span><span class="sxs-lookup"><span data-stu-id="224cb-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="224cb-p103">O ambiente corporativo simulado de desenvolvimento/teste do Office 365 consiste em uma assinatura de avaliação do Office 365 e uma intranet da organização simplificada conectada à Internet, que está hospedada em serviços de infraestrutura do Microsoft Azure. Você pode criar esta configuração totalmente na nuvem da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="224cb-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="224cb-p104">Use esse ambiente para demonstrar um recurso ou um aplicativo em um ambiente que se assemelha a uma rede de organização típica conectada à Internet ou para recursos que exigem esse tipo de ambiente. Para o ambiente de desenvolvimento/teste corporativo simulado do Office 365, conclua as etapas de 1, 2 e 3 deste artigo.</span><span class="sxs-lookup"><span data-stu-id="224cb-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="224cb-p105">Talvez você queira imprimir este artigo para deixar guardado os valores específicos que serão necessários para esse ambiente durante os 30 dias da assinatura de avaliação do Office 365. Você pode estender a assinatura de avaliação para mais 30 dias, sem complicação. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com um pequeno número de licenças.</span><span class="sxs-lookup"><span data-stu-id="224cb-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Guias do Laboratório de Teste da Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="224cb-118">Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="224cb-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="224cb-119">Fase 1: Criar a configuração padrão no Azure</span><span class="sxs-lookup"><span data-stu-id="224cb-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="224cb-120">Siga as instruções em [Ambiente de desenvolvimento/teste de configuração de base](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="224cb-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="224cb-p106">Você precisará de uma assinatura do Azure. Você pode usar a [avaliação gratuita do Azure](https://azure.microsoft.com/pricing/free-trial/) para essa configuração. Se você tiver uma assinatura do MSDN ou Visual Studio, consulte o [Crédito mensal do Azure para assinantes do Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="224cb-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="224cb-124">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="224cb-124">Here is the resulting configuration.</span></span>
  
![O ambiente de desenvolvimento/teste de Configuração de Base no Azure](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
<span data-ttu-id="224cb-126">Essa configuração consiste nas máquinas virtuais DC1, APP1 e CLIENT1 na sub-rede de uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="224cb-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="224cb-127">Fase 2: Criar uma assinatura de avaliação do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="224cb-128">Para começar a usar a sua assinatura de avaliação do Office 365 E5, primeiro é necessário um nome de empresa fictícia e uma nova conta da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="224cb-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="224cb-p107">Recomendamos que você use uma variante do nome de empresa Contoso para o nome da sua empresa, que é uma empresa fictícia usada no conteúdo de exemplo da Microsoft, mas não é necessário. Registre o seu nome de empresa fictícia aqui: ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="224cb-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./images/Common_Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="224cb-p108">Para se inscrever em uma nova conta da Microsoft, acesse [https://outlook.com](https://outlook.com) e crie uma conta com um novo endereço e conta de email. Você usará essa conta para se inscrever no Office 365.</span><span class="sxs-lookup"><span data-stu-id="224cb-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="224cb-133">Armazene o nome e sobrenome da sua nova conta aqui: ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="224cb-133">Record the first and last name of your new account here: ![](./images/Common_Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="224cb-134">Armazene o novo endereço de conta de email aqui: ![](./images/Common_Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="224cb-134">Record the new email account address here: ![](./images/Common_Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="224cb-135">Inscrever-se em uma assinatura de avaliação do Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="224cb-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="224cb-136">Para o ambiente de desenvolvimento/teste leve do Office 365, abra o navegador da Internet em seu computador e acesse [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="224cb-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="224cb-137">Para o ambiente de desenvolvimento/teste corporativo simulado do Office 365, conecte-se a CLIENT1 com a conta CORP\Usuário1 do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="224cb-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="224cb-138">Na tela Inicial, execute o Microsoft Edge e acesse [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="224cb-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="224cb-139">Na página **Bem-vindo, fale mais sobre você**, especifique:</span><span class="sxs-lookup"><span data-stu-id="224cb-139">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="224cb-140">Sua localização física</span><span class="sxs-lookup"><span data-stu-id="224cb-140">Your physical location</span></span>
    
  - <span data-ttu-id="224cb-141">Nome e sobrenome da sua nova conta da Microsoft</span><span class="sxs-lookup"><span data-stu-id="224cb-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="224cb-142">Seu novo endereço de conta de email</span><span class="sxs-lookup"><span data-stu-id="224cb-142">Your new email account address</span></span>
    
  - <span data-ttu-id="224cb-143">Um número de telefone comercial</span><span class="sxs-lookup"><span data-stu-id="224cb-143">A business phone number</span></span>
    
  - <span data-ttu-id="224cb-144">Nome da sua empresa fictícia</span><span class="sxs-lookup"><span data-stu-id="224cb-144">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="224cb-145">Um tamanho de organização de 250-999</span><span class="sxs-lookup"><span data-stu-id="224cb-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="224cb-146">Clique em **Apenas mais uma etapa**.</span><span class="sxs-lookup"><span data-stu-id="224cb-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="224cb-147">Na página **Crie a sua ID de usuário**, digite um nome de usuário com base em seu novo endereço de email, sua empresa fictícia após o sinal de @ (remova todos os espaços no nome) e depois uma senha (duas vezes) para essa nova conta do Office 365.</span><span class="sxs-lookup"><span data-stu-id="224cb-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="224cb-148">Armazene a senha que você digitou em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="224cb-148">Record the password in a secure location.</span></span>
    
    <span data-ttu-id="224cb-149">Armazene o nome da sua empresa fictícia, a ser chamada de **nome da organização**, aqui: ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="224cb-149">Record your fictional company name, to be referred to as the **organization name**, here: ![](./images/Common_Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="224cb-150">Clique em **Criar minha conta**.</span><span class="sxs-lookup"><span data-stu-id="224cb-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="224cb-p109">Na página **Prove. que você. não é. um. robô.**, digite o número do seu telefone capaz de receber mensagem de texto e clique em **Enviar mensagem**.</span><span class="sxs-lookup"><span data-stu-id="224cb-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="224cb-153">Digite o código de verificação da mensagem de texto recebida e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="224cb-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="224cb-154">Armazene a URL da página de entrada aqui (selecione e copie): ![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="224cb-154">Record the sign-in page URL here (select and copy): ![](./images/Common_Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="224cb-155">Armazene a ID de usuário aqui (selecione e copie): ![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="224cb-155">Record the user ID here (select and copy): ![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="224cb-156">Esse valor será chamado de **Nome de administrador global do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="224cb-156">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="224cb-157">Quando você vir a mensagem, **Você está pronto para avançar**, clique nela.</span><span class="sxs-lookup"><span data-stu-id="224cb-157">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="224cb-158">Na próxima página, aguarde até o Office 365 concluir a configuração e os blocos estarem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="224cb-158">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="224cb-159">Você verá a página principal do portal do Office 365 em que pode acessar os serviços do Office Online e o Centro de administração do Office 365 .</span><span class="sxs-lookup"><span data-stu-id="224cb-159">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="224cb-160">Para o ambiente corporativo simulado de desenvolvimento/teste do Office 365, aqui está a sua configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="224cb-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![O ambiente de desenvolvimento/teste do Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="224cb-162">Esta configuração consiste em:</span><span class="sxs-lookup"><span data-stu-id="224cb-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="224cb-163">As máquinas virtuais DC1, APP1 e CLIENT1 em uma sub-rede de uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="224cb-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="224cb-164">Uma assinatura de avaliação do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="224cb-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="224cb-165">Fase 3: Configurar a sua assinatura de avaliação do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="224cb-166">Nesta fase, você configura a sua assinatura do Office 365 com outros usuários e sites de equipe do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="224cb-166">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="224cb-167">Primeiro, adicione quatro novos usuários e atribua licenças do E5 a eles.</span><span class="sxs-lookup"><span data-stu-id="224cb-167">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="224cb-168">Use as instruções em [Conectar-se ao PowerShell do Office 365](https://technet.microsoft.com/library/dn975125.aspx) para instalar os módulos do PowerShell e se conectar à sua nova assinatura do Office 365 a partir de:</span><span class="sxs-lookup"><span data-stu-id="224cb-168">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="224cb-169">Seu computador (para o ambiente leve de desenvolvimento/teste do Office 365).</span><span class="sxs-lookup"><span data-stu-id="224cb-169">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="224cb-170">A máquina virtual CLIENT1 (para o ambiente de desenvolvimento/teste corporativo simulado do Office 365).</span><span class="sxs-lookup"><span data-stu-id="224cb-170">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="224cb-171">Na caixa de diálogo Solicitação de credenciais do Windows PowerShell, digite o nome de administrador global do Office 365 (exemplo: jdoe@contosotoycompany.onmicrosoft.com) e a senha.</span><span class="sxs-lookup"><span data-stu-id="224cb-171">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="224cb-172">Preencha o nome de sua organização (exemplo: contosotoycompany), o código de país com dois caracteres de seu local e execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="224cb-172">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
> [!TIP]
> <span data-ttu-id="224cb-173">Clique [aqui](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) para obter um arquivo de texto que contém todos os comandos do PowerShell deste artigo.</span><span class="sxs-lookup"><span data-stu-id="224cb-173">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all of the PowerShell commands in this article.</span></span>

<span data-ttu-id="224cb-174">Na exibição do comando **New-MsolUser**, anote a senha gerada para a conta de Usuário 2 e grave-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="224cb-174">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="224cb-175">Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="224cb-175">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="224cb-176">Na exibição do comando **New-MsolUser**, anote a senha gerada para a conta de Usuário 3 e grave-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="224cb-176">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="224cb-177">Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="224cb-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="224cb-178">Na exibição do comando **New-MsolUser**, anote a senha gerada para a conta de Usuário 4 e grave-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="224cb-178">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="224cb-179">Execute os seguintes comandos no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="224cb-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="224cb-180">Na exibição do comando **New-MsolUser**, anote a senha gerada para a conta de Usuário 5 e grave-a em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="224cb-180">From the display of the **New-MsolUser** command, note the generated password for the Development VP account and record it in a safe location.</span></span>
  
<span data-ttu-id="224cb-181">Em seguida, crie três novos sites de equipe do SharePoint Online para os departamentos de produção, vendas e suporte.</span><span class="sxs-lookup"><span data-stu-id="224cb-181">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="224cb-182">Crie três novos sites de equipe do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="224cb-182">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="224cb-183">Instale o [Shell de Gerenciamento do SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251) (a versão x64).</span><span class="sxs-lookup"><span data-stu-id="224cb-183">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="224cb-184">Clique em **Iniciar**, digite **sharepoint** e, em seguida, clique em **Shell de gerenciamento do SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="224cb-184">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="224cb-185">Preencha o nome da sua organização (exemplo: contosotoycompany) e, em seguida, execute os seguintes comandos do prompt do Shell de gerenciamento do SharePoint Online para se conectar ao serviço do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="224cb-185">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="224cb-186">Na caixa de diálogo **Shell de Gerenciamento Online do Microsoft SharePoint**, digite o nome de administrador global do Office 365 (exemplo: jdoe@contosotoycompany.onmicrosoft.com) e a senha e clique em **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="224cb-186">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="224cb-187">Para criar três novos sites de equipe (vendas, produção e suporte), preencha o nome de administrador global do Office 365 e, em seguida, execute os seguintes comandos do prompt do Shell de Gerenciamento Online do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="224cb-187">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="224cb-188">Execute este comando para listar as URLs desses novos sites:</span><span class="sxs-lookup"><span data-stu-id="224cb-188">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="224cb-189">No Internet Explorer, insira a URL do site de produção para ver o site de equipe padrão do SharePoint Online para o departamento de produção.</span><span class="sxs-lookup"><span data-stu-id="224cb-189">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="224cb-190">Valores de registro para referência futura</span><span class="sxs-lookup"><span data-stu-id="224cb-190">Record values for future reference</span></span>

<span data-ttu-id="224cb-191">Armazene esses valores para trabalhar com ou implantar guias de laboratório de teste adicionais no ambiente de teste:</span><span class="sxs-lookup"><span data-stu-id="224cb-191">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="224cb-192">O nome de administrador global do Office 365: ![](./images/Common_Images/TableLine.png).onmicrosoft.com (da etapa 9 da fase 2)</span><span class="sxs-lookup"><span data-stu-id="224cb-192">Office 365 global administrator name: ![](./images/Common_Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="224cb-193">Também armazene a senha dessa conta em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="224cb-193">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="224cb-194">O nome da organização da sua assinatura de avaliação: ![](./images/Common_Images/TableLine.png) (da etapa 4 da fase 2)</span><span class="sxs-lookup"><span data-stu-id="224cb-194">Your trial subscription organization name: ![](./images/Common_Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="224cb-195">Para listar as contas do usuário 2, Usuário 3, Usuário 4 e Usuário 5, execute o seguinte comando no prompt do Módulo do Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="224cb-195">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="224cb-196">Armazene os nomes de contas aqui:</span><span class="sxs-lookup"><span data-stu-id="224cb-196">Record the account names here:</span></span>
    
  - <span data-ttu-id="224cb-197">Nome da conta do Usuário 2: usuário2@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="224cb-197">User 2 account name: user2@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="224cb-198">Nome da conta do Usuário 3: usuário3@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="224cb-198">User 3 account name: user3@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="224cb-199">Nome da conta do Usuário 4: usuário4@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="224cb-199">User 4 account name: user4@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="224cb-200">Nome da conta do Usuário 5: usuário5@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="224cb-200">User 5 account name: user5@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="224cb-201">Também armazene as senhas dessas contas em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="224cb-201">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="224cb-202">Para listar as URLs para os sites de equipe de Vendas, Produção e Suporte, execute o seguinte comando no prompt do Shell de Gerenciamento Online do SharePoint:</span><span class="sxs-lookup"><span data-stu-id="224cb-202">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="224cb-203">URL do site produção: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="224cb-203">Production site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="224cb-204">URL do site de vendas: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="224cb-204">Sales site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="224cb-205">URL do site de suporte: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="224cb-205">Support site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="224cb-206">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="224cb-206">Next steps</span></span>

<span data-ttu-id="224cb-207">Use estes outros artigos em seu ambiente de desenvolvimento/teste do Office 365:</span><span class="sxs-lookup"><span data-stu-id="224cb-207">Use these additional articles in your Office 365 and EMS dev/test environment:</span></span>
  
- [<span data-ttu-id="224cb-208">Sincronização de diretório do ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-208">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-209">Autenticação multifator para o ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-209">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-210">Identidade federada para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-210">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-211">Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-211">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-212">Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-212">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-213">Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-213">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-214">Proteção de arquivos confidenciais no ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-214">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-215">Site de equipe do SharePoint Online isolado no seu ambiente de desenvolvimento/teste</span><span class="sxs-lookup"><span data-stu-id="224cb-215">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-216">Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="224cb-216">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="224cb-217">Estenda o seu ambiente de desenvolvimento/teste do Office 365 para incluir outras ofertas da nuvem da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="224cb-217">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="224cb-218">Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="224cb-218">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="224cb-219">Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="224cb-219">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="224cb-220">Confira também</span><span class="sxs-lookup"><span data-stu-id="224cb-220">See Also</span></span>

- [<span data-ttu-id="224cb-221">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="224cb-221">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="224cb-222">Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="224cb-222">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="224cb-223">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="224cb-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


