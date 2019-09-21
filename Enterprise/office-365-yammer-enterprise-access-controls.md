---
title: Controles de acesso corporativo do Office 365 Yammer
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Resumo: um breve resumo sobre os controles de acesso corporativo do Yammer no ambiente de produção.'
ms.openlocfilehash: 19910ec0771b3034e7a290190ae7045ffc8651cf
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067152"
---
# <a name="yammer-enterprise-access-controls"></a>Controles de acesso do Yammer Enterprise 

O acesso físico e lógico ao ambiente de produção do Yammer é restrito a um pequeno conjunto de pessoas (infraestrutura e operações). Como em outros engenheiros do Office 365, os engenheiros do Yammer têm zero acesso à dados dos clientes. O acesso deve ser solicitado usando um sistema de controle de acesso just-in-time baseado em aprovação semelhante ao Lockbox com um número limitado de aprovadores. Os aprovadores verificam a solicitação (por exemplo, eles verificam se a solicitação é legítima com base em necessidade, caso de negócios, hora etc.) e, em seguida, aprovar ou negar a solicitação. Se a solicitação for aprovada, o acesso JIT será concedido para um tempo definido e limitado. Após o tempo de acesso ser excedido, o acesso expira automaticamente.

Como em outros serviços do Office 365, todo o acesso ao ambiente de produção do Yammer usa a autenticação multifator. Todos os acessos e o histórico de comandos são atribuídos a um usuário e registrados e revisados regularmente pela equipe de segurança do Yammer.

Para obter mais informações sobre administração e gerenciamento do Yammer, consulte [ajuda do administrador do Yammer](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).