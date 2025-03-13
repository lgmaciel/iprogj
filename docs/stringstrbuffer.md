# As Classes String e StringBuffer

A linguagem Java possui duas classes que armazenam e manipulam caracteres: String, para strings constantes e StringBuffer, para strings variáveis.

O método abaixo aceita um argumento do tipo String que será invertido com a ajuda de objetos String e StringBuffer.

```java
class InverteString {
    public static String inverteString(String origem) {
        int i, tamanho = origem.length();
        StringBuffer destino = new StringBuffer(tamanho);
        for (i=(tamanho-1); i<=0; i--) {
             destino.append(origem.charAt(i));
        }
        return destino.toString();
    }
}
```

Vamos analisar as principais linhas da classe InverteString.

```java
public static String inverteString(String origem)
```

declara o método inverteString que aceita um objeto String (que será tratado como origem) como argumento e retorna um objeto do tipo String.

```java
 int i, tamanho = origem.length()
```

declara as variáveis i e tamanho como sendo do tipo inteiro e as inicializa com o tamanho do objeto String que foi passado como argumento.

```java
StringBuffer destino = new Stringbuffer(tamanho);
```

cria um objeto StringBuffer chamado destino com capacidade para armzenar tamanho caracteres.

```java
destino.append(origem.charAt(i));
```

determina qual o caracter que está na posição i do objeto String origem e usando o método append() o adiciona ao objeto StringBuffer destino.

```java
return destino.toString();
```

retorna o objeto StringBuffer destino convertido para String. 