---
title: Configurar a sincronização de diretório com o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Saiba como configurar a sincronização de diretórios entre o Office 365 e seu local no Active Directory.
ms.openlocfilehash: f2cd29e7a81854bb64f6317aa2b41e674ae22df4
ms.sourcegitcommit: a4546e1f3fe9e8e25a56ed350400d51eb7dd7f83
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "29555437"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurar a sincronização de diretório com o Office 365

O Office 365 usa o serviço de gerenciamento de identidade de usuário baseada em nuvem do Azure Active Directory para gerenciar usuários. Também é possível integrar seu Active Directory no local com o Azure AD por meio da sincronização seu ambiente local com o Office 365. Depois que você configurar a sincronização você pode optar por ter sua autenticação de usuário ocorra dentro do Azure AD ou em seu diretório local.
  
## <a name="office-365-directory-synchronization"></a>Sincronização de diretórios do Office 365

Você pode usar a identidade sincronizada ou identidade federada entre sua organização local e o Office 365. Com identidade sincronizada, você gerenciar seus usuários locais e eles são autenticados pelo Windows Azure AD quando eles usam a mesma senha na nuvem como local. Esse é o cenário mais comum de sincronização de diretório. Autenticação de passagem ou identidade federada, permite que você gerencie seus usuários locais e eles são autenticados por seu diretório local. Identidade federada requer configuração adicional e permite que os usuários entrar somente uma vez. Para obter detalhes, leia [Understanding Office 365 Identity e o Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Você deseja atualizar de sincronização do Windows Azure Active Directory (DirSync) para conectar do Azure Active Directory?

Se você está usando no momento DirSync e deseja atualizar, vá direto [Azure.com](https://azure.com) para [obter instruções de atualização](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Conecte-se os pré-requisitos para o Azure AD.

Você obtém uma assinatura gratuita do Azure AD com sua assinatura do Office 365. Quando você configura a sincronização de diretório, você instalará conectar do Azure Active Directory em um dos servidores no local.
  
Para o Office 365, você precisará:
  
- Verifique se o seu domínio local (o procedimento orientará você isso).
- Ter permissões de [atribuir funções de administrador no Office 365 para empresas](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) para seu locatário do Office 365 e o Active Directory local.

Para seu servidor local no qual você instalou Connect do Azure AD, você precisará os seguintes softwares:
  
|**Sistema operacional de servidor**|**Outro software**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell é instalado por padrão, nenhuma ação é necessária.  <br> -Net 4.5.1 e versões posteriores são oferecidos pelo Windows Update. Verifique se que você instalou as atualizações mais recentes para o Windows Server, no painel de controle. |
|**Windows Server 2008 R2 com Service Pack 1 (SP1)** ou o **Windows Server 2012** | -A versão mais recente do PowerShell está disponível no Windows Management Framework 4.0. Procure no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br> -.net 4.5.1 e versões posteriores estão disponíveis no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -A última versão suportada do PowerShell está disponível no Windows Management Framework 3.0, disponível no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.net 4.5.1 e versões posteriores estão disponíveis no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Se você estiver usando o Windows Azure Active Directory DirSync, o número máximo de membros do grupo de distribuição que você pode sincronizar a partir de seu local no Active Directory para o Windows Azure Active Directory é 15.000. Para conectar do Azure AD, esse número é 50.000. 
  
Para revisar mais cuidadosamente o hardware, software, a conta e requisitos de permissões, requisitos de certificado SSL e limites de objeto para conectar do Azure AD, leia [os pré-requisitos para conectar do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
Você também pode revisar o Azure Connect da AD [histórico de versão de lançamento](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) para ver o que é incluído e corrigido em cada versão.

## <a name="to-set-up-directory-synchronization"></a>Para configurar a sincronização de diretório

1. Faça logon no Centro de administração do Office 365 e escolha **usuários** \> **Usuários ativos** no painel de navegação esquerdo.
2. No Centro de administração do Office 365, na página **usuários ativos** , escolha **mais** \> **sincronização de diretórios**.

    ![No menu mais, escolha a sincronização de diretórios](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Na página de **preparação do Active Directory** , selecione o link de **Download Microsoft Azure Active Directory Connect ferramenta** para começar. Para obter mais informações sobre o processo de instalação do Azure Active Directory Connect, consulte [mapa de instalação Azure AD Connect e a integridade de conectar-se do Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Atribuir licenças aos usuários sincronizados

Depois de você ter sincronizado seus usuários para o Office 365, são criados, mas você precisa atribuir licenças a eles para que possam usar os recursos do Office 365, como email. Para obter instruções, consulte [Atribuir licenças aos usuários no Office 365 para empresas](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Concluir a configuração domínios

Siga as etapas em [criar registros DNS para Office 365 ao gerenciar seus registros DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) para terminar de configurar seus domínios.