---
title: Suporte ao aplicativo cliente do Office 365-autenticação moderna
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
search.appverid:
- MET150
description: Suporte do aplicativo cliente do Office 365 para autenticação moderna.
ms.openlocfilehash: 8118ab6c9a7f62f01cede259b5b38c3242106102
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085350"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Suporte ao aplicativo cliente do Office 365-autenticação moderna

O recurso de autenticação moderna da Microsoft habilita o logon baseado na biblioteca de autenticação do Active Directory (ADAL) para aplicativos clientes do Office em diferentes plataformas. Isso permite que os recursos de entrada, como a autenticação multiFator (MFA), cartões inteligentes e autenticação baseada em certificado.

Saiba mais sobre [autenticação](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) multifator e [autenticação baseada em certificado](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Plataformas com suporte

 - Área de trabalho do Windows 10
 - Aplicativos modernos do Windows 10
 - Navegador
 - Android
 - Emiti
 - macOS

Para obter mais informações sobre suporte a plataformas no Office 365, consulte [System Requirements for Office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clientes com suporte

As versões mais recentes dos seguintes clientes suportam a autenticação moderna:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Ícone do Azure](media/o365-azure-64x64.png) <br> [Portal do <br> Azure AD](https://azure.microsoft.com/features/azure-portal/) | ![Ícone do portal da empresa](media/o365-microsoft-64x64.png) <br> [Portal <br> da empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Ícone do Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Ícone do Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Ícone do Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![Ícone de fluxo](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Ícone de formulários](media/o365-forms-64x64.png) <br> [Formulários](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Ícone de Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Ícone de administração do Office 365](media/o365-o365admin-64x64.png) <br> [Administração do <br> Office 365](https://products.office.com/business/manage-office-365-admin-app) | ![Ícone de lente](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![Ícone do OneDrive for Business](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Ícone do OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Ícone do Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Ícone do Planner](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Ícone do PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![Ícone do PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Ícone de projeto](media/o365-project-64x64.png) <br> [Projecto](https://products.office.com/project) | ![Ícone do SharePoint](media/o365-sharepoint-64x64.png) <br> [Do](https://products.office.com/sharepoint) | ![Ícone do Skype for Business](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> Business](https://www.skype.com/business/) | ![Ícone de StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Ícone de notas auto-adesivas](media/o365-stickynotes-64x64.png) <br> [Sticky Notes](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Ícone de fluxo](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Ícone de Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Ícone do teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Ícone de tarefas pendentes](media/o365-todo-64x64.png) <br> [Tarefa pendente](https://todo.microsoft.com)
| ![Ícone do Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Ícone do Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Ícone do Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Ícone do Yammer](media/o365-yammer-64x64.png) <br> [Notificador do Yammer <br>](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Módulos do PowerShell suportados

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Ícone do Azure](media/o365-azure-64x64.png) <br> [PowerShell do <br> Azure AD](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Ícone do Exchange](media/o365-exchange-64x64.png) <br> [PowerShell do <br> Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Ícone do SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell do <br> SharePoint Online](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)