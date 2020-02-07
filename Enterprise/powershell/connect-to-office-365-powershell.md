---
title: Conectar-se ao PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumo: conecte-se à sua organização do Office 365, usando o Office 365 PowerShell para realizar tarefas do centro de administração a partir da linha de comando.'
ms.openlocfilehash: 96ad47e6f60d6e098deffb48c56b4004d732b033
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844252"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="7106a-103">Conectar-se ao PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="7106a-103">Connect to Office 365 PowerShell</span></span>

<span data-ttu-id="7106a-104">O Office 365 PowerShell permite gerenciar as configurações do Office 365 da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7106a-104">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="7106a-105">Conectar-se ao Office 365 PowerShell é um processo simples em que você instala o software necessário e se conecta à sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="7106a-105">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="7106a-106">Existem duas versões do módulo do PowerShell usadas para se conectar ao Office 365 e administrar contas de usuários, grupos e licenças:</span><span class="sxs-lookup"><span data-stu-id="7106a-106">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="7106a-107">O Azure Active Directory PowerShell para Graph (inclui **AzureAD** no nome dos cmdlets)</span><span class="sxs-lookup"><span data-stu-id="7106a-107">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span>
- <span data-ttu-id="7106a-108">O Módulo Microsoft Azure Active Directory para Windows PowerShell (inclui **MSol** no nome dos cmdlets)</span><span class="sxs-lookup"><span data-stu-id="7106a-108">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="7106a-109">A partir da data deste artigo, o Azure Active Directory PowerShell para o módulo do Graph não substituiu completamente a funcionalidade dos cmdlets do Módulo Microsoft Azure Active Directory para o módulo do Windows PowerShell para a administração de usuários, grupos e licenças.</span><span class="sxs-lookup"><span data-stu-id="7106a-109">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="7106a-110">Em muitos casos, é necessário usar as duas versões.</span><span class="sxs-lookup"><span data-stu-id="7106a-110">In many cases, you need to use both versions.</span></span> <span data-ttu-id="7106a-111">As duas versões podem ser instaladas com segurança no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="7106a-111">You can safely install both versions on the same computer.</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="7106a-112">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="7106a-112">What do you need to know before you begin?</span></span>

<span data-ttu-id="7106a-113">Você pode usar as seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="7106a-113">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="7106a-114">Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="7106a-114">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="7106a-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="7106a-115">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>

    > [!NOTE]
    > <span data-ttu-id="7106a-116">Você deve usar a versão 5.1 ou posterior do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7106a-116">You must use PowerShell version 5.1 or later.</span></span> <span data-ttu-id="7106a-117">Para Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, e Windows Server 2008 R2 SP1, baixe e instale o [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="7106a-117">For Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2 SP1, download and install the [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span> 
    
    > [!NOTE]
    ><span data-ttu-id="7106a-p104">Use uma versão de 64 bits do Windows, pois o suporte para a versão de 32 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell foi descontinuada em outubro de 2014.</span><span class="sxs-lookup"><span data-stu-id="7106a-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
<span data-ttu-id="7106a-120">Esses procedimentos são destinados aos usuários membros de uma função de administrador do Office 365.</span><span class="sxs-lookup"><span data-stu-id="7106a-120">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="7106a-121">Para saber mais, confira [Sobre as funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="7106a-121">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="7106a-122">Conecte-se ao Azure Active Directory PowerShell para o módulo do Graph.</span><span class="sxs-lookup"><span data-stu-id="7106a-122">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="7106a-123">Os comandos no [Azure Active Directory PowerShell para o módulo do Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) possuem **AzureAD** no nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7106a-123">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="7106a-124">Para os procedimentos que exigem os novos cmdlets no Azure Active Directory PowerShell para o módulo do Graph, use estas etapas para instalar o módulo e se conectar à sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="7106a-124">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="7106a-125">Confira o [Azure Active Directory PowerShell para o módulo do Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obter mais informações sobre o suporte a diferentes versões do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="7106a-125">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="7106a-126">Etapa 1: instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="7106a-126">Step 1: Install required software</span></span>

<span data-ttu-id="7106a-p106">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="7106a-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="7106a-129">Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="7106a-129">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="7106a-130">Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="7106a-130">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```powershell
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="7106a-131">Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="7106a-131">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="7106a-132">Etapa 2: conectar-se ao Azure AD da sua assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="7106a-132">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="7106a-133">Para se conectar ao Azure AD da sua assinatura do Office 365 com um nome de conta e senha, ou com autenticação multifator (MFA), execute um destes comandos de um prompt de comando do Windows PowerShell (não é necessário ser privilegiado).</span><span class="sxs-lookup"><span data-stu-id="7106a-133">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="7106a-134">**Nuvem do Office 365**</span><span class="sxs-lookup"><span data-stu-id="7106a-134">**Office 365 cloud**</span></span> | <span data-ttu-id="7106a-135">**Comando**</span><span class="sxs-lookup"><span data-stu-id="7106a-135">**Command**</span></span> |
| <span data-ttu-id="7106a-136">Office 365 no Mundo (+GCC)</span><span class="sxs-lookup"><span data-stu-id="7106a-136">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="7106a-137">Office 365 operado pela 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="7106a-137">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="7106a-138">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="7106a-138">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="7106a-139">Office 365 U.S. Government DoD e Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="7106a-139">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="7106a-140">Na caixa de diálogo **Entrar na sua conta**, digite seu nome de usuário e senha para uma conta corporativa ou de estudante do Office 365, e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="7106a-140">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="7106a-141">Se você estiver usando uma MFA, siga as instruções das caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.</span><span class="sxs-lookup"><span data-stu-id="7106a-141">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

<span data-ttu-id="7106a-142">Depois de se conectar, você pode usar os cmdlets do [módulo do Azure Active Directory PowerShell para Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="7106a-142">After connecting, you can use the cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="7106a-143">Conecte com o Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7106a-143">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="7106a-144">Os comandos no Módulo Microsoft Azure Active Directory para Windows PowerShell têm **Msol** no nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7106a-144">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>

>[!Note]
><span data-ttu-id="7106a-145">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="7106a-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="7106a-146">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7106a-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="7106a-147">Etapa 1: instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="7106a-147">Step 1: Install required software</span></span>

<span data-ttu-id="7106a-p108">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="7106a-p108">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="7106a-150">Instale a versão de 64 bits do Assistente de Conexão do Microsoft Online Services: [Assistente de Conexão do Microsoft Online Services para profissionais de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="7106a-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="7106a-151">Instale o Módulo Microsoft Azure Active Directory para Windows PowerShell seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="7106a-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="7106a-152">Abra um prompt de comando privilegiado do Windows PowerShell (execute o Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="7106a-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="7106a-153">Execute o comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="7106a-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="7106a-154">Se solicitado a instalar o provedor de NuGet, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="7106a-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="7106a-155">Se solicitado a instalar o módulo de PSGallery, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="7106a-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="7106a-156">Etapa 2: conectar-se ao Azure AD da sua assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="7106a-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="7106a-157">Para se conectar ao Azure AD da sua assinatura do Office 365 com um nome de conta e senha, ou com autenticação multifator (MFA), execute um destes comandos de um prompt de comando do Windows PowerShell (não é necessário ser privilegiado).</span><span class="sxs-lookup"><span data-stu-id="7106a-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with multi-factor authentication (MFA), run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="7106a-158">**Nuvem do Office 365**</span><span class="sxs-lookup"><span data-stu-id="7106a-158">**Office 365 cloud**</span></span> | <span data-ttu-id="7106a-159">**Comando**</span><span class="sxs-lookup"><span data-stu-id="7106a-159">**Command**</span></span> |
| <span data-ttu-id="7106a-160">Office 365 no Mundo (+GCC)</span><span class="sxs-lookup"><span data-stu-id="7106a-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="7106a-161">Office 365 operado pela 21 Vianet</span><span class="sxs-lookup"><span data-stu-id="7106a-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="7106a-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="7106a-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="7106a-163">Office 365 U.S. Government DoD e Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="7106a-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="7106a-164">Na caixa de diálogo **Entrar na sua conta**, digite seu nome de usuário e senha para uma conta corporativa ou de estudante do Office 365, e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="7106a-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="7106a-165">Se você estiver usando uma MFA, siga as instruções das caixas de diálogo adicionais para fornecer mais informações de autenticação, como um código de verificação.</span><span class="sxs-lookup"><span data-stu-id="7106a-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="7106a-166">Como saber se funcionou?</span><span class="sxs-lookup"><span data-stu-id="7106a-166">How do you know this worked?</span></span>

<span data-ttu-id="7106a-p109">Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="7106a-p109">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="7106a-169">Caso você receba erros, verifique os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="7106a-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="7106a-170">**Senha incorreta é um problema comum**.</span><span class="sxs-lookup"><span data-stu-id="7106a-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="7106a-171">Execute a Etapa 2 novamente.</span><span class="sxs-lookup"><span data-stu-id="7106a-171">Run Step 2 again.</span></span> <span data-ttu-id="7106a-172">e preste muita atenção ao nome de usuário e à senha inseridos.</span><span class="sxs-lookup"><span data-stu-id="7106a-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="7106a-173">**O Módulo Microsoft Azure Active Directory para Windows PowerShell requer que o recurso do Microsoft .NET Framework 3.5.* x* esteja habilitado em seu computador**. É provável que seu computador tenha uma versão mais recente instalada (por exemplo, 4 ou 4.5.* x*), mas a compatibilidade com versões anteriores do .NET Framework pode ser habilitada ou desabilitada.</span><span class="sxs-lookup"><span data-stu-id="7106a-173">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="7106a-174">Para mais informações, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="7106a-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="7106a-175">Para Windows Server 2012 ou Windows Server 2012 R2, confira [Habilitar o .NET Framework 3.5 usando o Assistente de Adição de Funções e Recursos](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="7106a-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="7106a-176">Para Windows 7 ou Windows Server 2008 R2, confira [Não é possível abrir o Módulo Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="7106a-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="7106a-177">Para Windows 10, Windows 8.1 e Windows 8, confira [Instalar o .NET Framework 3.5 no Windows 10, Windows 8.1 e Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="7106a-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="7106a-p112">**Sua versão do Módulo Microsoft Azure Active Directory para Windows PowerShell deve estar desatualizada.** Para verificar, execute o seguinte comando no Office 365 PowerShell ou no Módulo Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7106a-p112">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="7106a-180">Se o número da versão retornado for menor que o valor 1.0.8070.2, desinstale o Módulo Microsoft Azure Active Directory para Windows PowerShell e instale a versão mais recente usando o link da Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="7106a-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="7106a-181">**Se você receber um erro de conexão, confira este tópico:** ["Connect-MsolService: ocorreu exceção do tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="7106a-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="7106a-182">Confira também</span><span class="sxs-lookup"><span data-stu-id="7106a-182">See also</span></span>

- [<span data-ttu-id="7106a-183">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7106a-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="7106a-184">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7106a-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="7106a-185">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7106a-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
