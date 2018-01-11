---
title: "Usar o PowerShell para realizar uma migração em estágios para o Office 365"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: "Resumo: Saiba como usar o Windows PowerShell para executar uma migração em estágios para o Office 365."
ms.openlocfilehash: 5143b039937389d965386de0e09f4f59db071c86
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>Usar o PowerShell para realizar uma migração em estágios para o Office 365

 **Resumo:** saiba como usar o Windows PowerShell para executar uma migração em estágios para o Office 365.
  
Você pode migrar o conteúdo de caixas de correio de usuários de um sistema de email de origem para o Office 365 ao longo do tempo usando uma migração em estágios.
  
Este artigo o orienta ao longo das tarefas envolvidas para uma migração em estágios de email usando o PowerShell do Exchange Online. O tópico [O que você precisa saber sobre uma migração de email em estágios para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487) fornece uma visão geral do processo de migração. Quando você estiver familiarizado com o conteúdo daquele artigo, use este para começar a migrar caixas de correio de um sistema de email para outro.
  
> [!NOTE]
> Você também pode usar o Centro de administração do Exchange para executar a migração em estágios. Confira [Realizar uma migração em estágios de email para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

Tempo estimado para a conclusão da tarefa: 2 a 5 minutos para criar um lote de migração. Depois que o lote de migração é iniciado, a duração da migração irá variar com base no número de caixas de correio no lote, no tamanho de cada caixa de correio e na sua capacidade de rede disponível. Para saber mais sobre outros fatores que afetam o tempo de migração de caixas de correio para o Office 365, confira [Desempenho de migração](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Para executar esses procedimentos, você precisa receber permissões. Para ver quais são as permissões necessárias, confira a entrada "Migração" no tópico [Permissões de destinatários](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Para usar os cmdlets do PowerShell do Exchange Online, você precisa entrar e importar os cmdlets para sua sessão local do Windows PowerShell. Confira [Conectar-se ao Exchange Online usando o PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obter instruções.
  
Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Etapas da migração

### <a name="step-1-prepare-for-a-staged-migration"></a>Etapa 1: preparar para uma migração em estágios

Antes de migrar as caixas de correio para o Office 365 usando uma migração em estágios, há algumas alterações que você deve fazer em seu ambiente do Exchange.
  
 **Configurar o Outlook em Qualquer Lugar em seu Exchange Server** local O serviço de migração de email usa o Outlook em Qualquer Lugar (também conhecido como RPC sobre HTTP) para se conectar a seu Exchange Server local. Para saber mais sobre como configurar o Outlook em Qualquer Lugar para o Exchange Server 2007 e para o Exchange 2003, confira o seguinte:
  
- [Exchange 2007: Como Habilitar o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Como configurar o Outlook em Qualquer Lugar com o Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> Você deve usar um certificado emitido por uma AC (autoridade de certificação) confiável com sua configuração do Outlook em Qualquer Lugar. O Outlook em Qualquer Lugar não pode ser configurado com um certificado autoassinado. Para saber mais, confira [Como configurar o SSL para o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=80875) 
  
 **Opcional: Verifique se você pode se conectar à sua organização do Exchange usando o Outlook em Qualquer Lugar** Tente um dos métodos a seguir para testar as configurações de conexão.
  
- Use o Outlook fora de sua rede corporativa para se conectar a sua caixa de correio local do Exchange.
    
- Use o [Analisador de Conectividade Remota do Microsoft Exchange]((https://www.testexchangeconnectivity.com/)) para testar as configurações de conexão. Use o Outlook em Qualquer Lugar (RPC sobre HTTP) ou os testes de descoberta automática do Outlook.
    
- Execute os seguintes comandos no PowerShell do Exchange Online:
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Definir permissões** A conta de usuário local que você usa para se conectar à sua organização local do Exchange (também chamada de administrador de migração) deve ter as permissões necessárias para acessar e modificar as caixas de correio locais que você deseja migrar para o Office 365. Essa conta de usuário é usada quando você se conecta a seu sistema de email criando um ponto de extremidade de migração, mais adiante neste procedimento ([Etapa 3: criar um ponto de extremidade de migração](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)).
  
Para migrar as caixas de correio, o administrador deve ter um dos seguintes conjuntos de permissão:
  
- Ser membro do grupo **Administradores de Domínio** no Active Directory na organização local.
    
    ou
    
- Ter a permissão **FullAccess** para cada caixa de correio local e a permissão **WriteProperty** para modificar a propriedade **TargetAddress** nas contas de usuário locais.
    
    ou
    
- Ter a permissão **Receive As** no banco de dados de caixa de correio local que armazena as caixas de correio do usuário e a permissão **WriteProperty** para modificar a propriedade **TargetAddress** nas contas de usuário locais.
    
Para obter instruções sobre como definir essas permissões, confira [Atribuir permissões para migrar caixas de correio para o Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).
  
 **Desabilitar a UM (Unificação de Mensagens)** Se a UM estiver habilitada para as caixas de correio locais que você está migrando, desabilite a UM antes da migração. Habilite a UM para as caixas de correio após a conclusão da migração. Para obter instruções, confira[desabilitar a unificação de mensagens](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Use a sincronização de diretório para criar novos usuários no Office 365.** Você usa a sincronização de diretório para criar todos os usuários locais em sua organização do Office 365.
  
Você precisa licenciar os usuários depois que eles são criados. O prazo é de 30 dias para adicionar licenças depois que os usuários são criados. Para obter as etapas para adicionar licenças, confira [Etapa 8: concluir tarefas pós-migração](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Você pode usar a Ferramenta de Sincronização do Microsoft Azure Active Directory ou o AAD Sync (Serviços de Sincronização do Microsoft Azure Active Directory) para sincronizar e criar seus usuários locais no Office 365. Depois que as caixas de correio são migradas para o Office 365, você gerencia as contas de usuário em sua organização local e elas são sincronizadas com sua organização do Office 365. Para saber mais, confira[Integração de diretórios](https://go.microsoft.com/fwlink/?LinkId=521788) .
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Etapa 2: criar um arquivo CSV para um lote de migração em estágios

Depois de identificar os usuários cujas caixas de correio locais você deseja migrar para o Office 365, use um arquivo CSV (de valores separados por vírgula) para criar um lote de migração. Cada linha no arquivo CSV, usado pelo Office 365 para executar a migração, contém informações sobre uma caixa de correio local. 
  
> [!NOTE]
> Não há um limite para o número de caixas de correio que você pode migrar para o Office 365 usando uma migração em estágios. No entanto, o arquivo CSV de um lote de migração pode conter no máximo 2.000 linhas. Para migrar mais de 2.000 caixas de correio, crie arquivos CSV adicionais e use cada arquivo para criar um novo lote de migração. 
  
 **Atributos com suporte**
  
O arquivo CSV para uma migração em estágios dá suporte aos três atributos a seguir. Cada linha no arquivo CSV corresponde a uma caixa de correio e deve conter um valor para cada um desses atributos.
  
|**Atributo**|**Descrição**|**Obrigatório?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Especifica o endereço de email SMTP principal, por exemplo, laurac@contoso.com, para caixas de correio locais.  <br/> Use o endereço SMTP principal para caixas de correio locais, e não IDs de usuário do Office 365. Por exemplo, se o domínio local se chamar contoso.com, mas o domínio de email do Office 365 se chamar service.contoso.com, você usará o nome de domínio contoso.com para endereços de email no arquivo CSV.  <br/> |Obrigatório  <br/> |
|Senha  <br/> |A senha a ser definida para a nova caixa de correio do Office 365. As restrições de senha aplicadas à sua organização do Office 365 também são aplicáveis às senhas incluídas no arquivo CSV.  <br/> |Opcional  <br/> |
|ForceChangePassword  <br/> |Especifica se um usuário deve alterar a senha na primeira vez que entrar em sua nova caixa de correio do Office 365. Use **True** ou **False** para o valor desse parâmetro. <br/> > [!NOTE]> Se você implementou uma solução de SSO (Logon Único) com a implantação do AD FS (Serviços de Federação do Active Directory) em sua organização local, deve usar **False** para o valor do atributo **ForceChangePassword**.          |Opcional  <br/> |
   
 **Formato de arquivo CSV**
  
Aqui está um exemplo do formato do arquivo CSV. Neste exemplo, três caixas de correio locais são migradas para o Office 365.
  
A primeira linha, ou linha de cabeçalho, do arquivo CSV lista os nomes dos atributos ou campos especificados nas linhas a seguir. Cada nome de atributo é separado por uma vírgula.
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Cada linha embaixo da linha de cabeçalho representa um usuário e fornece as informações que serão utilizadas para migrar a caixa de correio dele. Os valores de atributo em cada linha devem estar na mesma ordem que os nomes dos atributos na linha de cabeçalho. 
  
Use qualquer editor de texto ou um aplicativo como o Excel para criar o arquivo CSV. Salve-o como um arquivo .csv ou .txt.
  
> [!NOTE]
> Se o arquivo CSV contiver caracteres não-ASCII ou especiais, salve-o com UTF-8 ou outra codificação Unicode. Dependendo do aplicativo, salvar o arquivo CSV com UTF-8 ou outra codificação Unicode pode ser mais fácil quando a localidade do sistema do computador corresponde ao idioma usado no arquivo CSV. 
  
### <a name="step-3-create-a-migration-endpoint"></a>Etapa 3: criar um ponto de extremidade de migração
<a name="BK_Endpoint"> </a>

Para migrar o email com êxito, o Office 365 precisa se conectar e se comunicar com o sistema de email de origem. Para fazer isso, o Office 365 usa um ponto de extremidade de migração. A fim de criar um ponto de extremidade de migração do Outlook em Qualquer Lugar usando o PowerShell, para a migração em estágios, primeiro [conecte-se ao Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Para criar um ponto de extremidade de migração do Outlook em Qualquer Lugar chamado "StagedEndpoint" no PowerShell do Exchange Online, execute os seguintes comandos:
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Para saber mais sobre o cmdlet **New-MigrationEndpoint**, confira[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).
  
> [!NOTE]
> O cmdlet **New-MigrationEndpoint** pode ser usado para especificar um banco de dados do serviço a usar, utilizando a opção **-TargetDatabase**. Caso contrário, o banco de dados é atribuído de forma aleatória do site do Serviços de Federação do Active Directory (AD FS) 2.0, no qual a caixa de correio de gerenciamento está localizada.
  
#### <a name="verify-it-worked"></a>Verifique se funcionou

No PowerShell do Exchange Online, execute o seguinte comando para exibir informações sobre o ponto de extremidade de migração "StagedEndpoint":
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Etapa 4: criar e iniciar um lote de migração em estágios
<a name="BK_Endpoint"> </a>

Você pode usar o cmdlet **New-MigrationBatch** no PowerShell do Exchange Online para criar um lote de migração de uso em uma migração de transferência. É possível criar um lote de migração e iniciá-lo automaticamente incluindo o parâmetro _AutoStart_. Como alternativa, você pode criar o lote de migração e iniciá-lo manualmente mais tarde usando o cmdlet **Start-MigrationBatch**. Este exemplo cria um lote de migração chamado "StagedBatch1" e utiliza o ponto de extremidade de migração criado na etapa anterior.
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

Este exemplo também cria um lote de migração chamado "StagedBatch1" e utiliza o ponto de extremidade de migração criado na etapa anterior. Como o parâmetro  _AutoStart_ não está incluído, o lote de migração deve ser iniciado manualmente no painel de migração ou usando o cmdlet **Start-MigrationBatch**. Como dito anteriormente, apenas um lote de migração de transferência pode existir de cada vez.
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Verifique se funcionou

Execute o seguinte comando no PowerShell do Exchange Online para exibir informações sobre o "StagedBatch1":
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Você também pode verificar se o lote foi iniciado executando o seguinte comando:
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Para saber mais sobre o cmdlet **Get-MigrationBatch**, confira[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Etapa 5: converter caixas de correio locais em usuários habilitados para email
<a name="BK_Endpoint"> </a>

Depois de migrar com êxito um lote de caixas de correio, é necessário permitir que os usuários acessem suas mensagens de alguma forma. Um usuário cuja caixa de correio foi migrada agora tem uma caixa de correio local e outra no Office 365. Os usuários que tiverem uma caixa de correio no Office 365 deixarão de receber novas mensagens na caixa de correio local. 
  
Como não concluiu suas migrações, você ainda não está pronto para direcionar todos os usuários para o Office 365 e seus emails. Então, o que fazer com as pessoas que têm ambas? Você pode alterar as caixas de correio locais que já migrou para usuários habilitados para email. Ao mudar de uma caixa de correio para um usuário habilitado para email, você pode direcionar o usuário para o Office 365 para acessar o email em vez de ir para a caixa de correio local. 
  
Outro motivo importante para converter as caixas de correio locais em usuários habilitados para email é manter os endereços proxy das caixas de correio do Office 365 copiando endereços proxy para usuários habilitados para email. Isso permite que você gerencie os usuários baseados em nuvem de sua organização local utilizando o Active Directory. Além disso, se você decidir desprogramar sua organização do Exchange Server local após todas as caixas de correio serem migradas para o Office 365, os endereços de proxy que você copiou para os usuários habilitados para email permanecerão em seu Active Directory local.
  
Para saber mais e para baixar os scripts que você pode executar para converter as caixas de correio em usuários habilitados para email, confira o seguinte:
  
- [Converter caixas de correio do Exchange 2007 em usuários habilitados para email](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [Converter caixas de correio do Exchange 2003 em usuários habilitados para email](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a>Etapa 6: excluir um lote de migração em estágios
<a name="BK_Endpoint"> </a>

 Após todas as caixas de correio em um lote de migração terem migrado com êxito e você ter convertido as caixas de correio locais no lote em usuários habilitados para email, tudo está pronto para excluir um lote de migração em estágios. Verifique se o email está sendo encaminhado para as caixas de correio do Office 365 no lote de migração. Ao excluir um lote de migração em estágios, o serviço de migração limpa todos os registros relacionados ao lote e o exclui.
  
Para excluir o lote de migração "StagedBatch1" no PowerShell do Exchange Online, execute o comando a seguir.
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

Para saber mais sobre o cmdlet **Remove-MigrationBatch**, confira[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Verifique se funcionou

Execute o seguinte comando no PowerShell do Exchange Online para exibir informações sobre o "IMAPBatch1":
  
```
Get-MigrationBatch StagedBatch1
```

O comando retornará o lote de migração com um status de **Removing** ou retornará um erro afirmando que o lote de migração não foi encontrado, confirmando que o lote foi excluído.
  
Para saber mais sobre o cmdlet **Get-MigrationBatch**, confira[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step7-assign-licenses-to-office-365-users"></a>Etapa7: atribuir licenças aos usuários do Office 365
<a name="BK_Endpoint"> </a>

Ative as contas de usuário do Office 365 para as contas migradas atribuindo licenças. Se você não atribuir uma licença, a caixa de correio será desabilitada quando terminar o período de carência (30 dias). Para atribuir uma licença no Centro de administração do Office 365, confira [Atribuir ou cancelar a atribuição de licenças para o Office 365 para empresas](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Etapa 8: concluir tarefas pós-migração
<a name="BK_Postmigration"> </a>

- **Crie um registro DNS de Descoberta Automática para que os usuários possam facilmente acessar suas caixas de correio.**Após todas as caixas de correio locais serem migradas para o Office 365, você pode configurar um registro DNS de Descoberta Automática para sua organização do Office 365 e habilitar os usuários a se conectarem facilmente a suas novas caixas de correio do Office 365 com o Outlook e clientes móveis. Esse novo registro DNS de descoberta automática tem que usar o mesmo namespace que você usar para a organização do Office 365. Por exemplo, se seu namespace baseado em nuvem for cloud.contoso.com, o registro DNS de Descoberta Automática a ser criado será autodiscover.cloud.contoso.com.
    
    O Office 365 usa um registro CNAME para implementar o serviço Descoberta Automática para o Outlook e para clientes móveis. O registro CNAME de Descoberta Automática deve conter as seguintes informações:
    
  - **Alias:** descoberta automática
    
  - **Destino:** autodiscover.outlook.com
    
    Para saber mais, confira [Criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Desativar servidores locais do Exchange.** Depois de verificar se todos os emails estão sendo roteados diretamente para as caixas de correio do Office 365 e quando você não precisar mais manter sua organização de email local ou não planejar implementar uma solução SSO, você poderá desinstalar o Exchange de seus servidores e remover sua organização local do Exchange.
    
    Para obter mais informações, confira o seguinte:
    
  - [Modificar ou remover o Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Como remover uma Organização do Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Como desinstalar o Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    
