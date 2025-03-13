# Especificadores de Acesso

Estes especificadores servem tanto para variáveis membro quanto para métodos membro.
 
``` 
Especificador 	classe 	subclasse 	pacote   todas
				
private 	        x 			
protected 	        x 	    x 	      x 	
public 	 	        x 	    x 	      x       x
package 	        x 		x 	
```

## Private

Um membro declarado como private só é acessível na classe onde ele está definido. Isto quer dizer que só instâncias da classe podem usá-lo. Este membro private é como um segredo que você não conta a ninguém.

```java

class Reservada {
    private String naoDigopraNinguem;
    
    private void naoContopraNinguem() {
        System.out.println(naoDigopraNinguem);
    }
}
```

Considere a seguinte classe:

```java
class Metida {
    void meConta() {
        Reservada x = new Reservada();
        x.naoDigopraNinguem = "Esqueci";
        x.naoContopraNinguem();
    }
 }
```
As linhas em destaque não são válidas, pois a classe Metida tenta acessar uma variável e um método privados pertencentes à classe Reservada.

Objetos do mesmo tipo têm acesso aos membros privados uns dos outros. Isto ocorre porque as restrições de acesso se aplicam a nível de classe ou de tipo (todas as instâncias da classe) e não a nível de objeto (uma instância em particular).
 
## Protected

O especificador protected permite que a classe, suas subclasses e as classes em seu pacote acessem o membro declarado como protected. Estes membros protected são como segredos de família (você não se importaria se toda sua família soubesse, mas não quer que alguém de fora fique sabendo).

Vamos supor que a classe Reservada pertence ao pacote Panelinha.
 
```java
package panelinha;

class Reservada {
    protected String DigopraVoce;
    protected void ContopraVoce() {
        System.out.println(DigopraVoce);
    }
}
```

Agora vamos colocar a classe Metida no pacote Panelinha também.

```java
package panelinha;

class Metida {
    void meConta() {
        Reservada x = new Reservada();
            x.DigopraVoce = "Lembrei";
            x.ContopraVoce();
    }
}
```

Agora a classe Metida pode acessar os membros digopraVoce e contopraVoce() da classe Reservada pois eles foram declarados como protected e as duas classes pertencem ao mesmo pacote.

Vejamos uma outra situação, onde teremos uma classe pertencente a um outro pacote mas ao mesmo tempo é uma subclasse de Reservada.

```java
package outros;

import panelinha.*;

classe Curiosa extends Reservada {
    void queroSaber(Reservada r, Curiosa c) {
        r.digopraVoce = "Esqueci"; // inválido
        c.digopraVoce = "Esqueci"; // válido
        r.contopraVoce();   // inválido
        c.contopraVoce();   // válido
    }
}
```

Se a classe Curiosa estivesse no pacote panelinha, ela teria acesso aos membros da classe Reservada.
 
## Public

O membro de uma classe que é declarado public fica acessível por qualquer classe de qualquer pacote. Declare membros publicos somente se o acesso a estes membros por outras classes não for afetar a estabilidade do objeto ou provocar resultados indesejáveis. Podemos dizer que quanto a estes métodos não há segredos pessoais ou familiares; você não se importa que todo mundo fique sabendo.

```java
package panelinha;

class Aberta {
    public String digo;
    public void conto() {
        System.out.println(digo);
    }
}
``` 

```java
package outros;

import panelinha.*;

classe Curiosa extends Aberta {
    void queroSaber(Aberta a, Curiosa c) {
        a.digo = "Esqueci"; // válido
        c.digo = "Esqueci"; // válido
        a.conto();  // válido
        c.conto();  // válido
    }
}
```


## Package

O nível de acesso package é o nível padrão. Se não especificarmos nenhum nível de acesso aos membros que criamos eles serão do tipo package.

Este nível permite que o membro seja acessível por classes que estão no mesmo pacote da classe onde o membro foi definido. Ele supõe que classes do mesmo pacote são "amigos de confiança".

Estes membros package seriam algo como aqueles segredos que você só conta aos seus amigos mais íntimos, nem sua família fica sabendo.

```java
package panelinha;

class Reservada {
    String digo;
    void conto() {
        System.out.println(digo);
    }
}
```

```java
class Curiosa extends Reservada {
    void queroSaber(Reservada r, Curiosa c) {
        r.digo = "Esqueci"; // válido
        c.digo = "Esqueci"; // válido
        r.conto();  // válido
        c.conto();  // válido
    }
}
```
A classe Curiosa consegue acessar os membros da classe Reservada pois ambas estão no pacote panelinha. Qualquer classe fora do pacote panelinha não terá este acesso. 