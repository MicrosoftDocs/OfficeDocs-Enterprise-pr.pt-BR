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
ms.openlocfilehash: eabf38e0ccef3335b2d198a33f5622d0d449589a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="build-from-the-ground-up"></a>Criação de ponta a ponta para cima

 **Resumo:** Obtenha os detalhes sobre o conjunto de nuvem blocos de construção de armazenamento que você pode usar para criar seu próprio serviço de armazenamento ou a solução.
  
Soluções de armazenamento "Build de ponta a ponta para cima":
  
- Permitem que você criar sua própria solução de armazenamento a partir do zero. 
    
- Requer programação usando as APIs REST.
    
- Forneça o máximo em flexibilidade e personalização.
    
As seções a seguir descrevem os detalhes de cada opção de armazenamento "Build de ponta a ponta para cima".
  
## <a name="azure-storage-files"></a>Armazenamento do Azure (arquivos)

### <a name="features"></a>Recursos

- Torna mais fácil mover aplicativos herdados para a nuvem
    
- Armazenamento de blob preferido para novos aplicativos
    
- Pode montar a partir de uma máquina virtual do Azure
    
- Pode montar local com SMB 3.0
    
- Funciona com Linux e Windows
    
- Não oferece suporte a autenticação baseada em AD Azure ou ACLs (chaves de conta de armazenamento do Azure fornecem autenticação e acesso autorizado para o compartilhamento de arquivos)
    
### <a name="common-uses"></a>Usos comuns

- Migrando aplicativos herdados para a nuvem que se baseiam nos compartilhamentos de arquivos
    
- Compartilhar ferramentas de desenvolvimento e testes
    
- Aplicativos distribuídos podem armazenar logs, dados de diagnóstico e despejos
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Arquivos de backup
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://msdn.microsoft.com/library/azure/dn166972.aspx).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-blobs"></a>Armazenamento (blobs) do Azure

### <a name="features"></a>Recursos

- Cada conta de armazenamento pode conter até 500 TB (uma assinatura pode ter várias contas de armazenamento)
    
- Contas de armazenamento são organizadas em recipientes, que podem ter segurança aplicada aos mesmos e podem conter blobs
    
- Bloquear blobs otimizados para o streaming e armazenando nuvem objetos, em tamanho até 200 GB
    
- Página blobs otimizados para representar PaaS discos e suporte aleatório grava, até 1 TB em tamanho
    
- Acrescentar blobs otimizados para acrescentar operações, até 195 GB
    
- Armazenamento Premium fornece mais rápidos IOPS por meio do armazenamento SSD
    
### <a name="common-uses"></a>Usos comuns

- Backups dos dispositivos, computadores, bancos de dados e arquivos de imagens e texto para aplicativos web
    
- Dados de configuração para aplicativos em nuvem
    
- Dados grandes, como logs e outros conjuntos de dados grandes
    
- Armazenamento para seus próprios serviços, como discos HDInsight e máquina virtual de blob de usos do Azure
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://msdn.microsoft.com/library/azure/dd179376.aspx).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-queues"></a>Armazenamento do Azure (filas)

### <a name="features"></a>Recursos

- Conta de armazenamento pode conter qualquer número de filas
    
- Fila pode conter qualquer número de mensagens (até que a conta de armazenamento está cheio)
    
- Mensagens da fila são automaticamente excluídas após sete dias se não recuperadas e excluídas por um aplicativo
    
- As mensagens podem ter até 64 KB em tamanho
    
- Protegido no nível da conta de armazenamento
    
- Filas servem para passar o controle de mensagens, dados não processados
    
### <a name="common-uses"></a>Usos comuns

- Criar um registro posterior de trabalho para processar de forma assíncrona
    
- Processamento de mensagens de log
    
- Desassociar aplicativos
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Distribuir eventos
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://msdn.microsoft.com/library/azure/dd179353.aspx).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-tables"></a>Armazenamento do Azure (tabelas)

### <a name="features"></a>Recursos

- Melhor para conjuntos de dados semi-estruturados
    
- Geralmente custo menor do que o SQL tradicional
    
- Muito rápido se consultando para chave, lento se consultando o valor
    
- Amplamente dimensionável; qualquer quantidade de tabelas até os limites da conta de armazenamento
    
- Acessível através da API REST, o protocolo oData limitado, .NET
    
- Os valores devem ser serializados
    
### <a name="common-uses"></a>Usos comuns

- Dados de usuário para aplicativos web
    
- Catálogos de endereços
    
- Informações do dispositivo
    
### <a name="key-storage-scenarios"></a>Cenários de armazenamento de chave

- Gerenciar dados
    
### <a name="resources"></a>Recursos

Para obter informações adicionais, clique [aqui](https://msdn.microsoft.com/library/azure/dd179463.aspx).
  
Para obter informações de custo, clique [aqui](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="microsoft-azure-storage-recommendations"></a>Recomendações de armazenamento do Microsoft Azure

Ao projetar sua solução de armazenamento personalizada com o armazenamento do Windows Azure, lembre-se do seguinte:
  
- Aproveite as várias contas de armazenamento maior escalabilidade, para maior tamanho (> 100 TB) ou para taxa de transferência mais (> 5.000 operações por segundo).
    
- Projete a capacidade para adicionar contas de armazenamento adicional, como uma alteração de configuração, e não como uma alteração de código.
    
- Selecione cuidadosamente o particionamento de funções para o armazenamento de tabela habilitar a escala desejada em termos de desempenho de inserção e de consulta.
    
- Escolha nomes de coluna curta para propriedades de tabela como os metadados (nomes de propriedade) são armazenados em banda (os nomes de coluna também é levada em contagem o tamanho máximo de linha de 1 MB).
    
- Quando possível, operações em armazenamento em lotes.
    
- Cache agressivamente informações do banco de dados de configuração em um cache distribuído.
    
- Se o desempenho de aplicativos ou confiabilidade depender tendo um determinado segmento de dados disponíveis no cache, seu aplicativo deve recusar solicitações de entrada até que o cache tenha sido previamente definido.
    
- Particione os dados em um verticalmente (pela tabela) ou horizontalmente (tabela de segmento entre vários fragmentos) para distribuir a carga em vários bancos de dados.
    
## <a name="see-also"></a>Veja também

[Armazenamento do Microsoft Cloud para arquitetos corporativos](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Roteiro do Enterprise Cloud da Microsoft: recursos para responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



