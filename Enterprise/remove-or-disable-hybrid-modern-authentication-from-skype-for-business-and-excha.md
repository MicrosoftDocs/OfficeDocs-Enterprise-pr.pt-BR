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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="0aefa-104">Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange</span><span class="sxs-lookup"><span data-stu-id="0aefa-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="0aefa-p102">Se você tiver habilitado híbrida moderno autenticação (HMA) descobriu que é inadequado para seu ambiente atual, você pode desabilitar HMA. Este artigo explica como.</span><span class="sxs-lookup"><span data-stu-id="0aefa-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="0aefa-107">Quem é este artigo para?</span><span class="sxs-lookup"><span data-stu-id="0aefa-107">Who is this article for?</span></span>

<span data-ttu-id="0aefa-108">Se você tiver habilitado moderno autenticação no Skype para Business Online ou no local, e/ou Exchange Online ou local e encontrado que você precisa desabilitar HMA, essas etapas são para você.</span><span class="sxs-lookup"><span data-stu-id="0aefa-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>
  
 <span data-ttu-id="0aefa-109">**Importante** Consulte o artigo " [Skype para topologias de negócios compatíveis com autenticação moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)" Se você estiver em Skype para Business Online ou local, tem um HMA topologia mista e precisar examinar topologias com suporte, antes de começar.</span><span class="sxs-lookup"><span data-stu-id="0aefa-109">**Important** See the ' [Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="0aefa-110">Como desabilitar a autenticação de moderno híbrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="0aefa-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="0aefa-111">**Exchange local**: Abra o Shell de gerenciamento do Exchange e execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="0aefa-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following command.</span></span> 
    
1. <span data-ttu-id="0aefa-112">Set-OrganizationConfig-OAuth2ClientProfileEnabled $false</span><span class="sxs-lookup"><span data-stu-id="0aefa-112">Set-OrganizationConfig -OAuth2ClientProfileEnabled $false</span></span>
    
2. <span data-ttu-id="0aefa-113">Set-AuthServer-Identity evoSTS - IsDefaultAuthorizationEndpoint $false</span><span class="sxs-lookup"><span data-stu-id="0aefa-113">Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false</span></span>
    
2. <span data-ttu-id="0aefa-p103">**Exchange Online**: conectar-se ao Exchange Online com o PowerShell remoto. Execute o seguinte comando para ativar o sinalizador *OAuth2ClientProfileEnabled* como 'falso'.</span><span class="sxs-lookup"><span data-stu-id="0aefa-p103">**Exchange Online**: Connect to Exchange Online with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false'.</span></span> 
    
1. <span data-ttu-id="0aefa-116">Set-OrganizationConfig-OAuth2ClientProfileEnabled: $false</span><span class="sxs-lookup"><span data-stu-id="0aefa-116">Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false</span></span>
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="0aefa-117">Como desabilitar a autenticação de moderno híbrida (Skype para negócios)</span><span class="sxs-lookup"><span data-stu-id="0aefa-117">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="0aefa-118">**Skype para negócios local**: execute os seguintes comandos no Skype do Shell de gerenciamento de negócios.</span><span class="sxs-lookup"><span data-stu-id="0aefa-118">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell.</span></span>
    
1. <span data-ttu-id="0aefa-119">Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity ""</span><span class="sxs-lookup"><span data-stu-id="0aefa-119">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""</span></span>
    
2. <span data-ttu-id="0aefa-p104">**Skype para negócios on-line**: conectar ao Skype for Business Online com o PowerShell remoto. Execute o seguinte comando para desabilitar a autenticação moderno.</span><span class="sxs-lookup"><span data-stu-id="0aefa-p104">**Skype for Business Online**: Connect to Skype for Business Online with Remote PowerShell. Run the following command to disable Modern Authentication.</span></span> 
    
1. <span data-ttu-id="0aefa-122">Set-CsOAuthConfiguration - ClientAdalAuthOverride não permitido</span><span class="sxs-lookup"><span data-stu-id="0aefa-122">Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed</span></span>
    
<span data-ttu-id="0aefa-123">[Vínculo inverso para a visão geral de autenticação moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="0aefa-123">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

