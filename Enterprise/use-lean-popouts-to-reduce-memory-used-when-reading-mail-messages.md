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
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Use popouts lean para reduzir a memória usada ao ler mensagens de email

Este artigo contém informações para melhorar o desempenho de download de mensagem no Outlook na web. Este artigo faz parte do projeto [de planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune) .
   
Como administrador global do Office 365, você pode configurar o Outlook na web para entregar *popouts lean* , um menor, menos a versão muita memória de determinadas mensagens de email no Microsoft Edge ou o Internet Explorer. Quando popouts lean são configurados para o Outlook na web, renderizado componentes do servidor são carregados que otimizar o desempenho. 
  
> [!NOTE]
> A partir de março de 2018, popouts lean atualmente não estão disponíveis para mensagens que especificam as restrições de direitos de uso, como o gerenciamento de direitos de informação (IRM). 
  
Esses recursos continuarão inserido na janela principal, mas não estão disponíveis no popouts lean:
  
- Complementos do Outlook
    
- Skype para presença de negócios
    
 **Para configurar lean popouts para todos os usuários dentro da sua organização do Office 365**
  
1. [Conecte-se ao Exchange Online usando o PowerShell remoto](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Execute o cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) com o parâmetro LeanPopoutEnabled da seguinte maneira: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    Por exemplo, para habilitar lean popouts para todos os usuários em sua organização:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    Para desabilitar lean popouts para todos os usuários em sua organização:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


