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
# <a name="gdpr-for-project-server"></a>RGPD para Project Server

O Project Server usa scripts personalizados para exportar e ocultar dados do usuário no Project Web App. O processo básico é o seguinte:

1.  Encontre os sites do Project Web App em seu farm.

2.  Encontre os projetos que contêm o usuário em cada site.

3.  Exporte e verifique os tipos de dados que você deseja analisar.

4.  Oculte os dados conforme for necessário.

Estas etapas são abordadas em detalhes nos seguintes artigos:

- [Exportar dados do usuário do Project Server](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [Excluir dados do usuário do Project Server](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


Observe que o Project Server foi criado a partir do SharePoint Server e que ele registra eventos nos logs de ULS do SharePoint e no banco de dados de uso.
