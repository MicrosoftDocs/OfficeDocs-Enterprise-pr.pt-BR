---
title: Exibir as contas de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
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
description: 'Resumo: exiba, liste ou exiba suas contas de usuário de várias maneiras com o Office 365 PowerShell.'
ms.openlocfilehash: 717a7c11f4e7f6d2e5e0c452854df7d4c419007e
ms.sourcegitcommit: 1dc7b4731cf9899c5ae867624ed142dbab0c517f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30683698"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Exibir as contas de usuário com o Office 365 PowerShell

**Resumo:** Exiba suas contas de usuário de várias maneiras com o Office 365 PowerShell.
  
Embora você possa usar o centro de administração do Office 365 para exibir as contas do seu locatário do Office 365, você também pode usar o Office 365 PowerShell e fazer algumas coisas que o centro de administração do Office 365 não pode.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Exibir todas as contas

Para exibir a lista completa de contas de usuário, execute este comando:
  
```
Get-AzureADUser
```

Você deve ver informações semelhantes a estas:
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>Exibir uma conta específica

Para exibir uma conta de usuário específica, preencha o nome da conta de logon da conta de usuário, também conhecida como nome UPN, remova os caracteres "<" e ">" e execute este comando:
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Veja um exemplo:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Exibir valores de propriedade adicionais para uma conta específica

Por padrão, o cmdlet **Get-AzureADUser** exibe apenas as propriedades ObjectID, DisplayName e userPrincipalName de accounts.

Para ser mais seletivo sobre a lista de propriedades a serem exibidas, você pode usar o cmdlet **Select-Object** em combinação com o cmdlet **Get-AzureADUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Azure Active Directory PowerShell para Graph para obter os resultados de um comando e enviá-lo para o próximo comando. Veja a seguir um exemplo de comando que exibe o DisplayName, o departamento e o UsageLocation para cada conta de usuário:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().
    
- Exibir apenas o nome da conta de usuário, o departamento e o local de uso ( **Select-Object DisplayName, Department, UsageLocation** ).
  
Para ver todas as propriedades de contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibi-los para uma conta de usuário específica. Veja um exemplo:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Como outro exemplo, você pode verificar o status habilitado de uma conta de usuário específica com o seguinte comando:
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Exibir algumas contas com base em uma propriedade comum

Para ser mais seletivo sobre a lista de contas a serem exibidas, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-AzureADUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa ao Azure Active Directory PowerShell para Graph para obter os resultados de um comando e enviá-lo para o próximo comando. Veja a seguir um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando instrui o Azure Active Directory PowerShell para Graph para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e envie-o para o próximo comando **|** ().
    
- Encontre todas as contas de usuário que têm um local de uso não especificado ( **onde-objeto {\_$. UsageLocation-EQ $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell a localizar apenas o conjunto de contas no qual a propriedade da conta de usuário do UsageLocation ( ** $ \_. UsageLocation** ) não é especificado ( **-EQ $NULL** ).
    
A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades de contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibi-los para uma conta de usuário específica. Veja um exemplo:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Por exemplo, na lista, **City** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários em Londres:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  A sintaxe do cmdlet **Where-Object** mostrado nesses exemplos é **onde-Object {$\_.** [nome da propriedade da conta de usuário] [operador de comparação] valor **}**. > [operador de comparação] é **-EQ** para igual a, **-ne** para não igual a, **-lt** para menor que, **-gT** para maior que e outros.  [value] normalmente é uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$NULL** para Unspecified> ver [onde-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obter mais informações.
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Exibir todas as contas

Para exibir a lista completa de contas de usuário, execute este comando:
  
```
Get-MsolUser
```

Você deve ver informações semelhantes a estas:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

O cmdlet **Get-MsolUser** também tem um conjunto de parâmetros para filtrar o conjunto de contas de usuário exibidas. Por exemplo, para a lista de usuários não licenciados (usuários que foram adicionados ao Office 365, mas que ainda não foram licenciados para usar qualquer um dos serviços), execute este comando.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Você deve ver informações semelhantes a estas:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Para obter mais informações sobre parâmetros adicionais para filtrar a exibição do conjunto de contas de usuário exibidas, consulte [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="view-a-specific-account"></a>Exibir uma conta específica

Para exibir uma conta de usuário específica, preencha o nome de entrada da conta de usuário da conta de usuário, também conhecida como nome de usuário principal (UPN), remova os caracteres "<" e ">" e execute este comando:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Exibir algumas contas com base em uma propriedade comum

Para ser mais seletivo sobre a lista de contas a serem exibidas, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-MsolUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que diz ao Office 365 PowerShell para obter os resultados de um comando e enviá-lo para o próximo comando. Veja a seguir um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().
    
- Encontre todas as contas de usuário que têm um local de uso não especificado ( **onde-objeto {\_$. UsageLocation-EQ $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell a localizar apenas o conjunto de contas no qual a propriedade da conta de usuário do UsageLocation ( ** $ \_. UsageLocation** ) não é especificado ( **-EQ $NULL** ).
    
Você deve ver informações semelhantes a estas:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades de contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibi-los para uma conta de usuário específica. Veja um exemplo:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Por exemplo, na lista, **City** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários em Londres:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  A sintaxe do cmdlet **Where-Object** mostrado nesses exemplos é **onde-Object {$\_.** [nome da propriedade da conta de usuário] [operador de comparação] valor **}**.  [operador de comparação] é **-EQ** para igual a, **-ne** para não é igual a, **-lt** para menor que, **-gt** para maior que e outros.  [value] normalmente é uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$NULL** para não especificado. ConFira [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obter mais informações.
  
Você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Exibir valores de propriedade adicionais para contas

Por padrão, o cmdlet **Get-MsolUser** exibe três propriedades de contas de usuário:
  
- Principal
    
- DisplayName
    
- isLicensed
    
Se você precisar de propriedades adicionais, como o departamento para o qual o usuário trabalha e o país/região em que o usuário usa os serviços do Office 365, você pode executar **Get-MsolUser** em combinação com o cmdlet **Select-Object** para especificar a lista de contas de usuário Propriedades. Veja um exemplo:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().
    
- Exibir apenas o nome da conta de usuário, o departamento e o local de uso ( **Select-Object DisplayName, Department, UsageLocation** ).
    
Você deve ver informações semelhantes a estas:
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

O cmdlet **Select-Object** permite que você escolha e escolha as propriedades que você deseja que um comando exiba. Para ver todas as propriedades de contas de usuário, use o caractere curinga (*) para exibi-las para uma conta de usuário específica. Veja um exemplo:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Para ser mais seletivo sobre a lista de contas a serem exibidas, você também pode usar o cmdlet **Where-Object** . Veja a seguir um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Este comando instrui o Office 365 PowerShell a:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-MsolUser** ) e envie-o para o próximo comando **|** ().
    
- Encontre todas as contas de usuário que têm um local de uso não especificado ( **onde-objeto {\_$. UsageLocation-EQ $Null}** ) e envie as informações resultantes para o próximo comando **|** (). Dentro das chaves, o comando está instruindo o Office 365 PowerShell a localizar apenas o conjunto de contas no qual a propriedade da conta de usuário do UsageLocation ( ** $ \_. UsageLocation** ) não é especificado ( **-EQ $NULL** ).
    
- Exibir apenas o nome da conta de usuário, o departamento e o local de uso ( **Select-Object DisplayName, Department, UsageLocation** ).
    
Você deve ver informações semelhantes a estas:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Se você estiver usando a sincronização de diretórios para criar e gerenciar seus usuários do Office 365, poderá exibir a conta local em que um usuário do Office 365 foi projetado. O seguinte pressupõe que o Azure AD Connect tenha sido configurado para usar a âncora de origem padrão de objectGUID (para saber mais sobre como configurar uma âncora de origem, confira [Azure ad Connect: design Concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) e pressupõe que o módulo do Active Directory para o PowerShell tenha foi instalado (consulte [ferramentas de RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a>Confira também

[Gerenciar licenças e contas de usuário usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

