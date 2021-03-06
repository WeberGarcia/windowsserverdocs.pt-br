---
title: Serviço de hospedagem da área de trabalho
description: Descreve os componentes de um serviço de hospedagem da área de trabalho.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: helohr
ms.date: 07/06/2018
ms.tgt_pltfrm: na
ms.topic: article
author: heidilohr
manager: dougkim
ms.openlocfilehash: 597016ecf10da0febb7ba1bb099da0c1dddf96ce
ms.sourcegitcommit: 3743cf691a984e1d140a04d50924a3a0a19c3e5c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2019
ms.locfileid: "63749227"
---
# <a name="desktop-hosting-service"></a>Serviço de hospedagem da área de trabalho

>Aplica-se a: Windows Server (Canal Semestral), Windows Server 2019, Windows Server 2016

Este artigo explicará a você mais sobre os componentes do serviço de hospedagem da área de trabalho.

## <a name="tenant-environment"></a>Ambiente de locatário

Conforme descrito em [Funções de Serviços de Área de Trabalho Remota](rds-roles.md), cada função desempenha um papel distinto no ambiente de locatário.

O serviço de hospedagem da área de trabalho do provedor é implementado como um conjunto de ambientes de locatários isolados. O ambiente de cada locatário consiste em um contêiner de armazenamento, um conjunto de máquinas virtuais e uma combinação de serviços do Azure, tudo se comunicando sobre uma rede virtual isolada. Cada máquina virtual contém um ou mais dos componentes que compõem o ambiente de área de trabalho hospedada do locatário. As subseções a seguir descrevem os componentes que compõem o ambiente de área de trabalho hospedada de cada locatário.

## <a name="active-directory-domain-services"></a>Active Directory Domain Services

AD DS (Active Directory Domain Services) fornece as informações de domínio e floresta, de modo que os usuários do locatário possam entrar em áreas de trabalho desktops e aplicativos para executar as cargas de trabalho deles. Isso também permite que você configure ou conecte a compartilhamentos de arquivos e bancos de dados necessários que podem ser exigidos para aplicativos do Windows.

A floresta do locatário não exige qualquer relação de confiança com a floresta de gerenciamento do provedor. Uma conta de administrador de domínio pode ser configurada no domínio do locatário para permitir que a equipe de suporte técnico do provedor execute tarefas administrativas no ambiente do locatário (tais como monitorar o status do sistema e aplicar atualizações de software) e para ajudar com solução de problemas e configuração.

Há várias maneiras de implantar o AD DS:

1. Habilitar o Active Directory Domain Services do Azure no ambiente de rede virtual do locatário. Isso criará uma instância gerenciada do AD DS para o locatário com base nos usuários e grupos que existem no Azure AD.
2. Configure um servidor AD DS autônomo no ambiente de rede virtual do locatário. Isso fornece todo o controle completo da instância AD DS em execução nas máquinas virtuais.
3. Crie uma conexão de VPN site a site para um servidor AD DS localizado no local do locatário. Isso permite ao locatário conectar à instância AD DS existente e reduzir a duplicação de usuários, grupos, unidades organizacionais e assim por diante.

Para obter mais informações, consulte os seguintes artigos:

* [Documentação do Azure Active Directory Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/)
* [Guia de Arquitetura de Referência de Hospedagem da Área de Trabalho para Windows Server 2012 R2](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal)
* [Criar uma conexão site a site no portal do Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal)

## <a name="sql-database"></a>Banco de dados SQL

O Banco de Dados SQL do Azure é usado pelo Agente de Conexão da Área de Trabalho Remota para armazenar informações de implantação, como o mapeamento das conexões dos usuários atuais com os servidores host.

Há várias maneiras de implantar um banco de dados SQL:

1. Criar um Banco de Dados SQL do Azure no ambiente do locatário. Isso fornece a funcionalidade de um banco de dados SQL redundante sem a necessidade de gerenciar os próprios servidores. Isso também permite que você pague pelo que consumir em vez de investir na infraestrutura.
2. Criar um cluster AlwaysOn do SQL Server. Isso permite que você aproveite a infraestrutura existente do SQL Server e fornece controle total sobre as instâncias do SQL Server.

Para obter mais informações sobre como configurar uma infraestrutura altamente disponível do banco de dados SQL, consulte os artigos a seguir:

* [O que é o serviço de Banco de Dados SQL do Azure?](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
* [Criação e configuração de grupos de disponibilidade (SQL Server)](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server?view=sql-server-2017).
* [Adicionar o servidor do Agente de Conexão de Área de Trabalho Remota à implantação e configurar a alta disponibilidade](rds-connection-broker-cluster.md).

## <a name="file-server"></a>Servidor de arquivos

O servidor de arquivos usa o protocolo SMB (Server Message Block) 3.0 para fornecer pastas compartilhadas. Essas pastas compartilhadas são usadas para criar e armazenar arquivos de disco de perfil do usuário (.vhdx), fazer backup de dados e permitir que os usuários compartilhem dados uns com os outros dentro do serviço de nuvem do locatário.

A máquina virtual usada para implantar o servidor de arquivos deve ter um disco de dados do Azure conectado e configurado com pastas compartilhadas. Os discos de dados do Azure usam cache com write-through, garantindo que as gravações no disco não serão apagadas sempre que a máquina virtual é reiniciada.

Locatários pequenos podem reduzir os custos ao combinar o servidor de arquivos e a [função de Licenciamento de Área de Trabalho Remota](rds-roles.md#remote-desktop-licensing) em uma única máquina virtual no ambiente do locatário.

Para obter mais informações, consulte os seguintes artigos:

* [Armazenamento no Windows Server](../../storage/storage.md)
* [Como anexar um disco de dados gerenciado a uma VM do Windows no portal do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/attach-managed-disk-portal?toc=%2Fazure%2Fvirtual-machines%2Fwindows%2Fclassic%2Ftoc.json)

### <a name="user-profile-disks"></a>Discos de perfil do usuário

Discos de perfil de usuário permitem que os usuários salvem arquivos e configurações pessoais quando estão conectados a uma sessão em um servidor Host da Sessão da Área de Trabalho Remota em uma coleção e, em seguida, acessam as mesmas configurações e arquivos ao entrar em um servidor [Host da Sessão da Área de Trabalho Remota](rds-roles.md#remote-desktop-session-host) diferente na coleção. Quando o usuário entra pela primeira vez, o servidor de arquivos do locatário cria um disco de perfil de usuário e esse disco é montado no servidor Host da Sessão da Área de Trabalho Remota que o usuário está conectado atualmente. Para cada entrada subsequente, o disco de perfil de usuário é montado no servidor Host da Sessão da Área de Trabalho Remota apropriado e é desmontado com cada saída. Somente o usuário pode acessar o conteúdo do disco de perfil.