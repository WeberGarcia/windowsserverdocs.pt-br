---
title: Subcomando DriverGroupFilter conjunto
description: 'Tópico de comandos do Windows para * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 829ab1f0-4514-421e-9cc0-767b238da69c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5423b6e7444c01c5889a5b207a545d1761a73402
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66441144"
---
# <a name="subcommand-set-drivergroupfilter"></a>Subcommand: set-DriverGroupFilter



Adiciona ou remove um filtro de grupo de driver existente de um grupo de drivers.

## <a name="syntax"></a>Sintaxe

```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type> [/Policy:{Include | Exclude}] [/AddValue:<Value> [/AddValue:<Value> ...]] [/RemoveValue:<Value> [/RemoveValue:<Value> ...]]
```

## <a name="parameters"></a>Parâmetros

|         Parâmetro          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Descrição                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /DriverGroup:\<Group Name> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Especifica o nome do grupo de drivers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|  [/Server:\<Server name>]  |                                                                                                                                                                                                                                                                                                                                                                                                                Especifica o nome do servidor. Isso pode ser o nome NetBIOS ou FQDN. Se não for especificado um nome de servidor, o servidor local será usado.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| /FilterType:\<FilterType>  |                                                                                                                                                                                                                                                                       Especifica o tipo de filtro de grupo de driver para adicionar ou remover. Você pode especificar vários filtros em um único comando. Para cada **/FilterType**, você pode adicionar ou remover vários valores usando **/RemoveValue** e **/AddValue**. \<FilterType > pode ser uma das seguintes opções:</br>**BiosVendor**</br>**BiosVersion**</br>**ChassisType**</br>**Fabricante**</br>**UUID**</br>**OsVersion**</br>**OsEdition**</br>**OsLanguage**                                                                                                                                                                                                                                                                        |
|     [/Policy:{Include      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Exclude}]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|    [/AddValue:\<Value>]    | Especifica o novo valor de cliente a adicionar ao filtro. Você pode especificar vários valores para um tipo único filtro. Consulte a lista a seguir para obter valores de atributo válido para **ChassisType**. Para obter informações sobre como obter os valores para todos os outros tipos de filtro, consulte [filtros de grupo de Driver](https://go.microsoft.com/fwlink/?LinkID=155158) (<https://go.microsoft.com/fwlink/?LinkID=155158>).</br>**Outros**</br>**UnknownChassis**</br>**Área de Trabalho**</br>**LowProfileDesktop**</br>**PizzaBox**</br>**MiniTower**</br>**Tower**</br>**portátil**</br>**Laptop**</br>**Notebook**</br>**Handheld**</br>**DockingStation**</br>**AllInOne**</br>**SubNotebook**</br>**SpaceSaving**</br>**LunchBox**</br>**MainSystemChassis**</br>**ExpansionChassis**</br>**SubChassis**</br>**BusExpansionChassis**</br>**PeripheralChassis**</br>**StorageChassis**</br>**RackMountChassis**</br>**SealedCaseComputer**</br>**MultiSystemChassis**</br>**CompactPci**</br>**AdvancedTca** |
|  [/RemoveValue:\<Value>]   |                                                                                                                                                                                                                                                                                                                                                                                                                                     Especifica o valor de cliente existentes para remover do filtro conforme especificado com **/AddValue**.                                                                                                                                                                                                                                                                                                                                                                                                                                      |

## <a name="BKMK_examples"></a>Exemplos

Para remover um filtro, digite um dos seguintes:
```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /AddValue:Name1 /RemoveValue:Name2
```
```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /RemoveValue:Name1 /FilterType:ChassisType /Policy:Exclude /AddValue:Tower /AddValue:MiniTower
```

#### <a name="additional-references"></a>Referências adicionais

[Chave da sintaxe de linha de comando](command-line-syntax-key.md)