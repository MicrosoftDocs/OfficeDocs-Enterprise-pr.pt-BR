---
title: Usar a rede de fornecimento de conteúdo do Office 365 com o SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Descreve como usar a rede de entrega de conteúdo (CDN) interno do Office 365 para acelerar a entrega dos ativos do SharePoint Online para todos os usuários, não importa onde eles estão localizados ou como eles acessam o seu conteúdo.
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539168"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a>Usar a rede de fornecimento de conteúdo do Office 365 com o SharePoint Online

Você pode hospedar estáticos ativos na rede de fornecimento de conteúdo de Office 365 (CDN) para oferecer melhor desempenho para as páginas do SharePoint Online. Estáticos ativos são arquivos que não são alterados com frequência, como imagens, vídeo e áudio, folhas de estilo, fontes e arquivos JavaScript. A CDN funciona como um proxy de cache distribuído geograficamente, obtendo quase ativos estáticos para os navegadores pedi-las. 
  
Se você já estiver familiarizado com o modo como as CDNs funcionem, você precisará concluir algumas etapas para configurá-lo. Este tópico descreve como. Leia informações sobre o Office 365 CDN e como começar a hospedagem seus ativos estáticos.
  
 **Cabeça de volta para o [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).**
  
## <a name="office-365-cdn-basics"></a>Noções básicas CDN do Office 365

O Office 365 CDN é incluído como parte da sua assinatura do SharePoint Online. Você não precisa pagar extra para ele. O Office 365 fornece suporte para ambas privadas e acesso público e permite aos ativos estática em vários locais ou origens de host. O Office 365 CDN não é igual a CDN do Windows Azure. Se precisar de mais informações sobre por que usar uma CDN ou sobre conceitos gerais de CDN, consulte [redes de fornecimento de conteúdo](content-delivery-networks.md).
  
## <a name="how-the-cdn-grants-access-to-end-users"></a>Como a CDN concede acesso aos usuários finais

Privada acessem estáticos ativos do Office 365 CDN recebe por tokens gerados pelo SharePoint Online. Usuários que já têm permissão para acessar até a pasta ou biblioteca designados por origem serão concedidos automaticamente tokens. SharePoint Online não suporta as permissões de nível de item para a CDN.
  
Por exemplo, para um arquivo localizado em `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, dado o seguinte:
  
- O usuário 1 tem acesso para folder1 e image1.jpg
    
- O usuário 2 não tem acesso para folder1
    
- 3 de usuário não tem acesso para folder1, mas é concedida permissão explícita para acessar image1.jpg através do SharePoint Online
    
- 4 de usuário tem acesso ao folder1, mas foi negado explicitamente acesso ao image1.jpg
    
Em seguida, as seguintes condições forem verdadeiras:
  
- O usuário 1 e 4 de usuário poderão acessar image1.jpg através do CDN.
    
- O usuário 2 e 3 do usuário não será capaz de acessar image1.jpg através do CDN.
    
    No entanto, User 3 ainda pode acessar o image1.jpg ativos diretamente através do SharePoint Online enquanto o usuário 4 não pode acessar o ativo através do SharePoint Online.
    
## <a name="overview-of-working-with-the-office-365-cdn"></a>Visão geral de como trabalhar com o Office 365 CDN

Para configurar o Office 365 CDN, você deve seguir estas etapas básicas:
  
- Planejar a implantação de CDN:
    
  - Determine quais ativos estáticos que você deseja hospedar na CDN do Office 365. Para obter informações detalhadas sobre como fazer essas opções, consulte [redes de fornecimento de conteúdo](content-delivery-networks.md).
    
  - [Determine onde deseja armazenar os ativos](use-office-365-cdn-with-spo.md#CDNStoreAssets). Este local é uma pasta ou uma biblioteca do SharePoint e é chamado de uma origem.
    
  - Determine se os ativos devem ser feitos públicos ou mantidos privados. Você fazer isso quando você [escolher se cada origem deve ser pública ou privada](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Se desejar, você pode ter várias origens nas quais alguns são públicos e alguns estão privadas.
    
- [Definido para cima e para configurar o Office 365 CDN usando o Shell de gerenciamento do SharePoint Online](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Quando você concluir esta etapa, você terá:
    
  - Habilitado a CDN para sua organização.
    
  - Adicionado o seus origens. Você identificar cada origem como pública ou privada.
    
Uma vez terminar com a instalação, [Gerenciar o Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) ao longo do tempo por: 
  
- Adicionar, atualizar e remover ativos
    
- Adicionando e removendo origens
    
- Configurando políticas CDN
    
- Se necessário, desabilitando a CDN do Office 365
    
## <a name="determine-where-you-want-to-store-your-assets"></a>Determinar onde deseja armazenar os ativos

A CDN busca seus ativos de um local chamado uma origem. Para o Office 365, uma origem é uma biblioteca do SharePoint ou a pasta que seja acessível por uma URL. Você tem grande flexibilidade quando você especificar origens para sua organização. Por exemplo, você pode especificar várias origens ou, uma única origem onde você deseja colocar todos os seus ativos CDN. Você pode optar por ter origens públicas ou privadas para a sua organização. A maioria das organizações optará por implementar uma combinação dos dois.
  
Se você definir centenas de origens, ele provavelmente terá um impacto negativo sobre o tempo que leva para processar solicitações. É recomendável que se você tiver mais de cerca de 100 origens você talvez queira pensar novamente sua arquitetura.
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a>Escolha se cada origem deve ser pública ou privada

Quando você identifica uma origem, especifique se ela deve ser feita pública ou privada. Independentemente de qual opção escolher, Microsoft faz todo o trabalho pesado para você quando se trata de administração da CDN em si. Além disso, você pode alterar mente mais tarde, depois de configurar o CDN e identificado suas origens.
  
Opções de públicas e particulares fornecem melhorias de desempenho, mas cada uma tem vantagens e atributos exclusivos.
  
 **Atributos e as vantagens de hospedagem ativos em uma origem de público**
  
- Ativos expostos em uma origem pública anonimamente são acessíveis por todos.
    
    > [!IMPORTANT]
    > Se você identificar uma origem pública na sua CDN, você nunca deve colocar os recursos que são considerados confidenciais à sua organização em uma origem pública ou a biblioteca do SharePoint Online. 
  
- Se você remover um ativo de uma origem de pública, o ativo pode continuar a estejam disponíveis por até 30 dias a partir do cache; No entanto, podemos invalidará links para os ativos na CDN dentro de 15 minutos.
    
- Quando você hospeda folhas de estilo (arquivos CSS) em uma origem de pública, você pode usar caminhos relativos e URIs dentro do código. Isso significa que é possível fazer referência a localização das imagens de plano de fundo e outros objetos em relação a localização do ativo que está chamando-lo.
    
- Enquanto você pode codificar o URL de uma origem público, fazer isso não é recomendado. O motivo para isso é que, se acessem a CDN ficar indisponível, a URL não resolverá automaticamente à sua organização no SharePoint Online e pode resultar em links desfeitos e outros erros.
    
- Os tipos de arquivo padrão que estão incluídos para origens públicas são. CSS, .eot,. gif,. ico,. JPEG,. jpg,. js,. map,. png,. SVG,. ttf e .woff. Você pode especificar os tipos de arquivo adicional.
    
- Se desejar, você pode configurar uma política para excluir os ativos que foram identificados por classificações de site que você especificar. Por exemplo, você pode optar por excluir todos os ativos que são marcados como "confidencial" ou "restritas", mesmo que elas são um tipo de arquivo permitidos e estão localizadas em uma origem de pública.
    
 **Atributos e as vantagens de hospedagem ativos em uma origem privada**
  
- Os usuários podem acessar apenas os ativos de uma origem privada se eles estão autorizados a fazê-lo. Acesso anônimo para esses ativos é impedido.
    
- Se você remover um ativo em relação à origem particular, o ativo pode continuar esteja disponível para até uma hora do cache; No entanto, podemos invalidará links para os ativos na CDN dentro de 15 minutos.
    
- Os tipos de arquivo padrão que estão incluídos para origens privadas são. ico,. gif,. jpg,. JPEG,. js e. PNG. Você pode especificar os tipos de arquivo adicional.
    
- Assim como as origens de públicas, você pode configurar uma política para excluir os ativos que foram identificados por classificações de site que você especificar, mesmo se você usar caracteres curinga para incluir todos os ativos dentro de uma pasta ou biblioteca do Site.
    
## <a name="default-office-365-cdn-origins"></a>Origens de Office 365 CDN padrão

A menos que você especifique o contrário, Office 365 configura algumas origens de padrão para você quando você habilita a CDN do Office 365. Se você inicialmente excluí-los, você pode adicionar esses origens após concluir a instalação.
  
Origens de privada padrão:
  
- \*/userphoto.aspx
    
- \*/siteassets
    
Origens de pública padrão:
  
- \*/MasterPage
    
- \*/biblioteca
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Instalar e configurar o Office 365 CDN usando o Shell de gerenciamento do SharePoint Online

Os procedimentos neste tópico exigem que você pode usar o Shell de gerenciamento do SharePoint Online para se conectar ao SharePoint Online. Para obter instruções, consulte [Connect to do PowerShell no SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).
  
Conclua estas etapas para instalar e configurar o CDN do Office 365 para hospedar seus estáticos ativos no SharePoint Online.
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a>Para habilitar a sua organização para usar o Office 365 CDN

Use o cmdlet **Set-SPOTenantCdnEnabled** para habilitar a sua organização para usar o Office 365 CDN. Você pode habilitar a sua organização usar origens públicas, origens privadas ou ambos com a CDN. Você também pode configurar o CDN do Office 365 para ignorar a configuração de origens padrão quando você ativá-la. Você sempre pode adicionar esses origens posteriormente, conforme descrito neste tópico. 
  
No Windows Powershell para SharePoint Online:
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Por exemplo, para permitir que sua organização use origens de públicas e particulares com a CDN, digite o seguinte comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Para permitir que sua organização use origens de públicas e particulares com a CDN mas ignorar a configuração as origens padrão, digite o seguinte comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Para permitir que sua organização use origens públicas com a CDN, digite o seguinte comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Para permitir que sua organização use origens privadas com a CDN, digite o seguinte comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Para obter mais informações sobre esse cmdlet, consulte [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a>(Opcional) Para alterar a lista de tipos de arquivo para incluir na CDN do Office 365
<a name="Office365CDNforSPOFileType"> </a>

> [!TIP]
> Quando você definir tipos de arquivo usando o cmdlet **Set-SPOTenantCdnPolicy** , substituirá a lista definida no momento. Se você deseja adicionar tipos de arquivo à lista, use o cmdlet primeiro para descobrir quais tipos de arquivo que já têm permissão e incluem-los na lista, juntamente com as novas. 
  
Use o cmdlet **Set-SPOTenantCdnPolicy** para definir tipos de arquivos estáticos que podem ser hospedados por origens de públicas e particulares na CDN. Por padrão, os tipos de ativos comuns são permitidos para. js,. gif,. jpg e. CSS de exemplo. 
  
No Windows PowerShell para SharePoint Online:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Para ver quais tipos de arquivo são permitidos atualmente pela CDN, use o cmdlet **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Para obter mais informações sobre esses cmdlets, consulte [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>(Opcional) Para alterar a lista de classificações de site que você deseja excluir da CDN do Office 365
<a name="Office365CDNforSPOSiteClassification"> </a>

> [!TIP]
> Quando você excluir classificações de sites usando o cmdlet **Set-SPOTenantCdnPolicy** , substituirá a lista definida no momento. Se você deseja excluir classificações de sites adicionais, use o cmdlet primeiro para saber quais classificações já são excluídas e adicioná-lo, juntamente com as novas. 
  
Use o cmdlet **Set-SPOTenantCdnPolicy** para excluir as classificações de site que você não deseja disponibilizar sobre a CDN. Por padrão, nenhuma classificações de site são excluídas. 
  
No Windows PowerShell para SharePoint Online:
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Para ver quais classificações de site são restritas atualmente, use o cmdlet **Get-SPOTenantCdnPolicies** : 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Para obter mais informações sobre esses cmdlets, consulte [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) e [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).
  
### <a name="to-add-an-origin-for-your-assets"></a>Para adicionar uma origem para os ativos
<a name="Office365CDNforSPOOrigin"> </a>

Use o cmdlet **Add-SPOTenantCdnOrigin** para definir uma origem. Você pode definir várias origens. A origem é uma URL que aponta para uma biblioteca do SharePoint ou a pasta que contém os ativos que você deseja ser hospedada pela CDN. 
  
> [!IMPORTANT]
> Se você identificar uma origem pública na sua CDN, você nunca deve colocar os recursos que são considerados confidenciais à sua organização na origem pública ou biblioteca do SharePoint Online. 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

Onde caminho é o caminho para a pasta que contém os ativos. Você pode usar caracteres curinga, além dos caminhos relativos. Por exemplo, para incluir todos os ativos na pasta masterpages para todos os sites como uma origem pública dentro a CDN, digite o seguinte comando:
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

Para obter mais informações sobre esse comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Após executar o comando, o sistema sincroniza todas a configuração no datacenter. Isso leva a 15 minutos.
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Exemplo: Configurar uma origem pública para suas páginas mestras e para sua biblioteca de estilos para o SharePoint Online
<a name="ExamplePublicOrigin"> </a>

Normalmente, essas origens estiver configuradas para você por padrão quando você habilita origens públicas para o Office 365 CDN. No entanto, se você quiser habilitá-los manualmente, siga estas etapas.
  
- Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a biblioteca de estilos como uma origem pública dentro do Office 365 CDN. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- Use o cmdlet **Add-SPOTenantCdnOrigin** para definir as páginas mestras como uma origem pública dentro do Office 365 CDN. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- Para obter mais informações sobre esse comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Após executar o comando, o sistema sincroniza todas a configuração no datacenter. Isso leva a 15 minutos.
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Exemplo: Configurar uma origem privada para seus ativos do site, páginas do site e publicação de imagens para SharePoint Online
<a name="ExamplePrivateOrigin"> </a>

- Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de ativos do site como uma origem privada dentro do Office 365 CDN. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de páginas do site como uma origem privada dentro do Office 365 CDN. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- Use o cmdlet **Add-SPOTenantCdnOrigin** para definir a pasta de imagens de publicação como uma origem privada dentro do Office 365 CDN. 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    Para obter mais informações sobre esse comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
    
    Após executar o comando, o sistema sincroniza todas a configuração no datacenter. Isso leva a 15 minutos.
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Exemplo: Configurar uma origem privada para um conjunto de sites para o SharePoint Online
<a name="ExamplePrivateOriginSiteCollection"> </a>

Use o cmdlet **Add-SPOTenantCdnOrigin** para definir um conjunto de sites como uma origem privada dentro do Office 365 CDN. Por exemplo, 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Para obter mais informações sobre esse comando e sua sintaxe, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).
  
Após executar o comando, o sistema sincroniza todas a configuração no datacenter. Isso leva a 15 minutos.
  
## <a name="manage-the-office-365-cdn"></a>Gerenciar o Office 365 CDN
<a name="CDNManage"> </a>

Depois que você tiver configurado a CDN, você pode fazer alterações à sua configuração como atualizar o conteúdo ou conforme suas necessidades mudam, conforme descrito nesta seção.
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a>Para adicionar, atualizar, ou remova ativos a CDN do Office 365
<a name="Office365CDNforSPOaddremoveasset"> </a>

Depois de ter concluído as etapas de instalação, você pode adicionar novos ativos e atualizar ou remover ativos existentes, sempre que desejar. Apenas faça as alterações dos ativos na pasta ou biblioteca do SharePoint que você identificou como uma origem. Se você adicionar um novo ativo, ele está disponível por meio do CDN imediatamente. No entanto, se você atualizar o ativo, levará até 15 minutos para a nova cópia propagar e se tornam disponíveis na CDN.
  
Se você precisar recuperar o local da origem, você pode usar o cmdlet **Get-SPOTenantCdnOrigins** . Para obter informações sobre como usar esse cmdlet, consulte [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a>Para remover uma origem da CDN do Office 365
<a name="Office365CDNforSPORemoveOrigin"> </a>

Se for necessário, você pode remover o acesso a uma pasta ou uma biblioteca do SharePoint que você identificou como uma origem. Para fazer isso, use o cmdlet **Remove-SPOTenantCdnOrigin** . Para obter informações sobre como usar esse cmdlet, consulte [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a>Para modificar uma origem na CDN do Office 365
<a name="Office365CDNforSPORemoveOrigin"> </a>

Você não pode modificar uma origem que você criou. Em vez disso, remova a origem e, em seguida, adicionar um novo. Para obter mais informações, consulte [para remover uma origem a partir do Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) e [Adicionar uma origem para os ativos](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).
  
### <a name="to-disable-the-office-365-cdn"></a>Para desabilitar a CDN do Office 365
<a name="Office365CDNforSPODisable"> </a>

Use o cmdlet **Set-SPOTenantCdnEnabled** para desabilitar a CDN para sua organização. Se você tiver ambas as públicas e particulares origens habilitadas para a CDN, você precisará executar o cmdlet duas vezes conforme mostrado nos exemplos a seguir. 
  
Para desabilitar o uso de origens públicos no CDN, no Windows Powershell para SharePoint Online, insira o seguinte comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Para desabilitar o uso das origens privadas na CDN, insira o seguinte comando:
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Para obter mais informações sobre esse cmdlet, consulte [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a>Solucionando problemas de configuração CDN do Office 365
<a name="CDNManage"> </a>

O ponto de extremidade não imediatamente estará disponível para uso, como leva tempo para que o registro para se propagar a CDN. Configuração leva 15 minutos.
  

