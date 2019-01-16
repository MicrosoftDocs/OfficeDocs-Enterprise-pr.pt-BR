---
title: Princípios de conectividade de rede do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/14/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid: MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: Antes de começar a planejar sua rede para conectividade de rede do Office 365, é importante entender os princípios de conectividade para gerenciar o tráfego de Office 365 de forma segura e obter o melhor desempenho possível. Este artigo ajudará você a entender as orientações mais recentes para otimizar com segurança de conectividade de rede do Office 365.
ms.openlocfilehash: d319d99cdd413fe1df9e8f88d18742ad464bbb3b
ms.sourcegitcommit: f0ba0d8c62f802447bc9d07f5d877067156fbed5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "28021802"
---
# <a name="office-365-network-connectivity-principles"></a>Princípios de conectividade de rede do Office 365

Antes de começar a planejar sua rede para conectividade de rede do Office 365, é importante entender os princípios de conectividade para gerenciar o tráfego de Office 365 de forma segura e obter o melhor desempenho possível. Este artigo ajudará você a entender as orientações mais recentes para otimizar com segurança de conectividade de rede do Office 365.
  
Redes corporativas tradicional destinam-se principalmente para fornecer aos usuários acesso aos dados hospedados em centros de dados da empresa operado com segurança de perímetro forte e aplicativos. O modelo tradicional pressupõe que os usuários acessarão aplicativos e dados de dentro do perímetro de rede corporativa, em links de WAN de filiais, ou remotamente através de conexões VPN. 
  
Adoção de aplicativos SaaS como o Office 365 move alguma combinação de serviços e dados fora do perímetro de rede. Sem otimização, o tráfego entre os usuários e aplicativos SaaS está sujeito a latência introduzida pela inspeção de pacotes, hairpins de rede, conexões inadvertidas aos pontos de extremidade geograficamente distantes e outros fatores. Você pode garantir o melhor desempenho do Office 365 e a confiabilidade Entendendo e implementando o diretrizes de otimização de chave.
  
Neste artigo, você aprenderá sobre:
  
- [Arquitetura do office 365](office-365-network-connectivity-principles.md#BKMK_Architecture) , como ela se aplica a conectividade do cliente para a nuvem
- Atualizado [princípios de conectividade do Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) e estratégias para otimizar o tráfego de rede e a experiência do usuário final
- O [serviço web de pontos de extremidade do Office 365](office-365-network-connectivity-principles.md#BKMK_WebSvc), que permite aos administradores de rede consumir uma lista estruturada de pontos de extremidade para uso na otimização de rede
- Orientação de [categorias de ponto de extremidade do novo Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) e otimização
- [Comparando a segurança do perímetro de rede com a segurança do ponto de extremidade](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Opções de [otimização incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) para o tráfego do Office 365

## <a name="office-365-architecture"></a>Arquitetura do Office 365
<a name="BKMK_Architecture"> </a>

Office 365 é distribuída nuvem Software-como um serviço (SaaS) que fornece cenários de produtividade e colaboração por meio de uma gama de microserviços e aplicativos, como o Exchange Online, SharePoint Online, Skype para negócios Online, Microsoft As equipes, Exchange Online Protection, Office Online e muitos outros. Enquanto aplicativos específicos do Office 365 podem ter seus recursos exclusivos, como ele se aplica à rede de cliente e conectividade com a nuvem, todos eles compartilham algumas entidades principais, metas e os padrões de arquitetura. Essas entidades e os padrões de arquitetura para conectividade são típicos para muitas outras nuvens SaaS e ao mesmo tempo sendo bem diferente de modelos de implantação típico do plataforma como serviço e nuvens de infraestrutura como serviço, como o Microsoft Windows Azure.
  
Um dos recursos mais significativos arquitetônicos do Office 365 (que é geralmente perdidas ou interpretado por planejadores de rede) é o que é um serviço distribuído realmente global, no contexto de como os usuários se conectam a ela. O local do locatário do Office 365 de destino é importante compreender a localidade de onde os dados de cliente são armazenados na nuvem, mas a experiência do usuário com o Office 365 não envolve se conectando diretamente ao discos contendo os dados. A experiência do usuário com o Office 365 (incluindo o desempenho, a confiabilidade e outras características importantes qualidade) envolve a conectividade através de portas de frente um serviço altamente distribuído, que são reduzidas em centenas de locais da Microsoft no mundo todo. Na maioria dos casos, a melhor experiência de usuário é obtida por permitindo que a rede do cliente para rotear solicitações de usuário para o ponto de entrada de serviço mais próximo do Office 365, em vez de se conectam ao Office 365 por meio de um ponto de saída em um local central ou a região.
  
Para a maioria dos clientes, os usuários do Office 365 são distribuídos em muitos locais. Para obter os melhores resultados, os princípios descritos neste documento devem ser encarados do dimensionamento (não dimensione) ponto de Vista, voltada à otimização de conectividade para o ponto mais próximo de presença na rede Global da Microsoft, não para o geográfica local do inquilino do Office 365. Em essência, isso significa que, apesar de dados de Inquilinos do Office 365 podem ser armazenados em uma localização geográfica específica, o experiência do Office 365 para que locatário permanece distribuída e pode estar presente no muito fechar proximidade (rede) para cada local do usuário final que tenha o locatário .
  
## <a name="office-365-connectivity-principles"></a>Princípios de conectividade do Office 365
<a name="BKMK_Principles"> </a>

A Microsoft recomenda os seguintes princípios para obter o desempenho e a conectividade do Office 365 ideal. Use estes princípios de conectividade do Office 365 para gerenciar o tráfego de e para obter o melhor desempenho ao conectar-se ao Office 365.
  
O principal objetivo do design de rede deve ser minimizar a latência, reduzindo o tempo de ida e volta (tempo de resposta) da sua rede com a rede Global do Microsoft, backbone de rede pública da Microsoft que interconexão todos os centros de dados da Microsoft com baixa latência e pontos de entrada de aplicativo espalhados pelo mundo na nuvem. Você pode aprender mais sobre a rede Global da Microsoft em [como a Microsoft amplia sua rede global rápida e confiável](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-office-365-traffic"></a>Identificar e diferenciar o tráfego do Office 365

![Identificar o tráfego do Office 365](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
A identificação de tráfego de rede do Office 365 é a primeira etapa na ser capaz de diferenciar esse tráfego de tráfego de rede genérico vinculada à Internet. Conectividade do Office 365 pode ser otimizada implementando uma combinação de abordagens como otimização de rota da rede, regras de firewall, configurações de proxy do navegador e desvio de inspeção de dispositivos de rede para determinados pontos de extremidade.
  
Orientações de otimização anteriores do Office 365 dividido pontos de extremidade do Office 365 em duas categorias, **necessários** e **opcionais**. Como pontos de extremidade foram adicionados para oferecer suporte a novos serviços do Office 365 e recursos, podemos ter reorganizado pontos de extremidade do Office 365 em três categorias: **otimizar**, **Permitir** e **padrão**. Diretrizes para cada categoria se aplica a todos os pontos de extremidade na categoria, tornando mais fácil de entender e implementar o otimizações. 
  
Para obter mais detalhes sobre os métodos de otimização e categorias de ponto de extremidade do Office 365, consulte a seção [categorias de ponto de extremidade do novo Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Agora, a Microsoft publica todos os pontos de extremidade do Office 365, como um serviço web e fornece orientação sobre como melhor usar esses dados. Para obter mais informações sobre como buscar e trabalhar com pontos de extremidade do Office 365, consulte o artigo [URLs do Office 365 e intervalos de endereços IP](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Enviar conexões de rede de saída localmente

![Enviar conexões de rede de saída localmente](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Saída DNS local e a Internet é de importância fundamental para reduzir a latência de conexão e para garantir que as conexões de usuário sejam feitas até o ponto mais próximo de entrada para serviços do Office 365. Em uma topologia de rede complexa, é importante implementar o DNS local e a saída de Internet local juntos. Para obter mais informações sobre como o Office 365 roteia as conexões de cliente até o ponto mais próximo de entrada, consulte o artigo [Conectividade do cliente](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Antes do advento serviços em nuvem, como o Office 365, o usuário final a conectividade de Internet como um fator de design na arquitetura de rede era relativamente simple. Quando os serviços de Internet e sites da web são distribuídos em todo o mundo, a latência entre os pontos de saída corporativo e qualquer ponto de extremidade de destino determinado é basicamente uma função de distância geográfica.
  
Em uma arquitetura de rede tradicional, todas as conexões de Internet de saída atravessam a rede corporativa em a saída de um local central. À medida que as ofertas de nuvem da Microsoft têm amadureceu, uma arquitetura de rede distribuída voltado à Internet tornou crítica para dar suporte a serviços em nuvem sensível a latência. A Microsoft Global Network foi projetado para acomodar requisitos de latência com a infra-estrutura de distribuído porta do serviço frontal, uma malha dinâmica dos pontos de entrada global que roteia as conexões de serviço de nuvem entrada para o ponto de entrada mais próximo. Isso é destinado para reduzir o comprimento da "última milha" clientes de nuvem da Microsoft diminuindo efetivamente a rota entre o cliente e a nuvem.
  
Enterprise WANs frequentemente são projetadas para backhaul o tráfego de rede para uma matriz da empresa central para inspeção antes da saída da Internet, geralmente por meio de um ou mais servidores de proxy. O diagrama abaixo ilustra uma topologia de rede como esta.
  
![Modelo de rede corporativo tradicional](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Como o Office 365 é executado no Microsoft Global Network, que inclui servidores front-end em todo o mundo, muitas vezes haverá um servidor front-end e está perto do local do usuário. Fornecendo um local de saída de Internet e configurando os servidores DNS internos para fornecer resolução de nomes locais para os pontos de extremidade do Office 365, o tráfego de rede destinado para o Office 365 pode se conectar aos servidores de front-end do Office 365 mais próximo possível ao usuário. O diagrama a seguir mostra um exemplo de uma topologia de rede que permite aos usuários se conectando de escritório principal, filial e locais remotos siga a rota mais curta para o ponto de entrada do Office 365 mais próximo.
  
![Modelo de rede WAN com pontos de saída regionais](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Diminuindo o caminho de rede para o Office 365 pontos de entrada dessa maneira podem melhorar o desempenho de conectividade e o usuário final experiência com o Office 365 e pode também ajuda a reduzir o impacto de futuras alterações na arquitetura de rede no desempenho do Office 365 e confiabilidade.
  
Além disso, as solicitações DNS podem introduzir a latência se o servidor DNS de resposta está distante ou ocupado. Você pode minimizar a latência de resolução de nome provisionamento servidores DNS locais em locais de filial e verificando-se de que eles estão configurados adequadamente para registros DNS do cache.
  
Enquanto a saída regional pode funcionam bem para o Office 365, o modelo de conectividade ideal seria sempre fornecer a saída de rede no local do usuário, independentemente se isso está na rede corporativa ou locais remotos, como home, hotéis, cafeterias e aeroportos. Este modelo de saída direto local é representado no diagrama a seguir.
  
![Arquitetura de rede de saída local](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
As empresas que adotaram o Office 365 podem tirar proveito da arquitetura de distribuído porta do serviço frontal da rede Global Microsoft, garantindo que conexões de usuário para o Office 365 levar a rota possível mais curta para a entrada de rede Global Microsoft mais próxima ponto. A arquitetura de rede de saída local faz isso, permitindo o tráfego do Office 365 para serem encaminhadas sobre a mais próximo de saída, independentemente do local do usuário.
  
A arquitetura de saída local tem as seguintes vantagens sobre o modelo tradicional:
  
- Fornece o melhor desempenho do Office 365 otimizando o comprimento de rota. Conexões de usuário final dinamicamente são roteadas para o ponto de entrada do Office 365 mais próximo pela infra-estrutura distribuído porta do serviço frontal.
- Reduz a carga em infraestrutura de rede corporativa, permitindo a saída local.
- Protege conexões em ambas as extremidades utilizando a segurança do cliente do ponto de extremidade e recursos de segurança de nuvem.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Evitar hairpins de rede

![Evite hairpins](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Como um regra geral, a rota mais curta, mais direta entre o usuário e mais próximo ponto de extremidade do Office 365 oferecerá o melhor desempenho. Um hairpin de rede acontece quando o tráfego WAN ou VPN acoplado para um destino específico primeiro seja direcionado para outro local intermediário (por exemplo, a pilha de segurança, corretor de acesso de nuvem, do gateway da web com base de nuvem), apresentando latência e redirecionamento possível para um ponto de extremidade geograficamente distante. Rede hairpins também podem ser causados por roteamento/correspondência ineficiências ou inadequadas pesquisas de DNS (remotas).
  
Para garantir a conectividade do Office 365 não está sujeito a hairpins de rede mesmo no caso de saída local, verifique se o provedor que é usado para fornecer a saída da Internet para o local do usuário tem uma relação de correspondência direta com a rede Global da Microsoft em Fechar proximidade ao local. Convém também configurar para enviar o tráfego confiável do Office 365 diretamente o roteamento de saída, em vez de proxy ou encapsulamento através de uma nuvem de terceiros ou o fornecedor de segurança de rede baseado em nuvem que processa o tráfego de sua vinculada à Internet. Resolução de nomes DNS local de pontos de extremidade do Office 365 ajuda a garantir que além de roteamento direto, os pontos de entrada do Office 365 mais próximos estão sendo usados para conexões de usuário.
  
Se você usar a rede baseada em nuvem ou serviços de segurança para o tráfego do Office 365, certifique-se de que o efeito de hairpinning é avaliado e seu impacto no desempenho do Office 365 é compreendido. Isso pode ser feito examinando o número e os locais dos locais de provedor de serviço através do qual o tráfego é encaminhado em relação ao número de filiais e aos pontos de rede Global da Microsoft, qualidade da relação de correspondência de rede do o provedor de serviços com seu ISP Microsoft e o impacto no desempenho do backhauling na infraestrutura do provedor de serviço.
  
Devido ao grande número de locais distribuídos com pontos de entrada do Office 365 e sua proximidade aos usuários finais, a rotear o tráfego de Office 365 para qualquer provedor de segurança ou de rede de terceiros pode ter um impacto adverso em conexões do Office 365 se não for de rede do provedor configurado para correspondência ideal do Office 365.
  
<a name="BKMK_P4"> </a>
### <a name="bypass-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Os proxies de desvio, dispositivos de inspeção de tráfego e as tecnologias de segurança duplicados

![Os proxies de desvio, dispositivos de inspeção de tráfego e as tecnologias de segurança duplicados](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Os clientes corporativos devem examinar sua segurança de rede e métodos de redução de risco especificamente para o Office 365 acoplada tráfego e usam os recursos de segurança do Office 365 para reduzir seus dependência em invasiva, afetar de desempenho e segurança da rede caro tecnologias para tráfego de rede do Office 365.
  
A maioria das redes de enterprise impor a segurança de rede para o tráfego de Internet usando tecnologias, como os proxies, inspeção SSL, inspeção de pacotes e sistemas de prevenção de perda de dados. Essas tecnologias fornecem mitigação de riscos importantes para solicitações de Internet genéricas, mas podem reduzir drasticamente o desempenho, escalabilidade e a qualidade da experiência do usuário final quando aplicada aos pontos de extremidade do Office 365.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Serviço de web de pontos de extremidade do Office 365

Administradores do Office 365 podem usar um script ou chamada REST para consumir uma lista estruturada de pontos de extremidade de pontos de extremidade do Office 365 serviço da web e atualizar as configurações de firewalls de perímetro e outros dispositivos de rede. Isso garantirá que tráfego acoplado para o Office 365 é identificado, adequadamente tratado e gerenciado de modo diferente do tráfego de rede acoplado para sites da web Internet genérico e frequentemente desconhecido. Para obter mais informações sobre como usar os pontos de extremidade do Office 365 serviço da web, consulte o artigo [URLs do Office 365 e intervalos de endereços IP](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Scripts de PAC (configuração automática de Proxy)
<a name="BKMK_WebSvc"> </a>

Administradores do Office 365 podem criar scripts de PAC (configuração automática de Proxy) que podem ser fornecidos aos computadores dos usuários por meio de WPAD ou GPO. Scripts de PAC podem ser usados para ignorar proxies para Office 365 solicitações de usuários WAN ou VPN, permitindo que o tráfego do Office 365 para usar conexões diretas de Internet ao invés atravessando a rede corporativa.
  
#### <a name="office-365-security-features"></a>Recursos de segurança do Office 365
<a name="BKMK_WebSvc"> </a>

Microsoft é transparente sobre segurança de datacenter, segurança operacional e redução de risco em torno de servidores do Office 365 e os pontos de extremidade de rede que eles representam. Recursos do Office 365 internos de segurança estão disponíveis para reduzir o risco de segurança de rede, como prevenção de perda de dados, antivírus, a autenticação multifator, caixa de bloqueio de cliente, proteção avançada de ameaça, inteligência de ameaça do Office 365, seguro do Office 365 Pontuação, Exchange Online Protection e segurança da rede DDOS.
  
Para obter mais informações sobre segurança de rede Global e de datacenter da Microsoft, consulte [Microsoft Central de confiabilidade](https://www.microsoft.com/en-us/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Novas categorias de ponto de extremidade do Office 365
<a name="BKMK_Categories"> </a>

Pontos de extremidade do Office 365 representam um conjunto variado de endereços de rede e sub-redes. Pontos de extremidade podem ser URLs, intervalos de endereços IP ou IP e alguns pontos de extremidade são listados com portas específicas de TCP/UDP. URLs podem ser um FQDN como *account.office.net* , ou uma URL de curinga, como * \*. office365*.
  
> [!NOTE]
> Os locais dos pontos de extremidade do Office 365 dentro da rede não estão diretamente relacionados para o local dos dados de Inquilino do Office 365. Por esse motivo, os clientes devem examinar o Office 365, como um serviço global e distribuído e não devem tentar bloquear as conexões de rede aos pontos de extremidade do Office 365 com base nos critérios geográficos.
  
Em nossa orientação anterior para gerenciar o tráfego do Office 365, os pontos de extremidade foram organizados em duas categorias, **necessários** e **opcionais**. Pontos de extremidade dentro de cada categoria requeridos otimizações diferentes dependendo do nível de importância do serviço e muitos clientes enfrentaram desafios em justificando a aplicação das otimizações de rede mesmo para a lista completa de endereços IP e URLs do Office 365. 
  
No novo modelo, os pontos de extremidade sejam separados em três categorias, **otimizar**, **Permitir** e **padrão**, fornecendo uma tabela dinâmica com base em prioridade sobre onde concentrar os esforços de otimização de rede para concretizar as melhorias de desempenho melhores e retornar sobre o investimento. Os pontos de extremidade são consolidados nas categorias acima com base na sensibilidade da experiência do usuário efetivo para o envelope de qualidade, o volume e o desempenho de rede dos cenários e facilidade de implementação. Otimizações recomendadas podem ser aplicadas da mesma maneira para todos os pontos de extremidade em uma determinada categoria.
  
- Pontos de extremidade de **otimizar** são necessários para a conectividade com todos os serviços do Office 365 e representam mais de 75% da largura de banda, conexões e volume de dados do Office 365. Esses pontos de extremidade representam cenários do Office 365 que são mais sensíveis ao desempenho, latência e disponibilidade de rede. Todos os pontos de extremidade são hospedados em data centers da Microsoft. Espera-se que a taxa de alteração para os pontos de extremidade nesta categoria é muito menor do que para os pontos de extremidade em duas categorias. Essa categoria inclui um conjunto muito pequeno (na ordem ~ 10) da chave de URLs e um conjunto definido de subredes IP dedicados ao cargas de trabalho de núcleo Office 365, como Exchange Online, SharePoint Online, Skype para Business Online e Teams da Microsoft.

    Uma lista condensada de pontos de extremidade críticos bem definidos deve ajudá-lo a planejar e implementar as otimizações de rede de alto valor para esses destinos mais rápidos e fácil.

    Exemplos de pontos de extremidade *Optimize* *https://outlook.office365.com* , *https://\<locatário\>. sharepoint.com* e *https://\<locatário\>-my.sharepoint.com* .

    Métodos de otimização incluem:

  - Bypass ou lista branca *Optimize* pontos de extremidade em dispositivos de rede e serviços que executam a interceptação de tráfego, SSL descriptografia, profunda inspeção de pacotes e filtragem de conteúdo.
  - Dispositivos de proxy local e serviços de nuvem proxy comuns utilizados para a navegação na Internet genérico de desvio.
  - Priorize a avaliação desses pontos de extremidade como totalmente confiável por seus sistemas de perímetro e a infraestrutura de rede.
  - Priorizar redução ou eliminação dos backhauling WAN e facilitar a saída de Internet com base distribuída direta para esses pontos de extremidade mais próximo de usuários/filiais possível.
  - Facilite a conectividade direta com esses pontos de extremidade de nuvem para usuários VPN por meio da implementação túnel em divisão.
  - Certifique-se de que os endereços IP retornados pela resolução de nomes DNS correspondem o caminho de roteamento de saída para esses pontos de extremidade.
  - Priorize esses pontos de extremidade para integração SD-WAN para roteamento de latência de danos direta, mínima para o ponto de correspondência de Internet mais próximo da rede global da Microsoft.

- Pontos de extremidade de **Permitir** são necessários para a conectividade com os recursos e serviços específicos do Office 365, mas não são tão sensíveis a latência como aqueles na categoria *Optimize* e desempenho da rede. A superfície de rede geral desses pontos de extremidade do ponto de vista da contagem de largura de banda e conexão também é consideravelmente menor. Esses pontos de extremidade são dedicados para o Office 365 e são hospedados em data centers da Microsoft. Eles representam um amplo conjunto de serviços do Office 365 micro e suas dependências (na ordem de aproximadamente 100 URLs) e esperados para alterar a uma taxa superior na categoria *Optimize* . Nem todos os pontos de extremidade nesta categoria estão associados a definido subredes IP dedicados.

    Otimizações de rede para *Permitir que* os pontos de extremidade podem melhorar a experiência de usuário do Office 365, mas alguns clientes podem optar por escopo essas otimizações mais estritamente para minimizar alterações em sua rede.

    Exemplos de pontos de extremidade de *Permitir* *https://\*. protection.outlook.com* e *https://accounts.accesscontrol.windows.net*.

    Métodos de otimização incluem:

  - Bypass ou lista branca *Permitir* pontos de extremidade em dispositivos de rede e serviços que executam a interceptação de tráfego, SSL descriptografia, profunda inspeção de pacotes e filtragem de conteúdo.
  - Priorize a avaliação desses pontos de extremidade como totalmente confiável por seus sistemas de perímetro e a infraestrutura de rede.
  - Priorizar redução ou eliminação dos backhauling WAN e facilitar a saída de Internet com base distribuída direta para esses pontos de extremidade mais próximo de usuários/filiais possível.
  - Certifique-se de que os endereços IP retornados pela resolução de nomes DNS correspondem o caminho de roteamento de saída para esses pontos de extremidade.
  - Priorize esses pontos de extremidade para integração SD-WAN para roteamento de latência de danos direta, mínima para o ponto de correspondência de Internet mais próximo da rede global da Microsoft.

- Pontos de extremidade **padrão** representam os serviços do Office 365 e dependências que não exigem qualquer otimização e podem ser tratadas por redes do cliente conforme normal Internet acoplado tráfego. Observe que alguns pontos de extremidade nesta categoria não podem ser hospedados em data centers da Microsoft. Exemplos incluem *https://odc.officeapps.live.com* e *https://appexsin.stb.s-msn.com*.

Para obter mais informações sobre as técnicas de otimização de rede do Office 365, consulte o artigo [pontos de extremidade de gerenciamento do Office 365](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Comparando a segurança do perímetro de rede com a segurança do ponto de extremidade
<a name="BKMK_SecurityComparison"> </a>

O objetivo de segurança de rede tradicional é proteger o perímetro de rede corporativa contra invasão e explorações mal-intencionado. Conforme as organizações adotam o Office 365, alguns serviços de rede e os dados são completamente ou parcialmente migrados para a nuvem. Como faz qualquer alteração fundamental para a arquitetura de rede, esse processo exige uma reavaliação de segurança de rede que leva em consideração o emergentes fatores:
  
- Como os serviços de nuvem são adotados, dados e serviços de rede são distribuídos entre centros de dados no local e a nuvem e segurança do perímetro não é mais adequada por conta própria.
- Usuários remotos se conectar aos recursos corporativos em centros de dados no local e na nuvem de locais não controladas como Residências, hotéis e lanchonetes.
- Recursos de segurança desenvolvido especificamente cada vez mais são criados no serviços em nuvem e potencialmente podem complementar ou substituir os sistemas de segurança existentes.

A Microsoft oferece uma ampla intervalo do Office 365 recursos de segurança e fornece diretrizes prescritivas para empregar práticas recomendadas de segurança que podem ajudá-lo a garantir a segurança de dados e rede para o Office 365. Práticas recomendadas incluem o seguinte:
  
- **Usar a autenticação multifator (MFA)** MFA adiciona uma camada adicional de proteção para a estratégia de senha forte por exigir que os usuários de agradecer uma chamada telefônica, uma notificação de aplicativo em seu telefone inteligente após inserir corretamente suas senhas ou mensagem de texto.

- **Segurança de aplicativo do uso Office 365 nuvem** Configure políticas para controlar a atividade anormal e agir contidas nela. Configurar alertas com segurança de aplicativo de nuvem do Office 365, de modo que os administradores podem examinar a atividade do usuário incomum ou riscado, como baixar grandes quantidades de dados, vários falhas em tentativas de entrar ou lida com conexões de um IP desconhecido ou perigoso.

- **Configurar a prevenção de perda de dados (DLP)** DLP permite identificar dados confidenciais e criar políticas que ajuda a impedir que os usuários acidentalmente ou intencionalmente compartilhamento de dados. DLP funciona entre o Office 365, incluindo o Exchange Online, SharePoint Online e OneDrive para que os usuários podem permanecer em conformidade sem interromper o fluxo de trabalho.

- **Uso do cliente Lockbox** Como um administrador do Office 365, você pode usar o cliente Lockbox para controlar como um engenheiro de suporte da Microsoft acessa os dados durante uma sessão de Ajuda. Em casos onde o engenheiro exige acesso aos seus dados para solucionar problemas e corrigir um problema, Lockbox do cliente permite que você aprovar ou rejeitar a solicitação de acesso.

- **Usar pontuação seguro do Office 365** Pontuação segura é uma ferramenta de análise de segurança que recomenda que você pode fazer para reduzir o risco. Pontuação segura analisa suas configurações do Office 365 e atividades e compará-los a uma linha de base estabelecida pela Microsoft. Você receberá uma pontuação com base em como alinhado estiver com as práticas recomendadas de segurança.

Uma abordagem abrangente para segurança reforçada deve incluir a consideração das seguintes opções:
  
- Deslocar ênfase de segurança do perímetro na direção de segurança de ponto de extremidade aplicando baseado em nuvem e recursos de segurança de cliente do Office.
  - Reduzir do perímetro de segurança para o datacenter
  - Habilite a confiança equivalente para dispositivos do usuário dentro do escritório ou em locais remotos
  - Foco no protegendo o local dos dados e o local do usuário
  - Usuário gerenciado máquinas têm maior confiança com segurança de ponto de extremidade
- Gerenciar a segurança de todas as informações de forma global, não concentrando-se exclusivamente no perímetro
  - Redefina WAN e a criação de segurança de rede de perímetro permitindo que o tráfego confiável para o desvio de dispositivos de segurança e separando os dispositivos não gerenciados redes Wi-Fi de convidado.
  - Reduz as necessidades de segurança de rede da borda WAN corporativa
  - Alguns dispositivos de segurança de perímetro de rede, como firewalls ainda são necessários, mas carregar é reduzido
  - Garante a saída local para o tráfego do Office 365
- Aprimoramentos podem ser abordados incrementalmente, conforme descrito na seção [otimização Incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) . Algumas técnicas de otimização podem oferecer melhor taxas de custo/benefício, dependendo de sua arquitetura de rede, e você deve escolher otimizações que fazem mais sentido para sua organização.

Para obter mais informações sobre conformidade e segurança do Office 365, consulte o artigo de [Visão geral da segurança e conformidade no Office 365](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## <a name="incremental-optimization"></a>Otimização incremental
<a name="BKMK_IncOpt"> </a>

Podemos ter representado o modelo de conectividade de rede ideal para SaaS neste artigo, mas para muitas organizações grandes com arquiteturas de rede historicamente complexa, não será prático diretamente fazer todas essas alterações. Nesta seção, abordamos um número de alterações incrementais que pode ajudar a melhorar a confiabilidade e desempenho do Office 365.
  
Os métodos que você usará para otimizar o tráfego do Office 365 irá variar dependendo da sua topologia de rede e os dispositivos de rede que você tenha implementado. Empresas de grandes porte com vários locais e práticas recomendadas de segurança de rede complexa precisará desenvolver uma estratégia que inclui a maior parte ou todo os princípios listados na seção [princípios de conectividade do Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) , enquanto as organizações menores podem apenas precisa considerar um ou dois.
  
Você pode abordar otimização como um processo incremental, a aplicação de cada método sucessivamente. A tabela a seguir lista os métodos de otimização de chave na ordem de seu impacto na latência e a confiabilidade para o maior número de usuários.
  
|**Método de otimização**|**Descrição**|**Impacto**|
|:-----|:-----|:-----|
|Resolução DNS local e saída de Internet  <br/> |Provisione servidores DNS locais em cada local e certifique-se de que saída de conexões do Office 365 para a Internet mais semelhante possível ao local do usuário.  <br/> | Minimizar a latência  <br/>  Melhorar a conectividade confiável para o ponto de entrada mais próximo do Office 365  <br/> |
|Adicionar pontos de saída regionais  <br/> |Se a sua rede corporativa possui vários locais, mas o ponto de saída de apenas um, adicione pontos de saída regionais para permitir que os usuários se conectem até o ponto de entrada do Office 365 mais próximo.  <br/> | Minimizar a latência  <br/>  Melhorar a conectividade confiável para o ponto de entrada mais próximo do Office 365  <br/> |
|Dispositivos de inspeção e proxies de desvio  <br/> |Configure os navegadores com arquivos PAC que enviam solicitações de Office 365 diretamente aos pontos de saída.  <br/> Configure firewalls para permitir o tráfego do Office 365 sem inspeção e roteadores de borda.  <br/> | Minimizar a latência  <br/>  Reduzir a carga nos dispositivos de rede  <br/> |
|Habilitar a conexão direta para usuários VPN  <br/> |Para usuários VPN, habilite as conexões do Office 365 conectar-se diretamente a partir de rede do usuário, em vez de no túnel VPN por meio da implementação túnel em divisão.  <br/> | Minimizar a latência  <br/>  Melhorar a conectividade confiável para o ponto de entrada mais próximo do Office 365  <br/> |
|Migrar da WAN tradicional para SD-WAN  <br/> |SD-WANs (Software definidos redes de longa distância) simplificam o gerenciamento de WAN e melhorar o desempenho, substituindo os roteadores tradicionais de WAN com dispositivos virtuais, semelhantes para a virtualização de recursos de computação usando as máquinas virtuais (VMs).  <br/> | Melhorar o desempenho e capacidade de gerenciamento de tráfego WAN  <br/>  Reduzir a carga nos dispositivos de rede  <br/> |
