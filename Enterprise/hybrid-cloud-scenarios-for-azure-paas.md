---
title: "Cenários de nuvem híbrida para PaaS do Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Resumo: Entenda os cenários e arquitetura híbrida para a plataforma Microsoft como um serviço (PaaS)-based ofertas de nuvem no Windows Azure."
ms.openlocfilehash: 304322e5ad36f0a7f385a41fc3f2e5232dcecd69
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="582a2-103">Cenários de nuvem híbrida para PaaS do Azure</span><span class="sxs-lookup"><span data-stu-id="582a2-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="582a2-104">**Resumo:** Entenda os cenários e arquitetura híbrida para a plataforma Microsoft como um serviço (PaaS)-based ofertas de nuvem no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="582a2-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="582a2-105">Combinar os dados no local ou recursos de computação com aplicativos novos ou convertidos em execução no Azure PaaS, que podem tirar proveito de escala, confiabilidade e desempenho na nuvem e oferecer um suporte melhor para usuários móveis.</span><span class="sxs-lookup"><span data-stu-id="582a2-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="582a2-106">Arquitetura de cenário do Windows Azure PaaS híbrida</span><span class="sxs-lookup"><span data-stu-id="582a2-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="582a2-107">A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em PaaS Microsoft no Azure.</span><span class="sxs-lookup"><span data-stu-id="582a2-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="582a2-108">**Figura 1: Cenários de implantação híbrida baseada em PaaS Microsoft no Azure**</span><span class="sxs-lookup"><span data-stu-id="582a2-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Cenários híbridos da Microsoft baseados em PaaS no Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS.png)
  
<span data-ttu-id="582a2-110">Para cada camada da arquitetura:</span><span class="sxs-lookup"><span data-stu-id="582a2-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="582a2-111">Cenários e aplicativos</span><span class="sxs-lookup"><span data-stu-id="582a2-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="582a2-112">Um aplicativo de PaaS híbrido é executado no Windows Azure e usa os recursos de computação ou armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="582a2-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="582a2-113">Identidade</span><span class="sxs-lookup"><span data-stu-id="582a2-113">Identity</span></span>
    
    <span data-ttu-id="582a2-114">Consiste de sincronização de diretório ou federação com um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="582a2-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="582a2-115">Rede</span><span class="sxs-lookup"><span data-stu-id="582a2-115">Network</span></span>
    
    <span data-ttu-id="582a2-p101">Consiste em seu pipe Internet existente ou uma conexão ExpressRoute com correspondência pública para PaaS do Azure. Você deve incluir uma maneira para o aplicativo do Azure PaaS acessar o recurso de compute ou armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="582a2-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="582a2-118">Local</span><span class="sxs-lookup"><span data-stu-id="582a2-118">On-premises</span></span>
    
    <span data-ttu-id="582a2-119">Consiste em infraestrutura de segurança e de identidade e a linha existente de aplicativos de negócios (LOB) ou servidores de banco de dados, que um aplicativo do Windows Azure PaaS pode acessar com segurança.</span><span class="sxs-lookup"><span data-stu-id="582a2-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="582a2-120">Aplicativo do Azure PaaS híbrida</span><span class="sxs-lookup"><span data-stu-id="582a2-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="582a2-121">Figura 2 mostra a configuração de um aplicativo híbrida executando no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="582a2-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="582a2-122">**Figura 2: Aplicativo de implantação híbrida baseada em PaaS Azure**</span><span class="sxs-lookup"><span data-stu-id="582a2-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![Aplicativo híbrido baseado em PaaS no Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps.png)
  
<span data-ttu-id="582a2-p102">Na Figura 2, uma rede local hospeda aplicativos nos servidores e DMZ contendo um servidor proxy ou armazenamento. Ele está conectado aos serviços do Azure PaaS pela Internet ou com uma conexão ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="582a2-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="582a2-126">Uma organização pode tornar seus recursos de armazenamento ou compute disponíveis para o aplicativo de híbrido Azure PaaS por:</span><span class="sxs-lookup"><span data-stu-id="582a2-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="582a2-127">Hospedando o recurso em servidores no DMZ.</span><span class="sxs-lookup"><span data-stu-id="582a2-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="582a2-128">Hospedagem de um servidor proxy reverso no DMZ, que permite solicitações de entrada, autenticadas e baseada em HTTPS para o recurso que está localizado no local.</span><span class="sxs-lookup"><span data-stu-id="582a2-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="582a2-129">O aplicativo do Azure pode usar as credenciais a partir de:</span><span class="sxs-lookup"><span data-stu-id="582a2-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="582a2-130">Azure AD, que pode ser sincronizado com seu provedor de identidade de local, como o Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="582a2-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="582a2-131">Um provedor de identidade de terceiros.</span><span class="sxs-lookup"><span data-stu-id="582a2-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="582a2-132">Aplicativo do exemplo Azure PaaS híbrido</span><span class="sxs-lookup"><span data-stu-id="582a2-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="582a2-133">A Figura 3 mostra um exemplo de aplicativo híbrida executando no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="582a2-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="582a2-134">**Figura 3: Um exemplo aplicativo baseado no Windows Azure PaaS híbrido**</span><span class="sxs-lookup"><span data-stu-id="582a2-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![Um aplicativo híbrido de exemplo baseado em PaaS no Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_Ex.png)
  
<span data-ttu-id="582a2-p103">Na Figura 3, um hosts de rede local uma LOB App. Azure PaaS hospeda um aplicativo móvel personalizado. Um smartphone na Internet acessa o aplicativo móvel personalizado no Azure, que envia solicitações de dados para o aplicativo LOB local.</span><span class="sxs-lookup"><span data-stu-id="582a2-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="582a2-p104">Este exemplo de aplicativo do Windows Azure PaaS híbrido é um aplicativo móvel personalizado que fornece informações de contato atualizadas sobre funcionários. O cenário híbrido de ponta a ponta consiste em:</span><span class="sxs-lookup"><span data-stu-id="582a2-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="582a2-141">Um smartphone aplicativo que exige validado, credenciais de local para ser executado.</span><span class="sxs-lookup"><span data-stu-id="582a2-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="582a2-142">Um aplicativo móvel personalizado em execução no Azure PaaS, que solicita informações sobre funcionários específicos com base em consultas do aplicativo do smartphone de um usuário.</span><span class="sxs-lookup"><span data-stu-id="582a2-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="582a2-143">Um servidor proxy reverso no DMZ que valide o aplicativo móvel personalizado e encaminha a solicitação.</span><span class="sxs-lookup"><span data-stu-id="582a2-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="582a2-144">Um farm de servidores de aplicativos LOB que atende à solicitação de contato, sujeito as permissões da conta do usuário.</span><span class="sxs-lookup"><span data-stu-id="582a2-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="582a2-145">Porque o provedor de identidade local foi sincronizado com o Azure AD, o aplicativo móvel personalizado e o aplicativo LOB possam validar nome da conta do usuário solicitante.</span><span class="sxs-lookup"><span data-stu-id="582a2-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="stretch-database-with-sql-server-2016"></a><span data-ttu-id="582a2-146">Estender o banco de dados com o SQL Server 2016</span><span class="sxs-lookup"><span data-stu-id="582a2-146">Stretch Database with SQL Server 2016</span></span>

<span data-ttu-id="582a2-147">Alongar banco de dados é um recurso do SQL Server 2016 que permite transparente e segurança mover dados frio, como dados corporativos fechado em uma tabela grande que contém as informações de pedido de cliente, para um banco de dados SQL Alongar no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="582a2-147">Stretch database is a feature of SQL Server 2016 that allows you to transparently and securely move cold data, such as closed business data in a large table that contains customer order information, to a SQL Stretch database in Azure.</span></span>
  
<span data-ttu-id="582a2-p105">Quando alongado, o conteúdo de uma instância do SQL Server, um banco de dados ou até mesmo em uma única tabela é a combinação de dados local no servidor do SQL Server 2016 e dados remotos no Windows Azure. Dados que se tornará qualificados para alongar automaticamente são movidos para o Azure pelo 2016 do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="582a2-p105">When stretched, the contents of a SQL Server instance, a database, or even a single table is the combination of local data in SQL Server 2016 server and remote data in Azure. Data that becomes eligible for stretch is automatically moved to Azure by SQL Server 2016.</span></span>
  
<span data-ttu-id="582a2-150">Figura 4 mostra o banco de dados de alongar com 2016 do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="582a2-150">Figure 4 shows Stretch Database with SQL Server 2016.</span></span>
  
<span data-ttu-id="582a2-151">**Figura 4: Alongamento banco de dados com o SQL Server 2016**</span><span class="sxs-lookup"><span data-stu-id="582a2-151">**Figure 4: Stretch Database with SQL Server 2016**</span></span>

![Estender o banco de dados com o SQL Server 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_SQL.png)
  
<span data-ttu-id="582a2-p106">Na Figura 4, uma rede local hospeda um servidor executando o SQL Server 2016 com um pequeno banco de dados local. Azure PaaS hospeda uma instância do banco de dados do SQL Server Alongar Azure com a parte estendida do banco de dados. Consultas de T-SQL de um usuário local enviadas ao SQL server no local com segurança são encaminhadas para o Azure SQL Alongar banco de dados, que retorna os resultados ao usuário solicitante.</span><span class="sxs-lookup"><span data-stu-id="582a2-p106">In Figure 4, an on-premises network hosts a server running SQL Server 2016 with a small local database. Azure PaaS hosts an instance of Azure SQL Server Stretch Database with the stretched portion of the database. T-SQL queries from an on-premises user sent to the on-premises SQL server are securely forwarded to the Azure SQL Stretch Database, which returns the results to the requesting user.</span></span>
  
 <span data-ttu-id="582a2-p107">Consultas de usuário que incluem os dados históricos transparente são encaminhadas para o banco de dados Alongar do SQL Azure. As consultas não precisará ser escritos novamente, mesmo que a tabela é alongada.</span><span class="sxs-lookup"><span data-stu-id="582a2-p107">User queries that include the historical data are transparently forwarded to Azure SQL Stretch database. The queries do not need to be re-written, even though the table is stretched.</span></span>
  
<span data-ttu-id="582a2-p108">Banco de dados Alongar fornece uma opção econômica para armazenamento de longo prazo e transparente acesso a dados históricos. Ele também resolve problemas de desempenho e disponibilidade que surgem quando tabelas tornam-se muito grandes.</span><span class="sxs-lookup"><span data-stu-id="582a2-p108">Stretch database provides a cost-effective option for long-term storage and transparent access to historical data. It also solves performance and availability problems that arise when tables become very large.</span></span>
  
<span data-ttu-id="582a2-160">Para obter mais informações, consulte [Alongar banco de dados](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="582a2-160">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="582a2-161">Veja também</span><span class="sxs-lookup"><span data-stu-id="582a2-161">See Also</span></span>

[<span data-ttu-id="582a2-162">Nuvem híbrida da Microsoft para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="582a2-162">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="582a2-163">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="582a2-163">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="582a2-164">Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="582a2-164">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



