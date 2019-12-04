---
title: Usar Lean pop-ups para reduzir a memória usada ao ler mensagens de email
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Este artigo contém informações para melhorar o desempenho de download de mensagens no Outlook na Web.
ms.openlocfilehash: 8437cde7ec2afa091ad1881a8cfc0d77f783d819
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814579"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="97660-103">Usar Lean pop-ups para reduzir a memória usada ao ler mensagens de email</span><span class="sxs-lookup"><span data-stu-id="97660-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="97660-104">Este artigo contém informações para melhorar o desempenho de download de mensagens no Outlook na Web.</span><span class="sxs-lookup"><span data-stu-id="97660-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="97660-105">Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o projeto do Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="97660-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
  
<span data-ttu-id="97660-106">Como administrador global do Office 365, você pode configurar o Outlook na Web para fornecer _Lean pop-ups_, uma versão menor e menos intensa de memória de determinadas mensagens de email no Microsoft Edge ou no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="97660-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver _lean popouts_, a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="97660-107">Quando o Lean pop-ups é configurado para o Outlook na Web, os componentes renderizados no servidor são carregados que otimizam o desempenho.</span><span class="sxs-lookup"><span data-stu-id="97660-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span>
  
> [!NOTE]
> <span data-ttu-id="97660-108">A partir de março de 2018, Lean pop-ups não estão disponíveis para mensagens que especificam restrições de direitos de uso, como gerenciamento de direitos de informação (IRM).</span><span class="sxs-lookup"><span data-stu-id="97660-108">As of March 2018, lean popouts are not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span>
  
<span data-ttu-id="97660-109">Esses recursos continuarão a funcionar na janela principal, mas não estão disponíveis no Lean pop-ups:</span><span class="sxs-lookup"><span data-stu-id="97660-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="97660-110">Suplementos do Outlook</span><span class="sxs-lookup"><span data-stu-id="97660-110">Outlook add-ins</span></span>
  
- <span data-ttu-id="97660-111">Presença do Skype for Business</span><span class="sxs-lookup"><span data-stu-id="97660-111">Skype for Business presence</span></span>
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a><span data-ttu-id="97660-112">Para configurar o Lean pop-ups para todos os usuários na sua organização do Office 365</span><span class="sxs-lookup"><span data-stu-id="97660-112">To configure lean popouts for all users within your Office 365 organization</span></span>
  
1. <span data-ttu-id="97660-113">[Conecte-se ao Exchange Online usando o PowerShell remoto](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="97660-113">[Connect to Exchange Online Using Remote PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
  
2. <span data-ttu-id="97660-114">Execute o cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) com o parâmetro LeanPopoutEnabled da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="97660-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span>

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="97660-115">Por exemplo, para habilitar o Lean pop-ups para todos os usuários em sua organização:</span><span class="sxs-lookup"><span data-stu-id="97660-115">For example, to enable lean popouts for all users in your organization:</span></span>
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="97660-116">Para desabilitar o Lean pop-ups para todos os usuários em sua organização:</span><span class="sxs-lookup"><span data-stu-id="97660-116">To disable lean popouts for all users in your organization:</span></span>

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
