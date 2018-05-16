---
title: Registrar o iOS e Android dispositivos em seu ambiente de desenvolvimento e teste do Microsoft Enterprise 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumo: Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.'
ms.openlocfilehash: b5ceecd74ac010d787bc580054d5dd43db952fef
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="76e52-103">Registrar o iOS e Android dispositivos em seu ambiente de desenvolvimento e teste do Microsoft Enterprise 365</span><span class="sxs-lookup"><span data-stu-id="76e52-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="76e52-104">**Resumo:** Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.</span><span class="sxs-lookup"><span data-stu-id="76e52-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="76e52-p101">O pacote de mobilidade do Microsoft Enterprise (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="76e52-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="76e52-p102">Se você precisar aplicar segurança no nível do dispositivo, você deve registrar os dispositivos em Microsoft Intune. Registro do dispositivo não apenas ajuda a gerenciar os dispositivos de propriedade da organização, mas também pessoal (BYOD) e dispositivos compartilhados, dependendo da sua organização do legal políticas.</span><span class="sxs-lookup"><span data-stu-id="76e52-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="76e52-109">Seguindo as instruções fornecidas neste artigo, você poderá registrar e testar recursos de gerenciamento de dispositivo móvel básica para dispositivos com Android e iOS em seu ambiente de desenvolvimento e teste da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="76e52-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="76e52-110">Fase 1: Crie seu ambiente de desenvolvimento e teste da Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="76e52-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="76e52-111">Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="76e52-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="76e52-112">Fase 2: Registrar seus dispositivos com Android e iOS</span><span class="sxs-lookup"><span data-stu-id="76e52-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="76e52-113">Primeiro, use as instruções em [instalar e acesse o aplicativo de Portal da empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar o aplicativo do Portal do Microsoft Intune empresa para seu locatário de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="76e52-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="76e52-114">Em seguida, use as instruções em [Configurar o acesso aos seus recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para registrar um dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="76e52-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="76e52-115">Em seguida, use as instruções em [registrar seu dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para registrar um dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="76e52-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="76e52-116">Fase 2: Gerenciar seus dispositivos com Android e iOS remotamente</span><span class="sxs-lookup"><span data-stu-id="76e52-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="76e52-p103">O Microsoft Intune fornece recursos de bloqueio e redefinição de senha remotos. Se alguém perder um dispositivo, você poderá bloqueá-lo remotamente. Se alguém se esquecer da senha, você poderá removê-la remotamente.</span><span class="sxs-lookup"><span data-stu-id="76e52-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="76e52-120">Para bloquear um dispositivo iOS remotamente:</span><span class="sxs-lookup"><span data-stu-id="76e52-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="76e52-121">Abra uma nova guia e vá para http://manage.microsoft.com (se necessário).</span><span class="sxs-lookup"><span data-stu-id="76e52-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="76e52-122">No console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="76e52-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="76e52-123">No painel **grupos** , abra **todos os dispositivos > dispositivos móveis todos > todos os dispositivos gerenciados direto**.</span><span class="sxs-lookup"><span data-stu-id="76e52-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="76e52-124">No painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="76e52-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="76e52-125">Na lista de dispositivos, clique no seu dispositivo iOS. </span><span class="sxs-lookup"><span data-stu-id="76e52-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="76e52-126">No seu dispositivo iOS, certifique-se de que ele esteja na tela principal. </span><span class="sxs-lookup"><span data-stu-id="76e52-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="76e52-p104">No seu computador de administração, na barra de tarefas, clique em **tarefas remotas > bloqueio remoto**. Assista seu dispositivo iOS conforme ele alterna para a tela de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="76e52-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="76e52-129">Para remover a senha:</span><span class="sxs-lookup"><span data-stu-id="76e52-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="76e52-130">Do seu computador de administração, no painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="76e52-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="76e52-p105">Na lista, clique em seu dispositivo iOS. Na barra de tarefas, clique em **tarefas remotas > redefinição de senha**. Aguarde um minuto.</span><span class="sxs-lookup"><span data-stu-id="76e52-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="76e52-p106">No seu dispositivo iOS, desbloqueá-lo e observe que não há uma senha. Para alterar a senha novamente, vá para **configurações**e, em seguida, a **senha**.</span><span class="sxs-lookup"><span data-stu-id="76e52-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="76e52-136">Para bloquear um dispositivo Android remotamente:</span><span class="sxs-lookup"><span data-stu-id="76e52-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="76e52-137">No console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="76e52-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="76e52-138">No painel **grupos** , abra **todos os dispositivos > dispositivos móveis todos > todos os dispositivos gerenciados direto**.</span><span class="sxs-lookup"><span data-stu-id="76e52-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="76e52-139">No painel de **Todos os dispositivos gerenciados direta** , clique na guia **dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="76e52-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="76e52-140">Na lista de dispositivos, clique no seu dispositivo Android. </span><span class="sxs-lookup"><span data-stu-id="76e52-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="76e52-141">No seu dispositivo Android, certifique-se de que ele esteja na tela principal. </span><span class="sxs-lookup"><span data-stu-id="76e52-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="76e52-p107">No seu computador de administração, na barra de tarefas, clique em **tarefas remotas > bloqueio remoto**. Quando solicitado, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="76e52-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="76e52-144">Observe seu dispositivo Android entrando na tela de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="76e52-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="76e52-145">Quando você redefinir a senha para dispositivos com Android, o portal de administração Intune gera e configura uma senha forte.</span><span class="sxs-lookup"><span data-stu-id="76e52-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="76e52-146">Para redefinir a senha remotamente:</span><span class="sxs-lookup"><span data-stu-id="76e52-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="76e52-147">Do seu computador de administração, na guia de console de administração do Microsoft Intune do navegador, no painel de **Todos os dispositivos gerenciados direta** , clique em seu dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="76e52-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="76e52-148">Na barra de tarefas, clique em **tarefas remotas > redefinição de senha**.</span><span class="sxs-lookup"><span data-stu-id="76e52-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="76e52-p108">Sobre o **tarefa remota: redefinição de senha** solicitar, clique em **Sim**. Aguarde um minuto.</span><span class="sxs-lookup"><span data-stu-id="76e52-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="76e52-151">No painel de **Todos os dispositivos gerenciados direta** , clique em **Exibir propriedades**.</span><span class="sxs-lookup"><span data-stu-id="76e52-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="76e52-152">Em **Redefinição de senha**, observe a nova senha.</span><span class="sxs-lookup"><span data-stu-id="76e52-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="76e52-153">No seu dispositivo Android, insira a nova senha na tela de bloqueio. </span><span class="sxs-lookup"><span data-stu-id="76e52-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="76e52-154">Para alterar a senha novamente, entram em **configurações**, toque em **dispositivo**, toque em **tela de bloqueio**, insira a nova senha novamente, toque em **bloqueio de tela**e sua escolha para a senha.</span><span class="sxs-lookup"><span data-stu-id="76e52-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="76e52-155">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="76e52-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="76e52-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="76e52-156">See Also</span></span>

[<span data-ttu-id="76e52-157">Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="76e52-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="76e52-158">Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="76e52-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="76e52-159">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="76e52-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="76e52-160">Mobilidade corporativos + segurança (EMS)</span><span class="sxs-lookup"><span data-stu-id="76e52-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


