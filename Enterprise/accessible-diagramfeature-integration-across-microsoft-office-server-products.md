---
title: Diagrama acessível - o recurso integração entre produtos Microsoft Office Server
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: d78983fa-0951-49b8-b890-d76a44c70035
description: Este artigo é uma versão de texto acessível do diagrama chamado o recurso integração entre produtos Microsoft Office Server - SharePoint Server, Exchange Server, Lync Server e Office Online.
ms.openlocfilehash: 809a9272d7088ac069aad6b64daedfe059188247
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504214"
---
# <a name="accessible-diagram---feature-integration-across-microsoft-office-server-products"></a>Diagrama acessível - o recurso integração entre produtos Microsoft Office Server

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado o recurso integração entre produtos Microsoft Office Server - SharePoint Server, Exchange Server, Lync Server e Office Online.
  
O diagrama consiste em várias guias, conforme indicado pelo títulos das seções deste documento.
  
## <a name="introduction-tab"></a>Guia de Introdução

### <a name="illustrations-for-cross-server-features"></a>Ilustrações para recursos entre servidores

Este arquivo do Visio (ou arquivo PDF multipage) tem nove guias, cada um deles tem informações e um diagrama sobre um recurso que funciona em produtos do Office Server.
  
Os recursos e as guias são: 
  
- Introdução
    
- Autenticação servidor-para-servidor 
    
- Fotos de usuário de alta resolução 
    
- Repositório unificado de contatos 
    
- Caixas de correio locais 
    
- Sincronização de tarefas do Exchange 
    
- Presença do Lync no Outlook Web App 
    
- Caixa postal
    
- Gravações de reuniões 
    
Envie feedback sobre esta solução ou solicitações de soluções adicionais para MODAContent@microsoft.com. 
  
### <a name="tips-for-printing"></a>Dicas para impressão

O tamanho da página de cada guia é 22 x 17 pol (cerca de um quarto do tamanho de um diagrama de engenharia ANSI). Você pode imprimir esta página em duas polegadas de folhas de porte Tabloide (11 x 17)) ou em quatro folhas Carta (11 x 8,5 polegadas). Se você tiver uma plotadora, você pode imprimir destes cartazes no seu tamanho completo. Se você não tiver plotadora, use as etapas a seguir para imprimir em papel menor. 
  
 **Imprimir cartazes em papel menor**
  
1. Abra o cartaz no Visio. 
    
2. No menu **arquivo** , clique em **Configurar página**. 
    
3. Na guia **Configurar impressão** , na seção **papel da impressora** , selecione o tamanho de papel desejado para a impressão.
    
4. Na guia **Configurar impressão** , na seção **zoom de impressão** , clique em **caber em**e insira **1 folha na horizontal por 1 folha na vertical**. 
    
5. Na guia **Tamanho da página** , clique em **Dimensionar para caber o conteúdo do desenho**e, em seguida, clique em **Okey**. 
    
6. No menu **arquivo** , clique em **Imprimir**. 
    
### <a name="microsoft-tags-and-qr-codes"></a>Códigos de QR e marcas da Microsoft

Use seu Windows phone ou baixar um leitor de código QR para obter mais informações sobre a implementação desses recursos. 
  
### <a name="cross-server-features"></a>Recursos entre servidores

Uma tabela mostra os recursos e os produtos de servidor do Office que usá-los. Os recursos são: 
  
Autenticação de servidor-para-servidor. Esse recurso é aplicável a: 
  
- SharePoint 
    
- Exchange
    
- Lync
    
- O Office Online (anteriormente conhecido como o Office Web Apps) 
    
Fotos do usuário de alta resolução. Esse recurso é aplicável a: 
  
- SharePoint
    
- Exchange
    
- Lync
    
Repositório de contatos unificado. Esse recurso é aplicável a: 
  
- Exchange
    
- Lync
    
Caixas de correio do site. Esse recurso é aplicável a: 
  
- SharePoint
    
- Exchange
    
Sincronização de tarefas do Exchange. Esse recurso é aplicável a: 
  
- SharePoint
    
- Exchange
    
Presença do Lync no Outlook Web App. Esse recurso é aplicável a: 
  
- Lync
    
Caixa postal. Esse recurso é aplicável a: 
  
- Lync
    
Gravações de reuniões. Esse recurso é aplicável a: 
  
- SharePoint
    
- Lync
    
### <a name="office-web-apps-server"></a>Office Web Apps Server

Office Web Apps Server é um produto de servidor do Office que fornece o arquivo baseado em navegador exibindo e editando serviços para arquivos do Office. Servidor do Office Web Apps funciona com os produtos e serviços que oferecem suporte a Web Application Open plataforma Interface Protocol (WOPI). Esses produtos, conhecidos como hosts, incluem o SharePoint 2013, Lync Server 2013 e Exchange Server 2013. 
  
Para saber mais sobre o Office Web Apps Server, baixe o pôster de simplificada de implantação do Office Web Apps em http://aka.ms/OfficeWebAppsPoster. 
  
## <a name="server-to-server-authentication-tab"></a>Guia de autenticação de servidor-para-servidor

### <a name="servicing-resource-requests-between-servers"></a>Atendendo a solicitações de recursos entre servidores

Autenticação de servidor-para-servidor é um novo recurso do Exchange Server 2013, Lync Server 2013 e SharePoint Server 2013 que permite que um servidor de recursos de solicitação de outro servidor em nome de um usuário. Esse recurso usa o setor standard Open Authorization (OAuth) 2.0 protocolo. Autenticação de servidor-para-servidor permite muitos novos cenários, como eDiscovery, fotos de usuário de alta resolução e caixas de correio do site. 
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="server-to-server-trust-relationships"></a>Relações de confiança de servidor-para-servidor

Para um servidor para atender a uma solicitação de recurso de entrada, ele deve confiar no servidor que fazendo a solicitação. Para estabelecer relação de confiança, você deve configurar as relações de confiança de servidor-para-servidor. 
  
Uma relação de confiança de servidor-para-servidor é uma maneira. Quando você configura um servidor que executa o SharePoint 2013 para confiar em um servidor Exchange 2013, o servidor que executa o SharePoint Server confianças solicitações de recursos do Exchange server, mas o servidor do Exchange não confiar em solicitações de recursos do servidor que executa o Servidor do SharePoint. Para integração perfeita, você deve estabelecer relações de confiança bidirecionais. 
  
O diagrama acompanha mostra relações de confiança de servidor-para-servidor que são estabelecidas como relações de confiança bidirecionais. As relações de confiança bidirecional mostradas estão entre um servidor Exchange, um servidor do SharePoint e um servidor do Lync. Cada tipo de servidor tem uma relação de confiança bidirecional com cada um dos dois servidores. 
  
### <a name="configuration"></a>Configuração

Para configurar uma relação de confiança de autenticação de servidor-para-servidor, você deve adicionar um novo emissor de token de segurança confiável que corresponde a cada servidor que envia solicitações de recursos em nome de usuários. Cada tipo de servidor tem um ponto de extremidade de metadados de JavaScript Object Notation (JSON) que contém informações de configuração e uma parte pública do certificado de assinatura de token de acesso. Parte da configuração de uma relação de confiança de autenticação de servidor-para-servidor está especificando o ponto de extremidade de metadados JSON de outro servidor. 
  
A tabela a seguir lista o ponto de extremidade de metadados JSON para cada servidor. A tabela mostra: 
  
- Um servidor do Exchange com um ponto de extremidade de metadados JSON de https://<server name>/autodiscover/metadata/json/1 
    
- Um servidor do Lync com um ponto de extremidade de metadados JSON de https://<server name>/metadata/json/1 
    
- Um servidor do SharePoint com um ponto de extremidade de metadados JSON de https://<web app name>/_layouts/15/metadata/json/1 
    
### <a name="example-how-server-to-server-authentication-works-for-ediscovery-between-sharepoint-and-exchange"></a>Exemplo: Servidor-para-servidor como funciona a autenticação para descoberta eletrônica entre o SharePoint e do Exchange

Neste exemplo, o servidor Exchange 2013 tiver sido configurado para confiar no servidor que executa o SharePoint Server com uma relação de confiança de servidor-para-servidor. Um centro de descoberta eletrônica no servidor que executa o SharePoint Server foi configurado para incluir dados nas caixas de correio no Exchange server. 
  
Solicitações de recursos em outro servidor assumem a forma de tokens de acesso que são enviadas para o serviço do servidor web no servidor de destino. 
  
O diagrama acompanha mostra como as consultas e tokens de acesso viagem entre os dois servidores. 
  
1. Um administrador de descoberta eletrônica envia uma consulta ao servidor que executa o servidor do SharePoint que inclui recursos em um servidor Exchange. 
    
2. O servidor que executa o SharePoint Server gera um token de acesso, que identifica o usuário e o recurso solicitado. 
    
3. O servidor que executa o SharePoint Server envia o token de acesso ao servidor do Exchange. 
    
4. O Exchange server valida o token de acesso e envia os resultados da consulta. 
    
5. O servidor que executa o SharePoint Server envia a eDiscovery resultados da consulta para o computador do administrador de descoberta eletrônica. 
    
## <a name="high-resolution-user-photos-tab"></a>Guia de usuário fotos de alta resolução

### <a name="larger-profile-picture-used-across-all-office-applications"></a>Maior imagem de perfil usada em todos os aplicativos do Office

Usando a guia de **fotos de alta resolução do usuário** , você pode armazenar fotos como 648 x 648 pixels no Exchange 2013. Eles podem ser acessados por aplicativos do cliente, incluindo o Outlook, Outlook Web App, SharePoint 2013, Lync 2013 e clientes de email móvel. Uma foto de baixa resolução também é armazenada no Active Directory.
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="configuration"></a>Configuração

Configurar autenticação de servidor para servidor: 
  
- Entre o Exchange 2013 e SharePoint 2013. 
    
- Entre o Exchange 2013 e Lync 2013. 
    
 **No Exchange Server 2013**
  
- Inicie e configure o serviço de descoberta automática do Exchange 2013. 
    
- Defina as URLs externas do SharePoint. Estes são os usos de URLs SharePoint quando ele acessa as fotos no Exchange. 
    
 **No SharePoint Server 2013**
  
- Instale o Exchange Web Services Managed API. Use o GacUtil para carregar o Microsoft.Exchange.WebServices.dll no Cache de Assembly Global (GAC). 
    
- Use o Windows PowerShell para configurar a sincronização de fotos com o Exchange. 
    
 **Como funciona**
  
- Os usuários carregar uma foto usando a página Minha conta no Outlook Web App (OWA) ou as configurações de conta no Outlook 2013. 
    
- Exchange redimensiona automaticamente a imagem para uso pelo AD DS (48 x 48 pixels) ou por outros aplicativos do Office, incluindo o OWA e o cliente do Outlook 2013 (96 x 96 pixels). 
    
Os usuários podem carregar imagens com intervalos de pixel de 48 × 48 para × 648 648. As fotos são redimensionadas: 
  
- 64 × 64 é usada para a miniatura da AD. 
    
- 96 × 96 é usada para o Lync 2013, Lync Web Access, Outlook e Outlook Web Access. 
    
- 648 × 648 é usada para o Lync Web Access e o Lync 2013. 
    
Por exemplo, scripts de configuração, consulte artigos do blog do Jens Trier Rasmussen: 
  
- Usando o Exchange 2013 fotos de alta resolução do SharePoint Server 2013 (http://aka.ms/Bhr4d2) 
    
- Integrando o Exchange 2013 e Lync Server 2013 (http://aka.ms/Pn08dw) 
    
O cartaz também contém os códigos de QR para esses dois artigos do blog. 
  
O diagrama acompanha mostra como um usuário pode atualizar uma foto para usar em todos os aplicativos do Office. 
  
1. Foto de atualizações do usuário no Outlook, SharePoint ou no Lync. Uma vez atualizados, atualizada foto é usada em todos os aplicativos do Office. 
    
2. O usuário pode usar diversas maneiras para atualizar uma foto: 
    
3. 
  - Cliente do Outlook ou no Outlook Web App (OWA) na porta 443 do HTTP para um servidor de acesso para cliente do Exchange. 
    
  - Meu Site via HTTP ou HTTPS para um servidor do SharePoint. SharePoint armazena em cache o usuário no banco de dados meusite (Https:443). As interfaces do servidor do SharePoint com o servidor de acesso de cliente do Exchange usando URLs externas definido no Exchange. 
    
  - Cliente do Lync 2013, que mantém um GetConnection com o Exchange server para obter atualizações de foto (solicitação HTTPS Get - 443). 
    
4. O servidor de acesso de cliente do Exchange conecta-se ao servidor de caixa de correio do Exchange usando a comunicação do Exchange interna. 
    
5. O servidor de caixa de correio do Exchange usa o Exchange 2013 para enviar a foto de alta resolução do usuário no AD DS (LDAP:389). 
    
6. A foto é sincronizada dos serviços de domínio Active Directory (AD DS) para o Lync endereço livro ABS (serviço) no servidor do Lync para que clientes herdados podem obter as mesmas fotos (LDAP:389). 
    
7. O cliente herdado Lync agora tem acesso à foto. 
    
## <a name="unified-contact-store-tab"></a>Guia de armazenamento de contato unificado

### <a name="exchange-2013-is-the-contact-store-for-all-office-applications"></a>Exchange 2013 é o armazenamento de contato para todos os aplicativos do Office

Repositório unificado de contatos (UCS) fornece uma experiência consistente de contato em produtos do Microsoft Office. Os usuários armazenam informações de todos os contatos em suas caixas de correio do Exchange 2013. As mesmas informações de contato fiquem disponíveis globalmente entre o Lync, Exchange, Outlook e Outlook Web App. 
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
 **Configuração**
  
- Configure a autenticação de servidor-para-servidor entre o Exchange Server 2013 e Lync Server 2013. 
    
- No Lync 2013, habilite a diretiva de repositório unificado de contatos (é habilitada por padrão). 
    
Por exemplo scripts de configuração, consulte o artigo do blog do Jens Trier Rasmussen: 
  
- Integrando o Exchange 2013 e Lync Server 2013 (http://aka.ms/Oyg7fh) 
    
 **Como funciona**
  
- Contatos do Lync para um usuário são migrados para o Exchange 2013 automaticamente quando o usuário fizer logon com o Lync 2013. 
    
- Os usuários podem acessar e gerenciar seus contatos do Lync do Lync 2013, Outlook 2013 ou Outlook Web Access. 
    
Contatos do usuário são migrados automaticamente para o servidor Exchange 2013 quando o usuário: 
  
1. Foi atribuída uma política de serviços de usuário com UcsAllowed definido como **True**. 
    
2. Tenha sido provisionado com uma caixa de correio do Exchange 2013 e tiver entrado na caixa de correio pelo menos uma vez. 
    
3. Se conecta ao Lync usando um cliente avançado do Lync 2013. 
    
Se conecta ao Lync usando um cliente avançado do Lync 2013. 
  
1. Se conecta ao suas caixas de correio do Exchange 2013 no servidor de acesso de cliente do Exchange, usando um cliente Outlook ou o Outlook Web App (OWA) sobre HTTPS/443. O servidor de caixa de correio do Exchange usa uma comunicação interna do Exchange para se comunicar com o servidor de acesso de cliente do Exchange. 
    
2. Se conecta ao Lync 2013. O cliente Lync contata o servidor de Lync via SIP/5061 HTTPS/443. 
    
3. O cliente Lync informa ao servidor do Lync que o usuário está habilitado para o repositório unificado de contatos via SIP/5061. 
    
4. O Lync server usa o serviço de armazenamento do Lync para migrar os contatos do usuário para o Exchange 2013 no servidor de acesso de cliente do Exchange. 
    
5. O usuário deve sair e entrar no Lync 2013 para que as alterações apareçam (não é mostrado no diagrama). 
    
6. Após a migração, o cliente Lync usa serviços Web do Exchange (EWS) para ler e manter os contatos do Lync. 
    
## <a name="site-mailboxes-tab"></a>Guia de caixas de correio de site

### <a name="a-central-filing-cabinet-for-emails-and-documents"></a>Um arquivo convencional central para emails e documentos

Caixas de correio de site melhorar a colaboração e produtividade do usuário, permitindo o acesso a documentos armazenados nas mensagens do SharePoint e email armazenadas no Exchange, usando a mesma interface de cliente. 
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
 **Configuração**
  
Configuração do SharePoint: 
  
- Configure a sincronização de perfil de usuário no farm do SharePoint. 
    
- Configure o aplicativo de serviço de gerenciamento de aplicativo no farm do SharePoint. 
    
- Configure SSL para a zona padrão para suportar a autenticação de servidor-para-servidor. 
    
- Instale a API do EWS nos servidores que executam o SharePoint 2013. 
    
- Estabeleça permissões de confiança e serviço OAuth em servidores que executam o SharePoint 2013. 
    
Configuração do Exchange: 
  
- Estabeleça permissões de confiança e serviço OAuth em servidores do Exchange. 
    
- Crie a política de provisionamento de caixa de correio do site. 
    
- Configure o prefixo de nome de caixa de correio de site (opcional). 
    
 **Como funciona**
  
Uma caixa de correio de site funcionalmente é composta de armazenamento de associação (proprietários e membros), compartilhado do SharePoint 2013 site por meio de uma caixa de correio do Exchange 2013 para mensagens de email e um site do SharePoint 2013 para documentos e uma interface de gerenciamento que cuida de provisionamento e precisa de ciclo de vida. 
  
O diagrama acompanha mostra os usuários que usam caixas de correio do site para acessar mensagens de email no Outlook e documentos armazenados no SharePoint. 
  
1. Os usuários podem acessar os documentos de sites de equipe do SharePoint por meio das caixas de correio de site no Outlook 2013 Pro Plus. 
    
2. Os usuários também podem ler emails na caixa de entrada de caixa de correio de Site do site de equipe do SharePoint. 
    
3. Emails são armazenados em caixas de correio de site em servidores do Exchange. 
    
4. Documentos são armazenados em caixas de correio de site em servidores do SharePoint. 
    
5. Os metadados do conteúdo no site do SharePoint é sincronizado com o Exchange usando a representação State Transfer (REST) API via HTTPS. 
    
### <a name="provisioning-and-management"></a>Provisionamento e gerenciamento

Caixas de correio de site são configuradas e gerenciadas pelo SharePoint 2013. Existem recursos do SharePoint e do Exchange para provisionamento e gerenciamento. 
  
#### <a name="sharepoint"></a>SharePoint

Um diagrama mostra os componentes no SharePoint que são necessárias para provisionar a caixa de correio do site, incluindo: 
  
- Aplicativo da Caixa de Correio do Site 
    
- Proprietários e membros do site de equipe 
    
- Política de ciclo de vida do site de equipe 
    
Provisionar uma nova caixa de correio do Site, instalar o aplicativo de caixa de correio de Site no site de equipe e acessar o aplicativo de pelo menos uma vez. 
  
A associação de site do SharePoint determina quem tem acesso à caixa de correio de Site. 
  
Retenção de caixa de correio do site segue a mesma política de ciclo de vida configurada para o site do SharePoint ao qual está associada. 
  
#### <a name="exchange"></a>Exchange

O diagrama mostra a política de provisionamento de caixa de correio do Site. Este é o componente do Exchange que é obrigatório para provisionar a caixa de correio do site.
  
No servidor do Exchange, você pode definir políticas de provisionamento de caixa de correio de Site. Essas políticas regem o email características enviados para e recebidos da caixa de correio do site, o tamanho da caixa de correio de site no servidor do Exchange e permitem que você defina um prefixo para endereços de email da caixa de correio do Site. 
  
Para implantações do Exchange local, você também precisará periodicamente pesquisar e excluir caixas de correio de Site que foram marcadas para exclusão por meio da diretiva de ciclo de vida do SharePoint. 
  
## <a name="exchange-task-synchronization-tab"></a>Guia de sincronização de tarefas do Exchange

### <a name="synchronizing-tasks-among-sharepoint-server-2013-project-server-2013-and-exchange-server-2013"></a>Sincronizando tarefas entre o SharePoint Server 2013, Project Server 2013 e Exchange Server 2013

Usando a sincronização de tarefas do Exchange, você pode sincronizar tarefas no SharePoint Server 2013 e Project Server 2013 com o Exchange Server 2013. Os usuários podem exibir e gerenciar suas tarefas no Outlook 2013 ou em Meu Site dele. 
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Project Server 2013 (opcional) 
    
 **Pré-requisitos**
  
No Exchange 2013: 
  
- Configure a permissão de confiança e serviço OAuth. 
    
No SharePoint Server 2013: 
  
- Aplicativo de serviço de perfil de usuário. 
    
- Aplicativo de serviço de gerenciamento de trabalho. 
    
- Pesquisa (Isso é necessário para as tarefas no SharePoint Server 2013). Configure com rastreamentos contínuos e rastreamentos incrementais. 
    
- É necessário o Secure Sockets Layer (SSL). 
    
- Os usuários que possuam Meus Sites existentes. 
    
- Projeto de aplicativo de serviço (para agregação tarefas do Project Server). 
    
- Exchange Web Services API em cada servidor front-end da web (isto é um arquivo separado .exe baixável que deve estar instalado). 
    
No Project Server 2013: 
  
- Crie sites do aplicativo Web do projeto. 
    
 **Como funciona**
  
Quando o modo de exibição de minhas tarefas em Meus Sites é aberto ou atualizado: 
  
- O aplicativo de serviço de gerenciamento de trabalho sincroniza entre o SharePoint Server e do Project Server. 
    
- Trabalho de Timer de sincronização do Exchange chama o aplicativo de serviço de gerenciamento de trabalho para sincronizar tarefas com o Exchange Server 2013. 
    
- A página Minhas tarefas em Meus Sites é atualizada. 
    
Quando o trabalho de Timer de sincronização do Exchange for executado: 
  
- O aplicativo de serviço de gerenciamento de trabalho sincroniza entre o SharePoint Server, Project Server e Exchange Server. 
    
O diagrama acompanha mostra a interação entre o SharePoint Server 2013, Exchange Server 2013, Outlook 2013 e Project Server 2013. 
  
SharePoint Server 2013 executa os trabalhos e os aplicativos a seguir: 
  
- Aplicativo de serviço de perfil de usuário. 
    
- Aplicativo de serviço de pesquisa. 
    
- Trabalho de aplicativo de serviço de gerenciamento, que é descrito abaixo. 
    
- Trabalho de Timer de sincronização do Exchange, que é descrita abaixo. 
    
- SharePoint Server 2013 contém Meu Site do usuário e outros Sites e executa várias tarefas de usuário. 
    
- SharePoint Server 2013 contém um índice de pesquisa. 
    
Exchange Server 2013 contém o seguinte: 
  
- Banco de dados do Exchange com informações de email do usuário 
    
- Tarefas de sincronização 
    
Outlook 2013 mostra o seguinte: 
  
- Os usuários podem aceitar para sincronizar suas tarefas, que é descrita abaixo. 
    
- Os usuários podem exibir e editar tarefas no Outlook. 
    
Project Server 2013 mostra o seguinte: 
  
- Banco de dados do Project 
    
- Sites do Project Web Access com tarefas 
    
O aplicativo de serviço de gerenciamento de trabalho: 
  
- Agrega tarefas de listas do SharePoint e listas de tarefas do projeto (não sincronizar tarefas com o Exchange Server). 
    
- Sincroniza quando os usuários exibir Meu Site dele. 
    
- Mantém a lista de usuários que consentimento. 
    
- Sincroniza o próximo lote de usuários. 
    
O trabalho de Timer de sincronização do Exchange: 
  
- Determina o próximo lote de usuários. 
    
- Garante que todos os usuários são sincronizados constantemente. 
    
- Inicia a chamada para o aplicativo de serviço de gerenciamento de trabalho para sincroniza tarefas com o Exchange Server para usuários que são aceitos em somente. 
    
Aceitar 
  
- Os usuários devem aceitar para sincronizar suas tarefas do Exchange com o Meu Site dele ou suas tarefas do SharePoint Server 2013 e Project Server 2013 com o Exchange Server 2013. 
    
## <a name="lync-presence-in-office-2013-outlook-web-app-and-sharepoint-server-tab"></a>Presença do Lync na guia Office 2013, o Outlook Web App e o SharePoint Server

### <a name="lync-server-as-the-authoritative-source-of-presence-information"></a>Lync Server, como a fonte autoritativa de informações de presença

Usando as informações de presença do Lync, é possível ter uma exibição consistente de informações de presença entre o Lync, Outlook e SharePoint. Informações de presença de consultas de Outlook diretamente do Lync, que é instalado localmente no mesmo computador que o Outlook. Quando os usuários exibir informações de presença no SharePoint Server, as informações de presença são consultadas pelo Lync no computador local.
  
Produtos de cliente: 
  
- Outlook 2013 
    
- Lync 2013 
    
Produtos de servidor: 
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
- SharePoint Server 2013 
    
 **Como funciona**
  
Desde que o Lync 2013 estiver instalado no computador local do usuário, Outlook e SharePoint Server exibem automaticamente as informações de presença de usuários. 
  
Para usuários do Outlook Web App, presença de consultas de CAS do Exchange em nome do usuário. 
  
 **Existem dois diagramas acompanha**
  
O primeiro mostra como um usuário entra no Outlook Web App e trocar consultas do Lync Server para obter informações de presença. 
  
1. O usuário entra no Outlook Web App. O computador cliente acessa o servidor de acesso de cliente (CAS) do Exchange via HTTPS/443 e também chama o servidor de caixa de correio do Exchange com uma comunicação interna do Exchange. 
    
2. O usuário entra no seu Exchange 2013 da caixa de correio, e o CAS do Exchange consulta o Lync Server para obter informações de presença sobre SIP / MTLS:5061. 
    
Para obter mais informações, consulte [integrando Microsoft Lync Server 2013 e o Microsoft Outlook Web App 2013](https://go.microsoft.com/fwlink/?LinkId=313522).
  
O segundo diagrama mostra como o Outlook e o SharePoint Server usam Lync 2013 para exibir as informações de presença de usuários. 
  
1. O usuário entra no Lync 2013 sobre SIP / TLS:5061, que chama o Lync server. 
    
2. R. o usuário entra suas caixas de correio do Exchange 2013 através do Outlook no Office 2013. O computador cliente acessa o servidor de acesso de cliente (CAS) do Exchange via HTTPS/443 e ele também chama o servidor de caixa de correio do Exchange com uma comunicação interna do Exchange. 
    
3. R. outlook chama o Lync instalado no mesmo computador que o Outlook para recuperar informações de presença. 
    
4. B. o usuário se conecta ao SharePoint MySite via HTTP ou HTTPS, que chama o servidor do SharePoint. 
    
5. B. o Internet Explorer chama o Lync, que é instalado no mesmo computador do navegador, para recuperar informações de presença. 
    
## <a name="voicemail-tab"></a>Guia de caixa postal

### <a name="exchange-um-is-the-voicemail-system-for-lync-server"></a>UM do Exchange é o sistema de caixa postal para o Lync Server

Caixa postal permite que um chamador deixar uma caixa postal aos usuários do Lync usando o Exchange Unified Messaging (UM). 
  
Produtos de cliente: 
  
- Lync 2013 
    
- Dispositivo PSTN (PBX, celular, POTS) 
    
Produtos de servidor: 
  
- Exchange Server 2013 
    
- Exchange Server 2013 
    
 **Como funciona**
  
Quando uma chamada não for atendida pelo receptor da chamada em qualquer um dos pontos de extremidade do receptor ativos, o Lync Server roteia a chamada para a caixa postal em UM do Exchange (isto é, caixa de correio de Exchange Server). 
  
O diagrama acompanha mostra o roteamento de chamadas para dois cenários: 
  
- O chamador inicia uma chamada usando o Lync 2013. 
    
- O chamador inicia uma chamada usando o dispositivo PSTN (PBX, celular, POTS). 
    
O chamador inicia uma chamada usando o Lync 2013: 
  
1. O chamador uma inicia uma chamada para o receptor usando o Lync 2013. A chamada é iniciada e enviada para o Lync Server. 
    
2. A chamada é roteada para o servidor primário do Lync do receptor. 
    
3. Lync Server liga para os pontos de extremidade ativos no Lync 2013 do receptor. 
    
4. Quando a chamada não for atendida, a chamada é roteada para a caixa postal (UM do Exchange) no Exchange CAS (roteador de chamada). 
    
O chamador inicia uma chamada usando o Lync 2013: 
  
1. B do chamador disca o número de telefone do receptor da chamada usando o PSTN. 
    
2. A chamada PSTN é encaminhada do gateway IP para o servidor de mediação, que é um servidor do Lync. 
    
3. O servidor de mediação routs a chamada para o servidor primário do Lync do receptor. 
    
4. Lync Server liga para os pontos de extremidade ativos no Lync 2013 do receptor. 
    
5. Quando a chamada não for atendida, a chamada é roteada para a caixa postal (UM do Exchange) no Exchange CAS (roteador de chamada). 
    
## <a name="meeting-recordings-tab"></a>Guia de gravações da reunião

### <a name="publish-your-meeting-recordings-on-your-sharepoint-team-site"></a>Publicar seus gravações de reuniões em seu site de equipe do SharePoint

Gravações de reuniões são um componente essencial da comunicação unificada. Uma boa maneira de compartilhar suas gravações de reunião é usar bibliotecas de ativos do SharePoint em seus sites de equipe para armazenar suas gravações de reuniões. 
  
Produtos de cliente: 
  
- Lync 2013 
    
Produtos de servidor: 
  
- Produtos de servidor: 
    
- SharePoint 2013 
    
Pré-requisitos: 
  
- Lync 2013 — A gravação de reunião é um recurso do lado do cliente do Lync 2013. 
    
- SharePoint 2013 — Você tem o site de equipe, onde deseja armazenar as gravações de reuniões já em funcionamento. 
    
 **O que é gravado?**
  
A seguir é registrada em um arquivo MP4 durante a reunião (cada ponto de marcador é precedido por um ícone que representa o tipo de gravação): 
  
- Todo o áudio 
    
- Vídeo (se usado) de alto-falante ativo 
    
- Vídeo panorama (se usado) 
    
- Todo o conteúdo é apresentado 
    
- Mensagens instantâneas * 
    
* Somente as mensagens instantâneas dentro da reunião são incluídas. Qualquer mensagens de ponto a ponto entre os participantes da reunião não faz parte da reunião e, portanto, não é capturado. 
  
O cartaz inclui dois diagramas para dois cenários diferentes: 
  
- Preparando para publicação gravações de reuniões 
    
- Gravação e publicação de uma reunião usando o cliente Lync 
    
### <a name="preparing-for-publishing-meeting-recordings"></a>Preparando para publicação gravações de reuniões

O diagrama mostra o SharePoint Server 2013 com um Site de equipe, centro de Administração Central e o servidor de serviços de informações da Internet (IIS). 
  
Site da equipe contém: 
  
- O ativo app biblioteca. 
    
- Biblioteca de ativos de reuniões, para o qual equipe membros enviam gravações de reuniões. 
    
O Centro de Administração Central contém definições gerais do aplicativo web. 
  
O servidor IIS contém configurações de IIS. 
  
Para preparar para a publicação de gravações de reuniões: 
  
1. Em seu site de equipe do SharePoint, adicione o App. biblioteca de ativos, opcionalmente, se você não conseguir efetuar o upload gravações de reuniões devido a restrições de tamanho ou tempos limites de conexão, execute as etapas adicionais de 2 e 3. 
    
2. Na Administração Central do SharePoint, altere a configuração de tamanho máximo de carregamento para o aplicativo web que contém seu conjunto de sites de equipe. 
    
3. Nas configurações do servidor IIS, aumente o limite de conexão do IIS para o site que contém seu conjunto de sites de equipe. 
    
 **Bibliotecas de ativos digitais**
  
Bibliotecas de ativos digitais são bibliotecas de ativos que contêm vídeos que têm certas implicações de desempenho e capacidade. Para obter mais informações, consulte o plano de bibliotecas de ativos digitais no SharePoint Server 2013 localizado em http://aka.ms/O1vq5w. O cartaz também inclui um código QR para acessar essa informação. 
  
### <a name="recording-and-publishing-a-meeting-using-the-lync-client"></a>Gravação e publicação de uma reunião usando o cliente Lync

O diagrama mostra um usuário usando o Lync para ingressar em uma reunião. A reunião é gravada usando o cliente do Lync, que cria um arquivo MP4 com o conteúdo das reuniões. A gravação de MP4 é salva na pasta de gravação do Lync em seu computador. Você pode mover a gravação MP4 sua biblioteca de ativos de reuniões, do qual você pode inseri-lo em um wiki, página do SharePoint ou blog. 
  
 **Para registrar e publicar uma reunião usando o cliente Lync**
  
1. Começar a gravar a reunião usando o cliente Lync. 
    
2. O conteúdo das reuniões é registrado em um arquivo MP4 durante a reunião. 
    
3. Após a reunião é concluído, a gravação MP4 aparece na pasta de gravação no seu computador (c:\\usuários\\<username>\\vídeos\\gravações do Lync). Opcionalmente, você pode personalizar a gravação de reunião usando o app Lync Recording Manager que obtém instalado com o cliente Lync. 
    
4. Arraste e solte na reunião gravação em sua biblioteca de ativos do SharePoint. 
    
5. Opcional: Depois a gravação estiver em sua biblioteca de ativos, você poderá inseri-lo em qualquer página do SharePoint. Para obter mais informações sobre esta etapa, consulte que a entrada de blog do Office 365, criar e publicar vídeos de treinamento com o SharePoint e o Lync Online, localizado em http://aka.ms/R61q35. 
    
 **Miniaturas de vídeo**
  
Miniaturas de vídeo melhoram a aparência de sua biblioteca de ativos. Para saber mais sobre como criar miniaturas para suas gravações de reuniões, consulte Capture ou alterar uma miniatura do vídeo, localizado em http://aka.ms/Kupj85. O cartaz também inclui um código QR para acessar essa informação. 
  

