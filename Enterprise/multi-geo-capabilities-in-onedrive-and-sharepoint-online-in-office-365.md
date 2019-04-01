---
title: Funcionalidades multigeográficas no OneDrive e no SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda a sua presença no Office 365 para várias regiões geográficas com funcionalidades multigeográficas do OneDrive Online.
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948582"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="d1553-103">Funcionalidades multigeográficas no OneDrive e no SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d1553-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="d1553-104">As funcionalidades multigeográfica do OneDrive e do SharePoint Online permite controlar o país ou região onde recursos compartilhados, como sites de equipe do SharePoint e caixas de correio do Grupo do Office 365 são armazenados em repouso.</span><span class="sxs-lookup"><span data-stu-id="d1553-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Office 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="d1553-105">Cada usuário, caixa de correio do Grupo e site do SharePoint possui uma Localização Preferencial do Dados (PDL) que indica a localização geográfica onde os dados relacionados devem ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="d1553-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="d1553-106">Dados pessoais do usuário (caixa de correio do Exchange e OneDrive) juntamente com Grupos do Office 365 ou sites do SharePoint criados por eles podem ser armazenados em uma localização geográfica especificada para atender aos requisitos de residência dos dados.</span><span class="sxs-lookup"><span data-stu-id="d1553-106">Users' personal data (Exchange mailbox and OneDrive) along with any Office 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="d1553-107">Você pode [especificar administradores diferentes para cada localização geográfica](add-a-sharepoint-geo-admin.md).</span><span class="sxs-lookup"><span data-stu-id="d1553-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="d1553-108">Os usuários têm uma experiência perfeita ao usar os serviços do Office 365, incluindo os aplicativos do Office, OneDrive e Search.</span><span class="sxs-lookup"><span data-stu-id="d1553-108">Users get a seamless experience when using Office 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="d1553-109">Para obter mais detalhes, confira [Experiência do usuário em um ambiente multigeográfico](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="d1553-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="d1553-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="d1553-110">OneDrive</span></span>

<span data-ttu-id="d1553-111">Cada usuário do OneDrive pode ser provisionado ou [movido por um administrador](move-onedrive-between-geo-locations.md) em um localização por satélite de acordo com PDL do usuário.</span><span class="sxs-lookup"><span data-stu-id="d1553-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="d1553-112">Os arquivos pessoais são mantidos nessa localização geográfica, embora eles possam ser compartilhados com usuários em outras localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="d1553-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sites-and-groups"></a><span data-ttu-id="d1553-113">Sites e Grupos</span><span class="sxs-lookup"><span data-stu-id="d1553-113">Active Directory Sites and Routing Groups tab</span></span>

<span data-ttu-id="d1553-114">Quando um usuário cria um site conectado a um grupo do SharePoint, o PDL é usado para determinar a localização geográfica onde o site e sua caixa de correio de Grupo associada do grupo foram criados.</span><span class="sxs-lookup"><span data-stu-id="d1553-114">When a user creates a SharePoint group-connected site, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="d1553-115">(Se o valor PDL do usuário ainda não foi definida ou foi definida em uma localização geográfica que ainda não foi configurada como uma localização por satélite, os sites e as caixas de correio são criados em uma localização central.)</span><span class="sxs-lookup"><span data-stu-id="d1553-115">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="d1553-116">Os serviços do Office 365 diferentes do Exchange, OneDrive, e SharePoint não são multigeográficos.</span><span class="sxs-lookup"><span data-stu-id="d1553-116">Office 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="d1553-117">No entanto, os grupos do Office 365 que são criados por esses serviços serão marcados com a PDL do criador e sua caixa de correio do Grupo do Exchange e o Site do Grupo do SharePoint O365 provisionados na localização geográfica correspondente.</span><span class="sxs-lookup"><span data-stu-id="d1553-117">However, Office 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="d1553-118">Gerenciar o ambiente multigeográfico</span><span class="sxs-lookup"><span data-stu-id="d1553-118">Managing the multi-geo environment</span></span>

<span data-ttu-id="d1553-119">A configuração e o gerenciamento do ambiente multigeográfico são feitos pelo centro de administração do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d1553-119">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![Captura de tela da página de localizações geográficas do centro de administração SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="d1553-121">(Algumas ações, como mover um site do SharePoint ou um site do OneDrive necessitam do Microsoft PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="d1553-121">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="d1553-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="d1553-122">See also</span></span>

[<span data-ttu-id="d1553-123">Aka.ms/GetMultiGeo </span><span class="sxs-lookup"><span data-stu-id="d1553-123">Aka.ms/GetMultiGeo </span></span>](https://Aka.ms/GetMultiGeo)

[<span data-ttu-id="d1553-124">Administrar um ambiente multigeográfico</span><span class="sxs-lookup"><span data-stu-id="d1553-124">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="d1553-125">Cotas de armazenamento do SharePoint em ambientes multigeográficos</span><span class="sxs-lookup"><span data-stu-id="d1553-125">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="d1553-126">Administrar caixas de correio do Exchange Online em um ambiente multigeográfico</span><span class="sxs-lookup"><span data-stu-id="d1553-126">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
