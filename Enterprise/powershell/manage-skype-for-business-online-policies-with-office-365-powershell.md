---
title: "Gerenciar Skype para políticas Business Online com o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "Resumo: Usar o PowerShell do Office 365 para gerenciar sua Skype para Business Online propriedades de conta de usuário com políticas."
ms.openlocfilehash: 9b3877d2680b2b36d155cb5dd2a69fa21c972fe3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="250de-103">Gerenciar Skype para políticas Business Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="250de-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="250de-104">**Resumo:** Use o Office 365 PowerShell para gerenciar sua Skype para Business Online propriedades de conta de usuário com políticas.</span><span class="sxs-lookup"><span data-stu-id="250de-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="250de-105">Para gerenciar várias propriedades da conta de usuário para Skype para Business Online, você deve especificá-las como propriedades das políticas com o Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="250de-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="250de-106">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="250de-106">Before you begin</span></span>

<span data-ttu-id="250de-107">Use essas instruções para obter configurado para executar os comandos (ignore as etapas que você já tenha concluído):</span><span class="sxs-lookup"><span data-stu-id="250de-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="250de-108">Baixe e instale o [Skype para módulo Business Connector Online](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="250de-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="250de-109">Abra um prompt de comando do Windows PowerShell e execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="250de-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="250de-110">Quando solicitado, insira seu Skype para Business Online nome da conta de administrador e senha.</span><span class="sxs-lookup"><span data-stu-id="250de-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="250de-111">Gerenciar políticas de conta de usuário</span><span class="sxs-lookup"><span data-stu-id="250de-111">Manage user account policies</span></span>

<span data-ttu-id="250de-p101">Muitos Skype para Business Online propriedades da conta de usuário são definidas por meio de políticas. Políticas são simplesmente coleções de configurações que podem ser aplicadas a um ou mais usuários. Dê uma olhada em como a uma diretiva tiver sido configurada, você pode executar esse comando de exemplo para a política de FederationAndPICDefault:</span><span class="sxs-lookup"><span data-stu-id="250de-p101">Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="250de-115">Por sua vez, você deve obter algo semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="250de-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="250de-p102">Neste exemplo, os valores nessa diretiva determinam o que um uso pode ou não podem fazer quando se trata de se comunicar com usuários federados. Por exemplo, a propriedade EnableOutsideAccess deve ser definida como True para um usuário sejam capazes de se comunicar com pessoas fora da organização. Observe que essa propriedade não aparecem no Centro de administração do Office 365. Em vez disso, a propriedade é definida automaticamente como True ou False com base em outras seleções feitas. As duas outras propriedades de interesse são:</span><span class="sxs-lookup"><span data-stu-id="250de-p102">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users. For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization. Note that this property does not appear in the Office 365 Admin center. Instead, the property is automatically set to True or False based on the other selections that you make. The other two properties of interest are:</span></span>
  
- <span data-ttu-id="250de-121">**EnableFederationAccess** indica se o usuário pode se comunicar com pessoas de domínios federados.</span><span class="sxs-lookup"><span data-stu-id="250de-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="250de-122">**EnablePublicCloudAccess** indica se o usuário pode se comunicar com usuários do Windows Live.</span><span class="sxs-lookup"><span data-stu-id="250de-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="250de-p103">Portanto, você não alterar diretamente as propriedades relacionadas à Federação em contas de usuário (por exemplo, **Set-CsUser-EnableFederationAccess $True**). Em vez disso, você atribuir uma conta uma política de acesso externo que tem os valores de propriedade desejada pré-configurados. Se quisermos que um usuário seja capaz de se comunicar com usuários federados e usuários do Windows Live, essa conta de usuário deve ser atribuída a uma política que permite esses tipos de comunicação.</span><span class="sxs-lookup"><span data-stu-id="250de-p103">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="250de-126">Se você deseja saber se ou não alguém pode se comunicar com usuários de fora da organização, você precisa:</span><span class="sxs-lookup"><span data-stu-id="250de-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="250de-127">Determinar qual política de acesso externo foi atribuída a esse usuário.</span><span class="sxs-lookup"><span data-stu-id="250de-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="250de-128">Determinar quais recursos são ou não permitidos por essa política.</span><span class="sxs-lookup"><span data-stu-id="250de-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="250de-129">Por exemplo, você pode fazer isso usando este comando:</span><span class="sxs-lookup"><span data-stu-id="250de-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="250de-130">Esse comando localiza a política atribuída ao usuário, em seguida, localiza os recursos habilitados ou desabilitados dentro dessa política.</span><span class="sxs-lookup"><span data-stu-id="250de-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="250de-p104">Observe que não há nenhuma cmdlets para criando ou modificando diretivas. Você deve usar as políticas previamente fornecidas pelo Office 365. Se você quiser dar uma olhada as políticas diferentes disponíveis, você pode usar estes comandos:</span><span class="sxs-lookup"><span data-stu-id="250de-p104">Note that there are no cmdlets for creating or for modifying policies. You must use the policies pre-supplied by Office 365. If you want to take a look at the different policies available, you can use these commands:</span></span>
  
- <span data-ttu-id="250de-134">Get-CsClientPolicy</span><span class="sxs-lookup"><span data-stu-id="250de-134">Get-CsClientPolicy</span></span>       
- <span data-ttu-id="250de-135">Get-CsConferencingPolicy</span><span class="sxs-lookup"><span data-stu-id="250de-135">Get-CsConferencingPolicy</span></span>        
- <span data-ttu-id="250de-136">Get-CsDialPlan</span><span class="sxs-lookup"><span data-stu-id="250de-136">Get-CsDialPlan</span></span>            
- <span data-ttu-id="250de-137">Get-CsExternalAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="250de-137">Get-CsExternalAccessPolicy</span></span>                         
- <span data-ttu-id="250de-138">Get-CsHostedVoicemailPolicy</span><span class="sxs-lookup"><span data-stu-id="250de-138">Get-CsHostedVoicemailPolicy</span></span>                        
- <span data-ttu-id="250de-139">Get-CsPresencePolicy</span><span class="sxs-lookup"><span data-stu-id="250de-139">Get-CsPresencePolicy</span></span>                               
- <span data-ttu-id="250de-140">Get-CsVoicePolicy</span><span class="sxs-lookup"><span data-stu-id="250de-140">Get-CsVoicePolicy</span></span>                                  

> [!NOTE]
> <span data-ttu-id="250de-p105">Um Skype para Business Online plano de discagem é uma diretiva em todos os aspectos, exceto o nome. O nome "plano de discagem" foi escolhido em vez, por exemplo, "diretiva de discagem" para fornecer compatibilidade com versões anteriores ao Office Communications Server e o Exchange.</span><span class="sxs-lookup"><span data-stu-id="250de-p105">A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="250de-143">Por exemplo, para considerar todas as políticas de voz disponíveis para uso, execute este comando:</span><span class="sxs-lookup"><span data-stu-id="250de-143">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="250de-p106">Isso retorna uma lista de todas as políticas de voz disponíveis para você. Tenha em mente, entretanto, que nem todas as políticas podem ser atribuídas a todos os usuários. Isso acontece devido à várias restrições envolvendo a localização geográfica e de licenciamento. (Os chamados "[local de uso](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") Se desejar saber as políticas de acesso externo e as diretivas de conferência que podem ser atribuídas a um usuário específico, use comandos semelhantes a estas:</span><span class="sxs-lookup"><span data-stu-id="250de-p106">That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="250de-p107">O parâmetro ApplicableTo limita os dados retornados para políticas que podem ser atribuídas ao usuário especificado (por exemplo, Antônio Teixeira). Dependendo das restrições de licenciamento e local de uso, isso pode representar um subconjunto de todas as políticas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="250de-p107">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="250de-150">Em alguns casos, propriedades das diretivas não são usadas com o Office 365, enquanto outros só podem ser gerenciados pela equipe de suporte da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="250de-150">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="250de-p108">Com Skype para Business Online, os usuários devem ser gerenciados por uma política de algum tipo. Se uma propriedade válida de relacionada à política estiver vazia, isso significa que o usuário em questão está sendo gerenciado por uma política global, o que é uma política que será automaticamente aplicada a um usuário, a menos que ele ou ela especificamente atribuída uma política por usuário. Porque não vemos uma diretiva de cliente listada para uma conta de usuário, ele é gerenciado pela política global. Você pode determinar a diretiva de cliente global com este comando:</span><span class="sxs-lookup"><span data-stu-id="250de-p108">With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="250de-155">See also</span><span class="sxs-lookup"><span data-stu-id="250de-155">See also</span></span>

#### 

[<span data-ttu-id="250de-156">Gerenciar o Skype for Business Online com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="250de-156">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="250de-157">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="250de-157">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="250de-158">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="250de-158">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

