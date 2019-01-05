---
title: Exibir licenças e serviços com o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explica como usar o Office 365 PowerShell para visualizar informações sobre os planos de licenciamento, serviços e licenças disponíveis na sua organização do Office 365.
ms.openlocfilehash: f673ac984e504a740dfac474821366d34de5ccbc
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730326"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="5455c-103">Exibir licenças e serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="5455c-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="5455c-104">**Resumo:** explica como usar o Office 365 PowerShell para visualizar informações sobre os planos de licenciamento, serviços e licenças disponíveis na sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="5455c-104">**Summary:** Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="5455c-105">Todas as assinaturas do Office 365 consistem nos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="5455c-105">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="5455c-p101">**Planos de licenciamento** Esses são também conhecidos como planos de licença ou planos do Office 365. Planos de licenciamento definem os serviços do Office 365 que estão disponíveis para usuários. Sua assinatura do Office 365 pode conter vários planos de licenciamento. Um plano de licenciamento de exemplo seria o Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="5455c-p101">**Licensing plans** These are also known as license plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="5455c-p102">**Serviços** Essas são também conhecidos como planos de serviço. Serviços são os produtos do Office 365, recursos e capacidades que estão disponíveis em cada plano de licenciamento, por exemplo, o Exchange Online e Office Professional Plus. Os usuários podem ter várias licenças atribuídas a eles de planos de licenciamento diferentes que concedem acesso aos serviços diferentes.</span><span class="sxs-lookup"><span data-stu-id="5455c-p102">**Services** These are also known as service plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="5455c-p103">**Licenças** Cada plano de licenciamento contém o número de licenças que você adquiriu. Você atribui licenças a usuários para que eles possam usar os serviços do Office 365 definidos pelo plano de licenciamento. Cada conta de usuário requer ao menos uma licença de um plano de licenciamento para poder fazer logon no Office 365 e usar os serviços.</span><span class="sxs-lookup"><span data-stu-id="5455c-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="5455c-p104">Você pode usar o Office 365 PowerShell para visualizar detalhes sobre os planos de licenciamento, licenças e serviços disponíveis na sua organização do Office 365. Confira mais informações sobre produtos, recursos e serviços disponíveis em diferentes assinaturas do Office 365 em [Opções de Planos do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="5455c-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5455c-118">Use o PowerShell do Azure Active Directory para o módulo de gráfico</span><span class="sxs-lookup"><span data-stu-id="5455c-118">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5455c-119">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="5455c-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="5455c-120">Para exibir informações de resumo sobre seus planos de licenciamento atuais e as licenças disponíveis para cada plano, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5455c-120">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="5455c-121">Os resultados contêm as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="5455c-121">The results contain the following information:</span></span>
  
- <span data-ttu-id="5455c-p105">**SkuPartNumber:** Mostra os planos de licenciamento disponíveis para sua organização. Por exemplo, `ENTERPRISEPACK` é o nome do sistema para Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="5455c-p105">**SkuPartNumber:** Shows the available licensing plans for your organization. For example, `ENTERPRISEPACK` is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="5455c-124">**Habilitado:** Número de licenças que você comprou de um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="5455c-124">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="5455c-125">**ConsumedUnits:** número de licenças que você atribuiu aos usuários de um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="5455c-125">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="5455c-126">Para exibir detalhes sobre os serviços do Office 365 estão disponíveis em todos os seus planos de licença, primeiro exiba uma lista de seus planos de licença.</span><span class="sxs-lookup"><span data-stu-id="5455c-126">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

<span data-ttu-id="5455c-127">Em seguida, armazene as informações de planos de licença em uma variável.</span><span class="sxs-lookup"><span data-stu-id="5455c-127">Next, store the license plans information in a variable.</span></span>

````
$licenses = Get-AzureADSubscribedSku
````

<span data-ttu-id="5455c-128">Em seguida, exibe os serviços em um plano de licença específico.</span><span class="sxs-lookup"><span data-stu-id="5455c-128">Next, display the services in a specific license plan.</span></span>

````
$licenses[<index>].ServicePlan
````

<span data-ttu-id="5455c-129">\<índice > é um inteiro que especifica o número da linha do plano de licença da exibição do `Get-AzureADSubscribedSku | Select SkuPartNumber` command, menos 1.</span><span class="sxs-lookup"><span data-stu-id="5455c-129">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="5455c-130">Por exemplo, se a exibição do `Get-AzureADSubscribedSku | Select SkuPartNumber` comando é isso:</span><span class="sxs-lookup"><span data-stu-id="5455c-130">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

<span data-ttu-id="5455c-131">Em seguida, o comando para exibir os serviços para o plano de licença ENTERPRISEPREMIUM é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5455c-131">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

````
$licenses[2].ServicePlan
````

<span data-ttu-id="5455c-p106">ENTERPRISEPREMIUM é a terceira linha. Portanto, o valor de índice é (3 - 1), ou 2.</span><span class="sxs-lookup"><span data-stu-id="5455c-p106">ENTERPRISEPREMIUM is the third row. Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="5455c-134">Para obter uma lista completa de planos de licença (também conhecido como nomes de produto), seus planos de serviço incluído e seus nomes amigáveis correspondentes, consulte [nomes de produto e os identificadores de plano de serviço para licenciamento](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="5455c-134">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5455c-135">Use o módulo do Microsoft Azure Active Directory para o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5455c-135">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5455c-136">Primeiro, [Conecte-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5455c-136">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="5455c-p107">Um script do PowerShell está disponível que automatiza os procedimentos descritos neste tópico. Especificamente, o script permite que você exibir e desabilite os serviços em sua organização do Office 365, incluindo Sway. Para obter mais informações, consulte [Desabilitar o acesso aos Sway com o Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="5455c-p107">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="5455c-140">Para exibir informações de resumo sobre seus planos de licenciamento atuais e as licenças disponíveis para cada plano, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5455c-140">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="5455c-141">Os resultados contêm as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="5455c-141">The results contain the following information:</span></span>
  
- <span data-ttu-id="5455c-p108">**AccountSkuId** Mostre os planos de licenciamento disponíveis para a sua organização usando a sintaxe `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ é o valor que você forneceu ao se inscrever no Office 365 e é exclusivo da sua organização. O valor do _<LicensingPlan>_ é o mesmo para todos. Por exemplo, no valor `litwareinc:ENTERPRISEPACK`, o nome da empresa é  `litwareinc` e o nome do plano de licenciamento `ENTERPRISEPACK`, que é o nome do sistema para o Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="5455c-p108">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="5455c-146">**ActiveUnits:** Número de licenças que você comprou de um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="5455c-146">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="5455c-147">**WarningUnits:** número de licenças em um plano de licenciamento que você não renovou e que expirará após um período de carência de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="5455c-147">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="5455c-148">**ConsumedUnits:** número de licenças que você atribuiu aos usuários de um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="5455c-148">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="5455c-149">Para exibir detalhes sobre os serviços do Office 365 disponíveis em todos os planos de licenciamento, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5455c-149">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="5455c-p109">A tabela a seguir mostra os planos de serviço do Office 365 e seus nomes amigáveis para os serviços mais comuns. Sua lista de planos de serviço pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="5455c-p109">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="5455c-152">**Plano de serviço**</span><span class="sxs-lookup"><span data-stu-id="5455c-152">**Service plan**</span></span>|<span data-ttu-id="5455c-153">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="5455c-153">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="5455c-154">Sway</span><span class="sxs-lookup"><span data-stu-id="5455c-154">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="5455c-155">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5455c-155">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="5455c-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="5455c-156">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="5455c-157">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="5455c-157">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="5455c-158">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="5455c-158">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="5455c-159">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="5455c-159">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="5455c-160">Office Online</span><span class="sxs-lookup"><span data-stu-id="5455c-160">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="5455c-161">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5455c-161">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="5455c-162">Plano 2 do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="5455c-162">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="5455c-163">Para obter uma lista completa de planos de licença (também conhecido como nomes de produto), seus planos de serviço incluído e seus nomes amigáveis correspondentes, consulte [nomes de produto e os identificadores de plano de serviço para licenciamento](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="5455c-163">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="5455c-164">Para exibir detalhes sobre os serviços do Office 365 disponíveis em um plano de licenciamento específico, use a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="5455c-164">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="5455c-165">Este exemplo mostra os serviços do Office 365 que estão disponíveis no plano de licenciamento de litwareinc: enterprisepack (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="5455c-165">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="5455c-166">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="5455c-166">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="5455c-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="5455c-167">See also</span></span>


[<span data-ttu-id="5455c-168">Gerenciar contas de usuário e licenças usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5455c-168">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5455c-169">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5455c-169">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5455c-170">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5455c-170">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
