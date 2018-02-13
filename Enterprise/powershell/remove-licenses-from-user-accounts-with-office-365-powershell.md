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
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Remover licenças de contas de usuários com o Office 365 PowerShell

**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.
  
## <a name="before-you-begin"></a>Antes de começar

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:
    
  - [Exibir licenças e serviços com o PowerShell do Office 365](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.
    
## <a name="the-short-version-instructions-without-explanations"></a>A versão curta (instruções sem explicações)
<a name="ShortVersion"> </a>

Esta seção apresenta os procedimentos sem divulgação ou explicação supérflua. Se você tiver dúvidas ou se quiser obter mais informações, leia o restante do tópico.
  
Para remover licenças de uma conta de usuário existente, use a seguinte sintaxe:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Para remover licenças de um grupo de usuários licenciados existentes, use um dos seguintes métodos:
  
- **Filter the accounts based on an existing account attribute** To do this, use the following syntax:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Use a list of specific accounts** To do this, perform the following steps:
    
1. Crie e salve um arquivo de texto que contenha uma conta em cada linha da seguinte forma:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Use a sintaxe a seguir:
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Para remover licenças de todas as contas de usuário existentes, use a seguinte sintaxe:
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>A versão longa (instruções com explicações detalhadas)
<a name="LongVersion"> </a>

Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.
  
Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.
  
And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Run that command, and Belinda Newman will no longer be licensed to use Office 365.
  
> [!NOTE]
> As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
Para verificar se a licença foi realmente removida, use Get-MsoIUser para verificar a conta de usuário em questão:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Veja também

Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Criar contas de usuários usando o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear contas de usuários com o Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Atribuir licenças a contas de usuários usando o PowerShell do Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>Começando a usar o Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

