---
title: Diagrama acessível-sites da Internet no Microsoft Azure para SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
f1.keywords:
- NOCSH
description: Este artigo é uma versão de texto acessível do diagrama chamado sites da Internet no Microsoft Azure para SharePoint 2013.
ms.openlocfilehash: a68c5f8a0e92c45e3c33caaca77be0d841aa6003
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843892"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagrama acessível-sites da Internet no Microsoft Azure para SharePoint 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado sites da Internet no Microsoft Azure para SharePoint 2013.
  
Este cartaz descreve e ilustra como os sites de Internet públicos se beneficiam da elasticidade de nuvem e do Azure AD para contas de cliente. Há seis cenários diferentes que descrevem como os sites da Internet se beneficiam do Azure: 
  
- Projetar e dimensionar a topologia do farm. 
    
- Ajuste para o Azure. 
    
- Escolha o modelo do Active Directory. 
    
- Design para gerenciamento de identidades, zonas e autenticação. 
    
- Criar sites e URLs para publicação entre sites. 
    
- Projetar o ambiente do Azure. 
    
## <a name="design-and-size-the-farm-topology"></a>Projetar e dimensionar a topologia do farm

Use as diretrizes de topologia, capacidade e desempenho do SharePoint 2013 no TechNet para projetar a topologia do farm. 
  
Verifique se o farm que você design atende aos objetivos de capacidade e desempenho. 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>Exemplo: farm de sites médios da Internet (~ 85 visualizações de página por segundo)

Este farm fornece uma topologia de farm de pesquisa do SharePoint 2013 tolerante a falhas que é otimizada para um corpus que contém 3,4 milhões itens. 
  
O farm de exemplo processa documentos 100-200 por segundo, dependendo do idioma e acomoda 85 visualizações de página por segundo e 100 consultas por segundo. 
  
O diagrama a seguir mostra um farm médio de sites da Internet com três tipos de servidores: 
  
- Servidores da Web 
    
- Servidores de aplicativos 
    
- Servidores de banco de dados 
    
#### <a name="web-servers"></a>Servidores da Web

Na seção servidores Web, há três servidores Web, host A, host B e host C. Cada servidor Web contém um cache distribuído, perfis de usuário, metadados gerenciados e recursos de processamento de consultas. Eles também contêm uma réplica de partição de índice que está em cada servidor. 
  
Para expandir, adicione um servidor Web adicional com os mesmos recursos, que permite a exibição de 28 páginas adicionais por segundo. 
  
#### <a name="application-servers"></a>Servidores de aplicativos

Na seção servidores de aplicativos, há três servidores de aplicativos, host D, host e host F. o host D contém componentes de rastreamento, administração, análise e processamento de conteúdo. O host E contém componentes de rastreamento, administração e processamento de conteúdo. O host F contém componentes de rastreamento e processamento de conteúdo. 
  
Para expandir, adicione um servidor de aplicativos com um componente de rastreamento e um componente de processamento de conteúdo para processar um documento adicional de 40 por segundo. 
  
#### <a name="database-servers"></a>Servidores de banco de dados

Na seção servidores de banco de dados, há dois servidores, host G e host H. Os servidores de banco de dados estão em hosts emparelhados para tolerância a falhas. 
  
O host G contém todo o banco de dados do SharePoint, incluindo o banco de dados de administração de pesquisa, o banco de dados de link, dois bancos de dados de rastreamento O host H contém todos os bancos de dados do SharePoint, incluindo cópias redundantes de todos os bancos de dados usando clusters SQL, espelhamento ou SQL Server 2012 AlwaysOn. 
  
## <a name="fine-tune-for-azure"></a>Ajuste fino para o Azure

Talvez seja necessário ajustar o farm do SharePoint para os conjuntos de disponibilidade na plataforma do Azure. Para garantir a alta disponibilidade de todos os componentes, verifique se as funções de servidor estão definidas de forma idêntica. 
  
Na topologia de exemplo no diagrama: 
  
- Os servidores Web e os servidores de banco de dados são configurados de forma idêntica. 
    
- Os três servidores de aplicativos não são configurados de forma idêntica. Essas funções de servidor exigem ajuste fino para os conjuntos de disponibilidade no Azure. 
    
### <a name="before"></a>Before

A parte superior do diagrama mostra o farm do SharePoint antes que ele tenha sido ajustado para conjuntos de disponibilidade no Azure. No diagrama, os três servidores de aplicativos host não são configurados de forma idêntica. O número de componentes é determinado pelos objetivos de desempenho e capacidade do farm. Os três servidores são configurados da seguinte maneira: 
  
- O servidor de aplicativos do host D é configurado com funções de rastreamento, administração, análise e processamento de conteúdo. 
    
- O servidor de aplicativos host E é configurado com as funções de rastreamento, administração e processamento de conteúdo. 
    
- O servidor de aplicativos do host F é configurado com as funções de rastreamento e processamento de conteúdo. 
    
### <a name="after"></a>After

Esta parte do diagrama mostra o farm do SharePoint após ele ter sido ajustado para conjuntos de disponibilidade no Azure. Para adaptar essa arquitetura para o Azure, replicaremos os quatro componentes em todos os três servidores. Isso aumenta o número de componentes além do que é necessário para desempenho e capacidade. A compensação é que esse design garante alta disponibilidade de todos os quatro componentes da plataforma do Azure quando essas três máquinas virtuais são atribuídas a um conjunto de disponibilidade. 
  
Os três servidores são configurados para todas as funções de rastreamento, administração, análise e processamento de conteúdo. 
  
## <a name="choose-the-active-directory-model"></a>Escolha o modelo do Active Directory

Todas as soluções do SharePoint exigem o AD DS (serviços de domínio Active Directory) do Windows. No momento, há duas opções para soluções do SharePoint no Azure. 
  
- Opção 1: domínio dedicado — você pode implantar um domínio dedicado e isolado no Azure para dar suporte a um farm do SharePoint. Essa é uma boa opção para sites de Internet voltados para o público. 
    
- Opção 2: estender o domínio local por meio de uma conexão VPN site a site. Quando você estende o domínio local por meio de uma conexão VPN site a site, os usuários acessam o farm do SharePoint como se estivessem hospedados no local. Você pode aproveitar as implementações existentes do Active Directory e do DNS. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Design para gerenciamento de identidades, zonas e autenticação

### <a name="design-for-accounts-and-authentication"></a>Design para contas e autenticação

Determine como as contas serão gerenciadas e qual tipo de autenticação será usado. 
  
#### <a name="accounts-for-site-developers-and-authors"></a>Contas para desenvolvedores e autores de sites

- Adicionar contas ao domínio no Azure. 
    
- Use o AD FS (serviços de Federação do Active Directory) no local para federar as contas internas para o domínio no Azure. 
    
- Se o design incluir uma conexão VPN site a site, use as contas internas. 
    
#### <a name="accounts-for-customers"></a>Contas para clientes

- Usar o Azure Active Directory. 
    
- Use um provedor baseado em SAML diferente. 
    
### <a name="design-for-zones"></a>Design para zonas

No SharePoint 2013, o gerenciamento de identidades é acrescentado à configuração de zonas e autenticação. 
  
Esse design oferece uma clara separação das contas de clientes de todas as outras contas. 
  
- Use este design se quiser que as contas de clientes sejam tratadas de uma mesma diferença das contas internas de autores e desenvolvedores de sites. 
    
- Usando esse design, você pode usar políticas de zona para limitar as ações do cliente em um aplicativo Web. 
    
- Esse design resulta em diferentes URLs para contas de cliente e contas internas. 
    
Neste exemplo: 
  
- Configure a zona padrão para contas internas. 
    
- Configure a zona de extranet para acesso autenticado pelo cliente. Usar o Azure Active Directory (AD) para contas de clientes ou usar um provedor baseado em SAML diferente. 
    
- Configure a zona da Internet para acesso anônimo. 
    
Não use um design de duas zonas no qual todos os usuários autenticados estão configurados para usar a zona padrão. 
  
O diagrama a seguir mostra um design de três zonas com separação das contas internas e do cliente. 
  
Os visitantes e clientes acessam o locatário do Azure AD no farm do SharePoint 2013 por meio de aplicativos Web em uma de duas zonas. As duas zonas incluem: 
  
- Zona: Internet para usuários anônimos 
    
- Zona: Extranet para usuários autenticados 
    
Os usuários com contas internas acessam o locatário do Azure Active Directory do AD DS e do AD FS no ambiente local por meio do túnel VPN para o Azure AD. A zona padrão fornece autenticação do Windows (NTLM). 
  
### <a name="design-for-connecting-to-azure-ad"></a>Design para se conectar ao Azure AD

 O Azure AD fornece recursos de gerenciamento de identidades e controle de acesso para serviços em nuvem. Os recursos incluem um repositório baseado em nuvem para dados de diretório e um conjunto principal de serviços de identidade, incluindo processos de logon do usuário, serviços de autenticação e AD FS. Os serviços de identidade que estão incluídos no Azure AD se integram facilmente às implantações do AD DS local e dão suporte completo a provedores de identidade de terceiros.
  
O diagrama de acompanhamento mostra o cenário a seguir: 
  
Ao integrar o SharePoint 2013 com o Azure Active Directory, um serviço de controle de acesso (ACS) do Azure serve a duas finalidades: 
  
-  O Azure AD usa SAML 2,0 e o SharePoint só funciona com o SAML 1,1. O ACS compreende os formatos e serve como intermediário para transformar os formatos de token entre o SharePoint e o Azure AD.
    
- O ACS substitui a necessidade do serviço de token de segurança do provedor de identidade (IP-STS) para este cenário SAML. 
    
Para obter mais informações, consulte Configurar o Azure AD com o SharePoint 2013 na biblioteca do TechNet. 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>Criar sites e URLs para publicação entre sites

Um design de aplicativo da Web é recomendado para cenários de publicação. 
  
- Os sites de criação e publicação estão no mesmo aplicativo Web. 
    
- A publicação entre sites é usada para publicar ativos. 
    
Use conjuntos de sites baseados em caminho e nomeados por host. 
  
- Um conjunto de sites raiz é um requisito. Crie este site como um site baseado em caminho. 
    
- Crie todos os outros conjuntos de sites como conjuntos de sites nomeados por host. 
    
URLs de aplicativo Web e site raiz 
  
- Use um nome interno para a URL do aplicativo Web. O SharePoint usa o nome da máquina local como o nome padrão, a menos que um nome diferente seja especificado. Você pode usar um nome de domínio reservado para o ambiente de rede interna. 
    
- O SharePoint atribui um número de porta não padrão quando o aplicativo Web é criado. Use este número de porta em vez da porta 80 ou a porta 443. Ou use um número de porta diferente, mas não padrão. 
    
- Use o mesmo nome e número de porta para o conjunto de sites raiz, que é um conjunto de sites baseado em caminho. 
    
O diagrama a seguir mostra os serviços do pool de aplicativos, como a pesquisa interagindo com conjuntos de sites usando aplicativos da Web. Os conjuntos de sites mostrados incluem: 
  
- Conjunto de sites baseado em caminho localizado https://internal:8000 em (site raiz). 
    
- Rastreamento: conjuntos de sites nomeados por host, localizados em um https://authoring.contoso.com:8000endereço como. 
    
- Consultas: 2 conjuntos de sites nomeados por host diferentes localizados em endereços como: 
    
  - https://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - https://www.contoso.com:8000 
    
  - https://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - https://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Projetar o ambiente do Azure

Este exemplo de arquitetura inclui os seguintes elementos: 
  
- Uma conexão VPN de site a site é opcional e estende o ambiente do Windows AD DS e DNS local para a rede virtual no Azure. 
    
- Opcionalmente, use um domínio dedicado no Azure para dar suporte ao farm do SharePoint. 
    
- Os servidores são divididos nos serviços de nuvem do Azure com base na função. 
    
- Os conjuntos de disponibilidade garantem alta disponibilidade de funções de servidor configuradas de forma idêntica. 
    
Para obter mais informações, consulte o seguinte artigo no TechNet: arquiteturas do Azure para soluções do SharePoint. 
  
O diagrama a seguir mostra um exemplo de um ambiente local conectado a uma rede virtual do Azure. 
  
Incluído no ambiente local, que é um elemento opcional do ambiente do Azure, os seguintes componentes são: 
  
- Windows Server 2012 RRAS 
    
- AD DS 
    
- Um gateway VPN do Windows Server e do AD DS para a sub-rede do gateway VPN ativa 
    
O ambiente de rede virtual do Azure inclui os seguintes componentes: 
  
- A sub-rede ativa do gateway VPN (sobrepondo ao ambiente local, se aplicável) 
    
- Serviço de nuvem que inclui o AD DS e o conjunto de disponibilidade de DNS (dois servidores) 
    
- Serviço de nuvem que inclui o conjunto de disponibilidade do servidor front-end (três servidores do SharePoint) e o conjunto de disponibilidade do servidor de aplicativos (três servidores do SharePoint) 
    
- Serviço de nuvem que contém dois conjuntos de disponibilidade de banco de dados 
    

