---
title: Mover os dados históricos de transação para a nuvem
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: 'Resumo: Como Contoso implementou o SQL Server Alongar banco de dados para reduzir as suas necessidades de armazenamento de dados no local e diariamente executando os custos.'
ms.openlocfilehash: 791b5d4f14ba7246221cf9b459c31c9ba1b54099
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915716"
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a>Mover os dados históricos de transação para a nuvem

 **Resumo:** Como a Contoso implementou Alongar banco de dados do SQL Server para reduzir as suas necessidades de armazenamento de dados no local e diariamente executando os custos.
  
Sistema de armazenamento corporativo da Contoso armazena uma grande quantidade de dados de histórico de transação para adesão com os requisitos normativos e para pesquisas de marketing e análise de tendências de gastos de BI. A Contoso também precisa restaurar os dados arquivados de fita magnético, um processo demorada. O hardware no sistema de armazenamento corporativo da Contoso estava perto de seu fim da vida útil e substitui-la seria muito caro. 
  
Como parte da sua necessidade comercial para dimensionar a seus centros de dados local, a Contoso optou por atualizar para o SQL Server 2016 devido ao recurso de híbrido de banco de dados Alongar e sua perfeita integração com o Windows Azure. Alongar do banco de dados permite que a Contoso mover os dados frio nas suas tabelas no local para armazenamento em nuvem, liberar espaço no disco local e reduzindo a manutenção. Dados quente e a frio são nas tabelas a mesma e estão sempre disponíveis para aplicativos e seus usuários e para manutenção, como backups e restaurações. A Figura 1 mostra Alongar banco de dados.
  
**Figura 1: SQL Server Database Alongar**

![SQL Server Stretch Database como uma solução de dados híbrida](media/Contoso-Poster/StretchDB01.png)
  
A Figura 1 mostra como um cliente SQL envia consultas T-SQL para um servidor executando o SQL Server 2016, que encaminha para um banco de dados do Windows Azure SQL Alongar no Azure PaaS.
  
Para obter mais informações, consulte [Alongar banco de dados](https://msdn.microsoft.com/library/dn935011.aspx).
  
Contoso usado estas etapas para mover seus dados históricos para a nuvem:
  
1. Analisar bancos de dados
    
    Realizou uma análise das tabelas nos bancos de dados que eles foi projetado para mover para a nuvem e corrigido quaisquer problemas. Supervisor de banco de dados do novo Alongar deu-las uma visão geral do que eles podem esperar de todos os recursos no SQL Server 2016, incluindo quais tabelas tenham dados frio que poderiam ser alongados.
    
2. Atualizar
    
    Atualizado servidores SQL existentes no datacenter Paris matrizes para 2016 do SQL Server.
    
3. Migrar dados frio para a nuvem
    
    Usando o SQL Management Studio, eles identificados alongar os bancos de dados e as tabelas para migrar para instâncias de banco de dados Alongar no Windows Azure. Ao longo do tempo e em segundo plano, SQL Server 2016 movidas os dados históricos para alongar bancos de dados no Windows Azure.
    
Aqui está a configuração resultante para um servidor executando o SQL Server 2016 da matriz da Paris.
  
**Figura 2: Usando o banco de dados de Alongar para um servidor em um datacenter da Contoso**

![SQL Server Stretch Database de configuração da Contoso para um único computador que executa o SQL Server](media/Contoso-Poster/StretchDB02.png)

  
A Figura 2 mostra como consultas de usuário para um servidor de aplicativos no datacenter da Contoso se tornam consultas SQL que são passadas para um banco de dados do Windows Azure SQL Alongar no Azure PaaS.
  
Os usuários acessam os dados por meio de consultas e aplicativos existentes. Políticas de acesso permanecem os mesmos. Não é mais adiante, é necessário para backups em fita. Manutenção consiste em fazendo backup e restaurando dados hot.
  
Depois da implementação do banco de dados de alongar, Contoso:
  
- Reduziu suas necessidades de armazenamento de dados local 85%.
    
- A atualização do sistema de armazenamento da empresa e a dependência de arquivos em fita magnético feitas desnecessárias.
    
- Reduziu os seus custos de execução diários significativamente.
    
## <a name="see-also"></a>Confira também

[Cenários empresariais para a Contoso Corporation](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Contoso no Microsoft Cloud](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitetura de TI da Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

[Alongar para o banco de dados](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)




