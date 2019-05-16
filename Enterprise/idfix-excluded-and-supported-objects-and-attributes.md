---
title: Objetos e atributos excluídos e suportados pelo IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Lista os atributos que são excluídos e suportados pela ferramenta IdFix.
ms.openlocfilehash: bf88fea3592860a89d69717177593b6553318ee4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067267"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Objetos e atributos excluídos e suportados pelo IdFix
Há dois conjuntos de regras mantidas pelo IdFix; Multilocatário e dedicado/ITAR. No momento, os dois conjuntos de regras excluem os mesmos objetos, atributos e valores de atributo de sua pesquisa. Isso pode ser alterado em versões futuras.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusões de erro de vários locatários e dedicados usadas pelo IdFix
Esta seção lista os objetos, atributos e valores que o IdFix exclui da pesquisa do diretório. O asterisco (\*) é um curinga que pode ser substituído por outros caracteres.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objetos, atributos e valores excluídos durante uma pesquisa do IdFix

|**Exclusão**|**Exemplo**|
|:-----|:-----|
|Administrador\* |Administrador |
|CAS_{\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-KrbTgt-link |
|IUSR\* |IUSR _ *MachineName* |
|Iwan\*  |IWAM _ *MachineName* |
|MSol\* |MSOL_AD_SYNC |
|à\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contém "\0ACNF:"|"\0ACNF: *GUID* " |
|Objeto contém o atributo IsCriticalSystemObject |Confira o [atributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Objetos e atributos de vários locatários e dedicados verificados por IdFix
Os atributos que são verificados em busca de erros pelo IdFix são descritos na seção "objeto de diretório e preparação de atributo" em [preparar atributos de diretório para sincronização com o Office 365 usando a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

