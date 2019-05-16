---
title: Cenários de nuvem híbrida para a PaaS do Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Resumo: entenda a arquitetura híbrida e os cenários para ofertas de nuvem com base na PaaS (plataforma como serviço) da Microsoft no Azure.'
ms.openlocfilehash: fcc335d0e53463dea4e7ac73c3885b39734db38e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067527"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="4a579-103">Cenários de nuvem híbrida para a PaaS do Azure</span><span class="sxs-lookup"><span data-stu-id="4a579-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="4a579-104">**Resumo:** Compreenda a arquitetura híbrida e os cenários para as ofertas de nuvem baseadas na PaaS (plataforma como serviço) da Microsoft no Azure.</span><span class="sxs-lookup"><span data-stu-id="4a579-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="4a579-105">Combine dados locais ou recursos de computação com aplicativos novos ou convertidos em execução na PaaS do Azure, o que pode aproveitar o desempenho, a confiabilidade e a escala da nuvem e oferecer um melhor suporte aos usuários móveis.</span><span class="sxs-lookup"><span data-stu-id="4a579-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="4a579-106">Arquitetura de cenário híbrido do Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="4a579-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="4a579-107">A Figura 1 mostra a arquitetura dos cenários híbridos baseados em PaaS da Microsoft no Azure.</span><span class="sxs-lookup"><span data-stu-id="4a579-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="4a579-108">**Figura 1: cenários híbridos baseados no Microsoft PaaS no Azure**</span><span class="sxs-lookup"><span data-stu-id="4a579-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Cenários híbridos baseados no Microsoft PaaS no Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="4a579-110">Para cada camada da arquitetura:</span><span class="sxs-lookup"><span data-stu-id="4a579-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="4a579-111">Aplicativos e cenários</span><span class="sxs-lookup"><span data-stu-id="4a579-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="4a579-112">Um aplicativo de PaaS híbrido é executado no Azure e usa recursos de computação ou armazenamento no local.</span><span class="sxs-lookup"><span data-stu-id="4a579-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="4a579-113">Identidade</span><span class="sxs-lookup"><span data-stu-id="4a579-113">Identity</span></span>
    
    <span data-ttu-id="4a579-114">O consiste em uma sincronização de diretório ou Federação com um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="4a579-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="4a579-115">Rede</span><span class="sxs-lookup"><span data-stu-id="4a579-115">Network</span></span>
    
    <span data-ttu-id="4a579-116">O consiste no seu pipe existente na Internet ou em uma conexão ExpressRoute com emparelhamento público para a PaaS do Azure.</span><span class="sxs-lookup"><span data-stu-id="4a579-116">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS.</span></span> <span data-ttu-id="4a579-117">Você deve incluir uma maneira de o aplicativo de PaaS do Azure acessar o recurso de armazenamento ou de computação local.</span><span class="sxs-lookup"><span data-stu-id="4a579-117">You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="4a579-118">No local</span><span class="sxs-lookup"><span data-stu-id="4a579-118">On-premises</span></span>
    
    <span data-ttu-id="4a579-119">O consiste em uma infraestrutura de identidade e segurança e em servidores de banco de dados ou aplicativos LOB (linha de negócios) existentes, que um aplicativo de PaaS do Azure pode acessar com segurança.</span><span class="sxs-lookup"><span data-stu-id="4a579-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="4a579-120">Aplicativo híbrido do Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="4a579-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="4a579-121">A Figura 2 mostra a configuração de um aplicativo híbrido executado no Azure.</span><span class="sxs-lookup"><span data-stu-id="4a579-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="4a579-122">**Figura 2: aplicativo híbrido baseado em PaaS do Azure**</span><span class="sxs-lookup"><span data-stu-id="4a579-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Aplicativo híbrido baseado em PaaS do Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="4a579-124">Na Figura 2, uma rede local hospeda o armazenamento ou aplicativos nos servidores e um DMZ contendo um servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="4a579-124">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server.</span></span> <span data-ttu-id="4a579-125">Ele está conectado aos serviços de PaaS do Azure pela Internet ou com uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="4a579-125">It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="4a579-126">Uma organização pode tornar seus recursos de computação ou de armazenamento disponíveis para o aplicativo híbrido do Azure PaaS por:</span><span class="sxs-lookup"><span data-stu-id="4a579-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="4a579-127">Hospedar o recurso em servidores no DMZ.</span><span class="sxs-lookup"><span data-stu-id="4a579-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="4a579-128">Hospedagem de um servidor proxy reverso no DMZ, que permite solicitações autenticadas, de entrada, baseadas em HTTPS para o recurso localizado no local.</span><span class="sxs-lookup"><span data-stu-id="4a579-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="4a579-129">O aplicativo do Azure pode usar credenciais de:</span><span class="sxs-lookup"><span data-stu-id="4a579-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="4a579-130">O Azure AD, que pode ser sincronizado com seu provedor de identidade local, como os serviços de domínio do Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="4a579-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="4a579-131">Um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="4a579-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="4a579-132">Exemplo de aplicativo híbrido do Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="4a579-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="4a579-133">A Figura 3 mostra um exemplo de aplicativo híbrido executado no Azure.</span><span class="sxs-lookup"><span data-stu-id="4a579-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="4a579-134">**Figura 3: um aplicativo híbrido baseado em PaaS de exemplo do Azure**</span><span class="sxs-lookup"><span data-stu-id="4a579-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Um exemplo de aplicativo híbrido baseado em PaaS do Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="4a579-136">Na Figura 3, uma rede local hospeda um aplicativo LOB.</span><span class="sxs-lookup"><span data-stu-id="4a579-136">In Figure 3, an on-premises network hosts an LOB app.</span></span> <span data-ttu-id="4a579-137">O Azure PaaS hospeda um aplicativo móvel personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a579-137">Azure PaaS hosts a custom mobile app.</span></span> <span data-ttu-id="4a579-138">Um smartphone na Internet acessa o aplicativo móvel personalizado no Azure, que envia solicitações de dados para o aplicativo LOB local.</span><span class="sxs-lookup"><span data-stu-id="4a579-138">A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="4a579-139">Este exemplo de aplicativo híbrido do Azure PaaS é um aplicativo móvel personalizado que fornece informações de contato atualizadas sobre funcionários.</span><span class="sxs-lookup"><span data-stu-id="4a579-139">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees.</span></span> <span data-ttu-id="4a579-140">O cenário híbrido de ponta a ponta consiste em:</span><span class="sxs-lookup"><span data-stu-id="4a579-140">The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="4a579-141">Um aplicativo do smartphone que requer credenciais locais e validadas para executar.</span><span class="sxs-lookup"><span data-stu-id="4a579-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="4a579-142">Um aplicativo móvel personalizado em execução na PaaS do Azure, que solicita informações sobre funcionários específicos com base nas consultas do aplicativo smartphone de um usuário.</span><span class="sxs-lookup"><span data-stu-id="4a579-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="4a579-143">Um servidor de proxy reverso na DMZ que valida o aplicativo móvel personalizado e encaminha a solicitação.</span><span class="sxs-lookup"><span data-stu-id="4a579-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="4a579-144">Um farm de servidor de aplicativos LOB que faz a solicitação de contato, sujeita às permissões da conta do usuário.</span><span class="sxs-lookup"><span data-stu-id="4a579-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="4a579-145">Como o provedor de identidade local foi sincronizado com o Azure AD, o aplicativo móvel personalizado e o aplicativo LOB podem validar o nome da conta do usuário solicitante.</span><span class="sxs-lookup"><span data-stu-id="4a579-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4a579-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="4a579-146">See Also</span></span>

[<span data-ttu-id="4a579-147">Nuvem híbrida da Microsoft para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="4a579-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="4a579-148">Recursos de arquitetura de TI da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="4a579-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

