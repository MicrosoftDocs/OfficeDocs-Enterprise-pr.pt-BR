---
title: Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Resumo: Usar o PowerShell do Office 365 para atribuir configurações de comunicação com Skype para políticas de negócios Online de por usuário.'
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
ms.locfileid: "17114802"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="54072-103">Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="54072-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="54072-104">**Resumo:** Use o Office 365 PowerShell para atribuir por usuário configurações de comunicação com Skype para políticas de negócios Online.</span><span class="sxs-lookup"><span data-stu-id="54072-104">**Summary:** Use Office 365 PowerShell to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
<span data-ttu-id="54072-105">Usar o Office 365 PowerShell é uma maneira eficiente para atribuir configurações de comunicação com Skype para políticas de negócios Online de por usuário.</span><span class="sxs-lookup"><span data-stu-id="54072-105">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="54072-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="54072-106">Before you begin</span></span>

<span data-ttu-id="54072-107">Use essas instruções para obter configurado para executar os comandos (ignore as etapas que você já tenha concluído):</span><span class="sxs-lookup"><span data-stu-id="54072-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="54072-108">Baixe e instale o [Skype para módulo Business Connector Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="54072-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="54072-109">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="54072-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
<span data-ttu-id="54072-110">Quando solicitado, insira seu Skype para Business Online nome da conta de administrador e senha.</span><span class="sxs-lookup"><span data-stu-id="54072-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="54072-111">Atualizar as configurações de comunicação externa para uma conta de usuário</span><span class="sxs-lookup"><span data-stu-id="54072-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="54072-p101">Suponha que você deseja alterar as configurações de comunicação externa em uma conta de usuário. Por exemplo, você deseja permitir Alex para se comunicar com usuários federados (EnableFederationAccess é igual a True), mas não com usuários do Windows Live (EnablePublicCloudAccess for igual a False). Para fazer isso, você precisa fazer duas coisas:</span><span class="sxs-lookup"><span data-stu-id="54072-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="54072-115">Localizar uma política de acesso externo que atenda aos nossos critérios.</span><span class="sxs-lookup"><span data-stu-id="54072-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="54072-116">Atribuir essa política de acesso externo a Antônio.</span><span class="sxs-lookup"><span data-stu-id="54072-116">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="54072-p102">Não é possível criar uma política personalizada para todos os nossos próprios. Isso acontece porque o Skype para Business Online não permite que você crie diretivas personalizadas. Em vez disso, você deve atribuir uma das políticas que foram criadas especificamente para o Office 365. Aqueles criados anteriormente políticas incluem: 4 políticas de cliente diferente, 224 políticas de conferência diferentes, 5 planos de discagem diferentes, 5 políticas de acesso externo diferentes, política de correio de voz hospedada 1 e 4 políticas de voz diferentes.</span><span class="sxs-lookup"><span data-stu-id="54072-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="54072-p103">Então, como determinar qual política de acesso externo para atribuir a Antônio? O comando a seguir retorna todas as políticas de acesso externo em que EnableFederationAccess for definido como True e EnablePublicCloudAccess for definida como False:</span><span class="sxs-lookup"><span data-stu-id="54072-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="54072-p104">O que significa o comando é retornar todas as políticas que atenderem a dois critérios: a propriedade EnableFederationAccess for definida como True e a política EnablePublicCloudAccess for definida como False. Por sua vez, esse comando retorna uma política que atenda aos nossos critérios (FederationOnly). Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="54072-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy that meets our criteria (FederationOnly). Here is an example:</span></span>
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="54072-p105">A identidade da política diz Tag: FederationOnly. Na verdade, a marca: prefixo é uma consequência do trabalho de pré-lançamento antecipado feito no Microsoft Lync 2013. Quando se trata de atribuir políticas aos usuários, você deve excluir a marca: prefix e use apenas o nome de política: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="54072-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="54072-p106">Agora que você sabe quais políticas atribuir a Antônio, podemos atribuir essa política usando o cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) . Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="54072-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="54072-131">Atribuindo uma política é muito simple: basta especificar a identidade do usuário e o nome da política a ser atribuído.</span><span class="sxs-lookup"><span data-stu-id="54072-131">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="54072-p107">E quando se trata de políticas e atribuições de políticas, você não está limitado a trabalhar com uma conta de usuário uma vez. Por exemplo, suponha que você precisa de uma lista de todos os usuários que têm permissão para se comunicar com parceiros federados e usuários do Windows Live. Já sabemos que esses usuários tiverem sido atribuídos a política de acesso de usuário externo FederationAndPICDefault. Porque sabemos que, você pode exibir uma lista de todos os usuários executando um comando simple. Aqui está o comando:</span><span class="sxs-lookup"><span data-stu-id="54072-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="54072-p108">Em outras palavras, nos mostrará todos os usuários cuja propriedade ExternalAccessPolicy é definida para FederationAndPICDefault. (E, para limitar a quantidade de informações que aparece na tela, use o cmdlet Select-Object para exibir nos mostrará apenas o nome de exibição de cada usuário.)</span><span class="sxs-lookup"><span data-stu-id="54072-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="54072-139">Para configurar todas as nossas contas de usuário para usar a mesma política, use este comando:</span><span class="sxs-lookup"><span data-stu-id="54072-139">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="54072-140">Esse comando usa Get-CsOnlineUser para retornar uma coleção de todos os usuários que tiverem sido habilitados para o Lync e, em seguida, envia todas essas informações para Grant-CsExternalAccessPolicy, que atribuirá a política de FederationAndPICDefault para cada usuário na coleção.</span><span class="sxs-lookup"><span data-stu-id="54072-140">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="54072-p109">Como um exemplo adicional, suponha que você atribuiu Alex anteriormente a política FederationAndPICDefault e agora você mudou de ideia e gostaria que ele seja gerenciado pela política de acesso externo global. Você não pode atribuir explicitamente a política global para qualquer pessoa. Ele é usado apenas se nenhuma outra diretiva por usuário é atribuída. Portanto, se quisermos Alex a ser gerenciado pela política global, você precisará *retirar a atribuição de* qualquer política por usuário previamente atribuída a ele. Aqui está um exemplo de comando:</span><span class="sxs-lookup"><span data-stu-id="54072-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="54072-p110">Esse comando define o nome da política de acesso externo atribuída à Alex para um nulo ($ $Null). NULL significa "nothing". Em outras palavras, nenhuma política de acesso externo é atribuída a Antônio. Quando nenhuma política de acesso externo é atribuída a um usuário, o que o usuário, obtém gerenciado pela diretiva global.</span><span class="sxs-lookup"><span data-stu-id="54072-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="54072-p111">Para desabilitar uma conta de usuário usando o Windows PowerShell, use os cmdlets do Windows Azure Active Directory para remover Skype de Alex licença Business Online. Para obter mais informações, consulte [Desabilitar o acesso aos serviços do Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="54072-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="54072-152">Veja também</span><span class="sxs-lookup"><span data-stu-id="54072-152">See also</span></span>

#### 

[<span data-ttu-id="54072-153">Gerenciar o Skype for Business Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="54072-153">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="54072-154">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="54072-154">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="54072-155">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="54072-155">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

