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
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Usar Lean pop-ups para reduzir a memória usada ao ler mensagens de email

Este artigo contém informações para melhorar o desempenho de download de mensagens no Outlook na Web. Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o projeto do Office 365](https://aka.ms/tune) .
   
Como administrador global do Office 365, você pode configurar o Outlook na Web para fornecer *Lean pop-ups* , uma versão menor e menos intensa de memória de determinadas mensagens de email no Microsoft Edge ou no Internet Explorer. Quando o Lean pop-ups é configurado para o Outlook na Web, os componentes renderizados no servidor são carregados que otimizam o desempenho. 
  
> [!NOTE]
> A partir de março de 2018, a Lean pop-ups não está disponível para mensagens que especificam restrições de direitos de uso, como gerenciamento de direitos de informação (IRM). 
  
Esses recursos continuarão a funcionar na janela principal, mas não estão disponíveis no Lean pop-ups:
  
- Suplementos do Outlook
    
- Presença do Skype for Business
    
 **Para configurar o Lean pop-ups para todos os usuários na sua organização do Office 365**
  
1. [Conecte-se ao Exchange Online usando o PowerShell remoto](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).
    
2. Execute o cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) com o parâmetro LeanPopoutEnabled da seguinte maneira: 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Por exemplo, para habilitar o Lean pop-ups para todos os usuários em sua organização:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Para desabilitar o Lean pop-ups para todos os usuários em sua organização:
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


