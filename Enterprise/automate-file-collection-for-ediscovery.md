---
title: Automatizar a coleta de arquivos para descoberta eletrônica
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Resumo: saiba como automatizar a coleta de arquivos dos computadores dos usuários para descoberta eletrônica.'
ms.openlocfilehash: ccea04f4573a16750f588295fca5621d5abd8498
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077714"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="f4a42-103">Automatizar a coleta de arquivos para descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="f4a42-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="f4a42-104">**Resumo:** Saiba como automatizar a coleta de arquivos dos computadores dos usuários para descoberta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="f4a42-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="f4a42-105">Todas as empresas enfrentam o potencial de processos judiciais ou outros tipos de ações legais.</span><span class="sxs-lookup"><span data-stu-id="f4a42-105">All companies face the potential of lawsuits or other types of legal action.</span></span> <span data-ttu-id="f4a42-106">Embora os departamentos jurídicos trabalhem para reduzir essa exposição, o litígio é um fato da vida útil da empresa.</span><span class="sxs-lookup"><span data-stu-id="f4a42-106">While legal departments work to reduce that exposure, litigation is a fact of business life.</span></span> <span data-ttu-id="f4a42-107">Quando uma empresa enfrenta ações legais, elas são necessárias, por meio do processo de descoberta legal, para fornecer todo o material documentário relevante para o tribunal e para o advogado oposto.</span><span class="sxs-lookup"><span data-stu-id="f4a42-107">When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="f4a42-108">a descoberta eletrônica é o processo pelo qual as empresas fazem inventário, pesquisa, identificar, preservar, filtrar e disponibilizar os materiais documentários relevantes que existem em formato eletrônico.</span><span class="sxs-lookup"><span data-stu-id="f4a42-108">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form.</span></span> <span data-ttu-id="f4a42-109">O SharePoint 2013, o Exchange Server 2013, o Lync Server 2013, o SharePoint Online e o Exchange Online podem armazenar grandes quantidades de conteúdo documentário.</span><span class="sxs-lookup"><span data-stu-id="f4a42-109">SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content.</span></span> <span data-ttu-id="f4a42-110">Dependendo da versão, esses produtos podem oferecer suporte a descoberta eletrônica e bloqueios no local (Lync através do Exchange Server), tornando mais fácil para as equipes legais indexar, identificar, reter e filtrar o conteúdo mais relevante para um determinado caso.</span><span class="sxs-lookup"><span data-stu-id="f4a42-110">Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="f4a42-111">Muitos documentos são armazenados nos computadores locais dos usuários (responsáveis), e não em um local centralizado.</span><span class="sxs-lookup"><span data-stu-id="f4a42-111">Many documents are stored on users' (Custodians) local computers, not in a centralized location.</span></span> <span data-ttu-id="f4a42-112">Isso torna praticamente impossível que o SharePoint 2013 pesquise e, se não puder ser pesquisado, não possa ser incluído no eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="f4a42-112">This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery.</span></span> <span data-ttu-id="f4a42-113">Esta solução mostra como usar scripts de logon, System Center Orchestrator 2012 R2 e Windows PowerShell para Exchange Server para automatizar a identificação e coleção de materiais documentários de computadores dos usuários.</span><span class="sxs-lookup"><span data-stu-id="f4a42-113">This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="f4a42-114">O que esta solução faz</span><span class="sxs-lookup"><span data-stu-id="f4a42-114">What this solution does</span></span>

<span data-ttu-id="f4a42-115">Esta solução usa um grupo de segurança global, uma diretiva de grupo e um script do Windows PowerShell para localizar, inventariar e coletar conteúdo e arquivos de repositório pessoal do Outlook de computadores locais de usuários para um compartilhamento de arquivo oculto.</span><span class="sxs-lookup"><span data-stu-id="f4a42-115">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share.</span></span> <span data-ttu-id="f4a42-116">A partir daí, os arquivos PST podem ser importados para o Exchange Server 2013 ou o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f4a42-116">From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online.</span></span> <span data-ttu-id="f4a42-117">Todos os arquivos são movidos usando um runbook do System Center Orchestrator 2012 R2 para outro compartilhamento de arquivos no Microsoft Azure para armazenamento de longo prazo e indexação pelo SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="f4a42-117">All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013.</span></span> <span data-ttu-id="f4a42-118">Em seguida, você usa centros de descoberta eletrônica em sua implantação local do SharePoint 2013 ou no SharePoint Online, como faria regularmente para executar a descoberta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="f4a42-118">You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="f4a42-119">Esta solução usa o Robocopy para copiar arquivos dos computadores dos responsáveis para um compartilhamento de arquivos centralizado.</span><span class="sxs-lookup"><span data-stu-id="f4a42-119">This solution uses robocopy to copy files from custodian's computers to a centralized file share.</span></span> <span data-ttu-id="f4a42-120">Como o Robocopy não copia arquivos que estão abertos ou bloqueados, qualquer arquivo, incluindo arquivos PST, que os responsáveis por abrir não serão coletados.</span><span class="sxs-lookup"><span data-stu-id="f4a42-120">Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected.</span></span> <span data-ttu-id="f4a42-121">Você terá que coletar manualmente.</span><span class="sxs-lookup"><span data-stu-id="f4a42-121">You will have to collect them manually.</span></span> <span data-ttu-id="f4a42-122">Esta solução fornece uma lista que identifica explicitamente os arquivos que não podem ser copiados e o caminho completo para cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="f4a42-122">This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="f4a42-123">O diagrama a seguir orienta você por todas as etapas e elementos da solução.</span><span class="sxs-lookup"><span data-stu-id="f4a42-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Visão geral da solução de conjunto de arquivos automatizado](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="f4a42-125">Legenda \* \* \* \*</span><span class="sxs-lookup"><span data-stu-id="f4a42-125">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![texto explicativo magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="f4a42-127">Crie um objeto de política de grupo (GPO) e associe-o ao script de logon da coleção.</span><span class="sxs-lookup"><span data-stu-id="f4a42-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![balão magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="f4a42-129">Configure o filtro de segurança do GPO para aplicar o GPO somente ao grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="f4a42-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![texto explicativo 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="f4a42-131">Os responsáveis fizer o logon e o GPO ser executado, chamando o script de logon da coleção.</span><span class="sxs-lookup"><span data-stu-id="f4a42-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![texto explicativo magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="f4a42-133">O script de logon da coleção faz o inventário de todas as unidades conectadas localmente no computador responsáveis, pesquisando os arquivos que você deseja e gravando sua localização.</span><span class="sxs-lookup"><span data-stu-id="f4a42-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![balão magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="f4a42-135">O script de logon da coleção copia os arquivos inventariados para um compartilhamento de arquivo oculto no servidor de teste.</span><span class="sxs-lookup"><span data-stu-id="f4a42-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![chamada magenta 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="f4a42-137">(Opção A) Execute manualmente o script de importação PST para importar os arquivos PST coletados para o Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="f4a42-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![texto explicativo de magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="f4a42-139">(Opção B) Usando a ferramenta e o processo de importação do Office 365, importe os arquivos PST coletados para o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f4a42-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![balão de magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="f4a42-141">Mova todos os arquivos coletados para um compartilhamento de arquivos do Azure para armazenamento de longo prazo com o runbook do MoveToColdStorage System Center Orchestrator 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="f4a42-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![texto explicativo magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="f4a42-143">Indexe os arquivos no compartilhamento de arquivos de armazenamento Cold com o SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="f4a42-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![texto explicativo Magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="f4a42-145">Realize o conteúdo de descoberta eletrônica no armazenamento Cold e no Exchange Server 2013 local.</span><span class="sxs-lookup"><span data-stu-id="f4a42-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![texto explicativo 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="f4a42-147">Realize o conteúdo de descoberta eletrônica no Office 365.</span><span class="sxs-lookup"><span data-stu-id="f4a42-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="f4a42-148">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f4a42-148">Prerequisites</span></span>

<span data-ttu-id="f4a42-149">A configuração dessa solução requer muitos elementos, a maioria dos quais você provavelmente já fez e configurou se você está pensando no eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="f4a42-149">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery.</span></span> <span data-ttu-id="f4a42-150">Para os elementos que você não pode ter ou que exijam uma configuração específica, forneceremos os links necessários para desenvolver sua configuração básica.</span><span class="sxs-lookup"><span data-stu-id="f4a42-150">For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration.</span></span> <span data-ttu-id="f4a42-151">Você deve ter a configuração básica in-loco antes de configurar a própria solução.</span><span class="sxs-lookup"><span data-stu-id="f4a42-151">You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="f4a42-152">Configuração base</span><span class="sxs-lookup"><span data-stu-id="f4a42-152">Base configuration</span></span>

|<span data-ttu-id="f4a42-153">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="f4a42-153">**Element**</span></span>|<span data-ttu-id="f4a42-154">**Link**</span><span class="sxs-lookup"><span data-stu-id="f4a42-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f4a42-155">Domínio dos serviços de domínio do Active Directory (AD DS)</span><span class="sxs-lookup"><span data-stu-id="f4a42-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="f4a42-156">Conectividade com a Internet da sua rede local</span><span class="sxs-lookup"><span data-stu-id="f4a42-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="f4a42-157">SQL Server 2012 para oferecer suporte ao SharePoint 2013 e ao System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f4a42-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="f4a42-158">Implantando o System Center Orchestrator-2012</span><span class="sxs-lookup"><span data-stu-id="f4a42-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="f4a42-159">SharePoint 2013 local ou baseado no Azure para descoberta eletrônica (necessário para A opção A)</span><span class="sxs-lookup"><span data-stu-id="f4a42-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="f4a42-160">Servidor de compartilhamento de arquivos no local para preparação</span><span class="sxs-lookup"><span data-stu-id="f4a42-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="f4a42-161">Exchange Server 2013 local para A opção uma importação de PST</span><span class="sxs-lookup"><span data-stu-id="f4a42-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="f4a42-162">CU5 (15.913.22) está disponível em [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="f4a42-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="f4a42-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f4a42-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="f4a42-164">Implantando o System Center Orchestrator-2012</span><span class="sxs-lookup"><span data-stu-id="f4a42-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="f4a42-165">Office 365 (E3 Plan) com Exchange Online e SharePoint Online (necessário para a opção B)</span><span class="sxs-lookup"><span data-stu-id="f4a42-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="f4a42-166">Para se inscrever em uma assinatura do Office 365 E3, confira [assinatura do office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span><span class="sxs-lookup"><span data-stu-id="f4a42-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="f4a42-167">Assinatura do Azure com uma máquina virtual</span><span class="sxs-lookup"><span data-stu-id="f4a42-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="f4a42-168">Para se inscrever no Azure, confira [inscrever-se no Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="f4a42-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="f4a42-169">Uma conexão VPN entre a rede local e sua assinatura do Azure</span><span class="sxs-lookup"><span data-stu-id="f4a42-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="f4a42-170">Para configurar um túnel VPN entre sua assinatura do Azure e sua rede local, consulte [conectar uma rede local a uma rede virtual do Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="f4a42-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="f4a42-171">Descoberta eletrônica do SharePoint 2013 configurada para pesquisar no SharePoint e no Exchange Server 2013 e, opcionalmente, Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="f4a42-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="f4a42-172">Para configurar a descoberta eletrônica dessa maneira, confira [Configurar a descoberta eletrônica no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) e[testar o guia de laboratório: configurar a descoberta eletrônica para um laboratório de teste de compartilhamentos de arquivos do Exchange, Lync, SharePoint e Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="f4a42-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="f4a42-173">Descoberta eletrônica no Office 365 para SharePoint Online e Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f4a42-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="f4a42-174">Para configurar a descoberta eletrônica no Office 365, consulte [configurar um centro de descoberta eletrônica no SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="f4a42-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="f4a42-175">Configurar o ambiente</span><span class="sxs-lookup"><span data-stu-id="f4a42-175">Configure the environment</span></span>

<span data-ttu-id="f4a42-176">Agora que você tem a configuração base in-loco, você pode prosseguir para configurar a própria solução.</span><span class="sxs-lookup"><span data-stu-id="f4a42-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="f4a42-177">Compartilhamento de arquivo de preparação</span><span class="sxs-lookup"><span data-stu-id="f4a42-177">Staging file share</span></span>

1. <span data-ttu-id="f4a42-178">No domínio local, crie um grupo de segurança global chamado responsáveis.</span><span class="sxs-lookup"><span data-stu-id="f4a42-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="f4a42-179">Criar um compartilhamento de arquivo oculto para os arquivos coletados de computadores.</span><span class="sxs-lookup"><span data-stu-id="f4a42-179">Create a hidden file share for the files that are collected from Custodians computers.</span></span> <span data-ttu-id="f4a42-180">Ele deve estar em um servidor local.</span><span class="sxs-lookup"><span data-stu-id="f4a42-180">This should be on an on-premises server.</span></span> <span data-ttu-id="f4a42-181">Por exemplo, em um servidor chamado preparação, crie um compartilhamento de arquivos chamado casos $.</span><span class="sxs-lookup"><span data-stu-id="f4a42-181">For example, on a server called Staging, create a file share called Cases$.</span></span> <span data-ttu-id="f4a42-182">O **$** é necessário para tornar este um compartilhamento oculto.</span><span class="sxs-lookup"><span data-stu-id="f4a42-182">The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="f4a42-183">Defina as seguintes permissões de compartilhamento:</span><span class="sxs-lookup"><span data-stu-id="f4a42-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="f4a42-184">Responsáveis: alterar, ler</span><span class="sxs-lookup"><span data-stu-id="f4a42-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="f4a42-185">Administradores: Controle Total</span><span class="sxs-lookup"><span data-stu-id="f4a42-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="f4a42-186">Subsistema confiável do Exchange: alterar, ler</span><span class="sxs-lookup"><span data-stu-id="f4a42-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="f4a42-187">Abra a guia **segurança** , adicione o grupo responsáveis e clique em **avançado**.</span><span class="sxs-lookup"><span data-stu-id="f4a42-187">Open the **Security** tab, add the Custodians group, and click **Advanced**.</span></span> <span data-ttu-id="f4a42-188">Defina as seguintes permissões para o grupo responsáveis:</span><span class="sxs-lookup"><span data-stu-id="f4a42-188">Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="f4a42-189">**Tipo: negar**</span><span class="sxs-lookup"><span data-stu-id="f4a42-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="f4a42-190">**Aplica-se a: esta pasta, subpastas e arquivos**</span><span class="sxs-lookup"><span data-stu-id="f4a42-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="f4a42-191">Clique em **permissões avançadas** e selecione o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f4a42-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="f4a42-192">**Atributos de leitura**</span><span class="sxs-lookup"><span data-stu-id="f4a42-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="f4a42-193">**Ler atributos estendidos**</span><span class="sxs-lookup"><span data-stu-id="f4a42-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="f4a42-194">**Permissões de leitura**</span><span class="sxs-lookup"><span data-stu-id="f4a42-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="f4a42-195">Teste o acesso ao compartilhamento de arquivos de casos $, fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f4a42-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="f4a42-196">Adicionar um usuário ao grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="f4a42-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="f4a42-197">Coloque um arquivo na pasta casos $.</span><span class="sxs-lookup"><span data-stu-id="f4a42-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="f4a42-198">Como usuário, navegue até o servidor de teste, por exemplo, navegue até o \\ \\compartilhamento de preparo para ver quais compartilhamentos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f4a42-198">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available.</span></span> <span data-ttu-id="f4a42-199">Você não verá os **casos $** share listados.</span><span class="sxs-lookup"><span data-stu-id="f4a42-199">You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="f4a42-200">Digite manualmente o caminho completo para os casos $ share no Explorer.</span><span class="sxs-lookup"><span data-stu-id="f4a42-200">Manually type the full path to the Cases$ share into Explorer.</span></span> <span data-ttu-id="f4a42-201">Isso deve abrir os casos $ share.</span><span class="sxs-lookup"><span data-stu-id="f4a42-201">This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="f4a42-202">Tente abrir o arquivo que você colocou anteriormente no compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="f4a42-202">Try to open the file you previously placed in the share.</span></span> <span data-ttu-id="f4a42-203">Isso deve falhar.</span><span class="sxs-lookup"><span data-stu-id="f4a42-203">This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="f4a42-204">Script de logon</span><span class="sxs-lookup"><span data-stu-id="f4a42-204">Logon script</span></span>

1. <span data-ttu-id="f4a42-205">Copie e cole este script do Windows PowerShell no bloco de notas:</span><span class="sxs-lookup"><span data-stu-id="f4a42-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="f4a42-206">Salve o script acima como CollectionScript. ps1 em um local que seja fácil de localizar, por exemplo, C:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="f4a42-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="f4a42-207">Use o recurso ir para no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="f4a42-207">Use the Go To feature in Notepad.</span></span> <span data-ttu-id="f4a42-208">Faça as seguintes alterações, conforme necessário:</span><span class="sxs-lookup"><span data-stu-id="f4a42-208">Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="f4a42-209">**Número da linha**</span><span class="sxs-lookup"><span data-stu-id="f4a42-209">**Line #**</span></span>|<span data-ttu-id="f4a42-210">**O que você precisa alterar**</span><span class="sxs-lookup"><span data-stu-id="f4a42-210">**What you need to change**</span></span>|<span data-ttu-id="f4a42-211">**Obrigatório/opcional**</span><span class="sxs-lookup"><span data-stu-id="f4a42-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f4a42-212">71</span><span class="sxs-lookup"><span data-stu-id="f4a42-212">71</span></span>  <br/> |<span data-ttu-id="f4a42-213">**$Filetypes** variável.</span><span class="sxs-lookup"><span data-stu-id="f4a42-213">**$FileTypes** variable.</span></span> <span data-ttu-id="f4a42-214">Inclua todas as extensões de tipo de arquivo que você deseja que o script faça inventário e colete na variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="f4a42-214">Include all the file type extensions that you want the script to inventory and collect in the array variable.</span></span> <br/> |<span data-ttu-id="f4a42-215">Opcional</span><span class="sxs-lookup"><span data-stu-id="f4a42-215">Optional</span></span>  <br/> |
|<span data-ttu-id="f4a42-216">76 e 77</span><span class="sxs-lookup"><span data-stu-id="f4a42-216">76 and 77</span></span>  <br/> |<span data-ttu-id="f4a42-217">Alterar a maneira como a variável de **$CaseNo** é criada para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="f4a42-217">Change the way the **$CaseNo** variable is built to suit your needs.</span></span> <span data-ttu-id="f4a42-218">O script captura a data atual e a hora e acrescenta o nome de usuário a ela.</span><span class="sxs-lookup"><span data-stu-id="f4a42-218">The script captures the current date and time and appends the user name to it.</span></span> <br/> |<span data-ttu-id="f4a42-219">Opcional</span><span class="sxs-lookup"><span data-stu-id="f4a42-219">Optional</span></span>  <br/> |
|<span data-ttu-id="f4a42-220">80</span><span class="sxs-lookup"><span data-stu-id="f4a42-220">80</span></span>  <br/> |<span data-ttu-id="f4a42-221">**$CaseRootLocation** variável precisa ser definida para o compartilhamento de arquivos do conjunto de servidores de preparo, por exemplo \*\* \\ \\, exemplos de preparação\\$\*\*.</span><span class="sxs-lookup"><span data-stu-id="f4a42-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="f4a42-222">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="f4a42-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="f4a42-223">Coloque o arquivo CollectionScript. ps1 no compartilhamento de arquivos Netlogon em um controlador de domínio.</span><span class="sxs-lookup"><span data-stu-id="f4a42-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="f4a42-224">Configurar o GPO para o script de logon e o grupo de responsáveis</span><span class="sxs-lookup"><span data-stu-id="f4a42-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="f4a42-225">Configure um script de logon para o grupo responsáveis seguindo a seção "como atribuir scripts de logon do usuário" no tópico, [usando scripts de inicialização, desligamento, logon e logoff na política de grupo](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span><span class="sxs-lookup"><span data-stu-id="f4a42-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="f4a42-226">Remova os usuários autenticados da **filtragem de segurança**e adicione o grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="f4a42-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="f4a42-227">Opção de importação de PST A, script para o Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="f4a42-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="f4a42-228">Copie e cole o seguinte script do Windows PowerShell no bloco de notas:</span><span class="sxs-lookup"><span data-stu-id="f4a42-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="f4a42-229">Salve o script como PSTImportScript. ps1 em um local que seja fácil de encontrar.</span><span class="sxs-lookup"><span data-stu-id="f4a42-229">Save the script as PSTImportScript.ps1 in a location that's easy for you to find.</span></span> <span data-ttu-id="f4a42-230">Por exemplo e facilidade de uso, crie uma pasta no seu servidor de teste, \\ \\chamada preparação\\de AFCScripts, e salve-a.</span><span class="sxs-lookup"><span data-stu-id="f4a42-230">For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="f4a42-231">Use o recurso ir para no bloco de notas e faça as seguintes alterações, conforme necessário:</span><span class="sxs-lookup"><span data-stu-id="f4a42-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="f4a42-232">**Número da linha**</span><span class="sxs-lookup"><span data-stu-id="f4a42-232">**Line #**</span></span>|<span data-ttu-id="f4a42-233">**O que você precisa alterar**</span><span class="sxs-lookup"><span data-stu-id="f4a42-233">**What you need to change**</span></span>|<span data-ttu-id="f4a42-234">**Obrigatório/opcional**</span><span class="sxs-lookup"><span data-stu-id="f4a42-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="f4a42-235">3,6</span><span class="sxs-lookup"><span data-stu-id="f4a42-235">12</span></span>  <br/> |<span data-ttu-id="f4a42-236">**$FolderIdentifier** marca as pastas de caixa de correio nas quais os PSTs são importados.</span><span class="sxs-lookup"><span data-stu-id="f4a42-236">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into.</span></span> <span data-ttu-id="f4a42-237">Altere isso se necessário.</span><span class="sxs-lookup"><span data-stu-id="f4a42-237">Change this if necessary.</span></span> <br/> |<span data-ttu-id="f4a42-238">Opcional</span><span class="sxs-lookup"><span data-stu-id="f4a42-238">Optional</span></span>  <br/> |
|<span data-ttu-id="f4a42-239">17.07.06</span><span class="sxs-lookup"><span data-stu-id="f4a42-239">17</span></span>  <br/> |<span data-ttu-id="f4a42-240">**$ConnectionURI** precisa ser definido para seu próprio servidor.</span><span class="sxs-lookup"><span data-stu-id="f4a42-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="f4a42-241">> [!IMPORTANT]> certifique-se de que o **$ConnectionURI** aponta para um local http, e não HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f4a42-241">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https.</span></span> <span data-ttu-id="f4a42-242">Ele não funcionará com https:.</span><span class="sxs-lookup"><span data-stu-id="f4a42-242">It won't work with https:.</span></span>          |<span data-ttu-id="f4a42-243">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="f4a42-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="f4a42-244">Verifique se a conta de subsistema confiável do Exchange tem permissões de leitura, gravação e execução \\ \\para o\\compartilhamento de casos de preparação $.</span><span class="sxs-lookup"><span data-stu-id="f4a42-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="f4a42-245">O script de importação de PST requer os dois parâmetros de entrada a seguir:</span><span class="sxs-lookup"><span data-stu-id="f4a42-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="f4a42-246">**$SourcePath** O local dos arquivos PST a serem importados, por \\ \\exemplo,\\exemplos de preparação $.</span><span class="sxs-lookup"><span data-stu-id="f4a42-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="f4a42-247">**$MailboxAlias** O alias da caixa de correio de destino que receberá os itens de email importados.</span><span class="sxs-lookup"><span data-stu-id="f4a42-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="f4a42-248">Por exemplo, se você deseja importar todos os arquivos PST do caminho \\Staging\Cases $ para uma caixa de correio com o alias eDiscoveryMailbox, você deve executar o script como este `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="f4a42-248">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="f4a42-249">Opção de importação de PST B, para o Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f4a42-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="f4a42-250">Crie a estrutura da caixa de correio para colocar os arquivos PST importados no.</span><span class="sxs-lookup"><span data-stu-id="f4a42-250">Create the mailbox structure to place the imported PST files into.</span></span> <span data-ttu-id="f4a42-251">Para saber mais sobre como criar uma caixa de correio de usuário no Exchange Online, confira[criar caixas de correio de usuário no Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="f4a42-251">For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="f4a42-252">Armazenamento Cold</span><span class="sxs-lookup"><span data-stu-id="f4a42-252">Cold storage</span></span>

1. <span data-ttu-id="f4a42-253">Crie um compartilhamento de arquivos na máquina virtual do Azure, onde todos os arquivos coletados serão colocados, por exemplo \\ \\,\\AZFile1 ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="f4a42-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="f4a42-254">Conceda à conta de acesso ao conteúdo padrão pelo menos permissões de leitura para o compartilhamento e todas as subpastas e arquivos.</span><span class="sxs-lookup"><span data-stu-id="f4a42-254">Grant the default content access account at least Read permissions to the share and all subfolders and files.</span></span> <span data-ttu-id="f4a42-255">Para obter mais informações sobre como configurar a pesquisa do SharePoint 2013, consulte [Create and configure a Search Service Application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="f4a42-255">For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="f4a42-256">Se você previr a importação de arquivos \\ \\PST\\do AZFile1 ContentColdStorage, conceda permissões de leitura, gravação e execução do subsistema confiável do Exchange para o compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="f4a42-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="f4a42-257">Orquestrador</span><span class="sxs-lookup"><span data-stu-id="f4a42-257">Orchestrator</span></span>

1. <span data-ttu-id="f4a42-258">Baixe o[ runbook MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) do centro de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4a42-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="f4a42-259">Abra o **runbook designer**, no painel **conexões** , clique na pasta para a qual você deseja importar o runbook.</span><span class="sxs-lookup"><span data-stu-id="f4a42-259">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into.</span></span> <span data-ttu-id="f4a42-260">Clique no menu **ações** e clique em **importar**.</span><span class="sxs-lookup"><span data-stu-id="f4a42-260">Click the **Actions** menu, and the click **Import**.</span></span> <span data-ttu-id="f4a42-261">A caixa de diálogo **importar** é exibida.</span><span class="sxs-lookup"><span data-stu-id="f4a42-261">The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="f4a42-262">Na caixa **local do arquivo** , digite o caminho e o nome de arquivo do runbook que você deseja importar ou clique nas reticências ( **...**) para navegar até o arquivo que você deseja importar.</span><span class="sxs-lookup"><span data-stu-id="f4a42-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="f4a42-263">Selecione **importar runbooks** e **importar dados criptografados do Orchestrator**.</span><span class="sxs-lookup"><span data-stu-id="f4a42-263">Select **Import runbooks** and **Import Orchestrator encrypted data**.</span></span> <span data-ttu-id="f4a42-264">Limpe **contadores**, **agendas**, **variáveis**, **grupos de computadores**, **importe configurações globais**e **substitua as configurações globais existentes**.</span><span class="sxs-lookup"><span data-stu-id="f4a42-264">Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="f4a42-265">Clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="f4a42-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="f4a42-266">Edite o runbook **MoveFilesToColdStorage** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f4a42-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="f4a42-267">**Mover arquivo** atividade-define o caminho do **arquivo de origem** para o compartilhamento de arquivo de \\ \\conjunto,\\por exemplo, exemplos de preparação $.</span><span class="sxs-lookup"><span data-stu-id="f4a42-267">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="f4a42-268">Defina a **pasta de destino** para o compartilhamento de arquivo de armazenamento Cold no Azure \\ \\,\\por exemplo, AZFile1 ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="f4a42-268">Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="f4a42-269">Selecione **criar um arquivo com um nome exclusivo**.</span><span class="sxs-lookup"><span data-stu-id="f4a42-269">Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="f4a42-270">**Excluir** atividade da pasta-defina **o caminho:** para o compartilhamento de arquivo da coleção \\ \\, por\\exemplo,\\casos de preparação $ \*, e selecione **excluir todos os arquivos e subpastas**.</span><span class="sxs-lookup"><span data-stu-id="f4a42-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="f4a42-271">Implante o runbook **MoveToColdStorage** usando os procedimentos de[implantação de Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span><span class="sxs-lookup"><span data-stu-id="f4a42-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="f4a42-272">Pesquisa do SharePoint no local para armazenamento Cold</span><span class="sxs-lookup"><span data-stu-id="f4a42-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="f4a42-273">Crie uma nova fonte de conteúdo no seu farm do SharePoint 2013 para o compartilhamento de armazenamento Cold no Azure \\ \\,\\por exemplo, AZFile1 ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="f4a42-273">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage.</span></span> <span data-ttu-id="f4a42-274">Para obter mais informações sobre como gerenciar fontes de conteúdo, consulte [Adicionar, editar ou excluir uma fonte de conteúdo no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="f4a42-274">For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="f4a42-275">Inicie um rastreamento completo.</span><span class="sxs-lookup"><span data-stu-id="f4a42-275">Start a full crawl.</span></span> <span data-ttu-id="f4a42-276">Para obter mais informações, consulte, [Iniciar, pausar, continuar ou parar um rastreamento no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="f4a42-276">For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="f4a42-277">Usando a solução</span><span class="sxs-lookup"><span data-stu-id="f4a42-277">Using the solution</span></span>

<span data-ttu-id="f4a42-278">Há cinco etapas principais para usar essa solução, supondo que você não queira importar os arquivos PST para o Exchange Server 2013 e o Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f4a42-278">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online.</span></span> <span data-ttu-id="f4a42-279">Esta seção fornece os procedimentos para todos eles.</span><span class="sxs-lookup"><span data-stu-id="f4a42-279">This section provides you with the procedures for all of them.</span></span> <span data-ttu-id="f4a42-280">Sua interação principal com a solução será fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f4a42-280">Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="f4a42-281">Gerenciar a associação do usuário no grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="f4a42-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="f4a42-282">Revise os arquivos de log gerados pelo script de logon.</span><span class="sxs-lookup"><span data-stu-id="f4a42-282">Review the log files generated by the logon script.</span></span> <span data-ttu-id="f4a42-283">O FileCopyErrors. log lista todos os arquivos que não foram copiados com êxito.</span><span class="sxs-lookup"><span data-stu-id="f4a42-283">The FileCopyErrors.log lists all the files that were not successfully copied.</span></span> <span data-ttu-id="f4a42-284">Você precisa decidir o que deseja fazer com eles</span><span class="sxs-lookup"><span data-stu-id="f4a42-284">You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="f4a42-285">Gerenciar o processo de importação de PST.</span><span class="sxs-lookup"><span data-stu-id="f4a42-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="f4a42-286">Mover os arquivos da coleção para o armazenamento Cold.</span><span class="sxs-lookup"><span data-stu-id="f4a42-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="f4a42-287">Todas as outras etapas não são específicas desta solução.</span><span class="sxs-lookup"><span data-stu-id="f4a42-287">All the other steps are not specific to this solution.</span></span> <span data-ttu-id="f4a42-288">São tarefas administrativas padrão realizadas no SharePoint 2013 e no Office 365 e no Azure.</span><span class="sxs-lookup"><span data-stu-id="f4a42-288">They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure.</span></span> <span data-ttu-id="f4a42-289">Há itens que esta solução não fornece orientações que você precisará para trabalhar com base nas necessidades da sua empresa, como:</span><span class="sxs-lookup"><span data-stu-id="f4a42-289">There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="f4a42-290">Controle de casos de descoberta eletrônica e quais responsáveis estão associados a esse caso.</span><span class="sxs-lookup"><span data-stu-id="f4a42-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="f4a42-291">Controlar quais conjuntos de coleções de arquivos são associados ao caso de descoberta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="f4a42-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="f4a42-292">Coordenar o tempo das etapas de importação e migração para o armazenamento Cold.</span><span class="sxs-lookup"><span data-stu-id="f4a42-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="f4a42-293">Gerenciar o espaço de arquivo usado no Azure.</span><span class="sxs-lookup"><span data-stu-id="f4a42-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="f4a42-294">Gerenciar as caixas de correio nas quais os PSTs são importados.</span><span class="sxs-lookup"><span data-stu-id="f4a42-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="f4a42-295">Backup e restauração de todos os dados locais.</span><span class="sxs-lookup"><span data-stu-id="f4a42-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="f4a42-296">Gerenciamento de responsáveis</span><span class="sxs-lookup"><span data-stu-id="f4a42-296">Custodian management</span></span>

- <span data-ttu-id="f4a42-297">Para iniciar o processo de coleta automatizada de arquivos para um usuário individual, adicione-os ao grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="f4a42-297">To start the automated file collection process for an individual user, add them to the Custodians group.</span></span> <span data-ttu-id="f4a42-298">Na próxima vez que o usuário fizer logon, o script de logon atribuído ao grupo responsáveis por meio da política de grupo será executado.</span><span class="sxs-lookup"><span data-stu-id="f4a42-298">The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="f4a42-299">Monitorar arquivos coletados e examinar arquivos de log</span><span class="sxs-lookup"><span data-stu-id="f4a42-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="f4a42-300">Assista ao compartilhamento de arquivo de coleção, \\ \\por exemplo\\, casos\\de preparação $ \*, para a pasta de coleção do usuário.</span><span class="sxs-lookup"><span data-stu-id="f4a42-300">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user.</span></span> <span data-ttu-id="f4a42-301">O nome da pasta será formatado da seguinte maneira: *yyyyMMddHHmm_UserName* .</span><span class="sxs-lookup"><span data-stu-id="f4a42-301">The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="f4a42-302">Quando a coleção estiver concluída, abra a pasta da coleção e navegue até a pasta _Log.</span><span class="sxs-lookup"><span data-stu-id="f4a42-302">When the collection is completed, open the collection folder, and browse to the _Log folder.</span></span> <span data-ttu-id="f4a42-303">Na pasta _Log, você verá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f4a42-303">In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="f4a42-304">Um arquivo XML para cada unidade local no computador do usuário, por exemplo, **um. xml**, **C. xml**.</span><span class="sxs-lookup"><span data-stu-id="f4a42-304">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**.</span></span> <span data-ttu-id="f4a42-305">Esses arquivos contêm as unidades de estoque que são nomeadas após e são usadas para a operação do Robocopy.</span><span class="sxs-lookup"><span data-stu-id="f4a42-305">These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="f4a42-306">O script de coleção só criará uma entrada no arquivo de inventário para os tipos de arquivo que você definiu no próprio script.</span><span class="sxs-lookup"><span data-stu-id="f4a42-306">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself.</span></span> <span data-ttu-id="f4a42-307">Ele não criará uma entrada de inventário para cada arquivo no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="f4a42-307">It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="f4a42-308">Um arquivo de log chamado FileCopyErrors. log para cada execução de coleção.</span><span class="sxs-lookup"><span data-stu-id="f4a42-308">One log file named FileCopyErrors.log for each collection run.</span></span> <span data-ttu-id="f4a42-309">Este arquivo contém uma lista dos arquivos que o Robocopy não pôde copiar para o compartilhamento de coleção de arquivos, por \\ \\exemplo,\\casos de\\preparação $ \*.</span><span class="sxs-lookup"><span data-stu-id="f4a42-309">This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*.</span></span> <span data-ttu-id="f4a42-310">Você precisará revisar esta ação e decidir quais ações tomar para esses arquivos perdidos.</span><span class="sxs-lookup"><span data-stu-id="f4a42-310">You will need to review this and decide what actions to take for these missed files.</span></span> <span data-ttu-id="f4a42-311">Normalmente, você precisará coletar manualmente, se quiser, ou pode decidir que elas não são necessárias e, portanto, podem ser omitidas da coleção.</span><span class="sxs-lookup"><span data-stu-id="f4a42-311">Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="f4a42-312">Opção de importação de PST A para o Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="f4a42-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="f4a42-313">Faça logon no servidor que hospeda o compartilhamento de arquivo de conjunto, por exemplo, **preparação**e abra o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f4a42-313">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell.</span></span> <span data-ttu-id="f4a42-314">Para obter mais informações sobre como iniciar o Windows PowerShell, consulte[iniciando o Windows PowerShell no Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="f4a42-314">For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="f4a42-315">Defina a política de execução como irrestrita.</span><span class="sxs-lookup"><span data-stu-id="f4a42-315">Set the Execution policy to Unrestricted .</span></span> <span data-ttu-id="f4a42-316">Digite `Set-ExecutionPolicy Unrestricted -Scope Process` no Windows PowerShell e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="f4a42-316">Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="f4a42-317">Execute o arquivo PSTImportScript. ps1 e forneça os parâmetros **$SourcePath** e **$MailboxAlias** .</span><span class="sxs-lookup"><span data-stu-id="f4a42-317">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters.</span></span> <span data-ttu-id="f4a42-318">Para obter mais informações sobre a execução de scripts do Windows PowerShell, consulte[running scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="f4a42-318">For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="f4a42-319">Revise a saída para ver se há erros.</span><span class="sxs-lookup"><span data-stu-id="f4a42-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="f4a42-320">Antes de tentar importar um arquivo PST com nome idêntico para a mesma caixa de correio, você precisa remover a solicitação de importação de caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="f4a42-320">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request.</span></span> <span data-ttu-id="f4a42-321">Execute o seguinte comando para fazer isso: `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span><span class="sxs-lookup"><span data-stu-id="f4a42-321">Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`.</span></span> <span data-ttu-id="f4a42-322">Você será solicitado a remover cada solicitação individual da fila.</span><span class="sxs-lookup"><span data-stu-id="f4a42-322">You will be prompted to remove each individual request from the queue.</span></span> <span data-ttu-id="f4a42-323">Responder conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="f4a42-323">Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="f4a42-324">Opção de importação de PST B, para o Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f4a42-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="f4a42-325">Para colocar os arquivos PST coletados no Exchange Online, siga os procedimentos na seção importar arquivos para o Office 365 através da seção carregamento de rede do [serviço de importação do office 365](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span><span class="sxs-lookup"><span data-stu-id="f4a42-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="f4a42-326">Mover para o armazenamento Cold</span><span class="sxs-lookup"><span data-stu-id="f4a42-326">Move to cold storage</span></span>

1. <span data-ttu-id="f4a42-327">Execute o runbook **MoveToColdStorage** usando os procedimentos em[executando Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span><span class="sxs-lookup"><span data-stu-id="f4a42-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="f4a42-328">Assista ao compartilhamento de arquivos do Azure que você está usando para armazenamento de longo \\ \\prazo\\, por exemplo, AZFile1 ContentColdStorage e o compartilhamento de arquivo da \\ \\coleção local\\, por exemplo, exemplos de preparação $.</span><span class="sxs-lookup"><span data-stu-id="f4a42-328">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$.</span></span> <span data-ttu-id="f4a42-329">Você deve ver os arquivos e pastas que aparecem no compartilhamento de arquivos de armazenamento Cold e desaparecem do conjunto de arquivos de coleção.</span><span class="sxs-lookup"><span data-stu-id="f4a42-329">You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="f4a42-330">Descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="f4a42-330">eDiscovery</span></span>

1. <span data-ttu-id="f4a42-331">Permitir que o rastreamento completo do compartilhamento de arquivos de armazenamento Cold seja executado como agendamentos ou iniciar um rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f4a42-331">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl.</span></span> <span data-ttu-id="f4a42-332">Para obter mais informações sobre como iniciar rastreamentos completos ou incrementais, consulte [Iniciar, pausar, continuar ou parar um rastreamento no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="f4a42-332">For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="f4a42-333">Criar um caso de descoberta eletrônica no SharePoint 2013 se você usou A opção A para um arquivo PST, importe ou crie um caso de descoberta eletrônica no SharePoint Online se você usou a opção B.</span><span class="sxs-lookup"><span data-stu-id="f4a42-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

