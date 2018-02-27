---
title: "Criar contas de usuários usando o Office 365 PowerShell"
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
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "Saiba como usar o Office 365 PowerShell para criar contas de usuários no Office 365."
ms.openlocfilehash: e5fed572d0b835a42071e77b4aeaf8714f2178bd
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Criar contas de usuários usando o Office 365 PowerShell

**Resumo:** saiba como usar o Office 365 PowerShell para criar contas de usuários no Office 365.
  
Você pode usar o Office 365 PowerShell para criar contas de usuários de forma eficiente, especialmente para várias contas de usuários. Quando você cria contas de usuários no Office 365 PowerShell, determinadas propriedades de conta são sempre obrigatórias. Outras propriedades, embora sejam importantes, não são obrigatórias para a criação de contas. Essas propriedades estão descritas na tabela a seguir:
  
****

|**Nome da propriedade**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Sim  <br/> |Esse é o nome para exibição usado nos serviços do Office 365. Por exemplo, Carlos Lima.  <br/> |
|**UserPrincipalName** <br/> |Sim  <br/> |Esse é o nome da conta usado para entrar nos serviços do Office 365. Por exemplo, carlosl@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |Não  <br/> ||
|**LastName** <br/> |Não  <br/> ||
|**LicenseAssignment** <br/> |Não  <br/> |Esse é o plano de licenciamento (também conhecido como plano de licença, plano do Office 365 ou SKU) do qual uma licença disponível será atribuída à conta do usuário. A licença determina os serviços do Office 365 que estão disponíveis para a conta. Não é necessário atribuir uma licença a um usuário ao criar a conta, mas a conta requer uma licença para acessar os serviços do Office 365. Você tem 30 dias para licenciar a conta de usuário depois de criá-la.<br/> Use o cmdlet **Get-MsolAccountSku** para exibir os planos de licenciamento ( **AccountSkuId** ) e as licenças disponíveis na organização. Para saber mais, confira o artigo [Exibir licenças e serviços com o PowerShell do Office 365](view-licenses-and-services-with-office-365-powershell.md).  <br/> |
|**Password** <br/> |Não  <br/> | Caso não especifique uma senha, nosso sistema atribuirá uma senha aleatória para a conta do usuário e a senha ficará visível nos resultados do comando. Se você especificar uma senha, ela deverá atender aos seguintes requisitos de complexidade: <br/>  Ter de 8 a 16 caracteres de texto ASCII. <br/>  Incluir caracteres dos três tipos a seguir: letras maiúsculas, letras minúsculas, números e símbolos. <br/> |
|**UsageLocation** <br/> |Não  <br/> |Esse é um código de país ISO 3166-1 alpha 2 válido. Por exemplo, FR para França e BR para Brasil. É importante fornecer esse valor, pois alguns serviços do Office 365 não estão disponíveis em certos países/regiões. Portanto, apenas será possível atribuir uma licença a uma conta de usuário depois de configurar esse valor na conta. Para saber mais, confira o artigo [Sobre restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   
## <a name="before-you-begin"></a>Antes de começar

Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>Use o Office 365 PowerShell para criar contas de usuários individuais

Para criar uma conta individual, use a seguinte sintaxe:
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

Nesse exemplo, criamos uma conta para o usuário chamado Carlos Lima do Brasil e atribuímos uma licença do plano de licenciamento  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>Use o Office 365 PowerShell para criar várias contas de usuários

1. Crie um arquivo CSV (arquivo de valores separados por vírgula ) que inclua as informações necessárias da conta do usuário. Por exemplo:
    
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

3. Examine o arquivo de saída para conferir os resultados. Não especificamos senhas, de modo que as senhas aleatórias geradas ficam visíveis no arquivo de saída.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>Use o módulo PowerShell do Azure Active Directory V2 para criar contas de usuários individuais.

Para usar o cmdlet **New-AzureADUser** no módulo do PowerShell Azure Active Directory V2, conecte-se primeiro à sua assinatura. Para conhecer as instruções, confira [Conectar-se com o módulo do PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Depois de se conectar, use a seguinte sintaxe para criar uma conta de individual:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

Neste exemplo, criamos uma conta para o usuário chamado Carlos Lima do Brasil:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>Confira também

Confira estes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear contas de usuários com o Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Atribuir licenças a contas de usuários usando o PowerShell do Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Remover licenças de contas de usuários com o Office 365 PowerShell](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Export-Csv](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

