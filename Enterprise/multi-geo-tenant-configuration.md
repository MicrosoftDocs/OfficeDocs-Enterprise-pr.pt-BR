---
title: Configuração de um locatário do Office 365 multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Saiba como configurar o Office 365 multigeográfico.
ms.openlocfilehash: e1e76482e6b775a2bb1b6ea4428112af738d6a5a
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070005"
---
# <a name="office-365-multi-geo-tenant-configuration"></a>Configuração de um locatário do Office 365 multigeográfico

Antes de configurar seu locatário do Office 365 multigeográfico, certifique-se de que você leu o [Plano para o Office 365 multigeográfico](plan-for-multi-geo.md). Para seguir as etapas neste artigo, você precisará de uma lista de localizações geográficas que você deseja habilitar como locais de satélite e os usuários de teste que você deseja provisionar para esses locais.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Adicionar recursos multigeográficos no plano do Office 365 para seu locatário

Para usar o Office 365 multigeográfico, é necessário o plano _Funcionalidades Multigeográficas no Office 365_. Trabalhar com sua equipe de conta para adicionar este plano para seu locatário. Sua equipe de conectará você com o especialista de licenciamento apropriado e fará a configuração do seu locatário.

Observe que o plano de _Funcionalidades Multigeográficas no Office 365_ é um plano de serviços de nível de usuário. Você precisa de uma licença para cada usuário que deseja hospedar em um local de satélite. Você pode adicionar mais licenças ao longo do tempo ao adicionar usuários em locais de satélite.

Depois que o locatário for provisionado com o plano  _Funcionalidades Multigeográficas no Office 365_, a guia **Localizaões geográficas** será disponibilizada no OneDrive e no Centro de administração do SharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>Adicionar locais de satélites ao seu locatário

Você deve adicionar um local de satélite para cada localização geográfica onde você deseja armazenar dados. As localizações geográficas disponíveis são mostrados na tabela a seguir:

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Captura de tela da página de localizações geográficas do centro de administração do SharePoint](media/sharepoint-multi-geo-admin-center.png)

Para adicionar um local de satélite

1. Abra o Centro de Administração do SharePoint.

2. Navegue até a guia **Localizações geográficas**.

3. Clique em **Adicionar local**.

4. Selecione o local que você deseja adicionar e clique em **Avançar**.

5. Digite o domínio que você deseja usar com a localização geográfica e clique em **Adicionar**.

6. Clique em **Fechar**.

O provisionamento pode levar desde algumas horas até 72 horas, dependendo do tamanho de seu locatário. Depois que o provisionamento de uma localização satélite for concluído, você receberá um email de confirmação. Quando o novo local geográfico for exibido em azul no mapa na guia **Localizações geográficas** no Centro de administração do OneDrive, você poderá definir o local preferencial de dados dos usuários como essa localização geográfica. 

> [!IMPORTANT]
> A nova localização satélite será definida com configurações padrão. Isso permitirá configurar a localização satélite de acordo com suas necessidades locais de conformidade.

## <a name="setting-users-preferred-data-location"></a>Defina o local de dados preferencial dos usuários
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Depois de habilitar as localizações satélites necessárias, você pode atualizar as contas de usuários para usar o local de dados de sua preferência. É recomendável definir um local preferencial de dados para todos os usuários, mesmo que o usuário permaneça no local de dados central.

> [!IMPORTANT]
> Se o local de dados preferencial do usuário for definido em um local que não foi configurado como um local de satélite ou um local central, o sistema adotará como padrão o local central ao provisionar sites do OneDrive e do SharePoint e caixas de correio de Grupo.

> [!TIP]
> É recomendável começar validações com um usuário de teste ou um pequeno grupo de usuários antes de implantar Funcionalidades Multigeográficas em sua organização de forma mais ampla.

Há dois tipos de objetos de usuário no Azure Active Directory: usuários somente nuvem e usuários sincronizados. Siga as instruções apropriadas para o seu tipo de usuário.

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a>Sincronizar o local de dados preferencial do usuário usando o Azure Active Directory Connect 

Se os usuários da empresa são sincronizados de um sistema local do AD (Active Directory) ao AAD (Azure Active Directory), o PreferredDataLocation deve ser preenchido no AD e sincronizado com o AAD. Siga o processo em [Sincronização do Azure AD Connect: configurar o local preferencial de dados para recursos do Office 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) para configurar a sincronização do local preferencial de dados do Active Directory local com o Azure Active Directory.

Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.

> [!IMPORTANT]
> Para novos usuários sem o OneDrive provisionado, aguarde pelo menos de 24 horas após o PDL do usuário ser sincronizado com o Azure Active Directory para que as alterações se propaguem antes de fazer logon no OneDrive for Business. (Configurar o Local de Dados Preferencial antes do usuário fazer o logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Configurar Local de Dados Preferencial para usuários somente na nuvem 

Se os usuários da empresa não estiverem sincronizados a partir de um sistema do Active Directory local para o Azure Active Directory, o que significa que são criados no Office 365 ou no Azure Active Directory, o PDL deverá ser definido usando o PowerShell do Azure Active Directory.

Os procedimentos desta seção exigem o [Módulo do Microsoft Azure Active Directory para o Módulo do Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se você já tiver instalado o PowerShell do Azure Active Directory, não se esqueça de atualizar para a versão mais recente.

1.  Abra o Módulo Microsoft Azure Active Directory para Windows PowerShell.

2.  Execute o `Connect-MsolService` e insira as credenciais de administrador global do locatário.

3.  Use o cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) para definir o local preferencial de dados para cada um dos usuários. Por exemplo:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Você pode confirmar se o local preferencial de dados foi atualizado corretamente usando o cmdlet Get-MsolUser. Por exemplo:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Captura de tela de uma janela do PowerShell mostrando o conjunto-msoluser](media/multi-geo-tenant-configuration-image3.png)

Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.

> [!IMPORTANT]
> Para novos usuários sem o OneDrive provisionado, aguarde pelo menos de 24 horas após o PDL ser feito para que as alterações se propaguem antes de fazer logon no OneDrive. (Configurar o Local de Dados Preferencial antes do usuário fazer o logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Provisionamento do OneNote e efeito de PDL

Se o usuário já tiver um site do OneDrive criado no locatário, configurar o PDL não moverá automaticamente o OneDrive existente. Para mover o OneDrive de um usuário, confira [Movimentação Geográfica do OneDrive for Business](move-onedrive-between-geo-locations.md) siga as instruções em Mover o OneDrive entre localizações geográfica. (Observe que a caixa de correio do Exchange do usuário não move automaticamente quando ao definir o PDL do usuário.)

Se o usuário não tiver um site do OneDrive no locatário, o OneDrive será provisionado para ele de acordo com o valor do PDL, supondo que o PDL do usuário corresponda a um dos locais de satélites da empresa.

## <a name="configuring-multi-geo-search"></a>Configurar pesquisa multigeográfica

O locatário com Funcionalidades Multigeográficas terá recursos de pesquisa agregados, permitindo que uma consulta de pesquisa retorne resultados de praticamente qualquer lugar no locatário.

Por padrão, pesquisas desses pontos de entrada retornam resultados agregados, mesmo que cada índice de pesquisa esteja em sua localização geográfica relevante:

- OneDrive for business

- Delve

- Página inicial do SharePoint

- Centro de Pesquisa

Além disso, recursos de pesquisa multigeográfica podem ser configurados para os aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint.

Examine [Configurar a pesquisa para o OneDrive for Business com a funcionalidade multigeográfica](configure-search-for-multi-geo.md) para obter instruções, incluindo limitações e diferenças.

## <a name="validating-the-office-365-multi-geo-configuration"></a>Validar a configuração do Office 365 multigeográfico

Veja a seguir alguns casos de uso básico que você pode incluir em seu plano de validação antes de implementar o Office 365 multigeográficolargamente em sua empresa. Depois de concluir esses testes e os casos de uso mais relevantes para sua empresa, você pode optar por prosseguir e adicionar os usuários em seu grupo piloto inicial.

**OneDrive for Business**

Selecione o OneDrive no inicializador de aplicativos do Office 365 e confirme que você será direcionado automaticamente para a localização geográfica apropriada do usuário com base no PDL do usuário. OneDrive for Business agora vai começar a provisionar nesse local. Uma vez provisionado, tente carregar e baixar alguns documentos.

**Aplicativo móvel do OneDrive**

Faça logon no aplicativo móvel do OneDrive com suas credenciais de conta de teste. Confirme se você pode ver os arquivos do OneDrive for Business e se pode interagir com eles no dispositivo móvel.

**Cliente de sincronização do OneDrive**

Confirme que o cliente de sincronização do OneDrive detecta automaticamente a localização geográfica do OneDrive for Business após o logon. Se você precisar baixar o cliente de sincronização, clique em **Sincronização** na biblioteca do OneDrive.

**Aplicativos do Office**

Confirme que você pode acessar o OneDrive for Business fazendo logon de um aplicativo do Office, como o Word. Abra o aplicativo do Office e selecione "OneDrive – <TenantName>". O Office detectará o local do OneDrive e mostrará os arquivos que você pode abrir.

**Compartilhamento**

Tente compartilhar arquivos do OneDrive. Confirme se o seletor de pessoas mostra todos os usuários online do SharePoint, independentemente da localização geográfica.
