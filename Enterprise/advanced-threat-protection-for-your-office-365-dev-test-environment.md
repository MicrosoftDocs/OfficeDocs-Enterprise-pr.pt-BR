---
title: Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: 'Resumo: Configure e demonstre a Proteção Avançada contra Ameaças do Office 365 no seu ambiente de desenvolvimento e teste do Office 365.'
ms.openlocfilehash: 53bff386490ed9647a511f75c997cb91b0acc181
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741337"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="e9209-103">Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e9209-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="e9209-104">**Resumo:** Configure e demonstre a Proteção Avançada contra Ameaças do Office 365 no seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e9209-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e9209-105">A Proteção Avançada contra Ameaças (ATP) do Office 365 é um recurso da Proteção do Exchange Online (EOP) que ajuda a evitar malware em emails.</span><span class="sxs-lookup"><span data-stu-id="e9209-105">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email.</span></span> <span data-ttu-id="e9209-106">Com ATP, você cria políticas no centro de administração do Exchange (Eat) ou no &amp; centro de conformidade de segurança que ajuda a garantir que seus usuários acessem apenas links ou anexos em emails identificados como não mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="e9209-106">With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious.</span></span> <span data-ttu-id="e9209-107">Para obter mais informações, consulte [proteção avançada contra ameaças para anexos seguros e links seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="e9209-107">For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="e9209-108">Com as instruções neste artigo, você configurará e testará a ATP na sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e9209-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="e9209-109">Fase 1: Desenvolver seu ambiente de desenvolvimento e teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="e9209-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="e9209-110">Se você só quiser testar a ATP de uma maneira leve com os requisitos mínimos, siga as instruções nas fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="e9209-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e9209-111">Se você quiser testar a ATP em uma empresa simulada, siga as instruções em [DirSync para seu ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="e9209-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e9209-112">O teste de ATP não exige o ambiente de desenvolvimento/teste corporativo simulado, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta dos serviços de domínio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="e9209-112">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="e9209-113">Ele é fornecido aqui como uma opção para que você possa testar a ATP e fazer testes com ele em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="e9209-113">It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="e9209-114">Fase 2: demonstrar o comportamento padrão de entrega de email do Office 365</span><span class="sxs-lookup"><span data-stu-id="e9209-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="e9209-115">Nesta fase, você demonstrará que, antes de configurar políticas de ATP, emails mal-intencionados são entregues às caixas de correio do Office 365 sem triagem ou mitigação.</span><span class="sxs-lookup"><span data-stu-id="e9209-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="e9209-116">Abra o Internet Explorer e entre na conta do Outlook que você criou na fase 2 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="e9209-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="e9209-117">Se estiver usando o ambiente de desenvolvimento e teste leve do Office 365, abra uma sessão particular do Internet Explorer e entre com o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="e9209-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="e9209-118">Se você estiver usando o ambiente de desenvolvimento/teste do Office Enterprise 365 simulado, use o [portal do Azure](https://portal.azure.com) para se conectar à máquina virtual do CLIENT1 e, em seguida, entre no CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e9209-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="e9209-119">Execute o Bloco de Notas e insira algum texto.</span><span class="sxs-lookup"><span data-stu-id="e9209-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="e9209-120">Salve o arquivo na pasta Documentos como **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="e9209-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="e9209-121">Na guia Email do Outlook do Internet Explorer, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="e9209-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="e9209-122">Em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste.</span><span class="sxs-lookup"><span data-stu-id="e9209-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="e9209-123">Para o assunto, digite **Suas novas chaves**.</span><span class="sxs-lookup"><span data-stu-id="e9209-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="e9209-124">No corpo, digite **Aqui está o arquivo**.</span><span class="sxs-lookup"><span data-stu-id="e9209-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="e9209-125">Clique em **Anexar**, clique duas vezes em **getKeys.js** na pasta Documentos, clique em **Anexar como cópia** e depois clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="e9209-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="e9209-126">Clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="e9209-126">Click **New**.</span></span>
    
10. <span data-ttu-id="e9209-127">Em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste.</span><span class="sxs-lookup"><span data-stu-id="e9209-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="e9209-128">Para o assunto, digite **Novo site de viagem**.</span><span class="sxs-lookup"><span data-stu-id="e9209-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="e9209-129">No corpo, digite **Alguém me encaminhou este site**.</span><span class="sxs-lookup"><span data-stu-id="e9209-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="e9209-130">No corpo, selecione o texto **este site** e clique no ícone de hiperlink na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="e9209-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="e9209-131">Em **URL**, digite **http://www.spamlink.contoso.com/**, clique em **OK**e, em seguida, clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="e9209-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="e9209-132">Abra uma instância separada do Internet Explorer no modo de navegação privada, vá para o centro de administração do[https://admin.microsoft.com](https://admin.microsoft.com)Microsoft 365 () e entre na sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="e9209-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="e9209-133">Na página principal do portal, clique no bloco Aplicativos e depois em **Email**.</span><span class="sxs-lookup"><span data-stu-id="e9209-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="e9209-134">Em Caixa de Entrada, clique na mensagem com o assunto **Suas novas chaves**.</span><span class="sxs-lookup"><span data-stu-id="e9209-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="e9209-135">Na pasta lixo eletrônico, clique na mensagem com o assunto **novo site da Web da viagem**.</span><span class="sxs-lookup"><span data-stu-id="e9209-135">In the Junk Mail folder, click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="e9209-136">Na mensagem, clique no link **este site** .</span><span class="sxs-lookup"><span data-stu-id="e9209-136">Within the message, click the **this site** link.</span></span> <span data-ttu-id="e9209-137">Você verá um "Opa!</span><span class="sxs-lookup"><span data-stu-id="e9209-137">You should see a "Oops!</span></span> <span data-ttu-id="e9209-138">O Internet Explorer não pôde encontrar spamlink.contoso.com. "</span><span class="sxs-lookup"><span data-stu-id="e9209-138">Internet Explorer could not find spamlink.contoso.com."</span></span> <span data-ttu-id="e9209-139">da.</span><span class="sxs-lookup"><span data-stu-id="e9209-139">page.</span></span> <span data-ttu-id="e9209-140">Este é o resultado correto porque não há nenhuma página da Web nesse local.</span><span class="sxs-lookup"><span data-stu-id="e9209-140">This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="e9209-p104">Observe que ambos os emails potencialmente mal-intencionados foram entregues com êxito. O email **Suas novas chaves** poderia conter malware não detectado, e o usuário poderia clicar no link possivelmente mal-intencionado no email **Novo site de viagem**.</span><span class="sxs-lookup"><span data-stu-id="e9209-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="e9209-143">Fase 3: Configurar políticas de anexo seguro e links seguros para a ATP</span><span class="sxs-lookup"><span data-stu-id="e9209-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="e9209-144">Nesta fase, você criará e configurará uma política de anexo seguro para impedir a entrega de emails com anexos possivelmente mal-intencionados e uma política de links seguros para impedir que os usuários acessem URLs possivelmente não seguras.</span><span class="sxs-lookup"><span data-stu-id="e9209-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="e9209-145">Na guia **Microsoft Office Home** do Internet Explorer, clique no bloco **administrador** .</span><span class="sxs-lookup"><span data-stu-id="e9209-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="e9209-146">Na navegação à esquerda, clique em **Centros de administração** e depois em **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="e9209-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="e9209-147">Na navegação à esquerda da guia Centro de administração do Exchange, clique em **ameaças avançadas**.</span><span class="sxs-lookup"><span data-stu-id="e9209-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="e9209-148">Clique na guia **anexos seguros** e depois clique no sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="e9209-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="e9209-149">Na **nova janela política de anexos confiáveis** , em **nome**, digite **política de anexo seguro-Bloquear**.</span><span class="sxs-lookup"><span data-stu-id="e9209-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="e9209-150">Para uma **resposta desconhecida de malware de anexos seguros**, clique em **Bloquear**.</span><span class="sxs-lookup"><span data-stu-id="e9209-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="e9209-151">Para **Redirecionar o anexo na detecção**, clique em **Habilitar redirecionamento** e digite o endereço de email da sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e9209-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="e9209-152">Para **Aplicado a**, clique na seta para baixo e depois em **O domínio do destinatário é**.</span><span class="sxs-lookup"><span data-stu-id="e9209-152">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="e9209-153">Na janela, clique no nome da sua organização (como contoso.onmicrosoft.com) e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9209-153">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="e9209-154">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e9209-154">Click **Save**.</span></span> <span data-ttu-id="e9209-155">Após a atualização, você deve ver o **bloco de política de anexo seguro**novo e habilitado.</span><span class="sxs-lookup"><span data-stu-id="e9209-155">After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="e9209-156">Clique na guia **links seguros** e depois clique no sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="e9209-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="e9209-157">Na janela **nova política de segurança de links**, em **Nome**, digite **Política de Link Seguro**.</span><span class="sxs-lookup"><span data-stu-id="e9209-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="e9209-158">Para **Selecionar a ação a ser tomada em relação a URLs potencialmente mal intencionadas e desconhecidas em mensagens.**, clique em **Ativado** e depois selecione **Não permitir que os usuários cliquem até a URL original**.</span><span class="sxs-lookup"><span data-stu-id="e9209-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="e9209-159">Para **Aplicado a**, clique na seta para baixo e depois em **O domínio do destinatário é**.</span><span class="sxs-lookup"><span data-stu-id="e9209-159">For **Applied to**, click the down arrow, and then click **The recipient domain is**.</span></span> <span data-ttu-id="e9209-160">Na janela, clique no nome da sua organização (como contoso.onmicrosoft.com) e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9209-160">In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="e9209-p108">Clique em **Salvar**. Você verá o novo item habilitado **Política de Link Seguro**.</span><span class="sxs-lookup"><span data-stu-id="e9209-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="e9209-163">Fase 4: Mostrar a ATP em ação</span><span class="sxs-lookup"><span data-stu-id="e9209-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="e9209-164">Nesta fase, você demonstrará como a ATP lida com emails potencialmente mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="e9209-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="e9209-165">Na instância do Internet Explorer que você usou para enviar o email na fase 2, na navegação à esquerda, clique em **itens enviados.**</span><span class="sxs-lookup"><span data-stu-id="e9209-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="e9209-166">Clique no email intitulado **suas novas chaves**, clique no ícone de seta para baixo e, em \*\*\*\* seguida, clique em encaminhar.</span><span class="sxs-lookup"><span data-stu-id="e9209-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="e9209-167">Para a nova mensagem, em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste e clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="e9209-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="e9209-168">Clique no email intitulado **novo site de viagem**, clique no ícone de seta para baixo, clique em **responder a todos**e, em seguida, clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="e9209-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="e9209-p109">Na instância do Internet Explorer que você usou para configurar as políticas de ATP na Fase 3, clique na guia Centro de administração do Exchange, clique no bloco Aplicativos e depois clique em **Email**. Você verá duas novas mensagens de email na caixa de entrada:</span><span class="sxs-lookup"><span data-stu-id="e9209-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="e9209-171">Uma delas como o título **Enc: Suas novas chaves**</span><span class="sxs-lookup"><span data-stu-id="e9209-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="e9209-172">Uma delas como o título **Enc: Novo site de viagem**</span><span class="sxs-lookup"><span data-stu-id="e9209-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="e9209-173">Abra a mensagem de email chamada **FW: novo site de viagem** e clique no link **este site** .</span><span class="sxs-lookup"><span data-stu-id="e9209-173">Open the email message titled **Fw: New travel web site** and click the **this site** link.</span></span> <span data-ttu-id="e9209-174">Você verá um "este site foi classificado como mal-intencionado".</span><span class="sxs-lookup"><span data-stu-id="e9209-174">You should see a "This website has been classified as malicious."</span></span> <span data-ttu-id="e9209-175">da.</span><span class="sxs-lookup"><span data-stu-id="e9209-175">page.</span></span> <span data-ttu-id="e9209-176">Isso demonstra que a ATP impede que você acesse o site potencialmente mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="e9209-176">This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="e9209-177">Na guia Centro de administração do Exchange do Internet Explorer, na navegação à esquerda, clique em **fluxo de emails**.</span><span class="sxs-lookup"><span data-stu-id="e9209-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="e9209-178">Clique na guia **rastreamento de mensagens** e depois clique em **pesquisar**.</span><span class="sxs-lookup"><span data-stu-id="e9209-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="e9209-179">Na janela **Resultados do Rastreamento de Mensagens**, clique duas vezes na mensagem com o assunto **Suas novas chaves**.</span><span class="sxs-lookup"><span data-stu-id="e9209-179">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**.</span></span> <span data-ttu-id="e9209-180">Esta mensagem foi entregue com êxito para a caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="e9209-180">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="e9209-181">Feche esta janela.</span><span class="sxs-lookup"><span data-stu-id="e9209-181">Close this window.</span></span>
    
10. <span data-ttu-id="e9209-182">Clique duas vezes na mensagem com o assunto **Novo site de viagem**.</span><span class="sxs-lookup"><span data-stu-id="e9209-182">Double-click the message with the subject **New travel web site**.</span></span> <span data-ttu-id="e9209-183">Esta mensagem foi entregue com êxito para a caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="e9209-183">This message was successfully delivered to the Inbox.</span></span> <span data-ttu-id="e9209-184">Feche esta janela.</span><span class="sxs-lookup"><span data-stu-id="e9209-184">Close this window.</span></span>
    
11. <span data-ttu-id="e9209-185">Clique duas vezes na mensagem com o assunto **Enc: Suas novas chaves**.</span><span class="sxs-lookup"><span data-stu-id="e9209-185">Double-click the message with the subject **Fw: Your new keys**.</span></span> <span data-ttu-id="e9209-186">Observe como essa mensagem foi processada pela ATP e entregue à caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="e9209-186">Note how this message was processed by ATP and then delivered to the Inbox.</span></span> <span data-ttu-id="e9209-187">Feche esta janela.</span><span class="sxs-lookup"><span data-stu-id="e9209-187">Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="e9209-188">O objetivo da política de anexos seguros era começar a examinar anexos por código mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="e9209-188">The purpose of the safe attachments policy was to begin scanning attachments for malicious code.</span></span> <span data-ttu-id="e9209-189">O anexo getKeys. js era permitido porque não foi determinado como mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="e9209-189">The getKeys.js attachment was allowed because it was not determined to be malicious.</span></span> <span data-ttu-id="e9209-190">Esta etapa mostra que a ATP executou uma verificação do anexo.</span><span class="sxs-lookup"><span data-stu-id="e9209-190">This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="e9209-191">Clique duas vezes na mensagem com o assunto **Enc: Novo site de viagem**.</span><span class="sxs-lookup"><span data-stu-id="e9209-191">Double-click the message with the subject **Fw: New travel web site**.</span></span> <span data-ttu-id="e9209-192">Observe que essa mensagem foi entregue com êxito para a caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="e9209-192">Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="e9209-193">Agora, você pode usar esse ambiente para criar novas políticas e fazer testes com a ATP.</span><span class="sxs-lookup"><span data-stu-id="e9209-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="e9209-194">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa Visual para todos os artigos da pilha do guia do laboratório de teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e9209-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e9209-195">Confira também
</span><span class="sxs-lookup"><span data-stu-id="e9209-195">See Also</span></span>

[<span data-ttu-id="e9209-196">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="e9209-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="e9209-197">Ambiente de desenvolvimento/teste para a Configuração Base</span><span class="sxs-lookup"><span data-stu-id="e9209-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="e9209-198">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e9209-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="e9209-199">DirSync para o ambiente de desenvolvimento/ teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e9209-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e9209-200">Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="e9209-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e9209-201">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="e9209-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="e9209-202">Proteção avançada para anexos seguros e links seguros</span><span class="sxs-lookup"><span data-stu-id="e9209-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


