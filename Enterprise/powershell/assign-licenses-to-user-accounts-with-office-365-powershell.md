---
title: Atribuir licenças a contas de usuários usando o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Explica como usar o Office 365 PowerShell para atribuir uma licença do Office 365 para usuários não licenciados.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123288"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Atribuir licenças a contas de usuários usando o PowerShell do Office 365

**Resumo:** explica como usar o Office 365 PowerShell para atribuir uma licença do Office 365 para usuários não licenciados.
  
O licenciamento de contas de usuário no Office 365 é importante, porque os usuários não poderão usar nenhum serviço do Office 365 até que suas contas sejam licenciadas. Você pode usar o Office 365 PowerShell para atribuir licenças de forma eficiente para contas não licenciadas, especialmente para várias contas. 

## <a name="before-you-begin"></a>Antes de começar
<a name="RTT"> </a>

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Use o cmdlet **Get-MsolAccountSku** para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano na sua organização. O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para mais informações sobre planos de licenciamento, licenças e serviços, confira [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Para localizar as contas não licenciadas em sua organização, execute o comando  `Get-MsolUser -All -UnlicensedUsersOnly`
    
- Você só pode atribuir licenças para contas de usuário que tenham o conjunto de propriedades **UsageLocation** definido como um código de país ISO 3166-1 alpha-2 válido. Por exemplo, US para os Estados Unidos e FR para a França. Alguns serviços do Office 365 não estão disponíveis em certos países. Para mais informações, confira [Sobre restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Para localizar contas que não tenham um valor **UsageLocation**, execute o comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Para definir o valor **UsageLocation** em uma conta, use a sintaxe `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Por exemplo,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro `-All`, somente as primeiras 500 contas serão retornadas.

## <a name="assigning-licenses-to-user-accounts"></a>Atribuir licenças às contas de usuário
    
Para atribuir uma licença a um usuário, use a seguinte sintaxe no Office 365 PowerShell:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

Este exemplo atribui uma licença do plano de licenciamento do `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ao usuário não licenciado `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Para atribuir uma licença a vários usuários sem licença, use a seguinte sintaxe:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Anotações**
  
- Você não pode atribuir várias licenças a um usuário do mesmo plano de licenciamento.
    
- Se você não tiver licenças o suficiente disponíveis, as licenças serão atribuídas aos usuários na ordem em que eles forem retornados pelo cmdlet **Get-MsolUser** até que as licenças disponíveis esgotem.
    
Este exemplo atribui licenças do plano de licenciamento do `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) a todos os usuários não licenciados.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

Este exemplo atribui essas mesmas licenças a usuários não licenciados no Departamento de vendas nos Estados Unidos.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Começando a usar o Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Confira também
<a name="SeeAlso"> </a>

Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Criar contas de usuário](create-user-accounts-with-office-365-powershell.md)
    
- [Exclua e restaure contas de usuário](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Contas de usuário do bloco](block-user-accounts-with-office-365-powershell.md)
    
- [Remover licenças de contas de usuário](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

