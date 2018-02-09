---
title: Registrar o iOS e Android dispositivos em seu ambiente de desenvolvimento e teste do Microsoft Enterprise 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "Resumo: Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente."
ms.openlocfilehash: 77b5074b083656fdfa2cd460510231dae0689d10
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="124ae-103">Registrar o iOS e Android dispositivos em seu ambiente de desenvolvimento e teste do Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="124ae-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="124ae-104">**Resumo:** Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.</span><span class="sxs-lookup"><span data-stu-id="124ae-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="124ae-p101">O pacote de mobilidade do Microsoft Enterprise (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="124ae-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="124ae-p102">Se você precisar aplicar segurança em nível de dispositivo, deverá registrar dispositivos no Microsoft Intune. A inscrição de dispositivos não só ajuda você a gerenciar dispositivos de propriedade da empresa, como também dispositivos pessoais (BYOD) e compartilhados, dependendo das políticas legais da sua organização.</span><span class="sxs-lookup"><span data-stu-id="124ae-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="124ae-109">Seguindo as instruções fornecidas neste artigo, você poderá registrar e testar recursos de gerenciamento de dispositivo móvel básica para dispositivos com Android e iOS em seu ambiente de desenvolvimento e teste da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="124ae-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="124ae-110">Fase 1: Crie seu ambiente de desenvolvimento e teste da Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="124ae-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="124ae-111">Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="124ae-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="124ae-112">Fase 2: Personalizar o aplicativo de Portal da Empresa do Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="124ae-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="124ae-113">Use essas etapas para personalizar o aplicativo de Portal da Empresa do Microsoft Intune para sua empresa fictícia:</span><span class="sxs-lookup"><span data-stu-id="124ae-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="124ae-114">Em uma nova guia, abra o console de administração do Microsoft Intune ([https://manage.microsoft.com](https://manage.microsoft.com)).</span><span class="sxs-lookup"><span data-stu-id="124ae-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="124ae-115">Clique em **Admin** , no painel de navegação e, em seguida, clique em **Gerenciamento de dispositivos móveis** do painel de **Administração** .</span><span class="sxs-lookup"><span data-stu-id="124ae-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="124ae-p103">Na lista de **tarefas** , selecione **Definir autoridade de gerenciamento de dispositivo móvel**. Certifique-se de que ele está definido como **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="124ae-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="124ae-118">No painel **Administração** , clique em **Portal da empresa**.</span><span class="sxs-lookup"><span data-stu-id="124ae-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="124ae-119">No painel de **Portal da empresa** , defina as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="124ae-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="124ae-120">Nome da empresa: \<seu nome de empresa fictícia ></span><span class="sxs-lookup"><span data-stu-id="124ae-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="124ae-121">O nome do contato de departamento IT: **User5**</span><span class="sxs-lookup"><span data-stu-id="124ae-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="124ae-122">Número de telefone do departamento de IT: **555-1234**</span><span class="sxs-lookup"><span data-stu-id="124ae-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="124ae-123">Endereço de email do departamento de IT: **User5 @**\<nome da empresa fictícia de organização > **. onmicrosoft.com** (o endereço de email da conta User5)</span><span class="sxs-lookup"><span data-stu-id="124ae-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="124ae-124">Em **personalização**, selecione **verde** na **cor do tema**.</span><span class="sxs-lookup"><span data-stu-id="124ae-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="124ae-125">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-125">Click **Save**.</span></span>
    
<span data-ttu-id="124ae-126">Em seguida, você instalará o aplicativo de Portal da Empresa do Microsoft Intune e registrará um dispositivo iOS ou Android e depois testará a funcionalidade básica de gerenciamento do console de administração do Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="124ae-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="124ae-127">Fase 3 (apenas para dispositivos iOS): Inscrever e gerenciar um dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="124ae-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="124ae-128">Para inscrever um dispositivo iOS para gerenciamento pelo Intune, você precisará do seguinte:</span><span class="sxs-lookup"><span data-stu-id="124ae-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="124ae-129">Um dispositivo iOS, como um Apple iPad ou um iPhone.</span><span class="sxs-lookup"><span data-stu-id="124ae-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="124ae-130">Conhecimento da senha do dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="124ae-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="124ae-p104">Uma ID da Apple (um nome de conta e senha). Se você não tiver um, vá para o [website da ID da Apple](https://appleid.apple.com/#!&amp;page=signin) e clique em **criar sua ID da Apple**. Crie uma ID da Apple correspondente à conta de administrador global de sua assinatura do Office 365. Registre seu novo nome de conta do Apple ID e a senha em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="124ae-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="124ae-p105">Um certificado do Apple Push Notification Service (APNs) é necessário para o Intune gerenciar dispositivos iOS e Mac. Quando o certificado for adicionado ao Intune, os usuários poderão instalar o aplicativo de Portal da Empresa do Microsoft Intune para registrarem seus dispositivos, ou o administrador poderá configurar o gerenciamento de dispositivos iOS de propriedade da empresa.</span><span class="sxs-lookup"><span data-stu-id="124ae-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="124ae-p106">Você precisa de um arquivo de solicitação de assinatura de certificado para solicitar um certificado de relação de confiança do Apple Push Certificates Portal. Para obter um arquivo de solicitação de assinatura de certificado:</span><span class="sxs-lookup"><span data-stu-id="124ae-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="124ae-139">No console de administração do Microsoft Intune, clique em **Admin** , no painel de navegação.</span><span class="sxs-lookup"><span data-stu-id="124ae-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="124ae-140">No painel **Administração** , abra **gerenciamento de dispositivos móveis > iOS e Mac OS X**e clique em **carregar um certificado APNs** em **tarefas**.</span><span class="sxs-lookup"><span data-stu-id="124ae-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="124ae-p107">No painel de **carregar um certificado APNs** , clique em **Baixar a solicitação de certificado APNs**. Salve o arquivo de solicitação (.csr) localmente com o nome do **teste de desenvolvimento**de assinatura de certificado.</span><span class="sxs-lookup"><span data-stu-id="124ae-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="124ae-143">Para obter um certificado do Apple Push Notification Service:</span><span class="sxs-lookup"><span data-stu-id="124ae-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="124ae-144">Abrir uma nova guia, vá para o [Portal do Apple Push certificados](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)e entrar com sua ID de Apple.</span><span class="sxs-lookup"><span data-stu-id="124ae-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="124ae-145">Na página **Introdução** , clique em **criar um certificado**.</span><span class="sxs-lookup"><span data-stu-id="124ae-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="124ae-146">Na página **Termos de uso** , selecione **eu leu e concorda com estes termos e condições**e, em seguida, clique em **Aceitar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="124ae-p108">Na página **criar um novo certificado de Push** , clique em **Procurar** e selecione o arquivo de **dev-test.csr** salvo no procedimento anterior e, em seguida, clique em **carregar**. Quando solicitado para abrir um arquivo json, salve-o na mesma pasta onde o arquivo dev-test.csr está armazenado.</span><span class="sxs-lookup"><span data-stu-id="124ae-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="124ae-149">Abra o [Portal do Apple Push certificados](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) em uma guia diferente e para **os certificados para servidores de terceiros**, clique em **Baixar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="124ae-p109">Quando solicitado para abrir um arquivo de .pem, salve-o com o nome **dev-test.pem** na mesma pasta onde o arquivo dev-test.csr está armazenado. Esse é o seu certificado APNs.</span><span class="sxs-lookup"><span data-stu-id="124ae-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="124ae-152">Para carregar o certificado APNs no Intune:</span><span class="sxs-lookup"><span data-stu-id="124ae-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="124ae-153">Na guia de console de administração do Microsoft Intune, na página **carregar um certificado APNs** , clique em **carregar o certificado APNs**.</span><span class="sxs-lookup"><span data-stu-id="124ae-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="124ae-154">Clique em **Procurar** e especifique o arquivo **dev-test.pem** .</span><span class="sxs-lookup"><span data-stu-id="124ae-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="124ae-p110">Clique em **Abrir**, digite seu nome de conta da ID da Apple e, em seguida, clique em **carregar**. Você verá uma mensagem **pronto para inscrição** na página **iOS e configuração do gerenciamento de dispositivo do MaxOS X Mobile** .</span><span class="sxs-lookup"><span data-stu-id="124ae-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="124ae-157">Com o certificado APNs instalado, agora o Intune pode registrar e gerenciar dispositivos iOS, enviando a política por push para os dispositivos móveis inscritos.</span><span class="sxs-lookup"><span data-stu-id="124ae-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="124ae-158">Para baixar o aplicativo de Portal da Empresa do Microsoft Intune e registrar o dispositivo iOS:</span><span class="sxs-lookup"><span data-stu-id="124ae-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="124ae-159">No seu dispositivo iOS, entre com seu ID Apple.</span><span class="sxs-lookup"><span data-stu-id="124ae-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="124ae-160">Abra o aplicativo de **Repositório da Apple** .</span><span class="sxs-lookup"><span data-stu-id="124ae-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="124ae-161">Digite **intune** na caixa Pesquisar e toque em **Microsoft Intune Portal da empresa**, e em seguida, **obter**e **instalar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="124ae-162">Depois que ele instala, toque em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="124ae-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="124ae-163">Na tela do **Portal da empresa Intune** , entre com sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="124ae-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="124ae-164">Na tela **Configuração de acesso empresa** , toque em **Iniciar**e, em seguida, toque duas vezes em **continuar** .</span><span class="sxs-lookup"><span data-stu-id="124ae-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="124ae-165">Sobre o **o que vem em seguida?** tela, toque em **registrar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="124ae-166">Sobre o **Ativar o administrador do dispositivo?** tela, toque em **Ativar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="124ae-167">Na tela de **Gerenciamento de perfil** , toque em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="124ae-168">Em **Inserir senha**, digite sua senha de dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="124ae-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="124ae-169">Na tela **o que vem em seguida** , toque em **registrar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="124ae-170">**Instalar o perfil**, toque em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="124ae-171">Na página **Aviso** , toque em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="124ae-172">No **Gerenciamento remoto**, toque em **Confiar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="124ae-173">Toque em **concluído** para concluir o processo de inscrição.</span><span class="sxs-lookup"><span data-stu-id="124ae-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="124ae-174">Quando solicitado a **abri-la no "Composição de Portal"?**, toque em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="124ae-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="124ae-175">Na tela **Configuração de acesso empresa** , toque em **Iniciar**e, em seguida, toque em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="124ae-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="124ae-176">Na tela principal do aplicativo de Portal da Empresa do Microsoft Intune, você verá:</span><span class="sxs-lookup"><span data-stu-id="124ae-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="124ae-177">Uma faixa verde.</span><span class="sxs-lookup"><span data-stu-id="124ae-177">A green banner.</span></span>
    
  - <span data-ttu-id="124ae-178">O nome da empresa fictícia no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="124ae-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="124ae-179">O nome do dispositivo iOS listado em **Meus dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="124ae-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="124ae-180">Na seção de **assistência técnica** , o **Nome do contato** do **User5** com o número de telefone de **555-1234** e um botão de **contato por email** .</span><span class="sxs-lookup"><span data-stu-id="124ae-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="124ae-p111">O Microsoft Intune fornece recursos de bloqueio e redefinição de senha remotos. Se alguém perder um dispositivo, você poderá bloqueá-lo remotamente. Se alguém se esquecer da senha, você poderá removê-la remotamente.</span><span class="sxs-lookup"><span data-stu-id="124ae-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="124ae-184">Para bloquear um dispositivo iOS remotamente:</span><span class="sxs-lookup"><span data-stu-id="124ae-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="124ae-185">Do seu computador de administração, na guia de console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="124ae-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="124ae-186">No painel **grupos** , abra **todos os dispositivos > dispositivos móveis todos > todos os dispositivos gerenciados direto**.</span><span class="sxs-lookup"><span data-stu-id="124ae-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="124ae-187">No painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="124ae-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="124ae-188">Na lista de dispositivos, clique no seu dispositivo iOS. </span><span class="sxs-lookup"><span data-stu-id="124ae-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="124ae-189">No seu dispositivo iOS, certifique-se de que ele esteja na tela principal. </span><span class="sxs-lookup"><span data-stu-id="124ae-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="124ae-p112">No seu computador de administração, na barra de tarefas, clique em **tarefas remotas > bloqueio remoto**. Assista seu dispositivo iOS conforme ele alterna para a tela de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="124ae-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="124ae-192">Para remover a senha:</span><span class="sxs-lookup"><span data-stu-id="124ae-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="124ae-193">Do seu computador de administração, no painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="124ae-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="124ae-p113">Na lista, clique em seu dispositivo iOS. Na barra de tarefas, clique em **tarefas remotas > redefinição de senha**. Aguarde um minuto.</span><span class="sxs-lookup"><span data-stu-id="124ae-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="124ae-p114">No seu dispositivo iOS, desbloqueá-lo e observe que não há uma senha. Para alterar a senha novamente, vá para **configurações**e, em seguida, a **senha**.</span><span class="sxs-lookup"><span data-stu-id="124ae-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="124ae-199">Fase 3 (apenas para dispositivos Android): Inscrever e gerenciar um dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="124ae-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="124ae-200">Você precisará do seguinte para registrar um dispositivo Android para gerenciamento pelo Intune:</span><span class="sxs-lookup"><span data-stu-id="124ae-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="124ae-201">Um dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="124ae-201">An Android device.</span></span>
    
- <span data-ttu-id="124ae-202">Conhecimento da senha do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="124ae-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="124ae-203">Para baixar o aplicativo de Portal da Empresa do Intune e registrar o dispositivo:</span><span class="sxs-lookup"><span data-stu-id="124ae-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="124ae-204">Usando seu dispositivo Android, vá para o **Repositório do Google tocar**e, em seguida, toque em **Guia de Introdução**.</span><span class="sxs-lookup"><span data-stu-id="124ae-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="124ae-205">Digite **intune** na caixa Pesquisar e toque em **intune portal da empresa** nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="124ae-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="124ae-206">Toque no item **Intune Portal da empresa** e, em seguida, toque em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="124ae-207">Na tela **para concluir a configuração de conta** , toque em **continuar**e, em seguida, **Ignore**.</span><span class="sxs-lookup"><span data-stu-id="124ae-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="124ae-p115">No **Portal de empresa Intune**, toque em **Aceitar**. O aplicativo é instalado.</span><span class="sxs-lookup"><span data-stu-id="124ae-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="124ae-210">Toque em **Abrir**e, em seguida, toque em **entrar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="124ae-211">Na tela do **Portal da empresa Intune** , entre com sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="124ae-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="124ae-212">Na tela **Configuração de acesso empresa** , toque em **Iniciar**e, em seguida, **continuar** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="124ae-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="124ae-213">Sobre o **o que vem em seguida?** tela, toque em **registrar**.</span><span class="sxs-lookup"><span data-stu-id="124ae-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="124ae-214">Sobre o **Ativar o administrador do dispositivo?** tela, toque em **Activate.**</span><span class="sxs-lookup"><span data-stu-id="124ae-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="124ae-p116">Na tela de **Diretiva de privacidade** , selecione **eu confirmar** e, em seguida, toque em **Confirmar**. Aguarde o conclusão do processo de inscrição.</span><span class="sxs-lookup"><span data-stu-id="124ae-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="124ae-217">Na tela de **Configuração de acesso empresa** , toque **continuar**e, em seguida, toque em **concluído**.</span><span class="sxs-lookup"><span data-stu-id="124ae-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="124ae-218">Na tela principal do aplicativo de Portal da Empresa do Microsoft Intune, você verá uma faixa verde e o nome da empresa fictícia no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="124ae-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="124ae-p117">Toque em **Meus dispositivos**. Você deve ver seu nome de dispositivo Android na lista.</span><span class="sxs-lookup"><span data-stu-id="124ae-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="124ae-p118">Toque em **contato IT**. Você deverá ver o número de telefone de **555-1234**, um botão de **contatos por email** , e entre em contato com o IT de **User5**.</span><span class="sxs-lookup"><span data-stu-id="124ae-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="124ae-p119">O Microsoft Intune fornece recursos de bloqueio e redefinição de senha remotos. Se alguém perder um dispositivo, você poderá bloqueá-lo remotamente. Se alguém se esquecer da senha, você poderá redefini-la remotamente.</span><span class="sxs-lookup"><span data-stu-id="124ae-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="124ae-226">Para bloquear um dispositivo Android remotamente:</span><span class="sxs-lookup"><span data-stu-id="124ae-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="124ae-227">Do seu computador de administração, na guia de console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="124ae-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="124ae-228">No painel **grupos** , abra **todos os dispositivos > dispositivos móveis todos > todos os dispositivos gerenciados direto**.</span><span class="sxs-lookup"><span data-stu-id="124ae-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="124ae-229">No painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="124ae-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="124ae-230">Na lista de dispositivos, clique no seu dispositivo Android. </span><span class="sxs-lookup"><span data-stu-id="124ae-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="124ae-231">No seu dispositivo Android, certifique-se de que ele esteja na tela principal. </span><span class="sxs-lookup"><span data-stu-id="124ae-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="124ae-p120">No seu computador de administração, na barra de tarefas, clique em **tarefas remotas > bloqueio remoto**. Quando solicitado, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="124ae-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="124ae-234">Observe seu dispositivo Android entrando na tela de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="124ae-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="124ae-235">Quando você redefinir a senha para dispositivos com Android, o portal de administração Intune gera e configura uma senha forte.</span><span class="sxs-lookup"><span data-stu-id="124ae-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="124ae-236">Para redefinir a senha remotamente:</span><span class="sxs-lookup"><span data-stu-id="124ae-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="124ae-237">Do seu computador de administração, na guia de console de administração do Microsoft Intune do navegador, no painel de **Todos os dispositivos gerenciados direta** , clique em seu dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="124ae-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="124ae-238">Na barra de tarefas, clique em **tarefas remotas > redefinição de senha**.</span><span class="sxs-lookup"><span data-stu-id="124ae-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="124ae-p121">Sobre o **tarefa remota: redefinição de senha** solicitar, clique em **Sim**. Aguarde um minuto.</span><span class="sxs-lookup"><span data-stu-id="124ae-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="124ae-241">No painel de **Todos os dispositivos gerenciados direta** , clique em **Exibir propriedades**.</span><span class="sxs-lookup"><span data-stu-id="124ae-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="124ae-242">Em **Redefinição de senha**, observe a nova senha.</span><span class="sxs-lookup"><span data-stu-id="124ae-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="124ae-243">No seu dispositivo Android, insira a nova senha na tela de bloqueio. </span><span class="sxs-lookup"><span data-stu-id="124ae-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="124ae-244">Para alterar a senha novamente, entram em **configurações**, toque em **dispositivo**, toque em **tela de bloqueio**, insira a nova senha novamente, toque em **bloqueio de tela**e sua escolha para a senha.</span><span class="sxs-lookup"><span data-stu-id="124ae-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="124ae-245">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="124ae-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="124ae-246">Veja também</span><span class="sxs-lookup"><span data-stu-id="124ae-246">See Also</span></span>

[<span data-ttu-id="124ae-247">O ambiente de desenvolvimento e teste da Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="124ae-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="124ae-248">Políticas MAM para seu ambiente de desenvolvimento e teste da Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="124ae-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="124ae-249">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="124ae-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="124ae-250">Mobilidade corporativos + segurança (EMS)</span><span class="sxs-lookup"><span data-stu-id="124ae-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


