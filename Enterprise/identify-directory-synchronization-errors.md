---
title: Exibir erros de sincronização de diretórios no Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Saiba como exibir erros de sincronização de diretório no Centro de administração do Office 365.
ms.openlocfilehash: 8beeeebbb24936abd7c93f4c04c0fa4e27c85c12
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327333"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="0772e-103">Exibir erros de sincronização de diretórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="0772e-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="0772e-p101">Você pode exibir erros de sincronização de diretório no Centro de administração do Office 365. Somente os erros de objeto de usuário são exibidos. Para exibir erros usando o PowerShell, consulte [objetos de identidade com DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="0772e-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="0772e-107">Depois de exibição, consulte [Corrigindo problemas com a sincronização de diretório para o Office 365](fix-problems-with-directory-synchronization.md) para corrigir os problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="0772e-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="0772e-108">Exibir erros de sincronização de diretório no Centro de administração</span><span class="sxs-lookup"><span data-stu-id="0772e-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="0772e-109">Para exibir quaisquer erros no Centro de administração:</span><span class="sxs-lookup"><span data-stu-id="0772e-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="0772e-110">Entre no Office 365 com a sua conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="0772e-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="0772e-111">Vá para o [Centro de administração sobre o Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="0772e-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="0772e-112">Na página **inicial** do, você verá a **Status do DirSync** lado a lado.</span><span class="sxs-lookup"><span data-stu-id="0772e-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![O Status de DirSync lado a lado no modo de visualização admin center](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="0772e-114">Na organização lado o lado, escolha **DirSync Status** para ir para a página **Status da sincronização de diretório** .</span><span class="sxs-lookup"><span data-stu-id="0772e-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="0772e-115">Na parte inferior da página, você pode ver se há erros de DirSync.</span><span class="sxs-lookup"><span data-stu-id="0772e-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![Na página Status da sincronização de diretório, você pode ver se há erros de objeto do DirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="0772e-117">Escolha **encontramos DirSync erros de objeto** para ir para uma exibição detalhada dos erros de sincronização de diretório.</span><span class="sxs-lookup"><span data-stu-id="0772e-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="0772e-118">Você também pode ir à página **DirSync erros** se você escolher **encontramos DirSync erros de objetos** no lado a lado **status de DirSync** .</span><span class="sxs-lookup"><span data-stu-id="0772e-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Página de erros de DirSync](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="0772e-120">Na página **DirSync erros** , escolha qualquer um dos erros listados para exibir o painel de detalhes, com informações sobre o erro e dicas sobre como corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="0772e-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
