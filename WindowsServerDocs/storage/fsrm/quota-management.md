---
title: Gerenciamento de cota
description: Este artigo descreve como criar e gerenciar cotas
ms.date: 7/7/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 6effaf7c2d197c08b4930e09c3ada96462b17d6f
ms.sourcegitcommit: ed27ddbe316d543b7865bc10590b238290a2a1ad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476187"
---
# <a name="quota-management"></a>Gerenciamento de cota

> Aplica-se a: Windows Server 2019, Windows Server 2016, Windows Server (canal semestral), Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

No nó **Gerenciamento de cota** do snap-in do Console de Gerenciamento Microsoft<sup>®</sup> do Gerenciador de Recursos de Servidor de Arquivos, você pode realizar as seguintes tarefas:

-   Criar cotas para limitar o espaço permitido de um volume ou uma pasta e gerar notificações quando os limites de cota são aproximados ou excedidos.
-   Gerar automaticamente cotas de aplicação automática que se aplicam a todas as subpastas existentes em um volume ou uma pasta e todas as subpastas criadas no futuro.
-   Definir modelos de cota que podem ser facilmente aplicados a novos volumes ou pastas e então usá-los em uma organização.

Por exemplo, você pode:

-   Colocar um limite de 200 megabytes (MB) em pastas de servidor pessoais dos usuários, com uma notificação por email enviada para você e o usuário quando 180 MB de armazenamento foi excedido.
-   Defina uma cota flexível de 500 MB na pasta compartilhada de um grupo. Quando esse limite de armazenamento for atingido, todos os usuários no grupo sejam notificados por email que a cota de armazenamento foi temporariamente estendida para 520 MB para que eles podem excluir arquivos desnecessários e cumprir a política de cota de 500 MB predefinido.
-   Receber uma notificação quando uma pasta temporária atingir 2 gigabytes (GB) de uso, mas não limitar a cota da pasta porque é necessário para um serviço em execução em seu servidor.

Esta seção inclui os seguintes tópicos:

-   [Criar uma cota](create-quota.md)
-   [Criar uma cota de aplicação automática](create-auto-apply-quota.md)
-   [Criar um modelo de cota](create-quota-template.md)
-   [Editar propriedades de modelo de cota](edit-quota-template-properties.md)
-   [Editar propriedades de cota de aplicação automática](edit-auto-apply-quota-properties.md)

> [!Note]
> Para definir notificações por email e recursos de relatório, você deve configurar primeiro as opções gerais do Gerenciador de recursos do servidor de arquivos.

## <a name="see-also"></a>Consulte também

-   [Definir opções do Gerenciador de Recursos de Servidor de Arquivos](setting-file-server-resource-manager-options.md)


