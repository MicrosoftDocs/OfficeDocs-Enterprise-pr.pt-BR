---
title: Deletar contas de usuários usando o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
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
ms.openlocfilehash: e62c06981a861580804dde852ad3da7bd729fdbe
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257642"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e3d38-103">Deletar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3d38-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e3d38-104">Você pode usar o PowerShell do Office 365 para excluir uma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="e3d38-104">You can use Office 365 PowerShell to delete a user account.</span></span>
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e3d38-105">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="e3d38-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e3d38-106">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e3d38-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="e3d38-107">Após a conexão, use a seguinte sintaxe para remover uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="e3d38-107">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

>[!Note]
><span data-ttu-id="e3d38-108">O PowerShell Core não é compatível com o módulo Microsoft Azure Active Directory para o módulo e cmdlets do Windows PowerShell com o **MSol** em seu nome.</span><span class="sxs-lookup"><span data-stu-id="e3d38-108">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e3d38-109">Para continuar usando esses cmdlets, você deve executá-los do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3d38-109">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="e3d38-110">Este exemplo remove a conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e3d38-110">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="e3d38-111">O parâmetro **-ObjectID** no cmdlet **Remove-AzureAD** aceita o nome de usuário da conta, também conhecido como o nome UPN, ou a ID de objeto da conta.</span><span class="sxs-lookup"><span data-stu-id="e3d38-111">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="e3d38-112">Para exibir o nome da conta com base no nome do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e3d38-112">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e3d38-113">Este exemplo exibe o nome da conta do usuário Carlos Lima.</span><span class="sxs-lookup"><span data-stu-id="e3d38-113">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e3d38-114">Para remover uma conta com base no nome de exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e3d38-114">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e3d38-115">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3d38-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e3d38-p102">Quando você exclui uma conta de usuário com o Módulo Microsoft Azure Active Directory para Windows PowerShell, ela não é excluída permanentemente. Você pode restaurar a conta de usuário excluída no prazo de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="e3d38-p102">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="e3d38-118">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e3d38-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


<span data-ttu-id="e3d38-119">Para excluir uma conta de usuário, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e3d38-119">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="e3d38-120">Este exemplo exclui a conta de usuário BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e3d38-120">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="e3d38-121">Para restaurar uma conta de usuário excluída no período de tolerância de 30 dias, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e3d38-121">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="e3d38-122">Este exemplo restaura a conta excluída BrendaF@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e3d38-122">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="e3d38-123">**Observações:**</span><span class="sxs-lookup"><span data-stu-id="e3d38-123">**Notes:**</span></span>
  
- <span data-ttu-id="e3d38-124">Para ver a lista de usuários excluídos que pode ser restaurados, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e3d38-124">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="e3d38-125">Se o nome UPN (nome principal do usuário) original da conta de usuário for usado por outra conta, use o parâmetro _NewUserPrincipalName_ no lugar de _UserPrincipalName_ para especificar um UPN diferente ao restaurar a conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="e3d38-125">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="e3d38-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="e3d38-126">See also</span></span>

[<span data-ttu-id="e3d38-127">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3d38-127">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e3d38-128">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3d38-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e3d38-129">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3d38-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

