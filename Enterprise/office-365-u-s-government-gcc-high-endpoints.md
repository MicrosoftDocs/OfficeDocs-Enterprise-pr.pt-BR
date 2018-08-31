---
title: Pontos de extremidade dos EUA governamentais GCC alta do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Se sua organização usa o Office 365 e restringe os computadores em sua rede de se conectar à Internet, abaixo você encontrará os pontos de extremidade (FQDNs, portas, URLs, IPv4 e IPv6 intervalos de endereços) que você deve incluir em seu saída permite listas garantir que sua computadores com êxito podem usar o Office 365.
hideEdit: true
ms.openlocfilehash: eb1ac47ad8317b46ce19106e8eeab5dae3c25432
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539376"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Pontos de extremidade dos EUA governamentais GCC alta do Office 365

 *Aplicável à: Administração do Office 365*

**Resumo:** O Office 365 requer conectividade à Internet. Os pontos de extremidade abaixo devem ser alcançados para clientes usando apenas planos de alta de GCC do governo dos EUA Office 365.
  
> [!NOTE]
> A Microsoft está desenvolvendo um serviço web baseado em REST para o endereço IP e as entradas de FQDN nesta página. Esse novo serviço ajudará você a configurar e atualizar os dispositivos de perímetro de rede, como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista, ou alterações específicas. Esse serviço eventualmente substituirão o documento XML, RSS feed e o endereço IP e as entradas de FQDN nesta página. Para testar esse novo serviço, vá para o [serviço Web](managing-office-365-endpoints.md#webservice).
  
 **Pontos de extremidade do office 365:** [Worldwide (incluindo GCC)](urls-and-ip-address-ranges.md)  |  [Office 365 operado pela Vianet 21](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Alemanha](office-365-germany-endpoints.md)  | [Office 365 US governamentais DoD](office-365-u-s-government-dod-endpoints.md) | *Alta de GCC do governo dos EUA Office 365* |
  
|||
|:-----|:-----|
|**Última atualização:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [assinatura do Log de alterações](https://aka.ms/usendpointrss) <br/> |**Download:** a lista completa em [formato XML](https://aka.ms/usdefenseendpoints) <br/> |
   
 Comece com [pontos de extremidade de gerenciamento do Office 365](managing-office-365-endpoints.md) entender as nossas recomendações para o gerenciamento de conectividade de rede usando esses dados. Dados de pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicadas 30 dias antes de começar a sendo ativo. Isso permite que os clientes que ainda não tenham automatizada atualizações para concluir seus processos antes que é necessária a conectividade do nova. Pontos de extremidade também podem ser atualizados durante o mês, se necessário para questões de suporte de endereço, incidentes de segurança ou outros requisitos operacionais imediatos. Os dados mostrados nesta página abaixo são gerados a partir de serviços da web baseado em REST. Se você estiver usando um script ou um dispositivo de rede para acessar esses dados, você deve ir diretamente para o [serviço Web](managing-office-365-endpoints.md#webservice) .

Dados de ponto de extremidade abaixo lista os requisitos para a conectividade da máquina de um usuário para o Office 365. Ele não inclui as conexões de rede da Microsoft em uma rede de cliente, às vezes chamado de híbrido ou conexões de rede de entrada.

Os pontos de extremidade são agrupados em quatro áreas de serviço. As áreas de serviço de três primeira independentemente podem ser selecionadas para conectividade. Área de serviço quarta é uma dependência comuns (chamada Microsoft 365 comuns e Online do Office) e sempre deve ter conectividade de rede.

Colunas de dados mostradas são:

- **ID**: número de identificação da linha, também conhecida como um conjunto de pontos de extremidade. Este ID é a mesma que é retornado pelo serviço da web para o conjunto de pontos de extremidade.

- **Categoria**: mostra se o conjunto de ponto de extremidade é classificado como "Otimizar", "Permitir" ou "Padrão". Você pode ler sobre essas categorias e orientação para o gerenciamento deles em [http://aka.ms/pnc](http://aka.ms/pnc). Essa coluna também lista quais conjuntos de ponto de extremidade são necessários para a conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para ter conectividade de rede, nós fornecemos anotações neste campo para indicar qual funcionalidade seria ausente se o conjunto de ponto de extremidade está bloqueado. Se você estiver excluindo uma área de todo o serviço, os conjuntos de ponto de extremidade listados conforme exigido não exigem conectividade.

- **ER**: esse é **Sim** , se o conjunto de ponto de extremidade é suportado pela ExpressRoute Azure com prefixos de rota do Office 365. Comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área de serviço listada. Quando ER for **não**, isso significa que ExpressRoute não é suportado para este conjunto de ponto de extremidade. No entanto, ele não deve ser presumido que não há rotas são anunciadas para um conjunto de pontos de extremidade onde ER é **não**. Se você planeja usar Connect do Azure AD, leia a [seção Considerações especiais](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) para garantir que você tem o apropriado configuração Connect do Azure AD.

- **Endereços**: lista os FQDNs ou nomes de domínio de curinga e intervalos de endereço IP para o conjunto de pontos de extremidade. Observe que um intervalo de endereços IP está no formato CIDR e pode incluir muitos endereços IP individuais na rede especificada.
 
- **Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você pode observar algumas duplicação em intervalos de endereço IP onde há portas diferentes listadas.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Observações da tabela:

- A segurança e o Centro de conformidade (SCC) oferece suporte para ExpressRoute do Windows Azure para o Office 365. O mesmo se aplica para muitos recursos expostos por meio de SCC, como relatórios, auditoria, eDiscovery avançado, DLP unificada e governança de dados. Dois recursos específicos, PST de importação e exportação, de descoberta eletrônica atualmente não suportam o Azure ExpressRoute com apenas filtros de rota de Office 365 devido à sua dependência no armazenamento de Blob do Azure. Para consumir esses recursos, você precisa ter conectividade separada para o armazenamento de Blob Azure usando quaisquer opções de conectividade Azure com suporte, que incluem a conectividade de Internet ou ExpressRoute Azure com filtros de rota pública do Windows Azure. Você deve avaliar o estabelecimento de tal conectividade para esses recursos. A equipe de proteção de informações do Office 365 está ciente de que esta limitação e está trabalhando ativamente para oferecer suporte para ExpressRoute do Windows Azure para o Office 365 como limitados às filtros de roteamento do Office 365 para esses recursos.

- Há adicionais opcionais pontos de extremidade do Office 365 ProPlus que não estejam listados e não são necessários para os usuários iniciam os aplicativos Office 365 ProPlus e editar documentos. Pontos de extremidade opcionais são hospedados em data centers da Microsoft e não processar, transmitir ou armazenar dados de clientes. É recomendável que as conexões de usuário para esses pontos de extremidade seja direcionado para o perímetro de saída de Internet padrão.

