---
title: Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
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
description: 'Resumo: Conecte o Windows PowerShell a todos os serviços do Office 365 em uma única janela do Windows PowerShell.'
ms.openlocfilehash: d47f4dab4938bd02be25525d2912604f676079db
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547749"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="8bed5-103">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bed5-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="8bed5-104">Quando você usa o PowerShell para gerenciar o Office 365, é possível ter até cinco sessões do Windows PowerShell diferentes abertas ao mesmo tempo que corresponde ao centro de administração do Microsoft 365, ao SharePoint Online, ao Exchange Online, ao Skype for Business Online, ao &amp; Microsoft Teams e ao centro de conformidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="8bed5-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="8bed5-105">Com cinco métodos de conexão diferentes em sessões separadas do Windows PowerShell, sua área de trabalho pode ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="8bed5-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consoles do Windows PowerShell em execução ao mesmo tempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="8bed5-107">Isso não é ideal para gerenciar o Office 365 porque não é possível trocar dados entre essas cinco janelas para gerenciamento entre serviços.</span><span class="sxs-lookup"><span data-stu-id="8bed5-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="8bed5-108">Este tópico descreve como usar uma única instância do Windows PowerShell a partir da qual você pode gerenciar o Office 365, o Skype for Business Online, o Exchange Online, o SharePoint Online, o &amp; Microsoft Teams e o centro de conformidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="8bed5-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="8bed5-109">Este artigo atualmente contém apenas os comandos para se conectar à nuvem do Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="8bed5-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="8bed5-110">As observações adicionais fornecem links para artigos com informações sobre como se conectar às outras nuvens do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bed5-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="8bed5-111">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="8bed5-111">Before you begin</span></span>

<span data-ttu-id="8bed5-112">Antes de poder gerenciar todo o Office 365 de uma única instância do Windows PowerShell, considere os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="8bed5-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="8bed5-113">O Office 365conta comercial ou escolar que você usa para esses procedimentos precisa ser um membro de uma função de administrador do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bed5-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="8bed5-114">Para saber mais, confira [Sobre as funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="8bed5-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="8bed5-115">Isso é um requisito para o Office 365 PowerShell, não necessariamente para todos os outros serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bed5-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="8bed5-116">Você pode usar as seguintes versões de 64 bits do Windows:</span><span class="sxs-lookup"><span data-stu-id="8bed5-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="8bed5-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8bed5-117">Windows 10</span></span>
    
  - <span data-ttu-id="8bed5-118">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="8bed5-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="8bed5-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="8bed5-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="8bed5-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8bed5-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="8bed5-121">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8bed5-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="8bed5-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="8bed5-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="8bed5-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="8bed5-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="8bed5-124">\*Você precisa instalar o Microsoft .NET Framework 4,5. *x* e, em seguida, o Windows management Framework 3,0 ou o Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="8bed5-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="8bed5-125">Para obter mais informações, consulte [instalando o .NET Framework e o](https://go.microsoft.com/fwlink/p/?LinkId=257868) [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="8bed5-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="8bed5-126">Você precisa usar uma versão de 64 bits do Windows devido aos requisitos para o módulo do Skype for Business Online e um dos módulos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bed5-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="8bed5-127">Você precisa instalar os módulos necessários para o Azure AD, o Exchange Online, o SharePoint Online, o Skype for Business Online e o Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="8bed5-127">You need to install the modules that are required for Azure AD, Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="8bed5-128">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="8bed5-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="8bed5-129">Shell de gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8bed5-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="8bed5-130">Skype for Business Online, módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bed5-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="8bed5-131">Exchange Online PowerShell v2</span><span class="sxs-lookup"><span data-stu-id="8bed5-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="8bed5-132">Visão geral do teams PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bed5-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="8bed5-133">O Windows PowerShell precisa ser configurado para executar scripts assinados do Skype for Business Online e do &amp; centro de conformidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="8bed5-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="8bed5-134">Para fazer isso, execute o seguinte comando em uma sessão elevada do Windows PowerShell (uma janela do Windows PowerShell que você abre selecionando **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="8bed5-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="8bed5-135">Etapas de conexão ao usar uma senha</span><span class="sxs-lookup"><span data-stu-id="8bed5-135">Connection steps when using a password</span></span>

<span data-ttu-id="8bed5-136">Aqui estão as etapas para se conectar a todos os serviços em uma única janela do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bed5-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="8bed5-137">Abra o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bed5-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="8bed5-138">Execute este comando e insira suas credenciais de conta corporativa ou de estudante do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8bed5-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="8bed5-139">Execute este comando para se conectar ao AD (Active Directory) do Azure usando o módulo do PowerShell do Azure Active Directory para Graph.</span><span class="sxs-lookup"><span data-stu-id="8bed5-139">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="8bed5-140">Como alternativa, se você estiver usando o módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="8bed5-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="8bed5-141">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="8bed5-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8bed5-142">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bed5-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="8bed5-143">Execute estes comandos para se conectar ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="8bed5-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="8bed5-144">Substitua _ \<domainhost>_ pelo valor real do seu domínio.</span><span class="sxs-lookup"><span data-stu-id="8bed5-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="8bed5-145">Por exemplo, para "litwareinc.onmicrosoft.com", o valor de _ \<>domainhost_ é "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="8bed5-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="8bed5-146">Execute estes comandos para se conectar ao Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="8bed5-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="8bed5-147">Um aviso sobre o aumento `WSMan NetworkDelayms` do valor é esperado na primeira vez que você se conecta e deve ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="8bed5-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="8bed5-148">Execute este comando para se conectar ao Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="8bed5-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="8bed5-149">Para se conectar ao Exchange Online para nuvens do Office 365 diferentes do mundo inteiro, use o parâmetro **-ExchangeEnvironmentName** .</span><span class="sxs-lookup"><span data-stu-id="8bed5-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="8bed5-150">Consulte [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="8bed5-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="8bed5-151">Execute estes comandos para se conectar ao Teams PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bed5-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="8bed5-152">Para conectar-se às nuvens do Microsoft Teams diferentes do mundo inteiro, confira [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span><span class="sxs-lookup"><span data-stu-id="8bed5-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="8bed5-153">Execute estes comandos para se conectar ao centro &amp; de conformidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="8bed5-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="8bed5-154">Para se conectar ao centro &amp; de conformidade de segurança para nuvens do Office 365 diferentes do mundo, confira [conectar-se ao office 365 segurança & centro de conformidade do PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="8bed5-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="8bed5-155">Aqui estão todos os comandos em um único bloco ao usar o módulo PowerShell do Azure Active Directory para Graph.</span><span class="sxs-lookup"><span data-stu-id="8bed5-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="8bed5-156">Especifique o nome do seu host de domínio e, em seguida, execute todos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="8bed5-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="8bed5-157">Como alternativa, aqui estão todos os comandos em um único bloco ao usar o módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bed5-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="8bed5-158">Especifique o nome do seu host de domínio e, em seguida, execute todos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="8bed5-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="8bed5-159">Quando estiver pronto para fechar a janela do Windows PowerShell, execute este comando para remover as sessões ativas para o Skype for Business Online, o SharePoint Online, &amp; o centro de conformidade de segurança e o Teams:</span><span class="sxs-lookup"><span data-stu-id="8bed5-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="8bed5-160">Etapas de conexão ao usar a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="8bed5-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="8bed5-161">Aqui estão todos os comandos em um único bloco para se conectar ao Azure AD, SharePoint Online, Skype for Business, Exchange Online e ao Microsoft Teams usando a autenticação multifator em uma única janela, usando o módulo do Azure Active Directory do PowerShell para Graph.</span><span class="sxs-lookup"><span data-stu-id="8bed5-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="8bed5-162">Especifique o nome UPN (nome principal de usuário) de uma conta de usuário e o nome de host do domínio e, em seguida, execute todos os itens de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="8bed5-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="8bed5-163">Como alternativa, aqui estão todos os comandos ao usar o módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bed5-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="8bed5-164">Para o centro &amp; de conformidade de segurança, confira [conectar-se ao centro de conformidade do Office 365 Security & o PowerShell usando a autenticação](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) multifator para se conectar usando a autenticação multifator:</span><span class="sxs-lookup"><span data-stu-id="8bed5-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="8bed5-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="8bed5-165">See also</span></span>

- [<span data-ttu-id="8bed5-166">Conectar-se ao PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="8bed5-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="8bed5-167">Gerenciar o SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bed5-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="8bed5-168">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bed5-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="8bed5-169">Use o Windows PowerShell para criar relatórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="8bed5-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
