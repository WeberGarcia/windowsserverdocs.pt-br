---
title: Adicionar uma guia a Configurações
description: Descreve como usar o Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aac6b7f3-9020-46c3-a83f-b81542300385
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 9eaa1aa5a9c5e8d4c2e36f2000e0adecc83245d9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854977"
---
# <a name="add-a-tab-to-settings"></a>Adicionar uma guia a Configurações

>Aplica-se a: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Você pode adicionar uma guia a Configurações no Dashboard criando e instalando um assembly de código usado pelo Gerenciador de Parâmetros no sistema operacional.  
  
## <a name="add-a-tab-to-settings"></a>Adicionar uma guia a Configurações  
 Você adiciona uma guia a Configurações executando as seguintes tarefas:  
  
-   [Adicionar uma implementação da interface ISettingsData ao assembly](Add-a-Tab-to-Settings.md#BKMK_ISettingsData).  
  
-   [Sign the assembly with an Authenticode signature](Add-a-Tab-to-Settings.md#BKMK_SignAssembly).  
  
-   [Instalar o assembly no computador de referência](Add-a-Tab-to-Settings.md#BKMK_InstallAssembly).  
  
###  <a name="BKMK_ISettingsData"></a> Adicionar uma implementação da interface ISettingsData ao assembly  
 A interface ISettingsData está incluída no namespace Microsoft.WindowsServerSolutions.Settings do assembly do AdminCommon.dll localizado em \Arquivos de programa\Windows Server\Bin.  
  
##### <a name="to-add-the-isettingsdata-code-to-the-assembly"></a>Para adicionar o código de ISettingsData ao assembly  
  
1.  Abra o Visual Studio 2010 como administrador clicando com o botão direito do mouse no programa no menu **Iniciar** e selecione **Executar como administrador**.  
  
2.  Clique em **Arquivo**, em **Novo**e em **Projeto**.  
  
3.  Na caixa de diálogo **Novo Projeto** , clique em **Visual C#**, clique em **Biblioteca de Classes**, digite **DashboardSettingsPage** para o nome da solução e clique em **OK**.  
  
    > [!IMPORTANT]
    >  O assembly instalado no servidor deve ser chamado de DashboardSettingsPage.dll e então copiar o dll em %Arquivos de programas%\Windows Server\Bin\OEM.  
  
4.  Criar o controle que você deseja usar na guia. Neste exemplo, o controle de configurações é nomeado MySettingsControl.  
  
5.  Renomeie o arquivo Class1.cs. Por exemplo, MySettingTab.cs.  
  
6.  Adicionar uma referência ao arquivo AdminCommon.dll.  
  
7.  Adicionar a seguinte instrução de uso:  
  
    ```c#  
    using Microsoft.WindowsServerSolutions.Settings;  
    ```  
  
8.  Altere o namespace e o cabeçalho de classe para corresponder ao exemplo a seguir:  
  
    ```  
  
    namespace DashboardSettingsPage  
    {  
        public class MySettingTab : ISettingsData  
        {  
        }  
    }  
  
    ```  
  
9. Criar uma instância do controle que você criou para a guia. Por exemplo:  
  
    ```c#  
    private MySettingsControl tab;  
    ```  
  
10. Adicionar o construtor da classe. O exemplo de código a seguir mostra o construtor:  
  
    ```  
  
    public MySettingTab()  
    {  
       tab = new MySettingsControl();  
    }  
    ```  
  
11. Adicione o método Commit, que envia as alterações de configuração. O exemplo de código a seguir mostra o método Commit:  
  
    ```  
  
    void ISettingsData.Commit(bool dismissed)  
    {  
       // Implement the code that is required to submit your setting changes  
    }  
    ```  
  
12. Adicione o método TabControl, que identifica o controle para a guia. O exemplo de código a seguir mostra o método TabControl:  
  
    ```  
  
    System.Windows.Forms.Control ISettingsData.TabControl  
    {  
       get { return tab; }  
    }  
    ```  
  
13. Adicione o método TabId, que fornece um identificador exclusivo para a guia. O exemplo de código a seguir mostra o método TabId:  
  
    ```  
  
    private Guid id = Guid.NewGuid();  
  
    Guid ISettingsData.TabId  
    {  
       get { return id; }  
    }  
    ```  
  
14. Adicione o método TabOrder, que retorna a ordem das guias. O exemplo de código a seguir mostra o método TabOrder:  
  
    ```  
  
    int ISettingsData.TabOrder  
    {  
       get { return 0; }  
    }  
    ```  
  
    > [!NOTE]
    >  A ordem da guia é definida usando números iniciando em 0. As guias de configuração internas da Microsoft são exibidas primeiro; a seguir, suas guias são exibidas, com base na ordem de guias definida por você. Por exemplo, se você tem três guias de configuração, especifique a ordem das guias como 0, 1 e 2 com base na ordem em que deseja que elas sejam exibidas.  
  
15. Adicione o método TabTitle, que fornece o título da guia. O exemplo de código a seguir mostra o método TabTitle:  
  
    ```  
  
    string ISettingsData.TabTitle  
    {  
      get { return "My Settings Tab"; }  
    }  
    ```  
  
    > [!NOTE]
    >  O texto do título também pode vir de um arquivo de recurso para acomodar necessidades de localização.  
  
16. Salve e crie a solução.  
  
###  <a name="BKMK_SignAssembly"></a> Assinar o assembly com uma assinatura Authenticode  
 Você deve assinar com a Authenticode o assembly para que seja usado no sistema operacional. Para obter mais informações sobre a assinatura do assembly, consulte [Assinando e verificando códigos com Authenticode](https://msdn.microsoft.com/library/ms537364\(VS.85\).aspx#SignCode).  
  
###  <a name="BKMK_InstallAssembly"></a> Instalar o assembly no computador de referência  
 Depois de criar a solução com êxito, coloque uma cópia do arquivo DashboardSettingsPage.dll na seguinte pasta no computador de referência:  
  
 **%Programfiles%\Windows Server\Bin\OEM**  
  
## <a name="see-also"></a>Consulte também  
 [Criando e personalizando a imagem](Creating-and-Customizing-the-Image.md)   
 [Personalizações adicionais](Additional-Customizations.md)   
 [Preparando a imagem para implantação](Preparing-the-Image-for-Deployment.md)   
 [Testando a experiência do usuário](Testing-the-Customer-Experience.md)