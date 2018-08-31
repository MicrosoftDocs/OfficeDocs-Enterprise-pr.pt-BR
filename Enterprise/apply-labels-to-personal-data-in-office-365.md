---
title: Aplicar rótulos a dados pessoais no Office 365
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
search.appverid:
- MET150
description: Saiba como usar os rótulos do Office como parte do seu plano de proteção do GDPR.
ms.openlocfilehash: c0058a023b807b81df42274d5e8b9408e37d505d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914926"
---
# <a name="apply-labels-to-personal-data-in-office-365"></a><span data-ttu-id="d1bd9-103">Aplicar rótulos a dados pessoais no Office 365</span><span class="sxs-lookup"><span data-stu-id="d1bd9-103">Apply labels to personal data in Office 365</span></span>

 <span data-ttu-id="d1bd9-p101">Este tópico é útil se estiver usando os rótulos do Office como parte do seu plano de proteção do GDPR. Atualmente, os rótulos podem ser criados no Centro de Conformidade e Segurança do Office 365 e na Proteção de Informações do Azure. Com o tempo, essas tecnologias se fundirão em uma experiência de classificação e rotulação unificadas, e você fará ainda mais com elas.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p101">Use this topic if you are using Office labels as part of your GDPR protection plan. Today labels can be created in the Office 365 Security & Compliance Center and in Azure Information Protection. Over time these technologies will converge into a unified labeling and classification experience and you will be able to achieve even more.</span></span>

<span data-ttu-id="d1bd9-p102">Se você estiver usando rótulos para a proteção de dados pessoais no Office 365, a Microsoft recomenda começar com os rótulos do Office. Use o Advanced Data Governance para aplicar automaticamente os rótulos com base nos tipos de informações confidenciais ou em outros critérios. Use os rótulos do Office com a prevenção contra perda de dados para protegê-los. Também é possível usar os rótulos com a Descoberta eletrônica e com a Pesquisa de Conteúdo. Em breve será possível usar tanto os rótulos quanto os tipos de informações confidenciais com o Cloud App Security para monitorar os dados pessoais localizados em outros aplicativos SaaS.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p102">If you are using labels for protection of personal data in Office 365, Microsoft recommends you start with Office labels. You can use Advanced Data Governance to automatically apply labels based on sensitive information types or other criteria. You can use Office labels with data loss prevention to apply protection. You can also use labels with eDiscovery and Content Search. You’ll soon be able to use both labels and sensitive information types with Cloud App Security to monitor personal data that resides in other SaaS apps.</span></span>

<span data-ttu-id="d1bd9-p103">Atualmente, os rótulos de Proteção de Informações do Azure são recomendados para arquivos no local e outros serviços e provedores na nuvem. Também são recomendados para arquivos no Office 365 que exijam a criptografia Azure Rights Management (Azure RMS) para a proteção de dados, como arquivos de segredos comerciais.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p103">Azure Information Protection labels are currently recommended for applying labels to files on premises and in other cloud services and providers. These are also recommended for files in Office 365 that require Azure Rights Management (Azure RMS) encryption for data protection, such as trade secret files.</span></span>

<span data-ttu-id="d1bd9-p104">No momento, não é recomendável usar a Proteção de Informações do Azure para aplicar a criptografia Azure RMS em arquivos do Office 365 com dados sujeitos ao GDPR. Os serviços do Office 365 no momento não leem os arquivos criptografados pelo RMS. Portanto, o serviço não consegue localizar dados confidenciais nesses arquivos.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p104">At this time, using Azure Information Protection to apply Azure RMS encryption is not recommended for files in Office 365 with data that is subject to the GDPR. Office 365 services currently cannot read into RMS-encrypted files. Therefore, the service can’t find sensitive data in these files.</span></span>

<span data-ttu-id="d1bd9-p105">Os rótulos de Proteção de Informações do Azure podem ser aplicados a emails no Exchange Online e funcionam em conjunto com a proteção contra perda de dados do Office 365. Em breve, com o mecanismo de classificação e rotulação unificadas, será possível usar os mesmos rótulos para emails e arquivos, incluindo rotular e proteger automaticamente os emails em trânsito.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p105">Azure Information Protection labels can be applied to mail in Exchange Online and these labels work with Office 365 data loss prevention. Coming soon with the unified classification and labeling engine you will be able to use the same labels for email and files, including automatically labeling and protecting email in transit.</span></span>

![Rótulos do Office 365 e rótulos da Proteção de Informações do Azure](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="d1bd9-120">Na ilustração:</span><span class="sxs-lookup"><span data-stu-id="d1bd9-120">In the illustration:</span></span>

-   <span data-ttu-id="d1bd9-121">Use os rótulos do Office 365 em dados pessoais e arquivos de segredos comerciais e altamente regulados no SharePoint Online e no OneDrive for Business.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-121">Use Office 365 labels for personal data and for highly regulated & trade secret files in SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="d1bd9-122">Use os rótulos da Proteção de Informações do Azure (AIP) em arquivos de segredos comerciais e altamente regulados, emails do Exchange Online, arquivos de outros serviços SaaS, arquivos em datacenters no local e arquivos em outros provedores em nuvem.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-122">Use Azure Information Protection (AIP) labels for highly regulated & trade secret files, Exchange Online email, files in other SaaS services, files in on-premises datacenters, and files in other cloud providers.</span></span>

-   <span data-ttu-id="d1bd9-123">Em breve: os dois tipos de rótulos se fundirão em uma experiência de classificação e rotulação unificadas.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-123">Coming soon: both types of labels will converge into a unified classification and labeling experience.</span></span>

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a><span data-ttu-id="d1bd9-124">Usar os rótulos do Office e os tipos de informações confidenciais no Microsoft 365 para proteção de informações</span><span class="sxs-lookup"><span data-stu-id="d1bd9-124">Use Office labels and sensitive information types across Microsoft 365 for information protection</span></span>

<span data-ttu-id="d1bd9-125">A ilustração a seguir mostra como os rótulos do Office e os tipos de informações confidenciais podem ser usados em políticas de rotulação, de prevenção contra perda de dados e nas políticas do Cloud App Security.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-125">The following illustration shows how Office labels and sensitive information types can be used in label policies, data loss prevention policies, and with Cloud App Security policies.</span></span>

![Rótulos do Office e tipos de informações confidenciais](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="d1bd9-127">Para maior acessibilidade, a tabela a seguir fornece os mesmos exemplos da ilustração.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-127">For accessibility, the following table provides the same examples in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d1bd9-128"><strong>Elementos de classificação</strong></span><span class="sxs-lookup"><span data-stu-id="d1bd9-128"><strong>Classification elements</strong></span></span></th>
<th align="left"><span data-ttu-id="d1bd9-129"><strong>Políticas de rotulação – dois exemplos</strong></span><span class="sxs-lookup"><span data-stu-id="d1bd9-129"><strong>Label policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="d1bd9-130"><strong>Políticas de prevenção contra perda de dados – dois exemplos</strong></span><span class="sxs-lookup"><span data-stu-id="d1bd9-130"><strong>Data loss prevention policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="d1bd9-131"><strong>Políticas do Cloud App Security para todos os aplicativos SaaS – um exemplo</strong></span><span class="sxs-lookup"><span data-stu-id="d1bd9-131"><strong>Cloud App Security policies for all SaaS apps — 1 example</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d1bd9-p106">Rótulos do Office. Exemplos: Pessoal, Público, Dados do cliente, Dados de RH, Confidencial, Altamente confidencial</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p106">Office labels. Examples: Personal, Public, Customer data, HR data, Confidential, Highly confidential</span></span></td>
<td align="left"><p><span data-ttu-id="d1bd9-p107">Aplicar automaticamente este rótulo...</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p107">Auto apply this label . . .</span></span></p>
<p><span data-ttu-id="d1bd9-137">Dados do cliente</span><span class="sxs-lookup"><span data-stu-id="d1bd9-137">Customer data</span></span></p>
<p><span data-ttu-id="d1bd9-p108">...aos documentos que correspondam a estes tipos de informações confidenciais...</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p108">. . . to documents that match these sensitive information types . . .</span></span></p>
<p><span data-ttu-id="d1bd9-144">&lt;lista de exemplos de tipos de informações confidenciais&gt;</span><span class="sxs-lookup"><span data-stu-id="d1bd9-144">&lt;list of example sensitive information types&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="d1bd9-p109">Aplicar esta proteção...</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p109">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="d1bd9-148">&lt;definir proteção&gt;</span><span class="sxs-lookup"><span data-stu-id="d1bd9-148">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="d1bd9-p110">...aos documentos com este rótulo...</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p110">. . . to documents with this label . . .</span></span></p>
<p><span data-ttu-id="d1bd9-155">Dados do cliente</span><span class="sxs-lookup"><span data-stu-id="d1bd9-155">Customer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="d1bd9-p111">Alertar quando os arquivos com esses atributos...</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p111">Alert when files with these attributes . . .</span></span></p>
<p><span data-ttu-id="d1bd9-159">&lt;atributo PII predefinido – ou – expressão personalizada&gt;</span><span class="sxs-lookup"><span data-stu-id="d1bd9-159">&lt;predefined PII attribute -or- custom expression&gt;</span></span></p>
<p><span data-ttu-id="d1bd9-p112">...forem compartilhados fora da organização em qualquer aplicativo sancionado pela SaaS </span><span class="sxs-lookup"><span data-stu-id="d1bd9-p112">. . . in any sanctioned SaaS app are shared outside the organization</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d1bd9-p113">Tipos de informações confidenciais. Exemplos: Número Nacional de Identificação da Bélgica, Número do cartão de crédito, Número de Cartão de Identidade da Croácia, ID nacional da Finlândia</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p113">Sensitive information types. Examples: Belgium National Number, Credit Card Number, Croatia Identity Cart Number, Finland National ID</span></span></td>
<td align="left"><p><span data-ttu-id="d1bd9-p114">Publicar rótulos para os usuários aplicarem manualmente...</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p114">Publish these labels for users to manually apply . . .</span></span></p>
<p><span data-ttu-id="d1bd9-169">&lt;selecionar rótulos&gt;</span><span class="sxs-lookup"><span data-stu-id="d1bd9-169">&lt;select labels&gt;</span></span></p>
<p><span data-ttu-id="d1bd9-p115">...nestes locais...</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p115">. . . to these locations . . .</span></span></p>
<p><span data-ttu-id="d1bd9-176">&lt;todos os locais ou escolher locais específicos&gt;</span><span class="sxs-lookup"><span data-stu-id="d1bd9-176">&lt;all locations or choose specific locations&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="d1bd9-p116">Aplicar esta proteção...</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p116">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="d1bd9-180">&lt;definir proteção&gt;</span><span class="sxs-lookup"><span data-stu-id="d1bd9-180">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="d1bd9-p117">...aos documentos que correspondam a estes tipos de informações confidenciais&gt;</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p117">. . . to documents that match these sensitive information types&gt;</span></span></p></td>
<td align="left"><span data-ttu-id="d1bd9-185">Observação: entre os atributos que chegarão em breve ao Cloud App Security estão os Tipos de informações confidenciais do Office 365 e os Rótulos unificados no Office 365 e na Proteção de Informações do Azure.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-185">Note: Attributes coming soon to Cloud App Security include Office 365 sensitive information types and Unified labels across Office 365 and Azure Information Protection.</span></span></td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a><span data-ttu-id="d1bd9-186">Priorizar as políticas de aplicação automática de rótulos</span><span class="sxs-lookup"><span data-stu-id="d1bd9-186">Prioritize auto-apply label policies</span></span>

<span data-ttu-id="d1bd9-p118">Para os dados pessoais sujeitos ao GDPR, a Microsoft recomenda a aplicação automática de rótulos usando os tipos de informações confidenciais que você selecionou para seu ambiente. É importante que as políticas de aplicação automática de rótulos sejam bem pensadas e testadas para alcançar o comportamento pretendido.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p118">For personal data that is subject to GDPR, Microsoft recommends auto-applying labels by using the sensitive information types you curated for your environment. It is important that auto-apply label policies are well designed and tested to ensure the intended behavior occurs.</span></span>

<span data-ttu-id="d1bd9-p119">Tanto a ordem de criação das políticas de aplicação automática quanto o fato de os usuários também aplicarem rótulos afetam o resultado. Por isso, é importante planejar a distribuição com atenção. Veja o que é preciso saber.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p119">The order that auto-apply policies are created and whether users are also applying these labels affect the result. So, it is important to carefully plan the roll-out. Here’s what you need to know.</span></span>

### <a name="one-label-at-a-time"></a><span data-ttu-id="d1bd9-191">Um rótulo por vez</span><span class="sxs-lookup"><span data-stu-id="d1bd9-191">One label at a time</span></span>

<span data-ttu-id="d1bd9-192">Só é possível atribuir um rótulo a um documento.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-192">You can only assign one label to a document.</span></span>

### <a name="older-auto-apply-policies-win"></a><span data-ttu-id="d1bd9-193">As políticas de aplicação automática mais antigas têm prioridade</span><span class="sxs-lookup"><span data-stu-id="d1bd9-193">Older auto-apply policies win</span></span>

<span data-ttu-id="d1bd9-p120">Se houver várias regras de atribuição de um rótulo de aplicação automática e o conteúdo atender às condições de várias regras, o rótulo para a regra mais antiga será atribuído. Por esse motivo, é importante planejar as políticas de rotulação com atenção antes de configurá-las. Se uma organização precisar de uma alteração na prioridade das políticas de rotulação, será necessário excluí-las e recriá-las.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p120">If there are multiple rules that assign an auto-apply label and content meets the conditions of multiple rules, the label for the oldest rule is assigned. For this reason, it is important to plan the label policies carefully before configuring them. If an organization requires a change to the priority of the label policies, they will need to delete and recreate them.</span></span>

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a><span data-ttu-id="d1bd9-197">Os rótulos aplicados manualmente pelo usuário prevalecem sobre os rótulos com aplicação automática</span><span class="sxs-lookup"><span data-stu-id="d1bd9-197">Manual user-applied labels trump auto-applied labels</span></span>

<span data-ttu-id="d1bd9-p121">Os rótulos aplicados manualmente pelo usuário prevalecem sobre os rótulos com aplicação automática.As políticas de aplicação automática não podem substituir um rótulo já aplicado por um usuário. Porém, os usuários podem substituir rótulos aplicados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p121">Manual user applied labels trump auto-applied labels. Auto-apply policies cannot replace a label that is already applied by a user. Users can replace labels that are auto-applied.</span></span>

### <a name="auto-assigned-labels-can-be-updated"></a><span data-ttu-id="d1bd9-201">Os rótulos atribuídos automaticamente podem ser atualizados</span><span class="sxs-lookup"><span data-stu-id="d1bd9-201">Auto-assigned labels can be updated</span></span>

<span data-ttu-id="d1bd9-202">Os rótulos atribuídos automaticamente podem ser atualizados por políticas de rotulação mais recentes ou por atualizações das políticas existentes.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-202">Auto-assigned labels can be updated by either newer label policies or by updates to existing policies.</span></span>

<span data-ttu-id="d1bd9-203">Seu plano para a implementação de rótulos deve:</span><span class="sxs-lookup"><span data-stu-id="d1bd9-203">Be sure your plan for implementing labels includes:</span></span>

-   <span data-ttu-id="d1bd9-204">Priorizar a ordem de criação de políticas de aplicação automática.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-204">Prioritizing the order that auto-apply policies are created.</span></span>

-   <span data-ttu-id="d1bd9-p122">Deixar tempo suficiente para a aplicação automática de rótulos antes da distribuição para os usuários aplicarem manualmente. Pode levar até sete dias para que os rótulos sejam aplicados a todo o conteúdo que atende às condições.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p122">Allowing enough time for labels to be automatically applied before rolling these out for users to manually apply. It can take up to seven days for the labels to be applied to all content that matches the conditions.</span></span>

### <a name="example-priority-for-creating-the-auto-apply-policies"></a><span data-ttu-id="d1bd9-207">Exemplo de prioridade para a criação de políticas de aplicação automática</span><span class="sxs-lookup"><span data-stu-id="d1bd9-207">Example priority for creating the auto-apply policies</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d1bd9-208"><strong>Rótulos</strong></span><span class="sxs-lookup"><span data-stu-id="d1bd9-208"><strong>Labels</strong></span></span></th>
<th align="left"><span data-ttu-id="d1bd9-209"><strong>Ordem de prioridade para a criação de políticas de aplicação automática </strong></span><span class="sxs-lookup"><span data-stu-id="d1bd9-209"><strong>Priority order to create auto-apply policies</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d1bd9-210">Recursos humanos – dados de funcionários</span><span class="sxs-lookup"><span data-stu-id="d1bd9-210">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="d1bd9-211">1</span><span class="sxs-lookup"><span data-stu-id="d1bd9-211">1</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d1bd9-212">Dados do cliente</span><span class="sxs-lookup"><span data-stu-id="d1bd9-212">Customer Data</span></span></td>
<td align="left"><span data-ttu-id="d1bd9-213">2</span><span class="sxs-lookup"><span data-stu-id="d1bd9-213">2</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d1bd9-214">Altamente confidencial</span><span class="sxs-lookup"><span data-stu-id="d1bd9-214">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="d1bd9-215">3</span><span class="sxs-lookup"><span data-stu-id="d1bd9-215">3</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d1bd9-216">Recursos humanos – dados salariais</span><span class="sxs-lookup"><span data-stu-id="d1bd9-216">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="d1bd9-217">4</span><span class="sxs-lookup"><span data-stu-id="d1bd9-217">4</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d1bd9-218">Confidencial</span><span class="sxs-lookup"><span data-stu-id="d1bd9-218">Confidential</span></span></td>
<td align="left"><span data-ttu-id="d1bd9-219">5</span><span class="sxs-lookup"><span data-stu-id="d1bd9-219">5</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d1bd9-220">Público</span><span class="sxs-lookup"><span data-stu-id="d1bd9-220">Public</span></span></td>
<td align="left"><span data-ttu-id="d1bd9-221">6</span><span class="sxs-lookup"><span data-stu-id="d1bd9-221">6</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d1bd9-222">Pessoal</span><span class="sxs-lookup"><span data-stu-id="d1bd9-222">Personal</span></span></td>
<td align="left"><span data-ttu-id="d1bd9-223">Nenhuma política de aplicação automática</span><span class="sxs-lookup"><span data-stu-id="d1bd9-223">No auto-apply policy</span></span></td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a><span data-ttu-id="d1bd9-224">Criar rótulos e políticas de aplicação automática de rótulos</span><span class="sxs-lookup"><span data-stu-id="d1bd9-224">Create labels and auto-apply label policies</span></span>

<span data-ttu-id="d1bd9-225">Crie rótulos e políticas no Centro de Conformidade e Segurança.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-225">Create labels and policies in the Security & Compliance Center.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d1bd9-226"><strong>Etapa</strong></span><span class="sxs-lookup"><span data-stu-id="d1bd9-226"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="d1bd9-227"><strong>Descrição</strong></span><span class="sxs-lookup"><span data-stu-id="d1bd9-227"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="d1bd9-228">Conceder permissões aos membros da sua equipe de conformidade.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-228">Give permissions to members of your compliance team.</span></span></p></td>
<td align="left"><p><span data-ttu-id="d1bd9-p123">Os membros da sua equipe de conformidade que criarão os rótulos precisam de permissões para usar o Centro de Conformidade e Segurança. Acesse as Permissões, no Centro de Conformidade e Segurança, e modifique os membros do grupo Administrador de Conformidade.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p123">Members of your compliance team who will create labels need permissions to use the Security &amp; Compliance Center. Go to Permissions in Security and Compliance Center and modify the members of the Compliance Administrator group.</span></span></p>
<p><span data-ttu-id="d1bd9-231">Confira <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Conceder aos usuários acesso ao Centro de Conformidade e Segurança do Office 365</a>.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-231">See <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Give users access to the Office 365 Security &amp; Compliance Center</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="d1bd9-232">Criar rótulos do Office.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-232">Create Office labels.</span></span></p></td>
<td align="left"><span data-ttu-id="d1bd9-233">Acesse Classificações, no Centro de Conformidade e Segurança, escolha Rótulos e crie os rótulos para o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-233">Go to Classifications in Security and Compliance Center, choose Labels, and create the labels for your environment.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="d1bd9-234">Criar políticas de aplicação automática para rótulos.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-234">Create auto-apply policies for labels.</span></span></p></td>
<td align="left"><span data-ttu-id="d1bd9-p124">Acesse Classificações, no Centro de Conformidade e Segurança, escolha Políticas de rotulação e crie as políticas para a aplicação automática de rótulos. Crie as políticas por ordem de prioridade.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-p124">Go to Classification in Security and Compliance Center, choose Label policies, and create the policies for auto-applying labels. Be sure to create these policies in the prioritized order.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="d1bd9-237">A ilustração a seguir mostra como criar um rótulo de aplicação automática para o Rótulo dados do cliente.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-237">The following illustration shows how to create an auto-apply label for the Customer data label.</span></span>

![Criar e aplicar um rótulo para dados do cliente](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="d1bd9-239">Na ilustração:</span><span class="sxs-lookup"><span data-stu-id="d1bd9-239">In the illustration:</span></span>

-   <span data-ttu-id="d1bd9-240">O rótulo "Dados do cliente" foi criado.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-240">The “Customer data” label is created.</span></span>

-   <span data-ttu-id="d1bd9-241">Os tipos de informações confidenciais desejados para o GDPR foram listados: Número Nacional de Identificação da Bélgica, Número do cartão de crédito, Número de Cartão de Identidade da Croácia, ID nacional da Finlândia.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-241">The desired sensitive information types for GDPR are listed: Belgium National Number, Credit Card Number, Croatia Identity Card Number, Finland National ID.</span></span>

-   <span data-ttu-id="d1bd9-242">Criar uma política de aplicação automática atribui o rótulo "Dados do cliente" a todo arquivo com um dos tipos de informação confidencial que você adicionar à política.</span><span class="sxs-lookup"><span data-stu-id="d1bd9-242">Create an auto-apply policy assigns the label “Customer data” to any file that includes one of the sensitive information types that you add to the policy.</span></span>
