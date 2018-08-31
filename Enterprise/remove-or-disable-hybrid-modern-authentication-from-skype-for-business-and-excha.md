---
title: Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: Se você tiver habilitado híbrida moderno autenticação (HMA) descobriu que é inadequado para seu ambiente atual, você pode desabilitar HMA. Este artigo explica como.
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539379"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange

Se você tiver habilitado híbrida moderno autenticação (HMA) descobriu que é inadequado para seu ambiente atual, você pode desabilitar HMA. Este artigo explica como.
  
## <a name="who-is-this-article-for"></a>Quem é este artigo para?

Se você tiver habilitado moderno autenticação no Skype para Business Online ou no local, e/ou Exchange Online ou local e encontrado que você precisa desabilitar HMA, essas etapas são para você.
  
 **Importante** Consulte o artigo " [Skype para topologias de negócios compatíveis com autenticação moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)" Se você estiver em Skype para Business Online ou local, tem um HMA topologia mista e precisar examinar topologias com suporte, antes de começar.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Como desabilitar a autenticação de moderno híbrida (Exchange)

1. **Exchange local**: Abra o Shell de gerenciamento do Exchange e execute o seguinte comando. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled $false
    
2. Set-AuthServer-Identity evoSTS - IsDefaultAuthorizationEndpoint $false
    
2. **Exchange Online**: conectar-se ao Exchange Online com o PowerShell remoto. Execute o seguinte comando para ativar o sinalizador *OAuth2ClientProfileEnabled* como 'falso'. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled: $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Como desabilitar a autenticação de moderno híbrida (Skype para negócios)

1. **Skype para negócios local**: execute os seguintes comandos no Skype do Shell de gerenciamento de negócios.
    
1. Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity ""
    
2. **Skype para negócios on-line**: conectar ao Skype for Business Online com o PowerShell remoto. Execute o seguinte comando para desabilitar a autenticação moderno. 
    
1. Set-CsOAuthConfiguration - ClientAdalAuthOverride não permitido
    
[Vínculo inverso para a visão geral de autenticação moderno](hybrid-modern-auth-overview.md) . 
  

