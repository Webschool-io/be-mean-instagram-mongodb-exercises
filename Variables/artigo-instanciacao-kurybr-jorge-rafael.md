# Instanciação com Javascript
Autor: Jorge Rafael


## Hoisting

No **Javascript**, as funções e variaveis são por padrão Hoisting;
Esse comportamento do Javascript, faz com que todas as declarações sejam jogadas ao topo de um escopo, seja o global ou dentro da função atual.
Em outras palavras, você é capaz de utilizar uma função ou variável mesmo antes da mesma ter sido declarada.

```javascript

//Exemplo com variavel
bola = 'azul';
var bola;

//Exemplo com Função
HelloWorld();
function HelloWorld() {
  console.log("Hello World");
}


```

## Closure

Closure são funções que foram criadas dentro de um escopo*, que utilizam de variaveis independentes da mesma.

Usando o exemplo:

```javascript

function Conversa() {
  var frase = "Olá amigo";
  function Falar(){
    console.info(frase);
  }
}

Conversa();

```

A função **Falar**, está dentro do escopo da função **Conversa**, nesse caso ela não tem variaveis próprias, e re-utiliza das variaveis da conversa para executar alguma ação.

Veja mais um exemplo de Closure:

```javascript

function Soma(x) {
  return function (y){
    return x + y
  }
}

var soma = Somar(1); // x = 1
console.info(soma(2))  // y  = 2
// x + y = 3

```
Executa a função Somar, passando o valor 1 como parametro, ou seja nesse caso **x = 1**, o retorno da função somar, é a função que estava encapsulada, nesse momento a variavel _soma_ se torna uma função.
Ao passar o valor 2 como parametro na soma, estou acionando a segunda função, atribuindo o valor 2 a variavel y **( y = 2 )**


## Variável Global
Uma variável global, é uma variável declarada fora de qualquer escopo, uma vez declarada essa variavel pode ser acessada por qualquer função.
```javascript

var x = "Sou Global o/"
console.info(x);
// Sou Global o/

function f1() { x = 10 }
f1();
console.info(x);
// 10

function f2() { x = 20 }
f2();
console.info(x);
// 20

function f3() {   x = "Sim, por que não ?" }
f3();
console.info(x);
// Sim, por que não ?

```
Como pode ver, uma variavel declarada fora de qualquer escopo, pode ser acessada e manipulada por qualquer função dentro código.

## Variável por parâmetro
Toda função possui dois parâmetros implícitos. **this**, representando o contexto da função, e **arguments**, representando os argumentos passados para a função.

Uma variavel enviada por parametro, é atribuida a uma nova variavel que irá fazer parte do escopo da função chamada.

```javascript
var nome = "Jorge"
function f1(nome) {
  nome = "Rafael";
}
f1(nome)
console.info(nome)
// Jorge

```
Mesmo passando a variavel nome, por parametro, dentro da função ela é atribuida a uma outra variavel, nesse caso chamada _nome_ também, porém as duas são independentes.

Para mudar o nome da variável externa teriamos que passar a variavel como retorno da função

```javascript
var nome = "Jorge"
function f1(nome) {
  nome = "Rafael";
  return nome;
}

nome = f1(nome); // Nesse caso estou retornando o nome alterado para a variável externa.
console.info(nome)
// Rafael

```



## Instanciação usando uma IIFE

**IIFE** ( _Immediately-Invoked Function Expression_ ) - São funções de invocação imediata, sem precisar se chamada no futuro !

```javascript

// Usando IIFE em uma função
(function () {
  'use strict'
  var nome = "Jorge"
  console.info(nome);
  // Jorge
}());

console.info(nome);
// ReferenceError: nome is not defined


```

Ao usar IIFE, você cria um escopo onde tudo que acontecer ali dentro, fica ali dentro !
No exemplo a cima, declaramos a variável **nome** dentro da função encapsulada ou seja, ela não existirá fora do escopo!

```javascript

// Usando IIFE em uma função
var nome = "Jorge";

(function () {
  'use strict'
   nome = "Rafael"
}());

console.info(nome);
// Rafael

```
Para entender um pouco melhor a função de invocação imediata, nesse exemplo criei uma variavel global, chamadas _nome_ e atribui um valor a ela, dentro de uma função que está sendo disparada no momento de criação dela!!

Atribuindo o nome Rafael, mesmo sem eu precisar disparar a função manualmente.



## Considerações

Existem várias formas de instanciar uma variável dentro do Javascript !
Existir várias formas não significa existir a melhor forma ! cada caso é um caso que tem que ser analisado.

Para evitar problemas normalmente é indicado sempre iniciar seu código dentro de uma IIFE global, no arquivo evitando que o código de um arquivo possa prejudicar outro criando um escopo local dentro do arquivo

```javascript


(function () {
  'use strict'

  // Seu código do arquivo aqui ....

}());

```

Desta forma, caso você usar um minificador de JS no futuro evitará problemas de variáveis globalmente declaradas !
