---
title: Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumo: Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.'
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188099"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="2593b-103">Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="2593b-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="2593b-104">**Resumo:** Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.</span><span class="sxs-lookup"><span data-stu-id="2593b-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="2593b-p101">O pacote de mobilidade do Microsoft Enterprise (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="2593b-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="2593b-p102">Se você precisar aplicar segurança no nível do dispositivo, você deve registrar os dispositivos em Microsoft Intune. Registro do dispositivo não apenas ajuda a gerenciar os dispositivos de propriedade da organização, mas também pessoal (BYOD) e dispositivos compartilhados, dependendo da sua organização do legal políticas.</span><span class="sxs-lookup"><span data-stu-id="2593b-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="2593b-109">Seguindo as instruções fornecidas neste artigo, você poderá registrar e testar recursos de gerenciamento de dispositivo móvel básica para dispositivos com Android e iOS em seu ambiente de desenvolvimento e teste da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2593b-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="2593b-110">Fase 1: Crie seu ambiente de desenvolvimento e teste da Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="2593b-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="2593b-111">Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="2593b-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="2593b-112">Fase 2: Registrar seus dispositivos com Android e iOS</span><span class="sxs-lookup"><span data-stu-id="2593b-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="2593b-113">Primeiro, use as instruções em [instalar e acesse o aplicativo de Portal da empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar o aplicativo do Portal do Microsoft Intune empresa para seu locatário de desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="2593b-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="2593b-114">Em seguida, use as instruções em [Configurar o acesso aos seus recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para registrar um dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="2593b-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="2593b-115">Em seguida, use as instruções em [registrar seu dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para registrar um dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="2593b-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="2593b-116">Fase 2: Gerenciar seus dispositivos com Android e iOS remotamente</span><span class="sxs-lookup"><span data-stu-id="2593b-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="2593b-p103">O Microsoft Intune fornece recursos de bloqueio e redefinição de senha remotos. Se alguém perder um dispositivo, você poderá bloqueá-lo remotamente. Se alguém se esquecer da senha, você poderá removê-la remotamente.</span><span class="sxs-lookup"><span data-stu-id="2593b-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="2593b-120">Para bloquear um dispositivo iOS remotamente:</span><span class="sxs-lookup"><span data-stu-id="2593b-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="2593b-121">Abra uma nova guia e vá para http://manage.microsoft.com (se necessário).</span><span class="sxs-lookup"><span data-stu-id="2593b-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="2593b-122">No console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="2593b-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="2593b-123">No painel **Grupos**, abra **Todos os dispositivos > Todos os dispositivos móveis > Todos os Dispositivos Gerenciados Diretamente**.</span><span class="sxs-lookup"><span data-stu-id="2593b-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="2593b-124">No painel **Todos os Dispositivos Gerenciados Diretamente**, clique na guia **Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="2593b-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="2593b-125">Na lista de dispositivos, clique no seu dispositivo iOS. </span><span class="sxs-lookup"><span data-stu-id="2593b-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="2593b-126">No seu dispositivo iOS, certifique-se de que ele esteja na tela principal. </span><span class="sxs-lookup"><span data-stu-id="2593b-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="2593b-p104">No computador de administração, na barra de tarefas, clique em **Tarefas Remotas > Bloqueio Remoto**. Observe seu dispositivo iOS entrando na tela de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2593b-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="2593b-129">Para remover a senha:</span><span class="sxs-lookup"><span data-stu-id="2593b-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="2593b-130">No computador de administração, no painel **Todos os Dispositivos Gerenciados Diretamente**, clique na guia **Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="2593b-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="2593b-p105">Na lista, clique no seu dispositivo iOS. Na barra de tarefas, clique em **Tarefas Remotas > Reconfiguração de Senha**. Aguarde um minuto.</span><span class="sxs-lookup"><span data-stu-id="2593b-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="2593b-p106">No seu dispositivo iOS, desbloqueie-o e observe que uma senha não existe mais. Para alterar novamente a senha, vá para **Configurações** e depois para **Senha**.</span><span class="sxs-lookup"><span data-stu-id="2593b-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="2593b-136">Para bloquear um dispositivo Android remotamente:</span><span class="sxs-lookup"><span data-stu-id="2593b-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="2593b-137">No console de administração do Microsoft Intune do navegador, clique em **grupos** , no painel de navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="2593b-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="2593b-138">No painel **Grupos**, abra **Todos os dispositivos > Todos os dispositivos móveis > Todos os Dispositivos Gerenciados Diretamente**.</span><span class="sxs-lookup"><span data-stu-id="2593b-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="2593b-139">No painel **Todos os Dispositivos Gerenciados Diretamente**, clique na guia **Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="2593b-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="2593b-140">Na lista de dispositivos, clique no seu dispositivo Android. </span><span class="sxs-lookup"><span data-stu-id="2593b-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="2593b-141">No seu dispositivo Android, certifique-se de que ele esteja na tela principal. </span><span class="sxs-lookup"><span data-stu-id="2593b-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="2593b-p107">No computador de administração, na barra de tarefas, clique em **Tarefas Remotas > Bloqueio Remoto**. Quando solicitado, clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="2593b-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="2593b-144">Observe seu dispositivo Android entrando na tela de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2593b-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="2593b-145">Quando você redefinir a senha para dispositivos com Android, o portal de administração Intune gera e configura uma senha forte.</span><span class="sxs-lookup"><span data-stu-id="2593b-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="2593b-146">Para redefinir a senha remotamente:</span><span class="sxs-lookup"><span data-stu-id="2593b-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="2593b-147">No computador de administração, na guia do console de administração do Microsoft Intune do navegador, no painel **Todos os Dispositivos Gerenciados Diretamente**, clique no seu dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="2593b-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="2593b-148">Na barra de tarefas, clique em **Tarefas Remotas > Reconfiguração de Senha**.</span><span class="sxs-lookup"><span data-stu-id="2593b-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="2593b-p108">No prompt **Tarefa Remota: Reconfiguração de Senha**, clique em **Sim**. Aguarde um minuto.</span><span class="sxs-lookup"><span data-stu-id="2593b-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="2593b-151">No painel **Todos os Dispositivos Gerenciados Diretamente**, clique em **Exibir Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="2593b-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="2593b-152">Em **Reconfiguração de Senha**, anote a nova senha.</span><span class="sxs-lookup"><span data-stu-id="2593b-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="2593b-153">No seu dispositivo Android, insira a nova senha na tela de bloqueio. </span><span class="sxs-lookup"><span data-stu-id="2593b-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="2593b-154">Para alterar novamente a senha, vá para **Configurações**, toque em **Dispositivo**, toque em **Tela de bloqueio**, insira novamente a nova senha, toque em **Bloqueio da tela** e depois na sua opção de senha.</span><span class="sxs-lookup"><span data-stu-id="2593b-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="2593b-155">Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="2593b-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2593b-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="2593b-156">See Also</span></span>

[<span data-ttu-id="2593b-157">Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="2593b-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="2593b-158">Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="2593b-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="2593b-159">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="2593b-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="2593b-160">Mobilidade corporativos + segurança (EMS)</span><span class="sxs-lookup"><span data-stu-id="2593b-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


