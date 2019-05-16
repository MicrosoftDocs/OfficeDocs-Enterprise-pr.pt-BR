---
title: Adicionar ou remover um administrador geográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: Saiba como adicionar ou remover um administrador geográfica no Office 365 Multi-Geo.
ms.openlocfilehash: 767dcf5284e93b9a2e908d4ec837f034b29cb6db
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068467"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a><span data-ttu-id="a6a57-103">Adicionar ou remover um administrador geográfico no Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="a6a57-103">Add or remove a geo administrator in Office 365 Multi-Geo</span></span>

<span data-ttu-id="a6a57-104">Você pode configurar administradores separados para cada localização geográfica que há em seu locatário.</span><span class="sxs-lookup"><span data-stu-id="a6a57-104">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="a6a57-105">Esses administradores terão acesso às configurações do SharePoint Online e do OneDrive específicas para sua localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="a6a57-105">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="a6a57-106">Alguns serviços, como o repositório de termos, são administrados da localização central e replicados para as localizações via satélite.</span><span class="sxs-lookup"><span data-stu-id="a6a57-106">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="a6a57-107">O administrador geográfico da localização central tem acesso a elas, enquanto que os administradores geográficos via satélite não.</span><span class="sxs-lookup"><span data-stu-id="a6a57-107">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="a6a57-108">Os administradores globais e administradores do SharePoint Online continuam a ter acesso às configurações da localização local e das localizações via satélite.</span><span class="sxs-lookup"><span data-stu-id="a6a57-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="a6a57-109">Configurar os administradores geográficos</span><span class="sxs-lookup"><span data-stu-id="a6a57-109">Configuring geo administrators</span></span>

<span data-ttu-id="a6a57-110">Configurar os administradores geográficos exige o módulo PowerShell do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a6a57-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="a6a57-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para se conectar ao centro de administração da localização geográfica onde você deseja adicionar o administrador geográfico. (Por exemplo, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="a6a57-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="a6a57-112">Para exibir os administradores geográficos existentes de um local, execute `Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="a6a57-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="a6a57-113">Adicionar um usuário como um administrador geográfico</span><span class="sxs-lookup"><span data-stu-id="a6a57-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="a6a57-114">Para adicionar um usuário como um administrador geográfico, execute `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="a6a57-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="a6a57-115">Para remover um usuário como um administrador geográfico de um local, execute  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="a6a57-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="a6a57-116">Adicionar um grupo como um administrador geográfico</span><span class="sxs-lookup"><span data-stu-id="a6a57-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="a6a57-117">Você pode adicionar um grupo de segurança ou de um grupo de segurança habilitado por email como um administrador geográfico. (Grupos de distribuição e Grupos do Office 365 não são suportados.)</span><span class="sxs-lookup"><span data-stu-id="a6a57-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="a6a57-118">Para adicionar um grupo como um administrador geográfico, execute `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="a6a57-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="a6a57-119">Para remover um grupo como um administrador geográfico, execute `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="a6a57-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="a6a57-120">Observe que nem todos os grupos de segurança têm um alias de grupo.</span><span class="sxs-lookup"><span data-stu-id="a6a57-120">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="a6a57-121">Se você quiser adicionar um grupo de segurança que tenha um alias, execute [Get-MsolGroup](https://docs.microsoft.com/pt-BR/powershell/module/msonline/get-msolgroup) para recuperar uma lista de grupos, localizar o ObjectID do grupo de segurança e, em seguida, execute:</span><span class="sxs-lookup"><span data-stu-id="a6a57-121">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="a6a57-122">Para remover um grupo usando o ObjectID, execute `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="a6a57-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="a6a57-123">Confira Também</span><span class="sxs-lookup"><span data-stu-id="a6a57-123">See Also</span></span>

[<span data-ttu-id="a6a57-124">Adicionar-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="a6a57-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="a6a57-125">Obter SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="a6a57-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="a6a57-126">Remover SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="a6a57-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

<span data-ttu-id="a6a57-127">
  [Configurar um alias (MailNickName) para um grupo de segurança](https://docs.microsoft.com/pt-BR/powershell/module/azuread/set-azureadgroup)</span><span class="sxs-lookup"><span data-stu-id="a6a57-127">[Set an alias (MailNickName) for a security group](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)</span></span>