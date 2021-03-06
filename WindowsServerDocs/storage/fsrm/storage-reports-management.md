---
title: Gerenciamento de relatórios de armazenamento
description: Este artigo descreve como gerar, agendar e monitorar relatórios de armazenamento
ms.date: 7/7/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 62215aa802e2509be5305aef53069ae9643562f1
ms.sourcegitcommit: ed27ddbe316d543b7865bc10590b238290a2a1ad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476097"
---
# <a name="storage-reports-management"></a>Gerenciamento de relatórios de armazenamento

> Aplica-se a: Windows Server 2019, Windows Server 2016, Windows Server (canal semestral), Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

No nó **Gerenciamento de relatórios de armazenamento** do snap-in do Console de Gerenciamento Microsoft<sup>®</sup> do Gerenciador de Recursos de Servidor de Arquivos, você pode realizar as seguintes tarefas:

-   Agendar relatórios periódicos que permitem que você identifique tendências no uso do disco.
-   Monitor tenta salvar arquivos não autorizados para todos os usuários ou para um grupo selecionado de usuários.
-   Gerar relatórios de armazenamento instantaneamente.

Por exemplo, você pode:

-   Agendar um relatório que será executado todo domingo à meia-noite, gerando uma lista que inclui os arquivos utilizados mais recentemente dos dois dias anteriores. Com essas informações, você pode monitorar a atividade de armazenamento no fim de semana e planejar o período de atividade do servidor que terá menos impacto sobre os usuários que se conectam de casa no final de semana.
-   Executar um relatório a qualquer momento para identificar todos os arquivos duplicados em um volume em um servidor para que o espaço em disco possa ser recuperado rapidamente sem perder nenhum dado.
-   Executar um arquivo com o relatório de grupo de arquivos para identificar como os recursos de armazenamento estão segmentados em grupos de arquivos diferentes 
-   Executar um relatório de Arquivos por Proprietário para analisar como os usuários individuais estão usando recursos de armazenamento compartilhado.

Esta seção inclui os seguintes tópicos:

-   [Agendar um conjunto de relatórios](schedule-set-of-reports.md)
-   [Gerar relatórios sob demanda](generate-reports-on-demand.md)

> [!Note]
> Para definir notificações por email e determinados recursos de relatório, você deve configurar primeiro as opções gerais do Gerenciador de recursos do servidor de arquivos.

## <a name="see-also"></a>Consulte também

-   [Definir opções do Gerenciador de Recursos de Servidor de Arquivos](setting-file-server-resource-manager-options.md)


