---
title: Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários.
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223103"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="fc572-103">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc572-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="fc572-104">**Resumo:** Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários.</span><span class="sxs-lookup"><span data-stu-id="fc572-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="fc572-p101">No Office 365, licencia para planos de licenciamento (também chamado de SKUs ou do Office 365 estiver planejando) conceder aos usuários acesso aos serviços do Office 365 que são definidos para esses planos. No entanto, um usuário pode não ter acesso a todos os serviços que estão disponíveis em uma licença atualmente atribuído a eles. Você pode usar o PowerShell do Office 365 para exibir o status dos serviços em contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="fc572-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="fc572-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="fc572-108">Before you begin</span></span>

- <span data-ttu-id="fc572-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fc572-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="fc572-111">Use os comandos `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` para encontrar as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="fc572-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="fc572-112">Os planos de licenciamento que estão disponíveis na sua organização.</span><span class="sxs-lookup"><span data-stu-id="fc572-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="fc572-113">Os serviços que estão disponíveis em cada plano de licenciamento e a ordem em que eles estão listados (o número do índice).</span><span class="sxs-lookup"><span data-stu-id="fc572-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="fc572-114">Para obter mais informações sobre o licenciamento planos, licenças e serviços, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fc572-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="fc572-115">Use o comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` para encontrar as licenças atribuídas a um usuário e a ordem na qual eles estão listados (o número de índice).</span><span class="sxs-lookup"><span data-stu-id="fc572-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="fc572-116">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="fc572-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="fc572-117">Para exibir serviços para uma conta de usuário</span><span class="sxs-lookup"><span data-stu-id="fc572-117">To view services for a user account</span></span>

<span data-ttu-id="fc572-118">Para exibir todos os serviços do Office 365 que um usuário tem acesso ao, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="fc572-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="fc572-p103">Este exemplo mostra os serviços aos quais o usuário BelindaN@litwareinc.com tem acesso. Mostra os serviços que estão associados a todas as licenças são atribuídas à sua conta.</span><span class="sxs-lookup"><span data-stu-id="fc572-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="fc572-121">Este exemplo mostra os serviços aos quais a usuária BrendaF@litwareinc.com tem acesso a partir da primeira licença atribuída à conta dela (o número de índice é 0).</span><span class="sxs-lookup"><span data-stu-id="fc572-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="fc572-122">Para localizar todos os usuários licenciados que foram habilitados ou não habilitados para serviços específicos, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="fc572-122">To find all the licensed users who have been enabled or not enabled for specific services, use the following syntax:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

<span data-ttu-id="fc572-123">Esses exemplos utilizam as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="fc572-123">These examples use the following information:</span></span>
  
- <span data-ttu-id="fc572-124">A licença que fornece acesso aos serviços do Office 365 que estamos interessados em é a primeira licença atribuída a todos os usuários (o número de índice é 0).</span><span class="sxs-lookup"><span data-stu-id="fc572-124">The license that gives access to the Office 365 services that we're interested in is the first license that's assigned to all users (the index number is 0).</span></span>
    
- <span data-ttu-id="fc572-p104">Os serviços do Office 365 que estamos interessados em são Skype para Business Online e o Exchange Online. As licenças que estão associados com o plano de licenciamento, Skype para Business Online é o serviço 6º listado (o número de índice é de 5), e o Exchange Online é o serviço de 9 listados (o número de índice é 8).</span><span class="sxs-lookup"><span data-stu-id="fc572-p104">The Office 365 services that we're interested in are Skype for Business Online and Exchange Online. For the licenses that are associated with the licensing plan, Skype for Business Online is the 6th service listed (the index number is 5), and Exchange Online is the 9th service listed (the index number is 8).</span></span>
    
<span data-ttu-id="fc572-127">Este exemplo retorna todas licenciados usuários habilitados para o Skype para Business Online e o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="fc572-127">This example returns all licensed users who are enabled for Skype for Business Online and Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

<span data-ttu-id="fc572-128">Este exemplo retorna todos os usuários licenciados que não estão habilitados para o Skype para Business Online ou Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="fc572-128">This example returns all licensed users who aren't enabled for Skype for Business Online or Exchange Online.</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<span data-ttu-id="fc572-129">Para exibir todos os serviços para um usuário que tenha sido atribuído a *várias licenças*, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="fc572-129">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a><span data-ttu-id="fc572-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="fc572-130">See also</span></span>

<span data-ttu-id="fc572-131">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fc572-131">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="fc572-132">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc572-132">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc572-133">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc572-133">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc572-134">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc572-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc572-135">Atribuir licenças a contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc572-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc572-136">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc572-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="fc572-137">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="fc572-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="fc572-138">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="fc572-138">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="fc572-139">Format-List</span><span class="sxs-lookup"><span data-stu-id="fc572-139">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="fc572-140">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="fc572-140">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="fc572-141">Select-Object</span><span class="sxs-lookup"><span data-stu-id="fc572-141">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="fc572-142">Where-Object</span><span class="sxs-lookup"><span data-stu-id="fc572-142">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="fc572-143">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="fc572-143">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]