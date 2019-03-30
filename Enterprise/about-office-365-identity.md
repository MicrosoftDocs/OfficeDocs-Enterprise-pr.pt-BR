---
title: Noções básicas sobre a identidade do Office 365 e o Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Saiba como a identidade do usuário é gerenciada no Office 365.
ms.openlocfilehash: c9dff7e17e4c0dcceb7cdeab86c1acdd40e01205
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001554"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Noções básicas sobre a identidade do Office 365 e o Azure Active Directory

O Office 365 usa o serviço de autenticação e identidade do usuário baseado em nuvem do Azure Active Directory (Azure AD) para gerenciar usuários. Escolha se o gerenciamento de identidades está configurado entre sua organização local e o Office 365 é uma decisão antecipada que é uma das bases de sua infraestrutura de nuvem. Como a alteração dessa configuração mais tarde pode ser difícil, considere cuidadosamente as opções para determinar o que funciona melhor para as necessidades da sua organização. Você pode escolher entre dois modelos de autenticação principais no Office 365 para configurar e gerenciar contas de usuário; **autenticação de nuvem** e **autenticação federada**.
  
É importante considerar cuidadosamente quais desses modelos de autenticação e identidade serão usados para começar a usar o. Pense no tempo, na complexidade existente e no custo de implementação e manutenção de cada uma das opções de autenticação e de identidade. Esses fatores são diferentes para todas as organizações; e você deve entender os principais conceitos das opções de identidade para ajudá-lo a escolher o modelo de autenticação e identidade que você deseja usar para sua implantação.
  
## <a name="cloud-authentication"></a>Autenticação na nuvem

Dependendo de se você tiver ou não tiver um ambiente existente do Active Directory no local, você tem várias opções para gerenciar autenticação e serviços de identidade para seus usuários com o Office 365.
  
### <a name="cloud-only"></a>Apenas Nuvem

Com o modelo somente de nuvem, você gerencia suas contas de usuário somente no Office 365. Nenhum servidor local é necessário; tudo isso é tratado na nuvem pelo Azure AD. Você cria e gerencia usuários no [centro de administração do Microsoft 365](https://admin.microsoft.com) ou usando os cmdlets e a identidade e a autenticação do Windows PowerShell [PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) são tratados completamente na nuvem pelo Azure AD. O modelo somente na nuvem é normalmente uma boa opção se: 
  
- Você não tem outro diretório de usuário local.
    
- Você tem um diretório local muito complexo e simplesmente deseja evitar o trabalho para integrá-lo.
    
- Você tem um diretório local existente, mas deseja executar uma avaliação ou um piloto do Office 365. Posteriormente, você poderá fazer a correspondência entre os usuários da nuvem e os usuários locais quando estiver pronto para se conectar ao seu diretório local.
    
Para começar a usar a identidade em nuvem, confira [Configurar o Office 365 para empresas](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Sincronização de hash de senha com logon único contínuo

A maneira mais simples de habilitar a autenticação para objetos de diretório local no Azure AD. Com a sincronização de hash de senha (PHS), você sincroniza seus objetos de conta de usuário do Active Directory local com o Office 365 e gerencia seus usuários no local. Hashes de senhas de usuário são sincronizados do seu Active Directory local para o Azure AD para que os usuários tenham a mesma senha no local e na nuvem. Quando as senhas são alteradas ou redefinidas no local, os novos hashes de senha são sincronizados com o Azure AD para que os usuários sempre possam usar a mesma senha para recursos de nuvem e recursos locais. As senhas nunca são enviadas para o Azure AD ou armazenadas no Azure AD em texto não criptografado. Alguns recursos premium do Azure AD, como proteção de identidade, exigem PHS independentemente do método de autenticação selecionado. Com o logon único contínuo, os usuários são automaticamente conectados ao Azure AD quando estão em seus dispositivos corporativos e conectados à sua rede corporativa.
  
Saiba mais sobre como [escolher a sincronização de hash de senha](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) e o [logon único contínuo](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Autenticação de passagem com logon único contínuo

Fornece uma validação de senha simples para os serviços de autenticação do Azure AD usando um agente de software em execução em um ou mais servidores locais para validar os usuários diretamente com o Active Directory local. Com a autenticação de passagem (PTA), você sincroniza os objetos de conta de usuário do Active Directory local com o Office 365 e gerencia seus usuários no local. Permite que os usuários entrem em recursos locais e do Office 365 e aplicativos usando sua conta e senha local. Essa configuração valida senhas de usuários diretamente em seu Active Directory local sem enviar hashes de senha para o Office 365. As empresas com um requisito de segurança para reforçar imediatamente os Estados da conta de usuário local, as diretivas de senha e o horário de logon usarão esse método de autenticação. Com o logon único contínuo, os usuários são automaticamente conectados ao Azure AD quando estão em seus dispositivos corporativos e conectados à sua rede corporativa.
  
Saiba mais sobre como [escolher a autenticação de passagem](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) e o [logon único contínuo](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Opções de autenticação federada

Se você tiver um ambiente do Active Directory existente no local, poderá integrar o Office 365 com seu diretório usando a autenticação federada para gerenciar a autenticação e os serviços de identidade para seus usuários no Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identidade federada com serviços de Federação do Active Directory (AD FS)

Principalmente para grandes organizações corporativas com requisitos de autenticação mais complexos, os objetos de diretório no local são sincronizados com o Office 365 e as contas de usuários são gerenciadas no local. Com o AD FS, os usuários têm a mesma senha no local e na nuvem e não precisam entrar novamente para usar o Office 365. Esse modelo de autenticação federada pode fornecer requisitos de autenticação adicionais, como a autenticação com base em Smartcard ou uma autenticação multifator de terceiros, e normalmente é necessário quando as organizações têm um requisito de autenticação Não suportado nativamente pelo Azure AD.
  
Saiba mais sobre como [escolher a identidade federada com AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Provedores de autenticação e identidade de terceiros

Os objetos de diretório no local podem ser sincronizados com o Office 365 e o acesso a recursos em nuvem é basicamente gerenciado por um provedor de identidade de terceiros (IdP). Se sua organização usa uma solução de Federação de terceiros, você pode configurar o logon com essa solução para o Office 365 desde que a solução de Federação de terceiros seja compatível com o Azure AD.
  
Saiba mais sobre a [compatibilidade de Federação do Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>ConFigurando identidade e autenticação com o Office 365

A integração de seus diretórios locais com o Office 365 e o Azure AD foi simplificada com o [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). O Azure AD Connect é a melhor maneira de conectar seus diretórios e é a recomendação da Microsoft para que as organizações Sincronizem seus usuários com a nuvem.
  
Você também pode usar os consultores do Azure AD: o [Azure ad Connect Advisor](https://aka.ms/aadconnectpwsync), o [supervisor de implantação do AD FS](https://aka.ms/adfsguidance)e o guia de [configuração do Azure ad Premium](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Treinamento em vídeo

Para obter mais informações, consulte o curso de vídeo [Office 365: gerenciar identidades usando o Azure ad Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), trazido para você pelo LinkedIn Learning.
