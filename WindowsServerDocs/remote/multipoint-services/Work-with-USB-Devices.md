---
title: Trabalhar com dispositivos USB
description: Saiba como os dispositivos USB funcionam com o MultiPoint Services
ms.custom: na
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a33f2b83-bbc2-4fc1-8a94-aaa985dfe1f9
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: f961f9270183b17855151f11ce222e3a5cc8df7d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883767"
---
# <a name="work-with-usb-devices"></a>Trabalhar com dispositivos USB
Você pode conectar dispositivos ao computador no seu sistema MultiPoint Services ou a um hub de estação do MultiPoint. O local no qual um dispositivo está conectado, e o tipo de dispositivo, afeta se um dispositivo está disponível para todos os usuários no sistema, somente a usuários individuais ou se ele não está disponível para todos os usuários. A seguir, há exemplos de diferentes tipos de conexão:  
  
-   Se você conectar um dispositivo diretamente ao computador, como uma impressora ou dispositivo de armazenamento em massa USB, o dispositivo poderá ser acessado por todos os usuários da sessão no sistema MultiPoint Services. Os usuários da estação da área de trabalho virtual não poderão acessar os dispositivos conectados diretamente ao computador.  
  
-   Se você conectar um dispositivo a um hub de estação, como um teclado, mouse, *dispositivo de áudio* ou dispositivo de armazenamento em massa, o dispositivo ficará disponível somente para o usuário conectado a essa estação do MultiPoint Services.  
  
-   Se você conectar certos tipos de dispositivos ao computador, como um teclado ou mouse, os dispositivos não ficarão disponíveis para todos os usuários no sistema.  
  
A tabela a seguir mostra uma lista de dispositivos e como eles se comportam dependendo de onde eles estiverem conectados ao sistema. Informações sobre como conectar hubs de estação são descritas em [trabalhando com hubs de estação](#working-with-station-hubs). Para obter mais informações sobre como conectar monitores de vídeo a uma estação são descritas em [trabalhar com dispositivos de vídeo](Work-with-Video-Devices.md).  
  
|||||  
|-|-|-|-|  
|**Dispositivo**|**Comportamento quando é conectado diretamente ao computador**|**Comportamento quando ele estiver conectado a uma estação**|**Notas**|  
|Teclado|Não recomendamos conectar um teclado diretamente ao computador.|Acessível somente para o usuário da estação.|Se o teclado contiver uma porta USB, o hub USB dentro do teclado poderá ser o hub de estação. Outros dispositivos USB conectados a essa porta estão disponíveis somente para o usuário que está usando esse teclado.<br /><br />Alguns hubs de estação são equipados com uma porta para mouse PS\/2 que é convertida em uma conexão USB dentro do hub.|  
|Mouse|Não recomendamos conectar um mouse diretamente ao computador.|Acessível somente para o usuário da estação.|Alguns hubs de estação são equipados com uma porta para mouse PS\/2 que é convertida em uma conexão USB dentro do hub.|  
|Hub USB|Ver [trabalhando com hubs de estação](#working-with-station-hubs).|Ver [trabalhando com hubs de estação](#working-with-station-hubs).||  
|Monitor de vídeo|Ver [dispositivos de vídeo do MultiPoint Services](work-with-video-devices.md).|Ver [dispositivos de vídeo do MultiPoint Services](work-with-video-devices.md).||  
|Dispositivos de saída de áudio como fones de ouvido|Não recomendamos conectar um dispositivo de saída de áudio diretamente ao computador.|Acessível somente para o usuário da estação.|Alguns hubs de estação são equipados com uma porta para áudio analógica que é convertida em uma conexão de áudio USB dentro do hub.|  
|Dispositivos de entrada de áudio como microfones|Não recomendamos conectar um dispositivo de entrada de áudio diretamente ao computador.|Acessível somente para o usuário da estação.|Alguns hubs de estação são equipados com uma porta para áudio analógica que é convertida em uma conexão de áudio USB dentro do hub.|  
|Impressoras|Acessível a todos os usuários do sistema. *|Acessível somente para o usuário da estação.||  
|Dispositivo de armazenamento em massa USB|Acessível a todos os usuários no sistema.\*|Acessível somente para o usuário da estação.|Esses dispositivos incluem unidades flash USB, discos rígidos externos e câmeras digitais.|  
|Webcams|Acessível a todos os usuários do sistema. *|Acessível somente para o usuário da estação.|Somente um usuário pode se conectar à câmera por vez.|  
  
* Os dispositivos que estão conectados ao computador host não são visíveis aos usuários que fizerem logon em estações de área de trabalho virtuais.  
  
Para obter mais informações sobre como configurar uma estação, consulte [Configurar uma estação](Set-Up-a-Station.md).  
  
### <a name="working-with-station-hubs"></a>Trabalhando com hubs de estação  
Há quatro maneiras de usar um hub USB quando ele está conectado a um sistema MultiPoint Services. Cada uma das maneiras a seguir fornece acesso diferente aos dispositivos conectados a ele, dependendo do tipo de hub e onde ele está conectado ao sistema.  
  
-   Um hub de estação conectado ao computador no seu sistema MultiPoint Services com um teclado conectado pode ser usado para criar uma estação do MultiPoint Services. Um teclado e um mouse são conectados ao hub de estação usando as portas disponíveis no hub. Um monitor de vídeo é conectado a uma porta de vídeo no computador ou a uma placa de vídeo no hub de estação, se disponível. O teclado, mouse e monitor são *associados* a uma estação do MultiPoint Services.  
  
-   Um hub USB conectado ao computador no seu sistema MultiPoint Services sem teclado conectado pode ser usado para conectar dispositivos adicionais no computador quando não houver portas suficientes para os dispositivos necessários. Todos os dispositivos conectados a esse hub USB estão disponíveis para todos os usuários do sistema MultiPoint Services. Isso não é considerado um hub de estação do MultiPoint Services.  
  
-   Um hub USB alimentado, conectado ao computador no seu sistema MultiPoint Services, também conhecido como um hub intermediário, pode ser usado para conectar hubs USB adicionais usados para criar estações do MultiPoint.  
  
-   Um hub USB conectado a um hub de estação pode ser usado para conectar dispositivos adicionais ao hub de estação. Teclados devem ser conectados diretamente ao hub de estação.  
  
Para obter mais informações sobre como configurar uma estação do MultiPoint Services, consulte [Configurar uma estação](Set-Up-a-Station.md).  
  
## <a name="see-also"></a>Consulte também  
[Trabalhar com dispositivos de vídeo](Work-with-Video-Devices.md)  
[Gerenciar Hardware da estação](Manage-Station-Hardware.md)  
[Configurar uma estação](Set-Up-a-Station.md)