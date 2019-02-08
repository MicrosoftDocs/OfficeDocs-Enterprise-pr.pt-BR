---
title: Suporte de aplicativo de cliente do Office 365 - autenticação moderno
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Suporte de aplicativo cliente do Office 365 para autenticação moderna.
ms.openlocfilehash: 18ef5b2219c9527594ae8fcff7e29052671d1431
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "29771120"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Suporte de aplicativo de cliente do Office 365 - autenticação moderno

O recurso de autenticação moderno da Microsoft permite baseada no Active Directory autenticação biblioteca ADAL entrar para aplicativos de cliente do Office em plataformas diferentes. Isso permite que os recursos de entrar, como a autenticação multifator (MFA), o cartão inteligente e a autenticação baseada em certificado.

Saiba mais sobre [a autenticação multifator](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) e [autenticação baseada em certificado](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Plataformas com suporte

 - Área de trabalho do Windows 10
 - Aplicativos moderno do Windows 10
 - Navegador
 - Android
 - iOS
 - macOS

## <a name="supported-clients"></a>Clientes com suporte

As versões mais recentes dos seguintes clientes suportam moderna autenticação:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Ícone do Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> Portal](https://azure.microsoft.com/features/azure-portal/) | ![Ícone de portal da empresa](media/o365-microsoft-64x64.png) <br> [Empresa <br> Portal](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Me aprofundar ícone](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Ícone de Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Ícone do Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![Ícone de fluxo](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Ícone de formulários](media/o365-forms-64x64.png) <br> [Formulários](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Ícone de Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Ícone de administração do Office 365](media/o365-o365admin-64x64.png) <br> [O Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![Ícone de Lente](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![OneDrive para o ícone de negócios](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Ícone do OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Ícone do Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Ícone de Planejador](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Ícone de PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![Ícone do PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Ícone de projeto](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Ícone do SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Skype para o ícone de negócios](media/o365-skypeforbusiness-64x64.png) <br> [Skype para <br> corporativos](https://www.skype.com/business/) | ![Ícone de StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Ícone de Notas Autoadesivas](media/o365-stickynotes-64x64.png) <br> [Sticky Notes](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Ícone de fluxo](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Ícone de sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Ícone de equipes](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Ícone de tarefas pendentes](media/o365-todo-64x64.png) <br> [Tarefa pendente](https://todo.microsoft.com)
| ![Ícone do Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Ícone do Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Ícone do Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Ícone do Yammer](media/o365-yammer-64x64.png) <br> [Yammer <br> notificação](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Módulos com suporte do PowerShell

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Ícone do Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Ícone do Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Ícone do SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)