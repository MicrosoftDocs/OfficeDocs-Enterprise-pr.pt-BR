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
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administrar caixas de correio do Exchange Online em um ambiente multigeográfico

É necessário o PowerShell remoto para exibir e configurar as propriedades multigeográficas no ambiente do Office 365. Para se conectar ao Exchange Online PowerShell, confira [Conectar ao Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

É necessário o [Módulo Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou superior em v1. x para ver a propriedade **PreferredDataLocation** nos objetos do usuário. Objetos do usuário sincronizados por meio do AAD Connect no AAD não podem ter seu valore **PreferredDataLocation** modificado diretamente por meio do AAD PowerShell. Objetos Apenas Nuvem de usuário podem ser modificados pelo AAD PowerShell. Para conectar-se ao PowerShell do Azure AD, confira [Conectar-se ao PowerShell do Office 365](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Conecte-se diretamente em uma localização geográfica usando o Exchange Online PowerShell
Normalmente, o Exchange Online PowerShell se conectará à localização central. No entanto, você também pode se conectar diretamente em localizações via satélite. Devido a melhorias de desempenho, recomendamos que você conecte-se diretamente a uma localização via satélite se você só gerenciar usuários nesta localização geográfica.

Para conectar-se a uma localização geográfica específica, o parâmetro *ConnectionUri* é diferente das instruções de conexão comuns. O restante dos comandos e valores são iguais. As etapas são:

1. Em seu computador local, abra o Windows PowerShell e execute o comando a seguir:
    
    ```
    $UserCredential = Get-Credential
    ```
   Na caixa de diálogo **Solicitação de Credencial do Windows PowerShell**, digite sua conta corporativa ou de estudante e senha, e clique em **OK**.
    
2. Substitua `<emailaddress>` com o endereço de email de **qualquer** caixa de correio na localização geográfica de destino e execute o seguinte comando. As permissões de caixa de correio e a relação com suas credenciais na Etapa 1 não são um fator; o endereço de email simplesmente informa ao Exchange Online como se conectar.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Por exemplo, se olga@contoso.onmicrosoft.com é o endereço de email de uma caixa de correio válida na área geográfica que você deseja conectar, execute o seguinte comando:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Execute o seguinte comando:
    
    ```
    Import-PSSession $Session
    ```


## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Exibir as localizações geográficas disponíveis que estão configurados em sua organização do Exchange Online
Para ver a lista de localizações geográficas configuradas no Office 365 Multi-Geo, execute o seguinte comando no Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-location-for-your-exchange-online-organization"></a>Exibir a localização central para sua organização do Exchange Online
Para exibir a localização central do locatário, execute o seguinte comando no Exchange Online PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Descobrir a localização geográfica de uma caixa de correio
O cmdlet **Get-Mailbox** no Exchange Online PowerShell exibe as seguintes propriedades relacionadas às áreas multigeográficas nas caixas de correio:

- **Banco de dados**: As 3 primeiras letras do nome do banco de dados correspondem ao código geográfico, o que determina onde a caixa de correio está localizada no momento. Para Caixas de Correio com Arquivo Online a propriedade **ArchiveDatabase** deve ser usada.

- **MailboxRegion**: Especifica o código da localização geográfica que foi definida pelo administrador (sincronizado do **PreferredDataLocation** no Azure AD).

- **MailboxRegionLastUpdateTime**: Indica quando o MailboxRegion foi atualizado (automaticamente ou manualmente).

Para ver as propriedades de uma caixa de correio, use a seguinte sintaxe:

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Por exemplo, para ver as informações Geográficas da caixa de correio chris@contoso.onmicrosoft.com, execute o seguinte comando:

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

A saída do comando será parecida com o seguinte:

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **Observação:** se o código de localização geográfica no nome do banco de dados não corresponde ao valor **MailboxRegion**, a caixa de correio será automaticamente colocada na fila de mudança e movida para a localização geográfica especificada pelo valor ** MailboxRegion** (O Exchange Online procura uma incompatibilidade entre esses valores de propriedade).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Mover uma caixa de correio apenas nuvem existente para uma localização geográfica específica
Um usuário apenas nuvem é um usuário não sincronizado com o locatário por meio do AAD Connect. Esse usuário foi criado diretamente no Azure AD. Use os cmdlets **Get-MsolUser** e **Set-MsolUser** no Módulo do Azure AD do Windows PowerShell para visualizar ou especificar a área geográfica onde a caixa de correio do usuário somente na nuvem será armazenada.

Para exibir o valor **PreferredDataLocation** para um usuário, use esta sintaxe no Azure AD PowerShell:

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Por exemplo, para ver o valor **PreferredDataLocation** para o usuário michelle@contoso.onmicrosoft.com, execute o seguinte comando:

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Para modificar o valor **PreferredDataLocation** para um objeto de usuário apenas nuvem, use a seguinte sintaxe no Azure AD PowerShell:

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Por exemplo, para configurar o valor **PreferredDataLocation** para a área geográfica União Europeia (UE) para o usuário michelle@contoso.onmicrosoft.com, execute o seguinte comando:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Observações**:

- Como mencionamos anteriormente é possível usar este procedimento para objetos sincronizados do usuário do Active Directory no local. Você precisa alterar o valor **PreferredDataLocation** no Active Directory e sincronizá-lo usando o AAD Connect. Para saber mais, confira [Sincronização do Azure Active Directory Connect: Configurar o local preferencial dos dados para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- O tempo que leva para relocar uma caixa de correio para uma nova localização geográfica depende de vários fatores:
 
  - O tamanho e tipo de caixa de correio.
 
  - O número de caixas de correio sendo movidas.
 
  - Disponibilidade de recursos de movimentação.

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Mover caixas de correio desabilitadas que estão em Retenção de Litígio
Caixas de correio desabilitadas em Retenção de Litígio são preservadas para fins de descoberta eletrônica não podem ser movidas alterando seu valor **PreferredDataLocation** no estado desabilitado. Para mover uma caixa de correio desabilitada em retenção de litígio:

1. Atribua temporariamente uma licença à caixa de correio.

2. Altere o **PreferredDataLocation**.

3. Remova a licença da caixa de correio depois de ser movida para a localização geográfica selecionada para colocá-la novamente no estado desabilitado.

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Criar novas caixas de correio em nuvem em uma localização geográfica específica
Para criar uma nova caixa de correio em uma localização geográfica específica, é preciso seguir uma destas etapas:

- Configurar o valor **PreferredDataLocation** conforme descrito na seção anterior *antes* da caixa de correio ser criada no Exchange Online. Por exemplo, configure valor **PreferredDataLocation** em um usuário antes de atribuir uma licença. 

- Atribuir uma licença e definir o valor **PreferredDataLocation** ao mesmo tempo.

Para criar um novo usuário licenciado apenas nuvem (não AAD Connect sincronizado) em uma localização geográfica específica, use a seguinte sintaxe no Azure AD PowerShell:

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
Este exemplo cria uma nova conta de usuário para Elizabeth Brunner com os seguintes valores:

- Nome de usuário principal: ebrunner@contoso.onmicrosoft.com

- Nome: Elizabeth

- Sobrenome: Brunner

- Nome para exibição Elizabeth Brunner

- Senha: gerada aleatoriamente e mostrada nos resultados do comando (porque não estamos usando o parâmetro *Senha*)

- Licença: contoso:ENTERPRISEPREMIUM (E5)

- Local: Austrália (AUS)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Para mais informações sobre como criar novas contas de usuário e encontrar valores LicenseAssignment no Azure AD PowerShell, confira [Criar contas de usuário com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [Exibir licenças e serviços com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> **Observação:** se você estiver usando o Exchange Online PowerShell para habilitar uma caixa de correio e precisa que a caixa de correio seja criada diretamente na localização geográfica especificada no **PreferredDataLocation**, é necessário usar um cmdlet do Exchange Online, como **Enable-Mailbox** ou **New-Mailbox** diretamente contra o serviço de nuvem. Se você usar o cmdlet **Enable-RemoteMailbox** do Exchange local, a caixa de correio será criada em uma localização central.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Integração de caixas de correio locais existentes em uma localização geográfica específica
Você pode usar as ferramentas de integração padrão e os processos para migrar uma caixa de correio de uma organização do Exchange local para o Exchange Online, incluindo o [Painel de migração no EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e o cmdlet [New-MigrationBatch ](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) no Exchange Online PowerShell.

A primeira etapa consiste em verificar um objeto de usuário existente para cada caixa de correio a ser integrada e verificar se o valor **PreferredDataLocation** correto está configurado no Azure AD. As ferramentas de integração respeitará o valor **PreferredDataLocation** e migrará as caixas de correio diretamente para a localização geográfica especificada.

Ou você pode usar as etapas a seguir para integrar as caixas de correio diretamente em uma localização geográfica específica usando o cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet no Exchange Online PowerShell.

1. Verifique se o objeto do usuário existe para cada caixa de correio integrada e se o **PreferredDataLocation** está definido com o valor desejado no Azure AD. O valor do **PreferredDataLocation** será sincronizado com o atributo **MailboxRegion** do objeto do usuário de email correspondentes no Exchange Online.

2. Conecte-se diretamente à localização geográfica por satélite específica usando as instruções de conexão anteriormente neste tópico.

3. No Exchange Online PowerShell armazene as credenciais de administrador local usadas para realizar a migração da caixa de correio em uma variável ao executar o seguinte comando:

    ```
    $RC = Get-Credential
    ```

4. No Exchange Online PowerShell, crie um novo **New-MoveRequest** semelhante ao exemplo a seguir: 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Repita a etapa #4 para cada caixa de correio que precisa migrar do Exchange para a localização por satélite que você está conectado.

6. Se precisar migrar caixas de correio adicionais para um localização por satélite diferente, repita as etapas 2 a 4 para cada localização por satélite específica.

## <a name="multi-geo-reporting"></a>Relatórios multigeográficos
**Relatórios de uso multigeográfico** no centro de administração do Microsoft 365 centro exiba a contagem de usuários por localização geográfica. O relatório exibe a distribuição do usuário no mês atual e fornece dados históricos para os últimos seis meses.

## <a name="see-also"></a>Confira também

[Gerenciar o Office 365 e o Exchange Online com o Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)