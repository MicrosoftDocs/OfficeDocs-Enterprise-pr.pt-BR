---
title: "Remover licenças de contas de usuários com o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: PowerShell, Ent_Office_Other, LIL_Placement, O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.
ms.openlocfilehash: 115a708d8def679d43d88e9c83b68ca13dd72fdc
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="0a8e7-103">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a8e7-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="0a8e7-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="0a8e7-105">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="0a8e7-105">Before you begin</span></span>

- <span data-ttu-id="0a8e7-p101">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="0a8e7-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="0a8e7-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="0a8e7-109">Exibir licenças e serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="0a8e7-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="0a8e7-110">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a8e7-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="0a8e7-111">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="0a8e7-112">A versão curta (instruções sem explicações)</span><span class="sxs-lookup"><span data-stu-id="0a8e7-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="0a8e7-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="0a8e7-113"></span></span>

<span data-ttu-id="0a8e7-p102">Esta seção apresenta os procedimentos sem divulgação ou explicação supérflua. Se você tiver dúvidas ou se quiser obter mais informações, leia o restante do tópico.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="0a8e7-116">Para remover licenças de uma conta de usuário existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="0a8e7-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="0a8e7-118">Para remover licenças de um grupo de usuários licenciados existentes, use um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="0a8e7-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="0a8e7-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="0a8e7-121">**Use a list of specific accounts** To do this, perform the following steps:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="0a8e7-122">Crie e salve um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="0a8e7-123">Use a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="0a8e7-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="0a8e7-125">Para remover licenças de todas as contas de usuário existentes, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="0a8e7-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="0a8e7-127">A versão longa (instruções com explicações detalhadas)</span><span class="sxs-lookup"><span data-stu-id="0a8e7-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="0a8e7-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="0a8e7-128"></span></span>

<span data-ttu-id="0a8e7-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="0a8e7-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="0a8e7-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="0a8e7-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span><span class="sxs-lookup"><span data-stu-id="0a8e7-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0a8e7-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="0a8e7-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="0a8e7-145">Para verificar se a licença foi realmente removida, use Get-MsoIUser para verificar a conta de usuário em questão:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="0a8e7-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="0a8e7-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="0a8e7-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0a8e7-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="0a8e7-149">See also</span></span>

<span data-ttu-id="0a8e7-150">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="0a8e7-151">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a8e7-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a8e7-152">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a8e7-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a8e7-153">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a8e7-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="0a8e7-154">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="0a8e7-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="0a8e7-155">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="0a8e7-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="0a8e7-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="0a8e7-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="0a8e7-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="0a8e7-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="0a8e7-158">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="0a8e7-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="0a8e7-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="0a8e7-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="0a8e7-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="0a8e7-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="0a8e7-161">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="0a8e7-161">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

