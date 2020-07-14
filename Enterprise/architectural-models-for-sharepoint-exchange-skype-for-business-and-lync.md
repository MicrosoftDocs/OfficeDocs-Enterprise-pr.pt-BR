---
title: Modelos de arquitetura para SharePoint, Exchange, Skype for Business e Lync
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: 'Resumo: obtenha os cartazes de TI que descrevem os modelos de arquitetura, implantação e opções de plataforma para o SharePoint, o Exchange, o Skype for Business e o Lync.'
ms.openlocfilehash: 9e6e4f2b32bb2e5b39f8891d8acddc0699cdbf8d
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102559"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Modelos de arquitetura para SharePoint, Exchange, Skype for Business e Lync

Estes cartazes de TI descrevem os modelos de arquitetura e as opções de implantação para o SharePoint, o Exchange, o Skype for Business e o Lync e fornecem informações sobre o design para a implantação do SharePoint no Microsoft Azure.
  
Com o Microsoft 365 é possível fornecer a colaboração e os serviços de comunicação com os quais seus usuários estão familiarizados, como serviço baseado na nuvem. Com algumas poucas exceções, a experiência do usuário permanece a mesma, tanto se você estiver mantendo uma implantação local ou usando o Microsoft 365. Essa experiência de usuário unificada torna a decisão de onde colocar cada carga de trabalho menos direta e gera perguntas como:
  
- Como determinar que opção de plataforma escolher para as suas cargas de trabalho individuais?
    
- Faz sentido manter algum serviço local?
    
- Em que cenário uma implantação híbrida é apropriada?
    
- Como o Microsoft Azure se encaixa na situação?
    
- Quais são as configurações suportadas para as cargas de trabalho do Office Server no Azure?
    
> [!TIP]
> Most of the posters on this page are available in multiple languages, including Chinese, English, French, German, Italian, Japanese, Korean, Portuguese, Russian, and Spanish. To download a poster in one of these languages, click the **More languages** link for that poster.
  
Let us know what you think! Send us email at [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Esta página liga você aos seguintes cartazes:
  
- **Cartazes de modelos de arquiteturas** É possível usar estes recursos para determinar a plataforma e a configuração ideais para o SharePoint 2016 e o Skype for Business 2015.
    
  - [Modelos de arquiteturas para o Microsoft SharePoint 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [Bancos de dados do SharePoint Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Modelos de arquitetura para o Microsoft Skype for Business 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Cartazes com opções de plataforma** Você pode usar estes recursos para determinar a plataforma a e configuração ideais do SharePoint 2013, do Exchange 2013 e do Lync 2013.
    
  - [Opções de plataforma para o SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Opções de plataforma para o Exchange 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Opções de plataforma para o Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **Cartazes com soluções para o SharePoint 2013 no Azure** Você pode usar estes cartazes de TI para determinar o design e a configuração para cargas de trabalho do SharePoint Server 2013 nos serviços de infraestrutura do Azure.
    
  - [Sites da Internet no Microsoft Azure usando o SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Amostra de design: sites da Internet no Microsoft Azure para SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Recuperação de desastres do SharePoint para o Microsoft Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Cartazes com modelos de arquitetura

These new IT posters for SharePoint 2016 and Skype for Business 2015 provide a way to compare the various deployment methods in an easy-to-print format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:
  
- **Visão geral** Um breve resumo da plataforma, incluindo um diagrama conceitual.
    
- **Melhor para** Cenários comuns que são ideais para a plataforma específica.
    
- **Requisitos de licença** As licenças necessárias para a implantação.
    
- **Tarefas de arquitetura** As decisões que você precisa tomar como arquiteto.
    
- **Tarefas ou responsabilidades dos profissionais de TI** As responsabilidades diárias que a equipe de TI precisa planejar.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Modelos de arquiteturas para o Microsoft SharePoint 2016

|**Item**|**Descrição**|
|:-----|:-----|
|[![Miniatura do cartaz de Modelos Arquitetônicos do SharePoint 2016](media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | Este cartaz de TI descreve as configurações locais do SharePoint Online, do Microsoft Azure, e do SharePoint de que os responsáveis por decisões de negócios e os arquitetos de soluções precisam saber. <br/><br/> - **SharePoint Online (SaaS)** – consome o SharePoint por meio de um modelo de assinatura de software como serviço (SaaS). <br/> - **SharePoint híbrido** – move seus sites e aplicativos do SharePoint para a nuvem seguindo seu ritmo. <br/> - **SharePoint in Azure (IaaS)** - You extend your on-premises environment into Microsoft Azure and deploy SharePoint 2016 Servers there. (This is recommended for High Availability/Disaster Recovery and dev/test environments.) <br/> - **SharePoint Local** – você planeja, implanta, mantém e customiza o ambiente de SharePoint em um datacenter que você mantém. <br/> |
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>Bancos de dados do SharePoint Server 2016

|**Item**|**Descrição**|
|:-----|:-----|
|[![Miniatura do cartaz de bancos de dados do SharePoint Server 2016](media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | This IT poster is a quick reference guide for SharePoint Server 2016 databases. Each database has the following details: <br/><br/> - Tamanho <br/> - Diretrizes de escala <br/> - Padrões I/O <br/> - Requisitos <br/><br/>  The first page has the SharePoint system databases and the service applications that have multiple databases. The second page shows all of the service applications that have single databases. <br/><br/>  Para saber mais sobre os bancos de dados para SharePoint Server 2016, confira [Tipos e descrições de bancos de dados no SharePoint Server 2016](https://docs.microsoft.com/SharePoint/technical-reference/database-types-and-descriptions) <br/> |
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Modelos de arquitetura para o Microsoft Skype for Business 2015

|**Item**|**Descrição**|
|:-----|:-----|
|[![Miniatura do cartaz de Modelos Arquitetônicos do Skype for Business](media/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |Este cartaz de TI descreve as configurações do Skype for Business Online, locais, híbridas, do cloud PBX e de integração com o Exchange e o SharePoint, que os responsáveis por decisões de negócios e os arquitetos de soluções precisam saber. <br/><br/> Destina-se a profissionais de TI com o objetivo de aumentar a consciência sobre os diferentes modelos de arquitetura fundamentais por meio dos quais o Skype for Business Online e o Skype for Business local podem ser consumidos. <br/><br/>Start with whichever configuration best suits your organization's needs and future plans. Consider and use others as needed. For example, you might want to consider integration with Exchange and SharePoint or a solution that takes advantage of Microsoft's Cloud PBX offering.  <br/> |
   
## <a name="platform-options-posters"></a>Cartazes com opções de plataforma

These IT posters for SharePoint 2013, Exchange 2013, and Lync 2013 provide a way to compare the various deployment methods at a single glance in a large poster format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:
  
- **Visão geral** Um breve resumo da plataforma, incluindo um diagrama conceitual.
    
- **Melhor para** Cenários comuns que são ideais para a plataforma específica.
    
- **Requisitos de licença** As licenças necessárias para a implantação.
    
- **Tarefas de arquitetura** As decisões que você precisa tomar como arquiteto.
    
- **Tarefas ou responsabilidades dos profissionais de TI** As responsabilidades diárias que a equipe de TI precisa planejar.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>Opções de Plataforma para o SharePoint 2013

****

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura de opções de plataforma do SharePoint 2013](media/SP-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |Para os responsáveis pela decisão de negócios (BDMs) e arquitetos, esse modelo mostra as opções de plataforma do SharePoint 2013, SharePoint no Microsoft 365, híbrida local com implantações do Microsoft 365, do Azure, e implantações somente no local. Inclui uma visão geral de cada arquitetura, recomendações, requisitos de licença e listas de arquiteto e tarefas de profissionais de TI para cada plataforma. Várias soluções do SharePoint no Azure estão em destaque. <br/> |
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Opções de plataforma para o Exchange 2013

****

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura de opções da plataforma Exchange](media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |Para os responsáveis por decisões de negócios e os arquitetos, este modelo descreve as opções de plataforma disponíveis para o Exchange 2013. Os clientes podem escolher entre o Exchange Online com o Microsoft 365, Exchange híbrido, Exchange Server local e Exchange Hospedado. O cartaz inclui detalhes de cada opção de arquitetura, incluindo os cenários mais ideais para cada uma delas, os requisitos de licença e as responsabilidades dos profissionais de TI. <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Opções de plataforma para o Lync 2013

****

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura de opções da plataforma Lync](media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |Para os responsáveis por decisões de negócios e os arquitetos, este modelo descreve as opções de plataforma disponível para o Lync 2013. Os clientes podem escolher entre o Lync Online com o Microsoft 365, o Lync Híbrido, o Lync Server local e o Lync Hospedado. O cartaz de TI inclui detalhes de cada opção de arquitetura, incluindo os cenários mais ideais para cada uma delas, os requisitos de licença e responsabilidades dos profissionais de TI.  <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Cartazes com soluções do SharePoint no Azure

Estes cartazes de TI mostram soluções baseadas em Azure usando o SharePoint Server 2013 em um formato de cartaz grande.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Sites da Internet no Microsoft Azure usando o SharePoint Server 2013

****

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem de sites da Internet em Azure usando SharePoint](media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |Este cartaz descreve as principais atividades de design e as opções de arquitetura recomendadas para sites voltados para a Internet no Azure.  <br/><br/> Para saber mais, confira os seguintes artigos:  <br/><br/> - [Sites da Internet no Microsoft Azure usando o SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Arquiteturas do Microsoft Azure para o SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="DesignSampleInternetSites"> </a>
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Exemplo de design: sites da Internet no Microsoft Azure para SharePoint 2013

****

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem da amostra de design: sites das Internet no Microsoft Azure para SharePoint 2013](media/MS-AZ-InternetSitesDesignSample.jpg)](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |Use este exemplo de design como ponto de partida para o seu próprio site de arquitetura voltada para a Internet no Azure usando o SharePoint Server 2013. <br/><br/> Para saber mais, confira os seguintes artigos:  <br/><br/> - [Sites da Internet no Microsoft Azure usando o SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Arquiteturas do Microsoft Azure para o SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Recuperação de desastres do SharePoint para o Microsoft Azure

****

|**Item**|**Descrição**|
|:-----|:-----|
|[![Processo de recuperação de desastres do SharePoint para o Azure](media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |Este cartaz de TI mostra os princípios de arquitetura de um ambiente de recuperação de desastre no Azure. <br/><br/> Para saber mais, confira os seguintes artigos:  <br/><br/> - [Recuperação de desastres do SharePoint Server 2013 no Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Arquiteturas do Microsoft Azure para o SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>Confira também

[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.yml)
  
[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Guias do Laboratório de Teste do Microsoft 365 para empresas](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)
  
[Soluções híbridas](hybrid-solutions.md)

