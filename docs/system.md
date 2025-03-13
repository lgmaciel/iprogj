# A classe System

Freqüentemente, um programa precisa acessar recursos do sistema como propriedades, entrada e saída padrão ou a hora atual. Seu programa pode usar estes recursos diretamente do ambiente runtime atual, mas seu programa seu programa só será capaz de rodar no ambiente para o qual foi escrito. Cada vez que você desejar rodar o programa em um novo ambiente, terá de portar o programa reescrevendo as partes do código que são dependentes do sistema.

O ambiente de desenvolvimento Java resolve este problema permitindo que seu programa use recursos do sistema através de uma interface de programação independente do sistema implementada pela classe System.

## Usando a classe System

Todos os métodos e variáveis da classe System são métodos de classe e variáveis de classe. Você não instancia a classe System para usá-la; você usa seus métodos e variáveis diretamente a partir de uma referência a classe System. Você já viu um exemplo disto na lição 2, onde usamos a variável de classe System.out para imprimir ?Hello World!? na saída padrão.

Você chama métodos de classe de forma parecida. Por exemplo, para chamar o método getProperty da classe System, adicione o nome do método ao final do nome da classe separado por um ponto.

System.getProperty(argumento)

O próximo programinha usa a classe System duas vezes, primeiro para pegar o nome do usuário atual e depois para escrever ele na saída padrão.

```java
class UserNameTest {
     public static void main(String[] args) {
        String name;
        name = System.getProperty(?user.name?);
        System.out.println(name);
     }
}
```

Note que este programa nunca instancia um objeto System.

## Os Streams de entrada e saída padrão

Temos três streams padrão, todos são gerenciados pela classe java.lang.System.

- Entrada padrão -  referenciado por System.in
- Saída padrão -  referenciado por System.out
- Saída de erro padrão -  referenciado por System.err

Provavelmente os itens da classe System usados mais freqüentemente são a saída padrão e a saída de erro padrão, que você usa para mostrar texto para o usuário.

Estes streams derivam da classe PrintStream. Você usa um destes três métodos da classe PrintStream para imprimir texto para o stream: print, println ou write.

Os métodos print e println são essencialmente o mesmo; ambos escrevem seu argumento String para o stream. A diferênca entre eles é que println adiciona um caracter de nova-linha no final de sua saída enquanto print não o faz. Em outras palavras, isto

```java
System.out.print("Duke não é um pingüim!\n");
```

é equivalente a isto

```java
System.out.println("Duke não é um pingüim!");
```

O método write é usado menos freqüentemente que os outros dois métodos. O método write escreve bytes para o stream. Use-o para escrever dados que não sejam ASCII.

Os métodos print e println recebem um único argumento. O argumento pode ser de um dos seguintes tipos: Object, String, char[], int, long, float, double e boolean. Há ainda uma versão extra de println que não recebe argumento algum e que simplesmente imprime um ?/n? para o stream.

```java
 class DataTypePrintTest {
         public static void main(String[] args) {

           Thread objectData = new Thread();
           String stringData = "Java Mania";
           char[] charArrayData = { 'a', 'b', 'c' };
           int integerData = 4;
           long longData = Long.MIN_VALUE;
           float floatData = Float.MAX_VALUE;
           double doubleData = Math.PI;
           boolean booleanData = true;

           System.out.println(objectData);
           System.out.println(stringData);
           System.out.println(charArrayData);
           System.out.println(integerData);
           System.out.println(longData);
           System.out.println(floatData);
           System.out.println(doubleData);
           System.out.println(booleanData);
         }
       }
```

Este programa produz a seguinte saída:

```
Thread[Thread-4,5,main]
Java Mania
abc
4
-9223372036854775808
3.40282e+38
3.14159
true 
```