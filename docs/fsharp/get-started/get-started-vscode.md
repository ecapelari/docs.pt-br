---
title: 'Introdução à linguagem F # em código do Visual Studio'
description: 'Saiba como usar o F # com o código do Visual Studio e o conjunto de plug-in de Ionide.'
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728622"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Introdução à linguagem F # em código do Visual Studio

Você pode escrever F # em [código do Visual Studio](https://code.visualstudio.com) com o [Ionide plug-in](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), para obter uma ótima experiência de ambiente de desenvolvimento integrado (IDE) de leve e de plataforma cruzada com o IntelliSense e o código básico refatorações. Visite [Ionide.io](http://ionide.io) para saber mais sobre o conjunto de plug-in.

## <a name="prerequisites"></a>Pré-requisitos

Você deve ter [git instalado](https://git-scm.com/download) e está disponível no seu caminho para fazer uso dos modelos de projeto em Ionide. Você pode verificar se ele está instalado corretamente, digitando `git --version` em um prompt de comando e pressionando **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

Usa Ionide [Mono](http://www.mono-project.com). A maneira mais fácil de instalar Mono em macOS é por meio de Homebrew. Simplesmente digite o seguinte em seu terminal:

```
brew install mono
```

Você também deve instalar o [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

No Linux, Ionide também usa [Mono](https://www.mono-project.com). Se você estiver em Debian ou Ubuntu, você pode usar o seguinte:

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Você também deve instalar o [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Se você estiver no Windows, você deve [instalar o Visual Studio com suporte do F #](get-started-visual-studio.md#installing-f). Isso instala todos os componentes necessários para escrever, compilar e executar código F #.

Você também deve instalar o [.NET Core SDK](https://www.microsoft.com/net/download/).

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>Instalando o plug-in Ionide e código do Visual Studio

Você pode instalar o Visual Studio Code do [code.visualstudio.com](https://code.visualstudio.com) site.

Em seguida, clique no ícone de extensões e procure "Ionide":

O plug-in somente necessário para suporte a F # no código do Visual Studio é [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). No entanto, você também pode instalar [Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter [FORJAR](https://fsharp.github.io/FAKE/) suporte e [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter [Paket](https://fsprojects.github.io/Paket/) suporte. FORJAR e Paket F # comunidade ferramentas adicionais para a criação de projetos e gerenciamento de dependências, respectivamente.

## <a name="creating-your-first-project-with-ionide"></a>Criando seu primeiro projeto com Ionide

Para criar um novo projeto de F #, abra o código do Visual Studio em uma nova pasta (você pode nomeá-lo como desejar).

Em seguida, abra a paleta de comando (**exibição > Paleta comando**) e digite o seguinte:

```
> F# new project
```

Isso é alimentado pelo [FORGE](https://github.com/fsharp-editing/Forge) projeto.

> [!NOTE]
Se você não vir Opções de modelo, tente atualizar modelos executando o seguinte comando na paleta de comando: `>F#: Refresh Project Templates`.

Selecione "F #: novo projeto" acessando **Enter**. Isso leva você para a próxima etapa para selecionar um modelo de projeto.

Escolha o `classlib` modelo e pressione **Enter**.

Em seguida, selecione um diretório para criar o projeto em. Se você deixar em branco, ele usa o diretório atual.

Por fim, nomeie o projeto na etapa final. F # usa [Pascal case](http://c2.com/cgi/wiki?PascalCase) para os nomes de projeto. Este artigo usa `ClassLibraryDemo` como o nome. Depois de inserir o nome que você deseja para seu projeto, pressione **Enter**.

Se você seguiu a etapa anterior, você deve obter o Visual Studio código espaço de trabalho no lado esquerdo seja exibido com o seguinte:

1. O F # projeto em si, sob o `ClassLibraryDemo` pasta.
2. A estrutura de diretório correto para a adição de pacotes por meio de [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Uma plataforma cruzada criar script com [ `FAKE` ](https://fsharp.github.io/FAKE/).
4. O `paket.exe` executável que pode buscar pacotes e resolver as dependências para você.
5. Um `.gitignore` de arquivo se deseja adicionar este projeto ao controle de origem com base no Git.

## <a name="writing-some-code"></a>Escrevendo um código

Abra o *ClassLibraryDemo* pasta.  Você deve ver os seguintes arquivos:

1. `ClassLibraryDemo.fs`, um arquivo de implementação do F # com uma classe definida.
2. `ClassLibraryDemo.fsproj`, um arquivo de projeto F # usado para compilar este projeto.
3. `Script.fsx`, um arquivo de script F # que carrega o arquivo de origem.
4. `paket.references`, um arquivo de Paket que especifica as dependências do projeto.

Abra `Script.fsx`e adicione o seguinte código ao final dele:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Esta função converte uma palavra em uma forma de [Pig latino](https://en.wikipedia.org/wiki/Pig_Latin). A próxima etapa é avaliar usando F # interativo (FSI).

Realce a função inteira (deve ser 11 linhas). Depois de selecioná-la, mantenha o **Alt** chave e clique em **Enter**. Você observará que uma janela pop-up abaixo, e ele deverá mostrar algo assim:

![Exemplo de saída de F # interativo com Ionide](media/getting-started-vscode/vscode-fsi.png)

Isso foi três coisas:

1. Iniciar o processo de FSI.
2. Ele enviado o código realçado sobre o processo FSI.
3. O processo FSI avaliado o código enviados pela.

Porque foi enviado por um [função](../language-reference/functions/index.md), agora você pode chamar essa função com FSI! Na janela interativa, digite o seguinte:

```fsharp
toPigLatin "banana";;
```

Você deve ver o seguinte resultado:

```fsharp
val it : string = "ananabay"
```

Agora, vamos tentar com uma vogal como a primeira letra. Insira o seguinte:

```fsharp
toPigLatin "apple";;
```

Você deve ver o seguinte resultado:

```fsharp
val it : string = "appleyay"
```

A função parece estar funcionando conforme o esperado. Parabéns, você criou sua primeira função F # em código do Visual Studio e avaliadas-lo com FSI apenas!

>[!NOTE]
Como você pode ter observado, as linhas no FSI são finalizadas com `;;`. Isso ocorre porque FSI permite que você insira várias linhas. O `;;` no final permite FSI saber quando o código for concluído.

## <a name="explaining-the-code"></a>Explicando o código

Se você não tiver certeza sobre o que o código está realmente fazendo, aqui está um passo a passo.

Como você pode ver, `toPigLatin` é uma função que usa uma palavra como sua entrada e o converte em uma representação de Pig-latino da palavra. As regras para isso são da seguinte maneira:

Se o primeiro caractere em uma palavra começar com uma vogal, adicione "Sim" para o fim da palavra. Se ele não começa com uma vogal, mover o primeiro caractere para o fim da palavra e "em" adicionar a ele.

Você pode ter observado FSI o seguinte:

```fsharp
val toPigLatin : word:string -> string
```

Isso indica que `toPigLatin` é uma função que aceita um `string` como entrada (chamado `word`) e retorna outro `string`. Isso é conhecido como o [assinatura de tipo da função](https://fsharpforfunandprofit.com/posts/function-signatures/), uma parte fundamental da linguagem F # que é a chave para compreender o código F #. Você também observa isso se você passar o mouse sobre a função no código do Visual Studio.

O corpo da função, você observará duas partes distintas:

1. Uma função interna, chamada `isVowel`, que determina se um determinado caractere (`c`) é uma vogal, verificando se ele corresponde a um dos padrões fornecidos por meio de [correspondência de padrões](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Um [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) expressão que verifica se o primeiro caractere é uma vogal e construções um retorno de valor sem os caracteres de entrada com base em se o primeiro caractere foi uma vogal ou não:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

O fluxo de `toPigLatin` é assim:

Verifique se o primeiro caractere da palavra entrada é uma vogal. Se for, anexe "Sim" para o fim da palavra. Caso contrário, mover o primeiro caractere para o fim da palavra e "em" adicionar a ele.

Há uma coisa final a observar sobre isso: não há nenhuma instrução explícita para retornar da função, ao contrário de muitos outros idiomas lá. Isso ocorre porque o F # é baseada em expressão, e a última expressão no corpo de uma função é o valor de retorno. Porque `if..then..else` em si for uma expressão, o corpo do `then` bloco ou o corpo do `else` bloco será retornado, dependendo do valor de entrada.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Movendo o código de script para o arquivo de implementação

As seções anteriores neste artigo demonstrou uma primeira etapa comum gravar código F #: gravar uma função inicial e executá-la interativamente com FSI. Isso é conhecido como o desenvolvimento controlado por REPL, onde [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) significa "Loop de impressão avaliar leitura". É uma ótima maneira de experimentar a funcionalidade até que você tenha algo em funcionamento.

A próxima etapa no desenvolvimento controlado por REPL é mover o código de trabalho em um arquivo de implementação do F #. Ele pode ser compilado pelo compilador F # em um assembly que pode ser executado.

Para começar, abra `ClassLibraryDemo.fs`.  Você observará que algum código já está em lá. Vá em frente e excluir a definição de classe, mas deixe o [ `namespace` ](../language-reference/namespaces.md) declaração na parte superior.

Em seguida, crie um novo [ `module` ](../language-reference/modules.md) chamado `PigLatin` e copie o `toPigLatin` função nele assim:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Em seguida, abra o `Script.fsx` novamente e excluir todo o `toPigLatin` funcionarão, mas certifique-se de manter as duas linhas seguintes no arquivo:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

A primeira linha é necessária para FSI script para carregar `ClassLibraryDemo.fs`. A segunda linha é uma conveniência: omiti-lo é opcional, mas você precisará digitar `open ClassLibraryDemo` em uma janela FSI se você quiser colocar o `ToPigLatin` módulo no escopo.

Em seguida, na janela FSI, chame a função com o `PigLatin` módulo definido anteriormente:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Sucesso! Obter os mesmos resultados como antes, mas agora carregado de um arquivo de implementação do F #. A principal diferença é que os arquivos de origem F # são compilados em assemblies que podem ser executados em qualquer lugar, não apenas em FSI.

## <a name="summary"></a>Resumo

Neste artigo, você aprendeu:

1. Como configurar o código do Visual Studio com Ionide.
2. Como criar seu primeiro projeto F # com Ionide.
3. Como usar o F # script para gravar sua primeira função F # em Ionide e, em seguida, execute-o no FSI.
4. Como migrar o código de script com fonte de F # e, em seguida, chamar esse código de FSI.

Você agora está pronto para escrever muito mais código F #, usando o código do Visual Studio e Ionide.

## <a name="troubleshooting"></a>Solução de problemas

Aqui estão algumas maneiras que você pode solucionar determinados problemas que possam ser executadas em:

1. Para obter recursos de Ionide de edição de código, os arquivos de F # precisam ser salvo em disco e dentro de uma pasta que está aberta no espaço de trabalho de código do Visual Studio.
2. Se tiver sido feitas alterações no sistema ou instalado Ionide pré-requisitos com código do Visual Studio abrir, reinicie o código do Visual Studio.
3. Verifique que você pode usar o compilador F # e F # interativo da linha de comando sem um caminho totalmente qualificado. Você pode fazer isso digitando `fsc` em uma linha de comando para o compilador de F #, e `fsi` ou `fsharpi` para o Visual F # ferramentas no Windows e Mono no Mac/Linux, respectivamente.
4. Se você tem caracteres inválidos em seus diretórios de projeto, Ionide podem não funcionar.  Se esse for o caso, renomeie os diretórios do projeto.
5. Se nenhum dos comandos Ionide está trabalhando, verifique seu [associações de código do Visual Studio](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) para ver se você estiver substituindo-os por engano.
6. Se Ionide é dividido em seu computador e nenhum deles corrigiu o problema, tente remover o `ionide-fsharp` diretório em seu computador e reinstale o conjunto de plug-in.

Ionide é um projeto de código aberto criado e mantido por membros da comunidade do F #. Reportar problemas e fique à vontade para contribuir no [Ionide-o VSCode: repositório FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).

Se você tiver um problema ao relatório, siga [as instruções para obter logs para usar ao relatar um problema](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Você também pode pedir para obter ajuda da comunidade do F # em e desenvolvedores Ionide o [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre F # e os recursos do idioma, check-out [Tour do F #](../tour.md).
