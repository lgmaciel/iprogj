# Vetores

Como outras linguagens de programação, Java permite que você manipule múltiplos valores através de vetor. 

A declaração de um vetor possui dois componentes básicos:

- o tipo de dados que o vetor irá guardar
- o nome do vetor.

```
tipo nomedoVetor[];
```

`tipo` é algo como int, float... nomedoVetor é qualquer identificador Java válido. Os colchetes (` [] `) na declaração indicam que `nomedoVetor` é um vetor.

A declaração nao aloca memória para conter os elementos do vetor. Se você tentar acessar ou atribuir algum valor para qualquer elemento que seja do vetor antes de que tenha sido alocada memória o compilador irá imprimir um erro do tipo:

```
"Variable nomedoVetor may not have been initialized".
```

Para alocar memória para o vetor você deve instanciá-lo usando o operador `new`.

```java
int valoresdeX[] = new int[10];
```

Vetores podem conter qualquer tipo de dado válido em Java, inclusive tipos de referência.

