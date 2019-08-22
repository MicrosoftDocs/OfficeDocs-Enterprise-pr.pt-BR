---
title: Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange
ms.author: kvice
author: kelleyvice-msft
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
ms.openlocfilehash: 91373adf590ad9a69880de20897795ced23d98b8
ms.sourcegitcommit: c8acfa57a22d7d055500f2e8b84a9ef252c70e82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "36493318"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="e8be0-104">Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange</span><span class="sxs-lookup"><span data-stu-id="e8be0-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="e8be0-105">Se você habilitou a autenticação moderna híbrida (HMA) apenas para encontrá-la inadequada ao seu ambiente atual, é possível desabilitar a HMA.</span><span class="sxs-lookup"><span data-stu-id="e8be0-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="e8be0-106">Este artigo explica como.</span><span class="sxs-lookup"><span data-stu-id="e8be0-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="e8be0-107">Quem é este artigo?</span><span class="sxs-lookup"><span data-stu-id="e8be0-107">Who is this article for?</span></span>

<span data-ttu-id="e8be0-108">Se você habilitou a autenticação moderna no Skype for Business online ou no local e/ou no Exchange Online ou no local e descobriu que precisa desabilitar a HMA, estas etapas são para você.</span><span class="sxs-lookup"><span data-stu-id="e8be0-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8be0-109">Consulte o artigo "topologias do[Skype for Business com suporte com autenticação moderna](https://technet.microsoft.com/en-us/library/mt803262.aspx)" se você estiver no Skype for Business online ou no local, tenha uma HMA de topologia mista e precise examinar as topologias com suporte antes de começar.</span><span class="sxs-lookup"><span data-stu-id="e8be0-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="e8be0-110">Como desabilitar a autenticação moderna híbrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="e8be0-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="e8be0-111">**Exchange local**: Abra o Shell de gerenciamento do Exchange e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e8be0-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="e8be0-112">**Exchange Online**: [Conecte-se ao Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) com o PowerShell remoto.</span><span class="sxs-lookup"><span data-stu-id="e8be0-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="e8be0-113">Execute o comando a seguir para transformar o sinalizador *OAuth2ClientProfileEnabled* como ' false ':</span><span class="sxs-lookup"><span data-stu-id="e8be0-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="e8be0-114">Como desabilitar a autenticação moderna híbrida (Skype for Business)</span><span class="sxs-lookup"><span data-stu-id="e8be0-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="e8be0-115">**Skype for Business local**: execute os seguintes comandos no Shell de gerenciamento do Skype for Business:</span><span class="sxs-lookup"><span data-stu-id="e8be0-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="e8be0-116">**Skype for Business online**: [conectar-se ao Skype for Business online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) com o PowerShell remoto.</span><span class="sxs-lookup"><span data-stu-id="e8be0-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="e8be0-117">Execute o seguinte comando para desabilitar a autenticação moderna:</span><span class="sxs-lookup"><span data-stu-id="e8be0-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="e8be0-118">[Link de volta para a visão geral da autenticação moderna](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="e8be0-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

