---
title: Escolha um tipo de namespace
description: Este artigo descreve como escolher um tipo de um namespace.
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: f83be7b2ec7dbe2383deb2d0a79e33d7c73f8849
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873797"
---
# <a name="choose-a-namespace-type"></a>Escolha um tipo de namespace

> Aplica-se a: Windows Server 2019, Windows Server (canal semestral), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

Ao criar um namespace, você deve escolher um dos dois tipos de namespace: um namespace autônomo ou um namespace baseado em domínio. Além disso, se você escolher um namespace baseado em domínio, você deve escolher um modo de namespace: Modo do Windows 2000 Server ou Windows Server 2008.

## <a name="choosing-a-namespace-type"></a>Escolhendo um tipo de namespace

Escolha um namespace autônomo se alguma das seguintes condições se aplicar ao seu ambiente:

-   Sua organização não usa os serviços de domínio do Active Directory (AD DS).
-   Você deseja aumentar a disponibilidade do namespace usando um cluster de failover.
-   Você precisa criar um único namespace com mais de 5.000 pastas DFS em um domínio que não atende aos requisitos para um namespace baseado em domínio (modo do Windows Server 2008) conforme descrito mais adiante neste tópico.

> [!NOTE]
> Para verificar o tamanho de um namespace, clique com botão direito do namespace na árvore de console de Gerenciamento DFS, clique em **Propriedades** e depois exibe o tamanho de namespace na caixa de diálogo **Propriedades de Namespace**. Para saber mais sobre a escalabilidade do Namespace de DFS, consulte o site da Microsoft [Serviços de arquivo](https://technet.microsoft.com/library/cc771548.aspx).

Escolha um namespace baseado em domínio se alguma das seguintes condições se aplicar ao seu ambiente:

-   Você deseja garantir a disponibilidade do namespace usando vários servidores de namespace.
-   Você deseja esconder o nome do servidor de namespace de usuários. Isso torna mais fácil substituir o servidor de namespace ou migrar o namespace para outro servidor.

## <a name="choosing-a-domain-based-namespace-mode"></a>Escolhendo um mode de namespace baseado em domínio

Se você escolher um namespace baseado em domínio, você deve escolher se deseja usar o modo Windows 2000 Server ou o Windows Server 2008. O modo do Windows Server 2008 inclui suporte para a enumeração baseada em acesso e maior escalabilidade. O namespace baseado em domínio introduzido no Windows 2000 Server agora é conhecido como "baseado em domínio namespaces (modo Windows 2000 Server)".

Para usar o modo do Windows Server 2008, o domínio e o namespace devem atender aos seguintes requisitos mínimos:

-   A floresta usa o Windows Server 2003 ou nível funcional de floresta superior.
-   O domínio usa o Windows Server 2008 ou o mais alto nível funcional do domínio.
-   Todos os servidores de namespace estão executando o Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 ou Windows Server 2008.

Se seu ambiente permitirem, escolha o modo do Windows Server 2008 quando você cria novos namespaces baseados em domínio. Esse modo oferece escalabilidade e recursos adicionais e também elimina a possível necessidade de migrar um namespace do modo do Windows 2000 Server.

Para obter informações sobre como migrar um namespace para o modo do Windows Server 2008, consulte [migrar um Namespace baseado em domínio para o modo do Windows Server 2008](migrate-a-domain-based-namespace-to-windows-server-2008-mode.md).

Se seu ambiente não oferece suporte a namespaces baseados em domínio no modo do Windows Server 2008, use o modo Windows 2000 Server existente para o namespace.

## <a name="comparing-namespace-types-and-modes"></a>Comparando modos e tipos de namespace

As características de cada tipo de namespace e o modo são descritos na tabela a seguir.

|Característica|Namespace autônomo|Namespace baseado em domínio (modo Windows 2000 Server) |Namespace baseado em domínio (modo Windows 2008 Server) | 
|---|---|---|---|
|Caminho ao namespace|\\\ *ServerName\RootName* |\\\ *NetBIOSDomainName\RootName* <br />\\\ *DNSDomainName\RootName*|\\\ *NetBIOSDomainName\RootName* <br /> \\\ *DNSDomainName\RootName*|
|Local de armazenamento de informações de Namespace|No registro e em um cache de memória no servidor de namespace|No AD DS e em um cache de memória em cada servidor de namespace|No AD DS e em um cache de memória em cada servidor de namespace|
|Recomendações de tamanho de Namespace|O namespace pode conter mais de 5.000 pastas com destinos; o limite recomendado é 50.000 pastas com destinos|O tamanho do objeto do namespace no AD DS deve ser menor que 5 megabytes (MB) para manter a compatibilidade com controladores de domínio que não estejam executando o Windows Server 2008. Isso significa não mais do que aproximadamente 5.000 pastas com destinos.|O namespace pode conter mais de 5.000 pastas com destinos; o limite recomendado é 50.000 pastas com destinos |
|Nível funcional de floresta do AD DS mínimos|AD DS não é obrigatório|Windows 2000|Windows Server 2003|
|Nível funcional de domínio do AD DS mínimos|AD DS não é obrigatório|Windows 2000 misto|Windows Server 2008|
|Servidores de namespace com suporte mínimo|Windows 2000 Server|Windows 2000 Server|Windows Server 2008|
|Suporte para enumeração baseada em acesso (se habilitado)|Sim, requer o servidor de namespace do Windows Server 2008|Não|Sim|
|Métodos com suporte para garantir a disponibilidade de namespace|Crie um namespace autônomo em um cluster de failover.|Use vários servidores de namespace para hospedar o namespace. (Os servidores de namespace devem ser no mesmo domínio.)|Use vários servidores de namespace para hospedar o namespace. (Os servidores de namespace devem ser no mesmo domínio.)|
|Suporte para usar replicação de DFS para replicar alvos de pasta|Suportado quando tiver ingressado em um domínio do AD DS|Com suporte|Com suporte|

## <a name="see-also"></a>Consulte também

-   [Implantando os Namespaces do DFS](deploying-dfs-namespaces.md)
-   [Migrar um Namespace baseado em domínio para o modo do Windows Server 2008](migrate-a-domain-based-namespace-to-windows-server-2008-mode.md)


