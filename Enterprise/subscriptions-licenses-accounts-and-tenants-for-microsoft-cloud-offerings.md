---
title: Assinaturas, licenças, contas e locatários para ofertas de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Resumo: entenda as relações das organizações, assinaturas, licenças, contas de usuário e locatários para ofertas de nuvem da Microsoft.'
ms.openlocfilehash: 52857196f53a44196c96f60bd70564f5e3221b80
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906248"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Assinaturas, licenças, contas e locatários para ofertas de nuvem da Microsoft

A Microsoft fornece uma hierarquia de organizações, assinaturas, licenças e contas de usuário para o uso consistente de identidades e cobrança para todas as ofertas de nuvem:
  
- Microsoft 365 e Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>Elementos da hierarquia

Aqui estão os elementos da hierarquia:
  
### <a name="organization"></a>Organização

An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.
  
### <a name="subscriptions"></a>Assinaturas

Uma assinatura é um contrato com a Microsoft para usar uma ou mais plataformas ou serviços de nuvem da Microsoft, para as quais as cobranças se acumulam com base em uma taxa de licença por usuário ou no consumo de recursos baseado na nuvem. 

- As ofertas de nuvem baseadas em software (SaaS) da Microsoft (Microsoft 365 e Dynamics 365) cobram taxas de licença por usuário. 
- As ofertas de nuvem de Plataforma como um Serviço (PaaS) e Infraestrutura como um Serviço (IaaS) da Microsoft (Azure) cobram com base no consumo de recursos na nuvem.
 
You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.
  
As organizações podem ter várias assinaturas para ofertas de nuvem da Microsoft. A Figura 1 mostra uma única organização com várias assinaturas do Microsoft 365, uma assinatura do Dynamics 365 e várias assinaturas do Azure.

**Figura 1: Exemplo de várias assinaturas de uma organização**

![Um exemplo de organização com várias assinaturas para ofertas de nuvem da Microsoft.](media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>Licenças

Para as ofertas de nuvem SaaS da Microsoft, uma licença permite que uma conta de usuário específica use os serviços da oferta na nuvem. Você será cobrado com uma taxa mensal fixa como parte da sua assinatura. Os administradores podem atribuir licenças a contas de usuários individuais na assinatura. Para o exemplo na Figura 2, a Contoso Corporation tem uma assinatura do Microsoft 365 E5 com licenças 100, que permite até 100 contas de usuário individuais para usar os recursos e serviços do Microsoft 365 e5.
  
**Figura 2: Licenças em assinaturas SaaS para uma organização**

![Um exemplo de várias licenças em assinaturas para ofertas em nuvem baseadas em SaaS da Microsoft.](media/Subscriptions/Subscriptions-Fig2.png)
  
Para serviços de nuvem baseados em PaaS do Azure, as licenças de software são integradas ao preço do serviço.
  
For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016. 
  
Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.
  
### <a name="user-accounts"></a>Contas de usuário

As contas de usuário para todas as ofertas de nuvem da Microsoft são armazenadas em um locatário do Azure Active Directory (Azure AD), que contém contas de usuários e grupos. Um locatário do Azure AD pode ser sincronizado com as contas de Serviços de Domínio Active Directory (AD DS) existentes usando o Azure AD Connect, um serviço baseado no Windows Server. Isso é conhecido como sincronização de diretório.
  
A Figura 3 mostra um exemplo de várias assinaturas de uma organização usando um locatário comum do Azure AD que contém as contas da organização.
  
**Figura 3: Várias assinaturas de uma organização que usam o mesmo locatário do Azure AD**

![Um exemplo de organização com várias assinaturas, todas usando o mesmo locatário do Microsoft Azure AD.](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Locatários

Para ofertas de nuvem SaaS, o locatário é o local regional que abriga os servidores que fornecem serviços em nuvem. Por exemplo, a Contoso Corporation escolheu a região Européia para hospedar seus locatários do Microsoft 365, EMS e Dynamics 365 para os trabalhadores do 15.000 na sede de Paris.
  
Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.
  
Um locatário do Azure AD é uma instância específica do Azure AD que contém contas e grupos. Assinaturas pagas ou de avaliação do Microsoft 365 ou Dynamics 365 incluem um locatário gratuito do Azure AD. Este locatário do Azure AD não inclui outros serviços do Azure e não é o mesmo que uma assinatura de avaliação ou paga do Azure.
  
### <a name="summary-of-the-hierarchy"></a>Resumo da hierarquia

Veja aqui uma rápida recapitulação:
  
- Uma organização pode ter várias assinaturas
    
  - Uma assinatura pode ter várias licenças
    
  - As licenças podem ser atribuídas a contas de usuários individuais
    
  - As contas de usuário são armazenadas em um locatário do Azure AD
    
Aqui está um exemplo da relação das organizações, assinaturas, licenças e contas de usuários:
  
- Uma organização identificada pelo nome de domínio público.
    
  - Uma assinatura do Microsoft 365 E3 com licenças de usuário.
    
    Uma assinatura do Microsoft 365 E5 com licenças de usuário.
    
    Uma assinatura Dynamics 365 com licenças de usuário.
    
    Várias assinaturas do Azure.
    
  - Contas de usuários da organização em um locatário comum do Azure AD.
    
Várias assinaturas de oferta do Microsoft Cloud podem usar o mesmo locatário do Azure AD que atua como um provedor de identidade comum. Um locatário do Azure AD central que contém as contas sincronizadas de seu AD DS no local fornece identidade baseada em nuvem como um serviço (IDaaS) para sua organização. 
  
**Figura 4: IDaaS e contas locais sincronizadas para uma organização**

![IDaaS ou Identidade como um serviço (IaaS) para a sua organização.](media/Subscriptions/Subscriptions-Fig4.png)
  
Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Combinar as assinaturas de várias ofertas de nuvem da Microsoft

A tabela a seguir descreve como você pode combinar várias ofertas da nuvem da Microsoft com base em assinaturas que você já tenha para um tipo de oferta da nuvem (os rótulos que estão na primeira coluna) e como adicionar uma assinatura em uma oferta diferente da nuvem (que está em várias colunas).
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |N/D  <br/> |Adicione uma assinatura do Azure na sua organização no portal do Azure.  <br/> |Adicionar uma assinatura do Dynamics 365 para sua organização no centro de administração do Microsoft 365.  <br/> |
|**Azure** <br/> |Você adiciona uma assinatura do Microsoft 365 à sua organização.  <br/> |N/D  <br/> |Adicione uma assinatura do Dynamics 365 para sua organização.  <br/> |
|**Dynamics 365** <br/> |Você adiciona uma assinatura do Microsoft 365 à sua organização.  <br/> |Adicione uma assinatura do Azure para sua organização no portal do Azure.  <br/> |NA  <br/> |
   
Uma maneira fácil de adicionar assinaturas de serviços baseados em SaaS da Microsoft para sua organização é por meio do centro de administração:
  
1. Entre no centro de administração do Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) com sua conta de administrador global.
    
2. Na navegação à esquerda da página inicial do **centro de administração **, clique em **Cobrança**e depois em **Serviços de compra**.
    
3. Na página **Serviços de compra**, compre as novas assinaturas.
    
O centro de administração atribui a organização e o locatário do Azure AD da sua assinatura do Microsoft 365 às novas assinaturas para ofertas de nuvem baseadas em SaaS.
  
Para adicionar uma assinatura do Azure com a mesma organização e o locatário do Azure AD como sua assinatura do Microsoft 365:
  
1. Entre no portal do Azure ( [https://portal.azure.com](https://portal.azure.com) ) com sua conta de administrador global do Microsoft 365.
    
2. Na navegação à esquerda, clique em **Assinaturas** e depois em **Adicionar**.
    
3. Na página **Adicionar assinatura**, selecione uma oferta e complete as informações de pagamento e o contrato.
    
Se você comprou as assinaturas do Azure e do Microsoft 365 separadamente e deseja acessar o locatário do Microsoft 365 Azure AD da sua assinatura do Azure, Confira as instruções em [Adicionar uma assinatura do Azure existente ao seu locatário do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>Confira também

[Recursos de arquitetura de TI do Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)
  
[Modelos de arquitetura para SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluções híbridas](hybrid-solutions.md)

## <a name="next-step"></a>Próxima etapa

[Avaliando a conectividade de rede do Microsoft 365](assessing-network-connectivity.md)
  
