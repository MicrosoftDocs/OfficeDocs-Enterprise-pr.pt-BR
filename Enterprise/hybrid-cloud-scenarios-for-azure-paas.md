---
title: "Cenários de nuvem híbrida para PaaS do Azure"
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
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "Resumo: Entenda os cenários e arquitetura híbrida para a plataforma Microsoft como um serviço (PaaS)-based ofertas de nuvem no Windows Azure."
ms.openlocfilehash: f6d7d1c9ca04c0b7bbaa020a771cf84734e5d385
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Cenários de nuvem híbrida para PaaS do Azure

 **Resumo:** Entenda os cenários e arquitetura híbrida para a plataforma Microsoft como um serviço (PaaS)-based ofertas de nuvem no Windows Azure.
  
Combinar os dados no local ou recursos de computação com aplicativos novos ou convertidos em execução no Azure PaaS, que podem tirar proveito de escala, confiabilidade e desempenho na nuvem e oferecer um suporte melhor para usuários móveis. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Arquitetura de cenário do Windows Azure PaaS híbrida

A Figura 1 mostra a arquitetura dos cenários de implantação híbrida baseada em PaaS Microsoft no Azure.
  
**Figura 1: Cenários de implantação híbrida baseada em PaaS Microsoft no Azure**

![Cenários híbridos da Microsoft baseados em PaaS no Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS.png)
  
Para cada camada da arquitetura:
  
- Cenários e aplicativos
    
    Um aplicativo de PaaS híbrido é executado no Windows Azure e usa os recursos de computação ou armazenamento local.
    
- Identidade
    
    Consiste de sincronização de diretório ou federação com um provedor de identidade de terceiros.
    
- Rede
    
    Consiste em seu pipe Internet existente ou uma conexão ExpressRoute com correspondência pública para PaaS do Azure. Você deve incluir uma maneira para o aplicativo do Azure PaaS acessar o recurso de compute ou armazenamento local.
    
- Local
    
    Consiste em infraestrutura de segurança e de identidade e a linha existente de aplicativos de negócios (LOB) ou servidores de banco de dados, que um aplicativo do Windows Azure PaaS pode acessar com segurança.
    
## <a name="azure-paas-hybrid-application"></a>Aplicativo do Azure PaaS híbrida

Figura 2 mostra a configuração de um aplicativo híbrida executando no Windows Azure.
  
**Figura 2: Aplicativo de implantação híbrida baseada em PaaS Azure**

![Aplicativo híbrido baseado em PaaS no Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps.png)
  
Na Figura 2, uma rede local hospeda aplicativos nos servidores e DMZ contendo um servidor proxy ou armazenamento. Ele está conectado aos serviços do Azure PaaS pela Internet ou com uma conexão ExpressRoute.
  
Uma organização pode tornar seus recursos de armazenamento ou compute disponíveis para o aplicativo de híbrido Azure PaaS por:
  
- Hospedando o recurso em servidores no DMZ.
    
- Hospedagem de um servidor proxy reverso no DMZ, que permite solicitações de entrada, autenticadas e baseada em HTTPS para o recurso que está localizado no local.
    
O aplicativo do Azure pode usar as credenciais a partir de:
  
- Azure AD, que pode ser sincronizado com seu provedor de identidade de local, como o Windows Server AD.
    
- Um provedor de identidade de terceiros.
    
### <a name="example-azure-paas-hybrid-application"></a>Aplicativo do exemplo Azure PaaS híbrido

A Figura 3 mostra um exemplo de aplicativo híbrida executando no Windows Azure.
  
**Figura 3: Um exemplo aplicativo baseado no Windows Azure PaaS híbrido**

![Um aplicativo híbrido de exemplo baseado em PaaS no Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_Ex.png)
  
Na Figura 3, um hosts de rede local uma LOB App. Azure PaaS hospeda um aplicativo móvel personalizado. Um smartphone na Internet acessa o aplicativo móvel personalizado no Azure, que envia solicitações de dados para o aplicativo LOB local.
  
Este exemplo de aplicativo do Windows Azure PaaS híbrido é um aplicativo móvel personalizado que fornece informações de contato atualizadas sobre funcionários. O cenário híbrido de ponta a ponta consiste em:
  
- Um smartphone aplicativo que exige validado, credenciais de local para ser executado.
    
- Um aplicativo móvel personalizado em execução no Azure PaaS, que solicita informações sobre funcionários específicos com base em consultas do aplicativo do smartphone de um usuário.
    
- Um servidor proxy reverso no DMZ que valide o aplicativo móvel personalizado e encaminha a solicitação.
    
- Um farm de servidores de aplicativos LOB que atende à solicitação de contato, sujeito as permissões da conta do usuário.
    
Porque o provedor de identidade local foi sincronizado com o Azure AD, o aplicativo móvel personalizado e o aplicativo LOB possam validar nome da conta do usuário solicitante.
  
## <a name="stretch-database-with-sql-server-2016"></a>Estender o banco de dados com o SQL Server 2016

Alongar banco de dados é um recurso do SQL Server 2016 que permite transparente e segurança mover dados frio, como dados corporativos fechado em uma tabela grande que contém as informações de pedido de cliente, para um banco de dados SQL Alongar no Windows Azure.
  
Quando alongado, o conteúdo de uma instância do SQL Server, um banco de dados ou até mesmo em uma única tabela é a combinação de dados local no servidor do SQL Server 2016 e dados remotos no Windows Azure. Dados que se tornará qualificados para alongar automaticamente são movidos para o Azure pelo 2016 do SQL Server.
  
Figura 4 mostra o banco de dados de alongar com 2016 do SQL Server.
  
**Figura 4: Alongamento banco de dados com o SQL Server 2016**

![Estender o banco de dados com o SQL Server 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_PaaS_Apps_SQL.png)
  
Na Figura 4, uma rede local hospeda um servidor executando o SQL Server 2016 com um pequeno banco de dados local. Azure PaaS hospeda uma instância do banco de dados do SQL Server Alongar Azure com a parte estendida do banco de dados. Consultas de T-SQL de um usuário local enviadas ao SQL server no local com segurança são encaminhadas para o Azure SQL Alongar banco de dados, que retorna os resultados ao usuário solicitante.
  
 Consultas de usuário que incluem os dados históricos transparente são encaminhadas para o banco de dados Alongar do SQL Azure. As consultas não precisará ser escritos novamente, mesmo que a tabela é alongada.
  
Banco de dados Alongar fornece uma opção econômica para armazenamento de longo prazo e transparente acesso a dados históricos. Ele também resolve problemas de desempenho e disponibilidade que surgem quando tabelas tornam-se muito grandes.
  
Para obter mais informações, consulte [Alongar banco de dados](https://msdn.microsoft.com/library/dn935011.aspx).
  
## <a name="see-also"></a>See Also

[Nuvem híbrida da Microsoft para arquitetos da empresa](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa da nuvem corporativa da Microsoft Recursos para responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)



