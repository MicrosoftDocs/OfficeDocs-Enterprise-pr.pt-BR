---
title: Preparar-se para provisionar usuários por meio da sincronização de diretórios para o Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Descreve como se preparar para provisionar usuários para o Office 365 usando a sincronização de diretórios e os benefícios de longo prazo de usar esse método.
ms.openlocfilehash: 0b2fe552911797337541bd25f0efcb81eab303bf
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071027"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Preparar-se para provisionar usuários por meio da sincronização de diretórios para o Office 365

O provisionamento de usuários com a sincronização de diretórios requer mais planejamento e preparação do que simplesmente gerenciar sua conta corporativa ou de estudante diretamente no Office 365. As tarefas adicionais de planejamento e preparação são necessárias para garantir que o Active Directory local seja sincronizado adequadamente com o Azure Active Directory. Os benefícios adicionados à sua organização incluem:
  
- Reduzindo os programas administrativos em sua organização
- Opcionalmente, habilitando o cenário de logon único
- Automatizar alterações de contas no Office 365
    
Para obter mais informações sobre as vantagens de usar a sincronização de diretório, consulte [mapa de sincronização de diretório]( https://go.microsoft.com/fwlink/p/?LinkId=525398) e [noções básicas sobre a identidade do Office 365 e o Azure Active Directory](about-office-365-identity.md).
  
Para determinar qual cenário é o melhor para a sua organização, revise a [comparação de ferramentas de integração de diretórios](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Tarefas de limpeza de diretório

Antes de começar a sincronizar seu diretório, você precisa limpar o diretório.
  
Revise também os [atributos sincronizados com o Azure Active Directory pelo Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).
  
> [!IMPORTANT]
> Se você não executar a limpeza de diretório antes de sincronizar, pode haver um efeito negativo significativo no processo de implantação. Pode levar dias ou até mesmo semanas para passar pelo ciclo de sincronização de diretórios, identificar erros e ressincronizar. 
  
No diretório local, conclua as seguintes tarefas de limpeza:
  
1. Certifique-se de que cada usuário ao qual serão atribuídas ofertas de serviço do Office 365 tem um endereço de email válido e exclusivo no atributo **proxyAddresses** . 
    
2. Remova os valores duplicados no atributo **proxyAddresses** . 
    
3.  Se possível, certifique-se de que cada usuário ao qual serão atribuídas ofertas de serviço do Office 365 tem um valor válido e exclusivo para o atributo **userPrincipalName** no objeto **User** do usuário. Para obter a melhor experiência de sincronização, verifique se o UPN do Active Directory local corresponde ao UPN da nuvem. Se um usuário não tiver um valor para o atributo **userPrincipalName** , o objeto de **usuário** deverá conter um valor válido e exclusivo para o atributo **sAMAccountName** . Remova os valores duplicados no atributo **userPrincipalName** . 
    
4. Para o uso ideal da GAL (lista de endereços global), certifique-se de que as informações nos seguintes atributos estão corretas:
    
  - givenName
  - surname
  - displayName
  - Cargo
  - Departamento
  - Escritório
  - Telefone comercial
  - Telefone celular
  - Número do fax
  - Endereço
  - Cidade
  - Estado
  - CEP
  - País
    
## <a name="directory-object-and-attribute-preparation"></a>Preparação de objeto e atributo de diretório

A sincronização de diretório com êxito entre o diretório local e o Office 365 requer que seus atributos de diretório local sejam preparados corretamente. Por exemplo, você precisa garantir que caracteres específicos não sejam usados em determinados atributos que são sincronizados com o ambiente do Office 365. Caracteres inesperados não causam a sincronização de diretório, mas podem retornar um aviso. Caracteres inválidos causarão falha na sincronização do diretório.
  
A sincronização de diretórios também falhará se alguns dos seus usuários do Active Directory tiverem um ou mais atributos duplicados. Cada usuário deve ter atributos exclusivos.
  
Os atributos que você precisa preparar estão listados aqui:
  
 **Observação:** Você também pode usar a [ferramenta IdFix](install-and-run-idfix.md) para tornar esse processo muito mais fácil. 
  
- **displayName**
    
  - Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365.
  - Se esse atributo existir no objeto user, deverá haver um valor para ele. Ou seja, o atributo não deve estar em branco.
  - Número máximo de caracteres: 256
    
- **givenName**
    
  - Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não o exigirá ou o usará.
  - Número máximo de caracteres: 64
    
- **mala**
    
  - O valor do atributo deve ser exclusivo no diretório.
    
    > [!NOTE]
    > Se houver valores duplicados, o primeiro usuário com o valor será sincronizado. Os usuários subsequentes não aparecerão no Office 365. Você deve modificar o valor no Office 365 ou modificar os dois valores no diretório local para que ambos os usuários apareçam no Office 365. 
  
- **mailNickname** (Alias do Exchange) 
    
  - O valor do atributo não pode começar com um ponto (.).
  - O valor do atributo deve ser exclusivo no diretório.
    
- **proxyAddresses**
    
  - Atributo de vários valores
  - Número máximo de caracteres por valor: 256
  - O valor do atributo não deve conter um espaço.
  - O valor do atributo deve ser exclusivo no diretório.
  - Caracteres inválidos: \< \> (); , [ ] "
    
    Observe que os caracteres inválidos se aplicam aos caracteres após o delimitador de tipo e ":", de modo que SMTP:User@contso.com seja permitido, mas SMTP:user:M@contoso.com não.
    
    > [!IMPORTANT]
    > Todos os endereços SMTP (Simple Mail Transport Protocol) devem estar em conformidade com os padrões de mensagens de email. Se houver endereços indesejados ou duplicados, consulte o tópico de ajuda [removendo endereços de proxy duplicados e indesejados no Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Número máximo de caracteres: 20
  - O valor do atributo deve ser exclusivo no diretório.
  - Caracteres inválidos: [\ "|, \< \> /: + =;? \* ]
  - Se um usuário tiver um atributo **sAMAccountName** inválido, mas tiver um atributo **userPrincipalName** válido, a conta do usuário será criada no Office 365. 
  - Se **sAMAccountName** e **userPrincipalName** forem inválidos, o atributo **userPrincipalName** do Active Directory local deverá ser atualizado. 
    
- **SN** sobrenome 
    
  - Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não o exigirá ou o usará.
    
- **targetAddress**
    
    É necessário que o atributo **targetAddress** (por exemplo, SMTP:Tom@contoso.com) preenchido para o usuário deve aparecer na GAL do Office 365. Em cenários de migração de mensagens de terceiros, isso exigiria a extensão de esquema do Office 365 para o diretório local. A extensão de esquema do Office 365 também adicionaria outros atributos úteis para gerenciar objetos do Office 365 que são preenchidos usando uma ferramenta de sincronização de diretório do diretório local. Por exemplo, o atributo **msExchHideFromAddressLists** para gerenciar caixas de correio ou grupos de distribuição ocultos seria adicionado. 
   
  - Número máximo de caracteres: 256
  - O valor do atributo não deve conter um espaço.
  - O valor do atributo deve ser exclusivo no diretório.
  - Caracteres inválidos \< \> : \ (); , [ ] "
  - Todos os endereços SMTP (Simple Mail Transport Protocol) devem estar em conformidade com os padrões de mensagens de email.
    
- **userPrincipalName**
    
  - O atributo **userPrincipalName** deve estar no formato de entrada no estilo da Internet, onde o nome do usuário é seguido pelo sinal de arroba (@) e um nome de domínio: por exemplo, User@contoso.com. Todos os endereços SMTP (Simple Mail Transport Protocol) devem estar em conformidade com os padrões de mensagens de email.
  - O número máximo de caracteres para o atributo **userPrincipalName** é 113. Um número específico de caracteres é permitido antes e depois do sinal de arroba (@), da seguinte maneira: 
  - Número máximo de caracteres para o nome de usuário que está na frente do sinal de arroba (@): 64
  - Número máximo de caracteres para o nome de domínio após o sinal de arroba (@): 48
  - Caracteres inválidos: &amp; \* \% +/=? { } | \< \> ( ) ; : , [ ] "
  - Um trema também é um caractere inválido.
  - O caractere @ é necessário em cada valor **userPrincipalName** . 
  - O caractere @ não pode ser o primeiro caractere em cada valor **userPrincipalName** . 
  - O nome de usuário não pode terminar com um ponto (.), um&amp;e comercial (), um espaço ou um sinal de arroba (@).
  - O nome de usuário não pode conter espaços.
  - Domínios roteáveis devem ser usados; por exemplo, domínios locais ou internos não podem ser usados.
  - Unicode é convertido em caracteres de sublinhado.
  - **userPrincipalName** não pode conter valores duplicados no diretório. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Preparar o atributo userPrincipalName

O Active Directory é projetado para permitir que os usuários finais em sua organização entrem em seu diretório usando **sAMAccountName** ou **userPrincipalName**. Da mesma forma, os usuários finais podem entrar no Office 365 usando o nome principal do usuário (UPN) de sua conta corporativa ou de estudante. A sincronização de diretório tenta criar novos usuários no Active Directory do Azure usando o mesmo UPN que está no seu diretório local. O UPN é formatado como um endereço de email. 

No Office 365, o UPN é o atributo padrão usado para gerar o endereço de email. É fácil obter **userPrincipalName** (no local e no Azure Active Directory) e o endereço de email principal no **proxyAddresses** definido como valores diferentes. Quando estão definidas como valores diferentes, pode haver confusão para administradores e usuários finais. 
  
É melhor alinhar esses atributos para reduzir a confusão. Para atender aos requisitos de logon único com os serviços de Federação do Active Directory (AD FS) 2,0, você precisa garantir que os UPNs no Azure Active Directory e sua correspondência do Active Directory local e estejam usando um namespace de domínio válido.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Adicionar um sufixo UPN alternativo ao AD DS

Talvez seja necessário adicionar um sufixo UPN alternativo para associar as credenciais corporativas do usuário ao ambiente do Office 365. Um sufixo UPN é a parte do UPN à direita do caractere @. UPNs usados para logon único podem conter letras, números, pontos, traços e sublinhados, mas nenhum outro tipo de caracteres.
  
Para obter mais informações sobre como adicionar um sufixo UPN alternativo ao Active Directory, consulte [preparar para a sincronização de diretórios]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Corresponder ao UPN local com o UPN do Office 365

Se você já configurou a sincronização de diretórios, o UPN do usuário para Office 365 pode não corresponder ao UPN local do usuário que está definido no serviço de diretório local. Isso pode ocorrer quando uma licença foi atribuída ao usuário antes da verificação do domínio. Para corrigir isso, use o [PowerShell para corrigir](https://go.microsoft.com/fwlink/p/?LinkId=396730) o UPN duplicado para atualizar o UPN do usuário para garantir que o UPN do Office 365 corresponda ao nome de usuário e ao domínio da empresa. Se você estiver atualizando o UPN no serviço de diretório local e quiser que ele seja sincronizado com a identidade do Azure Active Directory, será necessário remover a licença do usuário no Office 365 antes de realizar as alterações no local. 
  
Consulte também [como preparar um domínio não roteável (como o domínio. local) para a sincronização de diretórios](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Ferramentas de integração de diretórios

A sincronização de diretórios é a sincronização de objetos de diretório (usuários, grupos e contatos) do seu ambiente do Active Directory local para a infraestrutura de diretório do Office 365, Azure Active Directory. Consulte [ferramentas de integração de diretórios](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obter uma lista das ferramentas disponíveis e sua funcionalidade. A ferramenta recomendada é [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Para obter mais informações sobre o Azure Active Directory Connect, confira [integração de suas identidades locais com o Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Quando as contas de usuário são sincronizadas com o diretório do Office 365 pela primeira vez, elas são marcadas como não ativadas. Eles não podem enviar nem receber emails e não consomem licenças de assinatura. Quando estiver pronto para atribuir assinaturas do Office 365 a usuários específicos, você deverá selecionar e ativá-las atribuindo [licenças aos usuários no Office 365 para empresas](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
Você também pode usar o [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) para atribuir licenças. Veja [como usar o PowerShell para atribuir automaticamente licenças aos usuários do Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) para uma solução automatizada.