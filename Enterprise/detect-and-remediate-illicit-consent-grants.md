---
title: Detectar e remediar concede consentimento ilícito no Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 4/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: Saiba como reconhecer e remediar consentimento ilícito concede ataque no Office 365.
ms.openlocfilehash: f6576fccd7cac49dbbf2e9ea359e08257ddc42d0
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-illicit-consent-grants-in-office-365"></a>Detectar e remediar concede consentimento ilícito no Office 365

**Resumo**  Saiba como reconhecer e remediar consentimento ilícito concede ataque no Office 365.

## <a name="what-is-the-illicit-consent-grant-attack-in-office-365"></a>Qual é o ataque de grant consentimento ilícito no Office 365?
Em um consentimento ilícito conceda ataque, que o invasor cria um aplicativo registrado Azure que solicita acesso a dados como informações de contato, email, ou documentos. O invasor truques, em seguida, um usuário final em concedendo consentimento desse aplicativo para acessar seus dados por meio de um ataque de phishing ou injeção de código ilícito em um site confiável. Depois que o aplicativo ilícito recebeu consentimento, ele tem nível de conta de acesso aos dados sem a necessidade de uma conta organizacional. Etapas de correção normal, como redefinir senhas de contas violadas ou que requerem autenticação multifator (MFA) nas contas, não são eficazes contra esse tipo de ataque, desde que essas são aplicativos de terceiros e são externas à organização. Esses ataques aproveitam um modelo de interação que partem do princípio a entidade que está chamando a informação é automação e não uma pessoa.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-office-365"></a>Qual um consentimento ilícito grant ataque a aparência no Office 365?
Você precisa para o Office 365 de **log de auditoria** para localizar sinais, também chamados de indicadores de comprometimento (IOC) desse ataque de pesquisa. Para organizações com vários aplicativos Azure registrado e uma grande base de usuários, a prática recomendada é examinar seu consentimento de organizações concede ao semanalmente.
### <a name="steps-for-finding-signs-of-this-attack"></a>Etapas para localizar os sinais desse ataque
1. Abra o **Centro de conformidade e segurança** no seu locatário do Office 365.
2. Navegue até o nó de **pesquisa & investigação** e selecione pesquisa de **log de auditoria** .
3. Criar uma pesquisa (todas as atividades e todos os usuários) e filtrar os resultados consentimento para o aplicativo e adicione OAuth2PermissionGrant.
4. Examine a propriedades estendidas e a seleção para ver se IsAdminContent for definido como True.


Se esse valor for true, indica que alguém com acesso de Administrador Global pode ter concedido amplo acesso aos dados. Se isso for inesperado, siga as etapas para [Confirmar um ataque](detect-and-remediate-illicit-consent-grants.md#confirmattack).

<a name="confirmattack"> </a>
## <a name="how-to-confirm-an-attack"></a>Como confirmar um ataque
Se você tiver um ou mais instâncias dos IOCs listadas acima, você precisará fazer mais investigação positiva, confirme que o ataque ocorreu. Você pode usar qualquer um desses três métodos para confirmar o ataque.
- Inventário de aplicativos e suas permissões usando o portal do Azure Active Directory. Esse método é completo, mas só é possível verificar um usuário cada vez que pode ser muito demorado se você tiver muitos usuários para verificar.
- Inventário de aplicativos e suas permissões usando o PowerShell. Este é o método mais rápido e mais completo, com o mínimo de sobrecarga.
- Ter seus usuários individualmente, verifique seus aplicativos e as permissões e relatar os resultados de volta para os administradores para remediação.

## <a name="inventory-apps-with-access-in-your-organization"></a>Inventário de aplicativos com o access em sua organização
Você pode fazer isso para os usuários com o Portal do Azure Active Directory ou PowerShell ou que os usuários individualmente enumerar seu acesso ao aplicativo.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Etapas para usar o Portal do Windows Azure Active Directory
Você pode pesquisar os aplicativos aos quais a qualquer usuário individual concedeu permissões usando o [Portal do Azure Active Directory](https://portal.azure.com/). 
1. Inscreva-se portal do Windows Azure com direitos administrativos.
2. Selecione o blade do Azure Active Directory.
3. Selecione **os usuários**.
4. Selecione o usuário que você deseja analisar.
5. Selecione os **aplicativos**.

Isso mostrará os aplicativos que estão atribuídos ao usuário e quais permissões tem os applcations.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>Etapas para ter que seus usuários enumerar seu acesso de aplicativo
Que os usuários acesse https://myapps.microsoft.com e revise seu próprios acesso ao aplicativo lá. Eles devem possam ver todos os aplicativos com o access, exibir detalhes sobre cada um deles (incluindo o escopo do access) e poderá revogar privilégios aos aplicativos suspeitos ou ilícitas.

### <a name="steps-for-doing-this-with-powershell"></a>Etapas para fazer isso com o PowerShell
A maneira mais simples de verificar o ataque ilícito Grant concorda é executar [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09), que será despejo todas as concessões de consentimento do OAuth e permissões do aplicativo para todos os usuários em sua locação em um único arquivo. csv. 

#### <a name="pre-requisites"></a>Pré-requisitos
- Biblioteca do Azure AD PowerShell instalada.
- Direitos de administrador global no locatário do que o script será executado contra.
- Administrador local no computador do qual será executado os scripts.

> [!IMPORTANT]
> É altamente recomendável que você exija a autenticação multifator em sua conta administrativa.  Esse script dá suporte à autenticação de MFA.

1. Inscreva-se ao computador que executará o script de com direitos de administrador local.
2. Faça download ou copie o script de [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) da GitHub para uma pasta da qual você executará o scruipt.  Esse será a mesma pasta que será gravado no arquivo de saída "permissions.csv".
3. Abra uma instância do PowerShell como administrador e abra até a pasta que você salvou o script.
4. Conectar ao seu diretório usando o cmdlet [Connect-AzureAD](https://docs.microsoft.com/en-us/powershell/module/azuread/connect-azuread?view=azureadps-2.0) .
5. Execute esta linha de comando do PowerShell da seguinte maneira:`.Get-AzureASPSPermissions.ps1 | Export-csv -path "Permissions.csv" -NoTypeInformation`

O script produz um arquivo chamado Permissions.csv. Siga estas etapas para procurar por aplicativo ilícito permissão concede: 
1. Pesquise o valor "AllPrinciples" na coluna ConsentType (coluna G). A permissão de AllPrincipals permite que o aplicativo cliente para acessar o conteúdo de todos os participantes em aluguel. Aplicativos do Office 365 nativos precisam essa permissão funcione corretamente. Todos os aplicativos não-Microsoft com esta permissão devem ser revisados cuidadosamente.
2.  Em revisão de coluna (coluna F) a permissão das permissões que cada delegadas aplicativo tem ao conteúdo. Procure a permissão "Ler" e "Gravar" ou "*. Todos os"permissão e revisar que essas cuidadosamente porque eles podem não ser apropriadas.
3.  Revise os usuários específicos que tenham consente concedidas. Se o perfil de alta ou usuários de alto impacto tiverem inadequado consente concedidas, você deve investigar melhor.
4.  Na coluna ClientDisplayName (coluna C) procure aplicativos que parecem suspeitos. Aplicativos com a palavra com grafia nomes, nomes de superusuário simples ou hacker-nomes devem ser revisados cuidadosamente.

## <a name="determine-the-scope-of-the-attack"></a>Determinar o escopo do ataque
Depois de concluir o inventário de acesso ao aplicativo, revise o Office 365 de **log de auditoria** para determinar o escopo completo da violação.  Pesquisa nos usuários afetados, os quadros de tempo que o aplicativo ilícito tinha acesso à sua organização e as permissões que tinha o aplicativo. Você pode pesquisar o **log de auditoria** no [Centro de conformidade e segurança do Office 365](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c). 

> [!IMPORTANT]
> [Auditoria de caixa de correio](https://support.office.com/en-us/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918) e [auditoria da atividade para administradores e usuários](https://support.office.com/en-us/article/turn-office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014) devem ter sido habilitada antes do ataque de obter essas informações.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant--attack"></a>Como parar e remediar um ataque de grant consentimento ilícito
Depois que você identificou um aplicativo com permissões ilícitas, você terá várias maneiras para remover esse acesso.
- Você pode revogar permissão do aplicativo no Azure Active Directory Portal por:
    - Navegue até o usuário afetado em blade do **Usuário do Windows Azure Active Directory** .
    - Selecione os **aplicativos**.
    - Selecione o aplicativo ilícito.
    - Clique em **Remover** na análise detalhada para baixo.
- Você pode revogar a concessão de consentimento do OAuth com o PowerShell seguindo as etapas descritas em [Remove-AzureADOAuth2PermissionGrant](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant?view=azureadps-2.0).
- Você pode revogar a atribuição de função do aplicativo de serviço com o PowerShell seguindo as etapas descritas em [Remove-AzureADServiceAppRoleAssignment](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment?view=azureadps-2.0).
- Você também pode desativar entrar para ao mesmo tempo conta afetado, que por sua vez desabilitará o aplicativo no acesso a dados dessa conta. Obviamente, isso não é ideal para a produtividade do usuário final, mas se você estiver trabalhando para limitar o impacto rapidamente, pode ser uma correção de curto prazo viável.
- Você pode desativar aplicativos integrados para sua locação. Isso é uma etapa drástica que desabilita a capacidade dos usuários finais conceder consentimento em uma base de todo o inquilino. Isso impede que os usuários inadvertidamente conceder acesso a um aplicativo mal-intencionado. Isso não é altamente recomendável conforme ele está seriamente prejudica a capacidade dos usuários sejam produtivos com os aplicativos de terceiros.  Você pode fazer isso seguindo as etapas no [Desativando integrada Apps ativada ou desativada](https://support.office.com/en-us/article/Turning-Integrated-Apps-on-or-off-7e453a40-66df-44ab-92a1-96786cb7fb34).

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>Proteger o Office 365 como um cybersecurity pro
Sua assinatura do Office 365 é fornecido com um conjunto avançado de recursos de segurança que você pode usar para proteger seus dados e seus usuários.  Use o [mapa de segurança do Office 365: principais prioridades para os primeiros 30 dias, 90 dias e além](https://support.office.com/en-us/article/office-365-security-roadmap-top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) para implementar as práticas recomendadas para proteger seu locatário do Office 365 do Microsoft.
- Tarefas para realizar nos primeiros 30 dias.  Elas têm efeito imediato e são baixo impacto para seus usuários.
- Tarefas para realizar em 90 dias. Essas demoram um pouco mais para planejar e implementar mas melhorar consideravelmente sua situação de segurança.
- Além de 90 dias. Esses aperfeiçoamentos se baseiam em seu primeiro trabalho de 90 dias.

## <a name="see-also"></a>Consulte também:
- [Aplicativo inesperado da minha lista de aplicativos](https://docs.microsoft.com/en-us/azure/active-directory/application-access-unexpected-application) orienta os administradores em várias ações que eles talvez queira fazer depois percebendo há aplicativos inesperados com acesso aos dados.
- [Integração de aplicativos com o Windows Azure Active Directory]  (https://docs.microsoft.com/en-us/azure/active-directory/active-directory-apps-permissions-consent) é uma visão geral de alto nível de consentimento e permissões.  Preste atenção para a seção de [Visão geral do framework consentimento](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#overview-of-the-consent-framework) .
- [Problemas de desenvolvimento meu aplicativo](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-application-dev-development-content-map) fornece links para vários artigos relacionados de consentimento.
- [Aplicativo e objetos de entidade de serviço no Windows Azure Active Directory (AD Azure)](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects) fornece uma visão geral dos objetos Application e serviço principais que são centrais para o modelo de aplicativo.
- [Gerenciar o acesso aos aplicativos](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-managing-access-to-apps) é uma visão geral dos recursos que os administradores devem gerenciar o acesso de usuário aos aplicativos.