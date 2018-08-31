---
title: Instalar e executar a ferramenta IdFix do Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Como instalar e executar a ferramenta IdFix do Office 365 para ajudar a limpar seu active directory antes de sincronizá-lo para o Office 365.
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539157"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Instalar e executar a ferramenta IdFix do Office 365

IdFix identifica erros como duplicatas e problemas de formatação em seu diretório antes de sincronizar com o Office 365. 
  
Para concluir esta tarefa com êxito, você deve estar familiarizado com o usuário, grupo e objetos de contato no Active Directory.
  
Se você não pode concluir essa tarefa, há algumas outras coisas que você pode fazer. Esses métodos podem ser mais fácil, mas eles também podem levar mais tempo ou ter outros inconvenientes. Eles são:
  
- **Executar a sincronização de diretórios sem executar o IdFix.** Você pode sincronizar seu diretório sem executar a ferramenta IdFix, mas não é recomendável. Corrigindo erros antes de sincronizar demora menos tempo e geralmente fornece uma transição mais suave para a nuvem. 
- **Contrate um consultor.** Obter ajuda especializada pode fazer com que seus usuários fiquem prontos para trabalhar com rapidez e que seu diretório seja sincronizado. 
    
## <a name="what-you-need-to-run-idfix"></a>O que você precisa para executar o IdFix

A maneira mais fácil de fazer o IdFix para cima e em execução é instalá-lo em um computador que está vinculado ao seu domínio. Você pode executá-lo no controlador de domínio, se desejar, mas não é necessário.
  
### <a name="idfix-hardware-requirements"></a>Requisitos de hardware do IdFix

O computador no qual você instalar o IdFix precisa atender a estes requisitos de hardware:
  
- 4 GB de RAM (mínimo)
- 2 GB de espaço em disco (mínimo)
    
### <a name="idfix-software-requirements"></a>Requisitos de software do IdFix

O computador onde você instala o IdFix precisa deve estar associado ao mesmo domínio do Active Directory do qual você deseja sincronizar usuários para o Office 365. O computador também precisa ter o .NET Framework 4.0 estiver instalado. 
  
Se você estiver executando o Windows Server 2008 ou Windows Server 2012, o .NET Framework provavelmente já está instalado. Se não, você pode [baixar o .NET 4.0 Centro de download da](https://go.microsoft.com/fwlink/p/?LinkId=400475) ou usando o Windows Update. 
  
### <a name="idfix-permissions-requirements"></a>Requisitos de permissões do IdFix

A conta de usuário que você usa para executar o IdFix precisa ter acesso de leitura/gravação ao diretório.
  
Se você não tiver certeza se a sua conta de usuário atende a esses requisitos, e você não souber como verificar, você pode instalar e executar o IdFix mesmo assim. Se a sua conta de usuário não tem as permissões corretas, o IdFix simplesmente exibirá um erro ao tentar executá-lo.
  
## <a name="install-idfix"></a>Instalar o IdFix

Para instalar o IdFix, baixe e descompacte o **IdFix.exe** como descrito nestas etapas: 
  
1. Faça logon no computador no qual deseja instalar a ferramenta IdFix.
    
2. Vá para o site de download da Microsoft para a [Ferramenta de correção de erro do IdFix DirSync](https://go.microsoft.com/fwlink/?linkid=867219).
    
3. Escolha **Download**.
    
4. Quando solicitado, escolha **Executar**.
    
5. Na caixa de diálogo **WinZip Self-Extractor** , na caixa de texto **descompactar pasta** , digite ou procure o local onde você deseja instalar a ferramenta IdFix. Por padrão, o IdFix é instalada no C:\Deployment ferramentas\. 
    
6. Escolha **Descompacte**.
    
## <a name="run-the-idfix-tool"></a>Executar a ferramenta IdFix

Após a instalação do IdFix, execute a ferramenta para procurar problemas no diretório:
  
1. Usando uma conta que tenha acesso de leitura/gravação ao diretório, faça logon no computador no qual você instalou o IdFix.
    
2. No Explorador de Arquivos, vá para o local onde você instalou o IdFix. Se você escolheu a pasta padrão durante a instalação, vá para C:\Ferramentas de Implantação\IdFix.
    
3. Clique duas vezes em **IdFix.exe**. 
    
    ![Escolha o arquivo IdFix.exe.](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. Por padrão, o IdFix usa a regra de multilocatário definida para testar as entradas em seu diretório. Esta é a regra direita definido para a maioria dos clientes do Office 365. No entanto, se você for um cliente ITAR (International tráfego nos Regulamentos de alerta) ou a dedicados do Office 365, você pode configurar o IdFix para usar a regra dedicada definida em vez disso. Se você não tiver certeza sobre qual tipo de cliente que você está, você pode ignorar com segurança esta etapa. Para definir a conjunto de regras para exclusivas, clique no ícone de engrenagem na barra de menus e escolha **exclusivas**.
    
5. Escolha a **consulta**.
    
    ![Escolha consulta no IdFix.](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. Por padrão, o IdFix pesquisa todo o diretório em busca de erros.
    
    Dependendo do tamanho do seu diretório, a execução da consulta pode demorar um pouco. Você pode observar o andamento na parte inferior da janela principal da ferramenta. Se você clicar em **Cancelar**, você precisará reiniciar desde o início.
    
    ![Contagem de consulta e de erro do IdFix.](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. Depois que o IdFix conclui a consulta, caso não haja erros em seu diretório, você pode seguir em frente e sincronizar seu diretório. Caso haja erros em seu diretório, é recomendável que você os corrija antes de sincronizar. Se você quiser informações específicas sobre os tipos de erros e recomendações sobre as melhores maneiras de corrigir cada um deles, consulte os links no final deste tópico. 
    
    Embora não seja obrigatório corrigir os erros antes de sincronizar, é altamente recomendável que você, pelo menos, analise todos os erros retornados pelo IdFix.
    
    Cada erro é exibido em uma linha separada na janela principal da ferramenta. 
    
8. Se você concorda com a alteração sugerida na coluna **UPDATE**, na coluna **ACTION** selecione o que deseja que o IdFix faça para implementar a alteração e, em seguida, clique em **Aplicar**. Quando você clica em **Aplicar**, a ferramenta faz as alterações no diretório.
    
    Você não precisa clique em **Aplicar** após cada atualização. Em vez disso, você pode corrigir vários erros antes de clicar em **Aplicar** e IdFix alterá-los ao mesmo tempo. Você pode classificar os erros por tipo de erro clicando em **erro** na parte superior da coluna que lista os tipos de erro. 
    
    Uma estratégia é corrija todos os erros do mesmo tipo; Por exemplo, corrija todas as duplicatas primeiro e aplicá-las. Em seguida, corrija os erros de formato de caractere e assim por diante. Cada vez que você aplica as alterações, a ferramenta IdFix cria um arquivo de log separado que você pode usar para desfazer suas alterações, caso você cometer um erro. O [log de transação](idfix-transaction-log.md) é armazenado na pasta que você instalou o IdFix no.  _C:\Deployment Tools\IdFix_ por padrão. 
    
    ![Remediando erros no IdFix.](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. Afinal das suas alterações são feitas para o diretório, executar o IdFix novamente para garantir que as correções feitas não introduzem novos erros. Você pode repetir essas etapas quantas vezes precisar. É uma boa ideia passar pelo processo algumas vezes, antes de sincronizar.
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>Quero aperfeiçoar minha pesquisa ou me aprofundar nos erros, o que mais eu posso fazer com o IdFix?

Mais informações detalhadas estão disponíveis com estes tópicos:
  
- [Preparar atributos de diretório para sincronização com o Office 365 usando a ferramenta IdFix](prepare-directory-attributes-for-synch-with-idfix.md) . Depois de instalar a ferramenta de salto para este tópico para obter instruções mais detalhadas sobre como executar a ferramenta, erros comuns que você encontrará sugerido correções, exemplos e práticas recomendadas para o que fazer quando você tiver um grande número de erros. 
- [Referência: O IdFix excluídos e suportados objetos e atributos](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Referência: Log de transações do IdFix do Office 365](idfix-transaction-log.md)
    
## <a name="video-training"></a>Treinamento em vídeo

Para obter mais informações, consulte a lição, [instalar e usar a ferramenta IDFix](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), levada a você pelo aprendizado LinkedIn.
  

