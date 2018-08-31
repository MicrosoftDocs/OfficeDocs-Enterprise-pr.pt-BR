---
title: Preparar um domínio não roteáveis para sincronização de diretórios
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Saiba o que fazer se você tiver um domínio não-routale associado com os usuários no local antes de sincronizar com o Office 365.
ms.openlocfilehash: 62779ba879522177ba15a491644ab42f5961ece0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539407"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="46343-103">Preparar um domínio não roteáveis para sincronização de diretórios</span><span class="sxs-lookup"><span data-stu-id="46343-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="46343-p101">Quando você sincronizar seu diretório local com o Office 365, você precisa ter um domínio verificado no Azure Active Directory. Somente o usuário Principal nomes (UPN) que estão associados ao domínio local são sincronizados. No entanto, qualquer UPN que contém um domínio não roteáveis, por exemplo. local (como billa@contoso.local), será sincronizada com uma. domínio onmicrosoft.com (como billa@contoso.onmicrosoft.com).</span><span class="sxs-lookup"><span data-stu-id="46343-p101">When you synchronize your on-premises directory with Office 365 you have to have a verified domain in Azure Active Directory. Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized. However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="46343-107">Se você usar atualmente um domínio. local para suas contas de usuário no Active Directory, é recomendável que você alterá-las para usar um domínio verificado (como billa@contoso.com) para sincronizar corretamente no seu domínio do Office 365.</span><span class="sxs-lookup"><span data-stu-id="46343-107">If you currently use a .local domain for your user accounts in Active Directory it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Office 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="46343-108">E se eu tiver apenas um domínio de local. local?</span><span class="sxs-lookup"><span data-stu-id="46343-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="46343-p102">A ferramenta mais recente, que você pode usar para sincronizar seu Active Directory para o Windows Azure Active Directory é nomeada Connect do Azure AD. Para obter mais informações, consulte [integrando suas identidades no local com o Windows Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624168).</span><span class="sxs-lookup"><span data-stu-id="46343-p102">The most recent tool you can use for synchronizing your Active Directory to Azure Active Directory is named Azure AD Connect. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=624168).</span></span>
  
<span data-ttu-id="46343-p103">Conectar do Azure AD sincroniza UPN e a senha dos usuários para que os usuários podem assinar com as mesmas credenciais que usam o local. No entanto, Connect do Azure AD sincroniza somente os usuários a domínios que são verificados pelo Office 365. Isso significa que o domínio também sejam verificado pelo Windows Azure Active Directory porque identidades do Office 365 são gerenciadas pelo Windows Azure Active Directory. Em outras palavras, o domínio deve ser um domínio da Internet válido (por exemplo, .com,. org, .net,. us, etc.). Se o seu Active Directory interna usa apenas um domínio não roteáveis (por exemplo,. local), isso possivelmente não pode corresponder ao domínio verificado que você tiver no Office 365. Para resolver esse problema alterando seu domínio primário no seu Active Directory local ou adicionando um ou mais sufixos de nome UPN.</span><span class="sxs-lookup"><span data-stu-id="46343-p103">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises. However, Azure AD Connect only synchronizes users to domains that are verified by Office 365. This means that the domain also is verified by Azure Active Directory because Office 365 identities are managed by Azure Active Directory. In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.). If your internal Active Directory only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Office 365. You can fix this issue by either changing your primary domain in your on premises Active Directory, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="46343-117">**Alterar seu domínio primário**</span><span class="sxs-lookup"><span data-stu-id="46343-117">**Change your primary domain**</span></span>

<span data-ttu-id="46343-p104">Altere seu domínio primário para um domínio que você tiver verificado no Office 365, por exemplo, contoso.com. Cada usuário que possui a Contoso do domínio é atualizado para contoso.com. Para obter instruções, consulte [Como o domínio renomear funciona](https://go.microsoft.com/fwlink/p/?LinkId=624174). No entanto, esse é um processo muito envolvido, e uma solução mais fácil é [sufixos de UPN adicionar e atualizar seus usuários a eles](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), conforme mostrado na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="46343-p104">Change your primary domain to a domain you have verified in Office 365, for example, contoso.com. Every user that has the domain contoso.local is then updated to contoso.com. For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174). This is a very involved process, however, and an easier solution is to [Add UPN suffixes and update your users to them](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), as shown in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="46343-122">**Adicionar sufixos UPN e atualizar seus usuários a eles**</span><span class="sxs-lookup"><span data-stu-id="46343-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="46343-p105">Você pode resolver o problema. local registrando novo sufixo UPN ou sufixos no Active Directory para corresponder ao domínio (ou domínios) verificado no Office 365. Após registrar o novo sufixo, você pode atualizar o usuário UPNs substituir. o local com o novo nome de domínio, por exemplo, para que uma conta de usuário se parece com billa@contoso.com.</span><span class="sxs-lookup"><span data-stu-id="46343-p105">You can solve the .local problem by registering new UPN suffix or suffixes in Active Directory to match the domain (or domains) you verified in Office 365. After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="46343-125">Depois de ter atualizado os UPNs para usar ao domínio verificado, você estará pronto para sincronizar seu Active Directory no local com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="46343-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises Active Directory with Office 365.</span></span>
  
 <span data-ttu-id="46343-126">**Etapa 1: Adicionar o novo sufixo UPN**</span><span class="sxs-lookup"><span data-stu-id="46343-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="46343-127">No servidor que executa o serviços de domínio Active Directory (AD DS), no Gerenciador de servidores escolher **Ferramentas** \> **domínios do Active Directory e relações de confiança**.</span><span class="sxs-lookup"><span data-stu-id="46343-127">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="46343-128">**Ou, se você não tiver o Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="46343-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="46343-129">Pressione a **tecla do Windows + R** para abrir a caixa de diálogo **Executar** e digite msc e escolha **Okey**.</span><span class="sxs-lookup"><span data-stu-id="46343-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![Escolha domínios do Active Directory e relações de confiança.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="46343-131">Na janela de **domínios do Active Directory e relações de confiança** , do mouse em **domínios do Active Directory e relações de confiança**e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="46343-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![Clique com o botão ActiveDirectory domínios e relações de confiança e escolha Propriedades](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="46343-133">Na guia **Sufixos UPN** , na caixa **Sufixos de nome UPN alternativo** , digite seu novo sufixo UPN ou sufixos e escolha **Adicionar** \> **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="46343-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![Adicionar um novo sufixo UPN](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="46343-135">Escolha **Okey** quando você terminar de adicionar sufixos.</span><span class="sxs-lookup"><span data-stu-id="46343-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="46343-136">**Etapa 2: Alterar o sufixo UPN para usuários existentes**</span><span class="sxs-lookup"><span data-stu-id="46343-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="46343-137">No servidor que executa o serviços de domínio Active Directory (AD DS), no Gerenciador de servidores escolher **Ferramentas** \> **e computadores do Active Directory Active Directory Users**.</span><span class="sxs-lookup"><span data-stu-id="46343-137">On the server that Active Directory Domain Services (AD DS) runs on, in the Server Manager choose **Tools** \> **Active Directory Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="46343-138">**Ou, se você não tiver o Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="46343-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="46343-139">Pressione a **tecla do Windows + R** para abrir a caixa de diálogo **Executar** e digite DSA. msc e clique em **Okey**</span><span class="sxs-lookup"><span data-stu-id="46343-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="46343-140">Selecione um usuário, com o botão direito e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="46343-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="46343-141">Na guia **conta** , na lista suspensa sufixo UPN, escolha Novo sufixo UPN e escolha **Okey**.</span><span class="sxs-lookup"><span data-stu-id="46343-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![Adicionar um novo sufixo UPN de um usuário](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="46343-143">Conclua estas etapas para cada usuário.</span><span class="sxs-lookup"><span data-stu-id="46343-143">Complete these steps for every user.</span></span>
    
    <span data-ttu-id="46343-144">Como alternativa você pode atualizar em massa sufixos de UPN [você também pode usar o Windows PowerShell para alterar o sufixo UPN para todos os usuários](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span><span class="sxs-lookup"><span data-stu-id="46343-144">Alternately you can bulk update the UPN suffixes [You can also use Windows PowerShell to change the UPN suffix for all users](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).</span></span>
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="46343-145">**Você também pode usar o Windows PowerShell para alterar o sufixo UPN para todos os usuários**</span><span class="sxs-lookup"><span data-stu-id="46343-145">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="46343-p106">Se você tiver muitos usuários para atualizar, é mais fácil usar o Windows PowerShell. O exemplo a seguir usa os cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) e [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) para alterar todos os sufixos de Contoso para contoso.com.</span><span class="sxs-lookup"><span data-stu-id="46343-p106">If you have a lot of users to update, it is easier to use Windows PowerShell. The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="46343-148">Execute os seguintes comandos do Windows PowerShell para atualizar todos os sufixos de Contoso para contoso.com:</span><span class="sxs-lookup"><span data-stu-id="46343-148">Run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
<span data-ttu-id="46343-149">Consulte o [módulo do Active Directory Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=624314) para saber mais sobre como usar o Windows PowerShell no Active Directory.</span><span class="sxs-lookup"><span data-stu-id="46343-149">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in Active Directory.</span></span> 

