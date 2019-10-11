---
title: Configurar propriedades da conta de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumo: Use o Office 365 PowerShell para configurar propriedades de várias contas de usuário ou individuais em seu locatário do Office 365.'
ms.openlocfilehash: 40d7e78b3fd6c011f6c53b2af433f258b888d5bb
ms.sourcegitcommit: ecfa362182f906befa885bf5f0094528ff570779
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "37435345"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurar propriedades da conta de usuário com o Office 365 PowerShell

 **Resumo:** Use o Office 365 PowerShell para configurar propriedades de várias contas de usuário ou individuais em seu locatário do Office 365.
  
Embora você possa usar o centro de administração do Microsoft 365 para configurar as propriedades das contas de usuário do seu locatário do Office 365, você também pode usar o Office 365 PowerShell e realizar algumas coisas que o centro de administração não pode.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Para configurar propriedades de contas de usuário com o módulo PowerShell do Azure Active Directory para Graph, use o cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) e especifique as propriedades a serem definidas ou alteradas. 

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
   
### <a name="change-properties-for-a-specific-user-account"></a>Alterar as propriedades de uma conta de usuário específica

Você identifica a conta com o parâmetro **-ObjectID** e define ou altera propriedades específicas com parâmetros adicionais. Veja a seguir uma lista dos parâmetros mais comuns.
  
- -Department "\<nome do departamento>"
    
- -DisplayName "\<nome de usuário completo>"
    
- -FacsimilieTelephoneNumber "\<número de fax>"
    
- -Exnamename\<"nome de usuário>"
    
- -Sobrenome "\<último nome do usuário>"
    
- – "\<Número de telefone celular>" móvel
    
- -JobTitle "\<título do trabalho>"
    
- -PreferredLanguage "\<idioma>"
    
- -StreetAddress "\<endereço>"
    
- -City "\<nome da cidade>"
    
- -State "\<nome do estado>"
    
- -PostalCode "\<> de código postal"
    
- -País "\<nome do país>"
    
- -TelephoneNumber "\<número de telefone do Office>"
    
- -UsageLocation "\<código de país ou região de 2 caracteres>"
    
    Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.
    
Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parâmetros adicionais.


Para exibir o nome principal do usuário para suas contas de usuário, execute o seguinte comando.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().
    
- Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **objeto Sort userPrincipalName** ) e envie-o para **|** o próximo comando ().
    
- Exibe apenas a propriedade nome principal do usuário para cada conta ( **Select-Object userPrincipalName** ).
- Exibir uma tela por vez ( **mais** ).
    
Este comando listará todas as suas contas. Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e, em seguida, execute os seguintes comandos:
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este exemplo exibe o nome principal do usuário para a conta de usuário com o nome de exibição de Carlos Lima.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição. Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Alterar propriedades de todas as contas de usuário

Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-AzureADUser** e **set-AzureADUser** . O exemplo a seguir altera o local de uso de todos os usuários para a França:
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().
    
- Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Alterar propriedades de um conjunto específico de contas de usuário

Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-AzureADUser**, **Where**e **set-AzureADUser** . O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().
    
- Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().
    
- Defina o local do usuário como França ( **set-AzureADUser-UsageLocation "fr"** ).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Para configurar propriedades de contas de usuário com o módulo Microsoft Azure Active Directory para Windows PowerShell, use o cmdlet Set-MsolUser e especifique as propriedades a serem definidas ou alteradas. 

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="change-properties-for-a-specific-user-account"></a>Alterar as propriedades de uma conta de usuário específica

Para configurar as propriedades de uma conta de usuário específica, use o cmdlet [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) e especifique as propriedades a serem definidas ou alteradas. 

Você identifica a conta com o parâmetro **-userPrincipalName** e define ou altera propriedades específicas com parâmetros adicionais. Veja a seguir uma lista dos parâmetros mais comuns.
  
- -City "\<nome da cidade>"
    
- -País "\<nome do país>"
    
- -Department "\<nome do departamento>"
    
- -DisplayName "\<nome de usuário completo>"
    
- – Fax "\<número de fax>"
    
- -FirstName "\<nome do usuário>"
    
- -LastName "\<último nome do usuário>"
    
- -MobilePhone "\<número de telefone celular>"
    
- -Office "\<local do Office>"
    
- -PhoneNumber "\<número de telefone do Office>"
    
- -PostalCode "\<> de código postal"
    
- -PreferredLanguage "\<idioma>"
    
- -State "\<nome do estado>"
    
- -StreetAddress "\<endereço>"
    
- -Title "\<nome do título>"
    
- -UsageLocation "\<código de país ou região de 2 caracteres>"
    
    Este é o código de país ou região ISO 3166-1 alfa-2 (a2) de duas letras.
    
Consulte [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parâmetros adicionais.

Para ver os nomes principais de usuário de todos os seus usuários, execute o seguinte comando.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().
    
- Classifique a lista de nomes de entidade de segurança de usuário alfabeticamente ( **objeto Sort userPrincipalName** ) e envie-o para **|** o próximo comando ().
    
- Exibe apenas a propriedade nome principal do usuário para cada conta ( **Select-Object userPrincipalName** ).
    
- Exibir uma tela por vez ( **mais** ).
    
Este comando listará todas as suas contas. Se você deseja exibir o nome principal de usuário para uma conta com base no seu nome de exibição (nome e sobrenome), preencha a variável de **$username** abaixo (removendo os \< caracteres e >) e, em seguida, execute os seguintes comandos:
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este exemplo exibe o nome principal do usuário chamado Carlos Lima.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Usando uma variável de **$UPN** , você pode fazer alterações em contas individuais com base no seu nome de exibição. Aqui está um exemplo de como definir o local de uso do Belinda Newman para a França, mas especificando seu nome de exibição em vez do nome principal do usuário:
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Alterar propriedades de todas as contas de usuário

Para alterar as propriedades de todos os usuários, você pode usar a combinação dos cmdlets **Get-MsolUser** e **set-MsolUser** . O exemplo a seguir altera o local de uso de todos os usuários para a França:
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().
    
- Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Alterar propriedades de um conjunto específico de contas de usuário

Para alterar as propriedades de um conjunto específico de contas de usuário, você pode usar a combinação dos cmdlets **Get-MsolUser**, **Where-Object**e **set-MsolUser** . O exemplo a seguir altera o local de uso de todos os usuários no departamento de contabilidade para a França:
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().
    
- Encontre todas as contas de usuário que têm a propriedade Department definida como "Accounting" ( **onde-Object {$ _. Department-EQ "Accounting"}** ) e envie as informações resultantes para o **|** próximo comando ().
    
- Defina o local do usuário como França ( **set-MsolUser-UsageLocation "fr"** ).
    

## <a name="see-also"></a>Confira também

[Gerenciar licenças e contas de usuário usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
