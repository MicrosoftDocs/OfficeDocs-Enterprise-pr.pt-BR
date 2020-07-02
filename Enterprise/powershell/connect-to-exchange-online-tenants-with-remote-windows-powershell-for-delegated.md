---
title: Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 'Resumo: use o Windows PowerShell remoto para se conectar ao Exchange Online utilizando o valor DelegatedOrg.'
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997367"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="666d2-103">Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="666d2-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

> [!IMPORTANT]
> <span data-ttu-id="666d2-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span><span class="sxs-lookup"><span data-stu-id="666d2-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span></span> <span data-ttu-id="666d2-105">If you aren't a DAP partner, don't use the procedures in this topic.</span><span class="sxs-lookup"><span data-stu-id="666d2-105">If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="666d2-106">Os parceiros DAP são parceiros de agregação e Provedores de Soluções na Nuvem (CSP).</span><span class="sxs-lookup"><span data-stu-id="666d2-106">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="666d2-107">Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas.</span><span class="sxs-lookup"><span data-stu-id="666d2-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="666d2-108">Eles reúnem assinaturas em suas ofertas de serviço aos respectivos clientes.</span><span class="sxs-lookup"><span data-stu-id="666d2-108">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="666d2-109">Eles possuem uma locação de parceiros que recebe automaticamente as permissões de administração em nome de (AOBO) para o seu cliente da Microsoft 365 locações, para que possam administrar e relatar todos os seus locações clientes.</span><span class="sxs-lookup"><span data-stu-id="666d2-109">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="666d2-110">Os parceiros DAP podem usar o Exchange Online PowerShell para gerenciar as configurações do Exchange Online do cliente e obter relatórios do Microsoft 365 a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="666d2-110">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="666d2-111">Use o Windows PowerShell em seu computador local para criar uma sessão do PowerShell remoto para o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="666d2-111">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="666d2-112">É um processo simples de três etapas onde você insere suas credenciais, fornece as configurações de conexão necessárias e, em seguida, importa os cmdlets do Exchange Online para a sua sessão local do Windows PowerShell, para que você possa usá-las.</span><span class="sxs-lookup"><span data-stu-id="666d2-112">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="666d2-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="666d2-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span></span> <span data-ttu-id="666d2-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span><span class="sxs-lookup"><span data-stu-id="666d2-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="666d2-115">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="666d2-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="666d2-116">Tempo estimado para conclusão: 5 minutos</span><span class="sxs-lookup"><span data-stu-id="666d2-116">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="666d2-117">Você pode usar as seguintes versões do Windows:</span><span class="sxs-lookup"><span data-stu-id="666d2-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="666d2-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="666d2-118">Windows 10</span></span>

  - <span data-ttu-id="666d2-119">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="666d2-119">Windows 8.1</span></span>

  - <span data-ttu-id="666d2-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="666d2-120">Windows Server 2016</span></span>

  - <span data-ttu-id="666d2-121">Windows Server 2012 ou Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="666d2-121">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="666d2-122">Windows 7 Service Pack 1 (SP1) <sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="666d2-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="666d2-123">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="666d2-123">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="666d2-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span><span class="sxs-lookup"><span data-stu-id="666d2-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span></span> <span data-ttu-id="666d2-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span><span class="sxs-lookup"><span data-stu-id="666d2-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="666d2-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span><span class="sxs-lookup"><span data-stu-id="666d2-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span></span> <span data-ttu-id="666d2-127">You'll get the following error when you try to connect:</span><span class="sxs-lookup"><span data-stu-id="666d2-127">You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="666d2-128">Para permitir que todos os scripts do PowerShell que você baixar da Internet sejam assinados por um fornecedor confiável, execute o seguinte comando em uma janela elevada do Windows PowerShell (uma janela do Windows PowerShell que você abre selecionando **Executar como administrador**):</span><span class="sxs-lookup"><span data-stu-id="666d2-128">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="666d2-129">Você só precisa definir essa configuração uma vez em seu computador, e não sempre que se conectar.</span><span class="sxs-lookup"><span data-stu-id="666d2-129">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="666d2-130">Para saber mais sobre os atalhos de teclado que podem se aplicar aos procedimentos deste tópico, confira o artigo [Atalhos de teclado no Centro de administração do Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span><span class="sxs-lookup"><span data-stu-id="666d2-130">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="666d2-131">Conectar ao Exchange Online para organizações do cliente</span><span class="sxs-lookup"><span data-stu-id="666d2-131">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="666d2-132">Em seu computador local, abra o Windows PowerShell e execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="666d2-132">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="666d2-133">Na caixa de diálogo **Solicitação de Credenciais do Windows PowerShell**, digite seu nome de usuário e senha do administrador DAP e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="666d2-133">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="666d2-134">Substitua _\<customer tenant domain name\>_ pelo nome do domínio do locatário ao qual você deseja se conectar e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="666d2-134">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="666d2-135">A etapa principal deste comando especifica qual cliente acessar para obter as informações do relatório.</span><span class="sxs-lookup"><span data-stu-id="666d2-135">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="666d2-136">Isso é feito no parâmetro _ConnectionURI_ , onde você fornece o FQDN do nome de domínio inicial como o valor para `?DelegatedOrg=` .</span><span class="sxs-lookup"><span data-stu-id="666d2-136">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="666d2-137">Esse valor indica o ponto de extremidade correto do PowerShell do Exchange Online para se conectar.</span><span class="sxs-lookup"><span data-stu-id="666d2-137">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="666d2-138">O PowerShell remoto deve se conectar aos relatórios do Microsoft 365 no contexto de um cliente específico cada vez que um relatório é executado.</span><span class="sxs-lookup"><span data-stu-id="666d2-138">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="666d2-139">Depois de se conectar ao PowerShell do Exchange Online, todos os comandos subsequentes são executados no contexto do cliente, que oferece acesso a todos os relatórios disponíveis para o cliente.</span><span class="sxs-lookup"><span data-stu-id="666d2-139">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="666d2-140">Execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="666d2-140">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="666d2-141">There's a limit of three simultaneous sessions that can run under one account.</span><span class="sxs-lookup"><span data-stu-id="666d2-141">There's a limit of three simultaneous sessions that can run under one account.</span></span> <span data-ttu-id="666d2-142">Be sure to disconnect the remote PowerShell session when you're finished.</span><span class="sxs-lookup"><span data-stu-id="666d2-142">Be sure to disconnect the remote PowerShell session when you're finished.</span></span> <span data-ttu-id="666d2-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span><span class="sxs-lookup"><span data-stu-id="666d2-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span></span> <span data-ttu-id="666d2-144">To disconnect the remote PowerShell session, run the following command:</span><span class="sxs-lookup"><span data-stu-id="666d2-144">To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="666d2-145">Como saber se funcionou?</span><span class="sxs-lookup"><span data-stu-id="666d2-145">How do you know this worked?</span></span>

<span data-ttu-id="666d2-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span><span class="sxs-lookup"><span data-stu-id="666d2-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span></span> <span data-ttu-id="666d2-147">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="666d2-147">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="666d2-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span><span class="sxs-lookup"><span data-stu-id="666d2-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="666d2-149">Caso você receba erros, verifique os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="666d2-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="666d2-150">A common problem is an incorrect password.</span><span class="sxs-lookup"><span data-stu-id="666d2-150">A common problem is an incorrect password.</span></span> <span data-ttu-id="666d2-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span><span class="sxs-lookup"><span data-stu-id="666d2-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="666d2-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="666d2-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span></span> <span data-ttu-id="666d2-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="666d2-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="666d2-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="666d2-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span></span> <span data-ttu-id="666d2-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span><span class="sxs-lookup"><span data-stu-id="666d2-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="666d2-156">Chamar o cmdlet diretamente com Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="666d2-156">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="666d2-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span><span class="sxs-lookup"><span data-stu-id="666d2-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span></span> <span data-ttu-id="666d2-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span><span class="sxs-lookup"><span data-stu-id="666d2-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span></span> <span data-ttu-id="666d2-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="666d2-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span></span> <span data-ttu-id="666d2-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span><span class="sxs-lookup"><span data-stu-id="666d2-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="666d2-161">Mais cmdlets de relatórios</span><span class="sxs-lookup"><span data-stu-id="666d2-161">More reporting cmdlets</span></span>

<span data-ttu-id="666d2-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span><span class="sxs-lookup"><span data-stu-id="666d2-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span></span> <span data-ttu-id="666d2-163">For more information about these cmdlets, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="666d2-163">For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="666d2-164">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="666d2-164">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="666d2-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="666d2-165">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="666d2-166">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="666d2-166">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="666d2-167">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="666d2-167">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="666d2-168">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="666d2-168">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

