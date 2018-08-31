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
ms.openlocfilehash: 07411600db11c8eea825c0ef5b82ea1206d20e11
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914956"
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="80ed4-103">Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="80ed4-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="80ed4-104">**Resumo:** Configure e demonstre a Proteção Avançada contra Ameaças do Office 365 no seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="80ed4-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="80ed4-p101">O Office 365 avançadas ameaça proteção (ATP) é um recurso do Exchange Online Protection (EOP) que ajuda a manter o malware fora do seu email. Com ATP, você deve criar diretivas no Centro de administração do Exchange (EAC) ou a segurança &amp; Centro de conformidade que ajudam a garantir que seus usuários acessam apenas links ou anexos em emails que são identificadas como não mal-intencionado. Para obter mais informações, consulte [proteção contra ameaças avançadas para anexos seguros e links de seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="80ed4-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="80ed4-108">Com as instruções neste artigo, você configurará e testará a ATP na sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="80ed4-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="80ed4-109">Fase 1: Desenvolver seu ambiente de desenvolvimento e teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="80ed4-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="80ed4-110">Se você quiser testar ATP de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="80ed4-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="80ed4-111">Se você quiser testar ATP em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="80ed4-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="80ed4-p102">O teste da ATP não requer o ambiente de desenvolvimento e teste em uma empresa simulada, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do AD no Windows Server. Ele é fornecido aqui como uma opção para que você possa testar a ATP e fazer testes com ele em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="80ed4-114">Fase 2: Demonstrar o comportamento de entrega de email padrão do Office 365</span><span class="sxs-lookup"><span data-stu-id="80ed4-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="80ed4-115">Nesta fase, você demonstrará que, antes de configurar políticas de ATP, emails mal-intencionados são entregues às caixas de correio do Office 365 sem triagem ou mitigação.</span><span class="sxs-lookup"><span data-stu-id="80ed4-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="80ed4-116">Abra o Internet Explorer e entrar com a conta do Outlook que você criou na fase 2 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="80ed4-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="80ed4-117">Se estiver usando o ambiente de desenvolvimento e teste leve do Office 365, abra uma sessão particular do Internet Explorer e entre com o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="80ed4-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="80ed4-118">Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, use o [portal Azure](https://portal.azure.com) para conectar a máquina virtual CLIENT1 e entrar em CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="80ed4-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="80ed4-119">Execute o Bloco de Notas e insira algum texto.</span><span class="sxs-lookup"><span data-stu-id="80ed4-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="80ed4-120">Salve o arquivo na pasta Documentos como **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="80ed4-121">Na guia Email do Outlook do Internet Explorer, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="80ed4-122">Em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste.</span><span class="sxs-lookup"><span data-stu-id="80ed4-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="80ed4-123">Para o assunto, digite **Suas novas chaves**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="80ed4-124">No corpo, digite **Aqui está o arquivo**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="80ed4-125">Clique em **Anexar**, clique duas vezes em **getKeys.js** na pasta Documentos, clique em **Anexar como cópia** e depois clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="80ed4-126">Clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-126">Click **New**.</span></span>
    
10. <span data-ttu-id="80ed4-127">Em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste.</span><span class="sxs-lookup"><span data-stu-id="80ed4-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="80ed4-128">Para o assunto, digite **Novo site de viagem**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="80ed4-129">No corpo, digite **Alguém me encaminhou este site**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="80ed4-130">No corpo, selecione o texto **este site** e clique no ícone de hiperlink na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="80ed4-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="80ed4-131">Em **URL**, digite **http://www.spamlink.contoso.com/**, clique em **Okey**e, em seguida, clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="80ed4-132">Abra uma instância separada do Internet Explorer no modo de navegação privada, vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e se conectar à sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="80ed4-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="80ed4-133">Na página principal do portal, clique no bloco Aplicativos e depois em **Email**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="80ed4-134">Em Caixa de Entrada, clique na mensagem com o assunto **Suas novas chaves**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="80ed4-p103">Na pasta Lixo eletrônico, clique na mensagem com o assunto **New viajam o site da web**. Dentro da mensagem, clique no link de **neste site** . Você deverá ver "Oops! Página do Internet Explorer não pôde encontrar spamlink.contoso.com.". Este é o resultado correto porque não há nenhuma página da web nesse local.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="80ed4-p104">Observe que ambos os emails potencialmente mal-intencionados foram entregues com êxito. O email **Suas novas chaves** poderia conter malware não detectado, e o usuário poderia clicar no link possivelmente mal-intencionado no email **Novo site de viagem**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="80ed4-143">Fase 3: Configurar políticas de anexo seguro e links seguros para a ATP</span><span class="sxs-lookup"><span data-stu-id="80ed4-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="80ed4-144">Nesta fase, você criará e configurará uma política de anexo seguro para impedir a entrega de emails com anexos possivelmente mal-intencionados e uma política de links seguros para impedir que os usuários acessem URLs possivelmente não seguras.</span><span class="sxs-lookup"><span data-stu-id="80ed4-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="80ed4-145">Na guia **Página inicial do Microsoft Office** do Internet Explorer, clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="80ed4-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="80ed4-146">Na navegação à esquerda, clique em **Centros de administração** e depois em **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="80ed4-147">Na navegação à esquerda da guia Centro de administração do Exchange, clique em **ameaças avançadas**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="80ed4-148">Clique na guia **anexos seguros** e depois clique no sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="80ed4-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="80ed4-149">Na janela **nova diretiva de segurança de anexos** , em **nome**, digite **Seguros política de anexo - bloco**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="80ed4-150">**Resposta de malware desconhecido anexos seguros**, clique em **Bloquear**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="80ed4-151">Para **Redirecionar o anexo na detecção**, clique em **Habilitar redirecionamento** e digite o endereço de email da sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="80ed4-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="80ed4-p105">Para **aplicado a**, clique na seta e, em seguida, clique em **domínio do destinatário é**. Na janela, clique em nome de sua organização (por exemplo, contoso.onmicrosoft.com) e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="80ed4-p106">Clique em **Salvar**. Depois da atualização, você verá a nova e habilitado a **Política de anexo seguros - bloco**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="80ed4-156">Clique na guia **links seguros** e depois clique no sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="80ed4-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="80ed4-157">Na janela **nova política de segurança de links**, em **Nome**, digite **Política de Link Seguro**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="80ed4-158">Para **Selecionar a ação a ser tomada em relação a URLs potencialmente mal intencionadas e desconhecidas em mensagens.**, clique em **Ativado** e depois selecione **Não permitir que os usuários cliquem até a URL original**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="80ed4-p107">Para **aplicado a**, clique na seta e, em seguida, clique em **domínio do destinatário é**. Na janela, clique em nome de sua organização (por exemplo, contoso.onmicrosoft.com) e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="80ed4-p108">Clique em **Salvar**. Você verá o novo item habilitado **Política de Link Seguro**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="80ed4-163">Fase 4: Mostrar a ATP em ação</span><span class="sxs-lookup"><span data-stu-id="80ed4-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="80ed4-164">Nesta fase, você demonstrará como a ATP lida com emails potencialmente mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="80ed4-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="80ed4-165">Da instância do Internet Explorer que você usou para enviar o email na fase 2, no painel de navegação esquerdo, clique em **itens enviados.**</span><span class="sxs-lookup"><span data-stu-id="80ed4-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="80ed4-166">Clique em email intitulado **suas novas chaves**, clique no ícone de seta para baixo e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="80ed4-167">Para a nova mensagem, em **Para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de teste e clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="80ed4-168">Clique em email intitulado **New viajam o site da web**, clique no ícone de seta para baixo, clique em **responder a todos**e clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="80ed4-p109">Na instância do Internet Explorer que você usou para configurar as políticas de ATP na Fase 3, clique na guia Centro de administração do Exchange, clique no bloco Aplicativos e depois clique em **Email**. Você verá duas novas mensagens de email na caixa de entrada:</span><span class="sxs-lookup"><span data-stu-id="80ed4-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="80ed4-171">Uma delas como o título **Enc: Suas novas chaves**</span><span class="sxs-lookup"><span data-stu-id="80ed4-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="80ed4-172">Uma delas como o título **Enc: Novo site de viagem**</span><span class="sxs-lookup"><span data-stu-id="80ed4-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="80ed4-p110">Abra a mensagem de email denominada **firmware: novo site de viagens** e clique no link **neste site** . Você deverá ver uma página "Este site tiver sido classificado como sendo maliciosas.". Isso demonstra que ATP está impedindo acessem o site da web potencialmente mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="80ed4-177">Na guia Centro de administração do Exchange do Internet Explorer, na navegação à esquerda, clique em **fluxo de emails**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="80ed4-178">Clique na guia **rastreamento de mensagens** e depois clique em **pesquisar**.</span><span class="sxs-lookup"><span data-stu-id="80ed4-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="80ed4-p111">Na janela de **Resultados de rastreamento de mensagem** , clique duas vezes a mensagem com o assunto **suas novas chaves**. Essa mensagem foi entregue com êxito para a caixa de entrada. Feche essa janela.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="80ed4-p112">Clique duas vezes a mensagem com o assunto **New viajam o site da web**. Essa mensagem foi entregue com êxito para a caixa de entrada. Feche essa janela.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="80ed4-p113">Clique duas vezes a mensagem com o assunto **firmware: suas novas chaves**. Observe como esta mensagem foi processada pelo ATP e, em seguida, entregue à caixa de entrada. Feche essa janela.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="80ed4-p114">A finalidade da diretiva de segurança de anexos era começar a verificação de anexos para código mal-intencionado. O anexo getKeys.js foi permitido porque não foi determinado mal-intencionados. Esta etapa mostra que ATP executa um exame do anexo.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="80ed4-p115">Clique duas vezes a mensagem com o assunto **firmware: novo site de viagens**. Observe que essa mensagem foi entregue com êxito para a caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="80ed4-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="80ed4-193">Agora, você pode usar esse ambiente para criar novas políticas e fazer testes com a ATP.</span><span class="sxs-lookup"><span data-stu-id="80ed4-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="80ed4-194">Clique [aqui](http://aka.ms/catlgstack) para ver um mapa visual para todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="80ed4-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="80ed4-195">Confira também</span><span class="sxs-lookup"><span data-stu-id="80ed4-195">See Also</span></span>

[<span data-ttu-id="80ed4-196">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="80ed4-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
<span data-ttu-id="80ed4-197">[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="80ed4-197">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>
  
[<span data-ttu-id="80ed4-198">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="80ed4-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="80ed4-199">DirSync para o ambiente de desenvolvimento/ teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="80ed4-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="80ed4-200">Segurança de Aplicativo na Nuvem para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="80ed4-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="80ed4-201">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="80ed4-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="80ed4-202">Proteção avançada para anexos seguros e links seguros</span><span class="sxs-lookup"><span data-stu-id="80ed4-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


