---
title: OneDrive para configuração do inquilino de negócios Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Saiba como configurar o OneDrive for Business Multi-Geo.
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive para configuração do inquilino de negócios Multi-Geo

Antes de configurar seu locatário do OneDrive for Business Multi-Geo, certifique-se de que você leu a [Planejar o OneDrive for Business Multi-Geo](plan-for-multi-geo.md). Para executar as etapas neste artigo, você precisará de uma lista de locais de que você deseja habilitar e os usuários de teste que você deseja provisionar para esses locais.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Adicionar as capacidades de Multi-Geo no plano do Office 365 para seu locatário

Para usar o OneDrive for Business Multi-Geo, você precisa ter o plano de _Recursos de Multi-Geo no Office 365_ . Trabalhar com sua equipe de conta para adicionar a este plano de seu locatário. Sua equipe de conta será conectá-lo com a especialista em licenciamento apropriada e obtenha seu locatário configurado.

Observe que o plano de _Recursos de Multi-Geo no Office 365_ é um plano de serviço de nível do usuário. Você precisa de uma licença para cada usuário que você deseja hospedar em um local de setellite. Você pode adicionar mais licenças ao longo do tempo à medida que você adiciona usuários nos locais de satélite.

Quando seu locatário tenha sido provisionado com o plano de _Recursos de Multi-Geo no Office 365_ , na guia **locais Geo** estará disponível no [Centro de administração do OneDrive](https://admin.onedrive.com).

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Definir os locais de dados permitido (ADL) ao seu locatário

Você deve definir o local dos dados uma permissão do SharePoint para cada localização geográfica onde você deseja usar o OneDrive for Business. Locais de geo disponíveis são mostradas na tabela a seguir:

<table>
<thead>
<tr class="header">
<th align="left"><strong>Local</strong></th>
<th align="left"><strong>Código</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">América do Norte</td>
<td align="left">NOME</td>
</tr>
<tr class="even">
<td align="left">Europa / Oriente Médio / África</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Pacífico Asiático</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Austrália</td>
<td align="left">AUSTRÁLIA</td>
</tr>
<tr class="odd">
<td align="left">Japão</td>
<td align="left">JAPONÊS</td>
</tr>
<tr class="even">
<td align="left">Canadá</td>
<td align="left">PODE</td>
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

Para adicionar um local de geo satélite

1. Abra o [Centro de administração do OneDrive](https://admin.onedrive.com).

2. Navegue até a guia **Geo locais** .

3. Clique em **Adicionar local**.

4. Selecione o local que você deseja adicionar e clique em **Avançar**.

5. Digite o domínio que você deseja usar com o local de geo e, em seguida, clique em **Adicionar**.

6. Clique em **Fechar**.

Depois de concluído o provisionamento de um local de satélite, você receberá um email de confirmação. Quando o novo local de geo aparece em azul no mapa na guia **locais Geo** no Centro de administração do OneDrive, você poderá prosseguir para definir o local dos dados preferencial dos usuários ao geo-local. 

> [!IMPORTANT]
> Irá configurar seu novo local geo satélite com as configurações padrão. Isso permitirá que você configure esse local geo conforme apropriado para suas necessidades de conformidade de local.

## <a name="setting-users-preferred-data-location"></a>A definição de local dos dados preferencial dos usuários
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Depois que você ativar os locais de dados necessários, você pode atualizar suas contas de usuário para usar o local apropriado aos dados. Recomendamos que você defina um local de dados preferida para cada usuário, mesmo se esse usuário permanecer no local de dados padrão.

> [!TIP]
> Recomendamos que você comece validações com um usuário de teste ou de um pequeno grupo de usuários antes de implantá Multi-Geo recursos em sua organização ampla.

AAD existem dois tipos de objetos de usuário: nuvem apenas usuários e sincronizados. Siga as instruções apropriadas para seu tipo de usuário.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Sincronizar o local do usuário preferencial dados usando o AD Connect 

Se os usuários da sua empresa são sincronizados a partir de um sistema do AD (Active Directory) no local para Windows Azure Active Directory (AAD), seu PreferredDataLocation deve ser preenchido no AD e sincronizada com AAD. Siga o processo em [sincronização do Azure Connect da AD: faça uma alteração na configuração padrão](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) configurar preferencial da sincronização local dos dados AD local para AAD.

Recomendamos que você inclua a definição de local dos dados preferencial do usuário como parte do seu fluxo de trabalho de criação de usuário padrão.

> [!IMPORTANT]
> Para novos usuários com nenhum OneDrive provisionado, aguarde pelo menos 24 horas depois que PDL um usuário é sincronizado com o AAD para que as alterações sejam propagadas antes que o usuário fizer logon ao OneDrive for Business. (Os dados preferenciais a definição local antes que o usuário fizer logon para provisionar sua OneDrive for Business garante que OneDrive de novo do usuário será provisionado no local correto).

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Configurando o local dos dados preferencial para nuvem somente os usuários 

Se os usuários da sua empresa não serão sincronizados com um sistema de AD (Active Directory) no local para Windows Azure Active Directory (AAD), que significa que eles são criados no Office 365 ou AAD, em seguida, PDL deve ser definida usando o PowerShell AAD.

Os procedimentos nesta seção exigem o [Microsoft Azure módulo Active Directory módulo para Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Se você já tiver PowerShell AAD instalado, verifique se que você atualizar para a versão mais recente.

1.  Abra o módulo do Microsoft Azure Active Directory para o Windows PowerShell.

2.  Execute `Connect-MsolService` e insira as credenciais de administrador global para seu locatário.

3.  Use o cmdlet [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) para definir o local de dados preferida para cada um dos seus usuários. Por exemplo:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Você pode verificar para confirmar que o local preferido de dados foi atualizado corretamente usando o cmdlet Get-MsolUser. Por exemplo:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

Recomendamos que você inclua a definição de local dos dados preferencial do usuário como parte do seu fluxo de trabalho de criação de usuário padrão.

> [!IMPORTANT]
> Para novos usuários com nenhum OneDrive provisionado, aguarde pelo menos 24 horas depois que PDL um usuário é definido para que as alterações sejam propagadas antes que o usuário fizer logon SharePoint OneDrive. (Os dados preferenciais a definição local antes que o usuário fizer logon para provisionar sua OneDrive for Business garante que OneDrive de novo do usuário será provisionado no local correto).

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Provisionamento de OneDrive e o efeito da PDL

Se o usuário já tem um site de OneDrive criado no locatário, definir sua PDL não moverá automaticamente sua OneDrive existente. Para mover OneDrive um usuário, consulte o [OneDrive for Business mover de Geo](move-onedrive-between-geo-locations.md) , siga as instruções no OneDrive movendo entre geo locais.

Se o usuário não tem um site de OneDrive dentro de locatário, OneDrive será provisionado para-los de acordo com o seu valor PDL, supondo que corresponde a um dos locais de dados permitidos da empresa (ADLs) PDL para o usuário.

## <a name="configuring-multi-geo-search"></a>Configurando a pesquisa de Multi-Geo

Seu locatário Multi-Geo terão os recursos de pesquisa agregadas permitindo que uma consulta de pesquisa, para retornar resultados de qualquer lugar dentro do inquilino.

Por padrão, as pesquisas desses pontos de entrada retornará resultados agregados, embora cada índice de pesquisa está localizada dentro de sua localização geo relevantes:

- OneDrive para business

- Delve

- Página inicial do SharePoint

- Centro de Pesquisa

Além disso, os recursos de pesquisa de Multi-Geo podem ser configurados para seus aplicativos de pesquisa personalizadas que usam a API de pesquisa do SharePoint.

Analise a [Configurar a pesquisa do OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) para obter instruções, incluindo quaisquer limitações e diferenças.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Validando o OneDrive for Business Multi-Geo configuração

Abaixo estão alguns casos de uso básico, que talvez você queira incluir em seu plano de validação antes amplamente aplicação do OneDrive for Business Multi-Geo à sua empresa. Depois que você concluir estes testes e qualquer casso adicionais que são relevantes para a sua empresa, você pode escolher passar para a adição de usuários no seu grupo piloto inicial.

**OneDrive for Business**

Selecione OneDrive o iniciador de aplicativo do Office 365 e confirme que você será direcionado automaticamente para o local geo apropriado para o usuário, com base em PDL do usuário. OneDrive for Business agora deve começar com o provisionamento nesse local. Uma vez provisionado, tente upload e download de alguns documentos.

**App móvel do OneDrive**

Faça logon em seu aplicativo móvel do OneDrive com suas credenciais de conta de teste. Confirme que você pode ver seu OneDrive para arquivos de negócios e pode interagir com eles a partir do seu dispositivo móvel.

**Cliente de sincronização do OneDrive**

Confirme que o cliente de sincronização do OneDrive detecta automaticamente seu OneDrive for Business geo-local durante o logon no. Se você precisar baixar o cliente de sincronização, você pode clicar **Sync** na biblioteca do OneDrive.

**Aplicativos do Office**

Confirme que você pode acessar o OneDrive for Business fazendo logon um aplicativo do Office, como o Word. Abra o Office de aplicativos e selecione "OneDrive – <TenantName>". Office detectará seu local de OneDrive e mostram os arquivos que pode ser aberto.

**Sharing**

Tente compartilhar arquivos OneDrive. Confirme que o people picker mostra todos os seus usuários online de SharePoint onde quer que estejam geo.
