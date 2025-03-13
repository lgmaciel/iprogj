# Implementando métodos


A implementação de um método está dividida em duas partes: a declaração e o corpo do método.

```java
declaraçãodoMétodo {
    corpodoMétodo
}
```

## Declaração do Método

A declaração de um método deve conter pelo menos uma indicação de qual valor o método retorna e um nome para o método.

```java
valordeRetorno nomedoMétodo() {
    ...
}
```


 Ex.:
```java
 class Pilha {
  ...
  boolean estaVazia() {
   ...
  }
 }
```
O exemplo acima declara um método chamado estaVazia que retorna um valor do tipo boolean (true ou false).
 

### Retornando valores

A linguagem Java exige que o método declare o tipo de dado que ele retorna. Se um método não retorna valor algum ele é declarado como sendo void.

Um método pode retornar tanto um valor de um tipo primitivo ou um valor de um tipo de referência (um objeto). O exemplo anterior retorna um valor de um tipo primitivo: boolean. Vejamos um método que retorna um valor de um tipo de referência.

```java
class Pilha {
    static final int PILHA_VAZIA = -1;
    Object elemento[];
    int elementonoTopo = PILHA_VAZIA;
        ...
    Object desempilha() {
        if (elementonoTopo == PILHA_VAZIA)
            return null;
        else {
            return elemento[elementonoTopo--];
        }
    }
}
```

O tipo de dado do valor retornado pelo método deve ser do mesmo tipo de dado do valor que foi declarado como sendo o do método. Quando retornamos um objeto, este objeto deve ser da mesma classe definida com o método ou de uma subclasse desta classe. Quando declaramos uma interface como um tipo de dado de retorno, o objeto retornado deve ser de uma classe que implemente esta interface. No exemplo anterior, poderíamos retornar qualquer objeto pois declaramos Object como sendo o valor de retorno. Todas as classes em Java são subclasses de Object.

## Nomeando métodos

Os métodos podem ter qualquer nome que seja um identificador Java válido. Existem três casos que devemos considerar quando estivermos dando nome a um método.

### Sobrecarga de métodos (polimorfismo)

A linguagem Java permite a sobrecarga de métodos, possibilitando que existam diversos métodos com o mesmo nome.

Suponha que você está escrevendo uma classe que irá escrever diversos tipos de dados (inteiros, strings, floats...). Você teria que pensar em um nome para cada método que você fosse escrever:

- escreveInteiro();
- escreveString();
- escreveFloat()...

Em Java, podemos tirar vantagem da sobrecarga e escrever todos estes métodos com um único nome. Vamos chamá-los de `escreve()`.

Na nossa classe, declararíamos diversos métodos chamados escreve() que teriam como grande diferenciador o tipo de dado do parâmetro recebido.

```java
class EscreveDados {
    void escreve(int i) {
        ...
    }
    void escreve(String s) {
        ...
    }
    void escreve(float f) {
        ...
    }
}
```

Os métodos serão diferenciados pelo compilador através do número e do tipo de argumentos que recebem. Note que os métodos sobrecarregados devem retornar o mesmo tipo de dados. Caso fizéssemos declarações como void escreve(int i) e int escreve(int z) na mesma classe, receberíamos uma mensagem de erro ao compilar o código.

### Construtores

Qualquer método cujo nome é o mesmo nome da classe é um método chamado de construtor. Construtores são usados para inicializar um novo objeto criado pela classe. Os construtores só podem ser chamados pelo operador new.

### Sobrescrita

Uma classe pode sobrescrever os métodos herdados da superclasse, desde que eles possuam a mesma declaração (tipo de retorno, nome, número e tipo de argumentos...).

## Passando informações para o método

Em Java, podemos passar argumentos de qualquer tipo de dados, desde tipos primitivos até tipos de referência.

```java
 class Circulo {
  ...
  public Circulo(int x, int y, int radianos) {
   ...
  }
 }
```

Destacada acima está a declaração de três parâmetros do tipo inteiro chamados x, y e radianos para o método Circulo.

Diferente de outras linguagens, Java não permite que passemos métodos como parâmetros para um método. O que pode ser feito para remediar isto é passar um objeto como parâmetro e depois chamar o método através do objeto.

O nome que damos ao argumento é o nome que será usado dentro do método. O nome do argumento pode ser o mesmo de uma variável membro da classe da qual o método é membro. Quando isso acontece, dizemos que o argumento está escondendo a variável membro da classe. Isto é comum em construtores.

```java
class Circulo {
    int x, y, radianos;
    public Circulo(int x, int y, int radianos) {
        this.x = x;
        this.y = y;
        this.radianos = radianos;
    }
}
```

Aqui, quando usamos as variáveis x, y e radianos, estamos nos referindo àquelas que foram passadas como argumento e não às variáveis membro da classe. Para fazer referência às variáveis membro da classe usamos this, que representa a classe atual. 
