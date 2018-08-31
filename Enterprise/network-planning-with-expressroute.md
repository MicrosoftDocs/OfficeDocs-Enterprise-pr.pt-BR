---
title: Planejamento de rede com o ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: ExpressRoute para o Office 365 fornece conectividade de camada 3 entre a sua rede e centros de dados da Microsoft. Os circuitos usam anúncios de rota Border Gateway Protocol (BGP) dos servidores de front-end do Office 365. Da perspectiva dos seus dispositivos de local, sempre que precisarem selecionar o caminho correto do TCP/IP para o Office 365, ExpressRoute do Windows Azure é visto como uma alternativa à Internet.
ms.openlocfilehash: 79cad16a619f048d1ba98b6058127f901211344d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539386"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planejamento de rede com o ExpressRoute para Office 365

ExpressRoute para o Office 365 fornece conectividade de camada 3 entre a sua rede e centros de dados da Microsoft. Os circuitos usam anúncios de rota Border Gateway Protocol (BGP) dos servidores de front-end do Office 365. Da perspectiva dos seus dispositivos de local, sempre que precisarem selecionar o caminho correto do TCP/IP para o Office 365, ExpressRoute do Windows Azure é visto como uma alternativa à Internet.
  
Azure ExpressRoute adiciona um caminho direto a um conjunto específico de recursos com suporte e serviços que são oferecidos pelos servidores do Office 365 em centros de dados da Microsoft. Azure ExpressRoute não substitui a conectividade à Internet para os data centers da Microsoft ou serviços básicos da Internet, como a resolução de nomes de domínio. Azure ExpressRoute e seus circuitos Internet devem ser protegido e redundantes.
  
A tabela a seguir destaca algumas diferenças entre a internet e as conexões do Azure ExpressRoute no contexto do Office 365.

|**Diferenças no planejamento de rede**|**Conexão de rede da Internet**|**Conexão de rede ExpressRoute**|
|:-----|:-----|:-----|
| Acesso aos serviços de internet necessários, incluindo;  <br/>  Resolução de nomes DNS  <br/>  Verificação de revogação de certificado  <br/>  Redes de distribuição de conteúdo  <br/> |Sim  <br/> |Solicitações para a Microsoft pertencem a infraestrutura DNS e/ou CDN pode usar a rede ExpressRoute.  <br/> |
| Acesso aos serviços do Office 365, inclusive;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business online  <br/>  Office Online  <br/>  Autenticação e Portal do office 365  <br/> |Sim, todos os aplicativos e recursos  <br/> |Sim, [recursos e aplicativos específicos](https://aka.ms/o365endpoints) <br/> |
|Segurança no perímetro ao local.  <br/> |Sim  <br/> |Sim  <br/> |
|Planejamento de alta disponibilidade.  <br/> |Failover para uma conexão de rede de internet alternativo  <br/> |Failover para uma conexão de ExpressRoute alternativo  <br/> |
|Conexão direta com um perfil de rede previsível.  <br/> |Não  <br/> |Sim  <br/> |
|Conectividade IPv6.  <br/> |Sim  <br/> |Sim  <br/> |

Expanda os títulos abaixo para rede mais orientação de planejamento. Também podemos ter gravadas uma série de [ExpressRoute do Windows Azure para treinamento do Office 365](https://channel9.msdn.com/series/aer) 10 partes que examina mais aprofundado.

## <a name="existing-azure-expressroute-customers"></a>Clientes existentes do Azure ExpressRoute

Se você estiver usando um circuito existente do Azure ExpressRoute e gostaria de adicionar a conectividade do Office 365 sobre esse circuito, você deve examinar o número de circuitos, os locais de saída e tamanho os circuitos para garantir que eles atenderão às necessidades de seu uso do Office 365. A maioria dos clientes exigem a largura de banda adicional e muitos circuitos adicionais.
  
Para habilitar o acesso de seus circuitos do Azure ExpressRoute existentes para o Office 365, [configure os filtros de rota](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) para garantir que os serviços do Office 365 estão acessíveis.
  
A assinatura do Windows Azure ExpressRoute é voltada, inscrições significado são vinculadas aos clientes para o cliente. Como um cliente, você pode ter vários circuitos ExpressRoute do Windows Azure e pode acessar muitos recursos de nuvem da Microsoft sobre esses circuitos. Por exemplo, você pode optar por acessar um Azure hospedados um locatário de produção do Office 365, um locatário de teste do Office 365 e máquina virtual por um par de circuitos do Azure ExpressRoute redundantes.
  
Esta tabela descreve os dois tipos de relações de correspondência, que você pode optar por implementar sobre seus circuitos.

|**Relação de correspondência**|**Azure privado**|**Microsoft**|
|:-----|:-----|:-----|
|**Serviços** <br/> |IaaS: Máquinas virtuais do Azure  <br/> |PaaS: Serviços de públicos Azure  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Conexão iniciação * * * <br/> |Cliente-para-Microsoft  <br/> Cliente da Microsoft  <br/> |Cliente-para-Microsoft  <br/> Cliente da Microsoft  <br/> |
|**Suporte de QoS** <br/> |Sem QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> QoS suporta Skype para negócios apenas no momento.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planejamento para o Windows Azure ExpressRoute de largura de banda

Cada cliente do Office 365 tem necessidades exclusivas de largura de banda dependendo do número de pessoas em cada local, como ativo estiverem com cada aplicativo do Office 365 e outros fatores, como o uso do local ou equipamento híbrida e configurações de segurança de rede.
  
Ter muito pouca largura de banda resultará em congestionamento, retransmissões de dados e os atrasos imprevisíveis. Ter muita largura de banda resultará em um custo desnecessário. Em uma rede existente, largura de banda é geralmente chamada em termos a quantidade de espaço disponível no circuito como uma porcentagem. Tendo o espaço reserva de 10% será provavelmente resultará na congestionamento e ter espaço reserva de 80% geralmente significa custo desnecessário. Alocações de destino do espaço de reserva típica são 20% a 50%.
  
Para localizar o nível adequado de largura de banda, o melhor mecanismo é testar seu consumo de rede existente. Isso é a única maneira de obter uma verdadeira medida de uso e precisa de cada configuração de rede e aplicativos são algumas maneiras exclusivo. Quando medir você vai querer preste atenção o consumo de largura de banda total, latência e congestionamento de TCP para entender a sua rede precisa.
  
Depois de ter uma linha de base estimada que inclui todos os aplicativos de rede, piloto do Office 365 com um pequeno grupo que compreende os diferentes perfis de pessoas da sua organização para determinar o uso real, e use as duas medidas para estimar a quantidade de largura de banda que é necessária para cada local do escritório. Se houver qualquer latência ou problemas de congestionamento de TCP encontrados em seus testes, você pode precisar mover quase a saída para as pessoas que usam o Office 365 ou remover rede intensiva verificação como inspeção da descriptografia SSL.
  
Todas as nossas recomendações sobre qual tipo de processamento de rede é recomendável se aplica aos circuitos ExpressRoute e a Internet. O mesmo é verdadeiro para o restante das orientações em nosso [site de ajuste de desempenho](https://aka.ms/tune).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>A aplicação de controles de segurança a ExpressRoute do Windows Azure para cenários do Office 365

Protegendo a conectividade do Azure ExpressRoute começa com os mesmos princípios que protegendo a conectividade com a Internet. Muitos clientes optar por implantar a rede e do perímetro controles ao longo do caminho de ExpressRoute conectar sua rede local para o Office 365 e outros nuvens da Microsoft. Esses controles podem incluir firewalls, proxies de aplicativo, prevenção contra vazamento de dados, a detecção de invasão, sistemas de prevenção de intrusão e assim por diante. Em muitos casos os clientes aplicar níveis diferentes de controles ao tráfego iniciado indo para a Microsoft, versus tráfego iniciado a partir do Microsoft pretende rede local do cliente, versus tráfego iniciado a partir pretende gerais de um local no local Destino da Internet.
  
Eis alguns exemplos de como integrar a segurança com o [modelo de conectividade de ExpressRoute](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models) você optar por implantar.

|**Opção de integração com ExpressRoute**|**Modelo de segurança de rede do perímetro**|
|:-----|:-----|
|Co localizado em uma troca de nuvem  <br/> |Instale o novo ou aproveitar a infra-estrutura existente do perímetro de segurança/no recurso localização conjunta em que a conexão ExpressRoute é estabelecida.  <br/> Facilidade de localização conjunta alavancar puramente para fins de roteamento/interconnect e conexões de distância inverso do recurso de localização conjunta à infraestrutura/perímetro de segurança local.  <br/> |
|Ethernet de ponto a ponto  <br/> |Encerrar a conexão de ponto a ponto ExpressRoute no local de infraestrutura do perímetro de segurança/local existente.  <br/> Instalar a nova infraestrutura de segurança/perímetro específica ao caminho ExpressRoute e encerrar a conexão de ponto a ponto lá.  <br/> |
|Para qualquer IPVPN  <br/> |Aproveite uma infraestrutura de segurança/perímetro local existente em todos os locais de saída para o IPVPN usado para ExpressRoute de conectividade do Office 365.  <br/> Hairpin o IPVPN usado para ExpressRoute para o Office 365 para locais específicos no local designado para servir como/do perímetro de segurança.  <br/> |

Alguns provedores de serviços também oferecem a funcionalidade de segurança/perímetro gerenciados como parte de suas soluções de integração com o Windows Azure ExpressRoute.
  
Ao considerar o posicionamento de topologia das opções de perímetro de rede/segurança usado para ExpressRoute para conexões do Office 365, a seguir está algumas considerações adicionais
  
- Os controles de segurança de rede/profundidade e tipo podem ter um impacto no desempenho e escalabilidade da experiência do usuário do Office 365.

- Saída (em-local -\>Microsoft) e de entrada (Microsoft -\>local) [se enabled] fluxos podem ter requisitos diferentes. Essas são provavelmente diferente de saída para destinos gerais da Internet.

- Requisitos do Office 365 para portas/protocolos e subredes IP necessários são os mesmos se o tráfego é roteado por meio de ExpressRoute para o Office 365 ou a Internet.

- Posicionamento topológico dos controles ao cliente/segurança de rede determina a rede de ponta a ponta ultimate entre o usuário e o serviço Office 365 e pode ter um impacto substancial sobre latência de rede e congestionamento.

- Os clientes são incentivados a projetar sua topologia de perímetro/de segurança para uso com ExpressRoute para o Office 365, de acordo com as práticas recomendadas para recuperação de desastre, alta disponibilidade e redundância.

Aqui está um exemplo de Woodgrove Bank que compara as diferentes opções de conectividade do Azure ExpressRoute com os modelos de segurança do perímetro discutidos acima.
  
### <a name="example-1-securing-azure-expressroute"></a>O exemplo 1: Protegendo ExpressRoute Azure
  
Woodgrove Bank está considerando a implementação ExpressRoute do Windows Azure e Após planejar a arquitetura ideal para [roteamento com ExpressRoute para o Office 365](routing-with-expressroute.md) e depois de usar as orientações acima para entender os requisitos de largura de banda, estiver determinando o método recomendado para proteger seu perímetro.
  
Para Woodgrove, uma organização multinacional com locais em vários continentes, segurança deve abranger todos os de perímetro. A opção de conectividade ideal para Woodgrove é uma conexão de multiponto com vários locais de correspondência em todo o mundo para atender às necessidades de seus funcionários em cada continente. Cada continente inclui circuitos redundantes do Azure ExpressRoute dentro do continente e segurança deve abranger todos esses.
  
Infraestrutura do Woodgrove seja confiável e pode manipular o trabalho adicional, como resultado, Woodgrove Bank é capaz de utilizar a infraestrutura de segurança de perímetro seus ExpressRoute do Windows Azure e da internet. Se isso não fosse o caso, Woodgrove podia optar por adquirir equipamentos adicionais para complementar seus equipamentos existente ou para lidar com um tipo diferente de conexão.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Alta disponibilidade e failover com ExpressRoute do Windows Azure
<a name="BKMK_high-availability"> </a>

É recomendável que pelo menos dois circuitos ativo de cada saída com ExpressRoute ao seu provedor de ExpressRoute de provisionamento. Este é o lugar mais comuns vemos falhas para clientes e você pode facilmente evitá-lo pelo provisionamento de um par de circuitos de ExpressRoute ativo/ativo. Também recomendamos pelo menos dois circuitos de Internet ativos/ativos porque muitos serviços do Office 365 só estão disponíveis através da Internet.
  
Dentro do ponto de saída da sua rede, há muitos outros dispositivos e circuitos que desempenham um papel fundamental na como pessoas percebem a disponibilidade. Essas partes de seus cenários de conectividade não estão cobertas pela ExpressRoute ou SLAs do Office 365, mas que desempenham uma função crítica na disponibilidade do serviço de ponta a ponta como perceptivelmente pelas pessoas em sua organização.
  
Foco nas pessoas que usam e operacional Office 365, se uma falha de qualquer um componente afetaria pessoas experiência usando o serviço, procure maneiras limitar a porcentagem do total de pessoas afetadas. Se um modo de failover for Operacionalmente complexo, considere a experiência dos República de muito tempo para recuperação e procure por modos de failover operacionalmente simples e automatizado.
  
Fora da sua rede, Office 365, ExpressRoute e seu provedor de ExpressRoute todos têm diferentes níveis de disponibilidade.
  
### <a name="service-availability"></a>Disponibilidade do serviço
  
- Serviços do Office 365 estão cobertos pela bem definida [contratos de nível de serviço](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx), que incluem o tempo de atividade e a disponibilidade métricas para os serviços individuais. Um motivo pelo que Office 365 pode manter tais níveis de serviço alta disponibilidade é a capacidade de componentes individuais para perfeitamente failover entre centros de dados do Microsoft muitos, usando o Microsoft network global. Esse failover estende do data center e de rede para vários pontos de saída de Internet e habilita failover com facilidade da perspectiva das pessoas usando o serviço.

- ExpressRoute [fornece um SLA de 99,9% de disponibilidade](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) em circuitos dedicados individuais entre a borda da rede Microsoft e a infraestrutura de provedor ou parceiro ExpressRoute. Esses níveis de serviço são aplicadas no nível de circuito de ExpressRoute, que consiste em [duas independente interconexão](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) entre o equipamento de Microsoft redundante e o equipamento de provedor de rede em cada local de correspondência.

### <a name="provider-availability"></a>Disponibilidade de provedor
  
- Parar de acordos de nível de serviço da Microsoft em seu provedor de ExpressRoute ou parceiro. Isso também é o primeiro lugar, você pode fazer as escolhas que influenciarão o seu nível de disponibilidade. Bastante avalie a arquitetura, disponibilidade e características de resiliência seu provedor ExpressRoute oferece entre seu perímetro de rede e sua conexão provedores em cada local de correspondência da Microsoft. Preste atenção os aspectos lógicos e físicos de redundância, equipamento de correspondência, circuitos WAN operadora fornecido e qualquer valor adicional adicione serviços, como serviços NAT ou firewalls gerenciados.

### <a name="designing-your-availability-plan"></a>Projetar seu plano de disponibilidade
  
É altamente recomendável que você planejar e projetar a alta disponibilidade e resiliência em seus cenários de conectividade de ponta a ponta para o Office 365. Inclua um design;
  
- Não há pontos únicos de falha, incluindo circuitos Internet e ExpressRoute.

- minimizando o número de pessoas afetados e a duração de que têm impacto para os modos de falha mais esperados.

- Otimizando o processo de recuperação simples, repetível e automática de modos de falha mais esperados.

- suporte completos demandas do tráfego de rede e a funcionalidade por meio de caminhos redundantes, sem prejuízo substancial.

Os cenários de conectividade devem incluir uma topologia de rede que é otimizada para vários caminhos de rede independentes e ativa para o Office 365. Isso resultará em uma disponibilidade de ponta a ponta melhor que uma topologia que é otimizada apenas para redundância no nível do dispositivo ou equipamento individual.
  
> [!TIP]
> Se os usuários estão distribuídos em vários continentes ou regiões geográficas e cada um desses locais se conecta sobre circuitos WAN redundantes em um local de local único onde se encontra um único circuito de ExpressRoute, os usuários observarão menor disponibilidade do serviço de ponta a ponta que um design de topologia de rede que inclua circuitos ExpressRoute independentes que se conectam as diferentes regiões para a correspondência mais próximo local.
  
É recomendável que pelo menos dois circuitos ExpressRoute com cada circuito se conectar com um local diferente de correspondência geográfico de provisionamento. Você deve provisionar esse par ativa-ativa de circuitos para cada região em que as pessoas usarão ExpressRoute conectividade para serviços do Office 365. Isso permite que cada região à permanecem conectadas durante um desastre que afeta um local principal como um datacenter ou local de correspondência. Configurá-los no como ativo/ativo permite o tráfego de usuário final para ser distribuído em vários caminhos de rede. Isso reduz o escopo das pessoas afetados durante interrupções de equipamento de rede ou dispositivo.
  
Não recomendamos o uso de um único circuito de ExpressRoute com a Internet como um backup.
  
### <a name="example-2-failover-and-high-availability"></a>Exemplo 2: Alta disponibilidade e Failover
  
Design de vários locais geográfico do Woodgrove Bank passou por uma revisão de roteamento, a largura de banda, segurança e agora deve passar por uma revisão de alta disponibilidade. Woodgrove pensa na alta disponibilidade à medida que cobrem três categorias; resiliência, confiabilidade e redundância.
  
Resiliência permite Woodgrove recuperar de falhas rapidamente. Confiabilidade permite Woodgrove oferecer um resultado consistente dentro do sistema. Redundância permite Woodgrove para uma movimentação entre um ou mais instâncias espelhadas da infraestrutura.
  
Dentro de cada configuração de borda, o Woodgrove tem redundantes IDS, Proxies e Firewalls. América do Norte, Woodgrove tem uma configuração de borda em datacenters Dallas e outra configuração de borda em datacenters Virgínia. O equipamento redundante em cada local oferece resiliência para esse local.
  
A configuração de rede do Woodgrove Bank é criada baseada em alguns princípios-chave:
  
- Dentro de cada região geográfica, há vários circuitos ExpressRoute do Windows Azure.

- Cada circuito dentro de uma região pode oferecer suporte a todo o tráfego de rede dentro dessa região.

- Roteamento claramente preferem uma ou outro caminho dependendo da disponibilidade, local e assim por diante.

- Failover entre circuitos Azure ExpressRoute acontece automaticamente sem configuração adicional ou Woodgrove precisa fazer nada.

- Failover entre circuitos Internet acontece automaticamente sem configuração adicional ou Woodgrove precisa fazer nada.

Nesta configuração, com redundância no nível de físicos e virtual, Woodgrove Bank é capaz de oferecer resiliência local, regional resiliência e flexibilidade global, de forma confiável. Woodgrove eleito essa configuração depois de avaliar um circuito Azure ExpressRoute único por região, bem como a possibilidade de failover para a internet.
  
Se Woodgrove não foi capaz de ter vários circuitos Azure ExpressRoute por região, rotear o tráfego originado na América do Norte para o circuito Azure ExpressRoute da Ásia-Pacífico adicionasse o um nível inaceitável de latência e a configuração de encaminhador DNS necessária adiciona complexidade.
  
Aproveitando a internet como uma configuração de backup não é recomendável. Isso interrompe o princípio de confiabilidade do Woodgrove, resultando em uma experiência inconsistente ao usar a conexão. Além disso, a configuração manual seriam necessária para failover, considerando os anúncios de BGP que tiverem sido configurados, configuração NAT, configuração do DNS e a configuração de proxy. Isso adicionado a complexidade de failover aumenta o tempo de recuperação e diminui sua capacidade para diagnosticar e resolver as etapas envolvidas.
  
Ainda tem dúvidas sobre como planejar e implementar o gerenciamento de tráfego ou ExpressRoute Azure? Leia o restante da nossa [orientações de desempenho e de rede](https://aka.ms/tune) ou o [Azure ExpressRoute FAQ](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).
  
## <a name="working-with-azure-expressroute-providers"></a>Trabalhando com provedores de ExpressRoute do Windows Azure
<a name="BKMK_high-availability"> </a>

Escolha os locais de seus circuitos com base em sua largura de banda, latência, segurança e planejamento de alta disponibilidade. Quando você souber os locais ideais que você gostaria de fazer circuitos [Revise a lista atual de provedores por região](https://azure.microsoft.com/documentation/articles/expressroute-locations/).
  
Trabalhar com o seu provedor ou provedores para selecionar as melhores opções de conectividade, ponto a ponto, multiponto ou hospedada. Lembre-se de que você pode misturar e corresponder as opções de conectividade, contanto que a largura de banda e outros componentes redundantes oferecem suporte a seu design de roteamento e a alta disponibilidade.
  
Aqui está um link curto que você pode usar para voltar:[https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>Tópicos relacionados
<a name="BKMK_high-availability"> </a>

[Conectividade de rede para Office 365](network-connectivity.md)
  
[Microsoft Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Como gerenciar o ExpressRoute para a conectividade do Office 365](managing-expressroute-for-connectivity.md)
  
[Como rotear com o ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Como implementar o ExpressRoute para Office 365](implementing-expressroute.md)
  
[Usando o comunidades BGP em ExpressRoute para cenários do Office 365 (preview)](bgp-communities-in-expressroute.md)
  
[Qualidade de mídia e o desempenho de conectividade de rede no Skype para negócios on-line](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Otimização de sua rede para Skype para negócios Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute e QoS em Skype para negócios on-line](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Fluxo de chamadas usando ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho](performance-tuning-using-baselines-and-history.md)
  
[Plano de solução de problemas de desempenho do Office 365](performance-troubleshooting-plan.md)
  
[URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Ajuste de desempenho e de rede do Office 365](network-planning-and-performance.md)
  
[Pontos de extremidade perguntas Frequentes do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
