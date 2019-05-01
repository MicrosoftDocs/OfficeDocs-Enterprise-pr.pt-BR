---
title: ExpressRoute para conectividade de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/12/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Resumo: entenda como o ExpressRoute pode ajudá-lo com conexões mais rápidas e mais confiáveis para plataformas e serviços em nuvem da Microsoft.'
ms.openlocfilehash: a3b36e98c946bc3ae7281bd38cd4b98820ee8afb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488079"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a>ExpressRoute para conectividade de nuvem da Microsoft

 **Resumo:** Entenda como o ExpressRoute pode ajudá-lo com conexões mais rápidas e mais confiáveis para plataformas e serviços em nuvem da Microsoft.
  
O ExpressRoute oferece uma conexão de rede privada, dedicada e de alta taxa de transferência para a nuvem da Microsoft.
  
## <a name="expressroute-to-the-microsoft-cloud"></a>ExpressRoute para a nuvem da Microsoft

Este é o caminho de rede para a nuvem da Microsoft sem uma conexão ExpressRoute.
  
**Figura 1: o caminho de rede sem o ExpressRoute**

![Figura 1: o caminho de rede sem o ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
A Figura 1 mostra o caminho típico entre uma rede local e a nuvem da Microsoft. A borda de rede local conecta-se à Internet por meio de um link de WAN para um provedor. O tráfego passa pela Internet para a borda da Microsoft Cloud. As ofertas de nuvem no Microsoft Cloud incluem o Office 365, o Microsoft Azure, o Microsoft Intune e o Dynamics 365. Os usuários de uma organização podem estar localizados na rede local ou na Internet.
  
Sem uma conexão ExpressRoute, a única parte do caminho de tráfego para a nuvem da Microsoft que você pode controlar (e ter uma relação com o provedor de serviços) é o link entre sua borda de rede local e seu ISP. 
  
O caminho entre o seu ISP e o Microsoft Cloud Edge é um sistema de entrega de melhor esforço na Internet sujeito a interrupções, congestionamento de tráfego e monitoramento por usuários mal-intencionados.
  
Os usuários na Internet, como usuários móveis ou remotos, enviam o tráfego para a nuvem da Microsoft pela Internet.
  
Estes são os caminhos de rede para a nuvem da Microsoft com uma conexão ExpressRoute.
  
**Figura 2: caminhos de rede com ExpressRoute**

![Figura 2: caminhos de rede com ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
A Figura 2 mostra dois caminhos de rede. O tráfego para o Microsoft Intune viaja para o mesmo caminho que o tráfego de Internet normal. O tráfego para o Office 365, Microsoft Azure e Dynamics 365 passa pela conexão ExpressRoute, um caminho dedicado entre a borda da rede local e a borda da Microsoft Cloud.
  
Com uma conexão ExpressRoute, agora você tem controle, por meio de uma relação com seu provedor de serviços, sobre todo o caminho de tráfego da sua borda para a borda da Microsoft em nuvem. Essa conexão pode oferecer desempenho previsível e um [SLA de tempo de atividade de 99,95%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).
  
Agora, você pode contar com a taxa de transferência e a latência previsíveis, com base na conexão do provedor de serviços, para os serviços do Office 365, Azure e Dynamics 365. As conexões ExpressRoute com o Microsoft Intune não são suportadas no momento.
  
O tráfego enviado pela conexão ExpressRoute não está mais sujeito a interrupções de Internet, congestionamento de tráfego e monitoramento.
  
Os usuários na Internet, como usuários móveis ou remotos, ainda enviam o tráfego para a nuvem da Microsoft pela Internet. Uma exceção é o tráfego para um aplicativo de linha de negócios de intranet hospedado no Azure IaaS, que é enviado pela conexão ExpressRoute por meio de uma conexão de acesso remoto à rede local.
  
Mesmo com uma conexão ExpressRoute, algum tráfego ainda é enviado pela Internet, como consultas de DNS, verificação de lista de certificados revogados e solicitações de rede de distribuição de conteúdo (CDN).
  
ConFira estes recursos adicionais para obter mais informações:
  
- [Rota Expressa para Office 365](https://aka.ms/expressrouteoffice365)
    
- [ExpressRoute para Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a>Vantagens do ExpressRoute para o Azure

Veja algumas vantagens de usar o ExpressRoute para serviços de nuvem baseados no Azure:
  
- **Desempenho previsível:** Com um caminho dedicado para a borda da nuvem da Microsoft, seu desempenho não está sujeito às interrupções e aos picos do provedor de Internet no tráfego da Internet. Você pode determinar e manter seus provedores em sua conta em um SLA de taxa de transferência e latência para a nuvem da Microsoft.
    
- **Privacidade dos dados de seu tráfego:** O tráfego enviado por sua conexão expressa dedicada não está sujeito à monitoração da Internet ou captura de pacotes e análise por usuários mal-intencionados. É tão seguro quanto usar links WAN baseados em comutação de rótulo de multiProtocolo (MPLS).
    
- **Conexões de alto desempenho:** Com amplo suporte para conexões ExpressRoute por provedores do Exchange e provedores de serviços de rede, você pode obter até um link de 10 Gbps para a nuvem da Microsoft.
    
- **Custo mais baixo para algumas configurações:** Embora as conexões de ExpressRoute sejam um custo adicional, em alguns casos, uma única conexão ExpressRoute pode custar menos do que aumentar sua capacidade de Internet em vários locais de sua organização para fornecer uma taxa de transferência adequada para os serviços de nuvem da Microsoft.
    
Uma conexão ExpressRoute não é uma garantia de melhor desempenho em todas as configurações. É possível ter um desempenho menor em relação a uma conexão ExpressRoute de baixa largura de banda do que uma conexão com a Internet de alta largura de banda que seja apenas alguns saltos de um datacenter regional da Microsoft.
  
Para obter as recomendações mais recentes para usar o ExpressRoute com o Office 365, consulte [ExpressRoute para office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).
  
## <a name="expressroute-connectivity-models"></a>Modelos de conectividade ExpressRoute

A tabela 1 mostra os três modelos de conectividade principais para conexões ExpressRoute.
  
|**Localizado em um Exchange na nuvem**|**Ethernet ponto a ponto**|**Conexão de qualquer um (IP VPN)**|
|:-----|:-----|:-----|
|![Modelo de conectividade ExpressRoute: localizado em um Exchange na nuvem](media/Network-Poster/ER-Conn1.png)|![Modelo de conectividade ExpressRoute: Ethernet ponto a ponto](media/Network-Poster/ER-Conn2.png)|![Modelo de conectividade ExpressRoute: conexão de qualquer um (IP VPN)](media/Network-Poster/ER-Conn3.png)|
|Se o seu datacenter estiver localizado em um recurso com uma troca de nuvem, você poderá solicitar uma conexão cruzada virtual para a nuvem da Microsoft por meio do Exchange Ethernet do provedor de colocalização.  <br/> |Se o seu datacenter estiver localizado em seu local, você poderá usar um link Ethernet ponto a ponto para se conectar à nuvem da Microsoft.  <br/> |Se você já estiver usando um provedor de IP VPN (MPLS) para conectar os sites da sua organização, uma conexão ExpressRoute ao Microsoft Cloud funcionará como outro local na sua WAN privada.  <br/> |
   
 **Tabela 1: modelos de conectividade do ExpressRoute**
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a>Relações de emparelhamento de rota para os serviços de nuvem da Microsoft

Uma única conexão ExpressRoute oferece suporte a até dois relacionamentos de emparelhamento do protocolo BGP (Border Gateway Protocol) diferentes para partes diferentes da nuvem da Microsoft. O BPG usa relações de emparelhamento para estabelecer informações de roteamento de confiança e Exchange.
  
**Figura 3: as duas relações de BGP diferentes em uma única conexão ExpressRoute**

![Figura 3: as duas relações de BGP diferentes em uma única conexão ExpressRoute](media/Network-Poster/ERPeering.png)
  
A Figura 3 mostra uma conexão ExpressRoute de uma rede local. A conexão ExpressRoute tem duas relações lógicas de emparelhamento. Uma relação de emparelhamento da Microsoft vai para os serviços Microsoft SaaS, incluindo o Office 365, o Dynamcs 365 e os serviços do Azure PaaS. Uma relação de emparelhamento privado passa para o Azure IaaS e para um gateway de rede virtual que hospeda máquinas virtuais.
  
A relação BGP de emparelhamento da Microsoft: 
  
- É de um roteador em sua DMZ para os endereços públicos do Office 365, do Dynamics 365 e dos serviços do Azure. 
    
- Oferece suporte à comunicação iniciada bidirecional.
    
A relação BGP de emparelhamento privado:
  
- É de um roteador na borda da rede da sua organização para os endereços IP privados atribuídos ao seu VNets do Azure.
    
- Oferece suporte à comunicação iniciada bidirecional.
    
- É uma extensão da rede da sua organização para a nuvem da Microsoft, completa com endereçamento e roteamento consistentes internamente.

>[!Note]
>A relação de BGP de emparelhamento público descrita em versões anteriores deste artigo foi preterida.
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a>Exemplo de implantação de aplicativo e fluxo de tráfego com ExpressRoute

O modo como o tráfego percorre as conexões ExpressRoute e dentro da nuvem da Microsoft é uma função das rotas nos saltos do caminho entre a origem e o comportamento de aplicativo e de destino. Veja a seguir um exemplo de um aplicativo em execução em uma máquina virtual do Azure que acessa um farm do SharePoint local em uma conexão VPN de site a site.
  
**Figura 4: um aplicativo em uma máquina virtual do Azure que acessa um farm local do SharePoint**

![Figura 4: um aplicativo em uma máquina virtual do Azure que acessa um farm local do SharePoint](media/Network-Poster/ER-App-Flow1.png)

  
A Figura 4 mostra um farm do SharePoint local, uma conexão VPN de site a site entre a rede local e uma rede virtual no Azure IaaS, um servidor de aplicativos executando como uma máquina virtual do Azure IaaS e o fluxo de tráfego entre o servidor de aplicativos e farm do SharePoint.
  
O aplicativo localiza o endereço IP do farm do SharePoint usando o DNS local e todo o tráfego passa pela conexão VPN site a site.
  
Esta organização migrou o farm local do SharePoint para o SharePoint Online no Office 365 e implantou uma conexão ExpressRoute.
  
**Figura 5: movendo o farm do SharePoint local para o SharePoint Online**

![Figura 5: movendo o farm do SharePoint local para o SharePoint Online](media/Network-Poster/Hairpin1.png)
  
A Figura 5 mostra a adição de uma conexão ExpressRoute com relações de emparelhamento com o Microsoft SaaS e o Office 365 e para o Azure IaaS contendo o servidor de aplicativos em uma rede virtual. O farm local do SharePoint foi migrado para o Office 365.
  
Com as relações de emparelhamento privado e da Microsoft:
  
- No gateway de rede virtual do Azure, locais no local estão disponíveis na conexão ExpressRoute.
    
- Na assinatura do Office 365, os endereços IP públicos de dispositivos de borda, como servidores proxy, estão disponíveis na conexão ExpressRoute.
    
- Na borda da rede local, os endereços IP privados da VNet do Azure e os endereços IP públicos do Office 365 estão disponíveis na conexão ExpressRoute.
    
Quando o aplicativo acessa as URLs do SharePoint Online, ele encaminha seu tráfego pela conexão ExpressRoute para um servidor proxy na borda. 
  
Quando o servidor proxy localizar o endereço IP do SharePoint Online, ele encaminhará o tráfego de volta pela conexão ExpressRoute. O tráfego de resposta Percorra o caminho reverso.
  
**Figura 6: fluxo de tráfego quando o farm do SharePoint foi migrado para o SharePoint Online no Office 365**

![Figura 6: fluxo de tráfego quando o farm do SharePoint foi migrado para o SharePoint Online no Office 365](media/Network-Poster/Hairpin2.png)

  
A Figura 6 mostra como o tráfego entre o servidor de aplicativos e o SharePoint Online no Office 365 flui sobre a relação de emparelhamento privado do servidor de aplicativos para a borda de rede local e, em seguida, da borda sobre a relação de emparelhamento da Microsoft para o Office 365.
  
O resultado é a fixação de cabelo, uma conseqüência do comportamento de roteamento e aplicativo.
  
## <a name="expressroute-and-microsofts-cloud-network"></a>Rota expressa e rede de nuvem da Microsoft

As conexões ExpressRoute estão disponíveis em duas versões diferentes: ExpressRoute e ExpressRoute Premium.
  
### <a name="expressroute"></a>ExpressRoute

O modo como o tráfego transita entre a rede da sua organização e um datacenter da Microsoft é uma combinação de:
  
- Seus locais.
    
- Locais de emparelhamento de nuvem da Microsoft (os locais físicos para se conectar ao Microsoft Edge).
    
- Locais de datacenter da Microsoft.
    
O Microsoft datacenter e locais de emparelhamento na nuvem estão conectados à rede de nuvem da Microsoft.
  
Ao criar uma conexão ExpressRoute com um local de emparelhamento de nuvem da Microsoft, você está conectado à rede do Microsoft Cloud e a todos os locais de datacenter da Microsoft no mesmo continente. O tráfego entre o local de emparelhamento da nuvem e o datacenter da Microsoft de destino é transportado pela rede da Microsoft em nuvem.
  
Isso pode resultar em uma entrega não ideal para data centers da Microsoft locais para o modelo de conectividade qualquer-para-qualquer.
  
**Figura 7: exemplo de uma organização geograficamente distribuída que usa uma única conexão ExpressRoute**

![Figura 7: exemplo de uma organização geograficamente distribuída que usa uma única conexão ExpressRoute](media/Network-Poster/MSNet1.png)
  
A Figura 7 mostra uma organização com dois locais, local 1 no noroeste dos Estados Unidos e local 2 no nordeste. Eles estão conectados por um provedor de WAN de qualquer um. Essa organização também tem uma conexão ExpressRoute com um local de emparelhamento da Microsoft na costa oeste. O tráfego de local 2 no nordeste destinado a um datacenter de costa leste deve viajar completamente pela WAN da organização para a costa oeste, para o local de emparelhamento da Microsoft e, em seguida, de volta em todo o país da rede de nuvem da Microsoft para a costa leste datacenter.
  
Para a entrega ideal, use várias conexões ExpressRoute para locais regionais de emparelhamento da nuvem da Microsoft. 
  
**Figura 8: o uso de várias conexões ExpressRoute para a entrega ideal para datacenters regionais**

![Figura 8: o uso de várias conexões ExpressRoute para a entrega ideal para datacenters regionais](media/Network-Poster/MSNet2.png)
  
A Figura 8 mostra a mesma organização com duas conexões ExpressRoute, uma para cada local, para locais de emparelhamento da Microsoft locais de região. Nessa configuração, o tráfego do local 2 no nordeste destinado a um datacenter de costa leste vai diretamente para um local de emparelhamento da costa leste, para a rede de nuvem da Microsoft e, em seguida, para o datacenter da costa leste.
  
Várias conexões ExpressRoute podem fornecer:
  
- Melhor desempenho para os locais de datacenters da Microsoft em região local.
    
- Maior disponibilidade para a nuvem da Microsoft quando uma conexão expressa local fica indisponível.
    
Isso funciona bem para organizações no mesmo continente. No enTanto, o tráfego para os data centers da Microsoft fora do continente da organização passa pela Internet.
  
Para o tráfego Intercontinental na rede do Microsoft Cloud, você deve usar conexões Premium do ExpressRoute.
  
### <a name="expressroute-premium"></a>ExpressRoute Premium

Para organizações distribuídas globalmente entre continentes, você pode usar o ExpressRoute Premium. 
  
Com o ExpressRoute Premium, você pode alcançar qualquer Datacenter da Microsoft em qualquer continente de qualquer local de emparelhamento da Microsoft em qualquer continente. O tráfego entre os continentes é transportado pela rede da Microsoft em nuvem.
  
Com várias conexões Premium do ExpressRoute, você pode ter:
  
- Melhor desempenho para data centers da Microsoft localmente.
    
- Maior disponibilidade para a nuvem global da Microsoft quando uma conexão expressa local fica indisponível.
    
O ExpressRoute Premium é necessário para conexões ExpressRoute baseadas no Office 365.
  
**Figura 9: a rede de nuvem da Microsoft em todo o mundo**

![Figura 9: a rede de nuvem da Microsoft em todo o mundo](media/Network-Poster/MSNet3.png)
  
A Figura 9 mostra um diagrama lógico da rede em nuvem da Microsoft em todo o mundo, com redes que abrangem os continentes e regiões do mundo e suas interconexões. Com uma parte da rede de nuvem da Microsoft em cada continente, uma empresa global cria conexões de ExpressRoute Premium a partir de seus escritórios de Hub regionais para locais de emparelhamento da Microsoft locais.
  
Para um escritório regional, o tráfego apropriado do Office 365 para:
  
- Os datacenters do Office 365 são transferidos pela rede de nuvem da Microsoft dentro do continente.
    
- Os datacenters do Office 365 em outro continente trafegam pela rede de nuvem do Intercontinental da Microsoft.
    
Para obter mais informações, consulte:
  
- [Treinamento do Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer/)
    
- [Planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune)
    
## <a name="expressroute-options"></a>Opções do ExpressRoute

Você também pode incorporar as seguintes opções à sua implantação do ExpressRoute:
  
- **Segurança na sua borda:** Para fornecer segurança avançada para o tráfego enviado e recebido pela conexão ExpressRoute, como inspeção de tráfego ou detecção de invasão/malware, coloque seus dispositivos de segurança no caminho de tráfego dentro do DMZ ou na borda da sua intranet.
    
- **Tráfego da Internet para VMs:** Para impedir que as VMs do Azure iniciem o tráfego diretamente com locais da Internet, anuncie a rota padrão à Microsoft. O tráfego para a Internet é roteado pela conexão ExpressRoute e por meio de seus servidores proxy no local. O tráfego de VMs do Azure para os serviços do Azure PaaS ou Office 365 é roteado de volta pela conexão ExpressRoute.
    
- **Otimizadores de WAN:** Você pode implantar otimizadores de WAN em ambos os lados de uma conexão de emparelhamento privado para uma rede virtual do Azure entre locais (VNet). Dentro da VNet do Azure, use um dispositivo de rede de otimizador de WAN do Azure Marketplace e o roteamento definido pelo usuário para encaminhar o tráfego pelo dispositivo.
    
- **Qualidade do serviço:** Use valores de ponto de código de serviços diferenciados (DSCP) no cabeçalho IPv4 do seu tráfego para marcá-lo para voz, vídeo/interativo ou entrega de melhor esforço. Isso é especialmente importante para o relacionamento de emparelhamento da Microsoft e o tráfego do Skype for Business online.
    
ConFira estes recursos adicionais para obter mais informações:
  
- [Rota Expressa para Office 365](https://aka.ms/expressrouteoffice365)
    
- [Treinamento do Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer/)
    
- [ExpressRoute para Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a>Próxima etapa

[Criação de rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a>Confira também

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

