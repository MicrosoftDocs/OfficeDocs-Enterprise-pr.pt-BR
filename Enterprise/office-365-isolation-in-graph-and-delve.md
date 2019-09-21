---
title: Isolamento de locatário do Office 365 no Office Graph e no Delve
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Resumo: uma explicação do isolamento de locatário no Office Graph e no Delve.'
ms.openlocfilehash: b974f8dfc86ba7d00bf434fef32718ad485aa55b
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067144"
---
# <a name="tenant-isolation-in-the-office-graph-and-delve"></a>Isolamento de locatário no Office Graph e Delve

## <a name="tenant-isolation-in-the-office-graph"></a>Isolamento de locatário no Office Graph
A atividade de modelos do [Office Graph](https://dev.office.com/officegraph) nos serviços do Office 365, incluindo Exchange Online, SharePoint Online, Yammer, Skype for Business, Azure Active Directory e mais e em serviços externos, como outros serviços da Microsoft ou serviços de terceiros. Os componentes do Office Graph são usados em todo o Office 365. O Office Graph representa uma coleção de conteúdo e atividade e as relações entre elas que ocorrem em todo o pacote do Office. Ele usa técnicas de aprendizado de máquina sofisticadas para conectar pessoas ao conteúdo relevante, conversas e pessoas em torno delas. Por exemplo, o índice de locatário no SharePoint Online tem um índice do Office Graph que é usado para atender consultas de Delve, o mecanismo de processamento de análise no SharePoint Online é usado para armazenar sinais e calcular insights e o Exchange Online calcula cada usuário cache de destinatários como entrada na análise de locatários.

O Office Graph contém informações sobre objetos corporativos, como pessoas e documentos, bem como os relacionamentos e interações entre esses objetos. Os relacionamentos e interações são representados como *bordas*. O Office Graph é segmentado por locatário, de forma que as bordas só podem existir entre *nós* na mesma locação. Um *nó* é uma entidade com um URI (Uniform Resource Identifier), tipo de nó, lista de controle de acesso e um conjunto de facetas contendo *metadados* e bordas. Cada nó tem metadados e bordas associados, organizados em *facetas* como no modelo de conhecimento comum. Os *metadados* são denominados Propriedades armazenadas em um nó que pode ser usado para pesquisa, filtragem ou análise no Office Graph. Uma *faceta* é uma coleção lógica de metadados e bordas em um nó. Cada faceta descreve um aspecto de um nó. 

O Office Graph não coloca todos os dados em um único repositório; em vez disso, ele armazena metadados e relações sobre dados que residem em outros locais. O Office Graph consiste em vários repositórios de dados e componentes de processamento:
- O repositório de gráficos do locatário fornece armazenamento em massa otimizado para análise eficiente.
- O cache de conteúdo ativo oferece acesso aleatório rápido ao nó ativo e às bordas para conduzir as experiências do usuário.
- O roteador de entrada notifica os componentes internos e externos das alterações no gráfico do locatário.

A análise em cada carga de trabalho deduz as ideias relevantes aos cálculos em todo o locatário e empurre-as para o gráfico do locatário. Os motivos da análise do locatário em todas as atividades de uma locação para produzir informações sobre padrões de comportamento. Por exemplo, o Exchange Online calcula o cache do destinatário para cada usuário com a análise que tem um motivo eficiente sobre a caixa de correio de cada usuário. Essas análises por usuário produzem um conjunto de *bordas RecipientCache* em cada pessoa, que por sua vez é enviado para o gráfico do locatário. Isso mantém o máximo de processamento de análise o mais próximo possível dos dados de origem.

## <a name="tenant-isolation-in-delve"></a>Isolamento de locatário no Delve
Como mencionado anteriormente, o Office Graph fornece experiências que ajudam as pessoas a descobrir e colaborar em atividades atuais em sua empresa e fornece uma plataforma centrada em entidade para análise do motivo de conteúdo e atividade em cargas de trabalho e Além do Office 365. O Delve é a primeira experiência do Office Graph.
O Delve é uma experiência da Web do Office 365 que superfícies o conteúdo do Office 365 e do Yammer Enterprise para o Office 365 Users via o Office Graph. A experiência da Web exibe dados como diferentes placas, cada uma com um determinado tópico, como a *tendência de me mostrar* ou *modificado por mim*. Cada placa consiste em vários cartões de documento que exibem o texto de resumo e uma imagem do documento. O cartão permite que os usuários façam coisas como abrir o documento ou uma página do Yammer para o documento. Há uma página para cada pessoa em um locatário do Office 365 que exibe os documentos mais relevantes para esta pessoa e ícones que podem invocar o Exchange Online ou o Skype for Business para interagir com essa pessoa. Como o Delve é baseado na API do Office Graph, ele é limitado pelo isolamento baseado em locatário dessa API.