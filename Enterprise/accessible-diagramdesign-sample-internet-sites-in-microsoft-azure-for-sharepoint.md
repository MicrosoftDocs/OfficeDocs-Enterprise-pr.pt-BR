---
title: Amostra de Design de diagrama acessível - sites da Internet no Microsoft Azure para o SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'Este artigo é uma versão de texto acessível do diagrama denominado amostra de Design: sites da Internet no Microsoft Azure para o SharePoint 2013.'
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
ms.locfileid: "17502754"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagrama acessível - exemplo de Design: sites da Internet no Microsoft Azure para o SharePoint 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama denominado amostra de Design: sites da Internet no Microsoft Azure para o SharePoint 2013.
  
Use este exemplo de design como ponto de partida para um site da Internet no Windows Azure usando o SharePoint 2013.
  
Este cartaz mostra um exemplo de como criar os seguintes aspectos do SharePoint 2013:
  
- Usuários
    
- Zonas e autenticação
    
- Farm de servidores
    
- Site de administração
    
- Serviços
    
- Pools de aplicativos e aplicativos da web
    
- Conjuntos de sites
    
- Sites
    
- Bancos de dados de conteúdo
    
- Zonas e URLs
    
## <a name="users-zones-and-authentication"></a>Usuários, zonas e autenticação

Há quatro tipos de contas de usuário neste design. Cada tipo de conta é associado com um site para o acesso e uma zona que usa um tipo específico de autenticação. 
  
- Clientes anônimos — clientes anônimos têm acesso através de um site como http://www.contoso.com. É a zona que utilizarem o "zona da Internet / anônimo", que usa a autenticação anônima.
    
- Autenticado clientes — autenticado clientes têm acesso através de um site, como https://secure.contoso.com. É a zona que utilizarem o "zona Extranet / SAML", que usa o Azure Active Directory com autenticação SAML.
    
- Os autores e desenvolvedores de sites — autores de Site e desenvolvedores têm acesso por meio de sites como http://authoring.contoso.com:8000 ou http://www.contoso.com:8000. É a zona que utilizarem o "zona padrão / integrada do Windows", que usa os serviços de domínio Active Directory (AD DS).
    
- Conta de rastreamento de pesquisa — A conta de rastreamento de pesquisa possui acesso por meio de sites como http://authoring.contoso.com:8000 ou http://www.contoso.com:8000. É a zona que ele usa o "zona padrão / integrada do Windows", que usa o AD DS com autenticação Windows NTLM.
    
## <a name="server-farm"></a>Farm de servidores

Os usuários acessam o farm de servidores por meio do Windows Azure. O farm de servidores contém um ou mais servidores Web.
  
## <a name="administration-site"></a>Site de administração

O site de administração contém vários servidores de aplicativos, que se comunicam com um Pool de aplicativos (1 de Pool de aplicativos no exemplo) que usa o Site da Administração Central do aplicativo web. O Site da Administração Central fornece acesso aos conjuntos de sites dentro da organização.
  
O site da administração também contém os servidores de banco de dados do SQL, que são os servidores de banco de dados com o SQL Server instalado e configurado para dar suporte a SQL clustering, espelhamento ou AlwaysOn (AlwaysOn é aplicado ao SQL Server 2012 apenas).
  
## <a name="services"></a>Serviços

O exemplo de design mostra um site de serviços de informações da Internet (IIS), serviços Web do SharePoint. Serviços Web do SharePoint contém um pool de aplicativos (2 de Pool de aplicativo) com três serviços, perfil de usuário, pesquisa e metadados gerenciados.
  
Observações sobre serviços para sites da Internet:
  
> Metadados gerenciados — Certifique-se de selecionar **Este aplicativo de serviço é o local de armazenamento padrão para conjuntos de termos específicos de coluna**.
    
> Gerenciamento de aplicativos — Não recomendamos usar aplicativos em um site de Internet público no Windows Azure.
    
## <a name="application-pools-and-web-applications"></a>Pools de aplicativos e aplicativos da web

O grupo padrão no Windows Azure mostra 3 de Pool de aplicativos, que contém um aplicativo web chamado Contoso Sites. Este conjunto de sites baseados em caminho está localizado em http://internal:8000.
  
## <a name="site-collections-and-sites"></a>Conjuntos de sites

Os conjuntos de sites contidos no pool de aplicativos incluem:
  
- Conjunto de sites nomeados por host 1 para rastreamento (exemplo local http://authoring.contoso.com:8000)
    
- Conjunto de sites nomeados por host 2 para consultas (amostra locais http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)
    
- Conjunto de sites nomeados por host 3 para consultas (amostra locais http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Bancos de dados de conteúdo

O exemplo mostra dois bancos de dados de conteúdo. Um é o conjunto de sites 1 usado para rastreamento (http://authoring.contoso.com:8000). O outro é para os conjuntos de dois sites 2 e 3 usadas para consultas (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 ou http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).
  
## <a name="zones-and-urls"></a>Zonas e URLs

O exemplo mostra três zonas com as URLs associadas com balanceamento de carga que são usadas por diferentes contas de usuário. 
  
Primeira lista das URLs e zonas está relacionada ao conjunto de sites 1 e contém as seguintes informações:
  
- Usuários - criadores de sites
    
- Zona - padrão
    
- URL com carga balanceada - http://authoring.contoso.com:8000
    
Segunda lista das URLs e zonas tem três tipos diferentes de usuários em três zonas diferentes. Ela está relacionada a conjunto de sites 2, e ele contém as seguintes informações:
  
Primeira zona:
  
- Usuários - criadores de sites
    
- Zona - padrão
    
- URL com carga balanceada - http://www.contoso.com:8000
    
Segunda zona:
  
- Usuários - clientes anônimos
    
- Zona - Internet
    
- Com balanceamento de carga URL - http://www.contoso.com
    
Terceira zona:
  
- Usuários - clientes autenticados
    
- Zona - Extranet
    
- Com balanceamento de carga URL - https://secure.contoso.com
    
A terceira lista das URLs e zonas tem três tipos diferentes de usuários em três zonas diferentes. Ela está relacionada a conjunto de sites 3 e ele contém as seguintes informações:
  
Primeira zona:
  
- Usuários - criadores de sites
    
- Zona - Internet
    
- URL com carga balanceada - http://assets.contoso.com:8000
    
Segunda zona:
  
- Usuários - clientes anônimos
    
- Zona - Internet
    
- Com balanceamento de carga URL - http://assets.contoso.com
    
Terceira zona:
  
- Usuários - clientes autenticados
    
- Zona - Extranet
    
- Com balanceamento de carga URL - http://secureassets.contoso.com
    

