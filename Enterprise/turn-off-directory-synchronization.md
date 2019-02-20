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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Saiba como usar o PowerShell para desativar a sincronização de diretório para o Office 365
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085070"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Desativar a sincronização de diretório do Office 365
Você pode usar o PowerShell para desativar a sincronização de diretórios. No enTanto, não é recomendável que você desative a sincronização de diretório como uma etapa de solução de problemas. Se precisar de ajuda para solucionar problemas de sincronização de diretórios, consulte o artigo [corrigindo problemas com a sincronização de diretórios para o Office 365](fix-problems-with-directory-synchronization.md) . 
  
[Entre em contato com o suporte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para produtos de negócios, se necessário.
  
## <a name="turn-off-directory-synchronization"></a>Desativar a sincronização de diretórios  
Para desativar a sincronização de diretórios:
  
1. Primeiro, instale o software necessário e conecte-se à sua assinatura do Office 365. Para obter instruções para ambos, consulte [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para desabilitar a sincronização de diretórios: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```