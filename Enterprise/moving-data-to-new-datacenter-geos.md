---
title: Movendo dados principais para o novo Office 365 datacenter GEOS
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: 'Nova GEOS de datacenter adicione capacidade e calcule recursos para dar suporte à demanda contínua do cliente e crescimento de uso. Além disso, o novo GEOS de datacenter oferece residências de dados geográficos para dados essenciais do cliente. Principais dados do cliente é um termo que se refere a um subconjunto de dados do cliente definido nos termos do Microsoft Online Services: conteúdo da caixa de correio do Exchange Online (corpo de email, entradas de calendário e conteúdo de anexos de email) e conteúdo do site do SharePoint Online e os arquivos armazenados nesse site e arquivos carregados no OneDrive for Business.'
ms.openlocfilehash: d30ad64c96a3a2e790b911845141e1601758d384
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "30647979"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a>Movendo dados principais para o novo Office 365 datacenter GEOS

Continuaremos a abrir a nova GEOS do datacenter para o Office 365 para serviços corporativos. Esses novos datacenters GEOS adicionam capacidade e computam recursos para dar suporte à demanda contínua do cliente e crescimento de uso. Além disso, o novo GEOS de datacenter oferece residências de dados geográficos para dados essenciais do cliente. 

Principais dados do cliente é um termo que se refere a um subconjunto de dados do cliente definido nos [termos do Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkID=249048): 
- Conteúdo de caixa de correio do Exchange Online (corpo de email, entradas de calendário e conteúdo de anexos de email)
- Conteúdo do site do SharePoint Online e os arquivos armazenados nesse site
- Arquivos carregados no OneDrive for Business 
  
Os clientes existentes que têm seus dados principais de cliente armazenados em uma geografia do datacenter já existente não são afetados pelo lançamento de uma nova Geografia de datacenter. Não apresentamos recursos exclusivos, recursos ou certificações de conformidade com a nova Geografia do datacenter. Como cliente em qualquer uma dessas duas GEOS, você terá os mesmos controles de qualidade de serviço, desempenho e segurança que fazia antes. Oferecemos clientes existentes que têm requisitos de residência de dados rigorosos e que estão listados na tabela abaixo, uma opção para que seus principais dados do cliente sejam movidos para a nova geografia.
  
|Clientes com endereço de cobrança em * * * *|Geo do datacenter anterior * * * *|Nova Geografia do datacenter * * * *|Geo disponível desde * * * *|
|:-----|:-----|:-----|:-----|
|Japão * * * *| Ásia/Pacífico | Japão | Dezembro de 2014 |
|Austrália, Nova Zelândia, Fiji * * * *| Ásia/Pacífico | Austrália | Março de 2015 |
|Índia * * * *| Ásia/Pacífico | Índia | Outubro de 2015 |
|Canadá * * * *| América do Norte | Canadá | Maio de 2016 |
|Reino Unido * * * *| Europa | United Kingdom | Setembro de 2016 |
|Coréia do Sul * * * *| Ásia/Pacífico | Coréia do Sul | Abril de 2017 |
|França * * * *| Europa | França | Março de 2018 |
|Emirados Árabes Unidos * * * *| Europa | Emirados Árabes Unidos | Apresentados |
|África do Sul * * * *| Europa | África do Sul | Apresentados |
   
> [!NOTE]
> A opção de residência de dados e a disponibilidade para mover os dados do cliente para a nova geografia não é um padrão para cada nova geografia que iniciamos. À medida que expandirmos para o novo GEOS no futuro, avaliaremos a disponibilidade e as condições dos dados serão movidas em uma geografia por localização geográfica. 
  
Novos clientes ou locatários do Office 365 criados após a disponibilidade da nova Geografia do datacenter terão seus principais dados de cliente armazenados em repouso na nova Geografia do datacenter automaticamente.
  
Uma lista completa de todos os GEOS do datacenter, datacenters e o local dos dados do cliente em repouso está disponível como parte dos [mapas](https://office.com/datamaps)de datacenter interativos. 
  
## <a name="data-residency-option"></a>Opção de residência de dados

Fornecemos uma opção de residência de dados para os clientes existentes do Office 365 que estão cobertos pelo datacenter GEOS listados na tabela acima. Com essa opção, os clientes com requisitos de residência de dados podem solicitar a transferência dos dados principais do cliente para a nova geografia. Recomendamos que nossos clientes não executem nenhuma ação, a menos que sua organização precise que os principais dados do cliente sejam armazenados em repouso em suas respectivas geografias de datacenter. Ao optar por mover seus dados, os clientes limitam as possibilidades da Microsoft de otimizar o local dos dados principais do cliente em repouso em sua geografia atual ou no novo data center. Como cliente em qualquer uma dessas duas GEOS, você terá os mesmos controles de qualidade de serviço, desempenho e segurança que fazia antes.
  
Os clientes que precisam ter seus dados principais movidos para a nova geografia com um prazo comprometido da solicitação da Microsoft para que seus dados sejam movidos em uma janela de registro definida.  Revise a página [como solicitar a movimentação de dados](request-your-data-move.md) para obter mais detalhes sobre a janela de registro da sua geografia e as etapas para se inscrever no programa.  As movimentações de dados podem levar até 24 meses após o período de solicitação ser concluído.

- Não se faz nenhum resultado de ação na Microsoft ser capaz de mover seus dados principais do cliente em repouso para a sua nova Geografia do datacenter ao longo do tempo, como parte do gerenciamento e otimização de serviços.Seus dados principais do csutomer só podem ser movidos para a sua nova Geografia do datacenter, não para qualquer outra geografia.Notificaremos os administradores de locatários por meio do centro de mensagens quando uma movimentação de gerenciamento de serviço for concluída.
   
- Não apresentamos recursos exclusivos, recursos ou certificações de conformidade com a nova Geografia do datacenter.
    
- A complexidade, a precisão e a escala em que precisamos realizar movimentações de dados dentro de um ambiente operado globalmente e automatizado proíbem o compartilhamento quando uma movimentação de dados é esperada para concluir o locatário ou qualquer outro locatário único. Os clientes receberão uma confirmação no centro de mensagens por serviço participante quando sua movimentação de dados tiver sido concluída. 
    
- Movimentação de dados é uma operação de serviço de back-end com impacto mínimo para os usuários finais. Os recursos que podem ser afetados são listados na página [durante e após a movimentação de dados](during-and-after-your-data-move.md) . Respeitamos o contrato de [nível de serviço (SLA) dos serviços online da Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=523897) para disponibilidade, portanto, não há nada que os clientes precisem preparar ou monitorar durante a movimentação. A notificação de qualquer manutenção de serviço é feita, se necessário. 
    
## <a name="related-topics"></a>Tópicos relacionados 
 
[Como solicitar a movimentação de dados](request-your-data-move.md)
    
[PERGUNTAS FREQUENTEs sobre movimentação de dados gerais](data-move-faq.md)
  
[Nova GEOS de datacenter do Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Serviços do Azure por região](https://azure.microsoft.com/en-us/regions/)
