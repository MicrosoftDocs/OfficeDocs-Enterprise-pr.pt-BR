---
title: Autenticação multifator para o ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
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
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 'Resumo: Configure a autenticação multifator usando mensagens de texto enviadas a um telefone inteligente em um ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: 13dc02cc23d12f6eb6e2898d34271685badd9f5a
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573975"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="d14cb-103">Autenticação multifator para o ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="d14cb-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="d14cb-104">**Resumo:** Configurar a autenticação multifator usando mensagens de texto enviadas a um telefone inteligente em um ambiente de desenvolvimento/teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d14cb-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="d14cb-105">Para obter um nível adicional de segurança para entrar em sua assinatura do Office 365, você pode habilitar a autenticação multifator do Azure, que requer mais do que apenas um nome de usuário e senha para autenticar uma conta.</span><span class="sxs-lookup"><span data-stu-id="d14cb-105">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account.</span></span> <span data-ttu-id="d14cb-106">Com a autenticação multifator para o Office 365, os usuários precisam confirmar uma chamada telefônica, digitar um código de verificação enviado em uma mensagem de texto ou especificar uma senha de aplicativo em telefones inteligentes depois de inserir corretamente suas senhas.</span><span class="sxs-lookup"><span data-stu-id="d14cb-106">With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords.</span></span> <span data-ttu-id="d14cb-107">O acesso só será possível depois que esse segundo fator de autenticação for atendido.</span><span class="sxs-lookup"><span data-stu-id="d14cb-107">They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="d14cb-108">Este artigo descreve como habilitar e testar a autenticação baseada em mensagem de texto para uma conta específica do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d14cb-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="d14cb-109">Há duas fases para configurar a autenticação multifator para o Office 365 em um ambiente de desenvolvimento/teste:</span><span class="sxs-lookup"><span data-stu-id="d14cb-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="d14cb-110">Criação do ambiente de desenvolvimento/teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d14cb-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="d14cb-111">Habilite e teste a autenticação multifator para a conta do usuário 2.</span><span class="sxs-lookup"><span data-stu-id="d14cb-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="d14cb-112">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="d14cb-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="d14cb-113">Fase 1: desenvolver seu ambiente de desenvolvimento/teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="d14cb-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="d14cb-114">Se você só quiser testar a autenticação multifator de forma leve com os requisitos mínimos, siga as instruções nas fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d14cb-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="d14cb-115">Se você quiser testar a autenticação multifator em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d14cb-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d14cb-116">Testar a autenticação multifator não requer o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="d14cb-116">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest.</span></span> <span data-ttu-id="d14cb-117">É fornecida aqui como uma opção para que você possa testar a autenticação multifator e experimentá-la em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="d14cb-117">It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="d14cb-118">Fase 2: habilitar e testar a autenticação multifator para a conta do usuário 2</span><span class="sxs-lookup"><span data-stu-id="d14cb-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="d14cb-119">Habilite a autenticação multifator para a conta do usuário 2 com estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d14cb-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="d14cb-120">Abra uma instância separada do navegador, vá para o portal do Office 365 ([https://www.office.com](https://www.office.com)) e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="d14cb-120">Open a separate instance of your browser, go to the Office 365 portal ([https://www.office.com](https://www.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="d14cb-121">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="d14cb-122">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="d14cb-123">No painel usuários ativos, clique em **mais > configuração de autenticação**multifator.</span><span class="sxs-lookup"><span data-stu-id="d14cb-123">In the Active users pane, click **More > Multi-factor authentication setup**.</span></span>
    
5. <span data-ttu-id="d14cb-124">Na lista, selecione a conta do **usuário 2** .</span><span class="sxs-lookup"><span data-stu-id="d14cb-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="d14cb-125">Na seção **usuário 2** , em **etapas rápidas**, clique em **habilitar**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="d14cb-126">Na caixa de diálogo **sobre como habilitar a autenticação** multifator, clique em **habilitar autenticação**multifator.</span><span class="sxs-lookup"><span data-stu-id="d14cb-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="d14cb-127">Na caixa de diálogo **atualizações com êxito** , clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-127">In the **Updates successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="d14cb-128">Na guia **Microsoft Office Home** , clique no ícone da conta de usuário no canto superior direito e clique em \*\*\*\* sair.</span><span class="sxs-lookup"><span data-stu-id="d14cb-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="d14cb-129">Feche a instância do navegador.</span><span class="sxs-lookup"><span data-stu-id="d14cb-129">Close your browser instance.</span></span>
    
<span data-ttu-id="d14cb-130">Conclua a configuração da conta do usuário 2 para usar uma mensagem de texto para validação e testá-la com estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d14cb-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="d14cb-131">Abra uma nova instância do navegador.</span><span class="sxs-lookup"><span data-stu-id="d14cb-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="d14cb-132">Vá para o portal do Office 365[https://www.office.com](https://www.office.com)() e entre com a conta do usuário 2 (Usuário2\<@ Organization name>. onmicrosoft. com) e a senha.</span><span class="sxs-lookup"><span data-stu-id="d14cb-132">Go to the Office 365 portal ([https://www.office.com](https://www.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="d14cb-133">Após entrar, você será solicitado a configurar a conta para a validação de segurança adicional.</span><span class="sxs-lookup"><span data-stu-id="d14cb-133">After signing in, you are prompted to set up the account for additional security validation.</span></span> <span data-ttu-id="d14cb-134">Clique em **Configurar agora**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-134">Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="d14cb-135">Na página **verificação de segurança adicional** :</span><span class="sxs-lookup"><span data-stu-id="d14cb-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="d14cb-136">Selecione seu país ou região.</span><span class="sxs-lookup"><span data-stu-id="d14cb-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="d14cb-137">Digite o número de telefone do telefone inteligente que receberá mensagens de texto.</span><span class="sxs-lookup"><span data-stu-id="d14cb-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="d14cb-138">em **método**, clique em **enviar um código por mensagem de texto**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="d14cb-139">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="d14cb-140">Insira o código de verificação da mensagem de texto recebida no telefone inteligente e clique em **verificar**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="d14cb-141">Na página **etapa 3: manter seus aplicativos existentes** , registre a senha do aplicativo exibida para a conta do usuário 2 em um local seguro e clique em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="d14cb-142">Se esta é a primeira vez que você entrou com a conta de usuário 2, você é solicitado a alterar a senha.</span><span class="sxs-lookup"><span data-stu-id="d14cb-142">If this is the first time you signed in with the User 2 account, you are prompted to change the password.</span></span> <span data-ttu-id="d14cb-143">Digite a senha original e uma nova senha duas vezes e clique em **Atualizar senha e entrar**.</span><span class="sxs-lookup"><span data-stu-id="d14cb-143">Type the original password and a new password twice, and then click **Update password and sign in**.</span></span> <span data-ttu-id="d14cb-144">Registre a nova senha em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="d14cb-144">Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="d14cb-145">Você deve ver o portal do Office 365 para o usuário 2 na guia **Microsoft Office Home** do navegador.</span><span class="sxs-lookup"><span data-stu-id="d14cb-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d14cb-146">Confira também
</span><span class="sxs-lookup"><span data-stu-id="d14cb-146">See Also</span></span>

[<span data-ttu-id="d14cb-147">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="d14cb-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
<span data-ttu-id="d14cb-148">[Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="d14cb-148">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="d14cb-149">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="d14cb-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="d14cb-150">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="d14cb-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="d14cb-151">Planejar a autenticação multifator para imPlantações do Office 365</span><span class="sxs-lookup"><span data-stu-id="d14cb-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

