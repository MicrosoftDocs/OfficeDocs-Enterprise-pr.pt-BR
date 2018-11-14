---
title: Colaboração entre locatários do Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Saiba como a colaboração do Office 365 funciona entre organizações e inquilinos.
ms.openlocfilehash: ec844f78a0ae31469c2ca92c5cb97d965bdb3508
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219881"
---
# <a name="office-365-inter-tenant-collaboration"></a>Colaboração entre locatários do Office 365

Este artigo descreve várias maneiras de colaborar entre dois locatários do Office 365. Ele foi projetado para administradores do Office 365.
  
Suponha que duas organizações, Fabrikam e Contoso, cada tem um Office 365 para o locatário de negócios e eles desejam trabalhar juntos em vários projetos; Alguns deles são executados por um tempo limitado e alguns deles estão em andamento. Como Fabrikam e Contoso habilitar seus pessoas e equipes colaborar com mais eficiência nos seus locatários diferentes do Office 365 de forma segura? O Office 365, juntamente com o Windows Azure Active Directory B2B colaboração, fornece várias opções. Este artigo descreve vários cenários principais que podem ser considerados Fabrikam e Contoso.
  
Opções de colaboração entre locatários do Office 365 incluem o uso de um local central para arquivos e conversas, compartilhando calendários, o uso de mensagens Instantâneas, chamadas de áudio/vídeo para comunicação e proteger o acesso aos recursos e aplicativos. Use as tabelas a seguir para saber mais e selecione soluções.
  
## <a name="exchange-online-collaboration-options"></a>Opções de colaboração on-line do Exchange

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Compartilhar calendários com outra organização do Office 365  <br/> |Os administradores podem configurar diferentes níveis de acesso de calendário no Exchange Online para permitir que as empresas colaborar com outras empresas e para permitir que os usuários compartilhem os agendamentos (informações de livre/ocupado) com outras pessoas  <br/> |[Compartilhando no Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relacionamentos de organização no Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Criar um relacionamento de organização no Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modificar e o relacionamento de organização no Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Remover um relacionamento de organização no Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Compartilhar calendários com usuários externos](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd)
 <br/> |
|Controlar como os usuários compartilhar seus calendários com pessoas fora da sua organização  <br/> |Os administradores de aplicar as políticas de compartilhamento às caixas de correio de usuários para controlar o que ela possa ser compartilhada com e o nível de acesso concedido  <br/> |[Compartilhamento de políticas no Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Criar uma política de compartilhamento no Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Aplicar uma política de compartilhamento às caixas de correio no Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modificar, desabilitar ou remover uma política de compartilhamento no Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurar os canais de email seguro e controlar o fluxo de emails com organizações parceiras  <br/> |Os administradores criar conectores para aplicar segurança a trocas de email com uma organização parceira ou o provedor de serviços. Os conectores impor a criptografia via segurança de camada de transporte (TLS), além de permitir restrições em nomes de domínio ou seu email de envio de parceiros de intervalos de endereços IP.  <br/> |[Como o Exchange Online usa o TLS para proteger conexões de email no Office 365](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Domínios remotos no Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configurar o conector para o fluxo de email seguro com uma organização parceira](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Práticas recomendadas de fluxo de emails para Exchange Online e Office 365 (visão geral)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online e OneDrive para opções de colaboração de negócios

|**Metas de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Compartilhar documentos e sites com usuários externos  <br/> |Os administradores configurar compartilhamento de locatário ou as contas autenticadas ou convidadas de conta de nível do conjunto de sites para a conta da Microsoft autenticados, trabalho ou escola  <br/> |[Gerenciar o compartilhamento externo para o ambiente do SharePoint Online](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Domínios restritos compartilhamento no Office 365 SharePoint Online e o OneDrive for Business](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Usar o SharePoint Online como uma solução de extranet business-to-business (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Controlando e controlando compartilhamento externo para usuários finais  <br/> |OneDrive para os proprietários dos arquivos de negócios e usuários do SharePoint Online finais configurar sites e compartilhamento de documentos e estabelecer notificações para rastrear o compartilhamento  <br/> |[Configurar as notificações de compartilhamento externo do OneDrive for Business](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Compartilhar arquivos ou pastas do SharePoint no Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype para opções de colaboração de negócios

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Skype para negócios Online - chamadas, mensagens Instantâneas e presença com outra Skype para usuários comerciais  <br/> |Os administradores podem habilitar seu Skype para que os usuários corporativos Online mensagens Instantâneas, fazer chamadas de áudio/vídeo e vejam a presença com usuários em outro locatário do Office 365.  <br/> |[Permitir que os usuários entrem em contato com usuários externos do Skype for Business](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype para negócios Online - IM, presença com usuários do Skype (consumidor) e chamadas  <br/> |Os administradores podem habilitar seu Skype para que os usuários corporativos Online mensagens Instantâneas, fazer chamadas e vejam a presença com usuários do Skype (consumidor).  <br/> |[Permitir que o Skype para usuários comerciais adicionar contatos do Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Opções do Azure AD B2B colaboração

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Colaboração de Azure AD B2B - compartilhamento com a adição de usuários externos a um grupo no diretório da organização de conteúdo  <br/> |Um administrador global para um locatário do Office 365 pode convidar pessoas em outro locatário do Office 365 para ingressar em seu diretório, adicione os usuários externos a um grupo e conceder acesso a conteúdo, como sites do SharePoint e bibliotecas para o grupo.  <br/> |[Qual é a visualização de colaboração do Windows Azure AD B2B?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [B2B do Azure AD: Novas atualizações facilitam a colaboração entre negócios](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Compartilhamento externo do Office 365 e colaboração do Windows Azure Active Directory B2B](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Colaboração de B2B do diretório ativo Azure API e personalização](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD e mostrar de identidade: colaboração B2B do Azure AD (Business to Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Opções de colaboração do Office 365

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Grupos do Office 365 - Email, calendário, OneNote e arquivos compartilhados em um local centralizado  <br/> |Há suporte para grupos no Essentials Business, Business Premium, educação e os planos de Enterprise E1, E3 e E5. Pessoas em um locatário do Office 365 podem criar um grupo e convidar pessoas em outro locatário do Office 365, como usuários convidados. Aplica-se ao Dynamics CRM também.  <br/> |[Saiba mais sobre os grupos do Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Acesso de convidado em grupos do Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Implantar o Office 365 grupos](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Opções de colaboração do Yammer

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Yammer - colaboração por meio de uma mídia social do enterprise  <br/> |A menos que a capacidade de criar grupos externos estiver desabilitada por um administrador do Yammer, os usuários podem criar grupos externos para colaborar no Yammer por meio de conversas, a capacidade de like e siga as postagens, compartilhar arquivos e chat online.  <br/> |[Criar e gerenciar grupos externos no Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Opções de colaboração de equipes

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Colaborar em equipes com usuários externos para a organização  <br/> |Um administrador global do inquilino do Office 365 convidando precisa habilitar colaboração externa em equipes. Proprietários de equipe e administradores globais agora poderão convidar qualquer pessoa com um endereço de email a colaboração em equipes.  <br/> Os administradores também podem gerenciar e editar o convidados já está presentes no seu locatário.  <br/> |[Autorizar o acesso de convidado](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Ativar ou desativar o acesso de convidado em equipes](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Usar o PowerShell para controlar o acesso de convidado](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Lista de verificação de acesso de convidado](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Exibir usuários de convidado](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Editar informações do usuário convidado](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|Os proprietários de equipe podem convidar e gerenciar como convidados colaboram em suas equipes.  <br/> |Os proprietários de equipe têm controles adicionais no que os convidados podem fazer em suas equipes.  <br/> |[Adicionar convidados](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Adicionar um convidado para uma equipe](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Gerenciar o acesso de convidado em equipes](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Ver quem está em uma equipe ou em um canal](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Convidados de outros tenants podem exibir o conteúdo em equipes e colaborar com outros membros  <br/> |Nenhum(a).  <br/> |[A experiência de acesso de convidado](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Opções de colaboração do Power BI

|**Meta de compartilhamento**|**Ação administrativa**|**Informações de instruções**|
|:-----|:-----|:-----|
|Power BI permite aos usuários externos convidado consumir conteúdo compartilhado para acessá-los por meio de links. Isso permite que os usuários da organização distribuir o conteúdo de forma segura entre as organizações.<br/> | O administrador do Power BI pode controlar se os usuários podem convidar usuários externos para exibir o conteúdo dentro da organização. <br/> |[Distribuir o conteúdo do Power BI para usuários de convidado externo com o Windows Azure AD B2B](https://docs.microsoft.com/en-us/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Pontos a serem consideradas sobre a colaboração de entre locatários do Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Compartilhamento de armazenamento, licenças, assinaturas e contas de usuário

Cada organização mantenha seu próprio contas de usuário, as identidades, grupos de segurança, assinaturas, licenças e armazenamento. Pessoas usam os recursos de colaboração no Office 365 em conjunto com o compartilhamento de políticas e configurações de segurança para fornecer acesso às informações necessárias, mantendo o controle dos ativos da empresa.
  
- **Contas de usuário:** Contas não podem ser compartilhadas e contas não podem ser duplicadas entre os locatários ou partições em que os serviços de diretório Active Directory local. 
    
- **Licenças &amp; inscrições:** No Office 365, licencia para planos de licenciamento (também chamado de SKUs ou do Office 365 estiver planejando) conceder aos usuários acesso aos serviços do Office 365 que são definidos para esses planos. 
    
- **Armazenamento:** Planos do Office 365, limites de software e limites para o SharePoint Online são gerenciados separadamente de limites de armazenamento de caixa de correio. Limites de armazenamento de caixa de correio são configurados e gerenciados usando o Exchange Online. Em ambos os cenários de armazenamento não pode ser compartilhado cruzado inquilinos. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>Podemos podem compartilhar espaços para nome de domínio entre locatários do Office 365?

Não. Domínios de vanity, fabrikam.com ou tailspintoys.com, só podem ser associados e usados com um locatário no momento. Cada inquilino deve ter seu próprio namespace; Espaços para nome UPN, SMTP e SIP não podem ser compartilhados entre locatários.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>E quanto a colaboração de entre locatários do Office 365 e componentes híbrida?

Componentes híbridos locais, como uma organização do Exchange e conectar do Azure AD, não podem ser divididos em vários locatários.
  

