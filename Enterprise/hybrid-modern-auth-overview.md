---
title: Visão geral da autenticação moderna híbrida e pré-requisitos para usá-lo com o Skype for Business e servidores do Exchange locais
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: A autenticação moderna é um método de gerenciamento de identidades que oferece autenticação e autorização de usuário mais seguras. Ele está disponível para implantações híbridas do Skype for Business Server local e do Exchange Server local, bem como de divisão de domínio do Skype for Business. Este artigo contém links para documentos relacionados sobre pré-requisitos, configuração/desabilitação da autenticação moderna e para alguns dos clientes relacionados (ex. Informações sobre clientes Outlook e Skype).
ms.openlocfilehash: 26efa77e3c98c0395188e6ca7a2f65cd3b8b939e
ms.sourcegitcommit: 19f0deee26b6cf2eef316c742054572bb9d98b84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "30458341"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Visão geral da autenticação moderna híbrida e pré-requisitos para usá-lo com o Skype for Business e servidores do Exchange locais

A autenticação moderna é um método de gerenciamento de identidades que oferece autenticação e autorização de usuário mais seguras. Ele está disponível para implantações híbridas do Office 365 do Skype for Business Server local e do Exchange Server local, bem como para os híbridos divididos do Skype for Business no domínio. Este artigo contém links para documentos relacionados sobre pré-requisitos, configuração/desabilitação da autenticação moderna e para alguns dos clientes relacionados (ex. Informações sobre clientes Outlook e Skype). 
  
- [O que é autenticação moderna?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [O que muda quando uso a autenticação moderna?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Verificar o status de autenticação moderna do seu ambiente local](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [Você atende aos pré-requisitos de autenticação modernos?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [O que mais preciso saber antes de começar?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Lista de URLs de autenticação modernas](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>O que é autenticação moderna?
<a name="BKMK_WhatisModAuth"> </a>

Ao falar sobre a comunicação entre um cliente (por exemplo, seu laptop ou seu telefone) e um servidor, a Microsoft usa a frase "autenticação moderna".
  
A autenticação moderna é um termo abrangente para uma combinação de métodos de autenticação e autorização, além de algumas medidas de segurança que dependem de políticas de acesso que você já conhece. Ele inclui:
  
- **Métodos de autenticação**: autenticação multifator; Autenticação baseada em certificado do cliente; e a biblioteca de autenticação do Active Directory ( [Adal](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Métodos de autorização**: implementação da Microsoft de autorização aberta (OAuth). 
    
- **Políticas de acesso condicional**: gerenciamento de aplicativo móvel (MAM) e acesso condicional do Azure Active Directory. 
    
O gerenciamento de identidades de usuário com autenticação moderna oferece aos administradores muitas ferramentas diferentes para usar quando se trata de proteger recursos e oferece métodos mais seguros de gerenciamento de identidades para o local (Exchange e Skype for Business), Exchange híbrido e cenários híbridos/de domínio divididos do Skype for Business.
  
Lembre-se de que, como o Skype for Business funciona em conjunto com o Exchange, o comportamento de logon que os usuários clientes do Skype for Business verão serão afetados pelo status de autenticação moderna do Exchange. Isso também se aplicará se você tiver uma divisão híbrida do Skype for Business. Além disso, o tipo de Hybrid do Skype for Business que dá suporte ao uso de autenticação moderna é freqüentemente chamado de um ' Split-Domain ' (em um divisão de domínio, você tem o Skype for Business Online e o Skype for Business local e os usuários são hospedados em ambos os locais).
  
> [!IMPORTANT]
> Você sabia que, em agosto de 2017, todos os novos locatários do Office 365 que incluem o Skype for Business Online e o Exchange Online terão a autenticação moderna habilitada por padrão? Os locatários pré-existentes não terão uma alteração no estado padrão de MA, mas todos os novos locatários suportam automaticamente o conjunto expandido de recursos de identidade que você vê listados acima. Para verificar o status do seu MA para o Skype for Business Online, você pode usar o Skype for Business online PowerShell com credenciais de administrador global. Execute `Get-CsOAuthConfiguration` para verificar a saída de-ClientADALAuthOverride. Se-ClientADALAuthOverride for ' Allowed ', sua autenticação moderna está ativada. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>O que muda quando uso a autenticação moderna?
<a name="BKMK_WhatChanges"> </a>

Ao usar a autenticação moderna com o Skype for Business ou o Exchange Server local, você ainda ** está autenticando usuários no local, mas a história ** de autorizar o acesso a recursos (como arquivos ou emails) é alterada. É por isso que, embora a autenticação moderna seja sobre a comunicação de cliente e de servidor, as etapas executadas durante a configuração do resultado MA no evoSTS (um serviço de token de segurança usado pelo Azure AD) estão sendo definidas como servidor de autenticação para o Skype for Business e o Exchange Server no local. 
  
A alteração no evoSTS permite que seus servidores locais aproveitem o OAuth (emissão de token) para autorizar seus clientes e também permite que os métodos de segurança de uso local sejam comuns na nuvem (como autenticação multifator). Além disso, o evoSTS emite tokens que permitem aos usuários solicitar acesso a recursos sem fornecer a senha como parte da solicitação. Não importa onde seus usuários estejam hospedados (de online ou no local), e não importa qual local hospede o recurso necessário, o EvoSTS se tornará o núcleo da autorização de usuários e clientes após a configuração da autenticação moderna.
  
Veja um exemplo do que eu quero dizer. Se o cliente Skype for Business precisa acessar o Exchange Server para obter informações de calendário em nome de um usuário, ele usa a biblioteca de autenticação do Active Directory (ADAL) para fazer isso. A ADAL é uma biblioteca de códigos projetada para disponibilizar recursos protegidos em seu diretório para aplicativos cliente usando tokens de segurança OAuth. A ADAL funciona com o OAuth para verificar declarações e trocar tokens (em vez de senhas) para conceder a um usuário acesso a um recurso. No passado, a autoridade em uma transação como esta--o servidor que sabe como validar declarações de usuário e emitir os tokens necessários--pode ter sido um serviço de token de segurança local ou até mesmo os serviços de Federação do Active Directory. No enTanto, a autenticação moderna centraliza essa autoridade no Azure Active Directory (Azure AD) na nuvem.
  
Isso também significa que, embora seus ambientes do Exchange Server e do Skype for Business possam ser totalmente locais, o servidor de autorização estará online e seu ambiente local deverá ter a capacidade de criar e manter uma conexão com o Office 365 assinatura na nuvem (e a instância do Azure Active Directory que sua assinatura usa como seu diretório).
  
O que não muda? Se você estiver em um domínio de divisão híbrida ou usando o Skype for Business e o Exchange Server no local, todos os usuários devem primeiro autenticar *no local* . Em uma implementação híbrida da autenticação moderna, Lyncdiscovery e ponto de descoberta automática no servidor local. 
  
> [!IMPORTANT]
> Se você precisar saber as topologias específicas do Skype for Business compatíveis com o MA, isso está [documentado aqui](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Verificar o status de autenticação moderna do seu ambiente local
<a name="BKMK_CheckStatus"> </a>

Como a autenticação moderna muda o servidor de autorização usado quando os serviços aproveitam o OAuth/S2S, você precisa saber se a autenticação moderna está ativada ou desAtivada para seu ambiente do Skype for Business e do Exchange. Você pode verificar o status em seus servidores Exchange ou Skype for Business, no local, executando o `Get-CSOAuthConfiguration` comando no PowerShell. Se o comando retornar uma propriedade ' OAuthServers ' vazia, a autenticação moderna estará desabilitada.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>Você atende aos pré-requisitos de autenticação modernos?

Verifique e verifique os itens da lista antes de continuar:
  
- **Específico do Skype for Business**
    
  - Todos os servidores devem ter o SFB Server 2015 CU5 ou posterior
    
  - O aparelho de filial de sustentabilidade da **exceção** (SBA) pode estar na versão atual (com base no Lync 2013) 
    
  - Seu domínio SIP é adicionado como um domínio federado no Office 365
    
  - Todos os front-ends do SFB devem ter conexões de saída para a Internet, URLs de autenticação do Office 365 (TCP 443) e CRLs raiz de certificado conhecidos (TCP 80) listadas nas linhas 56 e 125 da seção "Microsoft 365 Common e Office Online" do [Office 365 URLs e IP intervalos de endereços](urls-and-ip-address-ranges.md).
    
 **Observação** Se os servidores front-end do Skype for Business usarem um servidor proxy para acesso à Internet, o IP do servidor proxy e o número da porta usados deverão ser inseridos na seção configuração do arquivo Web. config para cada front-end. 
  
- C:\Arquivos de Files\Skype for Business Server 2015 \ Web Components\Web ticket\int\web.config
    
- C:\Arquivos de Files\Skype for Business Server 2015 \ Web Components\Web ticket\ext\web.config
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> Não se esqueça de assinar o RSS feed para [URLs e intervalos de endereços IP do Office 365](urls-and-ip-address-ranges.md) para manter-se atualizado com as listas de URLs necessárias mais recentes. 
  
- **Específico do Exchange Server**
    
  - Você está usando o Exchange Server 2013 CU19 e up, ou o Exchange Server 2016 CU8 e superior.
    
  - Não há um Exchange Server 2010 no ambiente.
    
  - O desCarregamento SSL não está configurado. A terminação de SSL e a nova criptografia são suportadas.
    
  - No caso de seu ambiente usar uma infraestrutura de servidor proxy para permitir que os servidores se conectem à Internet, verifique se todos os servidores do Exchange têm o servidor proxy definido na propriedade [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) .
    
- **Requisitos de protocolo e cliente do Exchange**
  
  - Os seguintes clientes suportam a autenticação moderna:

  |**Clientes**|**Protocolo principal**|**Anotações**|
  |:-----|:-----|:-----|
  |Outlook 2013 e Outlook 2016  <br/> |MAPI sobre HTTP  <br/> |O MAPI sobre HTTP deve estar habilitado no Exchange para aproveitar a autenticação moderna com esses clientes (geralmente habilitados ou verdadeiros para novas instalações do Exchange 2013 Service Pack 1 e posterior); para obter mais informações, consulte [como a autenticação moderna funciona para aplicativos cliente do office 2013 e do office 2016](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Verifique se você está executando a compilação mínima necessária do Outlook; Confira [as atualizações mais recentes para as versões do Outlook que usam o Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 para Mac  <br/> |Serviços Web do Exchange  <br/> |  <br/> |
  |Outlook para iOS e Android  <br/> |  <br/> |Consulte [usando a autenticação moderna híbrida com Outlook para IOS e Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) para obter mais informações.  <br/> |
  |Clientes do Exchange ActiveSync (por exemplo, iOS11 mail)  <br/> |Exchange ActiveSync  <br/> |Para clientes do Exchange ActiveSync que dão suporte à autenticação moderna, você deve recriar o perfil para mudar da autenticação básica para a autenticação moderna.  <br/> |

- **Pré-requisitos gerais**
    
  - Se você usar o ADFS, deverá ter o Windows 2012 R2 ADFS 3,0 e superior para Federação
    
  - Suas configurações de identidade são qualquer um dos tipos suportados pelo AAD Connect (como a sincronização de hash de senha, a autenticação de passagem, o STS local suportado pelo Office 365, et cetera.)
    
  - Você tem a conexão do AAD configurada e funcionando para replicação e sincronização do usuário.
    
  - Você verificou que o híbrido está configurado usando o modo de topologia híbrida clássica do Exchange entre seu ambiente local e o Office 365. Declaração de suporte oficial para o Exchange Hybrid diz que você deve ter a CU atual ou a CU-1 atual.
    
    > [!Note]
    > A autenticação moderna híbrida não é suportada com o [agente híbrido](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).
    
  - Certifique-se de que um usuário de teste local, bem como um usuário de teste híbrido hospedado no Office 365, possa fazer logon no cliente de área de trabalho do Skype for Business (se você quiser usar a autenticação moderna com o Skype) e o Microsoft Outlook (se quiser usar a autenticação moderna com o Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>O que mais preciso saber antes de começar?
<a name="BKMK_Whatelse"> </a>

1. Todos os cenários para servidores locais envolvem a configuração da autenticação moderna local (na verdade, para o Skype for Business há uma lista de topologias com suporte) para que o servidor responsável por autenticação e autorização esteja na nuvem da Microsoft ( O serviço de token de segurança do AAD, chamado ' evoSTS ', e a atualização do Azure Active Directory (AAD) sobre as URLs ou namespaces usados por sua instalação local do Skype for Business ou do Exchange. Portanto, os servidores locais usam uma dependência de nuvem da Microsoft. Executar esta ação pode ser considerada Configurando a "autenticação híbrida".
    
2. Este artigo é voltado para outras pessoas que ajudarão você a escolher topologias de autenticação modernas com suporte (necessário apenas para o Skype for Business) e artigos de instruções que descrevem as etapas de configuração ou etapas para desabilitar a autenticação moderna, para o Exchange local e Skype for Business no local. Favorito esta página no navegador se você precisar de uma base inicial para usar a autenticação moderna em seu ambiente de servidor.
    
## <a name="list-of-modern-authentication-urls"></a>Lista de URLs de autenticação modernas
<a name="BKMK_URLListforMA"> </a>

- [Como configurar o Exchange Server no local para usar a autenticação moderna](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Topologias do Skype for Business compatíveis com a autenticação moderna](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Como configurar o Skype for Business no local para usar a autenticação moderna](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Remover ou desabilitar a autenticação moderna híbrida do Skype for Business e do Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

