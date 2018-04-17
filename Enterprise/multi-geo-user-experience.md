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
# <a name="user-experience-in-a-multi-geo-environment"></a>User experience in a multi-geo environment

Here’s what your users will see in a OneDrive Multi-Geo configuration:

#### <a name="users-onedrive-for-business-location"></a>User’s OneDrive for Business location

Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.

#### <a name="sharing"></a>Compartilhamento

The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.

#### <a name="office-applications"></a>Aplicativos do Office

Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.

#### <a name="onedrive-for-business-sync-client"></a>OneDrive for Business Sync Client

The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.

#### <a name="office-365-app-launcher"></a>Inicializador de aplicativos do Office 365

The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.

#### <a name="delve-user-profiles"></a>Delve User profiles

User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.

If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.

#### <a name="delve"></a>Delve

For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.

#### <a name="search"></a>Pesquisa

Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.

The following search clients are supported:

-   OneDrive for Business

-   Delve

-   SharePoint Home

-   The Search Center

-   Custom search applications that use the SharePoint Search API

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS and Android 

The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.

See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.

#### <a name="teams-experience"></a>Teams Experience

Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.
