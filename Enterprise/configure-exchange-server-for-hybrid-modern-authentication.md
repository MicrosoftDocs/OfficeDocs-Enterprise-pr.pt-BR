---
title: Como configurar o Exchange Server no local para usar a autenticação moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: Híbrido moderno autenticação (HMA), é um método de gerenciamento de identidade que oferece mais seguro de autenticação e autorização e está disponível para implantações híbridas do Exchange server local.
ms.openlocfilehash: cfacb5661ddf4a2ac61054582f0c2043d8fe7a5a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975189"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Como configurar o Exchange Server no local para usar a autenticação moderna híbrida

Híbrido moderno autenticação (HMA), é um método de gerenciamento de identidade que oferece mais seguro de autenticação e autorização e está disponível para implantações híbridas do Exchange server local.
  
## <a name="fyi"></a>FYI

Antes de começar, posso chamar:
  
- Autenticação de moderno híbrida \> HMA
    
- Local do Exchange \> EXCH
    
- Exchange Online \> EXO
    
Além disso, *que se um elemento gráfico neste artigo tem um objeto que tem ' acinzentado ' ou 'esmaecida' isso significa que o elemento mostrado em cinza não está incluído na configuração HMA específica* . 
  
## <a name="enabling-hybrid-modern-authentication"></a>Habilitar a autenticação híbrida moderno

Ativando HMA meios:
  
1. Sendo Verifique se que você está cumprindo os pré-requisitos antes de começar.
    
1. Desde muitos **pré-requisitos** são comuns para ambos os Skype para Exchange, [Visão geral da autenticação de moderno híbrida e pré-requisitos para utilizá-lo com local Skype para servidores Exchange e de negócios](hybrid-modern-auth-overview.md)e de negócios. Faça isso antes de começar qualquer uma das etapas neste artigo.
    
2. Adicionando local URLs do web service como nomes de entidade de serviço (SPNs) no Windows Azure AD.
    
3. Garantindo que todos os diretórios virtuais estão habilitados para HMA
    
4. Verificando o objeto de servidor de autenticação EvoSTS
    
5. Habilitando HMA no ajuste
    
 **Observação** Sua versão do Office oferecem suporte a MA? Consulte [moderno como funciona a autenticação para aplicativos de cliente do Office 2013 e Office 2016](modern-auth-for-office-2013-and-2016.md).
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>Verifique se que você atende a todos os pré-requisitos

Como muitos pré-requisitos são comuns para ambos os Skype para Exchange e de negócios, examine o [Visão geral da autenticação de moderno híbrida e pré-requisitos para utilizá-lo com Skype local para os servidores de negócios e do Exchange](hybrid-modern-auth-overview.md). Fazer esta *antes de* começar qualquer uma das etapas neste artigo. 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Adicionar local de URLs de serviço web como SPNs no Azure AD

Execute os comandos que atribuir sua web local URLs de serviço, como o Windows Azure AD SPNs. SPNs são usados por computadores clientes e dispositivos durante a autenticação e autorização. Todas as URLs que poderiam ser usadas para conectar-se no local para Windows Azure Active Directory (AAD) devem ser registradas no AAD (Isso inclui namespaces internos e externos).
  
Primeiro, reúna todas as URLs que você precisa adicionar no AAD. Execute estes comandos no local:
  
- Get-MapiVirtualDirectory | Servidor de FL,\*url\*
    
- Get-WebServicesVirtualDirectory | Servidor de FL,\*url\*
    
- **Get-ActiveSyncVirtualDirectory | Servidor de FL,\*url\***
    
- Get-OABVirtualDirectory | Servidor de FL,\*url\*
    
Verifique se as URLs que os clientes podem se conectar a são listados como nomes de entidade de serviço HTTPS no AAD.
  
1. Primeiro, se conecte ao AAD com [estas instruções](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).
    
2. Para o Exchange URLs relacionados, digite o seguinte comando:
    
- Get-MsolServicePrincipal - AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | Selecione - ExpandProperty ServicePrincipalNames
    
Tomar nota das (e captura de tela para comparação posterior) a saída deste comando, que deve incluir um https:// * descoberta automática. *SeuDomínio* .com * e URL de *e-mailseudominio.com* https://, mas consistem principalmente SPNs que começam com 00000002-0000-0ff1-ce00-000000000000 /. Se houver https:// URLs a partir de seu local que está ausente precisamos adicionar esses registros específicos a essa lista. 
  
3. Se você não vir os registros MAPI/HTTP, EWS, ActiveSync, OAB e descoberta automática internos e externos nessa lista, você deve adicioná-los usando o comando a seguir (o exemplo URLs são '`mail.corp.contoso.com`'e'`owa.contoso.com`', mas você tinha a **Substituir as URLs de exemplo com seu próprio** ) : <br/>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. Verifique se que seus novos registros foram adicionados executando o comando Get-MsolServicePrincipal da etapa 2 novamente e, em seguida, procurando por meio de saída. Compare a lista / captura de tela de antes da nova lista de SPNs (você pode também a nova lista de captura de tela para seus registros). Se você tiver sido bem-sucedida, você verá duas novas URLs na lista. Vai pelo nosso exemplo, a lista de SPNs agora inclui as URLs específicas `https://mail.corp.contoso.com` e `https://owa.contoso.com`. 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>Verifique se que diretórios virtuais estão configuradas corretamente

Verificar agora OAuth adequadamente está habilitado no Exchange em todos os do Outlook diretórios virtuais pode usar, executando os seguintes comandos:

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

Seleção a saída para certificar-se de **OAuth** está habilitada em cada um desses VDirs, você verá algo semelhante a esta (e o mais importante a ser analisado é 'OAuth'); 
  
 **[PS] C:\Windows\System32\>Get-MapiVirtualDirectory | servidor de FL,\*url\*,\*auth\***
  
 **Servidor: EX1**
  
 **InternalUrl:`https://mail.contoso.com/mapi`**
  
 **ExternalUrl:`https://mail.contoso.com/mapi`**
  
 **IISAuthenticationMethods: {Ntlm, OAuth, negociar}**
  
 **InternalAuthenticationMethods: {Ntlm, OAuth, negociar}**
  
 **ExternalAuthenticationMethods: {Ntlm, OAuth, negociar}**
  
Se o OAuth está faltando qualquer servidor e qualquer um dos quatro diretórios virtuais, você precisará adicioná-lo usando os comandos relevantes antes de continuar.
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Confirmar que o objeto do servidor de autenticação EvoSTS está presente

Volte para o Shell de gerenciamento do Exchange local para esse último comando. Agora você pode validar que o seu local tem uma entrada para o provedor de autenticação evoSTS:
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
A saída deve mostrar um AuthServer do EvoSts nome e o estado 'Enabled' deve ser True. Se você não vir isso, você deve baixar e executar a versão mais recente do Assistente de configuração híbrida.
  
 **Importante** Se você estiver executando o Exchange 2010 em seu ambiente, o provedor de autenticação EvoSTS não será criado. 
  
## <a name="enable-hma"></a>Habilitar HMA

Execute o seguinte comando no Shell de gerenciamento do Exchange, no local:

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Verificar

Depois que você ativar HMA, próximo de login do cliente usarão o novo fluxo de autenticação. Observe que apenas ativem HMA não aciona um re-autenticação para qualquer cliente. O clientes sua reconexão com base no tempo de vida de e/ou os tokens de autenticação têm os certificados.
  
Você também deve mantenha pressionada a tecla CTRL ao mesmo tempo que Right clicar no ícone para o cliente do Outlook (também na bandeja do Windows notificações) e clique em Status do Conexão. Procure o endereço de SMTP do cliente em relação a um tipo de 'Authn' de ' portador\*', que representa o token do transportador usado em OAuth.
  
 **Observação** Precisa configurar Skype for Business com HMA? Você precisará de dois artigos: um que lista [topologias com suporte](https://technet.microsoft.com/en-us/library/mt803262.aspx)e outro que mostra [como fazer a configuração](configure-skype-for-business-for-hybrid-modern-authentication.md).
  

## <a name="related-topics"></a>Tópicos relacionados

[Visão geral do híbrido autenticação moderno e pré-requisitos para usá-lo com Skype local para os servidores de negócios e do Exchange](hybrid-modern-auth-overview.md) 
  

