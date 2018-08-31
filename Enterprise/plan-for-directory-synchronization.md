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
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Descreve a sincronização de diretórios com o Office 365, limpeza do Active Directory e a ferramenta conectar do Azure Active Directory.
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539294"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Plano para sincronização de diretórios para o Office 365
Dependendo da necessidade comercial e requisitos técnicos, sincronização de diretórios é a opção de provisionamento mais comuns para os clientes corporativos que estejam mudando para o Office 365. Sincronização de diretórios permite que as identidades a ser gerenciado no Active Directory local e todas as atualizações para que a identidade são sincronizadas para o Office 365.
  
Há algumas coisas que você deve ter em mente ao planejar uma implementação de sincronização de diretórios, incluindo a preparação de diretório e os requisitos e a funcionalidade do Azure Active Directory. Preparação de diretório aborda algumas áreas. Elas incluem as atualizações de atributo, auditoria e planejamento de posicionamento de controladores de domínio. Planejamento de requisitos e a funcionalidade inclui determinar as permissões necessárias, planejamento para cenários de multiforest/diretório, planejamento de capacidade e sincronização bidirecional.
  
## <a name="office-365-identity-models"></a>Modelos de identidade do Office 365
O Office 365 usa dois modelos de autenticação e identidade principais: autenticação e autenticação federada na nuvem.
  
### <a name="cloud-authentication"></a>Autenticação de nuvem
[Identidade de nuvem](about-office-365-identity.md) - criar e gerenciar usuários no Centro de administração do Office 365, você também pode usar o Windows PowerShell ou Azure Active Directory para gerenciar seus usuários. 
  
[Senha de hash sincronizar com logon único perfeita](about-office-365-identity.md) - a maneira mais simples para habilitar a autenticação para objetos de diretório local no Windows Azure AD. Com sincronização de hash de senha (PHS), você pode sincronizar seus objetos de conta do usuário do local do Active Directory com o Office 365 e gerenciar seu usuários no local. 
  
[Autenticação de passagem com logon único perfeita](about-office-365-identity.md) - fornece uma validação de senha simples para serviços de autenticação do Azure AD usando um agente de software em execução em um ou mais servidores no local para validar os usuários diretamente com seu Active Directory no local. 
  
### <a name="federated-authentication"></a>Autenticação federada
[Identidade federada com serviços de Federação do Active Directory AD FS](about-office-365-identity.md) - principalmente para organizações de grande porte com requisitos de autenticação mais complexos, objetos de diretório são sincronizados com o Office 365 e local são contas de usuários gerenciado no local. 
  
[Provedores de autenticação e identidade de terceiros](about-office-365-identity.md) - diretório local objetos podem ser sincronizados para o Office 365 e o acesso a recursos na nuvem principalmente é gerenciado por um provedor de identidade de terceiros (IdP). 
  
## <a name="active-directory-cleanup"></a>Limpeza do Active Directory
Para ajudar a garantir uma transição direta para o Office 365 usando a sincronização, é altamente recomendável que você prepare sua floresta do Active Directory antes de começar sua implantação de sincronização de diretório do Office 365.
  
Quando você [Configurar a sincronização de diretórios no Office 365](set-up-directory-synchronization.md), uma das etapas é [Baixar](install-and-run-idfix.md)e executar a ferramenta IdFix. Você pode usar a ferramenta IdFix para ajudá-lo com a [Limpeza do diretório](prepare-directory-attributes-for-synch-with-idfix.md).
  
Limpeza do seu diretório deve focalizar as seguintes tarefas:

- Remova atributos de **proxyAddress** e **userPrincipalName** duplicados.
- Atualizar atributos **userPrincipalName** vazios ou inválidos com atributos **userPrincipalName** válidos.
- Remover caracteres questionável e inválido na **givenName**, sobrenome ( **sn** ), **sAMAccountName**, **displayName**, **email**, **proxyAddresses**, **mailNickname**e **userPrincipalName** atributos. Para obter detalhes sobre a preparação de atributos, consulte a [lista de atributos que são sincronizados pela ferramenta de sincronização do Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).
    
    > [!NOTE]
    > Esses são os mesmos atributos que sincroniza Connect do Azure AD. 
  
## <a name="multiforest-deployment-considerations"></a>Considerações sobre a implantação de várias florestas
Para várias florestas e opções de SSO, use o [sinalizador instalação do Windows Azure AD conectar](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Se sua organização tem várias florestas para autenticação (florestas de logon), é altamente recomendável o seguinte:
  
- **Avaliar consolidando suas florestas.** Em geral, há mais sobrecarga necessária para manter várias florestas. A menos que sua organização tem restrições de segurança que impõem a necessidade de florestas separadas, considere a simplificação do seu ambiente local.
- **Apenas ao uso em sua floresta do logon primário.** Considere a possibilidade de implantar o Office 365 somente na sua floresta logon primário para a distribuição inicial do Office 365. 
    
Se você não pode consolidar sua implantação de várias florestas do Active Directory ou estiver usando outros serviços de diretório para gerenciar identidades, você poderá sincronizar esses recursos com a Ajuda da Microsoft ou de um parceiro.
  
Para obter mais informações, consulte [Sincronização do diretório de várias florestas com cenário de logon único](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Ferramentas de integração de diretório
Sincronização de diretórios é a sincronização de objetos de diretório (usuários, grupos e contatos) do seu ambiente do Active Directory local para a infraestrutura de diretório do Office 365. Consulte [as ferramentas de integração de diretório](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obter uma lista das ferramentas disponíveis e suas funcionalidades. A ferramenta recomendada para usar é [Conectar do Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Quando as contas de usuário são sincronizadas com o diretório do Office 365 pela primeira vez, eles são marcados como não está ativado. Não podem enviar ou receber emails, e não consomem licenças de assinatura. Quando você estiver pronto para atribuir assinaturas do Office 365 para usuários específicos, você deve selecionar e ativá-los, atribuindo uma licença válida.
  
Sincronização de diretórios é necessária para os seguintes recursos e funcionalidades:
  
- SSO
    
- Coexistência do Lync
    
- Exchange implantação híbrida, incluindo:
    
  - Totalmente compartilhada a lista de endereços global (GAL) entre seu ambiente do Exchange no local e o Office 365.
  - Sincronizar informação de GAL de sistemas de email diferentes.
  - A capacidade de adicionar usuários e remover usuários do Office 365 ofertas de serviço. Isso requer o seguinte:
  - Sincronização bidirecional deve ser configurada durante a instalação de sincronização de diretório. Por padrão, a ferramenta de sincronização de diretório gravar informações sobre o diretório apenas para a nuvem. Quando você configurar a sincronização bidirecional, você habilita a funcionalidade de write-back de modo que um número limitado de atributos de objeto é copiado da nuvem e gravado-los novamente para seu Active Directory local. Write-back é também conhecido como modo híbrida do Exchange. 
  - Uma implantação híbrida do Exchange local
  - A capacidade de mover algumas caixas de correio do usuário para o Office 365 enquanto mantém outras usuário caixas de correio no local.
  - Remetentes seguros e remetentes bloqueados no local é replicado para o Office 365.
  - Delegação básica e funcionalidade de email enviar em nome de.
  - Você tem uma solução de autenticação de cartão inteligente ou multi-factor integrado no local.
    
- Sincronização de fotos, miniaturas, salas de conferência e grupos de segurança