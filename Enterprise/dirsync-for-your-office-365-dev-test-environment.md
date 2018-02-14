---
title: DirSync para seu ambiente de desenvolvimento e teste do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "Resumo: Configure a sincronização de diretórios para o seu ambiente de desenvolvimento e teste do Office 365."
ms.openlocfilehash: 8a656ea742af642a8b4dc3e096764f0e8cbde074
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a><span data-ttu-id="0af2f-103">DirSync para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0af2f-103">DirSync for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="0af2f-104">**Resumo:** Configure a sincronização de diretório para o seu ambiente de desenvolvimento e teste do Office 365.</span><span class="sxs-lookup"><span data-stu-id="0af2f-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="0af2f-p101">Muitas organizações uso Connect do Azure AD e sincronização de diretório (DirSync) para sincronizar o conjunto de contas em sua floresta do Windows Server Active Directory (AD) de local para o conjunto de contas no Office 365. Este artigo descreve como você pode adicionar DirSync com sincronização de senha para o ambiente de desenvolvimento e teste do Office 365, resultando na configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="0af2f-p101">Many organizations use Azure AD Connect and directory synchronization (DirSync) to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add DirSync with password synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![O ambiente de desenvolvimento e teste do Office 365 com o DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="0af2f-108">Esta configuração consiste em:</span><span class="sxs-lookup"><span data-stu-id="0af2f-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="0af2f-109">Um Office 365 E5 avaliação assinatura, que expira 30 dias a partir de quando você criá-lo.</span><span class="sxs-lookup"><span data-stu-id="0af2f-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="0af2f-p102">Uma intranet da organização simplificado conectado à Internet, consistindo em três máquinas virtuais em uma sub-rede de uma rede virtual do Azure (DC1, APP1 e CLIENT1). Conectar do Azure AD executa no APP1 para sincronizar o domínio do Windows Server AD para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="0af2f-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="0af2f-112">Há duas fases para configurar esse ambiente de desenvolvimento e teste:</span><span class="sxs-lookup"><span data-stu-id="0af2f-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="0af2f-113">Crie o ambiente de desenvolvimento e teste do Office 365 (os DC1, APP1 e CLIENT1 máquinas virtuais em uma rede virtual do Azure com uma assinatura de avaliação do Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="0af2f-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
    
2. <span data-ttu-id="0af2f-114">Instalar e configurar o Azure Connect do AD no APP1.</span><span class="sxs-lookup"><span data-stu-id="0af2f-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="0af2f-115">Clique [aqui](http://aka.ms/catlgstack) para obter um mapa visual para todos os artigos na pilha de um Microsoft Cloud Test Lab Guide.</span><span class="sxs-lookup"><span data-stu-id="0af2f-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="0af2f-116">Fase 1: Criar um ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0af2f-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="0af2f-p103">Siga as instruções em fases 1, 2 e 3 do artigo [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md) . Aqui está a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="0af2f-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![O ambiente de desenvolvimento e teste do Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="0af2f-120">Esta configuração consiste em:</span><span class="sxs-lookup"><span data-stu-id="0af2f-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="0af2f-121">Uma assinatura de avaliação do E5 do Office 365.</span><span class="sxs-lookup"><span data-stu-id="0af2f-121">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="0af2f-122">Uma intranet da organização simplificado conectado à Internet, consistindo das máquinas virtuais DC1, APP1 e CLIENT1 em uma sub-rede de uma rede virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="0af2f-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="0af2f-123">Fase 2: Instalar o Azure AD conectar no APP1</span><span class="sxs-lookup"><span data-stu-id="0af2f-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="0af2f-p104">Depois de instalado e configurado, Connect do Azure AD sincroniza o conjunto de contas no domínio CORP Windows Server AD com o conjunto de contas em sua assinatura de avaliação do Office 365. O procedimento a seguir orienta você na instalação Connect do Azure AD no APP1 e verificando se ela funciona.</span><span class="sxs-lookup"><span data-stu-id="0af2f-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="0af2f-126">Instalar e configurar o Azure Connect do AD no APP1</span><span class="sxs-lookup"><span data-stu-id="0af2f-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="0af2f-127">No [portal do Azure](https://portal.azure.com), conecte-se App1 com CORP\\conta User1.</span><span class="sxs-lookup"><span data-stu-id="0af2f-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="0af2f-128">No APP1, abra um prompt de comando do Windows PowerShell de nível de administrador e, em seguida, execute estes comandos:</span><span class="sxs-lookup"><span data-stu-id="0af2f-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="0af2f-129">Na barra de tarefas, clique em **Internet Explorer** e vá para [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="0af2f-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="0af2f-130">Na página Microsoft Azure Active Directory Connect, clique em **Download**e, em seguida, clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="0af2f-131">Na página **Bem-vindo ao conectar do Azure AD** , clique em **Concordo**e clique em **continuar**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="0af2f-132">Na página **Configurações Express** , clique em **usar configurações express**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="0af2f-133">Na página **conectar ao AD do Windows Azure** , digite o nome da sua conta de administrador global no tipo de **nome de usuário,** sua senha na **senha**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="0af2f-134">Na página **conectar ao AD DS** , digite **CORP\\User1** em **nome de usuário,** digite sua senha em **senha**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="0af2f-135">Na página **configuração de entrada do Azure AD** , clique em **continuar sem qualquer domínio verificado**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="0af2f-136">Na página **pronto para configurar** , clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="0af2f-137">Na página **configuração concluída** , clique em **Sair**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="0af2f-138">No Internet Explorer, vá para o portal do Office 365 ([https://portal.office.com](https://portal.office.com)) e entrar em sua assinatura de avaliação do Office 365 com sua conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="0af2f-138">In Internet Explorer, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="0af2f-139">Na página principal do portal, clique em **Admin**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="0af2f-140">Na navegação à esquerda, clique em **Usuários > Usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="0af2f-p105">Observe a conta denominada **User1**. Esta conta é do domínio CORP Windows Server AD e prova DirSync funcionou.</span><span class="sxs-lookup"><span data-stu-id="0af2f-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that DirSync has worked.</span></span>
    
15. <span data-ttu-id="0af2f-p106">Clique na conta **User1** . Para licenças de produto, clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="0af2f-p107">Em **licenças do produto**, selecione seu país e clique em controle **desativado** para **Office 365 Enterprise E5** (alternando para **ativado**). Clique em **Salvar** na parte inferior da página e, em seguida, clique em **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="0af2f-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="0af2f-147">Essa é a configuração resultante.</span><span class="sxs-lookup"><span data-stu-id="0af2f-147">This is the resulting configuration.</span></span>
  
![O ambiente de desenvolvimento e teste do Office 365 com o DirSync](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="0af2f-149">Esta configuração consiste em:</span><span class="sxs-lookup"><span data-stu-id="0af2f-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="0af2f-150">Uma assinatura de avaliação do E5 do Office 365.</span><span class="sxs-lookup"><span data-stu-id="0af2f-150">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="0af2f-p108">Uma intranet da organização simplificado conectado à Internet, consistindo das máquinas virtuais DC1, APP1 e CLIENT1 em uma sub-rede de uma rede virtual do Azure. Conectar do Azure AD executa no APP1 para sincronizar o domínio CORP Windows Server AD para o Office 365 a cada 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="0af2f-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="0af2f-153">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="0af2f-153">Next Step</span></span>

<span data-ttu-id="0af2f-154">Quando estiver pronto para implantar o DirSync para sua organização, consulte [Implantar o Office 365 sincronização de diretórios (DirSync) no Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="0af2f-154">When you are ready to deploy DirSync for your organization, see [Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0af2f-155">Veja também</span><span class="sxs-lookup"><span data-stu-id="0af2f-155">See Also</span></span>

[<span data-ttu-id="0af2f-156">Guias do Laboratório de Teste (TLGs) para adoção de nuvem</span><span class="sxs-lookup"><span data-stu-id="0af2f-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="0af2f-157">Ambiente de desenvolvimento e teste de configuração de base</span><span class="sxs-lookup"><span data-stu-id="0af2f-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="0af2f-158">Ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0af2f-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="0af2f-159">Segurança de aplicativo de nuvem para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0af2f-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="0af2f-160">Proteção de ameaça avançada para seu ambiente de desenvolvimento e teste do Office 365</span><span class="sxs-lookup"><span data-stu-id="0af2f-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="0af2f-161">Adoção da nuvem e soluções híbridas</span><span class="sxs-lookup"><span data-stu-id="0af2f-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




