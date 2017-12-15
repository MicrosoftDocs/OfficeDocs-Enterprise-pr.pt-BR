---
title: "Testar o guia de laboratório configurar do Exchange integrado, laboratório de teste do Lync e o SharePoint"
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: "Resumo: Saiba como criar um laboratório de teste integrado que contém um servidor que executa o Exchange Server 2013, um servidor que executa o Lync Server 2013 e um servidor que executa o SharePoint Server 2013."
ms.openlocfilehash: 6fc3bc05db0d28bc4de2be77671ccf5e8fc55926
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="4d200-103">Guia de laboratório de teste: Configurar um laboratório de teste integrado do Exchange, Lync e SharePoint</span><span class="sxs-lookup"><span data-stu-id="4d200-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="4d200-104">**Resumo:** Saiba como criar um laboratório de teste integrado que contém um servidor que executa o Exchange Server 2013, um servidor que executa o Lync Server 2013 e um servidor que executa o SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="4d200-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="4d200-105">Laboratório de teste que é resultado nesta configuração, que inclui a autenticação de servidor-para-servidor entre todos os três tipos de servidores, pode ser usado para criar o e demonstrar o produtos vários cenários e soluções que usam um servidor que executa o Exchange Server 2013, um servidor que executa o Lync Server 2013 e um servidor que executa o SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="4d200-105">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="4d200-106">Este documento contém instruções para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4d200-106">This document contains instructions for the following:</span></span>
  
1. <span data-ttu-id="4d200-107">Configurando o laboratório de teste de configuração básica do Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="4d200-107">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="4d200-108">Instalando e configurando um novo servidor com o nome SQL1.</span><span class="sxs-lookup"><span data-stu-id="4d200-108">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="4d200-109">Instalando o SQL Server 2012 no servidor SQL1.</span><span class="sxs-lookup"><span data-stu-id="4d200-109">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="4d200-110">Instalando e configurando um novo computador cliente denominado CLIENT2.</span><span class="sxs-lookup"><span data-stu-id="4d200-110">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="4d200-111">Instalando e configurando o Exchange Server 2013 em EX1.</span><span class="sxs-lookup"><span data-stu-id="4d200-111">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="4d200-112">Instalando e configurando um novo servidor denominado LYNC1.</span><span class="sxs-lookup"><span data-stu-id="4d200-112">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="4d200-113">Instalando o Lync Server 2013 Standard Edition no LYNC1.</span><span class="sxs-lookup"><span data-stu-id="4d200-113">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="4d200-114">Instalando o SharePoint Server 2013 no SP1.</span><span class="sxs-lookup"><span data-stu-id="4d200-114">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="4d200-115">Configurando a integração entre EX1, LYNC1 e SP1.</span><span class="sxs-lookup"><span data-stu-id="4d200-115">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="4d200-116">**Assista a integrado do Exchange, Lync e vídeo de visão geral do guia de laboratório de teste do SharePoint**</span><span class="sxs-lookup"><span data-stu-id="4d200-116">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

![Ícone de vídeo (botão reproduzir)](images/mod_icon_video_M.png)
  
<span data-ttu-id="4d200-118">Para obter informações sobre como configurar este laboratório de teste no Hyper-V, consulte [hospedando o Exchange integrado, Lync e o SharePoint com o Windows Server 2012 Hyper-V do laboratório de teste](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="4d200-118">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="4d200-119">Como baixar o guia do laboratório de teste</span><span class="sxs-lookup"><span data-stu-id="4d200-119">Download the test lab guide</span></span>

<span data-ttu-id="4d200-120">[Guia de laboratório de teste: configurar um Exchange integrado, Lync e do laboratório de teste do SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="4d200-120">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4d200-121">See Also</span><span class="sxs-lookup"><span data-stu-id="4d200-121">See Also</span></span>

[<span data-ttu-id="4d200-122">Guias de laboratório de teste</span><span class="sxs-lookup"><span data-stu-id="4d200-122">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




