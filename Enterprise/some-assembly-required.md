---
title: "Alguns assembly necessário"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: "Resumo: Conheça os detalhes sobre o conjunto de opções de armazenamento de nuvem que você pode usar para criar sua solução de armazenamento personalizado."
ms.openlocfilehash: bf6f7586b3a890cd25aba314e4892d5e2ac5bb34
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="some-assembly-required"></a>Alguns assembly necessário

 **Resumo:** Obtenha os detalhes sobre o conjunto de nuvem opções de armazenamento que você pode usar para criar sua solução de armazenamento personalizado.
  
Soluções de armazenamento de "Alguns assembly necessário":
  
- Use serviços existentes como um ponto de partida para sua solução de armazenamento.
    
- Exigem alguma configuração ou codificação.
    
- Pode ser personalizada para atender às suas necessidades.
    
As seções a seguir descrevem os detalhes de cada solução de armazenamento "Alguns assembly necessário".
  
## <a name="azure-content-delivery-network"></a>Rede de fornecimento de conteúdo do Azure

### <a name="features"></a>Recursos

- Análise de tempo real e avançada
    
- Segurança robusta contra DDoS
    
- Obtém conteúdo automaticamente de um site do Windows Azure ou o serviço de nuvem do Windows Azure depois que você configurar a integração
    
- Nova parceria com Akamai
    
- Pode manipular os picos de tráfego repentinas e pesadas
    
### <a name="common-uses"></a>Usos comuns

- Distribuir áudio, vídeo, aplicativos, imagens e outros arquivos rápido e mais confiável para clientes usando os servidores que estejam mais próximos a eles
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
- Gerenciar vídeos
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://azure.microsoft.com/services/cdn/).
  
Para obter informações de custo, clique [aqui](https://azure.microsoft.com/pricing/details/cdn/).
  
## <a name="hdinsight"></a>HdInsight

### <a name="features"></a>Recursos

- Distribuição de Hadoop Apache possibilitada pela nuvem serviço uma dados Lake
    
- Dimensionar a petabytes sob demanda
    
- Processar dados não estruturados e semi-estruturados Develop em Java, .NET e muito mais
    
- Ignore a aquisição e manutenção de hardware
    
- Conectar os clusters de Hadoop local com a nuvem
    
- Flexibilidade para implantar arbitrários projetos Hadoop através de scripts personalizados (por exemplo, R, Giraph, Solr)
    
### <a name="common-uses"></a>Usos comuns

- Cargas de trabalho de análise de dados
    
- Estrutura de processamento de dados na memória para grandes dados (Spark)
    
- Processamento de fluxo em tempo real (tempestade)
    
- Processamento transacional grande (OLTP) de dados não-relacionais (HBase)
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://azure.microsoft.com/services/hdinsight/).
  
Para obter informações de custo, clique [aqui](https://azure.microsoft.com/pricing/details/hdinsight/).
  
## <a name="azure-sql-database"></a>Banco de Dados SQL Azure

### <a name="features"></a>Recursos

- Otimizada para reduzir os custos e gerenciamento
    
- Atualização, recuperação de desastres e alta disponibilidade automática
    
- Recomendada para organizações Gerenciando centenas ou milhares de bancos de dados de até 1 TB em tamanho
    
- Técnicas de fragmentação podem dividir dados em bancos de dados para armazenamento aumentada
    
- Alongar para o banco de dados com o SQL Server 2016
    
### <a name="common-uses"></a>Usos comuns

- Novos aplicativos projetados para nuvem com dados relacionais
    
- Processamento de dados sobre conjuntos de dados de esquema, altamente estruturados com relações
    
- Dados espaciais ou tipos de dados avançados
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
### <a name="elastic-database"></a>Banco de dados Elástico

Use os recursos praticamente ilimitados do SQL Azure do banco de dados quando:
  
- A quantidade total de dados é muito grande para caber dentro das restrições de um único banco de dados.
    
- A taxa de transferência da transação da carga de trabalho geral excede os recursos de um único banco de dados.
    
- Inquilinos exigem o isolamento físico entre si, portanto, bancos de dados separados são necessários para cada inquilino.
    
- Precisam residem em diferentes regiões geográficas para conformidade, desempenho ou geopolíticas razões diferentes seções de um banco de dados.
    
Com o dimensionamento vertical, você pode alterar o nível de desempenho de banco de dados do Azure/edition ou usando pools elástica do banco de dados.
  
![Dimensionamento vertical fornecido pelo Banco de Dados SQL do Azure.](images/Storage_Poster/CloudStor-VertScale.png)
  
Com o dimensionamento horizontal, você pode adicionar novos bancos de dados, conforme necessário.
  
![Dimensionamento horizontal fornecido pelo Banco de Dados SQL do Azure.](images/Storage_Poster/CloudStor-HorizScale.png)
  
Clique [aqui](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction) para obter mais informações.
  
### <a name="stretch-database-with-sql-server-2016"></a>Estender o banco de dados com o SQL Server 2016

Alongar banco de dados é um recurso do SQL Server 2016 que permite transparente e segurança mover dados frio, como dados corporativos fechado em uma tabela grande que contém as informações de pedido de cliente, para um banco de dados SQL Alongar no Windows Azure. Quando alongado, o conteúdo de uma instância do SQL Server, um banco de dados ou até mesmo em uma única tabela é a combinação de dados local no servidor do SQL Server 2016 e dados remotos no Windows Azure. Dados que se tornará qualificados para alongar automaticamente são movidos para o Azure pelo 2016 do SQL Server.
  
![Estender o banco de dados com o SQL Server 2016.](images/Storage_Poster/CloudStor-Stretch.png)
  
Consultas de usuário que incluem os dados históricos transparente são encaminhadas para o banco de dados Alongar do SQL Azure. As consultas não precisará ser escritos novamente, mesmo que a tabela é alongada.
  
Banco de dados Alongar fornece uma opção econômica para armazenamento de longo prazo e transparente acesso a dados históricos. Ele também resolve problemas de desempenho e disponibilidade que surgem quando tabelas tornam-se muito grandes.
  
Clique [aqui](https://msdn.microsoft.com/library/dn935011.aspx) para obter mais informações.
  
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](http://azure.microsoft.com/services/sql-database/).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/sql-database/).
  
## <a name="azure-cosmos-db"></a>Azure Cosmos DB

### <a name="features"></a>Recursos

- Há uma garantia de baixa latência e SLA de disponibilidade de 99,99% com escala ilimitada, elástica de armazenamento e a taxa de transferência
    
- Todos os dados é globalmente replicadas em qualquer número de regiões com failover transparente e quatro níveis de consistência bem definida
    
- Indexa automaticamente todos os seus dados sem a necessidade de esquemas ou índices secundários
    
- Transações de item multi e consultas SQL de Rich e JavaScript
    
### <a name="common-uses"></a>Usos comuns

- IoT, Mobile e Social
    
- Jogos
    
- Varejo
    
- Gerenciamento de conteúdo
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
### <a name="cosmos-db-vs-azure-tables-vs-azure-sql-database"></a>O banco de dados do cosmos DB versus Azure tabelas versus Azure SQL

Atributos comuns de Cosmos DB, o armazenamento de tabela do Windows Azure e o banco de dados do Windows Azure SQL:
  
- SLA de disponibilidade 99.99
    
- Serviços de banco de dados totalmente gerenciado
    
- ISO 27001, HIPAA e compatível com as cláusulas de modelo da UE
    
A tabela a seguir mostra os atributos incomuns do Azure Cosmos DB, o armazenamento de tabela do Windows Azure e banco de dados de SQL Azure.
  
![Atributos incomuns do Cosmos DB vs. Tabelas do Azure vs. Banco de Dados SQL do Azure](images/Storage_Poster/CloudStor-Table.png)
  
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](http://azure.microsoft.com/services/documentdb/).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/documentdb/).
  
## <a name="azure-media-services"></a>Azure Media Services

### <a name="features"></a>Recursos

- Ao vivo e vídeo na entrega por demanda (VOD) com escala
    
- Codificação altamente disponível e streaming
    
- Suporta Flash, iOS, Android, HTML5 e Xbox
    
- Suporte DRM certificado Studio
    
- Monetização de conteúdo avançado
    
- Amplo ecossistema de parceiros previamente integrados
    
### <a name="common-uses"></a>Usos comuns

- Codificar, armazenar e transmitir áudio e vídeo em escala
    
- Streaming de tempo real e VOD
    
- Gerenciamento de conteúdo de vídeo simplificado
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar vídeos
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://azure.microsoft.com/services/media-services/).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/media-services/).
  
## <a name="azure-redis-cache"></a>Cache do Azure relacionada

### <a name="features"></a>Recursos

- Servidor seguro e dedicado relacionada com alta disponibilidade com failover gerenciados pela Microsoft e replicação de dados
    
- Recomendado para qualquer aplicativo que precisam de alta taxa de transferência
    
- Disponível em dimensiona até 530 GB e além (com Premium e fragmentação automática)
    
- Persistência relacionada persiste na memória cache de dados para o armazenamento do Windows Azure
    
- Clustering relacionada permite obter a taxa de transferência e a escala máxima
    
- Isolamento de segurança e rede avançado com suporte de rede Virtual do Azure
    
### <a name="common-uses"></a>Usos comuns

- Pesquisa inversa de dados em qualquer serviço de armazenamento no Windows Azure, como Cosmos DB e o banco de dados de SQL Azure
    
- Conteúdo sincronizado de outras fontes de dados
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Cache de dados
    
- Agente de mensagem para aplicativos de alta taxa de transferência
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](http://azure.microsoft.com/services/cache/).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/cache/).
  
## <a name="sql-server-on-an-azure-vm"></a>SQL Server em uma VM Azure

### <a name="features"></a>Recursos

- SQL Server em execução como um aplicativo instalado em uma máquina virtual do Azure
    
- Usar uma imagem da galeria com o SQL Server instalado ou trazer sua própria licença do SQL Server
    
### <a name="common-uses"></a>Usos comuns

- Gerenciar dados de aplicativos
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](http://azure.microsoft.com/services/virtual-machines/).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/virtual-machines/).
  
## <a name="storsimple"></a>Desempenho do StorSimple

### <a name="features"></a>Recursos

- Armazenamento de SAN com SSD e HDD na matriz de armazenamento local híbrida, com armazenamento em nuvem como uma extensão integrada da solução híbrida de escalável, enterprise
    
- Dados estruturados de eliminação da duplicação de embutida, compactação, hierarquia automática e não estruturados de criptografia e parcialmente
    
- Proteção de dados de externa automatizado usando instantâneos de nuvem
    
- Recuperação de desastres altamente eficiente, independente de local
    
- Mobilidade de dados para dados corporativos com o aparelho de desempenho do StorSimple virtuais no Windows Azure
    
### <a name="common-uses"></a>Usos comuns

- Gerenciar o crescimento de dados relacionado ao compartilhamentos de arquivos, os arquivos e outros repositórios de dados
    
- Externo dados proteção e recuperação de desastres para máquinas virtuais, compartilhamentos de arquivos, SQL e SharePoint (usando o Remote Blob Storage)
    
- Utilizar instantâneos de nuvem para clonar dados no Windows Azure e aumentar a agilidade dos negócios
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
- Colaborar
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](http://azure.microsoft.com/services/storsimple/).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storsimple/).
  
## <a name="azure-sql-data-warehouse"></a>Armazém de dados do SQL Azure

### <a name="features"></a>Recursos

- Armazém de dados elástica que pode chegar a petabytes até 32 consultas simultâneas
    
- Gerenciar grandes volumes de dados estruturados com fast analytics dinamicamente crescer e encolher compute em segundos
    
- Oferece suporte à criptografia de dados transparente
    
- O backup de cada 8 horas para 7 dias
    
### <a name="common-uses"></a>Usos comuns

- Relatórios de vendas
    
- Relatórios de uso
    
- Muitos dados
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://azure.microsoft.com/services/sql-data-warehouse/).
  
Para obter informações de custo, clique [aqui](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).
  
## <a name="azure-data-lake-store"></a>Repositório de Lake de dados do Windows Azure

### <a name="features"></a>Recursos

- Um repositório de hyper-escala para cargas de trabalho de análise de dados grande
    
- Um sistema de arquivos do Hadoop distribuído para a nuvem
    
- Sem fixos limites de tamanho de arquivo
    
- Sem limites fixos no tamanho de conta
    
- Dados não estruturados e estruturados no formato nativo
    
- Taxa de transferência enorme para aumentar o desempenho analítico
    
- Alta durabilidade, disponibilidade e confiabilidade (SLA de nível empresarial 99,9% e suporte 24/7)
    
- Controle de acesso do Azure Active Directory
    
### <a name="common-uses"></a>Usos comuns

- Repositório de toda a empresa para armazenar cada tipo de dados coletados em um único lugar
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://azure.microsoft.com/services/data-lake-store/).
  
Para obter informações de custo, clique [aqui](https://azure.microsoft.com/pricing/details/data-lake-store/).
  
## <a name="next-step"></a>Próxima etapa

Examine as opções de armazenamento de nuvem [construir a partir do zero](build-from-the-ground-up.md) .
  
## <a name="see-also"></a>See Also

[Armazenamento em nuvem da Microsoft para arquitetos da empresa](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



