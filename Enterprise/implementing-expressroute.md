---
title: Como implementar o ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
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
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: ExpressRoute para o Office 365 fornece um caminho alternativo de roteamento para internet muitos enfrentados pelos serviços do Office 365. A arquitetura do ExpressRoute para o Office 365 se baseia em anuncie públicos prefixos IP dos serviços do Office 365 que já estão acessíveis através da Internet em seus circuitos ExpressRoute provisionados para redistribuição subsequente desses prefixos IP em sua rede. Com ExpressRoute você efetivamente habilitar várias diferentes caminhos de roteamento, através da internet e ExpressRoute, para muitos serviços do Office 365. Este estado do roteamento em sua rede pode representar uma alteração significativa para como sua topologia de rede interna é criada.
ms.openlocfilehash: e535135557f7f2f64077c1d926f120fff78dbd42
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "25715867"
---
# <a name="implementing-expressroute-for-office-365"></a>Como implementar o ExpressRoute para Office 365

ExpressRoute para o Office 365 fornece um caminho alternativo de roteamento para internet muitos enfrentados pelos serviços do Office 365. A arquitetura do ExpressRoute para o Office 365 se baseia em anuncie públicos prefixos IP dos serviços do Office 365 que já estão acessíveis através da Internet em seus circuitos ExpressRoute provisionados para redistribuição subsequente desses prefixos IP em sua rede. Com ExpressRoute você efetivamente habilitar várias diferentes caminhos de roteamento, através da internet e ExpressRoute, para muitos serviços do Office 365. Este estado do roteamento em sua rede pode representar uma alteração significativa para como sua topologia de rede interna é criada.
  
 **Status:** Guia completo v2
  
Planeje cuidadosamente sua ExpressRoute para a implementação do Office 365 para acomodar para a complexidade da rede de ter de roteamento disponíveis via ambas um circuito dedicado com rotas inseridas no sua rede principal e a internet. Se você e sua equipe não executam o planejamento detalhado e teste neste guia, há um alto risco que você vai enfrentar intermitente ou uma perda total de conectividade para o Office 365 serviços quando o circuito ExpressRoute está habilitado.
  
Para uma implementação com êxito, você precisará analisar os requisitos de infraestrutura, passar a avaliação de rede detalhado e projetar, planejar a distribuição de maneira em estágios e controlada cuidadosamente e crie um plano de teste e a validação detalhada. Para um ambiente distribuído grande não é incomum ver implementações abranger vários meses. Este guia foi projetado para ajudá-lo a planejar com antecedência.
  
Implantações de grandes porte bem-sucedida podem tirar seis meses no planejamento e geralmente incluem os membros da equipe de várias áreas da organização, incluindo a rede, os administradores de servidor de Firewall e Proxy, administradores do Office 365, segurança, suporte ao usuário final, project gerenciamento e apoio executivo. Seu investimento no processo de planejamento reduzirá a probabilidade de que você vai sofrer falhas de implantação, resultando em tempo de inatividade ou solução de problemas complexas e caras.
  
Esperamos que os seguintes pré-requisitos para ser concluída antes que este guia de implementação é iniciado.
  
1. Você concluiu uma avaliação de rede para determinar se ExpressRoute é recomendado e aprovada.

2. Você selecionou um provedor de serviço de rede ExpressRoute. Encontre detalhes sobre os [parceiros de ExpressRoute e aos locais](https://azure.microsoft.com/documentation/articles/expressroute-locations/).

3. Você já tenha lido e compreender a [documentação ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) e a rede interna é capaz de atender aos ExpressRoute pré-requisitos ponta a ponta.

4. Sua equipe tem ler todas as orientações pública e a documentação em [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert)e observadas da série [ExpressRoute do Windows Azure para treinamento do Office 365](https://channel9.msdn.com/series/aer) no Channel 9 para obter uma compreensão do críticos detalhes técnicos, incluindo:

      - As dependências de internet dos serviços SaaS.

      - Como evitar assimétricas rotas e tratar do roteamento complexos.

      - Como incorporar a segurança de perímetro, disponibilidade e controles de nível de aplicativo.

## <a name="begin-by-gathering-requirements"></a>Comece a coleta de requisitos
<a name="requirements"> </a>

Inicie determinando quais recursos e serviços que você planeja adotar dentro da sua organização. Você precisa determinar quais recursos dos serviços do Office 365 diferentes serão usados e quais locais em sua rede hospedará pessoas que usam esses recursos. Com o catálogo de cenários, é necessário adicionar a rede de atributos que cada um desses cenários exigem; como os fluxos de tráfego de rede de entrada e saída e se os pontos de extremidade do Office 365 estão disponíveis via ExpressRoute ou não.
  
Para coletar os requisitos da sua organização:
  
- Catálogo o tráfego de rede de entrada e saída para os sua organização estiver usando serviços do Office 365. Consulte a página de intervalos de endereço IP e URLs do Office 365 para a descrição de fluxos que exigem diferentes cenários do Office 365.

- Reunir documentação da topologia de rede existente mostrando detalhes do seu backbone de rede de longa distância interna e a topologia, a conectividade dos sites de satélite, conectividade de usuário milha última, o roteamento para os pontos de saída do perímetro de rede e serviços de proxy.

  - Identifique os pontos de extremidade de serviço de entrada nos diagramas de rede que outros serviços do Microsoft Office 365 e o conectará à, mostrando a internet e caminhos de conexão ExpressRoute propostos.

  - Identifique todos os locais do usuário geográfica e conectividade WAN entre locais, juntamente com os quais locais têm atualmente uma saída para a internet e quais locais são propostos para ter uma saída para um local de correspondência ExpressRoute.

  - Identificar todos os dispositivos de borda, como proxies, firewalls e assim por diante e elas se relacionam fluxos indo pela Internet e ExpressRoute de catálogo.

  - Se os usuários finais irão acessar os serviços do Office 365 via roteamento direct ou proxy de aplicativo indiretas para fluxos de Internet e ExpressRoute do documento.

- Adicionar o local do seu locatário e atender-me locais ao seu diagrama de rede.

- Estime as rede esperado e observado latência características de desempenho e de locais de usuário principal para o Office 365. Tenha em mente que o Office 365 é um conjunto global e distribuído de serviços e usuários se conectarão ao locais que podem ser diferentes do local de seus inquilinos. Por esse motivo, é recomendável para medir e otimizar a latência entre o usuário e a borda mais próxima da rede global da Microsoft através de conexões de ExpressRoute e a Internet. Você pode usar as descobertas de avaliação de rede para auxiliar com esta tarefa.

- Lista os requisitos de alta disponibilidade que precisam ser atendidos com a nova conexão ExpressRoute e segurança da rede de empresa. Por exemplo, como os usuários continuarão obter acesso ao Office 365 em caso da saída de Internet ou falha de circuito de ExpressRoute.

- Documento quais Office 365 de rede de entrada e saída flui usará o caminho da Internet e que usará ExpressRoute. As especificações de localizações geográficas dos seus usuários e os detalhes de sua topologia de rede local podem exigir o plano seja diferente do local de um usuário para outro.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>O tráfego de rede de entrada e saída do catálogo
<a name="trafficCatalog"> </a>

Para minimizar a complexidade de rede de roteamento e outros, é recomendável que você só use ExpressRoute para o Office 365 para os fluxos de tráfego de rede que são necessárias para passar por uma conexão dedicado devido aos requisitos normativos ou como resultado da avaliação de rede. Além disso, recomendamos que você deve preparar o escopo dos fluxos de tráfego de rede de entrada e saída de roteamento e a abordagem de ExpressRoute como diferentes e distintos estágios do projeto de implementação. Implantar ExpressRoute para Office 365 para o usuário apenas iniciadas fluxos de tráfego de rede de saída e deixe fluxos de tráfego de rede de entrada pela Internet podem ajudar a controlar o aumento no topológica complexidade e os riscos de apresentando adicionais assimétrica possibilidades de roteamento.
  
Seu catálogo de tráfego de rede deve conter listagens de todas as conexões de rede de entrada e saída que você vai ter entre sua rede local e a Microsoft.
  
- Fluxos de tráfego de rede de saída são quaisquer cenários onde uma conexão é iniciado do seu ambiente local, como os clientes internos ou servidores, com um destino dos serviços do Microsoft. Essas conexões podem ser diretas para o Office 365 ou indiretas, como quando a conexão passa servidores proxy, firewalls ou outros dispositivos de rede no caminho para o Office 365.

- Fluxos de tráfego de rede de entrada são quaisquer cenários onde uma conexão é iniciada de nuvem da Microsoft para um host local. Essas conexões geralmente precisam passar por meio do firewall e outra infraestrutura de segurança que requer a diretiva de segurança do cliente para fluxos de originado externamente.

Leia a seção **simetria da rota de garantia** do artigo [roteamento com ExpressRoute para o Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) para determinar quais serviços enviará o tráfego de entrada e procure a coluna marcada **ExpressRoute para o Office 365** no [Office 365 pontos de extremidade](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) artigo de referência para determinar o restante das informações de conectividade.
  
Para cada serviço que requer uma conexão de saída, você vai querer descrevem a conectividade planejada para o serviço, incluindo o roteamento de rede, a configuração de proxy, inspeção de pacotes, e precisa de largura de banda.
  
Para cada serviço que requer uma conexão de entrada, você precisará algumas informações adicionais. Servidores em nuvem da Microsoft estabelecerá conexões à sua rede local. para garantir que as conexões sejam feitas corretamente, você vai querer descrevem todos os aspectos dessa conectividade, inclusive; as entradas DNS públicas para os serviços que aceitarão essas conexões de entrada, o CIDR formatado endereços de IP de IPv4, qual equipamento ISP está envolvido, e como entrada de NAT ou fonte NAT é tratado para essas conexões.
  
Conexões de entrada devem ser revisadas independentemente se estiver se conectando pela internet ou ainda não foram introduzido ExpressRoute para garantir o roteamento assimétrico. Em alguns casos, local pontos de extremidade de serviços do Office 365 iniciam conexões de entrada para maio também precisam ser acessados por outros Microsoft e os serviços de não-Microsoft. É fundamental que habilitar ExpressRoute o roteamento para esses serviços para o Office 365 não quebra a outros cenários. Em muitos casos, os clientes, talvez seja necessário implementar as alterações específicas à sua rede interna, como fonte com base em NAT, para assegurar que os fluxos de entrada da Microsoft permaneçam simétricos após ExpressRoute está habilitado.
  
Aqui está um exemplo do nível de detalhes necessário. Nesse caso Exchange híbrido seria encaminhar para o sistema local via ExpressRoute.

|**Propriedade de Conexão**|**Valor**|
|:-----|:-----|
|**Direção do tráfego de rede** <br/> |entrada  <br/> |
|**Serviço** <br/> |Exchange híbrido  <br/> |
|**Público ponto de extremidade do Office 365 (origem)** <br/> |O Exchange Online (endereços IP)  <br/> |
|**Público ponto de extremidade de local (de destino)** <br/> |5.5.5.5  <br/> |
|**Entrada de (Internet) DNS pública** <br/> |Autodiscover.contoso.com  <br/> |
|**Será esse ponto de extremidade de local usado para por outros serviços da Microsoft (não - Office 365)** <br/> |Não  <br/> |
|**Neste ponto de extremidade de local será usado pelos usuários/sistemas na Internet** <br/> |Sim  <br/> |
|**Sistemas internos publicado por meio de pontos de extremidade públicos** <br/> |Função acesso para cliente do Exchange Server (local) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Anúncio de IP do ponto de extremidade público** <br/> |**Para Internet**: 5.5.0.0/16  <br/> **Para ExpressRoute**: 5.5.5.0/24  <br/> |
|**Controles de segurança/perímetro** <br/> |**Caminho de Internet**: DeviceID_002  <br/> **Caminho de ExpressRoute**: DeviceID_003  <br/> |
|**Alta disponibilidade** <br/> |Ativa/ativa entre 2 geograficamente redundante  <br/> ExpressRoute circuitos - Chicago e Dallas  <br/> |
|**Controle de simetria de caminho** <br/> |**Método**: NAT de origem  <br/> **Caminho de Internet**: origem NAT as conexões 192.168.5.5 de entrada  <br/> |**Caminho de ExpressRoute**: conexões de fonte NAT 192.168.1.0 (Chicago) e 192.168.2.0 (Dallas)  <br/> |

Aqui está um exemplo de um serviço que só é saído:

|**Propriedade de Conexão**|**Valor**|
|:-----|:-----|
|**Direção do tráfego de rede** <br/> |Saída  <br/> |
|**Serviço** <br/> |SharePoint Online  <br/> |
|**Ponto de extremidade de local (origem)** <br/> |Estação de trabalho do usuário  <br/> |
|**Público ponto de extremidade do Office 365 (de destino)** <br/> |SharePoint Online (endereços IP)  <br/> |
|**Entrada de (Internet) DNS pública** <br/> |\*. sharepoint.com (e FQDNs adicionais)  <br/> |
|**Referências de CDN** <br/> |CDN.sharepointonline.com (e FQDNs adicionais) - endereços IP mantidas por provedores CDN)  <br/> |
|**Anúncio de IP e NAT em uso** <br/> |**Caminho de Internet/NAT de origem**: 1.1.1.0/24  <br/> **Caminho de ExpressRoute/NAT de origem**: 1.1.2.0/24 (Chicago) e 1.1.3.0/24 (Dallas)  <br/> |
|**Método de conectividade** <br/> |**Internet**: por meio do proxy de camada 7 (arquivo. PAC)  <br/> **ExpressRoute**: direcionar circulação (nenhum proxy)  <br/> |
|**Controles de segurança/perímetro** <br/> |**Caminho de Internet**: DeviceID_002  <br/> **Caminho de ExpressRoute**: DeviceID_003  <br/> |
|**Alta disponibilidade** <br/> |**Caminho de Internet**: saída do internet redundantes  <br/> **Caminho de ExpressRoute**: ativa/ativa 'quente Batata' roteamento entre 2 circuitos ExpressRoute geograficamente redundante - Chicago e Dallas  <br/> |
|**Controle de simetria de caminho** <br/> |**Método**: NAT para todas as conexões de fonte  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Design de sua topologia de rede com conectividade regional
<a name="topology"> </a>

Depois que você entende os serviços e seus fluxos de tráfego de rede associado, você pode criar um diagrama de rede que incorpora esses novos requisitos de conectividade e ilustra as alterações que você fará para usar ExpressRoute para o Office 365. O diagrama deve incluir:
  
1. Onde o Office 365 e outros serviços serão acessados de todos os locais de usuário.

2. Todos os pontos de saída ExpressRoute e da internet.

3. Dispositivos de saída e de entrada todos os que gerenciam a conectividade dentro e fora da rede, inclusive roteadores, firewalls, servidores de proxy de aplicativo e detecção de intrusão/prevenção.

4. Destinos internos para todo o tráfego de entrada, como os servidores internos do ADFS que aceitar conexões de servidores de proxy de aplicativo da web do ADFS.

5. Catálogo de todas as sub-redes IP que será anunciado

6. Identifique cada local onde as pessoas serão acessar o Office 365 de e listar o reunir-me locais que serão usados para ExpressRoute.

7. Locais e partes de sua topologia de rede interna, onde os prefixos de IP Microsoft aprendidos ExpressRoute serão aceitas, filtrados e propagadas para.

8. A topologia de rede deve ilustram a localização geográfica de cada segmento de rede e como ele se conecta à rede Microsoft via ExpressRoute e/ou a Internet.

O diagrama abaixo mostra cada local onde as pessoas usarão Office 365 de junto com os anúncios de roteamento de entrada e saídos para o Office 365.
  
![Reunir geográfica regional de ExpressRoute-me](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Para tráfego de saída, as pessoas acessar o Office 365 em uma destas três formas:
  
1. Por meio de uma reunião-me local na América do Norte para as pessoas na Califórnia.

2. Por meio de uma reunião-me local em Hong Kong para as pessoas em Hong Kong.

3. Através da internet, em Bangladesh onde há menos pessoas e nenhum circuito ExpressRoute provisionado.

![Conexões de saída para o diagrama regional](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
Da mesma forma, o tráfego de rede de entrada do Office 365 retorna uma destas três formas:
  
1. Por meio de uma reunião-me local na América do Norte para as pessoas na Califórnia.

2. Por meio de uma reunião-me local em Hong Kong para as pessoas em Hong Kong.

3. Através da internet, em Bangladesh onde há menos pessoas e nenhum circuito ExpressRoute provisionado.

![Conexões de entrada para o diagrama regional](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Determinar o reunir apropriado-me local

A seleção de reunir-me locais, que são o local físico onde o seu circuito ExpressRoute conecta sua rede à rede Microsoft, é influenciada pelos locais onde as pessoas irão acessar o Office 365 de. Como uma oferta de SaaS, o Office 365 não funcionam sob o modelo regional IaaS ou PaaS da mesma maneira que o Azure faz. Em vez disso, o Office 365 é um conjunto de distribuída dos serviços de colaboração, onde os usuários talvez precisem se conectar aos pontos de extremidade em vários data centers e regiões, que não estejam necessariamente no mesmo local ou na região onde o locatário do usuário está hospedado.
  
Isso significa que a consideração mais importante que você precisa tomar ao selecionar reunir-me locais para ExpressRoute para o Office 365 é onde as pessoas na sua organização se conectarão de. A recomendação geral para melhor conectividade do Office 365 é implementar o roteamento, para que as solicitações de usuário para serviços do Office 365 são entregues no Microsoft network sobre o caminho mais curto de rede, isso é também está sendo conhecido como 'quente Batata' roteamento. Por exemplo, se a maioria dos usuários do Office 365 em um ou dois locais, selecionando reunir-me locais que estão o próximo até o local desses usuários criará o design ideal. Se sua empresa tiver população de grande de usuários em diferentes regiões muitos, convém considerar tendo vários circuitos ExpressRoute e atender-me locais. Para alguns dos seus locais do usuário, o caminho mais curto/mais ideal em Microsoft network e o Office 365, talvez não seja por meio de sua reunião interna de WAN e ExpressRoute-me points, mas através da Internet.
  
Muitas vezes, há vários reunir-me locais que pôde ser selecionados dentro de uma região com proximidade relativa para seus usuários. Preencha a tabela a seguir para guiá-suas decisões.

|**Reunir planejada de ExpressRoute-me locais no Califórnia e Nova York**||
|:-----|:-----|
|Localidade  <br/> |Número de pessoas  <br/> |Esperado latência à rede Microsoft sobre a saída da Internet  <br/> |Latência esperada à rede Microsoft sobre ExpressRoute  <br/> |
|Los Angeles  <br/> |10.000  <br/> |~ 15 MS  <br/> |~ 10 ms (via vale do silício)  <br/> |
|Washington DC  <br/> |15.000  <br/> |~ 20 MS  <br/> |~ 10 ms (por meio de Nova York)  <br/> |
|Dallas  <br/> |5.000  <br/> |~ 15 MS  <br/> |~ 40ms (por meio de Nova York)  <br/> |

Depois que a arquitetura de rede global mostrando a região do Office 365, reunir de provedor de serviços de rede ExpressRoute-me locais e a quantidade de pessoas por local foi desenvolvido, ele pode ser usado para identificar se qualquer otimizações podem ser feitas. Pode também mostrar global hairpin conexões de rede onde o tráfego roteia a uma localização distante para obter o reunir-me local. Se um hairpin na rede global foi descoberto, que ele deve ser remediado antes de continuar. Localizar outro reunir-me local ou usar seletiva Internet inovador saída pontos para evitar a "hairpin".
  
O primeiro diagrama, mostra um exemplo de um cliente com dois locais físicos na América do Norte. Você pode ver as informações sobre os diversos escritórios, locais de Inquilino do Office 365, e atendem a várias opções para ExpressRoute-me locais. Neste exemplo, o cliente tenha selecionado o reunir-me local com base em dois princípios, na ordem:
  
1. Próximo a pessoas na sua organização.

2. Mais próximos próximos de um datacenter da Microsoft onde o Office 365 está hospedado.

![Reunir geográfica de ExpressRoute US-me](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Expandindo desse conceito um pouco mais, mostra o diagrama segundo um cliente de exemplo multinacionais enfrentado com informações semelhantes e tomada de decisões. Esse cliente tem uma pequena empresa em Bangladesh com uma pequena equipe de dez pessoas focados no crescimento suas Pegadas na região. Não há um reunir-me local em Chennai e um datacenter da Microsoft com o Office 365 hospedados em Chennai tão atenderem aos-me local faria sentido; No entanto, para dez pessoas, a despesa de circuito adicional é fatigante. Ao olhar para a sua rede, você precisará determinar se a latência envolvidos em enviar o tráfego de rede através de sua rede é mais eficiente do que a letra maiuscula para adquirir outro circuito de ExpressRoute de gastos.
  
Como alternativa, as dez pessoas em Bangladesh perceba um melhor desempenho com o tráfego de rede enviado pela internet à rede Microsoft que seria roteamento em sua rede interna, como podemos mostraram nos diagramas a introdutório e reproduzida abaixo.
  
![Conexões de saída para o diagrama regional](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Criar sua ExpressRoute para o plano de implementação do Office 365
<a name="implementation"> </a>

Seu plano de implementação deve abranger os detalhes técnicos de configuração ExpressRoute, bem como os detalhes de configuração da outra infra-estrutura em sua rede, como o seguinte.
  
- Planeje quais serviços divididos entre ExpressRoute e a Internet.

- Planejar a largura de banda, segurança, alta disponibilidade e failover.

- Projetar a entrada e saída roteamento, incluindo as otimizações de caminho de roteamento apropriada para locais diferentes

- Decidir quanto ExpressRoute rotas serão anunciadas em sua rede e qual é o mecanismo para clientes selecionar um caminho de Internet ou ExpressRoute; Por exemplo, direcione o proxy de aplicativo ou de roteamento.

- Planeje a alteração de registro de DNS, incluindo as entradas de [Estrutura de política do remetente](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) .

- Planejar a estratégia NAT, incluindo a fonte de entrada e saída NAT.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planejar seu roteamento com a internet e caminhos de rede ExpressRoute
<a name="paths"> </a>

- Para sua implantação inicial, todos os serviços de entrada, como o email de entrada ou conectividade híbrida, são recomendados para usar a internet.

- Planeje o usuário final cliente LAN roteamento, como [Configurar um arquivo de PAC/WPAD](https://aka.ms/manageo365endpoints), rota padrão, servidores proxy e anúncios de rota BGP.

- Planeje o roteamento de perímetro, incluindo servidores proxy, firewalls e proxies de nuvem.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planejar a largura de banda, segurança, alta disponibilidade e failover
<a name="availability"> </a>

Crie um plano para a largura de banda necessária para cada carga de trabalho principal do Office 365. Estime separadamente Exchange Online, SharePoint Online e Skype para requisitos de largura de banda Business Online. Você pode usar as calculadoras de estimativa que fornecemos para Exchange Online e Skype para negócios como um ponto de partida; No entanto, um teste piloto com um exemplo representativo de perfis de usuário e locais é necessário para entender completamente as necessidades de largura de banda da sua organização.
  
Adicionar como a segurança é tratada em cada internet e ExpressRoute saída local para seu plano, lembre-se todas as conexões de ExpressRoute para o Office 365 usam a correspondência de público e ainda devem ser protegidas de acordo com suas políticas de segurança da empresa da conexão a externo redes.
  
Adicione detalhes a seu plano sobre quais pessoas serão afetadas pela qual tipo de interrupção e como as pessoas poderão realizar seus trabalhos em plena capacidade da maneira mais simples.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planejar requisitos de largura de banda, incluindo Skype para requisitos de negócios em tremulação, latência, congestionamento e espaço reserva
  
Skype para Business Online também tem requisitos de rede adicionais específicas quais são descritos no artigo [qualidade de mídia e o desempenho da conectividade de rede em Skype para negócios Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Leia a seção **planejamento de largura de banda para ExpressRoute do Windows Azure** no [planejamento de rede com ExpressRoute para o Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Ao realizar uma avaliação de largura de banda com seus usuários piloto, você pode usar o nosso guia; [Ajuste de desempenho de office 365 usando linhas de base e histórico de desempenho](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planejar requisitos de alta disponibilidade
  
Crie um plano para alta disponibilidade atender às suas necessidades e incorporá-los a seu diagrama de topologia de rede atualizado. Leia a seção de **alta disponibilidade e failover com ExpressRoute do Windows Azure** no [planejamento de rede com ExpressRoute para o Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planejar requisitos de segurança de rede
  
Crie um plano para atender às suas necessidades de segurança de rede e incorporá-los a seu diagrama de topologia de rede atualizado. Leia a seção **Applying controles de segurança para o Windows Azure ExpressRoute para cenários do Office 365** no [planejamento de rede com ExpressRoute para o Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Conectividade de saída do serviço de design
<a name="outbound"> </a>

ExpressRoute para o Office 365 tem requisitos de rede de *saída* que podem estar familiarizados. Especificamente, os endereços IP que representam os seus usuários e redes para o Office 365 e a atuam como os pontos de extremidade de origem para conexões de rede de saída para a Microsoft devem seguir os requisitos específicos descritos abaixo.
  
1. Os pontos de extremidade devem ser endereços IP públicos, que são registrados para sua empresa ou operadora fornecendo conectividade ExpressRoute a você.

2. Os pontos de extremidade devem ser anunciado à Microsoft e validado/aceitos pelo ExpressRoute.

3. Os pontos de extremidade não devem ser anunciados para a Internet com a métrica de roteamento do mesma ou mais preferencial.

4. Os pontos de extremidade não devem ser usados para conectividade com o Microsoft services que não sejam configuradas pela ExpressRoute.

Se o seu design de rede não atender a esses requisitos, há um alto risco em que os usuários observarão falhas de conectividade para o Office 365 e outros serviços da Microsoft devido à rota preto buraco ou roteamento assimétrico. Esse problema ocorre quando as solicitações para os serviços Microsoft são roteadas pela ExpressRoute, mas as respostas serão ignoradas pelo dispositivos de rede com estado, como firewalls e respostas são roteadas de volta pela internet, ou vice-versa.
  
O método mais comum que você pode usar para atender aos requisitos acima é usar NAT, implementados como parte da sua rede ou fornecidos pela sua operadora ExpressRoute de origem. Fonte NAT permite que abstrai os detalhes e endereçamento IP privado da sua rede de internet do ExpressRoute e; juntamente com anúncios de rota IP adequados, fornecem um mecanismo simples para garantir simetria de caminho. Se você estiver usando dispositivos de rede com estado que são específicos para locais de correspondência ExpressRoute, você deve implementar os pools NAT separados para cada ExpressRoute correspondência para garantir simetria de caminho.
  
Leia mais sobre os [requisitos de NAT ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-nat/).
  
Adicione as alterações para a conectividade de saída para o diagrama de topologia de rede.
  
### <a name="design-inbound-service-connectivity"></a>Projetar a conectividade do serviço de entrada
<a name="inbound"> </a>

A maioria das implantações empresariais Office 365 pressupõem alguma forma de conectividade de entrada do Office 365 para serviços no local, como para o Exchange, SharePoint e Skype para cenários híbridos corporativos, migrações de caixa de correio e a autenticação usando o ADFS infraestrutura. Quando ExpressRoute você ativar um caminho de roteamento adicional entre sua rede local e a Microsoft para conectividade de saída, essas conexões de entrada inadvertidamente podem ser afetadas pelo roteamento assimétrico, mesmo se você pretende ter esses fluxos continuam a Use a Internet. Algumas precauções descritas a seguir são recomendadas para garantir que não há nenhum impacto para Internet baseada em fluxos de entrada do Office 365 para sistemas de local.
  
Para minimizar os riscos de roteamento assimétrico para fluxos de tráfego de rede de entrada, todas as conexões de entrada devem usar fonte NAT antes que eles estiver roteados em segmentos de rede que têm roteamento visibilidade ExpressRoute. Se as conexões de entrada são permitidas em um segmento de rede com roteamento visibilidade ExpressRoute sem fonte NAT, as solicitações originadas do Office 365 irá inserir da internet, mas a resposta voltando ao Office 365 será preferem o ExpressRoute caminho de rede voltar à rede Microsoft, fazendo com que o serviço de roteamento assimétrico.
  
Você pode considerar a um dos seguintes padrões de implementação para atender a esse requisito:
  
1. Executar fonte NAT antes de solicitações são roteadas para a rede interna usando o equipamento de rede, como firewalls ou balanceadores no caminho de carga da Internet aos seus sistemas locais.

2. Certifique-se de que as rotas de ExpressRoute não sejam propagadas para os segmentos de rede onde os serviços de entrada, como frente encerrar servidores ou reverso sistemas de proxy, manipulação Internet conexões residem.

Explicitamente accounting para esses cenários em sua rede e mantendo todo o tráfego de rede de entrada ao redor ajuda a Internet para minimizar o risco operacional de roteamento assimétrico e implantação.
  
Pode haver casos em que você pode escolher para direcionar alguns fluxos de entrada através de conexões de ExpressRoute. Para esses cenários, tome as seguintes considerações adicionais em consideração.
  
1. O Office 365 pode apenas destino local pontos de extremidade que usam IPs pública. Isso significa que, mesmo se o ponto de extremidade de entrada é exposto somente para o Office 365 via ExpressRoute no local, ele ainda precisa ter IP público associado a ela.

2. Resolução de nomes DNS que os serviços do Office 365 executam para resolver pontos de extremidade de local acontecer usando DNS público. Isso significa que você deve registrar o FQDN dos pontos de extremidade da entrada de serviço para mapeamentos de IP na Internet.

3. Para receber conexões de rede de entrada pela ExpressRoute, as subredes de IP públicas para esses pontos de extremidade devem ser para ser divulgado à Microsoft sobre ExpressRoute.

4. Avaliar com cuidado esses fluxos de tráfego de rede de entrada para garantir a segurança adequada e controles de rede são aplicados a eles de acordo com suas diretivas de rede e segurança da empresa.

5. Uma vez seu pontos de extremidade de entrada são anunciados à Microsoft sobre ExpressRoute no local, ExpressRoute efetivamente se tornará o caminho de roteamento preferencial para esses pontos de extremidade para todos os serviços da Microsoft, incluindo o Office 365. Isso significa que as sub-redes de ponto de extremidade devem ser usadas apenas para comunicação com os serviços do Office 365 e nenhum outro serviço do Microsoft Network. Caso contrário, seu design fará o roteamento assimétrico onde as conexões de entrada a partir de outros serviços preferem rotear da Microsoft entrada sobre ExpressRoute, enquanto o caminho de retorno usará a Internet.

6. No evento um ExpressRoute por circuito ou reunir-me local está inativo, você precisará garantir a organização local pontos de extremidade de entrada ainda estão disponíveis para aceitar solicitações através de um caminho de rede separado. Isso pode significar sub-redes publicidade para esses pontos de extremidade por meio de vários circuitos ExpressRoute.

7. Recomendamos a aplicação de origem NAT para todos os fluxos de tráfego de rede de entrada entrar em sua rede por meio de ExpressRoute, especialmente quando esses fluxos cruzar os dispositivos de rede com estado, como firewalls.

8. Alguns serviços no local, como proxy ADFS ou descoberta automática do Exchange, poderão receber as solicitações de entrada dos usuários da Internet e serviços do Office 365. Para essas solicitações Office 365 será direcionar o mesmo FQDN que solicitações de usuário pela Internet. Permitindo que as conexões de entrada do usuário da internet para os pontos de extremidade de local, ao forçar conexões do Office 365 para usar ExpressRoute, representa a complexidade de roteamento significativa. Para a maioria dos clientes, a implementação de nesses cenários complexos sobre ExpressRoute não é recomendada devido às considerações operacionais. Essa sobrecarga adicional inclui, gerenciar os riscos de roteamento assimétrico e exige que você gerenciar cuidadosamente anúncios de roteamento e diretivas entre várias dimensões.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Atualizar o seu plano de topologia de rede para mostrar como você faria evitar rotas assimétricas
<a name="asymmetric"> </a>

Você deseja evitar roteamento assimétrico para garantir que as pessoas na sua organização podem usar perfeitamente Office 365, bem como outros serviços importantes na internet. Há duas configurações comuns os clientes têm que causam o roteamento assimétrico. Agora é um bom momento para examinar a configuração de rede que você estiver planejando usar e verifique se um desses cenários de roteamento assimétricos pode existir.
  
Para começar, vai examinamos algumas situações diferentes associadas com o seguinte diagrama de rede. Neste diagrama, todos os servidores que receber solicitações de entrada, como ADFS ou local híbrido servidores estão no data center Nova Jersey e são anunciadas à internet.
  
1. Embora a rede de perímetro seja segura, não NAT fonte está disponível para solicitações de entrada.

2. Os servidores no data center Nova Jersey são poderá ver a internet e ExpressRoute rotas.

![Visão geral da conectividade ExpressRoute](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Também temos sugestões sobre como corrigi-los.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problema 1: Nuvem para conexão local pela Internet
  
O diagrama a seguir ilustra o caminho de rede assimétrica tomado quando sua configuração de rede não fornece NAT para solicitações de entrada de nuvem da Microsoft pela internet.
  
1. A solicitação de entrada do Office 365 recupera o endereço IP do ponto de extremidade de local de DNS público e envia a solicitação à sua rede de perímetro.

2. Nesta configuração defeituoso, não há nenhuma NAT fonte configurado ou disponível na rede de perímetro onde o tráfego estiver resultando enviado no IP de origem real de endereços que está sendo usado como o destino de retorno.

  - O servidor em sua rede roteia o tráfego de retorno para o Office 365 através de qualquer conexão de rede ExpressRoute disponível.

  - O resultado é um caminho assimétrico para aquele fluxo para o Office 365, resultando em uma conexão desfeito.

![Problema de roteamento ExpressRoute Asymetric 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>1a solução: NAT de origem
  
Simplesmente adicionando uma fonte de NAT à solicitação de entrada resolve esta rede configurado incorretamente. Neste diagrama:
  
1. A solicitação de entrada continua insiram pela rede de perímetro a nova Jersey do data center. Neste momento NAT de origem está disponível.

2. A resposta das rotas de servidor em direção a IP associados a NAT fonte, em vez do endereço IP original, resultando na resposta retornando ao longo do mesmo caminho de rede.

![Solução de roteamento ExpressRoute Asymetric 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Solução 1b: roteiro de escopo
  
Como alternativa, você pode optar por não permitir que o BGP ExpressRoute prefixos para ser divulgado, removendo o caminho de rede alternativo para os computadores. Neste diagrama:
  
1. A solicitação de entrada continua insiram pela rede de perímetro a nova Jersey do data center. Nesse momento os prefixos divulgados da Microsoft via circuito ExpressRoute não estão disponíveis para o Centro de dados da Nova Jersey.

2. A resposta das rotas de servidor em direção a IP associados com o endereço IP original em relação à rota somente disponível, resultando na resposta retornando ao longo do mesmo caminho de rede.

![Solução de roteamento ExpressRoute Asymetric 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problema 2: Nuvem para conexão de local sobre ExpressRoute
  
O diagrama a seguir ilustra o caminho de rede assimétrica tomado quando sua configuração de rede não fornece NAT para solicitações de entrada de nuvem da Microsoft via ExpressRoute.
  
1. A solicitação de entrada do Office 365 recupera o endereço IP do DNS e envia a solicitação à sua rede de perímetro.

2. Nesta configuração defeituoso, não há nenhuma NAT fonte configurado ou disponível na rede de perímetro onde o tráfego estiver resultando enviado no IP de origem real de endereços que está sendo usado como o destino de retorno.

  - O computador em sua rede roteia o tráfego de retorno para o Office 365 através de qualquer conexão de rede ExpressRoute disponível.

  - O resultado é uma conexão assimétrica para o Office 365.

![Problema de roteamento ExpressRoute Asymetric 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Solução 2: Origem NAT
  
Simplesmente adicionando uma fonte de NAT à solicitação de entrada resolve esta rede configurado incorretamente. Neste diagrama:
  
1. A solicitação de entrada continua insiram pela rede de perímetro do Centro de dados de Nova York. Neste momento NAT de origem está disponível.

2. A resposta das rotas de servidor em direção a IP associados a NAT fonte, em vez do endereço IP original, resultando na resposta retornando ao longo do mesmo caminho de rede.

![Solução de roteamento ExpressRoute Asymetric 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Papel, verifique se o design de rede possui simetria de caminho

Neste ponto, você precisará verificar em papel que seu plano de implementação oferece simetria da rota para os diferentes cenários nos quais você vai usando o Office 365. Você vai identificar a rota de rede específico esperada a ser executada quando uma pessoa utiliza diferentes recursos do serviço. Da rede local e roteamento de WAN, para os dispositivos de perímetro, como o caminho de conectividade; ExpressRoute ou a internet e para a conexão ao ponto de extremidade online.
  
Você precisará fazer isso para todos os serviços de rede do Office 365 que estavam anteriormente identificados como serviços que sua organização adotará.
  
Ele ajuda a fazer essa paper passagem de rotas com uma segunda pessoa. Explique a eles onde cada salto de rede é esperado para obter sua próxima rota da e certifique-se de que você está familiarizado com os caminhos de roteamento. Lembre-se de que ExpressRoute sempre fornecerá uma rota mais com escopo para endereços IP do servidor do Microsoft dando a ele um custo menor de rota que uma rota padrão de Internet.
  
### <a name="design-client-connectivity-configuration"></a>Configuração de conectividade de cliente de design
<a name="asymmetric"> </a>

![Usando arquivos de PAC com ExpressRoute](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Se você estiver usando um servidor proxy para internet acoplado tráfego você precisa ajustar qualquer PAC ou arquivos de configuração do cliente para garantir que os computadores clientes em sua rede estão configurados corretamente para enviar o tráfego de ExpressRoute desejado para o Office 365 sem transiting seu servidor proxy e o tráfego restante, incluindo alguns tráfego do Office 365, é enviada ao proxy relevante. Leia nosso guia sobre como [gerenciar pontos de extremidade do Office 365](https://aka.ms/manageo365endpoints) por exemplo arquivos PAC.
  
> [!NOTE]
> Os pontos de extremidade alterar com frequência, quantas vezes por semana. Você só deve fazer alterações de acordo com os serviços e recursos que sua organização tenha adotado para reduzir o número de alterações, que você deve certificar permaneçam atual. Preste atenção close à **Data efetiva** no RSS feed onde as alterações são anunciadas e um registro é mantido de todas as antigas alterações, IP endereços que são anunciados pode não ser divulgada ou removida do anúncio, até a data efetiva for atingida.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Construir sua implantação e os procedimentos de teste
<a name="testing"> </a>

Seu plano de implementação deve incluir tanto testes e planejamento de reversão. Se sua implementação não está funcionando conforme o esperado, o plano deve ser projetado para afetar o menor número de pessoas antes de que são detectados problemas. Estes são alguns princípios de alto níveis que seu plano deve ser considerados.
  
1. Preparar a rede segmento e usuário serviço inclusão para minimizar a interrupção.

2. Plano para testar a rotas com traceroute e TCP se conectam a partir de um host de conectadas internet separado.

3. De preferência, o teste dos serviços de entrada e saídos deve ser feita em uma rede de teste isolado com um locatário de teste o Office 365.

      - Como alternativa, teste pode ser executado em uma rede de produção se o cliente ainda não estiver usando o Office 365 ou está em piloto.

      - Como alternativa, teste pode ser executadas durante uma interrupção de produção que está reservada para teste e monitoramento apenas.

      - Como alternativa, o teste pode ser feito verificando rotas para cada serviço em cada nó do roteador de camada 3. Este retorno ao estado só deve ser usado se nenhum outro teste for possível, pois uma falta de teste físico introduz riscos.

### <a name="build-your-deployment-procedures"></a>Crie os procedimentos de implantação

Os procedimentos de implantação devem distribuir para pequenos grupos de pessoas em estágios para permitir testes antes de implantar a maiores grupos de pessoas. A seguir estão várias maneiras de preparar a implantação do ExpressRoute.
  
1. Configurar ExpressRoute com correspondência da Microsoft e têm os anúncios de rota encaminhados para um único host apenas para fins de teste de preparo.

2. Anunciar rotas à rede ExpressRoute para um único segmento de rede em um primeiro momento e expanda anúncios de rota por segmento de rede ou a região.

3. Se implantar o Office 365 pela primeira vez, use a implantação de rede ExpressRoute como um piloto para um pequeno número de pessoas.

4. Se estiver usando servidores proxy, você pode configurar como alternativa um arquivo de PAC de teste para direcionar um pequeno número de pessoas para ExpressRoute com comentários e teste antes de adicionar mais.

Seu plano de implementação deve listar cada um dos procedimentos de implantação que devem ser seguidos ou comandos que precisam ser usados para implantar a configuração de rede. Quando chega a hora de interrupção da rede todas as alterações que está sendo feita deve estar entre o plano de implantação redigidas que foi escrito com antecedência e o ponto revisado. Consulte nossa orientação sobre a configuração técnica dos ExpressRoute.
  
- Atualizando seus registros SPF TXT, se você alterou os endereços IP para todos os servidores no local que continuarão a enviar email.

- Atualizando quaisquer entradas DNS para servidores locais, se você alterou os endereços IP para acomodar uma nova configuração de NAT.

- Certifique-se de que você se inscreveu no RSS feed para notificações de ponto de extremidade do Office 365 manter as configurações de roteamento ou proxy.

Após a conclusão da sua implantação ExpressRoute os procedimentos no plano de teste devem ser executados. Resultados para cada procedimento devem estar conectados. Você deve incluir procedimentos para a reversão para o ambiente de produção original no caso os resultados do plano de teste indicam que a implementação não foi bem-sucedida.
  
### <a name="build-your-test-procedures"></a>Crie os procedimentos de teste

Os procedimentos de testes devem incluir testes para cada serviço de rede de entrada e saída para o Office 365 que usarão ExpressRoute e aquelas que não. Os procedimentos devem incluir o teste de cada local de rede exclusivo incluindo os usuários que não são local em da LAN corporativa.
  
Alguns exemplos de atividades de teste incluem o seguinte.
  
1. Ping de seu roteador local ao seu roteador de operador de rede.

2. Valide a 500 + Office 365 e CRM Online endereço IP anúncios são recebidos pelo seu roteador local.

3. Validar sua entrada e saída NAT está funcionando entre ExpressRoute e a rede interna.

4. Valide que rotas para seu NAT estão sendo anunciadas do seu roteador.

5. Valide que ExpressRoute aceitou suas prefixos anunciados.

      - Use o cmdlet a seguir para verificar os anúncios de correspondência:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Valide a seu público IP NAT de intervalo não é anunciado para a Microsoft por meio de qualquer outro ExpressRoute ou circuito de rede de Internet público, a menos que é um subconjunto específico de um intervalo maior como no exemplo anterior.

7. ExpressRoute circuitos estiver emparelhados, validar que as sessões BGP estejam em execução.

8. Configurar um único host no interior da sua NAT e use ping, tracert e tcpping para testar a conectividade entre o novo circuito para o outlook.office365.com de host. Como alternativa, você poderia usar uma ferramenta como Wireshark ou Microsoft Network Monitor 3.4 em uma porta espelhada para o MSEE para validar que você está capazes de se conectar ao endereço IP associado ao outlook.office365.com.

9. Testar a funcionalidade de nível de aplicativo para o Exchange Online.

  - Testar o Outlook é capaz de se conectar ao Exchange Online e envio/recebimento de email.

  - Testar o Outlook é capaz de usar o modo online.

  - Testar a capacidade de conectividade e envio/recebimento do smartphone.

10. Testar a funcionalidade de nível de aplicativo para o SharePoint Online

  - Teste OneDrive para o cliente de sincronização de negócios.

  - Testar o acesso de web do SharePoint Online.

11. Testar funcionalidade de nível de aplicativo para Skype para cenários de chamada de negócios:

  - Ingresse como usuário autenticado [convidar iniciada pelo usuário final] a chamada em conferência.

  - Convide o usuário para a chamada em conferência [convidar enviada de MCU].

  - Ingressar em conferências como usuário anônimo usando o Skype para aplicativo web de negócios.

  - Ingressar em chamadas de sua conexão com fio do PC, telefone IP e dispositivo móvel.

  - Chamada para o usuário federado chamada para validação de PSTN: chamada for concluída, a qualidade da chamada é aceitável, tempo de conexão é aceitável.

  - Verifique se foi atualizado para ambos os membros do inquilino de status de presença dos contatos e usuários federados.

### <a name="common-problems"></a>Problemas comuns

Roteamento assimétrico é o problema de implementação mais comum. Aqui estão algumas fontes comuns para procurar por:
  
- Usando uma topologia de roteamento de rede aberto ou flat sem NAT no local de origem.

- Não usando SNAT para rotear para entrada serviços através da internet e o ExpressRoute conexões.

- Testando não serviços de entrada no ExpressRoute em uma rede de teste antes de implantar amplamente.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Implantando ExpressRoute a conectividade através de sua rede
<a name="testing"> </a>

Preparar sua implantação para um segmento de rede ao mesmo tempo, aplicação progressivamente a conectividade para diferentes partes da rede com um plano para reverter para cada novo segmento de rede. Se sua implantação está alinhada com uma implantação do Office 365, implantar para seus usuários piloto do Office 365 primeiro e estender a partir daí.
  
Primeiro para o seu teste e, em seguida, para a produção:
  
- Execute as etapas de implantação para habilitar ExpressRoute.

- Teste sua vejam que as rotas de rede são conforme o esperado.

- Execute o teste de cada serviço de entrada e saído.

- Reversão, se você descobrir quaisquer problemas.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Configurar uma conexão de teste para ExpressRoute com um segmento de rede de teste

Agora que você tem o plano completo em papel é tempo para testar em uma pequena escala. Esse teste você estabelecerá uma conexão ExpressRoute único com Microsoft Peering a uma sub-rede de teste em sua rede local. Você pode configurar um [locatário avaliação do Office 365](https://go.microsoft.com/fwlink/p/?LinkID=403802) com conectividade para e da sub-rede do teste e incluir todos os serviços de entrada e saídos que será utilizada na produção da sub-rede de teste. Configurar o DNS para o segmento de rede de teste e estabelecer todos os serviços de entrada e saídos. Executar o seu plano de teste e certifique-se de que você está familiarizado com o roteamento para cada serviço e a propagação da rota.
  
### <a name="execute-the-deployment-and-test-plans"></a>Execute os planos de implantação e teste

À medida que concluir os itens descritos acima, desmarque as áreas você concluir e garantir que você e sua equipe revisá-las antes de executá-lo a implantação e testar planos.
  
- Lista de serviços de entrada e saídas que estão envolvidos na alteração de rede.

- Diagrama de arquitetura de rede global mostrando a saída de internet e o ExpressRoute reunir-me locais.

- Diagrama do roteamento de rede demonstrando os caminhos de rede diferente, usados para cada serviço implantado.

- Um plano de implantação com etapas para implementar as alterações e reversão, se necessário.

- Um plano de teste para testar cada serviço de rede e do Office 365.

- Concluída a validação de papel de rotas de produção para serviços de entrada e saídas.

- Um teste concluído em um segmento de rede de teste incluindo testes de disponibilidade.

Escolha uma janela de interrupção que é grande o suficiente para ser executado por meio do plano de implantação inteira e o plano de teste, tem algum tempo disponível para solução de problemas e o tempo para a distribuição novamente caso seja necessário.
  
> [!CAUTION]
> Devido à natureza complexa do roteamento pela internet e ExpressRoute, é recomendável que o tempo de buffer adicionais seja adicionado a esta janela para lidar com roteamento complexo de solução de problemas.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Configurar QoS do Skype para negócios Online

QoS é necessário obter os benefícios de voz e reunião Skype para negócios Online. Após certificar-se de que a conexão de rede ExpressRoute não bloqueie qualquer um dos seu outro acesso de serviço do Office 365, você pode configurar QoS. Configuração de QoS é descrita no artigo [ExpressRoute e QoS em Skype para negócios Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .
  
## <a name="troubleshooting-your-implementation"></a>A implementação da solução de problemas
<a name="troubleshooting"> </a>

O primeiro lugar, a aparência é as etapas neste guia de implementação, foram qualquer perdidas no seu plano de implementação? Volte e executar o teste se possível para replicar o erro e depurá-lo lá de rede de pequeno.
  
Identifica quais entrada ou saída serviços falha durante o teste. Obtenha especificamente os endereços IP e sub-redes para cada um dos serviços que falhou. Vá em frente e Oriente o diagrama de topologia de rede em papel e validar o roteamento. Validar especificamente onde o roteamento de ExpressRoute é anunciado para, esse roteamento durante a interrupção se possível com os rastreamentos de teste.
  
Execute PSPing com um rastreamento de rede para cada ponto de extremidade do cliente e avaliar os endereços IP de origem e destino para validar que estão conforme o esperado. Execute o telnet para qualquer host de correio que você exponha na porta 25 e verificar que o SNAT é ocultar o endereço IP de origem original se isso é esperado.
  
Tenha em mente que, ao mesmo tempo em que implantar o Office 365 com uma conexão de ExpressRoute, que você precisará garantir a configuração de rede para ExpressRoute foi projetado de forma ideal e você também tiver otimizado os outros componentes em sua rede, como computadores cliente. Além de usar este guia de planejamento para solucionar as etapas que você possa ter perdido, podemos também tenha escrito um [plano para o Office 365 de solução de problemas de desempenho](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .
  
Aqui está um link curto que você pode usar para voltar: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>Tópicos relacionados

[Conectividade de rede para Office 365](network-connectivity.md)
  
[Microsoft Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Como gerenciar o ExpressRoute para a conectividade do Office 365](managing-expressroute-for-connectivity.md)
  
[Como rotear com o ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planejamento de rede com o ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Como usar comunidades do BGP no ExpressRoute para cenários do Office 365 (visualização)](bgp-communities-in-expressroute.md)
  
[Qualidade da mídia e desempenho de conectividade de rede no Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Como otimizar a sua rede para o Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute e QoS no Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Fluxo de chamadas usando o ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho](performance-tuning-using-baselines-and-history.md)
  
[Plano de solução de problemas de desempenho do Office 365](performance-troubleshooting-plan.md)
  
[URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Rede do Office 365 e ajuste de desempenho](network-planning-and-performance.md)
