---
title: Proteger as contas de administradores globais do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Protege o acesso de administrador global à sua assinatura do Office 365 com estas três etapas.
ms.openlocfilehash: 7260e903ea007735c87ab8aa826e3b97e7bd28c1
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539390"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Proteger as contas de administradores globais do Office 365

 **Resumo:** Protege sua assinatura do Office 365 contra ataques com base no comprometimento de uma conta de administrador global. 
  
As violações de segurança de uma assinatura do Office 365, incluindo a coleta de informações e ataques de phishing, normalmente são feitas por comprometer as credenciais de uma conta de administrador global do Office 365. Segurança na nuvem é uma parceria entre você e a Microsoft:
  
- Serviços de nuvem da Microsoft são compilados em uma base de confiabilidade e segurança. A Microsoft fornece a controles de segurança e recursos para ajudá-lo a proteger os dados e aplicativos.
    
- Você é proprietário seus dados e identidades e a responsabilidade de proteção-los, a segurança dos seus recursos no local e a segurança dos componentes de nuvem, que você controlar.
    
A Microsoft fornece recursos para ajudar a proteger a sua organização, mas são efetivas apenas se você usá-los. Se você não usá-los, você pode estar vulnerável a ataques. Para proteger suas contas de administrador global, a Microsoft está aqui para ajudá-lo com instruções detalhadas para:
  
1. Criar contas de administrador global do Office 365 dedicadas e usá-los somente quando necessário.
    
2. Configurar a autenticação multifator para contas de administrador global do Office 365 dedicadas e usar o formulário mais forte de autenticação secundário.
    
3. Habilitar e configurar a segurança de aplicativo do Office 365 nuvem para monitorar a atividade da conta de administrador global suspeitas de.
    
> [!NOTE]
> Embora este artigo concentra-se em contas de administrador global, você também deve considerar se adicionais contas com amplas permissões para acessar os dados na sua assinatura, como administrador de descoberta eletrônica ou segurança ou conformidade contas de administrador, devem ser protegidos da mesma maneira. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Etapa 1. Criar contas de administrador global do Office 365 dedicadas e usá-los somente quando necessário

Há relativamente poucas tarefas administrativas, como atribuindo funções a contas de usuário, que exigem privilégios de administrador global. Portanto, em vez de usar contas de usuário cotidianos que tiverem sido atribuídas a função de administrador global, siga estas etapas:
  
1. Determine o conjunto de contas de usuário que tiverem sido atribuídas a função de administrador global. Você pode fazer isso com este comando no prompt de comando do Microsoft Azure Active Directory módulo para Windows PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Inscreva-se em sua assinatura do Office 365 com uma conta de usuário que tenha sido atribuída a função de administrador global.
    
3. Criar pelo menos um e até um máximo de cinco dedicado contas de usuário de administrador global. **Uso longo. caracteres de senhas fortes, pelo menos, 12** Consulte [criar uma senha forte](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obter mais informações. Armazene as senhas para as novas contas em um local seguro. 
    
4. Atribua a função de administrador global a cada uma das contas de usuário de administrador global novo dedicado.
    
5. Sair do Office 365.
    
6. Entrar com uma das novas contas de usuário do administrador global dedicado.
    
7. Para cada conta de usuário existente que tinha sido atribuída a função de administrador global da etapa 1:
    
  - Remova a função de administrador global.
    
  - Atribua funções de administrador para a conta que são apropriados para a função de trabalho e a responsabilidade desse usuário. Para obter mais informações sobre diversas funções de administrador no Office 365, consulte [funções de administrador do Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. Sair do Office 365.
    
O resultado deve ser:
  
- As contas de usuário somente na sua assinatura que possuem a função de administrador global são o novo conjunto de contas de administrador global dedicado. Verificar isso com o seguinte comando do PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- Todas as outras contas de usuários comuns que gerenciam sua assinatura têm funções de administrador atribuídas que estão associadas às responsabilidades de trabalho deles.
    
A partir neste momento em diante, você entrar com as contas de administrador global dedicado somente para tarefas que exigem privilégios de administrador global. Todos os outro administração do Office 365 devem ser feito pela atribuição de outras funções de administração para contas de usuário.
  
> [!NOTE]
> Sim, isso requer etapas adicionais para desconectá-como sua conta de usuário cotidianos e entrar com uma conta de administrador global dedicado. Mas isso só precisa ser feito ocasionalmente para operações de administrador global. Considere que recuperando sua assinatura do Office 365 após uma violação da conta de administrador global requer etapas muito mais. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Etapa 2. Configurar a autenticação multifator para contas de administrador global do Office 365 dedicadas e usar o formulário mais forte de autenticação secundário

A autenticação multifator (MFA) para suas contas de administrador global requer informações adicionais além do nome da conta e senha. O Office 365 oferece suporte a esses métodos de verificação:
  
- Uma chamada telefônica
    
- Uma senha gerada aleatoriamente
    
- Um cartão inteligente (físico ou virtual)
    
- Um dispositivo biométrico
    
Se você estiver uma pequena empresa que está usando contas de usuário armazenadas somente na nuvem (o modelo de identidade de nuvem), execute estas etapas para configurar MFA usando uma chamada telefônica ou um código de verificação de mensagem de texto enviada para um telefone inteligente:
  
1. [Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Set up 2-etapa de verificação para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada dedicada a conta de administrador global para chamada telefônica ou mensagem de texto como o método de verificação. 
    
Se você for uma grande organização que está usando um modelo de identidade do Office 365 híbrido, você tem mais opções de verificação. Se você tiver a infra-estrutura de segurança já em vigor para um método de autenticação secundária mais seguro, execute estas etapas:
  
1. [Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Set up 2-etapa de verificação para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada dedicada a conta de administrador global para o método de verificação apropriada. 
    
Se a infraestrutura de segurança para o método de verificação mais forte desejado não estiver instalado e funcionando para Office 365 MFA, é altamente recomendável que você configure contas de administrador global dedicado com MFA usando uma chamada telefônica ou uma mensagem de texto código de verificação enviado a um telefone inteligente para suas contas de administrador global como uma medida de segurança provisório. Não deixe suas contas de administrador global dedicado sem a proteção adicional fornecida pelo MFA.
  
Para saber mais, consulte as informações sobre como [planejar a autenticação multifator para implantações do Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).
  
Para se conectar aos serviços do Office 365 com MFA e PowerShell, consulte [Este artigo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Etapa 3. Monitor das atividades da conta de administrador global suspeitas

Segurança de aplicativo de nuvem do Office 365 permite que você crie políticas para notificá-lo de comportamento suspeito em sua assinatura. Segurança de aplicativo de nuvem é incorporada ao Office 365 E5, mas também está disponível como um serviço separado. Por exemplo, se você não tiver E5 do Office 365, você pode adquirir licenças individuais de segurança de aplicativo de nuvem para as contas de usuário que são atribuídas a administrador global, os administradores de segurança e funções de administrador de conformidade.
  
Se você tiver segurança de aplicativo de nuvem em sua assinatura do Office 365, execute estas etapas:
  
1. Entrar no portal do Office 365 com uma conta que é atribuída a função de administrador de segurança ou administrador de conformidade.
    
2. [Ative a segurança de aplicativo do Office 365 nuvem](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Examine suas [políticas de detecção de anomalias na segurança de aplicativo de nuvem do Office 365](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) para notificá-lo por email dos padrões anômalos das atividades administrativas privilegiada. 
    
Para adicionar uma conta de usuário à função de administrador de segurança, [Conecte-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) com uma conta de administrador global dedicado e MFA, preencha o nome principal do usuário da conta de usuário e, em seguida, execute estes comandos: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Para adicionar uma conta de usuário à função de administrador de conformidade, preencha o nome principal do usuário da conta de usuário e, em seguida, execute estes comandos:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Proteções adicionais para empresas

Depois que as etapas 1 a 3, usam esses métodos adicionais para garantir que sua conta de administrador global e a configuração que você executar utilizá-lo, são mais seguro possível.
  
### <a name="privileged-access-workstation-paw"></a>Acesso privilegiado estação de trabalho (PATA)

Para garantir que a execução de tarefas com altos privilégios é mais segura possível, use uma PATA. Uma PATA é um computador dedicado que é usado somente para as tarefas de configuração confidenciais, como a configuração de Office 365, que requer uma conta de administrador global. Como este computador não é usado para navegar na Internet ou email diariamente, é melhor protegido contra ameaças e ataques pela Internet.
  
Para obter instruções sobre como configurar uma PATA, consulte [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Gerenciamento de identidade do Azure AD de privilégios (PIM)

Em vez de suas contas de administrador global permanentemente ser atribuídos à função de administrador global, você pode usar o Azure AD PIM para habilitar just-in-time, sob demanda atribuição da função de administrador global quando necessário.
  
Em vez de suas contas de administrador global sendo um administrador permanente, eles se tornam elegíveis administradores. A função de administrador global está inativa até que alguém precisa dele. Você deve concluir um processo de ativação para adicionar a função de administrador global para a conta de administrador global por um período predeterminado. Quando o tempo expira, PIM remove a conta de administrador global a função de administrador global.
  
Usando PIM e esse processo reduz significativamente a quantidade de tempo que suas contas de administrador global são vulneráveis a ataques e usar por usuários mal-intencionados.
  
Para obter mais informações, consulte [Configurar o Azure AD privilegiado gerenciamento de identidade](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> PIM está disponível com o Windows Azure Active Directory Premium P2, que está incluído com mobilidade corporativos + E5 de segurança (EMS), ou você pode adquirir licenças individuais para suas contas de administrador global. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Software de gerenciamento (SIEM) eventos e informações de segurança para o log do Office 365

Software SIEM executado em um servidor executa uma análise em tempo real de alertas de segurança e eventos criados por aplicativos e o hardware de rede. Para permitir que seu servidor SIEM incluir eventos e alertas de segurança do Office 365 em sua análise e funções de emissão de relatórios, integre essas no sistema SIEM:
  
- AD do Azure
    
    Para obter mais informações, consulte [integra-se logs do Azure recursos nos seus sistemas SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Office 365 Cloud App Security
    
    Para obter mais informações, consulte [integra-se seu servidor SIEM com segurança de aplicativo de nuvem do Office 365](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Próxima etapa

Consulte as [práticas recomendadas de segurança para o Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

