# Tratamento de exceções

Todos sabemos que ocorrem erros nos programas de computador; mas o que realmente importa é o que acontece depois de ocorrer um erro. Como o erro é tratado? Como tratá-lo? O programa pode se recuperar?

A linguagem Java usa exceções para dar capacidade aos programas de tratar erros. Uma exceção é um evento que ocorre durante a execução de um programa que rompe o fluxo normal de instruções. Se você já andou tentando escrever algum código Java diferente dos exemplos apresentados anteriormente, provavelmente você já se deparou com uma mensagem parecida com essa:

```
InputFile.java:9: Exception java.io.FileNotFoundException must be caught, or it must be declared in the throws clause of this method.
                fis = new FileInputStream(filename);
                      ^
```

Esta mensagem indica que o compilador encontrou uma exceção que não está sendo tratada. A linguagem Java requer que um método ou apanhe todas as exceções retornadas pelos métodos dos objetos que ele está usando ou especifique que ele pode retornar este tipo de exceção.

> Obs.: O termo "exceção" na verdade vem de "evento excepcional", ou seja, algo bem diferente de exceção.

## O que são exceções?

Uma exceção é um evento que ocorre durante a execução de um programa que rompe o fluxo normal de instruções.

Muitos tipos de erros podem causar uma exceção. Estes erros podem ir desde sérios problemas de hardware, como uma falha geral no HD, até erros simples de programa, como tentar acessar um elemento que está fora de um array (ArrayIndexOutOfBoundsException). Quando tal erro ocorre em um método, o método cria um objeto Exception e o etrega ao sistema runtime. Este objeto Exception contém informações sobre a exceção, incluindo o tipo e o estado do programa quando o erro ocorreu. O sistema runtime é então responsável por achar algum código para tratar o erro. Na terminologia do Java, criar uma um objeto Exception e entregá-lo ao sistema runtime é chamado jogar (throw) uma exceção.

Depois que um método devolve uma exceção, o runtime procura alguém para tratar a exceção. O conjunto dos possíveis "alguéms" que podem tratar a exceção é o conjunto de métodos na pilha de chamada do método onde o erro ocorreu. O runtime procura de trás para frente através da pilha de chamada, começando com o método onde ocorreu o erro, até que ele encontre um método que contenha um exception handler (código que irá tratar a exceção) apropriado. Um exception handler é considerado apropriado se o tipo de exceção devolvida é do mesmo tipo que a exceção tratada pelo handler. Dizemos que o exception handler escolhido apanhou (catch) a exceção.

Se o runtime procurar em todos os métodos e não encontrar o exception handler apropriado ele irá terminar (conseqüentemente seu programa também).
 
Separando o código normal do código de tratamento de erros

Na programação tradicional, a detecção, documentação e tratamento de erros geralmente leva ao famoso e confuso código espaguete. Por exemplo, suponha que você tem uma função que lê um arquivo inteiro na memória. Em pseudocódigo, sua função seria algo assim:

```java
lerArquivo() {
        abrir o arquivo;
        determinar seu tamanho;
        alocar aquela quantidade de memória;
        ler o arquivo na memória
        fechar o arquivo;
}
```
Em uma primeira olhada, esta função parece bastante simples, mas ela ignora todos estes erros em potencial:

- O que acontece se o arquivo não puder ser aberto?
- O que acontece se o tamanho do arquivo não puder ser determinado?
- O que acontece se não puder ser alocada memória suficiente?
- O que acontece se a leitura falhar?
- O que acontece se o arquivo não puder ser fechado?

Para responder estas questões quanto a sua função lerArquivo, você tem que adicionar uma porção de código para fazer a detecção do erro, documentação e tratamento. Sua função poderia acabar parecendo algo assim:

```java
codigoDoErro lerArquivo() {
    inicializa codigoErro = 0;
    abrir o arquivo
    if (oArquivoEstaAberto) {
        determinar o tamanho do arquivo;
        if (conseguimosTamanhoArquivo) {
            alocar esta quantidade de memória;
            if (conseguimosAlocarEstaQuantidade) {
                ler o arquivo na a memória;
                if (leituraFalhou) {
                    codigoErro = -1;
                }
            } else {
                codigoErro = -2;
              }
        } else {
                codigoErro = -3;
            }
        fechar arquivo;
        if (ArquivoNaoFechou && codigoErro == 0) {
            codigoErro = -4;
        } else {
            codigoErro = codigoErro e -4;
            }
    } else {
        codigoErro = -5;
    }
    return codigoErro;
}
```

Com a detecção do código embutida, suas 7 linhas de código originais (em negrito) foram inchadas e se tornaram 29 linha de codigo. Pior, há tanto código para detectar, documentar e retornar que as 7 linhas originais ficaram perdidas na bagunça. Pior ainda, o fluxo lógico do código também se perdeu na bagunça, tornando difícil dizer se o código está fazendo a coisa certa.

O Java nos dá uma solução elegante para o problema do gerenciamento de erros: exceções. As exceções permitem que você escreva o fluxo principal de seu código e trate dos casos excepcionais em outro lugar. Veja como fica a função lerArquivo usando exceções:

```java
lerArquivo() {
    try {
        abrir o arquivo;
        determinar seu tamanho;
        alocar aquela quantidade de memória;
        ler o arquivo na memória
        fechar o arquivo;
    } catch (aberturaArquivoFalhou) {
        fazer algo aqui;
    } catch (determinarTamanhoFalhou) {
        fazer algo aqui;
    } catch (alocacaoDeMemóriaFalhou) {
        fazer algo aqui;
    } catch (leituraFalhou) {
        fazer algo aqui;
    } catch (fechamentoFalhou) {
        fazer algo aqui;
    }
}
```

Repare que as exceções não livram você do trabalho de detectar, documentar e tratar os erros. O que as exceções lhe proporcionam são as formas de separar os detalhes de o que fazer quando algo fora do ordinário acontece da lógica principal do programa. Repare também que ficamos com 19 linhas ao invés de 29 e ainda fizemos um trabalho mais eficiente e limpo.
 
## Apanhando e tratando exceções

Veremos, agora, como como apanhar e como tratar uma exceção. O exemplo abaixo define e implementa a classe chamada ListOfNumbers. A classe ListOfNumbers chama dois métodos de classes que estão nos pacotes do Java que podem devolver exceções.

```java
import java.io.*;
import java.util.Vector;

class ListOfNumbers {
    private Vector victor;
    final int size = 10;

    public ListOfNumbers () {
        int i;
        victor = new Vector(size);
        for (i = 0; i < size; i++)
            victor.addElement(new Integer(i));
    }

    public void writeList() {
        PrintStream pStr = null;

        System.out.println("Entering try statement");
        int i;
        pStr = new PrintStream(
                  new BufferedOutputStream(
                     new FileOutputStream("OutFile.txt")));

        for (i = 0; i < size; i++)
            pStr.println("Value at: " + i + " = " + victor.elementAt(i));

        pStr.close();
    }
}
```

A classe ListOfNumbers cria um Vector que contém dez elementos Integer com valores sequenciais de 0 a 9. Ela também define um método chamado writeList que grava a lista de números em um arquivo texto chamado OutFile.txt.

O método writeList chama dois métodos que podem devolver exceções. A linha a seguir invoca o construtor para FileOutputStream, que devolve uma IOException se o arquivo não pode se aberto por alguma razão:

```java
pStr = new PrintStream(
            new BufferedOutputStream(
                new FileOutputStream("OutFile.txt")));
```

O método elementAt da classe Vector devolve uma ArrayIndexOutOfBoundsException se você tentar acessar um índice que é muito pequeno (um valor negativo) ou muito grande (maior do que o número de elementos contidos no vetor).

```java
pStr.println("Value at: " + i + " = " + victor.elementAt(i));
```
Se você tentar compilar a classe ListOfNumbers, o compilador imprime uma mensagem de erro sobre a exceção devolvida pelo construtor FileOutputStream mas não mostra nada sobre a exceção devolvida por elementAt. Isto é porque a exceção devolvida por FileOutputStream (IOException) é uma checked exception (um tipo de exceção que somos obrigados a tratar ou a fazer algo com ela pois é verificada pelo compilador) e a exceção devolvida pelo método elementAt (ArrayIndexOutOfBoundsException) é uma runtime exception (um tipo de exceção que não somos obrigados a tratar).

Veremos, agora, como escrever um exception handler para apanhar e tratar tais exceções. São três os componentes de um exception handler: try, catch e finally.

## O bloco try

O primeiro passo para se construir um exception handler é encerrar as linhas de código que podem devolver uma exceção com um bloco try. Dizemos que o bloco try governa o código encerrado nele e define o escopo de qualquer exception handler (estabelecido pelos blocos catch subseqüentes) associado a ele. Em geral, um bloco try fica assim:

```java
try {
    código Java que pode retornar uma exceção
}
```

A lista a seguir usa um único try para todo o método porque o código tende a ficar mais fácil de ler.

```java
PrintStream pstr;

          try {
              int i;

              System.out.println("Entering try statement");
              pStr = new PrintStream(
                        new BufferedOutputStream(
                           new FileOutputStream("OutFile.txt")));

              for (i = 0; i < size; i++)
                  pStr.println("Value at: " + i + " = " + victor.elementAt(i));
          }
```

Se uma exceção ocorrer dentro do bloco try, esta exceção é tratada pelo exception handler associado a este try.  Um try deve estar acompanhado de pelo menos um bloco catch ou um bloco finally.
 

## O(s) bloco(s) catch

Você associa exception handlers a um try dando-lhe um ou mais blocos catch, assim:

```java
try {
    ...
{ catch ( ... ) {
    ...
} catch ( ... ) {
    ...
} ...
```

A forma geral para um bloco catch é:

```java
catch (umObjetoThrowable nomeDeVariável) {
    código Java que irá tratar a exceção;
}
```

Como você pode ver, o bloco catch requer um único argumento formal. O argumento para o catch se parece com a declaração de um argumento para um método. O tipo do argumento, umObjetoThrowable, declara o tipo da exceção que o handler pode tratar e deve ser o nome de uma classe que seja subclasse da classe Throwable. nomeDeVariável é o nome pelo qual o handler pode fazer referência a exceção apanhada pelo handler. Por exemplo, o exception handler do método writeList chama o método getMessage da exceção usando o nome declarado para a exceção e:

```java
e.getMessage();
```

O novo método writeList usa dois exception handlers para o seu bloco try, com um handler para cada tipo de exceção que pode ser retornada no bloco: ArrayIndexOutOfBounds e IOException.

```java
try {
              . . .

    } catch (ArrayIndexOutOfBoundsException e) {
        System.err.println("Caught ArrayIndexOutOfBoundsException: "+
            e.getMessage());
    } catch (IOException e) {
        System.err.println("Caught IOException: " + e.getMessage());
    }
```

Vamos supor que ocorreu uma IOException dentro do bloco try. O sistema runtime imediatamente tenta localizar um exception handler apropriado. O runtime inicia sua procura no topo da pilha de chamada. Quando a exceção ocorreu, o construtor FileOutputStream estava no topo da pilha. No entanto, o construtor FileOutputStream não tem um exception handler apropriado então o runtime verifica o próximo método na pilha de chamada: o método writeList. O método writeList tem dois exception handlers: um para ArrayIndexOutOfBoundsException e um para IOException.

O runtime analisa os handler do writeList na ordem em que eles aparecem após o try. O primeiro exception handler cujo argumento coincidir com a exceção retornada é aquele que será escolhido pelo runtime para tratar a exceção. O argumento para o primeiro exception handler é ArrayIndexOutOfBoundsException, mas a exceção devolvida foi uma IOException, então o runtime continua sua procura por um event handler apropriado. O argumento para o segundo event handler o writeList é uma IOException. A exceção devolvida pelo construtor FileOutputStream é também uma IOException é pode ser atribuída legalmente ao argumento IOException do handler. Portanto este handler é escolhido e o runtime o executa; então o handler imprime:

```
Caught IOException: OutFile.txt
``` 

## O bloco finally

O passo final na construção de um event handler é prover um mecanismo que faça a limpeza do método antes (possivelmente) de permitir que o controle seja passado para outra parte do programa. Você faz isso encerrando o código de limpeza em um bloco finally. Você pode usar o bloco finally para fechar arquivos ou liberar outros recursos do sistema.

O bloco try do método writeList abre um PrintStream. O programa deve fechar aquele stream andes de permitir que o controlo passe para fora do método writeList. Isto nos deixa em uma situação um tanto complicada porque o bloco try do writeList tem três possibilidades de encerramento diferentes:

- A instrução new FileOutputStream falhou e devolveu uma IOException.
- A instrução victor.elementAt(i) falhou e devolveu uma ArrayIndexOutOfBoundsException.
- Tudo ocorreu bem e o bloco try encerrou normalmente.

O sistema runtime sempre executa as instruções de um bloco finally não importando o que aconteca no bloco try. Este é o bloco finally para o método writeList. Ele limpa e fecha o PrintStream.

```java
finally {
    if (pStr != null) {
        System.out.println("Closing PrintStream");
        pStr.close();
    } else {
        System.out.println("PrintStream not open");
    }
}
```

Quando todos os componentes são colocados juntos, o método write list fica assim:

```java
public void writeList() {
    PrintStream pStr = null;

    try {
        int i;

        System.out.println("Entering try statement");
        pStr = new PrintStream( new BufferedOutputStream(new
                                        FileOutputStream("OutFile.txt")));
        for (i = 0; i < size; i++)
            pStr.println("Value at: " + i + " = " + victor.elementAt(i));
    } catch (ArrayIndexOutOfBoundsException e) {
        System.err.println("Caught ArrayIndexOutOfBoundsException: " +
                                e.getMessage());
    } catch (IOException e) {
        System.err.println("Caught IOException: " + e.getMessage());
    } finally {
        if (pStr != null) {
            System.out.println("Closing PrintStream");
            pStr.close();
        } else {
            System.out.println("PrintStream not open");
        }
    }
 }
```

## Especificando as exceções devolvidas por um método

Se não é apropriado que seu método apanhe e trate uma exceção jogada por um dos métodos que ele chama, ou se o seu método joga sua própria exceção, você deve especificar isto na declaração do método.

Para dizer que writeList devolve ArrayIndexOutOfBoundsException e IOException ao invés de apanhá-las, você adiciona uma cláusula throws na declaração do método. A cláusula throws é composta pela palavra-chave throws seguida de uma lista separada por virgulas de todoas as exceções que o método devolve. A cláusula throws vai após o nome do método e sua lista de argumentos e antes da chave ( { ) que define o escopo do método. Por exemplo:

```java
public void writeList() throws IOException, ArrayIndexOutOfBoundsException {
```

Lembre-se de que ArrayIndexOutOfBoundsException é uma runtime exception, portanto você não precisa especificá-la na cláusula throws, ainda que possa fazer se quiser.