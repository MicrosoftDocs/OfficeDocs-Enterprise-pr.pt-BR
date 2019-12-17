---
title: Use o Windows PowerShell para criar relatórios no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/22/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: 'Resumo: use o Office 365 PowerShell para criar relatórios que você não pode produzir no centro de administração do Microsoft 365.'
ms.openlocfilehash: 9b3ab8490eb3b4b89878eb8ea94ebc5a99ca9254
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072453"
---
# <a name="use-windows-powershell-to-create-reports-in-office-365"></a><span data-ttu-id="ffe2f-103">Use o Windows PowerShell para criar relatórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="ffe2f-103">Use Windows PowerShell to create reports in Office 365</span></span>

<span data-ttu-id="ffe2f-104">Há muitos relatórios diferentes disponíveis no centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ffe2f-104">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="ffe2f-105">No entanto, esses relatórios não apresentam todas as informações e, às vezes, você precisa de mais.</span><span class="sxs-lookup"><span data-stu-id="ffe2f-105">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="ffe2f-106">É aí que você precisa do Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-106">That's when you need Office 365 PowerShell</span></span>
  
<span data-ttu-id="ffe2f-107">Estes artigos descrevem como usar o Office 365 PowerShell para obter informações do locatário do Office 365:</span><span class="sxs-lookup"><span data-stu-id="ffe2f-107">These articles that describe how to use Office 365 PowerShell to obtain information from your Office 365 tenant:</span></span>
  
- <span data-ttu-id="ffe2f-108">Introdução aos relatórios usando o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ffe2f-108">Getting started with reporting using Office 365 PowerShell:</span></span>
    
  - [<span data-ttu-id="ffe2f-109">O Office 365 PowerShell pode revelar informações adicionais que você não consegue ver com o Centro de administração</span><span class="sxs-lookup"><span data-stu-id="ffe2f-109">Office 365 PowerShell can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="ffe2f-110">O Office 365 PowerShell é ótimo para a filtragem de dados</span><span class="sxs-lookup"><span data-stu-id="ffe2f-110">Office 365 PowerShell is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="ffe2f-111">Com o Office 365 PowerShell, é mais fácil imprimir ou salvar dados</span><span class="sxs-lookup"><span data-stu-id="ffe2f-111">Office 365 PowerShell makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="ffe2f-112">Relatórios de contas de usuário e licenças:</span><span class="sxs-lookup"><span data-stu-id="ffe2f-112">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="ffe2f-113">Exibir licenças e serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="ffe2f-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="ffe2f-114">Exibir usuários licenciados e não licenciados com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="ffe2f-114">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="ffe2f-115">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-115">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="ffe2f-116">Exibir as contas de usuário com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-116">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="ffe2f-117">Relatórios do SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="ffe2f-117">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="ffe2f-118">Gerenciar usuários e grupos do SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-118">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx)
    
  - [<span data-ttu-id="ffe2f-119">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-119">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="ffe2f-120">Relatórios do Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="ffe2f-120">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="ffe2f-121">Display Exchange Online mailbox information with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-121">Display Exchange Online mailbox information with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="ffe2f-122">Display Exchange Online reports with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-122">Display Exchange Online reports with Office 365 PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="ffe2f-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="ffe2f-123">See also</span></span>

[<span data-ttu-id="ffe2f-124">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-124">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ffe2f-125">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-125">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="ffe2f-126">Gerenciar o SharePoint Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-126">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="ffe2f-127">Gerenciar contas de usuário, licenças e grupos com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffe2f-127">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
