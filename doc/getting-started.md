---
# SPDX-FileCopyrightText: 2006-2024 John MacFarlane.

# SPDX-License-Identifier: GPL-2.0-or-later
# Documentation licensed under the GNU General Public License Version 2 or
# later.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docsdevbr/pandoc-website-pt-br/blob/-/LICENSES/GPL-2.0-or-later.txt

source_url: https://github.com/jgm/pandoc/blob/3.12/doc/getting-started.md
source_revision: 80303beb35cff4ae8aab571a65d4e0938f0a7970
translation_status: ready

title: Primeiros passos com o pandoc
author: John MacFarlane
---

Este documento destina-se a pessoas que não estão familiarizadas com ferramentas
de linha de comando.
Especialistas em linha de comando podem ir diretamente para o
[Guia da Pessoa Usuária](https://pandoc.org/MANUAL.html)
ou para a página de manual do pandoc.

# Passo 1: instale o pandoc

Primeiro, instale o pandoc seguindo as
[instruções para a sua plataforma](https://pandoc.org/installing.html).

# Passo 2: abra um terminal

O pandoc é uma ferramenta de linha de comando.
Não possui interface gráfica de pessoa usuária.
Portanto, para usá-lo, você precisará abrir uma janela de terminal:

- No OS X, a aplicação Terminal pode ser encontrada em
  `/Applications/Utilities`.
  Abra uma janela do Finder e vá para `Applications` e, em seguida, `Utilities`.
  Depois, clique duas vezes em `Terminal`.
  (Ou clique no ícone da lanterna no canto superior direito da tela e digite
  `Terminal` — você deverá ver o `Terminal` em `Applications`.)

- No Windows, você pode usar o prompt de comando clássico ou o terminal
  PowerShell, que é mais moderno.
  Se você usa o Windows no modo desktop, execute o comando `cmd` ou `powershell`
  a partir do menu Iniciar.
  Se você usa a tela inicial do Windows 8, basta digitar `cmd` ou `powershell`
  e, em seguida, executar a aplicação "Prompt de Comando" ou
  "Windows PowerShell".
  Se estiver usando o `cmd`, digite `chcp 65001` antes de usar o pandoc para
  definir a codificação como UTF-8.

- No Linux, existem muitas configurações possíveis, dependendo do ambiente de
  desktop que você está usando:

  * No Unity, use a função de busca no `Dash` e procure por `Terminal`.
    Ou use o atalho de teclado `Ctrl-Alt-T`.
  * No Gnome, vá para `Applications`, depois `Accessories` e selecione
    `Terminal`, ou use `Ctrl-Alt-T`.
  * No XFCE, vá para `Applications`, depois `System` e `Terminal`, ou use
    `Super-T`.
  * No KDE, vá para `KMenu`, depois `System` e `Terminal Program (Konsole)`.

Agora você deve ver um retângulo com um "prompt" (possivelmente apenas um
símbolo como `%`, mas provavelmente incluindo mais informações, como seu nome de
usuário e diretório) e um cursor piscando.

Vamos verificar se o pandoc está instalado.
Digite

    pandoc --version

e pressione Enter.
Você deverá ver uma mensagem informando qual versão do pandoc está instalada e
fornecendo algumas informações adicionais.

# Passo 3: mudando de diretório

Primeiro, vamos ver onde estamos.
Digite

    pwd

no Linux ou OSX, ou

    echo %cd%

no Windows, e pressione Enter.
O terminal deve exibir o seu diretório de trabalho atual.
(Consegue adivinhar o que `pwd` significa?)
Esse deve ser o seu diretório pessoal.

Vamos navegar agora para o diretório `Documents`: digite

    cd Documents

e pressione Enter.
Agora digite

    pwd

(ou `echo %cd%` no Windows) novamente.
Você deve estar no subdiretório `Documents` do seu diretório pessoal.
Para voltar ao diretório pessoal, você pode digitar

    cd ..

O `..` significa "um nível acima".

Volte para o diretório `Documents` se ainda não estiver lá.
Vamos tentar criar um subdiretório chamado `pandoc-test`:

    mkdir pandoc-test

Agora, entre no diretório `pandoc-test`:

    cd pandoc-test

Se o prompt não indicar em qual diretório você está, você pode confirmar sua
localização executando

    pwd

(ou `echo %cd%`) novamente.

Certo, isso é tudo o que você precisa saber por enquanto sobre o uso do
terminal.
Mas aqui vai um segredo que vai poupar você de muita digitação.
Você pode sempre usar a tecla de seta para cima para percorrer o histórico
de comandos.
Assim, se quiser usar um comando que digitou anteriormente, não precisa
digitá-lo novamente: basta usar a seta para cima até que ele apareça.
Experimente.
(Você também pode usar a seta para baixo para navegar na direção oposta.)
Após encontrar o comando, pode usar as setas para a esquerda e para a direita e
a tecla Backspace/Delete para editá-lo.

A maioria dos terminais também suporta o preenchimento automático de nomes de
diretórios e arquivos via tecla Tab.
Para testar isso, vamos primeiro voltar ao diretório `Documents`:

    cd ..

Agora, digite

    cd pandoc-

e pressione a tecla Tab em vez de Enter.
Seu terminal deve completar o restante (`test`), e então você pode pressionar
Enter.

Para recapitular:

- `pwd` (ou `echo %cd%` no Windows) para ver qual é o diretório de trabalho
  atual.
- `cd foo` para mudar para o subdiretório `foo` do seu diretório de trabalho.
- `cd ..` para subir para o diretório pai do diretório de trabalho.
- `mkdir foo` para criar um subdiretório chamado `foo` no diretório de trabalho.
- seta para cima para navegar pelo histórico de comandos.
- tecla Tab para completar nomes de diretórios e arquivos.

# Passo 4: usando o pandoc como filtro

Digite

    pandoc

e pressione Enter.
Você deverá ver o cursor parado, aguardando que você digite algo.
Digite o seguinte:

    Hello *pandoc*!

    - one
    - two

Quando terminar (o cursor deve estar no início da linha), digite `Ctrl-D` no OS
X ou Linux, ou `Ctrl-Z` seguido de `Enter` no Windows.
Agora você deverá ver seu texto convertido para HTML!

    <p>Hello <em>pandoc</em>!</p>
    <ul>
    <li>one</li>
    <li>two</li>
    </ul>

O que acabou de acontecer?
Quando o pandoc é invocado sem especificar arquivos de entrada, ele opera como
um "filtro", recebendo a entrada do terminal e enviando a saída de volta para o
terminal.
Você pode usar esse recurso para experimentar o pandoc.

Por padrão, a entrada é interpretada como pandoc markdown e a saída é HTML.
Mas podemos mudar isso.
Vamos tentar converter *de* HTML *para* markdown:

    pandoc -f html -t markdown

Agora digite:

    <p>Hello <em>pandoc</em>!</p>

e pressione `Ctrl-D` (ou `Ctrl-Z` seguido de `Enter` no Windows).
Você deverá ver:

    Hello *pandoc*!

Agora tente converter algo de markdown para LaTeX.
Que comando você acha que deve usar?

# Passo 5: noções básicas sobre editores de texto

Provavelmente você vai querer usar o pandoc para converter um arquivo, e não
para ler texto diretamente no terminal.
Isso é simples, mas primeiro precisamos criar um arquivo de texto no nosso
subdiretório `pandoc-test`.

**Importante:** Para criar um arquivo de texto, você precisará usar um editor de
texto, *não* um processador de texto como o Microsoft Word.
No Windows, você pode usar o `Bloco de Notas` (em `Acessórios`).
No OS X, você pode usar o `TextEdit` (em `Applications`).
No Linux, diferentes plataformas vêm com diferentes editores de texto: o Gnome
tem o `GEdit` e o KDE tem o `Kate`.

Abra o seu editor de texto.
Digite o seguinte:

    ---
    title: Test
    ...

    # Test!

    This is a test of *pandoc*.

    - list one
    - list two

Agora, salve o arquivo como `test1.md` no diretório `Documents/pandoc-test`.

Nota: Se você trabalha muito com texto simples, vai querer um editor melhor do
que o `Bloco de Notas` ou o `TextEdit`.
Você pode dar uma olhada no
[Visual Studio Code](https://code.visualstudio.com/)
ou no [Sublime Text](https://www.sublimetext.com/) ou (se estiver disposto a
dedicar um tempo para aprender uma interface diferente) no
[Vim](https://www.vim.org) ou no [Emacs](https://www.gnu.org/software/emacs).

# Passo 6: convertendo um arquivo

Volte ao seu terminal.
Você ainda deve estar no diretório `Documents/pandoc-test`.
Verifique isso com o comando `pwd`.

Agora digite

    ls

(ou `dir` se estiver no Windows).
Isso listará os arquivos no diretório atual.
Você deve ver o arquivo que criou, `test1.md`.

Para convertê-lo para HTML, use este comando:

    pandoc test1.md -f markdown -t html -s -o test1.html

O nome do arquivo `test1.md` indica ao pandoc qual arquivo converter.
A opção `-s` instrui a criação de um arquivo "independente", com cabeçalho e
rodapé, e não apenas um fragmento.
E a opção `-o test1.html` indica que a saída deve ser salva no arquivo
`test1.html`.
Observe que poderíamos ter omitido `-f markdown` e `-t html`, já que o padrão é
converter de Markdown para HTML, mas não faz mal incluí-los.

Verifique se o arquivo foi criado digitando `ls` novamente.
Você deve ver `test1.html`.
Agora, abra-o em um navegador.
No OS X, você pode digitar

    open test1.html

No Windows, digite

    .\test1.html

Você deverá ver uma janela do navegador exibindo seu documento.

Para criar um documento LaTeX, basta alterar ligeiramente o comando:

    pandoc test1.md -f markdown -t latex -s -o test1.tex

Tente abrir o arquivo `test1.tex` no seu editor de texto.

O pandoc geralmente consegue identificar os formatos de entrada e saída a partir
das extensões dos arquivos.
Portanto, você poderia ter usado apenas:

    pandoc test1.md -s -o test1.tex

O pandoc sabe que você está tentando criar um documento LaTeX devido à extensão
`.tex`.

Agora, tente criar um documento do Word (com a extensão `docx`).

Se quiser criar um PDF, você precisará ter o LaTeX instalado.
(Consulte o [MacTeX](https://tug.org/mactex/) no OS X,  o
[MiKTeX](https://miktex.org) no Windows ou instale o pacote texlive no Linux.)
Em seguida, execute

    pandoc test1.md -s -o test1.pdf

# Passo 7: opções de linha de comando

Agora você já conhece o básico.
O pandoc possui muitas opções.
Neste ponto, você pode começar a aprender mais sobre elas lendo o
[Guia da Pessoa Usuária](https://pandoc.org/MANUAL.html).

Aqui está um exemplo.
A opção `--mathml` faz com que o pandoc converta expressões matemáticas em TeX
para MathML.
Digite

    pandoc --mathml

e, em seguida, insira este texto, seguido de `Ctrl-D` (`Ctrl-Z` seguido de
`Enter` no Windows):

    $x = y^2$

Agora tente fazer o mesmo sem a opção `--mathml`.
Percebeu a diferença na saída?

Se você esquecer uma opção ou quais formatos são suportados, pode sempre usar

    pandoc --help

para obter uma lista de todas as opções suportadas.

Em sistemas OS X ou Linux, você também pode usar

    man pandoc

para acessar a página de manual do pandoc.
Todas essas informações também estão disponíveis no Guia da Pessoa Usuária.

Se tiver dificuldades, você pode sempre fazer perguntas no
[fórum de discussão](https://github.com/jgm/pandoc/discussions).
Mas não deixe de consultar as [FAQs](https://pandoc.org/faqs.html) primeiro
e pesquisar no fórum para ver se a sua dúvida já foi
respondida anteriormente.

If you get stuck, you can always ask questions on the
[discussion forum](https://github.com/jgm/pandoc/discussions).
But be sure to check the [FAQs](https://pandoc.org/faqs.html) first,
and search through the forum to see if your question has
been answered before.

