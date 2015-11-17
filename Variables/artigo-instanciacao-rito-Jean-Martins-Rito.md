# Artigo - Instanciação no Javascript
autor: Jean Martins Rito
github: http://github.com/rito

Quando recebi o desafio de escrever este artigo, a princípio torci o nariz. Se estou fazendo um curso, em tese precisaria receber a teoria e depois fazer os exercícios propostos daquele conteúdo. Legal, estava tranquilo, até surgir o desafio de escrever o artigo. Como fazer um artigo, com conceitos técnicos que não vi, e que não domino?

Legal, Bora escrever de um jeito que eu mesmo consiga entender, visto que muita informação existente na internet, são de técnicos, extremamente técnicos, que escrevem para outros técnicos, e se esquecem que nem todos entendem do que estão falando.
Um item não entendido, ou mal explicado, pode confundir ainda mais, e até fazer pensar que a linguagem é muito complicado, ou que a pessoa nunca entenderá programação. Será que este tabu realmente é verdade?

Desafio Aceito!!!


### Hoisting

Hoist em inglês significa levantar ou suspender algo através de um aparato mecânico. Em bom português, significa usar o guindaste para elevar um objeto. E é isto o que acontece em JavaScript quando declaramos uma variável ou função. Sua declaração é “elevada” para o topo do escopo.

Em outras palavras, esta "Elevação" nada mais é que trazer para o início do escopo a declaração de variáveis e funções.

Vamos usar um exemplo onde você queira usar uma função para juntar 2 palavras:

```
juntarPalavras("guarda", "chuva");
```

Se pensarmos numa linguagem interpretada, que vá executando o código conforme vai "lendo", linha a linha, ao chegar nesta função, teremos um erro, pois esta função não foi definida ainda, é como se você estivesse tentando executar algo que ainda não existe!

Declarar funções no início do programa resolveu o problema por um tempo, pois todas as funções e variáveis eram declaradas antes de serem usadas, sendo assim não se tinha erros de referência.

E para que isto não ocorra, é onde surgiu o conceito de Hosting no Javascript, com o tempo pensaram em uma maneira mais amigável e fácil de ler. Por que não deixar as definições em qualquer lugar do código, e usá-las em qualquer lugar que queira? Agora, os compiladores ou até mesmo linguagens runtime leem todo o programa para saber que funções e variáveis você declarou no código. Após isso, a execução real acontece e ele já sabe onde está cada coisa. JavaScript faz exatamente isso. Isto é Hoisting!!!

Vamos a alguns exemplos:

```
> nome = 'Jean';
> console.log(nome);
Jean
>
```


Até aqui tranquilo, vamos mudar um pouco as coisas:

```
> var nome = meunome;
> console.log(nome);
undefined
//ReferenceError: meunome is not defined
```
Seguindo o conceito explicado acima, como vamos atribuir nome, com o valor de meunome se esta variável não existe?

Agora mudando um pouco:

```

> var meunome;
> console.log(nome);
> var nome = meunome;
undefined
>
```

Agora apresentou UNDEFINED!!!

Isso acontece porque o JavaScript não obriga você a declarar variáveis, permite que você defina as funções em qualquer lugar que você queira, o que lhe permite usar uma função antes de sua definição. O nome hoisting, elevação ou até mesmo içamento, é só um termo especificado, pois ele arranca as declarações até o topo do seu escopo.

Agora o que ficou confuso é a questão da declaração e a inicialização!!!

Declarar a variável meunome:
```
> var meunome;
undefined
>
```

Agora o que é iniciar o conteúdo Jean:

```
> meunome = 'Jean';
'Jean'
>
```

Agora com uma função:
```
console.log(multiplicaNumero(10,10));
var multiplicaNumero = function(a,b) {
  return a*b;
}

//TypeError: undefined is not a function

```
Ele elevou a declaração var multiplicaNumero, mas como chamamos antes de ele ser iniciado recebemos um erro.

E agora se mudarmos para isto:
```
console.log(multiplicaNumero(10,10));
multiplicaNumero = function(a,b) {
  return a*b;
}


//ReferenceError: multiplicaNumero is not defined

```
Nesse caso, o erro foi que o multiplicaNumero não foi declarado!

E agora se transformarmos em uma função?? (Não sei por que, mas isso me lembrou do JavaScript Funcional!!!!)

```
console.log(multiplicaNumero(10,10));
function multiplicaNumero (a,b) {
  return a*b;
}

//100
```

TADA!!!!

Agora o código executou sem erro porque toda declaração de função não anônima é elevada para o topo do escopo.

Com isso aprendemos que é uma boa prática declarar e/ou iniciar variáveis e funções no início do escopo. E outra, utilizarmos funções não anônimas, e utilizando sempre o conceito de reaproveitamento! :)

Acho que ficou um pouco mais claro pra mim. E pra você?


### Closure

Agora tentar explicar de uma maneira mais clara o que é Closure...!

"Closures (fechamentos) são funções que se referem a variáveis livres (independentes)."

Show!!! #SQN
Que porra é essa?

Em outras palavras, a função definida no closure "lembra" do ambiente em que ela foi criada.

Quase... Dá pra ser mais claro?

Vamos ver se melhora com um pouco de prática pra tirarmos novas conclusões:

```
function init() {
  var name = "Rito";
  function displayName() {
    console.log(name);
  }
  displayName();
}
init();


//Rito
```

A função init() cria uma variável local chamada name, e depois define uma função chamada displayName().

displayName() é uma função aninhada (um closure) — ela é definida dentro da função init(), e está disponivel apenas dentro do corpo daquela função.
Diferente de init(), displayName() não tem variáveis locais próprias, e ao invés disso reusa a variável name declarada na função pai.

Este é um exemplo de  escopo léxico : em JavaScript, o escopo de uma variável é definido por sua localização dentro do código fonte (isto é aparentemente  léxico ) e funções aninhadas têm acesso às variáveis declaradas em seu escopo externo.

Agora outro exemplo:

```
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  
console.log(add10(2));





//7
//12
```

Neste exemplo definimos a função makeAdder(x) que toma um único argumento x e retorno uma nova função. A função retornada toma então um único argumento, y, e retorna então a soma de x e de y.

Na essência o makeAdder trata-se de uma função fábrica - irá construir outras funções que podem adicionar um determinado valor específico a seu argumento. No exemplo acima usamos a fábrica de funções para criar duas novas funções - uma que adiciona 5 ao argumento, e outra que adiciona 10.

Ambas as funções add5 e add10   são closures. Compartilham o mesmo corpo de definição de função mas armazenam diferentes ambientes. No ambiente da add5, por exemplo, x equivale a 5, enquanto na add10 o valor de x é 10.

Esta é a teoria — mas closures são realmente úteis? Vamos considerar suas aplicações práticas. Uma closure deixa você associar dados (do ambiente) com uma função que trabalha estes dados. Isto está diretamente ligado com programação orientada a objetos, onde objetos nos permitem associar dados (as propriedades do objeto) utilizando um ou mais métodos.

Consequentemente, você pode utilizar uma closure em qualquer lugar onde você normalmente utilizaria um objeto de único método.

Situações onde você poderia utilizar isto são comuns em ambientes web. Muitos códigos escrito em JavaScript para web são baseados em eventos - nós definimos algum comportamento e então, o atribuimos a um evento que será disparado pelo usuário (quando uma tecla for pressionada, por exemplo). Nosso código normalmente é utilizado como callback: uma função que será executada como resposta ao evento.

Um exemplo prático: suponha que queremos adicionar alguns botões para ajustar o tamanho do texto de uma página. Um jeito de fazer seria especificar o tamanho da fonte no elemento body e então definir o tamanho dos outros elementos da página (os cabeçalhos, por exemplo) utilizando a unidade relativa em:

```
body {
  font-family: Helvetica, Arial, sans-serif;
  font-size: 12px;
}

h1 {
  font-size: 1.5em;
}
h2 {
  font-size: 1.2em;
}
```

Nossos botões interativos de tamanho de texto podem alterar a propriedade font-size do elemento body, e os ajustes serão refletidos em outros elementos graças à unidade relativa.

O código JavaScript:

```
function makeSizer(size) {
  return function() {
    document.body.style.fontSize = size + 'px';
  };
}

var size12 = makeSizer(12);
var size14 = makeSizer(14);
var size16 = makeSizer(16);
```

size12, size14 e size16 agora são funções que devem redimensionar o texto do elemento body para 12.14 e 16 pixels respectivamente. Nós podemos designá-las à botões (neste caso, links) como feito a seguir:

```
document.getElementById('size-12').onclick = size12;
document.getElementById('size-14').onclick = size14;
document.getElementById('size-16').onclick = size16;
```

```
<a href="#" id="size-12">12</a>
<a href="#" id="size-14">14</a>
<a href="#" id="size-16">16</a>
```

Entendido?

### Variável Global

Todas as variáveis declaradas fora de uma função estão no escopo global.
Qualquer variável declarada ou inicializada fora de uma função é uma variável global, e estará portanto disponível para toda a aplicação. Por exemplo:

```
var myName = "Jean";
```

ou
```
firstName = "Richard";
```
ou
```
var name;
name;
```

Se uma variável é inicializada (atribuída com um valor) sem primeiro ser declarada com a palavra chave var, ela é automaticamente adicionada ao contexto global sendo assim portanto uma variável global:

```
function showAge() {
    //age é uma variável global porque ela não foi declarada com a palavra chave var dentro da função
    age = 90;
    console.log(age);
}

showAge();


//age está no contexto global, então está disponível aqui, também
console.log(age);


//90
//90
```

Demonstração de variáveis que estão no Escopo Global mesmo que pareça o contrário:

```
//Ambas variáveis firstName estão no escopo global, mesmo que a segunda esteja dentro do bloco {}
var firstName = "Jean";
{
    var firstName = "Rito";
}

//Para reiterar: JavaScript não tem escopo por nível de bloco
//A segunda declaração ou firstName simplesmente redeclara e sobrescreve a primeira

console.log (firstName);


//Rito
```



### Variável por parâmetro


Aqui foi meio complicado achar uma referência, mas vamos ver se consigo explicar, algo simples, de uma maneira mais simples. Acho que aqui eu me complico mais, pois saber o que acontece, nem sempre é fácil de se explicar! hehe

Você pode ter funções que recebem parâmetros:

```
function somar(parametroA, parametroB){
  soma = parametroA + parametroB;
  console.log(soma)
}

somar(3,5);

//8

```

Quando se passa parâmetros para a função, dentro dela, é como se fossem novas variáveis. Isso fica mais claro quando "manipulamos" uma variável global dentro da função:

```
parametroA = 4;
parametroB = 5;

function somar(parametroA, parametroB){
  soma = parametroA + parametroB;
  console.log("A soma de A + B = " + soma);
  console.log("Pois aqui temos A = " + parametroA + " e B = " + parametroB);
  parametroA = 1;
  parametroB = 2;
  console.log("Agora mudei os valores dentro da função. A = " + parametroA + " e B = " + parametroB);

}

somar(parametroA, parametroB);
console.log("Fora da função continuamos tendo A = " + parametroA + " e B = " + parametroB);


```

Como Resultado deste código acima, temos:

```
A soma de A + B = 9
Pois aqui temos A = 4 e B = 5
Agora mudei os valores dentro da função. A = 1 e B = 2
Fora da função continuamos tendo A = 4 e B = 5

```

### Instanciação usando uma IIFE

O termo IIFE, vem do Immediately-Invoked Function Expression, e usado para se referir a funções que são imediatamente executadas ao serem definidas.

Há vários locais que podemos usar uma IIFE, porém o mais comum é quando queremos criar um escopo no JavaScript para que as variáveis definidas dentro da função não poluam o escopo global.

Isso é tudo a respeito de evitar ao máximo criar variáveis globais no JavaScript, e criar escopos quando e onde precisarmos.

```
(function () {
  'use strict'

  var sayHi = 'oi'
  console.log(sayHi) // Aqui ele retorna oi
}())

console.log(sayHi) // Aqui ele retorna: ReferenceError: sayHi is not defined
```

Assim mantemos as variáveis todas dentro do nosso código, evitando que o JavaScript de outras pessoas alterem nossas variáveis. Como libs de terceiros ou curiosos com o DevTools aberto. Imagina alguém alterando o preço de um produto porque a variável “productPrice” é global? Não seria legal. (Um exemplo hipotético, acho que você sacou a ideia, certo?)

IIFE geralmente ficam dentro de parênteses ( ), o que eles fazem basicamente é retornar qualquer coisa que você coloque dentro dele, como se fossem parâmetros de uma função.

```
(i) // undefined // Porque i não existe
(1 + 2) // retorna 3

var fn = (function () { return 'oi' }) // retorna toda a função para a variável fn
fn() // 'oi'
```

Porém se colocarmos um () logo depois da função:

```
var fn = (function () { return 'oi' }()) // Executa a função dentro dos parênteses
fn // 'oi' // O que é retornado pelo primeiro ( ) é o return da função


```

Desenhando um pouquinho o exemplo:

![Desenhando pra mim mesmo](http://tutsmais.com.br/blog/wp-content/uploads/2015/05/Screen-Shot-2015-05-01-at-16.18.24.png)

Podemos definir uma IIFE sem usar o primeiro parênteses abraçando toda a function, ou trocar o parênteses que invoca a function de lugar:


```
var fn = function () { return 'oi' }(); // Funciona

var fn = (function () { return 'oi' }()) // Funciona e é validado pelo JSLint

var fn = (function () { return 'oi' })() // Também funciona, mas não é validado pelo JSLint

```

Nós geralmente colocamos o primeiro parênteses como uma forma de padronizar, uma convenção. E a vantagem de usar o primeiro parênteses é que você pode executar as funções anônimas sem necessariamente atribuir o valor que ela retorna para uma variável.

A maior vantagem de usar IIFEs, é porque as IIFE faz com que todo o código que está em volta do seu script não tenha acesso as variáveis que você define.

Outra coisa interessante é que no segundo parênteses, onde invocamos a function, podemos passar qualquer parâmetro como se fosse qualquer outra função.

```
(function (string) {
  console.log(string)
}('oi'))

// Log 'oi'

```

Podemos usar em um return, podemos definir uma função que a variável será o return da IIFE

```
var conte = (function () {
  var numero = 0;

  return function () {
    numero = numero + 1

    return numero
  }
}())

conte() // 1
conte() // 2
conte() // 3
conte() // 4

```

Assim por exemplo, a função é definida por uma IIFE que retorna uma function, então o valor da variável “conte” não será toda a função, porém apenas a função do return, que por sua vez tem acesso ao escopo criado dentro da IIFE.

Dessa forma sempre que executamos “conte()” a função tem acesso a variável “numero” porém fora dessa função essa variável não existe.

Podemos chamar essa variável numero de variável “privada” porque só temos acesso a ela dentro da nossa função IIFE, assim podemos criar métodos que manipulam os dados da variável numero.

Você deve usar uma IIFE sempre que surgir a necessidade de isolar as variáveis que você precisa do escopo global. Isso é uma boa prática e é uma forma de fazer com que seu código funcione bem independente de onde ele for usado, são práticas como essa, que libs como jQuery, AngularJS, React e várias outras libs e frameworks usam.

O let já funciona nos browsers mais modernos, e para alguns casos que hoje precisaríamos usar IIFE para isolar variáveis, no futuro (também conhecido como hoje) você poderá usar o let para declarar variáveis.

O let está disponível no ES6. :)

Acho que é isso!!! Espero não ter esquecido de nada. Ou não ter compreendido por completo.

Digerindo bastante coisa neste momento!!! :)




### Referências Bibliográficas
http://tableless.com.br/elevacao-ou-javascript-hoisting/
http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/
https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures
http://javascriptbrasil.com/2013/10/11/escopo-de-variavel-e-hoisting-no-javascript-explicado/
https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Fun%C3%A7%C3%B5es
http://tutsmais.com.br/blog/javascript-2/o-que-e-iife-no-javascript/
http://jstherightway.org/pt-br/
