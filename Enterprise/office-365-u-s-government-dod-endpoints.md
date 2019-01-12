---
title: Pontos de extremidade do Office 365 DoD do governo dos EUA
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/11/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: 'Resumo: O Office 365 requer conectividade à Internet. Os pontos de extremidade abaixo devem ser alcançados para clientes que usam os planos do Office 365 US governamentais DoD apenas.'
hideEdit: true
ms.openlocfilehash: 3809298c012d41126271c3eec0981b5a6b7415c9
ms.sourcegitcommit: 79ffc3bfded032ee510b800426a0619e19e46915
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "27896371"
---
# <a name="office-365-us-government-dod-endpoints"></a>Pontos de extremidade do Office 365 DoD do governo dos EUA

*Aplicável à: Administração do Office 365*

 **Resumo:** O Office 365 requer conectividade à Internet. Os pontos de extremidade abaixo devem ser alcançados para clientes que usam os planos do Office 365 US governamentais DoD apenas.
  
> [!NOTE]
> A Microsoft lançou um serviço web baseado em REST para as entradas de endereço IP e FQDN desta página. Esse novo serviço ajudará você a configurar e atualizar dispositivos de perímetro de rede como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista ou alterações específicas. Este serviço substitui o documento XML desta página, que foi preterido em 2 de outubro de 2018. Para experimentar o novo serviço, acesse [serviço Web](office-365-ip-web-service.md).
  
 **Pontos de extremidade do Office 365:** [global (incluindo GCC)](urls-and-ip-address-ranges.md) | [Office 365 operado pela 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Alemanha](office-365-germany-endpoints.md)  |  *Office 365 Governo dos E.U.A. Departamento de Defesa* | [GCC High do Office 365 Governo dos E.U.A. ](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Última atualização:** 01/11/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [assinatura do Log de alterações](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Download:** a lista completa no [formato JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |
   
 Comece com [pontos de extremidade de gerenciamento do Office 365](managing-office-365-endpoints.md) entender as nossas recomendações para o gerenciamento de conectividade de rede usando esses dados. Dados de pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicadas 30 dias antes de começar a sendo ativo. Isso permite que os clientes que ainda não tenham automatizada atualizações para concluir seus processos antes que é necessária a conectividade do nova. Pontos de extremidade também podem ser atualizados durante o mês, se necessário para questões de suporte de endereço, incidentes de segurança ou outros requisitos operacionais imediatos. Os dados mostrados nesta página abaixo são gerados a partir de serviços da web baseado em REST. Se você estiver usando um script ou um dispositivo de rede para acessar esses dados, você deve ir diretamente para o [serviço Web](office-365-ip-web-service.md) .

Os dados dos pontos de extremidade abaixo listam requisitos de conectividade do computador de um usuário para o Office 365. Eles não incluem conexões de rede da Microsoft com uma rede de clientes, que são algumas vezes chamadas conexões de rede híbridas ou de entrada.

Os pontos de extremidade são agrupados em quatro áreas de serviço. As primeiras três áreas de serviço podem ser selecionadas independentemente de conectividade. A quarta área de serviço é uma dependência comum (chamada de Microsoft 365 Comum e Office Online) e deve ter sempre conectividade de rede.

As colunas de dados exibidas são:

- **ID**: O número de ID da linha, também conhecido como um conjunto de pontos de extremidade. Esse ID é o mesmo que é retornado pelo serviço web ao conjunto de pontos de extremidade.

- **Categoria**: mostra se o conjunto de pontos de extremidade é categorizado como "Otimizar", "Permitir" ou "Padrão". Leia sobre essas categorias e diretrizes para gerenciamento de todos eles em [ http://aka.ms/pnc ](http://aka.ms/pnc). Esta coluna também lista quais conjuntos de ponto de extremidade são necessários para que haja conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para que haja conectividade de rede, fornecemos notas nesse campo para indicar qual funcionalidade estaria ausente se o conjunto de pontos de extremidade estiver bloqueado. Se você estiver excluindo uma área de serviço inteira, os conjuntos de pontos de extremidade listados como necessários não vão precisar de conectividade.

- **ER**: esse é **Sim** , se o conjunto de ponto de extremidade é suportado pela ExpressRoute Azure com prefixos de rota do Office 365. Comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área de serviço listada. Quando ER for **não**, isso significa que ExpressRoute não é suportado para este conjunto de ponto de extremidade. No entanto, ele não deve ser presumido que não há rotas são anunciadas para um conjunto de pontos de extremidade onde ER é **não**. Se você planeja usar Connect do Azure AD, leia a [seção Considerações especiais](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) para garantir que você tem o apropriado configuração Connect do Azure AD.

- **Endereços**: lista os FQDNs ou nomes de domínio curinga e intervalos de endereços IP para o conjunto de pontos de extremidade. Observe que o intervalo de endereços IP está no formato CIDR e pode incluir vários endereços IP individuais na rede especificada.
 
- **Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você poderá notar algumas duplicações nos intervalos de endereços IP em que há diferentes portas listadas.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Observações da tabela:

- A segurança e o Centro de conformidade (SCC) oferece suporte para ExpressRoute do Windows Azure para o Office 365. O mesmo se aplica para muitos recursos expostos por meio de SCC, como relatórios, auditoria, eDiscovery avançado, DLP unificada e governança de dados. Dois recursos específicos, PST de importação e exportação, de descoberta eletrônica atualmente não suportam o Azure ExpressRoute com apenas filtros de rota de Office 365 devido à sua dependência no armazenamento de Blob do Azure. Para consumir esses recursos, você precisa ter conectividade separada para o armazenamento de Blob Azure usando quaisquer opções de conectividade Azure com suporte, que incluem a conectividade de Internet ou ExpressRoute Azure com filtros de rota pública do Windows Azure. Você deve avaliar o estabelecimento de tal conectividade para esses recursos. A equipe de proteção de informações do Office 365 está ciente de que esta limitação e está trabalhando ativamente para oferecer suporte para ExpressRoute do Windows Azure para o Office 365 como limitados às filtros de roteamento do Office 365 para esses recursos.

- Há adicionais opcionais pontos de extremidade do Office 365 ProPlus que não estejam listados e não são necessários para os usuários iniciam os aplicativos Office 365 ProPlus e editar documentos. Pontos de extremidade opcionais são hospedados em data centers da Microsoft e não processar, transmitir ou armazenar dados de clientes. É recomendável que as conexões de usuário para esses pontos de extremidade seja direcionado para o perímetro de saída de Internet padrão.
