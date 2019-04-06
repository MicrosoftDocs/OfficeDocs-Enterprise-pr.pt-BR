---
title: Exibir erros de sincronização de diretório no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Saiba como exibir os erros de sincronização de diretório no centro de administração do Microsoft 365.
ms.openlocfilehash: 8450c2e26c9c9ae194be46d81018a20c91e35f29
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001804"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="b084a-103">Exibir erros de sincronização de diretório no Office 365</span><span class="sxs-lookup"><span data-stu-id="b084a-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="b084a-104">Você pode exibir os erros de sincronização de diretório no [centro de administração do Microsoft 365](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="b084a-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="b084a-105">Somente os erros de objeto do usuário são exibidos.</span><span class="sxs-lookup"><span data-stu-id="b084a-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="b084a-106">Para exibir erros usando o PowerShell, consulte [identificar objetos com DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="b084a-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="b084a-107">Após a exibição, confira [corrigir problemas de sincronização de diretório para o Office 365](fix-problems-with-directory-synchronization.md) para corrigir quaisquer problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="b084a-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="b084a-108">Exibir erros de sincronização de diretório no centro de administração</span><span class="sxs-lookup"><span data-stu-id="b084a-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="b084a-109">Para exibir qualquer erro no centro de administração:</span><span class="sxs-lookup"><span data-stu-id="b084a-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="b084a-110">Entre no Office 365 com uma conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="b084a-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="b084a-111">Vá até o [centro de administração](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="b084a-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="b084a-112">Na **Home** Page, você verá o bloco **status DirSync** .</span><span class="sxs-lookup"><span data-stu-id="b084a-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![O bloco de status dirSync na visualização do centro de administração](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="b084a-114">No bloco, escolha **status DirSync** para ir para a página **status de sincronização de diretório** .</span><span class="sxs-lookup"><span data-stu-id="b084a-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="b084a-115">Na parte inferior da página, você pode ver se há erros dirSync.</span><span class="sxs-lookup"><span data-stu-id="b084a-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Na página status de sincronização de diretório, você pode ver se há erros de objeto dirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="b084a-117">Escolha encontramos **erros de objeto DirSync** para ir para um modo de exibição detalhado dos erros de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="b084a-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="b084a-118">Você também pode acessar a página **erros DirSync** se escolher erros de **objeto DirSync** no bloco de **status DirSync** .</span><span class="sxs-lookup"><span data-stu-id="b084a-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Página de erros dirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="b084a-120">Na página **erros DirSync** , escolha qualquer um dos erros listados para exibir o painel de detalhes com informações sobre o erro e dicas sobre como corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="b084a-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
