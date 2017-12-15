---
title: "Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "Saiba como atribuir licenças às contas de usuário e desativar os planos de serviço específico ao mesmo tempo usando o PowerShell do Office 365."
ms.openlocfilehash: 907314e13b353e5d5ddbcd8fe467db568473d0b3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>Desabilitar o acesso aos serviços durante a atribuição de licenças de usuário

**Resumo:**  Saiba como atribuir licenças às contas de usuário e desativar os planos de serviço específico ao mesmo tempo usando o PowerShell do Office 365.
  
Assinaturas do Office 365 vêm com planos de serviço para serviços individuais. Administradores do Office 365 geralmente precisam desativar os planos de determinados ao atribuir licenças aos usuários. Com as instruções deste artigo, você pode atribuir uma licença do Office 365 ao desativar os planos de serviço específico usando o PowerShell para uma conta de usuário individual ou várias contas de usuário.
  
> [!NOTE]
> Este artigo se baseia no trabalho de Siddhartha Parmar, um engenheiro de escalonamento de suporte da Microsoft. 
  
## <a name="before-you-begin"></a>Antes de começar

Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>Coletar informações sobre assinaturas e planos de serviço

Execute este comando para ver suas inscrições atuais:
  
```
Get-MsolAccountSku
```

Na exibição do `Get-MsolAccountSku` comando:
  
- **AccountSkuId** é uma assinatura para sua organização no \<OrganizationName >:\<assinatura > formato. O \<OrganizationName > é o valor que você forneceu ao registrado no Office 365 e é exclusivo para a sua organização. O \<assinatura > valor é para uma inscrição específica. Por exemplo, para litwareinc: enterprisepack, o nome da organização é litwareinc e o nome da inscrição é ENTERPRISEPACK (Office 365 Enterprise E3).
    
- **ActiveUnits** é o número de licenças que você comprou para a assinatura.
    
- **WarningUnits** é o número de licenças em uma assinatura que você ainda não renovado e que irá expirar após o período de carência de 30 dias.
    
- **ConsumedUnits** é o número de licenças que você atribuiu aos usuários para a assinatura.
    
Observe o AccountSkuId para sua assinatura do Office 365 que contém os usuários que você deseja da licença. Além disso, certifique-se de que não há licenças suficientes para atribuir (subtrair **ConsumedUnits** da **ActiveUnits** ).
  
Em seguida, execute este comando para ver os detalhes sobre os planos de serviço do Office 365 estão disponíveis em todas as suas assinaturas:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Na janela deste comando, determine quais planos de serviço que você gostaria de desabilitar ao atribuir licenças aos usuários.
  
Aqui está uma lista parcial de planos de serviço e seus serviços do Office 365 correspondentes.
  
|**Plano de serviço**|**Descrição**|
|:-----|:-----|
|SWAY  <br/> |Sway  <br/> |
|INTUNE_O365  <br/> |Gerenciamento de Dispositivos Móveis para o Office 365  <br/> |
|YAMMER_ENTERPRISE  <br/> |Yammer  <br/> |
|RMS_S_ENTERPRISE  <br/> |Azure Rights Management (RMS)  <br/> |
|OFFICESUBSCRIPTION  <br/> |Office Professional Plus  <br/> |
|MCOSTANDARD  <br/> |Skype for Business online  <br/> |
|SHAREPOINTWAC  <br/> |Office Online  <br/> |
|SHAREPOINTENTERPRISE  <br/> |SharePoint Online  <br/> |
|EXCHANGE_S_ENTERPRISE  <br/> |Plano 2 do Exchange Online  <br/> |
   
Agora que você tiver o AccountSkuId e os planos de serviço para desabilitar, você pode atribuir licenças para um usuário individual ou para vários usuários.
  
## <a name="for-a-single-user"></a>Para um único usuário

Para um único usuário, preencha o nome principal de usuário de conta de usuário, o AccountSkuId e a lista de planos de serviço desativar e remover o texto explicativo e o \< e > caracteres. Em seguida, execute os comandos resultantes no prompt de comando do PowerShell.
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

Aqui está um bloco de comando de exemplo para a conta denominada belindan@contoso.com, para a licença de contoso:ENTERPRISEPACK, e os planos de serviço para desabilitar são RMS_S_ENTERPRISE, SWAY, INTUNE_O365 e YAMMER_ENTERPRISE:
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a>Para vários usuários

Para realizar essa tarefa de administração para vários usuários, crie um arquivo de texto delimitado por vírgula (CSV) que contém os campos UserPrincipalName e UsageLocation. Aqui está um exemplo:
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Em seguida, preencha o local dos arquivos CSV de saída e a entrada, a conta de ID de SKU e a lista de planos de serviço para desabilitar e, em seguida, execute os comandos de resultantes no prompt de comando do PowerShell.
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Este bloco de comando do PowerShell:
  
- Exibe o nome principal de usuário de cada usuário.
    
- Atribui personalizados licenças para cada usuário.
    
- Cria um arquivo CSV com todos os usuários que foram processados e mostra seus status de licença.
    
## <a name="see-also"></a>See also

#### 

[Desabilitar o acesso aos serviços com o PowerShell do Office 365](disable-access-to-services-with-office-365-powershell.md)
  
[Desabilitar o acesso aos Sway com o Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)
  
[Gerenciar contas de usuário e licenças usando o PowerShell do Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)

