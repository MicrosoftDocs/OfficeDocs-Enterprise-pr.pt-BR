---
title: Usando o comunidades BGP em ExpressRoute para cenários do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: 'Conectar-se ao Office 365 usar o Windows Azure ExpressRoute se baseia em anúncios BGP de subredes de IP específicas que representam redes onde os pontos de extremidade do Office 365 estão implantados. Devido à natureza global do Office 365 e o número de serviços que constituem o Office 365, os clientes frequentemente têm necessidade de gerenciar os anúncios que eles aceitarem em sua rede. Redução do número de subredes IP; conhecida como prefixos IP em todo o restante deste artigo, para alinhar com a terminologia de gerenciamento de rede BGP, serve as seguintes metas de final para clientes:'
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539160"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Usando o comunidades BGP em ExpressRoute para cenários do Office 365

Conectar-se ao Office 365 usar o Windows Azure ExpressRoute se baseia em anúncios BGP de subredes de IP específicas que representam redes onde os pontos de extremidade do Office 365 estão implantados. Devido à natureza global do Office 365 e o número de serviços que constituem o Office 365, os clientes frequentemente têm necessidade de gerenciar os anúncios que eles aceitarem em sua rede. Redução do número de subredes IP; conhecida como prefixos IP em todo o restante deste artigo, para alinhar com a terminologia de gerenciamento de rede BGP, serve as seguintes metas de final para clientes:
  
- **Gerenciar os prefixos IP anunciados números aceitos** - que possuem uma infraestrutura de rede interna ou uma operadora de rede que suporta apenas um número limitado de prefixos IP e a clientes que têm uma operadora de rede que cobranças para aceitar os prefixos acima de um número limitado será deseja avaliar o número total de prefixos já foi divulgado para sua rede e selecionar quais aplicativos do Office 365 são mais adequados para ExpressRoute.

- **Gerenciar a quantidade de largura de banda necessária no circuito Azure ExpressRoute** - clientes talvez queira controlar o envelope de largura de banda dos serviços do Office 365 no caminho ExpressRoute versus o caminho da Internet. Isso permite aos clientes reservar ExpressRoute de largura de banda para aplicativos específicos, como Skype para negócios e encaminhar os aplicativos do Office 365 restantes no caminho de Internet.

Para ajudar os clientes a essas metas, prefixos de IP do Office 365 que são anunciados pela ExpressRoute estão marcados com valores comunidade BGP de serviço específicos conforme mostrado no exemplo abaixo.
  
> [!NOTE]
> Você deve esperar alguns tráfego de rede associado com outros aplicativos a serem incluídos no valor de comunidade. Este é o comportamento esperado para um Software global como um oferta de serviço com data centers e serviços compartilhados. Isso tiver sido minimizado onde for possível com as metas de dois acima, gerenciando contagem de prefixo e/ou a largura de banda em mente.

|**Serviço**|**Valor de comunidade BGP**|**Anotações**|
|:-----|:-----|:-----|
|Exchange\*  <br/> |12076:5010  <br/> |Inclui os serviços do Exchange e o EOP\*  <br/> |
|SharePoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype para negócios\*  <br/> |12076:5030  <br/> |Skype for Business online  <br/> |
|outros serviços do Office 365\*  <br/> |12076:5100  <br/> |Inclui o Azure Active Directory (cenários de autenticação e a sincronização de diretórios), bem como serviços do Portal do Office 365  <br/> |
|\*O escopo dos cenários de serviço incluídos no ExpressRoute está documentado no artigo [pontos de extremidade do Office 365](https://aka.ms/o365endpoints) .  <br/> \*\*Serviços adicionais e os valores de comunidade BGP podem ser adicionados no futuro. [Consulte a lista atual de comunidades BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/).<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Quais são os cenários mais comuns para uso de comunidades BGP?

Clientes podem usar comunidades BGP para regular grupos de prefixos IP que são aceitos pelos seu rede por meio do Windows Azure ExpressRoute, assim que influenciam a contagem total de prefixo IP e o envelope de largura de banda esperada de certos serviços do Office 365. É importante entender que todos os Office 365 exigirá que Internet acoplado tráfego independentemente do uso do Windows Azure ExpressRoute ou comunidades BGP. Três cenários a seguir são os usos mais comuns dessa funcionalidade.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Cenário 1: Minimizando o número de prefixos de IP do Office 365

Contoso Corporation é uma empresa de 50.000 pessoa que atualmente usa o Office 365 para Exchange Online e SharePoint Online. Na revisão ExpressRoute requisitos que Contoso determina seus dispositivos de rede em vários locais regionais não podem manipular os tamanhos de tabela de roteamento acima 100 entradas de rota adicional. O número total de prefixos IP que ExpressRoute seria anunciar para o conjunto completo de serviços do Office 365 e concluiu que ele excede 100 revisado da Contoso. Para manter-se no 100 entradas de rota adicional, Contoso escopos o uso de ExpressRoute para o Office 365 para apenas o BGP Online do SharePoint comunidade valor, 12076:5020, recebido por meio de correspondência da Microsoft ExpressRoute.

|**Marca de comunidade BGP usada**|**Funcionalidade roteável pela ExpressRoute do Windows Azure**|**Rotas de Internet necessárias**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive for Business  <br/> | DNS, lista de certificados Revogados, &amp; CDN solicitações  <br/>  Todos os outros serviços do Office 365 não especificamente suportados sobre ExpressRoute do Windows Azure  <br/>  Todos os outros serviços de nuvem da Microsoft  <br/>  Portal do Office 365, autenticação do Office 365, &amp; Office Online  <br/>  Exchange Online, Exchange Online Protection e Skype para negócios Online  <br/> |

> [!NOTE]
> Para atingir inferiores contagens de prefixo para cada serviço, persistirá uma quantidade mínima de sobreposição entre os serviços. Este é o comportamento esperado.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Cenário 2: ExpressRoute escopo e largura de banda interna usam para alguns serviços do Office 365

Fabrikam Inc, uma grande empresa multinacional com uma rede heterogênea distribuída é um assinante de muitos serviços do Office 365, inclusive; Exchange Online, SharePoint Online e Skype para negócios on-line. Infraestrutura de roteamento interna da Fabrikam pode lidar com milhares de prefixos IP em suas tabelas de roteamento; No entanto, Fabrikam só deseja provisionar ExpressRoute e largura de banda interna para os aplicativos do Office 365 que são mais confidenciais de desempenho da rede e usar sua largura de banda de Internet existente para todos os outros aplicativos do Office 365.
  
Por esse motivo, Fabrikam escopos sua largura de banda para apenas Skype para valor de comunidade BGP Online de negócios, 12076:5030, recebido por meio de correspondência ExpressRoute Microsoft Azure ExpressRoute. O tráfego de rede restantes associado com o Office 365 continua a usar os pontos de saída da internet.

|**Marca de comunidade BGP usada**|**Funcionalidade roteável pela ExpressRoute do Windows Azure**|**Rotas de Internet necessárias**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP sinalização, downloads, compartilhamento de voz, vídeo e da área de trabalho  <br/> | DNS, lista de certificados Revogados, &amp; CDN solicitações  <br/>  Todos os outros serviços do Office 365 não especificamente suportados sobre ExpressRoute do Windows Azure  <br/>  Todos os outros serviços de nuvem da Microsoft  <br/>  Portal do Office 365, autenticação do Office 365, &amp; Office Online  <br/>  Skype para telemetria de negócios, dicas rápidas do Skype cliente, conectividade pública de IM  <br/>  Exchange Online, Exchange Online Protection e o SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Cenário 3: Azure ExpressRoute de escopo para serviços do Office 365 somente

Woodgrove Bank é um cliente de vários serviços de nuvem da Microsoft incluindo o Office 365. Depois de avaliar a sua rede capacidade e consumo Woodgrove Bank decide implantar o Azure ExpressRoute como o caminho preferido para os serviços do Office 365 com suporte. As tabelas de roteamento podem suportar o conjunto completo de prefixos de IP do Office 365 e os circuitos Azure ExpressRoute que eles tenham sido configurados oferecem suporte a todas as necessidades de largura de banda e latência projetadas.
  
Para garantir que o tráfego de rede associado com os serviços de nuvem da Microsoft que não seja o uso de ExpressRoute para o Office 365 para todos os prefixos IP escopos do Office 365, Woodgrove Bank marcados com valores de comunidade BGP específicos do Office 365, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**Marca de comunidade BGP usada**|**Funcionalidade roteável pela ExpressRoute do Windows Azure**|**Rotas de Internet necessárias**|
|:-----|:-----|:-----|
|Exchange, Skype para os negócios, SharePoint, &amp; outros serviços  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive for Business  <br/> Skype SIP sinalização, downloads, compartilhamento de voz, vídeo e da área de trabalho  <br/> Portal do Office 365, autenticação do Office 365, &amp; Office Online  <br/> | DNS, lista de certificados Revogados, &amp; CDN solicitações  <br/>  Todos os outros serviços do Office 365 não especificamente suportados sobre ExpressRoute do Windows Azure  <br/>  Todos os outros serviços de nuvem da Microsoft  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Principais considerações para o uso de comunidades BGP de planejamento

Os clientes que preferem tirar proveito das comunidades BGP para influenciar como ExpressRoute é divulgado e propagada por meio de rede do cliente devem levar em consideração as considerações a seguir:
  
- Ao usar comunidades BGP em seu design de rede, é importante garantir a rota simetria ainda é mantida. Em alguns casos, a adição ou remoção das comunidades BGP pode criar uma situação onde roteamento simétrica for interrompido e sua configuração de roteamento deve ser atualizada para restabelecer o roteamento simétrico.

- Escopo da Azure ExpressRoute com valores de comunidade BGP é uma ação de cliente. Microsoft irá anunciar a todos os prefixos IP associados a relação aos independentemente de qualquer escopo configurado pelo cliente.

- Azure ExpressRoute não oferece suporte a todas as ações na rede da Microsoft com base no cliente atribuído comunidades BGP.

- Os prefixos IP usados pelo Office 365are apenas marcado com valores de comunidade BGP específicos do serviço, local, não há suporte para as comunidades BGP mais específicas. Serviços do Office 365 estão globais de natureza temporária, filtragem prefixos baseados no local do inquilino ou não há suporte para dados dentro da nuvem do Office 365. A abordagem recomendada é para configurar sua rede para coordenar o mais curta ou mais preferido caminho de rede do local de rede do usuário para a Microsoft global network, independentemente da localização física do endereço IP do serviço do Office 365 que está solicitando.

- Os prefixos IP incluídos em cada valor de comunidade BGP representam uma sub-rede que contém os endereços IP para o aplicativo do Office 365 associadas ao valor. Em alguns casos, mais de um aplicativo do Office 365 tem endereços IP dentro de uma sub-rede, resultando em um prefixo de IP existentes em mais de um valor de comunidade. Isso é esperado, embora raramente, comportamento devido a fragmentação de alocação e não afeta as metas de gerenciamento de contagem ou largura de banda de prefixo. Os clientes são incentivados a usar a opção "permitir o que é necessário" abordagem em vez de "negar o que não seja necessário" quando tirando proveito das comunidades BGP para o Office 365 minimizar o efeito.

- O uso de comunidades BGP não altera a configuração necessária para usar o Office 365 ou requisitos de conectividade de rede base. Clientes que desejam acessar o Office 365 ainda serão necessários para poder acessar a Internet.

- Escopo da Azure ExpressRoute com comunidades BGP afeta somente as rotas que sua rede interna pode ver sobre a relação de correspondência da Microsoft. Você pode precisar fazer configurações de nível aplicativos adicionais, como o uso de uma configuração de PAC ou WPAD em conjunto com o roteamento com escopo.

- Além de usar o Microsoft atribuído comunidades BGP, os clientes podem optar por atribuir suas próprias comunidades BGP a aprendidas por meio do Azure ExpressRoute influenciar o roteamento interno de prefixos de IP do Office 365. Um caso de uso popular é atribuindo uma comunidade BGP local com base para todas as rotas aprendidas por meio de cada ExpressRoute determinado correspondência local e depois usando essas informações downstream na rede do cliente para coordenar o mais curta ou caminho de rede em de maior preferência Rede da Microsoft. O uso do cliente atribuído comunidades BGP com ExpressRoute para cenários do Office 365 estiver fora do escopo do controle Microsoft ou visibilidade.

Aqui está um link curto que você pode usar para voltar: [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365).
  
## <a name="related-topics"></a>Tópicos relacionados

[Conectividade de rede para Office 365](network-connectivity.md)
  
[Microsoft Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Como gerenciar o ExpressRoute para a conectividade do Office 365](managing-expressroute-for-connectivity.md)
  
[Como rotear com o ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planejamento de rede com o ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Qualidade de mídia e o desempenho de conectividade de rede no Skype para negócios on-line](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute e QoS em Skype para negócios on-line](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Fluxo de chamadas usando ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Como implementar o ExpressRoute para Office 365](implementing-expressroute.md)
  
[Suporte para comunidades BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho](performance-tuning-using-baselines-and-history.md)
  
[Plano de solução de problemas de desempenho do Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute treinamento do Office 365](https://channel9.msdn.com/series/aer)
