---
title: Suporte ao aplicativo cliente do Office 365-autenticação baseada em certificado
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: Suporte do aplicativo cliente do Office 365 para autenticação baseada em certificado.
ms.openlocfilehash: 88bc59934399588f0a5c682c6b136ad0948ecd52
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "33990901"
---
# <a name="office-365-client-app-support--certificate-based-authentication"></a>Suporte ao aplicativo cliente do Office 365-autenticação baseada em certificado

A autenticação baseada em certificado permite que você autentique no Azure Active Directory com um certificado de cliente em dispositivos Windows, Android ou iOS. A configuração desse recurso elimina a necessidade de inserir uma combinação de nome de usuário e senha em determinados emails e aplicativos do Microsoft Office em seu dispositivo móvel.

Saiba mais sobre [a autenticação baseada em certificado](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Plataformas com suporte

 - Windows 10 desktop<sup>2</sup>
 - Aplicativos modernos do Windows 10
 - Navegadores da Web
 - Android
 - iOS
 - macOS<sup>1</sup> <sup>2</sup>

Para obter mais informações sobre suporte a plataformas no Office 365, consulte [System Requirements for Office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Clientes com suporte

As versões mais recentes dos seguintes clientes dão suporte à autenticação baseada em certificado:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Ícone do Access](media/o365-access-64x64.png) <br> [Acesso](https://products.office.com/access) | ![Ícone do Azure](media/o365-azure-64x64.png) <br> [Portal do <br> Azure AD](https://azure.microsoft.com/features/azure-portal/) | ![Ícone do portal da empresa](media/o365-microsoft-64x64.png) <br> [Portal <br> da empresa](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Ícone do Delve](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Ícone do Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Ícone de borda](media/o365-edge-64x64.png) <br> [Vertical](https://www.microsoft.com/windows/microsoft-edge) | ![Ícone do Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Ícone de fluxo](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Ícone de formulários](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Ícone de Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Ícone de administração do Office 365](media/o365-o365admin-64x64.png) <br> [Administração do <br> Office 365](https://products.office.com/business/manage-office-365-admin-app) | ![Ícone de lente](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Ícone do OneDrive for Business](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Ícone do OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Ícone do Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Ícone do Planner](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Ícone do PowerApps](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![Ícone do PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![Ícone do PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Ícone de projeto](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) 
| ![Ícone do Publisher](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Ícone do SharePoint](media/o365-sharepoint-64x64.png) <br> [Do](https://products.office.com/sharepoint) | ![Ícone do Skype for Business](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> Business](https://www.skype.com/business/) | ![Ícone de notas auto-adesivas](media/o365-stickynotes-64x64.png) <br> [Notas auto-adesivas](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Ícone de fluxo](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) 
| ![Ícone de Sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Ícone do teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Ícone de tarefas pendentes](media/o365-todo-64x64.png) <br> [Tarefa pendente](https://todo.microsoft.com) | ![Ícone do Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Ícone do Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Ícone do Yammer](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>Módulos do PowerShell suportados

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Ícone do Azure](media/o365-azure-64x64.png) <br> [PowerShell do <br> Azure AD](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Ícone do Exchange](media/o365-exchange-64x64.png) <br> [PowerShell do <br> Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Ícone do SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell do <br> SharePoint Online](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> suporte para onedrive no MacOS disponível em breve. <br>
> <sup>2</sup> o suporte para o Yammer na área de trabalho do Windows e no MacOS estará disponível em breve.