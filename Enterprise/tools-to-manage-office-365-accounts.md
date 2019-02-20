---
title: Ferramentas para gerenciar contas do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Saiba quais ferramentas usar para gerenciar seus usuários do Office 365 e como o que você pode usar depende de como você gerencia as identidades do usuário. '
ms.openlocfilehash: e13b6a998aa6de433d85ef3be60f08703eb914d4
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085380"
---
# <a name="tools-to-manage-office-365-accounts"></a>Ferramentas para gerenciar contas do Office 365

Você pode gerenciar os usuários do Office 365 de várias maneiras diferentes, dependendo da sua configuração. Você pode gerenciar usuários no centro de administração do Office 365, no Windows PowerShell, no diretório local ou no portal de administração do Azure Active Directory. 

Assim que você adquirir o Office 365, o centro de administração e o Windows PowerShell podem ser usados para gerenciar contas. Ao gerenciar identidades de nuvem, cada pessoa em sua organização tem uma ID de usuário e senha separada para o Office 365. Se você deseja integrar com sua infraestrutura local e ter contas de usuário sincronizadas com o Office 365, você pode usar o Azure Active Directory Connect para fornecer sincronização de identidades e, opcionalmente, fornecer sincronização de senha ou completa funcionalidade de logon único.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planejar para onde e como você irá gerenciar suas contas de usuário

Onde e como você pode gerenciar suas contas de usuário depende do modelo de identidade que você deseja usar para o seu Office 365. Os dois modelos gerais são autenticação de nuvem e autenticação federada.
  
### <a name="cloud-authentication"></a>Autenticação na nuvem

- [Office 365 Identity](about-office-365-identity.md) -Create and Manage Users in the Office 365 Admin Center, você também pode usar o Windows PowerShell ou o Azure Active Directory para gerenciar seus usuários.
- [Sincronização de hash de senha com logon único contínuo](about-office-365-identity.md) -a maneira mais simples de habilitar a autenticação para objetos de diretório local no Azure AD. Com a sincronização de hash de senha (PHS), você sincroniza seus objetos de conta de usuário do Active Directory local com o Office 365 e gerencia seus usuários no local. 
- [Autenticação de passagem com logon único contínuo](about-office-365-identity.md) -fornece uma validação de senha simples para os serviços de autenticação do Azure ad usando um agente de software em execução em um ou mais servidores locais para validar os usuários diretamente com o seu Active Directory local. 
    
### <a name="federated-authentication"></a>Autenticação federada

- [Office 365 Identity](about-office-365-identity.md) -primariamente para grandes organizações corporativas com requisitos de autenticação mais complexos, os objetos de diretório no local são sincronizados com o Office 365 e as contas de usuários são gerenciadas no local. 
- [Provedores de autenticação e de identidade](about-office-365-identity.md) de terceiros-os objetos de diretório no local podem ser sincronizados com o Office 365 e o acesso a recursos em nuvem é basicamente gerenciado por um provedor de identidade de terceiros (IDP). 
    
## <a name="managing-accounts"></a>Gerenciando contas

Ao decidir o modo como sua organização criará e gerenciará contas, considere o seguinte:
  
- O software de sincronização de diretório precisa ser instalado em servidores dentro do seu ambiente local para conectar as identidades entre o Office 365 e seu diretório local.
- Qualquer opção de sincronização de diretório, incluindo as opções de SSO, requer que seus atributos de diretório local atendam aos padrões. As informações específicas de quais atributos são usados no seu diretório e qual limpeza (se houver) é necessária são descritas em preparar-se [para provisionar usuários por meio da sincronização de diretórios com o Office 365](prepare-for-directory-synchronization.md). ConFira [instalar e executar a ferramenta IdFix do Office 365](install-and-run-idfix.md) para obter instruções sobre como usar o IdFix para automatizar a limpeza de diretório. 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a>Planejar como você vai criar contas do Office 365
A tabela a seguir lista as diferentes ferramentas de gerenciamento de conta:
    
|**Opção**|**Anotações**|
|:-----|:-----|
|**Office 365 admin center** | - [Adicionar usuários individualmente ou em massa ao Office 365-ajuda para administradores](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> – Fornece uma interface Web simples para adicionar e alterar contas de usuário. <br> – Não pode ser usado para alterar usuários se a sincronização de diretórios estiver habilitada (a atribuição de local e licença pode ser definida). <br> – Não pode ser usado com opções de SSO. <br> |
|**Windows PowerShell** | - [Gerenciar o Office 365 com o Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> – Permite que você adicione usuários a usuários em massa usando um script do Windows PowerShell. <br> – Pode ser usado para atribuir local e licenças a contas, independentemente de como as contas são criadas. <br> |
|**Importar grandes quantidades** | - [Adicionar vários usuários ao mesmo tempo para o Office 365-ajuda para administradores](add-several-users-at-the-same-time.md) <br> – Permite que você importe um arquivo CSV para adicionar um grupo de usuários ao Office 365. <br> – Não pode ser usado com opções de SSO. <br> |
|**Azure Active Directory** | – Você Obtém uma edição gratuita do Azure Active Directory com sua assinatura do Office 365. – Você pode executar funções como redefinição de senha de autoatendimento para usuários em nuvem e a personalização das páginas de entrada e painel de acesso usando a edição gratuita.<br> – Para obter uma funcionalidade aprimorada, você pode atualizar para o Basic Edition ou Premium Edition. ConFira [Azure Active Directory Editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) para obter a lista de recursos com suporte.<br> |
|**Sincronização de diretório** | - [Integração de suas identidades locais com o Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> – Para a sincronização de diretório com ou sem sincronização de senha, use o [Azure ad Connect com as configurações expressas](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br>  – Para várias florestas e opções de SSO, use a [instalação personalizada do Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430). <br> – Fornece a infraestrutura necessária para habilitar o SSO. <br> – Necessário para vários cenários híbridos (migração em estágios, Exchange híbrido) <br> – Sincroniza os grupos de segurança e habilitados para email do seu diretório local. <br> |
   
Independentemente de como você pretende adicionar as contas de usuário ao Office 365, você precisa gerenciar vários recursos de conta, como atribuir licenças, especificar o local e assim por diante. Esses recursos podem ser gerenciados de longo prazo no centro de administração do Office 365 ou você também pode [criar contas de usuário com o Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
Se você optar por adicionar e gerenciar todos os seus usuários por meio do centro de administração do Office 365, você especificará o local e atribuirá licenças ao mesmo tempo que a criação da conta do Office 365. Como resultado, não é necessário o planejamento.
    
> [!IMPORTANT]
> A criação de contas no Office 365 sem a atribuição de uma licença (para o SharePoint Online, por exemplo) significa que o proprietário da conta pode exibir o portal do Office 365, mas não pode acessar qualquer um dos serviços dentro da assinatura da sua empresa. Depois de atribuir um local e a licença, a conta é replicada para o serviço ou serviços que você atribuiu. O usuário pode entrar em sua conta e usar os serviços que você atribuiu a eles.