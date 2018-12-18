---
title: Suporte a IPv6 nos serviços do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Resumo: Descreve o suporte a IPv6 nos componentes do Microsoft Office 365 e no ofertas governamentais do Office 365.'
ms.openlocfilehash: 75ed1c8ffe96ed1b09aa8802e11ae195ad60a4f2
ms.sourcegitcommit: d165aef59fe9a9ef538e6756fb014909a7cf975b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2018
ms.locfileid: "27294455"
---
# <a name="ipv6-support-in-office-365-services"></a>Suporte a IPv6 nos serviços do Office 365

 **Resumo**: descreve o suporte a IPv6 nos componentes do Microsoft Office 365 e no ofertas governamentais do Office 365.
  
O Office 365 oferece suporte a IPv6 e IPv4; No entanto, nem todos os recursos do Office 365 são totalmente habilitados com IPv6. Isso significa que você deve usar o IPv4 e IPv6 para se conectar ao Office 365. Se você está filtrando o tráfego de saída para o Office 365, a lista completa dos endereços IPv6 que são suportados pelo Office 365 pode ser encontrada no artigo [URLs do Office 365 e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744). Depois de sua rede estiver configurada e os endereços IPv6 adequados são permitidos, você pode baixar o [plano de teste de IPv6 do Office 365](https://go.microsoft.com/fwlink/?LinkId=293447) do Microsoft Download Center.
  
||
|:-----|
| Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Suporte a IPv6 no serviço de assinatura do Office 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online e IPv6

Se o programa que você usa para se conectar ao Exchange Online oferece suporte a IPv6, ele usará IPv6 por padrão em redes com e sem fio. Se você deseja controlar as comunicações para o Exchange Online, use os intervalos de endereços IP no [Office 365 URLs e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online e IPv6

 **Office 365 Government G1/G3/G4/K1** Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele tentará usar IPv6 por padrão.
  
 **Nuvem pública de multilocatário** Microsoft permite que o IPv6 Online do SharePoint em sua solicitação. Você precisará fornecer que o CIDR representado endereços IP para a infra-estrutura DNS da sua organização. Tenha em mente que esse infraestrutura DNS não pode ser compartilhada por outras empresas para IPv6 estar habilitado para seu locatário. Depois que o IPv6 está ativado, se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele usa IPv6 por padrão.
  
Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele usará IPv6 por padrão em redes com e sem fio. Se você deseja controlar as comunicações para o SharePoint Online, use os intervalos de endereços IP no [Office 365 URLs e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
 **Office 365 Government G1/G3/G4/K1** Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele tentará usar IPv6 por padrão.
  
### <a name="skype-for-business-and-ipv6"></a>Skype para IPv6 e de negócios

Esteja ciente de IPv6 não é suportado no Skype para negócios e não pode ser habilitado.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection e IPv6

Exchange Online Protection (EOP) oferece suporte a IPv6, se a transmissão ocorre via protocolo de segurança de camada de transporte. Para o intervalo EOP, use [URLs do Office 365 e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744).
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Suporte a IPv6 para ofertas governamentais do Office 365

Suporte de IPv6 para ofertas governamentais do Office 365 está em conformidade com o Office de gerenciamento e Memorando de orçamento (orientações) para gerentes de informações de diretor de agências e departamentos executivo, bem como o Federal governamentais adoção de protocolo IP versão 6 (IPv6 ) memorando. [Microsoft Office 365 para agências governamentais](https://go.microsoft.com/fwlink/p/?LinkId=325414) é um serviço de multilocatário que armazena nos dados do governo em uma nuvem de comunidade segregada. Como outras ofertas do Office 365, ele fornece serviços de produtividade e colaboração, incluindo o Exchange Online, Skype para negócios, SharePoint Online e Office Professional Plus. As ofertas de governo do Microsoft Office 365 se aplicam somente para 2013 e posterior. Para obter mais informações sobre as ofertas governamentais do Office 365, consulte [anunciando o Office 365 para agências governamentais: nuvem de comunidade governamental uma conosco](https://go.microsoft.com/fwlink/p/?LinkId=325414). O tráfego de internacional no alerta regulamentos (ITAR) é um conjunto de regulamentos do governo americano que controlam a exportação e importação de artigos relacionados à defesa e serviços na [Lista de Munições Estados Unidos (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 para empresas fornece serviços de hospedagem dedicados para soluções de produtividade da Microsoft que suportam a segurança, privacidade e requisitos de conformidade a normas para nós agências federais exigir Federal Information Security Certificação Management (FISMA) e as entidades comerciais está sujeito a ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Aspectos a serem considerados ao usar o IPv6 e o Office 365

Recomendamos que você não desativar o IPv6. Para obter mais informações, consulte [IPv6 para Microsoft Windows: perguntas frequentes](https://go.microsoft.com/fwlink/p/?LinkId=325418). Para determinar quais versões IP que estão sendo usados em sua rede, considere o seguinte:
  
- Se a exibição do comando IPConfig no prompt de comando contiver linhas com o nome "Endereço IPv6" ou "Endereço IPv6 temporário", você tem IPv6 em seu ambiente.

- Se todos os endereços IPv6 começarem com "fe80" e corresponderem às linhas chamadas "Endereço de IPv6 Link Local", você não tem IPv6 em seu ambiente.

Essas considerações podem ser aplicadas à sua rede:
  
- O serviço de assinatura pública não oferece suporte a compras com cartão de crédito por IPv6. Isso não se aplica à Government Community Cloud (GCC) porque os governos tem o licenciamento Contrato Enterprise (EA).

- O IPv6 não oferece suporte a alguns cenários dos Serviços de Gerenciamento de Direitos (RMS).

- IPv6 não oferece suporte para BlackBerry® Enterprise Server (BES) porque o BlackBerry não oferece suporte a IPv6.

- Se você usar os serviços de Federação do Active Directory (AD FS) com o Office 365, anuncie seu ponto de extremidade de rede do AD FS para o Office 365 usando IPv6 não é suportado. Você não deve incluir registros AAAA na entrada do AD FS DNS ao usar o Exchange Online. 

Aqui está um link curto que você pode usar para voltar: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>Confira também

[Papel de posição de tecnologia da Microsoft](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[V6 e TCP/IP v4](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[Guia de sobrevivência do IPv6](https://go.microsoft.com/fwlink/p/?LinkID=237480)
