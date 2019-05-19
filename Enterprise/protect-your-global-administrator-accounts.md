---
title: Proteger as contas de administradores globais do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 5/16/2019
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
description: Proteger o acesso de administrador global à sua assinatura do Office 365.
ms.openlocfilehash: 353787ccda7ab96583fe75bc423f70d339d3435b
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162394"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="18519-103">Proteger as contas de administradores globais do Office 365</span><span class="sxs-lookup"><span data-stu-id="18519-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="18519-104">**Resumo:** Proteja sua assinatura do Office 365 contra ataques com base no comprometimento de uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="18519-105">As brechas de segurança de uma assinatura do Office 365, incluindo a coleta de informações e os ataques de phishing, são normalmente realizadas comprometendo as credenciais de uma conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="18519-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="18519-106">A segurança na nuvem é uma parceria entre você e a Microsoft:</span><span class="sxs-lookup"><span data-stu-id="18519-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="18519-107">Os serviços de nuvem da Microsoft são criados em uma base de confiança e segurança.</span><span class="sxs-lookup"><span data-stu-id="18519-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="18519-108">A Microsoft fornece recursos e controles de segurança para ajudá-lo a proteger seus dados e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="18519-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="18519-109">Você tem seus próprios dados e identidades e a responsabilidade de protegê-los, a segurança de seus recursos locais e a segurança dos componentes de nuvem que você controla.</span><span class="sxs-lookup"><span data-stu-id="18519-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="18519-110">A Microsoft fornece recursos para ajudar a proteger sua organização, mas elas só serão eficazes se você usá-las.</span><span class="sxs-lookup"><span data-stu-id="18519-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="18519-111">Se você não usá-los, pode estar vulnerável a ataques.</span><span class="sxs-lookup"><span data-stu-id="18519-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="18519-112">Para proteger suas contas de administrador global, a Microsoft está aqui para ajudá-lo com instruções detalhadas para:</span><span class="sxs-lookup"><span data-stu-id="18519-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="18519-113">Crie contas de administrador global do Office 365 exclusivas e as use somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="18519-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="18519-114">Configure a autenticação multifator para suas contas de administrador global do Office 365, e use a forma mais segura de autenticação secundária.</span><span class="sxs-lookup"><span data-stu-id="18519-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
> [!NOTE]
> <span data-ttu-id="18519-115">Embora este artigo se concentre nas contas de administrador global, você deve considerar se as contas adicionais têm permissões amplas para acessar os dados em sua assinatura, como administrador de descoberta eletrônica ou administrador de segurança ou conformidade contas, devem ser protegidas da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="18519-115">Although this article is focused on global administrator accounts, you should consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="18519-116">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="18519-116">Step 1.</span></span> <span data-ttu-id="18519-117">Criar contas de administrador global do Office 365 exclusivas e usá-las somente quando necessário</span><span class="sxs-lookup"><span data-stu-id="18519-117">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="18519-118">Há relativamente poucas tarefas administrativas, como a atribuição de funções a contas de usuário, que exigem privilégios de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-118">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="18519-119">Portanto, em vez de usar contas de usuário diárias às quais a função de administrador global tenha sido atribuída, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="18519-119">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="18519-120">Determine o conjunto de contas de usuário que foram atribuídas à função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-120">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="18519-121">Você pode fazer isso com o Azure Active Directory (Azure AD), comando PowerShell para Graph:</span><span class="sxs-lookup"><span data-stu-id="18519-121">You can do this with Azure Active (Azure AD) Directory PowerShell for Graph  command:</span></span>
  
  ```
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. <span data-ttu-id="18519-122">Entre em sua assinatura do Office 365 com uma conta de usuário que tenha sido atribuída à função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-122">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="18519-123">Crie pelo menos um e até um máximo de cinco contas de usuário de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="18519-123">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="18519-124">**Use senhas fortes pelo menos 12 caracteres.**</span><span class="sxs-lookup"><span data-stu-id="18519-124">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="18519-125">Consulte [criar uma senha forte](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="18519-125">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="18519-126">Armazene as senhas das novas contas em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="18519-126">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="18519-127">Atribua a função de administrador global a cada uma das novas contas de usuário de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="18519-127">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="18519-128">Saia do Office 365.</span><span class="sxs-lookup"><span data-stu-id="18519-128">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="18519-129">Entre com uma das novas contas de usuário do administrador global dedicado.</span><span class="sxs-lookup"><span data-stu-id="18519-129">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="18519-130">Para cada conta de usuário existente que tenha sido atribuída à função de administrador global da etapa 1:</span><span class="sxs-lookup"><span data-stu-id="18519-130">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="18519-131">Remova a função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-131">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="18519-132">Atribuir funções de administrador à conta que são apropriadas para a função e responsabilidade do trabalho do usuário.</span><span class="sxs-lookup"><span data-stu-id="18519-132">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="18519-133">Para obter mais informações sobre várias funções de administrador no Office 365, consulte [about Office 365 admin Roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="18519-133">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).</span></span>
    
8. <span data-ttu-id="18519-134">Saia do Office 365.</span><span class="sxs-lookup"><span data-stu-id="18519-134">Sign out of Office 365.</span></span>
    
<span data-ttu-id="18519-135">O resultado deve ser:</span><span class="sxs-lookup"><span data-stu-id="18519-135">The result should be:</span></span>
  
- <span data-ttu-id="18519-136">As únicas contas de usuários que possuem a função de administrador global em sua assinatura fazem parte do novo conjunto de contas de administradores globais dedicadas.</span><span class="sxs-lookup"><span data-stu-id="18519-136">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="18519-137">Verifique isso com o seguinte comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="18519-137">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- <span data-ttu-id="18519-138">Todas as outras contas de usuários comuns que gerenciam sua assinatura têm funções de administrador atribuídas que estão associadas às responsabilidades de trabalho deles.</span><span class="sxs-lookup"><span data-stu-id="18519-138">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="18519-139">Desse momento em diante, você entra com as contas de administrador global dedicadas apenas para tarefas que exigem privilégios de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-139">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="18519-140">Todas as outras administração do Office 365 devem ser feitas por meio da atribuição de outras funções de administração às contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="18519-140">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="18519-141">Isso requer etapas adicionais para sair como sua conta de usuário diária e entrar com uma conta de administrador global dedicada.</span><span class="sxs-lookup"><span data-stu-id="18519-141">This does require additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="18519-142">Mas isso só precisa ser feito ocasionalmente para operações de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-142">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="18519-143">Considere a recuperação de sua assinatura do Office 365 após uma violação de conta de administrador global exigir muito mais etapas.</span><span class="sxs-lookup"><span data-stu-id="18519-143">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span>
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="18519-144">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="18519-144">Step 2.</span></span> <span data-ttu-id="18519-145">Configurar a autenticação multifator para suas contas de administrador global do Office 365 exclusiva e usar a forma mais forte de autenticação secundária</span><span class="sxs-lookup"><span data-stu-id="18519-145">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="18519-146">A MFA (autenticação multifator) requer informações adicionais além do nome da conta e senha.</span><span class="sxs-lookup"><span data-stu-id="18519-146">Multi-factor authentication (MFA) requires additional information beyond the account name and password.</span></span> <span data-ttu-id="18519-147">O Office 365 suporta estes métodos de verificação:</span><span class="sxs-lookup"><span data-stu-id="18519-147">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="18519-148">Uma chamada telefônica</span><span class="sxs-lookup"><span data-stu-id="18519-148">A phone call</span></span>
    
- <span data-ttu-id="18519-149">Uma senha gerada aleatoriamente</span><span class="sxs-lookup"><span data-stu-id="18519-149">A randomly generated pass code</span></span>
    
- <span data-ttu-id="18519-150">Um cartão inteligente (físico ou virtual)</span><span class="sxs-lookup"><span data-stu-id="18519-150">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="18519-151">Um dispositivo biométrico</span><span class="sxs-lookup"><span data-stu-id="18519-151">A biometric device</span></span>
    
<span data-ttu-id="18519-152">Se você é uma pequena empresa que está usando contas de usuário armazenadas apenas na nuvem (modelo de identidade somente na nuvem), use estas etapas para configurar a MFA usando uma chamada telefônica ou um código de verificação de mensagem de texto enviado a um telefone inteligente:</span><span class="sxs-lookup"><span data-stu-id="18519-152">If you are a small business that is using user accounts stored only in the cloud (the cloud-only identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="18519-153">[Habilitar a MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span><span class="sxs-lookup"><span data-stu-id="18519-153">[Enable MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="18519-154">[Configurar a verificação em duas etapas para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada conta de administrador global dedicada para chamada telefônica ou mensagem de texto como o método de verificação.</span><span class="sxs-lookup"><span data-stu-id="18519-154">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="18519-155">Se você é uma organização maior que usa um modelo de identidade híbrida do Office 365, você tem mais opções de verificação.</span><span class="sxs-lookup"><span data-stu-id="18519-155">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="18519-156">Se você já tiver a infraestrutura de segurança em vigor para um método de autenticação secundário mais seguro, use estas etapas:</span><span class="sxs-lookup"><span data-stu-id="18519-156">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="18519-157">[Habilitar a MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span><span class="sxs-lookup"><span data-stu-id="18519-157">[Enable MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="18519-158">[Configure a verificação em duas etapas para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada conta de administrador global dedicada para o método de verificação apropriado.</span><span class="sxs-lookup"><span data-stu-id="18519-158">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="18519-159">Se a infraestrutura de segurança para o método de verificação mais forte desejado não estiver em vigor e estiver funcionando para o Office 365 MFA, é altamente recomendável que você configure contas de administrador global dedicadas com a MFA usando uma chamada telefônica ou uma mensagem de texto código de verificação enviado a um telefone inteligente para suas contas de administrador global como medida de segurança provisória.</span><span class="sxs-lookup"><span data-stu-id="18519-159">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="18519-160">Não deixe suas contas de administrador global dedicadas sem a proteção adicional fornecida pela MFA.</span><span class="sxs-lookup"><span data-stu-id="18519-160">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="18519-161">Para saber mais, consulte as informações sobre como [planejar a autenticação multifator para implantações do Office 365](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).</span><span class="sxs-lookup"><span data-stu-id="18519-161">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).</span></span>
  
<span data-ttu-id="18519-162">Para se conectar aos serviços do Office 365 com MFA e PowerShell, consulte [Este artigo](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="18519-162">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>


## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="18519-163">Proteções adicionais para organizações empresariais</span><span class="sxs-lookup"><span data-stu-id="18519-163">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="18519-164">Após as etapas 1 e 2, use esses métodos adicionais para garantir que sua conta de administrador global e a configuração que você executa usando a mesma sejam as mais seguras possíveis.</span><span class="sxs-lookup"><span data-stu-id="18519-164">After steps 1 and 2, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation"></a><span data-ttu-id="18519-165">Estação de trabalho de acesso privilegiado</span><span class="sxs-lookup"><span data-stu-id="18519-165">Privileged access workstation</span></span>

<span data-ttu-id="18519-166">Para garantir que a execução de tarefas altamente privilegiadas seja o mais segura possível, use uma estação de trabalho privilegiada (pata).</span><span class="sxs-lookup"><span data-stu-id="18519-166">To ensure that the execution of highly privileged tasks is as secure as possible, use a privileged access workstation (PAW).</span></span> <span data-ttu-id="18519-167">Um pata é um computador dedicado que é usado apenas para tarefas de configuração confidenciais, como a configuração do Office 365 que requer uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-167">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="18519-168">Como este computador não é usado diariamente para navegação na Internet ou email, é melhor proteger contra ataques e ameaças da Internet.</span><span class="sxs-lookup"><span data-stu-id="18519-168">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="18519-169">Para obter instruções sobre como configurar um pata, consulte [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="18519-169">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management"></a><span data-ttu-id="18519-170">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="18519-170">Azure AD Privileged Identity Management</span></span>

<span data-ttu-id="18519-171">Em vez de ter suas contas de administrador global atribuídas permanentemente à função de administrador global, você pode usar o gerenciamento de identidade privilegiada do Azure AD para habilitar a atribuição sob demanda e Just-in-time da função de administrador global quando é necessários.</span><span class="sxs-lookup"><span data-stu-id="18519-171">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD Privileged Identity Management (PIM) to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="18519-172">Em vez de suas contas de administrador global serem um administrador permanente, elas se tornam administradores qualificados.</span><span class="sxs-lookup"><span data-stu-id="18519-172">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="18519-173">A função de administrador global está inativa até que alguém precise dela.</span><span class="sxs-lookup"><span data-stu-id="18519-173">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="18519-174">Em seguida, conclua um processo de ativação para adicionar a função de administrador global à conta de administrador global para uma quantidade de tempo predeterminada.</span><span class="sxs-lookup"><span data-stu-id="18519-174">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="18519-175">Quando o tempo expira, o PIM remove a função de administrador global da conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-175">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="18519-176">Usar o PIM e esse processo reduz significativamente a quantidade de tempo que suas contas de administrador global estão vulneráveis a ataques e uso por usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="18519-176">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="18519-177">Para obter mais informações, consulte [Configure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="18519-177">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="18519-178">O PIM está disponível com o Azure AD Premium P2, que está incluído no Enterprise Mobility + Security (EMS) E5 ou você pode adquirir licenças individuais para suas contas de administrador global.</span><span class="sxs-lookup"><span data-stu-id="18519-178">PIM is available with Azure AD Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="18519-179">Software de gerenciamento de eventos e informações de segurança (SIEM) para log do Office 365</span><span class="sxs-lookup"><span data-stu-id="18519-179">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="18519-180">O software SIEM executado em um servidor realiza análises em tempo real de alertas e eventos de segurança criados por aplicativos e hardware de rede.</span><span class="sxs-lookup"><span data-stu-id="18519-180">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="18519-181">Para permitir que o seu servidor SIEM inclua alertas e eventos de segurança do Office 365 em suas funções de análise e relatórios, integre o Azure AD no SEIM.</span><span class="sxs-lookup"><span data-stu-id="18519-181">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate Azure AD into you SEIM.</span></span> <span data-ttu-id="18519-182">Confira [integrar logs dos recursos do Azure em seus sistemas Siem](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="18519-182">See [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="18519-183">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="18519-183">Next step</span></span>

<span data-ttu-id="18519-184">Se você estiver configurando a identidade para sua assinatura do Office 365, consulte:</span><span class="sxs-lookup"><span data-stu-id="18519-184">If you're setting up identity for your Office 365 subscription, see:</span></span>

- <span data-ttu-id="18519-185">[Identidades somente na nuvem](cloud-only-identities.md) se você estiver usando a identidade somente na nuvem</span><span class="sxs-lookup"><span data-stu-id="18519-185">[Cloud-only identities](cloud-only-identities.md) if you're using cloud-only identity</span></span>
- <span data-ttu-id="18519-186">[Preparar a sincronização de diretórios](prepare-for-directory-synchronization.md) se você estiver usando a identidade híbrida</span><span class="sxs-lookup"><span data-stu-id="18519-186">[Prepare for directory synchronization](prepare-for-directory-synchronization.md) if you're using hybrid identity</span></span>

  
## <a name="see-also"></a><span data-ttu-id="18519-187">Confira também</span><span class="sxs-lookup"><span data-stu-id="18519-187">See also</span></span>

<span data-ttu-id="18519-188">[Mapa de segurança do Office 365](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span><span class="sxs-lookup"><span data-stu-id="18519-188">[Office 365 security roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span></span>
