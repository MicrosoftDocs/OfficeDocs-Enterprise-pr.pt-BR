---
title: "A autenticação multifator para seu ambiente de desenvolvimento e teste do Office 365"
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "Resumo: Configure a autenticação multifator usando mensagens de texto enviadas a um telefone inteligente em um ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: 66b0fadd097e6df940754c28cd7b95549eb3a761
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="71acc-103">A autenticação multifator para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="71acc-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="71acc-104">**Resumo:** Configure a autenticação multifator usando mensagens de texto enviadas a um telefone inteligente em um ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="71acc-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="71acc-p101">Para um nível adicional de segurança para entrar em sua assinatura do Office 365, você pode habilitar a autenticação multifator Azure, que requer mais do que apenas um nome de usuário e uma senha para verificar uma conta. Com a autenticação multifator para o Office 365, os usuários são necessários para reconhecer uma chamada telefônica, digite um código de verificação enviado em uma mensagem de texto ou especificar uma senha de app em seus telefones inteligentes após inserir corretamente suas senhas. Eles podem entrar somente depois que esse segundo fator de autenticação foram atendido.</span><span class="sxs-lookup"><span data-stu-id="71acc-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to verify an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="71acc-108">Este artigo descreve como habilitar e testar a autenticação baseada em mensagens de texto de uma conta específica do Office 365.</span><span class="sxs-lookup"><span data-stu-id="71acc-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="71acc-109">Há duas fases para configurar a autenticação multifator para o Office 365 em um ambiente de desenvolvimento e teste:</span><span class="sxs-lookup"><span data-stu-id="71acc-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="71acc-110">Crie o ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="71acc-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="71acc-111">Habilitar e testar a autenticação multifator para a conta de usuário 2.</span><span class="sxs-lookup"><span data-stu-id="71acc-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="71acc-112">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="71acc-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="71acc-113">Fase 1: Desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="71acc-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="71acc-114">Se você deseja testar a autenticação multifator de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="71acc-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="71acc-115">Se você deseja testar a autenticação multifator em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="71acc-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="71acc-p102">Testar a autenticação multifator não requer que o ambiente de desenvolvimento e teste de simulado empresarial, que inclui uma intranet simulada conectada à Internet e a sincronização de diretório para uma floresta do Windows Server AD. Ele é fornecido aqui como uma opção para que você possa testar a autenticação multifator e experimentar em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="71acc-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="71acc-118">Fase 2: Habilitar e testar a autenticação multifator para a conta de usuário 2</span><span class="sxs-lookup"><span data-stu-id="71acc-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="71acc-119">Habilite a autenticação multifator para a conta de usuário 2 com estas etapas:</span><span class="sxs-lookup"><span data-stu-id="71acc-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="71acc-120">Abra uma instância separada do navegador, vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e então entrar com sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="71acc-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="71acc-121">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="71acc-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="71acc-122">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="71acc-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="71acc-123">No painel de usuários ativos, clique em **mais > instalação Azure multi-factor auth**.</span><span class="sxs-lookup"><span data-stu-id="71acc-123">In the Active users pane, click **More > Setup Azure multi-factor auth**.</span></span>
    
5. <span data-ttu-id="71acc-124">Na lista, clique na conta de **usuário 2** .</span><span class="sxs-lookup"><span data-stu-id="71acc-124">In the list, click the **User 2** account.</span></span>
    
6. <span data-ttu-id="71acc-125">Na seção **2 do usuário** , em **etapas rápidas**, clique em **Habilitar**.</span><span class="sxs-lookup"><span data-stu-id="71acc-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="71acc-126">Na caixa de diálogo **sobre como habilitar a autenticação multifator** , clique em **Habilitar a autenticação multifator**.</span><span class="sxs-lookup"><span data-stu-id="71acc-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="71acc-127">Na caixa de diálogo **atualizar com êxito** , clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="71acc-127">In the **Update successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="71acc-128">Na guia **Página inicial do Microsoft Office** , clique no ícone de conta de usuário no canto superior direito e clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="71acc-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="71acc-129">Feche sua instância do navegador.</span><span class="sxs-lookup"><span data-stu-id="71acc-129">Close your browser instance.</span></span>
    
<span data-ttu-id="71acc-130">Conclua a configuração da conta do usuário 2 a usar uma mensagem de texto para validação e testá-lo com estas etapas:</span><span class="sxs-lookup"><span data-stu-id="71acc-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="71acc-131">Abra uma nova instância do navegador.</span><span class="sxs-lookup"><span data-stu-id="71acc-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="71acc-132">Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e o logon com a conta de usuário 2 (Usuário2 @\<nome da organização >. onmicrosoft.com) e a senha.</span><span class="sxs-lookup"><span data-stu-id="71acc-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="71acc-p103">Depois de entrar, você precisará configurar a conta para a validação de segurança adicionais. Clique em **montá-lo agora**.</span><span class="sxs-lookup"><span data-stu-id="71acc-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="71acc-135">Na página **verificação de segurança adicionais** :</span><span class="sxs-lookup"><span data-stu-id="71acc-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="71acc-136">Selecione seu país ou região.</span><span class="sxs-lookup"><span data-stu-id="71acc-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="71acc-137">Digite o número de telefone do telefone inteligente que receberá mensagens de texto.</span><span class="sxs-lookup"><span data-stu-id="71acc-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="71acc-138">Selecione **Enviar-me um código de mensagem de texto**.</span><span class="sxs-lookup"><span data-stu-id="71acc-138">Select **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="71acc-139">Clique em **contato me**.</span><span class="sxs-lookup"><span data-stu-id="71acc-139">Click **Contact me**.</span></span>
    
6. <span data-ttu-id="71acc-140">Insira o código de verificação da mensagem de texto recebida no seu telefone inteligente e clique em **Verificar**.</span><span class="sxs-lookup"><span data-stu-id="71acc-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="71acc-141">Sobre o **etapa 3: mantenha seus aplicativos existentes** página, registre a senha do aplicativo exibido para a conta de usuário 2 em um local seguro e clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="71acc-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="71acc-142">Volta na página de entrada, digite a senha para a conta de usuário 2 e clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="71acc-142">Back on the sign-in page, type the password for the User 2 account and click **Sign in**.</span></span>
    
9. <span data-ttu-id="71acc-143">Insira o código de verificação da mensagem de texto recebida no seu telefone inteligente e, em seguida, clique em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="71acc-143">Enter the verification code from the text message received on your smart phone, and then click **Sign in**.</span></span>
    
10. <span data-ttu-id="71acc-p104">Se essa for a primeira vez você entrou com a conta de usuário 2, você será solicitado alterar a senha. Digite a senha original e uma nova senha duas vezes e, em seguida, clique em **Atualizar senha e entrar**. Registre a nova senha em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="71acc-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="71acc-147">Você deverá ver o portal do Office 365 para o usuário 2.</span><span class="sxs-lookup"><span data-stu-id="71acc-147">You should see the Office 365 portal for User 2.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="71acc-148">Veja também</span><span class="sxs-lookup"><span data-stu-id="71acc-148">See Also</span></span>

[<span data-ttu-id="71acc-149">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="71acc-149">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="71acc-150">Ambiente de desenvolvimento e teste de configuração de base</span><span class="sxs-lookup"><span data-stu-id="71acc-150">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="71acc-151">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="71acc-151">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="71acc-152">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="71acc-152">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="71acc-153">Planejar a autenticação multifator para implantações do Office 365</span><span class="sxs-lookup"><span data-stu-id="71acc-153">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

