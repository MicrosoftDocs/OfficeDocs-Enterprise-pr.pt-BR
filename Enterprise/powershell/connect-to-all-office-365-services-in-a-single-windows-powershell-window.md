---
title: Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/10/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Resumo: Conecte o Windows PowerShell para todos os serviços do Office 365 em uma única janela do Windows PowerShell.'
ms.openlocfilehash: ffa603ec50c95f5800315eee07b4d01e058852f3
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="d3f2b-103">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3f2b-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="d3f2b-104">**Resumo:** Em vez de gerenciar diferentes serviços do Office 365 em janelas separadas de console do PowerShell, é possível conectar-se a todos os serviços do Office 365 e gerenciá-los da janela do console único.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="d3f2b-p101">Quando você usar o PowerShell para gerenciar o Office 365, é possível ter até cinco sessões diferentes do Windows PowerShell abrir ao mesmo tempo correspondente ao centro de administração do Office 365, SharePoint Online, Exchange Online, Skype para Business Online e a segurança &amp;Centro de conformidade. Com cinco métodos diferentes de conexão em sessões separados do Windows PowerShell, sua área de trabalho pode ser assim:</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consoles do Windows PowerShell em execução ao mesmo tempo](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="d3f2b-p102">Isso não é ideal para gerenciar o Office 365 porque você não pode trocar dados entre esses cinco windows para o gerenciamento de cross-service. Este tópico descreve como usar uma única instância do Windows PowerShell a partir do qual você pode gerenciar o Office 365, Skype Business Online, Exchange Online, SharePoint Online e a segurança &amp; Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d3f2b-110">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="d3f2b-110">Before you begin</span></span>
<span data-ttu-id="d3f2b-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="d3f2b-111"></span></span>

<span data-ttu-id="d3f2b-112">Antes de você pode gerenciar tudo do Office 365 de uma única instância do Windows PowerShell, considere os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="d3f2b-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="d3f2b-p103">O Office 365 funcionam ou escola a conta que você usa para esses procedimentos necessidades para ser um membro de uma função de administrador do Office 365. Para obter mais informações, consulte [funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este um requisito para o Office 365 PowerShell, mas não necessariamente para todos os outros serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="d3f2b-116">Você pode usar as seguintes versões de 64 bits do Windows:</span><span class="sxs-lookup"><span data-stu-id="d3f2b-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="d3f2b-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d3f2b-117">Windows 10</span></span>
    
  - <span data-ttu-id="d3f2b-118">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="d3f2b-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="d3f2b-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d3f2b-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="d3f2b-120">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d3f2b-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="d3f2b-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="d3f2b-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="d3f2b-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="d3f2b-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="d3f2b-p104">Você precisa instalar o Microsoft .NET Framework 4.5. *x* e, em seguida, ambos o Windows Management Framework 3.0 ou o Windows Management Framework 4.0. Para obter mais informações, consulte [Instalando o .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) e [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="d3f2b-125">Você precisa usar uma versão de 64 bits do Windows devido aos requisitos para o Skype para módulo Business Online e outra os módulos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-125">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="d3f2b-126">Você precisa instalar os módulos necessários para o Office 365, SharePoint Online e Skype para Business Online:</span><span class="sxs-lookup"><span data-stu-id="d3f2b-126">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="d3f2b-127">Microsoft Online Service Assistente de conexão para profissionais de TI RTW</span><span class="sxs-lookup"><span data-stu-id="d3f2b-127">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="d3f2b-128">Windows Azure Active Directory módulo para Windows PowerShell (versão de 64 bits) com o comando **Install-módulo MSOnline** em um prompt de comando elevado do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-128">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="d3f2b-129">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="d3f2b-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="d3f2b-130">Skype para negócios on-line, o módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3f2b-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="d3f2b-p105">Windows PowerShell deve ser configurado para executar scripts assinados Skype para Business Online, o Exchange Online e a segurança &amp; Centro de conformidade. Para fazer isso, execute o seguinte comando em uma sessão do Windows PowerShell com privilégios elevados (uma janela do Windows PowerShell para abrir, selecione **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="d3f2b-133">Etapas de Conexão ao usar uma senha</span><span class="sxs-lookup"><span data-stu-id="d3f2b-133">Connection steps when using a password</span></span>
<span data-ttu-id="d3f2b-134"><a name="ConnStepsPassword"> </a></span><span class="sxs-lookup"><span data-stu-id="d3f2b-134"></span></span>

<span data-ttu-id="d3f2b-135">Aqui estão as etapas para se conectar a todos os serviços em uma única janela do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="d3f2b-136">Abra o Windows PowerShell como um administrador (use **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="d3f2b-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="d3f2b-137">Execute este comando e insira seu trabalho do Office 365 ou escola credenciais da conta.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="d3f2b-138">Execute estes comandos para se conectar ao Office 365.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-138">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="d3f2b-p106">Execute estes comandos para se conectar ao SharePoint Online. Substituir _ \<domainhost >_ com o valor real para seu domínio. Por exemplo, para `litwareinc.onmicrosoft.com`, o _ \<domainhost >_ valor é `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="d3f2b-p107">Execute estes comandos para se conectar ao Skype para negócios Online. Um aviso sobre o aumento do `WSMan NetworkDelayms` valor esperado na primeira vez que você se conectar e devem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="d3f2b-144">Execute estes comandos para se conectar ao Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-144">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. <span data-ttu-id="d3f2b-145">Execute estes comandos para se conectar à segurança &amp; Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-145">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
  Import-PSSession $SccSession
  ```

<span data-ttu-id="d3f2b-p108">Aqui estão todos os comandos em um único bloco. Especifique o nome do seu host do domínio e execute todas elas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p108">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $SccSession
```
<span data-ttu-id="d3f2b-148">Quando você estiver pronto para fechar a janela do Windows PowerShell para baixo, execute este comando para remover as sessões ativas para Skype para Business Online, Exchange Online, SharePoint Online e a segurança &amp; Centro de conformidade:</span><span class="sxs-lookup"><span data-stu-id="d3f2b-148">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="d3f2b-149">Etapas de Conexão ao usar a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="d3f2b-149">Connection steps when using multi-factor authentication</span></span>
<span data-ttu-id="d3f2b-150"><a name="ConnStepsMFA"> </a></span><span class="sxs-lookup"><span data-stu-id="d3f2b-150"></span></span>

<span data-ttu-id="d3f2b-p109">Aqui estão todos os comandos em um único bloco para se conectar ao AD do Windows Azure, SharePoint Online e Skype para negócios usando a autenticação multifator em uma única janela. Especifique o nome de nome principal (UPN) do usuário de uma conta de administrador global e seu nome de host do domínio e execute todas elas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-p109">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
#If you are running Office 365 commands that contain "AzureAd" in their name, use this command:
Connect-AzureAD
#If you are running Office 365 commands that contain "Msol" in their name, comment the preceding command and un-comment the following command:
#Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="d3f2b-153">Para o Exchange Online e a segurança &amp; Centro de conformidade, consulte os tópicos a seguir para se conectar usando a autenticação multifator:</span><span class="sxs-lookup"><span data-stu-id="d3f2b-153">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- <span data-ttu-id="d3f2b-154">[Connect to Exchange Online PowerShell usando a autenticação multifator](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="d3f2b-154">[Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell).</span></span>
- [<span data-ttu-id="d3f2b-155">Conectar-se ao PowerShell do Centro de conformidade usando a autenticação multifator & de segurança do Office 365</span><span class="sxs-lookup"><span data-stu-id="d3f2b-155">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="d3f2b-156">Observe que, em ambos os casos, você deve se conectar usando sessões separadas do Exchange Online Remote PowerShell módulo.</span><span class="sxs-lookup"><span data-stu-id="d3f2b-156">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="d3f2b-157">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="d3f2b-157">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="d3f2b-158">Veja também</span><span class="sxs-lookup"><span data-stu-id="d3f2b-158">See also</span></span>

- [<span data-ttu-id="d3f2b-159">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3f2b-159">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d3f2b-160">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3f2b-160">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="d3f2b-161">Gerenciar o SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3f2b-161">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="d3f2b-162">Gerenciar contas de usuário e licenças usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="d3f2b-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="d3f2b-163">Use o Windows PowerShell para criar relatórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="d3f2b-163">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
