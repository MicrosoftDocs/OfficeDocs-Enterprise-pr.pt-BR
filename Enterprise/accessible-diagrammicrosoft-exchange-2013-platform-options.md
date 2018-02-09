---
title: "Diagrama acessível - opções de plataforma do Microsoft Exchange 2013"
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
description: "Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Exchange 2013, que está disponível em diagramas técnicos."
ms.openlocfilehash: e1c4957c9152c5a23008c657d7e2d0d47b5cce0f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a>Diagrama acessível - opções de plataforma do Microsoft Exchange 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado opções de plataforma do Microsoft Exchange 2013, que está disponível em [Diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Este cartaz descreve o que arquitetos e business decision tomadores de precisam saber sobre implantações do Exchange Online e o Exchange Server e inclui: 
  
- Uma comparação de quatro opções de plataforma disponíveis para o Exchange 2013: Exchange Online (Office 365), Exchange híbrido, Exchange Server local e Provider-Hosted Exchange. 
    
- Descrições de três recursos novos ou atualizados no Exchange 2013. 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a>Comparação entre quatro diferentes implantações para a plataforma Exchange 2013

Comparação fornece informações sobre cada opção de implantação nas seguintes áreas: 
  
- Uma visão geral dos recursos de implantação diferentes 
    
- Benefícios da implementação de cada opção de implantação 
    
- Requisitos de licenciamento 
    
- Tarefas necessárias de arquiteturais 
    
- Responsabilidades do IT Pro para implementar cada opção de implantação 
    
### <a name="overview"></a>Visão geral

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Ganho de eficiência e reduzir os custos com o Office 365.
  
O diagrama acompanha mostra o Exchange Online com um locatário do Azure Active Directory que sincroniza os nomes de conta e senhas entre o ambiente de serviços de domínio Active Directory (AD DS) no local e o locatário do Azure Active Directory. Os serviços de Federação do Active Directory (AD FS) é necessário para o serviço single sign-on. 
  
Descrição dos recursos e funcionalidades:
  
- A operação de servidores e de software do servidor é manipulada pela Microsoft.
    
- Conjunto de recursos de rich do Exchange Server 2013 como um serviço baseado em nuvem.
    
- Sempre atualizada com os recursos mais recentes.
    
- Exchange Online Protection (EOP) é incluído para anti-spam/anti-malware protection.
    
- Alta disponibilidade incorporada com um 99,9% contrato de nível de serviço (SLA).
    
- Sincronização de diretórios incluindo senhas entre o local serviços de domínio do Active Directory (AD DS) e o locatário do Azure Active Directory. Os serviços de Federação do Active Directory (AD FS) é necessário para o serviço single sign-on.
    
#### <a name="exchange-hybrid"></a>Exchange híbrido

Você pode aproveitar os benefícios do Office 365, mantendo o Exchange Server local.
  
O diagrama acompanha mostra o Office 365 com o Exchange Online em que alguns usuários estão hospedados no local e alguns usuários hospedados online. Ele também mostra um locatário do Azure Active Directory que sincroniza os nomes de conta e senhas entre o ambiente de serviços de domínio Active Directory (AD DS) no local e o locatário do Azure Active Directory.
  
Descrição dos recursos e funcionalidades:
  
- Alguns usuários estão hospedados no local e alguns usuários hospedados online e usuários compartilham o mesmo espaço de endereço de email.
    
- Aproveita a infra-estrutura existente do Exchange Server.
    
- Migre do Exchange local para o Exchange Online ao longo do tempo, no seu calendário.
    
- Integre com outros aplicativos do Office 365, incluindo o Lync Online e SharePoint Online.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

Você pode criar e gerenciar sua própria infra-estrutura do Exchange Server 2013.
  
O diagrama acompanha mostra uma infraestrutura do Exchange Server com um ambiente de serviços de domínio Active Directory (AD DS) do local onde os usuários são hospedados no local.
  
Descrição dos recursos e funcionalidades:
  
- Maior grau de personalização para sua configuração e controle.
    
- Nenhuma dependência no mantendo a afinidade de sessão na camada de balanceamento de carga.
    
- Simple alta disponibilidade e resiliência do site usando grupos de disponibilidade de banco de dados (DAGs).
    
- Gerenciados disponibilidade que ajuda você a manter uma excelente experiência de usuário.
    
- Aproveite a infra-estrutura de armazenamento e o hardware existente.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado em provedor

Você pode terceirizar sua carga de trabalho do Exchange Server para um provedor de soluções do Exchange Server.
  
O diagrama acompanha mostra um ambiente do Exchange Server que é operado e mantido por um provedor.
  
Descrição dos recursos e funcionalidades:
  
- A operação de servidores e de software do servidor é manipulada pelo provedor.
    
- Planejamento, dimensionamento, dimensionamento e manutenção da infraestrutura do Exchange Server são delegadas ao provedor.
    
- Manutenção de serviço é manipulada pelo provedor.
    
- O conjunto de recursos do Exchange é limitado a versão do software implantada pelo seu provedor.
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Benefícios da implementação de cada opção de implantação

#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

Essa opção de implantação é melhor para:
  
- Organizações que buscam para reduzir os custos de operações para o local do Exchange implantações.
    
- Organizações que planejam aproveitar outras ofertas do Office 365, como o SharePoint Online e o Lync Online.
    
#### <a name="exchange-hybrid"></a>Exchange híbrido

Essa opção de implantação é melhor para:
  
- Facilitando uma migração do Exchange local para o Exchange Online.
    
- Dando suporte a sites remotos sem investir em infraestrutura de escritório de filial.
    
- Empresas multinacionais com subsidiárias que exigem dados devem residir no local.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

Essa opção de implantação é melhor para:
  
- Soluções altamente personalizadas.
    
- Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados pelo Exchange Online.
    
- As organizações está sujeito às normas de governança de dados que exigem dados devem residir no local.
    
- Organizações que desejam retém o controle da plataforma inteira and solution.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado em provedor

Essa opção de implantação é melhor para:
  
- Organizações que precisam de funcionalidade do servidor do Exchange, mas deseja terceirizar sua implantação e manutenção.
    
- Organizações que precisam de opções de suporte personalizado.
    
- Soluções personalizadas e integração com aplicativos personalizados oferecidos pelo provedor.
    
- Soluções herdada com componentes de terceiros que dependem de hardware e software que não são suportados pelo Exchange Online.
    
### <a name="license-requirements"></a>Requisitos de licença

A tabela a seguir detalha os requisitos de licença de cada opção de implantação.
  
|**Opção de implantação**|**Requisitos de licença**|
|:-----|:-----|
|Exchange Online (Office 365)  <br/> |Modelo de assinatura  <br/> |
|Exchange híbrido  <br/> | Office 365 - modelo de assinatura <br/>  Local - todas as licenças de local se aplicam (licenças de revisão para trocas Server local) <br/>  Licença de servidor híbrido * <br/> |
|Exchange Server local  <br/> | Sistema operacional do servidor <br/>  Licença de servidor do Exchange 2013 <br/>  Licença de acesso para cliente Exchange 2013 <br/> |
|Exchange hospedado em provedor  <br/> |Custos baseiam-se no contrato com o provedor  <br/> |
   
### <a name="architecture-tasks"></a>Tarefas de arquitetura

Esta seção lista as tarefas de arquiteturais para cada opção de implantação.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Planejar e projetar a sincronização de diretório.
    
- Certifique-se de capacidade de rede e conectividade através de firewalls, servidores proxy, gateways e em links de WAN.
    
#### <a name="exchange-hybrid"></a>Exchange híbrido

Além das tarefas a arquitetura para o Office 365 e o local de ambientes:
  
- Decida se deseja fornecer um logon único na experiência.
    
- Decida se deseja rotear emails de entrada da Internet por meio de uma organização local ou Exchange Online Protection.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

- Projete a topologia do Exchange.
    
- Planeje a capacidade para hardware de servidor.
    
- Projete a topologia de roteamento de mensagem.
    
- Projetar o balanceamento de carga para servidores de acesso para cliente.
    
- Plano para alta disponibilidade usando grupos de disponibilidade de banco de dados.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado em provedor

Verifique se a capacidade da rede e a disponibilidade por meio de firewalls, servidores proxy, gateways e em links de WAN estão disponíveis para o seu provedor.
  
### <a name="it-pro-responsibilities"></a>Responsabilidades do IT Pro

Esta seção lista as responsabilidades profissionais de TI para cada opção de implantação.
  
#### <a name="exchange-online-office-365"></a>Exchange Online (Office 365)

- Implemente o plano de sincronização de diretório.
    
- Planejar e implementar os registros DNS internos e externos e roteamento.
    
- Configure o servidor proxy ou firewall para o endereço IP do Office 365 e requisitos de URL.
    
- Administre as contas de usuário e as configurações do Exchange Online.
    
#### <a name="exchange-hybrid"></a>Exchange híbrido

Além das responsabilidades profissionais de TI para o Office 365 e o local de ambientes:
  
- Configure serviços de Federação Active Directory (AD FS) para logon único em (se desejar).
    
- Configure certificados do Exchange para comunicações seguras entre os servidores Exchange 2013 e o Office 365.
    
- Configure registros DNS para o caminho de email de Internet entrado desejado.
    
#### <a name="exchange-server-on-premises"></a>Exchange Server local

- Configure os certificados necessários para os serviços do Exchange.
    
- Provisione os servidores.
    
- Implemente a topologia de roteamento de mensagem do Exchange.
    
- Implemente grupos de disponibilidade de banco de dados.
    
- Atualizar e manter servidores do Exchange.
    
- Dependendo da utilização, adicionar ou remover servidores conforme necessário.
    
#### <a name="provider-hosted-exchange"></a>Exchange hospedado em provedor

Responsabilidades do provedor incluem:
  
- Manutenção do sistema e de serviço.
    
- Recurso de distribuições.
    
- Recuperação de desastres e proteção de dados.
    
Responsabilidades da equipe de TI em sua organização incluem criando e gerenciando contas de usuário.
  
#### <a name="more-information"></a>Mais informações

Para saber mais sobre o Exchange Online (Office 365), consulte o seguinte:
  
- [Descrição do serviço do Exchange Online](https://aka.ms/EXOSD)
    
- [Biblioteca on-line do Exchange no TechNet](https://aka.ms/EXOTN)
    
- [Portal Online do Exchange](https://aka.ms/EXO)
    
Para saber mais sobre o híbrido do Exchange, consulte o seguinte:
  
- [Implantações híbridas do Exchange 2013](https://aka.ms/ExchangeHybrid). Lembre-se de que a licença de servidor híbrido só é necessária para os seguintes cenários: organização do Exchange 2010 com o servidor híbrido do Exchange 2013 e a organização do Exchange 2007 com o servidor híbrido do Exchange 2013 ou Exchange 2010.
    
- [O Office 365 entrar](https://aka.ms/HybridKey)
    
Para saber mais sobre o Exchange Server local, consulte o seguinte:
  
- [Biblioteca do Exchange Server 2013 no TechNet](https://aka.ms/Ex2013TN)
    
- [Portal do Exchange Server 2013](https://aka.ms/Exchange2013)
    
- [Arquitetura do Exchange Server 2013](https://aka.ms/Ex2013SP1ArchPoster)
    
Para saber mais sobre Provider-Hosted Exchange, consulte o seguinte:
  
[Orientação e soluções de hospedagem e de multilocação do Exchange Server 2013](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a>Descrições dos três recursos novos ou atualizados no Exchange 2013

### <a name="exchange-online-protection"></a>Proteção do Exchange Online

Exchange Online Protection (EOP) oferece proteção antispam e antimalware para qualquer implantação, fornecendo uma camada de recursos de proteção que são implantados em uma rede global de centros de dados. Isso ajuda a simplificar o gerenciamento de seus ambientes de mensagens. EOP está incluído no Exchange Online assinaturas, mas você também pode aproveitá-lo para implantações híbridas e no local.
  
Os diagramas acompanha mostram as implantações do Exchange Online, Exchange híbrido e Exchange local que incluem a camada EOP na rede global.
  
### <a name="exchange-server-deployment-assistant"></a>Assistente de implantação do Exchange Server

O Assistente de implantação do Exchange Server é uma ferramenta baseada na web que faz algumas perguntas sobre seu ambiente atual e, em seguida, gera uma lista de verificação personalizada que tenha um passo a passo para ajudá-lo a implantar o Exchange Server para diferentes tipos de cenários. Se você estiver migrando de uma versão anterior do Exchange para o Exchange 2013, migrando para o Exchange Online ou planejando uma infraestrutura híbrida, o Assistente de implantação do Exchange Server cria uma lista de verificação de implantação personalizada para seu cenário.
  
Acompanha a captura de tela mostra uma lista de verificação de exemplo que foi criada usando o Assistente de implantação do Exchange Server.
  
### <a name="integration-with-lync-and-sharepoint"></a>Integração com o Lync e o SharePoint

Exchange Server 2013 inclui vários recursos que integram com o Lync Server 2013 e SharePoint Server 2013. Juntos, esses produtos oferecem um conjunto rico de recursos e melhorar a colaboração em toda a organização. 
  
Um diagrama acompanha mostra o cartaz de autenticação de servidor-para-servidor e inclui um link para o pôster. 
  
- Arquivamento, retenção e descoberta eletrônica
    
- Caixas de correio locais
    
- Repositório unificado de contatos
    
- Fotos de alta resolução do usuário
    
- Presença do Lync no Outlook e Outlook Web App
    
- Autenticação servidor-para-servidor
    
- Caixa postal
    
- Gravações de reuniões
    
- Sincronização de tarefas do Exchange
    
Um diagrama acompanha mostra o cartaz da arquitetura do Exchange Server 2013 SP1 e inclui um link para o pôster.
  

