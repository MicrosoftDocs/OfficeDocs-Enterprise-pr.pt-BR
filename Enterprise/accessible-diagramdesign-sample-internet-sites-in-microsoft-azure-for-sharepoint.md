---
title: "Amostra de Design de diagrama acessível - sites da Internet no Microsoft Azure para o SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "Este artigo é uma versão de texto acessível do diagrama denominado amostra de Design: sites da Internet no Microsoft Azure para o SharePoint 2013."
ms.openlocfilehash: 1d84900a931bf9a01cd2e757a5fc671455e076f5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="1808d-103">Diagrama acessível - exemplo de Design: sites da Internet no Microsoft Azure para o SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="1808d-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="1808d-104">**Resumo:** Este artigo é uma versão de texto acessível do diagrama denominado amostra de Design: sites da Internet no Microsoft Azure para o SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="1808d-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="1808d-105">Use este exemplo de design como ponto de partida para um site da Internet no Windows Azure usando o SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="1808d-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="1808d-106">Este cartaz mostra um exemplo de como criar os seguintes aspectos do SharePoint 2013:</span><span class="sxs-lookup"><span data-stu-id="1808d-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="1808d-107">Usuários</span><span class="sxs-lookup"><span data-stu-id="1808d-107">Users</span></span>
    
- <span data-ttu-id="1808d-108">Zonas e autenticação</span><span class="sxs-lookup"><span data-stu-id="1808d-108">Zones and authentication</span></span>
    
- <span data-ttu-id="1808d-109">Farm de servidores</span><span class="sxs-lookup"><span data-stu-id="1808d-109">Server farm</span></span>
    
- <span data-ttu-id="1808d-110">Site de administração</span><span class="sxs-lookup"><span data-stu-id="1808d-110">Administration site</span></span>
    
- <span data-ttu-id="1808d-111">Serviços</span><span class="sxs-lookup"><span data-stu-id="1808d-111">Services</span></span>
    
- <span data-ttu-id="1808d-112">Pools de aplicativos e aplicativos da web</span><span class="sxs-lookup"><span data-stu-id="1808d-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="1808d-113">Conjuntos de sites</span><span class="sxs-lookup"><span data-stu-id="1808d-113">Site collections</span></span>
    
- <span data-ttu-id="1808d-114">Sites</span><span class="sxs-lookup"><span data-stu-id="1808d-114">Sites</span></span>
    
- <span data-ttu-id="1808d-115">Bancos de dados de conteúdo</span><span class="sxs-lookup"><span data-stu-id="1808d-115">Content databases</span></span>
    
- <span data-ttu-id="1808d-116">Zonas e URLs</span><span class="sxs-lookup"><span data-stu-id="1808d-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="1808d-117">Usuários, zonas e autenticação</span><span class="sxs-lookup"><span data-stu-id="1808d-117">Users, zones and authentication</span></span>

<span data-ttu-id="1808d-p101">Há quatro tipos de contas de usuário neste design. Cada tipo de conta é associado com um site para o acesso e uma zona que usa um tipo específico de autenticação.</span><span class="sxs-lookup"><span data-stu-id="1808d-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="1808d-120">Clientes anônimos — clientes anônimos têm acesso através de um site como http://www.contoso.com. É a zona que utilizarem o "zona da Internet / anônimo", que usa a autenticação anônima.</span><span class="sxs-lookup"><span data-stu-id="1808d-120">Anonymous customers — Anonymous customers have access through a site such as http://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="1808d-121">Autenticado clientes — autenticado clientes têm acesso através de um site, como https://secure.contoso.com. É a zona que utilizarem o "zona Extranet / SAML", que usa o Azure Active Directory com autenticação SAML.</span><span class="sxs-lookup"><span data-stu-id="1808d-121">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="1808d-p102">Os autores e desenvolvedores de sites — autores de Site e desenvolvedores têm acesso por meio de sites como http://authoring.contoso.com:8000 ou http://www.contoso.com:8000. É a zona que utilizarem o "zona padrão / integrada do Windows", que usa os serviços de domínio Active Directory (AD DS).</span><span class="sxs-lookup"><span data-stu-id="1808d-p102">Site authors and developers — Site authors and developers have access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="1808d-p103">Conta de rastreamento de pesquisa — A conta de rastreamento de pesquisa possui acesso por meio de sites como http://authoring.contoso.com:8000 ou http://www.contoso.com:8000. É a zona que ele usa o "zona padrão / integrada do Windows", que usa o AD DS com autenticação Windows NTLM.</span><span class="sxs-lookup"><span data-stu-id="1808d-p103">Search Crawl Account — The search crawl account has access through sites such as http://authoring.contoso.com:8000 or http://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="1808d-126">Farm de servidores</span><span class="sxs-lookup"><span data-stu-id="1808d-126">Server farm</span></span>

<span data-ttu-id="1808d-p104">Os usuários acessam o farm de servidores por meio do Windows Azure. O farm de servidores contém um ou mais servidores Web.</span><span class="sxs-lookup"><span data-stu-id="1808d-p104">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="1808d-129">Site de administração</span><span class="sxs-lookup"><span data-stu-id="1808d-129">Administration site</span></span>

<span data-ttu-id="1808d-p105">O site de administração contém vários servidores de aplicativos, que se comunicam com um Pool de aplicativos (1 de Pool de aplicativos no exemplo) que usa o Site da Administração Central do aplicativo web. O Site da Administração Central fornece acesso aos conjuntos de sites dentro da organização.</span><span class="sxs-lookup"><span data-stu-id="1808d-p105">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="1808d-132">O site da administração também contém os servidores de banco de dados do SQL, que são os servidores de banco de dados com o SQL Server instalado e configurado para dar suporte a SQL clustering, espelhamento ou AlwaysOn (AlwaysOn é aplicado ao SQL Server 2012 apenas).</span><span class="sxs-lookup"><span data-stu-id="1808d-132">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="1808d-133">Serviços</span><span class="sxs-lookup"><span data-stu-id="1808d-133">Services</span></span>

<span data-ttu-id="1808d-p106">O exemplo de design mostra um site de serviços de informações da Internet (IIS), serviços Web do SharePoint. Serviços Web do SharePoint contém um pool de aplicativos (2 de Pool de aplicativo) com três serviços, perfil de usuário, pesquisa e metadados gerenciados.</span><span class="sxs-lookup"><span data-stu-id="1808d-p106">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="1808d-136">Observações sobre serviços para sites da Internet:</span><span class="sxs-lookup"><span data-stu-id="1808d-136">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="1808d-137">Metadados gerenciados — Certifique-se de selecionar **Este aplicativo de serviço é o local de armazenamento padrão para conjuntos de termos específicos de coluna**.</span><span class="sxs-lookup"><span data-stu-id="1808d-137">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="1808d-138">Gerenciamento de aplicativos — Não recomendamos usar aplicativos em um site de Internet público no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="1808d-138">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="1808d-139">Pools de aplicativos e aplicativos da web</span><span class="sxs-lookup"><span data-stu-id="1808d-139">Application pools and web applications</span></span>

<span data-ttu-id="1808d-p107">O grupo padrão no Windows Azure mostra 3 de Pool de aplicativos, que contém um aplicativo web chamado Contoso Sites. Este conjunto de sites baseados em caminho está localizado em http://internal:8000.</span><span class="sxs-lookup"><span data-stu-id="1808d-p107">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at http://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="1808d-142">Conjuntos de sites</span><span class="sxs-lookup"><span data-stu-id="1808d-142">Site collections and sites</span></span>

<span data-ttu-id="1808d-143">Os conjuntos de sites contidos no pool de aplicativos incluem:</span><span class="sxs-lookup"><span data-stu-id="1808d-143">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="1808d-144">Conjunto de sites nomeados por host 1 para rastreamento (exemplo local http://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="1808d-144">Host-named site collection 1 for crawling (example location http://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="1808d-145">Conjunto de sites nomeados por host 2 para consultas (amostra locais http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="1808d-145">Host-named site collection 2 for queries (sample locations http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="1808d-146">Conjunto de sites nomeados por host 3 para consultas (amostra locais http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="1808d-146">Host-named site collection 3 for queries (sample locations http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="1808d-147">Bancos de dados de conteúdo</span><span class="sxs-lookup"><span data-stu-id="1808d-147">Content databases</span></span>

<span data-ttu-id="1808d-p108">O exemplo mostra dois bancos de dados de conteúdo. Um é o conjunto de sites 1 usado para rastreamento (http://authoring.contoso.com:8000). O outro é para os conjuntos de dois sites 2 e 3 usadas para consultas (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 ou http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span><span class="sxs-lookup"><span data-stu-id="1808d-p108">The example shows two content databases. One is for the site collection 1 used for crawling (http://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000, or http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="1808d-151">Zonas e URLs</span><span class="sxs-lookup"><span data-stu-id="1808d-151">Zones and URLs</span></span>

<span data-ttu-id="1808d-152">O exemplo mostra três zonas com as URLs associadas com balanceamento de carga que são usadas por diferentes contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="1808d-152">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="1808d-153">Primeira lista das URLs e zonas está relacionada ao conjunto de sites 1 e contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="1808d-153">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="1808d-154">Usuários - criadores de sites</span><span class="sxs-lookup"><span data-stu-id="1808d-154">Users - Site authors</span></span>
    
- <span data-ttu-id="1808d-155">Zona - padrão</span><span class="sxs-lookup"><span data-stu-id="1808d-155">Zone - Default</span></span>
    
- <span data-ttu-id="1808d-156">URL com carga balanceada - http://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="1808d-156">Load-balanced URL - http://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="1808d-p109">Segunda lista das URLs e zonas tem três tipos diferentes de usuários em três zonas diferentes. Ela está relacionada a conjunto de sites 2, e ele contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="1808d-p109">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="1808d-159">Primeira zona:</span><span class="sxs-lookup"><span data-stu-id="1808d-159">First zone:</span></span>
  
- <span data-ttu-id="1808d-160">Usuários - criadores de sites</span><span class="sxs-lookup"><span data-stu-id="1808d-160">Users - Site authors</span></span>
    
- <span data-ttu-id="1808d-161">Zona - padrão</span><span class="sxs-lookup"><span data-stu-id="1808d-161">Zone - Default</span></span>
    
- <span data-ttu-id="1808d-162">URL com carga balanceada - http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="1808d-162">Load-balanced URL - http://www.contoso.com:8000</span></span>
    
<span data-ttu-id="1808d-163">Segunda zona:</span><span class="sxs-lookup"><span data-stu-id="1808d-163">Second zone:</span></span>
  
- <span data-ttu-id="1808d-164">Usuários - clientes anônimos</span><span class="sxs-lookup"><span data-stu-id="1808d-164">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="1808d-165">Zona - Internet</span><span class="sxs-lookup"><span data-stu-id="1808d-165">Zone - Internet</span></span>
    
- <span data-ttu-id="1808d-166">Com balanceamento de carga URL - http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1808d-166">Load-balanced URL - http://www.contoso.com</span></span>
    
<span data-ttu-id="1808d-167">Terceira zona:</span><span class="sxs-lookup"><span data-stu-id="1808d-167">Third zone:</span></span>
  
- <span data-ttu-id="1808d-168">Usuários - clientes autenticados</span><span class="sxs-lookup"><span data-stu-id="1808d-168">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="1808d-169">Zona - Extranet</span><span class="sxs-lookup"><span data-stu-id="1808d-169">Zone - Extranet</span></span>
    
- <span data-ttu-id="1808d-170">Com balanceamento de carga URL - https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1808d-170">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="1808d-p110">A terceira lista das URLs e zonas tem três tipos diferentes de usuários em três zonas diferentes. Ela está relacionada a conjunto de sites 3 e ele contém as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="1808d-p110">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="1808d-173">Primeira zona:</span><span class="sxs-lookup"><span data-stu-id="1808d-173">First zone:</span></span>
  
- <span data-ttu-id="1808d-174">Usuários - criadores de sites</span><span class="sxs-lookup"><span data-stu-id="1808d-174">Users - Site authors</span></span>
    
- <span data-ttu-id="1808d-175">Zona - Internet</span><span class="sxs-lookup"><span data-stu-id="1808d-175">Zone - Internet</span></span>
    
- <span data-ttu-id="1808d-176">URL com carga balanceada - http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="1808d-176">Load-balanced URL - http://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="1808d-177">Segunda zona:</span><span class="sxs-lookup"><span data-stu-id="1808d-177">Second zone:</span></span>
  
- <span data-ttu-id="1808d-178">Usuários - clientes anônimos</span><span class="sxs-lookup"><span data-stu-id="1808d-178">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="1808d-179">Zona - Internet</span><span class="sxs-lookup"><span data-stu-id="1808d-179">Zone - Internet</span></span>
    
- <span data-ttu-id="1808d-180">Com balanceamento de carga URL - http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1808d-180">Load-balanced URL - http://assets.contoso.com</span></span>
    
<span data-ttu-id="1808d-181">Terceira zona:</span><span class="sxs-lookup"><span data-stu-id="1808d-181">Third zone:</span></span>
  
- <span data-ttu-id="1808d-182">Usuários - clientes autenticados</span><span class="sxs-lookup"><span data-stu-id="1808d-182">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="1808d-183">Zona - Extranet</span><span class="sxs-lookup"><span data-stu-id="1808d-183">Zone - Extranet</span></span>
    
- <span data-ttu-id="1808d-184">Com balanceamento de carga URL - http://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1808d-184">Load-balanced URL - http://secureassets.contoso.com</span></span>
    

