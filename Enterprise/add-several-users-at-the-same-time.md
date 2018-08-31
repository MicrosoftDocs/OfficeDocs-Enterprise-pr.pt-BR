---
title: Adicionar vários usuários ao mesmo tempo no Office 365 – Ajuda para Administradores
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: 'Saiba como adicionar o arquivo formatado de vários usuários para o Office 365 para empresas de uma lista em uma planilha ou outro CSV. Assista a um vídeo sobre como YouTube que explica como adicionar contas para o Office 365. Ao final desse processo, cada usuário com uma conta terá uma caixa de correio do Office 365. '
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539185"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="d1402-105">Adicionar vários usuários ao mesmo tempo no Office 365 – Ajuda para Administradores</span><span class="sxs-lookup"><span data-stu-id="d1402-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="d1402-p102">Cada pessoa da sua equipe precisa de uma conta de usuário antes que eles possam entrar e acessar os serviços do Office 365, como email e escritório. Se você tiver muitas pessoas, você pode adicionar suas contas ao mesmo tempo de uma planilha do Excel ou outro arquivo salvo no formato CSV. [é não tem certeza de qual formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="d1402-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a><span data-ttu-id="d1402-109">Adicionar vários usuários para o Office 365 no Centro de administração do Office 365</span><span class="sxs-lookup"><span data-stu-id="d1402-109">Add multiple users to Office 365 in the Office 365 admin center</span></span>

1. <span data-ttu-id="d1402-110">Entre no Office 365 com sua conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="d1402-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="d1402-111">No Centro de administração do Office 365, escolha **usuários** \> **usuários ativos**.</span><span class="sxs-lookup"><span data-stu-id="d1402-111">In the Office 365 admin center, choose **Users** \> **Active users**.</span></span>
    
    ![No Centro de administração, escolha usuários e, em seguida, ativa](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. <span data-ttu-id="d1402-113">No menu suspenso **mais** , escolha **importar vários usuários**.</span><span class="sxs-lookup"><span data-stu-id="d1402-113">In the **More** drop-down, choose **Import multiple users**.</span></span>
    
4. <span data-ttu-id="d1402-114">No painel **importar vários usuários** , você pode opcionalmente baixar um arquivo CSV de exemplo com ou sem dados de amostra preenchidos.</span><span class="sxs-lookup"><span data-stu-id="d1402-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![No menu suspenso mais, escolha Importar vários usuários](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="d1402-116">Sua planilha precisa incluir os **títulos de colunas de mesma exato** como o exemplo de um (nome de usuário, nome, etc...). Se você usar o modelo, abri-lo em uma ferramenta de edição de texto, como o bloco de notas e considere deixando todos os dados na linha 1 sozinhos e apenas inserem dados nas linhas 2 e abaixo.</span><span class="sxs-lookup"><span data-stu-id="d1402-116">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="d1402-117">Sua planilha também precisa incluir valores para o nome de usuário (como bob@contoso.com) e um nome de exibição (como Bob Kelly) para cada usuário.</span><span class="sxs-lookup"><span data-stu-id="d1402-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="d1402-118">Insira um caminho de arquivo na caixa ou escolha **Procurar** para navegar até o local do arquivo CSV, depois escolha **Verificar**.</span><span class="sxs-lookup"><span data-stu-id="d1402-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Seu arquivo CSV é verificado](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="d1402-p103">Se houver problemas com o arquivo, o problema é exibido no painel. Você também pode baixar um arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="d1402-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
6. <span data-ttu-id="d1402-122">Na caixa de diálogo **definir opções de usuário** , você pode definir o status de entrada e escolha a licença do produto que será atribuída a todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="d1402-122">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
7. <span data-ttu-id="d1402-123">Na caixa de diálogo **Exibir seu resultado** , você pode optar por enviar os resultados para si mesmo ou outros usuários (serão senhas em texto sem formatação) e você pode ver quantos usuários foram criados, e se você precisar comprar mais licenças para atribuir a alguns dos novos usuários.</span><span class="sxs-lookup"><span data-stu-id="d1402-123">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="d1402-124">Assista ao vídeo</span><span class="sxs-lookup"><span data-stu-id="d1402-124">Watch the video</span></span>
<span data-ttu-id="d1402-125"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="d1402-125"></span></span>

 <span data-ttu-id="d1402-126">Assista a um vídeo rápido que mostra como em massa adicionar usuários.</span><span class="sxs-lookup"><span data-stu-id="d1402-126">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="d1402-127">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d1402-127">Next steps</span></span>
<span data-ttu-id="d1402-128"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="d1402-128"></span></span>

- <span data-ttu-id="d1402-p104">Agora que essas pessoas têm contas, precisam [baixar e instalar ou reinstala o Office 365 ou 2016 do Office em um PC ou Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Cada pessoa da sua equipe pode instalar o Office 365 em até 5 computadores ou Macs.</span><span class="sxs-lookup"><span data-stu-id="d1402-p104">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="d1402-p105">Cada pessoa também pode [Configurar os aplicativos do Office e email em um dispositivo móvel](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) em até 5 tablets e 5 telefones, como iPhones, iPads e Android telefones e tablets. Dessa forma, que eles podem editar arquivos do Office em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="d1402-p105">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets. This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="d1402-133">Para obter uma lista de ponta a ponta das etapas de instalação, consulte [Configurar o Office 365 para empresas](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) .</span><span class="sxs-lookup"><span data-stu-id="d1402-133">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="d1402-134">Para obter mais informações sobre como adicionar usuários ao Office 365</span><span class="sxs-lookup"><span data-stu-id="d1402-134">More information about how to add users to Office 365</span></span>
<span data-ttu-id="d1402-135"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="d1402-135"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="d1402-136">Não tem certeza que formato CSV é?</span><span class="sxs-lookup"><span data-stu-id="d1402-136">Not sure what CSV format is?</span></span>
<span data-ttu-id="d1402-137"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="d1402-137"></span></span>

<span data-ttu-id="d1402-p106">Um arquivo CSV é um arquivo com valores separados por vírgulas. Você pode criar ou editar um arquivo com qualquer editor de texto ou de um programa de planilha, como o Excel.</span><span class="sxs-lookup"><span data-stu-id="d1402-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="d1402-p107">Você pode baixar [essa planilha de exemplo](https://www.microsoft.com/en-us/download/details.aspx?id=45485) como um ponto de partida. Lembre-se de que o Office 365 exige títulos de coluna na primeira linha portanto não substituí-los por algo diferente.</span><span class="sxs-lookup"><span data-stu-id="d1402-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="d1402-142">Salve o arquivo com um novo nome e especifique o formato CSV.</span><span class="sxs-lookup"><span data-stu-id="d1402-142">Save the file with a new name, and specify CSV format.</span></span>
  
![Uma imagem de como salvar um arquivo no Excel, no formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="d1402-p108">Quando você salva o arquivo, você provavelmente receberá um prompt de que alguns recursos na sua pasta de trabalho serão perdidos se você salvar o arquivo no formato CSV. Isso é okey. Clique em **Sim** para continuar.</span><span class="sxs-lookup"><span data-stu-id="d1402-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Uma imagem do aviso de que você pode obter do Excel perguntando se você realmente deseja salvar o arquivo como um formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="d1402-148">Dicas para formatar sua planilha</span><span class="sxs-lookup"><span data-stu-id="d1402-148">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="d1402-149"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="d1402-149"></span></span>

- <span data-ttu-id="d1402-p109">**eu preciso os mesmos títulos de coluna como a planilha de amostra?** Sim. A planilha de exemplo contém os títulos de coluna na primeira linha. Estes títulos são necessários. Para cada usuário que você deseja adicionar ao Office 365, crie uma linha sob o título. Se você adicionar, alterar ou excluir qualquer um dos títulos de coluna, Office 365 pode não ser capaz de criar usuários das informações no arquivo do.</span><span class="sxs-lookup"><span data-stu-id="d1402-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="d1402-p110">**o que ocorre se eu não tenho todas as informações necessárias para cada usuário?** O nome de usuário e o nome de exibição são necessários, e você não pode adicionar um novo usuário sem essas informações. Se você não possui algumas das outras informações, como o fax, você pode usar um espaço, além de uma vírgula para indicar que o campo deve permanecer em branco.</span><span class="sxs-lookup"><span data-stu-id="d1402-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="d1402-p111">* * Como pequeno ou grande pode ser a planilha? * * A planilha deve ter pelo menos duas linhas. Um é para os títulos de coluna (o usuário coluna rótulo de dados) e outra para o usuário. Você não pode ter mais de 251 linhas. Se você precisar importar mais de 250 usuários, você pode criar mais de uma planilha.</span><span class="sxs-lookup"><span data-stu-id="d1402-p111">** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="d1402-p112">* * Quais idiomas pode usar? * * Quando você criar sua planilha, você pode inserir rótulos de coluna de dados de usuário em qualquer idioma ou caracteres, mas você não deve alterar a ordem dos rótulos, conforme mostrado no exemplo. Você pode fazer com que entradas para os campos, usando qualquer idioma ou caracteres e salve o arquivo em um formato Unicode ou UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d1402-p112">** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="d1402-p113">**o que ocorre se eu estou adicionando usuários de diferentes países ou regiões?** Crie uma planilha separada para cada área. Você precisará percorrer o grosso Assistente para adicionar usuários qual cada planilha, oferecendo um único local de todos os usuários incluídos no arquivo que você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="d1402-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="d1402-p114">**Existe um limite para o número de caracteres que eu posso usar?** A tabela a seguir mostra os rótulos de coluna de dados de usuário e o comprimento máximo de caracteres para cada da planilha de amostra.</span><span class="sxs-lookup"><span data-stu-id="d1402-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="d1402-172">**Rótulo de coluna de dados de usuário**</span><span class="sxs-lookup"><span data-stu-id="d1402-172">**User data column label**</span></span>|<span data-ttu-id="d1402-173">**Comprimento máximo de caracteres**</span><span class="sxs-lookup"><span data-stu-id="d1402-173">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d1402-174">Nome de usuário (obrigatório)</span><span class="sxs-lookup"><span data-stu-id="d1402-174">User Name (Required)</span></span>  <br/> |<span data-ttu-id="d1402-p115">incluindo 79 o sinal de arroba (@), em name@domain o formato. \<extensão\>. O alias do usuário não pode exceder 30 caracteres e o nome de domínio não pode exceder 48 caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1402-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="d1402-177">Nome</span><span class="sxs-lookup"><span data-stu-id="d1402-177">First Name</span></span>  <br/> |<span data-ttu-id="d1402-178">64</span><span class="sxs-lookup"><span data-stu-id="d1402-178">64</span></span>  <br/> |
|<span data-ttu-id="d1402-179">Sobrenome</span><span class="sxs-lookup"><span data-stu-id="d1402-179">Last Name</span></span>  <br/> |<span data-ttu-id="d1402-180">64</span><span class="sxs-lookup"><span data-stu-id="d1402-180">64</span></span>  <br/> |
|<span data-ttu-id="d1402-181">Nome para exibição (obrigatório)</span><span class="sxs-lookup"><span data-stu-id="d1402-181">Display Name (required)</span></span>  <br/> |<span data-ttu-id="d1402-182">256</span><span class="sxs-lookup"><span data-stu-id="d1402-182">256</span></span>  <br/> |
|<span data-ttu-id="d1402-183">Cargo</span><span class="sxs-lookup"><span data-stu-id="d1402-183">Job Title</span></span>  <br/> |<span data-ttu-id="d1402-184">64</span><span class="sxs-lookup"><span data-stu-id="d1402-184">64</span></span>  <br/> |
|<span data-ttu-id="d1402-185">Departamento</span><span class="sxs-lookup"><span data-stu-id="d1402-185">Department</span></span>  <br/> |<span data-ttu-id="d1402-186">64</span><span class="sxs-lookup"><span data-stu-id="d1402-186">64</span></span>  <br/> |
|<span data-ttu-id="d1402-187">Número do escritório</span><span class="sxs-lookup"><span data-stu-id="d1402-187">Office Number</span></span>  <br/> |<span data-ttu-id="d1402-188">128</span><span class="sxs-lookup"><span data-stu-id="d1402-188">128</span></span>  <br/> |
|<span data-ttu-id="d1402-189">Telefone Comercial</span><span class="sxs-lookup"><span data-stu-id="d1402-189">Office Phone</span></span>  <br/> |<span data-ttu-id="d1402-190">64</span><span class="sxs-lookup"><span data-stu-id="d1402-190">64</span></span>  <br/> |
|<span data-ttu-id="d1402-191">Celular</span><span class="sxs-lookup"><span data-stu-id="d1402-191">Mobile Phone</span></span>  <br/> |<span data-ttu-id="d1402-192">64</span><span class="sxs-lookup"><span data-stu-id="d1402-192">64</span></span>  <br/> |
|<span data-ttu-id="d1402-193">Fax</span><span class="sxs-lookup"><span data-stu-id="d1402-193">Fax</span></span>  <br/> |<span data-ttu-id="d1402-194">64</span><span class="sxs-lookup"><span data-stu-id="d1402-194">64</span></span>  <br/> |
|<span data-ttu-id="d1402-195">Endereço</span><span class="sxs-lookup"><span data-stu-id="d1402-195">Address</span></span>  <br/> |<span data-ttu-id="d1402-196">1023</span><span class="sxs-lookup"><span data-stu-id="d1402-196">1023</span></span>  <br/> |
|<span data-ttu-id="d1402-197">Cidade</span><span class="sxs-lookup"><span data-stu-id="d1402-197">City</span></span>  <br/> |<span data-ttu-id="d1402-198">128</span><span class="sxs-lookup"><span data-stu-id="d1402-198">128</span></span>  <br/> |
|<span data-ttu-id="d1402-199">Estado ou Província</span><span class="sxs-lookup"><span data-stu-id="d1402-199">State or Province</span></span>  <br/> |<span data-ttu-id="d1402-200">128</span><span class="sxs-lookup"><span data-stu-id="d1402-200">128</span></span>  <br/> |
|<span data-ttu-id="d1402-201">CEP ou código Postal</span><span class="sxs-lookup"><span data-stu-id="d1402-201">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="d1402-202">40</span><span class="sxs-lookup"><span data-stu-id="d1402-202">40</span></span>  <br/> |
|<span data-ttu-id="d1402-203">País ou Região</span><span class="sxs-lookup"><span data-stu-id="d1402-203">Country or Region</span></span>  <br/> |<span data-ttu-id="d1402-204">128</span><span class="sxs-lookup"><span data-stu-id="d1402-204">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="d1402-205">Ainda está com problemas ao adicionar usuários para o Office 365?</span><span class="sxs-lookup"><span data-stu-id="d1402-205">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="d1402-p116">**Verifique novamente se a planilha está formatada corretamente.** Verifique se os títulos de coluna para certificar-se de que haja correspondência com os títulos no arquivo de exemplo. Certifique-se de que você está seguindo as regras de comprimentos de caracteres, e cada campo é separado por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="d1402-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="d1402-p117">* * Se você não vir os novos usuários no Office 365 imediatamente, aguarde alguns minutos. * * Pode demorar um pouco enquanto para alterações vá em todos os serviços no Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1402-p117">** If you don't see the new users in Office 365 right away, wait a few minutes. ** It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a><span data-ttu-id="d1402-211">Adicionar vários usuários para o Office 365 no Centro de administração do Office 365 antigo</span><span class="sxs-lookup"><span data-stu-id="d1402-211">Add multiple users to Office 365 in the old Office 365 admin center</span></span>

1. <span data-ttu-id="d1402-212">Baixe [essa planilha de exemplo](https://www.microsoft.com/en-us/download/details.aspx?id=45485) e abri-lo no Excel.</span><span class="sxs-lookup"><span data-stu-id="d1402-212">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="d1402-213">Sua planilha precisa incluir os **títulos de colunas de mesma exato** como o exemplo de um (nome de usuário, nome, etc...). Se você usar o modelo, considere deixando todos os dados na linha 1 sozinhos e apenas inserem dados nas linhas 2 e abaixo.</span><span class="sxs-lookup"><span data-stu-id="d1402-213">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="d1402-p118">Sua planilha também precisa incluir valores para o nome de usuário (como bob@contoso.com) e um nome de exibição (como Bob Kelly) para cada usuário. Para deixar os outros campos em branco, insira um espaço, além de uma vírgula no campo conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1402-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Um arquivo CVS de amostra que tenha especificadas de linhas em branco](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="d1402-p119">Se você tiver pessoas que trabalham em diferentes países, você precisará criar uma planilha para os usuários em cada país. Por exemplo, uma planilha que lista todas as pessoas que funciona nos EUA e outro que lista todas as pessoas que funciona no Japão. Isso ocorre porque a disponibilidade dos serviços do Office 365 varia por região.</span><span class="sxs-lookup"><span data-stu-id="d1402-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="d1402-p120">**Dica:** Antes de adicionar vários usuários para o Office 365, você talvez queira prática com a planilha de exemplo. Por exemplo, edite a planilha de amostra com os dados de alguns dos seus usuários, diga 5 ou 10 e salve o arquivo com um novo nome. Executar etapas descritas neste procedimento, verifique os resultados e excluir as novas contas e recomece novamente. Dessa forma, que você pode practice obtendo todos o direito de dados à sua situação. Confira também [dicas para formatação de sua planilha](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="d1402-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="d1402-225">Entre no Office 365 com sua conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="d1402-225">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="d1402-226">Vá para o centro de administração do Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1402-226">Go to the Office 365 admin center.</span></span>
    
4. <span data-ttu-id="d1402-p121">Para as pessoas a usar os serviços do Office 365, elas precisam ser atribuiu uma licença. Antes de continuar, talvez você queira Verifique se você tem licenças suficientes para todas as pessoas listadas em sua planilha. Escolha **de faturamento** \> **inscrições** para ver se você tem suficiente. Se você precisar comprar mais licenças, escolha * * alterar a quantidade de licença * *. Ou, você pode executar o assistente e atribuir as licenças que você tiver, compra mais licenças posteriormente e executar novamente o assistente.</span><span class="sxs-lookup"><span data-stu-id="d1402-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose ** Change license quantity **. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="d1402-p122">Agora vá para o grosso Adicionar Assistente para usuários: escolha **usuários** \> **Usuários ativos**. Escolha ![o ícone para a adição de muitos usuários para o Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1402-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Uma imagem da seção usuários do Centro de administração do Office 365](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="d1402-235">A maior parte adicionar usuários assistente aparece e percorre a adição de um grupo de usuários para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1402-235">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="d1402-236">Na etapa 1: selecione um arquivo CSV, especifique seu próprio planilha conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1402-236">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Etapa 1 de em massa adicionar usuários Assistente - arquivo CSV Select](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="d1402-238">Na etapa 2 - verificação, o assistente informa se o conteúdo da planilha está formatado corretamente.</span><span class="sxs-lookup"><span data-stu-id="d1402-238">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Etapa 2 de em massa adicionar usuários Assistente - verificação](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="d1402-p123">Na etapa 3 - configurações, escolha **permitidos** para que as pessoas listadas em sua planilha poderão usar o Office 365. Também escolha o país em que essas pessoas usarão o Office 365. Lembre-se se algumas pessoas na sua organização pretende usar o Office 365 em um país diferente, crie uma planilha separada com seus nomes e executar o grosso Adicionar Assistente usuários novamente para adicioná-los.</span><span class="sxs-lookup"><span data-stu-id="d1402-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Etapa 3 de em massa adicionar usuários Wizard - configurações](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="d1402-244">Página Atribuir licenças informa quantas licenças estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d1402-244">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Etapa 4 do assistente em massa adicionar usuários - licenças](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="d1402-p124">Você pode escolher **comprar mais licenças**, mas você vai deixar em massa adicionar o Assistente para usuários e vá para **faturamento** no Centro de administração do Office 365. Depois de comprar mais licenças, você vai ter que aguarde alguns minutos para a ordem de processamento e iniciar o grosso adicione Assistente para usuários desde o início.</span><span class="sxs-lookup"><span data-stu-id="d1402-p124">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Office 365 admin center. After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="d1402-248">Se você não comprar mais licenças, contas não serão criadas para cada pessoa listada em sua planilha.</span><span class="sxs-lookup"><span data-stu-id="d1402-248">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="d1402-249">Neste exemplo, podemos não comprar mais licenças de qualquer e continuar com a maior parte adicionar o Assistente para usuários.</span><span class="sxs-lookup"><span data-stu-id="d1402-249">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="d1402-250">Na etapa 5 - enviar resultados, digite os endereços de email das pessoas que você deseja obter um email alertando que lista *todos os* do Office 365 nomes de usuário e senhas temporárias para as pessoas na planilha.</span><span class="sxs-lookup"><span data-stu-id="d1402-250">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Etapa 5 de em massa adicionar usuários Assistente - enviar resultados](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="d1402-p125">O seguinte email é enviado a todos os endereços de email que você especificou na etapa 5 - enviar resultados. Este email indica as contas que foram criadas. Observe que as contas não foram criadas para algumas pessoas porque não havia licenças suficientes.</span><span class="sxs-lookup"><span data-stu-id="d1402-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Um exemplo de email com informações de credencial do usuário](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="d1402-p126">Você pode comprar mais licenças posteriormente e novamente em massa Adicionar Assistente para usuários com a mesma planilha. O assistente ignora os usuários que já têm contas; no relatório de resultados, ele indicará que a "nome de usuário duplicado" para indicar a alguém com essas informações já tem uma conta.</span><span class="sxs-lookup"><span data-stu-id="d1402-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="d1402-258">A página final na massa Adicionar Assistente de usuários lista os nomes de usuário e senhas temporárias, conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1402-258">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Etapa 6 em massa adicionar usuários Assistente - enviar resultados](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="d1402-p127">Depois de adicionar usuários ao Office 365, você precisa informá-los sobre suas próprias informações de conta do Office 365. Use o processo normal para a comunicação de novas senhas.</span><span class="sxs-lookup"><span data-stu-id="d1402-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

