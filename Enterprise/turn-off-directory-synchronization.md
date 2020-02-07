---
title: Desativar a sincronização de diretório no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
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
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Saiba como usar o PowerShell para desativar a sincronização de diretório para o Office 365
ms.openlocfilehash: eab736241372b2d1b6023dc803dff540dded64ae
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841008"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="12cd1-103">Desativar a sincronização de diretório no Office 365</span><span class="sxs-lookup"><span data-stu-id="12cd1-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="12cd1-104">Você pode usar o PowerShell para desativar a sincronização de diretórios.</span><span class="sxs-lookup"><span data-stu-id="12cd1-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="12cd1-105">No entanto, não é recomendável que você desative a sincronização de diretório como uma etapa de solução de problemas.</span><span class="sxs-lookup"><span data-stu-id="12cd1-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="12cd1-106">Se precisar de ajuda para solucionar problemas de sincronização de diretórios, consulte o artigo [corrigindo problemas com a sincronização de diretórios para o Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="12cd1-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="12cd1-107">[Entre em contato com o suporte](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para produtos de negócios, se necessário.</span><span class="sxs-lookup"><span data-stu-id="12cd1-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="12cd1-108">Desativar a sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="12cd1-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="12cd1-109">Para desativar a sincronização de diretórios:</span><span class="sxs-lookup"><span data-stu-id="12cd1-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="12cd1-110">Primeiro, instale o software necessário e conecte-se à sua assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="12cd1-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="12cd1-111">Para obter instruções, consulte [conectar-se com o módulo Microsoft Azure Active Directory para Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="12cd1-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="12cd1-112">Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para desabilitar a sincronização de diretórios:</span><span class="sxs-lookup"><span data-stu-id="12cd1-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
