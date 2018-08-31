---
title: Aplicativos integrados e Microsoft Azure AD para administradores do Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 3/5/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Saiba como o O365 integrado aplicativos registrados e administrado no Azure AD.
ms.openlocfilehash: 0482271f15dc5e2b81e36fd265b49da6eba18702
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914996"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Aplicativos integrados e Microsoft Azure AD para administradores do Office 365

Há mais com o gerenciamento de aplicativos integrados que acabou [Desativando integrada Apps ativada ou desativada](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114). Com o advento das APIs REST Office 365, os usuários podem conceder acesso de aplicativos aos seus dados do Office 365, como emails, calendários, contatos, usuários, grupos, arquivos e pastas. Por padrão, os usuários precisam individualmente conceder permissões para cada aplicativo, mas isso não pode ser dimensionado bem se você deseja autorizar um aplicativo uma vez a nível de administrador global e distribui-la para toda a sua organização por meio do iniciador de aplicativo. Para fazer isso, você deve registrar o aplicativo no Windows Azure AD. Existem algumas etapas que você deve realizar antes de você pode registrar um aplicativo no Azure AD e algumas informações de plano de fundo que você deve saber que podem ajudá-lo gerenciá-los em sua organização do Office 365. Este artigo o aponta a esses recursos.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Recursos de Windows Azure AD para os administradores do Office 365

Você deve fazer estes dois procedimentos antes de poder gerenciar seus aplicativos do Office 365 no Azure AD.
  
|**Pré-requisitos**|**Comments**|
|:-----|:-----|
|[Registre a sua assinatura gratuita do Active Directory do Azure](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Cada assinatura paga para o Office 365 vem com uma assinatura gratuita do Windows Azure Active Directory. Você pode usar o Windows Azure AD para gerenciar seus aplicativos e para criar e gerenciar contas de usuário e grupo. Para ativar essa assinatura e acessar o portal de gerenciamento do Windows Azure, você deve concluir um processo de registro de uma única vez. Posteriormente, você pode ir para o Windows Azure AD do Centro de administração do Office 365.  <br/> |
|[Ativar ou desativar a aplicativos integrados](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Você deve ativar aplicativos integrada aos seus usuários para permitir que aplicativos de terceiros acessar suas informações do Office 365 e de registro de aplicativos no Windows Azure AD. Por exemplo, quando alguém usa um aplicativo de terceiros, esse aplicativo pode pedir para permissão para acessar seu calendário e editar arquivos que estão em um pasta de negócios do OneDrive.  <br/> |
   
Gerenciamento de aplicativos do Office 365 exige que você tenha conhecimento de aplicativos no Windows Azure AD. Estes artigos ajudam a oferecer o plano de fundo que você precisa.
  
|**Artigo de plano de fundo**|**Comments**|
|:-----|:-----|
|[Atender o iniciador de aplicativo do Office 365](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Se estiver familiarizado com o iniciador de aplicativo, talvez você queira saber o que é e como usá-lo. O iniciador app foi projetado para ajudá-lo a obter para seus aplicativos em qualquer lugar no Office 365.  <br/> |
|[Adicionar, atualizar e remover um aplicativo](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |Este tópico mostra como adicionar, atualizar ou remover um aplicativo no Windows Azure Active Directory. Você vai aprender sobre os diferentes tipos de aplicativos que podem ser integrados ao Windows Azure AD e como configurar seus aplicativos para acessar outros recursos, como web APIs e muito mais.  <br/> |
|[Ter seu aplicativo aparecem no iniciador de aplicativo do Office 365](https://go.microsoft.com/fwlink/?LinkId=617138).  <br/> |O iniciador app no Office 365 que torna mais fácil para os usuários encontrem e acessar seus aplicativos. Este artigo descreve as maneiras como você como um desenvolvedor pode obter seus aplicativos apareça na iniciadores de aplicativo dos usuários e também oferecem uma experiência de logon único (SSO) usando suas credenciais do Office 365.  <br/> |
|[Visão geral da plataforma APIs do Office 365](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |As APIs do Office 365 lhe permite fornecer acesso aos dados do Office 365 do cliente, incluindo as coisas mais eles importam — seus emails, calendários, contatos, os usuários e grupos, arquivos e pastas. Há um diagrama boa neste artigo que ilustra a relação entre aplicativos do Office 365, Windows Azure AD, e os dados que acessam os aplicativos.  <br/> |
|[Integração de aplicativos no Windows Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617141) <br/> | Saiba mais sobre os aplicativos que são integrados com o Azure Active Directory e como registrar seu aplicativo, entender os conceitos por trás de um aplicativo registrado e saiba mais sobre diretrizes para multi-branding aplicativos de locatário.  <br/> |
|[Tutoriais de integração do Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617144) <br/> |O objetivo desses tutoriais é mostrar como configurar o SSO do Windows Azure AD para aplicativos SaaS de terceiros.  <br/> |
|[Cenários de autenticação do Azure AD.](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD simplifica a autenticação para desenvolvedores, fornecendo identidade como um serviço, com suporte para protocolos padrão do setor como OAuth 2.0 e conecte-se OpenID, bem como abrir bibliotecas de origem para diferentes plataformas para ajudá-lo a iniciar rapidamente a codificação. Este documento ajuda você a entender os vários cenários Azure AD suporta e mostra como começar.  <br/> |
|[Acesso de aplicativo](https://go.microsoft.com/fwlink/?LinkId=617146) <br/> |Azure AD permite fácil integração a muitos dos softwares populares de hoje como um aplicativos de serviço (SaaS); Ele fornece gerenciamento de acesso e identidade, e ele oferece um painel de acesso para usuários onde eles possam descobrir qual eles têm acesso ao aplicativo e onde eles podem usar o SSO para acessar seus aplicativos. Este artigo fornece links para os recursos relacionados que permitem que você saiba mais sobre os aprimoramentos de acesso do aplicativo para o Windows Azure AD e como você pode contribuir com eles.  <br/> |
|[Adicionar ou remover os blocos no iniciador de aplicativo do Office 365](https://support.office.com/article/0b71362d-ce56-4d21-9b2f-bdb750a82b81) <br/> |Você pode obter acesso rápido de aplicativos que você usa diariamente, adicionando ou removendo aplicativos em que o iniciador de aplicativo do Office 365.  <br/> |
   

