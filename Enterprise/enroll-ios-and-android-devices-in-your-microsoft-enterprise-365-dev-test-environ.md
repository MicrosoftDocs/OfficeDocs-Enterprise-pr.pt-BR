---
title: Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 'Resumo: Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720407"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="d58ee-103">Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="d58ee-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="d58ee-104">**Resumo:** Use este guia de laboratório de teste para registrar os dispositivos em seu ambiente de desenvolvimento e teste da Microsoft 365 e gerenciá-los remotamente.</span><span class="sxs-lookup"><span data-stu-id="d58ee-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="d58ee-p101">O pacote de mobilidade do Microsoft Enterprise (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="d58ee-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="d58ee-p102">Se você precisar aplicar segurança no nível do dispositivo, você deve registrar os dispositivos em Microsoft Intune. Registro do dispositivo não apenas ajuda a gerenciar os dispositivos de propriedade da organização, mas também pessoal (BYOD) e dispositivos compartilhados, dependendo da sua organização do legal políticas.</span><span class="sxs-lookup"><span data-stu-id="d58ee-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="d58ee-109">Seguindo as instruções fornecidas neste artigo, você poderá registrar e testar recursos de gerenciamento de dispositivo móvel básica para dispositivos com Android e iOS em seu ambiente de desenvolvimento e teste da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d58ee-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="d58ee-110">Fase 1: Crie seu ambiente de desenvolvimento e teste da Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d58ee-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="d58ee-111">Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d58ee-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="d58ee-112">Fase 2: Registrar seus dispositivos com Android e iOS</span><span class="sxs-lookup"><span data-stu-id="d58ee-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="d58ee-113">Primeiro, use as instruções em [instalar e acesse o aplicativo de Portal da empresa](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) para personalizar o aplicativo Microsoft Intune Portal da empresa para o seu ambiente de teste.</span><span class="sxs-lookup"><span data-stu-id="d58ee-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="d58ee-114">Em seguida, use as instruções em [Configurar o acesso aos seus recursos de empresa](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) para registrar um dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="d58ee-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="d58ee-115">Em seguida, use as instruções em [registrar seu dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) para registrar um dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="d58ee-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="d58ee-116">Fase 3: Gerenciar seus dispositivos com Android e iOS remotamente</span><span class="sxs-lookup"><span data-stu-id="d58ee-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="d58ee-p103">Microsoft Intune fornece recursos de redefinição de bloqueio remoto e uma senha. Se alguém perder seus dispositivos, você pode bloquear o dispositivo remotamente. Se alguém esquecer sua senha, é possível redefini-lo remotamente.</span><span class="sxs-lookup"><span data-stu-id="d58ee-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="d58ee-120">Para bloquear um dispositivo Android ou o iOS remotamente:</span><span class="sxs-lookup"><span data-stu-id="d58ee-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="d58ee-121">Entrar no portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com) com as credenciais da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="d58ee-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="d58ee-122">Clique em **todos os serviços**, digite **Intune**e clique em **Intune**.</span><span class="sxs-lookup"><span data-stu-id="d58ee-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="d58ee-123">Clique em **dispositivos > todos os dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="d58ee-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="d58ee-124">Na lista de dispositivos, clique em um iOS ou um dispositivo Android e, em seguida, clique na ação de **bloqueio remoto** .</span><span class="sxs-lookup"><span data-stu-id="d58ee-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="d58ee-125">Para redefinir a senha remotamente:</span><span class="sxs-lookup"><span data-stu-id="d58ee-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="d58ee-126">Se necessário, entrar no portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com) com as credenciais da sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="d58ee-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="d58ee-127">Clique em **todos os serviços**, digite **Intune**e clique em **Intune**.</span><span class="sxs-lookup"><span data-stu-id="d58ee-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="d58ee-128">Clique em **dispositivos > todos os dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="d58ee-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="d58ee-p104">Da lista de dispositivos você gerenciar, clique em um iOS ou um dispositivo Android e escolha **… Mais**. Escolha a ação remota dispositivo **Remover a senha** .</span><span class="sxs-lookup"><span data-stu-id="d58ee-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="d58ee-131">Experimentação adicionais, consulte [ações de dispositivo disponível](https://docs.microsoft.com/intune/device-management#available-device-actions).</span><span class="sxs-lookup"><span data-stu-id="d58ee-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="d58ee-132">Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="d58ee-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d58ee-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="d58ee-133">See Also</span></span>

[<span data-ttu-id="d58ee-134">Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="d58ee-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="d58ee-135">Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="d58ee-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="d58ee-136">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="d58ee-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="d58ee-137">Mobilidade corporativos + segurança (EMS)</span><span class="sxs-lookup"><span data-stu-id="d58ee-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


