---
title: Integração do Azure com o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Sua assinatura do Office 365 inclui uma assinatura do Azure AD. Integre o Office 365 com o Azure AD se você quiser sincronização de senha ou logon único com seu ambiente local.
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085470"
---
# <a name="azure-integration-with-office-365"></a>Integração do Azure com o Office 365

O Office 365 usa o Azure Active Directory (Azure AD) para gerenciar as identidades de usuário em segundo plano. Sua assinatura do Office 365 inclui uma assinatura gratuita do Azure AD para que você possa integrar o Office 365 ao Azure AD se quiser sincronizar senhas ou configurar o logon único com seu ambiente local. Você também pode comprar recursos avançados para gerenciar melhor suas contas.
  
O Azure também oferece outras funcionalidades, como gerenciamento de aplicativos integrados, que você pode usar para estender e personalizar suas assinaturas do Office 365.
  
Você pode usar os consultores de implantação do Azure AD para uma experiência de instalação e configuração conduzida:
 - [Supervisor de conexão do Azure AD](https://aka.ms/aadconnectpwsync)
 - [Supervisor de implantação do AD FS](https://aka.ms/adfsguidance)
 - [Assistente de implantação do Azure RMS](https://aka.ms/azuremsguidance)
 - [Guia de instalação do Azure AD Premium](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Edições do Azure Active Directory e gerenciamento de identidade do Office 365

Se você tiver uma assinatura paga do Office 365, também terá uma assinatura gratuita do Azure AD. Você pode usar o Azure AD para criar e gerenciar contas de usuário e de grupo. Para ativar esta assinatura, você deve concluir um registro de uma única vez. Depois disso, você pode acessar o Azure AD do seu portal de administração do Office 365. Para obter instruções, consulte [registrar sua assinatura gratuita do Azure ad](https://go.microsoft.com/fwlink/p/?LinkId=617127). 
  
> [!TIP]
> Siga as instruções acima para registrar a assinatura gratuita do Azure AD que vem com sua assinatura do Office 365. Não vá diretamente para o azure.microsoft.com para se inscrever ou você terminará com uma assinatura de avaliação ou paga para o Microsoft Azure que seja separada do seu gratuito para o Office 365. 
  
Com a assinatura gratuita, você pode sincronizar com os diretórios locais, configurar o logon único e sincronizar com vários softwares como aplicativos de serviço, como Salesforce, DropBox e muito mais.
  
Se quiser uma funcionalidade avançada do AD DS, uma sincronização bidirecional e outros recursos de gerenciamento, você poderá atualizar sua assinatura gratuita para uma assinatura premium paga. Para obter detalhes, consulte [Azure Active Directory Editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).
  
Para obter mais informações sobre o Office 365 e o Azure AD, consulte underStanding [office 365 Identity e Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>Estenda os recursos do seu locatário do Office 365

|**Recurso**|**Descrição**|
|:-----|:-----|
|Aplicativos integrados  <br/> |Você pode conceder acesso a aplicativos individuais para seus dados do Office 365, como emails, calendários, contatos, usuários, grupos, arquivos e pastas. Você também pode autorizar esses aplicativos no nível de administração global e disponibilizá-los para toda a empresa registrando os aplicativos no Azure AD. Para obter detalhes [, consulte aplicativos integrados e o Azure ad para administradores do Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).<br/> Consulte também [Galeria de aplicativos do Azure AD e logon único](https://go.microsoft.com/fwlink/p/?LinkId=698604).  <br/> |
|PowerApps  <br/> | Os aplicativos de energia são aplicativos focados para dispositivos móveis que podem se conectar às fontes de dados existentes, como listas do SharePoint e outros aplicativos de dados. Consulte [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps Page](https://powerapps.microsoft.com/) para obter detalhes.<br/> |
   
Para outros recursos sobre a nuvem da Microsoft e o Office 365, consulte estes recursos:
  
- [Identidade do Microsoft Cloud para arquitetos corporativos](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [Implantar a DirSync (sincronização de diretórios) do Office 365 no Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

Saiba mais em [aplicativos integrados e Azure ad para administradores do Office 365](integrated-apps-and-azure-ads.md) e [Galeria de aplicativos do Azure AD e logon único](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

### <a name="power-apps"></a>Aplicativos de energia
Os aplicativos de energia são aplicativos focados para dispositivos móveis que podem se conectar às fontes de dados existentes, como listas do SharePoint e outros aplicativos de dados. Consulte [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps Page](https://powerapps.microsoft.com/) para obter detalhes.