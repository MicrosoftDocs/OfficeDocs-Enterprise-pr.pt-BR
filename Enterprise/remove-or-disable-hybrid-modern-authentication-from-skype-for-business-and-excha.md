---
title: Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: Se você habilitou a autenticação moderna híbrida (HMA) apenas para encontrá-la inadequada ao seu ambiente atual, é possível desabilitar a HMA. Este artigo explica como.
ms.openlocfilehash: 011e24c546fede11177e49ce8b36599d7d81d121
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070977"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange

Se você habilitou a autenticação moderna híbrida (HMA) apenas para encontrá-la inadequada ao seu ambiente atual, é possível desabilitar a HMA. Este artigo explica como.
  
## <a name="who-is-this-article-for"></a>Quem é este artigo?

Se você habilitou a autenticação moderna no Skype for Business online ou no local e/ou no Exchange Online ou no local e descobriu que precisa desabilitar a HMA, estas etapas são para você.

> [!IMPORTANT]
> Consulte o artigo "topologias do[Skype for Business com suporte com autenticação moderna](https://technet.microsoft.com/en-us/library/mt803262.aspx)" se você estiver no Skype for Business online ou no local, tenha uma HMA de topologia mista e precise examinar as topologias com suporte antes de começar.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Como desabilitar a autenticação moderna híbrida (Exchange)

1. **Exchange local**: Abra o Shell de gerenciamento do Exchange e execute os seguintes comandos: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Conecte-se ao Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) com o PowerShell remoto. Execute o comando a seguir para transformar o sinalizador *OAuth2ClientProfileEnabled* como ' false ':

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Como desabilitar a autenticação moderna híbrida (Skype for Business)

1. **Skype for Business local**: execute os seguintes comandos no Shell de gerenciamento do Skype for Business:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for Business online**: [conectar-se ao Skype for Business online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) com o PowerShell remoto. Execute o seguinte comando para desabilitar a autenticação moderna:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Link de volta para a visão geral da autenticação moderna](hybrid-modern-auth-overview.md) . 
  

