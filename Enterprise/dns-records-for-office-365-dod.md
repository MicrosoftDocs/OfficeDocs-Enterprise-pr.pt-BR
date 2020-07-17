---
title: Registros DNS para Office 365 DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Resumo: registros DNS do Office 365 DoD'
hideEdit: true
ms.openlocfilehash: d1f8c82224934f11eddbfa10c5dea7d15cc9e9a2
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339775"
---
# <a name="dns-records-for-office-365-dod"></a><span data-ttu-id="d7c49-103">Registros DNS para Office 365 DoD</span><span class="sxs-lookup"><span data-stu-id="d7c49-103">DNS records for Office 365 DoD</span></span>

<span data-ttu-id="d7c49-104">*Este artigo se aplica ao Office 365 DoD e à Microsoft 365 DoD*</span><span class="sxs-lookup"><span data-stu-id="d7c49-104">*This article applies to Office 365 DoD and Microsoft 365 DoD*</span></span>

<span data-ttu-id="d7c49-105">Como parte da integração com o Office 365 DoD, você precisará adicionar seus domínios SMTP e SIP ao seu locatário de serviços online.</span><span class="sxs-lookup"><span data-stu-id="d7c49-105">As part of onboarding to Office 365 DoD, you will need to add your SMTP and SIP domains to your Online Services tenant.</span></span>  <span data-ttu-id="d7c49-106">Você fará isso usando o cmdlet New-MsolDomain no PowerShell do Azure AD ou usar o [portal do Azure governamental](https://portal.azure.us) para iniciar o processo de adicionar o domínio e provar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="d7c49-106">You’ll do this using the New-MsolDomain cmdlet in Azure AD PowerShell or use the [Azure Government Portal](https://portal.azure.us) to start the process of adding the domain and proving ownership.</span></span>

<span data-ttu-id="d7c49-107">Depois que você tiver seus domínios adicionados ao seu locatário e validado, use as orientações a seguir para adicionar os registros DNS apropriados para os serviços abaixo.</span><span class="sxs-lookup"><span data-stu-id="d7c49-107">Once you have your domains added to your tenant and validated, use the following guidance to add the appropriate DNS records for the services below.</span></span>  <span data-ttu-id="d7c49-108">Talvez seja necessário modificar a tabela abaixo para se adequar às necessidades da sua organização em relação ao (s) registro (s) MX de entrada e a qualquer registro de descoberta automática do Exchange existente.</span><span class="sxs-lookup"><span data-stu-id="d7c49-108">You may need to modify the below table to fit your organization’s needs with respect to the inbound MX record(s) and any existing Exchange Autodiscover record(s) you have in place.</span></span>  <span data-ttu-id="d7c49-109">É altamente recomendável coordenar esses registros DNS com sua equipe de mensagens para evitar qualquer interrupção ou entrega incorreta de emails.</span><span class="sxs-lookup"><span data-stu-id="d7c49-109">We strongly recommend coordinating these DNS records with your messaging team to avoid any outages or mis-delivery of email.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="d7c49-110">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d7c49-110">Exchange Online</span></span>

| <span data-ttu-id="d7c49-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="d7c49-111">Type</span></span> | <span data-ttu-id="d7c49-112">Prioridade</span><span class="sxs-lookup"><span data-stu-id="d7c49-112">Priority</span></span> | <span data-ttu-id="d7c49-113">Nome do host</span><span class="sxs-lookup"><span data-stu-id="d7c49-113">Host name</span></span> | <span data-ttu-id="d7c49-114">Aponta para o endereço ou o valor</span><span class="sxs-lookup"><span data-stu-id="d7c49-114">Points to address or value</span></span> | <span data-ttu-id="d7c49-115">TTL</span><span class="sxs-lookup"><span data-stu-id="d7c49-115">TTL</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="d7c49-116">MX</span><span class="sxs-lookup"><span data-stu-id="d7c49-116">MX</span></span> | <span data-ttu-id="d7c49-117">,0</span><span class="sxs-lookup"><span data-stu-id="d7c49-117">0</span></span> | @ | <span data-ttu-id="d7c49-118">*Tenant*. mail.Protection.office365.us (veja a seguir os detalhes adicionais)</span><span class="sxs-lookup"><span data-stu-id="d7c49-118">*tenant*.mail.protection.office365.us (see below for additional details)</span></span> | <span data-ttu-id="d7c49-119">1 Hour</span><span class="sxs-lookup"><span data-stu-id="d7c49-119">1 Hour</span></span> |
| <span data-ttu-id="d7c49-120">TXT</span><span class="sxs-lookup"><span data-stu-id="d7c49-120">TXT</span></span> | - | @ | <span data-ttu-id="d7c49-121">v = spf1 inclui include. Protection. office365. us-all</span><span class="sxs-lookup"><span data-stu-id="d7c49-121">v=spf1 include:spf.protection.office365.us -all</span></span> | <span data-ttu-id="d7c49-122">1 Hour</span><span class="sxs-lookup"><span data-stu-id="d7c49-122">1 Hour</span></span> |
| <span data-ttu-id="d7c49-123">CNAME</span><span class="sxs-lookup"><span data-stu-id="d7c49-123">CNAME</span></span> | - | <span data-ttu-id="d7c49-124">autodiscover</span><span class="sxs-lookup"><span data-stu-id="d7c49-124">autodiscover</span></span> | <span data-ttu-id="d7c49-125">autodiscover-dod.office365.us</span><span class="sxs-lookup"><span data-stu-id="d7c49-125">autodiscover-dod.office365.us</span></span> | <span data-ttu-id="d7c49-126">1 Hour</span><span class="sxs-lookup"><span data-stu-id="d7c49-126">1 Hour</span></span> |

### <a name="exchange-autodiscover-record"></a><span data-ttu-id="d7c49-127">Registro de descoberta automática do Exchange</span><span class="sxs-lookup"><span data-stu-id="d7c49-127">Exchange Autodiscover record</span></span>

<span data-ttu-id="d7c49-128">Se você tiver o Exchange Server local, recomendamos que você saia do registro existente enquanto migra para o Exchange Online e atualize esse registro depois de concluir a migração.</span><span class="sxs-lookup"><span data-stu-id="d7c49-128">If you have Exchange Server on-premises, we recommend leaving your existing record in place while you migrate to Exchange Online, and update that record once you have completed your migration.</span></span>

### <a name="exchange-online-mx-record"></a><span data-ttu-id="d7c49-129">Registro MX do Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d7c49-129">Exchange Online MX Record</span></span>

<span data-ttu-id="d7c49-130">O valor do registro MX para seus domínios aceitos segue um formato padrão, conforme observado acima: *Tenant*. mail.Protection.office365.us, substituindo o *locatário* pela primeira parte do nome do locatário padrão.</span><span class="sxs-lookup"><span data-stu-id="d7c49-130">The MX record value for your accepted domains follows a standard format as noted above: *tenant*.mail.protection.office365.us, replacing *tenant* with the first part of your default tenant name.</span></span>

<span data-ttu-id="d7c49-131">Por exemplo, se o nome do seu locatário for contoso.onmicrosoft.us, você usaria **contoso.mail.Protection.office365.us** como o valor para o seu registro MX.</span><span class="sxs-lookup"><span data-stu-id="d7c49-131">For example, if your tenant name is contoso.onmicrosoft.us, you’d use **contoso.mail.protection.office365.us** as the value for your MX record.</span></span>

## <a name="skype-for-business-online"></a><span data-ttu-id="d7c49-132">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="d7c49-132">Skype for Business Online</span></span>

### <a name="cname-records"></a><span data-ttu-id="d7c49-133">Registros CNAME</span><span class="sxs-lookup"><span data-stu-id="d7c49-133">CNAME records</span></span>

| <span data-ttu-id="d7c49-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="d7c49-134">Type</span></span> | <span data-ttu-id="d7c49-135">Nome do host</span><span class="sxs-lookup"><span data-stu-id="d7c49-135">Host name</span></span> | <span data-ttu-id="d7c49-136">Aponta para o endereço ou o valor</span><span class="sxs-lookup"><span data-stu-id="d7c49-136">Points to address or value</span></span> | <span data-ttu-id="d7c49-137">TTL</span><span class="sxs-lookup"><span data-stu-id="d7c49-137">TTL</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="d7c49-138">CNAME</span><span class="sxs-lookup"><span data-stu-id="d7c49-138">CNAME</span></span> | <span data-ttu-id="d7c49-139">sip</span><span class="sxs-lookup"><span data-stu-id="d7c49-139">sip</span></span> | <span data-ttu-id="d7c49-140">sipdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="d7c49-140">sipdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="d7c49-141">1 Hour</span><span class="sxs-lookup"><span data-stu-id="d7c49-141">1 Hour</span></span> |
| <span data-ttu-id="d7c49-142">CNAME</span><span class="sxs-lookup"><span data-stu-id="d7c49-142">CNAME</span></span> | <span data-ttu-id="d7c49-143">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="d7c49-143">lyncdiscover</span></span> | <span data-ttu-id="d7c49-144">webdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="d7c49-144">webdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="d7c49-145">1 Hour</span><span class="sxs-lookup"><span data-stu-id="d7c49-145">1 Hour</span></span> | 

### <a name="srv-records"></a><span data-ttu-id="d7c49-146">Registros SRV</span><span class="sxs-lookup"><span data-stu-id="d7c49-146">SRV records</span></span>

| <span data-ttu-id="d7c49-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="d7c49-147">Type</span></span> | <span data-ttu-id="d7c49-148">Serviço</span><span class="sxs-lookup"><span data-stu-id="d7c49-148">Service</span></span> | <span data-ttu-id="d7c49-149">Protocolo</span><span class="sxs-lookup"><span data-stu-id="d7c49-149">Protocol</span></span> | <span data-ttu-id="d7c49-150">Porta</span><span class="sxs-lookup"><span data-stu-id="d7c49-150">Port</span></span> | <span data-ttu-id="d7c49-151">Peso</span><span class="sxs-lookup"><span data-stu-id="d7c49-151">Weight</span></span> | <span data-ttu-id="d7c49-152">Priority</span><span class="sxs-lookup"><span data-stu-id="d7c49-152">Priority</span></span> | <span data-ttu-id="d7c49-153">Nome</span><span class="sxs-lookup"><span data-stu-id="d7c49-153">Name</span></span> | <span data-ttu-id="d7c49-154">Target</span><span class="sxs-lookup"><span data-stu-id="d7c49-154">Target</span></span> | <span data-ttu-id="d7c49-155">TTL</span><span class="sxs-lookup"><span data-stu-id="d7c49-155">TTL</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="d7c49-156">SRV</span><span class="sxs-lookup"><span data-stu-id="d7c49-156">SRV</span></span> | <span data-ttu-id="d7c49-157">\_sip</span><span class="sxs-lookup"><span data-stu-id="d7c49-157">\_sip</span></span> | <span data-ttu-id="d7c49-158">\_TLS</span><span class="sxs-lookup"><span data-stu-id="d7c49-158">\_tls</span></span> | <span data-ttu-id="d7c49-159">443</span><span class="sxs-lookup"><span data-stu-id="d7c49-159">443</span></span> | <span data-ttu-id="d7c49-160">1 </span><span class="sxs-lookup"><span data-stu-id="d7c49-160">1</span></span> | <span data-ttu-id="d7c49-161">100</span><span class="sxs-lookup"><span data-stu-id="d7c49-161">100</span></span> | @ | <span data-ttu-id="d7c49-162">sipdir.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="d7c49-162">sipdir.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="d7c49-163">1 hora</span><span class="sxs-lookup"><span data-stu-id="d7c49-163">1 Hour</span></span> |
| <span data-ttu-id="d7c49-164">SRV</span><span class="sxs-lookup"><span data-stu-id="d7c49-164">SRV</span></span> | <span data-ttu-id="d7c49-165">\_sipfederationtls</span><span class="sxs-lookup"><span data-stu-id="d7c49-165">\_sipfederationtls</span></span> | <span data-ttu-id="d7c49-166">\_TCP</span><span class="sxs-lookup"><span data-stu-id="d7c49-166">\_tcp</span></span> | <span data-ttu-id="d7c49-167">5061</span><span class="sxs-lookup"><span data-stu-id="d7c49-167">5061</span></span> | <span data-ttu-id="d7c49-168">1 </span><span class="sxs-lookup"><span data-stu-id="d7c49-168">1</span></span> | <span data-ttu-id="d7c49-169">100</span><span class="sxs-lookup"><span data-stu-id="d7c49-169">100</span></span> | @ | <span data-ttu-id="d7c49-170">sipfed.online.dod.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="d7c49-170">sipfed.online.dod.skypeforbusiness.us</span></span> | <span data-ttu-id="d7c49-171">1 Hour</span><span class="sxs-lookup"><span data-stu-id="d7c49-171">1 Hour</span></span> |

## <a name="additional-dns-records"></a><span data-ttu-id="d7c49-172">Registros DNS adicionais</span><span class="sxs-lookup"><span data-stu-id="d7c49-172">Additional DNS records</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7c49-173">Se você tiver um registro CNAME *msoID* existente na sua zona DNS, você deve **remover** o registro do DNS neste momento.</span><span class="sxs-lookup"><span data-stu-id="d7c49-173">If you have an existing *msoid* CNAME record in your DNS zone, you must **remove** the record from DNS at this time.</span></span>  <span data-ttu-id="d7c49-174">O registro msoID é incompatível com aplicativos corporativos da Microsoft 365 *(anteriormente chamado Office 365 ProPlus)* e impedirá a ativação do sucesso.</span><span class="sxs-lookup"><span data-stu-id="d7c49-174">The msoid record is incompatible with Microsoft 365 Enterprise Apps *(formerly Office 365 ProPlus)* and will prevent activation from succeeding.</span></span>
