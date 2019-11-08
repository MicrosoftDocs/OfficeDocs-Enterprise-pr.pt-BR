---
title: Controle de acesso e isolamento do Office 365 no Azure Active Directory
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
description: 'Resumo: como o isolamento e o controle de acesso funcionam no Azure Active Directory.'
ms.openlocfilehash: 0e6423c53bd0c2823708f59830d1ba628a0c71ca
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035778"
---
# <a name="isolation-and-access-control-in-azure-active-directory"></a>Isolamento e controle de acesso do Azure Active Directory

O Azure Active Directory foi projetado para hospedar vários locatários de forma altamente segura através do isolamento lógico de dados. O acesso ao Azure Active Directory é restringido por uma camada de autorização. O Azure Active Directory isola os clientes que usam contêineres de locatário como limites de segurança para proteger o conteúdo de um cliente, de modo que o conteúdo não possa ser acessado ou comprometido por colocatários. Três verificações são realizadas pela camada de autorização do Azure Active Directory:

- O principal está habilitado para acesso ao locatário do Azure Active Directory?
- O principal está habilitado para acesso aos dados neste locatário?
- A função do principal neste locatário é autorizada para o tipo de acesso a dados solicitado?

Nenhum aplicativo, usuário, servidor ou serviço pode acessar o Azure Active Directory sem a autenticação apropriada e token ou certificado. As solicitações serão rejeitadas se não forem acompanhadas por credenciais adequadas.

Efetivamente, o Azure Active Directory hospeda cada locatário em seu próprio contêiner protegido, com políticas e permissões para e dentro do contêiner exclusivamente proprietário e gerenciado pelo locatário.
 
![Contêiner do Azure](media/office-365-isolation-azure-container.png)

O conceito de contêineres de locatário está profundamente refinado no serviço de diretório em todas as camadas, de portais de forma totalmente direcionada para o armazenamento persistente. Mesmo quando vários metadados do locatário do Azure Active Directory são armazenados no mesmo disco físico, não há relação entre os contêineres que não são definidos pelo serviço de diretório, que, por sua vez, é determinado pelo administrador do locatário. Não pode haver conexões diretas com o armazenamento do Azure Active Directory a partir de qualquer aplicativo ou serviço solicitante sem passar pela camada de autorização.

No exemplo abaixo, a Contoso e a Fabrikam têm contêineres separados e dedicados, e mesmo que esses contêineres possam compartilhar algumas das mesmas infra-estruturas subjacentes, como servidores e armazenamento, eles permanecem separados e isolados uns dos outros, e por portão por camadas de autorização e controle de acesso.
 
![Contêineres dedicados do Azure](media/office-365-isolation-azure-dedicated-containers.png)

Além disso, não há componentes de aplicativo que podem ser executados de dentro do Azure Active Directory, e não é possível que um locatário viole forçosamente a integridade de outro locatário, chaves de criptografia de acesso de outro locatário ou leia dados brutos do servidor.

Por padrão, o Azure Active Directory proíbe todas as operações emitidas por identidades em outros locatários. Cada locatário é logicamente isolado no Azure Active Directory por meio de controles de acesso baseados em declarações. Leituras e gravações de dados de diretório são delimitadas aos contêineres de locatários e restringidas por uma camada de abstração interna e uma camada de controle de acesso baseado em função (RBAC), que juntos aplicam o locatário como o limite de segurança. Todas as solicitações de acesso a dados de diretório são processadas por essas camadas e todas as solicitações de acesso no Office 365 são vigiadas pela lógica acima.

O Azure Active Directory tem a América do Norte, governo dos EUA, União Européia, Alemanha e partições mundiais. Há um locatário em uma única partição, e as partições podem conter vários locatários. As informações de partição são recortadas dos usuários. Uma determinada partição (incluindo todos os locatários dentro dela) é replicada em vários datacenters. A partição de um locatário é escolhida com base nas propriedades do locatário (por exemplo, o código do país). Segredos e outras informações confidenciais em cada partição são criptografados com uma chave dedicada. As chaves são geradas automaticamente quando uma nova partição é criada.

As funcionalidades de sistema do Azure Active Directory são uma instância exclusiva para cada sessão de usuário. Além disso, o Azure Active Directory usa tecnologias de criptografia para fornecer isolamento de recursos compartilhados do sistema no nível da rede para impedir a transferência não autorizada e indesejada das informações.
