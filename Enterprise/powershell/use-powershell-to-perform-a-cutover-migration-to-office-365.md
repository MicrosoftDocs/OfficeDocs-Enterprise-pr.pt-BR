---
title: Usar o PowerShell para realizar uma migração de substituição para o Office 365
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 'Resumo: Saiba como usar o Windows PowerShell para executar uma migração de substituição para o Office 365.'
ms.openlocfilehash: db2782faac86e53ffd4d2794ee77d53605c9484e
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193681"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>Usar o PowerShell para realizar uma migração de substituição para o Office 365

 **Resumo:** saiba como usar o Windows PowerShell para executar uma migração de substituição para o Office 365.
  
Você pode migrar o conteúdo de caixas de correio de um sistema de email de origem para o Office 365 de uma só vez usando uma migração de substituição. Este artigo apresenta as tarefas para uma migração de substituição de email usando o PowerShell do Exchange Online. 
  
Examinando o tópico [O que você precisa saber sobre uma migração de substituição de email para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), você pode obter uma visão geral do processo de migração. Quando você estiver familiarizado com o conteúdo daquele artigo, use este para começar a migrar caixas de correio de um sistema de email para outro.
  
> [!NOTE]
> Você também pode usar o Centro de administração do Exchange para executar a migração de substituição. Confira [Realizar uma migração de substituição de email para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

Tempo estimado para a conclusão da tarefa: 2 a 5 minutos para criar um lote de migração. Depois que o lote de migração é iniciado, a duração da migração irá variar com base no número de caixas de correio no lote, no tamanho de cada caixa de correio e na sua capacidade de rede disponível. Para saber mais sobre outros fatores que afetam o tempo de migração de caixas de correio para o Office 365, confira [Desempenho de migração](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Para executar esses procedimentos, você precisa receber permissões. Para saber quais permissões são necessárias, confira a entrada "Migração" em uma tabela no tópico [Permissões de destinatários](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Para usar os cmdlets do PowerShell do Exchange Online, você precisa entrar e importar os cmdlets para sua sessão local do Windows PowerShell. Confira [Conectar-se ao Exchange Online usando o PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obter instruções.
  
Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Etapas da migração

### <a name="step-1-prepare-for-a-cutover-migration"></a>Etapa 1: preparar para uma migração de transferência
<a name="BK_Step1"> </a>

- **Adicione sua organização do Exchange no local como um domínio aceito da organização do Office 365.** O serviço de migração usa o endereço SMTP das caixas de correio no local a fim de criar a ID e o endereço de email do usuário do Microsoft Online Services para as novas caixas de correio do Office 365. A migração apresentará falha se o domínio do Exchange não for um domínio aceito ou o domínio principal da organização do Office 365. Para saber mais, confira[Verificar seu domínio no Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Configure o Outlook em Qualquer Lugar no servidor Exchange no local** O serviço de migração de email usa o RPC sobre HTTP ou o Outlook em Qualquer Lugar para se conectar ao servidor do Exchange no local. Para saber mais sobre como configurar o Outlook em Qualquer Lugar para Exchange 2010, Exchange 2007 e Exchange 2003, confira o seguinte:
    
  - [Exchange 2010: Habilitar o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007: Como Habilitar o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003: Cenários de implantação para RPC sobre HTTP](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Como Configurar o Outlook em Qualquer Lugar com o Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > Sua configuração do Outlook em Qualquer Lugar deve ser configurada com um certificado emitido por uma autoridade de certificação (AC) confiável. Ele não pode ser configurado com um certificado autoassinado. Para saber mais, confira [Como configurar o SSL para o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
- **Verifique se você pode se conectar à organização do Exchange usando o Outlook em Qualquer Lugar** Experimente um destes métodos para testar suas configurações de conexão:
    
  - Use o Microsoft Outlook de fora da rede corporativa para se conectar à sua caixa de correio do Exchange no local.
    
  - Use o [Analisador de Conectividade Remota do Microsoft Exchange](https://www.testexchangeconnectivity.com/) para testar suas configurações de conexão. Use o Outlook em Qualquer Lugar (RPC sobre HTTP) ou testes de descoberta automática do Outlook.
    
  - Execute os comandos a seguir no PowerShell do Exchange Online.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Atribuir as permissões necessárias para acessar caixas de correio em sua organização do Exchange de uma conta de usuário local.** A conta de usuário local que você usa para se conectar à sua organização do Exchange local (também chamada de administrador de migração) deve ter as permissões necessárias para acessar as caixas de correio local que você deseja migrar para o Office 365. Esta conta de usuário é usada para criar um ponto de extremidade de migração para sua organização local.
    
    A lista a seguir mostra os privilégios administrativos necessários para migrar caixas de correio usando uma migração de transferência. Existem três opções possíveis.
    
  - O administrador de migração deve ser membro do grupo **Administradores de Domínio** no Active Directory na organização local.
    
    Ou
    
  - O administrador de migração deve ser atribuído a permissão **FullAccess** para cada caixa de correio local.
    
    Ou
    
  - O administrador de migração deve ser atribuído a permissão **Receber como** no banco de dados da caixa de correio local que armazena as caixas de correio do usuário.
    
- **Desabilite a Unificação de Mensagens.** Se as caixas de correio locais que você está migrando estiverem habilitadas para a UM (Unificação de Mensagens), será necessário desabilitar a UM nas caixas de correio antes de migrá-las. Em seguida, você poderá habilitar a UM nas caixas de correio depois que a migração for concluída.
    
- **Grupos de segurança e delegados** Este serviço de migração de emails não consegue detectar se grupos locais do Active Directory são grupos de segurança ou não e, portanto, não pode provisionar qualquer grupo migrado como grupo de segurança para o Office 365. Se quiser ter grupos de segurança em seu locatário do Office 365, será necessário provisionar um grupo de segurança habilitado para email vazio em seu locatário do Office 365 antes de iniciar a migração de transferência. Além disso, esse método de migração só move caixas de correio, usuários de email, contatos de email e grupos habilitados para email. Se qualquer outro objeto do Active Directory, como um usuário que não tenha sido migrado para o Office 365, for atribuído como um gerente ou delegado para um objeto que está sendo migrado, ele deverá ser removido do objeto antes da migração.
    
### <a name="step-2-create-a-migration-endpoint"></a>Etapa 2: criar um ponto de extremidade de migração
<a name="BK_Step2"> </a>

Para migrar o email com êxito, o Office 365 precisa se conectar e se comunicar com o sistema de email de origem. Para fazer isso, o Office 365 usa um ponto de extremidade de migração. Para criar um ponto de extremidade de migração do Outlook em Qualquer Lugar para a migração de substituição, primeiro [conecte-se ao Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Execute os seguintes comandos no PowerShell do Exchange Online:
  
```
$Credentials = Get-Credential
```

O exemplo usa o cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) para obter e testar as configurações de conexão ao servidor do Exchange local e usa essas configurações de conexão para criar o ponto de extremidade de migração chamado "CutoverEndpoint".
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> O cmdlet **New-MigrationEndpoint** pode ser usado para especificar um banco de dados do serviço a usar, utilizando a opção **-TargetDatabase**. Caso contrário, o banco de dados é atribuído de forma aleatória do site do Serviços de Federação do Active Directory (AD FS) 2.0, no qual a caixa de correio de gerenciamento está localizada.
  
#### <a name="verify-it-worked"></a>Verifique se funcionou

No PowerShell do Exchange Online, execute o seguinte comando para exibir informações sobre o ponto de extremidade de migração "CutoverEndpoint":
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Etapa 3: criar o lote de migração de transferência
<a name="BK_Step3"> </a>

Você pode usar o cmdlet **New-MigrationBatch** no PowerShell do Exchange Online para criar um lote de migração de uso em uma migração de transferência. É possível criar um lote de migração e iniciá-lo automaticamente incluindo o parâmetro _AutoStart_. Como alternativa, você pode criar o lote de migração e iniciá-lo manualmente mais tarde usando o cmdlet **Start-MigrationBatch**. Este exemplo cria um lote de migração chamado "CutoverBatch" e utiliza o ponto de extremidade de migração criado na etapa anterior.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

Este exemplo também cria um lote de migração chamado "CutoverBatch" e utiliza o ponto de extremidade de migração criado na etapa anterior. Como o parâmetro  _AutoStart_ não está incluído, o lote de migração deve ser iniciado manualmente no painel de migração ou usando o cmdlet **Start-MigrationBatch**. Como dito anteriormente, apenas um lote de migração de transferência pode existir de cada vez.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Verifique se funcionou

Para verificar se você criou com êxito um lote de migração para uma migração de substituição, execute o seguinte comando no PowerShell do Exchange Online para exibir informações sobre o novo lote de migração:
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Etapa 4: iniciar o lote de migração de transferência
<a name="BK_Step4"> </a>

Para iniciar o lote de migração no PowerShell do Exchange Online, execute o seguinte comando. Isso criará um lote de migração chamado "CutoverBatch".
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Verifique se funcionou

Se um lote de migração for iniciado com êxito, seu status no painel de migração será especificado como Sincronizando. Para verificar se você iniciou com êxito um lote de migração usando o PowerShell do Exchange Online, execute o seguinte comando:
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>Etapa 5: Rotear o email para o Office 365
<a name="BK_Step5"> </a>

Os sistemas de email usam um registro DNS chamado de registro MX para descobrir onde entregar os emails. Durante o processo de migração de email, seu registro MX estava apontando para o sistema de email de origem. Agora que a migração de email para o Office 365 foi concluída, é hora de apontar seu registro MX para o Office 365. Isso ajuda a garantir que o email seja entregue a suas caixas de correio do Office 365. Movendo o registro MX, você também poderá desativar seu sistema de email antigo quando estiver pronto. 
  
Para muitos provedores DNS, existem instruções específicas para [alterar seu registro MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Se seu provedor DNS não estiver incluído ou se você desejar ter uma noção das instruções gerais, [instruções gerais sobre o registro MX ](https://go.microsoft.com/fwlink/?LinkId=397449) também são fornecidas.
  
Pode levar até 72 horas para que os sistemas de email de seus clientes e parceiros reconheçam o registro MX alterado. Aguarde pelo menos 72 horas antes de prosseguir para a próxima tarefa: [Etapa 6: excluir o lote de migração de transferência](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>Etapa 6: excluir o lote de migração de transferência
<a name="Bk_step6"> </a>

Depois de alterar o registro MX e verificar se todos os emails estão sendo roteados para as caixas de correio do Office 365, notifique os usuários de que seus emails estão indo para o Office 365. Depois disso, você pode excluir o lote de migração de substituição. Antes de excluir o lote de migração, verifique os itens a seguir.
  
- Todos os usuários estão usando caixas de correio do Office 365. Depois que o lote for excluído, os emails enviados às caixas de correio no servidor Exchange local não serão copiados para as caixas de correio correspondentes do Office 365.
    
- As caixas de correio do Office 365 foram sincronizadas pelo menos uma vez depois que os emails começaram a ser enviados diretamente a elas. Para fazer isso, verifique se o valor na caixa Hora da Última Sincronização para o lote de migração é mais recente do que quando o email começou a ser roteado diretamente para as caixas de correio do Office 365.
    
Para excluir o lote de migração "CutoverBatch" no PowerShell do Exchange Online, execute o seguinte comando:
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Seção 7: atribuir licenças de usuários
<a name="BK_Step7"> </a>

 **Ative as contas de usuário do Office 365 para as contas migradas atribuindo licenças.** Se você não atribuir uma licença, a caixa de correio será desabilitada quando terminar o período de carência (30 dias). Para atribuir uma licença no Centro de administração do Office 365, confira[Atribuir ou cancelar a atribuição de licenças para o Office 365 para empresas](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Etapa 8: concluir tarefas pós-migração
<a name="BK_Step8"> </a>

- **Crie um registro DNS de Descoberta Automática para que os usuários possam facilmente acessar suas caixas de correio.** Após todas as caixas de correio locais serem migradas para o Office 365, você pode configurar um registro DNS de Descoberta Automática para sua organização do Office 365 e habilitar os usuários a se conectarem facilmente a suas novas caixas de correio do Office 365 com o Outlook e clientes móveis. Esse novo registro DNS de descoberta automática tem que usar o mesmo namespace que você usar para a organização do Office 365. Por exemplo, se seu namespace baseado em nuvem for cloud.contoso.com, o registro DNS de Descoberta Automática a ser criado será autodiscover.cloud.contoso.com.
    
    Se mantiver seu servidor Exchange, você também deverá verificar se o registro DNS CNAME de Descoberta Automática aponta para o Office 365 no DNS interno e externo após a migração para que o cliente do Outlook se conecte à caixa de correio correta.
    
    > [!NOTE]
    >  No Exchange 2007, Exchange 2010 e no Exchange 2013, você também deve definir o  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` como `Null`. 
  
    O Office 365 usa um registro CNAME para implementar o serviço Descoberta Automática para o Outlook e para clientes móveis. O registro CNAME de Descoberta Automática deve conter as seguintes informações:
    
  - **Alias:** descoberta automática
    
  - **Destino:** autodiscover.outlook.com
    
    Para saber mais, confira [Criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Desativar servidores locais do Exchange.** Depois de verificar se todos os emails estão sendo roteados diretamente para as caixas de correio do Office 365 e quando você não precisar mais manter sua organização de email local ou não planejar implementar uma solução de SSO (logon único), você poderá desinstalar o Exchange de seus servidores e remover sua organização local do Exchange.
    
    Para obter mais informações, confira o seguinte:
    
  - [Modificar ou remover o Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Como remover uma Organização do Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Como desinstalar o Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

