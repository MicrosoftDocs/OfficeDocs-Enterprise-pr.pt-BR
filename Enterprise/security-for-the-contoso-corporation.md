---
title: "Segurança para a Contoso Corporation"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: "Resumo: Entenda como Contoso mapeadas seus requisitos de segurança para recursos no ofertas de nuvem da Microsoft e determinado um caminho para a preparação de segurança na nuvem."
ms.openlocfilehash: f8df7f6437159aefe88851a22cc8da8b19c3838c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="security-for-the-contoso-corporation"></a>Segurança para a Contoso Corporation

 **Resumo:** Compreenda como Contoso mapeadas seus requisitos de segurança para recursos no ofertas de nuvem da Microsoft e determinado um caminho para a preparação de segurança na nuvem.
  
Contoso é sério sobre seus proteção e a segurança das informações. Ao fazer a transição de infra-estrutura de TI para um outro inclusive de nuvem, feitas certeza de que seus requisitos de segurança local tinham suporte e implementados no ofertas de nuvem da Microsoft.
  
## <a name="contosos-security-requirements-in-the-cloud"></a>Requisitos de segurança da Contoso na nuvem

Aqui estão os requisitos de segurança da Contoso para a nuvem:
  
- Autenticação forte aos recursos de nuvem
    
    Acesso aos recursos de nuvem devem ser autenticados e, onde for possível, utilize a autenticação multifator.
    
- Criptografia para o tráfego na Internet
    
    Nenhum dado enviado pela Internet está no formulário de texto sem formatação. Sempre use conexões HTTPS, IPsec ou outros métodos de criptografia de dados de ponta a ponta.
    
- Criptografia de dados em repouso na nuvem
    
    Todos os dados armazenados em discos ou em outro lugar na nuvem devem estar no formato criptografado.
    
- ACLs para acesso de privilégio mínimo
    
    Permissões de conta para acessar recursos na nuvem e o que é permitido fazer devem seguir as diretrizes de privilégios mínimos.
    
## <a name="contosos-data-sensitivity-classification"></a>Classificação de sensibilidade de dados da Contoso

Usando as informações no do Microsoft [Kit de ferramentas de classificação de dados](https://msdn.microsoft.com/library/hh204743.aspx), a Contoso realizou uma análise dos seus dados e determinados níveis a seguir.
  
|**Nível 1: Valor de negócio baixa**|**Nível 2: Valor de negócio médio**|**Nível 3: Valor de negócios de alto**|
|:-----|:-----|:-----|
|Dados são criptografados e está disponível somente para usuários autenticados  <br/> Fornecido para todos os dados armazenados no local e no armazenamento baseado em nuvem e cargas de trabalho, como o Office 365. Os dados são criptografados enquanto ele reside no serviço e em trânsito entre os dispositivos de cliente e de serviço.  <br/> Exemplos de dados de nível 1 são as comunicações de negócios normal (email) e arquivos de vendas administrativos e suportam a funcionários.  <br/> |Proteção de perda de dados e autenticação forte além de nível 1  <br/> Autenticação forte inclui a autenticação multifator com a validação de SMS. Prevenção de perda de dados garante que as informações confidenciais ou críticas não viajam fora da rede local.  <br/> Exemplos de dados de nível 2 são informações legais e financeiras e dados de pesquisa e desenvolvimento de novos produtos.  <br/> |Além os maiores níveis de criptografia, autenticação e auditoria de nível 2  <br/> Os mais altos níveis de criptografia de dados em repouso e na nuvem, em conformidade com regulamentos regionais, combinado com a autenticação multifator com cartões inteligentes e granular auditoria e alertas.  <br/> Exemplos de dados de nível 3 são clientes e parceiros informações de identificação pessoal e especificações de engenharia de produto e técnicas de fabricação proprietárias.  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>Mapeando ofertas de nuvem da Microsoft e recursos para os níveis de dados da Contoso

A tabela a seguir mostra o mapeamento de níveis de dados da Contoso recursos nas ofertas de nuvem da Microsoft:
  
||**SaaS**|**PaaS Azure**|**Azure IaaS**|
|:-----|:-----|:-----|:-----|
|Nível 1: Valor de negócio baixa  <br/> | HTTPS para todas as conexões <br/>  Criptografia de tempo de parada <br/> | Suporte apenas conexões HTTPS <br/>  Criptografar arquivos armazenados no Windows Azure <br/> | Exigir HTTPS ou IPsec para acesso ao servidor <br/>  Criptografia de disco do Windows Azure <br/> |
|Nível 2: Valor de negócio médio  <br/> | Azure AD a autenticação multifator (MFA) com o SMS <br/> | Use o Windows Azure chave Vault chaves de criptografia <br/>  Azure MFA do AD com o SMS <br/> | MFA com SMS <br/> |
|Nível 3: Valor de negócios de alto  <br/> | Sistema de gerenciamento de direitos do Windows Azure (RMS) <br/>  Azure MFA do AD com cartões inteligentes <br/>  Acesso de condicional Intune <br/> | Azure RMS <br/>  Azure MFA do AD com cartões inteligentes <br/> | MFA com cartões inteligentes <br/> |
   
## <a name="contosos-information-policies"></a>Políticas de informações da Contoso

A tabela a seguir lista as políticas de informações da Contoso.
  
||**Acesso**|**Retenção de dados**|**Proteção de informações**|
|:-----|:-----|:-----|:-----|
|Nível 1: Valor de negócio baixa  <br/> | Permitir o acesso a todos <br/> |6 meses  <br/> |Usar a criptografia  <br/> |
|Nível 2: Valor de negócio médio  <br/> | Permitir acesso a Contoso funcionários, fornecedores e parceiros <br/>  Usar MFA, TLS e MAM <br/> |2 anos  <br/> |Usar valores de hash para integridade dos dados  <br/> |
|Nível 3: Valor de negócios de alto  <br/> | Permitir acesso a executivos e lidera a fabricação e de engenharia <br/>  RMS com somente os dispositivos de rede gerenciada <br/> |sete anos  <br/> |Usar assinaturas digitais para não-recusa  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>Caminho da Contoso para preparação de segurança de nuvem

A Contoso usou as seguintes etapas para preparar seu segurança para a nuvem da Microsoft:
  
1. Otimizar a contas de administrador para a nuvem
    
    Contoso fez uma revisão ampla das contas de administrador do AD do Windows Server existentes e configure a uma série de grupos e contas de administrador de nuvem.
    
2. Executar a análise de classificação de dados em três níveis
    
    A Contoso executada uma análise criteriosa e determinados os três níveis, que era usado para determinar a nuvem da Microsoft que oferece recursos para proteger os dados mais valiosos da Contoso.
    
3. Determinar as políticas de proteção de acesso, retenção e informações para níveis de dados
    
    Com base nos níveis de dados, a Contoso determinados requisitos detalhados, que serão utilizados para se qualificar futuras cargas de trabalho do IT sendo movidas para a nuvem.
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Uso da Contoso das práticas recomendadas de segurança do Office 365

De acordo com o Office 365 práticas recomendadas de segurança, os administradores de segurança e o departamento de TI da Contoso implantou o seguinte:
  
- **Contas de administrador global com senhas fortes muito de dedicada**
    
    Em vez de atribuir a função de administrador global às contas de usuário cotidianos, Contoso tem criar três, dedicada a contas de administrador global com senhas fortes muito. Entrar com uma conta de administrador global é feito apenas para as tarefas administrativas específicas e as senhas são conhecidas apenas à equipe designada. Os administradores de segurança da Contoso atribuiu funções de administrador para contas que são apropriadas para a função de trabalho dessa pessoa IT e responsabilidade.
    
    Para obter mais informações, consulte [funções de administrador do Office 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).
    
- **A autenticação multifator (MFA) para contas de usuário importantes**
    
    MFA adiciona uma camada adicional de proteção para o processo de entrada por exigir que os usuários de agradecer uma chamada telefônica, uma notificação de aplicativo em seu telefone inteligente após inserir corretamente suas senhas ou mensagem de texto. Com MFA, contas de usuário do Office 365 estão protegidas contra entrar não autorizado, mesmo se uma senha de conta for comprometida.
    
  - Para proteger contra um comprometimento da assinatura do Office 365, a Contoso habilitado MFA em todas as três contas de administrador global.
    
  - Para proteger contra ataques de phishing, na qual um invasor compromete as credenciais de uma pessoa confiável na organização e envia emails mal-intencionado, Contoso habilitado MFA em todas as contas de usuário para os gerentes, incluindo o quadro de executivos.
    
    Para obter mais informações, consulte [Planejar a autenticação multifator para implantações do Office 365](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)
    
- **Gerenciamento de segurança avançada (ASM)**
    
    Usos ASM configurou as diretivas para o monitoramento de atividade anormal. Os administradores de segurança da Contoso configurar alertas com ASM, de modo que os administradores de TI são notificados de atividade do usuário incomum ou riscado, como baixar grandes quantidades de dados, vários falhou tentativas de entrada ou entradas de endereços IP perigosos ou desconhecidos
    
    Para obter mais informações, consulte [Visão geral do gerenciamento avançado de segurança no Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).
    
- **Log de auditoria de caixa de correio e de fluxo de email seguro**
    
    Especialistas em segurança de Contoso estão usando o Exchange Online Protection e proteção de ameaça avançadas (ATP) para proteger contra malware desconhecido, vírus e URLs mal-intencionadas transmitidos por meio de emails. A Contoso também tem para determinar que entrou no caixas de correio do usuário, mensagens, enviadas e outras atividades realizadas pelo proprietário da caixa de correio, um usuário delegado ou administrador do log de auditoria de caixa de correio habilitada.
    
    Para obter mais informações, consulte: 
    
  - [Proteção de Anti-Spam de Email do Office 365](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [Proteção contra ameaças avançadas para anexos seguros e links de seguros](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [Habilitar a auditoria de caixa de correio no Office 365](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **Prevenção de perda de dados (DLP)**
    
    Contoso tem identificado seus dados confidenciais e configurou as diretivas DLP para Exchange Online, SharePoint Online e OneDrive ajudar a impedir que usuários acidentalmente ou intencionalmente compartilhamento de dados. 
    
    Para obter mais informações, consulte [Visão geral das políticas de prevenção de perda de dados](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).
    
## <a name="see-also"></a>Veja também

[Contoso na Microsoft Cloud](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitetura de TI do Microsoft](microsoft-cloud-it-architecture-resources.md)

[Roteiro do Enterprise Cloud da Microsoft: recursos para os responsáveis pelas decisões de TI](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Práticas recomendadas de segurança para o Office 365](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




