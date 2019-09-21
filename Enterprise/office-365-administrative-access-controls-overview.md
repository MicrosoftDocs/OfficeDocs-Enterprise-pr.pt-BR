---
title: Controles de acesso administrativo no Office 365
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
description: 'Resumo: uma visão geral dos controles de acesso administrativo e categorização de dados do Office 365.'
ms.openlocfilehash: e8cc470c617deea7435841f276b772b0a8ef17a3
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067184"
---
# <a name="administrative-access-controls-in-office-365"></a>Controles de acesso administrativo no Office 365 

A Microsoft investiu pesadamente em sistemas e controles que automatizam a maioria das operações do Office 365 enquanto limitava intencionalmente o acesso ao conteúdo do cliente pela Microsoft. Os seres humanos governam o serviço e o software opera o serviço. Isso permite que a Microsoft gerencie o Office 365 em escala e gerencie os riscos de ameaças internas ao conteúdo do cliente.

Por padrão, os engenheiros da Microsoft têm nenhum privilégio administrativo de pé e zero acesso de pé ao conteúdo do cliente no Office 365. Um engenheiro da Microsoft pode ter acesso limitado, auditado e protegido ao conteúdo de um cliente por um período limitado de tempo. O acesso é apenas quando necessário para operações de serviço e somente quando aprovado por um membro do gerenciamento sênior da Microsoft. Para clientes licenciados de lockbox de clientes, o cliente fornece aprovação de acesso para seu conteúdo hospedado no Office 365.

A Microsoft fornece serviços online usando várias formas de entrega na nuvem:

- **Nuvens públicas:** Inclui versões de vários locatários do Office 365, Azure e outros serviços hospedados na América do Norte, América do Sul, Europa, Ásia, Austrália, etc.
- **Nuvens nacionais:** Inclui todas as nuvens soberana e operadas por terceiros fora dos Estados Unidos (exceto aqueles observados anteriormente), como o Office 365 na China (operado pela 21Vianet) e o Office 365 na Alemanha (operado pela Microsoft, mas em um modelo no qual um data de confiança em alemão, O alemão Telekom, controla e monitora o acesso da Microsoft aos dados e sistemas de clientes que contêm dados do cliente).
- **Nuvens governamentais:** Inclui os serviços do Office 365 e do Azure que estão disponíveis para os clientes do governo dos Estados Unidos.

Para os fins deste artigo, os serviços do Office 365 incluem:

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [OneDrive for Business](https://docs.microsoft.com/OneDrive/onedrive)
- [Skype for Business](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a>Controles de acesso do Office 365

Para fins de controle de acesso, a Microsoft categoriza os dados do Office 365 como dados do cliente ou outros tipos de dados.

### <a name="customer-data"></a>Dados do cliente

Os dados do cliente são todos os dados fornecidos por ou em nome de um cliente ao usar os serviços do Office 365. Este é o conteúdo do cliente criado diretamente ou carregado por usuários do Office 365, incluindo:

- Emails
- Conteúdo do SharePoint Online
- Mensagens instantâneas
- Itens de calendário
- Documentos
- Contatos
- Informações de identificação do usuário final (EUII) (dados exclusivos de um usuário ou que são vinculados a um usuário individual, mas não inclui conteúdo do cliente).

### <a name="other-types-of-data"></a>Outros tipos de dados

Outros tipos de dados incluem:

- **Dados da conta:** Inclui dados administrativos (informações fornecidas por administradores ao inscrever-se ou comprar serviços) e dados de pagamento (informações sobre instrumentos de pagamento, como detalhes do cartão de crédito).
- **Informações de identificação corporativa:** Inclui dados usados para identificar um locatário, dados de uso e não vinculáveis a um usuário individual ou incluído no conteúdo do cliente.
- **Metadados do sistema:** Inclui logs de serviço que contêm definições de configuração, status do sistema, endereços IP da Microsoft e informações técnicas sobre inscrições e locatários.

A Microsoft estabeleceu mecanismos de controle de acesso para garantir que ninguém tenha acesso não aprovado aos dados do cliente ou aos dados de controle de acesso. Os dados de controle de acesso gerenciam o acesso a outros tipos de dados ou funções dentro do ambiente, incluindo acesso ao conteúdo do cliente ou EUII, senhas da Microsoft, certificados de segurança e outros dados relacionados à autenticação. Os mecanismos de controle de acesso também protegem contra acesso físico, lógico ou remoto não aprovado ao ambiente de produção do Office 365.

Há três categorias de controles de acesso usados pela Microsoft para a operação do Office 365:

- Controles de isolamento
- Controles de pessoal
- Controles de tecnologia

Quando combinadas, esses controles ajudam a evitar e detectar ações mal-intencionadas no Office 365. Além dos controles de isolamento, pessoal e tecnologia usados pela Microsoft, há uma quarta categoria de controles: as implementadas por clientes.

O Office 365 permite que você gerencie dados da mesma forma que os dados são gerenciados em ambientes locais. A pessoa que assina uma organização para o Office 365 se torna automaticamente um administrador global. O administrador global tem acesso a todos os recursos nos portais de gerenciamento e pode:

- Criar ou editar usuários
- Atribuir funções de administrador a outras pessoas
- Redefinir senhas de usuário
- Gerenciar licenças de usuário
- Gerenciar domínios
- Aprovar solicitações de lockbox do cliente

Recomendamos que cada organização configure pelo menos duas contas de administrador. Para organizações de grande porte, recomendamos contas de administração especializadas que atendam a diferentes funções.

Para obter informações sobre como atribuir permissões e funções de administrador, consulte [atribuindo funções de administrador no office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) e [sobre as funções de administrador do Office 365](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).

## <a name="related-links"></a>Links relacionados

- [Controles de isolamento](office-365-isolation-controls.md)
- [Controles de pessoal](office-365-personnel-controls.md)
- [Controles de tecnologia](office-365-technology-controls.md)
- [Monitorando e auditando controles de acesso ](office-365-monitoring-and-auditing-access-controls.md)
- [Controles de acesso do Yammer Enterprise](office-365-yammer-enterprise-access-controls.md)