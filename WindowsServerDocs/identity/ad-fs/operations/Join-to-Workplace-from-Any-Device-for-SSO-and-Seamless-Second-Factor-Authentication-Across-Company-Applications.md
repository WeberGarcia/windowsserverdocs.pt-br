---
ms.assetid: e22d84a5-113d-4bec-b484-036ed29f0c28
title: ingresso no Local de Trabalho em qualquer dispositivo de SSO e autenticação de dois fatores contínua em aplicativos da empresa
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 12/05/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: e9d6161666be89673cff6ef1a975d3205fa4b5c9
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189093"
---
# <a name="join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications"></a>ingresso no Local de Trabalho em qualquer dispositivo de SSO e autenticação de dois fatores contínua em aplicativos da empresa



O aumento rápido no número de dispositivos de consumidor e o acesso onipresente a informações está mudando a maneira como as pessoas entendem sua tecnologia. O uso constante da tecnologia da informação durante todo o dia, juntamente com o acesso fácil a informações, está obscurecendo os limites tradicionais entre trabalho e vida doméstica. Esses limites inconstantes são acompanhados pela crença esse pessoal tecnologia selecionada e personalizada para se ajustar personalidades, atividades e agendas dos usuários-deve se estender ao local de trabalho. Para acomodar a necessidade crescente de dispositivos de consumidor pessoal serem conectados a redes corporativas, estamos introduzindo as seguintes propostas de valor:

-   Os administradores podem controlar quem tem acesso a recursos da empresa com base no aplicativo, usuário, dispositivo e local.

-   Os funcionários podem acessar aplicativos e dados de qualquer lugar, em qualquer dispositivo. Os funcionários podem usar Logon Único em aplicativos de navegador ou aplicativos empresariais.

## <a name="key-concepts-introduced-in-the-solution"></a>Principais conceitos introduzidos na solução

### <a name="workplace-join"></a>Ingresso no local de trabalho
Usando o Ingresso no Local de Trabalho, os operadores de informações podem ingressar seus dispositivos pessoais aos computadores do local de trabalho de suas empresas para acessarem serviços e recursos empresariais. Quando você ingressa seu dispositivo pessoal no local de trabalho, ele se torna um dispositivo conhecido e fornece autenticação de dois fatores contínua e Logon Único a aplicativos e recursos do local de trabalho. Quando um dispositivo ingressa por meio do Ingresso no Local de Trabalho, atributos do dispositivo podem ser recuperados no diretório para conduzir o acesso condicional com o objetivo de autorizar a emissão de tokens de segurança para aplicativos. Dispositivos Windows 8.1, iOS 6.0+ e Android 4.0+ podem ser unidos usando o Ingresso no Local de Trabalho.

### <a name="BKMK_DRS"></a>Serviço de registro de dispositivo do Active Directory do Azure
O Ingresso no Local de Trabalho se tornou possível pelo serviço de registro do dispositivo do Active Directory do Azure. Quando um dispositivo ingressa pelo Ingresso no Local de Trabalho, o serviço provisiona um objeto de dispositivo no Active Directory do Azure e configura uma chave no dispositivo local usado para representar a identidade do dispositivo. Essa identidade de dispositivo pode então ser usada com as regras de controle de acesso para aplicativos hospedados na nuvem e locais.

Para obter mais detalhes, consulte [Introdução ao gerenciamento de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).

### <a name="workplace-join-as-a-seamless-second-factor-authentication"></a>O Ingresso no Local de Trabalho como um autenticação de dois fatores contínua
As empresas podem gerenciar o risco relacionado ao acesso a informações e conduzir o controle e a conformidade, ao mesmo tempo em que concedem acesso a recursos corporativos aos dispositivos de consumidor. O Ingresso no Local de Trabalho em dispositivos fornece as seguintes funcionalidades aos administradores:

-   Identifica dispositivos conhecidos com autenticação de dispositivo. Os administradores podem usar essas informações para conduzir acesso condicional e controlar o acesso a recursos.

-   Fornece uma experiência de entrada contínua para os usuários acessarem recursos da empresa em dispositivos confiáveis.

### <a name="single-sign-on"></a>Logon Único
O SSO (Logon Único) no contexto desse cenário é a funcionalidade que reduz o número de prompts de senhas que o usuário final precisa digitar para acessar os recursos da empresa em dispositivos conhecidos. Essa funcionalidade implica que haverá apenas um prompt aos usuários durante o tempo de vida do SSO para acessar aplicativos e recursos da empresa nesse dispositivo. Se um dispositivo utiliza o Ingresso no Local Trabalho, o usuário que está registrado para usar esse dispositivo adquire SSO persistente, por padrão, por sete dias. Esse usuário tem uma perfeita experiência de entrada na mesma sessão ou em novas sessões.

## <a name="solution-overview"></a>Visão geral da solução
Como parte dessa solução, aprenda como usar o Ingresso no Local de Trabalho em um dispositivo com suporte e experimentar o Logon Único a um recurso da empresa.

> [!NOTE]
> Para oferecer suporte a dispositivos com Windows 8.1, iOS 6.0+ e Android 4.0+, você DEVE configurar o registro de dispositivo do Active Directory do Azure com write-back do objeto de dispositivo, consulte [Guia passo a passo de acesso condicional no local usando o serviço de registro de dispositivo do Active Directory do Azure](https://msdn.microsoft.com/library/azure/dn788908.aspx)

Estes guias de solução orientam você nas seguintes etapas passo a passo:

1.  [Passo a passo: Ingressar no local de trabalho com um dispositivo do Windows](../../ad-fs/operations/Walkthrough--Workplace-Join-with-a-Windows-Device.md)

2.  [Passo a passo: Ingressar no Local de Trabalho com um dispositivo iOS](../../ad-fs/operations/Walkthrough--Workplace-Join-with-an-iOS-Device.md)

3.  [Passo a passo: Ingressar no local de trabalho com um dispositivo Android](../../ad-fs/operations/walkthrough--workplace-join-to-an-android-device.md)

## <a name="see-also"></a>Consulte também
[Configurar um servidor de federação com o Device Registration Service](../deployment/configure-a-federation-server-with-device-registration-service.md)



