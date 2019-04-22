---
title: bitsadmin getdescription
description: Tópico de comandos do Windows para **bitsadmin getdescription** -recupera a descrição do trabalho especificado.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3974603-ebbe-4d31-8217-040fe2d90c85
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ee20dd808cdbc8b76f44b7b14c9fd65b313a74e5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813127"
---
# <a name="bitsadmin-getdescription"></a>bitsadmin getdescription



Recupera a descrição do trabalho especificado.

## <a name="syntax"></a>Sintaxe

```
bitsadmin /GetDescription <Job>
```

## <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------|-----------|
|Job|Nome de exibição ou o GUID do trabalho|

## <a name="BKMK_examples"></a>Exemplos

O exemplo a seguir recupera a descrição do trabalho nomeado *myDownloadJob*.
```
C:\>bitsadmin /GetDescription myDownloadJob
```

#### <a name="additional-references"></a>Referências adicionais

[Chave de sintaxe de linha de comando](command-line-syntax-key.md)