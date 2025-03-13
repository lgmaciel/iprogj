# Strings

Manipulamos dados compostos por múltiplos caracteres através de um objeto String.

Uma seqüência de caracteres é chamada de *string* e é implementada no ambiente Java pela classe String.

```java
String args[];
```
O código acima declara um vetor chamado args que conterá referências a objetos String. Podemos fazer uso de strings literais.

```java
"Java is cool!"
```

O compilador aloca um objeto String implicitamente quando encontra uma string literal como a do código acima.

> Objetos String são imutáveis, quer dizer: uma vez criados, não podem ser modificados. Para manipular caracteres usamos os objetos StringBuffer.

Podemos, ainda, concatenar strings. Para isso usamos o operador +.

```java
"Java " + "is" + adj
```