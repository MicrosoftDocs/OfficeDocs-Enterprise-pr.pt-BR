---
title: Log de transações do IdFix do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Fornece um exemplo e descreve a Convenção de nomenclatura e o nível de log padrão do log de transações do IdFix do Office 365.
ms.openlocfilehash: 0c6f2dd64cb406681c0a98099b2a42887ee79c25
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067257"
---
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="710cb-103">Log de transações do IdFix do Office 365</span><span class="sxs-lookup"><span data-stu-id="710cb-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="710cb-104">Fornece um exemplo e descreve a Convenção de nomenclatura e o nível de log padrão do log de transações do IdFix do Office 365.</span><span class="sxs-lookup"><span data-stu-id="710cb-104">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="710cb-105">Local do log de transações do IdFix</span><span class="sxs-lookup"><span data-stu-id="710cb-105">IdFix transaction log location</span></span>

<span data-ttu-id="710cb-106">A ferramenta IdFix do Office 365 cria um novo log de transações cada vez que você clica em **aplicar** no IdFix e aplica as alterações à floresta do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="710cb-106">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="710cb-107">O log de transações é salvo na mesma pasta onde você instalou o IdFix.</span><span class="sxs-lookup"><span data-stu-id="710cb-107">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="710cb-108">Por padrão, essa pasta é C:\Deployment Tools\IDFix.</span><span class="sxs-lookup"><span data-stu-id="710cb-108">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="710cb-109">O nome do arquivo de log de transações usa um formato de carimbo de data e hora, por exemplo, Verbose 6-1-2018 6-17-22 PM indica um arquivo que foi gerado em 1º de junho de 2018 às 6:17:22 PM.</span><span class="sxs-lookup"><span data-stu-id="710cb-109">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="710cb-110">Verbose indica o nível de log.</span><span class="sxs-lookup"><span data-stu-id="710cb-110">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="710cb-111">Nível de log do log de transações do IdFix</span><span class="sxs-lookup"><span data-stu-id="710cb-111">IdFix transaction log logging level</span></span>

<span data-ttu-id="710cb-112">A palavra Verbose no nome do arquivo de log de transações indica o nível de log no arquivo.</span><span class="sxs-lookup"><span data-stu-id="710cb-112">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="710cb-113">Verbose significa que a quantidade máxima de informações é capturada no log.</span><span class="sxs-lookup"><span data-stu-id="710cb-113">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="710cb-114">Este é o nível de log padrão.</span><span class="sxs-lookup"><span data-stu-id="710cb-114">This is the default logging level.</span></span> <span data-ttu-id="710cb-115">No momento, não é possível alterar o nível de log.</span><span class="sxs-lookup"><span data-stu-id="710cb-115">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="710cb-116">Formato de log de transações do IdFix</span><span class="sxs-lookup"><span data-stu-id="710cb-116">IdFix transaction log format</span></span>

<span data-ttu-id="710cb-117">O IdFix grava os resultados de cada ação de **atualização** em um log de transações, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="710cb-117">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```