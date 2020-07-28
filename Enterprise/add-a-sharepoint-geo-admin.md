---
title: Adicionar ou remover um administrador geográfico
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords:
- NOCSH
description: Saiba como adicionar ou remover um administrador geográfico no Microsoft 365 Multi-Geo.
ms.openlocfilehash: 13b730de6b318ddb3a4cf3a084d4b59e56a82dbf
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433602"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a>Adicionar ou remover um administrador geográfico no Microsoft 365 Multi-Geo.

Você pode configurar administradores separados para cada localização geográfica que há em seu locatário. Esses administradores terão acesso às configurações do SharePoint Online e do OneDrive específicas para sua localização geográfica.

Alguns serviços, como o repositório de termos, são administrados da localização central e replicados para as localizações via satélite. O administrador geográfico da localização central tem acesso a elas, enquanto que os administradores geográficos via satélite não.

Os administradores globais e administradores do SharePoint Online continuam a ter acesso às configurações da localização local e das localizações via satélite.

## <a name="configuring-geo-administrators"></a>Configurar os administradores geográficos

Configurar os administradores geográficos exige o módulo PowerShell do SharePoint Online.

Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para se conectar ao centro de administração da localização geográfica onde você deseja adicionar o administrador geográfico. (Por exemplo, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)

Para exibir os administradores geográficos existentes de um local, execute `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Adicionar um usuário como um administrador geográfico

Para adicionar um usuário como um administrador geográfico, execute `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Para remover um usuário como um administrador geográfico de um local, execute  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Adicionar um grupo como um administrador geográfico

Você pode adicionar um grupo de segurança ou um grupo de segurança habilitado para e-mails como administrador geográfico. (Grupos de distribuição e grupos do Microsoft 365 não são suportados.)

Para adicionar um grupo como um administrador geográfico, execute `Add-SPOGeoAdministrator -GroupAlias <alias>`

Para remover um grupo como um administrador geográfico, execute `Remove-SPOGeoAdministrator -GroupAlias <alias>`

Observe que nem todos os grupos de segurança têm um alias de grupo. Se você quiser adicionar um grupo de segurança que tenha um alias, execute [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) para recuperar uma lista de grupos, localizar o ObjectID do grupo de segurança e, em seguida, execute:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Para remover um grupo usando o ObjectID, execute `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>Confira Também

[Adicionar-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Obter SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remover SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Configurar um alias (MailNickName) para um grupo de segurança](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)