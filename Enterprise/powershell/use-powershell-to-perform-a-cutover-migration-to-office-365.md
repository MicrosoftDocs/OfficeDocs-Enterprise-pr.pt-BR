---
title: "Usar o PowerShell para realizar uma migração de substituição para o Office 365"
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: "Resumo: Saiba como usar o Windows PowerShell para executar uma migração de substituição para o Office 365."
ms.openlocfilehash: 8181d59f53464034a584724dcb53956976c917dd
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="cc4c9-103">Usar o PowerShell para realizar uma migração de substituição para o Office 365</span><span class="sxs-lookup"><span data-stu-id="cc4c9-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

 <span data-ttu-id="cc4c9-104">**Resumo:** saiba como usar o Windows PowerShell para executar uma migração de substituição para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-104">**Summary:** Learn how to use Windows PowerShell to perform a cutover migration to Office 365.</span></span>
  
<span data-ttu-id="cc4c9-p101">Você pode migrar o conteúdo de caixas de correio de um sistema de email de origem para o Office 365 de uma só vez usando uma migração de substituição. Este artigo apresenta as tarefas para uma migração de substituição de email usando o PowerShell do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p101">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="cc4c9-p102">Examinando o tópico [O que você precisa saber sobre uma migração de substituição de email para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), você pode obter uma visão geral do processo de migração. Quando você estiver familiarizado com o conteúdo daquele artigo, use este para começar a migrar caixas de correio de um sistema de email para outro.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p102">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cc4c9-p103">Você também pode usar o Centro de administração do Exchange para executar a migração de substituição. Confira [Realizar uma migração de substituição de email para o Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p103">You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="cc4c9-111">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="cc4c9-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="cc4c9-p104">Tempo estimado para a conclusão da tarefa: 2 a 5 minutos para criar um lote de migração. Depois que o lote de migração é iniciado, a duração da migração irá variar com base no número de caixas de correio no lote, no tamanho de cada caixa de correio e na sua capacidade de rede disponível. Para saber mais sobre outros fatores que afetam o tempo de migração de caixas de correio para o Office 365, confira [Desempenho de migração](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p104">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="cc4c9-p105">Para executar esses procedimentos, você precisa receber permissões. Para saber quais permissões são necessárias, confira a entrada "Migração" em uma tabela no tópico [Permissões de destinatários](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="cc4c9-p106">Para usar os cmdlets do PowerShell do Exchange Online, você precisa entrar e importar os cmdlets para sua sessão local do Windows PowerShell. Confira [Conectar-se ao Exchange Online usando o PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obter instruções.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="cc4c9-119">Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="cc4c9-120">Etapas da migração</span><span class="sxs-lookup"><span data-stu-id="cc4c9-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="cc4c9-121">Etapa 1: preparar para uma migração de transferência</span><span class="sxs-lookup"><span data-stu-id="cc4c9-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="cc4c9-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="cc4c9-122"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="cc4c9-p107">**Adicione sua organização do Exchange no local como um domínio aceito da organização do Office 365.** O serviço de migração usa o endereço SMTP das caixas de correio no local a fim de criar a ID e o endereço de email do usuário do Microsoft Online Services para as novas caixas de correio do Office 365. A migração apresentará falha se o domínio do Exchange não for um domínio aceito ou o domínio principal da organização do Office 365. Para saber mais, confira[Verificar seu domínio no Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p107">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="cc4c9-p108">**Configure o Outlook em Qualquer Lugar no servidor Exchange no local** O serviço de migração de email usa o RPC sobre HTTP ou o Outlook em Qualquer Lugar para se conectar ao servidor do Exchange no local. Para saber mais sobre como configurar o Outlook em Qualquer Lugar para Exchange 2010, Exchange 2007 e Exchange 2003, confira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="cc4c9-130">Exchange 2010: Habilitar o Outlook em Qualquer Lugar</span><span class="sxs-lookup"><span data-stu-id="cc4c9-130">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="cc4c9-131">Exchange 2007: Como Habilitar o Outlook em Qualquer Lugar</span><span class="sxs-lookup"><span data-stu-id="cc4c9-131">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="cc4c9-132">Exchange 2003: Cenários de implantação para RPC sobre HTTP</span><span class="sxs-lookup"><span data-stu-id="cc4c9-132">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="cc4c9-133">Como Configurar o Outlook em Qualquer Lugar com o Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="cc4c9-133">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="cc4c9-p109">Sua configuração do Outlook em Qualquer Lugar deve ser configurada com um certificado emitido por uma autoridade de certificação (AC) confiável. Ele não pode ser configurado com um certificado autoassinado. Para saber mais, confira [Como configurar o SSL para o Outlook em Qualquer Lugar](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="cc4c9-p110">**Verifique se você pode se conectar à organização do Exchange usando o Outlook em Qualquer Lugar** Experimente um destes métodos para testar suas configurações de conexão:</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="cc4c9-139">Use o Microsoft Outlook de fora da rede corporativa para se conectar à sua caixa de correio do Exchange no local.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="cc4c9-p111">Use o [Analisador de Conectividade Remota do Microsoft Exchange](https://www.testexchangeconnectivity.com/) para testar suas configurações de conexão. Use o Outlook em Qualquer Lugar (RPC sobre HTTP) ou testes de descoberta automática do Outlook.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="cc4c9-142">Execute os comandos a seguir no PowerShell do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-142">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="cc4c9-p112">**Atribua as permissões necessárias a uma conta de usuário local para acessar caixas de correio em sua organização do Exchange.** A conta de usuário local que você usa para conectar-se à organização do Exchange no local (também chamada deadministrador de migração) deve ter as permissões necessárias para acessar as caixas de correio no local que você deseja migrar para o Office 365. Essa conta de usuário é usada para criar um ponto de extremidade de migração para a sua organização local.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p112">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.** The on-premises user account that you use to connect to your on-premises Exchange organization (also called themigration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="cc4c9-p113">A lista a seguir mostra os privilégios administrativos necessários para migrar caixas de correio usando uma migração de transferência. Existem três opções possíveis.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="cc4c9-148">O administrador de migração deve ser membro do grupo **Administradores de Domínio** no Active Directory na organização local.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="cc4c9-149">Ou</span><span class="sxs-lookup"><span data-stu-id="cc4c9-149">Or</span></span>
    
  - <span data-ttu-id="cc4c9-150">O administrador de migração deve ser atribuído a permissão **FullAccess** para cada caixa de correio local.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="cc4c9-151">Ou</span><span class="sxs-lookup"><span data-stu-id="cc4c9-151">Or</span></span>
    
  - <span data-ttu-id="cc4c9-152">O administrador de migração deve ser atribuído a permissão **Receber como** no banco de dados da caixa de correio local que armazena as caixas de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="cc4c9-p114">**Desabilite a Unificação de Mensagens.** Se as caixas de correio locais que você está migrando estiverem habilitadas para a UM (Unificação de Mensagens), será necessário desabilitar a UM nas caixas de correio antes de migrá-las. Em seguida, você poderá habilitar a UM nas caixas de correio depois que a migração for concluída.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="cc4c9-p115">**Grupos de segurança e delegados** Este serviço de migração de emails não consegue detectar se grupos locais do Active Directory são grupos de segurança ou não e, portanto, não pode provisionar qualquer grupo migrado como grupo de segurança para o Office 365. Se quiser ter grupos de segurança em seu locatário do Office 365, será necessário provisionar um grupo de segurança habilitado para email vazio em seu locatário do Office 365 antes de iniciar a migração de transferência. Além disso, esse método de migração só move caixas de correio, usuários de email, contatos de email e grupos habilitados para email. Se qualquer outro objeto do Active Directory, como um usuário que não tenha sido migrado para o Office 365, for atribuído como um gerente ou delegado para um objeto que está sendo migrado, ele deverá ser removido do objeto antes da migração.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p115">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="cc4c9-160">Etapa 2: criar um ponto de extremidade de migração</span><span class="sxs-lookup"><span data-stu-id="cc4c9-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="cc4c9-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="cc4c9-161"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="cc4c9-p116">Para migrar o email com êxito, o Office 365 precisa se conectar e se comunicar com o sistema de email de origem. Para fazer isso, o Office 365 usa um ponto de extremidade de migração. Para criar um ponto de extremidade de migração do Outlook em Qualquer Lugar para a migração de substituição, primeiro [conecte-se ao Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p116">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="cc4c9-165">Para obter uma lista completa dos comandos de migração, confira [Cmdlets de movimentação e migração](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-165">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="cc4c9-166">Execute os seguintes comandos no PowerShell do Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="cc4c9-166">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="cc4c9-167">O exemplo usa o cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) para obter e testar as configurações de conexão ao servidor do Exchange local e usa essas configurações de conexão para criar o ponto de extremidade de migração chamado "CutoverEndpoint".</span><span class="sxs-lookup"><span data-stu-id="cc4c9-167">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="cc4c9-p117">O cmdlet **New-MigrationEndpoint** pode ser usado para especificar um banco de dados do serviço a usar, utilizando a opção **-TargetDatabase**. Caso contrário, o banco de dados é atribuído de forma aleatória do site do Serviços de Federação do Active Directory (AD FS) 2.0, no qual a caixa de correio de gerenciamento está localizada.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="cc4c9-170">Verifique se funcionou</span><span class="sxs-lookup"><span data-stu-id="cc4c9-170">Verify it worked</span></span>

<span data-ttu-id="cc4c9-171">No PowerShell do Exchange Online, execute o seguinte comando para exibir informações sobre o ponto de extremidade de migração "CutoverEndpoint":</span><span class="sxs-lookup"><span data-stu-id="cc4c9-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="cc4c9-172">Etapa 3: criar o lote de migração de transferência</span><span class="sxs-lookup"><span data-stu-id="cc4c9-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="cc4c9-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="cc4c9-173"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="cc4c9-p118">Você pode usar o cmdlet **New-MigrationBatch** no PowerShell do Exchange Online para criar um lote de migração de uso em uma migração de transferência. É possível criar um lote de migração e iniciá-lo automaticamente incluindo o parâmetro _AutoStart_. Como alternativa, você pode criar o lote de migração e iniciá-lo manualmente mais tarde usando o cmdlet **Start-MigrationBatch**. Este exemplo cria um lote de migração chamado "CutoverBatch" e utiliza o ponto de extremidade de migração criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="cc4c9-p119">Este exemplo também cria um lote de migração chamado "CutoverBatch" e utiliza o ponto de extremidade de migração criado na etapa anterior. Como o parâmetro  _AutoStart_ não está incluído, o lote de migração deve ser iniciado manualmente no painel de migração ou usando o cmdlet **Start-MigrationBatch**. Como dito anteriormente, apenas um lote de migração de transferência pode existir de cada vez.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="cc4c9-181">Verifique se funcionou</span><span class="sxs-lookup"><span data-stu-id="cc4c9-181">Verify it worked</span></span>

<span data-ttu-id="cc4c9-182">Para verificar se você criou com êxito um lote de migração para uma migração de substituição, execute o seguinte comando no PowerShell do Exchange Online para exibir informações sobre o novo lote de migração:</span><span class="sxs-lookup"><span data-stu-id="cc4c9-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="cc4c9-183">Etapa 4: iniciar o lote de migração de transferência</span><span class="sxs-lookup"><span data-stu-id="cc4c9-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="cc4c9-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="cc4c9-184"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="cc4c9-p120">Para iniciar o lote de migração no PowerShell do Exchange Online, execute o seguinte comando. Isso criará um lote de migração chamado "CutoverBatch".</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="cc4c9-187">Verifique se funcionou</span><span class="sxs-lookup"><span data-stu-id="cc4c9-187">Verify it worked</span></span>

<span data-ttu-id="cc4c9-p121">Se um lote de migração for iniciado com êxito, seu status no painel de migração será especificado como Sincronizando. Para verificar se você iniciou com êxito um lote de migração usando o PowerShell do Exchange Online, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="cc4c9-190">Etapa 5: Rotear o email para o Office 365</span><span class="sxs-lookup"><span data-stu-id="cc4c9-190">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="cc4c9-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="cc4c9-191"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="cc4c9-p122">Os sistemas de email usam um registro DNS chamado de registro MX para descobrir onde entregar os emails. Durante o processo de migração de email, seu registro MX estava apontando para o sistema de email de origem. Agora que a migração de email para o Office 365 foi concluída, é hora de apontar seu registro MX para o Office 365. Isso ajuda a garantir que o email seja entregue a suas caixas de correio do Office 365. Movendo o registro MX, você também poderá desativar seu sistema de email antigo quando estiver pronto.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p122">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="cc4c9-p123">Para muitos provedores DNS, existem instruções específicas para [alterar seu registro MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Se seu provedor DNS não estiver incluído ou se você desejar ter uma noção das instruções gerais, [instruções gerais sobre o registro MX ](https://go.microsoft.com/fwlink/?LinkId=397449) também são fornecidas.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="cc4c9-p124">Pode levar até 72 horas para que os sistemas de email de seus clientes e parceiros reconheçam o registro MX alterado. Aguarde pelo menos 72 horas antes de prosseguir para a próxima tarefa: [Etapa 6: excluir o lote de migração de transferência](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="cc4c9-201">Etapa 6: excluir o lote de migração de transferência</span><span class="sxs-lookup"><span data-stu-id="cc4c9-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="cc4c9-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="cc4c9-202"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="cc4c9-p125">Depois de alterar o registro MX e verificar se todos os emails estão sendo roteados para as caixas de correio do Office 365, notifique os usuários de que seus emails estão indo para o Office 365. Depois disso, você pode excluir o lote de migração de substituição. Antes de excluir o lote de migração, verifique os itens a seguir.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p125">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="cc4c9-p126">Todos os usuários estão usando caixas de correio do Office 365. Depois que o lote for excluído, os emails enviados às caixas de correio no servidor Exchange local não serão copiados para as caixas de correio correspondentes do Office 365.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p126">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="cc4c9-p127">As caixas de correio do Office 365 foram sincronizadas pelo menos uma vez depois que os emails começaram a ser enviados diretamente a elas. Para fazer isso, verifique se o valor na caixa Hora da Última Sincronização para o lote de migração é mais recente do que quando o email começou a ser roteado diretamente para as caixas de correio do Office 365.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p127">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="cc4c9-210">Para excluir o lote de migração "CutoverBatch" no PowerShell do Exchange Online, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="cc4c9-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="cc4c9-211">Seção 7: atribuir licenças de usuários</span><span class="sxs-lookup"><span data-stu-id="cc4c9-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="cc4c9-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="cc4c9-212"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="cc4c9-p128">**Ative as contas de usuário do Office 365 para as contas migradas atribuindo licenças.** Se você não atribuir uma licença, a caixa de correio será desabilitada quando terminar o período de carência (30 dias). Para atribuir uma licença no Centro de administração do Office 365, confira[Atribuir ou cancelar a atribuição de licenças para o Office 365 para empresas](https://go.microsoft.com/fwlink/?LinkId=536681).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p128">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.** If you don't assign a license, the mailbox is disabled when the grace period ends (30 days). To assign a license in the Office 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="cc4c9-216">Etapa 8: concluir tarefas pós-migração</span><span class="sxs-lookup"><span data-stu-id="cc4c9-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="cc4c9-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="cc4c9-217"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="cc4c9-p129">**Crie um registro DNS de Descoberta Automática para que os usuários possam facilmente acessar suas caixas de correio.**Após todas as caixas de correio locais serem migradas para o Office 365, você pode configurar um registro DNS de Descoberta Automática para sua organização do Office 365 e habilitar os usuários a se conectarem facilmente a suas novas caixas de correio do Office 365 com o Outlook e clientes móveis. Esse novo registro DNS de descoberta automática tem que usar o mesmo namespace que você usar para a organização do Office 365. Por exemplo, se seu namespace baseado em nuvem for cloud.contoso.com, o registro DNS de Descoberta Automática a ser criado será autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p129">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="cc4c9-222">Se mantiver seu servidor Exchange, você também deverá verificar se o registro DNS CNAME de Descoberta Automática aponta para o Office 365 no DNS interno e externo após a migração para que o cliente do Outlook se conecte à caixa de correio correta.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="cc4c9-223">No Exchange 2007, Exchange 2010 e no Exchange 2013, você também deve definir o  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` como `Null`.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="cc4c9-p130">O Office 365 usa um registro CNAME para implementar o serviço Descoberta Automática para o Outlook e para clientes móveis. O registro CNAME de Descoberta Automática deve conter as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p130">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="cc4c9-226">**Alias:** descoberta automática</span><span class="sxs-lookup"><span data-stu-id="cc4c9-226">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="cc4c9-227">**Destino:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="cc4c9-227">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="cc4c9-228">Para saber mais, confira [Criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="cc4c9-228">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="cc4c9-p131">**Desativar servidores locais do Exchange.** Depois de verificar se todos os emails estão sendo roteados diretamente para as caixas de correio do Office 365 e quando você não precisar mais manter sua organização de email local ou não planejar implementar uma solução de SSO (logon único), você poderá desinstalar o Exchange de seus servidores e remover sua organização local do Exchange.</span><span class="sxs-lookup"><span data-stu-id="cc4c9-p131">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="cc4c9-231">Para obter mais informações, confira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cc4c9-231">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="cc4c9-232">Modificar ou remover o Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="cc4c9-232">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="cc4c9-233">Como remover uma Organização do Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="cc4c9-233">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="cc4c9-234">Como desinstalar o Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="cc4c9-234">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

