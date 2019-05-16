---
title: Desativar a sincronização de diretório no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Saiba como usar o PowerShell para desativar a sincronização de diretório para o Office 365
ms.openlocfilehash: 83a01d827217db141016f622a2cb417f93f88e76
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070357"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Desativar a sincronização de diretório no Office 365
Você pode usar o PowerShell para desativar a sincronização de diretórios. No entanto, não é recomendável que você desative a sincronização de diretório como uma etapa de solução de problemas. Se precisar de ajuda para solucionar problemas de sincronização de diretórios, consulte o artigo [corrigindo problemas com a sincronização de diretórios para o Office 365](fix-problems-with-directory-synchronization.md) . 
  
[Entre em contato com o suporte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para produtos de negócios, se necessário.
  
## <a name="turn-off-directory-synchronization"></a>Desativar a sincronização de diretórios  
Para desativar a sincronização de diretórios:
  
1. Primeiro, instale o software necessário e conecte-se à sua assinatura do Office 365. Para obter instruções para ambos, consulte [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para desabilitar a sincronização de diretórios: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```