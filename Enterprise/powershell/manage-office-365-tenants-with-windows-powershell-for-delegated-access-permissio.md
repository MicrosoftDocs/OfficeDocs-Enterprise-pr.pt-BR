---
title: Gerenciar locatários do Office 365 com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Resumo: Use o Windows PowerShell para o Office 365 para gerenciar as locações do cliente.'
ms.openlocfilehash: a45fb7b888d7e591f6765150525f0b50c72ddc5c
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257586"
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Gerenciar locatários do Office 365 com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)

 **Resumo:** use o Windows PowerShell para o Office 365 para gerenciar os locatários do cliente.
  
O Windows PowerShell permite que os parceiros de distribuição e provedor de soluções em nuvem (CSP) administrem e reportem facilmente as configurações de locação do cliente que não estão disponíveis no centro de administração do Microsoft 365. Observe que as permissões de administrar em nome de (AOBO) são necessárias para que a conta de administrador do parceiro se conecte ao seu cliente locações.
  
Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas. Eles reúnem assinaturas do Office 365 em suas ofertas de serviço aos seus clientes. Quando eles vendem uma assinatura do Office 365, recebem automaticamente permissões de Administrar Em Nome de (AOBO) para as locações de cliente para que possam administrar e relatar todas as suas locações de cliente.
## <a name="what-do-you-need-to-know-before-you-begin"></a>O que você precisa saber antes de começar?

Os procedimentos neste tópico exigem que você se conecte ao Windows PowerShell para Office 365. Para obter instruções, veja [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
  
Você também precisa ter as credenciais de administrador de locatários do parceiro.
  
## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

### <a name="list-all-tenant-ids"></a>Listar todas as IDs de Locatários

> [!NOTE]
> Caso tenha mais de 500 locatários, analise a sintaxe do cmdlet com o  _-All_ ou o _-MaxResultsParameter_. Isso se aplica aos outros cmdlets que podem proporcionar uma grande saída, como o **Get-MsolUser**.
  
Para listar todas as IDs de Locatários do cliente às quais você tem acesso, execute este comando.
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

Uma lista de todos os locatários do cliente será exibida pela **TenantId**.

>[!Note]
>O PowerShell Core não é compatível com o módulo Microsoft Azure Active Directory para o módulo e cmdlets do Windows PowerShell com o **MSol** em seu nome. Para continuar usando esses cmdlets, você deve executá-los do Windows PowerShell.
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Obter uma ID de Locatário usando o nome de domínio

Para obter a **TenantId** de um locatário específico do cliente por nome de domínio, execute este comando. Substitua _<domainname.onmicrosoft.com>_ pelo nome de domínio real do locatário do cliente desejado.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Listar todos os domínios de um locatário

Para obter todos os domínios de qualquer locatário de um cliente, execute este comando. Substitua o  _<customer TenantId value>_ pelo valor real.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

Se você registrou domínios adicionais, serão retornados todos os domínios associados à **TenantId** do cliente.
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Obter um mapeamento de todos os locatários e domínios registrados

Os comandos anteriores do Windows PowerShell para o Office 365 mostravam como recuperar IDs de Locatário ou domínios, mas não ambos ao mesmo tempo e sem nenhum mapeamento claro entre todos eles. Esse comando gera uma lista de todas as IDs de Locatários do cliente e os respectivos domínios.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Obter todos os usuários de um locatário

Os comandos **UserPrincipalName**, o **DisplayName** e o status **isLicensed** serão exibidos para todos os usuários de um determinado locatário. Substitua o _<customer TenantId value>_ pelo valor real.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Obter todos os detalhes sobre um usuário

Caso pretenda conferir todas as propriedades de um usuário específico, execute este comando. Substitua _<customer TenantId value>_ e _<user principal name value>_ pelos valores reais.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Adicionar usuários, definir opções e atribuir licenças

A criação, configuração e licenciamento em massa de usuários do Office 365 é particularmente eficiente ao usar o Windows PowerShell para o Office 365. Nesse processo de duas etapas, primeiro crie entradas para todos os usuários que deseja adicionar em um arquivo (CSV) de valor separado por vírgula e, em seguida, importe esse arquivo usando o Windows PowerShell para o Office 365. 
  
#### <a name="create-a-csv-file"></a>Criar um arquivo CSV

Crie um arquivo CSV usando este formato:
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
em que:
  
- **UsageLocation**: O valor para isso é o código de país/região ISO de duas letras do usuário. Os códigos de país/região podem ser visualizados na[Plataforma de Navegação Online ISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Por exemplo, o código para os Estados Unidos é US e o código para o Brasil é BR. 
    
- **LicenseAssignment**: O valor para isso tem o seguinte formato: `syndication-account:<PROVISIONING_ID>`. Por exemplo, se você está atribuindo licenças para usuários do O365_Business_Premium, o valor de **LicenseAssignment** tem a seguinte aparência: **syndication-account:O365_Business_Premium**. Você vai encontrar as PROVISIONING_IDs no portal do parceiro de distribuição ao qual tem acesso como um parceiro de agregação ou um CSP.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>Importar o arquivo CSV e criar os usuários

Depois de criar o arquivo CSV, execute este comando para criar contas de usuários com senhas que não perdem a validade. Essas senhas atribuem a licença especificada e os usuários devem alterá-la no primeiro logon. Não deixe de substituir o nome correto do arquivo CSV.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Confira também

#### 

[Ajuda para parceiros](https://go.microsoft.com/fwlink/p/?LinkId=533477)

