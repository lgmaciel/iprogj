# Variáveis e tipos de dados

Todas as variáveis em Java têm um tipo, um nome e um escopo. Uma declaração de variável sempre contém dois componentes: o tipo da variável e seu nome. 

## Tipos de variáveis

Todas as variáveis em Java devem ser de um determinado tipo. O tipo da variável determina o tipo de dados que a variável irá armazenar e consequentimente as operações que poderão ser realizadas com ela.

Existem outras duas categorias de dados em Java: tipos primitivos e tipos de referência.

Tipos primitivos contém um único valor e incluem tipos como inteiro, ponto flutuante, caracteres e boolean (lógico).

```  
Tipo 	Tamanho 	Descrição
		
números inteiros 		
byte 	8 bits 	    compl. de 2, faixa: -128 até 127
short 	16 bits 	compl. de 2, faixa: -32768 até 32767
int 	32 bits 	compl. de 2, faixa: -2147483648 até
2147483647
long 	64 bits 	compl. de 2, faixa:
-9223372036854775808 até 9223372036854775807
		
números reais 		
float 	32 bits 	Ponto flutuante de precisão simples
double 	64 bits 	Ponto flutuante de precisão dupla
		
outros tipos 		
char 	16 bits 	Um caractere simples
boolean 	indefinido 	Um valor do tipo falso/verdadeiro
```

Tipos de referência são chamados assim porque o valor de uma variável de referência é uma referência (ou um ponteiro em outra terminologia) para o valor atual, ou conjunto de valores, representados pela variável. Do outro lado estão as variáveis primitivas, que quando utilizadas se referem ao valor atual da variável.

Vetores, classes e interfaces são também tipos de referência. Por isso, quando você cria uma classe ou interface você está, no fundo, definindo um novo tipo de dado.

## Nomes de variáveis

Por convenção, nomes de variáveis iniciam com uma letra minúscula (nomes de classe iniciam com uma letra maiúscula).

Em Java, um nome de variável:

1. deve ser um identificador Java válido compreendido por uma série de caracteres Unicode. Unicode é um sistema de codificação de caracteres projetado para suportar textos escritos em diversas línguas. O Unicode permite a codificação de até 34.168 caracteres. Isto permite que você use em seus programas nomes de variáveis ou comentários em idiomas como Grego, Russo, Hebraico e outros.
1. não deve ser igual a uma palavra-chave ou um valor boolean literal (true ou false)
1. não deve ter o mesmo nome de outra variável cuja declaração aparece no mesmo escopo.

A regra 3 implica que variáveis podem ter o mesmo nome que outras variáveis cujas declarações aparecem em um escopo diferente.

## Escopo

O escopo da variável é determinado pela localização da variável, ou seja, onde a declaração dela aparece no código.

O escopo de uma variável é o bloco de código de onde a variável é acessível. O escopo da variável também determina quando a variável é criada e destruída. Você determina o escopo de uma variável quando a declara. O escopo enquadra a variável em uma destas categorias.

 - variável membro
 - variável local
 - parâmetro de método
 - parâmetro de tratamento de exceção

Uma variável membro é um membro de uma classe ou objeto e é declarada com a classe (não com um dos métodos da classe).

Variáveis locais são declaradas com um método ou com um bloco de código em um método. Em geral, uma variável local é acessível de sua declaração até o fim do bloco de código onde ela foi declarada.

Parametros de método são argumentos formais para métodos e construtores e são usados para passar valores para métodos e contrutores. O escopo para um parâmetro de método é todo o método ou construtor para o qual ele é um parâmetro.

Parâmetros para tratamento de exceção são similares a parâmetros para métodos mas são argumentos tanto para um tratamento de exceção quanto para um método ou um construtor.