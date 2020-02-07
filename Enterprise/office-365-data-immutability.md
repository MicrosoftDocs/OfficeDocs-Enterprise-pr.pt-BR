---
title: Imutabilidade dos dados do Office 365
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
f1.keywords:
- NOCSH
description: Define e explica a imutabilidade dos dados no Office 365.
ms.openlocfilehash: 8e52d1be87bff163b2d1cfc9233de08861104681
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844512"
---
# <a name="immutability-in-office-365"></a>Imutabilidade no Office 365

Conformidade normativa, requisitos de governança interna ou riscos de litígio exigem que as organizações preservem email e dados associados em um formulário detectável. Todos os dados no sistema devem ser detectáveis e nenhum deles pode ser destruído ou alterado. O termo padrão do setor para isso é "imutabilidade".

Os métodos tradicionais de imutabilidade geralmente funcionam movendo mensagens de email para um local de armazenamento separado e somente leitura. Embora esses sistemas atendam à finalidade de preservar itens de caixa de correio para descoberta, eles geralmente afetam a experiência do usuário removendo itens preservados do fluxo de trabalho diário personalizado. Para profissionais de ti, esta abordagem de imutabilidade requer a implantação e a manutenção contínua de um servidor separado e uma infraestrutura de armazenamento. A descoberta é realizada com ferramentas externas ao sistema de email e inclui custos associados de implantação e manutenção.

Com os recursos de política de retenção e preservação in-loco do arquivamento no Office 365 e seus serviços, você pode preservar e reter várias classes de dados de entrada, internos e de saída. Isso inclui:

- Comunicações de email de entrada e saída
- Manuais e registros contidos no formulário de email ou em documentos online compartilhados
- Solicitações de reunião
- Fax
- Mensagens instantâneas
- Documentos compartilhados durante reuniões online
- Caixa postal

Além disso, a Microsoft desenvolveu recursos complementares para permitir o [arquivamento de dados](https://support.office.com/article/Archiving-third-party-data-in-Office-365-0ce338d5-3666-4a18-86ab-c6910ff408cc) de outras fontes por meio da integração com soluções de captura e gerenciamento de dados de terceiros. Após a importação dos dados de terceiros, é possível aplicar recursos de conformidade do Office 365 aos dados, incluindo:

- [Retenção de litígio](https://docs.microsoft.com/microsoft-365/compliance/create-a-litigation-hold)
- [Descoberta eletrônica in-loco e retenção](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)
- [Pesquisa de Conformidade](https://docs.microsoft.com/microsoft-365/compliance/search-for-content)
- [Arquivamento no Local](https://docs.microsoft.com/microsoft-365/compliance/enable-archive-mailboxes)
- [Auditoria de caixa de correio](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing)
- [Políticas de retenção](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)

Por exemplo, quando uma caixa de correio é colocada em retenção de litígio, os dados de terceiros são preservados. Você pode pesquisar dados de terceiros usando a descoberta eletrônica in-loco ou a pesquisa de conformidade. Ou você pode aplicar políticas de arquivamento e retenção a dados de terceiros, da mesma forma que você pode para os dados da Microsoft. O arquivamento de dados de terceiros no Office 365 ajuda sua organização a manter-se em conformidade com as políticas governamentais e regulamentares.

O arquivamento no Office 365 fornece um armazenamento compatível com as regras de Securities-4 e a interrupções do Exchange (seg). O Office 365 preserva arquivos permanentes de todos os dados coletados em um formato não-regravável e não apagável usando políticas de retenção e políticas de preservação in-loco, incluindo bloqueio de preservação.

Especificamente:

- Todos os registros armazenados usando as políticas de retenção mencionadas acima são mantidos em uma área de armazenamento dedicada fora do âmbito do usuário comum. Somente os usuários autorizados podem acessar e Pesquisar esses registros, mas não podem alterá-los ou apagá-los.
- Os metadados de cada item incluem um carimbo de data/hora usado no cálculo da duração da retenção. Os carimbos de data/hora são aplicados quando um novo item é recebido ou criado e não pode ser modificado ou removido dos metadados.
- O arquivamento no Office 365 permite aos usuários combinar diferentes políticas de retenção e ações de bloqueio para criar políticas de retenção granulares. Essas políticas definem o tipo ou o local dos itens preservados e a duração da preservação.
- O recurso de bloqueio de preservação permite que os usuários escolham se desejam tornar a política uma política restritiva. Uma política restritiva proíbe que qualquer pessoa tenha a capacidade de remover, desabilitar ou fazer qualquer alteração na política de retenção. Isso significa que, quando o bloqueio de preservação estiver habilitado, ele não poderá ser desabilitado, e nenhum mecanismo existirá sob o qual qualquer dado dos responsáveis existentes que foram coletados pelas políticas de retenção em vigor poderá ser substituído, modificado, apagado ou excluído durante o período de preservação. Além disso, o período de retenção definido pelo bloqueio de preservação não pode ser reduzido ou reduzido. No entanto, ele pode ser estendido, no caso de um requisito legal para continuar a retenção dos dados armazenados, conforme observado acima. O bloqueio de preservação garante que ninguém, nem mesmo administradores ou aqueles com certos controles de acesso, possam alterar as configurações ou substituir ou apagar os dados que foram armazenados, disponibilizar o arquivamento no Office 365 em linha com as orientações definidas na versão 2003 de seg Regra 17a-4.

Para entender como o Office 365 ajuda você a cumprir as obrigações normativas, especificamente em relação aos requisitos da regra 17a-4, consulte este [White Paper](https://go.microsoft.com/fwlink/?linkid=830440) que abrange o arquivamento do Exchange Online, o SharePoint Online, o onedrive for Business e o Skype for Business. O White Paper também fornece uma análise detalhada dos recursos de arquivamento e funcionalidades do Office 365 em relação a cada um dos requisitos na regra 17a-4 da SEC e demonstra aos clientes regulamentados como o arquivamento do Office 365 pode permitir que eles atendam a esses atende.