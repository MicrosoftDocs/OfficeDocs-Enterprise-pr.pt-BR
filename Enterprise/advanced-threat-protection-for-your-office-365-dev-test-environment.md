---
title: "Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "Resumo: Configurar e demonstrar a proteção de ameaça avançadas do Office 365 em seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: 2715e2722ab2826d4a4e05db0f9bd4cd9035fb98
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="db5fa-103">Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="db5fa-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="db5fa-104">**Resumo:** Configurar e demonstrar a proteção de ameaça avançadas do Office 365 em seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="db5fa-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="db5fa-p101">O Office 365 avançadas ameaça proteção (ATP) é um recurso do Exchange Online Protection (EOP) que ajuda a manter o malware fora do seu email. Com ATP, você deve criar diretivas no Centro de administração do Exchange (EAC) ou a segurança &amp; Centro de conformidade que ajudam a garantir que seus usuários acessam apenas links ou anexos em emails que são identificadas como não mal-intencionado. Para obter mais informações, consulte [proteção contra ameaças avançadas para anexos seguros e links de seguros](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="db5fa-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security &amp; Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see [Advanced threat protection for safe attachments and safe links](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx).</span></span>
  
<span data-ttu-id="db5fa-108">Com as instruções neste artigo, você configurará e testará a ATP na sua assinatura de avaliação do Office 365.</span><span class="sxs-lookup"><span data-stu-id="db5fa-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="db5fa-109">Fase 1: Desenvolver seu ambiente de desenvolvimento e teste do Office 365 leve ou em uma empresa simulada</span><span class="sxs-lookup"><span data-stu-id="db5fa-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="db5fa-110">Se você quiser testar ATP de forma leve com os requisitos mínimos, siga as instruções em fases 2 e 3 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="db5fa-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="db5fa-111">Se você quiser testar ATP em uma empresa simulada, siga as instruções no [DirSync para seu ambiente de desenvolvimento e teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="db5fa-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="db5fa-p102">O teste da ATP não requer o ambiente de desenvolvimento e teste em uma empresa simulada, que inclui uma intranet simulada conectada à Internet e a sincronização de diretórios para uma floresta do AD no Windows Server. Ele é fornecido aqui como uma opção para que você possa testar a ATP e fazer testes com ele em um ambiente que representa uma organização típica.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="db5fa-114">Fase 2: Demonstrar o comportamento de entrega de email padrão do Office 365</span><span class="sxs-lookup"><span data-stu-id="db5fa-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="db5fa-115">Nesta fase, você demonstrará que, antes de configurar políticas de ATP, emails mal-intencionados são entregues às caixas de correio do Office 365 sem triagem ou mitigação.</span><span class="sxs-lookup"><span data-stu-id="db5fa-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="db5fa-116">Abra o Internet Explorer e entrar com a conta do Outlook que você criou na fase 2 do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="db5fa-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="db5fa-117">Se estiver usando o ambiente de desenvolvimento e teste leve do Office 365, abra uma sessão particular do Internet Explorer e entre com o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="db5fa-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="db5fa-118">Se você estiver usando o ambiente de desenvolvimento e teste do Office 365 enterprise simulado, use o [portal Azure](https://portal.azure.com) para conectar a máquina virtual CLIENT1 e entrar em CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="db5fa-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="db5fa-119">Execute o Bloco de Notas e insira algum texto.</span><span class="sxs-lookup"><span data-stu-id="db5fa-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="db5fa-120">Salve o arquivo para a pasta de documentos como **getKeys.js**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="db5fa-121">Na guia email do Outlook do Internet Explorer, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="db5fa-122">Na caixa **para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="db5fa-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="db5fa-123">Para o assunto, digite **suas novas chaves**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="db5fa-124">No corpo, digite **que aqui está o arquivo**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="db5fa-125">Clique em **Anexar**, clique duas vezes em **getKeys.js** na pasta documentos, clique em **Anexar como uma cópia**e, em seguida, clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="db5fa-126">Clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-126">Click **New**.</span></span>
    
10. <span data-ttu-id="db5fa-127">Na caixa **para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de avaliação.</span><span class="sxs-lookup"><span data-stu-id="db5fa-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="db5fa-128">Para o assunto, digite **New viajam o site da web**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="db5fa-129">No corpo, digite **que alguém me encaminhadas neste site**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="db5fa-130">No corpo, selecione o texto **deste site** e clique no ícone de hiperlink na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="db5fa-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="db5fa-131">Em **URL**, digite **http://www.spamlink.contoso.com/**, clique em **Okey**e, em seguida, clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="db5fa-132">Abra uma instância separada do Internet Explorer no modo de navegação particular, vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="db5fa-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="db5fa-133">Na página principal do portal, clique no lado de aplicativos e, em seguida, clique em **email**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="db5fa-134">Na caixa de entrada, clique na mensagem com o assunto **suas novas chaves**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="db5fa-p103">Na pasta Lixo eletrônico, clique na mensagem com o assunto **New viajam o site da web**. Dentro da mensagem, clique no link de **neste site** . Você deverá ver "Oops! Página do Internet Explorer não pôde encontrar spamlink.contoso.com.". Este é o resultado correto porque não há nenhuma página da web nesse local.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="db5fa-p104">Observe que ambos esses emails potencialmente mal-intencionados foram entregue com êxito. O email de **suas novas chaves** pode conter malware não detectado e o usuário foi permitido a clicar no link potencialmente mal-intencionados no email **novo site da web de viagens** .</span><span class="sxs-lookup"><span data-stu-id="db5fa-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="db5fa-143">Fase 3: Configurar políticas de anexo seguro e links seguros para a ATP</span><span class="sxs-lookup"><span data-stu-id="db5fa-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="db5fa-144">Nesta fase, você criará e configurará uma política de anexo seguro para impedir a entrega de emails com anexos possivelmente mal-intencionados e uma política de links seguros para impedir que os usuários acessem URLs possivelmente não seguras.</span><span class="sxs-lookup"><span data-stu-id="db5fa-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="db5fa-145">Na guia **Página inicial do Microsoft Office** do Internet Explorer, clique no lado do **Admin** .</span><span class="sxs-lookup"><span data-stu-id="db5fa-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="db5fa-146">No painel de navegação esquerdo, clique em **Admin centrais**e **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="db5fa-147">No painel de navegação à esquerda da guia Exchange admin center, clique em **Avançado de ameaças**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="db5fa-148">Clique na guia **anexos seguros** e, em seguida, clique no sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="db5fa-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="db5fa-149">Na janela **nova diretiva de segurança de anexos** , em **nome**, digite **Seguros política de anexo - bloco**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="db5fa-150">**Resposta de malware desconhecido anexos seguros**, clique em **Bloquear**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="db5fa-151">Para **redirecionar o anexo na detecção**, clique em **Habilitar redirecionamento** e digite o endereço de email da sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="db5fa-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="db5fa-p105">Para **aplicado a**, clique na seta e, em seguida, clique em **domínio do destinatário é**. Na janela, clique em nome de sua organização (por exemplo, contoso.onmicrosoft.com) e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="db5fa-p106">Clique em **Salvar**. Depois da atualização, você verá a nova e habilitado a **Política de anexo seguros - bloco**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="db5fa-156">Clique na guia **links seguros** e, em seguida, clique no sinal de adição.</span><span class="sxs-lookup"><span data-stu-id="db5fa-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="db5fa-157">Na janela **nova política de links de seguros** , em **nome**, digite **Diretiva de Link seguros**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="db5fa-158">Para **Selecionar a ação para URLs potencialmente mal-intencionados desconhecidos em mensagens**, clique **em**e selecione **não permitir aos usuários clicarem por meio de URL original**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="db5fa-p107">Para **aplicado a**, clique na seta e, em seguida, clique em **domínio do destinatário é**. Na janela, clique em nome de sua organização (por exemplo, contoso.onmicrosoft.com) e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="db5fa-p108">Clique em **Salvar**. Você verá a nova e habilitado para a **Política de Link seguros**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="db5fa-163">Fase 4: Mostrar a ATP em ação</span><span class="sxs-lookup"><span data-stu-id="db5fa-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="db5fa-164">Nesta fase, você demonstrará como a ATP lida com emails potencialmente mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="db5fa-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="db5fa-165">Da instância do Internet Explorer que você usou para enviar o email na fase 2, no painel de navegação esquerdo, clique em **itens enviados.**</span><span class="sxs-lookup"><span data-stu-id="db5fa-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="db5fa-166">Clique em email intitulado **suas novas chaves**, clique no ícone de seta para baixo e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="db5fa-167">Da nova mensagem, na **para**, digite o endereço de email do nome do administrador global do Office 365 da sua assinatura de avaliação e, em seguida, clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="db5fa-168">Clique em email intitulado **New viajam o site da web**, clique no ícone de seta para baixo, clique em **responder a todos**e clique em **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="db5fa-p109">Da instância do Internet Explorer que você usou para configurar políticas de ATP na fase 3, clique na guia de Central de administração do Exchange, clique no lado de aplicativos e, em seguida, clique em **email**. Você deverá ver duas novas mensagens de email na caixa de entrada:</span><span class="sxs-lookup"><span data-stu-id="db5fa-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="db5fa-171">Um intitulado **firmware: suas novas chaves**</span><span class="sxs-lookup"><span data-stu-id="db5fa-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="db5fa-172">Um intitulado **firmware: novo site de viagens**</span><span class="sxs-lookup"><span data-stu-id="db5fa-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="db5fa-p110">Abra a mensagem de email denominada **firmware: novo site de viagens** e clique no link **neste site** . Você deverá ver uma página "Este site tiver sido classificado como sendo maliciosas.". Isso demonstra que ATP está impedindo acessem o site da web potencialmente mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="db5fa-177">No Exchange admin center guia do Internet Explorer, no painel de navegação esquerdo, clique em **fluxo de emails**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="db5fa-178">Clique na guia **rastreamento de mensagem** e clique em **Pesquisar**.</span><span class="sxs-lookup"><span data-stu-id="db5fa-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="db5fa-p111">Na janela de **Resultados de rastreamento de mensagem** , clique duas vezes a mensagem com o assunto **suas novas chaves**. Essa mensagem foi entregue com êxito para a caixa de entrada. Feche essa janela.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="db5fa-p112">Clique duas vezes a mensagem com o assunto **New viajam o site da web**. Essa mensagem foi entregue com êxito para a caixa de entrada. Feche essa janela.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="db5fa-p113">Clique duas vezes a mensagem com o assunto **firmware: suas novas chaves**. Observe como esta mensagem foi processada pelo ATP e, em seguida, entregue à caixa de entrada. Feche essa janela.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="db5fa-p114">A finalidade da diretiva de segurança de anexos era começar a verificação de anexos para código mal-intencionado. O anexo getKeys.js foi permitido porque não foi determinado mal-intencionados. Esta etapa mostra que ATP executa um exame do anexo.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="db5fa-p115">Clique duas vezes a mensagem com o assunto **firmware: novo site de viagens**. Observe que essa mensagem foi entregue com êxito para a caixa de entrada.</span><span class="sxs-lookup"><span data-stu-id="db5fa-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="db5fa-193">Agora, você pode usar esse ambiente para criar novas políticas e fazer testes com a ATP.</span><span class="sxs-lookup"><span data-stu-id="db5fa-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="db5fa-194">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="db5fa-194">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="db5fa-195">Veja também</span><span class="sxs-lookup"><span data-stu-id="db5fa-195">See Also</span></span>

[<span data-ttu-id="db5fa-196">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="db5fa-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="db5fa-197">Ambiente de desenvolvimento e teste de configuração de base</span><span class="sxs-lookup"><span data-stu-id="db5fa-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="db5fa-198">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="db5fa-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="db5fa-199">DirSync para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="db5fa-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="db5fa-200">Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="db5fa-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="db5fa-201">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="db5fa-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

[<span data-ttu-id="db5fa-202">Proteção contra ameaças avançadas para anexos seguros e links de seguros</span><span class="sxs-lookup"><span data-stu-id="db5fa-202">Advanced threat protection for safe attachments and safe links</span></span>](https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653)


