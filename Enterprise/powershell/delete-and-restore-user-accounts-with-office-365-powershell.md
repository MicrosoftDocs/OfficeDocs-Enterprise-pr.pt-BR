---
title: "Excluir e restaurar contas de usuários usando o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Aprenda a usar o Office 365 PowerShell para excluir e restaurar contas de usuários do Office 365."
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e50bb-103">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e50bb-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e50bb-104">**Resumo:** aprenda a usar o Office 365 PowerShell para excluir e restaurar contas de usuários do Office 365.</span><span class="sxs-lookup"><span data-stu-id="e50bb-104">Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts</span></span>
  
<span data-ttu-id="e50bb-p101">Quando você usa o Office 365 PowerShell para excluir uma conta de usuário, ela não é excluída permanentemente. Você pode restaurar a conta de usuário excluída no prazo de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="e50bb-p101">When you use Office 365 PowerShell to delete a user account, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="e50bb-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="e50bb-107">Before you begin</span></span>

- <span data-ttu-id="e50bb-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e50bb-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="e50bb-110">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="e50bb-110">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="e50bb-111">Usar o Office 365 PowerShell para bloquear o acesso a contas de usuário individuais</span><span class="sxs-lookup"><span data-stu-id="e50bb-111">Use Office 365 PowerShell to block access to individual user accounts</span></span>
<span data-ttu-id="e50bb-112"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="e50bb-112"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="e50bb-113">Para excluir uma conta de usuário, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e50bb-113">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="e50bb-114">Este exemplo exclui a conta de usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e50bb-114">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="e50bb-115">Para restaurar uma conta de usuário excluída no período de tolerância de 30 dias, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e50bb-115">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="e50bb-116">Este exemplo restaura a conta excluída BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e50bb-116">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="e50bb-117">**Observações:**</span><span class="sxs-lookup"><span data-stu-id="e50bb-117">**Notes:**</span></span>
  
- <span data-ttu-id="e50bb-118">Para ver a lista de usuários excluídos que pode ser restaurados, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e50bb-118">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="e50bb-119">Se o nome UPN (nome principal do usuário) original da conta de usuário for usado por outra conta, use o parâmetro  _NewUserPrincipalName_ no lugar de _UserPrincipalName_ para especificar um UPN diferente ao restaurar a conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="e50bb-119">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a><span data-ttu-id="e50bb-120">Usar o módulo PowerShell do Azure Active Directory V2 para remover uma conta de usuário</span><span class="sxs-lookup"><span data-stu-id="e50bb-120">Use the Azure Active Directory V2 PowerShell module to remove a user account</span></span>
<span data-ttu-id="e50bb-121"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="e50bb-121"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="e50bb-p103">Para usar o cmdlet **Remove-AzureADUser** no módulo PowerShell do Azure Active Directory V2, conecte-se primeiro à sua assinatura. Para conhecer as instruções, confira [Conectar-se com o módulo PowerShell do Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="e50bb-p103">To use the **Remove-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="e50bb-124">Após a conexão, use a seguinte sintaxe para remover uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="e50bb-124">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <Account>
```

<span data-ttu-id="e50bb-125">Este exemplo remove a conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e50bb-125">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="e50bb-126">O parâmetro **-ObjectID** no cmdlet **Remove-AzureAD** aceita o nome da conta, também conhecido como o nome UPN, ou a ID de objeto da conta.</span><span class="sxs-lookup"><span data-stu-id="e50bb-126">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="e50bb-127">Para exibir o nome da conta com base no nome do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e50bb-127">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e50bb-128">Este exemplo exibe o nome da conta do usuário Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="e50bb-128">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e50bb-129">Para remover uma conta com base no nome do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e50bb-129">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a><span data-ttu-id="e50bb-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="e50bb-130">See also</span></span>
<span data-ttu-id="e50bb-131"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="e50bb-131"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="e50bb-132">Confira estes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e50bb-132">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="e50bb-133">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e50bb-133">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="e50bb-134">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e50bb-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="e50bb-135">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="e50bb-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="e50bb-136">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e50bb-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="e50bb-137">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="e50bb-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="e50bb-138">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="e50bb-138">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="e50bb-139">Remove-MsolUser</span><span class="sxs-lookup"><span data-stu-id="e50bb-139">Remove-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [<span data-ttu-id="e50bb-140">Restore-MsolUser</span><span class="sxs-lookup"><span data-stu-id="e50bb-140">Restore-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [<span data-ttu-id="e50bb-141">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="e50bb-141">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

