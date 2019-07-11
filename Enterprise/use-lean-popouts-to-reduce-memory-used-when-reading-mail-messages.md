---
title: Usar Lean pop-ups para reduzir a memória usada ao ler mensagens de email
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/8/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Este artigo contém informações para melhorar o desempenho de download de mensagens no Outlook na Web.
ms.openlocfilehash: a9070d9aefc8e4c223667848b4af5c06518de076
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616804"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="e4757-103">Usar Lean pop-ups para reduzir a memória usada ao ler mensagens de email</span><span class="sxs-lookup"><span data-stu-id="e4757-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="e4757-104">Este artigo contém informações para melhorar o desempenho de download de mensagens no Outlook na Web.</span><span class="sxs-lookup"><span data-stu-id="e4757-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="e4757-105">Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o projeto do Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="e4757-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="e4757-106">Como administrador global do Office 365, você pode configurar o Outlook na Web para fornecer *Lean pop-ups* , uma versão menor e menos intensa de memória de determinadas mensagens de email no Microsoft Edge ou no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e4757-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="e4757-107">Quando o Lean pop-ups é configurado para o Outlook na Web, os componentes renderizados no servidor são carregados que otimizam o desempenho.</span><span class="sxs-lookup"><span data-stu-id="e4757-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e4757-108">A partir de março de 2018, a Lean pop-ups não está disponível para mensagens que especificam restrições de direitos de uso, como gerenciamento de direitos de informação (IRM).</span><span class="sxs-lookup"><span data-stu-id="e4757-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="e4757-109">Esses recursos continuarão a funcionar na janela principal, mas não estão disponíveis no Lean pop-ups:</span><span class="sxs-lookup"><span data-stu-id="e4757-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="e4757-110">Suplementos do Outlook</span><span class="sxs-lookup"><span data-stu-id="e4757-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="e4757-111">Presença do Skype for Business</span><span class="sxs-lookup"><span data-stu-id="e4757-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="e4757-112">**Para configurar o Lean pop-ups para todos os usuários na sua organização do Office 365**</span><span class="sxs-lookup"><span data-stu-id="e4757-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="e4757-113">[Conecte-se ao Exchange Online usando o PowerShell remoto](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="e4757-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="e4757-114">Execute o cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) com o parâmetro LeanPopoutEnabled da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e4757-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="e4757-115">Por exemplo, para habilitar o Lean pop-ups para todos os usuários em sua organização:</span><span class="sxs-lookup"><span data-stu-id="e4757-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="e4757-116">Para desabilitar o Lean pop-ups para todos os usuários em sua organização:</span><span class="sxs-lookup"><span data-stu-id="e4757-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


