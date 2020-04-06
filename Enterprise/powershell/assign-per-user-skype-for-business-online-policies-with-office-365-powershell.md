---
title: Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Resumo: Use o Office 365 PowerShell para atribuir configurações de comunicação por usuário com as políticas do Skype for Business online.'
ms.openlocfilehash: 615deca2790e206e6cf117283321307aa01eac74
ms.sourcegitcommit: f2aefbc2dbbe969fea9db3a4c558651496532413
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2020
ms.locfileid: "43146806"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="d621f-103">Atribuir Skype de por usuário para políticas de negócios Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d621f-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="d621f-104">O uso do Office 365 PowerShell é uma maneira eficiente de atribuir configurações de comunicação por usuário com as políticas do Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="d621f-104">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d621f-105">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="d621f-105">Before you begin</span></span>

<span data-ttu-id="d621f-106">Use estas instruções para configurar a execução dos comandos (pule as etapas que você já concluiu):</span><span class="sxs-lookup"><span data-stu-id="d621f-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="d621f-107">Baixe e instale o [módulo do conector do Skype for Business online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="d621f-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="d621f-108">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d621f-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="d621f-109">Quando solicitado, insira o nome da conta e a senha do administrador do Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="d621f-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="d621f-110">Atualizando configurações de comunicação externa para uma conta de usuário</span><span class="sxs-lookup"><span data-stu-id="d621f-110">Updating external communication settings for a user account</span></span>

<span data-ttu-id="d621f-111">Suponha que você queira alterar as configurações de comunicação externa em uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="d621f-111">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="d621f-112">Por exemplo, você deseja permitir que Alex se comunique com usuários federados (EnableFederationAccess é igual a true), mas não com usuários do Windows Live (EnablePublicCloudAccess é igual a false).</span><span class="sxs-lookup"><span data-stu-id="d621f-112">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="d621f-113">Para fazer isso, você precisa fazer duas coisas:</span><span class="sxs-lookup"><span data-stu-id="d621f-113">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="d621f-114">Localizar uma política de acesso externo que atenda aos nossos critérios.</span><span class="sxs-lookup"><span data-stu-id="d621f-114">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="d621f-115">Atribuir essa política de acesso externo a Antônio.</span><span class="sxs-lookup"><span data-stu-id="d621f-115">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="d621f-116">Você não pode criar uma política personalizada todos nossos.</span><span class="sxs-lookup"><span data-stu-id="d621f-116">You can't create a custom policy all our own.</span></span> <span data-ttu-id="d621f-117">Isso ocorre porque o Skype for Business online não permite que você crie políticas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="d621f-117">That's because Skype for Business Online does not allow you to create custom policies.</span></span> <span data-ttu-id="d621f-118">Em vez disso, você deve atribuir uma das políticas que foram criadas especificamente para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="d621f-118">Instead, you must assign one of the policies that were created specifically for Office 365.</span></span> <span data-ttu-id="d621f-119">Essas políticas previamente criadas incluem: 4 diferentes políticas de cliente, 224 diferentes políticas de conferência, cinco planos de discagem diferentes, cinco políticas de acesso externo diferentes, 1 política de caixa postal hospedada e 4 políticas de voz diferentes.</span><span class="sxs-lookup"><span data-stu-id="d621f-119">Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="d621f-120">Então, como determinar qual política de acesso externo atribuirá a Alex?</span><span class="sxs-lookup"><span data-stu-id="d621f-120">So how do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="d621f-121">O comando a seguir retorna todas as políticas de acesso externo em que EnableFederationAccess é definido como True e EnablePublicCloudAccess como False:</span><span class="sxs-lookup"><span data-stu-id="d621f-121">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="d621f-122">O que o comando faz é retornar todas as políticas que atendem a dois critérios: a propriedade EnableFederationAccess é definida como true e a política EnablePublicCloudAccess é definida como false.</span><span class="sxs-lookup"><span data-stu-id="d621f-122">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False.</span></span> <span data-ttu-id="d621f-123">Por sua vez, esse comando retorna uma política que atende aos nossos critérios (FederationOnly).</span><span class="sxs-lookup"><span data-stu-id="d621f-123">In turn, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="d621f-124">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="d621f-124">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="d621f-125">A identidade da política diz a marca: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="d621f-125">The policy Identity says Tag:FederationOnly.</span></span> <span data-ttu-id="d621f-126">Na verdade, o prefixo Tag: é um carryover de um trabalho pré-lançamento anterior do Microsoft Lync 2013.</span><span class="sxs-lookup"><span data-stu-id="d621f-126">As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013.</span></span> <span data-ttu-id="d621f-127">No que diz respeito à atribuição de políticas a usuários, você deve excluir o prefixo Tag: e usar apenas o nome da política: FederationOnly.</span><span class="sxs-lookup"><span data-stu-id="d621f-127">When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="d621f-128">Agora que você sabe qual política será atribuída a Alex, podemos atribuir essa política usando o cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) .</span><span class="sxs-lookup"><span data-stu-id="d621f-128">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="d621f-129">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="d621f-129">Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="d621f-130">Atribuir uma política é muito simples: basta especificar a identidade do usuário e o nome da política a ser atribuída.</span><span class="sxs-lookup"><span data-stu-id="d621f-130">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="d621f-131">E quando se trata de políticas e atribuições de política, você não está limitado a trabalhar com as contas de usuário uma vez.</span><span class="sxs-lookup"><span data-stu-id="d621f-131">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="d621f-132">Por exemplo, suponha que você precise de uma lista de todos os usuários que têm permissão para se comunicar com parceiros federados e com usuários do Windows Live.</span><span class="sxs-lookup"><span data-stu-id="d621f-132">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="d621f-133">Já sabemos que esses usuários foram atribuídos à política de acesso de usuário externo FederationAndPICDefault.</span><span class="sxs-lookup"><span data-stu-id="d621f-133">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="d621f-134">Como sabemos que, você pode exibir uma lista de todos os usuários executando um comando simples.</span><span class="sxs-lookup"><span data-stu-id="d621f-134">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="d621f-135">Este é o comando:</span><span class="sxs-lookup"><span data-stu-id="d621f-135">Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="d621f-136">Em outras palavras, isso nos mostra todos os usuários cuja propriedade ExternalAccessPolicy está definida como FederationAndPICDefault.</span><span class="sxs-lookup"><span data-stu-id="d621f-136">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="d621f-137">(E, para limitar a quantidade de informações que aparece na tela, use o cmdlet Select-Object para exibir apenas mostrar o nome de exibição de cada usuário.)</span><span class="sxs-lookup"><span data-stu-id="d621f-137">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="d621f-138">Para configurar todas as contas de usuário para usar essa mesma política, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d621f-138">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="d621f-139">Este comando usa Get-CsOnlineUser para retornar uma coleção de todos os usuários que tenham sido habilitados para o Lync e, em seguida, envia todas as informações para Grant-CsExternalAccessPolicy, que atribui a política de FederationAndPICDefault a cada e a todos os usuários da coleção.</span><span class="sxs-lookup"><span data-stu-id="d621f-139">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="d621f-140">Como um exemplo adicional, suponha que você tenha anteriormente atribuído a Alex a política FederationAndPICDefault e agora já alterou sua mente e gostaria que ele fosse gerenciado pela política de acesso externo global.</span><span class="sxs-lookup"><span data-stu-id="d621f-140">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="d621f-141">Você não pode atribuir explicitamente a política global a qualquer pessoa.</span><span class="sxs-lookup"><span data-stu-id="d621f-141">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="d621f-142">Ela só será usada se nenhuma política por usuário for atribuída.</span><span class="sxs-lookup"><span data-stu-id="d621f-142">It is only used if no other per-user policy is assigned.</span></span> <span data-ttu-id="d621f-143">Portanto, se quisermos que Alex seja gerenciado pela política global, você precisará *cancelar a atribuição* de qualquer política por usuário atribuída anteriormente a ele.</span><span class="sxs-lookup"><span data-stu-id="d621f-143">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="d621f-144">Este é um exemplo de comando:</span><span class="sxs-lookup"><span data-stu-id="d621f-144">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="d621f-145">Este comando define o nome da política de acesso externo atribuída a Alex como um valor nulo ($Null).</span><span class="sxs-lookup"><span data-stu-id="d621f-145">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="d621f-146">NULL significa "Nothing".</span><span class="sxs-lookup"><span data-stu-id="d621f-146">Null means "nothing".</span></span> <span data-ttu-id="d621f-147">Em outras palavras, nenhuma política de acesso externo é atribuída a Alex.</span><span class="sxs-lookup"><span data-stu-id="d621f-147">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="d621f-148">Quando nenhuma política de acesso externo é atribuída a um usuário, esse usuário é gerenciado pela política global.</span><span class="sxs-lookup"><span data-stu-id="d621f-148">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="d621f-149">Para desabilitar uma conta de usuário usando o Windows PowerShell, use os cmdlets do Azure Active Directory para remover a licença do Skype for Business online de Alex.</span><span class="sxs-lookup"><span data-stu-id="d621f-149">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license.</span></span> <span data-ttu-id="d621f-150">Para obter mais informações, consulte [desabilitar o acesso aos serviços com o Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d621f-150">For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="d621f-151">Gerenciando um grande número de usuários</span><span class="sxs-lookup"><span data-stu-id="d621f-151">Managing large numbers of users</span></span>

<span data-ttu-id="d621f-152">Para gerenciar grandes números de usuários (1000 ou mais), você precisa em lotes os comandos por meio de um bloco de script usando o cmdlet [Invoke-Command](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) .</span><span class="sxs-lookup"><span data-stu-id="d621f-152">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="d621f-153">Nos exemplos anteriores, cada vez que um cmdlet é executado, ele deve configurar a chamada e, em seguida, aguardar o resultado antes de enviá-lo de volta.</span><span class="sxs-lookup"><span data-stu-id="d621f-153">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="d621f-154">Ao usar um bloco de script, isso permite que os cmdlets sejam executados remotamente e, depois de concluídos, enviem os dados de volta.</span><span class="sxs-lookup"><span data-stu-id="d621f-154">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

<span data-ttu-id="d621f-155">Isso encontrará 500 usuários por vez que não têm uma política de cliente.</span><span class="sxs-lookup"><span data-stu-id="d621f-155">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="d621f-156">Ele concederá a eles a política de cliente "ClientPolicyNoIMURL" e a política de acesso externo "FederationAndPicDefault".</span><span class="sxs-lookup"><span data-stu-id="d621f-156">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="d621f-157">Os resultados são enviados em lotes em grupos de 50 e cada lote de 50 é enviado para a máquina remota.</span><span class="sxs-lookup"><span data-stu-id="d621f-157">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d621f-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="d621f-158">See also</span></span>

[<span data-ttu-id="d621f-159">Gerenciar o Skype for Business Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d621f-159">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="d621f-160">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d621f-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d621f-161">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d621f-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
