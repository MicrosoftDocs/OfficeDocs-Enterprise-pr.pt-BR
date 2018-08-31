---
title: Noções básicas sobre identidade do Office 365 e Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Saiba como a identidade do usuário é gerenciada no Office 365.
ms.openlocfilehash: 0fb6e77aef4495b2284256c13cb21320e6292746
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914976"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Noções básicas sobre identidade do Office 365 e Azure Active Directory

O Office 365 usa o usuário baseada em nuvem autenticação e identidade serviço Azure Active Directory (AD Azure) para gerenciar usuários. Escolhendo se o gerenciamento de identidade é configurado entre sua organização local e o Office 365 é uma decisão inicial que é uma das bases da sua infraestrutura de nuvem. Como alterar essa configuração posteriormente pode ser difícil, considere cuidadosamente as opções para determinar o que funciona melhor para as necessidades da sua organização. Você pode escolher entre dois modelos de autenticação principal no Office 365 para configurar e gerenciar contas de usuário; **autenticação de nuvem** e **autenticação federada**.
  
É importante considerar cuidadosamente qual desses modelos de autenticação e identidade usar para fazer e em execução. Pense sobre o tempo, complexidade existente e custo para implementar e manter cada uma das opções de autenticação e identidade. Esses fatores são diferentes para cada organização; e você deve compreender os conceitos principais para as opções de identidade para ajudá-lo a escolher o modelo de identidade e autenticação que você deseja usar para sua implantação.
  
## <a name="cloud-authentication"></a>Autenticação de nuvem

Dependendo se você tiver ou não têm um existente do Active Directory ambiente local, você tem várias opções para gerenciar os serviços de autenticação e identidade para os usuários com o Office 365.
  
### <a name="cloud-only"></a>Apenas Nuvem

Com o modelo somente em nuvem, você gerenciar suas contas de usuário no Office 365 apenas. Não há servidores locais são necessários; é tudo tratado na nuvem pelo Windows Azure AD. Criar e gerenciar usuários no Centro de administração do Office 365 ou usando o Windows PowerShell [cmdlets do PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) e identidade e autenticação são tratados completamente na nuvem por Azure AD. O modelo de nuvem apenas geralmente é uma boa se escolher: 
  
- Você não tem que nenhum outro diretório de usuário local.
    
- Você tem um diretório local muito complexa e deseja simplesmente obter a evitar o trabalho de integrar com ele.
    
- Você tem um diretório local existente, mas você deseja executar uma avaliação ou piloto do Office 365. Posteriormente, você pode combinar os usuários de nuvem para usuários locais quando estiver pronto para se conectar ao seu diretório local.
    
Para começar com a identidade de nuvem, consulte [Configurar o Office 365 para empresas](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Sincronização de hash de senha com perfeita sign-on único

A maneira mais simples para habilitar a autenticação para objetos de diretório local no Windows Azure AD. Com sincronização de hash de senha (PHS), você pode sincronizar seus objetos de conta do usuário do local do Active Directory com o Office 365 e gerenciar seu usuários no local. Hashes de senhas de usuário são sincronizados do seu Active Directory no local para o Windows Azure AD para que os usuários tenham a mesma senha no local e na nuvem. Quando as senhas são alteradas ou redefinir local, os novos hashes de senha são sincronizados para o Windows Azure AD para que os usuários possam usar sempre a mesma senha para recursos de nuvem e no local. As senhas nunca são enviadas para o Windows Azure AD ou armazenadas no Azure AD em texto não criptografado. Alguns recursos premium do Azure AD, como a proteção de identidade, exigem PHS independentemente de qual método de autenticação está selecionado. Com perfeita sign-on único, os usuários entrarão automaticamente Windows Azure AD quando estão em seus dispositivos corporativos e conectados à rede corporativa.
  
Saiba mais sobre [escolhendo a sincronização de hash de senha](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) e [perfeita single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Autenticação de passagem com perfeita sign-on único

Fornece uma validação de senha simples para serviços de autenticação do Azure AD usando um agente de software em execução em um ou mais servidores no local para validar os usuários diretamente com o seu local no Active Directory. Com a autenticação de passagem (PTA), você pode sincronizar objetos de conta de usuário local do Active Directory com o Office 365 e gerenciar seu usuários no local. Permite que seus usuários entrar no local e recursos do Office 365 e aplicativos usando sua conta local e a senha. Essa configuração valida senhas dos usuários diretamente em relação ao seu local Active Directory sem enviar hashes de senha para o Office 365. As empresas com um requisito de segurança para impor imediatamente a conta de usuário local afirma, diretivas de senha e o horário de logon usaria este método de autenticação. Com perfeita sign-on único, os usuários entrarão automaticamente Windows Azure AD quando estão em seus dispositivos corporativos e conectados à rede corporativa.
  
Saiba mais sobre [escolhendo a autenticação de passagem](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) e [perfeita single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Opções de autenticação federada

Se você tiver um existente do Active Directory ambiente local, você pode integrar o Office 365 com o seu diretório, usando a autenticação federada para gerenciar os serviços de autenticação e identidade para os usuários no Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identidade federada com os serviços de Federação do Active Directory (AD FS)

Principalmente para organizações de grande porte com requisitos de autenticação mais complexos, objetos de diretório são sincronizados com o Office 365 e local contas de usuários são gerenciadas no local. Com o AD FS, os usuários têm a mesma senha no local e na nuvem e eles não precisam entrar novamente para usar o Office 365. Este modelo de autenticação federada pode fornecer requisitos de autenticação adicional, autenticação baseada em cartão inteligente ou uma terceiro a autenticação multifator e é geralmente necessário quando as organizações têm um requisito de autenticação não nativamente suportados pelo Windows Azure AD.
  
Saiba mais sobre como [Escolher a identidade federada com AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Provedores de autenticação e identidade de terceiros

Objetos de diretório que podem ser sincronizados para o Office 365 e local acesso aos recursos de nuvem principalmente é gerenciado por um provedor de identidade de terceiros (IdP). Se sua organização usa uma solução de federação de terceiros, você pode configurar logon com essa solução para o Office 365 desde que a solução de federação de terceiros é compatível com o Windows Azure AD.
  
Saiba mais sobre a [compatibilidade de Federação do Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Configurando a autenticação e identidade com o Office 365

Integrando seus diretórios no local com o Office 365 e o Azure AD foi simplificado com [Connect do Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Conectar do Azure AD é a melhor maneira de se conectar seus diretórios e recomendação da Microsoft, para as organizações para sincronizar seus usuários para a nuvem.
  
Você também pode usar os consultores do Azure AD: o [Azure Connect da AD advisor](https://aka.ms/aadconnectpwsync), o [Supervisor de implantação do AD FS](https://aka.ms/adfsguidance)e o [guia de instalação do Windows Azure AD Premium](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Treinamento em vídeo

Para obter mais informações, consulte o curso vídeo [Office 365: gerenciar identidades usando o Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), levado a você pelo aprendizado LinkedIn.
