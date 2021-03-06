---
title: Por que as estações de trabalho de acesso privilegiado podem ajudar a proteger sua organização
description: Como a PAW pode aumentar a postura de segurança da sua organização
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 93589778-3907-4410-8ed5-e7b6db406513
ms.date: 03/13/2019
ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: mas
ms.openlocfilehash: 9ac591d65fb84f3c0a8bbd33ca71c93daf892ced
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280725"
---
# <a name="privileged-access-workstations"></a>Estações de trabalho com acesso privilegiado

>Aplica-se a: Windows Server

As PAWs (Privileged Access Workstations, Estações de Trabalho com Acesso Privilegiado) fornecem um sistema operacional dedicado para tarefas confidenciais, que é protegido contra ataques da Internet e vetores de ameaça. Separar essas tarefas confidenciais e contas do diário usar estações de trabalho e dispositivos fornece uma ótima proteção contra ataques de phishing, aplicativo e vulnerabilidades do SO, vários ataques de representação e ataques de roubo de credenciais, como o pressionamento de tecla registro em log, [Pass-the-Hash](https://aka.ms/pth)e Pass-The-Ticket.

## <a name="what-is-a-privileged-access-workstation"></a>O que é uma estação de trabalho de acesso privilegiado?

Em termos simples, uma PAW é uma estação de trabalho robusta e bloqueada, projetada para fornecer garantias de alta segurança para contas e tarefas confidenciais.  Recomenda-se as PAWs para a administração de sistemas de identidade, serviços de nuvem, malha de nuvem privada e funções corporativas confidenciais.

> [!NOTE]
> A arquitetura da PAW não exige um mapeamento 1:1 de contas para as estações de trabalho, embora seja uma configuração comum. A PAW cria um ambiente de estação de trabalho confiável que pode ser usado por uma ou mais contas.

Para fornecer a segurança máxima, as PAWs devem sempre executar o sistema operacional mais recente e mais seguro disponível: A Microsoft recomenda expressamente o Windows 10 Enterprise, que inclui vários recursos de segurança adicionais não disponíveis em outras edições (especificamente, [Credential Guard](https://technet.microsoft.com/library/mt483740%28v=vs.85%29.aspx) e [Device Guard](https://technet.microsoft.com/library/dn986865(v=vs.85).aspx)).

> [!NOTE]
> As organizações sem acesso ao Windows 10 Enterprise podem usar o Windows 10 Pro, que inclui várias tecnologias de base essenciais para as PAWs, incluindo a Inicialização Confiável, o BitLocker e a Área de Trabalho Remota.  Clientes da área de educação podem usar o Windows 10 Education.  O Windows 10 Home não deve ser usado para uma PAW.
>
> Para uma comparação entre as diferentes edições do Windows 10, leia [este artigo](https://www.microsoft.com/en-us/WindowsForBusiness/Compare).

Os controles de segurança da PAW concentram-se na atenuação de riscos da alta probabilidade de comprometimento e de alto impacto. Isso inclui a redução de ataques no ambiente e os riscos que podem diminuir a eficácia dos controles da PAW ao longo do tempo:

* **Ataques da Internet**: a maioria dos ataques são provenientes direta ou indiretamente de fontes na Internet e usa a Internet para transferência de dados e comando e controle (C2). Isolar a PAW da Internet aberta é essencial para garantir que não seja comprometida.
* **Risco de uso**: se for muito difícil usar uma PAW para tarefas diárias, os administradores serão motivados a criar soluções para facilitar seu trabalho. Frequentemente, essas soluções alternativas deixam as contas e a estação de trabalho administrativas vulneráveis a riscos consideráveis de segurança, portanto é fundamental envolver e capacitar os usuários da PAW para atenuar esses problemas de uso com segurança. Isso pode ser feito escutando os comentários, instalando ferramentas e scripts necessários para realizar seus trabalhos e garantir que todo o pessoal administrativo estejam cientes por que eles precisam usar uma PAW, que é uma PAW é e como usá-lo corretamente e com êxito.
* **Riscos de ambiente**: como muitos computadores e contas do ambiente estão expostos ao risco da Internet, direta ou indiretamente, uma PAW deve ser protegida contra ataques de ativos comprometidos no ambiente de produção. Isso exige a minimização do uso de contas que têm acesso às PAWs para proteger e monitorar essas estações de trabalho especializadas e ferramentas de gerenciamento.
* **Adulteração da cadeia de suprimentos**: embora seja impossível remover todos os riscos possíveis de adulteração da cadeia de suprimentos de hardware e software, algumas ações importantes podem mitigar os vetores de ataque críticos que estão prontamente disponíveis para os invasores. Isso inclui a validação da integridade de todas as mídias de instalação ([princípio da origem limpa](https://aka.ms/cleansource)) e o uso de um fornecedor confiável e respeitável de hardware e software.
* **Ataques físicos**: como as PAWs podem ser fisicamente móveis e podem ser usadas fora das instalações físicas seguras, devem ser protegidas contra ataques que utilizam o acesso físico não autorizado ao computador.

> [!NOTE]
> Uma PAW não protegerá um ambiente de um adversário que já obteve acesso administrativo em uma Floresta do Active Directory.
> Como muitas implementações existentes dos Active Directory Domain Services já estão em operação há anos sob o risco de roubo de credenciais, as organizações devem presumir a violação e considerar a possibilidade de que exista um comprometimento despercebido de credenciais do administrador corporativo ou de domínio. Uma organização que suspeita do comprometimento do domínio deve considerar o uso de serviços profissionais de resposta a incidentes.
>
> Para saber mais sobre diretrizes de resposta e recuperação, consulte as seções "Responder a atividades suspeitas" e "Recuperar-se de uma violação" em [Atenuar a Passagem de Hash e outros roubos de credenciais](https://aka.ms/pth), versão 2.
>
> Visite os [serviços de Recuperação e Resposta a incidentes da Microsoft](https://www.microsoft.com/en-us/microsoftservices/campaigns/cybersecurity-protection.aspx) para saber mais.

### <a name="paw-hardware-profiles"></a>Perfis de hardware PAW

A equipe administrativa também é usuários padrão – eles precisam de uma PAW, bem como uma estação de trabalho do usuário padrão para verificar email, navegar na web e acessar corporativos de linha de aplicativos de negócios.  É essencial para o sucesso de qualquer implantação de PAW garantir que os administradores possam permanecer produtivos e seguros.  Uma solução segura que limita drasticamente a produtividade será abandonada pelos usuários em detrimento de uma que aprimora a produtividade (mesmo que isso seja feito de uma maneira insegura).

Para equilibrar a necessidade de segurança com a necessidade de produtividade, a Microsoft recomenda o uso de um destes perfis de hardware de PAW:

* **Hardware dedicado** -separe dispositivos dedicados para tarefas de usuário versus tarefas administrativas.
* **Uso simultâneo**: um único dispositivo que pode executar tarefas administrativas e tarefas do usuário simultaneamente, tirando proveito da virtualização do sistema operacional ou da apresentação.

As organizações podem usar apenas um perfil ou ambos. Não há preocupações quanto à interoperabilidade entre os perfis de hardware, e as organizações têm a flexibilidade de combinar o perfil de hardware com a necessidade específica e a situação de um determinado administrador.

> [!NOTE]
> É essencial que, em todos esses cenários, a equipe administrativa receba uma conta de usuário padrão que é separada de contas administrativas designadas. As contas administrativas devem ser usadas apenas no sistema operacional administrativo da PAW.

Esta tabela resume as vantagens e desvantagens relativas de cada perfil de hardware da perspectiva de facilidade de uso operacional e produtividade e segurança.  As duas abordagens de hardware fornecem uma segurança sólida para contas administrativas contra roubo de credenciais e reutilização.

|**Cenário**|**Vantagens**|**Desvantagens**|
|--------|---------|-----------|
|Hardware dedicado|-   Sinal forte para a confidencialidade das tarefas<br />-   Separação de segurança mais sólida|-   Espaço em disco adicional<br />-   Peso adicional (para trabalho remoto)<br />-   Custo de hardware|
|Uso simultâneo|-   Custo de hardware menor<br />-   Experiência de dispositivo único|-   Compartilhamento de teclado/mouse único cria o risco de erros/riscos acidentais|

Este guia contém instruções detalhadas para a configuração da PAW para a abordagem de hardware dedicado. Se houver requisitos de uso simultâneo dos perfis de hardware, você poderá adaptar por conta própria as instruções com base neste guia ou contratar uma organização de serviços profissionais, como a Microsoft, para auxiliar nessa tarefa.

#### <a name="dedicated-hardware"></a>Hardware dedicado

Nesse cenário, uma PAW é usada para a administração, e é completamente separada do PC usado para atividades diárias, como email, edição de documentos e trabalho de desenvolvimento. Todos os aplicativos e ferramentas de administração são instalados na PAW, e todos os aplicativos de produtividade são instalados na estação de trabalho de usuário padrão. As instruções passo a passo deste guia têm base nesse perfil de hardware.

#### <a name="simultaneous-use---adding-a-local-user-vm"></a>Uso simultâneo: adicionar uma VM de usuário local

Neste cenário de uso simultâneo, um único PC é usado para tarefas de administração e atividades diárias, como email, edição de documentos e trabalho de desenvolvimento. Nessa configuração, o sistema operacional do usuário fica disponível enquanto estiver desconectado (para edição de documentos e trabalho em emails armazenados localmente em cache), mas exige processos de suporte e de hardware que podem acomodar esse estado desconectado.

![Diagrama que mostra que, neste cenário de uso simultâneo, um único PC é usado para tarefas de administração e atividades diárias, como email, edição de documentos e trabalho de desenvolvimento](../media/privileged-access-workstations/PAWFig10.JPG)

O hardware físico executa dois sistemas operacionais localmente:

* **Sistema operacional de administração**: o host físico executa o Windows 10 no host da PAW para Tarefas administrativas
* **Sistema operacional do usuário**: uma máquina virtual Hyper-V do cliente do Windows 10 executa uma imagem corporativa

Com o Windows 10 Hyper-V, uma máquina virtual do convidado (também executando o Windows 10) pode ter uma experiência de usuário, incluindo som, vídeo e aplicativos de comunicação da Internet, como o Skype for Business.

Nessa configuração, o trabalho diário que não exige privilégios administrativos é realizado na máquina virtual de SO do usuário que possui uma imagem corporativa regular do Windows 10 e não está sujeita às restrições aplicadas ao host da PAW. Todo o trabalho administrativo é feito no sistema operacional do administrador.

Para configurar isso, siga as instruções neste guia para o host da PAW, adicione recursos do Hyper-V do cliente, crie uma VM de usuário e instale uma imagem corporativa do Windows 10 na VM do usuário.

Leia o artigo [Cliente Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/index) para saber mais sobre esse recurso. Observe que o sistema operacional em máquinas virtuais de convidado precisará ser licenciado por [Licenciamento de produtos da Microsoft](https://www.microsoft.com/en-us/Licensing/product-licensing/products.aspx), também descrito [aqui](https://download.microsoft.com/download/9/8/D/98D6A56C-4D79-40F4-8462-DA3ECBA2DC2C/Licensing_Windows_Desktop_OS_for_Virtual_Machines.pdf).

#### <a name="simultaneous-use---adding-remoteapp-rdp-or-a-vdi"></a>Uso simultâneo: Adicionar RemoteApp, RDP ou uma VDI

Neste cenário de uso simultâneo, um único PC é usado para tarefas de administração e atividades diárias, como email, edição de documentos e trabalho de desenvolvimento. Nessa configuração, os sistemas operacionais de usuário são implantados e gerenciados centralmente (na nuvem ou em seu datacenter), mas não ficarão disponíveis enquanto estiverem desconectados.

![Figura que mostra que, neste cenário de uso simultâneo, um único PC é usado para tarefas de administração e atividades diárias, como email, edição de documentos e trabalho de desenvolvimento](../media/privileged-access-workstations/PAWFig11.JPG)

O hardware físico executa um único sistema operacional de PAW localmente para tarefas administrativas e entra em contato com um serviço de área de trabalho remota da Microsoft ou de terceiros para aplicativos de usuário, como email, edição de documento e aplicativos de linha de negócios.

Nessa configuração, o trabalho diário que não exige privilégios administrativos é realizado nos SOs e aplicativos remotos, que não estão sujeitos às restrições aplicadas ao host da PAW. Todo o trabalho administrativo é feito no sistema operacional do administrador.

Para configurar isso, siga as instruções neste guia para o host da PAW, permita a conectividade de rede com os serviços de Área de Trabalho Remota e, em seguida, adicione atalhos à área de trabalho do usuário na PAW a fim de acessar os aplicativos. Os serviços de área de trabalho remota podem ser hospedados de várias maneiras, incluindo:

* Um serviço existente de Área de Trabalho Remota ou VDI (local ou na nuvem)
* Um novo serviço instalado localmente ou na nuvem
* RemoteApp do Azure usando modelos pré-configurados do Office 365 ou suas próprias imagens de instalação

Para saber mais sobre o RemoteApp do Azure, visite [esta página](https://www.remoteapp.windowsazure.com).

## <a name="how-microsoft-is-using-administrative-workstations"></a>Como a Microsoft está usando estações de trabalho administrativas

A Microsoft usa a abordagem de arquitetura de PAW internamente, em nossos sistemas, e com nossos clientes. A Microsoft usa as estações de trabalho administrativas internamente em várias atividades, incluindo a administração da infraestrutura do Microsoft IT, desenvolvimento de infraestrutura de malha de nuvem do Microsoft e operações e outros ativos de alto valor.

Este guia é fundamentado diretamente na arquitetura de referência de PAW (Estação de Trabalho com Acesso Privilegiado) implantada por nossas equipes de serviços profissionais de segurança cibernética para proteger os clientes contra ataques de segurança cibernética. As estações de trabalho administrativas também são um elemento essencial da proteção mais forte para tarefas de administração de domínio, a arquitetura de referência de floresta administrativa do ESAE (Ambiente administrativo de segurança avançada).

Para obter mais detalhes sobre a floresta administrativa de ESAE, consulte o *abordagem de Design de floresta administrativa ESAE* seção [protegendo Material de referência de acesso privilegiado](../securing-privileged-access/securing-privileged-access-reference-material.md#esae-administrative-forest-design-approach).

## <a name="architecture-overview"></a>Visão geral da arquitetura

O diagrama a seguir ilustra um "canal" separado para administração (uma tarefa altamente confidencial), que é criado pela manutenção de contas administrativas e estações de trabalho dedicadas e separadas.

![O diagrama a seguir ilustra um "canal" separado para administração (uma tarefa altamente confidencial) criado pela manutenção de contas administrativas e estações de trabalho dedicadas e separadas](../media/privileged-access-workstations/PAWFig1.JPG)

Essa abordagem de arquitetura amplia as proteções encontradas nos recursos [Credential Guard](https://technet.microsoft.com/library/mt483740%28v=vs.85%29.aspx) e [Device Guard](https://technet.microsoft.com/library/dn986865(v=vs.85).aspx) do Windows 10 e vai além dessas proteções para contas e tarefas confidenciais.

Essa metodologia é apropriada para contas que têm acesso a ativos de alto valor:

* **Privilégios administrativos** -as PAWs fornecem maior segurança para alto impacto funções administrativas de TI e tarefas. Essa arquitetura pode ser aplicada à administração de vários tipos de sistemas, incluindo Domínios e Florestas do Active Directory, locatários do Microsoft Azure Active Directory, locatários do Office 365, PCN (Redes de controle de processo), sistemas SCADA (Aquisição de dados e controle de supervisão), caixas eletrônicos e dispositivos para pontos de venda.
* **Os operadores de informações de confidencialidade alta** -a abordagem usada em uma PAW também pode fornecer proteção para tarefas do trabalhador de informações altamente confidenciais e a equipe de como as que envolvem atividades de fusão e aquisição pré-lançamento, pré-lançamento relatórios financeiros, presença organizacional mídias sociais, comunicações executivas, segredos de comerciais executivas, pesquisa confidencial ou outros dados confidenciais ou proprietários. Este guia não discute detalhadamente as configurações desses cenários de trabalhador de informações, nem inclui esse cenário nas instruções técnicas.

    > [!NOTE]
    > A TI da Microsoft usa PAWs (chamadas internamente de "estações de trabalho de administração seguras" ou SAWs) para gerenciar o acesso seguro aos sistemas internos de alto valor dentro da Microsoft. Este guia oferece detalhes adicionais sobre o uso de PAW na Microsoft na seção "Como a Microsoft usa as estações de trabalho de administração". Para saber mais sobre essa abordagem de ambiente com ativos de alto valor, consulte o artigo [Proteger ativos de alto valor com estações de trabalho de administração seguras](https://msdn.microsoft.com/library/mt186538.aspx).

Este documento descreverá o motivo de essa prática ser recomendada para proteger contas privilegiadas de alto impacto, a aparência dessas soluções de PAW para proteção de privilégios administrativos e como implantar rapidamente uma solução de PAW para administração de domínio e serviços de nuvem.

Este documento fornece orientações detalhadas para implementar várias configurações de PAW e inclui instruções detalhadas de implementação para ajudar com a proteção de suas contas de alto impacto comuns:

* [**Fase 1: implantação imediata para administradores do Active Directory** ](#phase-1-immediate-deployment-for-active-directory-administrators) isso fornece rapidamente uma PAW que pode proteger no local de funções de administração de domínio e floresta
* [**Fase 2: extensão da PAW a todos os administradores** ](#phase-2-extend-paw-to-all-administrators) habilita a proteção para os administradores de serviços de nuvem, como o Office 365 e do Azure, servidores corporativos, aplicativos corporativos e estações de trabalho
* [**Fase 3: segurança avançada de PAW** ](#phase-3-extend-and-enhance-protection) este tópico aborda considerações sobre segurança da PAW e proteções adicionais

### <a name="why-dedicated-workstations"></a>Por que dedicado estações de trabalho?

O ambiente atual de ameaças para as organizações está repleto de phishing sofisticado e outros ataques da Internet que geram riscos contínuos de comprometimento da segurança para contas e estações de trabalho expostas na Internet.

Esse ambiente de ameaças exige que as organizações adotem uma postura de segurança "supor uma violação" ao criar proteções para ativos de alto valor, como contas administrativas e ativos corporativos confidenciais. Esses ativos de alto valor precisam ser protegidos contra ameaças diretas da Internet e contra ataques vindos de outras estações de trabalho, servidores e dispositivos no ambiente.

![Figura que mostra o risco aos ativos gerenciados se um invasor assumir o controle de uma estação de trabalho de usuário na qual credenciais confidenciais são usadas](../media/privileged-access-workstations/PAWFig2.JPG)

Essa figura retrata o risco aos ativos gerenciados se um invasor assumir o controle de uma estação de trabalho do usuário na qual credenciais confidenciais são usadas.

Um invasor no controle de um sistema operacional conta com várias maneiras de obter acesso ilícito a todas as atividades na estação de trabalho e de representar a conta legítima. Diversas técnicas de ataques conhecidas e desconhecidas podem ser usadas para obter esse nível de acesso. O volume e a sofisticação cada vez maiores dos ciberataques exigiram a extensão desse conceito de separação a fim de desligar completamente os sistemas operacionais de clientes das contas confidenciais. Para saber mais sobre esses tipos de ataques, visite o [Site de passagem de hash](https://www.microsoft.com/pth) e consulte os white papers e vídeos informativos, além de mais referências.

A abordagem PAW é uma extensão da prática recomendada bem estabelecida de uso de contas de usuário e de administrador separadas para a equipe administrativa. Esta prática usa uma conta administrativa atribuída individualmente e completamente separada da conta padrão do usuário. A PAW amplia essa prática de separação de conta, fornecendo uma estação de trabalho confiável para essas contas confidenciais.

Esta orientação sobre PAW tem como objetivo ajudá-lo a implementar essa funcionalidade a fim de proteger contas de alto valor, como administradores de TI altamente privilegiados e contas corporativas de alta confidencialidade. O guia ajudará você a:

* Restringir a exposição de credenciais somente aos hosts confiáveis
* Fornecer uma estação de trabalho altamente segura a administradores, para que eles possam executar com facilidade as tarefas administrativas.

Restringir as contas confidenciais apenas às PAWs seguras é uma proteção bem simples para essas contas, pois elas são altamente úteis para os administradores e dificultam muito a vitória de um adversário.

### <a name="alternate-approaches"></a>Abordagens alternativas

Esta seção compara a segurança das abordagens alternativas às PAWs e contém informações sobre como integrar corretamente essas abordagens dentro de uma arquitetura de PAW. todas essas abordagens apresentam riscos consideráveis quando implementadas sozinhas, mas podem agregar valor à implementação da PAW em alguns cenários.

#### <a name="credential-guard-and-windows-hello-for-business"></a>Credential Guard e o Windows Hello para empresas

Apresentado no Windows 10, o [Credential Guard](https://technet.microsoft.com/library/mt483740%28v=vs.85%29.aspx) usa segurança baseada em virtualização e em hardware para atenuar ataques comuns de roubo de credenciais, como Passagem de Hash, protegendo as credenciais derivadas. A chave privada para as credenciais usadas pelo [Windows Hello para empresas](https://aka.ms/passport) pode ser também ser protegidos pelo hardware do Trusted Platform Module (TPM).

São atenuações eficientes, mas as estações de trabalho podem ficar vulneráveis a certos ataques, mesmo se as credenciais são protegidas pelo Credential Guard ou o Windows Hello para empresas. Ataques podem incluir abuso de privilégios e uso de credenciais diretamente de um dispositivo comprometido, reutilização de credenciais roubadas anteriormente antes da habilitação do Credential Guard e abuso de ferramentas de gerenciamento e configurações de aplicativos fracos na estação de trabalho.

A orientação sobre PAW nesta seção inclui o uso de várias dessas tecnologias para contas e tarefas de alta confidencialidade.

#### <a name="administrative-vm"></a>VM administrativa

Uma máquina virtual de administrativa (Admin VM) é um sistema operacional dedicado para tarefas administrativas hospedado em um desktop de usuário padrão. Embora essa abordagem seja semelhante à PAW no fornecimento de um sistema operacional dedicado para tarefas administrativas, tem uma falha fatal: a VM administrativa depende do desktop de usuário padrão para sua segurança.

O diagrama a seguir ilustra a capacidade de os invasores seguirem a cadeia de controle até o objeto de destino de interesse com uma VM de administrador em uma Estação de trabalho de usuário, e isso dificulta a criação de um caminho na configuração inversa.

A arquitetura de PAW não permite a hospedagem de uma VM de administrador em uma estação de trabalho do usuário, mas uma VM de usuário com uma imagem corporativa padrão pode ser hospedada em uma PAW de administrador para fornecer à equipe um único PC para todas as responsabilidades.

![Diagrama da arquitetura de PAW](../media/privileged-access-workstations/PAWFig9.JPG)

#### <a name="shielded-vm-based-paws"></a>Blindado PAWs baseada em VM

Uma variante segura do modelo administrativo de VM é usar [máquinas virtuais blindadas](../../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms.md) para hospedar um ou mais VMs de administração junto com uma VM de usuário.
VMs blindadas são projetadas para executar cargas de trabalho seguras em um ambiente em que usuários potencialmente não confiáveis ou código pode estar em execução na área de trabalho de usuário padrão do computador físico.
Uma VM blindada tem um TPM virtual que permite criptografar seus próprios dados em repouso e vários controles administrativos, como acesso de console básico, PowerShell Direct e a capacidade de depurar a VM estiverem desativados para isolar ainda mais a VM da área de trabalho do usuário padrão e outras VMs.
As chaves para uma VM blindada são armazenadas em um servidor de gerenciamento de chaves confiável, o que exige que o dispositivo físico para atestar a sua identidade e a integridade antes de liberar uma tecla para iniciar a máquina virtual.
Isso garante que as VMs blindadas só podem iniciar nos dispositivos pretendidos e que esses dispositivos estejam em execução de configurações de software conhecido e confiável.

Como as VMs blindadas são isoladas entre si e a área de trabalho do usuário padrão, é aceitável para executar várias VMs blindadas de PAW em um único host, mesmo quando essas VMs administrador gerenciar diferentes camadas.

Consulte a [implantar as PAWs usando uma malha protegida](#deploy-paws-using-a-guarded-fabric) seção abaixo para obter mais informações.

#### <a name="jump-server"></a>Servidor de salto

Arquiteturas administrativas de "Servidor de salto" definem um pequeno número de servidores de console administrativos e restringem seu uso para tarefas administrativas. Isso normalmente tem base em serviços de área de trabalho remota, em uma solução de virtualização de apresentação de terceiros ou em uma tecnologia de VDI (Virtual Desktop Infrastructure).

Essa abordagem é proposta com frequência para reduzir os riscos à administração e fornecer algumas garantias de segurança, mas a abordagem de servidor de salto por si só é vulnerável a certos ataques, pois viola o [princípio de "origem limpa"](../securing-privileged-access/securing-privileged-access-reference-material.md#clean-source-principle). O princípio de origem limpa exige que todas as dependências de segurança sejam tão confiáveis quanto o objeto que está sendo protegido.

![Figura que mostra uma relação de controle simples](../media/privileged-access-workstations/PAWFig3.JPG)

Esta figura mostra uma relação de controle simples. Qualquer pessoa que tem controle de um objeto é uma dependência de segurança desse objeto. Se um adversário puder controlar uma dependência de segurança de um objeto alvo (entidade), ele poderá controlar esse objeto.

A sessão administrativa no servidor de salto depende da integridade do computador local que a acessa. Se esse computador for uma estação de trabalho de usuário sujeita a ataques de phishing e outros vetores de ataque baseados na Internet, a sessão administrativa também estará sujeita a esses riscos.

![Figura que mostra como os invasores podem seguir uma cadeia de controle estabelecida até o objeto de destino de interesse](../media/privileged-access-workstations/PAWFig4.JPG)

A figura acima mostra como os invasores podem seguir uma cadeia de controle estabelecida até o objeto de destino de interesse.

Embora alguns controles avançados de segurança, como a autenticação multifator, possam aumentar a dificuldade de um invasor assumir o controle dessa sessão administrativa a partir da estação de trabalho de usuário, nenhum recurso de segurança pode proteger totalmente contra ataques técnicos quando um invasor tiver acesso administrativo do computador de origem (por exemplo, injetando comandos ilícitos em uma sessão legítima, sequestrando processos legítimos, etc.)

A configuração padrão neste guia sobre PAW instala ferramentas administrativas na PAW, mas também é possível adicionar uma arquitetura de servidor de salto, se for necessário.

![Figura que mostra como a inversão da relação de controle e o acesso a aplicativos de usuário em uma estação de trabalho administrativa não proporcionam ao invasor um caminho até o objeto de destino](../media/privileged-access-workstations/PAWFig5.JPG)

Essa figura mostra como a inversão da relação de controle e o acesso a aplicativos de usuário em uma estação de trabalho administrativa não proporcionam ao invasor um caminho até o objeto de destino. O servidor de salto do usuário ainda está exposto a riscos, portanto os controles de proteção adequados, os controles de investigação e os processos de resposta ainda devem ser aplicados nesse computador voltado para a Internet.

Essa configuração exige que os administradores sigam de perto as práticas operacionais a fim de assegurar que não insiram acidentalmente credenciais de administrador na sessão de usuário em seus desktops.

![Figura que mostra como o acesso a um servidor de salto administrativo de uma PAW não adiciona um caminho do invasor até os ativos administrativos](../media/privileged-access-workstations/PAWFig6.JPG)

Essa figura mostra como o acesso a um servidor de salto administrativo a partir de uma PAW não adiciona um caminho até os recursos administrativos para o invasor. Um servidor de salto com uma PAW permite, neste caso, a consolidação do número de locais para monitoramento da atividade administrativa e a distribuição de ferramentas e aplicativos administrativos. Isso adiciona certa complexidade ao design, mas pode simplificar o monitoramento de segurança e as atualizações de software se uma grande quantidade de contas e estações de trabalho forem usadas em sua implementação da PAW. Seria necessário criar e configurar o servidor de salto com padrões de segurança semelhantes aos da PAW.

#### <a name="privilege-management-solutions"></a>Soluções de gerenciamento de privilégio

As soluções de Gerenciamento de privilégios são aplicativos que fornecem acesso temporário a privilégios discretos ou a contas privilegiadas sob demanda. As soluções de Gerenciamento de privilégios são um componente extremamente valioso em uma estratégia completa de proteção do acesso privilegiado, e fornecem visibilidade e responsabilidade fundamentais das atividades administrativas.

Essas soluções normalmente usam um fluxo de trabalho flexível para conceder acesso, e muitas têm recursos de segurança adicionais, como gerenciamento de senhas de contas de serviço e integração com servidores de salto administrativos. Há muitas soluções no mercado que oferecem recursos de gerenciamento de privilégios. Uma delas é o PAM (gerenciamento de acesso privilegiado) do MIM (Microsoft Identity Manager).

A Microsoft recomenda o uso de uma PAW para acessar soluções de gerenciamento de privilégios. O acesso a essas soluções deve ser concedido somente às PAWs. A Microsoft não recomenda o uso dessas soluções como substituição para uma PAW, pois o acesso de privilégios usando essas soluções em um desktop de usuário potencialmente comprometido viola o princípio da [origem limpa](https://aka.ms/cleansource), conforme ilustrado no diagrama a seguir:

![Diagrama que mostra que a Microsoft não recomenda o uso dessas soluções como substituição para uma PAW, pois o acesso de privilégios usando essas soluções em um desktop de usuário potencialmente comprometido viola o princípio da origem limpa](../media/privileged-access-workstations/PAWFig7.JPG)

O fornecimento de uma PAW para acessar essas soluções permite que você obtenha os benefícios de segurança da PAW e da solução de gerenciamento de privilégios, conforme ilustrado neste diagrama:

![Diagrama que mostra que o fornecimento de uma PAW para acessar essas soluções permite que você obtenha os benefícios de segurança da PAW e da solução de gerenciamento de privilégios](../media/privileged-access-workstations/PAWFig8.JPG)

> [!NOTE]
> Esses sistemas devem ser classificados com a camada mais alta de privilégio que eles gerenciam, e devem ser protegidos nesse nível de segurança ou acima dele. Eles são configurados normalmente para gerenciar soluções e ativos de Camada 0, e devem ser classificados na Camada 0.
> Para obter mais informações sobre o modelo de camadas, consulte [ https://aka.ms/tiermodel ](https://aka.ms/tiermodel) para obter mais informações sobre grupos de camada 0, consulte equivalência de camada 0 na [protegendo Material de referência de acesso privilegiado](../securing-privileged-access/securing-privileged-access-reference-material.md).

Para obter mais informações sobre como implantar o gerenciamento de acesso do Microsoft Identity Manager (privilegiado) de MIM PAM (), consulte [https://aka.ms/mimpamdeploy](https://aka.ms/mimpamdeploy)

## <a name="paw-scenarios"></a>Cenários de PAW

Esta seção contém orientações sobre os cenários nos quais este guia de PAW deve ser aplicado. Em todos os cenários, os administradores devem ser treinados para usar as PAWs apenas para executar o suporte de sistemas remotos. Para incentivar o uso seguro e bem-sucedido, todos os usuários de PAW também devem ser incentivados a fornecer comentários a fim de melhorar a experiência da PAW, e esses comentários devem ser examinados com atenção para proporcionar integração com seu programa de PAW.

Em todos os cenários, talvez seja necessário ampliar a proteção em fases mais avançadas e usar perfis de hardware diferentes para atender aos requisitos de segurança ou uso das funções.

> [!NOTE]
> Esta orientação diferencia explicitamente entre os que precisam de acesso a serviços específicos na internet (como portais administrativos do Azure e Office 365) e "Internet aberta" de todos os hosts e serviços.

Consulte a [página de Modelo de camadas](https://aka.ms/tiermodel) para saber mais sobre as designações de camadas.

|**Cenários**|**Usar PAW?**|**Escopo e considerações de segurança**|
|---------|--------|---------------------|
|Administradores do Active Directory: Camada 0|Sim|Uma PAW criada com orientação de Fase 1 é suficiente para esta função.<br /><br />-   É possível adicionar uma floresta administrativa para fornecer a proteção mais forte para este cenário. Para saber mais sobre a floresta administrativa de ESAE, consulte [Abordagem de design de floresta administrativa de ESAE](../securing-privileged-access/securing-privileged-access-reference-material.md#esae-administrative-forest-design-approach)<br />- Uma PAW pode ser usada para administrar vários domínios ou florestas.<br />-Se os controladores de domínio são hospedados em uma infraestrutura como serviço (IaaS) ou solução de virtualização local, você deve priorizar a implementação das PAWs para os administradores dessas soluções.|
|Serviços de administração de IaaS e PaaS do Azure: Camada 1 ou Camada 0 (consulte Considerações de escopo e design)|Sim|Uma PAW criada usando as diretrizes fornecidas na Fase 2 é suficiente para essa função.<br /><br />-   As PAWs devem ser usadas pelo menos para o Administrador global e o Administrador de cobrança da assinatura. Você também deve usar PAWs para administradores delegados de servidores críticos ou confidenciais.<br />-As pAWs devem ser usadas para gerenciar o sistema operacional e aplicativos que fornecem sincronização de diretório e federação de identidade para serviços de nuvem, como [do Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) e serviços de Federação do Active Directory (ADFS).<br />-   As restrições para a rede de saída devem permitir a conectividade apenas a serviços de nuvem autorizados usando as diretrizes da Fase 2. Não deve haver acesso à Internet aberta a partir das PAWs.<br />-Windows Defender Exploit Guard deve ser configurado na estação de trabalho **Observação:**     Uma assinatura é considerada de camada 0 para uma floresta se os controladores de domínio ou outros hosts de camada 0 estiverem na assinatura. Uma assinatura será de Camada 1 se não houver servidores de Camada 0 hospedados no Azure.|
|Administrador do locatário do Office 365 <br />- Camada 1|Sim|Uma PAW criada usando as diretrizes fornecidas na Fase 2 é suficiente para essa função.<br /><br />-   As PAWs devem ser usadas pelo menos para o Administrador de cobrança da assinatura, o Administrador global, o Administrador do Exchange, o Administrador do SharePoint e funções de Administrador de gerenciamento de usuário. Considere também o uso de PAWs para os administradores delegados de dados altamente críticos ou confidenciais.<br />-Windows Defender Exploit Guard deve ser configurado na estação de trabalho.<br />-   As restrições para a rede de saída devem permitir a conectividade apenas a serviços da Microsoft usando as diretrizes da Fase 2. Não deve haver acesso à Internet aberta a partir das PAWs.|
|Administrador de serviços de nuvem de outros IaaS ou PaaS<br />- Camada 0 ou Camada1 (consulte Considerações de escopo e design)|Sim|Uma PAW criada usando as diretrizes fornecidas na Fase 2 é suficiente para essa função.<br /><br />-   As PAWs devem ser usadas para qualquer função que tenha direitos administrativos sobre VMs hospedadas na nuvem, incluindo a capacidade para instalar agentes, exportar arquivos de disco rígido ou acessar o armazenamento no qual os discos rígidos com sistemas operacionais, dados confidenciais ou dados comerciais críticos são armazenados.<br />-   As restrições para a rede de saída devem permitir a conectividade apenas a serviços da Microsoft usando as diretrizes da Fase 2. Não deve haver acesso à Internet aberta a partir das PAWs.<br />-Windows Defender Exploit Guard deve ser configurado na estação de trabalho. **Observação:** Uma assinatura é a camada 0 para uma floresta se os controladores de domínio ou outros hosts de camada 0 estiverem na assinatura. Uma assinatura será de Camada 1 se não houver servidores de Camada 0 hospedados no Azure.|
|Administradores de virtualização<br />- Camada 0 ou Camada1 (consulte Considerações de escopo e design)|Sim|Uma PAW criada usando as diretrizes fornecidas na Fase 2 é suficiente para essa função.<br /><br />-   As PAWs devem ser usadas para qualquer função que tenha direitos administrativos sobre VMs, incluindo a capacidade para instalar agentes, exportar arquivos de disco rígido virtual ou acessar o armazenamento no qual os discos rígidos com informações de sistemas operacionais convidados, dados confidenciais ou dados comerciais críticos são armazenados. **Observação:** Um sistema de virtualização (e seus administradores) são considerados camada 0 para uma floresta se os controladores de domínio ou outros hosts de camada 0 estiverem na assinatura. Uma assinatura será de Camada 1 se não houver servidores de Camada 0 hospedados no sistema de virtualização.|
|Administradores de manutenção do servidor<br />- Camada 1|Sim|Uma PAW criada usando as diretrizes fornecidas na Fase 2 é suficiente para essa função.<br /><br />-   Uma PAW deverá ser usada para os administradores que atualizam, aplicam patches e solucionam problemas de aplicativos e servidores corporativos executando o servidor Windows, Linux e outros sistemas operacionais.<br />-   Talvez seja necessário adicionar ferramentas de gerenciamento dedicadas às PAWs a fim de lidar com a escala maior desses administradores.|
|Administradores de estação de trabalho do usuário <br />- Camada 2|Sim|Uma PAW criada usando as orientações fornecidas na Fase 2 é suficiente para as funções que têm direitos administrativos em dispositivos de usuário final (como funções de suporte técnico e deskside).<br /><br />-   Talvez seja necessário instalar aplicativos adicionais em PAWs a fim de habilitar o gerenciamento de tíquetes e outras funções de suporte.<br />-Windows Defender Exploit Guard deve ser configurado na estação de trabalho.<br />    Talvez seja necessário adicionar ferramentas de gerenciamento dedicadas às PAWs a fim de lidar com a escala maior desses administradores.|
|Administradores de SQL, SharePoint ou LOB (linha de negócios)<br />- Camada 1|Sim|Uma PAW criada com as orientações da Fase 2 é suficiente para esta função.<br /><br />-   Talvez seja necessário instalar ferramentas de gerenciamento adicionais nas PAWs a fim de permitir que os administradores gerenciem aplicativos sem precisarem se conectar a servidores usando a Área de Trabalho Remota.|
|Usuários que gerenciam presença em redes sociais|Parcialmente|Uma PAW criada usando as diretrizes fornecidas na Fase 2 pode ser usada como ponto de partida para fornecer segurança a essas funções.<br /><br />-   Proteger e gerenciar contas de redes sociais usando o Azure Active Directory (AAD) para compartilhamento, proteção e controle de acesso a contas de redes sociais.<br />    Para saber mais sobre esse recurso, leia [esta postagem de blog](http://blogs.technet.com/b/ad/archive/2015/02/20/azure-ad-automated-password-roll-over-for-facebook-twitter-and-linkedin-now-in-preview.aspx).<br />-   As restrições para a rede de saída devem permitir a conectividade com esses serviços. Isso pode ser feito permitindo que conexões com a Internet aberta (risco de segurança muito maior que elimina muitas garantias da PAW) ou permitindo somente endereços DNS necessários para o serviço (pode ser difícil de obter).|
|Usuários padrão|Não|Embora muitas etapas de proteção possam ser usadas para usuários padrão, a PAW foi criada para isolar contas do acesso à Internet aberta que a maioria dos usuários precisa para funções de trabalho.|
|VDI/Quiosque de convidado|Não|Embora muitas etapas de proteção possam ser usadas para um sistema de quiosque para convidados, a arquitetura de PAW foi projetada para fornecer maior segurança para contas de alta confidencialidade, e não uma segurança maior para contas de confidencialidade inferior.|
|Usuário VIP (executivos, pesquisadores, etc.)|Parcialmente|Uma PAW criada usando as diretrizes fornecidas na fase 2 pode ser usada como um ponto de partida para fornecer segurança para essas funções.<br /><br />-   Esse cenário é semelhante a uma área de trabalho de usuário padrão, mas normalmente tem um perfil de aplicativo menor, mais simples e bem conhecido. Normalmente, esse cenário exige o descobrimento e a proteção de dados, serviços e aplicativos confidenciais (que podem ou não ser instalados em desktops).<br />-   Essas funções geralmente exigem um alto grau de segurança e um grau muito alto de facilidade de uso, o que exige alterações de design a fim de atender às preferências do usuário.|
|Sistemas de controle industriais (por exemplo, SCADA, PCN e DCS)|Parcialmente|Uma PAW criada usando a orientação fornecida na Fase 2 pode ser usada como ponto de partida para fornecer segurança para essas funções, pois a maioria dos consoles ICS (incluindo padrões comuns como SCADA e PCN) não exige a navegação na Internet aberta e a verificação de emails.<br /><br />-Aplicativos usados para controlar máquinas físicas precisaria ser integrados e testados para compatibilidade e protegidos adequadamente.|
|Sistema operacional incorporado|Não|Apesar de muitas etapas de proteção da PAW poderem ser usadas para sistemas operacionais incorporados, uma solução personalizada precisaria ser desenvolvida para a proteção nesse cenário.|

> [!NOTE]
> **Cenários de combinação** Alguns funcionários podem ter responsabilidades administrativas que abrangem vários cenários.
> Nesses casos, as regras de chave para ter em mente são sempre devem ser seguidas as regras de modelo de camada. Consulte a página Modelo de camadas para saber mais.

> [!NOTE]
> **Dimensionando o programa de PAW** como seu programa de PAW aumenta para abranger mais administradores e funções, você precisa continuar assegurando a aderência aos padrões de segurança e usabilidade. Isso pode exigir a atualização das estruturas de seu suporte de TI ou a criação de novas estruturas para resolver desafios específicos da PAW, como o processo de integração, gerenciamento de incidentes, gerenciamento de configuração e coleta de comentários para resolver desafios de uso.  Por exemplo, sua organização decide permitir cenários de home office para administradores, o que exigiria uma mudança de PAWs de desktop para PAWs de laptop, uma mudança que pode precisar de considerações de segurança adicionais.  Outro exemplo comum é a criação ou atualização do treinamento para novos administradores, treinamento que agora deve incluir o conteúdo sobre o uso apropriado de uma PAW (incluindo porque uma PAW é importante e sua definição).  Para obter mais considerações que devem ser abordadas ao dimensionar seu programa de PAW, consulte a Fase 2 das instruções.

Este guia contém instruções detalhadas para a configuração da PAW para os cenários indicados acima. Se houver requisitos para os outros cenários, você poderá adaptar por conta própria as instruções com base neste guia ou contratar uma organização de serviços profissionais, como a Microsoft, para auxiliar nessa tarefa.

Para saber mais sobre como usar os serviços da Microsoft para projetar uma PAW personalizada para o seu ambiente, entre em contato com seu representante da Microsoft ou visite [esta página](https://www.microsoft.com/en-us/microsoftservices/campaigns/cybersecurity-protection.aspx).

## <a name="paw-phased-implementation"></a>Implementação de Phased da PAW

Como a PAW deve fornecer uma fonte confiável e segura para administração, é essencial que o processo de compilação seja seguro e confiável.  Esta seção fornecerá instruções detalhadas que permitirão a você criar suas próprias PAWs usando princípios e conceitos gerais muito semelhantes aos usados pela TI da Microsoft e pela engenharia de nuvem da Microsoft e organizações de gerenciamento de serviço.

As instruções são divididas em três fases que se concentram em adotar rapidamente as atenuações mais importantes e, em seguida, aumentar e expandir progressivamente o uso da PAW na empresa.

* [Fase 1: implantação imediata para administradores do Active Directory](#phase-1-immediate-deployment-for-active-directory-administrators)
* [Fase 2: extensão da PAW a todos os administradores](#phase-2-extend-paw-to-all-administrators)
* [Fase 3: segurança avançada de PAW](#phase-3-extend-and-enhance-protection)

É importante observar que as fases sempre devem ser realizadas em ordem, mesmo se forem planejadas e implementadas como parte do mesmo projeto geral.

### <a name="phase-1-immediate-deployment-for-active-directory-administrators"></a>Fase 1: Implantação imediata para administradores do Active Directory

Finalidade: Fornece rapidamente uma PAW que pode proteger funções de administração de domínio e floresta local.

Escopo: Administradores de camada 0 incluindo administradores de empresa, Admins. do domínio (para todos os domínios) e os administradores de outros sistemas de identidade autoritativos.

A Fase 1 concentra-se nos administradores que gerenciam seu domínio do Active Directory local, que são funções extremamente importantes e frequentemente alvo de invasores. Esses sistemas de identidade funcionarão com eficiência para proteger esses administradores se os seus Controladores de Domínios do Active Directory estiverem hospedados em datacenters locais, em IaaS (Infraestrutura como serviço) do Azure ou outro provedor de IaaS.

Durante essa fase, você criará a estrutura administrativa e protegida de unidade organizacional do Active Directory para hospedar sua PAW (Estação de Trabalho com Acesso Privilegiado), bem como implantar as próprias PAWs.  Essa estrutura também inclui as políticas de grupo e grupos necessários para dar suporte à PAW.  Você criará a maioria da estrutura usando scripts do PowerShell que estão disponíveis na [Galeria do TechNet](https://aka.ms/pawmedia).

Os scripts criarão as seguintes unidades organizacionais e grupos de segurança:

* Unidades organizacionais (UO)
   * Seis novas UOs nível superior:  Admin; Grupos; Servidores de camada 1; Estações de trabalho; Contas de usuário; e quarentena do computador.  Cada UO de nível superior conterá várias UOs.
* Grupos
   * Seis novos grupos habilitados de segurança globais:  Manutenção da replicação de camada 0; Manutenção do servidor de camada 1; Operadores de suporte técnico de serviço; Manutenção de estação de trabalho; Usuários da PAW. Manutenção PAW.

Você também criará vários objetos de diretiva de grupo: Configuração da PAW - computador; Configuração da PAW - usuário. RestrictedAdmin requerida - computador; Restrições de saída de PAW; Restringir o Logon da estação de trabalho; Restringir o Logon no servidor.

A Fase 1 inclui as seguintes etapas:

#### <a name="complete-the-prerequisites"></a>Completar os pré-requisitos

1. **Certifique-se de que todos os administradores usem contas individuais e separadas para atividades de administração e de usuário final** (incluindo email, navegação na Internet, aplicativos de linha de negócios e outras atividades não administrativas).  Atribuir uma conta administrativa para cada funcionário autorizado separada de sua conta de usuário padrão é fundamental para o modelo da PAW, pois somente determinadas contas terão permissão para fazer logon na PAW.

   > [!NOTE]
   > Cada administrador deve usar sua própria conta para administração.  Não compartilhe uma conta administrativa.

2. **Minimize o número de administradores privilegiados de Camada 0**.  Como cada administrador deve usar uma PAW, reduzir o número de administradores reduz o número de PAWs necessárias para dar suporte a eles e os custos associados. A contagem inferior de administradores também resulta em uma exposição menor desses privilégios e riscos associados. Embora seja possível para administradores em um local compartilharem uma PAW, os administradores em locais físicos separados exigirão PAWs separadas.
3. **Adquira hardware de um fornecedor confiável que atenda a todos os requisitos técnicos**. A Microsoft recomenda a aquisição de hardware que atende aos requisitos técnicos no artigo [Proteger as credenciais de domínio com o Credential Guard](https://technet.microsoft.com/library/mt483740%28v=vs.85%29.aspx).

   > [!NOTE]
   > A PAW instalada no hardware sem esses recursos pode fornecer proteções significativas, mas os recursos de segurança avançados, como o Credential Guard e o Device Guard não estarão disponíveis.  O Credential Guard e o Device Guard não são necessários para a implantação da Fase 1, mas são altamente recomendados como parte da Fase 3 (proteção avançada).
   >
   > Certifique-se de que o hardware usado para a PAW tenha origem de um fabricante e fornecedor cujas práticas de segurança sejam confiáveis para a organização. Essa é uma aplicação do princípio de origem limpa com o objetivo de fornecer segurança para a cadeia de suprimentos.
   >
   > Para saber mais sobre a importância da segurança na cadeia de suprimentos, visite [este site](https://www.microsoft.com/security/cybersecurity/).

4. **Adquirir e validar o necessários Windows 10 Enterprise Edition e o software de aplicativo**. Obtenha o software necessário para a PAW e valide-o usando a orientação em [Origem limpa para mídia de instalação](https://aka.ms/cleansource).

   * Windows 10 Enterprise Edition
   * [Ferramentas de Administração de Servidor Remoto](https://www.microsoft.com/en-us/download/details.aspx?id=45520) para Windows 10
   * [Windows 10 linhas de base de segurança](https://aka.ms/win10baselines)

      > [!NOTE]
      > A Microsoft publica os hashes MD5 para todos os sistemas operacionais e aplicativos no MSDN, mas nem todos os fornecedores de software fornecem uma documentação semelhante.  Nesses casos, é necessário recorrer a outras estratégias.  Para saber mais sobre a validação de software, consulte [Origem limpa](https://aka.ms/cleansource) para mídia de instalação.

5. **Certifique-se de que o servidor do WSUS esteja disponível na Intranet**. Você precisará de um servidor do WSUS na Intranet para baixar e instalar atualizações para PAW. Este servidor do WSUS deve ser configurado para aprovar automaticamente todas as atualizações de segurança para Windows 10, ou a equipe administrativa deverá ter responsabilidade para aprovar rapidamente as atualizações de software.

   > [!NOTE]
   > Para saber mais, veja a seção “Aprovar automaticamente atualizações para instalação” em [Guia sobre aprovação de atualizações](https://technet.microsoft.com/library/cc708458(v=ws.10).aspx).

#### <a name="deploy-the-admin-ou-framework-to-host-the-paws"></a>Implantar a estrutura de UO de administração para hospedar as PAWs

1. Baixe a biblioteca de scripts de PAW na [Galeria do TechNet](https://aka.ms/PAWmedia)

   > [!NOTE]
   > Baixar todos os arquivos e salvá-los no mesmo diretório e execute-os na ordem especificada abaixo.  Create-PAWGroups depende da estrutura de UO criada por Create-PAWOUs, e Set-PAWOUDelegation depende dos grupos criados por Create-PAWGroups.
   > Não modifique os scripts ou o arquivo de valores separados por vírgulas (CSV).

2. **Execute o script Create-PAWOUs.ps1**.  Esse script criará a nova estrutura da unidade organizacional (UO) no Active Directory e bloqueará a herança de GPO em novas UOs, conforme apropriado.
3. **Execute o script Create-PAWGroups.ps1**.  Esse script criará novos grupos de segurança globais nas UOs apropriadas.

   > [!NOTE]
   > Embora esse script crie novos grupos de segurança, ele não os preencherá automaticamente.

4. **Execute o script Set-PAWOUDelegation.ps1**.  Esse script atribuirá permissões às novas UOs para os grupos apropriados.

#### <a name="move-tier-0-accounts-to-the-admintier-0accounts-ou"></a>Mova as contas de camada 0 para a UO admin\camada 0\contas

Mova cada conta que seja membro do grupo Administrador de Domínio, Administrador de Empresa ou de grupos equivalentes à Camada 0 (incluindo associação aninhada) para esta UO. Se sua organização tiver seus próprios grupos que foram adicionados a esses grupos, você deverá movê-los para a UO de Admin\Camada 0\Grupos.

   > [!NOTE]
   > Para saber mais sobre quais grupos são de Camada 0, consulte "Equivalência à Camada 0" em [Proteção do material de referência de acesso privilegiado](../securing-privileged-access/securing-privileged-access-reference-material.md).

#### <a name="add-the-appropriate-members-to-the-relevant-groups"></a>Adicionar os membros apropriados aos grupos relevantes

1. **Usuários da PAW**: adicione administradores de Camada 0 com os grupos Administradores de Domínio ou de Empresa que você identificou na Etapa 1 da Fase 1.
2. **Manutenção de PAW**: adicione pelo menos uma conta a ser usada para manutenção da PAW e tarefas de solução de problemas. As Contas de Manutenção de PAW raramente serão usadas.

   > [!NOTE]
   > Não adicione a mesma conta de usuário ou grupo a Usuários da PAW e Manutenção da PAW.  O modelo de segurança da PAW tem base parcialmente na suposição de que a conta de usuário da PAW tem direitos privilegiados em sistemas gerenciados ou sobre a própria PAW, mas não em ambos.
   >
   > * Isso é importante para a criação de boas práticas e hábitos administrativos na Fase 1.
   > * Isso é extremamente importante para a Fase 2 e fases seguintes para evitar o escalonamento de privilégios por meio da PAW, pois as PAWs envolvem Camadas.
   >
   > De forma ideal, nenhuma equipe recebe tarefas em várias camadas a fim de aplicar o princípio de segregação de tarefas, mas a Microsoft reconhece que muitas organizações podem ter uma equipe limitada (ou outros requisitos organizacionais) que não permitem essa segregação completa. Nesses casos, a mesma equipe pode receber ambas as funções, mas não deve usar a mesma conta para essas funções.

#### <a name="create-paw-configuration---computer-group-policy-object-gpo"></a>Criar o objeto de política de grupo (GPO) "Da PAW configuração – computador"

Nesta seção, você criará um novo "PAW configuração – Computer" GPO que fornece proteções específicas para essas PAWs e vinculá-lo a UO de dispositivos de camada 0 ("dispositivos" em camada 0\Admin).

   > [!NOTE]
   > **Não adicione essas configurações à Política de Domínio Padrão**.  Isso potencialmente afetará as operações em todo o seu ambiente do Active Directory.  Apenas defina essas configurações nos GPOs recém-criados descritos aqui e aplique-as apenas à UO da PAW.

1. **Acesso de Manutenção da PAW**: essa configuração definirá a associação de grupos privilegiados específicos nas PAWs a um conjunto específico de usuários. Acesse *Configuração do Computador\Preferências\Configurações de Painel de Controle\Usuários e Grupos Locais* e execute as etapas abaixo:
   1. Clique em **Novo** e em **Grupo Local**
   2. Selecione a ação **Atualizar** e selecione "Administradores (interno)" (não use o botão Procurar para selecionar o grupo Administradores do domínio).
   3. Marque as caixas de seleção **Excluir todos os usuários membros** e **Excluir todos os grupos membros**
   4. Adicione Manutenção da PAW (pawmaint) e Administrador (novamente, não use o botão Procurar para selecionar o administrador).

      > [!NOTE]
      > Não adicione o grupo Usuários da PAW à lista de membros para o grupo local de Administradores.  Para garantir que os Usuários da PAW não possam, acidental ou deliberadamente, modificar configurações de segurança da própria PAW, eles não devem ser membros dos grupos locais de Administradores.
      >
      > Para saber mais sobre como usar as Preferências de Política de Grupo para modificar a associação de grupo, consulte o artigo da TechNet [Configurar um Item de Grupo Local](https://technet.microsoft.com/library/cc732525.aspx).

2. **Restringir a Associação no Grupo Local** - essa configuração garantirá que a associação dos grupos de administradores locais na estação de trabalho esteja sempre vazia
   1. Acesse Configuração do Computador\Preferências\Configurações de Painel de Controle\Usuários e Grupos Locais e execute as etapas abaixo:
      1. Clique em **Novo** e em **Grupo Local**
      2. Selecione a ação **Atualizar** e selecione "Operadores de Backup (interno)" (não use o botão Procurar para selecionar o grupo Operadores de Backup de domínio).
      3. Marque as caixas de seleção **Excluir todos os usuários membros** e **Excluir todos os grupos de membros**.
      4. Não adicione nenhum membro ao grupo.  Simplesmente clique em **OK**.  Ao atribuir uma lista vazia, a política de grupo automaticamente removerá todos os membros e garantirá uma lista de membros vazia sempre que cada política de grupo for atualizada.
   2. Conclua as etapas acima para os seguintes grupos adicionais:
      * Operadores criptográficos
      * Administradores do Hyper-V
      * Operadores de configuração de rede
      * Usuários avançados
      * Usuários da Área de Trabalho Remota
      * Replicadores
   3. **Restrições de Logon PAW** -essa configuração limita as contas que podem se conectar à paw. Execute as etapas abaixo para definir essa configuração:
      1. Acesse Configuração do Computador\Políticas\Configurações do Windows\Configurações de Segurança\Políticas locais\Atribuição de direitos de usuário\ Permitir logon localmente.
      2. Selecione Definir estas configurações de política e adicione "Usuários da PAW" e os administradores (novamente, não use o botão Procurar para selecionar os administradores).
   4. **Bloquear Tráfego de Rede de Entrada** - essa configuração garante que nenhum tráfego de rede de entrada não solicitado tenha permissão na PAW. Execute as etapas abaixo para definir essa configuração:
      1. Acesse Configuração do Computador\Políticas\Configurações do Windows\Configurações de Segurança\Firewall do Windows com Segurança Avançada\Firewall do Windows com Segurança Avançada e execute estas etapas:
         1. Clique com o botão direito do mouse em Firewall do Windows com Segurança Avançada e selecione **Importar política**.
         2. Clique em **Sim** para aceitar que isso substituirá quaisquer políticas de firewall existentes.
         3. Navegue até PAWFirewall.wfw e selecione **Abrir**.
         4. Clique em **OK**.

            > [!NOTE]
            > Você pode adicionar endereços ou sub-redes que precisam acessar a PAW com tráfego não solicitado neste momento (por exemplo, software de verificação ou gerenciamento de segurança).
            > As configurações no arquivo WFW permitirão o firewall no modo "Bloquear – Padrão" para todos os perfis de firewall, desativarão a mesclagem de regra e habilitarão o registro em log de pacotes descartados e bem-sucedidos. Essas configurações serão bloquear o tráfego não solicitado enquanto ainda permite que a comunicação bidirecional em conexões iniciadas da PAW, impedem que usuários com acesso administrativo local criem regras de firewall local que poderia substituir as configurações de GPO e Certifique-se de que o tráfego dentro e fora da PAW está registrado.
            > **Abrir esse firewall expandirá a superfície de ataque da PAW e aumentará o risco de segurança. Antes de adicionar os endereços, consulte a seção Gerenciar e operar a PAW neste guia**.

   5. **Configurar o Windows Update para o WSUS** - execute as etapas abaixo para alterar as configurações a fim de configurar o Windows Update para as PAWs:
      1. Vá para o computador Computador\Diretivas\Modelos Administrativos\Componentes do Windows\Windows Update e siga as etapas abaixo:
         1. Habilite a política **Configurar Atualizações Automáticas**.
         2. Selecione a opção **4 - Baixar automaticamente e agendar a instalação**.
         3. Altere a opção **Dia agendado para a instalação** para **0 - Todos os dias** e a opção **Hora agendada para a instalação** para algo de sua preferência.
         4. Habilitar a opção **especificar o local de serviço de atualização na intranet da Microsoft** política, e especifique em ambas as opções a URL do servidor WSUS ESAE.
   6. Vincule o "da PAW configuração – Computer" GPO da seguinte maneira:

         |Política|Local do link|
         |-----|---------|
         |Configuração da PAW - Computador |Admin\Camada 0\Dispositivos|

#### <a name="create-paw-configuration---user-group-policy-object-gpo"></a>Criar o objeto de política de grupo (GPO) "Da PAW configuração – usuário"

Nesta seção, você criará um novo "PAW configuração – usuário" GPO que fornece proteções específicas para essas PAWs e um link para a UO de contas de camada 0 ("contas" em camada 0\Admin).

   > [!NOTE]
   > Não adicione essas configurações à Política de Domínio Padrão

1. **Bloquear navegação na Internet** - Para deter a navegação acidental na Internet, isso definirá um endereço de proxy de um endereço de loopback (127.0.0.1).
   1. Vá para a configuração do usuário windows\registro. Clique com botão direito do registro, selecione **New** > **Item do registro** e defina as seguintes configurações:
      1. Ação:  Substituir
      2. Hive: HKEY_CURRENT_USER
      3. Caminho da chave:  Software\Microsoft\Windows\CurrentVersion\Internet Settings
      4. Nome do valor: ProxyEnable

         > [!NOTE]
         > Não selecione a caixa Padrão à esquerda do nome do Valor.

      5. Tipo de valor: REG_DWORD
      6. 방법 2 1
         1. Clique na guia Comum e selecione **Remover este item quando ele não for mais aplicado**.
         2. Na guia Comum selecione **Direcionamento de nível de item** e clique em **Direcionamento**.
         3. Clique em **Novo Item** e selecione **Grupo de segurança**.
         4. Selecione o botão "..." e navegue até o grupo Usuários da PAW.
         5. Clique em **Novo Item** e selecione **Grupo de segurança**.
         6. Selecione o botão "..." e navegue até o grupo **Administradores de Serviços de Nuvem**.
         7. Clique no item **Administradores de Serviços de Nuvem** e clique em **Opções de Item**.
         8. Selecione **Não é**.
         9. Clique em **OK** na janela de direcionamento.
      7. Clique em **OK** para concluir a configuração de política de grupo ProxyServer
   2. Vá para a configuração do usuário windows\registro. Clique com botão direito do registro, selecione **New** > **Item do registro** e defina as seguintes configurações:

      * Ação: Substituir
      * Hive: HKEY_CURRENT_USER
      * Caminho da chave: Software\Microsoft\Windows\CurrentVersion\Internet Settings
         * Nome do valor: ProxyServer

            > [!NOTE]
            > Não selecione a caixa Padrão à esquerda do nome do Valor.

         * Tipo de valor: REG_SZ
         * 방법 2 127.0.0.1:80
            1. Clique na guia **Comum** e selecione **Remover este item quando ele não for mais aplicado**.
            2. Na guia **Comum** selecione **Direcionamento de nível de item** e clique em **Direcionamento**.
            3. Clique em **Novo Item** e selecione Grupo de segurança.
            4. Selecione o botão "..." e adicione o grupo Usuários da PAW.
            5. Clique em **Novo Item** e selecione Grupo de segurança.
            6. Selecione o botão "..." e navegue até o grupo **Administradores de Serviços de Nuvem**.
            7. Clique no item **Administradores de Serviços de Nuvem** e clique em **Opções de Item**.
            8. Selecione **Não é**.
            9. Clique em **OK** na janela de direcionamento.

   3. Clique em **OK** para concluir a configuração de política de grupo ProxyServer,
2. Vá para o usuário Computador\Diretivas\Modelos Administrativos\Componentes do Windows\Internet Explorer e habilite as opções a seguir. Essas configurações impedirão que os administradores substituam as configurações de proxy manualmente.
   1. Habilite **Desativar a alteração das definições de Configuração Automática**.
   2. Habilite **Impedir alteração das configurações de proxy**.

#### <a name="restrict-administrators-from-logging-onto-lower-tier-hosts"></a>Impedir que administradores efetuem logon em hosts de camada inferior

Nesta seção, configuraremos as políticas de grupo para impedir que contas com privilégios administrativos façam logon em hosts de camadas inferiores.

1. Crie o novo GPO **Restringir Logon na Estação de Trabalho** essa configuração restringirá o logon de contas de administrador de Camada 0 e Camada 1 em estações de trabalho padrão.  Esse GPO deve ser vinculado o UO de nível superior de "Estações de trabalho" e têm as seguintes configurações:
   * No computador \ Diretivas \ Configurações de segurança locais \ Atribuição direitos Negar logon como um trabalho em lotes, selecione **definir estas configurações de política** e adicione os grupos de camada 1 e camada 0:     Enterprise Admins de domínio administradores de esquema domínio \ Administradores de administradores conta Backup Operadores de impressão operadores Server operadores domínio controladores grupo controladores de domínio somente leitura política criadores proprietários criptográfico Oper ators

         > [!NOTE]
         > Built-in Tier 0 Groups, see Tier 0 equivalency for more details.

         Other Delegated Groups

         > [!NOTE]
         > Any custom created groups with effective Tier 0 access, see Tier 0 equivalency for more details.

         Tier 1 Admins

         > [!NOTE]
         > This Group was created earlier in Phase 1.

   * No computador \ Diretivas \ Configurações de segurança locais \ Atribuição direitos Negar logon como um serviço, selecione **definir estas configurações de política** e adicione os grupos de camada 1 e camada 0:     Enterprise Admins de domínio administradores de esquema domínio \ Administradores de administradores conta Backup Operadores de impressão operadores Server operadores domínio controladores grupo controladores de domínio somente leitura política criadores proprietários criptográfico Oper ators

         > [!NOTE]
         > Note: Built-in Tier 0 Groups, see Tier 0 equivalency for more details.

         Other Delegated Groups

         > [!NOTE]
         > Note: Any custom created groups with effective Tier 0 access, see Tier 0 equivalency for more details.

         Tier 1 Admins

         > [!NOTE]
         > Note: This Group was created earlier in Phase 1

2. Criar o novo **restringir Logon no servidor** GPO - essa configuração restringirá as contas de administrador de camada 0 efetuar logon em servidores da camada 1.  Esse GPO deve ser vinculado a UO de nível superior de "Servidores da camada 1" e têm as seguintes configurações:
   * No computador \ Diretivas \ Configurações de segurança locais \ Atribuição direitos Negar logon como um trabalho em lotes, selecione **definir estas configurações de política** e adicione os grupos de camada 0:     Enterprise Admins de domínio administradores de esquema domínio \ Administradores de administradores conta Backup Operadores de impressão operadores Server operadores domínio controladores grupo controladores de domínio somente leitura política criadores proprietários criptográfico Oper ators

         > [!NOTE]
         > Built-in Tier 0 Groups, see Tier 0 equivalency for more details.

         Other Delegated Groups

         > [!NOTE]
         > Any custom created groups with effective Tier 0 access, see Tier 0 equivalency for more details.

   * No computador \ Diretivas \ Configurações de segurança locais \ Atribuição direitos Negar logon como um serviço, selecione **definir estas configurações de política** e adicione os grupos de camada 0:     Enterprise Admins de domínio administradores de esquema domínio \ Administradores de administradores conta Backup Operadores de impressão operadores Server operadores domínio controladores grupo controladores de domínio somente leitura política criadores proprietários criptográfico Oper ators

         > [!NOTE]
         > Built-in Tier 0 Groups, see Tier 0 equivalency for more details.

         Other Delegated Groups

         > [!NOTE]
         > Any custom created groups with effective Tier 0 access, see Tier 0 equivalency for more details.

   * No computador \ Diretivas \ Configurações de segurança locais \ Atribuição direitos Negar logon localmente, selecione **definir estas configurações de política** e adicione os grupos de camada 0:     Enterprise Admins de domínio administradores de esquema conta de Admins operadores operadores de Backup Operadores de impressão operadores Server operadores domínio controladores grupo controladores de domínio somente leitura política criadores proprietários criptográfico

         > [!NOTE]
         > Note: Built-in Tier 0 Groups, see Tier 0 equivalency for more details.

         Other Delegated Groups

         > [!NOTE]
         > Note: Any custom created groups with effective Tier 0 access, see Tier 0 equivalency for more details.

#### <a name="deploy-your-paws"></a>Implantar sua(s) PAW(s)

   > [!NOTE]
   > Certifique-se de que a PAW esteja desconectada da rede durante o processo de compilação do sistema operacional.

1. Instale o Windows 10 usando a mídia de instalação de origem limpa que você obteve anteriormente.

   > [!NOTE]
   > Você pode usar o MDT (Microsoft Deployment Toolkit) ou outro sistema de implantação de imagem automatizado para automatizar a implantação da PAW, mas é necessário garantir que o processo de compilação seja tão confiável quanto a PAW. Os adversários procuram especificamente por imagens corporativas e sistemas de implantação (incluindo ISOs, pacotes de implantação etc.) como um mecanismo de persistência, então sistemas de implantação ou imagens preexistentes não devem ser usados.
   >
   > Se você automatizar a implantação da PAW, faça o seguinte:
   >
   > * Compile o sistema usando a mídia de instalação validada seguindo a orientação em [Origem limpa para a mídia de instalação](https://aka.ms/cleansource).
   > * Certifique-se de que o sistema de implantação automatizado esteja desconectado da rede durante o processo de compilação do sistema operacional.

2. Defina uma senha complexa e exclusiva para a conta de administrador local.  Não use uma senha que foi usada para qualquer outra conta no ambiente.

   > [!NOTE]
   > A Microsoft recomenda usar a [LAPS (Solução de Senha de Administrador Local)](https://www.microsoft.com/en-us/download/details.aspx?id=46899) para gerenciar a senha de administrador local para todas as estações de trabalho, incluindo as PAWs.  Se você usar a LAPS, conceda somente ao grupo Manutenção da PAW o direito de ler senhas gerenciadas pela LAPS para as PAWs.

3. Instale as Ferramentas de Administração de Servidor Remoto para Windows 10 usando a mídia de instalação de origem limpa.
4. Configurar o Windows Defender Exploit Guard

   > [!NOTE]
   > Diretrizes de configuração a seguir

5. Conectar a PAW à rede.  Certifique-se de que a PAW possa conectar-se a pelo menos um Controlador de Domínio (DC).
6. Usando uma conta membro do grupo Manutenção da PAW, execute o seguinte comando do PowerShell na PAW recém-criada a fim de ingressar o domínio na UO adequada:

   `Add-Computer -DomainName Fabrikam -OUPath "OU=Devices,OU=Tier 0,OU=Admin,DC=fabrikam,DC=com"`

   Substitua as referências a *Fabrikam* por seu nome de domínio, conforme apropriado.  Se o seu nome de domínio se estender a vários níveis (por exemplo, child.fabrikam.com), adicione os outros nomes com o identificador "DC =" na ordem em que aparecem no nome de domínio totalmente qualificado do domínio.

   > [!NOTE]
   > Se você implantou uma [Floresta Administrativa ESAE](https://aka.ms/esae) (para administradores de Camada 0 na Fase 1) ou um [PAM (gerenciamento de acesso privilegiado) do MIM (Microsoft Identity Manager)](https://aka.ms/mimpamdeploy) (para administradores de Camada 1 e 2 na Fase 2), você ingressaria a PAW ao domínio nesse ambiente, em vez do domínio de produção.

7. Aplique todas as atualizações críticas e importantes do Windows antes de instalar qualquer outro software (incluindo ferramentas administrativas, agentes etc.).
8. Force a aplicação da Política de Grupo.
   1. Abra um prompt de comando com privilégios elevados e digite o seguinte comando: `Gpupdate /force /sync`
   2. Reinicie o computador

9. (Opcional) Instale ferramentas adicionais necessárias para os administradores de diretório Active Directory. Instale outras ferramentas ou scripts necessários para realizar seus trabalhos. Avalie o risco de exposição de credencial nos computadores de destino com alguma ferramenta antes de adicioná-los a uma PAW. Acesse [esta página](https://aka.ms/logontypes) para obter mais informações sobre como avaliar as ferramentas administrativas e os métodos de conexão para o risco de exposição de credencial. Obtenha todas as mídias de instalação usando as diretrizes de [Origem limpa para a mídia de instalação](https://aka.ms/cleansource).

   > [!NOTE]
   > Usar um servidor de salto como local central para essas ferramentas pode reduzir a complexidade, mesmo que não sirva como um limite de segurança.

10. (Opcional) Baixe e instale o software de acesso remoto necessário. Se os administradores usarem a PAW remotamente para administração, instale o software de acesso remoto usando as diretrizes de segurança de seu fornecedor de solução de acesso remoto. Obtenha todas as mídias de instalação usando as diretrizes de Origem limpa para a mídia de instalação.

    > [!NOTE]
    > Considere cuidadosamente todos os riscos envolvidos na permissão de acesso remoto via uma PAW.  Embora uma PAW móvel permita vários cenários importantes, incluindo home office, o software de acesso remoto pode ficar vulnerável a ataques e ser usado para comprometer uma PAW.

11. Valide a integridade do sistema da PAW revisando e confirmando que todas as configurações apropriadas foram aplicadas usando as etapas abaixo:
    1. Confirme se apenas as políticas de grupo específicas às PAWs foram aplicadas à PAW
       1. Abra um prompt de comando com privilégios elevados e digite o seguinte comando: `Gpresult /scope computer /r`
       2. Examine a lista resultante e certifique-se de que as políticas de grupo que aparecem são aqueles que você criou logo acima.
    2. Confirme que nenhuma conta de usuário adicional é membro dos grupos privilegiados na PAW usando as etapas abaixo:
       1. Abra **Editar Usuários e Grupos Locais** (lusrmgr.msc), selecione **Grupos** e confirme que os únicos membros do grupo local Administradores são a conta de Administrador local e o grupo de segurança global Manutenção da PAW.

          > [!NOTE]
          > O grupo Usuários da PAW não deve ser membro do grupo local Administradores.  Os únicos membros devem ser a conta local de Administrador e o grupo de segurança global Manutenção da PAW (e Usuários da PAW não deve ser um membro desse grupo global).

       2. Além disso, usando **Editar Usuários e Grupos Locais**, verifique se os seguintes grupos têm algum membro: Os administradores do Hyper-V de operadores criptográficos de operadores de backup de configuração operadores Power usuários usuários da área de trabalho remota replicadores de rede

12. (Opcional) Se sua organização usa uma solução de gerenciamento (SIEM) do evento e informações de segurança, certifique-se de que a PAW esteja [configurado para encaminhar eventos para o sistema usando o encaminhamento de eventos do Windows (WEF)](http://blogs.technet.com/b/jepayne/archive/2015/11/24/monitoring-what-matters-windows-event-forwarding-for-everyone-even-if-you-already-have-a-siem.aspx) ou esteja registrada com o solução para que a SIEM receba ativamente eventos e informações da PAW.  Os detalhes dessa operação poderão variar com base em sua solução SIEM.

    > [!NOTE]
    > Se a SIEM exigir um agente executado como uma conta de sistema ou de administração local nas PAWs, certifique-se de que as SIEMs sejam gerenciadas com o mesmo nível de confiança que os controladores de domínio e sistemas de identidade.

13. (Opcional) Se você optar por implantar LAPS para gerenciar a senha para a conta de administrador local em sua PAW, verifique se a senha é registrada com êxito.

    * Usando uma conta com permissões para ler senhas gerenciadas por LAPS, abra **Usuários e Computadores do Active Directory** (dsa.msc).  Verifique se Recursos avançados está habilitado e, em seguida, clique com o botão direito do mouse no objeto do computador apropriado.  Selecione a guia Editor de Atributos e confirme se o valor para msSVSadmPwd foi preenchido com uma senha válida.

### <a name="phase-2-extend-paw-to-all-administrators"></a>Fase 2: Extensão da PAW a todos os administradores

Escopo: Todos os usuários com direitos administrativos sobre aplicativos de missão crítica e dependências.  Isso deve incluir pelo menos os administradores de servidores de aplicativos, soluções de monitoramento de integridade w segurança operacional, soluções de virtualização, sistemas de armazenamento e dispositivos de rede.

> [!NOTE]
> As instruções nesta fase presumem que a Fase 1 foi concluída totalmente.  Comece a fase 2 até concluir todas as etapas na fase 1.

Depois de confirmar que todas as etapas foram executadas, execute as etapas abaixo para concluir a Fase 2:

#### <a name="recommended-enable-restrictedadmin-mode"></a>(Recomendado) Habilitar **RestrictedAdmin** modo

Habilitar esse recurso em seus servidores existentes e estações de trabalho e, em seguida, impor o uso desse recurso. Esse recurso exigirá que os servidores de destino para estar em execução no Windows Server 2008 R2 ou posterior e direcionar as estações de trabalho para executar o Windows 7 ou posterior.

1. Habilite o modo **RestrictedAdmin** nos servidores e estações de trabalho seguindo as instruções disponíveis nesta [página](https://aka.ms/rdpra).

   > [!NOTE]
   > Antes de habilitar esse recurso para servidores voltados à Internet, considere o risco de os adversários serem capazes de autenticar nesses servidores com um hash de senha roubada anteriormente.

2. Crie o GPO (Objeto de Política de Grupo) "RestrictedAdmin Required – Computer". Esta seção cria um GPO que impõe o uso da opção /RestrictedAdmin para conexões de Área de Trabalho Remota de saída, protegendo contas contra o roubo de credenciais nos sistemas de destino
   * Acesse Configuração do Computador\Políticas\Modelos Administrativos\Sistema\Delegação de Credenciais\Restringir delegação de credenciais para servidores remotos e defina como **Habilitado**.
3. Vincule o **RestrictedAdmin** Requires - Computador aos dispositivos apropriados da Camada 1 e/ou Camada 2 usando as opções de Política a seguir:
   * Configuração da PAW - Computador
      * -> Local do link: Admin\Camada 0\Dispositivos (existente)
   * Configuração da PAW - Usuário
      * -> Local do link: Admin\camada 0\contas
   * RestrictedAdmin Required - Computador
      * -> Admin\Tier1\Devices ou -> Admin\Tier2\Devices (ambos são opcionais)

   > [!NOTE]
   > Isso não é necessário para sistemas de Camada 0, pois esses sistemas já estão no controle total de todos os ativos no ambiente.

#### <a name="move-tier-1-objects-to-the-appropriate-ous"></a>Mover objetos da camada 1 para as UOs apropriadas

1. Mova grupos da Camada 1 para a UO Admin\Camada 1\Grupos. Localize todos os grupos que concedem os seguintes direitos administrativos e mova-os para essa UO.
   * Administrador local em mais de um servidor
      * Acesso Administrativo aos serviços de nuvem
      * Acesso Administrativo aos aplicativos corporativos
2. Mova as contas da Camada 1 para a UO Admin\Camada 1\Contas. Mova cada conta membro dos grupos de Camada 1 (incluindo associação aninhada) para essa UO.
3. Adicionar os membros apropriados aos grupos relevantes
   * **Administradores de Camada 1** - Esse grupo conterá os Administradores de Camada 1 que não poderão efetuar logon em hosts de Camada 2. Adicione todos os seus grupos administrativos camada 1 que possuam privilégios administrativos em servidores ou serviços da internet.

      > [!NOTE]
      > Se a equipe administrativa tiver obrigações de gerenciamento de ativos em várias camadas, será necessário criar uma conta de administrador separada por camada.

4. Habilite o Credential Guard para reduzir o risco de roubo e reutilização de credenciais.  O Credential Guard é um novo recurso do Windows 10 que restringe o acesso do aplicativos às credenciais, impedindo ataques de roubo de credenciais (incluindo Passagem de Hash).  O Credential Guard é completamente transparente para o usuário final e exige o mínimo de configuração.  Para saber mais sobre o Credential Guard, incluindo etapas de implantação e requisitos de hardware, consulte o artigo [Proteger as credenciais de domínio com o Credential Guard](https://technet.microsoft.com/library/mt483740%28v=vs.85%29.aspx).

   > [!NOTE]
   > O Device Guard deve ser habilitado para configurar e usar o Credential Guard.  No entanto, não é necessário configurar quaisquer outras proteções do Device Guard para usar o Credential Guard.

5. (Opcional) Habilite a conectividade com serviços de nuvem. Esta etapa permite o gerenciamento de serviços de nuvem como o Azure e o Office 365 com as garantias de segurança apropriadas. Esta etapa também é necessária para o Microsoft Intune, a fim de gerenciar as PAWs.

   > [!NOTE]
   > Ignore esta etapa se não houver a necessidade de conectividade de nuvem para a administração dos serviços de nuvem ou para o gerenciamento pelo Intune.

   * Essas etapas restringirão a comunicação pela Internet somente aos serviços de nuvem autorizados (mas não a Internet aberta) e acrescentarão proteções aos navegadores e a outros aplicativos que processarão o conteúdo da Internet. Esses PAWs para administração nunca devem ser usadas para tarefas de usuário padrão, como comunicação e produtividade pela Internet.
   * Para habilitar a conectividade para os serviços da PAW, execute as etapas abaixo:

   1. Configure a PAW para permitir somente destinos da Internet autorizados.  Como estender sua implantação PAW para habilitar a administração de nuvem, você precisa permitir o acesso a serviços autorizados durante a filtragem de acesso da internet aberta onde ataques com mais facilidade podem ser montados em relação a seus administradores.

      1. Crie **administradores de serviços de nuvem** de grupo e adicionar todas as contas que exigem acesso aos serviços de nuvem na internet.
      2. Baixe o arquivo *proxy.pac* da PAW na [Galeria do TechNet](https://aka.ms/pawmedia) e publique-o em um site interno.

         > [!NOTE]
         > Será necessário atualizar o arquivo *proxy.pac* após o download, para garantir que ele esteja atualizado e completo.  
         > A Microsoft publica todas as URLs atuais do Office 365 e do Azure [Centro de Suporte do Office](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US). Essas instruções pressupõem que você usará o Internet Explorer (ou Microsoft Edge) para a administração do Office 365, Azure e outros serviços de nuvem. A Microsoft recomenda a configuração de restrições semelhantes para qualquer navegador de terceiros que você precise usar para a administração. Só use navegadores da Web nas PAWs para a administração de serviços de nuvem, nunca para navegação geral.
         >
         > Talvez seja necessário adicionar outros destinos da Internet válidos para aumentar essa lista para outro provedor de IaaS, mas não adicione sites de produtividade, entretenimento, notícias ou pesquisa a esta lista.
         >
         > Talvez você precise ajustar o arquivo PAC para acomodar um endereço de proxy válido a ser usado para esses endereços.
         >
         > Você também pode restringir o acesso da PAW usando um proxy da Web para uma defesa mais profunda. Não recomendamos isso sem o arquivo PAC, pois ele apenas restringirá o acesso às PAWs enquanto estiver conectado à rede corporativa.

      3. Após a configuração do arquivo *proxy.pac*, atualize o GPO Configuração da PAW - Usuário.
         1. Vá para a configuração do usuário windows\registro. Clique com botão direito do registro, selecione **New** > **Item do registro** e defina as seguintes configurações:
            1. Ação: Substituir
            2. Hive: HKEY_ CURRENT_USER
            3. Caminho da chave: Software\Microsoft\Windows\CurrentVersion\Internet Settings
            4. Nome do valor: AutoConfigUrl

               > [!NOTE]
               > Não selecione a caixa **Padrão** à esquerda do nome do Valor.

            5. Tipo de valor: REG_SZ
            6. Dados do valor: insira a URL completa para o *PAC* de arquivo, incluindo http:// e o nome do arquivo - por exemplo http://proxy.fabrikam.com/proxy.pac.  A URL também pode ser uma URL de rótulo único – por exemplo, http://proxy/proxy.pac

               > [!NOTE]
               > O arquivo PAC também pode estar hospedado em um compartilhamento de arquivos, com a sintaxe file://server.fabrikan.com/share/proxy.pac, mas isso exige a permissão do protocolo file://. Consulte a "Observação: Preterido de Scripts do File://-based Proxy"seção desse [Noções básicas sobre configuração do Proxy Web](http://blogs.msdn.com/b/ieinternals/archive/2013/10/11/web-proxy-configuration-and-ie11-changes.aspx) blog para obter mais detalhes sobre como configurar o valor de registro necessárias.

            7. Clique na guia **Comum** e selecione **Remover este item quando ele não for mais aplicado**.
            8. Na guia **Comum** selecione **Direcionamento de nível de item** e clique em **Direcionamento**.
            9. Clique em **Novo Item** e selecione **Grupo de segurança**.
            10. Selecione o botão "..." e navegue até o grupo **Administradores de Serviços de Nuvem**.
            11. Clique em **Novo Item** e selecione **Grupo de segurança**.
            12. Selecione o botão "..." e navegue até o grupo **Usuários da PAW**.
            13. Clique no item **Usuários de PAW** e clique em **Opções de Item**.
            14. Selecione **Não é**.
            15. Clique em **OK** na janela de direcionamento.
            16. Clique em **OK** para concluir a configuração de política de grupo **AutoConfigUrl**.
   2. Aplique as Linhas de base de segurança do Windows 10 e o Link de acesso do serviço de nuvem das linhas de base de segurança para Windows e para o acesso ao serviço de nuvem (se for necessário) às UOs corretas usando as etapas abaixo:
      1. Extraia o conteúdo do arquivo ZIP de Linhas de base de segurança do Windows 10.
      2. Crie esses GPOs, [importe as configurações da política](https://technet.microsoft.com/library/cc753786.aspx) e [vincule](https://technet.microsoft.com/library/cc732979.aspx) de acordo com esta tabela. Vincule cada política a cada local e garante que a ordem siga a tabela (entradas inferiores na tabela devem ser aplicadas posteriormente e com maior prioridade):

         **Políticas:**

         |||
         |-|-|
         |CM Windows 10 - Segurança de Domínio|N/A - Não Vincular Agora|
         |SCM Windows 10 TH2 - Computador|Admin\Camada 0\Dispositivos|
         ||Admin\Camada 1\Dispositivos|
         ||Admin\Camada 2\Dispositivos|
         |SCM Windows 10 TH2- BitLocker|Admin\Camada 0\Dispositivos|
         ||Admin\Camada 1\Dispositivos|
         ||Admin\Camada 2\Dispositivos|
         |SCM Windows 10 - Credential Guard|Admin\Camada 0\Dispositivos|
         ||Admin\Camada 1\Dispositivos|
         ||Admin\Camada 2\Dispositivos|
         |SCM Internet Explorer - computador|Admin\Camada 0\Dispositivos|
         ||Admin\Camada 1\Dispositivos|
         ||Admin\Camada 2\Dispositivos|
         |Configuração da PAW - Computador|Admin\Camada 0\Dispositivos (existente)|
         ||Admin\Camada 1\Dispositivos (novo link)|
         ||Admin\Camada 2\Dispositivos (novo link)|
         |RestrictedAdmin Required - Computador|Admin\Camada 0\Dispositivos|
         ||Admin\Camada 1\Dispositivos|
         ||Admin\Camada 2\Dispositivos|
         |SCM Windows 10 - Usuário|Admin\Camada 0\Dispositivos|
         ||Admin\Camada 1\Dispositivos|
         ||Admin\Camada 2\Dispositivos|
         |SCM Internet Explorer - Usuário|Admin\Camada 0\Dispositivos|
         ||Admin\Camada 1\Dispositivos|
         ||Admin\Camada 2\Dispositivos|
         |Configuração da PAW - Usuário|Admin\Camada 0\Dispositivos (existente)|
         ||Admin\Camada 1\Dispositivos (novo link)|
         ||Admin\Camada 2\Dispositivos (novo link)|

         > [!NOTE]
         > O "SCM Windows 10 - Segurança" GPO pode ser vinculado ao domínio independentemente da PAW, mas afetará todo o domínio.

6. (Opcional) Instale ferramentas adicionais necessárias para administradores de camada 1. Instale outras ferramentas ou scripts necessários para realizar seus trabalhos. Avalie o risco de exposição de credencial nos computadores de destino com alguma ferramenta antes de adicioná-los a uma PAW. Para saber mais sobre como avaliar as ferramentas administrativas e os métodos de conexão com relação ao risco de exposição de credencial visite [esta página](https://aka.ms/logontypes). Obtenha todas as mídias de instalação usando as diretrizes de Origem limpa para a mídia de instalação
7. Identifique e obtenha com segurança o software e os aplicativos necessários para administração.  Isso é semelhante ao trabalho realizado na Fase 1, mas com um escopo mais amplo devido à quantidade maior de aplicativos, serviços e sistemas que estão sendo protegidos.

   > [!NOTE]
   > Certifique-se de que você proteja esses novos aplicativos (incluindo navegadores da web) por aceitar aceitando as proteções fornecidas pelo Windows Defender Exploit Guard.

   Exemplos de aplicativos e softwares adicionais:

      * Microsoft Azure PowerShell
      * Office 365 PowerShell (também conhecido como Módulo do Microsoft Online Services)
      * Software de gerenciamento de aplicativo ou de serviço com base no Console de Gerenciamento Microsoft
      * Software de gerenciamento de aplicativo ou de serviço proprietário (não baseado em MMC)

         > [!NOTE]
         > Agora, muitos aplicativos são gerenciados exclusivamente em navegadores da Web, incluindo muitos serviços de nuvem.  Embora isso reduza a quantidade de aplicativos que precisam ser instalados em uma PAW, isso também introduz o risco de problemas de interoperabilidade do navegador.  Talvez seja necessário implantar um navegador da Web que não seja da Microsoft em instâncias específicas da PAW a fim de habilitar a administração de serviços específicos.  Se você implantar um navegador da Web adicional, siga todos os princípios de origem limpa e proteja o navegador de acordo com as diretrizes de segurança do fornecedor.

8. (Opcional) Baixe e instale os agentes de gerenciamento necessários.

   > [!NOTE]
   > Se você optar por instalar agentes de gerenciamento adicionais (monitoramento, segurança, gerenciamento de configuração etc.), é vital que você verifique se os sistemas de gerenciamento são confiáveis no mesmo nível que os controladores de domínio e sistemas de identidade. Consulte Gerenciar e atualizar PAWs para obter orientação adicional.

9. Avalie a infraestrutura para identificar sistemas que exigem as proteções de segurança adicionais fornecidas por uma PAW.  Saiba exatamente quais sistemas devem ser protegidos.  Faça perguntas importantes sobre os próprios recursos, como:

   * Onde estão os sistemas de destino que devem ser gerenciados?  Eles são coletados em um único local físico, ou conectados a uma única sub-rede bem definida?
   * Quantos sistemas existem?
   * Esses sistemas dependem de outros sistemas (virtualização, armazenamento etc.) e, em caso afirmativo, como esses sistemas são gerenciados?  Como os sistemas críticos são expostos a essas dependências, e quais são os riscos adicionais associados a essas dependências?
   * Qual a importância dos serviços gerenciados, e quais são as perdas esperada se esses serviços forem comprometidos?

      > [!NOTE]
      > Inclua seus serviços de nuvem nesta avaliação, os invasores visam cada vez mais as implantações de nuvem desprotegidas, e é essencial que você administre esses serviços com a segurança que você usaria com seus aplicativos de missão crítica locais.

        Use esta avaliação para identificar os sistemas específicos que exigem proteção adicional, e estender seu programa PAW para os administradores desses sistemas.  Entre os exemplos comuns de sistemas que se beneficiam muito da administração baseada em PAW estão o SQL Server (local e SQL Azure), aplicativos de recursos humanos e software financeiro.

        > [!NOTE]
        > Se um recurso for gerenciado de um sistema Windows, ele poderá ser gerenciado com uma PAW, mesmo se o próprio aplicativo for executado em um sistema operacional diferente do Windows ou em uma plataforma de nuvem que não seja da Microsoft.  Por exemplo, o proprietário de uma assinatura do Amazon Web Services só deve usar uma PAW para administrar essa conta.

10. Desenvolva um método de solicitação e a distribuição para implantar as PAWs em larga escala em sua organização.  Dependendo do número de PAWs que você optar por implantar na Fase 2, talvez seja necessário automatizar o processo.

    * Considere o desenvolvimento de um processo de solicitação e aprovação formal para que os administradores usem a fim de obter uma PAW.  Esse processo ajudaria a padronizar o processo de implantação, assegurar a responsabilidade para dispositivos PAW e ajudar a identificar lacunas na implantação da PAW.
    * Conforme mencionado anteriormente, essa solução de implantação deve ser separada dos métodos de automação existentes (que talvez já estejam comprometidos) e deve seguir os princípios descritos na Fase 1.

        > [!NOTE]
        > Qualquer sistema que gerencie os recursos deve ser ele próprio gerenciado no mesmo nível de confiança ou superior.

11. Revise e, se for necessário, implante perfis de hardware de PAW adicionais.  Talvez o perfil de hardware que você escolheu para implantação da Fase 1 não seja adequado para todos os administradores.  Revise os perfis de hardware e, se for apropriado, selecione perfis de hardware de PAW adicionais, a fim de atender às necessidades dos administradores.  Por exemplo, o perfil de Hardware dedicado (separar PAW das estações de trabalho de uso diário) pode ser inadequado para um administrador que viaja frequentemente. Nesse caso, você pode optar por implantar o perfil de Uso simultâneo (PATA com VM de usuário) para esse administrador.
12. Considere as necessidades culturais, operacionais, comunicações e de treinamento que acompanham uma implantação de PAW estendida.   Uma alteração considerável em um modelo administrativo naturalmente exigirá um certo nível de gerenciamento de mudanças, e é essencial agregar isso ao próprio projeto de implantação.  Considere no mínimo o seguinte:

    * Como você comunicará as alterações à liderança sênior para garantir o apoio dela?  Qualquer projeto sem o apoio da liderança sênior provavelmente falhará ou, no máximo, terá dificuldades de financiamento e ampla aceitação.
    * Como você documentará o novo processo para administradores?  Essas alterações devem ser documentadas e comunicadas não apenas aos administradores existentes (que devem mudar seus hábitos e gerenciar os recursos de forma diferente), mas também para novos administradores (aqueles promovidos de dentro ou contratados de fora da organização).  É essencial que a documentação esteja clara e enfatize totalmente a importância das ameaças, a função da PAW na proteção dos administradores e como usar a PAW corretamente.

      > [!NOTE]
      > Isso é especialmente importante para funções com alta rotatividade, incluindo, mas sem limitação, a equipe de suporte técnico.

    * Como você garantirá a conformidade com o novo processo?  Enquanto o modelo PAW inclua diversos controles técnicos para evitar a exposição de credenciais com altos privilégios, é impossível evitar totalmente toda exposição possível usando unicamente controles técnicos.  Por exemplo, embora seja possível evitar que um administrador faça logon em um desktop de usuário com credenciais privilegiadas, o simples ato de tentar o logon pode expor as credenciais a algum malware instalado desse desktop de usuário.  Portanto, é essencial que você descreva, além dos benefícios do modelo da PAW, os riscos da não conformidade.  Isso deve ser complementado por auditoria e alertas, para que a exposição de credencial possa ser detectada e resolvida rapidamente.

### <a name="phase-3-extend-and-enhance-protection"></a>Fase 3: Estender e aprimorar a proteção

Escopo: Essas proteções aprimoram os sistemas desenvolvidos na fase 1, reforçando a proteção básica com recursos avançados, incluindo a autenticação multifator e regras de acesso de rede.

> [!NOTE]
> Essa fase pode ser executada a qualquer momento após a conclusão da Fase 1.  Ela não depende da conclusão da Fase 2 e, portanto, pode ser realizada antes, simultaneamente ou após a Fase 2.

Execute as etapas abaixo para configurar essa fase:

1. **Habilitar a autenticação multifator para contas com privilégios**.  A autenticação multifator reforça a segurança da conta exigindo que o usuário forneça um token físico além das credenciais.  A autenticação multifator complementa muito bem as políticas de autenticação, mas não depende de políticas de autenticação para a implantação (e, da mesma forma, as políticas de autenticação não exigem autenticação multifator).  A Microsoft recomenda o uso de uma destas formas de autenticação multifator:

   * **Cartão inteligente**: Um cartão inteligente é um dispositivo físico portátil e inviolável que fornece uma segunda verificação durante o processo de logon do Windows.  Ao exigir que um indivíduo possua um cartão para o logon, você pode reduzir o risco de reutilização remota das credenciais roubadas.  Para saber mais sobre o logon com cartão inteligente no Windows, consulte o artigo [Visão geral do cartão inteligente](https://technet.microsoft.com/library/hh831433.aspx).
   * **Cartão inteligente virtual**:  Um cartão inteligente virtual fornece os mesmos benefícios de segurança como cartões inteligentes físicos, com o benefício adicional de ser vinculado a um hardware específico.  Para obter detalhes sobre a implantação e requisitos de hardware, consulte os artigos [visão geral do cartão inteligente Virtual](https://technet.microsoft.com/library/dn593708.aspx) e [começar com os cartões inteligentes virtuais: Guia passo a passo](https://technet.microsoft.com/library/dn579260.aspx).
   * **Windows Hello para empresas**: Windows Hello para empresas permite que os usuários autentiquem uma conta da Microsoft, uma conta do Active Directory, uma conta do Microsoft Azure Active Directory (Azure AD) ou serviço não são da Microsoft que oferece suporte à autenticação de ID FIDO (Fast Online). Após uma verificação inicial em duas etapas durante o Windows Hello para o registro de negócios, um Windows Hello para empresas está configurado no dispositivo do usuário e o usuário configura um gesto, que pode ser o Windows Hello ou um PIN. Windows Hello para credenciais de negócios são um par de chaves assimétricas, que pode ser gerado em ambientes isolados do Trusted Platform Modules (TPMs).
      Para obter mais informações sobre o Windows Hello para leitura de negócios [Windows Hello para empresas](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification) artigo.
   * **Autenticação multifator do Azure**:  A autenticação multifator (MFA) fornece a segurança de um segundo fator de verificação, bem como proteção aprimorada por meio de monitoramento baseados em aprendizado de máquina e análise.  A MFA do Azure pode proteger não só os administradores do Azure, mas muitas outras soluções, incluindo aplicativos Web, Azure Active Directory e soluções locais, como o acesso remoto e Área de Trabalho Remota.  Para saber mais sobre a autenticação multifator do Azure, consulte o artigo [Autenticação multifator](https://azure.microsoft.com/services/multi-factor-authentication).

2. **Inclua aplicativos usando o Windows Defender Application Control e/ou AppLocker confiáveis**.  Ao limitar a capacidade do código não confiável ou não assinado executar em uma PAW, você reduz ainda mais a probabilidade de atividade mal-intencionada e comprometimento.  O Windows inclui duas opções principais para controle de aplicativo:

   * **AppLocker**:  O AppLocker ajuda os administradores a controlar quais aplicativos podem ser executados em um determinado sistema.  O AppLocker pode ser controlado centralmente pela política de grupo, e aplicado a usuários ou grupos específicos (para aplicativos direcionados a usuários de PAWs).  Para saber mais sobre como o AppLocker, consulte o artigo da TechNet [Visão geral do AppLocker](https://technet.microsoft.com/library/hh831440.aspx).
   * **Windows Defender Application Control**: o novo recurso do Windows Defender Application Control fornece controle aprimorado de aplicativos com base em hardware que, ao contrário do AppLocker, não pode ser substituído no dispositivo afetado.  Como o AppLocker, o Windows Defender Application Control pode ser controlado por meio da diretiva de grupo e direcionado a usuários específicos.  Para obter mais informações sobre como restringir o uso do aplicativo com o Windows Defender Application Control, consulte [guia de implantação do controle de aplicativos do Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide).

3. **Use Usuários Protegidos, Políticas de Autenticação e Silos de Autenticação para proteger ainda mais as contas privilegiadas**.  Os membros de Usuários Protegidos estão sujeitos a políticas de segurança adicionais que protegem as credenciais armazenadas no agente de segurança local (LSA) e reduz bastante o risco de roubo e reutilização de credenciais.  Políticas e silos de autenticação controlam como os usuários privilegiados podem acessar recursos no domínio.  Coletivamente, essas proteções fortalecem consideravelmente a segurança da conta desses usuários privilegiados.  Para saber mais sobre esses recursos, consulte o artigo da Web [Como configurar contas protegidas](https://technet.microsoft.com/library/dn518179.aspx).

   > [!NOTE]
   > Essas proteções são complementares e não substituem as medidas existentes de segurança na Fase 1.  Os administradores ainda devem usar contas separadas para administração e uso geral.

## <a name="managing-and-updating"></a>Gerenciamento e atualização

As PAWs devem ter recursos antimalware, e as atualizações de software devem ser aplicadas rapidamente a fim de manter a integridade dessas estações de trabalho.

Gerenciamento de configuração adicional, monitoramento operacional e gerenciamento de segurança também podem ser usados com PAWs, mas a integração deles deve ser considerada com cuidado, pois cada recurso de gerenciamento também introduz o risco de comprometimento da PAW por meio dessa ferramenta. Se faz sentido introduzir recursos avançados de gerenciamento depende de vários fatores, incluindo:

* O estado de segurança e práticas do recurso de gerenciamento (incluindo práticas de atualização de software para a ferramenta, contas e funções administrativas nessas funções, sistemas operacionais nos quais ferramenta está hospedada ou dos quais é gerenciada e quaisquer outras dependências de hardware ou software dessa ferramenta)
* A frequência e a quantidade de implantações de software e atualizações em suas PAWs
* Requisitos para obter informações detalhadas de inventário e configuração
* Requisitos de monitoramento de segurança
* Padrões organizacionais e outros fatores organizacionais específicos

De acordo com o princípio da origem limpa, todas as ferramentas usadas para gerenciar ou monitorar as PAWs devem ser confiáveis no nível das PAWs, ou acima dele. Isso geralmente exige que essas ferramentas sejam gerenciadas de uma PAW para garantir a ausência de dependência de segurança de estações de trabalho com privilégios inferiores.

Esta tabela descreve as diferentes abordagens que podem ser usadas para gerenciar e monitorar as PAWs:

|Abordagem|Considerações|
|------|---------|
|Padrão na PAW<br /><br />-   Windows Server Update Services<br />-   Windows Defender|-   Sem custo adicional<br />-   Realiza funções básicas de segurança necessárias<br />-   Instruções incluídas neste guia|
|Gerenciar com o [Intune](https://technet.microsoft.com/library/jj676587.aspx)|<ul><li>Fornece controle e visibilidade com base na nuvem<br /><br /><ul><li>Implantação de software</li><li>o   Gerenciar atualizações de software</li><li>Gerenciamento de política de firewall do Windows</li><li>Proteção antimalware</li><li>Assistência Remota</li><li>Gerenciamento de licenças de software.</li></ul></li><li>Nenhuma infraestrutura de servidor é necessária</li><li>Exige as seguintes etapas de "Habilitar a conectividade para serviços de nuvem" na Fase 2</li><li>Se o computador PAW não tiver ingressado em um domínio, será necessário aplicar as linhas de base de SCM às imagens locais usando as ferramentas fornecidas no download de linha de base de segurança.</li></ul>|
|Novas instâncias do System Center para gerenciar PAWs|-   Oferece visibilidade e controle de configuração, implantação de software e atualizações de segurança<br />-   Exige infraestrutura de servidor separada, protegendo-a no nível das PAWs e qualificações de equipe para os funcionários altamente privilegiados|
|Gerenciar PAWs com ferramentas de gerenciamento existentes|-Cria um risco significativo para comprometimento das PAWs, a menos que a infraestrutura de gerenciamento existente seja levada até o nível de segurança das PAWs **Observação:**     Microsoft geralmente não incentivo essa abordagem, a menos que sua organização tenha um motivo específico para usá-lo. Em nossa experiência, normalmente há um custo muito alto de colocar todas essas ferramentas (e suas dependências de segurança) até o nível de segurança das PAWs.<br />-   A maioria dessas ferramentas oferece visibilidade e controle de configuração, implantação de software e atualizações de segurança|
|Ferramentas de Verificação de Segurança ou monitoramento precisam de acesso de administrador|Inclui qualquer ferramenta que instala um agente ou exige uma conta com acesso administrativo local.<br /><br />-   Exige que a garantia de segurança da ferramenta seja levada até o nível das PAWs.<br />-   Pode exibir uma postura de segurança inferior das PAWs a fim de oferecer suporte à funcionalidade da ferramenta (abrir portas, instalar Java e outro middleware etc.), criando uma decisão de compensação de segurança,|
|SIEM (Gerenciamento de informações e eventos de segurança)|<ul><li>Se a SIEM não tiver um agente<br /><br /><ul><li>Pode acessar eventos nas PAWs sem acesso administrativo usando uma conta do grupo **Leitores de Log de Eventos**</li><li>Exigirá a abertura das portas de rede a fim de permitir o tráfego de entrada dos servidores SIEM</li></ul></li><li>Se a SIEM exigir um agente, consulte outra linha: **Ferramentas de Verificação de Segurança ou monitoramento que precisam de acesso administrativo**.</li></ul>|
|Windows Event Forwarding|-   Fornece um método sem agente de encaminhamento de eventos de segurança das PAWs para um coletor externo ou SIEM<br />-  Pode acessar eventos em PAWs sem acesso administrativo<br />-   Não exige a abertura das portas de rede a fim de permitir o tráfego de entrada dos servidores SIEM|

## <a name="operating-paws"></a>Operação das PAWs

A solução PAW deve ser operada usando os padrões em [Padrões operacionais](https://aka.ms/securitystandards) com base no Princípio da origem limpa.

## <a name="deploy-paws-using-a-guarded-fabric"></a>Implantar as PAWs usando uma malha protegida

Um [protegidos do fabric](https://aka.ms/shieldedvms) pode ser usado para executar cargas de trabalho PAW em uma máquina virtual blindada em um laptop ou servidor de salto.
Adotar essa abordagem requer extra de infra-estrutura e etapas operacionais, mas pode tornar mais fácil reimplantar PAW imagens em intervalos regulares e lhe permite consolidar várias PAWs diferentes de em camadas (ou classificações) em máquinas virtuais em execução lado a lado em um único dispositivo.
Para obter uma explicação completa sobre as promessas de segurança e a topologia de malha protegida, consulte o [documentação de malha protegida](https://aka.ms/shieldedvms).

### <a name="changes-to-the-paw-gpos"></a>Alterações nos GPOs de PAW

Ao usar blindadas baseadas em VM PAWs, o [configurações de GPO recomendadas](#create-paw-configuration---computer-group-policy-object-gpo) definido acima precisará ser modificado para suporte ao uso de máquinas virtuais.

1. Crie uma nova UO para os hosts físicos da PAW. PAWs físicas e virtuais têm requisitos de segurança diferentes e devem ser separadas adequadamente no Active Directory.
2. O GPO de computador PAW deve ser vinculado a ambos os físicos e virtuais da PAW UOs.
3. Crie um novo GPO da paw físico adicionar os usuários PAW para o grupo de administradores do Hyper-V. Isso é necessário para permitir que os administradores para se conectar ao administrador de VMs e ligá-los de ativar/desativar conforme necessário. É importante que o registro de usuário em PAW físico não tem direitos de administrador, acesso à internet ou a capacidade de copiar dados de máquina virtual mal-intencionada de compartilhamentos de rede ou dispositivos de armazenamento externo à paw físico.
4. Crie um novo GPO para o administrador de VMs para adicionar usuários PAW ao grupo usuários da área de trabalho remota. Isso permitirá que os usuários a usar o Hyper-V aprimorada sessões do Console, que oferecem uma melhor experiência de usuário e permite a passagem de cartão inteligente para a máquina virtual.

### <a name="set-up-the-host-guardian-service"></a>Configurar o serviço guardião de Host

Serviço guardião de Host é responsável por atestar a identidade e a integridade de um dispositivo físico da PAW.
Somente as máquinas que são conhecidas por HGS e executando um confiável [política de integridade de código](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) têm permissão para iniciar o backup de VMs blindadas.
Isso ajuda a proteger as VMs blindadas, o qual executam cargas de trabalho confiáveis para gerenciar seus recursos em camadas, contra ameaças do ambiente de desktop de usuário.

Como o HGS é responsável por determinar quais dispositivos podem executar VMs da PAW, ele é considerado um recurso de nível 0.
Ele deve ser implantado juntamente com outros recursos de camada 0 e protegido contra acesso não autorizado de físico e lógico.
HGS é uma função clusterizada, tornando mais fácil para escalar horizontalmente para a implantação de qualquer tamanho.
A regra geral é planejar 1 servidor HGS para cada 1.000 dispositivos que você tem, com um mínimo de 3 nós.

1. Para instalar seu primeiro servidor HGS, inicie com o [HGS instalar - floresta de bastiões](../../security/guarded-fabric-shielded-vm/guarded-fabric-install-hgs-in-a-bastion-forest.md) do artigo e ingresse HGS para seu domínio de nível 0.

2. Em seguida, [criar certificados para HGS](../../security/guarded-fabric-shielded-vm/guarded-fabric-obtain-certs.md) usando sua autoridade de certificação corporativa.
Qualquer pessoa em posse da criptografia HGS e certificados de assinatura pode descriptografar uma VM blindada, portanto, se você tiver acesso a um módulo de segurança de Hardware para proteger as chaves privadas, é recomendável que você gerar esses certificados usando um HSM.
Para aumentar a segurança, selecione um tamanho de chave maior que ou igual a 4096 bits.

3. Por fim, siga as etapas a serem [inicializar seu servidor HGS](../../security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-bastion.md) na **TPM modo**.
Inicialização configura o Atestado e serviços da web de proteção de chave usados pelo seu PAWs.
HGS deve estar [configurado com um certificado TLS](../../security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https.md) para proteger essas comunicações e somente a porta 443 deverá ser aberta de redes não confiáveis para HGS.

4. Siga as etapas para [adicionar nós adicionais](../../security/guarded-fabric-shielded-vm/guarded-fabric-configure-additional-hgs-nodes.md) para sua segunda, terceiro, adicionais e nós HGS.

5. Se seu servidor HGS está executando o Windows Server 2019 ou posterior, você pode habilitar um recurso opcional para armazenar em cache as chaves para VMs blindadas em PAWs para que possam ser usados offline. As chaves são lacradas para a configuração de segurança atual do sistema para impedir que alguém use chaves armazenadas em cache em outro computador ou no mesmo computador em um estado inseguro. Isso pode ser uma solução útil se os usuários PAW viajam sem acesso à Internet, mas ainda precisará ser capaz de fazer logon em suas VMs da PAW. Para usar esse recurso, execute o seguinte comando em qualquer servidor HGS:

      ```powershell
      Set-HgsKeyProtectionConfiguration -AllowKeyMaterialCaching:$true
      ```

### <a name="set-up-the-physical-paw-device"></a>Configurar o dispositivo físico de PAW

O dispositivo físico da PAW é considerado não confiável por padrão na solução de malha protegida.
Ele pode provar que ele seja confiável durante o processo de Atestado, após o qual ele pode obter as chaves necessárias para iniciar uma VM blindada de administração.
O dispositivo deve ser capaz de executar o Hyper-V e tem inicialização segura e um TPM 2.0 habilitado para atender a [pré-requisitos de host protegido](../../security/guarded-fabric-shielded-vm/guarded-fabric-guarded-host-prerequisites.md).
É a versão mínima do sistema operacional para dar suporte a todas as funcionalidades PAW **Windows 10 versão 1803**.

A PAW física deve ser configurada como qualquer outro, com exceção de que todos os usuários PAW precisará ser administradores do Hyper-V para ser capaz de ativar o administrador da VM e conectá-lo.
Em seu ambiente de sala limpa, você precisará criar uma configuração de ouro para cada combinação exclusiva de hardware/software que você está implantando como hosts protegidos do admin VMs.
Em cada configuração de ouro, conclua as seguintes tarefas:

1. Instale as atualizações mais recentes para Windows, drivers e firmware na máquina, bem como qualquer gerenciamento de terceiros ou agentes de monitoramento.
2. [Capturar as informações de linha de base necessária](../../security/guarded-fabric-shielded-vm/guarded-fabric-tpm-trusted-attestation-capturing-hardware.md), incluindo o identificador exclusivo TPM (chave de endosso), inicialização medidas (log TCG) e política de integridade para a máquina de código.
3. Copie esses artefatos para um servidor HGS e execute os comandos de Atestado do HGS no artigo anterior para registrar o host. Se todos os hosts usam a mesma política de integridade de código e/ou usam a mesma configuração de hardware, você precisará registrar o log TCG/política de integridade de código uma vez.

### <a name="create-the-signed-template-disk"></a>Criar o disco de modelo assinado

VMs blindadas são criadas usando discos de modelo assinado.
A assinatura é verificada no momento da implantação para verificar a integridade do disco e a autenticidade antes de liberar os segredos, como a senha de administrador na VM.

Para criar um disco de modelo assinado, siga as etapas de implantação da fase 1 na regular, máquina virtual de geração 2.
Esta máquina se tornará a imagem dourada uma VM de administrador.
Você pode criar mais de um disco de modelo para ter especializada em ferramentas disponíveis em diferentes contextos.

Quando a VM estiver configurada como desejado, execute `C:\Windows\System32\sysprep\sysprep.exe` e escolher **Generalize** o disco. **Desligar** o sistema operacional quando a generalização é concluída.

Por fim, execute as [Assistente de modelo de disco](../../security/guarded-fabric-shielded-vm/guarded-fabric-create-a-shielded-vm-template.md) no arquivo VHDX da VM para instalar os componentes do BitLocker e gerar a assinatura do disco.

#### <a name="create-the-shielding-data-file"></a>Criar o arquivo de dados de blindagem

O disco de modelo generalizado é emparelhado com um arquivo de dados de blindagem, que contém os segredos necessários para provisionar uma VM blindada.
O arquivo de dados de blindagem inclui:
   - Uma lista dos guardiões, que definem as malhas onde a VM pode ser executado. Cada cluster HGS é um guardião para dispositivos PAW protegidos por ele.
   - Uma lista de assinaturas de disco confiável para a implantação. Arquivos de dados de blindagem só liberará seus segredos para VMs criadas usando a mídia de origem autorizada.
   - Uma política de segurança que determina se as proteções adicionais devem ser colocadas em vigor para proteger a VM do host e se a VM tem permissão para mover para outro computador. Administrador PAW VMs deve sempre totalmente protegido.
   - O arquivo de especialização de Unattend. XML, que permite que o Windows concluir a instalação automaticamente e inclui segredos, como a senha do administrador local.
   - Arquivos adicionais, como certificados RDP ou VPN.

Consulte a [artigo do arquivo de dados de blindagem](../../security/guarded-fabric-shielded-vm/guarded-fabric-tenant-creates-shielding-data.md) para obter etapas sobre como criar um arquivo de dados de blindagem.

As chaves de proprietário para as VMs blindadas são extremamente sensíveis e devem ser mantidas em um HSM ou armazenadas offline em um local seguro.
Eles podem ser usados em um cenário de vidro de quebra de emergência para inicializar uma VM blindada sem a presença do HGS.

É altamente recomendável que os dados para o administrador PAW de blindagem VMs incluem a configuração para bloquear uma VM para o primeiro host físico onde ele é inicializado.
Isso impedirá que alguém movendo uma VM de administração de uma PAW para PAW outro no mesmo ambiente.
Para usar esse recurso, crie o arquivo de dados de blindagem com o PowerShell e inclua o **BindToHostTpm** parâmetro:

```powershell
New-ShieldingDataFile -Policy Shielded -BindToHostTpm [...]
```

#### <a name="deploy-an-admin-vm"></a>Implantar uma VM de administração

Depois que o disco de modelo e o arquivo de dados de blindagem estiverem prontos, você pode implantar uma VM em qualquer PAW que foi registrada com o HGS de administração.

1. Copie o disco de modelo (. vhdx) e o arquivo de dados de blindagem (. PDK) para um dispositivo confiável da PAW.
2. Siga as instruções para [implantar uma nova VM blindada usando o PowerShell](../../security/guarded-fabric-shielded-vm/guarded-fabric-create-a-shielded-vm-using-powershell.md)
3. Conclua as etapas restantes na fase 1 do processo de implantação para proteger o sistema operacional da VM e configurá-lo para sua função pretendida, conforme apropriado.


## <a name="related-topics"></a>Tópicos relacionados

[Serviços de segurança cibernética da Microsoft envolventes](https://www.microsoft.com/en-us/microsoftservices/campaigns/cybersecurity-protection.aspx)

[Taste of Premier: Como mitigar Pass-the-Hash e outras formas de roubo de credenciais](https://channel9.msdn.com/Blogs/Taste-of-Premier/Taste-of-Premier-How-to-Mitigate-Pass-the-Hash-and-Other-Forms-of-Credential-Theft)

[Microsoft Advanced Threat Analytics](https://aka.ms/ata)

[Proteger as credenciais de domínio derivadas com o Credential Guard](https://technet.microsoft.com/library/mt483740%28v=vs.85%29.aspx)

[Visão geral de proteção do dispositivo](https://technet.microsoft.com/library/dn986865(v=vs.85).aspx)

[Proteger ativos de alto valor com estações de trabalho de administração seguras](https://msdn.microsoft.com/library/mt186538.aspx)

[Modo de usuário isolado no Windows 10 com Dave Probert (Channel 9)](https://channel9.msdn.com/Blogs/Seth-Juarez/Isolated-User-Mode-in-Windows-10-with-Dave-Probert)

[Isolado processos de modo de usuário e recursos no Windows 10, com Logan Gabriel (Channel 9)](http://channel9.msdn.com/Blogs/Seth-Juarez/Isolated-User-Mode-Processes-and-Features-in-Windows-10-with-Logan-Gabriel)

[Mais sobre processos e recursos no modo de usuário isolado do Windows 10 com Dave Probert (Channel 9)](https://channel9.msdn.com/Blogs/Seth-Juarez/More-on-Processes-and-Features-in-Windows-10-Isolated-User-Mode-with-Dave-Probert)

[Atenuação de roubo de credenciais usando o Windows 10 modo de usuário isolado (Channel 9)](https://channel9.msdn.com/Blogs/Seth-Juarez/Mitigating-Credential-Theft-using-the-Windows-10-Isolated-User-Mode)

[Habilitar a validação de KDC estrita no Kerberos do Windows](https://www.microsoft.com/en-us/download/details.aspx?id=6382)

[O que há de novo na autenticação Kerberos para Windows Server 2012](https://technet.microsoft.com/library/hh831747.aspx)

[Garantia do mecanismo de autenticação do AD DS no guia passo a passo do Windows Server 2008 R2](https://technet.microsoft.com/library/dd378897(v=ws.10).aspx)

[Trusted Platform Module](C:/sd/docs/p_ent_keep_secure/p_ent_keep_secure/trusted_platform_module_technology_overview.xml)
