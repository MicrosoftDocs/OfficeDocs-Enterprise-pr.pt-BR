---
title: Baixar e executar a ferramenta IdFix do Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Como baixar e executar a ferramenta IdFix do Office 365 para ajudar a limpar seu Active Directory Domain Services (AD DS) antes de sincronizá-lo com o Office 365.
ms.openlocfilehash: d816abe8e93830832077c614e496576d42890d50
ms.sourcegitcommit: 7f025939c9dad676602bcd7693a8e356821fd456
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2020
ms.locfileid: "43068773"
---
# <a name="download-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="2f75c-103">Baixar e executar a ferramenta IdFix do Office 365</span><span class="sxs-lookup"><span data-stu-id="2f75c-103">Download and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="2f75c-104">*Esse artigo se aplica ao Office 365 Enterprise e ao Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="2f75c-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="2f75c-105">O IdFix identifica erros como duplicatas e problemas de formatação no Serviços de Domínio Active Directory (AD DS) antes de sincronizá-lo com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="2f75c-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="2f75c-106">Para concluir esta tarefa com êxito, você deve estar seguro para trabalhar com objetos de usuário, grupo e contato no AD DS.</span><span class="sxs-lookup"><span data-stu-id="2f75c-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="2f75c-107">Se não puder concluir essa tarefa, há algumas outras coisas que você pode fazer.</span><span class="sxs-lookup"><span data-stu-id="2f75c-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="2f75c-108">Esses métodos podem ser mais fáceis, mas também podem levar mais tempo ou ter outras desvantagens.</span><span class="sxs-lookup"><span data-stu-id="2f75c-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="2f75c-109">Que são:</span><span class="sxs-lookup"><span data-stu-id="2f75c-109">They are:</span></span>
  
- <span data-ttu-id="2f75c-110">**Executar a sincronização de diretórios sem executar o IdFix**</span><span class="sxs-lookup"><span data-stu-id="2f75c-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="2f75c-111">Você pode sincronizar seu diretório sem usar a ferramenta IdFix, mas não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="2f75c-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="2f75c-112">A correção de erros antes da sincronização leva menos tempo e geralmente proporciona uma transição mais suave para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="2f75c-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="2f75c-113">**Contratar um consultor**</span><span class="sxs-lookup"><span data-stu-id="2f75c-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="2f75c-114">Obter ajuda especializada pode colocar seus usuários prontos para trabalhar com rapidez e seu diretório sincronizado.</span><span class="sxs-lookup"><span data-stu-id="2f75c-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="2f75c-115">O que você precisa para executar o IdFix</span><span class="sxs-lookup"><span data-stu-id="2f75c-115">What you need to run IdFix</span></span>

<span data-ttu-id="2f75c-116">A maneira mais fácil de garantir que o IdFix funcione é baixá-lo em um computador que ingressou no seu domínio do AD DS. </span><span class="sxs-lookup"><span data-stu-id="2f75c-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="2f75c-117">Você pode executá-lo no controlador de domínio, se desejar, mas isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="2f75c-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="2f75c-118">Requisitos de hardware do IdFix</span><span class="sxs-lookup"><span data-stu-id="2f75c-118">IdFix hardware requirements</span></span>

<span data-ttu-id="2f75c-119">O computador onde você baixa o IdFix precisa atender a estes requisitos mínimos de hardware:</span><span class="sxs-lookup"><span data-stu-id="2f75c-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="2f75c-120">4 GB de RAM</span><span class="sxs-lookup"><span data-stu-id="2f75c-120">4 GB RAM</span></span>
- <span data-ttu-id="2f75c-121">2 GB de espaço em disco rígido</span><span class="sxs-lookup"><span data-stu-id="2f75c-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="2f75c-122">Requisitos de software do IdFix</span><span class="sxs-lookup"><span data-stu-id="2f75c-122">IdFix software requirements</span></span>

<span data-ttu-id="2f75c-123">O computador onde você baixa o IdFix precisa ser associado ao mesmo domínio do AD DS do qual você deseja sincronizar os usuários com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="2f75c-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Office 365.</span></span> 

<span data-ttu-id="2f75c-124">O computador também precisa ter o .NET Framework 4.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="2f75c-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="2f75c-125">Se você estiver executando o Windows Server 2008 ou posterior, o .NET Framework provavelmente já está instalado. </span><span class="sxs-lookup"><span data-stu-id="2f75c-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="2f75c-126">Caso contrário, você pode [baixar o .NET 4,0 do centro de download](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou com o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="2f75c-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="2f75c-127">Requisitos de permissões do IdFix</span><span class="sxs-lookup"><span data-stu-id="2f75c-127">IdFix permissions requirements</span></span>

<span data-ttu-id="2f75c-128">A conta de usuário que você usa para executar o IdFix deve ter acesso de leitura e gravação ao domínio do AD DS.</span><span class="sxs-lookup"><span data-stu-id="2f75c-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="2f75c-129">Se você não tiver certeza se sua conta de usuário atende a esses requisitos e se não tem certeza de como verificar, ainda assim é possível baixar e executar o IdFix. </span><span class="sxs-lookup"><span data-stu-id="2f75c-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="2f75c-130">Se sua conta de usuário não tiver as permissões corretas, o IdFix simplesmente exibirá um erro quando você tentar executá-la.</span><span class="sxs-lookup"><span data-stu-id="2f75c-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="2f75c-131">Baixar e extrair o IdFix</span><span class="sxs-lookup"><span data-stu-id="2f75c-131">Download and extract IdFix</span></span>

<span data-ttu-id="2f75c-132">Siga estas instruções.</span><span class="sxs-lookup"><span data-stu-id="2f75c-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="2f75c-133">Faça logon no computador em que você deseja executar a ferramenta IdFix.</span><span class="sxs-lookup"><span data-stu-id="2f75c-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="2f75c-134">Vá para o site da [ferramenta de correção de erros do IdFix DirSync](https://github.com/microsoft/idfix) .</span><span class="sxs-lookup"><span data-stu-id="2f75c-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="2f75c-135">Clique em **Iniciar** na seção **início do ClickOnce** para baixar o arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="2f75c-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="2f75c-136">Abra o arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="2f75c-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="2f75c-137">Na janela **IdFix**, escolha **Extrair** e, em seguida, **Extrair tudo**.</span><span class="sxs-lookup"><span data-stu-id="2f75c-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="2f75c-138">Por padrão, o IdFix é extraído para `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="2f75c-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="2f75c-139">Escolha **Extrair**.</span><span class="sxs-lookup"><span data-stu-id="2f75c-139">Choose **Extract**.</span></span>

<span data-ttu-id="2f75c-140">Suas etapas podem variar com base na sua versão do Windows e no navegador da Internet.</span><span class="sxs-lookup"><span data-stu-id="2f75c-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="2f75c-141">Executar a ferramenta IdFix</span><span class="sxs-lookup"><span data-stu-id="2f75c-141">Run the IdFix tool</span></span>

<span data-ttu-id="2f75c-142">Depois de baixar e extrair o IdFix, execute-o para procurar problemas no seu domínio do AD DS.</span><span class="sxs-lookup"><span data-stu-id="2f75c-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="2f75c-143">Usando uma conta com acesso de leitura/gravação ao seu domínio do AD DS, entre no computador onde você baixou o IdFix.</span><span class="sxs-lookup"><span data-stu-id="2f75c-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="2f75c-144">No explorador de arquivos, vá para o local onde você extraiu o IdFix. </span><span class="sxs-lookup"><span data-stu-id="2f75c-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="2f75c-145">Se você escolher a pasta padrão durante a extração, vá para `C:\Users\<your user name>\Documents\IdFix`.</span><span class="sxs-lookup"><span data-stu-id="2f75c-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="2f75c-146">Clique duas vezes em **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="2f75c-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="2f75c-147">Por padrão, o IdFix usa a regra de Multilocatário definida para testar as entradas em seu diretório.</span><span class="sxs-lookup"><span data-stu-id="2f75c-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="2f75c-148">Este é o conjunto de regras correto para a maioria dos clientes do Office 365. </span><span class="sxs-lookup"><span data-stu-id="2f75c-148">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="2f75c-149">No entanto, se você for um cliente do Office 365 Dedicado ou do Regulamento Internacional de Tráfego de Armas (ITAR)), você poderá configurar o IdFix para usar o conjunto de regras Dedicado.</span><span class="sxs-lookup"><span data-stu-id="2f75c-149">However, if you are an Office 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="2f75c-150">Se você não tem certeza do tipo de cliente que você é, ignore esta etapa.</span><span class="sxs-lookup"><span data-stu-id="2f75c-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="2f75c-151">Para definir o conjunto de regras para Dedicado, clique no ícone de engrenagem na barra de menus e escolha **Dedicado**.</span><span class="sxs-lookup"><span data-stu-id="2f75c-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="2f75c-152">Escolha **Consulta**.</span><span class="sxs-lookup"><span data-stu-id="2f75c-152">Choose **Query**.</span></span>
    
    ![Escolha consulta em IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="2f75c-154">Por padrão, o IdFix procura erros em todo o diretório.</span><span class="sxs-lookup"><span data-stu-id="2f75c-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="2f75c-155">Dependendo do tamanho do seu diretório, a execução da consulta pode demorar um pouco.</span><span class="sxs-lookup"><span data-stu-id="2f75c-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="2f75c-156">Você pode observar o andamento na parte inferior da janela principal da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="2f75c-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="2f75c-157">Se você clicar em **Cancelar**, será necessário recomeçar do início.</span><span class="sxs-lookup"><span data-stu-id="2f75c-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="2f75c-158">Depois que o IdFix concluir a consulta, você poderá sincronizar seu diretório se não houver erros. </span><span class="sxs-lookup"><span data-stu-id="2f75c-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="2f75c-159">Se houver erros no diretório, é recomendável corrigi-los antes de sincronizar. </span><span class="sxs-lookup"><span data-stu-id="2f75c-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="2f75c-160">Confira [preparar atributos de diretório para sincronização com o Office 365](prepare-directory-attributes-for-synch-with-idfix.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2f75c-160">See [prepare directory attributes for synchronization with Office 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="2f75c-161">Embora não seja obrigatório corrigir os erros antes de sincronizar, é altamente recomendável que você, pelo menos, analise todos os erros retornados pelo IdFix.</span><span class="sxs-lookup"><span data-stu-id="2f75c-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="2f75c-162">Cada erro é exibido em uma linha separada na janela principal da ferramenta. </span><span class="sxs-lookup"><span data-stu-id="2f75c-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="2f75c-163">Se você concorda com a alteração sugerida na coluna **ATUALIZAÇÃO**, selecione na coluna **AÇÃO** o que deseja que a IdFix faça para implementar a alteração e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="2f75c-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="2f75c-164">Quando você clica em **Aplicar**, a ferramenta faz todas as alterações no diretório.</span><span class="sxs-lookup"><span data-stu-id="2f75c-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="2f75c-165">Você não precisa clicar em **Aplicar** após cada atualização.</span><span class="sxs-lookup"><span data-stu-id="2f75c-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="2f75c-166">Em vez disso, é possível corrigir vários erros antes de clicar em **Aplicar** e o IdFix alterará todos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="2f75c-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="2f75c-167">Você pode classificar os erros por tipo de erro clicando em **ERRO** na parte superior da coluna que lista os tipos de erro.</span><span class="sxs-lookup"><span data-stu-id="2f75c-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="2f75c-168">Uma estratégia é corrigir todos os erros do mesmo tipo. Por exemplo, corrija primeiro todas as duplicatas e aplique-as.</span><span class="sxs-lookup"><span data-stu-id="2f75c-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="2f75c-169">Em seguida, corrija os erros de formato de caractere e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="2f75c-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="2f75c-170">Todas as vezes que você aplicar as alterações, a ferramenta IdFix cria um arquivo de log separado que você pode usar para desfazer as alterações caso cometa um erro.</span><span class="sxs-lookup"><span data-stu-id="2f75c-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="2f75c-171">O [log de transações](idfix-transaction-log.md) é armazenado na pasta onde você extraiu o IdFix, que é_C:\Usuários\<seu nome de usuário>\Documentos\idFix_ por padrão.</span><span class="sxs-lookup"><span data-stu-id="2f75c-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![Correção de erros no IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="2f75c-173">Depois de fazer todas as alterações no diretório, execute o IdFix novamente para garantir que as correções feitas não introduzam novos erros.</span><span class="sxs-lookup"><span data-stu-id="2f75c-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="2f75c-174">Você pode repetir essas etapas quantas vezes precisar.</span><span class="sxs-lookup"><span data-stu-id="2f75c-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="2f75c-175">É uma boa ideia executar esse processo algumas vezes antes de sincronizar.</span><span class="sxs-lookup"><span data-stu-id="2f75c-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="2f75c-176">Recursos adicionais no IdFix</span><span class="sxs-lookup"><span data-stu-id="2f75c-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="2f75c-177">Objetos e atributos excluídos e compatíveis com o IdFix</span><span class="sxs-lookup"><span data-stu-id="2f75c-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="2f75c-178">Log de transações IdFix do Office 365</span><span class="sxs-lookup"><span data-stu-id="2f75c-178">Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="2f75c-179">Treinamentos em vídeo</span><span class="sxs-lookup"><span data-stu-id="2f75c-179">Video training</span></span>

<span data-ttu-id="2f75c-180">Para obter mais informações, confira a lição [Instalar e usar a ferramenta IdFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), oferecida pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="2f75c-180">For more information, see the lesson [Install and use the IdFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

