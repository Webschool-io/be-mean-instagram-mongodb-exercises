# Javascript - Instanciação
**autor**: Francisross Soares de Oliveira

O objetivo desse artigo é apresentar as principais formas de criar e instanciar variáveis no JavaScript. O JavaScript é uma linguagem da família de linguagem baseadas em C, mas o seu escopo funciona diferente das irmãs: C, C++ e Java.

## Hoisting
Hoisting significa usar guindaste para elevar algo. Sendo assim no JavaScript toda vez que uma váriavel ou função é declarada, sua declaração vai para cima do escopo antes mesmo do código ser executado.

##### Variáveis
Se você atribui valor para a variável no momento da sua definição, o que é hoisted é apenas a declaração, o valor é `undefined`, ou seja o valor só passará a existir a partir do momento em que o código passar pela atribuição do mesmo.

```
console.log(a)
var a = 2
console.log(a)
```
No exemplo acima em um primeiro momento será impresso no console, `undefined`, pois como já dito o hoisting aconteceu apenas da declaração, já no segundo momento, imprimirá o valor correto da variável.

##### Funcões
Em uma função o hoisting não ocorre apenas com o nome da função, mas com o seu corpo também.
```
hello()
function hello() {
  console.log('Hello World')
}
```
Se executarmos o exemplo acima, a função é executada normalmente sem apresentar nenhum erro.

Podemos declarar uma função como uma expressão, e dessa forma ela obedecerá ao hoisting de uma variável.
```
hello()
var hello = function() {}
```
Dessa forma nos será retornado um erro do tipo `TypeError`.

## Closures
Uma closure é uma função dentro de outra função que tem acesso as variáveis de nível exterior e global.

Closures são usados no Node.js, e podem ser complicados com Noje.js assíncrono e arquitetura não bloqueante. E são são frequentemente usados no jQuery e em todo pedaço de código JavaScript que você lê.
```
$(function () {
    var selections = [];
    $(".class").click(function () {
        selections.push(this.prop ("name"));
    });
});
```

## Variável Global
Todas variáveis declaradas fora de uma função estão no escopo global, e sendo assim fica disponível para toda a aplicação. Se uma variável é declarada sem a palavra reservada `var` ela é automaticamente adicionada ao escopo global.

```
var nome = "Francis Soares de Oliveira";

function hello()
{
  v = "Variável declarada em uma função e com escopo global";
  console.log("Hello " + nome);
}

hello();
console.log(v);
```

## Variável por Parâmetro

Parâmetros são variáveis passados para serem utilizados dentro de uma função, se for adicionada uma variável como parâmetro, apenas o seu valor é recebido.

```
n = 3;

function double(number){
  return number * 2;
};

console.log(double(n));
```

Você pode definir valores default para um parâmetro, para o caso de ele não ser passado. Mas para isso não aplicamos como em algumas linguagens, `param = value`, deve-se ser testado dentro da função para atribuir o valor default, como no exemplo abaixo.

```
function hello(name)
{
    name = typeof name !== 'undefined' ? name : 'visitante';
    console.log('Hello ' + name);
}

hello();
hello('Francis');
```

## Instanciação usando uma IIFE

IIFE é uma definição para funções que são executadas imediatamente ao serem definidas. O uso mais comum de uma IIFE é quando queremos criar um escopo em `JavaScript` e que as vareáveis criadas dentro da função não venham poluir o escopo global.

```
(function () {
  'use strict'

  var msg = 'oi'
  console.log(msg)
}());

console.log(msg)
```

Ao tentar acessar a variável global `msg` na última linha do exemplo acima ocorre um erro, pois não esta contida na função anônima definida.

Você deve usar uma `IIFE` sempre que surgir a necessidade de isolar as variáveis que você precisa do escopo global. São práticas como essa, que libs como jQuery, AngularJS, React e várias outras libs e frameworks usam.
