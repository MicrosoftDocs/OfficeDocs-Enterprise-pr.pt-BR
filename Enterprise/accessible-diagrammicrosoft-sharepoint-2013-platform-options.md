---
title: Diagrama acessível – opções de plataforma do Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- SPO_Content
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
f1.keywords:
- NOCSH
description: Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft SharePoint 2013.
ms.openlocfilehash: 100645b8de8487497eca4a2581523818e18834b3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843872"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Diagrama acessível – opções de plataforma do Microsoft SharePoint 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft SharePoint 2013.
  
Quais responsáveis pelas decisões de negócios (BDMs) e arquitetos precisam saber sobre o Office 365, o Microsoft Azure e implantações locais. 
  
Este cartaz tem duas seções: 
  
- Uma comparação de quatro implantações diferentes para o SharePoint 2013: SharePoint no Office 365, um híbrido do Office 365 com uma implantação local do SharePoint 2013, Azure e uma implantação local do SharePoint 2013. 
    
- Uma descrição de três cargas de trabalho típicas para mover para o Azure. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Comparação de quatro implantações diferentes para a plataforma do SharePoint 2013

A comparação fornece informações sobre cada opção de implantação relacionada às seguintes áreas: 
  
- Uma visão geral dos diferentes recursos de implantação 
    
- O que cada tipo de implantação é ideal para 
    
- Requisitos de licença 
    
- Tarefas de arquitetura necessárias para implementar 
    
- Responsabilidades de profissionais de ti para implementação 
    
### <a name="overview"></a>Visão Geral

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

Ganhe eficiência e otimize o custo com planos multilocatários do Office 365. 
  
O diagrama a seguir mostra o SharePoint Online com um locatário do Azure Active Directory, que sincroniza nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory. 
  
Descrição dos recursos: 
  
- Software como serviço (SaaS). 
    
- O conjunto de recursos avançados está sempre atualizado. 
    
- Inclui um locatário do Azure Active Directory (pode ser usado com outros aplicativos). 
    
- A integração de diretórios inclui a sincronização de nomes de contas e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory. 
    
- Se o logon único (SSO) for um requisito, o AD FS (serviços de Federação do Active Directory) pode ser implementado. 
    
- Comunicação de cliente pela Internet por meio de acesso criptografado e autenticado (porta 443). 
    
- A migração de dados é limitada ao que pode ser carregado pela Internet. 
    
- Personalizações: aplicativos para Office, SharePoint e SharePoint Designer 2013. 
    
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

Combinar os benefícios do Office 365 com uma implantação local do SharePoint 2013. 
  
O diagrama a seguir mostra o Office 365 com o SharePoint online usando o serviços corporativos de conectividade (BCS) para se conectar a um farm local do SharePoint Server 2013. 
  
Escolha quais dos seguintes recursos serão integrados: 
  
Pesquisa do SharePoint 
  
- Os usuários podem ver os resultados de pesquisa de ambos os ambientes. 
    
- Os usuários da extranet podem fazer logon remotamente com uma conta do Active Directory local e usar toda a funcionalidade híbrida disponível. 
    
BCS
  
No SharePoint Online: os usuários podem executar operações de leitura e gravação. O serviço BCS se conecta a um farm local do SharePoint Server 2013. O serviço BCS configurado nos agentes do farm local a conexão com pontos de extremidade do serviço OData local. 
  
Duet Enterprise Online 
  
No SharePoint Online, os usuários podem realizar operações de leitura e gravação em um sistema SAP local. 
  
#### <a name="azure"></a>Azure

Aproveite a nuvem enquanto mantém o controle total da plataforma e dos recursos. 
  
O diagrama a seguir mostra o Azure, que contém dois serviços de nuvem, um farm do SharePoint 2013 e o Windows Server Active Directory com o DNS conectado a usuários pela Internet ou conectando-se ao Active Directory local via túnel VPN. 
  
Os recursos incluem: 
  
-  O Azure é uma plataforma que fornece a infraestrutura e os serviços de aplicativo necessários para hospedar um farm do SharePoint 2013.
    
- Serviços de infraestrutura. 
    
- Melhor plataforma de nuvem nativa para o SQL Server e o SharePoint. 
    
- Os recursos de computação estão disponíveis quase imediatamente sem nenhum compromisso. 
    
- Concentre-se nos aplicativos, em vez de datacenters e infraestrutura. 
    
- Ambientes de desenvolvimento e teste de baixo custo. 
    
- As soluções do SharePoint podem ser acessadas pela Internet ou acessíveis apenas de um ambiente corporativo por meio de um túnel VPN de site a site. 
    
- As personalizações não são limitadas. 
    
#### <a name="on-premises"></a>Local

Você tem tudo. 
  
O diagrama a seguir mostra um ambiente local com servidores Web, servidores de aplicativos e o Active Directory se comunicando com todos os bancos de dados e servidores de aplicativos dedicados para pesquisa. 
  
Os recursos incluem: 
  
- Planejamento de capacidade e dimensionamento. 
    
- Aquisição e configuração do servidor. 
    
- Instalação. 
    
- Expansão, aplicação de patch e operações. 
    
- Backup de dados. 
    
- Manutenção de um ambiente de recuperação de desastres. 
    
- As personalizações não são limitadas. 
    
### <a name="deployment-type-is-best-for---"></a>O tipo de implantação é melhor para o. . .

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

- Compartilhamento e colaboração externos seguros. (Recurso exclusivo!) 
    
- Intranet — sites de equipe, meus sites e colaboração interna. 
    
- Armazenamento de documentos e controle de versão na nuvem. 
    
- Site básico voltado para o público. 
    
Recursos adicionais com planos de assinatura dedicados do Office 365: 
  
- Equipamento de datacenter da Microsoft dedicado à sua organização e não compartilhado com nenhuma outra organização. 
    
- Cada ambiente do cliente reside em uma rede fisicamente separada. 
    
- Comunicação de cliente através de uma VPN protegida por IPSec ou uma conexão privada de Propriedade do cliente. A autenticação de dois fatores é opcional. 
    
- ITAR-planos de suporte. 
    
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

- Use o Office 365 para compartilhamento externo e colaboração em vez de configurar um ambiente de extranet. 
    
- Mover meus sites (OneDrive for Business) para a nuvem para facilitar o acesso dos usuários aos seus arquivos remotamente. 
    
- Inicie novos sites de equipe no Office 365. 
    
- Integre um site do Office 365 com o ambiente do SharePoint de BCS local. 
    
#### <a name="azure"></a>Azure

- SharePoint para sites da Internet — sites voltados ao público. Aproveite o Azure AD para contas de clientes e autenticação. 
    
- Ambientes de desenvolvimento, teste e preparação — rapidamente provisionar e desprovisionar ambientes inteiros. 
    
- Aplicativos híbridos — aplicativos que abrangem seu datacenter e a nuvem. 
    
- Ambiente de recuperação de desastres — recupere rapidamente de um desastre. Pagar somente para uso. 
    
- Farms que exigem relatórios ou auditoria profundas. 
    
- Web Analytics. 
    
- Criptografia de dados em repouso (os dados são criptografados nos bancos de dados SQL). 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Criptografia de dados em repouso (os dados são criptografados nos bancos de dados SQL)

- Farms no país (quando os dados precisam residir em uma jurisdição). 
    
- Soluções complexas de BI que devem residir perto de BI de dados. 
    
- Soluções de nuvem privada. 
    
- Soluções altamente personalizadas. 
    
- Soluções legadas com componentes de terceiros que dependem de hardware e software que não são suportados nos serviços de infraestrutura do Azure. 
    
- Restrições de privacidade que impedem a sincronização de contas do Active Directory com o Azure Active Directory (um requisito para o Office 365). 
    
- Organizações que preferem o controle de toda a plataforma e solução. 
    
### <a name="license-requirements"></a>Requisitos de licença

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

Modelo de assinatura. Nenhuma licença adicional necessária. 
  
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

- Office 365 – modelo de assinatura. Nenhuma licença adicional necessária. 
    
- Local – todas as licenças locais são aplicadas. 
    
#### <a name="azure"></a>Azure

-  Assinatura do Azure (inclui o sistema operacional do servidor)
    
- SQL Server 
    
- Licença de servidor do SharePoint 2013 
    
- Licença de acesso para cliente do SharePoint 2013 
    
#### <a name="on-premises"></a>Local

- Sistema operacional do servidor 
    
- SQL Server 
    
- Licença de servidor do SharePoint 2013 
    
- Licença de acesso para cliente do SharePoint 2013 
    
### <a name="architecture-tasks"></a>Tarefas de arquitetura

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

- Planejar e projetar a integração de diretórios. Duas opções. Qualquer uma das opções pode ser implantada no local ou no Azure: a sincronização de senha (requer o servidor de 1 64 bits). SSO (requer o AD FS e vários servidores). 
    
- Garantir a capacidade e a disponibilidade da rede por meio de firewalls, servidores de proxy, gateways e entre links de WAN. 
    
- Adquirir certificados SSL de terceiros para oferecer segurança corporativa para ofertas de serviços do Office 365. 
    
- Planeje o nome do locatário e projete a arquitetura e a governança do conjunto de sites. 
    
- Planejar personalizações, soluções e aplicativos para o SharePoint Online. 
    
- Decida se você deseja se conectar ao Office 365 usando o protocolo de Internet 6 (IPv6). Isso não é comum. 
    
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

Além das tarefas para os ambientes do Office 365 e local: 
  
- Determine quanta integração de recursos você deseja e escolha a topologia híbrida. Consulte este pôster de modelo: qual topologia híbrida devo usar? 
    
- Se necessário, determine qual dispositivo de servidor proxy será usado. 
    
#### <a name="azure"></a>Azure

Projete o ambiente de rede do Azure: 
  
- Rede virtual no Azure, incluindo sub-redes. 
    
- Ambiente de domínio e integração com servidores locais. 
    
- Endereços IP e DNS. 
    
- Grupos de afinidade e contas de armazenamento. 
    
Projete o ambiente do SharePoint no Azure: 
  
- Topologia de farm do SharePoint e arquitetura lógica. 
    
-  Conjuntos de disponibilidade do Azure e atualizar domínios.
    
- Tamanhos de máquinas virtuais. 
    
- Ponto de extremidade com balanceamento de carga. 
    
- Pontos de extremidade externos para acesso público, se for preferível. 
    
- Ambiente de recuperação de desastres. 
    
#### <a name="on-premises"></a>Local

Projetar o ambiente do SharePoint em um ambiente local existente: 
  
- Topologia de farm do SharePoint e arquitetura lógica. 
    
- Hardware do servidor. 
    
- Ambiente virtual, se usado. 
    
- Balanceamento de carga. 
    
- Integração com o AD DS e o DNS. 
    
- Ambiente de recuperação de desastres. 
    
### <a name="it-pro-responsibilities"></a>Responsabilidades de profissionais de ti

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

- Verifique se as estações de trabalho de usuário atendem aos pré-requisitos de cliente do Office 365. 
    
- Implementar o plano de integração de diretórios. 
    
- Planejar e implementar registros DNS internos e externos e roteamento. 
    
- Configure o proxy ou firewall para os requisitos de URL e endereço IP do Office 365. 
    
- Criar e atribuir permissões a conjuntos de sites. 
    
- Implementar personalizações, soluções e aplicativos para o SharePoint Online. 
    
- Monitorar a disponibilidade da rede e identificar possíveis afunilamentos. 
    
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

Além das tarefas para os ambientes do Office 365 e local: 
  
- Configure o dispositivo de servidor proxy, se necessário. 
    
- Configure a infraestrutura de gerenciamento de identidade híbrida: autenticação de SSO e servidor para servidor entre os dois ambientes. 
    
- Configure a integração dos recursos escolhidos: Search, BCS, Duet Enterprise online. 
    
#### <a name="azure"></a>Azure

Implantar e gerenciar o ambiente do Azure e do SharePoint: 
  
- Implementar e gerenciar o ambiente de rede do Azure. 
    
- Implantar o ambiente do SharePoint. 
    
- Atualizar servidores de farm do SharePoint. 
    
- Adicionar ou desligar máquinas virtuais conforme necessário com base na utilização do farm. 
    
- Aumentar ou diminuir tamanhos de máquina virtual, conforme necessário. 
    
- Faça backup do ambiente do SharePoint. 
    
- Implementar o ambiente de recuperação de desastres e o protocolo. 
    
#### <a name="on-premises"></a>Local

Implantar e gerenciar o ambiente local do SharePoint: 
  
- Provisionar servidores. 
    
- Implantar o ambiente do SharePoint. 
    
- Atualizar servidores de farm do SharePoint. 
    
- Adicione ou remova servidores de farm conforme necessário com base na utilização do farm. 
    
- Faça backup do ambiente do SharePoint. 
    
- Implementar o ambiente de recuperação de desastres e o protocolo. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Três cargas de trabalho típicas para mover para o Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 mais componentes de diretório no Azure

Implantar os componentes de integração de diretório do Office 365 no Azure é mais rápido porque pode implantar máquinas virtuais sob demanda. 
  
#### <a name="directory-synchronization-server-only"></a>Somente servidor de sincronização de diretório

Em vez de implantar o servidor de sincronização de diretório de 64 bits no seu ambiente local, Provisione uma máquina virtual no Azure. 
  
O diagrama a seguir mostra o SharePoint Online com um locatário do Azure Active Directory, que sincroniza nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Sincronização de diretórios e AD FS

Essa opção permite que você ofereça suporte a identidades federadas do Office 365 (SSO) sem adicionar hardware à sua infraestrutura local. Também fornece resiliência se o ambiente do Active Directory local não estiver disponível. 
  
- Os componentes de integração de diretórios residem no Azure. 
    
- O AD FS é publicado na Internet por meio de proxies do AD FS no Azure. 
    
- O tráfego de autenticação do cliente, para usuários que estão se conectando de qualquer local, é tratado por servidores e proxies do AD FS implantados no Azure. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Site voltado para o público e o Azure AD para autenticação de clientes

Aproveite a capacidade de expansão fácil para a demanda, colocando seu site na Internet no Azure. Use o Azure AD para armazenar contas de cliente. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Vantagens do Azure para sites da Internet

- Pague apenas os recursos necessários, dimensionando o número de máquinas virtuais com base na utilização do farm. 
    
- Adicione relatórios detalhados e análises da Web. 
    
- Concentre-se no desenvolvimento de um ótimo site, em vez de criar uma infraestrutura. 
    
#### <a name="azure-ad"></a>Azure AD

O Azure AD fornece recursos de gerenciamento de identidades e controle de acesso para serviços em nuvem. Os recursos incluem um repositório baseado em nuvem para dados de diretório e um conjunto principal de serviços de identidade, incluindo processos de logon do usuário, serviços de autenticação e AD FS. Os serviços de identidade que estão incluídos no Azure AD se integram facilmente às implantações do Active Directory local e dão suporte completo a provedores de identidade de terceiros. 
  
O diagrama a seguir mostra a configuração de zonas e autenticação importantes para sites voltados para a Internet. O diagrama mostra o locatário do Azure Active Directory, que contém um farm do SharePoint no Azure com duas zonas: 
  
- Uma zona da Internet que interage com visitantes anônimos e autenticados e clientes fora da rede 
    
- Uma zona padrão que contém NTLM para rastreamento e autenticação do Windows que interage com sua implantação local do Active Directory em um túnel VPN. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Farm local mais recuperação de desastre no Azure

Escolha uma opção de recuperação de desastres que corresponda aos seus requisitos de negócios. O Azure fornece opções de nível de entrada para empresas que são introdução à recuperação de desastres e opções avançadas para empresas com requisitos de alta resiliência. 
  
#### <a name="cold-standby"></a>Espera Cold

- O farm está totalmente construído, mas as máquinas virtuais são interrompidas. (Você está pagando apenas quando estão executando!) 
    
- A manutenção do ambiente inclui o início das máquinas virtuais de hora para hora, aplicação de patch, atualização e verificação do ambiente. 
    
- Inicie o ambiente completo em caso de desastre. 
    
#### <a name="warm-standby"></a>Espera passiva

- Isso inclui um pequeno farm que é provisionado e em execução. 
    
- O farm pode servir imediatamente aos usuários em caso de failover. 
    
- Expanda o farm rapidamente para atender à base completa do usuário. 
    
#### <a name="hot-standby"></a>Espera ativa

Um farm de tamanho completo é provisionado e executado no modo de espera. 
  
O diagrama a seguir mostra um farm local interagindo com o ambiente de recuperação de desastres do SharePoint no Azure. Os bancos de dados locais usam o envio de logs do SQL Server sobre o túnel VPN para acessar o ambiente de recuperação de desastres do SharePoint, que inclui dois servidores de banco de dados SQL que contêm os bancos de dados do SharePoint, dois servidores Web front-end e dois SharePoint Servidores de aplicativos. 
  

