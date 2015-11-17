# Artigo - Instanciação no Javascript
**autor**: Yves Cabral Mariano

## Hoisting

Primeiramente, segundo o Google Tradutor, uma das traduções de **hoist** em inglês seria **levantar**. Mas como esse conceito de levantar poderia ser aplicados às variáveis e funçẽos do Javascript? Vamos lá.

> **Hoisting** é um comportamento do JavaScript de mover as declarações para o topo do escopo. ([Mozilla Developers](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting), tradução livre)

Com esse comportamento o Javascript possibilita que uma variável ou função seja declarada depois do seu uso. Vejamos essas duas execuções de código:

Exemplo 1
```js
// É mostrado o erro no console
try {
  console.log(a)
} catch (e) {
  console.error('A variável `a` não foi definida.')
}
```

Exemplo 2
```js
//É impresso undefined no console
try {
  console.log(a);
  var a = 2;
} catch (e) {
  console.error('A variável `a` não foi definida.')
}
```

A partir da execução desses dois exemplos podemos perceber duas coisas. A primeira, e mais óbvia, é que podemos declarar a variável em qualquer local do nosso escopo que ela será levada para cima. Porém, a segunda coisa é que apenas a declaração sofre *hoisting* e não a inicialização.

Seguindo a lógica que o *hoisting* também é aplicado às funções, qual será a mensagem que será mostrada ao usuário?

```js
alert(FooOrBar())

function FooOrBar() {
    function f() {
        return "foo"
    }
    
    return f()
    
    function f() {
        return "bar"
    }
}
```
A mensagem que será mostrada será `bar`. A função `f()` foi declarada uma vez antes da linha de código onde é retornada e, em seguida, é declarada novamente, sendo assim sobrescrita por causa do hosting, mesmo que essa nova declaração esteja após o `return`.

## Closure

*Closure* é um conceito recorrente na programação orientada a objetos. Ela permite, no Javascript, que uma função se "lembre" das variáveis e funções do ambiente da qual ela está inserida. Vejamos o seguinte código simples de exemplo:

```js
function hello() {
    var message = "Hello World!"
    function f() {
        alert(message)
    }
    f()
}
hello()   
```
O nosso *closure* seria a função `hello()`, dentro dela temos a função `f()` que consegue acessar a variável `message`, mesmo não estando declarada no seu escopo.

Vamos fazer um exemplo um pouco mais complicado.
```js
function adder(n) {
    return function(m) {
        return n + m;
    }
}
add1 = adder(1)
add2 = adder(2)

var x = add1(10); // 11
var y = add2(10); // 12
```

Nesse exemplo, temos uma função que retorna uma outra função que transforma a variável em que ela ficar salva em uma função "adicionadora". Desse jeito quando criamos as variáveis `x` e `y` e declaramos elas como sendo o resultados das funções `add1` e `add2`, obtemos como resultado o número passado como parâmetro mais o número que foi passado na declaração da função.

## Variável Global

Qualquer variável declarada fora do escopo de uma função será uma variável considerada como global. Isso quer dizer que essa variável estará acessível em qualquer parte do código.

```js
var i = 42;
function meaningOfLife() {
    return "The meaning of life is " + i;
}
alert(meaningOfLife());
```
No exemplo acima a variável `i` pode ser acessada sem problemas já que foi declarada no escopo global da aplicação.

Uma peculiaridade do Javascript é que variáveis que sejam declaradas sem o comando `var`, mesmo que estejam dentro de uma função, serão tratadas como variáveis globais. Veja no exemplo:

```js
function test() {
    x = 77;
}
test()
console.log(x) // 77
```
Se tentarmos acessar a variável `x` no contexto global da aplicação conseguiremos retornar o seu valor, pois não usamos o comando `var` dentro da declaração da nossa função `test`.
## Variável por parâmetro

Funções recebem parâmetros, e dentro do contexto da função elas receberão novos nomes, mesmo que sejam variáveis mandadas para a função vindas de outros contextos. Além disso, essas variáveis podem ser acessadas apenas dentro da função. Se modifcarmos o exemplo anterior para receber uma variável por meo de parâmetro e tentarmos acessá-la de fora dará errado.
```js
function test(x) {
    console.log(x);
}
test(77)       // 77
console.log(x) // ReferenceError: x is not defined
```
## Instanciação usando uma IIFE
*Immediately-Invoked Function Expression* (IIFE) é uma função que é executada imediatamente no momento em é definida. Baseando-se no conceito de *clousure*, essa forma de instanciação é utilizada principalmente quando se quer isolar variáveis do contexto global.
```js
var count = (function () {
  var n = 0;
  return function () {
    n += 1
    return n
  }
}())
console.log(count()) // 1
console.log(n) // ReferenceError: n is not defined
console.log(count.n) // undefined
console.log(count()) // 2
```
Dessa mesma maneira, também é possível criar objetos com variáveis encapsuladas no Javascript.

Também é possível mandar variáveis do contexto global para dentro da função passando-as como parâmetro. Antigamente, antes do $ ser adotado pelo plugin [jQuery](https://jquery.com/), em projetos reais de páginas web isso era muito comum usar o IIFE com o objeto do jQuery. No exemplo abaixo, nós passamos a deixar de ter que escrever `j Q u e r y` para escrever apenas `$`.
```js
(function($) {
  $('body').html('JS is the best!');
})(jQuery)
```
