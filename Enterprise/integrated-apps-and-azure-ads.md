---
title: Aplicativos integrados e Azure AD para administradores do Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Saiba como os aplicativos integrados do O365 são registrados e administrados no Azure AD
ms.openlocfilehash: 6846b57256bd81ae8d2054d69bd8f980d91d6ce9
ms.sourcegitcommit: 160a2564c90a4d64d19f072e0de9fe1b3cd0c917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "42417056"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Aplicativos integrados e Azure AD para administradores do Office 365

Há mais informações para gerenciar aplicativos integrados do que apenas [Ativar ou desativar aplicativos integrados](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114). Com o advento das APIs REST do Office 365, os usuários podem conceder aos aplicativos acesso aos dados do Office 365, como emails, calendários, contatos, usuários, grupos, arquivos e pastas. Por padrão, os usuários precisam conceder permissões individualmente a cada aplicativo, mas isso não é bem redimensionado se você deseja autorizar um aplicativo uma vez no nível de administrador global e distribuí-lo para toda a sua organização por meio do inicializador de aplicativos. Para fazer isso, você deve registrar o aplicativo no Azure AD. Há algumas etapas que você precisa seguir antes de registrar um aplicativo no Azure AD e algumas informações de fundo que você deve saber que podem ajudá-lo a gerenciar aplicativos em sua organização do Office 365. Este artigo aponta você para esses recursos.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Recursos do Azure AD para administradores do Office 365

Você precisa fazer estes dois procedimentos antes de gerenciar seus aplicativos do Office 365 no Azure AD.
  
|**Pré-requisitos**|**Comments**|
|:-----|:-----|
|[Usar sua assinatura gratuita do Azure Active Directory no Office 365](https://docs.microsoft.com/microsoft-365/compliance/use-your-free-azure-ad-subscription-in-office-365) <br/> |Cada assinatura paga do Office 365 vem com uma assinatura gratuita do Azure Active Directory. Você pode usar o Azure AD para gerenciar seus aplicativos e para criar e gerenciar contas de usuário e de grupo. Para usar o Azure AD, basta ir para o portal do Azure e entrar usando sua conta do Office 365.  <br/> |
|[Ativando ou desativando aplicativos integrados](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Você deve ativar aplicativos integrados para seus usuários para permitir que aplicativos de terceiros acessem suas informações do Office 365 e para registrar aplicativos no Azure AD. Por exemplo, quando alguém usa um aplicativo de terceiros, esse aplicativo pode pedir permissão para acessar seu calendário e editar arquivos que estão em uma pasta do OneDrive for Business.  <br/> |
   
O gerenciamento de aplicativos do Office 365 requer que você tenha conhecimento dos aplicativos no Azure AD. Estes artigos ajudam a fornecer o plano de fundo necessário.
  
|**Artigo de plano de fundo**|**Comments**|
|:-----|:-----|
|[Conheça o inicializador de aplicativos do Office 365](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Se você é novo no inicializador de aplicativos, você pode estar se perguntando o que é e como usá-lo. O inicializador de aplicativos foi projetado para ajudá-lo a obter seus aplicativos de qualquer lugar no Office 365.  <br/> |
|[Visão geral das APIs de Gerenciamento do Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) <br/> |As APIs do Office 365 permitem que você forneça acesso aos dados do Office 365 do cliente, incluindo as coisas com as quais eles se preocupam com a maioria: seus emails, calendários, contatos, usuários e grupos, arquivos e pastas. Há um bom diagrama neste artigo que ilustra a relação entre os aplicativos do Office 365, o AD do Azure e os dados que os aplicativos acessam.  <br/> |
|[Integração de aplicativos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Saiba mais sobre os aplicativos integrados ao Azure Active Directory e como registrar seu aplicativo, compreender os conceitos por trás de um aplicativo registrado e saiba mais sobre as diretrizes de identidade visual para aplicativos de vários locatários.  <br/> |
|[Adicionar blocos personalizados ao inicializador de aplicativos](https://docs.microsoft.com/office365/admin/manage/customize-the-app-launcher)  <br/> |O inicializador de aplicativos no Office 365 torna mais fácil para os usuários encontrar e acessar seus aplicativos. Este artigo descreve as maneiras como um desenvolvedor pode fazer seus aplicativos aparecerem nos iniciadores de aplicativos dos usuários e também conceder a eles uma experiência de logon único (SSO) usando suas credenciais do Office 365.  <br/> |
|[Tutoriais de integração do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |O objetivo desses tutoriais é mostrar como configurar o Azure AD SSO para aplicativos SaaS de terceiros.  <br/> |
|[Cenários de autenticação do Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |O Azure AD simplifica a autenticação para desenvolvedores ao fornecer a identidade como um serviço, com suporte para protocolos padrão do setor, como OAuth 2,0 e OpenID Connect, bem como bibliotecas de código aberto para diferentes plataformas para ajudá-lo a iniciar a codificação rapidamente. Este documento ajuda você a compreender os vários cenários com suporte para o Azure AD e mostra como começar.  <br/> |
|[Acesso ao aplicativo](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |O Azure AD permite a integração fácil a muitos dos aplicativos de software populares (SaaS) atuais. Ele fornece gerenciamento de identidade e acesso e fornece um painel de acesso para os usuários onde eles podem descobrir quais aplicativos têm acesso a eles e onde eles podem usar o SSO para acessar seus aplicativos. Este artigo fornece links para os recursos relacionados que permitem que você saiba mais sobre os aprimoramentos de acesso ao aplicativo do Azure AD e como você pode contribuir para eles.  <br/> |
|[Personalizar a experiência do Office 365](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Você pode obter acesso rápido aos aplicativos que você usa todos os dias adicionando ou removendo aplicativos no inicializador de aplicativos do Office 365.  <br/> |
   

