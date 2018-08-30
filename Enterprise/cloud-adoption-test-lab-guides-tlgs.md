---
title: Testar o Office 365 com os Guias de Laboratório de Teste (TLGs) para adoção da nuvem
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/23/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Resumo: use estes Guias de Laboratório de Teste (TLGs) para adoção da nuvem para configurar ambientes de desenvolvimento/teste, de prova de conceito ou de demonstração para produtos do Office 365, Dynamics 365 e Office Server.'
ms.openlocfilehash: 796d34294ef92702214df30ca5553759554996d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "23041495"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>Testar o Office 365 com os Guias de Laboratório de Teste (TLGs) para adoção da nuvem

 **Resumo:** use estes Guias de Laboratório de Teste (TLGs) para adoção da nuvem para configurar ambientes de desenvolvimento/teste, de prova de conceito ou de demonstração para produtos do Office 365, Dynamics 365 e Office Server.
  
Os TLGs ajudam você a aprender rapidamente sobre os produtos da Microsoft. Eles são ótimos para situações nas quais você precisa avaliar uma tecnologia ou configuração antes de decidir se ela serve para você ou antes de distribui-la aos usuários. A experiência prática no estilo "criei por conta própria e funciona" ajuda você a entender os requisitos de implantação de um novo produto ou solução para poder planejar melhor sua hospedagem em produção.
  
Os TLGs também criam ambientes representativos de desenvolvimento/teste de aplicativos, também conhecidos como ambientes de desenvolvimento/teste.
  
![Guias do Laboratório de Teste da Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Consulte estes recursos adicionais antes de começar:
  
- Exibir a sessão do Microsoft Virtual Academy [Guias do Laboratório de Teste da Microsoft Cloud com Adoção de Nuvem](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 ) (apenas 22 minutos).
    
- Clique [aqui](http://aka.ms/catlgstack) para exibir um mapa visual para todos os artigos da pilha da Guia do Laboratório de Teste do One Microsoft Cloud.
    
## <a name="office-365-devtest-environment"></a>Ambiente de desenvolvimento/teste do Office 365

Use estes artigos para compilar seu ambiente de desenvolvimento/teste do Office 365:
  
- [Configuração básica do ambiente de desenvolvimento/teste](base-configuration-dev-test-environment.md) 
    
    Crie uma intranet simplificada em execução nos serviços de infraestrutura do Microsoft Azure. Esta é uma etapa opcional se você quiser compilar uma configuração corporativa simulada.
    
- [Ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md)
    
    Crie uma assinatura de avaliação do Office 365 Enterprise E5, o que pode ser feito de seu computador ou de uma intranet simplificada em execução em serviços de infraestrutura do Azure.
    
- [DirSync para o ambiente de desenvolvimento/teste do Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Instale e configure o Azure AD Connect para a sincronização de diretório com a sincronização de senha. Esta é uma etapa opcional se você quiser compilar uma configuração corporativa simulada.
    
Para seu ambiente de desenvolvimento/teste do Office 365, use estes artigos para demonstrar os recursos corporativos do Office 365:
  
- [Autenticação multifator para o ambiente de desenvolvimento/teste do Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configure e teste a autenticação secundária para uma conta em sua assinatura do Office 365 usando uma mensagem de texto enviada ao seu smartphone.
    
- [Identidade federada para seu ambiente de desenvolvimento/teste do Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configure e demonstre a autenticação federada com as contas de um domínio do Windows Server Active Directory.
    
- [Cloud App Security para o ambiente de desenvolvimento/teste do Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Configure e demonstre a Segurança no Aplicativo na Nuvem do Office 365, que permite a criação de políticas que monitoram e informam sobre atividades suspeitas em sua assinatura do Office 365.
    
- [Proteção Avançada contra Ameaças para seu ambiente de desenvolvimento/teste do Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configure e demonstre a Proteção Avançada contra Ameaças, que é um recurso da Proteção do Exchange Online (EOP) que ajuda a evitar malware em emails.
    
- [Descoberta Eletrônica Avançada para o seu ambiente de desenvolvimento/teste do Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Adicione dados de exemplo e demonstre a Descoberta Eletrônica Avançada, que permite que você localize e analise rapidamente os dados armazenados no Office 365, incluindo emails e documentos.
    
- [Proteção de arquivos confidenciais no ambiente de desenvolvimento/teste do Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Demonstre como você pode usar o Gerenciamento de Direitos de Informação do Office 365 para proteger os dados em documentos confidenciais, mesmo quando são postados acidentalmente nas pastas de documento erradas.
    
- [Classificação de dados e rotulagem no ambiente de desenvolvimento/teste do Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Demonstre como o cliente da Proteção de Informações do Azure (AIP) pode ser usado para classificar os documentos com vários níveis de segurança.
    
- [Site de equipe do SharePoint Online isolado no seu ambiente de desenvolvimento/teste](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Demonstre como criar um site de equipe do SharePoint Online isolado do restante da organização para recursos sensíveis ou altamente confidenciais.
    
## <a name="the-microsoft-365-enterprise-test-environment"></a>Ambiente de teste do Microsoft 365 Enterprise

Crie um ambiente de teste para o [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) com [estes artigos](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).
 
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365

Adicione uma assinatura de avaliação do Dynamics 365 e teste os recursos e cenários integrados do Office 365 e do Dynamics 365 com estes artigos:
  
- [Office 365 e o ambiente de desenvolvimento/teste do Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
    Adicione uma assinatura de avaliação do Dynamics 365 e as licenças e as permissões do Dynamics 365 às suas contas de usuário.
    
- [Integração com o Exchange Online para seu ambiente de desenvolvimento/teste do Office 365 e do Dynamics 365](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    Configure e demonstre como o Office 365 e o Dynamics 365 funcionam juntos em caixas de correio do Exchange Online.
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>Ambiente de desenvolvimento/teste do One Microsoft Cloud

Crie um ambiente de desenvolvimento/teste que inclua todas as ofertas de nuvem da Microsoft: Office 365, Azure, EMS e Dynamics 365. Consulte o [ambiente de desenvolvimento/teste da One Microsoft Cloud](the-one-microsoft-cloud-dev-test-environment.md) para obter instruções passo a passo.
  
## <a name="simulated-cross-premises-devtest-environments"></a>Ambientes simulados de desenvolvimento/teste entre instalações

Você pode criar um ambiente de desenvolvimento/teste entre instalações, o que inclui uma rede virtual do Azure e uma rede local simulada, com estes artigos:
  
- [Rede virtual entre locais simulada no Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Crie uma intranet simulada conectada a uma rede virtual do Azure em uma configuração de nuvem híbrida.
    
- [Intranet do SharePoint Server 2016 no ambiente de desenvolvimento/teste do Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Crie um farm do SharePoint Server 2016 com um único servidor na rede virtual do Azure e teste a conectividade e administração da rede local simulada.
    
## <a name="additional-cloud-based-devtest-environments"></a>Ambientes adicionais de desenvolvimento/teste baseados em nuvem

Aqui estão ambientes adicionais de desenvolvimento/teste baseados em nuvem que você pode criar nos serviços de infraestrutura do Azure:
  
- [Ambiente de desenvolvimento/teste do SharePoint Server 2016 no Azure](https://technet.microsoft.com/library/mt723354.aspx)
    
    Crie um farm do SharePoint Server 2016 com um único servidor nos serviços de infraestrutura do Azure.
    
- [Ambiente de desenvolvimento/teste do Exchange 2016 no Azure](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    Crie um único servidor do Exchange 2016 nos serviços de infraestrutura do Azure.
    
- [Ambientes de desenvolvimento/teste do SharePoint Server 2013 no Azure](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    Crie farms do SharePoint Server 2013 básicos e de alta disponibilidade nos serviços de infraestrutura do Azure.
    
## <a name="see-also"></a>Confira também

[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Recursos de arquitetura de TI da Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Modelos de arquitetura para SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluções híbridas](hybrid-solutions.md)


