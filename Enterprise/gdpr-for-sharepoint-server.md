---
title: RGPD para SharePoint Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Saiba mais sobre como atender aos requisitos de RGPD no SharePoint Server local.
ms.openlocfilehash: 81ee339748923af835f88f73f5cf891d01212a17
ms.sourcegitcommit: 53a57b0617b5bb22beea766e515873d14b3a4783
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "19186610"
---
# <a name="gdpr-for-sharepoint-server"></a><span data-ttu-id="d9d9a-103">RGPD para SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="d9d9a-103">GDPR for SharePoint Server</span></span>

<span data-ttu-id="d9d9a-104">Como parte da proteção de informações pessoais, recomendamos o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-104">As part of safeguarding personal information, we recommend the following:</span></span>

-   <span data-ttu-id="d9d9a-105">Classifique seus dados usando a Proteção de Informações do Azure.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-105">Classify your data, using Azure Information Protection.</span></span>

-   <span data-ttu-id="d9d9a-p101">Execute o SharePoint Server em uma configuração de privilégios mínimos. Consulte [Planejamento para administração de privilégios mínimos no SharePoint Server](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration) e [Segurança para o SharePoint Server](https://docs.microsoft.com/pt-BR/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p101">Run SharePoint Server in a least-privileged configuration. See [Plan for least-privileged administration in SharePoint Server](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration) and [Security for SharePoint Server](https://docs.microsoft.com/pt-BR/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server) for more information.</span></span>

-   <span data-ttu-id="d9d9a-108">[Habilite a criptografia BitLocker em seus servidores](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).</span><span class="sxs-lookup"><span data-stu-id="d9d9a-108">[Enable BitLocker encryption on your servers](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).</span></span>

## <a name="user-generated-content"></a><span data-ttu-id="d9d9a-109">Conteúdo gerado pelo usuário</span><span class="sxs-lookup"><span data-stu-id="d9d9a-109">User Generated content</span></span>

<span data-ttu-id="d9d9a-110">A abordagem básica recomendada para o conteúdo gerado pelo usuário em sites e bibliotecas do SharePoint Server é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-110">The basic recommended approach for user generated content contained in SharePoint Server sites and libraries is:</span></span>

-   <span data-ttu-id="d9d9a-111">Use a Proteção de Informações do Azure para identificar os dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-111">Use Azure Information Protection to label sensitive data.</span></span>

-   <span data-ttu-id="d9d9a-112">Use a [Pesquisa do SharePoint Server](https://docs.microsoft.com/SharePoint/search/search) e a [Descoberta eletrônica](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server) para recuperar dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-112">Use [SharePoint Server search](https://docs.microsoft.com/SharePoint/search/search) and [eDiscovery](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server) to retrieve sensitive data.</span></span>

<span data-ttu-id="d9d9a-113">A abordagem recomendada para compartilhamentos de arquivos e sites do SharePoint inclui estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-113">The recommended approach for files shares and SharePoint sites and libraries includes these steps:</span></span>

1.  <span data-ttu-id="d9d9a-114">**Instale e configure o verificador da Proteção de Informações do Azure.**</span><span class="sxs-lookup"><span data-stu-id="d9d9a-114">**Install and configure Azure Information Protection scanner.**</span></span>

    -   <span data-ttu-id="d9d9a-115">Decida quais tipos de dados confidenciais usar.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-115">Decide which sensitive data types to use.</span></span>

    -   <span data-ttu-id="d9d9a-116">Especifique quais sites do SharePoint usar.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-116">Specify which SharePoint sites to use.</span></span>

2.  <span data-ttu-id="d9d9a-117">**Execute um ciclo de descoberta**.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-117">**Complete a discovery cycle.**</span></span>

    -   <span data-ttu-id="d9d9a-118">Execute o verificador no modo de descoberta e valide os resultados.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-118">Run the scanner in discovery mode and validate the findings.</span></span>

    -   <span data-ttu-id="d9d9a-119">Se necessário, otimize as condições e os tipos de informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-119">If needed, optimize the conditions and sensitive information types.</span></span>

    -   <span data-ttu-id="d9d9a-120">Avalie o impacto esperado de aplicar rótulos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-120">Assess the expected impact of automatically applying labels.</span></span>

3.  <span data-ttu-id="d9d9a-121">**Execute o verificador da Proteção de Informações do Azure para aplicar rótulos a documentos qualificados**.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-121">**Run the Azure Information Protection scanner to apply labels to qualifying documents**.</span></span>

4.  <span data-ttu-id="d9d9a-122">**Para a proteção:**</span><span class="sxs-lookup"><span data-stu-id="d9d9a-122">**For protection:**</span></span>

    <span data-ttu-id="d9d9a-p102">a. Configure regras de prevenção contra a perda de dados do Exchange para proteger documentos com o rótulo desejado.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p102">a.  Configure Exchange data loss prevention rules to protect documents with the desired label.</span></span>

    <span data-ttu-id="d9d9a-p103">b. Certifique-se de usar permissões para limitar quem pode acessar os arquivos.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p103">b.  Be sure permissions to limit who can access files.</span></span>

    <span data-ttu-id="d9d9a-p104">c. Para o SharePoint, use a proteção de IRM para bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p104">c.  For SharePoint, use IRM-protection for libraries.</span></span>

5.  <span data-ttu-id="d9d9a-129">**Para monitorar, integre os logs do Windows Server com uma ferramenta SIEM.**</span><span class="sxs-lookup"><span data-stu-id="d9d9a-129">**For monitoring, integrate Windows Server logs with a SIEM tool.**</span></span>

    <span data-ttu-id="d9d9a-p105">a. Para localizar dados pessoais para solicitações de titulares de dados, use o Centro de Pesquisa ou a Descoberta eletrônica.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p105">a.  To find personal data for data subject requests, use Search Center or eDiscovery.</span></span>

<span data-ttu-id="d9d9a-p106">Ao aplicar rótulos em dados confidenciais, certifique-se de usar um rótulo que não esteja configurado com proteção. Isso inclui criptografia que impeça que os serviços detectem dados confidenciais nos arquivos.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p106">When applying labels to sensitive data, be sure to use a label that is not configured with protection. Protection includes encryption which prevents services from detecting sensitive data in the files.</span></span>

<span data-ttu-id="d9d9a-134">Saiba mais sobre como usar o verificador da Proteção de Informações do Azure para localizar e rotular dados pessoais no [Microsoft GDPR Data Discovery Toolkit](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners).</span><span class="sxs-lookup"><span data-stu-id="d9d9a-134">For more information on using Azure Information Protection scanner to find and label personal data, see the [Microsoft GDPR Data Discovery Toolkit](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners).</span></span>

<span data-ttu-id="d9d9a-p107">Consulte informações sobre como configurar o verificador para analisar condições e os tipos de informações confidenciais para prevenção contra perda de dados (DLP) do Office 365 em [Como configurar as condições de classificação automática e recomendada para a Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification). Observe que os novos tipos de informações confidenciais do Office 365 não estarão disponíveis imediatamente para usar com o verificador e tipos de informações confidenciais personalizados não podem ser usados com o verificador.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p107">For information on configuring the scanner for conditions and using the Office 365 data loss prevention (DLP) sensitive information types, see [How to configure conditions for automatic and recommended classification for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification). Note that new Office 365 sensitive information types will not be immediately available to use with the scanner and custom sensitive information types cannot be used with the scanner.</span></span>

## <a name="removing-personal-information-from-office-files"></a><span data-ttu-id="d9d9a-137">Remover informações pessoais de arquivos do Office</span><span class="sxs-lookup"><span data-stu-id="d9d9a-137">Removing personal information from Office files</span></span>

<span data-ttu-id="d9d9a-p108">A remoção de informações pessoais (como metadados ou comentários em um documento do Word) de arquivos do Office que estão armazenados em uma biblioteca de documentos do SharePoint deve ser feita manualmente. Siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p108">Removing personal information (such as metadata or comments in a Word document) from Office files that are stored in a SharePoint document library must be done manually. Follow these steps:</span></span>

1.  <span data-ttu-id="d9d9a-140">Baixe uma cópia do documento do SharePoint Server para seu disco local.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-140">Download a copy of the document from SharePoint Server to your local disk.</span></span>

2.  <span data-ttu-id="d9d9a-141">Exclua o documento da biblioteca de documentos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-141">Delete the document from the SharePoint document library.</span></span>

3.  <span data-ttu-id="d9d9a-142">Siga as etapas em [Remover dados ocultos e informações pessoais ao inspecionar documentos](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F).</span><span class="sxs-lookup"><span data-stu-id="d9d9a-142">Follow the steps in [Remove hidden data and personal information by inspecting documents](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F).</span></span>

4.  <span data-ttu-id="d9d9a-143">Reenvie o documento para a biblioteca de documentos do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-143">Upload the document back to the SharePoint document library.</span></span>

## <a name="telemetry-and-log-files"></a><span data-ttu-id="d9d9a-144">Telemetria e arquivos de log</span><span class="sxs-lookup"><span data-stu-id="d9d9a-144">Telemetry and log files</span></span>

### <a name="uls-logs"></a><span data-ttu-id="d9d9a-145">Logs do ULS</span><span class="sxs-lookup"><span data-stu-id="d9d9a-145">ULS Logs</span></span>

<span data-ttu-id="d9d9a-p109">O Serviço de Log Unificado (ULS) e o Log de uso no SharePoint Server acompanham diversas funções de sistema e podem conter informações do usuário. Logs do ULS e logs de uso são arquivos de texto e podem ser pesquisados usando diversas ferramentas de pesquisa. O [cmdlet Merge-SPLogFile do PowerShell](https://docs.microsoft.com/pt-BR/powershell/module/sharepoint-server/merge-splogfile) fornece uma maneira de retornar os registros dos logs do ULS em vários servidores de um farm.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p109">Unified Logging Service (ULS) and Usage logging in SharePoint Server track a variety of system functions and can contain user information. ULS logs and usage logs are text files and can be searched using a variety of searching tools. The [Merge-SPLogFile PowerShell cmdlet](https://docs.microsoft.com/pt-BR/powershell/module/sharepoint-server/merge-splogfile) provides a way to return records from the ULS logs on multiple servers in a farm.</span></span>

<span data-ttu-id="d9d9a-p110">Considere configurar as políticas de retenção de logs para o valor mínimo necessário para seus objetivos de negócios. Consulte informações sobre como configurar o registro em log no SharePoint Server em [Configurar o registro de diagnóstico no SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p110">Consider setting log retention policies to the minimum value needed for your business purposes. For information about configuring logging in SharePoint Server, see [Configure diagnostic logging in SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span></span>

<span data-ttu-id="d9d9a-151">Observe que alguns eventos de sistema também são registrados no Log de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-151">Note that some system events are also logged to the Windows Event Log.</span></span>

### <a name="usage-database"></a><span data-ttu-id="d9d9a-152">Banco de dados de uso</span><span class="sxs-lookup"><span data-stu-id="d9d9a-152">Usage Database</span></span>

<span data-ttu-id="d9d9a-p111">O banco de dados de uso do SharePoint Server (nome padrão WSS_Logging) contém um subconjunto das informações encontradas nos logs do ULS. A retenção máxima dos dados nesse banco de dados é de 30 dias. Recomendamos que você defina essa configuração para a menor duração permitida por suas necessidades de negócios. Para saber mais, consulte [Configurar o registro de diagnóstico no SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p111">The SharePoint Server Usage database (default name WSS_Logging) contains a subset of the information found in the ULS logs. The maximum retention of data in this database is 30 days. We recommend that you configure it for the shortest duration allowable by your business needs. For more information, see [Configure diagnostic logging in SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span></span>

## <a name="personal-information-and-search"></a><span data-ttu-id="d9d9a-157">Informações pessoais e pesquisa</span><span class="sxs-lookup"><span data-stu-id="d9d9a-157">Personal information and search</span></span>

<span data-ttu-id="d9d9a-158">Os registros de uso e de histórico de consultas de pesquisa contêm referências a nomes de usuários.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-158">The search query history and usage records contain references to user names.</span></span>

### <a name="query-history-and-favorite-queries"></a><span data-ttu-id="d9d9a-159">Histórico de consultas e consultas favoritas</span><span class="sxs-lookup"><span data-stu-id="d9d9a-159">Query history and favorite queries</span></span>

<span data-ttu-id="d9d9a-p112">No SharePoint Server 2013 e no SharePoint Server 2016, históricos de consultas e consultas "favoritas" expiram automaticamente após 365 dias. Se um usuário deixar sua organização, será possível remover referências ao nome dele do histórico de consultas usando as etapas abaixo.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p112">In SharePoint Server 2013 and SharePoint Server 2016, query histories and ‘favorite’ queries automatically expire after 365 days. If a user leaves your organization, it is possible to remove references to a user's name from the query history using the steps below..</span></span>

<span data-ttu-id="d9d9a-162">As consultas SQL a seguir aplicam-se ao SharePoint 2013 e ao SharePoint 2016 e permitem:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-162">The following SQL queries apply to SharePoint 2013 and SharePoint 2016 and make it possible to:</span></span>

-   <span data-ttu-id="d9d9a-163">Exportar o histórico de consultas ou as consultas favoritas de um usuário</span><span class="sxs-lookup"><span data-stu-id="d9d9a-163">Export a user’s query history or favorite queries</span></span>

-   <span data-ttu-id="d9d9a-164">Remover referências a nomes de usuários do histórico de consultas</span><span class="sxs-lookup"><span data-stu-id="d9d9a-164">Remove references to user names in the query history</span></span>

#### <a name="export-a-users-queries-since-a-specific-date"></a><span data-ttu-id="d9d9a-165">Exportar as consultas de um usuário desde uma data específica</span><span class="sxs-lookup"><span data-stu-id="d9d9a-165">Export a user’s queries since a specific date</span></span> 

<span data-ttu-id="d9d9a-166">Use o procedimento a seguir para exportar as consultas das tabelas de logs de consulta Link Store, executada por @UserName desde @StartTime.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-166">Use the following procedure to export queries from the Link Store query log tables, performed by @UserName since @StartTime.</span></span>

```sql
[In dbo].[LinkStore_<ID>]:
CREATE PROCEDURE proc_MSS_GetQueryTermsForUser 
( 
    @UserName nvarchar(256), 
    @StartTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT searchTime, queryString 
    FROM 
        dbo.MSSQLogPageImpressionQuery 
    WITH 
        (NOLOCK) 
    WHERE 
        userName = @UserName AND 
        searchTime > @StartTime 
END 
GO 
```

#### <a name="export-a-users-queries-from-the-past-100-days"></a><span data-ttu-id="d9d9a-167">Exportar as consultas dos últimos 100 dias para um usuário</span><span class="sxs-lookup"><span data-stu-id="d9d9a-167">Export a user’s queries from the past 100 days</span></span>

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetQueryTermsForUser '0#.w|domain\username', @FROMDATE 
```

#### <a name="export-a-users-favorite-queries"></a><span data-ttu-id="d9d9a-168">Exportar as consultas favoritas de um usuário</span><span class="sxs-lookup"><span data-stu-id="d9d9a-168">Export a user’s favorite queries</span></span>

<span data-ttu-id="d9d9a-169">Use o procedimento a seguir para exportar as consultas favoritas de um usuário das tabelas de resultado pessoal do banco de dados Search Admin, executadas por @UserName, desde <DateTime>.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-169">Use the following procedure to export a user's favorite queries from the Search Admin DB personal result tables, performed by @UserName, since <DateTime>.</span></span>

```sql
In [dbo].[Search_<ID>]:
CREATE PROCEDURE proc_MSS_GetPersonalFavoriteQueries 
( 
    @UserName nvarchar(256), 
    @SearchTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT max(queries.SearchTime) as SearchTime, 
           max(queries.querystring) as queryString, 
           max(url.url) as URL 
    FROM MSSQLogOwner owners WITH(NOLOCK) 
    JOIN MSSQLogPersonalResults results WITH(NOLOCK) on owners.OwnerId = results.OwnerId 
    JOIN MSSQLogUrl url WITH(NOLOCK) on results.ClickedUrlId = url.urlId 
    JOIN MSSQLogPersonalQueries queries WITH(NOLOCK) on results.OwnerId = queries.OwnerId 
    WHERE queries.SearchTime > @SearchTime 
        AND queries.UserName = @UserName 
        GROUP BY queries.QueryString,url.url 
END 
GO 
```

#### <a name="export-a-users-favorite-queries-from-the-past-100-days"></a><span data-ttu-id="d9d9a-170">Exportar as consultas favoritas dos últimos 100 dias para um usuário</span><span class="sxs-lookup"><span data-stu-id="d9d9a-170">Export a user’s favorite queries from the past 100 days</span></span> 

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetPersonalFavoriteQueries '0#.w|domain\username', @FROMDATE 
```

#### <a name="remove-references-to-user-names-that-are-more-than-x-days-old"></a><span data-ttu-id="d9d9a-171">Remover referências a nomes de usuários com mais de X dias</span><span class="sxs-lookup"><span data-stu-id="d9d9a-171">Remove references to user names that are more than X days old</span></span>

<span data-ttu-id="d9d9a-p113">Use o procedimento a seguir para remover as referências a *todos* os nomes de usuários que têm mais do que @Days das tabelas de log de consultas Links Store. O procedimento removerá apenas as referências anteriores ao momento atual até atingir o @LastCleanupTime.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p113">Use the following procedure to remove references to *all* user names that are more than @Days old, from the Links Store query log tables. The procedure only removes references backwards in time until it reaches the @LastCleanupTime.</span></span>

```sql
In [dbo].[LinksStore_<ID>]:  
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-a-specific-user-name-thats-more-than-x-days-old"></a><span data-ttu-id="d9d9a-174">Remover referências a um nome de usuário específico com mais de X dias</span><span class="sxs-lookup"><span data-stu-id="d9d9a-174">Remove references to a specific user name that’s more than X days old</span></span>

<span data-ttu-id="d9d9a-p114">Use o procedimento a seguir para remover as referências a um nome de usuário *específico* das tabelas de log de consultas Links Store, onde as referências têm mais de @Days. O procedimento removerá apenas as referências anteriores ao momento atual até atingir o @LastCleanupTime.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p114">Use the following procedure to remove references to a *specific* user name from the Links Store query log tables, where the references are more than @Days old. The procedure only removes references backwards in time until it reaches the @LastCleanupTime.</span></span>

```sql
In [dbo].[LinksStore_<ID>]:
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @UserName nvarchar(256),
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-all-user-names-in-the-query-history-from-a-date-and-up-to-the-past-30-days"></a><span data-ttu-id="d9d9a-177">Remover referências a todos os nomes de usuário no histórico de consultas a partir de determinada data até os últimos 30 dias</span><span class="sxs-lookup"><span data-stu-id="d9d9a-177">Remove references to all user names in the query history from a date and up to the past 30 days</span></span>

```sql
EXECUTE proc_MSS_QLog_Cleanup_Users '1-1-2017', 30 
```

### <a name="delete-usage-records"></a><span data-ttu-id="d9d9a-178">Excluir registros de uso</span><span class="sxs-lookup"><span data-stu-id="d9d9a-178">Delete usage records</span></span>

<span data-ttu-id="d9d9a-p115">O SharePoint Server 2013 e o SharePoint Server 2016 excluem automaticamente os registros de uso após 3 anos. Você pode excluir esses registros manualmente usando o procedimento a seguir:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p115">SharePoint Server 2013 and SharePoint Server 2016 automatically deletes usage records after 3 years. You can manually delete such records using the procedure below:</span></span>

<span data-ttu-id="d9d9a-181">Para excluir todos os registros de uso associados a documentos excluídos:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-181">To delete all usage records associated with deleted documents:</span></span> 

1.  <span data-ttu-id="d9d9a-182">Verifique se você tem a atualização mais recente do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-182">Ensure that you have the latest SharePoint update installed.</span></span> 

2.  <span data-ttu-id="d9d9a-183">Inicie um shell de Gerenciamento do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-183">Start a SharePoint Management Shell.</span></span>

3.  <span data-ttu-id="d9d9a-184">Interrompa e desmarque a Análise de Uso:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-184">Stop and Clear the Usage Analytics analysis:</span></span> 

    ```powershell
    $tj = Get-SPTimerJob -Type Microsoft.Office.Server.Search.Analytics.UsageAnalyticsJobDefinition 
    $tj.StopAnalysis() 
    $tj.ClearAnalysis() 
    ```

4.  <span data-ttu-id="d9d9a-185">Espere até que a análise seja iniciada novamente (pode levar até 24 horas).</span><span class="sxs-lookup"><span data-stu-id="d9d9a-185">Wait for the analysis to start again (might take up to 24 hours).</span></span> 

5.  <span data-ttu-id="d9d9a-p116">Na próxima execução da análise, ela despejará todos os registros do banco de dados de Relatórios de Análise. Esse despejo completo pode levar algum tempo se o banco de dados tiver várias entradas.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p116">On the next run of the analysis, it will dump all records from the Analytics Reporting database. This full dump may take a while for a large database with many entries.</span></span>

6.  <span data-ttu-id="d9d9a-p117">Aguarde 10 dias. A análise é executada diariamente e os registros associados a documentos excluídos serão removidos após a décima execução. Essa execução pode levar mais tempo do que o normal se muitos registros precisarem ser excluídos.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p117">Wait for 10 days. The analysis runs daily, and records associated with deleted documents will be removed after the 10^th^ run. This run may take longer than normal if many records need to be deleted.</span></span> 

### <a name="personal-information-and-search-in-sharepoint-server-2010"></a><span data-ttu-id="d9d9a-191">Informações pessoais e pesquisa no SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="d9d9a-191">Personal information and search in SharePoint Server 2010</span></span>

#### <a name="fast-search-server-2010-for-sharepoint"></a><span data-ttu-id="d9d9a-192">Microsoft FAST Search Server 2010 para SharePoint</span><span class="sxs-lookup"><span data-stu-id="d9d9a-192">FAST Search Server 2010 for SharePoint</span></span> 

<span data-ttu-id="d9d9a-p118">Além de armazenar arquivos no índice, o complemento FAST Search Server 2010 também armazena arquivos em um formato intermediário chamado FixML. Arquivos FiXML são compactados regularmente, por padrão, entre 3h e 5h toda noite. A compactação remove os arquivos excluídos dos arquivos FiXML automaticamente. Para garantir a remoção em tempo hábil das informações pertencentes a usuários ou documentos excluídos, certifique-se de que a compactação esteja sempre habilitada.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p118">In addition to storing files in the index, the FAST Search Server 2010 Add-On also stores files in an intermediate format called FixML. FiXML files are compacted regularly, by default between 3 am and 5 am every night. Compaction removes deleted files from the FiXML files automatically. To ensure timely removal of information belonging to deleted users or documents, ensure that compaction is always enabled.</span></span>

### <a name="hybrid-search"></a><span data-ttu-id="d9d9a-197">Pesquisa híbrida</span><span class="sxs-lookup"><span data-stu-id="d9d9a-197">Hybrid search</span></span> 

<span data-ttu-id="d9d9a-p119">As ações recomendadas para as soluções de pesquisa híbrida são as mesmas que para a pesquisa no SharePoint Server ou no SharePoint Online. Existem duas soluções de pesquisa híbrida:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p119">The recommended actions for hybrid search solutions are the same as for search in SharePoint Server or SharePoint Online. There are two hybrid search solutions:</span></span>

<span data-ttu-id="d9d9a-p120">**A solução de pesquisa híbrida em nuvem**: com a solução de pesquisa híbrida em nuvem para SharePoint, você indexa todo o seu conteúdo rastreado, incluindo o conteúdo do local, no índice de pesquisa do Office 365. Quando os usuários consultam o índice de pesquisa no Office 365, eles obtêm resultados de pesquisa do conteúdo local e do Office 365. Quando documentos são excluídos do ambiente do SharePoint Server, eles também são excluídos do índice de pesquisa do Office 365. [Leia mais sobre a solução de pesquisa híbrida em nuvem](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint) e [como componentes e bancos de dados de pesquisa interagem na pesquisa híbrida em nuvem](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint) para entender melhor como o RGPD afeta o ambiente híbrido.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p120">**The cloud hybrid search solution -** With the cloud hybrid search solution for SharePoint, you index all your crawled content, including on-premises content, in your search index in Office 365. When users query your search index in Office 365, they get search results from both on-premises and Office 365 content. When documents are deleted from the SharePoint Server environment, they are also deleted from the search index in Office 365. [Read more about the cloud hybrid search solution](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint) and [how search components and databases interact in cloud hybrid search](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint) to understand better how GDPR affects the hybrid environment.</span></span>

<span data-ttu-id="d9d9a-p121">**A solução de pesquisa federada híbrida**: com a solução de pesquisa federada híbrida, você usa o índice no SharePoint Server e no Office 365. Ambos os serviços de pesquisa do SharePoint Server e do SharePoint Online podem consultar o índice de pesquisa em outro lugar e retornar resultados federados. Quando os usuários pesquisam no Centro de Pesquisa, os resultados são exibidos tanto no índice de pesquisa no SharePoint Server quanto no índice de pesquisa no Office 365. [Leia mais sobre a solução de pesquisa híbrida federada ](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint) para entender melhor como o RGPD afeta o ambiente híbrido.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p121">**The hybrid federated search solution -** With the hybrid federated search solution, you use both your index in SharePoint Server and your index in Office 365. Both SharePoint Server and SharePoint Online Search services can query the search index in the other environment and return federated results. When users search from a Search Center, the search results come from both your search index in SharePoint Server and your search index in Office 365. [Read more about the hybrid federated search solution](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint) to understand better how GDPR affects the hybrid environment.</span></span>

## <a name="on-prem-to-cloud-migrations"></a><span data-ttu-id="d9d9a-208">Migrações do local para a nuvem</span><span class="sxs-lookup"><span data-stu-id="d9d9a-208">On Prem to Cloud Migrations</span></span>

<span data-ttu-id="d9d9a-p122">Durante a migração de dados do SharePoint Server para o SharePoint Online, pode haver dados duplicados em ambos os locais por um período. Se você tiver dados que precisa excluir durante a migração, recomendamos concluir a migração primeiro e excluir os dados de ambos os locais. Você pode consultar os dados para exportação de qualquer local.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p122">While migrating data from SharePoint Server to SharePoint Online, duplicate data may exist in both locations for a time. If you have data that you need to delete that is in mid-migration, we recommend that you complete the migration first, and then delete the data from both locations. You can query data for export from either location.</span></span>

## <a name="user-profile-data"></a><span data-ttu-id="d9d9a-212">Dados de perfil do usuário</span><span class="sxs-lookup"><span data-stu-id="d9d9a-212">User profile data</span></span>

<span data-ttu-id="d9d9a-p123">O serviço Perfil de Usuário permite a importação de dados de perfil de uma variedade de fontes externas. Consultas e atualizações desses dados de perfil devem ser realizadas nos sistemas nos quais os dados são dominados. Caso você faça atualizações no sistema externo, sincronize novamente os perfis de usuário no SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p123">The User Profile Service allows for import of profile data from a variety of external sources. Queries for and update of such user profile data should be handled in the systems in which the data is mastered. If you make updates to the external system, be sure to synchronize the user profiles in SharePoint Server again.</span></span>

<span data-ttu-id="d9d9a-216">Siga estas etapas básicas para remover as informações pessoais de um usuário de seu perfil do SharePoint Server:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-216">Follow these basic steps to remove a user’s personal information from their SharePoint Server user profile:</span></span>

1.  <span data-ttu-id="d9d9a-p124">Remova as informações do usuário de qualquer sistema externo que alimente o perfil de usuário do SharePoint Server. Se você estiver usando a sincronização de diretórios, o usuário deverá ser removido do ambiente do Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p124">Remove the user information from any external systems that feed into the SharePoint Server user profile. If you are using directory synchronization, the user must be removed from the on-premises Active Directory environment.</span></span>

2.  <span data-ttu-id="d9d9a-219">Execute uma [sincronização de perfil](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually) no SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-219">Run a [profile synchronization](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually) on SharePoint Server.</span></span>

3.  <span data-ttu-id="d9d9a-p125">Exclua o perfil do SharePoint Server. Quando terminar, o SharePoint Server removerá totalmente o perfil do banco de dados de perfis de usuários em 30 dias. A página de perfil e o site pessoal de usuário serão excluídos.</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p125">Delete the profile from SharePoint Server. Once this is done, SharePoint Server will fully remove the profile from the User Profile Database in 30 days. The user’s profile page and personal site will be deleted.</span></span>

<span data-ttu-id="d9d9a-p126">Depois de excluir o perfil de um usuário, algumas informações limitadas (como a ID do usuário) ainda poderão estar registradas em conjuntos de sites que o usuário acessou. Se quiser excluir dados de um conjunto de sites, isso pode ser feito usando o CSOM. Um exemplo de script é fornecido abaixo:</span><span class="sxs-lookup"><span data-stu-id="d9d9a-p126">After deleting a user’s profile, some limited information (such as user ID) may still be recorded in site collections that the user has visited. If you choose to delete this data from a given site collection, this can be done using CSOM. A sample script is provided below:</span></span>

```powershell
$username = "<admin@company.sharepoint.com>"
$password = "password"
$url = "<https://site.sharepoint.com>"
$securePassword = ConvertTo-SecureString $Password -AsPlainText -Force

# the path here may need to change if you used e.g. C:Lib.
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.dll"
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.Runtime.dll"

# connect/authenticate to SharePoint Online and get ClientContext object.
$clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($url)
$credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($username, $securePassword)
$clientContext.Credentials = $credentials
if (!$clientContext.ServerObjectIsNull.Value)
{
    Write-Host "Connected to SharePoint Online site: '$Url'" -ForegroundColor Green
}

# Get user
$user = $clientContext.Web.SiteUsers.GetByLoginName("i:0#.f|membership|user@company.sharepoint.com")

# Redact user
$user.Email = "Redacted"
$user.Title = "Redacted"
$user.Update()
$clientContext.Load($user)
$clientContext.ExecuteQuery()

# Get users
$users = $clientContext.Web.SiteUsers

# Remove user from site
$users.RemoveById($user.Id)
$clientContext.Load($users)
$clientContext.ExecuteQuery()
```