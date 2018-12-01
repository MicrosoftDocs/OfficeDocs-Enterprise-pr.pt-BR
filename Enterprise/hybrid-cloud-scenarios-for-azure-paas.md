---
title: Cenários de nuvem híbrida para a PaaS do Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Resumo: Entenda os cenários e arquitetura híbrida para a plataforma Microsoft como um serviço (PaaS)-based ofertas de nuvem no Windows Azure.'
ms.openlocfilehash: e536d81b6b14b05bef49d7c91b0404faec64303b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123328"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="4ec1c-103">Cenários de nuvem híbrida para a PaaS do Azure</span><span class="sxs-lookup"><span data-stu-id="4ec1c-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="4ec1c-104">**Resumo:** Entenda os cenários e arquitetura híbrida para a plataforma Microsoft como um serviço (PaaS)-based ofertas de nuvem no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="4ec1c-105">Combinar os dados no local ou recursos de computação com aplicativos novos ou convertidos em execução no Azure PaaS, que podem tirar proveito de escala, confiabilidade e desempenho na nuvem e oferecer um suporte melhor para usuários móveis.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="4ec1c-106">Arquitetura de cenário do Windows Azure PaaS híbrida</span><span class="sxs-lookup"><span data-stu-id="4ec1c-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="4ec1c-107">A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em PaaS Microsoft no Azure.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="4ec1c-108">**Figura 1: Cenários de implantação híbrida baseada em PaaS Microsoft no Azure**</span><span class="sxs-lookup"><span data-stu-id="4ec1c-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Cenários híbridos da Microsoft baseados em PaaS no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="4ec1c-110">Para cada camada da arquitetura:</span><span class="sxs-lookup"><span data-stu-id="4ec1c-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="4ec1c-111">Cenários e aplicativos</span><span class="sxs-lookup"><span data-stu-id="4ec1c-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="4ec1c-112">Um aplicativo de PaaS híbrido é executado no Windows Azure e usa os recursos de computação ou armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="4ec1c-113">Identidade</span><span class="sxs-lookup"><span data-stu-id="4ec1c-113">Identity</span></span>
    
    <span data-ttu-id="4ec1c-114">Consiste de sincronização de diretório ou federação com um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="4ec1c-115">Rede</span><span class="sxs-lookup"><span data-stu-id="4ec1c-115">Network</span></span>
    
    <span data-ttu-id="4ec1c-p101">Consiste em seu pipe Internet existente ou uma conexão ExpressRoute com correspondência pública para PaaS do Azure. Você deve incluir uma maneira para o aplicativo do Azure PaaS acessar o recurso de compute ou armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="4ec1c-118">Local</span><span class="sxs-lookup"><span data-stu-id="4ec1c-118">On-premises</span></span>
    
    <span data-ttu-id="4ec1c-119">Consiste em infraestrutura de segurança e de identidade e a linha existente de aplicativos de negócios (LOB) ou servidores de banco de dados, que um aplicativo do Windows Azure PaaS pode acessar com segurança.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="4ec1c-120">Aplicativo do Azure PaaS híbrida</span><span class="sxs-lookup"><span data-stu-id="4ec1c-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="4ec1c-121">Figura 2 mostra a configuração de um aplicativo híbrida executando no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="4ec1c-122">**Figura 2: Aplicativo de implantação híbrida baseada em PaaS Azure**</span><span class="sxs-lookup"><span data-stu-id="4ec1c-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Aplicativo híbrido baseado em PaaS no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="4ec1c-p102">Na Figura 2, uma rede local hospeda aplicativos nos servidores e DMZ contendo um servidor proxy ou armazenamento. Ele está conectado aos serviços do Azure PaaS pela Internet ou com uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="4ec1c-126">Uma organização pode tornar seus recursos de armazenamento ou compute disponíveis para o aplicativo de híbrido Azure PaaS por:</span><span class="sxs-lookup"><span data-stu-id="4ec1c-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="4ec1c-127">Hospedando o recurso em servidores no DMZ.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="4ec1c-128">Hospedagem de um servidor proxy reverso no DMZ, que permite solicitações de entrada, autenticadas e baseada em HTTPS para o recurso que está localizado no local.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="4ec1c-129">O aplicativo do Azure pode usar as credenciais a partir de:</span><span class="sxs-lookup"><span data-stu-id="4ec1c-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="4ec1c-130">Azure AD, que pode ser sincronizado com seu provedor de identidade de local, como o Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="4ec1c-131">Um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="4ec1c-132">Aplicativo do exemplo Azure PaaS híbrido</span><span class="sxs-lookup"><span data-stu-id="4ec1c-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="4ec1c-133">A Figura 3 mostra um exemplo de aplicativo híbrida executando no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="4ec1c-134">**Figura 3: Um exemplo aplicativo baseado no Windows Azure PaaS híbrido**</span><span class="sxs-lookup"><span data-stu-id="4ec1c-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Um aplicativo híbrido de exemplo baseado em PaaS no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="4ec1c-p103">Na Figura 3, um hosts de rede local uma LOB App. Azure PaaS hospeda um aplicativo móvel personalizado. Um smartphone na Internet acessa o aplicativo móvel personalizado no Azure, que envia solicitações de dados para o aplicativo LOB local.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="4ec1c-p104">Este exemplo de aplicativo do Windows Azure PaaS híbrido é um aplicativo móvel personalizado que fornece informações de contato atualizadas sobre funcionários. O cenário híbrido de ponta a ponta consiste em:</span><span class="sxs-lookup"><span data-stu-id="4ec1c-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="4ec1c-141">Um smartphone aplicativo que exige validado, credenciais de local para ser executado.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="4ec1c-142">Um aplicativo móvel personalizado em execução no Azure PaaS, que solicita informações sobre funcionários específicos com base em consultas do aplicativo do smartphone de um usuário.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="4ec1c-143">Um servidor proxy reverso no DMZ que valide o aplicativo móvel personalizado e encaminha a solicitação.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="4ec1c-144">Um farm de servidores de aplicativos LOB que atende à solicitação de contato, sujeito as permissões da conta do usuário.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="4ec1c-145">Porque o provedor de identidade local foi sincronizado com o Azure AD, o aplicativo móvel personalizado e o aplicativo LOB possam validar nome da conta do usuário solicitante.</span><span class="sxs-lookup"><span data-stu-id="4ec1c-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4ec1c-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="4ec1c-146">See Also</span></span>

[<span data-ttu-id="4ec1c-147">Nuvem híbrida da Microsoft para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="4ec1c-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="4ec1c-148">Recursos de arquitetura de TI do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="4ec1c-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

