---
title: Por que você precisa usar o Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Resumo: você deve ser capaz de usar o Office 365 PowerShell para gerenciar o Office 365, em alguns casos, com mais eficiência e em outros casos por necessidade.'
ms.openlocfilehash: 66782a9165c76c7e1d506e40fa1cacd6db0c6724
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747440"
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="2d1d7-103">Por que você precisa usar o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d1d7-103">Why you need to use Office 365 PowerShell</span></span>

<span data-ttu-id="2d1d7-104">Com o centro de administração do Microsoft 365, você não só pode gerenciar suas licenças e contas de usuário do Office 365, mas também pode gerenciar os produtos de servidor do Office 365: Exchange, Skype for Business Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-104">With the Microsoft 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 server products: Exchange, Skype for Business Online, and SharePoint Online.</span></span> <span data-ttu-id="2d1d7-105">No entanto, você também pode gerenciar esses elementos com os comandos do Office 365 PowerShell, tirando proveito de um ambiente de linha de comando e de linguagem de script para velocidade, automação e capacidade adicional.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-105">However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="2d1d7-106">Neste artigo, mostraremos a você as seguintes maneiras em que você pode usar o Office 365 PowerShell para gerenciar o Office 365.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-106">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365.</span></span>
  
- <span data-ttu-id="2d1d7-107">O Office 365 PowerShell pode revelar informações adicionais que você não consegue ver com o centro de administração do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="2d1d7-107">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>
    
- <span data-ttu-id="2d1d7-108">O Office 365 tem recursos que você pode configurar apenas usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d1d7-108">Office 365 has features that you can only configure by using Office 365 PowerShell</span></span>
    
- <span data-ttu-id="2d1d7-109">Office 365 PowerShell é ótimo para realizar operações em massa</span><span class="sxs-lookup"><span data-stu-id="2d1d7-109">Office 365 PowerShell is great at performing bulk operations</span></span>
    
- <span data-ttu-id="2d1d7-110">O Office 365 PowerShell é ótimo na filtragem de dados</span><span class="sxs-lookup"><span data-stu-id="2d1d7-110">Office 365 PowerShell is great at filtering data</span></span>
    
- <span data-ttu-id="2d1d7-111">O Office 365 PowerShell torna mais fácil imprimir ou salvar dados</span><span class="sxs-lookup"><span data-stu-id="2d1d7-111">Office 365 PowerShell makes it easy to print or save data</span></span>
    
- <span data-ttu-id="2d1d7-112">O Office 365 PowerShell permite que você gerencie produtos de servidor</span><span class="sxs-lookup"><span data-stu-id="2d1d7-112">Office 365 PowerShell lets you manage across server products</span></span>
    
<span data-ttu-id="2d1d7-p102">Antes de começar, saiba que o Office 365 PowerShell é um conjunto de módulos para o Windows PowerShell, um ambiente de linha de comando para plataformas e serviços baseados em Windows. Esse ambiente cria uma linguagem de shell de comando que pode ser estendida com módulos adicionais e fornece uma maneira de executar comandos simples ou complexos, ou scripts. Por exemplo, depois de instalar os módulos do Office 365 PowerShell e entrar com sua assinatura do Office 365, você poderá executar esse comando para listar todas as caixas de correio do usuário para o Microsoft Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts. For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```powershell
Get-Mailbox
```

<span data-ttu-id="2d1d7-116">A obtenção da lista de caixas de correio também pode ser feita facilmente usando o centro de administração do Microsoft 365, mas contar o número de itens em todas as listas de todos os sites de todos os seus aplicativos Web não pode ser feito facilmente.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-116">Getting the list of mailboxes can also be easily done using the Microsoft 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="2d1d7-117">Observe que o Office 365 PowerShell foi projetado para aumentar e aprimorar sua capacidade de gerenciar o Office 365, não para substituir o centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-117">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Microsoft 365 admin center.</span></span> <span data-ttu-id="2d1d7-118">Como administrador do Office 365, você deve se familiarizar com o mínimo de usar o Office 365 PowerShell porque há alguns procedimentos de configuração que só podem ser feitos com os comandos do Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-118">As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands.</span></span> <span data-ttu-id="2d1d7-119">Nesses casos, você precisará compreender como:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-119">In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="2d1d7-120">Instalar os módulos do Office 365 PowerShell (feito apenas uma vez para cada computador do administrador).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-120">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="2d1d7-121">Conectar-se a sua assinatura do Office 365 (feita uma vez para cada sessão do PowerShell).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-121">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="2d1d7-122">Reunir as informações necessárias para executar os comandos necessários do Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-122">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="2d1d7-123">Executar os comandos do Office 365 PowerShell com êxito.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-123">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="2d1d7-p104">Depois de aprender essas habilidades básicas, não é necessário listar os usuários de caixa de correio com o comando **Get-Mailbox**, também não é preciso entender como criar um novo comando como o anterior para contar todos os itens nas listas de todos os sites para todos os seus aplicativos Web. A Microsoft e a comunidade de administradores do Office 365 podem ajudá-lo conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a><span data-ttu-id="2d1d7-126">O Office 365 PowerShell pode revelar informações adicionais que você não consegue ver com o centro de administração do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="2d1d7-126">Office 365 PowerShell can reveal additional information that you cannot see with the Microsoft 365 admin center</span></span>

<span data-ttu-id="2d1d7-127">O centro de administração 365 da Microsoft exibe muitas informações úteis, mas isso não significa que ela exiba todas as informações possíveis que o Office 365 armazena em usuários, licenças, caixas de correio e sites.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-127">The Microsoft 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites.</span></span> <span data-ttu-id="2d1d7-128">Veja um exemplo de **usuários e grupos** no centro de administração do Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-128">Here is an example for **users and groups** in the Microsoft 365 admin center:</span></span>
  
![Exemplo de exibição de usuários e grupos no centro de administração do Microsoft 365.](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="2d1d7-130">Para muitas finalidades, isso exibe as informações que você precisa saber.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-130">For many purposes, this displays the information you need to know.</span></span> <span data-ttu-id="2d1d7-131">No entanto, há ocasiões em que você precisa de mais.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-131">However, there are times when you need more.</span></span> <span data-ttu-id="2d1d7-132">Por exemplo, o licenciamento do Office 365 (e os recursos do Office 365 disponíveis para um usuário) dependem parte da localização geográfica desse usuário.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-132">For example, Office 365 licensing (and the Office 365 features available to a user) depend in part on that user's geographic location.</span></span> <span data-ttu-id="2d1d7-133">As políticas e os recursos que você pode estender para um usuário que reside nos Estados Unidos podem não ser os mesmos que as políticas e os recursos que você pode estender para um usuário que mora na Índia ou na Bélgica.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-133">The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium.</span></span> <span data-ttu-id="2d1d7-134">Você pode usar o centro de administração do Microsoft 365 para determinar a localização geográfica de um usuário com estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-134">You can use the Microsoft 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="2d1d7-135">Clique duas vezes no **Nome de exibição** do usuário.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-135">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="2d1d7-136">No painel de exibição de propriedades do usuário, clique em **detalhes**.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-136">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="2d1d7-137">Na exibição detalhes, clique em **detalhes adicionais**.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-137">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="2d1d7-138">Role para baixo até ver o cabeçalho **País ou região**:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-138">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Exemplo das informações de região de um usuário no centro de administração do Microsoft 365.](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="2d1d7-140">Escreva o nome de exibição e localização do usuário em um pedaço de papel ou copie e cole no Bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-140">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="2d1d7-p107">Você deve repetir este procedimento para cada usuário. Quando há muitos usuários, isso pode ser uma tarefa entediante. Com o Office 365 PowerShell, você pode exibir essas informações para todos os usuários com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> <span data-ttu-id="2d1d7-144">Este comando requer a instalação do [módulo do Microsoft Azure Active Directory](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-144">This command requires you to install the [Windows Azure Active Directory module](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).</span></span> 
  
<span data-ttu-id="2d1d7-145">Este é um exemplo de exibição:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-145">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="2d1d7-146">A interpretação deste comando do Office 365 PowerShell é: obter todos os usuários na assinatura atual do Office 365 ( **Get-MsolUser** ), mas exibir apenas o nome e o local para cada usuário ( **Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-146">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="2d1d7-p108">Porque o Office 365 PowerShell dá suporte a uma linguagem de shell de comando, você pode manipular ainda mais as informações obtidas do comando **Get-MSolUser**. Por exemplo, talvez você queira classificar esses usuários por sua localização, agrupar todos os usuários brasileiros, todos os usuários dos Estados Unidos etc. Este é o comando:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p108">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="2d1d7-149">Este é um exemplo de exibição:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-149">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  <span data-ttu-id="2d1d7-150">A interpretação deste comando do Office 365 PowerShell é: obter todos os usuários na assinatura atual do Office 365, mas exibir apenas o nome e o local para cada usuário e classificá-los primeiro pela localização, depois pelos nomes ( **Sort UsageLocation, DisplayName**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-150">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="2d1d7-p109">Você também pode usar a filtragem adicional. Por exemplo, se você quiser ver informações sobre usuários baseados no Brasil, use este comando:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p109">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="2d1d7-153">Este é um exemplo de exibição:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-153">Here is an example of the display:</span></span>
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="2d1d7-154">A interpretação deste comando do Office 365 PowerShell é: obter todos os usuários na assinatura atual do Office 365 que estejam no Brasil (**Where {$\_.UsageLocation -eq "BR"}**), em seguida, exibir o nome e o local de cada usuário.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-154">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="2d1d7-155">**Uma rápida observação sobre domínios maiores**</span><span class="sxs-lookup"><span data-stu-id="2d1d7-155">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="2d1d7-p110">Se você tiver um domínio muito grande, com dezenas de milhares de usuários, alguns dos exemplos que mostramos neste artigo podem levar a "limitação". Isso significa que, com base em coisas como poder de computação e largura de banda de rede disponível, você está tentando um pouco demais de uma só vez. Por causa disso, grandes organizações podem desejar dividir alguns dos comandos do Office 365 PowerShell em dois comandos. Por exemplo, este comando retorna todas as contas de usuário e mostra o nome e o local de cada usuário:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p110">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="2d1d7-p111">Isso funciona bem com domínios menores. Em uma grande organização, no entanto, talvez você precise dividi-lo em dois comandos: um comando para armazenar as informações da conta do usuário em uma variável e outro comando para exibir as informações necessárias. Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p111">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```powershell
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


<span data-ttu-id="2d1d7-163">A interpretação deste conjunto de comandos do Office 365 PowerShell é:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-163">The interpretation of this set of Office 365 PowerShell commands is:</span></span>
- <span data-ttu-id="2d1d7-164">Obter todos os usuários na assinatura atual do Office 365 e armazenar as informações em uma variável chamada $x (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-164">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="2d1d7-165">Exibir o conteúdo da variável $x, mas incluir apenas o nome e o local para cada usuário (**$x | Select DisplayName, UsageLocation**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-165">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="2d1d7-166">O Office 365 tem recursos que você pode configurar apenas com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d1d7-166">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>

<span data-ttu-id="2d1d7-167">O centro de administração do Microsoft 365 destina-se a fornecer acesso às tarefas administrativas mais comuns ou significativas que se aplicam à maioria das pessoas.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-167">The Microsoft 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people.</span></span> <span data-ttu-id="2d1d7-168">Em outras palavras, o centro de administração do Microsoft 365 foi projetado para que o administrador típico pudesse usar a ferramenta para realizar as tarefas de gerenciamento mais comuns.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-168">In other words, the Microsoft 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks.</span></span> <span data-ttu-id="2d1d7-169">Por essa definição, isso significa que há algumas tarefas que não podem ser concluídas usando o centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-169">By this definition, that means that there are some tasks that can't be completed by using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="2d1d7-170">Por exemplo, o Centro de administração Skype for Business online fornece algumas opções para criar convites personalizados para reunião:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-170">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![Exemplo da exibição de convites de reunião personalizados no Centro de administração do Skype for Business Online.](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="2d1d7-p113">Com essas configurações, você pode adicionar um toque de personalização e profissionalismo a convites de reunião. No entanto, há muito mais configurações de reunião do que simplesmente criar convites personalizados de reunião. Por exemplo, por padrão, as reuniões permitem:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p113">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="2d1d7-175">Usuários anônimos obterem entrada automática para cada reunião.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-175">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="2d1d7-176">Participantes gravem a reunião.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-176">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="2d1d7-177">Todos os usuários da sua organização serem designado como apresentadores quando eles entrarem na reunião.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-177">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="2d1d7-p114">Essas configurações não estão disponíveis no Centro de administração do Skype for Business online. No entanto, você pode controlá-las no Office 365 PowerShell. Veja um comando que desabilita essas três configurações:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p114">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="2d1d7-181">Este comando requer que você instale o [Módulo do PowerShell Skype for Business Online ](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-181">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="2d1d7-182">A interpretação deste comando do Office 365 PowerShell é: para obter as configurações para novas reuniões do Skype for Business Online ( **Set-CsMeetingConfiguration** ), desabilite a permissão para que usuários anônimos obtenham entrada automática para reuniões ( **- AdmitAnonymousUsersByDefault $False** ), desabilite a capacidade dos participantes de gravarem reuniões ( **- AllowConferenceRecording $False** ) e não defina todos os usuários da sua organização como apresentadores ( **- DesignateAsPresenter "None"** ).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-182">The interpretation of this Office 365 PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="2d1d7-183">Se você mudar de ideia e desejar restaurar essas configurações padrão (todas são ativadas), execute este comando:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-183">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="2d1d7-p115">Isso é apenas um exemplo. Existem outros, é por isso que você, como administrador do Office 365, precisa estar familiarizado com a execução de comandos do Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p115">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="2d1d7-186">O Office 365 PowerShell é ideal para realizar operações em massa</span><span class="sxs-lookup"><span data-stu-id="2d1d7-186">Office 365 PowerShell is great at carrying out bulk operations</span></span>

<span data-ttu-id="2d1d7-187">Historicamente, interfaces visuais como o centro de administração do Microsoft 365 são mais valiosas quando você tem uma única operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-187">Historically, visual interfaces like the Microsoft 365 admin center are most valuable when you have a single operation to perform.</span></span> <span data-ttu-id="2d1d7-188">Por exemplo, se for necessário desabilitar uma conta de usuário, você poderá usar o centro de administração do Microsoft 365 para localizar e desmarcar rapidamente uma caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-188">For example, if you need to disable one user account, you can use the Microsoft 365 admin center to quickly locate and clear a checkbox.</span></span> <span data-ttu-id="2d1d7-189">Isso pode ser mais simples do que executar uma operação semelhante no Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-189">This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="2d1d7-190">Mas se você precisar alterar muitas coisas ou algumas coisas selecionadas dentro de um grande conjunto de outras coisas, o centro de administração do Microsoft 365 pode não ser o melhor uso do tempo.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-190">But if you have to change many things or some selected things within a large set of other things, the Microsoft 365 admin center might not be the best use of your time.</span></span> <span data-ttu-id="2d1d7-191">Por exemplo, se você tivesse que alterar o prefixo em milhares de números de telefone ou você precisava remover um usuário específico, Ken Myer, de todos os seus sites do SharePoint Online, como faria isso no centro de administração do Microsoft 365?</span><span class="sxs-lookup"><span data-stu-id="2d1d7-191">For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Microsoft 365 admin center?</span></span>
  
<span data-ttu-id="2d1d7-192">Para o último exemplo, você tem centenas de sites do SharePoint Online e não sabe nem mesmo saber quais são os que Ken Araújo é membro.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-192">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member.</span></span> <span data-ttu-id="2d1d7-193">Isso significa que você terá que começar no centro de administração do Microsoft 365 e, em seguida, executar este procedimento para cada site:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-193">That means you'll have to start at the Microsoft 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="2d1d7-194">Clicar na **URL** do site.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-194">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="2d1d7-195">Na caixa **Propriedades da coleção de sites**, clicar no link **Endereço de Site da Web** para abrir o site.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-195">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="2d1d7-196">No site, clicar em **Compartilhar**.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-196">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="2d1d7-197">Na caixa de diálogo **Compartilhar** clicar no link que mostra a você todos os usuários que têm permissão para o site:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-197">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![Exemplo de como exibir os membros de um site do SharePoint Online no Centro de administração do SharePoint Online.](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="2d1d7-199">Na caixa de diálogo **Compartilhado com** clicar em **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-199">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="2d1d7-200">Rolar pela lista de usuários, encontrar e selecionar Paulo Araújo (supondo que ele tem permissões para o site) e então clicar em **Remover Permissões do Usuário**.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-200">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="2d1d7-201">Pode demorar muito tempo para você fazer isso em uma centena de sites.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-201">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="2d1d7-202">A alternativa é usar o Office 365 PowerShell e o comando a seguir para remover Paulo Araújo de todos os sites:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-202">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="2d1d7-203">Este comando requer que você instale o [Conectar ao PowerShell do SharePoint Online](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-203">This command requires that you install the [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="2d1d7-204">A interpretação deste comando do Office 365 PowerShell é: obtenha todos os sites do SharePoint na assinatura atual do Office 365 ( **Get-SPOSite** ) e, em cada site, remova Paulo Araújo da lista de usuários que podem acessá-los ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-204">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="2d1d7-205">Como estamos dizendo para o Office 365 para remover Ken Araújo de todos os sites, incluindo aqueles que não têm acesso, a exibição desse comando mostrará erros para aqueles sites nos quais ele não tem acesso no momento.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-205">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access.</span></span> <span data-ttu-id="2d1d7-206">Podemos usar uma condição adicional nesse comando para remover Paulo Araújo somente de sites com ele esteja na lista de login, mas os erros listados não provocam danos aos sites.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-206">We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves.</span></span> <span data-ttu-id="2d1d7-207">Este comando pode levar alguns minutos para ser executado em centenas de sites, em vez de horas de trabalho por meio do centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-207">This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="2d1d7-p120">Este é outro exemplo de operação em massa. Use este comando para adicionar Mila Moraes, uma nova administradora do SharePoint, para todos os sites na organização:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p120">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="2d1d7-210">A interpretação deste comando do Office 365 PowerShell é: obter todos os sites do SharePoint na assinatura atual do Office 365 e, em cada site, permitir o acesso de Mila Moraes adicionando o nome de logon dela ao grupo Membros do site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "mmoraes@litwareinc.com" -Group "Members"}** ).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-210">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="2d1d7-211">O Office 365 PowerShell é ótimo na filtragem de dados</span><span class="sxs-lookup"><span data-stu-id="2d1d7-211">Office 365 PowerShell is great at filtering data</span></span>

<span data-ttu-id="2d1d7-212">O centro de administração do Microsoft 365 fornece várias maneiras diferentes de filtrar seus dados para localizar de forma rápida e fácil um subconjunto de informações direcionado.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-212">The Microsoft 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information.</span></span> <span data-ttu-id="2d1d7-213">Por exemplo, o Exchange facilita a filtragem de praticamente qualquer propriedade da caixa de correio de um usuário.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-213">For example, Exchange makes it easy to filter on practically any property of a user mailbox.</span></span> <span data-ttu-id="2d1d7-214">Por exemplo, esta é uma lista de caixas de correio para todos os usuários que moram em Belo Horizonte:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-214">For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![Exemplo de uma pesquisa avançada no centro de administração do Microsoft 365 para a lista de caixas de correio para todos os usuários que moram na cidade do belo horizonte.](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="2d1d7-p122">O Centro de administração do Exchange também permite que você combine critérios de filtro. Por exemplo, você pode encontrar as caixas de correio para todas as pessoas que moram em Belo Horizonte e que trabalham no departamento financeiro.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p122">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="2d1d7-p123">No entanto, existem limitações no que você pode fazer no Centro de administração do Exchange. Por exemplo, talvez você queira localizar caixas de correio de quem mora em Belo Horizonte ou Curitiba ou caixas de correio para todas as pessoas que não moram em Belo Horizonte.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p123">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="2d1d7-220">Com o Office 365 PowerShell, você pode obter uma lista de caixas de correio de todas as pessoas que vivem nas cidades de Belo Horizonte ou Curitiba com este comando:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-220">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="2d1d7-221">Este é um exemplo de exibição:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-221">Here is an example of the display:</span></span>
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  <span data-ttu-id="2d1d7-222">A interpretação deste comando do Office 365 PowerShell é: obter todos os usuários na assinatura atual do Office 365 que têm uma caixa de correio nas cidades de Curitiba ou Belo Horizonte ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "Curitiba" -or $\_.City -eq "Belo Horizonte")}** ), em seguida, exibir o nome e a cidade de cada um ( **Select DisplayName, City** ).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-222">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="2d1d7-223">Este é o comando para listar todas as caixas de correio de quem mora em qualquer lugar, exceto Belo Horizonte:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-223">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="2d1d7-224">Este é um exemplo de exibição:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-224">Here is an example of the display:</span></span>
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  <span data-ttu-id="2d1d7-225">A interpretação deste comando do Office 365 PowerShell é: obter todos os usuários na assinatura atual do Office 365 com uma caixa de correio não localizada na cidade de Belo Horizonte ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Belo Horizonte"}** ), em seguida, exibir o nome e a cidade de cada um.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-225">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="2d1d7-p124">Você também pode usar caracteres curinga nos seus filtros do Office 365 PowerShell para corresponder a parte de um nome. Por exemplo, suponha que você esteja procurando uma conta de usuário e tudo aquilo que você consegue se lembrar é que o sobrenome é Mendes, ou talvez seja Gonçalves ou quem sabe Gomes.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p124">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="2d1d7-228">Você pode rastrear esse usuário no centro de administração do Microsoft 365 usando a ferramenta de pesquisa e executando três pesquisas diferentes:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-228">You could track down that user in the Microsoft 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="2d1d7-229">Uma para  *Mendes*</span><span class="sxs-lookup"><span data-stu-id="2d1d7-229">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="2d1d7-230">Uma para  *Gonçalves*</span><span class="sxs-lookup"><span data-stu-id="2d1d7-230">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="2d1d7-231">Uma para  *Gomes*</span><span class="sxs-lookup"><span data-stu-id="2d1d7-231">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="2d1d7-p125">Como todos esses três nomes terminam em "es", você pode dizer ao Office 365 PowerShell para exibir todos os usuários cujos nomes terminam em "es". Este é o comando:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p125">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="2d1d7-p126">A interpretação deste comando do Office 365 PowerShell é: obter todos os usuários na assinatura atual do Office 365, mas usar um filtro que lista apenas os usuários cujos sobrenomes terminam em "es" ( **-Filter '{LastName -like "\*son"}'** ). O \* representa qualquer conjunto de caracteres, que são as letras no caso do sobrenome do usuário.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p126">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ). The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="2d1d7-236">O Office 365 PowerShell torna mais fácil imprimir ou salvar dados</span><span class="sxs-lookup"><span data-stu-id="2d1d7-236">Office 365 PowerShell makes it easy to print or save data</span></span>

<span data-ttu-id="2d1d7-237">O centro de administração 365 da Microsoft permite exibir listas de dados.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-237">The Microsoft 365 admin center lets you view lists of data.</span></span> <span data-ttu-id="2d1d7-238">Veja um exemplo do centro de administração do Skype for Business online que exibe uma lista de usuários que foram habilitados para o Skype for Business Online:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-238">Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![Exemplo do Centro de administração do Skype for Business Online exibindo uma lista de usuários que foram habilitados para o Skype for Business Online.](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="2d1d7-240">Para salvar essas informações em um arquivo, você deve copiá-lo e colá-lo em um documento ou no Excel.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-240">To save that information to a file, you must copy and paste it into a document or Excel.</span></span> <span data-ttu-id="2d1d7-241">Em ambos os casos, a cópia pode exigir uma formatação adicional.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-241">In either case, the copy might require additional formatting.</span></span> <span data-ttu-id="2d1d7-242">Além disso, o centro de administração do Microsoft 365 não oferece uma maneira de imprimir diretamente a lista exibida.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-242">Additionally, the Microsoft 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="2d1d7-p129">Felizmente, você pode usar o Office 365 PowerShell para exibir não apenas uma lista, mas para salvá-la em um arquivo que pode ser facilmente importado para o Excel. Este é um exemplo do comando para salvar dados do usuário do Skype for Business online em valores separados por vírgula (CSV), um arquivo que pode ser facilmente importado como uma tabela em uma planilha do Excel:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p129">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="2d1d7-245">Este é um exemplo de exibição:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-245">Here is an example of the display:</span></span>
  
![Exemplo de uma tabela importada para uma planilha do Excel para os dados do usuário do Skype for Business Online que foram salvos em um arquivo de valores separados por vírgula (CSV).](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="2d1d7-247">A interpretação deste comando do Office 365 PowerShell é: obter todos os usuários do Skype for Business Online na assinatura atual do Office 365 ( **Get-CsOnlineUser** ), obter apenas o nome de usuário, o UPN e o local ( **Select DisplayName, UserPrincipalName, UsageLocation** ) e, em seguida, salvar informações no arquivo CSV chamado C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" - NoTypeInformation** ).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-247">The interpretation of this Office 365 PowerShell command is: Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="2d1d7-p130">Você também pode usar opções para salvar a lista como um arquivo XML ou como uma página HTML. Na verdade, com os comandos adicionais do PowerShell, você poderia salvá-la diretamente como um arquivo do Excel, com qualquer formatação personalizada desejada.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p130">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="2d1d7-p131">Você também pode enviar a saída de um comando do Office 365 PowerShell que exibe uma lista diretamente para a impressora padrão no Windows. Este é um exemplo de comando:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p131">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="2d1d7-252">O seu documento impresso ficará assim:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-252">Here's what your printed document will look like:</span></span>
  
![Exemplo de um documento impresso que foi a saída de um comando do Office 365 PowerShell listado diretamente para a impressora padrão no Windows.](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="2d1d7-254">A interpretação deste comando do Office 365 PowerShell é: obter todos os usuários do Skype for Business Online na assinatura atual do Office 365, obter apenas o nome de usuário, o UPN e o local e enviá-las para a impressora padrão do Windows ( **Out-Printer** ).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-254">The interpretation of this Office 365 PowerShell command is:  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="2d1d7-255">O documento impresso tem a mesma formatação simples exibida dentro da janela de comando do Office 365 PowerShell, mas após ter criado um comando do Office 365 PowerShell para listar o que você precisa, basta adicionar **| Out-Printer** no final do comando para obter uma cópia para trabalhar.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-255">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="2d1d7-256">O Office 365 PowerShell permite que você gerencie produtos de servidor</span><span class="sxs-lookup"><span data-stu-id="2d1d7-256">Office 365 PowerShell lets you manage across server products</span></span>

<span data-ttu-id="2d1d7-p132">Os diferentes componentes que compõem o Office 365 são projetados para trabalhar juntos. Por exemplo, suponha que você adicionou um novo usuário ao Office 365 e, ao fazer isso, você especificou informações como o departamento e o telefone desse usuário. Essas informações estarão disponíveis se você acessar as informações do usuário de qualquer um dos produtos de servidor do Office 365: Skype for Business online, Exchange, ou SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p132">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="2d1d7-p133">Mas isso se trata de informações genéricas que existem em todo o conjunto de produtos. Informações específicas do produto, por exemplo, as informações sobre uma caixa de correio do Exchange do usuário, geralmente não estão disponíveis em todo o pacote. Por exemplo, se você deseja saber se a caixa de correio do usuário está habilitada ou não, essas informações estão disponíveis somente no Centro de administração do Exchange.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p133">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="2d1d7-263">Suponha que você queira fazer um relatório que mostre as seguintes informações sobre todos os seus usuários:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-263">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="2d1d7-264">O nome de exibição do usuário</span><span class="sxs-lookup"><span data-stu-id="2d1d7-264">The user's display name</span></span>
    
- <span data-ttu-id="2d1d7-265">Se o usuário tem uma licença para o Office 365</span><span class="sxs-lookup"><span data-stu-id="2d1d7-265">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="2d1d7-266">Se a caixa de correio do Exchange do usuário está habilitada</span><span class="sxs-lookup"><span data-stu-id="2d1d7-266">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="2d1d7-267">Se o usuário está habilitado para o Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="2d1d7-267">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="2d1d7-268">No momento, você não pode usar o centro de administração do Microsoft 365 para produzir um relatório desse tipo com facilidade.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-268">You currently cannot use the Microsoft 365 admin center to easily produce such a report.</span></span> <span data-ttu-id="2d1d7-269">Em vez disso, você precisará criar um documento separado para armazenar as informações, como uma planilha do Excel e obter todos os nomes de usuário e informações de licenciamento do centro de administração do Microsoft 365, obter informações de caixa de correio do centro de administração do Exchange, obter o Skype for Informações do Business Online do centro de administração do Skype for Business Online e, em seguida, agrupar e combinar essas informações.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-269">Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Microsoft 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="2d1d7-270">A alternativa é usar um script do Office 365 PowerShell para compilar esse relatório para você.</span><span class="sxs-lookup"><span data-stu-id="2d1d7-270">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="2d1d7-p135">O script de exemplo a seguir é mais complicado do que os comandos que vimos até agora neste artigo. Mas, mostra a possibilidade de usar o Office 365 PowerShell para criar modos de exibição de informações que são muito difíceis de serem feitos de outra maneira. Aqui está o script que pode compilar e exibir a lista necessária:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-p135">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
```powershell
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="2d1d7-274">Este é um exemplo de exibição:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-274">Here is an example of the display:</span></span>
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="2d1d7-275">A interpretação deste script do Office 365 PowerShell é:</span><span class="sxs-lookup"><span data-stu-id="2d1d7-275">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="2d1d7-276">Obter todos os usuários na assinatura atual do Office 365 e armazenar as informações em uma variável chamada $x (**$x = Get-MsolUser**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-276">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="2d1d7-277">Iniciar um loop que é executado em todos os usuários na variável denominada $x (**foreach ($i in $x)**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-277">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="2d1d7-278">Definir uma variável chamada $y e armazenar as informações da caixa de correio do usuário nela (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-278">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="2d1d7-279">Adicionar uma nova propriedade à informação do usuário chamada IsMailBoxEnabled e configurá-la para o valor da propriedade IsMailBoxEnabled da caixa de correio do usuário (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-279">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="2d1d7-280">Definir uma variável chamada $y e armazenar as informações do usuário do Skype for Business Online nela (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-280">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="2d1d7-281">Adicionar uma nova propriedade à informação do usuário chamada EnabledForSfB e configurá-la para o valor da propriedade Habilitada das informações do usuário do Skype for Business Online (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-281">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="2d1d7-282">Exibir a lista de usuários, mas incluir apenas os nomes, informar se eles estão licenciados e incluir as duas novas propriedades que indicam se as caixas de correio deles estão ativadas e se elas estão habilitadas para o Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span><span class="sxs-lookup"><span data-stu-id="2d1d7-282">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2d1d7-283">Veja também</span><span class="sxs-lookup"><span data-stu-id="2d1d7-283">See also</span></span>

[<span data-ttu-id="2d1d7-284">Introdução ao Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d1d7-284">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="2d1d7-285">Gerenciar contas de usuário e licenças usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d1d7-285">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="2d1d7-286">Use o Windows PowerShell para criar relatórios no Office 365</span><span class="sxs-lookup"><span data-stu-id="2d1d7-286">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

