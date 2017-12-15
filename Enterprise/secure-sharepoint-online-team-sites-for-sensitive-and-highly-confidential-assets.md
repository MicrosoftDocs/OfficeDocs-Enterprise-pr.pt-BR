---
title: Proteger sites de equipe do SharePoint Online para os ativos altamente confidenciais
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "Resumo: Como Contoso implementou proteção confidencial e altamente confidenciais sites de equipe do SharePoint Online para mais fácil, ainda segura, colaboração para executivos e seus centros de pesquisa."
ms.openlocfilehash: 1574babb54bfcb3fd74fb8ce4f31c364bb96b14a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="a11a2-103">Proteger sites de equipe do SharePoint Online para os ativos altamente confidenciais</span><span class="sxs-lookup"><span data-stu-id="a11a2-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="a11a2-104">**Resumo:** Como proteção confidencial da Contoso implementada e altamente confidenciais SharePoint Online sites de equipe para colaboração mais fácil, embora segura, para executivos e seus centros de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="a11a2-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers.</span></span>
  
<span data-ttu-id="a11a2-p101">A liderança executiva da Contoso deseja usar o Office 365 e armazenar os arquivos em um único local para colaboração, independentemente de onde um executivo pode ser. Da mesma forma, os departamentos de pesquisa da Contoso — com divisões em Paris, Moscou, Nova York, Pequim e Bangalore — gostaria de fazer a transição de seus ativos digitais do local para a nuvem para facilitar o acesso e colaboração mais vulnerável entre equipes.</span><span class="sxs-lookup"><span data-stu-id="a11a2-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="a11a2-p102">No entanto, em ambos os casos, o acesso a esses recursos deve ser restrito ao subconjunto de pessoas que têm permissão para exibir ou alterá-los, com permissões em andamento para o site administrado pela equipe de TI. Além disso, mesmo se alguns recursos são intencionalmente ou não distribuído, eles deverão ser criptografados e tem permissões para impedir aqueles que não têm acesso para exibir ou alterar seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a11a2-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="a11a2-109">Os administradores de segurança e o SharePoint em Contoso do departamento de TI decidiu usar proteção confidencial e altamente confidenciais sites de equipe do SharePoint Online, conforme mostrado na Figura 1.</span><span class="sxs-lookup"><span data-stu-id="a11a2-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="a11a2-110">**Figura 1: Comparação de proteção confidencial e altamente confidenciais sites de equipe do SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="a11a2-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![Proteção com alto nível de confidencialidade para sites de equipe do SharePoint Online](images/Contoso_Poster/SP_Solution.png)
  
<span data-ttu-id="a11a2-112">A Contoso usou estas etapas para criar sites de equipe do SharePoint Online seguras para seus executivos e equipes de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="a11a2-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="a11a2-113">Criar um site de equipe ' **executivos** confidencial SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a11a2-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="a11a2-114">O novo site de equipe usa grupos existentes do Windows Azure AD (Active Directory) para executivos como membros com o nível de permissão do SharePoint editar e um pequeno conjunto de contas de administrador do SharePoint como proprietários com o nível de permissão Controle total.</span><span class="sxs-lookup"><span data-stu-id="a11a2-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="a11a2-115">Migrar os arquivos de executivos</span><span class="sxs-lookup"><span data-stu-id="a11a2-115">Migrate executives files</span></span>
    
    <span data-ttu-id="a11a2-116">Mova o local executivo arquivos e pastas existentes para o novo site de equipe executivos SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a11a2-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="a11a2-117">Criar um site de equipe ' **Research** altamente confidencial SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a11a2-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="a11a2-p103">O novo site de equipe usa grupos existentes de equipe de pesquisa Azure AD como membros com o nível de permissão de edição e um pequeno conjunto de contas de administrador do SharePoint como proprietários com o nível de permissão Controle total. Um rótulo AIP atribuído a pesquisa de arquivos garante que eles são criptografados e apenas membros de um grupo de pesquisa podem abri-los.</span><span class="sxs-lookup"><span data-stu-id="a11a2-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="a11a2-120">Migrar os arquivos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="a11a2-120">Migrate research files</span></span>
    
    <span data-ttu-id="a11a2-121">Mova a equipe de pesquisa existente no local arquivos e pastas para o novo site de equipe de pesquisa do SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="a11a2-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="a11a2-p104">O resultado é dois sites de colaboração cujo acesso hermeticamente é controlado por segurança e administradores do SharePoint. Para arquivos com o rótulo altamente confidenciais AIP, mesmo que elas sejam distribuídas fora o site de equipe de pesquisa, eles são criptografados e só podem ser abertos por um membro de uma equipe de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="a11a2-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="a11a2-124">Para obter mais informações, consulte [arquivos e sites seguro do SharePoint Online](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span><span class="sxs-lookup"><span data-stu-id="a11a2-124">For more information, see [Secure SharePoint Online sites and files](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files).</span></span>
  
 <span data-ttu-id="a11a2-125">Para definir isso para esse demonstração, prova de conceito ou desenvolvimento e teste, consulte [sites seguro do SharePoint Online em um ambiente de desenvolvimento e teste](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span><span class="sxs-lookup"><span data-stu-id="a11a2-125">To set this up for demonstration, proof-of-concept, or dev/test, see [Secure SharePoint Online sites in a dev/test environment](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a11a2-126">See Also</span><span class="sxs-lookup"><span data-stu-id="a11a2-126">See Also</span></span>

[<span data-ttu-id="a11a2-127">Cenários empresariais para a Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="a11a2-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="a11a2-128">Contoso em nuvem da Microsoft</span><span class="sxs-lookup"><span data-stu-id="a11a2-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="a11a2-129">Recursos de arquitetura de TI do Microsoft</span><span class="sxs-lookup"><span data-stu-id="a11a2-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="a11a2-130">Alongar para o banco de dados</span><span class="sxs-lookup"><span data-stu-id="a11a2-130">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="a11a2-131">Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI</span><span class="sxs-lookup"><span data-stu-id="a11a2-131">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




