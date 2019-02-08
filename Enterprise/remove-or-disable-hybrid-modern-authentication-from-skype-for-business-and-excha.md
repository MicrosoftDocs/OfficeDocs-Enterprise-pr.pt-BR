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
ms.openlocfilehash: 802add6295edffe3ec80e70e9bd70663479ec61a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25359023"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange

Se você tiver habilitado híbrida moderno autenticação (HMA) descobriu que é inadequado para seu ambiente atual, você pode desabilitar HMA. Este artigo explica como.
  
## <a name="who-is-this-article-for"></a>Quem é este artigo para?

Se você tiver habilitado moderno autenticação no Skype para Business Online ou no local, e/ou Exchange Online ou local e encontrado que você precisa desabilitar HMA, essas etapas são para você.

> [!IMPORTANT]
> Consulte o artigo "[Skype para topologias de negócios compatíveis com autenticação moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)" Se você estiver em Skype para Business Online ou local, tem um HMA topologia mista e precisar examinar topologias com suporte, antes de começar.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Como desabilitar a autenticação de moderno híbrida (Exchange)

1. **Exchange local**: Abra o Shell de gerenciamento do Exchange e execute os seguintes comandos: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [conectar-se ao Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) com o PowerShell remoto. Execute o seguinte comando para ativar o sinalizador *OAuth2ClientProfileEnabled* como 'falso':

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Como desabilitar a autenticação de moderno híbrida (Skype para negócios)

1. **Skype para negócios local**: execute os seguintes comandos no Skype do Shell de gerenciamento de negócios:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype para negócios on-line**: [conectar-se ao Skype para negócios Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) com o PowerShell remoto. Execute o seguinte comando para desabilitar a autenticação moderno:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Vínculo inverso para a visão geral de autenticação moderno](hybrid-modern-auth-overview.md) . 
  

