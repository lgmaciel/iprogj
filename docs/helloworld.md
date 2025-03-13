# O programa "Hello World!"

Ao terminar esta lição você terá criado, compilado e executado sua primeira aplicação Java.



## 1º. Criar o código fonte da aplicação

Crie um arquivo chamado HelloWorld.java com o código Java mostrado aqui:

```java
class HelloWorld {

    public static void main (String args[]) {
        System.out.println("Hello World!");
    }

}
```

## 2º. Compilar o código fonte

No prompt de comando digite:

```sh
javac HelloWorld.java
```

Se tudo correr bem, o compilador criará um arquivo chamado HelloWorld.class.

## 3º. Executar a aplicação

No prompt digite:
```sh
java HelloWorld
```

Você deverá ver "Hello World!" escrito na saída padrão.


### Analisando "Hello World!"

Agora que você já viu, compilou e executou aquela que, provavelmente, foi sua primeira aplicação Java, você deve estar imaginando como é que ela funciona e o quanto ela se pareçem com outras aplicações Java.


```java
class HelloWorld {

    public static void main (String args[]) {
        System.out.println("Hello World!");
    }

}
```

A primeira linha inicia um bloco de definição de classe. Uma classe - a pedra fundamental de uma linguagem orientada a objetos - é a parte do código que descreve os dados e comportamentos associados com instâncias dessa classe.

Quando você instancia uma classe você cria um objeto que se pareçe e age de forma semelhante a outras instâncias da mesma classe.

Os dados associados com a classe ou objetos são armazenados em variáveis; os comportamentos associados com uma classe ou objeto são implementados com métodos.

Um exemplo tradicional de objeto no mundo da programação é uma classe que representa um retângulo.

A `classe` deve conter variáveis para a origem do retângulo, sua largura e sua altura. A classe deve também conter um método que calcule a área do retângulo.

Uma `instância da classe` retângulo deve conter a informação para *um retângulo específico*, como as dimensões do piso da sala, ou as dimensões desta página.

Em Java, a forma mais simples de uma definição de classe é:

```java
class Nome {

. . .

}
```

A palavra chave `class` inicia a definição de classe da classe chamada Nome. As variáveis e métodos da classe estão envolvidas pelas chaves que iniciam e finalizam o bloco de definição de classe. O programinha "Hello World!" não possui variáveis e possui um único método chamado main().
 
 

### O método main()

Toda aplicação Java deve possuir um método main() cuja declaração se pareçe com isto:

```java
public static void main(String args[])
```
A declaração do método main() contém três modificadores:

- public: indica que main() pode ser chamado por qualquer objeto
- static: indica que só haverá uma cópia de main() na memória
- void: indica que main() não retorna nenhum valor

### Como o método main() é invocado?

O método main(), em Java, é similar à função main() em C e C++. Quando você executa um programa C ou C++, o runtime inicia seu programa chamando sua função main().

Similarmente, quando o interpretador Java executa uma aplicação (chamando sua classe de controle) ele começa chamando o método main() da classe. O método main(), então, chama todos os outros métodos necessários para rodar sua aplicação.

#### Argumentos para o método main()

Como você pode ver no segmento de código a seguir, o método main() aceita um único argumento: um vetor de strings.

```java
public static void main(String args[])
```

Este vetor de strings é o mecanismo pelo qual o runtime passa informações para sua aplicação. Cada string no vetor é um argumento de linha de comando.

> O número de argumentos em Java difere do número de argumentos em C e C++. 
>
> Em C e C++ o nome do programa também é tomado como argumento. Por exemplo:
> ```sh
> C:\>dump 0000.
> ```
>
> O argumento para dump é 0000, mas dump também entra no vetor argv[] > como argumento.
> 
> Em Java, args[] recebe só 0000, dump fica de fora automaticamente. 

Nosso exemplo não recebe argumento algum, por isso não há muito o que se discutir sobre argumentos por enquanto.

