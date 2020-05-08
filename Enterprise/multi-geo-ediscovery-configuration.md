---
title: Configurar o Microsoft 365 Multi-Geo eDiscovery
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
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Saiba como configurar o eDiscovery no Microsoft 365 Multi-Geo.
ms.openlocfilehash: a956a38f00590161c04009b472a4a8a9d2e89d2b
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057951"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Configuração do Microsoft 365 Multi-Geo eDiscovery

Por padrão, o gerente ou administrador da Descoberta Eletrônica de um locatário multigeográfico poderá realizar a Descoberta Eletrônica apenas na localização central desse locatário. Para poder realizar a descoberta eletrônica nas localizações no satélite, está disponível, no PowerShell, um novo parâmetro de Filtro de Segurança de Conformidade, chamado "Região".

O administrador global do Microsoft 365 deve atribuir permissões ao eDiscovery Manager para permitir que outras pessoas executem o eDiscovery e atribuam o parâmetro "Região" no seu Filtro de segurança de conformidade aplicável para especificar a região de execução do eDiscovery como localização do satélite; caso contrário, nenhum eDiscovery será executado na localização por satélite.

Quando a função de gerente ou administrador de Descoberta Eletrônica é definida para uma determinada localização satélite, o gerente ou o administrador só poderá realizar ações de pesquisa de Descoberta Eletrônica em sites do SharePoint e do OneDrive naquela localização satélite. Se ele tentar pesquisar sites do SharePoint ou do OneDrive fora da localização satélite especificada, nenhum resultado será apresentado. Além disso, quando o gerente ou administrador de Descoberta Eletrônica de uma localização satélite aciona uma exportação, os dados são exportados para a instância do Azure daquela região. Isso ajuda as organizações a permanecerem em conformidade, não permitindo que o conteúdo seja exportado para além de fronteiras controladas.

> [!NOTE]
> Caso seja necessário que o gerente de Descoberta Eletrônica pesquise diversas localizações satélites no SharePoint, será necessário criar outra conta de usuário para ele, a qual especifique a localização satélite alternativa onde se encontram os sites do OneDrive ou do SharePoint.

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

Para configurar o Filtro de Segurança de Conformidade para uma região:

1. [Conecte-se ao Centro de conformidade e segurança do Microsoft 365 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)

2. Use a seguinte sintaxe:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Por exemplo:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Confira o artigo sobre o cmdlet [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/new-compliancesecurityfilter) para ver os sintaxe e parâmetros adicionais.
