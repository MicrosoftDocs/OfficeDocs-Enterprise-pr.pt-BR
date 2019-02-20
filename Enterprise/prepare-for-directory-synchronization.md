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
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085100"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="c5deb-103">Prepare-se para provisionar usuários por meio da sincronização de diretório para o Office 365</span><span class="sxs-lookup"><span data-stu-id="c5deb-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="c5deb-p101">O provisionamento de usuários com a sincronização de diretórios requer mais planejamento e preparação do que simplesmente gerenciar sua conta corporativa ou de estudante diretamente no Office 365. As tarefas adicionais de planejamento e preparação são necessárias para garantir que o Active Directory local seja sincronizado adequadamente com o Azure Active Directory. Os benefícios adicionados à sua organização incluem:</span><span class="sxs-lookup"><span data-stu-id="c5deb-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="c5deb-107">Reduzir os programas administrativos em sua organização</span><span class="sxs-lookup"><span data-stu-id="c5deb-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="c5deb-108">Opcionalmente, habilitando o cenário de logon único</span><span class="sxs-lookup"><span data-stu-id="c5deb-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="c5deb-109">Automatizar as alterações de conta no Office 365</span><span class="sxs-lookup"><span data-stu-id="c5deb-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="c5deb-110">Para obter mais informações sobre as vantagens de usar a sincronização de diretório, consulte [mapa de sincronização de diretório]( https://go.microsoft.com/fwlink/p/?LinkId=525398) e [noções básicas sobre a identidade do Office 365 e o Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="c5deb-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="c5deb-111">Para determinar qual cenário é o melhor para a sua organização, revise a [comparação de ferramentas de integração de diretórios](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span><span class="sxs-lookup"><span data-stu-id="c5deb-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="c5deb-112">Tarefas de limpeza de diretório</span><span class="sxs-lookup"><span data-stu-id="c5deb-112">Directory cleanup tasks</span></span>

<span data-ttu-id="c5deb-113">Antes de começar a sincronizar seu diretório, você precisa limpar o diretório.</span><span class="sxs-lookup"><span data-stu-id="c5deb-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="c5deb-114">Revise também os [atributos sincronizados com o Azure Active Directory pelo Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span><span class="sxs-lookup"><span data-stu-id="c5deb-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="c5deb-p102">Se você não executar a limpeza de diretório antes de sincronizar, pode haver um efeito negativo significativo no processo de implantação. Pode levar dias ou até mesmo semanas para passar pelo ciclo de sincronização de diretórios, identificar erros e ressincronizar.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="c5deb-117">No diretório local, conclua as seguintes tarefas de limpeza:</span><span class="sxs-lookup"><span data-stu-id="c5deb-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="c5deb-118">Verifique se cada usuário ao qual serão atribuídas ofertas de serviços do Office 365 tem um endereço de email válido e exclusivo no atributo **proxyAddresses**.</span><span class="sxs-lookup"><span data-stu-id="c5deb-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="c5deb-119">Remover valores duplicados no atributo **proxyAddresses**.</span><span class="sxs-lookup"><span data-stu-id="c5deb-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="c5deb-p103">Se possível, certifique-se de que cada usuário ao qual serão atribuídas ofertas de serviço do Office 365 tem um valor válido e exclusivo para o atributo **userPrincipalName** no objeto **User** do usuário. Para obter a melhor experiência de sincronização, verifique se o UPN do Active Directory local corresponde ao UPN da nuvem. Se um usuário não tiver um valor para o atributo **userPrincipalName** , o objeto de **usuário** deverá conter um valor válido e exclusivo para o atributo **sAMAccountName** . Remova os valores duplicados no atributo **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="c5deb-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="c5deb-124">Para garantir o melhor uso da lista de endereços global (GAL), verifique se as informações nos seguintes atributos estão corretas:</span><span class="sxs-lookup"><span data-stu-id="c5deb-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="c5deb-125">givenName </span><span class="sxs-lookup"><span data-stu-id="c5deb-125">givenName</span></span>
  - <span data-ttu-id="c5deb-126">surname</span><span class="sxs-lookup"><span data-stu-id="c5deb-126">surname</span></span>
  - <span data-ttu-id="c5deb-127">displayName</span><span class="sxs-lookup"><span data-stu-id="c5deb-127">displayName</span></span>
  - <span data-ttu-id="c5deb-128">Cargo</span><span class="sxs-lookup"><span data-stu-id="c5deb-128">Job Title</span></span>
  - <span data-ttu-id="c5deb-129">Departamento</span><span class="sxs-lookup"><span data-stu-id="c5deb-129">Department</span></span>
  - <span data-ttu-id="c5deb-130">Escritório</span><span class="sxs-lookup"><span data-stu-id="c5deb-130">Office</span></span>
  - <span data-ttu-id="c5deb-131">Telefone Comercial</span><span class="sxs-lookup"><span data-stu-id="c5deb-131">Office Phone</span></span>
  - <span data-ttu-id="c5deb-132">Celular</span><span class="sxs-lookup"><span data-stu-id="c5deb-132">Mobile Phone</span></span>
  - <span data-ttu-id="c5deb-133">Número de Fax</span><span class="sxs-lookup"><span data-stu-id="c5deb-133">Fax Number</span></span>
  - <span data-ttu-id="c5deb-134">Endereço</span><span class="sxs-lookup"><span data-stu-id="c5deb-134">Street Address</span></span>
  - <span data-ttu-id="c5deb-135">Cidade</span><span class="sxs-lookup"><span data-stu-id="c5deb-135">City</span></span>
  - <span data-ttu-id="c5deb-136">Estado ou Província</span><span class="sxs-lookup"><span data-stu-id="c5deb-136">State or Province</span></span>
  - <span data-ttu-id="c5deb-137">CEP ou Código Postal</span><span class="sxs-lookup"><span data-stu-id="c5deb-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="c5deb-138">País ou Região</span><span class="sxs-lookup"><span data-stu-id="c5deb-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="c5deb-139">Preparação de objetos e atributos de diretório</span><span class="sxs-lookup"><span data-stu-id="c5deb-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="c5deb-p104">A sincronização de diretório com êxito entre o diretório local e o Office 365 requer que seus atributos de diretório local sejam preparados corretamente. Por exemplo, você precisa garantir que caracteres específicos não sejam usados em determinados atributos que são sincronizados com o ambiente do Office 365. Caracteres inEsperados não causam a sincronização de diretório, mas podem retornar um aviso. Caracteres inVálidos causarão falha na sincronização do diretório.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="c5deb-p105">A sincronização de diretórios também falhará se alguns dos seus usuários do Active Directory tiverem um ou mais atributos duplicados. Cada usuário deve ter atributos exclusivos.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="c5deb-146">Os atributos que você precisa preparar estão listados aqui:</span><span class="sxs-lookup"><span data-stu-id="c5deb-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="c5deb-147">**Observação:** Você também pode usar a [ferramenta IdFix](install-and-run-idfix.md) para tornar esse processo muito mais fácil.</span><span class="sxs-lookup"><span data-stu-id="c5deb-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="c5deb-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="c5deb-148">**displayName**</span></span>
    
  - <span data-ttu-id="c5deb-149">Se o atributo existe no objeto do usuário, ele será sincronizado com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="c5deb-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="c5deb-p106">Se esse atributo existir no objeto de usuário, deve haver um valor para ela. Ou seja, o atributo não deve estar em branco.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="c5deb-152">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="c5deb-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="c5deb-153">\*\*givenName \*\*</span><span class="sxs-lookup"><span data-stu-id="c5deb-153">**givenName**</span></span>
    
  - <span data-ttu-id="c5deb-154">Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não necessitará dele ou irá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="c5deb-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="c5deb-155">Número máximo de caracteres: 64</span><span class="sxs-lookup"><span data-stu-id="c5deb-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="c5deb-156">**email**</span><span class="sxs-lookup"><span data-stu-id="c5deb-156">**mail**</span></span>
    
  - <span data-ttu-id="c5deb-157">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="c5deb-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c5deb-p107">Se houver valores duplicados, o primeiro usuário com o valor será sincronizado. Os usuários subsequentes não aparecerão no Office 365. Você deve modificar o valor no Office 365 ou modificar os dois valores no diretório local para que ambos os usuários apareçam no Office 365.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="c5deb-161">**mailNickname** (alias do Exchange)</span><span class="sxs-lookup"><span data-stu-id="c5deb-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="c5deb-162">O valor do atributo não pode começar com um ponto (.).</span><span class="sxs-lookup"><span data-stu-id="c5deb-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="c5deb-163">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="c5deb-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="c5deb-164">\*\*proxyAddresses \*\*</span><span class="sxs-lookup"><span data-stu-id="c5deb-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="c5deb-165">Atributo de vários valores</span><span class="sxs-lookup"><span data-stu-id="c5deb-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="c5deb-166">A quantidade máxima de caracteres por valor: 256</span><span class="sxs-lookup"><span data-stu-id="c5deb-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="c5deb-167">O valor do atributo não deve conter um espaço.</span><span class="sxs-lookup"><span data-stu-id="c5deb-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="c5deb-168">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="c5deb-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="c5deb-169">Caracteres inVálidos: \< \> (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="c5deb-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="c5deb-170">Observe que os caracteres inválidos se aplicam aos caracteres após o delimitador de tipo e ":", de modo que SMTP:User@contso.com seja permitido, mas SMTP:user:M@contoso.com não.</span><span class="sxs-lookup"><span data-stu-id="c5deb-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="c5deb-p108">Todos os endereços SMTP (Simple Mail Transport Protocol) devem estar em conformidade com os padrões de mensagens de email. Se houver endereços indesejados ou duplicados, consulte o tópico de ajuda [removendo endereços de proxy duplicados e indesejados no Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span><span class="sxs-lookup"><span data-stu-id="c5deb-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="c5deb-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="c5deb-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="c5deb-174">Número máximo de caracteres: 20</span><span class="sxs-lookup"><span data-stu-id="c5deb-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="c5deb-175">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="c5deb-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="c5deb-p109">Caracteres inVálidos: [\ "|, \< \> /: + =;? \* ]</span><span class="sxs-lookup"><span data-stu-id="c5deb-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="c5deb-178">Se um usuário tiver um atributo **sAMAccountName** inválido, mas tiver um atributo **userPrincipalName** válido, a conta de usuário será criada no Office 365.</span><span class="sxs-lookup"><span data-stu-id="c5deb-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="c5deb-179">Se **sAMAccountName** e **userPrincipalName** forem inválidos, o atributo **userPrincipalName** do Active Directory local deverá ser atualizado.</span><span class="sxs-lookup"><span data-stu-id="c5deb-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="c5deb-180">**sn** (sobrenome)</span><span class="sxs-lookup"><span data-stu-id="c5deb-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="c5deb-181">Se o atributo existir no objeto do usuário, ele será sincronizado com o Office 365, mas o Office 365 não necessitará dele ou irá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="c5deb-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="c5deb-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="c5deb-182">**targetAddress**</span></span>
    
    <span data-ttu-id="c5deb-p110">É necessário que o atributo **targetAddress** (por exemplo, SMTP:Tom@contoso.com) preenchido para o usuário deve aparecer na GAL do Office 365. Em cenários de migração de mensagens de terceiros, isso exigiria a extensão de esquema do Office 365 para o diretório local. A extensão de esquema do Office 365 também adicionaria outros atributos úteis para gerenciar objetos do Office 365 que são preenchidos usando uma ferramenta de sincronização de diretório do diretório local. Por exemplo, o atributo **msExchHideFromAddressLists** para gerenciar caixas de correio ou grupos de distribuição ocultos seria adicionado.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="c5deb-187">Número máximo de caracteres: 256</span><span class="sxs-lookup"><span data-stu-id="c5deb-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="c5deb-188">O valor do atributo não deve conter um espaço.</span><span class="sxs-lookup"><span data-stu-id="c5deb-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="c5deb-189">O valor do atributo deve ser exclusivo dentro do diretório.</span><span class="sxs-lookup"><span data-stu-id="c5deb-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="c5deb-190">Caracteres inVálidos \< \> : \ (); , [ ] "</span><span class="sxs-lookup"><span data-stu-id="c5deb-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="c5deb-191">Todos os endereços no Protocolo SMTP devem estar em conformidade com os padrões de emails.</span><span class="sxs-lookup"><span data-stu-id="c5deb-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="c5deb-192">**Principal**</span><span class="sxs-lookup"><span data-stu-id="c5deb-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="c5deb-p111">O atributo **userPrincipalName** deve estar no formato de entrada no estilo da Internet, onde o nome do usuário é seguido pelo sinal de arroba (@) e um nome de domínio: por exemplo, User@contoso.com. Todos os endereços SMTP (Simple Mail Transport Protocol) devem estar em conformidade com os padrões de mensagens de email.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="c5deb-p112">A quantidade máxima de caracteres para o atributo **userPrincipalName** é 113. Permite-se uma quantidade específica de caracteres antes e depois do sinal (@), como a seguir:</span><span class="sxs-lookup"><span data-stu-id="c5deb-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="c5deb-197">Número máximo de caracteres para o nome de usuário antes do sinal de arroba (@): 64</span><span class="sxs-lookup"><span data-stu-id="c5deb-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="c5deb-198">Número máximo de caracteres para o nome de domínio após o sinal de arroba (@): 48</span><span class="sxs-lookup"><span data-stu-id="c5deb-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="c5deb-p113">Caracteres inVálidos: &amp; \* \% +/=? { } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="c5deb-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="c5deb-201">Um trema também é um caractere inválido.</span><span class="sxs-lookup"><span data-stu-id="c5deb-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="c5deb-202">O caractere @ é necessário em cada valor **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="c5deb-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="c5deb-203">O caractere @ não pode ser o primeiro caractere em cada valor **userPrincipalName**.</span><span class="sxs-lookup"><span data-stu-id="c5deb-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="c5deb-204">O nome de usuário não pode terminar com um ponto (.), um&amp;e comercial (), um espaço ou um sinal de arroba (@).</span><span class="sxs-lookup"><span data-stu-id="c5deb-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="c5deb-205">O nome de usuário não pode conter espaços.</span><span class="sxs-lookup"><span data-stu-id="c5deb-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="c5deb-206">Domínios roteáveis devem ser usados; por exemplo, domínios locais ou internos não podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="c5deb-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="c5deb-207">Unicode é convertido para caracteres sublinhados.</span><span class="sxs-lookup"><span data-stu-id="c5deb-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="c5deb-208">**userPrincipalName** não pode conter valores duplicados no diretório.</span><span class="sxs-lookup"><span data-stu-id="c5deb-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="c5deb-209">Preparar o atributo userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="c5deb-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="c5deb-p114">O Active Directory é projetado para permitir que os usuários finais em sua organização entrem em seu diretório usando **sAMAccountName** ou **userPrincipalName**. Da mesma forma, os usuários finais podem entrar no Office 365 usando o nome principal do usuário (UPN) de sua conta corporativa ou de estudante. A sincronização de diretório tenta criar novos usuários no Active Directory do Azure usando o mesmo UPN que está no seu diretório local. O UPN é formatado como um endereço de email.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="c5deb-p115">No Office 365, o UPN é o atributo padrão usado para gerar o endereço de email. É fácil obter **userPrincipalName** (no local e no Azure Active Directory) e o endereço de email principal no **proxyAddresses** definido como valores diferentes. Quando estão definidas como valores diferentes, pode haver confusão para administradores e usuários finais.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="c5deb-p116">É melhor alinhar esses atributos para reduzir a confusão. Para atender aos requisitos de logon único com os serviços de Federação do Active Directory (AD FS) 2,0, você precisa garantir que os UPNs no Azure Active Directory e sua correspondência do Active Directory local e estejam usando um namespace de domínio válido.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="c5deb-219">Adicionar um sufixo UPN alternativo ao AD DS</span><span class="sxs-lookup"><span data-stu-id="c5deb-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="c5deb-p117">Talvez seja necessário adicionar um sufixo UPN alternativo para associar as credenciais corporativas do usuário ao ambiente do Office 365. Um sufixo UPN é a parte de um UPN à direita do caractere @. Os UPNs usados para logon único podem conter letras, números, pontos, traços e sublinhados, mas nenhum outro tipo de caractere.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="c5deb-223">Para obter mais informações sobre como adicionar um sufixo UPN alternativo ao Active Directory, consulte [preparar para a sincronização de diretórios]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span><span class="sxs-lookup"><span data-stu-id="c5deb-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="c5deb-224">Corresponder ao UPN local com o UPN do Office 365</span><span class="sxs-lookup"><span data-stu-id="c5deb-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="c5deb-p118">Se você já configurou a sincronização de diretórios, o UPN do usuário para Office 365 pode não corresponder ao UPN local do usuário que está definido no serviço de diretório local. Isso pode ocorrer quando um usuário recebeu uma licença antes da verificação do domínio. Para corrigir isso, use o [PowerShell para corrigir](https://go.microsoft.com/fwlink/p/?LinkId=396730) o UPN duplicado para atualizar o UPN do usuário para garantir que o UPN do Office 365 corresponda ao nome de usuário e ao domínio da empresa. Se você estiver atualizando o UPN no serviço de diretório local e quiser que ele seja sincronizado com a identidade do Azure Active Directory, será necessário remover a licença do usuário no Office 365 antes de realizar as alterações no local.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="c5deb-229">Consulte também [como preparar um domínio não roteável (como o domínio. local) para a sincronização de diretórios](prepare-a-non-routable-domain-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="c5deb-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="c5deb-230">Ferramentas de integração de diretórios</span><span class="sxs-lookup"><span data-stu-id="c5deb-230">Directory integration tools</span></span>

<span data-ttu-id="c5deb-p119">A sincronização de diretórios é a sincronização de objetos de diretório (usuários, grupos e contatos) do seu ambiente do Active Directory local para a infraestrutura de diretório do Office 365, Azure Active Directory. Consulte [ferramentas de integração de diretórios](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obter uma lista das ferramentas disponíveis e sua funcionalidade. A ferramenta recomendada é [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Para obter mais informações sobre o Azure Active Directory Connect, confira [integração de suas identidades locais com o Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span><span class="sxs-lookup"><span data-stu-id="c5deb-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="c5deb-p120">Quando as contas de usuário são sincronizadas com o diretório do Office 365 pela primeira vez, elas são marcadas como não ativadas. Eles não podem enviar nem receber emails e não consomem licenças de assinatura. Quando estiver pronto para atribuir assinaturas do Office 365 a usuários específicos, você deverá selecionar e ativá-las atribuindo [licenças aos usuários no Office 365 para empresas](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span><span class="sxs-lookup"><span data-stu-id="c5deb-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="c5deb-p121">Você também pode usar o [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) para atribuir licenças. Veja [como usar o PowerShell para atribuir automaticamente licenças aos usuários do Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) para uma solução automatizada.</span><span class="sxs-lookup"><span data-stu-id="c5deb-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>