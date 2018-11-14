---
title: Solicitações de rede no Office para Mac
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/9/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Office para aplicativos do Mac oferecem uma experiência de app nativo na plataforma macOS. Cada aplicativo foi projetado para funcionar em uma variedade de cenários, incluindo Estados quando nenhum acesso à rede estiver disponível. Quando uma máquina estiver conectada a uma rede, os aplicativos se conecte automaticamente a uma série de serviços baseados na web para fornecer funcionalidade avançada. Este documento descreve quais pontos de extremidade e URLs tentam alcançar os aplicativos e os serviços fornecidos. Essa informação é útil quando a solução de problemas de rede problemas de configuração e a configuração de uma diretiva para servidores de proxy da rede. Os detalhes deste artigo destinam-se para complementar o URL do Office 365 e o artigo de intervalos de endereços.
ms.openlocfilehash: 929b93433f5d990952b540a1b28fe2ac74edfb5d
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219891"
---
# <a name="network-requests-in-office-for-mac"></a>Solicitações de rede no Office para Mac

Office para aplicativos do Mac oferecem uma experiência de app nativo na plataforma macOS. Cada aplicativo foi projetado para funcionar em uma variedade de cenários, incluindo Estados quando nenhum acesso à rede estiver disponível. Quando uma máquina estiver conectada a uma rede, os aplicativos se conecte automaticamente a uma série de serviços baseados na web para fornecer funcionalidade avançada. As informações a seguir descrevem quais pontos de extremidade e URLs tentam alcançar os aplicativos e os serviços fornecidos. Essas informações são úteis ao solucionar problemas de configuração de rede e definir políticas para servidores de proxy da rede. Os detalhes deste artigo destinam-se para complementar o [artigo de intervalos de URL do Office 365 e o endereço](urls-and-ip-address-ranges.md), que inclui os pontos de extremidade para computadores que executam o Microsoft Windows. A menos que observado, as informações neste artigo também se aplica ao 2019 do Office para Mac e 2016 do Office para Mac, que estão disponíveis como uma única compra de um repositório de varejo ou por meio de um contrato de licenciamento por volume. 

  
A maior parte deste artigo é tabelas detalham as URLs de rede, tipo e descrição do serviço ou recurso fornecido pelo ponto de extremidade. Cada um dos aplicativos Office pode ser diferente no seu uso do serviço e o ponto de extremidade. Os aplicativos a seguintes são definidos nas tabelas a seguir:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: o serviço outlook
- N: OneNote
   
O tipo de URL é definido da seguinte maneira:
  
- Santa: Estática - a URL é embutidas no aplicativo cliente.
    
- SS: Delimitadas estática-o URL é codificada como parte de uma página da web ou redirecionador.
    
- CS: Config Service - a URL é retornada como parte do serviço de configuração do Office.

    
## <a name="office-for-mac-default-configuration"></a>Office para a configuração padrão do Mac

 **Instalação e atualizações**
  
Os seguintes pontos de extremidade de rede são usados para fazer o download do Office para o programa de instalação do Mac da rede de entrega conteúdo a Microsoft (CDN).
  
|**URL**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |SANTA  <br/> |Serviço do vínculo progressivo de Portal de instalação do Office 365 para pacotes de instalação mais recentes.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Local dos pacotes de instalação na rede de entrega de conteúdo.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Local dos pacotes de instalação na rede de entrega de conteúdo.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |SANTA  <br/> |Ponto de extremidade de controle de gerenciamento para o Microsoft AutoUpdate  <br/> |
   
 **Primeira inicialização de aplicativo**
  
Os seguintes pontos de extremidade de rede são contatados na primeira inicialização de um aplicativo do Office. Esses pontos de extremidade fornecem funcionalidade avançada do Office para usuários e as URLs são contatadas independentemente do tipo de licença (incluindo a instalações de licença de Volume).
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |SANTA  <br/> |Configuração de 'Flighting' - permite a luz de recurso-up e experimentação.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |SANTA  <br/> |Teste de configuração de rede 'Flighting'  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |SANTA  <br/> |Teste de configuração de rede 'Flighting'  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |SANTA  <br/> |Serviço de configuração do Office - lista de pontos de extremidade de serviço do mestre.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |SANTA  <br/> |Download de regras de telemetria do Office - informa o cliente sobre quais dados e eventos para carregar o serviço de telemetria.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |R  <br/> |CS  <br/> |Serviço de telemetria do OneNote  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |SANTA  <br/> |Telemetria do Office carregar relatórios - "Heartbeart" e os eventos de erro que ocorrem no cliente são carregados para o serviço de telemetria.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Serviço de modelo Online do Office - fornece aos usuários os modelos de documentos online.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Downloads de modelos do Office - armazenamento de imagens de modelo PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Configuração de armazenamento para aplicativos do Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Catálogo de serviços de integração do Office documento (lista de pontos de extremidade e serviços) e descoberta de Realm inicial.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Recursos para descoberta de Realm inicial v2 (15.40 e posterior)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |SANTA  <br/> |Microsoft AutoUpdate manifestos - verifica se há atualizações disponíveis  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Biblioteca do Microsoft Ajax JavaScript  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |ZZ  <br/> |SS  <br/> |Aplicativo do Wikipedia para configuração do Office e recursos.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Aplicativo do Bing Map para configuração do Office e recursos.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Aplicativo de gráfico de pessoas para configuração do Office e recursos.  <br/> |
|```https://www.onenote.com/```  <br/> |R  <br/> |SANTA  <br/> |O que há de novo conteúdo para o OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |R  <br/> |SANTA  <br/> |Novo conteúdo para o OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |R  <br/> |SS  <br/> |What's New imagens para o OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |Q  <br/> |SANTA  <br/> |Suporte no aplicativo de serviço.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |Q  <br/> |SANTA  <br/> |Serviço de detecção de conta de email.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |SANTA  <br/> |Descoberta automática do Outlook  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |SANTA  <br/> |Ponto de extremidade do Outlook para o serviço Office 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |Q  <br/> |SANTA  <br/> |Ícones de suplementos do Outlook.  <br/> |
   
> [!NOTE]
> O serviço de configuração do Office atua como um serviço de descoberta automática para todos os clientes do Microsoft Office, não apenas para Mac. Os pontos de extremidade retornados na resposta são semi-estruturados estáticos alteração é raros, mas ainda possíveis. 
  
 **Inscrição**
  
Os seguintes pontos de extremidade de rede são contatados ao entrar no armazenamento baseado em nuvem. Dependendo do tipo de conta, diferentes serviços podem ser contatados. Por exemplo:
  
- **MSA: Microsoft Account** - normalmente utilizado para cenários de consumidor e varejo 
    
- **OrgID: organização conta** - normalmente utilizado para cenários comerciais 
    
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |SANTA  <br/> |Serviço de autorização do Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |SANTA  <br/> |Serviço de logon do Office 365 (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |SANTA  <br/> |Serviço de logon da conta da Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Auxiliar de serviço de logon de conta da Microsoft (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Login do Office 365 Branding (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Documento e casas localizador de armazenamento  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |A maioria dos serviço de documentos usados recentemente (MRU)  <br/> |
   
> [!NOTE]
> Baseada em assinatura e varejo de licenças, entrando ambos ativa o produto e permite o acesso aos recursos de nuvem como OneDrive. Para instalações de licença de Volume, os usuários ainda são solicitados a entrar (por padrão), mas que só é necessária para acessar recursos de nuvem, como o produto já está ativado. 
  
 **Ativação do produto**
  
Os seguintes pontos de extremidade de rede se aplicam a assinatura do Office 365 e a licença de varejo ativações. Especificamente, isso não se aplicam a instalações de licença de Volume.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Serviço de Licenciamento do Office  <br/> |
   
 **O que há de novo conteúdo**
  
Os seguintes pontos de extremidade de rede aplicam-se somente à assinatura do Office 365.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |Qual é o conteúdo da página nova JSON.  <br/> |
   
 **Pesquisador**
  
Os seguintes pontos de extremidade de rede aplicam-se somente à assinatura do Office 365.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |ZZ  <br/> |CS  <br/> |Serviço de Web do Pesquisador  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |ZZ  <br/> |CS  <br/> |Conteúdo estático do Pesquisador  <br/> |
|```https://www.bing.com/```  <br/> |ZZ  <br/> |CS  <br/> |Provedor de conteúdo do Pesquisador  <br/> |
   
 **Pesquisa Inteligente**
  
Os seguintes pontos de extremidade de rede se aplicam a assinatura do Office 365 e a licença de Volume de varejo/ativações.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Serviço Web de ideias de pesquisas  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |Biblioteca de JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |Suporte a biblioteca JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Ideias para o provedor de conteúdo  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Ideias para o provedor de conteúdo  <br/> |
   
 **Designer do PowerPoint**
  
Os seguintes pontos de extremidade de rede aplicam-se somente à assinatura do Office 365.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |M  <br/> |CS  <br/> |Serviço de web Designer do PowerPoint  <br/> |
   
 **Iniciador Rápido do PowerPoint**
  
Os seguintes pontos de extremidade de rede aplicam-se somente à assinatura do Office 365.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |M  <br/> |CS  <br/> |Serviço web de QuickStarter de PowerPoint  <br/> |
   
 **Enviar um sorriso/severo**
  
Os seguintes pontos de extremidade de rede se aplicam a assinatura do Office 365 e a licença de Volume de varejo/ativações.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |Enviar um serviço sorriso  <br/> |
   
 **Entre em contato com suporte**
  
Os seguintes pontos de extremidade de rede se aplicam a assinatura do Office 365 e a licença de Volume de varejo/ativações.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |Q  <br/> |CS  <br/> |Entre em contato com o serviço de suporte  <br/> |
|```https://acompli.helpshift.com/```  <br/> |Q  <br/> |CS  <br/> |Suporte no aplicativo de serviço  <br/> |
   
 **Salvar como PDF**
  
Os seguintes pontos de extremidade de rede se aplicam a assinatura do Office 365 e a licença de Volume de varejo/ativações.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |ZZ  <br/> |CS  <br/> |Serviço de conversão de documento do Word (PDF)  <br/> |
   
 **Office Apps (também conhecido como suplementos)**
  
Os seguintes pontos de extremidade de rede se aplicam a assinatura do Office 365 e a licença de Volume de varejo/ativações quando os suplementos de aplicativo do Office são confiáveis.
  
|**URL**|**Apps**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Configuração de armazenamento de aplicativos do Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |ZZ  <br/> |SS  <br/> |Recursos de aplicativo do Wikipedia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Recursos de aplicativo Bing Map  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Recursos de aplicativo do gráfico de pessoas  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Serviço de redirecionamento do Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Bibliotecas de JavaScript do Office  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Telemetria e o serviço de relatório para aplicativos do Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |ZZ  <br/> |SS  <br/> |Biblioteca do Microsoft Ajax JavaScript  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Biblioteca do Microsoft Ajax JavaScript  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Bibliotecas de JavaScript do Office  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de suporte  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de suporte  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de suporte  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |Biblioteca de JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Relatório de erros  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Recursos de fonte  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Serviço de telemetria  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Relatórios de telemetria  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Biblioteca de ativos de armazenamento do Microsoft  <br/> |
|```https://*.wikipedia.org/```  <br/> |ZZ  <br/> |SS  <br/> |Recursos da página Wikipedia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |ZZ  <br/> |SS  <br/> |Recursos de mídia Wikipedia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |ZZ  <br/> |SS  <br/> |Quadro de área restrita do Wikipedia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Modelos de mapa  <br/> |
   
 **Links Seguros**
  
O ponto de extremidade de rede seguinte se aplica a todos os aplicativos do Office para a assinatura do Office 365 apenas.
  
|**URL**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Serviço de Link seguro da Microsoft  <br/> |
   
 **Travar relatórios**
  
O ponto de extremidade de rede seguinte se aplica a todos os aplicativos do Office para ativações de assinatura do Office 365 e a licença de varejo/Volume. Quando um processo falha inesperadamente, um relatório é gerado e enviado para o serviço do Watson.
  
|**URL**|**Tipo**|**Descrição**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |SANTA  <br/> |Serviço de relatório de erros da Microsoft  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |SANTA  <br/> |Serviço de ideias de colaboração do Office  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Opções para reduzir o tráfego e solicitações de rede

A configuração padrão do Office para Mac oferece a melhor experiência de usuário, tanto em termos de funcionalidade e mantendo a máquina atualizado. Em alguns cenários, você poderá impedir que aplicativos contatar os pontos de extremidade de rede. Esta seção discute as opções para fazê-lo.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Desabilitar suplementos entrar na nuvem e do Office
  
Os clientes de licença de volume podem ter políticas estrita sobre o salvamento de documentos para armazenamento baseado em nuvem. A seguinte preferência por aplicativo pode ser definida para desativar MSA/OrgID de entrada e o acesso a suplementos do Office.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Se os usuários tentam acessar a função Sign-In, eles verão um erro que uma conexão de rede não está presente. Porque esta preferência também bloqueia a ativação do produto online, ele deve ser usado somente para instalações de licença de Volume. Especificamente, usar essa preferência impedirá que acessem os seguintes pontos de extremidade de aplicativos do Office:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Todos os pontos de extremidade listados na 'Entrar' seção acima.
    
- Todos os pontos de extremidade listados na seção 'Pesquisa inteligente' acima.
    
- Todos os pontos de extremidade listados na seção de ativação do produto acima.
    
- Todos os pontos de extremidade listados na seção 'Office Apps (também conhecido como suplementos)' acima.
    
Para restabelecer a funcionalidade total para o usuário, defina a preferência para '2' ou removê-lo.
  
> [!NOTE]
> Esta preferência requer o Office para compilação Mac 15.25 [160726] ou posterior. 
  
### <a name="telemetry"></a>Telemetria
  
Office para Mac envia informações de telemetria para a Microsoft em intervalos regulares. Dados são carregados no ponto de extremidade 'Ligação'. Os dados de telemetria ajudam a equipe de engenharia avaliar a integridade e quaisquer comportamentos inesperados de cada aplicativo do Office. Há duas categorias de telemetria:
  
- **Pulsação** contém informações de versão e licença. Esses dados são enviados imediatamente após o lançamento do aplicativo. 
    
- **Uso** contém informações sobre como os aplicativos estão sendo usados e erros não fatais. Esses dados são enviados a cada 60 minutos. 
    
Microsoft leva muito a sério a sua privacidade. Você pode ler sobre a política de coleta de dados da Microsoft em [https://privacy.microsoft.com](https://privacy.microsoft.com). Para impedir que aplicativos enviando telemetria 'Uso', a preferência **SendAllTelemetryEnabled** pode ser ajustada. A preferência é por aplicativo e pode ser definida por meio de perfis de configuração do macOS ou manualmente de Terminal: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Telemetria Heartbeat é sempre enviada e não pode ser desabilitada.
  
### <a name="crash-reporting"></a>Travar relatórios
  
Quando ocorre um erro fatal do aplicativo, o aplicativo será encerrada e carregar um relatório de falha para o serviço de 'Watson' inesperadamente. O relatório de falha consiste em uma pilha de chamada, que é a lista de etapas que o aplicativo estava processando levaram à falha. Essas etapas ajudam a equipe de engenharia identificar a função exato que falharam e por quê.
  
Em alguns casos, o conteúdo de um documento fará com que o aplicativo falhe. Se o aplicativo identifica o documento como a causa, ele pedirá ao usuário se ele é okey para também enviar o documento, juntamente com a pilha de chamadas. Os usuários podem fazer uma opção consciente essa pergunta. Os administradores de TI podem ter requisitos estrito sobre a transmissão de documentos e verifique a decisão em nome do usuário para nunca enviar documentos. A seguinte preferência pode ser definida para impedir que os documentos que estão sendo enviadas e para suprimir o prompt para o usuário:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> Se **SendAllTelemetryEnabled** estiver definida como **FALSE**, todos travar relatórios para que o processo está desabilitado. Para habilitar o relatório de pane sem enviar telemetria de uso, a seguinte preferência pode ser definida:```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Atualizações
  
A Microsoft lança Office para atualizações do Mac em intervalos regulares (normalmente, uma vez por mês). Recomendamos que os usuários e administradores de TI para manter máquinas atualizados para garantir que as correções de segurança mais recentes estiverem instalados. Em casos onde deseja que os administradores de TI bastante, controlar e gerenciar atualizações de máquina, a seguinte preferência pode ser definida para impedir que o processo de atualização automática do detectando automaticamente e oferecendo atualizações de produto:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Bloqueio de solicitações com um Firewall/Proxy
  
Se seus blocos de organização solicita a URLs por meio de um servidor proxy ou firewall não deixe de configurar as URLs listadas neste documento como uma permissão ou bloquear listados com uma resposta X 40 (ex.: 403 ou 404). Uma resposta de X 40 permitirá que os aplicativos do Office aceitar normalmente a incapacidade de acessar o recurso e irá fornecer uma experiência de usuário mais rápida, que simplesmente soltando a conexão, que por sua vez fará com que o cliente repetir.
  
Se seu servidor proxy requer autenticação, uma resposta 407 será retornado ao cliente. Para uma melhor experiência, certifique-se de que você está usando o Office para compilações Mac 15.27 ou posteriores, conforme elas incluem correções específicas para trabalhar com os servidores NTLM e Kerberos.
  
  
## <a name="see-also"></a>Confira também

[URLs e intervalos de endereços IP do Office 365](urls-and-ip-address-ranges.md)

