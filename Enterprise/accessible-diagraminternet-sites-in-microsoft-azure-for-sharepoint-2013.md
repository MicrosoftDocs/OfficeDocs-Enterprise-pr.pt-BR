---
title: "Diagrama acessível - sites da Internet no Microsoft Azure para o SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: "Este artigo é uma versão de texto acessível do diagrama denominada sites da Internet no Microsoft Azure para SharePoint 2013."
ms.openlocfilehash: 7713d4e91f97a1b4139510f6a7c320c69ace43cf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagrama acessível - sites da Internet no Microsoft Azure para o SharePoint 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama denominada sites da Internet no Microsoft Azure para SharePoint 2013.
  
Este pôster descreve e ilustra como público benefícios de sites de Internet do Azure AD para contas de cliente e de nuvem elasticidade. Há seis diferentes cenários que descrevem como sites da Internet se beneficiar do Azure: 
  
- Criar e dimensionar a topologia de farm. 
    
- Ajuste para Azure. 
    
- Escolha o modelo do Active Directory. 
    
- Design para gerenciamento de identidade, zonas e autenticação. 
    
- Design de sites e URLs para publicação intersite. 
    
- Projete o ambiente do Azure. 
    
## <a name="design-and-size-the-farm-topology"></a>Criar e dimensionar a topologia de farm

Use as diretrizes de topologia, a capacidade e desempenho para o SharePoint 2013 no TechNet para desenhar a topologia de farm. 
  
Certifique-se de que o farm que você projetar cumpre os objetivos de desempenho e capacidade. 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>Exemplo: Farm médio Sites da Internet (~ 85 exibições de página por segundo)

Este farm fornece uma topologia de farm de pesquisa do SharePoint 2013 tolerante a falhas que é otimizada para um corpus que contém 3,400,000 itens. 
  
O farm de exemplo processa os documentos de 100 a 200 por segundo, dependendo do idioma, e ele acomoda 85 visualizações de página por segunda e 100 consultas por segundo. 
  
O diagrama acompanha mostra um farm médio de sites de internet com três tipos de servidores: 
  
- Servidores da Web 
    
- Servidores de aplicativos 
    
- Servidores de banco de dados 
    
#### <a name="web-servers"></a>Servidores Web

Na seção de servidores web, há três servidores web, Host A, Host B e c de Host. Cada servidor web contém um cache distribuído, perfis de usuário, metadados gerenciados e recursos de processamento de consultas. Eles também contêm uma réplica da partição de índice que está em cada servidor. 
  
Para dimensionar, adicionar um servidor de web adicionais com os mesmos recursos, o que permite uma 28 adicionais de exibições de página por segundo. 
  
#### <a name="application-servers"></a>Servidores de aplicativos

Na seção servidores de aplicativo, há três servidores de aplicativos, Host D, F de Host, e Host F. Host D contém os componentes de processamento de rastreamento, administração, análise e conteúdo. Host E contém os componentes de processamento de rastreamento, administração e de conteúdo. Host F contém os componentes de processamento de conteúdo e de rastreamento. 
  
Para dimensionar, adicione um servidor de aplicativos com um componente de rastreamento e um componente para processar uma documentos adicionais de 40 por segundo de processamento de conteúdo. 
  
#### <a name="database-servers"></a>Servidores de banco de dados

Na seção servidores de banco de dados, existem dois servidores Host G e h de Host. Os servidores de banco de dados estão em hosts emparelhados para tolerância a falhas. 
  
Host G contém o banco de dados do SharePoint todos, incluindo o banco de dados vinculado, banco de dados de administração de pesquisa, dois bancos de dados de rastreamento, um banco de dados de análise e todos os outros bancos de dados do SharePoint. Host H contém os bancos de dados do SharePoint todos, inclusive cópias redundantes de todos os bancos de dados usando o SQL clustering, espelhamento ou SQL Server 2012 AlwaysOn. 
  
## <a name="fine-tune-for-azure"></a>Ajuste para o Windows Azure

O farm do SharePoint talvez precisem ser ajustadas para conjuntos de disponibilidade na plataforma Windows Azure. Para garantir a alta disponibilidade de todos os componentes, certifique-se de que as funções de servidor tudo identicamente são configuradas. 
  
Na topologia de exemplo no diagrama: 
  
- Os servidores web e os servidores de banco de dados são configurados de forma idêntica. 
    
- Os servidores de três aplicativos não são configurados de forma idêntica. Essas funções de servidor requerem o ajuste fino para disponibilidade define no Windows Azure. 
    
### <a name="before"></a>Antes

A parte superior do diagrama mostra o farm do SharePoint antes que ele tenha sido ajustado para disponibilidade define no Windows Azure. No diagrama, os servidores de aplicativos de três do host não são identicamente configurados. O número de componentes é determinado pelas metas de desempenho e capacidade para o farm. Três servidores são configurados da seguinte maneira: 
  
- Servidor de aplicativos host D é configurado com as funções de processamento de rastreamento, administração, análise e conteúdo. 
    
- Servidor de aplicativos host f é configurado com as funções de processamento de rastreamento, administração e de conteúdo. 
    
- Servidor de aplicativos host F é configurado com funções de processamento de conteúdo e de rastreamento. 
    
### <a name="after"></a>After

Esta parte do diagrama mostra o farm do SharePoint depois que ele tenha sido ajustado para disponibilidade define no Windows Azure. Para adaptar-se essa arquitetura para o Windows Azure, podemos vai replicar quatro componentes em todos os três servidores. Isso aumenta o número de componentes além do que é necessário para desempenho e capacidade. A desvantagem é que esse design garante a alta disponibilidade de todos os quatro componentes na plataforma Windows Azure quando essas três máquinas virtuais são atribuídas a um conjunto de disponibilidade. 
  
Três servidores estiverem configurados para todos têm as funções de processamento de rastreamento, administração, análise e conteúdo. 
  
## <a name="choose-the-active-directory-model"></a>Escolha o modelo do Active Directory

Todas as soluções do SharePoint exigem o Windows Active Directory Domain Services (AD DS). Neste momento, há duas opções para soluções do SharePoint no Windows Azure. 
  
- Opção 1: De domínio dedicado — você pode implantar um domínio dedicado e isolado no Azure para oferecer suporte a um farm do SharePoint. Esta é uma boa opção para sites da Internet público. 
    
- Opção 2: Estenda o domínio local por meio de uma conexão de VPN-to-site. Quando você estende o domínio local por meio de uma conexão VPN de site a site, os usuários acessar o farm do SharePoint como se estivesse hospedado no local. Você pode tirar proveito das suas implementações existentes do Active Directory e DNS. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Design para gerenciamento de identidade, zonas e autenticação

### <a name="design-for-accounts-and-authentication"></a>Design para contas e autenticação

Determine como contas serão gerenciadas e qual tipo de autenticação será usado. 
  
#### <a name="accounts-for-site-developers-and-authors"></a>Contas para autores e desenvolvedores de site

- Adicione contas ao domínio no Windows Azure. 
    
- Use os serviços de Federação do Active Directory (AD FS) no local para estabelecer uma federação as contas internas no domínio no Windows Azure. 
    
- Se o design inclui uma conexão VPN de site a site, use as contas internas. 
    
#### <a name="accounts-for-customers"></a>Contas para clientes

- Use o Azure Active Directory. 
    
- Use um provedor de SAML-based diferente. 
    
### <a name="design-for-zones"></a>Design de zonas

No SharePoint 2013, gerenciamento de identidade é acrescentado na configuração de zonas e autenticação. 
  
Esse design fornece a separação clara de contas do cliente de todas as outras contas. 
  
- Use esse design, se você quiser contas de cliente a ser tratada completamente diferente do que as contas internas para autores e desenvolvedores de site. 
    
- Usando esse design, você pode usar políticas de zona para limitar as ações do cliente em um aplicativo web. 
    
- Esse design resulta em diferentes URLs para contas de cliente e internos. 
    
Neste exemplo: 
  
- Configure a zona padrão para contas internas. 
    
- Configure a zona extranet para acesso de cliente autenticado. Use o Azure AD (Active Directory) para contas de cliente, ou um provedor de SAML-based diferente. 
    
- Configure a zona da Internet para acesso anônimo. 
    
Não use um design de dois-zona na qual todos os usuários autenticados são configurados para usar a zona padrão. 
  
O diagrama acompanha mostra um design de três-zone com separação de internos e contas de cliente. 
  
Visitantes e clientes acessam o locatário do AD do Windows Azure no farm do SharePoint 2013 por meio de aplicativos da web em uma das duas zonas. As duas zonas incluem: 
  
- Zona: Internet para usuários anônimos 
    
- Zona: Extranet para usuários autenticados 
    
Usuários com contas internas acessem o locatário do Azure Active Directory do AD DS e AD FS no ambiente local através do túnel VPN para o Windows Azure AD. A zona padrão fornece autenticação do Windows (NTLM). 
  
### <a name="design-for-connecting-to-azure-ad"></a>Design para conexão com o Azure AD.

 Azure AD fornece recursos de controle acesso e o gerenciamento de identidade para serviços de nuvem. Os recursos incluem um repositório baseado em nuvem para dados de diretório e um conjunto básico de serviços de identidade, incluindo processos de logon do usuário, serviços de autenticação e AD FS. Os serviços de identidade que estão incluídos no Windows Azure AD facilmente integram com o seu local implantações do AD DS e totalmente provedores de identidade de terceiros de suporte.
  
O diagrama acompanha mostra o cenário a seguir: 
  
Ao integrar o SharePoint 2013 com o Windows Azure Active Directory, um serviço de controle de acesso (ACS) do Azure tem duas finalidades: 
  
-  Azure AD usa SAML 2.0 e SharePoint só funciona com o SAML 1.1. ACS entende ambos os formatos e serve como intermediário para transformar os tokens formatos entre o SharePoint e o Azure AD.
    
- ACS substitui a necessidade para o provedor security token serviço identidade (IP-STS) para este cenário SAML. 
    
Para obter mais informações, consulte Configure Azure AD com o SharePoint 2013 na TechNet library. 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>Projetar sites e URLs para publicação intersite

Um um design de aplicativo da web é recomendado para cenários de publicação. 
  
- Tanto a criação e publicação de sites estão no mesmo aplicativo web. 
    
- Publicação intersite é usada para publicar ativos. 
    
Use conjuntos de sites baseados em caminho e nome de host. 
  
- Um conjunto de sites raiz é um requisito. Crie este site como um site baseado em caminho. 
    
- Crie todos os outros conjuntos de sites como conjuntos de sites nomeados por host. 
    
URLs de site raiz e aplicativo Web 
  
- Use um nome interno para a URL do aplicativo web. SharePoint usa o nome da máquina local como o nome padrão, a menos que um nome diferente for especificado. Você pode usar um nome de domínio que está reservado para o ambiente de rede interna. 
    
- SharePoint atribui um número de porta não padrão quando o aplicativo web é criado. Use esse número de porta, em vez de porta 80 ou 443. Ou use um número de porta diferente, mas não-padrão. 
    
- Use o mesmo nome e o número da porta para o conjunto de sites raiz, que é um conjunto de sites baseados em caminho. 
    
O diagrama acompanha mostra serviços de pool de aplicativos, como pesquisa a interação com os conjuntos de sites usando os aplicativos web. Os conjuntos de sites mostrados incluem: 
  
- Conjunto de sites baseados em caminho localizado em http://internal:8000 (site raiz). 
    
- Rastreamento: Conjuntos de sites nomeados por Host localizados em um endereço como https://authoring.contoso.com:8000. 
    
- Consultas: 2 conjuntos de sites nomeados por Host separados localizada endereços como: 
    
  - http://www.contoso.com 
    
  - https://Secure.contoso.com 
    
  - http://www.contoso.com:8000 
    
  - http://Assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - http://Assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Projetar o ambiente do Azure

Essa arquitetura de exemplo inclui os seguintes elementos: 
  
- Uma conexão de VPN-to-site é opcional e estende o local Windows AD DS e o ambiente de DNS para a rede virtual no Windows Azure. 
    
- Opcionalmente, use um domínio dedicado no Windows Azure para suportar o farm do SharePoint. 
    
- Servidores estão divididos entre os serviços de nuvem Azure com base na função. 
    
- Conjuntos de disponibilidade garantir a alta disponibilidade das funções de servidor configurado de forma idêntica. 
    
Para obter mais informações, consulte o artigo a seguir no TechNet: Azure Architectures for SharePoint Solutions. 
  
O diagrama acompanha mostra um exemplo de um ambiente local se conectar com uma rede virtual do Azure. 
  
Estão incluídos no ambiente local, que é um elemento opcional do ambiente do Azure, os seguintes componentes: 
  
- Windows Server 2012 RRAS 
    
- AD DS 
    
- Um gateway VPN do Windows Server e o AD DS para a sub-rede do Gateway de VPN ativo 
    
O ambiente de rede virtual do Azure inclui os seguintes componentes: 
  
- A sub-rede do Gateway de VPN ativo (sobrepostas com o ambiente local, se aplicável) 
    
- Serviço de nuvem que inclui a disponibilidade do AD DS e DNS definido (dois servidores) 
    
- Serviço de nuvem que incluem a disponibilidade do servidor front-end definido (três servidores do SharePoint) e a disponibilidade do servidor de aplicativo definido (três servidores do SharePoint) 
    
- Define um serviço em nuvem que contém dois disponibilidade de banco de dados 
    

