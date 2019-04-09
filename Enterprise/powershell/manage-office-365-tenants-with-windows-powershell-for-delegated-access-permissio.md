---
title: Gerenciar locatários do Office 365 com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Resumo: Use o Windows PowerShell para o Office 365 para gerenciar as locações do cliente.'
ms.openlocfilehash: 4fec058bfd7b7dffa2c29add23d99a144f78decf
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001854"
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="4d1a5-103">Gerenciar locatários do Office 365 com o Windows PowerShell para parceiros com permissões de acesso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="4d1a5-103">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="4d1a5-104">**Resumo:** use o Windows PowerShell para o Office 365 para gerenciar os locatários do cliente.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-104">**Summary:** Use Windows PowerShell for Office 365 to manage your customer tenancies.</span></span>
  
<span data-ttu-id="4d1a5-p101">O Windows PowerShell permite aos Parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP). administrar e gerar relatórios facilmente das configurações de locação do cliente, que não estão disponíveis no Centro de administração do Office 365. Observe que as permissões "Administrar em Nome de" (AOBO) são necessárias para a conta de administrador do parceiro para se conectar às locações dos clientes.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Office 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="4d1a5-107">Os Parceiros com Permissão de Acesso Delegada (DAP) são parceiros da Agregação e dos Provedores de Soluções em Nuvem (CSP).</span><span class="sxs-lookup"><span data-stu-id="4d1a5-107">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="4d1a5-108">Muitas vezes, eles são provedores de rede ou de telecomunicações para outras empresas.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="4d1a5-109">Eles reúnem assinaturas do Office 365 em suas ofertas de serviço aos seus clientes.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-109">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="4d1a5-110">Quando eles vendem uma assinatura do Office 365, recebem automaticamente permissões de Administrar Em Nome de (AOBO) para as locações de cliente para que possam administrar e relatar todas as suas locações de cliente.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-110">When they sell an O365_W14_2nd subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="4d1a5-111">O que você precisa saber antes de começar?</span><span class="sxs-lookup"><span data-stu-id="4d1a5-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="4d1a5-p103">Os procedimentos neste tópico exigem que você se conecte ao Windows PowerShell para Office 365. Para obter instruções, veja [Conectar-se ao PowerShell do Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="4d1a5-114">Você também precisa ter as credenciais de administrador de locatários do parceiro.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-114">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="4d1a5-115">O que você deseja fazer?</span><span class="sxs-lookup"><span data-stu-id="4d1a5-115">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="4d1a5-116">Listar todas as IDs de Locatários</span><span class="sxs-lookup"><span data-stu-id="4d1a5-116">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="4d1a5-p104">Caso tenha mais de 500 locatários, analise a sintaxe do cmdlet com o  _-All_ ou o _-MaxResultsParameter_. Isso se aplica aos outros cmdlets que podem proporcionar uma grande saída, como o **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="4d1a5-119">Para listar todas as IDs de Locatários do cliente às quais você tem acesso, execute este comando.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-119">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="4d1a5-120">Uma lista de todos os locatários do cliente será exibida pela **TenantId**.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-120">This will display a listing of all your customer tenants by **TenantId**.</span></span>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="4d1a5-121">Obter uma ID de Locatário usando o nome de domínio</span><span class="sxs-lookup"><span data-stu-id="4d1a5-121">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="4d1a5-p105">Para obter a **TenantId** de um locatário específico do cliente por nome de domínio, execute este comando. Substitua _<domainname.onmicrosoft.com>_ pelo nome de domínio real do locatário do cliente desejado.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="4d1a5-124">Listar todos os domínios de um locatário</span><span class="sxs-lookup"><span data-stu-id="4d1a5-124">List all domains for a tenant</span></span>

<span data-ttu-id="4d1a5-p106">Para obter todos os domínios de qualquer locatário de um cliente, execute este comando. Substitua o  _<customer TenantId value>_ pelo valor real.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="4d1a5-127">Se você registrou domínios adicionais, serão retornados todos os domínios associados à **TenantId** do cliente.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-127">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="4d1a5-128">Obter um mapeamento de todos os locatários e domínios registrados</span><span class="sxs-lookup"><span data-stu-id="4d1a5-128">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="4d1a5-p107">Os comandos anteriores do Windows PowerShell para o Office 365 mostravam como recuperar IDs de Locatário ou domínios, mas não ambos ao mesmo tempo e sem nenhum mapeamento claro entre todos eles. Esse comando gera uma lista de todas as IDs de Locatários do cliente e os respectivos domínios.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p107">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="4d1a5-131">Obter todos os usuários de um locatário</span><span class="sxs-lookup"><span data-stu-id="4d1a5-131">Get all users for a tenant</span></span>

<span data-ttu-id="4d1a5-p108">Os comandos **UserPrincipalName**, o **DisplayName** e o status **isLicensed** serão exibidos para todos os usuários de um determinado locatário. Substitua o _<customer TenantId value>_ pelo valor real.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="4d1a5-134">Obter todos os detalhes sobre um usuário</span><span class="sxs-lookup"><span data-stu-id="4d1a5-134">Get all details about a user</span></span>

<span data-ttu-id="4d1a5-p109">Caso pretenda conferir todas as propriedades de um usuário específico, execute este comando. Substitua _<customer TenantId value>_ e _<user principal name value>_ pelos valores reais.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="4d1a5-137">Adicionar usuários, definir opções e atribuir licenças</span><span class="sxs-lookup"><span data-stu-id="4d1a5-137">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="4d1a5-p110">A criação, configuração e licenciamento em massa de usuários do Office 365 é particularmente eficiente ao usar o Windows PowerShell para o Office 365. Nesse processo de duas etapas, primeiro crie entradas para todos os usuários que deseja adicionar em um arquivo (CSV) de valor separado por vírgula e, em seguida, importe esse arquivo usando o Windows PowerShell para o Office 365.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p110">The bulk creation, configuration, and licensing of Office 365 users is particularly efficient by using Windows PowerShell for Office 365. In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="4d1a5-140">Criar um arquivo CSV</span><span class="sxs-lookup"><span data-stu-id="4d1a5-140">Create a CSV file</span></span>

<span data-ttu-id="4d1a5-141">Crie um arquivo CSV usando este formato:</span><span class="sxs-lookup"><span data-stu-id="4d1a5-141">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="4d1a5-142">em que:</span><span class="sxs-lookup"><span data-stu-id="4d1a5-142">where:</span></span>
  
- <span data-ttu-id="4d1a5-p111">**UsageLocation**: O valor para isso é o código de país/região ISO de duas letras do usuário. Os códigos de país/região podem ser visualizados na[Plataforma de Navegação Online ISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Por exemplo, o código para os Estados Unidos é US e o código para o Brasil é BR.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="4d1a5-p112">**LicenseAssignment**: O valor para isso tem o seguinte formato: `syndication-account:<PROVISIONING_ID>`. Por exemplo, se você está atribuindo licenças para usuários do O365_Business_Premium, o valor de **LicenseAssignment** tem a seguinte aparência: **syndication-account:O365_Business_Premium**. Você vai encontrar as PROVISIONING_IDs no portal do parceiro de distribuição ao qual tem acesso como um parceiro de agregação ou um CSP.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="4d1a5-149">Importar o arquivo CSV e criar os usuários</span><span class="sxs-lookup"><span data-stu-id="4d1a5-149">Import the CSV file and create the users</span></span>

<span data-ttu-id="4d1a5-p113">Depois de criar o arquivo CSV, execute este comando para criar contas de usuários com senhas que não perdem a validade. Essas senhas atribuem a licença especificada e os usuários devem alterá-la no primeiro logon. Não deixe de substituir o nome correto do arquivo CSV.</span><span class="sxs-lookup"><span data-stu-id="4d1a5-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="4d1a5-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="4d1a5-152">See also</span></span>

#### 

[<span data-ttu-id="4d1a5-153">Ajuda para parceiros</span><span class="sxs-lookup"><span data-stu-id="4d1a5-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

