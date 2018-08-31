---
title: Como configurar o Skype for Business no local para usar a autenticação moderna híbrida
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: Autenticação moderna, é um método de gerenciamento de identidade que oferece a autorização e autenticação de usuário mais segura, está disponível para Skype para Business server local e Exchange server local, bem como a divisão de domínios Skype para híbridas de negócios.
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539487"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Como configurar o Skype for Business no local para usar a autenticação moderna híbrida

Autenticação moderna, é um método de gerenciamento de identidade que oferece a autorização e autenticação de usuário mais segura, está disponível para Skype para Business server local e Exchange server local, bem como a divisão de domínios Skype para híbridas de negócios.
  
 **Importante** Gostaria de saber mais sobre autenticação moderno (MA) e por que você talvez prefira usá-lo em sua empresa ou organização? Verifique se [Este documento](hybrid-modern-auth-overview.md) para obter uma visão geral. Se você precisar saber qual Skype para topologias de negócios são compatíveis com o MA, que está documentado aqui! 
  
 **Antes de começar**, posso chamar: 
  
- Autenticação moderna \> MA
    
- Autenticação de moderno híbrida \> HMA
    
- Local do Exchange \> EXCH
    
- Exchange Online \> EXO
    
- Skype para negócios local \> SFB
    
- e Skype para negócios Online \> SFBO
    
Além disso, * se um elemento gráfico neste artigo tem um objeto que tenha 'acinzentado' ou 'esmaecida' que significa que o elemento mostrado em cinza **não está** incluído na configuração MA específico. * 
  
## <a name="read-the-summary"></a>Leia o resumo

Esse resumo concentra-se o processo em etapas que talvez caso contrário, obtenha perdidos durante a execução e é bom para uma lista de verificação geral rastrear onde você está no processo.
  
1. Primeiro, verifique se que você atende a todos os pré-requisitos.
    
1. Desde muitos **pré-requisitos** são comuns para ambos os Skype para Exchange, [consulte o artigo de visão geral para a sua lista de verificação de pré-req](hybrid-modern-auth-overview.md)e de negócios. Fazer esta *antes de* começar qualquer uma das etapas neste artigo. 
    
2. Colete as informações de HMA específicos, que você precisará de um arquivo ou o OneNote.
    
3. Ativar Diante moderno autenticação para EXO (se ela não ainda esteja ativada).
    
4. Ativar Diante moderno autenticação para SFBO (se ela não ainda esteja ativada).
    
5. Ative a autenticação moderno híbrido para Exchange local.
    
6. Ative a autenticação moderno híbrido para Skype para negócios local.
    
Observe que essas etapas ativem MA para SFB, SFBO, EXCH e EXO – ou seja, todos os produtos que podem participar de uma configuração de HMA do SFB e SFBO (incluindo dependências em EXCH/EXO). Em outras palavras, se os usuários estejam hospedados em / criou caixas de correio em qualquer parte do híbrido (EXO + SFBO, EXO + SFB, EXCH + SFBO, ou EXCH + SFB), seu produto acabado terá a seguinte aparência:
  
![Um misto Skype de 6 de topologia do business HMA tem MA em todos os locais de possíveis quatro.](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
Como você pode ver, existem quatro diferentes locais para ativar o MA! Para uma melhor experiência do usuário é recomendável que você ativar MA em todos os quatro desses locais. Se você não pode ativar MA todos nesses locais, ajuste as etapas para que você ativar MA apenas nos locais que são necessárias para o seu ambiente.
  
Consulte o [tópico de suporte para Skype for Business com o MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) para topologias com suporte. 
  
 **Importante** Verifique novamente cumprir todos os pré-requisitos antes de começar. Você encontrará essas informações [aqui](hybrid-modern-auth-overview.md).
  
## <a name="collect-all-hma-specific-info-youll-need"></a>Coletar todas as informações de HMA específicos, que você precisará

Depois que você tiver com verificação dupla que você cumpre os [pré-requisitos](hybrid-modern-auth-overview.md) para usar a autenticação moderno (consulte a observação acima), você deve criar um arquivo para armazenar as informações que você precisará para configurar HMA nas etapas com antecedência. Exemplos usados neste artigo: 
  
- **Domínio SIP/SMTP**
    
  - Contoso.com ex. (é federado com o Office 365)
    
- **ID do inquilino**
    
  - O GUID que representa seu locatário do Office 365 (no login do contoso.onmicrosoft.com).
    
- **SFB 2015 CU5 URLs do Web Service**
    
Você precisará do URL do serviço de web internos e externos para todos os pools de SfB 2015 implantados. Para obtê-los, execute o seguinte do Skype do Shell de gerenciamento de negócios:
  
Get-CsService - WebServer | Select-Object PoolFqdn, InternalFqdn, Fqdnexterno | FL
  
- Interna ex.:https://lyncwebint01.contoso.com
    
- External ex.:https://lyncwebext01.contoso.com
    
Se você estiver usando um servidor Standard Edition, a URL interna ficará em branco. Nesse caso, use o fqdn do pool para a URL interna.
  
## <a name="turn-on-modern-authentication-for-exo"></a>Ativar a autenticação moderna para EXO

Siga as instruções aqui: [Exchange Online: como habilitar o seu locatário para autenticação moderno.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>Ativar a autenticação moderna para SFBO

Siga as instruções aqui: [Skype para Business Online: habilitar o seu locatário para autenticação moderno](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Ativar a autenticação moderno híbrida do Exchange local

Siga as instruções aqui: [como configurar o Exchange Server local para usar a autenticação híbrida moderno](configure-exchange-server-for-hybrid-modern-authentication.md).
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Ativar a autenticação moderno híbrido para Skype para negócios no local

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Adicionar local de URLs de serviço web como SPNs no Azure AD

Agora, você precisará executar comandos para adicionar as URLs (anteriormente coletados) como entidades de serviço no SFBO.
  
 **Observação** Nomes de entidade de serviço (SPNs) identificam os serviços da web e associá-los a uma entidade de segurança (por exemplo, um nome de conta ou grupo), para que o serviço possa atuar em nome de um usuário autorizado. Clientes de autenticação a um servidor verifique o uso das informações que SPNs contidas em. 
  
1. Primeiro, se conecte ao AAD com [estas instruções](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).
    
2. Execute este comando no local, para obter uma lista das URLs do web service SFB.
    
  - Get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Selecione ServicePrincipalNames - ExpandProperty
    
    Observe que o AppPrincipalId começa com '00000004'. Isso corresponde ao Skype para negócios Online.
    
    Tomar nota das (e captura de tela para comparação posterior) a saída deste comando, que incluem um SE e a URL do WS, mas consistem principalmente SPNs que começam com 00000004-0000-0ff1-ce00-000000000000 /.
    
3. Se os internos **ou** externos SFB URLs no local estão ausentes (por exemplo, https://lyncwebint01.contoso.com e https://lyncwebext01.contoso.com) precisamos adicionar esses registros específicos a essa lista. 
    
    Certifique-se de substituir *as URLs de exemplo* , abaixo, aos URLs reais nos comandos Add! 
    
  - $x = get-MsolServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ") 
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ") 
    
  - Set-MSOLServicePrincipal - AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 - ServicePrincipalNames $x.ServicePrincipalNames
    
4. Verifique se que seus novos registros foram adicionados executando o comando Get-MsolServicePrincipal da etapa 2 novamente e, em seguida, procurando por meio de saída. Compare a lista / captura de tela de antes da nova lista de SPNs (você pode também a nova lista de captura de tela para seus registros). Se você tiver sido bem-sucedida, você verá duas novas URLs na lista. Vai pelo nosso exemplo, a lista de SPNs agora inclui as URLs específicas https://lyncweb01.contoso.com e https://autodiscover.contoso.com.
    
### <a name="create-the-evosts-auth-server-object"></a>Criar o objeto de servidor de autenticação EvoSTS

Execute o seguinte comando no Skype do Shell de gerenciamento de negócios.
  
- New-CsOAuthServer-Identity evoSTS - MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml - AcceptSecurityIdentifierInformation $true-AzureAD de tipo
    
### <a name="enable-hybrid-modern-authentication"></a>Habilitar a autenticação híbrida moderno

Esta é a etapa que realmente ativa MA. Todas as etapas anteriores podem ser executadas antes do tempo, sem alterar o fluxo de autenticação de cliente. Quando você estiver pronto para alterar o fluxo de autenticação, execute este comando no Skype do Shell de gerenciamento de negócios. 
  
- Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity evoSTS
    
## <a name="verify"></a>Verificar

Depois que você ativar HMA, próximo de login do cliente usarão o novo fluxo de autenticação. Observe que apenas ativem HMA não aciona um re-autenticação para qualquer cliente. O clientes sua reconexão com base no tempo de vida de e/ou os tokens de autenticação têm os certificados.
  
Para testar se HMA está funcionando depois que tiver habilitado, saia de um cliente Windows SFB de teste e não se esqueça de clicar em 'Excluir minhas credenciais'. Entre novamente. O cliente agora deve usar o fluxo de autenticação moderno e seu login agora incluirá um prompt do **Office 365** para um 'trabalho ou escola' conta, Vista direita antes que o cliente contata o servidor e registra você. 
  
Você deve também verificar as informações de configuração' ' Skype para clientes corporativos para uma autoridade de OAuth' '. Para fazer isso no computador cliente, mantenha pressionada a tecla CTRL ao mesmo tempo em que você clique com botão direito do Skype para o ícone de negócios na bandeja de notificação do Windows. No menu exibido, clique em informações de configuração. Na janela 'Skype para obter informações de configuração de negócios' que aparecerá na área de trabalho, procure o seguinte:
  
![As informações de configuração de um Skype Business Client usando a autenticação moderno mostram uma Lync e a URL de autoridade do EWS OAUTH do https://login.windows.net/common/oauth2/authorize.](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
Você também deve mantenha pressionada a tecla CTRL ao mesmo tempo que Right clicar no ícone para o cliente do Outlook (também na bandeja do Windows notificações) e clique em Status do Conexão. Procure o endereço de SMTP do cliente em relação a um tipo de Authn de ' portador\*', que representa o token do transportador usado em OAuth.
  
## <a name="related-articles"></a>Artigos relacionados

[Vínculo inverso para a visão geral de autenticação moderno](hybrid-modern-auth-overview.md) . 
  
É preciso saber como usar a autenticação moderno (ADAL) para sua Skype para clientes de negócios? Temos etapas [aqui](https://technet.microsoft.com/en-us/library/mt710548.aspx).
  
Deseja para ler estas etapas que eles aparecem para o Exchange Server, local, executando sem SFB? Essas etapas estão disponíveis aqui.
  

