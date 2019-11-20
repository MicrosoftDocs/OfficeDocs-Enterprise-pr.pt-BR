---
title: Avaliando a conectividade de rede do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/7/2019
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
ms.openlocfilehash: 8b784da9dcb8b5e821197e72ccc5ab49b976ba74
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745714"
---
# <a name="assessing-office-365-network-connectivity"></a>Avaliando a conectividade de rede do Office 365

*Este artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*

O Office 365 foi projetado para permitir que clientes em todo o mundo se conectem ao serviço usando uma conexão com a Internet. À medida que o serviço evolui, a segurança, o desempenho e a confiabilidade do Office 365 são aprimorados com base nos clientes que usam a Internet para estabelecer uma conexão com o serviço.
  
Os clientes que planejam usar o Office 365 devem avaliar suas necessidades existentes e previstas de conectividade com a Internet como parte do projeto de implantação. Para implantações corporativas confiáveis e a conectividade apropriada para a Internet é uma parte crítica do consumo de recursos e cenários do Office 365.
  
As avaliações de rede podem ser realizadas por várias pessoas e organizações diferentes, dependendo do tamanho e das preferências. O escopo de rede da avaliação também pode variar dependendo de onde você está no processo de implantação. Para ajudá-lo a entender melhor o que é necessário para executar uma avaliação de rede, produzimos um guia de avaliação de rede para ajudá-lo a entender as opções disponíveis para você. Essa avaliação determinará quais etapas e recursos precisam ser adicionados ao projeto de implantação para permitir que você adote o Office 365 com êxito.
  
Uma avaliação de rede abrangente fornecerá soluções possíveis para os desafios de design de rede, juntamente com detalhes de implementação. Algumas avaliações de rede mostrarão que a conectividade de rede ideal para o Office 365 pode ser acomodada com configurações secundárias ou alterações de design à rede existente e à infraestrutura de saída de Internet.

Algumas avaliações indicarão que a conectividade de rede com o Office 365 exigirá investimentos adicionais em componentes de rede. Por exemplo, redes corporativas que abrangem filiais e várias regiões geográficas podem exigir investimentos em soluções SD-WAN ou infraestrutura de roteamento otimizada para dar suporte à conectividade com a Internet para o Office 365. Ocasionalmente, uma avaliação indicará que a conectividade de rede com o Office 365 é influenciada por normas ou requisitos de desempenho para cenários como a [qualidade de mídia do Skype for Business online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Esses requisitos adicionais podem levar a investimentos na infraestrutura de conectividade com a Internet, otimização de roteamento e conectividade direta especializada.

Alguns recursos para ajudá-lo a avaliar sua rede:

- Confira [visão geral da conectividade de rede do office 365](office-365-networking-overview.md) para obter informações conceituais sobre a rede do Office 365.
- Confira os [princípios de conectividade de rede do office 365](https://aka.ms/o365networkingprinciples) para entender os princípios de conectividade para o gerenciamento seguro do tráfego do Office 365 e obter o melhor desempenho possível.
- Inscreva-se no [Microsoft FastTrack](https://www.microsoft.com/fasttrack) para obter assistência interativa com o planejamento, design e implantação do Office 365. 
- Consulte a seção [ferramenta de integração de rede do Office 365](assessing-network-connectivity.md#the-office-365-network-onboarding-tool) abaixo para executar os testes de conectividade básicos que fornecem orientações específicas sobre as melhorias de conectividade de rede que podem ser feitas entre um determinado local de usuário e o Office 365.

> [!NOTE]
> A autorização da Microsoft é necessária para usar o ExpressRoute para o Office 365. A Microsoft revisa cada solicitação de cliente e autoriza apenas o ExpressRoute para o uso do Office 365 quando o requisito normativo de um cliente exige conectividade direta. Se você tiver esses requisitos, forneça o trecho de texto e o link da Web para a regulamentação que você interpreta para indicar que a conectividade direta é necessária no [formulário de solicitação do ExpressRoute para Office 365](https://aka.ms/O365ERReview) para começar a análise da Microsoft. Assinaturas não autorizadas tentando criar filtros de roteamento para o Office 365 receberão uma [mensagem de erro](https://support.microsoft.com/kb/3181709).
  
Principais pontos a serem considerados ao planejar sua avaliação de rede para o Office 365:
  
- O Office 365 é um serviço seguro, confiável e de alto desempenho executado pela Internet pública. Continuamos a investir para aprimorar esses aspectos do serviço. Todos os serviços do Office 365 estão disponíveis por meio da conectividade com a Internet.

- Estamos continuamente otimizando os principais aspectos do Office 365, como disponibilidade, alcance global e desempenho para conectividade baseada na Internet. Por exemplo, muitos serviços do Office 365 aproveitam um conjunto de expansão de nós de borda voltados para a Internet. Esta rede de borda oferece a melhor proximidade e desempenho para conexões vindas pela Internet.

- Ao considerar o uso do Office 365 para qualquer um dos serviços incluídos, como Teams ou recursos de voz, vídeo ou reunião do Skype for Business Online, os clientes devem concluir uma avaliação de rede de ponta a ponta e atender aos requisitos de conectividade usando [o Microsoft FastTrack](https://www.microsoft.com/fasttrack).

Se você estiver avaliando o Office 365 e não tiver certeza de onde começar com sua avaliação de rede ou se encontrou desafios de design de rede que precisa de ajuda para superar, trabalhe com sua equipe de conta da Microsoft.

## <a name="the-office-365-network-onboarding-tool"></a>A ferramenta de integração de rede do Office 365

A [ferramenta de integração de rede do Office 365](https://aka.ms/netonboard) é uma ferramenta de avaliação de rede de verificação de conceito (VDC) que executa testes de conectividade básicos em seu locatário do Office 365 e faz recomendações de design de rede específicas para o desempenho ideal do Office 365. A ferramenta realça as escolhas de design de perímetro de rede corporativa comuns, que são úteis para a navegação na Web da Internet, mas afetam o desempenho de aplicativos SaaS grandes, como o Office 365.

A ferramenta de integração de rede faz o seguinte:

- Detecta o local ou você pode especificar um local para teste
- Verifica o local da saída da rede
- Testa o caminho de rede para a porta frontal mais próxima do serviço do Office 365
- Fornece testes avançados usando um aplicativo do Windows 10 para download que torna as recomendações de design de rede de perímetro relacionadas a servidores proxy, firewalls e DNS. A ferramenta também executa testes de desempenho para o Skype for Business Online, o Microsoft Teams, o SharePoint Online e o Exchange Online.

A ferramenta tem dois componentes: uma interface do usuário baseada em navegador que coleta informações básicas de conectividade e um aplicativo baixável do Windows 10 que executa testes avançados e retorna dados de avaliação adicionais.

A ferramenta baseada em navegador exibe as seguintes informações:

- Guia resultados e impacto
  - O local em um mapa da porta frontal do serviço de uso
  - O local em um mapa de outras portas frontais de serviço que forneceriam conectividade ideal
  - Desempenho relativo comparado com outros clientes do Office 365 perto de você
- Guia detalhes e soluções
  - Local do usuário por cidade e país
  - Local de egresso de rede por cidade, estado e país
  - Distância de saída do usuário para a rede
  - Localização de porta de entrada do serviço do Exchange Online do Office 365
  - Melhores porta (s) de serviço do Exchange Online do Office 365 para o local do usuário
  - Clientes em sua área de metrô com melhor desempenho

O aplicativo para download de testes avançados fornece as seguintes informações adicionais:

- Guia detalhes e soluções (acrescentado)
  - Gateway padrão do usuário
  - Servidor DNS cliente
  - Resolvedor de DNS recursivo de cliente
  - Servidor DNS do Exchange Online
  - Servidor DNS do SharePoint Online
  - Identificação do servidor proxy
  - Verificação de conectividade de mídia
  - Perda de pacotes de qualidade de mídia
  - Latência de qualidade de mídia
  - Tremulação de qualidade de mídia
  - Reordenação de pacote de qualidade de mídia
- Testes de conectividade para vários pontos de extremidade específicos do recurso
- Diagnóstico de caminho de rede que inclui dados de tracert e latência para o Exchange Online, SharePoint Online e serviços do teams

Você pode ler sobre a ferramenta de integração de rede do Office 365 e fornecer comentários na [ferramenta de integração de rede do office 365 atualizada com a nova](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) postagem do blog de recomendações de design de rede. As informações sobre atualizações futuras para esta ferramenta e outras atualizações de rede do Office 365 serão publicadas no blog de [rede do office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) .
  
Aqui está um link curto que você pode usar para voltar: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Confira também

[Visão geral da conectividade de rede do Office 365](office-365-networking-overview.md)

[Princípios de conectividade de rede do Office 365](https://aka.ms/o365networkingprinciples)

[Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md)

[URLs e intervalos de endereços IP do Office 365](urls-and-ip-address-ranges.md)

[URL do serviço Web e endereço IP do Office 365](office-365-ip-web-service.md)

[Rede do Office 365 e ajuste de desempenho](network-planning-and-performance.md)

[Visão geral do Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
