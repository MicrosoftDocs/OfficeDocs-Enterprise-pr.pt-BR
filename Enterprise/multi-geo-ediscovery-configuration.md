---
title: Configurar a descoberta eletrônica do Office 365 multigeográfica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Saiba como configurar a descoberta eletrônica no Office 365 multigeográfica.
ms.openlocfilehash: 11d226605ba1f194393405edd5bb535da6ad7343
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933929"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a>Configuração de descoberta eletrônica do Office 365 multigeográfica


Por padrão, o gerente ou administrador de Descoberta Eletrônica de um locatário multigeográfico poderá realizar a Descoberta Eletrônica apenas na localização central desse locatário. Para poder realizar a descoberta eletrônica nas localizações no satélite, está disponível, no PowerShell, um novo parâmetro de Filtro de Segurança de Conformidade, chamado "Região".

O administrador global do Office 365 deve atribuir permissões de gerente de Descoberta Eletrônica para permitir que outras pessoas possam realizá-la e atribuir o parâmetro "Região" no Filtro de Segurança e Conformidade deles, para especificar a região como uma localização no satélite para a realização da Descoberta. Caso contrário, a Descoberta Eletrônica não será realizada para nenhuma localização no satélite.

Quando a função de gerente ou administrador de Descoberta Eletrônica é definida para uma determinada localização satélite, o gerente ou o administrador só poderá realizar ações de pesquisa de Descoberta Eletrônica em sites do SharePoint e do OneDrive naquela localização satélite. Se ele tentar pesquisar sites do SharePoint ou do OneDrive fora da localização satélite especificada, nenhum resultado será apresentado. Além disso, quando o gerente ou administrador de Descoberta Eletrônica de uma localização satélite aciona uma exportação, os dados são exportados para a instância do Azure daquela região. Isso ajuda as organizações a permanecerem em conformidade, não permitindo que o conteúdo seja exportado para além de fronteiras controladas.

> [!NOTE]
> Caso seja necessário que o gerente de Descoberta Eletrônica pesquise diversas localizações satélites no SharePoint, será necessário criar outra conta de usuário para ele, a qual especifique a localização satélite alternativa onde se encontram os sites do OneDrive ou do SharePoint.

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

Para configurar o Filtro de Segurança de Conformidade para uma região:

1.  Abra o Windows PowerShell

2.  Digite  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** TODOS **-FilterName** InsiraONomeParaOQualDesejaAtribuir **-Region** InsiraOParâmetroDeRegiao **-Users** InsiraONomePrincipalDoUsuario

    Por exemplo: **New-ComplianceSecurityFilter -Action** TODOS **-FilterName** NomeDosGerentesDeDescobertaEletronica **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

Confira o artigo sobre o cmdlet [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para ver os parâmetros adicionais e a sintaxe
