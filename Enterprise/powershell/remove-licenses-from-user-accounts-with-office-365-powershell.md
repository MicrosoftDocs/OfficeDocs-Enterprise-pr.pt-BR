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
ms.openlocfilehash: d419aab9b3287364567e03accdfb2e687eacb0de
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Remover licenças de contas de usuários com o Office 365 PowerShell

**Resumo:** Explica como usar o Office 365 PowerShell para remover licenças do Office 365 que previamente atribuídas aos usuários.
  
## <a name="before-you-begin"></a>Antes de começar

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Para exibir as informações de licenciamento plano ( **AccountSkuID** ) em sua organização, consulte os seguintes tópicos:
    
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

Este exemplo remove o `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) da conta de usuário BelindaN@litwareinc.com.
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Para remover licenças de um grupo de usuários licenciados existentes, use um dos seguintes métodos:
  
- **Filtrar as contas com base em um atributo existente da conta** Para fazer isso, use a seguinte sintaxe:
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Este exemplo remove o `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenças de opinião para usuários no departamento de vendas nos Estados Unidos.
    
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
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

Este exemplo remove o `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) das contas de usuário definidos no arquivo de texto C:\My Documents\Accounts.txt.
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

Para remover licenças de todas as contas de usuário existentes, use a seguinte sintaxe:
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

Este exemplo remove o `litwareinc:ENTERPRISEPACK` licença (Office 365 Enterprise E3) de todos os existentes licenciados contas de usuário.
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>A versão longa (instruções com explicações detalhadas)
<a name="LongVersion"> </a>

Nada dura indefinidamente e que inclui licenças do Office 365: cedo ou tarde, há virão vez quando você precisa remover a licença de uma conta de usuário. Talvez o usuário está acontecendo deixe; Talvez o usuário não precisa mais a licença; bem, talvez - há obviamente, qualquer número dos motivos por que talvez você queira remover uma licença de usuário.
  
Antes de prosseguir qualquer outra é importante observar que a remoção de uma licença requer que você, vamos, remova a licença: desabilitar todos os serviços em uma licença não é a mesma coisa que a remoção da licença. Por exemplo, suponha que usamos para cima todas as nossas licenças do Office 365; em outras palavras, temos não licenças disponíveis qualquer. Você decide siga o procedimento em [Desabilitar o acesso aos serviços do Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) para desabilitar todos os serviços, digamos, na conta de Belinda Newman. Depois que fazemos que, quantas licenças serão temos disponíveis para nós? É isso mesmo: zero. Sim, o procedimento daquele tópico irá *Desabilitar* todos os serviços em licença de Belinda, mas não desabilitará (ou seja, delete) a licença em si. A licença ainda será válida e ele ainda será atribuído ao Belinda Newman. Ela só não poderão usar essa licença para acessar quaisquer serviços do Office 365.
  
E isso é importante: se você deseja remover uma licença de um usuário deve realmente *Remover* a licença. Desabilitar todos os serviços impedirá que o usuário faça logon no Office 365, mas ele não libera a sua licença. Se você deseja retomar uma licença atualmente atribuído a um usuário que você precisa executar um comando semelhante a este, um comando que usa o parâmetro _RemoveLicenses_ para remover efetivamente a licença atribuída anteriormente a Belinda:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

Execute esse comando e Belinda Newman será não é mais licenciado para usar o Office 365.
  
> [!NOTE]
> Como você pode ver, quando você usa o parâmetro _RemoveLicenses_ que é preciso especificar o nome da licença a ser removido. Se não tiver certeza de qual plano de licenciamento foi usado para atribuir uma licença para o usuário, basta executar um comando semelhante a esta:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
Para verificar se a licença foi realmente removida, use Get-MsoIUser para verificar a conta de usuário em questão:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

Se tudo correu, propriedade **isLicensed** de Belinda agora será definida `False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

Outra maneira para liberar uma licença é, excluindo a conta de usuário. Para obter mais informações, consulte [Excluir e restaurar as contas de usuário com o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
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

||
|:-----|
|![O ícone pequeno do LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Começando a usar o Office 365?**         Descubra cursos em vídeo gratuitos para [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), oferecidos pelo LinkedIn Learning. |
   

