---
title: Adicionar ou remover um administrador geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba como adicionar ou remover um administrador geo no OneDrive para Business Multi-Geo.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="84709-103">Adicionar ou remover um administrador geo no OneDrive para Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="84709-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="84709-p101">Você pode configurar administradores separados para cada localidade geo que você tem no seu locatário. Esses administradores terão acesso às configurações de SharePoint Online e OneDrive que são específicos para sua localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="84709-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="84709-p102">Alguns serviços - como o repositório de termos - são administrados do local central e replicados para locais de satélite. O administrador geo para o local central tem acesso a esses, enquanto não geo admins para locais de satélite.</span><span class="sxs-lookup"><span data-stu-id="84709-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="84709-108">Os administradores globais e do SharePoint Online continuar têm acesso a configurações em todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="84709-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="84709-109">Configurando geo administradores</span><span class="sxs-lookup"><span data-stu-id="84709-109">Configuring geo administrators</span></span>

<span data-ttu-id="84709-110">Configurar geo admins requer o módulo de PowerShell do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="84709-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="84709-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectar o Centro de administração do geo local onde deseja adicionar o administrador do geo. (Por exemplo, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="84709-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="84709-112">Para adicionar um usuário como um administrador geo, execute:`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="84709-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="84709-113">Para exibir os administradores geo existente de um local, execute`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="84709-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="84709-114">Para remover um usuário como um administrador Geo de um local, execute`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="84709-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="84709-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="84709-115">See Also</span></span>

[<span data-ttu-id="84709-116">Adicionar-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="84709-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="84709-117">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="84709-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="84709-118">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="84709-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)