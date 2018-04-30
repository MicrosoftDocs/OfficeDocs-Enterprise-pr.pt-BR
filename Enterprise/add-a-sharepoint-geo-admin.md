---
title: Adicionar ou remover um administrador geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba como adicionar ou remover um administrador geo no OneDrive para Business Multi-Geo.
ms.openlocfilehash: 7630597654df9ad78619b94fedc9e18d5b0b721e
ms.sourcegitcommit: 886b23f590f6187f7a98c1083a3b49359ec2a5c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Adicionar ou remover um administrador geo no OneDrive para Busniess Multi-Geo

Você pode configurar administradores separados para cada localidade geo que você tem no seu locatário. Esses administradores terão acesso às configurações de SharePoint Online e OneDrive que são específicos para sua localização geográfica.

Alguns serviços - como o repositório de termos - são administrados do local central e replicados para locais de satélite. O administrador geo para o local central tem acesso a esses, enquanto não geo admins para locais de satélite.

Os administradores globais e do SharePoint Online continuar têm acesso a configurações em todos os locais de geo.

## <a name="configuring-geo-administrators"></a>Configurando geo administradores

Configurar geo admins requer o módulo de PowerShell do SharePoint Online.

Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectar o Centro de administração do geo local onde deseja adicionar o administrador do geo. (Por exemplo, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Para exibir os administradores geo existente de um local, execute`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Adicionando um usuário como um administrador geo

Para adicionar um usuário como um administrador geo, execute:`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Para remover um usuário como um administrador Geo de um local, execute`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Adicionar um grupo como um administrador geo

Você pode adicionar um grupo de segurança ou de um grupo de segurança habilitados para email como um administrador de geo. (Grupos de distribuição e grupos do Office 365 não são suportados.)

Para adicionar um grupo como um administrador geo, execute:`Add-SPOGeoAdministrator -GroupAlias <alias>`

Para remover um grupo como um administrador geo, execute`Remove-SPOGeoAdministrator -GroupAlias <alias>`

Observe que nem todos os grupos de segurança tem um alias de grupo. Se você deseja adicionar um grupo de segurança que não tem um alias, execute [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) para recuperar uma lista de grupos, encontre ObjectID do grupo de segurança e, em seguida, execute:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Para remover um grupo usando o ObjectID, execute`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>Confira também

[Adicionar-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Definir um alias (MailNickName) para um grupo de segurança](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)