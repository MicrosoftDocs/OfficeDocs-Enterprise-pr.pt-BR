---
title: Ajuste o desempenho do Exchange Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Este artigo contém dicas gerais e links para outros recursos que descrevem como melhorar o desempenho do Exchange Online.
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539503"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="d9798-103">Ajuste o desempenho do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d9798-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="d9798-p101">Este artigo contém dicas gerais e links para outros recursos que descrevem como melhorar o desempenho do Exchange Online. Este artigo faz parte do projeto [de planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="d9798-p101">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="d9798-106">Fatores a serem considerados para melhorar o desempenho do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d9798-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="d9798-107">Para melhorar a velocidade de migração e reduzir as restrições de largura de banda da sua organização do Exchange Online, considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9798-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="d9798-p102">**Reduza os tamanhos de caixa de correio.** Caixas de correio menores melhoram a velocidade de migração.</span><span class="sxs-lookup"><span data-stu-id="d9798-p102">**Reduce mailbox sizes.** Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="d9798-p103">**Use os recursos de movimentação da caixa de correio com uma implantação híbrida do Exchange.** Com uma implantação híbrida do Exchange, email offline (na forma de arquivos .OST) não é necessário fazer um novo download ao migrar para o Exchange Online. Isto reduz muito seus requisitos da largura de banda para download.</span><span class="sxs-lookup"><span data-stu-id="d9798-p103">**Use the mailbox move capabilities with an Exchange hybrid deployment.** With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online. This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="d9798-p104">**Agende as movimentações de caixa de correio para períodos de pouco tráfego da Internet e baixo uso do Exchange local.** Ao agendar as movimentações, as solicitações de migração são enviadas para o proxy de replicação de caixa de correio e podem não ocorrer imediatamente.</span><span class="sxs-lookup"><span data-stu-id="d9798-p104">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.** When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="d9798-p105">**Usar popouts lean para Outlook na web.** Popouts lean menor, fornecem menos versões muita memória de determinadas mensagens de email no Microsoft Edge ou o Internet Explorer por alguns componentes no servidor de renderização. Para obter mais informações, consulte [popouts lean de uso para reduzir a memória usada ao ler mensagens de email](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span><span class="sxs-lookup"><span data-stu-id="d9798-p105">**Use lean popouts for Outlook on the web.** Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server. For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>
    
<span data-ttu-id="d9798-118">Para obter mais informações sobre o desempenho de migração do Exchange, consulte [desempenho de migração do Office 365 e práticas recomendadas](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span><span class="sxs-lookup"><span data-stu-id="d9798-118">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

