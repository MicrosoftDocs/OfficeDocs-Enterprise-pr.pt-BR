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
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)

> [!IMPORTANT]
> The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic. 
  
Os parceiros DAP são parceiros de agregação e Provedores de Soluções na Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas em suas ofertas de serviço aos respectivos clientes. Eles possuem uma locação de parceiros que recebe automaticamente as permissões de administração em nome de (AOBO) para o seu cliente da Microsoft 365 locações, para que possam administrar e relatar todos os seus locações clientes.

Os parceiros DAP podem usar o Exchange Online PowerShell para gerenciar as configurações do Exchange Online do cliente e obter relatórios do Microsoft 365 a partir da linha de comando. Use o Windows PowerShell em seu computador local para criar uma sessão do PowerShell remoto para o Exchange Online. É um processo simples de três etapas onde você insere suas credenciais, fornece as configurações de conexão necessárias e, em seguida, importa os cmdlets do Exchange Online para a sua sessão local do Windows PowerShell, para que você possa usá-las.

> [!NOTE]
> DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

- Tempo estimado para conclusão: 5 minutos

- Você pode usar as seguintes versões do Windows:
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 ou Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1) <sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  Para permitir que todos os scripts do PowerShell que você baixar da Internet sejam assinados por um fornecedor confiável, execute o seguinte comando em uma janela elevada do Windows PowerShell (uma janela do Windows PowerShell que você abre selecionando **Executar como administrador**):

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  Você só precisa definir essa configuração uma vez em seu computador, e não sempre que se conectar.

- Para saber mais sobre os atalhos de teclado que podem se aplicar aos procedimentos deste tópico, confira o artigo [Atalhos de teclado no Centro de administração do Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=534017).

## <a name="connect-to-exchange-online-for-customer-organizations"></a>Conectar ao Exchange Online para organizações do cliente

1. Em seu computador local, abra o Windows PowerShell e execute o comando a seguir.
    
    ```
    $UserCredential = Get-Credential
    ```

    Na caixa de diálogo **Solicitação de Credenciais do Windows PowerShell**, digite seu nome de usuário e senha do administrador DAP e clique em **OK**.
    
2. Substitua _\<customer tenant domain name\>_ pelo nome do domínio do locatário ao qual você deseja se conectar e execute o seguinte comando:
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    A etapa principal deste comando especifica qual cliente acessar para obter as informações do relatório. Isso é feito no parâmetro _ConnectionURI_ , onde você fornece o FQDN do nome de domínio inicial como o valor para `?DelegatedOrg=` . Esse valor indica o ponto de extremidade correto do PowerShell do Exchange Online para se conectar. O PowerShell remoto deve se conectar aos relatórios do Microsoft 365 no contexto de um cliente específico cada vez que um relatório é executado. Depois de se conectar ao PowerShell do Exchange Online, todos os comandos subsequentes são executados no contexto do cliente, que oferece acesso a todos os relatórios disponíveis para o cliente.
    
3. Execute o seguinte comando.
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>Como saber se funcionou?

After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.
  
Caso você receba erros, verifique os seguintes requisitos:
  
- A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.
    
- The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Chamar o cmdlet diretamente com Invoke-Command

Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Mais cmdlets de relatórios

The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

