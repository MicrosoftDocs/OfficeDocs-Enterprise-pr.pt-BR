---
title: "Exibir licenças e serviços com o PowerShell do Office 365"
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
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: "Explica como usar o Office 365 PowerShell para visualizar informações sobre os planos de licenciamento, serviços e licenças disponíveis na sua organização do Office 365."
ms.openlocfilehash: 7564da2093bdc9de45e239be8196a626214871ba
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Exibir licenças e serviços com o PowerShell do Office 365

**Resumo:** explica como usar o Office 365 PowerShell para visualizar informações sobre os planos de licenciamento, serviços e licenças disponíveis na sua organização do Office 365.
  
Todas as assinaturas do Office 365 consistem nos seguintes elementos:
- **Planos de licenciamento** Também são conhecidos comoplanos de licença ou planos do Office 365. Os planos de licenciamento determinam os serviços do Office 365 que estão disponíveis para os usuários. A assinatura do Office 365 pode conter vários planos de licenciamento. Um exemplo de plano seria o Office 365 Enterprise E3.
    
- **Serviços** Eles também são conhecidos comoplanos de serviço. Os serviços são os produtos, recursos e capacidades do Office 365 que estão disponíveis no plano de licenciamento, por exemplo, o Exchange Online e o Office Professional Plus. Os usuários podem receber várias licenças de diferentes planos de licenciamento que garantem o acesso a diferentes serviços.
    
- **Licenças** Cada plano de licenciamento contém o número de licenças que você adquiriu. Você atribui licenças a usuários para que eles possam usar os serviços do Office 365 definidos pelo plano de licenciamento. Cada conta de usuário requer ao menos uma licença de um plano de licenciamento para poder fazer logon no Office 365 e usar os serviços.
    
Você pode usar o Office 365 PowerShell para visualizar detalhes sobre os planos de licenciamento, licenças e serviços disponíveis na sua organização do Office 365. Confira mais informações sobre produtos, recursos e serviços disponíveis em diferentes assinaturas do Office 365 em [Opções de Planos do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).
## <a name="before-you-begin"></a>Antes de começar
<a name="RTT"> </a>

- Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).
    
- Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico. Especificamente, o script permite exibir e desabilitar serviços em sua organização do Office 365, incluindo o Sway. Para saber mais, confira [Desabilitar o acesso ao Sway com o PowerShell do Office 365](disable-access-to-sway-with-office-365-powershell.md).
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>Exibir informações sobre os planos de licenciamento e as licenças disponíveis
<a name="ShortVersion"> </a>

Para exibir informações resumidas sobre seus planos de licenciamento atuais e as licenças disponíveis para cada plano, execute o seguinte comando no Office 365 PowerShell:
  
```
Get-MsolAccountSku
```

Os resultados contêm as seguintes informações:
  
- **AccountSkuId** Mostre os planos de licenciamento disponíveis para a sua organização usando a sintaxe `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ é o valor que você forneceu ao se inscrever no Office 365 e é exclusivo da sua organização. O valor do _<LicensingPlan>_ é o mesmo para todos. Por exemplo, no valor `litwareinc:ENTERPRISEPACK`, o nome da empresa é  `litwareinc` e o nome do plano de licenciamento `ENTERPRISEPACK`, que é o nome do sistema para o Office 365 Enterprise E3.
    
- **ActiveUnits:** número de licenças que você comprou para um plano de licenciamento específico.
    
- **WarningUnits:** número de licenças em um plano de licenciamento que você não renovou e que expirará após um período de carência de 30 dias.
    
- **ConsumedUnits:** número de licenças que você atribuiu aos usuários de um plano de licenciamento específico.
    
Para exibir detalhes sobre os serviços do Office 365 disponíveis em todos os planos de licenciamento, execute o seguinte comando:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

A tabela a seguir mostra os planos de serviço do Office 365 e seus nomes amigáveis para os serviços mais comuns. Sua lista de planos de serviço pode ser diferente. Peça ao [Suporte do Office](https://support.office.com/home/contact) a lista completa de planos de serviço e seus nomes amigáveis.
  
|****Plano de serviço****|****Descrição****|
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
   
Para exibir detalhes sobre os serviços do Office 365 disponíveis em um plano de licenciamento específico, use a sintaxe a seguir.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

Este exemplo mostra os serviços do Office 365 que estão disponíveis no plano de licenciamento litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>Começando a usar o Office 365?
<a name="ShortVersion"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Confira também
<a name="ShortVersion"> </a>

#### 

[Exibir usuários licenciados e não licenciados com o PowerShell do Office 365](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
  
[Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)
#### 

[Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

