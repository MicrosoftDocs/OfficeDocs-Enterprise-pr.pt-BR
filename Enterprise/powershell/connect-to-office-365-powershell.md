---
title: Conectar-se ao PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumo: Conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para executar tarefas da central de administração a partir da linha de comando.'
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639772"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="513d9-103">Conectar-se ao PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="513d9-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="513d9-104">**Resumo:** Conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para executar tarefas de administração a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="513d9-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="513d9-105">O Office 365 PowerShell permite que você gerencie suas configurações do Office 365 a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="513d9-105">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="513d9-106">Conectar-se ao Office 365 PowerShell é um processo simples onde você instala o software necessário e, em seguida, conecta-se à sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="513d9-106">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="513d9-107">Há duas versões do módulo do PowerShell que você usa para se conectar ao Office 365 e administrar contas de usuário, grupos e licenças:</span><span class="sxs-lookup"><span data-stu-id="513d9-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="513d9-108">PowerShell do Azure Active Directory para Graph (os cmdlets incluem **AzureAD** em seu nome)</span><span class="sxs-lookup"><span data-stu-id="513d9-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="513d9-109">Módulo do Microsoft Azure Active Directory para Windows PowerShell (os cmdlets incluem **MSol** em seu nome)</span><span class="sxs-lookup"><span data-stu-id="513d9-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="513d9-110">A partir da data deste artigo, o módulo PowerShell do Azure Active Directory para Graph não substitui completamente a funcionalidade nos cmdlets do módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell para administração de usuários, grupos e licenças .</span><span class="sxs-lookup"><span data-stu-id="513d9-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="513d9-111">Em muitos casos, você precisa usar ambas as versões.</span><span class="sxs-lookup"><span data-stu-id="513d9-111">In many cases, you need to use both versions.</span></span> <span data-ttu-id="513d9-112">Você pode instalar com segurança ambas as versões no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="513d9-112">You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="513d9-p103">\*\*Novo no PowerShell? \*\* Veja um [vídeo de visão geral do PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), apresentado pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="513d9-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="513d9-115">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="513d9-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="513d9-116">Tempo estimado para conclusão: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="513d9-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="513d9-117">Você pode usar as seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="513d9-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="513d9-118">Windows 10, Windows 8,1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="513d9-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="513d9-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="513d9-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="513d9-p104">Use uma versão de 64 bits do Windows, pois o suporte para a versão de 32 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell foi descontinuada em outubro de 2014.</span><span class="sxs-lookup"><span data-stu-id="513d9-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="513d9-122">Esses procedimentos se destinam a usuários que são membros de uma função de administrador do Office 365.</span><span class="sxs-lookup"><span data-stu-id="513d9-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="513d9-123">Para saber mais, veja [Sobre as funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="513d9-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="513d9-124">Conectar-se ao Azure Active Directory PowerShell para o módulo do Graph</span><span class="sxs-lookup"><span data-stu-id="513d9-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="513d9-125">Os comandos no módulo do [PowerShell do Azure Active Directory para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) têm **AzureAD** em seu nome de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="513d9-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="513d9-126">Para procedimentos que exigem os novos cmdlets no módulo PowerShell do Azure Active Directory para Graph, use estas etapas para instalar o módulo e se conectar à sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="513d9-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="513d9-127">Confira [Azure Active Directory PowerShell for Graph Module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obter informações sobre o suporte para diferentes versões do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="513d9-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="513d9-128">Etapa 1: Instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="513d9-128">Step 1: Install required software</span></span>

<span data-ttu-id="513d9-p106">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="513d9-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="513d9-131">Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="513d9-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="513d9-132">Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="513d9-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="513d9-133">Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="513d9-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="513d9-134">Etapa 2: conectar-se ao Azure AD para sua assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="513d9-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="513d9-135">Para se conectar ao Azure AD para sua assinatura do Office 365 com um nome de conta e senha ou com a *autenticação multifator (MFA)*, execute um destes comandos a partir de um prompt de comando do Windows PowerShell (ele não precisa ser elevado).</span><span class="sxs-lookup"><span data-stu-id="513d9-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="513d9-136">**Nuvem do Office 365**</span><span class="sxs-lookup"><span data-stu-id="513d9-136">**Office 365 cloud**</span></span> | <span data-ttu-id="513d9-137">**Command**</span><span class="sxs-lookup"><span data-stu-id="513d9-137">**Command**</span></span> |
| <span data-ttu-id="513d9-138">Office 365 em todo o mundo (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="513d9-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="513d9-139">Office 365 operado por 21 vianet</span><span class="sxs-lookup"><span data-stu-id="513d9-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="513d9-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="513d9-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="513d9-141">Office 365 governo dos EUA DoD e Office 365 governo dos EUA</span><span class="sxs-lookup"><span data-stu-id="513d9-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="513d9-142">Na caixa de diálogo **entrar em sua conta** , digite o nome de usuário e a senha da conta corporativa ou de estudante do Office 365 e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="513d9-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="513d9-143">Se você estiver usando a MFA, siga as instruções nas caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.</span><span class="sxs-lookup"><span data-stu-id="513d9-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="513d9-144">Após a conexão, você pode usar os novos cmdlets para o [módulo do PowerShell do Azure Active Directory para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="513d9-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="513d9-145">Conecte com o Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="513d9-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="513d9-146">Os comandos no Módulo Microsoft Azure Active Directory para Windows PowerShell têm **Msol** no nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="513d9-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="513d9-147">Etapa 1: instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="513d9-147">Step 1: Install required software</span></span>

<span data-ttu-id="513d9-p107">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="513d9-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="513d9-150">Instale a versão de 64 bits do Assistente de Conexão do Microsoft Online Services: [Assistente de Conexão do Microsoft Online Services para profissionais de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="513d9-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="513d9-151">Instale o Módulo Microsoft Azure Active Directory para Windows PowerShell seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="513d9-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="513d9-152">Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="513d9-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="513d9-153">Execute o comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="513d9-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="513d9-154">Se solicitado a instalar o provedor de NuGet, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="513d9-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="513d9-155">Se solicitado a instalar o módulo de PSGallery, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="513d9-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="513d9-156">Etapa 2: conectar-se ao Azure AD para sua assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="513d9-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="513d9-157">Para se conectar ao Azure AD para sua assinatura do Office 365 com um nome de conta e senha ou com a *autenticação multifator (MFA)*, execute um destes comandos a partir de um prompt de comando do Windows PowerShell (ele não precisa ser elevado).</span><span class="sxs-lookup"><span data-stu-id="513d9-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="513d9-158">**Nuvem do Office 365**</span><span class="sxs-lookup"><span data-stu-id="513d9-158">**Office 365 cloud**</span></span> | <span data-ttu-id="513d9-159">**Command**</span><span class="sxs-lookup"><span data-stu-id="513d9-159">**Command**</span></span> |
| <span data-ttu-id="513d9-160">Office 365 em todo o mundo (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="513d9-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="513d9-161">Office 365 operado por 21 vianet</span><span class="sxs-lookup"><span data-stu-id="513d9-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="513d9-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="513d9-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="513d9-163">Office 365 governo dos EUA DoD e Office 365 governo dos EUA</span><span class="sxs-lookup"><span data-stu-id="513d9-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="513d9-164">Na caixa de diálogo **entrar em sua conta** , digite o nome de usuário e a senha da conta corporativa ou de estudante do Office 365 e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="513d9-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="513d9-165">Se você estiver usando a MFA, siga as instruções nas caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.</span><span class="sxs-lookup"><span data-stu-id="513d9-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="513d9-166">Como saber se funcionou?</span><span class="sxs-lookup"><span data-stu-id="513d9-166">How do you know this worked?</span></span>

<span data-ttu-id="513d9-p108">Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="513d9-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="513d9-169">Caso você receba erros, verifique os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="513d9-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="513d9-170">**Um problema comum é uma senha incorreta**.</span><span class="sxs-lookup"><span data-stu-id="513d9-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="513d9-171">Execute a etapa 2 novamente.</span><span class="sxs-lookup"><span data-stu-id="513d9-171">Run Step 2 again.</span></span> <span data-ttu-id="513d9-172">e preste atenção ao nome de usuário e à senha que você digitou.</span><span class="sxs-lookup"><span data-stu-id="513d9-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="513d9-173">\* *O módulo Microsoft Azure Active Directory para Windows PowerShell exige que o Microsoft .net Framework 3,5.* o recurso x \* está habilitado no computador \* *. É provável que seu computador tenha uma versão mais recente instalada (por exemplo, 4 ou 4,5.* x \*), mas a compatibilidade com versões anteriores do .NET Framework pode ser habilitada ou desabilitada.</span><span class="sxs-lookup"><span data-stu-id="513d9-173">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="513d9-174">Para mais informações, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="513d9-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="513d9-175">Para Windows Server 2012 ou Windows Server 2012 R2, confira [Habilitar o .NET Framework 3.5 usando o Assistente de Adição de Funções e Recursos](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="513d9-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="513d9-176">Para Windows 7 ou Windows Server 2008 R2, confira [Não é possível abrir o módulo Microsoft Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="513d9-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="513d9-177">Para Windows 10, Windows 8,1 e Windows 8, consulte [instalar o .NET Framework 3,5 no Windows 10, Windows 8,1 e Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="513d9-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="513d9-p111">**Sua versão do Módulo Microsoft Azure Active Directory para Windows PowerShell deve estar desatualizada.** Para verificar, execute o seguinte comando no Office 365 PowerShell ou no Módulo Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="513d9-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="513d9-180">Se o número da versão retornado for menor que o valor 1.0.8070.2, desinstale o Módulo Microsoft Azure Active Directory para Windows PowerShell e instale a versão mais recente usando o link da Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="513d9-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="513d9-181">**Se você receber um erro de conexão, confira este tópico:** ["Connect-MsolService: ocorreu exceção do tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="513d9-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="513d9-182">Confira também</span><span class="sxs-lookup"><span data-stu-id="513d9-182">See also</span></span>

- [<span data-ttu-id="513d9-183">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="513d9-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="513d9-184">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="513d9-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="513d9-185">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="513d9-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="513d9-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="513d9-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="513d9-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="513d9-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

