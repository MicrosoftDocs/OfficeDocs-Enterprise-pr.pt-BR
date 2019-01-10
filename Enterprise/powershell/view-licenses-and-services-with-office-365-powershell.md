---
title: Exibir licenças e serviços com o PowerShell do Office 365
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
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explica como usar o Office 365 PowerShell para visualizar informações sobre os planos de licenciamento, serviços e licenças disponíveis na sua organização do Office 365.
ms.openlocfilehash: 8efc123e2820560b4bd8547f4c99bccae242956f
ms.sourcegitcommit: 96313c3c812bae47819f603af995839f4da034c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "27786147"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Exibir licenças e serviços com o PowerShell do Office 365

**Resumo:** explica como usar o Office 365 PowerShell para visualizar informações sobre os planos de licenciamento, serviços e licenças disponíveis na sua organização do Office 365.
  
Todas as assinaturas do Office 365 consistem nos seguintes elementos:

- **Planos de licenciamento** Esses são também conhecidos como planos de licença ou planos do Office 365. Planos de licenciamento definem os serviços do Office 365 que estão disponíveis para usuários. Sua assinatura do Office 365 pode conter vários planos de licenciamento. Um plano de licenciamento de exemplo seria o Office 365 Enterprise E3.
    
- **Serviços** Essas são também conhecidos como planos de serviço. Serviços são os produtos do Office 365, recursos e capacidades que estão disponíveis em cada plano de licenciamento, por exemplo, o Exchange Online e Office Professional Plus. Os usuários podem ter várias licenças atribuídas a eles de planos de licenciamento diferentes que concedem acesso aos serviços diferentes.
    
- **Licenças** Cada plano de licenciamento contém o número de licenças que você adquiriu. Você atribui licenças a usuários para que eles possam usar os serviços do Office 365 definidos pelo plano de licenciamento. Cada conta de usuário requer ao menos uma licença de um plano de licenciamento para poder fazer logon no Office 365 e usar os serviços.
    
Você pode usar o Office 365 PowerShell para visualizar detalhes sobre os planos de licenciamento, licenças e serviços disponíveis na sua organização do Office 365. Confira mais informações sobre produtos, recursos e serviços disponíveis em diferentes assinaturas do Office 365 em [Opções de Planos do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use o PowerShell do Azure Active Directory para o módulo do gráfico

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Para exibir informações de resumo sobre seus planos de licenciamento atuais e as licenças disponíveis para cada plano, execute o seguinte comando:
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Os resultados contêm as seguintes informações:
  
- **SkuPartNumber:** Mostra os planos de licenciamento disponíveis para sua organização. Por exemplo, `ENTERPRISEPACK` é o nome do sistema para Office 365 Enterprise E3.
    
- **Habilitado:** Número de licenças que você comprou de um plano de licenciamento específico.
    
- **ConsumedUnits:** número de licenças que você atribuiu aos usuários de um plano de licenciamento específico.
    
Para exibir detalhes sobre os serviços do Office 365 estão disponíveis em todos os seus planos de licença, primeiro exiba uma lista de seus planos de licença.

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

Em seguida, armazene as informações de planos de licença em uma variável.

````
$licenses = Get-AzureADSubscribedSku
````

Em seguida, exibe os serviços em um plano de licença específico.

````
$licenses[<index>].ServicePlans
````

\<índice > é um inteiro que especifica o número da linha do plano de licença da exibição do `Get-AzureADSubscribedSku | Select SkuPartNumber` command, menos 1.

Por exemplo, se a exibição do `Get-AzureADSubscribedSku | Select SkuPartNumber` comando é isso:

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

Em seguida, o comando para exibir os serviços para o plano de licença ENTERPRISEPREMIUM é o seguinte:

````
$licenses[2].ServicePlans
````

ENTERPRISEPREMIUM é a terceira linha. Portanto, o valor de índice é (3 - 1), ou 2.

Para obter uma lista completa de planos de licença (também conhecido como nomes de produto), seus planos de serviço incluído e seus nomes amigáveis correspondentes, consulte [nomes de produto e os identificadores de plano de serviço para licenciamento](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Um script do PowerShell está disponível que automatiza os procedimentos descritos neste tópico. Especificamente, o script permite que você exibir e desabilite os serviços em sua organização do Office 365, incluindo Sway. Para obter mais informações, consulte [Desabilitar o acesso aos Sway com o Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Para exibir informações de resumo sobre seus planos de licenciamento atuais e as licenças disponíveis para cada plano, execute o seguinte comando:
  
```
Get-MsolAccountSku
```

Os resultados contêm as seguintes informações:
  
- **AccountSkuId** Mostre os planos de licenciamento disponíveis para a sua organização usando a sintaxe `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ é o valor que você forneceu ao se inscrever no Office 365 e é exclusivo da sua organização. O valor do _<LicensingPlan>_ é o mesmo para todos. Por exemplo, no valor `litwareinc:ENTERPRISEPACK`, o nome da empresa é  `litwareinc` e o nome do plano de licenciamento `ENTERPRISEPACK`, que é o nome do sistema para o Office 365 Enterprise E3.
    
- **ActiveUnits:** Número de licenças que você comprou de um plano de licenciamento específico.
    
- **WarningUnits:** número de licenças em um plano de licenciamento que você não renovou e que expirará após um período de carência de 30 dias.
    
- **ConsumedUnits:** número de licenças que você atribuiu aos usuários de um plano de licenciamento específico.
    
Para exibir detalhes sobre os serviços do Office 365 disponíveis em todos os planos de licenciamento, execute o seguinte comando:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

A tabela a seguir mostra os planos de serviço do Office 365 e seus nomes amigáveis para os serviços mais comuns. Sua lista de planos de serviço pode ser diferente. 
  
|**Plano de serviço**|**Descrição**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plano 2 do Exchange Online  <br/> |
   
Para obter uma lista completa de planos de licença (também conhecido como nomes de produto), seus planos de serviço incluído e seus nomes amigáveis correspondentes, consulte [nomes de produto e os identificadores de plano de serviço para licenciamento](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Para exibir detalhes sobre os serviços do Office 365 disponíveis em um plano de licenciamento específico, use a sintaxe a seguir.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Este exemplo mostra os serviços do Office 365 que estão disponíveis no plano de licenciamento de litwareinc: enterprisepack (Office 365 Enterprise E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>Começando a usar o Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Confira também


[Gerenciar licenças e contas de usuário usando o Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Gerenciar o Office 365 com o Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introdução ao Office 365 PowerShell](getting-started-with-office-365-powershell.md)
