---
title: Criar a mídia de restauração do cliente de vários idiomas
description: Descreve como usar o Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fdbc016-d464-43cb-bd75-8a63e61588a2
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 1ad934d297c3092050bd6adbb6bb0f50d1ec6f36
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879867"
---
# <a name="build-multi-language-client-restore-media"></a>Criar a mídia de restauração do cliente de vários idiomas

>Aplica-se a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

> [!NOTE]
>  Você deve primeiro criar uma imagem multilíngue do Windows, conforme descrito no [passo a passo: Criação de imagem multilíngue do Windows](https://technet.microsoft.com/library/jj126995) antes de adicionar o pacote de idiomas do Windows Server Essentials em Install. wim.  
  
 Ao criar o DVD de instalação do servidor de vários idiomas, os pacotes de idiomas serão instalados no Servidor install.wim. Os recursos localizados para o assistente de restauração serão instalados como parte do pacote de idiomas.  
  
### <a name="to-build-a-multi-language-client-restore-media"></a>Para criar uma mídia de restauração do cliente de vários idiomas.  
  
1.  Monte install.wim em c:\mount, chamamos a pasta c:\mount\Program Files\Windows Server\bin\ClientRestore como a raiz da mídia de restauração do cliente: [RestoreMediaRoot] abaixo:  
  
    ```  
    dism /mount-wim /wimfile:install.wim /index:1 /mountdir:c:\mount  
    ```  
  
2.  Monte o arquivo WIM de restauração do cliente em [RestoreMediaRoot]\Sources\Boot.wim (As mesmas etapas precisam ser realizadas para boot_x86.wim também). A linha de comando é:  
  
    ```  
    dism /mount-wim /wimfile:boot.wim /index:1 /mountdir:c:\mountRestore  
    ```  
  
3.  Adicione o pacote WinPE-Setup.cab à mídia de restauração executando:  
  
    ```  
    dism /image:c:\mountRestore /add-package /packagepath:WinPE-Setup.cab  
    ```  
  
4.  Use o bloco de notas para editar c:\mountRestore\windows\system32\winpeshl.ini, preencha com o seguinte conteúdo:  
  
    ```  
    [LaunchApp]  
    AppPath = %SYSTEMDRIVE%\sources\SelectLanguage.exe  
    ```  
  
5.  Adicionar pacotes de idiomas à mídia de restauração. Pacotes de idiomas podem ser adicionados executando o seguinte comando:  
  
    ```  
    dism /image:c:\mountRestore /add-package /packagepath:[language pack path]  
    ```  
  
     Os seguintes pacotes de idiomas precisam ser adicionais:  
  
    1.  Pacote de idioma WinPE (lp.cab)  
  
    2.  Pacote do idioma WinPE-Setup (WinPE-Setup_[lang].cab, por exemplo, WinPE-Setup_en-us.cab)  
  
    3.  Para fontes asiáticas, incluindo zh-cn, zh-tw, zh-hk, ko-kr, ja-jp, um pacote de fontes adicional precisa ser instalado (winpe-fontsupport-[lang].cab, por exemplo, winpe-fontsupport-zh-cn.cab)  
  
6.  Gere o novo arquivo Lang.ini executando:  
  
    ```  
    dism /image:c:\mountRestore /Gen-LangINI /distribution:mount  
    ```  
  
7.  Confirme e desmonte a imagem executando:  
  
    ```  
    dism /unmount-wim /mountdir:c:\mountRestore /commit  
    ```  
  
8.  Repita as etapas de 2 até 7 para [RestoreMediaroot]\Sources\Boot_x86.wim.  
  
9. Confirme e desmonte a imagem executando:  
  
    ```  
    dism /unmount-wim /mountdir:c:\mount /commit  
    ```  
  
## <a name="see-also"></a>Consulte também  

 [Criando e personalizando a imagem](Creating-and-Customizing-the-Image.md)   
 [Personalizações adicionais](Additional-Customizations.md)   
 [Preparando a imagem para implantação](Preparing-the-Image-for-Deployment.md)   
 [Testando a experiência do usuário](Testing-the-Customer-Experience.md)

 [Criando e personalizando a imagem](../install/Creating-and-Customizing-the-Image.md)   
 [Personalizações adicionais](../install/Additional-Customizations.md)   
 [Preparando a imagem para implantação](../install/Preparing-the-Image-for-Deployment.md)   
 [Testando a experiência do usuário](../install/Testing-the-Customer-Experience.md)

