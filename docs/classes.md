# Criando Classes

Vejamos agora como escrever as classes que utilizaremos para criar nossos objetos.

> Relembrando: uma classe é um modelo para suas instâncias (os objetos).

## Declaração

A declaração da classe declara qual o nome da classe e outros atributos como: superclasse, se é uma classe publica, abstrata ou final... No mínimo, a declaração de uma classe deve conter a palavra-chave class e o nome da classe que se está definindo.

```java
class NomedaClasse {
 ...
}
```

Vejamos o código para declarar uma classe chamada Geral:

```
class Geral {
  ...
}
```

Os nomes de classe, por convenção, começam por letra maiúscula. Além disso, os nomes escolhidos devem ser identificadores Java válidos.

Uma declaração de classe da forma apresentada acima, será geralmente a mais usada. Contudo, na declaração de uma classe podemos dizer muito mais sobre a classe. Podemos:

- declarar qual a superclasse da classe;
- listar quais interfaces esta classe implementa;
- dizer se a classe é do tipo public, abstract ou final

## A Superclasse

Mesmo que você não declare a superclasse de sua classe, ainda assim ela terá uma. Se não especificarmos a superclasse, será assumido que nossa classe tem como superclasse a classe Object (declarada em java.lang). Portanto, a superclasse da classe que definimos acima é Object.

Para especificarmos a superclasse de nossa classe, usamos, após o nome da classe,  a palavra-chave extends seguida do nome da superclasse, assim:

```java
class NomedaClasse extends NomedaSuperclasse {
  ...
}
```

Portanto, a linha de definição da classe que criamos acima é, na verdade, esta.

```java
class Geral extends java.lang.Object {
  ...
 }
```

## Listando as interfaces implementadas

Vamos começar esclareçendo o que é uma interface. Uma interface simplesmente declara um conjunto de constantes e métodos que não possuem nenhuma implementação. Quando a classe implementa uma interface, ela deve prover a implementação para os métodos declarados na interface.

Para declarar que a classe implementa uma ou mais interfaces, usamos a palavra-chave implements seguida por uma lista separada por virgulas das interfaces implementadas.

```java
class NomedaClasse extends Superclasse implements Interface {
 ...
}
```

## Public, Abstract e Final

Estes são modificadores para a classe. Eles vão antes do nome da classe na declaração e são opcionais.

`public` - é padrão uma classe só poder ser usada por classes que estão no mesmo pacote em que ela está declarada. O modificador public declara que a classe pode ser usada por objetos que estão fora do pacote atual. Por convenção, se for usado public, ele será o primeiro ítem na linha de declaração de uma classe.

`abstract` - declara que a classe é uma classe abstrata. Uma classe abstrata é uma classe que só serve para ser subclasseada, por isso não pode ser instanciada.

`final` - declara que a classe não pode ser subclasseada.

## Estrutura geral do corpo de uma classe

O corpo da classe é dividido em duas partes:

- variáveis membro (que representam os estados da classe);
- métodos membro (que implementam os comportamentos da classe).

Apesar de não ser necessário, costumamos declarar as variáveis membro da classe primeiro.

Ex:
```java
public class UmaQualquer extends QualquerOutra {
    int x,y;
    float a;
    float calcula(int rx, int ry) {
        x = rx; y = ry;
        return a = x / y;
    }
}
```

### Declarando as variáveis membro

Uma declaração de variável membro deve conter, no mínimo, o tipo de dado da variável e seu nome.

```
tipo nomedaVariável;
```
Observe as declarações das variáveis membro feitas no exemplo acima

```java
 public class UmaQualquer extends QualquerOutra {
    int x,y;
    float a;
    float calcula(int rx, int ry) {
        x = rx; y = ry;
        return a = x / y;
    }
 }
 ```

e repare que elas aparecem dentro do corpo da classe e fora da declaração de um método. Esta posição, ou escopo, define que estas são variáveis membro da classe.

Um nome de variável membro, assim como de qualquer outra variável em Java, deve ser um identificador Java válido e, por convenção, deve começar por letra minúscula.

Não podemos declarar duas variáveis membro com o mesmo nome em uma mesma classe, mas podemos delcarar um método com o mesmo nome de uma classe.

```java
class UmaQualquer {
    int calcula, x, y;

    float calcula(int rx, int ry) {
        x = rx; y = ry;
        return (x/y);
    }
}
```

Além do tipo da variável, podemos especificar uma série de atributos quando declaramos uma variável membro: o acesso que outros objetos terão a essa variável; se ela será uma variável somente da classe ou instanciável ou se ela é uma constante.

Podemos resumir a declaração das variáveis membro com a seguinte sintaxe:

```
[especificadordeAcesso] [static] [final] [transient] [volatile] tipo nomedaVariável
```
