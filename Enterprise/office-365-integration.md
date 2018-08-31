---
title: Integração com o Office 365 com ambientes locais
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Saiba como integrar o Office 365 com seus serviços de diretório existentes.
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539298"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Integração com o Office 365 com ambientes locais

É possível integrar o Office 365 com seus serviços de diretório existentes e com uma instalação local do Exchange Server e do Skype para Business Server 2015 ou SharePoint Server 2013.
  
 - Ao integrar com serviços de diretório, você pode sincronizar e gerenciar contas de usuário para ambos os ambientes. Você também pode adicionar sincronização de hash de senha ou logon único (SSO) para que os usuários podem fazer logon em ambos os ambientes com suas credenciais locais.
 - Ao integrar com os produtos de servidor local, você pode criar um ambiente híbrido. Um ambiente híbrido pode ajudar conforme você migrar usuários ou informações para o Office 365 ou você pode continuar a ter alguns usuários ou algumas informações no local e alguns na nuvem. Para obter mais informações sobre ambientes híbridos, consulte [Visão geral de soluções de nuvem híbrida do Office 365](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).

Você também pode usar os consultores do Azure AD para obter orientações de instalação personalizada:
- [Supervisor do Azure AD conectar](https://aka.ms/aadconnectpwsync)
- [Supervisor de implantação do AD FS](https://aka.ms/adfsguidance)
- [Assistente de implantação do RMS do Azure](https://aka.ms/azuremsguidance)
- [Orientações de instalação do Windows Azure AD Premium](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Antes de começar
Antes de integrar o Office 365 e um ambiente local, você também precisa participar de [planejamento de rede](network-planning-and-performance.md)e ajuste de desempenho para o Office 365. Convém também compreender os [modelos de identidade](about-office-365-identity.md) de disponíveis no Office 365. 

Consulte [onde para gerenciar o usuário do Office 365 contas](manage-office-365-accounts.md) para obter uma lista das ferramentas que você pode usar para gerenciar contas e usuários do Office 365. 
  
## <a name="integrate-office-365-with-directory-services"></a>Integrar o Office 365 com serviços de diretório
Se você tiver contas de usuário existentes em um diretório local, você não deseja recriar todas as contas no Office 365 e introduzir diferenças ou erros entre os ambientes de risco. Sincronização de diretórios ajuda você a espelhar essas contas entre seu online e ambientes locais. Com a sincronização de diretório, os usuários não precisarão se lembrar novas informações para cada ambiente e você não precisa criar ou atualizar contas duas vezes. Você precisará [preparar seu diretório local](prepare-for-directory-synchronization.md) para sincronização de diretórios, você pode fazer isso manualmente ou usar a [ferramenta IdFix](install-and-run-idfix.md) (IdFix ferramenta funciona apenas com o Active Directory). 
  
![Usar sincronização de diretórios para manter sincronizados informações da conta de usuário on-line e no local](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Se desejar que os usuários possam fazer logon para o Office 365 com suas credenciais de local, você também pode configurar SSO. Com o SSO, o Office 365 é configurado para confiar o ambiente local para autenticação do usuário.
  
![Com o logon único, a mesma conta está disponível nos ambientes online e local](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
As técnicas de gerenciamento de conta de usuário diferente fornecem experiências diferentes para seus usuários, conforme mostrado na tabela a seguir.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**Sincronização de diretórios com ou sem autenticação de passagem ou de sincronização de hash de senha**
Um usuário fizer logon com seu ambiente local com sua conta de usuário (domínio \ nome_de_usuário). Quando forem para o Office 365, eles devem efetuar logon novamente com sua conta de trabalho ou da escola (user@domain.com). O nome de usuário é o mesmo em ambos os ambientes. Quando você adiciona a sincronização de hash de senha ou a autenticação de passagem, o usuário tem a mesma senha para ambos os ambientes, mas será necessário fornecer essas credenciais novamente ao fazer logon no Office 365. Sincronização de diretórios com sincronização de hash de senha é o cenário de sincronização de diretório mais comumente usadas.

Para configurar a sincronização de diretórios, use o Azure Active Directory Connect. Para obter instruções, leia a [Configurar a sincronização de diretórios para o Office 365](set-up-directory-synchronization.md)e [conectar com configurações express a uso Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Saiba mais sobre como [Preparar provisionar usuários por meio da sincronização de diretório para o Office 365](prepare-for-directory-synchronization.md) e [integrar o seu local identifica com o Windows Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>**Sincronização de diretórios com o SSO**
Um usuário fizer logon com seu ambiente local com sua conta de usuário. Quando forem para o Office 365, que seja tenham feito logon automaticamente ou que fizerem logon usando as mesmas credenciais que eles usam para seu ambiente local (domínio \ nome_de_usuário).

Para configurar o SSO, você também usar Connect do Azure AD. Para obter instruções, leia [Connect do uso Azure AD com configurações personalizadas](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Saiba mais sobre o [acesso aos aplicativos e logon único com o Windows Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect
Conectar do Azure AD substitui versões mais antigas do que as ferramentas de integração de identidade, como DirSync e sincronização do Azure AD. Para obter mais informações, consulte [integrando suas identidades no local com o Windows Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). Se você deseja atualizar de sincronização do Azure Active Directory para conectar do Azure AD, consulte [as instruções de atualização](https://go.microsoft.com/fwlink/p/?LinkId=733240). Consulte uma arquitetura de solução construída Office 365 para [Sincronização](https://go.microsoft.com/fwlink/?LinkId=517887)de diretórios (DirSync) no Microsoft Azure.