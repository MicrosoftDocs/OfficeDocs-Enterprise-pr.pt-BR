---
title: Adicionar ou remover um administrador geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba como adicionar ou remover um administrador geo no OneDrive para Business Multi-Geo.
ms.openlocfilehash: b88467cf2f33ec3a3a8bf6c2d6927e69e9f7af65
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="57ad7-103">Adicionar ou remover um administrador geo no OneDrive para Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="57ad7-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="57ad7-p101">Você pode configurar administradores separados para cada localidade geo que você tem no seu locatário. Esses administradores terão acesso às configurações de SharePoint Online e OneDrive que são específicos para sua localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="57ad7-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="57ad7-p102">Alguns serviços - como o repositório de termos - são administrados do local central e replicados para locais de satélite. O administrador geo para o local central tem acesso a esses, enquanto não geo admins para locais de satélite.</span><span class="sxs-lookup"><span data-stu-id="57ad7-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="57ad7-108">Os administradores globais e do SharePoint Online continuar têm acesso a configurações em todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="57ad7-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="57ad7-109">Configurando geo administradores</span><span class="sxs-lookup"><span data-stu-id="57ad7-109">Configuring geo administrators</span></span>

<span data-ttu-id="57ad7-110">Configurar geo admins requer o módulo de PowerShell do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="57ad7-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="57ad7-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectar o Centro de administração do geo local onde deseja adicionar o administrador do geo. (Por exemplo, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="57ad7-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="57ad7-112">Para exibir os administradores geo existente de um local, execute`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="57ad7-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="57ad7-113">Adicionando um usuário como um administrador geo</span><span class="sxs-lookup"><span data-stu-id="57ad7-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="57ad7-114">Para adicionar um usuário como um administrador geo, execute:`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="57ad7-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="57ad7-115">Para remover um usuário como um administrador Geo de um local, execute`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="57ad7-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="57ad7-116">Adicionar um grupo como um administrador geo</span><span class="sxs-lookup"><span data-stu-id="57ad7-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="57ad7-117">Você pode adicionar um grupo de segurança ou de um grupo de segurança habilitados para email como um administrador de geo. (Grupos de distribuição e grupos do Office 365 não são suportados.)</span><span class="sxs-lookup"><span data-stu-id="57ad7-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="57ad7-118">Para adicionar um grupo como um administrador geo, execute:`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="57ad7-118">To add a group as a geo admin, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="57ad7-119">Para remover um grupo como um administrador geo, execute`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="57ad7-119">To remove a group as a geo admin, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="57ad7-p103">Observe que nem todos os grupos de segurança tem um alias de grupo. Se você deseja adicionar um grupo de segurança que não tem um alias, execute [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) para recuperar uma lista de grupos, encontre ObjectID do grupo de segurança e, em seguida, execute:</span><span class="sxs-lookup"><span data-stu-id="57ad7-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="57ad7-122">Para remover um grupo usando o ObjectID, execute`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="57ad7-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="57ad7-123">Como acessar o Centro de administração para um local específico de geo</span><span class="sxs-lookup"><span data-stu-id="57ad7-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="57ad7-124">Para administrar as configurações de OneDrive para sua localização geográfica, os administradores devem acessar diretamente usando o seguinte formato de URL do Centro de administração do OneDrive:</span><span class="sxs-lookup"><span data-stu-id="57ad7-124">To administer OneDrive settings for their geo-location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="57ad7-125">https://admin.onedrive.com/?geo=<*Geo*></span><span class="sxs-lookup"><span data-stu-id="57ad7-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="57ad7-126">Por exemplo, o Centro de administração do OneDrive para Canadá está localizado em: https://admin.onedrive.com/?geo=CAN.</span><span class="sxs-lookup"><span data-stu-id="57ad7-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="57ad7-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="57ad7-127">See Also</span></span>

[<span data-ttu-id="57ad7-128">Adicionar-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="57ad7-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="57ad7-129">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="57ad7-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="57ad7-130">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="57ad7-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="57ad7-131">Definir um alias (MailNickName) para um grupo de segurança</span><span class="sxs-lookup"><span data-stu-id="57ad7-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)