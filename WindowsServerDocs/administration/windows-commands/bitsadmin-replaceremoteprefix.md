---
title: bitsadmin replaceremoteprefix
description: Tópico de comandos do Windows para **bitsadmin replaceremoteprefix** -todos os arquivos no trabalho cujo URL remota começa com *OldPrefix* são alteradas para usar *NewPrefix*.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0e0abb1-bdb4-4c74-abbc-16c809f5fd81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 25c0f997ea0b9f97051baa291bdf87c84b6b1cbb
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66811301"
---
# <a name="bitsadmin-replaceremoteprefix"></a>bitsadmin replaceremoteprefix

Todos os arquivos no trabalho cujo URL remota começa com *OldPrefix* são alteradas para usar *NewPrefix*.

## <a name="syntax"></a>Sintaxe

```
bitsadmin /ReplaceRemotePrefix <Job> <OldPrefix> <NewPrefix
```

## <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------|-----------|
|Job|Nome de exibição ou o GUID do trabalho|
|OldPrefix|Prefixo de URL existente|
|NewPrefix|Novo prefixo de URL|

## <a name="examples"></a>Exemplos

O exemplo a seguir altera todos os arquivos em um trabalho denominado *myDownloadJob* cuja URL remota começa com *http://stageserver* para *http://prodserver* .

```
C:\>bitsadmin /ReplaceRemotePrefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>Informações adicionais

[Chave da sintaxe de linha de comando](command-line-syntax-key.md)