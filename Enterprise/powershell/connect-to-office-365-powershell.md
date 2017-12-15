---
title: Conectar-se ao PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- DecEntMigration
- apr17entnews
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Resumo: Conecte à sua organização do Office 365 usando o Office 365 PowerShell para realizar tarefas do Office 365 admin center a partir da linha de comando."
ms.openlocfilehash: 3ac368a3d3584c15e1d0c26104616e8258a78e7b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="2732e-103">Conectar-se ao PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="2732e-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="2732e-104">**Resumo:** Conecte-se à sua organização do Office 365 usando o Office 365 PowerShell para realizar tarefas de administração do Office 365 da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2732e-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="2732e-p101">O Office 365 PowerShell permite que você para gerenciar suas configurações do Office 365 da linha de comando. Conectar-se ao Office 365 PowerShell é um processo de três etapas simples onde você instala o software necessário, execute o software necessário e conecte-se à sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2732e-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="2732e-107">Observe que essas instruções de conexão são os mesmos no tópico [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span><span class="sxs-lookup"><span data-stu-id="2732e-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="2732e-p102">**Novo PowerShell?** Consulte a um [Vídeo de visão geral do PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), levado a você pelo aprendizado LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="2732e-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="2732e-110">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="2732e-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="2732e-111">Tempo estimado para conclusão: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="2732e-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="2732e-112">Você pode usar as seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="2732e-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="2732e-113">Windows 10, Windows 8.1, Windows 8 ou Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="2732e-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="2732e-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="2732e-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="2732e-p103">Use uma versão de 64 bits do Windows. Suporte para a versão de 32 bits do Microsoft Azure Active Directory módulo para Windows PowerShell foi descontinuado em outubro de 2014.</span><span class="sxs-lookup"><span data-stu-id="2732e-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="2732e-p104">O Office 365 funcionam ou escola a conta que você usa para esses procedimentos necessidades para ser um membro de uma função de administrador do Office 365. Para obter mais informações, consulte [funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="2732e-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>
    
## <a name="step-1-install-required-software"></a><span data-ttu-id="2732e-119">Etapa 1: Instalar o software necessário</span><span class="sxs-lookup"><span data-stu-id="2732e-119">Step 1: Install required software</span></span>

<span data-ttu-id="2732e-p105">Essas etapas precisam ser executadas apenas uma vez em seu computador e não toda vez em que você se conectar. No entanto, você provavelmente precisará instalar a versão mais recente do software periodicamente.</span><span class="sxs-lookup"><span data-stu-id="2732e-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="2732e-122">Instale a versão de 64 bits do Assistente de conexão do Microsoft Online Services: [Assistente de entrada do Microsoft Online Services para RTW de profissionais de TI](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span><span class="sxs-lookup"><span data-stu-id="2732e-122">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="2732e-123">Instale a versão de 64 bits do Módulo Microsoft Azure Active Directory para Windows PowerShell seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2732e-123">Install the 64-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="2732e-124">Abra a página da Web do [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185)</span><span class="sxs-lookup"><span data-stu-id="2732e-124">Open the [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) web page.</span></span>
    
  - <span data-ttu-id="2732e-125">Em **Arquivos em Download** na parte inferior da página, clique em **Download** para o arquivo **AdministrationConfig-V1.1.166.0-GA.msi** e instale-o.</span><span class="sxs-lookup"><span data-stu-id="2732e-125">In **Files in Download** at the bottom of the page, click **Download** for the **AdministrationConfig-V1.1.166.0-GA.msi** file, and then install it.</span></span>
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a><span data-ttu-id="2732e-126">Etapa 2: Abrir o Módulo do Microsoft Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="2732e-126">Step 2: Open the Windows Azure Active Directory Module</span></span>

1. <span data-ttu-id="2732e-127">Localizar e abrir o Módulo Microsoft Azure Active Directory para Windows PowerShell usando um dos seguintes métodos com base na sua versão do Windows:</span><span class="sxs-lookup"><span data-stu-id="2732e-127">Find and open the Microsoft Azure Active Directory Module for Windows PowerShell by using one of the following methods based on your version of Windows:</span></span>
    
  - <span data-ttu-id="2732e-128">**Menu Iniciar** A partir da área de trabalho, clique em **Iniciar** e, em seguida, digiteAzure.</span><span class="sxs-lookup"><span data-stu-id="2732e-128">**Start menu** From the desktop, click **Start**, and then type Azure.</span></span>
    
  - <span data-ttu-id="2732e-129">**Sem menu Iniciar** ProcurarAzure usando qualquer um destes métodos:</span><span class="sxs-lookup"><span data-stu-id="2732e-129">**No Start menu** Search forAzure using any of these methods:</span></span>
    
  - <span data-ttu-id="2732e-130">Na tela Inicial, clique em uma área vazia e digite Azure.</span><span class="sxs-lookup"><span data-stu-id="2732e-130">On the Start screen, click an empty area, and type Azure.</span></span>
    
  - <span data-ttu-id="2732e-p106">Na área de trabalho ou na tela Inicial, pressione a tecla Windows + Q. No botão Pesquisar, digite Azure.</span><span class="sxs-lookup"><span data-stu-id="2732e-p106">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Azure.</span></span>
    
  - <span data-ttu-id="2732e-p107">Na área de trabalho ou tela Iniciar, mova o cursor ao canto superior direito ou passe o dedo da borda direita da tela para mostrar os botões da esquerda. Selecione o botão Pesquisar e digite **Azure**.</span><span class="sxs-lookup"><span data-stu-id="2732e-p107">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and type **Azure**.</span></span>
    
2. <span data-ttu-id="2732e-135">Nos resultados, clique em **Módulo Microsoft Azure Active Directory para Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2732e-135">In the results, click **Microsoft Azure Active Directory Module for Windows PowerShell**.</span></span>
    
## <a name="step-3-connect-to-your-office-365-subscription"></a><span data-ttu-id="2732e-136">Etapa 3: Conectar-se à assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="2732e-136">Step 3: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="2732e-137"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="2732e-137"><a name="step3"> </a></span></span>

<span data-ttu-id="2732e-138">Para conectar-se apenas com o  *nome e senha de conta*  :</span><span class="sxs-lookup"><span data-stu-id="2732e-138">To connect with just an  *account name and password*  :</span></span>
  
1. <span data-ttu-id="2732e-139">Na janela de comando **Módulo Microsoft Azure Active Directory para Windows PowerShell**, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="2732e-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following commands.</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. <span data-ttu-id="2732e-140">Na caixa de diálogo **Solicitação de Credencial do Windows PowerShell**, digite o nome de usuário e a senha do Office 365conta comercial ou escolar e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="2732e-140">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="2732e-141">Para conectar-se com a  *MFA (autenticação multifator)*  :</span><span class="sxs-lookup"><span data-stu-id="2732e-141">To connect with  *multi-factor authentication (MFA)*  :</span></span>
  
1. <span data-ttu-id="2732e-142">Na janela de comando **Módulo Microsoft Azure Active Directory para Windows PowerShell**, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2732e-142">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
  ```
  Connect-MsolService
  ```

2. <span data-ttu-id="2732e-143">Na caixa de diálogo **PowerShell do Azure Active Directory**, digite seu Office 365conta comercial ou escolarnome de usuário e senha e clique em **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="2732e-143">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
3. <span data-ttu-id="2732e-144">Siga as instruções na caixa de diálogo **PowerShell do Azure Active Directory** para fornecer informações de autenticação adicionais, como o código de verificação, e clique **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="2732e-144">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="2732e-145">Como saber se funcionou?</span><span class="sxs-lookup"><span data-stu-id="2732e-145">How do you know this worked?</span></span>
<span data-ttu-id="2732e-146"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="2732e-146"><a name="step3"> </a></span></span>

<span data-ttu-id="2732e-p108">Se você não recebeu um erro, a conexão foi estabelecida. Um teste rápido é executar um cmdlet Office 365, por exemplo, **Get-MsolUser**, e ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="2732e-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="2732e-149">Caso você receba erros, verifique os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="2732e-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="2732e-p109">**Senhas incorretas são problemas comuns**. Execute as Etapa 3 novamente e preste muita atenção ao nome de usuário e à senha inseridos.</span><span class="sxs-lookup"><span data-stu-id="2732e-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="2732e-p110">**O Módulo Microsoft Azure Active Directory para Windows PowerShell requer que o recurso do Microsoft .NET Framework 3.5. _x_ esteja habilitado em seu computador**. É provável que seu computador tenha uma versão mais recente instalada (por exemplo, 4 ou 4.5. _x_), mas a compatibilidade com versões anteriores do .NET Framework pode ser habilitada ou desabilitada. Para saber mais, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="2732e-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="2732e-157">Para Windows Server 2012 ou Windows Server 2012 R2, consulte [Habilitar o .NET Framework 3.5 usando Adicionar funções e recursos do assistente](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="2732e-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="2732e-158">Para o Windows 8 ou Windows 8.1, consulte [Instalando o .NET Framework 3.5 no Windows 8 ou 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="2732e-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="2732e-159">Para o Windows 7 ou Windows Server 2008 R2, consulte [não é possível abrir o Windows Azure Active Directory módulo para Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="2732e-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="2732e-p111">**Sua versão do Módulo Microsoft Azure Active Directory para Windows PowerShell deve estar desatualizada.** Para verificar, execute o seguinte comando no Office 365 PowerShell ou no Módulo Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="2732e-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="2732e-162">Se o número da versão retornado for menor que o valor 1.0.8070.2, desinstale o Módulo Microsoft Azure Active Directory para Windows PowerShell e instale a versão mais recente usando o link da Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="2732e-162">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="2732e-163">**Se você receber um erro de conexão, consulte este tópico:** ["Connect-MsolService: Ocorreu exceção do tipo" Erro](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span><span class="sxs-lookup"><span data-stu-id="2732e-163">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="2732e-164">Conectar-se ao módulo do PowerShell V2 do Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="2732e-164">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="2732e-165"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="2732e-165"><a name="ConnectV2"> </a></span></span>

<span data-ttu-id="2732e-166">Para os procedimentos que exigem os novos cmdlets no [módulo PowerShell do Azure Active Directory V2](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use estas etapas para instalar o módulo e se conectar à sua assinatura do Office 365:</span><span class="sxs-lookup"><span data-stu-id="2732e-166">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="2732e-167">Abra um prompt de comando elevado do Windows PowerShell (execute o Windows PowerShell como administrador).</span><span class="sxs-lookup"><span data-stu-id="2732e-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="2732e-168">Na janela de comando do **Administrador: Windows PowerShell**, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="2732e-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="2732e-169">Se solicitado a instalar um módulo de um repositório não confiável, digite **Y** e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="2732e-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>
    
3. <span data-ttu-id="2732e-170">Quando a instalação do novo módulo estiver concluída, use estes comandos para se conectar à sua assinatura do Office 365:</span><span class="sxs-lookup"><span data-stu-id="2732e-170">When the installation of the new module is complete, use these commands to connect to your Office 365 subscription:</span></span>
    
  -  <span data-ttu-id="2732e-171">Com um  *nome e senha da conta*  :</span><span class="sxs-lookup"><span data-stu-id="2732e-171">With an *account name and password*  :</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 <span data-ttu-id="2732e-172">Na caixa de diálogo **Solicitação de Credencial do Windows PowerShell**, digite o nome de usuário e a senha do Office 365conta comercial ou escolar e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="2732e-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
  - <span data-ttu-id="2732e-173">Com  *MFA (Autenticação Multifator)*  :</span><span class="sxs-lookup"><span data-stu-id="2732e-173">With  *multi-factor authentication (MFA)*  :</span></span>
    
  ```
  Connect-AzureAD
  ```

<span data-ttu-id="2732e-174">Na caixa de diálogo **PowerShell do Azure Active Directory**, digite seu Office 365conta comercial ou escolarnome de usuário e senha e clique em **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="2732e-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="2732e-175">Siga as instruções na caixa de diálogo **PowerShell do Azure Active Directory** para fornecer informações de autenticação adicionais, como o código de verificação, e clique **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="2732e-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="2732e-176">Depois de se conectar, você poderá usar os novos cmdlets do [módulo do PowerShell V2 do Azure Active Directory](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span><span class="sxs-lookup"><span data-stu-id="2732e-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2732e-177">See also</span><span class="sxs-lookup"><span data-stu-id="2732e-177">See also</span></span>

#### 

[<span data-ttu-id="2732e-178">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2732e-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2732e-179">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2732e-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="2732e-180">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2732e-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[<span data-ttu-id="2732e-181">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="2732e-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="2732e-182">Conecte-se-MsolService</span><span class="sxs-lookup"><span data-stu-id="2732e-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

