---
title: Desabilitar o acesso aos serviços com o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/11/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Explica como usar o Office 365 PowerShell para desabilitar o acesso aos serviços do Office 365 para usuários em sua organização.
ms.openlocfilehash: 66f6c04c1488f14d5752974a5475e7ef11279406
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897414"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Desabilitar o acesso aos serviços com o PowerShell do Office 365

**Resumo:** Explica como usar o Office 365 PowerShell para desabilitar o acesso aos serviços do Office 365 para usuários em sua organização.
  
Quando uma conta do Office 365 é atribuída a uma licença de um plano de licenciamento, serviços do Office 365 são disponibilizados para o usuário dessa licença. No entanto, você pode controlar os serviços do Office 365 que o usuário pode acessar. Por exemplo, mesmo que a licença permite acesso ao serviço do SharePoint Online, você pode desabilitar o acesso a ele. Você pode usar o Office 365 PowerShell para desabilitar o acesso a qualquer número de serviços para um plano de licenciamento específico para:

- Uma conta individual
    
- Um grupo de contas.
    
- Todas as contas em sua organização.
    
## <a name="before-you-begin"></a>Antes de começar
<a name="RTT"> </a>

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Você pode usar o cmdlet **Get-MsolAccountSku** para exibir seus planos de licenciamento disponíveis e que estão disponíveis nesses planos de serviços do Office 365. Para obter mais informações, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Para ver o antes e depois os resultados dos procedimentos neste tópico, consulte [Exibir detalhes de licença e serviço de conta com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Um script do PowerShell está disponível que automatiza os procedimentos descritos neste tópico. Especificamente, o script permite que você exibir e desabilite os serviços em sua organização do Office 365, incluindo Sway. Para obter mais informações, consulte [Desabilitar o acesso aos Sway com o Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_ , somente as contas de 500 usuário primeira são retornadas.
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Desabilitar serviços específicos do Office 365 para usuários específicos para um plano de licenciamento específico
  
Para desabilitar um conjunto específico de serviços do Office 365 para usuários de um plano de licenciamento específico, execute as seguintes etapas:
  
1. Identificar os serviços indesejáveis no plano de licenciamento usando a seguinte sintaxe:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  O exemplo a seguir cria um objeto de **LicenseOptions** que desabilita os Serviços Online do Office e SharePoint Online no plano de licenciamento denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Use o objeto **LicenseOptions** da Etapa 1 em um ou mais usuários.
    
  - Para criar uma nova conta que tem serviços desabilitados, use a seguinte sintaxe:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  O exemplo a seguir cria uma nova conta para Allie Bellew que atribui a licença e desabilita os serviços descritos na etapa 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  Para obter mais informações sobre a criação de contas de usuário no Office 365 PowerShell, consulte [criar contas de usuário com o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Para desabilitar os serviços de um usuário licenciado existente, use a seguinte sintaxe:
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  Este exemplo desabilita os serviços do usuário BrendaF@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Para desabilitar os serviços descritos na etapa 1 para todos os usuários licenciados existentes, especifique o nome do seu plano do Office 365 da exibição do cmdlet **Get-MsolAccountSku** (por exemplo, **litwareinc: enterprisepack**) e, em seguida, execute os seguintes comandos:
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - Para desabilitar os serviços para um grupo de usuários existentes, use um dos seguintes métodos para identificar os usuários:
    
  - **Filtrar as contas com base em um atributo existente da conta** Para fazer isso, use a seguinte sintaxe:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  O exemplo a seguir desabilita os serviços para os usuários no departamento de vendas nos Estados Unidos.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Usar uma lista de contas específicas** Para fazer isso, execute as seguintes etapas:
    
1. Crie um arquivo de texto que contenha uma conta em cada linha da seguinte forma:
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  Neste exemplo, o arquivo de texto é c:\\Meus documentos\\Accounts.txt.
    
2. Execute o seguinte comando:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Se desejar desabilitar o acesso aos serviços para vários planos de licenciamento, repita as instruções acima para cada plano de licenciamento, garantindo que:

- As contas de usuário atribuiu o plano de licenciamento.
- Para desabilitar os serviços estão disponíveis no plano de licenciamento.

Para desabilitar os serviços do Office 365 para usuários enquanto eles atribuídas a um plano de licenciamento, consulte [Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário](disable-access-to-services-while-assigning-user-licenses.md).


## <a name="new-to-office-365"></a>Começando a usar o Office 365?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Confira também
<a name="SeeAlso"> </a>

Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:
  
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Excluir e restaurar contas de usuários usando o Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear contas de usuários com o Office 365 PowerShell](block-user-accounts-with-office-365-powershell.md)
    
- [Atribuir licenças a contas de usuários usando o PowerShell do Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Criar contas de usuários usando o Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)
    
Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [New-MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

