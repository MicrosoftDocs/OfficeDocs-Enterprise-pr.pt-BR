---
title: Conectividade da rede com o Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: O Office 365 foi projetado para permitir que clientes em todo o mundo se conectem ao serviço usando uma conexão com a Internet. À medida que o serviço evolui, a segurança, o desempenho e a confiabilidade do Office 365 são aprimorados com base nos clientes que usam a Internet para estabelecer uma conexão com o serviço.
ms.openlocfilehash: 4510cb073c0fde64abc4ee796a55d7ef32662f8c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069867"
---
# <a name="network-connectivity-to-office-365"></a>Conectividade da rede com o Office 365

O Office 365 foi projetado para permitir que clientes em todo o mundo se conectem ao serviço usando uma conexão com a Internet. À medida que o serviço evolui, a segurança, o desempenho e a confiabilidade do Office 365 são aprimorados com base nos clientes que usam a Internet para estabelecer uma conexão com o serviço.
  
Os clientes que planejam usar o Office 365 devem avaliar suas necessidades existentes e previstas de conectividade com a Internet como parte do projeto de implantação. Para implantações corporativas confiáveis e a conectividade apropriada para a Internet é uma parte crítica do consumo de recursos e cenários do Office 365.
  
As avaliações de rede podem ser realizadas por várias pessoas e organizações diferentes, dependendo do tamanho e das preferências. O escopo de rede da avaliação também pode variar dependendo de onde você está no processo de implantação. Para ajudá-lo a entender melhor o que é necessário para executar uma avaliação de rede, produzimos um guia de avaliação de rede para ajudá-lo a entender as opções disponíveis para você. Essa avaliação determinará quais etapas e recursos precisam ser adicionados ao projeto de implantação para permitir que você adote o Office 365 com êxito.
  
Uma avaliação de rede abrangente, como as prescritas na [estrutura de operações do Skype](https://www.skypeoperationsframework.com/) , fornecerá soluções possíveis para os desafios de design de rede, juntamente com detalhes de implementação. A maioria das avaliações de rede indicará que a conectividade de rede com o Office 365 pode ser acomodada com [configurações secundárias ou alterações de design](https://aka.ms/manageo365endpoints) à rede existente e à infraestrutura de saída de Internet.

Algumas avaliações indicarão que a conectividade de rede com o Office 365 exigirá investimentos adicionais em componentes de rede. Por exemplo, investimentos em largura de banda de WAN ou infraestrutura de roteamento otimizada para dar suporte à conectividade com a Internet para o Office 365. Ocasionalmente, uma avaliação indicará que a conectividade de rede com o Office 365 é influenciada por normas ou requisitos de desempenho para cenários como a [qualidade de mídia do Skype for Business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Esses requisitos adicionais podem levar a investimentos na infraestrutura de conectividade com a Internet, otimização de roteamento e conectividade direta especializada.
  
> [!NOTE]
> A autorização da Microsoft é necessária para usar o ExpressRoute para o Office 365. A Microsoft revisa cada solicitação de cliente e autoriza apenas o ExpressRoute para o uso do Office 365 quando o requisito normativo de um cliente exige conectividade direta. Se você tiver esses requisitos, forneça o trecho de texto e o link da Web para a regulamentação que você interpreta para indicar que a conectividade direta é necessária no [formulário de solicitação do ExpressRoute para Office 365](https://aka.ms/O365ERReview) para começar a análise da Microsoft. Assinaturas não autorizadas tentando criar filtros de roteamento para o Office 365 receberão uma [mensagem de erro](https://support.microsoft.com/kb/3181709).
  
Principais pontos a serem considerados ao planejar sua avaliação de rede para o Office 365:
  
- O Office 365 é um serviço seguro, confiável e de alto desempenho executado pela Internet pública. Continuamos a investir para aprimorar esses aspectos do serviço. Todos os serviços do Office 365 estão disponíveis por meio da conectividade com a Internet.

- Estamos continuamente otimizando os principais aspectos do Office 365, como disponibilidade, alcance global e desempenho para conectividade baseada na Internet. Por exemplo, muitos serviços do Office 365 aproveitam um conjunto de expansão de nós de borda voltados para a Internet. Esta rede de borda oferece a melhor proximidade e desempenho para conexões vindas pela Internet.

- Ao considerar o uso do Office 365 para qualquer um dos serviços incluídos, como recursos de voz, vídeo ou reunião do Skype for Business Online, os clientes devem concluir uma avaliação de rede de ponta a ponta e atender aos requisitos usando nossa estrutura de operações do Skype. Esses clientes terão várias opções para atender a requisitos específicos de conectividade de nuvem, incluindo o ExpressRoute.

Confira o estudo de caso da Microsoft, otimizando o [desempenho da rede para o Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Se você estiver avaliando o Office 365 e não tiver certeza de onde começar com sua avaliação de rede ou se encontrou desafios de design de rede que precisa de ajuda para superar, trabalhe com sua equipe de conta da Microsoft.
  
Além disso, leia os [princípios de conectividade de rede do office 365](https://aka.ms/o365networkingprinciples) para entender os princípios de conectividade para o gerenciamento seguro do tráfego do Office 365 e obter o melhor desempenho possível. Este artigo o ajudará a entender as orientações mais recentes para otimizar com segurança a conectividade de rede do Office 365.
  
Aqui está um link curto que você pode usar para voltar: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Confira também

[Gerenciar pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Perguntas frequentes sobre pontos de extremidade do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Rede do Office 365 e ajuste de desempenho](network-planning-and-performance.md)
  
[Microsoft Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Como rotear com o ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planejamento de rede com o ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Usando comunidades BGP no ExpressRoute para cenários do Office 365 (versão prévia)](bgp-communities-in-expressroute.md)
  
[Qualidade da mídia e desempenho de conectividade de rede no Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Princípios de conectividade de rede do Office 365](https://aka.ms/o365networkingprinciples)
