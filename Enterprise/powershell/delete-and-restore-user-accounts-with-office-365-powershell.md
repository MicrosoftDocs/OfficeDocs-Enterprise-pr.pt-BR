---
title: Deletar contas de usuários usando o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Saiba como usar o Office 365 PowerShell para excluir contas de usuários do Office 365.
ms.openlocfilehash: 0b882f3bdf9070c83baffaca65a7c80c98cd4ed9
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546462"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f1f31-103">Deletar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1f31-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="f1f31-104">**Resumo:** Saiba como usar o Office 365 PowerShell para excluir e restaurar contas de usuários do Office 365.</span><span class="sxs-lookup"><span data-stu-id="f1f31-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="f1f31-105">Você pode usar o PowerShell do Office 365 para excluir uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="f1f31-105">You can use the Office 365 admin center to create a new user account.</span></span>

   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f1f31-106">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="f1f31-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="f1f31-107">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="f1f31-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="f1f31-108">Após a conexão, use a seguinte sintaxe para remover uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="f1f31-108">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="f1f31-109">Este exemplo remove a conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="f1f31-109">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="f1f31-110">O parâmetro **-ObjectID** no cmdlet **Remove-AzureAD** aceita o nome de usuário da conta, também conhecido como o nome UPN, ou a ID de objeto da conta.</span><span class="sxs-lookup"><span data-stu-id="f1f31-110">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="f1f31-111">Para exibir o nome da conta com base no nome do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="f1f31-111">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f1f31-112">Este exemplo exibe o nome da conta do usuário Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="f1f31-112">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="f1f31-113">Para remover uma conta com base no nome de exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="f1f31-113">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f1f31-114">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f1f31-114">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

<span data-ttu-id="f1f31-p101">Quando você exclui uma conta de usuário com o Módulo Microsoft Azure Active Directory para Windows PowerShell, ela não é excluída permanentemente. Você pode restaurar a conta de usuário excluída no prazo de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="f1f31-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="f1f31-117">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f1f31-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="f1f31-118">Para excluir uma conta de usuário, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="f1f31-118">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="f1f31-119">Este exemplo exclui a conta de usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="f1f31-119">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="f1f31-120">Para restaurar uma conta de usuário excluída no período de tolerância de 30 dias, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="f1f31-120">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="f1f31-121">Este exemplo restaura a conta excluída BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="f1f31-121">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="f1f31-122">**Observações:**</span><span class="sxs-lookup"><span data-stu-id="f1f31-122">**Notes:**</span></span>
  
- <span data-ttu-id="f1f31-123">Para ver a lista de usuários excluídos que pode ser restaurados, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1f31-123">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="f1f31-124">Se o nome UPN (nome principal do usuário) original da conta de usuário for usado por outra conta, use o parâmetro _NewUserPrincipalName_ no lugar de _UserPrincipalName_ para especificar um UPN diferente ao restaurar a conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="f1f31-124">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="f1f31-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="f1f31-125">See also</span></span>

[<span data-ttu-id="f1f31-126">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1f31-126">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f1f31-127">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1f31-127">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f1f31-128">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1f31-128">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

