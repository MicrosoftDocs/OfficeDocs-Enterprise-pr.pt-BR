---
title: Modelos de identidade do Office 365 e o Active Directory do Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 05/20/2019
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Saiba como a identidade do usuário é gerenciada no Office 365.
ms.openlocfilehash: a44f3073895ef1c8172a6ab5637f50cd9c6ac186
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843802"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a>Modelos de identidade do Office 365 e o Active Directory do Azure

*Esse artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*

O Office 365 usa o Azure Active Directory (Azure AD), um serviço de autenticação e identidade do usuário baseado na nuvem que está incluído em sua assinatura do Office 365, para gerenciar identidades e autenticação para o Office 365. Obter sua infraestrutura de identidade configurada corretamente é vital para gerenciar o acesso de usuário do Office 365 e permissões para sua organização.

Antes de começar, Assista a este vídeo para obter uma visão geral dos modelos de identidade e autenticação para o Office 365 e para o Microsoft 365.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

Sua primeira opção de planejamento é o modelo de identidade do Office 365.

## <a name="office-365-identity-models"></a>Modelos de identidade do Office 365

Para planejar contas de usuário, primeiro você precisa entender os dois modelos de identidade no Microsoft 365. Você pode manter as identidades da sua organização apenas na nuvem ou pode manter suas identidades do AD DS (serviços de domínio Active Directory) locais e usá-las para autenticação quando os usuários acessarem os serviços de nuvem do Microsoft 365.  

Estes são os dois tipos de identidade e seus benefícios e melhores necessidades.

|||
|:-------|:-----|:-----|
|  | **Identidade somente na nuvem** | **Identidade híbrida** |
| **Definição** | A conta de usuário existe somente no locatário do Azure Active Directory (Azure AD) para sua assinatura do Microsoft 365. | A conta de usuário existe no AD DS e uma cópia também está no locatário do Azure AD para sua assinatura do Microsoft 365. A conta de usuário no Azure AD também pode incluir uma versão de hash da senha da conta de usuário. |
| **Como o Microsoft 365 autentica as credenciais do usuário** | O locatário do Azure AD para sua assinatura do Microsoft 365 realiza a autenticação com a conta de identidade de nuvem. | O locatário do Azure AD para sua assinatura do Microsoft 365 manipula o processo de autenticação ou redireciona o usuário para outro provedor de identidade. |
| **Melhor para** | Organizações que não têm ou precisam de um AD DS local. | Organizações que usam o AD DS ou outro provedor de identidade. |
| **Melhor benefício** | Simples de usar. Não é necessária nenhuma ferramenta ou servidor de diretório extra. | Os usuários podem usar as mesmas credenciais ao acessar recursos locais ou baseados em nuvem. |
||||

## <a name="cloud-only-identity"></a>Identidade somente na nuvem

Uma identidade somente na nuvem usa contas de usuário que existem somente no Azure AD. A identidade em nuvem é normalmente usada por pequenas organizações que não têm servidores locais ou não usam o AD DS para gerenciar identidades locais. 

Estes são os componentes básicos da identidade somente na nuvem.
 
![Componentes básicos da identidade somente na nuvem](./media/about-office-365-identity/cloud-only-identity.png)

Os usuários locais e remotos (online) usam suas contas de usuário e senhas do Azure AD para acessar os serviços de nuvem do Office 365. O Azure AD autentica as credenciais do usuário com base em suas contas de usuário e senhas armazenadas.

### <a name="administration"></a>Administração
Como as contas de usuário são armazenadas apenas no Azure AD, você gerencia identidades de nuvem com ferramentas como o [centro de administração do Microsoft 365](https://admin.microsoft.com) e o Windows PowerShell com o módulo PowerShell do Azure Active Directory para Graph. 

## <a name="hybrid-identity"></a>Identidade híbrida

A identidade híbrida usa contas originadas em um AD DS local e ter uma cópia no locatário do Azure AD de uma assinatura do Microsoft 365. No entanto, a maioria das alterações só flui de uma forma. As alterações feitas nas contas de usuário do AD DS são sincronizadas com sua cópia no Azure AD. Mas as alterações feitas nas contas baseadas em nuvem no Azure AD, como novas contas de usuário, não são sincronizadas com o AD DS.

O Azure AD Connect fornece a sincronização de contas contínuas. Ele é executado em um servidor local, verifica as alterações no AD DS e encaminha essas alterações para o Azure AD. O Azure AD Connect oferece a capacidade de filtrar quais contas estão sincronizadas e se deve sincronizar uma versão de hash de senhas de usuário, conhecida como sincronização de hash de senha (PHS).

Ao implementar a identidade híbrida, seu AD DS local é a fonte autoritativa de informações da conta. Isso significa que você realiza tarefas de administração principalmente no local, que são então sincronizadas com o Azure AD. 

Estes são os componentes da identidade híbrida.

![Componentes da identidade híbrida](./media/about-office-365-identity/hybrid-identity.png)

O locatário do Azure AD tem uma cópia das contas do AD DS. Nessa configuração, os usuários locais e remotos que acessam o Microsoft 365 Cloud Services são autenticados no Azure AD.

>[!Note]
>Você sempre precisa usar o Azure AD Connect para sincronizar contas de usuário para identidade híbrida. Você precisa das contas de usuário sincronizadas no Azure AD para realizar a atribuição de licença e o gerenciamento de grupo, configurar permissões e outras tarefas administrativas que envolvem contas de usuário.
>

### <a name="administration"></a>Administração

Como as contas de usuário originais e autoritativas são armazenadas no AD DS local, você gerencia suas identidades com as mesmas ferramentas que o AD DS, como a ferramenta usuários e computadores do Active Directory. 

Você não usa o centro de administração do Microsoft 365 ou o Windows PowerShell para gerenciar contas de usuário sincronizadas no Azure AD.

## <a name="next-step"></a>Próxima etapa

Se você precisar do modelo de identidade somente na nuvem, confira [identidades somente na nuvem](cloud-only-identities.md).

Se você precisar do modelo de identidade híbrida, consulte [sincronização de diretório](plan-for-directory-synchronization.md).
  

## <a name="video-training"></a>Treinamentos em vídeo

Consulte o curso de vídeo [Office 365: gerenciar identidades usando o Azure ad Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), trazido para você pelo LinkedIn Learning.

## <a name="see-also"></a>Confira também

[Visão geral do Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
