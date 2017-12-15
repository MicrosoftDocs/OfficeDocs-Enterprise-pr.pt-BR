---
title: "Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "Resumo: Use o Windows PowerShell remoto para se conectar ao Exchange Online utilizando o parâmetro DelegatedOrg."
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Conectar-se aos locatários do Exchange Online com o Windows PowerShell remoto para parceiros com permissões de acesso delegado (DAP)

 **Resumo:** Use o Windows PowerShell remoto para se conectar ao Exchange Online usando o parâmetro _DelegatedOrg_ .
  
O Windows PowerShell remoto permite gerenciar as configurações do Exchange Online a partir da linha de comando. Use o Windows PowerShell em um computador local para criar uma sessão remota do Exchange Online. É um processo simples de três etapas em que você insere suas credenciais do Exchange Online, fornece as configurações de conexão necessárias e, em seguida, importa os cmdlets do Exchange Online para sua sessão local do Windows PowerShell de forma que possa usá-los.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

- Tempo estimado para conclusão: 5 minutos
    
- Você pode usar as seguintes versões do Windows:
    
  - Windows 10
    
  - Windows 8.1 ou Windows 8
    
  - Windows Server 2012 R2 ou Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * É necessário instalar o .NET Framework 4.5.1 ou o .NET Framework 4.5 e, em seguida, o Windows Management Framework 4.0 ou o Windows Management Framework 3.0. Para obter mais informações, confira os seguintes recursos:
    
  - [Instalando o .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) ou[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- Para saber mais sobre os atalhos de teclado que podem se aplicar aos procedimentos deste tópico, confira o artigo [Atalhos de teclado no Centro de administração do Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=534017).
    
## 

> [!IMPORTANT]
> Este procedimento se aplica apenas aosparceiros com permissão de acesso delegado (DAP). Se você não for um parceiro DAP, não use este procedimento. 
  
Os parceiros DAP são parceiros de agregação e Provedores de Soluções na Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas em suas ofertas de serviço aos respectivos clientes. Eles possuem uma locação de parceiro que recebe automaticamente permissões do tipo Administrar em nome de (AOBO) para as Office 365locações de clientes, de modo que possam administrar e relatar todas as locações dos clientes.
  
## <a name="connect-to-exchange-online"></a>Conectar-se ao Exchange Online

1. Abra o Windows PowerShell no computador local e execute o seguinte comando.
    
  ```
  $UserCredential = Get-Credential
  ```

    Na caixa de diálogo **Solicitação de Credenciais do Windows PowerShell**, digite seu nome de usuário e senha do administrador DAP e clique em **OK**.
    
2. Execute o seguinte comando, substituindo _<customer tenant domain name>_ com o nome do domínio locatário que você deseja se conectar.
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    A etapa principal deste comando especifica qual cliente acessar para obter as informações do relatório. Faça isso no parâmetro  _ConnectionURI_, no qual você fornece o FQDN do nome de domínio inicial como o valor para o parâmetro  _DelegatedOrg_. Isso informa ao Windows PowerShell remoto para o PowerShell remoto do Exchange OnlineWindows PowerShell o ponto de extremidade ao qual se conectar. O Windows PowerShell remoto deve se conectar ao relatório do Office 365 no contexto de um cliente específico, sempre que um relatório for executado. Depois de especificar esse cliente, todos os comandos a seguir serão executados no contexto desse cliente. Isso permite ao parceiro acessar os relatórios disponíveis para esse cliente.
    
3. execute o seguinte comando.
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> Há um limite de três sessões que podem ser executadas simultaneamente em uma conta. Quando concluir, verifique se desconectou a sessão do Windows PowerShell remoto. Quando você fecha a janela do Windows PowerShell sem desconectar a sessão, pode usar todas as sessões do Windows PowerShell remoto disponíveis; no entanto, será necessário aguardar a expiração das sessões. Para desconectar a sessão remota do Windows PowerShell, execute o seguinte comando. >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>Como saber se funcionou?

Após a etapa 3, os cmdlets do Exchange Online são importados para sua sessão local do Windows PowerShell e é possível acompanhar por uma barra de progresso. Se você não receber qualquer erro, se conectará com êxito. Execute um cmdlet do Exchange Online como um teste rápido; por exemplo, o **Get-Mailbox**, e confira os resultados.
  
Caso você receba erros, verifique os seguintes requisitos:
  
- Um problema comum é uma senha incorreta. Execute as três etapas novamente e preste muita atenção ao nome de usuário e à senha inseridos na Etapa 1.
    
- Para ajudar a evitar os ataques de Negação de Serviço (DoS), você está limitado a três conexões do Windows PowerShell remoto abertas para sua organização do Exchange Online.
    
- O Windows PowerShell deve ser configurado para executar scripts. Você só precisa definir essa configuração uma vez em seu computador, e não sempre que se conectar. Para habilitar o Windows PowerShell para executar scripts assinados, execute o seguinte comando em uma janela elevada do Windows PowerShell (uma janela do Windows PowerShell que você abriu ao selecionar a opção **Executar como administrador**).
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- A conta que você usa para se conectar ao Exchange Online deve estar habilitada para o Windows PowerShell remoto. Para saber mais, confira o artigo [Gerenciar o Acesso ao PowerShell Remoto no Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- O tráfego da porta TCP 80 precisa estar aberto entre seu computador local e o Exchange Online. Provavelmente ele está aberto, mas é algo a ser considerado caso a sua organização tenha uma política de acesso à Internet restritiva.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Chamar o cmdlet diretamente com Invoke-Command

A importação de uma sessão do Windows PowerShell remoto pode ser um processo demorado, pois ela carrega todos os cmdlets do Exchange Online. Isso pode ser um problema no processamento em lotes; por exemplo, quando você executa relatórios ou faz alterações em massa em diversos locatários. Como uma alternativa ao uso do **Import-PSSession**, chame os cmdlets que deseja usar diretamente com o **Invoke-Command**. Por exemplo, para chamar o cmdlet **get-mailbox**, substitua essa sintaxe para `Import-PSSession $Session`.
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>Mais cmdlets de relatórios

Os cmdlets usados neste tópico são os cmdlets do Windows PowerShell. Para saber mais sobre esses cmdlets, confira os tópicos a seguir:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

