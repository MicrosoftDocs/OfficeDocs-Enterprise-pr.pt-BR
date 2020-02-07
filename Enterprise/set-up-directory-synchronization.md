---
title: Configurar a sincronização de diretório no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: Saiba como configurar a sincronização de diretório entre o Office 365 e o seu Active Directory local.
ms.openlocfilehash: d549d2b56ef1d642e5dfc16b747e6eb909dd7337
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844042"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurar a sincronização de diretório no Office 365

*Esse artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*

O Office 365 usa um inquilino do Azure Active Directory (Azure AD) para armazenar e gerenciar identidades para autenticação e permissões para acessar recursos baseados em nuvem. 

Se você tiver um Active Directory Domain Services (AD DS) local, poderá sincronizar suas contas de usuário, grupos e contatos do AD DS com o inquilino do Azure AD de sua assinatura do Office 365. Esta é uma identidade híbrida do Office 365. Estes são seus componentes.

![Componentes da sincronização de diretórios para o Office 365](./media/about-office-365-identity/hybrid-identity.png)

O Azure AD Connect é executado em um servidor local e sincroniza seu AD DS com o locatário do Azure AD. Juntamente com a sincronização de diretórios, você também pode especificar estas opções de autenticação:

- Sincronização de hash de senha (PHS)

  O Azure AD realiza a própria autenticação.

- Autenticação de passagem (PTA)

  O Azure AD faz o AD DS executar a autenticação.

- Autenticação federada

  O Azure AD redireciona o computador cliente que solicita autenticação para entrar em contato com outro provedor de identidade.

Confira [Identidades híbridas](plan-for-directory-synchronization.md) para obter mais informações.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Revisar os pré-requisitos para o Azure AD Connect

Você recebe uma assinatura gratuita do Azure AD com a sua assinatura do Office 365. Ao configurar a sincronização de diretórios, você instalará o Azure AD Connect em um dos servidores locais.
  
Para o Office 365, é necessário:
  
- Verificar o seu domínio local. O assistente do Azure AD Connect orientará você sobre isso.
- Obtenha os nomes de usuário e senhas para as contas de administrador do seu locatário do Office 365 e do AD DS.

Para o servidor local no qual você instala o Azure AD Connect, será necessário:
  
|**Sistema operacional do servidor**|**Outro software**|
|:-----|:-----|
|Windows Server 2012 R2 e posterior | - O PowerShell é instalado por padrão, nenhuma ação é necessária.  <br> - O Net 4.5.1 e as versões posteriores são oferecidos por meio do Windows Update. Verifique se você instalou as atualizações mais recentes para o Windows Server no Painel de Controle. |
|Windows Server 2008 R2 com Service Pack 1 (SP1)** ou Windows Server 2012 | - A versão mais recente do PowerShell está disponível no Windows Management Framework 4.0. Procure por ela no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - O .NET 4.5.1 e as versões posteriores estão disponíveis no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | - A última versão do Windows PowerShell com suporte está disponível no Windows Management Framework 3.0, disponível no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - O .NET 4.5.1 e as versões posteriores estão disponíveis no [Centro de Download da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Confira [Pré-requisitos para o Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) para obter detalhes sobre requisitos de hardware, software, conta e permissões, requisitos de certificado SSL e limites de objetos para o Azure AD Connect.
  
Também é possível examinar o [histórico de versões de lançamento](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) do Azure AD Connect para ver o que está incluído e o que foi corrigido em cada versão.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Instalar o Azure AD Connect e configurar a sincronização de diretórios

Antes de começar, verifique se você tem:

- O nome de usuário e senha de um administrador global do Office 365
- O nome de usuário e senha de um administrador de domínio do AD DS
- Qual método de autenticação (PHS, PTA, federado)
- Se você deseja usar o [Logon Único Contínuo (SSO) do Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

Siga estas etapas:

1. Entre no [centro de administração do Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) e escolha **Usuários** \> **Usuários Ativos** na navegação à esquerda.
2. Na página **usuários ativos** , escolha **mais** (três pontos) \> **sincronização de diretório**.
  
3. Na página de **preparação do Azure Active Directory** , selecione a guia **vá para o centro de download para obter o link da ferramenta Azure ad Connect** para começar. 
4. Siga as etapas no [roteiro de instalação do Azure AD Connect e do Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Concluir a configuração dos domínios

Siga as etapas em [Criar registros DNS para o Office 365 ao gerenciar seus registros DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) para concluir a configuração dos seus domínios.

## <a name="next-step"></a>Próxima etapa

[Atribuir licenças às contas de usuário](assign-licenses-to-user-accounts.md)
