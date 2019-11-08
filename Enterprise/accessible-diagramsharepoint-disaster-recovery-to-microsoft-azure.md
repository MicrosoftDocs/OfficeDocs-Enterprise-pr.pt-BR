---
title: Diagrama acessível-recuperação de desastre do SharePoint para o Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Este artigo é uma versão de texto acessível do diagrama chamado recuperação de desastre do SharePoint para o Microsoft Azure.
ms.openlocfilehash: e711452f6e019ceb280d43c2e0167507a0b0ef20
ms.sourcegitcommit: b4514cd852093181dd4c27009a78aca3ca50d2e2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2019
ms.locfileid: "38038230"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>Diagrama acessível-recuperação de desastre do SharePoint para o Microsoft Azure

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado recuperação de desastre do SharePoint para o Microsoft Azure.
  
Este cartaz fornece exemplos de arquiteturas para a criação de um ambiente de recuperação no Azure. 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>Ambiente local com um ambiente de recuperação do Azure

O diagrama mostra um exemplo de arquitetura usada para o ambiente de produção de um ambiente local que usa o Azure para recuperação. 
  
### <a name="on-premises-production-environment"></a>Ambiente de produção local

O diagrama a seguir mostra um ambiente de produção ativo com quatro camadas de servidores em um farm de servidores. 
  
#### <a name="tier-1"></a>Camada 1

Há dois servidores para o processamento de consultas e serviços de front-end. Há uma partição de índice que fornece uma réplica dos dois servidores. 
  
#### <a name="tier-2"></a>Camada 2

Há dois servidores para o cache distribuído nessa camada. 
  
#### <a name="tier-3"></a>Camada 3

Há três servidores nessa camada. Cada servidor fornece os seguintes serviços: 
  
- Serviços de backend 
    
- Admin 
    
- Gerenciador de fluxos de trabalho 
    
- Rastreamento 
    
- Processamento de conteúdo 
    
- Análise 
    
#### <a name="tier-4"></a>Camada 4

Há dois servidores nessa camada. Ambos os servidores têm três grupos de disponibilidade, da seguinte maneira: 
  
- O grupo de disponibilidade #1 fornece recursos de pesquisa. 
    
- O grupo de disponibilidade #2 fornece aplicativos de conteúdo, configuração e serviço. 
    
- O grupo de disponibilidade #3 fornece conteúdo. 
    
Há também um servidor de compartilhamento de arquivos nessa camada. Os servidores de camada 4 usam o envio de logs para se comunicar com este servidor. Este servidor, por sua vez, se comunica através da replicação do sistema de arquivos distribuídos (DFSR) para um servidor de compartilhamento de arquivos no ambiente de recuperação de espera passiva do Azure, conforme descrito na seção a seguir. 
  
### <a name="azure-recovery-environment"></a>Ambiente de recuperação do Azure

#### <a name="warm-standby-environment-running-virtual-machines"></a>Ambiente de espera passiva executando máquinas virtuais

O diagrama a seguir mostra o ambiente local replicado exatamente no ambiente de recuperação do Azure. O servidor de compartilhamento de arquivos desse ambiente está vinculado ao ambiente local por meio do DFSR. O DFSR transfere logs do ambiente de produção para o ambiente de recuperação por meio do servidor de compartilhamento de arquivos. 
  
### <a name="overview"></a>Visão geral

O ambiente de recuperação de desastres para um farm local do SharePoint 2013 pode ser hospedado no Azure. 
  
-  Os serviços de infraestrutura do Azure fornecem um data center secundário.
    
- Pague apenas os recursos que você usa. 
    
- Pequenos farms de recuperação podem ser dimensionados após um desastre para atender às metas de escala e capacidade. 
    
O farm de recuperação no Azure é configurado da forma mais idêntica possível para o farm local de produção. 
  
- Mesma representação de funções de servidor. 
    
- Mesma configuração de personalizações. 
    
- Mesma configuração dos recursos de pesquisa (eles podem estar em uma versão menor do farm de produção). 
    
O envio de logs e o DFSR são usados para copiar backups de banco de dados e logs de transações para o farm do Azure. 
  
- O DFSR é usado para transferir logs do ambiente de produção para o ambiente de recuperação. Em um cenário WAN, a DFSR é mais eficiente do que enviar os logs diretamente para o servidor secundário no Azure. 
    
- Os logs são repetidos nos computadores do SQL Server baseados no Azure. 
    
- Os bancos de dados enviados por log não são anexados ao farm até que um exercício de recuperação seja realizado. 
    
Procedimentos de failover: 
  
1. Parar o envio de logs. 
    
2. Pare de aceitar o tráfego para o farm principal. 
    
3. Reproduza os logs de transação finais. 
    
4. Anexe os bancos de dados de conteúdo ao farm. 
    
5. Inicie um rastreamento completo. 
    
6. Restaure os aplicativos de serviço dos bancos de dados de serviços replicados. 
    
Os objetivos de recuperação fornecidos por esta solução incluem: 
  
- Sites e conteúdo 
    
- Pesquisar (rastreado novamente, sem histórico de pesquisa) 
    
- Serviços
    
Itens adicionais que podem ser tratados pelos serviços de consultoria da Microsoft ou por um parceiro: 
  
- Sincronizando soluções de farm personalizadas 
    
- Conexões com fontes de dados locais (BDC (conectividade de dados corporativos) e fontes de conteúdo de pesquisa) 
    
- Cenários de restauração de pesquisa 
    
- Objetivos de tempo de recuperação (RTO) e objetivos de ponto de recuperação (RPO) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>Ambiente de espera Cold executando máquinas virtuais

Os ambientes de espera Cold levam mais tempo para começar, mas são menos caros. 
  
- O farm está totalmente construído, mas as máquinas virtuais são interrompidas após a criação do farm. Você paga apenas os custos de processamento quando as máquinas virtuais estão em execução, mas os custos de transferência de dados de rede e armazenamento são aplicáveis. 
    
- No caso de um desastre, todas as máquinas virtuais no farm são iniciadas e corrigidas. 
    
- Os backups e logs de transações são aplicados aos bancos de dados do farm. 
    
A lista a seguir descreve procedimentos adicionais para ambientes de espera Cold: 
  
- Ative as máquinas virtuais regularmente para corrigir, atualizar e verificar o ambiente. 
    
- Execute procedimentos para atualizar DNS e endereços IP. 
    
- Configure o AlwaysOn do SQL após um failover. 
    
O diagrama a seguir mostra um ambiente de recuperação replicado em máquinas virtuais. Após o failover para um ambiente de espera Cold, todas as máquinas virtuais são iniciadas e os grupos de disponibilidade são configurados usando logs de repetição para disponibilizar os servidores de banco de dados. 
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Ambiente de recuperação do SharePoint no Azure

Projete e construa o ambiente de failover no Azure. 
  
- Criar uma rede virtual no Azure. 
    
- Conecte a rede local com a rede virtual no Azure com uma conexão VPN de site a site. Esta conexão usa um gateway dinâmico no Azure. 
    
- Implante um ou mais controladores de domínio na rede virtual do Azure e configure-os para que funcionem com seu domínio local. Esses controladores de domínio são servidores de catálogo. 
    
- Adaptar o farm do SharePoint para os serviços de nuvem e conjuntos de disponibilidade. 
    
- Implante o farm do SharePoint, além de um servidor de arquivos para hospedar compartilhamentos de arquivos. 
    
- Configurar o envio de logs e o DFSR entre o ambiente local e o ambiente de recuperação baseado no Azure. 
    
O diagrama a seguir mostra o ambiente local e a rede virtual do Azure com os seguintes recursos: 
  
### <a name="on-premises-environment"></a>Ambiente no local

- Windows Server 2012 RRAS 
    
- Servidor do Active Directory 
    
A interface de rede local com a rede virtual do Azure por meio de um gateway VPN (rede virtual privada). 
  
### <a name="azure-virtual-network"></a>Rede virtual do Azure

As interfaces de gateway VPN com uma sub-rede ativa de gateway VPN. 
  
Há três serviços de nuvem na rede virtual do Azure: 
  
- O primeiro serviço de nuvem tem dois servidores Active Directory e DNS com um conjunto de disponibilidade. 
    
- O segundo serviço de nuvem tem três conjuntos de servidores: dois servidores de cache distribuído com um conjunto de disponibilidade. Dois servidores front-end com um conjunto de disponibilidade. Três servidores de back-end com um conjunto de disponibilidade.
    
- O terceiro serviço de nuvem tem três servidores de banco de dados com um conjunto de disponibilidade. Um desses servidores de banco de dados é um compartilhamento de arquivos para o envio de logs e um terceiro nó de uma maioria de nós para o SQL Server AlwaysOn. 
    
### <a name="build-the-ad-ds-hybrid-environment"></a>Criar o ambiente híbrido do AD DS

A configuração do AD DS para esta solução constitui um cenário de implantação híbrida no qual o AD DS é implantado parcialmente no local e implantado parcialmente nas máquinas virtuais do Azure. 
  
Importante — antes de implantar o AD DS no Azure, leia as diretrizes para implantar o Windows Server Active Directory nas máquinas virtuais dohttps://docs.microsoft.com/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100)Microsoft Azure (. 
  
 
Essa arquitetura de referência inclui duas máquinas virtuais configuradas como controladores de domínio. Cada uma é configurada da seguinte maneira: 
  
- Tamanho – pequeno. 
    
- Sistema operacional — Windows Server 2012. 
    
- Função — controlador de domínio AD DS designado como um servidor de catálogo global. Essa configuração reduz o tráfego de egresso na conexão VPN. Em um ambiente de vários domínios com altas taxas de alteração, configure os controladores de domínio no local para não sincronizar com os servidores de catálogo global no Azure. 
    
- Discos de dados — Coloque o banco de dados do AD DS, os logs e o SYSVOL nos discos de dados do Azure. Não coloque esses no disco do sistema operacional ou nos discos temporários fornecidos pelo Azure. Isso é importante. 
    
- Função — instale e configure o DNS do Windows nos controladores de domínio. 
    
- Endereços IP — use endereços IP dinâmicos. Isso exige que você crie uma rede virtual do Azure. 
    

