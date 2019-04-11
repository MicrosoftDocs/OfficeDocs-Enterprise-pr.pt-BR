---
title: Exchange Multi-geográfica
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Saiba mais sobre recursos de várias geografia no Exchange Online.
ms.openlocfilehash: 70db45bb7626c49a2c9cd6ec827bff6ca16d4673
ms.sourcegitcommit: 5e85536a6f53262136acfaac640f5d109a65f643
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2019
ms.locfileid: "31765063"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Recursos multigeográficos no Exchange Online

Em um ambiente multigeográfico, você pode selecionar o local do conteúdo da caixa de correio do Exchange Online (dados em repouso) em uma base por usuário.

Você pode colocar caixas de correio em locais geográficos de satélite:

- Criar uma nova caixa de correio do Exchange Online diretamente em uma localização geográfica de satélite.

- Mover uma caixa de correio do Exchange Online existente para uma localização geográfica de satélite, alterando o local de dados preferencial do usuário.

- Integração de uma caixa de correio de uma organização local do Exchange diretamente em um local geográfico de satélite.

## <a name="mailbox-placement-and-moves"></a>Posicionamento e movimentação de caixa de correio

Depois que a Microsoft concluir as etapas de configuração multigeográficas de pré-requisito, o Exchange Online honrará o atributo **PreferredDataLocation** nos objetos de usuário no Azure AD.

O Exchange Online sincroniza a propriedade **PreferredDataLocation** do Azure ad para a propriedade **MailboxRegion** no serviço de diretório do Exchange Online. O valor de **MailboxRegion** determina o local geográfico onde as caixas de correio do usuário e as caixas de correio de arquivo morto associadas serão colocadas. Não é possível configurar a caixa de correio principal de um usuário e as caixas de correio de arquivo morto para residir em diferentes locais geográficos. Somente um local geográfico pode ser configurado por objeto do usuário.

- Quando o **PreferredDataLocation** é configurado em um usuário com uma caixa de correio existente, a caixa de correio será colocada em uma fila de realocação e automaticamente movida para o local geográfico especificado.

- Quando o **PreferredDataLocation** é configurado em um usuário sem uma caixa de correio existente, quando você provisiona a caixa de correio, ele será provisionado no local geográfico especificado.

- Quando o **PreferredDataLocation** não for especificado em um usuário, quando você provisionar a caixa de correio, ele será provisionado na localização geográfica central.

- Se o código **PreferredDataLocation** estiver incorreto (por exemplo, um tipo de Nan em vez de um), a caixa de correio será provisionada na localização geográfica central.

**Observação**: as reuniões hospedadas de várias geografias e do Skype for Business online usam a propriedade **PreferredDataLocation** em objetos de usuário para localizar serviços. Se você configurar valores de **PreferredDataLocation** em objetos de usuário para reuniões hospedadas de modo regional, a caixa de correio para esses usuários será automaticamente movida para o local geográfico especificado após a hospedagem múltipla ser habilitada no locatário do Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitações de recursos para várias GEOS no Exchange Online

- Os recursos de segurança e conformidade (por exemplo, auditoria e descoberta eletrônica) que estão disponíveis no centro de administração do Exchange (Eat) não estão disponíveis em organizações multigeográfico. Em vez disso, você precisa usar o [centro de conformidade do & de segurança do Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar recursos de segurança e conformidade.

- Os usuários do Outlook para Mac podem ter uma perda temporária de acesso à sua pasta de arquivo morto online enquanto você move a caixa de correio para um novo local geográfico. Esta condição ocorre quando as caixas de correio primárias e de arquivo morto do usuário estão em locais geográficos diferentes, porque as movimentações de caixa de correio entre geografias podem ser concluídas em momentos diferentes.

- Os usuários não podem compartilhar *pastas de caixa de correio* entre locais geográficos no Outlook na Web (anteriormente conhecido como Outlook Web App ou OWA). Por exemplo, um usuário na União Européia não pode usar o Outlook na Web para abrir uma pasta compartilhada em uma caixa de correio localizada nos Estados Unidos. No enTanto, os usuários do Outlook na Web podem abrir *outras caixas de correio* em diferentes locais geográficos usando uma janela do navegador separada, conforme descrito em [abrir a caixa de correio de outra pessoa em uma janela do navegador separada no Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

  **Observação**: o compartilhamento de pastas de caixa de correio entre regiões tem suporte no Outlook no Windows.

- As pastas públicas são suportadas em organizações com várias geografias. No enTanto, as pastas públicas devem permanecer no local geográfico central. Não é possível mover pastas públicas para locais geográficos satélite.
