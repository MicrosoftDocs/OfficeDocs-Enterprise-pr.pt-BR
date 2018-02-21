---
title: "Bloquear contas de usuários com o Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Explica como usar o Office 365 PowerShell para bloquear e desbloquear o acesso às contas do Office 365."
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="9265a-103">Bloquear contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9265a-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="9265a-104">**Resumo:**  Explica como usar o Office 365 PowerShell para bloquear e desbloquear o acesso às contas do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9265a-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="9265a-p101">Bloqueando o acesso a uma conta do Office 365 impede que qualquer pessoa usando a conta para entrar e acessar os serviços e os dados em sua organização do Office 365. Quando você bloqueia o acesso à conta, o usuário recebe a seguinte mensagem de erro quando tentarem entrar:</span><span class="sxs-lookup"><span data-stu-id="9265a-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. When you block access to the account, the user receives the following error message when they attempt to sign in:</span></span>
  
![Conta bloqueada do Office 365.](images/o365_powershell_account_blocked.png)
  
<span data-ttu-id="9265a-108">Você pode usar o Office 365 PowerShell para bloquear o acesso individuais e várias contas de usuário.</span><span class="sxs-lookup"><span data-stu-id="9265a-108">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="9265a-109">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="9265a-109">Before you begin</span></span>

- <span data-ttu-id="9265a-p102">Os procedimentos deste tópico exigem que você se conecte ao Office 365 PowerShell. Para obter instruções, confira [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9265a-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="9265a-112">Quando você bloquear uma conta de usuário, ela pode levar desde que 24 horas, entre em vigor em clientes e dispositivos de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="9265a-112">When you block a user account, it might take as long as 24 hours to take effect on all the user's devices and clients.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="9265a-113">Usar o Office 365 PowerShell para bloquear o acesso a contas de usuário individuais</span><span class="sxs-lookup"><span data-stu-id="9265a-113">Use Office 365 PowerShell to block access to individual user accounts</span></span>

<span data-ttu-id="9265a-114">Use a seguinte sintaxe para bloquear o acesso a uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="9265a-114">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

<span data-ttu-id="9265a-115">Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="9265a-115">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="9265a-116">Para desbloquear a conta do usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9265a-116">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

<span data-ttu-id="9265a-117">A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9265a-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a><span data-ttu-id="9265a-118">Use o Office 365 PowerShell para bloquear o acesso a várias contas de usuário</span><span class="sxs-lookup"><span data-stu-id="9265a-118">Use Office 365 PowerShell to block access to multiple user accounts</span></span>

<span data-ttu-id="9265a-119">Primeiro, crie um arquivo de texto que contém uma conta em cada linha semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="9265a-119">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="9265a-p103">Nos comandos a seguir, o arquivo de texto de exemplo é C:\My Documents\Accounts.txt. Substitua pelo caminho e o nome do seu arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="9265a-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="9265a-122">Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9265a-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="9265a-123">Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9265a-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a><span data-ttu-id="9265a-124">Usar o módulo PowerShell do Azure Active Directory V2 para bloquear o acesso a contas de usuário</span><span class="sxs-lookup"><span data-stu-id="9265a-124">Use the Azure Active Directory V2 PowerShell module to block access to user accounts</span></span>

<span data-ttu-id="9265a-p104">Para usar o cmdlet **New-AzureADUser** no módulo PowerShell do Azure Active Directory V2, você deve primeiro conectar-se à sua assinatura. Para conhecer as instruções, confira[Conectar-se com o módulo PowerShell do Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="9265a-p104">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="9265a-127">Após a conexão, use a seguinte sintaxe para bloquear uma conta de usuário individual:</span><span class="sxs-lookup"><span data-stu-id="9265a-127">After you have connected, use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="9265a-128">O parâmetro -ObjectID no cmdlet Set-AzureAD aceita o nome da conta, também conhecido como o nome UPN, ou a ID de objeto da conta.</span><span class="sxs-lookup"><span data-stu-id="9265a-128">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="9265a-129">Esse exemplo bloqueia o acesso à conta de usuário ricardoc@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="9265a-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="9265a-130">Para desbloquear essa conta de usuário, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9265a-130">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="9265a-131">Para exibir a conta de usuário que UPN com base no nome para exibição do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="9265a-131">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="9265a-132">Este exemplo exibe a conta de usuário para o usuário chamado Caleb Sills UPN.</span><span class="sxs-lookup"><span data-stu-id="9265a-132">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="9265a-133">Para bloquear uma conta com base no nome do usuário, use os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="9265a-133">To block an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="9265a-134">A qualquer momento, você pode verificar o status bloqueado de uma conta de usuário com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9265a-134">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

<span data-ttu-id="9265a-135">Para bloquear o acesso a várias contas de usuário, crie um arquivo de texto que contém um nome de conta em cada linha semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="9265a-135">To block access to multiple user accounts, create a text file that contains one account name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="9265a-p105">Nos comandos a seguir, o arquivo de texto de exemplo é C:\My Documents\Accounts.txt. Substitua pelo caminho e o nome do seu arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="9265a-p105">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="9265a-138">Para bloquear o acesso às contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9265a-138">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="9265a-139">Para desbloquear as contas listadas no arquivo de texto, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9265a-139">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a><span data-ttu-id="9265a-140">Veja também</span><span class="sxs-lookup"><span data-stu-id="9265a-140">See also</span></span>
<span data-ttu-id="9265a-141"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="9265a-141"></span></span>

<span data-ttu-id="9265a-142">Confira os seguintes tópicos adicionais sobre como gerenciar usuários com o Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9265a-142">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="9265a-143">Criar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9265a-143">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9265a-144">Excluir e restaurar contas de usuários usando o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9265a-144">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9265a-145">Atribuir licenças a contas de usuários usando o PowerShell do Office 365</span><span class="sxs-lookup"><span data-stu-id="9265a-145">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="9265a-146">Remover licenças de contas de usuários com o Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9265a-146">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="9265a-147">Para saber mais sobre os cmdlets usados nestes procedimentos, confira os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="9265a-147">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="9265a-148">Get-Content</span><span class="sxs-lookup"><span data-stu-id="9265a-148">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [<span data-ttu-id="9265a-149">Set-MsolUser</span><span class="sxs-lookup"><span data-stu-id="9265a-149">Set-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [<span data-ttu-id="9265a-150">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="9265a-150">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

