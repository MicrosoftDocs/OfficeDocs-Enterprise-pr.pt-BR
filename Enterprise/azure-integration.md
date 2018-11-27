---
title: Integração do Azure com o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Sua assinatura do Office 365 inclui uma assinatura do Windows Azure AD. Integre o Office 365 com o Azure AD, se desejar sincronização de senha ou serviço single sign-on com seu ambiente local.
ms.openlocfilehash: 8b7af5ba8d5106900384369a3e6548af40f9e201
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674415"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="50afb-104">Integração do Azure com o Office 365</span><span class="sxs-lookup"><span data-stu-id="50afb-104">Azure integration with Office 365</span></span>

<span data-ttu-id="50afb-p102">O Office 365 usa o Azure Active Directory (AD Azure) para gerenciar identidades de usuário nos bastidores. Sua assinatura do Office 365 inclui uma assinatura gratuita do Azure AD para que você pode integrar o Office 365 com o Azure AD se você deseja sincronizar as senhas ou configurar o single sign-on com seu ambiente local. Você também pode comprar recursos avançados para gerenciar melhor suas contas.</span><span class="sxs-lookup"><span data-stu-id="50afb-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="50afb-108">Azure também oferece outras funcionalidades, como gerenciar aplicativos integrados, que você pode usar para ampliar e personalizar suas assinaturas do Office 365.</span><span class="sxs-lookup"><span data-stu-id="50afb-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="50afb-109">Você pode usar os consultores de implantação do Windows Azure AD para uma experiência interativa de instalação e configuração:</span><span class="sxs-lookup"><span data-stu-id="50afb-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="50afb-110">Supervisor do Azure AD conectar</span><span class="sxs-lookup"><span data-stu-id="50afb-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="50afb-111">Supervisor de implantação do AD FS</span><span class="sxs-lookup"><span data-stu-id="50afb-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="50afb-112">Assistente de implantação do RMS do Azure</span><span class="sxs-lookup"><span data-stu-id="50afb-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="50afb-113">Guia de instalação do Windows Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="50afb-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="50afb-114">Edições do Azure AD e o gerenciamento de identidades do Office 365</span><span class="sxs-lookup"><span data-stu-id="50afb-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="50afb-p103">Se você tiver uma assinatura paga para o Office 365, você também tem uma assinatura gratuita do Azure AD. Você pode usar o Windows Azure AD para criar e gerenciar contas de usuário e grupo. Para ativar esta inscrição, que você deve concluir um registro de uma única vez. Depois disso, você pode acessar o Azure AD de seu portal de administração do Office 365. Para obter instruções, consulte [registrar seu livre assinatura do Windows Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span><span class="sxs-lookup"><span data-stu-id="50afb-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="50afb-p104">Siga as instruções acima para registrar o Azure AD livre assinatura que acompanha a sua assinatura para o Office 365. Não vá diretamente para azure.microsoft.com inscrever ou acabará com uma assinatura paga ou de avaliação para Microsoft Azure separado daquele que sua gratuito para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="50afb-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="50afb-122">Com a assinatura gratuita que você pode sincronizar com diretórios no local, defina o single sign-on e sincronizar com o software de muitos como aplicativos de serviço, a equipe de vendas, a pasta de recados e muitos outros.</span><span class="sxs-lookup"><span data-stu-id="50afb-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="50afb-p105">Se você deseja a funcionalidade avançada do AD DS, sincronização bidirecional e outros recursos de gerenciamento, você pode atualizar sua assinatura gratuita em uma assinatura paga premium. Para obter detalhes, consulte [edições do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="50afb-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="50afb-125">Para obter mais informações sobre o Office 365 e o Azure AD, consulte [Understanding Office 365 Identity e o Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span><span class="sxs-lookup"><span data-stu-id="50afb-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="50afb-126">Estender os recursos de locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="50afb-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="50afb-127">**Recurso**</span><span class="sxs-lookup"><span data-stu-id="50afb-127">**Feature**</span></span>|<span data-ttu-id="50afb-128">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="50afb-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="50afb-129">Aplicativos integrados</span><span class="sxs-lookup"><span data-stu-id="50afb-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="50afb-p106">Você pode conceder acesso a aplicativos individuais aos seus dados do Office 365, como emails, calendários, contatos, usuários, grupos, arquivos e pastas. Você também pode autorizar esses aplicativos no nível de administrador global e disponibilizá-los para toda a sua empresa pelo registro de aplicativos no Windows Azure AD. Para obter detalhes, consulte [Apps integrada e o Azure AD para administradores do Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span><span class="sxs-lookup"><span data-stu-id="50afb-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="50afb-133">Consulte também [Galeria de aplicativo do Windows Azure AD e single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="50afb-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="50afb-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="50afb-134">PowerApps</span></span>  <br/> | <span data-ttu-id="50afb-p107">Aplicativos de energia são focados aplicativos para dispositivos móveis que podem se conectar aos dados existentes fontes, como listas do SharePoint e outros aplicativos de dados. Para obter detalhes, consulte [criar um PowerApp para obter uma lista no SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) e [PowerApps página](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="50afb-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="50afb-137">Para outros recursos sobre o Microsoft Cloud e o Office 365, consulte estes recursos:</span><span class="sxs-lookup"><span data-stu-id="50afb-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="50afb-138">Identidade do Microsoft Cloud para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="50afb-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="50afb-139">Implantar a DirSync (sincronização de diretórios) do Office 365 no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="50afb-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="50afb-140">Saiba mais em [aplicativos integrada e o Azure AD para administradores do Office 365](integrated-apps-and-azure-ads.md) e [Galeria de aplicativo do Windows Azure AD e single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span><span class="sxs-lookup"><span data-stu-id="50afb-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="50afb-141">Aplicativos de energia</span><span class="sxs-lookup"><span data-stu-id="50afb-141">Power Apps</span></span>
<span data-ttu-id="50afb-p108">Aplicativos de energia são focados aplicativos para dispositivos móveis que podem se conectar aos dados existentes fontes, como listas do SharePoint e outros aplicativos de dados. Para obter detalhes, consulte [criar um PowerApp para obter uma lista no SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) e [PowerApps página](https://powerapps.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="50afb-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>