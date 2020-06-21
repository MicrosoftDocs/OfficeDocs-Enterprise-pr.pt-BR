---
title: Log de transações do Microsoft 365 IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Fornece um exemplo e descreve a Convenção de nomenclatura e o nível de log padrão do log de transações do Microsoft 365 IdFix.
ms.openlocfilehash: 199d765d640a30fa163f74e6b6029b228b41a63d
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774506"
---
# <a name="microsoft-365-idfix-transaction-log"></a><span data-ttu-id="b18ba-103">Log de transações do Microsoft 365 IdFix</span><span class="sxs-lookup"><span data-stu-id="b18ba-103">Microsoft 365 IdFix transaction log</span></span>

<span data-ttu-id="b18ba-104">*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="b18ba-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b18ba-105">Fornece um exemplo e descreve a Convenção de nomenclatura e o nível de log padrão do log de transações do Microsoft 365 IdFix.</span><span class="sxs-lookup"><span data-stu-id="b18ba-105">Provides an example and describes the naming convention and default log level of the Microsoft 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="b18ba-106">Local do log de transações do IdFix</span><span class="sxs-lookup"><span data-stu-id="b18ba-106">IdFix transaction log location</span></span>

<span data-ttu-id="b18ba-107">A ferramenta Microsoft 365 IdFix cria um novo log de transações cada vez que você clica em **aplicar** no IdFix e aplica as alterações à floresta do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b18ba-107">The Microsoft 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="b18ba-108">O log de transações é salvo na mesma pasta onde você instalou o IdFix.</span><span class="sxs-lookup"><span data-stu-id="b18ba-108">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="b18ba-109">Por padrão, essa pasta é C:\Deployment Tools\IDFix.</span><span class="sxs-lookup"><span data-stu-id="b18ba-109">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="b18ba-110">O nome do arquivo de log de transações usa um formato de carimbo de data e hora, por exemplo, Verbose 6-1-2018 6-17-22 PM indica um arquivo que foi gerado em 1º de junho de 2018 às 6:17:22 PM.</span><span class="sxs-lookup"><span data-stu-id="b18ba-110">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="b18ba-111">Verbose indica o nível de log.</span><span class="sxs-lookup"><span data-stu-id="b18ba-111">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="b18ba-112">Nível de log do log de transações do IdFix</span><span class="sxs-lookup"><span data-stu-id="b18ba-112">IdFix transaction log logging level</span></span>

<span data-ttu-id="b18ba-113">A palavra Verbose no nome do arquivo de log de transações indica o nível de log no arquivo.</span><span class="sxs-lookup"><span data-stu-id="b18ba-113">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="b18ba-114">Verbose significa que a quantidade máxima de informações é capturada no log.</span><span class="sxs-lookup"><span data-stu-id="b18ba-114">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="b18ba-115">Este é o nível de log padrão.</span><span class="sxs-lookup"><span data-stu-id="b18ba-115">This is the default logging level.</span></span> <span data-ttu-id="b18ba-116">No momento, não é possível alterar o nível de log.</span><span class="sxs-lookup"><span data-stu-id="b18ba-116">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="b18ba-117">Formato de log de transações do IdFix</span><span class="sxs-lookup"><span data-stu-id="b18ba-117">IdFix transaction log format</span></span>

<span data-ttu-id="b18ba-118">O IdFix grava os resultados de cada ação de **atualização** em um log de transações, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b18ba-118">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
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