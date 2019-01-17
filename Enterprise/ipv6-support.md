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
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327353"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="5d51a-103">Suporte a IPv6 nos serviços do Office 365</span><span class="sxs-lookup"><span data-stu-id="5d51a-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="5d51a-104">**Resumo**: descreve o suporte a IPv6 nos componentes do Microsoft Office 365 e no ofertas governamentais do Office 365.</span><span class="sxs-lookup"><span data-stu-id="5d51a-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="5d51a-p101">O Office 365 oferece suporte a IPv6 e IPv4; No entanto, nem todos os recursos do Office 365 são totalmente habilitados com IPv6. Isso significa que você deve usar o IPv4 e IPv6 para se conectar ao Office 365. Se você está filtrando o tráfego de saída para o Office 365, a lista completa dos endereços IPv6 que são suportados pelo Office 365 pode ser encontrada no artigo [URLs do Office 365 e intervalos de endereços IP](urls-and-ip-address-ranges.md). Depois de sua rede estiver configurada e os endereços IPv6 adequados são permitidos, você pode baixar o [plano de teste de IPv6 do Office 365](https://go.microsoft.com/fwlink/?LinkId=293447) do Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="5d51a-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="5d51a-109">Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="5d51a-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="5d51a-110">Suporte a IPv6 no serviço de assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="5d51a-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="5d51a-111">Exchange Online e IPv6</span><span class="sxs-lookup"><span data-stu-id="5d51a-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="5d51a-p102">Se o programa que você usa para se conectar ao Exchange Online oferece suporte a IPv6, ele usará IPv6 por padrão em redes com e sem fio. Se você deseja controlar as comunicações para o Exchange Online, use os intervalos de endereços IP no [Office 365 URLs e intervalos de endereços IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="5d51a-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="5d51a-114">SharePoint Online e IPv6</span><span class="sxs-lookup"><span data-stu-id="5d51a-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="5d51a-115">**Office 365 Government G1/G3/G4/K1** Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele tentará usar IPv6 por padrão.</span><span class="sxs-lookup"><span data-stu-id="5d51a-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="5d51a-p103">**Nuvem pública de multilocatário** Microsoft permite que o IPv6 Online do SharePoint em sua solicitação. Você precisará fornecer que o CIDR representado endereços IP para a infra-estrutura DNS da sua organização. Tenha em mente que esse infraestrutura DNS não pode ser compartilhada por outras empresas para IPv6 estar habilitado para seu locatário. Depois que o IPv6 está ativado, se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele usa IPv6 por padrão.</span><span class="sxs-lookup"><span data-stu-id="5d51a-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="5d51a-p104">Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele usará IPv6 por padrão em redes com e sem fio. Se você deseja controlar as comunicações para o SharePoint Online, use os intervalos de endereços IP no [Office 365 URLs e intervalos de endereços IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="5d51a-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="5d51a-122">**Office 365 Government G1/G3/G4/K1** Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele tentará usar IPv6 por padrão.</span><span class="sxs-lookup"><span data-stu-id="5d51a-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="5d51a-123">Skype para IPv6 e de negócios</span><span class="sxs-lookup"><span data-stu-id="5d51a-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="5d51a-124">Esteja ciente de IPv6 não é suportado no Skype para negócios e não pode ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="5d51a-124">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="5d51a-125">Exchange Online Protection e IPv6</span><span class="sxs-lookup"><span data-stu-id="5d51a-125">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="5d51a-p105">Exchange Online Protection (EOP) oferece suporte a IPv6, se a transmissão ocorre via protocolo de segurança de camada de transporte. Para o intervalo EOP, use [URLs do Office 365 e intervalos de endereços IP](urls-and-ip-address-ranges.md).</span><span class="sxs-lookup"><span data-stu-id="5d51a-p105">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="5d51a-128">Suporte a IPv6 para ofertas governamentais do Office 365</span><span class="sxs-lookup"><span data-stu-id="5d51a-128">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="5d51a-p106">Suporte de IPv6 para ofertas governamentais do Office 365 está em conformidade com o Office de gerenciamento e Memorando de orçamento (orientações) para gerentes de informações de diretor de agências e departamentos executivo, bem como o Federal governamentais adoção de protocolo IP versão 6 (IPv6 ) memorando. [Microsoft Office 365 para agências governamentais](https://go.microsoft.com/fwlink/p/?LinkId=325414) é um serviço de multilocatário que armazena nos dados do governo em uma nuvem de comunidade segregada. Como outras ofertas do Office 365, ele fornece serviços de produtividade e colaboração, incluindo o Exchange Online, Skype para negócios, SharePoint Online e Office Professional Plus.</span><span class="sxs-lookup"><span data-stu-id="5d51a-p106">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus.</span></span> 

<span data-ttu-id="5d51a-p107">As ofertas de governo do Microsoft Office 365 se aplicam somente para 2013 e posterior. Para obter mais informações sobre as ofertas governamentais do Office 365, consulte [anunciando o Office 365 para agências governamentais: nuvem de comunidade governamental uma conosco](https://go.microsoft.com/fwlink/p/?LinkId=325414). O tráfego de internacional no alerta regulamentos (ITAR) é um conjunto de regulamentos do governo americano que controlam a exportação e importação de artigos relacionados à defesa e serviços na [Lista de Munições Estados Unidos (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span><span class="sxs-lookup"><span data-stu-id="5d51a-p107">The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="5d51a-135">Microsoft Office 365 para empresas fornece serviços de hospedagem dedicados para soluções de produtividade da Microsoft que suportam a segurança, privacidade e requisitos de conformidade a normas para nós agências federais exigir Federal Information Security Certificação Management (FISMA) e as entidades comerciais está sujeito a ITAR.</span><span class="sxs-lookup"><span data-stu-id="5d51a-135">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="5d51a-136">Aspectos a serem considerados ao usar o IPv6 e o Office 365</span><span class="sxs-lookup"><span data-stu-id="5d51a-136">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="5d51a-p108">Recomendamos que você não desativar o IPv6. Para obter mais informações, consulte este [artigo de orientações](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Para determinar quais versões IP que estão sendo usados em sua rede, considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5d51a-p108">We recommend that you do not disable IPv6. For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="5d51a-140">Se a exibição do comando **IPConfig** no prompt de comando contiver linhas com o nome "Endereço IPv6" ou "Endereço IPv6 temporário", você tem IPv6 em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="5d51a-140">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="5d51a-141">Se todos os endereços IPv6 começarem com "fe80" e corresponderem às linhas chamadas "Endereço de IPv6 Link Local", você não tem IPv6 em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="5d51a-141">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="5d51a-142">Essas considerações podem ser aplicadas à sua rede:</span><span class="sxs-lookup"><span data-stu-id="5d51a-142">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="5d51a-p109">O serviço de assinatura pública não oferece suporte a compras com cartão de crédito por IPv6. Isso não se aplica à Government Community Cloud (GCC) porque os governos tem o licenciamento Contrato Enterprise (EA).</span><span class="sxs-lookup"><span data-stu-id="5d51a-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="5d51a-145">O IPv6 não oferece suporte a alguns cenários dos Serviços de Gerenciamento de Direitos (RMS).</span><span class="sxs-lookup"><span data-stu-id="5d51a-145">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="5d51a-146">IPv6 não oferece suporte para BlackBerry® Enterprise Server (BES) porque o BlackBerry não oferece suporte a IPv6.</span><span class="sxs-lookup"><span data-stu-id="5d51a-146">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="5d51a-p110">Se você usar os serviços de Federação do Active Directory (AD FS) com o Office 365, anuncie seu ponto de extremidade de rede do AD FS para o Office 365 usando IPv6 não é suportado. Você não deve incluir registros AAAA na entrada do AD FS DNS ao usar o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="5d51a-p110">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported. You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="5d51a-149">Aqui está um link curto que você pode usar para voltar: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="5d51a-149">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5d51a-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="5d51a-150">See also</span></span>

<span data-ttu-id="5d51a-151">[Mapa de aprendizado de IPv6](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="5d51a-151">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="5d51a-152">Guia de sobrevivência do IPv6</span><span class="sxs-lookup"><span data-stu-id="5d51a-152">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
