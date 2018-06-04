---
title: Proteger arquivos do SharePoint Online com a Proteção de Informações do Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Resumo: aplique a Proteção de Informações do Azure para proteger arquivos em um site de equipe altamente confidencial do SharePoint Online.'
ms.openlocfilehash: bab799a784cac579c92fb06ea17592d85fd59af2
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2018
ms.locfileid: "19168495"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Proteger arquivos do SharePoint Online com a Proteção de Informações do Azure

 **Resumo:** aplique a Proteção de Informações do Azure para proteger arquivos em um site de equipe altamente confidencial do SharePoint Online.
  
Use as etapas neste artigo para configurar a Proteção de Informações do Azure para fornecer criptografia e permissões para arquivos em um site de equipe altamente confidencial do SharePoint Online. A proteção de criptografia e permissões acompanha um arquivo mesmo quando ele é baixado do site. Para saber mais sobre sites de equipe altamente confidenciais do SharePoint Online, confira [Sites e arquivos seguros do SharePoint Online](secure-sharepoint-online-sites-and-files.md).
  
> [!NOTE]
> Quando a criptografia da Proteção de Informações do Azure é aplicada aos arquivos armazenados no Office 365, o serviço não pode processar o conteúdo desses arquivos. Coautoria, descoberta eletrônica, pesquisa, Delve e outros recursos de colaboração não funcionam. Políticas DLP só funcionam com metadados (incluindo rótulos do Office 365), mas não com o conteúdo desses arquivos (como números de cartão de crédito em arquivos). 
  
Primeiro, use as instruções em [Ativar o Azure RMS com o centro de administração do Office 365 para sua assinatura do Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).
  
Em seguida, configure a Proteção de Informações do Azure com uma nova política com escopo e um sub-rótulo para proteção e permissões do seu site de equipe altamente confidencial do SharePoint Online.
  
1. Entre no Portal do Office 365 com uma conta que tenha a função de Administrador de Segurança ou Administrador da Empresa. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Em uma guia separada do navegador, vá para o Portal do Azure ([https://portal.azure.com](https://portal.azure.com)).
    
3. Se esta é a primeira vez que configura a Proteção de Informações do Azure, confira estas [instruções](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).
    
4. No painel de lista, clique em **Todos os serviços**, digite **informações** e clique em **Proteção de Informações do Azure**.
    
5. Na folha **Proteção de Informações do Azure**, clique em **Políticas no escopo > + Adicionar uma nova política**.
    
6. Digite um nome para a nova política no **Nome da política** e uma descrição em **Descrição**.
    
7. Clique em **Selecionar quais usuários ou grupos obtêm esta política > Usuário/ Grupos**, e selecione o grupo de acesso dos membros do site para o site da equipe do SharePoint Online altamente confidencial. 
    
8. Clique em **Selecionar > OK**.
    
9. Para o rótulo **Altamente Confidencial**, clique nas reticências (...) e, em seguida, clique em **Adicionar um sub-rótulo**.
    
10. Digite um nome para o subrótulo em **Nome** e uma descrição do rótulo em **Descrição**.
    
11. Em **Definir permissões para documentos e emails que contenham este rótulo**, clique em **Proteger**.
    
12. Na seção **Proteção**, clique em **Azure (chave de nuvem)**.
    
13. Na folha **Proteção**, em **Configurações de proteção**, clique em **+ Adicionar permissões**.
    
14. Na folha **Adicionar permissões**, em **Especificar usuários e grupos**, clique em **+ Procurar no diretório**.
    
15. No painel **Usuários e Grupos do AAD**, selecione o grupo de acesso de membros do site para seu site de equipe altamente confidencial do SharePoint Online e clique em **Selecionar**.
    
16. Em **Escolher permissões da predefinição**, desmarque as caixas de seleção **Imprimir**, **Copiar e extrair conteúdo** e **Encaminhar**.
    
17. Clique em **OK** duas vezes.
    
18. Na folha **Sub-rótulo**, clique em **Salvar**.
    
19. Feche a nova folha de política com escopo.
    
20. Na folha **Proteção de Informações do Azure – Políticas com escopo**, clique em **Publicar**.
    
Aqui está a configuração resultante para seu site de equipe altamente confidencial do SharePoint Online.
  
![Rótulo da Proteção de Informações do Azure de um site de equipe isolado do SharePoint Online.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
Agora você está pronto para começar a criar documentos e protegê-los com a Proteção de Informações do Azure e seu novo rótulo.
  
Você deve [Instalar o cliente da Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) em seu dispositivo ou computador baseado no Windows. Você pode criar scripts e automatizar a instalação, ou os usuários podem instalar o cliente manualmente. Confira os seguintes recursos:
  
- [O lado do cliente da Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Instalando o cliente da Proteção de Informações do Azure](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [Página de download para a instalação manual](https://www.microsoft.com/download/details.aspx?id=53018)
    
Depois de instalado, os usuários executam e entram em um aplicativo do Office (como o Microsoft Word) com suas contas do Office 365. A nova barra **Proteção de Informações** permite aos usuários selecionar um novo rótulo. Certifique-se de que os usuários saibam o site da equipe do SharePoint Online e qual rótulo devem usar para proteger os arquivos altamente confidenciais.
  
> [!NOTE]
> Se houver vários sites de equipe do SharePoint Online altamente confidenciais, crie várias políticas de escopo de Proteção de Informações do Azure com sub-rótulos com as configurações acima, com as permissões para cada sub-rótulo definidas para o grupo de acesso de membros do site, de um site específico de equipe do SharePoint Online. 
  
## <a name="see-also"></a>Confira também

[Proteger sites e arquivos do SharePoint Online](secure-sharepoint-online-sites-and-files.md)
  
[Proteger os sites do SharePoint Online em um ambiente de desenvolvimento/teste](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Diretrizes de segurança da Microsoft para campanhas políticas, instituições sem fins lucrativos e outras organizações Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[Adoção da nuvem e de soluções híbridas](cloud-adoption-and-hybrid-solutions.md)




