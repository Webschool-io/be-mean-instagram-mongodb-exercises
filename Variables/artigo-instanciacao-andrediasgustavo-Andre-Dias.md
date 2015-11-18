# Artigo - Instanciação de Variáveis em Javascript

**autor**: André Dias

**Email**: andrediasgustavo@gmail.com

Esse artigo trata sobre instanciação de variáveis e suas diversas características peculiares da linguagem Javascript.

## Hoisting

O termo Hoist vem do inglês, e em português quer dizer içar, levantar, e é essa característica que confunde muitos programadores que não tem muito conhecimento de javascript, por que apesar da linguagem ser similar em sintaxe a linguagens como C/C++ e java, ela não funciona da mesma maneira em relação ao escopo das variaveis e funções, essas linguagens(c, c++, java), tem seu escopo por bloco(if, while, switch), já o Javascript tem o escopo criado apenas por funções e por closures(será o tema da próxima seção) e pelo let que é uma feature do ES 2015. E essa característica que é nomeada de hoisting possibilita então que seja chamado uma variável ou função antes que seja declarada. 

Vamos ver como o código pode apresentar algo totalmente inesperado se o programador não conhecer muito bem a linguagem.

```
function foo() {
  function bar() {
    return 5
  }

  return bar()

  function bar() {
    return 10
  }
}

console.log(foo())

```

Se o programador desavisado e desconhecedor da linguagem, escrever esse código esperará que o resultado será 5 e não 10, mas é aí que entra o Hoisting, nesse código a última function bar declarada é elevada por causa do hoisting e sobrescreve a primeira function bar alterando seu valor e por fim retornando 10 e não 5.

Dentro do Hoisting precisamos entender duas situações em que ele se apresenta, na **Variable Hoisting** e na **Function Hoisting**:

Variable Hoisting significa que toda variavel é **hoisted**, mas apenas sua declaração é levantada e não sua inicialização então nesse exemplo abaixo, veremos isso com mais cuidado.

```
// exemplo 1
try {
  console.log(a)
} catch (e) {
  console.error('A variável `a` não foi definida.')
}

// A resposta desse código e A variável `a` não foi definida.

// exemplo 2
try {
  console.log(a)
  var a = 2
} catch (e) {
  console.error('A variável `a` não foi definida.')
}

// // A resposta desse codigo e undefined

```

No exemplo 1 podemos ver que claramente ocorrerá um erro pois simplesmente não foi definida e por consequência é retornado um erro. Já no exemplo 2 o hoisting entra em ação elevando a declaração da variável a mas não sua inicialização com o valor 2, então por consequencia disso é retornado undefined.

No Function Hoisting a situação muda um pouco não apenas a declaração da função é hoisted mas o seu corpo também, mas há um porém uma função pode ser declarada como uma expressão e nesse caso a regra da variable hoisting é que comanda.

Vamos ver um caso de function hoisting:

```
foo()
function foo() {
  console.log('bar');
}

```

Nessa siatuação se vê claramente que irá imprimir no console a palavra 'bar' por que como explicado acima não apenas o nome da função mas o seu corpo também.


```

function teste(){
  function novo() {
    return "testando o novo";
  }

  return novo();

  function novo() {
    return "Eu que vou aparecer";
  }
}

console.log(teste())

```

Nesse codigo muito parecido com o nosso primeiro exemplo desse artigo, o hoisting faz com que a ultima função sobrescreva a primeira alterando a mensagem no console.

## Closure

Closure é um conceito que, de forma simplificada, permite que uma função acesse variáveis de sua função parente. E um ponto muito importante nas closures é que é feita a cópia das referências das variáveis, e não de seus valores.

Isto significa que ao alterar o valor de uma variável dentro de um closure todos os outros contextos que possuem referência para essa variável irão obter este valor quando acessá-la. Esse é um ponto onde deve se ter muito cuidado para que ocorra problemas de escopo.

Veremos aqui a seguir um exemplo para entendermos mais sobre estes aspectos:

```

function start() {
    var message = "hello world";

    function display() {
        console.log(message);
    }

    display();
}

```

No exemplo a função display tem acesso a variável message, mas note que a variável foi declarada no corpo da função parente start. A função "de dentro" tem acesso as variáveis da "função de fora". display no exemplo é considerado um **closure**.

E as variáveis referenciadas da função parente continuam disponíveis mesmo ao final de sua execução: 

```

function getDisplay() {
    var message = "hello world";
    return function display() {
        console.log(message);
    };
}

var display = getDisplay();
display();

```

Note que agora a exibição do valor de message é feito mesmo após sua função (getDisplay) já ter terminado sua execução. Isso é possivel por que a linguagem prove para função não só a referências de suas variáveis locais e variáveis globais mas também as referências das variáveis não locais, que não estão nem em seu escopo e nem no escopo global, mas que de alguma forma se tornaram acessível a ela.

## Variável Global

Variaveis podem ser locais ou globais, variaveis locais podem sem chamadas apenas dentro do seu escopo, já as globais podem ser chamadas de qualquer lugar do codigo, as variaveis locais duram apenas o tempo que dura a função onde ela esta declarada, as variaveis globais duram o tempo que a pagina estiver aberta. E na questões dos nomes variaveis locais e globais podem ter o mesmo nome pois a variavel local só tem sentido em seu escopo, e não afeta a variavel global. 

```

var teste = "Hello World";

// A local aCentaur variable is declared in this function.
function escopoLocal(){

   var teste = "bye, world";
}

escopoLocal();
teste += " I won't leave this world so soon!";

console.log(teste);

Hello World I won't leave this world so soon!

```

Nesse exemplo fica bem claro a questão do escopo.

## Variável por parâmetro

Quando passamos um parâmetro em uma função, este se torna uma variável local para o escopo daquela função. É como se fizessemos uma declaração de uma variável dentro do escopo daquela função.
O mesmo ocorre para as variáveis globais. Quando estas são passadas como parâmetro é como se fizessemos uma cópia de seu conteúdo para uma variável com o mesmo nome mas de escopo local ou seja apenas seu valor é recebido pela função. Qualquer alteração feita nesta variável permanecerá no escopo local, não sendo replicado para o escopo global.

## Instanciação usando uma IIFE

A IIFE que significa Immediately-Invoked Function Expression, que traduzindo de maneira simplista é "função imediatamente executavel" é uma maneira de criar um escopo restrito não acessado de forma normal, e assim criar o que em outra linguagems chamand strict, isso protege o codigo para que não seja alterado por engano ou por querer mesmo. Isso é uma boa prática e permite que seu codigo seja usado em diversos locais sem entrar em problemas por causa do nome dela.

Podemos atribuir uma IIFE a uma variavel desse modo:

```

var fn = (function () { 
	return 'oi'; 
}()) 	// Executa a função dentro dos parênteses
console.log(fn);// 'oi' 
// O que é retornado pelo primeiro ( ) é o return da função

ou 

var fn = (function () { 
	return 'oi' }) // retorna toda a função para a variável fn
conselo.log(fn()); // 'oi'

```

Outra coisa interessante é que no segundo parênteses, onde invocamos a function, podemos passar qualquer parâmetro.

```

(function (string) {
  console.log(string)
}('oi'))
 
// Log 'oi'

```

Desse forma podemos perceber que a tecnica de IIFE que vem da functional programming é otima para isolar variaveis, e impedir problema no escopo global.

