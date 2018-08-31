---
title: Objetos e atributos excluídos e compatíveis com a IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Lista os atributos que são excluídos e suportados pelo IdFix tool.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539286"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Objetos e atributos excluídos e compatíveis com a IdFix
Há dois conjuntos de regras mantidos pelo IdFix: Multilocatário e Dedicado/ITAR. Neste momento, os dois conjuntos de regras excluem os mesmos objetos, atributos e valores de atributos de sua pesquisa. Isso pode mudar em futuras versões.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusões de erros de Multilocatário e Dedicado usados pelo IdFix
Esta seção lista os objetos, atributos e valores que IdFix exclui da sua pesquisa do diretório. O asterisco (\*) é um curinga que pode ser substituído por outros caracteres.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objetos, atributos e valores excluídos durante uma pesquisa do IdFix

|**Exclusão**|**Exemplo**|
|:-----|:-----|
|Feito\* |Administrador |
|{CAS_\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Convidado\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |MS-DS-KrbTgt-Link |
|IUSR _\* |IUSR _ *machinename* |
|IWAM\*  |IWAM _ *machinename* |
|msol\* |MSOL_AD_SYNC |
|conta suporte _\* ||
|SystemMailbox\* |SystemMailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName contém "\0ACNF:"|"\0ACNF: *GUID* " |
|O objeto contém o atributo IsCriticalSystemObject |Consulte [atributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Atributos e objetos de Multilocatário e Dedicado verificados pelo IdFix
Os atributos que são verificados quanto a erros pelo IdFix são descritos na seção "Objetos e atributos preparação de diretório" em [Preparar atributos de diretório para sincronização com o Office 365 usando a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

