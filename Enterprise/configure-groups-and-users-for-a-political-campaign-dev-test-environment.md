---
title: "Configurar grupos e usuários para um ambiente de desenvolvimento e teste de campanha política"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "Resumo: Crie assinaturas de avaliação de segurança (EMS) + Office 365 e mobilidade da empresa com usuários e grupos para um ambiente de desenvolvimento e teste de campanha política."
ms.openlocfilehash: e876c8770651c3f23c06c9c499bdaabca52da353
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>Configurar grupos e usuários para um ambiente de desenvolvimento e teste de campanha política

 **Resumo:** Crie assinaturas de avaliação de segurança (EMS) + Office 365 e mobilidade da empresa com usuários e grupos para um ambiente de desenvolvimento e teste de campanha política.
  
Use as instruções deste artigo para criar um ambiente de desenvolvimento e teste que inclui contas de usuário simplificada e grupos para a solução de [Diretrizes de segurança da Microsoft para campanhas político, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) .
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>Fase 1: Criar seu ambiente de desenvolvimento e teste do Office 365

Nesta fase, você deve obter assinaturas de avaliação do Office 365 E5 e mobilidade corporativos + E5 de segurança (EMS) para uma empresa fictícia que representa uma campanha de política.
  
Primeiro, siga as instruções na **fase 2** do [ambiente de desenvolvimento e teste do Office 365](office-365-dev-test-environment.md).
  
Em seguida, inscreva-se para a assinatura de avaliação do EMS E5 e adicioná-lo à mesma organização que sua assinatura de avaliação do Office 365.
  
1. Se necessário, entre no portal do Office 365 com as credenciais da conta de administrador global de sua assinatura de avaliação. Para obter ajuda, consulte [Where entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Clique no lado do **Admin** .
    
3. Na guia do **Centro de administração do Office** em seu navegador, no painel de navegação esquerdo, clique em **faturamento > Serviços de compra**.
    
4. Na página **Serviços de compra** , localize o item de **mobilidade corporativos + E5 de segurança** . Passe o ponteiro do mouse sobre ele e clique em **Iniciar a versão gratuita de avaliação**.
    
5. Na página **confirmar seu pedido** , clique em **tente agora**.
    
6. Na página **confirmação de ordem** , clique em **continuar**.
    
Em seguida, habilite a licença do EMS E5 para sua conta de administrador global.
  
1. Na guia do **Centro de administração do Office 365** em seu navegador, no painel de navegação esquerdo, clique em **usuários > usuários ativos**.
    
2. Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **licenças de produto**.
    
3. No painel de **licenças do produto** , ativar a licença do produto para **mobilidade corporativos + E5 de segurança** para **ativado**, clique em **Salvar** e, em seguida, clique duas vezes em **Fechar** .
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>Fase 2: Criar e configurar seus grupos do Windows Azure AD (Active Directory)

Nesta fase, criar e configurar os grupos do Azure AD para sua campanha.
  
Primeiro, crie um conjunto de grupos para uma campanha político típica com o portal do Azure.
  
1. Em uma guia separada no seu navegador, vá para o portal do Windows Azure em [https://portal.azure.com](https://portal.azure.com). Se necessário, entre com as credenciais da conta de administrador global para a sua assinatura de avaliação do Office 365 E5.
    
2. No portal do Azure, clique em **Azure Active Directory > usuários e grupos > todos os grupos**.
    
3. Execute as seguintes etapas para cada nome de grupo nesta lista:
    
  - Sênior e à equipe estratégica
    
  - Equipe de TI
    
  - Equipe de análise
    
  - Equipe de núcleo regular
    
  - Equipe de operações
    
  - Equipe de campo
    
1. No blade **todos os grupos** , clique em **+ novo grupo**.
    
2. Digite o nome de grupo da lista em **nome**.
    
3. Selecione o **usuário dinâmico** na **associação**.
    
4. Clique em **Sim** para **Habilitar o Office recursos**.
    
5. Clique em **Add query de dinâmico**.
    
6. No **Adicionar usuários onde**, selecione o **departamento**.
    
7. No próximo campo, selecione **é igual a**.
    
8. No campo próximo, digite o nome de grupo da lista.
    
9. Clique em **Add query**e, em seguida, clique em **criar**.
    
10. Clique em **usuários e grupos - todos os grupos**.
    
Em seguida, configure os grupos para que os membros são automaticamente atribuídos licenças do Office 365 E5 e EMS E5.
  
1. No portal do Azure, clique em **Azure Active Directory > licenças > todos os produtos**.
    
2. Na lista, selecione **Enterprise mobilidade + E5 de segurança** e o **Office 365 Enterprise E5**e, em seguida, clique em **+ atribuir**.
    
3. Na blade **atribuir licença** , clique em **usuários e grupos**.
    
4. Na lista de grupos, selecione o seguinte:
    
  - Equipe de análise
    
  - Equipe de campo
    
  - Equipe de TI
    
  - Equipe de operações
    
  - Equipe de núcleo regular
    
  - Sênior e à equipe estratégica
    
5. Clique em **Selecionar**e, em seguida, clique em **atribuir**.
    
6. Feche a Azure guia portal no seu navegador.
    
## <a name="phase-3-add-your-user-accounts"></a>Fase 3: Adicionar suas contas de usuário

Nesta fase, você pode adicionar as contas de usuário de exemplo para sua campanha política.
  
Primeiro, você [conectar com o módulo do Azure Active Directory V2 PowerShell](https://go.microsoft.com/fwlink/?linkid=842218).
  
Em seguida, preencha o nome da sua organização, seu local e uma senha comum e, em seguida, execute estes comandos no prompt de comando do PowerShell ou ambiente de Script integrado (ISE):
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> O uso de uma senha comum aqui é para automação e facilidade de configuração para um ambiente de desenvolvimento e teste. Isso não é recomendado para assinaturas de produção. Conforme você entrar com cada um dessas novas contas de usuário, você será solicitado para alterar a senha. 
  
Use estas etapas para verificar se a associação ao grupo dinâmico e licenciamento baseado no grupo estão funcionando corretamente.
  
1. Na guia **Página inicial do Microsoft Office** do seu navegador, clique no lado do **Admin** .
    
2. Na guia novo **Centro de administração do Office** do seu navegador, clique em **usuários**.
    
3. Na lista de usuários, clique em **candidato**.
    
4. No painel que lista as propriedades da conta de usuário de **candidato** , verifique se:
    
  - Ele é um membro do grupo **sênior e à equipe estratégico** (em **associações de grupo**).
    
  - Ela recebeu as licenças de **mobilidade corporativos + E5 de segurança** e o **Office 365 Enterprise E5** (em **licenças do produto**).
    
5. Feche o painel de conta de usuário do **candidato** .
    
## <a name="record-values-for-future-reference"></a>Valores do registro para referência futura

Esses valores para trabalhar com o Office 365 e EMS assinaturas de avaliação para este ambiente de desenvolvimento e teste de registro:
  
- O nome da sua organização de assinatura de avaliação: _ 
    
    Por exemplo, o nome de domínio de assinatura de avaliação de contoso.onmicrosoft.com, o nome da organização é "contoso".
    
- O nome de administrador global do Office 365: ___.onmicrosoft.com
    
    Registre a senha dessa conta e a senha inicial comuns para as outras contas de usuário em um local seguro.
    
## <a name="next-step"></a>Próxima etapa

Construa os quatro tipos diferentes de sites de equipe do SharePoint Online neste ambiente de desenvolvimento e teste com [criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política](create-team-sites-in-a-political-campaign-dev-test-environment.md).
  
## <a name="see-also"></a>Veja também

[Orientação de segurança da Microsoft para campanhas políticas, organizações sem fins lucrativos e outras organizações ágil](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Criar sites de equipe em um ambiente de desenvolvimento e teste de campanha política](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
  
[Adoção da nuvem e soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




