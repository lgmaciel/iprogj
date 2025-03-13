# Objetos (uso)

Depois de ter criado um objeto, acredito que você vai querer usá-lo para alguma coisa. Nesta lição veremos como se faz isso.

Vamos utilizar o retângulo da lição passada. Digamos que você quer mudar o retângulo de posição.

A classe Rectangle nos dá duas formas de fazer isso:

1. alterando os valores x e y do objeto diretamente
1. chamando o método move()

Referenciando as variáveis de um objeto

Para referenciar as variáveis de um objeto simplesmente adicione o nome da variável ao nome do objeto intercalando-os com um ponto ("."). Assim:

```java
referênciaObjeto.variável
```

Digamos que nosso objeto Rectangle se chama rect. Você acessa suas variáveis x e y assim: rect.x e rect.y. Agora que sabemos os nomes das variáveis x e y, podemos usá-las como se fossem nomes "normais" de variáveis.

```java
rect.x = 0;
rect.y = 0;
```

A classe Rectangle ainda possui mais duas variáveis: width e height. Poderiamos usar estas variáveis para calcular a área do retângulo:

```java
area = rect.width * rect.height;
```

Repare que a primeira parte do nome de uma variável deve ser uma referência a um objeto (um ponteiro em outra terminologia). Voce também pode usar qualquer expressão que retorna uma referência a um objeto. Lembre-se que o operador new retorna uma referência a um objeto. Então você pode usar o valor retornado de new para acessar uma nova variável de um objeto.

```java
largura = new Rectangle().height;
```

## Invocando os métodos de um objeto

Invocar os métodos de um objeto é similar a chamada de uma de suas variáveis. Para chamar um método do objeto, faça como você fez antes para referenciar uma de suas variáveis, adicione o nome do método ao nome do objeto intercalando-os com um ponto (".").

```java
referênciaObjeto = nomedoMétodo(argumentos);
```

##Eliminando objetos

Muitas linguagens de programação orientadas a objeto atribuem a você a responsabilidade de lidar com a finalização (eliminação) dos objetos que já não são mais necessários ao seu programa. Criar este código para gerenciar a memória geralmente é chato e não é incomum o algorítmo conter erros. A linguagem Java nos poupa deste trabalho pois implementa um sistema chamado de Coleta de Lixo que automáticamente apaga os objetos que ele julga não estarem mais em uso.

O runtime do Java sabe se o objeto pode ou não ser coletado se não estiverem mais sendo feitas referências a este objeto. Podemos eliminar, desta forma, um objeto simplesmente atribuindo o valor null à variável que é referência ao objeto. Assim não haverá mais referências sendo feitas.

## Finalização

Antes de um objeto ser coletado, o runtime do Java ainda dá uma chance ao objeto para que ele mesmo se finalize através de uma chamada ao método finalize do objeto. Este processo é conhecido como finalização.

> podemos requisitar a execução do coletor de lixo (garbage colector) através de uma chamada ao método gc() da classe System, assim: System.gc(). O processo de coleta dura em média 20 milisegundos. 
