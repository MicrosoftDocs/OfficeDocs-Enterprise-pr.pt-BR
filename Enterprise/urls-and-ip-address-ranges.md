---
title: 'URLs e intervalos de endereço IP do Office 365 '
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/14/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Resumo: o Office 365 requer conectividade com a Internet. Os pontos de extremidade abaixo devem estar acessíveis para os clientes que usam os planos do Office 365, incluindo a Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: acccd4dbb1d9d7107542b711c5a7dd34d2f33c71
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547759"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>URLs e intervalos de endereço IP do Office 365 

 **Resumo:** o Office 365 requer conectividade com a Internet. Os pontos de extremidade abaixo devem estar acessíveis para os clientes que usam os planos do Office 365, incluindo a Government Community Cloud (GCC).
  
> [!NOTE]
> Como parte da resposta da Microsoft à crise do COVID-19, a Microsoft declarou uma moratória temporária em algumas alterações planejadas de URLs e endereços IP. Essa moratória pretende fornecer confiança e simplicidade às equipes de TI de clientes para implementação de otimizações de rede recomendadas para cenários de trabalho em casa do Office 365. De 24 de março de 2020 até 30 de junho de 2020, essa moratória interromperá alterações nos principais serviços do Office 365 (Exchange Online, SharePoint Online e Microsoft Teams) para intervalos de IP e URLs incluídas na categoria Otimizar. As alterações dentro de outras categorias de ponto de extremidade ocorrerão normalmente. Durante esse período, os clientes podem usar as definições de ponto de extremidade do serviço da categoria Otimizar, do Office 365, de uma maneira estática para executar otimizações de rede direcionadas (por exemplo, reservas de largura de banda ou configuração de VPN de túnel dividido) com risco mínimo para a conectividade do Office 365 devido a alterações na rede de nuvem. Para garantir que não haja interrupções no serviço no final do período de moratória, a Microsoft recomenda que os clientes implemente os processos de automação e/ou de gerenciamento de alterações para pontos de extremidade do serviço do Office 365 usando as diretrizes fornecidas em [Gerenciando pontos de extremidade do Office 365](managing-office-365-endpoints.md).

> [!NOTE]
> A Microsoft lançou um serviço web baseado em REST para as entradas de endereço IP e FQDN desta página. Esse novo serviço ajudará você a configurar e atualizar dispositivos de perímetro de rede como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista ou alterações específicas. Este serviço substitui o documento XML desta página, que foi preterido em 2 de outubro de 2018. Para experimentar o novo serviço, acesse [serviço Web](office-365-ip-web-service.md).
  
*Office 365 Worldwide (+GCC)* | [Office 365 operado pela 21 Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Alemanha](office-365-germany-endpoints.md) | [Office 365 Departamento de Defesa do Governo dos E.U.A.](office-365-u-s-government-dod-endpoints.md)  | [Office 365 GCC Alta do Governo dos E.U.A.](office-365-u-s-government-gcc-high-endpoints.md) |
  
||||
|:-----|:-----|:-----|
|**Última atualização:** 14/04/2020 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Assinatura do log de alterações](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Baixar:** todos os destinos obrigatórios e opcionais em uma lista [no formato em JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> | **Use:** nossos arquivos proxy [PAC](managing-office-365-endpoints.md#pacfiles) <br/> |

 Comece com [Gerenciar os pontos de extremidade do Office 365](managing-office-365-endpoints.md) para entender nossas recomendações para gerenciar a conectividade de rede usando estes dados. Os dados dos pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicadas 30 dias antes de se tornarem ativas. Isso permite que os clientes que ainda não têm atualizações automáticas completem seus processos antes de precisarem de nova conectividade. Os pontos de extremidade também podem ser atualizados durante o mês, se necessário, para tratar de escalações de suporte, incidentes de segurança ou outros requisitos operacionais imediatos. Todos os dados exibidos abaixo nesta página são gerados a partir dos serviços web baseados em REST. Se estiver usando um script ou dispositivo de rede para acessar esses dados, vá diretamente para o [serviço Web](office-365-ip-web-service.md).

Os dados do terminal abaixo listam os requisitos de conectividade da máquina de um usuário ao Office 365. Ele não inclui conexões de rede da Microsoft em uma rede de clientes, às vezes chamadas de conexões de rede híbridas ou de entrada. Consulte [Terminais adicionais](additional-office365-ip-addresses-and-urls.md) para obter mais informações.

Os pontos de extremidade são agrupados em quatro áreas de serviço. As primeiras três áreas de serviço podem ser selecionadas independentemente de conectividade. A quarta área de serviço é uma dependência comum (chamada de Microsoft 365 Common and Office) e deve ter sempre conectividade de rede.

As colunas de dados exibidas são:

- **ID**: O número de ID da linha, também conhecido como um conjunto de pontos de extremidade. Esse ID é o mesmo que é retornado pelo serviço web ao conjunto de pontos de extremidade.

- **Categoria**: Mostra se o conjunto de terminais está classificado como "Otimizar", "Permitir" ou "Padrão". Você pode ler sobre essas categorias e orientações para o gerenciamento delas em [https://aka.ms/pnc](https://aka.ms/pnc). Esta coluna também lista quais conjuntos de terminais são necessários para se ter conectividade de rede. Quanto aos conjuntos de terminais que não precisam ter conectividade de rede, fornecemos notas neste campo para indicar qual funcionalidade faltaria se o conjunto de terminais estivesse bloqueado. Se você excluir uma área de serviço inteira, os conjuntos de terminais listados conforme necessário não exigirão conectividade.

- **ER**: Aqui, você verá um **Sim** se o conjunto de pontos de extremidade tem suporte no Azure ExpressRoute com prefixos de rota do Office 365. A comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área do serviço listada. Quando o ER estiver marcado como**Não**, isso significa que o ExpressRoute não é suportado para esse conjunto de pontos de extremidade. No entanto, não devemos presumir que não existem rotas anunciadas para um conjunto de ponto de extremidade onde ER está marcado como **Não**.

- **Endereços**: lista os FQDNs ou nomes de domínio curinga e intervalos de endereços IP para o conjunto de pontos de extremidade. Observe que o intervalo de endereços IP está no formato CIDR e pode incluir vários endereços IP individuais na rede especificada.
 
- **Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você poderá notar algumas duplicações nos intervalos de endereços IP em que há diferentes portas listadas.

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
>Para saber as URLs e endereços IP do Yammer, consulte [esta postagem de blog](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).
>

## <a name="related-topics"></a>Tópicos Relacionados

[Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md)
  
[Solucionar problemas de conectividade do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Conectividade de cliente](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Redes de distribuição de conteúdo](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Intervalos de IP do Datacenter do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Grupos de notícias públicos da Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
