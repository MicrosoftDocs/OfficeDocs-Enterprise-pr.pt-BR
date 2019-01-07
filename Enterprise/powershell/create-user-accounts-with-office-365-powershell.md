---
title: Criar contas de usuários usando o Office 365 PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Saiba como usar o Office 365 PowerShell para criar contas de usuários no Office 365.
ms.openlocfilehash: 902f44dd4fc42d8f29ce92748cbbf1ce03c6615b
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730306"
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Criar contas de usuários usando o Office 365 PowerShell

**Resumo:** saiba como usar o Office 365 PowerShell para criar contas de usuários no Office 365.
  
Você pode usar o Office 365 PowerShell para criar contas de usuários de forma eficiente, especialmente para várias contas de usuários. Quando você cria contas de usuários no Office 365 PowerShell, determinadas propriedades de conta são sempre obrigatórias. Outras propriedades, embora sejam importantes, não são obrigatórias para a criação de contas. Essas propriedades estão descritas na tabela a seguir:
  
|**Nome da propriedade**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Sim  <br/> |Esse é o nome para exibição usado nos serviços do Office 365. Por exemplo, Carlos Lima.  <br/> |
|**UserPrincipalName** <br/> |Sim  <br/> |Esse é o nome da conta usado para entrar nos serviços do Office 365. Por exemplo, carlosl@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |Não  <br/> ||
|**LastName** <br/> |Não  <br/> ||
|**LicenseAssignment** <br/> |Não  <br/> |Esse é o plano de licenciamento (também conhecido como plano de licença, plano do Office 365 ou SKU) do qual uma licença disponível será atribuída à conta do usuário. A licença determina os serviços do Office 365 disponíveis para a conta. Não é necessário atribuir uma licença a um usuário ao criar a conta, mas a conta requer uma licença para acessar os serviços do Office 365. Você tem 30 dias para licenciar a conta de usuário depois de criá-la. |
|**Password** <br/> |Não  <br/> | Caso não especifique uma senha, nosso sistema atribuirá uma senha aleatória para a conta do usuário e a senha ficará visível nos resultados do comando. Se você especificar uma senha, ela deverá Se você especificar uma senha, ela precisará ter de 8 a 16 caracteres de texto ASCII de qualquer um dos três tipos a seguir: letras minúsculas, letras maiúsculas, números e símbolos. <br/> |
|**UsageLocation** <br/> |Não  <br/> |Esse é um código de país ISO 3166-1 alpha 2 válido. Por exemplo, FR para França e BR para Brasil. É importante fornecer esse valor, pois alguns serviços do Office 365 não estão disponíveis em certos países/regiões. Portanto, só será possível atribuir uma licença a uma conta de usuário após configurar esse valor na conta. Confira mais informações no artigo [Sobre restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Depois de se conectar, use a seguinte sintaxe para criar uma conta individual:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

Neste exemplo, criamos uma conta para o usuário chamado Carlos Lima do Brasil:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>Criar uma conta de usuário individual

Para criar uma conta individual, use a seguinte sintaxe:
  
```
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

Para listar os nomes do plano de licenciamento disponível, use este comando:

````
Get-MsolAccountSku
````

Nesse exemplo, criamos uma conta para o usuário chamado Carlos Lima do Brasil e atribuímos uma licença do plano de licenciamento `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>Criar várias contas de usuários

1. Crie um arquivo CSV (arquivo de valores separados por vírgula) que inclua as informações necessárias da conta do usuário. Por exemplo:
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>Os nomes de coluna e a respectiva ordem na primeira linha do arquivo CSV são arbitrários, mas você pode verificar se os dados no restante do arquivo correspondem à ordem dos nomes e usar esses nomes para os valores de parâmetro, no comando do Office 365 PowerShell.
    
2. Use a sintaxe a seguir:
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

Nesse exemplo, criamos as contas de usuários do arquivo C:\Meus Documentos\NewAccounts.csv e registramos os resultados no arquivo C:\Meus Documentos\NewAccountResults.csv
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Examine o arquivo de saída para conferir os resultados. Não especificamos senhas, de modo que as senhas aleatórias que o Office 365 gerou ficam visíveis no arquivo de saída.
    
## <a name="see-also"></a>Confira também

[Gerenciar licenças e contas de usuário usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
