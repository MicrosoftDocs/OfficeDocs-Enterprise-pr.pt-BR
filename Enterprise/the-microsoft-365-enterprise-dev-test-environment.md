---
title: Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Resumo: use este Guia de laboratório de teste para criar um ambiente de desenvolvimento/teste que incluir o Office 365 E5, Enterprise Mobility + Security (EMS) E5 e um computador executando o Windows 10 Enterprise.'
ms.openlocfilehash: 03fa8e0a4e8d90fcb834eeb2491d3dd39b67ff05
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "19178643"
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a>Ambiente de desenvolvimento/teste do Microsoft 365 Enterprise

 **Resumo:** use este Guia de laboratório de teste para criar um ambiente de desenvolvimento/teste que incluir o Office 365 E5, Enterprise Mobility + Security (EMS) E5 e um computador executando o Windows 10 Enterprise.
  
Este artigo fornece instruções passo a passo para criar um ambiente de teste simplificado testar os recursos e funcionalidades do [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a>Fase 1: Criar sua assinatura do Office 365 E5

Siga as etapas das Fases 2 e 3 do [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md) para criar um ambiente de desenvolvimento/teste simples do Office 365, como mostrado na Figura 1.
  
**Figura 1: Sua assinatura do Office 365 E5 com as contas de usuário e do locatário do Azure Active Directory (AD)**

![Fase 1 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> A assinatura de avaliação do Office 365 E5 é de 30 dias, que podem ser facilmente estendidos por até 60 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com algumas licenças. 
  
## <a name="phase-2-add-ems"></a>Fase 2: Adicionar o EMS

Nesta fase, inscreva-se para a assinatura de avaliação do EMS E5 e adicione-a à mesma organização de sua assinatura de avaliação do Office 365 E5.
  
Primeiro adicione a assinatura de avaliação do EMS E5 e atribua uma licença EMS à sua conta de administrador global.
  
1. Em uma instância particular do navegador da Internet, entre no Portal do Office 365 com as credenciais da conta de administrador global. Para obter ajuda, consulte [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Clique no bloco de **Administração**.
    
3. Na guia **Centro de Administração do Office** no navegador, no painel de navegação esquerdo, clique em **Cobrança > Comprar serviços**.
    
4. Na página **Comprar serviços**, encontre o item **Enterprise Mobility + Security E5**. Passe o ponteiro do mouse sobre ele e clique em **Iniciar avaliação gratuita**.
    
5. Na página **Confirmar seu pedido**, clique em **Experimentar agora**.
    
6. Na página **Recibo do pedido**, clique em **Continuar**.
    
7. Na guia **Centro de administração do Office 365** do navegador, no painel de navegação esquerdo, clique em **Usuários > Usuários ativos**.
    
8. Clique em sua conta de administrador global e, em seguida, clique em **Editar** para **Licenças de produto**.
    
9. No painel **Licenças de produto**, mude a licença de produto de **Enterprise Mobility + Security E5** para **Ativada**, clique em **Salvar** e clique em **Fechar** duas vezes.
    
> [!NOTE]
> A assinatura de avaliação do Enterprise Mobility + Security E5 dura 90 dias. Para um ambiente de desenvolvimento/teste permanente, crie uma nova assinatura paga com uma pequena quantidade de licenças. 
  
 ***Se você tiver concluído a Fase 3 do*** [ambiente de desenvolvimento/teste do Office 365](office-365-dev-test-environment.md), repita as etapas 8 e 9 do procedimento anterior para todas as suas contas (Usuário 2, Usuário 3, Usuário 4 e Usuário 5).
  
Seu ambiente de desenvolvimento/teste agora tem:
  
- As assinaturas de avaliação do Office 365 Enterprise E5 e do EMS E5 compartilham o mesmo locatário do Azure AD com sua lista de contas de usuário.
- Todas as suas contas de usuário apropriadas (a conta do administrador global ou todas as cinco contas de usuário) estão habilitadas para usar o Office 365 E5 e o EMS E5.
    
A Figura 2 mostra a configuração resultante, que adiciona o EMS.
  
**Figura 2: Adicionar a assinatura de avaliação do EMS**

![Fase 2 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a>Fase 3: Criar um computador com o Windows 10 Enterprise

Nesta fase, crie um computador autônomo executando o Windows 10 Enterprise.
  
### <a name="physical-computer"></a>Computador físico

Obtenha um computador pessoal e instale o Windows 10 Enterprise. Você pode baixar a versão de avaliação do Windows 10 Enterprise [aqui](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine"></a>Máquina virtual

Crie uma máquina virtual usando o hipervisor de sua escolha e instale o Windows 10 Enterprise. Você pode baixar a versão de avaliação do Windows 10 Enterprise [aqui](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine-in-azure"></a>Máquina virtual no Azure

Para criar uma máquina virtual do Windows 10 no Microsoft Azure, ***você deve ter uma assinatura baseada no Visual Studio***, que tem acesso à imagem do Windows 10 Enterprise. Outros tipos de assinatura do Azure, como assinaturas de avaliação e pagas, não têm acesso a esta imagem. Confira as informações mais recentes em [Usar o cliente do Windows no Azure para cenários de desenvolvimento/teste](https://docs.microsoft.com/azure/virtual-machines/windows/client-images).
  
> [!NOTE]
> Os conjuntos de comandos a seguir usam a versão mais recente do Azure PowerShell. Confira [Introdução aos cmdlets do Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Esses conjuntos de comandos montam uma máquina virtual do Windows 10 Enterprise chamada WIN10 e toda a infraestrutura necessária, incluindo um grupo de recursos, uma conta de armazenamento e uma rede virtual. Se você já estiver familiarizado com os serviços de infraestrutura Azure, adapte estas instruções para se ajustar à sua infraestrutura implantada no momento. 
  
Inicie um prompt do Microsoft PowerShell.
  
Entre na sua conta do Azure usando o comando a seguir.
  
```
Login-AzureRMAccount
```

Para obter o nome de sua assinatura, use este comando.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Defina sua assinatura do Azure. Substitua tudo o que está entre aspas, incluindo os caracteres \< e >, pelo nome correto.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

Depois, crie um novo grupo de recursos. Para determinar um nome exclusivo para o grupo de recursos, use este comando para listar os grupos de recursos existentes.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Crie seu novo grupo de recursos com estes comandos. Substitua tudo o que está entre aspas, incluindo os caracteres \< e >, pelos nomes corretos.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Em seguida, crie uma nova rede virtual e uma máquina virtual WIN10 com estes comandos. Quando solicitado, forneça o nome e a senha da conta de administrador local para WIN10 e armazene-os em um local seguro.
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a>Fase 4: Adicionar o computador com Windows 10 no Azure AD

Depois de criar a máquina física ou virtual com Windows 10 Enterprise, entre com uma conta de administrador local.
  
> [!NOTE]
> Conecte uma máquina virtual no Azure usando [estas instruções](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Entre com as credenciais da conta de administrador local. 
  
Em seguida, adicione o computador WIN10 no locatário do Azure AD das suas assinaturas do Office 365 e EMS.
  
1. Na área de trabalho do computador WIN10, clique em **Iniciar > Configurações > Contas > Acessar trabalho ou escola > Conectar**.
    
2. Na caixa de diálogo **Configurar uma conta corporativa ou de estudante**, clique em **Adicionar este dispositivo ao Azure AD**.
    
3. Em **Conta corporativa ou de estudante**, digite o nome da conta do administrador global da sua assinatura do Office 365 e clique em **Avançar**.
    
4. Em **Digitar Senha**, digite a senha da conta de administrador global e clique em **Entrar**.
    
5. Quando solicitado para garantir que esta é sua organização, clique em **Ingressar** e em **Concluído**.
    
6. Feche a janela de configurações.
    
Em seguida, instale o Office 365 ProPlus no computador WIN10.
  
1. Abra o navegador do Microsoft Edge e entre no Portal do Office 365 com as credenciais da conta de administrador global. Para obter ajuda, confira [Onde entrar no Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).
    
2. Na guia **Microsoft Office Home**, clique em **Instalar o Office 2016**.
    
3. Quando solicitado sobre o que fazer, clique em **Executar** e em **Sim** para **Controle de Conta de Usuário**.
    
4. Aguarde até concluir a instalação do Office. Quando você vir **Tudo pronto!**, clique duas vezes em **Fechar**.
    
A Figura 3 mostra o ambiente resultante, que inclui o computador do WIN10 que:

- Ingressou no locatário do Azure AD das suas assinaturas do Office 365 e EMS.
- Registrou um dispositivo do Azure AD no Intune (EMS).
- Instalou o Office 365 ProPlus.
  
**Figura 3: a configuração de final de um ambiente de desenvolvimento/teste do Microsoft 365**

![Fase 4 do ambiente de desenvolvimento/teste do Microsoft 365 Enterprise](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
Agora você está pronto para experimentar os recursos adicionais do [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Próximas etapas

Confira estes artigos adicionais para explorar os recursos do Microsoft 365 Enterprise:
  
- [Adicionar políticas do gerenciamento de aplicativos móveis (MAM)](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Registrar dispositivos iOS e Android](https://technet.microsoft.com/library/mt743077.aspx)
    
- [Configurar e testar o Gerenciamento de Segurança Avançada](https://technet.microsoft.com/library/mt757250.aspx)
    
- [Configurar e testar a Proteção Avançada contra Ameaças](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a>Confira também

- [Documentação do Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/)
- [Implantar o Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [Ambiente de desenvolvimento/teste do One Microsoft Cloud](the-one-microsoft-cloud-dev-test-environment.md)
- [Guias do Laboratório de Teste (TLGs) para adoção de nuvem](cloud-adoption-test-lab-guides-tlgs.md)
