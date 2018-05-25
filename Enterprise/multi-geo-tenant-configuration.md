---
title: Configuração de locatário multigeográfico do Onedrive for Business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Saiba como configurar o OneDrive for Business com a funcionalidade multigeográfica.
ms.openlocfilehash: 29e69fa6e5a9715360b61024ee41dee4cd4b95b1
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>Configuração de locatário multigeográfico do Onedrive for Business

Antes de configurar o locatário para o OneDrive for Business com a funcionalidade multigeográfica, leia [Plano do OneDrive for Business com a funcionalidade multigeográfica](plan-for-multi-geo.md). Para seguir as etapas deste artigo, você precisará de uma lista de locais que deseja habilitar e os usuários de teste que deseja provisionar para esses locais.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Adicionar recursos multigeográficos no plano do Office 365 para seu locatário

Para usar o OneDrive for Business com Funcionalidades Multigeográficas, é necessário o plano _Funcionalidades Multigeográficas no Office 365_. Trabalhe com sua equipe de conta para adicionar esse plano ao locatário. A equipe de conta conectará você ao especialista em licenciamento apropriado e configurará o locatário.

Observe que o plano de _Funcionalidades Multigeográficas no Office 365_ é um plano de serviços de nível de usuário. Você precisa de uma licença para cada usuário que deseja hospedar em um local de satélite. Você pode adicionar mais licenças ao longo do tempo ao adicionar usuários em locais de satélite.

Depois que o locatário for provisionado com o plano _Funcionalidades Multigeográficas no Office 365_, a guia **Locais geográficos** será disponibilizada na [Centro de administração do OneDrive](https://admin.onedrive.com).

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Defina Locais de Dados Permitidos (ADL) para seu locatário

Você deve definir um Local de Dados Permitido para o SharePoint para cada localização geográfica onde deseja usar o OneDrive for Business. As localizações geográficas disponíveis são mostradas na seguinte tabela:

<table>
<thead>
<tr class="header">
<th align="left"><strong>Localização</strong></th>
<th align="left"><strong>Código</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">América do Norte</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">Europa/Oriente Médio/África</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Ásia – Pacífico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Austrália</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Japão</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Canadá</td>
<td align="left">CAN</td>
</tr>
<tr class="odd">
<td align="left">Reino Unido</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">Coreia</td>
<td align="left">KOR</td>
</tr>
</tbody>
</table>

Para adicionar um local geográfico de satélite

1. Abra o [Centro de administração do OneDrive](https://admin.onedrive.com)

2. Navegue até a guia **Localizações geográficas**.

3. Clique em **Adicionar local**.

4. Selecione o local que você deseja adicionar e clique em **Avançar**.

5. Digite o domínio que você deseja usar com a localização geográfica e clique em **Adicionar**.

6. Clique em **Fechar**.

O provisionamento pode levar desde algumas horas até 72 horas, dependendo do tamanho do locatário. Depois que o provisionamento de um local de satélite for concluído, você receberá um email de confirmação. Quando o novo local geográfico for exibido em azul no mapa na guia **Localizações geográficas** no Centro de administração do OneDrive, você poderá definir o local preferencial de dados dos usuários como essa localização geográfica. 

> [!IMPORTANT]
> A nova localização geográfica de satélite será definida com configurações padrão. Isso permitirá configurar a localização geográfica de acordo com suas necessidades de conformidade local.

## <a name="setting-users-preferred-data-location"></a>Definir o local der dados preferencial dos usuários
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Depois de habilitar as localizações de dados necessárias, você pode atualizar as contas de usuário para usar o local de dados apropriado. É recomendável definir um local preferencial de dados para todos os usuários, mesmo que o usuário permaneça no local de dados padrão.

> [!TIP]
> É recomendável começar validações com um usuário de teste ou um pequeno grupo de usuários antes de implantar Funcionalidades Multigeográficas em sua organização mais ampla.

Há dois tipos de objetos de usuário no AAD: usuários somente de nuvem e usuários sincronizados. Siga as instruções apropriadas para o tipo de usuário.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Sincronizar o local de dados preferencial do usuário usando o AD Connect 

Se os usuários da empresa são sincronizados com um sistema do AD (Active Directory) no local ao AAD (Azure Active Directory), PreferredDataLocation deve ser populado no AD e sincronizado com o AAD. Siga o processo em [Sincronização do Azure AD Connect: fazer uma alteração na configuração padrão](https://docs.microsoft.com/pt-BR/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) para configurar a sincronização de local preferencial de dados do AD local para o AAD.

Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.

> [!IMPORTANT]
> Para novos usuários sem o OneDrive provisionado, aguarde pelo menos 24 horas após o PDL do usuário ser sincronizado com o AAD para que as alterações se propaguem antes que o usuário faça logon no OneDrive for Business. (Configurar o local preferencial de dados antes que o usuário faça logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Configurar local de dados preferencial para usuários somente na nuvem 

Se os usuários da empresa não estiverem sincronizados de um sistema do AD (Active Directory) local para o AAD (Azure Active Directory), ou seja, são criados no Office 365 ou no AAD, o PDL deverá ser definido usando o PowerShell do AAD.

Os procedimentos desta seção exigem o [Módulo do Microsoft Azure Active Directory para o Módulo do Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se você já tiver instalado o PowerShell do AAD, atualize para a versão mais recente.

1.  Abra o Módulo Microsoft Azure Active Directory para Windows PowerShell.

2.  Execute o `Connect-MsolService` e insira as credenciais de administrador global do locatário.

3.  Use o cmdlet [Set-MsolUser](https://docs.microsoft.com/pt-BR/powershell/msonline/v1/set-msoluser) para definir o local preferencial de dados para cada um dos usuários. Por exemplo:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Você pode confirmar se o local preferencial de dados foi atualizado corretamente usando o cmdlet Get-MsolUser. Por exemplo:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.

> [!IMPORTANT]
> Para novos usuários sem o OneDrive provisionado, aguarde pelo menos 24 horas após o PDL do usuário ser definido para que as alterações se propaguem antes que o usuário faça logon no OneDrive do SharePoint. (Configurar o local preferencial de dados antes que o usuário faça logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Provisionamento do OneNote e efeito de PDL

Se o usuário já tiver um site do OneDrive criado no locatário, configurar o PDL não moverá automaticamente o OneDrive existente. Para mover o OneDrive de um usuário, confira [Movimentação geográfica do OneDrive for Business](move-onedrive-between-geo-locations.md). Siga as instruções em Mover o OneDrive entre locais geográficos.

Se o usuário não tiver um site do OneDrive no locatário, o OneDrive será provisionado para ele de acordo com o valor de PDL, supondo que o PDL do usuário corresponda a um dos locais de dados permitidos (ADLs) da empresa.

## <a name="configuring-multi-geo-search"></a>Configurar pesquisa multigeográfica

O locatário com Funcionalidades Multigeográficas terá recursos de pesquisa agregados, permitindo que uma consulta de pesquisa retorne resultados de praticamente qualquer lugar no locatário.

Por padrão, pesquisas desses pontos de entrada retornam resultados agregados, mesmo que cada índice de pesquisa esteja em sua localização geográfica relevante:

- OneDrive for business

- Delve

- Página inicial do SharePoint

- Centro de Pesquisa

Além disso, recursos de pesquisa multigeográfica podem ser configurados para os aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint.

Examine [Configurar a pesquisa para o OneDrive for Business com a funcionalidade multigeográfica](configure-search-for-multi-geo.md) para obter instruções, incluindo limitações e diferenças.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Validar a configuração multigeográfica do OneDrive for Business

Veja a seguir alguns casos de uso básicos que convém incluir em seu plano de validação antes de implantar amplamente o OneDrive for Business com Funcionalidades Multigeográficas em sua empresa. Depois de concluir essas testes e os casos de uso mais relevantes para sua empresa, você pode optar por adicionar os usuários em seu grupo piloto inicial.

**OneDrive for Business**

Selecione o OneDrive por meio do inicializador de aplicativos do Office 365 e confirme se você será direcionado automaticamente para a localização geográfica apropriada do usuário, com base no PDL do usuário. O OneDrive for Business agora deve iniciar o provisionamento nesse local. Após o provisionamento, tente carregar e baixar alguns documentos.

**Aplicativo móvel do OneDrive**

Faça logon no aplicativo móvel do OneDrive com suas credenciais de conta de teste. Confirme se você pode ver os arquivos do OneDrive for Business e se pode interagir com eles no dispositivo móvel.

**Cliente de sincronização do OneDrive**

Confirme que o cliente de sincronização do OneDrive detecta automaticamente a localização geográfica do OneDrive for Business após o logon. Se você precisar baixar o cliente de sincronização, clique em **Sincronização** na biblioteca do OneDrive.

**Aplicativos do Office**

Confirme que você pode acessar o OneDrive for Business fazendo logon de um aplicativo do Office, como o Word. Abra o aplicativo do Office e selecione "OneDrive – <TenantName>". O Office detectará o local do OneDrive e mostrará os arquivos que você pode abrir.

**Compartilhamento**

Tente compartilhar arquivos do OneDrive. Confirme se o seletor de pessoas mostra todos os usuários online do SharePoint, independentemente da localização geográfica.
