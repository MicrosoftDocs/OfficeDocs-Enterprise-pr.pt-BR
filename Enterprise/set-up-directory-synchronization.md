---
title: Configurar a sincronização de diretório no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Saiba como configurar a sincronização de diretórios entre o Office 365 e o Active Directory local.
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162474"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurar a sincronização de diretório no Office 365

O Office 365 usa um locatário do Azure Active Directory (Azure AD) para armazenar e gerenciar identidades para autenticação e permissões para acessar recursos baseados em nuvem. 

Se você tiver um Active Directory Domain Services (AD DS) local, poderá sincronizar suas contas de usuário, grupos e contatos do AD DS com o locatário do Azure AD da sua assinatura do Office 365. Esta é uma identidade híbrida do Office 365. Estes são os componentes.

![](./media/about-office-365-identity/hybrid-identity.png)

O Azure AD Connect é executado em um servidor local e sincroniza seu AD DS com o locatário do Azure AD. Juntamente com a sincronização de diretórios, você também pode especificar estas opções de autenticação:

- Sincronização de hash de senha (PHS)

  O Azure AD executa a própria autenticação.

- Autenticação de passagem (PTA)

  O Azure AD tem o AD DS executando a autenticação.

- Autenticação federada

  O Azure AD redireciona o computador cliente solicitando a autenticação para entrar em contato com outro provedor de identidade.

Confira [identidades híbridas](plan-for-directory-synchronization.md) para obter mais informações.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Examine os pré-requisitos para o Azure AD Connect

Você Obtém uma assinatura gratuita do Azure AD com sua assinatura do Office 365. Ao configurar a sincronização de diretórios, você instalará o Azure AD Connect em um dos servidores locais.
  
Para o Office 365, você precisará:
  
- Verifique seu domínio local. O assistente do Azure AD Connect orienta você por isso.
- Obtenha os nomes de usuário e senhas das contas de administrador do seu locatário do Office 365 e do AD DS.

Para o servidor local em que você instala o Azure AD Connect, você precisará de:
  
|**Sistema operacional do servidor**|**Outro software**|
|:-----|:-----|
|Windows Server 2012 R2 e posterior | -O PowerShell é instalado por padrão, nenhuma ação é necessária.  <br> -NET 4.5.1 e versões posteriores são oferecidos por meio do Windows Update. Verifique se você instalou as atualizações mais recentes do Windows Server no painel de controle. |
|Windows Server 2008 R2 com Service Pack 1 (SP1) * * ou Windows Server 2012 | – A versão mais recente do PowerShell está disponível no Windows Management Framework 4,0. Procure por ele no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> – As versões do .NET 4.5.1 e posteriores estão disponíveis no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | – A versão com suporte mais recente do PowerShell está disponível no Windows Management Framework 3,0, disponível no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> – As versões do .NET 4.5.1 e posteriores estão disponíveis no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Consulte [pré-requisitos para o Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) para obter detalhes sobre requisitos de hardware, software, conta e permissões, requisitos de certificado SSL e limites de objeto para o Azure ad Connect.
  
Você também pode analisar o histórico de versões da [versão](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) do Azure ad Connect para ver o que está incluído e corrigido em cada versão.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. instalar o Azure AD Connect e configurar a sincronização de diretórios

Antes de começar, certifique-se de que:

- O nome de usuário e a senha de um administrador global do Office 365
- O nome de usuário e a senha de um administrador de domínio do AD DS
- Qual método de autenticação (PHS, PTA, federado)
- Se você deseja usar o [logon único (SSO) contínuo do Azure ad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

Siga estas etapas:

1. Entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) e escolha usuários **ativos** do **usuário** \> no painel de navegação à esquerda.
2. No centro de administração, na página **usuários ativos** , escolha **mais** \> **sincronização de diretórios**.

    ![No menu mais, escolha sincronização de diretório](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Na página de **preparação do Active Directory** , selecione o link **baixar a ferramenta de conexão do Active Directory do Microsoft Azure** para começar. 
4. Siga as etapas no [mapa de instalação de integridade do Azure ad Connect e do Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. concluir a configuração dos domínios

Siga as etapas em [criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) para concluir a configuração dos seus domínios.

## <a name="next-step"></a>Próxima etapa

[Atribuir licenças a contas de usuário](assign-licenses-to-user-accounts.md).
