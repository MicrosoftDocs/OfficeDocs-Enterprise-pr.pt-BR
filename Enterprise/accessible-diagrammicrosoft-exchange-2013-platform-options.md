---
title: Diagrama acessível-opções de plataforma do Microsoft Exchange 2013
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Exchange 2013, disponível em diagramas técnicos.
ms.openlocfilehash: ddf215544b811257e6d43f212784a3a1e5aac7b0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068587"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>Diagrama acessível-opções de plataforma do Microsoft Exchange 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Exchange 2013, disponível em [diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Este cartaz descreve quais responsáveis pelas decisões de negócios (BDMs) e arquitetos precisam saber sobre as implantações do Exchange Online e do Exchange Server e incluem: 
  
- Uma comparação de quatro opções de plataforma disponíveis para o Exchange 2013: Exchange Online (Office 365), Exchange híbrido, Exchange Server local e Exchange hospedado pelo provedor. 
    
- Descrições de três recursos novos ou atualizados no Exchange 2013. 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Comparação de quatro implantações diferentes para a plataforma Exchange 2013

A comparação fornece informações sobre cada opção de implantação nas seguintes áreas: 
  
- Uma visão geral dos diferentes recursos de implantação 
    
- Benefícios da implementação de cada opção de implantação 
    
- Requisitos de licença 
    
- Tarefas de arquitetura necessárias 
    
- Responsabilidades de profissionais de ti para implementar cada opção de implantação 
    
### <a name="overview"></a>Visão geral

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Você obtém eficiência e reduz custos com o Office 365.
  
O diagrama a seguir mostra o Exchange Online com um locatário do Azure Active Directory que sincroniza nomes de conta e senhas entre o ambiente do AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory. O AD FS (serviços de Federação do Active Directory) é necessário para o logon único. 
  
Descrição dos recursos e funcionalidade:
  
- A operação de servidores e software de servidor é manipulada pela Microsoft.
    
- Conjunto de recursos avançados do Exchange Server 2013 como um serviço baseado em nuvem.
    
- Sempre atualizado com os recursos mais recentes.
    
- O proteção do Exchange Online (EOP) está incluído para proteção antispam/antimalware.
    
- Alta disponibilidade interna com um contrato de nível de serviço (SLA) de 99,9%.
    
- Sincronização de diretório, incluindo senhas entre o AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory. O AD FS (serviços de Federação do Active Directory) é necessário para o logon único.
    
#### <a name="exchange-hybrid"></a>Exchange Híbrido

Você pode aproveitar os benefícios do Office 365 enquanto mantém o Exchange Server no local.
  
O diagrama a seguir mostra o Office 365 com o Exchange Online em que alguns usuários estão hospedados no local e alguns usuários estão hospedados online. Também mostra um locatário do Azure Active Directory que sincroniza nomes de conta e senhas entre o ambiente do AD DS (serviços de domínio Active Directory) local e o locatário do Azure Active Directory.
  
Descrição dos recursos e funcionalidade:
  
- Alguns usuários estão hospedados no local e alguns usuários estão hospedados online, e os usuários compartilham o mesmo espaço de endereço de email.
    
- Aproveita a infraestrutura existente do Exchange Server.
    
- Migre do Exchange no local para o Exchange Online com o passar do tempo, no seu cronograma.
    
- Integre-se com outros aplicativos do Office 365, incluindo o Lync Online e o SharePoint Online.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

Você pode criar e gerenciar sua própria infraestrutura do Exchange Server 2013.
  
O diagrama a seguir mostra uma infraestrutura do Exchange Server com um ambiente do AD DS (serviços de domínio Active Directory) local onde os usuários estão hospedados no local.
  
Descrição dos recursos e funcionalidade:
  
- O maior grau de controle e personalização da sua configuração.
    
- Nenhuma dependência para manter a afinidade da sessão na camada de balanceamento de carga.
    
- Alta disponibilidade simples e resiliência de site usando grupos de disponibilidade de banco de dados (DAGs).
    
- Disponibilidade gerenciada que ajuda você a manter uma ótima experiência do usuário.
    
- Aproveite o hardware existente e a infraestrutura de armazenamento.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado pelo provedor

Você pode terceirizar sua carga de trabalho do Exchange Server para um provedor de soluções do Exchange Server.
  
O diagrama a seguir mostra um ambiente do Exchange Server operado e mantido por um provedor.
  
Descrição dos recursos e funcionalidade:
  
- A operação de servidores e software de servidor é manipulada pelo seu provedor.
    
- O planejamento, o dimensionamento, a escalabilidade e a manutenção da infraestrutura do Exchange Server são delegados ao seu provedor.
    
- A manutenção do serviço é manipulada pelo seu provedor.
    
- O conjunto de recursos do Exchange é limitado à versão do software implantada pelo provedor.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Benefícios da implementação de cada opção de implantação

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Essa opção de implantação é melhor para:
  
- Organizações que procuram reduzir os custos de operações para implantações locais do Exchange.
    
- Organizações que planejam aproveitar outras ofertas do Office 365, como o SharePoint Online e o Lync Online.
    
#### <a name="exchange-hybrid"></a>Exchange Híbrido

Essa opção de implantação é melhor para:
  
- Facilitar uma migração do Exchange no local para o Exchange Online.
    
- Suporte a sites remotos sem investir na infraestrutura de filial do escritório.
    
- Empresas multinacionais com subsidiárias que exigem dados para residir no local.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

Essa opção de implantação é melhor para:
  
- Soluções altamente personalizadas.
    
- Soluções herdadas com componentes de terceiros que dependem de hardware e software que não são compatíveis com o Exchange Online.
    
- As organizações estão sujeitas às regulamentações de governança de dados que exigem dados para residir no local.
    
- Organizações que desejam manter o controle de toda a plataforma e solução.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado pelo provedor

Essa opção de implantação é melhor para:
  
- Organizações que precisam de funcionalidade do Exchange Server, mas que desejam terceirizar sua implantação e manutenção.
    
- Organizações que precisam de opções de suporte personalizado.
    
- Soluções e integração personalizadas com aplicativos personalizados oferecidos pelo provedor.
    
- Soluções herdadas com componentes de terceiros que dependem de hardware e software que não são compatíveis com o Exchange Online.
    
### <a name="license-requirements"></a>Requisitos de licença

A tabela a seguir detalha os requisitos de licença para cada opção de implantação.
  
|**Opção de implantação**|**Requisitos de licença**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |Modelo de assinatura  <br/> |
|Exchange Híbrido  <br/> | Office 365-modelo de assinatura <br/>  Local-todas as licenças locais são aplicadas (revise as licenças do servidor de troca local) <br/>  Licença de servidor híbrido * <br/> |
|Exchange Server local  <br/> | Sistema operacional do servidor <br/>  Licença de servidor do Exchange 2013 <br/>  Licença de acesso para cliente do Exchange 2013 <br/> |
|Exchange hospedado pelo provedor  <br/> |Os custos são baseados no contrato com o provedor  <br/> |
   
### <a name="architecture-tasks"></a>Tarefas de arquitetura

Esta seção lista as tarefas arquitetônicas de cada opção de implantação.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Planejar e projetar a sincronização de diretórios.
    
- Garantir a capacidade e a conectividade da rede por meio de firewalls, servidores de proxy, gateways e entre links de WAN.
    
#### <a name="exchange-hybrid"></a>Exchange Híbrido

Além das tarefas de arquitetura para os ambientes do Office 365 e local:
  
- Decida se deseja fornecer uma experiência de logon único.
    
- Decida se deseja encaminhar emails de entrada da Internet por meio de uma organização local ou através do Exchange Online Protection.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

- Projetar a topologia do Exchange.
    
- Planejar a capacidade do hardware do servidor.
    
- Criar a topologia de roteamento de mensagens.
    
- Designar balanceamento de carga para servidores de acesso para cliente.
    
- Planejar a alta disponibilidade usando grupos de disponibilidade de banco de dados.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado pelo provedor

Certifique-se de que a capacidade e a disponibilidade da rede por meio de firewalls, servidores de proxy, gateways e links de WAN estão disponíveis para o provedor.
  
### <a name="it-pro-responsibilities"></a>Responsabilidades de profissionais de ti

Esta seção lista as responsabilidades de profissionais de ti para cada opção de implantação.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Implementar o plano de sincronização de diretórios.
    
- Planejar e implementar registros DNS internos e externos e roteamento.
    
- Configure o servidor de proxy ou o firewall para os requisitos de URL e endereço IP do Office 365.
    
- Administre as contas de usuário e as configurações do Exchange Online.
    
#### <a name="exchange-hybrid"></a>Exchange Híbrido

Além das responsabilidades do profissional de ti para os ambientes do Office 365 e locais:
  
- Configure o AD FS (serviços de Federação do Active Directory) para logon único (se desejado).
    
- Configure certificados do Exchange para comunicações seguras entre os servidores do Exchange 2013 e o Office 365.
    
- Configurar registros DNS para o caminho de email da Internet de entrada desejado.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

- Configure os certificados necessários para os serviços do Exchange.
    
- Provisionar os servidores.
    
- Implementar a topologia de roteamento de mensagens do Exchange.
    
- Implementar grupos de disponibilidade de banco de dados.
    
- Atualizar e manter servidores do Exchange.
    
- Dependendo da utilização, adicione ou remova os servidores conforme necessário.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado pelo provedor

As responsabilidades do provedor incluem:
  
- Manutenção do sistema e do serviço.
    
- Distribuições de recursos.
    
- Proteção de dados e recuperação de desastres.
    
As responsabilidades da equipe de ti em sua organização incluem a criação e o gerenciamento de contas de usuário.
  
#### <a name="more-information"></a>Mais informações

Para saber mais sobre o Exchange Online (Office 365), confira o seguinte:
  
- [Descrição do serviço do Exchange Online](https://aka.ms/EXOSD)
    
- [Biblioteca do Exchange Online no TechNet](https://aka.ms/EXOTN)
    
- [Portal do Exchange Online](https://aka.ms/EXO)
    
Para saber mais sobre o Exchange híbrido, confira o seguinte:
  
- Implantações híbridas do [Exchange 2013](https://aka.ms/ExchangeHybrid). Você deve observar que a licença de servidor híbrido só é necessária para os seguintes cenários: organização do Exchange 2010 com o servidor do Exchange 2013 Hybrid Server e a organização do Exchange 2007 com o Exchange 2013 ou Exchange 2010 Hybrid Server.
    
- [Entrada do Office 365](https://aka.ms/HybridKey)
    
Para saber mais sobre o Exchange Server local, confira o seguinte:
  
- [Biblioteca do Exchange Server 2013 no TechNet](https://aka.ms/Ex2013TN)
    
- [Portal do Exchange Server 2013](https://aka.ms/Exchange2013)
    
- [Arquitetura do Exchange Server 2013](https://aka.ms/Ex2013SP1ArchPoster)
    
Para saber mais sobre o Exchange hospedado pelo provedor, confira o seguinte:
  
[Orientações e soluções de hospedagem e multilocação do Exchange Server 2013](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Descrições de três recursos novos ou atualizados no Exchange 2013

### <a name="exchange-online-protection"></a>Proteção do Exchange Online

O Exchange Online Protection (EOP) fornece proteção antispam e antimalware para qualquer implantação fornecendo uma camada de recursos de proteção implantados em uma rede global de data centers. Isso ajuda a simplificar o gerenciamento de seus ambientes de mensagens. O EOP está incluído nas assinaturas do Exchange Online, mas você também pode utilizá-lo para implantações híbridas e locais.
  
Os diagramas a seguir mostram implantações para o Exchange Online, o Exchange híbrido e o Exchange local que incluem a camada EOP na rede global.
  
### <a name="exchange-server-deployment-assistant"></a>Assistente de Implantação do Exchange Server

O assistente de implantação do Exchange Server é uma ferramenta baseada na Web que faz algumas perguntas sobre seu ambiente atual e, em seguida, gera uma lista de verificação passo a passo personalizada para ajudá-lo a implantar o Exchange Server para diferentes tipos de cenários. Se você estiver migrando de uma versão anterior do Exchange para o Exchange 2013, migrar para o Exchange Online ou planejar uma infraestrutura híbrida, o assistente de implantação do Exchange Server cria uma lista de verificação de implantação personalizada para seu cenário.
  
A captura de tela a seguir mostra um exemplo de lista de verificação que foi criada usando o assistente de implantação do Exchange Server.
  
### <a name="integration-with-lync-and-sharepoint"></a>Integração com o Lync e o SharePoint

O Exchange Server 2013 inclui muitos recursos que se integram ao Lync Server 2013 e ao SharePoint Server 2013. Juntos, esses produtos oferecem um pacote avançado de recursos e aprimoram a colaboração em sua organização. 
  
Um diagrama de acompanhamento mostra o pôster de autenticação de servidor para servidor e inclui um link para o pôster. 
  
- Arquivamento, retenção e descoberta eletrônica
    
- Caixas de correio local
    
- Repositório unificado de contatos
    
- Fotos do usuário de alta resolução
    
- Presença do Lync no Outlook e no Outlook Web App
    
- Autenticação de servidor para servidor
    
- Caixa postal
    
- Gravações de reunião
    
- Sincronização de tarefas do Exchange
    
Um diagrama de acompanhamento mostra o pôster da arquitetura do Exchange Server 2013 SP1 e inclui um link para o pôster.
  

