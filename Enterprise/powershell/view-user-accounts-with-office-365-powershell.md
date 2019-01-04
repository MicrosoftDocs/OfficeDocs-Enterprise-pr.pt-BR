---
title: Exibir as contas de usuário com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
description: 'Resumo: Assista, listar ou exibir suas contas de usuário de diversas maneiras com o Office 365 PowerShell.'
ms.openlocfilehash: dc33b64207341576968867fbeea6f211034eeca6
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546522"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Exibir as contas de usuário com o Office 365 PowerShell

**Resumo:** Exiba suas contas de usuário de diversas maneiras com o Office 365 PowerShell.
  
Embora você possa usar o Centro de administração do Office 365 para exibir as contas para seu locatário do Office 365, você também pode usar o Office 365 PowerShell e fazer algumas coisas que não é possível o Centro de administração do Office 365.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo de gráfico

Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Exibir todas as contas

Para exibir a lista completa das contas de usuário, execute este comando:
  
```
Get-AzureADUser
```

Você deverá ver informações parecidas com estas:
  
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

Para exibir uma conta de usuário específica, preencha o nome principal do usuário (UPN) da conta de usuário, remova o "<" e ">" caracteres e execute este comando:
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Exibir valores de propriedades adicionais para uma conta específica

Por padrão, o cmdlet **Get-AzureADUser** exibe apenas as propriedades ObjectID, DisplayName e UserPrincipalName das contas.

Para ser mais seletiva sobre a lista de propriedades para exibir, você pode usar o cmdlet **Select-Object** em combinação com o cmdlet **Get-AzureADUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa o Azure Active Directory PowerShell para o gráfico obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe o DisplayName, departamento e UsageLocation para cada conta de usuário:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Este comando instrui o Office 365 PowerShell para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Exibe somente o usuário nome, departamento e uso local da conta ( **Select-Object DisplayName, departamento, UsageLocation** ).
  
Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Como outro exemplo, é possível verificar o status ativado de uma conta de usuário específico com o seguinte comando:
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Exibir alguns contas com base em uma propriedade comum

Para ser mais seletiva sobre a lista de contas para exibir, você pode usar o cmdlet **Where-Object** em combinação com o cmdlet **Get-AzureADUser** . Para combinar os dois cmdlets, usamos o caractere "pipe" "|", que informa o Azure Active Directory PowerShell para o gráfico obter os resultados de um comando e enviá-lo para o próximo comando. Aqui está um exemplo de comando que exibe apenas as contas de usuário que têm um local de uso não especificado:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando instrui o Azure Active Directory PowerShell para o gráfico para:
  
- Obtenha todas as informações sobre as contas de usuário ( **Get-AzureADUser** ) e enviá-lo para o próximo comando ( **|** ).
    
- Localizar todas as contas de usuário que têm um local de uso não especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Dentro das chaves, o comando instrui o Office 365 PowerShell encontrar apenas o conjunto de contas no qual o usuário UsageLocation conta propriedade ( ** $ \_. UsageLocation** ) não é especificado ( **-eq $Null** ).
    
A propriedade **UsageLocation** é apenas uma das muitas propriedades associadas a uma conta de usuário. Para ver todas as propriedades para contas de usuário, use o cmdlet **Select-Object** e o caractere curinga (*) para exibir todos eles para uma conta de usuário específico. Aqui está um exemplo:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Por exemplo, nessa lista, **Cidade** é o nome de uma propriedade de conta de usuário. Isso significa que você pode usar o seguinte comando para listar todas as contas de usuário para usuários mora em Londres:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  A sintaxe para o cmdlet **Where-Object** mostrada neste exemplo é **Where-Object {$\_.** [nome de propriedade de conta do usuário] [operador de comparação] [valor] **}**. > [operador de comparação] é **-eq** for igual a, **-ne** para não é igual a, **-lt** for menor que, **-gt** para maior e outros.  [valor] é geralmente uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$Null** para não for especificado > consulte [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obter mais informações.
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o módulo do Microsoft Azure Active Directory para o Windows PowerShell

Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Exibir todas as contas

Para exibir a lista completa das contas de usuário, execute este comando:
  
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

Para obter mais informações sobre parâmetros adicionais para filtrar a exibição o conjunto de contas de usuário exibida, consulte [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="view-a-specific-account"></a>Exibir uma conta específica

Para exibir uma conta de usuário específica, preencha o nome principal do usuário (UPN) da conta de usuário, remova o "<" e ">" caracteres e execute este comando:
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Exibir alguns contas com base em uma propriedade comum

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
>  A sintaxe para o cmdlet **Where-Object** mostrada neste exemplo é **Where-Object {$\_.** [nome de propriedade de conta do usuário] [operador de comparação] [valor] **}**.  [operador de comparação] é **-eq** for igual a, **-ne** para não é igual a, **-lt** for menor que, **-gt** para maior e outros.  [valor] é geralmente uma cadeia de caracteres (uma sequência de letras, números e outros caracteres), um valor numérico ou **$Null** para não for especificado. Para obter mais informações, consulte o [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
Você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Exibir valores de propriedades adicionais para contas

O cmdlet **Get-MsolUser** por padrão exibe três propriedades de contas de usuário:
  
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
Scott Wallace           Operations
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

Se você estiver usando a sincronização de diretórios para criar e gerenciar os usuários do Office 365, você pode exibir qual um usuário do Office 365 tenha sido projetado de conta local. A seguir pressupõe que se conectar do Azure AD foi configurada para usar a âncora de fonte padrão do ObjectGUID (para obter mais informações sobre como configurar uma âncora de origem, consulte [Connect do Azure AD: conceitos de projeto](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) e pressupõe que o módulo do Active Directory para o powershell tem foi instalado (consulte [Ferramentas RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a>Confira também

[Gerenciar contas de usuário e licenças usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)

