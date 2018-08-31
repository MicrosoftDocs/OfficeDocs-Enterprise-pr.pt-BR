---
title: Use popouts lean para reduzir a memória usada ao ler mensagens de email
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Este artigo contém informações para melhorar o desempenho de download de mensagem no Outlook na web.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539213"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="93e1b-103">Use popouts lean para reduzir a memória usada ao ler mensagens de email</span><span class="sxs-lookup"><span data-stu-id="93e1b-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="93e1b-p101">Este artigo contém informações para melhorar o desempenho de download de mensagem no Outlook na web. Este artigo faz parte do projeto [de planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="93e1b-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="93e1b-p102">Como administrador global do Office 365, você pode configurar o Outlook na web para entregar *popouts lean* , um menor, menos a versão muita memória de determinadas mensagens de email no Microsoft Edge ou o Internet Explorer. Quando popouts lean são configurados para o Outlook na web, renderizado componentes do servidor são carregados que otimizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="93e1b-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="93e1b-108">A partir de março de 2018, popouts lean atualmente não estão disponíveis para mensagens que especificam as restrições de direitos de uso, como o gerenciamento de direitos de informação (IRM).</span><span class="sxs-lookup"><span data-stu-id="93e1b-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="93e1b-109">Esses recursos continuarão inserido na janela principal, mas não estão disponíveis no popouts lean:</span><span class="sxs-lookup"><span data-stu-id="93e1b-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="93e1b-110">Complementos do Outlook</span><span class="sxs-lookup"><span data-stu-id="93e1b-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="93e1b-111">Skype para presença de negócios</span><span class="sxs-lookup"><span data-stu-id="93e1b-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="93e1b-112">**Para configurar lean popouts para todos os usuários dentro da sua organização do Office 365**</span><span class="sxs-lookup"><span data-stu-id="93e1b-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="93e1b-113">[Conecte-se ao Exchange Online usando o PowerShell remoto](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="93e1b-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="93e1b-114">Execute o cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) com o parâmetro LeanPopoutEnabled da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="93e1b-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="93e1b-115">Por exemplo, para habilitar lean popouts para todos os usuários em sua organização:</span><span class="sxs-lookup"><span data-stu-id="93e1b-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="93e1b-116">Para desabilitar lean popouts para todos os usuários em sua organização:</span><span class="sxs-lookup"><span data-stu-id="93e1b-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


