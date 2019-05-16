---
title: 'Criar um grupo no Office 365 com uma PDL específica '
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba como criar um grupo do Office 365 com um local de dados preferencial especificado em um ambiente multigeógrafico.
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069997"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>Criar um grupo no Office 365 com uma PDL específica 

Quando os usuários em um ambiente multigeógrafico criam um grupo do Office 365, o grupo local de dados preferenciais é definido automaticamente para o usuário. Se precisar criar um grupo com uma PDL específica, você pode fazer isso usando o cmdlet do novo PowerShell do Microsoft Exchange Online UnifiedGroup. Quando você fizer isso, a caixa de correio de grupo e o site do SharePoint associados ao grupo serão provisionados na PDL especificada.

Você precisa ser um administrador global ou administrador do SharePoint Online para corrigir esses erros.

Para criar um grupo do Office 365 com PDL que você especificar, conecte-se ao PowerShell do Exchange Online e passar o parâmetro *- MailBoxRegion* com o código de localização geográfica.

Por exemplo: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![O Cmdlet do PowerShell de captura de tela do novo UnifiedGroup com sintaxe](media/multi-geo-new-group-with-pdl-powershell.png)

Observe que o provisionamento de sites de grupo do SharePoint é sob demanda. O site será configurado a primeira vez que um membro ou proprietário do grupo tentar acessá-lo.

## <a name="geo-location-codes"></a>Códigos de localização geográfica

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>Confira também

[Conectar-se ao PowerShell do Exchange Online ](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)