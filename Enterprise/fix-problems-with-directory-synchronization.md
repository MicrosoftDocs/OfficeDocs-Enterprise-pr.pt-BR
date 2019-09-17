---
title: Corrigindo problemas de sincronização de diretório no Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Descreve causas comuns de problemas com a sincronização de diretórios no Office 365 e fornece alguns métodos para ajudar a solucionar problemas.
ms.openlocfilehash: 3a1cf63122be84dc3e1c60e84a9a3a488f81bc0f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067667"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Corrigindo problemas de sincronização de diretório no Office 365

Com a sincronização de diretórios, você pode continuar a gerenciar os usuários e grupos locais, e sincronizar acréscimos, eliminações e alterações com a nuvem. Mas a configuração é um pouco complicada e algumas vezes pode ser difícil identificar a origem dos problemas. Temos recursos para ajudá-lo a identificar os possíveis problemas e corrigi-los.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Como saber se algo está errado?

A primeira indicação de que algo está errado é quando o bloco do Status do DirSync no Centro de administração do Microsoft 365 indica que há um problema:
  
![O bloco de Status do DirSync na visualização do centro de administração](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Você também receberá um email (no email alternativo e no seu email de administrador) do Office 365 que indica que seu locatário encontrou erros de sincronização de diretório. Confira os detalhes em [Identificar erros de sincronização de diretório no Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Como usar a ferramenta Azure Active Directory Connect?

No [Centro de administração do Microsoft 365](https://admin.microsoft.com), navegue até ** Usuários ** \> **Usuários ativos**. Clique no menu **Mais** e selecione **Sincronização de diretórios**. 
  
![No menu Mais, escolha Sincronização de diretórios](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
Siga as [instruções no assistente](set-up-directory-synchronization.md) para baixar o Azure AD Connect. 
  
Se você ainda estiver usando a Sincronização do Azure Active Directory (DirSync), confira o tópico [Como solucionar problemas de instalação da Ferramenta de Sincronização do Azure Active Directory e mensagens de erro do Assistente de Configuração no Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para saber mais sobre os requisitos do sistema para instalar o DirSync, as permissões necessárias e como solucionar erros comuns. 
  
Para atualizar da Sincronização do Azure Active Directory para o Azure AD Connect, confira as [instruções de atualização](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Resolvendo causas comuns de problemas com a sincronização de diretórios no Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Os objetos sincronizados não são exibidos ou atualizados online, ou estou recebendo relatórios de erros de sincronização do serviço.**

- [Sincronização de identidades e resiliência do atributo duplicada](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Tenho um alerta no centro de administração ou estou recebendo emails automáticos informando que não houve eventos de sincronização recentes**
- [Solucionar problemas de conectividade com o Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Contas e permissões do Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Sincronização do Azure AD Connect: como gerenciar a conta de serviço do Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [A sincronização do diretório com o Azure Active Directory para ou você é alertado de que a sincronização não aconteceu há mais de um dia](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**As senhas não estão sincronizando ou estou vendo um alerta no centro de administração de que não houve sincronização de hash de senhas recentes**
- [Implementação de sincronização de hash de senha com a sincronização do Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Estou vendo um alerta de cota de objeto excedida**
- Temos uma cota interna de objetos para ajudar a proteger o serviço. Se você tiver objetos demais em seu diretório e precisar sincronizar com o Office 365, terá que [Entrar em contato com o suporte de produtos empresariais](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar sua cota.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Preciso saber quais são os atributos sincronizados**
- É possível encontrar uma lista de todos os atributos que estão sincronizados entre o local e a nuvem [aqui](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Não consigo gerenciar ou remover os objetos que foram sincronizados na nuvem**
- Você está pronto para gerenciar objetos somente na nuvem? Ou existe um objeto que foi excluído localmente, mas está preso na nuvem? Confira [Como solucionar erros durante a sincronização](https://go.microsoft.com/fwlink/p/?linkid=842044) e este [artigo sobre suporte](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obter orientação sobre como resolver esses problemas.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Recebi uma mensagem de erro informando que minha empresa excedeu o número de objetos que podem ser sincronizados**
- Leia mais sobre o problema [aqui](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Outros recursos

- [Script para corrigir UPNs duplicados](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Como preparar um domínio não roteável (por exemplo, domínio .local) para a sincronização de diretórios](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script para contar o total de objetos sincronizados](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Solucionar problemas do AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Usar o PowerShell para corrigir os atributos DisplayName vazios para grupos habilitados para email](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Usar o PowerShell para corrigir UPN duplicado](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Usar o PowerShell para corrigir endereços de email duplicados](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Ferramentas de diagnóstico

A [ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) é usada para realizar a descoberta e a reparação de objetos de identidade e seus atributos em um ambiente do Active Directory local que está em preparação para migrar para o Office 365. A IdFix é para os administradores do Active Directory responsáveis pelo DirSync com o serviço Office 365. 

[Baixar a ferramenta IdFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) no Centro de Download da Microsoft.