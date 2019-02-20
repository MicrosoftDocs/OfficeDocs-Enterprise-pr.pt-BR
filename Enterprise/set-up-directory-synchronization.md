---
title: Configurar a sincronização de diretórios com o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085260"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurar a sincronização de diretórios com o Office 365

O Office 365 usa o serviço de gerenciamento de identidade de usuário baseado em nuvem do Azure Active Directory para gerenciar usuários. Você também pode integrar seu Active Directory local com o Azure AD sincronizando seu ambiente local com o Office 365. Depois de configurar a sincronização, você pode optar por fazer com que a autenticação do usuário ocorra no AD do Azure ou no diretório local.
  
## <a name="office-365-directory-synchronization"></a>Sincronização de diretórios do Office 365

Você pode usar identidade sincronizada ou identidade federada entre sua organização local e o Office 365. Com a identidade sincronizada, você gerencia os usuários locais e eles são autenticados pelo Azure AD quando eles usam a mesma senha na nuvem como local. Este é o cenário mais comum de sincronização de diretórios. A autenticação de passagem ou a identidade federada permite que você gerencie os usuários no local e eles são autenticados por seu diretório local. A identidade federada requer configuração adicional e permite que os usuários entrem apenas uma vez. Para obter detalhes, leia underStanding [Office 365 Identity e Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Deseja atualizar da sincronização do Windows Azure Active Directory (dirSync) para o Azure Active Directory Connect?

Se você está usando o dirSync e deseja atualizar, vá para [Azure.com](https://azure.com) para obter [instruções de atualização](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Pré-requisitos para o Azure AD Connect

Você recebe uma assinatura gratuita do Azure AD com sua assinatura do Office 365. Ao configurar a sincronização de diretórios, você instalará o Azure Active Directory Connect em um dos servidores locais.
  
Para o Office 365, você precisará:
  
- Verifique seu domínio local (o procedimento o guiará por isso).
- [Atribuir funções de administrador no office 365 para](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissões de negócios para o locatário do Office 365 e o Active Directory local.

Para o servidor local no qual você instala o Azure AD Connect, você precisará do seguinte software:
  
|**SISTEMA operacional do servidor**|**Outro software**|
|:-----|:-----|
|**Windows Server 2012 R2** | -O PowerShell é instalado por padrão, nenhuma ação é necessária.  <br> -NET 4.5.1 e versões posteriores são oferecidos por meio do Windows Update. Verifique se você instalou as atualizações mais recentes do Windows Server no painel de controle. |
|**Windows server 2008 R2 com Service Pack 1 (SP1)** ou **Windows Server 2012** | – A versão mais recente do PowerShell está disponível no Windows Management Framework 4,0. Procure por ele no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br> – As versões do .NET 4.5.1 e posteriores estão disponíveis no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | – A versão com suporte mais recente do PowerShell está disponível no Windows Management Framework 3,0, disponível no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> – As versões do .NET 4.5.1 e posteriores estão disponíveis no [centro de download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Se você estiver usando o dirSync do Azure Active Directory, o número máximo de membros do grupo de distribuição que você pode sincronizar de seu Active Directory local para o Azure Active Directory é 15.000. Para o Azure AD Connect, esse número é 50.000. 
  
Para rever cuidadosamente os requisitos de hardware, software, conta e permissões, requisitos de certificado SSL e limites de objeto para o Azure AD Connect, leia os [pré-requisitos para o Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
Você também pode analisar o histórico de versões da [versão](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) do Azure ad Connect para ver o que está incluído e corrigido em cada versão.

## <a name="to-set-up-directory-synchronization"></a>Para configurar a sincronização de diretórios

1. entre no centro de administração do Office 365 e escolha usuários **ativos** do **usuário** \> no painel de navegação à esquerda.
2. no centro de administração do Office 365, na página **usuários ativos** , escolha **mais** \> **sincronização de diretório**.

    ![No menu mais, escolha sincronização de diretório](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Na página de **preparação do Active Directory** , selecione o link **baixar a ferramenta de conexão do Active Directory do Microsoft Azure** para começar. Para obter mais informações sobre o processo de instalação do Azure Active Directory Connect, consulte [Azure ad Connect e Azure ad Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Atribuir licenças a usuários sincronizados

Depois de sincronizar seus usuários com o Office 365, eles são criados, mas você precisa atribuir licenças a eles para que eles possam usar os recursos do Office 365, como email. Para obter instruções, consulte [assign licenses to Users in Office 365 for Business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Concluir a configuração dos domínios

Siga as etapas em [criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) para concluir a configuração dos seus domínios.