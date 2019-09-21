---
title: Controles de pessoal do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 'Resumo: uma visão geral das práticas de triagem de pessoal da Microsoft para o Office 365.'
ms.openlocfilehash: 82a8578ef5b5812dc3dfcfa69ccff604d2254286
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067122"
---
# <a name="office-365-personnel-controls"></a>Controles de pessoal do Office 365 

A triagem de pessoal, o processo de revisão e validação do comportamento passado e o status de um candidato é um importante controle de mitigação para impedir o comprometimento do serviço do Office 365. Enquanto o comportamento passado não é uma previsão perfeita do comportamento futuro, ele ajuda a identificar possíveis atores defeituosos. O padrão de triagem de pessoal da Microsoft se aplica a todos os funcionários da Microsoft, estagiários e equipes contingentes envolvidos no desenvolvimento, na operação ou na entrega de serviços online para clientes do governo ou da nuvem comercial. Padrões de triagem para ambientes de nuvem nacionais não operados pela Microsoft são definidos pelo pessoal do parceiro operacional para cada ambiente específico.

## <a name="the-microsoft-personnel-screening-standard"></a>O padrão de triagem de pessoal da Microsoft

As práticas de triagem de pessoal do Office 365 são alinhadas com os padrões corporativos da Microsoft e os controles NIST (National Institute of Standards and Technology) para a triagem de pessoal. A equipe da Microsoft que precisa acessar os seguintes estão sujeitas ao padrão de triagem de pessoal da Microsoft:

- Acesso físico a datacenters, colocalidades, salas seguras, compartimentos, racks de servidor ou sites de borda que oferecem a infraestrutura que oferece suporte a serviços online para clientes governamentais ou de nuvem comercial.
- Acesso lógico a dados governamentais ou de cliente de nuvem comercial fornecido por meio de ambientes gerenciados específicos.
- Acesso de gerenciamento de rede a dispositivos e serviços que transportem ou armazenem dados de clientes de nuvem ou do governo comercial.

Eventos específicos relacionados ao pessoal que disparam os requisitos de filtragem incluem:

- Nova equipe da Microsoft colocada em funções em que a triagem é um requisito definido.
- Equipe interna da Microsoft transferida ou movida para uma função existente que atualmente inclui a triagem como um requisito definido.
- Funções existentes que alteram o escopo para incluir a triagem como um requisito definido.

## <a name="screening-enforcement-criteria"></a>Critérios de imposição de triagem

Para garantir que apenas o pessoal aprovado tenha acesso aos dados do cliente ou ambientes que exijam a triagem, os critérios de aplicação a seguir se aplicam.

**Apenas ambientes de nuvem dos Estados Unidos**:

- O acesso aos dados do cliente ou ambientes que exigem a triagem é permitido somente depois que o Adjudication é concluído e os requisitos de filtragem são aprovados.
- A equipe da Microsoft que não precisa mais acessar dados do cliente ou ambientes relacionados tem acesso removido ao sair da Microsoft ou de mudar para uma nova função.
- A equipe da Microsoft deixa cartões inteligentes de ambiente em tela com gerenciamento antes de sair dos Estados Unidos.

**Ambientes de nuvem nacionais**:

- O operador de terceiros ou a equipe de confiança de dados é responsável por gerenciar e impor o acesso a ambientes de nuvem nacionais.

Nos ambientes de serviços em nuvem da Microsoft, o acesso é restrito com base na função de uma pessoa e no tipo de dados envolvido, conforme detalhado na tabela abaixo. Pessoal qualificado ou não qualificado fisicamente localizado fora dos Estados Unidos não tem permissão para ter acesso aos dados do cliente dentro de uma nuvem dos Estados Unidos. O acesso aos ambientes de nuvem nacionais é restrito para que a equipe da Microsoft não tenha acesso técnico a dados do cliente ou sistemas que contenham dados do cliente, sem a aprovação do operador de terceiros ou de confiança de dados.

| Role | Acesso aos dados do cliente | Acesso aos dados do sistema |
|---------------------------------------------------------------------------|------------------------------|---------------------------------|
| Pessoal qualificado localizado fisicamente nos Estados Unidos | Permitido | Permitido |
| Pessoal qualificado localizado fisicamente fora dos Estados Unidos | Não permitido | Permitido |
| Acesso de exceção internacional para a equipe da Microsoft: permite que o acesso lógico para a equipe da Microsoft não resida no país onde os dados de clientes governamentais ou comerciais estão em repouso | Não permitido | Permitido |
| Pessoal não qualificado (pessoal não filtrado que exige um Escort por pessoal qualificado) | Permitido com autorização | Permitido com supervisão Escort |

## <a name="microsoft-pre-employment-screening"></a>Triagem de pré-emprego da Microsoft

Onde a legislação local permite, o departamento de segurança global da Microsoft conduz a triagem de pré-emprego. Essa é uma investigação de fundo formal que inclui os seguintes critérios:

- Uma verificação do currículo de conclusão e precisão do candidato
- Confirmação de qualificações acadêmicas e profissionais
- Investigação de qualquer perda de credenciais profissionais
- Verificação dos últimos três empregadores
- Uma verificação de registros de polícia para crimes condenações
- Confirmação de identidade de uma identificação emitida pelo governo
- Verificações de crédito onde apropriado

As verificações periódicas de tela e/ou de segundo plano podem ser necessárias para determinadas funções de gerenciamento, segurança ou outras, incluindo, mas não se limitar a funcionários baseados nos Estados Unidos em funções que exigem acesso aos dados do cliente.
Para pessoas contingentes, o contrato com o terceiro especifica os requisitos da Microsoft para a triagem que devem ser conduzidas pela terceiros. Para verificações em segundo plano, a empresa de terceiros é responsável por fornecer à verificação da Microsoft que uma verificação em segundo plano foi executada. Os resultados da verificação em segundo plano normalmente são recebidos por email do departamento de recursos humanos de terceiros. Os funcionários internacionais da equipe de contrato podem ser isentos do processo de triagem em segundo plano devido às leis em países que proíbem verificações em segundo plano.

## <a name="microsoft-employment-screening"></a>Triagem de emprego da Microsoft

Desde 2004 nos Estados Unidos, a Microsoft exige que os funcionários e os estagiários transmitam uma tela de registro criminal de sete anos como parte da triagem de contratação. A triagem de felonies, Misdemeanors e verificação de educação e histórico de empregos está incluída.

Antes de atribuir um funcionário da Microsoft ou qualquer subcontratado atribuído pela Microsoft para fornecer serviços relacionados ao Office 365, a Microsoft conduz e exige que os subcontratados realizem uma verificação em segundo plano que consiste em um rastreamento de número de segurança social e verificação de registro criminal. Os dados dessa verificação em segundo plano são um fator na decisão de contratação. A verificação de registro criminal inclui uma verificação de registros criminais de crimes e contravenções de sete anos de registros federais, estaduais e municípios (conforme aplicável).

Como condição de emprego e, no momento da admissão, todos os funcionários da Microsoft precisam assinar acordos de confidencialidade e não divulgação e verificar se eles revisaram o manual do funcionário da Microsoft.

## <a name="microsoft-cloud-background-check"></a>Verificação em segundo plano do Microsoft Cloud

Uma verificação em segundo plano do Microsoft Cloud é necessária para os candidatos contratados como funcionários que fornecem serviços relacionados ao Office 365 nos Estados Unidos. Os funcionários da Microsoft nos Estados Unidos com acesso aos dados do cliente devem seguir o processo de verificação em segundo plano do Microsoft Cloud exigido por todos os serviços do Office 365. Fora dos Estados Unidos, o processo varia. Por exemplo, a nuvem da Microsoft para a Alemanha usa um modelo de aprovação de confiança de dados, projetado para garantir que a confiança de dados (uma empresa alemã), e não a Microsoft, esteja no controle de acesso aos dados dos clientes. A nuvem da Microsoft na Alemanha é entregue de datacenters na Alemanha, e os centros de operações (OC) que contêm a equipe técnica dos dados de confiança também estão na Alemanha. Ambas as instalações de datacenter e OC são operadas, mantidas e controladas pelo confiável de dados.

A tabela a seguir lista as verificações executadas como parte da verificação em segundo plano do Microsoft Cloud.

| Análises | Descrição |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pesquisa de número de segurança social | Verifica se o número de seguro social fornecido é válido. |
| Verificação de antecedentes criminais | Registros criminais de sete anos procure por crimes e contravenções offenses nos níveis de estado, região e local e, conforme apropriado, no nível federal. |
| Office de lista de controle de ativos estrangeiros | Departamento da lista de pessoas e organizações com os quais os cidadãos e residentes permanentes dos Estados Unidos não têm permissão para fazer negócios. |
| Central de setores e lista de segurança | Lista de pessoas e entidades do departamento de comércio, bloqueando as atividades de exportação. |
| Lista de pessoas desbloqueadas de controles de comércio de defesa (*adicionado em 1º de julho de 2010*) | Lista de pessoas e entidades do departamento de estado, bloqueando as atividades de exportação relacionadas ao setor de proteção. |

Os resultados da verificação em segundo plano do Microsoft Cloud são armazenados em nosso banco de dados de funcionários e conectados a nossos sistemas de controle de acesso de datacenter. Se a verificação em segundo plano do Microsoft Cloud expirar e o funcionário não a renovar, o acesso aos serviços do Office 365 será revogado e não estará mais disponível até que a verificação em segundo plano do Microsoft Cloud seja concluída. Quando o relacionamento de emprego com a Microsoft termina, todos os acessos de datacenters são imediatamente revogados.

A cidadania dos Estados Unidos é verificada para todos os funcionários com acesso físico ou lógico aos serviços governamentais do Office 365 Brasil. Para verificar a cidadania, funcionários e/ou novos candidatos de contratação são atendidos com um representante de cidadania americana que é treinado para analisar a documentação de verificação de cidadania dos EUA. Funcionários ou novos candidatos de admissão devem trazer a documentação necessária e assinar um formulário de atestado em uma reunião com o representante de cidadania para sua região. A reunião deve ser feita em pessoa. Depois que a pessoa atende ao representante de cidadania e forneceu a documentação e as assinaturas necessárias, o representante de cidadania encaminha uma cópia dos documentos às operações de equipe da Microsoft que enviam a cópia para manutenção de registros.

A equipe com acesso lógico à nuvem da Comunidade do governo dos EUA do Office 365, ou acesso lógico ou físico às ofertas do governo dos EUA do Azure, devem estar em conformidade com os requisitos do governo federal das [informações de justiça criminal do FBI Services](https://www.fbi.gov/services/cjis) (CJIS), incluindo a triagem de pessoal. A triagem do CJIS no suporte do serviço do governo dos EUA do Office 365 inclui uma verificação de fundo criminal com base em impressão digital confederados pela Agência de sistema do CJIS designada adjudicator em [Estados que foram registrados](https://blogs.office.com/2013/10/23/california-and-microsoft-sign-cjis-security-policy-agreement/) no Microsoft Online Services CJIS programa de suporte.
