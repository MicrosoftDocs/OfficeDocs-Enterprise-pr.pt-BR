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
ms.openlocfilehash: 96870923c00cebc247609b67378fd39011077d45
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072373"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="f7e52-103">Criar um grupo no Office 365 com uma PDL específica </span><span class="sxs-lookup"><span data-stu-id="f7e52-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="f7e52-104">Quando os usuários em um ambiente multigeógrafico criam um grupo do Office 365, o grupo local de dados preferenciais é definido automaticamente para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f7e52-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="f7e52-105">Os administradores globais, do SharePoint e do Exchange podem criar grupos em qualquer região que selecionarem.</span><span class="sxs-lookup"><span data-stu-id="f7e52-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="f7e52-106">Se precisar criar um grupo com uma PDL específica, você pode fazer isso através do centro do administração do SharePoint ou através do cmdlet do novo PowerShell do Microsoft Exchange Online UnifiedGroup.</span><span class="sxs-lookup"><span data-stu-id="f7e52-106">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="f7e52-107">Quando você fizer isso, a caixa de correio de grupo e o site do SharePoint associados ao grupo serão provisionados na PDL especificada.</span><span class="sxs-lookup"><span data-stu-id="f7e52-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="f7e52-108">Para criar um grupo do Office 365 com a PDL que você especificar, vá para o centro de administração do SharePoint na localização geográfica em que você deseja criar o site de grupo.</span><span class="sxs-lookup"><span data-stu-id="f7e52-108">To create an Office 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="f7e52-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f7e52-109">For example:</span></span>

<span data-ttu-id="f7e52-110">Se você deseja criar um site de grupo no local da Austrália, poderá ir para https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement </span><span class="sxs-lookup"><span data-stu-id="f7e52-110">If you wan to create a group site in your Australtia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="f7e52-111">Selecione **+ Criar**.</span><span class="sxs-lookup"><span data-stu-id="f7e52-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="f7e52-112">Siga o processo para criar um site de grupo.</span><span class="sxs-lookup"><span data-stu-id="f7e52-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="f7e52-113">O seu site de grupo será provisionado na localização geográfica correspondente ao centro de administração do SharePoint no qual você iniciou a solicitação de criação de site.</span><span class="sxs-lookup"><span data-stu-id="f7e52-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="f7e52-114">Usando o PowerShell do Exchange</span><span class="sxs-lookup"><span data-stu-id="f7e52-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="f7e52-115">Conecte-se ao PowerShell do Exchange Online e passe o parâmetro *-MailBoxRegion* com o código de localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="f7e52-115">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="f7e52-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f7e52-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![O Cmdlet do PowerShell de captura de tela do novo UnifiedGroup com sintaxe](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="f7e52-118">Observe que o provisionamento de sites de grupo do SharePoint é sob demanda.</span><span class="sxs-lookup"><span data-stu-id="f7e52-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="f7e52-119">O site será configurado a primeira vez que um membro ou proprietário do grupo tentar acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="f7e52-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="f7e52-120">Códigos de localização geográfica</span><span class="sxs-lookup"><span data-stu-id="f7e52-120">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="f7e52-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="f7e52-121">See also</span></span>

[<span data-ttu-id="f7e52-122">Conectar-se ao PowerShell do Exchange Online </span><span class="sxs-lookup"><span data-stu-id="f7e52-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
