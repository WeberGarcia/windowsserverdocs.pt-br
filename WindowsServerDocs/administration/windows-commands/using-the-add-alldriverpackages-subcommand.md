---
title: Usando o subcomando add AllDriverPackages
description: 'Tópico de comandos do Windows para * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba6641c1-d7e9-43a9-9819-702dad5484ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3f934d8c65da939fb60c564b375699f411b7c9ac
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440828"
---
# <a name="using-the-add-alldriverpackages-subcommand"></a>Usando o subcomando add AllDriverPackages



Adiciona todos os pacotes de driver que são armazenados em uma pasta em um servidor.

## <a name="syntax"></a>Sintaxe

```
WDSUTIL /Add-AllDriverPackages /FolderPath:<Folder Path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>]
```

## <a name="parameters"></a>Parâmetros

|          Parâmetro           |                                                              Descrição                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  /FolderPath:\<Folder Path>  |                      Especifica o caminho completo para a pasta que contém os arquivos. inf para os pacotes de driver.                      |
|   [/Server:\<Server name>]   | Especifica o nome do servidor. Isso pode ser o nome NetBIOS ou FQDN. Se nenhum nome de servidor for especificado, o servidor local será usado. |
|     [/Architecture:{x86      |                                                                 ia64                                                                  |
| [/DriverGroup:\<Group Name>] |                             Especifica o nome do grupo de drivers para o qual os pacotes devem ser adicionados.                             |

## <a name="BKMK_examples"></a>Exemplos

Para adicionar pacotes de driver, digite o seguinte:
```
WDSUTIL /verbose /Add-AllDriverPackages /FolderPath:"C:\Temp\Drivers" /Architecture:x86
```
```
WDSUTIL /Add-AllDriverPackages /FolderPath:"C:\Temp\Drivers\Printers" /DriverGroup:"Printer Drivers"
```

#### <a name="additional-references"></a>Referências adicionais

[Chave da sintaxe de linha de comando](command-line-syntax-key.md)

[Add-WdsDriverPackage](https://technet.microsoft.com/library/dn283440.aspx)