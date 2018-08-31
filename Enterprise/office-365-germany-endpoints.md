---
title: Pontos de extremidade do Office 365 Germany
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Se sua organização usa o Office 365 e restringe os computadores em sua rede de se conectar à Internet, abaixo você encontrará os pontos de extremidade (FQDNs, portas, URLs e IPv4 e IPv6 intervalos de endereços) que você deve incluir em seu saída permite listas garantir que sua computadores com êxito podem usar o Office 365.
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539130"
---
# <a name="office-365-germany-endpoints"></a>Pontos de extremidade do Office 365 Germany

 *Aplicável à: Administração do Office 365*

**Resumo:** O Office 365 requer conectividade à Internet. Os pontos de extremidade abaixo devem ser alcançados para clientes usando apenas planos do **Office 365 Alemanha** .
  
> [!NOTE]
> A Microsoft está desenvolvendo um serviço web baseado em REST para o endereço IP e as entradas de FQDN nesta página. Esse novo serviço ajudará você a configurar e atualizar os dispositivos de perímetro de rede, como firewalls e servidores proxy. Você pode baixar a lista de pontos de extremidade, a versão atual da lista, ou alterações específicas. Esse serviço eventualmente substituirão o documento XML, RSS feed e o endereço IP e as entradas de FQDN nesta página. Para testar esse novo serviço, vá para o [serviço Web](managing-office-365-endpoints.md#webservice). 
  
 **Pontos de extremidade do office 365:** [Worldwide (incluindo GCC)](urls-and-ip-address-ranges.md)   |  [Office 365 operado pela Vianet 21](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Alemanha* | [Office 365 US governamentais DoD](office-365-u-s-government-dod-endpoints.md) | [Alta de GCC do governo dos EUA Office 365](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**Última atualização:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [lista de alterações para os pontos de extremidade do Office 365 Alemanha](office-365-germany-endpoints-change-log.md)||

Comece com [pontos de extremidade de gerenciamento do Office 365](managing-office-365-endpoints.md) entender as nossas recomendações para o gerenciamento de conectividade de rede usando esses dados. Dados de pontos de extremidade são atualizados no início de cada mês com novos endereços IP e URLs publicadas 30 dias antes de começar a sendo ativo. Isso permite que os clientes que ainda não tenham automatizada atualizações para concluir seus processos antes que é necessária a conectividade do nova. Pontos de extremidade também podem ser atualizados durante o mês, se necessário para questões de suporte de endereço, incidentes de segurança ou outros requisitos operacionais imediatos. Você sempre pode consultar a [lista de alterações para os pontos de extremidade do Office 365 Alemanha](office-365-germany-endpoints-change-log.md).

Os dados mostrados nesta página abaixo são gerados a partir de serviços da web baseado em REST. Se você estiver usando um script ou um dispositivo de rede para acessar esses dados, você deve ir diretamente para o [serviço Web](managing-office-365-endpoints.md#webservice) .

Dados de ponto de extremidade abaixo lista os requisitos para a conectividade da máquina de um usuário para o Office 365. Ele não inclui as conexões de rede da Microsoft em uma rede de cliente, às vezes chamado de híbrido ou conexões de rede de entrada.

Os pontos de extremidade são agrupados em quatro áreas de serviço. As áreas de serviço de três primeira independentemente podem ser selecionadas para conectividade. Área de serviço quarta é uma dependência comuns (chamada Microsoft 365 comuns e Online do Office) e sempre deve ter conectividade de rede.

Colunas de dados mostradas são:

- **ID**: número de identificação da linha, também conhecida como um conjunto de pontos de extremidade. Este ID é a mesma que é retornado pelo serviço da web para o conjunto de pontos de extremidade.

- **Categoria**: mostra se o conjunto de ponto de extremidade é classificado como "Otimizar", "Permitir" ou "Padrão". Você pode ler sobre essas categorias e orientação para o gerenciamento deles em [http://aka.ms/pnc](http://aka.ms/pnc). Essa coluna também lista quais conjuntos de ponto de extremidade são necessários para a conectividade de rede. Para conjuntos de ponto de extremidade que não são necessários para ter conectividade de rede, nós fornecemos anotações neste campo para indicar qual funcionalidade seria ausente se o conjunto de ponto de extremidade está bloqueado. Se você estiver excluindo uma área de todo o serviço, os conjuntos de ponto de extremidade listados conforme exigido não exigem conectividade.

- **ER**: esse é **Sim** , se o conjunto de ponto de extremidade é suportado pela ExpressRoute Azure com prefixos de rota do Office 365. Comunidade do BGP que inclui os prefixos de rota mostrados se alinha com a área de serviço listada. Quando ER for **não**, isso significa que ExpressRoute não é suportado para este conjunto de ponto de extremidade. No entanto, ele não deve ser presumido que não há rotas são anunciadas para um conjunto de pontos de extremidade onde ER é **não**.

- **Endereços**: lista os FQDNs ou nomes de domínio de curinga e intervalos de endereço IP para o conjunto de pontos de extremidade. Observe que um intervalo de endereços IP está no formato CIDR e pode incluir muitos endereços IP individuais na rede especificada.
 
- **Portas**: lista as portas TCP ou UDP que são combinadas com os endereços para formar o ponto de extremidade de rede. Você pode observar algumas duplicação em intervalos de endereço IP onde há portas diferentes listadas.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

