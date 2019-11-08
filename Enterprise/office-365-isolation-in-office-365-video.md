---
title: Isolamento de locatário do Office 365 no Office 365 vídeo
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
description: 'Resumo: uma explicação do isolamento de locatário no Office 365 video.'
ms.openlocfilehash: c9be942e10debeb729cda87a88131c17d736d4a2
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035581"
---
# <a name="tenant-isolation-in-office-365-video"></a>Isolamento de locatário no Vídeo do Office 365

> [!NOTE]
> O vídeo do Office 365 será substituído pelo Microsoft Stream. Para saber mais sobre o novo serviço de vídeo corporativo que adiciona inteligência à colaboração de vídeo e saiba mais sobre os planos de transição para clientes atuais de vídeo do Office 365, consulte [Migrate to Stream from office 365 Video](https://docs.microsoft.com/stream/).

## <a name="introduction"></a>Introdução

O armazenamento do Azure é usado para armazenar dados de vários serviços do Office 365, incluindo vídeo e Sway do Office 365. O armazenamento do Azure inclui o armazenamento de BLOB, que é um repositório de objetos de nuvem altamente escalonável, baseado em REST, que é usado para armazenar dados não estruturados. O armazenamento do Azure usa um modelo de controle de acesso simples; cada assinatura do Azure pode criar uma ou mais contas de armazenamento. Cada conta de armazenamento tem uma única chave secreta que é usada para controlar o acesso a todos os dados da conta de armazenamento. Isso oferece suporte ao cenário típico onde o armazenamento é associado aos aplicativos e esses aplicativos têm controle total sobre seus dados associados; por exemplo, Sway que armazena conteúdo no armazenamento do Azure. Todo o conteúdo do cliente para Sway é armazenado em contas de armazenamento do Azure compartilhadas. O conteúdo de cada usuário está em uma árvore de diretório separada de BLOBs no armazenamento do Azure.

Os sistemas que gerenciam o acesso aos ambientes do cliente (por exemplo, o portal do Azure, SMAPI, etc.) são isolados em um aplicativo do Azure operado pela Microsoft. Isso separa logicamente a infraestrutura de acesso do cliente da camada de armazenamento e dos aplicativos do cliente.

## <a name="tenant-isolation-in-office-365-video"></a>Isolamento de locatário no Vídeo do Office 365

O [vídeo do Office 365](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6) é um portal empresarial que oferece às organizações um destino altamente seguro e em toda a organização para lançamento, compartilhamento e descoberta de conteúdo de vídeo. No vídeo do Office 365, os vídeos de cada locatário são mantidos isolados e criptografados em todos os locais e só estão disponíveis para usuários autenticados que tenham acesso e permissões aos vídeos da organização. O vídeo do Office 365 usa uma combinação de tecnologias para fazer isso:

- O SharePoint Online é usado para armazenar o arquivo de vídeo e os metadados (título do vídeo, descrição, etc.). Ele também fornece a camada de segurança e conformidade (incluindo autenticação) e recursos de pesquisa.
- O serviços de mídia do Azure oferece transcodificação, streaming adaptável, entrega segura (usando criptografia AES) e recursos de miniatura.

O [serviços de mídia do Azure](https://azure.microsoft.com/services/media-services/) é uma oferta de plataforma como serviço para habilitar fluxos de trabalho de mídia de ponta a ponta na nuvem. A plataforma fornece uma API REST para carregar, codificar, criptografar (com PlayReady) e entrega de mídia através de datacenters do Azure em todo o mundo.

Todos os carregamentos do vídeo do Office 365 ocorrem via HTTPS. Quando um arquivo de vídeo é carregado, ele é armazenado no SharePoint Online e uma cópia do arquivo é enviada por meio de um canal criptografado para os serviços de mídia do Azure. O serviços de mídia do Azure transcodifica o vídeo em vários formatos otimizados para visualização da experiência (por exemplo, móvel, largura de banda baixa, alta largura de banda, etc.). Esses arquivos, juntamente com o arquivo original adquirido durante o carregamento, são armazenados no armazenamento de blob do Azure. Os arquivos são criptografados usando AES 128 conforme o algoritmo de pacote de criptografia comum MPEG (ou uma versão anterior do PlayReady) para reprodução e criptografados usando criptografia de armazenamento do AES 256 antes de ser armazenado no armazenamento de blob do Azure. (Usando o SDK do cliente do Azure Media Services, os clientes podem controlar qual criptografia é usada. Por exemplo, um cliente poderia aplicar a criptografia de armazenamento do Azure Media Services (AES 256) a um ativo de mídia de alto valor antes de carregar o armazenamento de blob do Azure.

O Azure Media Services também gera uma miniatura para o vídeo, que ele transmite junto com os metadados de miniatura para o SharePoint Online por meio de um canal criptografado.
