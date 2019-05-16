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
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="bbeb2-103">Criar um grupo no Office 365 com uma PDL específica </span><span class="sxs-lookup"><span data-stu-id="bbeb2-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="bbeb2-104">Quando os usuários em um ambiente multigeógrafico criam um grupo do Office 365, o grupo local de dados preferenciais é definido automaticamente para o usuário.</span><span class="sxs-lookup"><span data-stu-id="bbeb2-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="bbeb2-105">Se precisar criar um grupo com uma PDL específica, você pode fazer isso usando o cmdlet do novo PowerShell do Microsoft Exchange Online UnifiedGroup.</span><span class="sxs-lookup"><span data-stu-id="bbeb2-105">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="bbeb2-106">Quando você fizer isso, a caixa de correio de grupo e o site do SharePoint associados ao grupo serão provisionados na PDL especificada.</span><span class="sxs-lookup"><span data-stu-id="bbeb2-106">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="bbeb2-107">Você precisa ser um administrador global ou administrador do SharePoint Online para corrigir esses erros.</span><span class="sxs-lookup"><span data-stu-id="bbeb2-107">You must be a global administrator or a SharePoint Online or Exchange Online administrator to do this.</span></span>

<span data-ttu-id="bbeb2-108">Para criar um grupo do Office 365 com PDL que você especificar, conecte-se ao PowerShell do Exchange Online e passar o parâmetro *- MailBoxRegion* com o código de localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="bbeb2-108">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="bbeb2-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bbeb2-109">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![O Cmdlet do PowerShell de captura de tela do novo UnifiedGroup com sintaxe](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="bbeb2-111">Observe que o provisionamento de sites de grupo do SharePoint é sob demanda.</span><span class="sxs-lookup"><span data-stu-id="bbeb2-111">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="bbeb2-112">O site será configurado a primeira vez que um membro ou proprietário do grupo tentar acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="bbeb2-112">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="bbeb2-113">Códigos de localização geográfica</span><span class="sxs-lookup"><span data-stu-id="bbeb2-113">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="bbeb2-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="bbeb2-114">See also</span></span>

[<span data-ttu-id="bbeb2-115">Conectar-se ao PowerShell do Exchange Online </span><span class="sxs-lookup"><span data-stu-id="bbeb2-115">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)