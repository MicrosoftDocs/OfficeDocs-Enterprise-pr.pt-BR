---
title: Criar um grupo do Microsoft 365 com uma PDL específica
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: Saiba como criar um grupo do Microsoft 365 com um local de dados preferencial especificado em um ambiente multigeográfico.
ms.openlocfilehash: bcababe39035550be445f2eee4d8121a2983132f
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433852"
---
# <a name="create-a-microsoft-365-group-with-a-specific-pdl"></a>Criar um grupo do Microsoft 365 com uma PDL específica

Quando os usuários em um ambiente multigeográfico criam um grupo do Microsoft 365, o local de dados preferido do grupo é automaticamente definido para o do usuário. Os administradores globais, do SharePoint e do Exchange podem criar grupos em qualquer região que selecionarem. 

Se precisar criar um grupo com uma PDL específica, você pode fazer isso através do centro do administração do SharePoint ou através do cmdlet do novo PowerShell do Microsoft Exchange Online UnifiedGroup. Quando você fizer isso, a caixa de correio de grupo e o site do SharePoint associados ao grupo serão provisionados na PDL especificada.

Para criar um grupo do Microsoft 365 com a PDL que você especificar, vá para o centro de administração do SharePoint no local geográfico onde você deseja criar o site do grupo.

Por exemplo:

Se você quer criar um site de grupo no seu local na Austrália, pode ir para https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Selecione **+ Criar**.
2. Siga o processo para criar um site de grupo.

O seu site de grupo será provisionado na localização geográfica correspondente ao centro de administração do SharePoint no qual você iniciou a solicitação de criação de site. 

Usando o PowerShell do Exchange 

Conecte-se ao PowerShell do Exchange Online e passe o parâmetro *-MailBoxRegion* com o código de localização geográfica.

Por exemplo: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![O Cmdlet do PowerShell de captura de tela do novo UnifiedGroup com sintaxe](media/multi-geo-new-group-with-pdl-powershell.png)

Observe que o provisionamento de sites de grupo do SharePoint é sob demanda. O site será configurado a primeira vez que um membro ou proprietário do grupo tentar acessá-lo.

## <a name="geo-location-codes"></a>Códigos de localização geográfica

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>Confira também

[Conectar-se ao PowerShell do Exchange Online ](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
