---
title: Experiência do usuário em um ambiente multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Saiba mais sobre a experiência do usuário do SharePoint e do OneDrive em um ambiente multigeográfico.
ms.openlocfilehash: 951efb636ce00f59393f624687d44a406fcf3fc0
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849827"
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="f604a-103">Experiência do usuário em um ambiente multigeográfico</span><span class="sxs-lookup"><span data-stu-id="f604a-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="f604a-104">Vejamos a seguir o que os usuários verão em uma configuração multigeográfica do OneDrive:</span><span class="sxs-lookup"><span data-stu-id="f604a-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="f604a-105">Local do OneDrive for Business do usuário</span><span class="sxs-lookup"><span data-stu-id="f604a-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="f604a-p101">Os usuários terão o OneDrive for Business provisionado em sua localização dados preferida. Se um usuário navegar para uma URL do OneDrive com uma localização geográfica incorreta (por exemplo, um indicador de uma localização geográfica anterior), eles serão redirecionados automaticamente para o OneDrive na localização geográfica adequada.</span><span class="sxs-lookup"><span data-stu-id="f604a-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="f604a-108">Compartilhamento</span><span class="sxs-lookup"><span data-stu-id="f604a-108">Sharing</span></span>

<span data-ttu-id="f604a-p102">A experiência do Seletor de Pessoas mostra todos os usuários independentemente da localização geográfica. Isso permite que um usuário compartilhe com outro usuário, em sua mesma localização geográfica ou em qualquer outra localização do seu locatário. O conteúdo de localizações geográficas diferentes será exibido na visualização **Compartilhado comigo** no OneDrive for Business do usuário, e poderá ser acessado com a experiência de logon único, independentemente de em qual localização geográfica estiver hospedado.</span><span class="sxs-lookup"><span data-stu-id="f604a-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="f604a-112">Aplicativos do Office</span><span class="sxs-lookup"><span data-stu-id="f604a-112">Office applications</span></span>

<span data-ttu-id="f604a-p103">Os aplicativos do Office como o Word, o Excel e o PowerPoint detectarão automaticamente a localização geográfica correta do OneDrive for Business para todos os usuários ao entrarem. Os usuários não precisam inserir a URL do OneDrive específica do local.</span><span class="sxs-lookup"><span data-stu-id="f604a-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="f604a-115">Cliente de sincronização do OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="f604a-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="f604a-116">O cliente de sincronização do OneDrive for Business (versão 17.3.6943.0625 e posteriores) detectará automaticamente a localização geográfica correta do OneDrive for Business para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f604a-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="f604a-117">Inicializador de aplicativos do Office 365</span><span class="sxs-lookup"><span data-stu-id="f604a-117">Office 365 app launcher</span></span>

<span data-ttu-id="f604a-p104">O inicializador de aplicativos reconhece localizações geográficas diferentes e direcionará cada bloco para a localização geográfica adequada da carga de trabalho. O bloco do OneDrive aponta para a localização geográfica correta na qual a biblioteca do OneDrive do usuário está hospedada, ao passo que o bloco do SharePoint apontará todos os usuários para o local central, pois os sites de equipe ainda estão hospedados lá.</span><span class="sxs-lookup"><span data-stu-id="f604a-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="f604a-120">Perfis do usuário Delve</span><span class="sxs-lookup"><span data-stu-id="f604a-120">Delve User profiles</span></span>

<span data-ttu-id="f604a-p105">As informações de perfil de usuário são controladas na localização geográfica do usuário. Ao selecionar um usuário, você será direcionado para a localização geográfica adequada do usuário, onde você verá os detalhes do perfil completos dele.</span><span class="sxs-lookup"><span data-stu-id="f604a-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="f604a-123">Se o Delve estiver desativado, você verá a experiência de perfil clássica no SharePoint, que não reconhece diferentes localizações geográficas.</span><span class="sxs-lookup"><span data-stu-id="f604a-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="f604a-124">Delve</span><span class="sxs-lookup"><span data-stu-id="f604a-124">Delve</span></span>

<span data-ttu-id="f604a-125">Para os usuários do Office 365 que estão nas instâncias-satélites, a multigeografia do Delve tem suporte, com a limitação de que o Delve não contém ligação para postagens de blog do SharePoint escritas por usuários em outras regiões, apenas para os sites de blog do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f604a-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="f604a-126">Pesquisar</span><span class="sxs-lookup"><span data-stu-id="f604a-126">Search</span></span>

<span data-ttu-id="f604a-p106">Cada localização geográfica tem o seu próprio índice de pesquisa e Centro de pesquisa. Quando um usuário faz uma pesquisa, a consulta é enviada a todas as localizações geográficas e os resultados retornados são mesclados e, depois, classificados de modo que o usuário obtenha resultados unificados. Os usuários obtêm resultados de todas as localizações geográfica independentemente da sua própria localização. Leia informações específicas em [Configurar a pesquisa do OneDrive for Business com Funcionalidade Multigeográfica](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="f604a-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="f604a-131">Há suporte para os seguintes clientes de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="f604a-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="f604a-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="f604a-132">OneDrive for Business</span></span>

-   <span data-ttu-id="f604a-133">Delve</span><span class="sxs-lookup"><span data-stu-id="f604a-133">Delve</span></span>

-   <span data-ttu-id="f604a-134">Página inicial do SharePoint</span><span class="sxs-lookup"><span data-stu-id="f604a-134">SharePoint Home</span></span>

-   <span data-ttu-id="f604a-135">O Centro de Pesquisa</span><span class="sxs-lookup"><span data-stu-id="f604a-135">The Search Center</span></span>

-   <span data-ttu-id="f604a-136">Aplicativos de pesquisa personalizada que usam a API de pesquisa do SharePoint</span><span class="sxs-lookup"><span data-stu-id="f604a-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="f604a-137">OneDrive para iOS e Android</span><span class="sxs-lookup"><span data-stu-id="f604a-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="f604a-p107">Os aplicativos móveis do OneDrive para iOS e Android mostrarão os seus arquivos do OneDrive e arquivos compartilhados com você, independentemente da localização geográfica deles. A pesquisa dos aplicativos móveis do OneDrive mostrará resultados relevantes de todas as localizações geográficas. Baixe a versão mais recente desses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f604a-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="f604a-141">Confira mais informações em [Usar o OneDrive para iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) e [Usar o OneDrive para Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36).</span><span class="sxs-lookup"><span data-stu-id="f604a-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="f604a-142">Experiência do Teams</span><span class="sxs-lookup"><span data-stu-id="f604a-142">Teams Experience</span></span>

<span data-ttu-id="f604a-p108">O Teams reconhece localizações geográficas diferentes. Os arquivos do OneDrive e os arquivos visualizados recentemente são mostrados independentemente da localização geográfica do usuário. As menções com @ funcionam com usuários de todas as localizações.</span><span class="sxs-lookup"><span data-stu-id="f604a-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
