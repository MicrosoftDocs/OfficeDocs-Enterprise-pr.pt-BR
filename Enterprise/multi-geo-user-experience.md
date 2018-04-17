---
title: User experience in a multgeo environment
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Learn about the SharePoint and OneDrive user experience in a multi-geo environment.
ms.openlocfilehash: 42e384d3e93ca3f5a06a8ee07a37b10e21477038
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="944fc-103">User experience in a multi-geo environment</span><span class="sxs-lookup"><span data-stu-id="944fc-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="944fc-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span><span class="sxs-lookup"><span data-stu-id="944fc-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="944fc-105">User’s OneDrive for Business location</span><span class="sxs-lookup"><span data-stu-id="944fc-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="944fc-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span><span class="sxs-lookup"><span data-stu-id="944fc-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="944fc-108">Compartilhamento</span><span class="sxs-lookup"><span data-stu-id="944fc-108">Sharing</span></span>

<span data-ttu-id="944fc-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span><span class="sxs-lookup"><span data-stu-id="944fc-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="944fc-112">Aplicativos do Office</span><span class="sxs-lookup"><span data-stu-id="944fc-112">Office applications</span></span>

<span data-ttu-id="944fc-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span><span class="sxs-lookup"><span data-stu-id="944fc-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="944fc-115">OneDrive for Business Sync Client</span><span class="sxs-lookup"><span data-stu-id="944fc-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="944fc-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span><span class="sxs-lookup"><span data-stu-id="944fc-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="944fc-117">Inicializador de aplicativos do Office 365</span><span class="sxs-lookup"><span data-stu-id="944fc-117">Office 365 app launcher</span></span>

<span data-ttu-id="944fc-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span><span class="sxs-lookup"><span data-stu-id="944fc-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="944fc-120">Delve User profiles</span><span class="sxs-lookup"><span data-stu-id="944fc-120">Delve User profiles</span></span>

<span data-ttu-id="944fc-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span><span class="sxs-lookup"><span data-stu-id="944fc-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="944fc-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span><span class="sxs-lookup"><span data-stu-id="944fc-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="944fc-124">Delve</span><span class="sxs-lookup"><span data-stu-id="944fc-124">Delve</span></span>

<span data-ttu-id="944fc-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span><span class="sxs-lookup"><span data-stu-id="944fc-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="944fc-126">Pesquisa</span><span class="sxs-lookup"><span data-stu-id="944fc-126">Search</span></span>

<span data-ttu-id="944fc-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span><span class="sxs-lookup"><span data-stu-id="944fc-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="944fc-131">The following search clients are supported:</span><span class="sxs-lookup"><span data-stu-id="944fc-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="944fc-132">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="944fc-132">OneDrive for Business</span></span>

-   <span data-ttu-id="944fc-133">Delve</span><span class="sxs-lookup"><span data-stu-id="944fc-133">Delve</span></span>

-   <span data-ttu-id="944fc-134">SharePoint Home</span><span class="sxs-lookup"><span data-stu-id="944fc-134">SharePoint Home</span></span>

-   <span data-ttu-id="944fc-135">The Search Center</span><span class="sxs-lookup"><span data-stu-id="944fc-135">The Search Center</span></span>

-   <span data-ttu-id="944fc-136">Custom search applications that use the SharePoint Search API</span><span class="sxs-lookup"><span data-stu-id="944fc-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="944fc-137">OneDrive iOS and Android</span><span class="sxs-lookup"><span data-stu-id="944fc-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="944fc-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span><span class="sxs-lookup"><span data-stu-id="944fc-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="944fc-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span><span class="sxs-lookup"><span data-stu-id="944fc-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="944fc-142">Teams Experience</span><span class="sxs-lookup"><span data-stu-id="944fc-142">Teams Experience</span></span>

<span data-ttu-id="944fc-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span><span class="sxs-lookup"><span data-stu-id="944fc-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
