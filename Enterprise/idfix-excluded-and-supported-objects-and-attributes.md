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
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Lista os atributos que são excluídos e suportados pela ferramenta IdFix.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085080"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>Objetos e atributos excluídos e compatíveis com a IdFix
Há dois conjuntos de regras mantidos pelo IdFix: Multilocatário e Dedicado/ITAR. Neste momento, os dois conjuntos de regras excluem os mesmos objetos, atributos e valores de atributos de sua pesquisa. Isso pode mudar em futuras versões.
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>Exclusões de erros de Multilocatário e Dedicado usados pelo IdFix
Esta seção lista os objetos, atributos e valores que o IdFix exclui da pesquisa do diretório. O asterisco (\*) é um curinga que pode ser substituído por outros caracteres.
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>Objetos, atributos e valores excluídos durante uma pesquisa do IdFix

|**Exclusão**|**Exemplo**|
|:-----|:-----|
|Administrador\* |Administrador |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Convidado\* ||
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
|O objeto contém o atributo IsCriticalSystemObject |ConFira o [atributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169). |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>Atributos e objetos de Multilocatário e Dedicado verificados pelo IdFix
Os atributos que são verificados em busca de erros pelo IdFix são descritos na seção "objeto de diretório e preparação de atributo" em [preparar atributos de diretório para sincronização com o Office 365 usando a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).
  

