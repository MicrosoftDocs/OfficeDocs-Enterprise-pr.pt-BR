---
title: Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Resumo: Use o Windows PowerShell remoto para se conectar ao Exchange Online utilizando o parâmetro DelegatedOrg.'
ms.openlocfilehash: d8cbb6640419ba2f1de868ae88b0a273c3f71ae7
ms.sourcegitcommit: f3f81d2c2e8290948d93f3f787a679c804840256
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="e5b2f-103">Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="e5b2f-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="e5b2f-104">**Resumo:** use o Windows PowerShell remoto para se conectar ao Exchange Online utilizando o parâmetro _DelegatedOrg_.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="e5b2f-p101">O Windows PowerShell remoto permite gerenciar as configurações do Exchange Online a partir da linha de comando. Use o Windows PowerShell em um computador local para criar uma sessão remota do Exchange Online. É um processo simples de três etapas em que você insere suas credenciais do Exchange Online, fornece as configurações de conexão necessárias e, em seguida, importa os cmdlets do Exchange Online para sua sessão local do Windows PowerShell de forma que possa usá-los.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="e5b2f-108">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="e5b2f-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="e5b2f-109">Tempo estimado para conclusão: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="e5b2f-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="e5b2f-110">Você pode usar as seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="e5b2f-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="e5b2f-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="e5b2f-111">Windows 10</span></span>
    
  - <span data-ttu-id="e5b2f-112">Windows 8.1 ou Windows 8</span><span class="sxs-lookup"><span data-stu-id="e5b2f-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="e5b2f-113">Windows Server 2012 R2 ou Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e5b2f-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="e5b2f-114">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="e5b2f-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="e5b2f-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="e5b2f-115">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="e5b2f-p102">\* É necessário instalar o .NET Framework 4.5.1 ou o .NET Framework 4.5 e, em seguida, o Windows Management Framework 4.0 ou o Windows Management Framework 3.0. Para saber mais, confira os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p102">\*You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
    - [<span data-ttu-id="e5b2f-118">Instalando o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e5b2f-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
    - <span data-ttu-id="e5b2f-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="e5b2f-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="e5b2f-120">Para saber mais sobre os atalhos de teclado que podem se aplicar aos procedimentos deste tópico, confira o artigo [Atalhos de teclado no Centro de administração do Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="e5b2f-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="e5b2f-p103">Este procedimento se aplica apenas aosparceiros com permissão de acesso delegado (DAP). Se você não for um parceiro DAP, não use este procedimento.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="e5b2f-p104">Os parceiros DAP são parceiros de agregação e Provedores de Soluções na Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas em suas ofertas de serviço aos respectivos clientes. Eles possuem uma locação de parceiro que recebe automaticamente permissões do tipo Administrar em nome de (AOBO) para as Office 365locações de clientes, de modo que possam administrar e relatar todas as locações dos clientes.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="e5b2f-127">Conectar-se ao Exchange Online</span><span class="sxs-lookup"><span data-stu-id="e5b2f-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="e5b2f-128">Em seu computador local, abra o Windows PowerShell e execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="e5b2f-129">Na caixa de diálogo **Solicitação de Credenciais do Windows PowerShell**, digite seu nome de usuário e senha do administrador DAP e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="e5b2f-130">Execute o comando a seguir, substituindo o _<customer tenant domain name>_ pelo nome de domínio do locatário ao qual você deseja se conectar.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="e5b2f-p105">A etapa principal deste comando especifica qual cliente acessar para obter as informações do relatório. Faça isso no parâmetro  _ConnectionURI_, no qual você fornece o FQDN do nome de domínio inicial como o valor para o parâmetro  _DelegatedOrg_. Isso informa ao Windows PowerShell remoto para o PowerShell remoto do Exchange OnlineWindows PowerShell o ponto de extremidade ao qual se conectar. O Windows PowerShell remoto deve se conectar ao relatório do Office 365 no contexto de um cliente específico, sempre que um relatório for executado. Depois de especificar esse cliente, todos os comandos a seguir serão executados no contexto desse cliente. Isso permite ao parceiro acessar os relatórios disponíveis para esse cliente.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="e5b2f-137">Execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="e5b2f-p106">Há um limite de três sessões que podem ser executadas simultaneamente em uma conta. Quando concluir, verifique se desconectou a sessão do Windows PowerShell remoto. Quando você fecha a janela do Windows PowerShell sem desconectar a sessão, pode usar todas as sessões do Windows PowerShell remoto disponíveis; no entanto, será necessário aguardar a expiração das sessões. Para desconectar a sessão remota do Windows PowerShell, execute o seguinte comando. >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="e5b2f-142">Como saber se funcionou?</span><span class="sxs-lookup"><span data-stu-id="e5b2f-142">How do you know this worked?</span></span>

<span data-ttu-id="e5b2f-p107">Após a etapa 3, os cmdlets do Exchange Online são importados para sua sessão local do Windows PowerShell e é possível acompanhar por uma barra de progresso. Se você não receber qualquer erro, se conectará com êxito. Execute um cmdlet do Exchange Online como um teste rápido; por exemplo, o **Get-Mailbox**, e confira os resultados.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="e5b2f-146">Caso você receba erros, verifique os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="e5b2f-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="e5b2f-p108">Um problema comum é uma senha incorreta. Execute as três etapas novamente e preste muita atenção ao nome de usuário e à senha inseridos na Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="e5b2f-149">Para ajudar a evitar os ataques de Negação de Serviço (DoS), você está limitado a três conexões do Windows PowerShell remoto abertas para sua organização do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="e5b2f-p109">O Windows PowerShell deve ser configurado para executar scripts. Você só precisa definir essa configuração uma vez em seu computador, e não sempre que se conectar. Para habilitar o Windows PowerShell para executar scripts assinados, execute o seguinte comando em uma janela elevada do Windows PowerShell (uma janela do Windows PowerShell que você abriu ao selecionar a opção **Executar como administrador**).</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="e5b2f-p110">A conta que você usa para se conectar ao Exchange Online deve estar habilitada para o Windows PowerShell remoto. Para saber mais, confira o artigo [Gerenciar o Acesso ao PowerShell Remoto no Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="e5b2f-p111">O tráfego da porta TCP 80 precisa estar aberto entre seu computador local e o Exchange Online. Provavelmente ele está aberto, mas é algo a ser considerado caso a sua organização tenha uma política de acesso à Internet restritiva.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="e5b2f-157">Chamar o cmdlet diretamente com Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e5b2f-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="e5b2f-p112">A importação de uma sessão do Windows PowerShell remoto pode ser um processo demorado, pois ela carrega todos os cmdlets do Exchange Online. Isso pode ser um problema no processamento em lotes; por exemplo, quando você executa relatórios ou faz alterações em massa em diversos locatários. Como uma alternativa ao uso do **Import-PSSession**, chame os cmdlets que deseja usar diretamente com o **Invoke-Command**. Por exemplo, para chamar o cmdlet **get-mailbox**, substitua essa sintaxe para `Import-PSSession $Session`.</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="e5b2f-162">Mais cmdlets de relatórios</span><span class="sxs-lookup"><span data-stu-id="e5b2f-162">More reporting cmdlets</span></span>

<span data-ttu-id="e5b2f-p113">Os cmdlets usados neste tópico são os cmdlets do Windows PowerShell. Para saber mais sobre esses cmdlets, confira os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="e5b2f-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="e5b2f-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="e5b2f-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="e5b2f-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e5b2f-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="e5b2f-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="e5b2f-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="e5b2f-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="e5b2f-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="e5b2f-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="e5b2f-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

