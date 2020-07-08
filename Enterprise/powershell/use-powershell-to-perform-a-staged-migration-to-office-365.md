---
title: Usar o PowerShell para realizar uma migração em estágios para o Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 'Resumo: Saiba como usar o Windows PowerShell para executar uma migração em estágios para o Office 365.'
ms.openlocfilehash: ca50edd079e17808c46ff5a956ed2efad34eb322
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052554"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>Usar o PowerShell para realizar uma migração em estágios para o Office 365

Você pode migrar o conteúdo de caixas de correio de usuários de um sistema de email de origem para o Office 365 ao longo do tempo usando uma migração em estágios.
  
This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.
  
> [!NOTE]
> You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.
  
To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.
  
Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Etapas da migração

### <a name="step-1-prepare-for-a-staged-migration"></a>Etapa 1: preparar para uma migração em estágios

Antes de migrar as caixas de correio para o Office 365 usando uma migração em estágios, há algumas alterações que você deve fazer em seu ambiente do Exchange.
  
 **Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:
  
- [Exchange 2007: Como Habilitar o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Como configurar o Outlook em Qualquer Lugar com o Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
 **Opcional: Verifique se você pode se conectar à sua organização do Exchange usando o Outlook em Qualquer Lugar** Tente um dos métodos a seguir para testar as configurações de conexão.
  
- Use o Outlook fora de sua rede corporativa para se conectar a sua caixa de correio local do Exchange.
    
- Use o [analisador de conectividade remota da Microsoft](https://https://testconnectivity.microsoft.com/) para testar suas configurações de conexão. Use o Outlook em Qualquer Lugar (RPC sobre HTTP) ou os testes de Descoberta Automática do Outlook.
    
- Execute os seguintes comandos no PowerShell do Exchange Online:
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).
  
Para migrar as caixas de correio, o administrador deve ter um dos seguintes conjuntos de permissão:
  
- Ser membro do grupo **Administradores de Domínio** no Active Directory na organização local.
    
    ou
    
- Ter a permissão **FullAccess** para cada caixa de correio local e a permissão **WriteProperty** para modificar a propriedade **TargetAddress** nas contas de usuário locais.
    
    ou
    
- Ter a permissão **Receive As** no banco de dados de caixa de correio local que armazena as caixas de correio do usuário e a permissão **WriteProperty** para modificar a propriedade **TargetAddress** nas contas de usuário locais.
    
Para obter instruções sobre como definir essas permissões, confira [Atribuir permissões para migrar caixas de correio para o Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).
  
 **Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.
  
You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Você pode usar a ferramenta de sincronização do Microsoft Azure Active Directory (Azure AD) ou os serviços de sincronização do Microsoft Azure AD para sincronizar e criar seus usuários locais no Office 365. Depois que as caixas de correio são migradas para o Office 365, você gerencia contas de usuário em sua organização local e elas estão sincronizadas com a organização do Office 365. Para obter mais informações, consulte[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Etapa 2: criar um arquivo CSV para um lote de migração em estágios

After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox. 
  
> [!NOTE]
> There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch. 
  
 **Atributos com suporte**
  
The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.
  
|**Atributo**|**Descrição**|**Obrigatório?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Especifica o endereço de email SMTP principal, por exemplo, laurac@contoso.com, para caixas de correio locais.  <br/> Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.  <br/> |Obrigatório  <br/> |
|Senha  <br/> |The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.  <br/> |Opcional  <br/> |
|ForceChangePassword  <br/> |Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. <br/> > [!NOTE]> Se você implementou uma solução de SSO (Logon Único) com a implantação do AD FS (Serviços de Federação do Active Directory) em sua organização local, deve usar **False** para o valor do atributo **ForceChangePassword**.          |Opcional  <br/> |
   
 **Formato de arquivo CSV**
  
Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.
  
The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row. 
  
Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.
  
> [!NOTE]
> If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file. 
  
### <a name="step-3-create-a-migration-endpoint"></a>Etapa 3: criar um ponto de extremidade de migração
<a name="BK_Endpoint"> </a>

To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Para criar um ponto de extremidade de migração do Outlook em Qualquer Lugar chamado "StagedEndpoint" no PowerShell do Exchange Online, execute os seguintes comandos:
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Para saber mais sobre o cmdlet **New-MigrationEndpoint**, confira[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).
  
> [!NOTE]
> The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.
  
#### <a name="verify-it-worked"></a>Verifique se funcionou

No PowerShell do Exchange Online, execute o seguinte comando para exibir informações sobre o ponto de extremidade de migração "StagedEndpoint":
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Etapa 4: criar e iniciar um lote de migração em estágios
<a name="BK_Endpoint"> </a>

You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Verifique se funcionou

Execute o seguinte comando no PowerShell do Exchange Online para exibir informações sobre o "StagedBatch1":
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Você também pode verificar se o lote foi iniciado executando o seguinte comando:
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Para saber mais sobre o cmdlet **Get-MigrationBatch**, confira[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Etapa 5: converter caixas de correio locais em usuários habilitados para email
<a name="BK_Endpoint"> </a>

After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox. 
  
Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox. 
  
Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.
    
### <a name="step-6-delete-a-staged-migration-batch"></a>Etapa 6: excluir um lote de migração em estágios
<a name="BK_Endpoint"> </a>

 After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.
  
Para excluir o lote de migração "StagedBatch1" no PowerShell do Exchange Online, execute o comando a seguir.
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Para saber mais sobre o cmdlet **Remove-MigrationBatch**, confira[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Verifique se funcionou

Execute o seguinte comando no PowerShell do Exchange Online para exibir informações sobre o "IMAPBatch1":
  
```powershell
Get-MigrationBatch StagedBatch1
```

O comando retornará o lote de migração com um status de **Removing** ou retornará um erro afirmando que o lote de migração não foi encontrado, confirmando que o lote foi excluído.
  
Para saber mais sobre o cmdlet **Get-MigrationBatch**, confira[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step7-assign-licenses-to-office-365-users"></a>Etapa7: atribuir licenças aos usuários do Office 365
<a name="BK_Endpoint"> </a>

Ative as contas de usuário do Office 365 para as contas migradas atribuindo licenças. Se você não atribuir uma licença, a caixa de correio será desabilitada quando terminar o período de cortesia (30 dias). Para atribuir uma licença no centro de administração do Microsoft 365, confira [Atribuir ou cancelar atribuição de licenças para o Office 365 para empresas](https://go.microsoft.com/fwlink/?LinkId=536681).
  
### <a name="step-8-complete-post-migration-tasks"></a>Etapa 8: concluir tarefas pós-migração
<a name="BK_Postmigration"> </a>

- **Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.
    
    Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:
    
  - **Alias:** descoberta automática
    
  - **Destino:** autodiscover.outlook.com
    
    Para saber mais, confira [Criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.
    
    Para obter mais informações, confira o seguinte:
    
  - [Modificar ou remover o Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Como remover uma Organização do Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Como desinstalar o Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

