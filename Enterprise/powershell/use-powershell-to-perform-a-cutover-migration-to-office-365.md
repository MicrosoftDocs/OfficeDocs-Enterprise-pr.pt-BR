---
title: Usar o PowerShell para realizar uma migração de substituição para o Office 365
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
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
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 'Resumo: Saiba como usar o Windows PowerShell para executar uma migração de substituição para o Office 365.'
ms.openlocfilehash: b40c6ac53a173f700c6b931781d98d7965a2be7c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998566"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>Usar o PowerShell para realizar uma migração de substituição para o Office 365

You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell. 
  
By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.
  
> [!NOTE]
> You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.
  
To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.
  
Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Etapas da migração

### <a name="step-1-prepare-for-a-cutover-migration"></a>Etapa 1: preparar para uma migração de transferência
<a name="BK_Step1"> </a>

- **Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:
    
  - [Exchange 2010: Habilitar o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007: Como Habilitar o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003: Cenários de implantação para RPC sobre HTTP](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Como Configurar o Outlook em Qualquer Lugar com o Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
- **Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:
    
  - Use o Microsoft Outlook de fora da rede corporativa para se conectar à sua caixa de correio do Exchange no local.
    
  - Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.
    
  - Execute os comandos a seguir no PowerShell do Exchange Online.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Atribua as permissões necessárias a uma conta de usuário local para acessar caixas de correio em sua organização do Exchange.** A conta de usuário local que você usa para se conectar à sua organização local do Exchange (também chamada de administrador de migração) deve ter as permissões necessárias para acessar as caixas de correio locais que você deseja migrar para o Office 365. Essa conta de usuário é usada para criar um ponto de extremidade de migração para a sua organização local.
    
    The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.
    
  - O administrador de migração deve ser membro do grupo **Administradores de Domínio** no Active Directory na organização local.
    
    Ou
    
  - O administrador de migração deve ser atribuído a permissão **FullAccess** para cada caixa de correio local.
    
    Ou
    
  - O administrador de migração deve ser atribuído a permissão **Receber como** no banco de dados da caixa de correio local que armazena as caixas de correio do usuário.
    
- **Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.
    
- **Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.
    
### <a name="step-2-create-a-migration-endpoint"></a>Etapa 2: criar um ponto de extremidade de migração
<a name="BK_Step2"> </a>

To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
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
> The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.
  
#### <a name="verify-it-worked"></a>Verifique se funcionou

No PowerShell do Exchange Online, execute o seguinte comando para exibir informações sobre o ponto de extremidade de migração "CutoverEndpoint":
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Etapa 3: criar o lote de migração de transferência
<a name="BK_Step3"> </a>

You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.
  
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

To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Verifique se funcionou

If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>Etapa 5: Rotear o email para o Office 365
<a name="BK_Step5"> </a>

Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready. 
  
For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.
  
It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>Etapa 6: excluir o lote de migração de transferência
<a name="Bk_step6"> </a>

After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.
  
- All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.
    
- Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.
    
Para excluir o lote de migração "CutoverBatch" no PowerShell do Exchange Online, execute o seguinte comando:
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Seção 7: atribuir licenças de usuários
<a name="BK_Step7"> </a>

 **Ative as contas de usuário do Office 365 para as contas migradas atribuindo licenças.** Se você não atribuir uma licença, a caixa de correio será desabilitada quando o período de cortesia terminar (30 dias). Para atribuir uma licença no centro de administração do Microsoft 365, confira[atribuir ou cancelar a atribuição de licenças para o Office 365 para empresas](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Etapa 8: concluir tarefas pós-migração
<a name="BK_Step8"> </a>

- **Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.
    
    Se mantiver seu servidor Exchange, você também deverá verificar se o registro DNS CNAME de Descoberta Automática aponta para o Office 365 no DNS interno e externo após a migração para que o cliente do Outlook se conecte à caixa de correio correta.
    
    > [!NOTE]
    >  No Exchange 2007, Exchange 2010 e no Exchange 2013, você também deve definir o  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` como `Null`. 
  
    Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:
    
  - **Alias:** descoberta automática
    
  - **Destino:** autodiscover.outlook.com
    
    Para saber mais, confira [Criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.
    
    Para obter mais informações, confira o seguinte:
    
  - [Modificar ou remover o Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Como remover uma Organização do Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Como desinstalar o Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

