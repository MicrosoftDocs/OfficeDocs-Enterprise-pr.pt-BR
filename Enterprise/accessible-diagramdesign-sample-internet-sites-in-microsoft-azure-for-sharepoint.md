---
title: Diagrama acessível-exemplo de design de sites da Internet no Microsoft Azure para SharePoint 2013
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
description: 'Este artigo é uma versão de texto acessível do diagrama chamado amostra de design: sites da Internet no Microsoft Azure para SharePoint 2013.'
ms.openlocfilehash: 0d42a96f80d47b360084557fea47c4155d106d30
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487827"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagrama acessível-exemplo de design: sites da Internet no Microsoft Azure para SharePoint 2013

**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado amostra de design: sites da Internet no Microsoft Azure para SharePoint 2013.
  
Use este exemplo de design como ponto de partida para um site voltado para a Internet no Azure usando o SharePoint 2013.
  
Este cartaz mostra um exemplo de como criar os seguintes aspectos do SharePoint 2013:
  
- Usuários
    
- Zonas e autenticação
    
- Farm de servidores
    
- Site de administração
    
- Serviços
    
- Pools de aplicativos e aplicativos Web
    
- Conjuntos de sites
    
- Sites
    
- Bancos de dados de conteúdo
    
- Zonas e URLs
    
## <a name="users-zones-and-authentication"></a>Usuários, zonas e autenticação

Há quatro tipos de contas de usuário nesse design. Cada tipo de conta é associada a um site para acesso e com uma zona que usa um tipo específico de autenticação. 
  
- Clientes anônimos — clientes anônimos têm acesso por meio de http://www.contoso.comum site como o. A zona que eles usam é a "zona de Internet/anônima", que usa a autenticação anônima.
    
- Clientes autenticados – clientes autenticados têm acesso por meio de um site https://secure.contoso.comcomo o. A zona que usa é "extranet Zone/SAML", que usa o Azure Active Directory com a autenticação SAML.
    
- Autores e desenvolvedores de sites — autores e desenvolvedores de sites têm acesso por meio http://authoring.contoso.com:8000 de http://www.contoso.com:8000sites como ou. A zona que usa é "padrão de zona/Windows integrado", que usa os serviços de domínio do Active Directory (AD DS).
    
- Conta de rastreamento de pesquisa — a conta de rastreamento de pesquisa tem acesso http://authoring.contoso.com:8000 por http://www.contoso.com:8000meio de sites como ou. A zona que ela usa é "padrão de zona/Windows integrado", que usa o AD DS com a autenticação NTLM do Windows.
    
## <a name="server-farm"></a>Farm de servidores

Os usuários acessam o farm de servidores por meio do Azure. O farm de servidores contém um ou mais servidores Web.
  
## <a name="administration-site"></a>Site de administração

O site de administração contém vários servidores de aplicativos, que se comunicam com um pool de aplicativos (pool de aplicativos 1 no exemplo) que usa o site da administração central do aplicativo Web. O site da administração central fornece acesso a conjuntos de sites dentro da organização.
  
O site de administração também contém servidores de banco de dados SQL, que são servidores de banco de dados com o SQL Server instalado e configurado para dar suporte a clustering SQL, espelhamento ou AlwaysOn (AlwaysOn aplica-se somente ao SQL Server 2012).
  
## <a name="services"></a>Serviços

O exemplo de design mostra um site dos serviços de informações da Internet (IIS), serviços Web do SharePoint. Os serviços Web do SharePoint contêm um pool de aplicativos (pool de aplicativos 2) com três serviços, perfil de usuário, pesquisa e metadados gerenciados.
  
Observações sobre serviços para sites da Internet:
  
> Metadados gerenciados — certifique-se de selecionar **este aplicativo de serviço é o local de armazenamento padrão para conjuntos de termos específicos de coluna**.
    
> Gerenciamento de aplicativos — não recomendamos o uso de aplicativos em um site de Internet público no Azure.
    
## <a name="application-pools-and-web-applications"></a>Pools de aplicativos e aplicativos Web

O grupo padrão no Azure mostra o pool de aplicativos 3, que contém um aplicativo Web chamado contoso sites. Este conjunto de sites baseado em caminho está localizado http://internal:8000em.
  
## <a name="site-collections-and-sites"></a>Conjuntos de sites e sites

Os conjuntos de sites contidos no pool de aplicativos incluem:
  
- Conjunto de sites com nome de host 1 para rastreamento (exemplo de localhttp://authoring.contoso.com:8000)
    
- Conjunto de sites nomeados por host 2 para consultas ( http://www.contoso.comlocais https://secure.contoso.comde exemplo,http://www.contoso.com:8000)
    
- Conjunto de sites nomeado por host 3 para consultas (locais http://assets.contoso.comde https://secureassets.contoso.comexemplo,http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Bancos de dados de conteúdo

O exemplo mostra dois bancos de dados de conteúdo. Um é para o conjunto de sites 1 usado para rastreamento (http://authoring.contoso.com:8000). O outro é para os dois conjuntos de sites 2 e 3 usados para consultashttp://www.contoso.com( https://secure.contoso.com, http://www.contoso.com:8000,, http://assets.contoso.comou https://secureassets.contoso.com, http://assets.contoso.com:8000),.
  
## <a name="zones-and-urls"></a>Zonas e URLs

O exemplo mostra três zonas com as URLs de carga balanceada associadas usadas por diferentes contas de usuário. 
  
A primeira lista de zonas e URLs está relacionada ao conjunto de sites 1 e contém as seguintes informações:
  
- Usuários-autores de site
    
- Zona-padrão
    
- URL com balanceamento de carga-http://authoring.contoso.com:8000
    
A segunda lista de zonas e URLs tem três tipos diferentes de usuários em três zonas diferentes. Ele está relacionado ao conjunto de sites 2 e contém as seguintes informações:
  
Primeira zona:
  
- Usuários-autores de site
    
- Zona-padrão
    
- URL com balanceamento de carga-http://www.contoso.com:8000
    
Segunda zona:
  
- Usuários-clientes anônimos
    
- Zona-Internet
    
- URL com balanceamento de carga-http://www.contoso.com
    
Terceira zona:
  
- Clientes autenticados por usuários
    
- Zona-Extranet
    
- URL com balanceamento de carga-https://secure.contoso.com
    
A terceira lista de zonas e URLs tem três tipos diferentes de usuários em três zonas diferentes. Ele está relacionado ao conjunto de sites 3 e contém as seguintes informações:
  
Primeira zona:
  
- Usuários-autores de site
    
- Zona-Internet
    
- URL com balanceamento de carga-http://assets.contoso.com:8000
    
Segunda zona:
  
- Usuários-clientes anônimos
    
- Zona-Internet
    
- URL com balanceamento de carga-http://assets.contoso.com
    
Terceira zona:
  
- Clientes autenticados por usuários
    
- Zona-Extranet
    
- URL com balanceamento de carga-http://secureassets.contoso.com
    

