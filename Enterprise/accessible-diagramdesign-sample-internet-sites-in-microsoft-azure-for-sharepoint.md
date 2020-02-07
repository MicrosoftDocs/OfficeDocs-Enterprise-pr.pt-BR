---
title: Diagrama acessível-exemplo de design de sites da Internet no Microsoft Azure para SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
f1.keywords:
- NOCSH
description: 'Este artigo é uma versão de texto acessível do diagrama chamado amostra de design: sites da Internet no Microsoft Azure para SharePoint 2013.'
ms.openlocfilehash: b3669304fee6b7a89bc5d1bde96c39c496122d48
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843792"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="14285-103">Diagrama acessível-exemplo de design: sites da Internet no Microsoft Azure para SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="14285-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="14285-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama chamado amostra de design: sites da Internet no Microsoft Azure para SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="14285-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="14285-105">Use este exemplo de design como ponto de partida para um site voltado para a Internet no Azure usando o SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="14285-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="14285-106">Este cartaz mostra um exemplo de como criar os seguintes aspectos do SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="14285-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="14285-107">Usuários</span><span class="sxs-lookup"><span data-stu-id="14285-107">Users</span></span>
    
- <span data-ttu-id="14285-108">Zonas e autenticação</span><span class="sxs-lookup"><span data-stu-id="14285-108">Zones and authentication</span></span>
    
- <span data-ttu-id="14285-109">Farm de servidores</span><span class="sxs-lookup"><span data-stu-id="14285-109">Server farm</span></span>
    
- <span data-ttu-id="14285-110">Site de administração</span><span class="sxs-lookup"><span data-stu-id="14285-110">Administration site</span></span>
    
- <span data-ttu-id="14285-111">Serviços</span><span class="sxs-lookup"><span data-stu-id="14285-111">Services</span></span>
    
- <span data-ttu-id="14285-112">Pools de aplicativos e aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="14285-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="14285-113">Conjuntos de sites</span><span class="sxs-lookup"><span data-stu-id="14285-113">Site collections</span></span>
    
- <span data-ttu-id="14285-114">Sites</span><span class="sxs-lookup"><span data-stu-id="14285-114">Sites</span></span>
    
- <span data-ttu-id="14285-115">Bancos de dados de conteúdo</span><span class="sxs-lookup"><span data-stu-id="14285-115">Content databases</span></span>
    
- <span data-ttu-id="14285-116">Zonas e URLs</span><span class="sxs-lookup"><span data-stu-id="14285-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="14285-117">Usuários, zonas e autenticação</span><span class="sxs-lookup"><span data-stu-id="14285-117">Users, zones and authentication</span></span>

<span data-ttu-id="14285-118">Há quatro tipos de contas de usuário nesse design.</span><span class="sxs-lookup"><span data-stu-id="14285-118">There are four types of user accounts in this design.</span></span> <span data-ttu-id="14285-119">Cada tipo de conta é associada a um site para acesso e com uma zona que usa um tipo específico de autenticação.</span><span class="sxs-lookup"><span data-stu-id="14285-119">Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="14285-120">Clientes anônimos — clientes anônimos têm acesso por meio de https://www.contoso.comum site como o.</span><span class="sxs-lookup"><span data-stu-id="14285-120">Anonymous customers — Anonymous customers have access through a site such as https://www.contoso.com.</span></span> <span data-ttu-id="14285-121">A zona que eles usam é a "zona de Internet/anônima", que usa a autenticação anônima.</span><span class="sxs-lookup"><span data-stu-id="14285-121">The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="14285-122">Clientes autenticados – clientes autenticados têm acesso por meio de um site https://secure.contoso.comcomo o.</span><span class="sxs-lookup"><span data-stu-id="14285-122">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com.</span></span> <span data-ttu-id="14285-123">A zona que usa é "extranet Zone/SAML", que usa o Azure Active Directory com a autenticação SAML.</span><span class="sxs-lookup"><span data-stu-id="14285-123">The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="14285-124">Autores e desenvolvedores de sites — autores e desenvolvedores de sites têm acesso por meio https://authoring.contoso.com:8000 de https://www.contoso.com:8000sites como ou.</span><span class="sxs-lookup"><span data-stu-id="14285-124">Site authors and developers — Site authors and developers have access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="14285-125">A zona que usa é "padrão de zona/Windows integrado", que usa os serviços de domínio do Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="14285-125">The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="14285-126">Conta de rastreamento de pesquisa — a conta de rastreamento de pesquisa tem acesso https://authoring.contoso.com:8000 por https://www.contoso.com:8000meio de sites como ou.</span><span class="sxs-lookup"><span data-stu-id="14285-126">Search Crawl Account — The search crawl account has access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000.</span></span> <span data-ttu-id="14285-127">A zona que ela usa é "padrão de zona/Windows integrado", que usa o AD DS com a autenticação NTLM do Windows.</span><span class="sxs-lookup"><span data-stu-id="14285-127">The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="14285-128">Farm de servidores</span><span class="sxs-lookup"><span data-stu-id="14285-128">Server farm</span></span>

<span data-ttu-id="14285-129">Os usuários acessam o farm de servidores por meio do Azure.</span><span class="sxs-lookup"><span data-stu-id="14285-129">The users access the server farm through Azure.</span></span> <span data-ttu-id="14285-130">O farm de servidores contém um ou mais servidores Web.</span><span class="sxs-lookup"><span data-stu-id="14285-130">The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="14285-131">Site de administração</span><span class="sxs-lookup"><span data-stu-id="14285-131">Administration site</span></span>

<span data-ttu-id="14285-132">O site de administração contém vários servidores de aplicativos, que se comunicam com um pool de aplicativos (pool de aplicativos 1 no exemplo) que usa o site da administração central do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="14285-132">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site.</span></span> <span data-ttu-id="14285-133">O site da administração central fornece acesso a conjuntos de sites dentro da organização.</span><span class="sxs-lookup"><span data-stu-id="14285-133">The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="14285-134">O site de administração também contém servidores de banco de dados SQL, que são servidores de banco de dados com o SQL Server instalado e configurado para dar suporte a clustering SQL, espelhamento ou AlwaysOn (AlwaysOn aplica-se somente ao SQL Server 2012).</span><span class="sxs-lookup"><span data-stu-id="14285-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="14285-135">Serviços</span><span class="sxs-lookup"><span data-stu-id="14285-135">Services</span></span>

<span data-ttu-id="14285-136">O exemplo de design mostra um site dos serviços de informações da Internet (IIS), serviços Web do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="14285-136">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services.</span></span> <span data-ttu-id="14285-137">Os serviços Web do SharePoint contêm um pool de aplicativos (pool de aplicativos 2) com três serviços, perfil de usuário, pesquisa e metadados gerenciados.</span><span class="sxs-lookup"><span data-stu-id="14285-137">SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="14285-138">Observações sobre serviços para sites da Internet:</span><span class="sxs-lookup"><span data-stu-id="14285-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="14285-139">Metadados gerenciados — certifique-se de selecionar **este aplicativo de serviço é o local de armazenamento padrão para conjuntos de termos específicos de coluna**.</span><span class="sxs-lookup"><span data-stu-id="14285-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="14285-140">Gerenciamento de aplicativos — não recomendamos o uso de aplicativos em um site de Internet público no Azure.</span><span class="sxs-lookup"><span data-stu-id="14285-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="14285-141">Pools de aplicativos e aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="14285-141">Application pools and web applications</span></span>

<span data-ttu-id="14285-142">O grupo padrão no Azure mostra o pool de aplicativos 3, que contém um aplicativo Web chamado contoso sites.</span><span class="sxs-lookup"><span data-stu-id="14285-142">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites.</span></span> <span data-ttu-id="14285-143">Este conjunto de sites baseado em caminho está localizado https://internal:8000em.</span><span class="sxs-lookup"><span data-stu-id="14285-143">This path-based site collection is located at https://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="14285-144">Conjuntos de sites e sites</span><span class="sxs-lookup"><span data-stu-id="14285-144">Site collections and sites</span></span>

<span data-ttu-id="14285-145">Os conjuntos de sites contidos no pool de aplicativos incluem:</span><span class="sxs-lookup"><span data-stu-id="14285-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="14285-146">Conjunto de sites com nome de host 1 para rastreamento (exemplo de localhttps://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="14285-146">Host-named site collection 1 for crawling (example location https://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="14285-147">Conjunto de sites nomeados por host 2 para consultas ( https://www.contoso.comlocais https://secure.contoso.comde exemplo,https://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="14285-147">Host-named site collection 2 for queries (sample locations https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="14285-148">Conjunto de sites nomeado por host 3 para consultas (locais https://assets.contoso.comde https://secureassets.contoso.comexemplo,https://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="14285-148">Host-named site collection 3 for queries (sample locations https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="14285-149">Bancos de dados de conteúdo</span><span class="sxs-lookup"><span data-stu-id="14285-149">Content databases</span></span>

<span data-ttu-id="14285-150">O exemplo mostra dois bancos de dados de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="14285-150">The example shows two content databases.</span></span> <span data-ttu-id="14285-151">Um é para o conjunto de sites 1 usado para rastreamento (https://authoring.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="14285-151">One is for the site collection 1 used for crawling (https://authoring.contoso.com:8000).</span></span> <span data-ttu-id="14285-152">O outro é para os dois conjuntos de sites 2 e 3 usados para consultashttps://www.contoso.com( https://secure.contoso.com, https://www.contoso.com:8000,, https://assets.contoso.comou https://secureassets.contoso.com, https://assets.contoso.com:8000),.</span><span class="sxs-lookup"><span data-stu-id="14285-152">The other is for the two site collections 2 and 3 used for queries (https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000, or https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="14285-153">Zonas e URLs</span><span class="sxs-lookup"><span data-stu-id="14285-153">Zones and URLs</span></span>

<span data-ttu-id="14285-154">O exemplo mostra três zonas com as URLs de carga balanceada associadas usadas por diferentes contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="14285-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="14285-155">A primeira lista de zonas e URLs está relacionada ao conjunto de sites 1 e contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="14285-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="14285-156">Usuários-autores de site</span><span class="sxs-lookup"><span data-stu-id="14285-156">Users - Site authors</span></span>
    
- <span data-ttu-id="14285-157">Zona-padrão</span><span class="sxs-lookup"><span data-stu-id="14285-157">Zone - Default</span></span>
    
- <span data-ttu-id="14285-158">URL com balanceamento de carga-https://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="14285-158">Load-balanced URL - https://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="14285-159">A segunda lista de zonas e URLs tem três tipos diferentes de usuários em três zonas diferentes.</span><span class="sxs-lookup"><span data-stu-id="14285-159">The second list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="14285-160">Ele está relacionado ao conjunto de sites 2 e contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="14285-160">It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="14285-161">Primeira zona:</span><span class="sxs-lookup"><span data-stu-id="14285-161">First zone:</span></span>
  
- <span data-ttu-id="14285-162">Usuários-autores de site</span><span class="sxs-lookup"><span data-stu-id="14285-162">Users - Site authors</span></span>
    
- <span data-ttu-id="14285-163">Zona-padrão</span><span class="sxs-lookup"><span data-stu-id="14285-163">Zone - Default</span></span>
    
- <span data-ttu-id="14285-164">URL com balanceamento de carga-https://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="14285-164">Load-balanced URL - https://www.contoso.com:8000</span></span>
    
<span data-ttu-id="14285-165">Segunda zona:</span><span class="sxs-lookup"><span data-stu-id="14285-165">Second zone:</span></span>
  
- <span data-ttu-id="14285-166">Usuários-clientes anônimos</span><span class="sxs-lookup"><span data-stu-id="14285-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="14285-167">Zona-Internet</span><span class="sxs-lookup"><span data-stu-id="14285-167">Zone - Internet</span></span>
    
- <span data-ttu-id="14285-168">URL com balanceamento de carga-https://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="14285-168">Load-balanced URL - https://www.contoso.com</span></span>
    
<span data-ttu-id="14285-169">Terceira zona:</span><span class="sxs-lookup"><span data-stu-id="14285-169">Third zone:</span></span>
  
- <span data-ttu-id="14285-170">Clientes autenticados por usuários</span><span class="sxs-lookup"><span data-stu-id="14285-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="14285-171">Zona-Extranet</span><span class="sxs-lookup"><span data-stu-id="14285-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="14285-172">URL com balanceamento de carga-https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="14285-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="14285-173">A terceira lista de zonas e URLs tem três tipos diferentes de usuários em três zonas diferentes.</span><span class="sxs-lookup"><span data-stu-id="14285-173">The third list of zones and URLs has three different types of users in three different zones.</span></span> <span data-ttu-id="14285-174">Ele está relacionado ao conjunto de sites 3 e contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="14285-174">It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="14285-175">Primeira zona:</span><span class="sxs-lookup"><span data-stu-id="14285-175">First zone:</span></span>
  
- <span data-ttu-id="14285-176">Usuários-autores de site</span><span class="sxs-lookup"><span data-stu-id="14285-176">Users - Site authors</span></span>
    
- <span data-ttu-id="14285-177">Zona-Internet</span><span class="sxs-lookup"><span data-stu-id="14285-177">Zone - Internet</span></span>
    
- <span data-ttu-id="14285-178">URL com balanceamento de carga-https://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="14285-178">Load-balanced URL - https://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="14285-179">Segunda zona:</span><span class="sxs-lookup"><span data-stu-id="14285-179">Second zone:</span></span>
  
- <span data-ttu-id="14285-180">Usuários-clientes anônimos</span><span class="sxs-lookup"><span data-stu-id="14285-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="14285-181">Zona-Internet</span><span class="sxs-lookup"><span data-stu-id="14285-181">Zone - Internet</span></span>
    
- <span data-ttu-id="14285-182">URL com balanceamento de carga-https://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="14285-182">Load-balanced URL - https://assets.contoso.com</span></span>
    
<span data-ttu-id="14285-183">Terceira zona:</span><span class="sxs-lookup"><span data-stu-id="14285-183">Third zone:</span></span>
  
- <span data-ttu-id="14285-184">Clientes autenticados por usuários</span><span class="sxs-lookup"><span data-stu-id="14285-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="14285-185">Zona-Extranet</span><span class="sxs-lookup"><span data-stu-id="14285-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="14285-186">URL com balanceamento de carga-https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="14285-186">Load-balanced URL - https://secureassets.contoso.com</span></span>
    

