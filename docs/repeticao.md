# Estruturas de Repetição

## for

Genericamente:

```java
for(inicialização; término; incremento) {
    bloco de código a ser executado enquanto a
    condição de término não for satisfeita.
}
```

`inicialização` é o código de inicialização da variável que será o *flag* do loop for. Por exemplo:

```java
int i = 0;
```

`término` é a condição que é avaliada a cada interação do loop for e que determina quando o loop deve ser encerrado. Por exemplo:

```java
i<=10;
```

`incremento` é o código que incrementa a variável que está sendo usada como flag. Por exemplo:

```java
i++;
```


O resultado fica assim:

```java
int i;
int tamanho = a.length(); // suponha que a é um vetor

for (i=0; i<tamanho; i++) {
    ...
}
```

Ou, declando `i` no próprio bloco `for` e usando o resultado de `a.length() diretamente, sem guardá-lo em uma variável auxiliar:

```java
for (int i=0; i<a.length(); i++) {
    ...
}
```

## do-while

Genericamente:

```java
do {
    bloco de código a ser executado
} while (expressão);
```

O bloco de código é executado enquanto expressão for verdadeiro.

## while

Genericamente:

```java
while (expresão) {
    bloco de código a ser executado
}
```

O bloco de código é executado enquanto expressão for verdadeiro.

Note que no caso de do-while, o bloco de código é executado pelo menos uma vez. 