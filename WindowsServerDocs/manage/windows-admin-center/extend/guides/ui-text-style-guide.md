---
title: Guia de estilo de texto e o design de IU de Windows Admin Center
description: Interface do usuário do Windows Admin Center texto e design de guia de estilo do SDK
ms.technology: manage
ms.topic: article
author: jasongerend
ms.author: jgerend
ms.date: 10/17/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: be41267d6584002ebf87e5fe828a41575d305e1b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445916"
---
# <a name="windows-admin-center-ui-text-and-design-style-guide"></a>Guia de estilo de texto e o design de IU de Windows Admin Center

>Aplica-se a: Windows Admin Center

Este tópico descreve a abordagem geral para escrita de texto (UI) da interface de usuário para o Windows Admin Center, bem como alguns convenções específicas e abordagens que estamos aproveitando.

Windows Admin Center e qualquer extensão deve seguir [princípios de voz da Microsoft](https://docs.microsoft.com/style-guide/brand-voice-above-all-simple-human) para que a experiência seja fácil de usar e amigável. Este guia de estilo baseia-se nestes princípios de voz, bem como o [Guia de estilo de escrita Microsoft](https://docs.microsoft.com/style-guide/welcome/), portanto, certifique-se de fazer check-out de ambos desses recursos para informações sobre coisas como [acessibilidade](https://docs.microsoft.com/style-guide/accessibility/accessibility-guidelines-requirements), [acrônimos](https://docs.microsoft.com/style-guide/acronyms)e [Escolha do word](https://docs.microsoft.com/style-guide/word-choice/) , como [ Por favor,](https://docs.microsoft.com/style-guide/a-z-word-list-term-collections/p/please)e [Desculpe](https://docs.microsoft.com/style-guide/a-z-word-list-term-collections/s/sorry).

## <a name="buttons"></a>Botões

- Botões devem ser uma palavra sempre que possível, especialmente se você planeja localizar sua ferramenta. Dois ou três são Okey mas evite mais. Se você tiver quatro palavras ou mais, seria melhor usar um controle de link.
- Rótulos de botão devem ser conciso, específicos e auto-explicativos. Em vez de um botão de "Enviar" genérico, use um verbo correspondente à ação de usuário, como "Criar", "Excluir", "Adicionar", "Formatação" etc.
- Se um botão segue uma pergunta, seu rótulo deve corresponder claramente para a pergunta (geralmente "Yes" ou "Não").

## <a name="capitalization"></a>Uso de maiúsculas

Podemos siga o estilo da Microsoft para [capitalização](https://docs.microsoft.com/style-guide/capitalization) - capitalização do estilo sentença de uso para praticamente tudo.

| Elemento de interface do usuário              |Uso de maiúsculas|Comentários|
|-------------------------|--------------|--------|
|Selos (por exemplo, VISUALIZAÇÃO) |Todo em maiúsculas      ||
|Todo o resto          |Estilo de frase|No entanto, há algumas exceções onde podemos desvendar propriedades do objeto do PowerShell que está fora do nosso controle ou de WMI.|

## <a name="colons"></a>Dois-pontos

Use dois-pontos para apresentar listas. Por exemplo:

    Choose one of the following:
    Cats
    Dogs
    Quokkas

Não use dois-pontos no texto de interface do usuário quando um rótulo está em outro de linha da coisa que ele rótulos ou quando há uma distinção clara entre o rótulo e a coisa rotulagem.

Use dois-pontos no texto de interface do usuário quando um rótulo está na mesma linha como o texto rotula e você precisa manter os dois elementos sejam executados juntos.

## <a name="confirmation-messages"></a>Mensagens de confirmação

Caixas de diálogo de confirmação são úteis quando continuar pode ter resultados inesperados, como perda de dados. Eles devem conter informações úteis, verificáveis com um resultado não criptografado, especialmente para eventos que não pode ser revertida. 

- Certifique-se de que uma confirmação é necessária. Se não houver nenhuma informação nova para oferecer (por exemplo, "você tem certeza?"), uma mensagem de confirmação não poderão ser necessária.  
- Verifique se o cliente deseja continuar com a ação.
- Verifique se que a instrução principal (título) e o texto explicativo (corpo) não redundantes.
- No título, defina os possíveis resultados como uma pergunta ou uma instrução sobre o que acontecerá em seguida. Por exemplo, "apagar todos os dados nessa unidade? ou "Você está prestes a apagar todos os seus dados".
- Adicione detalhes no corpo. Se não houver uma variável, como o nome do item que você está prestes a alteração, incluí-lo aqui.
- Inclua uma pergunta simples (ou no cabeçalho ou no corpo) que enquadra uma escolha clara entre os dois botões de ação.
- Para uma opção complexa, use Sim/não botões, que incentivar leitura cuidadosa. Para uma opção mais simples, usem os botões que são específicas para a ação, como excluir todos os ou Cancelar.

## <a name="first-run-experiences"></a>Experiências de primeira execução

Na primeira vez que um usuário visita uma página, você tem uma oportunidade para ajudá-los a começar a usar a ferramenta. Isso pode ser:

- Uma sequência de texto em uma página vazia com curtas instruções sobre como começar , por exemplo, "Selecione Adicionar para adicionar um aplicativo."
- Um link para o controle que obtém o usuário iniciado, por exemplo, "Adicione um aplicativo para começar."
- Um pequena e curta animação ou vídeo mostrando o usuário como começar

Aqui estão algumas dicas de nosso guia de estilo do Windows:

### <a name="1-be-helpful"></a>1. Ofereça ajuda

- Evite uma linguagem e estilo de marketing.
- Quando você demonstrar ou sugerir algo, verifique se o resultado final está claro; apenas mostrar para o cliente como fazer algo não é uma maneira eficaz caso não saibam o que estão fazendo.
- Não apresente dicas se o cliente não precisar delas.

### <a name="2-show-dont-tell"></a>2. Mostrar, não diga

Mantenha o texto simples possível (pense em animações pequenas ou vídeos).

### <a name="3-dont-overwhelm"></a>3. Não sobrecarregar

- Limitar pop-ups e dicas para 4 por sessão de uso combinados — incluindo notificações do sistema e notificações do shell.
- Verifique se que o tempo de pop-ups é útil.
- Não impede que o cliente fazendo algo.
- Certifique-se de que os pop-ups pode ser descartados facilmente.

### <a name="4-keep-it-contextual"></a>4. Mantenha-contextuais

- Momentos de ensino são mais eficazes quando apresentados no momento certo.
- Se você criar tutoriais ou apresentações de slides, mantenha as informações concretas.
- Não use marketing "complicado": concentre-se em dicas e truques específicos.
- Forneça uma maneira dos clientes retornarem ao tutorial depois, caso seja relevante (pessoas geralmente não retêm as informações na primeira vez, mas as instruções de configuração podem ser mais relevantes somente uma vez).
- Mensagens vazias são um lugar natural para aprendizado e/ou felicidade: mantenha tudo simples e informativo.

### <a name="5-minimize-painful-setup"></a>5. Minimizar dolorosa instalação

Quando você precisar que o cliente execute outra ação para experimentar o valor completo (entrar em um serviço online etc.), torne o processo o mais simples possível.

- As mensagens devem ser curtas e diretas.
- Evite assustá-los. Se possível, forneça um meio para se conectar a partir de onde estejam.
- Se possível, habilite a opção de execução posterior e, em seguida, lembre-os para executá-la posteriormente.
- Caso retire-os da experiência, forneça uma maneira de voltar de forma rápida e fácil.

## <a name="help-links"></a>Links de ajuda

Aqui estão algumas dicas de nosso guia de estilo do Windows:

### <a name="when-should-we-provide-a-help-link"></a>Quando estamos deve fornecer um link de ajuda?

Quase nunca. Forneça um link de Ajuda somente quando:

- Há uma questão óbvia e importante que os clientes têm probabilidade de ter enquanto eles estão na interface do usuário, a resposta para o qual o ajudará a ter êxito em que a tarefa de interface do usuário. 
- Não há espaço suficiente na interface do usuário para fornecer a quantidade de informações necessárias para que os usuários a tarefa de interface do usuário ser bem-sucedido. 

### <a name="where-should-help-links-appear"></a>Onde devem ajudar os links são exibidos? 

- Links de texto deve aparecer o mais próximo do elemento de interface do usuário que a Ajuda é direcionada quanto possível. 
- Se você deve fornecer um link de texto que se aplica a uma tela de interface do usuário inteira, coloque-o na parte inferior esquerda da tela. 
- Se você fornecer um link por meio de um botão de Ajuda (?), a dica de ferramenta deve ser "Help".

### <a name="what-url-should-we-use"></a>Qual URL podemos usar?

Nunca vincular diretamente para um endereço web — em vez disso, use um serviço de redirecionamento.

Os desenvolvedores da Microsoft devem usar um FWLink, exceto quando ele for um link de ajuda os usuários podem precisar digitar manualmente, que usam maiuscula um link aka.ms (desde que o destino da URL é um site que automaticamente reconhece a localidade do navegador, como o Docs.microsoft.com)

### <a name="text-guidelines"></a>Diretrizes de texto 

- Use frases completas.
- Não inclua pontuação, exceto para os pontos de interrogação final. 
- Você não precisa usar o mesmo texto como o título da tarefa; usar o texto que faz sentido no contexto da interface do usuário, mas certifique-se de que há uma conexão lógica entre os dois. Por exemplo: 
- Link de Ajuda: Quais são os riscos de permitir exceções? 
- Título do tópico da Ajuda: "Permitir um programa para se comunicar por meio do Firewall do Windows"
- Pode ser tão específico quanto possível sobre o conteúdo do tópico da Ajuda. 
    - Nosso estilo
        - Como o Firewall do Windows ajuda a proteger o meu computador?
        - Por que os destaques podem melhorar uma imagem
    - Não é nosso estilo
        - Para obter mais informações sobre o Firewall do Windows
        - Saiba mais sobre o gerenciamento de cores
        - Saiba mais
- Use a frase inteira para o texto do link, não apenas as palavras-chave. 
    - Nosso estilo 
        - [Quais são os riscos de permitir exceções?]()
    - Não é nosso estilo
        - Quais são as [riscos de permitir exceções]()? 

## <a name="error-messages"></a>Mensagens de erro

Aqui estão algumas diretrizes adaptado a partir da guia de estilo do Windows:

Uma boa mensagem de gravação é um equilíbrio entre fornecendo suficiente explicação, mas não estão sendo excessivamente técnico; entre os estados casual e forma agradável, mas não ou importunas.

### <a name="general-guidelines"></a>Diretrizes gerais

Use uma mensagem por caso de erro.

#### <a name="headings"></a>Títulos

- Mantê-lo em breve e concisa explicar o que é o problema ou **ideal é que o que fazer**. <br>Alguns superfícies de interface do usuário podem ter títulos que truncar em vez de encapsular quando eles são muito longos, portanto, fique atento a essas.
- Use a solução no título, se ele é uma etapa simples.
- Certifique-se de que o título está relacionado diretamente para o botão, caso o leitor ignora o texto do corpo.
- Evite usar a "Houve um problema" nos títulos, a menos que você tenha que não há outra opção. Ser mais específico sobre o problema.
- Evite o uso de variáveis (como nomes de arquivo, pasta e aplicativo) nos cabeçalhos. Colocá-los no corpo.

#### <a name="body"></a>Corpo

- Se o título suficientemente explica o problema ou a solução, você não precisa de corpo de texto.
- Não repita o título na mensagem com palavras ligeiramente diferentes.
- Se comunicar claramente e forma concisa o que a solução é.
- Concentre-se em fornecer aos fatos pela primeira vez.
- Os usuários não o culparia para o erro.
- Se não houver um código de erro associado ao erro e se você acha que incluir o código de erro pode ajudar o cliente ou o suporte da Microsoft a pesquisar o problema, incluí-lo diretamente abaixo do texto do corpo e gravá-lo da seguinte maneira:

    Código de erro: # # #

    Se o cliente tem todas as informações necessárias para resolver o erro sem o código, você não precisará incluí-lo.

#### <a name="buttons"></a>Botões

- Gravar o texto do botão para que ele seja uma resposta específica para a instrução principal. Se isso não for possível, use "Fechar" para o texto do botão exoneração (em vez de "Okey" ou "Concluído").
- Se você tiver mais de um botão, verifique o botão mais à esquerda a ação que o usuário é incentivado a tomar. Tornar o botão mais à direita da ação mais conservadora, como "Cancelar".

#### <a name="help-links"></a>Links de ajuda

Considere somente os links de ajuda para mensagens de erro que você não pode fazer específicas e acionáveis.

## <a name="null-state-text"></a>Texto do estado nulo

Eis aqui alguma ajuda do guia de estilo Windows.

Estado nulo ocorre quando os dados do cliente ou o conteúdo está ausente de um aplicativo ou recurso, quando nenhum resultado será retornado após uma pesquisa, ou quando for necessário faltam informações de um formulário, como informações de cobrança para uma transação.

### <a name="guidelines"></a>Diretrizes

- Se possível, use situações do estado nulo como uma oportunidade de ensinar as pessoas sobre como usar o recurso (por exemplo, como adicionar música, onde a localizar as imagens, etc.)  
  - Se você tiver um título em sua interface do usuário, explique a ação a ser realizada para "corrigir" estado nulo (por exemplo, "adicionar alguns música") 
  - Divirta-se com o texto. Esse espaço pode ser uma oportunidade de fornecer a felicidade, pois ele provavelmente não será visto várias vezes. 
  - Evitar "É solitário aqui." Isso é triste e foi o uso excessivo. 
  - Evitar a perguntas como "Ainda não tiver conectado sua impressora?" Okey para usar uma vez, mas esse formato tende a obter uso excessivo e perguntas fazer mais carga/pressão sobre o cliente. Isso também pode parecer condescendente. 
  - Variedade no texto do estado nulo é algo bom. 

### <a name="examples"></a>Exemplos

- "Adicionar alguém como um favorito, e você poderá vê-los aqui."
- "Você tem qualquer realizações ou clipes jogos estiver particularmente orgulhoso da? Adicioná-los para seu showcase."
- "Ninguém em uma festa ainda. Inicie um!"
- "Quando alguém adicionar você como um amigo, você poderá vê-los aqui."
- "Quando você coisas como desbloquear conquistas, gravar clipes de jogos e adicionar amigos, você verá tudo aqui."
- "Seus amigos Favoritos aparecerão aqui, você pode ver quando estiver online e o que eles planejam."

## <a name="punctuation"></a>Pontuação

- Sem pontuação final (pontos e interrogação) para títulos ou frases incompletas. Uma exceção é uma caixa de diálogo de confirmação onde o título faz a pergunta
- Use as instruções do guia de estilo doa Microsoft sobre [pontos](https://docs.microsoft.com/style-guide/punctuation/periods) e [pontos de interrogação](https://docs.microsoft.com/style-guide/punctuation/question-marks).

## <a name="status-messages"></a>Mensagens de status

Mensagens de status consistem em notificações e mensagens de janela pop-up (proposta).

|Tipo de cadeia de caracteres         | Observações                               |
|------------        |-------------------------------------|
|Notificação do sistema               |Frases com a mensagem de pontuação - idealmente com uma variável de objeto para que os usuários podem entender qual o objeto de final se aplica ao caso eles tenham navegado para longe do objeto|
|Título de notificação|Frases w/out pontuação final (Este é um título) - idealmente com uma variável de objeto|
|Detalhes da notificação|Sentenças completos, idealmente com um link para a interface do usuário que exibe o objeto|

Aqui estão algumas recomendações detalhadas para mensagens de notificação:

|Tipo de cadeia de caracteres         | Observações                               |
|------------        |-------------------------------------|
|Iniciado             |Omita quando possível: geralmente pule apenas a mensagem em andamento para minimizar o número de distrações.|
|Em andamento         |Comece com o verbo da ação que você estiver realizando e terminarem com reticências para indicar uma operação em andamento. Veja um exemplo:<br> *Criando o volume de "dados do cliente"...*|
|Êxito             |Comece com "Com êxito" e termine com o software que acabamos de fazer. Veja um exemplo:<br> *Criado com êxito o volume de "dados do cliente".*|
|Falha             |Comece com "Não pôde" e termine com o que o software não conseguiu realizar. Veja um exemplo:<br> *Não foi possível criar o volume de "dados do cliente".*|

## <a name="tooltips"></a>Dicas de ferramenta

Dicas de ferramenta boa brevemente descrevem controles sem rótulo ou providenciar um pouco de informações adicionais para controles de rotulado, quando isso é útil. Eles também podem ajudar os clientes navegar a interface do usuário, oferecendo adicionais — não redundantes — informações sobre rótulos de controle, ícones, links, etc.

Dicas de ferramenta devem ser usadas com moderação ou nada. Eles podem ser uma interrupção para o cliente, portanto, não inclua uma dica de ferramenta que simplesmente se repete um rótulo ou informa o óbvio. Ele sempre deve adicionar informações valiosas.

|    Contexto                                 |    Como escrever as dicas de ferramenta    |
|    -----------------------                 |    -------------------------    |
|Quando um controle ou elemento de interface do usuário é sem rótulo...|Use uma frase substantiva simples e descritivo. Por exemplo:<br> Realce de caneta |
|Quando um elemento de interface do usuário é rotulado, mas sua finalidade precisa de esclarecimento...|<ul><li>Descreva resumidamente o que você pode fazer com este elemento de interface do usuário. </li><li>Use o formulário de verbo imperativa. Por exemplo, "localizar texto nesse arquivo" (não "localizar o texto neste arquivo").</li><li>Não inclua pontuação final, a menos que haja várias frases completas.</li> </ul>|
|Quando um rótulo de texto é truncada ou provável truncar em alguns idiomas...|<ul><li>Forneça o rótulo completo na dica de ferramenta.</li><li>Opcional: Em outra linha, forneça uma descrição de esclarecimento das, mas somente se necessário.</li><li>Não fornece uma dica de ferramenta se as informações de completo é fornecida em outro lugar na página ou fluxo.</li></ul>|
|Se um atalho de teclado está disponível...|<ul><li>Opcional: Forneça o atalho de teclado entre parênteses após o rótulo ou a frase descritivo, por exemplo "Print (Ctrl + P)" ou "Localizar o texto neste arquivo (Ctrl + F)"</li><li>Ele é Okey para adicionar um atalho de teclado úteis para uma esclarecimento das dica de ferramenta, mas evitar adicionar uma dica de ferramenta apenas para mostrar um atalho de teclado. </li></ul>|