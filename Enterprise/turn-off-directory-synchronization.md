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
ms.openlocfilehash: efee8b216d63f32ac64a559aca3bcb55b0a933c1
ms.sourcegitcommit: 3ed7b1eacf009581a9897524c181afa3e555ad3f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "41570888"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="228d7-103">Desativar a sincronização de diretório no Office 365</span><span class="sxs-lookup"><span data-stu-id="228d7-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="228d7-104">Você pode usar o PowerShell para desativar a sincronização de diretórios.</span><span class="sxs-lookup"><span data-stu-id="228d7-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="228d7-105">No entanto, não é recomendável que você desative a sincronização de diretório como uma etapa de solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="228d7-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="228d7-106">Se precisar de ajuda para solucionar problemas de sincronização de diretórios, consulte o artigo [corrigindo problemas com a sincronização de diretórios para o Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="228d7-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="228d7-107">[Entre em contato com o suporte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para produtos de negócios, se necessário.</span><span class="sxs-lookup"><span data-stu-id="228d7-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="228d7-108">Desativar a sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="228d7-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="228d7-109">Para desativar a sincronização de diretórios:</span><span class="sxs-lookup"><span data-stu-id="228d7-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="228d7-110">Primeiro, instale o software necessário e conecte-se à sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="228d7-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="228d7-111">Para obter instruções, consulte [conectar-se com o módulo Microsoft Azure Active Directory para Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="228d7-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="228d7-112">Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para desabilitar a sincronização de diretórios:</span><span class="sxs-lookup"><span data-stu-id="228d7-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
