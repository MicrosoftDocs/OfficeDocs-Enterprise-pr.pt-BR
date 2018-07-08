---
title: Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 'Resumo: Use este guia de laboratório de teste para adicionar políticas de gerenciamento (MAM) de aplicativo móvel do EMS ao seu ambiente de desenvolvimento e teste da Microsoft 365.'
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188149"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="0354f-103">Políticas MAM para o ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="0354f-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="0354f-104">**Resumo:** Use este guia de laboratório de teste para adicionar políticas de gerenciamento (MAM) de aplicativo móvel do EMS ao seu ambiente de desenvolvimento e teste da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0354f-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="0354f-p101">O Microsoft Enterprise mobilidade + segurança (EMS) ajuda a manter seus funcionários produtivos utilizando seus aplicativos favoritos e dispositivos enquanto protege os dados da sua organização. Para obter mais informações, consulte [Enterprise mobilidade + segurança (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span><span class="sxs-lookup"><span data-stu-id="0354f-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="0354f-107">Com as instruções deste artigo, você pode adicionar políticas de gerenciamento (MAM) do aplicativo móvel ao seu ambiente de desenvolvimento e teste da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0354f-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="0354f-108">Fase 1: Criar o seu ambiente de desenvolvimento e teste da Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0354f-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="0354f-109">Siga as instruções no [ambiente de desenvolvimento e teste o Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="0354f-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="0354f-110">Fase 2: Criar e implantar políticas de MAM para dispositivos iOS e Android</span><span class="sxs-lookup"><span data-stu-id="0354f-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="0354f-111">Nesta fase, você criará e implantará duas políticas de MAM diferentes: uma para dispositivos iOS e outra para dispositivos Android.</span><span class="sxs-lookup"><span data-stu-id="0354f-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="0354f-112">Vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e se conectar à sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="0354f-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="0354f-113">Em uma nova guia do navegador, abra o portal do Windows Azure ([https://azure.portal.com](https://azure.portal.com)) e entrar usando sua conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="0354f-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="0354f-114">Na guia Azure portal no Internet Explorer, no painel de navegação, clique em **todos os serviços**, digite **Intune**e, em seguida, clique em **Intune**.</span><span class="sxs-lookup"><span data-stu-id="0354f-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **All services**, type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="0354f-115">No painel de navegação à esquerda, clique em **Grupos**.</span><span class="sxs-lookup"><span data-stu-id="0354f-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="0354f-116">No blade **grupos-All grupos** , clique em **+ novo grupo**.</span><span class="sxs-lookup"><span data-stu-id="0354f-116">On the **Groups-All groups** blade, click **+ New Group**.</span></span>
    
6. <span data-ttu-id="0354f-117">No **grupo** blade, selecione **Office 365** para **tipo de grupo?**, digite **gerenciados iOS usuários de dispositivo** em **nome**, selecione **atribuído** no **tipo de associação**e, em seguida, clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-117">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span> 
    
7. <span data-ttu-id="0354f-118">Feche a folha **Grupo**.</span><span class="sxs-lookup"><span data-stu-id="0354f-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="0354f-119">No blade **grupos-All grupos** , clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-119">On the **Groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="0354f-120">No **grupo** blade, selecione **Office 365** para **tipo de grupo?**, digite **gerenciados Android usuário de dispositivo** em **nome**, selecione **atribuído** no **tipo de associação**e, em seguida, clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-120">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed Android device user** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span>
    
10. <span data-ttu-id="0354f-121">Feche o blade **grupos grupos a todos** .</span><span class="sxs-lookup"><span data-stu-id="0354f-121">Close the **Groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="0354f-122">Na folha **Intune**, na lista **Tarefas rápidas**, clique em **Crie uma política de conformidade**.</span><span class="sxs-lookup"><span data-stu-id="0354f-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="0354f-123">Na folha **Perfis de Políticas de Conformidade**, clique em **Criar Política**.</span><span class="sxs-lookup"><span data-stu-id="0354f-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="0354f-p102">Na folha **Criar Política**, em **Nome**, digite **iOS**. Em **Plataforma**, selecione **iOS**, clique em **OK** na folha **Política de conformidade do iOS** e depois clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="0354f-126">Na folha **Perfis de Políticas de Conformidade**, clique em **Criar Política**.</span><span class="sxs-lookup"><span data-stu-id="0354f-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="0354f-p103">Na folha **Criar Política**, em **Nome**, digite **Android**. Em **Plataforma**, selecione **Android**, clique em **OK** na folha **Política de conformidade do Android** e depois clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="0354f-129">Na folha **Perfis de Políticas de Conformidade**, clique no nome da política **Android**.</span><span class="sxs-lookup"><span data-stu-id="0354f-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="0354f-130">Na navegação à esquerda da folha **Android - Propriedades**, clique em **Atribuições** e depois em **Grupos selecionados**.</span><span class="sxs-lookup"><span data-stu-id="0354f-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="0354f-131">Na folha **Grupos selecionados**, clique no grupo **Usuários de dispositivos Android gerenciados** e depois clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="0354f-132">Clique em **Salvar**e feche o blade **Android - atribuições** .</span><span class="sxs-lookup"><span data-stu-id="0354f-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="0354f-133">Na folha **Perfis de Políticas de Conformidade**, clique no nome da política **iOS**.</span><span class="sxs-lookup"><span data-stu-id="0354f-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="0354f-134">Na navegação à esquerda da folha **iOS - Propriedades**, clique em **Atribuições** e depois em **Grupos selecionados**.</span><span class="sxs-lookup"><span data-stu-id="0354f-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="0354f-135">Na folha **Grupos selecionados**, clique no grupo **Usuários de dispositivos iOS gerenciados** e depois clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="0354f-136">Clique em **Salvar**e feche o blade **iOS - atribuições** .</span><span class="sxs-lookup"><span data-stu-id="0354f-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="0354f-137">Feche a folha **Perfis de Políticas de Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="0354f-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="0354f-138">Na folha **Intune**, clique em **Gerenciar aplicativos** na navegação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="0354f-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="0354f-139">Na folha **Aplicativos Móveis**, clique em **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="0354f-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="0354f-140">Na lista de aplicativos, clique em **PowerPoint**, </span><span class="sxs-lookup"><span data-stu-id="0354f-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="0354f-p104">Na folha **Visão Geral do PowerPoint**, clique em **Atribuições > Selecionar grupos > Dispositivos iOS gerenciados > Selecionar**. Em **Tipo**, selecione **Disponível** e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="0354f-143">Repita a etapa 28 para os seguintes aplicativos:</span><span class="sxs-lookup"><span data-stu-id="0354f-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="0354f-144">Outlook para Android</span><span class="sxs-lookup"><span data-stu-id="0354f-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="0354f-145">Word para iOS</span><span class="sxs-lookup"><span data-stu-id="0354f-145">Word for iOS</span></span>
    
  - <span data-ttu-id="0354f-146">Excel para iOS</span><span class="sxs-lookup"><span data-stu-id="0354f-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="0354f-147">Outlook para iOS</span><span class="sxs-lookup"><span data-stu-id="0354f-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="0354f-148">Microsoft Dynamics CRM no iPad para iOS</span><span class="sxs-lookup"><span data-stu-id="0354f-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="0354f-149">Microsoft Dynamics CRM no iPhone para iOS</span><span class="sxs-lookup"><span data-stu-id="0354f-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="0354f-150">Dynamics CRM para Telefones para Android</span><span class="sxs-lookup"><span data-stu-id="0354f-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="0354f-151">Dynamics CRM para Tablets para Android</span><span class="sxs-lookup"><span data-stu-id="0354f-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="0354f-152">Excel para Android</span><span class="sxs-lookup"><span data-stu-id="0354f-152">Excel for Android</span></span>
    
  - <span data-ttu-id="0354f-153">Word para Android</span><span class="sxs-lookup"><span data-stu-id="0354f-153">Word for Android</span></span>
    
  - <span data-ttu-id="0354f-154">OneNote para iOS</span><span class="sxs-lookup"><span data-stu-id="0354f-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="0354f-155">Feche a folha **Aplicativos Móveis - Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="0354f-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="0354f-156">Na folha **Aplicativos Móveis**, clique em **Políticas de Proteção de Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="0354f-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="0354f-157">Na folha **Políticas de Proteção de Aplicativo**, clique em **Adicionar uma política**.</span><span class="sxs-lookup"><span data-stu-id="0354f-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="0354f-158">Na folha **Adicionar uma política**, digite **iOS** e clique em **Selecionar aplicativos necessários**.</span><span class="sxs-lookup"><span data-stu-id="0354f-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="0354f-159">Na folha **Aplicativos**, clique em **PowerPoint**, **Microsoft Dynamics CRM no iPhone**, **Excel**, **Microsoft Dynamics CRM no iPhone**, **Word**, **OneNote** e **Outlook** e depois clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="0354f-160">Na folha **Adicionar uma política**, clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="0354f-161">Na folha **Políticas de Proteção de Aplicativo**, clique em **Adicionar uma política**.</span><span class="sxs-lookup"><span data-stu-id="0354f-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="0354f-162">Na folha **Adicionar uma política**, digite **Android**, selecione **Android** em **Plataforma** e clique em **Selecionar aplicativos necessários**.</span><span class="sxs-lookup"><span data-stu-id="0354f-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="0354f-163">Na folha **Aplicativos**, clique em **PowerPoint**, **Dynamics CRM para tablets**, **Excel**, **Word**, **Outlook** e **Dynamics CRM para telefones**. Em seguida, clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="0354f-164">Na folha **Adicionar uma política**, clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="0354f-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="0354f-165">Agora, você tem duas políticas de MAM, uma para dispositivos iOS e outra para dispositivos Android, e está pronto para trabalhar com configurações de teste para os aplicativos selecionados.</span><span class="sxs-lookup"><span data-stu-id="0354f-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="0354f-166">Clique [aqui](http://aka.ms/catlgstack) para acessar um mapa visual de todos os artigos da pilha do Guia do Laboratório de Teste do One Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="0354f-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0354f-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="0354f-167">See Also</span></span>

[<span data-ttu-id="0354f-168">Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="0354f-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="0354f-169">Registre dispositivos iOS e Android em seu ambiente de desenvolvimento/teste do Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="0354f-169">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="0354f-170">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="0354f-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="0354f-171">Mobilidade corporativos + segurança (EMS)</span><span class="sxs-lookup"><span data-stu-id="0354f-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


