---
title: Princípios de conectividade de rede do Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: Antes de começar a planejar sua rede para a conectividade de rede do Office 365, é importante compreender os princípios de conectividade para o gerenciamento seguro do tráfego do Office 365 e obter o melhor desempenho possível. Este artigo o ajudará a entender as orientações mais recentes para otimizar com segurança a conectividade de rede do Office 365.
ms.openlocfilehash: 29cfd5725d4c80f30146abcd921c37305c30b17d
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998660"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Princípios de conectividade de rede do Microsoft 365

*Este artigo se aplica ao Microsoft 365 Enterprise e ao Office 365 Enterprise.*

Antes de começar a planejar sua rede para a conectividade de rede do Microsoft 365, é importante compreender os princípios de conectividade para gerenciar com segurança o tráfego da Microsoft 365 e obter o melhor desempenho possível. Este artigo o ajudará a entender as orientações mais recentes para otimizar a conectividade de rede do Microsoft 365 com segurança.
  
As redes corporativas tradicionais são projetadas principalmente para fornecer aos usuários acesso a aplicativos e dados hospedados em datacenters da empresa operados com alta segurança de perímetro. O modelo tradicional pressupõe que os usuários acessarão aplicativos e dados de dentro do perímetro de rede corporativa, através de links WAN de filiais ou remotamente por conexões VPN.
  
A adoção de aplicativos SaaS como a Microsoft 365 move uma combinação de serviços e dados fora do perímetro da rede. Sem otimização, o tráfego entre usuários e aplicativos SaaS está sujeito à latência introduzida pela inspeção de pacotes, hairpins de rede, conexões inadvertidas para pontos de extremidade distantes geograficamente e outros fatores. Você pode garantir o melhor desempenho e a confiabilidade da Microsoft 365, compreendendo e implementando as principais diretrizes de otimização.
  
Neste artigo, você aprenderá sobre:
  
- A [arquitetura do Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Architecture) como ela se aplica à conectividade do cliente à nuvem
- Princípios e estratégias de [conectividade da Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Principles) atualizados para otimizar o tráfego de rede e a experiência do usuário final
- O [serviço Web de pontos de extremidade do Office 365](office-365-network-connectivity-principles.md#BKMK_WebSvc), que permite aos administradores de rede consumir uma lista estruturada de pontos de extremidade para uso na otimização de rede
- Novas orientações de otimização e [categorias de pontos de extremidade do Office 365](office-365-network-connectivity-principles.md#BKMK_Categories)
- [Comparando a segurança de perímetro de rede com segurança de ponto](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Opções de [otimização incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) para o tráfego do Microsoft 365
- O [teste de conectividade do Microsoft 365](https://aka.ms/netonboard), uma nova ferramenta para testar a conectividade básica com o Microsoft 365

## <a name="microsoft-365-architecture"></a>Arquitetura do Microsoft 365
<a name="BKMK_Architecture"> </a>

A Microsoft 365 é uma nuvem de software (SaaS) distribuída que oferece cenários de produtividade e colaboração por meio de um conjunto variado de micro serviços e aplicativos, como o Exchange Online, o SharePoint Online, o Skype for Business Online, o Microsoft Teams, o Exchange Online Protection, o Office em um navegador e muitos outros. Embora aplicativos específicos do Microsoft 365 possam ter seus recursos exclusivos como se aplicam à rede do cliente e à conectividade com a nuvem, todos eles compartilham algumas principais entidades, metas e padrões de arquitetura. Essas entidades e os padrões de arquitetura para a conectividade são típicos para muitas outras nuvens de SaaS e, ao mesmo tempo, ser muito diferentes dos modelos de implantação típicos de nuvens de plataforma como serviço e infraestrutura como serviço, como o Microsoft Azure.
  
Um dos recursos arquitetônicos mais significativos do Microsoft 365 (que é freqüentemente perdido ou mal interpretado pelos planejadores de rede) é que ele é um serviço distribuído verdadeiramente global, no contexto de como os usuários se conectam a ele. O local do Microsoft 365 locatário de destino é importante para entender a localidade de onde os dados do cliente são armazenados na nuvem, mas a experiência do usuário com a Microsoft 365 não envolve a conexão direta com os discos que contêm os dados. A experiência do usuário com o Microsoft 365 (incluindo desempenho, confiabilidade e outras características de qualidade importantes) envolve a conectividade por meio de uma conexão de front Doors de serviço altamente distribuído que são dimensionadas entre centenas de locais da Microsoft em todo o mundo. Na maioria dos casos, a melhor experiência do usuário é alcançada permitindo que a rede do cliente encaminhe as solicitações do usuário para o ponto de entrada mais próximo do serviço Microsoft 365, em vez de se conectar ao Microsoft 365 por meio de um ponto de saída em um local ou região central.
  
Para a maioria dos clientes, os usuários do Microsoft 365 são distribuídos em vários locais. Para obter os melhores resultados, os princípios descritos neste documento devem ser examinados do ponto de vista de dimensionamento (sem escala), concentrando-se na otimização da conectividade para o ponto mais próximo de presença na rede global da Microsoft, não na localização geográfica do locatário do Microsoft 365. Em essência, isso significa que, embora os dados do locatário do Microsoft 365 possam ser armazenados em um local geográfico específico, a experiência da Microsoft 365 para esse locatário permanece distribuída e pode estar presente em proximidade (rede) para cada local de usuário final que o locatário tem.
  
## <a name="microsoft-365-connectivity-principles"></a>Princípios de conectividade do Microsoft 365
<a name="BKMK_Principles"> </a>

A Microsoft recomenda os princípios a seguir para obter a melhor conectividade e o desempenho do Microsoft 365. Use estes princípios de conectividade do Microsoft 365 para gerenciar seu tráfego e obter o melhor desempenho ao se conectar ao Microsoft 365.
  
O objetivo principal no design de rede deve ser minimizar a latência reduzindo o tempo de resposta (RTT) da sua rede para a rede global da Microsoft, o backbone de rede pública da Microsoft que interconecta todos os datacenters da Microsoft com pontos de entrada de baixa latência e de aplicativos de nuvem espalhados pelo mundo. Você pode saber mais sobre a rede global da Microsoft em [como a Microsoft cria sua rede global rápida e confiável](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Identificar e diferenciar o tráfego do Microsoft 365

![Identificar o tráfego do Microsoft 365](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Identificar o tráfego de rede do Microsoft 365 é a primeira etapa para ser capaz de diferenciar esse tráfego de tráfego de rede genérico associado à Internet. A conectividade Microsoft 365 pode ser otimizada implementando uma combinação de abordagens como otimização de rota de rede, regras de firewall, configurações de proxy do navegador e bypass de dispositivos de inspeção de rede para determinados pontos de extremidade.
  
Diretrizes anteriores de otimização da Microsoft 365 divididas pontos de extremidade do Microsoft 365 em duas categorias, **obrigatórias** e **opcionais**. À medida que os pontos de extremidade foram adicionados para suportar novos serviços e recursos do Microsoft 365, reorganizamos pontos de extremidade do Microsoft 365 em três categorias: **otimizar**, **permitir** e **padrão**. As diretrizes para cada categoria se aplicam a todos os pontos de extremidade da categoria, facilitando a compreensão e a implementação de otimizações.
  
Para obter mais detalhes sobre as categorias de ponto de extremidade do Microsoft 365, consulte a seção [novas categorias de pontos de extremidade do Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Agora, a Microsoft publica todos os pontos de extremidade do Microsoft 365 como um serviço Web e fornece orientações sobre como usar esses dados. Para obter mais informações sobre como buscar e trabalhar com pontos de extremidade do Microsoft 365, consulte o artigo sobre [URLs e intervalos de endereços IP do Office 365](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Enviar conexões de rede de saída localmente

![Enviar conexões de rede de saída localmente](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
O DNS local e o egresso da Internet são fundamentais para reduzir a latência de conexão e garantir que as conexões de usuário sejam feitas para o ponto de entrada mais próximo dos serviços do Microsoft 365. Em uma topologia de rede complexa, é importante implementar o egresso local de DNS e a Internet. Para obter mais informações sobre como o Microsoft 365 roteia conexões de cliente para o ponto de entrada mais próximo, consulte o artigo [Client Connectivity](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Antes do surgimento de serviços em nuvem como o Microsoft 365, a conectividade de Internet do usuário final como um fator de design na arquitetura de rede era relativamente simples. Quando os serviços de Internet e os sites são distribuídos em todo o mundo, a latência entre os pontos de egresso corporativos e qualquer ponto de extremidade de destino é basicamente uma função de distância geográfica.
  
Em uma arquitetura de rede tradicional, todas as conexões de saída da Internet atravessam a rede corporativa e saem de um local central. À medida que as ofertas de nuvem da Microsoft ficaram amadurecedas, uma arquitetura de rede distribuída voltada para a Internet se tornou crítica para o suporte a serviços em nuvem sensíveis à latência. A rede global da Microsoft foi projetada para acomodar requisitos de latência com a infraestrutura de porta frontal de serviço distribuído, uma malha dinâmica de pontos de entrada globais que roteia conexões de serviço de nuvem de entrada para o ponto de entrada mais próximo. Isso se destina a reduzir o tamanho da "última milha" para os clientes do Microsoft Cloud, reduzindo efetivamente a rota entre o cliente e a nuvem.
  
As WANs corporativas geralmente são projetadas para backhaul o tráfego de rede para um escritório central da empresa para inspeção antes da saída para a Internet, geralmente por meio de um ou mais servidores proxy. O diagrama a seguir ilustra essa topologia de rede.
  
![Modelo de rede corporativa tradicional](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Como o Microsoft 365 é executado na rede global da Microsoft, que inclui servidores front-end em todo o mundo, muitas vezes haverá um servidor front-end próximo ao local do usuário. Ao fornecer a saída da Internet local e configurar servidores DNS internos para fornecer resolução de nomes locais para os pontos de extremidade do Microsoft 365, o tráfego de rede destinado ao Microsoft 365 pode se conectar aos servidores front-end da Microsoft 365 o mais próximo possível do usuário. O diagrama abaixo mostra um exemplo de topologia de rede que permite que os usuários se conectem do escritório principal, filiais e locais remotos para acompanhar a rota mais curta para o ponto de entrada mais próximo do Microsoft 365.
  
![Modelo de rede WAN com pontos de saída regionais](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
A redução do caminho de rede para os pontos de entrada do Microsoft 365 dessa forma pode melhorar o desempenho da conectividade e a experiência do usuário final no Microsoft 365 e também pode ajudar a reduzir o impacto das futuras alterações na arquitetura de rede no desempenho e na confiabilidade do Microsoft 365.
  
Além disso, as solicitações de DNS podem apresentar latência se o servidor DNS de resposta estiver distante ou ocupado. Você pode minimizar a latência de resolução de nome ao provisionar os servidores DNS locais em locais de filiais e garantir que eles sejam configurados para armazenar em cache os registros DNS de forma apropriada.
  
Embora a saída regional possa funcionar bem para o Microsoft 365, o modelo de conectividade ideal seria sempre fornecer egresso de rede no local do usuário, independentemente se isso está na rede corporativa ou locais remotos, como casa, hotéis, lanchonetes e aeroportos. Esse modelo de egresso direta local é representado no diagrama abaixo.
  
![Arquitetura de rede de saída local](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
As empresas que adotaram o Microsoft 365 podem aproveitar a arquitetura de porta frontal de serviço distribuído da rede global da Microsoft, assegurando que as conexões de usuário para a Microsoft 365 tenham a rota mais curta possível para o ponto de entrada de rede global da Microsoft mais próximo. A arquitetura de rede de saída local faz isso permitindo que o tráfego do Microsoft 365 seja roteado através da saída mais próxima, independentemente do local do usuário.
  
A arquitetura de egresso local tem os seguintes benefícios em relação ao modelo tradicional:
  
- Oferece o melhor desempenho da Microsoft 365, otimizando o tamanho da rota. As conexões de usuário final são direcionadas dinamicamente para o ponto de entrada mais próximo da Microsoft 365 pela infraestrutura de porta frontal de serviço distribuído.
- Reduz a carga na infraestrutura de rede corporativa, permitindo a saída local.
- Protege as conexões em ambas as extremidades, aproveitando a segurança do ponto de extremidade do cliente e os recursos de segurança na nuvem.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Evitar hairpins de rede

![Evitar hairpins](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Como regra geral, a rota mais curta e direta entre o usuário e o ponto de extremidade mais próximo do Microsoft 365 oferecerá o melhor desempenho. Um hairpin de rede ocorre quando o tráfego de WAN ou VPN vinculado a um determinado destino é direcionado primeiro para outro local intermediário (como pilha de segurança, agente de acesso à nuvem, do gateway da Web baseado em nuvem), apresentando latência e redirecionamento em potencial para um ponto de extremidade distante geograficamente. O hairpins de rede também pode ser causado por ineficiências de roteamento/emparelhamento ou de buscas de DNS de baixo (remoto).
  
Para garantir que a conectividade do Microsoft 365 não esteja sujeita à rede hairpins mesmo no caso de egresso local, verifique se o provedor de serviço de Internet usado para fornecer egresso de Internet para o local de usuário tem uma relação de emparelhamento direto com a rede global da Microsoft em proximidade com esse local. Você também pode configurar o roteamento de saída para enviar diretamente o tráfego confiável da Microsoft 365, em vez de fazer o proxy ou o encapsulamento por meio de uma nuvem de terceiros ou um fornecedor de segurança de rede baseado em nuvem que processa seu tráfego de Internet. A resolução de nomes DNS locais de pontos de extremidade do Microsoft 365 ajuda a garantir que, além do roteamento direto, os pontos de entrada do Microsoft 365 mais próximos estejam sendo usados para conexões de usuário.
  
Se você usar a rede baseada em nuvem ou serviços de segurança para o seu tráfego do Microsoft 365, certifique-se de que o efeito grampeamento seja avaliado e que seu impacto no desempenho da Microsoft 365 seja compreendido. Isso pode ser feito examinando o número e os locais dos locais do provedor de serviços por meio dos quais o tráfego é encaminhado em relação ao número de seus escritórios de filiais e pontos de emparelhamento da rede global da Microsoft, qualidade da relação de emparelhamento de rede do provedor de serviços com seu ISP e a Microsoft e o impacto de desempenho da infraestrutura de serviço.
  
Devido ao grande número de locais distribuídos com pontos de entrada do Microsoft 365 e sua proximidade com os usuários finais, o roteamento de tráfego da Microsoft 365 para qualquer rede de terceiros ou provedor de segurança pode ter um impacto adverso nas conexões do Microsoft 365 se a rede do provedor não estiver configurada para o emparelhamento do Microsoft 365 ideal.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Avaliar o bypass de proxies, dispositivos de inspeção de tráfego e tecnologias de segurança duplicadas

![Ignorar proxies, dispositivos de inspeção de tráfego e tecnologias de segurança duplicadas](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Os clientes corporativos devem revisar os métodos de segurança de rede e de redução de risco especificamente para o tráfego de entrada da Microsoft 365 e usar os recursos de segurança do Microsoft 365 para reduzir a confiança no impacto intrusivo, no desempenho e nas tecnologias caras de segurança de rede para o tráfego de rede do Microsoft 365
  
A maioria das redes corporativas impõe a segurança de rede para o tráfego da Internet usando tecnologias como proxies, inspeção de SSL, inspeção de pacote e sistemas de prevenção contra perda de dados. Essas tecnologias oferecem uma redução de risco importante para solicitações de Internet genéricas, mas podem reduzir drasticamente o desempenho, a escalabilidade e a qualidade da experiência do usuário final quando aplicadas aos pontos de extremidade do Microsoft 365.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Serviço Web de pontos de extremidade do Office 365

Os administradores do Microsoft 365 podem usar um script ou uma chamada REST para consumir uma lista estruturada de pontos de extremidade do serviço Web de pontos de extremidade do Office 365 e atualizar as configurações de firewalls de perímetro e outros dispositivos de rede. Isso garantirá que o tráfego associado ao Microsoft 365 seja identificado, tratado apropriadamente e gerenciado de forma diferente do tráfego de rede de acordo com os sites genéricos e geralmente desconhecidos da Internet. Para obter mais informações sobre como usar o serviço Web de pontos de extremidade do Office 365, consulte o artigo sobre [URLs e intervalos de endereços IP do office 365](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Scripts de PAC (configuração automática de proxy)
<a name="BKMK_WebSvc"> </a>

Os administradores do Microsoft 365 podem criar scripts de PAC (configuração automática de proxy) que podem ser entregues a computadores do usuário via WPAD ou GPO. Os scripts de PAC podem ser usados para ignorar proxies para solicitações do Microsoft 365 de usuários de WAN ou VPN, permitindo que o tráfego da Microsoft 365 use conexões diretas com a Internet, em vez de atravessar a rede corporativa.
  
#### <a name="microsoft-365-security-features"></a>Recursos de segurança do Microsoft 365
<a name="BKMK_WebSvc"> </a>

A Microsoft é transparente sobre a segurança de datacenter, a segurança operacional e a redução de riscos em torno dos servidores da Microsoft 365 e dos pontos de extremidade de rede que representam. Os recursos de segurança internos do Microsoft 365 estão disponíveis para reduzir o risco de segurança de rede, como prevenção contra perda de dados, antivírus, autenticação multifator, caixa de bloqueio de cliente, proteção avançada contra ameaças, Microsoft 365 Threat Intelligence, Microsoft 365 recorde, proteção do Exchange Online e segurança de DDOS de rede.
  
Para obter mais informações sobre o Microsoft datacenter e a segurança de rede global, consulte a [central de confiabilidade da Microsoft](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Novas categorias de pontos de extremidade do Office 365
<a name="BKMK_Categories"> </a>

Os pontos de extremidade do Office 365 representam um conjunto variado de endereços de rede e sub-redes. Os pontos de extremidade podem ser URLs, endereços IP ou intervalos IP e alguns pontos de extremidade são listados com portas TCP/UDP específicas. URLs podem ser um FQDN como *Account.Office.net* ou uma URL curinga como * \* . office365.com*.
  
> [!NOTE]
> Os locais dos pontos de extremidade do Office 365 dentro da rede não estão diretamente relacionados ao local dos dados de locatário do Microsoft 365. Por esse motivo, os clientes devem examinar o Microsoft 365 como um serviço distribuído e global e não devem tentar bloquear conexões de rede para pontos de extremidade do Office 365 com base nos critérios geográficos.
  
Em nossa orientação prévia para gerenciar o tráfego do Microsoft 365, os pontos de extremidade foram organizados em duas categorias, **obrigatórias** e **opcionais**. Os pontos de extremidade dentro de cada categoria exigiam otimizações diferentes dependendo da criticalidade do serviço, e muitos clientes enfrentam desafios para justificar o aplicativo das mesmas otimizações de rede à lista completa de URLs e endereços IP do Office 365.
  
No novo modelo, os pontos de extremidade são separados em três categorias, **otimizar**, **permitir** e **padrão**, fornecendo uma tabela dinâmica baseada em prioridades em que você deve concentrar os esforços de otimização de rede para obter os melhores aprimoramentos de desempenho e retorno sobre o investimento. Os pontos de extremidade são consolidados nas categorias acima com base na confidencialidade da experiência de usuário efetiva para a qualidade da rede, o envelope de volume e desempenho de cenários e a facilidade de implementação. As otimizações recomendadas podem ser aplicadas da mesma maneira a todos os pontos de extremidade em uma determinada categoria.
  
- **Otimizar** pontos de extremidade é necessário para conectividade a cada serviço do Office 365 e representar mais de 75% de largura de banda, conexões e volume de dados do Office 365. Esses pontos de extremidade representam cenários do Office 365 que são mais confidenciais para desempenho da rede, latência e disponibilidade. Todos os pontos de extremidade são hospedados em datacenters da Microsoft. A taxa de alteração para os pontos de extremidade desta categoria deve ser muito menor do que os pontos de extremidade nas outras duas categorias. Esta categoria inclui um conjunto muito pequeno (na ordem de aproximadamente 10) de URLs de chave e um conjunto definido de sub-redes IP dedicadas às cargas de trabalho principais do Office 365, como o Exchange Online, o SharePoint Online, o Skype for Business Online e o Microsoft Teams.

    Uma lista condensada de pontos de extremidade críticos bem definidos deve ajudá-lo a planejar e implementar otimizações de rede de alto valor para esses destinos de forma mais rápida e fácil.

    Exemplos de *otimização* de pontos de extremidade incluem *https://outlook.office365.com* , *https:// \<tenant\> . SharePoint.com* e *https:// \<tenant\> -My.SharePoint.com* .

    Os métodos de otimização incluem:

  - Bypass ou whitelist *otimiza* pontos de extremidade em dispositivos de rede e serviços que realizam interceptação de tráfego, descriptografia SSL, inspeção de pacote profunda e filtragem de conteúdo.
  - Ignorar dispositivos de proxy locais e serviços de proxy baseados em nuvem comumente usados para a navegação genérica na Internet.
  - Priorize a avaliação desses pontos de extremidade como totalmente confiáveis para sua infraestrutura de rede e sistemas de perímetro.
  - Priorize a redução ou a eliminação de inviabilização de WAN e facilite a saída direta com base na Internet para esses pontos de extremidade próximos aos usuários/locais de filiais.
  - Facilite a conectividade direta para esses pontos de extremidade de nuvem para usuários VPN implementando o túnel de divisão.
  - Verifique se os endereços IP retornados pela resolução de nomes DNS correspondem ao caminho de egresso de roteamento desses pontos de extremidade.
  - Priorize esses pontos de extremidade para a integração SD-WAN para roteamento de latência direta e mínima para o ponto de emparelhamento da Internet mais próximo da rede global da Microsoft.

- **Permite que** os pontos de extremidade sejam necessários para conectividade com serviços e recursos específicos do Office 365, mas não são tão sensíveis ao desempenho e à latência da rede que os da categoria *otimizar* . A superfície geral da rede desses pontos de extremidade do ponto de vista da contagem de largura de banda e de conexão também é significativamente menor. Esses pontos de extremidade são dedicados ao Office 365 e são hospedados em datacenters da Microsoft. Eles representam um amplo conjunto de serviços do Office 365 e suas dependências (na ordem de ~ 100 URLs) e devem mudar com uma taxa mais alta do que aqueles na categoria *otimizar* . Nem todos os pontos de extremidade desta categoria estão associados a sub-redes IP dedicadas definidas.

    Otimizações de rede para *permitir* pontos de extremidade podem melhorar a experiência do usuário do Office 365, mas alguns clientes podem optar por fazer o escopo dessas otimizações de forma mais estreita para minimizar as alterações em sua rede.

    Exemplos de *permitir* pontos de extremidade incluem *https:// \* . Protection.Outlook.com* e *https://accounts.accesscontrol.windows.net* .

    Os métodos de otimização incluem:

  - Bypass ou whitelist *permite* pontos de extremidade em dispositivos de rede e serviços que realizam interceptação de tráfego, descriptografia SSL, inspeção de pacote profunda e filtragem de conteúdo.
  - Priorize a avaliação desses pontos de extremidade como totalmente confiáveis para sua infraestrutura de rede e sistemas de perímetro.
  - Priorize a redução ou a eliminação de inviabilização de WAN e facilite a saída direta com base na Internet para esses pontos de extremidade próximos aos usuários/locais de filiais.
  - Verifique se os endereços IP retornados pela resolução de nomes DNS correspondem ao caminho de egresso de roteamento desses pontos de extremidade.
  - Priorize esses pontos de extremidade para a integração SD-WAN para roteamento de latência direta e mínima para o ponto de emparelhamento da Internet mais próximo da rede global da Microsoft.

- **Os** pontos de extremidade padrão representam os serviços e dependências do Office 365 que não exigem otimização e que podem ser tratados por redes de clientes como tráfego de entrada da Internet normal. Observe que alguns pontos de extremidade nesta categoria podem não estar hospedados nos datacenters da Microsoft. Os exemplos incluem *https://odc.officeapps.live.com* e *https://appexsin.stb.s-msn.com* .

Para obter mais informações sobre as técnicas de otimização de rede do Office 365, consulte o artigo [Managing office 365 Endpoints](https://support.office.com/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Comparando a segurança de perímetro de rede com segurança de ponto
<a name="BKMK_SecurityComparison"> </a>

O objetivo da segurança de rede tradicional é reforçar o perímetro da rede corporativa contra invasão e explorações mal-intencionadas. À medida que as organizações adotam o Microsoft 365, alguns serviços e dados de rede são parcialmente ou completamente migrados para a nuvem. Como acontece com qualquer alteração fundamental na arquitetura de rede, esse processo requer uma reavaliação da segurança de rede que leva em conta os fatores emergentes:
  
- À medida que os serviços de nuvem são adotados, os serviços de rede e os dados são distribuídos entre os data centers locais e a nuvem, e a segurança de perímetro não é mais adequada por conta própria.
- Os usuários remotos se conectam aos recursos corporativos em datacenters locais e na nuvem de locais não controlados, como residências, hotéis e lanchonetes.
- Os recursos de segurança criados por finalidade estão cada vez mais incorporados aos serviços em nuvem e podem potencialmente complementar ou substituir sistemas de segurança existentes.

A Microsoft oferece uma ampla variedade de recursos de segurança da Microsoft 365 e fornece orientação prescritiva para o emprego de práticas recomendadas de segurança que podem ajudar a garantir a segurança de dados e de rede para o Microsoft 365. As práticas recomendadas são as seguintes:
  
- **Usar a protocolo de autenticação multifator (MFA)** A MFA adiciona uma camada adicional de proteção a uma estratégia de senha forte, exigindo que os usuários reconheçam uma chamada telefônica, uma mensagem de texto ou uma notificação de aplicativo em seu telefone inteligente após a inserção correta da senha.

- **Usar o Microsoft Cloud app Security** Configurar políticas para controlar atividades anômalas e agir sobre ela. Configurar alertas com o Microsoft Cloud app Security para que os administradores possam examinar atividades de usuário incomuns ou arriscadas, como baixar grandes quantidades de dados, várias tentativas de entrada com falha ou conexões de endereços IP desconhecidos ou perigosos.

- **Configurar a DLP (prevenção contra perda de dados)** O DLP permite identificar dados confidenciais e criar políticas que ajudam a evitar que os usuários compartilhem acidentalmente ou intencionalmente os dados. A DLP funciona no Microsoft 365, incluindo o Exchange Online, o SharePoint Online e o OneDrive para que os usuários possam permanecer em conformidade sem interromper o fluxo de trabalho.

- **Usar Lockbox de cliente** Como um administrador do Microsoft 365, você pode usar o Lockbox do cliente para controlar como um engenheiro de suporte da Microsoft acessa seus dados durante uma sessão de ajuda. Em casos em que o engenheiro requer acesso aos dados para solucionar e corrigir um problema, o Sistema de Proteção de Dados do Cliente permite que você aprove ou rejeite a solicitação de acesso.

- **Usar a pontuação segura do Office 365** A pontuação segura é uma ferramenta de análise de segurança que recomenda o que você pode fazer para reduzir ainda mais o risco. A pontuação segura examina suas configurações e atividades do Microsoft 365 e as compara a uma linha de base estabelecida pela Microsoft. Você receberá uma pontuação com base em como o alinhamento está com as práticas recomendadas de segurança.

Uma abordagem holística à segurança avançada deve incluir a consideração do seguinte:
  
- Deslocar a ênfase da segurança de perímetro em relação à segurança do ponto de extremidade aplicando recursos de segurança de cliente do Office e baseado em nuvem.
  - Reduzir o perímetro de segurança para o datacenter
  - Habilitar a confiança equivalente para dispositivos de usuário dentro do escritório ou em locais remotos
  - Foco em proteger o local dos dados e o local do usuário
  - As máquinas de usuário gerenciadas têm confiança maior com segurança de ponto de extremidade
- Gerenciar toda a segurança de informações de forma holística, sem se concentrar exclusivamente no perímetro
  - Redefina o WAN e a criação da segurança de rede de perímetro, permitindo que o tráfego confiável ignore os dispositivos de segurança e separando os dispositivos não gerenciados para redes Wi-Fi convidados.
  - Reduz os requisitos de segurança de rede da borda WAN corporativa
  - Alguns dispositivos de segurança de perímetro de rede, como firewalls, ainda são necessários, mas a carga é reduzida
  - Garante o egresso local para o tráfego do Microsoft 365
- Os aprimoramentos podem ser abordados em incrementos, conforme descrito na seção [otimização incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) . Algumas técnicas de otimização podem oferecer melhores taxas de custo/benefício, dependendo da arquitetura da rede, e você deve escolher otimizações que fazem mais sentido para sua organização.

Para obter mais informações sobre segurança e conformidade do Microsoft 365, consulte o artigo [visão geral de segurança e conformidade no Office 365](https://support.office.com/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## <a name="incremental-optimization"></a>Otimização incremental
<a name="BKMK_IncOpt"> </a>

Nós representamos o modelo de conectividade de rede ideal para o SaaS anteriormente neste artigo, mas, para muitas organizações grandes, com arquiteturas de rede complexas históricas, não será prático fazer todas essas alterações diretamente. Nesta seção, discutimos várias alterações incrementais que podem ajudar a melhorar o desempenho e a confiabilidade do Microsoft 365.
  
Os métodos que você usará para otimizar o tráfego do Microsoft 365 irão variar dependendo da sua topologia de rede e dos dispositivos de rede que você implementou. Grandes empresas com vários locais e práticas de segurança de rede complexas precisarão desenvolver uma estratégia que inclua a maioria ou todos os princípios listados na seção [princípios de conectividade do Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Principles) , enquanto organizações menores podem apenas considerar um ou dois.
  
Você pode abordar a otimização como um processo incremental, aplicando cada método sucessivamente. A tabela a seguir lista os principais métodos de otimização em ordem de impacto na latência e confiabilidade para o maior número de usuários.
  
|**Método de otimização**|**Descrição**|**Impacto**|
|:-----|:-----|:-----|
|Resolução de DNS local e saída de Internet  <br/> |Provisione servidores DNS locais em cada local e certifique-se de que o Microsoft 365 conexões de saída para a Internet o mais próximo possível do local do usuário.  <br/> | Minimizar latência  <br/>  Melhorar a conectividade confiável para o ponto de entrada mais próximo do Microsoft 365  <br/> |
|Adicionar pontos de saída regionais  <br/> |Se sua rede corporativa tiver vários locais, mas apenas um ponto de saída, adicione pontos de saída regionais para permitir que os usuários se conectem ao ponto de entrada do Microsoft 365 mais próximo.  <br/> | Minimizar latência  <br/>  Melhorar a conectividade confiável para o ponto de entrada mais próximo do Microsoft 365  <br/> |
|Ignorar proxies e dispositivos de inspeção  <br/> |Configure navegadores com arquivos de PAC que enviam solicitações do Microsoft 365 diretamente aos pontos de saída.  <br/> Configure roteadores de borda e firewalls para permitir o tráfego do Microsoft 365 sem inspeção.  <br/> | Minimizar latência  <br/>  Reduzir a carga nos dispositivos de rede  <br/> |
|Habilitar conexão direta para usuários VPN  <br/> |Para usuários VPN, habilite conexões Microsoft 365 para se conectar diretamente a partir da rede do usuário, e não do túnel VPN, implementando o túnel de divisão.  <br/> | Minimizar latência  <br/>  Melhorar a conectividade confiável para o ponto de entrada mais próximo do Microsoft 365  <br/> |
|Migrar da WAN tradicional para o SD-WAN  <br/> |SD-WANs (redes de longa distância definidas pelo software) simplificam o gerenciamento de WAN e aprimoram o desempenho substituindo roteadores WAN tradicionais por dispositivos virtuais, semelhante à virtualização de recursos de computação usando VMs (máquinas virtuais).  <br/> | Melhorar o desempenho e a capacidade de gerenciamento do tráfego de WAN  <br/>  Reduzir a carga nos dispositivos de rede  <br/> |

## <a name="related-topics"></a>Tópicos Relacionados

[Visão geral da conectividade de rede do Microsoft 365](office-365-networking-overview.md)

[Gerenciar pontos de extremidade do Office 365](managing-office-365-endpoints.md)

[URLs e intervalos de endereços IP do Office 365](urls-and-ip-address-ranges.md)

[URL do serviço Web e endereço IP do Office 365](office-365-ip-web-service.md)

[Avaliando a conectividade de rede do Microsoft 365](assessing-network-connectivity.md)

[Planejamento de rede e ajuste de desempenho para o Microsoft 365](network-planning-and-performance.md)

[Ajuste de desempenho do Office 365 usando linhas de base e histórico de desempenho](performance-tuning-using-baselines-and-history.md)

[Plano de solução de problemas de desempenho do Office 365](performance-troubleshooting-plan.md)

[Redes de Distribuição de Conteúdo](content-delivery-networks.md)

[Teste de conectividade do Microsoft 365](https://aka.ms/netonboard)

[Como a Microsoft cria sua rede global rápida e confiável](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog de rede do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
