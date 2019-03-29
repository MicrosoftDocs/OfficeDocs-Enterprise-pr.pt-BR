---
title: Administrar caixas de correio do Exchange Online em um ambiente multigeográfico
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Saiba como administrar a configuração multigeográfica doExchange Online com o Microsoft PowerShell.
ms.openlocfilehash: 5e1108c946ab1d9588ad5d1d41f21799e8254257
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30933923"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a><span data-ttu-id="f3470-103">Administrar caixas de correio do Exchange Online em um ambiente multigeográfico</span><span class="sxs-lookup"><span data-stu-id="f3470-103">Administering Exchange Online mailboxes in a multi-geo environment</span></span>

<span data-ttu-id="f3470-104">É necessário o PowerShell remoto para exibir e configurar as propriedades multigeográficas no ambiente do Office 365.</span><span class="sxs-lookup"><span data-stu-id="f3470-104">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment.</span></span> <span data-ttu-id="f3470-105">Para se conectar ao Exchange Online PowerShell, confira [Conectar ao Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="f3470-105">To learn how to connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>

<span data-ttu-id="f3470-106">É necessário o [Módulo Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou superior em v1. x para ver a propriedade **PreferredDataLocation** nos objetos do usuário.</span><span class="sxs-lookup"><span data-stu-id="f3470-106">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects.</span></span> <span data-ttu-id="f3470-107">Objetos do usuário sincronizados por meio do AAD Connect no AAD não podem ter seu valore **PreferredDataLocation** modificado diretamente por meio do AAD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3470-107">User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell.</span></span> <span data-ttu-id="f3470-108">Objetos Apenas Nuvem de usuário podem ser modificados pelo AAD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3470-108">Cloud-only user objects can be modified via AAD PowerShell.</span></span> <span data-ttu-id="f3470-109">Para conectar-se ao PowerShell do Azure AD, confira [Conectar-se ao PowerShell do Office 365](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="f3470-109">To connect to Security & Compliance Center PowerShell, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a><span data-ttu-id="f3470-110">Conecte-se diretamente em uma localização geográfica usando o Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3470-110">Connect directly to a geo location using Exchange Online PowerShell</span></span>
<span data-ttu-id="f3470-111">Normalmente, o Exchange Online PowerShell se conectará à localização central.</span><span class="sxs-lookup"><span data-stu-id="f3470-111">Typically, Exchange Online PowerShell will connect to the central location.</span></span> <span data-ttu-id="f3470-112">No entanto, você também pode se conectar diretamente em localizações via satélite.</span><span class="sxs-lookup"><span data-stu-id="f3470-112">But, you can also connect directly to satellite locations.</span></span> <span data-ttu-id="f3470-113">Devido a melhorias de desempenho, recomendamos que você conecte-se diretamente a uma localização via satélite se você só gerenciar usuários nesta localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="f3470-113">Because of performance improvements, we recommend connecting directly to the satellite location when you only manage users in that geo location.</span></span>

<span data-ttu-id="f3470-114">Para conectar-se a uma localização geográfica específica, o parâmetro *ConnectionUri* é diferente das instruções de conexão comuns.</span><span class="sxs-lookup"><span data-stu-id="f3470-114">To connect to a specific geo location, the *ConnectionUri* parameter is different than the regular connection instructions.</span></span> <span data-ttu-id="f3470-115">O restante dos comandos e valores são iguais.</span><span class="sxs-lookup"><span data-stu-id="f3470-115">The rest of the commands and values are the same.</span></span> <span data-ttu-id="f3470-116">As etapas são:</span><span class="sxs-lookup"><span data-stu-id="f3470-116">The steps are:</span></span>

1. <span data-ttu-id="f3470-117">Em seu computador local, abra o Windows PowerShell e execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="f3470-117">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="f3470-118">Na caixa de diálogo **Solicitação de Credencial do Windows PowerShell**, digite sua conta corporativa ou de estudante e senha, e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="f3470-118">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="f3470-119">Substitua `<emailaddress>` com o endereço de email de **qualquer** caixa de correio na localização geográfica de destino e execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="f3470-119">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command.</span></span> <span data-ttu-id="f3470-120">As permissões de caixa de correio e a relação com suas credenciais na Etapa 1 não são um fator; o endereço de email simplesmente informa ao Exchange Online como se conectar.</span><span class="sxs-lookup"><span data-stu-id="f3470-120">Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="f3470-121">Por exemplo, se olga@contoso.onmicrosoft.com é o endereço de email de uma caixa de correio válida na área geográfica que você deseja conectar, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f3470-121">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="f3470-122">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f3470-122">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```


## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="f3470-123">Exibir as localizações geográficas disponíveis que estão configurados em sua organização do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f3470-123">View the available geo locations that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="f3470-124">Para ver a lista de localizações geográficas configuradas no Office 365 Multi-Geo, execute o seguinte comando no Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f3470-124">To see the list of configured geo locations in Office 365 Multi-Geo, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-location-for-your-exchange-online-organization"></a><span data-ttu-id="f3470-125">Exibir a localização central para sua organização do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="f3470-125">View the central location for your Exchange Online organization</span></span>
<span data-ttu-id="f3470-126">Para exibir a localização central do locatário, execute o seguinte comando no Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f3470-126">To view your tenant's central location, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="f3470-127">Descobrir a localização geográfica de uma caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f3470-127">Find the geo location of a mailbox</span></span>
<span data-ttu-id="f3470-128">O cmdlet **Get-Mailbox** no Exchange Online PowerShell exibe as seguintes propriedades relacionadas às áreas multigeográficas nas caixas de correio:</span><span class="sxs-lookup"><span data-stu-id="f3470-128">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="f3470-129">**Banco de dados**: As 3 primeiras letras do nome do banco de dados correspondem ao código geográfico, o que determina onde a caixa de correio está localizada no momento.</span><span class="sxs-lookup"><span data-stu-id="f3470-129">**Database**: The first 3 letters of the database name correspond to the geo code, which tells you where the mailbox is currently located.</span></span> <span data-ttu-id="f3470-130">Para Caixas de Correio com Arquivo Online a propriedade **ArchiveDatabase** deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="f3470-130">For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="f3470-131">**MailboxRegion**: Especifica o código da localização geográfica que foi definida pelo administrador (sincronizado do **PreferredDataLocation** no Azure AD).</span><span class="sxs-lookup"><span data-stu-id="f3470-131">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="f3470-132">**MailboxRegionLastUpdateTime**: Indica quando o MailboxRegion foi atualizado (automaticamente ou manualmente).</span><span class="sxs-lookup"><span data-stu-id="f3470-132">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="f3470-133">Para ver as propriedades de uma caixa de correio, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="f3470-133">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="f3470-134">Por exemplo, para ver as informações Geográficas da caixa de correio chris@contoso.onmicrosoft.com, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f3470-134">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="f3470-135">A saída do comando será parecida com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f3470-135">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="f3470-136">**Observação:** se o código de localização geográfica no nome do banco de dados não corresponde ao valor **MailboxRegion**, a caixa de correio será automaticamente colocada na fila de mudança e movida para a localização geográfica especificada pelo valor \*\* MailboxRegion\*\* (O Exchange Online procura uma incompatibilidade entre esses valores de propriedade).</span><span class="sxs-lookup"><span data-stu-id="f3470-136">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a><span data-ttu-id="f3470-137">Mover uma caixa de correio apenas nuvem existente para uma localização geográfica específica</span><span class="sxs-lookup"><span data-stu-id="f3470-137">Move an existing cloud-only mailbox to a specific geo location</span></span>
<span data-ttu-id="f3470-138">Um usuário apenas nuvem é um usuário não sincronizado com o locatário por meio do AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="f3470-138">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect.</span></span> <span data-ttu-id="f3470-139">Esse usuário foi criado diretamente no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f3470-139">This user was created directly in Azure AD.</span></span> <span data-ttu-id="f3470-140">Use os cmdlets **Get-MsolUser** e **Set-MsolUser** no Módulo do Azure AD do Windows PowerShell para visualizar ou especificar a área geográfica onde a caixa de correio do usuário somente na nuvem será armazenada.</span><span class="sxs-lookup"><span data-stu-id="f3470-140">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="f3470-141">Para exibir o valor **PreferredDataLocation** para um usuário, use esta sintaxe no Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f3470-141">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="f3470-142">Por exemplo, para ver o valor **PreferredDataLocation** para o usuário michelle@contoso.onmicrosoft.com, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f3470-142">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="f3470-143">Para modificar o valor **PreferredDataLocation** para um objeto de usuário apenas nuvem, use a seguinte sintaxe no Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f3470-143">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="f3470-144">Por exemplo, para configurar o valor **PreferredDataLocation** para a área geográfica União Europeia (UE) para o usuário michelle@contoso.onmicrosoft.com, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f3470-144">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="f3470-145">**Observações**:</span><span class="sxs-lookup"><span data-stu-id="f3470-145">**Notes**:</span></span>

- <span data-ttu-id="f3470-146">Como mencionamos anteriormente é possível usar este procedimento para objetos sincronizados do usuário do Active Directory no local.</span><span class="sxs-lookup"><span data-stu-id="f3470-146">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory.</span></span> <span data-ttu-id="f3470-147">Você precisa alterar o valor **PreferredDataLocation** no Active Directory e sincronizá-lo usando o AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="f3470-147">You need to change the **PreferredDataLocation** value in Active Directory and synchronize it using AAD Connect.</span></span> <span data-ttu-id="f3470-148">Para saber mais, confira [Sincronização do Azure Active Directory Connect: Configurar o local preferencial dos dados para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="f3470-148">For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="f3470-149">O tempo que leva para relocar uma caixa de correio para uma nova localização geográfica depende de vários fatores:</span><span class="sxs-lookup"><span data-stu-id="f3470-149">How long it takes to relocate a mailbox to a new geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="f3470-150">O tamanho e tipo de caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="f3470-150">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="f3470-151">O número de caixas de correio sendo movidas.</span><span class="sxs-lookup"><span data-stu-id="f3470-151">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="f3470-152">Disponibilidade de recursos de movimentação.</span><span class="sxs-lookup"><span data-stu-id="f3470-152">The availability of move resources.</span></span>

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="f3470-153">Mover caixas de correio desabilitadas que estão em Retenção de Litígio</span><span class="sxs-lookup"><span data-stu-id="f3470-153">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="f3470-154">Caixas de correio desabilitadas em Retenção de Litígio são preservadas para fins de descoberta eletrônica não podem ser movidas alterando seu valor **PreferredDataLocation** no estado desabilitado.</span><span class="sxs-lookup"><span data-stu-id="f3470-154">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state.</span></span> <span data-ttu-id="f3470-155">Para mover uma caixa de correio desabilitada em retenção de litígio:</span><span class="sxs-lookup"><span data-stu-id="f3470-155">To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="f3470-156">Atribua temporariamente uma licença à caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="f3470-156">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="f3470-157">Altere o **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="f3470-157">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="f3470-158">Remova a licença da caixa de correio depois de ser movida para a localização geográfica selecionada para colocá-la novamente no estado desabilitado.</span><span class="sxs-lookup"><span data-stu-id="f3470-158">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="f3470-159">Criar novas caixas de correio em nuvem em uma localização geográfica específica</span><span class="sxs-lookup"><span data-stu-id="f3470-159">Create new cloud mailboxes in a specific geo location</span></span>
<span data-ttu-id="f3470-160">Para criar uma nova caixa de correio em uma localização geográfica específica, é preciso seguir uma destas etapas:</span><span class="sxs-lookup"><span data-stu-id="f3470-160">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="f3470-161">Configurar o valor **PreferredDataLocation** conforme descrito na seção anterior *antes* da caixa de correio ser criada no Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f3470-161">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online.</span></span> <span data-ttu-id="f3470-162">Por exemplo, configure valor **PreferredDataLocation** em um usuário antes de atribuir uma licença.</span><span class="sxs-lookup"><span data-stu-id="f3470-162">For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="f3470-163">Atribuir uma licença e definir o valor **PreferredDataLocation** ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="f3470-163">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="f3470-164">Para criar um novo usuário licenciado apenas nuvem (não AAD Connect sincronizado) em uma localização geográfica específica, use a seguinte sintaxe no Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f3470-164">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="f3470-165">Este exemplo cria uma nova conta de usuário para Elizabeth Brunner com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="f3470-165">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="f3470-166">Nome de usuário principal: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="f3470-166">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="f3470-167">Nome: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="f3470-167">First name: Elizabeth</span></span>

- <span data-ttu-id="f3470-168">Sobrenome: Brunner</span><span class="sxs-lookup"><span data-stu-id="f3470-168">Last name: Brunner</span></span>

- <span data-ttu-id="f3470-169">Nome para exibição Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="f3470-169">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="f3470-170">Senha: gerada aleatoriamente e mostrada nos resultados do comando (porque não estamos usando o parâmetro *Senha*)</span><span class="sxs-lookup"><span data-stu-id="f3470-170">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="f3470-171">Licença: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="f3470-171">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="f3470-172">Local: Austrália (AUS)</span><span class="sxs-lookup"><span data-stu-id="f3470-172">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="f3470-173">Para mais informações sobre como criar novas contas de usuário e encontrar valores LicenseAssignment no Azure AD PowerShell, confira [Criar contas de usuário com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [Exibir licenças e serviços com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="f3470-173">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="f3470-174">**Observação:** se você estiver usando o Exchange Online PowerShell para habilitar uma caixa de correio e precisa que a caixa de correio seja criada diretamente na localização geográfica especificada no **PreferredDataLocation**, é necessário usar um cmdlet do Exchange Online, como **Enable-Mailbox** ou **New-Mailbox** diretamente contra o serviço de nuvem.</span><span class="sxs-lookup"><span data-stu-id="f3470-174">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service.</span></span> <span data-ttu-id="f3470-175">Se você usar o cmdlet **Enable-RemoteMailbox** do Exchange local, a caixa de correio será criada em uma localização central.</span><span class="sxs-lookup"><span data-stu-id="f3470-175">If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the central location.</span></span>

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="f3470-176">Integração de caixas de correio locais existentes em uma localização geográfica específica</span><span class="sxs-lookup"><span data-stu-id="f3470-176">Onboard existing on-premises mailboxes in a specific geo location</span></span>
<span data-ttu-id="f3470-177">Você pode usar as ferramentas de integração padrão e os processos para migrar uma caixa de correio de uma organização do Exchange local para o Exchange Online, incluindo o [Painel de migração no EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e o cmdlet [New-MigrationBatch ](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) no Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3470-177">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="f3470-178">A primeira etapa consiste em verificar um objeto de usuário existente para cada caixa de correio a ser integrada e verificar se o valor **PreferredDataLocation** correto está configurado no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f3470-178">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD.</span></span> <span data-ttu-id="f3470-179">As ferramentas de integração respeitará o valor **PreferredDataLocation** e migrará as caixas de correio diretamente para a localização geográfica especificada.</span><span class="sxs-lookup"><span data-stu-id="f3470-179">The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="f3470-180">Ou você pode usar as etapas a seguir para integrar as caixas de correio diretamente em uma localização geográfica específica usando o cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet no Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3470-180">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="f3470-181">Verifique se o objeto do usuário existe para cada caixa de correio integrada e se o **PreferredDataLocation** está definido com o valor desejado no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f3470-181">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD.</span></span> <span data-ttu-id="f3470-182">O valor do **PreferredDataLocation** será sincronizado com o atributo **MailboxRegion** do objeto do usuário de email correspondentes no Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="f3470-182">The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="f3470-183">Conecte-se diretamente à localização geográfica por satélite específica usando as instruções de conexão anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="f3470-183">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="f3470-184">No Exchange Online PowerShell armazene as credenciais de administrador local usadas para realizar a migração da caixa de correio em uma variável ao executar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f3470-184">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="f3470-185">No Exchange Online PowerShell, crie um novo **New-MoveRequest** semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f3470-185">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="f3470-186">Repita a etapa #4 para cada caixa de correio que precisa migrar do Exchange para a localização por satélite que você está conectado.</span><span class="sxs-lookup"><span data-stu-id="f3470-186">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="f3470-187">Se precisar migrar caixas de correio adicionais para um localização por satélite diferente, repita as etapas 2 a 4 para cada localização por satélite específica.</span><span class="sxs-lookup"><span data-stu-id="f3470-187">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

## <a name="multi-geo-reporting"></a><span data-ttu-id="f3470-188">Relatórios multigeográficos</span><span class="sxs-lookup"><span data-stu-id="f3470-188">Multi-geo reporting</span></span>
<span data-ttu-id="f3470-189">**Relatórios de uso multigeográfico** no centro de administração do Microsoft 365 centro exiba a contagem de usuários por localização geográfica.</span><span class="sxs-lookup"><span data-stu-id="f3470-189">**Multi-Geo Usage Reports** in the Microsoft 365 admin center displays the user count by geo location.</span></span> <span data-ttu-id="f3470-190">O relatório exibe a distribuição do usuário no mês atual e fornece dados históricos para os últimos seis meses.</span><span class="sxs-lookup"><span data-stu-id="f3470-190">The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3470-191">Confira também</span><span class="sxs-lookup"><span data-stu-id="f3470-191">See also</span></span>

[<span data-ttu-id="f3470-192">Gerenciar o Office 365 e o Exchange Online com o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3470-192">Managing Office 365 and Exchange Online with Windows PowerShell</span></span>](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)