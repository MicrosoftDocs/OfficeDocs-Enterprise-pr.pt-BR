---
title: Diagrama acessível – opções da plataforma Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
f1.keywords:
- NOCSH
description: Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Lync 2013, disponível em diagramas técnicos.
ms.openlocfilehash: ff03899a57ff7fbd902cd3cacfc2005d27595c55
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844632"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>Diagrama acessível – opções da plataforma Microsoft Lync 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Lync 2013, disponível em [diagramas técnicos](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Este cartaz descreve quais responsáveis pelas decisões de negócios (BDMs) e arquitetos precisam saber sobre as implantações do Lync Online (Office 365) e do Lync Server e incluem:
  
- Uma comparação de quatro opções de implantação diferentes: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server e Lync Server hospedado pelo provedor. 
    
- Dois cenários de exemplo para implantar o Lync 2013.
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Comparação de quatro implantações diferentes para a plataforma Lync 2013

A comparação fornece informações sobre cada opção de implantação nas seguintes áreas: 
  
- Uma visão geral dos diferentes recursos de implantação
    
- Benefícios da implementação de cada opção de implantação
    
- Requisitos de licença
    
- Tarefas de arquitetura necessárias
    
- Responsabilidades de profissionais de ti para implementar cada opção de implantação
    
### <a name="overview"></a>Visão Geral

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Você obtém eficiência e otimiza o custo com planos multilocatário do Office 365.
  
O diagrama a seguir mostra o Lync Online com um locatário do Azure Active Directory, que sincroniza nomes de conta e senhas entre o ambiente do AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory. 
  
Descrição dos recursos e funcionalidade:
  
- Software como serviço (SaaS).
    
- Conjunto de recursos avançado que está sempre atualizado.
    
- O inclui um locatário do Azure Active Directory para contas online, que podem ser usadas com outros aplicativos. 
    
- A integração de diretórios inclui a sincronização de nomes de conta e senhas entre o ambiente do AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory.
    
- Se o logon único (SSO) for um requisito, o AD FS (serviços de Federação do Active Directory) deverá ser implementado. 
    
- A comunicação do cliente pela Internet é criptografada e autenticada.
    
- Equipamento de telefone herdado, rede telefônica pública comutada (PSTN), a conectividade está disponível por meio de provedores de terceiros.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

Você pode combinar os benefícios do Office 365 com uma implantação local do Lync 2013.
  
O diagrama a seguir mostra o Office 365 com o Lync Online em que alguns usuários estão hospedados no local e alguns usuários estão hospedados online. Um servidor de borda implantado no local também é mostrado.
  
Descrição dos recursos e funcionalidade:
  
- Alguns usuários estão hospedados no local e alguns usuários estão hospedados online, mas os usuários compartilham o mesmo domínio SIP (como contoso.com).
    
- Aproveite a infraestrutura existente do Lync Server 2013, incluindo as conexões com o PSTN.
    
- Adicione novos usuários do Lync Online facilmente quando eles não exigirem PSTN.
    
- Migre do Lync local para o Lync Online com o passar do tempo, no seu cronograma.
    
- Integre-se com outros aplicativos do Office 365, incluindo o Exchange Online e o SharePoint Online.
    
#### <a name="lync-server"></a>Lync Server

Nesta implantação, você tem todos os itens. O diagrama a seguir mostra uma infraestrutura do Lync Server com um ambiente do AD DS (serviços de domínio Active Directory) local onde os usuários estão hospedados no local.
  
Descrição dos recursos e funcionalidade:
  
- Planejamento de capacidade e dimensionamento.
    
- Aquisição e configuração do servidor.
    
- Instalação.
    
- Expansão, aplicação de patch e operações.
    
- Backup de dados.
    
- Manutenção de failover e recuperação de desastre.
    
- Conexão da infraestrutura do Lync Server 2013 à PSTN.
    
- Integração com equipamento de telefone existente, como PBXs (Private Branch eXchanges).
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado pelo provedor

Nesta implantação, o provedor é proprietário de tudo. O diagrama a seguir mostra a rede de um provedor, incluindo seus servidores e equipamentos com uma conexão a um ambiente local.
  
Descrição dos recursos e funcionalidade:
  
- Planejamento de capacidade e dimensionamento.
    
- Aquisição e configuração do servidor.
    
- Instalação.
    
- Expansão, aplicação de patch e operações.
    
- Backup de dados.
    
- Manutenção de failover e recuperação de desastre.
    
- Integração com equipamento de telefone existente, como PBXs (Private Branch eXchanges).
    
- Além disso, o provedor pode:
    
  - Instale seus servidores e equipamentos em sua própria rede com uma conexão com sua local (linha sólida).
    
  - Instale seus servidores no local (linha pontilhada).
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Benefícios da implementação de cada opção de implantação

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Sem carga operacional de servidores locais ou software de servidor.
    
- Recursos de comunicação do Lync Server 2013 como um serviço baseado em nuvem.
    
- Presença do Lync, mensagens instantâneas, chamadas de áudio e vídeo, reuniões online avançadas e recursos de Webconferência abrangentes.
    
- Usado com organizações geograficamente dispersas ou com funcionários móveis primariamente.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

- Use o Lync Online para usuários remotos e integração com parceiros de negócios.
    
- Facilite uma migração do Lync local para o Lync Online.
    
- Dar suporte a sites remotos sem usar um aparelho de filial do escritório.
    
- Facilidade de adicionar o suporte do Lync para novas aquisições de negócios.
    
#### <a name="lync-server"></a>Lync Server

- Soluções de nuvem privada.
    
- Soluções altamente personalizadas.
    
- Soluções herdadas com componentes de terceiros que dependem de hardware e software que não são compatíveis com o Lync Online.
    
- Restrições de privacidade que impedem a sincronização de contas do AD DS com o Office 365.
    
- Organizações que desejam controlar toda a plataforma e a solução.
    
- Substituição de PBX pelo Lync Enterprise Voice.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado pelo provedor

- Organizações que desejam a funcionalidade do Lync Server, mas que desejam terceirizar sua implantação e manutenção.
    
- Soluções baseadas em provedor.
    
- Soluções altamente personalizadas.
    
- Soluções herdadas com componentes de terceiros que dependem de hardware e software que não são compatíveis com o Lync Online.
    
- Substituição de PBX pelo Lync Enterprise Voice.
    
### <a name="license-requirements"></a>Requisitos de licença

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Modelo de assinatura.
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

- Office 365 – modelo de assinatura. Nenhuma licença adicional necessária. 
    
- Local – todas as licenças locais são aplicadas. 
    
#### <a name="lync-server"></a>Lync Server

- Sistema operacional do servidor
    
- SQL Server
    
- Licença do Lync 2013 Server
    
- Licença de acesso para cliente do Lync 2013
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado pelo provedor

Os custos são baseados no acordo com o seu provedor de soluções do Lync.
  
### <a name="architecture-tasks"></a>Tarefas de arquitetura

Esta seção lista as tarefas arquitetônicas de cada opção de implantação.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Planejar e projetar a sincronização de diretórios.
    
- Garantir a capacidade e a disponibilidade da rede por meio de firewalls, servidores de proxy, gateways e entre links de WAN.
    
- Adquirir certificados SSL de terceiros para oferecer segurança corporativa para ofertas de serviços do Office 365.
    
- Decida se você deseja se conectar ao Office 365 com o protocolo IPv6 (Internet Protocol version 6).
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

Além das tarefas para os ambientes do Office 365 e local:
  
- Determine quanta integração de recursos você deseja usar com as versões local e online do Exchange Server e do SharePoint.
    
- Se necessário, determine qual dispositivo de servidor proxy será usado para solicitações do Office 365.
    
#### <a name="lync-server"></a>Lync Server

Projetar o ambiente do Lync em um ambiente local existente:
  
- Topologia do Lync para escritórios centrais e filiais.
    
- Hardware de servidor, incluindo virtualização.
    
- Integração com os serviços de domínio do Active Directory (AD DS) e o DNS.
    
- Balanceamento de carga para pools do Lync Server.
    
- Failover e recuperação de desastre.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado pelo provedor

- Para uma instalação baseada em nuvem, determine a conexão com a rede do provedor de serviços.
    
- Para uma instalação local, determine o posicionamento dos servidores Lync do provedor em sua rede.
    
- Para os dois tipos, determine a integração com o AD DS e o equipamento de PBX.
    
### <a name="it-pro-responsibilities"></a>Responsabilidades de profissionais de ti

Esta seção lista as responsabilidades de profissionais de ti para cada opção de implantação.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Implantar e gerenciar o Lync Online (Office 365):
  
- Implementar o plano de sincronização de diretórios.
    
- Planejar e implementar registros DNS internos e externos e roteamento.
    
- Configure seu proxy ou firewall para os requisitos de URL e endereço IP do Office 365.
    
- Administrar as contas de usuário e as configurações do Lync Online.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

Além das tarefas para os ambientes do Office 365 e local:
  
- Configure o dispositivo de servidor proxy, se necessário.
    
- Configure a integração de recursos com as versões local e online do Exchange Server e do SharePoint.
    
#### <a name="lync-server"></a>Lync Server

Implantar e gerenciar o Lync Server em um ambiente local:
  
- Provisionar os servidores.
    
- Implantar a topologia do Lync.
    
- Atualize os servidores do Lync.
    
- Adicionar ou remover servidores de topologia conforme necessário com base na utilização.
    
- Implementar o ambiente de failover e recuperação de desastres.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado pelo provedor

Trabalhe com o provedor para:
  
- Integre o Lync Server à sua rede.
    
- Integre o Lync Server com outros produtos da Microsoft ou soluções personalizadas.
    
- Monitorar a adesão ao contrato de nível de serviço (SLA) do provedor.
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Dois cenários de exemplo para a implantação do Lync 2013

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Componentes de sincronização de diretório no Microsoft Azure

A implantação de componentes de sincronização de diretório do Office 365 no Azure é mais rápida devido à capacidade de implantar máquinas virtuais sob demanda.
  
O diagrama a seguir mostra o Lync Online com um locatário do Azure Active Directory, que sincroniza nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.
  
 **Somente servidor de sincronização de diretório**. Em vez de implantar o servidor de sincronização de diretório de 64 bits no seu ambiente local, você provisiona uma máquina virtual no Azure pela Internet.
  
 **Sincronização de diretórios + AD FS**. Essa opção permite que você ofereça suporte a identidades federadas do Office 365 (SSO) sem adicionar hardware à sua infraestrutura local. Também fornece resiliência se o ambiente do Active Directory local não estiver disponível. Os recursos dessa opção incluem:
  
- Os componentes de integração de diretório são executados como máquinas virtuais do Azure.
    
- O AD FS é publicado na Internet através de proxies do AD FS executados como máquinas virtuais do Azure.
    
- O tráfego de autenticação de cliente, para usuários que estão se conectando de qualquer local, é tratado pelos servidores e proxies do AD FS implantados como máquinas virtuais do Azure.
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Integração do Lync com o Exchange e o SharePoint no Office 365

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server com Exchange Online e SharePoint Online

O diagrama a seguir mostra o Office 365 com o Exchange Online e o SharePoint Online conectados a um farm local do Lync Server 2013.
  
As vantagens dessa implantação permitem:
  
- Use o conjunto de recursos completo do Lync Server 2013.
    
- Aproveite o equipamento de telefone local existente, como PBXs.
    
- Use o Exchange Online para email, descarregando o ônus de servidores de email locais e armazenamento.
    
- Use o SharePoint Online para colaboração, carregando o ônus de manter os servidores locais do SharePoint.
    
- Use o Lync, o Exchange e os recursos integrados do SharePoint, incluindo Unificação de mensagens (UM) no Office 365.
    
#### <a name="exchange-server-with-lync-online"></a>Servidor Exchange com Lync Online

O diagrama a seguir mostra o Office 365 com Lync Online conectado a um farm local do Exchange Server.
  
As vantagens dessa implantação permitem:
  
- Aproveite a infraestrutura existente do Exchange.
    
- Use o Lync Online para recursos de presença, mensagens instantâneas e conferência.
    

