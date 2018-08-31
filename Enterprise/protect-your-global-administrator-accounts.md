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
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="8a020-103">Proteger as contas de administradores globais do Office 365</span><span class="sxs-lookup"><span data-stu-id="8a020-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="8a020-104">**Resumo:** Protege sua assinatura do Office 365 contra ataques com base no comprometimento de uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="8a020-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="8a020-p101">As violações de segurança de uma assinatura do Office 365, incluindo a coleta de informações e ataques de phishing, normalmente são feitas por comprometer as credenciais de uma conta de administrador global do Office 365. Segurança na nuvem é uma parceria entre você e a Microsoft:</span><span class="sxs-lookup"><span data-stu-id="8a020-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="8a020-p102">Serviços de nuvem da Microsoft são compilados em uma base de confiabilidade e segurança. A Microsoft fornece a controles de segurança e recursos para ajudá-lo a proteger os dados e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8a020-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="8a020-109">Você é proprietário seus dados e identidades e a responsabilidade de proteção-los, a segurança dos seus recursos no local e a segurança dos componentes de nuvem, que você controlar.</span><span class="sxs-lookup"><span data-stu-id="8a020-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="8a020-p103">A Microsoft fornece recursos para ajudar a proteger a sua organização, mas são efetivas apenas se você usá-los. Se você não usá-los, você pode estar vulnerável a ataques. Para proteger suas contas de administrador global, a Microsoft está aqui para ajudá-lo com instruções detalhadas para:</span><span class="sxs-lookup"><span data-stu-id="8a020-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="8a020-113">Criar contas de administrador global do Office 365 dedicadas e usá-los somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="8a020-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="8a020-114">Configurar a autenticação multifator para contas de administrador global do Office 365 dedicadas e usar o formulário mais forte de autenticação secundário.</span><span class="sxs-lookup"><span data-stu-id="8a020-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="8a020-115">Habilitar e configurar a segurança de aplicativo do Office 365 nuvem para monitorar a atividade da conta de administrador global suspeitas de.</span><span class="sxs-lookup"><span data-stu-id="8a020-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="8a020-116">Embora este artigo concentra-se em contas de administrador global, você também deve considerar se adicionais contas com amplas permissões para acessar os dados na sua assinatura, como administrador de descoberta eletrônica ou segurança ou conformidade contas de administrador, devem ser protegidos da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="8a020-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="8a020-p104">Etapa 1. Criar contas de administrador global do Office 365 dedicadas e usá-los somente quando necessário</span><span class="sxs-lookup"><span data-stu-id="8a020-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="8a020-p105">Há relativamente poucas tarefas administrativas, como atribuindo funções a contas de usuário, que exigem privilégios de administrador global. Portanto, em vez de usar contas de usuário cotidianos que tiverem sido atribuídas a função de administrador global, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="8a020-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="8a020-p106">Determine o conjunto de contas de usuário que tiverem sido atribuídas a função de administrador global. Você pode fazer isso com este comando no prompt de comando do Microsoft Azure Active Directory módulo para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8a020-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="8a020-123">Inscreva-se em sua assinatura do Office 365 com uma conta de usuário que tenha sido atribuída a função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="8a020-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="8a020-p107">Criar pelo menos um e até um máximo de cinco dedicado contas de usuário de administrador global. **Uso longo. caracteres de senhas fortes, pelo menos, 12** Consulte [criar uma senha forte](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obter mais informações. Armazene as senhas para as novas contas em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="8a020-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="8a020-128">Atribua a função de administrador global a cada uma das contas de usuário de administrador global novo dedicado.</span><span class="sxs-lookup"><span data-stu-id="8a020-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="8a020-129">Sair do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a020-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="8a020-130">Entrar com uma das novas contas de usuário do administrador global dedicado.</span><span class="sxs-lookup"><span data-stu-id="8a020-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="8a020-131">Para cada conta de usuário existente que tinha sido atribuída a função de administrador global da etapa 1:</span><span class="sxs-lookup"><span data-stu-id="8a020-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="8a020-132">Remova a função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="8a020-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="8a020-p108">Atribua funções de administrador para a conta que são apropriados para a função de trabalho e a responsabilidade desse usuário. Para obter mais informações sobre diversas funções de administrador no Office 365, consulte [funções de administrador do Office 365](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="8a020-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="8a020-135">Sair do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8a020-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="8a020-136">O resultado deve ser:</span><span class="sxs-lookup"><span data-stu-id="8a020-136">The result should be:</span></span>
  
- <span data-ttu-id="8a020-p109">As contas de usuário somente na sua assinatura que possuem a função de administrador global são o novo conjunto de contas de administrador global dedicado. Verificar isso com o seguinte comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8a020-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="8a020-139">Todas as outras contas de usuários comuns que gerenciam sua assinatura têm funções de administrador atribuídas que estão associadas às responsabilidades de trabalho deles.</span><span class="sxs-lookup"><span data-stu-id="8a020-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="8a020-p110">A partir neste momento em diante, você entrar com as contas de administrador global dedicado somente para tarefas que exigem privilégios de administrador global. Todos os outro administração do Office 365 devem ser feito pela atribuição de outras funções de administração para contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="8a020-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8a020-p111">Sim, isso requer etapas adicionais para desconectá-como sua conta de usuário cotidianos e entrar com uma conta de administrador global dedicado. Mas isso só precisa ser feito ocasionalmente para operações de administrador global. Considere que recuperando sua assinatura do Office 365 após uma violação da conta de administrador global requer etapas muito mais.</span><span class="sxs-lookup"><span data-stu-id="8a020-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="8a020-p112">Etapa 2. Configurar a autenticação multifator para contas de administrador global do Office 365 dedicadas e usar o formulário mais forte de autenticação secundário</span><span class="sxs-lookup"><span data-stu-id="8a020-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="8a020-p113">A autenticação multifator (MFA) para suas contas de administrador global requer informações adicionais além do nome da conta e senha. O Office 365 oferece suporte a esses métodos de verificação:</span><span class="sxs-lookup"><span data-stu-id="8a020-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="8a020-149">Uma chamada telefônica</span><span class="sxs-lookup"><span data-stu-id="8a020-149">A phone call</span></span>
    
- <span data-ttu-id="8a020-150">Uma senha gerada aleatoriamente</span><span class="sxs-lookup"><span data-stu-id="8a020-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="8a020-151">Um cartão inteligente (físico ou virtual)</span><span class="sxs-lookup"><span data-stu-id="8a020-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="8a020-152">Um dispositivo biométrico</span><span class="sxs-lookup"><span data-stu-id="8a020-152">A biometric device</span></span>
    
<span data-ttu-id="8a020-153">Se você estiver uma pequena empresa que está usando contas de usuário armazenadas somente na nuvem (o modelo de identidade de nuvem), execute estas etapas para configurar MFA usando uma chamada telefônica ou um código de verificação de mensagem de texto enviada para um telefone inteligente:</span><span class="sxs-lookup"><span data-stu-id="8a020-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="8a020-154">[Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="8a020-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="8a020-155">[Set up 2-etapa de verificação para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada dedicada a conta de administrador global para chamada telefônica ou mensagem de texto como o método de verificação.</span><span class="sxs-lookup"><span data-stu-id="8a020-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="8a020-p114">Se você for uma grande organização que está usando um modelo de identidade do Office 365 híbrido, você tem mais opções de verificação. Se você tiver a infra-estrutura de segurança já em vigor para um método de autenticação secundária mais seguro, execute estas etapas:</span><span class="sxs-lookup"><span data-stu-id="8a020-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="8a020-158">[Habilitar MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="8a020-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="8a020-159">[Set up 2-etapa de verificação para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada dedicada a conta de administrador global para o método de verificação apropriada.</span><span class="sxs-lookup"><span data-stu-id="8a020-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="8a020-p115">Se a infraestrutura de segurança para o método de verificação mais forte desejado não estiver instalado e funcionando para Office 365 MFA, é altamente recomendável que você configure contas de administrador global dedicado com MFA usando uma chamada telefônica ou uma mensagem de texto código de verificação enviado a um telefone inteligente para suas contas de administrador global como uma medida de segurança provisório. Não deixe suas contas de administrador global dedicado sem a proteção adicional fornecida pelo MFA.</span><span class="sxs-lookup"><span data-stu-id="8a020-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="8a020-162">Para saber mais, consulte as informações sobre como [planejar a autenticação multifator para implantações do Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="8a020-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="8a020-163">Para se conectar aos serviços do Office 365 com MFA e PowerShell, consulte [Este artigo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="8a020-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="8a020-p116">Etapa 3. Monitor das atividades da conta de administrador global suspeitas</span><span class="sxs-lookup"><span data-stu-id="8a020-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="8a020-p117">Segurança de aplicativo de nuvem do Office 365 permite que você crie políticas para notificá-lo de comportamento suspeito em sua assinatura. Segurança de aplicativo de nuvem é incorporada ao Office 365 E5, mas também está disponível como um serviço separado. Por exemplo, se você não tiver E5 do Office 365, você pode adquirir licenças individuais de segurança de aplicativo de nuvem para as contas de usuário que são atribuídas a administrador global, os administradores de segurança e funções de administrador de conformidade.</span><span class="sxs-lookup"><span data-stu-id="8a020-p117">Office 365 Cloud App Security allows you to create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="8a020-169">Se você tiver segurança de aplicativo de nuvem em sua assinatura do Office 365, execute estas etapas:</span><span class="sxs-lookup"><span data-stu-id="8a020-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="8a020-170">Entrar no portal do Office 365 com uma conta que é atribuída a função de administrador de segurança ou administrador de conformidade.</span><span class="sxs-lookup"><span data-stu-id="8a020-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="8a020-171">[Ative a segurança de aplicativo do Office 365 nuvem](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="8a020-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="8a020-172">Examine suas [políticas de detecção de anomalias na segurança de aplicativo de nuvem do Office 365](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) para notificá-lo por email dos padrões anômalos das atividades administrativas privilegiada.</span><span class="sxs-lookup"><span data-stu-id="8a020-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="8a020-173">Para adicionar uma conta de usuário à função de administrador de segurança, [Conecte-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) com uma conta de administrador global dedicado e MFA, preencha o nome principal do usuário da conta de usuário e, em seguida, execute estes comandos:</span><span class="sxs-lookup"><span data-stu-id="8a020-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="8a020-174">Para adicionar uma conta de usuário à função de administrador de conformidade, preencha o nome principal do usuário da conta de usuário e, em seguida, execute estes comandos:</span><span class="sxs-lookup"><span data-stu-id="8a020-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="8a020-175">Proteções adicionais para empresas</span><span class="sxs-lookup"><span data-stu-id="8a020-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="8a020-176">Depois que as etapas 1 a 3, usam esses métodos adicionais para garantir que sua conta de administrador global e a configuração que você executar utilizá-lo, são mais seguro possível.</span><span class="sxs-lookup"><span data-stu-id="8a020-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="8a020-177">Acesso privilegiado estação de trabalho (PATA)</span><span class="sxs-lookup"><span data-stu-id="8a020-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="8a020-p118">Para garantir que a execução de tarefas com altos privilégios é mais segura possível, use uma PATA. Uma PATA é um computador dedicado que é usado somente para as tarefas de configuração confidenciais, como a configuração de Office 365, que requer uma conta de administrador global. Como este computador não é usado para navegar na Internet ou email diariamente, é melhor protegido contra ameaças e ataques pela Internet.</span><span class="sxs-lookup"><span data-stu-id="8a020-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="8a020-181">Para obter instruções sobre como configurar uma PATA, consulte [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="8a020-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="8a020-182">Gerenciamento de identidade do Azure AD de privilégios (PIM)</span><span class="sxs-lookup"><span data-stu-id="8a020-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="8a020-183">Em vez de suas contas de administrador global permanentemente ser atribuídos à função de administrador global, você pode usar o Azure AD PIM para habilitar just-in-time, sob demanda atribuição da função de administrador global quando necessário.</span><span class="sxs-lookup"><span data-stu-id="8a020-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="8a020-p119">Em vez de suas contas de administrador global sendo um administrador permanente, eles se tornam elegíveis administradores. A função de administrador global está inativa até que alguém precisa dele. Você deve concluir um processo de ativação para adicionar a função de administrador global para a conta de administrador global por um período predeterminado. Quando o tempo expira, PIM remove a conta de administrador global a função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="8a020-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="8a020-188">Usando PIM e esse processo reduz significativamente a quantidade de tempo que suas contas de administrador global são vulneráveis a ataques e usar por usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="8a020-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="8a020-189">Para obter mais informações, consulte [Configurar o Azure AD privilegiado gerenciamento de identidade](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="8a020-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="8a020-190">PIM está disponível com o Windows Azure Active Directory Premium P2, que está incluído com mobilidade corporativos + E5 de segurança (EMS), ou você pode adquirir licenças individuais para suas contas de administrador global.</span><span class="sxs-lookup"><span data-stu-id="8a020-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="8a020-191">Software de gerenciamento (SIEM) eventos e informações de segurança para o log do Office 365</span><span class="sxs-lookup"><span data-stu-id="8a020-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="8a020-p120">Software SIEM executado em um servidor executa uma análise em tempo real de alertas de segurança e eventos criados por aplicativos e o hardware de rede. Para permitir que seu servidor SIEM incluir eventos e alertas de segurança do Office 365 em sua análise e funções de emissão de relatórios, integre essas no sistema SIEM:</span><span class="sxs-lookup"><span data-stu-id="8a020-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="8a020-194">AD do Azure</span><span class="sxs-lookup"><span data-stu-id="8a020-194">Azure AD</span></span>
    
    <span data-ttu-id="8a020-195">Para obter mais informações, consulte [integra-se logs do Azure recursos nos seus sistemas SIEM](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="8a020-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="8a020-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="8a020-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="8a020-197">Para obter mais informações, consulte [integra-se seu servidor SIEM com segurança de aplicativo de nuvem do Office 365](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="8a020-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="8a020-198">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="8a020-198">Next step</span></span>

<span data-ttu-id="8a020-199">Consulte as [práticas recomendadas de segurança para o Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="8a020-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

