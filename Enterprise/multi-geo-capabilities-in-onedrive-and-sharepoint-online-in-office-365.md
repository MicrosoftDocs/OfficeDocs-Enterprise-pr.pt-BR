---
title: Funcionalidades multigeográficas no OneDrive e no SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda a sua presença no Office 365 para várias regiões geográficas com funcionalidades multigeográficas do OneDrive Online.
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948582"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Funcionalidades multigeográficas no OneDrive e no SharePoint Online

As funcionalidades multigeográfica do OneDrive e do SharePoint Online permite controlar o país ou região onde recursos compartilhados, como sites de equipe do SharePoint e caixas de correio do Grupo do Office 365 são armazenados em repouso.

Cada usuário, caixa de correio do Grupo e site do SharePoint possui uma Localização Preferencial do Dados (PDL) que indica a localização geográfica onde os dados relacionados devem ser armazenados. Dados pessoais do usuário (caixa de correio do Exchange e OneDrive) juntamente com Grupos do Office 365 ou sites do SharePoint criados por eles podem ser armazenados em uma localização geográfica especificada para atender aos requisitos de residência dos dados. Você pode [especificar administradores diferentes para cada localização geográfica](add-a-sharepoint-geo-admin.md).

Os usuários têm uma experiência perfeita ao usar os serviços do Office 365, incluindo os aplicativos do Office, OneDrive e Search. Para obter mais detalhes, confira [Experiência do usuário em um ambiente multigeográfico](multi-geo-user-experience.md).

## <a name="onedrive"></a>OneDrive

Cada usuário do OneDrive pode ser provisionado ou [movido por um administrador](move-onedrive-between-geo-locations.md) em um localização por satélite de acordo com PDL do usuário. Os arquivos pessoais são mantidos nessa localização geográfica, embora eles possam ser compartilhados com usuários em outras localizações geográficas.

## <a name="sites-and-groups"></a>Sites e Grupos

Quando um usuário cria um site conectado a um grupo do SharePoint, o PDL é usado para determinar a localização geográfica onde o site e sua caixa de correio de Grupo associada do grupo foram criados. (Se o valor PDL do usuário ainda não foi definida ou foi definida em uma localização geográfica que ainda não foi configurada como uma localização por satélite, os sites e as caixas de correio são criados em uma localização central.)

Os serviços do Office 365 diferentes do Exchange, OneDrive, e SharePoint não são multigeográficos. No entanto, os grupos do Office 365 que são criados por esses serviços serão marcados com a PDL do criador e sua caixa de correio do Grupo do Exchange e o Site do Grupo do SharePoint O365 provisionados na localização geográfica correspondente. 

## <a name="managing-the-multi-geo-environment"></a>Gerenciar o ambiente multigeográfico

A configuração e o gerenciamento do ambiente multigeográfico são feitos pelo centro de administração do SharePoint. 

![Captura de tela da página de localizações geográficas do centro de administração SharePoint](media/sharepoint-multi-geo-admin-center.png)

(Algumas ações, como mover um site do SharePoint ou um site do OneDrive necessitam do Microsoft PowerShell.)

## <a name="see-also"></a>Confira também

[Aka.ms/GetMultiGeo ](https://Aka.ms/GetMultiGeo)

[Administrar um ambiente multigeográfico](administering-a-multi-geo-environment.md)

[Cotas de armazenamento do SharePoint em ambientes multigeográficos](sharepoint-multi-geo-storage-quota.md)

[Administrar caixas de correio do Exchange Online em um ambiente multigeográfico](administering-exchange-online-multi-geo.md)
