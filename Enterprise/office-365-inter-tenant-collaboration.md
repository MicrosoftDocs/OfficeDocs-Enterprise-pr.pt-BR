---
title: Colaboração interlocatário do Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-collaboration
- M365-subscription-management
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Saiba como o Office 365 Collaboration funciona em locatários e organizações.
ms.openlocfilehash: f68b04fe1b4d8acd26fc866bb88c09a16bb242de
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031216"
---
# <a name="office-365-inter-tenant-collaboration"></a>Colaboração interlocatário do Office 365

Este artigo descreve várias maneiras de colaborar entre dois locatários do Office 365. Destina-se aos administradores do Office 365.
  
Suponha que duas organizações, a Fabrikam e a contoso, tenham um locatário do Office 365 for Business e queiram trabalhar juntas em vários projetos; alguns dos quais são executados por um tempo limitado e alguns estão em andamento. Como a Fabrikam e a contoso podem permitir que suas pessoas e equipes colaborem com mais eficiência em seus diferentes locatários do Office 365 de uma maneira segura? O Office 365, em conjunto com a colaboração B2B do Azure Active Directory, oferece várias opções. Este artigo descreve vários cenários importantes que a Fabrikam e a contoso podem considerar.
  
As opções de colaboração entre locatários do Office 365 incluem o uso de um local central para arquivos e conversas, compartilhamento de calendários, uso de mensagens instantâneas, chamadas de áudio/vídeo para comunicação e proteção do acesso a recursos e aplicativos. Use as tabelas a seguir para selecionar soluções e saiba mais.
  
## <a name="exchange-online-collaboration-options"></a>Opções de colaboração do Exchange Online

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Compartilhar calendários com outra organização do Office 365  <br/> |Os administradores podem configurar diferentes níveis de acesso de calendário no Exchange Online para permitir que as empresas colaborem com outras empresas e para permitir que os usuários compartilhem as agendas (informações de disponibilidade) com outras pessoas  <br/> |[Compartilhamento no Exchange Online](https://technet.microsoft.com/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relações de organização no Exchange Online](https://technet.microsoft.com/library/jj916658%28v=exchg.150%29.aspx) <br/> [Criar um relacionamento de organização no Exchange Online](https://technet.microsoft.com/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modificar e relações de organização no Exchange Online](https://technet.microsoft.com/library/jj916659%28v=exchg.150%29.aspx) <br/> [Remover um relacionamento de organização no Exchange Online](https://technet.microsoft.com/library/jj916657%28v=exchg.150%29.aspx) <br/> [Compartilhar calendários com usuários externos](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd)
 <br/> |
|Controlar como os usuários compartilham seus calendários com pessoas de fora da sua organização  <br/> |Os administradores aplicam políticas de compartilhamento a caixas de correio de usuários para controlar quem pode ser compartilhado e o nível de acesso concedido  <br/> |[Políticas de compartilhamento no Exchange Online](https://technet.microsoft.com/library/jj916673%28v=exchg.150%29.aspx) <br/> [Criar uma política de compartilhamento no Exchange Online](https://technet.microsoft.com/library/jj916676%28v=exchg.150%29.aspx) <br/> [Aplicar uma política de compartilhamento a caixas de correio no Exchange Online](https://technet.microsoft.com/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modificar, desabilitar ou remover uma política de compartilhamento no Exchange Online](https://technet.microsoft.com/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurar canais de email seguro e controlar o fluxo de emails com organizações parceiras  <br/> |Os administradores criam conectores para aplicar segurança a trocas de email com uma organização de parceiro ou um provedor de serviços. Os conectores aplicam criptografia via protocolo TLS, além de permitir restrições em nomes de domínio ou intervalos de endereços IP dos quais seus parceiros enviam email.  <br/> |[Como o Exchange Online usa o TLS para proteger conexões de email no Office 365](https://technet.microsoft.com/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Domínios remotos no Exchange Online](https://technet.microsoft.com/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configurar o conector para o fluxo de email seguro com uma organização parceira](https://technet.microsoft.com/library/dn751021%28v=exchg.150%29.aspx) <br/> [Práticas recomendadas de fluxo de emails para Exchange Online e Office 365 (visão geral)](https://technet.microsoft.com/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>Opções de colaboração do SharePoint Online e do OneDrive for Business

|**Compartilhando metas**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Compartilhar sites e documentos com usuários externos  <br/> |Os administradores configuram o compartilhamento no locatário ou no nível do conjunto de sites para contas da conta da Microsoft, de conta de trabalho ou da escola autenticadas ou de convidado  <br/> |[Gerenciar compartilhamento externo para o ambiente do SharePoint Online](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Compartilhamento de domínios restritos no Office 365 SharePoint Online e no OneDrive for Business](https://support.office.com/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Usar o SharePoint Online como uma solução de extranet B2B (entre empresas)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Controlar e controlar o compartilhamento externo para usuários finais  <br/> |Proprietários de arquivos do OneDrive for Business e usuários finais do SharePoint Online configurar o compartilhamento de sites e documentos e estabelecer notificações para controlar o compartilhamento  <br/> |[Configurar notificações para compartilhamento externo para o OneDrive for Business](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Compartilhar arquivos ou pastas do SharePoint no Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Opções de colaboração do Skype for Business

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Skype for Business online-IM, chamadas e presença com outros usuários do Skype for Business  <br/> |Os administradores podem habilitar seus usuários do Skype for Business online para mensagens instantâneas, fazer chamadas de áudio/vídeo e ver a presença com usuários em outro locatário do Office 365.  <br/> |[Permitir que os usuários entrem em contato com usuários externos do Skype for Business](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype for Business online-IM, chamadas e presença com usuários do Skype (consumidor)  <br/> |Os administradores podem habilitar seus usuários do Skype for Business online para mensagens instantâneas, fazer chamadas e ver a presença com usuários do Skype (consumidor).  <br/> |[Permitir que os usuários do Skype for Business adicionem contatos do Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Opções de colaboração B2B do Azure AD

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Colaboração B2B do Azure AD – compartilhamento de conteúdo adicionando usuários externos a um grupo no diretório de uma organização  <br/> |Um administrador global para um locatário do Office 365 pode convidar pessoas de outro locatário do Office 365 para ingressar no seu diretório, adicionar esses usuários externos a um grupo e conceder acesso ao conteúdo, como bibliotecas e sites do SharePoint para o grupo.  <br/> |[O que é a visualização de colaboração B2B do Azure AD?](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [B2B do Azure AD: novas atualizações fazem collab fácil de negócios](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Compartilhamento externo do Office 365 e colaboração B2B do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Personalização e API de colaboração B2B do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD e identidade mostrar: colaboração B2B do Azure AD (negócios para negócios](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Opções de colaboração do Office 365

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Grupos do Office 365-email, calendário, OneNote e arquivos compartilhados em um local central  <br/> |Os grupos têm suporte nos planos Business Essentials, Business Premium, Education e Enterprise E1, E3 e e5. Pessoas em um locatário do Office 365 podem criar um grupo e convidar pessoas em outro locatário do Office 365 como usuários convidados. Aplica-se ao Dynamics CRM também.  <br/> |[Saiba mais sobre os grupos do Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Acesso de convidados nos grupos do Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Implantar grupos do Office 365](https://technet.microsoft.com/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Opções de colaboração do Yammer

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Yammer-colaboração por meio de um meio social corporativo  <br/> |A menos que a capacidade de criar grupos externos seja desabilitada por um administrador do Yammer, os usuários podem criar grupos externos para colaborar no Yammer através de conversas, a capacidade de seguir e acompanhar postagens, compartilhar arquivos e bater papo online.  <br/> |[Criar e gerenciar grupos externos no Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Opções de colaboração do teams

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Colaborar no Microsoft Teams com usuários externos à organização  <br/> |Um administrador global para o locatário convite do Office 365 precisa habilitar a colaboração externa no Microsoft Teams. Administradores globais e proprietários de equipe agora poderão convidar qualquer pessoa com um endereço de email para colaborar no Microsoft Teams.  <br/> Os administradores também podem gerenciar e editar convidados já presentes no locatário.  <br/> |[Autorizar acesso de convidados](https://docs.microsoft.com/microsoftteams/teams-dependencies) <br/> [Ativar ou desativar o acesso de convidados no Microsoft Teams](https://docs.microsoft.com/microsoftteams/set-up-guests) <br/> [Usar o PowerShell para controlar o acesso de convidados](https://docs.microsoft.com/microsoftteams/guest-access-powershell) <br/> [Lista de verificação de acesso de convidados](https://docs.microsoft.com/microsoftteams/guest-access-checklist) <br/> [Exibir usuários convidados](https://docs.microsoft.com/microsoftteams/view-guests) <br/> [Editar informações do usuário convidado](https://docs.microsoft.com/microsoftteams/edit-guests-information) <br/> |
|Os proprietários de equipe podem convidar e gerenciar como os convidados colaboram dentro de suas equipes.  <br/> |Os proprietários de equipe têm controles adicionais sobre o que os convidados podem fazer em suas equipes.  <br/> |[Adicionar convidados](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Adicionar um convidado a uma equipe](https://docs.microsoft.com/microsoftteams/add-guests) <br/> [Gerenciar o acesso de convidados no Teams](https://docs.microsoft.com/microsoftteams/manage-guests) <br/> [Ver quem está em uma equipe ou em um canal](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Convidados de outros locatários podem exibir conteúdo no Teams e colaborar com outros membros  <br/> |Nenhum.  <br/> |[A experiência de acesso de convidados](https://docs.microsoft.com/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Opções de colaboração do Power BI

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|O Power BI permite que usuários convidados externos consumam conteúdo compartilhado por meio de links. Isso permite que os usuários da organização distribuam conteúdo de uma maneira segura entre as organizações.<br/> | O administrador do Power BI pode controlar se os usuários podem convidar usuários externos para exibir conteúdo dentro da organização. <br/> |[Distribuir conteúdo do Power BI para usuários convidados externos com o Azure AD B2B](https://docs.microsoft.com/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Pontos a serem cientes sobre a colaboração entre locatários do Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Compartilhamento de contas de usuário, licenças, assinaturas e armazenamento

Cada organização mantém suas próprias contas de usuário, identidades, grupos de segurança, assinaturas, licenças e armazenamento. As pessoas usam os recursos de colaboração no Office 365 junto com políticas de compartilhamento e configurações de segurança para fornecer acesso às informações necessárias, mantendo o controle dos ativos da empresa.
  
- **Contas de usuário:** As contas não podem ser compartilhadas e as contas não podem ser duplicadas entre os locatários ou partições nos serviços de diretório do Active Directory local. 
    
- **Assinaturas &amp; de licenças:** No Office 365, as licenças de planos de licenciamento (também chamados de SKUs ou planos do Office 365) dão aos usuários acesso aos serviços do Office 365 definidos para esses planos. 
    
- **Armazenamento:** Nos planos do Office 365, os limites do software e os limites do SharePoint Online são gerenciados separadamente dos limites de armazenamento da caixa de correio. Os limites de armazenamento de caixa de correio são configurados e gerenciados usando o Exchange Online. Em ambos os cenários, o armazenamento não pode ser compartilhadas entre locatários. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Podemos compartilhar namespaces de domínio nos locatários do Office 365?

Não. Os domínios do personalizado, como fabrikam.com ou tailspintoys.com, só podem ser associados e usados com um locatário no momento. Cada locatário deve ter seu próprio namespace; Os namespaces de UPN, SMTP e SIP não podem ser compartilhados entre locatários.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>E os componentes híbridos e a colaboração entre locatários do Office 365?

Os componentes híbridos locais, como uma organização do Exchange e o Azure AD Connect, não podem ser divididos em vários locatários.
  

