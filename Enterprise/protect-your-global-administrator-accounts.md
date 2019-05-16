---
title: Proteger as contas de administradores globais do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
audience: Admin
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
description: Proteja o acesso de administrador global à sua assinatura do Office 365 com estas três etapas.
ms.openlocfilehash: bb1b19a7ac0ec8e32c23303e8acf2b7ee42f0532
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071017"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a>Proteger as contas de administradores globais do Office 365

 **Resumo:** Proteja sua assinatura do Office 365 contra ataques com base no comprometimento de uma conta de administrador global. 
  
As brechas de segurança de uma assinatura do Office 365, incluindo a coleta de informações e os ataques de phishing, são normalmente realizadas comprometendo as credenciais de uma conta de administrador global do Office 365. A segurança na nuvem é uma parceria entre você e a Microsoft:
  
- Os serviços de nuvem da Microsoft são criados em uma base de confiança e segurança. A Microsoft fornece recursos e controles de segurança para ajudá-lo a proteger seus dados e aplicativos.
    
- Você tem seus próprios dados e identidades e a responsabilidade de protegê-los, a segurança de seus recursos locais e a segurança dos componentes de nuvem que você controla.
    
A Microsoft fornece recursos para ajudar a proteger sua organização, mas elas só serão eficazes se você usá-las. Se você não usá-los, pode estar vulnerável a ataques. Para proteger suas contas de administrador global, a Microsoft está aqui para ajudá-lo com instruções detalhadas para:
  
1. Crie contas de administrador global do Office 365 exclusivas e as use somente quando necessário.
    
2. Configure a autenticação multifator para suas contas de administrador global do Office 365, e use a forma mais segura de autenticação secundária.
    
3. Habilitar e configurar o Office 365 Cloud app Security para monitorar a atividade de conta de administrador global suspeito.
    
> [!NOTE]
> Embora este artigo se concentre em contas de administrador global, você também deve considerar se as contas adicionais com permissões amplas para acessar os dados em sua assinatura, como administrador de descoberta eletrônica ou segurança ou conformidade as contas de administrador devem ser protegidas da mesma maneira. 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Etapa 1. Criar contas de administrador global do Office 365 exclusivas e usá-las somente quando necessário

Há relativamente poucas tarefas administrativas, como a atribuição de funções a contas de usuário, que exigem privilégios de administrador global. Portanto, em vez de usar contas de usuário diárias às quais a função de administrador global tenha sido atribuída, siga estas etapas:
  
1. Determine o conjunto de contas de usuário que foram atribuídas à função de administrador global. Você pode fazer isso com este comando no prompt de comando do módulo do Microsoft Azure Active Directory para Windows PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. Entre em sua assinatura do Office 365 com uma conta de usuário que tenha sido atribuída à função de administrador global.
    
3. Crie pelo menos um e até um máximo de cinco contas de usuário de administrador global dedicadas. **Use senhas fortes pelo menos 12 caracteres.** Consulte [criar uma senha forte](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obter mais informações. Armazene as senhas das novas contas em um local seguro. 
    
4. Atribua a função de administrador global a cada uma das novas contas de usuário de administrador global dedicadas.
    
5. Saia do Office 365.
    
6. Entre com uma das novas contas de usuário do administrador global dedicado.
    
7. Para cada conta de usuário existente que tenha sido atribuída à função de administrador global da etapa 1:
    
  - Remova a função de administrador global.
    
  - Atribuir funções de administrador à conta que são apropriadas para a função e responsabilidade do trabalho do usuário. Para obter mais informações sobre várias funções de administrador no Office 365, consulte [about Office 365 admin Roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
8. Saia do Office 365.
    
O resultado deve ser:
  
- As únicas contas de usuários que possuem a função de administrador global em sua assinatura fazem parte do novo conjunto de contas de administradores globais dedicadas. Verifique isso com o seguinte comando do PowerShell:
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- Todas as outras contas de usuários comuns que gerenciam sua assinatura têm funções de administrador atribuídas que estão associadas às responsabilidades de trabalho deles.
    
Desse momento em diante, você entra com as contas de administrador global dedicadas apenas para tarefas que exigem privilégios de administrador global. Todas as outras administração do Office 365 devem ser feitas por meio da atribuição de outras funções de administração às contas de usuário.
  
> [!NOTE]
> Sim, isso requer etapas adicionais para sair como sua conta de usuário diária e entrar com uma conta de administrador global dedicada. Mas isso só precisa ser feito ocasionalmente para operações de administrador global. Considere a recuperação de sua assinatura do Office 365 após uma violação de conta de administrador global exigir muito mais etapas. 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a>Etapa 2. Configurar a autenticação multifator para suas contas de administrador global do Office 365 exclusiva e usar a forma mais forte de autenticação secundária

A MFA (autenticação multifator) para suas contas de administrador global requer informações adicionais além do nome da conta e senha. O Office 365 suporta estes métodos de verificação:
  
- Uma chamada telefônica
    
- Uma senha gerada aleatoriamente
    
- Um cartão inteligente (físico ou virtual)
    
- Um dispositivo biométrico
    
Se você é uma pequena empresa que está usando contas de usuário armazenadas apenas na nuvem (modelo de identidade de nuvem), use estas etapas para configurar a MFA usando uma chamada telefônica ou um código de verificação de mensagem de texto enviado a um telefone inteligente:
  
1. [Habilitar a MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Configurar a verificação em duas etapas para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada conta de administrador global dedicada para chamada telefônica ou mensagem de texto como o método de verificação. 
    
Se você é uma organização maior que usa um modelo de identidade híbrida do Office 365, você tem mais opções de verificação. Se você já tiver a infraestrutura de segurança em vigor para um método de autenticação secundário mais seguro, use estas etapas:
  
1. [Habilitar a MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).
    
2. [Configure a verificação em duas etapas para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada conta de administrador global dedicada para o método de verificação apropriado. 
    
Se a infraestrutura de segurança para o método de verificação mais forte desejado não estiver em vigor e estiver funcionando para o Office 365 MFA, é altamente recomendável que você configure contas de administrador global dedicadas com a MFA usando uma chamada telefônica ou uma mensagem de texto código de verificação enviado a um telefone inteligente para suas contas de administrador global como medida de segurança provisória. Não deixe suas contas de administrador global dedicadas sem a proteção adicional fornecida pela MFA.
  
Para saber mais, consulte as informações sobre como [planejar a autenticação multifator para implantações do Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).
  
Para se conectar aos serviços do Office 365 com MFA e PowerShell, consulte [Este artigo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a>Etapa 3. Monitorar a atividade de conta de administrador global suspeito

O Office 365 Cloud app Security permite que você crie políticas para notificá-lo de comportamento suspeito na sua assinatura. O Cloud app Security é integrado ao Office 365 e5, mas também está disponível como um serviço separado. Por exemplo, se você não tiver o Office 365 e5, poderá adquirir licenças de segurança de aplicativos de nuvem individuais para as contas de usuário atribuídas às funções de administrador global, administrador de segurança e administrador de conformidade.
  
Se você tiver o Cloud app Security em sua assinatura do Office 365, siga estas etapas:
  
1. Entre no centro de administração do Microsoft 365 com uma conta à qual a função Administrador de segurança ou administrador de conformidade tenha sido atribuída.
    
2. [Ative o Office 365 Cloud app Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).
    
3. Revise suas [políticas de detecção de anomalias no Office 365 Cloud app Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) para notificá-lo por email de padrões anormais de atividades administrativas privilegiadas. 
    
Para adicionar uma conta de usuário à função de administrador de segurança, [Conecte-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) com uma conta de administrador global dedicada e a MFA, preencha o nome principal de usuário da conta de usuário e execute estes comandos: 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

Para adicionar uma conta de usuário à função de administrador de conformidade, preencha o nome principal do usuário da conta de usuário e execute estes comandos:
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a>Proteções adicionais para organizações empresariais

Após as etapas 1-3, use estes métodos adicionais para garantir que sua conta de administrador global, e a configuração que você executa usando a mesma, sejam o mais seguras possível.
  
### <a name="privileged-access-workstation-paw"></a>Estação de trabalho de acesso privilegiado (pata)

Para garantir que a execução de tarefas altamente privilegiadas seja o mais segura possível, use um pata. Um pata é um computador dedicado que é usado apenas para tarefas de configuração confidenciais, como a configuração do Office 365 que requer uma conta de administrador global. Como este computador não é usado diariamente para navegação na Internet ou email, é melhor proteger contra ataques e ameaças da Internet.
  
Para obter instruções sobre como configurar um pata, consulte [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).
  
### <a name="azure-ad-privileged-identity-management-pim"></a>Gerenciamento de identidade privilegiado (PIM) do Azure AD

Em vez de ter as contas de administrador global atribuídas permanentemente à função de administrador global, você pode usar o PIM AD do Azure para habilitar a atribuição sob demanda e Just-in-time da função de administrador global quando for necessário.
  
Em vez de suas contas de administrador global serem um administrador permanente, elas se tornam administradores qualificados. A função de administrador global está inativa até que alguém precise dela. Em seguida, conclua um processo de ativação para adicionar a função de administrador global à conta de administrador global para uma quantidade de tempo predeterminada. Quando o tempo expira, o PIM remove a função de administrador global da conta de administrador global.
  
Usar o PIM e esse processo reduz significativamente a quantidade de tempo que suas contas de administrador global estão vulneráveis a ataques e uso por usuários mal-intencionados.
  
Para obter mais informações, consulte [Configure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).
  
> [!NOTE]
> O PIM está disponível com o Azure Active Directory Premium P2, que está incluído no Enterprise Mobility + Security (EMS) e5, ou você pode adquirir licenças individuais para suas contas de administrador global. 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a>Software de gerenciamento de eventos e informações de segurança (SIEM) para log do Office 365

O software SIEM executado em um servidor realiza análises em tempo real de alertas e eventos de segurança criados por aplicativos e hardware de rede. Para permitir que seu servidor SIEM inclua alertas e eventos de segurança do Office 365 em suas funções de análise e relatórios, integre-os no seu sistema SIEM:
  
- Azure AD
    
    Para obter mais informações, consulte [integrar logs dos recursos do Azure em seus sistemas Siem](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).
    
- Office 365 Cloud App Security
    
    Para obter mais informações, consulte [integrar seu servidor Siem com o Office 365 Cloud app Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).
    
## <a name="next-step"></a>Próxima etapa

Consulte [práticas recomendadas de segurança para o Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).
  

