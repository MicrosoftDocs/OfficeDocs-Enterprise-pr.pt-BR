---
title: Recursos de multi-Geo no Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Expanda sua presença do Office 365 para várias regiões geográficas com os recursos de multi-geo no Exchange Online.
ms.openlocfilehash: ea00ab52142e92e122273ab4ba718e98bd94b572
ms.sourcegitcommit: 12d3223cc2d6bf39a8960409a923254e1790fd2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Recursos de multi-Geo no Exchange Online

Recursos de multi-Geo no Office 365 habilitar um único locatário englobe vários locais geográficos (Geos). Quando Multi-Geo estiver habilitada, os clientes podem selecionar o local do conteúdo de caixa de correio Exchange Online (dados em repouso) em uma base por usuário.

Seu local de locatário inicial (conhecido como seus "padrão" ou "central" local) é determinada com base em seu endereço de cobrança. Quando Multi-Geo estiver habilitada, você pode colocar a caixas de correio em locais adicionais "satélite" por:

- Criando uma nova caixa de correio Exchange Online diretamente em um satélite.

- Mover uma caixa de correio do Exchange Online existente para um satélite.

- Inclusão de uma caixa de correio de uma organização do Exchange local diretamente em um satélite.

Os Geos a seguintes estão disponíveis para uso em uma configuração de Multi-Geo:

- Ásia Pacífico

- Austrália

- Canadá

- União Europeia

- Índia (atualmente disponível apenas a clientes com os endereços de cobrança na Índia)

- Japão

- Coreia

- Reino Unido

- Estados Unidos

## <a name="prerequisite-configuration"></a>Configuração de pré-requisito
Antes de começar a usar o Multi-Geo recursos no Exchange Online, o Microsoft precisa configurar seu locatário do Exchange Online para suporte Multi-Geo. Esse processo de configuração de uma única vez é disparado quando você solicitar licenças Multi-Geo e geralmente deve levar menos de 30 dias para ser concluída.

Você receberá notificações no [Centro de mensagem do Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) quando sua configuração tiver iniciado e concluído. Configuração automaticamente é disparada quando você adquirir licenças de Multi-Geo.

## <a name="mailbox-placement-and-moves"></a>Movimentações e posicionamento de caixa de correio
Após a conclusão da Microsoft as etapas de configuração de Multi-Geo pré-requisito, o Exchange Online aceita o atributo **PreferredDataLocation** em objetos de usuário no Windows Azure AD.

O Exchange Online sincroniza a propriedade **PreferredDataLocation** do Azure AD para a propriedade **MailboxRegion** no serviço de diretório Exchange Online. O valor **MailboxRegion** determina o Geo onde caixas de correio de usuário e qualquer caixa de correio de arquivo morto associada será colocada. Não é possível configurar da caixa de correio e arquivamento caixas de correio primárias um usuário para residir em Geos diferentes. Apenas um Geo pode ser configurado por um objeto de usuário.

- Quando **PreferredDataLocation** estiver configurada em um usuário com uma caixa de correio existente, a caixa de correio será movida automaticamente para o Geo especificado. 

- Quando **PreferredDataLocation** estiver configurada em um usuário sem uma caixa de correio existente, a caixa de correio será provisionada para o Geo especificado. 

- Se nenhum Geo for especificado, a caixa de correio será colocada no Geo padrão.

**Observação**: capacidades de Multi-Geo e Skype para Business Online regional hospedada reuniões usam a propriedade **PreferredDataLocation** nos objetos de usuário para localizar serviços. Se você configurar valores **PreferredDataLocation** em objetos de usuário para reuniões regional hospedadas, a caixa de correio dos usuários serão automaticamente movida para o Geo especificado depois Multi-Geo está habilitado no inquilino do Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitações do recurso para Multi-Geo no Exchange Online
1. Apenas caixas de correio do usuário, caixas de correio de recurso (caixas de correio de sala e equipamento) e caixas de correio compartilhadas suportam recursos de Multi-Geo. Caixas de correio de pasta pública e grupos do Office 365 só podem ser colocados em Geo de página inicial do cliente.
 
2. Segurança e conformidade recursos (por exemplo, auditoria e descoberta eletrônica) que estão disponíveis no Centro de administração do Exchange (EAC) não estão disponíveis nas organizações Multi-Geo. Em vez disso, você precisará usar o [Centro de conformidade e segurança do Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar recursos de segurança e conformidade.

3. Outlook para Mac usuários perceba uma perda temporária de acesso a sua pasta de arquivo morto Online enquanto você move suas caixas de correio para um novo Geo. Esta condição ocorre quando o principal do usuário e caixas de correio de arquivo morto estejam em Geos diferentes, porque cross-Geo movimentações de caixa de correio podem ser concluído em momentos diferentes.

4. Os usuários não podem compartilhar *pastas de caixa de correio* entre Geos no Outlook na web (anteriormente conhecido como o Outlook Web App ou no OWA). Por exemplo, um usuário na União Europeia não pode usar o Outlook na web para abrir uma pasta compartilhada em uma caixa de correio que está localizada nos Estados Unidos. No entanto, o Outlook em que os usuários da web pode abrir *outras caixas de correio* em diferentes Geos usando uma janela separada do navegador, conforme descrito em [Abrir a caixa de correio de outra pessoa em uma janela separada do navegador no Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Observação**: o compartilhamento de pasta de caixa de correio entre-Geo é suportado no Outlook no Windows.

5. Atualmente, a delegação de calendário entre-Geo não é suportada no Outlook na web. Delegação de calendário entre-Geo é suportada no Outlook no Windows.

## <a name="administration"></a>Administração 
PowerShell remoto é necessária para exibir e configurar propriedades relacionadas ao Geo no seu ambiente do Office 365. Para obter informações sobre vários módulos do PowerShell usados para administrar o Office 365, consulte [Gerenciando o Office 365 e o Exchange Online com o Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- É necessário o [Módulo Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 ou posterior em v1. x para ver a propriedade **PreferredDataLocation** em objetos de usuário. Para se conectar ao AD do Windows Azure PowerShell, consulte [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Para conectar ao Exchange Online PowerShell, consulte [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Conectar-se diretamente a um Geo específico usando o PowerShell do Exchange Online
Normalmente, o Exchange Online PowerShell se conectará ao Geo padrão. Porém, você também pode conectar diretamente à Geos não-padrão. Devido aos aprimoramentos de desempenho, recomendamos que você se conectando diretamente ao Geo não-padrão, quando você gerencia somente usuários em que Geo.

Para conectar a um Geo específico, o parâmetro *ConnectionUri* é diferente das instruções de conexão regular. O restante dos comandos e valores são os mesmos. As etapas são:

1. No computador local, abra o Windows PowerShell e execute o seguinte comando:
    
    ```
    $UserCredential = Get-Credential
    ```
   Na caixa de diálogo **Solicitação de credencial do Windows PowerShell** , digite seu trabalho escola conta e senha e clique em **Okey**.
    
2. Substituir `<emailaddress>` com o endereço de email de **qualquer** caixa de correio de destino Geo e execute o comando a seguir. Suas permissões na caixa de correio e a relação com suas credenciais na etapa 1 não são um fator; o endereço de email simplesmente informa o Exchange Online onde para se conectar.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Por exemplo, se olga@contoso.onmicrosoft.com é o endereço de email de uma caixa de correio válida do Geo que você deseja se conectar, execute o seguinte comando:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Execute o comando a seguir:
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Requisitos de versão do Azure AD Connect
Conectar AAD versão 1.1.524.0 ou posterior é o único método suportado para definir a propriedade **PreferredDataLocation** nos objetos de usuário que são sincronizados do Active Directory no local. Para obter instruções detalhadas, consulte [sincronização do Azure Active Directory Connect: configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Códigos de geo
Você pode usar os códigos de três letras para especificar o Geo na propriedade **PreferredDataLocation** . A tabela a seguir lista os códigos para o Geos disponíveis:

|Geo |Código |
|---------|---------|
|Ásia/Pacífico |APC |
|Austrália |AUSTRÁLIA |
|Canadá |PODE |
|União Europeia |EUR |
|Índia |IND |
|Japão |JAPONÊS |
|Coreia |KOR |
|Reino Unido |GBR |
|Estados Unidos |NOME |

**Observação**: as propriedades **PreferredDataLocation** e **MailboxRegion** são cadeias de caracteres com nenhuma verificação de erro. Se você inserir um valor inválido (por exemplo, NAN) a caixa de correio será colocada no Geo padrão.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Exibir o Geos disponíveis que estão configurados em sua organização do Exchange Online
Para ver a lista de Geos configurado em sua organização do Exchange Online, execute o seguinte comando no Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

A saída do comando será parecida com o seguinte:

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a>Encontrar o local de Geo de uma caixa de correio
O cmdlet **Get-Mailbox** no Exchange Online PowerShell exibirá as seguintes propriedades relacionadas ao Geo em caixas de correio:

- **Banco de dados**: as primeiro 3 letras do nome do banco de dados correspondem ao código de Geo, que informa onde a caixa de correio está localizada no momento.

- **MailboxRegion**: Especifica o código de Geo que foi definido para o administrador (sincronizado a partir **PreferredDataLocation** no Azure AD).

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

> [!NOTE]
> Se o código Geo no nome do banco de dados não coincidir com o valor de **MailboxRegion** , a caixa de correio será movida automaticamente para o Geo especificado pelo valor **MailboxRegion** (Exchange Online parecidas uma incompatibilidade entre esses valores de propriedade).

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a>Mover uma caixa de correio da nuvem existente para um Geo específico
Use os cmdlets **Get-MsolUser** e **Set-MsolUser** no módulo Azure AD para Windows PowerShell para exibir ou especificar o Geo qual caixa de correio do usuário será armazenada.

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

Por exemplo, para definir o valor de **PreferredDataLocation** para a União Europeia (EUR) para michelle@contoso.onmicrosoft.com o usuário, execute o seguinte comando:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Observações**:

- Conforme mencionado anteriormente para objetos de usuário sincronizado do Active Directory no local, você não pode usar este procedimento. Você precisa alterar o valor de **PreferredDataLocation** usando AAD se conectar. Para obter mais informações, consulte [sincronização do Azure Active Directory Connect: configurar o local dos dados preferencial para recursos do Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Quanto tempo leva para mover uma caixa de correio depende de vários fatores:
 
  - O tamanho e o tipo de caixa de correio.
 
  - O número de caixas de correio sendo movido.
 
  - A disponibilidade dos recursos de movimentação.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Move desabilitado caixas de correio que estão na retenção de litígio
Desabilitado caixas de correio em retenção de litígio que são preservadas para eDiscovery fins não podem ser movidos, alterando seu valor **PreferredDataLocation** em seu estado desabilitado. Para mover uma caixa de correio desabilitada em suspensão de litígio:

1. Atribua temporariamente uma licença à caixa de correio.

2. Altere o **PreferredDataLocation**.

3. Remova a licença da caixa de correio depois que ela foi movida para a localização geográfica selecionada para colocá-lo novamente em estado desativado.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Criar novas caixas de correio da nuvem em um Geo específico 
Para criar uma nova caixa de correio em um Geo específico, você precisará fazer qualquer uma dessas etapas:

- Configure o valor de **PreferredDataLocation** , conforme descrito em anterior seção *antes da* caixa de correio é criada no Exchange Online (por exemplo, definindo o valor de **PreferredDataLocation** em um usuário antes de atribuir uma licença). 

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

Local de 3: Austrália (Austrália)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Para obter mais informações sobre como criar novas contas de usuário e Localizando LicenseAssignment valores no PowerShell do Windows Azure AD, consulte [criar contas de usuário com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [Exibir as licenças e serviços com o Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> [!NOTE]
> Se você estiver usando o PowerShell do Exchange para habilitar uma caixa de correio e precisam ser criados diretamente a Geo especificado em **PreferredDataLocation**a caixa de correio, você precisará usar um cmdlet do Exchange Online como **Enable-Mailbox** ou **New-Mailbox** diretamente contra o serviço de nuvem. Se você usar o cmdlet **Enable-RemoteMailbox** local Exchange, a caixa de correio será criada no Geo padrão.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Existente onboard local caixas de correio de um específico Geo
Você pode usar as ferramentas de inclusão standard e processos para migrar uma caixa de correio de uma organização do Exchange no local para o Exchange Online, incluindo o [Painel de migração no EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e o cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) no Exchange Online PowerShell.

A primeira etapa é verificar se que existe um objeto de usuário para cada caixa de correio a ser onboarded e verifique se que o valor de **PreferredDataLocation** correto está configurado no Azure AD. As ferramentas de inclusão respeitam o valor de **PreferredDataLocation** e irá migrar as caixas de correio diretamente para o Geo especificado.

Ou então, você pode usar as seguintes etapas para caixas de correio onboard diretamente em um Geo específico usando o cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) no PowerShell do Exchange Online.

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

5. Repita a etapa #4 para cada caixa de correio que você precisa para migrar do Exchange local para o satélite Geo que você está conectado atualmente.

6. Se você precisar migrar caixas de correio adicionais para um satélite diferente Geo, repita as etapas 2 a 4 para cada Geo de satélite específico.

### <a name="multi-geo-reporting"></a>Relatórios de multi-Geo
**Relatórios de uso de Multi-Geo** no Centro de administração do Office 365 exibe a contagem de usuários por Geo. O relatório exibe a distribuição dos usuários para o mês atual e fornece dados históricos para os últimos seis meses.
 
