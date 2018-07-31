---
title: Suporte para aplicativos de cliente do Office 365 - acesso condicional
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
ms.collection: Strat_O365_Enterprise
description: Compreender o suporte ao aplicativo de cliente do Office 365 para acesso condicional
ms.openlocfilehash: f9a1b4c022b00569a392d7f50bfcae583847ea3c
ms.sourcegitcommit: 4e654517825b74a3bbe171b915b134ba49231e2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2018
ms.locfileid: "21541961"
---
# <a name="office-365-client-app-support---conditional-access"></a>Suporte para aplicativos de cliente do Office 365 - acesso condicional

Na área de trabalho moderna, os usuários podem acessar os recursos da sua organização usando uma variedade de dispositivos e aplicativos de praticamente qualquer lugar. Como resultado, concentrando-se apenas em quem pode acessar um recurso não for suficiente mais. Sua organização também deve suportar como e onde um recurso está sendo acessado em sua infra-estrutura de controle de acesso. Com o dispositivo, local e acesso de condicional baseado em autenticação multifator Azure AD, você pode atender a esse requisito novo. Acesso condicional é um recurso do Azure Active Directory que permite que você aplique controles em que o acesso aos aplicativos em seu ambiente, tudo com base nas condições específicas e gerenciado de um local central. 

Saiba mais sobre [baseados no dispositivo](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications), [com base no local](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)e acesso condicional [baseado em MFA](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) .

## <a name="supported-platforms"></a>Plataformas com suporte

 - Área de trabalho do Windows 10
 - Aplicativos moderno do Windows 10
 - Navegador
 - Android
 - iOS
 - macOS<sup>1</sup>

## <a name="supported-clients"></a>Clientes com suporte

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Me aprofundar ícone](images/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Ícone do Excel](images/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Ícone de fluxo](images/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Ícone de formulários](images/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Ícone de Kaizala](images/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Ícone de administração do Office 365](images/o365-o365admin-64x64.png) <br> [O Office 365 <br> Admin](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive para o ícone de negócios](images/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Ícone do OneNote](images/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Ícone do Outlook](images/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Ícone de Planejador](images/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![Ícone de PowerBI](images/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Ícone do PowerPoint](images/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Ícone de projeto](images/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Ícone do SharePoint](images/o365-sharepoint-64x64.png) <br> [SharePoint<sup>1</sup>](https://products.office.com/sharepoint) | ![Skype para o ícone de negócios](images/o365-skypeforbusiness-64x64.png) <br> [Skype para <br> corporativos](https://www.skype.com/business/) 
| ![Ícone de StaffHub](images/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![Ícone de fluxo](images/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Ícone de sway](images/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Ícone de equipes](images/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Ícone de tarefas pendentes](images/o365-todo-64x64.png) <br> [Tarefa pendente](https://todo.microsoft.com) 
| ![Ícone do Visio](images/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Ícone do Word](images/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Ícone do Yammer](images/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> Suporte a aplicativo SharePoint <sup>1</sup> em macOS em breve.