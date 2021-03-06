---
title: O AD FS paginado entrar
description: Este documento descreve a nova experiência entrar do AD FS de 2019.
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 09/19/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: c528b9c4e944849b7ed9a2fc5213a7b263be70c7
ms.sourcegitcommit: ccc802338b163abdad2e53b55f39addcfea04603
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66687383"
---
# <a name="ad-fs-paginated-sign-in"></a>O AD FS paginado entrar


Para AD FS no Windows Server 2019, Reformulamos a interface do usuário entrar.  Agora, a entrada do AD FS terá a mesma aparência e funcionalidade do AD do Azure.  Isso fornecerá aos usuários uma experiência mais consistente entrar, incorporando um fluxo de usuário centralizado e paginados.

## <a name="whats-changing"></a>O que está sendo alterado.
No AD FS no Windows Server 2012 R2 e 2016, a tela de entrada tinha algo parecido com isto:

![oldsignin](media/AD-FS-paginated-sign-in/signin1.png)

Estamos movendo longe exibindo um único formulário localizado no lado direito da tela.

No AD FS no Windows Server 2019, essas são as alterações de design principais que você verá:


- **Um centralizada da interface do usuário**. Anteriormente, a interface do usuário entrar existia no lado direito da tela, conforme mostrado acima. Mudamos o centro para modernizar a experiência e a frente da interface do usuário.
- **Paginação**. Em vez de fornecer um formato longo para preencher, incorporamos um novo fluxo que o guiarão a experiência de entrada passo a passo. Nossa telemetria mostra que, com essa abordagem, nossos clientes têm entradas mais bem-sucedidas. Ele também fornece mais flexibilidade para incorporar vários métodos de autenticação, como autenticação de fator do telefone.

![newsignin](media/AD-FS-paginated-sign-in/signin2.png)

Na primeira página, você será solicitado a inserir seu nome de usuário. Você também pode selecionar a opção "Manter-me conectado" para reduzir a frequência de prompts de entrada e permanecer conectado quando for seguro fazê-lo. (Essa opção é desabilitada por padrão).

![newsignin](media/AD-FS-paginated-sign-in/signin3.png)

Na segunda página, você verá as opções de autenticação configuradas pelo seu administrador. Se estiver habilitado, permitindo a autenticação externa como primário, isso será incluído também.

![newsignin](media/AD-FS-paginated-sign-in/signin4.png)

Na terceira página, você será solicitado a inserir sua senha (supondo que você selecionou "Senha" como a opção de autenticação).

## <a name="how-to-get-the-new-experience"></a>Como obter a nova experiência

### <a name="new-installation-of-ad-fs"></a>Nova instalação do AD FS
Se você for um novo cliente para o AD FS, você receberá o novo design por padrão.

### <a name="upgrading-a-farm"></a>Atualizando um farm
Se você for um cliente existente do AD FS 2012 R2 ou 2016, há duas maneiras de receber o novo design após a atualização de servidores para o AD FS 2019 e habilitando o FBL para 2019.

- Permitir que a nova entrada por meio do Powershell. Execute o seguinte comando para habilitar a paginação: ``Set-AdfsGlobalAuthenticationPolicy -EnablePaginatedAuthenticationPages $true``

 - Habilite autenticação externa como primário, por meio do Powershell ou por meio do Gerenciador do servidor do AD FS. A nova entrada paginada páginas será habilitada quando esse recurso está habilitado.
Se você for um novo cliente para o AD FS, você receberá o novo design por padrão. No entanto, se você for um cliente existente com o AD FS 2012 R2 ou 2016, há várias etapas que você precisará levar para receber o novo design: ``Set-AdfsGlobalAuthenticationPolicy -AllowAdditionalAuthenticationAsPrimary $true``

## <a name="customization"></a>Personalização
As opções de personalização ainda será aplicáveis para o AD FS de 2019.
Abaixo estão alguns links para outros documentos para sua referência.

• Para aqueles que não planeja atualizar seus servidores AD FS 2019, mas ainda deseja que o novo design: [Usando um tema da Web de experiência do usuário do Azure AD nos serviços de Federação do Active Directory](azure-ux-web-theme-in-ad-fs.md)

• Um local central para personalização: [Personalização de entrada de usuário do AD FS](ad-fs-user-sign-in-customization.md)
