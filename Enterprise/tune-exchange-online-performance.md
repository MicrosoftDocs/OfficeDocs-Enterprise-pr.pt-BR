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
# <a name="tune-exchange-online-performance"></a>Ajuste o desempenho do Exchange Online

Este artigo contém dicas gerais e links para outros recursos que descrevem como melhorar o desempenho do Exchange Online. Este artigo faz parte do projeto [de planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune) .
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Fatores a serem considerados para melhorar o desempenho do Exchange Online

Para melhorar a velocidade de migração e reduzir as restrições de largura de banda da sua organização do Exchange Online, considere o seguinte:
  
- **Reduza os tamanhos de caixa de correio.** Caixas de correio menores melhoram a velocidade de migração. 
    
- **Use os recursos de movimentação da caixa de correio com uma implantação híbrida do Exchange.** Com uma implantação híbrida do Exchange, email offline (na forma de arquivos .OST) não é necessário fazer um novo download ao migrar para o Exchange Online. Isto reduz muito seus requisitos da largura de banda para download. 
    
- **Agende as movimentações de caixa de correio para períodos de pouco tráfego da Internet e baixo uso do Exchange local.** Ao agendar as movimentações, as solicitações de migração são enviadas para o proxy de replicação de caixa de correio e podem não ocorrer imediatamente. 
    
- **Usar popouts lean para Outlook na web.** Popouts lean menor, fornecem menos versões muita memória de determinadas mensagens de email no Microsoft Edge ou o Internet Explorer por alguns componentes no servidor de renderização. Para obter mais informações, consulte [popouts lean de uso para reduzir a memória usada ao ler mensagens de email](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).
    
Para obter mais informações sobre o desempenho de migração do Exchange, consulte [desempenho de migração do Office 365 e práticas recomendadas](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
  

