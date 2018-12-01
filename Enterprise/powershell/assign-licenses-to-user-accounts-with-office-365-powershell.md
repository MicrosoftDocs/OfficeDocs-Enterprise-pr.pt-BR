---
title: Atribuir licenças a contas de usuários usando o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Explica como usar o Office 365 PowerShell para atribuir uma licença do Office 365 para usuários não licenciados.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123288"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c70ea-103">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="c70ea-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c70ea-104">**Resumo:** explica como usar o Office 365 PowerShell para atribuir uma licença do Office 365 para usuários não licenciados.</span><span class="sxs-lookup"><span data-stu-id="c70ea-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="c70ea-p101">O licenciamento de contas de usuário no Office 365 é importante, porque os usuários não poderão usar nenhum serviço do Office 365 até que suas contas sejam licenciadas. Você pode usar o Office 365 PowerShell para atribuir licenças de forma eficiente para contas não licenciadas, especialmente para várias contas.</span><span class="sxs-lookup"><span data-stu-id="c70ea-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="c70ea-107">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="c70ea-107">Before you begin</span></span>
<span data-ttu-id="c70ea-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="c70ea-108"><a name="RTT"> </a></span></span>

- <span data-ttu-id="c70ea-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c70ea-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c70ea-p103">Use o cmdlet **Get-MsolAccountSku** para exibir os planos de licenciamento disponíveis e o número de licenças disponíveis em cada plano na sua organização. O número de licenças disponíveis em cada plano é **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para mais informações sobre planos de licenciamento, licenças e serviços, confira [Exibir licenças e serviços com o Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="c70ea-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="c70ea-114">Para localizar as contas não licenciadas em sua organização, execute o comando  `Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="c70ea-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="c70ea-p104">Você só pode atribuir licenças para contas de usuário que tenham o conjunto de propriedades **UsageLocation** definido como um código de país ISO 3166-1 alpha-2 válido. Por exemplo, US para os Estados Unidos e FR para a França. Alguns serviços do Office 365 não estão disponíveis em certos países. Para mais informações, confira [Sobre restrições de licença](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="c70ea-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="c70ea-p105">Para localizar contas que não tenham um valor **UsageLocation**, execute o comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Para definir o valor **UsageLocation** em uma conta, use a sintaxe `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Por exemplo,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span><span class="sxs-lookup"><span data-stu-id="c70ea-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="c70ea-122">Se você usar o cmdlet **Get-MsolUser** sem usar o parâmetro `-All`, somente as primeiras 500 contas serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="c70ea-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="c70ea-123">Atribuir licenças às contas de usuário</span><span class="sxs-lookup"><span data-stu-id="c70ea-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="c70ea-124">Para atribuir uma licença a um usuário, use a seguinte sintaxe no Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c70ea-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="c70ea-125">Este exemplo atribui uma licença do plano de licenciamento do `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ao usuário não licenciado `belindan@litwareinc.com`.</span><span class="sxs-lookup"><span data-stu-id="c70ea-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="c70ea-126">Para atribuir uma licença a vários usuários sem licença, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="c70ea-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="c70ea-127">**Anotações**</span><span class="sxs-lookup"><span data-stu-id="c70ea-127">**Notes**</span></span>
  
- <span data-ttu-id="c70ea-128">Você não pode atribuir várias licenças a um usuário do mesmo plano de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="c70ea-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="c70ea-129">Se você não tiver licenças o suficiente disponíveis, as licenças serão atribuídas aos usuários na ordem em que eles forem retornados pelo cmdlet **Get-MsolUser** até que as licenças disponíveis esgotem.</span><span class="sxs-lookup"><span data-stu-id="c70ea-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="c70ea-130">Este exemplo atribui licenças do plano de licenciamento do `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) a todos os usuários não licenciados.</span><span class="sxs-lookup"><span data-stu-id="c70ea-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="c70ea-131">Este exemplo atribui essas mesmas licenças a usuários não licenciados no Departamento de vendas nos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="c70ea-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="c70ea-132">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="c70ea-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="c70ea-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="c70ea-133">See also</span></span>
<span data-ttu-id="c70ea-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="c70ea-134"></span></span>

<span data-ttu-id="c70ea-135">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c70ea-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="c70ea-136">Criar contas de usuário</span><span class="sxs-lookup"><span data-stu-id="c70ea-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c70ea-137">Exclua e restaure contas de usuário</span><span class="sxs-lookup"><span data-stu-id="c70ea-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c70ea-138">Contas de usuário do bloco</span><span class="sxs-lookup"><span data-stu-id="c70ea-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="c70ea-139">Remover licenças de contas de usuário</span><span class="sxs-lookup"><span data-stu-id="c70ea-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="c70ea-140">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="c70ea-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="c70ea-141">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="c70ea-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="c70ea-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="c70ea-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="c70ea-143">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="c70ea-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="c70ea-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="c70ea-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="c70ea-145">Select-Object</span><span class="sxs-lookup"><span data-stu-id="c70ea-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="c70ea-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="c70ea-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

