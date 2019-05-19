---
title: Identidades somente na nuvem do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Descreve como criar usuários e grupos quando sua assinatura do Office 365 está usando identidades somente na nuvem.
ms.openlocfilehash: 7a2aaf7705378da3cbd91b415f07d10b6e039293
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164606"
---
# <a name="office-365-cloud-only-identities"></a>Identidades somente na nuvem do Office 365

Com a identidade somente na nuvem, todos os usuários, grupos e contatos são armazenados no locatário do Azure Active Directory (Azure AD) da sua assinatura do Office 365. Estes são os componentes básicos da identidade somente na nuvem.
 
![](./media/about-office-365-identity/cloud-only-identity.png)

Os usuários e suas contas de usuário nas organizações podem ser categorizados de várias maneiras. Por exemplo, alguns são funcionários e têm um status permanente. Alguns são fornecedores, contratadores ou parceiros que têm um status temporário. Alguns são usuários externos que não têm contas de usuário, mas ainda precisam ter acesso a serviços e recursos específicos para oferecer suporte à interação e à colaboração. Por exemplo:

- As contas do locatário representam os usuários em sua organização para os quais você atribui uma licença para os serviços de nuvem

- As contas B2B (Business to Business) representam os usuários de fora da sua organização que você convida para participar da colaboração, fazem o estoque dos tipos de usuários para sua organização. Quais são os agrupamentos? Por exemplo, você pode agrupar usuários por função ou finalidade de alto nível em sua organização.

Além disso, alguns serviços de nuvem podem ser compartilhados com usuários de fora de sua organização que não tenham contas de usuário. Você também precisará identificar esses grupos de usuários.

Você pode usar grupos no Azure AD para várias finalidades que simplificam o gerenciamento de seu ambiente de nuvem. Por exemplo, com grupos do Azure AD, você pode:

- Use o licenciamento baseado em grupo para atribuir licenças do Office 365 às contas de usuário automaticamente assim que elas forem adicionadas.
- Adicionar contas de usuário para grupos específicos de forma dinâmica com base em atributos das contas de usuário, como o departamento.
- Provisionar usuários automaticamente para aplicativos de Software como um Serviço (SaaS) e para proteger o acesso a esses aplicativos com a autenticação multifator e outras regras de acesso condicional.
- Provisione permissões e níveis de acesso para sites de equipe do SharePoint Online.

Você pode criar novos ***usuários*** com:

- [O centro de administração do Microsoft 365](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

Você pode criar novos ***grupos*** com:

- [O centro de administração do Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a>Próxima etapa para identidades somente na nuvem

[Atribuir licenças às contas de usuário](assign-licenses-to-user-accounts.md)
