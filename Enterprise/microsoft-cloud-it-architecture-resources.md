---
title: Recursos de arquitetura de TI do Microsoft Cloud
ms.author: bcarter
author: brendacarter
manager: laurawi
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 28986107-e2fb-4116-bfdd-f66d751a7c16
search.appverid:
- MET150
description: 'Resumo: conheça os principais conceitos de arquitetura de nuvens relacionados à segurança, redes, implantação híbrida e identidade da Microsoft. Examine as recomendações indicadas para a proteção de arquivos, identidades e dispositivos ao usar a nuvem da Microsoft. Saiba como implantar uma área de trabalho moderna e segura com o Windows 10 e o Office ProPlus.'
ms.openlocfilehash: f2f466ff0f5f13e2b7e3bfb85f77a7e7961fcde2
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844932"
---
# <a name="microsoft-cloud-it-architecture-resources"></a>Recursos de arquitetura de TI do Microsoft Cloud

 **Resumo:** conheça os principais conceitos da Microsoft de arquitetura de nuvem para identidade, segurança, redes e híbrida. Examine as recomendações indicadas para a proteção de arquivos, identidades e dispositivos ao usar a nuvem da Microsoft. Saiba como implantar uma área de trabalho moderna e segura com o Windows 10 e o Office ProPlus.
  
Esses cartazes e ferramentas de arquitetura proporcionam informações sobre os serviços em nuvem da Microsoft, incluindo o Office 365, Windows 10, Azure Active Directory, Microsoft Intune, Microsoft Dynamics 365 e soluções híbridas no local e em nuvem. Os arquitetos e tomadores de decisões da TI podem usar esses recursos para determinar as soluções ideais para suas cargas de trabalho e para tomar decisões em relação aos principais componentes de infraestrutura, como a identidade e a segurança. 
  
<!--**[Microsoft's Enterprise Cloud Roadmap](microsoft-cloud-it-architecture-resources.md#roadmap)** (Sway) -->
    
- **[Série Microsoft cloud para arquitetos empresariais](microsoft-cloud-it-architecture-resources.md#cloudarch)** 
    <!-- [Microsoft Cloud Services and Platform Options](microsoft-cloud-it-architecture-resources.md#platformoptions) -->
    - [Identidade do Microsoft Cloud para arquitetos corporativos](microsoft-cloud-it-architecture-resources.md#identity)
    - [Segurança no Microsoft Cloud para arquitetos corporativos](microsoft-cloud-it-architecture-resources.md#security)
    - [Rede do Microsoft Cloud para arquitetos corporativos](microsoft-cloud-it-architecture-resources.md#networking)
    - [Nuvem híbrida da Microsoft para arquitetos corporativos](microsoft-cloud-it-architecture-resources.md#hybrid)
    - [Ataques comuns e recursos da Microsoft que protegem sua organização](#common-attacks-and-microsoft-capabilities-that-protect-your-organization)
    - [Infraestrutura de base do Microsoft 365 Enterprise](#m365foundationinfra)
    - [Abordagens de arquitetura para as migrações de locatário do Microsoft Cloud para o locatário](#architecture-approaches-for-microsoft-cloud-tenant-to-tenant-migrations)
    
- **[Série de solução do Office 365 Enterprise](microsoft-cloud-it-architecture-resources.md#BKMK_o365solutions)**:
    - [Microsoft Teams e serviços de produtividade relacionados no Microsoft 365 para arquitetos de TI](#microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects)
    - [Grupos no Microsoft 365 para arquitetos de TI](#groups-in-microsoft-365-for-it-architects)
    - [Proteção de identidade e dispositivo para o Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    - [Soluções de proteção de arquivos do Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    - [Proteção de Informações do Office 365 para o RGPD](#office-365-information-protection-for-gdpr)
    - [Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações do Agile](#microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations)
    - [Soluções de telefonia da Microsoft](#microsoft-telephony-solutions) 
    - [Implantar uma área de trabalho segura e moderna com a Microsoft](microsoft-cloud-it-architecture-resources.md#msd)
    
Dê sua opinião! Envie um email para [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 

<!--
<a name="roadmap"></a>
## Microsoft's Enterprise Cloud Roadmap

See the posters, icon sets, community venues, and other resources that describe the industry's most complete cloud solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumbnail for Enterprise Cloud Roadmap](media/c8b293b9-5992-4d29-b579-a6bbbd59d8d6.png)          ](https://aka.ms/cloudarchitecture) <br/> [Microsoft's Enterprise Cloud Roadmap](https://aka.ms/cloudarchitecture) (https://aka.ms/cloudarchitecture) <br/> |Swipe through this Sway experience for the resources that describe the industry's most complete cloud solution.  <br/> |
-->
  
<a name="cloudarch"></a>
## Série Microsoft Cloud para arquitetos corporativos

Esses cartazes de arquitetura em nuvem proporcionam informações sobre os serviços em nuvem da Microsoft, incluindo o Office 365, Azure Active Directory, Microsoft Intune, Microsoft Dynamics CRM Online e soluções híbridas no local e em nuvem. Os arquitetos e tomadores de decisões da TI podem usar esses recursos para determinar as soluções ideais para suas cargas de trabalho e para tomar decisões em relação aos principais componentes de infraestrutura, como a identidade e a segurança.

<!--  
<a name="platformoptions"></a>
### Microsoft Cloud Services and Platform Options

Learn key differences between Microsoft cloud services and platform offerings. Find the best fit for your solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumb image of cloud architecture model with service options](media/ff5c74e2-afc6-40c1-9292-cc4cb128cdd1.png)          ](https://www.microsoft.com/download/details.aspx?id=54432) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524731)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=524732)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=54432) <br/> | This model describes: <ul><li>  Software as a Service (SaaS) offerings, including Office 365 </li><li>  Platform as a Service (PaaS) features in Microsoft Azure </li><li>  Infrastructure as a Service (IaaS) features in Microsoft Azure </li><li>  Private cloud datacenter capabilities using Windows Server and System Center </li><li>  Learn how Microsoft's own IT department is migrating to these cloud services and building its hybrid cloud. </li></ul><br/>|
-->

   
<a name="identity"></a>
### Identidade do Microsoft Cloud para arquitetos corporativos

O que os arquitetos de TI precisam saber sobre a criação de identidade para organizações que usam plataformas e serviços em nuvem da Microsoft.
  
|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura do modelo de identidade de nuvem da Microsoft](media/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png)          ](https://www.microsoft.com/download/details.aspx?id=54431) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586)  \| [Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd)           \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=54431) <br/> | Este modelo contém: <ul><li>Introdução à identidade com a nuvem da Microsoft </li><li>Recursos do Azure AD IDaaS </li><li>Integração de contas do Active Directory Domain Services no local com o Microsoft Azure Active Directory </li><li>Colocando componentes de diretório no Azure </li><li>Opções de serviços de domínio para cargas de trabalho no Azure IaaS </li></ul><br/>|
   
<a name="security"></a>
### <a name="microsoft-cloud-security-for-enterprise-architects"></a>Segurança no Microsoft Cloud para arquitetos corporativos

O que os arquitetos de TI precisam saber sobre segurança em plataformas e serviços em nuvem da Microsoft.
  
|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura do modelo de segurança em nuvem da Microsoft](media/5dc26f80-8888-4572-8ed9-a120d711e0f0.png)          ](https://www.microsoft.com/download/details.aspx?id=48121) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842070)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=842071)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=48121) <br/> | Este modelo contém: <ul><li>Função da Microsoft no fornecimento de plataformas e serviços seguros</li><li>Responsabilidade do cliente em reduzir os riscos de segurança</li><li>Principais certificações de segurança </li><li>Ofertas de segurança fornecidas pelos serviços de consultoria da Microsoft </ul><br/>|
   
<a name="networking"></a>
### <a name="microsoft-cloud-networking-for-enterprise-architects"></a>Rede do Microsoft Cloud para arquitetos corporativos

O que os arquitetos de TI precisam saber sobre redes para plataformas e serviços em nuvem da Microsoft.
  
|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura do modelo de sistema de rede em nuvem da Microsoft](media/95e8ab6a-b4d0-4836-acc1-b0b77ebf46e6.png)](media/Network-Poster/MSFT_cloud_architecture_networking.pdf) <br/> [PDF](media/Network-Poster/MSFT_cloud_architecture_networking.pdf)  \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Network-Poster/MSFT_cloud_architecture_networking.vsdx) <br/> | Este modelo contém: <ul><li> Expandindo sua rede para conectividade de nuvem </li><li> Elementos comuns de conectividade de nuvem da Microsoft </li><li> ExpressRoute para conectividade de nuvem da Microsoft </li><li> Criação de rede para o Microsoft IaaS, Azure PaaS e Azure IaaS </li></ul><br/>  <br/>|

<a name="hybrid"></a>
### <a name="microsoft-hybrid-cloud-for-enterprise-architects"></a>Nuvem híbrida da Microsoft para arquitetos corporativos

O que os arquitetos de TI precisam saber sobre nuvem híbrida dos serviços e plataformas da Microsoft.
  
|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura do modelo híbrido em nuvem da Microsoft](media/9989c71e-f6a0-4dbe-906c-43e67b3ce537.png)](media/Hybrid-Poster/MSFT_cloud_architecture_hybrid.pdf) <br/> [PDF](media/Hybrid-Poster/MSFT_cloud_architecture_hybrid.pdf)  \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Hybrid-Poster/MSFT_cloud_architecture_hybrid.vsdx)  | Este modelo contém: <ul><li> Ofertas de nuvem da Microsoft (SaaS, Azure PaaS e Azure IaaS) e seus elementos em comum </li><li> Arquitetura de nuvem híbrida para as ofertas de nuvem da Microsoft </li><li> Cenários de nuvem híbrida para o Microsoft SaaS (Office 365), Azure PaaS e Azure IaaS </li></ul><br/>|
   
<a name="attacks"></a>
### <a name="common-attacks-and-microsoft-capabilities-that-protect-your-organization"></a>Ataques comuns e recursos da Microsoft que protegem sua organização
Conheça os ataques cibernéticos mais comuns e saiba como a Microsoft pode ajudar sua organização em cada etapa de um ataque. 

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura do cartaz de Ataques comuns.](media/common%20attacks-thumb3.png) ](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) <br/> [PDF](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) \| [Visio](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.vsdx) <br/> | Este cartaz ilustra o caminho dos ataques comuns e descreve quais recursos ajudam a impedir os invasores em cada etapa de um ataque. <br/>|

<a name="m365foundationinfra"></a>
### <a name="microsoft-365-enterprise-foundation-infrastructure"></a>Infraestrutura de base do Microsoft 365 Enterprise

Obtenha uma visão geral da [infraestrutura de base](https://docs.microsoft.com/microsoft-365/enterprise/deploy-foundation-infrastructure) do Microsoft 365 Enterprise para começar sua implantação.
  
|**Item**|**Descrição**|
|:-----|:-----|
|[![Miniatura do pôster de infraestrutura de base do Microsoft 365 Enterprise](media/Microsoft365EnterpriseFoundInfra-thumb.png)](https://aka.ms/m365efoundinfraposter) <br/> [Exibir online](https://aka.ms/m365efoundinfraposter) \| [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/deploy-foundation-infrastructure/Microsoft365EnterpriseFoundInfra.pdf) <br/> | Este pôster resume cada fase da infraestrutura de base em termos de metas, recursos e ferramentas, decisões de design, resultados de configuração, integração, atualizações e monitoramento contínuos. <br/>| 

### <a name="architecture-approaches-for-microsoft-cloud-tenant-to-tenant-migrations"></a>Abordagens de arquitetura para as migrações de locatário do Microsoft Cloud para o locatário 
Esta série de tópicos ilustra várias abordagens de arquitetura para fusões, aquisições, despojamento e outros cenários que podem levar você a migrar para um novo locatário de nuvem. Esses tópicos fornecem diretrizes de ponto de partida para o planejamento.

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura para o cartaz de arquitetura lógica do Teams](downloads/msft-tenant-to-tenant-migration-thumb.png)](downloads/Microsoft-365-tenant-to-tenant-migration.pdf) <br/> [PDF](downloads/Microsoft-365-tenant-to-tenant-migration.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/Microsoft-365-tenant-to-tenant-migration.vsdx)     |Este modelo contém: <ul><li>Um mapeamento de cenários de negócios para abordagens de arquitetura</li><li>Considerações de design</li><li>Fluxo de migração de evento único</li><li>Fluxos de migração do usuário</li><li>Fluxo de movimentação ou de divisão do locatário</li></ul>|

<a name="BKMK_o365solutions"></a>
## <a name="microsoft-365-enterprise-solution-series"></a>Série de solução do Microsoft 365 Enterprise

A série de solução do Microsoft 365 Enterprise fornece orientações para a implementação de recursos do Microsoft 365, especialmente quando os recursos e as tecnologias se encontram.

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams e serviços de produtividade relacionados no Microsoft 365 para arquitetos de TI
A arquitetura lógica dos serviços de produtividade no Microsoft 365, liderada pelo Microsoft Teams.

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura para o cartaz de arquitetura lógica do Teams](downloads/msft-teams-logical-architecture-thumb.png)](downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)     |A Microsoft fornece um conjunto de serviços de produtividade que trabalham juntos para fornecer experiências de colaboração com recursos de governança de dados, segurança e conformidade. <br/> <br/>Esta série de ilustrações oferece uma visão da arquitetura lógica dos serviços de produtividade para arquitetos empresariais, liderada pelo Microsoft Teams.|


### <a name="groups-in-microsoft-365-for-it-architects"></a>Grupos no Microsoft 365 para arquitetos de TI
O que os arquitetos de TI precisam saber sobre os grupos no Microsoft 365

|**Item**|**Descrição**|
|:-----|:-----|
|[![Imagem em miniatura de infográfico sobre os grupos](downloads/msft-m365-groups-architecture-thumb.png)](downloads/msft-m365-groups.pdf) <br/> [PDF](downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) |Essas ilustrações detalham os diferentes tipos de grupos, como eles são criados e gerenciados e algumas recomendações de governança.|

   
<a name="BKMK_O365IDP"></a>
### <a name="identity-and-device-protection-for-office-365"></a>Proteção de identidade e dispositivo para o Office 365

Recursos recomendados para proteger identidades e dispositivos que acessam o Office 365, outros serviços SaaS e aplicativos locais publicados com o Proxy de Aplicativo do Azure AD.
  
|**Item**|**Descrição**|
|:-----|:-----|
|[![Pôster de modelo: proteção de identidade e do dispositivo para o Office 365 e outros aplicativos SaaS](media/c1cfb31b-5150-45ff-b46c-3a237e9f5581.png)          ](https://www.microsoft.com/download/details.aspx?id=55032) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=841656)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657)  \| [Mais idiomas](https://www.microsoft.com/download/details.aspx?id=55032) <br/> |É importante usar níveis consistentes de proteção em seus dados, identidades e dispositivos. Este documento mostra quais recursos são comparáveis com mais informações sobre recursos para proteger identidades e dispositivos.  <br/> |
   
<a name="BKMK_O365fileprotect"></a>
### <a name="file-protection-solutions-in-office-365"></a>Soluções de proteção de arquivos do Office 365

Recursos recomendados para proteção de arquivos do Office 365 com base em três níveis diferentes de confidencialidade.
  
|**Item**|**Descrição**|
|:-----|:-----|
|[![Miniatura de conjunto de minicartazes de soluções para proteção de arquivos no Office 365](media/24be68b5-d852-4fdb-94ad-94491a19edd8.png)          ](https://www.microsoft.com/download/details.aspx?id=55523) <br/> [PDF](https://go.microsoft.com/fwlink/?linkid=2004320)  \| [Visio](https://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.vsdx) <br/> |É importante usar níveis consistentes de proteção para dados, identidades e dispositivos. Este documento mostra quais recursos são comparáveis com mais informações sobre recursos para proteger os arquivos do Office 365.  <br/> |
   

### <a name="office-365-information-protection-for-gdpr"></a>Proteção de Informações do Office 365 para RGPD

Recomendações prescritivas para descoberta, classificação, proteção e monitoramento de dados pessoais. Ela usa o GDRP (Regulamento Geral sobre a Proteção de Dados) como exemplo, mas é possível aplicar o mesmo processo a fim de a cumprir os requisitos de vários outros regulamentos.

|**Item**|**Descrição**|
|:-----|:-----|
|![Miniatural para a Proteção de Informações do Office 365 para o RGPD](media/o365infoprotectforgdpr-thumb.png)  <br/> [PDF](https://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.pdf) \| [Visio](https://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.vsdx)    |Para ver esse conteúdo em formato de artigo, confira [Proteção de informações do Office 365 para o GDPR](https://docs.microsoft.com/Office365/SecurityCompliance/office-365-information-protection-for-gdpr).      |

### <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a>Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile 

Estas diretrizes descrevem como implementar um ambiente de nuvem seguro. As diretrizes da solução podem ser usadas por qualquer organização. Isso inclui ajuda adicional para organizações ágeis com contas de convidado e acesso BYOD. Você pode usar essas diretrizes como o ponto inicial para a criação do seu ambiente. 


|**Item**|**Descrição**|
|:-----|:-----|
|**Diretrizes de segurança da Microsoft para campanhas políticas** <br/> [![Miniatura para conjunto de minipôsteres.](media/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf) <br/> [PDF](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)  \| [Visio](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.vsdx) <br/> |Este guia usa uma organização de campanha política como exemplo. Use este guia como um ponto de partida para qualquer ambiente.  <br/> |
|**Diretrizes de segurança da Microsoft para organizações sem fins lucrativos** <br/> [![Imagem em miniatura para arquivos disponíveis para download](media/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf) <br/> [PDF](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)  \| [Visio](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.vsdx) <br/> |Este guia é ligeiramente revisado para organizações sem fins lucrativos. Por exemplo, ele faz referência aos planos do Office 365 para entidades sem fins lucrativos. As diretrizes técnicas são as mesmas do guia de solução de campanha política.  <br/> |

Este guia contém as Guias de laboratório de teste. Para saber mais, confira [Diretrizes de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágeis](https://docs.microsoft.com/Office365/SecurityCompliance/microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o).

### <a name="microsoft-telephony-solutions"></a>Soluções de telefonia da Microsoft

A Microsoft oferece suporte a várias opções conforme você começa sua jornada no Teams na nuvem da Microsoft. Esse cartaz ajuda você a decidir qual solução de telefonia da Microsoft (sistema de telefone na nuvem ou o Enterprise Voice local) é ideal para os usuários de sua organização e como sua organização pode se conectar à Rede pública de telefonia comutada (PSTN).

![Miniatura do cartaz de Soluções de telefonia da Microsoft](media/microsoft-telephony-solutions-thumb.png) <br/>
[PDF](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.pdf) | [Visio](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.vsdx) 

Para saber mais, confira o artigo neste cartaz: [Soluções de telefonia da Microsoft](https://docs.microsoft.com/SkypeForBusiness/hybrid/msft-telephony-solutions).
  
<a name="msd"></a>
### <a name="deploy-a-modern-and-secure-desktop-with-microsoft"></a>Implantar uma área de trabalho segura e moderna com a Microsoft

O que os arquitetos de TI precisam saber sobre implantação e gerenciamento de atualizações para o Office 365 ProPlus no Windows 10.
  
|**Item**|**Descrição**|
|:-----|:-----|
|[![Miniatura do modelo Implantar uma área de trabalho segura e moderna com a Microsoft](media/321dd59c-d992-4c7a-a7b6-c23a783858bd.png)          ](https://www.microsoft.com/download/details.aspx?id=55987) <br/> [PDF](https://download.microsoft.com/download/4/E/9/4E90E227-770A-41D1-99FE-925A64D81A55/MSFT_modern_secure_desktop.pdf)  \| [Visio](https://download.microsoft.com/download/4/E/9/4E90E227-770A-41D1-99FE-925A64D81A55/MSFT_modern_secure_desktop.vsdx) <br/> | Este modelo contém: <ul><li>  Implantação do Windows 10 e Office ProPlus da nuvem da Microsoft </li><li>  Implementar o Windows 10 e Office ProPlus com o System Center Configuration Manager </li><li>  Gerenciamento de atualizações do Windows 10 e Office ProPlus da nuvem da Microsoft </li><li>  Gerenciar as atualizações do Windows 10 e Office ProPlus com o Microsoft Endpoint Configuration Manager </li><li>  Recursos adicionais de proteção do Windows 10 </li></ul><br/> |
   
## <a name="see-also"></a>Confira também

[Modelos de arquitetura para SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Soluções de segurança](security-solutions.md)
  
[Soluções híbridas](hybrid-solutions.md)

