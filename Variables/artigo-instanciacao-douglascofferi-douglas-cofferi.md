# Instanciação de Variáveis no Javascript
autor: **Douglas Cofferi**

## Hoisting

Hoisting é um comportamento padrão de JavaScript de mover todas as declarações para o topo do escopo atual. Toda vez que uma variável é definida, sua declaração é hoisted, mas não sua inicialização. Isso quer dizer que a declaração da variável vai para cima do escopo antes mesmo do código ser executado, mas esta variável não recebe nenhum valor e permanece como undefined.

Exemplo:
```js
// Irá imprimir `undefined`
try {
  console.log(a)
  var a = 2
} catch (e) {
  console.error('A variável `a` não foi definida.')
}
```

## Closure

Uma closure ocorre normalmente quando uma função é declarada dentro do corpo de outra, e a função interior referencia variáveis locais da função exterior. Em tempo de execução, quando a função exterior é executada, então uma closure é formada, que consiste do código da função interior e referências para quaisquer variáveis no escopo da função exterior que a closure necessita.

Exemplo:
```js
var digaSeuNome = function( nome ) {
    var msg = "Olá " + nome + ". Seja bem-vindo!";
    var exibeMensagem = function() {
        alert( msg );
    };

    exibeMensagem();
};

digaSeuNome("João");    // Olá João. Seja bem-vindo!
```

No exemplo a cima temos uma função definida dentro de outra função. A função interna utiliza de parâmetros e variáveis da função externa… basicamente, este é o conceito de closure.
 
	
## Variável Global

Uma variável **GLOBAL** pode ser usada dentro de uma função como se fosse uma variável qualquer, e se o seu valor for alterado em uma uma função (que não seja passada por parâmetro) por exemplo, o seu valor será alterado também para o restante do código/aplicação. Desta forma, deve se tomar muito cuidado ao utilizar variáveis globais.

Exemplo:
```js
var nome = "Douglas Cofferi";

function retornaAutor(){
	return 'Autor: ' + nome;
}
```

## Variável por parâmetro

Quando uma variável é passada como parâmetro para uma função, é como se fosse uma nova variável ou seja as alterações feitas dentro do escopo dessa função somente serão visíveis no próprio escopo. Caso seja passada uma variável GLOBAL como parâmetro o mesmo acontece.
O valor das variáveis passadas como parâmetro somente irão receber o valor alterado dentro da função caso as mesmas sejam retornadas por referência. Assim o ponteiro da memória onde está sendo alterado os valores não é trocado para um ponteiro novo.

## Instanciação usando uma IIFE

Immediately-Invoked Function Expression (IIFE) geralmente ficam dentro de parênteses (), o que eles fazem basicamente é retornar qualquer coisa que você coloque dentro dele, como se fossem parâmetros de uma função.

```js
function () {
	console.log('Olá')
}()
```

Uma variável pode receber o valor de uma IIFE apenas pelo seu retorno/resultado. 
Para passar um parâmetro para uma IIFE basta utilizar o segundo parâmetro da mesma ou seja:
Outra coisa interessante é que no segundo parênteses, onde invocamos a function, podemos passar qualquer parâmetro como se fosse qualquer outra função.

Exemplo:
```js
(function (string) {
  console.log(string)
}('Olá'))
 
```
 
Você deve usar uma IIFE sempre que surgir a necessidade de isolar as variáveis que você precisa do escopo global. Isso é uma boa prática e é uma forma de fazer com que seu código funcione bem independente de onde ele for usado.

## Fontes

https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures

http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/

http://klauslaube.com.br/2011/05/29/afinal-o-que-sao-closures.html

http://tutsmais.com.br/blog/javascript-2/o-que-e-iife-no-javascript/