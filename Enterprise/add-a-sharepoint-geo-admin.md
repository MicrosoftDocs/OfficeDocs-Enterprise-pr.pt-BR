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
ms.openlocfilehash: 7630597654df9ad78619b94fedc9e18d5b0b721e
ms.sourcegitcommit: 886b23f590f6187f7a98c1083a3b49359ec2a5c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="6676d-103">Adicionar ou remover um administrador geo no OneDrive para Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="6676d-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="6676d-p101">Você pode configurar administradores separados para cada localidade geo que você tem no seu locatário. Esses administradores terão acesso às configurações de SharePoint Online e OneDrive que são específicos para sua localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="6676d-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="6676d-p102">Alguns serviços - como o repositório de termos - são administrados do local central e replicados para locais de satélite. O administrador geo para o local central tem acesso a esses, enquanto não geo admins para locais de satélite.</span><span class="sxs-lookup"><span data-stu-id="6676d-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="6676d-108">Os administradores globais e do SharePoint Online continuar têm acesso a configurações em todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="6676d-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="6676d-109">Configurando geo administradores</span><span class="sxs-lookup"><span data-stu-id="6676d-109">Configuring geo administrators</span></span>

<span data-ttu-id="6676d-110">Configurar geo admins requer o módulo de PowerShell do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="6676d-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="6676d-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectar o Centro de administração do geo local onde deseja adicionar o administrador do geo. (Por exemplo, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="6676d-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="6676d-112">Para exibir os administradores geo existente de um local, execute`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="6676d-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="6676d-113">Adicionando um usuário como um administrador geo</span><span class="sxs-lookup"><span data-stu-id="6676d-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="6676d-114">Para adicionar um usuário como um administrador geo, execute:`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="6676d-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="6676d-115">Para remover um usuário como um administrador Geo de um local, execute`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="6676d-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="6676d-116">Adicionar um grupo como um administrador geo</span><span class="sxs-lookup"><span data-stu-id="6676d-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="6676d-117">Você pode adicionar um grupo de segurança ou de um grupo de segurança habilitados para email como um administrador de geo. (Grupos de distribuição e grupos do Office 365 não são suportados.)</span><span class="sxs-lookup"><span data-stu-id="6676d-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="6676d-118">Para adicionar um grupo como um administrador geo, execute:`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="6676d-118">To add a group as a geo admin, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="6676d-119">Para remover um grupo como um administrador geo, execute`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="6676d-119">To remove a group as a geo admin, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="6676d-p103">Observe que nem todos os grupos de segurança tem um alias de grupo. Se você deseja adicionar um grupo de segurança que não tem um alias, execute [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) para recuperar uma lista de grupos, encontre ObjectID do grupo de segurança e, em seguida, execute:</span><span class="sxs-lookup"><span data-stu-id="6676d-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="6676d-122">Para remover um grupo usando o ObjectID, execute`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="6676d-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="6676d-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="6676d-123">See Also</span></span>

[<span data-ttu-id="6676d-124">Adicionar-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="6676d-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="6676d-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="6676d-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="6676d-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="6676d-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="6676d-127">Definir um alias (MailNickName) para um grupo de segurança</span><span class="sxs-lookup"><span data-stu-id="6676d-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)