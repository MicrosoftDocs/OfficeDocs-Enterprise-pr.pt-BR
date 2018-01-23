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
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "Explica como usar o Office 365 PowerShell para remover licenças do Office 365 que previamente atribuídas aos usuários."
ms.openlocfilehash: 21aed391cf0395bf51a7e99cf9f8f0e34bfd9d10
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="89433-103">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89433-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="89433-104">**Resumo:** Explica como usar o Office 365 PowerShell para remover licenças do Office 365 que previamente atribuídas aos usuários.</span><span class="sxs-lookup"><span data-stu-id="89433-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="89433-105">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="89433-105">Before you begin</span></span>

- <span data-ttu-id="89433-p101">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="89433-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="89433-108">Para exibir as informações de licenciamento plano ( **AccountSkuID** ) em sua organização, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="89433-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="89433-109">Exibir licenças e serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="89433-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="89433-110">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89433-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="89433-111">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="89433-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="89433-112">A versão curta (instruções sem explicações)</span><span class="sxs-lookup"><span data-stu-id="89433-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="89433-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="89433-113"></span></span>

<span data-ttu-id="89433-p102">Esta seção apresenta os procedimentos sem divulgação ou explicação supérflua. Se você tiver dúvidas ou se quiser obter mais informações, leia o restante do tópico.</span><span class="sxs-lookup"><span data-stu-id="89433-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="89433-116">Para remover licenças de uma conta de usuário existente, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="89433-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="89433-117">Este exemplo remove o `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) da conta de usuário BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="89433-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="89433-118">Para remover licenças de um grupo de usuários licenciados existentes, use um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="89433-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="89433-119">**Filtrar as contas com base em um atributo existente da conta** Para fazer isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="89433-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="89433-120">Este exemplo remove o `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenças de opinião para usuários no departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="89433-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="89433-121">**Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="89433-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="89433-122">Crie e salve um arquivo de texto que contenha uma conta em cada linha da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="89433-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="89433-123">Use a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="89433-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="89433-124">Este exemplo remove o `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) das contas de usuário definidos no arquivo de texto C:\My Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="89433-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="89433-125">Para remover licenças de todas as contas de usuário existentes, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="89433-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="89433-126">Este exemplo remove o `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) de todos os existentes licenciados contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="89433-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="89433-127">A versão longa (instruções com explicações detalhadas)</span><span class="sxs-lookup"><span data-stu-id="89433-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="89433-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="89433-128"></span></span>

<span data-ttu-id="89433-p103">Nada dura indefinidamente e que inclui licenças do Office 365: cedo ou tarde, há virão vez quando você precisa remover a licença de uma conta de usuário. Talvez o usuário está acontecendo deixe; Talvez o usuário não precisa mais a licença; bem, talvez - há obviamente, qualquer número dos motivos por que talvez você queira remover uma licença de usuário.</span><span class="sxs-lookup"><span data-stu-id="89433-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="89433-p104">Antes de prosseguir qualquer outra é importante observar que a remoção de uma licença requer que você, vamos, remova a licença: desabilitar todos os serviços em uma licença não é a mesma coisa que a remoção da licença. Por exemplo, suponha que usamos para cima todas as nossas licenças do Office 365; em outras palavras, temos não licenças disponíveis qualquer. Você decide siga o procedimento em [Desabilitar o acesso aos serviços do Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) para desabilitar todos os serviços, digamos, na conta de Belinda Newman. Depois que fazemos que, quantas licenças serão temos disponíveis para nós? É isso mesmo: zero. Sim, o procedimento daquele tópico irá *Desabilitar* todos os serviços em licença de Belinda, mas não desabilitará (ou seja, delete) a licença em si. A licença ainda será válida e ele ainda será atribuído ao Belinda Newman. Ela só não poderão usar essa licença para acessar quaisquer serviços do Office 365.</span><span class="sxs-lookup"><span data-stu-id="89433-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="89433-p105">E isso é importante: se você deseja remover uma licença de um usuário deve realmente *Remover* a licença. Desabilitar todos os serviços impedirá que o usuário faça logon no Office 365, mas ele não libera a sua licença. Se você deseja retomar uma licença atualmente atribuído a um usuário que você precisa executar um comando semelhante a este, um comando que usa o parâmetro _RemoveLicenses_ para remover efetivamente a licença atribuída anteriormente a Belinda:</span><span class="sxs-lookup"><span data-stu-id="89433-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="89433-142">Execute esse comando e Belinda Newman será não é mais licenciado para usar o Office 365.</span><span class="sxs-lookup"><span data-stu-id="89433-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="89433-p106">Como você pode ver, quando você usa o parâmetro _RemoveLicenses_ que é preciso especificar o nome da licença a ser removido. Se não tiver certeza de qual plano de licenciamento foi usado para atribuir uma licença para o usuário, basta executar um comando semelhante a esta:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="89433-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="89433-145">Para verificar se a licença foi realmente removida, use Get-MsoIUser para verificar a conta de usuário em questão:</span><span class="sxs-lookup"><span data-stu-id="89433-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="89433-146">Se tudo correu, propriedade **isLicensed** de Belinda agora será definida `False`:</span><span class="sxs-lookup"><span data-stu-id="89433-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="89433-p107">Outra maneira para liberar uma licença é, excluindo a conta de usuário. Para obter mais informações, consulte [Excluir e restaurar as contas de usuário com o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="89433-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89433-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="89433-149">See also</span></span>

<span data-ttu-id="89433-150">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="89433-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="89433-151">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89433-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="89433-152">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89433-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="89433-153">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="89433-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="89433-154">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="89433-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="89433-155">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="89433-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="89433-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="89433-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="89433-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="89433-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="89433-158">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="89433-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="89433-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="89433-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="89433-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="89433-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="89433-161">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="89433-161">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

