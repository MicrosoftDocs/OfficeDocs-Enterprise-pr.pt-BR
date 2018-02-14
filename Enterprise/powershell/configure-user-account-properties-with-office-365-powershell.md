---
title: "Configurar propriedades da conta de usuário com o Office 365 PowerShell"
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "Resumo: Usar o PowerShell do Office 365 para configurar propriedades de um indivíduo ou várias contas de usuário no seu locatário do Office 365."
ms.openlocfilehash: 60b3c1d91df0cb28f19f60a285093de7337904a9
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurar propriedades da conta de usuário com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para configurar propriedades de um indivíduo ou várias contas de usuário no seu locatário do Office 365.
  
Embora você possa usar o Centro de administração do Office 365 para configurar propriedades para as contas de usuário do seu locatário do Office 365, você também pode usar o PowerShell do Office 365 e fazer algumas coisas que não é possível o Centro de administração do Office 365.
  
## <a name="before-you-begin"></a>Antes de começar

Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
  
## <a name="change-properties-for-a-specific-user-account"></a>Alterar as propriedades de uma conta de usuário específica

Para configurar as propriedades de uma conta de usuário específico, você use o cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e especifique as propriedades para definir ou alterar. Este exemplo de comando altera o local de uso de Belinda Newman para França:
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Identificar a conta com o parâmetro **- UserPrincipalName** e definir ou alterar propriedades específicas com parâmetros adicionais. Aqui está uma lista dos parâmetros mais comuns.
  
- -Cidade "\<nome da cidade >"
    
- -País "\<nome do país >"
    
- -Departamento "\<nome de departamento >"
    
- -DisplayName "\<nome completos do usuário >"
    
- -Fax "\<número de fax >"
    
- -FirstName "\<nome usuário >"
    
- -LastName "\<sobrenome do usuário >"
    
- -MobilePhone "\<o número de telefone celular >"
    
- -Office "\<local do escritório >"
    
- -PhoneNumber "\<o número de telefone do escritório >"
    
- -PostalCode "\<CEP >"
    
- -PreferredLanguage "\<idioma >"
    
- -State "\<estado nome >"
    
- -StreetAddress "\<endereço >"
    
- -Title "\<nome título >"
    
- -UsageLocation "\<código de país ou região 2 caracteres >"
    
    Este é o código de região ou país com duas letras ISO 3166-1 alpha-2 (A2).
    
Consulte [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parâmetros adicionais.
  
Para ver os nomes de entidade de usuário de todos os seus usuários, execute o seguinte comando.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Classifique a lista de nomes de entidade de usuário em ordem alfabética ( **Objeto Sort UserPrincipalName** ) e enviá-lo para o próximo comando ( **|** ).
    
- Exiba apenas a propriedade de nome Principal de usuário para cada conta ( **UserPrincipalName Select-Object** ).
    
- Exibi-las uma tela por vez ( **mais** ).
    
Esse comando listará todas as suas contas. Se você quiser exibir o nome Principal de usuário para uma conta com base em sua exibição nome (nome e sobrenome), preencha a variável **$userName** abaixo (removendo o \< e > caracteres), e, em seguida, execute os seguintes comandos:
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este exemplo exibe o nome Principal de usuário para o usuário chamado Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Usando uma variável de **$upn** , você pode fazer alterações para contas individuais com base em seu nome para exibição. Aqui está um exemplo de definição de local de uso de Belinda Newman como França, mas especificando seu nome para exibição em vez de seu nome Principal de usuário:
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>Alterar propriedades para todas as contas de usuário

Para alterar propriedades para todos os usuários, você pode usar a combinação dos cmdlets **Get-MsolUser** e **Set-MsolUser** . O exemplo a seguir altera o local de uso para todos os usuários para França:
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Defina o local do usuário para França ( **Set-MsolUser-UsageLocation "FR"** ).
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Alterar as propriedades de um conjunto específico de contas de usuário

Para alterar propriedades para um conjunto específico de conta de usuário, você pode usar a combinação dos cmdlets **Get-MsolUser**, **Where-Object**e **Set-MsolUser** . O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para França:
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Localizar todas as contas de usuário que tenham sua propriedade departamento definido como "Accounting" ( **Where-Object {$_. Departamento - eq "Accounting"}** ) e enviar as informações resultantes para o próximo comando ( **|** ).
    
- Defina o local do usuário para França ( **Set-MsolUser-UsageLocation "FR"** ).
    
- Exibi-las uma tela por vez ( **mais** ).
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Use o módulo do Azure Active Directory V2 PowerShell para configurar propriedades da conta de usuário

Para configurar as propriedades de contas de usuário com o módulo do Azure Active Directory PowerShell V2, você use o cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e especifique as propriedades para definir ou alterar. Mas, primeiro, você deve se conectar à sua assinatura. Para ver as instruções, consulte [Connect com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="change-properties-for-a-specific-user-account"></a>Alterar as propriedades de uma conta de usuário específica

Este exemplo de comando altera o local de uso de Belinda Newman para França:
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Identificar a conta com o parâmetro **- ObjectID** e definir ou alterar propriedades específicas com parâmetros adicionais. Aqui está uma lista dos parâmetros mais comuns.
  
- -Departamento "\<nome de departamento >"
    
- -DisplayName "\<nome completos do usuário >"
    
- -FacsimilieTelephoneNumber "\<número de fax >"
    
- -GivenName "\<nome usuário >"
    
- -Sobrenome "\<sobrenome do usuário >"
    
- -Móvel "\<o número de telefone celular >"
    
- -JobTitle "\<cargo >"
    
- -PreferredLanguage "\<idioma >"
    
- -StreetAddress "\<endereço >"
    
- -Cidade "\<nome da cidade >"
    
- -State "\<estado nome >"
    
- -PostalCode "\<CEP >"
    
- -País "\<nome do país >"
    
- -TelephoneNumber "\<o número de telefone do escritório >"
    
- -UsageLocation "\<código de país ou região 2 caracteres >"
    
    Este é o código de região ou país com duas letras ISO 3166-1 alpha-2 (A2).
    
Consulte [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parâmetros adicionais.
  
Para exibir o nome Principal de usuário para suas contas de usuário, execute o seguinte comando.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Classifique a lista de nomes de entidade de usuário em ordem alfabética ( **Objeto Sort UserPrincipalName** ) e enviá-lo para o próximo comando ( **|** ).
    
- Exiba apenas a propriedade de nome Principal de usuário para cada conta ( **UserPrincipalName Select-Object** ).
- Exibi-las uma tela por vez ( **mais** ).
    
Esse comando listará todas as suas contas. Se você quiser exibir o nome Principal de usuário para uma conta com base em sua exibição nome (nome e sobrenome), preencha a variável **$userName** abaixo (removendo o \< e > caracteres), e, em seguida, execute os seguintes comandos:
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este exemplo exibe o nome Principal de usuário para o usuário chamado Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Usando uma variável de **$upn** , você pode fazer alterações para contas individuais com base em seu nome para exibição. Aqui está um exemplo de definição de local de uso de Belinda Newman como França, mas especificando seu nome para exibição em vez de seu nome Principal de usuário:
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Alterar propriedades para todas as contas de usuário

Para alterar propriedades para todos os usuários, você pode usar a combinação dos cmdlets **Get-AzureADUser** e **Set-AzureADUser** . O exemplo a seguir altera o local de uso para todos os usuários para França:
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Defina o local do usuário para França ( **Set-AzureADUser-UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Alterar as propriedades de um conjunto específico de contas de usuário

Para alterar propriedades para um conjunto específico de conta de usuário, você pode usar a combinação dos cmdlets **Get-AzureADUser**, **onde**e **Set-AzureADUser** . O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para França:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Localizar todas as contas de usuário que tenham sua propriedade departamento definida como "Accounting" ( **onde {$_. Departamento - eq "Accounting"}** ) e enviar as informações resultantes para o próximo comando ( **|** ).
    
- Defina o local do usuário para França ( **Set-AzureADUser-UsageLocation "FR"** ).
    
## <a name="see-also"></a>Veja também

#### 

[Gerenciar contas de usuário e licenças usando o PowerShell do Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

