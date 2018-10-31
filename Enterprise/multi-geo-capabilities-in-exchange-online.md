---
title: Recursos de multi-Geo no Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Expanda sua presença do Office 365 para várias regiões geográficas com os recursos de multi-geo no Exchange Online.
ms.openlocfilehash: 5f34a2da47b9767aa9dfe22c6be7237951128960
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849917"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Recursos de multi-Geo no Exchange Online

Recursos de multi-Geo no Office 365 habilitar um único locatário englobe vários locais geográficos. Quando multi-geo estiver habilitada, os clientes podem selecionar o local do conteúdo de caixa de correio Exchange Online (dados em repouso) em uma base por usuário.

Seu local de locatário inicial (conhecido como o local central) é determinada com base em seu endereço de cobrança. Quando multi-geo estiver habilitada, você pode colocar a caixas de correio em locais adicionais de satélite por:

- Criando uma nova caixa de correio Exchange Online diretamente em um local de satélite.

- Mover uma caixa de correio do Exchange Online existente para um local de satélite.

- Inclusão de uma caixa de correio de uma organização do Exchange local diretamente em um local de satélite.

Os locais de geo a seguir estão disponíveis para uso em uma configuração de Multi-Geo:

- Ásia Pacífico

- Austrália

- Canadá

- União Europeia

- França

- Índia (atualmente disponível apenas a clientes com os endereços de cobrança na Índia)

- Japão

- Coreia

- Reino Unido

- Estados Unidos

## <a name="prerequisite-configuration"></a>Configuração de pré-requisito
Antes de começar a usar o Multi-Geo recursos no Exchange Online, o Microsoft precisa configurar seu locatário do Exchange Online para suporte multi-geo. Esse processo de configuração de uma única vez é disparado depois que você encomendar o Office 365 Multi-Geo e as licenças mostram no seu locatário. Esse processo de configuração de uma única vez normalmente deve levar menos de 30 dias para ser concluída. Para encomendar o Office 365 Multi-Geo, contate o representante da Microsoft. Para obter mais informações, consulte https://aka.ms/Multi-Geo.

Você receberá notificações no [Centro de mensagem do Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) , quando a configuração foi concluída. Configuração automaticamente é acionada depois de suas licenças multi-geo mostram no seu locatário.

## <a name="mailbox-placement-and-moves"></a>Movimentações e posicionamento de caixa de correio
Após a conclusão das etapas de configuração de pré-requisito multi-geo da Microsoft, Exchange Online aceita o atributo **PreferredDataLocation** em objetos de usuário no Windows Azure AD.

O Exchange Online sincroniza a propriedade **PreferredDataLocation** do Azure AD para a propriedade **MailboxRegion** no serviço de diretório Exchange Online. O valor **MailboxRegion** determina o Geo onde caixas de correio de usuário e qualquer caixa de correio de arquivo morto associada será colocada. Não é possível configurar principal da caixa de correio e arquivamento caixas de correio um usuário para residir em geo diferentes locais. Somente um local geo pode ser configurado por um objeto de usuário.

- Quando **PreferredDataLocation** estiver configurada em um usuário com uma caixa de correio existente, a caixa de correio será colocado em uma fila de realocação e movidas automaticamente para o local de geo especificado. 

- Quando **PreferredDataLocation** estiver configurada em um usuário sem uma caixa de correio existente, a caixa de correio será provisionada no local, geo especificado. 

- Quando **PreferredDataLocation** não for especificado em um usuário, a caixa de correio será colocada no local central.

- Se o código de **PreferredDataLocation** está incorreto (por exemplo, um tipo de NAN em vez do nome), a caixa de correio será colocada no local central.

**Observação**: capacidades de multi-geo e Skype para Business Online regional hospedada reuniões usam a propriedade **PreferredDataLocation** nos objetos de usuário para localizar serviços. Se você configurar valores **PreferredDataLocation** em objetos de usuário para reuniões regional hospedadas, a caixa de correio dos usuários serão automaticamente movida para o local especificado geo depois multi-geo está habilitado no inquilino do Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitações do recurso para Multi-Geo no Exchange Online
1. Apenas caixas de correio do usuário, caixas de correio de recurso (caixas de correio de sala e equipamento) e caixas de correio compartilhadas suportam recursos de multi-geo. Caixas de correio de pasta de públicos e grupos do Office 365 permanecem no local central.
 
2. Segurança e conformidade recursos (por exemplo, auditoria e descoberta eletrônica) que estão disponíveis no Centro de administração do Exchange (EAC) não estão disponíveis nas organizações multi-geo. Em vez disso, você precisará usar o [Centro de conformidade e segurança do Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar recursos de segurança e conformidade.

3. Outlook para Mac usuários perceba uma perda temporária de acesso a sua pasta de arquivo morto Online enquanto move suas caixas de correio para um novo local de geo. Esta condição ocorre quando o principal do usuário e arquivar caixas de correio estão em locais diferentes geo, porque cross-Geo movimentações de caixa de correio podem ser concluído em momentos diferentes.

4. Os usuários não podem compartilhar *pastas de caixa de correio* entre localidades geo no Outlook na web (anteriormente conhecido como o Outlook Web App ou no OWA). Por exemplo, um usuário na União Europeia não pode usar o Outlook na web para abrir uma pasta compartilhada em uma caixa de correio que está localizada nos Estados Unidos. No entanto, o Outlook em que os usuários da Web pode abrir *outras caixas de correio* em diferentes Geos usando uma janela separada do navegador, conforme descrito em [Abrir a caixa de correio de outra pessoa em uma janela separada do navegador no Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Observação**: o compartilhamento de pasta de caixa de correio entre-geo é suportado no Outlook no Windows.

## <a name="administration"></a>Administração 
PowerShell remoto é necessária para exibir e configurar o multi geo propriedades no seu ambiente do Office 365. Para obter informações sobre vários módulos do PowerShell usados para administrar o Office 365, consulte [Gerenciando o Office 365 e o Exchange Online com o Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- É necessário o [Módulo Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou posterior em v1. x para ver a propriedade **PreferredDataLocation** em objetos de usuário. Objetos de usuário sincronizados via AAD conectar no AAD não podem ter seu valor **PreferredDataLocation** modificada diretamente por meio do PowerShell AAD. Objetos de usuário somente na nuvem podem ser modificados por meio do PowerShell AAD. Para se conectar ao AD do Windows Azure PowerShell, consulte [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Para conectar ao Exchange Online PowerShell, consulte [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Conectar-se diretamente a um Geo específico usando o PowerShell do Exchange Online
Normalmente, o PowerShell do Exchange Online se conectará geo local padrão. Porém, você também pode conectar diretamente para os locais de geo não-padrão. Devido aos aprimoramentos de desempenho, é recomendável conectar-se diretamente para o local não-padrão geo quando você gerencia somente os usuários nesta localização geográfica.

Para conectar a um Geo específico, o parâmetro *ConnectionUri* é diferente das instruções de conexão regular. O restante dos comandos e valores são os mesmos. As etapas são:

1. No computador local, abra o Windows PowerShell e execute o seguinte comando:
    
    ```
    $UserCredential = Get-Credential
    ```
   Na caixa de diálogo **Solicitação de credencial do Windows PowerShell** , digite seu trabalho escola conta e senha e clique em **Okey**.
    
2. Substituir `<emailaddress>` com o endereço de email de **qualquer** caixa de correio no local do destino geo e execute o comando a seguir. Suas permissões na caixa de correio e a relação com suas credenciais na etapa 1 não são um fator; o endereço de email simplesmente informa o Exchange Online onde para se conectar.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Por exemplo, se olga@contoso.onmicrosoft.com é o endereço de email de uma caixa de correio válida do Geo que você deseja se conectar, execute o seguinte comando:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Execute o seguinte comando:
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Requisitos de versão do Azure AD Connect
Conectar AAD versão 1.1.524.0 ou posterior é o único método suportado para definir a propriedade **PreferredDataLocation** nos objetos de usuário que são sincronizados do Active Directory no local. Objetos de usuário sincronizados via AAD conectar no AAD não podem ter seu valor **PreferredDataLocation** modificada diretamente por meio do PowerShell AAD. Objetos de usuário somente na nuvem podem ser modificados por meio do PowerShell AAD. Para obter instruções detalhadas, consulte [sincronização do Azure Active Directory Connect: configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Códigos de geo
Você pode usar os códigos de três letras para especificar o Geo na propriedade **PreferredDataLocation** . A tabela a seguir lista os códigos para o Geos disponíveis:

|Geo |Código |
|---------|---------|
|Ásia/Pacífico |APC |
|Austrália |AUS |
|Canadá |CAN |
|União Europeia |EUR |
|França |FRA|
|Índia |IND |
|Japão |JPN |
|Coreia |KOR |
|Reino Unido |GBR |
|Estados Unidos |NAM |

**Observação**: as propriedades **PreferredDataLocation** e **MailboxRegion** são cadeias de caracteres com nenhuma verificação de erro. Se você inserir um valor inválido (por exemplo, NAN) a caixa de correio será colocada no Geo padrão.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Exibir o Geos disponíveis que estão configurados em sua organização do Exchange Online
Para ver a lista de Geos configurado em sua organização do Exchange Online, execute o seguinte comando no Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

A saída do comando será parecida com o seguinte:

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Modo de exibição padrão Geo para sua organização do Exchange Online
Para exibir o geo padrão da sua organização do Exchange Online, execute o seguinte comando no Exchange Online PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

A saída do comando será parecida com o seguinte:

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>Encontrar o local de Geo de uma caixa de correio
O cmdlet **Get-Mailbox** no PowerShell do Exchange Online é exibido a seguir multi-geo relacionadas a propriedades em caixas de correio:

- **Banco de dados**: as primeiro 3 letras do nome do banco de dados correspondem ao código de Geo, que informa onde a caixa de correio está localizada no momento. Caixas de correio de arquivo morto Online o **ArchiveDatabase** propriedade deve ser usada.

- **MailboxRegion**: Especifica o código de local geo que foi definido para o administrador (sincronizado a partir **PreferredDataLocation** no Azure AD).

- **MailboxRegionLastUpdateTime**: indica quando MailboxRegion última atualização (automática ou manualmente).

Para ver essas propriedades para uma caixa de correio, use a seguinte sintaxe:

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Por exemplo, para ver as informações de localização geográfica para chris@contoso.onmicrosoft.com a caixa de correio, execute o seguinte comando:

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

A saída do comando será parecida com o seguinte:

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **Observação:** Se o código de local geo no nome do banco de dados não coincidir com o valor de **MailboxRegion** , a caixa de correio será automaticamente ser colocado em uma fila de realocação e movido para o local de geo especificado pelo valor **MailboxRegion** (procura Exchange Online um incompatibilidade entre esses valores de propriedade).

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>Mover uma caixa de correio somente em nuvem existente para um Geo específico
Um usuário somente na nuvem é um usuário não sincronizadas para o inquilino via AAD se conectar. Este usuário foi criado diretamente no Azure AD. Use os cmdlets **Get-MsolUser** e **Set-MsolUser** no módulo Azure AD para Windows PowerShell para exibir ou especificar o Geo onde será armazenada caixa de correio do usuário somente na nuvem.

Para exibir o valor de **PreferredDataLocation** para um usuário, use esta sintaxe no Windows Azure AD PowerShell:

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Por exemplo, para ver o valor de **PreferredDataLocation** para michelle@contoso.onmicrosoft.com o usuário, execute o seguinte comando:

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

A saída do comando será parecida com o seguinte:

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

Para modificar o valor de **PreferredDataLocation** para um objeto de usuário somente na nuvem, use a seguinte sintaxe no Windows Azure AD PowerShell:

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Por exemplo, para definir o valor de **PreferredDataLocation** como geo a União Europeia (EUR) para michelle@contoso.onmicrosoft.com o usuário, execute o seguinte comando:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Observações**:

- Como mencionado anteriormente você não pode usar este procedimento para objetos de usuário sincronizado do Active Directory no local. Você precisa alterar o valor de **PreferredDataLocation** usando AAD se conectar. Para obter mais informações, consulte [sincronização do Azure Active Directory Connect: configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Quanto tempo levará para realocar um mailboxfrom que seu geo atual para o novo local desejado geo depende de vários fatores:
 
  - O tamanho e o tipo de caixa de correio.
 
  - O número de caixas de correio sendo movido.
 
  - A disponibilidade dos recursos de movimentação.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Move desabilitado caixas de correio que estão na retenção de litígio
Desabilitado caixas de correio em retenção de litígio que são preservadas para eDiscovery fins não podem ser movidos, alterando seu valor **PreferredDataLocation** em seu estado desabilitado. Para mover uma caixa de correio desabilitada em suspensão de litígio:

1. Atribua temporariamente uma licença à caixa de correio.

2. Altere o **PreferredDataLocation**.

3. Remova a licença da caixa de correio depois que ela foi movida para o local selecionado geo para colocá-lo novamente em estado desativado.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Criar novas caixas de correio da nuvem em um Geo específico 
Para criar uma nova caixa de correio em um local específico geo, você precisará fazer qualquer uma dessas etapas:

- Configure o valor de **PreferredDataLocation** , conforme descrito no anterior seção *antes da* que caixa de correio é criada no Exchange Online. Por exemplo, configure o valor de **PreferredDataLocation** em um usuário antes de atribuir uma licença. 

- Atribua uma licença ao mesmo tempo em que você definir o valor de **PreferredDataLocation** .

Para criar um novo somente em nuvem licenciado usuário (não AAD conectar sincronizados) em um Geo específico, use a seguinte sintaxe no Windows Azure AD PowerShell:

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
Este exemplo cria uma nova conta de usuário para Elizabeth Brunner com os seguintes valores:

- Nome principal do usuário: ebrunner@contoso.onmicrosoft.com

- Nome: Elizabeth

- Sobrenome: Brunner

- Nome para exibição Elizabeth Brunner

- Senha: gerada aleatoriamente e mostra os resultados do comando (porque não estamos usando o parâmetro *Password* )

- Licença: contoso:ENTERPRISEPREMIUM (E5)

- Local: Austrália (Austrália)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Para obter mais informações sobre como criar novas contas de usuário e Localizando LicenseAssignment valores no PowerShell do Windows Azure AD, consulte [criar contas de usuário com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [Exibir as licenças e serviços com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> **Observação:** Se você estiver usando o PowerShell do Exchange Online para habilitar uma caixa de correio e precisam ser criados diretamente a Geo especificado em **PreferredDataLocation**a caixa de correio, você precisará usar um cmdlet do Exchange Online como **Enable-Mailbox** ou **New-Mailbox **diretamente em relação ao serviço de nuvem. Se você usar o cmdlet **Enable-RemoteMailbox** local Exchange, a caixa de correio será criada no Geo padrão.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Existente onboard local caixas de correio de um específico Geo
Você pode usar as ferramentas de inclusão standard e processos para migrar uma caixa de correio de uma organização do Exchange no local para o Exchange Online, incluindo o [Painel de migração no EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e o cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) no Exchange Online PowerShell.

A primeira etapa é verificar se que existe um objeto de usuário para cada caixa de correio a ser onboarded e verifique se que o valor de **PreferredDataLocation** correto está configurado no Azure AD. As ferramentas de inclusão respeitam o valor de **PreferredDataLocation** e irá migrar as caixas de correio diretamente para o Geo especificado.

Ou então, você pode usar as seguintes etapas para caixas de correio onboard diretamente em um local específico geo usando o cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) no PowerShell do Exchange Online.

1. Verifique se que o objeto de usuário existe para cada caixa de correio a ser onboarded e que o **PreferredDataLocation** está definido como o valor desejado no Azure AD. O valor de **PreferredDataLocation** será sincronizado com o atributo **MailboxRegion** do objeto de usuário de email correspondente no Exchange Online.

2. Conecte-se diretamente para o satélite específico Geo usando as instruções de conexão do anteriormente neste tópico.

3. No PowerShell do Exchange Online, armazene as credenciais de administrador local que é usada para executar uma migração de caixa de correio em uma variável executando o seguinte comando:

    ```
    $RC = Get-Credential
    ```

4. No PowerShell do Exchange Online, crie um novo **New-MoveRequest** semelhante ao exemplo a seguir: 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Repita a etapa #4 para cada caixa de correio que você precisa para migrar do Exchange local para o local de satélite que você está atualmente conectado ao.

6. Se você precisa saber para migrar caixas de correio adicionais para um local diferente de satélite, repita as etapas 2 a 4 para cada local de satélite específico.

### <a name="multi-geo-reporting"></a>Relatórios de multi-Geo
**Relatórios de uso de Multi-Geo** no Centro de administração do Office 365 exibe a contagem de usuário pelo geo local. O relatório exibe a distribuição dos usuários para o mês atual e fornece dados históricos para os últimos seis meses.
