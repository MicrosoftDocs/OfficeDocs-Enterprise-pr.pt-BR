---
title: A Contoso precisa e da infraestrutura de TI
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "Resumo: Compreenda a estrutura básica da Contoso local como seus negócios precisa podem ser atendidos por ofertas de nuvem da Microsoft e a infraestrutura de TI."
ms.openlocfilehash: 98ead7ffa3164c3cd57ec50def836b690881ba63
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="contosos-it-infrastructure-and-needs"></a>A Contoso precisa e da infraestrutura de TI

 **Resumo:** Compreenda a estrutura básica da Contoso local como seus negócios precisa podem ser atendidos por ofertas de nuvem da Microsoft e a infraestrutura de TI.
  
A Contoso está em processo de transição de um local, a infraestrutura de TI centralizado para um outro inclusive de nuvem que incorpora as cargas de trabalho de produtividade pessoal baseado em nuvem, aplicativos e cenários híbridos.
  
## <a name="contosos-existing-it-infrastructure"></a>Infraestrutura de TI da Contoso

A Contoso usa principalmente centralizado infraestrutura de TI, com centros de dados de aplicativo na sede Paris local.
  
**Figura 1: Infra-estrutura de TI da Contoso**

![Infraestrutura de TI da Contoso](images/Contoso_Poster/Existing_IT.png)
  
A Figura 1 mostra um escritório matriz com a Internet, DMZ e centros de dados de aplicativo.
  
Em DMZ da Contoso, fornecem os diferentes conjuntos de servidores:
  
- Acesso remoto para o proxy de intranet e web Contoso para trabalhadores na sede Paris.
    
- Hospedagem para o site público Contoso, do qual os clientes podem solicitar produtos, partes ou fontes.
    
- Hospedando o parceiro Contoso extranet para colaboração e comunicação parceiros.
    
## <a name="contosos-business-needs"></a>Necessidades de negócios da Contoso

Aqui estão as necessidades de negócios da Contoso em ordem de prioridade:
  
1. Cumprir os requisitos normativos regionais
    
    Para evitar multas e manter boas relações com governos locais, a Contoso deve assegurar a conformidade com normas de armazenamento e a criptografia de dados.
    
2. Melhorar o gerenciamento de fornecedores e parceiros
    
    O parceiro extranet é a duração e caras de manter. A Contoso deseja substituí-la por uma solução baseada na nuvem que usa autenticação federada.
    
3. Melhorar a produtividade da força de trabalho móvel, gerenciamento de dispositivo e acesso
    
    Força de trabalho somente mobile da Contoso está expandindo e necessidades de gerenciamento de dispositivos para garantir acesso mais eficiente aos recursos e a proteção à propriedade intelectual.
    
4. Reduzir a infra-estrutura de acesso remoto
    
    Movendo recursos comumente acessados pelos funcionários remotos para a nuvem, Contoso economizarão, reduzindo os custos de manutenção e suporte para sua solução de acesso remoto.
    
5. Dimensionar para baixo de centros de dados no local
    
    Os datacenters Contoso contêm centenas de servidores, alguns dos quais estão executando funções herdadas ou de arquivamento que distraem a equipe de TI de manutenção de cargas de trabalho de valor comercial alto.
    
6. Recursos de computação e armazenamento de dimensione para processamento de final de trimestre
    
    Fim do trimestre contabilidade financeira e processamento, juntamente com o gerenciamento do inventário de projeção requer curto prazo aumenta em servidores e armazenamento.
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a>Mapeamento de negócios da Contoso precisa ofertas de nuvem da Microsoft

Com base em uma análise das ofertas de nuvem da Microsoft, a Contoso do departamento de TI determinou que o mapeamento a seguir:
  
|**Software como serviço (SaaS)**|**Plataforma como um serviço (PaaS Azure)**|**Infraestrutura como um serviço (Azure IaaS)**|
|:-----|:-----|:-----|
|**Office 365:** Aplicativos de produtividade de pessoal e de grupo principal na nuvem. <br/> Necessidades de negócios: 1 3 5  <br/> |Hospedar vendas e suporte a documentos e sistemas de informação usando aplicativos baseados em nuvem.  <br/> Necessidade comercial: 3  <br/> |Mova os sistemas de arquivamento e herdados para servidores baseados em nuvem.  <br/> Necessidade comercial: 5  <br/> |
|**Dynamics 365:** Use o gerenciamento de fornecedores e clientes baseados em nuvem. Remova o parceiro extranet no DMZ.<br/> Necessidade comercial: 2  <br/> |Aplicativos móveis são baseadas em nuvem, em vez de Paris com base no datacenter.  <br/> Necessidades de negócios: 3 de 4  <br/> |Migre dados fora do local de centros de dados e aplicativos pouco usado.  <br/> Necessidade comercial: 5  <br/> |
|**Intune/EMS:** Gerencie dispositivos com Android e iOS. <br/> Necessidade comercial: 3  <br/> ||Adicione servidores temporários e armazenamento para necessidades de processamento de final de trimestre.  <br/> Necessidade comercial: 6  <br/> |
   
## <a name="see-also"></a>See Also

[Contoso em nuvem da Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)


