# Estruturas de seleção

## if-else

Genericamente:

```java
if (expressão) {
    bloco de código a ser executado caso a expressão  seja verdadeira
}
```
> No caso de o bloco de código consistir de apenas uma linha, as chaves ( {} ) não são necessárias.

Caso você deseje executar um outro bloco de código se a expressão for falsa, utilize else dessa forma:

```java
if (expressão) {
    bloco de código a ser executado caso a expressão  seja verdadeira
} else {
    bloco de código a ser executado caso a expressão  seja falsa
}
```

Você ainda pode encadear os if's.

```java
if (c1) {
 ...
} else if (c2) {
 ...
} else if (c3) {
 ...
} else {
 ...
}
```

## switch

O mesmo resultado pode ser obtido usando switch.

```java
switch ( c ) {

    case 1: {...
            }
            break;
    case 2: {...
            }
            break;
    case 3: {...
            }
            break;
    default: {...
            }
            break;
}
```

As instruções `break` são necessárias para evitar que todos os cases sejam executados sequencialmente. No entanto, haverá casos em que você desejará que os cases sejam todos executados sequencialmente até a próxima instrução break.

```java
int numeroDias;

switch(mes) {
    case1:
    case3:
    case5:
    case7:
    case8:
    case10:
    case12: {
        numeroDias=31;
    }
        break;
    case 4:
    case 6:
    case 9:
    case 11: {
     numDays = 30:
    }
        break;
    case 2:
        if ((ano%4)==0&&(ano%100)!=0) {
            numeroDias =29;
        } else {
            numeroDias = 28;
        }
        break;
}
```