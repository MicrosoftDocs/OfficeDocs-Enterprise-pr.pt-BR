---
title: "Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell"
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
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "Resumo: Conecte o Windows PowerShell para todos os serviços do Office 365 em uma única janela do Windows PowerShell."
ms.openlocfilehash: 5f97924d141afa4319c761fee86b13cb2b0705fb
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="468ad-103">Conectar-se a todos os serviços do Office 365 usando uma única janela do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="468ad-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="468ad-104">**Resumo:** Em vez de gerenciar diferentes serviços do Office 365 em janelas separadas de console do PowerShell, é possível conectar-se a todos os serviços do Office 365 e gerenciá-los da janela do console único.</span><span class="sxs-lookup"><span data-stu-id="468ad-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="468ad-p101">Quando você usar o PowerShell para gerenciar o Office 365, é possível ter até cinco sessões diferentes do Windows PowerShell abrir ao mesmo tempo correspondente ao centro de administração do Office 365, SharePoint Online, Exchange Online, Skype para Business Online e a segurança &amp;Centro de conformidade. Com cinco métodos diferentes de conexão em sessões separados do Windows PowerShell, sua área de trabalho pode ser assim:</span><span class="sxs-lookup"><span data-stu-id="468ad-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![Cinco consoles do Windows PowerShell em execução ao mesmo tempo](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="468ad-p102">Isso não é ideal para gerenciar o Office 365 porque você não pode trocar dados entre esses cinco windows para o gerenciamento de cross-service. Este tópico descreve como usar uma única instância do Windows PowerShell a partir do qual você pode gerenciar o Office 365, Skype Business Online, Exchange Online, SharePoint Online e a segurança &amp; Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="468ad-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="468ad-110">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="468ad-110">Before you begin</span></span>
<span data-ttu-id="468ad-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-111"></span></span>

<span data-ttu-id="468ad-112">Antes de você pode gerenciar tudo do Office 365 de uma única instância do Windows PowerShell, considere os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="468ad-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="468ad-p103">O Office 365 funcionam ou escola a conta que você usa para esses procedimentos necessidades para ser um membro de uma função de administrador do Office 365. Para obter mais informações, consulte [funções de administrador do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367). Este um requisito para o Office 365 PowerShell, mas não necessariamente para todos os outros serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="468ad-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="468ad-116">Você pode usar as seguintes versões de 64 bits do Windows:</span><span class="sxs-lookup"><span data-stu-id="468ad-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="468ad-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="468ad-117">Windows 10</span></span>
    
  - <span data-ttu-id="468ad-118">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="468ad-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="468ad-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="468ad-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="468ad-120">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="468ad-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="468ad-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="468ad-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="468ad-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="468ad-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="468ad-p104">Você precisa instalar o Microsoft .NET Framework 4.5. _x_ e, em seguida, ambos o Windows Management Framework 3.0 ou o Windows Management Framework 4.0. Para obter mais informações, consulte [Instalando o .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) e [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span><span class="sxs-lookup"><span data-stu-id="468ad-p104">You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="468ad-126">Você precisa usar uma versão de 64 bits do Windows devido aos requisitos para o Skype para módulo Business Online e outra os módulos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="468ad-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="468ad-127">Você precisa instalar os módulos necessários para o Office 365, SharePoint Online e Skype para Business Online:</span><span class="sxs-lookup"><span data-stu-id="468ad-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
  - [<span data-ttu-id="468ad-128">Microsoft Online Service Assistente de conexão para profissionais de TI RTW</span><span class="sxs-lookup"><span data-stu-id="468ad-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [<span data-ttu-id="468ad-129">Windows Azure Active Directory módulo para Windows PowerShell (versão de 64 bits)</span><span class="sxs-lookup"><span data-stu-id="468ad-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version)</span></span>](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [<span data-ttu-id="468ad-130">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="468ad-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [<span data-ttu-id="468ad-131">Skype para negócios on-line, o módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="468ad-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="468ad-p105">Windows PowerShell deve ser configurado para executar scripts assinados Skype para Business Online, o Exchange Online e a segurança &amp; Centro de conformidade. Para fazer isso, execute o seguinte comando em uma sessão do Windows PowerShell com privilégios elevados (uma janela do Windows PowerShell para abrir, selecione **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="468ad-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="468ad-134">A versão curta (instruções sem explicações)</span><span class="sxs-lookup"><span data-stu-id="468ad-134">The short version (instructions without explanations)</span></span>
<span data-ttu-id="468ad-135"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-135"></span></span>

<span data-ttu-id="468ad-p106">Esta seção apresenta as etapas de conexão sem explicações detalhadas. Se você tiver dúvidas ou se quiser obter mais informações, leia o restante do tópico. Os números de etapa aqui correspondem às seções de etapas numeradas no restante do tópico:</span><span class="sxs-lookup"><span data-stu-id="468ad-p106">This section presents the connection steps without in-depth explanations. If you have questions or want more information, you can read rest of the topic. The step numbers here match the step-numbered sections in the rest of the topic:</span></span>
  
1. <span data-ttu-id="468ad-139">Abra o Windows PowerShell como um administrador (use **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="468ad-139">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="468ad-140">Execute este comando e insira seu trabalho do Office 365 ou escola credenciais da conta.</span><span class="sxs-lookup"><span data-stu-id="468ad-140">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="468ad-141">Execute estes comandos para se conectar ao Office 365.</span><span class="sxs-lookup"><span data-stu-id="468ad-141">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="468ad-p107">Execute estes comandos para se conectar ao SharePoint Online. Substituir _ \<domainhost >_ com o valor real para seu domínio. Por exemplo, para `litwareinc.onmicrosoft.com`, o _ \<domainhost >_ valor é `litwareinc`.</span><span class="sxs-lookup"><span data-stu-id="468ad-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="468ad-p108">Execute estes comandos para se conectar ao Skype para negócios Online. Um aviso sobre o aumento do `WSMan NetworkDelayms` valor esperado na primeira vez que você se conectar e devem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="468ad-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="468ad-147">Execute estes comandos para se conectar ao Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="468ad-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="468ad-148">Execute estes comandos para se conectar à segurança &amp; Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="468ad-148">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="468ad-p109">O prefixo de texto "cc" é adicionado a *todas as* segurança &amp; nomes de cmdlet do Centro de conformidade para que você possa executar cmdlets que existem no Exchange Online e a segurança &amp; Centro de conformidade na mesma sessão do Windows PowerShell. Por exemplo, **Get-RoleGroup** torna-se **Get-ccRoleGroup** na segurança &amp; Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="468ad-p109">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="468ad-p110">Aqui estão todos os comandos em um único bloco. Especifique o nome do seu host do domínio e execute todas elas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="468ad-p110">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="468ad-153">Quando você estiver pronto para fechar a janela do Windows PowerShell para baixo, execute este comando para remover as sessões ativas para Skype para Business Online, Exchange Online, SharePoint Online e a segurança &amp; Centro de conformidade:</span><span class="sxs-lookup"><span data-stu-id="468ad-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="468ad-154">A versão longa (instruções com explicações detalhadas)</span><span class="sxs-lookup"><span data-stu-id="468ad-154">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="468ad-155"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-155"></span></span>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a><span data-ttu-id="468ad-156">Etapa 1: abrir o Windows PowerShell como administrador</span><span class="sxs-lookup"><span data-stu-id="468ad-156">Step 1: Open Windows PowerShell as an administrator</span></span>
<span data-ttu-id="468ad-157"><a name="Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-157"></span></span>

<span data-ttu-id="468ad-158">Se você estiver executando o Windows 10, Windows 8, Windows 8.1, 2016 do Windows Server, Windows Server 2012 R2 ou Windows Server 2012 R2, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="468ad-158">If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:</span></span>
  
1. <span data-ttu-id="468ad-159">Use qualquer um desses métodos para localizar o atalho do **Windows PowerShell**:</span><span class="sxs-lookup"><span data-stu-id="468ad-159">Use any of these methods to find the shortcut for **Windows PowerShell**:</span></span>
    
  - <span data-ttu-id="468ad-160">Na tela Iniciar, clique em uma área vazia e digite o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="468ad-160">On the Start screen, click an empty area, and type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="468ad-p111">Na área de trabalho ou tela Iniciar, pressione o Windows chave + Q. No botão Pesquisar, digite o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="468ad-p111">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="468ad-p112">Na área de trabalho ou tela Iniciar, mova o cursor ao canto superior direito ou passe o dedo da borda direita da tela para mostrar os botões da esquerda. Selecione o botão Pesquisar e insira o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="468ad-p112">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.</span></span>
    
2. <span data-ttu-id="468ad-165">Nos resultados, clique com botão direito **Do Windows PowerShell**e selecione **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="468ad-165">In the results, right-click **Windows PowerShell**, and select **Run as administrator**.</span></span>
    
3. <span data-ttu-id="468ad-166">Se a caixa de diálogo **Controle de conta de usuário** for exibida, selecione **Sim** para verificar que você deseja executar o Windows PowerShell sob as credenciais de administrador.</span><span class="sxs-lookup"><span data-stu-id="468ad-166">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="468ad-167">Se você estiver executando o Windows 7 SP1 (ou Windows Server 2008 R2 SP1), faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="468ad-167">If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:</span></span>
  
1. <span data-ttu-id="468ad-p113">No menu **Iniciar** , selecione **Todos os programas** > **Acessórios** > **Do Windows PowerShell**. Com o botão direito **Do Windows PowerShell**e, em seguida, selecione **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="468ad-p113">On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>
    
2. <span data-ttu-id="468ad-170">Se a caixa de diálogo **Controle de conta de usuário** for exibida, selecione **Sim** para verificar que você deseja executar o Windows PowerShell sob as credenciais de administrador.</span><span class="sxs-lookup"><span data-stu-id="468ad-170">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="468ad-p114">Você deve executar o Windows PowerShell como administrador. Se não fizer isso, você vai receber uma mensagem de erro semelhante a esta quando você tenta importar um dos módulos necessários.</span><span class="sxs-lookup"><span data-stu-id="468ad-p114">You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.</span></span>
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

<span data-ttu-id="468ad-p115">A única maneira de remediar a situação é fechar o Windows PowerShell e reiniciá-lo como um administrador. Aqui está uma maneira rápida e fácil saber se você estiver executando o Windows PowerShell como um administrador: prompt é `PS C:\Windows\System32>`, e não `PS C:\Users\YourUserName>`.</span><span class="sxs-lookup"><span data-stu-id="468ad-p115">The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.</span></span>

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a><span data-ttu-id="468ad-175">Etapa 2: Criar um objeto de credenciais do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="468ad-175">Step 2: Create a Windows PowerShell credentials object</span></span>
<span data-ttu-id="468ad-176"><a name="Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-176"></span></span>

<span data-ttu-id="468ad-p116">O objeto de credenciais oferece uma maneira criptografada para passar o seu nome de usuário e senha para o Windows PowerShell. Para criar um objeto de credenciais, execute o seguinte comando no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="468ad-p116">The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.</span></span>
  
```
$credential = Get-Credential
```

> [!NOTE]
>  <span data-ttu-id="468ad-p117">`$credential`é uma variável que armazenará o objeto de credenciais. Você não precisa nomeie a variável `$credential`, mas fazer isso torna mais fácil de lembrar qual variável contém o objeto de credenciais. (E que é importante, porque vai reutilizar a essa variável várias vezes). Que também facilitará a seguir nossos exemplos, pois este artigo sempre usarão `$credential` para representar o objeto de credenciais.</span><span class="sxs-lookup"><span data-stu-id="468ad-p117">`$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.</span></span>
  
<span data-ttu-id="468ad-182">Em seguida, o Windows PowerShell exibirá uma caixa de diálogo parecida com esta.</span><span class="sxs-lookup"><span data-stu-id="468ad-182">Windows PowerShell will then display a dialog box that looks like this.</span></span>
  
![Caixa de diálogo de solicitação de credenciais em branco.](images/o365_powershell_empty_credentials_box.png)
  
<span data-ttu-id="468ad-184">Digite seu trabalho ou nome de usuário de conta na caixa **nome de usuário** , usando o formato _username@domainname_ (por exemplo, kenmyer@litwareinc.onmicrosoft.com); da escola Digite sua senha na caixa **senha** ; e, em seguida, clique em **Okey**:</span><span class="sxs-lookup"><span data-stu-id="468ad-184">Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:</span></span>
  
![Conclusão da caixa de diálogo de solicitação de credenciais.](images/o365_powershell_completed_credentials_box.png)
  
<span data-ttu-id="468ad-p118">Observe que, como normalmente é o caso, você não verá qualquer tipo de confirmação de que o objeto de credenciais foi criado. (Windows PowerShell geralmente informa quando as coisas dão erradas, mas não sempre diz quando coisas ir para a direita.) Se você quiser verificar se o objeto de credenciais foi criado, digite o seguinte no Windows PowerShell e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="468ad-p118">Note that, as is often the case, you won't see any sort of confirmation that the credentials object was created. (Windows PowerShell typically tells you when things go wrong but doesn't always tell you when things go right.) If you want to verify that the credentials object was created, type the following in Windows PowerShell and then press Enter.</span></span>
  
```
$credential
```

<span data-ttu-id="468ad-188">Depois você deve ver algo como o seguinte na tela:</span><span class="sxs-lookup"><span data-stu-id="468ad-188">You should then see something similar to this on the screen.</span></span>
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

<span data-ttu-id="468ad-p119">Uma coisa deve ter em mente aqui é que o cmdlet [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) apenas cria o objeto de credenciais; ele não autenticar você ou caso contrário, verifique se o nome de usuário e a senha que você forneceu estão corretas. Por exemplo, suponha que você digitado incorretamente o nome de usuário como kenmyer@litwareinc.onmicrosoft.com. Se você fizer isso, **Get-Credential** criará um objeto de credenciais usando esse nome de usuário e sem verificar ver se esse é realmente um nome de usuário válido. Você não sabe se você tiver criado um objeto de credenciais válidas realmente até que você realmente os utilizam esse objeto para tentar se conectar aos serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="468ad-p119">One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.</span></span>
  
### <a name="step-3-connect-to-office-365"></a><span data-ttu-id="468ad-192">Etapa 3: Conectar-se ao Office 365</span><span class="sxs-lookup"><span data-stu-id="468ad-192">Step 3: Connect to Office 365</span></span>
<span data-ttu-id="468ad-193"><a name="Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-193"></span></span>

<span data-ttu-id="468ad-194">Começaremos conectando-se ao Office 365 em si.</span><span class="sxs-lookup"><span data-stu-id="468ad-194">We'll start by connecting to Office 365 itself.</span></span> 
  
<span data-ttu-id="468ad-p120">A primeira coisa que precisamos fazer aqui é importar o módulo do Office 365 (o Microsoft Azure Active Directory módulo para Windows PowerShell). Para fazer isso, execute este comando no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="468ad-p120">The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.</span></span>
  
```
Import-Module MsOnline
```

<span data-ttu-id="468ad-197">No entanto, execute o comando a seguir para verificar se o módulo foi importado.</span><span class="sxs-lookup"><span data-stu-id="468ad-197">If you want to verify that the module was imported, run this command.</span></span>
  
```
Get-Module
```

<span data-ttu-id="468ad-198">Em algum lugar na lista de módulos retornados por esse comando você verá algo semelhante isso: `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span><span class="sxs-lookup"><span data-stu-id="468ad-198">Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span></span>
  
<span data-ttu-id="468ad-199">Se você vir `MSOnline` listado, isso significa que tudo correu.</span><span class="sxs-lookup"><span data-stu-id="468ad-199">If you see  `MSOnline` listed, that means that everything went according to plan.</span></span>
  
<span data-ttu-id="468ad-200">Com o objeto de credenciais criado (consulte [etapa 2: criar um objeto de credenciais do Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) e com o `MsOnline` módulo carregado, podemos agora pode se conectar ao Office 365 usando o cmdlet [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) e o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="468ad-200">With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.</span></span>
  
```
Connect-MsolService -Credential $credential
```

<span data-ttu-id="468ad-p121">Observe que tudo o que você precisa fornecer é o objeto de credenciais ( `$credential`). Com base nessas credenciais, Office 365 irá automaticamente conectá-lo ao domínio correto. Você não precisará especificar o nome do seu domínio ao se executar o **Connect-MsolService**.</span><span class="sxs-lookup"><span data-stu-id="468ad-p121">Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.</span></span>
  
<span data-ttu-id="468ad-204">Para verificar que você realmente *estiver* conectado ao Office 365, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="468ad-204">To verify that you really  *are*  connected to Office 365, run this command.</span></span>
  
```
Get-MsolDomain
```

<span data-ttu-id="468ad-205">Como resposta, você deve receber alguma coisa parecida com:</span><span class="sxs-lookup"><span data-stu-id="468ad-205">In return, you should get back something similar to this.</span></span>
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a><span data-ttu-id="468ad-206">Etapa 4: Conectar ao SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="468ad-206">Step 4: Connect to SharePoint Online</span></span>
<span data-ttu-id="468ad-207"><a name="Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-207"></span></span>

<span data-ttu-id="468ad-208">Importe o módulo do SharePoint Online com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="468ad-208">Import the SharePoint Online module with the following command:</span></span>
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

<span data-ttu-id="468ad-209">A opção _DisableNameChecking_ suprime esse aviso.</span><span class="sxs-lookup"><span data-stu-id="468ad-209">The  _DisableNameChecking_ switch suppresses this warning.</span></span>
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

<span data-ttu-id="468ad-p122">Para se conectar ao SharePoint Online, você precisa fornecer duas partes de informações: suas credenciais e a URL do site de administração do SharePoint Online. A parte de credenciais é fácil: já armazenamos que na variável `$credential` (consulte [etapa 2: criar um objeto de credenciais do Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). Para a URL do seu site de administração, que é fácil de determinar, também. Suponha que o seu nome de domínio do Office 365 é `litwareinc.onmicrosoft.com`.</span><span class="sxs-lookup"><span data-stu-id="468ad-p122">In order to connect to SharePoint Online, you need to supply two pieces of information: your credentials and the URL of your SharePoint Online admin site. The credentials part is easy: we've already stored that in the variable  `$credential` (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). As for the URL of your admin site, that's easy enough to determine, as well. Suppose your Office 365 domain name is  `litwareinc.onmicrosoft.com`.</span></span>
  
<span data-ttu-id="468ad-214">Para determinar a URL do site de administração, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="468ad-214">To determine the admin site URL, do this:</span></span>
  
1. <span data-ttu-id="468ad-215">Iniciar usando o prefixo `https://`.</span><span class="sxs-lookup"><span data-stu-id="468ad-215">Start by using the prefix  `https://`.</span></span>
    
2. <span data-ttu-id="468ad-p123">Adicione a parte de host de domínio do seu nome de domínio. Por exemplo, para `litwareinc.onmicrosoft.com`, o nome de host do domínio é `litwareinc`. Para `contoso.onmicrosoft.com`, o nome de host do domínio é `contoso`.</span><span class="sxs-lookup"><span data-stu-id="468ad-p123">Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.</span></span>
    
3. <span data-ttu-id="468ad-219">Adicione um hífen (-) seguido `admin.sharepoint.com`.</span><span class="sxs-lookup"><span data-stu-id="468ad-219">Add a hyphen (-) followed by  `admin.sharepoint.com`.</span></span>
    
<span data-ttu-id="468ad-220">Em outras palavras:</span><span class="sxs-lookup"><span data-stu-id="468ad-220">In other words:</span></span>
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
<span data-ttu-id="468ad-p124">Após ter construído a URL, em seguida, você pode usar essa URL e seu objeto de credenciais para se conectar ao SharePoint Online. Chame o cmdlet [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) , usando um comando semelhante a este.</span><span class="sxs-lookup"><span data-stu-id="468ad-p124">After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.</span></span>
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

<span data-ttu-id="468ad-223">Para verificar que a conexão foi feita, execute o seguinte comando no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="468ad-223">To verify that the connection has been made, run the following command in Windows PowerShell.</span></span>
  
```
Get-SPOSite
```

<span data-ttu-id="468ad-p125">Você deve obter uma lista de todos os sites do SharePoint Online. Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="468ad-p125">You should get a list of all your SharePoint Online sites. Here is an example:</span></span>
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

<span data-ttu-id="468ad-p126">Comandos do seu Office 365 (aqueles descrito em [etapa 3: conectar ao Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) será trabalho ainda. (Tente executar **Get-MsolUser**e veja por si mesmo). Isso significa que agora você pode gerenciar Office 365 e o SharePoint Online da mesma instância do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="468ad-p126">Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.</span></span>
  
### <a name="step-5-connect-to-skype-for-business-online"></a><span data-ttu-id="468ad-228">Etapa 5: Conectar-se ao Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="468ad-228">Step 5: Connect to Skype for Business Online</span></span>
<span data-ttu-id="468ad-229"><a name="Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-229"></span></span>

<span data-ttu-id="468ad-p127">Conectando a Skype para Business Online (e para o Exchange Online ou a segurança &amp; Centro de conformidade) é diferente de conectar-se ao Office 365 ou no SharePoint Online. Isso acontece porque o Skype para cmdlets Business Online e o Exchange Online não obter instalado no computador, semelhante a como o Office 365 e os cmdlets do SharePoint Online. Em vez disso, cada vez que entrar, os cmdlets apropriados são temporariamente copiados para seu computador. Quando você aprovar, esses cmdlets, em seguida, são removidos do seu computador.</span><span class="sxs-lookup"><span data-stu-id="468ad-p127">Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.</span></span>
  
<span data-ttu-id="468ad-p128">Para se conectar ao Skype para Business Online, você precisa importar o Skype para módulo Business Online. Para fazer isso, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="468ad-p128">In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.</span></span>
  
```
Import-Module SkypeOnlineConnector
```

<span data-ttu-id="468ad-236">Na primeira vez que fizer isso, você visualizará a seguinte mensagem de aviso, que pode ignorar com segurança.</span><span class="sxs-lookup"><span data-stu-id="468ad-236">The first time you do this, you might see the following warning message, which you can safely ignore.</span></span>
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

<span data-ttu-id="468ad-237">Depois que o módulo foi importado, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="468ad-237">After the module has been imported, run this command.</span></span>
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

<span data-ttu-id="468ad-p129">Criamos uma sessão PowerShell remota. Nesse caso, isso significa que podemos se conectou a uma instância do Windows PowerShell em execução em um dos servidores do Office 365.</span><span class="sxs-lookup"><span data-stu-id="468ad-p129">We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers.</span></span> 
  
<span data-ttu-id="468ad-p130">Embora que fizemos uma conexão para o Office 365, podemos ainda não baixou os scripts, cmdlets e outros itens necessários para gerenciar Skype para Business Online. Para fazer isso, temos que executar este comando.</span><span class="sxs-lookup"><span data-stu-id="468ad-p130">Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.</span></span>
  
```
Import-PSSession $sfboSession
```

<span data-ttu-id="468ad-242">Quando você importa a sessão do Windows PowerShell, você deverá ver uma barra de progresso semelhante ao seguinte, uma barra de progresso que emite um relatório sobre todos o Skype para Business Online cmdlets sendo importados para o seu computador.</span><span class="sxs-lookup"><span data-stu-id="468ad-242">When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.</span></span>
  
![Barra de progresso do Lync Online.](images/o365_powershell_lync_progress_bar.png)
  
<span data-ttu-id="468ad-244">Quando a barra de progresso desaparece, você deve então ver saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="468ad-244">When the progress bar disappears, you should then see output similar to the following.</span></span>
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a><span data-ttu-id="468ad-245">Etapa 6: Conectar-se ao Exchange Online</span><span class="sxs-lookup"><span data-stu-id="468ad-245">Step 6: Connect to Exchange Online</span></span>
<span data-ttu-id="468ad-246"><a name="Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-246"></span></span>

<span data-ttu-id="468ad-247">Execute este comando, que cria uma sessão remota do Windows PowerShell com o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="468ad-247">Run this command, which creates a remote Windows PowerShell session with Exchange Online.</span></span>
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> <span data-ttu-id="468ad-p131">Por que é o comando para conectar-se ao Exchange Online mais complicados do que o comando para conectar Skype para Business Online? Tecnicamente, não é: os dois comandos façam exatamente a mesma coisa. No entanto, o Skype para equipe Business Online criado seu próprio cmdlet — **New-CsOnlineSession** — que oculta alguns dos parâmetros (como _a autenticação_ e _AllowRedirection_) que são usados durante a conexão com o Exchange Online. Em vez de exigir que você digitar essa informação sozinho, os parâmetros de _autenticação_ e _AllowRedirection_ efetivamente são internos para o cmdlet **New-CsOnlineSession** . Você precisa digitar esses parâmetros durante a conexão com o Exchange Online, como o Exchange Online usa o cmdlet [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) padrão para se conectar ao Office 365. A desvantagem é que você tenha um pouco mais de digitação para fazer. A vantagem é que você não precisa baixar e instalar um módulo do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="468ad-p131">Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.</span></span>
  
<span data-ttu-id="468ad-255">Agora, tudo o que você deve fazer é importar nesta sessão remota, exatamente como fizemos com Skype para negócios Online.</span><span class="sxs-lookup"><span data-stu-id="468ad-255">All you have to do now is import this remote session, just like we did with Skype for Business Online.</span></span>
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

<span data-ttu-id="468ad-256">Você deve ver algo como o seguinte na tela.</span><span class="sxs-lookup"><span data-stu-id="468ad-256">You should see something similar to this on the screen.</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

<span data-ttu-id="468ad-257">Agora tente executar este comando:</span><span class="sxs-lookup"><span data-stu-id="468ad-257">Now try running this command.</span></span>
  
```
Get-AcceptedDomain
```

<span data-ttu-id="468ad-258">Em troca, você deverá ver informações sobre seus domínios do Office 365 que estiverem configurados para endereços de email no Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="468ad-258">In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.</span></span>
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a><span data-ttu-id="468ad-259">Etapa 7: Conectar à segurança &amp; Centro de conformidade</span><span class="sxs-lookup"><span data-stu-id="468ad-259">Step 7: Connect to the Security &amp; Compliance Center</span></span>
<span data-ttu-id="468ad-260"><a name="Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-260"></span></span>

<span data-ttu-id="468ad-p132">A segurança &amp; Centro de conformidade é um serviço no Office 365 que permite que você para gerenciar recursos de conformidade de um local. Para obter mais informações, consulte o [Centro de conformidade do Office 365](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span><span class="sxs-lookup"><span data-stu-id="468ad-p132">The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span></span>
  
<span data-ttu-id="468ad-263">As instruções de conexão para a segurança &amp; Centro de conformidade são muito semelhantes aos para Exchange Online, mas com um pouco, que você verá em breve.</span><span class="sxs-lookup"><span data-stu-id="468ad-263">The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.</span></span>
  
<span data-ttu-id="468ad-264">Execute este comando, que cria uma sessão PowerShell remota com a segurança &amp; Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="468ad-264">Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.</span></span>
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

<span data-ttu-id="468ad-265">Agora execute este comando:</span><span class="sxs-lookup"><span data-stu-id="468ad-265">Now run this command:</span></span>
  
```
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="468ad-p133">Novamente, esse comando é muito semelhante ao comando para o Exchange Online. A opção _DisableNameChecking_ não é necessária porque não há nenhum verbo não aprovado na segurança &amp; Centro de conformidade. Mas e quanto adicionais ou `-Prefix cc` parâmetro e valor? É o pouco que nós dissemos sobre.</span><span class="sxs-lookup"><span data-stu-id="468ad-p133">Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.</span></span>
  
<span data-ttu-id="468ad-p134">O Exchange Online e a segurança &amp; Centro de conformidade compartilhar alguns cmdlets que possuem exatamente os mesmos nomes e fornecer a mesma funcionalidade. **Get-RoleGroup** é um exemplo.</span><span class="sxs-lookup"><span data-stu-id="468ad-p134">Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.</span></span>
  
<span data-ttu-id="468ad-p135">O que acontece se você tentar importar duas sessões que contêm cmdlets com o mesmo nome? Eles entrarem em conflito. Você receberá uma mensagem de aviso amarelo ganhar que diz, `WARNING: Proxy creation has been skipped for the following command:` seguido pela lista de cmdlets conflitantes que não puderam ser importados. O resultado final? É possível executar **Get-RoleGroup** no Exchange Online porque você lá conectado pela primeira vez, mas não é possível executar **Get-RoleGroup** na segurança &amp; conformidade centraliza porque você lá conectado última e os cmdlets conflitantes recusou a ser importado.</span><span class="sxs-lookup"><span data-stu-id="468ad-p135">So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.</span></span>
  
<span data-ttu-id="468ad-p136">A maneira mais fácil para lidar com esse problema é adicionar um prefixo de texto arbitrário à segurança importada &amp; cmdlets do Centro de conformidade. Fizemos essa usando o parâmetro _Prefix_ com o valor "cc" no cmdlet **Import-PSSession** . O que que fazer para nós? Eliminava os conflitos alterando (ligeiramente) a segurança &amp; nomes de cmdlet do Centro de conformidade para esta sessão. Todas a segurança importada &amp; cmdlets do Centro de conformidade agora começar com "cc" no substantivo do nome do cmdlet (à direita do "-"). Por exemplo, o cmdlet **Get-RoleGroup** contenciosos torna-se **Get-ccRoleGroup** para a segurança &amp; Centro de conformidade para que ele não fique em conflito com **Get-RoleGroup** para Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="468ad-p136">The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.</span></span>
  
<span data-ttu-id="468ad-p137">A desvantagem?  *Todos os*  Segurança &amp; nomes de cmdlet do Centro de conformidade recebem o prefixo "cc" — mesmo exclusivos cmdlets que ele não é necessário. Por exemplo, **Get-ComplianceSearch** torna-se **Get-ccComplianceSearch** , mesmo que não haja nenhuma dessas cmdlet no Exchange Online. É um pouco de um problema, mas não é tão ruim ao considerar os benefícios do gerenciamento de todos os serviços do Office 365 em uma única sessão do Windows PowerShell. Lembre-se adicionar "cc" para os nomes de cmdlet para todos os procedimentos na segurança &amp; Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="468ad-p137">The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="468ad-288">Se tudo correr bem, você verá algo semelhante a isso:</span><span class="sxs-lookup"><span data-stu-id="468ad-288">If all goes well, you'll see something similar to this:</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

<span data-ttu-id="468ad-289">Agora você tem liberdade para gerenciar todos os serviços do Office 365 em uma única sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="468ad-289">Now you are free to manage all Office 365 services in a single Windows PowerShell session.</span></span>
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a><span data-ttu-id="468ad-290">Etapa 8: Encerrar normalmente suas sessões do PowerShell</span><span class="sxs-lookup"><span data-stu-id="468ad-290">Step 8: Gracefully end your PowerShell sessions</span></span>
<span data-ttu-id="468ad-291"><a name="Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-291"></span></span>

<span data-ttu-id="468ad-p138">Se você apenas fechar a janela do Windows PowerShell, sua Skype para conexão remota Business Online permanece ativa para os próximas 15 minutos ou mais. Porque Skype para Business Online limita o número de conexões simultâneas que qualquer pessoa ou qualquer um domínio pode ter aberto, que poderia ser um problema. Com Skype para Business Online, um administrador individual pode ter, no máximo, três conexões abertas de uma só vez, e um domínio pode ter um máximo de nove conexões abertas. Se você entrar no Skype para Business Online e saia sem fechar corretamente a sessão, essa sessão permanece aberta para os próximas 15 minutos ou mais. Como resultado, que é uma conexão menos disponível para você ou outros administradores em seu domínio.</span><span class="sxs-lookup"><span data-stu-id="468ad-p138">If you just close the Windows PowerShell window, your Skype for Business Online remote connection will remain active for the next 15 minutes or so. Because Skype for Business Online limits the number of simultaneous connections that any one person or any one domain can have open, that could be a problem. With Skype for Business Online, an individual administrator can have, at most, three open connections at one time, and a domain can have a maximum of nine open connections. If you sign in to Skype for Business Online and then exit without properly closing the session, that session remains open for the next 15 minutes or so. As a result, that's one fewer connection available to you or to other administrators in your domain.</span></span>
  
<span data-ttu-id="468ad-p139">Em vez disso, vamos fechar as sessões remotas para Skype para Business Online, o Exchange Online e a segurança &amp; conformidade centraliza normalmente. Antes de fazer isso, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="468ad-p139">Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.</span></span>
  
```
Get-PSSession
```

<span data-ttu-id="468ad-p140">O cmdlet [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) deve mostrar a você possui pelo menos três sessões remotas abrir, um para Skype para Business Online, um para o Exchange Online e outro para a segurança &amp; Centro de conformidade (é possível você poderia ter mais de três remota sessões em execução, dependendo se você usou esta instância do Windows PowerShell para se conectar ao algo diferente, além de serviços do Office 365). Você verá algo semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="468ad-p140">The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.</span></span>
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

<span data-ttu-id="468ad-p141">Para fechar a essas três sessões, execute estes comandos um de cada vez. O primeiro comando fecha o Skype para sessão Business Online, o segundo fecha a sessão do Exchange Online, e a terceira fecha a segurança &amp; sessão do Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="468ad-p141">To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.</span></span>
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

<span data-ttu-id="468ad-303">Se você executar o cmdlet **Get-PSSession** agora, você deverá ver nada nisso (a menos que você tenha outras conexões remotas ativas em funcionamento).</span><span class="sxs-lookup"><span data-stu-id="468ad-303">If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).</span></span>
  
![Console do Windows PowerShell com nenhuma sessão remota.](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> <span data-ttu-id="468ad-305">Se você preferir fechar todas as suas sessões remotas ao mesmo tempo, você pode usar este comando: >`Get-PSSession | Remove-PSSession`</span><span class="sxs-lookup"><span data-stu-id="468ad-305">If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`</span></span>
  
<span data-ttu-id="468ad-306">Caso você tente executar um cmdlet de qualquer uma dessas fechado sessões (por exemplo, **Get-CsMeetingConfiguration** no Skype para Business Online), você receberá uma mensagem de erro semelhante a este.</span><span class="sxs-lookup"><span data-stu-id="468ad-306">If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.</span></span>
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="468ad-307">Recebemos essa mensagem de erro porque os cmdlets do Skype para Business Online, o Exchange Online e a segurança &amp; Centro de conformidade foram excluídos quando fechamos as sessões remotas.</span><span class="sxs-lookup"><span data-stu-id="468ad-307">We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.</span></span>
  
<span data-ttu-id="468ad-308">Para fechar a sessão do SharePoint Online, digite este comando.</span><span class="sxs-lookup"><span data-stu-id="468ad-308">To close the SharePoint Online session, type this command.</span></span>
  
```
Disconnect-SPOService
```

<span data-ttu-id="468ad-309">Se você tentar executar o cmdlet **Get-SPOSite** agora, você receberá uma mensagem de erro semelhante a esta.</span><span class="sxs-lookup"><span data-stu-id="468ad-309">If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.</span></span>
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

<span data-ttu-id="468ad-310">Você não é possível recuperar as informações do site porque você não está conectado ao SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="468ad-310">You can't retrieve site information because you're no longer connected to SharePoint Online.</span></span>
  
<span data-ttu-id="468ad-p142">Às propriedades de sua conexão com o Office 365, embora não haja um cmdlet do **Connect-MsolService** , não há nenhum cmdlet de **Disconnect-MsolService** correspondente. Portanto para o Office 365, basta feche a janela do Windows PowerShell. No entanto, ainda é uma boa ideia fazer isso últimos, portanto você pode adequadamente desconectar do SharePoint Online, Skype para Business Online, o Exchange Online e a segurança &amp; Centro de conformidade.</span><span class="sxs-lookup"><span data-stu-id="468ad-p142">As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="new-to-office-365"></a><span data-ttu-id="468ad-314">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="468ad-314">New to Office 365?</span></span>
<span data-ttu-id="468ad-315"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="468ad-315"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="468ad-316">Veja também</span><span class="sxs-lookup"><span data-stu-id="468ad-316">See also</span></span>

#### 

[<span data-ttu-id="468ad-317">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="468ad-317">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="468ad-318">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="468ad-318">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="468ad-319">Gerenciar o SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="468ad-319">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="468ad-320">Gerenciar contas de usuário e licenças usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="468ad-320">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="468ad-321">Use o Windows PowerShell para criar relatórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="468ad-321">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

