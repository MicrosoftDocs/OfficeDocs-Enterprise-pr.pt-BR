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
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="19c41-103">Proteger as contas de administradores globais do Office 365</span><span class="sxs-lookup"><span data-stu-id="19c41-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="19c41-104">**Resumo:** Proteja sua assinatura do Office 365 contra ataques com base no comprometimento de uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="19c41-105">As brechas de segurança de uma assinatura do Office 365, incluindo a coleta de informações e os ataques de phishing, são normalmente realizadas comprometendo as credenciais de uma conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="19c41-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="19c41-106">A segurança na nuvem é uma parceria entre você e a Microsoft:</span><span class="sxs-lookup"><span data-stu-id="19c41-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="19c41-107">Os serviços de nuvem da Microsoft são criados em uma base de confiança e segurança.</span><span class="sxs-lookup"><span data-stu-id="19c41-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="19c41-108">A Microsoft fornece recursos e controles de segurança para ajudá-lo a proteger seus dados e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="19c41-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="19c41-109">Você tem seus próprios dados e identidades e a responsabilidade de protegê-los, a segurança de seus recursos locais e a segurança dos componentes de nuvem que você controla.</span><span class="sxs-lookup"><span data-stu-id="19c41-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="19c41-110">A Microsoft fornece recursos para ajudar a proteger sua organização, mas elas só serão eficazes se você usá-las.</span><span class="sxs-lookup"><span data-stu-id="19c41-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="19c41-111">Se você não usá-los, pode estar vulnerável a ataques.</span><span class="sxs-lookup"><span data-stu-id="19c41-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="19c41-112">Para proteger suas contas de administrador global, a Microsoft está aqui para ajudá-lo com instruções detalhadas para:</span><span class="sxs-lookup"><span data-stu-id="19c41-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="19c41-113">Crie contas de administrador global do Office 365 exclusivas e as use somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="19c41-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="19c41-114">Configure a autenticação multifator para suas contas de administrador global do Office 365, e use a forma mais segura de autenticação secundária.</span><span class="sxs-lookup"><span data-stu-id="19c41-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="19c41-115">Habilitar e configurar o Office 365 Cloud app Security para monitorar a atividade de conta de administrador global suspeito.</span><span class="sxs-lookup"><span data-stu-id="19c41-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="19c41-116">Embora este artigo se concentre em contas de administrador global, você também deve considerar se as contas adicionais com permissões amplas para acessar os dados em sua assinatura, como administrador de descoberta eletrônica ou segurança ou conformidade as contas de administrador devem ser protegidas da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="19c41-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="19c41-117">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="19c41-117">Step 1.</span></span> <span data-ttu-id="19c41-118">Criar contas de administrador global do Office 365 exclusivas e usá-las somente quando necessário</span><span class="sxs-lookup"><span data-stu-id="19c41-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="19c41-119">Há relativamente poucas tarefas administrativas, como a atribuição de funções a contas de usuário, que exigem privilégios de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="19c41-120">Portanto, em vez de usar contas de usuário diárias às quais a função de administrador global tenha sido atribuída, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="19c41-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="19c41-121">Determine o conjunto de contas de usuário que foram atribuídas à função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="19c41-122">Você pode fazer isso com este comando no prompt de comando do módulo do Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="19c41-122">You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="19c41-123">Entre em sua assinatura do Office 365 com uma conta de usuário que tenha sido atribuída à função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="19c41-124">Crie pelo menos um e até um máximo de cinco contas de usuário de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="19c41-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="19c41-125">**Use senhas fortes pelo menos 12 caracteres.**</span><span class="sxs-lookup"><span data-stu-id="19c41-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="19c41-126">Consulte [criar uma senha forte](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="19c41-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="19c41-127">Armazene as senhas das novas contas em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="19c41-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="19c41-128">Atribua a função de administrador global a cada uma das novas contas de usuário de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="19c41-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="19c41-129">Saia do Office 365.</span><span class="sxs-lookup"><span data-stu-id="19c41-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="19c41-130">Entre com uma das novas contas de usuário do administrador global dedicado.</span><span class="sxs-lookup"><span data-stu-id="19c41-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="19c41-131">Para cada conta de usuário existente que tenha sido atribuída à função de administrador global da etapa 1:</span><span class="sxs-lookup"><span data-stu-id="19c41-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="19c41-132">Remova a função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="19c41-133">Atribuir funções de administrador à conta que são apropriadas para a função e responsabilidade do trabalho do usuário.</span><span class="sxs-lookup"><span data-stu-id="19c41-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="19c41-134">Para obter mais informações sobre várias funções de administrador no Office 365, consulte [about Office 365 admin Roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span><span class="sxs-lookup"><span data-stu-id="19c41-134">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="19c41-135">Saia do Office 365.</span><span class="sxs-lookup"><span data-stu-id="19c41-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="19c41-136">O resultado deve ser:</span><span class="sxs-lookup"><span data-stu-id="19c41-136">The result should be:</span></span>
  
- <span data-ttu-id="19c41-137">As únicas contas de usuários que possuem a função de administrador global em sua assinatura fazem parte do novo conjunto de contas de administradores globais dedicadas.</span><span class="sxs-lookup"><span data-stu-id="19c41-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="19c41-138">Verifique isso com o seguinte comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="19c41-138">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="19c41-139">Todas as outras contas de usuários comuns que gerenciam sua assinatura têm funções de administrador atribuídas que estão associadas às responsabilidades de trabalho deles.</span><span class="sxs-lookup"><span data-stu-id="19c41-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="19c41-140">Desse momento em diante, você entra com as contas de administrador global dedicadas apenas para tarefas que exigem privilégios de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="19c41-141">Todas as outras administração do Office 365 devem ser feitas por meio da atribuição de outras funções de administração às contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="19c41-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="19c41-142">Sim, isso requer etapas adicionais para sair como sua conta de usuário diária e entrar com uma conta de administrador global dedicada.</span><span class="sxs-lookup"><span data-stu-id="19c41-142">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="19c41-143">Mas isso só precisa ser feito ocasionalmente para operações de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="19c41-144">Considere a recuperação de sua assinatura do Office 365 após uma violação de conta de administrador global exigir muito mais etapas.</span><span class="sxs-lookup"><span data-stu-id="19c41-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="19c41-145">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="19c41-145">Step 2.</span></span> <span data-ttu-id="19c41-146">Configurar a autenticação multifator para suas contas de administrador global do Office 365 exclusiva e usar a forma mais forte de autenticação secundária</span><span class="sxs-lookup"><span data-stu-id="19c41-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="19c41-147">A MFA (autenticação multifator) para suas contas de administrador global requer informações adicionais além do nome da conta e senha.</span><span class="sxs-lookup"><span data-stu-id="19c41-147">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password.</span></span> <span data-ttu-id="19c41-148">O Office 365 suporta estes métodos de verificação:</span><span class="sxs-lookup"><span data-stu-id="19c41-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="19c41-149">Uma chamada telefônica</span><span class="sxs-lookup"><span data-stu-id="19c41-149">A phone call</span></span>
    
- <span data-ttu-id="19c41-150">Uma senha gerada aleatoriamente</span><span class="sxs-lookup"><span data-stu-id="19c41-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="19c41-151">Um cartão inteligente (físico ou virtual)</span><span class="sxs-lookup"><span data-stu-id="19c41-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="19c41-152">Um dispositivo biométrico</span><span class="sxs-lookup"><span data-stu-id="19c41-152">A biometric device</span></span>
    
<span data-ttu-id="19c41-153">Se você é uma pequena empresa que está usando contas de usuário armazenadas apenas na nuvem (modelo de identidade de nuvem), use estas etapas para configurar a MFA usando uma chamada telefônica ou um código de verificação de mensagem de texto enviado a um telefone inteligente:</span><span class="sxs-lookup"><span data-stu-id="19c41-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="19c41-154">[Habilitar a MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="19c41-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="19c41-155">[Configurar a verificação em duas etapas para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada conta de administrador global dedicada para chamada telefônica ou mensagem de texto como o método de verificação.</span><span class="sxs-lookup"><span data-stu-id="19c41-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="19c41-156">Se você é uma organização maior que usa um modelo de identidade híbrida do Office 365, você tem mais opções de verificação.</span><span class="sxs-lookup"><span data-stu-id="19c41-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="19c41-157">Se você já tiver a infraestrutura de segurança em vigor para um método de autenticação secundário mais seguro, use estas etapas:</span><span class="sxs-lookup"><span data-stu-id="19c41-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="19c41-158">[Habilitar a MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span><span class="sxs-lookup"><span data-stu-id="19c41-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="19c41-159">[Configure a verificação em duas etapas para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada conta de administrador global dedicada para o método de verificação apropriado.</span><span class="sxs-lookup"><span data-stu-id="19c41-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="19c41-160">Se a infraestrutura de segurança para o método de verificação mais forte desejado não estiver em vigor e estiver funcionando para o Office 365 MFA, é altamente recomendável que você configure contas de administrador global dedicadas com a MFA usando uma chamada telefônica ou uma mensagem de texto código de verificação enviado a um telefone inteligente para suas contas de administrador global como medida de segurança provisória.</span><span class="sxs-lookup"><span data-stu-id="19c41-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="19c41-161">Não deixe suas contas de administrador global dedicadas sem a proteção adicional fornecida pela MFA.</span><span class="sxs-lookup"><span data-stu-id="19c41-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="19c41-162">Para saber mais, consulte as informações sobre como [planejar a autenticação multifator para implantações do Office 365](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span><span class="sxs-lookup"><span data-stu-id="19c41-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="19c41-163">Para se conectar aos serviços do Office 365 com MFA e PowerShell, consulte [Este artigo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="19c41-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="19c41-164">Etapa 3.</span><span class="sxs-lookup"><span data-stu-id="19c41-164">Step 3.</span></span> <span data-ttu-id="19c41-165">Monitorar a atividade de conta de administrador global suspeito</span><span class="sxs-lookup"><span data-stu-id="19c41-165">Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="19c41-166">O Office 365 Cloud app Security permite que você crie políticas para notificá-lo de comportamento suspeito na sua assinatura.</span><span class="sxs-lookup"><span data-stu-id="19c41-166">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription.</span></span> <span data-ttu-id="19c41-167">O Cloud app Security é integrado ao Office 365 e5, mas também está disponível como um serviço separado.</span><span class="sxs-lookup"><span data-stu-id="19c41-167">Cloud App Security is built into Office 365 E5, but is also available as a separate service.</span></span> <span data-ttu-id="19c41-168">Por exemplo, se você não tiver o Office 365 e5, poderá adquirir licenças de segurança de aplicativos de nuvem individuais para as contas de usuário atribuídas às funções de administrador global, administrador de segurança e administrador de conformidade.</span><span class="sxs-lookup"><span data-stu-id="19c41-168">For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="19c41-169">Se você tiver o Cloud app Security em sua assinatura do Office 365, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="19c41-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="19c41-170">Entre no centro de administração do Microsoft 365 com uma conta à qual a função Administrador de segurança ou administrador de conformidade tenha sido atribuída.</span><span class="sxs-lookup"><span data-stu-id="19c41-170">Sign into the Microsoft 365 admin center with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="19c41-171">[Ative o Office 365 Cloud app Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span><span class="sxs-lookup"><span data-stu-id="19c41-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="19c41-172">Revise suas [políticas de detecção de anomalias no Office 365 Cloud app Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) para notificá-lo por email de padrões anormais de atividades administrativas privilegiadas.</span><span class="sxs-lookup"><span data-stu-id="19c41-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="19c41-173">Para adicionar uma conta de usuário à função de administrador de segurança, [Conecte-se ao Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) com uma conta de administrador global dedicada e a MFA, preencha o nome principal de usuário da conta de usuário e execute estes comandos:</span><span class="sxs-lookup"><span data-stu-id="19c41-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="19c41-174">Para adicionar uma conta de usuário à função de administrador de conformidade, preencha o nome principal do usuário da conta de usuário e execute estes comandos:</span><span class="sxs-lookup"><span data-stu-id="19c41-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="19c41-175">Proteções adicionais para organizações empresariais</span><span class="sxs-lookup"><span data-stu-id="19c41-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="19c41-176">Após as etapas 1-3, use estes métodos adicionais para garantir que sua conta de administrador global, e a configuração que você executa usando a mesma, sejam o mais seguras possível.</span><span class="sxs-lookup"><span data-stu-id="19c41-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="19c41-177">Estação de trabalho de acesso privilegiado (pata)</span><span class="sxs-lookup"><span data-stu-id="19c41-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="19c41-178">Para garantir que a execução de tarefas altamente privilegiadas seja o mais segura possível, use um pata.</span><span class="sxs-lookup"><span data-stu-id="19c41-178">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW.</span></span> <span data-ttu-id="19c41-179">Um pata é um computador dedicado que é usado apenas para tarefas de configuração confidenciais, como a configuração do Office 365 que requer uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-179">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="19c41-180">Como este computador não é usado diariamente para navegação na Internet ou email, é melhor proteger contra ataques e ameaças da Internet.</span><span class="sxs-lookup"><span data-stu-id="19c41-180">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="19c41-181">Para obter instruções sobre como configurar um pata, consulte [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="19c41-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="19c41-182">Gerenciamento de identidade privilegiado (PIM) do Azure AD</span><span class="sxs-lookup"><span data-stu-id="19c41-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="19c41-183">Em vez de ter as contas de administrador global atribuídas permanentemente à função de administrador global, você pode usar o PIM AD do Azure para habilitar a atribuição sob demanda e Just-in-time da função de administrador global quando for necessário.</span><span class="sxs-lookup"><span data-stu-id="19c41-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="19c41-184">Em vez de suas contas de administrador global serem um administrador permanente, elas se tornam administradores qualificados.</span><span class="sxs-lookup"><span data-stu-id="19c41-184">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="19c41-185">A função de administrador global está inativa até que alguém precise dela.</span><span class="sxs-lookup"><span data-stu-id="19c41-185">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="19c41-186">Em seguida, conclua um processo de ativação para adicionar a função de administrador global à conta de administrador global para uma quantidade de tempo predeterminada.</span><span class="sxs-lookup"><span data-stu-id="19c41-186">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="19c41-187">Quando o tempo expira, o PIM remove a função de administrador global da conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-187">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="19c41-188">Usar o PIM e esse processo reduz significativamente a quantidade de tempo que suas contas de administrador global estão vulneráveis a ataques e uso por usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="19c41-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="19c41-189">Para obter mais informações, consulte [Configure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="19c41-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="19c41-190">O PIM está disponível com o Azure Active Directory Premium P2, que está incluído no Enterprise Mobility + Security (EMS) e5, ou você pode adquirir licenças individuais para suas contas de administrador global.</span><span class="sxs-lookup"><span data-stu-id="19c41-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="19c41-191">Software de gerenciamento de eventos e informações de segurança (SIEM) para log do Office 365</span><span class="sxs-lookup"><span data-stu-id="19c41-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="19c41-192">O software SIEM executado em um servidor realiza análises em tempo real de alertas e eventos de segurança criados por aplicativos e hardware de rede.</span><span class="sxs-lookup"><span data-stu-id="19c41-192">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="19c41-193">Para permitir que seu servidor SIEM inclua alertas e eventos de segurança do Office 365 em suas funções de análise e relatórios, integre-os no seu sistema SIEM:</span><span class="sxs-lookup"><span data-stu-id="19c41-193">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="19c41-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="19c41-194">Azure AD</span></span>
    
    <span data-ttu-id="19c41-195">Para obter mais informações, consulte [integrar logs dos recursos do Azure em seus sistemas Siem](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="19c41-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="19c41-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="19c41-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="19c41-197">Para obter mais informações, consulte [integrar seu servidor Siem com o Office 365 Cloud app Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span><span class="sxs-lookup"><span data-stu-id="19c41-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="19c41-198">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="19c41-198">Next step</span></span>

<span data-ttu-id="19c41-199">Consulte [práticas recomendadas de segurança para o Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span><span class="sxs-lookup"><span data-stu-id="19c41-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

