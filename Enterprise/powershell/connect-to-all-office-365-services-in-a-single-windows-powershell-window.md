---
title: Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
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
description: 'Resumo: Conecte o Windows PowerShell a todos os serviços do Office 365 em uma única janela do Windows PowerShell.'
ms.openlocfilehash: 38221a2c9b50aaeab217016336cf4d020abd706a
ms.sourcegitcommit: 2e5e2c65a1b785e229f1f7fd5b219f1b3de96f97
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "30339509"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="ec72d-103">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec72d-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="ec72d-104">**Resumo:** Em vez de gerenciar diferentes serviços do Office 365 em janelas de console do PowerShell separadas, você pode se conectar a todos os serviços do Office 365 e gerenciá-los em uma única janela do console.</span><span class="sxs-lookup"><span data-stu-id="ec72d-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="ec72d-105">Quando você usa o PowerShell para gerenciar o Office 365, é possível ter até cinco sessões do Windows PowerShell diferentes abertas ao mesmo tempo que corresponde ao Office 365 Administration Center, SharePoint Online, Exchange Online, Skype for Business Online e à segurança &amp;Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="ec72d-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="ec72d-106">Com cinco métodos de conexão diferentes em sessões separadas do Windows PowerShell, sua área de trabalho pode ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="ec72d-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consoles do Windows PowerShell em execução ao mesmo tempo](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="ec72d-108">Isso não é ideal para gerenciar o Office 365 porque não é possível trocar dados entre essas cinco janelas para gerenciamento entre serviços.</span><span class="sxs-lookup"><span data-stu-id="ec72d-108">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="ec72d-109">Este tópico descreve como usar uma única instância do Windows PowerShell a partir da qual você pode gerenciar o Office 365, o Skype for Business Online, o Exchange Online, o SharePoint &amp; online e o centro de conformidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="ec72d-109">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="ec72d-110">Este artigo atualmente contém apenas os comandos para se conectar à nuvem do Office 365 Worldwide (+ GCC).</span><span class="sxs-lookup"><span data-stu-id="ec72d-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="ec72d-111">As observações adicionais fornecem links para artigos com informações sobre como se conectar às outras nuvens do Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec72d-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="ec72d-112">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="ec72d-112">Before you begin</span></span>

<span data-ttu-id="ec72d-113">Antes de poder gerenciar todo o Office 365 de uma única instância do Windows PowerShell, considere os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="ec72d-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="ec72d-114">O Office 365conta comercial ou escolar que você usa para esses procedimentos precisa ser um membro de uma função de administrador do Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec72d-114">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="ec72d-115">Para obter mais informações, consulte [sobre as funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span><span class="sxs-lookup"><span data-stu-id="ec72d-115">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="ec72d-116">Isso é um requisito para o Office 365 PowerShell, não necessariamente para todos os outros serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec72d-116">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="ec72d-117">Você pode usar as seguintes versões de 64 bits do Windows:</span><span class="sxs-lookup"><span data-stu-id="ec72d-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="ec72d-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="ec72d-118">Windows 10</span></span>
    
  - <span data-ttu-id="ec72d-119">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="ec72d-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="ec72d-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="ec72d-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="ec72d-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ec72d-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="ec72d-122">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ec72d-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="ec72d-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="ec72d-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="ec72d-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="ec72d-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="ec72d-125">\*Você precisa instalar o Microsoft .NET Framework 4,5. *x* e, em seguida, o Windows management Framework 3,0 ou o Windows management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="ec72d-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="ec72d-126">Para obter mais informações, consulte [instalando o .NET Framework e o](https://go.microsoft.com/fwlink/p/?LinkId=257868) [windows Management Framework 3,0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="ec72d-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="ec72d-127">Você precisa usar uma versão de 64 bits do Windows devido aos requisitos para o módulo do Skype for Business Online e um dos módulos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec72d-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="ec72d-128">Você precisa instalar os módulos necessários para o Azure AD, o SharePoint Online e o Skype for Business Online:</span><span class="sxs-lookup"><span data-stu-id="ec72d-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="ec72d-129">Azure Active Directory v2</span><span class="sxs-lookup"><span data-stu-id="ec72d-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="ec72d-130">Shell de Gerenciamento do SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ec72d-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="ec72d-131">Skype for Business Online, módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec72d-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="ec72d-132">O Windows PowerShell precisa ser configurado para executar scripts assinados para o Skype for Business Online, o Exchange Online e &amp; o centro de conformidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="ec72d-132">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="ec72d-133">Para fazer isso, execute o seguinte comando em uma sessão elevada do Windows PowerShell (uma janela do Windows PowerShell que você abre selecionando **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="ec72d-133">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="ec72d-134">Etapas de conexão ao usar uma senha</span><span class="sxs-lookup"><span data-stu-id="ec72d-134">Connection steps when using a password</span></span>

<span data-ttu-id="ec72d-135">Aqui estão as etapas para se conectar a todos os serviços em uma única janela do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec72d-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="ec72d-136">Abra o Windows PowerShell como administrador (use **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="ec72d-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="ec72d-137">Execute este comando e insira suas credenciais de conta corporativa ou de estudante do Office 365.</span><span class="sxs-lookup"><span data-stu-id="ec72d-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="ec72d-138">Execute este comando para se conectar ao AD (Active Directory) do Azure usando o módulo do PowerShell do Azure Active Directory para Graph.</span><span class="sxs-lookup"><span data-stu-id="ec72d-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="ec72d-139">Como alternativa, se você estiver usando o módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="ec72d-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. <span data-ttu-id="ec72d-140">Execute estes comandos para se conectar ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="ec72d-140">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="ec72d-141">Substitua _ \<domainhost>_ pelo valor real do seu domínio.</span><span class="sxs-lookup"><span data-stu-id="ec72d-141">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="ec72d-142">por exemplo, para "litwareinc.onmicrosoft.com", o valor de _ \<domainhost>_ é "litwareinc".</span><span class="sxs-lookup"><span data-stu-id="ec72d-142">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="ec72d-143">Execute estes comandos para se conectar ao Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="ec72d-143">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="ec72d-144">Um aviso sobre o aumento `WSMan NetworkDelayms` do valor é esperado na primeira vez que você se conecta e deve ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="ec72d-144">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="ec72d-145">Execute estes comandos para se conectar ao Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ec72d-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="ec72d-146">Para conectar-se ao Exchange Online para nuvens do Office 365 diferentes do mundo inteiro, confira [conectar-se ao PowerShell do Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="ec72d-146">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="ec72d-147">Execute estes comandos para se conectar ao centro &amp; de conformidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="ec72d-147">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="ec72d-148">Para se conectar ao centro &amp; de conformidade de segurança para nuvens do Office 365 diferentes do mundo, confira [conectar-se ao Office 365 Security _AMP_ Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="ec72d-148">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="ec72d-149">Aqui estão todos os comandos em um único bloco ao usar o módulo PowerShell do Azure Active Directory para Graph.</span><span class="sxs-lookup"><span data-stu-id="ec72d-149">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="ec72d-150">Especifique o nome do seu host de domínio e, em seguida, execute todos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ec72d-150">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="ec72d-151">Como alternativa, aqui estão todos os comandos em um único bloco ao usar o módulo do Microsoft Azure Active Directory para o módulo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec72d-151">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="ec72d-152">Especifique o nome do seu host de domínio e, em seguida, execute todos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ec72d-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="ec72d-153">Quando estiver pronto para fechar a janela do Windows PowerShell, execute este comando para remover as sessões ativas para o Skype for Business Online, o Exchange Online, o SharePoint Online e &amp; o centro de conformidade de segurança:</span><span class="sxs-lookup"><span data-stu-id="ec72d-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="ec72d-154">Etapas de conexão ao usar a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="ec72d-154">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="ec72d-155">Aqui estão todos os comandos em um único bloco para se conectar ao Azure AD, SharePoint Online e Skype para buiness usando a autenticação multifator em uma única janela usando o módulo do PowerShell do Azure Active Directory para Graph.</span><span class="sxs-lookup"><span data-stu-id="ec72d-155">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="ec72d-156">Especifique o nome UPN (nome principal de usuário) de uma conta de usuário e o nome de host do domínio e, em seguida, execute todos os itens de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="ec72d-156">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="ec72d-157">Como alternativa, aqui estão todos os comandos ao usar o módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec72d-157">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="ec72d-158">Para o Exchange Online e o &amp; centro de conformidade de segurança, consulte os seguintes tópicos para se conectarem usando a autenticação multifator:</span><span class="sxs-lookup"><span data-stu-id="ec72d-158">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="ec72d-159">Conectar-se ao PowerShell do Exchange Online usando a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="ec72d-159">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="ec72d-160">Conectar-se ao Office 365 Security & Compliance Center PowerShell usando a autenticação multifator</span><span class="sxs-lookup"><span data-stu-id="ec72d-160">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="ec72d-161">Observe que, em ambos os casos, você deve se conectar usando sessões separadas do módulo do PowerShell remoto do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="ec72d-161">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="ec72d-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec72d-162">See also</span></span>

- [<span data-ttu-id="ec72d-163">Conectar-se ao PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="ec72d-163">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="ec72d-164">Gerenciar o SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec72d-164">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="ec72d-165">Gerenciar contas de usuário e licenças usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec72d-165">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="ec72d-166">Use o Windows PowerShell para criar relatórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="ec72d-166">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
