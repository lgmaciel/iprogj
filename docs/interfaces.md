# Interfaces

Uma interface é uma coleção de definições de métodos (sem implementações) e valores constantes. A definição de uma interface é parecida com a definição de uma classe. Uma definição de interface possui dois componentes: declaração e corpo.

```java
declaraçãodaInterface {
    corpodaInterface
}
```

A declaraçãodaInterface declara vários atributos sobre a interface: como seu nome e se ela extende uma outra interface. O corpodaInterface contém as declarações das contantes e dos métodos da interface.

```java
[public] interface nome [extends superinterfaces] {
 ...
}
```

Para usar uma interface, você escreve uma classe que implementa a interface. Quando uma classe implementa uma interface, ela deve prover a implementação para os métodos declarados na interface e, se houverem, suas superinterfaces.

Quando você define uma nova interface, você está, em essência, definindo um novo tipo de dado de referência. Você pode usar nomes de interfaces em qualquer lugar onde você usaria qualquer outro nome de tipo: declarações de variáveis, parâmetros para métodos...

> Interfaces são uma excelente alternativa à herança múltipla (não permitida pelo Java). A heranca múltipla é necessária no caso em que uma classe precisa ser subclasse direta de mais de uma classe ao mesmo tempo. Interfaces são um recurso poderoso também para outros fins. Prometo falar mais sobre isso uma outra hora. (16/10/2000)