---
title: Conectar-se ao PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 'Resumo: conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para realizar tarefas do Centro de administração do Office 365 a partir da linha de comando.'
ms.openlocfilehash: 71b8c8d61a914fa7fd036fadb7e17ca3f66cd639
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="ab213-103">Conectar-se ao PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="ab213-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="ab213-104">**Resumo:** conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para realizar tarefas de administração do Office 365 a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ab213-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="ab213-p101">O Office 365 PowerShell permite gerenciar as configurações do Office 365 na linha de comando. Conectar-se ao Office 365 PowerShell é um processo simples de três etapas em que você instala e executa o software necessário e depois se conecta à sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="ab213-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="ab213-p102">**Novo no PowerShell? ** Veja um [vídeo de visão geral do PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), apresentado pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="ab213-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="ab213-109">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="ab213-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="ab213-110">Tempo estimado para conclusão: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="ab213-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="ab213-111">Você pode usar as seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="ab213-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="ab213-112">Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="ab213-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="ab213-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="ab213-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="ab213-p103">Use uma versão de 64 bits do Windows, pois o suporte para a versão de 32 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell foi descontinuada em outubro de 2014.</span><span class="sxs-lookup"><span data-stu-id="ab213-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="ab213-p104">Estes procedimentos destinam-se para os usuários que são membros de uma função de administrador do Office 365. Para obter mais informações, consulte [funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="ab213-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ab213-118">Conecte com o Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab213-118">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ab213-119">Os comandos no Módulo Microsoft Azure Active Directory para Windows PowerShell têm **Msol** no nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab213-119">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="ab213-120">Etapa 1: instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="ab213-120">Step 1: Install required software</span></span>

<span data-ttu-id="ab213-p105">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="ab213-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="ab213-123">Instale a versão de 64 bits do Assistente de Conexão do Microsoft Online Services: [Assistente de Conexão do Microsoft Online Services para profissionais de TI RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="ab213-123">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="ab213-124">Instale o Módulo Microsoft Azure Active Directory para Windows PowerShell seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ab213-124">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="ab213-125">Abra um prompt de comando do PowerShell do nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="ab213-125">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="ab213-126">Execute o comando **Install-Module MSOnline**.</span><span class="sxs-lookup"><span data-stu-id="ab213-126">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="ab213-127">Se solicitado a instalar o provedor de NuGet, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="ab213-127">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="ab213-128">Se solicitado a instalar o módulo de PSGallery, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="ab213-128">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="ab213-129">Após a instalação, feche a janela de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab213-129">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-your-office-365-subscription"></a><span data-ttu-id="ab213-130">Etapa 2: conectar-se à sua assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="ab213-130">Step 2: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="ab213-131"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="ab213-131"></span></span>

<span data-ttu-id="ab213-132">Para conectar-se apenas com *nome e senha de conta*:</span><span class="sxs-lookup"><span data-stu-id="ab213-132">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="ab213-133">Execute o prompt de comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab213-133">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="ab213-134">Na janela de comando do **Windows PowerShell**, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="ab213-134">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="ab213-135">Na caixa de diálogo **Solicitação de Credencial do Windows PowerShell**, digite seu nome de usuário e senha para a conta corporativa ou de estudante do Office 365 e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab213-135">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="ab213-136">Para conectar-se com a *MFA (autenticação multifator)*:</span><span class="sxs-lookup"><span data-stu-id="ab213-136">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="ab213-137">Execute o prompt de comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab213-137">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="ab213-138">Na janela de comando **Módulo Microsoft Azure Active Directory para Windows PowerShell**, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab213-138">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="ab213-139">Na caixa de diálogo **PowerShell do Azure Active Directory**, digite seu nome de usuário e senha para a conta corporativa ou de estudante do Office 365 e clique em **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ab213-139">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="ab213-140">Siga as instruções na caixa de diálogo **PowerShell do Azure Active Directory** para fornecer informações de autenticação adicionais, como o código de verificação, e clique **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ab213-140">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="ab213-141">Como saber se funcionou?</span><span class="sxs-lookup"><span data-stu-id="ab213-141">How do you know this worked?</span></span>
<span data-ttu-id="ab213-142"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="ab213-142"></span></span>

<span data-ttu-id="ab213-p106">Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="ab213-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="ab213-145">Caso você receba erros, verifique os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="ab213-145">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="ab213-p107">**Senhas incorretas são problemas comuns**. Execute as Etapa 3 novamente e preste muita atenção ao nome de usuário e à senha inseridos.</span><span class="sxs-lookup"><span data-stu-id="ab213-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="ab213-p108">* *O Microsoft Azure Active Directory módulo para Windows PowerShell requer que o Microsoft .NET Framework 3.5.* x * recurso está ativado em seu computador * *. É provável que o seu computador tiver uma versão mais recente instalada (por exemplo, 4 ou 4.5.* x *), mas com versões anteriores a compatibilidade com versões mais antigas do .NET Framework pode ser habilitada ou desabilitada. Para obter mais informações, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="ab213-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.*x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.*x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="ab213-151">Para Windows Server 2012 ou Windows Server 2012 R2, confira [Habilitar o .NET Framework 3.5 usando o Assistente de Adição de Funções e Recursos](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="ab213-151">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="ab213-152">Para Windows 8 ou Windows 8.1, confira [Instalando o .NET Framework 3.5 no Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="ab213-152">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="ab213-153">Para Windows 7 ou Windows Server 2008 R2, confira [Não é possível abrir o módulo Microsoft Azure Active Directory para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="ab213-153">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="ab213-p109">**Sua versão do Módulo Microsoft Azure Active Directory para Windows PowerShell deve estar desatualizada.** Para verificar, execute o seguinte comando no Office 365 PowerShell ou no Módulo Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ab213-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="ab213-156">Se o número da versão retornado for menor que o valor 1.0.8070.2, desinstale o Módulo Microsoft Azure Active Directory para Windows PowerShell e instale a versão mais recente usando o link da Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="ab213-156">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="ab213-157">**Se você receber um erro de conexão, confira este tópico:** ["Connect-MsolService: ocorreu exceção do tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="ab213-157">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ab213-158">Conecte-se com o Azure Active Directory PowerShell para o módulo de gráfico</span><span class="sxs-lookup"><span data-stu-id="ab213-158">Connect with the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="ab213-159"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="ab213-159"></span></span>

<span data-ttu-id="ab213-160">Os comandos do Azure Active Directory PowerShell para o módulo de gráfico tem "AzureAD" em seu nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab213-160">Commands in the Azure Active Directory PowerShell for Graph module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="ab213-161">Para obter os procedimentos que exigem os cmdlets novos no Azure Active Directory PowerShell para o módulo de gráfico, execute estas etapas para instalar o módulo e conecte-se à sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="ab213-161">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="ab213-162">Consulte o [Azure Active Directory PowerShell para o módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) para obter informações sobre o suporte para diferentes versões do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="ab213-162">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="ab213-163">Etapa 1: instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="ab213-163">Step 1: Install required software</span></span>

<span data-ttu-id="ab213-p110">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="ab213-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="ab213-166">Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="ab213-166">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="ab213-167">Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="ab213-167">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="ab213-168">Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="ab213-168">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-office-365"></a><span data-ttu-id="ab213-169">Etapa 2: conectar-se ao Office 365</span><span class="sxs-lookup"><span data-stu-id="ab213-169">Step 2: Connect to Office 365</span></span>

<span data-ttu-id="ab213-170">Para se conectar à sua assinatura do Office 365 com um *nome de conta e senha*:</span><span class="sxs-lookup"><span data-stu-id="ab213-170">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="ab213-171">Na caixa de diálogo **Solicitação de Credencial do Windows PowerShell**, digite seu nome de usuário e senha para a conta corporativa ou de estudante do Office 365 e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab213-171">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="ab213-172">Para se conectar à sua assinatura do Office 365 com a *MFA (autenticação multifator)*:</span><span class="sxs-lookup"><span data-stu-id="ab213-172">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="ab213-173">Na caixa de diálogo **PowerShell do Azure Active Directory**, digite seu nome de usuário e senha para a conta corporativa ou de estudante do Office 365 e clique em **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ab213-173">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="ab213-174">Siga as instruções na caixa de diálogo **PowerShell do Azure Active Directory** para fornecer informações de autenticação adicionais, como o código de verificação, e clique **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ab213-174">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="ab213-175">Depois de se conectar, você pode usar os novos cmdlets para o [Windows Azure Active Directory PowerShell para o módulo de gráfico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="ab213-175">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ab213-176">Confira também</span><span class="sxs-lookup"><span data-stu-id="ab213-176">See also</span></span>

- [<span data-ttu-id="ab213-177">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab213-177">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="ab213-178">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab213-178">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="ab213-179">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab213-179">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="ab213-180">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="ab213-180">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="ab213-181">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="ab213-181">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

