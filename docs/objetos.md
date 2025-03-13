# Objetos (declaração, instanciação e inicialização)

Nesta lição veremos o que é preciso fazer para criar os objetos que usaremos em nossos programas. Já que um objeto é uma instância de uma classe, para criar um objeto você deve usar uma classe. Veremos, também, que a criação de um objeto passa por três etapas:

Veja a linha de código a seguir:

```java
Date hoje = new Date();
```

Esta é uma linha de código que cria um objeto do tipo Date chamado hoje. Temos que identificar as operações que estão ocorrendo nesta linha (declaração, instanciação e inicialização). Date hoje é uma declaração de variável. Ela só está dizendo ao compilador que o nome hoje será utilizado para referenciar um objeto do tipo Date. O operador new instancia um novo objeto Date. Date() inicializa o objeto.

## Declaração

Uma declaração de objeto pode aparecer sozinha, como uma declaração de variáveis

```java
Date hoje;
```

ou, como geralmente ocorre, acompanhando a linha de criação do objeto (como ocorreu no exemplo acima).

De qualquer maneira, a declaração de um objeto é igual a declaração de uma variável:

```
tipo nome
```

`tipo` é o tipo do objeto e `nome` o nome do objeto.

Em Java, classes e interfaces são como tipos de dados, por isso tipo pode ser o nome de uma classe (como Date) ou o nome de uma interface (interfaces são discutidas posteriormente).

A linha `Date hoje`, não instancia o objeto (não cria), só informa ao compilador que `hoje` estará se referindo a um objeto `Date`. Para instanciar um objeto você usa o operador `new`.

## Instanciação

O operador new instancia um novo objeto alocando memória para ele. Este operador requer um único argumento: uma chamada a um construtor. Construtores são métodos responsáveis pela inicialização de novos objetos. Resumindo: o operador new cria o objeto e o construtor o inicializa.

Veja o exemplo:

```java
new Rectangle(0,0,100,200);
```

`Rectangle(0,0,100,200)` é uma chamada a um construtor da classe Rectangle.

O operador new retorna uma referência para o novo objeto criado. Esta referencia pode ser atribuida a uma váriavel do tipo apropriado.

```java
Rectangle rect = new Rectangle(0,0,100,200);
``` 

## Inicialização

As classes provêem construtores para inicializar seus objetos. Os construtores vão attribuir valores às variáveis do objeto. Uma classe pode disponibilizar vários construtores para que sejam possíveis diversas formas de inicialização. Se você for olhar a implementação da classe, será fácil identificar quais são os métodos construtores porque eles têm o mesmo nome da classe e não têm um tipo de retorno.

No inicio da lição vimos a seguinte linha:

```java
Date hoje = new Date();
```

`Date()` é um construtor que não recebe argumento algum. Este tipo de construtor é conhecido como o construtor padrão. Todas as classes têm pelo menos um construtor: o padrão. 