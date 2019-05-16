---
title: Remover licenças de contas de usuários com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/07/2019
audience: Admin
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
description: Explica como usar o Office 365 PowerShell para remover as licenças do Office 365 que foram previamente atribuídas aos usuários.
ms.openlocfilehash: 80b708e5ce2d16f65ed02681d8f3e00a7fe33fcb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068737"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Remover licenças de contas de usuários com o Office 365 PowerShell

**Resumo:** Explica como usar o Office 365 PowerShell para remover as licenças do Office 365 que foram previamente atribuídas aos usuários.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

Em seguida, liste os planos de licença para seu locatário com este comando.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Em seguida, obtenha o nome de entrada da conta para a qual você deseja remover uma licença, também conhecido como o nome de usuário principal (UPN).

Por fim, especifique os nomes de entrada e de plano de licença do usuário, remova os caracteres "<" e ">" e execute esses comandos.

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

   
Para exibir as informações do plano de licenciamento (**AccountSkuID** ) em sua organização, consulte os seguintes tópicos:
    
  - [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
    
Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _-All_, somente as primeiras 500 contas serão retornadas.
    
### <a name="removing-licenses-from-user-accounts"></a>Removendo licenças de contas de usuário

Para remover licenças de uma conta de usuário existente, use a seguinte sintaxe:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

Este exemplo remove a `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) da conta de usuário BelindaN@litwareinc.com.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>Você não pode usar o cmdlet Set-MsolUserLicense para cancelar a atribuição ** de usuários de licenças canceladas. Você deve fazer isso individualmente para cada conta de usuário no centro de administração do Microsoft 365.
>

Para remover licenças de um grupo de usuários licenciados existentes, use um dos seguintes métodos:
  
- **Filtrar as contas com base em um atributo de conta existente** Para fazer isso, use a seguinte sintaxe:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Este exemplo remove as `litwareinc:ENTERPRISEPACK` licenças (Office 365 Enterprise E3) de todas as contas de usuários no departamento de vendas nos Estados Unidos.
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:
    
1. Crie e salve um arquivo de texto que contenha uma conta em cada linha da seguinte forma:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Use a sintaxe a seguir:
    
  ```
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

Este exemplo remove a `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) das contas de usuário definidas no arquivo de texto c:\Meus Documents\Accounts.txt.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

Para remover licenças de todas as contas de usuário existentes, use a seguinte sintaxe:
  
```
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Este exemplo remove a `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) de todas as contas de usuário licenciado existentes.
  
```
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

Outra maneira de liberar uma licença é excluir a conta de usuário. Para obter mais informações, consulte [excluir e restaurar contas de usuário com o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Confira também

[Gerenciar licenças e contas de usuário usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>Começando a usar o Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

