---
title: 'Windows Server, versão 1803: recursos que foram removidos'
description: Saiba mais sobre os recursos que serão removidos ou preteridos no Windows Server, versão 1803 ou em uma versão futura
ms.prod: windows-server-threshold
ms.mktglfcycl: plan
ms.localizationpriority: medium
ms.sitesec: library
author: lizap
ms.author: elizapo
ms.date: 05/10/2018
ms.openlocfilehash: c80738fe7ceda43a1a73adb0a8b1061bbb24319f
ms.sourcegitcommit: 3743cf691a984e1d140a04d50924a3a0a19c3e5c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2019
ms.locfileid: "63684519"
---
# <a name="features-removed-or-planned-for-replacement-starting-with-windows-server-version-1803"></a>Recursos removidos ou com substituição planejada do Windows Server versão 1803 em diante

> Aplica-se a: Windows Server, versão 1803

Cada versão do Windows Server adiciona novos recursos e funcionalidades; removemos também ocasionalmente, recursos e funcionalidades, geralmente porque adicionamos a melhor opção. Veja os detalhes sobre os recursos e as funcionalidades que foram removidos no Windows Server, versão 1803.   

> [!TIP]
> - Você pode obter acesso antecipado a builds do Windows Server ao ingressar no [Programa Windows Insider](https://insider.windows.com). Essa é uma ótima maneira de testar as alterações de recurso.
> - Tem dúvidas sobre outras versões? Confira as informações sobre o [Windows Server 2016](deprecated-features.md) e o [Windows Server, versão 1709](removed-features-1709.md).

**A lista está sujeita a alteração e pode não incluir todos os recursos ou as funcionalidades afetadas.** 

## <a name="features-we-removed-in-this-release"></a>Recursos que removemos nesta versão

Removemos os seguintes recursos e funcionalidades da imagem do produto instalado no Windows Server, versão 1803. Aplicativos ou código que dependam desses recursos não funcionarão nesta versão, a menos que você use um método alternativo.   

|Recurso    |Em vez disso, você pode usar...|
|-----------|--------------------|
|[Serviço de Replicação de Arquivos](https://support.microsoft.com/en-us/help/4025991/windows-server-version-1709-no-longer-supports-frs)|Os Serviços de Replicação de Arquivos, introduzidos no Windows Server 2003 R2, foram substituídos pela Replicação do DFS. Será preciso [migrar controladores de domínio que usam FRS para Replicação do DFS com SYSVOL](https://blogs.technet.microsoft.com/filecab/2014/06/25/streamlined-migration-of-frs-to-dfsr-sysvol/).|
|HNV (Virtualização de Rede Hyper-V)|A [Virtualização de rede](../networking/sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md) agora está incluída no Windows Server como parte da solução de SDN [(Rede definida pelo software)](../networking/sdn/software-defined-networking.md), que também inclui o controlador de rede, balanceamento de carga de software, roteamento definido pelo usuário e listas de controle de acesso.|

## <a name="features-were-no-longer-developing"></a>Recursos que não desenvolvemos mais

Não desenvolvemos mais ativamente estes recursos e podemos removê-los de uma atualização futura. Alguns recursos foram substituídos por outros recursos ou funcionalidades, enquanto outros agora estão disponíveis de fontes diferentes. 

>[!NOTE]
> Observe que alguns dos recursos e funções descritas abaixo não são incluídos na opção de instalação Server Core, que é fornecida no Windows Server, versão 1803. Eles *estão* presentes no Server com a opção de instalação de Experiência desktop, que lançamos com o Windows Server 2016 e lançaremos novamente no Windows Server 2019.

Se tiver comentários sobre a substituição proposta de qualquer um desses recursos, você poderá usar o [aplicativo Hub de Comentários](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). 

|Recurso ou função    |Em vez disso, você pode usar...|
|-----------|---------------------|
|Digitalização de Negócios, também chamada de DSM (Gerenciamento de Digitalização Distribuída)|A [funcionalidade de Gerenciamento de Digitalização](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759124\(v%3dws.11\)) foi introduzida no Windows Server 2008 R2 e permitiu a verificação segura e o gerenciamento de scanners em uma empresa. Não estamos mais estamos investindo nesse recurso e não existem dispositivos disponíveis que oferecem suporte a ele.|
|Tecnologias de transição de IPv4/6 (6to4, ISATAP e Túneis Diretos)|O 6to4 foi desabilitado por padrão desde o Windows 10, versão 1607 (a Atualização de Aniversário), o ISATAP foi desabilitado por padrão desde o Windows 10, versão 1703 (a Atualização para Criadores) e os Túneis Diretos estão desabilitados por padrão. Use o suporte a IPv6 nativo.|
|[MultiPoint Services](../remote/multipoint-services/multipoint-services.md)|Não estamos mais desenvolvendo a função de MultiPoint Services como parte do Windows Server. Serviços do MultiPoint Connector estão disponíveis por meio do [Recurso sob demanda](https://docs.microsoft.com/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities) para Windows Server e Windows 10. Você pode usar [Serviços de Área de Trabalho Remota](../remote/remote-desktop-services/welcome-to-rds.md), especificamente o Host da Sessão dos Serviços de Área de Trabalho Remota para fornecer conectividade de RDP. |
|[Pacotes de símbolos offline](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-symbols) (MSIs de símbolo de depuração)|Não estamos mais disponibilizando os pacotes de símbolos como um MSI para download. Em vez disso, o [Servidor de símbolos da Microsoft está mudando para ser um armazenamento de símbolos com base no Azure](https://blogs.msdn.microsoft.com/windbg/2017/10/18/update-on-microsofts-symbol-server/). Se você precisar de símbolos do Windows, conecte-se ao Servidor de símbolos da Microsoft para armazenar em cache local os símbolos ou usar um arquivo de manifesto com SymChk.exe em um computador com acesso à Internet.|
|[Agente de Conexão de Área de Trabalho Remota e Host de Virtualização de Área de Trabalho Remota](../remote/remote-desktop-services/desktop-hosting-service.md) em uma instalação Server Core|A maioria das implantações de Serviços de Área de Trabalho Remota tem essas funções colocalizadas com o RDSH (Host da Sessão da Área de Trabalho Remota), que requer um servidor com Experiência desktop; para ser consistente com RDSH. Estamos alterando essas funções para também exigirem o servidor com Experiência desktop. Não estamos mais desenvolvendo essas funções de RDS para uso em uma [instalação Server Core](../administration/server-core/what-is-server-core.md). Se você precisa [implantar essas funções como parte da sua infraestrutura de Área de Trabalho Remota](../remote/remote-desktop-services/rds-deploy-infrastructure.md), pode [instalá-las no Windows Server 2016 com Experiência desktop](getting-started-with-server-with-desktop-experience.md). <br/><br/>Essas funções também são incluídas na opção de instalação da Experiência desktop do Windows Server 2019. Você pode testá-las no [build do Participante do Programa Windows Insider do Windows Server 2019](https://docs.microsoft.com/windows-insider/at-work/): apenas certifique-se de escolher a imagem de LTSC. |
|[RemoteFX vGPU](../remote/remote-desktop-services/rds-remotefx-vgpu.md)|Estamos desenvolvendo novas opções de aceleração de elementos gráficos para ambientes virtualizados. Você também pode usar a [DDA (Atribuição de Dispositivos Discretos)](../virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment.md) como alternativa.|
|[Políticas de restrição de software](../identity/software-restriction-policies/software-restriction-policies.md) na Política de Grupo|Em vez de usar as Políticas de restrição de software pela Política de Grupo, você pode usar o [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/applocker/applocker-overview) ou o [Controle de Aplicativos do Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control) para controlar quais aplicativos os usuários podem acessar e qual código pode ser executado no kernel.|
|Espaços de Armazenamento em uma configuração compartilhada usando uma malha de SAS|Em vez disso, implante [Espaços de Armazenamento Diretos](../storage/storage-spaces/storage-spaces-direct-overview.md). Os Espaços de Armazenamento Direto dão suporte ao uso de compartimentos de SAS certificados para HLK, mas em uma configuração não compartilhada, como descrito nos [requisitos de hardware de Espaços de Armazenamento Diretos](../storage/storage-spaces/storage-spaces-direct-hardware-requirements.md).|
|Experiência do Windows Server Essentials|Não estamos mais desenvolvendo a função de experiência Essentials para o Windows Server Standard ou SKUs do Windows Server Datacenter. Se precisar de uma solução de servidor fácil de usar para empresas de pequeno a médio porte, confira a nossa nova solução [Microsoft 365 para empresas](https://www.microsoft.com/microsoft-365/business) ou use o [Windows Server 2016 Essentials](https://docs.microsoft.com/windows-server-essentials/get-started/get-started).|

