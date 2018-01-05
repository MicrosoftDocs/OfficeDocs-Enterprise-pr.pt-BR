---
title: "Exibir licenças e serviços com o PowerShell do Office 365"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- DecEntMigration
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: "Explica como usar o Office 365 PowerShell para visualizar informações sobre os planos de licenciamento, serviços e licenças disponíveis na sua organização do Office 365."
ms.openlocfilehash: dc9ea5ad5077062a05c0070ffecbf580d3aacc49
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a><span data-ttu-id="bfef2-103">Exibir licenças e serviços com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="bfef2-103">View licenses and services with Office 365 PowerShell</span></span>

<span data-ttu-id="bfef2-104">**Resumo:** explica como usar o Office 365 PowerShell para visualizar informações sobre os planos de licenciamento, serviços e licenças disponíveis na sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="bfef2-104">[] Explains how to use Office 365 PowerShell to view information about the licensing plans, services, and licenses that are available in your Office 365 organization.</span></span>
  
<span data-ttu-id="bfef2-105">Todas as assinaturas do Office 365 consistem nos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="bfef2-105">Every Office 365 subscription consists of the following elements:</span></span>
- <span data-ttu-id="bfef2-p101">**Planos de licenciamento** Também são conhecidos comoplanos de licença ou planos do Office 365. Os planos de licenciamento determinam os serviços do Office 365 que estão disponíveis para os usuários. A assinatura do Office 365 pode conter vários planos de licenciamento. Um exemplo de plano seria o Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="bfef2-p101">**Licensing plans** These are also known aslicense plans or Office 365 plans. Licensing plans define the Office 365 services that are available to users. Your Office 365 subscription may contain multiple licensing plans. An example licensing plan would be Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="bfef2-p102">**Serviços** Eles também são conhecidos comoplanos de serviço. Os serviços são os produtos, recursos e capacidades do Office 365 que estão disponíveis no plano de licenciamento, por exemplo, o Exchange Online e o Office Professional Plus. Os usuários podem receber várias licenças de diferentes planos de licenciamento que garantem o acesso a diferentes serviços.</span><span class="sxs-lookup"><span data-stu-id="bfef2-p102">**Services** These are also known asservice plans. Services are the Office 365 products, features, and capabilities that are available in each licensing plan, for example, Exchange Online and Office Professional Plus. Users can have multiple licenses assigned to them from different licensing plans that grant access to different services.</span></span>
    
- <span data-ttu-id="bfef2-p103">**Licenças** Cada plano de licenciamento contém o número de licenças que você adquiriu. Você atribui licenças a usuários para que eles possam usar os serviços do Office 365 definidos pelo plano de licenciamento. Cada conta de usuário requer ao menos uma licença de um plano de licenciamento para poder fazer logon no Office 365 e usar os serviços.</span><span class="sxs-lookup"><span data-stu-id="bfef2-p103">**Licenses** Each licensing plan contains the number of licenses that you purchased. You assign licenses to users so they can use the Office 365 services that are defined by the licensing plan. Every user account requires at least one license from one licensing plan so they can log on to Office 365 and use the services.</span></span>
    
<span data-ttu-id="bfef2-p104">Você pode usar o Office 365 PowerShell para visualizar detalhes sobre os planos de licenciamento, licenças e serviços disponíveis na sua organização do Office 365. Confira mais informações sobre produtos, recursos e serviços disponíveis em diferentes assinaturas do Office 365 em [Opções de Planos do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span><span class="sxs-lookup"><span data-stu-id="bfef2-p104">You can use Office 365 PowerShell to view details about the available licensing plans, licenses, and services in your Office 365 organization. For more information about the products, features, and services that are available in different Office 365 subscriptions, see [Office 365 Plan Options](https://go.microsoft.com/fwlink/p/?LinkId=691147).</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="bfef2-118">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="bfef2-118">Before you begin</span></span>
<span data-ttu-id="bfef2-119"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="bfef2-119"></span></span>

- <span data-ttu-id="bfef2-p105">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bfef2-p105">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="bfef2-p106">Um script do PowerShell está disponível e automatiza os procedimentos descritos neste tópico. Especificamente, o script permite exibir e desabilitar serviços em sua organização do Office 365, incluindo o Sway. Para saber mais, confira [Desabilitar o acesso ao Sway com o PowerShell do Office 365](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="bfef2-p106">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a><span data-ttu-id="bfef2-125">Exibir informações sobre os planos de licenciamento e as licenças disponíveis</span><span class="sxs-lookup"><span data-stu-id="bfef2-125">View information about licensing plans and the available licenses</span></span>
<span data-ttu-id="bfef2-126"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="bfef2-126"></span></span>

<span data-ttu-id="bfef2-127">Para exibir informações resumidas sobre seus planos de licenciamento atuais e as licenças disponíveis para cada plano, execute o seguinte comando no Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bfef2-127">To view summary information about your current licensing plans and the available licenses for each plan, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="bfef2-128">Os resultados contêm as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="bfef2-128">The results contain the following information:</span></span>
  
- <span data-ttu-id="bfef2-p107">**AccountSkuId** Mostre os planos de licenciamento disponíveis para a sua organização usando a sintaxe `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ é o valor que você forneceu ao se inscrever no Office 365 e é exclusivo da sua organização. O valor do _<LicensingPlan>_ é o mesmo para todos. Por exemplo, no valor `litwareinc:ENTERPRISEPACK`, o nome da empresa é  `litwareinc` e o nome do plano de licenciamento `ENTERPRISEPACK`, que é o nome do sistema para o Office 365 Enterprise E3.</span><span class="sxs-lookup"><span data-stu-id="bfef2-p107">**AccountSkuId** Show the available licensing plans for your organization by using the syntax `<CompanyName>:<LicensingPlan>`.  _<CompanyName>_ is the value that you provided when you enrolled in Office 365, and is unique for your organization. The _<LicensingPlan>_ value is the same for everyone. For example, in the value `litwareinc:ENTERPRISEPACK`, the company name is  `litwareinc`, and the licensing plan name  `ENTERPRISEPACK`, which is the system name for Office 365 Enterprise E3.</span></span>
    
- <span data-ttu-id="bfef2-133">**ActiveUnits:** número de licenças que você comprou para um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="bfef2-133">**ActiveUnits** Number of licenses that you've purchases for a specific licensing plan.</span></span>
    
- <span data-ttu-id="bfef2-134">**WarningUnits:** número de licenças em um plano de licenciamento que você não renovou e que expirará após um período de carência de 30 dias.</span><span class="sxs-lookup"><span data-stu-id="bfef2-134">**WarningUnits** Number of licenses in a licensing plan that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="bfef2-135">**ConsumedUnits:** número de licenças que você atribuiu aos usuários de um plano de licenciamento específico.</span><span class="sxs-lookup"><span data-stu-id="bfef2-135">**ConsumedUnits** Number of licenses that you've assigned to users from a specific licensing plan.</span></span>
    
<span data-ttu-id="bfef2-136">Para exibir detalhes sobre os serviços do Office 365 disponíveis em todos os planos de licenciamento, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="bfef2-136">To view details about the Office 365 services that are available in all of your license plans, run the following command:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="bfef2-p108">A tabela a seguir mostra os planos de serviço do Office 365 e seus nomes amigáveis para os serviços mais comuns. Sua lista de planos de serviço pode ser diferente. Peça ao [Suporte do Office]((https://support.office.com/home/contact)) a lista completa de planos de serviço e seus nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="bfef2-p108">The following table shows the Office 365 service plans and their friendly names for the most common services. Your list of service plans might be different. For a complete list of service plans and their friendly names, contact [Office Support]((https://support.office.com/home/contact)).</span></span>
  
|<span data-ttu-id="bfef2-140">****Plano de serviço****</span><span class="sxs-lookup"><span data-stu-id="bfef2-140">****Service plan****</span></span>|<span data-ttu-id="bfef2-141">****Descrição****</span><span class="sxs-lookup"><span data-stu-id="bfef2-141">****Description****</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="bfef2-142">Sway</span><span class="sxs-lookup"><span data-stu-id="bfef2-142">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="bfef2-143">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bfef2-143">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="bfef2-144">Yammer</span><span class="sxs-lookup"><span data-stu-id="bfef2-144">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="bfef2-145">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="bfef2-145">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="bfef2-146">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="bfef2-146">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="bfef2-147">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="bfef2-147">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="bfef2-148">Office Online</span><span class="sxs-lookup"><span data-stu-id="bfef2-148">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="bfef2-149">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bfef2-149">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="bfef2-150">Plano 2 do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="bfef2-150">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="bfef2-151">Para exibir detalhes sobre os serviços do Office 365 disponíveis em um plano de licenciamento específico, use a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="bfef2-151">To view details about the Office 365 services that are available in a specific licensing plan, use the following syntax.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

<span data-ttu-id="bfef2-152">Este exemplo mostra os serviços do Office 365 que estão disponíveis no plano de licenciamento litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="bfef2-152">This example shows the Office 365 services that are available in the   (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a><span data-ttu-id="bfef2-153">Começando a usar o Office 365?</span><span class="sxs-lookup"><span data-stu-id="bfef2-153">New to Office 365?</span></span>
<span data-ttu-id="bfef2-154"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="bfef2-154"></span></span>

||
|:-----|
|<span data-ttu-id="bfef2-p109">![O ícone pequeno do LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Começando a usar o Office 365?**         Descubra cursos em vídeo gratuitos para [Office 365 admins and IT pros]((https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)), oferecidos pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="bfef2-p109">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros]((https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="bfef2-157">Veja também</span><span class="sxs-lookup"><span data-stu-id="bfef2-157">See also</span></span>
<span data-ttu-id="bfef2-158"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="bfef2-158"></span></span>

#### 

[<span data-ttu-id="bfef2-159">Exibir usuários licenciados e não licenciados com o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="bfef2-159">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
  
[<span data-ttu-id="bfef2-160">Exibir licença da conta e detalhes do serviço com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bfef2-160">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
#### 

[<span data-ttu-id="bfef2-161">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="bfef2-161">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)

