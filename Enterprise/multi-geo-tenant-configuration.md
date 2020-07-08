---
title: Configuração do locatário do Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Aprenda a configurar o Microsoft 365 Multi-Geo.
ms.openlocfilehash: 928033dcbec0ad0b52f24bd0bec4dd6b9f9331bc
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052564"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Configuração do locatário do Microsoft 365 Multi-Geo

Antes de configurar seu locatário do Microsoft 365 Multi-Ge, certifique-se de que você leu o [Plano do Microsoft 365 Multi-Geo](plan-for-multi-geo.md). Para seguir as etapas neste artigo, você precisará de uma lista de localizações geográficas que você deseja habilitar como locais de satélite e os usuários de teste que você deseja provisionar para esses locais.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Adicionar o funcionalidades multigeográficas no Microsoft 365 ao seu locatário

Para usar o Microsoft 365 Multi-Geo, você precisa dos _Recursos Multi-Geo no plano do Microsoft 365_. Trabalhar com sua equipe de conta para adicionar este plano para seu locatário. Sua equipe de conectará você com o especialista de licenciamento apropriado e fará a configuração do seu locatário.

Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.

Depois que seu locatário for provisionado com os _Recursos de várias regiões no plano do Microsoft 365_, a guia **Locais geográficos** ficará disponível nos centros de administração do OneDrive e do SharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>Adicionar locais de satélites ao seu locatário

Você deve adicionar um local de satélite para cada localização geográfica onde você deseja armazenar dados. As localizações geográficas disponíveis são mostrados na tabela a seguir:

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Captura de tela da página de localizações geográficas do centro de administração do SharePoint](media/sharepoint-multi-geo-admin-center.png)

Para adicionar um local de satélite

1. Abra o Centro de Administração do SharePoint.

2. Navegue até a guia **Localizações geográficas**.

3. Clique em **Adicionar local**.

4. Selecione o local que você deseja adicionar e clique em **Avançar**.

5. Digite o domínio que você deseja usar com a localização geográfica e clique em **Adicionar**.

6. Clique em **Fechar**.

Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location. 

> [!IMPORTANT]
> Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.

## <a name="setting-users-preferred-data-location"></a>Defina o local de dados preferencial dos usuários
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.

> [!IMPORTANT]
> Se o local de dados preferencial do usuário for definido em um local que não foi configurado como um local de satélite ou um local central, o sistema adotará como padrão o local central ao provisionar sites do OneDrive e do SharePoint e caixas de correio de Grupo.

> [!TIP]
> É recomendável começar validações com um usuário de teste ou um pequeno grupo de usuários antes de implantar Funcionalidades Multigeográficas em sua organização de forma mais ampla.

Há dois tipos de objetos de usuário no Azure Active Directory: usuários somente nuvem e usuários sincronizados. Siga as instruções apropriadas para o seu tipo de usuário.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Sincronizar o Local de Dados Preferencial do usuário usando o Azure AD Connect 

Se os usuários de sua empresa estiverem sincronizados de um sistema local do Active Directory para o Azure AD, seu PreferredDataLocation deve ser preenchido no AD e sincronizado com o Azure AD.

Siga o processo na [Sincronização do Azure Active Directory Connect: configure o local preferencial de dados para os recursos do Microsoft 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) para configurar a sincronização do local preferencial de dados dos serviços de domínio do Active Directory (AD DS) local para o Azure AD.

Recomendamos que você inclua o Local de Dados Preferencial do usuário na configuração como parte do fluxo de trabalho de criação de usuário padrão.

> [!IMPORTANT]
> Para novos usuários sem o OneDrive provisionado, aguarde pelo menos 24 horas após o PDL do usuário ser sincronizado com o Azure AD para que as alterações se propaguem antes de fazer logon no OneDrive for Business. (Configurar o Local de Dados Preferencial antes do usuário fazer o logon para provisionar o OneDrive for Business garante que o novo OneDrive do usuário seja provisionado no local correto.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Configurar Local de Dados Preferencial para usuários somente na nuvem 

Se os usuários da sua empresa não forem sincronizados de um sistema Active Directory local com o Azure AD, significando que eles são criados no Microsoft 365 ou no Azure AD, então a PDL deve ser definida usando o Módulo Microsoft Azure Active Directory para Windows PowerShell.

Os procedimentos nessa seção exigem o [Módulo Microsoft Azure Active Directory para Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se você já tiver esse módulo, certifique-se de atualizar para a versão mais recente.

1.  [Conecte-se e entre](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) com um conjunto de credenciais de administrador global para o seu locatário.

2.  Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:

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

- OneDrive for Business

- Delve

- Página inicial do SharePoint

- Centro de Pesquisa

Além disso, recursos de pesquisa multigeográfica podem ser configurados para os aplicativos de pesquisa personalizados que usam a API de pesquisa do SharePoint.

Examine [Configurar a pesquisa para o OneDrive for Business com a funcionalidade multigeográfica](configure-search-for-multi-geo.md) para obter instruções, incluindo limitações e diferenças.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Validar a configuração do Microsoft 365 Multi-Geo

Abaixo estão alguns casos de uso básicos que você pode incluir no seu plano de validação antes de lançar amplamente o Microsoft 365 Multi-Geo na sua empresa. Depois de concluir esses testes e os casos de uso mais relevantes para sua empresa, você pode optar por prosseguir e adicionar os usuários em seu grupo piloto inicial.

**OneDrive for Business**

Selecione o OneDrive no iniciador de aplicativos do Microsoft 365 e confirme se você é direcionado automaticamente para o local geográfico apropriado para o usuário, com base na PDL do usuário. OneDrive for Business agora vai começar a provisionar nesse local. Uma vez provisionado, tente carregar e baixar alguns documentos.

**Aplicativo móvel do OneDrive**

Faça logon no aplicativo móvel do OneDrive com as credenciais da sua conta de teste. Confirme se você pode ver os arquivos do OneDrive for Business e se pode interagir com eles no dispositivo móvel.

**Cliente de sincronização do OneDrive**

Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.

**Aplicativos do Office**

Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.

**Compartilhamento**

Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.
