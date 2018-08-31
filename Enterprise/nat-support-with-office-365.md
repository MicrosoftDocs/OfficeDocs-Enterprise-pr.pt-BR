---
title: Suporte NAT com o Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: 'Resumo: fornece detalhes sobre como se aproximar do número de clientes correto que você pode usar por endereço IP na sua organização, usando a Conversão de Endereços de Rede (NAT).'
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539120"
---
# <a name="nat-support-with-office-365"></a>Suporte NAT com o Office 365

 **Resumo:** fornece detalhes sobre como se aproximar do número de clientes correto que você pode usar por endereço IP na sua organização, usando a Conversão de Endereços de Rede (NAT). 
  
Anteriormente, a orientação sugerido que o número máximo de clientes do Exchange que você deve usar para se conectar ao Office 365 por endereço IP era de cerca de 2.000 clientes por porta de rede.
  
## <a name="why-use-nat"></a>Por que usar a NAT?

Usando NAT, milhares de pessoas em uma rede corporativa podem "compartilhar" poucos endereços IP roteáveis publicamente.
  
A maioria das redes corporativas usa o espaço de endereço IP (RFC1918) privado. O espaço de endereço privado é alocado pela IANA (Internet Assigned Numbers Authority) e destinado unicamente para as redes que não roteiam diretamente para e a partir da Internet global.
  
Para fornecer acesso à Internet para dispositivos em um espaço de endereço IP particular, as organizações usam tecnologias de gateway, como firewalls e proxies que fornecem conversão de endereço de rede (NAT) ou serviços (PAT) de conversão de endereço de porta. Esses gateways tornar tráfego internamente dispositivos com a Internet (incluindo o Office 365) parecem ser provenientes de um ou mais endereços IP roteáveis publicamente. Cada conexão de saída de um dispositivo interno é convertido em uma porta TCP de origem diferentes no endereço IP público. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Por que você precisa ter tantas conexões aberta para o Office 365 ao mesmo tempo?

O Outlook  pode abrir oito ou mais conexões (nas situações em que há suplementos, calendários compartilhados, caixas de correio, etc.). Como existe um máximo de 64.000 portas disponíveis em um dispositivo NAT baseado no Windows, pode haver um máximo de 8.000 usuários por trás de um endereço IP antes das portas se esgotarem. Note que se os clientes estiverem usando dispositivos baseados no SO diferente do Windows para NAT, o total de portas disponíveis dependerá de qual dispositivo NAT ou software está sendo usado. Neste caso, o número máximo de portas poderia ser inferior a 64.000. A disponibilidade das portas também é afetada por outros fatores, como o limite do Windows de 4.000 portas para uso próprio, o que reduz o número total de portas disponíveis para 60.000. Pode haver outros aplicativos, como o Internet Explorer, que podem se conectar ao mesmo tempo, requerendo portas adicionais.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Máximo de cálculo de dispositivos suportados em um único endereço IP público com o Office 365

Para determinar o número máximo de dispositivos por trás de um único endereço IP público, você deve monitorar o tráfego de rede para determinar o consumo da porta de pico por cliente. Além disso, um fator de pico deve ser usado para o uso da porta (mínimo de 4). 
  
 **Use a seguinte fórmula para calcular o número de dispositivos suportados por endereço IP:**
  
Dispositivos máximos suportados em um único endereço IP público = (64.000 - portas restritas) / (consumo da porta + fator de pico de pico)
  
 **Por exemplo, se o seguinte for verdadeiro:**
  
- **Portas restritas:** 4.000 para o sistema operacional 
    
- **Consumo da porta de pico:** 6 por dispositivo 
    
- **Fator de pico:** 4 
    
Em seguida, os dispositivos máximos suportados por trás de um único endereço IP público = (64.000 4.000) / (6 + 4) = 6.000
  
Com a versão do pacote, incluído nas atualizações de setembro de 2011 do Microsoft Office Outlook 2007 ou de novembro de 2011 do Microsoft Outlook 2010 ou uma atualização posterior, o número de conexões do Outlook (ambas Office Outlook 2007 com o serviço de hospedagem do Office 365 Pack 2 e o Outlook 2010) para Exchange pode ser, no mínimo, 2. Você precisará fator nos sistemas operacionais diferentes, comportamentos do usuário, e assim por diante para determinar o número mínimo e máximo de portas que sua rede precisarão de no máximo.
  
Se você quiser dar suporte a dispositivos mais atrás de um único endereço IP público, siga as etapas descritas para avaliar o número máximo de dispositivos que podem ser suportados:
  
Monitorar o tráfego de rede para determinar o consumo da porta de pico por cliente. Você deve coletar esses dados:
  
- A partir de vários locais
    
- A partir de vários dispositivos
    
- Em vários momentos
    
Use a fórmula anterior para calcular os usuários máximos por endereço IP que podem ser suportados em seu ambiente.
  
Há vários métodos para distribuindo a carga de cliente em outros endereços IP públicos. Estratégias disponíveis dependem os recursos da solução corporativa gateway. A solução mais simples é segmentar seu espaço de endereço do usuário e "atribuir" estaticamente um número de endereços IP para cada gateway. Outra alternativa que oferecem vários dispositivos de gateway é a capacidade de usar um pool de endereços IP. A vantagem do pool de endereços é que ele é muito mais dinâmico e menos suscetíveis a requerem ajustes à medida que cresce sua base de usuários.
  
## <a name="see-also"></a>Confira também

[Gerenciando pontos de extremidade do Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Pontos de extremidade perguntas Frequentes do Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

