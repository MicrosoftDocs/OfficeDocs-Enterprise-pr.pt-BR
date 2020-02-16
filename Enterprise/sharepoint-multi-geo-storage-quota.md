---
title: Cotas de armazenamento do SharePoint em ambientes multigeográficos
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Saiba mais sobre as cotas de armazenamento do SharePoint em ambientes multigeográficos.
ms.openlocfilehash: b04c05f911e6ba4c5362e64dc6db4bf711ed78aa
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974203"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="e9072-103">Cotas de armazenamento do SharePoint em ambientes multigeográficos</span><span class="sxs-lookup"><span data-stu-id="e9072-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="e9072-104">Por padrão, todas as localizações geográficas de um ambiente multigeográfico compartilham a cota de armazenamento disponível do locatário.</span><span class="sxs-lookup"><span data-stu-id="e9072-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="e9072-105">Com as configurações de cota de armazenamento geográfico do SharePoint é possível gerenciar a cota de armazenamento para cada localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="e9072-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="e9072-106">Ao alocar a cota de armazenamento de uma localização geográfica, ela torna-se a quantidade máxima de armazenamento disponível daquela localização geográfica e será deduzida da cota de armazenamento disponível do locatário.</span><span class="sxs-lookup"><span data-stu-id="e9072-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="e9072-107">A cota de armazenamento do locatário disponível restante é, em seguida, compartilhada entre as localizações geográficas configuradas para as quais uma cota de armazenamento específica não foi alocada.</span><span class="sxs-lookup"><span data-stu-id="e9072-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="e9072-108">A cota de armazenamento do SharePoint de qualquer localização geográfica pode ser alocada pelo administrador do SharePoint Online ao conectar-se à localização central.</span><span class="sxs-lookup"><span data-stu-id="e9072-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="e9072-109">Administradores geográficos para localizações via satélite podem exibir a cota de armazenamento, mas não podem alocá-la.</span><span class="sxs-lookup"><span data-stu-id="e9072-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="e9072-110">Definir uma cota de armazenamento para uma localização geográfica</span><span class="sxs-lookup"><span data-stu-id="e9072-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="e9072-111">Use o [Módulo do Microsoft SharePoint Online](https://www.microsoft.com/download/details.aspx?id=35588 ) e conecte-se a uma localização central para alocar a cota de armazenamento de uma localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="e9072-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/download/details.aspx?id=35588 ) and connect to the central location to allocate the storage quota for a geo location.</span></span> 

<span data-ttu-id="e9072-112">Para alocar uma Cota de Armazenamento para um localização, execute o cmdlet:</span><span class="sxs-lookup"><span data-stu-id="e9072-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

<span data-ttu-id="e9072-113">Para exibir a Cota de Armazenamento da localização geográfica atual, execute:</span><span class="sxs-lookup"><span data-stu-id="e9072-113">To view Storage Quota for the current geo location, run:</span></span>

`Get-SPOGeoStorageQuota`

![Captura de tela da janela do PowerShell mostrando o cmdlet Get SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

<span data-ttu-id="e9072-115">Para exibir a Cota de Armazenamento para todas as localizações geográficas, execute:</span><span class="sxs-lookup"><span data-stu-id="e9072-115">To view Storage Quota for all geo locations, run:</span></span>

`Get-SPOGeoStorageQuota -AllLocations`

<span data-ttu-id="e9072-116">Para remover a cota de armazenamento alocado para uma localização geográfica, defina `StorageQuota value = 0`:</span><span class="sxs-lookup"><span data-stu-id="e9072-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
