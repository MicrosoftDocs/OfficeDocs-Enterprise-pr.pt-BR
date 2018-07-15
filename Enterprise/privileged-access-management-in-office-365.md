---
title: Privilégios acessar management no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Use este tópico para saber mais sobre o recurso de gerenciamento de acesso privilegiado no Office 365
ms.openlocfilehash: b2db3e16e53cca7deb2bf8fbff61b5b981f42fa6
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319202"
---
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="2c755-103">Privilégios acessar management no Office 365</span><span class="sxs-lookup"><span data-stu-id="2c755-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c755-104">Este tópico aborda as diretrizes de implantação e configuração para recursos da versão beta pública só está disponíveis no Office 365 E5 e avançadas SKUs de conformidade.</span><span class="sxs-lookup"><span data-stu-id="2c755-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="2c755-p101">Privilegiado acesso gerenciamento permite que o controle de acesso granular sobre tarefas de administração com privilégios no Office 365.  Ele pode ajudar a proteger sua organização contra violações que possam usar contas de administração com privilégios existentes com acesso a posição a dados confidenciais ou acesso às definições de configuração crítico. Após habilitar o gerenciamento de acesso privilegiado, serão necessário solicitar acesso just-in-time para executar tarefas com privilégios elevados e privilegiadas por meio de um fluxo de trabalho de aprovação que é altamente no escopo do tempo-limite e usuários. Isso dá usuários just-o suficiente-acesso para realizar a tarefa em questão, sem o risco de exposição dos dados confidenciais ou definições de configuração crítico. Habilitando o gerenciamento de acesso privilegiado no Office 365 permitirá a sua organização para operar com zero privilégios a posição e fornecem uma camada de defesa contra vulnerabilidades resultantes por causa de tal acesso administrativo de posição.</span><span class="sxs-lookup"><span data-stu-id="2c755-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="2c755-110">Este tópico vai guiá-lo por meio de habilitando e configurando o gerenciamento de acesso privilegiado em sua organização do Office 365 e servir como um guia de referência para a solicitação, aprovar e gerenciamento do recurso.</span><span class="sxs-lookup"><span data-stu-id="2c755-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="2c755-111">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="2c755-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="2c755-112">Funcionalidade limitada</span><span class="sxs-lookup"><span data-stu-id="2c755-112">Limited functionality</span></span>
<span data-ttu-id="2c755-p102">Durante a versão beta pública, privilegiado acesso a recursos de gerenciamento só estão disponíveis por meio do [PowerShell do Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) no Office 365. Acesso de privilegiado gerenciamento abrange as definições de tarefa no nível de cmdlets de gerenciamento do Exchange. Em Office 365 versões futuras, acesso privilegiado recursos estarão disponíveis por meio do portal de administração e abordarão outros serviços de cargas de trabalho do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c755-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="2c755-116">Conectar-se para o Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c755-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="2c755-117">As etapas de configuração neste tópico vai orientá-lo por meio de habilitação e usar acesso privilegiado no Office 365 usando o PowerShell do Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="2c755-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="2c755-118">Siga as etapas em [Connect to Exchange Online PowerShell usando a autenticação multifator](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) para se conectar ao Exchange Online PowerShell com suas credenciais do Office 365 para habilitar e configurar o acesso privilegiado para sua organização.</span><span class="sxs-lookup"><span data-stu-id="2c755-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="2c755-p103">Você não precisará habilitar a autenticação multifator para sua organização do Office 365 usar as etapas para habilitar o acesso privilegiado ao conectar ao PowerShell do Exchange Online. Conexão com a autenticação multifator cria um token de OAuth que é usado pelo acesso privilegiado para assinar suas solicitações.</span><span class="sxs-lookup"><span data-stu-id="2c755-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="2c755-121">Habilitar e configurar o gerenciamento de acesso privilegiado</span><span class="sxs-lookup"><span data-stu-id="2c755-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="2c755-122">Etapa 1 - Criar grupo do aprovador</span><span class="sxs-lookup"><span data-stu-id="2c755-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="2c755-p104">No Portal de administração do Office 365, selecione **grupos** > **Adicionar um grupo**, em seguida, crie um grupo de segurança habilitado para email para os aprovadores de acesso padrão privilegiado. Quando concluir, selecione **Adicionar** para criar e salvar o grupo de aprovador.</span><span class="sxs-lookup"><span data-stu-id="2c755-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Tela de aprovadores acesso privilegiado no portal de administração do Office 365](images/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="2c755-p105">Neste momento, somente os usuários com acesso administrativo têm permissão para aprovar solicitações de acesso ao Office 365 privilegiada. No futuro, qualquer usuário que faz parte do grupo dos aprovadores será aprovar solicitações de acesso.</span><span class="sxs-lookup"><span data-stu-id="2c755-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="2c755-128">Etapa 2 - habilitar acesso privilegiado no Office 365</span><span class="sxs-lookup"><span data-stu-id="2c755-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="2c755-129">Acesso privilegiado deve ser explicitamente ativado ao grupo padrão aprovador e incluindo um conjunto de contas de sistema que deseja sejam excluídos do controle de acesso de gerenciamento de acesso privilegiado.</span><span class="sxs-lookup"><span data-stu-id="2c755-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="2c755-130">Execute o seguinte comando no PowerShell do Exchange Online para habilitar o acesso privilegiado e atribuir o grupo do aprovador:</span><span class="sxs-lookup"><span data-stu-id="2c755-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="2c755-131">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c755-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="2c755-132">Contas de sistema recurso é disponibilizado garantir que certas automáticos em suas organizações podem trabalhar sem dependência no acesso privilegiado, no entanto, é recomendável que tal exclusões ser excepcionais e devem ser aprovados e auditadas aqueles permitidos regularmente.</span><span class="sxs-lookup"><span data-stu-id="2c755-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="2c755-133">Etapa 3: criar uma política de aprovação</span><span class="sxs-lookup"><span data-stu-id="2c755-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="2c755-p106">Uma política de aprovação permite definir os requisitos específicos de aprovação com escopo em tarefas individuais. As opções de tipo de aprovação são **Auto** ou **Manual**.</span><span class="sxs-lookup"><span data-stu-id="2c755-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="2c755-136">Execute o seguinte comando no Exchange Online PowerShell para definir uma política de aprovação:</span><span class="sxs-lookup"><span data-stu-id="2c755-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="2c755-137">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c755-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="2c755-138">Usar o acesso privilegiado em sua organização do Office 365</span><span class="sxs-lookup"><span data-stu-id="2c755-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="2c755-139">Autorização de elevação solicitante para executar tarefas</span><span class="sxs-lookup"><span data-stu-id="2c755-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="2c755-p107">Uma vez ativado, com privilégios de acesso requer aprovações para executar qualquer tarefa que tem uma política de aprovação associados definida. Os usuários que precisam executar tarefas incluídas na uma política de aprovação deve solicitar e receber aprovação de acesso para que as permissões necessárias para executar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="2c755-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="2c755-142">Execute o seguinte comando no Exchange Online PowerShell para criar e enviar uma solicitação de aprovação ao grupo do aprovador:</span><span class="sxs-lookup"><span data-stu-id="2c755-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="2c755-143">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c755-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="2c755-144">Exibir o status das solicitações de elevação</span><span class="sxs-lookup"><span data-stu-id="2c755-144">View status of elevation requests</span></span>
<span data-ttu-id="2c755-145">Depois que uma solicitação de aprovação é criada, o status da solicitação de elevação podem ser revisados usando o associado com o ID de solicitação.</span><span class="sxs-lookup"><span data-stu-id="2c755-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="2c755-146">Execute o seguinte comando no Exchange Online PowerShell para exibir o status de uma solicitação de aprovação para uma ID de solicitação específica:</span><span class="sxs-lookup"><span data-stu-id="2c755-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="2c755-147">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c755-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="2c755-148">Aprovar uma solicitação de autorização de elevação</span><span class="sxs-lookup"><span data-stu-id="2c755-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="2c755-149">Quando uma solicitação de aprovação é criada, os membros do grupo aprovador relevantes receberão uma notificação de e-mail e podem aprovar a solicitação associada com o ID de solicitação.</span><span class="sxs-lookup"><span data-stu-id="2c755-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="2c755-150">Execute o seguinte comando no Exchange Online PowerShell para aprovar uma solicitação de autorização de elevação:</span><span class="sxs-lookup"><span data-stu-id="2c755-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="2c755-151">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c755-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="2c755-152">Rejeitar uma solicitação de autorização de elevação</span><span class="sxs-lookup"><span data-stu-id="2c755-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="2c755-153">Quando uma solicitação de aprovação é criada, membros do grupo relevantes aprovador podem negar a solicitação associada com o ID de solicitação.</span><span class="sxs-lookup"><span data-stu-id="2c755-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="2c755-154">Execute o seguinte comando no Exchange Online PowerShell para negar uma solicitação de autorização de elevação:</span><span class="sxs-lookup"><span data-stu-id="2c755-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="2c755-155">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c755-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="2c755-156">Executando a tarefa</span><span class="sxs-lookup"><span data-stu-id="2c755-156">Running the task</span></span>
<span data-ttu-id="2c755-p108">Após a aprovação for concedida, o usuário solicitante pode executar a tarefa pretendida e acesso privilegiado será autorizar e executar a tarefa em nome dos usuários. A aprovação permanecerá válida para os solicitados duração (duração padrão é 4 horas), durante o qual o solicitante pode executar a tarefa pretendida várias vezes. Todas essas execuções são registradas e torná-los disponíveis para auditoria de conformidade e segurança.</span><span class="sxs-lookup"><span data-stu-id="2c755-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="2c755-160">Desabilitar acesso privilegiado no Office 365</span><span class="sxs-lookup"><span data-stu-id="2c755-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="2c755-p109">Se necessário, você pode desativar o gerenciamento de acesso privilegiado no Office 365. Desabilitando privilegiada acesso não exclui quaisquer políticas de aprovação associados ou a grupos de aprovador.</span><span class="sxs-lookup"><span data-stu-id="2c755-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="2c755-163">Execute o seguinte comando no Exchange Online Powershell para desabilitar o acesso privilegiado:</span><span class="sxs-lookup"><span data-stu-id="2c755-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="2c755-164">Gerenciados acesso ao Microsoft Graph in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="2c755-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c755-165">Esta seção aborda as diretrizes de implantação e configuração para um recurso do Microsoft Graph versão beta pública só está disponível no Office 365 E5 e avançadas SKUs de conformidade.</span><span class="sxs-lookup"><span data-stu-id="2c755-165">This section covers deployment and configuration guidance for a public beta Microsoft Graph feature only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="2c755-p110">Acesso gerenciado para o Microsoft Graph in Microsoft Azure é um serviço que ajuda as organizações a exercer um nível granular de controle sobre seus dados do Office 365. Este sistema permite que os desenvolvedores de aplicativos de falsificar ideias com esses dados.</span><span class="sxs-lookup"><span data-stu-id="2c755-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="2c755-p111">Este sistema usa acesso ao Office 365 privilegiado reivindicar controle sobre seus dados por meio de seu fluxo de trabalho de aprovação, permitindo o acesso com escopo aos dados do Office 365 com supervisão de admin. Solicitações de dados são quando os aplicativos são instalados e exigem acesso aos dados do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c755-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="2c755-170">Exibir detalhes da solicitação</span><span class="sxs-lookup"><span data-stu-id="2c755-170">View request details</span></span>
<span data-ttu-id="2c755-171">Exibir detalhes das solicitações de acesso de dados do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c755-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="2c755-172">Execute o seguinte comando no Exchange Online Powershell para visualizar as solicitações de dados:</span><span class="sxs-lookup"><span data-stu-id="2c755-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="2c755-173">Exemplo de saída:</span><span class="sxs-lookup"><span data-stu-id="2c755-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="2c755-174">Aprovar solicitações de acesso de dados</span><span class="sxs-lookup"><span data-stu-id="2c755-174">Approve data access requests</span></span>
<span data-ttu-id="2c755-175">Todas as solicitações de acesso de dados podem ser aprovadas por meio dos cmdlets de aprovação de acesso privilegiado standard.</span><span class="sxs-lookup"><span data-stu-id="2c755-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="2c755-176">Execute o seguinte comando no Exchange Online Powershell para aprovar solicitações de todos os dados para o solicitante específico:</span><span class="sxs-lookup"><span data-stu-id="2c755-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="2c755-177">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c755-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="2c755-178">Obtendo ajuda e fornecer comentários</span><span class="sxs-lookup"><span data-stu-id="2c755-178">Getting help and providing feedback</span></span>
<span data-ttu-id="2c755-p112">Reconhecemos que, durante o beta público, você pode se deparar com um bug ocasional ou ter comentários e sugestões sobre como podemos melhorar o gerenciamento de acesso privilegiado. Podemos seus comentários são importantes e incentivar a compartilhá-las conosco:</span><span class="sxs-lookup"><span data-stu-id="2c755-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="2c755-181">Poste seus comentários sugestões da ad no [Grupo do Yammer de visualização do Office](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span><span class="sxs-lookup"><span data-stu-id="2c755-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="2c755-182">Arquivo seus relatórios de bugs sob o caminho de área "Office 365 privilegiado acesso gerenciamento" no [VSO de visualização do Office](https://office-previews.visualstudio.com/previews).</span><span class="sxs-lookup"><span data-stu-id="2c755-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="2c755-183">Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="2c755-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="2c755-184">Quais SKUs precisa usar acesso privilegiado no Office 365?</span><span class="sxs-lookup"><span data-stu-id="2c755-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="2c755-185">Privilegiado acesso gerenciamento no Office 365 atualmente só está disponível para clientes com E5 e avançadas SKUs de conformidade.</span><span class="sxs-lookup"><span data-stu-id="2c755-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="2c755-186">Quando o acesso privilegiado estará disponível para cargas de trabalho do Office 365 além do Exchange?</span><span class="sxs-lookup"><span data-stu-id="2c755-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="2c755-p113">Pretendemos oferecer esse recurso em outras cargas de trabalho do Office 365 em breve. Quando estamos prontos para compartilhar um cronograma, ele estará disponível por meio do mapa do Office 365.</span><span class="sxs-lookup"><span data-stu-id="2c755-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="2c755-189">Como isso é diferente do gerenciamento de identidade do Windows Azure Active Directory privilegiado?</span><span class="sxs-lookup"><span data-stu-id="2c755-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="2c755-p114">Acesso privilegiado gerenciamento no Office 365 e o complemento de [gerenciamento de identidade do Azure AD privilegiado](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) uns aos outros, fornecendo acesso para controlar com acesso just-in-time em escopos diferentes. Juntos, eles oferecem um conjunto robusto de controles de proteção de seus dados.</span><span class="sxs-lookup"><span data-stu-id="2c755-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="2c755-p115">Privilegiado access pode ser definido e com escopo no nível da tarefa, enquanto o Azure AD privilegiado Identity Management aplica no nível de função com a capacidade de executar várias tarefas de gerenciamento no Office 365.  Gerenciamento de identidade Azure AD privilegiado principalmente permite Gerenciando acessos para grupos de função enquanto com privilégios e funções do AD gerenciamento de acesso no Office 365 é aplicado no nível da tarefa.</span><span class="sxs-lookup"><span data-stu-id="2c755-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="2c755-194">**Privilegiada habilitando acessar management no Office 365 durante o uso do Windows Azure AD privilegiado gerenciamento de identidade já:** Adicionar o gerenciamento de acesso privilegiado no Office 365 pode fornecer outra camada granular de proteção e recursos para acesso privilegiado ao Office 365 dados de auditoria.</span><span class="sxs-lookup"><span data-stu-id="2c755-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="2c755-195">**Habilitando o Azure AD privilegiado gerenciamento de identidade durante a utilização do já privilegiado gerenciamento de acesso no Office 365:**  Adicionando o Azure AD privilegiado gerenciamento de identidade a privilegiada gerenciamento de acesso no Office 365 pode estender privilegiado acesso aos dados fora do Office 365 definida principalmente por função ou a identidade de um usuário.</span><span class="sxs-lookup"><span data-stu-id="2c755-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="2c755-196">É necessário ser um Administrador Global para gerenciar o acesso privilegiado no Office 365?</span><span class="sxs-lookup"><span data-stu-id="2c755-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="2c755-p116">Durante a visualização, você precisa ter privilégios de Administrador Global para poder gerenciar acesso privilegiado no Office 365. Os usuários que estão incluídos no grupo dos aprovadores um não precisam ser um Administrador Global para revisar e aprovar solicitações.</span><span class="sxs-lookup"><span data-stu-id="2c755-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="2c755-199">Como é o gerenciamento de acesso privilegiado no Office 365 relacionadas ao cliente Lockbox?</span><span class="sxs-lookup"><span data-stu-id="2c755-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="2c755-p117">[Lockbox do cliente](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) permite que um nível de controle de acesso para as organizações para acesso a dados pelo seu provedor de serviço, ou seja, a Microsoft. Privilegiado acesso management no Office 365 permite que o controle de acesso granular dentro de uma organização para todas as tarefas do Office 365 privilegiado.</span><span class="sxs-lookup"><span data-stu-id="2c755-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>