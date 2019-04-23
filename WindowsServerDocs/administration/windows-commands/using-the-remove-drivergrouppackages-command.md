---
title: Usando o comando remove-DriverGroupPackages
description: 'Tópico de comandos do Windows para * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b499635-6285-491c-8854-5665489f4364
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8c00251dd07fca2491fedf6aed0c6989ee65a0dc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59866007"
---
# <a name="using-the-remove-drivergrouppackages-command"></a>Usando o comando remove-DriverGroupPackages

>Aplica-se a: Windows Server (canal semestral), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Remove os pacotes de driver de um grupo de drivers em um servidor.
## <a name="syntax"></a>Sintaxe
```
wdsutil /remove-DriverGroupPackages /DriverGroup:<Group Name> [/Server:<Server Name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value> ...]
```
## <a name="parameters"></a>Parâmetros
|Parâmetro|Descrição|
|-------|--------|
|/DriverGroup:<Group Name>|Especifica o nome do grupo de drivers.|
|[/Server:<Server name>]|Especifica o nome do servidor. Isso pode ser o nome NetBIOS ou FQDN. Se não for especificado um nome de servidor, o servidor local será usado.|
|/Filtertype:<Filter type>|Especifica o atributo do pacote de driver a ser pesquisado. Você pode especificar vários atributos em um único comando. Você também deve especificar **/Operator** e **/valor** com essa opção.<br /><br /><Filter type> Pode ser uma das seguintes opções:<br /><br />**PackageId**<br /><br />**PackageName**<br /><br />**PackageEnabled**<br /><br />**Packagedateadded**<br /><br />**PackageInfFilename**<br /><br />**PackageClass**<br /><br />**PackageProvider**<br /><br />**PackageArchitecture**<br /><br />**PackageLocale**<br /><br />**PackageSigned**<br /><br />**PackagedatePublished**<br /><br />**Packageversion**<br /><br />**Driverdescription**<br /><br />**DriverManufacturer**<br /><br />**DriverHardwareId**<br /><br />**DrivercompatibleId**<br /><br />**DriverExcludeId**<br /><br />**DriverGroupId**<br /><br />**DriverGroupName**|
|/Operator:{Equal &#124; NotEqual &#124; GreaterOrEqual &#124; LessOrEqual &#124; Contains}|Especifica a relação entre o atributo e os valores. Você só pode especificar **Contains** com atributos de cadeia de caracteres. Você só pode especificar **GreaterOrEqual** e **LessOrEqual** com atributos de data e a versão.|
|/Value:<Value>|Especifica o valor de pesquisa especificado <attribute>. Você pode especificar vários valores para uma única **/Filtertype**. A lista a seguir descreve os atributos que você pode especificar para cada filtro. Para obter mais informações sobre esses atributos, consulte [atributos de Driver e pacote](https://go.microsoft.com/fwlink/?LinkId=166895) (https://go.microsoft.com/fwlink/?LinkId=166895).<br /><br />-PackageId - especifique um GUID válido. Por exemplo: {4d36e972-e325-11ce-bfc1-08002be10318}.<br />-PackageName especificar qualquer valor de cadeia de caracteres.<br />-Especifique PackageEnabled - **Yes** ou **não**.<br />-Packagedateadded - especifique a data no seguinte formato: AAAA/MM/DD<br />-PackageInfFilename especificar qualquer valor de cadeia de caracteres.<br />-PackageClass - especifique um nome de classe válido ou o GUID de classe. Por exemplo:  **Unidade de disco**, **Net**, ou {4d36e972-e325-11ce-bfc1-08002be10318}.<br />-PackageProvider especificar qualquer valor de cadeia de caracteres.<br />-Especifique PackageArchitecture - **x86**, **x64**, ou **ia64**.<br />-PckageLocale - especifique um identificador de idioma válido. Por exemplo: **en-US** ou **es-ES**.<br />-Especifique PackageSigned - **Yes** ou **não**.<br />-PackagedatePublished - especifique a data no seguinte formato: AAAA/MM/DD<br />-Packageversion - especifique a versão no seguinte formato: a.b.x.y. Por exemplo:  6.1.0.0<br />-Driverdescription especificar qualquer valor de cadeia de caracteres.<br />-DriverManufacturer especificar qualquer valor de cadeia de caracteres.<br />-DriverHardwareId - especificar qualquer valor de cadeia de caracteres.<br />-DrivercompatibleId - especificar qualquer valor de cadeia de caracteres.<br />-DriverExcludeId - especificar qualquer valor de cadeia de caracteres.<br />-DriverGroupId - especifique um GUID válido. Por exemplo: {4d36e972-e325-11ce-bfc1-08002be10318}.<br />-DriverGroupName especificar qualquer valor de cadeia de caracteres.|
## <a name="BKMK_examples"></a>Exemplos
Para remover pacotes de driver de um grupo de drivers, digite um dos seguintes:
```
wdsutil /verbose /remove-DriverGroupPackages /DriverGroup:printerdrivers
/Filtertype:DriverManufacturer /Operator:NotEqual /Value:Name1 /Value:Name2
```
```
wdsutil /verbose /remove-DriverGroupPackages /DriverGroup:DisplayDrivers
/Filtertype:PackageArchitecture /Operator:Equal /Value:x86
/Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```
#### <a name="additional-references"></a>Referências adicionais
[Chave de sintaxe de linha de comando](command-line-syntax-key.md)
[usando o comando remove-DriverGroupPackage](using-the-remove-drivergrouppackage-command.md)