---
title: Proteger as contas de administradores globais do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Proteger o acesso de administrador global à sua assinatura do Office 365.
ms.openlocfilehash: fcd4d69df967ad592af52a36a55008463b6f30e2
ms.sourcegitcommit: cc05697650e0a49d7901d6c9a14753e2f8e79362
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "42979363"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="966e1-103">Proteger as contas de administradores globais do Office 365</span><span class="sxs-lookup"><span data-stu-id="966e1-103">Protect your Office 365 global administrator accounts</span></span>

> [!NOTE]
> <span data-ttu-id="966e1-104">Uma conta de administrador global pode ser criada sem adicionar nenhuma licença.</span><span class="sxs-lookup"><span data-stu-id="966e1-104">A global administrator account can be created without adding any licenses.</span></span>

<span data-ttu-id="966e1-105">*Esse artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="966e1-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="966e1-106">As brechas de segurança de uma assinatura do Office 365, incluindo a coleta de informações e os ataques de phishing, são normalmente realizadas comprometendo as credenciais de uma conta de administrador global do Office 365.</span><span class="sxs-lookup"><span data-stu-id="966e1-106">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="966e1-107">A segurança na nuvem é uma parceria entre você e a Microsoft:</span><span class="sxs-lookup"><span data-stu-id="966e1-107">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="966e1-108">Os serviços de nuvem da Microsoft são criados em uma base de confiança e segurança.</span><span class="sxs-lookup"><span data-stu-id="966e1-108">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="966e1-109">A Microsoft fornece recursos e controles de segurança para ajudá-lo a proteger seus dados e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="966e1-109">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="966e1-110">Você tem seus próprios dados e identidades e a responsabilidade de protegê-los, a segurança de seus recursos locais e a segurança dos componentes de nuvem que você controla.</span><span class="sxs-lookup"><span data-stu-id="966e1-110">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="966e1-111">A Microsoft fornece recursos para ajudar a proteger sua organização, mas elas só serão eficazes se você usá-las.</span><span class="sxs-lookup"><span data-stu-id="966e1-111">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="966e1-112">Se você não usá-los, pode estar vulnerável a ataques.</span><span class="sxs-lookup"><span data-stu-id="966e1-112">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="966e1-113">Para proteger suas contas de administrador global, a Microsoft está aqui para ajudá-lo com instruções detalhadas para:</span><span class="sxs-lookup"><span data-stu-id="966e1-113">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="966e1-114">Crie contas de administrador global do Office 365 exclusivas e as use somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="966e1-114">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="966e1-115">Configure a autenticação multifator para suas contas de administrador global do Office 365, e use a forma mais segura de autenticação secundária.</span><span class="sxs-lookup"><span data-stu-id="966e1-115">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
> [!NOTE]
> <span data-ttu-id="966e1-116">Embora este artigo se concentre nas contas de administrador global, você deve considerar se as contas adicionais têm permissões amplas para acessar os dados em sua assinatura, como administrador de descoberta eletrônica ou administrador de segurança ou conformidade contas, devem ser protegidas da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="966e1-116">Although this article is focused on global administrator accounts, you should consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="966e1-117">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="966e1-117">Step 1.</span></span> <span data-ttu-id="966e1-118">Criar contas de administrador global do Office 365 exclusivas e usá-las somente quando necessário</span><span class="sxs-lookup"><span data-stu-id="966e1-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="966e1-119">Há relativamente poucas tarefas administrativas, como a atribuição de funções a contas de usuário, que exigem privilégios de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="966e1-120">Portanto, em vez de usar contas de usuário diárias às quais a função de administrador global tenha sido atribuída, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="966e1-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="966e1-121">Determine o conjunto de contas de usuário que foram atribuídas à função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="966e1-122">Você pode fazer isso com o Azure Active Directory (Azure AD), comando PowerShell para Graph:</span><span class="sxs-lookup"><span data-stu-id="966e1-122">You can do this with Azure Active (Azure AD) Directory PowerShell for Graph  command:</span></span>
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. <span data-ttu-id="966e1-123">Entre em sua assinatura do Office 365 com uma conta de usuário que tenha sido atribuída à função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="966e1-124">Crie pelo menos um e até um máximo de cinco contas de usuário de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="966e1-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="966e1-125">**Use senhas fortes pelo menos 12 caracteres.**</span><span class="sxs-lookup"><span data-stu-id="966e1-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="966e1-126">Consulte [criar uma senha forte](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="966e1-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="966e1-127">Armazene as senhas das novas contas em um local seguro.</span><span class="sxs-lookup"><span data-stu-id="966e1-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="966e1-128">Atribua a função de administrador global a cada uma das novas contas de usuário de administrador global dedicadas.</span><span class="sxs-lookup"><span data-stu-id="966e1-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="966e1-129">Saia do Office 365.</span><span class="sxs-lookup"><span data-stu-id="966e1-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="966e1-130">Entre com uma das novas contas de usuário do administrador global dedicado.</span><span class="sxs-lookup"><span data-stu-id="966e1-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="966e1-131">Para cada conta de usuário existente que tenha sido atribuída à função de administrador global da etapa 1:</span><span class="sxs-lookup"><span data-stu-id="966e1-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="966e1-132">Remova a função de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="966e1-133">Atribuir funções de administrador à conta que são apropriadas para a função e responsabilidade do trabalho do usuário.</span><span class="sxs-lookup"><span data-stu-id="966e1-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="966e1-134">Para obter mais informações sobre várias funções de administrador no Office 365, consulte [about admin Roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="966e1-134">For more information about various admin roles in Office 365, see [About admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).</span></span>
    
8. <span data-ttu-id="966e1-135">Saia do Office 365.</span><span class="sxs-lookup"><span data-stu-id="966e1-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="966e1-136">O resultado deve ser:</span><span class="sxs-lookup"><span data-stu-id="966e1-136">The result should be:</span></span>
  
- <span data-ttu-id="966e1-137">As únicas contas de usuários que possuem a função de administrador global em sua assinatura fazem parte do novo conjunto de contas de administradores globais dedicadas.</span><span class="sxs-lookup"><span data-stu-id="966e1-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="966e1-138">Verifique isso com o seguinte comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="966e1-138">Verify this with the following PowerShell command:</span></span>
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- <span data-ttu-id="966e1-139">Todas as outras contas de usuários comuns que gerenciam sua assinatura têm funções de administrador atribuídas que estão associadas às responsabilidades de trabalho deles.</span><span class="sxs-lookup"><span data-stu-id="966e1-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="966e1-140">Desse momento em diante, você entra com as contas de administrador global dedicadas apenas para tarefas que exigem privilégios de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="966e1-141">Todas as outras administração do Office 365 devem ser feitas por meio da atribuição de outras funções de administração às contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="966e1-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="966e1-142">Isso requer etapas adicionais para sair como sua conta de usuário diária e entrar com uma conta de administrador global dedicada.</span><span class="sxs-lookup"><span data-stu-id="966e1-142">This does require additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="966e1-143">Mas isso só precisa ser feito ocasionalmente para operações de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="966e1-144">Considere a recuperação de sua assinatura do Office 365 após uma violação de conta de administrador global exigir muito mais etapas.</span><span class="sxs-lookup"><span data-stu-id="966e1-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span>
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="966e1-145">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="966e1-145">Step 2.</span></span> <span data-ttu-id="966e1-146">Configurar a autenticação multifator para suas contas de administrador global do Office 365 exclusiva e usar a forma mais forte de autenticação secundária</span><span class="sxs-lookup"><span data-stu-id="966e1-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="966e1-147">A MFA (autenticação multifator) requer informações adicionais além do nome da conta e senha.</span><span class="sxs-lookup"><span data-stu-id="966e1-147">Multi-factor authentication (MFA) requires additional information beyond the account name and password.</span></span> <span data-ttu-id="966e1-148">O Office 365 suporta estes métodos de verificação:</span><span class="sxs-lookup"><span data-stu-id="966e1-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="966e1-149">Uma chamada telefônica</span><span class="sxs-lookup"><span data-stu-id="966e1-149">A phone call</span></span>
    
- <span data-ttu-id="966e1-150">Uma senha gerada aleatoriamente</span><span class="sxs-lookup"><span data-stu-id="966e1-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="966e1-151">Um cartão inteligente (físico ou virtual)</span><span class="sxs-lookup"><span data-stu-id="966e1-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="966e1-152">Um dispositivo biométrico</span><span class="sxs-lookup"><span data-stu-id="966e1-152">A biometric device</span></span>
    
<span data-ttu-id="966e1-153">Se você é uma pequena empresa que está usando contas de usuário armazenadas apenas na nuvem (modelo de identidade somente na nuvem), use estas etapas para configurar a MFA usando uma chamada telefônica ou um código de verificação de mensagem de texto enviado a um telefone inteligente:</span><span class="sxs-lookup"><span data-stu-id="966e1-153">If you are a small business that is using user accounts stored only in the cloud (the cloud-only identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="966e1-154">[Configurar a MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span><span class="sxs-lookup"><span data-stu-id="966e1-154">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="966e1-155">[Configurar a verificação em duas etapas para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada conta de administrador global dedicada para chamada telefônica ou mensagem de texto como o método de verificação.</span><span class="sxs-lookup"><span data-stu-id="966e1-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="966e1-156">Se você é uma organização maior que usa um modelo de identidade híbrida do Office 365, você tem mais opções de verificação.</span><span class="sxs-lookup"><span data-stu-id="966e1-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="966e1-157">Se você já tiver a infraestrutura de segurança em vigor para um método de autenticação secundário mais seguro, use estas etapas:</span><span class="sxs-lookup"><span data-stu-id="966e1-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="966e1-158">[Configurar a MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span><span class="sxs-lookup"><span data-stu-id="966e1-158">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="966e1-159">[Configure a verificação em duas etapas para o Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) para configurar cada conta de administrador global dedicada para o método de verificação apropriado.</span><span class="sxs-lookup"><span data-stu-id="966e1-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="966e1-160">Se a infraestrutura de segurança para o método de verificação mais forte desejado não estiver em vigor e estiver funcionando para o Office 365 MFA, é altamente recomendável que você configure contas de administrador global dedicadas com a MFA usando uma chamada telefônica ou uma mensagem de texto código de verificação enviado a um telefone inteligente para suas contas de administrador global como medida de segurança provisória.</span><span class="sxs-lookup"><span data-stu-id="966e1-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="966e1-161">Não deixe suas contas de administrador global dedicadas sem a proteção adicional fornecida pela MFA.</span><span class="sxs-lookup"><span data-stu-id="966e1-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="966e1-162">Para saber mais, consulte as informações sobre como [planejar a autenticação multifator para implantações do Office 365](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).</span><span class="sxs-lookup"><span data-stu-id="966e1-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).</span></span>
  
<span data-ttu-id="966e1-163">Para se conectar aos serviços do Office 365 com MFA e PowerShell, consulte estes artigos:</span><span class="sxs-lookup"><span data-stu-id="966e1-163">To connect to Office 365 services with MFA and PowerShell, see these articles:</span></span>

- [<span data-ttu-id="966e1-164">Office 365 PowerShell para contas de usuário, grupos e licenças</span><span class="sxs-lookup"><span data-stu-id="966e1-164">Office 365 PowerShell for user accounts, groups, and licenses</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [<span data-ttu-id="966e1-165">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="966e1-165">Exchange Online</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [<span data-ttu-id="966e1-166">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="966e1-166">SharePoint Online</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [<span data-ttu-id="966e1-167">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="966e1-167">Skype for Business Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="966e1-168">Proteções adicionais para organizações empresariais</span><span class="sxs-lookup"><span data-stu-id="966e1-168">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="966e1-169">Após as etapas 1 e 2, use esses métodos adicionais para garantir que sua conta de administrador global e a configuração que você executa usando a mesma sejam as mais seguras possíveis.</span><span class="sxs-lookup"><span data-stu-id="966e1-169">After steps 1 and 2, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation"></a><span data-ttu-id="966e1-170">Estação de trabalho de acesso privilegiado</span><span class="sxs-lookup"><span data-stu-id="966e1-170">Privileged access workstation</span></span>

<span data-ttu-id="966e1-171">Para garantir que a execução de tarefas altamente privilegiadas seja o mais segura possível, use uma estação de trabalho privilegiada (pata).</span><span class="sxs-lookup"><span data-stu-id="966e1-171">To ensure that the execution of highly privileged tasks is as secure as possible, use a privileged access workstation (PAW).</span></span> <span data-ttu-id="966e1-172">Um pata é um computador dedicado que é usado apenas para tarefas de configuração confidenciais, como a configuração do Office 365 que requer uma conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-172">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="966e1-173">Como este computador não é usado diariamente para navegação na Internet ou email, é melhor proteger contra ataques e ameaças da Internet.</span><span class="sxs-lookup"><span data-stu-id="966e1-173">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="966e1-174">Para obter instruções sobre como configurar um pata, consulte [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw).</span><span class="sxs-lookup"><span data-stu-id="966e1-174">For instructions on how to set up a PAW, see [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management"></a><span data-ttu-id="966e1-175">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="966e1-175">Azure AD Privileged Identity Management</span></span>

<span data-ttu-id="966e1-176">Em vez de ter suas contas de administrador global atribuídas permanentemente à função de administrador global, você pode usar o gerenciamento de identidade privilegiada do Azure AD para habilitar a atribuição sob demanda e Just-in-time da função de administrador global quando é necessários.</span><span class="sxs-lookup"><span data-stu-id="966e1-176">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD Privileged Identity Management (PIM) to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="966e1-177">Em vez de suas contas de administrador global serem um administrador permanente, elas se tornam administradores qualificados.</span><span class="sxs-lookup"><span data-stu-id="966e1-177">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="966e1-178">A função de administrador global está inativa até que alguém precise dela.</span><span class="sxs-lookup"><span data-stu-id="966e1-178">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="966e1-179">Em seguida, conclua um processo de ativação para adicionar a função de administrador global à conta de administrador global para uma quantidade de tempo predeterminada.</span><span class="sxs-lookup"><span data-stu-id="966e1-179">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="966e1-180">Quando o tempo expira, o PIM remove a função de administrador global da conta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-180">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="966e1-181">Usar o PIM e esse processo reduz significativamente a quantidade de tempo que suas contas de administrador global estão vulneráveis a ataques e uso por usuários mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="966e1-181">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="966e1-182">Para obter mais informações, consulte [Azure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span><span class="sxs-lookup"><span data-stu-id="966e1-182">For more information, see [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="966e1-183">O PIM está disponível com o Azure AD Premium P2, que acompanha o Microsoft 365 Enterprise E5 ou Enterprise Mobility + Security (EMS) e5, ou você pode adquirir licenças individuais para suas contas de administrador global.</span><span class="sxs-lookup"><span data-stu-id="966e1-183">PIM is available with Azure AD Premium P2, which is included with Microsoft 365 Enterprise E5 or Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="966e1-184">Software de gerenciamento de eventos e informações de segurança (SIEM) para log do Office 365</span><span class="sxs-lookup"><span data-stu-id="966e1-184">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="966e1-185">O software SIEM executado em um servidor realiza análises em tempo real de alertas e eventos de segurança criados por aplicativos e hardware de rede.</span><span class="sxs-lookup"><span data-stu-id="966e1-185">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="966e1-186">Para permitir que o seu servidor SIEM inclua alertas e eventos de segurança do Office 365 em suas funções de análise e relatórios, integre o Azure AD no SEIM.</span><span class="sxs-lookup"><span data-stu-id="966e1-186">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate Azure AD into you SEIM.</span></span> <span data-ttu-id="966e1-187">Confira [introdução à integração de logs do Azure](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span><span class="sxs-lookup"><span data-stu-id="966e1-187">See [Introduction to Azure Log Integration](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="966e1-188">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="966e1-188">Next step</span></span>

<span data-ttu-id="966e1-189">Se você estiver configurando a identidade para sua assinatura do Office 365, consulte:</span><span class="sxs-lookup"><span data-stu-id="966e1-189">If you're setting up identity for your Office 365 subscription, see:</span></span>

- <span data-ttu-id="966e1-190">[Identidades somente na nuvem](cloud-only-identities.md) se você estiver usando a identidade somente na nuvem</span><span class="sxs-lookup"><span data-stu-id="966e1-190">[Cloud-only identities](cloud-only-identities.md) if you're using cloud-only identity</span></span>
- <span data-ttu-id="966e1-191">[Preparar a sincronização de diretórios](prepare-for-directory-synchronization.md) se você estiver usando a identidade híbrida</span><span class="sxs-lookup"><span data-stu-id="966e1-191">[Prepare for directory synchronization](prepare-for-directory-synchronization.md) if you're using hybrid identity</span></span>

  
## <a name="see-also"></a><span data-ttu-id="966e1-192">Confira também</span><span class="sxs-lookup"><span data-stu-id="966e1-192">See also</span></span>

<span data-ttu-id="966e1-193">[Mapa de segurança do Office 365](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span><span class="sxs-lookup"><span data-stu-id="966e1-193">[Office 365 security roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span></span>
