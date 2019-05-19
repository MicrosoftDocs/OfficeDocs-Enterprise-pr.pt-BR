---
title: Atribuir licenças do Office 365 a contas de usuário
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
description: Descreve como atribuir licenças do Office 365 a contas de usuário, individualmente ou com base na associação de grupo.
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164596"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>Atribuir licenças do Office 365 a contas de usuário

Para o modelo de identidade somente na nuvem, você pode atribuir licenças do Office 365 a contas de usuário à medida que elas são criadas, dependendo de como você as cria.

Para o modelo de identidade híbrida, quando as contas de usuário dos serviços de domínio Active Directory (AD DS) são sincronizadas pela primeira vez, elas não recebem automaticamente uma licença do Office 365.

Em ambos os casos, você deve atribuir uma licença às contas de usuário para que seus usuários possam acessar os serviços do Office 365, como email e Microsoft Teams.

Você pode atribuir licenças a contas de usuário individualmente ou automaticamente através da Associação de grupo.

Para atribuir licenças do Office 365 a contas de usuário individuais, você pode usar:

- [O centro de administração do Microsoft 365](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

Para atribuição de licença automática, confira [Licenciamento baseado em grupo no Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Próximas etapas

Com o conjunto completo de contas de usuário às quais foram atribuídas licenças, agora você está pronto para:

- [Implantar software cliente, como o Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [Configurar o gerenciamento de dispositivos móveis](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Configurar serviços e aplicativos](configure-services-and-applications.md)
