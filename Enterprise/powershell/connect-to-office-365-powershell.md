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
description: 'Resumo: Conecte à sua organização do Office 365 usando o Office 365 PowerShell para realizar tarefas de centro de administração da linha de comando.'
ms.openlocfilehash: ae0449611703759105d92a706cf78ba4a58ad4b2
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897194"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="bbaf8-103">Conectar-se ao PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="bbaf8-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="bbaf8-104">**Resumo:** Conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para executar tarefas de administração da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="bbaf8-p101">O Office 365 PowerShell permite gerenciar suas configurações do Office 365 da linha de comando. Conectar-se ao Office 365 PowerShell é um processo simples onde você instala o software necessário e conecte-se à sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p101">Office 365 PowerShell lets you manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="bbaf8-107">Existem duas versões do módulo do PowerShell que você usa para se conectar ao Office 365 e administrar licenças, grupos e contas de usuário:</span><span class="sxs-lookup"><span data-stu-id="bbaf8-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="bbaf8-108">Azure Active Directory PowerShell para gráfico (cmdlets incluem **AzureAD** em seu nome)</span><span class="sxs-lookup"><span data-stu-id="bbaf8-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="bbaf8-109">Microsoft Azure Active Directory módulo para Windows PowerShell (cmdlets incluem **MSol** em seu nome)</span><span class="sxs-lookup"><span data-stu-id="bbaf8-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="bbaf8-p102">A partir da data deste artigo, o Azure Active Directory PowerShell para o módulo de gráfico não substitui completamente a funcionalidade dos cmdlets do módulo do Microsoft Azure Active Directory módulo para Windows PowerShell para o usuário, grupo e administração de licença . Em muitos casos, você precisará usar as duas versões. Com segurança, você pode instalar ambas as versões no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p102">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="bbaf8-p103">\*\*Novo no PowerShell? \*\* Veja um [vídeo de visão geral do PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), apresentado pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="bbaf8-115">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="bbaf8-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="bbaf8-116">Tempo estimado para conclusão: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="bbaf8-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="bbaf8-117">Você pode usar as seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="bbaf8-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="bbaf8-118">10 do Windows, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="bbaf8-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="bbaf8-119">Windows Server 2019, 2016 do Windows Server, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="bbaf8-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="bbaf8-p104">Use uma versão de 64 bits do Windows, pois o suporte para a versão de 32 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell foi descontinuada em outubro de 2014.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="bbaf8-p105">Estes procedimentos destinam-se para os usuários que são membros de uma função de administrador do Office 365. Para obter mais informações, consulte [funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p105">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="bbaf8-124">Conecte-se com o Azure Active Directory PowerShell para o módulo de gráfico</span><span class="sxs-lookup"><span data-stu-id="bbaf8-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="bbaf8-125">Comandos no módulo do [Azure Active Directory PowerShell para gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) têm **AzureAD** em seu nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="bbaf8-126">Para obter os procedimentos que exigem os cmdlets novos no Azure Active Directory PowerShell para o módulo de gráfico, execute estas etapas para instalar o módulo e conecte-se à sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="bbaf8-127">Consulte o [Azure Active Directory PowerShell para o módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obter informações sobre o suporte para diferentes versões do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="bbaf8-128">Etapa 1: instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="bbaf8-128">Step 1: Install required software</span></span>

<span data-ttu-id="bbaf8-p106">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="bbaf8-131">Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="bbaf8-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="bbaf8-132">Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="bbaf8-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="bbaf8-133">Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="bbaf8-134">Etapa 2: Conectar ao Azure AD para sua assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="bbaf8-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="bbaf8-135">Para conectar ao Azure AD para sua assinatura do Office 365 com um nome de conta e senha ou com *a autenticação multifator (MFA)*, execute um destes comandos em um prompt de comando do Windows PowerShell (ele não tem de ser elevado).</span><span class="sxs-lookup"><span data-stu-id="bbaf8-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="bbaf8-136">**Nuvem do Office 365**</span><span class="sxs-lookup"><span data-stu-id="bbaf8-136">**Office 365 cloud**</span></span> | <span data-ttu-id="bbaf8-137">**Comando**</span><span class="sxs-lookup"><span data-stu-id="bbaf8-137">**Command**</span></span> |
| <span data-ttu-id="bbaf8-138">O Office 365 em todo o mundo (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="bbaf8-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="bbaf8-139">Office 365 operado pela Vianet 21</span><span class="sxs-lookup"><span data-stu-id="bbaf8-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="bbaf8-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="bbaf8-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="bbaf8-141">Office 365 US governamentais DoD e governamentais do Office 365 US GCC alta</span><span class="sxs-lookup"><span data-stu-id="bbaf8-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="bbaf8-142">Na caixa de diálogo **logon em sua conta** , digite o seu trabalho do Office 365 ou o nome de usuário da conta de escola e a senha e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="bbaf8-143">Se você estiver usando MFA, siga as instruções nas caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="bbaf8-144">Depois de se conectar, você pode usar os novos cmdlets para o [Windows Azure Active Directory PowerShell para o módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="bbaf8-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="bbaf8-145">Conecte com o Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbaf8-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="bbaf8-146">Os comandos no Módulo Microsoft Azure Active Directory para Windows PowerShell têm **Msol** no nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="bbaf8-147">Etapa 1: instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="bbaf8-147">Step 1: Install required software</span></span>

<span data-ttu-id="bbaf8-p107">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="bbaf8-150">Instale a versão de 64 bits do Assistente de Conexão do Microsoft Online Services: [Assistente de Conexão do Microsoft Online Services para profissionais de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="bbaf8-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="bbaf8-151">Instale o Módulo Microsoft Azure Active Directory para Windows PowerShell seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="bbaf8-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="bbaf8-152">Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="bbaf8-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="bbaf8-153">Execute o comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="bbaf8-154">Se solicitado a instalar o provedor de NuGet, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="bbaf8-155">Se solicitado a instalar o módulo de PSGallery, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="bbaf8-156">Etapa 2: Conectar ao Azure AD para sua assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="bbaf8-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="bbaf8-157">Para conectar ao Azure AD para sua assinatura do Office 365 com um nome de conta e senha ou com *a autenticação multifator (MFA)*, execute um destes comandos em um prompt de comando do Windows PowerShell (ele não tem de ser elevado).</span><span class="sxs-lookup"><span data-stu-id="bbaf8-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="bbaf8-158">**Nuvem do Office 365**</span><span class="sxs-lookup"><span data-stu-id="bbaf8-158">**Office 365 cloud**</span></span> | <span data-ttu-id="bbaf8-159">**Comando**</span><span class="sxs-lookup"><span data-stu-id="bbaf8-159">**Command**</span></span> |
| <span data-ttu-id="bbaf8-160">O Office 365 em todo o mundo (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="bbaf8-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="bbaf8-161">Office 365 operado pela Vianet 21</span><span class="sxs-lookup"><span data-stu-id="bbaf8-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="bbaf8-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="bbaf8-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="bbaf8-163">Office 365 US governamentais DoD e governamentais do Office 365 US GCC alta</span><span class="sxs-lookup"><span data-stu-id="bbaf8-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironmentName USGovernment` |
|||

<span data-ttu-id="bbaf8-164">Na caixa de diálogo **logon em sua conta** , digite o seu trabalho do Office 365 ou o nome de usuário da conta de escola e a senha e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="bbaf8-165">Se você estiver usando MFA, siga as instruções nas caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="bbaf8-166">Como saber se funcionou?</span><span class="sxs-lookup"><span data-stu-id="bbaf8-166">How do you know this worked?</span></span>

<span data-ttu-id="bbaf8-p108">Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="bbaf8-169">Caso você receba erros, verifique os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="bbaf8-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="bbaf8-p109">**Um problema comum é uma senha incorreta**. Execute novamente a etapa 2. e preste atenção o nome de usuário e a senha que você digitar.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p109">**A common problem is an incorrect password**. Run Step 2 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="bbaf8-p110">\* *O Microsoft Azure Active Directory módulo para Windows PowerShell requer que o Microsoft .NET Framework 3.5.* x \* recurso está ativado em seu computador \* *. É provável que o seu computador tiver uma versão mais recente instalada (por exemplo, 4 ou 4.5.* x \*), mas com versões anteriores a compatibilidade com versões mais antigas do .NET Framework pode ser habilitada ou desabilitada. Para obter mais informações, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="bbaf8-175">Para Windows Server 2012 ou Windows Server 2012 R2, confira [Habilitar o .NET Framework 3.5 usando o Assistente de Adição de Funções e Recursos](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="bbaf8-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="bbaf8-176">Para Windows 7 ou Windows Server 2008 R2, confira [Não é possível abrir o módulo Microsoft Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="bbaf8-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="bbaf8-177">Para 10 do Windows, Windows 8.1 e Windows 8, consulte [instalar o .NET Framework 3.5 no Windows 10, Windows 8.1 e Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="bbaf8-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="bbaf8-p111">**Sua versão do Módulo Microsoft Azure Active Directory para Windows PowerShell deve estar desatualizada.** Para verificar, execute o seguinte comando no Office 365 PowerShell ou no Módulo Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bbaf8-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="bbaf8-180">Se o número da versão retornado for menor que o valor 1.0.8070.2, desinstale o Módulo Microsoft Azure Active Directory para Windows PowerShell e instale a versão mais recente usando o link da Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="bbaf8-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="bbaf8-181">**Se você receber um erro de conexão, confira este tópico:** ["Connect-MsolService: ocorreu exceção do tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="bbaf8-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="bbaf8-182">Confira também</span><span class="sxs-lookup"><span data-stu-id="bbaf8-182">See also</span></span>

- [<span data-ttu-id="bbaf8-183">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbaf8-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="bbaf8-184">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbaf8-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="bbaf8-185">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbaf8-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="bbaf8-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="bbaf8-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="bbaf8-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="bbaf8-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

