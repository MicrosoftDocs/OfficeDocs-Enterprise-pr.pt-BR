---
title: Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
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
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213948"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="70926-103">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="70926-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="70926-104">**Resumo:** Explica como usar o Office 365 PowerShell para determinar os serviços do Office 365 que tiverem sido atribuídos aos usuários.</span><span class="sxs-lookup"><span data-stu-id="70926-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="70926-p101">No Office 365, licencia para planos de licenciamento (também chamado de SKUs ou do Office 365 estiver planejando) conceder aos usuários acesso aos serviços do Office 365 que são definidos para esses planos. No entanto, um usuário pode não ter acesso a todos os serviços que estão disponíveis em uma licença atualmente atribuído a eles. Você pode usar o PowerShell do Office 365 para exibir o status dos serviços em contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="70926-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="70926-108">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="70926-108">Before you begin</span></span>

- <span data-ttu-id="70926-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="70926-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="70926-111">Use os comandos `Get-MsolAccountSku` e `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` para encontrar as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="70926-111">Use the commands  `Get-MsolAccountSku` and `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` to find the following information:</span></span>
    
  - <span data-ttu-id="70926-112">Os planos de licenciamento que estão disponíveis na sua organização.</span><span class="sxs-lookup"><span data-stu-id="70926-112">The licensing plans that are available in your organization.</span></span>
    
  - <span data-ttu-id="70926-113">Os serviços que estão disponíveis em cada plano de licenciamento e a ordem em que eles estão listados (o número do índice).</span><span class="sxs-lookup"><span data-stu-id="70926-113">The services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>
    
     <span data-ttu-id="70926-114">Para obter mais informações sobre o licenciamento planos, licenças e serviços, consulte [Exibir as licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="70926-114">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="70926-115">Use o comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` para encontrar as licenças atribuídas a um usuário e a ordem na qual eles estão listados (o número de índice).</span><span class="sxs-lookup"><span data-stu-id="70926-115">Use the command  `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` to find the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>
    
- <span data-ttu-id="70926-116">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro _All_, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="70926-116">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    

## <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="70926-117">Para exibir serviços para uma conta de usuário</span><span class="sxs-lookup"><span data-stu-id="70926-117">To view services for a user account</span></span>

<span data-ttu-id="70926-118">Para exibir todos os serviços do Office 365 que um usuário tem acesso ao, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="70926-118">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="70926-p103">Este exemplo mostra os serviços aos quais o usuário BelindaN@litwareinc.com tem acesso. Mostra os serviços que estão associados a todas as licenças são atribuídas à sua conta.</span><span class="sxs-lookup"><span data-stu-id="70926-p103">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="70926-121">Este exemplo mostra os serviços aos quais a usuária BrendaF@litwareinc.com tem acesso a partir da primeira licença atribuída à conta dela (o número de índice é 0).</span><span class="sxs-lookup"><span data-stu-id="70926-121">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="70926-122">Para exibir todos os serviços para um usuário que tenha sido atribuído a *várias licenças*, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="70926-122">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

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

  
## <a name="see-also"></a><span data-ttu-id="70926-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="70926-123">See also</span></span>

<span data-ttu-id="70926-124">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="70926-124">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="70926-125">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="70926-125">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="70926-126">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="70926-126">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="70926-127">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="70926-127">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="70926-128">Atribuir licenças a contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="70926-128">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="70926-129">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="70926-129">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="70926-130">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="70926-130">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="70926-131">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="70926-131">ConvertTo-Html</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [<span data-ttu-id="70926-132">Format-List</span><span class="sxs-lookup"><span data-stu-id="70926-132">Format-List</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [<span data-ttu-id="70926-133">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="70926-133">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="70926-134">Select-Object</span><span class="sxs-lookup"><span data-stu-id="70926-134">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="70926-135">Where-Object</span><span class="sxs-lookup"><span data-stu-id="70926-135">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a><span data-ttu-id="70926-136">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="70926-136">New to Office 365?</span></span>


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]