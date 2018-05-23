---
title: RGPD para Project Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Saiba mais sobre como atender aos requisitos de RGPD no Project Server local.
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a><span data-ttu-id="8338c-103">RGPD para Project Server</span><span class="sxs-lookup"><span data-stu-id="8338c-103">Plan for Project Server</span></span>

<span data-ttu-id="8338c-p101">O Project Server usa scripts personalizados para exportar e ocultar dados do usuário no Project Web App. O processo básico é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8338c-p101">Project Server uses custom scripts to export and redact user data in Project Web App. The basic process is:</span></span>

1.  <span data-ttu-id="8338c-106">Encontre os sites do Project Web App em seu farm.</span><span class="sxs-lookup"><span data-stu-id="8338c-106">Find the Project Web App sites in your farm.</span></span>

2.  <span data-ttu-id="8338c-107">Encontre os projetos que contêm o usuário em cada site.</span><span class="sxs-lookup"><span data-stu-id="8338c-107">Find the projects in each site that contain the user.</span></span>

3.  <span data-ttu-id="8338c-108">Exporte e verifique os tipos de dados que você deseja analisar.</span><span class="sxs-lookup"><span data-stu-id="8338c-108">Export and review the types of data that you want to review.</span></span>

4.  <span data-ttu-id="8338c-109">Oculte os dados conforme for necessário.</span><span class="sxs-lookup"><span data-stu-id="8338c-109">Redact data as needed.</span></span>

<span data-ttu-id="8338c-110">Estas etapas são abordadas em detalhes nos seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="8338c-110">These three scenarios are covered in detail in the following articles:</span></span>

- [<span data-ttu-id="8338c-111">Exportar dados do usuário do Project Server</span><span class="sxs-lookup"><span data-stu-id="8338c-111">Export user data from Project Server</span></span>](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [<span data-ttu-id="8338c-112">Excluir dados do usuário do Project Server</span><span class="sxs-lookup"><span data-stu-id="8338c-112">Delete user data from Project Server</span></span>](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


<span data-ttu-id="8338c-113">Observe que o Project Server foi criado a partir do SharePoint Server e que ele registra eventos nos logs de ULS do SharePoint e no banco de dados de uso.</span><span class="sxs-lookup"><span data-stu-id="8338c-113">Note that Project Server is built on top of SharePoint Server and logs events to the SharePoint ULS logs and Usage database.</span></span>
