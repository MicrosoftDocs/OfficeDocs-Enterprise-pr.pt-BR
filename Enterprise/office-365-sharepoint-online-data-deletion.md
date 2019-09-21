---
title: Exclusão de dados do SharePoint Online para o Office 365
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
description: Uma explicação da exclusão de dados no SharePoint Online.
ms.openlocfilehash: ff219654387a17598f1ada8c866a005d8d4f5449
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067179"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a><span data-ttu-id="97540-103">Exclusão de dados do SharePoint Online no Office 365</span><span class="sxs-lookup"><span data-stu-id="97540-103">SharePoint Online Data Deletion in Office 365</span></span>

<span data-ttu-id="97540-104">O SharePoint Online armazena objetos como código abstrato em bancos de dados de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="97540-104">SharePoint Online stores objects as abstracted code within application databases.</span></span> <span data-ttu-id="97540-105">Quando um usuário carrega um arquivo no SharePoint Online, esse arquivo é desmontado e traduzido no código do aplicativo e armazenado em várias tabelas em vários bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="97540-105">When a user uploads a file to SharePoint Online, that file is disassembled and translated into application code and stored in multiple tables across multiple databases.</span></span> <span data-ttu-id="97540-106">No SharePoint Online, todo o conteúdo que um cliente carrega é dividido em partes, criptografadas (potencialmente com várias chaves AES de 256 bits) e distribuídas no datacenter.</span><span class="sxs-lookup"><span data-stu-id="97540-106">In SharePoint Online, all content that a customer uploads is broken into chunks, encrypted (potentially with multiple AES 256-bit keys), and distributed across the datacenter.</span></span> <span data-ttu-id="97540-107">Para obter detalhes específicos sobre o processo de fragmentação e criptografia, consulte [Encryption in the Microsoft Cloud](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md).</span><span class="sxs-lookup"><span data-stu-id="97540-107">For specific details about the chunking and encryption process, see [Encryption in the Microsoft Cloud](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md).</span></span> 

<span data-ttu-id="97540-108">No SharePoint Online, os itens são mantidos por 93 dias a partir do momento em que você os exclui do local original.</span><span class="sxs-lookup"><span data-stu-id="97540-108">In SharePoint Online, items are retained for 93 days from the time you delete them from their original location.</span></span> <span data-ttu-id="97540-109">Eles permanecem na lixeira do site o horário inteiro, a menos que alguém os exclua ou esvazia essa lixeira.</span><span class="sxs-lookup"><span data-stu-id="97540-109">They stay in the site Recycle Bin the entire time, unless someone deletes them from there or empties that Recycle Bin.</span></span> <span data-ttu-id="97540-110">Nesse caso, os itens vão para a lixeira do conjunto de sites, onde eles permanecem no restante dos 93 dias.</span><span class="sxs-lookup"><span data-stu-id="97540-110">In that case, the items go to the site collection Recycle Bin, where they stay for the remainder of the 93 days.</span></span> <span data-ttu-id="97540-111">Para obter informações sobre como restaurar itens excluídos, consulte [restaurar itens na lixeira de um site do SharePoint](https://support.office.com/en-us/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) e [restaurar itens excluídos da](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b)lixeira do conjunto de sites.</span><span class="sxs-lookup"><span data-stu-id="97540-111">For info about restoring deleted items, see [Restore items in the Recycle Bin of a SharePoint site](https://support.office.com/en-us/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) and [Restore deleted items from the site collection recycle bin](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b).</span></span> <span data-ttu-id="97540-112">O tempo de retenção da lixeira não é configurável no SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="97540-112">The Recycle Bin retention time is not configurable in SharePoint Online.</span></span>

<span data-ttu-id="97540-113">Ao excluir um conjunto de sites, você também está excluindo a hierarquia de sites na coleção e todos os conteúdos dentro deles:</span><span class="sxs-lookup"><span data-stu-id="97540-113">When you delete a site collection, you're also deleting the hierarchy of sites in the collection, and all content within them:</span></span>
- <span data-ttu-id="97540-114">Documentos e bibliotecas de documentos</span><span class="sxs-lookup"><span data-stu-id="97540-114">Documents and document libraries</span></span>
- <span data-ttu-id="97540-115">Lista e dados de lista</span><span class="sxs-lookup"><span data-stu-id="97540-115">Lists and list data</span></span>
- <span data-ttu-id="97540-116">Definições de configuração do site</span><span class="sxs-lookup"><span data-stu-id="97540-116">Site configuration settings</span></span>
- <span data-ttu-id="97540-117">Informações de função e segurança relacionadas ao site ou seus subsites</span><span class="sxs-lookup"><span data-stu-id="97540-117">Role and security information that is related to the site or its subsites</span></span>
- <span data-ttu-id="97540-118">Subsites do site de nível superior, seu conteúdo e informações de usuário</span><span class="sxs-lookup"><span data-stu-id="97540-118">Subsites of the top-level website, their contents, and user information</span></span>

<span data-ttu-id="97540-119">Se você excluir acidentalmente um conjunto de sites, ele poderá ser restaurado por um administrador global ou do SharePoint usando o centro de administração do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="97540-119">If you accidentally delete a site collection, it can be restored by a global or SharePoint admin using the SharePoint admin center.</span></span> 

<span data-ttu-id="97540-120">A exclusão fixa ocorre quando um usuário limpa itens excluídos da lixeira do conjunto de sites, quando os períodos de retenção e backup expiram ou quando um administrador exclui permanentemente um conjunto de sites usando o [cmdlet Remove-SPODeletedSite](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="97540-120">Hard deletion occurs when a user purges deleted items from the site collection Recycle Bin, when the retention and backup periods expire, or when an administrator permanently deletes a site collection using the [Remove-SPODeletedSite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span></span> <span data-ttu-id="97540-121">Quando um usuário exclui (permanentemente exclui ou limpa) o conteúdo do SharePoint Online, todas as chaves de criptografia dos blocos excluídos também são excluídas.</span><span class="sxs-lookup"><span data-stu-id="97540-121">When a user hard deletes (permanently deletes, or purges) content from SharePoint Online, all encryption keys for the deleted chunks are also deleted.</span></span> <span data-ttu-id="97540-122">Os blocos nos discos que armazenaram anteriormente os fragmentos excluídos são marcados como não usados e estão disponíveis para reutilização.</span><span class="sxs-lookup"><span data-stu-id="97540-122">The blocks on the disks that previously stored the deleted chunks are marked as unused and available for re-use.</span></span>
