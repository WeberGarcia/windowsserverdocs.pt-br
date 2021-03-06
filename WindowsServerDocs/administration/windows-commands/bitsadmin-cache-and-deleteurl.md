---
title: DeleteUrl e cache bitsadmin
description: Tópico de comandos do Windows para **bitsadmin cache e deleteurl** -exclui todas as entradas de cache para a URL fornecida.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a831c49e1461761cb7466b46e7a5ad8e037f4ec9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816647"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>DeleteUrl e cache bitsadmin



Exclui todas as entradas de cache para a URL fornecida.

## <a name="syntax"></a>Sintaxe

```
bitsadmin /DeleteURL url
```

## <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------|-----------|
|url|A URL que identifica um arquivo remoto.|

## <a name="BKMK_examples"></a>Exemplos

O exemplo a seguir exclui todas as entradas de cache para https://www.microsoft.com/en/us/default.aspx
```
C:\>bitsadmin /DeleteURL https://www.microsoft.com/en/us/default.aspx 
```

#### <a name="additional-references"></a>Referências adicionais

[Chave de sintaxe de linha de comando](command-line-syntax-key.md)