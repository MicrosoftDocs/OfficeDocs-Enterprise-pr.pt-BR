---
title: "Diagrama acessível - recuperação de desastres do SharePoint para o Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: "Este artigo é uma versão de texto acessível do diagrama chamado de recuperação de desastres do SharePoint para o Microsoft Azure."
ms.openlocfilehash: 2babb1910b0cd8dcbfe4cc0bf32de7c714c05fc0
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>Diagrama acessível - recuperação de desastres do SharePoint para o Microsoft Azure

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado de recuperação de desastres do SharePoint para o Microsoft Azure.
  
Este cartaz fornece exemplos de arquiteturas para a criação de um ambiente de recuperação no Windows Azure. 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>Ambiente de local com um ambiente de recuperação do Azure

O diagrama mostra um exemplo de arquitetura usado para o ambiente de produção de um ambiente de local que usa o Windows Azure para recuperação. 
  
### <a name="on-premises-production-environment"></a>Ambiente de produção do local

O diagrama acompanha mostra um ambiente de produção ao vivo com quatro níveis de servidores em um farm de servidores. 
  
#### <a name="tier-1"></a>Nível 1

Há dois servidores de serviços de front-end e processamento de consultas. Não há uma partição do índice que fornece uma réplica de ambos os servidores. 
  
#### <a name="tier-2"></a>Camada 2

Há dois servidores de cache distribuído nesse nível. 
  
#### <a name="tier-3"></a>Camada 3

Há três servidores nesse nível. Cada servidor fornece os seguintes serviços: 
  
- Serviços de back-end 
    
- Administrador 
    
- Gerenciador de fluxo de trabalho 
    
- Rastreamento 
    
- Processamento de conteúdo 
    
- Análise 
    
#### <a name="tier-4"></a>Nível 4

Há dois servidores nesse nível. Ambos os servidores têm três grupos de disponibilidade, da seguinte maneira: 
  
- Grupo de disponibilidade #1 fornece recursos de pesquisa. 
    
- Grupo de disponibilidade #2 fornece conteúdo, configuração e aplicativos de serviço. 
    
- Grupo de disponibilidade #3 fornece conteúdo. 
    
Também é um servidor nesse nível de compartilhamento de arquivo. Os servidores de camada 4 usam o envio de logs para se comunicar com este servidor. Este servidor, por sua vez, comunica-se via distribuído arquivo sistema replicação (DFSR) para um servidor de compartilhamento de arquivos no ambiente de recuperação de espera passiva Azure, conforme descrito na seção a seguir. 
  
### <a name="azure-recovery-environment"></a>Ambiente de recuperação do Azure

#### <a name="warm-standby-environment-running-virtual-machines"></a>Ambiente de em espera passiva máquinas virtuais em execução

O diagrama acompanha mostra o ambiente local replicado exatamente no ambiente de recuperação do Azure. O servidor de compartilhamento de arquivos nesse ambiente está vinculado DFSR do ambiente local. DFSR transfere logs do ambiente de produção para o ambiente de recuperação por meio do servidor de compartilhamento de arquivo. 
  
### <a name="overview"></a>Visão geral

O ambiente de recuperação de desastres para um farm do SharePoint 2013 no local pode ser hospedado no Windows Azure. 
  
-  Serviços de infraestrutura Azure fornece um datacenter secundário.
    
- Preste apenas para os recursos usados. 
    
- Farms de recuperação pequenas podem ser dimensionados após um desastre para cumprir as metas de dimensionamento e capacidade. 
    
O farm de recuperação no Windows Azure é configurado como identicamente possível ao farm do local de produção. 
  
- Mesma representação das funções de servidor. 
    
- Mesma configuração das personalizações. 
    
- Mesma configuração de recursos de pesquisa (essas podem estar em uma versão menor do que o farm de produção). 
    
Envio de logs e DFSR são usados para copiar backups de banco de dados e logs de transação para o farm do Azure. 
  
- DFSR é usado para transferir os logs do ambiente de produção para o ambiente de recuperação. Em um cenário WAN, DFSR é mais eficiente do que os logs diretamente para o servidor secundário de envio no Windows Azure. 
    
- Logs são reproduzidos nos computadores com base no Windows Azure SQL Server. 
    
- Bancos de dados enviados com logs não são anexados ao farm até que um exercício de recuperação é executado. 
    
Procedimentos de failover: 
  
1. Pare o envio de log. 
    
2. Pare de aceitar o tráfego para o farm principal. 
    
3. Repetição durante os logs de transações final. 
    
4. Anexe os bancos de dados de conteúdo ao farm. 
    
5. Inicie um rastreamento completo. 
    
6. Restaure aplicativos de serviço dos bancos de dados replicados. 
    
Objetivos de recuperação fornecidos por essa solução incluem: 
  
- Sites e conteúdo 
    
- Pesquisa (novamente não rastreado, nenhum histórico de pesquisa) 
    
- Serviços
    
Itens adicionais que podem ser abordados por um parceiro ou de serviços de consultoria da Microsoft: 
  
- Sincronizando soluções personalizadas do farm 
    
- Conexões com fontes de dados no local (conectividade de dados corporativos (BDC) e pesquisar fontes de conteúdo) 
    
- Cenários de restauração de pesquisa 
    
- Objetivos de tempo de recuperação (RTO) e objetivos de ponto de recuperação (RPO) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>Ambiente de em espera a frio máquinas virtuais em execução

Ambientes de espera a frio demoram mais para iniciar, mas são baratos. 
  
- O farm totalmente é criado, mas as máquinas virtuais são interrompidas depois que o farm é criado. Você paga apenas os custos de processamento quando as máquinas virtuais estão funcionando, mas aplicam custos de transferência de dados de armazenamento e de rede. 
    
- Em caso de desastre, todas as máquinas virtuais do farm foram iniciadas e corrigidas. 
    
- Backups e logs de transações são aplicados nos bancos de dados do farm. 
    
A lista a seguir descreve os procedimentos adicionais para ambientes de espera a frio: 
  
- Ative máquinas virtuais regularmente para o patch, atualizar e verificar o ambiente. 
    
- Execute os procedimentos para atualizar o DNS e endereços IP. 
    
- Configure SQL AlwaysOn após um failover. 
    
O diagrama acompanha mostra um ambiente de recuperação replicado nas máquinas virtuais. Após o failover para um ambiente em espera a frio, todas as máquinas virtuais são iniciadas e os grupos de disponibilidade são configurados usando logs de repetição para disponibilizar os servidores de banco de dados. 
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Ambiente de recuperação do SharePoint no Windows Azure

Projetar e criar o ambiente de failover no Windows Azure. 
  
- Crie uma rede virtual no Windows Azure. 
    
- Conecte a rede local com a rede virtual no Windows Azure com uma conexão de VPN-to-site. Esta conexão utiliza um gateway dinâmico no Windows Azure. 
    
- Implantar um ou mais controladores de domínio para a rede virtual do Azure e configurá-los para trabalhar com seu domínio local. Esses controladores de domínio são servidores de catálogo. 
    
- Adaptar-se o farm do SharePoint para conjuntos de disponibilidade e de serviços de nuvem. 
    
- Implante o farm do SharePoint mais de um servidor de arquivos em compartilhamentos de arquivos de host. 
    
- Configure o envio de log e DFSR entre o ambiente local e o ambiente de recuperação baseada no Windows Azure. 
    
O diagrama acompanha mostra o ambiente local e a rede virtual do Azure com os seguintes recursos: 
  
### <a name="on-premises-environment"></a>Ambiente no local

- Windows Server 2012 RRAS 
    
- Servidor do Active Directory 
    
As interfaces de rede local com a rede virtual do Azure através de um gateway de rede virtual privada (VPN). 
  
### <a name="azure-virtual-network"></a>Rede virtual do Azure

As interfaces de gateway VPN com uma sub-rede de gateway VPN ativa. 
  
Há três serviços de nuvem a rede virtual do Azure: 
  
- O primeiro serviço de nuvem tem dois Active Directory e servidores DNS com uma disponibilidade definida. 
    
- O serviço de nuvem segundo tem três conjuntos de servidores: dois servidores de cache com um conjunto de disponibilidade de distribuídos. Dois servidores front-end com um conjunto de disponibilidade. Três servidores back-end com um conjunto de disponibilidade.
    
- O serviço de nuvem terceiro tem três servidores de banco de dados com um conjunto de disponibilidade. Um desses servidores de banco de dados é um compartilhamento de arquivo para o nó de uma terceira e de envio de log da maioria nó para SQL Server AlwaysOn. 
    
### <a name="build-the-ad-ds-hybrid-environment"></a>Criar o ambiente híbrido do AD DS

A configuração do AD DS para essa solução constitui um cenário de implantação híbrido no qual o AD DS é parcialmente implantados no local e parcialmente implantadas em máquinas virtuais do Azure. 
  
Importante — Antes de implantar o AD DS no Windows Azure, leia as diretrizes para implantar o Windows Server Active Directory no Microsoft máquinas virtuais do Azure (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx). 
  
Para obter orientação completa sobre como projetar e implantar ambientes do Active Directory, consulte http://TechNet.microsoft.com. 
  
Essa arquitetura de referência inclui duas máquinas virtuais configuradas como controladores de domínio. Cada uma é configurada da seguinte maneira: 
  
- Tamanho — pequeno. 
    
- Sistema operacional — Windows Server 2012. 
    
- Função — Controlador de domínio de AD DS designado como um servidor de catálogo global. Essa configuração reduz o tráfego de saída entre a conexão VPN. Em um ambiente de vários domínio com altas taxas de alteração, configure o domínio controladores local não sincronizar com os servidores de catálogo global no Windows Azure. 
    
- Discos de dados — colocar o banco de dados do AD DS, logs e SYSVOL em discos de dados do Azure. Não coloque essas do disco de sistema operacional ou os discos temporários fornecidos pelo Windows Azure. Isso é importante. 
    
- Função — Instalar e configurar o DNS do Windows nos controladores de domínio. 
    
- Endereços IP — usar endereços IP dinâmicos. Isso exige a criação de uma rede Virtual do Azure. 
    

