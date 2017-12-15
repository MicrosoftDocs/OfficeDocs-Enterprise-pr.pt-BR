---
title: "Diagrama acessível - opções de plataforma do Microsoft SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: "Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft SharePoint 2013."
ms.openlocfilehash: 9cd282cc723376f85fe2cbc5a439ee24fd2ab883
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Diagrama acessível - opções de plataforma do Microsoft SharePoint 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft SharePoint 2013.
  
O que arquitetos e business decision tomadores de precisam saber sobre o Office 365, Microsoft Azure e implantações em instalações. 
  
Este cartaz tem duas seções: 
  
- Uma comparação dos quatro diferentes implantações do SharePoint 2013: SharePoint no Office 365, um híbrido do Office 365 com uma implantação local do SharePoint 2013, Windows Azure e uma implantação local do SharePoint 2013. 
    
- Uma descrição das três cargas de trabalho típicas para mover para o Windows Azure. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Comparação entre quatro diferentes implantações para a plataforma SharePoint 2013

Comparação fornece informações sobre cada opção de implantação relacionada às seguintes áreas: 
  
- Uma visão geral dos recursos de implantação diferentes 
    
- O que é melhor para cada tipo de implantação 
    
- Requisitos de licença 
    
- Tarefas de arquitetura necessárias para implementar 
    
- IT profissionais responsabilidades da implementação 
    
### <a name="overview"></a>Visão geral

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

Ganho de eficiência e otimizar o custo com vários locatários planos do Office 365. 
  
O diagrama acompanha mostra o SharePoint Online com um locatário do Azure Active Directory, o que sincroniza os nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory. 
  
Descrição de recursos: 
  
- Software como um serviço (SaaS). 
    
- Conjunto de recursos avançados sempre é atualizado. 
    
- Inclui um locatário do Azure Active Directory (pode ser usado com outros aplicativos). 
    
- Integração de diretórios inclui sincronizando nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory. 
    
- Se o logon único (SSO) é um requisito, os serviços de Federação do Active Directory (AD FS) pode ser implementados. 
    
- Comunicação do cliente pela Internet por meio de acesso criptografado e autenticado (porta 443). 
    
- Migração de dados está limitada a que pode ser carregado pela Internet. 
    
- Personalizações: Aplicativos para Office, SharePoint e o SharePoint Designer 2013. 
    
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

Combine os benefícios do Office 365 com uma implantação local do SharePoint 2013. 
  
O diagrama acompanha mostra o Office 365 com o SharePoint Online usando os serviços corporativos de conectividade (BCS) para conectar a um farm do SharePoint Server 2013 local. 
  
Escolha qual dos seguintes recursos para integrar: 
  
Pesquisa do SharePoint 
  
- Os usuários podem ver resultados de pesquisa de ambos os ambientes. 
    
- Usuários da extranet podem fazer logon com uma conta do Active Directory local e usar toda a funcionalidade híbrida disponível remotamente. 
    
BCS
  
Do SharePoint Online: Os usuários podem realizar leitura e operações de gravação. O serviço BCS conecta-se a um farm do SharePoint Server 2013 local. O serviço BCS configurado nos agentes de farm local a conexão aos pontos de extremidade de serviço OData local. 
  
Duet Enterprise Online 
  
Do SharePoint Online, os usuários podem executar leitura e gravação operações em relação a um sistema SAP no local. 
  
#### <a name="azure"></a>Azure

Tirar proveito da nuvem, mantendo o controle total da plataforma e recursos. 
  
O diagrama acompanha mostra Azure, que contém dois serviços de nuvem, um farm do SharePoint 2013 e Windows Server Active Directory com o DNS, conectando-se aos usuários através da Internet ou a conexão com o Active Directory no local por meio de túnel VPN. 
  
Os recursos incluem: 
  
-  Windows Azure é uma plataforma que fornece os serviços de infraestrutura e aplicativos necessários para hospedar um farm do SharePoint 2013.
    
- Serviços de infraestrutura. 
    
- Plataforma de nuvem nativo recomendada para SQL Server e SharePoint. 
    
- Recursos de computação estão disponíveis quase imediatamente com nenhum compromisso. 
    
- Concentre-se nos aplicativos, em vez de data centers e infra-estrutura. 
    
- Ambientes de desenvolvimento e teste e econômica. 
    
- Soluções do SharePoint podem ser acessível pela Internet ou acessível somente a partir de um ambiente corporativo por meio de um túnel VPN-to-site. 
    
- Personalizações não são limitadas. 
    
#### <a name="on-premises"></a>No local

Você é proprietário tudo. 
  
O diagrama acompanha mostra um ambiente no local com servidores web, servidores de aplicativos e do Active Directory se comunicam com todos os bancos de dados e servidores de aplicativos dedicado para pesquisa. 
  
Os recursos incluem: 
  
- Planejamento de capacidade e dimensionamento. 
    
- Aquisição de servidor e a instalação. 
    
- Implantação. 
    
- Dimensionamento, aplicando o patch e operações. 
    
- Fazendo backup de dados. 
    
- Mantendo um ambiente de recuperação de desastres. 
    
- Personalizações não são limitadas. 
    
### <a name="deployment-type-is-best-for---"></a>Tipo de implantação é melhor para...

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

- Proteja a colaboração e compartilhamento externo. (Recurso exclusivo!) 
    
- Intranet — Colaboração interna, Meus Sites e sites de equipe. 
    
- Armazenamento de documentos e controle de versão na nuvem. 
    
- Site público de Basic. 
    
Recursos adicionais com planos de assinatura dedicados do Office 365: 
  
- Equipamento de datacenter da Microsoft que é dedicado à sua organização e não é compartilhado com qualquer outra organização. 
    
- Ambiente de cada cliente reside em uma rede fisicamente separada. 
    
- Comunicação do cliente em uma VPN protegido por IPSec ou conexão privada de propriedade do cliente. Autenticação de dois fatores é opcional. 
    
- Suporte de ITAR planos. 
    
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

- Use o Office 365 para compartilhamento e colaboração em vez de configurar um ambiente de extranet externo. 
    
- Mova Meus Sites (OneDrive for Business) para a nuvem facilitam para os usuários acessem seus arquivos remotamente. 
    
- Inicie novos sites de equipe no Office 365. 
    
- Integre um site do Office 365 com o ambiente do SharePoint de BCS no local. 
    
#### <a name="azure"></a>Azure

- SharePoint para Sites da Internet — pública enfrentados pelos sites. Beneficie-se do Azure AD para contas de cliente e de autenticação. 
    
- Desenvolvedor, teste e preparo de ambientes — rapidamente provisionar e desprovisionamento ambientes inteiros. 
    
- Aplicativos híbridos — aplicativos que abrangem o seu data center e a nuvem. 
    
- Ambiente de recuperação de desastre — rapidamente a recuperação de desastres. Preste apenas para uso. 
    
- Farms que exigem a profundidade de relatórios ou auditoria. 
    
- Análise da Web. 
    
- Criptografia de dados em repouso (dados criptografados nos bancos de dados SQL). 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Criptografia de dados em repouso (dados criptografados nos bancos de dados SQL)

- Farms de país (quando os dados é necessário para residem em uma jurisdição). 
    
- Soluções de BI complexas que devem residir fechar aos dados de BI. 
    
- Soluções de nuvem privada. 
    
- Soluções altamente personalizadas. 
    
- Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados nos serviços de infraestrutura do Windows Azure. 
    
- Restrições de privacidade que evitam a sincronização de contas do Active Directory com o Windows Azure Active Directory (um requisito para o Office 365). 
    
- Organizações que preferem o controle da plataforma inteira and solution. 
    
### <a name="license-requirements"></a>Requisitos de licença

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

Modelo de assinatura. Não há licenças adicionais necessárias. 
  
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

- Office 365 — Modelo de assinatura. Não há licenças adicionais necessárias. 
    
- Local — Se aplicam todas as licenças de local. 
    
#### <a name="azure"></a>Azure

-  Assinatura do Windows Azure (inclui o sistema operacional do servidor)
    
- SQL Server 
    
- Licença de servidor do SharePoint 2013 
    
- Licença de acesso para cliente do SharePoint 2013 
    
#### <a name="on-premises"></a>No local

- Sistema operacional do servidor 
    
- SQL Server 
    
- Licença de servidor do SharePoint 2013 
    
- Licença de acesso para cliente do SharePoint 2013 
    
### <a name="architecture-tasks"></a>Tarefas de arquitetura

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

- Design e plano de integração de diretório. Duas opções. Qualquer uma das opções podem ser implantados no local ou no Windows Azure: sincronização de senha (requer um servidor de 64 bits). SSO (requer o AD FS e vários servidores). 
    
- Certifique-se de capacidade de rede e a disponibilidade por meio de firewalls, servidores proxy, gateways e em links de WAN. 
    
- Adquira certificados SSL de terceiros para fornecer segurança da empresa para ofertas de serviços do Office 365. 
    
- O nome do locatário de planejar e projetar a arquitetura do conjunto de sites e um governança. 
    
- Planeje personalizações, soluções e aplicativos para o SharePoint Online. 
    
- Decida se deseja se conectar ao Office 365 usando o Internet Protocol 6 (IPv6). Isso não é comum. 
    
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

Além das tarefas para o Office 365 e o local de ambientes: 
  
- Determine quanto integração do recurso desejado e escolha a topologia híbrida. Consulte este cartaz de modelo: qual topologia híbrida devo usar? 
    
- Se for necessário, determine qual dispositivo do servidor de proxy será usado. 
    
#### <a name="azure"></a>Azure

Projete o ambiente de rede Windows Azure: 
  
- Rede virtual dentro do Azure, incluindo sub-redes. 
    
- Ambiente de domínio e integração com servidores locais. 
    
- Endereços IP e DNS. 
    
- Afinidade de grupos e contas de armazenamento. 
    
Projete o ambiente do SharePoint no Windows Azure: 
  
- Topologia de farm do SharePoint e arquitetura lógica. 
    
-  Conjuntos de disponibilidade do Azure e domínios de atualização.
    
- Tamanhos de máquinas virtuais. 
    
- Ponto de extremidade com balanceamento de carga. 
    
- Pontos de extremidade externos para acesso público, se o que é preferível. 
    
- Ambiente de recuperação de desastres. 
    
#### <a name="on-premises"></a>No local

Projete o ambiente do SharePoint em um ambiente local existente: 
  
- Topologia de farm do SharePoint e arquitetura lógica. 
    
- Hardware de servidor. 
    
- Ambiente virtual, se usado. 
    
- Balanceamento de carga. 
    
- Integração com o AD DS e DNS. 
    
- Ambiente de recuperação de desastres. 
    
### <a name="it-pro-responsibilities"></a>IT profissionais responsabilidades

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 no Office 365

- Certifique-se de estações de trabalho do usuário atender aos pré-requisitos de cliente do Office 365. 
    
- Implemente o plano de integração de diretório. 
    
- Planejar e implementar os registros DNS internos e externos e roteamento. 
    
- Configure o proxy ou firewall para o endereço IP do Office 365 e requisitos de URL. 
    
- Criar e atribuir permissões aos conjuntos de sites. 
    
- Implementar personalizações, soluções e aplicativos para o SharePoint Online. 
    
- Monitorar a disponibilidade da rede e identificar afunilamentos possíveis. 
    
#### <a name="hybrid-with-office-365"></a>Híbrido com o Office 365

Além das tarefas para o Office 365 e o local de ambientes: 
  
- Configure o dispositivo de servidor proxy, se necessário. 
    
- Configurar a infraestrutura de gerenciamento de identidade híbrida: SSO e autenticação de servidor-para-servidor entre os dois ambientes. 
    
- Configurar a integração dos recursos escolhidos: pesquisa, o BCS, Duet Enterprise Online. 
    
#### <a name="azure"></a>Azure

Implantar e gerenciar o ambiente do Windows Azure e o SharePoint: 
  
- Implementar e gerenciar o ambiente de rede do Azure. 
    
- Implante o ambiente do SharePoint. 
    
- Atualize servidores de farm do SharePoint. 
    
- Adicionar ou desligar máquinas virtuais conforme necessário com base na utilização de farm. 
    
- Aumentar ou diminuir os tamanhos de máquina virtual, conforme necessário. 
    
- Faça backup do ambiente do SharePoint. 
    
- Implemente o ambiente de recuperação de desastres e o protocolo. 
    
#### <a name="on-premises"></a>No local

Implantar e gerenciar o SharePoint no ambiente local: 
  
- Servidores de provisionamento. 
    
- Implante o ambiente do SharePoint. 
    
- Atualize servidores de farm do SharePoint. 
    
- Adicionar ou remover servidores do farm conforme necessário com base na utilização de farm. 
    
- Faça backup do ambiente do SharePoint. 
    
- Implemente o ambiente de recuperação de desastres e o protocolo. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Três cargas de trabalho típicas para mover para o Windows Azure

### <a name="office-365-plus-directory-components-in-azure"></a>O Office 365 mais componentes de diretório no Windows Azure

Implantar o Office 365 componentes de integração de diretório no Windows Azure é mais rápido porque ele pode implantar máquinas virtuais sob demanda. 
  
#### <a name="directory-synchronization-server-only"></a>Somente servidor de sincronização de diretório

Em vez de implantar o servidor de sincronização de diretório de 64 bits em seu ambiente local, em vez disso provisionar uma máquina virtual no Windows Azure. 
  
O diagrama acompanha mostra o SharePoint Online com um locatário do Azure Active Directory, o que sincroniza os nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Sincronização de diretórios plus do AD FS

Essa opção permite que você ofereça suporte a identidades do Office 365 federado (SSO) sem adicionar hardware à infraestrutura local. Ele também fornece resiliência se o ambiente do Active Directory local não está disponível. 
  
- Componentes de integração de diretório residem no Windows Azure. 
    
- O AD FS é publicado na Internet por meio de proxies do AD FS no Windows Azure. 
    
- Tráfego de autenticação de cliente, para usuários que estão se conectando de qualquer local, é tratado por servidores AD FS e proxies que são implantados no Azure. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Site de Internet público e o Azure AD para autenticação de cliente

Aproveite a capacidade de expansão facilmente a demanda colocando em seu site da Internet no Windows Azure. Use o Azure AD para armazenar contas de cliente. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Vantagens do Azure para sites da Internet

- Preste apenas para os recursos que necessários dimensionando o número de máquinas virtuais com base na utilização de farm. 
    
- Adicione profundidade a emissão de relatórios e do web analytics. 
    
- Foco no desenvolvimento de um grande site, em vez da criação de infra-estrutura. 
    
#### <a name="azure-ad"></a>AD do Azure

Azure AD fornece recursos de controle acesso e o gerenciamento de identidade para serviços de nuvem. Os recursos incluem um repositório baseado em nuvem para dados de diretório e um conjunto básico de serviços de identidade, incluindo processos de logon do usuário, serviços de autenticação e AD FS. Os serviços de identidade que estão incluídos no Windows Azure AD integram facilmente suas implantações do Active Directory local e suportam totalmente os provedores de identidade de terceiros. 
  
O diagrama acompanha mostra a configuração de zonas e autenticação que é importante para sites na Internet. O diagrama mostra o Azure Active Directory inquilino, que contém um Farm do SharePoint no Azure com duas zonas: 
  
- Uma zona da Internet que interage com visitantes anônimos e autenticados e clientes fora da rede 
    
- Uma zona padrão que contém o NTLM para autenticação do Windows que interage com sua implantação do Active Directory local um túnel VPN e de rastreamento. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Farm local além de recuperação de desastres no Azure

Escolha uma opção de recuperação de desastres que atenda às suas necessidades de negócios. Azure fornece opções de nível básica para empresas de Introdução à recuperação de desastres e opções avançadas para empresas de grande porte com requisitos de alta resiliência. 
  
#### <a name="cold-standby"></a>Espera a frio

- O farm totalmente é criado, mas as máquinas virtuais são interrompidas. (Você está pagando somente quando eles estão executando!) 
    
- Manter o ambiente inclui começar as máquinas virtuais do tempo em tempos, patches, atualizando e verificando o ambiente. 
    
- Inicie o ambiente completo em caso de desastre. 
    
#### <a name="warm-standby"></a>Espera passiva

- Isso inclui um pequeno farm é provisionado e em execução. 
    
- O farm imediatamente pode atender a usuários em caso de um failover. 
    
- Dimensionar o farm rapidamente para atender a base completos do usuário. 
    
#### <a name="hot-standby"></a>Espera ativa

Um farm de tamanho totalmente é provisionado e executado em espera. 
  
O diagrama acompanha mostra um farm local interação com o ambiente de recuperação de desastres do SharePoint no Azure. Usam o os bancos de dados local envio de Log do SQL Server no túnel VPN para acessar o ambiente de recuperação de desastres do SharePoint, que inclui dois servidores de banco de dados SQL que contêm os bancos de dados do SharePoint, dois servidores Web Front-End e dois SharePoint Servidores de aplicativos. 
  

