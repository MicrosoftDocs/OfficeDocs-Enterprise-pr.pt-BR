---
title: Guia do laboratório de teste configure um laboratório de teste do Exchange, Lync e SharePoint integrado
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
f1.keywords:
- NOCSH
description: 'Resumo: saiba como criar um laboratório de teste integrado que contenha um servidor que executa o Exchange Server 2013, um servidor que executa o Lync Server 2013 e um servidor que executa o SharePoint Server 2013.'
ms.openlocfilehash: 6041f47520f7a02efe08d05835ca0f15dfd6633a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841098"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="9a98f-103">Guia do laboratório de teste: configurar um laboratório de teste do Exchange, Lync e SharePoint integrado</span><span class="sxs-lookup"><span data-stu-id="9a98f-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="9a98f-104">**Resumo:** Saiba como criar um laboratório de teste integrado que contenha um servidor que executa o Exchange Server 2013, um servidor que executa o Lync Server 2013 e um servidor que executa o SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="9a98f-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="9a98f-105">**Assista ao vídeo visão geral do guia do laboratório de teste do Exchange, Lync e SharePoint**</span><span class="sxs-lookup"><span data-stu-id="9a98f-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="9a98f-106">O laboratório de teste resultante dessa configuração, que inclui a autenticação de servidor para servidor entre todos os três tipos de servidores, pode ser usado para criar e demonstrar cenários e soluções de vários produtos que usam um servidor que executa o Exchange Server 2013, um servidor que executa o Lync Server 2013 e um servidor que executa o SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="9a98f-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="9a98f-107">Este documento contém instruções para:</span><span class="sxs-lookup"><span data-stu-id="9a98f-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="9a98f-108">Configurar o laboratório de teste de configuração básica do Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="9a98f-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="9a98f-109">Instalando e configurando um novo servidor com o nome SQL1.</span><span class="sxs-lookup"><span data-stu-id="9a98f-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="9a98f-110">Instalando o SQL Server 2012 no servidor do SQL1.</span><span class="sxs-lookup"><span data-stu-id="9a98f-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="9a98f-111">Instalação e configuração de um novo computador cliente chamado CLIENT2.</span><span class="sxs-lookup"><span data-stu-id="9a98f-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="9a98f-112">Instalando e Configurando o Exchange Server 2013 no EX1.</span><span class="sxs-lookup"><span data-stu-id="9a98f-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="9a98f-113">Instalando e configurando um novo servidor chamado LYNC1.</span><span class="sxs-lookup"><span data-stu-id="9a98f-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="9a98f-114">Instalando o Lync Server 2013 Standard Edition no LYNC1.</span><span class="sxs-lookup"><span data-stu-id="9a98f-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="9a98f-115">Instalando o SharePoint Server 2013 no SP1.</span><span class="sxs-lookup"><span data-stu-id="9a98f-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="9a98f-116">Configurando a integração entre o EX1, o LYNC1 e o SP1.</span><span class="sxs-lookup"><span data-stu-id="9a98f-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="9a98f-117">Para obter informações sobre como configurar esse laboratório de teste no Hyper-V, consulte [hospedagem do laboratório de teste do Exchange, Lync e SharePoint integrado com o Windows Server 2012 Hyper-v](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="9a98f-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="9a98f-118">Como baixar o guia do laboratório de teste</span><span class="sxs-lookup"><span data-stu-id="9a98f-118">Download the test lab guide</span></span>

<span data-ttu-id="9a98f-119">[Guia do laboratório de teste: configurar um laboratório de teste do Exchange, Lync e SharePoint integrado](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="9a98f-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9a98f-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a98f-120">See Also</span></span>

[<span data-ttu-id="9a98f-121">Guias de laboratório de teste</span><span class="sxs-lookup"><span data-stu-id="9a98f-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




