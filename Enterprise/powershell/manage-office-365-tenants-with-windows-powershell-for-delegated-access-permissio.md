---
title: Gerenciar locatários do Microsoft 365 com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Resumo: Use o Windows PowerShell para Microsoft 365 para gerenciar o locações do cliente.'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998227"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Gerenciar locatários do Microsoft 365 com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)

O Windows PowerShell permite que os parceiros de distribuição e provedor de soluções em nuvem (CSP) administrem e reportem facilmente as configurações de locação do cliente que não estão disponíveis no centro de administração do Microsoft 365. Observe que as permissões "Administrar em Nome de" (AOBO) são necessárias para a conta de administrador do parceiro para se conectar às locações dos clientes.
  
Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles agrupam assinaturas do Microsoft 365 em suas ofertas de serviço para seus clientes. Ao vender uma assinatura do Microsoft 365, elas recebem automaticamente as permissões de administração em nome de (AOBO) para o cliente locações, para que possam administrar e relatar o locações do cliente.
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
Você também precisa ter as credenciais de administrador de locatários do parceiro.
  
## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

### <a name="list-all-tenant-ids"></a>Listar todas as IDs de Locatários

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
Para listar todas as IDs de Locatários do cliente às quais você tem acesso, execute este comando.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

Uma lista de todos os locatários do cliente será exibida pela **TenantId**.

>[!Note]
>O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome. Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Obter uma ID de Locatário usando o nome de domínio

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Listar todos os domínios de um locatário

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Se você registrou domínios adicionais, serão retornados todos os domínios associados à **TenantId** do cliente.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Obter um mapeamento de todos os locatários e domínios registrados

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Obter todos os usuários de um locatário

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Obter todos os detalhes sobre um usuário

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Adicionar usuários, definir opções e atribuir licenças

A criação, configuração e licenciamento em massa de usuários do Microsoft 365 é particularmente eficiente usando o Windows PowerShell para Office 365. Nesse processo de duas etapas, primeiro crie entradas para todos os usuários que deseja adicionar em um arquivo (CSV) de valor separado por vírgula e, em seguida, importe esse arquivo usando o Windows PowerShell para o Office 365. 
  
#### <a name="create-a-csv-file"></a>Criar um arquivo CSV

Crie um arquivo CSV usando este formato:
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
em que:
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Importar o arquivo CSV e criar os usuários

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Confira também

#### 

[Ajuda para parceiros](https://go.microsoft.com/fwlink/p/?LinkId=533477)

