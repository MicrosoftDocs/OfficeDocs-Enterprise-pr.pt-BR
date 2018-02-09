---
title: "Criação de ponta a ponta para cima"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "Resumo: Conheça os detalhes sobre o conjunto de nuvem blocos de construção de armazenamento que você pode usar para criar seu próprio serviço de armazenamento ou a solução."
ms.openlocfilehash: be7ea3e7526115f1a983ec89f2afeb5d130daee1
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="54f7f-103">Criação de ponta a ponta para cima</span><span class="sxs-lookup"><span data-stu-id="54f7f-103">Build from the ground up</span></span>

 <span data-ttu-id="54f7f-104">**Resumo:** Obtenha os detalhes sobre o conjunto de nuvem blocos de construção de armazenamento que você pode usar para criar seu próprio serviço de armazenamento ou a solução.</span><span class="sxs-lookup"><span data-stu-id="54f7f-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="54f7f-105">Soluções de armazenamento "Build de ponta a ponta para cima":</span><span class="sxs-lookup"><span data-stu-id="54f7f-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="54f7f-106">Permitem que você criar sua própria solução de armazenamento a partir do zero.</span><span class="sxs-lookup"><span data-stu-id="54f7f-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="54f7f-107">Requer programação usando as APIs REST.</span><span class="sxs-lookup"><span data-stu-id="54f7f-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="54f7f-108">Forneça o máximo em flexibilidade e personalização.</span><span class="sxs-lookup"><span data-stu-id="54f7f-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="54f7f-109">As seções a seguir descrevem os detalhes de cada opção de armazenamento "Build de ponta a ponta para cima".</span><span class="sxs-lookup"><span data-stu-id="54f7f-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="54f7f-110">Armazenamento do Azure (arquivos)</span><span class="sxs-lookup"><span data-stu-id="54f7f-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="54f7f-111">Recursos</span><span class="sxs-lookup"><span data-stu-id="54f7f-111">Features</span></span>

- <span data-ttu-id="54f7f-112">Torna mais fácil mover aplicativos herdados para a nuvem</span><span class="sxs-lookup"><span data-stu-id="54f7f-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="54f7f-113">Armazenamento de blob preferido para novos aplicativos</span><span class="sxs-lookup"><span data-stu-id="54f7f-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="54f7f-114">Pode montar a partir de uma máquina virtual do Azure</span><span class="sxs-lookup"><span data-stu-id="54f7f-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="54f7f-115">Pode montar local com SMB 3.0</span><span class="sxs-lookup"><span data-stu-id="54f7f-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="54f7f-116">Funciona com Linux e Windows</span><span class="sxs-lookup"><span data-stu-id="54f7f-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="54f7f-117">Não oferece suporte a autenticação baseada em AD Azure ou ACLs (chaves de conta de armazenamento do Azure fornecem autenticação e acesso autorizado para o compartilhamento de arquivos)</span><span class="sxs-lookup"><span data-stu-id="54f7f-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="54f7f-118">Usos comuns</span><span class="sxs-lookup"><span data-stu-id="54f7f-118">Common uses</span></span>

- <span data-ttu-id="54f7f-119">Migrando aplicativos herdados para a nuvem que se baseiam nos compartilhamentos de arquivos</span><span class="sxs-lookup"><span data-stu-id="54f7f-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="54f7f-120">Compartilhar ferramentas de desenvolvimento e testes</span><span class="sxs-lookup"><span data-stu-id="54f7f-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="54f7f-121">Aplicativos distribuídos podem armazenar logs, dados de diagnóstico e despejos</span><span class="sxs-lookup"><span data-stu-id="54f7f-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="54f7f-122">Cenários de armazenamento de chave</span><span class="sxs-lookup"><span data-stu-id="54f7f-122">Key storage scenarios</span></span>

- <span data-ttu-id="54f7f-123">Arquivos de backup</span><span class="sxs-lookup"><span data-stu-id="54f7f-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="54f7f-124">Recursos</span><span class="sxs-lookup"><span data-stu-id="54f7f-124">Resources</span></span>

<span data-ttu-id="54f7f-125">Para obter informações adicionais, clique [aqui](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span><span class="sxs-lookup"><span data-stu-id="54f7f-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="54f7f-126">Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="54f7f-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="54f7f-127">Armazenamento (blobs) do Azure</span><span class="sxs-lookup"><span data-stu-id="54f7f-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="54f7f-128">Recursos</span><span class="sxs-lookup"><span data-stu-id="54f7f-128">Features</span></span>

- <span data-ttu-id="54f7f-129">Cada conta de armazenamento pode conter até 500 TB (uma assinatura pode ter várias contas de armazenamento)</span><span class="sxs-lookup"><span data-stu-id="54f7f-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="54f7f-130">Contas de armazenamento são organizadas em recipientes, que podem ter segurança aplicada aos mesmos e podem conter blobs</span><span class="sxs-lookup"><span data-stu-id="54f7f-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="54f7f-131">Bloquear blobs otimizados para o streaming e armazenando nuvem objetos, em tamanho até 200 GB</span><span class="sxs-lookup"><span data-stu-id="54f7f-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="54f7f-132">Página blobs otimizados para representar PaaS discos e suporte aleatório grava, até 1 TB em tamanho</span><span class="sxs-lookup"><span data-stu-id="54f7f-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="54f7f-133">Acrescentar blobs otimizados para acrescentar operações, até 195 GB</span><span class="sxs-lookup"><span data-stu-id="54f7f-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="54f7f-134">Armazenamento Premium fornece mais rápidos IOPS por meio do armazenamento SSD</span><span class="sxs-lookup"><span data-stu-id="54f7f-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="54f7f-135">Usos comuns</span><span class="sxs-lookup"><span data-stu-id="54f7f-135">Common uses</span></span>

- <span data-ttu-id="54f7f-136">Backups dos dispositivos, computadores, bancos de dados e arquivos de imagens e texto para aplicativos web</span><span class="sxs-lookup"><span data-stu-id="54f7f-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="54f7f-137">Dados de configuração para aplicativos em nuvem</span><span class="sxs-lookup"><span data-stu-id="54f7f-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="54f7f-138">Dados grandes, como logs e outros conjuntos de dados grandes</span><span class="sxs-lookup"><span data-stu-id="54f7f-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="54f7f-139">Armazenamento para seus próprios serviços, como discos HDInsight e máquina virtual de blob de usos do Azure</span><span class="sxs-lookup"><span data-stu-id="54f7f-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="54f7f-140">Cenários de armazenamento de chave</span><span class="sxs-lookup"><span data-stu-id="54f7f-140">Key storage scenarios</span></span>

- <span data-ttu-id="54f7f-141">Gerenciar dados</span><span class="sxs-lookup"><span data-stu-id="54f7f-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="54f7f-142">Recursos</span><span class="sxs-lookup"><span data-stu-id="54f7f-142">Resources</span></span>

<span data-ttu-id="54f7f-143">Para obter informações adicionais, clique [aqui](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span><span class="sxs-lookup"><span data-stu-id="54f7f-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="54f7f-144">Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="54f7f-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="54f7f-145">Armazenamento do Azure (filas)</span><span class="sxs-lookup"><span data-stu-id="54f7f-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="54f7f-146">Recursos</span><span class="sxs-lookup"><span data-stu-id="54f7f-146">Features</span></span>

- <span data-ttu-id="54f7f-147">Conta de armazenamento pode conter qualquer número de filas</span><span class="sxs-lookup"><span data-stu-id="54f7f-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="54f7f-148">Fila pode conter qualquer número de mensagens (até que a conta de armazenamento está cheio)</span><span class="sxs-lookup"><span data-stu-id="54f7f-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="54f7f-149">Mensagens da fila são automaticamente excluídas após sete dias se não recuperadas e excluídas por um aplicativo</span><span class="sxs-lookup"><span data-stu-id="54f7f-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="54f7f-150">As mensagens podem ter até 64 KB em tamanho</span><span class="sxs-lookup"><span data-stu-id="54f7f-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="54f7f-151">Protegido no nível da conta de armazenamento</span><span class="sxs-lookup"><span data-stu-id="54f7f-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="54f7f-152">Filas servem para passar o controle de mensagens, dados não processados</span><span class="sxs-lookup"><span data-stu-id="54f7f-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="54f7f-153">Usos comuns</span><span class="sxs-lookup"><span data-stu-id="54f7f-153">Common uses</span></span>

- <span data-ttu-id="54f7f-154">Criar um registro posterior de trabalho para processar de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="54f7f-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="54f7f-155">Processamento de mensagens de log</span><span class="sxs-lookup"><span data-stu-id="54f7f-155">Processing log messages</span></span>
    
- <span data-ttu-id="54f7f-156">Desassociar aplicativos</span><span class="sxs-lookup"><span data-stu-id="54f7f-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="54f7f-157">Cenários de armazenamento de chave</span><span class="sxs-lookup"><span data-stu-id="54f7f-157">Key storage scenarios</span></span>

- <span data-ttu-id="54f7f-158">Distribuir eventos</span><span class="sxs-lookup"><span data-stu-id="54f7f-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="54f7f-159">Recursos</span><span class="sxs-lookup"><span data-stu-id="54f7f-159">Resources</span></span>

<span data-ttu-id="54f7f-160">Para obter informações adicionais, clique [aqui](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span><span class="sxs-lookup"><span data-stu-id="54f7f-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="54f7f-161">Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="54f7f-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="54f7f-162">Armazenamento do Azure (tabelas)</span><span class="sxs-lookup"><span data-stu-id="54f7f-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="54f7f-163">Recursos</span><span class="sxs-lookup"><span data-stu-id="54f7f-163">Features</span></span>

- <span data-ttu-id="54f7f-164">Melhor para conjuntos de dados semi-estruturados</span><span class="sxs-lookup"><span data-stu-id="54f7f-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="54f7f-165">Geralmente custo menor do que o SQL tradicional</span><span class="sxs-lookup"><span data-stu-id="54f7f-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="54f7f-166">Muito rápido se consultando para chave, lento se consultando o valor</span><span class="sxs-lookup"><span data-stu-id="54f7f-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="54f7f-167">Amplamente dimensionável; qualquer quantidade de tabelas até os limites da conta de armazenamento</span><span class="sxs-lookup"><span data-stu-id="54f7f-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="54f7f-168">Acessível através da API REST, o protocolo oData limitado, .NET</span><span class="sxs-lookup"><span data-stu-id="54f7f-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="54f7f-169">Os valores devem ser serializados</span><span class="sxs-lookup"><span data-stu-id="54f7f-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="54f7f-170">Usos comuns</span><span class="sxs-lookup"><span data-stu-id="54f7f-170">Common uses</span></span>

- <span data-ttu-id="54f7f-171">Dados de usuário para aplicativos web</span><span class="sxs-lookup"><span data-stu-id="54f7f-171">User data for web applications</span></span>
    
- <span data-ttu-id="54f7f-172">Catálogos de endereços</span><span class="sxs-lookup"><span data-stu-id="54f7f-172">Address books</span></span>
    
- <span data-ttu-id="54f7f-173">Informações do dispositivo</span><span class="sxs-lookup"><span data-stu-id="54f7f-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="54f7f-174">Cenários de armazenamento de chave</span><span class="sxs-lookup"><span data-stu-id="54f7f-174">Key storage scenarios</span></span>

- <span data-ttu-id="54f7f-175">Gerenciar dados</span><span class="sxs-lookup"><span data-stu-id="54f7f-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="54f7f-176">Recursos</span><span class="sxs-lookup"><span data-stu-id="54f7f-176">Resources</span></span>

<span data-ttu-id="54f7f-177">Para obter informações adicionais, clique [aqui](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span><span class="sxs-lookup"><span data-stu-id="54f7f-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="54f7f-178">Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="54f7f-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="54f7f-179">Recomendações de armazenamento do Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="54f7f-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="54f7f-180">Ao projetar sua solução de armazenamento personalizada com o armazenamento do Windows Azure, lembre-se do seguinte:</span><span class="sxs-lookup"><span data-stu-id="54f7f-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="54f7f-181">Aproveite as várias contas de armazenamento maior escalabilidade, para maior tamanho (> 100 TB) ou para taxa de transferência mais (> 5.000 operações por segundo).</span><span class="sxs-lookup"><span data-stu-id="54f7f-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="54f7f-182">Projete a capacidade para adicionar contas de armazenamento adicional, como uma alteração de configuração, e não como uma alteração de código.</span><span class="sxs-lookup"><span data-stu-id="54f7f-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="54f7f-183">Selecione cuidadosamente o particionamento de funções para o armazenamento de tabela habilitar a escala desejada em termos de desempenho de inserção e de consulta.</span><span class="sxs-lookup"><span data-stu-id="54f7f-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="54f7f-184">Escolha nomes de coluna curta para propriedades de tabela como os metadados (nomes de propriedade) são armazenados em banda (os nomes de coluna também é levada em contagem o tamanho máximo de linha de 1 MB).</span><span class="sxs-lookup"><span data-stu-id="54f7f-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="54f7f-185">Quando possível, operações em armazenamento em lotes.</span><span class="sxs-lookup"><span data-stu-id="54f7f-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="54f7f-186">Cache agressivamente informações do banco de dados de configuração em um cache distribuído.</span><span class="sxs-lookup"><span data-stu-id="54f7f-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="54f7f-187">Se o desempenho de aplicativos ou confiabilidade depender tendo um determinado segmento de dados disponíveis no cache, seu aplicativo deve recusar solicitações de entrada até que o cache tenha sido previamente definido.</span><span class="sxs-lookup"><span data-stu-id="54f7f-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="54f7f-188">Particione os dados em um verticalmente (pela tabela) ou horizontalmente (tabela de segmento entre vários fragmentos) para distribuir a carga em vários bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="54f7f-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="54f7f-189">Veja também</span><span class="sxs-lookup"><span data-stu-id="54f7f-189">See Also</span></span>

[<span data-ttu-id="54f7f-190">Armazenamento do Microsoft Cloud para arquitetos corporativos</span><span class="sxs-lookup"><span data-stu-id="54f7f-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="54f7f-191">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="54f7f-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="54f7f-192">Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="54f7f-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



