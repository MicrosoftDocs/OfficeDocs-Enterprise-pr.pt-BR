---
title: Experiência do usuário em um ambiente de multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba mais sobre a experiência do usuário do SharePoint e OneDrive em um ambiente multi-geo.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="f09b3-103">Experiência do usuário em um ambiente multi-geo</span><span class="sxs-lookup"><span data-stu-id="f09b3-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="f09b3-104">Aqui está o que os usuários verão em uma configuração de OneDrive Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="f09b3-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="f09b3-105">OneDrive do usuário para o local da empresa</span><span class="sxs-lookup"><span data-stu-id="f09b3-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="f09b3-p101">Os usuários terão sua OneDrive for Business provisionado no seu local de dados preferida. Se um usuário navega até um URL de OneDrive que contém uma localização geográfica incorreta (por exemplo, um indicador de um local de geo anterior), eles serão automaticamente redirecionados para o OneDrive no geo-local apropriado.</span><span class="sxs-lookup"><span data-stu-id="f09b3-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="f09b3-108">Compartilhando</span><span class="sxs-lookup"><span data-stu-id="f09b3-108">Sharing</span></span>

<span data-ttu-id="f09b3-p102">A experiência do People Picker mostra todos os usuários onde quer que estejam geo. Isso permite que um usuário compartilhar com outro usuário em seu geo mesmo ou em qualquer um dos outros locais de localização geográfica do seu locatário. Conteúdo de diferente geo locais serão exibidas no modo de exibição **compartilhou** no OneDrive do usuário for Business e podem ser acessados com experiência de Single-Sign-On independentemente de qual geo-local está hospedada no.</span><span class="sxs-lookup"><span data-stu-id="f09b3-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="f09b3-112">Aplicativos do Office</span><span class="sxs-lookup"><span data-stu-id="f09b3-112">Office applications</span></span>

<span data-ttu-id="f09b3-p103">Aplicativos do Office como Word, Excel e PowerPoint detectará automaticamente o correto OneDrive for Business geo-local para cada usuário quando fazem logon. Os usuários não precisam digitar a URL de geo específica para sua OneDrive.</span><span class="sxs-lookup"><span data-stu-id="f09b3-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="f09b3-115">OneDrive for Business cliente de sincronização</span><span class="sxs-lookup"><span data-stu-id="f09b3-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="f09b3-116">O OneDrive for Business cliente de sincronização (versão 17.3.6943.0625 e posterior) detectará automaticamente o OneDrive correto para o local da empresa geo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f09b3-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="f09b3-117">Inicializador de aplicativos do Office 365</span><span class="sxs-lookup"><span data-stu-id="f09b3-117">Office 365 app launcher</span></span>

<span data-ttu-id="f09b3-p104">O iniciador app está ciente Multi-Geo e direcionará cada lado a lado para o local apropriado geo da carga de trabalho. Os pontos de blocos de OneDrive para o local correto geo onde a biblioteca do OneDrive do usuário está hospedada, enquanto a lado a lado SharePoint apontará todos os usuários para o local central, como sites de equipe ainda estejam hospedados lá.</span><span class="sxs-lookup"><span data-stu-id="f09b3-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="f09b3-120">Me aprofundar perfis de usuário</span><span class="sxs-lookup"><span data-stu-id="f09b3-120">Delve User profiles</span></span>

<span data-ttu-id="f09b3-p105">Informações de perfil de usuário são administradas no local de geo do usuário. Ao selecionar um usuário, você será direcionado para o local de geo apropriado para o usuário, onde você verá seus detalhes de perfil completo.</span><span class="sxs-lookup"><span data-stu-id="f09b3-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="f09b3-123">Se Delve estiver desativada, você verá o perfil clássico experiência no SharePoint, que não é multi-geo ciente.</span><span class="sxs-lookup"><span data-stu-id="f09b3-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="f09b3-124">Delve</span><span class="sxs-lookup"><span data-stu-id="f09b3-124">Delve</span></span>

<span data-ttu-id="f09b3-125">Para usuários do Office 365 que estiverem nas instâncias de satélite, Multi-Geo me aprofundar é suportado, com a limitação que são Delve não vinculados a postagens de blog do SharePoint escritas por usuários de outras regiões, apenas aos seus sites de blog do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f09b3-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="f09b3-126">Pesquisa</span><span class="sxs-lookup"><span data-stu-id="f09b3-126">Search</span></span>

<span data-ttu-id="f09b3-p106">Cada local geo tem seus próprios índice de pesquisa e o Centro de pesquisa. Quando um usuário procura, a consulta é enviada para todos os locais de geo e resultados retornados são mesclados e, em seguida, classificados para que o usuário obtém resultados unificados. Os usuários obtém os resultados de todos os locais de geo onde quer que estejam suas próprias geo. Consulte [Configurar a pesquisa do OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) para obter informações específicas.</span><span class="sxs-lookup"><span data-stu-id="f09b3-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="f09b3-131">Há suporte para os seguintes clientes de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="f09b3-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="f09b3-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="f09b3-132">OneDrive for Business</span></span>

-   <span data-ttu-id="f09b3-133">Delve</span><span class="sxs-lookup"><span data-stu-id="f09b3-133">Delve</span></span>

-   <span data-ttu-id="f09b3-134">Página inicial do SharePoint</span><span class="sxs-lookup"><span data-stu-id="f09b3-134">SharePoint Home</span></span>

-   <span data-ttu-id="f09b3-135">Centro de pesquisa</span><span class="sxs-lookup"><span data-stu-id="f09b3-135">The Search Center</span></span>

-   <span data-ttu-id="f09b3-136">Aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint</span><span class="sxs-lookup"><span data-stu-id="f09b3-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="f09b3-137">OneDrive iOS e Android</span><span class="sxs-lookup"><span data-stu-id="f09b3-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="f09b3-p107">O iOS OneDrive e aplicativos móveis Android mostrará seus arquivos de OneDrive e os arquivos compartilhados com você, independente da sua localização geográfica. Pesquisa de aplicativos móveis OneDrive mostrará resultados relevantes de todos os locais de geo. Baixe a versão mais recente desses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f09b3-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="f09b3-141">Para obter mais informações, consulte Use [OneDrive em iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) e [Uso do OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .</span><span class="sxs-lookup"><span data-stu-id="f09b3-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="f09b3-142">Experiência de equipes</span><span class="sxs-lookup"><span data-stu-id="f09b3-142">Teams Experience</span></span>

<span data-ttu-id="f09b3-p108">As equipes é multi-geo ciente. Arquivos de OneDrive e visualizadas recentemente são mostrados, independentemente da localização do geo do usuário. @ menções o trabalho com usuários de todos os locais de geo.</span><span class="sxs-lookup"><span data-stu-id="f09b3-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
