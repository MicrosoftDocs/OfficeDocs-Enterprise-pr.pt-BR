---
title: "Exibir as contas de usuário com o Office 365 PowerShell"
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "Resumo: Assista, listar ou exibir suas contas de usuário de diversas maneiras com o Office 365 PowerShell."
ms.openlocfilehash: e9ffa439c1840cbbbd8a47c2835d9427330804be
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Exibir as contas de usuário com o Office 365 PowerShell

 **Resumo:** Exibir, listar ou exibir suas contas de usuário de diversas maneiras com o Office 365 PowerShell.
  
Embora você possa usar o Centro de administração do Office 365 para exibir as contas para seu locatário do Office 365, você também pode usar o Office 365 PowerShell e fazer algumas coisas que não é possível o Centro de administração do Office 365.
  
## <a name="before-you-begin"></a>Antes de começar

Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
  
## <a name="display-office-365-user-account-information"></a>Exibir informações da conta de usuário do Office 365

Para exibir a lista completa das contas de usuário, execute este comando no prompt de comando seu Office 365 PowerShell ou o ambiente de Script integrado PowerShell (ISE).
  
```
Get-MsolUser
```

Você deverá ver informações parecidas com estas:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

O cmdlet **Get-MsolUser** também tem um conjunto de parâmetros para filtrar o conjunto de contas de usuário exibida. Por exemplo, para a lista de usuários não licenciados (usuários que foram adicionados ao Office 365, mas ainda não foram licenciados para usar qualquer um dos serviços), execute este comando.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Você deverá ver informações parecidas com estas:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Para obter mais informações sobre parâmetros adicionais para filtrar a exibição o conjunto de contas de usuário exibida, consulte [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .
  
Para ser mais seletiva sobre a lista de contas para exibir, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-MsolUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Office 365 PowerShell para obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).
    
Você deverá ver informações parecidas com estas:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Por exemplo, nessa lista, **Cidade** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários mora em Londres:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  A sintaxe para o cmdlet **Where-Object** mostrada neste exemplo é **Where-Object {$\_.** [nome de propriedade de conta do usuário] [operador de comparação] [valor] **}**. > [operador de comparação] é **-eq** for igual a, **-ne** para não é igual a, **-lt** for menor que, **-gt** para maior e outros > [valor] normalmente é uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$Null** para não for especificado > consulte [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obter mais informações.
  
Você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>Selecionar as propriedades da conta de usuário a serem exibidas

O cmdlet [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) por padrão exibe três propriedades de contas de usuário:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Se você precisar propriedades adicionais, como o departamento que o usuário trabalha e o país/região onde o usuário usa os serviços do Office 365, você pode executar o **Get-MsolUser** em combinação com o cmdlet **Select-Object** para especificar a lista de conta de usuário Propriedades. Aqui está um exemplo:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).
    
Você deverá ver informações parecidas com estas:
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

O cmdlet **Select-Object** permite que você escolher as propriedades que você deseja exibir um comando. Para ver todas as propriedades para contas de usuário, use o caractere curinga (*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Para ser mais seletiva sobre a lista de contas para exibir, você também pode usar o cmdlet **Where-Object** . Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e enviar as informações resultantes para o próximo comando ( **|** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).
    
- Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).
    
Você deverá ver informações parecidas com estas:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>Use o módulo do Azure Active Directory PowerShell V2 para exibir as contas de usuário

Para exibir propriedades de contas de usuário com o módulo do Azure Active Directory PowerShell V2, você deve usar o cmdlet [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Mas, primeiro, você deve se conectar à sua assinatura. Para ver as instruções, consulte[Connect com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="display-office-365-user-account-information"></a>Exibir informações da conta de usuário do Office 365

Para exibir a lista completa das contas de usuário, execute este comando no prompt de comando seu Office 365 PowerShell ou o ambiente de Script integrado PowerShell (ISE).
  
```
Get-AzureADUser
```

O cmdlet **Get-AzureADUser** por padrão exibe três propriedades de contas de usuário:
  
- ObjectID
    
- DisplayName
    
- UserPrincipalName
    
Para ser mais seletiva sobre a lista de contas para exibir, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-AzureADUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Office 365 PowerShell para obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).
    
A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibir todos eles para uma conta de usuário específico, uma página de cada vez ( **mais** ). Aqui está um exemplo:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

Por exemplo, **Cidade** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários mora em Londres:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  A sintaxe para o cmdlet **Where-Object** mostrada neste exemplo é **Where-Object {$\_.** [nome de propriedade de conta do usuário] [operador de comparação] [valor] **}**. > [operador de comparação] é **-eq** for igual a, **-ne** para não é igual a, **-lt** for menor que, **-gt** para maior e outros > [valor] normalmente é uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$Null** para não for especificado > consulte[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obter mais informações.
  
### <a name="select-the-user-account-properties-to-display"></a>Selecionar as propriedades da conta de usuário a serem exibidas

O cmdlet **Get-AzureADUser** por padrão exibe as propriedades ObjectID, DisplayName e UserPrincipalName das contas de usuário. Se você precisar propriedades adicionais, como o departamento que o usuário trabalha e o país/região onde o usuário usa os serviços do Office 365, é possível executar **Get-AzureADUser** em combinação com o cmdlet **Select-Object** para especificar a lista de usuário Propriedades da conta. Aqui está um exemplo:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).
    
Para ser mais seletiva sobre a lista de contas para exibir, você também pode usar o cmdlet **Where-Object** . Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) e enviar as informações resultantes para o próximo comando ( **|** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).
    
- Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).
    
## <a name="new-to-office-365"></a>Começando a usar o Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a>Confira também

#### 

[Gerenciar contas de usuário e licenças usando o PowerShell do Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

