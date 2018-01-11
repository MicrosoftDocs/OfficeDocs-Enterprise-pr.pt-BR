---
title: "Mover dados de histórico de transação para a nuvem"
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
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: 'Resumo: Como Contoso implementou o SQL Server Alongar banco de dados para reduzir as suas necessidades de armazenamento de dados no local e diariamente executando os custos.'
ms.openlocfilehash: ef21b00f54fcc6efda2e83cb5952a99c7b8c8f28
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="bde5c-103">Mover dados de histórico de transação para a nuvem</span><span class="sxs-lookup"><span data-stu-id="bde5c-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="bde5c-104">**Resumo:** Como a Contoso implementou Alongar banco de dados do SQL Server para reduzir as suas necessidades de armazenamento de dados no local e diariamente executando os custos.</span><span class="sxs-lookup"><span data-stu-id="bde5c-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="bde5c-p101">Sistema de armazenamento corporativo da Contoso armazena uma grande quantidade de dados de histórico de transação para adesão com os requisitos normativos e para pesquisas de marketing e análise de tendências de gastos de BI. A Contoso também precisa restaurar os dados arquivados de fita magnético, um processo demorada. O hardware no sistema de armazenamento corporativo da Contoso estava perto de seu fim da vida útil e substitui-la seria muito caro.</span><span class="sxs-lookup"><span data-stu-id="bde5c-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="bde5c-p102">Como parte da sua necessidade comercial para dimensionar a seus centros de dados local, a Contoso optou por atualizar para o SQL Server 2016 devido ao recurso de híbrido de banco de dados Alongar e sua perfeita integração com o Windows Azure. Alongar do banco de dados permite que a Contoso mover os dados frio nas suas tabelas no local para armazenamento em nuvem, liberar espaço no disco local e reduzindo a manutenção. Dados quente e a frio são nas tabelas a mesma e estão sempre disponíveis para aplicativos e seus usuários e para manutenção, como backups e restaurações. A Figura 1 mostra Alongar banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bde5c-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="bde5c-112">**Figura 1: SQL Server Database Alongar**</span><span class="sxs-lookup"><span data-stu-id="bde5c-112">**Figure 1: SQL Server Stretch Database**</span></span>

![SQL Server Stretch Database como uma solução de dados híbrida](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="bde5c-114">A Figura 1 mostra como um cliente SQL envia consultas T-SQL para um servidor executando o SQL Server 2016, que encaminha para um banco de dados do Windows Azure SQL Alongar no Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="bde5c-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="bde5c-115">Para obter mais informações, consulte [Alongar banco de dados](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="bde5c-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="bde5c-116">Contoso usado estas etapas para mover seus dados históricos para a nuvem:</span><span class="sxs-lookup"><span data-stu-id="bde5c-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="bde5c-117">Analisar bancos de dados</span><span class="sxs-lookup"><span data-stu-id="bde5c-117">Analyze databases</span></span>
    
    <span data-ttu-id="bde5c-p103">Realizou uma análise das tabelas nos bancos de dados que eles foi projetado para mover para a nuvem e corrigido quaisquer problemas. Supervisor de banco de dados do novo Alongar deu-las uma visão geral do que eles podem esperar de todos os recursos no SQL Server 2016, incluindo quais tabelas tenham dados frio que poderiam ser alongados.</span><span class="sxs-lookup"><span data-stu-id="bde5c-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="bde5c-120">Atualizar</span><span class="sxs-lookup"><span data-stu-id="bde5c-120">Upgrade</span></span>
    
    <span data-ttu-id="bde5c-121">Atualizado servidores SQL existentes no datacenter Paris matrizes para 2016 do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bde5c-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="bde5c-122">Migrar dados frio para a nuvem</span><span class="sxs-lookup"><span data-stu-id="bde5c-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="bde5c-p104">Usando o SQL Management Studio, eles identificados alongar os bancos de dados e as tabelas para migrar para instâncias de banco de dados Alongar no Windows Azure. Ao longo do tempo e em segundo plano, SQL Server 2016 movidas os dados históricos para alongar bancos de dados no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="bde5c-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="bde5c-125">Aqui está a configuração resultante para um servidor executando o SQL Server 2016 da matriz da Paris.</span><span class="sxs-lookup"><span data-stu-id="bde5c-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="bde5c-126">**Figura 2: Usando o banco de dados de Alongar para um servidor em um datacenter da Contoso**</span><span class="sxs-lookup"><span data-stu-id="bde5c-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![SQL Server Stretch Database de configuração da Contoso para um único computador que executa o SQL Server](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="bde5c-128">A Figura 2 mostra como consultas de usuário para um servidor de aplicativos no datacenter da Contoso se tornam consultas SQL que são passadas para um banco de dados do Windows Azure SQL Alongar no Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="bde5c-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="bde5c-p105">Os usuários acessam os dados por meio de consultas e aplicativos existentes. Políticas de acesso permanecem os mesmos. Não é mais adiante, é necessário para backups em fita. Manutenção consiste em fazendo backup e restaurando dados hot.</span><span class="sxs-lookup"><span data-stu-id="bde5c-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="bde5c-133">Depois da implementação do banco de dados de alongar, Contoso:</span><span class="sxs-lookup"><span data-stu-id="bde5c-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="bde5c-134">Reduziu suas necessidades de armazenamento de dados local 85%.</span><span class="sxs-lookup"><span data-stu-id="bde5c-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="bde5c-135">A atualização do sistema de armazenamento da empresa e a dependência de arquivos em fita magnético feitas desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="bde5c-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="bde5c-136">Reduziu os seus custos de execução diários significativamente.</span><span class="sxs-lookup"><span data-stu-id="bde5c-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="bde5c-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="bde5c-137">See Also</span></span>

[<span data-ttu-id="bde5c-138">Cenários empresariais para a Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="bde5c-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="bde5c-139">Contoso na Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="bde5c-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="bde5c-140">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="bde5c-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="bde5c-141">Alongar para o banco de dados</span><span class="sxs-lookup"><span data-stu-id="bde5c-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="bde5c-142">Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="bde5c-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




