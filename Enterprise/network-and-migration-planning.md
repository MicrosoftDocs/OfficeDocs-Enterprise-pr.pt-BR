---
title: Planejamento de migração e rede para o Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contém links para informações sobre o planejamento de rede e teste e migração para o Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223053"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planejamento de migração e rede para o Office 365

Este artigo contém links para informações sobre planejamento e teste de rede e migração para o Office 365.
  
Antes de implantar pela primeira vez ou migrar para o Office 365, você pode usar as informações nestes tópicos para estimar a largura de banda necessária e, então, testar e verificar se você possui largura de banda suficiente para implantar ou migrar para o Office 365.

||
|:-----|
| Este artigo faz parte do [planejamento de rede e ajuste de desempenho para o Office 365](https://aka.ms/tune).|

|||
|:-----|:-----|
|![Consulte Microsoft Cloud Networking para pôster arquitetos da empresa](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Para conhecer as etapas otimizar sua rede para o Office 365 e outras plataformas de nuvem da Microsoft e serviços, consulte o cartaz de [Rede da nuvem com a Microsoft para arquitetos da empresa](https://aka.ms/cloudarchnetworking) . |
   
## <a name="estimate-network-bandwidth-requirements"></a>Estimar os requisitos de largura de banda de rede
<a name="EstimateBandwidthRequirements"> </a>

Usando o Office 365 pode aumentar a utilização de circuito de internet da sua organização. É importante determinar se a largura de banda disponível no momento é suficiente para lidar com o aumento estimado depois que o Office 365 é totalmente implantado, deixando pelo menos de 20% capacidade para lidar com mais visitados de dias.
  
Para estimar a largura de banda, siga estas etapas:
  
1. Avalie o número de clientes que usarão cada saída da Internet. Permitir que nossa rede multi-terabit manipular o máximo possível da conexão possível. 
    
2. Determine quais serviços do Office 365 e recursos estarão disponíveis para clientes usarem. Além disso, você provavelmente terá grupos de pessoas com diferentes serviços ou perfis de uso.
    
3. Medir o uso de rede para um grupo piloto dos clientes. Certifique-se de que os clientes piloto são representativo de diferentes perfis de pessoas na organização, bem como os diferentes locais geográficos. Você pode cross-verificar os resultados em relação a nossas calculadoras antigos [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)e [Skype para negócios](https://go.microsoft.com/fwlink/p/?LinkId=321551) ou o [estudo de caso](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) que realizamos nossa própria rede. 
    
4. Use as medidas do grupo piloto extrapolar necessidades da organização inteira e teste novamente para validar as estimativas antes de fazer alterações em sua rede.
    
## <a name="test-your-existing-network"></a>Testar a sua rede existente
<a name="calculators"> </a>

 **Ferramentas de rede.** Testar e validar sua largura de banda da Internet para determinar as restrições de latência, upload e download. Essas ferramentas ajudarão você a determinar os recursos de rede para a migração, bem como após você totalmente estiver implantado. 
  
- [Analisador de mensagem do Microsoft](https://technet.microsoft.com/library/jj649776.aspx): analisador de mensagem é uma ferramenta eficaz para solucionar possíveis problemas de rede. Analisador de mensagem captura, exibe e analisa o tráfego de mensagens baseada no protocolo e mensagens do sistema. Analisador de mensagem também permite importar, agregar e analisar dados de arquivos de log e rastreamento.
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): testa a conectividade em seu ambiente Exchange Online.
    
- Use o [Assistente de recuperação para o Office 365 e de suporte da Microsoft](https://diagnostics.office.com/#/Download?env=SOC) para corrigir problemas do Outlook e o Office 365. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Best practices for network planning and improving migration performance for Office 365
<a name="BestPractices"> </a>

Aprofundar um pouco nestas práticas recomendadas para obter mais informações sobre como melhorar sua experiência do Office 365.
  
1. Deseja começar a ajudar seus usuários imediatamente? Consulte as [práticas recomendadas para usar o Office 365 em uma rede lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) para obter dicas sobre como usar o Office 365, incluindo o Exchange Online, SharePoint Online e Lync Online, quando sua rede simplesmente não trabalhar de forma. Este artigo vincula o check-out para cargas de conteúdo no TechNet e Support.office.com para otimizar sua experiência do Office 365 e inclui informações sobre fácil maneiras para personalizar suas páginas da web e como definir as configurações do Internet Explorer para a melhor experiência do Office 365. 
    
2. Leia os [Princípios de conectividade de rede do Office 365](https://aka.ms/o365networkingprinciples) para entender os princípios de conectividade para gerenciar o tráfego do Office 365 de forma segura e Obtendo o melhor desempenho possível. Este artigo ajudará você a entender as orientações mais recentes para otimizar com segurança de conectividade de rede do Office 365. 
    
3. Melhorar o desempenho de migração de email ao gerenciar cuidadosamente o agendamento de atualizações do Windows. Você pode atualizar os computadores cliente em lotes e certifique-se de que todos os computadores clientes sejam atualizados antes de migrar para o Office 365 para regular o uso da largura de banda de rede. Para obter mais informações, consulte [atualizar manualmente e configurar áreas de trabalho para o Office 365 para obter as atualizações mais recentes](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Tráfego de rede do Office 365 funciona melhor quando ele tem tratado como um serviço de Internet confiável e permitido para ignorar grande parte da filtragem tradicionais e verificação que algumas organizações colocar em tráfego de rede aos serviços de Internet não confiáveis. Isso geralmente inclui a remoção de saída de processamento, como a autenticação do usuário de proxy e inspeção de pacotes, bem como garantir a saída local para a Internet com a conversão de endereços de rede (NAT) adequadas e a capacidade de largura de banda suficiente para lidar com o aumento solicitações de rede. Consulte [Gerenciando o Office 365 pontos de extremidade](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)para obter orientação adicional sobre como configurar sua rede para lidar com o Office 365 como um serviço de Internet confiável em sua rede.
    
1. Verifique se os [pontos de extremidade de gerenciamento do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). O tráfego adicional, indo para o Office 365 resulta em um aumento de conexões de saída de proxy, bem como um aumento no tráfego seguro sobre TLS/SSL.
    
2. Se seu proxies de saída requerem autenticação de usuário que você pode enfrentar conectividade lenta ou uma perda de funcionalidade. Ignorar o requisito de autenticação para os domínios do Office 365 pode reduzir essa sobrecarga.
    
3. Se você possui um grande número de caixas de correio e calendários compartilhados, talvez você veja um aumento no número de conexões do Outlook para o Exchange. Por exemplo, o cliente do Outlook pode abrir até duas conexões adicionais para cada calendário compartilhado em uso. Neste caso, verifique se o proxy de saída pode lidar com as conexões ou ignorar o proxy para conexões com o Office 365 para o Outlook.
    
4. Determine o número máximo de dispositivos suportados para um endereço IP público e como balancear a carga entre vários endereços IP. Para obter mais informações, consulte [suporte a NAT com o Office 365](nat-support-with-office-365.md).
    
5. Se você estiver inspecionando conexões de saída de computadores em sua rede, ignorar essa filtragem para os domínios do Office 365 melhorará conectividade e desempenho. Além disso, ignorar inspeção de saída com frequência elimina a necessidade de uma única saída de Internet e habilita o local de saída da Internet para solicitações de rede de destino do Office 365.
    
6. Alguns clientes encontrar as configurações de rede interna podem afetar o desempenho. Configurações como o tamanho de unidade (MTU) máxima da transmissão, negociação automática ou a detecção automática de rede e rotas abaixo do ideal para a Internet são locais comuns para procurar.
    
## <a name="network-planning-reference-for-office-365"></a>Referência de planejamento de rede para o Office 365
<a name="NetReference"> </a>

Estes tópicos contêm informações detalhadas de referência de rede do Office 365.
  
- [Gerenciando pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Conectividade de cliente](client-connectivity.md)
    
- [Redes de distribuição de conteúdo](content-delivery-networks.md)
    
- [Registros de Domain Name System externos para o Office 365](external-domain-name-system-records.md)
    
- [Suporte a IPv6 nos serviços do Office 365](ipv6-support.md)
    
- [Princípios de conectividade de rede do Office 365](https://aka.ms/o365networkingprinciples)
    
- [Microsoft Virtual Academy: Gerenciamento de desempenho Office 365](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [Rede de vídeo do Office 365 frequentemente perguntas Frequentes](office-365-video-networking-faq.md)
    
- [Planejar dispositivos de rede que se conectam aos serviços do Office 365](plan-for-network-devices.md)
    
- [Supervisores de implantação para serviços do Office 365](deployment-advisors-for-office-365.md)
    

