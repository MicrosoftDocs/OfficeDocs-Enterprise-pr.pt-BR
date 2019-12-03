---
title: Exibir licenças e serviços com o PowerShell do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
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
ms.openlocfilehash: b8a0bb1845f3c0db5aa47cea0c2f6e5e580c804f
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655843"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="31a06-103">Exibir licenças e serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="31a06-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="31a06-104">Todas as assinaturas do Office 365 consistem nos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="31a06-104">Every Office 365 subscription consists of the following elements:</span></span>

- <span data-ttu-id="31a06-105">**Planos de licenciamento** Eles também são conhecidos como planos de licença ou planos do Office 365.</span><span class="sxs-lookup"><span data-stu-id="31a06-105">**Licensing plans** These are also known as license plans or Office 365 plans.</span></span> <span data-ttu-id="31a06-106">Os planos de licenciamento definem os serviços do Office 365 que estão disponíveis para os usuários.</span><span class="sxs-lookup"><span data-stu-id="31a06-106">Licensing plans define the Office 365 services that are available to users.</span></span> <span data-ttu-id="31a06-107">Sua assinatura do Office 365 pode conter vários planos de licenciamento.</span><span class="sxs-lookup"><span data-stu-id="31a06-107">Your Office 365 subscription may contain multiple licensing plans.</span></span> <span data-ttu-id="31a06-108">Um plano de licenciamento de exemplo seria o Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="31a06-108">An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="31a06-109">**Serviços** do Eles também são conhecidos como planos de serviço.</span><span class="sxs-lookup"><span data-stu-id="31a06-109">**Services** These are also known as service plans.</span></span> <span data-ttu-id="31a06-110">Os serviços são os produtos, recursos e recursos do Office 365 que estão disponíveis em cada plano de licenciamento, por exemplo, o Exchange Online e o Office Professional Plus.</span><span class="sxs-lookup"><span data-stu-id="31a06-110">Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus.</span></span> <span data-ttu-id="31a06-111">Os usuários podem receber várias licenças de diferentes planos de licenciamento que garantem o acesso a diferentes serviços.</span><span class="sxs-lookup"><span data-stu-id="31a06-111">Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="31a06-p103">**Licenças** Cada plano de licenciamento contém o número de licenças que você adquiriu. Você atribui licenças a usuários para que eles possam usar os serviços do Office 365 definidos pelo plano de licenciamento. Cada conta de usuário requer ao menos uma licença de um plano de licenciamento para poder fazer logon no Office 365 e usar os serviços.</span><span class="sxs-lookup"><span data-stu-id="31a06-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="31a06-p104">Você pode usar o Office 365 PowerShell para visualizar detalhes sobre os planos de licenciamento, licenças e serviços disponíveis na sua organização do Office 365. Confira mais informações sobre produtos, recursos e serviços disponíveis em diferentes assinaturas do Office 365 em [Opções de Planos do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="31a06-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="31a06-117">Use o PowerShell do Azure Active Directory para o módulo do gráfico</span><span class="sxs-lookup"><span data-stu-id="31a06-117">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="31a06-118">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="31a06-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="31a06-119">Para exibir informações resumidas sobre seus planos de licenciamento atuais e as licenças disponíveis para cada plano, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="31a06-119">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

<span data-ttu-id="31a06-120">Os resultados contêm as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="31a06-120">The results contain the following information:</span></span>
  
- <span data-ttu-id="31a06-121">**SkuPartNumber:** Mostra os planos de licenciamento disponíveis para sua organização.</span><span class="sxs-lookup"><span data-stu-id="31a06-121">**SkuPartNumber:** Shows the available licensing plans for your organization.</span></span> <span data-ttu-id="31a06-122">Por exemplo, `ENTERPRISEPACK` é o nome do plano de licença para o Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="31a06-122">For example, `ENTERPRISEPACK` is the license plan name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="31a06-123">**Habilitado:** Número de licenças que você comprou para um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="31a06-123">**Enabled:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="31a06-124">**ConsumedUnits:** número de licenças que você atribuiu aos usuários de um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="31a06-124">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="31a06-125">Para exibir detalhes sobre os serviços do Office 365 que estão disponíveis em todos os seus planos de licença, primeiro exiba uma lista de seus planos de licença.</span><span class="sxs-lookup"><span data-stu-id="31a06-125">To view details about the Office 365 services that are available in all of your license plans, first display a list of your license plans.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="31a06-126">Em seguida, armazene as informações dos planos de licença em uma variável.</span><span class="sxs-lookup"><span data-stu-id="31a06-126">Next, store the license plans information in a variable.</span></span>

```powershell
$licenses = Get-AzureADSubscribedSku
```

<span data-ttu-id="31a06-127">Em seguida, exiba os serviços em um plano de licença específico.</span><span class="sxs-lookup"><span data-stu-id="31a06-127">Next, display the services in a specific license plan.</span></span>

```powershell
$licenses[<index>].ServicePlans
```

<span data-ttu-id="31a06-128">\<index> é um número inteiro que especifica o número da linha do plano de licença a partir da `Get-AzureADSubscribedSku | Select SkuPartNumber` exibição do comando, menos 1.</span><span class="sxs-lookup"><span data-stu-id="31a06-128">\<index> is an integer that specifies the row number of the license plan from the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command, minus 1.</span></span>

<span data-ttu-id="31a06-129">Por exemplo, se a exibição do `Get-AzureADSubscribedSku | Select SkuPartNumber` comando for:</span><span class="sxs-lookup"><span data-stu-id="31a06-129">For example, if the display of the `Get-AzureADSubscribedSku | Select SkuPartNumber` command is this:</span></span>

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

<span data-ttu-id="31a06-130">Em seguida, o comando para exibir os serviços do plano de licença do ENTERPRISEPREMIUM é:</span><span class="sxs-lookup"><span data-stu-id="31a06-130">Then the command to display the services for the ENTERPRISEPREMIUM license plan is this:</span></span>

```powershell
$licenses[2].ServicePlans
```

<span data-ttu-id="31a06-131">ENTERPRISEPREMIUM é a terceira linha.</span><span class="sxs-lookup"><span data-stu-id="31a06-131">ENTERPRISEPREMIUM is the third row.</span></span> <span data-ttu-id="31a06-132">Portanto, o valor de índice é (3-1) ou 2.</span><span class="sxs-lookup"><span data-stu-id="31a06-132">Therefore, the index value is (3 - 1), or 2.</span></span>

<span data-ttu-id="31a06-133">Para obter uma lista completa de planos de licença (também conhecidos como nomes de produtos), seus planos de serviço incluídos e seus nomes amigáveis correspondentes, confira [nomes de produtos e identificadores de planos de serviço para licenciamento](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="31a06-133">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="31a06-134">Use o Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31a06-134">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="31a06-135">Primeiro, [conectar-se ao seu locatário do Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="31a06-135">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

>[!Note]
><span data-ttu-id="31a06-136">Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="31a06-136">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="31a06-137">Especificamente, o script permite que você exiba e desabilite serviços na sua organização do Office 365, incluindo Sway.</span><span class="sxs-lookup"><span data-stu-id="31a06-137">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="31a06-138">Para saber mais, confira [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="31a06-138">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
>
    
<span data-ttu-id="31a06-139">Para exibir informações resumidas sobre seus planos de licenciamento atuais e as licenças disponíveis para cada plano, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="31a06-139">To view summary information about your current licensing plans and the available licenses for each plan, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="31a06-140">O PowerShell Core não é compatível com o módulo do Microsoft Azure Active Directory para módulo e cmdlets do Windows PowerShell com **MSol** no nome.</span><span class="sxs-lookup"><span data-stu-id="31a06-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="31a06-141">Para continuar usando esses cmdlets, você deve executá-los a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31a06-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="31a06-142">Os resultados contêm as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="31a06-142">The results contain the following information:</span></span>
  
- <span data-ttu-id="31a06-p109">**AccountSkuId** Mostre os planos de licenciamento disponíveis para a sua organização usando a sintaxe `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ é o valor que você forneceu ao se inscrever no Office 365 e é exclusivo da sua organização. O valor do _<LicensingPlan>_ é o mesmo para todos. Por exemplo, no valor `litwareinc:ENTERPRISEPACK`, o nome da empresa é  `litwareinc` e o nome do plano de licenciamento `ENTERPRISEPACK`, que é o nome do sistema para o Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="31a06-p109">**AccountSkuId:** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="31a06-147">**ActiveUnits:** Número de licenças que você comprou para um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="31a06-147">**ActiveUnits:** Number of licenses that you've purchased for a specific licensing plan.</span></span>
    
- <span data-ttu-id="31a06-148">**WarningUnits:** número de licenças em um plano de licenciamento que você não renovou e que expirará após um período de carência de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="31a06-148">**WarningUnits:** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="31a06-149">**ConsumedUnits:** número de licenças que você atribuiu aos usuários de um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="31a06-149">**ConsumedUnits:** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="31a06-150">Para exibir detalhes sobre os serviços do Office 365 disponíveis em todos os planos de licenciamento, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="31a06-150">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="31a06-151">A tabela a seguir mostra os planos de serviço do Office 365 e seus nomes amigáveis para os serviços mais comuns.</span><span class="sxs-lookup"><span data-stu-id="31a06-151">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="31a06-152">Sua lista de planos de serviço pode ser diferente.</span><span class="sxs-lookup"><span data-stu-id="31a06-152">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="31a06-153">**Plano de serviço**</span><span class="sxs-lookup"><span data-stu-id="31a06-153">**Service plan**</span></span>|<span data-ttu-id="31a06-154">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="31a06-154">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="31a06-155">Sway</span><span class="sxs-lookup"><span data-stu-id="31a06-155">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="31a06-156">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="31a06-156">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="31a06-157">Yammer</span><span class="sxs-lookup"><span data-stu-id="31a06-157">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="31a06-158">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="31a06-158">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="31a06-159">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="31a06-159">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="31a06-160">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="31a06-160">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="31a06-161">Office</span><span class="sxs-lookup"><span data-stu-id="31a06-161">Office</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="31a06-162">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="31a06-162">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="31a06-163">Plano 2 do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="31a06-163">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="31a06-164">Para obter uma lista completa de planos de licença (também conhecidos como nomes de produtos), seus planos de serviço incluídos e seus nomes amigáveis correspondentes, confira [nomes de produtos e identificadores de planos de serviço para licenciamento](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="31a06-164">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="31a06-165">Para exibir detalhes sobre os serviços do Office 365 disponíveis em um plano de licenciamento específico, use a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="31a06-165">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="31a06-166">Este exemplo mostra os serviços do Office 365 que estão disponíveis no plano de licenciamento do litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="31a06-166">This example shows the Office 365 services that are available in the litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a><span data-ttu-id="31a06-167">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="31a06-167">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="31a06-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="31a06-168">See also</span></span>

[<span data-ttu-id="31a06-169">Gerenciar licenças e contas de usuário usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="31a06-169">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="31a06-170">Gerenciar o Office 365 com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="31a06-170">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="31a06-171">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="31a06-171">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
