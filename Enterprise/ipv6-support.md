---
title: Suporte a IPv6 nos serviços do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/12/2017
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
ms.openlocfilehash: 74752988803728ef4c319e368150b90f7e5d2599
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223123"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="8ed20-103">Suporte a IPv6 nos serviços do Office 365</span><span class="sxs-lookup"><span data-stu-id="8ed20-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="8ed20-104">**Resumo**: descreve o suporte a IPv6 nos componentes do Microsoft Office 365 e no ofertas governamentais do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8ed20-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="8ed20-p101">O Office 365 oferece suporte a IPv6 e IPv4; No entanto, nem todos os recursos do Office 365 são totalmente habilitados com IPv6. Isso significa que você deve usar o IPv4 e IPv6 para se conectar ao Office 365. Se você está filtrando o tráfego de saída para o Office 365, a lista completa dos endereços IPv6 que são suportados pelo Office 365 pode ser encontrada no artigo [URLs do Office 365 e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744). Depois de sua rede estiver configurada e os endereços IPv6 adequados são permitidos, você pode baixar o [plano de teste de IPv6 do Office 365](https://go.microsoft.com/fwlink/?LinkId=293447) do Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="8ed20-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="8ed20-109">Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="8ed20-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="8ed20-110">Suporte a IPv6 no serviço de assinatura do Office 365</span><span class="sxs-lookup"><span data-stu-id="8ed20-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="8ed20-111">Exchange Online e IPv6</span><span class="sxs-lookup"><span data-stu-id="8ed20-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="8ed20-p102">Se o programa que você usa para se conectar ao Exchange Online oferece suporte a IPv6, ele usará IPv6 por padrão em redes com e sem fio. Se você deseja controlar as comunicações para o Exchange Online, use os intervalos de endereços IP no [Office 365 URLs e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="8ed20-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="8ed20-114">SharePoint Online e IPv6</span><span class="sxs-lookup"><span data-stu-id="8ed20-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="8ed20-115">**Office 365 Government G1/G3/G4/K1** Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele tentará usar IPv6 por padrão.</span><span class="sxs-lookup"><span data-stu-id="8ed20-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="8ed20-p103">**Nuvem pública de multilocatário** Microsoft permite que o IPv6 Online do SharePoint em sua solicitação. Você precisará fornecer que o CIDR representado endereços IP para a infra-estrutura DNS da sua organização. Tenha em mente que esse infraestrutura DNS não pode ser compartilhada por outras empresas para IPv6 estar habilitado para seu locatário. Depois que o IPv6 está ativado, se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele usa IPv6 por padrão.</span><span class="sxs-lookup"><span data-stu-id="8ed20-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="8ed20-p104">Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele usará IPv6 por padrão em redes com e sem fio. Se você deseja controlar as comunicações para o SharePoint Online, use os intervalos de endereços IP no [Office 365 URLs e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="8ed20-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
 <span data-ttu-id="8ed20-122">**Office 365 Government G1/G3/G4/K1** Se o programa que você usa para se conectar ao SharePoint Online suporta IPv6, ele tentará usar IPv6 por padrão.</span><span class="sxs-lookup"><span data-stu-id="8ed20-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="8ed20-123">Skype para IPv6 e de negócios</span><span class="sxs-lookup"><span data-stu-id="8ed20-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="8ed20-p105">Microsoft habilitará o IPv6 para Skype para negócios em sua solicitação na nuvem pública multilocatário e no Office 365 Government G1/G3/G4/K1 assinaturas. Depois que ele está ativado, se o programa que você usa para se conectar ao Skype para a empresa oferece suporte a IPv6, ele usará IPv6 por padrão. Se você deseja controlar as comunicações para Skype para os negócios, use os intervalos de endereços IP no [Office 365 URLs e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="8ed20-p105">Microsoft will enable IPv6 for Skype for Business at your request in the public multi-tenant cloud and in Office 365 Government G1/G3/G4/K1 subscriptions. After it's enabled, if the program that you use to connect to Skype for Business supports IPv6, it will use IPv6 by default. If you want to control communications to Skype for Business, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
<span data-ttu-id="8ed20-127">Esteja ciente de IPv6 não está disponível em todas as regiões e a Microsoft não poderá ativá-lo para seu locatário neste momento.</span><span class="sxs-lookup"><span data-stu-id="8ed20-127">Please be aware IPv6 is not available in all regions and Microsoft may not be able to activate it for your Tenant at this time.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="8ed20-128">Exchange Online Protection e IPv6</span><span class="sxs-lookup"><span data-stu-id="8ed20-128">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="8ed20-p106">Exchange Online Protection (EOP) oferece suporte a IPv6, se a transmissão ocorre via protocolo de segurança de camada de transporte. Para o intervalo EOP, use [URLs do Office 365 e intervalos de endereços IP](https://go.microsoft.com/fwlink/?LinkId=293744).</span><span class="sxs-lookup"><span data-stu-id="8ed20-p106">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="8ed20-131">Suporte a IPv6 para ofertas governamentais do Office 365</span><span class="sxs-lookup"><span data-stu-id="8ed20-131">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="8ed20-p107">Suporte de IPv6 para ofertas governamentais do Office 365 está em conformidade com o Office de gerenciamento e Memorando de orçamento (orientações) para gerentes de informações de diretor de agências e departamentos executivo, bem como o Federal governamentais adoção de protocolo IP versão 6 (IPv6 ) memorando. [Microsoft Office 365 para agências governamentais](https://go.microsoft.com/fwlink/p/?LinkId=325414) é um serviço de multilocatário que armazena nos dados do governo em uma nuvem de comunidade segregada. Como outras ofertas do Office 365, ele fornece serviços de produtividade e colaboração, incluindo o Exchange Online, Skype para negócios, SharePoint Online e Office Professional Plus. As ofertas de governo do Microsoft Office 365 se aplicam somente para 2013 e posterior. Para obter mais informações sobre as ofertas governamentais do Office 365, consulte [anunciando o Office 365 para agências governamentais: nuvem de comunidade governamental uma conosco](https://go.microsoft.com/fwlink/p/?LinkId=325414). O tráfego de internacional no alerta regulamentos (ITAR) é um conjunto de regulamentos do governo americano que controlam a exportação e importação de artigos relacionados à defesa e serviços na [Lista de Munições Estados Unidos (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 para empresas fornece serviços de hospedagem dedicados para soluções de produtividade da Microsoft que suportam a segurança, privacidade e requisitos de conformidade a normas para nós agências federais exigir Federal Information Security Certificação Management (FISMA) e as entidades comerciais está sujeito a ITAR.</span><span class="sxs-lookup"><span data-stu-id="8ed20-p107">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus. The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="8ed20-139">Aspectos a serem considerados ao usar o IPv6 e o Office 365</span><span class="sxs-lookup"><span data-stu-id="8ed20-139">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="8ed20-p108">Recomendamos que você não desativar o IPv6. Para obter mais informações, consulte [IPv6 para Microsoft Windows: perguntas frequentes](https://go.microsoft.com/fwlink/p/?LinkId=325418). Para determinar quais versões IP que estão sendo usados em sua rede, considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8ed20-p108">We recommend that you do not disable IPv6. For more information, see [IPv6 for Microsoft Windows: Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?LinkId=325418). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="8ed20-143">Se a exibição do comando IPConfig no prompt de comando contiver linhas com o nome "Endereço IPv6" ou "Endereço IPv6 temporário", você tem IPv6 em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="8ed20-143">If the display of the IPConfig command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="8ed20-144">Se todos os endereços IPv6 começarem com "fe80" e corresponderem às linhas chamadas "Endereço de IPv6 Link Local", você não tem IPv6 em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="8ed20-144">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="8ed20-145">Essas considerações podem ser aplicadas à sua rede:</span><span class="sxs-lookup"><span data-stu-id="8ed20-145">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="8ed20-p109">O serviço de assinatura pública não oferece suporte a compras com cartão de crédito por IPv6. Isso não se aplica à Government Community Cloud (GCC) porque os governos tem o licenciamento Contrato Enterprise (EA).</span><span class="sxs-lookup"><span data-stu-id="8ed20-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="8ed20-148">O IPv6 não oferece suporte a alguns cenários dos Serviços de Gerenciamento de Direitos (RMS).</span><span class="sxs-lookup"><span data-stu-id="8ed20-148">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="8ed20-149">IPv6 não oferece suporte para BlackBerry® Enterprise Server (BES) porque o BlackBerry não oferece suporte a IPv6.</span><span class="sxs-lookup"><span data-stu-id="8ed20-149">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

<span data-ttu-id="8ed20-150">Aqui está um link curto que você pode usar para voltar:[https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="8ed20-150">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8ed20-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="8ed20-151">See also</span></span>

[<span data-ttu-id="8ed20-152">Papel de posição de tecnologia da Microsoft</span><span class="sxs-lookup"><span data-stu-id="8ed20-152">Microsoft Technology Position Paper</span></span>](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[<span data-ttu-id="8ed20-153">V6 e TCP/IP v4</span><span class="sxs-lookup"><span data-stu-id="8ed20-153">TCP/IP v4 and v6</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[<span data-ttu-id="8ed20-154">Guia de sobrevivência do IPv6</span><span class="sxs-lookup"><span data-stu-id="8ed20-154">IPv6 Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=237480)
