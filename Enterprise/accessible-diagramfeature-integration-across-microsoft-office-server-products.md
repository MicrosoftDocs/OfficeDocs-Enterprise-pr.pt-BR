---
title: Diagrama acessível-integração de recursos nos produtos do Microsoft Office Server
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
description: Este artigo é uma versão de texto acessível do diagrama chamado integração de recursos nos produtos do Microsoft Office Server-SharePoint Server, Exchange Server, Lync Server e Office Online.
ms.openlocfilehash: 809a9272d7088ac069aad6b64daedfe059188247
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487790"
---
# <a name="accessible-diagram---feature-integration-across-microsoft-office-server-products"></a>Diagrama acessível-integração de recursos nos produtos do Microsoft Office Server

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado integração de recursos nos produtos do Microsoft Office Server-SharePoint Server, Exchange Server, Lync Server e Office Online.
  
O diagrama consiste em várias guias, conforme indicado pelos títulos da seção deste documento.
  
## <a name="introduction-tab"></a>Guia introdução

### <a name="illustrations-for-cross-server-features"></a>Ilustrações para recursos de servidor cruzado

Este arquivo do Visio (ou arquivo PDF multipage) tem nove guias, cada uma com informações e um diagrama sobre um recurso que funciona nos produtos do Office Server.
  
Os recursos e guias são: 
  
- Introdução
    
- Autenticação de servidor para servidor 
    
- Fotos do usuário de alta resolução 
    
- Repositório unificado de contatos 
    
- Caixas de correio local 
    
- Sincronização de tarefas do Exchange 
    
- Presença do Lync no Outlook Web App 
    
- Caixa postal
    
- Gravações de reunião 
    
Envie comentários sobre esta solução ou solicite soluções adicionais para o MODAContent@microsoft.com. 
  
### <a name="tips-for-printing"></a>Dicas para impressão

O tamanho da página de cada guia é 22 x 17 polegadas (cerca de um trimestre do tamanho de um diagrama de engenharia ANSI). Você pode imprimir essa página em duas folhas de tamanho tablóide (17 x 11) polegadas) ou quatro folhas de tamanho carta (279 x 8,5 polegadas). Se você tiver uma plotadora, poderá imprimir os cartazes no tamanho original. Caso contrário, use as etapas a seguir para imprimir em um papel menor. 
  
 **Imprimir cartazes em papel de tamanho menor**
  
1. Abra o cartaz no Visio. 
    
2. No menu **Arquivo**, clique em **Configuração de Página**. 
    
3. Na guia  **Configurar Impressão**, na seção **Papel da impressora**, selecione o tamanho de papel desejado.
    
4. Na guia **Configurar Impressão**, na seção **Zoom de impressão**, clique em **Caber em** e especifique **1 folha na horizontal por 1 folha na vertical**. 
    
5. Na guia **Tamanho da Página**, clique em **Dimensionar para caber o conteúdo do desenho** e clique em **OK**. 
    
6. No menu **Arquivo**, clique em **Imprimir**. 
    
### <a name="microsoft-tags-and-qr-codes"></a>Marcas da Microsoft e códigos QR

Use o Windows Phone ou baixe um leitor de código QR para obter mais informações sobre a implementação desses recursos. 
  
### <a name="cross-server-features"></a>Recursos entre servidores

Uma tabela mostra os recursos e os produtos do Office Server que os utilizam. Os recursos são: 
  
Autenticação de servidor para servidor. Esse recurso se aplica a: 
  
- SharePoint 
    
- Exchange
    
- Lync
    
- Office Online (anteriormente conhecido como Office Web Apps) 
    
Fotos do usuário de alta resolução. Esse recurso se aplica a: 
  
- SharePoint
    
- Exchange
    
- Lync
    
Repositório uniFicado de contatos. Esse recurso se aplica a: 
  
- Exchange
    
- Lync
    
Caixas de correio de site. Esse recurso se aplica a: 
  
- SharePoint
    
- Exchange
    
Sincronização de tarefas do Exchange. Esse recurso se aplica a: 
  
- SharePoint
    
- Exchange
    
Presença do Lync no Outlook Web App. Esse recurso se aplica a: 
  
- Lync
    
Postal. Esse recurso se aplica a: 
  
- Lync
    
Gravações de reunião. Esse recurso se aplica a: 
  
- SharePoint
    
- Lync
    
### <a name="office-web-apps-server"></a>Servidor do Office Web Apps

Office Web Apps Server é um produto do servidor Office que fornece serviços de edição e visualização de arquivos baseado no navegador para os arquivos do Office . O servidor do Office Web Apps funciona com produtos e serviços que suportam o WOPI (Open Platform Interface Protocol) do aplicativo Web. Esses produtos, conhecidos como hosts, incluem SharePoint 2013, Lync Server 2013, e Exchange Server 2013. 
  
Para saber mais sobre o Office Web Apps Server, baixe o pôster simplificado de implantação do http://aka.ms/OfficeWebAppsPosterOffice Web Apps em. 
  
## <a name="server-to-server-authentication-tab"></a>Guia Autenticação de servidor para servidor

### <a name="servicing-resource-requests-between-servers"></a>Manutenção de solicitações de recurso entre servidores

A autenticação de servidor para servidor é um novo recurso do Exchange Server 2013, do Lync Server 2013 e do SharePoint Server 2013 que permite que um servidor solicite recursos de outro servidor em nome de um usuário. Este recurso usa o protocolo de autorização aberta padrão do setor (OAuth) 2,0. A autenticação de servidor para servidor permite vários novos cenários, como descoberta eletrônica, fotos de usuário de alta resolução e caixas de correio de site. 
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="server-to-server-trust-relationships"></a>Relações de confiança de servidor para servidor

Para um servidor atender a uma solicitação de recurso de entrada, ele deve confiar no servidor que está fazendo a solicitação. Para estabelecer essa relação de confiança, você deve configurar relações de confiança de servidor para servidor. 
  
Uma relação de confiança de servidor para servidor é uma forma. Quando você configura um servidor que executa o SharePoint 2013 para confiar em um servidor do Exchange 2013, o servidor que executa as solicitações de recursos de confiança do SharePoint Server do Exchange Server, mas o servidor do Exchange não confia em solicitações de recursos do servidor executado SharePoint Server. Para uma integração perfeita, você deve estabelecer relações de confiança bidirecionais. 
  
O diagrama a seguir mostra as relações de confiança de servidor para servidor estabelecidas como relações de confiança bidirecionais. As relações de confiança bidirecionais mostradas estão entre um servidor Exchange, um SharePoint Server e um Lync Server. Cada tipo de servidor tem uma relação de confiança bidirecional com cada um dos outros dois servidores. 
  
### <a name="configuration"></a>Configuração

Para configurar uma relação de confiança de autenticação de servidor para servidor, você deve adicionar um novo emissor de token de segurança confiável que corresponda a cada servidor que envia solicitações de recursos em nome dos usuários. Cada tipo de servidor tem um ponto de extremidade de metadados do JavaScript Object Notation (JSON) que contém informações de configuração e uma parte pública do certificado de autenticação de token de acesso. Parte da configuração de uma confiança de autenticação de servidor para servidor é especificar o ponto de extremidade de metadados JSON do outro servidor. 
  
A tabela a seguir lista o ponto de extremidade de metadados JSON para cada servidor. A tabela mostra: 
  
- Um servidor Exchange com um ponto de extremidade de metadados<server name>JSON de https:///autodiscover/Metadata/JSON/1 
    
- Um Lync Server com um ponto de extremidade de metadados<server name>JSON de https:///Metadata/JSON/1 
    
- Um servidor do SharePoint com um ponto de extremidade de<web app name>metadados JSON de https:///_layouts/15/Metadata/JSON/1 
    
### <a name="example-how-server-to-server-authentication-works-for-ediscovery-between-sharepoint-and-exchange"></a>Exemplo: como a autenticação de servidor para servidor funciona para descoberta eletrônica entre o SharePoint e o Exchange

Neste exemplo, o servidor Exchange 2013 foi configurado para confiar no servidor que executa o SharePoint Server com uma relação de confiança de servidor para servidor. Um centro de descoberta eletrônica no servidor que executa o SharePoint Server foi configurado para incluir dados em caixas de correio no servidor Exchange. 
  
As solicitações de recursos em outro servidor têm a forma de tokens de acesso que são enviados para o serviço de servidor Web no servidor de destino. 
  
O diagrama a seguir mostra como as consultas e os tokens de acesso trafegam entre os dois servidores. 
  
1. Um administrador de descoberta eletrônica envia uma consulta para o servidor que executa o SharePoint Server que inclui recursos em um servidor Exchange. 
    
2. O servidor que executa o SharePoint Server gera um token de acesso, identificando o usuário e o recurso solicitado. 
    
3. O servidor que executa o SharePoint Server envia o token de acesso ao servidor Exchange. 
    
4. O servidor do Exchange valida o token de acesso e envia os resultados da consulta. 
    
5. O servidor que executa o SharePoint Server envia os resultados da consulta de descoberta eletrônica para o computador do administrador de descoberta eletrônica. 
    
## <a name="high-resolution-user-photos-tab"></a>Guia fotos do usuário de alta resolução

### <a name="larger-profile-picture-used-across-all-office-applications"></a>Imagem de perfil maior usada em todos os aplicativos do Office

Usando a guia **fotos do usuário de alta resolução** , você pode armazenar fotos até 648 x 648 pixels no Exchange 2013. Eles podem ser acessados por aplicativos cliente, incluindo Outlook, Outlook Web App, SharePoint 2013, Lync 2013 e clientes de email móveis. Uma foto de baixa resolução também é armazenada no Active Directory.
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="configuration"></a>Configuração

Configurar autenticação de servidor para servidor: 
  
- Entre o Exchange 2013 e o SharePoint 2013. 
    
- Entre o Exchange 2013 e o Lync 2013. 
    
 **No Exchange Server 2013**
  
- Inicie e configure o serviço de descoberta automática do Exchange 2013. 
    
- Definir URLs externas para o SharePoint. Estas são as URLs que o SharePoint usa quando acessa fotos no Exchange. 
    
 **No SharePoint Server 2013**
  
- Instale a API gerenciada dos serviços Web do Exchange. Use o GacUtil para carregar o Microsoft. Exchange. WebServices. dll no cache de assembly global (GAC). 
    
- Use o Windows PowerShell para configurar a sincronização de fotos com o Exchange. 
    
 **Como funciona**
  
- Os usuários carregam uma foto usando a página minha conta no Outlook Web App (OWA) ou configurações de conta no Outlook 2013. 
    
- O Exchange redimensiona automaticamente a imagem para uso pelo AD DS (48 x 48 pixels) ou por outros aplicativos do Office, incluindo o OWA e o cliente do Outlook 2013 (96 x 96 pixels). 
    
Os usuários podem carregar imagens com intervalos de pixels de 48 × 48 para 648 × 648. As fotos são redimensionadas: 
  
- 64 × 64 é usado para a miniatura de anúncio. 
    
- 96 × 96 é usado para Outlook Web Access, Outlook, Lync Web Access e Lync 2013. 
    
- 648 × 648 é usado para Lync Web Access e Lync 2013. 
    
Por exemplo, exemplos de scripts de configuração, consulte o artigo de blog de Jens Trier escapa: 
  
- Usando fotos de alta resolução do Exchange 2013 do SharePoint Server 2013 (http://aka.ms/Bhr4d2) 
    
- Integração do Exchange 2013 e do Lync Server 2013 (http://aka.ms/Pn08dw) 
    
O cartaz também contém códigos QR para esses dois artigos de blog. 
  
O diagrama a seguir mostra como um usuário pode atualizar uma foto para ser usada em todos os aplicativos do Office. 
  
1. O usuário atualiza a foto no Outlook, SharePoint ou Lync. Após a atualização, a foto atualizada é usada em todos os aplicativos do Office. 
    
2. O usuário pode usar várias maneiras diferentes de atualizar uma foto: 
    
3. 
  - Cliente do Outlook ou Outlook Web App (OWA) pela porta HTTP 443 para um servidor de acesso para cliente do Exchange. 
    
  - Meu site sobre HTTP ou HTTPS para um SharePoint Server. O SharePoint armazena em cache o usuário no banco de dados de meusite (https: 443). As interfaces do SharePoint Server com o servidor de acesso para cliente do Exchange usando URLs externas definidas no Exchange. 
    
  - Lync 2013 cliente, que mantém uma getConnection com o Exchange Server para obter atualizações de foto (HTTPS Get Request-443). 
    
4. O servidor de acesso para cliente do Exchange se conecta ao servidor de caixa de correio do Exchange usando a comunicação interna do Exchange. 
    
5. O servidor de caixa de correio do Exchange usa o Exchange 2013 para empurrar a foto do usuário de alta resolução para o AD DS (LDAP: 389). 
    
6. A foto é sincronizada a partir do AD DS (serviços de domínio Active Directory) para o serviço de catálogo de endereços (ABS) do Lync no Lync Server para que os clientes herdados possam obter a mesma foto (LDAP: 389). 
    
7. O cliente herdado do Lync agora tem acesso à foto. 
    
## <a name="unified-contact-store-tab"></a>Guia repositório uniFicado de contatos

### <a name="exchange-2013-is-the-contact-store-for-all-office-applications"></a>O Exchange 2013 é o repositório de contatos para todos os aplicativos do Office

O uso do repositório uniFicado de contatos (UCS) fornece uma experiência de contato consistente nos produtos do Microsoft Office. Os usuários armazenam todas as informações de contato em suas caixas de correio do Exchange 2013. As mesmas informações de contato estão disponíveis globalmente no Lync, no Exchange, no Outlook e no Outlook Web App. 
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
 **Configuração**
  
- Configure a autenticação de servidor para servidor entre o Exchange Server 2013 e o Lync Server 2013. 
    
- No Lync 2013, habilite a política de repositório unificado de contatos (o padrão é habilitado). 
    
Por exemplo, exemplos de scripts de configuração, consulte o artigo do blog de Jens Trier escapa: 
  
- Integração do Exchange 2013 e do Lync Server 2013 (http://aka.ms/Oyg7fh) 
    
 **Como funciona**
  
- Os contatos do Lync para um usuário são migrados para o Exchange 2013 automaticamente quando o usuário faz logon com o Lync 2013. 
    
- Os usuários podem acessar e gerenciar seus contatos do Lync do Lync 2013, Outlook 2013 ou Outlook Web Access. 
    
Os contatos de um usuário são migrados automaticamente para o servidor Exchange 2013 quando o usuário: 
  
1. Foi atribuída uma política de serviços de usuário que tem UcsAllowed definido como **true**. 
    
2. Foi provisionado com uma caixa de correio do Exchange 2013 e entrou na caixa de correio pelo menos uma vez. 
    
3. Entra no Lync usando um cliente avançado do Lync 2013. 
    
Entra no Lync usando um cliente avançado do Lync 2013. 
  
1. Entrar na sua caixa de correio do Exchange 2013 no servidor de acesso para cliente do Exchange, usando um cliente do Outlook ou o Outlook Web App (OWA) sobre HTTPS/443. O servidor de caixa de correio do Exchange usa uma comunicação interna do Exchange para se comunicar com o servidor de acesso para cliente do Exchange. 
    
2. Entrar no Lync 2013. O cliente Lync contata o Lync Server sobre SIP/5061 HTTPS/443. 
    
3. O cliente Lync informa ao Lync Server que o usuário está habilitado para o repositório uniFicado de contatos sobre SIP/5061. 
    
4. O Lync Server usa o serviço de armazenamento do Lync para migrar os contatos do usuário para o Exchange 2013 no servidor de acesso para cliente do Exchange. 
    
5. O usuário deve sair e entrar no Lync 2013 para que as alterações sejam exibidas (não mostradas no diagrama). 
    
6. Após a migração, o cliente Lync usa os serviços Web do Exchange (EWS) para ler e manter os contatos do Lync. 
    
## <a name="site-mailboxes-tab"></a>Guia caixas de correio do site

### <a name="a-central-filing-cabinet-for-emails-and-documents"></a>Um gabinete de arquivamento central para emails e documentos

As caixas de correio de site melhoram a colaboração e a produtividade do usuário, permitindo o acesso a documentos armazenados no SharePoint e mensagens de email armazenadas no Exchange, usando a mesma interface de cliente. 
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
 **Configuração**
  
Configuração do SharePoint: 
  
- Configure a sincronização de perfil de usuário no farm do SharePoint. 
    
- Configure o aplicativo de serviço de gerenciamento de aplicativos no farm do SharePoint. 
    
- Configure o SSL para a zona padrão para oferecer suporte à autenticação de servidor para servidor. 
    
- Instale a API EWS nos servidores que executam o SharePoint 2013. 
    
- Estabeleça a confiança OAuth e as permissões de serviço em servidores que executam o SharePoint 2013. 
    
Configuração do Exchange: 
  
- Estabeleça a confiança OAuth e as permissões de serviço nos servidores Exchange. 
    
- Criar política de provisionamento de caixa de correio de site. 
    
- Configure o prefixo do nome da caixa de correio do site (opcional). 
    
 **Como funciona**
  
Uma caixa de correio de site é composta funcionalmente pela associação ao site do SharePoint 2013 (proprietários e membros), armazenamento compartilhado através de uma caixa de correio do Exchange 2013 para emails e um site do SharePoint 2013 para documentos e uma interface de gerenciamento que lida com as necessidades de provisionamento e ciclo de vida. 
  
O diagrama a seguir mostra os usuários que usam caixas de correio de site para acessar mensagens de email no Outlook e documentos armazenados no SharePoint. 
  
1. Os usuários podem acessar os documentos do site de equipe do SharePoint por meio das caixas de correio do site no Outlook 2013 Pro Plus. 
    
2. Os usuários também podem ler emails na caixa de entrada de caixa de correio do site do site de equipe do SharePoint. 
    
3. Os emails são armazenados em caixas de correio de site em servidores Exchange. 
    
4. Os documentos são armazenados em caixas de correio de site em servidores do SharePoint. 
    
5. Os metadados do conteúdo no site do SharePoint são sincronizados com o Exchange usando a API de transferência de estado de representação (REST) sobre HTTPS. 
    
### <a name="provisioning-and-management"></a>Provisionamento e gerenciamento

As caixas de correio de site são provisionadas e gerenciadas por meio do SharePoint 2013. Há recursos do SharePoint e do Exchange para provisionamento e gerenciamento. 
  
#### <a name="sharepoint"></a>SharePoint

Um diagrama mostra os componentes do SharePoint necessários para provisionar a caixa de correio do site, incluindo: 
  
- Aplicativo da Caixa de Correio do Site 
    
- Membros e proprietários do site de equipe 
    
- Política de ciclo de vida do site de equipe 
    
Para provisionar uma nova caixa de correio de site, instale o aplicativo de caixa de correio de site no site de equipe e acesse o aplicativo pelo menos uma vez. 
  
A associação de site do SharePoint determina quem tem acesso à caixa de correio do site. 
  
A retenção de caixa de correio de site segue a mesma política de ciclo de vida configurada para o site do SharePoint ao qual está associada. 
  
#### <a name="exchange"></a>Exchange

O diagrama mostra a política de provisionamento de caixa de correio de site. Este é o componente do Exchange necessário para provisionar a caixa de correio do site.
  
No servidor Exchange, você pode definir as políticas de provisionamento de caixa de correio de site. Essas políticas regem as características de email enviadas e recebidas da caixa de correio do site, o tamanho da caixa de correio do site no servidor Exchange e permite que você defina um prefixo para endereços de email de caixa de correio de site. 
  
Para implantações locais do Exchange, você também precisa procurar e excluir periodicamente as caixas de correio de site que foram marcadas para exclusão por meio da política de ciclo de vida do SharePoint. 
  
## <a name="exchange-task-synchronization-tab"></a>Guia de sincronização de tarefas do Exchange

### <a name="synchronizing-tasks-among-sharepoint-server-2013-project-server-2013-and-exchange-server-2013"></a>Sincronizando tarefas entre o SharePoint Server 2013, o Project Server 2013 e o Exchange Server 2013

Usando a sincronização de tarefas do Exchange, você pode sincronizar tarefas no SharePoint Server 2013 e no Project Server 2013 com o Exchange Server 2013. Os usuários podem exibir e gerenciar suas tarefas no Outlook 2013 ou em meu site. 
  
 **Produtos de servidor**
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Project Server 2013 (opcional) 
    
 **Pré-requisitos**
  
No Exchange 2013: 
  
- Configurar a confiança OAuth e a permissão de serviço. 
    
No SharePoint Server 2013: 
  
- Aplicativo de serviço de perfil de usuário. 
    
- Aplicativo de serviço de gerenciamento de trabalho. 
    
- Search (isso é necessário para tarefas no SharePoint Server 2013). Configure com rastreamentos contínuos e rastreamentos incrementais. 
    
- Secure Sockets Layer (SSL) é necessário. 
    
- Os usuários têm meus sites existentes. 
    
- Aplicativo de serviço do Project (para agregar tarefas do Project Server). 
    
- API de serviços Web do Exchange em cada servidor Web front-end (este é um arquivo. exe separado para download que deve ser instalado). 
    
No Project Server 2013: 
  
- Criar sites do aplicativo Web do projeto. 
    
 **Como funciona**
  
Quando o modo de exibição minhas tarefas nos meus sites é aberto ou atualizado: 
  
- O aplicativo de serviço de gerenciamento de trabalho sincroniza entre o SharePoint Server e o Project Server. 
    
- O trabalho de timer de sincronização do Exchange chama o aplicativo de serviço de gerenciamento de trabalho para sincronizar tarefas com o Exchange Server 2013. 
    
- A página minhas tarefas nos meus sites é atualizada. 
    
Quando o trabalho de timer de sincronização do Exchange é executado: 
  
- O aplicativo de serviço de gerenciamento de trabalho sincroniza entre o SharePoint Server, o Project Server e o Exchange Server. 
    
O diagrama a seguir mostra a interação entre o SharePoint Server 2013, o Exchange Server 2013, o Outlook 2013 e o Project Server 2013. 
  
O SharePoint Server 2013 executa os seguintes trabalhos e aplicativos: 
  
- Aplicativo de serviço de perfil de usuário. 
    
- Aplicativo de serviço de pesquisa. 
    
- Aplicativo de serviço de gerenciamento de trabalho, que é descrito abaixo. 
    
- Trabalho de timer de sincronização do Exchange, que é descrito abaixo. 
    
- O SharePoint Server 2013 contém o meu site e outros sites do usuário e executa várias tarefas do usuário. 
    
- O SharePoint Server 2013 contém um índice de pesquisa. 
    
O Exchange Server 2013 contém o seguinte: 
  
- Banco de dados do Exchange com informações de email do usuário 
    
- Tarefas de sincronização 
    
O Outlook 2013 mostra o seguinte: 
  
- Os usuários podem optar por sincronizar suas tarefas, que são descritas abaixo. 
    
- Os usuários podem exibir e editar tarefas no Outlook. 
    
O Project Server 2013 mostra o seguinte: 
  
- Banco de dados do Project 
    
- Sites do Project Web Access com tarefas 
    
O aplicativo de serviço de gerenciamento de trabalho: 
  
- Agrega tarefas de listas do SharePoint e listas de tarefas do projeto (não sincroniza tarefas com o Exchange Server). 
    
- Sincroniza quando os usuários exibem o meu site. 
    
- Mantém a lista de usuários que optam por você. 
    
- Sincroniza o próximo lote de usuários. 
    
O trabalho de timer de sincronização do Exchange: 
  
- Determina o próximo lote de usuários. 
    
- Garante que todos os usuários sejam constantemente sincronizados. 
    
- Inicia a chamada para o aplicativo de serviço de gerenciamento de trabalho para sincronizar tarefas com o Exchange Server para usuários que são aceitos somente. 
    
Aceitar 
  
- Os usuários devem optar por sincronizar suas tarefas do Exchange com o meu site ou com suas tarefas do SharePoint Server 2013 e do Project Server 2013 com o Exchange Server 2013. 
    
## <a name="lync-presence-in-office-2013-outlook-web-app-and-sharepoint-server-tab"></a>Presença do Lync no Office 2013, no Outlook Web App e na guia do SharePoint Server

### <a name="lync-server-as-the-authoritative-source-of-presence-information"></a>Lync Server como a fonte autoritativa de informações de presença

Usando as informações de presença do Lync, você pode ter uma visão consistente das informações de presença entre o Lync, o Outlook e o SharePoint. O Outlook consulta informações de presença diretamente do Lync, que é instalado localmente no mesmo computador que o Outlook. Quando os usuários exibem informações de presença no SharePoint Server, as informações de presença são consultadas pelo Lync no computador local.
  
Produtos de cliente: 
  
- Outlook 2013 
    
- Lync 2013 
    
Produtos de servidor: 
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
- SharePoint Server 2013 
    
 **Como funciona**
  
Desde que o Lync 2013 esteja instalado no computador local do usuário, o Outlook e o SharePoint Server exibirão automaticamente as informações de presença dos usuários. 
  
Para usuários do Outlook Web App, o Exchange CAS consulta presença em nome do usuário. 
  
 **Há dois diagramas de acompanhamento**
  
O primeiro mostra como um usuário entra no Outlook Web App e, em seguida, procura informações de presença no Lync Server do Exchange. 
  
1. O usuário entra no Outlook Web App. O computador cliente acessa o servidor de acesso para cliente (CAS) do Exchange sobre HTTPS/443 e também chama o servidor de caixa de correio do Exchange com uma comunicação interna do Exchange. 
    
2. O usuário entra em suas caixas de correio do Exchange 2013 e o Exchange CAS consulta o Lync Server para obter informações de presença sobre SIP/MTLS: 5061. 
    
Para obter mais informações, consulte [integraNdo o Microsoft Lync Server 2013 e o Microsoft Outlook Web App 2013](https://go.microsoft.com/fwlink/?LinkId=313522).
  
O segundo diagrama mostra como o Outlook e o SharePoint Server usam o Lync 2013 para exibir as informações de presença dos usuários. 
  
1. O usuário entra no Lync 2013 sobre SIP/TLS: 5061, que chama o Lync Server. 
    
2. R. O usuário entra em suas caixas de correio do Exchange 2013 por meio do Outlook no Office 2013. O computador cliente acessa o servidor de acesso para cliente (CAS) do Exchange sobre HTTPS/443 e também chama o servidor de caixa de correio do Exchange com uma comunicação interna do Exchange. 
    
3. R. O Outlook chama o Lync instalado no mesmo computador que o Outlook para recuperar informações de presença. 
    
4. A.b.c.. O usuário se conecta ao meusite do SharePoint por HTTP ou HTTPS, que chama o SharePoint Server. 
    
5. A.b.c.. O Internet Explorer chama o Lync, que é instalado no mesmo computador que o navegador, para recuperar informações de presença. 
    
## <a name="voicemail-tab"></a>Guia caixa postal

### <a name="exchange-um-is-the-voicemail-system-for-lync-server"></a>UM do Exchange é o sistema de caixa postal para o Lync Server

A caixa postal permite que um chamador deixe uma caixa postal para os usuários do Lync usando a uniFicação de mensagens (UM) do Exchange. 
  
Produtos de cliente: 
  
- Lync 2013 
    
- Dispositivo PSTN (PBX, celular, POTS) 
    
Produtos de servidor: 
  
- Exchange Server 2013 
    
- Exchange Server 2013 
    
 **Como funciona**
  
Quando uma chamada não é atendida pelo receptor em qualquer um dos pontos de extremidade ativos do destinatário da chamada, o Lync Server encaminha a chamada para a caixa postal no Exchange UM (ou seja, servidor de caixa de correio do Exchange). 
  
O diagrama a seguir mostra o roteamento de chamadas para dois cenários: 
  
- O chamador inicia uma chamada usando o Lync 2013. 
    
- O chamador inicia uma chamada usando o dispositivo PSTN (PBX, celular, POTS). 
    
O chamador inicia uma chamada usando o Lync 2013: 
  
1. O chamador A inicia uma chamada para o receptor usando o Lync 2013. A chamada é iniciada e enviada ao Lync Server. 
    
2. A chamada é roteada para o servidor local do Lync do destinatário da chamada. 
    
3. O Lync Server toca os pontos de extremidade ativos do receptor da chamada no Lync 2013. 
    
4. Quando a chamada não é atendida, a chamada é roteada para a caixa postal (UM do Exchange) na autoridade de certificação do Exchange (roteador de chamada). 
    
O chamador inicia uma chamada usando o Lync 2013: 
  
1. O chamador B disca o número de telefone do receptor usando PSTN. 
    
2. A chamada PSTN é roteada do gateway IP para o servidor de mediação, que é um Lync Server. 
    
3. O servidor de mediação routs a chamada para o servidor local do Lync do chamado. 
    
4. O Lync Server toca os pontos de extremidade ativos do receptor da chamada no Lync 2013. 
    
5. Quando a chamada não é atendida, a chamada é roteada para a caixa postal (UM do Exchange) na autoridade de certificação do Exchange (roteador de chamada). 
    
## <a name="meeting-recordings-tab"></a>Guia gravações de reunião

### <a name="publish-your-meeting-recordings-on-your-sharepoint-team-site"></a>Publicar suas gravações de reunião no site de equipe do SharePoint

As gravações de reunião são um componente principal da comunicação unificada. Uma boa maneira de compartilhar suas gravações de reunião é usar as bibliotecas de ativos do SharePoint em seus sites de equipe para armazenar suas gravações de reunião. 
  
Produtos de cliente: 
  
- Lync 2013 
    
Produtos de servidor: 
  
- Produtos de servidor: 
    
- SharePoint 2013 
    
Pré-requisitos 
  
- Lync 2013 — a gravação da reunião é um recurso do lado do cliente no Lync 2013. 
    
- SharePoint 2013 — você tem o site de equipe onde deseja armazenar as gravações de reunião que já estão funcionando. 
    
 **O que é gravado?**
  
Os itens a seguir são registrados em um arquivo MP4 durante a reunião (cada marcador é precedido de um ícone que representa o tipo de gravação): 
  
- Todos os áudio 
    
- Vídeo do orador ativo (se usado) 
    
- Vídeo panorâmico (se usado) 
    
- Todo o conteúdo apresentado 
    
- Mensagens instantâneas * 
    
* Apenas as mensagens instantâneas dentro da reunião estão incluídas. Qualquer mensagem ponto a ponto entre os participantes da reunião não faz parte da reunião e, portanto, não é capturada. 
  
O pôster inclui dois diagramas para dois cenários diferentes: 
  
- Preparando para publicar gravações de reunião 
    
- Gravar e publicar uma reunião usando o cliente Lync 
    
### <a name="preparing-for-publishing-meeting-recordings"></a>Preparando para publicar gravações de reunião

O diagrama mostra o SharePoint Server 2013 com um site de equipe, centro de Administração Central e servidor de serviços de informações da Internet (IIS). 
  
O site de equipe contém: 
  
- O aplicativo da biblioteca de ativos. 
    
- Biblioteca de ativos de reuniões, ao qual os membros da equipe enviam gravações de reunião. 
    
O centro de Administração Central contém as configurações gerais do aplicativo Web. 
  
O servidor IIS contém as configurações do IIS. 
  
Para se preparar para publicar gravações de reunião: 
  
1. Em seu site de equipe do SharePoint, adicione o aplicativo da biblioteca de ativos. Opcionalmente, se você não conseguir carregar gravações de reunião devido a restrições de tamanho ou tempo limite de conexão, execute as etapas 2 e 3 adicionais. 
    
2. Na administração central do SharePoint, altere a configuração de tamanho máximo de carregamento para o aplicativo Web que contém o conjunto de sites de equipe. 
    
3. Nas configurações do servidor IIS, aumente o tempo limite de conexão do IIS para o site que contém o conjunto de sites de equipe. 
    
 **Bibliotecas de ativos digitais**
  
Bibliotecas de ativos digitais são bibliotecas de ativos que contêm vídeos com determinadas implicações de capacidade e desempenho. Para obter mais informações, consulte Plan Digital Asset Libraries in SharePoint Server 2013 localizado http://aka.ms/O1vq5wem. O cartaz também inclui um código QR para acessar essas informações. 
  
### <a name="recording-and-publishing-a-meeting-using-the-lync-client"></a>Gravar e publicar uma reunião usando o cliente Lync

O diagrama mostra um usuário usando o Lync para ingressar em uma reunião. A reunião é registrada usando o cliente Lync, que cria um arquivo MP4 com o conteúdo da reunião. A gravação MP4 é salva na pasta de gravação do Lync em seu computador. Você pode mover a gravação MP4 para a sua biblioteca de ativos de reuniões, na qual você pode inseri-la em um wiki, em uma página do SharePoint ou em um blog. 
  
 **Para gravar e publicar uma reunião usando o cliente Lync**
  
1. Iniciar a gravação da reunião usando o cliente Lync. 
    
2. O conteúdo da reunião é gravado em um arquivo MP4 durante a reunião. 
    
3. Depois que a reunião terminar, a gravação MP4 aparecerá na pasta gravação em seu computador (C:\\usuários\\<username>\\vídeos\\Lync Records). Opcionalmente, você pode personalizar a gravação da reunião usando o aplicativo Gerenciador de gravação do Lync que é instalado com o cliente Lync. 
    
4. Arraste e solte a gravação de reunião na sua biblioteca de ativos do SharePoint. 
    
5. Opcional: depois que a gravação estiver em sua biblioteca de ativos, você poderá inseri-la em qualquer página do SharePoint. Para obter mais informações sobre esta etapa, confira a entrada de blog do Office 365, crie e publique vídeos de treinamento com o SharePoint http://aka.ms/R61q35e o Lync Online, localizado em. 
    
 **Miniaturas de vídeo**
  
As miniaturas de vídeo melhoram a aparência da sua biblioteca de ativos. Para saber mais sobre como criar miniaturas para suas gravações de reunião, confira capturar ou alterar uma miniatura de http://aka.ms/Kupj85vídeo, localizada em. O cartaz também inclui um código QR para acessar essas informações. 
  

