---
title: Ferramentas para gerenciar contas do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/3/2018
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Saiba quais ferramentas usar para gerenciar os usuários do Office 365 e como você pode usar depende de como gerenciar identidades de usuário. '
ms.openlocfilehash: 24a7dd72603b881ea0810d0712900bc78dc34a81
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539147"
---
# <a name="tools-to-manage-office-365-accounts"></a>Ferramentas para gerenciar contas do Office 365

Você pode gerenciar usuários do Office 365 de várias maneiras diferentes, dependendo da sua configuração. Você pode gerenciar os usuários no Office 365 admin center, Windows PowerShell, seu diretório local, ou no portal de administração do Windows Azure Active Directory. Assim que você comprar o Office 365, o Centro de administração e o Windows PowerShell podem ser usado para gerenciar contas. Quando o gerenciamento de identidades de nuvem cada pessoa em sua organização tem um ID de usuário separada e uma senha para o Office 365. Se você deseja integrar com sua infraestrutura local e têm contas de usuário sincronizado com o Office 365, você pode usar Azure Active Directory Connect para fornecer sincronização de identidades e, opcionalmente, fornecer sincronização de senha ou completos funcionalidade de logon única.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planejar onde e como você irá gerenciar suas contas de usuário

Onde e como você pode gerenciar suas contas de usuário depende do modelo de identidade que você deseja usar para o Office 365. Os dois modelos gerais são autenticação federada e autenticação de nuvem.
  
### <a name="cloud-authentication"></a>Autenticação de nuvem

- [Autenticação de nuvem](about-office-365-identity.md#cloud-authentication) - criar e gerenciar usuários no Centro de administração do Office 365, você também pode usar o Windows PowerShell ou Azure Active Directory para gerenciar seus usuários. 
    
- [Senha de hash sincronizar com logon único perfeita](about-office-365-identity.md) - a maneira mais simples para habilitar a autenticação para objetos de diretório local no Windows Azure AD. Com sincronização de hash de senha (PHS), você pode sincronizar seus objetos de conta do usuário do local do Active Directory com o Office 365 e gerenciar seu usuários no local. 
    
- [Autenticação de passagem com logon único perfeita](about-office-365-identity.md) - fornece uma validação de senha simples para serviços de autenticação do Azure AD usando um agente de software em execução em um ou mais servidores no local para validar os usuários diretamente com seu Active Directory no local. 
    
### <a name="federated-authentication"></a>Autenticação federada

- [Opções de autenticação federada](about-office-365-identity.md#federated-authentication-options) - principalmente para organizações de grande porte com requisitos de autenticação mais complexos, objetos de diretório são sincronizados com o Office 365 e local contas de usuários são gerenciadas no local. 
    
- [Provedores de autenticação e identidade de terceiros](about-office-365-identity.md) - diretório local objetos podem ser sincronizados para o Office 365 e o acesso a recursos na nuvem principalmente é gerenciado por um provedor de identidade de terceiros (IdP). 
    
## <a name="managing-accounts"></a>Gerenciamento de contas

Ao decidir qual modo de sua organização irá criar e gerenciar contas, considere o seguinte:
  
- O software de sincronização de diretório precisa ser instalado em servidores no seu ambiente local para conectar as identidades entre o Office 365 e o seu diretório local.
    
- Qualquer opção de sincronização de diretório, inclusive opções de SSO, requer que seus atributos de diretório local atendem aos padrões. As especificações de quais atributos são usados em seu diretório e qual limpeza (se houver) é necessária são descritas em [Prepare to para provisionar usuários por meio da sincronização de diretório para o Office 365](prepare-for-directory-synchronization.md). Para obter instruções sobre como usar o IdFix para automatizar a limpeza do diretório, consulte [instalar e executar a ferramenta IdFix do Office 365](install-and-run-idfix.md) . 
    
- Planeje como você vai criar contas do Office 365.
    
    A tabela a seguir lista as ferramentas de gerenciamento de conta diferente.
    
|**Opção**|**Anotações**|
|:-----|:-----|
|Centro de administração do Office 365  <br/> |[Adicionar usuários individualmente ou em massa para o Office 365 - ajuda de Admin](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  Fornece uma interface web simples para adicionar e alterar as contas de usuário.  <br/>  Não pode ser usado para alterar os usuários se a sincronização de diretórios estiver ativada (o local e a licença de atribuição pode ser definida).  <br/>  Não pode ser usado com as opções SSO.  <br/> |
|Windows PowerShell  <br/> |[Gerenciar o Office 365 com o Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Permite que você adicione usuários em usuários em massa usando um script do Windows PowerShell.  <br/>  Pode ser usado para atribuir o local e licenças às contas, independentemente de como as contas são criadas.  <br/> |
|Importar grandes quantidades  <br/> |[Adicionar vários usuários ao mesmo tempo no Office 365 – Ajuda para Administradores](add-several-users-at-the-same-time.md) <br/>  Permite que você importe um arquivo CSV para adicionar um grupo de usuários para o Office 365.  <br/>  Não pode ser usado com as opções SSO.  <br/> |
|Azure Active Directory  <br/> |Você pode obter uma edição gratuita do Azure Active Directory com a sua assinatura do Office 365. Você pode executar funções como senha de autoatendimento redefinidos para usuários na nuvem e personalização das páginas para entrar e painel de acesso usando a edição livre. Para obter funcionalidade avançada, você pode atualizar para a edição básica ou a edição premium. Consulte [edições do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698465) para a lista de recursos com suporte.<br/> |
|Sincronização de diretório  <br/> |[Integrando suas identidades no local com o Windows Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Sincronização de diretórios com ou sem a sincronização de senha, use a [opção conectar AD Azure com configurações express](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Para várias florestas e opções de SSO, use o [sinalizador instalação do Windows Azure AD conectar](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Fornece a infraestrutura necessária habilitar o SSO.  <br/>  Obrigatório para muitos cenários híbridos:  <br/>  Migração em estágios  <br/>  Híbridos do Exchange  <br/>  Sincroniza a segurança e os grupos ativados por e-mail a partir de seu diretório local.  <br/> |
   
- Independentemente de como você pretende adicionar as contas de usuário para o Office 365, você precisa gerenciar vários recursos de conta, como atribuir licenças, especificando o local e assim por diante. Esses recursos podem ser gerenciados longo prazo do Centro de administração do Office 365 ou você também pode [criar contas de usuário com o Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Se você optar por adicione e gerencie todos os seus usuários por meio do Centro de administração do Office 365, você especifique o local e atribuir licenças ao mesmo tempo como a criação de conta do Office 365. Como resultado, não muito planejamento é necessário.
    
    > [!IMPORTANT]
    > Criação de contas no Office 365 sem atribuir uma licença (para o SharePoint Online, por exemplo) significa que o proprietário da conta pode visualizar o portal Office 365, mas não pode acessar qualquer um dos serviços de assinatura da sua empresa. Depois de atribuir um local e a licença, a conta for replicada para o serviço ou os serviços que você atribuiu. O usuário pode entrar em sua conta e usar os serviços que você atribuiu a eles. 
  
## <a name="next-steps"></a>Próximas etapas

[Integração com o Office 365 com ambientes locais](office-365-integration.md)
  
## <a name="see-also"></a>Confira também

[Gerenciar contas de usuário no Office 365](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

