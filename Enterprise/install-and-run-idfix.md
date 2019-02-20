---
title: Instalar e executar a ferramenta IdFix do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Como instalar e executar a ferramenta IdFix do Office 365 para ajudar a limpar o Active Directory antes de sincronizá-lo com o Office 365.
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085400"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="aaa8c-103">Instalar e executar a ferramenta IdFix do Office 365</span><span class="sxs-lookup"><span data-stu-id="aaa8c-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="aaa8c-104">IdFix identifica erros como duplicatas e problemas de formatação no seu diretório antes de sincronizar com o Office 365.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="aaa8c-105">Para concluir essa tarefa com êxito, você deve estar seguro para trabalhar com objetos de usuário, de grupo e de contato no Active Directory.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="aaa8c-p101">Se você não puder concluir esta tarefa, há algumas outras coisas que você pode fazer. Esses métodos podem ser mais fáceis, mas também podem demorar mais ou ter outras desvantagens. Eles são:</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="aaa8c-p102">**Executar a sincronização de diretórios sem executar o IdFix.** Você pode sincronizar seu diretório sem executar a ferramenta IdFix, mas não é recomendável. A correção de erros antes da sincronização leva menos tempo e geralmente fornece uma transição mais suave para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="aaa8c-p103">**Contrate um consultor.** Obter ajuda especializada pode fazer com que seus usuários fiquem prontos para trabalhar com rapidez e que seu diretório seja sincronizado.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="aaa8c-114">O que você precisa para executar o IdFix</span><span class="sxs-lookup"><span data-stu-id="aaa8c-114">What you need to run IdFix</span></span>

<span data-ttu-id="aaa8c-p104">A maneira mais fácil de obter o IdFix em funcionamento é instalá-lo em um computador que tenha ingressado no seu domínio. Você pode executá-lo no controlador de domínio, se desejar, mas isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="aaa8c-117">Requisitos de hardware do IdFix</span><span class="sxs-lookup"><span data-stu-id="aaa8c-117">IdFix hardware requirements</span></span>

<span data-ttu-id="aaa8c-118">O computador onde você instala o IdFix precisa atender a estes requisitos mínimos de hardware:</span><span class="sxs-lookup"><span data-stu-id="aaa8c-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="aaa8c-119">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="aaa8c-119">4 GB RAM</span></span>
- <span data-ttu-id="aaa8c-120">2 GB de espaço em disco rígido</span><span class="sxs-lookup"><span data-stu-id="aaa8c-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="aaa8c-121">Requisitos de software do IdFix</span><span class="sxs-lookup"><span data-stu-id="aaa8c-121">IdFix software requirements</span></span>

<span data-ttu-id="aaa8c-p105">O computador onde você instala o IdFix precisa ser associado ao mesmo domínio do Active Directory do qual você deseja sincronizar os usuários para o Office 365. O computador também precisa ter o .NET Framework 4,0 instalado.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p105">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="aaa8c-p106">Se você estiver executando o Windows Server 2008 ou o Windows Server 2012, o .NET Framework provavelmente já está instalado. Caso contrário, você pode [baixar o .net 4,0 do centro de download](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou através do Windows Update.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="aaa8c-126">Requisitos de permissões do IdFix</span><span class="sxs-lookup"><span data-stu-id="aaa8c-126">IdFix permissions requirements</span></span>

<span data-ttu-id="aaa8c-127">A conta de usuário que você usa para executar o IdFix precisa ter acesso de leitura/gravação ao diretório.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="aaa8c-p107">Se você não tiver certeza se sua conta de usuário atende a esses requisitos e se não tem certeza de como verificar, ainda pode instalar e executar o IdFix. Se sua conta de usuário não tiver as permissões corretas, o IdFix simplesmente exibirá um erro quando você tentar executá-la.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="aaa8c-130">Instalar o IdFix</span><span class="sxs-lookup"><span data-stu-id="aaa8c-130">Install IdFix</span></span>

<span data-ttu-id="aaa8c-131">Para instalar o IdFix, baixe e descompacte o **IdFix. exe**:</span><span class="sxs-lookup"><span data-stu-id="aaa8c-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="aaa8c-132">Faça logon no computador no qual deseja instalar a ferramenta IdFix.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="aaa8c-133">Vá para o site de download da Microsoft para a [ferramenta de correção de erros do IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).</span><span class="sxs-lookup"><span data-stu-id="aaa8c-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="aaa8c-134">Escolha **Download**.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="aaa8c-135">Quando solicitado, escolha **executar**.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="aaa8c-p108">Na caixa de diálogo **WinZip Self-Extractor** , na caixa de texto **pasta de** descompactar, digite ou procure o local onde você deseja instalar a ferramenta IdFix. Por padrão, o IdFix é instalado `C:\Deployment Tools\`no.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="aaa8c-138">Escolha **unzip**.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="aaa8c-139">Executar a ferramenta IdFix</span><span class="sxs-lookup"><span data-stu-id="aaa8c-139">Run the IdFix tool</span></span>

<span data-ttu-id="aaa8c-140">Após a instalação do IdFix, execute a ferramenta para procurar problemas no diretório:</span><span class="sxs-lookup"><span data-stu-id="aaa8c-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="aaa8c-141">Usando uma conta que tenha acesso de leitura/gravação ao diretório, faça logon no computador no qual você instalou o IdFix.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="aaa8c-p109">No explorador de arquivos, vá para o local onde você instalou o IdFix. Se você escolher a pasta padrão durante a instalação, vá `C:\Deployment Tools\IdFix`para.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="aaa8c-144">Clique duas vezes em **IdFix.exe**.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-144">Double-click **IdFix.exe**.</span></span> 
    
    ![Escolha o arquivo IdFix. exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="aaa8c-p110">Por padrão, o IdFix usa o conjunto de regras multiLocatário para testar as entradas no seu diretório. Este é o conjunto de regras correto para a maioria dos clientes do Office 365. No enTanto, se você for um cliente do Office 365 dedicado ou ITAR (leis internacionais de tráfego de braços), poderá configurar o IdFix para usar o conjunto de regras dedicado. Se você não tiver certeza sobre o tipo de cliente que você está, pode ignorar esta etapa com segurança. Para definir o conjunto de regras como dedicado, clique no ícone de engrenagem na barra de menus e, em seguida, escolha **dedicado**.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="aaa8c-151">Escolha **consulta**.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-151">Choose **Query**.</span></span>
    
    ![Escolha consulta no IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="aaa8c-153">Por padrão, o IdFix pesquisa todo o diretório em busca de erros.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="aaa8c-p111">Dependendo do tamanho do seu diretório, a execução da consulta pode demorar um pouco. Você pode assistir ao progresso na parte inferior da janela principal da ferramenta. Se você clicar em **Cancelar**, precisará reiniciar desde o início.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix consulta e contagem de erros.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="aaa8c-p112">Depois que o IdFix concluir a consulta, você poderá sincronizar o diretório se não houver erros. Se houver erros no diretório, é recomendável corrigi-los antes de sincronizar. Se você deseja obter informações mais específicas sobre os tipos de erros e recomendações sobre a melhor maneira de corrigir cada um deles, consulte os links no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p112">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="aaa8c-161">Embora não seja obrigatório corrigir os erros antes de sincronizar, é altamente recomendável que você, pelo menos, analise todos os erros retornados pelo IdFix.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="aaa8c-162">Cada erro é exibido em uma linha separada na janela principal da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="aaa8c-p113">Se você concorda com a alteração sugerida na coluna **UPDATE**, na coluna **ACTION** selecione o que deseja que o IdFix faça para implementar a alteração e, em seguida, clique em **Aplicar**. Quando você clica em **Aplicar**, a ferramenta faz as alterações no diretório.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="aaa8c-p114">Você não precisa clicar em **aplicar** após cada atualização. Em vez disso, você pode corrigir vários erros antes de clicar em **aplicar** e o IdFix todos serão alterados ao mesmo tempo. Você pode classificar os erros por tipo de erro clicando em **erro** na parte superior da coluna que lista os tipos de erro.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="aaa8c-p115">Uma estratégia é corrigir todos os erros do mesmo tipo; por exemplo, corrija primeiro todas as duplicatas e aplique-as. Em seguida, corrija os erros de formato de caractere e assim por diante. Cada vez que você aplica as alterações, a ferramenta IdFix cria um arquivo de log separado que você pode usar para desfazer suas alterações caso você cometa um erro. O [log de transações](idfix-transaction-log.md) é armazenado na pasta em que você instalou o IdFix.  _C:\Deployment Tools\IdFix_ por padrão.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![Correção de erros no IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="aaa8c-p116">Depois que todas as suas alterações forem feitas no diretório, execute IdFix novamente para garantir que as correções que você fez não introduziu novos erros. Você pode repetir essas etapas quantas vezes for necessário. É uma boa ideia passar pelo processo algumas vezes antes de sincronizar.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="aaa8c-177">Quero aperfeiçoar minha pesquisa ou me aprofundar nos erros, o que mais eu posso fazer com o IdFix?</span><span class="sxs-lookup"><span data-stu-id="aaa8c-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="aaa8c-178">Mais informações detalhadas estão disponíveis com estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="aaa8c-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="aaa8c-p117">[Preparar atributos de diretório para sincronização com o Office 365 usando a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Após instalar a ferramenta, vá para este tópico para obter instruções mais detalhadas sobre como executar a ferramenta, erros comuns que você encontrará, sugestões de correção, exemplos e práticas recomendadas para o que fazer quando você tiver um grande número de erros.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="aaa8c-181">Referência: IdFix objetos e atributos excluídos e com suporte</span><span class="sxs-lookup"><span data-stu-id="aaa8c-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="aaa8c-182">Referência: Log de transações do IdFix do Office 365</span><span class="sxs-lookup"><span data-stu-id="aaa8c-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="aaa8c-183">Treinamento em vídeo</span><span class="sxs-lookup"><span data-stu-id="aaa8c-183">Video training</span></span>

<span data-ttu-id="aaa8c-184">Para obter mais informações, consulte a lição [instalar e usar a ferramenta IDFix](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), trazida para você pelo LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="aaa8c-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

