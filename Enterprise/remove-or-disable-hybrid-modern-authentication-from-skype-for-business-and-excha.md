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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="5a7f6-104">Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange</span><span class="sxs-lookup"><span data-stu-id="5a7f6-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="5a7f6-p102">Se você tiver habilitado híbrida moderno autenticação (HMA) descobriu que é inadequado para seu ambiente atual, você pode desabilitar HMA. Este artigo explica como.</span><span class="sxs-lookup"><span data-stu-id="5a7f6-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="5a7f6-107">Quem é este artigo para?</span><span class="sxs-lookup"><span data-stu-id="5a7f6-107">Who is this article for?</span></span>

<span data-ttu-id="5a7f6-108">Se você tiver habilitado moderno autenticação no Skype para Business Online ou no local, e/ou Exchange Online ou local e encontrado que você precisa desabilitar HMA, essas etapas são para você.</span><span class="sxs-lookup"><span data-stu-id="5a7f6-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a7f6-109">Consulte o artigo "[Skype para topologias de negócios compatíveis com autenticação moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)" Se você estiver em Skype para Business Online ou local, tem um HMA topologia mista e precisar examinar topologias com suporte, antes de começar.</span><span class="sxs-lookup"><span data-stu-id="5a7f6-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="5a7f6-110">Como desabilitar a autenticação de moderno híbrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="5a7f6-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="5a7f6-111">**Exchange local**: Abra o Shell de gerenciamento do Exchange e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="5a7f6-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="5a7f6-p103">**Exchange Online**: [conectar-se ao Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) com o PowerShell remoto. Execute o seguinte comando para ativar o sinalizador *OAuth2ClientProfileEnabled* como 'falso':</span><span class="sxs-lookup"><span data-stu-id="5a7f6-p103">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="5a7f6-114">Como desabilitar a autenticação de moderno híbrida (Skype para negócios)</span><span class="sxs-lookup"><span data-stu-id="5a7f6-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="5a7f6-115">**Skype para negócios local**: execute os seguintes comandos no Skype do Shell de gerenciamento de negócios:</span><span class="sxs-lookup"><span data-stu-id="5a7f6-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="5a7f6-p104">**Skype para negócios on-line**: [conectar-se ao Skype para negócios Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) com o PowerShell remoto. Execute o seguinte comando para desabilitar a autenticação moderno:</span><span class="sxs-lookup"><span data-stu-id="5a7f6-p104">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell. Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="5a7f6-118">[Vínculo inverso para a visão geral de autenticação moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="5a7f6-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

