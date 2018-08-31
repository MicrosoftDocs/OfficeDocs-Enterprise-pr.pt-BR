---
title: Planejamento de migração e rede para o Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contém links para informações sobre o planejamento de rede e teste e migração para o Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223053"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="759f9-103">Planejamento de migração e rede para o Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="759f9-104">Este artigo contém links para informações sobre planejamento e teste de rede e migração para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="759f9-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="759f9-105">Antes de implantar pela primeira vez ou migrar para o Office 365, você pode usar as informações nestes tópicos para estimar a largura de banda necessária e, então, testar e verificar se você possui largura de banda suficiente para implantar ou migrar para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="759f9-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="759f9-106">Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="759f9-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![Consulte Microsoft Cloud Networking para pôster arquitetos da empresa](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="759f9-108">Para conhecer as etapas otimizar sua rede para o Office 365 e outras plataformas de nuvem da Microsoft e serviços, consulte o cartaz de [Rede da nuvem com a Microsoft para arquitetos da empresa](https://aka.ms/cloudarchnetworking) .</span><span class="sxs-lookup"><span data-stu-id="759f9-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="759f9-109">Estimar os requisitos de largura de banda de rede</span><span class="sxs-lookup"><span data-stu-id="759f9-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="759f9-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="759f9-110"></span></span>

<span data-ttu-id="759f9-p101">Usando o Office 365 pode aumentar a utilização de circuito de internet da sua organização. É importante determinar se a largura de banda disponível no momento é suficiente para lidar com o aumento estimado depois que o Office 365 é totalmente implantado, deixando pelo menos de 20% capacidade para lidar com mais visitados de dias.</span><span class="sxs-lookup"><span data-stu-id="759f9-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="759f9-113">Para estimar a largura de banda, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="759f9-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="759f9-p102">Avalie o número de clientes que usarão cada saída da Internet. Permitir que nossa rede multi-terabit manipular o máximo possível da conexão possível.</span><span class="sxs-lookup"><span data-stu-id="759f9-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="759f9-p103">Determine quais serviços do Office 365 e recursos estarão disponíveis para clientes usarem. Além disso, você provavelmente terá grupos de pessoas com diferentes serviços ou perfis de uso.</span><span class="sxs-lookup"><span data-stu-id="759f9-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="759f9-p104">Medir o uso de rede para um grupo piloto dos clientes. Certifique-se de que os clientes piloto são representativo de diferentes perfis de pessoas na organização, bem como os diferentes locais geográficos. Você pode cross-verificar os resultados em relação a nossas calculadoras antigos [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)e [Skype para negócios](https://go.microsoft.com/fwlink/p/?LinkId=321551) ou o [estudo de caso](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) que realizamos nossa própria rede.</span><span class="sxs-lookup"><span data-stu-id="759f9-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="759f9-121">Use as medidas do grupo piloto extrapolar necessidades da organização inteira e teste novamente para validar as estimativas antes de fazer alterações em sua rede.</span><span class="sxs-lookup"><span data-stu-id="759f9-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="759f9-122">Testar a sua rede existente</span><span class="sxs-lookup"><span data-stu-id="759f9-122">Test your existing network</span></span>
<span data-ttu-id="759f9-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="759f9-123"></span></span>

 <span data-ttu-id="759f9-p105">**Ferramentas de rede.** Testar e validar sua largura de banda da Internet para determinar as restrições de latência, upload e download. Essas ferramentas ajudarão você a determinar os recursos de rede para a migração, bem como após você totalmente estiver implantado.</span><span class="sxs-lookup"><span data-stu-id="759f9-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="759f9-p106">[Analisador de mensagem do Microsoft](https://technet.microsoft.com/library/jj649776.aspx): analisador de mensagem é uma ferramenta eficaz para solucionar possíveis problemas de rede. Analisador de mensagem captura, exibe e analisa o tráfego de mensagens baseada no protocolo e mensagens do sistema. Analisador de mensagem também permite importar, agregar e analisar dados de arquivos de log e rastreamento.</span><span class="sxs-lookup"><span data-stu-id="759f9-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="759f9-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): testa a conectividade em seu ambiente Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="759f9-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="759f9-131">Use o [Assistente de recuperação para o Office 365 e de suporte da Microsoft](https://diagnostics.office.com/#/Download?env=SOC) para corrigir problemas do Outlook e o Office 365.</span><span class="sxs-lookup"><span data-stu-id="759f9-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="759f9-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="759f9-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="759f9-133"></span></span>

<span data-ttu-id="759f9-134">Aprofundar um pouco nestas práticas recomendadas para obter mais informações sobre como melhorar sua experiência do Office 365.</span><span class="sxs-lookup"><span data-stu-id="759f9-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="759f9-p107">Deseja começar a ajudar seus usuários imediatamente? Consulte as [práticas recomendadas para usar o Office 365 em uma rede lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) para obter dicas sobre como usar o Office 365, incluindo o Exchange Online, SharePoint Online e Lync Online, quando sua rede simplesmente não trabalhar de forma. Este artigo vincula o check-out para cargas de conteúdo no TechNet e Support.office.com para otimizar sua experiência do Office 365 e inclui informações sobre fácil maneiras para personalizar suas páginas da web e como definir as configurações do Internet Explorer para a melhor experiência do Office 365.</span><span class="sxs-lookup"><span data-stu-id="759f9-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="759f9-p108">Leia os [Princípios de conectividade de rede do Office 365](https://aka.ms/o365networkingprinciples) para entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível. Este artigo ajudará você a entender as orientações mais recentes para otimizar com segurança de conectividade de rede do Office 365.</span><span class="sxs-lookup"><span data-stu-id="759f9-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="759f9-p109">Melhorar o desempenho de migração de email ao gerenciar cuidadosamente o agendamento de atualizações do Windows. Você pode atualizar os computadores cliente em lotes e certifique-se de que todos os computadores clientes sejam atualizados antes de migrar para o Office 365 para regular o uso da largura de banda de rede. Para obter mais informações, consulte [atualizar manualmente e configurar áreas de trabalho para o Office 365 para obter as atualizações mais recentes](https://support.microsoft.com/gp/office-2013-365-update).</span><span class="sxs-lookup"><span data-stu-id="759f9-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="759f9-p110">Tráfego de rede do Office 365 funciona melhor quando ele tem tratado como um serviço de Internet confiável e permitido para ignorar grande parte da filtragem tradicionais e verificação que algumas organizações colocar em tráfego de rede aos serviços de Internet não confiáveis. Isso geralmente inclui a remoção de saída de processamento, como a autenticação do usuário de proxy e inspeção de pacotes, bem como garantir a saída local para a Internet com a conversão de endereços de rede (NAT) adequadas e a capacidade de largura de banda suficiente para lidar com o aumento solicitações de rede. Consulte [Gerenciando o Office 365 pontos de extremidade](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)para obter orientação adicional sobre como configurar sua rede para lidar com o Office 365 como um serviço de Internet confiável em sua rede.</span><span class="sxs-lookup"><span data-stu-id="759f9-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="759f9-p111">Verifique se os [pontos de extremidade de gerenciamento do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). O tráfego adicional, indo para o Office 365 resulta em um aumento de conexões de saída de proxy, bem como um aumento no tráfego seguro sobre TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="759f9-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="759f9-p112">Se seu proxies de saída requerem autenticação de usuário que você pode enfrentar conectividade lenta ou uma perda de funcionalidade. Ignorar o requisito de autenticação para os domínios do Office 365 pode reduzir essa sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="759f9-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="759f9-p113">Se você possui um grande número de caixas de correio e calendários compartilhados, talvez você veja um aumento no número de conexões do Outlook para o Exchange. Por exemplo, o cliente do Outlook pode abrir até duas conexões adicionais para cada calendário compartilhado em uso. Neste caso, verifique se o proxy de saída pode lidar com as conexões ou ignorar o proxy para conexões com o Office 365 para o Outlook.</span><span class="sxs-lookup"><span data-stu-id="759f9-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="759f9-p114">Determine o número máximo de dispositivos suportados para um endereço IP público e como balancear a carga entre vários endereços IP. Para obter mais informações, consulte [suporte a NAT com o Office 365](nat-support-with-office-365.md).</span><span class="sxs-lookup"><span data-stu-id="759f9-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="759f9-p115">Se você estiver inspecionando conexões de saída de computadores em sua rede, ignorar essa filtragem para os domínios do Office 365 melhorará conectividade e desempenho. Além disso, ignorar inspeção de saída com frequência elimina a necessidade de uma única saída de Internet e habilita o local de saída da Internet para solicitações de rede de destino do Office 365.</span><span class="sxs-lookup"><span data-stu-id="759f9-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="759f9-p116">Alguns clientes encontrar as configurações de rede interna podem afetar o desempenho. Configurações como o tamanho de unidade (MTU) máxima da transmissão, negociação automática ou a detecção automática de rede e rotas abaixo do ideal para a Internet são locais comuns para procurar.</span><span class="sxs-lookup"><span data-stu-id="759f9-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="759f9-159">Referência de planejamento de rede para o Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="759f9-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="759f9-160"></span></span>

<span data-ttu-id="759f9-161">Estes tópicos contêm informações detalhadas de referência de rede do Office 365.</span><span class="sxs-lookup"><span data-stu-id="759f9-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="759f9-162">Gerenciando pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="759f9-163">Conectividade de cliente</span><span class="sxs-lookup"><span data-stu-id="759f9-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="759f9-164">Redes de distribuição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="759f9-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="759f9-165">Registros de Domain Name System externos para o Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="759f9-166">Suporte a IPv6 nos serviços do Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="759f9-167">Princípios de conectividade de rede do Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="759f9-168">Microsoft Virtual Academy: Gerenciamento de desempenho Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="759f9-169">Rede de vídeo do Office 365 frequentemente perguntas Frequentes</span><span class="sxs-lookup"><span data-stu-id="759f9-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="759f9-170">Planejar dispositivos de rede que se conectam aos serviços do Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="759f9-171">Supervisores de implantação para serviços do Office 365</span><span class="sxs-lookup"><span data-stu-id="759f9-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

