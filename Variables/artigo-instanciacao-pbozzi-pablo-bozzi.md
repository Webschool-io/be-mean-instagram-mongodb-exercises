# Artigo - Instanciação de Variáveis no Javascript
autor: **PABLO BOZZI FLORES OLIVEIRA**
email: **pablobozzi@gmail.com**

Este artigo visa axplanar os conceitos acerca da instanciação de varíáveis no Javascript.

Segundo o Wikipedia, JavaScript é uma linguagem de programação interpretada. Foi originalmente implementada como parte dos navegadores web para que scripts pudessem ser executados do lado do cliente e interagissem com o usuário sem a necessidade deste script passar pelo servidor, controlando o navegador, realizando comunicação assíncrona e alterando o conteúdo do documento exibido.

## 1. Características

    * Imperativa e estruturada: JavaScript suporta os elementos de sintaxe de programação estruturada da linguagem C (por exemplo, if, while, switch).
    * Tipagem dinâmica: Como na maioria das linguagens de script, tipos são associados com valores, não com variáveis.
    * Baseada em objetos: JavaScript é quase inteiramente baseada em objetos. Objetos JavaScript são arrays associativos, aumentados com protótipos.
    * Avaliação em tempo de execução: JavaScript inclui a função eval que consegue executar em tempo de execução comandos da linguagem que estejam escritos em uma string.
    * Funcional: Na orientação a objetos a menor parte de um sistema é um objeto. Você pode atribuir objetos a variáveis, pode passá-los por parâmetro e ter métodos retornando objetos. Na programação funcional, a menor parte do seu sistema é uma função. Isso implica que você pode atribuir funções a variáveis, pode passá-las por parâmetro e mesmo fazer com que uma função retorne outra função.

## 2. Hoisting

No Javascript uma variável pode ser declarada após ter sido utilizada. Em outras palavras, uma váriavel pode ser utilizada antes de ter sido declarada.

Exemplo:
```js
> x=5; // Atribui 5 a x
5
> var y=x; // Declara y com o valor de x
undefined
> y // Exibe o valor de y
5
> var x=10; // Declara x com o valor de 10
undefined
> x // Exibe o valor de x
10
> y // Exibe o valor de y
5
```

**Dica:** Javascript no modo estrito não permite que você utilize uma variável se ela não for declarada, tornando mais fácil de escrever um JavaScript seguro. Para isso utilize a diretiva "use strict".

Exemplo:
```js
> function myFunction() {
... "use strict"; // Uso da diretiva
... x=5;
... }
undefined
> myFunction();
ReferenceError: x is not defined // Erro, x não foi declarado
    at myFunction (repl:3:2)
    at repl:1:1
    at REPLServer.defaultEval (repl.js:248:27)
    at bound (domain.js:280:14)
    at REPLServer.runBound [as eval] (domain.js:293:12)
    at REPLServer.<anonymous> (repl.js:412:12)
    at emitOne (events.js:82:20)
    at REPLServer.emit (events.js:169:7)
    at REPLServer.Interface._onLine (readline.js:210:10)
    at REPLServer.Interface._line (readline.js:549:8)
> 
```

**Dica:** Objetos também são variáveis!

## 3. Closures - Variáveis locais e globais

No Javascript as variáveis pertencem ao escopo **local** ou **global**. As variáveis privadas podem ser criadas com closures.

Um função pode acessar todas as variáveis declaradas dentro de seu escopo.

Exemplo:
```js
> function myFunction() {
... var a=4;
... return a*a;
... }
undefined
> myFunction();
16
> a
ReferenceError: a is not defined // Erro, a não foi declarado
    at repl:1:1
    at REPLServer.defaultEval (repl.js:248:27)
    at bound (domain.js:280:14)
    at REPLServer.runBound [as eval] (domain.js:293:12)
    at REPLServer.<anonymous> (repl.js:412:12)
    at emitOne (events.js:82:20)
    at REPLServer.emit (events.js:169:7)
    at REPLServer.Interface._onLine (readline.js:210:10)
    at REPLServer.Interface._line (readline.js:549:8)
    at REPLServer.Interface._ttyWrite (readline.js:826:14)
> 
```

Mas também uma função pode acessar variáveis fora de seu escopo.

Exemplo:
```js
> var a=4;
undefined
> function myFunction() {
... return a*a;
... }
undefined
> myFunction();
16 // Retorna 16
> 
```

No primeiro exemplo **a** é uma variável local e só pode ser acessada ou utilizada dentro do escopo da função. No segundo exemplo **a** é uma variável **global** e pertence a todo o escopo. As variáveis globais pertencem a todo o escopo e podem utilizadas e ser alteradas por qualquer script no escopo.

## 4. Variável por parâmetro

Uma função Javascript não realiza qualquer validação nos valores de seus parâmetros (argumentos).

Os parâmetros de uma função são os nomes listados na definição da função.

Os argumentos de uma função são os valores passados (e recebidos) para a função.

### 1. Regras

    * A assinatura de uma função não define o tipo dos seus parâmetros.
    * As funções Javascript não realizam qualquer tipo de validação aos seus argumentos.
    * As funções Javascript não verificam a quantidade de parâmetros informados.

### 2. O objeto 'arguments'

As funções Javascript possuem um objeto chamado **arguments** por padrão. Ele contém um array dos argumentos utilizados quando a função fora chamada (invocada).

```js
> function max() { // Não recebe parâmetros
... var i;
... var max=-Infinity;
... for(i=0;i<arguments.length;i++) { // Percorre o objeto arguments
..... if(arguments[i]>max){
....... max=arguments[i];
....... }
..... }
... return max;
... }
undefined
> x=max(1,123,500,115,44,88);
500 // Maior valor passado como parâmetro
```

**Dica:** Argumentos são passados por valor enquanto que objetos são passados por referência. Ou seja, mudanças no argumentos só serão visualizadas dentro do escopo da função enquanto que mudanças realizadas nos objetos serão visualizadas fora do escopo da função.

## 5. Instanciação usando uma IIFE

Não demora muito quando você se depara com o seguinte código:

```js
> (function (){
... x=5; // Corpo da função
... })();
undefined
> 
```

À primeira vista é muito confuso, porém o conceito é simples. O padrão é chamado de **Immediately Invoked Function Expression** (ou **IIFE**).

Em Javascript funções podem ser declaradas tanto através de uma declaração de função quanto de uma expressão de função. Uma declaração de função é o modo normal de se criar uma função.

```js
// Declaração de função
function myFunction() { /* lógica aqui */ }
```

De outro lado, se você atribuir uma função À uma variável ou propriedade, você estará lidando com uma expressão de função.

```js
// Atribuição de uma expressão de função a uma variável
var myFunction=function() { /* lógica aqui */ };

// Atribuição de uma expressão de função a uma propriedade
var myObj = {
    myFunction:function() { /* lógica aqui */ }
};
```

Uma função criada no contexto de uma expressão é também uma funçẽso de expressão. Exemplo:

```js
// Tudo dentro do parênteses é uma expressão de função
(function() { /* lógica aqui */ });

// Tudo depois do operador ! é parte de uma expressão
!function() { /* lógica aqui */ };
```

O ponto chave sobre expressões Javascript é que elas retornam valores. Em ambos os casos acima o valor retornado da expressão é a função.

A razão principal para usar um **IIFE** é para ter privacidade. Isso porque o scopo das variáveis declaradas com **var** dentro de uma **IIFE** é restrito à função e não podem ser acessadas de fora.

Exemplo:
```js
> (function(){
... var x=5;
... console.log(x);
... })(); // Escreve 5
5
undefined
> console.log(x); // Erro de refência (x não foi declarado)
ReferenceError: x is not defined
    at repl:1:13
    at REPLServer.defaultEval (repl.js:248:27)
    at bound (domain.js:280:14)
    at REPLServer.runBound [as eval] (domain.js:293:12)
    at REPLServer.<anonymous> (repl.js:412:12)
    at emitOne (events.js:82:20)
    at REPLServer.emit (events.js:169:7)
    at REPLServer.Interface._onLine (readline.js:210:10)
    at REPLServer.Interface._line (readline.js:549:8)
    at REPLServer.Interface._ttyWrite (readline.js:826:14)
> 
```

Claro que podemos nomear e chamar explicitamente uma função para atingir os mesmos propósitos.

```js
> (function myFunction(){
... var x=5;
... console.log(x);
... })(); // Escreve 5
5
undefined
> myFunction(); // Erro de referência (myFunction não foi declarado)
ReferenceError: myFunction is not defined 
    at repl:1:1
    at REPLServer.defaultEval (repl.js:248:27)
    at bound (domain.js:280:14)
    at REPLServer.runBound [as eval] (domain.js:293:12)
    at REPLServer.<anonymous> (repl.js:412:12)
    at emitOne (events.js:82:20)
    at REPLServer.emit (events.js:169:7)
    at REPLServer.Interface._onLine (readline.js:210:10)
    at REPLServer.Interface._line (readline.js:549:8)
    at REPLServer.Interface._ttyWrite (readline.js:826:14)
> 
```

## 6. Considerações

Javascript e Java são linguagens completamente diferentes, ambos no conceito e design. Javascript foi criada por Brendan Eich em 1995, e se tornou um padrão ECMA em 1997. Hoje o seu nome oficial é ECMA-262. Na data da estrita deste artigo, ECMAScript 6 (lançada em Junho de 2015) é sua última versão oficial.
