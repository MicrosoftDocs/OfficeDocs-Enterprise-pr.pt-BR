---
title: Exibir erros de sincronização de diretório no Microsoft 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Saiba como exibir os erros de sincronização de diretório no centro de administração do Microsoft 365.
ms.openlocfilehash: 57ca9ce125679931adcca93621474cec9ee9b82f
ms.sourcegitcommit: 3349fdaff646f5f7d92c22565402dfc22c12d2ed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2020
ms.locfileid: "44842063"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="c6d48-103">Exibir erros de sincronização de diretório no Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c6d48-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="c6d48-104">Você pode exibir os erros de sincronização de diretório no centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c6d48-104">You can view directory synchronization errors in the Microsoft 365 admin center.</span></span> <span data-ttu-id="c6d48-105">Somente os erros de objeto do usuário são exibidos.</span><span class="sxs-lookup"><span data-stu-id="c6d48-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="c6d48-106">Para exibir erros com o PowerShell, confira [identificar objetos com o DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="c6d48-106">To view errors with PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a><span data-ttu-id="c6d48-107">Exibir erros de sincronização de diretório no centro de administração do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c6d48-107">View directory synchronization errors in the Microsoft 365 admin center</span></span>

<span data-ttu-id="c6d48-108">Para exibir qualquer erro no centro de administração do Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="c6d48-108">To view any errors in the Microsoft 365 admin center:</span></span>
  
1. <span data-ttu-id="c6d48-109">Entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com) com uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c6d48-109">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with a global administrator account.</span></span> 
    
2. <span data-ttu-id="c6d48-110">Na **Home** Page, você verá o cartão de **Gerenciamento de usuários** .</span><span class="sxs-lookup"><span data-stu-id="c6d48-110">On the **Home** page, you'll see the **User management** card.</span></span> 
    
    ![A placa de gerenciamento de usuário no centro de administração do Microsoft 365](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. <span data-ttu-id="c6d48-112">No cartão, escolha **erros de sincronização** no **Azure ad Connect** para ver os erros na página **erros de sincronização de diretório** .</span><span class="sxs-lookup"><span data-stu-id="c6d48-112">On the card, choose **Sync errors** under **Azure AD Connect** to see the errors on the **Directory sync errors** page.</span></span>   
    
    ![Um exemplo da página de erros de sincronização de diretório](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. <span data-ttu-id="c6d48-114">Escolha qualquer um dos erros para exibir o painel de detalhes com informações sobre o erro e dicas sobre como corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="c6d48-114">Choose any of the errors to display the details pane with information about the error and tips on how to fix it.</span></span>

   ![Exemplo de detalhes de um erro de sincronização de diretório](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
<span data-ttu-id="c6d48-116">Após a exibição, confira [corrigir problemas de sincronização de diretório para o Microsoft 365](fix-problems-with-directory-synchronization.md) para corrigir quaisquer problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="c6d48-116">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>

