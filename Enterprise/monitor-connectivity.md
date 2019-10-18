---
title: Monitorar a conectividade do Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Depois de implantar o Office 365, você pode manter a conectividade do Office 365 usando algumas das ferramentas e técnicas abaixo. É importante que você compreenda as diretrizes oficiais do Serviço de Integridade e Continuidade, assim como nossas melhores práticas, para usar o Office 365 em uma rede lenta. Você também precisará obter o aplicativo de administração do Office 365 e marcar nossa Ajuda Administrativa do Office 365 para empresas como favorita.
ms.openlocfilehash: ce307e01a3d7da4a24a06e58d293b9598c684d8f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070047"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="fe8a5-105">Monitorar a conectividade do Office 365</span><span class="sxs-lookup"><span data-stu-id="fe8a5-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="fe8a5-p102">Depois de implantar o Office 365, você pode manter a conectividade do Office 365 usando algumas das ferramentas e técnicas abaixo. É importante que você compreenda as diretrizes oficiais do [Serviço de Integridade e Continuidade](https://technet.microsoft.com/library/office-365-service-health.aspx), assim como nossas [melhores práticas, para usar o Office 365 em uma rede lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Você também precisará obter o [aplicativo de administração do Office 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) e marcar nossa [Ajuda Administrativa do Office 365 para empresas](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791) como favorita.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://technet.microsoft.com/library/office-365-service-health.aspx) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="fe8a5-109">Monitorar a conectividade do Office 365</span><span class="sxs-lookup"><span data-stu-id="fe8a5-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="fe8a5-110">**Obter notificação de novos pontos de extremidade do Office 365**</span><span class="sxs-lookup"><span data-stu-id="fe8a5-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="fe8a5-p103">Se você estiver [Gerenciando pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), convém receber notificações quando publicarmos novos pontos de extremidade, e então você pode assinar nosso feed RSS usando seu leitor de RSS favorito. Veja como [assinar pelo Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416), ou também é possível [receber as atualizações do feed RSS por email](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span><span class="sxs-lookup"><span data-stu-id="fe8a5-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="fe8a5-113">**Usar o System Center para monitorar o Office 365**</span><span class="sxs-lookup"><span data-stu-id="fe8a5-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="fe8a5-p104">Se estiver usando o Microsoft System Center, você pode baixar o [Pacote de Gerenciamento do System Center para Office 365](https://www.microsoft.com/download/details.aspx?id=43708) para começar a monitorar o Office 365 hoje mesmo. Para obter mais orientações, consulte o guia de operações do pacote de gerenciamento ou este post no blog [Monitoramento do Office 365 usando o gerente de operações do System Center](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span><span class="sxs-lookup"><span data-stu-id="fe8a5-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="fe8a5-116">**Monitorar a integridade do Azure ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="fe8a5-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="fe8a5-117">Se você estiver se conectando ao Office 365 usando o Azure ExpressRoute para Office 365, desejará garantir que você está usando tanto o Painel de Integridade de Serviços do Office 365 quanto o Azure [Reduzir o tempo de solução de problemas com a integridade de recursos do Azure](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) </span><span class="sxs-lookup"><span data-stu-id="fe8a5-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="fe8a5-118">**Usar o Azure AD Connect Health com o AD FS**</span><span class="sxs-lookup"><span data-stu-id="fe8a5-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="fe8a5-119">Se você estiver usando AD FS para logon único com o Office 365, convém começar [usando o Azure AD Connect Health para monitorar a infraestrutura de AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span><span class="sxs-lookup"><span data-stu-id="fe8a5-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="fe8a5-120">**Monitorar programaticamente o Office 365**</span><span class="sxs-lookup"><span data-stu-id="fe8a5-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="fe8a5-121">Confira nossa orientação sobre a [API de gerenciamento do Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span><span class="sxs-lookup"><span data-stu-id="fe8a5-121">Refer to our guidance on the [Office 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="fe8a5-122">Aqui está um link curto que você pode usar para voltar: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="fe8a5-122">Here's a short link you can use to come back: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fe8a5-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe8a5-123">See also</span></span>

[<span data-ttu-id="fe8a5-124">Configurar aplicativos e serviços do Office 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="fe8a5-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
<span data-ttu-id="fe8a5-125">[Preparar sua organização para o Office 365 Enterprise](get-your-organization-ready-for-office-365.md)
</span><span class="sxs-lookup"><span data-stu-id="fe8a5-125">[Get your organization ready for Office 365 Enterprise](get-your-organization-ready-for-office-365.md)</span></span>
  
[<span data-ttu-id="fe8a5-126">Planejamento de rede e ajuste de desempenho para Office 365</span><span class="sxs-lookup"><span data-stu-id="fe8a5-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="fe8a5-127">Integração do Office 365 com ambientes locais</span><span class="sxs-lookup"><span data-stu-id="fe8a5-127">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="fe8a5-128">Gerenciar pontos de extremidade do Office 365</span><span class="sxs-lookup"><span data-stu-id="fe8a5-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
