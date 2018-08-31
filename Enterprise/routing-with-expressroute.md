---
title: Como rotear com o ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/7/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Para entender o tráfego de roteamento para o Office 365 usando o Windows Azure ExpressRoute corretamente, você precisará de uma noção exata dos requisitos de roteamento ExpressRoute principais a ExpressRoute circuitos e domínios de roteamento. Essas dispor os fundamentos para usar ExpressRoute dependerão os clientes do Office 365.
ms.openlocfilehash: e80ce78c0b229881349a4d02c7708fb9509748a9
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539184"
---
# <a name="routing-with-expressroute-for-office-365"></a>Como rotear com o ExpressRoute para Office 365

Para entender o tráfego de roteamento para o Office 365 usando o Windows Azure ExpressRoute corretamente, você precisará de uma noção exata de núcleo [ExpressRoute requisitos de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-routing/) e [ExpressRoute circuitos e domínios de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/). Essas dispor os fundamentos para usar ExpressRoute dependerão os clientes do Office 365.
  
Alguns dos principais itens nos artigos acima que você precisa entender incluem:
  
- Circuitos ExpressRoute não são mapeados para a infra-estrutura física específica, mas são uma conexão lógica feita em um único local de correspondência pela Microsoft e um provedor de correspondência em seu nome.

- Não há um mapeamento 1:1 entre um circuito ExpressRoute e uma s-chave do cliente.

- Cada circuito pode suportar até 3 relações de correspondência independentes (correspondência pública do Windows Azure, correspondência Azure privada e correspondência da Microsoft); O Office 365 exige a correspondência da Microsoft.

- Cada circuito tem uma largura de banda fixa que é compartilhada entre todas as relações de correspondência.

- Lida com qualquer público IPv4 e público como números que serão usados para o ExpressRoute circuito deve ser validado como sendo pertencentes a você, ou atribuído exclusivamente para você pelo proprietário do intervalo de endereços.

- Os circuitos ExpressRoute virtuais são redundantes globalmente e seguirão práticas de roteamento BGP padrão. Esse é o motivo pelo qual recomendamos dois circuitos físicos por saída ao seu provedor em uma configuração ativa/ativa.

Consulte a [página de perguntas Frequentes](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) para mais informações sobre os serviços de suporte, os custos e detalhes de configuração. Consulte o [artigo de locais de ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-locations/) para obter informações na lista de provedores de conectividade que oferece suporte da Microsoft. Também podemos ter gravadas uma série de [ExpressRoute do Windows Azure para treinamento do Office 365](https://channel9.msdn.com/series/aer) 10 partes no Channel 9 para ajudar a explicar os conceitos mais detalhadamente.
  
## <a name="ensuring-route-symmetry"></a>Garantindo que a rota simetria

Os servidores de front-end do Office 365 estão acessíveis na Internet e ExpressRoute. Esses servidores serão preferem rotear via circuitos ExpressRoute quando ambos estão disponíveis. Por isso há a possibilidade de assimetria rota se prefere do tráfego da sua rede rotear o seus circuitos de Internet. Assimétricas rotas são um problema porque os dispositivos que executam inspeção de pacotes com informações de estado podem bloquear o tráfego de retorno que segue um caminho diferente os pacotes de saída seguida.
  
Independentemente se você inicia uma conexão para o Office 365 pela Internet ou ExpressRoute, a fonte deve ser um endereço roteável publicamente. Com muitos clientes correspondência diretamente com a Microsoft, ter endereços privados onde é possível entre os clientes a duplicação não é viável.
  
A seguir são cenários onde as comunicações do Office 365 para sua rede local serão iniciadas. Para simplificar o design de sua rede, é recomendável roteamento essas sobre o caminho da Internet.
  
- ADFS durante a validação de senha para a entrada.

- [Implantações híbridas do Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- Email de um locatário do Exchange Online para um host local..

- Caixas de correio Online do SharePoint enviar do SharePoint Online para um host local.

- [SharePoint federados pesquisa híbrida](https://technet.microsoft.com/library/dn197174.aspx).

- [SharePoint híbrido BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype para o híbrido de negócios](https://technet.microsoft.com/en-us/library/jj205403.aspx) e/ou [Skype para federação de negócios](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype para o Business Connector de nuvem](https://technet.microsoft.com/library/mt605227.aspx ).

Para o Microsoft rotear novamente para sua rede para esses fluxos de tráfego bidirecional, as rotas BGP para seus dispositivos de locais devem ser compartilhadas com a Microsoft.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Decidindo quais aplicativos e recursos rotear sobre ExpressRoute

Quando você configurar uma relação de correspondência usando o domínio de roteamento correspondência da Microsoft e é aprovados para o acesso apropriado, você poderá ver PaaS e o SaaS todos os serviços disponíveis ao longo do ExpressRoute. Os serviços do Office 365 projetados para ExpressRoute podem ser gerenciados com [comunidades BGP](https://aka.ms/bgpexpressroute365) ou [filtros de rota](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal).
  
Outros aplicativos como vídeo do Office 365, é um aplicativo do Office 365; No entanto, o vídeo do Office 365 é composto de três componentes diferentes, o portal, o serviço de streaming e a rede de fornecimento de conteúdo. O portal reside no SharePoint Online, a vida streaming de serviço no Windows Azure Media Services, e a rede de fornecimento de conteúdo fica dentro a CDN do Windows Azure. A tabela a seguir descreve esses componentes.
  
| |
|**Componente**|**Aplicativo subjacente**|**Incluído na comunidade do SharePoint Online BGP?**|**Usar**|
|:-----|:-----|:-----|:-----|
|Portal de vídeo do Office 365  <br/> |SharePoint Online  <br/> |Sim  <br/> |Configuração, carregamento  <br/> |
|Serviço de streaming de vídeo do Office 365  <br/> |Azure Media Services  <br/> |Não  <br/> |Serviço de streaming, usado no caso do vídeo não está disponível da CDN  <br/> |
|Rede de fornecimento de conteúdo de vídeo do Office 365  <br/> |Azure CDN  <br/> |Não  <br/> |Principal fonte de streaming/download de vídeo. [Saiba mais sobre redes de vídeo do Office 365](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).<br/> |

Cada um dos recursos do Office 365 que estão disponíveis usando o Microsoft correspondência são listados no [artigo de pontos de extremidade do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) por tipo de aplicativo e o FQDN. O motivo para usar o FQDN nas tabelas é permitir que os clientes a gerenciar o tráfego usando arquivos PAC ou outras configurações de proxy, consulte nosso guia para [gerenciar pontos de extremidade do Office 365](https://aka.ms/manageo365endpoints) por exemplo PAC arquivos.
  
Em determinadas situações usamos um domínio curinga onde um ou mais sub-FQDNs são anunciadas diferente do domínio de curinga de nível superior. Isso geralmente ocorre quando o caractere curinga representa uma longa lista de servidores que sejam todos anunciadas aos ExpressRoute e a Internet, enquanto um pequeno conjunto de subsites de destinos são divulgado apenas para a Internet, ou vice-versa. Consulte as tabelas abaixo para entender onde as diferenças são.
  
Esta tabela exibe o caractere curinga FQDNs são anunciadas com a internet e o Azure ExpressRoute junto com os FQDNs de sub que são anunciados apenas para a internet.

|**Domínio de curinga divulgado a circuitos ExpressRoute e Internet**|**Sub-FQDN divulgado a apenas circuitos de Internet**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |Click.email.microsoftonline.com  <br/> https://portal.microsoftonline.comhttps://portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> Nexus.officeapps.Live.com  <br/> ODC.officeapps.Live.com  <br/> ODC.officeapps.Live.com  <br/> CDN.odc.officeapps.Live.com  <br/> ols.officeapps.Live.com  <br/> ocsredir.officeapps.Live.com  <br/> ocws.officeapps.Live.com  <br/> ocsa.officeapps.Live.com  <br/> |

Geralmente arquivos PAC destinam-se a enviar solicitações de rede para ExpressRoute divulgado pontos de extremidade diretamente para o circuito e todas as outras solicitações de rede até o proxy. Se você estiver configurando um arquivo de PAC desta, redigir seu arquivo PAC na seguinte ordem:
  
1. Inclua os FQDNs de sub da coluna dois na tabela acima na parte superior do seu arquivo PAC, enviando o tráfego na direção do seu proxy. Criamos um arquivo de PAC de amostra para uso em nosso artigo sobre como [gerenciar pontos de extremidade do Office 365](https://aka.ms/manageexpressroute365).

2. Inclua todos os FQDNs marcados anunciados para ExpressRoute [neste artigo](https://aka.ms/o365endpoints) abaixo da primeira seção, enviando o tráfego diretamente para sua circuito ExpressRoute.

3. Inclua outros pontos de extremidade de rede ou regras abaixo essas duas entradas, enviando o tráfego na direção do seu proxy.

Esta tabela exibe os domínios de curinga que são anunciados circuitos de Internet apenas junto com os FQDNs de sub que sejam anunciados aos ExpressRoute do Windows Azure e circuitos de Internet. Para o seu arquivo PAC acima, os FQDNs na coluna dois a tabela a seguir são listados como sendo anunciado para ExpressRoute no link referenciado, o que significa que eles seriam incluídos no segundo grupo de entradas no arquivo.

|**Domínio de curinga divulgado a apenas circuitos de Internet**|**Sub-FQDN divulgado a circuitos ExpressRoute e Internet**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> Home.Office.com  <br/> Outlook.Office.com  <br/> Portal.Office.com  <br/> www.Office.com  <br/> |
|\*. office.net  <br/> |Agent.Office.NET  <br/> |
|\*. office365  <br/> |Outlook.office365.com  <br/> SMTP.office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> descoberta automática -\<locatário\>. outlook.com  <br/> |
|\*. no windows.net  <br/> |login.Windows.NET  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Rotear o tráfego de Office 365 pela Internet e ExpressRoute

Para rotear para o Office 365 o aplicativo de sua escolha que você precisará determinar uma série de fatores importantes.
  
1. Quanta largura de banda que o aplicativo exigirá. Uso existente de amostragem é o único método confiável para determinar isso em sua organização.

2. Quais local saída (is) deseja que o tráfego de rede para sair da sua rede de. Você deve planejar minimizar a latência de rede para conectividade com o Office 365, como isso afetará o desempenho. Como Skype para negócios usa vídeo e voz em tempo real é particularmente suscetível a latência de rede ruim.

3. Se você quiser todos ou um subconjunto de seus locais de rede aproveitar ExpressRoute.

4. Locais que o seu provedor de rede escolhida oferece ExpressRoute de.

Depois de determinar as respostas a essas perguntas, você pode provisionar um circuito ExpressRoute que atende às necessidades de largura de banda e local. Para mais de rede assistência de planejamento, consulte o [estudo de caso sobre como as alças de Microsoft rede planejamento de desempenho](https://aka.ms/tunemsit)e a [rede do Office 365 ajuste a guia](https://aka.ms/tune) .
  
### <a name="example-1-single-geographic-location"></a>O exemplo 1: Single localização geográfica
  
Este exemplo é um cenário de uma empresa fictícia chamada Trey Research, que tem um único local geográfico.
  
Funcionários em Trey Research só são permitidos para se conectar aos serviços e sites da internet que o departamento de segurança permite explicitamente no par de saída proxies estabelecidos entre a rede corporativa e seu ISP.
  
Trey Research estiver planejando usar o Windows Azure ExpressRoute para o Office 365 e reconhece que alguns tráfego, como o tráfego destinado para redes de fornecimento de conteúdo não poderá ser roteado sobre o ExpressRoute para conexão do Office 365. Desde que todo o tráfego, já rotas para os dispositivos de proxy por padrão, essas solicitações continuarão funcionando como antes. Após Trey Research determina que pode atender a requisitos de roteamento do Azure ExpressRoute, eles prosseguir para criar um circuito, configure o roteamento e vincular o novo circuito ExpressRoute a uma rede virtual. Depois que a configuração do Windows Azure ExpressRoute fundamental estiver no lugar, Trey Research usa o [arquivo de PAC n º 2 que publicamos](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) para rotear o tráfego com dados específicos do cliente sobre o ExpressRoute direto para conexões do Office 365.
  
Conforme mostrado no diagrama a seguir, Trey Research é capaz de satisfazer a necessidade para rotear o tráfego do Office 365 através da internet e um subconjunto de tráfego via ExpressRoute usando uma combinação de alterações de configuração de proxy de roteamento e de saída.
  
1. Usando o [arquivo de PAC n º 2 que publicamos](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) para rotear o tráfego por meio de um ponto de saída de internet separado para ExpressRoute do Windows Azure para o Office 365.

2. Os clientes são configurados com uma rota padrão rumo proxies da Trey Research.

Neste cenário de exemplo, Trey Research está usando um dispositivo de proxy de saída. Da mesma forma, os clientes que não estiverem usando o Windows Azure ExpressRoute para o Office 365 talvez queira usar essa técnica para rotear o tráfego com base no custo do inspecionando o tráfego destinado a pontos de extremidade de alto volume conhecido.
  
O mais alto volume FQDNs para Exchange Online, SharePoint Online e Skype para Business Online são as seguintes:
  
![Rede de borda ExpressRoute do cliente](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- Outlook.office365.com, outlook.office.com

- \<nome do locatário\>. sharepoint.com, \<nome do locatário\>-my.sharepoint.com, \<nome do locatário\>-\<app\>. sharepoint.com

- \*. Lync.com juntamente com os intervalos de IP para o tráfego não-TCP

- \*broadcast.officeapps.Live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \* Word-edit.officeapps.live.com \*view.officeapps.live.com do word, office.live.com

Saiba mais sobre como [implantar e gerenciar configurações de proxy no Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) e [garantindo que o Office 365 não é acelerado pelo seu proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Com um único circuito ExpressRoute, não há nenhuma alta disponibilidade para Trey Research. No caso de falha de par da Trey redundante de dispositivos de borda que estão atendendo a conectividade ExpressRoute, não há um circuito ExpressRoute adicional de failover para. Isso deixa Trey Research em um impasse conforme o failover para a internet exigirão reconfiguração manual e em alguns casos endereços IP de novo. Se Trey quiser adicionar a alta disponibilidade, a solução mais simples é adicionar circuitos de ExpressRoute adicionais para cada local e configurar os circuitos uma maneira de ativo/ativo.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>ExpressRoute roteamento para o Office 365 com vários locais

O último cenário, o roteamento de tráfego do Office 365 através de ExpressRoute é a base para a arquitetura de roteamento ainda mais complexa. Independentemente do número de locais, número de continentes onde esses locais existirem, o número de ExpressRoute circuitos e assim por diante, ser capaz de rotear o tráfego de alguns à Internet e alguns tráfego via ExpressRoute serão necessária.
  
As perguntas adicionais que precisam ser respondidas para clientes com vários locais em várias regiões incluem:
  
1. Você requer um circuito ExpressRoute em cada local? Se você estiver usando o Skype para Business Online ou estiver preocupado com a sensibilidade de latência do SharePoint Online ou Exchange Online, um par redundante de circuitos de ExpressRoute ativos/ativos são recomendados em cada local. Consulte o Skype para mídia qualidade e rede conectividade guia Business para obter mais detalhes.

2. Se um circuito ExpressRoute não está disponível em uma região específica, como deve Office 365 destinado tráfego ser roteado?

3. Qual é o método preferencial para tráfego consolidando no caso de redes com muitos locais pequenos?

Cada uma dessas representa um desafio exclusivo que exige a avaliar a sua própria rede, bem como as opções disponíveis na Microsoft.

|**Consideração**|**Componentes de rede para avaliar**|
|:-----|:-----|
|Circuitos em mais de um local  <br/> |Recomendamos um mínimo de dois circuitos configurados de maneira ativa/ativa.  <br/> Necessidades de custos, latência e largura de banda devem ser comparadas.  <br/> Use o custo de rota BGP, arquivos PAC e NAT para gerenciar o roteamento com vários circuitos.  <br/> |
|Roteamento de locais sem um circuito ExpressRoute  <br/> |Recomendamos a resolução DNS como próximo a pessoa que inicia a solicitação para o Office 365 e saída.  <br/> Encaminhamento de DNS pode ser usado para permitir que os escritórios remotos descobrir o ponto de extremidade apropriado.  <br/> Clientes do escritório remoto devem ter uma rota disponível que fornece acesso aos ExpressRoute circuito.  <br/> |
|Consolidação de pequena empresa  <br/> |Uso de largura de banda e dados disponíveis deve ser comparado cuidadosamente.  <br/> |

> [!NOTE]
> Microsoft será preferem ExpressRoute pela internet, se a rota estiver disponível, independentemente da localização física.
  
Cada uma dessas considerações deve ser levada em conta para cada rede exclusivo. A seguir está um exemplo.
  
### <a name="example-2-multi-geographic-locations"></a>Exemplo 2: Locais de vários locais geográficos
  
Este exemplo é um cenário de uma empresa fictícia chamada Humongous Insurance quem tem várias localizações geográficas.
  
Humongous Insurance seja geograficamente dispersa com escritórios em todo o mundo. Eles desejam implementar ExpressRoute do Windows Azure para o Office 365 manter a maioria dos seu tráfego do Office 365 em conexões de rede direta. Humongous Insurance também tem escritórios em dois continentes adicionais. Os funcionários no escritório remoto onde ExpressRoute não é viável precisará rotear novamente para uma ou ambas as instalações principais para usar uma conexão ExpressRoute.
  
O princípio orientando deve obter o tráfego do Office 365 destinado a um datacenter da Microsoft assim que possível. Neste exemplo, Humongous Insurance deve decidir se os escritórios remotos devem rotear pela Internet para chegar a um datacenter da Microsoft sobre qualquer conexão mais depressa possível, ou se os escritórios remotos devem rotear por uma rede interna para chegar à Microsoft Datacenter sobre uma conexão ExpressRoute mais depressa possível.
  
Arquitetura de aplicativos, redes e data centers da Microsoft são desenvolvidos para tirar communications globalmente diversos e pessoal-los da maneira mais eficiente possível. Essa é uma das maiores redes do mundo. Solicitações destinadas para Office 365 que permanecem em redes de clientes mais do que o necessário não conseguirá aproveitar as vantagens dessa arquitetura.
  
Situação da Humongous Insurance, eles devem continuar dependendo dos aplicativos que pretendem usar via ExpressRoute. Por exemplo, se ele for um Skype para negócios Online de cliente ou pretende aproveitar a conectividade de ExpressRoute durante a conexão com Skype externo para reuniões Online de negócios, o design recomendado no Skype Business Online qualidade de mídia e rede Guia de conectividade é para provisionar um circuito ExpressRoute adicional para o local de terceiro. Isso pode ser mais caro de uma perspectiva de rede; No entanto, roteamento solicitações de um continente para outro antes de fornecimento de um datacenter da Microsoft pode causar uma experiência de baixa ou não-utilizável durante Skype para comunicações e reuniões Online de negócios.
  
Se Humongous Insurance não está usando ou não pretende aproveitar Skype para Business Online de nenhuma maneira, rotear tráfego de rede do Office 365 destinado um continente com um ExpressRoute conexão pode ser viável entanto pode causar latência desnecessária ou TCP congestionamento. Em ambos os casos, roteamento Internet tráfego destinado para a Internet no site local é recomendado para tirar proveito das redes de fornecimento de conteúdo que o Office 365 depende.
  
![Região geográfica de várias ExpressRoute](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Quando Humongous Insurance estiver planejando implantar sua estratégia de várias geografia, há algumas coisas a serem consideradas ao redor de tamanho de circuito, número de circuitos, failover e assim por diante.
  
Com ExpressRoute em um único local com várias regiões tentar usar o circuito, Humongous Insurance deseja garantir que as conexões para o Office 365 do escritório remoto são enviadas para o datacenter do Office 365 mais próximo de matrizes e recebidas pela localização de matrizes. Para fazer isso, Humongous Insurance implementa o encaminhamento de DNS para reduzir o número de viagens de ida e pesquisas de DNS necessárias para estabelecer a conexão apropriada com o mais próximo ao ponto de saída de internet matrizes do ambiente do Office 365. Isso impede que o cliente resolver um servidor front-end local e garante que o servidor de Front-End que a pessoa se conecta ao está perto as matrizes onde o Humongous Insurance é correspondência com a Microsoft. Você também pode saber para [atribuir um encaminhador condicional de um nome de domínio](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx).
  
Neste cenário, o tráfego do escritório remoto seria resolver a infraestrutura de front-end do Office 365 na América do Norte e aproveitar o Office 365 para se conectar aos servidores back-end de acordo com a arquitetura do aplicativo Office 365. Por exemplo, o Exchange Online seria encerrar a conexão na América do Norte e esses servidores de front-end seriam conectar ao servidor de caixa de correio de back-end onde o inquilino estava instalado. Todos os serviços possuem um serviço de porta de frontal amplamente distribuídos composto de destinos de difusão e unicast.
  
Se Humongous tem escritórios principais em vários continentes, um mínimo de dois circuitos ativos/ativos por região são recomendados para reduzir a latência para aplicativos confidenciais, como Skype para Business Online. Se todos os escritórios estão em um único continente ou não está usando a colaboração em tempo real, ter uma saída consolidada ou distribuída aponte é uma decisão de cliente específico. Quando vários circuitos estiverem disponíveis, roteamento de BGP garantirá failover tiver qualquer circuito único de ficar indisponível.
  
Saiba mais sobre a amostra de [configurações de roteamento](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) e [https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/).
  
## <a name="selective-routing-with-expressroute"></a>Seletiva de roteamento com ExpressRoute

Roteamento seletiva com ExpressRoute pode ser necessários para uma variedade de motivos, como testes, aplicação do ExpressRoute a um subconjunto de usuários. Existem diversas ferramentas que os clientes podem usar para rotear o tráfego de rede do Office 365 seletivamente via ExpressRoute:
  
1. **Filtragem de rota/segregação** - permitindo que as rotas BGP para o Office 365 via ExpressRoute a um subconjunto dos roteadores ou sub-redes. Isso encaminha seletivamente por segmento de rede do cliente ou o local do escritório físico. Isso é comum para distribuição intercalar do ExpressRoute para o Office 365 e está configurado em seus dispositivos BGP.

2. **Arquivos de PAC/URLs** - direcionando o Office 365 destinado tráfego de rede para os FQDNs específicos rotear em um caminho específico. Isso encaminha seletivamente pelo computador cliente conforme identificado pela [implantação do arquivo PAC](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies).

3. **Filtragem de rotas** - [filtros de roteamento](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) são uma maneira de consumir um subconjunto dos serviços com suporte por meio de correspondência da Microsoft.

4. **Comunidades BGP** - filtragem baseada em [marcas de comunidade BGP](https://aka.ms/bgpexpressroute365) permite que um cliente determinar quais aplicativos do Office 365 percorrerá ExpressRoute e qual percorrerá a internet.

Aqui está um link curto que você pode usar para voltar:[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>Tópicos relacionados

[Conectividade de rede para Office 365](network-connectivity.md)
  
[Microsoft Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Como gerenciar o ExpressRoute para a conectividade do Office 365](managing-expressroute-for-connectivity.md)
  
[Planejamento de rede com o ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Como implementar o ExpressRoute para Office 365](implementing-expressroute.md)
  
[Qualidade de mídia e o desempenho de conectividade de rede no Skype para negócios on-line](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Otimização de sua rede para Skype para negócios Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute e QoS em Skype para negócios on-line](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Fluxo de chamadas usando ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Usando o comunidades BGP em ExpressRoute para cenários do Office 365](bgp-communities-in-expressroute.md)
  
[Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho](performance-tuning-using-baselines-and-history.md)
  
[Plano de solução de problemas de desempenho do Office 365](performance-troubleshooting-plan.md)
  
[URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Ajuste de desempenho e de rede do Office 365](network-planning-and-performance.md)
