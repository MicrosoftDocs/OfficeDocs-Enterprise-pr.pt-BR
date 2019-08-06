---
title: Adicionar vários usuários ao mesmo tempo para o Office 365 - Ajuda da administração
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
audience: Admin
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
description: 'Saiba como adicionar vários usuários ao Office 365 para empresas de uma lista em uma planilha ou outro arquivo formatado por CSV. Assista a um vídeo sobre o YouTube que explica como adicionar contas ao Office 365. No final desse processo, cada usuário com uma conta terá uma caixa de correio do Office 365. '
ms.openlocfilehash: ece3cc6f207b5c0caaa03880da925eb3b6ac2c5b
ms.sourcegitcommit: 6c3003380491fba6dacb299754716901c20ba629
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "36198653"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="26dcb-105">Adicionar vários usuários ao mesmo tempo para o Office 365 – Ajuda da administração</span><span class="sxs-lookup"><span data-stu-id="26dcb-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="26dcb-p102">É necessário que cada pessoa na sua equipe tenha uma conta de usuário para poder entrar e acessar os serviços do Office 365, como o email e o Office. Se houver muitas pessoas, é possível adicionar todas as contas de uma só vez a partir de uma planilha do Excel ou de outro arquivo salvo em formato CSV. [Não sabe o que é o formato CSV?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="26dcb-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="26dcb-109">Adicionar vários usuários ao Office 365 no centro de administração do Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="26dcb-109">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="26dcb-110">Entre no Office 365 com uma conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="26dcb-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="26dcb-111">No centro de administração, escolha usuários **ativos**do **usuário** \> .</span><span class="sxs-lookup"><span data-stu-id="26dcb-111">In the admin center, choose **Users** \> **Active users**.</span></span>
    
    ![No centro de administração, escolha usuários e, em seguida, usuários ativos](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
    
3. <span data-ttu-id="26dcb-113">No painel **Importar vários usuários**, opcionalmente, você pode baixar um arquivo CSV de exemplo com ou sem dados de exemplo preenchidos.</span><span class="sxs-lookup"><span data-stu-id="26dcb-113">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="26dcb-115">A planilha deve incluir **exatamente os mesmos títulos de coluna** que os da planilha de exemplo (Nome de Usuário, Nome, etc...). Se você usar o modelo, abra-o em uma ferramenta de edição de texto, como o Bloco de Notas, e considere a opção de manter todos os dados na linha 1 e inserir dados apenas nas linhas 2 e abaixo.</span><span class="sxs-lookup"><span data-stu-id="26dcb-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="26dcb-116">A planilha também precisa incluir valores de nome de usuário (por exemplo, carlos@contoso.com) e um nome para exibição (por exemplo, Carlos Lima) para cada usuário.</span><span class="sxs-lookup"><span data-stu-id="26dcb-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

4. <span data-ttu-id="26dcb-117">Insira um caminho de arquivo na caixa ou escolha **Procurar** para navegar até o local do arquivo CSV. Em seguida, escolha **Verificar**.</span><span class="sxs-lookup"><span data-stu-id="26dcb-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="26dcb-p103">Se houver algum problema com o arquivo, o problema será exibido no painel. Você também pode baixar um arquivo de log.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="26dcb-121">Na caixa de diálogo **Definir opções do usuário**, você pode definir o status de entrada e escolher a licença de produto que será atribuída a todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="26dcb-121">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="26dcb-122">Na caixa de diálogo **Exibir seu resultado**, você pode optar por enviar os resultados a si mesmo ou a outros usuários (as senhas estarão em texto sem formatação), pode ver quantos usuários foram criados e se precisa comprar mais licenças para atribuir a alguns dos novos usuários.</span><span class="sxs-lookup"><span data-stu-id="26dcb-122">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="26dcb-123">Ver o vídeo</span><span class="sxs-lookup"><span data-stu-id="26dcb-123">Watch the video</span></span>
<span data-ttu-id="26dcb-124"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="26dcb-124"></span></span>

 <span data-ttu-id="26dcb-125">Assista a um vídeo curto que mostra como adicionar usuários em massa.</span><span class="sxs-lookup"><span data-stu-id="26dcb-125">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="26dcb-126">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="26dcb-126">Next steps</span></span>
<span data-ttu-id="26dcb-127"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="26dcb-127"></span></span>

- <span data-ttu-id="26dcb-128">Agora que essas pessoas têm contas, elas precisam [baixar e instalar ou reinstalar o office 365 ou o office 2016 em um PC ou Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span><span class="sxs-lookup"><span data-stu-id="26dcb-128">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="26dcb-129">Cada pessoa de sua equipe pode instalar o Office 365 em até 5 PCs ou Macs.</span><span class="sxs-lookup"><span data-stu-id="26dcb-129">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="26dcb-130">Cada pessoa também pode [configurar os aplicativos do Office e o email em um dispositivo móvel](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) em até 5 tablets e 5 telefones, como iPhones, iPads e telefones e tablets Android.</span><span class="sxs-lookup"><span data-stu-id="26dcb-130">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="26dcb-131">Dessa forma, elas podem editar arquivos do Office em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="26dcb-131">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="26dcb-132">Consulte [Configurar o Office 365 for Business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) para obter uma lista completa das etapas de configuração.</span><span class="sxs-lookup"><span data-stu-id="26dcb-132">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="26dcb-133">Mais informações sobre como adicionar usuários ao Office 365</span><span class="sxs-lookup"><span data-stu-id="26dcb-133">More information about how to add users to Office 365</span></span>
<span data-ttu-id="26dcb-134"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="26dcb-134"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="26dcb-135">Não sabe o que é o formato CSV?</span><span class="sxs-lookup"><span data-stu-id="26dcb-135">Not sure what CSV format is?</span></span>
<span data-ttu-id="26dcb-136"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="26dcb-136"></span></span>

<span data-ttu-id="26dcb-p106">Um arquivo CSV é um arquivo com valores separados por vírgulas. Você pode criar ou editar um arquivo como esse com qualquer editor de texto ou programa de planilha, como o Excel.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="26dcb-p107">Você pode baixar [esta planilha de exemplo](https://www.microsoft.com/en-us/download/details.aspx?id=45485) como ponto de partida. Lembre-se de que o Office 365 requer títulos de coluna na primeira linha; portanto, não os substitua por outra coisa.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="26dcb-141">Salve o arquivo com um novo nome e especifique o formato CSV.</span><span class="sxs-lookup"><span data-stu-id="26dcb-141">Save the file with a new name, and specify CSV format.</span></span>
  
![Uma imagem de como salvar um arquivo em Excel no formato CSV](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="26dcb-p108">Ao salvar o arquivo, você provavelmente receberá um aviso de que alguns recursos da pasta de trabalho serão perdidos se você salvar o arquivo no formato CSV. Não há problema. Clique em **Sim** para continuar.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Uma imagem da solicitação que você poderá receber no Excel para confirmar se deseja salvar o arquivo em formato CSV](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="26dcb-147">Dicas para formatar a sua planilha</span><span class="sxs-lookup"><span data-stu-id="26dcb-147">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="26dcb-148"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="26dcb-148"></span></span>

- <span data-ttu-id="26dcb-p109">**Preciso dos mesmos títulos de coluna como mostrado na planilha de exemplo?** Sim. A planilha de exemplo contém títulos de coluna na primeira linha. Esses títulos são obrigatórios. Para cada usuário que você desejar adicionar ao Office 365, crie uma linha sob o título. Se você adicionar, mudar ou excluir qualquer um dos títulos de coluna, o Office 365 poderá não ser capaz de criar os usuários com base nas informações do arquivo.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="26dcb-p110">**E se eu não tiver todas as informações necessárias sobre cada usuário?** O nome de usuário e o nome para exibição são obrigatórios, e não será possível adicionar um novo usuário sem essas informações. Caso não tenha alguma outra informação, como o fax, use um espaço e uma vírgula para indicar que o campo deve permanecer em branco.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="26dcb-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="26dcb-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="26dcb-p113">**E se eu estiver adicionando usuários de diferentes países ou regiões?** Crie uma planilha separada para cada área. Você precisará percorrer o assistente Adicionar usuários em massa em cada planilha, fornecendo um único local para todos os usuários incluídos no arquivo que você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="26dcb-p114">**Há um limite quanto ao número de caracteres que eu posso usar?** A tabela a seguir mostra os rótulos de colunas de dados de usuário e o respectivo tamanho máximo de caracteres na planilha de exemplo.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="26dcb-171">**Rótulo da coluna de dados do usuário**</span><span class="sxs-lookup"><span data-stu-id="26dcb-171">**User data column label**</span></span>|<span data-ttu-id="26dcb-172">**Comprimento máximo de caracteres**</span><span class="sxs-lookup"><span data-stu-id="26dcb-172">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="26dcb-173">Nome de Usuário (Obrigatório)</span><span class="sxs-lookup"><span data-stu-id="26dcb-173">User Name (Required)</span></span>  <br/> |<span data-ttu-id="26dcb-p115">79 incluindo o sinal (@), no formato de nome@domínio.\<extensão\>. O alias do usuário não pode exceder 30 caracteres e o nome de domínio não pode exceder 48 caracteres.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="26dcb-176">Nome</span><span class="sxs-lookup"><span data-stu-id="26dcb-176">First Name</span></span>  <br/> |<span data-ttu-id="26dcb-177">64</span><span class="sxs-lookup"><span data-stu-id="26dcb-177">64</span></span>  <br/> |
|<span data-ttu-id="26dcb-178">Sobrenome</span><span class="sxs-lookup"><span data-stu-id="26dcb-178">Last Name</span></span>  <br/> |<span data-ttu-id="26dcb-179">64</span><span class="sxs-lookup"><span data-stu-id="26dcb-179">64</span></span>  <br/> |
|<span data-ttu-id="26dcb-180">Nome de Exibição (obrigatório)</span><span class="sxs-lookup"><span data-stu-id="26dcb-180">Display Name (required)</span></span>  <br/> |<span data-ttu-id="26dcb-181">256</span><span class="sxs-lookup"><span data-stu-id="26dcb-181">256</span></span>  <br/> |
|<span data-ttu-id="26dcb-182">Cargo</span><span class="sxs-lookup"><span data-stu-id="26dcb-182">Job Title</span></span>  <br/> |<span data-ttu-id="26dcb-183">64</span><span class="sxs-lookup"><span data-stu-id="26dcb-183">64</span></span>  <br/> |
|<span data-ttu-id="26dcb-184">Departamento</span><span class="sxs-lookup"><span data-stu-id="26dcb-184">Department</span></span>  <br/> |<span data-ttu-id="26dcb-185">64</span><span class="sxs-lookup"><span data-stu-id="26dcb-185">64</span></span>  <br/> |
|<span data-ttu-id="26dcb-186">Número Comercial</span><span class="sxs-lookup"><span data-stu-id="26dcb-186">Office Number</span></span>  <br/> |<span data-ttu-id="26dcb-187">128</span><span class="sxs-lookup"><span data-stu-id="26dcb-187">128</span></span>  <br/> |
|<span data-ttu-id="26dcb-188">Telefone Comercial</span><span class="sxs-lookup"><span data-stu-id="26dcb-188">Office Phone</span></span>  <br/> |<span data-ttu-id="26dcb-189">64</span><span class="sxs-lookup"><span data-stu-id="26dcb-189">64</span></span>  <br/> |
|<span data-ttu-id="26dcb-190">Telefone Celular</span><span class="sxs-lookup"><span data-stu-id="26dcb-190">Mobile Phone</span></span>  <br/> |<span data-ttu-id="26dcb-191">64</span><span class="sxs-lookup"><span data-stu-id="26dcb-191">64</span></span>  <br/> |
|<span data-ttu-id="26dcb-192">Fax</span><span class="sxs-lookup"><span data-stu-id="26dcb-192">Fax</span></span>  <br/> |<span data-ttu-id="26dcb-193">64</span><span class="sxs-lookup"><span data-stu-id="26dcb-193">64</span></span>  <br/> |
|<span data-ttu-id="26dcb-194">Endereço</span><span class="sxs-lookup"><span data-stu-id="26dcb-194">Address</span></span>  <br/> |<span data-ttu-id="26dcb-195">1023</span><span class="sxs-lookup"><span data-stu-id="26dcb-195">1023</span></span>  <br/> |
|<span data-ttu-id="26dcb-196">Cidade</span><span class="sxs-lookup"><span data-stu-id="26dcb-196">City</span></span>  <br/> |<span data-ttu-id="26dcb-197">128</span><span class="sxs-lookup"><span data-stu-id="26dcb-197">128</span></span>  <br/> |
|<span data-ttu-id="26dcb-198">Estado ou Província</span><span class="sxs-lookup"><span data-stu-id="26dcb-198">State or Province</span></span>  <br/> |<span data-ttu-id="26dcb-199">128</span><span class="sxs-lookup"><span data-stu-id="26dcb-199">128</span></span>  <br/> |
|<span data-ttu-id="26dcb-200">CEP</span><span class="sxs-lookup"><span data-stu-id="26dcb-200">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="26dcb-201">40</span><span class="sxs-lookup"><span data-stu-id="26dcb-201">40</span></span>  <br/> |
|<span data-ttu-id="26dcb-202">País ou Região</span><span class="sxs-lookup"><span data-stu-id="26dcb-202">Country or Region</span></span>  <br/> |<span data-ttu-id="26dcb-203">128</span><span class="sxs-lookup"><span data-stu-id="26dcb-203">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="26dcb-204">Ainda com problemas ao adicionar usuários ao Office 365?</span><span class="sxs-lookup"><span data-stu-id="26dcb-204">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="26dcb-p116">**Verifique se o arquivo está formatado corretamente.** Verifique se os títulos das colunas correspondem àqueles do arquivo de exemplo. Você deverá seguir as regras de tamanho de caracteres e verificar se cada campo está separado por uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="26dcb-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-admin-center"></a><span data-ttu-id="26dcb-210">Adicionar vários usuários ao Office 365 no centro de administração antigo</span><span class="sxs-lookup"><span data-stu-id="26dcb-210">Add multiple users to Office 365 in the old admin center</span></span>

1. <span data-ttu-id="26dcb-211">Baixe [esta planilha de exemplo](https://www.microsoft.com/en-us/download/details.aspx?id=45485) e abra-a no Excel.</span><span class="sxs-lookup"><span data-stu-id="26dcb-211">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="26dcb-212">A planilha deve incluir **exatamente os mesmos títulos de coluna** que os da planilha de exemplo (Nome de Usuário, Nome, etc...). Se você usar o modelo, considere a opção de manter todos os dados na linha 1 e inserir dados apenas nas linhas 2 e abaixo.</span><span class="sxs-lookup"><span data-stu-id="26dcb-212">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="26dcb-p118">A planilha também precisa incluir os valores para o nome de usuário (por exemplo, carlos@contoso.com) e um nome para exibição (por exemplo, Carlos Lima) para cada usuário. Para deixar os outros campos em branco, insira um espaço e uma vírgula no campo, conforme mostrado na figura abaixo.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![Um modelo de arquivo CVS com linhas em branco especificadas](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="26dcb-p119">Se você tiver pessoas trabalhando em diferentes países/regiões, precisará criar uma planilha para os usuários em cada país/região. Por exemplo, uma planilha que lista todas as pessoas que vivem nos EUA e outra que lista todos os que vivem no Japão. Isso é necessário porque a disponibilidade dos serviços do Office 365 varia em cada região.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="26dcb-p120">**Dica:** antes de adicionar um grande número de usuários ao Office 365, talvez você queira praticar com uma planilha de exemplo. Por exemplo, edite a planilha de exemplo com dados de alguns dos seus usuários, talvez 5 ou 10, e salve o arquivo com um novo nome. Execute as etapas descritas neste procedimento, verifique os resultados, exclua as novas contas e comece novamente. Dessa forma, você pode praticar como obter todos os dados corretos para a sua situação. Confira também [Dicas para formatar a sua planilha](add-several-users-at-the-same-time.md#__toc314595848).</span><span class="sxs-lookup"><span data-stu-id="26dcb-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="26dcb-224">Entre no Office 365 com uma conta corporativa ou de estudante.</span><span class="sxs-lookup"><span data-stu-id="26dcb-224">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="26dcb-225">Vá para o centro de administração.</span><span class="sxs-lookup"><span data-stu-id="26dcb-225">Go to the admin center.</span></span>
    
4. <span data-ttu-id="26dcb-p121">Para que as pessoas possam usar serviços do Office 365, elas precisam ter uma licença atribuída. Antes de continuar, convém verificar se você possui licenças suficientes para todos os usuários listados na sua planilha. Escolha **Cobrança** \> **Assinaturas** para ver se há licenças suficientes. Se você precisar comprar mais licenças, escolha \*\* Alterar a quantidade de licenças \*\*. Ou você pode executar o assistente, atribuir as licenças que você possui, comprar outras licenças mais tarde e executar o assistente novamente.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="26dcb-p122">Agora, vá para o assistente Adicionar usuários em massa: escolha **Usuários** \> **Usuários Ativos**. Escolha ![O ícone para adicionar vários usuários ao Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Uma imagem da seção usuários do centro de administração](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="26dcb-234">O assistente Adicionar usuários em massa aparecerá e o guiará pelas etapas para adicionar um grupo de usuários ao Office 365.</span><span class="sxs-lookup"><span data-stu-id="26dcb-234">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="26dcb-235">Na Etapa 1, Selecione um arquivo CSV, especifique a sua própria planilha conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="26dcb-235">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![Etapa 1 do Assistente de Adição de Usuários em Massa - Selecionar Arquivo CSV](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="26dcb-237">Na Etapa 2, Verificação, o assistente informa se o conteúdo da planilha está formatado corretamente.</span><span class="sxs-lookup"><span data-stu-id="26dcb-237">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![Etapa 2 do Assistente de Adição de Usuários em Massa - Verificação](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="26dcb-p123">Na Etapa 3, Configurações, escolha **Permitidos** para que as pessoas listadas na sua planilha possam usar o Office 365. Escolha também o país/região em que essas pessoas usarão o Office 365. Lembre-se, se algumas pessoas em sua organização forem usar o Office 365 em outro país, crie uma planilha separada com os nomes delas e execute o assistente Adicionar usuários em massa novamente para adicioná-los.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![Etapa 3 do Assistente de Adição de Usuários em Massa - Configurações](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="26dcb-243">A página de atribuição de licenças informa quantas licenças estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="26dcb-243">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![Etapa 4 do Assistente de Adição de Usuários em Massa - Licenças](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="26dcb-245">Você pode escolher **comprar mais licenças**, mas sairá do assistente de adição de usuários em massa e vá para **cobrança** no centro de administração do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="26dcb-245">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Microsoft 365 admin center.</span></span> <span data-ttu-id="26dcb-246">Após comprar mais licenças, você terá que esperar alguns minutos para que o pedido seja processado e para que você possa iniciar o assistente para Adicionar usuários em massa desde o começo.</span><span class="sxs-lookup"><span data-stu-id="26dcb-246">After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="26dcb-247">Se você não comprar mais licenças, não serão criadas contas para todas as pessoas listadas na sua planilha.</span><span class="sxs-lookup"><span data-stu-id="26dcb-247">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="26dcb-248">Vamos ver o que acontece se nós não comprarmos mais licenças e continuarmos com o assistente Adicionar usuários em massa.</span><span class="sxs-lookup"><span data-stu-id="26dcb-248">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="26dcb-249">Na Etapa 5 - Enviar resultados, digite os endereços de email das pessoas que você deseja que recebam um email listando  *todos*  os nomes de usuário e senhas temporárias do Office 365 para as pessoas na planilha.</span><span class="sxs-lookup"><span data-stu-id="26dcb-249">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![Etapa 5 do Assistente de Adição de Usuários em Massa - Enviar Resultados](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="26dcb-p125">O seguinte email é enviado a todos os endereços de email especificados na Etapa 5 - Enviar resultados. Esse email indica que contas foram criadas. Observe que não foram criadas contas para algumas pessoas porque não havia licenças suficientes.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![Email de exemplo com informações de credenciais do usuário](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="26dcb-p126">Você pode comprar outras licenças mais tarde e executar novamente o assistente Adicionar usuários em massa com a mesma planilha. O assistente ignora os usuários que já têm contas; o relatório de resultados mostrará "nome de usuário duplicado" para indicar que alguém com aquelas informações já possui uma conta.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="26dcb-257">A página final do assistente o assistente Adicionar usuários em massa lista os nomes de usuário e senhas temporárias, conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="26dcb-257">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![Etapa 6 do Assistente de Adição de Usuários em Massa - Enviar Resultados](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="26dcb-p127">Após adicionar usuários ao Office 365, você deve fornecer a eles as informações de conta do Office 365. Use seu processo normal para comunicar as novas senhas.</span><span class="sxs-lookup"><span data-stu-id="26dcb-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

