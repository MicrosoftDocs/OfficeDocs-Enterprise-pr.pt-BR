---
title: Automatizar a coleção de arquivos para a Descoberta eletrônica
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Resumo: Saiba como automatizar o conjunto de arquivos dos computadores do usuário para a descoberta eletrônica.'
ms.openlocfilehash: 12d61d2c43a297001eecf463991654afbcfccb1a
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915746"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="9d3a0-103">Automatizar a coleção de arquivos para a Descoberta eletrônica</span><span class="sxs-lookup"><span data-stu-id="9d3a0-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="9d3a0-104">**Resumo:** Saiba como automatizar o conjunto de arquivos dos computadores do usuário para a descoberta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="9d3a0-p101">Todas as empresas enfrentam o potencial de ações legais ou outros tipos de ações legais. Enquanto departamentos legais trabalham para reduzir a essa exposição, litígio é um fato da vida útil de negócios. Quando uma empresa faces ação judicial, eles são necessários, pelo processo de descoberta legal, para fornecer a todos os materiais de documentos relevantes para o tribunal e advogado oposto.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="9d3a0-p102">descoberta eletrônica é o processo pelo qual as empresas de estoque, pesquisa, identificam, preservar, filtrar e disponibilizar os materiais de documentos relevantes que existem em formulário eletrônico. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online e Exchange Online podem armazenar grandes quantidades de conteúdo de documentos. Dependendo da versão, esses produtos podem suportar a descoberta eletrônica e in-loco retém (Lync através do servidor do Exchange), tornando mais fácil para que as equipes legais indexar, identificam, mantenha e filtrar o conteúdo mais relevante para uma determinada ocorrência.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="9d3a0-p103">Muitos documentos são armazenados em dos usuários (responsáveis) computadores locais, não em um local centralizado. Isso torna impossível essencialmente para o SharePoint 2013 pesquisar e se ele não pode ser pesquisado, ele não pode ser incluído no eDiscovery. Essa solução mostra como usar scripts de logon, o System Center Orchestrator 2012 R2 e o Windows PowerShell para o Exchange Server para automatizar a identificação e o conjunto de documentos materiais dos computadores dos usuários.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="9d3a0-114">Esta solução não</span><span class="sxs-lookup"><span data-stu-id="9d3a0-114">What this solution does</span></span>

<span data-ttu-id="9d3a0-p104">Esta solução usa um grupo de segurança global, diretiva de grupo e um script do Windows PowerShell para localizar, de estoque e coletar conteúdo e os arquivos de armazenamento pessoal (. PST) do Outlook dos computadores de usuários locais para um compartilhamento de arquivo oculto. A partir daí, os arquivos PST podem ser importados para o Exchange Server 2013 ou Exchange Online. Todos os arquivos são movidos usando um runbook do System Center Orchestrator 2012 R2 para outro compartilhamento de arquivo no Microsoft Azure para armazenamento de longo prazo e indexação pelo SharePoint 2013. Você então usar centros de eDiscovery em sua implantação do SharePoint 2013 no local ou no SharePoint Online como faria regularmente para executar a descoberta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="9d3a0-p105">Esta solução usa o robocopy para copiar os arquivos dos computadores dos responsáveis para um compartilhamento de arquivo centralizado. Porque o robocopy não copia os arquivos que são aberto ou bloqueado, quaisquer arquivos, incluindo arquivos PST, que dos responsáveis abriu não será coletado. Você precisará coletá-los manualmente. Essa solução fornecem uma lista que identifica explicitamente os arquivos que ele não é possível copiar e o caminho completo para cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="9d3a0-123">O diagrama a seguir percorre todas as etapas e os elementos da solução.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![Visão geral da solução de coleção de arquivos automatizada](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="9d3a0-125">Legenda \* \* \*</span><span class="sxs-lookup"><span data-stu-id="9d3a0-125">****Legend****</span></span>||
|:-----|:-----|
|![balão magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="9d3a0-127">Criar um objeto de diretiva de grupo (GPO) e associá-lo com o script de logon da coleção.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![balão magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="9d3a0-129">Configure o filtro de segurança do GPO para aplicar o GPO somente ao grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![balão magenta 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="9d3a0-131">Dos responsáveis faz logon e executa o GPO, chamar o script de logon da coleção.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![balão magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="9d3a0-133">O script de logon da coleção faz o inventário todas as unidades conectadas localmente no computador responsáveis, pesquisar os arquivos que deseja e seu local de gravação.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![balão magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="9d3a0-135">O script de logon da coleção copia os arquivos inventariados para um compartilhamento de arquivo oculto no servidor intermediário.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![balão magenta 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="9d3a0-137">(Uma opção) Manualmente, execute o script de importação de PST para importar os arquivos PST coletados para Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![balão magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="9d3a0-139">(Opção B) Usando a ferramenta de importação do Office 365 e o processo, importe os arquivos PST coletados para Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![balão magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="9d3a0-141">Mova coletados todos os arquivos para um compartilhamento de arquivo Azure para armazenamento de longo prazo com o runbook MoveToColdStorage System Center Orchestrator 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![balão magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="9d3a0-143">Indexe os arquivos em compartilhamento de arquivos o armazenamento frio com o SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![balão magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="9d3a0-145">Execute a descoberta eletrônica no conteúdo em armazenamento de frio e do local Exchange Server 2013.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![balão magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="9d3a0-147">Execute a descoberta eletrônica no conteúdo no Office 365.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="9d3a0-148">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9d3a0-148">Prerequisites</span></span>

<span data-ttu-id="9d3a0-p106">A configuração dessa solução requer muitos elementos, mais dos quais você provavelmente in-loco e configurou se você estiver pensando sobre a descoberta eletrônica. Para os elementos que você pode não ter ou aquelas que exigem uma configuração específica, forneceremos você com os links que você precisa criar sua configuração de base. Você deve ter a configuração básica in-loco antes de configurar a solução em si.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="9d3a0-152">Configuração base</span><span class="sxs-lookup"><span data-stu-id="9d3a0-152">Base configuration</span></span>

|<span data-ttu-id="9d3a0-153">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-153">**Element**</span></span>|<span data-ttu-id="9d3a0-154">**Link**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9d3a0-155">Domínio do Active Directory Domain Services (AD DS)</span><span class="sxs-lookup"><span data-stu-id="9d3a0-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="9d3a0-156">Conectividade de Internet da sua rede local</span><span class="sxs-lookup"><span data-stu-id="9d3a0-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="9d3a0-157">SQL Server 2012 para dar suporte ao SharePoint 2013 e o System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d3a0-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="9d3a0-158">Implantando o System Center Orchestrator - 2012</span><span class="sxs-lookup"><span data-stu-id="9d3a0-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="9d3a0-159">Local ou Azure com base em SharePoint 2013 para descoberta eletrônica (necessária para a opção uma)</span><span class="sxs-lookup"><span data-stu-id="9d3a0-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="9d3a0-160">Servidor de compartilhamento de arquivos local para preparação</span><span class="sxs-lookup"><span data-stu-id="9d3a0-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="9d3a0-161">Local do Exchange Server 2013 para importação de PST de uma opção</span><span class="sxs-lookup"><span data-stu-id="9d3a0-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="9d3a0-162">CU5 (15.913.22) está disponível em [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="9d3a0-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d3a0-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="9d3a0-164">Implantando o System Center Orchestrator - 2012</span><span class="sxs-lookup"><span data-stu-id="9d3a0-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="9d3a0-165">Office 365 (plano E3) com o Exchange Online e SharePoint Online (necessário para a opção B)</span><span class="sxs-lookup"><span data-stu-id="9d3a0-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="9d3a0-166">Para se inscrever para uma assinatura do Office 365 E3, consulte [assinatura do Office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="9d3a0-167">Assinatura do Windows Azure com uma máquina virtual</span><span class="sxs-lookup"><span data-stu-id="9d3a0-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="9d3a0-168">Para se inscrever para um Azure, consulte [inscrever-se no Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="9d3a0-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="9d3a0-169">Uma conexão VPN entre sua rede local e a sua assinatura do Windows Azure</span><span class="sxs-lookup"><span data-stu-id="9d3a0-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="9d3a0-170">Para configurar um túnel VPN entre sua assinatura do Windows Azure e sua rede local, consulte [Connect uma local da rede para uma rede virtual do Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="9d3a0-171">EDiscovery do SharePoint 2013 configurado para pesquisar por meio do SharePoint e Exchange Server 2013 e, opcionalmente, Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="9d3a0-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="9d3a0-172">Para configurar o eDiscovery dessa maneira, consulte [Configurar o eDiscovery no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) e[Test Lab Guide: configurar a descoberta eletrônica para um Exchange, Lync, SharePoint e do laboratório de teste de compartilhamentos de arquivo Windows](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="9d3a0-173">descoberta eletrônica no Office 365 para o SharePoint Online e o Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9d3a0-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="9d3a0-174">Para configurar o eDiscovery no Office 365, consulte [Configurar uma central de descoberta eletrônica no SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="9d3a0-175">Configurar o ambiente</span><span class="sxs-lookup"><span data-stu-id="9d3a0-175">Configure the environment</span></span>

<span data-ttu-id="9d3a0-176">Agora que você tem a configuração básica in-loco, você pode mover com antecedência para configurar a solução em si.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="9d3a0-177">Compartilhamento de arquivo do teste</span><span class="sxs-lookup"><span data-stu-id="9d3a0-177">Staging file share</span></span>

1. <span data-ttu-id="9d3a0-178">No domínio local, crie um grupo de segurança global chamado responsáveis.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="9d3a0-p107">Crie um compartilhamento de arquivo oculto para os arquivos que são coletadas de computadores responsáveis. Este deve ser em um servidor local. Por exemplo, em um servidor chamado preparo, crie um compartilhamento de arquivo chamado $ casos. O **$** é necessário para fazer isso em um compartilhamento oculto.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="9d3a0-183">Defina as permissões de compartilhamento a seguir:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="9d3a0-184">Responsáveis: Alteração e leitura</span><span class="sxs-lookup"><span data-stu-id="9d3a0-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="9d3a0-185">Administradores: Controle Total</span><span class="sxs-lookup"><span data-stu-id="9d3a0-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="9d3a0-186">Subsistema confiável do Exchange: Leitura, alteração</span><span class="sxs-lookup"><span data-stu-id="9d3a0-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="9d3a0-p108">Abra a guia **segurança** , adicione o grupo responsáveis e clique em **Avançado**. Defina as seguintes permissões para o grupo responsáveis:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="9d3a0-189">**Tipo: Negar**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="9d3a0-190">**Aplica-se a: esta pasta, subpastas e arquivos**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="9d3a0-191">Clique em **Permissões avançadas** e selecione o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="9d3a0-192">**Atributos de leitura**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="9d3a0-193">**Ler atributos estendidos**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="9d3a0-194">**Permissões de leitura**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="9d3a0-195">Teste o acesso ao compartilhamento de arquivos de $ casos fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="9d3a0-196">Adicione um usuário ao grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="9d3a0-197">Coloca um arquivo na pasta de $ casos.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="9d3a0-p109">Como o usuário, vá para o servidor de teste, por exemplo, navegue até o \\ \\preparo compartilhar para ver quais compartilhamentos estão disponíveis. Você não deve ver o compartilhamento de **casos$** listado.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="9d3a0-p110">Manualmente, digite o caminho completo para o compartilhamento de $ casos no Explorer. Isso deve abrir o compartilhamento de $ casos.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="9d3a0-p111">Tente abrir o arquivo que você colocou anteriormente no compartilhamento. Isso deve falhar.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="9d3a0-204">Script de logon</span><span class="sxs-lookup"><span data-stu-id="9d3a0-204">Logon script</span></span>

1. <span data-ttu-id="9d3a0-205">Copie e cole este script do Windows PowerShell no bloco de notas:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
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

2. <span data-ttu-id="9d3a0-206">Salve o script acima como CollectionScript.ps1 em um local fácil de encontrar, por exemplo, c:\\AFCScripts.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="9d3a0-p112">Use o recurso ir para no bloco de notas. Faça as seguintes alterações, conforme necessário:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="9d3a0-209">**Número da linha**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-209">**Line #**</span></span>|<span data-ttu-id="9d3a0-210">**Você precisa alterar**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-210">**What you need to change**</span></span>|<span data-ttu-id="9d3a0-211">**Obrigatório/opcional**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9d3a0-212">71</span><span class="sxs-lookup"><span data-stu-id="9d3a0-212">71</span></span>  <br/> |<span data-ttu-id="9d3a0-p113">Variável de **$FileTypes** . Inclua todas as extensões de tipo de arquivo que você deseja que o script de estoque e coletar na variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="9d3a0-215">Opcional</span><span class="sxs-lookup"><span data-stu-id="9d3a0-215">Optional</span></span>  <br/> |
|<span data-ttu-id="9d3a0-216">76 e 77</span><span class="sxs-lookup"><span data-stu-id="9d3a0-216">76 and 77</span></span>  <br/> |<span data-ttu-id="9d3a0-p114">Alterar a maneira como a variável **$CaseNo** é criado para atender às suas necessidades. O script captura a data atual e a hora e o acrescenta o nome de usuário a ela.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="9d3a0-219">Opcional</span><span class="sxs-lookup"><span data-stu-id="9d3a0-219">Optional</span></span>  <br/> |
|<span data-ttu-id="9d3a0-220">80</span><span class="sxs-lookup"><span data-stu-id="9d3a0-220">80</span></span>  <br/> |<span data-ttu-id="9d3a0-221">Compartilha **$CaseRootLocation** variável precisa ser definida como seu arquivo preparo de conjunto de servidores, por exemplo ** \\ \\preparo\\casos$**.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="9d3a0-222">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9d3a0-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="9d3a0-223">Coloque o arquivo de CollectionScript.ps1 no compartilhamento de arquivo de logon de rede em um controlador de domínio.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="9d3a0-224">Configurar o GPO para o script de logon e o grupo de responsáveis</span><span class="sxs-lookup"><span data-stu-id="9d3a0-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="9d3a0-225">Configure um script de logon para o grupo responsáveis seguindo a seção "Como atribuir scripts de logon do usuário" no tópico, [usando inicialização, desligamento, Logon e os Scripts de Logoff na diretiva de grupo](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="9d3a0-226">Remover usuários autenticados do **Filtro de segurança**e adicione o grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="9d3a0-227">PST importar opção A, o script do Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="9d3a0-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="9d3a0-228">Copie e cole o seguinte script do Windows PowerShell no bloco de notas:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
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
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
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

2. <span data-ttu-id="9d3a0-p115">Salve o script como PSTImportScript.ps1 em um local fácil de encontrar. Por exemplo e facilidade de uso, crie uma pasta no seu servidor intermediário chamado \\ \\preparo\\AFCScripts e salvá-lo nesse local.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="9d3a0-231">Use o recurso ir para no bloco de notas e faça as seguintes alterações, conforme necessário:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="9d3a0-232">**Número da linha**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-232">**Line #**</span></span>|<span data-ttu-id="9d3a0-233">**Você precisa alterar**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-233">**What you need to change**</span></span>|<span data-ttu-id="9d3a0-234">**Obrigatório/opcional**</span><span class="sxs-lookup"><span data-stu-id="9d3a0-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9d3a0-235">12 </span><span class="sxs-lookup"><span data-stu-id="9d3a0-235">12</span></span>  <br/> |<span data-ttu-id="9d3a0-p116">As pastas de caixa de correio que PSTs são importados para marcas de **$FolderIdentifier** . Altere essa opção se necessário.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="9d3a0-238">Opcional</span><span class="sxs-lookup"><span data-stu-id="9d3a0-238">Optional</span></span>  <br/> |
|<span data-ttu-id="9d3a0-239">17 </span><span class="sxs-lookup"><span data-stu-id="9d3a0-239">17</span></span>  <br/> |<span data-ttu-id="9d3a0-240">**$ConnectionUri** deve ser definida para seu próprio servidor.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="9d3a0-p117">> [!IMPORTANT]> Verifique se sua **$ConnectionUri** aponta para um local de http, https não. Ele não funcionará com https:.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="9d3a0-243">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9d3a0-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="9d3a0-244">Verifique se a conta de subsistema confiável do Exchange tem permissões de leitura, gravação e execução para o \\ \\preparo\\compartilhamento de $ casos.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="9d3a0-245">O script de importação de PST requer os dois parâmetros de entrada a seguintes:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="9d3a0-246">**$SourcePath** O local dos arquivos PST a ser importado, por exemplo \\ \\preparo\\casos$.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="9d3a0-247">**$MailboxAlias** O alias da caixa de correio de destino que receberá os itens de e-mail importadas.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="9d3a0-248">Por exemplo, se você deseja importar todos os arquivos PST do caminho da \\Staging\Cases$ em uma caixa de correio com o eDiscoveryMailbox alias, você pode executar o script semelhante a esta `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-248">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="9d3a0-249">Opção de importação de PST B, para o Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9d3a0-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="9d3a0-p118">Crie a estrutura da caixa de correio para colocar os arquivos PST importados em. Para obter mais informações sobre como criar uma caixa de correio do usuário no Exchange Online, consulte[Criar caixas de correio de usuário no Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="9d3a0-252">Armazenamento frio</span><span class="sxs-lookup"><span data-stu-id="9d3a0-252">Cold storage</span></span>

1. <span data-ttu-id="9d3a0-253">Criar um compartilhamento de arquivo no Windows Azure Máquina Virtual, onde todos os arquivos coletados serão colocados, por exemplo, \\ \\AZFile1\\ContentColdStorage.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="9d3a0-p119">Conceder a conta de acesso a conteúdo padrão pelo menos permissões de leitura para o compartilhamento e todas as subpastas e arquivos. Para obter mais informações sobre como configurar a pesquisa do SharePoint 2013, consulte [criar e configurar um aplicativo de serviço de pesquisa no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="9d3a0-256">Se você prevê a importação de arquivos PST do \\ \\AZFile1\\ContentColdStorage, conceder leia subsistema confiável do Exchange, gravação e execução de permissões para o compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="9d3a0-257">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="9d3a0-257">Orchestrator</span></span>

1. <span data-ttu-id="9d3a0-258">Baixe o[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) do Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="9d3a0-p120">Abrir o **Runbook Designer**, no painel **conexões** , clique na pasta que você deseja importar o runbook em. Clique no menu **ações** e clique em **Importar**. Será exibida a caixa de diálogo de **importação** .</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="9d3a0-262">Na caixa **Local do arquivo** , digite o nome de arquivo e caminho do runbook que você deseja importar ou clique nas reticências ( **…**) para navegar até o arquivo que você deseja importar.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="9d3a0-p121">Selecione **Importar runbooks** e **Orchestrator importar os dados criptografados**. Desmarque **contadores**, **agendas**, **variáveis**, **Grupos de computadores**, **configurações globais de importação**e **Substituir as configurações globais existentes**.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="9d3a0-265">Clique em **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="9d3a0-266">Edite o runbook **MoveFilesToColdStorage** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="9d3a0-p122">Atividade de **Mover arquivos** - definir o caminho do **Arquivo de origem** para o compartilhamento de arquivos da coleção, por exemplo \\ \\preparo\\casos$. Conjunto de compartilhar a **Pasta de destino** para o arquivo frio armazenamento no Windows Azure, por exemplo \\ \\AZFile1\\ContentColdStorage. Selecione **criar um arquivo com um nome exclusivo**.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="9d3a0-270">**Excluir pasta** atividade - definir o **caminho:** à coleção de compartilhamento de arquivo, por exemplo \\ \\preparo\\casos$\\* e selecione **Excluir todos os arquivos e subpastas**.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="9d3a0-271">Implante o runbook **MoveToColdStorage** usando os procedimentos em[Implantando Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="9d3a0-272">Pesquisa do SharePoint local para armazenamento frio</span><span class="sxs-lookup"><span data-stu-id="9d3a0-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="9d3a0-p123">Criar uma nova fonte de conteúdo em seu farm do SharePoint 2013 para o compartilhamento de armazenamento frio no Windows Azure, por exemplo \\ \\AZFile1\\ContentColdStorage. Para obter mais informações sobre como gerenciar fontes de conteúdo, consulte [Adicionar, editar ou excluir uma fonte de conteúdo no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="9d3a0-p124">Inicie um rastreamento completo. Para mais informações, consulte [Iniciar, pausar, retomar ou parar um rastreamento no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="9d3a0-277">Usando a solução</span><span class="sxs-lookup"><span data-stu-id="9d3a0-277">Using the solution</span></span>

<span data-ttu-id="9d3a0-p125">Há cinco etapas principais usando essa solução, supondo que você não quiser importar os arquivos PST para o Exchange Server 2013 e Exchange Online. Esta seção fornece os procedimentos para todos eles. Sua principal interação com a solução será ao fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="9d3a0-281">Gerencie a associação do usuário no grupo responsáveis.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="9d3a0-p126">Revise os arquivos de log gerados pelo script de logon. O FileCopyErrors.log lista todos os arquivos que não foram copiados com êxito. É necessário decidir o que você deseja fazer com eles</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="9d3a0-285">Gerenciando o processo de importação de PST.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="9d3a0-286">Mover os arquivos da coleção para armazenamento frio.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="9d3a0-p127">Todas as outras etapas não são específicas para essa solução. Eles são tarefas administrativas padrão que podem ser executadas no SharePoint 2013 e o Office 365 e o Windows Azure. Existem itens que essa solução não oferece quaisquer diretrizes que você precisará trabalhar check-out com base nas necessidades da sua empresa, como:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p127">All the other steps are not specific to this solution. They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure. There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="9d3a0-290">Controlando seus casos de eDiscovery e quais responsáveis estão associados a qual caso.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="9d3a0-291">Controlando quais conjuntos de conjuntos de arquivo são associe com qual caso de descoberta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="9d3a0-292">Coordenar o tempo de importação e mover para armazenamento frio etapas.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="9d3a0-293">Gerenciando o espaço de arquivo usado no Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="9d3a0-294">Gerenciando as caixas de correio que PSTs são importados para.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="9d3a0-295">Backup e restauração de todos os dados de local.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="9d3a0-296">Gerenciamento dos responsáveis</span><span class="sxs-lookup"><span data-stu-id="9d3a0-296">Custodian management</span></span>

- <span data-ttu-id="9d3a0-p128">Para iniciar o processo de coleta automatizada de arquivos para um usuário individual, adicioná-los ao grupo responsáveis. Na próxima vez que o usuário fizer logon, o script de logon atribuído ao grupo responsáveis pela diretiva de grupo será executado.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="9d3a0-299">Monitore arquivos coletados e revisar os arquivos de log</span><span class="sxs-lookup"><span data-stu-id="9d3a0-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="9d3a0-p129">Assista o arquivo da coleção compartilhar, por exemplo \\ \\preparo\\casos$\\*, para a pasta da coleção do usuário. O nome da pasta será formatado como esta: *yyyyMMddHHmm_UserName* .</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="9d3a0-p130">Quando a coleção for concluída, abra a pasta da coleção e navegue até a pasta _Log. Na pasta _Log, você verá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="9d3a0-p131">Um arquivo XML para cada unidade local no computador do usuário, por exemplo **A.xml**, **C.xml**. Esses arquivos contêm as unidades de estoque que são nomeados após, e elas são usadas para a operação robocopy.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="9d3a0-p132">O script de coleção somente criará uma entrada no arquivo inventário para os tipos de arquivo que você definiu no próprio script. Além disso, ele não criará uma entrada de inventário para todos os arquivos no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="9d3a0-p133">Um arquivo de log denominado FileCopyErrors.log para cada conjunto de executar. Esse arquivo contém uma lista dos arquivos que robocopy poderia não uma cópia para o conjunto de arquivos compartilhar, por exemplo, \\ \\preparo\\casos$\\*. Você precisará revisar isso e decidir quais ações tomar para esses arquivos perdidos. Normalmente, você tanto precisa coletá-los manualmente, se desejado, ou você pode decidir que eles não são necessários e, portanto, podem ser omitidos da coleção.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="9d3a0-312">Opção de importação de PST uma para o Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="9d3a0-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="9d3a0-p134">Faça logon servidor que hospeda o compartilhamento de arquivos da coleção, por exemplo **preparo**e abra o Windows PowerShell. Para obter mais informações sobre como iniciar o Windows PowerShell, consulte[Iniciando o Windows PowerShell no Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="9d3a0-p135">Defina a diretiva de execução como irrestrito. Tipo `Set-ExecutionPolicy Unrestricted -Scope Process` em Windows PowerShell e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="9d3a0-p136">Execute o arquivo PSTImportScript.ps1 e fornecem os parâmetros **$SourcePath** e **$MailboxAlias** . Para obter mais informações sobre a execução de scripts do Windows PowerShell, consulte[Executando Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="9d3a0-319">Analise a saída se há erros.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="9d3a0-p137">Antes de tentar importar um arquivo PST de nome idêntico para a mesma caixa de correio, você precisa remover a solicitação de importação da caixa de correio. Execute o seguinte comando para fazer isso: `Get-MailboxImportRequest | Remove-MailboxImportRequest`. Você será solicitado para remover a cada solicitação individual da fila. Responda conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="9d3a0-324">Opção de importação de PST B, para o Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9d3a0-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="9d3a0-325">Para colocar os arquivos PST coletados em Exchange Online, siga os procedimentos nos arquivos de importação para o Office 365 por meio da seção de carregamento de rede do [Serviço de importação do Office 365](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="9d3a0-326">Migrar para o armazenamento frio</span><span class="sxs-lookup"><span data-stu-id="9d3a0-326">Move to cold storage</span></span>

1. <span data-ttu-id="9d3a0-327">Execute o runbook **MoveToColdStorage** usando os procedimentos em[Execução Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="9d3a0-p138">Observação o compartilhamento de arquivo Azure que você está usando para armazenamento de longo prazo, por exemplo \\ \\AZFile1\\ContentColdStorage e o arquivo da coleção local compartilharem, por exemplo \\ \\preparo\\casos$. Você deve ver os arquivos e pastas aparecem no compartilhamento de arquivo frio armazenamento e desaparecem do compartilhamento de arquivos da coleção.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="9d3a0-330">Descoberta Eletrônica</span><span class="sxs-lookup"><span data-stu-id="9d3a0-330">eDiscovery</span></span>

1. <span data-ttu-id="9d3a0-p139">Permitir o rastreamento completo do compartilhamento de arquivo frio armazenamento para executar como agendas, ou inicia um rastreamento. Para obter mais informações sobre como iniciar rastreamentos completos ou incrementais, consulte [Iniciar, pausar, retomar ou parar um rastreamento no SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span><span class="sxs-lookup"><span data-stu-id="9d3a0-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="9d3a0-333">Criar um caso de descoberta eletrônica no SharePoint 2013, se você usou a opção uma para uma importação de arquivos PST ou criar um caso de descoberta eletrônica no SharePoint Online, se você tiver usado a opção B.</span><span class="sxs-lookup"><span data-stu-id="9d3a0-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

