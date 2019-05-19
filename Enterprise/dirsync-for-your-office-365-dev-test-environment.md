---
title: Sincronização de diretório do ambiente de desenvolvimento/teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: 'Resumo: Configure a sincronização de diretórios do ambiente de desenvolvimento/teste do Office 365.'
ms.openlocfilehash: c1596b12ab3c6c8feda3063134cc53a5f18919af
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162424"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="9029d-103">Sincronização de diretório do ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="9029d-103">Directory synchronization for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="9029d-104">**Resumo:** Configure a sincronização de diretórios do ambiente de desenvolvimento/teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9029d-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="9029d-p101">Muitas organizações usam o Azure AD Connect e a sincronização de diretório para sincronizar o conjunto de contas em sua floresta local do AD DS (Active Directory Domain Services) com o conjunto de contas no Office 365. Este artigo descreve como você pode adicionar a sincronização de diretório com a sincronização de hash de senha para o ambiente de desenvolvimento/de teste do Office 365, resultando na seguinte configuração.</span><span class="sxs-lookup"><span data-stu-id="9029d-p101">Many organizations use Azure AD Connect and directory synchronization to synchronize the set of accounts in their on-premises Active Directory Domain Services (AD DS) forest to the set of accounts in Office 365. This article describes how you can add directory synchronization with password hash synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![Ambiente de desenvolvimento/de teste do Office 365 com a sincronização de diretório](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="9029d-108">Esta configuração consiste em:</span><span class="sxs-lookup"><span data-stu-id="9029d-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="9029d-109">Uma assinatura de avaliação do Office 365 E5, que expira 30 dias depois de você criá-la.</span><span class="sxs-lookup"><span data-stu-id="9029d-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="9029d-p102">Uma intranet de organização simplificada conectada à Internet, que consiste em três máquinas virtuais em uma sub-rede de uma rede virtual do Azure (DC1 APP1 e CLIENT1). O Azure AD Connect é executado no APP1 para sincronizar o domínio do AD DS com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="9029d-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the AD DS domain to Office 365.</span></span>
    
<span data-ttu-id="9029d-112">Há duas fases para configurar esse ambiente de desenvolvimento/ de teste:</span><span class="sxs-lookup"><span data-stu-id="9029d-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="9029d-113">Crie um ambiente de desenvolvimento/de teste do Office 365 (as máquinas virtuais do DC1, APP1 e CLIENT1 em uma rede virtual do Azure com uma assinatura de avaliação do Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="9029d-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="9029d-114">Instale e configure o Azure AD Connect no APP1.</span><span class="sxs-lookup"><span data-stu-id="9029d-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="9029d-115">Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual de todos os artigos da pilha da Guia do Laboratório de Teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9029d-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="9029d-116">Fase 1: Criar um ambiente de desenvolvimento/de teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="9029d-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="9029d-p103">Siga as instruções nas fases 1, 2 e 3 do artigo [Ambiente de desenvolvimento/de teste do Office 365](office-365-dev-test-environment.md). Aqui está a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="9029d-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![O ambiente de desenvolvimento/teste do Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="9029d-120">Esta configuração consiste em:</span><span class="sxs-lookup"><span data-stu-id="9029d-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="9029d-121">Uma assinatura de avaliação do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="9029d-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="9029d-122">Uma intranet de organização simplificada conectado à Internet, que consiste em máquinas virtuais do DC1 APP1 e CLIENT1 em uma sub-rede de uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="9029d-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="9029d-123">Fase 2: Instalar o Azure AD Connect no APP1</span><span class="sxs-lookup"><span data-stu-id="9029d-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="9029d-p104">Depois de instalado e configurado, o Azure AD Connect sincroniza o conjunto de contas no domínio CORP do AD DS com o conjunto de contas de assinatura de avaliação do Office 365. O procedimento a seguir orientará a instalação do Azure AD Connect no APP1 e a confirmação de seu bom funcionamento.</span><span class="sxs-lookup"><span data-stu-id="9029d-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP AD DS domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and checking that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="9029d-126">Instalar e configurar o Azure AD Connect na APP1</span><span class="sxs-lookup"><span data-stu-id="9029d-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="9029d-127">Do [Portal do Azure](https://portal.azure.com), conecte-se ao APP1 com a conta CORP\\Usuário1.</span><span class="sxs-lookup"><span data-stu-id="9029d-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="9029d-128">Do APP1, abra um prompt de comando do nível de administrador do Windows PowerShell e execute estes comandos:</span><span class="sxs-lookup"><span data-stu-id="9029d-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="9029d-129">Na barra de tarefas, clique em **Internet Explorer** e acesse [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="9029d-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="9029d-130">Na página do Microsoft Azure Active Directory Connect, clique em **Baixar** e, em seguida, clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="9029d-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="9029d-131">Na página **Bem-vindo ao Azure AD Connect**, clique em **Concordo** e, em seguida, **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="9029d-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="9029d-132">Na página **Configurações Expressas**, clique em **Usar configurações expressas**.</span><span class="sxs-lookup"><span data-stu-id="9029d-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="9029d-133">Na página **Conectar-se ao Azure AD**, digite o nome de sua conta de administrador global em **Nome de usuário**, digite a sua senha em **Senha** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9029d-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="9029d-134">Na página **Conectar-se ao AD DS**, digite **CORP\\Usuário1** em **Nome de usuário,** digita a senha em **Senha** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9029d-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="9029d-135">Na página **Configuração de entrada do Azure AD**, clique em **Continuar sem domínio verificado** e depois em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="9029d-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="9029d-136">Na página **Pronto para configurar**, clique em **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="9029d-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="9029d-137">Na página **Configuração concluída**, clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="9029d-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="9029d-138">No Internet Explorer, vá ao centro de administração do Office 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) e entre na sua assinatura de avaliação do Office 365 com a sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="9029d-138">In Internet Explorer, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="9029d-139">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="9029d-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="9029d-140">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="9029d-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="9029d-p105">Observe a conta denominada **Usuário1**. Essa conta fica no domínio CORP do AD Ds e é uma prova de que a sincronização de diretórios funcionou.</span><span class="sxs-lookup"><span data-stu-id="9029d-p105">Note the account named **User1**. This account is from the CORP AD DS domain and is proof that directory synchronization has worked.</span></span>
    
15. <span data-ttu-id="9029d-p106">Clique na conta **Usuário1**. Para licenças de produto, clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="9029d-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="9029d-p107">Em **Licenças de produto**, selecione o seu país/região e, em seguida, clique no controle **Desativado** para **Office 365 Enterprise E5** (mudando-o para **Ativado**). Clique em **Salvar** na parte inferior da página e clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="9029d-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="9029d-147">Esta é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="9029d-147">This is the resulting configuration.</span></span>
  
![Ambiente de desenvolvimento/de teste do Office 365 com a sincronização de diretório](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="9029d-149">Esta configuração consiste em:</span><span class="sxs-lookup"><span data-stu-id="9029d-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="9029d-150">Uma assinatura de avaliação do Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="9029d-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="9029d-p108">Uma intranet de organização simplificada conectada à Internet, que consiste nas máquinas virtuais DC1, APP1 e CLIENT1 em uma sub-rede de uma rede virtual do Azure. O Azure AD Connect é executado no APP1 para sincronizar o domínio CORP do AD DS com o Office 365 a cada 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="9029d-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP AD DS domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="9029d-153">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="9029d-153">Next Step</span></span>

<span data-ttu-id="9029d-154">Quando estiver pronto para implantar a sincronização de diretórios da sua organização, confira [Implantar sincronização de diretórios do Office 365 no Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="9029d-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9029d-155">Confira também
</span><span class="sxs-lookup"><span data-stu-id="9029d-155">See Also</span></span>

[<span data-ttu-id="9029d-156">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="9029d-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

<span data-ttu-id="9029d-157">[O ambiente de desenvolvimento/teste de configuração base](base-configuration-dev-test-environment.md) </span><span class="sxs-lookup"><span data-stu-id="9029d-157">[Base Configuration dev/test environment](base-configuration-dev-test-environment.md)</span></span>

[<span data-ttu-id="9029d-158">Ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="9029d-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)

[<span data-ttu-id="9029d-159">Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento/teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="9029d-159">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="9029d-160">Adoção da nuvem e de soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="9029d-160">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




