---
title: Criação de rede para o Microsoft SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Resumo: entenda como otimizar sua rede para acessar os serviços SaaS da Microsoft, incluindo o Office 365, o Microsoft Intune e o Dynamics 365.'
ms.openlocfilehash: 695e3255bf1afcb5314985caccb15ead410d93f6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067767"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="ba78f-103">Criação de rede para o Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="ba78f-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="ba78f-104">**Resumo:** Entenda como otimizar sua rede para acessar os serviços SaaS da Microsoft, incluindo o Office 365, o Microsoft Intune e o Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="ba78f-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="ba78f-105">A otimização da sua rede para os serviços de SaaS da Microsoft exige a configuração de dispositivos de borda e interno para direcionar as diferentes categorias de tráfego para os serviços de SaaS da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ba78f-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="ba78f-106">Etapas para preparar sua rede para os serviços Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="ba78f-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="ba78f-107">Siga estas etapas para otimizar a rede para os serviços Microsoft SaaS:</span><span class="sxs-lookup"><span data-stu-id="ba78f-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="ba78f-108">Siga as **etapas para preparar sua rede para o serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="ba78f-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="ba78f-109">Adicione uma conexão à Internet para cada um dos seus escritórios.</span><span class="sxs-lookup"><span data-stu-id="ba78f-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="ba78f-110">Certifique-se de que os ISPs de todas as conexões com a Internet usem um servidor DNS com um endereço IP local.</span><span class="sxs-lookup"><span data-stu-id="ba78f-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="ba78f-111">Examine seus hairpins de rede, destinos intermediários, como serviços de segurança baseados em nuvem, e elimine-os se possível.</span><span class="sxs-lookup"><span data-stu-id="ba78f-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="ba78f-112">Configure seus dispositivos de borda para ignorar o processamento para as categorias otimizar e permitir do tráfego Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="ba78f-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="ba78f-113">Otimizando o tráfego para os serviços SaaS da Microsoft</span><span class="sxs-lookup"><span data-stu-id="ba78f-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="ba78f-114">Há três categorias de tráfego de SaaS da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="ba78f-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="ba78f-115">Otimização</span><span class="sxs-lookup"><span data-stu-id="ba78f-115">Optimize</span></span>

  <span data-ttu-id="ba78f-116">Necessário para conectividade a cada serviço Microsoft SaaS e representa mais de 75% de largura de banda, conexões e volume de dados do SaaS da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ba78f-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="ba78f-117">Permitir</span><span class="sxs-lookup"><span data-stu-id="ba78f-117">Allow</span></span>

  <span data-ttu-id="ba78f-118">Necessário para conectividade com serviços e recursos Microsoft SaaS específicos, mas não são tão sensíveis ao desempenho da rede e à latência que na categoria otimizar.</span><span class="sxs-lookup"><span data-stu-id="ba78f-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="ba78f-119">Padrão</span><span class="sxs-lookup"><span data-stu-id="ba78f-119">Default</span></span>

  <span data-ttu-id="ba78f-120">Representa serviços e dependências Microsoft SaaS que não exigem nenhuma otimização.</span><span class="sxs-lookup"><span data-stu-id="ba78f-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="ba78f-121">Você pode tratar o tráfego de categoria padrão, como o tráfego de Internet normal.</span><span class="sxs-lookup"><span data-stu-id="ba78f-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="ba78f-122">**Figura 1: configuração recomendada para o tráfego de SaaS da Microsoft para todos os escritórios**</span><span class="sxs-lookup"><span data-stu-id="ba78f-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Figura 1: configuração recomendada para o tráfego de SaaS da Microsoft para todos os escritórios](media/Network-Poster/SaaS1.png)

<span data-ttu-id="ba78f-124">A Figura 1 mostra a configuração recomendada de todos os escritórios, incluindo filiais e escritórios regionais ou centrais, nos quais:</span><span class="sxs-lookup"><span data-stu-id="ba78f-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="ba78f-125">A categoria **padrão** e o tráfego geral da Internet são roteados para escritórios que têm servidores proxy e outros dispositivos de borda para oferecer proteção contra riscos de segurança baseados na Internet.</span><span class="sxs-lookup"><span data-stu-id="ba78f-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="ba78f-126">**Otimizar** e **permitir** tráfego de categoria é encaminhado diretamente para a borda do front-end de rede da Microsoft mais próximo do escritório que contém o usuário de conexão, ignorando servidores proxy e outros dispositivos de borda.</span><span class="sxs-lookup"><span data-stu-id="ba78f-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="ba78f-127">Os dispositivos de rede de longa distância (SD-WAN) definidos por software em filiais separam tráfego para:</span><span class="sxs-lookup"><span data-stu-id="ba78f-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="ba78f-128">A categoria **padrão** e o tráfego geral da Internet vão para um escritório central ou regional no backbone Wan.</span><span class="sxs-lookup"><span data-stu-id="ba78f-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="ba78f-129">**Otimizar** e **permitir que** o tráfego de categoria vá para o ISP que fornece a conexão local com a Internet.</span><span class="sxs-lookup"><span data-stu-id="ba78f-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="ba78f-130">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="ba78f-130">For more information, see:</span></span>
  
- [<span data-ttu-id="ba78f-131">Princípios de conectividade de rede</span><span class="sxs-lookup"><span data-stu-id="ba78f-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="ba78f-132">Planejamento de migração e rede para Office 365</span><span class="sxs-lookup"><span data-stu-id="ba78f-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="ba78f-133">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ba78f-133">Next step</span></span>

[<span data-ttu-id="ba78f-134">Criação de rede para o Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="ba78f-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="ba78f-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="ba78f-135">See also</span></span>

[<span data-ttu-id="ba78f-136">Rede do Microsoft Cloud para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="ba78f-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="ba78f-137">Recursos de arquitetura de TI da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="ba78f-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

