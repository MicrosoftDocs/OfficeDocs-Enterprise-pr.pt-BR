---
title: Conectar-se a todos os serviços do Microsoft 365 usando uma única janela do Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Resumo: Conecte o Windows PowerShell a todos os serviços do Microsoft 365 em uma única janela do Windows PowerShell.'
ms.openlocfilehash: a037de53dcbf8fed95b9b4d5f05677997135dfb3
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230837"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="0c944-103">Conectar-se a todos os serviços do Microsoft 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c944-103">Connect to all Microsoft 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="0c944-104">Quando você usa o PowerShell para gerenciar o Microsoft 365, é possível ter até cinco sessões do Windows PowerShell diferentes abertas ao mesmo tempo que corresponde ao centro de administração do Microsoft 365, ao SharePoint Online, ao Exchange Online, ao Skype for Business Online, ao Microsoft Teams e ao centro de conformidade de segurança &amp; .</span><span class="sxs-lookup"><span data-stu-id="0c944-104">When you use PowerShell to manage Microsoft 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="0c944-105">Com cinco métodos de conexão diferentes em sessões separadas do Windows PowerShell, sua área de trabalho pode ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="0c944-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consoles do Windows PowerShell em execução ao mesmo tempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="0c944-107">Isso não é ideal para gerenciar o Microsoft 365 porque você não pode trocar dados entre essas cinco janelas para o gerenciamento entre serviços.</span><span class="sxs-lookup"><span data-stu-id="0c944-107">This is not optimal for managing Microsoft 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="0c944-108">Este tópico descreve como usar uma única instância do Windows PowerShell a partir da qual você pode gerenciar contas do Microsoft 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams e o centro de conformidade de segurança &amp; .</span><span class="sxs-lookup"><span data-stu-id="0c944-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Microsoft 365 accounts, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="0c944-109">Este artigo atualmente contém apenas os comandos para se conectar à nuvem do mundo (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="0c944-109">This article currently only contains the commands to connect to the Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="0c944-110">As observações adicionais fornecem links para artigos com informações sobre como se conectar às outras nuvens do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0c944-110">Additional notes provide links to articles with information about connecting to the other Microsoft 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="0c944-111">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="0c944-111">Before you begin</span></span>

<span data-ttu-id="0c944-112">Antes de poder gerenciar todo o Microsoft 365 de uma única instância do Windows PowerShell, considere os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="0c944-112">Before you can manage all of Microsoft 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="0c944-113">A conta corporativa ou de estudante da Microsoft 365 que você usa para esses procedimentos precisa ser membro de uma função de administrador do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0c944-113">The Microsoft 365 work or school account that you use for these procedures needs to be a member of a Microsoft 365 admin role.</span></span> <span data-ttu-id="0c944-114">Para saber mais, confira [Sobre funções de administrador](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).</span><span class="sxs-lookup"><span data-stu-id="0c944-114">For more information, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).</span></span> <span data-ttu-id="0c944-115">Isso é um requisito para o PowerShell para o Microsoft 365, não necessariamente para todos os outros serviços da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0c944-115">This a requirement for PowerShell for Microsoft 365, not necessarily for all other Microsoft 365 services.</span></span>
    
- <span data-ttu-id="0c944-116">Você pode usar as seguintes versões de 64 bits do Windows:</span><span class="sxs-lookup"><span data-stu-id="0c944-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="0c944-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="0c944-117">Windows 10</span></span>
    
  - <span data-ttu-id="0c944-118">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="0c944-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="0c944-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="0c944-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="0c944-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="0c944-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="0c944-121">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="0c944-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="0c944-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="0c944-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="0c944-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="0c944-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="0c944-124">\*Você precisa instalar o Microsoft .NET Framework 4,5. *x* e, em seguida, o Windows management Framework 3,0 ou o Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="0c944-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="0c944-125">Para obter mais informações, consulte [instalando o .NET Framework e o](https://go.microsoft.com/fwlink/p/?LinkId=257868) [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="0c944-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="0c944-126">Você precisa usar uma versão de 64 bits do Windows devido aos requisitos para o módulo do Skype for Business Online e um dos módulos do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0c944-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Microsoft 365 modules.</span></span>
    
- <span data-ttu-id="0c944-127">Você precisa instalar os módulos necessários para o Azure Active Directory (Azure AD), o Exchange Online, o SharePoint Online, o Skype for Business Online e o Teams:</span><span class="sxs-lookup"><span data-stu-id="0c944-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="0c944-128">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="0c944-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="0c944-129">Shell de gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="0c944-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="0c944-130">Skype for Business Online, Módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c944-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="0c944-131">Exchange Online PowerShell v2</span><span class="sxs-lookup"><span data-stu-id="0c944-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="0c944-132">Visão geral do teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c944-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="0c944-133">O Windows PowerShell precisa ser configurado para executar scripts assinados do Skype for Business Online e do &amp; centro de conformidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="0c944-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="0c944-134">Para fazer isso, execute o seguinte comando em uma sessão elevada do Windows PowerShell (uma janela do Windows PowerShell que você abre selecionando **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="0c944-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-just-a-password"></a><span data-ttu-id="0c944-135">Etapas de conexão ao usar apenas uma senha</span><span class="sxs-lookup"><span data-stu-id="0c944-135">Connection steps when using just a password</span></span>

<span data-ttu-id="0c944-136">Aqui estão as etapas para se conectar a todos os serviços em uma única janela do PowerShell quando você estiver usando apenas uma senha para entrar.</span><span class="sxs-lookup"><span data-stu-id="0c944-136">Here are the steps to connect to all the services in a single PowerShell window when you are using just a password for sign-in.</span></span>
  
1. <span data-ttu-id="0c944-137">Abra o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c944-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="0c944-138">Execute este comando e insira suas credenciais de conta corporativa ou de estudante da Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="0c944-138">Run this command and enter your Microsoft 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="0c944-139">Execute este comando para se conectar ao Azure AD usando o módulo PowerShell do Azure Active Directory para Graph.</span><span class="sxs-lookup"><span data-stu-id="0c944-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="0c944-140">Como alternativa, se você estiver usando o módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="0c944-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="0c944-141">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="0c944-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="0c944-142">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c944-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="0c944-143">Execute estes comandos para se conectar ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="0c944-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="0c944-144">Especifique o nome da organização do seu domínio.</span><span class="sxs-lookup"><span data-stu-id="0c944-144">Specify the organization name for your domain.</span></span> <span data-ttu-id="0c944-145">Por exemplo, para "litwareinc.onmicrosoft.com", o valor do nome da organização é "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="0c944-145">For example, for "litwareinc.onmicrosoft.com", the  organization name value is "litwareinc".</span></span>
    
  ```powershell
  $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
  Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
  ```

5. <span data-ttu-id="0c944-146">Execute estes comandos para se conectar ao Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="0c944-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="0c944-147">Um aviso sobre o aumento do `WSMan NetworkDelayms` valor é esperado na primeira vez que você se conecta e deve ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="0c944-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="0c944-148">Execute este comando para se conectar ao Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0c944-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="0c944-149">Para se conectar ao Exchange Online para nuvens Microsoft 365 diferentes do mundo, use o parâmetro **-ExchangeEnvironmentName** .</span><span class="sxs-lookup"><span data-stu-id="0c944-149">To connect to Exchange Online for Microsoft 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="0c944-150">Consulte [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0c944-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="0c944-151">Execute estes comandos para se conectar ao Teams PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c944-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="0c944-152">Para conectar-se às nuvens do Microsoft Teams diferentes do mundo inteiro, confira [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="0c944-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="0c944-153">Execute estes comandos para se conectar ao centro de conformidade de segurança &amp; .</span><span class="sxs-lookup"><span data-stu-id="0c944-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="0c944-154">Para se conectar ao &amp; centro de conformidade de segurança para nuvens Microsoft 365 diferentes do mundo, confira [conectar-se ao PowerShell do centro de conformidade do & de segurança](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="0c944-154">To connect to the Security &amp; Compliance Center for Microsoft 365 clouds other than Worldwide, see [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="0c944-155">Aqui estão todos os comandos em um único bloco ao usar o módulo PowerShell do Azure Active Directory para Graph.</span><span class="sxs-lookup"><span data-stu-id="0c944-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="0c944-156">Especifique o nome do seu host de domínio e, em seguida, execute todos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="0c944-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="0c944-157">Como alternativa, aqui estão todos os comandos em um único bloco ao usar o módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c944-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="0c944-158">Especifique o nome do seu host de domínio e, em seguida, execute todos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="0c944-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="0c944-159">Quando estiver pronto para fechar a janela do Windows PowerShell, execute este comando para remover as sessões ativas para o Skype for Business Online, o SharePoint Online, o centro de conformidade de segurança &amp; e o Teams:</span><span class="sxs-lookup"><span data-stu-id="0c944-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="0c944-160">Etapas de conexão ao usar a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="0c944-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="0c944-161">Aqui estão todos os comandos em um único bloco para se conectar ao Azure AD, SharePoint Online, Skype for Business, Exchange Online e ao Microsoft Teams usando a autenticação multifator em uma única janela, usando o módulo do Azure Active Directory do PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="0c944-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="0c944-162">Especifique o nome UPN (nome principal de usuário) de uma conta de usuário e o nome de host do domínio e, em seguida, execute todos os itens de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="0c944-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="0c944-163">Como alternativa, aqui estão todos os comandos ao usar o módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c944-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="0c944-164">Para o centro de conformidade de segurança &amp; , confira [conectar-se ao PowerShell do centro de conformidade de & de segurança usando a autenticação multifator](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) para se conectar usando a autenticação multifator:</span><span class="sxs-lookup"><span data-stu-id="0c944-164">For the Security &amp; Compliance Center, see [Connect to Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="0c944-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c944-165">See also</span></span>

- [<span data-ttu-id="0c944-166">Conectar o Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c944-166">Connect to Microsoft 365 with PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="0c944-167">Gerenciar o SharePoint Online com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c944-167">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="0c944-168">Gerenciar contas de usuário, licenças e grupos do Microsoft 365 com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c944-168">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="0c944-169">Usar o Windows PowerShell para criar relatórios no Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0c944-169">Use Windows PowerShell to create reports in Microsoft 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
