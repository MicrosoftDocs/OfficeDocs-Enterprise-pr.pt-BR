---
title: Plano para sincronização de diretórios para o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Descreve a sincronização de diretório com o Office 365, a limpeza do Active Directory e a ferramenta Azure Active Directory Connect.
ms.openlocfilehash: 5f380efe3293d25e2e208c5fef836a89f6fa0cc8
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085280"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Plano para sincronização de diretórios para o Office 365
Dependendo da necessidade de negócios e dos requisitos técnicos, a sincronização de diretórios é a opção de provisionamento mais comum para clientes corporativos que estão migrando para o Office 365. A sincronização de diretórios permite que as identidades sejam gerenciadas no Active Directory local e todas as atualizações para essa identidade são sincronizadas com o Office 365.
  
Há algumas coisas que você deve ter em mente ao planejar uma implementação da sincronização de diretórios, incluindo a preparação do diretório e os requisitos e a funcionalidade do Azure Active Directory. A preparação do diretório abrange algumas áreas. Eles incluem atualizações de atributo, auditoria e planejamento do controlador de domínio. Os requisitos e as funcionalidades de planejamento incluem determinar as permissões necessárias, planejamento para cenários de várias florestas/diretórios, planejamento de capacidade e sincronização bidirecional.
  
## <a name="office-365-identity-models"></a>Modelos de identidade do Office 365
O Office 365 usa dois modelos de autenticação e identidade principais: autenticação de nuvem e autenticação federada.
  
### <a name="cloud-authentication"></a>Autenticação na nuvem
[Identidade em nuvem](about-office-365-identity.md) -criar e gerenciar usuários no centro de administração do Office 365, você também pode usar o Windows PowerShell ou o Azure Active Directory para gerenciar seus usuários. 
  
[Sincronização de hash de senha com logon único contínuo](about-office-365-identity.md) -a maneira mais simples de habilitar a autenticação para objetos de diretório local no Azure AD. Com a sincronização de hash de senha (PHS), você sincroniza seus objetos de conta de usuário do Active Directory local com o Office 365 e gerencia seus usuários no local. 
  
[Autenticação de passagem com logon único contínuo](about-office-365-identity.md) -fornece uma validação de senha simples para os serviços de autenticação do Azure ad usando um agente de software em execução em um ou mais servidores locais para validar os usuários diretamente com o seu Active Directory local. 
  
### <a name="federated-authentication"></a>Autenticação federada
[Identidade federada com os serviços de Federação do Active Directory AD FS](about-office-365-identity.md) – primariamente para grandes organizações corporativas com requisitos de autenticação mais complexos, os objetos de diretório no local são sincronizados com o Office 365 e as contas de usuários são gerenciado no local. 
  
[Provedores de autenticação e de identidade](about-office-365-identity.md) de terceiros-os objetos de diretório no local podem ser sincronizados com o Office 365 e o acesso a recursos em nuvem é basicamente gerenciado por um provedor de identidade de terceiros (IDP). 
  
## <a name="active-directory-cleanup"></a>Limpeza do Active Directory
Para ajudar a garantir uma transição contínua para o Office 365 usando a sincronização, recomendamos enfaticamente que você prepare sua floresta do Active Directory antes de começar sua implantação de sincronização de diretório do Office 365.
  
Ao [Configurar a sincronização de diretórios no Office 365](set-up-directory-synchronization.md), uma das etapas é [baixar e executar a ferramenta IdFix](install-and-run-idfix.md). Você pode usar a ferramenta IdFix para ajudar com a [limpeza de diretório](prepare-directory-attributes-for-synch-with-idfix.md).
  
Sua limpeza de diretório deve se concentrar nas seguintes tarefas:

- Remover os atributos **ProxyAddress** e **userPrincipalName** duplicados.
- Atualizar atributos **userPrincipalName** vazios ou inválidos com atributos **userPrincipalName** válidos.
- Remover caracteres inválidos e questionáveis em **** excertoname, sobrenome ( **SN** ) **, sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailNickname**e **userPrincipalName** atributos. Para obter detalhes sobre como preparar atributos, consulte [lista de atributos que são sincronizados pela ferramenta de sincronização do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).
    
    > [!NOTE]
    > Estes são os mesmos atributos que o Azure AD Connect sincroniza. 
  
## <a name="multiforest-deployment-considerations"></a>Considerações sobre a implantação de várias florestas
Para várias florestas e opções de SSO, use a [instalação personalizada do Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Se sua organização tiver várias florestas para autenticação (florestas de logon), recomendamos enfaticamente o seguinte:
  
- **Avaliar a consolidação de suas florestas.** Em geral, há mais sobrecarga necessária para manter várias florestas. A menos que sua organização tenha restrições de segurança que ditem a necessidade de florestas separadas, considere simplificar o ambiente local.
- **Use somente na floresta de logon principal.** Considere a implantação do Office 365 somente em sua floresta de logon principal para a sua distribuição inicial do Office 365. 
    
Se você não puder consolidar sua implantação do Active Directory com várias florestas ou se estiver usando outros serviços de diretório para gerenciar identidades, talvez seja possível sincronizá-las com a ajuda da Microsoft ou de um parceiro.
  
Para obter mais informações, consulte [sincronização de diretórios com várias florestas com o cenário de logon único](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Ferramentas de integração de diretórios
A sincronização de diretórios é a sincronização de objetos de diretório (usuários, grupos e contatos) do seu ambiente do Active Directory local para a infraestrutura de diretório do Office 365. Consulte [ferramentas de integração de diretórios](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obter uma lista das ferramentas disponíveis e sua funcionalidade. A ferramenta recomendada para usar o [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Quando as contas de usuário são sincronizadas com o diretório do Office 365 pela primeira vez, elas são marcadas como não ativadas. Eles não podem enviar nem receber emails e não consomem licenças de assinatura. Quando estiver pronto para atribuir assinaturas do Office 365 a usuários específicos, você deverá selecionar e ativá-las atribuindo uma licença válida.
  
A sincronização de diretórios é necessária para os seguintes recursos e funcionalidade:
  
- SSO
    
- Coexistência do Lync
    
- Implantação híbrida do Exchange, incluindo:
    
  - GAL (lista de endereços global) totalmente compartilhada entre seu ambiente do Exchange local e o Office 365.
  - Sincronizar informação de GAL de sistemas de email diferentes.
  - A capacidade de adicionar usuários e remover usuários das ofertas de serviço do Office 365. Isso requer o seguinte:
  - A sincronização bidirecional deve ser configurada durante a configuração de sincronização de diretório. Por padrão, as ferramentas de sincronização de diretório gravam informações de diretório somente na nuvem. Ao configurar a sincronização bidirecional, você habilita a funcionalidade de write-back para que um número limitado de atributos de objeto seja copiado da nuvem e, em seguida, os escreveu novamente no seu Active Directory local. O Write-back também é conhecido como modo híbrido do Exchange. 
  - Uma implantação híbrida local do Exchange
  - A capacidade de mover algumas caixas de correio do usuário para o Office 365 enquanto mantém outras caixas de correio do usuário no local.
  - Remetentes confiáveis e remetentes bloqueados no local são replicados para o Office 365.
  - Delegação básica e funcionalidade de email enviar em nome de.
  - Você tem uma solução integrada de cartão inteligente ou de autenticação multifator no local.
    
- Sincronização de fotos, miniaturas, salas de conferência e grupos de segurança