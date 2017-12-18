---
title: Microsoft Azure arquiteturas do SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: "Resumo: Soluções do SharePoint 2013 podem ser hospedadas em máquinas virtuais do Microsoft Azure. Saiba quais tipos de soluções são adequados e como configurar o Microsoft Azure para hospedar um."
ms.openlocfilehash: ee157ef81101cd51090fff50c972edd37562a179
ms.sourcegitcommit: 4a347cfb16405d5213b28f332d80e244fca0fb8f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2017
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>Microsoft Azure arquiteturas do SharePoint 2013

 **Resumo:** Soluções do SharePoint 2013 podem ser hospedadas em máquinas virtuais do Microsoft Azure. Saiba quais tipos de soluções são adequados e como configurar o Microsoft Azure para hospedar um.
  
Windows Azure é um bom ambiente para hospedar uma solução do SharePoint Server 2013. Na maioria dos casos, é recomendável que o Office 365, mas um farm do SharePoint Server hospedado no Windows Azure pode ser uma boa opção para soluções específicas. Este artigo descreve como projetar soluções de modo que eles fiquem uma boa cabem na plataforma Windows Azure do SharePoint. As duas soluções específicas a seguintes são usadas como exemplos:
  
- [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Sites da Internet no Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Soluções recomendadas do SharePoint para serviços de infraestrutura do Windows Azure

Serviços de infraestrutura do Windows Azure é uma opção atraente para a hospedagem de soluções do SharePoint. Algumas soluções são a melhor opção para essa plataforma que outros. A tabela a seguir mostra as soluções recomendadas.
  
|**Solução**|**Por que essa solução é recomendada para o Windows Azure**|
|:-----|:-----|
|Ambientes de desenvolvimento e teste  <br/> |É fácil criar e gerenciar esses ambientes.  <br/> |
|Recuperação de desastres do farms do SharePoint local no Azure  <br/> |**Hospedado de datacenter secundário** Use o Windows Azure em vez de investimento em um datacenter secundário em uma região diferente. <br/> **Ambientes de recuperação de desastre de menor custo** Manter e se pague menos recursos que um ambiente de recuperação de desastres no local. O número de recursos depende do ambiente de recuperação de desastres que você escolher: espera a frio, espera passiva ou espera ativa.<br/> **Plataforma mais elástica** Em caso de desastre, facilmente dimensionamento seu farm do SharePoint de recuperação para atender a requisitos de carga. Dimensione em quando não precisar mais os recursos.<br/> Consulte o [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).  <br/> |
|Sites na Internet que usam os recursos e a escala não está disponível no Office 365  <br/> |**Concentre seus esforços** Concentre-se no criando um grande site, em vez da criação de infra-estrutura. <br/> **Beneficie-se de elasticidade no Windows Azure** Dimensionar o farm para a demanda adicionando novos servidores e se pague apenas para os recursos que necessários. A alocação dinâmica de máquina não é suportado (AutoEscala).<br/> **Usar o Azure Active Directory (AD)** Beneficie-se do Azure AD para contas de cliente. <br/> **Adicionar funcionalidade do SharePoint não está disponível no Office 365** Adicione profundidade a emissão de relatórios e do web analytics. <br/> Consulte os [Sites da Internet no Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).  <br/> |
|Farms de aplicativo para oferecer suporte a ambientes do Office 365 ou no local  <br/> |**Compilação, teste e hospedar aplicativos** no Windows Azure para oferecer suporte tanto no local e ambientes em nuvem. <br/> **Host Essa função** no Windows Azure em vez de comprar novo hardware para ambientes locais. <br/> |
   
Para intranet e soluções de colaboração e cargas de trabalho, considere as seguintes opções:
  
- Determine se o Office 365 atende aos seus requisitos de negócios ou pode ser a parte da solução. O Office 365 fornece um conjunto de recursos avançados que sempre está atualizado.
    
- Se o Office 365 não atender a todas as suas necessidades de negócios, considere uma implementação padrão do SharePoint 2013 no local de serviços de consultoria Microsoft (MCS). Uma arquitetura padrão pode ser uma solução mais barata, mais rápida e mais fácil para você ofereça suporte a que uma personalizada. 
    
- Se uma implementação padrão não atender às suas necessidades de negócios, considere uma solução personalizada no local.
    
- Se usar uma plataforma de nuvem é importante para seus requisitos de negócios, considere uma implementação padrão ou personalizada do SharePoint 2013 hospedados nos serviços de infraestrutura do Windows Azure. Soluções do SharePoint são muito mais fácil suportar no Azure que outras plataformas de nuvem pública do Microsoft não nativo.
    
## <a name="before-you-design-the-azure-environment"></a>Antes de criar o ambiente do Azure

Embora este artigo usa as topologias do SharePoint de exemplo, você pode usar esses conceitos de design com qualquer topologia de farm do SharePoint. Antes de projetar o ambiente do Azure, use a seguinte orientação de topologia, arquitetura, capacidade e desempenho para projetar o farm do SharePoint:
  
- [Design de arquitetura para profissionais de TI do SharePoint 2013](http://technet.microsoft.com/en-us/sharepoint/fp123594.aspx)
    
- [Planejar para desempenho e capacidade de gerenciamento no SharePoint Server 2013](http://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a>Determinar o tipo de domínio do Active Directory

Cada farm do SharePoint Server depende do Active Directory para fornecer contas administrativas para a instalação de farm. Neste momento, há duas opções para soluções do SharePoint no Windows Azure. Eles são descritos na tabela a seguir.
  
|**Opção**|**Descrição**|
|:-----|:-----|
|Domínio dedicado  <br/> |Você pode implantar um domínio do Active Directory dedicado e isolado no Azure para dar suporte ao seu farm do SharePoint. Esta é uma boa opção para sites da Internet público.  <br/> |
|Estender o domínio local por meio de uma conexão entre locais  <br/> |Quando você estende o domínio local por meio de uma conexão entre locais, os usuários acessar o farm do SharePoint por meio de sua intranet como se estivesse hospedado no local. Você pode tirar proveito da sua implementação do local do Active Directory e DNS.  <br/> Uma conexão entre locais é necessária para a criação de um ambiente de recuperação de desastres no Azure fazer failover para do farm local.  <br/> |
   
Este artigo inclui os conceitos de design para estender o domínio local por meio de uma conexão entre locais. Se sua solução usa um domínio dedicado, você não precisa uma conexão entre locais.
  
## <a name="design-the-virtual-network"></a>Projetar a rede virtual

Primeiro você precisa de uma rede virtual no Windows Azure, que inclui as sub-redes no qual você colocará suas máquinas virtuais. A rede virtual precisa de um espaço de endereço IP particular, que partes da qual você atribui as sub-redes.
  
Se você estiver estendendo sua rede local no Azure por meio de uma conexão entre locais (necessário para um ambiente de recuperação de desastre), você deve escolher um espaço de endereço privado que não ainda esteja em uso em outro local na rede da organização, que pode incluir seu ambiente local e outras redes virtuais do Azure. 
  
**Figura 1: Ambiente de local com uma rede virtual no Windows Azure**

![Design de uma rede virtual do Microsoft Azure para uma solução do SharePoint. Uma sub-rede para o gateway Azure. Uma sub-rede para as máquinas virtuais.](images/OPrrasconWA_AZarch.png)
  
Neste diagrama:
  
- Uma rede virtual no Windows Azure é ilustrada lado a lado no ambiente local. Dois ambientes ainda não estão conectados por uma conexão entre locais, que pode ser uma conexão VPN de site para sites ou ExpressRoute.
    
- Neste ponto, a rede virtual inclui apenas as sub-redes e não há outros elementos de arquitetura. Uma sub-rede hospedará o Azure gateway e outras sub-redes hospedam as camadas do farm do SharePoint, com uma adicional para o Active Directory e DNS.
    
## <a name="add-cross-premises-connectivity"></a>Adicionar a conectividade entre locais

A próxima etapa de implantação é criar a conexão entre locais (se isso se aplica à sua solução). Para conexões entre locais, um gateway Azure reside em uma sub-rede de gateway separado, que você deve criar e atribuir um espaço de endereçamento. 
  
Quando você planeja uma conexão entre locais, você pode definir e cria um gateway Azure e conexão para um dispositivo de gateway local.
  
**Figura 2: Usando um gateway Azure e um dispositivo de gateway local para fornecer conectividade to-site entre o ambiente local e o Windows Azure**

![Ambiente local conectado a uma rede virtual do Azure por uma conexão entre locais, que pode ser uma conexão VPN site a site ou um ExpressRoute](images/AZarch_VPNgtwyconnct.png)
  
Neste diagrama:
  
- Adicionando ao diagrama anterior, o ambiente local está conectado à rede virtual Azure por uma conexão entre local, que pode ser uma conexão VPN de site para sites ou ExpressRoute.
    
- Um gateway Azure estiver em uma sub-rede de gateway.
    
- O ambiente local inclui um dispositivo de gateway, como um roteador ou servidor VPN.
    
Para obter informações adicionais planejar e criar uma rede virtual entre locais, consulte [Connect uma local da rede para uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-windows-server-active-directory-ad-and-dns"></a>Adicionar o Windows Server Active Directory (AD) e DNS

Recuperação de desastres no Azure, você implanta o Windows Server AD e DNS em um cenário híbrido onde o Windows Server AD é implantado tanto no local e nas máquinas virtuais do Azure.
  
**Figura 3: Configuração do domínio do Active Directory de híbrido**

![As duas máquinas virtuais implantadas na rede virtual do Azure e na sub-rede do Farm do SharePoint são réplicas de controladores de domínios e de servidores DNS](images/AZarch_HyADdomainConfig.png)
  
Este diagrama se baseia nos diagramas anteriores, adicionando duas máquinas virtuais para um servidor AD do Windows e a sub-rede do DNS. Essas máquinas virtuais são os servidores DNS e controladores de domínio de réplica. Eles são uma extensão do ambiente do Windows Server AD local. 
  
A tabela a seguir fornece recomendações de configuração para essas máquinas virtuais no Windows Azure. Usá-las como um ponto de partida para projetar seu próprio ambiente — mesmo para um domínio dedicado onde o seu ambiente do Azure não se comunicar com seu ambiente local.
  
|**Item**|**Configuração**|
|:-----|:-----|
|Tamanho da máquina virtual no Windows Azure  <br/> |Tamanho a1 ou A2 na camada Standard  <br/> |
|Sistema operacional  <br/> |Windows Server 2012 R2  <br/> |
|Função do Active Directory  <br/> |Controlador de domínio de DS AD designado como um servidor de catálogo global. Essa configuração reduz o tráfego de saída entre a conexão entre locais.  <br/> Em um ambiente de vários domínios com altas taxas de alteração (isso não é comum), configure os controladores de domínio no local não para sincronizar com os servidores de catálogo global no Windows Azure, para reduzir o tráfego de replicação.  <br/> |
|Função DNS  <br/> |Instalar e configurar o serviço de servidor DNS nos controladores de domínio.  <br/> |
|Discos de dados  <br/> |Coloque o banco de dados do Active Directory, logs e SYSVOL em discos do Azure de dados adicionais. Não coloque essas do disco de sistema operacional ou os discos temporários fornecidos pelo Windows Azure.  <br/> |
|Endereços IP  <br/> |Usar endereços IP estáticos e configurar a rede virtual para atribuir esses endereços para as máquinas virtuais na rede virtual depois que os controladores de domínio foram configurados.  <br/> |
   
> [!IMPORTANT]
> Antes de implantar o Active Directory no Windows Azure, leia [as diretrizes para implantar o Windows Server Active Directory nas máquinas virtuais do Windows Azure](https://go.microsoft.com/fwlink/p/?linkid=392681). Esses ajuda a determinar se uma arquitetura diferente ou definições de configuração diferentes são necessários para sua solução. 
  
## <a name="add-the-sharepoint-farm"></a>Adicionar o farm do SharePoint

Coloca as máquinas virtuais do farm do SharePoint em níveis em que as sub-redes apropriadas.
  
**Figura 4: Posicionamento de máquinas virtuais do SharePoint**

![Os servidores de banco de dados e as funções de servidor do SharePoint adicionados à rede virtual do Azure na sub-rede do Farm do SharePoint](images/AZarch_SPVMsinCloudSer.png)
  
Este diagrama se baseia nos diagramas anteriores, adicionando as funções de servidor de farm do SharePoint em seus respectivas camadas.
  
- Duas máquinas virtuais do banco de dados executando o SQL Server criar a camada de banco de dados.
    
- Duas máquinas virtuais executando o SharePoint Server 2013 para cada um dos seguintes camadas: servidores front-end, servidores de cache distribuído e servidores back-end.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Projetar e funções de servidor para conjuntos de disponibilidade e domínios de falha de sintonia fina

Um domínio de falha é um agrupamento de hardware nas quais instâncias de função executar. Máquinas virtuais dentro do mesmo domínio de falha podem ser atualizadas pela infraestrutura do Windows Azure ao mesmo tempo. Ou então, eles podem falhar ao mesmo tempo, porque eles compartilham o mesmo rack. Para evitar o risco de ter duas máquinas virtuais no mesmo domínio da falha, você pode configurar suas máquinas virtuais como um conjunto de disponibilidade, o que garante que cada máquina virtual está em um domínio de falha de diferentes. Se três máquinas virtuais forem configuradas como um conjunto de disponibilidade, Azure garante que não mais de dois das máquinas virtuais estão localizados no mesmo domínio de falha.
  
Ao criar a arquitetura do Windows Azure para um farm do SharePoint, configure funções de servidor idênticos para fazer parte de um conjunto de disponibilidade. Isso garante que suas máquinas virtuais estão espalhadas por vários domínios de falha.
  
**Figura 5: Usar conjuntos de disponibilidade do Azure para fornecer alta disponibilidade para as camadas de farm do SharePoint**

![Configuração de conjuntos de disponibilidade na infraestrutura do Azure para uma solução do SharePoint 2013](images/AZenv_WinAzureAvailSetsHA.png)
  
Este diagrama chama a configuração dos conjuntos de disponibilidade na infraestrutura do Windows Azure. Cada uma das seguintes funções compartilham um conjunto de disponibilidade separados:
  
- DNS e active Directory
    
- Banco de dados
    
- Back-end
    
- Distribuir o cache
    
- Front-end
    
O farm do SharePoint talvez precise ser tudo bem ajustado na plataforma Windows Azure. Para garantir a alta disponibilidade de todos os componentes, certifique-se de que o servidor funções são todos configuradas de forma idêntica.
  
Aqui está um exemplo que mostra uma arquitetura de Sites da Internet padrão que atenda aos objetivos de desempenho e capacidade de específica. Este exemplo é destaque no modelo de arquitetura do seguinte: [Arquiteturas de pesquisa de Sites de Internet do SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Figura 6: Exemplo de planejamento para metas de desempenho e capacidade em um farm de três camadas**

![Arquitetura de Sites da Internet padrão do SharePoint 2013 com as alocações de componentes que atendem aos objetivos específicos de capacidade e de desempenho](images/AZarch_CapPerfexmpArch.png)
  
Neste diagrama:
  
- Um farm de três camadas é representada: servidores web, servidores de aplicativos e servidores de banco de dados.
    
- Os servidores de três web são configurados de forma idêntica com vários componentes.
    
- Os servidores de banco de dados de dois são configurados de forma idêntica.
    
- Os servidores de três aplicativos não são configurados de forma idêntica. Essas funções de servidor requerem o ajuste fino para disponibilidade define no Windows Azure.
    
Vamos analisar mais detalhadamente a camada do servidor de aplicativo.
  
**Figura 7: Camada do servidor de aplicativos antes de ajuste fino**

![Camada de servidor de aplicativos do SharePoint Server 2013 de exemplo antes do ajuste para os conjuntos de disponibilidade do Microsoft Azure](images/AZarch_AppServtierBefore.png)
  
Neste diagrama:
  
- Três servidores estão incluídas na camada de aplicativos.
    
- O primeiro servidor inclui quatro componentes.
    
- O segundo servidor inclui três componentes.
    
- O terceiro servidor inclui dois componentes.
    
Você pode determinar o número de componentes pelas metas de desempenho e capacidade para o farm. Para adaptar-se essa arquitetura para o Windows Azure, podemos vai replicar quatro componentes em todos os três servidores. Isso aumenta o número de componentes além do que é necessário para desempenho e capacidade. A desvantagem é que esse design garante a alta disponibilidade de todos os quatro componentes na plataforma Windows Azure quando essas três máquinas virtuais são atribuídas a um conjunto de disponibilidade.
  
**Figura 8: Camada do servidor de aplicativo depois de ajuste fino**

![Camada de servidor de aplicativos do SharePoint Server 2013 de exemplo após o ajuste para os conjuntos de disponibilidade do Microsoft Azure](images/AZarch_AppServtierAfter.png)
  
Este diagrama mostra todos os servidores de aplicativos três configurados de forma idêntica com os mesmos quatro componentes.
  
Quando adicionamos conjuntos de disponibilidade para as camadas do farm do SharePoint, a implementação for concluída.
  
**Figura 9: Concluído farm do SharePoint nos serviços de infraestrutura do Windows Azure**

![Farm do SharePoint 2013 de exemplo nos serviços de infraestrutura do Azure com rede virtual, conectividade entre locais, sub-redes, VMs e conjuntos de disponibilidade](images/7256292f-bf11-485b-8917-41ba206153ee.png)
  
Este diagrama mostra o farm do SharePoint implementado no serviços de infraestrutura do Windows Azure, com conjuntos de disponibilidade para fornecer os domínios com falha para os servidores em cada camada.
  
**Participe da discussão**

|**Entre em contato conosco**|**Descrição**|
|:-----|:-----|
|**Qual conteúdo de adoção de nuvem faça você precisa?** <br/> |Estamos criando conteúdo para a adoção de nuvem que abrange várias plataformas de nuvem da Microsoft e serviços. Fale conosco pensar em nosso conteúdo de adoção de nuvem ou pedir enviando e-mails para [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)conteúdo específico.<br/> |
|**Participe da discussão de adoção de nuvem** <br/> |Se você estiver entusiasmados pela sobre soluções baseadas em nuvem, considere ingressando a nuvem adoção consultoria placa (CAAB) para se conectar com uma comunidade amplos, vibrante de desenvolvedores de conteúdo Microsoft, profissionais do setor e clientes de todo o mundo. Para ingressar, adicione si mesmo como um membro do [espaço CAAB (placa de consultoria da adoção nuvem)](https://aka.ms/caab) da Microsoft Tech comunidade e envie-em um email rápido em[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Qualquer pessoa pode ler o conteúdo relacionado à comunidade no [blog CAAB](https://blogs.technet.com/b/solutions_advisory_board/). No entanto, os membros CAAB obtém convites para seminários na Web privados que descrevem os novos recursos de adoção de nuvem e soluções.<br/> |
|**Obtenha a arte que aparece aqui** <br/> |Se você quiser uma cópia editável da arte que você vê neste artigo, voltaremos felizes em enviá-lo. Envie sua solicitação, incluindo a URL e o título da arte, como [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).<br/> |
   
## <a name="see-also"></a>See Also

[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Sites da Internet no Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


