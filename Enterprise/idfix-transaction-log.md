---
title: Log de transações IdFix do Office 365
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
ms.openlocfilehash: 22ea5af87b1bbcaa96f88e3746a50f1411a01b9a
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813419"
---
# <a name="office-365-idfix-transaction-log"></a>Log de transações IdFix do Office 365

*Esse artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*

Fornece um exemplo e descreve a Convenção de nomenclatura e o nível de log padrão do log de transações do IdFix do Office 365.
  
## <a name="idfix-transaction-log-location"></a>Local do log de transações do IdFix

A ferramenta IdFix do Office 365 cria um novo log de transações cada vez que você clica em **aplicar** no IdFix e aplica as alterações à floresta do Active Directory. O log de transações é salvo na mesma pasta onde você instalou o IdFix. Por padrão, essa pasta é C:\Deployment Tools\IDFix. O nome do arquivo de log de transações usa um formato de carimbo de data e hora, por exemplo, Verbose 6-1-2018 6-17-22 PM indica um arquivo que foi gerado em 1º de junho de 2018 às 6:17:22 PM. Verbose indica o nível de log. 
  
## <a name="idfix-transaction-log-logging-level"></a>Nível de log do log de transações do IdFix

A palavra Verbose no nome do arquivo de log de transações indica o nível de log no arquivo. Verbose significa que a quantidade máxima de informações é capturada no log. Este é o nível de log padrão. No momento, não é possível alterar o nível de log.
  
## <a name="idfix-transaction-log-format"></a>Formato de log de transações do IdFix

O IdFix grava os resultados de cada ação de **atualização** em um log de transações, conforme mostrado no exemplo a seguir:
  
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