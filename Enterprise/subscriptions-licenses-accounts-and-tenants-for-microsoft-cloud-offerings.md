---
title: Inscrições, licenças, contas e inquilinos para as ofertas de nuvem da Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: 'Resumo: Compreenda os relacionamentos de organizações, inscrições, licenças, contas de usuário e inquilinos nas ofertas de nuvem da Microsoft.'
ms.openlocfilehash: ff4854bc66f9a500715bbcd2da696b9a4519aa82
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Inscrições, licenças, contas e inquilinos para as ofertas de nuvem da Microsoft

 **Resumo:** Compreenda as relações entre organizações, inscrições, licenças, contas de usuário e inquilinos nas ofertas de nuvem da Microsoft.
  
A Microsoft fornece uma hierarquia de organizações, inscrições, licenças e contas de usuário para uso consistente de identidades e cobrança nas suas ofertas de nuvem:
  
- Microsoft Office 365
    
    Consulte [preços e planos de negócios](https://products.office.com/business/compare-office-365-for-business-plans) para obter mais informações.
    
- Microsoft Azure
    
    Para obter mais informações, consulte [preços do Azure](https://azure.microsoft.com/pricing/) .
    
- Microsoft Intune e a mobilidade corporativos + segurança (EMS)
    
    Para obter mais informações, consulte [Intune preços](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) .
    
- Microsoft Dynamics 365
    
    Para obter mais informações, consulte [Dynamics 365 preços](https://dynamics.microsoft.com/) .
    
## <a name="elements-of-the-hierarchy"></a>Elementos da hierarquia

Aqui estão os elementos da hierarquia:
  
### <a name="organization"></a>Organização

Uma organização representa uma entidade de negócios que está usando ofertas de nuvem da Microsoft, normalmente identificadas por um nome de domínio (DNS) do sistema de nomes de domínio público por exemplo, contoso.com. A organização é um contêiner para assinaturas.
  
### <a name="subscriptions"></a>Assinaturas

Uma assinatura é um contrato com a Microsoft para usar um ou mais plataformas de nuvem da Microsoft ou serviços, para o qual os encargos acumulam com base em uma taxa de licença de por usuário ou em consumo de recursos na nuvem. Software da Microsoft como um serviço (SaaS)-ofertas baseado em nuvem (Office 365, Intune/EMS e Dynamics 365) cobram por usuário taxas de licença. Plataforma como um serviço (PaaS) e a infraestrutura como uma taxa de ofertas (Azure) de nuvem de serviço (IaaS) com base no consumo de recursos de nuvem da Microsoft.
  
Você também pode usar uma assinatura de avaliação, mas a assinatura expira após um período específico de tempo ou consumo encargos. Você pode converter uma assinatura de avaliação em uma assinatura paga.
  
As organizações podem ter diversas assinaturas para ofertas de nuvem da Microsoft. A Figura 1 mostra um exemplo.
  
**Figura 1: Exemplo de diversas assinaturas para uma organização**

![Um exemplo de organização com várias assinaturas para ofertas de nuvem da Microsoft.](images/Subscriptions/Subscriptions_Fig1.png)

  
A Figura 1 mostra uma única organização que tem diversas assinaturas do Office 365, uma assinatura Intune, uma assinatura do Dynamics 365 e diversas assinaturas Azure.
  
### <a name="licenses"></a>Licenças

Para as ofertas de nuvem da Microsoft SaaS, uma licença permite que uma conta de usuário específica usar os serviços de nuvem que oferece. Você é cobradas a uma taxa mensal fixa como parte de sua assinatura. Os administradores atribuem licenças às contas de usuário individuais na assinatura. No exemplo na Figura 2, a Contoso Corporation tem uma assinatura do Office 365 Enterprise E5 com 100 licenças, que permite a até 100 contas de usuário individuais para usar os serviços e recursos da empresa E5.
  
**Figura 2: Licenças dentro as assinaturas com base em SaaS para uma organização**

![Um exemplo de várias licenças dentro de assinaturas para ofertas de nuvem com base em SaaS da Microsoft.](images/Subscriptions/Subscriptions_Fig2.png)
  
Para serviços de nuvem baseada no Windows Azure PaaS, licenças de software estão integradas aos preços de serviço.
  
Para máquinas virtuais com base no Windows Azure IaaS, licenças adicionais para usar o software ou aplicativo instalado em uma imagem de máquina virtual podem ser necessárias. Algumas imagens de máquina virtual tem licenciado versões do software instalado e o custo está incluído na taxa de por minuto para o servidor. Exemplos são as imagens de máquina virtual para 2014 do SQL Server e SQL Server 2016. 
  
Algumas imagens de máquina virtual tem as versões de avaliação dos aplicativos instalados e precisam de licenças de aplicativos de software adicional para uso além do período de avaliação. Por exemplo, a imagem de máquina virtual de avaliação do SharePoint Server 2016 inclui uma versão de avaliação de 2016 do SharePoint Server pré-instalado. Para continuar usando o SharePoint Server 2016 após a data de expiração de trilha, você deve adquirir uma licença do SharePoint Server 2016 e licenças de cliente da Microsoft. Esses encargos são separados da assinatura do Windows Azure e a taxa de por minuto para executar a máquina virtual ainda se aplica.
  
### <a name="user-accounts"></a>Contas do usuário

Contas de usuário para todas as ofertas de nuvem da Microsoft são armazenadas em um locatário do Azure Active Directory (AD), que contém os grupos e contas de usuário. Um locatário do Azure AD pode ser sincronizado com suas contas do Windows Server AD existentes usando o Windows Azure AD de conectar, um serviço baseado em servidor do Windows. Isso é conhecido como a sincronização de diretório (DirSync).
  
Figura 3 mostra um exemplo de diversas assinaturas de uma organização usando um locatário comuns do Azure AD que contém as contas da organização.
  
**Figura 3: Diversas assinaturas de uma organização que usam o mesmo inquilino do Azure AD.**

![Um exemplo de organização com várias assinaturas usando o mesmo locatário do Microsoft Azure AD.](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a>Locatários

Para ofertas de nuvem SaaS, o inquilino é o local regional que hospeda os servidores fornecendo serviços de nuvem. Por exemplo, a Contoso Corporation escolheu a região europeu para hospedar seus locatários do Office 365, EMS e Dynamics 365 para os trabalhadores de 15.000 em suas matrizes de Paris.
  
Serviços do Azure PaaS e cargas de trabalho baseados na máquina virtual hospedadas no Azure IaaS podem ter locação em qualquer datacenter do Windows Azure no mundo inteiro. Especifique o datacenter do Windows Azure, conhecido como o local, quando você cria o Azure PaaS app ou o serviço ou o elemento de uma carga de trabalho IaaS.
  
Um locatário do Azure AD é uma instância específica do Azure AD contendo as contas e grupos. As assinaturas pagas ou de avaliação do Office 365, Dynamics 365 ou Intune/EMS incluem um livre locatário do Azure AD. Este locatário do Azure AD não inclui outros serviços do Azure e não é o mesmo que uma assinatura paga ou de avaliação do Azure.
  
### <a name="summary-of-the-hierarchy"></a>Resumo da hierarquia

Aqui está um resumo rápido:
  
- Uma organização pode ter diversas assinaturas
    
  - Uma assinatura pode ter várias licenças
    
  - Licenças podem ser atribuídas a contas de usuário individuais
    
  - Contas de usuário são armazenadas em um locatário do Azure AD.
    
Aqui está um exemplo da relação de organizações, inscrições, licenças e contas de usuário:
  
- Uma organização identificada por seu nome de domínio público.
    
  - Uma assinatura do Office 365 Enterprise E3 com licenças de usuário.
    
    Uma assinatura do Office 365 Enterprise E5 com licenças de usuário.
    
    Uma assinatura do EMS com licenças de usuário.
    
    Uma assinatura do Dynamics 365 com licenças de usuário.
    
    Diversas assinaturas Azure.
    
  - Contas de usuário da organização em um locatário comuns do Windows Azure AD.
    
Vários nuvem da Microsoft que oferece assinaturas pode usar o mesmo inquilino do Azure AD que atua como um provedor de identidade comuns. Uma central locatário do Azure AD que contém as contas sincronizadas do seu local Windows Server AD fornece identidade baseada em nuvem como um serviço (IDaaS) para sua organização. Isso é mostrado na Figura 4.
  
**Figura 4: Contas locais sincronizados e IDaaS para uma organização**

![IDaaS de IaaS (identidade como um serviço) para a sua organização.](images/Subscriptions/Subscriptions_Fig4.png)
  
Figura 4 mostra como um locatário comuns do Windows Azure AD é utilizado por SaaS ofertas de nuvem da Microsoft, aplicativos do Windows Azure PaaS e máquinas virtuais no Azure IaaS que utilizam serviços de domínio do Windows Azure AD. Conectar do Azure AD sincroniza a floresta do Windows Server AD local com o locatário do Azure AD.
  
Para obter mais informações sobre a integração de identidade nas ofertas de nuvem da Microsoft, consulte [Identidade de nuvem da Microsoft para arquitetos da empresa](https://aka.ms/cloudarchidentity).
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>A combinação de assinaturas para várias ofertas de nuvem da Microsoft

A tabela a seguir descreve como você pode combinar vários ofertas de nuvem da Microsoft com base em já tiver uma assinatura para um tipo de nuvem, oferecendo (os rótulos descendente a primeira coluna) e adicionando uma assinatura para uma nuvem diferente oferta (passando pela as colunas).
  
||**Office 365**|**Windows Azure**|**Intune/EMS**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Office 365** <br/> |NA  <br/> |Você pode adicionar uma assinatura do Windows Azure para a sua organização do portal do Azure.  <br/> |Você pode adicionar uma assinatura Intune/EMS à sua organização do portal do Office 365.  <br/> |Você pode adicionar uma assinatura do Dynamics 365 à sua organização do portal do Office 365.  <br/> |
|**Windows Azure** <br/> |Você pode adicionar uma assinatura do Office 365 para sua organização.  <br/> |NA  <br/> |Você pode adicionar uma assinatura Intune/EMS à sua organização.  <br/> |Você pode adicionar uma assinatura do Dynamics 365 à sua organização.  <br/> |
|**Intune/EMS** <br/> |Você pode adicionar uma assinatura do Office 365 para sua organização.  <br/> |Você pode adicionar uma assinatura do Windows Azure para a sua organização do portal do Azure.  <br/> |NA  <br/> |Você pode adicionar uma assinatura do Dynamics 365 à sua organização.  <br/> |
|**Dynamics 365** <br/> |Você pode adicionar uma assinatura do Office 365 para sua organização.  <br/> |Você pode adicionar uma assinatura do Windows Azure para a sua organização do portal do Azure.  <br/> |Você pode adicionar uma assinatura Intune/EMS à sua organização.  <br/> |NA  <br/> |
   
Uma maneira fácil de adicionar assinaturas à sua organização para serviços da Microsoft baseada em SaaS é através da Central de administração do Office 365:
  
1. Entrar no portal do Office 365 ([https://portal.office.com](https://portal.office.com)) com seu administrador global da conta e, em seguida, clique em **Admin**.
    
2. Do painel de navegação esquerdo da home page do **Centro de administração** , clique em **faturamento**e, em seguida, **Serviços de compra**.
    
3. Na página **Serviços de compra** , adquira as novas assinaturas.
    
O Centro de administração do Office 365 atribui a organização e o locatário do Azure AD de sua assinatura do Office 365 para novas inscrições para ofertas de SaaS com base em nuvem.
  
Para adicionar uma assinatura do Windows Azure com a mesma organização e o locatário do Azure AD como sua assinatura do Office 365:
  
1. Entrar no portal do Windows Azure ([https://portal.azure.com](https://portal.azure.com)) com sua conta de administrador global do Office 365.
    
2. No painel de navegação esquerdo, clique em **assinaturas**e, em seguida, clique em **Adicionar**.
    
3. Na página **Adicionar assinatura** , selecione uma oferta e concluir as informações de pagamento e o contrato.
    
Se você comprou assinaturas do Windows Azure e o Office 365 separadamente e deseja acessar o locatário do Office 365 Azure AD de sua assinatura do Windows Azure, consulte as instruções em [associar um locatário do Office 365 com uma assinatura do Windows Azure](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).
  
## <a name="see-also"></a>Veja também

[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Modelos de arquitetura para SharePoint, Exchange, Skype for Business e Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluções híbridas](hybrid-solutions.md)
  
[Contas de usuário para a Contoso Corporation, licenças e assinaturas](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



