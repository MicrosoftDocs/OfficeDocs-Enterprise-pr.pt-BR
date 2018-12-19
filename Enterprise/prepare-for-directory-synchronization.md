---
title: Prepare-se para provisionar usuários por meio da sincronização de diretório para o Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Descreve como preparar para provisionar usuários para o Office 365 usando a sincronização de diretórios e os benefícios de longo prazo do uso deste método.
ms.openlocfilehash: 8e84f4602b79ce321cd9a71e6c35331baf40f7f0
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371115"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Prepare-se para provisionar usuários por meio da sincronização de diretório para o Office 365

Provisionamento de usuários com a sincronização de diretório exige mais planejamento e preparação que simplesmente gerenciar sua conta do trabalho ou da escola diretamente no Office 365. As tarefas de planejamento e preparação adicionais são necessárias para garantir que o seu local Active Directory sincroniza adequadamente no Windows Azure Active Directory. Os benefícios adicionais à sua organização incluem:
  
- Reduzir os programas administrativos em sua organização
- Opcionalmente, habilitando o cenário de logon único
- Automatizar as alterações de conta no Office 365
    
Para obter mais informações sobre as vantagens do uso de sincronização de diretórios, consulte o [roteiro de sincronização de diretório]( https://go.microsoft.com/fwlink/p/?LinkId=525398) e [Noções básicas sobre Office 365 Identity e o Azure Active Directory](about-office-365-identity.md).
  
Para determinar qual cenário é a melhor para a sua organização, examine a [comparação de ferramentas de integração de diretório](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Tarefas de limpeza do diretório

Antes de começar a sincronizar seu diretório, você precisa limpar seu diretório.
  
Analise também o [atributos são sincronizados com o Windows Azure Active Directory por Connect do Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).
  
> [!IMPORTANT]
> Se você não executar a limpeza do diretório antes de sincronizar, pode haver um efeito de negativo significativo sobre o processo de implantação. Ele pode levar dias ou até mesmo semanas, para passar o ciclo de sincronização de diretórios, identificando erros e ressincronização. 
  
No seu diretório local, conclua as seguintes tarefas de limpeza:
  
1. Verifique se cada usuário ao qual serão atribuídas ofertas de serviços do Office 365 tem um endereço de email válido e exclusivo no atributo **proxyAddresses**. 
    
2. Remover valores duplicados no atributo **proxyAddresses**. 
    
3.  Se possível, certifique-se de que cada usuário ao qual será atribuído ofertas de serviço do Office 365 tem um valor válido e exclusivo para o atributo **userPrincipalName** no objeto de **usuário** do usuário. Para melhor experiência de sincronização, certifique-se de UPN Active Directory local corresponde a nuvem UPN. Se um usuário não tiver um valor para o atributo **userPrincipalName** , o objeto de **usuário** deve conter um valor válido e exclusivo para o atributo **sAMAccountName** . Remova valores duplicados no atributo **userPrincipalName** . 
    
4. Para garantir o melhor uso da lista de endereços global (GAL), verifique se as informações nos seguintes atributos estão corretas:
    
  - givenName 
  - surname
  - displayName
  - Cargo
  - Departamento
  - Escritório
  - Telefone Comercial
  - Celular
  - Número de Fax
  - Endereço
  - Cidade
  - Estado ou Província
  - CEP ou Código Postal
  - País ou Região
    
## <a name="directory-object-and-attribute-preparation"></a>Preparação de objetos e atributos de diretório

Sincronização de diretórios bem-sucedida entre seu diretório local e o Office 365 exige que seu atributos de diretório local estejam adequadamente preparados. Por exemplo, você precisará garantir que os caracteres específicos não são usados em determinados atributos que são sincronizados com o ambiente do Office 365. Caracteres inesperados não farão com que a sincronização de diretório falhar, mas podem retornar um aviso. Caracteres inválidos fará com que a sincronização de diretório falhar.
  
Sincronização de diretórios também falhará se alguns dos usuários do Active Directory possuem um ou mais atributos duplicados. Cada usuário deve ter atributos exclusivos.
  
Os atributos que você precisa para preparar são listados aqui:
  
 **Observação:** Você também pode usar a [ferramenta IdFix](install-and-run-idfix.md) para tornar esse processo muito mais fácil. 
  
- **displayName**
    
  - Se o atributo existe no objeto do usuário, ele será sincronizado com o Office 365.
  - Se esse atributo existir no objeto de usuário, deve haver um valor para ela. Ou seja, o atributo não deve estar em branco.
  - Número máximo de caracteres: 256
    
- **givenName **
    
  - Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não necessitará dele ou irá usá-lo.
  - Número máximo de caracteres: 64
    
- **email**
    
  - O valor do atributo deve ser exclusivo dentro do diretório.
    
    > [!NOTE]
    > Se houver valores duplicados, o primeiro usuário com o valor é sincronizado. Usuários subsequentes não aparecerá no Office 365. Você deve modificar o valor no Office 365 ou modificar ambos dos valores no diretório local na ordem de ambos os usuários apareça no Office 365. 
  
- **mailNickname** (alias do Exchange) 
    
  - O valor do atributo não pode começar com um ponto (.).
  - O valor do atributo deve ser exclusivo dentro do diretório.
    
- **proxyAddresses **
    
  - Atributo de valores múltiplos
  - A quantidade máxima de caracteres por valor: 256
  - O valor do atributo não deve conter um espaço.
  - O valor do atributo deve ser exclusivo dentro do diretório.
  - Caracteres inválidos: \< \> (); , [ ] "
    
    Observe que os caracteres inválidos se aplicam aos caracteres seguindo o delimitador do tipo e ":", de forma que SMTP:User@contso.com é permitida, mas SMTP:user:M@contoso.com não está.
    
    > [!IMPORTANT]
    > Todos os endereços de protocolo de transporte de email simples (SMTP) devem ser compatíveis com os padrões de mensagens de email. Se os endereços duplicados ou indesejados existirem, consulte o tópico de Ajuda, [Remover proxy duplicado e indesejado endereços no Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Número máximo de caracteres: 20
  - O valor do atributo deve ser exclusivo dentro do diretório.
  - Caracteres inválidos: [\ "|, /: \< \> + =;? \* ]
  - Se um usuário tiver um atributo **sAMAccountName** inválido, mas tiver um atributo **userPrincipalName** válido, a conta de usuário será criada no Office 365. 
  - Se **sAMAccountName** e **userPrincipalName** forem inválidos, o atributo de **userPrincipalName** local do Active Directory deve ser atualizado. 
    
- **sn** (sobrenome) 
    
  - Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não necessitará dele ou irá usá-lo.
    
- **targetAddress**
    
    É obrigatório se o atributo **targetAddress** (por exemplo, SMTP:tom@contoso.com) que é preenchido para o usuário deverá aparecer no Office 365 GAL. Cenários de migração de mensagens de terceiros, isso exigiria a extensão de esquema do Office 365 para o diretório local. A extensão de esquema do Office 365 também seria adicionar outros atributos úteis para gerenciar o Office 365 objetos que são preenchidos usando uma ferramenta de sincronização de diretórios do diretório local. Por exemplo, o atributo **msExchHideFromAddressLists** para gerenciar caixas de correio ocultas ou grupos de distribuição seria adicionado. 
   
  - Número máximo de caracteres: 256
  - O valor do atributo não deve conter um espaço.
  - O valor do atributo deve ser exclusivo dentro do diretório.
  - Caracteres inválidos: \ \< \> (); , [ ] "
  - Todos os endereços no Protocolo SMTP devem estar em conformidade com os padrões de emails.
    
- **userPrincipalName**
    
  - O atributo **userPrincipalName** deve estar no estilo Internet entrar formato onde o nome de usuário é seguido do sinal de arroba (@) e um nome de domínio: por exemplo, user@contoso.com. Todos os endereços de protocolo de transporte de email simples (SMTP) devem ser compatíveis com os padrões de mensagens de email.
  - A quantidade máxima de caracteres para o atributo **userPrincipalName** é 113. Permite-se uma quantidade específica de caracteres antes e depois do sinal (@), como a seguir: 
  - Número máximo de caracteres para o nome de usuário antes do sinal de arroba (@): 64
  - Número máximo de caracteres para o nome de domínio após o sinal de arroba (@): 48
  - Caracteres inválidos: \ % &amp; \* + / =? { } | \< \> ( ) ; : , [ ] "
  - Tem trema também é um caractere inválido.
  - O caractere @ é necessário em cada valor **userPrincipalName** . 
  - O caractere @ não pode ser o primeiro caractere em cada valor **userPrincipalName**. 
  - O nome de usuário não pode terminar com um ponto (.), um e comercial (&amp;), um espaço ou um sinal de arroba (@).
  - O nome de usuário não pode conter espaços.
  - Domínios roteáveis devem ser usados; Por exemplo, domínios locais ou internos não podem ser usados.
  - Unicode é convertido para caracteres sublinhados.
  - **userPrincipalName** não pode conter valores duplicados no diretório. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Preparar o atributo userPrincipalName

Active Directory é projetado para permitir que os usuários finais na sua organização para entrar no seu diretório usando o **sAMAccountName** ou **userPrincipalName**. Da mesma forma, os usuários finais podem entrar no Office 365 usando o nome principal do usuário (UPN) dos seus trabalhos ou escola conta. Sincronização de diretórios tenta criar novos usuários no Windows Azure Active Directory usando o UPN mesmo que esteja no seu diretório local. O UPN é formatado como um endereço de email. 

No Office 365, o UPN é o atributo padrão que é usado para gerar o endereço de email. É fácil obter **userPrincipalName** (no local e no Windows Azure Active Directory) e o endereço de email primário no **proxyAddresses** definidos como valores diferentes. Quando eles estiverem definidos como valores diferentes, pode haver confusão para os administradores e usuários finais. 
  
É melhor alinhar esses atributos para reduzir a confusão. Para atender a requisitos de single sign-on com os serviços de Federação do Active Directory (AD FS) 2.0, você precisará garantir que o UPNs no Windows Azure Active Directory e seu local Active Directory correspondem e estiver usando um namespace de domínio válidos.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Adicionar um sufixo UPN alternativo ao AD DS

Você pode precisar adicionar um sufixo UPN alternativo para associar as credenciais do usuário corporativo ao ambiente do Office 365. Um sufixo UPN é a parte de um UPN à direita do caractere @. UPNs que são usados para o serviço single sign-on podem conter letras, números, períodos, traços e sublinhados, mas não há outros tipos de caracteres.
  
Para obter mais informações sobre como adicionar um sufixo UPN alternativo ao Active Directory, consulte [Prepare para sincronização de diretórios]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Corresponder o UPN local com o Office 365 UPN

Se você já tiver configurado a sincronização de diretórios, UPN do usuário para o Office 365 pode não corresponder o UPN do local do usuário que está definido no seu serviço de diretório local. Isso pode ocorrer quando um usuário foi atribuído uma licença antes do domínio foi verificado. Para corrigir esse problema, use o [PowerShell para corrigir o UPN duplicado](https://go.microsoft.com/fwlink/p/?LinkId=396730) para atualizar o UPN do usuário para garantir que o UPN do Office 365 coincide com o nome de usuário corporativo e o domínio. Se você estiver atualizando o UPN no serviço de diretório local e gostaria que ele para sincronizar com a identidade do Windows Azure Active Directory, você precisa remover a licença do usuário no Office 365 antes de fazer o alterações no local. 
  
Consulte também [como preparar um domínio não roteáveis (por exemplo, o domínio. local) para sincronização de diretórios](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Ferramentas de integração de diretório

Sincronização de diretórios é a sincronização de objetos de diretório (usuários, grupos e contatos) do seu ambiente do Active Directory local a infraestrutura de diretório do Office 365, o Azure Active Directory. Consulte [As ferramentas de integração de diretório](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obter uma lista das ferramentas disponíveis e suas funcionalidades. A ferramenta recomendada é o [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Para obter mais informações sobre como conectar do Azure Active Directory, consulte [integrando suas identidades no local com o Windows Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Quando as contas de usuário são sincronizadas com o diretório do Office 365 pela primeira vez, eles são marcados como não ativado. Não podem enviar ou receber emails, e não consomem licenças de assinatura. Quando você estiver pronto para atribuir assinaturas do Office 365 para usuários específicos, você deve selecionar e ativá-los por [Atribuir licenças aos usuários no Office 365 para empresas](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
Você também pode usar o [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) para atribuir licenças. Consulte [como usar o PowerShell para atribuir licenças automaticamente para os usuários do seu Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) para uma solução automatizada.