---
title: Visão geral do híbrido autenticação moderno e pré-requisitos para usá-lo com Skype local para os servidores de negócios e do Exchange
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 8/27/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: Autenticação moderna é um método de gerenciamento de identidade que ofereça mais seguro de autenticação e autorização. Ele está disponível para implantações híbridas, do Skype para Business server local e Exchange server local, bem como a divisão de domínios Skype para híbridas de negócios. Este artigo apresenta links para relacionadas a documentos sobre pré-requisitos, instalação/desabilitar a autenticação moderno e para algumas das informações relacionadas do cliente (clientes do Outlook e Skype ex.).
ms.openlocfilehash: 3d510c6d3e9f8ff885279dc008eeefb5d1014639
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240586"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Visão geral do híbrido autenticação moderno e pré-requisitos para usá-lo com Skype local para os servidores de negócios e do Exchange

Autenticação moderna é um método de gerenciamento de identidade que ofereça mais seguro de autenticação e autorização. Ele está disponível para implantações híbridas do Office 365 do Skype para Business server local e Exchange server local, bem como, Skype de divisão de domínios para híbridas de negócios. Este artigo apresenta links para relacionadas a documentos sobre pré-requisitos, instalação/desabilitar a autenticação moderno e para algumas das informações relacionadas do cliente (clientes do Outlook e Skype ex.). 
  
- [O que é autenticação moderno?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [O que muda quando eu uso moderno autenticação?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Verificar o status de autenticação moderno do seu ambiente local](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [Você cumpre os pré-requisitos de autenticação moderno?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [O que mais preciso saber antes de começar?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Lista das URLs de autenticação moderno](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>O que é autenticação moderno?
<a name="BKMK_WhatisModAuth"> </a>

Quando falamos sobre a comunicação entre um cliente (por exemplo, seu laptop ou seu telefone) e um servidor, a Microsoft usa a frase 'Moderno authentication'.
  
Autenticação moderna é um termo geral para uma combinação de métodos de autorização e autenticação, bem como algumas medidas de segurança que contam com políticas de acesso que você já esteja familiarizado com. Ela inclui:
  
- **Métodos de autenticação**: autenticação multifator; Autenticação baseada em certificado do cliente; e a biblioteca de autenticação do Active Directory ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Métodos de autorização**: implementação de autorização aberta (OAuth) da Microsoft. 
    
- **Políticas de acesso condicional**: gerenciamento de aplicativo de celular (MAM) e o acesso condicional do Azure Active Directory. 
    
Gerenciamento de identidades de usuário com a autenticação moderno oferece aos administradores muitas ferramentas diferentes para usar quando ele trata de proteger recursos e oferece mais seguros métodos de gerenciamento de identidades para tanto no local (Exchange e Skype for Business), híbrida do Exchange e Skype para cenários de divisão/híbrida-domain comerciais.
  
Lembre-se de que, como Skype para negócios trabalha junto com o Exchange, o comportamento de logon Skype para o cliente de negócios, os usuários verão será afetado pelo status moderno autenticação do Exchange. Isso também se aplicará se você tiver um Skype para o híbrido de divisão de domínios de negócios. Além disso, o tipo do Skype para o híbrido de negócios que suporta o uso da autenticação moderno geralmente é chamado um 'split-domínio' (em um domínio dividido, você tem Skype para Business Online e o Skype para negócios prem e os usuários estão hospedados em ambos os locais).
  
 **Importante** Você sabia que, a partir de agosto de 2017, todos os novos locatários do Office 365 que incluem Skype para negócios online e Exchange online terá autenticação moderno habilitado por padrão? Inquilinos pré-existente não terão uma alteração em seu estado de MA padrão, mas todos os locatários novos automaticamente suportam o conjunto expandido de recursos de identidade, que você verá listadas acima. Para verificar o status da sua MA Skype para negócios online, você pode usar o Skype para PowerShell online de negócios com credenciais de Administrador Global. Execute 'Get-CsOAuthConfiguration' para verificar a saída do - ClientADALAuthOverride. Se - ClientADALAuthOverride é 'permitido' autenticação do seu moderno está ligado. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>O que muda quando eu uso moderno autenticação?
<a name="BKMK_WhatChanges"> </a>

Ao usar a autenticação moderno com Skype local para negócios ou Exchange server, você ainda estiver *autenticar* os usuários no local, mas a história de *Autorizar* o acesso às alterações de recursos (como emails ou arquivos). É por isso que, embora esteja autenticação moderno sobre a comunicação do cliente e servidor, as etapas executadas durante a configuração de resultado MA no evoSTS (um serviço de Token segurança usada pelo Windows Azure AD) que está sendo definido como servidor de autenticação para Skype para negócios e do Exchange server local. 
  
A alteração evoSTS permite que o seu local servidores tirar vantagem do OAuth (emissão de tokens) para autorizar seus clientes e também permite que seu local usar métodos de segurança comuns na nuvem (como a autenticação multifator). Além disso, o evoSTS emite tokens que permitem aos usuários solicitar acesso a recursos sem fornecer suas senhas como parte da solicitação. Não importa onde os usuários estão hospedados (do online ou local), e não importa qual local hospeda o recurso necessário, EvoSTS se tornará o núcleo da autorização de usuários e clientes após configurar a autenticação moderno.
  
Aqui está um exemplo de I significado. Se precisar de Skype para o cliente de negócios acessar o Exchange server para obter informações de calendário em nome de um usuário, ele usa a biblioteca de autenticação do Active Directory (ADAL) para fazê-lo. ADAL é uma biblioteca de código projetada para disponibilizar recursos protegidos em seu diretório para aplicativos cliente usando OAuth tokens de segurança. ADAL funciona com OAuth para verificar declarações e também para trocar tokens (em vez de senhas), para conceder acesso a um usuário a um recurso. No passado, a autoridade de uma transação como esse – o servidor que sabe como validar as declarações de usuário e emitir os tokens needed-- pode ter sido um serviço de Token de segurança local ou até mesmo Active Directory Federation Services. No entanto, autenticação Moderno centraliza essa autoridade com o Windows Azure Active Directory (AD Azure) na nuvem.
  
Isso também significa que, mesmo que seu servidor Exchange e Skype para ambientes de negócios podem estar totalmente local, o servidor de autorizar será on-line e seu ambiente local deve ter a capacidade de criar e manter uma conexão ao seu escritório assinatura 365 na nuvem (e a instância do Azure Active Directory que sua assinatura usa como seu diretório).
  
O que não é alterado? Se você estiver em um híbrido de divisão de domínios ou usando Skype para negócios e do Exchange server local, todos os usuários devem primeiro autenticar *no local* . Em uma implementação híbrida de autenticação moderno, Lyncdiscovery e Autodiscovery apontam para seu servidor local. 
  
 **Importante** Se você precisa saber o Skype específico para topologias de negócios compatível com o MA, que é [documentado direita aqui](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Verificar o status de autenticação moderno do seu ambiente local
<a name="BKMK_CheckStatus"> </a>

Como autenticação moderno altera o servidor de autorização usado quando os serviços utilizam OAuth/S2S, você precisa saber se a autenticação moderno está ativada ou desativada para seu Skype para ambiente de negócios e do Exchange. Você pode verificar o status em seu Exchange ou Skype para servidores de negócios, localmente, executando o comando Get-CSOAuthConfiguration no PowerShell. Se o comando retorna uma propriedade de 'OAuthServers' vazia, autenticação moderno está desabilitada.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Você cumpre os pré-requisitos de autenticação moderno?

Verifique se e verifique estes itens fora de sua lista antes de continuar:
  
- **Skype para negócios específicos**
    
  - Todos os servidores devem ter SFB Server 2015 CU5 ou posterior
    
  - **Exceção** - aparelho de filial de persistência (SBA) pode ser na versão atual (com base no Lync 2013) 
    
  - O domínio SIP é adicionado como um domínio federado no Office 365
    
  - Todos os SFB Front-Ends devem ter conexões de saída para a internet, como URLs de autenticação do Office 365 (TCP 443) e a raiz do certificado bem conhecido CRLs (TCP 80) listadas nas linhas 1 e 2 da seção 'Office 365 autenticação e identidade' do IP e [URLs do Office 365 intervalos de endereços](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E).
    
 **Observação** Se seu Skype para servidores front-end de negócios usar um servidor proxy para acessar a Internet, o proxy server IP e número de porta usado deve ser inserido na seção Configuração do arquivo Web. config para cada front-end. 
  
- c:\Program files\Skype para Business Server 2015\Web Components\Web ticket\int\web.config
    
- c:\Program files\Skype para Business Server 2015\Web Components\Web ticket\ext\web.config
    
- \</System.IdentityModel.Services\>
    
     \<System.NET\> 
    
     \<defaultProxy\> 
    
     \<proxy 
    
     proxyaddress = "http://192.168.100.60:8080" 
    
     bypassonlocal = "true" 
    
     /\> 
    
     \</defaultProxy\> 
    
     \</System.NET\> 
    
    \</ configuração\>
    
 **Importante** Certifique-se de se inscrever no RSS feed para as [URLs do Office 365 e intervalos de endereços IP](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) permanecer atualizado com as listagens mais recentes de URLs necessárias. 
  
- **Servidor Exchange específico**
    
  - Você estiver usando o Exchange server 2013 CU19 e para cima, ou Exchange server 2016 CU8 e para cima.
    
  - Não há nenhum Exchange server 2010 no ambiente.
    
  - Descarregamento de SSL não está configurado. Nova criptografia e terminação SSL é suportada.
    
  - No caso de seu ambiente utiliza uma infra-estrutura de servidor proxy para permitir que os servidores para se conectar à Internet, certifique-se de que todos os servidores do Exchange tem o servidor de proxy definido na propriedade [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) .
    
- **Requisitos de protocolo e o cliente do Exchange**
  
  - Os seguintes clientes suportam moderna autenticação:

  |**Clientes**|**Protocolo primário**|**Anotações**|
  |:-----|:-----|:-----|
  |Outlook 2013 e Outlook 2016  <br/> |MAPI sobre HTTP  <br/> |MAPI sobre HTTP deve ser habilitada no Exchange a fim de aproveitar a autenticação moderna com estes clientes (geralmente habilitada ou True para novas instalações do Exchange 2013 Service Pack 1 e superior); Para obter mais informações, consulte [moderno como funciona a autenticação para aplicativos de cliente do Office 2013 e Office 2016](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Certifique-se de que você está executando a compilação de necessária mínima do Outlook; consulte [as atualizações mais recentes para versões do Outlook que usam o Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 para Mac  <br/> |Serviços Web do Exchange  <br/> |  <br/> |
  |Outlook para iOS e Android  <br/> |  <br/> |Consulte [híbrida usando autenticação moderno com o Outlook para iOS e Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) para obter mais informações.  <br/> |
  |Clientes do Exchange ActiveSync (por exemplo, iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |Para clientes do Exchange ActiveSync que oferecem suporte à autenticação moderna, você deverá recriar o perfil para alternar entre a autenticação básica para autenticação moderna.  <br/> |

- **Pré-requisitos gerais**
    
  - Se você usar o ADFS, você deve ter o Windows 2012 R2 ADFS 3.0 e acima para federação
    
  - Suas configurações de identidade são qualquer um dos tipos suportados pelo AAD conectar (como sincronização de hash de senha, autenticação de passagem, STS suportados pelo Office 365 no local, etc.)
    
  - Você tem AAD conectar configurado e funcionando para sincronização e replicação de usuário.
    
  - Você verificou que híbrida está funcionando entre seu local e o Office 365:
    
  - Declaração de suporte oficial do Exchange híbrido informa que você deve ter CU atual ou CU atual - 1.
    
  - Tornar-se de que ambas as um usuário de teste de local, bem como um usuário de teste híbridos hospedados no Office 365, pode fazer logon o Skype para o cliente de desktop de negócios (se você deseja usar autenticação moderno com Skype) e o Microsoft Outlook (se desejar assim usar autenticação moderno com Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>O que mais preciso saber antes de começar?
<a name="BKMK_Whatelse"> </a>

1. Todos os cenários para servidores locais envolvem configurar autenticação moderno local (na verdade, por Skype para negócios há uma lista de topologias com suporte) para que o servidor responsável pela autenticação e autorização no (Microsoft Cloud Serviço de token segurança do AAD, chamado 'evoSTS') e atualizar o Windows Azure Active Directory (AAD) sobre o URLs ou namespaces usados por sua instalação local de qualquer um dos Skype para negócios ou Exchange. Portanto, os servidores locais assumem uma dependência do Microsoft Cloud. Realizar essa ação pode ser considerado Configurando 'híbrida auth'.
    
2. Este artigo está vinculado check-out para outras pessoas que ajudarão você a escolha com suporte a topologias de autenticação moderno (necessárias somente para Skype for Business) e instruções articles essa estrutura de tópicos as etapas de instalação ou as etapas para desativar a autenticação moderno, para Exchange local e Skype for Business no local. Favorito nesta página no seu navegador, se você vai precisar de uma base inicial para usar autenticação moderno em seu ambiente de servidor.
    
## <a name="list-of-modern-authentication-urls"></a>Lista das URLs de autenticação moderno
<a name="BKMK_URLListforMA"> </a>

- [Como configurar o Exchange Server local para usar a autenticação moderno](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Skype para topologias de negócios compatíveis com autenticação moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Como configurar Skype para negócios local para usar a autenticação moderno](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Como remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

