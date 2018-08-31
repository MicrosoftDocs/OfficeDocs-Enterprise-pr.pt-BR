---
title: Desativar a sincronização de diretório do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Aprenda a usar o PowerShell para desativar a sincronização de diretórios para o Office 365
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539371"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Desativar a sincronização de diretório do Office 365
Você pode usar o PowerShell para desativar a sincronização de diretórios. No entanto, não é recomendável que você desative a sincronização de diretórios, como uma etapa de solução de problemas. Se precisar de ajuda para solucionar problemas de sincronização de diretórios, consulte o artigo [Corrigindo problemas com a sincronização de diretório para o Office 365](fix-problems-with-directory-synchronization.md) . 
  
Para [contatar o suporte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para produtos de negócios, se necessário.
  
## <a name="turn-off-directory-synchronization"></a>Desativar a sincronização de diretórios  
Para desativar a sincronização de diretórios:
  
1. Primeiro, instale os softwares necessários e se conectar à sua assinatura do Office 365. Para obter instruções para ambos, consulte [conectar-se ao Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para desabilitar a sincronização de diretórios: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```