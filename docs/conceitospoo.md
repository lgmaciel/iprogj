# Conceitos de Programação Orientada a Objetos

Esta lição explica os conceitos básicos da programação orientada a objetos. Não nos preocuparemos, por enquanto, em como aplicar estes conceitos em Java, somente com sua utilização abstrata.

## O que é um objeto?

Como o nome (programação orientada a objetos) dá a entender, objetos são o conceito chave para entender a programação orientada a objetos. Você pode olhar ao seu redor agora e ver muitos exemplos de objetos de verdade: sua mesa; sua televisão; seu cachorro; sua bicicleta.

Estes objetos do mundo real compartilham duas características; todos eles têm estados e comportamentos. Por exemplo: Bicicletas têm estados (marcha atual, duas rodas, número de marchas) e comportamentos (freiar, acelerar, reduzir, trocar marchas).

Objetos de software são modelados a partir de objetos verdadeiros, por isso eles também possuem estados e atitudes. Um objeto de software mantém seus estados em variáveis e implementam suas atitudes através de métodos.

> `Objeto` É um conjunto de variáveis e métodos relacionados.

Você pode representar objetos verdadeiros em programas usando objetos de software. Você pode querer representar cães de verdade como objetos de software em um programa de animação ou uma bicicleta de verdade como uma bicicleta de exercícios eletrônica. Você ainda pode usar objetos de software para "objetificar" conceitos abstratos. Por exemplo, "evento" é um objeto comumente usado em um sistema GUI Windows para representar o evento, por exemplo, de pressionar o botão do mouse ou digitar algo no teclado.

Tudo o que o objeto de software conhece (estados) e pode fazer (comportamentos) são expressados pelas variáveis e métodos deste objeto. Um objeto de software que modela sua bicicleta deve ter variáveis que indiquem o estado atual da bicicleta: sua velocidade é de x Km/h; a cadência do pedal é de y rpm; sua marcha atual é a nª.

Estas variáveis e métodos são formalmente conhecidos como variáveis de instância e métodos de instância, para distinguir eles de variáveis de classe e métodos de classe (que são descritos mais tarde).

A bicicleta de software também deve ter métodos para freiar, trocar a cadência dos pedais e trocar as marchas. (A bicicleta não deve ter um método para trocar sua velocidade, já que a velocidade da bicicleta é, na verdade, uma conseqüência de em qual marcha ela está, qual é a sua velocidade e qual é a inclinação do morro que o ciclista está subindo ou descendo).

Tudo que um objeto não conhece ou não pode fazer é excluído do objeto. Por exemplo, sua bicicleta (provavelmente) não tem um nome, e ela não pode correr ou latir. Por isso, não existem  variáveis ou métodos para estes estados e comportamentos.

## O que são mensagens?

Um objeto sozinho geralmente não é muito útil e costuma aparecer apenas como um componente de uma aplicação ou programa que contém muitos objetos. É pela interação entre estes objetos que conseguimos maior ordem e funcionalidade e comportamentos mais complexos. Sua bicicleta pendurada em um gancho na garagem é só um monte de aço, borracha e graxa; sozinha a bicicleta é incapaz de qualquer atividade. A bicicleta é útil somente quando outro objeto (você) interage com ela (começa a pedalar).

Objetos de software interagem e comunicam-se uns com os outros mandando mensagens de um para o outro. Quando o objeto A quer que o objeto B acione um de seus métodos, o objeto A manda uma mensagem para o objeto B.

Às vezes o objeto receptor precisa de mais informação, para que ele saiba exatamente o que fazer. Por exemplo: quando você quer trocar marchas em sua bicicleta, você tem que indicar qual marcha você quer. Esta informação é passada junto com a mensagem como um parâmetro.

> `Mensagem` é um pedido feito de um objeto a outro solicitando ao objeto receptor a execução de um de seus métodos.

Uma mensagem é composta de três partes:

1. o objeto para o qual a mensagem é endereçada (ex. a bicicleta)
1. o nome do método a ser executado
1. quaisquer parâmetros solicitados pelo método 

Estes três componentes são informação suficiente para que o objeto receptor execute o método desejado. Não é necessário nenhuma outra informação ou contexto.

## O que são classes?

No mundo real, você geralmente tem muitos objetos do mesmo tipo. Por exemplo, sua bicicleta é uma das muitas bicicletas no mundo. Usando a terminologia da programação orientada a objetos, dizemos que seu objeto bicicleta é uma instância da classe de objetos conhecida como bicicletas. Todas as bicicletas têm algum estado e comportamentos em comum. Contudo, cada estado da bicicleta é independente e pode ser diferente de outras bicicletas.

Quando constróem bicicletas, os fabricantes tiram vantagem do fato de que bicicletas compartilham características e constróem muitas bicicletas partindo de um mesmo modelo. Seria muito ineficiente produzir um novo modelo para cada bicicleta que fosse fabricada.

Em um software orientado a objetos, também é possível ter muitos objetos do mesmo tipo e que compartilham características: retângulos, registros de empregados, vídeo clipes e outros. Como os fabricantes de bicicletas, você pode tirar vantagem do fato de que objetos do mesmo tipo são similares e você pode criar um modelo para estes objetos. "Modelos" de objetos em software são chamados de classes.

> `Classe` É um modelo ou protótipo que define as variáveis e métodos comuns a todos os objetos de um certo tipo.

Por exemplo, você pode criar a classe bicicleta que deve declarar várias variáveis para guardar a marcha atual, a cadência atual dos pedais, etc. Ela também declara e provê implementações para os métodos que permitem ao ciclista trocar as marchas, freiar e alterar a cadência dos pedais.

Os valores para as variáveis são providos por cada instância da classe. Então, depois de você ter criado a classe bicicleta, você deve instanciá-la (criar uma instância dela) antes de poder usá-la. Quando você cria uma instância de uma classe, as variáveis declaradas pela classe são alocadas em memória. Então você pode usar os métodos de instância para designar valores para as variáveis. Instâncias de uma mesma classe compartilham implementações de métodos.

### Os benefícios das classes

Objetos nos dão os benefícios da modularidade e do ocultamento de informações. Classes dão o benefício da reutilização. Fabricantes de bicicletas reutilizam o mesmo molde para construir montes e montes de bicicletas. Programadores usam a mesma classe para criar montes e montes de objetos.

## O que é herança?

Genericamente falando, objetos são definidos em termos de classes. Você fica sabendo muito sobre um objeto conhecendo sua classe. Mesmo se você não sabe o que é uma Mountain Bike, se eu lhe disser que é uma bicicleta você vai saber que uma Mountain Bike tem duas rodas, barra de direção e pedais.

Sistemas orientados a objetos levam isso um passo à frente e permitem que classes sejam definidas em termos de outras classes. Por exemplo, bicicletas de corrida e Mountain Bikes são ambas diferentes tipos de bicicletas. Na terminologia de programação orientada a objetos, bicicletas de corrida e mountain bikes são ambas subclasses da classe bicicleta. Da mesma forma, a classe bicicleta é a superclasse de bicicletas de corrida e mountain bikes.

Cada subclasse herda estados (na forma de declarações de variáveis) da superclasse. Bicicletas de corrida e mountain bikes compartilham alguns estados: cadência dos pedais, velocidade e aparência. Cada subclasse também herda métodos da superclasse. Bicicletas de corrida e mountain bikes compartilhas algumas atitudes: freiar e alterar a velocidade das pedaladas.

Contudo, sublcasses não são limitadas aos estados e atitudes providos a elas por sua superclasse. Subclasses podem adicionar variáveis e métodos às variáveis e métodos herdados da superclasse.

Subclasses também podem sobrepor métodos herdados e prover implementações especializadas para estes métodos. Por exemplo, se você tem uma mountain bike com um conjunto extra de marchas, você pode sobrepor o método "trocar marchas" e o ciclista poderá agora trocar suas novas marchas.

Você não está limitado somente a um nível de herança, a árvore de herança, ou hierarquia de classes, pode ser tão profunda quanto necessário. Métodos e variáveis vão sendo herdados e herdados através destes níveis, e quanto mais profunda a árvore vai ficando, mais especializados os objetos vão se tornando, juntamente com suas atitudes.

### Os benefícios da herança

1. Subclasses acrescentam atitudes especializadas à uma base de elementos comuns herdados da superclasse. Através do uso de herança, programadores podem reutilizar o código que está na superclasse muitas vezes.
1. Programadores podem implementar superclasses que definem atitudes "genéricas", chamadas de classes abstratas. Nas classes abstratas, a
 essência da superclasse é definida e pode estar parcialmente implementada, mas muito da classe é deixado indefinido e não implementado. Para usá-las, os programadores preenchem os detalhes que faltam criando subclasses especializadas.
