---
title: Criação de rede para o Microsoft SaaS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Resumo: Entenda como otimizar sua rede para o acesso aos serviços de SaaS da Microsoft, incluindo o Office 365 e Microsoft Intune Dynamics 365.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872262"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="8bfa2-103">Criação de rede para o Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="8bfa2-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="8bfa2-104">**Resumo:** Compreenda como otimizar sua rede para o acesso aos serviços de SaaS da Microsoft, incluindo o Office 365 e Microsoft Intune Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="8bfa2-105">Otimizando a sua rede de serviços Microsoft SaaS requer a configuração de internos e os dispositivos de borda para rotear as diferentes categorias de tráfego para os serviços Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="8bfa2-106">Etapas para preparar sua rede para serviços SaaS da Microsoft</span><span class="sxs-lookup"><span data-stu-id="8bfa2-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="8bfa2-107">Siga estas etapas para otimizar a sua rede de serviços SaaS da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="8bfa2-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="8bfa2-108">Percorra a seção de **etapas para preparar sua rede para serviços de nuvem da Microsoft** em [elementos comuns da conectividade de nuvem da Microsoft](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="8bfa2-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="8bfa2-109">Adicione uma conexão de Internet a cada um dos seus escritórios.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="8bfa2-110">Certifique-se de que os provedores para todas as conexões de Internet usam um servidor DNS com um endereço IP local.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="8bfa2-111">Examinar seu hairpins de rede, os destinos intermediários como serviços de segurança baseado em nuvem e eliminá-los a se possível.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="8bfa2-112">Configure os dispositivos de borda para ignorar o processamento da otimizar e permitir a categorias de tráfego do Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="8bfa2-113">Otimizando o tráfego para os serviços da Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="8bfa2-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="8bfa2-114">Existem três categorias de tráfego SaaS Microsoft:</span><span class="sxs-lookup"><span data-stu-id="8bfa2-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="8bfa2-115">Otimização</span><span class="sxs-lookup"><span data-stu-id="8bfa2-115">Optimize</span></span>

  <span data-ttu-id="8bfa2-116">Necessário para conectividade com cada serviço Microsoft SaaS e representam mais de 75% da largura de banda do Microsoft SaaS, conexões e volume de dados.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="8bfa2-117">Permitir</span><span class="sxs-lookup"><span data-stu-id="8bfa2-117">Allow</span></span>

  <span data-ttu-id="8bfa2-118">Necessário para conectividade para específica Microsoft SaaS serviços e recursos mas não são sensível aos desempenho da rede e latência como aqueles na categoria Optimize.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="8bfa2-119">Padrão</span><span class="sxs-lookup"><span data-stu-id="8bfa2-119">Default</span></span>

  <span data-ttu-id="8bfa2-p101">Representam os serviços Microsoft SaaS e dependências que não exigem qualquer otimização. Você pode tratar tráfego, categoria padrão como normal tráfego da Internet.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="8bfa2-122">**Figura 1: Configuração recomendada para o tráfego de Microsoft SaaS para todos os escritórios**</span><span class="sxs-lookup"><span data-stu-id="8bfa2-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Figura 1: Configuração recomendada para o tráfego de Microsoft SaaS para todos os escritórios](media/Network-Poster/SaaS1.png)

<span data-ttu-id="8bfa2-124">A Figura 1 mostra a configuração recomendada de todos os escritórios, incluindo filiais e aquelas regionais ou central, na qual:</span><span class="sxs-lookup"><span data-stu-id="8bfa2-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="8bfa2-125">Categoria **padrão** e gerais do tráfego da Internet é encaminhado para escritórios com servidores proxy e outros dispositivos de borda para oferecer proteção contra riscos de segurança baseado na Internet.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="8bfa2-126">**Otimizar** e **Permitir** tráfego de categoria é encaminhado diretamente até a borda do Microsoft rede front-end mais próxima do office que contém o usuário se conectando, ignorando servidores proxy e outros dispositivos de borda.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="8bfa2-127">Dispositivos de rede (SD-WAN) de área ampla definida pelo software nas filiais separam o tráfego para que:</span><span class="sxs-lookup"><span data-stu-id="8bfa2-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="8bfa2-128">Categoria **padrão** e gerais de tráfego de Internet vai para um escritório central ou regional sobre o backbone de rede de longa distância.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="8bfa2-129">**Otimizar** e **Permitir** o tráfego categoria vai para o ISP fornecendo a conexão de Internet local.</span><span class="sxs-lookup"><span data-stu-id="8bfa2-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="8bfa2-130">Para saber mais, confira:</span><span class="sxs-lookup"><span data-stu-id="8bfa2-130">For more information, see:</span></span>
  
- [<span data-ttu-id="8bfa2-131">Princípios de conectividade de rede</span><span class="sxs-lookup"><span data-stu-id="8bfa2-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="8bfa2-132">Planejamento de migração e rede para Office 365</span><span class="sxs-lookup"><span data-stu-id="8bfa2-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="8bfa2-133">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="8bfa2-133">Next step</span></span>

[<span data-ttu-id="8bfa2-134">Criação de rede para o Microsoft Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="8bfa2-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="8bfa2-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="8bfa2-135">See also</span></span>

[<span data-ttu-id="8bfa2-136">Rede do Microsoft Cloud para Arquitetos Corporativos</span><span class="sxs-lookup"><span data-stu-id="8bfa2-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="8bfa2-137">Recursos de arquitetura de TI do Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="8bfa2-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

