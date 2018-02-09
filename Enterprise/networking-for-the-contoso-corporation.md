---
title: Sistema de rede para a Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: "Resumo: Entenda a definição e elementos de nuvem da Microsoft híbrida."
ms.openlocfilehash: 1f023364c4b2e9c64af954ec9ba63a6197ebc01a
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="networking-for-the-contoso-corporation"></a>Sistema de rede para a Contoso Corporation

 **Resumo:** Compreenda a definição e elementos de nuvem da Microsoft híbrida.
  
Para adotar uma infra-estrutura inclusive de nuvem, engenheiros de rede da Contoso concretizados do turno fundamental da maneira que o tráfego de rede para viagens de serviços em nuvem. Em vez de apenas otimizar o tráfego para os servidores locais e data centers, igual atenção à otimização de tráfego até a borda da Internet e pela Internet.
  
## <a name="contosos-networking-infrastructure"></a>Infraestrutura de rede da Contoso

A Contoso tem a infra-estrutura de rede mostrada na Figura 1.
  
**Figura 1: WAN de infra-estrutura da Contoso**

![Infraestrutura WAN da Contoso conectando a sede, os centros regionais e as filiais](images/Contoso_Poster/Contoso_WW_Net.png)
  
A Figura 1 mostra os escritórios da Contoso em todo o mundo e o conjunto de regionais e links de WAN office satélite entre elas.
  
Elementos adicionais de sua rede são as seguintes:
  
- Rede local
    
    Links de WAN conectam as matrizes Paris para escritórios regionais e escritórios regionais em escritórios satélites em uma configuração de hub e spoke. Dentro de cada escritório, roteadores entregar o tráfego para hosts ou pontos de acesso sem fio em sub-redes, que usa o espaço de endereço IP particular.
    
- Conectividade com a Internet
    
    Cada escritório tem seu próprio conectividade de Internet por meio de um servidor proxy. Isso geralmente é implementado como uma WAN link para um provedor de local que também fornece endereços IP públicos para o servidor proxy.
    
- Presença na Internet
    
    A Contoso possui o nome de domínio público de contoso.com. O site web público de Contoso para encomendar produtos é um conjunto de servidores em um datacenter conectados à Internet no campus Paris. A Contoso usa um /24 intervalo de endereços IP público na Internet.
    
## <a name="contosos-app-infrastructure"></a>Infraestrutura de app da Contoso

Arquitetura do Contoso criada sua infraestrutura de aplicativo e servidor para o seguinte:
  
**Figura 2: Infra-estrutura da Contoso para aplicativos internos**

![Infraestrutura da Contoso para aplicativos internos](images/Contoso_Poster/App_Infra.png)
  
- Filiais usam servidores locais de armazenamento em cache para armazenar documentos acessados frequentemente e sites internos.
    
- Hubs regionais usam servidores de aplicativos regionais para regionais e de filiais. Esses servidores sincronizam com servidores na matriz da Paris.
    
- O campus Paris tem os datacenters que contêm os servidores de aplicativos centralizado que atendem a toda a organização.
    
Para usuários de satélite ou escritórios regionais de hub, 60% dos recursos necessários pelos funcionários podem ser atendidas por servidores do office hub regionais e de satélite. Vincular a 40% adicionais de recurso solicitações devem passar pela WAN campus da Paris.
  
## <a name="contosos-network-analysis"></a>Análise de rede da Contoso

Aqui estão os resultados da análise da Contoso das alterações necessárias em sua rede para acomodar as diferentes categorias de ofertas de nuvem da Microsoft:
  
|**SaaS ofertas de nuvem: Office 365, EMS e Dynamics 365**|**Azure PaaS: Aplicativos móveis**|**Windows Azure IaaS: Cargas de trabalho baseado em servidor**|
|:-----|:-----|:-----|
|Adoção bem-sucedida dos serviços de SaaS pelos usuários depende altamente disponível e de alto desempenho conectividade à Internet ou diretamente aos serviços de nuvem da Microsoft.  <br/> Para usuários móveis, seu acesso à Internet atual é assumido para ser adequado.  <br/> Para os usuários na intranet da Contoso, cada escritório deve ser analisado e otimizado para taxa de transferência para a Internet e tempos de ida e volta para os locatários do Office 365, EMS e Dynamics 365 de hospedagem do datacenter de Europa da Microsoft.  <br/> |Os funcionários móveis da melhor suporte, aplicativos herdados e alguns sites de compartilhamento de arquivo estão sendo refeitas e implantados como aplicativos do Windows Azure PaaS. Para obter o desempenho ideal, Contoso planeja implantar aplicativos novos a partir de vários centros de dados Azure no mundo inteiro. Gerenciador de tráfego do Azure para enviar o cliente solicitações de aplicativos, se elas se originam de um usuário móvel ou em um computador no escritório, para o datacenter do Windows Azure mais próximo do aplicativo de hospedagem.  <br/>  O departamento de TI precisará adicionar PaaS o desempenho de aplicativos e distribuição de tráfego à sua solução de monitoramento de integridade de rede. <br/> |Para mover alguns servidores herdados e arquivamento sem os datacenters de campus Paris e adicionar servidores conforme necessário para o processamento de ponta trimestre, Contoso planeja usar máquinas virtuais executando nos serviços de infraestrutura do Windows Azure.  <br/> As redes virtuais do Azure que contêm esses servidores devem ser projetadas para espaços de endereçamento não sobrepostos, DNS roteamento e integrada.  <br/> O departamento de TI deve incluir esses novos servidores em seus gerenciamento de rede e o sistema de monitoramento.  <br/> |
   
## <a name="contosos-use-of-expressroute"></a>Uso da Contoso do ExpressRoute

ExpressRoute é uma conexão WAN dedicada de seu local para um local de correspondência do Microsoft que se conecta a sua rede a rede de nuvem da Microsoft. As conexões de ExpressRoute oferecem desempenho previsível e um SLA do tempo de atividade de 99,9%. .
  
Com uma conexão ExpressRoute, você está conectado à rede de nuvem da Microsoft e todos os locais de datacenter Microsoft no mesmo continente. O tráfego entre o local de correspondência da nuvem e o datacenter da Microsoft de destino é transmitido a rede de nuvem da Microsoft
  
**Figura 3: A Microsoft cloud rede mundial**

![A rede de nuvem da Microsoft em todo o mundo](images/Contoso_Poster/MS_WW_Cloud.png)
  
A Figura 3 mostra a rede de nuvem Microsoft interconexão para as diversas regiões do mundo.
  
Com o ExpressRoute Premium, você poderá encontrá-qualquer datacenter da Microsoft em qualquer continente de qualquer local de correspondência da Microsoft em qualquer continente. O tráfego entre continentes é realizado através da rede de nuvem da Microsoft.
  
Com base na análise de tráfego atual e futuro para as ofertas de nuvem da Microsoft, a Contoso tem realizou uma avaliação de rede e implementado uma conexão ExpressRoute (baseado em MPLS) para qualquer para acesso aos recursos do Windows Azure, com correspondência pública e privada relações de confiança, das matrizes Paris até o local de correspondência da Microsoft na Europa.
  
Esta conexão fornecerá a Contoso departamento de TI:
  
- Desempenho consistente para a administração dos aplicativos do Windows Azure PaaS distribuídas
    
    Todos de desenvolvedores de aplicativos e a infraestrutura principal IT da Contoso, os administradores são no campus Paris. Com aplicativos do Azure PaaS distribuídos para diferentes datacenters Azure em todo o mundo, a Contoso precisa desempenho consistente do campus da Paris para administrar os aplicativos e seus recursos de armazenamento, que consistem em TB de documentos.
    
- Desempenho consistente para a administração de servidores no Azure IaaS
    
    Administradores de datacenter da Contoso estão em campus da Paris e os servidores a serem implantados no Azure são uma extensão do datacenter Paris. A Contoso precisa desempenho consistente para esses novos servidores para acessar aplicativos herdados e armazenamento de arquivamento e para o processamento de final de trimestre.
    
## <a name="contosos-path-to-cloud-networking-readiness"></a>Caminho da Contoso para preparação de rede em nuvem

A Contoso usa as seguintes etapas para preparar sua rede para a nuvem da Microsoft:
  
1. Otimizar os computadores dos funcionários para acesso à Internet
    
    Computadores individuais serão verificados para garantir que a pilha de TCP/IP mais recente, navegador, os drivers de placa de rede e atualizações de segurança e o sistema operacional estão instaladas.
    
2. Analisar a utilização de conexão de Internet em cada escritório e aumentar conforme necessário
    
    Cada escritório será analisado para o uso de Internet atual e a largura de banda do link WAN será aumentada se operando 70% ou acima de utilização.
    
3. Analisar sistemas DMZ em cada escritório para um desempenho ideal
    
    Firewalls, IDSs e outros sistemas no caminho da Internet serão analisados para um desempenho ideal. Servidores proxy serão atualizados ou atualizados conforme necessário.
    
4. Adicionar ExpressRoute do campus da Paris
    
    Fornece acesso uniforme aos recursos do Windows Azure para a administração de cargas de trabalho Azure PaaS e IaaS.
    
5. Criar e testar um perfil do Gerenciador de tráfego do Windows Azure para aplicativos do Windows Azure PaaS
    
    Teste um perfil do Gerenciador de tráfego do Azure que usa o método de roteamento de desempenho adquira experiência nos distribuir o tráfego da Internet para escritórios regionais.
    
6. Reservar espaço de endereço privado para VNets do Windows Azure
    
    Com base nos números dos servidores projetados de curtos e longo prazo no Azure IaaS, reserve espaço de endereço privado para VNets do Windows Azure e suas sub-redes.
    
## <a name="see-also"></a>Veja também

[Contoso na Microsoft Cloud](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



