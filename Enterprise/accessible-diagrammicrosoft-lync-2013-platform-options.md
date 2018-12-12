---
title: Diagrama acessível - opções de plataforma do Microsoft Lync 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Lync 2013, que está disponível em diagramas técnicos.
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504084"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>Diagrama acessível - opções de plataforma do Microsoft Lync 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Lync 2013, que está disponível em [Diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Este cartaz descreve o que arquitetos e business decision tomadores de precisam saber sobre o Lync Online (Office 365) e as implantações do Lync Server e inclui:
  
- Uma comparação das quatro opções de implantação diferentes: Lync Online (Office 365), Lync Online/servidor híbrido, Lync Server e Provider-Hosted Lync Server. 
    
- Dois cenários de exemplo de implantação do Lync 2013.
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Comparação entre quatro diferentes implantações para a plataforma do Lync 2013

Comparação fornece informações sobre cada opção de implantação nas seguintes áreas: 
  
- Uma visão geral dos recursos de implantação diferentes
    
- Benefícios da implementação de cada opção de implantação
    
- Requisitos de licenciamento
    
- Tarefas necessárias de arquiteturais
    
- Responsabilidades do IT Pro para implementar cada opção de implantação
    
### <a name="overview"></a>Visão geral

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Ganho de eficiência e otimizar o custo com vários locatários planos do Office 365.
  
O diagrama acompanha mostra Lync Online com um locatário do Azure Active Directory, o que sincroniza os nomes de conta e senhas entre o ambiente de serviços de domínio Active Directory (AD DS) no local e o locatário do Azure Active Directory. 
  
Descrição dos recursos e funcionalidades:
  
- Software como um serviço (SaaS).
    
- Avançado conjunto que sempre está atualizado de recursos.
    
- Inclui um locatário do Azure Active Directory para contas online, que pode ser usado com outros aplicativos. 
    
- Integração de diretórios inclui sincronizando nomes de conta e senhas entre o ambiente de serviços de domínio Active Directory (AD DS) no local e o locatário do Azure Active Directory.
    
- Se o logon único (SSO) é um requisito, os serviços de Federação do Active Directory (AD FS) devem ser implementados. 
    
- Comunicação do cliente pela Internet é criptografada e autenticada.
    
- Equipamento de telefone herdado, pública comutada (PSTN) rede telefônica, conectividade está disponível por meio de provedores de terceiros.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

Você pode combinar os benefícios do Office 365 com uma implantação local do Lync 2013.
  
O diagrama acompanha mostra o Office 365 com o Lync Online onde alguns usuários estão hospedados no local e alguns usuários hospedados online. Um servidor de borda é implantados no local também é mostrado.
  
Descrição dos recursos e funcionalidades:
  
- Alguns usuários hospedados no local e alguns usuários hospedados online, mas os usuários compartilhem o mesmo domínio SIP (por exemplo, contoso.com).
    
- Aproveite sua infra-estrutura existente do Lync Server 2013, incluindo as conexões para o PSTN.
    
- Adicione novos usuários do Lync Online facilmente quando eles não exigem PSTN.
    
- Migre do Lync local para o Lync Online ao longo do tempo, no seu calendário.
    
- Integre com outros aplicativos do Office 365, incluindo o Exchange Online e SharePoint Online.
    
#### <a name="lync-server"></a>Lync Server

Nesta implantação, você é proprietário tudo. O diagrama acompanha mostra uma infra-estrutura do Lync Server com um ambiente de serviços de domínio Active Directory (AD DS) do local onde os usuários são hospedados no local.
  
Descrição dos recursos e funcionalidades:
  
- Planejamento de capacidade e dimensionamento.
    
- Aquisição de servidor e a instalação.
    
- Implantação.
    
- Dimensionamento, aplicando o patch e operações.
    
- Fazendo backup de dados.
    
- Mantendo o failover e recuperação de desastres.
    
- Conectando-se a infraestrutura do Lync Server 2013 para a PSTN.
    
- Integração com o equipamento de telefone existente, como privada de comutação telefônica (PBXs).
    
#### <a name="provider-hosted-lync-server"></a>Hospedado em provedor do Lync Server

Nesta implantação, o seu provedor é proprietário tudo. O diagrama acompanha mostra uma rede provedor incluindo seus servidores e equipamentos com uma conexão para um ambiente local.
  
Descrição dos recursos e funcionalidades:
  
- Planejamento de capacidade e dimensionamento.
    
- Aquisição de servidor e a instalação.
    
- Implantação.
    
- Dimensionamento, aplicando o patch e operações.
    
- Fazendo backup de dados.
    
- Mantendo o failover e recuperação de desastres.
    
- Integração com o equipamento de telefone existente, como privada de comutação telefônica (PBXs).
    
- Além disso, o provedor pode:
    
  - Instale os seus servidores e equipamentos em sua própria rede com uma conexão para o seu local (linha sólida).
    
  - Instale os seus servidores em seu local (linha pontilhada).
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Benefícios da implementação de cada opção de implantação

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Nenhuma carga operacional dos servidores locais ou software de servidor.
    
- Recursos de comunicação do Lync Server 2013, como um serviço baseado em nuvem.
    
- Lync presença, mensagens instantâneas, áudio e vídeo chamar, reuniões online ricas e recursos de webconferência extensiva.
    
- Usada com organizações geograficamente dispersos ou com os funcionários móveis principalmente.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

- Use o Lync Online para usuários remotos e integração com parceiros comerciais.
    
- Facilite uma migração do Lync local para o Lync Online.
    
- Suporte a sites remotos sem usar um aparelho de escritório de filial.
    
- Facilidade de adição de suporte do Lync para novas aquisições de negócios.
    
#### <a name="lync-server"></a>Lync Server

- Soluções de nuvem privada.
    
- Soluções altamente personalizadas.
    
- Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados pelo Lync Online.
    
- Restrições de privacidade que evitam a sincronização de contas do AD DS com o Office 365.
    
- Organizações que desejam controlar a plataforma inteira e a solução.
    
- Substituição de PBX com o Enterprise Voice do Lync.
    
#### <a name="provider-hosted-lync-server"></a>Hospedado em provedor do Lync Server

- Organizações que deseja as funcionalidades do Lync Server, mas quer terceirizar sua implantação e manutenção.
    
- Soluções baseadas no provedor.
    
- Soluções altamente personalizadas.
    
- Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados pelo Lync Online.
    
- Substituição de PBX com o Enterprise Voice do Lync.
    
### <a name="license-requirements"></a>Requisitos de licença

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Modelo de assinatura.
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

- Office 365 — Modelo de assinatura. Não há licenças adicionais necessárias. 
    
- Local — Se aplicam todas as licenças de local. 
    
#### <a name="lync-server"></a>Lync Server

- Sistema operacional do servidor
    
- SQL Server
    
- Licença de servidor do Lync 2013
    
- Licença de acesso de cliente do Lync 2013
    
#### <a name="provider-hosted-lync-server"></a>Hospedado em provedor do Lync Server

Custos se baseiam no contrato com seu provedor de soluções do Lync.
  
### <a name="architecture-tasks"></a>Tarefas de arquitetura

Esta seção lista as tarefas de arquiteturais para cada opção de implantação.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Design e plano de sincronização de diretórios.
    
- Certifique-se de capacidade de rede e a disponibilidade por meio de firewalls, servidores proxy, gateways e em links de WAN.
    
- Adquira certificados SSL de terceiros para fornecer segurança da empresa para ofertas de serviços do Office 365.
    
- Decida se deseja conectar ao Office 365 com protocolo IP versão 6 (IPv6).
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

Além das tarefas para o Office 365 e o local de ambientes:
  
- Determine quanto integração do recurso que você deseja usar com o local e as versões online do Exchange Server e SharePoint.
    
- Se for necessário, determine qual dispositivo do servidor de proxy será usado para solicitações do Office 365.
    
#### <a name="lync-server"></a>Lync Server

Projete o ambiente do Lync em um ambiente local existente:
  
- Topologia do Lync para central e filiais.
    
- Hardware de servidor, incluindo a virtualização.
    
- Integração com serviços de domínio do Active Directory (AD DS) e DNS.
    
- Balanceamento de carga para os pools do Lync server.
    
- Failover e recuperação de desastres.
    
#### <a name="provider-hosted-lync-server"></a>Hospedado em provedor do Lync Server

- Para uma instalação baseada em nuvem, determine a conexão de rede do provedor de serviços.
    
- Para uma instalação local, determine o posicionamento de servidores do Lync do provedor em sua rede.
    
- Para os dois tipos, determine a integração com o AD DS e seu equipamento de PBX.
    
### <a name="it-pro-responsibilities"></a>Responsabilidades do IT Pro

Esta seção lista as responsabilidades profissionais de TI para cada opção de implantação.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Implantar e gerenciar o Lync Online (Office 365):
  
- Implemente o plano de sincronização de diretório.
    
- Planejar e implementar os registros DNS internos e externos e roteamento.
    
- Configure seu proxy ou firewall para o endereço IP do Office 365 e requisitos de URL.
    
- Administre contas de usuário e configurações do Lync Online.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Lync Online/servidor híbrido (domínio dividido)

Além das tarefas para o Office 365 e o local de ambientes:
  
- Configure o dispositivo de servidor proxy, se necessário.
    
- Configure a integração de recursos com o local e versões online do Exchange Server e do SharePoint.
    
#### <a name="lync-server"></a>Lync Server

Implantar e gerenciar o Lync Server em um ambiente local:
  
- Provisione os servidores.
    
- Implante a topologia do Lync.
    
- Atualize servidores do Lync.
    
- Adicionar ou remover servidores de topologia conforme necessário com base na utilização.
    
- Implemente o ambiente de recuperação de desastres e failover.
    
#### <a name="provider-hosted-lync-server"></a>Hospedado em provedor do Lync Server

Trabalhar com o provedor para:
  
- Integre o Lync Server em sua rede.
    
- Integre o Lync Server com outros produtos da Microsoft ou soluções personalizadas.
    
- Monitorar a adesão com um contrato de nível de serviço (SLA) do provedor.
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Dois cenários de exemplo de implantação do Lync 2013

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Componentes de sincronização de diretórios no Microsoft Azure

Implantar o Office 365 componentes de sincronização de diretório no Windows Azure é mais rápido devido a capacidade de implantar máquinas virtuais sob demanda.
  
O diagrama acompanha mostra Lync Online com um locatário do Azure Active Directory, o que sincroniza os nomes de conta e senhas entre o ambiente do Active Directory local e o locatário do Azure Active Directory.
  
 **Somente servidor de sincronização de diretório**. Em vez de Implantando o servidor de sincronização de diretório de 64 bits em seu ambiente local, você pode provisionar uma máquina virtual no Azure pela Internet.
  
 **Sincronização de diretórios + AD FS**. Essa opção permite que você ofereça suporte a identidades do Office 365 federado (SSO) sem adicionar hardware à infraestrutura local. Ele também fornece resiliência se o ambiente do Active Directory local não está disponível. Os recursos desta opção incluem:
  
- Componentes de integração de diretório são executados como máquinas virtuais do Azure.
    
- O AD FS é publicado na Internet por meio de proxies do AD FS executando como máquinas virtuais do Azure.
    
- Tráfego de autenticação de cliente, para usuários que estão se conectando de qualquer local, é tratado por servidores AD FS e proxies que são implantados como máquinas virtuais do Azure.
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Integração do Lync com o Exchange e SharePoint no Office 365

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server com o Exchange Online e SharePoint Online

O diagrama acompanha mostra o que Office 365 com o Exchange Online e SharePoint Online conectados a um farm do Lync Server 2013 local.
  
As vantagens dessa implantação permitem que você:
  
- Use o conjunto completo de recursos do Lync Server 2013.
    
- Aproveite o equipamento de telefone local existente, como PBXs.
    
- Use o Exchange Online para email, diminuir a carga de armazenamento e de servidores de email local.
    
- Use o SharePoint Online para colaboração, a descarga a tarefa de manutenção de servidores locais do SharePoint.
    
- Uso o Lync, Exchange e SharePoint integrado de recursos, incluindo Unified Messaging (UM) no Office 365.
    
#### <a name="exchange-server-with-lync-online"></a>Exchange Server com o Lync Online

O diagrama acompanha mostra o que Office 365 com o Lync Online conectados a um farm de servidor Exchange local.
  
As vantagens dessa implantação permitem que você:
  
- Aproveite a infra-estrutura existente do Exchange.
    
- Use o Lync Online para os recursos de conferência, mensagens instantâneas e presença.
    

