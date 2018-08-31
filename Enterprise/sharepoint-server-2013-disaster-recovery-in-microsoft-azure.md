---
title: Recuperação de Desastre do SharePoint Server 2013 no Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 'Resumo: Usando o Windows Azure, você pode criar um ambiente de recuperação de desastres para seu farm do SharePoint local. Este artigo descreve como projetar e implementar esta solução.'
ms.openlocfilehash: 56d9fa039bfe533afbc5ac7c1e060d43c0801aef
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915796"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Recuperação de Desastre do SharePoint Server 2013 no Microsoft Azure

 **Resumo:** Usando o Windows Azure, você pode criar um ambiente de recuperação de desastres para seu farm do SharePoint local. Este artigo descreve como projetar e implementar esta solução.

 **Assista o vídeo de visão geral de recuperação de desastres do SharePoint Server 2013**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 Quando acidente seu ambiente do SharePoint local, sua prioridade mais alta é obter o sistema executando novamente rapidamente. Recuperação de desastres com o SharePoint é mais rápido e fácil quando você tiver um ambiente de backup já em execução no Microsoft Azure. Este vídeo explica os principais conceitos de um ambiente do SharePoint passiva de failover e complementa os detalhes completos disponíveis neste artigo.
  
Use este artigo com o seguinte modelo de solução: **SharePoint Disaster Recovery in Microsoft Azure**.
  
[![Processo de recuperação de desastre do SharePoint para o Azure](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
Neste artigo:
  
- [Usar os serviços de infraestrutura do Windows Azure para recuperação de desastres](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#AZ)
    
- [Descrição da solução](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#SOL)
    
- [Arquitetura detalhada](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#arch)
    
- [Mapa de recuperação de desastres](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#RDmap)
    
- [Fase 1: Criar o ambiente de recuperação de desastres](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase1)
    
- [Fase 2: Criar a rede virtual do Azure e uma conexão VPN](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase2)
    
- [Fase 3: Implantar o Active Directory e serviços de nome de domínio à rede virtual do Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase3)
    
- [Fase 4: Implantar o farm de recuperação do SharePoint no Windows Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase4)
    
- [Fase 5: Configurar DFSR entre os farms](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase5)
    
- [Fase 6: Configurar o envio de logs para o farm de recuperação](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase6)
    
- [Fase 7: Validar o failover e recuperação](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Phase7)
    
- [Ambiente de prova de conceito da Microsoft](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#POC)
    
- [Dicas de solução de problemas](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md#Troubleshooting)
    
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Usar os serviços de infraestrutura do Windows Azure para recuperação de desastres

Muitas organizações não têm um ambiente de recuperação de desastres para o SharePoint, que pode ser caro construir e manter o local. Serviços do Azure infraestrutura oferece opções de atraentes para desastres ambientes de recuperação que são mais flexível e mais barata que as alternativas de local.
  
As vantagens do uso de serviços de infraestrutura do Windows Azure incluem:
  
- **Menos dispendiosos recursos** Manter e se pague menos recursos que ambientes de recuperação de desastres no local. O número de recursos depende de qual ambiente de recuperação de desastre, você escolher: espera a frio, espera passiva ou espera ativa.
    
- **Melhor flexibilidade de recursos** Em caso de desastre, facilmente dimensionar seu farm do SharePoint de recuperação para atender aos requisitos de carga. Dimensione em quando não precisar mais os recursos.
    
- **Compromisso de datacenter inferior** Use os serviços de infraestrutura do Windows Azure em vez de investimento em um datacenter secundário em uma região diferente.
    
Há menos complexas opções para as organizações apenas introdução com recuperação de desastres e opções avançadas para organizações com requisitos de resiliência de alta. As definições para ambientes de espera a frio, passiva e hot são um pouco diferentes quando o ambiente está hospedado em uma plataforma de nuvem. A tabela a seguir descreve esses ambientes de criação de um farm de recuperação do SharePoint no Windows Azure.
  
**Tabela: Ambientes de recuperação**

|**Tipo de ambiente de recuperação**|**Descrição**|
|:-----|:-----|
|Hot  <br/> |Um farm totalmente dimensionado é provisionado, atualizadas e está sendo executado no modo de espera.  <br/> |
|Passiva  <br/> |O farm é criado e máquinas virtuais estão em execução e atualizados.  <br/> Recuperação inclui anexar bancos de dados de conteúdo, aplicativos de serviço de provisionamento e rastreamento de conteúdo.  <br/> O farm pode ser uma versão menor do que o farm de produção e, em seguida, reduzidas para servir completos do usuário base.  <br/> |
|Frio  <br/> |O farm totalmente é criado, mas as máquinas virtuais são interrompidas.  <br/> Manter o ambiente inclui iniciar as máquinas virtuais do tempo, aplicando o patch, atualizando e verificando o ambiente.  <br/> Inicie o ambiente completo em caso de desastre.  <br/> |
   
É importante avaliar os objetivos de tempo de recuperação (Recovery Time Objectives) e objetivos de ponto de recuperação (RPOs) da sua organização. Esses requisitos determinam qual ambiente é o investimento mais apropriado para sua organização.
  
As diretrizes deste artigo descrevem como implementar um ambiente em espera passiva. Você também pode adaptá-lo em um ambiente em espera a frio, embora precisam ser seguidas procedimentos adicionais para dar suporte a esse tipo de ambiente. Este artigo não descreve como implementar um ambiente em espera ativa.
  
Para obter mais informações sobre as soluções de recuperação de desastres, consulte [alta disponibilidade e conceitos de recuperação de desastres no SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) e [Escolha uma estratégia de recuperação de desastres para o SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).
  
## <a name="solution-description"></a>Descrição da solução

A solução de recuperação de desastre em espera passiva requer o seguinte ambiente:
  
- Um farm de produção do SharePoint local
    
- Um farm do SharePoint de recuperação no Windows Azure
    
- Uma conexão VPN de site a site entre os dois ambientes
    
A figura a seguir ilustra esses três elementos.
  
**Figura: Elementos de uma solução em espera passiva no Azure**

![Elementos de uma solução de espera ativa do SharePoint no Azure](media/AZarch-AZWarmStndby.png)
  
Envio com distribuído arquivo sistema replicação (DFSR) de log do SQL Server é usado para copiar backups de banco de dados e logs de transação para o farm de recuperação no Windows Azure: 
  
- DFSR transfere logs do ambiente de produção para o ambiente de recuperação. Em um cenário WAN, DFSR é mais eficiente do que os logs diretamente para o servidor secundário de envio no Windows Azure.
    
- Logs são reproduzidos ao SQL Server no ambiente de recuperação no Windows Azure.
    
- Não anexar enviados com logs SharePoint conteúdo bancos de dados no ambiente de recuperação até que um exercício de recuperação é executado.
    
Execute as seguintes etapas para recuperar o farm:
  
1. Pare o envio de log.
    
2. Pare de aceitar o tráfego para o farm principal.
    
3. Repetição durante os logs de transações final.
    
4. Anexe os bancos de dados de conteúdo ao farm.
    
5. Restaure aplicativos de serviço dos bancos de dados replicados.
    
6. Atualize registros de sistema de nome de domínio (DNS) para apontar para o farm de recuperação.
    
7. Inicie um rastreamento completo.
    
Recomendamos que você poderá testar essas etapas regularmente e documentá-los para ajudar a garantir que sua recuperação live seja executado sem problemas. Anexar bancos de dados de conteúdo e aplicativos de serviço de restauração podem levar algum tempo e geralmente envolvem algumas configuração manual.
  
Após uma recuperação é executada, essa solução oferece os itens listados na tabela a seguir.
  
**Tabela: Objetivos de recuperação de solução**

|**Item**|**Descrição**|
|:-----|:-----|
|Sites e conteúdo  <br/> |Sites e conteúdo estão disponíveis no ambiente de recuperação.  <br/> |
|Uma nova instância de pesquisa  <br/> |Nesta solução em espera passiva, a pesquisa não é restaurada dos bancos de dados de pesquisa. Componentes de pesquisa do farm de recuperação são configurados como da mesma forma como possíveis para o farm de produção. Depois que os sites e conteúdo são restaurados, um rastreamento completo é iniciado para reconstruir o índice de pesquisa. Você não precisará aguardar o rastreamento a ser concluídas para disponibilizar os sites e conteúdo.  <br/> |
|Serviços  <br/> | Os serviços que armazenam dados em bancos de dados são restaurados dos bancos de dados enviados com logs. Serviços que não armazene dados nos bancos de dados simplesmente foram iniciados. <br/>  Nem todos os serviços com bancos de dados precisam ser restaurado. Os seguintes serviços não precisam ser restaurado a partir de bancos de dados e simplesmente podem ser iniciados após o failover: <br/>  Coleta de Dados de Uso e Integridade <br/>  Serviço de Controle de Sessão <br/>  Automação do Word <br/>  Qualquer outro serviço que não usa um banco de dados <br/> |
   
Você pode trabalhar com os serviços de consultoria Microsoft (MCS) ou um parceiro para atender aos objetivos de recuperação mais complexa. Estas são resumidas na tabela a seguir.
  
**Tabela: Outros itens que podem ser abordados pelo MCS ou um parceiro**

|**Item**|**Descrição**|
|:-----|:-----|
|Sincronizando soluções personalizadas do farm  <br/> |Idealmente, a configuração do farm de recuperação é idêntica ao farm de produção. Você pode trabalhar com um consultor ou parceiro para avaliar se soluções personalizadas do farm são replicadas e se o processo está em vigor para manter dois ambientes sincronizados.  <br/> |
|Conexões com fontes de dados no local  <br/> |Talvez não seja prático replicar conexões para sistemas de dados back-end, conexões (BDC) do controlador de domínio de backup e fontes de conteúdo de pesquisa.  <br/> |
|Cenários de restauração de pesquisa  <br/> |Porque as implantações do enterprise search tendem a ser bastante exclusivo e complexas, a restauração de pesquisa dos bancos de dados exige um investimento maior. Você pode trabalhar com um consultor ou parceiro para identificar e implementar cenários de restauração de pesquisa que sua organização pode exigir.  <br/> |
   
As diretrizes fornecidas neste artigo pressupõe que o farm local já foi desenvolvido e implantado.
  
## <a name="detailed-architecture"></a>Arquitetura detalhada

Idealmente, a configuração do farm de recuperação no Windows Azure é idêntica de produção farm local, incluindo o seguinte:
  
- A mesma representação das funções de servidor
    
- A mesma configuração de personalizações
    
- A mesma configuração de componentes de pesquisa
    
O ambiente no Azure pode ser uma versão menor do que o farm de produção. Se você planeja dimensionar o farm de recuperação após o failover, é importante que cada tipo de função de servidor inicialmente ser representado.
  
Algumas configurações talvez não seja práticas replicar no ambiente de failover. Certifique-se de testar os procedimentos de failover e o ambiente para ajudar a garantir que o farm de failover oferece o nível de serviço esperado.
  
Essa solução não estabelece uma topologia específica para um farm do SharePoint. O foco desta solução é usar o Windows Azure para o farm de failover e implementar o envio de logs e DFSR entre os dois ambientes.
  
### <a name="warm-standby-environments"></a>Ambientes de espera passiva

Em um ambiente em espera passiva, todas as máquinas virtuais no ambiente do Azure estão em execução. O ambiente estiver pronto para um evento ou exercício de failover.
  
A figura a seguir ilustra uma solução de recuperação de desastre de um farm do SharePoint local a um farm do SharePoint com base no Windows Azure que esteja configurado como um ambiente em espera passiva.
  
**Figura: Topologia e principais elementos de um farm de produção e um farm de recuperação de espera passiva**

![Topologia de um farm do SharePoint e um farm de recuperação de espera passiva](media/AZarch-AZWarmStndby.png)
  
Neste diagrama:
  
- Dois ambientes são mostrados lado a lado: o farm do SharePoint no local e o farm de espera passiva no Azure.
    
- Cada ambiente inclui um compartilhamento de arquivos.
    
- Cada farm inclui quatro camadas. Para atingir a alta disponibilidade, cada camada inclui dois servidores ou máquinas virtuais que são configuradas de forma idêntica para uma função específica, como serviços de front-end, cache distribuído, serviços back-end e bancos de dados. Não é importante nessa ilustração chamar componentes específicos. Os dois farms são configurados de forma idêntica.
    
- A camada de quarta é a camada de banco de dados. Envio de logs é usado para copiar os logs do servidor de banco de dados secundário no ambiente local para o compartilhamento de arquivos no mesmo ambiente.
    
- A DFSR copia os arquivos do compartilhamento de arquivos no ambiente local para o compartilhamento de arquivos no ambiente Azure.
    
- O envio de logs reproduz os logs do compartilhamento de arquivos no ambiente Azure para a réplica primária no grupo de disponibilidade AlwaysOn do SQL Server no ambiente secundário.
    
### <a name="cold-standby-environments"></a>Ambientes de espera a frio

Em um ambiente em espera a frio, a maioria das máquinas virtuais do SharePoint farm pode ser desligada. (É recomendável ocasionalmente Iniciando as máquinas virtuais, como a cada duas semanas ou uma vez por mês, para que cada máquina virtual pode ser sincronizado com o domínio.) As seguintes máquinas virtuais no ambiente de recuperação Azure devem permanecer em execução para ajudar a garantir operações contínuas de envio de logs e DFSR:
  
- O compartilhamento de arquivo
    
- Servidor de banco de dados principal
    
- Pelo menos uma máquina virtual que executa o Windows Server Active Directory Domain Services e DNS
    
A figura a seguir mostra um ambiente de failover do Windows Azure no qual a máquina virtual do compartilhamento de arquivo e a máquina de virtual de banco de dados principal do SharePoint estão em execução. Todas as outras máquinas de virtuais do SharePoint são interrompidas. A máquina virtual que está executando o Windows Server Active Directory e DNS não será mostrada.
  
**Figura: Farm de recuperação de espera a frio com máquinas virtuais em execução**

![Elementos de uma solução de espera inativa do SharePoint no Azure](media/AZarch-AZColdStndby.png)
  
Após o failover para um ambiente em espera a frio, todas as máquinas virtuais são iniciadas e o método para alcançar a alta disponibilidade dos servidores de banco de dados deve ser configurado, como grupos de disponibilidade AlwaysOn do SQL Server.
  
Se vários grupos de armazenamento são implementados (bancos de dados estão espalhados por mais de um conjunto de alta disponibilidade do SQL Server), deve estar executando o banco de dados primário para cada grupo de armazenamento para aceitar os logs associados ao seu grupo de armazenamento.
  
### <a name="skills-and-experience"></a>Habilidades e experiência

Várias tecnologias são usadas nessa solução de recuperação de desastres. Para ajudar a garantir que essas tecnologias interagem conforme o esperado, cada componente em locais e do ambiente do Azure deve ser instalado e configurado corretamente. É recomendável que a pessoa ou equipe que configura essa solução tenham um conhecimento de trabalho de forte e conhecimentos práticos com as tecnologias descritas nos seguintes artigos:
  
- [Serviços de replicação do arquivos distribuídos (DFS) do sistema](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Failover do Windows Server Clustering (WSFC) com o SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [Grupos de Disponibilidade AlwaysOn (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [Backup e restauração de bancos de dados do SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [Implantação de instalação e o farm do SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
Finalmente, é recomendável habilidades que você pode usar para automatizar as tarefas associadas com essas tecnologias de script. É possível usar as interfaces de usuário disponíveis para concluir todas as tarefas descritas nesta solução. No entanto, uma abordagem manual pode ser demorada e sujeita a erros e fornece resultados inconsistentes.
  
Além do Windows PowerShell, também há bibliotecas do Windows PowerShell para SQL Server, SharePoint Server e Windows Azure. Não se esqueça T-SQL, que também pode ajudar a reduzir o tempo para configurar e manter seu ambiente de recuperação de desastres.
  
## <a name="disaster-recovery-roadmap"></a>Mapa de recuperação de desastres

![Representação visual do mapa de recuperação de desastres do SharePoint.](media/Azure-DRroadmap.png)
  
Este mapa pressupõe que você já tem um farm do SharePoint Server 2013 implantado na produção.
  
**Tabela: Mapa para recuperação de desastres**

|**Fase**|**Descrição**|
|:-----|:-----|
|Fase 1  <br/> |Projete o ambiente de recuperação de desastres.  <br/> |
|Fase 2  <br/> |Crie a rede virtual do Azure e uma conexão VPN.  <br/> |
|Fase 3  <br/> |Implante a rede virtual do Azure Active Directory do Windows e serviços de nome de domínio.  <br/> |
|Fase 4  <br/> |Implante o farm de recuperação do SharePoint no Windows Azure.  <br/> |
|Fase 5  <br/> |Configure DFSR entre os farms.  <br/> |
|Fase 6  <br/> |Configure o envio de logs para o farm de recuperação.  <br/> |
|Fase 7  <br/> | Valide soluções de failover e recuperação. Isso inclui os seguintes procedimentos e tecnologias: <br/>  Pare o envio de log. <br/>  Restaure os backups. <br/>  Rastrear o conteúdo. <br/>  Recupere serviços. <br/>  Gerencie registros DNS. <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>Fase 1: Criar o ambiente de recuperação de desastres

Use as diretrizes in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) para criar o ambiente de recuperação de desastre, incluindo o farm de recuperação do SharePoint. Você pode usar os elementos gráficos no arquivo do Visio de [Solução de recuperação de desastres do SharePoint no Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) para iniciar o processo de design. Recomendamos que você crie de todo o ambiente antes de iniciar qualquer trabalho no ambiente do Azure.
  
Além das diretrizes fornecidas no [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) para projetar a rede virtual, conexão VPN, Active Directory e farm do SharePoint, certifique-se de adicionar uma função de compartilhamento de arquivo para o ambiente do Azure.
  
Para suportar o envio de log em uma solução de recuperação de desastre, uma máquina de virtual de compartilhamento de arquivo é adicionada à sub-rede em que as funções de banco de dados residem. O compartilhamento de arquivos também serve como o terceiro nó da maioria nó para o grupo de disponibilidade do SQL Server AlwaysOn. Esta é a configuração recomendada para um farm do SharePoint padrão que usa os grupos de disponibilidade AlwaysOn do SQL Server. 
  
> [!NOTE]
> É importante revisar os pré-requisitos para um banco de dados participar de um grupo de disponibilidade do SQL Server AlwaysOn. Para obter mais informações, consulte [os pré-requisitos, restrições e recomendações para grupos de disponibilidade do AlwaysOn](https://go.microsoft.com/fwlink/p/?LinkId=510870). 
  
**Figura: O posicionamento de um servidor de arquivos usado para uma solução de recuperação de desastres**

![Mostra uma VM de compartilhamento de arquivos adicionada ao mesmo serviço de nuvem que contém as funções de servidor de banco de dados do SharePoint.](media/AZenv-FSforDFSRandWSFC.png)
  
Neste diagrama, uma máquina de virtual de compartilhamento de arquivo é adicionada à mesma sub-rede no Azure que contém as funções de servidor de banco de dados. Não adicione a máquina virtual do compartilhamento de arquivo a uma disponibilidade definidas com outras funções de servidor, como as funções do SQL Server.
  
Se você estiver preocupado com a alta disponibilidade dos logs, considere adotar uma abordagem de diferente usando o [SQL Server backup e restauração com o serviço de armazenamento de Blob do Azure](https://go.microsoft.com/fwlink/p/?LinkId=393113). Esse é um novo recurso no Azure que salva logs diretamente em uma URL de armazenamento de blob. Esta solução não inclui diretrizes sobre como usar esse recurso.
  
Ao criar o farm de recuperação, tenha em mente que um ambiente de recuperação de desastres bem-sucedido reflete com precisão o farm de produção que você deseja recuperar. O tamanho do farm de recuperação não é o mais importante no design do farm de recuperação, implantação e teste. Escala de farm varia de organização para organização com base nos requisitos de negócios. Talvez seja possível usar um farm reduzido por uma breve interrupção ou até que as exigências de desempenho e capacidade exigem que você dimensionar o farm.
  
Configure o farm de recuperação identicamente forem possíveis para o farm de produção para que ele atenda às suas necessidades de (SLA) contrato de nível de serviço e fornece a funcionalidade que você precisa oferecer suporte a sua empresa. Ao criar o ambiente de recuperação de desastres, também examine seu processo de gerenciamento de alterações para o seu ambiente de produção. Recomendamos que você estenda o processo de gerenciamento de alterações para o ambiente de recuperação, atualizando o ambiente de recuperação no mesmo intervalo como um ambiente de produção. Como parte do processo de gerenciamento de alteração, é recomendável manter um inventário detalhado de sua configuração de farm, aplicativos e usuários. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Fase 2: Criar a rede virtual do Azure e uma conexão VPN

[Conectar um local de rede para uma rede virtual do Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) mostra como planejar e implantar a rede virtual no Windows Azure e como criar a conexão VPN. Siga as orientações no tópico para concluir os procedimentos a seguir:
  
- Planeje o espaço de endereço IP particular da rede Virtual.
    
- Planeje as alterações de infra-estrutura de roteamento para a rede Virtual.
    
- Planeje regras de firewall para o tráfego de e para o dispositivo VPN local.
    
- Criar a rede virtual entre locais no Azure.
    
- Configure o roteamento entre sua rede local e a rede Virtual.
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Fase 3: Implantar o Active Directory e serviços de nome de domínio à rede virtual do Azure

Essa fase inclui Implantando o Windows Server Active Directory e DNS à rede Virtual em um cenário híbrido, conforme descrito em [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) e como ilustrado na figura a seguir.
  
**Figura: Configuração de domínio do Active Directory de híbrido**

![As duas máquinas virtuais implantadas na rede virtual do Azure e na sub-rede do Farm do SharePoint são réplicas de controladores de domínios e de servidores DNS](media/AZarch-HyADdomainConfig.png)
  
Na ilustração, duas máquinas virtuais são implantadas para a mesma sub-rede. Essas máquinas virtuais são a cada duas funções hospedagem: Active Directory e DNS.
  
Antes de implantar o Active Directory no Windows Azure, leia [as diretrizes para implantar o Windows Server Active Directory nas máquinas virtuais do Windows Azure](https://go.microsoft.com/fwlink/p/?linkid=392681). Estas diretrizes ajudam a determinar se você precisa de uma arquitetura diferente ou configurações diferentes para sua solução.
  
Para obter orientações detalhadas sobre como configurar um controlador de domínio no Windows Azure, consulte [instalar um controlador de domínio réplica Active Directory em redes virtuais do Azure](https://go.microsoft.com/fwlink/p/?LinkId=392687).
  
Antes dessa fase, você não implantar máquinas virtuais para a rede Virtual. As máquinas virtuais para hospedar o Active Directory e DNS provavelmente não são as máquinas virtuais maiores, que você precisa para a solução. Antes de implantar essas máquinas virtuais, crie primeiro a máquina virtual maior que você planeja usar em sua rede Virtual. Isso ajuda a garantir que sua solução pousar em uma marca no Azure que permite que o maior tamanho que você precisa. Você não precisará configurar essa máquina virtual neste momento. Simplesmente criá-lo e defini-la à parte. Se você não fizer isso, você pode executar com uma limitação quando você tenta criar máquinas virtuais do maiores posteriormente, que era um problema no momento em que este artigo foi escrito. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Fase 4: Implantar o farm de recuperação do SharePoint no Windows Azure

Implante o farm do SharePoint em sua rede Virtual de acordo com seus planos de design. Pode ser útil analisar o [Planning for SharePoint 2013 nos serviços de infraestrutura do Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=400984) antes de implantar o SharePoint funções no Windows Azure.
  
Considere as seguintes práticas que constatamos criando nossa prova de ambiente de conceito:
  
- Crie máquinas virtuais, usando o portal do Azure ou PowerShell.
    
- Windows Azure e o Hyper-V não dão suporte a memória dinâmica. Certifique-se de que isso é acrescentado em seus planos de capacidade e o desempenho.
    
- Reinicie as máquinas virtuais por meio da interface do Azure, não a partir do logon de máquina virtual em si. Usando a interface do Azure funciona melhor e é mais previsível.
    
- Se você deseja desligar uma máquina virtual para salvar os custos, use a interface do Azure. Se você desligar partir do logon de máquina virtual, tarifas continuam se acumulam.
    
- Use uma convenção de nomenclatura para as máquinas virtuais.
    
- Preste atenção ao qual local datacenter as máquinas virtuais estão sendo implantadas.
    
- Não há suporte para o recurso de dimensionamento automático no Windows Azure para funções do SharePoint.
    
- Não configure os itens no farm que será restaurado, como conjuntos de sites. 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Fase 5: Configurar DFSR entre os farms

Para configurar a replicação de arquivo usando DFSR, use o snap-in de gerenciamento de DNS. No entanto, antes da instalação DFSR, faça logon no seu servidor de arquivos local e o servidor de arquivos Azure e ativar o serviço no Windows.
  
No painel Gerenciador de servidores, conclua as seguintes etapas:
  
- Configure o servidor local.
    
- Inicie o **Assistente de recursos e funções de adicionar**.
    
- Abra o nó do **arquivo e serviços de armazenamento** .
    
- Selecione **Namespaces DFS** e **replicação DFS**.
    
- Clique em **Avançar** para concluir as etapas do assistente.
    
A tabela a seguir fornece links para artigos de referência DFSR e postagens de blog.
  
**Tabela: Artigos de referência para DFSR**

|**Título**|**Descrição**|
|:-----|:-----|
|[Replicação](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |Tópico do TechNet do Gerenciamento DFS com links para replicação  <br/> |
|[Replicação do DFS: Guia de sobrevivência](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |Wiki com links para informações do DFS  <br/> |
|[Replicação do DFS: Perguntas frequentes sobre](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |Tópico do TechNet de replicação do DFS  <br/> |
|[Blog de Jose Barreto](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |Blog escrito por um gerente de programa Principal da equipe do servidor de arquivos na Microsoft  <br/> |
|[A equipe de armazenamento da Microsoft - arquivo de gabinete de Blog](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |Blog sobre serviços de arquivo e recursos de armazenamento no Windows Server  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Fase 6: Configurar o envio de logs para o farm de recuperação

Envio de log é o componente crítico para configurar a recuperação de desastres nesse ambiente. Você pode usar o envio de log para enviar automaticamente os arquivos de log de transações para bancos de dados de uma instância de servidor de banco de dados primário para uma instância do servidor de banco de dados secundário. Para configurar o envio de log, consulte [Configure envio de logs no SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping). 
  
> [!IMPORTANT]
> Suporte de envio de logs no SharePoint Server está limitado a determinados bancos de dados. Para obter mais informações, consulte [Supported alta disponibilidade e opções de recuperação de desastres para bancos de dados do SharePoint (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121). 
  
## <a name="phase-7-validate-failover-and-recovery"></a>Fase 7: Validar o failover e recuperação

O objetivo dessa fase final é verificar se a solução de recuperação de desastres funciona conforme o planejado. Para fazer isso, crie um evento de failover que desliga o farm de produção e inicia o backup do farm de recuperação como uma substituição. Você pode iniciar uma situação de failover manualmente ou usando scripts.
  
A primeira etapa é interromper as solicitações de usuário de entrada para os serviços de farm ou de conteúdo. Você pode fazer isso por meio da desabilitação entradas DNS ou desligar os servidores web front-end. Depois que o farm está "desativado", você pode transferir o processamento para o farm de recuperação.
  
### <a name="stop-log-shipping"></a>Parar o envio de logs

Você deve parar o envio de log antes da recuperação do farm. Interromper o envio de log no servidor secundário no Windows Azure pela primeira vez e parariam no servidor primário no local. Use o script a seguir para interromper o envio de logs no primeiro servidor secundário e, em seguida, no servidor primário. Os nomes de banco de dados no script podem ser diferentes, dependendo do seu ambiente.
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>Restaure os backups

Backups devem ser restaurados na ordem na qual eles foram criados. Antes de restaurar um backup do log de transação específica, primeiro você deve restaurar os backups anteriores a seguintes sem retomar transações não confirmadas (ou seja, usando `WITH NORECOVERY`):
  
- O backup do banco de dados completo e o último backup diferencial - restaurar estes backups, se houver algum, sendo usado antes do backup de log de transação específica. Antes do backup do banco de dados completo ou diferencial mais recente foi criado, o banco de dados estava usando o modelo de recuperação completa ou o modelo de recuperação de log em massa.
    
- Todos os backups do log de transação - restaurar qualquer backups de logs de transação tomadas após o backup completo do banco de dados ou o backup diferencial (se você restaurar um) e antes do log de transação específica em backup. Backups de log devem ser aplicados na sequência em que foram criados, sem qualquer lacunas na cadeia de log.
    
Para recuperar o banco de dados de conteúdo no servidor secundário para que os sites de renderização, remova todas as conexões de banco de dados antes da recuperação. Para restaurar o banco de dados, execute a seguinte instrução SQL.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> Quando você usa explicitamente o T-SQL, especifique **WITH NORECOVERY** ou **WITH RECOVERY** em cada instrução de restauração para eliminar a ambiguidade — isso é muito importante ao escrever scripts. Depois que os backups completos e diferenciais são restaurados, os logs de transação possam ser restaurados no SQL Server Management Studio. Além disso, porque o envio de log já estiver parado, o banco de dados de conteúdo está em um estado de espera, portanto, você deve alterar o estado para acesso total.
  
No SQL Server Management Studio, do mouse em banco de dados **WSS_Content** , aponte para **tarefas** > **Restaurar**e clique em **Log de transações** (se você não tiver restaurado do backup completo, isso não está disponível). Para obter mais informações, consulte[restaurar um Backup do Log de transações (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).
  
### <a name="crawl-the-content-source"></a>Rastreie a fonte de conteúdo

Você deve iniciar um rastreamento completo para cada fonte de conteúdo restaurar o serviço de pesquisa. Observe que você perde algumas informações de análise do farm local, como as recomendações de pesquisa. Antes de iniciar os rastreamentos completos, use o cmdlet **Restore-SPEnterpriseSearchServiceApplication** do Windows PowerShell e especifique o banco de administração de pesquisa enviados com logs e replicado, **Search_Service__DB_<GUID>**. Este cmdlet permite que a configuração de pesquisa, esquema, propriedades gerenciadas, regras e fontes e cria um conjunto padrão de outros componentes.
  
Para iniciar um rastreamento completo, conclua as seguintes etapas:
  
1. No SharePoint 2013 Central Administration, vá para o **Gerenciamento de aplicativos** > **Aplicativos de serviço** > **Gerenciar aplicativos de serviço**e, em seguida, clique no aplicativo de serviço de pesquisa que você deseja rastrear.
    
2. Na página **Administração da pesquisa** , clique em **Fontes de conteúdo**, aponte para a fonte de conteúdo que deseja, clique na seta e, em seguida, clique em **Iniciar rastreamento completo**.
    
### <a name="recover-farm-services"></a>Recuperar serviços de farm

A tabela a seguir mostra como recuperar serviços que tiverem enviados com logs bancos de dados, os serviços que tem bancos de dados, mas não são recomendados para restaurar com envio de log e os serviços que não possuem bancos de dados.
  
> [!IMPORTANT]
> Restaurar um banco de dados do SharePoint no local ao ambiente do Azure não irá recuperar todos os serviços do SharePoint que não tiver já instalado no Azure manualmente. 
  
**Tabela: Referência de banco de dados de aplicativo de serviço**

|**Restaurar esses serviços de bancos de dados enviados com logs**|**Esses serviços tem bancos de dados, mas é recomendável que você iniciar esses serviços sem restaurar seus bancos de dados**|**Esses serviços não armazene dados nos bancos de dados; iniciar esses serviços após o failover**|
|:-----|:-----|:-----|
| Serviço de Tradução Automática <br/>  Serviço de Metadados Gerenciados <br/>  Serviço de Repositório Seguro <br/>  Perfil de usuário. (Somente, os bancos de dados de perfil e marcação Social são suportados. O banco de dados de sincronização não é suportado). <br/>  Serviço de Configurações de Assinatura do Microsoft SharePoint Foundation <br/> | Coleta de Dados de Uso e Integridade <br/>  Serviço de Controle de Sessão <br/>  Automação do Word <br/> | Serviços do Excel <br/>  Serviços PerformancePoint <br/>  Conversão do PowerPoint <br/>  Serviço de Gráficos do Visio <br/>  Gerenciamento de Trabalho <br/> |
   
O exemplo a seguir mostra como restaurar o serviço de metadados gerenciados de um banco de dados.
  
Isso usa o banco de dados existente do Managed_Metadata_DB. Esse banco de dados é log enviado, mas há em um aplicativo de serviço ativas no farm secundário, portanto ela precisa estar conectado depois que o aplicativo de serviço está no lugar.
  
Primeiro, use `New-SPMetadataServiceApplication`e especifique o `DatabaseName` alternar com o nome do banco de dados restaurado.
  
Em seguida, configure o novo aplicativo de serviço de metadados gerenciados no servidor secundário, da seguinte maneira:
  
- Nome: Serviço de metadados gerenciados
    
- Servidor de banco de dados: O nome do banco de dados do log de transações remetido
    
- Nome do banco de dados: Managed_Metadata_DB
    
- Pool de aplicativos: aplicativos de serviço do SharePoint 
    
### <a name="manage-dns-records"></a>Gerenciar registros DNS

Você deve criar manualmente registros DNS para apontar para seu farm do SharePoint.
  
Na maioria dos casos em que você tiver vários servidores web front-end, faz sentido para aproveitar o recurso de balanceamento de carga de rede no Windows Server 2012 ou um balanceador de carga de hardware para distribuir as solicitações entre os servidores web front-end no farm. Balanceamento de carga de rede também pode ajudar a reduzir o risco, distribuindo solicitações para os outros servidores se um dos seus servidores web front-end falhar. 
  
Normalmente, quando você configura o balanceamento de carga de rede, o cluster é atribuído a um único endereço IP. Em seguida, crie um registro de host DNS no provedor de DNS para a sua rede que aponta para o cluster. (Para esse projeto, podemos colocar um servidor DNS no Windows Azure para resiliência em caso de uma falha de datacenter local.) Por exemplo, você pode criar um registro de DNS, em Gerenciador de DNS no Active Directory, por exemplo, chamado `http://sharepoint.contoso.com`, que aponta para o endereço IP do cluster com balanceamento de carga.
  
Para obter acesso externo ao seu farm do SharePoint, você pode criar um registro de host em um servidor DNS externo com a mesma URL que os clientes usam na sua intranet (por exemplo, `http://sharepoint.contoso.com`) que aponta para um endereço IP externo em seu firewall. (Uma prática recomendada, usando esse exemplo, é configurar o DNS dividido para que o servidor DNS interno é autoritativo para `contoso.com` e encaminha solicitações diretamente ao cluster de farm do SharePoint, em vez de solicitações de roteamento DNS para seu servidor DNS externo.) Em seguida, você pode mapear o endereço IP externo para o endereço IP interno do cluster local para que os clientes encontram os recursos que estão procurando.
  
A partir daqui, você pode executar em alguns cenários de recuperação de desastres diferentes:
  
 **Cenário de exemplo: farm do SharePoint no local não está disponível devido a falha de hardware no farm do SharePoint local.** Nesse caso, após concluir as etapas de failover ao farm do SharePoint do Azure, você pode configurar a rede balanceamento de carga na recuperação do SharePoint servidores da web front-end do farm, da mesma maneira que você fez com o farm local. Em seguida, você pode redirecionar o registro de host em seu provedor de DNS interno para apontar para o endereço IP do cluster do farm de recuperação. Observe que pode levar algum tempo antes de registros DNS em cache nos clientes são atualizado e apontar para o farm de recuperação.
  
 **Cenário de exemplo: O datacenter local é completamente perdido.** Esse cenário pode ocorrer devido a um desastre natural, como um incêndio ou inundação. Nesse caso, para uma empresa, você provavelmente teria um datacenter secundário hospedado em outra região, bem como sua sub-rede Azure que tem seus próprios serviços de diretório e o DNS. Como no cenário anterior de desastre, você pode redirecionar seus registros DNS internos e externos para apontar para o farm do SharePoint do Azure. Novamente, tenha em mente que a propagação de registro de DNS pode levar algum tempo.
  
Se você estiver usando conjuntos de sites nomeados por host, conforme recomendado na [arquitetura do conjunto de sites nomeados por Host e implantação (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment), você pode ter vários conjuntos de sites hospedados pelo mesmo aplicativo web em seu farm do SharePoint, com exclusivo Nomes DNS (por exemplo, `http://sales.contoso.com` e `http://marketing.contoso.com`). Nesse caso, você pode criar registros DNS para cada conjunto de sites que apontam para seu endereço IP do cluster. Depois que uma solicitação chega seus servidores web front-end do SharePoint, eles lidar com o roteamento de cada solicitação para o conjunto de sites apropriado.
  
## <a name="microsoft-proof-of-concept-environment"></a>Ambiente de prova de conceito da Microsoft

Podemos projetado e testado um ambiente de prova de conceito para essa solução. O objetivo do design para nosso ambiente de teste foi implantar e recuperar um farm do SharePoint que podem ser encontradas no ambiente do cliente. Que fizemos suposições várias, mas sabíamos que o farm necessários para fornecer toda a funcionalidade de caixa sem quaisquer personalizações. A topologia foi projetada para alta disponibilidade usando as diretrizes de práticas recomendadas do grupo de campo e o produto.
  
A tabela a seguir descreve as máquinas virtuais do Hyper-V que podemos criada e configurada para o ambiente de teste no local.
  
**Tabela: teste de máquinas virtuais para o local**

|**Nome do servidor**|**Função**|**Configuração**|
|:-----|:-----|:-----|
|DC1  <br/> |Controlador de domínio com o Active Directory.  <br/> |Dois processadores  <br/> De 512 MB por meio de 4 GB de RAM  <br/> 1 x 127 GB de disco rígido  <br/> |
|RRAS  <br/> |Servidor configurado com a função de roteamento e acesso remoto (RRAS).  <br/> |Dois processadores  <br/> 2-8 GB de RAM  <br/> 1 x 127 GB de disco rígido  <br/> |
|FS1  <br/> |Servidor de arquivos com um ponto de extremidade DFSR e compartilhamentos para fazer backups.  <br/> |Quatro processadores  <br/> 2-12 GB de RAM  <br/> 1 x 127 GB de disco rígido  <br/> 1 x 1 TB no disco rígido (SAN)  <br/> 1 x 750 GB de disco rígido  <br/> |
|SP-WFE1, SP-WFE2  <br/> |Servidores web front-end.  <br/> |Quatro processadores  <br/> 16 GB de RAM  <br/> |
|SP-APP1, SP-APP2, SP-APP3  <br/> |Servidores de aplicativos.  <br/> |Quatro processadores  <br/> 2-16 GB de RAM  <br/> |
|SP-SQL-HA1, SP-SQL-HA2  <br/> |Servidores de banco de dados, configurados com grupos de disponibilidade do SQL Server 2012 AlwaysOn para fornecer alta disponibilidade. Essa configuração utiliza SP-SQL-HA1 e SP-SQL-HA2, como as réplicas primárias e secundárias.  <br/> |Quatro processadores  <br/> 2-16 GB de RAM  <br/> |
   
A tabela a seguir descreve as configurações de unidade para as máquinas virtuais do Hyper-V que podemos criada e configurada para o web front-end e servidores de aplicativos para o ambiente de teste no local.
  
**Tabela: requisitos de unidade de máquina Virtual para Web Front End e servidores de aplicativos para o local de teste**

|**Letra da unidade**|**Tamanho**|**Nome do diretório**|**Path**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Unidade do sistema  <br/> |<DriveLetter>:\\Arquivos de programa\\Microsoft SQL Server\\  <br/> |
|J  <br/> |80  <br/> |Unidade de log (40 GB)  <br/> |<DriveLetter>:\\Arquivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\dados  <br/> |
|Sex.  <br/> |80  <br/> |Página (36 GB)  <br/> |<DriveLetter>:\\Arquivos de programa\\Microsoft SQL Server\\MSSQL\\dados  <br/> |
   
A tabela a seguir descreve as configurações de unidade para as máquinas virtuais do Hyper-V criada e configurada para servir como servidores de banco de dados do local. Na página **Configuração do mecanismo de banco de dados** , acesse a guia de **Diretórios de dados** para definir e confirme as configurações mostradas na tabela a seguir.
  
**Tabela: requisitos de unidade de máquina Virtual para o servidor de banco de dados para o local de teste**

|**Letra da unidade**|**Tamanho**|**Nome do diretório**|**Path**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Diretório raiz de dados  <br/> |<DriveLetter>:\\Arquivos de programa\\Microsoft SQL Server\\  <br/> |
|J  <br/> |500  <br/> |Diretório de banco de dados do usuário  <br/> |<DriveLetter>:\\Arquivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\dados  <br/> |
|Sex.  <br/> |500  <br/> |Diretório de log do banco de dados de usuário  <br/> |<DriveLetter>:\\Arquivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\dados  <br/> |
|Y  <br/> |500  <br/> |Diretório Temp DB  <br/> |<DriveLetter>:\\Arquivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\dados  <br/> |
|X  <br/> |500  <br/> |Diretório de log Temp DB  <br/> |<DriveLetter>:\\Arquivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\dados  <br/> |
   
### <a name="setting-up-the-test-environment"></a>Configurar o ambiente de teste

Durante as fases de implantação diferentes, a equipe de testes geralmente trabalhou na arquitetura local primeira e, em seguida, no ambiente do Azure correspondente. Isso reflete os casos reais gerais onde farms de produção internamente já estão sendo executadas. O que é ainda mais importante é que você deve conhecer a carga de trabalho de produção atual, a capacidade e desempenho típico. Além de como criar um modelo de recuperação de desastres que pode atender aos requisitos de negócios, você deve dimensionar os servidores do farm de recuperação para proporcionar um nível mínimo de serviço. Em um ambiente em espera a frio ou passiva, um farm de recuperação é geralmente menor que um farm de produção. Após a recuperação de farm seja estável e na produção, o farm pode ser dimensionado up e out para atender aos requisitos de carga de trabalho.
  
Implantamos nosso ambiente de teste nos seguintes três fases:
  
- Configurar a infraestrutura híbrida
    
- Provisione os servidores
    
- Implantar os farms do SharePoint
    
#### <a name="set-up-the-hybrid-infrastructure"></a>Configurar a infraestrutura híbrida

Esta fase envolvida configurar um ambiente de domínio para o farm local e para o farm de recuperação no Windows Azure. Além das tarefas normais associadas à configuração do Active Directory, a equipe de teste implementou uma solução de roteamento e uma conexão VPN entre os dois ambientes.
  
#### <a name="provision-the-servers"></a>Provisione os servidores

Além dos servidores do farm, era necessário para servidores de provisionamento para os controladores de domínio e configurar um servidor para manipular RRAS, bem como a VPN to-site. Dois servidores de arquivos foram provisionados para o serviço DFSR e vários computadores cliente foram provisionados para os testadores.
  
#### <a name="deploy-the-sharepoint-farms"></a>Implantar os farms do SharePoint

Os farms do SharePoint foram implantados em dois estágios para simplificar a estabilização do ambiente e a solução de problemas, se necessário. Durante a primeira etapa, cada farm foi implantado no número mínimo de servidores para cada camada da topologia para suportar a funcionalidade necessária.
  
Criamos os servidores de banco de dados com o SQL Server instalado antes de criar os servidores do SharePoint 2013. Como se tratava de uma nova implantação, criamos os grupos de disponibilidade antes de implantar o SharePoint. Criamos três grupos com base em diretrizes de práticas recomendadas MCS. 
  
> [!NOTE]
> Crie espaço reservado bancos de dados para que você possa criar grupos de disponibilidade antes da instalação do SharePoint. Para obter mais informações, consulte [Configurar o SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)
  
Podemos criado o farm e Unido servidores adicionais na seguinte ordem:
  
- Provisione SP-SQL-HA1 e SP-SQL-HA2.
    
- Configurar o AlwaysOn e crie os três grupos de disponibilidade para o farm. 
    
- Provisionar SP-APP1 para hospedar a Administração Central.
    
- Provisione SP-WFE1 e SP-WFE2 para hospedar o cache distribuído. 
    
Nós usamos o parâmetro _skipRegisterAsDistributedCachehost_ quando executamos **psconfig.exe** na linha de comando. Para obter mais informações, consulte [plano para feeds e serviço de Cache distribuído no SharePoint Server 2013](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service). 
  
Podemos repetido as seguintes etapas no ambiente de recuperação:
  
- Provisione AZ-SQL-HA1 e AZ-SQL-HA2.
    
- Configurar o AlwaysOn e crie os três grupos de disponibilidade para o farm.
    
- Provisionar AZ-APP1 para hospedar a Administração Central.
    
- Provisione AZ-WFE1 e AZ-WFE2 para hospedar o cache distribuído.
    
Depois, configuramos o cache distribuído e usuários de teste adicionado e conteúdo de teste, começamos estágio dois da implantação. Isso necessário ampliando as camadas e configurando os servidores do farm para oferecer suporte a topologia de alta disponibilidade descrita na arquitetura do farm.
  
A tabela a seguir descreve as máquinas virtuais, sub-redes e conjuntos de disponibilidade que configuramos para nosso farm de recuperação.
  
**Tabela: Infraestrutura de farm de recuperação**

|**Nome do servidor**|**Função**|**Configuração**|**Subrede**|**Conjunto de disponibilidade**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Controlador de domínio com o Active Directory  <br/> |Dois processadores  <br/> De 512 MB por meio de 4 GB de RAM  <br/> 1 x 127 GB de disco rígido  <br/> |SP-ADservers  <br/> ||
|AZ-SP-FS  <br/> |Servidor de arquivos com compartilhamentos para fazer backups e um ponto de extremidade para DFSR  <br/> | Configuração de a5: <br/>  Dois processadores <br/>  14 GB de RAM <br/>  1 x 127 GB de disco rígido <br/>  1 x 135 GB de disco rígido <br/>  1 x 127 GB de disco rígido <br/>  1 x 150 GB de disco rígido <br/> |SP-databaseservers  <br/> |DATA_SET  <br/> |
|AZ-WFE1, AZ-WFE2  <br/> |Servidores de Front End Web  <br/> | Configuração de a5: <br/>  Dois processadores <br/>  14 GB de RAM <br/>  1 x 127 GB de disco rígido <br/> |SP-servidores Web  <br/> |WFE_SET  <br/> |
|AZ-APP1, AZ-APP2, AZ-APP3  <br/> |Servidores de aplicativos  <br/> | Configuração de a5: <br/>  Dois processadores <br/>  14 GB de RAM <br/>  1 x 127 GB de disco rígido <br/> |SP-applicationservers  <br/> |APP_SET  <br/> |
|AZ - SQL-HA1, AZ - SQL-HA2  <br/> |Servidores de banco de dados e as réplicas primária e secundária para grupos de disponibilidade do AlwaysOn  <br/> | Configuração de a5: <br/>  Dois processadores <br/>  14 GB de RAM <br/> |SP-databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>Operações

Depois que a equipe de teste estabilizada os ambientes de farm e concluiu os testes funcionais, eles iniciado as seguintes operações de tarefas necessárias para configurar o ambiente de recuperação de local:
  
- Configure os backups completos e diferenciais.
    
- Configure DFSR nos servidores de arquivos que transferir os logs de transações entre o ambiente local e o ambiente do Azure.
    
- Configure o envio de logs no servidor de banco de dados primário.
    
- Estabilização, validar e solucionar problemas de envio de log, conforme necessário. Isso incluiu identificar e documentar qualquer comportamento que pode causar problemas, como a latência de rede, que pode causar falhas de sincronização de arquivo DFSR ou de envio de log.
    
### <a name="databases"></a>Bancos de dados

Nossos testes de failover envolvidos seguintes bancos de dados: 
  
- WSS_Content
    
- ManagedMetadata
    
- BD Perfil
    
- Sincronização DB
    
- Banco de dados social
    
- Hub de tipo de conteúdo (um banco de dados para um Hub de agregação de tipo de conteúdo dedicado)
    
## <a name="troubleshooting-tips"></a>Dicas de solução de problemas

A seção explica os problemas encontrados durante a nossos testes e suas soluções. 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Usando a ferramenta de gerenciamento de repositório de termos causou o erro, "o repositório de metadados gerenciados ou Conexão atualmente não está disponível."

Certifique-se de que a conta do pool de aplicativos usada pelo aplicativo web tem o acesso de leitura a permissão de repositório de termos.
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Conjuntos de termos personalizado não estão disponíveis no conjunto de sites

Verifique se há uma associação de aplicativo de serviço ausentes entre seu hub de tipo de conteúdo e seu conjunto de sites de conteúdo. Além disso, sob o **metadados gerenciados - <site collection name> Conexão** propriedades de tela, verifique se essa opção está habilitada: **Este aplicativo de serviço é o local de armazenamento padrão para conjuntos de termos específicos de coluna.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>O comando Get-ADForest Windows PowerShell gerará o erro, "o termo 'Get-ADForest' não é reconhecido como o nome de um cmdlet, função, arquivo de script ou um programa operável."

Ao configurar perfis de usuário, é necessário o nome da floresta do Active Directory. No Assistente para recursos e adicionar funções, certifique-se de que você ativou o Active Directory módulo para Windows PowerShell (sob o **Ferramentas de administração de servidor remoto > Ferramentas de administração de função > AD DS e ferramentas do AD LDS** seção). Além disso, execute os comandos a seguintes antes de usar o **Get-ADForest** para ajudar a garantir que seu software dependências são carregadas.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwaysonhealth-xevent-session-on-server-name"></a>Falha de criação do grupo de disponibilidade em iniciando a sessão XEvent 'AlwaysOn_health' em '<server name>'

Verifique se ambos os nós do cluster de failover estão o Status "Até" e não "Pausado" ou "Parado". 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>Trabalho de envio de log do SQL Server falha com acesso negado erro ao tentar se conectar ao compartilhamento de arquivos

Certifique-se de que o SQL Server Agent esteja em execução em credenciais de rede, no lugar das credenciais padrão.
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>Trabalho de envio de log do SQL Server indica êxito, mas não há arquivos são copiados

Isso acontece porque a preferência de backup padrão para um grupo de disponibilidade é **Preferir secundário**. Certifique-se de que você execute o trabalho de envio de log do servidor secundário para o grupo de disponibilidade, em vez de primário; Caso contrário, o trabalho falhará silenciosamente. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Falha ao iniciar automaticamente após a instalação o serviço de metadados gerenciados (ou outro serviço do SharePoint)

Serviços podem levar alguns minutos para ser iniciados, dependendo do desempenho e a carga atual do seu servidor do SharePoint. Clique em **Iniciar** para o serviço e forneça tempo adequado para inicialização ao atualizar ocasionalmente, os serviços na tela de servidor para monitorar seu status manualmente. Caso o serviço permanecerá parado, habilitar o log de diagnóstico do SharePoint, tentar iniciar o serviço novamente e verifique o log de erros. Para obter mais informações, consulte [Configure diagnostic logging in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Após alterar o DNS para o ambiente de failover do Windows Azure, navegadores de cliente continuam a usar o endereço IP antigo para o site do SharePoint

Sua alteração DNS pode não ser visível para todos os clientes imediatamente. Em um cliente de teste, execute o seguinte comando em um prompt de comando elevado e tentar acessar o site novamente.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Recursos adicionais

[Suporte para as opções de alta disponibilidade e recuperação de desastres para bancos de dados do SharePoint](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[Configurar grupos de disponibilidade AlwaysOn do SQL Server 2012 no SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>Confira também

[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)



