---
title: ExpressRoute para conectividade de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Resumo: Entenda como ExpressRoute pode ajudá-lo com mais rápidas e confiáveis de conexões para os serviços de nuvem da Microsoft e plataformas.'
ms.openlocfilehash: 3ac8d52f50ff6df612de68ea51136fc16d5c9169
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872322"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a>ExpressRoute para conectividade de nuvem da Microsoft

 **Resumo:** Compreenda como ExpressRoute pode ajudá-lo com mais rápidas e confiáveis de conexões para os serviços de nuvem da Microsoft e plataformas.
  
O ExpressRoute oferece uma conexão de rede privada, dedicada e de alta taxa de transferência para a nuvem da Microsoft.
  
## <a name="expressroute-to-the-microsoft-cloud"></a>ExpressRoute para a nuvem da Microsoft

Aqui é o caminho de rede para a nuvem da Microsoft sem uma conexão ExpressRoute.
  
**Figura 1: O caminho de rede sem o ExpressRoute**

![Figura 1: O caminho de rede sem o ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
A Figura 1 mostra o caminho típico entre uma rede local e a nuvem da Microsoft. A borda da rede local conecta-se à Internet por meio de uma WAN link para um provedor. O tráfego viaja pela Internet e o limite da nuvem da Microsoft. Ofertas de nuvem em nuvem da Microsoft incluem o Office 365, Microsoft Azure, Microsoft Intune e Dynamics 365. Os usuários de uma organização podem ser localizados na rede local ou na Internet.
  
Sem uma conexão de ExpressRoute, a única parte do caminho do tráfego para a nuvem da Microsoft que podem controlar (e ter uma relação com o provedor de serviço) é o vínculo entre sua borda da rede local e seu ISP. 
  
O caminho entre seu ISP e a borda de nuvem da Microsoft é um sistema de entrega de melhor esforço na Internet sujeito interrupções, congestionamento de tráfego e monitoramento por usuários mal-intencionados.
  
Os usuários da Internet, como usuários móveis ou remotos, enviam o tráfego para a nuvem da Microsoft pela Internet.
  
Aqui estão os caminhos de redes para a nuvem da Microsoft com uma conexão ExpressRoute.
  
**Figura 2: Os caminhos de rede sem o ExpressRoute**

![Figura 2: Os caminhos de rede sem o ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
A Figura 2 mostra dois caminhos de redes. Tráfego para o Microsoft Intune viaja mesmo caminho de tráfego de Internet normal. Tráfego para o Office 365 e Microsoft Azure Dynamics 365 viaja entre a conexão ExpressRoute, um caminho dedicado entre a borda da rede local e a borda da nuvem da Microsoft.
  
Com uma conexão ExpressRoute, agora você tem um controle, por meio de uma relação com seu provedor de serviços, no caminho de todo tráfego da sua borda para a Microsoft cloud borda. Essa conexão pode oferecer desempenho previsível e um [tempo de atividade 99,95% SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).
  
Agora, você pode contar com previsível taxa de transferência e latência, com base na conexão do seu provedor de serviços, aos serviços do Office 365, Windows Azure e Dynamics 365. Conexões de ExpressRoute com Microsoft Intune não são suportados no momento.
  
Tráfego enviado pela conexão a ExpressRoute não são mais está sujeito a Internet interrupções, congestionamento de tráfego e monitoramento.
  
Os usuários da Internet, como usuários móveis ou remotos, ainda enviam o tráfego para a nuvem da Microsoft pela Internet. Uma exceção é o tráfego para uma linha de intranet do aplicativo de negócios hospedada no Azure IaaS, que são enviados pela conexão a ExpressRoute por meio de uma conexão de acesso remoto à rede local.
  
Mesmo com uma conexão ExpressRoute, alguns tráfego ainda é enviado pela Internet, como as consultas DNS, verificação, lista de certificados revogados e solicitações de rede de fornecimento de conteúdo (CDN).
  
Consulte estes recursos adicionais para obter mais informações:
  
- [ExpressRoute para Office 365](https://aka.ms/expressrouteoffice365)
    
- [ExpressRoute para o Windows Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a>Vantagens da ExpressRoute para o Windows Azure

Aqui estão algumas vantagens de usar ExpressRoute para serviços de nuvem baseada no Windows Azure:
  
- **Desempenho previsível:** Com um caminho dedicado até a borda da nuvem da Microsoft, seu desempenho não está sujeito interrupções do provedor de Internet e picos de tráfego da Internet. Você pode determinar e responsabilizar seus provedores a uma taxa de transferência e latência SLA para a nuvem da Microsoft.
    
- **Privacidade de dados para seu tráfego:** Tráfego enviado pela sua conexão de ExpressRoute dedicado não está sujeito a captura de pacote ou de monitoramento de Internet e análise por usuários mal-intencionados. É mais seguro usando links de WAN com base em Multiprotocol Label alternando MPLS.
    
- **Conexões de alta taxa de transferência:** Com suporte ampla ExpressRoute conexões por provedores do exchange e provedores de serviços de rede, você pode obter até um link Gbps 10 para a nuvem da Microsoft.
    
- **Menor custo para algumas configurações:** Embora ExpressRoute conexões sejam um custo adicional, em alguns casos uma conexão de ExpressRoute único pode custo menor do que aumentando sua capacidade de Internet em vários locais da sua organização para fornecer a taxa de transferência adequada aos serviços de nuvem da Microsoft.
    
Uma conexão ExpressRoute não é uma garantia de um melhor desempenho em cada configuração. É possível ter desempenho inferior sobre uma conexão de ExpressRoute pouca largura de banda que uma conexão de Internet de alta largura de banda é apenas alguns saltos para longe de um datacenter regional da Microsoft.
  
Para obter as recomendações mais recentes para usar ExpressRoute com o Office 365, consulte [ExpressRoute para o Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).
  
## <a name="expressroute-connectivity-models"></a>Modelos de conectividade de ExpressRoute

A tabela 1 mostra os três modelos de conectividade principal para conexões de ExpressRoute.
  
|**Co localizado em uma troca de nuvem**|**Ethernet de ponto a ponto**|**Para qualquer conexão de (VPN IP)**|
|:-----|:-----|:-----|
|![Modelo de conectividade ExpressRoute: Localizado em um Exchange na nuvem](media/Network-Poster/ER-Conn1.png)|![Modelo de conectividade ExpressRoute: Ethernet de ponto a ponto](media/Network-Poster/ER-Conn2.png)|![Modelo de conectividade ExpressRoute: Conexão tipo any-to-any (IP VPN)](media/Network-Poster/ER-Conn3.png)|
|Se seu datacenter co estiver localizado em um recurso com uma troca de nuvem, você pode solicitar uma conexão entre virtual para a nuvem da Microsoft através de intercâmbio de Ethernet do provedor a localização conjunta.  <br/> |Se seu datacenter estiver localizado em seu local, você pode usar um link de Ethernet de ponto a ponto para conectar-se para a nuvem da Microsoft.  <br/> |Se você já estiver usando um provedor de VPN IP (MPLS) para conectar os sites da sua organização, uma conexão ExpressRoute para a nuvem da Microsoft atua como outro local na sua WAN privada.  <br/> |
   
 **Tabela 1: Modelos de conectividade de ExpressRoute**
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a>Relacionamentos de correspondência ExpressRoute aos serviços de nuvem da Microsoft

Uma conexão de ExpressRoute único oferece suporte a até três Border Gateway Protocol (BGP) aos relacionamentos diferentes para diferentes partes de nuvem da Microsoft. BPG usa relações de correspondência para estabelecer a confiança e trocar informações de roteamento.
  
**Figura 3: As três diferentes relações BGP em uma única conexão ExpressRoute**

![Figura 3: As três diferentes relações BGP em uma única conexão ExpressRoute](media/Network-Poster/ERPeering.png)
  
A Figura 3 mostra uma conexão ExpressRoute de uma rede local. A conexão ExpressRoute tem três relacionamentos lógicos de correspondência. Uma relação de correspondência da Microsoft vai para serviços de SaaS Microsoft, incluindo o Office 365 e Dynamcs CRM Online. Uma relação de correspondência pública vai aos serviços do Azure PaaS. Uma relação de correspondência privada vai para o Windows Azure IaaS e um gateway de rede virtual que hospeda máquinas virtuais.
  
O relacionamento BGP aos Microsoft: 
  
- É a partir de um roteador em sua DMZ e os endereços públicos de serviços do Office 365 e Dynamics 365. 
    
- Oferece suporte a comunicação iniciada pelo bidirecional.
    
O relacionamento BGP correspondência público:
  
- É a partir de um roteador em sua DMZ e os endereços IP públicos de serviços do Azure.
    
- Suporta comunicação unidirecional iniciadas dos sistemas locais somente. O relacionamento de correspondência não oferece suporte a comunicação iniciada dos serviços do Azure PaaS.
    
O relacionamento BGP correspondência privado:
  
- É de um roteador na borda da rede da organização para os endereços IP privados atribuídos ao seu VNets do Windows Azure.
    
- Oferece suporte a comunicação iniciada pelo bidirecional.
    
- É uma extensão da rede da organização para a nuvem da Microsoft, completa com endereçamento e roteamento internamente consistente.
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a>Exemplo de fluxo de tráfego e implantação de aplicativo com ExpressRoute

Como o tráfego viaja através de conexões de ExpressRoute e em nuvem da Microsoft é uma função das rotas em de saltos do caminho entre a origem e o comportamento de destino e o aplicativo. Aqui está um exemplo de um aplicativo executado em uma máquina virtual do Azure que acessa um farm do SharePoint no local através de uma conexão de VPN-to-site.
  
**Figure 4: Um aplicativo em uma máquina virtual Azure acessando um farm local do SharePoint**

![Figure 4: Um aplicativo em uma máquina virtual Azure acessando um farm local do SharePoint](media/Network-Poster/ER-App-Flow1.png)

  
Mostra a Figura 4 fluxo de um farm do SharePoint local, uma conexão VPN de site a site entre a rede local e uma rede virtual no Azure IaaS, um servidor de aplicativos executando como uma máquina virtual de Azure IaaS e o tráfego entre o servidor de aplicativos e o farm do SharePoint.
  
O aplicativo localiza o endereço IP do farm do SharePoint usando o DNS local e todo o tráfego vai sobre a conexão de VPN-to-site.
  
Esta organização migrados seu farm do SharePoint no local para o SharePoint Online no Office 365 e implantado uma conexão ExpressRoute.
  
**Figura 5: Movendo o farm local do SharePoint para o SharePoint Online**

![Figura 5: Movendo o farm local do SharePoint para o SharePoint Online](media/Network-Poster/Hairpin1.png)
  
Figura 5 mostra a adição de uma conexão ExpressRoute com relações de correspondência para Microsoft SaaS e o Office 365 e Windows Azure IaaS que contém o servidor de aplicativos em uma rede virtual. O farm do SharePoint local foi migrado para o Office 365.
  
Com as relações de correspondência privadas e da Microsoft:
  
- Do gateway rede virtual do Azure, os locais de local estão disponíveis na conexão ExpressRoute.
    
- De assinatura do Office 365, os endereços IP públicos dispositivos de borda, como servidores proxy, estão disponíveis na conexão ExpressRoute.
    
- Da rede local borda, os endereços IP privados de VNet o Azure e os endereços IP públicos do Office 365 estão disponíveis na conexão ExpressRoute.
    
Quando o aplicativo acessa as URLs do SharePoint Online, ele encaminha seu tráfego entre a conexão ExpressRoute em um servidor de proxy em da borda. 
  
Quando o servidor proxy localiza o endereço IP do SharePoint Online, ele encaminha o tráfego novamente sobre a conexão ExpressRoute. Tráfego de resposta passa o caminho reverso.
  
**Figura 6: Fluxo de tráfego quando o farm do SharePoint foi migrado para o SharePoint Online no Office 365**

![Figura 6: Fluxo de tráfego quando o farm do SharePoint foi migrado para o SharePoint Online no Office 365](media/Network-Poster/Hairpin2.png)

  
A Figura 6 mostra como o tráfego entre o servidor de aplicativo e o SharePoint Online no Office 365 sobre a relação de correspondência particular do servidor de aplicativos até a borda da rede local e, em seguida, da borda ao redor a relação de correspondência da Microsoft para o Office 365.
  
O resultado é uma forma de fixação, uma consequência do comportamento de roteamento e de aplicativos.
  
## <a name="expressroute-and-microsofts-cloud-network"></a>Rede de nuvem da Microsoft e de ExpressRoute

Conexões ExpressRoute estão disponíveis nas duas versões diferentes: ExpressRoute e ExpressRoute Premium.
  
### <a name="expressroute"></a>ExpressRoute

Como o tráfego viaja entre a rede de organização e o Microsoft Data Center é uma combinação de:
  
- Seus locais.
    
- Microsoft aos locais em nuvem (locais físicos para conectar até a borda da Microsoft).
    
- Locais de datacenter da Microsoft.
    
Datacenter da Microsoft e locais de correspondência de nuvem são conectados à rede de nuvem da Microsoft.
  
Quando você cria uma conexão ExpressRoute para um local de correspondência de nuvem do Microsoft, você está conectado à rede de nuvem da Microsoft e todos os locais de datacenter Microsoft no mesmo continente. O tráfego entre o local de correspondência da nuvem e o datacenter da Microsoft de destino é realizado através da rede de nuvem da Microsoft.
  
Isso pode resultar em entrega não ideal em centros de dados Microsoft locais para o modelo de conectividade para qualquer.
  
**Figura 7: Exemplo de uma organização geograficamente distribuídos que usa uma conexão de ExpressRoute único**

![Figura 7: Exemplo de uma organização geograficamente distribuídos que usa uma conexão de ExpressRoute único](media/Network-Poster/MSNet1.png)
  
Figura 7 mostra uma organização com dois locais, 1 do local em que o Noroeste dos Estados Unidos e local 2 nordeste do Estados Unidos. Eles são conectados por um provedor WAN para qualquer. Esta organização também tem uma conexão ExpressRoute para um local de correspondência da Microsoft na Costa Oeste. Tráfego de local 2 da região nordeste destinado a um datacenter Costa Leste deve viagens por toda WAN a organização da Costa Oeste, para o local de correspondência do Microsoft e, em seguida, volta em todo o país através da rede de nuvem da Microsoft para da Costa Leste Datacenter.
  
Para entrega ideal, use várias conexões de ExpressRoute para regionais locais de correspondência nuvem da Microsoft. 
  
**Figura 8: O uso de várias conexões ExpressRoute para entrega ideal para data centers regionais**

![Figura 8: O uso de várias conexões ExpressRoute para entrega ideal para data centers regionais](media/Network-Poster/MSNet2.png)
  
Figura 8 mostra a mesma organização com duas conexões ExpressRoute, um para cada local, para um local regional Microsoft aos locais. Nesta configuração, o tráfego do local 2 da região nordeste destinado a um datacenter Costa Leste passa diretamente para um local de correspondência da Costa Leste, para a rede de nuvem da Microsoft e, em seguida, para o datacenter Costa Leste.
  
Várias conexões de ExpressRoute podem fornecer:
  
- Melhor desempenho para locais de datacenter Microsoft locais regional.
    
- Maior disponibilidade para a nuvem da Microsoft quando uma conexão de ExpressRoute local fica indisponível.
    
Isso funciona bem para organizações do mesmo continente. No entanto, o tráfego para centros de dados do Microsoft fora continente da organização viaja pela Internet.
  
Para tráfego intercontinentais através da rede de nuvem da Microsoft, você deve usar conexões ExpressRoute Premium.
  
### <a name="expressroute-premium"></a>ExpressRoute Premium

Para organizações que sejam distribuídas globalmente em continentes diferentes, você pode usar ExpressRoute Premium. 
  
Com o ExpressRoute Premium, você poderá encontrá-qualquer datacenter da Microsoft em qualquer continente de qualquer local de correspondência da Microsoft em qualquer continente. O tráfego entre continentes é realizado através da rede de nuvem da Microsoft.
  
Com várias conexões de ExpressRoute Premium, você pode ter:
  
- Melhor desempenho em locais continentally centros de dados do Microsoft.
    
- Maior disponibilidade para o Microsoft cloud global quando uma conexão de ExpressRoute local fica indisponível.
    
ExpressRoute Premium é necessário para conexões de ExpressRoute baseadas no Office 365. No entanto, não há nenhum custo adicional para empresas com usuários de 500 ou mais licenciados.
  
**Figura 9: Mundial Microsoft cloud network**

![Figura 9: A rede de nuvem da Microsoft em todo o mundo](media/Network-Poster/MSNet3.png)
  
Figura 9 mostra um diagrama lógico da rede da nuvem Microsoft no mundo todo, com redes que ultrapassam o continentes e regiões do mundo e suas interconexões. Com uma parte da rede de nuvem da Microsoft em cada continente, uma empresa global cria ExpressRoute Premium conexões de seus escritórios regionais hub para local Microsoft aos locais.
  
De um escritório regional, apropriadas tráfego do Office 365 para:
  
- Continental centros de dados do Office 365 são transferidas pela rede Microsoft cloud dentro do continente.
    
- Centros de dados do Office 365 em outro continente viajam através da rede de nuvem Microsoft intercontinentais.
    
Para saber mais, confira:
  
- [Azure ExpressRoute treinamento do Office 365](https://channel9.msdn.com/series/aer/)
    
- [Planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune)
    
- [Gerenciamento de desempenho do Office 365](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a>Opções de ExpressRoute

As opções a seguir também podem ser incorporadas em sua implantação ExpressRoute:
  
- **Segurança na sua borda:** Para fornecer segurança avançada para o tráfego enviado e recebido através de conexão de ExpressRoute, como inspeção do tráfego ou detecção de intrusão/malware, coloque seus aparelhos de segurança no caminho do tráfego em sua DMZ ou na borda de sua intranet.
    
    Tráfego da Internet para máquinas virtuais para impedir que o Azure VMs iniciando tráfego diretamente com locais da Internet, anunciar a rota padrão para a Microsoft. O tráfego para a Internet será roteado entre a conexão ExpressRoute e através de seus servidores de proxy local. Tráfego de máquinas virtuais do Windows Azure para serviços do Azure PaaS ou do Office 365 é encaminhado volta entre a conexão ExpressRoute.
    
- **Otimizadores WAN:** Você pode implantar otimizadores WAN em ambos os lados de uma conexão privada de correspondência para um Azure locais cruzados rede virtual (VNet). Dentro do Azure VNet, use um aparelho de rede WAN otimizador do Azure marketplace e definida pelo usuário de roteamento para rotear o tráfego através do aparelho.
    
- **Qualidade de serviço:** Use valores de ponto de código de serviços diferenciados (DSCP) no cabeçalho IPv4 do tráfego para marcá-la para voz, vídeo/interativa ou entrega de melhor esforço. Isso é especialmente importante para a relação de correspondência da Microsoft e Skype para tráfego Business Online.
    
Consulte estes recursos adicionais para obter mais informações:
  
- [ExpressRoute para Office 365](https://aka.ms/expressrouteoffice365)
    
- [Azure ExpressRoute treinamento do Office 365](https://channel9.msdn.com/series/aer/)
    
- [ExpressRoute para o Windows Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a>Próxima etapa

[Criação de rede para o Microsoft SaaS](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a>Confira também

[Rede do Microsoft Cloud para Arquitetos Corporativos](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

