##Instanciação com Javascript  
#####Autor: Thiago Rodrigues Magalhães


##Introdução

Antes de começarmos o artigo, é importante fazer uma breve introdução sobre o funcionamento do escopo no JavaScript.

#####Ok! Mas o que é escopo?
Escopo é um delimitador, que define o grau de ocultação das informações, ou seja, a visibilidade e a acessibilidade das variáveis e das funções as quais estão associadas.

#####Hmm!?
Trocando em miúdos, se tivermos dois escopos e instanciarmos em cada escopo uma variável com o mesmo nome, elas serão tratadas como diferentes. As alterações que você faz em uma delas, não irá mudar o valor da outra. Esse conceito é importante e muito útil, por exemplo, quando se desenvolve um sistema em equipe poderá ocorrer de ser criada variáveis com o mesmo nome o que tornaria difícil o desenvolvimento do sistema se não existisse o escopo. Já da para você ter uma ideia do motivo.

#####Ah!
Vale lembrar que diferente de outras linguagens como C/C++, condicionais como if, for e while por exemplo não delimitam um novo escpo no JavaScript. Para criarmos um escopo no JavaScript a principal forma que utilizamos é a criação de funções, a famosa function.

#####Show me the code!

No código a seguir, você verá que o if como foi dito acima, não é um delimitador, ele não cria um novo escopo.
```
  var number = 10;

  if (true) {
    var number;
    console.log(a);
  }

```

Utilizamos a function para criar um novo escopo.
```
  var number = 10;

  function init() {
    var number = 5;
    console.log(number);
  }

  init();
  console.log(number);

```

Qual o resultado desses códigos ? Faça o teste e verás. :D


##Hoisting

Hoisting (em português, levantar) é um procedimento do JavaScript onde as variáveis declaradas dentro do escopo são "levantadas" para o topo  se traduzido literalmente significa: levantar algo através de algum meio, em JavaScript quando declaramos uma variável ou função ela sobe para o topo do escopo. Vale ressaltar que é levado para o topo apenas a declaração da variável, sua instanciação não é levada junto.

#####Existe dois tipos de hoisting, a Variable hoisting e a Function hoisting. Vamos ver os dois na prática.

```
  function nota () {
    console.log(ap1);
  }

  nota();
```
O código acima resultaria em erro, lógico, já que a variável ap1 não foi criada.

```
  function nota () {
    console.log(ap1);
    var ap1 = 10;
    console.log(ap1);
  }

  nota();
```
Já esse outro código iria imprimir respectivamente ```undefined```, ```10```. Primeiramente irá imprimir ```undefined``` porque a variável ap1 foi elevada para cima, mas não foi instanciada. Depois irá imprimir ```10``` já que ela foi instanciada com esse valor.

Esse foi um exemplo de Variable hoisting, quando as variáveis são elevadas. Mas como você viu o spoiler mais em cima, também existe a Function hoisting. Mas ela funciona um pouco diferente, veja.

```
  meuTime()
  
  function meuTime () {
    console.log('Flamengo');
  }
```
Bom. Você já sabe o que o hoisting faz e já deve imaginar que a função ```meuTime``` irá executar normalmente, mas eu lhe pergunto, a chamada da função ```meuTime()``` irá imprimir "Flamengo" ou simplemente não irá imprimir nada?

#####Faça a sua aposta!
Diferente do que aconteceria se fosse trabalhado com variáveis, a chamada da função irá imprimir "Flamengo". Você deve está se perguntar, o por quê disso. A resposta é simples, se tratanto de Function Hoisting não apenas o nome da função é levado para o topo, mas também o seu escopo, todo o seu corpo irá junto.

#####Um outro exemplo...
```
  function meuTime () {

    function time () {
      return "Flamengo";
    }

    return time();

    function time () {
      return "Brasil";
    }

  }

  meuTime();
```
E agora!? É simples. Irá imprimir ```Brasil```, simplesmente porque a segunda função ```time()``` será elevada ao topo, mas ela fica depois da função ```time()``` já existe, logo era irá sobrescrever a primeira, o resultado você já sabe.

#####E se eu fizesse...
```
  meuTime();

  function meuTime () { }
```
Iria retornar um erro. Avisando que undefined não pode ser usado como uma função.

#####Dicas
Já que as declarações e as funções são sempre elevadas, é sempre uma boa prática criar no topo todas as funções e variáveis que você utilizará dentro do escopo. Fica mais visível, melhor para outras pessoas que estão lendo o seu código e pode evitar que você se confunda.


##Closures

Clousures nada mais é que uma função filho que tem acesso a variáveis da sua função pai. Clousures, tem acesso as variáveis da função exterior (pai), acesso a variáveis globais e é claro ao seu próprio escopo.
Para criarmos um Clousure basta criar uma função dentro de outra função e para ter acesso as variáveis do pai não é necessário passar os valores por parâmetro, vocês podem acessá-las diretamente. Veja um exemplo:

```
function flash (name) {
  var init = "My name is";

  function fastest () {
    return init + " " + name + ". And I am the fastest man alive.";
  }

  return fastest();
}

console.log(flash("Thiago"));
```
O resultado será ```My name is Thiago. And I am the fastest man alive.```. Simples não !?

####Mas...
Você pode pensar: A função fastest() não é um novo escopo? Como ela tem acesso a variável de outro escopo?. Vou lhe explicar. Sim fastest é um novo escopo, mas veja, ```init``` pertence ao escopo ```flash``` então tudo o que eu fizer dentro desse escopo é lógico que poderei fazer o uso dessa váriavel e dentro do escopo fastest não foi criado uma variável com o mesmo nome, então ela associa essa variável a váriavel pai.

####Com código fica mais fácil.
```
function flash (name) {
  var init = "My name is";

  function fastest () {
    init = "Meu nome é";
    return init + " " + name + ". And I am the fastest man alive.";
  }

  console.log(fastest());
  console.log(init);
}

console.log(flash("Thiago"));
```
####Primeiro, copie o código e veja o que acontece...
O que aconteceu foi que a variável ```init``` que pertence ao escopo de flash recebeu o texto ```Meu nome é```.

####E como eu crio uma variável com o mesmo nome?
Siiiiiiimples. basta colocar ```var``` e o nome da variável. Pegue esse mesmo código e troque ```init = "Meu nome é";``` por ```var init = "Meu nome é";``` veja o que acontece. Se alguma coisa mudar, você já deve ter uma ideia do porquê.

####Por que preciso disso?
Você precisa disso encapsular funções e deixar o código mais limpo. Imagine que você precise de uma função e que essa só poderá ser utilizada por outra função especifica, sendo por algum motivo necessario você ter acesso aos parâmetros e que também seja necessario atualizá-los, fica bem mais fácil e o código fica bem mais legivel se você criar essa função (uma função filha) dentro da função que fará uso dela, função pai, tendo acesso as suas variáveis diretamente.


##Variável Global

Uma variável global está disponível e pode ser usada em toda a aplicação de forma direta. Não existe segredo.

####Como criar uma variável global?
Qualquer variável criada fora de uma função é uma global, podendo ser criada dentro de uma função. Vejamos:

####Fora da função
```
var flag = true;
//ou
flag = "The Flash";
//ou
var flag;
//ou
name;
```
####Dentro da função
```
function myName () {
  name = "Thiago";
}

myName();

console.log(name);
```
Sim. Se você prestar atenção, percebeu que a função acima não tinha o ```var``` antes. O que diferencia se a variável é global ou local (pertencendo ao escopo em que foi criada) é se ela possui ou não o ```var```. Então cuidado para que não acabe criando uma variável global sem querer.


## Variáveis por parâmetro
A passagem de variáveis por parâmetro é uma caracterista da programação funcional, que foi herdada pelo JavaScript. Ela permite passa uma variável ou função para um outro escopo, no caso da variável ela será tratada como local, mesmo que você esteja passando uma variável global. Vamos ao código, assim ficará mais claro.

````
function age () {
  var a = 2015;
  function next (p) {
    p++;
    console.log(p);
  }
  next(a);
  console.log(a);
}

age();
```
Entendeu? Não entendeu? Calma que irei explicar. Dentro da nossa função age, criamos uma variável chamada a que recebe o valor 2015, logo em seguida criamos uma função chamada next colocando entre parenteses um ```p``` que nada mais é do que uma variável local que terá seu valor setado na chamada desta função.

####Então que aconteceu no código acima foi que...
Criamos uma função next com um argumento p. Quando chamamos a função next, colocamos entre parênteses uma variável que já existe, no caso foi ```a``` com o valor 2015, essa é a nossa passagem por parâmetro. Com isso a variável ```p``` pertencente a esse escopo recebe o valor 2015 e as mudanças que fizermos nessa variável não afetara a variável ```a```.

####Hmmm.. E se o argumento tiver o mesmo nome da variável passada?
```
function age () {
  a = 2015;
  function next (a) {
    a++;
    console.log(a);
  }
  next(a);
  console.log(a);
}
```
"No problem". Estaremos criando da mesma forma uma variável local.

####Quando eu irei precisar passar uma variável global por parâmetro?
Você irá precisar quando for usar o valor da variável global ela irá ou poderá haver modificações durante o processo, mas você quer que essas modificações sejam apenas durante a execução dessa função, mantendo inalterado o valor da variável global no final do processo.

```
ano = 2015;

function next (a) {
  a++;
  console.log(a);
}

next(ano);
console.log(ano);
```


## Instanciação usando IIFE
Immediately-Invoked Function Expression, vulgo IIFE e como o próprio nome já diz é uma função que é invocada imediatamente e automaticamente. Ao criarmos uma IIFE, estamos criando um novo escopo, um trecho de código autoexecutavel, que é útil para evitar a poluição do código com a criação de várias variáveis globais e evitando que outras funções tenham acesso as suas variáveis.

####Como criamos esse tipo de função?
Simples. Geralmente, IFFE ficam dentro de parênteses, dentro dos parênteses é crianda uma função anônima e logo depois é colocado um ```()``` que é responsável por invocar a função.

```
(function () {
  console.log('IIFE');
}());
```

####Geralmente? Por que geralmente?
Geralmente porque existe três formas de criarmos uma IFFE.

```
var fun = function () { console.log('oi'); }(); // Funciona

// Funciona e é validado pelo [JSLint] (https://pt.wikipedia.org/wiki/JSLint)
(function () {
  console.log('IIFE');
}());

// Funciona e não é validado pelo [JSLint] (https://pt.wikipedia.org/wiki/JSLint)
(function () {
  console.log('IIFE'); 
})();
```

##Bibliografia

[Wikipedia] (https://pt.wikipedia.org/wiki/Escopo_%28computa%C3%A7%C3%A3o%29)
[loopinfinito] (http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/)
[hugobessa] (https://www.hugobessa.com.br/posts/entendendo-escopo-e-hoisting-no-javascript/)
[javascriptbrasil] (http://javascriptbrasil.com/2013/10/12/entenda-closures-no-javascript-com-facilidade/)
[javascriptbrasil] (http://javascriptbrasil.com/2013/10/11/escopo-de-variavel-e-hoisting-no-javascript-explicado/)
[tutsmais] (http://tutsmais.com.br/blog/javascript-2/o-que-e-iife-no-javascript/)